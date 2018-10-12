---
title: 클라우드 관리 게이트웨이에 대한 계획
titleSuffix: Configuration Manager
description: 인터넷 기반 클라이언트의 관리를 간소화하도록 CMG(클라우드 관리 게이트웨이)를 계획하고 설계합니다.
ms.date: 09/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9b25b7a5b7df42dc83bec18d38b44c7807e6dc1a
ms.sourcegitcommit: 2badee2b63ae63687795250e298f463474063100
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45601129"
---
# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Configuration Manager에서 클라우드 관리 게이트웨이 계획

*적용 대상: System Center Configuration Manager(현재 분기)*
 
<!--1101764--> CMG(클라우드 관리 게이트웨이)는 인터넷에서 Configuration Manager 클라이언트를 관리할 수 있는 간단한 방법을 제공합니다. CMG를 클라우드 서비스로 Microsoft Azure에 배포하면 추가 인프라 없이 인터넷에서 로밍하는 기존 클라이언트를 관리할 수 있습니다. 또한 온-프레미스 인프라를 인터넷에 노출할 필요도 없습니다. 

> [!Tip]  
> 이 기능은 버전 1610에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1802 버전부터 이 기능은 더 이상 시험판 기능이 아닙니다.  


> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  


필수 구성 요소를 설정한 후 Configuration Manager 콘솔에서 CMG를 만드는 작업은 다음 세 단계로 구성됩니다.
1. CMG 클라우드 서비스를 Azure에 배포합니다.
2. CMG 연결 지점 역할을 추가합니다. 
3. 서비스에 대한 사이트 및 사이트 역할을 구성합니다. 서비스가 배포 및 구성되면 클라이언트에서 인트라넷 또는 인터넷에 관계없이 온-프레미스 사이트 역할에 원활하게 액세스합니다.

이 문서에서는 CMG에 대해 알아보고, 사용자 환경에 맞게 설계하고, 구현을 계획하기 위한 기초 지식을 제공합니다. 



## <a name="scenarios"></a>시나리오 

CMG가 유용한 몇 가지 시나리오가 있습니다. 일반적인 몇 가지 시나리오는 다음과 같습니다.  

- Active Directory 도메인 가입 ID를 사용하여 기존 Windows 클라이언트를 관리합니다. 이러한 클라이언트로 Windows 7, Windows 8.1 및 Windows 10이 포함됩니다. PKI 인증서를 사용하여 통신 채널을 보호합니다. 포함되는 관리 작업은 다음과 같습니다.  
    - 소프트웨어 업데이트 및 엔드포인트 보호
    - 인벤토리 및 클라이언트 상태
    - 호환성 설정
    - 장치에 소프트웨어 배포
    - Windows 10 전체 업그레이드 작업 순서(1802 버전 현재)

- Azure AD(Azure Active Directory)와 함께 하이브리드 또는 순수 클라우드 도메인에 가입한 최신 ID를 사용하여 기존 Windows 10 클라이언트를 관리합니다. 클라이언트는 PKI 인증서 대신 Azure AD를 사용하여 인증합니다. Azure AD를 사용하면 복잡한 PKI 시스템보다 설치, 구성 및 유지 관리가 더 간단합니다. 관리 작업은 첫 번째 시나리오와 동일하며, 다음과 같습니다.  
    - 사용자에게 소프트웨어 배포  

- 인터넷을 통해 Windows 10 장치에 Configuration Manager 클라이언트를 설치합니다. Azure AD를 사용하면 장치에서 클라이언트 등록 및 할당을 위해 CMG를 인증할 수 있습니다. 클라이언트는 수동으로 설치하거나 Microsoft Intune과 같은 다른 소프트웨어 배포 방법을 사용하여 설치할 수 있습니다.  

- 공동 관리를 사용하여 새 장치를 프로비전합니다. CMG는 공동 관리에 필요하지 않습니다. Windows AutoPilot, Azure AD, Microsoft Intune 및 Configuration Manager와 관련된 새 장치에 대한 종단 간 시나리오를 완료하는 데 도움이 됩니다.  

