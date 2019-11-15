---
title: 로그 수집기
titleSuffix: Configuration Manager
description: 로그 수집기 도구를 사용하여 Desktop Analytics 문제를 해결할 수 있습니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 349b2a69-af46-481f-afb2-24d98774e852
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e133adf70f66041da43570503c0e7813a59350d0
ms.sourcegitcommit: d3aa20e2d12b5a68c7d672172234c65095fd4ce8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810636"
---
# <a name="desktop-analytics-log-collector"></a>Desktop Analytics 로그 수집기

Configuration Manager 버전 1906부터 Configuration Manager 설치 디렉터리에서 **DesktopAnalyticsLogsCollector.ps1** 도구를 사용하여 Desktop Analytics 디바이스 등록 문제를 해결할 수 있습니다. 이 도구는 몇 가지 기본적인 문제 해결 단계를 실행하고 관련 로그를 단일 작업 디렉터리로 수집합니다. 이 콘텐츠를 Microsoft 지원과 공유할 수 있습니다.


## <a name="prerequisites"></a>필수 구성 요소

- Windows 10, Windows 8.1 또는 Windows 7 서비스 팩 1을 실행하는 Desktop Analytics 클라이언트

- 디바이스에서 관리자로 스크립트를 실행하고 **관리자 권한으로 실행**합니다.

    > [!Tip]
    > 이 도구에서 Configuration Manager **스크립트** 기능을 사용할 수 있습니다. 자세한 내용은 [예제 5: Configuration Manager **스크립트**를 통해 스크립트 배포](#bkmk_ex5)를 참조하세요.

- Windows 7 서비스 팩 1의 경우 PowerShell 버전 4.0 이상
    - [.NET 프레임워크 버전 4.6 이상](https://dotnet.microsoft.com/download/dotnet-framework)

    - [Windows Management Framework 버전 4.0](http://aka.ms/wmf4download) [이상](http://aka.ms/wmf5download)

## <a name="usage"></a>사용

Configuration Manager 설치 콘텐츠(`SMSSETUP\TOOLS\DesktopAnalyticsLogsCollector\DesktopAnalyticsLogsCollector.ps1`)에서 스크립트를 가져옵니다.

``` Syntax
DesktopAnalyticsLogsCollector.ps1
    [-LogPath] <String>
    [-LogMode] <Int16>
    [-CollectNetTrace] <Int16>
    [-CollectUTCTrace] <Int16>
```

## <a name="parameters"></a>매개 변수

### `-LogPath`

로그 및 기타 출력 파일을 저장할 로컬 또는 UNC 경로를 지정합니다.

**값**:

- 로컬 경로(최대 길이 = 130), 예를 들면 `c:\myfolder`와 같습니다.

- UNC 경로(최대 길이 = 130), 예를 들면 `\\myserver\myfolder`와 같습니다.

**형식**: 문자열

**위치**: 1

**기본값**: `$Env:SystemDrive\M365AnalyticsLogs` (매개 변수가 null이거나, 비어 있거나, 공백인 경우 스크립트는 시스템 드라이브 아래에 M365AnalyticsLogs 폴더를 만듭니다.)

### `-LogMode`

로그의 세부 정보 표시 수준을 지정합니다.

**값**:

- `0`: 스크립트 메시지를 PowerShell 명령 창에만 기록합니다.

- `1`: 출력 폴더와 PowerShell 명령 창에서 로그 파일 모두에 스크립트 메시지를 기록합니다.

- `2`: 스크립트 메시지를 출력 폴더 아래에 있는 로그 파일에만 기록합니다.

**형식**: Int16

**위치**: 2

**기본값**: `1` (스크립트 파일을 로그 파일과 PowerShell 명령 창에 모두 기록합니다.)

### `-CollectNetTrace`

스크립트가 네트워크 추적을 수집하는지 여부를 지정합니다.

**값**:

- `0`: 네트워크 추적을 활성화하지 마세요.

- `1` (0이 아닌 정수 값): 네트워크 추적을 활성화하고 결과를 수집합니다.

**형식**: Int16

**위치**: 3

**기본값**: `0` (네트워크 추적을 활성화하지 마세요.)

### `-CollectUTCTrace`

스크립트가 Windows UTC 추적을 수집하고 연결 진단을 실행할지 여부를 지정합니다.

**값**:

- `0`: UTC 추적을 활성화하거나 연결 진단을 실행하지 마세요.

- `1` (0이 아닌 정수 값): UTC 추적을 활성화하여 연결 진단을 실행하고 결과를 수집합니다.

**형식**: Int16

**위치**: 4

**기본값**: `0` (UTC 추적을 활성화하거나 연결 진단을 실행하지 마세요.)


## <a name="output"></a>출력

스크립트는 지정된 경로 아래에 *작업 폴더*를 만듭니다. 예: **M365AnalyticsLogs_yy_MM_dd_HH_mm_ss**. 모든 출력 파일을 이 작업 폴더에 저장합니다.

스크립트가 *로그 파일*에 쓸 수 있도록 설정하면 작업 폴더에 하나가 생성됩니다. 예: **M365AnalyticsLogs_ yy_MM_dd_HH_mm_ss.txt**.

스크립트는 작업 폴더에 다른 *진단 파일*도 생성합니다. 예:

- `installedKBs.txt`: 디바이스에 설치된 Windows 업데이트 목록
- `appcompat`: 애플리케이션 호환성 데이터
- `Reg*.txt`: Windows 레지스트리에서 내보낸 데이터가 포함된 일련의 파일


## <a name="examples"></a>예

### <a name="bkmk_ex1"></a> 예제 1: 기본값을 사용하여 PowerShell 명령 창을 통해 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1
```

### <a name="bkmk_ex2"></a> 예제 2: 지정된 매개 변수를 사용하여 PowerShell 명령 창을 통해 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1 -LogPath "c:\testABC" -LogMode 0 -CollectNetTrace 0 -CollectUTCTrace 0
```

### <a name="bkmk_ex3"></a> 예제 3: 위치에 지정된 매개 변수를 사용하여 PowerShell 명령 창을 통해 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1 "c:\testABC" 2 0 0
```

### <a name="bkmk_ex4"></a> 예제 4: 지정된 매개 변수 및 상세 메시지를 사용하여 PowerShell 명령 창을 통해 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1 -LogMode 1 -Verbose
```

### <a name="bkmk_ex5"></a> 예제 5: Configuration Manager **스크립트**를 통해 스크립트 배포

자세한 내용은 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

DesktopAnalyticsLogsCollector.ps1은 Microsoft에 의해 디지털 서명됩니다. 대상 디바이스에서 Microsoft 코드 서명 인증서를 신뢰할 수 있는 게시자로 추가해야 할 수도 있습니다.

1. Windows 탐색기에서 스크립트의 속성을 엽니다. **디지털 서명** 탭으로 전환하고 **세부 정보**를 선택합니다.

2. **일반** 탭에서 **인증서 보기**를 선택합니다.

    > [!Note]
    > 다른 메커니즘을 통해 인증서를 배포하려면 먼저 인증서를 파일로 내보냅니다. **세부 정보** 탭으로 이동하여 **파일에 복사**를 클릭합니다.

3. **인증서 설치**를 선택합니다. 인증서를 가져와 **신뢰할 수 있는 게시자** 저장소에 배치합니다.


## <a name="see-also"></a>참고 항목

- [Desktop Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)

- [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)
