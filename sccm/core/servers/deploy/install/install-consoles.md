---
title: 콘솔 설치
titleSuffix: Configuration Manager
description: 중앙 관리 사이트 또는 기본 사이트에 연결할 Configuration Manager 콘솔을 설치합니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f17e479ef6b285cdb70960471dced73e83af520c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32339437"
---
# <a name="install-the-system-center-configuration-manager-console"></a>System Center Configuration Manager 콘솔 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

관리자는 Configuration Manager 콘솔을 사용하여 Configuration Manager 환경을 관리합니다. 각 Configuration Manager 콘솔은 중앙 관리 사이트 또는 기본 사이트에 연결할 수 있습니다. Configuration Manager 콘솔을 보조 사이트에 연결할 수는 없습니다.

> [!NOTE]  
>  관리자는 해당 사용자 계정에 할당된 사용 권한에 따라 콘솔에서 개체를 볼 수 있습니다. 역할 기반 관리에 대한 자세한 내용은 [역할 기반 관리의 기본 사항](../../../../core/understand/fundamentals-of-role-based-administration.md)을 참조하세요.  

 사이트 서버를 설치하는 경우 Configuration Manager 콘솔을 동시에 설치할 수 있습니다. 사이트 서버 설치와 별도로 콘솔을 설치하려면 독립 실행형 설치 관리자를 실행합니다.  

 독립 실행형 설치 관리자를 사용하여 Configuration Manager 콘솔을 설치하려면 다음 절차를 따르세요.  

## <a name="to-install-the-configuration-manager-console-by-using-the-setup-wizard"></a>설치 마법사를 사용하여 Configuration Manager 콘솔을 설치하려면  

1.  다음 요구 사항을 충족하는지 확인합니다.  

    -  콘솔에 대한 대상 컴퓨터에 로컬 **관리자** 권한이 있습니다.  

    -   Configuration Manager 콘솔 설치 파일의 위치에 대한 **읽기** 권한이 있습니다.  

2.  다음 위치 중 하나로 이동합니다.  

    -   사이트 서버에서 `<Configuration Manager site server installation path>\Tools\ConsoleSetup`으로 이동합니다.  

    -   Configuration Manager 원본 미디어에서 `<Configuration Manager source files>\Smssetup\Bin\I386`으로 이동합니다.  

    > [!TIP]  
    >  Configuration Manager 콘솔 설치 관리자는 System Center Configuration Manager 설치 미디어보다 사이트 서버에서 시작하는 것이 좋습니다. 사이트 서버를 설치하는 경우 Configuration Manager 콘솔 설치 파일 및 사이트의 지원되는 언어 팩이 **Tools\ConsoleSetup** 하위 폴더에 복사됩니다. 설치 미디어에서 Configuration Manager 콘솔을 설치하면 항상 영어 버전이 설치됩니다. 사이트 서버가 다른 언어를 지원하거나 대상 컴퓨터의 OS가 다른 언어로 설정된 경우에도 이 동작이 발생합니다. 필요에 따라 **ConsoleSetup** 폴더를 대체 위치에 복사하여 설치를 시작할 수 있습니다.

3.  Configuration Manager 콘솔 설치 마법사를 열려면 **consolesetup.exe**를 두 번 클릭합니다.  

    > [!IMPORTANT]  
    >  Configuration Manager 콘솔은 항상 **consolesetup.exe**를 사용하여 설치합니다. adminconsole.msi를 실행하여 Configuration Manager 콘솔을 설치할 수 있지만 이 방법은 필수 구성 요소 또는 종속성 검사를 실행하지 않습니다. 제대로 설치되지 않을 수 있습니다.  

4.  마법사에서 **다음**을 선택합니다.  

5.  **사이트 서버** 페이지에서 Configuration Manager 콘솔이 연결할 사이트 서버의 FQDN(정규화된 도메인 이름)을 입력합니다.  

6.  **설치 폴더** 페이지에서 Configuration Manager 콘솔에 대한 설치 폴더를 입력합니다. 폴더 경로 끝에 공백을 삽입해서도 유니코드 문자를 포함해서도 안 됩니다.  

7.  **사용자 환경 개선 프로그램** 페이지에서 CEIP(사용자 환경 개선 프로그램)에 대한 참여 여부를 선택합니다.  
    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

8.  **설치 준비 완료** 페이지에서 **설치**를 선택하여 Configuration Manager 콘솔을 설치합니다.  



## <a name="to-install-the-configuration-manager-console-from-a-command-prompt"></a>명령 프롬프트에서 Configuration Manager 콘솔을 설치하려면  

1.  Configuration Manager 콘솔을 설치할 서버에서 명령 프롬프트 창을 열고 다음 위치 중 하나로 이동합니다.  

    -   `<Configuration Manager site server installation path>\Tools\ConsoleSetup`  

    -   `<Configuration Manager installation media>\SMSSETUP\BIN\I386`  

    > [!TIP]  
    >  명령 프롬프트에서 Configuration Manager 콘솔을 설치하면 항상 영어 버전이 설치됩니다. 대상 컴퓨터의 OS가 다른 언어로 설정된 경우에도 이 동작이 발생합니다. Configuration Manager 콘솔을 영어 이외의 버전으로 설치하려면 [설치 마법사를 사용하여 Configuration Manager 콘솔을 설치](#to-install-the-configuration-manager-console-by-using-the-setup-wizard)해야 합니다.  

2.  명령 프롬프트에서 **consolesetup.exe**를 입력합니다. 다음 명령줄 옵션 중에서 선택합니다.  

|  명령줄 옵션을 사용합니다.     | 설명     |
  |-------------|-------------|
  |/q|Configuration Manager 콘솔을 무인 설치 모드로 설치합니다. 이 옵션을 사용할 때는 **EnableSQM**, **TargetDir**및 **DefaultSiteServerName** 옵션을 사용해야 합니다.|  
  |/uninstall|Configuration Manager 콘솔을 제거합니다. **/q** 옵션과 함께 사용할 경우 이 옵션을 먼저 지정합니다.|  
  |LangPackDir|언어 파일이 포함된 폴더의 경로를 지정합니다. **설치 다운로더** 를 사용하면 언어 파일을 다운로드할 수 있습니다. 이 옵션을 사용하지 않으면 설치 프로그램은 현재 폴더에서 언어 폴더를 찾습니다. 언어 폴더를 찾지 못하면 계속 설치가 진행되고 영어 버전만 설치됩니다. 자세한 내용은 [설치 다운로더](setup-downloader.md)를 참조하세요.|  
  |TargetDir|Configuration Manager 콘솔을 설치할 설치 폴더를 지정합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.|  
  |EnableSQM|CEIP(사용자 환경 개선 프로그램) 참여 여부를 지정합니다. CEIP에 참여하려면 **1** 값을 사용하고 프로그램에 참여하지 않으려면 **0** 값을 사용합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.</br></br>참고: Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.|  
  |DefaultSiteServerName|콘솔이 열릴 때 연결할 사이트 서버의 FQDN을 지정합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.|  


  ### <a name="examples"></a>예

  -  `consolesetup.exe /q TargetDir="D:\Program Files\ConfigMgr" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com`  

  -  `consolesetup.exe /q LangPackDir=C:\Downloads\ConfigMgr TargetDir="D:\Program Files\ConfigMgr Console" EnableSQM=1 DefaultSiteServerName=MyServer.Contoso.com`  

  -  `consolesetup.exe /uninstall /q`  
