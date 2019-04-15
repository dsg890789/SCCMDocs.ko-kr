---
title: 콘솔 설치
titleSuffix: Configuration Manager
description: 중앙 관리 사이트 또는 기본 사이트에 연결할 Configuration Manager 콘솔을 설치합니다.
ms.date: 04/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d39c201f-d364-4e7b-bde4-faa76d747f33
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1469845ce89b0de08a687baf3d518c1bd6d5294d
ms.sourcegitcommit: 5ee9487c891c37916294bd34a10d04e398f111f7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59069537"
---
# <a name="install-the-configuration-manager-console"></a>Configuration Manager 콘솔 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

관리자는 Configuration Manager 콘솔을 사용하여 Configuration Manager 환경을 관리합니다. 각 Configuration Manager 콘솔은 (CAS)중앙 관리 사이트 또는 기본 사이트에 연결할 수 있습니다. Configuration Manager 콘솔을 보조 사이트에 연결할 수는 없습니다.

Configuration Manager 콘솔은 항상 CAS 또는 주 사이트에 대한 사이트 서버에 설치됩니다. 사이트 서버 설치와 별도로 콘솔을 설치하려면 독립 실행형 설치 관리자를 실행합니다.  



## <a name="prerequisites"></a>필수 구성 요소

- 콘솔에 대한 대상 컴퓨터에 로컬 **관리자** 권한이 있습니다.  

- Configuration Manager 콘솔 설치 파일의 위치에 대한 **읽기** 권한이 있습니다.  



## <a name="source-paths"></a>원본 경로

사용할 원본 경로를 결정합니다.  

- 사이트 서버의 ConsoleSetup 폴더: `<Configuration Manager site server installation path>\Tools\ConsoleSetup`  

    사이트 서버를 설치하면 사이트에 대해 지원되는 언어 팩과 콘솔 설치 파일을 **Tools\ConsoleSetup** 하위 폴더에 복사합니다. 필요에 따라 **ConsoleSetup** 폴더를 대체 위치에 복사하여 설치를 시작할 수 있습니다. 사이트를 업데이트하면 로컬 버전이 항상 최신 상태로 유지됩니다.  

- Configuration Manager 설치 미디어: `<Configuration Manager installation media>\SMSSETUP\BIN\I386`  

    설치 미디어에서 Configuration Manager 콘솔을 설치하면 항상 영어 버전이 설치됩니다. 사이트 서버가 다른 언어를 지원하거나 대상 컴퓨터의 OS가 다른 언어로 설정된 경우에도 이 동작이 발생합니다.  

가능하면 소스 미디어가 아닌 **ConsoleSetup** 폴더에서 콘솔 설치 관리자를 시작합니다.

> [!Important]  
> **CD.Latest** 원본 파일을 시용하여 콘솔을 설치하지 마세요. 지원되지 않는 시나리오이므로, 콘솔 설치에 문제가 발생할 수 있습니다. 자세한 내용은 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder#unsupported-scenarios)를 참조하세요.<!-- SCCMDocs issue 1359 -->  

콘솔을 다른 컴퓨터에서 설치하기 위한 패키지를 생성하는 경우, 패키지에 다음 파일이 포함되어 있는지 확인합니다.<!--3612513-->

- ConsoleSetup.exe
- AdminConsole.msi
- ConfigMgr.AC_Extension.i386.cab(1902 버전부터)
- ConfigMgr.AC_Extension.amd64.cab(1902 버전부터)



## <a name="use-the-setup-wizard"></a>설치 마법사 사용  

1. 원본 경로를 검색하여 **ConsoleSetup.exe**를 엽니다.  

    > [!IMPORTANT]  
    > 콘솔은 항상 **ConsoleSetup.exe**를 사용하여 설치해야 합니다. AdminConsole.msi를 실행하여 Configuration Manager 콘솔을 설치할 수 있지만 이 방법은 필수 구성 요소 또는 종속성 검사를 실행하지 않습니다. 제대로 설치되지 않을 수 있습니다.  

2. 마법사에서 **다음**을 선택합니다.  

