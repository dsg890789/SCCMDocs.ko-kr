---
title: "Windows 컴퓨터 원격 관리 | System Center Configuration Manager"
description: "System Center Configuration Manager를 사용하여 원격 Windows 클라이언트 컴퓨터를 관리합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
caps.latest.revision: 5
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 02c11420d3b05ad4eaae31d9413b66459751da70
ms.openlocfilehash: 51a9b7269993bfa133382b88792ac94032824eed


---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 절차를 사용하여 System Center Configuration Manager에서 컴퓨터를 원격으로 관리합니다.  

 원격 제어를 사용하기 전에 다음 항목 정보를 검토해야 합니다.  

-   [System Center Configuration Manager에서 원격 제어에 대한 필수 조건](../../../../core/clients/manage/remote-control/prerequisites-for-remote-control.md)  

-   [System Center Configuration Manager에서 원격 제어 구성](../../../../core/clients/manage/remote-control/configuring-remote-control.md)  

 세 가지 방법 중 하나를 사용하여 Configuration Manager 원격 제어 뷰어를 시작할 수 있습니다.  

-   Configuration Manager 콘솔을 사용하여  

-   Windows 명령 프롬프트에서  

-   **Microsoft System Center 2012** 프로그램 그룹에서 Configuration Manager 콘솔을 실행하는 컴퓨터의 Windows **시작** 메뉴에서  

### <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 클라이언트 컴퓨터를 원격으로 관리하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **장치** 또는 **장치 컬렉션**을 클릭합니다.  

3.  원격으로 관리할 컴퓨터를 선택한 다음 **홈** 탭의 **장치** 그룹에서 **시작**을 클릭하고 **원격 제어**를 클릭합니다.  

    > [!IMPORTANT]  
    >  클라이언트 설정 **원격 제어 권한을 묻는 메시지를 사용자에게 표시** 가 **True**로 설정되어 있는 경우 원격 컴퓨터의 사용자가 원격 제어 프롬프트에 동의할 때까지 연결을 시작하지 않습니다. 자세한 내용은 [System Center Configuration Manager에서 원격 제어 구성](../../../../core/clients/manage/remote-control/configuring-remote-control.md)을 참조하세요.  

4.  **Configuration Manager 원격 제어** 창이 열린 후 클라이언트 컴퓨터를 원격으로 관리할 수 있습니다. 연결을 구성하려면 다음 옵션을 사용합니다.  

    > [!NOTE]  
    >  연결한 컴퓨터에 다중 모니터가 있으면 이러한 모든 모니터의 화면 표시가 원격 제어 창에 표시됩니다.  

    -   **파일 - 연결** – 다른 컴퓨터에 연결합니다. 원격 제어 세션이 활성화된 경우 이 옵션을 사용할 수 없습니다.  

    -   **파일 - 연결 끊기** – 활성화된 원격 제어 세션 연결을 끊지만 **Configuration Manager 원격 제어** 창을 닫지 않습니다.  

    -   **파일 - 종료** – 활성화된 원격 제어 세션의 연결을 끊고 **Configuration Manage 원격 제어** 창을 닫습니다.  

        > [!NOTE]  
        >  원격 제어 세션의 연결을 끊으면 보고 있는 컴퓨터에서 Windows 클립보드 내용이 삭제됩니다.  

    -   **보기 - 전체 화면** – **Configuration Manager 원격 제어** 창을 최대화하여 사용 가능한 모든 디스플레이 공간을 채웁니다.  

        > [!NOTE]  
        >  전체 화면 모드를 종료하려면 Ctrl+Alt+Break를 누릅니다.  

    -   **보기 - 크기 조정** - 원격 컴퓨터의 화면 표시를 **Configuration Manager 원격 제어** 창의 크기에 맞게 조정합니다.  

    -   **보기- 상태 표시줄** – **Configuration Manager 원격 제어** 창 상태 표시줄의 화면 표시를 전환합니다.  

    -   **작업 - Ctrl+Alt+Del 키 보내기** – Ctrl+Alt+Del 키 조합을 원격 컴퓨터로 보냅니다.  

    -   **작업 - 클립보드 공유 사용** - 항목을 원격 컴퓨터에서 복사하고 붙여넣을 수 있습니다. 이 값을 변경하는 경우 변경 사항이 적용되도록 원격 제어 세션을 다시 시작해야 합니다.  

        > [!NOTE]  
        >  Configuration Manager 콘솔에서 클립보드 공유를 사용하도록 설정하지 않으려면 콘솔을 실행하는 컴퓨터에서 레지스트리 키 값 **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard Sharing**을 **0**으로 설정합니다.  

    -   **작업 - 원격 키보드 및 마우스 잠금** – 사용자가 원격 컴퓨터로 작업할 수 없도록 원격 키보드 및 마우스를 잠급니다.  

    -   **도움말 - 원격 제어 정보** – 원격 제어 뷰어의 현재 버전에 대한 정보를 표시합니다.  

5.  원격 컴퓨터의 사용자가 Windows 알림 영역에서 Configuration Manager**원격 제어** 아이콘을 클릭하거나 원격 제어 세션 표시줄의 아이콘을 클릭하면 원격 제어 세션에 대한 자세한 내용을 볼 수 있습니다.  

6.  원격 제어 세션이 더 이상 필요하지 않으면 앞에서 설명한 메서드 중 하나를 사용하여 원격 제어 세션을 종료합니다.  

### <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>Windows 명령줄에서 원격 제어 뷰어를 시작하려면  

-   Windows 명령 프롬프트에 *<Configuration Manager 설치 폴더\>***\AdminConsole\Bin\x64\CmRcViewer.exe**를 입력합니다.  

    > [!NOTE]  
    >  CmRcViewer.exe에서 다음 명령줄 옵션을 지원합니다.  
    >   
    >  -   *<주소\>* - NetBIOS 이름, FQDN(정규화된 도메인 이름) 또는 연결할 클라이언트 컴퓨터의 IP 주소를 지정합니다.  
    > -   *<사이트 서버 이름\>* - 원격 제어 세션과 관련된 상태 메시지를 보낼 System Center 2012 Configuration Manager 사이트 서버의 이름을 지정합니다.  
    > -   **/?** – 원격 제어 뷰어에 대한 명령줄 옵션을 표시합니다.  
    >   
    >  **예:CmRcViewer.exe** *<주소\>* *<\\\사이트 서버 이름 >*  



<!--HONumber=Nov16_HO1-->


