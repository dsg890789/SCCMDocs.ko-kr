---
title: 클라이언트 설정
titleSuffix: Configuration Manager
description: 클라이언트 동작을 제어하기 위한 기본 및 사용자 지정 설정에 대해 알아봅니다.
ms.date: 08/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b272a8988a3e8d2e09b4043c087207e62c59b274
ms.sourcegitcommit: 5e7c4d36f4cdb3390ad3b381d31a3e1e4bf3c6e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/11/2019
ms.locfileid: "55986589"
---
# <a name="about-client-settings-in-configuration-manager"></a>Configuration Manager의 클라이언트 설정 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

**관리** 작업 영역에 있는 **클라이언트 설정** 노드에서 Configuration Manager 콘솔의 모든 클라이언트 설정을 관리합니다. Configuration Manager에는 기본 설정 집합이 포함되어 있습니다. 기본 클라이언트 설정을 변경하면 이러한 설정이 계층 구조의 모든 클라이언트에 적용됩니다. 또한 사용자 지정 클라이언트 설정을 구성할 수 있습니다. 사용자 지정 클라이언트 설정을 컬렉션에 할당하면 기본 클라이언트 설정이 재정의됩니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.

다음 섹션에서는 설정 및 옵션에 대해 자세히 설명합니다.  
 

## <a name="background-intelligent-transfer-service-bits"></a>BITS(Background Intelligent Transfer Service)  

### <a name="limit-the-maximum-network-bandwidth-for-bits-background-transfers"></a>BITS 백그라운드 전송의 최대 네트워크 대역폭 제한
이 옵션이 **예**인 경우 클라이언트에서는 BITS 대역폭 제한을 사용합니다. 이 그룹에서 다른 설정을 구성하려면 이 설정을 사용하도록 설정해야 합니다. 

### <a name="throttling-window-start-time"></a>제한 기간 시작 시간
BITS 제한 기간의 현지 시작 시간을 지정합니다.  

### <a name="throttling-window-end-time"></a>제한 기간 끝 시간
BITS 제한 기간의 현지 종료 시간을 지정합니다. 종료 시간이 **제한 기간 시작 시간**과 같을 경우 BITS 제한이 항상 사용됩니다.  

### <a name="maximum-transfer-rate-during-throttling-window-kbps"></a>제한 기간 내의 최대 전송 속도(Kbps)
클라이언트가 해당 기간 동안 사용할 수 있는 최대 전송 속도를 지정합니다.  

### <a name="allow-bits-downloads-outside-the-throttling-window"></a>제한 기간 외에 BITS 다운로드 허용
클라이언트가 지정된 기간 외에 별도의 BITS 설정을 사용하도록 허용합니다.  

### <a name="maximum-transfer-rate-outside-the-throttling-window-kbps"></a>제한 기간 외의 최대 전송 속도(Kbps)
BITS 제한 기간이 아닐 때 클라이언트가 사용할 수 있는 최대 전송률을 지정합니다.  



## <a name="client-cache-settings"></a>클라이언트 캐시 설정

### <a name="configure-branchcache"></a>BranchCache 구성
[Windows BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache)에 대해 클라이언트 컴퓨터를 설정합니다. 클라이언트에 대해 BranchCache 캐싱을 허용하려면 **BranchCache 사용**을 **예**로 설정합니다.

- **BranchCache 사용** </br>
    클라이언트 컴퓨터에서 BranchCache를 사용하도록 설정합니다.

- **최대 BranchCache 캐시 크기(디스크의 비율)** </br>
    BranchCache를 사용할 수 있는 디스크의 비율입니다. 

### <a name="configure-client-cache-size"></a>클라이언트 캐시 크기 구성
Windows 컴퓨터의 Configuration Manager 클라이언트 캐시에서 애플리케이션 및 프로그램 설치에 사용되는 임시 파일이 저장됩니다. 이 옵션을 **아니요**로 설정하는 경우 기본 크기는 5,120MB입니다.

**예**를 선택하는 경우 다음을 지정합니다.
- **최대 캐시 크기(MB)**
- **최대 캐시 크기(디스크의 비율)** </br>
클라이언트 캐시 크기가 MB(메가바이트) 또는 디스크에 대한 백분율 최댓값(둘 중 더 작은 크기)으로 확장됩니다. 

### <a name="enable-configuration-manager-client-in-full-os-to-share-content"></a>콘텐츠를 공유하도록 정품 OS에서 구성 관리자 클라이언트 사용
Configuration Manager 클라이언트에 대한 [피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)를 사용하도록 설정합니다. **예**를 선택한 다음, 클라이언트가 피어 컴퓨터와 통신하는 포트를 지정합니다. 
- **초기 네트워크 브로드캐스트를 위한 포트**(기본값 8004)
- **피어에서 콘텐츠를 다운로드하기 위한 포트**(기본값 8003) </br>
Configuration Manager는 이 트래픽을 허용하도록 자동으로 Windows 방화벽 규칙을 구성합니다. 다른 방화벽을 사용하는 경우 이 트래픽을 허용하도록 수동으로 포트를 구성해야 합니다.




## <a name="client-policy"></a>클라이언트 정책  

### <a name="client-policy-polling-interval-minutes"></a>클라이언트 정책 폴링 간격(분)

다음 Configuration Manager 클라이언트가 클라이언트 정책을 다운로드하는 빈도를 지정합니다.
-   Windows 컴퓨터(예: 데스크톱, 서버, 랩톱)  
-   Configuration Manager에서 등록된 모바일 디바이스  
-   Mac 컴퓨터  
-   Linux 또는 UNIX를 실행하는 컴퓨터  

### <a name="enable-user-policy-on-clients"></a>클라이언트에 대한 사용자 정책 사용

이 옵션을 **예**로 설정하고 [사용자 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser)을 사용하면 로그인한 사용자를 대상으로 하는 애플리케이션 및 프로그램이 클라이언트에 수신됩니다.  

애플리케이션 카탈로그는 사이트 서버에서 사용자에게 사용 가능한 소프트웨어 목록을 수신합니다. 따라서 사용자가 애플리케이션 카탈로그에서 애플리케이션을 확인하고 요청하기 위해 이 설정이 **예**일 필요가 없습니다. 설정이 **아니요**인 경우, 사용자가 응용 프로그램 카탈로그에 표시된 응용 프로그램을 설치할 수 없습니다.  

또한 이 설정이 **아니요**이면 사용자는 배포되는 필수 애플리케이션을 받을 수 없습니다. 또한 사용자는 사용자 정책에서 다른 관리 작업도 받을 수 없습니다.  

이 설정은 컴퓨터가 인트라넷 또는 인터넷에 있는 경우 사용자에게 적용됩니다. 인터넷에서도 사용자 정책을 사용하려는 경우 **예**로 설정해야 합니다.  

### <a name="enable-user-policy-requests-from-internet-clients"></a>인터넷 클라이언트의 사용자 정책 요청 사용

사용자가 인터넷 기반 컴퓨터에서 사용자 정책을 받으려면 이 옵션을 **예**로 설정합니다. 다음 요구 사항도 적용됩니다.  

- 클라이언트와 사이트가 [인터넷 기반 클라이언트 관리](/sccm/core/clients/manage/plan-internet-based-client-management) 또는 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)에 대해 구성됩니다.  

- **클라이언트에 대한 사용자 정책 사용** 설정이 **예**입니다.  

