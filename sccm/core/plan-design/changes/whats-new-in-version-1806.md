---
title: 버전 1806의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager 최신 라인인 1806 버전에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.
ms.date: 10/26/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0249dbd3-1e85-4d05-a9e5-420fbe44d850
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4e260f26295a27c91a69cad563eaec2395b00a5c
ms.sourcegitcommit: e0438c191df945305625ae91596c9417d16e8510
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/25/2019
ms.locfileid: "68491686"
---
# <a name="whats-new-in-version-1806-of-configuration-manager-current-branch"></a>Configuration Manager 1806 버전의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 현재 분기에 대한 1806 업데이트는 콘솔 내 업데이트로 사용할 수 있습니다. 1706, 1710 또는 1802 버전을 실행하는 사이트에서 이 업데이트를 적용합니다. <!-- baseline only statement: When installing a new site, it's also available as a baseline version.-->

이 업데이트를 설치하기 위한 최신 검사 목록을 항상 검토하세요. 자세한 내용은 [업데이트 1806을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1806)을 참조하세요. 사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1806#post-update-checklist)도 검토하세요.

<!--
> [!Important]  
> This article currently lists all significant features in this version. However, not all sections yet link to updated content with further information on the new features. Keep checking this page regularly for updates. Changes are noted with the ***[Updated]*** tag. This note will be removed when the content is finalized.  
-->

다음 섹션에서는 Configuration Manager 최신 라인인 1806 버전에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.  



## <a name="deprecated-features-and-operating-systems"></a>사용되지 않는 기능 및 운영 체제

[제거되는 기능과 사용되지 않는 항목](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)에서 구현되기 전의 지원 변경 내용을 알아보세요.

2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 기능이 사용되지 않습니다. 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  

<!--
Version 1806 drops support for the following products:
-->



## <a name="site-infrastructure"></a>사이트 인프라

### <a name="cmpivot"></a>CMPivot
<!--1358456-->
Configuration Manager는 고객이 보고용으로 사용하는 디바이스 데이터의 대규모 중앙 저장소를 항상 제공해왔습니다. 이 사이트는 일반적으로 매주 이 데이터를 수집합니다. CMPivot은 사용자 환경에서 디바이스의 실시간 상태에 액세스할 수 있는 새로운 콘솔 내 유틸리티입니다. 이 유틸리티는 대상 컬렉션에서 현재 연결된 모든 디바이스에 대해 바로 쿼리를 실행하고 결과를 반환합니다. 그러면 도구에서 이 데이터를 필터링하고 그룹화할 수 있습니다. 온라인 클라이언트에서 실시간 데이터를 제공함으로써 비즈니스 질문에 신속하게 대답하고 문제를 해결하며 보안 인시던트에 응답할 수 있습니다. 

자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot)을 참조하세요.  


### <a name="site-server-high-availability"></a>사이트 서버 고가용성
<!--1128774-->
독립 실행형 기본 사이트 서버 역할에 대한 고가용성은 추가 사이트 서버를 수동모드에서 설치하기 위한 Configuration Manager 기반 솔루션입니다. 수동 모드의 사이트 서버는 활성 모드의 기존의 사이트 서버 외의 추가 서버입니다. 수동 모드의 사이트 서버는 필요할 때 즉시 사용할 수 있습니다. 

자세한 내용은 다음 아티클을 참조하세요. 
- [사이트 서버 고가용성](/sccm/core/servers/deploy/configure/site-server-high-availability) 
- [순서도 - 수동 모드로 사이트 서버 설정](/sccm/core/servers/deploy/configure/passive-site-server-flowchart)
- [순서도-사이트 서버 승격(계획됨)](/sccm/core/servers/deploy/configure/promote-site-server-flowchart)
- [순서도-사이트 서버 승격(계획되지 않음)](/sccm/core/servers/deploy/configure/promote-site-server-unplanned-flowchart)


### <a name="improvements-to-management-insights"></a>관리 인사이트 향상
이 릴리스에서는 관리 인사이트의 다음 사항이 개선되었습니다.  

- 일부 관리 인사이트에는 작업을 수행할 수 있는 옵션이 있습니다. 이 작업은 콘솔에서 연결된 노드로 이동하거나 필터링된 쿼리 기반 보기를 표시합니다.<!--1357930-->  

- 사전 대응적 유지 관리를 위한 새 그룹을 6개의 새 규칙으로 사용할 수 있습니다. 구성 문제의 가능성을 밝혀 일반 관리를 통해 해당 문제를 방지하는 데 도움이 됩니다.<!--1352184-->  

자세한 내용은 [관리 인사이트](/sccm/core/servers/manage/management-insights)를 참조하세요.


### <a name="configuration-manager-tools"></a>Configuration Manager 도구
<!--1357145-->
Configuration Manager 서버 및 클라이언트 도구가 이제 서버에 포함되었습니다. 사이트 서버의 `CD.Latest\SMSSETUP\Tools` 폴더에서 찾을 수 있습니다. 추가로 설치할 필요가 없습니다. 

자세한 내용은 [Configuration Manager 도구](/sccm/core/support/tools)를 참조하세요.


### <a name="exclude-active-directory-containers-from-discovery"></a>검색에서 Active Directory 컨테이너 제외
<!--1358143-->
검색되는 개체 수를 줄이기 위해 이제 Active Directory 시스템 검색에서 특정 컨테이너를 제외합니다. 

