---
title: 작업 순서 미디어에 대한 시작 전 명령
titleSuffix: Configuration Manager
description: 시작 전 명령에 사용할 스크립트를 만들고, 시작 전 명령과 연관된 콘텐츠를 배포하고, 미디어 안에 시작 전 명령을 구성합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: ccc9f652-2953-4c38-8a90-c799484105ca
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9dd921d58e6ef777017af3e2eb24dbf4bd611fab
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821072"
---
# <a name="prestart-commands-for-task-sequence-media-in-configuration-manager"></a>Configuration Manager의 작업 순서 미디어에 대한 시작 전 명령

*적용 대상: Configuration Manager(현재 분기)*

부팅 미디어, 독립 실행형 미디어 및 사전 준비된 미디어와 함께 사용할 시작 전 명령을 Configuration Manager에서 만들 수 있습니다. 시작 전 명령은 작업 순서를 선택하기 전에 실행되고 Windows PE에서 사용자와 상호 작용할 수 있는 스크립트 또는 실행 파일입니다. 시작 전 명령은 사용자에게 정보를 알리고 이 정보를 작업 순서 환경에 저장하거나, 정보에 사용될 작업 순서 변수를 쿼리할 수 있습니다. 대상 컴퓨터가 부팅하면 정책이 관리 지점에서 다운로드되기 전에 명령줄이 실행됩니다. 시작 전 명령에 사용할 스크립트를 만들고, 시작 전 명령과 연관된 콘텐츠를 배포하고, 미디어 안에 시작 전 명령을 구성하려면 다음 절차를 따르십시오.  

## <a name="create-a-script-file-to-use-for-the-prestart-command"></a>시작 전 명령에 사용할 스크립트 파일 만들기  
 작업 순서 변수는 작업 순서가 실행되는 동안 Microsoft.SMS.TSEnvironment COM 개체를 사용하여 읽고 쓸 수 있습니다. 다음 예제는 _SMSTSLogPath 작업 순서 변수를 쿼리하여 현재 로그 위치를 가져오는 Visual Basic 스크립트 파일을 보여 줍니다. 또한 스크립트는 사용자 지정 변수를 설정합니다.  

``` VBScript
dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")  
dim logPath  
' You can query the environment to get an existing variable.  
logPath = env("_SMSTSLogPath")  
' You can also set a variable in the OSD environment.  
env("MyCustomVariable") = "varname"  
```  

## <a name="create-a-package-for-the-script-file-and-distribute-the-content"></a>스크립트 파일용 패키지 만들기 및 콘텐츠 배포  
 시작 전 명령에 대한 스크립트 또는 실행 파일을 만든 후에는 스크립트 또는 실행 파일에 대한 파일을 호스트할 패키지 원본을 만들고, 해당 파일용 패키지를 만든 후(프로그램 불필요), 콘텐츠를 배포 지점에 배포해야 합니다.  

 패키지 만들기에 대한 자세한 내용은 [패키지 및 프로그램](../../apps/deploy-use/packages-and-programs.md)을 참조하세요.  

 콘텐츠를 배포하는 방법에 대한 자세한 내용은 [콘텐츠 배포](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute)를 참조하세요.  

## <a name="configure-the-prestart-command-in-media"></a>미디어에서 시작 전 명령 구성  
 작업 순서 미디어 만들기 마법사에서 독립 실행형 미디어, 부팅 가능한 미디어 또는 미리 준비된 미디어에 대해 시작 전 명령을 구성할 수 있습니다. 미디어 유형에 대한 자세한 내용은 [작업 순서 미디어 만들기](../deploy-use/create-task-sequence-media.md)를 참조하세요. 미디어에서 시작 전 명령을 만들려면 다음 절차를 따르십시오.  

#### <a name="to-create-a-prestart-command-in-media"></a>미디어에서 시작 전 명령을 만들려면  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **작업 순서 미디어 만들기** 를 클릭하여 작업 순서 미디어 만들기 마법사를 시작합니다.  

4.  **미디어 유형 선택** 페이지에서 **독립 실행형 미디어**, **부팅 가능한 미디어**또는 **미리 준비된 미디어**를 선택하고 **다음**을 클릭합니다.  

5.  마법사의 **사용자 지정** 페이지로 이동합니다. 마법사에서 다른 페이지를 구성하는 방법에 대한 자세한 내용은 [작업 순서 미디어 만들기](../deploy-use/create-task-sequence-media.md)를 참조하세요.  

6.  **사용자 지정** 페이지에서 다음 정보를 지정한 후에 **다음**을 클릭합니다.  

    -   **시작 전 명령 사용**을 선택합니다.  

    -   **명령줄** 텍스트 상자에 시작 전 명령용으로 만든 스크립트 또는 실행 파일을 입력합니다.  

        > [!IMPORTANT]  
        >  **cmd /C <시작 전 명령\>** 을 사용하여 시작 전 명령을 지정합니다. 예를 들어 시작 전 명령 스크립트의 이름으로 TSScript.vbs를 사용한 경우 명령줄에 **cmd /C TSScript.vbs** 를 입력합니다. 여기서 **cmd /C** 는 새 Windows 명령 인터프리터 창을 열고 Path 환경 변수를 사용하여 시작 전 명령 스크립트 또는 실행 파일을 검색합니다. 시작 전 명령의 전체 경로를 지정할 수도 있지만 드라이브 구성이 다른 컴퓨터에서는 드라이브 문자가 달라질 수 있습니다.  

    -   **시작 전 명령을 위한 파일 포함**을 선택합니다.  

    -   **설정** 을 클릭하여 시작 전 명령 파일과 연결된 패키지를 선택합니다.  

    -   **찾아보기** 를 클릭하여 시작 전 명령에 대한 콘텐츠를 호스트하는 배포 지점을 선택합니다.  

7.  마법사를 완료합니다.  