3. **사이트 서버** 페이지에서 Configuration Manager 콘솔이 연결할 사이트 서버의 FQDN(정규화된 도메인 이름)을 입력합니다.  

4. **설치 폴더** 페이지에서 Configuration Manager 콘솔에 대한 설치 폴더를 입력합니다. 폴더 경로 끝에 공백을 삽입해서도 유니코드 문자를 포함할 수 없습니다.  

5. **사용자 환경 개선 프로그램** 페이지에서 CEIP(사용자 환경 개선 프로그램)에 대한 참여 여부를 선택합니다.  

    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

6. 에 **설치 준비 완료** 페이지에서 **설치**를 선택합니다.  



## <a name="install-from-a-command-prompt"></a>명령 프롬프트에서 설치  

> [!TIP]  
> 명령 프롬프트에서 Configuration Manager 콘솔을 설치하면 항상 영어 버전이 설치됩니다. 대상 컴퓨터의 OS가 다른 언어로 설정된 경우에도 이 동작이 발생합니다. 영어 이외의 언어로 Configuration Manager 콘솔을 설치하려면 [설치 마법사](#use-the-setup-wizard)를 사용하세요.  


### <a name="consolesetupexe-command-line-options"></a>ConsoleSetup.exe 명령줄 옵션

#### <a name="q"></a>/q

Configuration Manager 콘솔을 무인 설치 모드로 설치합니다. 이 옵션을 사용할 때는 **EnableSQM**, **TargetDir**및 **DefaultSiteServerName** 옵션을 사용해야 합니다.

#### <a name="uninstall"></a>/uninstall

Configuration Manager 콘솔을 제거합니다. **/q** 옵션과 함께 사용할 경우 이 옵션을 먼저 지정합니다.

#### <a name="langpackdir"></a>LangPackDir

언어 파일이 포함된 폴더의 경로를 지정합니다. **설치 다운로더** 를 사용하면 언어 파일을 다운로드할 수 있습니다. 이 옵션을 사용하지 않으면 설치 프로그램은 현재 폴더에서 언어 폴더를 찾습니다. 언어 폴더를 찾지 못하면 계속 설치가 진행되고 영어 버전만 설치됩니다. 자세한 내용은 [설치 다운로더](setup-downloader.md)를 참조하세요.

#### <a name="targetdir"></a>TargetDir

Configuration Manager 콘솔을 설치할 설치 폴더를 지정합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.

#### <a name="enablesqm"></a>EnableSQM

CEIP(사용자 환경 개선 프로그램) 참여 여부를 지정합니다. CEIP에 참여하려면 **1** 값을 사용하고 프로그램에 참여하지 않으려면 **0** 값을 사용합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.

> [!Important]  
> Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다. 매개 변수를 사용하면 설치가 실패합니다.

#### <a name="defaultsiteservername"></a>DefaultSiteServerName

콘솔이 열릴 때 연결할 사이트 서버의 FQDN을 지정합니다. 이 옵션은 **/q** 옵션을 사용하는 경우에 필요합니다.


### <a name="examples"></a>예

> [!Important]  
> 버전 1802 이상에는 **EnableSQM** 매개 변수가 포함되지 않습니다.

#### <a name="silent-install"></a>자동 설치

`ConsoleSetup.exe /q TargetDir="%ProgramFiles%\ConfigMgr Console" DefaultSiteServerName=MyServer.Contoso.com`

#### <a name="silent-install-with-language-packs"></a>언어 팩을 사용하여 자동 설치

`ConsoleSetup.exe /q TargetDir="C:\Program Files\ConfigMgr Console" DefaultSiteServerName=MyServer.Contoso.com LangPackDir=C:\Downloads\ConfigMgr`  

#### <a name="silent-uninstall"></a>자동 제거

`ConsoleSetup.exe /uninstall /q`  



## <a name="see-also"></a>참고 항목

관리자는 해당 사용자 계정에 할당된 사용 권한에 따라 콘솔에서 개체를 볼 수 있습니다. 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.

Configuration Manager 콘솔 탐색의 기본 사항에 대한 자세한 내용은 [콘솔 사용](/sccm/core/servers/manage/admin-console)을 참조하세요.
