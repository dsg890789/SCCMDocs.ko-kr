---
title: "부팅 이미지 사용자 지정 - Configuration Manager | Microsoft 문서"
description: "Configuration Manager 또는 DISM(배포 이미지 서비스 및 관리) 명령줄 도구를 사용하여 부팅 이미지 사용자 지정하는 몇 가지 방법을 알아봅니다."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9cbfc406-d009-446d-8fee-4938de48c919
caps.latest.revision: 15
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 89158debdf4c345a325feeb608db2215a88ed81b
ms.openlocfilehash: ab2ecb64c9c80b4effed79ba08769c99473db0c4


---
# <a name="customize-boot-images-with-system-center-configuration-manager"></a>System Center Configuration Manager로 부팅 이미지 사용자 지정

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 각 버전은 Windows ADK(Windows Assessment and Deployment Kit)의 특정 버전을 지원합니다. 부팅 이미지가 지원되는 버전의 Windows ADK에 있는 Windows PE 버전을 기반으로 하는 경우 Configuration Manager 콘솔에서 부팅 이미지를 제공하거나 사용자 지정할 수 있습니다. 다른 부팅 이미지의 경우 Windows AIK 및 Windows ADK의 구성 요소인 DISM(배포 이미지 서비스 및 관리) 명령줄 도구를 사용하는 등의 다른 방법을 사용하여 해당 이미지를 사용자 지정해야 합니다.  

 다음에는 지원되는 Windows ADK 버전, Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 기반 Windows PE 버전, DISM을 통해 사용자 지정하여 Configuration Manager에 이미지를 추가할 수 있는 부팅 이미지의 기반 Windows PE 버전이 나와 있습니다.  

-   **Windows ADK 버전**  

     Windows 10용 Windows ADK  

-   **Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 Windows PE 버전**  

     Windows PE 10  

-   **Configuration Manager 콘솔에서 사용자 지정할 수 없지만 지원되는 부팅 이미지의 Windows PE 버전**  

     Windows PE 3.1<sup>1</sup> 및 Windows PE 5  

     <sup>1</sup> 부팅 이미지가 Windows PE 3.1을 기반으로 하는 경우에만 Configuration Manager에 부팅 이미지를 추가할 수 있습니다. Windows 7 SP1용 Windows AIK 추가 기능을 설치하여 Windows 7 SP1용 Windows AIK 추가 기능(Windows PE 3.1에 기반)이 포함된 Windows 7용 Windows AIK(Windows PE 3에 기반)로 업그레이드하세요. [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=5188)에서 Windows 7 SP1용 Windows AIK 추가 기능을 다운로드할 수 있습니다.  

     예를 들어 Configuration Manager를 설치한 경우 Configuration Manager 콘솔에서 Windows 10용 Windows ADK(Windows PE 10 기반)의 부팅 이미지를 사용자 지정할 수 있습니다. 그러나 Windows PE 5를 기반으로 하는 부팅 이미지가 지원되지만 여러 컴퓨터의 부팅 이미지를 사용자 지정하고 Windows 8용 Windows ADK와 함께 설치된 DISM 버전을 사용해야 합니다. 그런 다음 부팅 이미지를 Configuration Manager 콘솔에 추가할 수 있습니다.  

 이 항목의 절차에서는 다음과 같은 Windows PE 패키지를 사용하여 Configuration Manager에 필요한 옵션 구성 요소를 부팅 이미지에 추가하는 방법을 보여 줍니다.  

-   **WinPE WMI**: Windows Management Instrumentation(WMI) 지원을 추가합니다.  

-   **WinPE-Scripting**: WSH(Windows Script Host) 지원을 추가합니다.  

-   **WinPE-WDS-Tools**: Windows 배포 서비스 도구를 설치합니다.  

 다른 Windows PE 패키지를 추가할 수 있습니다. 다음 리소스에서는 부팅 이미지에 추가할 수 있는 선택적 구성 요소에 대한 자세한 정보를 제공합니다.  

