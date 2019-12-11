---
title: 패키지 정의 파일
titleSuffix: Configuration Manager
description: 패키지 정의 파일을 사용 하 여 Configuration Manager 패키지 및 프로그램을 만드는 방법에 대해 알아봅니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 2de963d7-ffb9-43c3-9e1d-fc992b67bebd
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: ba927286e79d88a6e034fd7eb14f5190cb1f34d6
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "68537681"
---
# <a name="package-definition-files"></a>패키지 정의 파일

*적용 대상: System Center Configuration Manager(현재 분기)*

패키지 정의 파일은 Configuration Manager의 [패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs) 만들기를 자동화 하는 데 도움이 되는 스크립트입니다. 이 스크립트는 Configuration Manager에서 패키지 및 프로그램을 만들기 위해 필요한 모든 정보(패키지 원본 파일의 위치 제외)를 제공합니다.

## <a name="about-the-package-definition-file-format"></a>패키지 정의 파일 형식 정보

각 패키지 정의 파일은 .ini 파일 형식을 사용 하는 ASCII 또는 UTF-8 텍스트 파일입니다. 여기에는 다음과 같은 섹션이 포함되어 있습니다.  

### <a name="pdf"></a>[PDF]

이 섹션의 파일 패키지 정의 파일을 식별합니다. 다음 정보를 포함 합니다.  

- **Version**: 파일이 사용하는 패키지 정의 파일 형식의 버전을 지정합니다. 이 버전은 작성 된 Configuration Manager 버전에 해당 합니다. 필수이 항목이입니다.  

### <a name="package-definition"></a>[패키지 정의]

패키지와 프로그램의 속성을 지정합니다. 다음 정보를 제공합니다.  

- **이름**: 최대 50 자, 패키지의 이름입니다.  

- **Version**(선택 사항): 최대 32자의 패키지 버전입니다.  

- **Icon**(선택 사항): 이 패키지에 사용할 아이콘이 있는 파일입니다. 지정된 경우 Configuration Manager 콘솔의 기본 패키지 아이콘이 이 아이콘으로 교체됩니다.

- **게시자**: 최대 32 자까지 패키지의 게시자입니다.

- **언어**: 최대 32 자까지 패키지의 언어 버전입니다.

- **Comment**(선택 사항): 패키지에 대한 최대 127자의 주석입니다.

- **ContainsNoFiles**:이 항목은 패키지에 원본 파일이 있는지 여부를 나타냅니다.  

- **프로그램**:이 패키지에 대해 정의 하는 프로그램입니다. 각 프로그램 이름에 해당 하는 **[프로그램]** 이 패키지 정의 파일의 섹션입니다.  

    예제:  

    `Programs=Typical, Custom, Uninstall`  

- **MIFFileName**: 최대 50 자는 패키지 상태를 포함 하는 관리 정보 형식 (MIF) 파일의 이름입니다.  

- **MIFName**: MIF 매칭을 위한 패키지 이름으로 최대 50자입니다.  

- **MIFVersion**: MIF 매칭을 위한 패키지의 버전 번호로 최대 32자입니다.  

- **MIFPublisher**: MIF 매칭을 위한 패키지의 소프트웨어 게시자로 최대 32자입니다.  

### <a name="program"></a>[프로그램]

**[패키지 정의]** 섹션의 **프로그램** 항목에서 지정한 각 프로그램에 대해 [program] 섹션을 포함 합니다. 이 섹션에서는 각 프로그램을 정의 합니다. 각 프로그램 섹션에서 다음 정보를 제공합니다.  

- **이름**: 최대 50 자 프로그램의 이름입니다. 이 항목은 패키지 내에서 고유 해야 합니다.  

- **Icon**(선택 사항): 이 프로그램에 사용할 아이콘이 있는 파일을 지정합니다. 이 아이콘은 Configuration Manager 콘솔의 기본 프로그램 아이콘을 대체 합니다. 클라이언트는 컬렉션에 프로그램을 배포 하는 경우에도이 아이콘을 표시 합니다.

- **Comment**(선택 사항): 프로그램에 대한 최대 127자의 주석입니다.

- **CommandLine**: 프로그램에 대한 최대 127자의 명령줄을 지정합니다. 패키지 원본 폴더를 기준으로 명령이입니다.