### <a name="specific-use-cases"></a>특정 사용 사례
이러한 시나리오에 적용할 수 있는 특정 장치 사용 사례는 다음과 같습니다.

- 로밍 장치(예: 랩톱)  

- WAN 또는 VPN 대신 인터넷을 통해 더 저렴하고 효율적으로 관리할 수 있는 원격/지점 장치  

- 인수 합병(장치를 Azure AD에 가입시키고 CMG를 통해 관리할 수 있는 가장 쉬운 방법일 수 있음)  

> [!Important]
> 기본적으로 모든 클라이언트에서 CMG에 대한 정책을 받고 인터넷 기반일 때 해당 정책을 사용하기 시작합니다. 조직에 적용되는 시나리오 및 사용 사례에 따라 CMG의 사용 범위를 지정해야 할 수도 있습니다. 자세한 내용은 [클라이언트에서 클라우드 관리 게이트웨이를 사용하도록 설정](/sccm/core/clients/deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway)을 참조하세요.


## <a name="topology-design"></a>토폴로지 디자인

### <a name="cmg-components"></a>CMG 구성 요소
CMG의 배포 및 운영에 포함되는 구성 요소는 다음과 같습니다.  

- Azure에서 **CMG 클라우드 서비스**는 CMG 연결 지점에 대한 Configuration Manager 클라이언트 요청을 인증하고 전달합니다.  
 
- **CMG 연결 지점** 사이트 시스템 역할을 사용하면 온-프레미스 네트워크에서 Azure의 CMG 서비스로 일관된 고성능 연결을 설정할 수 있습니다. 또한 연결 정보 및 보안 설정을 포함한 설정을 CMG에 게시합니다. CMG 연결 지점은 URL 매핑에 따라 클라이언트 요청을 CMG에서 온-프레미스 역할로 전달합니다.

- [**서비스 연결 지점**](/sccm/core/servers/deploy/configure/about-the-service-connection-point) 사이트 시스템 역할은 모든 CMG 배포 작업을 처리하는 클라우드 서비스 관리자 구성 요소를 실행합니다. 또한 Azure AD의 서비스 상태 및 로깅 정보를 모니터링하고 보고합니다. 서비스 연결 지점이 [온라인 모드](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes)인지 확인합니다.  

- **관리 지점** 사이트 시스템 역할은 정상적인 각 클라이언트 요청을 처리합니다.  

- **소프트웨어 업데이트 지점** 사이트 시스템 역할은 정상적인 각 클라이언트 요청을 처리합니다.  

- **인터넷 기반 클라이언트**는 CMG에 연결하여 온-프레미스 Configuration Manager 구성 요소에 액세스합니다.

- CMG는 **인증서 기반 HTTPS** 웹 서비스를 사용하여 클라이언트와의 네트워크 통신을 보호합니다.  

- 인터넷 기반 클라이언트는 ID 및 인증을 위해 **PKI 인증서 또는 Azure AD**를 사용합니다.  

- [**클라우드 배포 지점**](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)은 필요에 따라 인터넷 기반 클라이언트에 콘텐츠를 제공합니다.  

    - 버전 1806부터 CMG는 클라이언트에게 콘텐츠를 제공할 수 있습니다. 이 기능은 필요한 인증서 및 Azure VM 비용을 줄여줍니다. 자세한 내용은 [CMG 수정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg)을 참조하세요.<!--1358651-->  


