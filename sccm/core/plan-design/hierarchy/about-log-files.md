---
title: 로그 파일 정보
titleSuffix: Configuration Manager
description: 로그 파일을 사용하여 Configuration Manager 클라이언트 및 사이트 시스템 문제를 해결할 수 있습니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: b1751e3c-a60c-4ab7-a943-2595df1eb612
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3885e4323e8c41bcf644de7c62fd1dcb22c684c8
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68538049"
---
# <a name="about-log-files-in-configuration-manager"></a>Configuration Manager의 로그 파일 정보

Configuration Manager에서는 클라이언트 및 사이트 서버 구성 요소가 개별 로그 파일에 프로세스 정보를 기록합니다. 이러한 로그 파일의 정보를 사용하면 발생할 수 있는 문제를 해결할 수 있습니다. Configuration Manager에서는 기본적으로 클라이언트 및 서버 구성 요소 로깅을 사용하도록 설정됩니다.

이 문서에서는 Configuration Manager 로그 파일에 대한 일반 정보를 제공합니다. 여기에는 사용할 도구, 로그를 구성하는 방법, 로그를 찾을 위치가 포함됩니다. 특정 로그 파일에 대한 자세한 내용은 [로그 파일 참조](/sccm/core/plan-design/hierarchy/log-files)를 참조하세요.


## <a name="BKMK_AboutLogs"></a>작동 방식

Configuration Manager의 프로세스 대부분은 해당 프로세스 전용 로그 파일에 작업 정보를 기록합니다. 로그 파일은 **.log** 또는 **.lo_** 파일 확장명으로 식별됩니다. Configuration Manager는 로그가 최대 크기에 도달할 때까지 .log 파일에 내용을 기록합니다. 로그가 가득 차면 .log 파일이 이름은 같지만 확장명은 .lo_인 파일에 복사되고 프로세스 또는 구성 요소는 계속 .log 파일에 기록합니다. .log 파일이 다시 최대 크기에 도달하면 .lo_ 파일을 덮어쓰게 되고 프로세스가 반복됩니다. 일부 구성 요소는 날짜 및 타임스탬프를 로그 파일 이름에 추가하고 .log 확장명을 유지하여 로그 파일 기록을 설정합니다.


## <a name="bkmk_tools"></a> 로그 뷰어 도구

모든 Configuration Manager 로그 파일은 일반 텍스트이므로 메모장과 같은 텍스트 리더를 사용하여 볼 수 있습니다. 로그는 다음 전문 도구 중 하나를 사용하여 가장 잘 볼 수 있는 고유한 서식을 사용합니다.