- **StartIn**: 프로그램의 작업 폴더를 최대 127자로 지정합니다. 이 항목은 클라이언트 컴퓨터의 절대 경로이거나 패키지 원본 폴더의 상대 경로일 수 있습니다.

- **Run**: 프로그램이 실행되는 프로그램 모드를 지정합니다. 지정할 수 있습니다 **최소화**, **최대화**, 또는 **숨김**. 이 항목을 포함 하지 않으면 프로그램은 표준 모드로 실행 됩니다.  

- **AfterRunning**: 프로그램이 성공적으로 완료된 후 발생하는 특별한 동작을 지정합니다. 사용 가능한 옵션은 **SMSRestart**, **ProgramRestart**, 또는 **SMSLogoff**. 이 항목을 포함 하지 않으면 프로그램에서 특수 한 작업을 실행 하지 않습니다.  

- **EstimatedDiskSpace**: 컴퓨터에서 소프트웨어 프로그램을 실행하는 데 필요한 디스크 공간의 크기를 지정합니다. 기본값은 **알 수 없음**입니다. 0 보다 크거나 같은 정수 값을 설정할 수 있습니다. 값을 지정 하는 경우 값의 단위도 포함 합니다.  

    예제:  

    `EstimatedDiskSpace=38MB`  

- **EstimatedRunTime**: 클라이언트 컴퓨터에서 프로그램이 실행될 것으로 예상하는 기간(분)을 지정합니다. 기본값은 **120**입니다. 값은 0 보다 큰 정수 또는 **알 수 없음**으로 설정할 수 있습니다.  

    예제:  

    `EstimatedRunTime=25`  

- **SupportedClients**: 이 프로그램이 실행되는 프로세서 및 운영 체제를 지정합니다. 플랫폼을 쉼표로 구분 합니다. 이 항목을 포함 하지 않으면 클라이언트는이 프로그램에 대해 지원 되는 플랫폼을 확인 하지 않습니다.  

- **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: **SupportedClients** 항목에서 지정된 운영 체제에 대한 버전 번호의 시작-끝 범위를 지정합니다.  

    예제:  

    ```INI
    SupportedClients=Win NT (I386),Win NT (IA64),Win NT (x64)  
    Win NT (I386) MinVersion1=5.00.2195.4  
    Win NT (I386) MaxVersion1=5.00.2195.4  
    Win NT (I386) MinVersion2=5.10.2600.2  
    Win NT (I386) MaxVersion2=5.10.2600.2  
    Win NT (I386) MinVersion3=5.20.0000.0  
    Win NT (I386) MaxVersion3=5.20.9999.9999  
    Win NT (I386) MinVersion4=5.20.3790.0  
    Win NT (I386) MaxVersion4=5.20.3790.2  
    Win NT (I386) MinVersion5=6.00.0000.0  
    Win NT (I386) MaxVersion5=6.00.9999.9999  
    Win NT (IA64) MinVersion1=5.20.0000.0  
    Win NT (IA64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion1=5.20.0000.0  
    Win NT (x64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion2=5.20.3790.0  
    Win NT (x64) MaxVersion2=5.20.9999.9999  
    Win NT (x64) MinVersion3=5.20.3790.0  
    Win NT (x64) MaxVersion3=5.20.3790.2  
    Win NT (x64) MinVersion4=6.00.0000.0  
    Win NT (x64) MaxVersion4=6.00.9999.9999
    ```  

- **AdditionalProgramRequirements**(선택 사항): 클라이언트 컴퓨터에 대한 다른 정보 또는 요구 사항을 최대 127자로 제공합니다.

- **CanRunWhen**: 클라이언트 컴퓨터에서 프로그램을 실행하는 데 필요한 사용자 상태를 지정합니다. 사용 가능한 값은 **UserLoggedOn**, **NoUserLoggedOn**, 또는 **AnyUserStatus**. 기본값은 **UserLoggedOn**.  

- **UserInputRequired**: 프로그램에 사용자의 조작이 필요한지 여부를 지정합니다. 사용 가능한 값은 **True** 또는 **False**. 기본값은 **True**. 이 항목은 **CanRunWhen**이 **UserLoggedOn**으로 설정되지 않은 경우 **False**로 설정됩니다.  

