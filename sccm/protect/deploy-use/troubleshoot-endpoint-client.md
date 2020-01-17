---
title: Endpoint Protection 문제 해결
titleSuffix: Configuration Manager
description: Windows Defender 및 Endpoint Protection 문제를 해결하는 방법을 알아봅니다.
ms.date: 09/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: d837253e-fcc2-422a-9e2c-c78b938dfd8c
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: c28fb1d8bad62f4aa84bb0d459579d97e4e0d28d
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75819406"
---
# <a name="troubleshoot-windows-defender-or-endpoint-protection-client"></a>Windows Defender 또는 Endpoint Protection 클라이언트 문제 해결

*적용 대상: Configuration Manager(현재 분기)*

Windows Defender 또는 Endpoint Protection 관련 된 문제가 발생 하는 경우이 문서를 참조 하 여 다음 문제를 해결 하십시오.  

- [Windows Defender 또는 Endpoint Protection 업데이트](#update-windows-defender-or-endpoint-protection)  
- [Windows Defender 또는 Endpoint Protection 서비스 시작](#starting-windows-defender-or-endpoint-protection-service)  
- [인터넷 연결 문제](#internet-connection-issues)  
- [수정할 수 없는 위협 감지](#detected-threat-cant-be-remediated)  

## <a name="update-windows-defender-or-endpoint-protection"></a>Windows Defender 또는 Endpoint Protection 업데이트

### <a name="symptoms"></a>증상

Windows Defender 또는 Endpoint Protection은 자동으로 Microsoft 업데이트와 함께 작동하여 바이러스 및 스파이웨어 정의를 최신 상태로 유지합니다.  

이 섹션에서는 다음과 같은 경우를 포함하여 자동 업데이트의 일반적인 문제를 설명합니다.  

- 업데이트가 실패했음을 나타내는 오류 메시지가 표시됩니다.  

- 업데이트를 확인할 때 바이러스 및 스파이웨어 정의 업데이트를 확인, 다운로드 또는 설치할 수 없다는 오류 메시지가 표시됩니다.  

- 디바이스가 인터넷에 연결된 경우에도 업데이트가 실패합니다.  

- 예약된 대로 업데이트가 자동으로 설치되지 않습니다.  

### <a name="causes"></a>원인

업데이트 문제의 가장 일반적인 원인은 인터넷 연결 문제입니다. 다른 웹 사이트는 찾아볼 수 있으므로 디바이스가 인터넷에 연결되어 있다는 사실이 확인되면 Windows의 설정과 충돌하는 것이 문제의 원인일 수 있습니다.  

### <a name="options-to-resolve"></a>해결할 옵션

#### <a name="step-1-reset-your-internet-settings"></a>1 단계: 인터넷 설정 다시 설정  

1. 웹 브라우저를 포함 하 여 열려 있는 모든 프로그램을 종료 합니다.  

    > [!NOTE]  
    > 이러한 인터넷 설정을 다시 설정 하는 경우 브라우저 임시 파일, 쿠키, 검색 기록 및 온라인 암호가 삭제 될 수 있습니다. 즐겨찾기를 삭제 하지 않습니다.  

2. **시작** 메뉴로 이동 하 여 `inetcpl.cpl`을 엽니다.  

3. **고급** 탭으로 전환 합니다.  

4. **Internet Explorer 설정 다시 설정**섹션에서 **다시 설정**을 선택 하 고 다시 **설정** 을 선택 하 여 확인 합니다.  

5. 설정이 다시 설정 되 면 **확인을** 선택 합니다.

6. Windows Defender를 다시 업데이트 해 보세요.

문제가 지속 되 면 다음 단계를 계속 합니다.  

#### <a name="step-2-make-sure-that-the-date-and-time-are-set-correctly-on-your-computer"></a>2단계: 컴퓨터의 날짜와 시간이 올바르게 설정되었는지 확인  

표시된 오류 메시지에 코드 0x80072f8f가 포함되어 있으면 컴퓨터의 잘못된 날짜 또는 시간 설정으로 인한 문제일 가능성이 큽니다. **시작** 메뉴로 이동 하 고 **설정**을 선택한 다음 **시간 & 언어**를 선택 하 고 **날짜 & 시간**을 선택 합니다.

#### <a name="step-3-rename-the-software-distribution-folder-on-your-computer"></a>3단계: 컴퓨터의 소프트웨어 배포 폴더 이름 바꾸기  

1. **Windows 업데이트** 서비스를 중지 합니다.  

    1. **시작**으로 이동 하 고 **services.msc**를 엽니다.  

    2. **Windows 업데이트** 서비스를 선택 합니다. **작업** 메뉴로 이동 하 고 **중지**를 선택 합니다.

2. **SoftwareDistribution** 디렉터리의 이름을 변경합니다.  

    1. 관리자 권한으로 명령 프롬프트를 엽니다.  

    2. 다음 명령을 입력합니다.

        ```cmd
        cd %windir%
        ren SoftwareDistribution SDTemp
        exit
        ```

3. **Windows 업데이트** 서비스를 다시 시작 합니다.

    1. **서비스** 창으로 다시 전환 합니다.  

    2. **Windows 업데이트** 서비스를 선택 합니다. **작업** 메뉴로 이동 하 고 **시작**을 선택 합니다.

    3. 서비스 창을 닫습니다.  

#### <a name="step-4-reset-the-microsoft-antivirus-update-engine-on-your-computer"></a>4단계: 컴퓨터의 Microsoft 바이러스 백신 업데이트 엔진 재설정  

1. 관리자 권한으로 명령 프롬프트를 엽니다.

2. 다음 명령을 입력합니다.

    ```cmd
    cd \

    cd program files\windows defender

    MpCmdRun -RemoveDefinitions -all

    exit
    ```

3. 컴퓨터를 다시 시작하십시오.  

4. Windows Defender를 다시 업데이트 해 보세요.

문제가 지속 되 면 다음 단계를 계속 합니다.  

#### <a name="step-5-manually-install-the-definition-updates"></a>5 단계: 정의 업데이트 수동 설치  

[최신 업데이트를 수동으로 다운로드](https://www.microsoft.com/en-us/wdsi/defenderupdates)합니다.  

#### <a name="step-6-contact-microsoft-support"></a>6단계: Microsoft 지원에 문의  

이러한 단계를 수행 해도 문제가 해결 되지 않으면 Microsoft 지원에 문의 하세요. 자세한 내용은 [지원 옵션 및 커뮤니티 리소스](/sccm/core/understand/find-help#BKMK_SupportOptions)를 참조 하세요.  

## <a name="starting-windows-defender-or-endpoint-protection-service"></a>Windows Defender 또는 Endpoint Protection 서비스 시작

### <a name="symptom"></a>증상

프로그램 서비스가 중지되어 **Windows Defender 또는 Endpoint Protection에서 컴퓨터를 모니터링하고 있지 않습니다. 지금 다시 시작해야 합니다.** 라는 메시지가 표시됩니다.

### <a name="solution"></a>솔루션

#### <a name="step-1-restart-your-computer"></a>1단계: 컴퓨터 다시 시작

모든 애플리케이션을 종료한 후 컴퓨터를 다시 시작합니다.  

#### <a name="step-2-check-the-windows-service"></a>2 단계: Windows 서비스 확인

1. **시작**으로 이동 하 고 **services.msc**를 엽니다.  

2. **Windows Defender 바이러스 백신 서비스**를 선택 합니다.  

3. **시작 유형**이 **자동**으로 설정되어 있는지 확인합니다.

4. **작업** 메뉴로 이동 하 여 **시작**을 선택 합니다.

    1. 이 작업을 사용할 수 없는 경우 **중지**를 선택 합니다. 서비스가 중지 될 때까지 기다린 다음 **시작** 작업을 선택 하 여 서비스를 다시 시작 합니다.  

이 프로세스 중에 나타날 수 있는 모든 오류를 확인 합니다. [Microsoft 지원에 문의](/sccm/core/understand/find-help#BKMK_SupportOptions) 하 여 오류 정보를 제공 합니다.  

#### <a name="step-3-remove-any-third-party-security-programs"></a>3 단계: 타사 보안 프로그램 제거  

> [!NOTE]  
> 일부 보안 응용 프로그램은 완전히 제거 되지 않습니다. 정리 유틸리티를 다운로드하여 실행하면 기존 보안 애플리케이션을 완전히 제거할 수 있습니다.  

1. **시작** 으로 이동 하 고 **appwiz.cpl**을 엽니다.  

2. 설치된 프로그램 목록에서 타사 보안 프로그램을 모두 제거합니다.

3. 컴퓨터를 다시 시작합니다.  

> [!CAUTION]  
> 보안 프로그램을 제거하면 컴퓨터는 비보호 상태가 됩니다. 기존 보안 프로그램을 제거한 후 Windows Defender를 설치 하는 데 문제가 있는 경우 [Microsoft 지원](https://support.microsoft.com/supportforbusiness/productselection)에 문의 하십시오. **보안** 제품군을 선택 하 고 **Windows Defender** 제품을 선택 합니다.

## <a name="internet-connection-issues"></a>인터넷 연결 문제

컴퓨터가 Windows 업데이트에서 최신 업데이트를 받으려면 인터넷에 연결 합니다.  

1. **시작** 으로 이동 하 여 **ncpa.cpl**을 엽니다.  

2. 연결 **상태**를 보려면 연결 이름을 엽니다.  

3. 컴퓨터가 연결 된 경우 **IPv4 연결** 및/또는 **IPv6 연결** 상태는 **인터넷**입니다.  

4. 컴퓨터가 연결 되지 않은 것으로 표시 되 면 연결 이름을 선택 하 고 **이 연결 진단**을 선택 합니다.

열려 있는 모든 프로그램을 닫고 컴퓨터를 다시 시작합니다.  

## <a name="detected-threat-cant-be-remediated"></a>재구성할 수 없는 위협 감지

Windows Defender 또는 Endpoint Protection에서 잠재적인 위협을 발견 하면 위협을 격리 하거나 제거 하 여 위협을 완화 하려고 시도 합니다. 이러한 위협은 압축 된 보관 파일 (`.zip`) 또는 네트워크 공유 내에서 숨길 수 있습니다.

### <a name="remove-or-scan-the-file"></a>파일 제거 또는 검사  

- 압축 된 보관 파일에서 위협이 검색 된 경우 해당 파일을 찾습니다. 파일을 삭제 하거나 수동으로 스캔 합니다. 파일을 마우스 오른쪽 단추로 클릭 하 고 **Windows Defender를 사용 하 여 검사**를 선택 합니다. Windows Defender가 파일에서 추가 위협을 검색 하면이를 알려 줍니다. 그런 다음 적절 한 작업을 선택할 수 있습니다.  

- 네트워크 공유에서 위협이 검색 된 경우 공유를 열고 수동으로 검사 합니다. 파일을 마우스 오른쪽 단추로 클릭 하 고 **Windows Defender를 사용 하 여 검사**를 선택 합니다. 네트워크 공유에서 추가 위협을 검색 하면 Windows Defender에서 사용자에 게 알립니다. 그런 다음 적절 한 작업을 선택할 수 있습니다.  

- 파일의 원본을 잘 모르겠으면 컴퓨터에서 전체 검색을 실행 합니다. 전체 검사를 완료 하는 데 다소 시간이 걸릴 수 있습니다.  

## <a name="see-also"></a>참고 항목

[Endpoint Protection 클라이언트에 대한 질문과 대답](/sccm/protect/deploy-use/endpoint-protection-client-faq)

[Endpoint Protection 클라이언트 도움말](/sccm/protect/deploy-use/endpoint-protection-client-help)
