---
title: MSfB 통합 문제 해결
titleSuffix: Configuration Manager
description: 비즈니스 및 교육 통합을 위한 Microsoft Store의 가장 일반적인 문제 중 일부를 해결 하기 위한 제안과 해결 방법을 제공 합니다.
ms.date: 12/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 09929057-ecf2-4d49-aee0-709916932b14
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6e8f59e874d89bcb64d3331d40ef044c4c8beb01
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74814279"
---
# <a name="troubleshoot-the-microsoft-store-for-business-and-education-integration-with-configuration-manager"></a>Configuration Manager와의 비즈니스 및 교육 통합을 위한 Microsoft Store 문제 해결

이 문서에서는 MSfB (비즈니스 및 교육)를 Configuration Manager와 통합 하는 데 Microsoft Store 사용할 수 있는 주요 문제 중 일부에 대 한 주요 문제 해결 팁과 픽스를 제공 합니다.

Configuration Manager에서 비즈니스 및 교육용 Microsoft Store를 사용 하는 방법에 대 한 자세한 내용은 Configuration Manager를 사용 하 여 [비즈니스 및 교육용 Microsoft Store에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)를 참조 하세요.

## <a name="monitor"></a>모니터

### <a name="component-status"></a>구성 요소 상태

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고, **시스템 상태**를 확장하고, **구성 요소 상태** 노드를 선택합니다. 다음 구성 요소의 상태를 모니터링 합니다.

- SMS_BUSINESS_APP_PROCESS_MANAGER
- SMS_CLOUDCONNECTION

### <a name="sync-status"></a>동기화 상태

Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **비즈니스용 Microsoft Store** 노드를 선택합니다. **마지막 동기화 상태** 열을 확인 합니다.

### <a name="view-synchronized-apps"></a>동기화 된 앱 보기

Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **애플리케이션 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 선택합니다.


## <a name="log-files"></a>로그 파일

### <a name="msfbsyncworkerlog"></a>MSfBSyncWorker.log

이 로그 파일은 서비스 연결 지점에서 Configuration Manager 설치 디렉터리의 `\Logs`에 있습니다. 클라우드 서비스와의 통신에 대 한 정보를 기록 합니다. 이 정보에는 메타 데이터, 아이콘, 패키지 및 라이선스 파일 검색이 포함 됩니다.

로그 수준을 변경 하려면 `HKLM\SOFTWARE\Microsoft\SMS\Tracing\SMS_CLOUDCONNECTION` 레지스트리 키에서 `LoggingLevel` 값을 `0`로 변경 합니다. 자세한 내용은 [로깅 옵션 구성](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_reg-site)을 참조 하세요.

### <a name="sms_cloudconnectionlog"></a>SMS_CLOUDCONNECTION.log

이 로그 파일은 서비스 연결 지점에서 Configuration Manager 설치 디렉터리의 `\Logs`에 있습니다. MSfBSyncWorker 서비스가 시작 되지 않았거나 반복적으로 시작 및 중지 되는 경우이 로그 파일의 항목을 검토 합니다.

> [!NOTE]
> 이 로그 파일은 다른 기능과 공유 됩니다.

### <a name="businessappprocessworkerlog"></a>BusinessAppProcessWorker.log

이 로그 파일은 계층 내 최상위 사이트의 사이트 서버에 있습니다. Configuration Manager 설치 디렉터리의 `\Logs` 아래에 있습니다. 다음 프로세스에 대 한 정보를 기록 합니다.

- BusinessAppProcessWorker 구성 요소에 의해 동기화 된 메타 데이터 정보를 데이터베이스에 삽입 합니다.
- `\InstallDir\inboxes\businessappprocess.box`에서 파일 처리

### <a name="sms_business_app_process_managerlog"></a>SMS_BUSINESS_APP_PROCESS_MANAGER.log

이 로그 파일은 계층 내 최상위 사이트의 사이트 서버에 있습니다. Configuration Manager 설치 디렉터리의 `\Logs` 아래에 있습니다. BusinessAppProcessWorker 서비스가 시작 되지 않았거나 반복적으로 시작 및 중지 되는 경우이 로그 파일의 항목을 검토 합니다.



