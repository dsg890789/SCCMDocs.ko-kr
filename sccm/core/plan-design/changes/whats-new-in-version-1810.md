---
title: 버전 1810의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager 최신 라인인 1810 버전에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4812324b-e6aa-4431-bf1d-9fcd763a8caa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 80c4798a93d2424759b85b7d8fe106b9251714a4
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52458177"
---
# <a name="whats-new-in-version-1810-of-configuration-manager-current-branch"></a>Configuration Manager 1810 버전의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 현재 분기에 대한 1810 업데이트는 콘솔 내 업데이트로 사용할 수 있습니다. 1710, 1802 또는 1806 버전을 실행하는 사이트에서 이 업데이트를 적용합니다. <!-- baseline only statement: When installing a new site, it's also available as a baseline version.-->

이 업데이트를 설치하기 위한 최신 검사 목록을 항상 검토하세요. 자세한 내용은 [업데이트 1810을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1810)을 참조하세요. 사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist)도 검토하세요.

> [!Note]  
> 이 문서는 현재 이 버전의 모든 중요한 기능을 나열합니다. 그러나 일부 섹션은 새 기능에 대한 추가 정보가 있는 업데이트된 콘텐츠에 아직 연결되지 않았습니다. 이 페이지에서 정기적으로 업데이트를 확인하세요. 변경 내용은 ***[업데이트]*** 태그로 표시됩니다. 이 표시는 콘텐츠가 최종 버전이 되면 제거될 것입니다.  

