---
title: "클라우드 관리 게이트웨이 계획 | Microsoft Docs"
description: 
ms.date: 06/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: a7380ae781447880ffcba0778694ea62e10c4889
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Configuration Manager에서 클라우드 관리 게이트웨이 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1610부터 클라우드 관리 게이트웨이는 인터넷에서 Configuration Manager 클라이언트를 관리할 수 있는 간단한 방법을 제공합니다. 클라우드 관리 게이트웨이 서비스의 경우 Microsoft Azure에 배포되고 Azure 구독이 필요합니다. 이 서비스는 클라우드 관리 게이트웨이 연결점이라는 새 역할을 사용하여 온-프레미스 Configuration Manager 인프라에 연결합니다. 배포되고 구성된 클라이언트는 내부 개인 네트워크 또는 인터넷에 연결되었는지 여부에 관계없이 온-프레미스 Configuration Manager 사이트 시스템 역할에 액세스할 수 있습니다.

> [!TIP]  
> 버전 1610에 도입된 클라우드 관리 게이트웨이는 시험판 기능입니다. 사용하도록 설정하려면 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

Configuration Manager 콘솔을 사용하여 Azure에 서비스를 배포하고 클라우드 관리 게이트웨이 연결점 역할을 추가하고 클라우드 관리 게이트웨이 트래픽을 허용하도록 사이트 시스템 역할을 구성합니다. 클라우드 관리 게이트웨이는 현재 관리 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.

컴퓨터를 인증하고 서비스의 다른 계층 간 통신을 암호화하려면 클라이언트 인증서 및 SSL(Secure Socket Layer) 인증서가 필요합니다. 클라이언트 컴퓨터는 일반적으로 그룹 정책 적용을 통해 클라이언트 인증서를 받습니다. 역할을 호스트하는 사이트 시스템 서버와 클라이언트 간의 트래픽을 암호화하려면 CA에서 사용자 지정 SSL 인증서를 만들어야 합니다. Configuration Manager에서 클라우드 관리 게이트웨이 서비스를 배포할 수 있도록 Azure에 관리 인증서도 설정해야 합니다.

## <a name="requirements-for-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 요구 사항

-   클라이언트 컴퓨터 및 클라우드 관리 게이트웨이 연결점을 실행하는 사이트 시스템 서버

-   클라이언트 컴퓨터에서 통신 암호화 및 클라우드 관리 게이트웨이 서비스의 ID 인증에 사용되는 내부 CA의 사용자 지정 SSL 인증서

-   클라우드 서비스에 대한 Azure 구독

-   Azure에서 Configuration Manager 인증에 사용되는 Azure 관리 인증서

## <a name="specifications-for-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 사양

- 클라우드 관리 게이트웨이의 각 인스턴스는 클라이언트 4,000개를 지원합니다.
- 가용성을 향상하려면 클라우드 관리 게이트웨이의 인스턴스를 두 개 이상 만드는 것이 좋습니다.
- 클라우드 관리 게이트웨이는 관리 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.
-   Configuration Manager의 다음 기능은 현재 클라우드 관리 게이트웨이에 대해 지원되지 않습니다.

    -   클라이언트 배포
    -   자동 사이트 할당
    -   사용자 정책
    -   응용 프로그램 카탈로그(소프트웨어 승인 요청 포함)
    -   전체 OSD(운영 체제 배포)
    -   Configuration Manager 콘솔
    -   원격 도구
    -   보고 웹 사이트
    -   Wake on LAN
    -   Mac, Linux 및 UNIX 클라이언트
    -   Azure Resource Manager
    -   피어 캐시
    -   온-프레미스 모바일 장치 관리

## <a name="cost-of-cloud-management-gateway"></a>클라우드 관리 게이트웨이 비용

>[!IMPORTANT]
>아래에 제공된 비용 정보는 평가 목적으로만 사용됩니다. 사용자 환경에 클라우드 관리 게이트웨이 사용의 전체 비용에 영향을 주는 다른 변수가 있을 수 있습니다.

클라우드 관리 게이트웨이는 Azure 구독 계정에 요금이 부과되는 다음 Microsoft Azure 기능을 사용합니다.

