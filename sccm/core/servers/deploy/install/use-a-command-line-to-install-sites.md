---
title: "명령줄 설치"
titleSuffix: Configuration Manager
description: "명령 프롬프트에서 여러 사이트 설치에 대해 System Center Configuration Manager 설치 프로그램을 실행하는 방법을 알아봅니다."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e7cdb1a9-140a-436e-ac71-72d083110223
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: dfef96a5512ca79252360da4b5eee39c04d90046
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="use-a-command-line-to-install-system-center-configuration-manager-sites"></a>명령줄을 사용하여 System Center Configuration Manager 사이트 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

 명령 프롬프트에서 System Center Configuration Manager 설치 프로그램을 실행하여 다양한 사이트 유형을 설치할 수 있습니다.

## <a name="supported-tasks-for-command-line-installations"></a>명령줄 설치에 대해 지원되는 작업
 설치 프로그램을 실행하는 이 방법은 다음과 같은 사이트 설치 및 사이트 유지 관리 작업을 지원합니다.

-   **명령 프롬프트에서 중앙 관리 사이트 또는 기본 사이트 설치**  
  [설치용 명령줄 옵션](../../../../core/servers/deploy/install/command-line-options-for-setup.md) 보기

-  **중앙 관리 사이트 또는 기본 사이트에서 사용 중인 언어 수정**  
    명령 프롬프트에서 사이트에 설치된 언어(모바일 장치용 언어 포함)를 수정하려면 다음을 수행해야 합니다.  

     -   사이트 서버의 **&lt;Configuration Manager 설치 경로\>\BIN\X64**에서 설치 프로그램 실행
     -   **/MANAGELANGS** 명령줄 옵션 사용
     -   추가 또는 제거할 언어를 지정하는 언어 스크립트 파일 지정  

    예를 들어 **setupwpf.exe /MANAGELANGS &lt;언어 스크립트 파일\>** 명령 구문을 사용합니다.  

    언어 스크립트 파일을 만들려면 [언어 관리용 명령줄 옵션](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Lang)의 정보를 참조하세요.  

-  **무인 사이트 설치 또는 사이트 복구를 위해 설치 스크립트 파일 사용**  
    설치 스크립트를 사용하여 명령 프롬프트에서 설치 프로그램을 실행할 수 있으며, 무인 사이트 설치를 실행합니다. 이 옵션을 사용하여 사이트를 복구할 수도 있습니다.    

    설치 프로그램에서 스크립트를 사용하려면  

    -   명령줄 옵션 **/SCRIPT**를 사용하여 설치 프로그램을 실행하고 스크립트 파일을 지정합니다.  

    -   필요한 키와 값으로 스크립트 파일을 구성해야 합니다.  

    중앙 관리 사이트 또는 기본 사이트의 무인 설치를 수행하려면 스크립트 파일에 다음 섹션이 있어야 합니다.  

    -   Identification    
    -   Options    
    -   SQLConfigOptions    
      -   HierarchyOptions    
    -   CloudConnectorOptions   

    사이트를 복구하려면 스크립트 파일의 다음 섹션도 포함해야 합니다.  

    -   Identification  
    -   복구

자세한 내용은 [Configuration Manager에 대한 무인 사이트 복구](/sccm/protect/understand/unattended-recovery)를 참조하세요.  

