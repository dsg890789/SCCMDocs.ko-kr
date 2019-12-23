---
title: 버전 1910의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager 현재 분기의 버전 1906에 도입된 변경 내용 및 새로운 기능에 대해 자세히 설명합니다.
ms.date: 12/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3e1ddb65-1193-46ce-a7c0-a48dfd9fd833
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 545b68cd1628bb9652f1e87da96e5fb6e18787f1
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198492"
---
# <a name="whats-new-in-version-1910-of-configuration-manager-current-branch"></a>Configuration Manager 현재 분기 버전 1910의 새로운 기능

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 현재 분기의 1910 업데이트는 콘솔 내 업데이트로 사용할 수 있습니다. 버전 1806 이상을 실행하는 사이트에서 이 업데이트를 적용합니다. <!-- baseline only statement:When installing a new site, it's also available as a baseline version.--> 이 문서에는 Configuration Manager 버전 1910의 변경 내용과 새로운 기능이 요약되어 있습니다.  

이 업데이트를 설치하기 위한 최신 검사 목록을 항상 검토하세요. 자세한 내용은 [업데이트 1910을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1910)을 참조하세요. 사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1910#post-update-checklist)도 검토하세요.

새 Configuration Manager 기능을 모두 활용하려면 사용자를 업데이트한 후 클라이언트를 최신 버전으로 업데이트합니다. 사이트 및 콘솔을 업데이트할 때 Configuration Manager 콘솔에 새 기능이 표시되지만 클라이언트 버전도 최신 버전이 될 때까지 전체 시나리오가 작동하지 않습니다.

> [!Tip]  
> 이 페이지가 업데이트될 때 알림을 받으려면 다음 URL을 복사하여 RSS 피드 판독기에 붙여넣으세요. `https://docs.microsoft.com/api/search/rss?search=%22what%27s+new+in+version+1910+-+Configuration+Manager%22&locale=en-us`

## <a name="bkmk_mem"></a> Microsoft Endpoint Configuration Manager

<!--4960084-->

Configuration Manager는 이제 Microsoft Endpoint Manager의 일부입니다.

![Microsoft Endpoint Configuration Manager](media/4960084-endpoint-manager-logo.png)

Microsoft Endpoint Manager는 모든 디바이스를 관리하기 위한 통합 솔루션입니다. Microsoft는 간소화된 라이선싱을 통해 Configuration Manager와 Intune을 함께 제공합니다. 원하는 대로 Microsoft 클라우드의 강력한 기능을 활용하면서 기존 Configuration Manager 투자를 계속 활용하세요.

다음 Microsoft 관리 솔루션은 이제 모두 **Microsoft Endpoint Manager** 브랜드의 일부입니다.