- 인터넷 기반 관리 지점이 Windows 인증(Kerberos 또는 NTLM)을 사용하여 사용자를 성공적으로 인증합니다. 자세한 내용은 [인터넷에서의 클라이언트 통신에 대한 고려 사항](/sccm/core/plan-design/hierarchy/communications-between-endpoints#BKMK_clientspan)을 참조하세요.  

- 1710 버전부터 클라우드 관리 게이트웨이는 Azure Active Directory를 사용하여 사용자를 성공적으로 인증합니다. 자세한 내용은 [Azure AD 가입 장치에 사용자가 사용할 수 있는 애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)를 참조하세요.  

이 옵션을 **아니요**로 설정하거나 이전 요구 사항이 충족되지 않으면 인터넷상의 컴퓨터에서 컴퓨터 정책만 받습니다. 이 시나리오에서는 사용자가 여전히 인터넷 기반 애플리케이션 카탈로그에서 애플리케이션을 확인, 요청 및 설치할 수 있습니다. 이 설정이 **아니요**이지만 **클라이언트에 대한 사용자 정책 사용**이 **예**이면 컴퓨터가 인트라넷에 연결될 때까지 사용자는 사용자 정책을 받을 수 없습니다.  

> [!NOTE]  
>  인터넷 기반 클라이언트 관리의 경우 사용자의 애플리케이션 승인 요청에는 사용자 정책 또는 사용자 인증이 필요하지 않습니다. 클라우드 관리 게이트웨이는 애플리케이션 승인 요청을 지원하지 않습니다.   



## <a name="cloud-services"></a>Cloud Services

### <a name="allow-access-to-cloud-distribution-point"></a>클라우드 배포 지점에 대한 액세스 허용
클라이언트에서 클라우드 배포 지점으로부터 콘텐츠를 가져오려면 이 옵션을 **예**로 설정합니다. 이 설정에서는 디바이스가 인터넷 기반일 필요가 없습니다.

### <a name="automatically-register-new-windows-10-domain-joined-devices-with-azure-active-directory"></a>Azure Active Directory에 새 Windows 10 도메인에 연결된 디바이스를 자동으로 등록 
하이브리드 연결을 지원하도록 Azure Active Directory를 구성한 경우 Configuration Manager는 이 기능에 대해 Windows 10 디바이스를 구성합니다. 자세한 내용은 [하이브리드 Azure Active Directory 연결 디바이스를 구성하는 방법](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)을 참조하세요.

### <a name="enable-clients-to-use-a-cloud-management-gateway"></a>클라이언트가 클라우드 관리 게이트웨이를 사용하도록 설정
기본적으로 모든 인터넷 로밍 클라이언트는 사용 가능한 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 사용합니다. 이 설정을 **아니요**로 구성하는 예제로 파일럿 프로젝트 상 또는 비용을 절감하기 위한 서비스의 사용 범위를 지정합니다.



##  <a name="compliance-settings"></a>호환성 설정  

### <a name="enable-compliance-evaluation-on-clients"></a>클라이언트에서 규정 준수 평가 사용
이 그룹의 다른 설정을 구성하려면 이 옵션을 **예**로 설정합니다.
 
### <a name="schedule-compliance-evaluation"></a>호환성 평가의 일정
**일정**을 선택하여 구성 기준 배포에 대한 기본 일정을 만듭니다. **구성 기준 배포** 대화 상자에서 각 기준에 대해 이 값을 구성할 수 있습니다.  

### <a name="enable-user-data-and-profiles"></a>사용자 데이터 및 프로필 사용
[사용자 데이터 및 프로필](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items) 구성 항목을 배포하려면 **예**를 선택합니다.



## <a name="computer-agent"></a>컴퓨터 에이전트  

### <a name="user-notifications-for-required-deployments"></a>필수 배포에 대한 사용자 알림

다음 세 가지 설정에 대한 자세한 내용은 [필수 배포에 대한 사용자 알림](/sccm/apps/deploy-use/deploy-applications#user-notifications-for-required-deployments)을 참조하세요.

-   **배포 최종 기한이 24시간 이상 남은 경우 사용자에게 다음 시간마다 미리 알림(시)**
-   **배포 최종 기한이 24시간 미만 남은 경우 사용자에게 다음 시간마다 미리 알림(시)** 
-   **배포 최종 기한이 1시간 미만 남은 경우 사용자에게 다음 시간마다 미리 알림(분)** 

### <a name="default-application-catalog-website-point"></a>기본 애플리케이션 카탈로그 웹 사이트 지점

> [!Note]  
> 버전 1806부터 응용 프로그램 카탈로그 웹 사이트 지점은 더 이상 *필요하지 않지만* *지원은 계속됩니다*. 자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_userex)을 참조하세요. 
> 
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

Configuration Manager에서는 이 설정을 사용하여 소프트웨어 센터의 애플리케이션 카탈로그에 사용자를 연결합니다. **웹 사이트 설정**을 선택하여 애플리케이션 카탈로그 웹 사이트 지점을 호스트하는 서버를 지정합니다. NetBIOS 이름 또는 FQDN을 입력하거나, 자동 검색을 지정하거나, 사용자 지정된 배포에 URL을 지정합니다. 대부분의 경우 자동 검색이 가장 좋은 방법입니다.

### <a name="add-default-application-catalog-website-to-internet-explorer-trusted-sites-zone"></a>기본 애플리케이션 카탈로그 웹 사이트를 Internet Explorer의 신뢰할 수 있는 사이트 영역에 추가

> [!Note]  
> 버전 1806부터 응용 프로그램 카탈로그 웹 사이트 지점은 더 이상 *필요하지 않지만* *지원은 계속됩니다*. 자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_userex)을 참조하세요. 
> 
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

이 옵션이 **예**인 경우 클라이언트에서는 현재 기본 애플리케이션 카탈로그 웹 사이트 URL을 Internet Explorer 신뢰할 수 있는 사이트 영역에 자동으로 추가합니다.  

이 설정은 보호 모드에 대한 Internet Explorer 설정이 사용되지 않도록 합니다. 보호 모드가 사용될 경우 Configuration Manager 클라이언트가 애플리케이션 카탈로그에서 애플리케이션을 설치하지 못할 수 있습니다. 또한 신뢰할 수 있는 사이트 영역은 기본적으로 Windows 인증을 요구하는 애플리케이션 카탈로그에 대한 사용자 로그인을 지원합니다.  

이 옵션을 **아니요**로 두는 경우 Configuration Manager 클라이언트는 애플리케이션 카탈로그에서 애플리케이션을 설치하지 못할 수 있습니다. 다른 방법은 클라이언트에서 사용하는 애플리케이션 카탈로그 URL의 다른 영역에 이러한 Internet Explorer 설정을 구성하는 것입니다.  

### <a name="allow-silverlight-applications-to-run-in-elevated-trust-mode"></a>Silverlight 애플리케이션의 높은 권한 모드 실행을 허용합니다.

> [!Important]  
> Configuration Manager 버전 1802부터 클라이언트는 Silverlight를 자동으로 설치하지 않습니다.
> 
> 버전 1806부터 응용 프로그램 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 사용자는 새로운 소프트웨어 센터를 사용해야 합니다. 자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_userex)을 참조하세요.  

애플리케이션 카탈로그를 사용할 사용자의 경우 이 설정을 **예**로 지정해야 합니다.  

이 설정을 변경하면 사용자가 다음에 브라우저를 로드하거나 현재 열려 있는 브라우저 창을 새로 고칠 때 변경 내용이 적용됩니다.  

