---
title: 클라우드 배포 지점
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라우드 배포 지점을 사용하여 Microsoft Azure를 통해 소프트웨어 콘텐츠를 배포하기 위한 계획과 디자인입니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3cd9c725-6b42-427d-9191-86e67f84e48c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 00c04190b954a7b19d4bea0e43b2dc6ecf9d8388
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53414993"
---
# <a name="use-a-cloud-distribution-point-in-configuration-manager"></a>Configuration Manager에서 클라우드 배포 지점 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

클라우드 배포 지점은 Microsoft Azure에서 PaaS(Platform-as-a-Service)로 호스팅되는 Configuration Manager 배포 지점입니다. 이 서비스에서 지원하는 시나리오는 다음과 같습니다.  

- 추가 온-프레미스 인프라 없이 인터넷 기반 클라이언트에 소프트웨어 콘텐츠 제공  

- 클라우드에서 콘텐츠 배포 시스템 지원  

- 기존 배포 지점에 대한 필요성 감소  


이 문서에서는 클라우드 배포 지점에 대해 알아보고, 사용을 계획하고, 구현을 설계합니다. 여기에는 다음과 같은 섹션이 포함됩니다.
- [기능 및 이점](#bkmk_features)
- [토폴로지 디자인](#bkmk_topology)
- [Requirements](#bkmk_requirements)
- [사양](#bkmk_spec)
- [비용](#bkmk_cost)
- [성능 및 크기 조정](#bkmk_perf)
- [포트 및 데이터 흐름](#bkmk_dataflow)
- [인증서](#bkmk_certs)
- [질문과 대답(FAQ)](#bkmk_faq)



## <a name="bkmk_features"></a> 기능 및 이점

### <a name="features"></a>기능

클라우드 배포 지점은 온-프레미스 배포 지점에서도 제공하는 몇 가지 기능을 지원합니다.  

-   클라우드 배포 지점을 개별적으로 또는 배포 지점 그룹의 구성원으로 관리합니다.  

-   클라우드 배포 지점을 대체 콘텐츠 위치로 사용합니다.  

-   인트라넷 및 인터넷 기반 클라이언트를 모두 지원합니다.  


### <a name="benefits"></a>이점

클라우드 배포 지점에서 추가로 제공하는 이점은 다음과 같습니다.  

-   사이트에서 콘텐츠를 Azure의 클라우드 배포 지점으로 보내기 전에 암호화합니다.  

-   클라이언트에서 변화하는 콘텐츠 요청 요구 사항을 충족하기 위해 Azure에서 클라우드 서비스의 크기를 수동으로 조정합니다. 이 경우 Configuration Manager에 추가 배포 지점을 설치하고 프로비전할 필요가 없습니다.  

-   Windows BranchCache 및 대체 콘텐츠 공급자와 같은 다른 콘텐츠 기술에 대해 구성된 클라이언트에서 콘텐츠 다운로드를 지원합니다.  

-   1806 버전부터 클라우드 배포 지점을 풀(pull) 배포 지점에 대한 원본 위치로 사용합니다.  


## <a name="bkmk_topology"></a> 토폴로지 디자인

클라우드 배포 지점의 배포 및 작동에 필요한 구성 요소는 다음과 같습니다.  

- Azure의 **클라우드 서비스**입니다. 사이트에서 이 서비스에 콘텐츠를 배포하며, 해당 콘텐츠는 Azure 클라우드 저장소에 저장됩니다. 관리 지점은 사용 가능한 원본 목록에서 이 콘텐츠 위치를 클라이언트에 적절하게 제공합니다.  

- **관리 지점** 사이트 시스템 역할에서 정상적인 각 클라이언트 요청을 처리합니다.  

    - 온-프레미스 클라이언트는 일반적으로 온-프레미스 관리 지점을 사용합니다.  

    - 인터넷 기반 클라이언트는 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway) 또는 [인터넷 기반 관리 지점](/sccm/core/clients/manage/plan-internet-based-client-management)을 사용합니다.  

- 클라우드 배포 지점에서 **인증서 기반 HTTPS** 웹 서비스를 사용하여 클라이언트와의 네트워크 통신을 보호합니다. 클라이언트는 이 인증서를 신뢰해야 합니다.  


### <a name="azure-resource-manager"></a>Azure Resource Manager
<!--1322209--> 1806 버전부터 **Azure Resource Manager 배포**를 사용하여 클라우드 배포 지점을 만듭니다. [Azure Resource Manager](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview)는 모든 솔루션 리소스를 [리소스 그룹](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-overview#resource-groups)이라는 단일 엔터티로 관리하기 위한 최신 플랫폼입니다. Azure Resource Manager로 클라우드 배포 지점을 배포하는 경우 사이트에서 Azure AD(Azure Active Directory)를 사용하여 필요한 클라우드 리소스를 인증하고 만듭니다. 이 최신 배포에는 클래식 Azure 관리 인증서가 필요하지 않습니다.  

> [!Note]  
> 이 기능은 Azure CSP(클라우드 서비스 공급자)를 지원하지 않습니다. Azure Resource Manager를 통한 클라우드 배포 지점 배포는 CSP에서 지원하지 않는 클래식 클라우드 서비스를 계속 사용합니다. 자세한 내용은 [Azure CSP에서 사용 가능한 Azure 서비스](/azure/cloud-solution-provider/overview/azure-csp-available-services)를 참조하세요.  

Azure 관리 인증서를 사용하는 **클래식 서비스 배포** 옵션도 클라우드 배포 지점 마법사에서 계속 제공됩니다. 리소스의 배포 및 관리를 간소화하려면 모든 새 클라우드 배포 지점에 Azure Resource Manager 배포 모델을 사용하는 것이 좋습니다. 가능하면 Resource Manager를 통해 기존 클라우드 배포 지점을 재배포합니다.

> [!Important]  
> 1810 버전부터 Azure의 클래식 서비스 배포는 Configuration Manager에서 사용되지 않습니다. 이 버전은 이러한 Azure 배포의 만들기를 지원하는 마지막 버전입니다. 이 기능은 2019년 7월 1일 이후 릴리스된 첫 번째 Configuration 매니저 버전에서 제거됩니다. 이 시간 전에 CMG 및 클라우드 배포 지점을 Azure Resource Manager 배포로 이동합니다. <!--SCCMDocs-pr issue #2993-->  

Configuration Manager는 기존 클래식 클라우드 배포 지점을 Azure Resource Manager 배포 모델로 마이그레이션하지 않습니다. Azure Resource Manager 배포를 사용하여 새 클라우드 배포 지점을 만든 다음, 클래식 클라우드 배포 지점을 제거합니다. 


### <a name="hierarchy-design"></a>계층 디자인

클라우드 배포 지점을 만드는 위치는 해당 콘텐츠에 액세스해야 하는 클라이언트에 따라 달라집니다. 1806 버전부터 클라우드 배포 지점에는 다음 세 가지 유형이 있습니다.  

- 클래식 서비스 배포: 기본 사이트에서만 이 유형을 만듭니다.  

- Azure Resource Manager 배포: 기본 사이트 또는 중앙 관리 사이트에서 이 유형을 만듭니다.  

- 클라우드 관리 게이트웨이에서 클라이언트에 콘텐츠를 제공할 수도 있습니다. 이 기능은 필요한 인증서 및 Azure VM 비용을 줄여줍니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.<!--1358651-->  


경계 그룹에 클라우드 배포 지점을 포함할지 여부를 결정하려면 다음 동작을 고려합니다.  

- 인터넷 기반 클라이언트는 경계 그룹을 사용하지 않는 대신, 인터넷 연결 배포 지점 또는 클라우드 배포 지점만 사용합니다. 이러한 유형의 클라이언트에 서비스를 제공하기 위해 클라우드 배포 지점만 사용하는 경우 해당 클라이언트가 경계 그룹에 포함될 필요가 없습니다.  

- 내부 네트워크의 클라이언트에서 클라우드 배포 지점을 사용하도록 하려면 클라이언트와 동일한 경계 그룹에 있어야 합니다. Azure에서 콘텐츠를 다운로드하는 데 드는 비용이 발생하므로 클라이언트는 콘텐츠 원본 목록의 마지막 클라우드 배포 지점에 높은 우선 순위를 지정합니다. 따라서 클라우드 배포 지점은 일반적으로 인트라넷 기반 클라이언트에 대한 대체 원본으로 사용됩니다. 클라우드 중심 디자인을 원하는 경우 이 비즈니스 요구 사항이 충족되도록 경계 그룹을 설계합니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups)을 참조하세요.  


Azure의 특정 지역에 클라우드 배포 지점을 설치하는 경우에도 클라이언트에서는 해당 Azure 지역을 인식하지 못하여 클라우드 배포 지점을 임의로 선택합니다. 클라우드 배포 지점을 여러 지역에 설치하고 클라이언트에서 콘텐츠 위치 목록에서 둘 이상의 클라우드 배포 지점을 받는 경우, 클라이언트는 동일한 Azure 지역의 클라우드 배포 지점을 사용하지 않을 수도 있습니다.  


### <a name="backup-and-recovery"></a>백업 및 복구  

계층 구조에서 클라우드 배포 지점을 사용할 때는 다음 정보를 사용하여 백업 및 복구를 계획합니다.  

- **백업 사이트 서버** 유지 관리 작업을 사용하는 경우 클라우드 배포 지점에 대한 구성이 Configuration Manager에 자동으로 포함됩니다.  

- 서버 인증 인증서의 복사본을 백업하고 저장합니다. Azure에서 클래식 서비스 배포를 사용하는 경우 Azure 관리 인증서의 복사본도 백업 및 저장됩니다. Configuration Manager 기본 사이트를 다른 서버에 복원할 때 해당 인증서를 다시 가져와야 합니다.  



##  <a name="bkmk_requirements"></a> 요구 사항

- 서비스를 호스팅하려면 **Azure 구독**이 필요합니다.  

    - **Azure 관리자**는 디자인에 따라 특정 구성 요소의 초기 생성에 참여해야 합니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요하지 않습니다.  

- 사이트 서버에는 클라우드 서비스를 배포하고 관리하기 위해 **인터넷 액세스** 권한이 필요합니다.  

- **Azure Resource Manager** 배포 방법을 사용하는 경우 Configuration Manager를 **클라우드 관리**용 [Azure AD](/sccm/core/servers/deploy/configure/azure-services-wizard)와 통합합니다. Azure AD *사용자 검색*은 필요하지 않습니다.  

- Azure 클래식 배포 방법을 사용하는 경우 **Azure 관리 인증서**가 필요합니다. 자세한 내용은 아래 [인증서](#bkmk_certs) 섹션을 참조하세요.   

    > [!TIP]  
    > Configuration Manager 버전 1806부터 **Azure Resource Manager** 배포 모델을 사용합니다. 이 배포 모델에는 관리 인증서가 필요하지 않습니다.  
    > 
    > 클래식 배포 메서드는 1810 버전을 기준으로 사용되지 않습니다.   

- **서버 인증 인증서**가 필요합니다. 자세한 내용은 아래 [인증서](#bkmk_certs) 섹션을 참조하세요.  

    - 복잡성을 줄이려면 서버 인증 인증서에 대한 공용 인증서 공급자를 사용하는 것이 좋습니다. 이렇게 하면 클라이언트에서 클라우드 서비스의 이름을 확인하기 위해 **DNS CNAME 별칭**도 필요합니다.  

- **클라우드 서비스** 그룹에서 **클라우드 배포 지점에 대한 액세스 허용** 클라이언트 설정을 **예**로 설정합니다. 기본적으로 이 값은 **아니요**로 설정되어 있습니다.  

- 클라이언트 디바이스에는 **인터넷 연결**이 필요하며 **IPv4**를 사용해야 합니다.  



## <a name="bkmk_spec"></a> 사양

- 클라우드 배포 지점은 [클라이언트 및 디바이스에 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)에 나와 있는 모든 Windows 버전을 지원합니다.  

- 관리자는 다음 유형의 지원되는 소프트웨어 콘텐츠를 배포합니다.  
  - 애플리케이션
  - 패키지
  - OS 업그레이드 패키지
  - 타사 소프트웨어 업데이트  

    > [!Important]  
    > Configuration Manager 콘솔은 클라우드 배포 지점에 Microsoft 소프트웨어 업데이트를 배포하는 것을 차단하지 않지만, 클라이언트에서 사용하지 않는 콘텐츠를 저장하는 데 드는 Azure 비용은 지불해야 합니다. 인터넷 기반 클라이언트는 항상 Microsoft 업데이트 클라우드 서비스에서 Microsoft 소프트웨어 업데이트 콘텐츠를 가져옵니다. Microsoft 소프트웨어 업데이트는 클라우드 배포 지점에 배포하지 마세요.    

- 1806 버전부터 클라우드 배포 지점을 원본으로 사용하도록 풀(pull) 배포 지점을 구성합니다. 자세한 내용은 [원본 배포 지점 정보](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point#about-source-distribution-points) 섹션을 참조하세요.<!--1321554-->  


### <a name="deployment-settings"></a>배포 설정

- **작업 순서를 실행하기 전에 콘텐츠를 로컬에 다운로드** 옵션을 사용하여 작업 순서를 배포하면 관리 지점에 클라우드 배포 지점이 콘텐츠 위치로 포함되지 않습니다. 클라이언트에서 클라우드 배포 지점을 사용할 수 있도록 **작업 순서를 시작하기 전에 모든 콘텐츠를 로컬에 다운로드** 옵션을 사용하여 작업 순서를 배포합니다.  

- 클라우드 배포 지점은 **배포 지점에서 프로그램 실행** 옵션을 사용하는 패키지 배포를 지원하지 않습니다. **배포 지점에서 콘텐츠를 다운로드하여 로컬로 실행** 배포 옵션을 사용합니다.  


### <a name="limitations"></a>제한 사항  

- 클라우드 배포 지점은 PXE 또는 멀티캐스트 사용 배포에 사용할 수 없습니다.  

- 클라우드 배포 지점은 App-V 스트리밍 애플리케이션을 지원하지 않습니다.  

- 클라우드 배포 지점에서 [콘텐츠를 사전 준비](/sccm/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent)할 수 없습니다. 클라우드 배포 지점을 관리하는 기본 사이트의 배포 관리자에서 모든 콘텐츠를 전송합니다.  

- 클라우드 배포 지점은 풀(pull) 배포 지점으로 구성할 수 없습니다.  



##  <a name="bkmk_cost"></a> 비용   
<!--501018-->
> [!IMPORTANT]  
> 다음 비용 정보는 평가 목적으로만 사용됩니다. 사용자 환경에는 클라우드 배포 지점을 사용하는 데 드는 전체 비용에 영향을 주는 다른 변수가 있을 수 있습니다.  

Configuration Manager에는 비용을 제어하고 데이터 액세스를 모니터링할 수 있는 다음과 옵션이 있습니다.  

- 클라우드 서비스에 저장하는 콘텐츠의 양을 제어하고 모니터링합니다. 자세한 내용은 [클라우드 배포 지점 모니터링](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure#bkmk_monitor)을 참조하세요.  

- 클라이언트 다운로드 임계값이 월간 한도에 도달하거나 이 한도를 초과하는 경우 사용자에게 경고하도록 Configuration Manager를 구성합니다. 자세한 내용은 [데이터 전송 임계값 경고](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure#bkmk_alerts)를 참조하세요.   

- 클라이언트가 클라우드 배포 지점에서 데이터를 전송하는 횟수를 줄이려면 다음 피어 캐싱 기술 중 하나를 사용합니다.  
  - Configuration Manager 피어 캐시
  - Windows BranchCache
  - Windows 10 배달 최적화  

    자세한 내용은 [콘텐츠 관리 관련 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)을 참조하세요.   


### <a name="components"></a>구성 요소

클라우드 배포 지점에서 사용하여 Azure 구독 계정에 요금이 청구되는 Azure 구성 요소는 다음과 같습니다.  

> [!Tip]  
> 1806 버전부터 클라우드 관리 게이트웨이에서도 콘텐츠를 클라이언트에 제공할 수 있습니다. 이 기능은 Azure VM을 통합하여 비용을 절감합니다. 자세한 내용은 [클라우드 관리 게이트웨이에 대한 비용](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#cost)을 참조하세요.  

#### <a name="virtual-machine"></a>가상 머신
- 클라우드 배포 지점은 Azure Cloud Services를 PaaS(Platform as a Service)로 사용합니다. 이 서비스는 컴퓨팅 비용이 발생하는 VM(가상 머신)을 사용합니다.  

- 각 클라우드 배포 지점 서비스는 두 개의 표준 A0 VM을 사용합니다.  

- 잠재적인 비용을 확인하려면 [Azure 가격 계산기](https://azure.microsoft.com/pricing/calculator/)를 참조하세요.

    > [!NOTE]  
    > 가상 머신 비용은 지역에 따라 다릅니다.

#### <a name="outbound-data-transfer"></a>아웃바운드 데이터 전송
- Azure로의 모든 데이터 흐름(수신 또는 업로드)은 추가 비용이 들지 않습니다. 콘텐츠를 사이트에서 클라우드 배포 지점으로 배포하는 경우 해당 콘텐츠는 Azure에 업로드됩니다.  

- 요금은 Azure에서 나가는 데이터(송신 또는 다운로드)를 기반으로 합니다. Azure에서 클라우드 배포 지점으로의 데이터 흐름은 클라이언트에서 다운로드하는 소프트웨어 콘텐츠로 구성됩니다.  

- 자세한 내용은 [클라우드 배포 지점 모니터링](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure#bkmk_monitor)을 참조하세요.  

- 잠재적인 비용을 확인하려면 [Azure 대역폭 가격 정보](https://azure.microsoft.com/pricing/details/bandwidth/)를 참조하세요. 데이터 전송에 대한 가격 책정은 계층화되어 있습니다. 많이 사용할수록 기가바이트당 지불하는 비용은 더 줄어 듭니다.  

#### <a name="content-storage"></a>콘텐츠 저장소
- 인터넷 기반 클라이언트는 추가 비용이 없이 Microsoft 업데이트 클라우드 서비스에서 Microsoft 소프트웨어 업데이트 콘텐츠를 가져옵니다. Microsoft 소프트웨어 업데이트가 포함된 소프트웨어 업데이트 배포 패키지를 클라우드 배포 지점에 배포하지 마세요. 그렇지 않으면 클라이언트에서 사용하지 않는 콘텐츠에 대한 데이터 저장소 비용이 발생합니다.  

- 클라우드 배포 지점에서 배포 모델에 따라 사용하는 표준 Blob 저장소는 다음과 같습니다.  

    - 클래식 배포에서는 Azure GRS(지역 중복 저장소)를 사용합니다. 자세한 내용은 [지역 중복 저장소](https://docs.microsoft.com/azure/storage/common/storage-redundancy-grs)를 참조하세요.  

    - Azure Resource Manager 배포에서는 Azure LRS(로컬 중복 저장소)를 사용합니다. 이렇게 변경하면 저장소 계정 비용이 절감됩니다. 클래식 배포에는 GRS의 추가 기능이 사용되지 않았습니다. 자세한 내용은 [로컬 중복 저장소](https://docs.microsoft.com/azure/storage/common/storage-redundancy-lrs)를 참조하세요.  

#### <a name="other-costs"></a>기타 비용
- 각 클라우드 서비스에는 동적 IP 주소가 있습니다. 각각의 고유 클라우드 배포 지점에서 새 동적 IP 주소를 사용합니다. 클라우드 서비스당 추가 VM을 추가하더라도 이러한 주소는 증가하지 않습니다.  



##  <a name="bkmk_dataflow"></a> 포트 및 데이터 흐름   

클라우드 배포 지점에는 다음 두 가지 기본 데이터 흐름이 있습니다.  

- 사이트 서버에서 Azure에 연결하여 클라우드 배포 지점 서비스를 설정합니다.  

- 클라이언트에서 클라우드 배포 지점에 연결하여 콘텐츠를 다운로드합니다.  


### <a name="site-server-to-azure"></a>사이트 서버에서 Azure에 연결

온-프레미스 네트워크에 대한 인바운드 포트는 열 필요가 없습니다. 사이트 서버에서 Azure 및 클라우드 배포 지점과의 모든 통신을 시작하여 클라우드 서비스를 배포, 업데이트 및 관리합니다. 사이트 서버에서 Microsoft 클라우드에 대한 아웃바운드 연결을 만들 수 있어야 합니다. 이 작업은 특정 사이트에 배포 지점 사이트 시스템 역할을 설치하는 작업과 동일합니다.  


### <a name="client-to-cloud-distribution-point"></a>클라이언트에서 클라우드 배포 지점에 연결

온-프레미스 네트워크에 대한 인바운드 포트는 열 필요가 없습니다. 인터넷 기반 클라이언트에서 Azure 서비스와 직접 통신합니다. 클라우드 배포 지점을 사용하는 내부 네트워크의 클라이언트에서 Microsoft 클라우드에 연결할 수 있어야 합니다. 

콘텐츠 위치 우선 순위 및 인트라넷 기반 클라이언트에서 클라우드 배포 지점을 사용하는 경우에 대한 자세한 내용은 [콘텐츠 원본 우선 순위](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#content-source-priority)를 참조하세요.

클라이언트에서 클라우드 배포 지점을 콘텐츠 위치로 사용하는 경우 다음과 같습니다.  

1. 관리 지점에서 콘텐츠 원본 목록과 함께 액세스 토큰을 클라이언트에 제공합니다. 이 토큰은 24시간 동안 유효하며, 클라우드 배포 지점에 액세스 권한을 클라이언트에 부여합니다.  

2. 관리 지점에서 클라우드 배포 지점의 **서비스 FQDN**을 사용하여 클라이언트의 위치 요청에 응답합니다. 이 속성은 서버 인증 인증서의 일반 이름과 동일합니다.  

    WallaceFalls.contoso.com과 같이 도메인 이름을 사용하는 경우 클라이언트는 먼저 이 FQDN을 확인하려고 시도합니다. Azure 서비스 이름을 확인하려면 클라이언트에 대한 도메인의 인터넷 연결 DNS에 CNAME 별칭이 필요합니다 (예: WallaceFalls.cloudapp.net).  

3. 다음으로, 클라이언트에서 Azure 서비스 이름(예: WallaceFalls.cloudapp.net)을 유효한 IP 주소로 확인합니다. 이 응답은 Azure의 DNS에서 처리해야 합니다.  

4. 클라이언트에서 클라우드 배포 지점에 연결합니다. Azure는 연결 부하를 VM 인스턴스 중 하나에 분산합니다. 클라이언트는 액세스 토큰을 사용하여 자체를 인증합니다.  

5. 클라우드 배포 지점에서 클라이언트의 액세스 토큰을 인증한 다음, Azure 저장소의 정확한 콘텐츠 위치를 클라이언트에 제공합니다.  

6. 클라이언트에서 클라우드 배포 지점의 서버 인증 인증서를 신뢰하면 Azure 저장소에 연결하여 콘텐츠를 다운로드합니다. 



##  <a name="bkmk_perf"></a> 성능 및 크기 조정   
<!--494872-->

배포 지점 디자인과 마찬가지로 다음 요소를 고려합니다.  
- 동시 클라이언트 연결 수
- 클라이언트에서 다운로드할 수 있는 콘텐츠의 크기
- 비즈니스 요구 사항이 충족될 수 있는 기간 

[토폴로지 디자인](#bkmk_topology)에 따라 클라이언트에서 지정된 콘텐츠에 대해 둘 이상의 클라우드 배포 지점을 선택할 수 있는 경우 이러한 클라우드 서비스 간에 자연스럽게 임의로 지정됩니다. 특정 콘텐츠를 단일 클라우드 배포 지점에만 배포하고 다수의 클라이언트에서 이 콘텐츠를 동시에 다운로드하려고 하는 경우 이 활동으로 인해 단일 클라우드 배포 지점에 더 많은 부하가 발생됩니다. 또한 추가 클라우드 배포 지점이 추가되면 별도의 Azure 저장소 서비스도 포함됩니다. 클라이언트에서 클라우드 배포 지점 구성 요소와 통신하고 콘텐츠를 다운로드하는 방법에 대한 자세한 내용은 [포트 및 데이터 흐름](#bkmk_dataflow)을 참조하세요.  

클라우드 배포 지점은 두 개의 Azure VM을 Azure 저장소의 프런트 엔드로 사용합니다. 고객 대부분의 요구 사항은 이 기본 배포에서 충족됩니다. 극단적인 일부 상황에서 많은 수의 클라이언트(예: 150,000개 클라이언트)가 동시에 연결되는 경우에는 Azure VM의 처리 용량이 이러한 클라이언트 요청을 따라갈 수 없습니다. 클라우드 배포 지점에 사용되는 Azure VM의 크기는 조정할 수 없습니다. Configuration Manager에서 클라우드 배포 지점의 VM 인스턴스 수를 구성할 수는 없지만, 필요한 경우 Azure Portal에서 클라우드 서비스를 다시 구성합니다. VM 인스턴스를 수동으로 더 많이 추가하거나 크기가 자동으로 조정되도록 서비스를 구성합니다. 

> [!Important]  
> Configuration Manager를 업데이트하면 사이트에서 클라우드 서비스를 다시 배포합니다. Azure Portal에서 클라우드 서비스를 수동으로 다시 구성하면 인스턴스 수가 기본값인 2로 다시 설정됩니다.  

Azure 저장소 서비스는 단일 파일에 대해 초당 500개의 요청을 지원합니다. 단일 클라우드 배포 지점의 성능 테스트에서 하나의 100MB 파일을 50,000개 클라이언트에 24시간 동안에 배포했습니다.<!--512106-->  



##  <a name="bkmk_certs"></a> 인증서  

클라우드 배포 지점 디자인에 따라 하나 이상의 디지털 인증서가 필요합니다.  


### <a name="general-information"></a>일반 정보
<!--SCCMDocs issue #779--> 클라우드 배포 지점에 대한 인증서는 다음 구성을 지원합니다.  

- **4096비트 키 길이**  

- 버전 1710부터는 **버전 3** 인증서를 지원합니다. 자세한 내용은 [CNG 인증서 개요](/sccm/core/plan-design/network/cng-certificates-overview)를 참조하세요.  

- 버전 1802부터 다음 정책을 사용하여 Windows를 구성합니다. **시스템 암호화: 암호화, 해시, 서명에 FIPS 규정 준수 알고리즘 사용**  

- 버전 1802부터는 **TLS 1.2**를 지원합니다. 자세한 내용은 [암호화 컨트롤 기술 참조](/sccm/core/plan-design/security/cryptographic-controls-technical-reference#about-ssl-vulnerabilities)를 참조하세요.  


### <a name="azure-management-certificate"></a>Azure 관리 인증서

*이 인증서는 클래식 서비스 배포에 필요하지만, Azure Resource Manager 배포에는 필요하지 않습니다.*

Azure 클래식 배포 방법을 사용하는 경우 **Azure 관리 인증서**가 필요합니다. 자세한 내용은 클라우드 관리 게이트웨이 인증서 문서의 [Azure 관리 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#azure-management-certificate) 섹션을 참조하세요. Configuration Manager 사이트 서버에서 이 인증서를 사용하여 Azure를 인증하여 클래식 배포를 만들고 관리합니다.  

> [!TIP]  
> Configuration Manager 버전 1806부터 **Azure Resource Manager** 배포 모델을 사용합니다. 이 배포 모델에는 관리 인증서가 필요하지 않습니다.  
> 
> 클래식 배포 메서드는 1810 버전을 기준으로 사용되지 않습니다.   

복잡성을 줄이려면 모든 Azure 구독 및 모든 Configuration Manager 사이트에서 클라우드 배포 지점 및 클라우드 관리 게이트웨이의 모든 클래식 배포에 동일한 Azure 관리 인증서를 사용합니다.


### <a name="server-authentication-certificate"></a>서버 인증 인증서

*이 인증서는 모든 클라우드 배포 지점 배포에 필요합니다.*

자세한 내용은 필요에 따라 [CMG 서버 인증 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-server-authentication-certificate) 및 다음 하위 섹션을 참조하세요.  
- 클라이언트에서 신뢰할 수 있는 CMG 루트 인증서
- 공용 공급자가 발급한 서버 인증 인증서
- 엔터프라이즈 PKI에서 발급한 서버 인증 인증서

클라우드 배포 지점은 클라우드 관리 게이트웨이와 동일한 방식으로 이 유형의 인증서를 사용합니다. 또한 클라이언트도 이 인증서를 신뢰해야 합니다. 복잡성을 줄이려면 공용 공급자가 발급한 인증서를 사용하는 것이 좋습니다. 

와일드카드 인증서를 사용하지 않는 한 동일한 인증서는 다시 사용하지 마세요. 클라우드 배포 지점 및 클라우드 관리 게이트웨이의 각 인스턴스에는 고유한 서버 인증 인증서가 필요합니다. 

PKI에서 이 인증서를 만드는 방법에 대한 자세한 내용은 [클라우드 배포 지점용 서비스 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012)를 참조하세요.  



##  <a name="bkmk_faq"></a> 질문과 대답(FAQ)   

### <a name="does-a-client-need-a-certificate-to-download-content-from-a-cloud-distribution-point"></a>클라우드 배포 지점에서 콘텐츠를 다운로드하려면 클라이언트에 인증서가 필요한가요?

클라이언트 인증 인증서는 필요하지 않습니다. 클라이언트는 클라우드 배포 지점에서 사용하는 서버 인증 인증서를 신뢰해야 합니다. 공용 인증서 공급자에서 이 인증서를 발급한 경우 대부분의 Windows 디바이스에는 이러한 공급자에 대해 신뢰할 수 있는 루트 인증서가 이미 포함되어 있습니다. 조직의 PKI에서 서버 인증 인증서를 발급한 경우 클라이언트는 전체 체인에 있는 발급 인증서를 신뢰해야 합니다. 이 체인에는 루트 인증 기관 및 모든 중간 인증 기관이 포함됩니다. PKI 디자인에 따라 이 인증서로 인해 클라우드 배포 지점의 배포에 복잡성이 추가로 발생할 수 있습니다. 이러한 복잡성을 방지하려면 클라이언트에서 이미 신뢰하는 공용 인증서 공급자를 사용하는 것이 좋습니다.  


### <a name="can-my-on-premises-clients-use-a-cloud-distribution-point"></a>온-프레미스 클라이언트에서 클라우드 배포 지점을 사용할 수 있나요?

예. 내부 네트워크의 클라이언트에서 클라우드 배포 지점을 사용하도록 하려면 클라이언트와 동일한 경계 그룹에 있어야 합니다. Azure에서 콘텐츠를 다운로드하는 데 드는 비용이 발생하므로 클라이언트는 콘텐츠 원본 목록의 마지막 클라우드 배포 지점에 높은 우선 순위를 지정합니다. 따라서 클라우드 배포 지점은 일반적으로 인트라넷 기반 클라이언트에 대한 대체 원본으로 사용됩니다. 클라우드 중심 디자인을 원하는 경우 이에 따라 경계 그룹을 설계합니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups)을 참조하세요.  


### <a name="do-i-need-azure-expressroute"></a>Azure ExpressRoute가 필요한가요?

[Azure ExpressRoute](/azure/expressroute/expressroute-introduction)를 통해 온-프레미스 네트워크를 Microsoft 클라우드로 확장할 수 있습니다. ExpressRoute 또는 이러한 다른 가상 네트워크 연결은 Configuration Manager 클라우드 배포 지점에 필요하지 않습니다.  

조직에서 ExpressRoute를 사용하는 경우 ExpressRoute를 사용하는 구독에서 클라우드 배포 지점에 대한 Azure 구독을 격리시킵니다. 이렇게 구성하면 클라우드 배포 지점에서 실수로 이 방식으로 연결되지 않도록 합니다.  


### <a name="do-i-need-to-maintain-the-azure-virtual-machines"></a>Azure 가상 머신을 유지 관리해야 하나요?

유지 관리가 필요하지 않습니다. 클라우드 배포 지점의 디자인은 Azure 플랫폼을 PaaS(Platform as a Service)로 사용합니다. Configuration Manager는 제공하는 구독을 사용하여 필요한 VM, 저장소 및 네트워킹을 만듭니다. Azure는 가상 머신을 보호하고 업데이트합니다. 이러한 VM은 IaaS(infrastructure as a service)의 경우처럼 온-프레미스 환경의 일부가 아닙니다. 클라우드 배포 지점은 Configuration Manager 환경을 클라우드로 확장하는 PaaS입니다. 자세한 내용은 [PaaS 클라우드 서비스 모델의 보안 이점](https://docs.microsoft.com/azure/security/security-paas-deployments#security-advantages-of-a-paas-cloud-service-model)을 참조하세요.  


### <a name="does-the-cloud-distribution-point-use-azure-cdn"></a>클라우드 배포 지점에서 Azure CDN을 사용하나요?

Azure CDN(Content Delivery Network)은 전 세계에 전략적으로 배치된 물리적 노드에서 콘텐츠를 캐시하여 고대역폭 콘텐츠를 빠르게 배달하기 위한 글로벌 솔루션입니다. 자세한 내용은 [Azure CDN이란?](https://docs.microsoft.com/azure/cdn/cdn-overview)을 참조하세요.

Configuration Manager 클라우드 배포 지점은 현재 Azure CDN을 지원하지 않습니다.



## <a name="next-steps"></a>다음 단계
[클라우드 배포 지점 설치](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure)