### <a name="azure-resource-manager"></a>Azure Resource Manager
<!-- 1324735 --> 1802 버전부터 **Azure Resource Manager 배포**를 사용하여 CMG를 만들 수 있습니다. [Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview)는 모든 솔루션 리소스를 [리소스 그룹](/azure/azure-resource-manager/resource-group-overview#resource-groups)이라는 단일 엔터티로 관리하기 위한 최신 플랫폼입니다. Azure Resource Manager로 CMG를 배포하는 경우 사이트에서 Azure AD(Azure Active Directory)를 사용하여 필요한 클라우드 리소스를 인증하고 만듭니다. 이 최신 배포에는 클래식 Azure 관리 인증서가 필요하지 않습니다.  

Azure 관리 인증서를 사용하는 **클래식 서비스 배포** 옵션도 CMG 마법사에서 계속 제공됩니다. 리소스의 배포 및 관리를 간소화하기 위해 모든 새 CMG 인스턴스에 Azure Resource Manager 배포 모델을 사용하는 것이 좋습니다. 가능한 경우 리소스 관리자를 통해 기존 CMG 인스턴스를 재배포합니다. 자세한 내용은 [CMG 수정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg)을 참조하세요.

> [!IMPORTANT]  
> 이 기능은 Azure CSP(클라우드 서비스 공급자) 지원을 사용하도록 설정하지 않습니다. Azure Resource Manager를 통한 CMG 배포는 CSP가 지원하지 않는 클래식 클라우드 서비스를 계속 사용합니다. 자세한 내용은 [Azure CSP에서 사용 가능한 Azure 서비스](/azure/cloud-solution-provider/overview/azure-csp-available-services)를 참조하세요. 


### <a name="hierarchy-design"></a>계층 디자인

계층 구조의 최상위 계층 사이트에서 CMG를 만듭니다. 중앙 관리 사이트인 경우 자식 기본 사이트에 CMG 연결 지점을 만들 수 있습니다. 클라우드 서비스 관리자 구성 요소는 중앙 관리 사이트에도 있는 서비스 연결 지점에 있습니다. 이 디자인은 필요한 경우 여러 기본 사이트 간에 서비스를 공유할 수 있습니다.

Azure에서 CMG 서비스를 여러 개 만들 수 있으며, CMG 연결 지점도 여러 개 만들 수 있습니다. 여러 CMG 연결 지점은 클라이언트 트래픽의 부하를 CMG에서 온-프레미스 역할로 분산합니다. 네트워크 대기 시간을 줄이려면 연결된 CMG를 기본 사이트와 동일한 지리적 지역에 할당합니다.

 > [!Note]  
 > 인터넷 기반 클라이언트와 CMG는 경계 그룹에 속하지 않습니다.

관리할 클라이언트 수와 같은 다른 요소도 CMG 디자인에 영향을 줍니다. 자세한 내용은 [성능 및 크기 조정](#performance-and-scale)을 참조하세요.

#### <a name="example-1-standalone-primary-site"></a>예 1: 독립 실행형 기본 사이트

Contoso는 뉴욕시의 본사에 있는 온-프레미스 데이터 센터에 독립 실행형 기본 사이트를 가지고 있습니다. 
- 네트워크 대기 시간을 줄이기 위해 미국 동부 Azure 지역에서 CMG를 만듭니다. 
- 모두 단일 CMG 서비스에 연결되는 두 개의 CMG 연결 지점을 만듭니다.  

클라이언트는 인터넷에 로밍할 때 미국 동부 Azure 지역의 CMG와 통신합니다. CMG는 두 CMG 연결 지점 모두를 통해 이 통신을 전달합니다.

#### <a name="example-2-hierarchy-with-site-specific-cmg"></a>예 2: 사이트별 CMG가 있는 계층 구조

Fourth Coffee는 시애틀 본사의 온-프레미스 데이터 센터에 중앙 관리 사이트를 가지고 있습니다. 한 기본 사이트는 동일한 데이터 센터에 있고, 다른 기본 사이트는 파리의 유럽 본사에 있습니다. 
- 중앙 관리 사이트에서 다음과 같이 두 개의 CMG 서비스를 만듭니다.
     - 미국 서부 Azure 지역에 CMG 하나
     - 유럽 서부 Azure 지역에 CMG 하나
- 시애틀 기반 기본 사이트에서 미국 서부 CMG에 연결되는 CMG 연결 지점을 만듭니다.
- 파리 기반 기본 사이트에서 유럽 서부 CMG와 연결되는 CMG 연결 지점을 만듭니다.

시애틀 기반 클라이언트는 인터넷에 로밍할 때 미국 서부 Azure 지역의 CMG와 통신합니다. CMG는 시애틀 기반 CMG 연결 지점을 통해 이 통신을 전달합니다.

마찬가지로, 파리 기반 클라이언트는 인터넷에 로밍할 때 유럽 서부 Azure 지역의 CMG와 통신합니다. CMG는 파리 기반 CMG 연결 지점을 통해 이 통신을 전달합니다. 파리 기반 사용자가 시애틀의 본사로 출장갔을 때에도 자신들의 컴퓨터는 유럽 서부 Azure 지역의 CMG와 계속 통신합니다. 

 > [!Note]  
 > Fourth Coffee는 미국 서부 CMG와 연결된 파리 기반 기본 사이트에 또 다른 CMG 연결 지점을 만드는 것을 고려했습니다. 파리 기반 클라이언트는 위치에 관계없이 두 CMG를 모두 사용하게 됩니다. 이 구성은 트래픽의 부하를 분산하고 서비스 중복성을 제공하는 데 도움이 되지만, 파리 기반 클라이언트에서 미국 기반 CMG와 통신할 때 지연이 발생할 수도 있습니다. Configuration Manager 클라이언트는 현재 지리적 지역을 인식하지 못하므로 지리적으로 더 가까운 CMG를 선호하지 않습니다. 클라이언트에서 임의로 사용 가능한 CMG를 사용합니다.



## <a name="requirements"></a>요구 사항

- CMG를 호스팅하는 **Azure 구독**  

    - **Azure 관리자**는 디자인에 따라 특정 구성 요소의 초기 생성에 참여해야 합니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요하지 않습니다.  

- **CMG 연결 지점**을 호스팅할 하나 이상의 온-프레미스 Windows 서버. 이 역할은 다른 Configuration Manager 사이트 시스템 역할과 함께 배치할 수 있습니다.  

- **서비스 연결 지점**은 [온라인 모드](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes)에 있어야 합니다.   

- CMG에 대한 [**서버 인증 인증서**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-server-authentication-certificate).  

- Azure 클래식 배포 방법을 사용하는 경우 [**Azure 관리 인증서**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#azure-management-certificate)를 사용해야 합니다.  

    > [!TIP]  
    > Configuration Manager 버전 1802부터 **Azure Resource Manager** 배포 모델을 사용하는 것이 좋습니다. 이 관리 인증서가 필요하지 않습니다.  

- 클라이언트 OS 버전 및 인증 모델에 따라 **다른 인증서**가 필요할 수 있습니다. 자세한 내용은 [CMG 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)를 참조하세요.  

    - 1802 버전부터 모든 CMG 지원 [**관리 지점에서 HTTPS를 사용**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#enable-management-point-for-https)하도록 구성해야 합니다.  

- Windows 10 클라이언트에 **Azure AD**와의 통합이 필요할 수 있습니다. 자세한 내용은 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요.  

- 클라이언트에서 **IPv4**를 사용해야 합니다.  



## <a name="specifications"></a>사양

- [클라이언트 및 장치에 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)에 나열된 Windows 버전은 모두 CMG에서 지원됩니다.  

- CMG는 관리 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.  

- CMG는 IPv6 주소와만 통신하는 클라이언트를 지원하지 않습니다.<!--495606-->  

- 네트워크 부하 분산 장치를 사용하는 소프트웨어 업데이트 지점은 CMG에서 작동하지 않습니다. <!--505311-->  

- 버전 1802부터 Azure 리소스 모델을 사용하는 CMG 배포는 Azure CSP(클라우드 서비스 공급자)에 대한 지원을 사용하지 않습니다. Azure Resource Manager를 통한 CMG 배포는 CSP에서 지원하지 않는 클래식 클라우드 서비스를 계속 사용합니다. 자세한 내용은 [Azure CSP에 사용할 수 있는 Azure 서비스](/azure/cloud-solution-provider/overview/azure-csp-available-services)를 참조하세요.  


### <a name="support-for-configuration-manager-features"></a>Configuration Manager 기능 지원
다음 표에는 Configuration Manager 기능에 대한 CMG 지원이 나열되어 있습니다.


|기능  |Support(지원)  |
|---------|---------|
| 소프트웨어 업데이트     | ![지원됨](media/green_check.png) |
| 엔드포인트 보호     | ![지원됨](media/green_check.png) |
| 하드웨어 및 소프트웨어 인벤토리     | ![지원됨](media/green_check.png) |
| 클라이언트 상태 및 알림     | ![지원됨](media/green_check.png) |
| 스크립트 실행     | ![지원됨](media/green_check.png) |
| 호환성 설정     | ![지원됨](media/green_check.png) |
| 클라이언트 설치<br>(Azure AD 통합 포함)     | ![지원됨](media/green_check.png)  (1706) |
| 소프트웨어 배포(장치 대상)     | ![지원됨](media/green_check.png) |
| 소프트웨어 배포(사용자 대상, 필수)<br>(Azure AD 통합 포함)     | ![지원됨](media/green_check.png)  (1710) |
| 소프트웨어 배포(사용자 대상, 사용 가능)<br>([모든 요구 사항](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)) | ![지원됨](media/green_check.png)  (1802) |
| Windows 10 전체 업그레이드 작업 순서     | ![지원됨](media/green_check.png)  (1802) |
| CMPivot     | ![지원됨](media/green_check.png)  (1806) |
| 다른 작업 순서 시나리오     | ![지원되지 않음](media/Red_X.png) |
| 클라이언트 강제 설치     | ![지원되지 않음](media/Red_X.png) |
| 자동 사이트 할당     | ![지원되지 않음](media/Red_X.png) |
| 응용 프로그램 카탈로그     | ![지원되지 않음](media/Red_X.png) |
| 소프트웨어 승인 요청     | ![지원되지 않음](media/Red_X.png) |
| Configuration Manager 콘솔     | ![지원되지 않음](media/Red_X.png) |
| 원격 도구     | ![지원되지 않음](media/Red_X.png) |
| 보고 웹 사이트     | ![지원되지 않음](media/Red_X.png) |
| Wake on LAN     | ![지원되지 않음](media/Red_X.png) |
| Mac, Linux 및 UNIX 클라이언트     | ![지원되지 않음](media/Red_X.png) |
| 피어 캐시     | ![지원되지 않음](media/Red_X.png) |
| 온-프레미스 MDM을 사용할 수 없음     | ![지원되지 않음](media/Red_X.png) |


|키|
|--|
|![지원됨](media/green_check.png) = 이 기능은 지원되는 모든 Configuration Manager 버전의 CMG에서 지원됩니다  |
|![지원됨](media/green_check.png)(*YYMM*) = 이 기능은 Configuration Manager의 *YYMM* 버전부터 CMG에서 지원됩니다  |
|![지원되지 않음](media/Red_X.png) = 이 기능은 CMG에서 지원되지 않음 |



## <a name="cost"></a>비용

>[!IMPORTANT]  
>다음 비용 정보는 평가 목적으로만 사용됩니다. 사용자 환경에 CMG 사용의 전체 비용에 영향을 주는 다른 변수가 있을 수 있습니다.

CMG는 다음과 같은 Azure 구성 요소를 사용하며, 이 경우 Azure 구독 계정에 요금이 청구됩니다.

#### <a name="virtual-machine"></a>가상 머신

- CMG는 Azure Cloud Services를 PaaS(Platform as a Service)로 사용합니다. 이 서비스는 컴퓨팅 비용이 발생하는 VM(가상 머신)을 사용합니다.  

- Configuration Manager 1706 버전에서 CMG는 표준 A2 VM을 사용합니다.  

- Configuration Manager 1710 버전부터 CMG는 표준 A2 V2 VM을 사용합니다.  

- CMG를 지원하는 VM 인스턴스의 수를 선택합니다. 1은 기본값이고, 16은 최댓값입니다. 이 숫자는 CMG를 만들 때 설정되며, 나중에 필요에 따라 변경하여 서비스의 크기를 조정할 수 있습니다.

- 클라이언트를 지원하는 데 필요한 VM 수에 대한 자세한 내용은 [성능 및 크기 조정](#performance-and-scale)을 참조하세요.

- 잠재적인 비용을 확인하려면 [Azure 가격 계산기](https://azure.microsoft.com/pricing/calculator/)를 참조하세요.

    > [!NOTE]  
    > 가상 머신 비용은 지역에 따라 다릅니다.

#### <a name="outbound-data-transfer"></a>아웃바운드 데이터 전송

- 요금은 Azure에서 나가는 데이터(송신 또는 다운로드)를 기반으로 합니다. Azure에 들어오는 모든 데이터(수신 또는 업로드)는 비용이 청구되지 않습니다. Azure에서 나가는 CMG 데이터 흐름에는 CMG에서 사이트에 전달하는 클라이언트에 대한 정책, 클라이언트 알림 및 클라이언트 응답이 포함됩니다. 이러한 응답에는 인벤토리 보고서, 상태 메시지 및 규정 준수 상태가 포함되어 있습니다.  

- CMG와 통신하는 클라이언트가 없는 경우에도 일부 백그라운드 통신으로 인해 CMG와 온-프레미스 사이트 간에 네트워크 트래픽이 발생합니다.  

- Configuration Manager 콘솔에서 **아웃바운드 데이터 전송(GB)** 을 봅니다. 자세한 내용은 [CMG에서 클라이언트 모니터링](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway)을 참조하세요.  

- 잠재적인 비용을 확인하려면 [Azure 대역폭 가격 정보](https://azure.microsoft.com/pricing/details/bandwidth/)를 참조하세요. 데이터 전송에 대한 가격 책정은 계층화되어 있습니다. 많이 사용할수록 기가바이트당 지불하는 비용은 더 줄어 듭니다.  

- *예측 목적으로만* 인터넷 기반 클라이언트에 대해 매월 클라이언트당 약 100-300MB를 예상합니다. 기본 클라이언트 구성에 대해서는 더 낮은 값으로 예상되지만, 더 적극적인 클라이언트 구성에 대해서는 더 높은 값으로 예상됩니다. 실제 사용은 클라이언트 설정을 구성하는 방법에 따라 다를 수 있습니다.  

   > [!NOTE]  
   > 소프트웨어 업데이트 또는 응용 프로그램 배포와 같은 다른 작업을 수행하는 경우 Azure로부터의 아웃바운드 데이터 전송량이 늘어납니다.

#### <a name="content-storage"></a>콘텐츠 저장소

- 인터넷 기반 클라이언트는 Windows 업데이트에서 Microsoft 소프트웨어 업데이트 콘텐츠를 무료로 가져옵니다. Microsoft 업데이트 콘텐츠가 포함된 업데이트 패키지를 클라우드 배포 지점에 배포하지 마세요. 그렇지 않으면 저장소 및 데이터 송신 비용이 발생할 수 있습니다.  

- 응용 프로그램 또는 타사 소프트웨어 업데이트와 같이 필요한 다른 콘텐츠의 경우 클라우드 배포 지점에 배포해야 합니다. 현재 CMG는 클라이언트에 콘텐츠를 보내는 데 클라우드 배포 지점만 지원합니다.  

- 자세한 내용은 [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#bkmk_cost) 사용 비용을 참조하세요.  

- 버전 1806부터 CMG는 클라이언트에게 콘텐츠를 제공할 수 있습니다. 이 기능은 필요한 인증서 및 Azure VM 비용을 줄여줍니다. 자세한 내용은 [CMG 수정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg)을 참조하세요.<!--1358651-->  


#### <a name="other-costs"></a>기타 비용

- 각 클라우드 서비스에는 동적 IP 주소가 있습니다. 고유한 CMG는 각각 새 동적 IP 주소를 사용합니다. CMG당 추가 VM을 추가하더라도 이러한 주소는 증가하지 않습니다.  



## <a name="performance-and-scale"></a>성능 및 크기 조정

CMG 크기 조정에 대한 자세한 내용은 [크기 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)을 참조하세요.

CMG 성능을 향상시키는 데 도움이 될 수 있는 권장 사항은 다음과 같습니다.

- 가능한 경우 동일한 네트워크 영역에 CMG, CMG 연결점 및 Configuration Manager 사이트 서버를 구성하여 대기 시간을 줄입니다.  

- 현재 Configuration Manager 클라이언트와 CMG 간의 연결은 지역을 인식하지 못합니다.  

- 서비스의 고가용성을 위해 둘 이상의 CMG 서비스와 사이트당 2개의 CMG 연결 지점을 만듭니다.  

- 더 많은 VM 인스턴스를 추가하여 더 많은 클라이언트를 지원하도록 CMG 크기를 조정합니다. Azure 부하 분산 장치는 서비스에 대한 클라이언트 연결을 제어합니다.  

- 부하를 분산하기 위해 CMG 연결 지점을 추가로 만듭니다. CMG는 트래픽을 라운드 로빈 방식으로 연결된 CMG 연결 지점에 분산합니다.  

- 지원되는 클라이언트 수를 초과하여 CMG의 부하가 높은 경우에도 CMG에서 요청을 처리하지만 지연이 발생할 수 있습니다.  


> [!Note]  
> Configuration Manager에는 CMG 연결 지점의 클라이언트 수에 대한 하드 제한이 없지만, Windows Server에서는 기본 최대 TCP 동적 포트 범위가 16,384입니다. Configuration Manager 사이트에서 하나의 CMG 연결 지점으로 16,384개보다 많은 클라이언트를 관리하는 경우 Windows Server 제한을 늘려야 합니다. 모든 클라이언트는 CMG 연결 지점에서 열려 있는 포트를 보유하는 클라이언트 알림용 채널을 유지 관리합니다. netsh 명령을 사용하여 이 제한을 늘리는 방법에 대한 자세한 내용은 [Microsoft 지원 문서 929851](https://support.microsoft.com/help/929851)을 참조하세요.



## <a name="ports-and-data-flow"></a>포트 및 데이터 흐름

온-프레미스 네트워크에 대한 인바운드 포트는 열 필요가 없습니다. 서비스 연결 지점과 CMG 연결 지점은 Azure 및 CMG와의 모든 통신을 시작합니다. 이러한 두 사이트 시스템 역할은 Microsoft 클라우드에 대한 아웃바운드 연결을 만들 수 있어야 합니다. 서비스 연결 지점은 Azure에서 서비스를 배포하고 모니터링하므로 온라인 모드여야 합니다. CMG 연결 지점은 CMG에 연결되어 CMG와 온-프레미스 사이트 시스템 역할 간의 통신을 관리합니다.

다음 다이어그램은 CMG에 대한 개념적인 기본 데이터 흐름입니다. ![CMG 데이터 흐름](media/cmg-data-flow.png)
   1. 서비스 연결 지점은 443 HTTPS 포트를 통해 Azure에 연결됩니다. Azure AD 또는 Azure 관리 인증서를 사용하여 인증합니다. 서비스 연결 지점은 CMG를 Azure에 배포합니다. CMG는 서버 인증 인증서를 사용하여 HTTPS 클라우드 서비스를 만듭니다.  

   2. CMG 연결 지점은 TCP-TLS 또는 HTTPS를 통해 Azure의 CMG에 연결됩니다. 열려 있는 연결을 유지하고 이후의 양방향 통신을 위한 채널을 작성합니다.   

   3. 클라이언트는 443 HTTPS 포트를 통해 CMG에 연결됩니다. Azure AD 또는 클라이언트 인증 인증서를 사용하여 인증합니다.  

   4. CMG는 기존 연결을 통해 클라이언트 통신을 온-프레미스 CMG 연결 지점으로 전달합니다. 인바운드 방화벽 포트를 열 필요가 없습니다.  

   5. CMG 연결 지점은 클라이언트 통신을 온-프레미스 관리 지점 및 소프트웨어 업데이트 지점으로 전달합니다.  

### <a name="required-ports"></a>필요한 포트
다음 표에는 필요한 네트워크 포트와 프로토콜이 나열되어 있습니다. *클라이언트*는 아웃바운드 포트가 필요한 연결을 시작하는 장치입니다. *서버*는 인바운드 포트가 필요한 연결을 수락하는 장치입니다. 

| 클라이언트  | 프로토콜 | 포트  | 서버  | 설명  |
|---------|---------|---------|---------|---------|
| 서비스 연결 지점     | HTTPS | 443        | Azure        | CMG 배포 |
| CMG 연결 지점     |  TCP-TLS | 10140-10155        | CMG 서비스        | CMG 채널을 작성하기 위한 기본 설정 프로토콜<sup>1</sup> |
| CMG 연결 지점     | HTTPS | 443        | CMG 서비스       | 하나의 VM 인스턴스에만 CMG 채널을 작성하기 위한 대체(fallback)<sup>2</sup> |
| CMG 연결 지점     |  HTTPS   | 10124-10139     | CMG 서비스       | 둘 이상의 VM 인스턴스에 CMG 채널을 작성하기 위한 대체(fallback)<sup>3</sup> |
| 클라이언트     |  HTTPS | 443         | CMG        | 일반 클라이언트 통신 |
| CMG 연결 지점      | HTTPS 또는 HTTP | 443 또는 80         | 관리 지점<br>(1706 또는 1710 버전) | 온-프레미스 트래픽, 포트는 관리 지점 구성에 따라 달라집니다. |
| CMG 연결 지점      | HTTPS | 443      | 관리 지점<br>(1802 버전) | 온-프레미스 트래픽은 HTTPS여야 합니다. |
| CMG 연결 지점      | HTTPS 또는 HTTP | 443 또는 80         | 소프트웨어 업데이트 지점 | 온-프레미스 트래픽, 포트는 소프트웨어 업데이트 지점 구성에 따라 달라집니다. |

<sup>1</sup> CMG 연결 지점은 먼저 각 CMG VM 인스턴스와 함께 수명이 긴 TCP-TLS 연결을 설정하려고 합니다. 10140 포트의 첫 번째 VM 인스턴스에 연결합니다. 두 번째 VM 인스턴스는 10141 포트(10155 포트의 16번째 VM 인스턴스까지)를 사용합니다. TCP TLS 연결이 최상의 성능을 제공하지만 인터넷 프록시는 지원하지 않습니다. CMG 연결 지점에서 TCP-TLS를 통해 연결할 수 없는 경우 HTTPS로 대체합니다.<sup>2</sup>  

<sup>2</sup> CMG 연결 지점에서 TCP-TLS<sup>1</sup>를 통해 CMG에 연결할 수 없는 경우, 하나의 VM 인스턴스에 대해서만 443 HTTPS 포트를 통해 Azure 네트워크 부하 분산 장치에 연결합니다.  

<sup>3</sup> 둘 이상의 VM 인스턴스가 있는 경우, CMG 연결 지점에서 443 HTTPS 포트가 아니라 10124 HTTPS 포트를 첫 번째 VM 인스턴스에 사용합니다. 10125 HTTPS 포트에서 두 번째 VM 인스턴스에(10139 HTTPS 포트의 16번째 VM 인스턴스까지) 연결합니다.


### <a name="internet-access-requirements"></a>인터넷 액세스 요구 사항

CMG 연결 지점 사이트 시스템은 웹 프록시 사용을 지원합니다. 프록시에 대해 이 역할을 구성하는 방법에 대한 자세한 내용은 [프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support#to-set-up-the-proxy-server-for-a-site-system-server)을 참조하세요. CMG 연결 지점에서 연결해야 하는 엔드포인트는 다음과 같습니다.  

- 특정 Azure 엔드포인트는 환경 및 구성에 따라 다릅니다. Configuration Manager는 이러한 엔드포인트를 사이트 데이터베이스에 저장합니다. SQL Server의 **AzureEnvironments** 테이블에서 Azure 엔드포인트 목록을 쿼리합니다.  

- ServiceManagementEndpoint(https://management.core.windows.net/)  

- StorageEndpoint(core.windows.net)  

- Configuration Manager 콘솔 및 클라이언트에서 Azure AD 토큰을 검색하는 경우: ActiveDirectoryEndpoint(https://login.microsoftonline.com/)  

- Azure AD 사용자를 검색하는 경우: AAD Graph 엔드포인트(https://graph.windows.net/)  



## <a name="next-steps"></a>다음 단계

- [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이 크기 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
- [클라우드 관리 게이트웨이에 대한 FAQ](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