<!--
Aside from new features, this release also includes additional changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 1810](https://support.microsoft.com/help/4459701).

For more information on changes to the Windows PowerShell cmdlets for Configuration Manager, see [PowerShell 1810 Release Notes](https://docs.microsoft.com/powershell/sccm/1810_release_notes?view=sccm-ps).

The following additional updates to this release are also now available:
- [Update rollup for Configuration Manager current branch, version 1810](https://support.microsoft.com/help/4462978)
-->

> [!Important]  
> 새 Configuration Manager 기능을 활용하려면 먼저 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.

이 문서는 Configuration Manager, 버전 1810에서 변경 내용 및 새로운 기능을 요약합니다.  



## <a name="bkmk_deprecated"></a> 사용되지 않는 기능 및 운영 체제

[제거되는 항목과 사용되지 않는 항목](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated)에서 구현되기 전의 지원 변경 내용을 알아보세요.

2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 기능이 사용되지 않습니다. 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  

Mac 및 Linux(모든 버전)용 SCEP(System Center Endpoint Protection)에 대한 지원은 2018년 12월 31일에 종료됩니다. Mac용 SCEP 및 Linux용 SCEP에 대한 새 바이러스 정의는 지원이 종료된 후에 중단될 수 있습니다. 자세한 내용은 [지원 종료 블로그 게시물](https://go.microsoft.com/fwlink/?linkid=870182)을 참조하세요.

Azure의 클래식 서비스 배포는 이제 Configuration Manager에서 사용되지 않습니다. 클라우드 관리 게이트웨이 및 클라우드 배포 지점에 대해 Azure Resource Manager 배포를 사용하기 시작합니다. 자세한 내용은 [CMG 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager)을 참조하세요.
<!--
Version 1810 drops support for the following products:
-->



## <a name="bkmk_infra"></a> 사이트 인프라

### <a name="support-for-windows-server-2019"></a>Windows Server 2019에 대한 지원
<!--1359195--> Configuration Manager는 이제 사이트 시스템으로 Windows Server 2019 및 Windows Server, 버전 1809를 지원합니다. 

자세한 내용은 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)를 참조하세요.


### <a name="hierarchy-support-for-site-server-high-availability"></a>사이트 서버 고가용성에 대한 계층 구조 지원
<!--1358224--> 중앙 관리 사이트 및 자식 기본 사이트는 이제 수동 모드의 추가 사이트 서버를 가질 수 있습니다. 

<!--For more information, see [Site server high availability](/sccm/core/servers/deploy/configure/site-server-high-availability).-->


### <a name="improvements-to-setup-prerequisites"></a>설치 필수 구성 요소에 대한 개선 사항

버전 1810을 설치하거나 해당 버전으로 업데이트하는 경우 Configuration Manager 설치는 이제 다음과 같은 필수 구성 요소 검사를 포함하거나 개선합니다.

- **시스템 다시 시작 보류 중**: 이 필수 구성 요소 검사는 이제 복원력이 향상되었습니다. Windows 기능에 대한 추가 레지스트리 키를 확인합니다. 자세한 내용은 [시스템 다시 시작 보류 중](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#pending-system-restart)을 참조하세요. <!--SCCMDocs-pr issue 3010-->  

- **SQL 변경 내용 추적 정리**: 사이트 데이터베이스에 SQL 변경 내용 추적 데이터의 백로그가 있는 경우 새 검사 이 백로그를 확인하고 지우는 절차를 포함한 자세한 내용은 [SQL 변경 내용 추적 정리](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#bkmk_changetracking)를 참조하세요. <!--SCCMDocs-pr issue 3023-->  

<!-- - **SQL Native Client version**: This prerequisite check is updated for versions of SQL Native Client that support TLS 1.2. The minimum version is 11.4.7001.0. For more information, see [SQL Native Client version](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#sql-native-client). <!--SCCMDocs-pr issue 3094->  
 -->
- **Windows 클러스터 노드의 사이트 시스템**: Configuration Manager 설치 프로세스는 장애 조치(failover) 클러스터링을 위한 Windows 역할이 있는 컴퓨터에서 사이트 서버 역할의 설치를 더 이상 차단하지 않습니다. SQL Always On에는 이 역할이 필요하므로 이전에는 사이트 서버에 사이트 데이터베이스를 공동 배치할 수 없었습니다. 이 변경을 사용하면 SQL Always On 및 사이트 서버를 수동 모드에서 사용하여 더 적은 수의 서버로 고가용성 사이트를 만들 수 있습니다. 자세한 내용은 [Windows 장애 조치(failover) 클러스터](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#windows-failover-cluster)를 참조하세요. <!--1359132-->  




### <a name="new-permission-for-client-notification-actions"></a>클라이언트 알림 작업에 대한 새 권한
<!--SCCMDocs-pr issue #2972--> 클라이언트 알림 작업은 이제 SMS_Collection 클래스에서 **알림 리소스** 권한이 필요합니다. 다음 기본 제공 역할은 기본적으로 이 권한을 가집니다.
- 전체 관리자  
- 인프라 관리자  

클라이언트 알림 작업을 사용해야 하는 사용자 지정 역할에 이 권한을 추가합니다. 

자세한 내용은 [클라이언트 알림](/sccm/core/clients/manage/client-notification)을 참조하세요.



## <a name="bkmk_content"></a> 콘텐츠 관리

### <a name="new-boundary-group-options"></a>새 경계 그룹 옵션
<!--1358749--> 이제 경계 그룹에는 사용자 환경에서 콘텐츠 배포를 보다 세밀하게 제어할 수 있는 다음 추가 설정이 포함됩니다.

- **같은 서브넷 내의 피어보다 배포 지점 선호**: 기본적으로 관리 지점은 콘텐츠 위치 목록의 맨 위에 피어 캐시 원본을 우선적으로 배치합니다. 이 설정은 피어 캐시 원본과 동일한 서브넷에 있는 클라이언트의 우선 순위를 반대로 바꿉니다.  

- **배포 지점보다 클라우드 배포 지점 선호**: 인터넷 연결이 더 빠른 지점이 있는 경우 이제 클라우드 콘텐츠에 우선 순위를 지정할 수 있습니다.  

자세한 내용은 [피어 다운로드를 위한 경계 그룹 옵션](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgoptions)을 참조하세요.


### <a name="management-insights-rule-for-peer-cache-source-client-version"></a>피어 캐시 원본 클라이언트 버전의 관리 인사이트 규칙
<!-- 1358008 --> **관리 인사이트** 노드에는 피어 캐시 원본으로 사용되지만 1806 이전 클라이언트 버전에서 업그레이드되지 않은 클라이언트를 식별하는 새 규칙이 있습니다. 새 규칙은 **피어 캐시 원본을 최신 버전의 Configuration Manager 클라이언트로 업그레이드**이고 새 **자동 유지 관리** 규칙 그룹의 일부입니다. 1806 이전 클라이언트는 1806 이상 버전을 실행하는 클라이언트의 피어 캐시 원본으로 사용될 수 없습니다. **작업 수행**을 선택하여 클라이언트 목록을 표시하는 장치 보기를 엽니다. 

자세한 내용은 [관리 인사이트](/sccm/core/servers/manage/management-insights)를 참조하세요.



## <a name="bkmk_client"></a> 클라이언트 관리

### <a name="new-client-notification-action-to-wake-up-device"></a>디바이스 절전 모드를 해제하는 새 클라이언트 알림 작업
<!--1317364--> 클라이언트가 사이트 서버와 동일한 서브넷에 있지 않더라도 Configuration Manager 콘솔에서 클라이언트의 절전 모드를 해제할 수 있습니다. 유지 관리를 수행하거나 디바이스를 쿼리해야 하는 경우 절전 상태의 원격 클라이언트로 인해 제한되지 않습니다. 사이트 서버는 클라이언트 알림 채널을 사용하여 동일한 원격 서브넷에서 깨어 있는 다른 클라이언트를 식별합니다. 그런 다음, 깨어 있는 클라이언트는 wake on LAN 요청(매직 패킷)을 전송합니다.

<!--For more information, see [Plan how to wake up clients](/sccm/core/clients/deploy/plan/plan-wake-up-clients).-->


### <a name="improvements-to-collection-evaluation"></a>컬렉션 평가의 개선 사항
<!--1358981--> 컬렉션 평가 동작의 다음 변경 내용이 사이트 성능을 개선할 수 있습니다.  
 
- 이전에 쿼리 기반 컬렉션에서 일정을 구성한 경우 사이트는 컬렉션 설정 **이 컬렉션에 대한 전체 업데이트 예약**을 사용하도록 설정했는지 여부에 관계없이 쿼리를 계속 평가합니다. 일정을 완전히 사용하지 않으려면 일정을 **없음**으로 변경해야 했습니다. 이제 이 설정을 사용하지 않도록 설정하면 사이트가 일정을 지웁니다. 컬렉션 평가 일정을 지정하려면 **이 컬렉션에 대한 전체 업데이트 예약** 옵션을 사용하도록 설정합니다.  

- **모든 시스템** 같은 기본 제공 컬렉션의 평가를 사용하지 않도록 설정할 수 없지만, 현재 일정을 구성할 수는 있습니다. 이 동작을 사용하면 비즈니스 요구 사항을 충족하는 시간에 이 작업을 사용자 지정할 수 있습니다. 

<!--For more information, see [How to create collections](/sccm/core/clients/manage/collections/create-collections).-->


### <a name="improvement-to-client-installation"></a>클라이언트 설치 기능 개선
<!--1358840--> Configuration Manager 클라이언트를 설치할 때 ccmsetup 프로세스는 관리 지점에 연결하여 필요한 콘텐츠를 찾습니다. 이전에는 이 프로세스에서 관리 지점이 클라이언트의 현재 경계 그룹에 있는 배포 지점만 반환합니다. 사용 가능한 콘텐츠가 없는 경우 설치 프로세스가 관리 지점에서 콘텐츠를 다운로드하는 것으로 대체됩니다. 필요한 콘텐츠가 있을 수 있는 다른 경계 그룹의 배포 지점으로 대체하는 옵션은 없습니다. 이제 관리 지점은 경계 그룹 구성을 기준으로 배포 지점을 반환합니다. 

자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_ccmsetup)을 참조하세요.


### <a name="improvements-to-internet-based-client-setup"></a>인터넷 기반 클라이언트 설정의 개선 사항
<!--1359181-->
<!--move this under co-management?--> 이 릴리스는 인터넷에서 클라이언트의 Configuration Manager 클라이언트 설정 프로세스를 추가로 간소화합니다. 사이트는 추가 Azure AD(Azure Active Directory) 정보를 CMG(클라우드 관리 게이트웨이)에 게시합니다. Azure AD에 가입된 클라이언트는 가입된 동일한 테넌트를 사용하여 ccmsetup 프로세스 중에 CMG에서 이 정보를 가져옵니다. 이 동작은 둘 이상의 Azure AD 테넌트가 있는 환경의 공동 관리에 디바이스를 등록하는 작업을 추가로 간소화합니다. 이제 유일한 두 개의 필수 ccmsetup 속성은 **CCMHOSTNAME** 및 **SMSSiteCode**입니다.

<!--For more information, see [Prepare Windows 10 devices for co-management](https://docs.microsoft.com/en-us/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client).-->



## <a name="bkmk_comgmt"></a> 공동 관리

### <a name="required-app-compliance-policy-for-co-managed-devices"></a>공동 관리하는 디바이스의 필수 앱 규정 준수 정책
<!--1358196--> Configuration Manager에서 필수 애플리케이션의 규정 준수 정책 규칙을 정의합니다. 이 앱 평가는 공동 관리하는 디바이스에 대해 Microsoft Intune으로 전송되는 전체 준수 상태의 일부입니다.

<!--For more information, see [Co-management for Windows 10 devices](/sccm/core/clients/manage/co-management-overview).-->


### <a name="improvement-to-co-management-dashboard"></a>공동 관리 대시보드 기능 개선
<!--1358980--> 공동 관리 대시보드가 다음과 같은 좀 더 자세한 정보로 개선되었습니다.  

- **공동 관리 등록 상태** 타일에 추가 상태가 포함됩니다.

- 깔때기형 차트가 있는 새 **공동 관리 상태** 타일은 등록 프로세스의 상태를 보여줍니다.

- **등록 오류** 수를 표시하는 새 타일

![상위 4개의 타일을 보여 주는 공동 관리 대시보드 스크린샷](media/1358980-comgmt-dashboard.png)

자세한 내용은 [공동 관리 대시보드](/sccm/core/clients/manage/co-management-dashboard)를 참조하세요.



<!-- ## <a name="bkmk_compliance"></a> Compliance settings -->



## <a name="bkmk_app"></a> 응용 프로그램 관리

### <a name="convert-applications-to-msix"></a>애플리케이션을 MSIX로 변환
<!--1359029--> 버전 1806부터 Configuration Manager는 새 Windows 10 앱 패키지(.msix) 형식의 배포를 지원합니다. 이제 기존 Windows Installer(.msi) 애플리케이션을 MSIX 형식으로 변환할 수 있습니다.

<!--For more information, see [Create Windows applications](/sccm/apps/get-started/creating-windows-applications#bkmk_general).  this might move to a new section for msix-->


### <a name="repair-applications"></a>애플리케이션 복구
<!--1357866--> Windows Installer 및 스크립트 설치 관리자 배포 유형에 대한 복구 명령줄을 지정합니다. 그런 다음, 배포에서 옵션을 활성화하는 경우 소프트웨어 센터에서 애플리케이션을 **복구**하는 새 단추를 사용할 수 있습니다. 복구 프로그램을 사용하여 애플리케이션을 구성하는 경우 사용자가 소프트웨어 센터에서 명령을 시작할 수 있습니다. 

자세한 내용은 [애플리케이션 만들기](/sccm/apps/deploy-use/create-applications#bkmk_dt-content) 및 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications#bkmk_deploy-settings)를 참조하세요.


### <a name="approve-application-requests-via-email"></a>이메일을 통해 애플리케이션 요청 승인
<!--1321550--> 애플리케이션 승인 요청에 대한 이메일 알림을 구성합니다. 사용자가 애플리케이션을 요청하면 메일을 받게 됩니다. 메일의 링크를 클릭하면 Configuration Manager 콘솔을 사용하지 않고 요청을 승인 또는 거부할 수 있습니다.

자세한 내용은 [애플리케이션 승인](/sccm/apps/deploy-use/app-approval)을 참조하세요.


### <a name="detection-methods-dont-load-windows-powershell-profiles"></a>검색 방법은 Windows PowerShell 프로필을 로드하지 않습니다.
<!--1359239--> 애플리케이션의 검색 방법에 대한 Windows PowerShell 스크립트 및 구성 항목의 설정을 사용할 수 있습니다. 이러한 스크립트가 클라이언트에서 실행되는 경우 Configuration Manager는 이제 `-NoProfile` 매개 변수를 사용하여 PowerShell을 호출합니다. 이 옵션은 프로필 없이 PowerShell을 시작합니다. 

PowerShell 프로필은 PowerShell이 시작될 때 실행되는 스크립트입니다. PowerShell 프로필을 만들어 환경을 사용자 지정하고 시작하는 모든 PowerShell 세션에 세션별 요소를 추가할 수 있습니다. 

> [!Note]  
> 동작의 이 변경 내용은 [스크립트](/sccm/apps/deploy-use/create-deploy-scripts) 또는 [CMPivot](/sccm/core/servers/manage/cmpivot)에 적용되지 않습니다. 이러한 기능은 모두 이미 이 PowerShell 매개 변수를 사용합니다.    

<!--For more information, see []().-->


## <a name="bkmk_osd"></a> OS 배포

### <a name="task-sequence-support-of-windows-autopilot-for-existing-devices"></a>기존 디바이스에 대한 Windows Autopilot의 작업 순서 지원
<!--1358333-->

[기존 장치에 대한 Windows Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)은 이제 Windows 10 Insider Preview와 함께 제공됩니다. 이 새로운 기능을 사용하면 단일, 네이티브 Configuration Manager 작업 순서를 사용하여 [Windows Autopilot 사용자 기반 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)용으로 Windows 7 디바이스를 이미지로 다시 설치하고 프로비전할 수 있습니다. 

<!--For more information, see []().--> 


### <a name="specify-the-drive-for-offline-os-image-servicing"></a>오프라인 OS 이미지 서비스용 드라이브 지정  
<!--1358924--> 이제 OS 이미지 및 OS 업그레이드 패키지에 소프트웨어 업데이트를 추가할 때 Configuration Manager에서 사용하는 드라이브를 지정합니다. 이 프로세스에서는 임시 파일이 있는 큰 디스크 공간을 사용할 수 있으므로 이 옵션을 통해 사용할 드라이브를 유연하게 선택할 수 있습니다. 

자세한 내용은 [OS 이미지 관리](/sccm/osd/get-started/manage-operating-system-images#bkmk_servicing-drive) 또는 [OS 업그레이드 패키지 관리](/sccm/osd/get-started/manage-operating-system-upgrade-packages#bkmk_servicing-drive)를 참조하세요.


### <a name="task-sequence-support-for-boundary-groups"></a>경계 그룹의 작업 순서 지원
<!--1359025--> 디바이스가 작업 순서를 실행하고 콘텐츠를 확보해야 하는 경우, 이제 Configuration Manager 클라이언트와 유사한 경계 그룹 동작을 사용합니다.   

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups#bkmk_bgr-osd)을 참조하세요.


### <a name="improvements-to-driver-maintenance"></a>드라이버 유지 관리 기능 개선
<!--1358270--> 이제 드라이버 패키지에는 **제조업체** 및 **모델**에 대한 추가 메타데이터 필드가 포함됩니다. 이러한 필드를 사용하여 일반적인 하우스키핑을 지원하거나 삭제할 수 있는 이전 및 중복 드라이버를 식별하기 위한 정보로 드라이버 패키지에 태그를 지정합니다.


### <a name="new-task-sequence-variable-for-last-action-name"></a>마지막 작업 이름에 대한 새 작업 순서 변수
<!--SCCMDocs-pr issue #2964--> 작업 순서 변수 _SMSTSLastActionRetCode와 함께 작업 순서는 새 변수 **_SMSTSLastActionName**도 설정합니다. 또한 smsts.log 파일에 이 값을 기록합니다. 이 새 변수는 작업 순서 문제를 해결할 때 유용합니다. 단계가 실패한 경우 사용자 지정 스크립트는 반환 코드와 함께 단계 이름을 포함할 수 있습니다.

자세한 내용은 [Task sequence variables](/sccm/osd/understand/task-sequence-variables#SMSTSLastActionName)\(작업 순서 변수\)를 참조하세요.



<!-- ## <a name="bkmk_userxp"></a> Software Center -->



## <a name="bkmk_sum"></a> 소프트웨어 업데이트

### <a name="phased-deployment-of-software-updates"></a>단계별 소프트웨어 업데이트 배포
<!--1358146--> 소프트웨어 업데이트에 대한 단계적 배포를 만듭니다. 단계적 배포에서는 사용자 지정 가능한 조건 및 그룹에 따라 소프트웨어 출시를 조정하고 순차적으로 진행할 수 있습니다.

자세한 내용은 [단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/sccm/sum/toc.json&bc=/sccm/sum/breadcrumb/toc.json)를 참조하세요.


### <a name="improvement-to-maintenance-windows-for-software-updates"></a>향상된 소프트웨어 업데이트에 대한 유지 관리 기간 기능
<!--vso2839307--> 다음 클라이언트 설정은 유지 관리 기간에서 소프트웨어 업데이트의 설치 동작을 제어하는 **소프트웨어 업데이트** 그룹에 있습니다. 

**"소프트웨어 업데이트" 유지 관리 기간을 사용할 수 있는 경우 "모든 배포" 유지 관리 기간에서 업데이트 설치 사용**

기본적으로 이 옵션은 기존 동작과 일관성을 유지하기 위해 **아니요**입니다. 클라이언트에서 다른 사용 가능한 유지 관리 기간을 사용하여 소프트웨어 업데이트를 설치할 수 있도록 하려면 **예**로 변경합니다.

<!--For more information, see []().-->



## <a name="bkmk_report"></a> 보고

### <a name="improvement-to-lifecycle-dashboard"></a>향상된 수명 주기 대시보드 기능
<!--1358702--> 제품 수명 주기 대시보드에는 이제 **System Center 2012 Configuration Manager 이상**에 대한 정보가 포함되어 있습니다. 

또한 새 보고서, **수명 주기 05A - 제품 수명 주기 대시보드**도 있습니다. 콘솔 내 대시보드와 유사한 정보를 포함합니다.

이 대시보드에 대한 자세한 내용은 [제품 수명 주기 대시보드 사용](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard)을 참조하세요.


### <a name="improvement-to-data-warehouse"></a>향상된 데이터 웨어하우스 기능
<!--1358870--> 이제 더 많은 테이블을 사이트 데이터베이스에서 데이터 웨어하우스로 동기화할 수 있습니다. 이렇게 변경하면 비즈니스 요구 사항에 따라 더 많은 보고서를 만들 수 있습니다.

자세한 내용은 [데이터 웨어하우스](/sccm/core/servers/manage/data-warehouse)를 참조하세요.



<!-- ## <a name="bkmk_inv"></a> Inventory -->




<!-- ## <a name="bkmk_protect"></a> Protect devices-->




## <a name="bkmk_admin"></a> Configuration Manager 콘솔

### <a name="configuration-manager-administrator-authentication"></a>Configuration Manager 관리자 인증
<!--1357013--> 이제 관리자가 Configuration Manager 사이트에 액세스하는 데 필요한 최소 인증 수준을 지정할 수 있습니다. 이 기능은 관리자에게 필요한 수준으로 Windows에 로그인하도록 요구합니다. 이 설정을 구성하려면 **계층 구조 설정**에서 **인증** 탭을 찾습니다. 

자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_auth)을 참조하세요.


### <a name="support-center"></a>지원 센터
<!--1357489--> 클라이언트 문제 해결, 실시간 로그 보기, 나중에 분석하기 위해 Configuration Manager 클라이언트 컴퓨터의 상태 캡처 등의 작업에 지원 센터를 사용합니다. 지원 센터는 많은 관리자 문제 해결 도구를 결합하는 단일 도구입니다. 사이트 서버의 **cd.latest\SMSSETUP\Tools\SupportCenter** 폴더에서 지원 센터 설치 관리자를 찾습니다.

자세한 내용은 [지원 센터](/sccm/core/support/support-center)를 참조하세요.


### <a name="management-insights-dashboard"></a>관리 인사이트 대시보드
<!--1357979-->

이제 **관리 인사이트** 노드에 그래픽 대시보드가 포함됩니다. 이 대시보드는 규칙 상태의 개요를 표시하므로 진행 상태를 보다 쉽게 표시할 수 있습니다. 이 대시보드에는 다음과 같은 타일이 있습니다.

- **관리 인사이트 인덱스**: 관리 인사이트 규칙에 대한 전체 진행 상황을 추적합니다. 인덱스는 가중 평균입니다. 중요 규칙이 가장 유용합니다. 이 인덱스는 선택적 규칙에 가장 작은 가중치를 부여합니다.  

- **관리 인사이트 그룹**: 각 그룹에 있는 규칙의 백분율을 표시합니다.  

- **관리 인사이트 우선 순위**: 우선 순위별 규칙의 백분율을 표시합니다.  

- **모든 인사이트**: 우선 순위 및 상태를 포함하는 인사이트 테이블입니다.  

![관리 인사이트 대시보드 스크린샷](media/1357979-management-insights-dashboard.png)

자세한 내용은 [관리 인사이트](/sccm/core/servers/manage/management-insights)를 참조하세요.


### <a name="improvements-to-cmpivot"></a>향상된 CMPivot 기능
<!--1359068--> CMPivot에서는 다음 사항이 개선되었습니다.

- **즐겨찾기** 쿼리 저장  

- 쿼리 요약 탭에서 실패 또는 오프라인 디바이스 수를 선택한 다음, **컬렉션 만들기** 옵션을 선택합니다. 

CMPivot의 추가 성능 및 문제 해결 기능 개선에 대한 자세한 내용은 [스크립트 기능 개선](#bkmk_scripts)을 참조하세요.

<!--For more information on CMPivot, see [CMPivot](/sccm/core/servers/manage/cmpivot).-->


### <a name="bkmk_scripts"></a> 스크립트 기능 개선
<!--1358239--> 이제 원시 또는 구조적 JSON 형식으로 세부 스크립트 출력을 볼 수 있습니다. 이 형식을 사용하면 출력을 더 쉽게 읽고 분석할 수 있습니다. 

다음 성능 및 문제 해결 개선 사항은 CMPivot 및 스크립트 둘 다에 적용됩니다.

- 업데이트된 클라이언트는 고속 통신 채널을 통해 사이트로 80KB 미만의 출력을 반환합니다. 이러한 변경으로 인해 스크립트 또는 쿼리 출력 표시 성능이 개선됩니다.  

- 문제 해결을 위한 추가 로그  

<!--For more information, see the following articles:  

- [Create and run PowerShell scripts from the Configuration Manager console](/sccm/apps/deploy-use/create-deploy-scripts)  

- [CMPivot](/sccm/core/servers/manage/cmpivot)  -->


### <a name="sms-provider-api"></a>SMS 공급자 API
<!--1321523--> SMS 공급자는 이제 WMI에 대한 읽기 전용 API 상호 운용성 액세스(HTTPS 이용)를 제공합니다. **SMS 공급자**는 클라우드 관리 게이트웨이 통해 통신할 수 있도록 옵션을 사용하여 역할로 표시됩니다. 이 설정에 대한 현재 사용은 원격 디바이스의 이메일을 통해 애플리케이션 승인을 활성화하는 것입니다. 자세한 내용은 [이메일을 통해 애플리케이션 요청 승인](#approve-application-requests-via-email)을 참조하세요.



## <a name="bkmk_opmdm"></a> 온-프레미스 MDM

### <a name="an-intune-connection-is-no-longer-required-for-on-premises-mdm"></a>Intune 연결이 온-프레미스 MDM에 필요하지 않음
<!--1359124--> Microsoft Intune 구독을 구성하기 위해 온-프레미스 MDM 필수 구성 요소는 더 이상 필요하지 않습니다. 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 



## <a name="next-steps"></a>다음 단계

이 버전을 설치할 준비가 되었으면 [Configuration Manager에 대한 업데이트 설치](/sccm/core/servers/manage/updates) 및 [업데이트 1810을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1810)을 참조하세요.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용합니다.  
>
>  다음에 대해 자세히 알아보세요.    
>   - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
>   - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

알려진 중요한 문제는 [릴리스 정보](/sccm/core/servers/deploy/install/release-notes)를 참조하세요.

사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1810#post-update-checklist)도 검토하세요.