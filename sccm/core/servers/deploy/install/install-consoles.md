---
title: "콘솔 설치 | System Center Configuration Manager"
description: "중앙 관리 사이트 또는 기본 사이트에 연결할 Configuration Manager 콘솔을 설치하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 1483e35a397667a340605c0454c1835ec6067d9e

---
# <a name="install-system-center-configuration-manager-consoles"></a>System Center Configuration Manager 콘솔 설치

*적용 대상: System Center Configuration Manager(현재 분기)*


관리자는 System Center Configuration Manager 콘솔을 사용하여 Configuration Manager 환경을 관리합니다. 각 Configuration Manager 콘솔은 중앙 관리 사이트 또는 기본 사이트에 연결할 수 있습니다. Configuration Manager 콘솔을 보조 사이트에 연결할 수는 없습니다.


> [!NOTE]  
>  콘솔을 실행하는 관리자에 대해 표시되는 개체는 해당 관리자에게 할당된 권한에 따라 달라집니다. 역할 기반 관리에 대한 자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../../../core/understand/fundamentals-of-role-based-administration.md)을 참조하세요.  

 Configuration Manager 콘솔은 설치 마법사에서 사이트 서버를 설치할 때 설치하거나 독립 실행형 응용 프로그램을 실행하여 설치할 수 있습니다.  

 독립 실행형 응용 프로그램을 사용하여 Configuration Manager 콘솔을 설치하려면 다음 절차를 따르세요.  

## <a name="to-install-a-configuration-manager-console"></a>Configuration Manager 콘솔을 설치하려면  

1.  Configuration Manager 콘솔 응용 프로그램을 실행하는 관리자에게 다음 보안 권한이 있는지 확인합니다.  

    -   콘솔을 실행할 컴퓨터에 대한**로컬 관리자** 권한  

    -   Configuration Manager 콘솔 설치 파일의 위치에 대한 **읽기** 권한  

2.  다음 위치 중 하나를 찾아봅니다.  

    -   Configuration Manager 원본 미디어에서 **&lt;ConfigMgrSourceFiles\>\Smssetup\Bin\I386**을 찾습니다.  

    -   사이트 서버에서 **&lt;Configuration Manager 사이트 서버 설치 경로\>\Tools\ConsoleSetup**을 찾습니다.  

    > [!TIP]  
    >  Configuration Manager 콘솔 설치를 시작합니다. System Center Configuration Manager 설치 미디어보다 사이트 서버에서 시작하는 것이 좋습니다. 사이트 서버를 통한 설치 방식에서는 Configuration Manager 콘솔 설치 파일 및 사이트의 지원되는 언어 팩이 **Tools\ConsoleSetup** 하위 폴더에 복사됩니다. 설치 미디어에서 Configuration Manager 콘솔을 설치하는 방식에서는 사이트 서버에서 지원되는 언어 또는 컴퓨터에서 실행 중인 운영 체제의 언어 설정에 관계없이 항상 영어 버전이 설치됩니다. 필요에 따라 **ConsoleSetup** 폴더를 대체 위치에 복사하여 설치를 시작할 수 있습니다.  

3.  **consolesetup.exe**를 두 번 클릭합니다. Configuration Manager 콘솔 설치 마법사가 열립니다.  

    > [!IMPORTANT]  
    >  Configuration Manager 콘솔은 항상 consolesetup.exe를 사용하여 설치해야 합니다. AdminConsole.msi를 실행하여 Configuration Manager 콘솔을 설치할 수도 있지만 이 방식을 사용할 경우 필수 조건 검사 또는 종속성 검사가 실행되지 않으며 제대로 설치되지 않을 수 있습니다.  

4.  시작 페이지에서 **다음**을 클릭합니다.  

5.  **사이트 서버** 페이지에서 Configuration Manager 콘솔이 연결할 사이트 서버의 FQDN(정규화된 도메인 이름)을 지정합니다.  

6.  **설치 폴더** 페이지에서 Configuration Manager 콘솔에 대한 설치 폴더를 지정합니다. 폴더 경로 끝에 공백을 삽입해서도 유니코드 문자를 포함해서도 안 됩니다.  

7.  **사용자 환경 개선 프로그램** 페이지에서 사용자 환경 개선 프로그램에 대한 참여 여부를 선택합니다.  

8.  **설치 준비 완료** 페이지에서 **설치**를 클릭하여 Configuration Manager 콘솔을 설치합니다.  

## <a name="to-install-a-configuration-manager-console-from-a-command-prompt"></a>명령 프롬프트에서 Configuration Manager 콘솔을 설치하려면  

1.  Configuration Manager 콘솔을 설치할 서버에서 명령 프롬프트 창을 열고 다음 위치 중 하나로 이동합니다.  

    -   **&lt;ConfigMgrSiteServerInstallationPath\>\Tools\ConsoleSetup**  

    -   **&lt;ConfigMgrInstallationMedia\>\SMSSETUP\BIN\I386**  

    > [!TIP]  
    >  명령 프롬프트에서 Configuration Manager 콘솔을 설치하는 경우 컴퓨터에서 실행 중인 운영 체제의 언어 설정에 관계없이 항상 영어 버전이 설치됩니다. Configuration Manager 콘솔을 다른 언어로 설치하려면 이전 절차를 사용하여 설치해야 합니다.  

2.  **consolesetup.exe** 를 입력하고 다음 명령줄 옵션 중에서 선택합니다.  

|  명령줄 옵션을 사용합니다.     | 설명     |
  | :------------- | :------------- |
  |/q|Configuration Manager 콘솔을 무인 설치 모드로 설치합니다. 이 옵션을 사용할 때는 **EnableSQM**, **TargetDir**및 **DefaultSiteServerName** 옵션을 사용해야 합니다.|  
  |/uninstall|Configuration Manager 콘솔을 제거합니다. **/q** 옵션과 함께 사용할 경우 이 옵션을 먼저 지정해야 합니다.|  
  |LangPackDir|언어 파일이 포함된 폴더의 경로를 지정합니다. **설치 다운로더** 를 사용하면 언어 파일을 다운로드할 수 있습니다. 이 옵션을 사용하지 않으면 설치 프로그램은 현재 폴더에서 언어 폴더를 찾습니다. 언어 폴더를 찾지 못하면 계속 설치가 진행되고 영어 버전만 설치됩니다. 자세한 내용은 [설치 다운로더](/sccm/core/servers/deploy/install/setup-downloader)를 참조하세요.|  
  |TargetDir|Configuration Manager 콘솔을 설치할 설치 폴더를 지정합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.|  
  |EnableSQM|CEIP(사용자 환경 개선 프로그램) 참여 여부를 지정합니다. 참여하면 1 값을 사용하고 참여하지 않으면 0 값을 사용합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.|  
  |DefaultSiteServerName|콘솔이 열릴 때 연결할 사이트 서버의 FQDN을 지정합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.|  


  **사용 예:**  
  -  **consolesetup.exe /q TargetDir="D:\Program Files\ConfigMgr" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe /q LangPackDir=C:\Downloads\ConfigMgr TargetDir="D:\Program Files\ConfigMgr" Console EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com**  

  -  **consolesetup.exe /uninstall /q**  



<!--HONumber=Nov16_HO1-->