-   Windows PE 5의 경우 [WinPE: 패키지 추가(선택적 구성 요소 참조)](https://msdn.microsoft.com/library/windows/hardware/dn938382\(v=vs.85\).aspx)를 참조하세요.  

-   Windows PE 3.1의 경우, Windows 7 TechNet 문서 라이브러리의 [Windows PE 이미지에 패키지 추가](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx) 항목을 참조하세요.  

> [!NOTE]
>추가된 도구를 포함하는 사용자 지정된 부팅 이미지에서 WinPE로 부팅하면 WinPE에서 명령 프롬프트를 열고 도구의 파일 이름을 입력하여 실행합니다. 이러한 도구의 위치는 경로 변수에 자동으로 추가됩니다. 명령 프롬프트는 부팅 이미지 속성의 **사용자 지정** 탭에서 **명령 지원 사용(테스트 전용)** 설정이 선택된 경우에만 추가할 수 있습니다.

## <a name="customize-a-boot-image-that-uses-windows-pe-5"></a>Windows PE 5를 사용하는 부팅 이미지 사용자 지정  
 Windows PE 5를 사용하는 부팅 이미지를 사용자 지정하려면 Windows ADK를 설치하고, DISM 명령줄 도구를 사용하여 부팅 이미지를 탑재하고, 선택적 구성 요소 및 드라이버를 추가하고, 부팅 이미지의 변경 내용을 커밋해야 합니다. 다음 절차에 따라 부팅 이미지를 사용자 지정할 수 있습니다.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-5"></a>Windows PE 5를 사용하는 부팅 이미지를 사용자 지정하려면  

1.  다른 버전의 Windows AIK 또는 Windows ADK와 어떤 Configuration Manager 구성 요소도 설치되어 있지 않은 컴퓨터에 Windows ADK를 설치합니다.  

2.  [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=39982)에서 Windows 8.1용 Windows ADK를 다운로드합니다.  

3.  Windows ADK 설치 폴더(예: <*설치 경로*>\Windows Kits\\<*버전*>\Assessment and Deployment Kit\Windows Preinstallation Environment\\<*x86 또는 amd64*>\\<*로캘*>)에서 부팅 이미지를 사용자 지정할 컴퓨터의 대상 폴더로 부팅 이미지(wimpe.wim)를 복사합니다. 이 절차에서는 C:\WinPEWAIK를 대상 이름으로 사용합니다.  

4.  DISM을 사용하여 부팅 이미지를 로컬 Windows PE 폴더에 탑재합니다. 예를 들어, 다음 명령줄을 입력합니다.  

     **dism.exe /mount-wim /wimfile:C:\WinPEWAIK\winpe.wim /index:1 /mountdir:C:\WinPEMount**  

     여기서 C:\WinPEWAIK는 부팅 이미지가 포함된 폴더이고, C:\WinPEMount는 탑재된 폴더입니다.  

    > [!NOTE]
    >  DISM에 대한 자세한 내용은 Windows 8.1 및 Windows 8 TechNet 문서 라이브러리의 [DISM - 배포 이미지 서비스 및 관리 기술 참조](http://technet.microsoft.com/library/hh824821.aspx) 항목을 참조하세요.

5.  부팅 이미지를 탑재한 후 DISM을 사용하여 부팅 이미지에 선택적 구성 요소를 추가합니다. Windows PE 5의 경우 64비트 선택적 구성 요소는 <*설치 경로*>\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs에 있습니다.  

    > [!NOTE]
    >  이 절차에서는 선택적 구성 요소에 대해 C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs 위치를 사용합니다. 사용하는 경로는 Windows ADK에 대해 선택하는 버전 및 설치 옵션에 따라 달라집니다.  

     선택적 구성 요소를 설치하려면 다음을 입력하세요.  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wmi.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-scripting.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\winpe-wds-tools.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\WinPE-SecureStartup.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<로캘\>* **\WinPE-SecureStartup_** *<로캘\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<로캘\>* **\WinPE-WMI_** *<로캘\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<로캘\>* **\WinPE-Scripting** *<로캘\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\\** *<로캘\>* **\WinPE-WDS-Tools_** *<로캘\>* **.cab"**  

     여기서 C:\WinPEMount는 탑재된 폴더이고 로캘은 구성 요소의 로캘입니다. 예를 들어 **ko-kr** 로캘의 경우 다음과 같이 입력합니다.  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-SecureStartup_en-us.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WMI_en-us.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-Scripting_en-us.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files (x86)\Windows Kits\8.1\Assessment and Deployment Kit\Windows Preinstallation Environment\amd64\WinPE_OCs\en-us\WinPE-WDS-Tools_en-us.cab"**  

    > [!TIP]
    >  부팅 이미지에 추가할 수 있는 선택적 구성 요소에 대한 자세한 내용은 Windows 8.1 및 Windows 8 TechNet 문서 라이브러리의 [Windows PE 선택적 구성 요소 참조](http://technet.microsoft.com/library/hh824926.aspx) 항목을 참조하세요.  

6.  필요한 경우 DISM을 사용하여 특정 드라이버를 부팅 이미지에 추가합니다. 다음을 입력하여 부팅 이미지에 드라이버를 추가하세요.  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:&lt;** *드라이버 .inf 파일의 경로* **>**  

     여기서 C:\WinPEMount는 탑재된 폴더입니다.  

7.  다음을 입력하여 부팅 이미지 파일을 분리하고 변경 사항을 커밋합니다.  

     **dism.exe /unmount-wim /mountdir:C:\WinPEMount /commit**  

     여기서 C:\WinPEMount는 탑재된 폴더입니다.  

8.  업데이트된 부팅 이미지를 Configuration Manager에 추가하여 작업 순서에서 사용 가능하도록 설정합니다. 다음 절차에 따라 업데이트된 부팅 이미지를 가져올 수 있습니다.  

    1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

    2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

    3.  **홈** 탭의 **만들기** 그룹에서 **부팅 이미지 추가** 를 클릭하여 부팅 이미지 추가 마법사를 시작합니다.  

    4.  **데이터 원본** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.  

        -   **경로** 상자에서 업데이트된 부팅 이미지 파일의 경로를 지정합니다. 지정하는 경로는 UNC 형식의 유효한 네트워크 경로여야 합니다. 예를 들어 **\\\\<***servername***>\\<***WinPEWAIK 공유***>\winpe.wim**과 같습니다.  

        -   **부팅 이미지** 드롭다운 목록에서 부팅 이미지를 선택합니다. WIM 파일에 여러 부팅 이미지가 포함되어 있는 경우 각 이미지가 나열됩니다.  

    5.  **일반** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.  

        -   **이름** 상자에서 부팅 이미지의 고유한 이름을 지정합니다.  

        -   **버전** 상자에서 부팅 이미지의 버전 번호를 지정합니다.  

        -   **설명** 상자에서 부팅 이미지의 사용 방법에 관한 간단한 설명을 지정합니다.  

    6.  마법사를 완료합니다.  

9. 부팅 이미지에서 명령 셸을 사용하도록 설정하여 Windows PE에서 해당 이미지를 디버그하고 문제를 해결할 수 있습니다. 다음 절차에 따라 명령 셸을 사용하도록 설정할 수 있습니다.  

    1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

    2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

    3.  목록에서 새 부팅 이미지를 찾아서 해당 이미지의 패키지 ID를 확인합니다. 부팅 이미지의 **이미지 ID** 열에서 패키지 ID를 찾아볼 수 있습니다.  

    4.  명령 프롬프트에서 **wbemtest** 를 입력하여 Windows Management Instrumentation 테스터를 엽니다.  

    5.  **네임스페이스**에 **\\\\<***SMS 공급자 컴퓨터***>\root\sms\site_<***사이트 코드***>**>를 입력하고 **연결**을 클릭합니다.  

    6.  **인스턴스 열기**를 클릭하고 **sms_bootimagepackage.packageID="<패키지 ID\>"**를 입력한 후 **확인**을 클릭합니다. 패키지ID의 경우, 3단계에서 확인한 값을 입력합니다.  

    7.  **개체 새로 고침**을 클릭한 후 **속성** 창에서 **EnableLabShell** 을 클릭합니다.  

    8.  **속성 편집**을 클릭하고 값을 **TRUE**로 변경한 다음 **속성 저장**을 클릭합니다.  

    9. **개체 저장**을 클릭한 다음 WMI 테스터를 종료합니다.  

10. 작업 순서에서 부팅 이미지를 사용하려면 먼저 부팅 이미지를 배포 지점, 배포 지점 그룹 또는 배포 지점 그룹과 연결된 컬렉션에 배포해야 합니다. 다음 절차에 따라 부팅 이미지를 배포할 수 있습니다.  

    1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

    2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

    3.  3단계에서 확인한 부팅 이미지를 클릭합니다.  

    4.  **홈** 탭의 **배포** 그룹에서 **배포 지점 업데이트**를 클릭합니다.  

## <a name="customize-a-boot-image-that-uses-windows-pe-31"></a>Windows PE 3.1을 사용하는 부팅 이미지 사용자 지정  
 WinPE 3.1을 사용하는 부팅 이미지를 사용자 지정하려면 Windows AIK를 설치하고, Windows 7 SP1용 Windows AIK 추가 기능을 설치하고, DISM 명령줄 도구를 사용하여 부팅 이미지를 탑재하고, 선택적 구성 요소 및 드라이버를 추가하고, 부팅 이미지의 변경 사항을 커밋해야 합니다. 다음 절차에 따라 부팅 이미지를 사용자 지정할 수 있습니다.  

#### <a name="to-customize-a-boot-image-that-uses-windows-pe-31"></a>Windows PE 3.1을 사용하는 부팅 이미지를 사용자 지정하려면  

1.  다른 버전의 Windows AIK 또는 Windows ADK와 어떤 Configuration Manager 구성 요소도 설치되어 있지 않은 컴퓨터에 Windows AIK를 설치합니다. [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=5753)에서 Windows AIK를 다운로드합니다.  

2.  Windows 7 SP1용 Windows AIK 추가 기능을 1단계의 컴퓨터에 설치합니다. [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=5188)에서 Windows 7 SP1용 Windows AIK 추가 기능을 다운로드합니다.  

3.  Windows AIK 설치 폴더(예: <*설치 경로*>\Windows AIK\Tools\PETools\amd64\\)에서 부팅 이미지를 사용자 지정할 컴퓨터의 폴더로 부팅 이미지(wimpe.wim)를 복사합니다. 이 절차에서는 C:\WinPEWAIK를 폴더 이름으로 사용합니다.  

4.  DISM을 사용하여 부팅 이미지를 로컬 Windows PE 폴더에 탑재합니다. 예를 들어, 다음 명령줄을 입력합니다.  

     **dism.exe /mount-wim /wimfile:C:\WinPEWAIK\winpe.wim /index:1 /mountdir:C:\WinPEMount**  

     여기서 C:\WinPEWAIK는 부팅 이미지가 포함된 폴더이고, C:\WinPEMount는 탑재된 폴더입니다.  

    > [!NOTE]
    >  DISM에 대한 자세한 내용은 Windows 7 TechNet 문서 라이브러리의 [배포 이미지 서비스 및 관리 기술 참조](http://technet.microsoft.com/library/dd744256\(v=ws.10\).aspx)를 참조하세요.  

5.  부팅 이미지를 탑재한 후 DISM을 사용하여 부팅 이미지에 선택적 구성 요소를 추가합니다. 예를 들어 Windows PE 3.1에서 선택적 구성 요소는 <*설치 경로*>\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\에 있습니다.  

    > [!NOTE]
    >  이 절차에서는 선택적 구성 요소에 대해 C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs 위치를 사용합니다. 사용하는 경로는 Windows AIK에 대해 선택하는 버전 및 설치 옵션에 따라 달라집니다.  

     선택적 구성 요소를 설치하려면 다음을 입력하세요.  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wmi.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-scripting.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\winpe-wds-tools.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<로캘\>* **\winpe-wmi_** *<로캘\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<로캘\>* **\winpe-scripting_** *<로캘\>* **.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\\** *<로캘\>* **\winpe-wds-tools_** *<로캘\>* **.cab"**  

     여기서 C:\WinPEMount는 탑재된 폴더이고 로캘은 구성 요소의 로캘입니다. 예를 들어 **ko-kr** 로캘의 경우 다음과 같이 입력합니다.  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wmi_en-us.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-scripting_en-us.cab"**  

     **dism.exe /image:C:\WinPEMount /add-package /packagepath:"C:\Program Files\Windows AIK\Tools\PETools\amd64\WinPE_FPs\en-us\winpe-wds-tools_en-us.cab"**  

    > [!TIP]
    >  부팅 이미지에 추가할 수 있는 여러 패키지에 대한 자세한 내용은 Windows 7 TechNet 문서 라이브러리의 [Windows PE 이미지에 패키지 추가](http://technet.microsoft.com/library/dd799312\(v=WS.10\).aspx)를 참조하세요.  

6.  필요한 경우 DISM을 사용하여 특정 드라이버를 부팅 이미지에 추가합니다. 필요한 경우 다음을 입력하여 부팅 이미지에 드라이버를 추가하세요.  

     **dism.exe /image:C:\WinPEMount /add-driver /driver:&lt;** *드라이버 .inf 파일의 경로* **>**  

     여기서 C:\WinPEMount는 탑재된 폴더입니다.  

7.  다음을 입력하여 부팅 이미지 파일을 분리하고 변경 사항을 커밋합니다.  

     **dism.exe /unmount-wim /mountdir:C:\WinPEMount /commit**  

     여기서 C:\WinPEMount는 탑재된 폴더입니다.  

8.  업데이트된 부팅 이미지를 Configuration Manager에 추가하여 작업 순서에서 사용 가능하도록 설정합니다. 다음 절차에 따라 업데이트된 부팅 이미지를 가져올 수 있습니다.  

    1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

    2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

    3.  **홈** 탭의 **만들기** 그룹에서 **부팅 이미지 추가** 를 클릭하여 부팅 이미지 추가 마법사를 시작합니다.  

    4.  **데이터 원본** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.  

        -   **경로** 상자에서 업데이트된 부팅 이미지 파일의 경로를 지정합니다. 지정하는 경로는 UNC 형식의 유효한 네트워크 경로여야 합니다. 예를 들어 **\\\\<***servername***>\\<***WinPEWAIK 공유***>\winpe.wim**과 같습니다.  

        -   **부팅 이미지** 드롭다운 목록에서 부팅 이미지를 선택합니다. WIM 파일에 여러 부팅 이미지가 포함되어 있는 경우 각 이미지가 나열됩니다.  

    5.  **일반** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.  

        -   **이름** 상자에서 부팅 이미지의 고유한 이름을 지정합니다.  

        -   **버전** 상자에서 부팅 이미지의 버전 번호를 지정합니다.  

        -   **설명** 상자에서 부팅 이미지의 사용 방법에 관한 간단한 설명을 지정합니다.  

    6.  마법사를 완료합니다.  

9. 부팅 이미지에서 명령 셸을 사용하도록 설정하여 Windows PE에서 해당 이미지를 디버그하고 문제를 해결할 수 있습니다. 다음 절차에 따라 명령 셸을 사용하도록 설정할 수 있습니다.  

    1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

    2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

    3.  목록에서 새 부팅 이미지를 찾아서 해당 이미지의 패키지 ID를 확인합니다. 부팅 이미지의 **이미지 ID** 열에서 패키지 ID를 찾아볼 수 있습니다.  

    4.  명령 프롬프트에서 **wbemtest** 를 입력하여 Windows Management Instrumentation 테스터를 엽니다.  

    5.  **네임스페이스**에 **\\\\<***SMS 공급자 컴퓨터***>\root\sms\site_<***사이트 코드***>**>를 입력하고 **연결**을 클릭합니다.  

    6.  **인스턴스 열기**를 클릭하고 **sms_bootimagepackage.packageID="<패키지 ID\>"**를 입력한 후 **확인**을 클릭합니다. 패키지ID의 경우, 3단계에서 확인한 값을 입력합니다.  

    7.  **개체 새로 고침**을 클릭한 후 **속성** 창에서 **EnableLabShell** 을 클릭합니다.  

    8.  **속성 편집**을 클릭하고 값을 **TRUE**로 변경한 다음 **속성 저장**을 클릭합니다.  

    9. **개체 저장**을 클릭한 다음 WMI 테스터를 종료합니다.  

10. 작업 순서에서 부팅 이미지를 사용하려면 먼저 부팅 이미지를 배포 지점, 배포 지점 그룹 또는 배포 지점 그룹과 연결된 컬렉션에 배포해야 합니다. 다음 절차에 따라 부팅 이미지를 배포할 수 있습니다.  

    1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.  

    2.  **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장한 다음 **부팅 이미지**를 클릭합니다.  

    3.  3단계에서 확인한 부팅 이미지를 클릭합니다.  

    4.  **홈** 탭의 **배포** 그룹에서 **배포 지점 업데이트**를 클릭합니다.  



<!--HONumber=Jan17_HO4-->