-   가상 컴퓨터

    -   클라우드 관리 게이트웨이에는 현재 Standard\_A2 가상 컴퓨터가 필요합니다. 서비스를 만들 때 서비스를 지원할 VM 수를 선택할 수 있습니다.

    -   예측 목적으로만, 단일 Azure Standard\_A2 가상 컴퓨터에서 약 2,000대의 동시 인터넷 기반 클라이언트를 지원할 수 있다고 추정합니다.

    -   잠재적인 비용을 확인하려면 [Azure 가격 계산기](https://azure.microsoft.com/en-us/pricing/calculator/)를 참조하세요.

      >[!NOTE]
      >가상 컴퓨터 비용은 지역에 따라 다릅니다.

-   아웃바운드 데이터 전송

    -   서비스에서 전송되는 데이터 흐름에 대해 비용이 청구됩니다. 잠재적인 비용을 확인하려면 [Azure 대역폭 가격 정보](https://azure.microsoft.com/en-us/pricing/details/bandwidth/)를 참조하세요.

    -   예측 목적으로만, 매시간 정책 새로 고침을 수행하는 인터넷 기반 클라이언트의 경우 월별 클라이언트당 약 100MB를 추정합니다.

    >[!NOTE]
    > 클라우드 관리 게이트웨이를 통해 지원되는 다른 작업(예: 소프트웨어 업데이트 또는 응용 프로그램 배포)을 수행하면 Azure에서 아웃바운드 데이터 전송량이 증가합니다.

-   콘텐츠 저장소

    -   클라우드 관리 게이트웨이를 사용하여 관리되는 인터넷 기반 클라이언트는 비용 없이 Windows 업데이트에서 소프트웨어 업데이트 콘텐츠를 가져옵니다.

    -   기타 필요한 콘텐츠(예: 응용 프로그램)는 클라우드 기반 배포 지점에 배포해야 합니다. 현재 클라우드 관리 게이트웨이는 클라우드 배포 지점만 클라이언트에 콘텐츠를 보낼 수 있도록 지원합니다.

    - 자세한 내용은 [클라우드 기반 배포](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) 사용에 대한 비용 계획을 참조하세요.

## <a name="frequently-asked-questions-about-the-cloud-management-gateway-cmg"></a>CMG(클라우드 관리 게이트웨이)에 대한 FAQ(질문과 대답)

### <a name="why-use-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이를 사용하는 이유

이 역할을 사용하여 Configuration Manager 콘솔에서 인터넷 기반 클라이언트 관리를 3단계로 간소화합니다.

1. [클라우드 관리 게이트웨이 만들기](/sccm/core/clients/manage/setup-cloud-management-gateway) 마법사를 사용하여 CMG를 Azure에 배포합니다.
2. [클라우드 관리 게이트웨이 연결 지점](/sccm/core/servers/deploy/configure/install-site-system-roles) 사이트 시스템 역할을 구성합니다.
3. 관리 지점 및 소프트웨어 업데이트 지점과 같은 [클라우드 관리 게이트웨이 트래픽에 대한 역할을 구성](/sccm/core/clients/manage/setup-cloud-management-gateway#step-7-configure-roles-for-cloud-management-gateway-traffic)합니다.

### <a name="how-does-the-cloud-management-gateway-work"></a>클라우드 관리 게이트웨이 작동 방식

- 클라우드 관리 게이트웨이 연결 지점을 사용하여 인터넷에서 클라우드 관리 게이트웨이로 일관되고 성능이 뛰어나 연결을 설정할 수 있습니다.
- Configuration Manager는 연결 정보 및 보안 설정을 비롯한 설정을 CMG에 게시합니다.
- CMG는 Configuration Manager 클라이언트 요청을 인증하고 클라우드 관리 게이트웨이 연결 지점으로 전달합니다. 이러한 요청은 URL 매핑에 따라 회사 네트워크의 역할에 전달됩니다.

### <a name="how-is-the-cloud-management-gateway-deployed"></a>클라우드 관리 게이트웨이 배포 방식

서비스 연결 지점의 클라우드 서비스 관리자 구성 요소는 모든 CMG 배포 작업을 처리합니다. 또한 Azure AD의 서비스 상태 및 로깅 정보를 모니터링하고 보고합니다.

#### <a name="certificate-requirements"></a>인증서 요구 사항

CMG를 보호하려면 다음 인증서가 필요합니다.

- **관리 인증서** - 자체 서명된 인증서를 포함하는 어떤 인증서도 될 수 있습니다. Azure AD에 업로드된 공용 인증서 또는 Configuration Manager로 가져온 [개인 키와 PFX](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)를 사용하여 Azure AD에서 인증을 받을 수 있습니다.
- **웹 서비스 인증서** - 공용 CA 인증서를 사용하여 클라이언트의 네이티브 신뢰를 얻는 것이 좋습니다. 공용 DNS 등록자에서 CName을 만들 수 있어야 합니다. 와일드카드 인증서는 지원되지 않습니다.
- **CMG에 업로드된 루트/SubCA 인증서** - CMG는 클라이언트 PKI 인증서에 대해 전체 체인 유효성 검사를 수행해야 합니다. 클라이언트 PKI 인증서를 발급하기 위해 엔터프라이즈 CA를 사용하며 해당 루트 또는 하위 CA를 인터넷에서 사용할 수 없는 경우 CMG로 업로드해야 합니다.

#### <a name="deployment-process"></a>배포 프로세스

배포는 다음 두 단계로 진행됩니다.

- 클라우드 서비스 배포
    - [Azure 서비스 정의 스키마](https://msdn.microsoft.com/library/azure/ee758711.aspx)(csdef) 파일 업로드
    - [Azure 서비스 구성 스키마](https://msdn.microsoft.com/library/azure/ee758710.aspx)(cscfg) 파일 업로드
- Azure AD에 CMG 구성 요소 설정 및 IIS(인터넷 정보 서비스)에서 끝점, HTTP 처리기 및 서비스 구성

CMG의 구성을 변경하면 CMG로의 구성 배포가 시작됩니다.

### <a name="how-does-the-cloud-management-gateway-help-ensure-security"></a>클라우드 관리 게이트웨이가 보안에 도움을 주는 방식

CMG는 다음과 같은 방법으로 보안을 보장하는 데 도움이 됩니다.

- 내부 인증서 및 연결 ID를 사용하여 상호 SSL 인증을 비롯한 CMG 연결 지점에서의 연결을 수락하고 관리합니다.
- 클라이언트 요청 수락 및 전달
    - 클라이언트 PKI 인증서에 대한 상호 SSL을 사용하여 연결을 미리 인증합니다.
    - 인증서 신뢰 목록은 클라이언트 PKI 인증서의 루트를 확인합니다. 사이트 속성의 클라이언트에서 통신 설정에서 이 설정을 지정할 수 있습니다. 또한 클라이언트에 대한 관리 지점의 경우와 동일한 유효성 검사를 수행합니다.
    - 수신된 URL의 유효성을 검사합니다.
    - 수신된 URL을 필터링하여 연결하는 CMG 연결 지점이 URL 요청을 처리할 수 있는지를 확인합니다.  
    - 각 게시 끝점에 대해 콘텐츠 길이 검사를 수행합니다.
    - '라운드 로빈'을 사용하여 같은 사이트의 CMG 연결 지점 간에 부하를 분산합니다.

- CMG 연결 지점을 보호합니다.
    - 연결 CMG의 모든 가상 인스턴스에 대해 일관된 HTTP/TCP 연결을 설정합니다. 1분마다 연결을 확인하고 유지 관리합니다.
    - 내부 인증서를 사용하여 CMG와의 SSL 인증을 상호 인증합니다.
    - URL 매핑을 기반으로 HTTP 요청을 전달합니다.
    - 연결 상태를 보고하여 관리 서비스 상태를 표시합니다.
    - 5분마다 끝점 기준으로 끝점 트래픽 보고서를 보고합니다.

- 관리 지점과 같이 게시하는 끝점 Configuration Manager 클라이언트 연결 역할과 클라이언트 요청을 처리하기 위한 IIS의 소프트웨어 업데이트 지점 호스트 끝점을 보호합니다. CMG에 게시된 모든 끝점에는 URL 매핑이 있습니다.
외부 URL은 클라이언트에서 CMG와 통신하기 위해 사용합니다.
내부 URL은 내부 서버에 요청을 전달하는 데 사용되는 CMG 연결 지점입니다.

#### <a name="example"></a>예:
관리 지점에서 CMG 트래픽을 사용하도록 설정하면 Configuration Manager는 ccm_system, ccm_incoming, sms_mp 같은 각 관리 지점 서버에 대해 내부적으로 URL 매핑 집합을 만듭니다.
관리 지점 ccm_system 끝점에 대한 외부 URL은 **https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System**과 같습니다.
URL은 각 관리 지점에 대해 고유합니다. 그런 후 Configuration Manager 클라이언트 **<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>** 같은 CMG 지원 MP 이름을 인터넷 관리 지점 목록에 추가합니다.
게시된 모든 외부 URL은 CMG에 자동으로 업로드되고, CMG에서 URL 필터링을 수행할 수 있게 됩니다. 모든 URL 매핑은 CMG 연결 지점에 복제되므로 외부 URL을 요청하는 클라이언트에 따라 내부 서버에 전달될 수 있습니다.

### <a name="what-ports-are-used-by-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 사용되는 포트

- 온-프레미스 네트워크에 필요한 인바운드 포트는 없습니다. CMG를 배포하면 CMG 집합이 자동으로 만들어집니다.
- 443 외에, CMG 연결 지점에 일부 아웃바운드 포트가 필요합니다.

|||||
|-|-|-|-|
|데이터 흐름|서버|서버 포트|클라이언트|
|CMG 배포|Azure|443|Configuration Manager 서비스 연결 지점|
|CMG 채널 구축|CMG|VM 인스턴스: 1 포트: 443<br>VM 인스턴스: N (N>=2 및 N<= 16) 포트: 10124~N 10140~N|CMG 연결 지점|
|클라이언트-CMG|CMG|443|클라이언트|
|사이트 역할에 대한 CMG 커넥터(현재 관리 지점 및 소프트웨어 업데이트 지점)|사이트 역할|사이트 역할에 대해 구성된 프로토콜/포트|CMG 연결 지점|

### <a name="how-can-you-improve-performance-of-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이의 성능을 향상시키는 방법

- 가능한 경우 동일한 네트워크 영역에 CMG, CMG 연결 지점 및 Configuration Manager 사이트 서버를 구성하여 대기 시간을 줄입니다.
- 현재 Configuration Manager 클라이언트와 CMG 간의 연결은 영역을 인식하지 않습니다.
- 고가용성을 확보하려면 사이트당 CMG의 가상 인스턴스 2개 이상과 CMG 연결 지점 2개 이상을 유지하는 것이 좋습니다.
- VM 인스턴스를 더 추가하여 더 많은 클라이언트를 지원하도록 CMG를 확장할 수 있습니다. Azure AD 부하 분산 장치를 통해 부하가 분산됩니다.
- 부하를 분산하기 위해 CMG 연결 지점을 추가로 만듭니다. CMG는 연결하는 CMG 연결 지점으로 트래픽을 ‘라운드 로빈’합니다.
- CMG VM 인스턴스당 지원 클라이언트 수는 1702 릴리스에서 6,000입니다. CMG 채널 부하가 높은 경우 요청은 계속 처리되지만 평소보다 오래 걸릴 수 있습니다.

### <a name="how-can-you-monitor-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이를 모니터링하는 방법

배포 문제 해결을 위해서는 **CloudMgr.log** 및 **CMGSetup.log**를 사용합니다.
서비스 상태 문제 해결에는 **CMGService.log** 및 **SMS_CLOUD_PROXYCONNECTOR.log**를 사용합니다.
클라이언트 트래픽 문제 해결에는 **CMGHttpHandler.log**, **CMGService.Log** 및 **SMS_CLOUD_PROXYCONNECTOR.log**를 사용합니다.

모든 CMG 관련 로그 파일 목록을 보려면 [Configuration Manager의 로그 파일](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)을 참조하세요.

## <a name="next-steps"></a>다음 단계

[클라우드 관리 게이트웨이 설정](setup-cloud-management-gateway.md)