- [Configuration Manager](https://docs.microsoft.com/configmgr)
- [Intune](https://docs.microsoft.com/intune)
- [Desktop Analytics](/configmgr/desktop-analytics/overview)
- [Autopilot](https://docs.microsoft.com/intune/enrollment/enrollment-autopilot)
- [Device Management 관리자 콘솔](https://go.microsoft.com/fwlink/?linkid=2109094)의 기타 기능

자세한 내용은 Microsoft 365의 Microsoft 기업 부사장인 Brad Anderson의 다음 게시물을 참조하세요.

- [공지 블로그 게시물](https://aka.ms/cmannounce)
- [비전 용지](https://aka.ms/MEMVisionPaper)
- [공지 요약 비디오](https://youtu.be/GS7oNPInFuw)

### <a name="what-things-change-in-configuration-manager-with-microsoft-endpoint-manager"></a>Configuration Manager가 Microsoft Endpoint Manager의 일부가 되면서 무엇이 달라졌나요?

버전 1910에서는 이름 변경을 제외하고는 Configuration Manager의 기능이 전과 동일합니다. 이름 변경으로 인해 다음과 같은 구성 요소를 사용하는 데 영향이 있을 수 있습니다.

- **Configuration Manager 콘솔**: Windows 시작 메뉴의 **Microsoft Endpoint Manager** 폴더에서 콘솔 및 **원격 제어 뷰어**의 바로 가기를 찾을 수 있습니다.

- **소프트웨어 센터**: Windows 시작 메뉴의 **Microsoft Endpoint Manager** 폴더에서 소프트웨어 센터 바로 가기를 찾을 수 있습니다.

![Microsoft Endpoint Manager 시작 메뉴 아이콘](media/microsoft-endpoint-manager-start-menu.png)

내부 문서를 이 새 위치로 업데이트하시기 바랍니다.

> [!TIP]
> Windows 10에서는 시작 메뉴를 열고 이름을 입력하면 아이콘을 찾을 수 있습니다. 예를 들어, Configuration Manager 콘솔을 찾으려면 `config`를 입력하고 소프트웨어 센터를 찾으려면 `software`를 입력합니다.

## <a name="bkmk_infra"></a> 사이트 인프라

### <a name="reclaim-sedo-lock"></a>SEDO 잠금 회수

<!--4786915-->

[현재 분기 버전 1906](/configmgr/core/plan-design/changes/whats-new-in-version-1906#reclaim-sedo-lock-for-task-sequences)부터 작업 순서 잠금을 해제할 수 있습니다. 이제 Configuration Manager 콘솔에서 모든 개체에 대한 잠금을 해제할 수 있습니다.

자세한 내용은 [Configuration Manager 콘솔 사용](/configmgr/core/servers/manage/admin-console#bkmk_sedo)을 참조하세요.

### <a name="extend-and-migrate-on-premises-site-to-microsoft-azure"></a>온-프레미스 사이트를 Microsoft Azure로 확장 및 마이그레이션
<!--3556022-->

이 새로운 도구를 사용하여 Configuration Manager를 위한 Azure VM(가상 머신)을 프로그래밍 방식으로 만들 수 있습니다. 수동 사이트 서버, 관리 지점 및 배포 지점과 같은 기본 설정 사이트 역할을 사용하여 설치할 수 있습니다. 새 역할의 유효성을 검사한 후에는 고가용성을 위해 추가 사이트 시스템으로 사용합니다. 또한 온-프레미스 사이트 시스템 역할을 제거하고 Azure VM 역할만 유지할 수 있습니다.

자세한 내용은 [온-프레미스 사이트를 Microsoft Azure로 확장 및 마이그레이션](/sccm/core/support/azure-migration-tool)을 참조하세요.

<!-- ## <a name="bkmk_cloud"></a> Cloud-attached management -->

## <a name="bkmk_da"></a> Desktop Analytics

Desktop Analytics 클라우드 서비스의 월별 변경 사항에 대한 자세한 내용은 [Desktop Analytics의 새로운 기능](/configmgr/desktop-analytics/whats-new)을 참조하세요.

## <a name="bkmk_real"></a> 실시간 관리

### <a name="optimizations-to-the-cmpivot-engine"></a>CMPivot 엔진에 대한 최적화
<!--3197353-->
ConfigMgr 클라이언트에 더 많은 처리를 푸시할 수 있는 몇 가지 중요한 최적화를 CMPivot 엔진에 추가했습니다. 최적화는 CMPivot 쿼리를 실행하는 데 필요한 네트워크 및 서버 CPU 로드를 크게 줄입니다. 이러한 최적화를 통해 이제 클라이언트 데이터(기가바이트)를 실시간으로 자세히 살펴볼 수 있습니다. 자세한 내용은 [CMPivot 엔진에 대한 최적화](/sccm/core/servers/manage/cmpivot#bkmk_optimization)를 참조하세요.

### <a name="additional-cmpivot-entities-and-enhancements"></a>추가 CMPivot 엔터티 및 향상된 기능
<!--5410930-->
문제 해결 및 헌팅을 지원하기 위해 여러 가지 새로운 CMPivot 엔터티 및 엔터티에 대한 향상된 기능이 추가되었습니다. 쿼리에 다음과 같은 엔터티가 포함되었습니다.

- Windows 이벤트 로그([WinEvent](/sccm/core/servers/manage/cmpivot#bkmk_WinEvent))
- 파일 콘텐츠([FileContent](/sccm/core/servers/manage/cmpivot#bkmk_File))
- 프로세스에 의해 로드된 dll([ProcessModule](/sccm/core/servers/manage/cmpivot#bkmk_ProcessModule))
- Azure Active Directory 정보([AADStatus](/sccm/core/servers/manage/cmpivot#bkmk_AadStatus))
- Endpoint Protection 상태([EPStatus](/sccm/core/servers/manage/cmpivot#bkmk_EPStatus))

또한 이 릴리스에는 몇 가지 CMPivot에 대한 [다른 향상된 기능](/sccm/core/servers/manage/cmpivot#bkmk_Other)이 포함되어 있습니다. 자세한 내용은 [1910 버전부터 CMPivot](/sccm/core/servers/manage/cmpivot#bkmk_cmpivot1910)을 참조하세요.

## <a name="bkmk_content"></a> 콘텐츠 관리

### <a name="microsoft-connected-cache-support-for-intune-win32-apps"></a>Intune Win32 앱에 대한 Microsoft Connected Cache 지원

<!--5032900-->

Configuration Manager 배포 지점에서 Microsoft Connected Cache를 사용하도록 설정하면 이제 공동 관리 클라이언트에 Microsoft Intune Win32 앱을 제공할 수 있습니다.

자세한 내용은 [Configuration Manager의 Microsoft Connected Cache](/configmgr/core/plan-design/hierarchy/microsoft-connected-cache#bkmk_intune)를 참조하세요.

> [!NOTE]
> Configuration Manager 현재 분기 지점 1906에는 Windows Server에 설치된 애플리케이션으로 아직 개발 단계에 있는 DOINC([전송 최적화 네트워크 내 캐시](/configmgr/core/plan-design/hierarchy/microsoft-connected-cache))가 포함되어 있습니다. 현재 분기 버전 1910부터, 이 기능을 **Microsoft Connected Cache**라고 합니다.
>
> Configuration Manager 배포 지점에 Connected Cache를 설치하면 제공 최적화 서비스 트래픽이 로컬 원본으로 오프로드됩니다. Connected Cache는 바이트 범위 수준에서 콘텐츠를 효율적으로 캐싱하여 이 동작을 수행합니다.

## <a name="bkmk_client"></a> 클라이언트 관리

### <a name="include-custom-configuration-baselines-as-part-of-compliance-policy-assessment"></a>준수 정책 평가의 일환으로 사용자 지정 구성 기준 포함
<!--3608345-->

이제 사용자 지정 구성 기준의 평가를 준수 정책 평가 규칙으로 추가할 수 있습니다. 구성 기준을 만들거나 편집하는 경우 **준수 정책 평가의 일부로 이 기준을 평가**할 수 있는 옵션을 사용할 수 있습니다. 준수 정책 규칙을 추가하거나 편집하는 경우 **준수 정책 평가에 구성된 기준 포함**이라는 조건을 사용할 수 있습니다.

공동 관리 디바이스의 경우 그리고 Configuration Manager 준수 평가 결과를 전체 규정 준수 상태의 일부로 취하도록 Intune을 구성하는 경우 이 정보가 Azure Active Directory로 전송됩니다. 이 정보를 Office 365 리소스에 대한 조건부 액세스에 사용할 수 있습니다.  

자세한 내용은 [준수 정책 평가의 일환으로 사용자 지정 구성 기준 포함](/sccm/compliance/deploy-use/create-configuration-baselines#bkmk_CAbaselines)을 참조하세요.

### <a name="enable-user-policy-for-windows-10-enterprise-multi-session"></a>Windows 10 Enterprise 다중 세션에서 사용자 정책 사용

<!--4737447-->

Configuration Manager 현재 분기 버전 1906에 [Windows Virtual Desktop](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#windows-virtual-desktop)의 지원이 도입되었습니다. 이 Microsoft Azure 환경은 여러 OS 버전을 지원하며, 그중에는 다중 동시 활성 사용자 세션을 허용하는 것도 있습니다. 그 예로 Windows 10 Enterprise 다중 세션을 들 수 있습니다.

다중 세션 디바이스에서 사용자 정책이 필요하고 잠재적인 성능 영향이 허용되는 경우 이제 사용자 정책을 사용하도록 클라이언트 설정을 구성할 수 있습니다. **클라이언트 정책** 그룹에서 다음 설정을 구성합니다. **다중 사용자 세션에 대한 사용자 정책 사용**.

자세한 내용은 [클라이언트 설정을 구성하는 방법](/configmgr/core/clients/deploy/configure-client-settings)을 참조하세요.


<!-- ## <a name="bkmk_comgmt"></a> Co-management -->


## <a name="bkmk_app"></a> 애플리케이션 관리

### <a name="deploy-microsoft-edge-version-77-and-later"></a>Microsoft Edge, 버전 77 이상 배포
<!--4561024-->
모든 새로운 Microsoft Edge는 비즈니스용으로 준비됩니다. 이제 Microsoft Edge 버전 77 이상을 사용자에게 배포할 수 있습니다. 관리자는 배포할 Microsoft Edge 클라이언트 버전과 함께 베타 또는 개발 채널을 선택할 수 있습니다.

자세한 내용은 [Microsoft Edge 버전 77 이상 배포](/sccm/apps/deploy-use/deploy-edge)를 참조하세요.

### <a name="improvements-to-application-groups"></a>애플리케이션 그룹 개선 사항

<!--4760058-->

현재 분기 버전 1906부터 디바이스 컬렉션을 단일 배포로 보낼 수 있는 애플리케이션 그룹을 만들 수 있습니다. 이 릴리스에서는 다음 기능이 개선되었습니다.

- 사용자는 소프트웨어 센터에서 앱 그룹을 **제거**할 수 있습니다.

- **사용자 컬렉션**에 앱 그룹을 배포할 수 있습니다.

자세한 내용은 [애플리케이션 그룹 만들기](/configmgr/apps/deploy-use/create-app-groups)를 참조하세요.


## <a name="bkmk_osd"></a> OS 배포

### <a name="improvements-to-the-task-sequence-editor"></a>작업 순서 편집기의 향상된 기능:

- **작업 순서 편집기 검색**<!--4621085-->: 그룹과 단계가 많은 대규모 작업 순서가 있는 경우 특정 단계를 찾기가 어려울 수 있습니다. 이제 작업 순서 편집기에서 검색할 수 있습니다. 이 작업을 통해 작업 순서에서 단계를 더 빨리 찾을 수 있습니다.

- **복사 및 붙여넣기 작업 순서 조건**<!--4621098-->: 한 작업 순서 단계의 조건을 다른 작업 순서 단계에서 다시 사용하려는 경우 이제 작업 순서 편집기에서 조건을 복사하여 붙여넣을 수 있습니다.

자세한 내용은 [작업 순서 편집기 사용](/configmgr/osd/understand/task-sequence-editor)에 관한 새로운 문서를 참조하세요.

### <a name="task-sequence-performance-improvements---power-plans"></a>작업 순서 성능 향상 - 전원 계획

<!--3555926-->

이제 고성능 전원 계획을 사용하여 작업 순서를 실행할 수 있습니다. 이 옵션은 작업 순서의 전체 속도를 향상시킵니다. 이 옵션은 기본 제공 고성능 전원 계획을 사용하도록 Windows를 구성하여 더 높은 전력을 소비하면서 최대 성능을 제공합니다.

자세한 내용은 [전원 계획의 성능 향상](/configmgr/osd/deploy-use/manage-task-sequences-to-automate-tasks#bkmk_perf)을 참조하세요.

### <a name="task-sequence-download-on-demand-over-the-internet"></a>인터넷을 통해 주문형으로 작업 순서 다운로드

<!--3601238-->

작업 순서를 사용하여 CMG(클라우드 관리 게이트웨이)를 통해 Windows 10 현재 위치 업그레이드를 배포할 수 있습니다. 그러나 작업 순서를 시작하기 전에 모든 콘텐츠를 로컬에 다운로드하도록 배포해야 합니다.

이 릴리스부터는 작업 순서 엔진이 콘텐츠 사용 CMG 또는 클라우드 배포 지점에서 패키지를 주문형으로 다운로드할 수 있습니다. 이러한 변경을 통해 인터넷 기반 장치에 대한 Windows 10 현재 위치 업그레이드 배포의 유연성을 강화할 수 있습니다.

자세한 내용은 [CMG를 통한 Windows 10 현재 위치 업그레이드 배포](/configmgr/osd/deploy-use/deploy-a-task-sequence#deploy-windows-10-in-place-upgrade-via-cmg)를 참조하세요.

### <a name="improvements-to-os-deployment"></a>향상된 OS 배포

이 릴리스에서는 OS 배포의 다음 사항이 개선되었습니다.

#### <a name="boot-image-keyboard-layout"></a>부팅 이미지 키보드 레이아웃

<!--4910348-->

부팅 이미지의 기본 키보드 레이아웃을 구성할 수 있습니다. 부팅 이미지의 **사용자 지정** 탭에서 새로 만들기 옵션을 사용하여 **WinPE에서 기본 키보드 레이아웃을 설정**합니다. en-us 이외의 언어를 선택하는 경우에도 Configuration Manager의 사용 가능한 입력 로캘에 en-us가 계속 포함됩니다. 디바이스에서 초기 키보드 레이아웃은 선택된 로캘이지만 사용자는 필요한 경우 디바이스를 en-us로 전환할 수 있습니다.

자세한 내용은 [부팅 이미지 관리](/configmgr/osd/get-started/manage-boot-images#customization)를 참조하세요.

#### <a name="import-a-single-index-of-an-os-upgrade-package"></a>OS 업그레이드 패키지의 단일 인덱스 가져오기

<!--4931110-->

OS 업그레이드 패키지를 가져올 때 **선택한 업그레이드 패키지의 install.wim 파일에서 특정 이미지 인덱스를 추출**할 수 있습니다. 이 동작은 OS 업그레이드 패키지의 기존 install.wim을 덮어쓴다는 점을 제외하고 [OS 이미지](/configmgr/osd/get-started/manage-operating-system-images#BKMK_AddOSImages)와 비슷합니다. 이미지 인덱스를 임시 위치로 추출한 다음, 원래 원본 디렉터리로 이동합니다.

자세한 내용은 [OS 업그레이드 패키지 관리](/configmgr/osd/get-started/manage-operating-system-upgrade-packages#BKMK_AddOSUpgradePkgs)를 참조하세요.

#### <a name="output-the-results-of-a-run-command-line-step-to-a-variable-during-a-task-sequence"></a>작업 순서 중 명령줄 실행 단계 결과를 변수에 출력

<!--user story 4977616/bug 4798352-->

이제 **명령줄 실행** 단계에 **작업 순서 변수에 출력**하는 옵션이 포함됩니다. 이 옵션을 사용하도록 설정하면 작업 순서가 명령의 출력을 사용자가 지정하는 사용자 지정 작업 순서 변수에 저장합니다.

자세한 내용은 [명령줄 실행](/configmgr/osd/understand/task-sequence-steps#BKMK_RunCommandLine)을 참조하세요.

#### <a name="improvements-to-task-sequence-debugger"></a>작업 순서 디버거의 향상된 기능

이 릴리스에 포함된 작업 순서 디버거의 향상된 기능은 다음과 같습니다.

- 새 작업 순서 변수 **TSDebugOnError**를 사용하여, 작업 순서에서 오류를 반환할 때 자동으로 디버거를 시작합니다.<!-- 5012536 -->

- 디버거에서 중단점을 만든 다음 작업 순서에서 컴퓨터를 다시 시작하는 경우, 디버거는 다시 시작한 후에도 중단점을 유지합니다.<!-- 5012509 -->

자세한 내용은 [작업 순서 디버거](/configmgr/osd/deploy-use/debug-task-sequence) 및 [작업 순서 변수 - TSDebugOnError](/configmgr/osd/understand/task-sequence-variables#TSDebugOnError)를 참조하세요.

#### <a name="improved-language-support-in-task-sequence"></a>작업 순서의 향상된 언어 지원

<!--5411057, 5138936-->

이 릴리스는 OS 배포 중에 언어 구성에 대한 제어를 추가합니다. 이러한 언어 설정을 이미 적용하고 있다면 이 변경으로 OS 배포 작업 순서를 간소화할 수 있습니다. 언어 또는 개별 스크립트 별로 여러 단계를 사용하는 대신, 기본 제공되는 **Windows 설정 적용** 단계의 언어별 인스턴스를 해당 언어에 대한 조건과 함께 사용합니다.

**Windows 설정 적용** 작업 순서 단계를 사용하여 다음 새로운 설정을 구성합니다.

- 입력 로캘(기본 키보드 레이아웃)
- 시스템 로캘
- UI 언어
- UI 언어 대체
- 사용자 로캘

자세한 내용은 [Windows 설정 적용](/configmgr/osd/understand/task-sequence-steps#BKMK_ApplyWindowsSettings)을 참조하세요.

#### <a name="new-variable-for-windows-10-in-place-upgrade"></a>Windows 10 현재 위치 업그레이드를 위한 새 변수

<!--4680263-->

Windows 설치가 완료되고 난 후 고성능 디바이스에서 발생하는 Windows 10 현재 위치 업그레이드 작업 순서의 타이밍 문제를 해결하기 위해 이제 새 작업 순서 변수 **SetupCompletePause**를 설정할 수 있습니다. 이 변수에 초 단위로 값을 할당하면, Windows 설치 프로세스에서 작업 순서를 시작하기 전까지 걸리는 시간을 지연시킵니다. 이 시간 제한을 통해 구성 관리자 클라이언트를 초기화할 수 있는 추가 시간이 제공됩니다.

자세한 내용은 [작업 순서 변수 - SetupCompletePause](/configmgr/osd/understand/task-sequence-variables#SetupCompletePause)를 참조하세요.

<!-- ## <a name="bkmk_userxp"></a> Software Center -->

## <a name="bkmk_sum"></a> 소프트웨어 업데이트

### <a name="additional-options-for-third-party-update-catalogs"></a>타사 업데이트 카탈로그에 대한 추가 옵션
<!--4469002-->
이제 타사 업데이트 카탈로그 동기화를 더욱 세부적으로 제어할 수 있습니다. Configuration Manager 버전 1910부터, 각 카탈로그의 동기화 일정을 개별적으로 구성할 수 있습니다. 범주화된 업데이트를 포함하는 카탈로그를 사용하는 경우 전체 카탈로그가 동기화되지 않도록 동기화에 특정 업데이트 범주만 포함되도록 구성할 수 있습니다. 범주화된 업데이트를 사용하여 범주를 배포할 때는 범주가 자동으로 다운로드되고 WSUS로 게시되도록 구성할 수 있습니다.

자세한 내용은 [타사 업데이트 사용](/sccm/sum/deploy-use/third-party-software-updates#bkmk_1910)을 참조하세요.

### <a name="use-delivery-optimization-for-all-windows-updates"></a>모든 Windows 업데이트에 대해 배달 최적화 사용
<!--4699118-->
이전에는 빠른 업데이트에서 전송 최적화만 사용할 수 있었습니다. Configuration Manager version 1910에서는 Windows 10 버전 1709 이상을 실행하는 클라이언트의 모든 Windows 업데이트 콘텐츠 배포에 전송 최적화를 사용할 수 있습니다.

자세한 내용은 다음을 참조하십시오.
- [Windows 10 업데이트 전송 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery#bkmk_DO-1910)
- [소프트웨어 업데이트를 위한 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#software-updates)
- [배달 최적화를 위한 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#delivery-optimization)

### <a name="additional-software-update-filter-for-adrs"></a>ADR용 추가 소프트웨어 업데이트 필터
<!--4852033-->
이제 자동 배포 규칙을 위한 업데이트 필터로 **Deployed**를 사용할 수 있습니다. 이 필터는 파일럿 또는 테스트 컬렉션에 배포해야 할 수 있는 새 업데이트를 식별하는 데 도움이 됩니다.

자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates#bkmk_adr-process)를 참조하세요.

## <a name="bkmk_o365"></a> Office 관리


### <a name="office-365-proplus-pilot-and-health-dashboard"></a>Office 365 ProPlus 파일럿 및 상태 대시보드
<!--4488272, 4488301-->

**Office 365 ProPlus 파일럿 및 상태 대시보드**를 사용하여 Office 365 ProPlus를 계획, 파일럿 및 배포할 수 있습니다. 대시보드는 Office 365 ProPlus를 사용하는 디바이스의 상태 인사이트를 제공하여 배포 계획에 영향을 줄 수 있는 문제를 식별하는 데 도움을 줍니다. **Office 365 ProPlus 파일럿 및 상태 대시보드**는 추가 기능 인벤토리를 기반으로한 파일럿 디바이스의 권장 사항을 제공합니다. 자세한 내용은 [Office 365 ProPlus 파일럿 및 상태 대시보드](/sccm/sum/deploy-use/office-365-dashboard#bkmk_pilot)를 참조하세요.

## <a name="bkmk_protect"></a> 보호

### <a name="bitlocker-management"></a>BitLocker 관리

<!--3601034-->

이제 Configuration Manager가 BitLocker 드라이브 암호화를 위한 다음과 같은 관리 기능을 제공합니다.

- 관리형 Windows 디바이스에 BitLocker 클라이언트 배포
- 디바이스 암호화 정책 관리
- 규정 준수 보고서
- 키 복구를 위한 웹 사이트 관리 및 모니터링
- 사용자 셀프 서비스 포털

자세한 내용은 [BitLocker 관리 계획](/configmgr/protect/plan-design/bitlocker-management)을 참조하세요.

## <a name="bkmk_admin"></a> Configuration Manager 콘솔

### <a name="view-active-consoles-and-message-administrators-through-console-connections"></a>콘솔 연결을 통해 활성 콘솔과 메시지 관리자 보기
<!--4923997-->
**콘솔 연결**을 다음과 같이 개선했습니다.

- Microsoft Teams를 통해 다른 Configuration Manager 관리자에게 메시지를 제공하는 기능.
- **마지막 콘솔 하트비트** 열이 **마지막으로 연결된 시간** 열로 바뀌었습니다.
  - 현재 어느 콘솔 연결이 활성 상태인지 확인할 수 있도록, 포그라운드에 있는 열린 콘솔이 10분마다 하트비트를 보냅니다.

자세한 내용은 For more information, see [최근에 연결된 콘솔 보기](/sccm/core/servers/manage/admin-console#bkmk_viewconnected) 및 [관리자에게 메시지 보내기](/sccm/core/servers/manage/admin-console#bkmk_message)를 참조하세요.

### <a name="client-diagnostics-actions"></a>클라이언트 진단 작업

<!--4433455-->

Configuration Manager 콘솔에 **클라이언트 진단**을 위한 새로운 디바이스 작업이 있습니다.

- **자세한 정보 로깅 사용** CCM 구성 요소의 전역 로그 수준을 자세히로 변경하고 디버그 로깅을 사용하도록 설정합니다.
- **자세한 정보 로깅 사용 안 함**: 전역 로그 수준을 기본값으로 변경하고 디버그 로깅을 사용하지 않도록 설정합니다.

자세한 내용은 [클라이언트 진단](/sccm/core/clients/manage/client-notification#client-diagnostics)을 참조하세요.

### <a name="improvements-to-console-search"></a>콘솔 검색 개선 사항
<!--4640570-->

이 릴리스에서는 Configuration Manager 콘솔의 검색 기능이 다음과 같이 개선되었습니다.

- 이제 **드라이버 패키지**에서 **모든 하위 폴더** 검색 옵션을 사용하고 노드의 **쿼리**를 사용할 수 있습니다.<!--2841181,5424892-->

- 검색에서 1000개 보다 많은 결과를 반환하는 경우 이제 알림 표시줄에서 **확인** 단추를 선택하여 더 많은 결과를 볼 수 있습니다.<!--4640570-->

## <a name="other-updates"></a>기타 업데이트

Configuration Manager용 Windows PowerShell cmdlet의 변경 내용에 대한 자세한 내용은 [PowerShell 버전 1910 릴리스 정보](https://docs.microsoft.com/powershell/sccm/1910-release-notes?view=sccm-ps)를 참조하세요.

<!--
As of this version, the following features are no longer pre-release:
- [SMS Provider administration service](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_admin-service)
- [Device Guard management](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)

Aside from new features, this release also includes additional changes such as bug fixes. For more information, see [Summary of changes in Configuration Manager current branch, version 1906](https://support.microsoft.com/help/4514258).

The following update rollup (4517869) is available in the console starting on October 1, 2019: [Update rollup for Configuration Manager current branch, version 1906](https://support.microsoft.com/help/4517869).

-->

<!--
### Hotfixes

The following additional hotfixes are available to address specific issues:

| ID | Title | Date | In-console |
|---------|---------|---------|---------|
| [4487960](https://support.microsoft.com/help/4487960) | Microsoft Intune connector certificate does not renew in Configuration Manager | 18 January 2019 | Yes |

> [!Note]  
> Starting in version 1902, in-console hotfixes now have supersedence relationships. For more information, see [Supersedence for in-console hotfixes](/sccm/core/servers/manage/updates#bkmk_supersede).
-->

## <a name="next-steps"></a>다음 단계

현재 버전 1910은 조기 업데이트 링을 위해 릴리스되었습니다. 이 업데이트를 설치하려면 옵트인해야 합니다. 자세한 내용은 [조기 업데이트 링](/sccm/core/servers/manage/checklist-for-installing-update-1910#early-update-ring)을 참조하세요.
<!--As of August 16, 2019, version 1906 is globally available for all customers to install.-->

이 버전을 설치할 준비가 되었으면 [Configuration Manager에 대한 업데이트 설치](/sccm/core/servers/manage/updates) 및 [업데이트 1910을 설치하기 위한 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1910)을 참조하세요.

> [!TIP]  
> 새 사이트를 설치하려면 기준 버전의 Configuration Manager를 사용합니다.  
>
> 다음에 대해 자세히 알아보세요.
>
> - [새 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  
> - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)  

알려진 중요한 문제는 [릴리스 정보](/sccm/core/servers/deploy/install/release-notes)를 참조하세요.

사이트를 업데이트한 후 [업데이트 후 검사 목록](/sccm/core/servers/manage/checklist-for-installing-update-1910#post-update-checklist)도 검토하세요.