- [CMTrace](#cmtrace)
- [OneTrace](#onetrace)
- [지원 센터 로그 뷰어](#support-center-log-viewer)

### <a name="cmtrace"></a>CMTrace

로그를 보려면 Configuration Manager 로그 뷰어 도구인 **CMTrace**를 사용합니다. 이 도구는 Configuration Manager 원본 미디어의 \\SMSSetup\\Tools 폴더에 있습니다. CMTrace 도구는 소프트웨어 라이브러리에 추가된 모든 부팅 이미지에 추가됩니다. 1806 버전부터 이제 CMTrace 로그 보기 도구가 Configuration Manager 클라이언트와 함께 자동으로 설치됩니다.<!--1357971--> 자세한 내용은 [CMTrace](/sccm/core/support/cmtrace)를 참조하세요.

### <a name="onetrace"></a>OneTrace

버전 1906부터는 **OneTrace**가 지원 센터의 새 로그 뷰어입니다. CMTrace와 작동이 비슷하며 기능이 향상되었습니다. 자세한 내용은 [지원 센터 OneTrace](/sccm/core/support/support-center-onetrace)를 참조하세요.

### <a name="support-center-log-viewer"></a>지원 센터 로그 뷰어

**지원 센터**에는 최신 로그 뷰어가 포함되어 있습니다. 이 도구는 CMTrace를 대신하며, 탭 및 도킹 가능한 창을 지원하는 사용자 지정 가능한 인터페이스를 제공합니다. 빠른 프레젠테이션 계층이 있으며 몇 초 안에 대용량 로그 파일을 로드할 수 있습니다. 자세한 내용은 [지원 센터 로그 뷰어 참조](/sccm/core/support/support-center-ui-reference#bkmk_log-viewer)를 참조하세요.

> [!Note]  
> 지원 센터 및 OneTrace는 WPF(Windows Presentation Foundation)를 사용합니다. 이 구성 요소는 Windows PE에서 사용할 수 없습니다. 계속 작업 순서 배포를 통해 부트 이미지에서 CMTrace를 사용합니다.


## <a name="bkmk_logoptions"></a> 로깅 옵션 구성

자세한 정보 표시 수준, 크기, 기록과 같은 로그 파일의 구성을 변경할 수 있습니다. 이러한 설정을 변경하는 방법에는 여러 가지가 있습니다.

- [클라이언트 설치 도중](#bkmk_logoptions-clientprop)
- [Configuration Manager Service Manager 사용](#bkmk_logoptions-sm)
- [Windows 레지스트리 사용](#bkmk_logoptions-registry)

### <a name="bkmk_logoptions-clientprop"></a> 클라이언트 설치 도중 로깅 옵션 구성

설치 중에 클라이언트 로그 파일의 구성을 설정할 수 있습니다. 다음 속성을 사용합니다.

- CCMENABLELOGGING
- CCMDEBUGLOGGING
- CCMLOGLEVEL
- CCMLOGMAXHISTORY
- CCMLOGMAXSIZE

자세한 내용은 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties#clientMsiProps)을 참조합니다.

### <a name="bkmk_logoptions-sm"></a> Configuration Manager Service Manager를 사용하여 로깅 옵션 구성

Configuration Manager가 로그 파일을 저장하는 위치 및 크기를 변경할 수 있습니다.  

로그 파일의 크기를 수정하거나, 로그 파일의 이름과 위치를 변경하거나, 여러 구성 요소가 하나의 로그 파일에 기록하도록 하려면 다음 단계를 따르세요.  

#### <a name="modify-logging-for-a-component"></a>구성 요소의 로깅 수정  

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **시스템 상태**를 펼친 다음 **사이트 상태** 또는 **구성 요소 상태** 노드를 선택합니다.  

2. 리본 메뉴에서 **시작**을 선택한 다음 **Configuration Manager Service Manager**를 선택합니다.  

3. Configuration Manager Service Manager가 열리면 관리할 사이트에 연결합니다. 관리할 사이트가 표시되지 않으면 **사이트**를 선택하고 **연결**을 선택한 다음 올바른 사이트의 사이트 서버 이름을 입력합니다.  

4. 해당 사이트를 확장하고 관리할 구성 요소의 위치에 따라 **구성 요소** 또는 **서버**로 이동합니다.  

5. 오른쪽 창에서 구성 요소를 하나 이상 선택합니다.  

6. **구성 요소** 메뉴에서 **로깅**을 선택합니다.  

7. **Configuration Manager 구성 요소 로깅** 대화 상자에서 선택한 구성 요소에 사용할 수 있는 구성 옵션을 완료합니다.  

8. **확인**을 선택하여 구성을 저장합니다.  

### <a name="bkmk_logoptions-registry"></a> Windows 레지스트리를 사용하여 로깅 옵션 구성

<!-- SCCMDocs#992 -->
서버 또는 클라이언트에서 Windows 레지스트리를 사용하여 다음 로깅 옵션을 변경합니다.

- 자세한 정보 표시 수준
- 최대 기록
- 최대 크기

문제를 해결할 때 Configuration Manager에 자세한 정보 로깅을 사용하도록 설정하여 로그 파일에 추가 세부 정보를 기록할 수 있습니다.

> [!Warning]
> 이러한 설정이 잘못 구성되면 Configuration Manager가 많은 양의 정보를 로깅하거나 전혀 로깅하지 않을 수 있습니다. 이 데이터는 문제 해결에 도움이 될 수 있지만 프로덕션 사이트에서 이러한 값을 변경할 때는 주의해야 합니다. 항상 랩 환경에서 이러한 변경 사항을 먼저 테스트합니다. 과도한 로깅이 발생해 로그 파일에서 관련 정보를 찾기 어렵게 될 수 있습니다.

이러한 레지스트리 설정을 변경한 후에는 구성 요소를 다시 시작합니다.

- 클라이언트 설정을 변경하는 경우 **SMS 에이전트 호스트** 서비스(CcmExec)를 다시 시작합니다.
- 서버 설정을 변경하는 경우 **SMS Executive** 서비스를 다시 시작합니다.

레지스트리 설정은 구성 요소에 따라 달라집니다.

- [클라이언트 및 관리 지점](#bkmk_reg-client)
- [사이트 서버](#bkmk_reg-site)
- [사이트 시스템 역할](#bkmk_reg-role)
- [Configuration Manager 콘솔](#bkmk_reg-console)

#### <a name="bkmk_reg-client"></a> 클라이언트 및 관리 지점 로깅 옵션

클라이언트 또는 관리 지점 사이트 시스템에서 모든 구성 요소의 로깅 옵션을 구성하려면 다음 Windows 레지스트리 키에서 다음 **REG_DWORD** 값을 구성합니다.

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Logging\@Global`

|Name  |값  |설명  |
|---------|---------|---------|
|LogLevel|`0`: 자세한 정보 표시<br>`1`: 기본값<br>`2`: 경고 및 오류<br>`3`: 오류만|로그 파일에 쓸 세부 정보 수준.|
|LogMaxHistory|0보다 크거나 같은 정수입니다. 예:<br>`0`: 기록 없음<br>`1`: 기본값|로그 파일이 최대 크기에 도달하면 클라이언트는 백업으로 이름을 바꾸고 새 로그 파일을 만듭니다. 유지할 이전 버전 수를 지정합니다.|
|LogMaxSize|10,000보다 크거나 같은 정수입니다. 예:<br>250000|최대 로그 파일 크기(바이트)입니다. 로그가 지정된 크기로 성장하면 클라이언트는 기록 파일로 이름을 바꾸고 새 파일을 만듭니다. 기본값은 250,000바이트입니다.|

> [!Note]  
> 이 레지스트리 키에 있을 수 있는 다른 값은 변경하지 마세요.

고급 디버깅의 경우 다음 Windows 레지스트리 키 아래 이 **REG_SZ** 값을 추가할 수도 있습니다.

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Logging\DebugLogging`

|Name  |값  |설명  |
|---------|---------|---------|
|사용 | `True`: 디버그 로그 사용<br>`False`: 디버그 로그 사용 안 함 |문제 해결을 위해 디버그 로깅을 사용하도록 설정합니다.|

이 설정을 사용하면 클라이언트는 문제 해결을 위한 하위 수준 정보를 로깅합니다. 프로덕션 사이트에서는 이 설정을 사용하지 마세요. 과도한 로깅이 발생해 로그 파일에서 관련 정보를 찾기 어렵게 될 수 있습니다. 문제를 해결한 후에는 이 설정을 해제해야 합니다.

#### <a name="bkmk_reg-site"></a> 사이트 서버 로깅 옵션

Configuration Manager 사이트 서버에서 설정을 전역으로 구성하거나 특정 구성 요소에 대해 구성할 수 있습니다.

다음 Windows 레지스트리 키에서 이러한 값을 구성합니다.

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Tracing`

|Name  |값  |유형  |설명
|---------|---------|---------|---------|
|SqlEnabled| `1`: SQL 추적 사용<br> `0`: SQL 추적 사용 안 함 |REG_DWORD|모든 사이트 서버 로그에 SQL 추적 로깅을 추가합니다.|
|ArchiveEnabled| `1`: 로그 보관 사용<br> `0`: 로그 보관 사용 안 함 | REG_DWORD |기록 보존을 위해 별도의 위치에 사이트 서버 로그를 보관합니다.|
|ArchivePath| 유효한 폴더 경로(예:`C:\Logs\Archive`) | REG_SZ |사이트 서버 로그를 보관할 경로입니다.|

문제 해결을 위해서만 SQL 추적을 사용합니다. 프로덕션 사이트에서는 사용하지 마세요. 과도한 로깅이 발생해 로그 파일에서 관련 정보를 찾기 어렵게 될 수 있습니다. 문제를 해결한 후에는 이 설정을 해제해야 합니다.

> [!Note]  
> 이 레지스트리 키에 있을 수 있는 다른 값은 변경하지 마세요.

특정 서버 구성 요소의 로깅 옵션을 구성하려면 다음 Windows 레지스트리 키에서 다음 **REG_DWORD** 값을 구성합니다.

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\Tracing\<ComponentName>`

|Name  |값  |설명  |
|---------|---------|---------|
|LoggingLevel|`0`: 자세한 정보 표시<br>`1`: 기본값<br>`2`: 경고 및 오류<br>`3`: 오류만|로그 파일에 쓸 세부 정보 수준.|
|LogMaxHistory|0보다 크거나 같은 정수입니다. 예:<br>`0`: 기록 없음<br>`1`: 기본값|로그 파일이 최대 크기에 도달하면 서버는 백업으로 이름을 바꾸고 새 로그 파일을 만듭니다. 유지할 이전 버전 수를 지정합니다.|
|MaxFileSize|10,000보다 크거나 같은 정수입니다. 예:<br>250000|최대 로그 파일 크기(바이트)입니다. 로그가 지정된 크기로 성장하면 클라이언트는 기록 파일로 이름을 바꾸고 새 파일을 만듭니다. 기본값은 250,000바이트입니다.|
|DebugLogging| `1`: 디버그 로그 사용<br>`0`: 디버그 로그 사용 안 함 |문제 해결을 위해 디버그 로깅을 사용하도록 설정합니다.|

DebugLogging 설정을 사용하면 서버는 문제 해결을 위한 하위 수준 정보를 로깅합니다. 프로덕션 사이트에서는 이 설정을 사용하지 마세요. 과도한 로깅이 발생해 로그 파일에서 관련 정보를 찾기 어렵게 될 수 있습니다. 문제를 해결한 후에는 이 설정을 해제해야 합니다.

> [!Note]  
> 이 레지스트리 키에 있을 수 있는 다른 값은 변경하지 마세요.

#### <a name="bkmk_reg-role"></a> 사이트 시스템 역할 로깅 옵션

Configuration Manager 서버 역할을 호스팅하는 사이트 시스템에서 설정을 전역으로 구성하거나 특정 구성 요소에 대해 구성할 수 있습니다.

특정 서버 구성 요소의 로깅 옵션을 구성하려면 다음 Windows 레지스트리 키에서 다음 **REG_DWORD** 값을 구성합니다.

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\<ComponentName>\Logging`

예를 들어 배포 지점 역할의 경우 다음과 같습니다.

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP\Logging`

|Name  |값  |설명  |
|---------|---------|---------|
|LogLevel|`0`: 자세한 정보 표시<br>`1`: 기본값<br>`2`: 경고 및 오류<br>`3`: 오류만|로그 파일에 쓸 세부 정보 수준.|
|LogMaxHistory|0보다 크거나 같은 정수입니다. 예:<br>`0`: 기록 없음<br>`1`: 기본값|로그 파일이 최대 크기에 도달하면 서버는 백업으로 이름을 바꾸고 새 로그 파일을 만듭니다. 유지할 이전 버전 수를 지정합니다.|
|LogMaxSize|10,000보다 크거나 같은 정수입니다. 예:<br>250000|최대 로그 파일 크기(바이트)입니다. 지정된 크기까지 로그가 증가하면 클라이언트는 기록 파일로 이름을 바꾸고 새 파일을 만듭니다. 기본값은 250,000바이트입니다.|

> [!Note]  
> 이 레지스트리 키에 있을 수 있는 다른 값은 변경하지 마세요.

#### <a name="bkmk_reg-console"></a> Configuration Manager 콘솔 로깅 옵션

Configuration Manager 콘솔의 AdminUI.log의 자세한 정보 표시 수준을 변경하려면 다음 절차를 따르세요.

1. 메모장 같은 XML 편집기에서 콘솔 구성 파일 **Microsoft.ConfigurationManagement.exe.config**를 엽니다. 기본 구성 파일은 다음 위치에 있습니다. `C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`

1. **system.diagnostics** > **원본** > **원본** 요소에서 **switchValue** 속성을 `Error`에서 `Verbose`로 변경합니다. 예:

    원본: `<source name="SmsAdminUISnapIn" switchValue="Error">` 새로 만들기: `<source name="SmsAdminUISnapIn" switchValue="Verbose" >`

1. 파일을 저장하고 콘솔을 다시 시작하세요.


## <a name="BKMK_LogLocation"></a> 로그 파일 찾기

Configuration Manager와 종속 구성 요소는 로그 파일을 다양한 위치에 저장합니다. 이러한 위치는 로그 파일을 만드는 프로세스와 환경의 구성에 따라 달라집니다.

다음 위치는 기본값입니다. 사용자 환경에서 설치 디렉터리를 사용자 지정한 경우 실제 경로는 달라질 수 있습니다.

- 클라이언트: `C:\Windows\CCM\logs`
- 서버: `C:\Program Files\Microsoft Configuration Manager\Logs`
- 관리 지점: `C:\SMS_CCM\Logs`
- Configuration Manager 콘솔: `C:\Program Files (x86)\Microsoft Configuration Manager\AdminConsole\AdminUILog`
- IIS: `C:\inetpub\logs\logfiles\w3svc1`

### <a name="task-sequence-log-locations"></a>작업 순서 로그 위치

작업 순서 로그 파일 **smsts.log** 의 위치는 작업 순서의 단계에 따라 달라집니다.

- Windows PE에서 [디스크 포맷 및 파티션 만들기](/sccm/osd/understand/task-sequence-steps#BKMK_FormatandPartitionDisk) 단계 이전: `X:\Windows\temp\smstslog\smsts.log`(X는 Windows PE RAM 드라이브)
- Windows PE에서 **디스크 포맷 및 파티션 만들기** 단계 이후: `X:\smstslog\smsts.log`였다가 디스크가 준비되면 `C:\_SMSTaskSequence\Logs\smstslog\smsts.log`로 복사됨
- 클라이언트를 설치하기 전 새 Windows OS: `C:\_SMSTaskSequence\Logs\smstslog\smsts.log`
- 클라이언트를 설치한 후 Windows: `C:\Windows\CCM\Logs\smstslog\smsts.log`
- 작업 순서가 완료된 후 Windows: `C:\Windows\CCM\Logs\smsts.log`

> [!Tip]  
> 읽기 전용 작업 순서 변수 [_SMSTSLogPath](/sccm/osd/understand/task-sequence-variables#SMSTSLogPath)는 항상 현재 로그 파일의 경로를 포함합니다.


## <a name="see-also"></a>참고 항목

- [로그 파일 참조](/sccm/core/plan-design/hierarchy/log-files)

- [지원 센터 OneTrace](/sccm/core/support/support-center-onetrace)

- [지원 센터 로그 파일 뷰어](/sccm/core/support/support-center#support-center-log-file-viewer)

- [CMTrace](/sccm/core/support/cmtrace)
