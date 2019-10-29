---
title: 로그 수집기
titleSuffix: Configuration Manager
description: 로그 수집기 도구를 사용 하 여 데스크톱 분석 문제를 해결할 수 있습니다.
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
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72810636"
---
# <a name="desktop-analytics-log-collector"></a>데스크톱 분석 로그 수집기

Configuration Manager 버전 1906부터 Configuration Manager 설치 디렉터리의 **DesktopAnalyticsLogsCollector** 도구를 사용 하 여 데스크톱 분석 장치 등록 문제를 해결할 수 있습니다. 이 도구는 몇 가지 기본적인 문제 해결 단계를 실행하고 관련 로그를 단일 작업 디렉터리로 수집합니다. Microsoft 지원과 함께이 콘텐츠를 공유할 수 있습니다.


## <a name="prerequisites"></a>필수 구성 요소

- Windows 10, Windows 8.1 또는 Windows 7 서비스 팩 1을 실행 하는 데스크톱 분석 클라이언트

- 관리자 권한으로 장치에서 스크립트를 실행 하 고 **관리자 권한으로를 실행**합니다.

    > [!Tip]
    > 이 도구에서 Configuration Manager **스크립트** 기능을 사용할 수 있습니다. 자세한 내용은 [예제 5: ](#bkmk_ex5)Configuration Manager **스크립트** 를 통해 스크립트를 배포 합니다.

- Windows 7 서비스 팩 1의 경우 PowerShell 버전 4.0 이상
    - [.NET framework 버전 4.6 이상](https://dotnet.microsoft.com/download/dotnet-framework)

    - [Windows Management Framework 버전 4.0](http://aka.ms/wmf4download) [이상](http://aka.ms/wmf5download)

## <a name="usage"></a>사용법

Configuration Manager 설치 콘텐츠에서 스크립트를 가져옵니다. `SMSSETUP\TOOLS\DesktopAnalyticsLogsCollector\DesktopAnalyticsLogsCollector.ps1`

``` Syntax
DesktopAnalyticsLogsCollector.ps1
    [-LogPath] <String>
    [-LogMode] <Int16>
    [-CollectNetTrace] <Int16>
    [-CollectUTCTrace] <Int16>
```

## <a name="parameters"></a>매개 변수

### `-LogPath`

로그 및 기타 출력 파일을 저장할 로컬 또는 UNC 경로를 지정 합니다.

**값**:

- 로컬 경로 (최대 길이 = 130) (예: `c:\myfolder`

- UNC 경로 (최대 길이 = 130) (예: `\\myserver\myfolder`

**형식**: 문자열

**위치**: 1

**기본값**: `$Env:SystemDrive\M365AnalyticsLogs` (이 매개 변수가 null 이거나 비어 있거나 공백인 경우 스크립트는 시스템 드라이브 아래에 M365AnalyticsLogs 폴더를 만듭니다.)

### `-LogMode`

로그의 세부 정보 표시 수준을 지정 합니다.

**값**:

- `0`: 스크립트 메시지를 PowerShell 명령 창에만 기록 합니다.

- `1`: 출력 폴더 및 PowerShell 명령 창에서 두 로그 파일에 스크립트 메시지를 기록 합니다.

- `2`: 출력 폴더 아래에 있는 로그 파일에 스크립트 메시지를 기록 합니다.

**형식**: Int16

**위치**: 2

**기본값**: `1` (로그 파일 및 PowerShell 명령 창에 스크립트 메시지 기록)

### `-CollectNetTrace`

스크립트에서 네트워크 추적을 수집 하는지 여부를 지정 합니다.

**값**:

- `0`: 네트워크 추적을 사용 하도록 설정 하지 마세요.

- `1` (0이 아닌 정수 값): 네트워크 추적을 사용 하도록 설정 하 고 결과를 수집 합니다.

**형식**: Int16

**위치**: 3

**기본값**: `0` (네트워크 추적 사용 안 함)

### `-CollectUTCTrace`

스크립트가 Windows UTC 추적을 수집 하 고 연결 진단을 실행 하는지 여부를 지정 합니다.

**값**:

- `0`: UTC 추적을 사용 하지 않거나 연결 진단을 실행 하지 마세요.

- `1` (0이 아닌 정수 값): UTC 추적을 사용 하도록 설정 하 고, 연결 진단을 실행 하 고, 결과를 수집 합니다.

**형식**: Int16

**위치**: 4

**기본값**: `0` (UTC 추적을 사용 하지 않거나 연결 진단을 실행 하지 않음)


## <a name="output"></a>출력

스크립트는 지정 된 경로 아래에 *작업 폴더* 를 만듭니다. 예를 들면 **M365AnalyticsLogs_yy_MM_dd_HH_mm_ss**입니다. 모든 출력 파일을이 작업 폴더에 저장 합니다.

스크립트가 *로그 파일*에 쓸 수 있도록 설정 하면 작업 폴더에 스크립트가 생성 됩니다. 예를 들면 **M365AnalyticsLogs_ yy_MM_dd_HH_mm_ss**입니다.

또한 스크립트는 작업 폴더에 다른 *진단 파일* 을 생성 합니다. 예:

- `installedKBs.txt`: 장치에 설치 된 Windows 업데이트 목록
- `appcompat`: 응용 프로그램 호환성 데이터
- `Reg*.txt`: Windows 레지스트리에서 내보낸 데이터가 포함 된 일련의 파일


## <a name="examples"></a>예

### <a name="bkmk_ex1"></a>예 1: PowerShell 명령 창을 통해 기본값을 사용 하 여 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1
```

### <a name="bkmk_ex2"></a>예 2: 지정 된 매개 변수를 사용 하 여 PowerShell 명령 창을 통해 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1 -LogPath "c:\testABC" -LogMode 0 -CollectNetTrace 0 -CollectUTCTrace 0
```

### <a name="bkmk_ex3"></a>예 3: 위치에 지정 된 매개 변수를 사용 하 여 PowerShell 명령 창을 통해 스크립트 실행

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1 "c:\testABC" 2 0 0
```

### <a name="bkmk_ex4"></a>예 4: 지정 된 매개 변수 및 자세한 메시지와 함께 PowerShell 명령 창을 통해 스크립트를 실행 합니다.

```PowerShell
.\DesktopAnalyticsLogsCollector.ps1 -LogMode 1 -Verbose
```

### <a name="bkmk_ex5"></a>예 5: Configuration Manager **스크립트** 를 통해 스크립트 배포

자세한 내용은 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

DesktopAnalyticsLogsCollector는 Microsoft에서 디지털 서명 합니다. 대상 장치에서 Microsoft 코드 서명 인증서를 신뢰할 수 있는 게시자로 추가 해야 할 수도 있습니다.

1. Windows 탐색기에서 스크립트 속성을 엽니다. **디지털 서명** 탭으로 전환 하 고 **세부 정보**를 선택 합니다.

2. **일반** 탭에서 **인증서 보기**를 선택 합니다.

    > [!Note]
    > 다른 메커니즘을 통해 인증서를 배포 하려면 먼저 인증서를 파일로 내보냅니다. **세부 정보** 탭으로 이동 하 고 **파일에 복사**를 선택 합니다.

3. **인증서 설치**를 선택 합니다. 인증서를 가져와 **신뢰할 수 있는 게시자** 저장소에 배치 합니다.


## <a name="see-also"></a>참고 항목

- [Desktop Analytics 문제 해결](/sccm/desktop-analytics/troubleshooting)

- [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)