무인 설치 스크립트 파일에서 사용할 키와 값 목록은 [무인 설치 스크립트 파일 키](../../../../core/servers/deploy/install/command-line-options-for-setup.md#bkmk_Unattended)를 참조하세요.  

## <a name="about-the-command-line-script-file"></a>명령줄 스크립트 파일 정보  
 Configuration Manager의 무인 설치를 수행하려는 경우 명령줄 옵션 **/SCRIPT**를 사용하여 설치 프로그램을 실행하고 설치 옵션이 포함된 스크립트 파일을 지정할 수 있습니다. 이 방법을 사용하여 수행할 수 있는 작업은 다음과 같습니다.  

-   중앙 관리 사이트 설치  
-   기본 사이트 설치  
-   Configuration Manager 콘솔 설치  
-   사이트 복구  

> [!NOTE]  
>  무인 스크립트 파일을 사용하여 Configuration Manager의 평가판 사이트를 라이선스 설치로 업그레이드할 수는 없습니다.  

### <a name="the-cdlatest-key-name"></a>CDLatest 키 이름
CD.Latest 폴더의 미디어를 사용하여 다음 네 가지 설치 옵션의 스크립팅된 설치를 실행할 경우 스크립트에 **CDLatest** 키와 **1** 값을 포함해야 합니다.
- 새 중앙 관리 사이트 설치
- 새 기본 사이트 설치
- 중앙 관리 사이트 복구
- 기본 사이트 복구

Microsoft 볼륨 라이선스 사이트에서 얻은 설치 미디어에는 이 값을 사용할 수 없습니다.
스크립트 파일에서 이 키 이름을 사용하는 방법에 대한 자세한 내용은 [명령줄 옵션](/sccm/core/servers/deploy/install/command-line-options-for-setup)을 참조하세요.



### <a name="create-the-script"></a>스크립트 만들기
[사용자 인터페이스를 통해 설치 프로그램을 실행하여 사이트를 설치](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md)하면 설치 스크립트가 자동으로 생성됩니다.  마법사의 **요약** 페이지에서 설정을 확인하면 다음과 같은 작업이 수행됩니다.  

-   설치 프로그램은 **%TEMP%\ConfigMgrAutoSave.ini**스크립트를 만듭니다.  이 파일은 사용 전에 이름을 바꿀 수 있지만 .ini 파일 확장명은 유지해야 합니다.  
-   무인 설치 스크립트에는 마법사에서 선택한 설정이 포함됩니다.  
-   스크립트를 만든 후에는 스크립트를 수정하여 계층의 다른 사이트를 설치할 수 있습니다.  
-   이 스크립트를 사용하여 Configuration Manager의 무인 설치를 수행할 수 있습니다.  

이 스크립트 파일은 기본 설정이 없다는 점만 제외하고 설치 마법사에서 요구하는 것과 같은 정보를 제공합니다.   
사용하는 설치 유형에 적용되는 설치 키의 값을 모두 지정해야 합니다.   

설치 프로그램이 무인 설치 스크립트를 만들 때 설치 중 사용자가 입력한 제품 키 값이 채워집니다. 이 키는 유효한 제품 키이거나, Configuration Manager의 평가 버전을 설치하는 경우 **EVAL**입니다. 스크립트의 제품 키 값이 채워지므로 필수 조건 검사를 완료할 수 있습니다.   

실제 사이트 설치가 시작되면 자동으로 만들어진 스크립트가 다시 기록되어서 만들어진 스크립트의 제품 키 값이 지워집니다. 새 사이트의 무인 설치를 위한 스크립트를 사용하기 전에 스크립트를 편집하여 유효한 제품 키를 입력하거나 Configuration Manager의 평가 버전을 지정할 수 있습니다.  

### <a name="section-names-key-names-and-values"></a>섹션 이름, 키 이름 및 값
스크립트에는 섹션 이름, 키 이름 및 값이 포함됩니다. 다음 정보에 유의하세요.
-   필수 세션 키 이름은 스크립팅하는 설치 유형에 따라 달라집니다.
-   섹션 내의 키 순서와 파일 내의 섹션 순서는 중요하지 않습니다.     
-   키는 대/소문자를 구분하지 않습니다.  
-   키에 값을 지정할 때에는 키 이름 뒤에 등호(=)를 추가하고 키 값을 입력해야 합니다.    

> [!TIP]  
>  전체 옵션 집합을 확인하려면 [설치 및 스크립트용 명령줄 옵션](../../../../core/servers/deploy/install/command-line-options-for-setup.md)을 참조하세요.  

## <a name="use-the-script-setup-command-line-option"></a>/SCRIPT 설치 명령줄 옵션 사용

-   설치 스크립트 파일을 사용하여 **/SCRIPT** 설치 명령줄 옵션 뒤에 파일 이름을 지정해야 합니다. 다음 정보에 유의하세요.   
    -   이 파일 이름의 확장명은 **.ini**여야 합니다.  
    -   명령 프롬프트에서 설치 스크립트 파일을 참조할 때는 파일의 전체 경로를 제공해야 합니다. 예를 들어 설치 초기화 파일의 이름이 Setup.ini이고 C:\Setup 폴더에 파일이 저장되어 있으면 명령 프롬프트에서 **setup /script c:\setup\setup.ini**를 입력합니다.  

-   설치 프로그램을 실행하는 계정에 컴퓨터에 대한 **관리자** 권한이 있어야 합니다. 무인 스크립트로 설치 프로그램을 실행하는 경우 **관리자 권한으로 실행** 옵션을 사용하여 명령 프롬프트 창을 엽니다.   
