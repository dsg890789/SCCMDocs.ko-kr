---
title: 버전 1906의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager 현재 분기의 버전 1906에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.
ms.date: 08/23/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 97e23075-549c-4e45-ab1e-0671027edacf
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 13c9f2e6f6b279aeea13ce2ede66b6d11f2c12a2
ms.sourcegitcommit: e2e07d74779a2f48693ecaa17a5974204949d109
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69999441"
---
# <a name="whats-new-in-version-1906-of-configuration-manager-current-branch"></a>Configuration Manager 현재 분기 버전 1906의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 현재 분기의 1906 업데이트는 콘솔 내 업데이트로 사용할 수 있습니다. 버전 1802 이상을 실행하는 사이트에서 이 업데이트를 적용합니다. <!-- baseline only statement:When installing a new site, it's also available as a baseline version.--> 이 문서에는 Configuration Manager 버전 1906의 변경 내용과 새로운 기능이 요약되어 있습니다.  

이 업데이트를 설치하기 위한 최신 검사 목록을 항상 검토하세요. 자세한 내용은 [업데이트 1906을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1906)을 참조하세요. 사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1906#post-update-checklist)도 검토하세요.

새 Configuration Manager 기능을 모두 활용하려면 사용자를 업데이트한 후 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22what%27s+new+in+version+1906+-+Configuration+Manager%22&locale=en-us`


## <a name="requirement-changes"></a>요구 사항 변경 내용

### <a name="version-1906-client-requires-sha-2-code-signing-support"></a>버전 1906 클라이언트는 SHA-2 코드 서명 지원 필요

<!--SCCMDocs-pr#3404-->
SHA-1 알고리즘의 약점과 업계 표준에 맞출 필요성 때문에 Microsoft는 이제 보다 안전한 SHA-2 알고리즘을 사용하여 Configuration Manager 바이너리에만 서명합니다. 다음 Windows OS 버전에는 SHA-2 코드 서명 지원을 위한 업데이트가 필요합니다.

- Windows 7 SP1
- Windows Server 2008 R2 SP1
- Windows Server 2008 SP2

자세한 내용은 [Windows 클라이언트 필수 조건](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#bkmk_sha2)을 참조하세요.


## <a name="bkmk_infra"></a> 사이트 인프라

### <a name="site-server-maintenance-task-improvements"></a>사이트 서버 유지 관리 작업 개선 사항

<!--3555894-->
이제 사이트 서버의 세부 정보 보기에 있는 해당 탭에서 사이트 서버 유지 관리 작업을 살펴보고 편집할 수 있습니다. 새 **유지 관리 작업** 탭은 다음과 같은 정보를 제공합니다.

- 작업을 사용하는 경우
- 작업 일정
- 마지막 시작 시간
- 마지막 컴파일 시간
- 작업이 완료된 경우

![사이트 서버의 세부 정보 보기에 있는 유지 관리 작업에 대한 새 탭](./media/3555894-maintenance-tasks.png)

자세한 내용은 [유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks#bkmk_MTs1906)을 참조하세요.

### <a name="configuration-manager-update-database-upgrade-monitoring"></a>Configuration Manager 업데이트 데이터베이스 업그레이드 모니터링

<!--4200581-->
Configuration Manager 업데이트를 적용하면 이제 설치 상태 창에서 **ConfigMgr 데이터베이스 업그레이드** 작업 상태를 볼 수 있습니다.

- 데이터베이스 업그레이드가 차단된 경우 **진행 중. 주의 필요**라는 경고가 표시됩니다.
   - cmupdate.log는 데이터베이스 업그레이드를 차단하는 SQL의 프로그램 이름 및 sessionid를 기록합니다.
- 데이터베이스 업그레이드가 더 이상 차단되지 않으면 상태가 **진행 중** 또는 **완료**로 다시 설정됩니다.
   - 데이터베이스 업그레이드가 차단되면 5분마다 업그레이드가 여전히 차단되는지 확인하는 작업이 수행됩니다.

   ![설치하는 동안 데이터베이스 업그레이드 모니터링](./media/4200581-database-upgrade-monitoring.png)

자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates#3-monitor-the-progress-of-updates-as-they-install)를 참조하세요.

### <a name="management-insights-rule-for-ntlm-fallback"></a>NTLM 대체에 대한 관리 인사이트 규칙

<!--4572953-->
관리 인사이트에는 사이트에 보안 수준이 낮은 NTLM 인증 대체 방법이 사용되는지 탐지하는 새 규칙 **NTLM 대체 사용**이 포함되어 있습니다.

자세한 내용은 [관리 인사이트](/sccm/core/servers/manage/management-insights#security)를 참조하세요.

### <a name="improvements-to-support-for-sql-always-on"></a>SQL Always On에 대한 지원 개선 사항

- 설치 프로그램에서 새 동기 복제본 추가<!--3127336-->: 이제 기존 SQL Always On 가용성 그룹에 새 보조 복제본 노드를 추가할 수 있습니다. 수동 프로세스가 아닌 Configuration Manager 설치를 사용하여 이 변경을 수행합니다. 자세한 내용은 [SQL Server Always On 가용성 그룹 구성](/sccm/core/servers/deploy/configure/configure-aoag#bkmk_sync)을 참조하세요.

- 다중 서브넷 장애 조치<!-- SCCMDocs-pr#3734 -->: 이제 SQL Server에서 [MultiSubnetFailover 연결 문자열 키워드](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server#MultiSubnetFailover)를 사용할 수 있습니다. 또한 사이트 서버를 수동으로 구성해야 합니다. 자세한 내용은 [다중 서브넷 장애 조치](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#multi-subnet-failover) 필수 구성 요소를 참조하세요.

- 분산 보기 지원<!-- SCCMDocs-pr#3792 -->: 사이트 데이터베이스를 SQL Server Always On 가용성 그룹에서 호스팅할 수 있으며, 데이터베이스 복제 링크를 사용하도록 설정하여 [분산 보기](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_dbrep)를 사용할 수 있습니다.

    > [!Note]  
    > 이 변경 내용은 SQL Server 클러스터에 적용되지 않습니다.

- 사이트 복구로 SQL Always On 그룹에 데이터베이스를 다시 만들 수 있습니다. 이 프로세스는 수동 및 자동 시딩 어느 쪽에서든 진행이 가능합니다.<!-- SCCMDocs-pr#3846 -->

- 새로운 설치 필수 구성 요소 확인:<!-- SCCMDocs-pr#3899 -->  

    - SQL 가용성 그룹 복제본은 시딩 모드가 모두 동일해야 합니다
    - SQL 가용성 그룹 복제본이 정상 상태여야 합니다

## <a name="bkmk_cloud"></a> 클라우드 연결 관리

### <a name="azure-active-directory-user-group-discovery"></a>Azure Active Directory 사용자 그룹 검색

<!--3611956-->

이제 Azure AD(Azure Active directory)에서 사용자 그룹 및 해당 그룹의 구성원을 검색할 수 있습니다. 사이트가 이전에 검색하지 않은 Azure AD 그룹에서 발견된 사용자는 Configuration Manager에서 사용자 리소스로 추가됩니다. 그룹이 보안 그룹이면 사용자 그룹 리소스 레코드가 생성됩니다. 이 기능은 [시험판 기능](/sccm/core/servers/manage/pre-release-features)이며 사용하도록 설정해야 합니다.

자세한 내용은 [검색 방법 구성](/sccm/core/servers/deploy/configure/configure-discovery-methods#bkmk_azuregroupdisco)을 참조하십시오.

### <a name="synchronize-collection-membership-results-to-azure-active-directory-groups"></a>Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화

<!--3607475-->

이제 Azure AD(Azure Active Directory) 그룹에 대한 컬렉션 멤버 자격 동기화를 사용할 수 있습니다. 이 동기화는 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

동기화를 통해 컬렉션 멤버 자격 결과에 따라 Azure AD 그룹 멤버 자격을 만들어 클라우드에서 기존 온-프레미스 그룹화 규칙을 사용할 수 있습니다. Azure AD 그룹에는 Azure Active Directory 레코드가 있는 디바이스만 반영됩니다. 하이브리드 Azure AD 조인 디바이스와 Azure Active Directory 조인 디바이스가 모두 지원됩니다.

자세한 내용은 [컬렉션 만들기](/sccm/core/clients/manage/collections/create-collections#bkmk_aadcollsync)를 참조하세요.


## <a name="bkmk_da"></a> Desktop Analytics

### <a name="readiness-insights-for-desktop-apps"></a>데스크톱 앱의 준비 상태 인사이트

<!-- 4021225 -->

이제 기간 업무 앱을 비롯한 데스크톱 애플리케이션에 대한 더 자세한 인사이트를 얻을 수 있습니다. 이전 App Health Analyzer 도구 키트는 이제 Configuration Manager 클라이언트와 통합되었습니다. 이 통합은 Desktop Analytics 포털에서 앱 준비 상태 인사이트의 배포 및 관리 효율성을 간소화합니다.

자세한 내용은 [Desktop Analytics의 호환성 평가](/sccm/desktop-analytics/compat-assessment#advanced-insights)를 참조하세요.


### <a name="dalogscollector-tool"></a>DALogsCollector 도구

<!--4622989-->
Configuration Manager 설치 디렉터리의 DesktopAnalyticsLogsCollector.ps1 도구를 사용하여 Desktop Analytics 문제를 해결할 수 있습니다. 이 도구는 몇 가지 기본적인 문제 해결 단계를 실행하고 관련 로그를 단일 작업 디렉터리로 수집합니다.

자세한 내용은 [로그 수집기](/sccm/desktop-analytics/log-collector)를 참조하세요.


## <a name="bkmk_real"></a> 실시간 관리

### <a name="add-joins-additional-operators-and-aggregators-in-cmpivot"></a>CMPivot에서 조인, 추가 연산자 및 집계 추가

<!--4054074-->

CMPivot의 경우, 이제 추가 산술 연산자와 집계뿐 아니라 레지스트리와 파일을 함께 사용하는 것과 같이 쿼리 조인을 추가하는 기능이 생겼습니다.

자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot#bkmk_cmpivot1906)을 참조하세요.

### <a name="cmpivot-standalone"></a>CMPivot 독립 실행형

<!--3555890, 4619340, 4692885 -->

이제 CMPivot을 독립 실행형 앱으로 사용할 수 있습니다. CMPivot 독립 실행형은 **시험판 기능**이며 영어로만 제공됩니다. Configuration Manager 콘솔 외부에서 CMPivot을 실행하여 사용자 환경에 포함된 디바이스의 실시간 상태를 확인할 수 있습니다. 이 변경을 통해 먼저 콘솔을 설치하지 않고도 디바이스에서 CMPivot을 사용할 수 있습니다.

컴퓨터에 콘솔을 설치하지 않은 기술 지원팀 또는 보안 관리자 등의 가상 사용자와 CMPivot 기능을 공유할 수 있습니다. 이러한 다른 가상 사용자는 일반적으로 사용하는 다른 도구와 함께 CMPivot을 사용하여 Configuration Manager를 쿼리할 수 있습니다. 이 풍부한 관리 데이터를 공유하면서 공조하여 여러 역할에서 나타나는 비즈니스 문제를 사전에 해결할 수 있습니다.

자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot#bkmk_standalone) 및 [시험판 기능](/sccm/core/servers/manage/pre-release-features#bkmk_table)을 참조하세요.

### <a name="added-permissions-to-the-security-administrator-role"></a>보안 관리자 역할에 권한 추가

<!--4683130-->

다음 권한이 Configuration Manager의 기본 제공 [**보안 관리자**](/sccm/core/understand/fundamentals-of-role-based-administration#bkmk_Planroles) 역할에 추가되었습니다.

- SMS 스크립트 읽기
- 컬렉션에서 CMPivot 실행
- 인벤토리 보고서 읽기

자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot#bkmk_cmpivot_secadmin1906)을 참조하세요.


## <a name="bkmk_content"></a> 콘텐츠 관리

### <a name="delivery-optimization-download-data-in-client-data-sources-dashboard"></a>클라이언트 데이터 원본 대시보드의 배달 최적화 다운로드 데이터

<!--3555759-->
클라이언트 데이터 원본 대시보드에 이제 [배달 최적화](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization) 데이터가 포함됩니다. 이 대시보드를 통해 환경에서 클라이언트가 어디로부터 콘텐츠를 가져오는지 파악할 수 있습니다.

자세한 내용은 [클라이언트 데이터 원본 대시보드](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)를 참조하세요.

### <a name="use-your-distribution-point-as-an-in-network-cache-server-for-delivery-optimization"></a>배포 지점을 배달 최적화를 위한 네트워크 내 캐시 서버로 사용

<!--3555764-->
이제 배포 지점에 배달 최적화 네트워크 내 캐시(DOINC) 서버를 설치할 수 있습니다. 이 온-프레미스 콘텐츠를 캐시하면 클라이언트들이 전송 최적화 기능을 활용하는 동시에 WAN 링크도 보호할 수 있습니다.

이 캐시 서버는 전송 최적화에 의해 다운로드된 콘텐츠에서 주문형 투명 캐시로 작동합니다. 클라이언트 설정을 사용하여 이 서버가 로컬 Configuration Manager 경계 그룹의 멤버에게만 제공되도록 합니다.

자세한 내용은 [Configuration Manager의 배달 최적화 네트워크 내 캐시](/sccm/core/plan-design/hierarchy/delivery-optimization-in-network-cache)를 참조하세요.


## <a name="bkmk_client"></a> 클라이언트 관리

### <a name="support-for-windows-virtual-desktop"></a>Windows Virtual Desktop 지원

<!--3556025-->
[Windows Virtual Desktop](https://docs.microsoft.com/azure/virtual-desktop/)은 Microsoft Azure 및 Microsoft 365의 미리 보기 기능입니다. 이제 Configuration Manager를 사용하여 Azure에서 Windows를 실행하는 이러한 가상 디바이스를 관리할 수 있습니다.

터미널 서버와 마찬가지로, 이러한 가상 디바이스는 여러 동시 활성 사용자 세션을 허용합니다. 클라이언트 성능에 도움이 되도록 Configuration Manager는 이제 이러한 여러 사용자 세션을 허용하는 모든 디바이스에서 사용자 정책을 해제합니다. 사용자 정책을 사용하도록 설정하더라도 클라이언트가 기본적으로 이러한 디바이스서 정책을 사용하지 않도록 설정하며, 여기에는 Windows Virtual Desktop과 터미널 서버가 포함됩니다.

자세한 내용은 [클라이언트 및 디바이스에 대해 지원되는 OS 버전](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#windows-computers)을 참조하세요.

### <a name="support-center-onetrace-preview"></a>지원 센터 OneTrace(미리 보기)

<!--3555962-->
OneTrace는 지원 센터의 새 로그 뷰어입니다. CMTrace와 비슷하게 작동하며 다음과 같이 향상되었습니다.

- 탭 형식 보기
- 도킹 가능한 창
- 향상된 검색 기능
- 로그 보기를 종료하지 않고 필터 사용 가능
- 스크롤바 힌트로 오류가 있는 클러스터를 신속하게 파악
- 신속한 대용량 파일 로그 열기

![OneTrace 로그 뷰어 스크린샷](./media/3555962-onetrace.png)

자세한 내용은 [지원 센터 OneTrace](/sccm/core/support/support-center-onetrace)를 참조하세요.

### <a name="configure-client-cache-minimum-retention-period"></a>클라이언트 캐시 최소 보존 기간 구성

<!--4485509-->
이제 Configuration Manager 클라이언트 클라이언트가 캐시된 콘텐츠를 유지하는 최소 시간을 지정할 수 있습니다. 이 클라이언트 설정은 공간이 더 필요할 경우 캐시에서 콘텐츠를 제거하기 전에 Configuration Manager 에이전트가 대기해야 하는 최소 시간을 정의합니다. 클라이언트 설정의 **클라이언트 캐시 설정** 그룹에서 다음 설정을 구성합니다. **캐시된 콘텐츠를 제거하기 전까지 최소 기간(분)** .

> [!Note]  
> 같은 클라이언트 설정 그룹에서 **콘텐츠를 공유하도록 정품 OS에서 구성 관리자 클라이언트 사용**의 기존 설정 이름이 이제 **피어 캐시 원본으로 사용**으로 바뀌었습니다. 설정의 동작은 변경되지 않습니다.  

자세한 내용은 [클라이언트 캐시 설정](/sccm/core/clients/deploy/about-client-settings#client-cache-settings)을 참조하세요.


## <a name="bkmk_comgmt"></a> 공동 관리

### <a name="improvements-to-co-management-auto-enrollment"></a>공동 관리 자동 등록 개선 사항

- 이제 새 공동 관리형 디바이스는 해당 Azure AD(Azure Active Directory) *디바이스* 토큰에 따라 Microsoft Intune 서비스에 자동으로 등록됩니다. 사용자가 디바이스에 로그인하여 자동 등록을 시작할 때까지 기다릴 필요가 없습니다. 이렇게 바뀐 덕분에 [등록 상태](/sccm/comanage/how-to-monitor#co-management-enrollment-status)가 *사용자 로그인 보류 중*인 디바이스 수를 줄일 수 있습니다.<!-- 4454491 -->

- 이미 공동 관리에 등록된 디바이스가 있는 고객의 경우, 이제 새 디바이스는 필수 조건을 충족하는 즉시 등록됩니다. 예를 들어 디바이스가 Azure AD에 조인되고 Configuration Manager 클라이언트가 설치된 경우입니다.<!--4321130-->

자세한 내용은 [공동 관리 사용 설정](/sccm/comanage/how-to-enable)을 참조하세요.

### <a name="multiple-pilot-groups-for-co-management-workloads"></a>공동 관리 워크로드를 위한 여러 파일럿 그룹

<!--3555750-->
이제 각 공동 관리 워크플로에 대한 여러 파일럿 컬렉션을 구성할 수 있습니다. 다양한 파일럿 컬렉션을 사용하면 워크로드를 바꿀 때 보다 세분화된 방식을 사용할 수 있습니다.

- **사용 여부** 탭에서 **Intune 자동 등록** 컬렉션을 지정할 수 있습니다.
    - 공동 관리에 등록하고 싶은 모든 클라이언트가 **Intune 자동 등록** 컬렉션에 포함되어야 합니다. 기본적으로 다른 준비 컬렉션의 상위 세트입니다.

- **준비** 탭에서 한 가지 파일럿 컬렉션을 모든 워크로드에 사용하는 대신, 각 워크로드에 사용할 개별 컬렉션을 선택할 수 있습니다.

    ![공동 관리 준비 탭에서 각 워크로드에 사용할 컬렉션을 선택할 수 있습니다.](./media/3555750-co-management-staging-tab.png)

이 옵션은 처음으로 공동 관리를 사용하도록 설정할 때에도 사용할 수 있습니다.

자세한 내용은 [공동 관리 사용 설정](/sccm/comanage/how-to-enable)을 참조하세요.

### <a name="co-management-support-for-government-cloud"></a>정부 클라우드를 위한 공동 관리 지원

<!--4075452-->
미국 정부 고객은 이제 Azure 미국 정부 클라우드(portal.azure.us)에서 공동 관리를 사용할 수 있습니다. 자세한 내용은 [공동 관리 사용 설정](/sccm/comanage/how-to-enable)을 참조하세요.


## <a name="bkmk_app"></a> 애플리케이션 관리

### <a name="filter-applications-deployed-to-devices"></a>디바이스에 배포된 필터 애플리케이션

<!--4451056-->
디바이스를 대상으로 하는 애플리케이션 배포의 사용자 범주가 이제 소프트웨어 센터에 필터로 표시됩니다. 해당 속성의 **소프트웨어 센터** 페이지에서 애플리케이션의 **사용자 범주**를 지정합니다. 그런 다음, 소프트웨어 센터에서 앱을 열고 사용 가능한 필터를 살펴봅니다.

자세한 내용은 [애플리케이션 정보 수동 지정](/sccm/apps/deploy-use/create-applications#bkmk_manual-app)을 참조하세요.

### <a name="application-groups"></a>애플리케이션 그룹

<!--3555907-->
사용자 또는 디바이스 컬렉션을 단일 배포로 보낼 수 있는 애플리케이션 그룹을 만듭니다. 앱 그룹에 대해 지정한 메타데이터는 소프트웨서 센터에 단일 항목으로 표시됩니다. 클라이언트가 특정 순서대로 앱을 설치하도록 그룹에서 순서를 지정할 수 있습니다.

이 기능은 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

자세한 내용은 [애플리케이션 그룹 만들기](/sccm/apps/deploy-use/create-app-groups)를 참조하세요.

### <a name="retry-the-install-of-pre-approved-applications"></a>사전 승인된 애플리케이션의 설치 다시 시도

<!--4336307-->
이제 이전에 사용자 또는 디바이스에 대해 승인한 앱의 설치를 다시 시도할 수 있습니다. 승인 옵션은 사용 가능한 배포에만 해당합니다. 사용자 앱을 제거할 경우 또는 최초 설치 프로세스가 실패한 경우 Configuration Manager가 그 상태를 다시 평가하지 않고 다시 설치합니다. 이 기능을 통해 엔지니어는 지원을 요청하는 사용자에 대해 앱 설치를 신속하게 다시 시도할 수 있습니다.

자세한 내용은 [애플리케이션 승인](/sccm/apps/deploy-use/app-approval)을 참조하세요.

### <a name="install-an-application-for-a-device"></a>디바이스용 애플리케이션 설치

<!--4402180-->
이제 Configuration Manager 콘솔에서 실시간으로 디바이스에 애플리케이션을 설치할 수 있습니다. 이 기능을 사용하면 애플리케이션마다 별도의 컬렉션이 필요하지 않습니다.

자세한 내용은 [디바이스용 애플리케이션 설치](/sccm/apps/deploy-use/install-app-for-device)를 참조하세요.

### <a name="improvements-to-app-approvals"></a>앱 승인 개선 사항

<!--4224910-->
이 릴리스에서는 앱 승인의 다음 사항이 개선되었습니다.

- 콘솔에서 앱 요청을 승인한 후 거부한 경우 이제 다시 승인할 수 있습니다. 승인 후에는 앱이 클라이언트에 다시 설치됩니다.  

- Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역의 **애플리케이션 관리**에서 **승인 요청** 노드의 이름이 **애플리케이션 요청**으로 변경됩니다.<!-- SCCMDocs-pr#4028 -->

- 앱 승인 요청을 제거하는 새 WMI 메서드 **DeleteInstance**가 있습니다. 이 작업은 디바이스에서 앱을 제거하지 않습니다. 아직 설치되어 있지 않으면 사용자가 소프트웨어 센터에서 앱을 설치할 수 없습니다.

- **CreateApprovedRequest** API를 호출하여 디바이스의 앱에 대해 미리 승인된 요청을 만듭니다. 클라이언트에 앱을 자동으로 설치하지 않으려면 **AutoInstall** 매개 변수를 `FALSE`로 설정합니다. 소프트웨어 센터에 앱이 표시되지만 자동으로 설치되지는 않습니다.

자세한 내용은 [애플리케이션 승인](/sccm/apps/deploy-use/app-approval)을 참조하세요.


## <a name="bkmk_osd"></a> OS 배포

### <a name="task-sequence-debugger"></a>작업 순서 디버거

<!--3612274-->
작업 순서 디버거는 새로운 문제 해결 도구입니다. 디버그 모드에서 한 디바이스 컬렉션에 작업 순서를 배포합니다. 이렇게 하면 제어되는 방식으로 작업 순서에 따라 문제 해결 및 조사를 지원할 수 있습니다.

![작업 순서 디버거 스크린샷](./media/3612274-tsdebug.png)

이 기능은 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

자세한 내용은 [작업 순서 디버그](/sccm/osd/deploy-use/debug-task-sequence)를 참조하세요.

### <a name="clear-app-content-from-client-cache-during-task-sequence"></a>작업 순서 중에 클라이언트 캐시에서 앱 콘텐츠 제거

<!--4485675-->
이제 **애플리케이션 설치** 작업 순서 단계에서 단계가 실행된 후 클라이언트 캐시의 앱 콘텐츠를 삭제할 수 있습니다.

자세한 내용은 [작업 순서 단계 정보](/sccm/osd/understand/task-sequence-steps#BKMK_InstallApplication)를 참조하세요.

> [!Important]  
> 이 새 기능을 지원하도록 대상 클라이언트를 최신 버전으로 업데이트합니다.

### <a name="reclaim-sedo-lock-for-task-sequences"></a>작업 순서의 SEDO 잠금 회수

<!--3699337-->
Configuration Manager 콘솔이 응답하지 않는 경우 잠금으로 인해 작업 순서를 더 이상 변경하지 못할 수 있습니다. 이제는 잠긴 작업 순서에 액세스하려고 할 때 **변경 내용을 취소**하고 계속 개체를 편집할 수 있습니다.

자세한 내용은 [작업 순서 관리](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#bkmk_sedo)를 참조하세요.

### <a name="pre-cache-driver-packages-and-os-images"></a>드라이버 패키지 및 OS 이미지 사전 캐시

<!--4224642-->
이제 작업 순서 사전 캐시에는 추가 콘텐츠 형식이 포함됩니다. 이전에는 콘텐츠 사전 캐시가 OS 업그레이드 패키지에만 적용되었습니다. 이제 사전 캐시를 사용하여 다음의 대역폭 사용량을 줄일 수 있습니다.

- OS 이미지
- 드라이버 패키지
- 패키지

자세한 내용은 [사전 캐시 콘텐츠 구성](/sccm/osd/deploy-use/configure-precache-content)을 참조하세요.

### <a name="improvements-to-os-deployment"></a>향상된 OS 배포

이 릴리스에서는 OS 배포의 다음 사항이 개선되었습니다.

- 다음 두 개의 PowerShell cmdlet을 사용하여 [작업 순서 실행](/sccm/osd/understand/task-sequence-steps#child-task-sequence) 단계를 만들고 편집합니다.<!--2839943-->

    - **New-CMTSStepRunTaskSequence**

    - **Set-CMTSStepRunTaskSequence**

- 이제 작업 순서를 실행할 때 변수를 좀 더 쉽게 편집할 수 있습니다. 작업 순서 마법사 창에서 작업 순서를 선택하면 작업 순서 변수를 편집하는 페이지에 **편집** 단추가 있습니다.<!-- 4668846 --> 자세한 내용은 [How to use task sequence variables](/sccm/osd/understand/using-task-sequence-variables#bkmk_set-tswiz)\(작업 순서 변수 사용 방법\)을 참조하세요.

- **BitLocker 사용 안 함** 작업 순서 단계에 새 다시 시작 카운터가 생겼습니다. 이 옵션을 사용하여 BitLocker를 사용하지 않는 상태로 유지하는 다시 시작 횟수를 지정합니다. 이 변경은 작업 순서를 간소화하는 데 도움이 됩니다. 이 단계의 여러 인스턴스를 추가하는 대신 단일 단계를 사용할 수 있습니다. <!--4512937--> 자세한 내용은 [Bitlocker 사용 안 함](/sccm/osd/understand/task-sequence-steps#BKMK_DisableBitLocker)을 참조하세요.

- 새 작업 순서 변수 **SMSTSRebootDelayNext**를 기존의 [SMSTSRebootDelay](/sccm/osd/understand/task-sequence-variables#SMSTSRebootDelay) 변수와 함께 사용하세요. 이후의 다시 부팅이 첫 번째 다시 부팅과 다른 시간 제한으로 수행되도록 하려면 이 새 변수를 다른 값(초)으로 설정합니다. <!--4447680--> 자세한 내용은 [SMSTSRebootDelayNext](/sccm/osd/understand/task-sequence-variables#SMSTSRebootDelayNext)를 참조하세요.

- 작업 순서는 새로운 읽기 전용 변수 **_SMSTSLastContentDownloadLocation**을 설정합니다. 이 변수는 작업 순서에서 콘텐츠를 다운로드했거나 다운로드하려고 시도한 마지막 위치를 포함하고 있습니다. 클라이언트 로그를 구문 분석하는 대신 이 변수를 검사하세요.<!-- 2840337 -->


## <a name="bkmk_userxp"></a> 소프트웨어 센터

### <a name="improvements-to-software-center-tab-customizations"></a>소프트웨어 센터 탭 사용자 지정의 개선 사항

<!--4063773-->
이제 소프트웨어 센터에 최대 5개의 사용자 지정 탭을 추가할 수 있습니다. 또한 이러한 탭이 소프트웨어 센터에 표시되는 순서를 편집할 수 있습니다.

자세한 내용은 [소프트웨어 센터 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-center)을 참조하세요.

### <a name="software-center-infrastructure-improvements"></a>소프트웨어 센터 인프라 개선 사항

<!--3555950-->

이 릴리스에서는 소프트웨어 센터의 인프라가 다음과 같이 개선되었습니다.

- 이제 소프트웨어 센터는 사용자를 대상으로 하는 앱의 관리 지점과 통신합니다. 애플리케이션 카탈로그는 더 이상 사용하지 않습니다. 이러한 변경을 통해 사이트에서 애플리케이션 카탈로그를 보다 쉽게 제거할 수 있습니다.

- 이전에 소프트웨어 센터는 사용 가능한 서버 목록에서 첫 번째 관리 지점을 선택했습니다. 이 릴리스부터 클라이언트가 사용하는 동일한 관리 지점을 사용합니다. 이러한 변경을 통해 소프트웨어 센터에서는 클라이언트와 동일한 할당된 기본 사이트의 관리 지점을 사용할 수 있습니다.

> [!Important]  
> 소프트웨어 센터 및 관리 지점에 대한 이러한 반복적 향상은 애플리케이션 카탈로그 역할의 사용 중지를 위한 것입니다.
>
> - 현재 분기 버전 1806을 기준으로 Silverlight 사용자 환경은 지원되지 않습니다.
> - 버전 1906부터 업데이트된 클라이언트는 사용자가 이용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다.
> - 2019년 10월 31일 이후 첫 번째 현재 분기 릴리스에서는 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  

자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat) 및 [소프트웨어 센터 계획](/sccm/apps/plan-design/plan-for-software-center)을 참조하세요.

### <a name="redesigned-notification-for-newly-available-software"></a>새로 제공되는 소프트웨어의 알림 재설계

<!--3555904-->
**새 소프트웨어를 사용할 수 있습니다** 알림은 특정 애플리케이션과 수정 버전의 사용자에게 한 번만 표시됩니다. 이후에는 사용자가 로그인할 때 알림이 표시되지 않습니다. 애플리케이션이 변경되거나 다시 배포된 경우 애플리케이션에 대한 다른 알림만 표시됩니다.

자세한 내용은 [애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application#end-user-experience)를 참조하세요.

### <a name="more-frequent-countdown-notifications-for-restarts"></a>다시 시작에 대한 카운트다운 알림 빈도 증가

<!--3976435-->

이제 중간 카운트다운 알림을 통해 보류 중인 다시 시작을 최종 사용자에게 미리 알리는 빈도가 늘었습니다. **컴퓨터 다시 시작** 페이지의 **클라이언트 설정**에서 일시적 알림의 간격을 정의할 수 있습니다. 마지막 카운트다운 알림 때까지 보류 중인 다시 시작에 대해 사용자에게 다시 알리는 빈도를 구성하려면 **컴퓨터 다시 시작 카운트다운 알림 다시 알림 기간 지정(분)** 값을 변경하세요.

또한 **사용자가 로그오프되거나 컴퓨터가 다시 시작되기 전의 간격(분)을 표시하는 임시 알림을 사용자에게 표시**의 최댓값이 1440분(24시간)에서 20160분(2주)으로 늘어났습니다.

자세한 내용은 [디바이스 다시 시작 알림](/sccm/core/clients/deploy/device-restart-notifications)과 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#computer-restart)를 참조하세요.

### <a name="direct-link-to-custom-tabs-in-software-center"></a>소프트웨어 센터의 사용자 지정 탭에 대한 직접 링크

<!--4655176-->

이제 사용자에게 소프트웨어 센터의 [사용자 지정 탭](/sccm/core/clients/deploy/about-client-settings#software-center-tab-visibility)에 대한 직접 링크를 제공할 수 있습니다.

다음 URL 형식을 사용하여 특정 탭에 대한 소프트웨어 센터를 엽니다.

`softwarecenter:page=CustomTab1`

`CustomTab1` 문자열은 유효한 첫 번째 사용자 지정 탭입니다.

예를 들어 Windows **실행** 창에 이 URL을 입력합니다.

소프트웨어 센터에서 이 구문을 사용하여 기본 탭을 열 수도 있습니다.

|명령줄  |탭  |
|---------|---------|
|`AvailableSoftware`|애플리케이션|
|`Updates`|업데이트|
|`OSD`|운영 체제|
|`InstallationStatus`|설치 상태|
|`Compliance`|디바이스 정책 준수|
|`Options`|Options|

자세한 내용은 [소프트웨어 센터 탭 표시 여부](/sccm/core/clients/deploy/about-client-settings#software-center-tab-visibility)를 참조하세요.

## <a name="bkmk_sum"></a> 소프트웨어 업데이트

### <a name="additional-options-for-wsus-maintenance"></a>WSUS 유지 관리 추가 옵션

<!--4110109-->
이제 정상 소프트웨어 업데이트 지점을 유지 관리하기 위해 Configuration Manager가 실행할 수 있는 WSUS 유지 관리 작업이 추가되었습니다. 모든 동기화 후 WSUS 유지 관리가 발생합니다. Configuration Manager는 이제 WSUS에서 만료된 업데이트를 거절하는 것 외에 다음을 수행할 수 있습니다.

- 사용되지 않는 업데이트를 WSUS 데이터베이스에서 제거.
- 비클러스터형 인덱스를 WSUS 데이터베이스에 추가하여 WSUS 정리 성능 개선.

자세한 내용은 [소프트웨어 업데이트 유지 관리](/sccm/sum/deploy-use/software-updates-maintenance#wsus-cleanup-starting-in-version-1906)를 참조하세요.

### <a name="configure-the-default-maximum-run-time-for-software-updates"></a>소프트웨어 업데이트에 대한 기본 최대 실행 시간 구성

<!--3734426-->

이제 소프트웨어 업데이트 설치를 완료해야 하는 최대 시간을 지정할 수 있습니다. 소프트웨어 업데이트 지점의 **최대 실행 시간** 탭에서 다음 항목을 지정할 수 있습니다.

- **Windows 기능 업데이트의 최대 실행 시간(분)**
- **Office 365 업데이트 및 Windows 비기능 업데이트의 최대 실행 시간(분)**

자세한 내용은 [소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates#bkmk_maxruntime)을 참조하세요.

### <a name="configure-dynamic-update-during-feature-updates"></a>기능 업데이트 동안 동적 업데이트 구성

<!--4062619-->

새 클라이언트 설정을 사용하여 Windows 10 기능 업데이트 설치 중에 [동적 업데이트](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/The-benefits-of-Windows-10-Dynamic-Update/ba-p/467847)를 구성합니다. 동적 업데이트에서는 Windows 설치 중에 언어 팩, 주문형 기능, 드라이버, 누적 업데이트를 다운로드하라는 지시를 인터넷에서 클라이언트에게 전달하여 설치를 진행합니다.

자세한 내용은 [소프트웨어 업데이트 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-updates) 및 [Windows를 서비스로 관리](/sccm/osd/deploy-use/manage-windows-as-a-service)를 참조하세요.

### <a name="new-windows-10-version-1903-and-later-product-category"></a>새 Windows 10 버전 1903 이상 제품 범주

<!--4682946-->

**Windows 10 버전 1903 이상**이 이전 버전처럼 **Windows 10** 제품의 일부가 아닌 제품 자체로 Microsoft 업데이트에 추가되었습니다. 이번 변화로 인해 클라이언트가 이러한 업데이트를 확인할 수 있도록 여러 수동 단계를 수행해야 했습니다. 새 제품에 대해 수행해야 하는 수동 단계의 수를 줄일 수 있었습니다.

Configuration Manager 버전 1906으로 업데이트하고 **Windows 10** 제품을 동기화하도록 선택한 경우 다음 작업이 자동으로 수행됩니다.

- **Windows 10 버전 1903 이상** 제품이 동기화에 추가됩니다.
- **Windows 10** 제품을 포함하고 있는 자동 배포 규칙은 **Windows 10 버전 1903 이상**을 포함하도록 업데이트됩니다.
- **Windows 10 버전 1903 이상** 제품을 포함하도록 서비스 플랜이 업데이트됩니다.

자세한 내용은 [동기화할 분류 및 제품 구성](/sccm/sum/get-started/configure-classifications-and-products), [서비스 플랜](/sccm/osd/deploy-use/manage-windows-as-a-service#servicing-plan-workflow), [배포 규칙 자동화](/sccm/sum/deploy-use/automatically-deploy-software-updates#bkmk_adr-process)를 참조하세요.

### <a name="drill-through-required-updates"></a>필수 업데이트 드릴스루

<!--4224414-->
이제 규정 준수 통계를 드릴스루하여 특정 소프트웨어 업데이트가 필요한 디바이스를 확인할 수 있습니다. 디바이스 목록을 보려면 디바이스가 속한 업데이트 및 컬렉션을 볼 수 있는 사용 권한이 필요합니다. 디바이스 목록을 드릴다운하려면 업데이트 **요약** 탭의 원형 차트 옆에 있는 **필수 보기** 하이퍼링크를 선택합니다. 하이퍼링크를 클릭하면 업데이트가 필요한 디바이스를 볼 수 있는 **디바이스**의 임시 노드로 이동합니다.

**필수 보기** 하이퍼링크는 다음 위치에서 사용할 수 있습니다.

   - **소프트웨어 라이브러리** > **소프트웨어 업데이트** > **모든 소프트웨어 업데이트**
   - **소프트웨어 라이브러리** > **Windows 10 서비스** > **모든 Windows 10 업데이트**
   - **소프트웨어 라이브러리** > **Office 365 클라이언트 관리** > **Office 365 업데이트**

자세한 내용은 [소프트웨어 업데이트 모니터링](/sccm/sum/deploy-use/monitor-software-updates#drill-through-required-updates), [Windows를 서비스로 관리](/sccm/osd/deploy-use/manage-windows-as-a-service#drill-through-required-updates), [Office 365 ProPlus 업데이트 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates#drill-through-required-office-365-updates)를 참조하세요.


## <a name="bkmk_o365"></a> Office 관리

### <a name="office-365-proplus-upgrade-readiness-dashboard"></a>Office 365 ProPlus 업그레이드 준비 대시보드

<!--4021125-->

Office 365 ProPlus로 업그레이드할 준비가 완료된 디바이스를 편리하게 확인할 수 있도록 하기 위해 새로운 준비 대시보드가 제공됩니다. 여기에는 Configuration Manager 현재 분기 버전 1902에 릴리스된 **Office 365 ProPlus 업그레이드 준비** 타일이 포함되어 있습니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동한 후 **Office 365 클라이언트 관리**를 확장하고 **Office 365 ProPlus 업그레이드 준비**노드를 선택합니다.

대시보드, 필수 조건 및 이 데이터 사용 방법에 대한 자세한 내용은 [Office 365 ProPlus 준비를 위한 통합](/sccm/sum/deploy-use/office-365-dashboard#office-365-proplus-upgrade-readiness-dashboard)을 참조하세요.


## <a name="bkmk_protect"></a> 보호

### <a name="windows-defender-application-guard-file-trust-criteria"></a>Windows Defender Application Guard 파일 신뢰 기준

<!--3555858-->

사용자가 일반적으로 WDAG(Windows Defender Application Guard)에서 열리는 파일을 신뢰할 수 있는 새 정책 설정이 있습니다. 성공적으로 완료되면 파일이 WDAG 안이 아니라 호스트 디바이스에서 열립니다.

자세한 내용은 [Windows Defender Application Guard 정책 만들기 및 배포](/sccm/protect/deploy-use/create-deploy-application-guard-policy#bkmk_FM)를 참조하세요.


## <a name="bkmk_admin"></a> Configuration Manager 콘솔

### <a name="role-based-access-for-folders"></a>폴더의 역할 기반 액세스 제어

<!--3600867-->

이제 폴더에 보안 범위를 설정할 수 있습니다. 폴더의 개체에 대한 액세스 권한은 있지만 폴더에 대한 액세스 권한은 없는 경우 개체를 볼 수 없습니다. 마찬가지로, 폴더에 대한 액세스 권한은 있지만 폴더의 파일에 대한 액세스 권한은 없는 경우 개체를 볼 수 없습니다. 폴더를 마우스 오른쪽 단추로 클릭하고 **보안 범위 설정**을 선택한 다음 적용할 보안 범위를 선택하세요.

자세한 내용은 [Configuration Manager 콘솔 사용](/sccm/core/servers/manage/admin-console#tips)과 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration#bkmk_config-folder)을 참조하세요.

### <a name="add-smbios-guid-column-to-device-and-device-collection-nodes"></a>디바이스 및 디바이스 컬렉션 노드에 SMBIOS GUID 열 추가

<!--4526580-->
**디바이스** 및 **디바이스 컬렉션** 노드에서 이제 새로운 **SMBIOS GUID** 열을 추가할 수 있습니다. 이 값은 시스템 리소스 클래스의 **BIOS GUID** 속성과 같습니다. 디바이스 하드웨어의 고유 식별자입니다.

### <a name="administration-service-support-for-security-nodes"></a>보안 노드에 대한 관리 서비스 지원

<!--4223683-->
이제 관리 서비스를 사용하도록 Configuration Manager 콘솔의 일부 노드를 설정할 수 있습니다. 이 변화 덕분에 콘솔이 WMI 대신 HTTPS를 통해 SMS 공급자와 통신할 수 있습니다.

자세한 정보는 [관리 서비스](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_admin-service)를 참조하세요.

> [!Note]
> 버전 1906부터 사이트 속성의 **클라이언트 컴퓨터 통신** 탭의 이름이 **통신 보안**으로 바뀝니다.<!-- SCCMDocs#1645 -->  

### <a name="collections-tab-in-devices-node"></a>디바이스 노드의 컬렉션 탭

<!--4616810-->
**자산 및 규정 준수** 작업 영역의 **디바이스** 노드로 이동하여 디바이스를 선택합니다. 세부 정보 창에서 새 **컬렉션** 탭으로 전환합니다. 이 탭은 이 디바이스를 포함하는 컬렉션을 나열합니다.

> [!Note]  
> - 이 탭은 현재 **디바이스 컬렉션** 노드의 디바이스 하위 노드에서 사용할 수 없습니다. 예를 들어, 컬렉션에서 **멤버 표시** 옵션을 선택할 때입니다.
> - 일부 사용자에게는 이 탭이 예상대로 채워지지 않을 수 있습니다. 디바이스가 속한 컬렉션의 전체 목록을 확인하려면 **전체 관리자** 보안 역할이 있어야 합니다. 이것은 알려진 문제입니다. <!--5107309-->

### <a name="task-sequences-tab-in-applications-node"></a>애플리케이션 노드의 작업 순서 탭

<!--4616810-->
**소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 펼치고 **애플리케이션** 노드로 이동한 다음, 애플리케이션을 선택합니다. 세부 정보 창에서 새 **작업 순서** 탭으로 전환합니다. 이 탭은 이 애플리케이션을 참조하는 작업 순서를 나열합니다.

### <a name="show-collection-name-for-scripts"></a>스크립트의 컬렉션 이름 표시

<!--4616810-->
**모니터링** 작업 영역에서 **스크립트 상태** 노드를 선택합니다. 이제 ID와 함께 **컬렉션 이름**이 나열됩니다.

### <a name="real-time-actions-from-device-lists"></a>디바이스 목록에서 실시간 작업

<!--4616810-->
몇 가지 방법으로 **자산 및 규정 준수** 작업 영역의 **디바이스**에서 디바이스 목록을 표시할 수 있습니다.

- **자산 및 규정 준수** 작업 영역에서 **디바이스 컬렉션** 노드를 선택합니다. 디바이스 컬렉션을 선택하고 **멤버 표시** 작업을 선택합니다. 이 작업을 수행하면 해당 컬렉션에 대한 디바이스 목록이 있는 **디바이스** 노드의 하위 노드가 열립니다.  

  - 컬렉션 하위 노드를 선택하면 리본의 컬렉션 그룹에서 **CMPivot**을 시작할 수 있습니다.  

- **모니터링** 작업 영역에서 **배포** 노드를 선택합니다. 배포를 선택하고 리본에서 **상태 보기** 작업을 선택합니다. 배포 상태 창에서 총 자산을 두 번 클릭하여 디바이스 목록까지 드릴스루합니다.  

  - 이 목록의 디바이스를 선택하면 리본의 디바이스 그룹에서 **CMPivot** 및 **스크립트 실행**을 시작할 수 있습니다.  

### <a name="order-by-program-name-in-task-sequence"></a>작업 순서에서 프로그램 이름별로 정렬

<!--4616810-->
**소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 펼치고 **작업 순서** 노드를 선택합니다. 작업 순서를 편집하고 [패키지 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallPackage) 단계를 선택하거나 추가합니다. 패키지에 둘 이상의 프로그램이 있는 경우 이제 드롭다운 목록이 프로그램을 사전순으로 정렬합니다.

### <a name="correct-names-for-client-operations"></a>클라이언트 작업의 올바른 이름

<!--4616810-->
**모니터링** 작업 영역에서 **클라이언트 작업**을 선택합니다. **다음 소프트웨어 업데이트 지점으로 전환** 작업의 이름이 이제 제대로 지정되었습니다.


## <a name="bkmk_deprecated"></a> 사용되지 않는 기능 및 운영 체제

[제거되는 항목과 사용되지 않는 항목](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)에서 구현되기 전의 지원 변경 내용을 알아보세요.

버전 1906에서는 다음 기능이 지원되지 않습니다.  

- 새 애플리케이션 카탈로그 역할을 설치할 수 없습니다. 업데이트된 클라이언트는 사용자가 사용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 자세한 내용은 [소프트웨어 센터 계획](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)을 참조하세요.

버전 1906에서는 다음 제품이 지원되지 않습니다.  

- Windows CE 7.0
- Windows 10 Mobile
- Windows 10 Mobile Enterprise


## <a name="other-updates"></a>기타 업데이트

이 버전부터 다음 기능은 더 이상 시험판 기능이 아닙니다.

- [SMS 공급자 관리 서비스](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_admin-service)
- [Device Guard 관리](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)

 새 기능 외에 이 릴리스에는 버그 수정과 같은 추가 변경 사항도 포함되어 있습니다. 자세한 내용은 [Configuration Manager 현재 분기 버전 1906의 변경 내용 요약](https://support.microsoft.com/help/4514258)을 참조하세요.

Configuration Manager용 Windows PowerShell cmdlet의 변경 내용에 대한 자세한 내용은 [PowerShell 버전 1906 릴리스 정보](https://docs.microsoft.com/powershell/sccm/1906-release-notes?view=sccm-ps)를 참조하세요.<!-- link is not live yet; will be published before this release branch -->

<!--
The following update rollup (4486457) is available in the console starting on 25 January 2019: [Update rollup for Configuration Manager current branch, version 1902](https://support.microsoft.com/help/4486457).

### Hotfixes

The following additional hotfixes are available to address specific issues:

| ID | Title | Date | In-console |
|---------|---------|---------|---------|
| [4487960](https://support.microsoft.com/help/4487960) | Microsoft Intune connector certificate does not renew in Configuration Manager | 18 January 2019 | Yes |

> [!Note]  
> Starting in version 1902, in-console hotfixes now have supersedence relationships. For more information, see [Supersedence for in-console hotfixes](/sccm/core/servers/manage/updates#bkmk_supersede).
-->


## <a name="next-steps"></a>다음 단계

<!--At this time, version 1906 is released for the early update ring. To install this update, you need to opt in. For more information, see [Early update ring](/sccm/core/servers/manage/checklist-for-installing-update-1906#early-update-ring). -->
2019년 8월 16일부터는 모든 고객이 설치할 수 있도록 버전 1906이 전 세계적으로 제공됩니다.

이 버전을 설치할 준비가 되었으면 [Configuration Manager에 대한 업데이트 설치](/sccm/core/servers/manage/updates) 및 [업데이트 1906을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1906)을 참조하세요.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용합니다.  
>
> 다음에 대해 자세히 알아보세요.
>
> - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
> - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)  

알려진 중요한 문제는 [릴리스 정보](/sccm/core/servers/deploy/install/release-notes)를 참조하세요.

사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1906#post-update-checklist)도 검토하세요.
