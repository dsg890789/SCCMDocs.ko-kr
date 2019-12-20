---
title: BitLocker 이벤트 로그
titleSuffix: Configuration Manager
description: Windows 이벤트 로그에서 BitLocker 정보를 사용 하 여 문제를 해결 하는 방법에 대해 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: a9ece9e8-37ec-441d-937c-be4941afce7f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 813975c200a281445a6fe24b9036216174acf393
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74662341"
---
# <a name="bitlocker-event-logs"></a>BitLocker 이벤트 로그

*적용 대상: Configuration Manager (현재 분기)*

BitLocker 관리 에이전트 및 웹 서비스는 Windows 이벤트 로그를 사용 하 여 메시지를 기록 합니다. 이벤트 뷰어에서 **응용 프로그램 및 서비스 로그**, **Microsoft**, **Windows**로 이동 합니다. 로그 채널 (노드)은 컴퓨터 및 구성 요소에 따라 다릅니다.

- **Mbam**: 클라이언트 컴퓨터의 BitLocker 관리 에이전트
- **Mbam-웹**:
  - 관리 지점의 복구 서비스
  - 셀프 서비스 포털
  - 웹 사이트 관리 및 모니터링

이러한 로그의 특정 메시지에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [클라이언트 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/client-event-logs)
- [서버 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/server-event-logs)

기본적으로 각 노드에는 **관리자** 와 **운영**이라는 두 개의 로그 채널이 표시 됩니다. 자세한 문제 해결 정보를 보려면 [분석 및 디버그 로그](#bkmk_debug)를 표시할 수도 있습니다.

## <a name="log-properties"></a>로그 속성

Windows 이벤트 뷰어에서 특정 로그를 선택 합니다. 예를 들어 관리자**를 **합니다. **작업** 메뉴로 이동 하 여 **속성**를 선택 합니다. 다음 설정을 구성합니다.

- **최대 로그 크기 (KB)** : 기본적으로이 설정은 모든 로그에 대해 `1028` (1mb)입니다.
- **최대 이벤트 로그 크기에 도달 하면**기본적으로 **관리** 및 **작업** 로그가 **필요에 따라 이벤트를 덮어쓰도록 설정 됩니다 (가장 오래 된 이벤트 먼저)** .

## <a name="bkmk_debug"></a> 분석 및 디버그 로그

문제 해결을 위해 자세한 로그를 사용 하도록 설정할 수 있습니다. 이벤트 뷰어에서 **보기** 메뉴로 이동 하 고 **분석 및 디버그 로그 표시**를 선택 합니다. 이제 로그 채널을 찾으면 **분석** 및 **디버그**라는 두 개의 추가 로그가 표시 됩니다.

> [!TIP]
> 기본적으로 이러한 로그에는 다음과 같은 속성이 있습니다.
>
> - **최대 로그 크기 (KB)** : `1028` (1mb)
> - **이벤트 덮어쓰지 않음(수동으로 로그 지우기)**

## <a name="export-logs-to-text"></a>로그를 텍스트로 내보내기

특히 [분석 및 디버그 로그](#bkmk_debug)를 사용 하 여 로그 항목을 한 텍스트 파일에 쉽게 검토할 수 있습니다. 다음 PowerShell 명령을 사용 하 여 이벤트 로그 항목을 텍스트 파일로 내보냅니다.

``` PowerShell
# Out-String with a larger -Width does a better job compared to using Out-File with -Width. -Oldest is only required with debug/analytic logs.

# Debug log
Get-WinEvent -LogName Microsoft-Windows-MBAM/Debug -Oldest | Format-Table -AutoSize | Out-String -Width 4096 | Out-File C:\Temp\MBAM_Log_Debug.txt

# Analytic log
Get-WinEvent -LogName Microsoft-Windows-MBAM/Analytic -Oldest | Format-Table -AutoSize | Out-String -Width 4096 | Out-File C:\Temp\MBAM_Log_Analytic.txt

# Admin log
# The above command truncates the output from the admin log, this sample reformats the strings
Get-WinEvent -LogName Microsoft-Windows-MBAM/Admin |
    Select TimeCreated, LevelDisplayName, TaskDisplayName, @{n='Message';e={$_.Message.trim()}} |
    Format-Table -AutoSize -Wrap | Out-String -Width 4096 |
    Out-File -FilePath C:\Temp\MBAM_Log_Admin.txt
```
