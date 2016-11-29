---
title: "Windows Defender 또는 Endpoint Protection 클라이언트 문제 해결 | System Center Configuration Manager"
description: "Windows Defender 및 Endpoint Protection 문제를 해결하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d837253e-fcc2-422a-9e2c-c78b938dfd8c
caps.latest.revision: 7
caps.handback.revision: 0
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 4d30cd85cb59f8f27704979074470bb06310054b


---
# <a name="troubleshooting-windows-defender-or-endpoint-protection-client"></a>Windows Defender 또는 Endpoint Protection 클라이언트 문제 해결

*적용 대상: System Center Configuration Manager(현재 분기)*


Windows Defender 또는 Endpoint Protection에 문제가 발생하면 보안 관리자에게 지원을 문의합니다. 다음 문제 해결을 시도할 수도 있습니다.  

-   [Endpoint Protection 클라이언트 설치](#install-the-endpoint-protection-client)  

-   [Windows Defender 또는 Endpoint Protection 업데이트](#update-windows-defender-or-endpoint-protection)  

-   [Windows Defender 또는 Endpoint Protection 서비스 시작](#starting-windows-defender-or-endpoint-protection-service)  

-   [인터넷 연결 문제](#internet-connection-issues)  

-   [수정할 수 없는 위협 감지](#detected-threat-cant-be-remediated)  

##  <a name="install-the-endpoint-protection-client"></a>Endpoint Protection 클라이언트 설치  

> [!NOTE]  
>  Windows Defender는 Windows 10 PC의 운영 체제에 설치됩니다.  

 **증상**  

 알 수 없는 이유로 설치에 실패하거나 오류 코드와 함께 오류 메시지가 표시됩니다. 오류 코드의 예는 0x80070643, 0X8007064A, 0x8004FF2E, 0x8004FF01, 0x8004FF07, 0x80070002, 0x8007064C, 0x8004FF00, 0x80070001, 0x80070656, 0x8004FF40, 0xC0000156, 0x8004FF41 0x8004FF0B, 0x8004FF11, 0x80240022, 0x8004FF04, 0x80070660, 0x800106B5, 0x80070715, 0x80070005, 0x8004EE00, 0x8007003, 0x800B0100, 0x8007064E, 0x8007007E 등입니다.  

 컴퓨터에서 Windows XP SP2(서비스 팩 2)를 실행 중인 경우 다음과 같은 오류 메시지가 하나 이상 표시될 수 있습니다.  

-   설치 마법사에 설치하는 데 필요한 필터 관리자 롤업 패키지가 없습니다.  

-   KB914882 설치 오류, 시스템에 설치된 언어가 업데이트 언어와 다르므로 Windows XP 파일을 업데이트할 수 없습니다.  

 **원인**  

 다른 보안 프로그램을 실행 중인 컴퓨터에는 Endpoint Protection을 설치할 수 없습니다. 다른 보안 프로그램을 제거해도 완전히 제거되지 않는 경우가 있습니다. Endpoint Protection을 설치하려면 정품 Windows 운영 체제를 사용해야 합니다.  

 **해결 방법**  

> [!IMPORTANT]  
>  이 문제를 해결하는 동안 컴퓨터를 다시 시작해야 할 수 있으므로, 이 항목을 쉽게 다시 찾을 수 있도록 이 페이지를 즐겨찾기에 추가하거나 인쇄하여 참고하십시오.  

### <a name="step-1-remove-any-existing-security-programs"></a>1단계: 기존 보안 프로그램 제거  

1.  기존 인터넷 보안 프로그램을 완전히 제거합니다.  

2.  컴퓨터를 다시 시작합니다.  

3.  Endpoint Protection을 다시 설치합니다. 위에 나와 있는 방법으로 문제가 해결되지 않을 경우 다음 단계를 수행합니다.  

### <a name="step-2-ensure-that-the-windows-installer-service-is-running"></a>2단계: Windows Installer 서비스가 실행 중인지 확인  

1.  **시작** 을 클릭하고 **services.msc**를 검색한 후 **Enter**키를 누릅니다.  

2.  **Windows Installer**를 마우스 오른쪽 단추로 클릭한 후 **시작**을 클릭합니다. **시작** 은 표시되지 않고 **중지** 및 **다시 시작** 옵션이 표시되면 서비스가 이미 시작되었음을 나타냅니다.  

3.  **서비스** 페이지의 **파일** 메뉴에서 **끝내기**를 클릭합니다.  

4.  **시작**을 클릭합니다. **프로그램 및 파일 검색** 상자에서 **명령 프롬프트**를 입력합니다. **명령 프롬프트**를 마우스 오른쪽 단추로 클릭하고 **관리자 권한으로 실행**을 클릭합니다.  

5.  **MSIEXEC /REGSERVER**를 입력한 후 **Enter**키를 누릅니다.  

    > [!NOTE]  
    >  이 명령의 실행 성공 여부를 알려 주는 메시지는 제공되지 않습니다.  

6.  Endpoint Protection을 다시 설치합니다. 위에 나와 있는 방법으로 문제가 해결되지 않을 경우 다음 단계를 수행합니다.  

### <a name="step-3-start-windows-in-selective-startup-mode"></a>3단계: 선택 모드로 Windows 시작  

1.  **시작** 을 클릭하고 **msconfig**를 검색한 후 **Enter**키를 누릅니다.  

2.  **일반** 탭에서 **선택 모드**를 클릭한 후 **시작 항목 로드** 확인란의 선택을 취소합니다.  

3.  **서비스** 탭에서 **모든 Microsoft 서비스 숨기기** 확인란을 선택한 후 목록에 남아 있는 서비스의 모든 확인란 선택을 취소합니다.  

4.  **확인**을 클릭한 후 **다시 시작** 을 클릭하여 컴퓨터를 다시 시작합니다.  

5.  Endpoint Protection을 다시 설치합니다.  

##  <a name="update-windows-defender-or-endpoint-protection"></a>Windows Defender 또는 Endpoint Protection 업데이트  
 Windows Defender 또는  
      Endpoint Protection은 자동으로 Microsoft 업데이트와 함께 작동하여 바이러스 및 스파이웨어 정의를 최신 상태로 유지합니다.  

 **증상**  

 이 문서에서는 다음과 같은 경우를 포함하여 자동 업데이트의 일반적인 문제를 설명합니다.  

-   업데이트가 실패했음을 나타내는 오류 메시지가 표시됩니다.  

-   업데이트를 확인할 때 바이러스 및 스파이웨어 정의 업데이트를 확인, 다운로드 또는 설치할 수 없다는 오류 메시지가 표시됩니다.  

-   인터넷에 연결된 경우에도 업데이트가 실패합니다.  

-   예약된 대로 업데이트가 자동으로 설치되지 않습니다.  

 **원인**  

 업데이트 문제의 가장 일반적인 원인은 인터넷 연결 문제입니다. 그러나 다른 웹 사이트는 찾아볼 수 있으므로 인터넷에 연결되어 있다는 사실이 확인되면 Windows Internet Explorer의 설정과 충돌하는 것이 문제의 원인일 수 있습니다.  

> [!IMPORTANT]  
>  이러한 단계를 완료하려면 Internet Explorer를 종료해야 합니다. 따라서 내용을 인쇄하거나 적어두거나 다른 파일에 복사한 후 나중에 액세스할 수 있도록 이 항목에 책갈피를 지정합니다.  

### <a name="step-1-reset-your-internet-explorer-settings"></a>1단계: Internet Explorer 설정 복원  

1.  Internet Explorer를 포함하여 열려 있는 모든 프로그램을 종료합니다.  

    > [!NOTE]  
    >  Internet Explorer에서 이러한 설정을 복원하면 임시 파일, 쿠키, 검색 기록 및 온라인 암호가 삭제됩니다. 하지만 즐겨찾기는 삭제되지 않습니다.  

2.  **시작** 을 클릭하고 **inetcpl.cpl**을 검색한 후 **Enter**키를 누릅니다.  

3.  **인터넷 옵션** 대화 상자에서 **고급** 탭을 클릭합니다.  

4.  **Internet Explorer 기본 설정 복원**에서 **다시 설정**을 클릭하고 **다시 설정** 을 다시 클릭합니다.  

5.  Internet Explorer의 설정을 복원이 끝날 때까지 기다린 후 **확인**을 클릭합니다.  

6.  Internet Explorer를 엽니다.  

7.  Microsoft Security Essentials를 열고 **업데이트** 탭을 클릭한 후 **업데이트**를 클릭합니다.  

8.  문제가 지속되면 다음 단계를 계속 진행합니다.  

### <a name="step-2-set-internet-explorer-as-the-default-browser"></a>2단계: Internet Explorer를 기본 브라우저로 설정  

1.  Internet Explorer를 포함하여 열려 있는 모든 프로그램을 종료합니다.  

2.  **시작** 을 클릭하고 **inetcpl.cpl**을 검색한 후 **Enter**키를 누릅니다.  

3.  **인터넷 옵션** 대화 상자에서 **프로그램** 탭을 클릭합니다.  

4.  **기본 웹 브라우저**에서 **기본 웹 브라우저로 설정**을 클릭합니다.  

5.  **확인**을 클릭합니다.  

6.  Windows Defender 또는  
          끝점 보호 **업데이트** 탭을 클릭한 다음 **업데이트**를 클릭합니다.  

7.  문제가 지속되면 다음 단계를 계속 진행합니다.  

### <a name="step-3-ensure-that-the-date-and-time-are-set-correctly-on-your-computer"></a>3단계: 컴퓨터의 날짜와 시간이 올바르게 설정되었는지 확인  

1.  Windows Defender 또는  
          끝점 보호  

2.  표시된 오류 메시지에 코드 0x80072f8f가 포함되어 있으면 컴퓨터의 잘못된 날짜 또는 시간 설정으로 인한 문제일 가능성이 큽니다.  

3.  컴퓨터의 날짜 또는 시간 설정을 복원하려면 [잘못된 바탕 화면 바로 가기 및 일반 시스템 유지 관리 작업 수정](http://go.microsoft.com/fwlink/?LinkId=155579) (http://go.microsoft.com/fwlink/?LinkId=155579)의 단계를 따르세요.  

### <a name="step-4-rename-the-software-distribution-folder-on-your-computer"></a>4단계: 컴퓨터의 소프트웨어 배포 폴더 이름 바꾸기  

1. 자동 업데이트 서비스 중지  

    1.  **시작** 을 클릭하고 **services.msc**을 검색한 후 **확인**을 클릭합니다.  

    2.  **자동 업데이트 서비스**를 마우스 오른쪽 단추로 클릭하고 **중지**를 클릭합니다.  

    3.  서비스 스냅인을 최소화합니다.  

2.  **SoftwareDistribution** 디렉터리의 이름을 다음과 같이 바꿉니다.  

    1.  **시작** 을 클릭하고  **cmd**을 검색한 후 **확인**을 클릭합니다.  

    2.  **cd %windir%**을 입력한 다음 **Enter**키를 누릅니다.  

    3.  **ren SoftwareDistribution SDTemp**을 입력한 다음 **Enter**키를 누릅니다.  

    4.  **exit**을 입력한 다음 **Enter**키를 누릅니다.  

3.  다음과 같이 자동 업데이트 서비스를 시작합니다.  

    1.  서비스 스냅인을 최대화합니다.  

    2.  **자동 업데이트 서비스**를 마우스 오른쪽 단추로 클릭하고 **시작**을 클릭합니다.  

    3.  서비스 스냅인 창을 닫습니다.  

### <a name="step-5-reset-the-microsoft-antivirus-update-engine-on-your-computer"></a>5단계: 컴퓨터의 Microsoft 바이러스 백신 업데이트 엔진 복원  

1.  **시작** 을 클릭하고  **cmd**를 검색한 후 **확인**을 클릭하고 **명령 프롬프트**를 마우스 오른쪽 단추로 클릭한 다음 **관리자 권한으로 실행**을 선택합니다.  

2.  **명령 프롬프트** 창에서 다음 명령을 입력하고 각 명령 다음에 **Enter** 키를 누릅니다.  

     **Cd\\**  

     **Cd program files\microsoft security essentials**  

     **Mpcmdrun -removedefinitions -all**  

     **끝내기**  

3.  컴퓨터를 다시 시작합니다.  

4.  Windows Defender 또는  
          Endpoint Protection을 열고 **업데이트** 탭을 클릭한 후 **업데이트**를 클릭합니다.  

5.  문제가 지속되면 다음 단계를 계속 진행합니다.  

### <a name="step-6-manually-install-the-virus-and-spyware-definition-updates"></a>6단계: 바이러스 및 스파이웨어 정의 업데이트를 수동으로 설치  

-   32비트 Windows 운영 체제를 실행하는 경우 [http://go.microsoft.com/fwlink/?LinkID=87342](http://go.microsoft.com/fwlink/?LinkID=87342) (http://go.microsoft.com/fwlink/?LinkID=87342)에서 수동으로 최신 업데이트를 다운로드합니다.  

-   64비트 Windows 운영 체제를 실행하는 경우 [http://go.microsoft.com/fwlink/?LinkID=87341](http://go.microsoft.com/fwlink/?LinkID=87341) (http://go.microsoft.com/fwlink/?LinkID=87341)에서 수동으로 최신 업데이트를 다운로드합니다.  

-   **실행**을 클릭합니다. 최신 업데이트가 수동으로 컴퓨터에 설치됩니다.  


### <a name="step-7-contact-support"></a>7단계: 지원 사이트에 문의  

-   해당 단계로 문제가 해결되지 않으면 지원 서비스에 문의합니다. 자세한 내용은 [고객지원](http://go.microsoft.com/fwlink/?LinkID=196174) (http://go.microsoft.com/fwlink/?LinkID=196174)을 참조하세요.  

##  <a name="starting-windows-defender-or-endpoint-protection-service"></a>Windows Defender 또는 Endpoint Protection 서비스 시작  
 **증상**  

 **프로그램 서비스가 중지되어 Windows Defender 또는**  
 **Endpoint Protection에서 컴퓨터를 모니터링하고 있지 않습니다. 지금 다시 시작해야 합니다.**"라는 메시지가 표시됩니다.  

 **해결 방법**  

### <a name="step-1-restart-your-computer"></a>1단계: 컴퓨터 다시 시작  

-   모든 응용 프로그램을 종료한 후 컴퓨터를 다시 시작합니다.  

### <a name="step-2-make-sure-the-windows-defender-orbr-endpoint-protection-service-is-set-to-automatic-and-is-started"></a>2단계: "Windows Defender" 또는<br />      "Endpoint Protection" 서비스가 자동으로 설정되고 시작되었는지 확인  

1.  **시작** 을 클릭하고 **services.msc**를 검색한 후 **Enter**키를 누릅니다.  

2.  **Microsoft Antimalware Service**를 검색한 후 마우스 오른쪽 단추를 클릭하여 **속성** 을 선택하거나 두 번 클릭하여 서비스를 엽니다.  

3.  "**시작 유형**"이 "**자동**"으로 설정되어 있는지 확인합니다.  

4.  **시작** 단추를 클릭하여 서비스를 시작합니다. **시작** 단추가 표시되지 않으면 **중지** 단추를 클릭한 후 **시작** 단추를 클릭하여 서비스를 다시 시작합니다.  

5.  이 과정에서 오류가 발생할 경우 오류 정보와 함께 온라인으로 지원 양식을 전송하여 문의하시기 바랍니다.  

### <a name="step-3-remove-any-existing-internet-security-programs"></a>3단계: 기존 인터넷 보안 프로그램 제거  

1.  **시작** 을 클릭하고 **appwiz.cpl**을 검색한 후 **Enter**키를 누릅니다.  

2.  설치된 프로그램 목록에서 타사 인터넷 보안 프로그램을 모두 제거합니다.*  

3.  컴퓨터를 다시 시작하고 Windows Defender 또는  
          Endpoint Protection을 다시 설치해 보세요.  

> [!NOTE]  
>  일부 인터넷 보안 응용 프로그램은 완전히 제거되지 않습니다. 정리 유틸리티를 다운로드하여 실행하면 기존 보안 응용 프로그램을 완전히 제거할 수 있습니다.  

> [!CAUTION]  
>  인터넷 보안 프로그램을 제거하면 컴퓨터는 비보호 상태가 됩니다. 기존 인터넷 보안 프로그램을 제거한 후 Endpoint Protection을 설치하는 데 문제가 있는 경우   
>       온라인으로 사례를 제출하여 Windows Defender 또는  
>       Endpoint Protection 지원 담당자에게 문의하세요(자세한 내용은 [온라인으로 사례를 제출하는 방법](http://www.microsoft.com/en-ph/security_essentials/Support/8c9074b6-1558-4d14-bc39-d294ced11096.aspx) 참조).  

### <a name="step-4-uninstallreinstall-endpoint-protection"></a>4단계: Endpoint Protection 제거/다시 설치  

1.  **시작** 을 클릭하고 **appwiz.cpl**을 검색한 후 **Enter**키를 누릅니다.  

2.  설치된 프로그램 목록에서 **Endpoint Protection**을 클릭하고 제거합니다.  

3.  메시지가 표시되면 컴퓨터를 다시 시작한 후 Endpoint Protection을 다시 설치합니다.  

##  <a name="internet-connection-issues"></a>인터넷 연결 문제  
 컴퓨터에 Windows 업데이트의 최신 업데이트가 수신되도록 하려면 인터넷에 연결되어 있어야 합니다.  

### <a name="step-1-verify-that-your-computer-is-connected-to-the-internet"></a>1단계: 컴퓨터가 인터넷에 연결되었는지 확인  

1.  **시작**을 클릭하고 **ncpa.cpl**을 검색한 후 **Enter**키를 누릅니다.  

2.  연결 이름을 마우스 오른쪽 단추로 클릭하고 **상태**를 클릭합니다.  

3.  컴퓨터가 연결된 경우 Windows XP에서 연결 상태는 **연결됨**, **사용**또는 **인증** 성공으로 표시됩니다. Windows Vista 및 Windows 7에서 **IPv4** 상태는 **인터넷**으로 표시됩니다.  

4.  컴퓨터가 연결되지 않은 것으로 표시되면 연결 이름을 마우스 오른쪽 단추로 클릭하고 **연결**, **사용**, **인증**또는 **복구**를 클릭합니다.  

### <a name="step-3-restart-your-computer"></a>3단계: 컴퓨터 다시 시작  

-   열려 있는 모든 프로그램을 닫고 컴퓨터를 다시 시작합니다.  

### <a name="step-4-if-you-still-cant-connect-to-the-internet-check-your-connections"></a>4단계: 여전히 인터넷에 연결할 수 없는 경우 연결 확인  

1.  전화 접속 연결을 사용하는 경우 벽면 잭과 모뎀의 전화선 연결에 문제가 없는지 확인합니다.  

2.  케이블 모뎀을 사용하는 경우 모뎀으로의 케이블 연결과 모뎀과 컴퓨터 간의 연결에 문제가 없는지 확인합니다.  

3.  케이블 모뎀 또는 DSL 라우터를 사용하는 경우 라우터 및 컴퓨터에 대한 연결에 문제가 없는지 확인합니다. 라우터 및 모뎀을 뽑은 후 끕니다. 잠시 기다렸다가 먼저 모뎀을 꽂고, 1분 정도 기다렸다가 라우터를 꽂은 후 컴퓨터를 다시 시작합니다.  

##  <a name="detected-threat-cant-be-remediated"></a>재구성할 수 없는 위협 감지  
 Windows Defender 또는  
      Endpoint Protection에서 .zip 파일 확장자의 압축 파일 또는 네트워크 공유 파일에 숨어 있는 잠재적인 위협을 검색하면 이 위협을 격리하거나 제거하는 방법으로 처리하려고 합니다.  

### <a name="remove-or-scan-the-file"></a>파일 제거 또는 검사  

-   .zip 파일에서 위협이 검색된 경우 해당 파일을 찾아 제거하거나 마우스 오른쪽 단추로 파일을 클릭한 후 **Windows Defender를 사용하여 검사** 또는 **Endpoint Protection을 사용하여 검사**를 선택하여 파일을 검사합니다. 해당 파일에서 추가 위협을 검색하면 Windows Defender 또는 Endpoint Protection에서 사용자가 적절한 조치를 선택할 수 있도록 이에 대한 알림을 표시합니다.  

-   네트워크 공유 파일에서 위협이 검색된 경우 해당 파일을 찾아 마우스 오른쪽 단추로 클릭한 후 **Windows Defender를 사용하여 검사** 또는 **Endpoint Protection을 사용하여 검사**를 선택하여 파일을 검사합니다. 네트워크 공유 파일에서 추가 위협을 검색하면 Windows Defender 또는 Endpoint Protection에서 사용자가 적절한 조치를 선택할 수 있도록 이에 대한 알림을 표시합니다.  

-   파일의 출처가 확실하지 않을 경우 컴퓨터에 대한 전체 검사를 실행하는 것이 가장 좋습니다. 전체 검사를 완료하려면 다소 시간이 소요되지만 Windows Defender 또는 Endpoint Protection에서 감염된 파일의 출처를 찾아 치료할 수 있습니다.  

### <a name="see-also"></a>참고 항목  
 [Endpoint Protection 클라이언트에 대한 질문과 대답](../../protect/deploy-use/endpoint-protection-client-faq.md)   

 [Endpoint Protection 클라이언트 도움말](../../protect/deploy-use/endpoint-protection-client-help.md)



<!--HONumber=Nov16_HO1-->