## <a name="last-sync-failed"></a>마지막 동기화에 실패했습니다.

마지막 동기화 상태가 *실패*인 경우 다음 [로그 파일](#log-files) 을 검토 하 여 증상을 파악 합니다.

- MSfBSyncWorker.log
- SMS_CLOUDCONNECTION.log

그리고 일반적인 문제에 대해서는 다음 섹션 중 하나를 살펴보세요.

- [권한 부여 오류](#bkmk_fail-symptom1)
- [비밀 키가 잘못 되었습니다.](#bkmk_fail-symptom2)
- [응용 프로그램 토큰을 가져오는 동안 오류 발생](#bkmk_fail-symptom3)
- [콘텐츠 위치가 존재 하지 않습니다.](#bkmk_fail-symptom4)
- [' GET ' 메서드를 호출 하는 http 요청을 수행 하는 동안 오류가 발생 했습니다.](#bkmk_fail-symptom5)
- [버퍼에 더 많은 바이트를 쓸 수 없습니다.](#bkmk_fail-symptom6)

### <a name="bkmk_fail-symptom1"></a>권한 부여 오류

#### <a name="cause"></a>원인

구성 된 Azure Active Directory (Azure AD) 응용 프로그램에이 테 넌 트의 비즈니스 및 교육용 Microsoft Store를 관리할 수 있는 권한이 없는 경우이 문제가 발생할 수 있습니다.

#### <a name="workaround"></a>해결 방법

1. 비즈니스 또는 교육 포털에 대 한 Microsoft Store 관리자로 로그인 합니다.
1. **설정**으로 이동 하 고 **관리 도구**를 선택 합니다.
1. 응용 프로그램이 나열 되지 않은 경우 **관리 도구 추가**를 선택 합니다. 그런 다음 이름으로 검색 하 고 Configuration Manager와 동일한 ClientID와 연결 된 Azure AD 응용 프로그램을 선택 합니다.
1. 상태가 **활성**으로 표시 되지 않으면 **작업** 섹션에서 **활성화** 를 선택 합니다.
1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **비즈니스용 Microsoft Store** 노드를 선택합니다. 저장소와 동기화 하거나 다음 동기화 간격이 발생할 때까지 기다립니다.

> [!Tip]
> Configuration Manager에서 ClientID를 찾으려면 다음을 수행 합니다.
>
> 1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장하고 **Azure Active Directory 테넌트** 노드를 선택합니다.
> 1. 비즈니스 및 교육 통합을 위해 Microsoft Store 사용 하는 테 넌 트를 선택 합니다.
> 1. 결과 창에서 일치 하는 응용 프로그램을 찾고 **클라이언트 ID** 열을 확인 합니다.

### <a name="bkmk_fail-symptom2"></a>비밀 키가 잘못 되었습니다.

#### <a name="cause"></a>원인

이 문제는 Azure AD 앱에서 비즈니스 및 교육 구성에 대 한 Microsoft Store에 대해 비밀 키가 만료 된 경우에 발생할 수 있습니다.

#### <a name="resolution"></a>해결 방법

Azure AD 응용 프로그램에 대 한 비밀 키를 갱신 합니다. 자세한 내용은 [비밀 키 갱신](/sccm/core/servers/deploy/configure/azure-services-wizard#bkmk_renew)을 참조하세요.

### <a name="bkmk_fail-symptom3"></a>응용 프로그램 토큰을 가져오는 동안 오류 발생

#### <a name="cause"></a>원인

이 문제는 연결 된 앱이 Azure AD에 더 이상 존재 하지 않는 경우 발생할 수 있습니다.

#### <a name="resolution"></a>해결 방법

비즈니스 및 교육용 Microsoft Store에 대 한 연결을 삭제 하 고 다시 만듭니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **비즈니스용 Microsoft Store** 노드를 선택합니다.
1. 기존 연결을 선택 합니다.
1. 리본에서 **삭제** 를 선택 합니다.

그런 다음 연결을 다시 만듭니다. 자세한 내용은 다음 아티클을 참조하세요.

- [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)
- [비즈니스 및 교육 동기화를 위한 Microsoft Store 설정](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#bkmk_setup)

### <a name="bkmk_fail-symptom4"></a>콘텐츠 위치가 존재 하지 않습니다.

#### <a name="cause"></a>원인

비즈니스 및 교육 연결에 대 한 Microsoft Store를 설정 하는 경우 동기화 된 콘텐츠를 저장할 네트워크 공유를 지정 합니다. 이 문제가 발생 하는 이유는이 공유가 없거나 권한이 잘못 된 경우에 발생할 수 있습니다.

구성 된 위치를 보려면 다음을 수행 합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **비즈니스용 Microsoft Store** 노드를 선택합니다.

1. 계정을 선택 하 고 해당 **속성**을 엽니다.

1. 구성 탭으로 전환합니다. **위치** 설정은 비즈니스 및 교육용 Microsoft Store에서 다운로드 한 응용 프로그램 콘텐츠를 저장할 네트워크 경로를 표시 합니다 **** .

#### <a name="workaround"></a>해결 방법

1. 아직 존재 하지 않는 경우 공유를 만듭니다.

1. 폴더에 대 한 NTFS 사용 권한 및 네트워크 공유에 대 한 사용 권한을 확인 합니다. 서비스 연결 지점의 컴퓨터 계정에 **읽기** 및 **쓰기** 권한을 부여 합니다.

위치를 다시 구성 하려면 새 콘텐츠 위치를 사용 하 여 연결을 삭제 하 고 다시 만듭니다.

### <a name="bkmk_fail-symptom5"></a>' GET ' 메서드를 호출 하는 http 요청을 수행 하는 동안 오류가 발생 했습니다.

#### <a name="cause"></a>원인

저장소에서 응용 프로그램을 동기화 하는 데 콘텐츠 URL이 만료 된 경우이 문제가 발생할 수 있습니다.

#### <a name="workaround"></a>해결 방법

동기화 프로세스 다시 시도

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고 **Cloud Services**를 확장한 후, **비즈니스용 Microsoft Store** 노드를 선택합니다.
1. 연결을 선택 합니다. 리본에서 **비즈니스용 Microsoft Store에서 동기화**를 선택 합니다.

매번 계속 진행 해야 합니다. 다음 요소에 따라 몇 가지 다시 시도를 수행할 수 있습니다.

- 오프 라인 응용 프로그램의 수
- 패키지의 크기
- 네트워크 속도

각 시도에서 오류가 발생 한 횟수를 표시 합니다. 오류 수가 감소 하지 않으면 다른 문제가 있습니다.

### <a name="bkmk_fail-symptom6"></a>버퍼에 더 많은 바이트를 쓸 수 없습니다.

#### <a name="cause"></a>원인

응용 프로그램의 패키지가 500 MB 보다 큰 경우이 문제가 발생할 수 있습니다. Configuration Manager는 500 MB 미만의 패키지가 있는 오프 라인 응용 프로그램의 자동 동기화만 지원 합니다.

#### <a name="workaround"></a>해결 방법

이러한 앱은 자동으로 동기화 할 수 없지만 콘텐츠를 다운로드 하 고 응용 프로그램을 수동으로 만들 수 있습니다.

1. **MSfBSynWorker**의 다음 줄에서 실패 한 응용 프로그램 ID를 가져옵니다.

    `Error(s) syncing or downloading application <ApplicationID> from the Microsoft Store for Business.`

1. 비즈니스 또는 교육 포털에 대 한 Microsoft Store 관리자로 로그인 합니다. 이 응용 프로그램에 대 한 페이지를 찾습니다.

    > [!Tip]
    > 페이지의 URL은 다음과 비슷합니다 `https://businessstore.microsoft.com/en-us/store/p/app/ApplicationID`

    1. 아직 선택 하지 않은 경우 **오프 라인**을 선택 합니다. 그런 다음 **관리**를 선택 합니다.

    1. 응용 프로그램 콘텐츠 공유에 지원 되는 모든 플랫폼에 대해 별도의 폴더를 만듭니다.

    1. 패키지 폴더에 패키지를 다운로드 합니다.

    1. 인코딩된 라이선스 파일을 패키지 폴더에 `.bin` 파일로 다운로드 합니다.

    1. 모든 필수 프레임 워크를 패키지 폴더에 다운로드 합니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하여 **애플리케이션 관리**를 확장하고 **애플리케이션** 노드를 선택합니다.

1. 응용 프로그램을 [만들고](/sccm/apps/deploy-use/create-applications)응용 프로그램 정보를 수동으로 지정 합니다.

    1. 이전에 다운로드 한 지원 되는 각 플랫폼에 대 한 배포 유형을 만듭니다.

    1. 유형: **Windows 앱 패키지(\*.appx, \*.appxbundle)**

    1. 필수 종속성 패키지가 아닌 실제 응용 프로그램 패키지에 대 한 appx/.appxbundle를 지정 합니다.

최종 **정보 가져오기** 페이지에서 다음 세부 정보를 확인 합니다.

- **라이선스 파일:** `.bin` 파일을 지정 합니다. 이 라이선스 파일은 오프 라인 앱에 필요 합니다.
- **Windows 앱 종속성:** 이 패키지에 대해 필요한 모든 종속성이 다운로드 되었는지 확인 합니다.


## <a name="sync-doesnt-run"></a>동기화 실행 안 됨

이 섹션에서는 다음과 같은 동기화 문제에 대해 설명 합니다.

- 수동으로 동기화 프로세스를 시작 하지만 실행 되지 않습니다.
- 사이트는 매일 자동으로 동기화 되지 않습니다.

다음 [로그 파일](#log-files) 을 검토 하 여 증상을 파악 합니다.

- BusinessAppProcessWorker.log
- SMS_BUSINESS_APP_PROCESS_MANAGER.log
- MSfBSyncWorker.log
- SMS_CLOUDCONNECTION.log

그리고 일반적인 문제에 대해서는 다음 섹션 중 하나를 살펴보세요.

- [수동 동기화가 시작 되지 않음](#bkmk_sync-symptom1)
- [자동 매일 동기화가 실행 되지 않고 SMS_BUSINESS_APP_PROCESS_MANAGER에서 "작업자 종료" 오류가 발생 합니다.](#bkmk_sync-symptom2)

### <a name="bkmk_sync-symptom1"></a>수동 동기화가 시작 되지 않음

#### <a name="cause"></a>원인

이 문제는 이전 동기화 후 10 분 이내에 동기화를 시작 하는 경우 발생할 수 있습니다. 10 분 간격 보다 더 자주 동기화 할 수 없습니다.

#### <a name="resolution"></a>해결 방법

다른 동기화를 시작 하기 전에 10 분 이상 기다립니다.

### <a name="bkmk_sync-symptom2"></a>자동 매일 동기화가 실행 되지 않고 SMS_BUSINESS_APP_PROCESS_MANAGER에서 "작업자 종료" 오류가 발생 합니다.

#### <a name="cause"></a>원인

SMS_BUSINESS_APP_PROCESS_MANAGER 구성 요소가 MSfBSyncWorker 스레드를 중지 하는 경우이 문제가 발생할 수 있습니다. 이 오류는 `2` 또는 `4` 작업자를 지정할 수 있습니다.

#### <a name="workaround"></a>해결 방법

**SMS_EXECUTIVE** 서비스를 다시 시작 합니다.

주 서비스를 다시 시작할 수 없는 경우 MSfB worker를 사용 하 여 두 구성 요소를 모두 중지 하 고 두 구성 요소를 모두 시작 합니다.

1. 서비스 연결 지점을 실행 하는 서버에서 Windows 레지스트리를 엽니다.

1. `HKLM\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_EXECUTIVE\Threads\SMS_CLOUDCONNECTION` 로 이동

    1. 요청 된 작업을 **중지**하도록 설정 합니다.

    1. 현재 상태 = **중지 됨**을 확인 하기 위해 새로 고칩니다.

1. `HKLM\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_EXECUTIVE\Threads\SMS_BUSINESS_APP_PROCESS_MANAGER` 로 이동

    1. 요청 된 작업을 **중지**하도록 설정 합니다.

    1. 현재 상태 = **중지 됨**을 확인 하기 위해 새로 고칩니다.

1. **SMS_CLOUDCONNECTION**에서 요청 된 작업을 **시작**으로 설정 합니다.

1. **SMS_BUSINESS_APP_PROCESS_MANAGER**에서 요청 된 작업을 **시작**으로 설정 합니다.


## <a name="language-related-issues"></a>언어 관련 문제

이 섹션에서는 다음과 같은 일반적인 문제를 다룹니다.

- [언어 선택 변경 내용이 적용 되지 않음](#bkmk_lang-symptom1)
- [일부 선택 된 언어가 모든 라이선스 정보에 대해 제공 되는 것은 아닙니다.](#bkmk_lang-symptom2)

### <a name="bkmk_lang-symptom1"></a>언어 선택 변경 내용이 적용 되지 않음

#### <a name="cause"></a>원인

이 문제는 언어 선택이 캐시 되 고 속성 값이 변경 된 후 지워지지 않는 경우에 발생할 수 있습니다.

#### <a name="workaround"></a>해결 방법

이 문제를 해결 하려면 **SMS_Executive** 서비스를 다시 시작 합니다.

### <a name="bkmk_lang-symptom2"></a>일부 선택 된 언어가 모든 라이선스 정보에 대해 제공 되는 것은 아닙니다.

#### <a name="cause"></a>원인

이 문제 Microsoft Store는 비즈니스 및 교육 응용 프로그램의 라이선스 정보에 지정 된 언어에 대 한 지역화 된 데이터가 포함 되지 않은 경우에 발생할 수 있습니다.

#### <a name="workaround"></a>해결 방법

만든 응용 프로그램에 대해 누락 된 언어를 수동으로 추가 합니다.


## <a name="offline-applications"></a>오프라인 애플리케이션

이 섹션에서는 다음과 같은 일반적인 문제를 다룹니다.

- [콘텐츠를 확인할 수 없기 때문에 오프 라인 응용 프로그램을 만들지 못했습니다.](#bkmk_off-symptom1)
- [오프 라인 라이선스 정보에서 만든 응용 프로그램 설치 실패](#bkmk_off-symptom2)

### <a name="bkmk_off-symptom1"></a>콘텐츠를 확인할 수 없기 때문에 오프 라인 응용 프로그램을 만들지 못했습니다.

#### <a name="cause"></a>원인

오프 라인 응용 프로그램의 동기화 된 콘텐츠가 손상 되거나 수정 된 경우이 문제가 발생할 수 있습니다.

#### <a name="workaround"></a>해결 방법

새 동기화를 시작 합니다. 동기화가 완료 되 면 잘못 된 콘텐츠 파일을 확인 하 고 다운로드 해야 합니다.

### <a name="bkmk_off-symptom2"></a>오프 라인 라이선스 정보에서 만든 응용 프로그램 설치 실패

#### <a name="cause"></a>원인

버전 1511 이전 버전의 Windows 10을 실행 하는 클라이언트에 응용 프로그램을 배포 하는 경우이 문제가 발생할 수 있습니다. 비즈니스 및 교육용 Microsoft Store의 오프 라인 사용이 허가 된 앱은 Windows 10 버전 1511 이상 에서만 지원 됩니다.

#### <a name="resolution"></a>해결 방법

최신 버전의 Windows 10을 설치합니다.


## <a name="next-steps"></a>다음 단계

추가 도움말을 찾으려면 [Configuration Manager 사용에 대 한 도움말 찾기](/sccm/core/understand/find-help)를 참조 하십시오.