자세한 내용은 [Active Directory 시스템 검색 구성](/sccm/core/servers/deploy/configure/configure-discovery-methods#bkmk_config-adsd)을 참조하세요.



## <a name="content-management"></a>콘텐츠 관리

### <a name="configure-a-remote-content-library-for-the-site-server"></a>사이트 서버에 대해 원격 콘텐츠 라이브러리 구성
<!--1357525-->
사이트 서버 고가용성을 구성하거나 중앙 관리 또는 기본 사이트 서버에서 하드 드라이브 공간을 확보하기 위해 다른 스토리지 위치로 콘텐츠 라이브러리를 이동합니다. 별도의 서버인 사이트 서버의 다른 드라이브 또는 SAN(스토리지 영역 네트워크)의 내결함성 디스크로 콘텐츠 라이브러리를 이동합니다. 

자세한 내용은 다음 아티클을 참조하세요. 
- [콘텐츠 라이브러리](/sccm/core/plan-design/hierarchy/the-content-library)
- [순서도 – 콘텐츠 라이브러리 관리](/sccm/core/plan-design/hierarchy/manage-content-library-flowchart)


### <a name="cloud-distribution-point-support-for-azure-resource-manager"></a>Azure Resource Manager에 대한 클라우드 배포 지점 지원
<!--1322209-->
클라우드 배포 지점을 만들 때 이제 마법사에서 **Azure Resource Manager 배포**를 만들 수 있는 옵션을 제공합니다. Azure Resource Manager는 모든 솔루션 리소스를 리소스 그룹이라는 단일 엔터티로 관리하기 위한 최신 플랫폼입니다. Azure Resource Manager로 클라우드 배포 지점을 배포하는 경우 사이트에서 Azure Active Directory를 사용하여 필요한 클라우드 리소스를 인증하고 만듭니다. 이 최신 배포에는 클래식 Azure 관리 인증서가 필요하지 않습니다. 

클라우드 배포 지점에 대한 기능 설명서도 수정 및 향상되었습니다. 자세한 내용은 다음 아티클을 참조하세요.
- [클라우드 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)   
- [클라우드 배포 지점 설치](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure)  


### <a name="pull-distribution-points-support-cloud-distribution-points-as-source"></a>풀(pull) 배포 지점은 클라우드 배포 지점을 원본으로 지원합니다.  
<!--1321554-->
많은 고객은 WAN을 통해 원본 배포 지점에서 콘텐츠를 다운로드하는 원격 사무실 또는 지사에서 풀(pull) 배포 지점을 사용합니다. 원격 사무실의 인터넷 연결 속도가 더 빠르거나 WAN 링크에 대한 로드를 줄이려는 경우 이제 Microsoft Azure의 클라우드 배포 지점을 원본으로 사용할 수 있습니다. 배포 지점 속성의 **풀(pull) 배포 지점** 탭에 원본을 추가하면 이제 사이트의 모든 클라우드 배포 지점이 사용 가능한 배포 지점으로 나열됩니다. 그렇지 않을 경우 두 사이트 시스템 역할의 동작이 동일하게 유지됩니다. 

자세한 내용은 [풀(pull) 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)을 참조하세요.


### <a name="enable-distribution-points-to-use-network-congestion-control"></a>배포 지점에서 네트워크 정체 제어를 사용하도록 설정
<!--1358112-->
Windows LEDBAT(Low Extra Delay Background Transport)는 백그라운드 네트워크 전송을 관리하는 데 도움이 되는 Windows Server의 기능입니다. 지원되는 Windows Server 버전에서 실행되는 배포 지점의 경우 네트워크 트래픽을 조정하는 데 유용한 옵션을 사용할 수 있습니다. 클라이언트는 사용 가능한 경우에만 네트워크 대역폭을 사용합니다. 

자세한 내용은 [Windows LEDBAT](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#windows-ledbat)를 참조하세요.


### <a name="partial-download-support-in-client-peer-cache-to-reduce-wan-utilization"></a>WAN 사용률을 줄이기 위해 클라이언트 피어 캐시에서 부분 다운로드 지원
<!--1357346-->
클라이언트 피어 캐시 원본은 이제 콘텐츠를 여러 부분으로 나눌 수 있습니다. 이러한 부분은 네트워크 전송을 최소화하여 WAN 사용률을 줄입니다. 관리 지점은 콘텐츠 부분의 더 자세한 추적을 제공합니다. 경계 그룹별로 동일한 콘텐츠의 2회 이상 다운로드를 제거하려고 시도합니다. 

자세한 내용은 [부분 다운로드 지원](/sccm/core/plan-design/hierarchy/client-peer-cache#bkmk_parts)을 참조하십시오. 


### <a name="boundary-group-options-for-peer-downloads"></a>피어 다운로드를 위한 경계 그룹 옵션
<!--1356193-->
이제 경계 그룹에는 사용자 환경에서 콘텐츠 배포를 보다 세밀하게 제어할 수 있는 추가 설정이 포함됩니다. 이 릴리스에서는 다음 옵션을 추가합니다.  

- **이 경계 그룹에서 피어 다운로드 허용**: 관리 지점은 피어 원본을 포함하는 콘텐츠 위치 목록을 클라이언트에 제공합니다. 이 설정은 배달 최적화 그룹에 대한 ID 적용에도 영향을 미칩니다.  

- **피어 다운로드 중에는 같은 서브넷 내의 피어만 사용**: 관리 지점은 클라이언트와 동일한 서브넷에 있는 콘텐츠 위치 목록 피어 원본에만 포함됩니다.  

자세한 내용은 [피어 다운로드를 위한 경계 그룹 옵션](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgoptions)을 참조하세요.


### <a name="improvement-to-peer-cache-source-location-status"></a>피어 캐시 원본 위치 상태 개선
<!--SCCMDocs issue 850-->
Configuration Manager는 피어 캐시 원본이 다른 위치로 로밍되었는지 여부를 보다 효율적으로 확인할 수 있습니다. 이 동작을 통해 관리 지점은 피어 캐시 원본을 이전 위치가 아닌 새 위치의 클라이언트에 콘텐츠 원본으로 제공합니다. 로밍 피어 캐시 원본에 피어 캐시 기능을 사용하는 경우 사이트를 1806 버전으로 업데이트 한 후 모든 피어 캐시 원본을 최신 클라이언트 버전으로 업데이트해야 합니다. 피어 캐시 원본이 버전 1806 이상으로 업데이트되기 전에는, 관리 지점이 이러한 피어 캐시 원본을 콘텐츠 위치 목록에 포함하지 않습니다.

자세한 내용은 [피어 캐시에 대한 요구 사항](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements)을 참조하세요.



<!-- ## Migration  -->



## <a name="client-management"></a>클라이언트 관리

### <a name="improvement-to-client-push-security"></a>클라이언트 푸시 보안 개선 사항
<!--1358204-->
구성 관리자 클라이언트 설치에 클라이언트 푸시 방법을 사용할 때 이제 사이트에서Kerberos 상호 인증을 요구합니다. 이 개선 사항은 서버와 클라이언트 간의 통신을 보안하는 데 도움이 됩니다. 

자세한 내용은 [클라이언트 푸시를 사용하여 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)을 참조하세요.


### <a name="bkmk_ehttp"></a> 향상된 HTTP 사이트 시스템
<!--1356889,1358228-->
모든 Configuration Manager 통신 경로에는 HTTPS 통신을 사용하는 것이 좋지만 일부 고객의 경우 PKI 인증서 관리 오버헤드로 인해 어려울 수 있습니다. Azure AD(Azure Active Directory) 통합이 도입되면서 인증서 요구 사항의 일부는 줄었지만 전체가 없어지지는 않았습니다. 

이번 릴리스에서는 클라이언트가 사이트 시스템과 통신하는 방법이 개선되었습니다. 사이트 속성의 **클라이언트 컴퓨터 통신** 탭에서 **HTTPS 또는 HTTP**에 대한 옵션을 선택한 다음, 새 옵션 **HTTP 사이트 시스템에 Configuration Manager 생성 인증서 사용**을 사용하도록 설정합니다. 이것은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)입니다.

자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.


### <a name="azure-ad-device-identity"></a>Azure AD 디바이스 ID 
<!--1358460-->
Azure AD 사용자가 로그인되지 않은 [Azure AD 조인](/azure/active-directory/devices/concept-azure-ad-join) 또는 [하이브리드 Azure AD 디바이스](/azure/active-directory/devices/concept-azure-ad-join-hybrid)에서 할당된 사이트와 안전하게 통신할 수 있습니다. 이제 클라우드 기반 디바이스 ID만 있으면 CMG 및 관리 지점을 인증하는 데 충분합니다.  

자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.


### <a name="cmtrace-installed-with-client"></a>CMTrace가 클라이언트와 함께 설치됨
<!--1357971-->
이제 CMTrace 로그 보기 도구가 Configuration Manager 클라이언트와 함께 자동으로 설치됩니다. 이 도구는 기본적으로 `%WinDir%\ccm\cmtrace.exe`인 클라이언트 설치 디렉터리에 추가됩니다. 

자세한 내용은 [CMTrace](/sccm/core/support/cmtrace)를 참조하세요.


### <a name="cloud-management-dashboard"></a>클라우드 관리 대시보드
<!--1358461-->
새로운 클라우드 관리 대시보드는 CMG(클라우드 관리 게이트웨이) 사용량에 대한 중앙 집중식 보기를 제공합니다. 사이트가 Azure AD에 등록되면 클라우드 사용자 및 디바이스에 대한 데이터도 표시됩니다.   

이 기능에는 문제 해결에 도움이 되도록 실시간 확인에 사용하는 **CMG 연결 분석기**도 포함됩니다. 콘솔 내 유틸리티는 서비스의 현재 상태를 확인하며, CMG 연결 지점을 통해 CMG 트래픽을 허용하는 모든 관리 지점에 대한 통신 채널을 확인합니다. 

자세한 내용은 [CMG 모니터링](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway) 문서의 다음 섹션을 참조하세요.  
- [클라우드 관리 대시보드](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway#cloud-management-dashboard)  
- [연결 분석기](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway#connection-analyzer)  


### <a name="improvements-to-cloud-management-gateway"></a>클라우드 관리 게이트웨이드의 향상된 기능

버전 1806에서 CMG(클라우드 관리 게이트웨이)에 포함된 향상된 기능은 다음과 같습니다.

#### <a name="simplified-client-bootstrap-command-line"></a>간소화된 클라이언트 부트스트랩 명령줄
<!--1358215-->
CMG를 통해 구성 관리자 클라이언트를 인터넷에 설치할 때 명령줄에 필요한 속성이 적어졌습니다. 이를 통해 공동 관리를 준비할 때 Microsoft Intune에서 명령줄 크기가 줄어듭니다. 

자세한 내용은 [공동 관리를 위해 인터넷 기반 디바이스를 준비하는 방법](/sccm/comanage/how-to-prepare-win10#install-the-configuration-manager-client)을 참조하세요.

#### <a name="download-content-from-a-cmg"></a>CMG에서 콘텐츠 다운로드
<!--1358651-->
이전에 클라우드 배포 지점 및 CMG를 별도 역할로 배포해야 했습니다. CMG도 이제 클라이언트에 콘텐츠를 서비스합니다. 이 기능은 필요한 인증서 및 Azure VM 비용을 줄여줍니다. 

자세한 내용은 [CMG 수정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg)을 참조하세요.

#### <a name="trusted-root-certificate-isnt-required-with-azure-ad"></a>신뢰할 수 있는 루트 인증서는 Azure AD에서 필요하지 않음
<!--503899-->
CMG를 만들 경우 설정 페이지에서 [신뢰할 수 있는 루트 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_cmgroot)를 더 이상 제공할 필요가 없습니다. 이 인증서는 클라이언트 인증용 Azure AD(Azure Active Directory)를 사용할 때 필요하지 않지만 마법사에서는 필요합니다. PKI 클라이언트 인증 인증서를 사용하는 경우 여전히 신뢰할 수 있는 루트 인증서를 CMG에 추가해야 합니다.



## <a name="co-management"></a>공동 관리

### <a name="sync-mdm-policy-from-microsoft-intune-for-a-co-managed-device"></a>Microsoft Intune에서 공동 관리하는 디바이스에 대한 MDM 정책 동기화
<!--1357377-->
공동 관리 워크로드를 전환할 경우 공동 관리되는 디바이스는 Microsoft Intune에서 자동으로 MDM 정책을 동기화합니다. 이 동기화는 Configuration Manager 콘솔의 클라이언트 알림에서 **컴퓨터 정책 다운로드** 작업 시작할 때 발생합니다. 

자세한 내용은 [Configuration Manager 워크로드를 Intune으로 전환하는 방법](/sccm/comanage/how-to-switch-workloads)을 참조하세요.


### <a name="transition-new-workloads-to-intune-using-co-management"></a>공동 관리를 사용하여 새 워크로드를 Intune으로 전환
이제 공동 관리를 사용하도록 설정한 후 다음 워크로드를 Configuration Manager에서 Intune으로 전환할 수 있습니다.  

- **디바이스 구성**<!--1357903-->: 이 워크로드를 통해 Intune을 사용하여 MDM 정책을 배포할 수 있지만 애플리케이션 배포에는 Configuration Manager를 계속 사용할 수 있습니다.  

- **Office 365**<!--1357841-->: 디바이스는Configuration Manager에서 Office 365 배포를 설치하지 않습니다.  

- **모바일 앱**<!--1357892-->: Intune에서 배포된 사용 가능한 모든 앱을 회사 포털에서 사용할 수 있습니다. Configuration Manager에서 배포하는 앱은 소프트웨어 센터에서 사용할 수 있습니다. 이것은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)입니다.  

이러한 워크로드를 전환하려면 공동 관리 속성 페이지로 이동하고 워크로드 슬라이더 막대를 Configuration Manager에서 **파일럿** 또는 **모두**로 이동합니다. 

자세한 내용은 [Windows 10 디바이스의 공동 관리](/sccm/comanage/overview)를 참조하세요.


### <a name="support-for-multiple-hierarchies-to-one-intune-tenant"></a>하나의 Intune 테넌트에 대한 여러 계층 구조 지원
<!--1357944-->
어떤 고객은 여러 Configuration Manager 계층 구조가 있고 향후 Azure Active Directory 및 Microsoft Intune에 대한 단일 테넌트로 통합하고자 합니다. 이제 공동 관리에서 동일한 Intune 테넌트에 대해 여러 Configuration Manager 환경을 지원합니다.

자세한 내용은 [공동 관리 필수 구성 요소](/sccm/comanage/overview#prerequisites)를 참조하세요.
 


## <a name="compliance-settings"></a>호환성 설정

### <a name="configure-windows-defender-smartscreen-settings-for-microsoft-edge"></a>Microsoft Edge용 Windows Defender SmartScreen 설정 구성
<!--1353701-->
Microsoft Edge 브라우저 준수 설정 정책에서 Windows Defender SmartScreen에 대한 다음 세 설정이 추가되었습니다. 
- SmartScreen 허용
- 사용자는 다음 사이트에 대해 SmartScreen 프롬프트를 재정의할 수 있음
- 사용자는 다음 파일에 대해 SmartScreen 프롬프트를 재정의할 수 있음

자세한 내용은 [Microsoft Edge 설정 구성](/sccm/compliance/deploy-use/browser-profiles)을 참조하세요.


### <a name="scap-extensions"></a>SCAP 확장
<!--1357552-->
콘솔 확장을 사용하여 SCAP(Convert Security Content Automation Protocol) 콘텐츠를 준수 설정 기준으로 변환하고 SCAP 보고서를 생성합니다. 이 기능은 XCCDF 규칙 준수뿐만 아니라 클라이언트 준수를 시각화하는 새 대시보드도 포함합니다. 

자세한 내용은 [SCAP 확장 정보](/sccm/compliance/plan-design/scap/about-scap)를 참조하세요.



## <a name="application-management"></a>애플리케이션 관리

### <a name="phased-deployment-of-applications"></a>애플리케이션의 단계적 배포
<!--1358147-->
애플리케이션에 대한 단계적 배포를 만듭니다. 단계적 배포에서는 사용자 지정 가능한 조건 및 그룹에 따라 소프트웨어 출시를 조정하고 순차적으로 진행할 수 있습니다. 예를 들어, 파일럿 컬렉션에 애플리케이션을 배포한 다음, 성공 조건에 따라 출시를 자동으로 계속합니다. 

자세한 내용은 다음 아티클을 참조하세요.  

- [단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/sccm/apps/toc.json&bc=/sccm/apps/breadcrumb/toc.json)  

- [단계적 배포 관리 및 모니터링](/sccm/osd/deploy-use/manage-monitor-phased-deployments?toc=/sccm/apps/toc.json&bc=/sccm/apps/breadcrumb/toc.json)  


### <a name="provision-windows-app-packages-for-all-users-on-a-device"></a>디바이스의 모든 사용자에 대해 Windows 앱 패키지 프로비전
<!--1358310-->
디바이스에서 모든 사용자에 대한 Windows 앱 패키지를 사용하여 애플리케이션을 프로비저닝합니다. 이 시나리오의 일반적인 한 예는 Minecraft 교육용 버전처럼 비즈니스 및 교육용 Microsoft Store의 앱을 학교에서 학생들이 사용하는 모든 디바이스에 프로비전하는 것입니다. 전에 Configuration Manager는 사용자 당 이러한 애플리케이션 설치만 지원했습니다. 새 디바이스에 로그인한 후 학생은 앱에 액세스하기를 기다려야 합니다. 앱이 모든 사용자용 디바이스에 프로비전되는 경우 더 신속하게 생산적이 될 수 있습니다. 

자세한 내용은 [Windows 애플리케이션 만들기](/sccm/apps/get-started/creating-windows-applications#bkmk_provision)를 참조하세요.


### <a name="office-customization-tool-integration-with-the-office-365-installer"></a>Office 365 설치 관리자와 Office 사용자 지정 도구 통합
<!--1358149-->
Office 사용자 지정 도구는 Configuration Manager 콘솔에서 Office 365 설치 관리자와 통합됩니다. Office 365에 대한 배포를 만들 때 최신 Office 관리 효율성 설정을 동적으로 구성합니다. Microsoft는 Office 365의 새 빌드 릴리스 시점에 Office 사용자 지정 도구를 업데이트합니다. 이 통합을 통해 Office 365에서 새 관리 효율성 설정이 제공되는 즉시 사용할 수 있습니다. 

자세한 내용은 [Office 365 앱 배포](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)를 참조하세요.


### <a name="support-for-new-windows-app-package-formats"></a>새로운 Windows 앱 패키지 형식에 대한 지원
<!--1357427-->
Configuration Manager는 이제 새 Windows 10 앱 패키지(.msix) 및 앱 번들(.msixbundle) 형식의 배포를 지원합니다. 

자세한 내용은 [Windows 애플리케이션 만들기](/sccm/apps/get-started/creating-windows-applications#bkmk_msix)를 참조하세요.


### <a name="uninstall-application-on-approval-revocation"></a>승인 취소 시 애플리케이션 제거
<!--1357891-->
애플리케이션 승인 취소 시의 동작이 변경되었습니다. 이제 애플리케이션에 대한 요청을 거부하면 클라이언트가 사용자 디바이스에서 애플리케이션을 제거합니다. 이를 위해서는 [선택적 기능](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_options)인 **디바이스당 사용자에 대한 응용 프로그램 요청 승인**을 사용하도록 설정해야 합니다. 

자세한 내용은 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications#bkmk_approval)를 참조하세요.


### <a name="package-conversion-manager"></a>Package Conversion Manager 
<!--1357861-->
Package Conversion Manager는 레거시 패키지를 Configuration Manager 현재 분기 애플리케이션으로 변환할 수 있는 통합 도구입니다. 이와 같은 변환을 수행한 후에는 종속성, 요구 사항 규칙, 사용자 디바이스 선호도 등의 애플리케이션 기능을 사용할 수 있습니다.

자세한 내용은 [Package Conversion Manager](/sccm/apps/pcm/package-conversion-manager)를 참조하세요.



## <a name="os-deployment"></a>OS 배포

### <a name="improvements-to-phased-deployments"></a>단계적 배포 개선 사항

이 릴리스에서는 단계적 배포의 다음 사항이 개선되었습니다.  

#### <a name="create-a-phased-deployment-with-manually-configured-phases"></a>수동으로 구성된 단계를 사용하여 단계별 배포 만들기
<!--1358148-->
이제 작업 순서에 대해 단계적 배포를 만들 때 단계를 수동으로 구성할 수 있습니다. 단계별 배포 만들기 마법사의 **단계** 탭에서 최대 10개의 추가 단계를 추가합니다. 자동으로 기본 두 단계 배포를 만드는 것도 계속 가능합니다. 

자세한 내용은 [수동으로 구성된 단계를 사용하여 단계적 배포 만들기 ](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence#bkmk_manual)를 참조하세요.

#### <a name="phased-deployment-status"></a>단계적 배포 상태
<!--1358577-->
이제 단계적 배포에서 기본 모니터링 환경을 제공합니다. **모니터링** 작업 영역의 **배포** 노드에서 단계적 배포를 선택한 다음, 리본에서 **단계적 배포 상태**를 클릭합니다. 

자세한 내용은 [단계적 배포 관리 및 모니터](/sccm/osd/deploy-use/manage-monitor-phased-deployments)를 참조하세요.  

#### <a name="gradual-rollout-during-phased-deployments"></a>단계적 배포 중 점진적 출시
<!--1358578-->
단계적 배포 중에 각 단계의 출시가 이제 점진적으로 수행됩니다. 이 동작은 배포 문제의 위험을 완화하고 콘텐츠의 클라이언트 배포로 인한 네트워크의 부하를 줄이는 데 도움이 됩니다. 사이트에서는 각 단계에 대한 구성에 따라 점진적으로 소프트웨어를 사용할 수 있도록 합니다. 단계의 모든 클라이언트는 소프트웨어를 사용할 수 있게 되는 시간을 기준으로 최종 기한을 갖게 됩니다. 사용 가능 시간과 최종 기한 사이의 기간은 단계의 모든 클라이언트에 대해 동일합니다. 

자세한 내용은 [단계 설정](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence#bkmk_settings)을 참조하세요.  


### <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Windows 10 현재 위치 업그레이드 작업 순서 개선 사항
<!--1358500-->
이제 Windows 10 현재 위치 업그레이드의 기본 작업 순서 템플릿에 업그레이드 프로세스가 실패할 경우, 추가할 권장 작업이 있는 새 그룹이 포함되어 있습니다. 이러한 작업을 수행하면 문제를 더 쉽게 해결할 수 있습니다. 이러한 도구 중 하나는 Windows [SetupDiag](https://docs.microsoft.com/windows/deployment/upgrade/setupdiag)입니다. 이 도구는 Windows 10 업그레이드 실패 이유에 대한 세부 정보를 얻기 위한 독립 실행형 진단 도구입니다. 

자세한 내용은 [OS를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#recommended-task-sequence-steps-on-failure)를 참조하세요.


### <a name="improvements-to-pxe-enabled-distribution-points"></a>PXE 사용 배포 지점 개선 사항
<!--1357580-->
배포 지점 속성의 **PXE** 탭에서 **Windows 배포 서비스 없이 PXE 응답기 사용**을 선택합니다. 이 새 옵션은 배포 지점에서 WDS(Windows 배포 서비스)가 필요하지 않은 PXE 응답기를 사용하도록 설정합니다. WDS가 필요하지 않으므로 PXE 사용 배포 지점은 Windows Server Core를 포함하여 클라이언트 또는 서버 OS일 수 있습니다. 이 새로운 PXE 응답기 서비스는 IPv6을 지원하므로 원격 사무실에서 PXE 사용 배포 지점의 유연성도 향상됩니다. 

자세한 내용은 [배포 지점에서 PXE를 사용하도록 설정](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.


### <a name="network-access-account-not-required-for-some-scenarios"></a>일부 시나리오에서 네트워크 액세스 계정이 필요하지 않음
<!--1358278,1358279-->
[향상된 HTTP 사이트 시스템](#bkmk_ehttp) 기능에서는 네트워크 액세스 계정에 대한 종속성도 일부 제거되었습니다. 에 새 사이트 옵션을 설정 하면 **HTTP 사이트 시스템에 대한 Configuration Manager 생성 인증서 사용**하기 위해 새 사이트 옵션을 사용하는 경우 다음과 같은 시나리오는 배포 지점에서 콘텐츠를 다운로드하기 위한 네트워크 액세스 계정이 필요하지 않습니다.  

- 부팅 미디어 또는 PXE에서 실행하는 작업 순서
- 소프트웨어 센터에서 실행하는 작업 순서  

이러한 작업 순서는 OS 배포 또는 사용자 지정용일 수 있습니다. 작업 그룹 컴퓨터에도 지원됩니다.

자세한 내용은 [작업 순서 및 네트워크 액세스 계정](/sccm/osd/plan-design/planning-considerations-for-automating-tasks#BKMK_TSNetworkAccessAccount)을 참조하세요.


### <a name="other-improvements-to-os-deployment"></a>기타 향상된 OS 배포

#### <a name="mask-sensitive-data-stored-in-task-sequence-variables"></a>작업 순서 변수에 저장된 중요한 데이터 마스킹
 <!--1358330-->
 **작업 순서 변수 설정** 단계에서 새 옵션인 **이 값 표시 안 함**을 선택합니다. 

 자세한 내용은 [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable)을 참조하세요. 

#### <a name="mask-program-name-during-run-command-step-of-a-task-sequence"></a>작업 순서의 명령 실행 단계에서 프로그램 이름 마스크
 <!--1358493-->
 잠재적으로 중요한 데이터가 표시되거나 기록되지 않도록 하려면 작업 순서 변수 **OSDDoNotLogCommand**를 구성합니다.  

 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#OSDDoNotLogCommand)\(작업 순서 변수\)를 참조하세요. 

#### <a name="task-sequence-variable-for-dism-parameters-when-installing-drivers"></a>드라이버를 설치할 때 DISM 매개 변수에 대한 작업 순서 변수
 <!--516679/2840016-->
 DISM에 대한 추가 명령줄 매개 변수를 지정하려면 새 작업 순서 변수 **OSDInstallDriversAdditionalOptions**를 사용합니다. 

 자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#OSDInstallDriversAdditionalOptions)\(작업 순서 변수\)를 참조하세요. 

#### <a name="option-to-use-full-disk-encryption"></a>전체 디스크 암호화 사용 옵션
 <!--SCCMDocs-pr issue 2671-->
 **BitLocker 사용** 및 **BitLocker 사전 프로비저닝** 단계에 모두 **전체 디스크 암호화 사용** 옵션이 포함되었습니다. 기본적으로 이러한 단계는 드라이브에서 사용된 공간을 암호화합니다. 이 기본 동작은 더 빠르고 효율적기 때문에 권장됩니다. 

 자세한 내용은 [BitLocker 사용](/sccm/osd/understand/task-sequence-steps#BKMK_EnableBitLocker) 및 [BitLocker 사전 프로비전](/sccm/osd/understand/task-sequence-steps#BKMK_PreProvisionBitLocker)을 참조하세요. 

#### <a name="client-provisioning-mode-isnt-enabled-with-windows-10-upgrade-compatibility-scan"></a>Windows 10 업그레이드 호환성 검사에서 클라이언트 프로비저닝 모드를 사용하도록 설정하지 않음
 <!--SCCMDocs-pr issue 2812-->
 이제 **업그레이드를 시작하지 않고 Windows 설치 프로그램 호환성 검사 수행** 옵션을 사용하는 경우 **운영 체제 업그레이드** 작업 순서 단계에서 구성 관리자 클라이언트를 프로비저닝 모드로 지정하지 않습니다.

 자세한 내용은 [운영 체제 업그레이드](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS)를 참조하세요.

#### <a name="revised-documentation-for-task-sequence-variables"></a>작업 순서 변수에 대한 설명서 수정
이제 작업 순서 변수 이해를 위한 다음 두 개의 새 문서가 제공됩니다.  

- [작업 순서 변수를 사용하는 방법](/sccm/osd/understand/using-task-sequence-variables)은 다양한 변수 형식, 변수를 설정하는 방법 및 변수에 액세스하는 방법을 설명하는 새 문서입니다.  

- [작업 순서 변수](/sccm/osd/understand/task-sequence-variables)는 모든 사용 가능한 작업 순서 변수에 대한 참조입니다. 이 문서는 기본 제공 변수와 작업 변수가 서로 분리되어 있던 이전 문서가 결합된 것입니다. 



## <a name="software-center"></a>소프트웨어 센터

> [!Important]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.


### <a name="software-center-infrastructure-improvements"></a>소프트웨어 센터 인프라 개선 사항
<!--1358309-->
소프트웨어 센터에 사용자가 사용할 수 있는 애플리케이션을 표시하는 데 더 이상 애플리케이션 카탈로그 역할이 필요하지 않습니다. 이 변경은 사용자에게 애플리케이션을 전달하기 위해 필요한 서버 인프라를 줄일 수 있습니다. 소프트웨어 센터는 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups#management-points)에 할당하여 대규모 환경의 크기 조정을 더 잘하도록 도움을 주는 이 정보를 얻으려면 관리 지점에 의존합니다.

자세한 내용은 [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)을 참조하세요.  

> [!Note]  
> 애플리케이션 카탈로그 웹 사이트 지점 및 웹 서비스 지점은 1806에서 더 이상 *필요하지 않지만* *지원은 계속*됩니다. 
> 
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  


### <a name="specify-the-visibility-of-the-application-catalog-website-link-in-software-center"></a>소프트웨어 센터에서 애플리케이션 카탈로그 웹 사이트 링크의 표시 여부 지정
<!--1358214-->
클라이언트 설정을 사용하면 소프트웨어 센터의 **설치 상태** 노드에 **애플리케이션 카탈로그 웹 사이트 열기** 링크를 표시할지 여부를 제어할 수 있습니다.  

자세한 내용은 [소프트웨어 센터 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-center)을 참조하세요.

> [!Note]  
> 애플리케이션 카탈로그 웹 사이트 지점에 대한 **Silverlight 사용자 환경**은 더 이상 지원되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.  


### <a name="custom-tab-for-webpage-in-software-center"></a>소프트웨어 센터의 웹 페이지용 사용자 지정 탭
<!--1358132-->
클라이언트 설정을 사용하여 소프트웨어 센터에서 사용자 지정된 탭을 만들어 웹 페이지를 엽니다. 이 기능을 사용하면 일관되고 신뢰할 수 있는 방식으로 최종 사용자에게 콘텐츠를 보여줄 수 있습니다. 다음 목록에는 몇 가지 예가 포함되어 있습니다.  

- IT 연락처: 조직의 IT 부서에 문의하는 방법에 대한 정보  

- IT 지원 센터: 기술 자료 검색 또는 지원 티켓 열기와 같은 IT 셀프 서비스 작업  

- 최종 사용자 설명서: 조직의 사용자가 애플리케이션을 사용하는 방법이나 Windows 10으로 업그레이드하는 방법과 같은 다양한 IT 토픽에 대한 아티클  

자세한 내용은 [소프트웨어 센터 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-center) 및 [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)를 참조하세요.


### <a name="maintenance-windows-in-software-center"></a>소프트웨어 센터의 유지 관리 기간
<!--1358131-->
소프트웨어 센터는 이제 다음 예약된 유지 관리 기간을 표시합니다. 설치 상태 탭에서 보기를 모두에서 예정으로 전환합니다. 시간 범위와 예약된 배포 목록을 표시합니다. 향후 유지 관리 기간이 없으면 목록은 비어 있습니다. 

자세한 내용은 [유지 관리 기간을 사용하는 방법](/sccm/core/clients/manage/collections/use-maintenance-windows) 및 [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)를 참조하세요.



## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="third-party-software-updates"></a>타사 소프트웨어 업데이트
<!--1357605, 1352101, 1358714-->
타사 소프트웨어 업데이트를 사용하면 Configuration Manager 콘솔에서 파트너 카탈로그를 구독하고 업데이트를 WSUS에 게시할 수 있습니다. 그런 다음, 기존 소프트웨어 업데이트 관리 프로세스를 사용하여 업데이트를 배포할 수 있습니다. 

자세한 내용은 [타사 업데이트 사용](/sccm/sum/deploy-use/third-party-software-updates)을 참조하세요.


### <a name="deploy-software-updates-without-content"></a>콘텐츠 없이 소프트웨어 업데이트 배포
<!--1357933-->
콘텐츠를 배포 지점에 처음 다운로드하여 배포하지 않고 디바이스에 소프트웨어 업데이트를 배포합니다. 이 기능은 매우 큰 업데이트 콘텐츠를 처리할 때 또는 항상 클라이언트가 Microsoft 업데이트 클라우드 서비스에서 콘텐츠를 가져오려 할 때 유용합니다. 이 시나리오에서 클라이언트는 이미 필요한 콘텐츠가 있는 피어로부터 콘텐츠를 다운로드할 수 있습니다. Configuration Manager 클라이언트는 계속 콘텐츠 다운로드를 관리하므로 Configuration Manager 피어 캐시 기능 또는 배달 최적화 같은 다른 기술을 활용할 수 있습니다. 이 기능은 Windows 및 Office 업데이트를 포함하여 Configuration Manager 소프트웨어 업데이트 관리에서 지원하는 모든 업데이트 유형을 지원합니다. 

자세한 내용은 [수동으로 소프트웨어 배포](/sccm/sum/deploy-use/manually-deploy-software-updates) 또는 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates) 시 **배포 패키지 없음** 옵션을 참조하세요.


### <a name="filter-automatic-deployment-rules-by-software-update-architecture"></a>소프트웨어 업데이트 아키텍처를 기준으로 자동 배포 규칙 필터링
 <!--1322266-->
이제 ADR(자동 배포 규칙)을 필터링하여 Itanium, ARM64 등의 아키텍처를 제외할 수 있습니다. 이제 자동 배포 규칙 만들기 마법사의 **소프트웨어 업데이트** 페이지에서**아키텍처** 속성 필터를 사용할 수 있습니다. 

자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)를 참조하세요.


### <a name="improved-wsus-maintenance"></a>개선된 WSUS 유지 관리 
<!--1357898-->
이제 WSUS 정리 마법사는 소프트웨어 업데이트 지점 구성 요소 속성에 정의된 교체 규칙에 따라 만료된 업데이트를 거부합니다. 

자세한 내용은 [소프트웨어 업데이트 유지 관리](/sccm/sum/deploy-use/software-updates-maintenance)를 참조하세요.



## <a name="reporting"></a>보고

### <a name="new-software-updates-compliance-report"></a>새 소프트웨어 업데이트 준수 보고서
<!--1357775-->
소프트웨어 업데이트 준수에 대한 보고서 보기에는 일반적으로 최근 사이트에 연결하지 않은 클라이언트의 데이터가 포함됩니다. 새 보고서 **준수 9 - 전체 상태 및 준수**에서는 특정 소프트웨어 업데이트 그룹에 대한 준수 결과를 “정상” 클라이언트별로 필터링할 수 있습니다. 이 보고서에서는 사용자 환경에서 활성 클라이언트의 보다 사실적인 준수 상태를 보여 줍니다. 

자세한 내용은 [소프트웨어 업데이트 보고서](/sccm/sum/deploy-use/monitor-software-updates#BKMK_SUReports)를 참조하세요.



## <a name="inventory"></a>인벤토리

### <a name="bkmk_bigint"></a> 큰 정수 값에 대한 하드웨어 인벤토리 개선 사항
<!--1357880-->
하드웨어 인벤토리에서 이전에는 4,294,967,296(2^32)보다 큰 정수에 대한 제한이 있었습니다. 하드 드라이브 크기(바이트)와 같은 특성의 경우 이 제한에 도달할 수 있습니다. 관리 지점에서 이 제한을 초과하는 정수 값을 처리하지 않으므로 값이 데이터베이스에 저장되지 않았습니다. 이번 릴리스에서는 이 제한이 18,446,744,073,709,551,616(2^64)으로 증가했습니다. 

자세한 내용은 [큰 정수 값 사용](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory#bkmk_bigint)을 참조하세요.


### <a name="hardware-inventory-default-unit-revision"></a>하드웨어 인벤토리 기본 단위 수정 버전
<!--514442-->
[Configuration Manager 버전 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710#site-infrastructure)에서 많은 보고 보기에 사용된 기본 단위는 메가바이트(MB)에서 기가바이트(GB)로 변경됐습니다. [큰 정수 값에 대한 하드웨어 인벤토리의 향상된 기능](#bkmk_bigint) 때문에 또한 고객 의견에 따라 이 기본 단위는 다시 MB로 됩니다.



<!-- ## Mobile device management -->



<!-- ## Protect devices-->




## <a name="configuration-manager-console"></a>Configuration Manager 콘솔

### <a name="product-lifecycle-dashboard"></a>제품 수명 주기 대시보드
<!--1319632-->
제품 수명 주기 대시보드에는 Configuration Manager로 관리되는 디바이스에 설치된 Microsoft 제품에 대한 Microsoft 수명 주기 정책의 상태가 표시됩니다. 또한 사용자 환경의 Microsoft 제품, 지원 가능성 상태 및 지원 종료 날짜에 대한 정보도 제공합니다. 대시보드를 사용하여 각 제품에 대한 지원 가용성을 파악합니다. 이 정보는 현재 지원 종료에 도달하기 전에 사용하는 Microsoft 제품을 업데이트할 시기를 계획하는 데 도움이 됩니다.   

자세한 내용은 [제품 수명 주기 대시보드](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard)를 참조하세요.


### <a name="copy-asset-details-from-monitoring-views"></a>모니터링 보기에서 자산 정보의 복사
<!--1357856-->
다음 **모니터링** 작업 영역에서 이제 텍스트 복사를 지원합니다.  

- **배포** 노드에서 배포를 선택하고 **상태 보기**를 클릭합니다. 배포 상태 보기의 **자산 정보** 창에서 하나 이상의 디바이스를 선택합니다.  

- **배포 상태** 노드를 확장하고 **콘텐츠 상태**를 선택합니다. 소프트웨어 항목을 선택하고 **상태 보기**를 클릭합니다. 콘텐츠 상태 보기의 **자산 세부 정보** 창에서 하나 이상의 배포 지점을 선택합니다. 

자산을 마우스 오른쪽 단추로 클릭하고 **복사**를 선택합니다. 이 작업에서는 선택한 자산을 전체 세부 정보가 담긴 쉼표 분리 목록으로 복사합니다. 이 보기에서는 키보드 바로 가기 **CTRL** + **C**도 작동합니다. 

자세한 내용은 [1806 버전의 콘솔 향상](/sccm/core/servers/manage/admin-console#copy-details-in-monitoring-views)을 참조하세요.


### <a name="improvements-to-the-surface-dashboard"></a>Surface 대시보드에 대한 개선 사항
<!--1358654-->
이 릴리스에 포함된 Surface 대시보드의 향상된 기능은 다음과 같습니다.  

- 특정 그래프 섹션을 선택하면 이제 Surface 대시보드에 관련 디바이스 목록이 표시됩니다.  

   - **Surface 디바이스 비율** 타일을 클릭하면 Surface 디바이스 목록이 열립니다.  

   - **상위 5개 펌웨어 버전** 타일에서 막대를 클릭하면 해당 특정 펌웨어 버전으로 Surface 디바이스 목록이 열립니다.  

- Surface 대시보드에서 이러한 디바이스 목록을 볼 때 디바이스를 마우스 오른쪽 단추로 클릭하고 일반 작업을 수행합니다.  

자세한 내용은 [Surface 대시보드](/sccm/core/clients/manage/surface-device-dashboard)를 참조하세요.


### <a name="view-the-currently-signed-on-user-for-a-device"></a>디바이스에 현재 로그온한 사용자 보기
<!--1358202-->
기본적으로 **자산 및 준수** 작업 영역의 **디바이스** 노드는 **현재 로그온한 사용자**에 대한 열을 표시합니다. 컬렉션 특정 디바이스 목록도 표시됩니다. 이 값은 [클라이언트 상태](/sccm/core/clients/manage/monitor-clients#bkmk_indStatus)만큼 최신 상태입니다. 사용자가 로그오프하면 클라이언트가 이 값을 지웁니다. 로그온한 사용자가 없으면 값이 비어 있습니다. 

자세한 내용은 [1806 버전의 콘솔 향상](/sccm/core/servers/manage/admin-console#view-users-for-a-device)을 참조하세요.


### <a name="submit-feedback-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 피드백 제출  
<!--1357542-->

웃는 얼굴 보내기! 이제 Configuration Manager 팀에게 사용자 경험을 직접 알릴 수 있습니다. Configuration Manager 콘솔에서 쉽게 피드백을 보낼 수 있습니다. 칭찬, 문제, 제안 사항 등 모든 피드백에 귀를 기울이겠습니다. Configuration Manager 콘솔의 오른쪽 위에서 리본 위의 웃는 얼굴 단추를 클릭합니다. 이 피드백은 Microsoft의 Configuration Manager 제품 팀에게 바로 전달됩니다. Windows 10 피드백 허브도 사용할 수 있지만, 콘솔 내 피드백 메커니즘을 사용하는 것이 좋습니다.  

자세한 내용은 [1806 버전의 콘솔 향상](/sccm/core/servers/manage/admin-console#send-feedback) 및 [제품 피드백](/sccm/core/understand/find-help#BKMK_1806Feedback)을 참조하세요.



## <a name="other-updates"></a>기타 업데이트

새 기능 외에 이 릴리스에는 버그 수정과 같은 추가 변경 사항도 포함되어 있습니다. 자세한 내용은 [Configuration Manager 현재 분기, 버전 1806의 변경 내용 요약](https://support.microsoft.com/help/4459701)을 참조하세요.

Configuration Manager용 Windows PowerShell cmdlet의 변경 내용에 대한 자세한 내용은 [PowerShell 1806 릴리스 정보](https://docs.microsoft.com/powershell/sccm/1806_release_notes?view=sccm-ps)를 참조하세요.

다음 업데이트 롤업(4462978)은 2018년 10월 24일부터 콘솔에서 사용할 수 있습니다. [Configuration Manager 현재 분기, 버전 1806용 업데이트 롤업](https://support.microsoft.com/help/4462978).


### <a name="hotfixes"></a>핫픽스

다음 추가 핫픽스는 특정 문제를 해결하는 데 사용할 수 있습니다.

| ID | 제목 | 날짜 | 콘솔 내 |
|---------|---------|---------|---------|
| [4346645](https://support.microsoft.com/help/4346645) | System Center Configuration Manager 버전 1806용 업데이트, 첫 번째 웨이브 | 2018년 8월 31일 | 예 |
| [4465865](https://support.microsoft.com/help/4465865) | 소프트웨어 업데이트는 WSUS가 연결되어 있지 않으면 Configuration Manager 환경에서 다운로드되지 않음<br><br>이 업데이트는 업데이트 롤업(4462978)에 포함되어 있음 | 2018년 10월 1일 | 예 |
| [4471892](https://support.microsoft.com/help/4471892) | PXE 응답기는 Configuration Manager 1806의 서브넷에서 작동하지 않음 | 2018년 11월 23일 | 아니요 |
| [4487960](https://support.microsoft.com/help/4487960) | Microsoft Intune 커넥터 인증서가 Configuration Manager에서 갱신되지 않음 | 2019년 1월 18일 | 예 |


## <a name="next-steps"></a>다음 단계

이 버전을 설치할 준비가 되었으면 [Configuration Manager에 대한 업데이트 설치](/sccm/core/servers/manage/updates) 및 [업데이트 1806을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1806)을 참조하세요.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용합니다.  
>
> 다음에 대해 자세히 알아보세요.    
> - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
> - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)

알려진 중요한 문제는 [릴리스 정보](/sccm/core/servers/deploy/install/release-notes)를 참조하세요.

사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1806#post-update-checklist)도 검토하세요.
