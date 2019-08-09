---
title: 릴리스 정보
titleSuffix: Configuration Manager
description: Microsoft 지원 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해 알아봅니다.
ms.date: 07/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 858ba3b39ea2290e1d5ca39d9d804e3f46be3002
ms.sourcegitcommit: ef7800a294e5db5d751921c34f60296c1642fc1f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712721"
---
# <a name="release-notes-for-configuration-manager"></a>Configuration Manager의 릴리스 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서는 제품 릴리스 정보가 긴급한 문제로 제한됩니다. 이러한 문제는 제품에서 아직 해결되지 않았거나 Microsoft 지원 기술 자료 문서에서 자세히 설명되지 않은 문제입니다.  

기능별 문서에는 핵심 시나리오에 영향을 주는 알려진 문제에 대한 정보가 포함됩니다.  

이 문서에는 Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. 기술 미리 보기 분기에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.  

다른 버전에서 도입된 새 기능에 대한 자세한 내용은 다음 문서를 참조하세요.

- [버전 1906의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1906)  
- [버전 1902의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1902)
- [버전 1810의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1810)
- [버전 1806의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1806)  

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22release+notes+-+Configuration+Manager%22&locale=en-us`


## <a name="set-up-and-upgrade"></a>설치 및 업그레이드  

### <a name="setup-prerequisite-warning-on-domain-functional-level-on-server-2019"></a>Server 2019에서 도메인 기능 수준에 대한 필수 구성 요소 경고 설정

<!-- 4904376 -->

*버전 1906에 적용*

Windows Server 2019를 실행하는 도메인 컨트롤러가 있는 환경에서 버전 1906에 대한 업데이트를 설치하는 경우 도메인 기능 수준에 대한 필수 구성 요소 검사는 다음 경고를 반환합니다.

`[Completed with warning]:Verify that the Active Directory domain functional level is Windows Server 2003 or later`

#### <a name="workaround"></a>해결 방법

경고를 무시합니다.

### <a name="azure-ad-user-discovery-and-collection-group-sync-dont-work-after-site-expansion"></a>사이트 확장 후 Azure AD 사용자 검색 및 컬렉션 그룹 동기화가 작동하지 않음

<!-- 4797313 -->
*버전 1906에 적용*

다음 기능 중 하나를 구성합니다.

- Azure Active Directory 사용자 그룹 검색
- Azure Active Directory 그룹에 컬렉션 멤버 자격 결과 동기화

그런 다음 독립 실행형 기본 사이트를 중앙 관리 사이트가 있는 계층 구조로 확장하면 SMS_AZUREAD_DISCOVERY_AGENT.log에 다음과 같은 오류가 표시됩니다.

`Could not obtain application secret for tenant xxxxx. If this is after a site expansion, please run "Renew Secret Key" from admin console.`

#### <a name="workaround"></a>해결 방법

Azure AD에서 앱 등록에 연결된 키를 갱신합니다. 자세한 내용은 [비밀 키 갱신](/sccm/core/servers/deploy/configure/azure-services-wizard#bkmk_renew)을 참조하세요.


### <a name="setup-command-line-option-joinceip-must-be-specified"></a>설치 명령줄 옵션 JoinCEIP를 지정해야 함

<!--510806-->
*적용 대상: Configuration Manager 버전 1802*

Configuration Manager 버전 1802부터 CEIP(사용자 환경 개선 프로그램) 기능은 제품에서 제거됩니다. 명령줄 또는 무인 스크립트에서 새 사이트의 [설치를 자동화하는](/sccm/core/servers/deploy/install/command-line-options-for-setup) 경우 설치 프로그램은 필요한 매개 변수가 누락되었다는 오류를 반환합니다.

#### <a name="workaround"></a>해결 방법

설치 프로세스의 결과에 영향을 주지 않지만 설치 명령줄에 **JoinCEIP** 매개 변수를 포함합니다.

> [!Note]  
> [콘솔 설치 프로그램](/sccm/core/servers/deploy/install/install-consoles)에 대한 EnableSQM 매개 변수가 필요하지 않습니다.

### <a name="cloud-service-manager-component-stopped-on-site-server-in-passive-mode"></a>클라우드 서비스 관리자 구성 요소가 수동 모드의 사이트 서버에서 정지

<!--VSO 2858826, SCCMDocs issue 772-->
*적용 대상: Configuration Manager 버전 1806*

[서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)이 [수동 모드의 사이트 서버](/sccm/core/servers/deploy/configure/site-server-high-availability)에 배치되면 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)의 배포 및 모니터링이 시작되지 않습니다. 클라우드 서비스 관리자 구성 요소(SMS_CLOUD_SERVICES_MANAGER)가 중지 상태에 있습니다.

#### <a name="workaround"></a>해결 방법

서비스 연결점 역할을 다른 서버로 이동합니다.


<!-- ## Backup and recovery  -->

<!--## Client deployment and upgrade-->


## <a name="os-deployment"></a>OS 배포

### <a name="after-passive-site-server-is-promoted-the-default-boot-image-packages-still-have-package-source-on-the-previous-active-server"></a>수동 사이트 서버가 승격된 후에도 기본 부팅 이미지 패키지에는 이전 활성 서버의 패키지 소스가 여전히 있습니다.

<!--3453224, SCCMDocs-pr issue 3097-->
*적용 대상: Configuration Manager 버전 1810*

수동 모드(서버 B)의 사이트 서버가 있는 경우, 사이트 서버를 활성으로 승격할 때 기본 부팅 이미지의 콘텐츠 위치는 이전의 활성 서버(서버 A)를 계속 참조합니다. 서버 A에 하드웨어 오류가 있으면 기본 부팅 이미지를 업데이트하거나 변경할 수 없습니다.

#### <a name="workaround"></a>해결 방법

없음


## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="security-roles-are-missing-for-phased-deployments"></a>단계적 배포에 대한 보안 역할이 누락됨

<!--3479337, SCCMDocs-pr issue 3095-->
*적용 대상: Configuration Manager 버전 1810, 1902*

**OS 배포 관리자** 기본 제공 보안 역할에는 [단계적 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)에 대한 권한이 있습니다. 이러한 권한이 없는 역할은 다음과 같습니다.  

- **애플리케이션 관리자**  
- **애플리케이션 배포 관리자**  
- **소프트웨어 업데이트 관리자**  

**앱 작성자** 역할은 단계적 배포에 대한 일부 권한이 있는 것처럼 보일 수 있지만 배포를 만들 수 없습니다.

이러한 역할이 있는 사용자는 단계적 배포 만들기 마법사를 시작할 수 있으며, 애플리케이션 또는 소프트웨어 업데이트에 대한 단계적 배포를 확인할 수 있습니다. 그러나 마법사를 완료하거나 기존 배포를 변경할 수 없습니다.

#### <a name="workaround"></a>해결 방법

사용자 지정 보안 역할을 만듭니다. 기존 보안 역할을 복사하고, **단계적 배포** 개체 클래스에 다음 권한을 추가합니다.

- 만들기  
- 삭제  
- 수정  
- 읽기  

자세한 내용은 [사용자 지정 보안 역할 만들기](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_CreateSecRole)를 참조하세요.

### <a name="changing-office-365-client-setting-doesnt-apply"></a>Office 365 클라이언트 설정 변경이 적용되지 않음

<!--511551-->
*적용 대상: Configuration Manager 버전 1802*  

**Office 365 클라이언트 에이전트 관리 사용**이 `Yes`로 구성된 [클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#enable-management-of-the-office-365-client-agent)을 배포합니다. 그런 다음, 설정을 `No` 또는 `Not Configured`로 변경합니다. 대상 클라이언트에서 정책을 업데이트하면 Office 365 업데이트가 Configuration Manager에서 계속 관리됩니다.

#### <a name="workaround"></a>해결 방법

다음 레지스트리 값을 `0`으로 변경하고 **Microsoft Office 간편 실행 서비스**(ClickToRunSvc)를 다시 시작합니다.

```Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\office\16.0\Common\officeupdate]
"OfficeMgmtCOM"=dword:00000000
```

## <a name="desktop-analytics"></a>Desktop Analytics

### <a name="if-you-use-hardware-inventory-for-distributed-views-you-cant-onboard-to-desktop-analytics"></a>분산 보기에 하드웨어 인벤토리를 사용하는 경우 Desktop Analytics에 등록할 수 없습니다.

<!-- 4950335 -->
*적용 대상: Configuration Manager 버전 1902(업데이트 롤업 포함) 및 버전 1906*

계층 구조가 있고 사이트 복제 링크에서 [분산 보기](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_distviews)에 **하드웨어 인벤토리** 사이트 데이터를 사용하도록 설정한 경우 Configuration Manager에서 Desktop Analytics 연결을 구성한 후 M365UploadWorker.log에 다음과 같은 오류가 표시됩니다.

`Unexpected exception 'System.Data.SqlClient.SqlException' Remote access is not supported for transaction isolation level "SNAPSHOT".:    at System.Data.SqlClient.SqlConnection.OnError(SqlException exception, Boolean breakConnection, Action'1 wrapCloseInAction)`

#### <a name="workaround"></a>해결 방법

모든 사이트 복제 링크에서 분산 보기에 **하드웨어 인벤토리** 사이트 데이터를 사용하지 않습니다.


### <a name="console-unexpectedly-closes-when-removing-collections"></a>컬렉션을 제거할 때 콘솔이 예기치 않게 닫힘

<!-- 4749443 -->
*적용 대상: Configuration Manager 버전 1902, 업데이트 롤업’*

사이트를 [Desktop Analytics](/sccm/desktop-analytics/connect-configmgr)에 연결한 후 **Desktop Analytics와 동기화할 특정 컬렉션을 선택**할 수 있습니다. 컬렉션을 제거하고 변경 내용을 적용하는 경우 새 컬렉션을 즉시 추가하면 처리되지 않은 예외가 발생합니다. 콘솔이 예기치 않게 닫힙니다.

#### <a name="workaround"></a>해결 방법

컬렉션을 제거하면 **확인**을 선택하여 속성 창을 닫습니다. 그런 다음 속성을 다시 열어 **Desktop Analytics 연결** 탭에서 새 컬렉션을 추가합니다.

### <a name="pilot-status-tile-shows-some-devices-as-undefined"></a>파일럿 상태 타일에서 일부 디바이스를 ‘정의되지 않음’으로 표시함

<!-- 4547783 -->
*적용 대상: Configuration Manager 버전 1902, 업데이트 롤업’*

Configuration Manager 콘솔을 사용하여 파일럿 배포 상태를 모니터링하는 경우 해당 배포 플랜의 Windows 대상 버전에서 최신 상태인 파일럿 디바이스는 파일럿 상태 타일에 **정의되지 않음**으로 표시됩니다.  

이러한 **정의되지 않음** 디바이스는 해당 배포 계획의 OS 대상 버전에서 **최신 상태**입니다. 추가 작업은 필요하지 않습니다.


## <a name="mobile-device-management"></a>모바일 디바이스 관리  

### <a name="validation-for-ios-app-link-sometimes-fails-on-valid-link"></a>iOS 앱 연결에 대한 유효성 검사가 유효한 링크에서 실패하는 경우가 있음

*적용 대상: Configuration Manager 1810 및 이전 버전*

<!-- LSI 106004348 -->
**App Store에서 iOS용 앱 패키지** 유형의 새 애플리케이션을 만드는 경우 유효성 검사기는 **위치**에 대한 일부 유효한 URL을 수락하지 않습니다. 특히 iOS App Store에는 URL의 앱 이름 섹션에 값이 필요하지 않습니다. 예를 들어 다음 링크는 모두 유효하며 동일한 앱을 가리킵니다. 그러나 **애플리케이션 생성 마법사**는 첫 번째 항목만 수락합니다.

- `https://itunes.apple.com/us/app/app-name/id123456789?mt=8`
- `https://itunes.apple.com/us/app//id123456789?mt=8`

#### <a name="workaround"></a>해결 방법

URL에서 앱 이름이 누락된 iOS 앱을 만들 때 URL에 앱 이름인 것처럼 값을 추가하세요. 예:

- `https://itunes.apple.com/us/app/any-string/id123456789?mt=8`

이 작업을 수행하여 마법사를 완료할 수 있습니다. 앱이 계속해서 iOS 디바이스에 성공적으로 배포됩니다. URL에 추가하는 문자열은 마법사의 **일반 정보** 탭에 있는 **이름**으로 나타납니다. 회사 포털에서 앱의 레이블이기도 합니다.




<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->

<!-- ## Endpoint Protection -->
