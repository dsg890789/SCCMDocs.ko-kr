---
title: Windows 컴퓨터 원격 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 원격 Windows 클라이언트 컴퓨터를 관리합니다.
ms.date: 11/02/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 3c9648c4-645e-4e47-ae10-2da817b8c83b
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8223577eb5ca5daf70a1eaefe815b386ea2934cf
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73623450"
---
# <a name="how-to-remotely-administer-a-windows-client-computer-by-using-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)* Configuration Manager에서는 **Configuration Manager 원격 제어**를 사용하여 클라이언트 컴퓨터에 연결할 수 있습니다. 원격 제어를 사용하기 전에 다음 문서의 정보를 검토해야 합니다.  

-   [System Center Configuration Manager에서 원격 제어에 대한 필수 조건](/sccm/core/clients/manage/remote-control/prerequisites-for-remote-control)  

-   [System Center Configuration Manager에서 원격 제어 구성](/sccm/core/clients/manage/remote-control/configuring-remote-control)  

원격 제어 뷰어를 시작하는 세 가지 방법은 다음과 같습니다.  

-   Configuration Manager 콘솔에서.  

-   Windows 명령 프롬프트에서.  

-   **Microsoft System Center** 프로그램 그룹에서 Configuration Manager 콘솔을 실행하는 컴퓨터의 Windows **시작** 메뉴에서.  

## <a name="to-remotely-administer-a-client-computer-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 클라이언트 컴퓨터를 원격으로 관리하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성** > **디바이스** 또는 **디바이스 컬렉션**을 선택합니다.  

3.  원격으로 관리할 컴퓨터를 선택한 다음 **홈** 탭의 **디바이스** 그룹에서 **시작** > **원격 제어**를 선택합니다.  

    > [!IMPORTANT]  
    >  클라이언트 설정 **원격 제어 권한을 묻는 메시지를 사용자에게 표시** 가 **True**로 설정되어 있는 경우 원격 컴퓨터의 사용자가 원격 제어 프롬프트에 동의할 때까지 연결을 시작하지 않습니다. 자세한 내용은 [System Center Configuration Manager에서 원격 제어 구성](/sccm/core/clients/manage/remote-control/configuring-remote-control)을 참조하세요.  