- **AdminRightsRequired**: 컴퓨터에서 프로그램을 실행하는 데 관리자 자격 증명이 필요한지 여부를 지정합니다. 사용 가능한 값은 **True** 또는 **False**. 기본값은 **False**입니다. 이 항목은 **CanRunWhen**이 **UserLoggedOn**으로 설정되지 않은 경우 **True**로 설정됩니다.  

- **UseInstallAccount**: 클라이언트 컴퓨터에서 프로그램을 실행할 때 클라이언트 소프트웨어 설치 계정을 사용할지 여부를 지정합니다. 이 값은 기본적으로 **False**. 또한이 값은 **False** 경우 **CanRunWhen** 로 설정 된 **UserLoggedOn**.  

- **DriveLetterConnection**: 프로그램에서 배포 지점의 패키지 파일에 대한 드라이브 문자 연결이 필요한지 여부를 지정합니다. 지정할 수 있습니다 **True** 또는 **False**. 기본값은 **False**이며, 이는 프로그램이 UNC(범용 명명 규칙) 연결을 사용할 수 있도록 합니다. 이 값이 **True**로 설정된 경우 클라이언트는 사용 가능한 다음 드라이브 문자를 사용합니다(Z:로 시작해서 역방향으로 진행).  

- **SpecifyDrive**(선택 사항): 프로그램이 배포 지점에서 패키지 파일에 연결하는 데 필요한 드라이브 문자를 지정합니다. 이 설정은 배포 지점에 대한 클라이언트 연결에 지정된 드라이브 문자를 강제로 사용하도록 합니다.

- **ReconnectDriveAtLogon**: 사용자가 로그온할 때 컴퓨터가 배포 지점에 다시 연결할지 여부를 지정합니다. 사용 가능한 값은 **True** 또는 **False**. 기본값은 **False**입니다.  

- **DependentProgram**: 현재 프로그램 전에 실행해야 하는 이 패키지의 프로그램을 지정합니다. 이 항목에서는 `DependentProgram=<ProgramName>`형식을 사용 합니다. 여기서 `<ProgramName>`는 패키지 정의 파일에서 해당 프로그램에 대 한 **이름** 항목입니다. 종속 프로그램 없는 경우에이 항목을 빈 둡니다.  

    예제:  

    `DependentProgram=Admin`  
    `DependentProgram=`  

- **Assignment**: 프로그램을 사용자에게 할당하는 방법을 지정합니다. 이 값은

    - **Firstuser**: 클라이언트에 로그인 하는 첫 번째 사용자만이 프로그램을 실행 합니다.
    - **Firstuser**: 로그인 하는 모든 사용자가 프로그램을 실행 합니다.

    **CanRunWhen**이 **UserLoggedOn**으로 설정되지 않은 경우 이 항목이 **FirstUser**로 설정됩니다.  

- **사용 안 함**:이 프로그램을 클라이언트에 배포할 수 있는지 여부를 지정 합니다. 사용 가능한 값은 **True** 또는 **False**. 기본값은 **False**입니다.  


## <a name="use-a-package-definition-file"></a>패키지 정의 파일 사용  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **애플리케이션 관리**를 펼치고, **패키지**를 선택합니다.  

2. 리본 메뉴에 있는 **홈** 탭의 **만들기** 그룹에서 **정의에서 패키지 만들기**를 선택합니다.  

3. **정의에서 패키지 만들기 마법사**의 **패키지 정의** 페이지에서 기존 패키지 정의 파일을 선택 합니다. 새 패키지 정의 파일을 열려면 **찾아보기**를 선택 합니다. 새 패키지 정의 파일을 지정한 후 **패키지 정의** 목록에서 선택 합니다.

4. **원본 파일** 페이지에서 패키지 및 프로그램을 위해 필요한 원본 파일에 대한 정보를 지정합니다.  

5. 패키지에 원본 파일이 필요한 경우 원본 **폴더** 페이지에서 사이트에서 원본 파일을 가져올 수 있는 위치를 지정 합니다.  

6. 마법사를 완료합니다.  


## <a name="see-also"></a>참고 항목

[패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs)