이 설정에 대한 자세한 내용은 [Microsoft Silverlight 5용 인증서 및 애플리케이션 카탈로그에 필요한 높은 권한 모드](/sccm/apps/plan-design/security-and-privacy-for-application-management#BKMK_CertificatesSilverlight5)를 참조하세요.  

### <a name="organization-name-displayed-in-software-center"></a>소프트웨어 센터에 표시된 조직 이름

소프트웨어 센터에서 사용자에게 표시되는 이름을 입력합니다. 사용자는 이러한 브랜드 정보를 통해 애플리케이션을 신뢰할 수 있는 원본으로 확인할 수 있습니다. 이 설정의 우선 순위에 대한 자세한 내용은 [브랜딩 소프트웨어 센터](/sccm/apps/plan-design/plan-for-and-configure-application-management#branding-software-center)를 참조하세요.  

### <a name="use-new-software-center"></a>새 소프트웨어 센터 사용

Configuration Manager 1802부터 기본 설정은 **예**입니다.

이 옵션을 **예**로 설정하면 모든 클라이언트 컴퓨터에서 소프트웨어 센터를 사용합니다. 소프트웨어 센터에서는 이전에 애플리케이션 카탈로그에서만 액세스할 수 있었던 사용자가 사용할 수 있는 앱을 보여줍니다. 애플리케이션 카탈로그에는 소프트웨어 센터의 필수 구성 요소가 아닌 Silverlight가 필요합니다.   

버전 1806부터 애플리케이션 카탈로그 웹 사이트 지점 및 웹 서비스 지점은 더 이상 *필요하지 않지만**지원은 계속*됩니다. 자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_userex)을 참조하세요. 
 
> [!Note]  
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  

### <a name="enable-communication-with-health-attestation-service"></a>상태 증명 서비스를 통한 통신 사용

Windows 10 디바이스에서 [상태 증명](/sccm/core/servers/manage/health-attestation)을 사용하려면 이 옵션을 **예**로 설정합니다. 이 설정을 사용하도록 설정하면 다음 설정도 구성에 사용할 수 있습니다.

### <a name="use-on-premises-health-attestation-service"></a>온-프레미스 상태 증명 서비스 사용

디바이스에서 온-프레미스 서비스를 사용하려면 이 옵션을 **예**로 설정합니다. Microsoft 클라우드 기반 서비스를 사용할 디바이스의 경우 이 옵션을 **아니요**로 설정합니다.  

### <a name="install-permissions"></a>설치 권한

> [!IMPORTANT]  
>  이 설정은 애플리케이션 카탈로그와 소프트웨어 센터에 적용됩니다. 사용자가 회사 포털을 사용할 때는 이 설정이 적용되지 않습니다.  

사용자가 소프트웨어, 소프트웨어 업데이트 및 작업 순서의 설치를 시작하는 방식을 구성합니다.  

-   **모든 사용자**: 게스트 이외의 권한 있는 사용자입니다.  

-   **관리자만**: 사용자는 로컬 관리자 그룹의 멤버여야 합니다.  

-   **관리자 및 기본 사용자만**: 사용자가 로컬 관리자 그룹의 멤버 또는 컴퓨터의 기본 사용자여야 합니다.  

-   **사용자 없음**: 클라이언트 컴퓨터에 로그인한 사용자가 소프트웨어 설치, 소프트웨어 업데이트 및 작업 순서를 시작할 수 없습니다. 컴퓨터에 필요한 배포는 항상 최종 기한에 설치됩니다. 사용자는 애플리케이션 카탈로그 또는 소프트웨어 센터에서 소프트웨어 설치를 시작할 수 없습니다.  

### <a name="suspend-bitlocker-pin-entry-on-restart"></a>다시 시작 시 BitLocker PIN 항목 일시 중단

컴퓨터에 BitLocker PIN 항목이 필요한 경우 이 옵션을 사용하면 소프트웨어 설치 후에 컴퓨터가 다시 시작할 때 PIN을 입력해야 하는 요구 사항을 우회합니다.  

-   **항상**: Configuration Manager가 다시 시작이 필요한 소프트웨어를 설치하고 컴퓨터를 다시 시작한 후 BitLocker 요구 사항을 일시적으로 중단합니다. 이 설정은 Configuration Manager에서 시작한 컴퓨터 다시 시작에만 적용됩니다. 이 설정은 사용자가 컴퓨터를 다시 시작할 때 BitLocker PIN을 입력해야 하는 요구 사항을 일시 중단하지 않습니다. BitLocker PIN 항목 요구 사항은 Windows 시작 후 다시 시작됩니다.

-   **안 함**: 다시 시작해야 하는 소프트웨어를 설치한 후에 Configuration Manager에서 BitLocker를 일시 중단하지 않습니다. 이 시나리오에서는 사용자가 PIN을 입력하여 표준 시작 프로세스를 완료하고 Windows를 로드할 때까지 소프트웨어 설치가 완료되지 않습니다.

### <a name="additional-software-manages-the-deployment-of-applications-and-software-updates"></a>추가 소프트웨어로 애플리케이션 및 소프트웨어 업데이트 배포 관리

이 옵션은 다음 조건 중 하나가 적용되는 경우에만 사용하도록 설정합니다.  

-   이 설정이 필요한 공급업체 솔루션을 사용합니다.  

-   Configuration Manager SDK(소프트웨어 개발 키트)를 사용하여 클라이언트 에이전트 알림과 애플리케이션 및 소프트웨어 업데이트의 설치를 관리합니다.  

> [!WARNING]  
>  이러한 조건을 모두 적용하지 않을 때 이 옵션을 선택하면 클라이언트에서 소프트웨어 업데이트 및 필수 애플리케이션을 설치하지 않습니다. 이 설정은 사용자가 애플리케이션 카탈로그에서 애플리케이션을 설치하거나 패키지, 프로그램 및 작업 순서를 설치하지 못하도록 합니다.  

### <a name="powershell-execution-policy"></a>PowerShell 실행 정책

Configuration Manager 클라이언트에서 Windows PowerShell 스크립트를 실행할 수 있는 방식을 구성합니다. 구성 항목에서 준수 설정을 검색하는 데 이러한 스크립트를 사용할 수 있습니다. 배포에 포함된 스크립트를 표준 스크립트로 전송할 수도 있습니다.  

-   **바이패스**: 서명되지 않은 스크립트가 실행될 수 있도록 Configuration Manager 클라이언트가 클라이언트 컴퓨터의 Windows PowerShell 구성을 바이패스합니다.  

-   **제한**: Configuration Manager 클라이언트가 클라이언트 컴퓨터의 현재 Windows PowerShell 구성을 사용합니다. 이 구성에 따라 서명되지 않은 스크립트 실행 가능 여부가 결정됩니다.  

-   **서명된 전체**: Configuration Manager 클라이언트는 신뢰할 수 있는 게시자가 서명한 스크립트만 실행합니다. 이 제한은 클라이언트 컴퓨터의 현재 PowerShell 구성과 별개로 적용됩니다.  

이 옵션을 사용하려면 Windows PowerShell 버전 2.0 이상이 필요합니다. 기본값은 **서명된 전체**입니다.  

> [!TIP]  
>  서명되지 않은 스크립트가 이 클라이언트 설정으로 인해 실행되지 못한 경우 Configuration Manager는 다음 방법으로 이 오류를 보고합니다.  
>   
> -   콘솔의 **모니터링** 작업 영역에는 배포 상태 오류 ID **0x87D00327**이 표시됩니다. 또한 **스크립트가 서명되지 않음**이라는 설명이 표시됩니다.  
> -   보고서에는 **검색 오류**라는 오류 유형이 표시됩니다. 그런 다음, 보고서에 오류 코드 **0x87D00327**과 **스크립트가 서명되지 않음**이라는 설명 또는 오류 코드 **0x87D00320**과 **스크립트 호스트가 설치되지 않음**이라는 설명이 표시됩니다. 예제 보고서는 **자산의 구성 기준에서 구성 항목의 자세한 오류 정보**입니다.  
> -   **DcmWmiProvider.log** 파일에는 **스크립트가 서명되지 않음(오류: 87D00327; 원본: CCM)** 메시지가 표시됩니다.  

### <a name="show-notifications-for-new-deployments"></a>새 배포에 대한 알림 표시

1주 이내에 사용할 수 있는 배포에 대한 알림을 표시하려면 **예**를 선택합니다. 이 메시지는 클라이언트 에이전트를 시작할 때마다 표시됩니다.

### <a name="disable-deadline-randomization"></a>최종 기한 임의 설정 사용 안 함

이 설정은 배포 최종 기한 후에 클라이언트에서 필수 소프트웨어 업데이트를 설치하는 데 최대 2시간의 활성화 지연 시간을 사용할지 여부를 결정합니다. 기본적으로 활성화 지연 시간은 사용하지 않도록 설정되어 있습니다.  

VDI(가상 데스크톱 인프라)를 사용하는 경우 이러한 지연 시간으로 인해 여러 가상 머신이 포함된 호스트 컴퓨터에 CPU 처리 및 데이터 전송을 분산할 수 있습니다. VDI를 사용하지 않더라도 많은 클라이언트에서 동일한 업데이트를 동시에 설치할 경우 사이트 서버의 CPU 사용량이 크게 늘어날 수 있습니다. 또한 이 동작으로 인해 배포 지점의 속도가 느려지며 사용 가능한 네트워크 대역폭이 대폭 감소할 수 있습니다.  

클라이언트에서 지연 시간 없이 배포 최종 기한에 필수 소프트웨어 업데이트를 설치해야 하는 경우 이 설정을 **예**로 구성합니다. 

### <a name="grace-period-for-enforcement-after-deployment-deadline-hours"></a>배포 최종 기한 이후 적용 유예 기간(시간)

최종 기한 이후에 필수 애플리케이션 또는 소프트웨어 업데이트 배포를 설치할 수 있는 더 많은 시간을 사용자에게 제공하려면 이 옵션을 **예**로 설정합니다. 이 유예 기간은 컴퓨터가 오랜 시간 동안 해제된 경우 또는 사용자가 많은 애플리케이션을 설치하거나 배포를 업데이트해야 하는 경우에 적용됩니다. 예를 들어 이 설정은 사용자가 휴가에서 돌아와 클라이언트에서 지연된 애플리케이션 배포를 설치하는 동안 너무 오래 기다려야 하는 경우에 도움이 됩니다. 

유예 기간은 1~120시간 사이로 설정합니다. **이 배포의 적용을 사용자 기본 설정에 따라 연기** 배포 속성과 함께 이 설정을 사용합니다. 자세한 내용은 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.


##  <a name="computer-restart"></a>컴퓨터 다시 시작  
다음 설정은 컴퓨터에 적용된 최단 유지 관리 기간보다 기간이 짧아야 합니다.  

-   **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**
-   **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 카운트다운 간격(분)을 표시하는 대화 상자 표시(사용자가 닫을 수 없음)**

유지 관리 기간에 대한 자세한 내용은 [System Center Configuration Manager에서 유지 관리 기간을 사용하는 방법](/sccm/core/clients/manage/collections/use-maintenance-windows)을 참조하세요.



## <a name="delivery-optimization"></a>배달 최적화

<!-- 1324696 --> Configuration Manager 경계 그룹을 사용하여 회사 네트워크 및 원격 사무실에 대한 콘텐츠 배포를 정의하고 규정합니다. [Windows 배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)는 Windows 10 디바이스 간에 콘텐츠를 공유하는 클라우드 기반의 피어 투 피어 기술입니다. 1802 버전부터 피어 간에 콘텐츠를 공유하는 경우 경계 그룹을 사용하도록 배달 최적화를 구성합니다.

 > [!Note]
 > 배달 최적화는 Windows 10 클라이언트에서만 사용할 수 있습니다.

### <a name="use-configuration-manager-boundary-groups-for-delivery-optimization-group-id"></a>배달 최적화 그룹 ID에 Configuration Manager 경계 그룹 사용
 **예**를 선택하여 경계 그룹 식별자를 클라이언트의 배달 최적화 그룹 식별자로 적용합니다. 클라이언트는 배달 최적화 클라우드 서비스와 통신할 때 이 식별자를 사용하여 원하는 콘텐츠가 있는 피어를 찾습니다. 



##  <a name="endpoint-protection"></a>Endpoint Protection  
> [!Tip]
> 다음 정보 외에도 다음에서 Endpoint Protection 클라이언트 설정을 사용하는 방법에 대한 세부 정보를 찾을 수 있습니다. [예제 시나리오: Endpoint Protection을 사용하여 맬웨어로부터 컴퓨터 보호](/sccm/protect/deploy-use/scenarios-endpoint-protection)

### <a name="manage-endpoint-protection-client-on-client-computers"></a>클라이언트 컴퓨터에서 Endpoint Protection 클라이언트 관리

계층 구조의 컴퓨터에서 기존 Endpoint Protection 및 Windows Defender 클라이언트를 관리하려면 **예**를 선택합니다.  

Endpoint Protection 클라이언트를 이미 설치했고 Configuration Manager를 사용하여 이를 관리하려면 이 옵션을 선택합니다. 이 별도 설치에는 Configuration Manager 애플리케이션 또는 패키지와 프로그램을 사용하는 스크립팅된 프로세스가 포함됩니다. Configuration Manager 1802부터 Windows 10 디바이스에 Endpoint Protection 에이전트를 설치할 필요가 없습니다. 그러나 이러한 디바이스는 여전히 사용하도록 설정된 **클라이언트 컴퓨터에서 Endpoint Protection 클라이언트를 관리**해야 합니다. <!--503654-->

### <a name="install-endpoint-protection-client-on-client-computers"></a>클라이언트 컴퓨터에 Endpoint Protection 클라이언트 설치

아직 클라이언트를 실행하지 않는 클라이언트 컴퓨터에서 Endpoint Protection 클라이언트를 설치하고 사용하도록 설정하려면 **예**를 선택합니다. Configuration Manager 1802부터 Windows 10 클라이언트에 Endpoint Protection 에이전트를 설치할 필요가 없습니다.  

> [!NOTE]  
>  Endpoint Protection 클라이언트가 이미 설치되어 있는 경우 **아니요**를 선택하면 Endpoint Protection 클라이언트가 제거되지 않습니다. Endpoint Protection 클라이언트를 제거하려면 **클라이언트 컴퓨터에서 Endpoint Protection 클라이언트 관리** 클라이언트 설정을 **아니요**로 설정합니다. 그런 다음 패키지 및 프로그램을 배포하여 Endpoint Protection 클라이언트를 제거합니다.  

<!-- removed in 1806, SMS 511544
### Automatically remove previously installed antimalware software before Endpoint Protection is installed

Set this option to **Yes** for the Endpoint Protection client to attempt to uninstall other antimalware applications. Multiple antimalware clients on the same device can conflict, and impact system performance.
-->

### <a name="allow-endpoint-protection-client-installation-and-restarts-outside-maintenance-windows-maintenance-windows-must-be-at-least-30-minutes-long-for-client-installation"></a>유지 관리 기간 외에 Endpoint Protection 클라이언트 설치 및 다시 시작을 허용합니다. 유지 관리 기간은 클라이언트를 설치하기 위해 30분 이상이어야 합니다.

유지 관리 기간을 사용하여 일반적인 설치 동작을 재정의하려면 이 옵션을 **예**로 설정합니다. 이 설정은 보안을 위해 시스템 유지 관리 작업의 우선 순위에 대한 비즈니스 요구 사항을 충족합니다. 

### <a name="for-windows-embedded-devices-with-write-filters-commit-endpoint-protection-client-installation-requires-restarts"></a>쓰기 필터를 지원하는 Windows Embedded 디바이스에 Endpoint Protection 클라이언트 설치 커밋(다시 시작 필요)

Windows Embedded 디바이스에서 쓰기 필터를 사용하지 않도록 설정하려면 **예**를 선택하고 디바이스를 다시 시작합니다. 이 동작으로 인해 디바이스에서 설치가 커밋됩니다.  

**아니요**를 선택하면 클라이언트가 디바이스를 다시 시작할 때 지워지는 임시 오버레이에 설치됩니다. 이 시나리오에서는 다른 설치에서 디바이스 변경 내용을 커밋할 때까지 Endpoint Protection 클라이언트가 완전히 설치되지 않습니다. 이 구성은 기본값입니다.  

### <a name="suppress-any-required-computer-restarts-after-the-endpoint-protection-client-is-installed"></a>Endpoint Protection 클라이언트 설치 후 필요한 컴퓨터 다시 시작 보류

Endpoint Protection 클라이언트 설치 후에 컴퓨터 다시 시작을 보류하려면 **예**를 선택합니다.  

> [!IMPORTANT]  
>  Endpoint Protection 클라이언트에서 컴퓨터를 다시 시작해야 하고 이 설정이 **아니요**인 경우 구성된 유지 관리 기간에 관계없이 다시 시작됩니다.  

### <a name="allowed-period-of-time-users-can-postpone-a-required-restart-to-complete-the-endpoint-protection-installation-hours"></a>Endpoint Protection 설치를 완료하는 데 필요한 다시 시작을 연기할 수 있도록 허용된 기간(시간)

Endpoint Protection 클라이언트를 설치한 후에 컴퓨터를 다시 시작해야 하는 경우 이 설정은 사용자가 필수 다시 시작을 연기할 수 있는 시간을 지정합니다. 이 설정에서는 **Endpoint Protection 클라이언트 설치 후 필요한 컴퓨터 다시 시작 보류** 설정이 **아니요**여야 합니다.  

### <a name="disable-alternate-sources-such-as-microsoft-windows-update-microsoft-windows-server-update-services-or-unc-shares-for-the-initial-definition-update-on-client-computers"></a>클라이언트 컴퓨터의 초기 정의 업데이트에 대체 원본(예: Microsoft Windows Update, Microsoft Windows Server Update Services 또는 UNC 공유) 사용 안 함

Configuration Manager에서 클라이언트 컴퓨터에 초기 정의 업데이트만 설치하도록 하려면 **예**를 선택합니다. 이 설정은 정의 업데이트 초기 설치 중에 불필요한 네트워크 연결을 방지하고 네트워크 대역폭의 사용량을 줄이는 데 유용합니다.  



##  <a name="enrollment"></a>등록

### <a name="polling-interval-for-mobile-device-legacy-clients"></a>모바일 디바이스 기존 클라이언트의 폴링 간격
**간격 설정**을 선택하여 레거시 모바일 디바이스가 정책을 폴링하는 기간을 분 또는 시간 단위로 지정합니다. 이러한 디바이스에는 Windows CE, Mac OS X 및 Unix 또는 Linux와 같은 플랫폼이 포함됩니다.

### <a name="polling-interval-for-modern-devices-minutes"></a>최신 디바이스에 대한 폴링 간격(분)
정책에 최신 디바이스를 폴링하는 시간(분)을 입력합니다. 이 설정은 온-프레미스 모바일 디바이스 관리를 통해 관리되는 Windows 10 디바이스에 적용됩니다.

### <a name="allow-users-to-enroll-mobile-devices-and-mac-computers"></a>사용자가 모바일 디바이스 및 Mac 컴퓨터를 등록할 수 있도록 허용
레거시 디바이스의 사용자 기반 등록을 사용하도록 설정하려면 이 옵션을 **예**로 설정한 다음, 다음 설정을 구성합니다.

-   **등록 프로필** </br>
**프로필 설정**을 선택하여 등록 프로필을 만들거나 선택합니다. 자세한 내용은 [등록을 위해 클라이언트 설정 구성](/sccm/core/clients/deploy/deploy-clients-to-macs#configure-client-settings-for-enrollment)을 참조하세요.

### <a name="allow-users-to-enroll-modern-devices"></a>사용자가 최신 디바이스를 등록하도록 허용
최신 디바이스의 사용자 기반 등록을 사용하도록 설정하려면 이 옵션을 **예**로 설정한 다음, 다음 설정을 구성합니다.

-   **최신 디바이스 등록 프로필** </br>
**프로필 설정**을 선택하여 등록 프로필을 만들거나 선택합니다. 자세한 내용은 [사용자가 최신 디바이스를 등록할 수 있도록 하는 등록 프로필 만들기](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm#bkmk_createProf)를 참조하세요.



##  <a name="hardware-inventory"></a>하드웨어 인벤토리  

### <a name="enable-hardware-inventory-on-clients"></a>클라이언트에서 하드웨어 인벤터리 사용

기본적으로 이 설정은 **예**입니다. 자세한 내용은 [하드웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory)를 참조하세요.

### <a name="hardware-inventory-schedule"></a>하드웨어 인벤토리 일정

**일정**을 선택하여 클라이언트가 하드웨어 인벤토리를 실행하는 빈도를 조정합니다. 기본적으로 이 주기는 7일마다 실행됩니다.

### <a name="maximum-random-delay-minutes"></a>최대 임의 지연(분)

정의된 일정에서 하드웨어 인벤토리 주기를 불규칙하게 지정하기 위해 Configuration Manager 클라이언트에 대한 최대 시간(분)을 지정합니다. 모든 클라이언트에서 이 불규칙화를 통해 사이트 서버에서 처리되는 인벤토리를 부하 분산할 수 있습니다. 0~480분 사이의 값을 지정할 수 있습니다. 기본적으로 이 값은 240분(4시간)으로 설정되어 있습니다.

### <a name="maximum-custom-mif-file-size-kb"></a>최대 사용자 지정 MIF 파일 크기(KB)

하드웨어 인벤토리 주기 중 클라이언트에서 수집하는 각 사용자 지정 MIF(관리 정보 형식) 파일에 허용되는 최대 크기(KB 단위)를 지정합니다. Configuration Manager 하드웨어 인벤토리 에이전트에서는 이 크기를 초과하는 사용자 지정 MIF 파일을 처리하지 않습니다. 1KB~5,120KB 사이의 크기를 지정할 수 있습니다. 기본적으로 이 값은 250KB로 설정되어 있습니다. 이 설정은 일반 하드웨어 인벤토리 데이터 파일의 크기에 영향을 주지 않습니다.  

> [!NOTE]  
>  이 설정은 기본 클라이언트 설정에서만 사용할 수 있습니다.  

### <a name="hardware-inventory-classes"></a>하드웨어 인벤토리 클래스

sms_def.mof 파일을 수동으로 편집하지 않고 클라이언트에서 수집하는 하드웨어 정보를 확장하려면 **클래스 설정**을 선택합니다. 자세한 내용은 [하드웨어 인벤토리를 구성하는 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.  

### <a name="collect-mif-files"></a>MIF 파일 수집

하드웨어 인벤토리가 수행되는 동안 Configuration Manager 클라이언트에서 MIF 파일을 수집할지 여부를 지정하려면 이 설정을 사용합니다.  

MIF 파일이 하드웨어 인벤토리를 통해 수집되려면 클라이언트 컴퓨터의 올바른 위치에 있어야 합니다. 기본적으로 파일은 다음과 같은 경로에 있습니다.  

-   **IDMIF 파일**은 Windows\System32\CCM\Inventory\Idmif 폴더에 있어야 합니다. 

-   **NOIDMIF 파일**은 Windows\System32\CCM\Inventory\Noidmif 폴더에 있어야 합니다.

> [!NOTE]  
>  이 설정은 기본 클라이언트 설정에서만 사용할 수 있습니다.

   

##  <a name="metered-internet-connections"></a>데이터 통신 연결  
 Windows 8 이상 컴퓨터에서 데이터 통신 연결을 사용하여 Configuration Manager와 통신하는 방법을 관리합니다. 때로 인터넷 공급자는 사용자가 데이터 통신 연결을 사용할 경우 보내고 받는 데이터 양을 기준으로 요금을 청구하기도 합니다.  

> [!NOTE]  
>  구성된 클라이언트 설정이 적용되지 않는 시나리오는 다음과 같습니다.  
>   
> -   컴퓨터가 로밍 데이터 통신 연결을 사용하는 경우 Configuration Manager 클라이언트에서 데이터를 Configuration Manager 사이트에 전송해야 하는 작업을 수행하지 않습니다.  
> -   Windows 네트워크 연결 속성이 데이터 통신이 아닌 연결로 구성된 경우 구성 관리자 클라이언트가 데이터 통신 연결이 아닌 것처럼 작동하므로 해당 사이트에 데이터를 전송합니다.  

### <a name="client-communication-on-metered-internet-connections"></a>데이터 통신 연결에서의 클라이언트 통신

이 설정에서 다음 옵션 중 하나를 선택합니다.  

-   **허용**: 클라이언트 디바이스에서 로밍 데이터 연결을 사용하지 않는 한 모든 클라이언트 통신이 요금제 인터넷 연결에 대해 허용됩니다.  

-   **제한**: 요금제 인터넷 연결에 대해 다음 클라이언트 통신만 허용됩니다.  

    -   클라이언트 정책 검색  

    -   사이트에 보낼 클라이언트 상태 메시지  

    -   애플리케이션 카탈로그를 사용한 소프트웨어 설치 요청  

    -   필수 배포(설치 최종 기한에 도달하는 경우)  

    > [!IMPORTANT]  
    >  클라이언트가 데이터 통신 연결 설정에 관계없이 소프트웨어 센터 또는 애플리케이션 카탈로그에서 소프트웨어 설치를 항상 허용합니다.  

    데이터 통신 연결의 데이터 전송 제한에 도달할 경우 클라이언트에서 더 이상 Configuration Manager 사이트와 통신을 시도하지 않습니다.  

-   **차단**: 데이터 통신 연결을 사용하는 경우 Configuration Manager 클라이언트에서 Configuration Manager 사이트와의 통신을 시도하지 않습니다. 이 옵션은 기본값입니다.  



##  <a name="power-management"></a>전원 관리  

### <a name="allow-power-management-of-devices"></a>디바이스의 전원 관리 허용

클라이언트에서 전원 관리를 사용하도록 설정하려면 이 옵션을 **예**로 설정합니다. 자세한 내용은 [전원 관리 소개](/sccm/core/clients/manage/power/introduction-to-power-management)를 참조하세요.

### <a name="allow-users-to-exclude-their-device-from-power-management"></a>사용자가 전원 관리에서 디바이스를 제외할 수 있도록 허용

소프트웨어 센터 사용자가 자신의 컴퓨터를 구성된 전원 관리 설정에서 제외할 수 있도록 허용하려면 **예**를 선택합니다.  

### <a name="enable-wake-up-proxy"></a>절전 모드 해제 프록시 사용

유니캐스트 패킷에 대해 구성된 사이트의 Wake On LAN 설정을 보완하려면 **예**를 지정합니다.  

절전 모드 해제 프록시에 대한 자세한 내용은 [클라이언트를 절전 모드에서 해제하는 방식 계획](/sccm/core/clients/deploy/plan/plan-wake-up-clients) 섹션을 참조하세요.  

> [!WARNING]  
>  프로덕션 네트워크에서 절전 모드 해제 프록시를 사용하려면 먼저 이 프록시의 작동 방식을 이해하고 테스트 환경에서 평가해야 합니다.  

필요한 경우 다음과 같이 추가 설정을 구성합니다.

-   **절전 모드 해제 프록시 포트 번호(UDP)**: 클라이언트에서 절전 모드인 컴퓨터에 절전 모드 해제 패킷을 보내는 데 사용하는 포트 번호입니다. 기본 포트 25536을 유지하거나 원하는 값으로 변경합니다.  

-   **Wake On LAN 포트 번호(UDP)**: 사이트 **속성**의 **포트** 탭에서 Wake On LAN(UDP) 포트 번호를 변경한 경우를 제외하고 기본값 9를 유지합니다.  

    > [!IMPORTANT]  
    >  이 번호는 사이트 **속성**에서 지정한 번호와 일치해야 합니다. 이 번호는 한곳에서 변경 시 다른 곳에서 자동으로 업데이트되지 않습니다.  

-   **절전 모드 해제 프록시에 대한 Windows Defender 방화벽 예외**: Configuration Manager 클라이언트는 Windows Defender 방화벽을 실행하는 디바이스에서 절전 모드 해제 프록시 포트 번호를 자동으로 구성합니다. **구성**을 선택하여 원하는 방화벽 프로필을 지정합니다.

    클라이언트에서 다른 방화벽을 실행하는 경우 **절전 모드 해제 프록시 포트 번호(UDP)** 를 허용하도록 수동으로 구성합니다.  
        
-   **IPv6 접두사(DirectAccess 또는 기타 장애가 있는 네트워크 디바이스에 필요한 경우)입니다. 여러 항목을 지정하려면 쉼표를 사용하십시오**: 네트워크에서 작동하는 절전 모드 해제 프록시에 필요한 IPv6 접두사를 입력합니다.



##  <a name="remote-tools"></a>원격 도구  

### <a name="enable-remote-control-on-clients-and-firewall-exception-profiles"></a>클라이언트에서 원격 제어 사용 및 방화벽 예외 프로필

Configuration Manager 원격 제어 기능을 사용하도록 설정하려면 **구성**을 선택합니다. 필요에 따라 클라이언트 컴퓨터에 대한 원격 제어를 허용하도록 방화벽 설정을 구성합니다.  

기본적으로 원격 제어는 사용되지 않습니다.  

> [!IMPORTANT]  
>  방화벽 설정이 구성되지 않으면 원격 제어가 올바르게 작동하지 않을 수 있습니다.  

### <a name="users-can-change-policy-or-notification-settings-in-software-center"></a>소프트웨어 센터에서 사용자가 정책 또는 알림 설정 변경 가능

사용자가 소프트웨어 센터 내에서 원격 제어 옵션을 변경할 수 있는지 여부를 선택합니다.  

### <a name="allow-remote-control-of-an-unattended-computer"></a>무인 컴퓨터의 원격 제어 허용

관리자가 원격 제어를 사용하여, 로그오프되었거나 잠겨 있는 클라이언트 컴퓨터에 액세스할 수 있는지 여부를 선택합니다. 이 설정이 사용되지 않으면 로그온되어 있거나 잠겨 있지 않은 컴퓨터만 원격으로 제어됩니다.  

### <a name="prompt-user-for-remote-control-permission"></a>원격 제어 권한을 묻는 메시지를 사용자에게 표시

클라이언트 컴퓨터에서 원격 제어 세션을 허용하기 전에 사용자의 권한을 묻는 메시지를 표시할지 여부를 선택합니다.  

### <a name="prompt-user-for-permission-to-transfer-content-from-shared-clipboard"></a>사용자에게 공유 클립보드의 콘텐츠 전송 권한 요청

원격 제어 세션에서 공유 클립보드의 콘텐츠를 전송하기 전에 사용자에게 파일 전송을 수락하거나 거부할 수 있는 기회를 허용합니다. 사용자는 세션당 한 번만 권한을 부여하면 됩니다. 뷰어는 사용자에게 파일 전송 권한을 부여할 수 없습니다.

### <a name="grant-remote-control-permission-to-local-administrators-group"></a>로컬 관리자 그룹에 원격 제어 권한 부여

원격 제어를 시작하는 서버의 로컬 관리자가 클라이언트 컴퓨터에 대한 원격 제어 세션을 설정할 수 있는지 여부를 선택합니다.  

### <a name="access-level-allowed"></a>허용된 액세스 수준

허용할 원격 제어 액세스 수준을 지정합니다. 다음 설정 중 하나를 선택합니다.  
- **액세스 못함**
- **보기 전용**
- **모든 권한**  

### <a name="permitted-viewers-of-remote-control-and-remote-assistance"></a>원격 제어 및 원격 지원의 허용된 뷰어

클라이언트 컴퓨터에 대한 원격 제어 세션을 설정할 수 있는 Windows 사용자의 이름을 지정하려면 **뷰어 설정**을 선택합니다.  

### <a name="show-session-notification-icon-on-taskbar"></a>작업 표시줄에 세션 알림 아이콘 표시

이 설정을 **예**로 구성하여 클라이언트의 Windows 작업 표시줄에서 활성 원격 제어 세션을 나타내는 아이콘을 표시합니다.  

### <a name="show-session-connection-bar"></a>세션 연결 모음 표시

활성 원격 제어 세션을 눈에 잘 띄게 나타내는 세션 연결 모음이 클라이언트에 표시되도록 하려면 이 옵션을 **예**로 설정합니다.  

### <a name="play-a-sound-on-client"></a>클라이언트에서 소리 재생

이 옵션을 설정하면 소리를 사용하여 클라이언트 컴퓨터에서 원격 제어 세션이 활성화된 경우를 나타냅니다. 다음 옵션 중 하나를 선택합니다.
- **소리 없음**
- **세션의 시작 및 전송**(기본값)
- **세션 중 반복적으로**  

### <a name="manage-unsolicited-remote-assistance-settings"></a>원치 않는 원격 지원 설정 관리

Configuration Manager에서 원치 않는 원격 지원 세션을 관리할 수 있도록 하려면 이 설정을 **예**로 구성합니다.  

원하지 않는 원격 지원 세션에서 클라이언트 컴퓨터의 사용자가 세션을 시작하기 위한 지원을 요청하지 않았습니다.  

### <a name="manage-solicited-remote-assistance-settings"></a>요청된 원격 지원 설정 관리

Configuration Manager에서 요청된 원격 지원 세션을 관리할 수 있도록 하려면 이 옵션을 **예**로 설정합니다.  

요청된 원격 지원 세션은 클라이언트 컴퓨터의 사용자가 관리자에게 원격 지원 요청을 보낸 세션입니다.  

### <a name="level-of-access-for-remote-assistance"></a>원격 지원의 액세스 수준

Configuration Manager 콘솔에서 시작되는 원격 지원 세션에 할당할 액세스 수준을 선택합니다. 다음 옵션 중 하나를 선택합니다.
- **없음**(기본값)
- **원격 보기**
- **모든 권한**

> [!NOTE]  
>  클라이언트 컴퓨터의 사용자가 항상 원격 지원 세션에 대한 권한을 부여해야 합니다.  

### <a name="manage-remote-desktop-settings"></a>원격 데스크톱 설정 관리

Configuration Manager에서 컴퓨터에 대한 원격 데스크톱 세션을 관리할 수 있도록 하려면 이 옵션을 **예**로 설정합니다.  

### <a name="allow-permitted-viewers-to-connect-by-using-remote-desktop-connection"></a>허용된 뷰어가 원격 데스크톱 연결을 사용하여 연결하도록 허용

허용된 뷰어 목록에 지정된 사용자를 클라이언트의 원격 데스크톱 로컬 사용자 그룹에 추가하려면 이 옵션을 **예**로 설정합니다.  

### <a name="require-network-level-authentication-on-computers-that-run-windows-vista-operating-system-and-later-versions"></a>Windows Vista 운영 체제 이후 버전을 실행하는 컴퓨터에 네트워크 수준 인증 필요

NLA(네트워크 수준 인증)를 사용하여 클라이언트 컴퓨터에 대한 원격 데스크톱 연결을 설정하려면 이 옵션을 **예**로 설정합니다. NLA는 사용자 인증을 완료한 후에 원격 데스크톱 연결을 설정하기 때문에 초기에 원격 컴퓨터 리소스가 더 적게 필요합니다. NLA를 사용하여 더 안전하게 구성합니다. NLA를 통해 컴퓨터를 악의적인 사용자 또는 소프트웨어로부터 보호하고 서비스 거부 공격의 위험을 줄일 수 있습니다.  



## <a name="software-center"></a>소프트웨어 센터

### <a name="select-these-new-settings-to-specify-company-information"></a>이러한 새 설정을 선택하여 회사 정보 지정
조직에 맞게 소프트웨어 센터를 브랜딩하려면 이 옵션을 **예**로 설정한 다음, 다음 설정을 지정합니다.

- **회사 이름**: 소프트웨어 센터에서 사용자에게 표시되는 조직 이름을 입력합니다.  

- **소프트웨어 센터에 대한 색 구성표**: **색 선택**을 클릭하여 소프트웨어 센터에서 사용할 기본 색을 정의합니다.  

- **소프트웨어 센터에 대한 로고 선택**: **찾아보기**를 클릭하여 소프트웨어 센터에 표시할 이미지를 선택합니다. 로고는 400x100 픽셀의 JPEG, PNG 또는 BMP여야 하며 최대 크기는 750KB입니다. 로고 파일 이름에는 공백이 없어야 합니다.  
         
### <a name="bkmk_HideUnapproved"></a> 소프트웨어 센터에서 승인되지 않은 프로그램 숨기기
Configuration Manager 버전 1802부터 이 옵션을 사용하도록 설정하면 승인이 필요한 사용자가 사용할 수 있는 애플리케이션이 소프트웨어 센터에서 숨겨집니다.   <!--1355146-->

### <a name="bkmk_HideInstalled"></a> 소프트웨어 센터에서 설치된 애플리케이션 숨기기
Configuration Manager 버전 1802부터 이 옵션을 사용하도록 설정하면 이미 설치된 애플리케이션이 더 이상 애플리케이션 탭에 표시되지 않습니다. 이 옵션은 Configuration Manager 1802를 설치하거나 이 버전으로 업그레이드할 때 기본값으로 설정됩니다. 설치된 애플리케이션은 설치 상태 탭에서 계속 검토할 수 있습니다. <!--1357592-->   
 
### <a name="bkmk_HideAppCat"></a> 소프트웨어 센터에서 애플리케이션 카탈로그 링크 숨기기
Configuration Manager 버전 1806부터 소프트웨어 센터에서 애플리케이션 카탈로그 웹 사이트 링크의 표시 여부를 지정할 수 있습니다. 이 옵션을 설정하면 사용자는 소프트웨어 센터의 설치 상태 노드에서 애플리케이션 카탈로그 웹 사이트 링크를 볼 수 없습니다. <!--1358214-->


### <a name="software-center-tab-visibility"></a>소프트웨어 센터 탭 표시 여부
이 그룹에서 추가 설정을 **예**로 구성하여 소프트웨어 센터에서 다음과 같은 탭을 표시하도록 설정합니다.
- **애플리케이션**
- **업데이트**
- **운영 체제**
- **설치 상태**
- **디바이스 호환성**
- **Options**
- **소프트웨어 센터용 사용자 지정 탭 지정**(1806 버전부터 적용) <!--1358132-->
    - **탭 이름**
    - **콘텐츠 URL**

>[!NOTE]
> 소프트웨어 센터에서 사용자 지정 탭으로 사용하는 경우 일부 웹 사이트 기능이 작동하지 않을 수 있습니다. 클라이언트에 배포하기 전에 이 결과를 테스트해야 합니다. <!--519659-->

예를 들어 조직에서 준수 정책을 사용하지 않고 소프트웨어 센터에서 디바이스 준수 탭을 숨기려면 **디바이스 준수 탭 사용**을 **아니요**로 설정합니다.



## <a name="software-deployment"></a>소프트웨어 배포  

### <a name="schedule-re-evaluation-for-deployments"></a>배포의 재평가 일정
Configuration Manager에서 모든 배포에 대한 요구 사항 규칙을 재평가하는 일정을 구성합니다. 기본값은 7일마다입니다.  

> [!IMPORTANT]  
> 이 설정은 네트워크 또는 사이트 서버에서보다 로컬 클라이언트에서 더 큰 영향을 미칩니다. 재평가 일정을 자주 지정하면 네트워크 및 클라이언트 컴퓨터의 성능에 부정적인 영향을 미칩니다. 기본값보다 더 낮은 값으로 설정하는 것은 권장되지 않습니다. 이 값을 변경한 경우에는 성능을 주의 깊게 모니터링하세요.  

**Configuration Manager** 제어판의 **작업** 탭에서 **애플리케이션 배포 평가 주기**를 선택하여 클라이언트에서 이 작업을 시작합니다.  



##  <a name="software-inventory"></a>소프트웨어 인벤토리  

### <a name="enable-software-inventory-on-clients"></a>클라이언트에서 소프트웨어 인벤토리 사용

이 옵션은 기본적으로 **예**로 설정됩니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.

### <a name="schedule-software-inventory-and-file-collection"></a>소프트웨어 인벤토리 및 파일 수집 일정

클라이언트가 소프트웨어 인벤토리 및 파일 컬렉션 주기를 실행하는 빈도를 조정하려면 **일정**을 선택합니다. 기본적으로 이 주기는 7일마다 실행됩니다.

### <a name="inventory-reporting-detail"></a>인벤토리 보고 세부 정보

인벤토리에 다음 수준 중 하나의 파일 정보를 지정합니다.
- **파일에만 해당**
- **제품에만 해당**
- **전체 세부 정보**(기본값)

### <a name="inventory-these-file-types"></a>다음 파일 형식 인벤토리

인벤토리할 파일 형식을 지정하려면 **형식 설정**을 선택하고 다음 옵션을 구성합니다.  

> [!NOTE]  
>  컴퓨터에 여러 사용자 지정 클라이언트 설정이 적용되는 경우, 각 설정을 통해 반환되는 인벤토리가 병합됩니다.  

-   인벤토리에 새 파일 형식을 추가하려면 **새로 만들기**를 선택합니다. 그런 다음 **인벤토리 파일 속성** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름**: 인벤토리할 파일의 이름을 지정합니다. 별표(**&#42;**) 와일드카드를 사용하여 모든 텍스트 문자열을 나타내고, 물음표(**?**)를 사용하여 단일 문자를 나타냅니다. 예를 들어 확장명 .doc을 갖는 모든 파일을 인벤토리하려는 경우 파일 이름을 **\*.doc**로 지정합니다.  

    -   **위치**: **설정**을 선택하여 **경로 속성** 대화 상자를 엽니다. 모든 클라이언트 하드 디스크에서 지정된 파일을 검색하거나, 지정된 경로(예: **C:\Folder**) 또는 지정된 변수(예: *%windir%*)를 검색하도록 소프트웨어 인벤토리를 구성할 수 있습니다. 지정된 경로 아래의 모든 하위 폴더를 검색할 수도 있습니다.  

    -   **암호화 및 압축된 파일 제외**: 이 옵션을 선택하면 압축되거나 암호화된 모든 파일이 인벤토리되지 않습니다.  

    -   **Windows 폴더의 파일 제외**: 이 옵션을 선택하면 Windows 폴더 및 해당 하위 폴더의 모든 파일이 인벤토리되지 않습니다.  

    **인벤토리 파일 속성** 대화 상자를 닫으려면 **확인**을 선택합니다. 인벤토리할 모든 파일을 추가한 후에 **확인**을 선택하여 **클라이언트 설정 구성** 대화 상자를 닫습니다.  

### <a name="collect-files"></a>파일 수집

클라이언트 컴퓨터에서 파일을 수집하려면 **파일 설정**을 선택하고 다음 설정을 구성합니다.  

> [!NOTE]  
>  컴퓨터에 여러 사용자 지정 클라이언트 설정이 적용되는 경우, 각 설정을 통해 반환되는 인벤토리가 병합됩니다.  

-   **클라이언트 설정 구성** 대화 상자에서 **새로 만들기**를 선택하여 수집할 파일을 추가합니다.  

-   **수집된 파일 속성** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름**: 수집할 파일의 이름을 지정합니다. 별표(**&#42;**) 와일드카드를 사용하여 모든 텍스트 문자열을 나타내고, 물음표(**?**)를 사용하여 단일 문자를 나타냅니다.  

    -   **위치**: **설정**을 선택하여 **경로 속성** 대화 상자를 엽니다. 모든 클라이언트 하드 디스크에서 수집할 파일을 검색하거나, 지정된 경로(예: **C:\Folder**) 또는 지정된 변수(예: *%windir%*)를 검색하도록 소프트웨어 인벤토리를 구성합니다. 지정된 경로 아래의 모든 하위 폴더를 검색할 수도 있습니다.  

    -   **암호화 및 압축된 파일 제외**: 이 옵션을 선택하면 압축되거나 암호화된 모든 파일이 수집되지 않습니다.  

    -   **총 파일 크기(KB)가 다음을 초과하면 파일 수집 중지**: 클라이언트가 해당 크기를 초과하면 지정된 파일 수집을 중지할 파일 크기(KB)를 지정합니다.  

    > [!NOTE]  
    >  사이트 서버에서 수집된 파일에 대해 가장 최근에 변경된 5개의 버전을 수집하여 `<ConfigMgr installation directory>\Inboxes\Sinv.box\Filecol` 디렉터리에 저장합니다. 마지막 소프트웨어 인벤토리 주기 이후에 파일이 변경되지 않은 경우 해당 파일이 다시 수집되지 않습니다.  
    >   
    >  소프트웨어 인벤토리는 20MB보다 큰 파일을 수집하지 않습니다.  
    >   
    >  **클라이언트 설정 구성** 대화 상자의 **모든 수집된 파일의 최대 크기(KB)** 값에는 수집된 모든 파일의 최대 크기가 표시됩니다. 이 크기에 도달하면 파일 수집이 중지됩니다. 이미 수집된 모든 파일은 유지되고 사이트 서버에 전송됩니다.  

    > [!IMPORTANT]
    >  다수의 큰 파일을 수집하도록 소프트웨어 인벤토리를 구성할 경우 이 구성으로 인해 네트워크와 사이트 서버의 성능에 부정적인 영향을 미칠 수 있습니다.  

    수집된 파일을 확인하는 방법에 대한 자세한 내용은 [소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory)을 참조하세요.  

    **수집된 파일 속성** 대화 상자를 닫으려면 **확인**을 선택합니다. 수집할 모든 파일을 추가한 후에 **확인**을 선택하여 **클라이언트 설정 구성** 대화 상자를 닫습니다.  

### <a name="set-names"></a>이름 설정

소프트웨어 인벤토리 에이전트는 파일 헤더 정보에서 제조업체 및 제품 이름을 검색합니다. 이러한 이름은 파일 헤더 정보에서 항상 표준화되지는 않습니다. 리소스 탐색기에서 소프트웨어 인벤토리를 볼 때 다른 버전의 동일한 제조업체나 제품 이름이 나타날 수 있습니다. 이러한 표시 이름을 표준화하려면 **이름 설정**을 선택하고 다음 설정을 구성합니다.  

-   **이름 유형**: 소프트웨어 인벤토리는 제조업체 및 제품 모두에 대한 정보를 수집합니다. **제조업체** 또는 **제품**의 표시 이름을 구성할지 여부를 선택합니다.  

-   **표시 이름**: **인벤토리 이름** 목록에 있는 이름 대신 사용할 표시 이름을 지정합니다. 새 표시 이름을 지정하려면 **새로 만들기**를 선택합니다.  

-   **인벤토리 이름**: 인벤토리 이름을 추가하려면 **새로 만들기**를 선택합니다. 소프트웨어 인벤토리에 있는 이 이름이 **표시 이름** 목록에서 선택한 이름으로 바뀝니다. 바꿀 여러 이름을 추가할 수 있습니다.  



##  <a name="software-metering"></a>소프트웨어 계량

### <a name="enable-software-metering-on-clients"></a>클라이언트에서 소프트웨어 계량 사용
기본적으로 이 설정은 **예**로 설정됩니다. 자세한 내용은 [소프트웨어 계량](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering#configure-software-metering)을 참조하세요.

### <a name="schedule-data-collection"></a>데이터 수집 일정
클라이언트가 소프트웨어 계량 주기를 실행하는 빈도를 조정하려면 **일정**을 선택합니다. 기본적으로 이 주기는 7일마다 실행됩니다.



##  <a name="software-updates"></a>소프트웨어 업데이트  

### <a name="enable-software-updates-on-clients"></a>클라이언트에서 소프트웨어 업데이트 사용

이 설정을 사용하여 Configuration Manager 클라이언트에서 소프트웨어 업데이트를 사용하도록 설정할 수 있습니다. 이 설정을 사용하지 않도록 설정하면 Configuration Manager에서 클라이언트로부터 기존 배포 정책을 제거합니다. 이 설정을 다시 사용하도록 설정하는 경우 클라이언트는 현재 배포 정책을 다운로드합니다.  

> [!IMPORTANT]  
>  이 설정을 사용하지 않는 경우 소프트웨어 업데이트에서 사용하는 준수 정책이 더 이상 작동하지 않게 됩니다.  

### <a name="software-update-scan-schedule"></a>소프트웨어 업데이트 검사 일정

클라이언트에서 준수 평가 검사를 시작하는 빈도를 지정하려면 **일정**을 선택합니다. 이 검사는 클라이언트의 소프트웨어 업데이트에 대한 상태(예: 필수 또는 설치됨)를 확인합니다. 준수 평가에 대한 자세한 내용은 [소프트웨어 업데이트 준수 평가](/sccm/sum/understand/software-updates-introduction#BKMK_SUMCompliance)를 참조하세요.  

기본적으로 이 검사는 7일마다 시작하는 단순 일정을 사용합니다. 사용자 지정 일정을 만들 수 있습니다. 정확한 시작 날짜와 시간을 지정하고, UTC(협정 세계시) 또는 현지 시간을 사용하고, 특정 요일에 대해 되풀이 간격을 구성할 수 있습니다.  

> [!NOTE]  
>  1일 미만의 간격을 지정할 경우 Configuration Manager에서 자동으로 기본값을 1일로 설정합니다.  

> [!WARNING]  
>  클라이언트 컴퓨터의 실제 시작 시간은 시작 시간에 임의 시간(최대 2시간)을 더한 값이 됩니다. 이 불규칙화는 클라이언트 컴퓨터가 검색을 시작하는 동시에 활성 소프트웨어 업데이트 지점에 연결되지 않도록 방지합니다.  

### <a name="schedule-deployment-re-evaluation"></a>배포 재평가 일정

소프트웨어 업데이트 클라이언트 에이전트에서 Configuration Manager 클라이언트 컴퓨터의 소프트웨어 업데이트에 대한 설치 상태를 재평가하는 빈도를 구성하려면 **일정**을 선택합니다. 이전에 설치된 소프트웨어 업데이트가 클라이언트에서 더 이상 발견되지 않지만 필요한 경우 클라이언트에서는 소프트웨어 업데이트를 다시 설치합니다.

소프트웨어 업데이트 준수 및 사용자가 소프트웨어 업데이트를 제거할 수 있는지 여부에 대한 회사 정책에 따라 이 일정을 조정합니다. 각 배포 재평가 주기에 따라 네트워크 및 클라이언트 컴퓨터 프로세서 작업이 활성화됩니다. 기본적으로 이 설정은 배포 재평가 검사를 7일마다 시작하는 단순 일정을 사용합니다.  

> [!NOTE]  
>  1일 미만의 간격을 지정할 경우 Configuration Manager에서 자동으로 기본값을 1일로 설정합니다.  

### <a name="when-any-software-update-deployment-deadline-is-reached-install-all-other-software-update-deployments-with-deadline-coming-within-a-specified-period-of-time"></a>소프트웨어 업데이트 배포의 최종 기한에 도달한 경우 지정한 기간 내에 기한이 있는 다른 모든 소프트웨어 업데이트 배포도 설치합니다.

지정한 기간 내에 최종 기한이 도래하는 필수 배포에서 모든 소프트웨어 업데이트를 설치하려면 이 옵션을 **예**로 설정합니다. 필수 소프트웨어 업데이트 배포가 최종 기한에 도달하면 클라이언트에서는 배포에서 소프트웨어 업데이트에 대한 설치를 시작합니다. 이 설정은 지정된 시간 내에 최종 기한이 있는 다른 필수 배포에서 소프트웨어 업데이트 설치할지 여부를 결정합니다.  

이 설정을 사용하여 필수 소프트웨어 업데이트의 설치를 가속화합니다. 이 설정을 통해 클라이언트 보안을 강화하고, 사용자 알림 및 클라이언트 다시 시작을 줄일 수도 있습니다. 기본적으로 이 설정은 **없음**으로 설정됩니다.  

### <a name="period-of-time-for-which-all-pending-deployments-with-deadline-in-this-time-will-also-be-installed"></a>보류된 모든 배포도 설치할 기간(최종 기한이 해당 기간 내에 포함되는 경우)

이 설정을 사용하여 이전 설정의 기간을 지정할 수 있습니다. 1~23시간, 1~365일 사이의 값을 입력할 수 있습니다. 기본적으로 이 설정은 7일로 구성됩니다.  

### <a name="enable-installation-of-express-installation-files-on-clients"></a>클라이언트에서 빠른 설치 파일의 설치 사용

클라이언트에서 빠른 설치 파일을 사용할 수 있게 하려면 이 옵션을 **예**로 설정합니다. 자세한 내용은 [Windows 10 업데이트에 대한 빠른 설치 파일 관리](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)를 참조하세요. 


### <a name="port-used-to-download-content-for-express-installation-files"></a>빠른 설치 파일 콘텐츠를 다운로드하는 데 사용할 포트

이 설정은 HTTP 수신기에 대한 로컬 포트가 기본 콘텐츠를 다운로드하도록 구성합니다. 기본적으로 8005로 설정됩니다. 이 포트는 클라이언트 방화벽에서 열 필요가 없습니다.

### <a name="enable-management-of-the-office-365-client-agent"></a>Office 365 클라이언트 에이전트 관리 사용

이 옵션을 **예**로 설정하면 Office 365 설치 설정을 구성할 수 있습니다. 또한 Office CDN(콘텐츠 배달 네트워크)에서 파일을 다운로드하고, Configuration Manager에 파일을 애플리케이션으로 배포할 수 있습니다. 자세한 내용은 [Office 365 ProPlus 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates)를 참조하세요.

### <a name="enable-third-party-software-updates"></a>타사 소프트웨어 업데이트 사용 

이 옵션을 **예**로 설정하면 '인트라넷 Microsoft 업데이트 서비스 위치에 대해 서명된 업데이트 허용' 정책이 설정되고, 클라이언트의 신뢰할 수 있는 게시자 저장소에 서명 인증서가 설치됩니다. 이 클라이언트 설정은 Configuration Manager 버전 1802에 추가되었습니다.



## <a name="state-messaging"></a>상태 메시지

### <a name="state-message-reporting-cycle-minutes"></a>상태 메시지 보고 주기(분)
클라이언트에서 상태 메시지를 보고하는 주기를 지정합니다. 기본적으로 이 설정은 15분입니다.



##  <a name="user-and-device-affinity"></a>사용자 및 디바이스 선호도  

### <a name="user-device-affinity-usage-threshold-minutes"></a>사용자 디바이스 선호도 사용량 임계값(분)
Configuration Manager에서 사용자 디바이스 선호도 매핑을 만들기 전에 시간(분)을 지정합니다. 이 값은 기본적으로 2,880분(2일)입니다.

### <a name="user-device-affinity-usage-threshold-days"></a>사용자 디바이스 선호도 사용량 임계값(일)
클라이언트에서 사용량 기반 디바이스 선호도에 대한 임계값을 측정할 시간(일)을 지정합니다. 이 값은 기본적으로 30일입니다.

> [!NOTE]  
>  예를 들어 **사용자 디바이스 선호도 사용량 임계값(분)** 을 **60**분으로 지정하고 **사용자 디바이스 선호도 사용량 임계값(일)** 을 **5**일로 지정합니다. 그러면 사용자가 디바이스에서 자동 선호도를 만들기 위해 5일 이내에 60분 동안 디바이스를 사용해야 합니다.  

### <a name="automatically-configure-user-device-affinity-from-usage-data"></a>사용량 데이터에서 사용자 디바이스 선호도 자동 구성
**예**를 선택하여 Configuration Manager에서 수집한 사용량 정보에 따라 사용자 디바이스 선호도를 자동으로 만듭니다.  

### <a name="allow-user-to-define-their-primary-devices"></a>사용자가 기본 디바이스를 정의할 수 있도록 허용
이 설정이 **예**이면 사용자가 소프트웨어 센터에서 고유한 기본 디바이스를 식별할 수 있습니다.



## <a name="windows-analytics"></a>Windows Analytics

이러한 설정에 대한 자세한 내용은 [Windows Analytics로 데이터를 보고하도록 클라이언트 구성](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics)을 참조하세요.
    