4.  **Configuration Manager 원격 제어** 창이 열린 후 클라이언트 컴퓨터를 원격으로 관리할 수 있습니다. 연결을 구성하려면 다음 옵션을 사용합니다.  

    > [!NOTE]  
    >  연결한 컴퓨터에 다중 모니터가 있으면 이러한 모든 모니터의 화면 표시가 원격 제어 창에 표시됩니다.  

    -   **File**
        - **연결** – 다른 컴퓨터에 연결합니다. 원격 제어 세션이 활성화된 경우 이 옵션을 사용할 수 없습니다.  
        -   **연결 끊기** – 활성화된 원격 제어 세션의 연결을 끊지만 **Configuration Manager 원격 제어** 창을 닫지 않습니다.  
        - **종료** – 활성화된 원격 제어 세션의 연결을 끊고 **Configuration Manager 원격 제어** 창을 닫습니다.  

        > [!NOTE]  
        >  원격 제어 세션의 연결을 끊으면 보고 있는 컴퓨터에서 Windows 클립보드 내용이 삭제됩니다.


    - **보기**
      - **색 깊이** - 픽셀당 16비트 또는 32비트를 선택합니다.
      -  **전체 화면** – **Configuration Manager 원격 제어** 창을 최대화합니다. 전체 화면 모드를 종료하려면 Ctrl+Alt+Break를 누릅니다.  
      - **저대역폭 연결에 맞게 최적화** - 연결이 낮은 대역폭이면 이 옵션을 선택합니다.
      - **화면 표시:**
        - **모든 화면** - Configuration Manager 1902에 추가되었습니다. 연결한 컴퓨터에 다중 모니터가 있으면 이러한 모든 모니터의 화면 표시가 원격 제어 창에 표시됩니다. 1902 이전에는 **모든 화면**이 다중 모니터가 있는 컴퓨터의 유일한 뷰입니다.
        -  **첫 번째 화면** - Configuration Manager 1902에 추가되었습니다. *첫 번째 화면*은 Windows 디스플레이 설정에서 가장 왼쪽 상단에 표시되는 화면입니다. 특정 화면을 선택할 수는 없습니다. 뷰어의 구성을 변경한 후에는 원격 세션을 다시 연결해야 합니다. 이때부터 뷰어에 선택 사항이 저장됩니다.
        -  **크기 조정** - 원격 컴퓨터의 화면 표시를 **Configuration Manager 원격 제어** 창의 크기에 맞게 조정합니다.
        - **상태 표시줄** – **Configuration Manager 원격 제어** 창 상태 표시줄의 화면 표시를 전환합니다.  

       > [!NOTE]  
       >  이때부터 뷰어에 선택 사항이 저장됩니다.

    -   **작업**
        - **Ctrl+Alt+Del 키 보내기** – Ctrl+Alt+Del 키 조합을 원격 컴퓨터로 보냅니다. 
        - **클립보드 공유 사용** - 항목을 원격 컴퓨터에서 복사하고 붙여넣을 수 있습니다. 이 값을 변경하는 경우 변경 사항이 적용되도록 원격 제어 세션을 다시 시작해야 합니다.   
          - Configuration Manager 콘솔에서 클립보드 공유를 사용하도록 설정하지 않으려면 콘솔을 실행하는 컴퓨터에서 레지스트리 키 값 **HKEY_CURRENT_USER\Software\Microsoft\ConfigMgr10\Remote Control\Clipboard Sharing**을 **0**으로 설정합니다.
        - **키보드 변환 사용** - 콘솔을 실행하는 컴퓨터의 키보드 레이아웃을 연결된 디바이스의 레이아웃으로 변환합니다.
        - **원격 키보드 및 마우스 잠금** – 사용자가 원격 컴퓨터로 작업할 수 없도록 원격 키보드 및 마우스를 잠급니다.  

    -   **도움말**
        - **원격 제어 정보** – 뷰어의 현재 버전을 표시합니다.  

5.  원격 컴퓨터의 사용자가 Configuration Manager **원격 제어** 아이콘을 클릭하면 원격 제어 세션에 대한 자세한 내용을 볼 수 있습니다. 이 아이콘은 Windows 알림 영역 또는 원격 제어 세션 표시줄에 있습니다.  

## <a name="to-start-the-remote-control-viewer-from-the-windows-command-line"></a>Windows 명령줄에서 원격 제어 뷰어를 시작하려면  

-   Windows 명령 프롬프트에 _<Configuration Manager Installation Folder\>_ **\AdminConsole\Bin\i386\CmRcViewer.exe**를 입력합니다.  

CmRcViewer.exe에서 다음 명령줄 옵션을 지원합니다.  

- *주소* - NetBIOS 이름, FQDN(정규화된 도메인 이름) 또는 연결할 클라이언트 컴퓨터의 IP 주소를 지정합니다.
- *사이트 서버 이름* - 원격 제어 세션과 관련된 상태 메시지를 보낼 System Center Configuration Manager 사이트 서버의 이름을 지정합니다.
- **/?** – 원격 제어 뷰어에 대한 명령줄 옵션을 표시합니다.  
     
**예: CmRcViewer.exe** *<주소\>* *<\\\사이트 서버 이름>* 

> [!NOTE]  
> Configuration Manager 콘솔에 지원되는 모든 운영 체제에서 원격 제어 뷰어를 사용할 수 있습니다. 자세한 내용은 [System Center Configuration Manager 콘솔의 지원되는 구성](/sccm/core/plan-design/configs/supported-operating-systems-consoles) 및 [System Center Configuration Manager에서 원격 제어에 대한 필수 구성 요소](/sccm/core/clients/manage/remote-control/prerequisites-for-remote-control)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[원격 제어 사용 감사](/sccm/core/clients/manage/remote-control/audit-remote-control-usage)
