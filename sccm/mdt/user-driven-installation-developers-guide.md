---
title: 사용자 구동 설치
titleSuffix: Microsoft Deployment Toolkit
description: 'Microsoft Deployment Toolkit 2013의 사용자 구동 설치에 대한 개발자 가이드입니다. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: a2b3a3a0-7b81-4191-b1f9-c618e59347c3
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 434178f100c32a4188ecf5283066f9332035f761
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2018
ms.locfileid: "27821087"
---
# <a name="user-driven-installation---developers-guide"></a>사용자 구동 설치 - 개발자 가이드
UDI(사용자 구동 설치)는 Microsoft® System Center 2012 R2 Configuration Manager의 OSD(운영 체제 배포) 기능을 사용하는 컴퓨터에 Windows 8.1 같은 Windows® 클라이언트 운영 체제를 간편하게 배포할 수 있도록 도와줍니다. UDI는 MDT(Microsoft Deployment Toolkit)에 포함되어 있습니다.  

## <a name="introduction"></a>소개  
 일반적으로 OSD 기능을 사용하여 운영 체제를 배포할 때 운영 체제 배포에 필요한 모든 정보를 제공해야 합니다. 이 정보는 구성 파일 또는 데이터베이스(예: CustomSettings.ini 파일 또는 MDT 데이터베이스 [MDT DB])에 구성됩니다. 배포를 시작하기 전에 모든 구성 설정을 제공해야 합니다.  

 UDI는 배포를 수행하기 전에 즉시 구성 정보를 제공할 수 있는 마법사 기반 인터페이스를 제공합니다. 이 동작을 통해 제네릭 OSD 작업 순서를 만든 다음, 배포 시 컴퓨터 관련 정보를 제공하면 배포 프로세스의 유연성을 대폭 향상할 수 있습니다.  

### <a name="target-audience"></a>대상 사용자  
 이 가이드는 UDI 마법사의 사용자 지정 페이지 및 UDI 마법사 디자이너의 사용자 지정 마법사 페이지 편집기를 만드는 개발자를 위해 작성되었습니다. 이 가이드에서는 독자가 다음을 사용하여 Windows 응용 프로그램을 개발하는 데 익숙하다고 가정합니다.  

-   사용자 지정 마법사 페이지를 만드는 데 사용되는 C++  

-   사용자 지정 마법사 페이지 편집기를 만드는 데 사용되는 Microsoft.NET Framework  

-   사용자 지정 마법사 페이지 편집기를 만드는 데 사용되는 WPF(Windows Presentation Foundation)  

-   사용자 지정 마법사 페이지 편집기를 만드는 데 사용 되는 C#, C++ 또는 Microsoft Visual Basic® .NET 같은 WPF 지원 언어  

### <a name="about-this-guide"></a>이 가이드 정보  
 이 가이드에서는 조직의 UTI를 사용자 지정하는 데 도움이 되는 필수 참조 정보를 제공합니다. 이 가이드에서는 MDT(UDI 포함) 설치, 운영 체제 및 응용 프로그램을 배포하도록 UDI 구성, UDI 마법사를 사용하여 배포 수행 등과 같은 관리 또는 운영 토픽에 대해서는 설명하지 않습니다. 이러한 토픽에 대한 자세한 내용은 MDT에 포함되어 있는 *Microsoft Deployment Toolkit 사용*의 UDI 토픽을 참조하세요.  

## <a name="udi-development-overview"></a>UDI 개발 개요  
 UDI를 개발하여 UDI에서 제공하는 기능을 확장할 수 있습니다. 일반적으로 UDI 배포 프로세스에서 사용하는 추가 정보를 수집하려는 경우에 UDI 개발이 필요합니다. 이 추가 정보는 보통 Configuration Manager의 UDI 작업 순서에 있는 작업 순서 단계에서 읽는 작업 순서 변수로 저장됩니다.  

### <a name="udi-architecture"></a>UDI 아키텍처  
 UDI 개발의 목표는 UDI 마법사에 표시할 수 있는 사용자 지정 마법사 페이지를 만드는 것입니다. 사용자 지정 마법사 페이지를 만들어서 조직의 비즈니스 및 기술 요구 사항을 충족하도록 UDI의 기존 기능을 확장할 수 있습니다. 사용자 지정 마법사 페이지는 UDI에서 제공하는 마법사 페이지에 더해서 또는 UDI에서 제공하는 마법사 페이지를 대신하여 정보를 수집합니다.  

 그림 1은 UDI 마법사 디자이너와 UDI 마법사 간의 관계를 보여줍니다.  

 ![UDIDevelopersGuide1](media/UDIDevelopersGuide1.jpg "UDIDevelopersGuide1")  
그림 1. UDI 마법사와 UDI 마법사 디자이너 간의 관계  

 **그림 1. UDI 마법사와 UDI 마법사 디자이너 간의 관계**  

 개념적 수준에서 UDI 개발에는 다음 항목 만들기가 포함됩니다.  

-   **사용자 지정 마법사 페이지**. 마법사 페이지는 UDI 마법사에 표시되며 배포 프로세스를 완료하는 데 필요한 정보를 수집합니다. Microsoft Visual Studio®에서 C++를 사용하여 마법사 페이지를 만듭니다. 사용자 지정 마법사 페이지는 UDI 마법사가 읽을 수 있는 Dll로 구현됩니다. UDI SDK(소프트웨어 개발 키트)에는 사용자 지정 마법사 페이지를 만드는 방법의 예제가 포함되어 있습니다.  

-   **사용자 지정 마법사 페이지 편집기**. 마법사 페이지 편집기를 사용하여 사용자 지정 마법사 페이지의 동작을 구성합니다. 사용자 지정 마법사 페이지 편집기는 UDI 마법사 디자이너가 읽을 수 있는 Dll로 구현됩니다. 다음 도구를 사용하여 마법사 페이지 편집기를 만듭니다.  

    -   [WPF](http://msdn.microsoft.com/library/ms754130.aspx) 버전 4.0  

    -   [Microsoft Prism](http://compositewpf.codeplex.com/) 버전 4.0  

    -   [Microsoft Unity Application Block](http://unity.codeplex.com/)(Unity) 버전 2.1  

     MDT는 UDI 마법사 디자이너에서 사용할 사용자 지정 마법사 페이지 편집기를 만드는 데 필요한 모든 어셈블리를 포함하고 있습니다. UDI SDK에는 사용자 지정 마법사 페이지 편집기를 만드는 방법의 예제가 포함되어 있습니다.  

 또한 UDI 마법사 디자이너는 지원 마법사 페이지 편집기 구성 파일을 사용합니다. 사용자 지정 마법사 페이지 및 사용자 지정 마법사 페이지 편집기를 만드는 과정의 일부로 마법사 페이지 편집기 구성 파일을 만듭니다. UDI 마법사 디자이너는 UDI 마법사 구성 파일 및 해당 .app 파일에 필요한 XML 정보를 만듭니다.  

### <a name="preparing-the-udi-development-environment"></a>UDI 개발 환경 준비  
 사용자 지정 마법사 페이지 및 마법사 페이지 편집기 만들기를 시작하려면 먼저 다음 단계를 수행하여 UDI 개발 환경을 준비해야 합니다.  

1.  [UDI 개발 환경 필수 구성 요소 준비](#PrepareUDIDevelopmentEnvironmentPrerequisites)에 설명된 대로 UDI 개발 환경 필수 구성 요소를 준비합니다.  

2.  [UDI 개발 환경 구성](#ConfigureUDIDevelopmentEnvironment)에 설명된 대로 UDI 개발 환경을 구성합니다.  

3.  [UDI 개발 환경 확인](#VerifyUDIDeploymentEnvironment)에 설명된 대로 UDI 개발 환경이 올바르게 구성되었는지 확인합니다.  

####  <a name="PrepareUDIDevelopmentEnvironmentPrerequisites"></a> UDI 개발 환경 필수 구성 요소 준비  
 UDI 개발 환경 필수 구성 요소를 준비하려면 다음 단계를 수행합니다.  

1.  [UDI 개발 환경 하드웨어 필수 구성 요소 준비](#PrepareUDIDevelopmentEnvironmentHardwarePrerequisites)에 설명된 대로 UDI 개발 환경 하드웨어 필수 구성 요소를 준비합니다.  

2.  [UDI 개발 환경 소프트웨어 필수 구성 요소 준비](#PrepareUDIDevelopmentEnvironmentSoftwarePrerequisites)에 설명된 대로 UDI 개발 환경 소프트웨어 필수 구성 요소를 준비합니다.  

#####  <a name="PrepareUDIDevelopmentEnvironmentHardwarePrerequisites"></a> UDI 개발 환경 하드웨어 필수 구성 요소 준비  
 UDI 개발 환경 하드웨어 필수 구성 요소는 사용하시는 Microsoft Visual Studio 2010 버전의 하드웨어 요구 사항과 동일합니다. 이러한 요구 사항에 대한 자세한 내용은 [Visual Studio 2010 제품](http://www.microsoft.com/visualstudio/products/2010-editions)에서 각 버전의 시스템 요구 사항을 참조하세요.  

#####  <a name="PrepareUDIDevelopmentEnvironmentSoftwarePrerequisites"></a> UDI 개발 환경 소프트웨어 필수 구성 요소 준비  
 UDI 개발 환경에는 다음과 같은 소프트웨어 필수 구성 요소가 있습니다.  

-   Visual Studio 2010에서 지원하는 Windows 운영 체제(Windows 7 또는 Windows Server® 2008 R2 권장)  

     개발하려는 프로세서 아키텍처를 지원하는 Windows 운영 체제가 필요합니다. 64비트 운영 체제를 사용하면 32비트 및 64비트 UDI 개발을 수행할 수 있습니다. 32비트 운영 체제에서는 32비트 UDI만 개발할 수 있습니다. 이러한 이유로 64비트 운영 체제를 사용해야 합니다.  

    > [!NOTE]
    >  Windows 운영 체제의 IntelItanium 버전(IA-64)은 UDI 개발 환경을 지원하지 않습니다.  

     Visual Studio 2010에서 지원하는 운영 체제에 대한 자세한 내용은 [Visual Studio 2010 제품](http://www.microsoft.com/visualstudio/products/2010-editions)에서 각 버전의 시스템 요구 사항을 참조하세요.  

-   Microsoft .NET Framework 버전 4.0(Visual Studio 2010에 필요)  

-   C++ 언어(UDI 마법사 페이지 확장에 사용되는 언어)  

-   C#, Visual Basic.NET, C++/공용 언어 인프라 등 WPF에서 지원하는 기타 언어(UDI 마법사 디자이너 마법사 페이지 편집기를 확장하는 데 사용)  

    > [!NOTE]
    >  UDI 마법사 디자이너 마법사 페이지 편집기에 대한 샘플 소스 코드는 C#으로 작성됩니다. 샘플 소스 코드를 사용하려면 C# 언어를 설치합니다.  

####  <a name="ConfigureUDIDevelopmentEnvironment"></a> UDI 개발 환경 구성  
 UDI 개발 환경 필수 구성 요소를 준비한 후에는 다음 단계를 수행하여 UDI 개발 환경을 구성합니다.  

1.  Visual Studio 2010을 설치합니다.  

     C++ 및 WPF에서 지원하는 기타 언어를 설치합니다.  

    > [!NOTE]
    >  UDI 마법사 디자이너 편집기 페이지에 대한 샘플 소스 코드는 C#으로 작성됩니다. 샘플 소스 코드를 사용하려면 C# 언어를 설치합니다.  

     Visual Studio 2010 설치에 대한 자세한 내용은 [Visual Studio 설치](http://msdn.microsoft.com/library/e2h7fzkw.aspx)를 참조하세요.  

2.  MDT를 설치합니다.  

     MDT 설치 방법에 대한 자세한 내용은 MDT 문서 *Microsoft Deployment Toolkit 사용*의 "MDT 설치 또는 MDT로 업그레이드" 섹션을 참조하세요.  

3.  Windows 탐색기에서 *local_folder*를 만듭니다(여기서 *local_folder*는 개발 컴퓨터의 로컬 드라이브에 있는 아무 폴더).  

4.  *installation_folder*\SDK 폴더를 *local_folder*로 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더이고, *local_folder*는 개발 컴퓨터의 로컬 드라이브에 있는 아무 폴더).  

     관리자 권한이 없으면 쓸 수 없는 Program Files 폴더에 MDT가 설치되어 있으므로 SDK 폴더를 다른 위치로 복사합니다. SDK 폴더를 다른 위치로 복사하면 관리자 권한 없이도 SDK 폴더의 파일을 수정할 수 있습니다.  

5.  *installation_folder*\Templates\Distribution\Tools 폴더를 *local_folder*로 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더이고, *local_folder*는 프로세스 앞부분에서 만든 폴더).  

6.  *local_folder*\Tools 폴더의 이름을 *local_folder*\OSDSetupWizard로 바꿉니다(여기서 *local_folder*는 프로세스 앞부분에서 만든 폴더).  

     여기까지 마치면 *local_folder* 아래의 폴더 구조가 그림 2의 폴더 구조와 비슷하게 보입니다(여기서 *local_folder*는 프로세스 앞부분에서 만든 폴더이며 그림에서는 *UDIDevelopment*로 표시).  

     ![UDIDevelopersGuide2](media/UDIDevelopersGuide2.jpg "UDIDevelopersGuide2")  
그림 2. UDI 개발에 대한 폴더 구조  

     **그림 2. UDI 개발에 대한 폴더 구조**  

####  <a name="VerifyUDIDeploymentEnvironment"></a> UDI 개발 환경 확인  
 UDI 개발 환경이 구성되었으면 Visual Studio 2010에서 샘플 프로젝트가 올바르게 빌드되는지 확인하여 UDI 개발 환경이 올바르게 구성되었는지 확인합니다.  

 다음 사항을 확인하여 UDI 개발 환경이 올바르게 구성되었는지 확인합니다.  

-   [SamplePage 프로젝트가 올바르게 빌드되는지 확인](#VerifySamplePageProjectBuildsCorrectly)에 설명된 대로 SamplePage 프로젝트가 올바르게 빌드되는지 여부  

-   [SampleEditor 프로젝트가 올바르게 빌드되는지 확인](#VerifySampleEditorProjectBuildsCorrectly)에 설명된 대로 SampleEditor 프로젝트가 올바르게 빌드되는지 여부  

#####  <a name="VerifySamplePageProjectBuildsCorrectly"></a> SamplePage 프로젝트가 올바르게 빌드되는지 확인  
 SamplePage 프로젝트는 UDI 마법사에 대한 사용자 지정 마법사 페이지를 만드는 방법의 예제를 제공합니다. SamplePage 프로젝트에 대한 자세한 내용은 [SamplePage Visual Studio 솔루션 검토](#ReviewSamplePageVisualStudioSolution)를 참조하세요.  

 **SamplePage 프로젝트가 올바르게 빌드되는지 확인하려면**  

1.  Visual Studio 2010을 시작합니다.  

2.  SamplePage 프로젝트를 엽니다.  

     SamplePage 프로젝트는 *local_folder*\SDK\UDI\SamplePage 폴더에 상주합니다(여기서 *local_folder*는 프로세스 앞부분에서 만든 폴더).  

3.  Visual Studio 2010의 솔루션 탐색기에서 SamplePage 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  

     **SamplePage 속성 페이지** 대화 상자가 나타납니다.  

4.  **SamplePage 속성 페이지** 대화 상자에서 구성 속성/디버깅으로 이동합니다.  

5.  디버깅 속성의 **구성** 아래에서 **모든 구성**을 선택합니다.  

6.  디버깅 속성의 **명령** 아래에 **$(TargetDir)\OSDSetupWizard.exe**를 입력합니다.  

7.  디버깅 속성의 **작업 디렉터리** 아래에 **$(TargetDir)** 를 입력합니다.  

8.  **SamplePage 속성 페이지** 대화 상자에서 Configuration Properties/Build Events/Post-Build Event로 이동합니다.  

9. 빌드 후 이벤트 속성의 **명령줄** 아래에 다음을 입력합니다.  

    ```  
    copy /y "$(ProjectDir)..\..\..\..\OSDSetupWizard\x86\*.*" "$(TargetDir)"  
    xcopy /y /i "$(ProjectDir)..\..\..\..\OSDSetupWizard\x86\en-us" "$(TargetDir)en-us"  
    copy /y "$(ProjectDir)..\..\..\..\OSDSetupWizard\OSDResults\Images\UDI_Wizard_Banner.bmp" "$(ProjectDir)header.bmp"  
    copy /y "$(ProjectDir)Config.xml" "$(TargetDir)”  
    copy /y "$(ProjectDir)header.bmp" "$(TargetDir)header.bmp"  
    ```  

10. **SamplePage 속성 페이지** 대화 상자에서 **확인**을 클릭합니다.  

11. 프로젝트를 저장합니다.  

12. **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.  

     소스가 오래 되었음을 알리고 프로젝트를 빌드할 것인지 묻는 **Microsoft Visual Studio** 대화 상자가 나타납니다.  

13. **Microsoft Visual Studio** 대화 상자에서 **예**를 클릭합니다.  

     OSDSetupWizard.exe에 사용할 수 있는 디버깅 정보가 없음을 알리는 **디버깅 정보 없음** 대화 상자가 나타납니다.  

14. **디버깅 정보 없음** 대화 상자에서 **예**를 클릭합니다.  

     사용자 지정 마법사 페이지가 표시된 UDI 마법사가 열립니다.  

15. **위치 선택**에서 값을 선택할 수 있는지 확인합니다.  

16. **샘플 페이지가 포함된 마법사** 양식에서 **취소**를 클릭합니다.  

     **마법사 취소** 대화 상자가 나타납니다.  

17. **마법사 취소** 대화 상자에서 **예**를 클릭합니다.  

18. Visual Studio 2010을 닫습니다.  

#####  <a name="VerifySampleEditorProjectBuildsCorrectly"></a> SampleEditor 프로젝트가 올바르게 빌드되는지 확인  
 SampleEditor 프로젝트는 UDI 마법사 디자이너에 대한 사용자 지정 마법사 페이지 편집기를 만드는 방법의 예제를 제공합니다. SampleEditor 프로젝트에 대한 자세한 내용은 [SamplePage Visual Studio 솔루션 검토](#ReviewSamplePageVisualStudioSolution)를 참조하세요.  

 **SampleEditor 프로젝트가 올바르게 빌드되는지 확인하려면**  

1.  Visual Studio 2010을 시작합니다.  

2.  SampleEditor 프로젝트를 엽니다.  

     SampleEditor 프로젝트는 *local_folder*\SDK\UDI\SampleEditor 폴더에 상주합니다(여기서 *local_folder*는 프로세스 앞부분에서 만든 폴더).  

3.  Visual Studio 2010의 솔루션 탐색기에서 SampleEditor 프로젝트를 선택합니다.  

4.  **프로젝트** 메뉴에서 **참조 추가**를 클릭합니다.  

     **참조 추가** 대화 상자가 열립니다.  

5.  **참조 추가** 대화 상자에서 **찾아보기** 탭을 클릭합니다.  

6.  **찾아보기** 탭에서 *installation_folder*\Bin으로 이동합니다(여기서 *installation_folder*는 MDT를 설치한 폴더). 다음 파일을 선택하고 **확인**을 클릭합니다.  

    -   Microsoft.Enterprise.UDIDesigner.Common.dll  

    -   Microsoft.Enterprise.UDIDesigner.DataService.dll  

    -   Microsoft.Enterprise.UDIDesigner.Infrastructure.dll  

    -   Microsoft.Practices.Prism.dll  

    -   Microsoft.Practices.ServiceLocation.dll  

    -   Microsoft.Practices.Unity.dll  

    -   RibbonControlsLibrary.dll  

    > [!NOTE]
    >  CTRL 키를 누른 상태로 파일을 클릭하여 **찾아보기** 탭에서 여러 파일을 선택할 수 있습니다.  

7.  솔루션 탐색기에서 SampleEditor/References로 이동합니다.  

8.  참조에 경고 또는 오류가 없는지 확인합니다.  

9. 솔루션 탐색기에서 SampleEditor 프로젝트를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  

     **SampleEditor 속성 페이지** 대화 상자가 나타납니다.  

10. **SampleEditor 속성 페이지** 대화 상자에서 **디버그** 탭을 클릭합니다.  

11. **디버그** 탭에서 **외부 프로그램 시작**을 클릭합니다.  

12. **외부 프로그램 시작**에서 ***installation_folder\Bin\UDIDesigner.exe***를 입력하고(여기서 *installation_folder*는 MDT를 설치한 폴더) **확인**을 클릭합니다.  

    > [!TIP]
    >  줄임표(...) 단추를 클릭하여 폴더를 찾아서 UDIDesigner.exe를 선택할 수 있습니다.  

13. **파일** 메뉴에서 **모두 저장**을 클릭합니다.  

14. *local_folder*\SDK\SamplePage\SamplePage.dll.config 파일을 *installation_folder*\Bin\Config 폴더로 복사합니다(여기서 *local_folder*는 구성 프로세스 앞부분에서 개발 컴퓨터에 만든 폴더이고, *installation_folder*는 MDT를 설치한 폴더).  

15. Visual Studio 2010의 **디버그** 메뉴에서 **디버깅 시작**을 클릭합니다.  

     UDI 마법사 디자이너가 시작됩니다.  

16. UDI 마법사 디자이너의 리본에서 **열기**를 클릭합니다.  

     **열기** 대화 상자가 나타납니다.  

17. **열기** 대화 상자에서 *local_folder*\SDK\SamplePage\SamplePage\Config.xml 파일을 엽니다(여기서 *local_folder*는 구성 프로세스의 앞부분에서 개발 컴퓨터에 만든 폴더).  

     Config.xml 파일이 열리고, 세부 정보 창에 사용자 지정 [StageGroup](#StageGroup)이 표시됩니다.  

18. 세부 정보 창에서 **구성** 탭을 클릭합니다.  

19. 다음을 포함하여 **위치** 상자에 대한 구성 정보를 검토합니다.  

    -   **위치** 상자를 설정 또는 해제하는 데 사용되는 **잠금 해제됨** 단추  

    -   **위치** 상자에 표시될 기본값을 입력하는 **기본값** 상자  

    -   **요약** 페이지에 표시되는 정보의 자막을 입력하는 **요약 페이지에 보이는 표시 이름**  

    -   가능한 위치 목록을 포함하고 있는 **위치** 목록 상자  

20. UDI 마법사 디자이너를 닫습니다.  

21. Visual Studio 2010을 닫습니다.  

## <a name="reviewing-the-udi-sdk-examples"></a>UDI SDK 예제 검토  
 개발을 시작하기 전에 UDI SDK에 제공된 예제를 검토합니다. 사용자 고유의 UDI 사용자 지정 마법사 페이지 및 마법사 페이지 편집기를 만드는 방법을 안내하는 이 가이드의 정보와 예제의 소스 코드를 사용합니다.  

 다음을 검토하여 UDI SDK 예제를 살펴봅니다.  

-   [SDK 폴더의 내용 검토](#ReviewContentsofSDKFolder)에 설명된 대로 설치 프로세스의 앞부분에서 복사한 SDK 폴더의 내용  

-   [SamplePage Visual Studio 솔루션 검토](#ReviewSamplePageVisualStudioSolution)에 설명된 사용자 지정 UDI 마법사 페이지 예제  

-   [SampleEditor Visual Studio 솔루션 검토](#ReviewSampleEditorVisualStudioSolution)에 설명된 사용자 지정 UDI 마법사 페이지 편집기 예제  

###  <a name="ReviewContentsofSDKFolder"></a> SDK 폴더의 내용 검토  
 UDI 개발 환경을 구성하는 동안 MDT를 설치한 폴더의 SDK 폴더를 사용자가 만든 다른 폴더로 복사했습니다. 표 1에는 SDK 폴더 바로 아래에 있는 폴더와 각 폴더에 대한 간략한 설명이 나와 있습니다.  

### <a name="table-1-folders-in-the-udi-sdk"></a>표 1. UDI SDK의 폴더  

|**폴더**|**이 폴더의 내용**|  
|-|-|  
|포함된 항목|UDI 마법사에 대한 사용자 지정 마법사 페이지를 만드는 데 필요한 C++ 헤더 파일|  
|라이브러리|사용자 지정 페이지에 연결될 C++ 라이브러리 파일. 정적 링크 라이브러리의 32비트 및 64비트 버전이 있습니다. **참고:** 라이브러리의 Itanium 버전(IA-64)은 사용할 수 없습니다.|  
|SampleEditor|UDI 마법사 디자이너에서 SamplePage 페이지를 편집하는 데 사용되는 사용자 지정 편집기를 빌드하기 위한 Visual Studio 프로젝트(C#으로 작성)|  
|SamplePage|사용자 지정 UDI 마법사 페이지를 빌드하기 위한 Visual Studio 프로젝트(Visual C++로 작성)|  

###  <a name="ReviewSamplePageVisualStudioSolution"></a> SamplePage Visual Studio 솔루션 검토  
 사용자 지정 마법사 페이지 및 마법사 페이지 편집기 만들기를 시작하려면 먼저 다음 작업을 수행하여 UDI 개발 환경을 준비해야 합니다.  

-   [마법사 페이지 수명 주기 검토](#ReviewWizardPageLifeCycle)에 설명된 대로 UDI 마법사 페이지의 수명 주기 단계를 검토합니다.  

-   [SamplePage 예제 검토](#ReviewSamplePageExample)에 설명된 대로 UDI SDK의 SamplePage 예제에 대한 Visual Studio 솔루션을 검토합니다.  

####  <a name="ReviewWizardPageLifeCycle"></a> 마법사 페이지 수명 주기 검토  
 UDI 마법사 페이지에는 페이지의 각 수명 주기 단계에 해당하는 메서드가 있습니다. 사용자 지정 마법사 페이지 만들기의 일부로 이러한 메서드를 사용자 코드로 재정의해야 합니다. 표 2에는 사용자가 재정의해야 하는 메서드가 나열되어 있으며, 마법사 페이지 수명 주기에서 메서드를 사용하는 시기를 포함하여 각 메서드에 대한 간략한 설명도 제공됩니다.  

### <a name="table-2-methods-in-a-wizard-page-life-cycle"></a>표 2. 마법사 페이지 수명 주기의 메서드  

|**방법**|**설명**|  
|-|-|  
|**OnWindowCreated**|이 메서드는 페이지의 창이 만들어진 후 한 번 호출됩니다.<br /><br /> 이 메서드의 경우 페이지를 처음으로 초기화하고 한 번만 수행하면 되는 코드를 작성해야 합니다. 예를 들어 이 메서드를 사용하여 필드를 초기화하거나 UDI 마법사 구성 파일의 **Setter** 요소에서 구성 정보를 읽습니다.|  
|**OnWindowShown**|이 메서드는 UDI 마법사에서 페이지가 표시될 때마다 호출됩니다. 페이지가 처음으로 표시될 때 그리고 사용자가 마법사에서 **다음** 또는 **뒤로**를 클릭하여 페이지를 이동할 때마다 호출됩니다.<br /><br /> 이 메서드의 경우 페이지를 표시할 준비를 하는 코드를 작성해야 합니다. 예를 들어 메모리 변수, 작업 순서 변수 또는 환경 변수를 읽은 후 이러한 변수의 변경 내용에 따라 페이지를 업데이트합니다.|  
|**OnCommonControlEvent**|이 메서드는 마법사 페이지가 표시되고 자식(일반적으로 공통 컨트롤)으로부터 WM_NOTIFY 메시지를 받을 때 언제든지 호출할 수 있습니다 .<br /><br /> 이 메서드의 경우 알림 메시지에 따라 WM_NOTIFY를 처리하는 코드를 작성해야 합니다. 예를 **TreeView** 컨트롤에 대한 클릭 또는 두 번 클릭 이벤트에 응답하는 것처럼 공통 컨트롤의 이벤트에 응답할 수 있습니다.|  
|**OnUnhandledEvent**|이 메서드는 마법사 페이지에 대한 처리되지 않은 창 메시지가 발생할 때 호출됩니다. 이 메서드는 이러한 창 메시지를 가로채어 처리할 수 있는 기회를 제공합니다.<br /><br /> 이 메서드의 경우 마법사 페이지에 적합한 창 메시지를 처리하는 코드를 작성해야 합니다. 일반적으로 이 메서드를 재정의할 필요는 없습니다.|  
|**OnNextClicked**|이 메서드는 마법사에서 **다음**을 클릭할 때 호출됩니다.<br /><br /> 이 메서드의 경우 마법사의 그 다음 페이지로 이동하기 전에 필요한 작업을 수행하는 코드를 작성해야 합니다. 예를 들어 시간이 오래 걸릴 수 있는 유효성 검사를 수행합니다. 유효성 검사가 실패하면 **다음** 요청을 취소하고 메시지를 표시할 수 있습니다.|  
|**OnWindowHidden**|이 메서드는 이전 또는 다음 마법사 페이지가 표시되고 페이지가 숨김 처리될 때마다 호출됩니다.<br /><br /> 이 메서드의 경우 페이지가 숨김 처리되기 전에, 다른 페이지가 표시되기에 앞서 작업을 수행하는 코드를 작성해야 합니다. 일반적으로 이 메서드를 재정의할 필요는 없습니다.|  

####  <a name="ReviewSamplePageExample"></a> SamplePage 예제 검토  
 SamplePage 예제의 마법사 페이지 수명 주기 동안 이벤트 시퀀스를 나타내는 다음 목록을 사용하여 SamplePage 예제를 검토합니다.  

1.  [1단계: UDI 마법사(OSDSetupWizard.exe)가 Config.xml 파일 읽기](#UDIWizardReadstheConfigFile)에 설명된 대로 UDI 마법사 OSDSetupWizard.exe가 예제(Config.xml 파일)의 UDI 마법사 구성 파일에서 구성 정보를 읽습니다.  

2.  [2단계: UDI 마법사가 사용자 지정 마법사 페이지에 대한 DLL 로드](#UDIWizardLoadstheDLLforCustomWizardPage)에 설명된 대로 UDI 마법사가 UDI 마법사 구성 파일에 나열된 각 마법사 페이지에 필요한 Dll을 로드합니다.  

3.  [3단계: UDI 마법사가 사용자 지정 마법사 페이지 표시](#UDIWizardDisplaysCustomWizardPage)에 설명된 대로 UDI 마법사가 사용자 지정 마법사 페이지를 표시하고 원하는 컨트롤 상호 작용을 허용합니다.  

4.  사용자 지정 마법사 페이지에서 정보를 수집한 후에는 필요한 작업을 수행하고, [4단계: 사용자 지정 마법사 페이지에서 다음 단추를 클릭](#TheNextButtonisClickedinCustomWizardPage)에 설명된 대로 **다음**을 클릭하여 마법사의 그 다음 단계를 진행합니다.  

#####  <a name="UDIWizardReadstheConfigFile"></a> 1단계: UDI 마법사(OSDSetupWizard.exe)가 Config.xml 파일 읽기  
 UDI 마법사(OSDSetupWizard.exe)는 시작되면 기본적으로 UDI 마법사 구성 파일을 읽습니다. 이 파일은 UDI 마법사의 기본 구성 파일인 UDIWizard_Config.xml 파일입니다.  

> [!NOTE]
>  이 예제에서는 구성 파일로 Config.xml 파일을 사용합니다. MDT에서 기본 구성 파일은 구성에 대한 MDT 파일 패키지의 스크립트 폴더에 있는 UDIWizard_Config.xml 파일입니다.  

 **/definition** 매개 변수를 사용하도록 UDI 마법사 작업 순서 단계를 수정하여 UDI 마법사가 사용하는 기본 구성 파일을 재정의할 수 있습니다. UDI 마법사가 사용하는 기본 구성 파일을 재정의하는 방법에 대한 자세한 내용은 "UDI 마법사가 사용하는 구성 파일 재정의"를 참조하세요.  

 Config.xml 파일의 최상위 요소는 다음과 같습니다.  

-   [DLLs](#DLLs) 요소  

-   [Style](#Style) 요소  

-   [Pages](#Pages) 요소  

-   [StageGroups](#StageGroups) 요소  

 UDI 마법사 구성 파일의 스키마 및 각 요소에 대한 자세한 내용은 [UDI 마법사 구성 파일 스키마 참조](#UDIWizardConfigurationFileSchemaReference)를 참조하세요.  

 UDI 마법사는 **DLLs** 요소를 검사하여 로드할 .dll 파일을 찾습니다. 이 예제에서는 두 개의 .dll 파일 SamplePage.dll 및 SharedPages.dll 파일이 나열되어 있습니다. 두 .dll 파일은 OSDSetupWizard.exe와 같은 폴더인 Tools\\*platform* 폴더에 있어야 합니다(*플랫폼*은 32비트 버전인 경우 x86, 64비트 버전인 경우 x64).  

 UDI 마법사는 **Pages** 요소를 검사하여 정의된 페이지를 찾습니다. 이 예제에서는 두 개의 페이지 **사용자 지정** 및 **SummaryPage** 페이지가 정의되었습니다. **Page** 요소의 **Type** 특성은 PageClassIDs.h 파일에 정의되어 있으며 사용자 지정 페이지의 형식을 고유하게 정의합니다.  

 이 예제에서 정의된 형식은 **Microsoft.SamplePage.LocationPage**입니다. 본인의 사용자 지정 페이지에서, 나중에 만드는 다른 페이지와 충돌하지 않도록 다음 항목을 바꿉니다.  

-   **Microsoft** 대신 해당 조직 이름.  

-   **SamplePage** 대신 해당 프로젝트 이름.  

-   **LocationPage** 대신 사용자 지정 마법사 페이지 이름.  

#####  <a name="UDIWizardLoadstheDLLforCustomWizardPage"></a> 2단계: UDI 마법사가 사용자 지정 마법사 페이지에 대한 DLL 로드  
 UDI 마법사는 DLL을 로드할 때 **RegisterFactories** 함수를 호출하며, 이 함수는 .dll 파일에서 구현해야 합니다. 이 예제에서 이 함수는 dllmain.ccp 파일에 구현되었습니다. 사용자가 만드는 각 마법사 페이지에서 **RegisterFactories** 함수를 구현해야 합니다.  

 **RegisterFactories** 함수는 마법사 페이지의 팩터리 클래스를 UDI 마법사의 클래스 팩터리 레지스트리에 등록하는 데 사용됩니다. *클래스 팩터리*는 또 다른 클래스 인스턴스를 만들 수 있는 클래스입니다. **RegisterFactories** 함수는 팩터리 클래스의 새 인스턴스를 만들어서 UDI 마법사의 클래스 팩터리 레지스트리에 해당 클래스를 전달하며, 이를 통해 마법사에서 해당 팩터리 클래스를 사용할 수 있게 됩니다. UDI 마법사는 사용자 지정 마법사 페이지에 대한 **Page** 요소의 **Type** 특성과 일치하는 ID에 등록된 팩터리 클래스를 찾습니다.  

 이 예제의 ID는 PageClassIds.h 파일의 **ID_Location**으로써 **Microsoft.SamplePage.LocationPage**로 정의되며, Config.xml 파일의 **Page** 요소에 대한 **Type** 특성과 일치합니다. **ID_Location**은 dllmain.ccp 파일에 구현된 **RegisterFactories** 함수의 매개 변수로 전달됩니다.  

 Register_*name* 함수 템플릿을 사용하여 함수를 만들면 간편하게 새 팩터리 인스턴스를 만들고 새로 만든 인스턴스를 등록할 수 있습니다. Register 함수 템플릿을 사용하여 제공된 **이름** 값은 **iClassFactory** 인터페이스를 구현해야 합니다. [ClassFactoryImpl 클래스](#ClassFactoryImplClass)는 클래스 팩터리를 구현하기 위한 세부 정보를 대부분 처리합니다.  

 또한 **RegisterFactories** 함수를 사용하여 작업 형식을 등록하고 형식의 유효성을 검사할 수 있습니다. 자세한 내용은 다음을 참조하세요.  

-   [사용자 지정 UDI 작업 만들기](#CreatingCustomUDITasks)  

-   [사용자 지정 UDI 유효성 검사기 만들기](#CreatingCustomUDIValidators)  

> [!NOTE]
>  이 예제는 오직 하나의 사용자 지정 마법사 페이지만 포함하고 등록합니다. 이 예제는 사용자 지정 작업 또는 유효성 검사기를 포함하고 있지 않으므로 사용자 지정 작업 또는 유효성 검사기를 등록하지 않습니다.  

#####  <a name="UDIWizardDisplaysCustomWizardPage"></a> 3단계: UDI 마법사가 사용자 지정 마법사 페이지 표시  
 예제의 사용자 지정 마법사 페이지는 LocationPage.cpp 파일에 정의됩니다. 마법사 페이지는 페이지의 여러 가지 기능을 제공하는 템플릿 클래스에서 파생됩니다. 모든 마법사 페이지는 [IWizardPage 인터페이스](#IWizardPageInterface)를 구현하는 [WizardPageImpl 템플릿 클래스](#WizardPageImplTemplateClass)에서 파생되어야 합니다. 각 마법사 페이지는 해당 요구 사항에 따라 다른 선택적 템플릿 클래스 및 해당 인터페이스를 구현할 수 있습니다.  

 [WizardPageImpl 템플릿 클래스](#WizardPageImplTemplateClass)는 사용자 지정 마법사 페이지를 작성하는 데 도움이 되는 여러 유용한 인터페이스를 제공합니다. 사용자 지정 마법사 페이지의 기본 클래스로 [WizardPageImpl 템플릿 클래스](#WizardPageImplTemplateClass)를 구현하세요.  

 사용 가능한 목록:  

-   마법사 페이지에 대한 템플릿 클래스는 [마법사 페이지 도우미 클래스](#WizardPageHelperClasses)를 참조하세요.  

-   마법사 페이지 템플릿 클래스에 대한 인터페이스는 [마법사 페이지 인터페이스](#WizardPageInterfaces)를 참조하세요.  

 이 예제의 사용자 지정 마법사 페이지는 [WizardPageImpl 템플릿 클래스](#WizardPageImplTemplateClass)에서 파생되며 [IWizardPage 인터페이스](#IWizardPageInterface)를 구현합니다. 또한 사용자 지정 마법사 페이지는 **IFieldCallback** 인터페이스를 구현합니다. 둘 다 LocationPage.cpp 파일에 구현됩니다.  

 예제 사용자 지정 마법사 페이지는 다음 메서드를 재정의합니다.  

-   **OnWindowCreated**. 예제 마법사 페이지의 **OnWindowCreated** 메서드는 다음 메서드를 호출합니다.  

    -   [AddField](#AddField). 이 메서드는 **Location**이라는 [Data](#Data) 요소가 Config.xml 파일에 있는 **IDD_LOCATION_PAGE** 리소스의 **IDC_COMBO_LOCATION** 상자 컨트롤과 관련이 있습니다.  

         **AddField** 메서드 외에도 [AddRadioGroup](#AddRadioGroup) 및 [AddToGroup](#AddToGroup) 메서드를 사용하여 다른 컨트롤과 동작을 지원할 수 있습니다.  

        > [!NOTE]
        >  [InitFields](#InitFields) 메서드를 호출하기 전에 [AddField](#AddField), [AddRadioGroup](#AddRadioGroup) 또는 [AddToGroup](#AddToGroup) 메서드를 호출해야 합니다.  

    -   [InitFields](#InitFields). 양식에 추가한 필드(컨트롤)를 초기화하려면 이 메서드를 사용합니다. 페이지의 포인터는 매개 변수입니다. 이 예제에서는 현재 페이지를 참조하는 **이** 포인터가 전달됩니다.  

        > [!NOTE]
        >  **이** 포인터를 사용할 수 있도록 지원하려면 [WizardPageImpl 템플릿 클래스](#WizardPageImplTemplateClass)가 지원하는 인터페이스 외에도 **IFieldCallback** 인터페이스를 구현해야 합니다.  

         **IFieldCallback** 인터페이스는 텍스트 상자 및 확인란 컨트롤 이외의 컨트롤에 대한 기본값을 설정하는 데 사용되는 **SetFieldDefault** 메서드를 호출합니다. 예제의 **SetFieldDefault** 메서드는 Config.xml 파일의 [Field](#Field) 요소에 대한 **Default** 요소에 지정된 기본값을 기반으로 콤보 상자 컨트롤의 초기 인덱스를 설정합니다.  

     **OnWindowCreated** 메서드는 [IFormController 인터페이스](#IFormController-Interface)를 사용하여 양식 컨트롤러를 설정합니다. 양식 컨트롤러 설정에 대한 자세한 내용은 [양식 설정](#SettingUptheForm)을 참조하세요.  

-   **InitLocations**. 이 메서드는 Config.xml 파일에서 위치 목록의 콤보 상자를 채웁니다. Confg.xml 파일의 [Data](#Data) 요소 및 자식 [DataItem](#DataItem) 요소는 사용 가능한 값 목록을 제공합니다.  

-   **OnNextClicked**. 이 메서드는 다음 작업을 수행합니다.  

    -   **TSLocation** 작업 순서 변수를 **SaveFields** 메서드를 사용하여 콤보 상자에서 선택한 값으로 업데이트합니다.  

    -   **SaveFields** 메서드를 사용하여 **요약** 페이지에 표시될 정보를 추가합니다.  

#####  <a name="TheNextButtonisClickedinCustomWizardPage"></a> 4단계: 사용자 지정 마법사 페이지에서 다음 단추를 클릭  
 사용자가 사용자 지정 마법사 페이지의 필드를 완료하고 **다음**을 클릭하면 **OnNextClicked** 메서드가 호출됩니다. **OnNextClicked** 메서드는 사용자 지정 마법사 페이지의 구성 변경 내용을 기록하는 등 마법사 페이지의 그 다음 페이지로 넘어가기 위해 필요한 작업을 수행합니다.  

 예제 사용자 지정 마법사 페이지에서는 **OnNextClicked** 메서드의 재정의가 LocationPage.ccp 파일에 구현되었습니다. 예제 사용자 지정 마법사 페이지의 **OnNextClicked** 메서드에서 다음 메서드가 호출됩니다.  

1.  [InitSection](#InitSection). 이 메서드는 **요약** 페이지에 표시되는 요약 데이터의 헤더(레이블 캡션)를 초기화합니다. 일반적으로 **DisplayName()** 함수를 사용하여 이 값을 설정할 수 있습니다. 이 캡션과 연결된 데이터는 [SaveFields](#SaveFields) 메서드를 사용하여 저장됩니다.  

2.  [SaveFields](#SaveFields). 이 메서드는 작업 순서 변수 및 **요약** 페이지에 표시되는 데이터에 필드 값을 저장합니다.  

###  <a name="ReviewSampleEditorVisualStudioSolution"></a> SampleEditor Visual Studio 솔루션 검토  
 사용자 지정 마법사 페이지 및 마법사 페이지 편집기 만들기를 시작하려면 먼저 다음 단계를 수행하여 UDI 개발 환경을 준비해야 합니다.  

-   [UDI 마법사 디자이너 아키텍처 검토](#ReviewUDIWizardDesignerArchitecture)에 설명된 대로 UDI 마법사 디자이너의 아키텍처를 검토합니다.  

-   [UDI 마법사 페이지의 구성 가능한 구성 요소 검토](#ReviewConfigurableComponentsofUDIWizardPage)에 설명된 대로 UDI 마법사 구성 파일을 사용하여 사용자 지정 가능한 UDI 마법사 페이지의 구성 요소를 검토합니다.  

-   [EditorPage 예제 검토](#ReviewEditorPageExample)에 설명된 대로 UDI SDK에 제공된 EditorPage 예제를 검토합니다.  

####  <a name="ReviewUDIWizardDesignerArchitecture"></a> UDI 마법사 디자이너 아키텍처 검토  
 UDI 마법사 디자이너는 WPF, Prism 및 Unity를 사용하여 개발되었습니다. UDI 디자이너는 런타임에 UDI 마법사가 읽는 UDI 마법사 구성 파일(UDIWizard_Config.xml)을 편집하는 데 사용됩니다. UDI 마법사 구성 파일의 [Pages](#Pages) 요소에는 각 마법사 페이지에 대한 별도의 [Page](#Page) 요소를 포함하는 페이지 목록이 들어 있습니다.  

 마법사 페이지의 구성 설정을 편집하면 UDI 마법사 디자이너는 마법사 페이지 형식에 해당하는 사용자 지정 페이지 편집기를 로드합니다. 사용자 지정 마법사 페이지 편집기는 WPF 사용자 정의 컨트롤로 개발되었습니다. 사용자 지정 마법사 페이지 편집기는 WPF에 [MVVM(Model–View–ViewModel)](http://msdn.microsoft.com/magazine/dd419663.aspx) 디자인 패턴을 사용합니다.  

 MVVM 디자인 패턴은 표시되는 데이터에서 사용자 인터페이스(UI; 프레젠테이션)를 분리하는 데 도움이 됩니다. 데이터는 UDI 마법사 구성 파일(예제의 Config.xml 파일)의 [Page](#Page) 요소에 대한 외관으로, [IDataService](#IDataService) 인터페이스의 [CurrentPage](#CurrentPage) 속성을 사용하여 액세스됩니다.  

 UDI 마법사 디자이너는 **DependencyAttribute**를 사용하여 Unity의 종속성 주입 프레임워크에 따라 **DataService** 클래스에 대한 액세스 권한을 획득합니다. Unity의 종속성 주입 프레임워크에 대한 자세한 내용은 [응용 프로그램에 수명 주입 - Unity Application Block 알아보기](http://msdn.microsoft.com/library/ff650806.aspx)를 참조하세요.  

####  <a name="ReviewConfigurableComponentsofUDIWizardPage"></a> UDI 마법사 페이지의 구성 가능한 구성 요소 검토  
 사용자 지정 마법사 페이지를 만들 때 일부 구성 설정이 코드에서 설정되고 페이지를 컴파일한 후 변경하지 못하게 될 수 있습니다. 하지만 다른 구성 설정의 경우 UDI 마법사 디자이너를 사용하여 변경할 수 있도록 허용해야 합니다.  

 일반적으로 UDI 마법사 디자이너를 사용하여 구성하려는 구성 설정은 UDI 마법사 구성 파일(이 예제에서는 Config.xml 파일)에 저장됩니다. 하지만 필요한 경우 별도의 구성 파일을 만들 수도 있습니다. 별도의 구성 파일을 사용하는 한 가지 예로는 **응용 프로그램 검색** 작업 및 **ApplicationPage** 마법사 페이지 형식에서 사용하는 UDIWizard_Config.xml.app 파일이 있습니다.  

 다음은 UDI 마법사 디자이너를 사용하여 관리할 수 있는 일반적인 구성 설정 목록입니다.  

-   **Field**. 사용자가 입력을 제공할 수 있도록 허용하려면 필드를 사용합니다. 필드는 UDI 마법사 구성 파일 (UDIWizard_Config.xml)에서 각 필드에 대한 구성 설정을 포함하는 [Field](#Field) 요소로 표시됩니다. 해당 마법사 페이지 편집기는 [FieldElementControl](#FieldElementControl)을 사용하여 필드의 필드 구성 설정을 편집하는 메서드를 제공해야 합니다.  

-   **속성**. Setter는 [Page](#Page) 요소의 페이지, [Field](#Field) 요소의 필드, [Data](#Data) 또는 [DataItem](#DataItem) 요소의 데이터처럼 페이지의 항목에 대한 속성 만들기를 도와줍니다. [Setter]() 요소에서 속성을 구성합니다. 정의하려는 각 속성에 대한 별도의 [Setter]() 요소를 추가합니다. [SetterControl](#SetterControl)을 사용하여 속성을 편집하고 다른 컨트롤을 사용하여 다른 [Setter]() 요소를 구성합니다.  

-   **데이터**. 데이터는 마법사 페이지 및 기타 구성 요소에서 사용하는 정보를 저장하는 데 사용됩니다. [Data](#Data) 또는 [DataItem](#DataItem) 요소를 사용하여 페이지 또는 필드에 대한 데이터를 정의할 수 있습니다. 데이터는 [Data](#Data) 또는 [DataItem](#DataItem) 요소의 적절한 사용을 통해 플랫 구조 또는 계층 구조로 정의할 수 있습니다. SDK의 예제에 나오는 Config.xml은 플랫 데이터 구조를 빌드하는 방법을 보여줍니다.  

 만드는 사용자 지정 마법사 페이지 편집기가 이러한 구성 설정을 관리할 수 있어야 합니다.  

####  <a name="ReviewEditorPageExample"></a> EditorPage 예제 검토  
 EditorPage 예제는 UDI 마법사 구성 파일의 **SamplePage** 마법사 페이지에 대한 구성 설정을 구성하는 데 사용됩니다. EditorPage 예제에는 다음과 같은 기본 구성 요소가 있습니다.  

-   **위치** 콤보 상자 설정을 구성하는 UI  

-   **위치** 콤보 상자에 표시되는 사용 가능 위치 목록에 위치를 추가하거나 편집하는 UI  

-   UDI 마법사 구성 파일에서 읽고 저장하는 구성 설정  

-   다른 구성 요소에 대한 지원 코드  

 다음 단계를 수행하여 Visual Studio에서 EditorPage 예제를 검토합니다.  

1.  [마법사 페이지 편집기 로드 및 초기화 검토](#ReviewWizardPageEditorLoadingInitialization)에 설명된 대로 UDI 마법사 디자이너에서 **SampleEditor** 마법사 페이지 편집기가 로드되고 초기화되는 방식을 검토합니다.  

2.  [위치 콤보 상자를 구성하는 데 사용되는 사용자 인터페이스 검토](#ReviewUserInterfaceUsedtoConfigureLocationComboBox)에 설명된 대로 LocationPageEditor.xaml 및 LocationPageEditor.xaml.cs 파일의 **위치** 콤보 상자를 편집하는 데 사용되는 UI를 검토합니다.  

3.  [사용 가능한 위치 목록을 수정하는 데 사용되는 사용자 인터페이스 검토](#ReviewUserInterfaceUsedtoModifyListofPossibleLocations)에 설명된 대로 AddEditLocationView.xaml 및 AddEditLocationView.xaml.cs 파일의 목록에 위치를 추가하거나 위치를 편집하는 데 사용되는 UI를 검토합니다.  

4.  [구성 정보를 관리하는 데 사용되는 코드 검토](#ReviewCodeUsedtoManageConfigurationInformation)에 설명된 대로 UDI 마법사 구성 파일에 저장된 구성 정보를 관리하는 데 사용되는 코드를 검토합니다.  

#####  <a name="ReviewWizardPageEditorLoadingInitialization"></a> 마법사 페이지 편집기 로드 및 초기화 검토  
 사용자 지정 마법사 페이지 편집기는 UDI 마법사 디자이너의 요구에 따라 로드됩니다. UDI 마법사 디자이너 구성 파일은 UDI 마법사 디자이너가 시작될 때 로드됩니다. UDI 마법사 디자이너는 .config 파일 확장이 있는 파일의 *install_folder*\Bin\Config 폴더(여기서 *install_folder*는 MDT가 설치된 폴더의 이름)를 검사합니다.  

 우리는 UDI 개발 환경을 구성하는 동안 SamplePage.dll.confg 파일을 *install_folder*\Bin\Config 폴더에 복사했습니다. UDI 마법사 디자이너를 시작하면 SamplePage.dll.confg 파일이 검색되어 로드됩니다.  

 UDI 마법사 디자이너는 SamplePage.dll.confg 파일에 있는 [Page](#Page) 요소의 다음 특성을 사용하여 EditorPage 예제를 로드하고 초기화합니다.  

-   **DesignerAssembly**. 이 특성은 로드할 DLL의 이름을 결정합니다. 이 DLL은 UDIDesigner.exe 파일과 같은 폴더, 즉 *install_folder*\Bin에 배치해야 합니다(여기서 *install_folder*는 MDT가 설치된 폴더의 이름).  

-   **DesignerType**. 이 특성은 WPF 사용자 정의 컨트롤을 포함하는 클래스의 Microsoft .NET 형식 이름입니다.  

-   **유형**. 이 특성은 UDI 마법사가 로드하는 사용자 지정 마법사 페이지의 페이지 형식을 구성하는 데 사용됩니다. UDI 마법사 디자이너는 이 특성을 사용하여 UDI 마법사 구성 파일에서 적절한 [Page](#Page) 요소를 찾습니다.  

-   **Dll**. 이 특성은 UDI 마법사 구성 파일에서 [DLL](#DLL) 요소를 구성하는 데 사용되며, 이 요소는 UDI 마법사 디자이너에서 만듭니다.  

-   **설명**. 마법사 페이지 편집기에 대한 정보를 제공하려면 이 특성을 사용합니다. 이 특성의 값은 "페이지 라이브러리"에 마법사 페이지를 추가하는 데 사용되는 UDI 마법사 디자이너의 **새 페이지 추가** 대화 상자에 표시됩니다.  

-   **DisplayName**. UDI 마법사 디자이너에 표시되는 사용자 지정 마법사 페이지의 이름을 제공하려면 이 특성을 사용합니다. 이 특성의 값은 "페이지 라이브러리"에 마법사 페이지를 추가하는 데 사용되는 UDI 마법사 디자이너의 **새 페이지 추가** 대화 상자에 표시됩니다.  

     예제에서 **SamplePage** 사용자 지정 마법사 페이지의 형식은 **Microsoft.SamplePage.LocationPage**이며 Config.xml 파일에 저장됩니다. Config.xml 파일은 *local_folder*\SDK\SamplePage\SamplePage 폴더에 있습니다(여기서 *local_folder*는 구성 프로세스의 앞부분에서 개발 컴퓨터에 만든 폴더).  

#####  <a name="ReviewUserInterfaceUsedtoConfigureLocationComboBox"></a> 위치 콤보 상자를 구성하는 데 사용되는 사용자 인터페이스 검토  
 마법사 페이지 편집기가 로드되고 초기화되면 **Microsoft.SamplePage.LocationPage** 형식의 페이지가 편집될 때 SampleEditor 마법사 페이지 편집기가 로드됩니다. 페이지 편집기의 UI는 LocationPageEditor.xaml 파일에 저장됩니다.  

 **디자인** 탭의 UI 요소 및 **XAML** 탭의 코드를 살펴보면 그래픽 UI와 XAML(Extensible Application Markup Language)의 요소 및 특성 간 관계를 알 수 있습니다.  

 예를 들어 XAML의 **Controls:FieldElementControl** 요소를 검토하면 해당 UI의 레이아웃과 어떤 관계인지 알 수 있습니다. [FieldElementControl](#FieldElementControl) 컨트롤을 정의하려면 **Controls:FieldElementControl** 요소를 사용합니다.  

 XAML 파일의 **Binding** 매개 변수는 샘플 페이지 편집기의 필드를 UDI 마법사 구성 파일의 정보에 바인딩합니다. 예를 들어 다음 코드는 **기본값** 텍스트 상자를 UDI 마법사 구성 파일(예제에서는 Config.xml)의 [Default](#Default) 요소에 연결합니다.  

```  
<TextBox Text="{Binding FieldData.DefaultValue,  
 UpdateSourceTrigger=PropertyChanged,  
 Mode=TwoWay}"/>  
```  

 자세한 내용은 [방법: 데이터를 XAML로 바인딩하는 방법](http://msdn.microsoft.com/library/ms748857.aspx)을 참조하세요.  

 그리드 보기에서 사용 가능한 위치 목록을 편집하려면 XAML의 **Views:CollectionTControl.ColumnCollectionView** 요소를 사용합니다. [CollectionTControl](#CollectionTControl) 컨트롤을 사용하여 그리드 보기를 표시하고 UDI 구성 파일에서 **Location**이라는 이름의 [Data](#Data) 요소에 그리드 보기를 바인딩합니다.  

#####  <a name="ReviewUserInterfaceUsedtoModifyListofPossibleLocations"></a> 사용 가능한 위치 목록을 수정하는 데 사용되는 사용자 인터페이스 검토  
 사용 가능한 위치 목록을 수정하는 데 사용되는 UI는 다음으로 구성됩니다.  

-   [위치 목록을 수정하는 데 사용되는 상황에 맞는 메뉴 및 리본 단추 검토](#ReviewContextSensitiveMenuandRibbonButtons)에 설명된 대로 위치 목록의 항목을 추가, 편집, 제거 또는 순서를 변경할 수 있는 상황에 맞는 메뉴  

-   [위치를 추가 또는 편집하는 데 사용되는 대화 상자 검토](#ReviewDialogBoxforAddingEditingLocations)에 설명된 대로 위치 목록에 항목을 추가하거나 항목을 편집하기로 선택하면 초기화되는 대화 상자  

######  <a name="ReviewContextSensitiveMenuandRibbonButtons"></a> 위치 목록을 수정하는 데 사용되는 상황에 맞는 메뉴 및 리본 단추 검토  
 위치 목록을 포함하고 있는 목록 상자를 마우스 오른쪽 단추로 클릭하면 상황에 맞는 메뉴가 표시됩니다. 리본에는 동일한 작업을 수행할 수 있는 해당 단추가 있습니다. LocationPageEditor.xaml 파일의 **Views:CollectionsTControl** 컨트롤 요소는 다음과 같이 수행되는 작업 및 사용자가 설정하는 속성에 따라 호출되는 메서드를 정의합니다.  

-   **SelectedItem**. 이 데이터 바인딩된 속성은 사용자가 목록에서 항목을 선택하면 활성화됩니다. 이 속성은 보기 모델의 **CurrentLocation** 속성에 연결됩니다. LocationPageEditorViewModel.cs 파일에 있으며, [CollectionTControl](#CollectionTControl) 컨트롤은 사용자가 기존 항목을 편집 또는 제거할 때 선택한 항목을 전달하는 데 이 속성을 사용합니다.  

-   **AddItemAction**. 이 작업은 사용자가 상황에 맞는 메뉴의 **항목 추가** 옵션 또는 리본의 해당 단추를 클릭할 때 수행됩니다. **AddLocationAction** 개체를 반환하는 보기 모델의 속성에 데이터가 바인딩됩니다. 이 개체는 **AddLocationCallback** 메서드로, LocationPageEditorViewModel.cs 파일에 있으며 AddEditLocationView.xaml 파일의 대화 상자를 표시합니다.  

-   **EditItemAction**. 이 작업은 사용자가 상황에 맞는 메뉴의 **항목 편집** 옵션을 클릭할 때 수행됩니다. **EditLocationAction** 개체를 반환하는 보기 모델의 속성에 데이터가 바인딩됩니다. 이 개체는 **EditLocationCallback** 메서드로, LocationPageEditorViewModel.cs 파일에 있으며 AddEditLocationView.xaml 파일의 대화 상자를 표시합니다.  

-   **RemoveAction**. 이 작업은 사용자가 상황에 맞는 메뉴의 **항목 제거** 옵션을 클릭할 때 수행됩니다. **RemoveAction** 개체를 반환하는 보기 모델의 속성에 데이터가 바인딩됩니다. 이 개체는 **EditLocationCallback** 메서드로, LocationPageEditorViewModel.cs 파일에 있으며 위치 삭제를 확인하는 메시지를 표시합니다.  

######  <a name="ReviewDialogBoxforAddingEditingLocations"></a> 위치를 추가 또는 편집하는 데 사용되는 대화 상자 검토  
 위치 목록에 새 위치를 추가하거나 기존 위치를 편집하는 경우 AddEditLocationView.xaml 파일에 있는 메시지가 표시됩니다. 이 메시지는 LocationPageEditorViewModel.cs 파일의 [ShowDialogWindow](#ShowDialogWindow) 창 메서드를 사용하여 표시됩니다.  

 AddEditLocationView.xaml 파일의 UI는 다음으로 구성됩니다.  

-   다음과 같은 요소를 포함하는 **DialogFrame**이라는 대화 상자 프레임:  

    -   대화 프레임의 **DialogTitle** 특성을 사용하여 구성하는 제목  

    -   **Approved** 속성이 **True**인 경우에 대한 반환 상태를 설정하는 **확인** 단추(LocationPageEditorViewModel.cs 파일의 **AddLocationCallback** 메서드에서 반환 상태를 확인하여 사용자가 **확인**을 클릭했는지 확인.)  

    -   **Approved** 속성이 **False**인 경우에 대한 반환 상태를 설정하는 **Cancel** 단추(LocationPageEditorViewModel.cs 파일의 **AddLocationCallback** 메서드에서 반환 상태를 확인하여 사용자가 **취소**를 클릭했는지 확인.)  

-   다음을 포함하는 WPF 요소:  

    -   **콘텐츠** 특성을 사용하여 구성하는 레이블  

    -   UDI 구성 파일(이 예제에서는 Config.xml 파일)에서 **Location**이라는 이름의 [Data](#Data) 요소에 바인딩되는 텍스트 상자  

######  <a name="ReviewCodeUsedtoManageConfigurationInformation"></a> 구성 정보를 관리하는 데 사용되는 코드 검토  
 사용자 지정 마법사 페이지에 대한 구성 정보는 UDI 마법사 구성 파일에 저장되며, 다음과 같습니다.  

-   UDI SDK와 함께 제공되는 예제의 Config.xml 파일(이 파일은 예제의 구성 설정만 포함)  

-   MDT와 함께 제공되고 *installation_folder*\Templates\Distribution\Scripts 폴더에 저장되는 UDIWizard_Config.xml 파일(여기서 *installation_folder*는 MDT를 설치한 폴더). 이 파일에는 모든 기본 제공 마법사 페이지 및 단계에 대한 구성 설정이 포함됩니다.  

 SampleEditor 예제에서, **Locations** 루틴은 구성 정보를 관리하는 데 도움이 되며 LocationPageEditorViewModel.cs 파일에 있습니다. **Locations** 루틴은 UDI 마법사 구성 파일의 위치 목록을 반환합니다. 구체적으로 말하면, 반환된 목록에는 UDI 마법사 구성 파일의 각 [DataItem](#DataItem) 요소가 포함됩니다.  

## <a name="creating-custom-udi-wizard-pages"></a>사용자 지정 UDI 마법사 페이지 만들기  
 사용자 지정 UDI 마법사 페이지를 만드는 대략적인 프로세스는 다음과 같습니다.  

1.  시작점으로 SamplePage 솔루션의 복사본을 만듭니다.  

2.  양식에 원하는 컨트롤(필드)을 배치합니다.  

3.  다음 단계를 포함하여 마법사 페이지가 로드(**OnWindowCreated** 메서드에 대한 재정의)될 때 적절한 작업을 수행하는 코드를 작성합니다.  

    1.  양식을 초기화합니다.  

    2.  메모리 변수, 작업 순서 변수, 환경 변수 또는 XML 파일 정보(예: **Setter** 속성)를 읽습니다.  

4.  다음 단계를 포함하여 페이지가 표시(**OnWindowShown** 메서드에 대한 재정의)될 때 적절한 작업을 수행하는 코드를 작성합니다.  

    1.  3단계에서 페이지가 로드될 때 읽은 정보에 따라 컨트롤을 사용하도록 또는 사용하지 않도록 설정합니다.  

    2.  읽은 정보에 따라 컨트롤 채우기처럼 3단계에서 페이지가 로드될 때 읽은 정보에 따라 컨트롤을 업데이트합니다.  

5.  사용자가 마법사 페이지와 상호 작용할 때 적절한 작업을 수행하는 코드를 작성합니다.  

6.  다음 단계를 포함하여 사용자가 UDI 마법사에서 **다음**을 클릭(**OnNextClicked** 메서드에 대한 재정의)할 때 적절한 작업을 수행하는 코드를 작성합니다.  

    1.  메모리 변수, 작업 순서 변수, 환경 변수 또는 XML 파일 정보를 업데이트합니다.  

    2.  요약 페이지 정보를 업데이트합니다(페이지의 필드에서 수행되지 않은 경우).  

7.  솔루션을 빌드합니다.  

     만드는 DLL 버전이 설치되는 MDT와 동일한 프로세서 플랫폼이어야 합니다. 구체적으로 말해서, Windows PE(Windows 사전 설치 환경)용 프로세서 플랫폼이어야 합니다. UDI 마법사는 다음 위치에서 실행할 수 있습니다.  

    -   **대상 컴퓨터의 기존 운영 체제**. 32비트 또는 64비트 Windows 운영 체제에서 마법사 페이지의 32비트 버전을 실행할 수 있습니다. 하지만 64비트 Windows 운영 체제에서는 마법사 페이지의 64비트 버전만 실행할 수 있습니다.  

    -   **대상 컴퓨터의 Windows PE**. Windows PE는 64비트 버전의 Windows PE에서 32비트 응용 프로그램을 실행하는 것을 지원하지 않습니다. 따라서 사용하려는 Windows PE의 각 프로세서 아키텍처에 대한 마법사 페이지 버전을 빌드해 두었어야 합니다.  

8.  사용자 지정 마법사 페이지의 DLL을 *installation_folder*\Templates\Distribution\Tools\ 플랫폼 폴더에 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더이고, *플랫폼*은 32비트 버전인 경우 **x86**, 64비트 버전인 경우 **x64**).  

9. 사용자 지정 페이지 편집기를 만드는 단계를 완료합니다.  

## <a name="creating-custom-wizard-page-editors"></a>사용자 지정 마법사 페이지 편집기 만들기  
 사용자 지정 UDI 마법사 페이지 편집기를 만드는 대략적인 프로세스는 다음과 같습니다.  

1.  시작점으로 SampleEditor 솔루션의 복사본을 만듭니다.  

2.  .xaml 파일에서 기본 페이지 편집기 UI를 만듭니다.  

3.  구성할 마법사 페이지의 요구 사항에 따라 [FieldElementControl](#FieldElementControl) 컨트롤의 인스턴스를 추가합니다(필요한 경우).  

4.  구성할 마법사 페이지의 요구 사항에 따라 [SetterControl](#SetterControl) 컨트롤의 인스턴스를 추가합니다(필요한 경우).  

5.  구성할 마법사 페이지의 요구 사항에 따라 [CollectionTControl](#CollectionTControl) 컨트롤의 인스턴스를 추가합니다(필요한 경우).  

6.  [IDataService](#IDataService) 인터페이스를 추가합니다.  

7.  사용자 지정 마법사 페이지 편집기를 사용하여 구성할 구성 설정에 따라 UDI 마법사 구성 파일을 업데이트하는 적절한 코드를 작성합니다.  

8.  .xaml 파일에서 자식 대화 상자를 만들고, 구성할 마법사 페이지의 요구 사항에 따라 [IMessageBoxService](#IMessageBoxService) 인터페이스를 사용하여 기본 페이지 편집기에서 자식 대화 상자를 호출합니다.  

9. 구성할 마법사 페이지의 요구 사항에 따라 UDI 마법사 디자이너 리본에 적절한 인터페이스를 추가합니다.  

10. 솔루션을 빌드합니다.  

    > [!NOTE]
    >  만드는 DLL 버전이 설치되는 MDT와 동일한 프로세서 플랫폼이어야 합니다. 예를 들어 64비트 버전의 MDT를 설치하는 경우 64비트 버전의 사용자 지정 페이지 편집기를 빌드해야 합니다.  

11. 해당 마법사 페이지(이 예제에서는 SamplePage.dll.config 파일)를 사용하여 필요한 Dll을 로드하고 마법사 페이지 편집기를 매핑할 UDI 마법사 디자이너 구성 파일을 만듭니다.  

     마법사 페이지와 마법사 페이지 편집기 사이의 매핑을 수행하는 데 필요한 요소에 대한 자세한 내용은 [DesignerMappings](#DesignerMappings) 요소, 자식 요소 및 해당 특성을 참조하세요.  

12. 이전 단계에서 만든 UDI 마법사 디자이너 구성 파일을 *installation_folder*\Bin\Config 폴더에 복사합니다(여기서 *installation_folder*는 MDT 버전을 설치한 폴더).  

13. 사용자 지정 마법사 페이지 편집기의 DLL을 *installation_folder*\Bin 폴더로 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더).  

##  <a name="CreatingCustomUDITasks"></a> 사용자 지정 UDI 작업 만들기  
 *UDI 작업*은 C++로 작성된 DLL이며 [ITask 인터페이스](#ITaskinterface)를 구현합니다. 사용자는 UDI 마법사 디자이너 구성 파일(.config 파일)을 만들고 *installation_folder*\Bin\Config 폴더에 배치하여 UDI 마법사 디자이너 작업 라이브러리에 DLL을 등록합니다(여기서 *installation_folder*는 MDT를 설치한 폴더).  

> [!NOTE]
>  동일한 .dll 파일 내에 마법사 페이지, 작업 및 유효성 검사기를 포함하는 DLL을 만들 수 있습니다. 마법사 페이지, 작업 및 DLL의 유효성 검사기에 대한 구성 설정을 포함하는 단일 UDI 마법사 디자이너 구성 파일(.config)도 만들 수 있습니다.  

 **사용자 지정 UDI 작업을 만들려면**  

1.  [ITask 인터페이스](#ITaskinterface) 및 다음 메서드를 구현하는 코드를 작성합니다.  

    -   [Init](#Init). 이 메서드는 작업을 초기화하기 위해 호출됩니다.  

    -   [Execute](#Execute). 이 메서드는 작업을 실행하기 위해 호출됩니다.  

2.  사용자 지정 작업 클래스 팩터리를 팩터리 레지스트리에 등록하는 코드를 작성합니다.  

3.  사용자 지정 작업에 대한 솔루션을 빌드합니다.  

    > [!NOTE]
    >  만드는 DLL 버전이 설치되는 MDT와 동일한 프로세서 플랫폼이어야 합니다. 예를 들어 64비트 버전의 MDT를 설치하는 경우 64비트 버전의 사용자 지정 UDI 작업을 빌드해야 합니다.  

4.  다음 예제와 비슷하게 UDI 마법사 디자이너 구성 파일의 [TaskLibrary](#TaskLibrary) 요소 아래에서 [Task](#Task) 요소를 만듭니다.  

    ```  
    <Task DLL="OSDRefreshWizard.dll" Description="Discovers supported applications for install." Type="Microsoft.OSDRefresh.AppDiscoveryTask" Name="Application Discovery">  
       <TaskItem Type="Setter" Name="Status Bitmap">  
          <Param Name="BitmapFilename"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Log File">  
          <Param Name="log"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Write Configuration File">  
          <Param Name="writecfg"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Read Configuration File">  
          <Param Name="readcfg"/>  
       </TaskItem>  
    </Task>  
    ```  

    > [!NOTE]
    >  모든 [Task](#Task) 요소는 **BitmapFilename** 매개 변수를 포함해야 합니다. 작업에서 요구하는 그 외의 모든 매개 변수를 지정합니다. 예를 들어 이전 예제에서 **log** 매개 변수는 로그 파일의 위치에 대한 매개 변수를 지정하는 데 사용됩니다.  

5.  이전 단계에서 만든 UDI 마법사 디자이너 구성 파일을 *installation_folder*\Bin\Config 폴더에 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더).  

6.  사용자 지정 작업의 DLL을 *installation_folder*\Templates\Distribution\Tools\ 플랫폼 폴더에 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더이고, *플랫폼*은 32비트 버전인 경우 **x86**, 64비트 버전인 경우 **x64**).  

##  <a name="CreatingCustomUDIValidators"></a> 사용자 지정 UDI 유효성 검사기 만들기  
 *UDI 유효성 검사기*는 C++로 작성된 DLL이며 **IValidator** 인터페이스를 구현합니다. 사용자는 UDI 마법사 디자이너 구성 파일(.config 파일)을 만들고 *installation_folder*\Bin\Config 폴더에 배치하여 UDI 마법사 디자이너 유효성 검사기 라이브러리에 DLL을 등록합니다(여기서 *installation_folder*는 MDT를 설치한 폴더).  

 **사용자 지정 UDI 유효성 검사기를 만들려면**  

1.  **BaseValidator** 클래스의 서브클래스를 만들고 다음 메서드를 구현하는 코드를 작성합니다.  

    -   **Init(IControl \*pControl, IWizardPageContainer \*pContainer, IStringProperties \*pProperties)**. 양식 컨트롤러는 유효성 검사기를 초기화하는 **Init** 멤버를 호출합니다. 이 메서드는 **BaseValidator** 클래스에 대한 **Init** 메서드를 호출해야 합니다. 이 메서드는 일반적으로 UDI 마법사 구성 파일에서 유효성 검사기에 대해 설정된 속성을 읽습니다. 예를 들어 **InvalidCharactersValidator** 유효성 검사기는 이 메서드를 사용하여 **InvalidChars** 속성의 값을 검색합니다.  

    -   **IsValid**. 양식 컨트롤러는 컨트롤에 유효한 텍스트가 포함되어 있는지 확인하기 위해 이 메서드를 호출합니다. 다음은 필드가 비어 있지는 않은지 확인하는 유효성 검사기의 **IsValid** 메서드에 대한 예제입니다.  

        ```  
        BOOL IsValid(LPBSTR pMessage)  
        {  
            __super::IsValid(pMessage);  

            _bstr_t text;  
            m_pText->GetText(text.GetAddress());  
            return (text.length() > 0);  
        }  
        ```  

    -   **Init(IControl \*pControl, LPCTSTR message)**. 유효성 검사기가 마법사 페이지 맨 아래의 컨트롤 콘텐츠 및 업데이트된 메시지의 유효성을 검사(또는 삭제)할 수 있도록 양식 컨트롤러는 각 키 입력 및 기타 이벤트에 대해 이 멤버를 호출합니다.  

     일반적으로 이러한 메서드만 재정의하면 됩니다. 그러나 유효성 검사기에 따라, 만드는 **BaseValidator** 클래스의 서브클래스에서 다른 메서드를 재정의해야 할 수도 있습니다. 다른 메서드에 대한 자세한 내용은 **BaseValidator** 클래스를 참조하세요.  

2.  사용자 지정 작업 클래스를 레지스트리 팩터리에 등록하는 코드를 작성합니다.  

3.  사용자 지정 작업에 대한 솔루션을 빌드합니다.  

    > [!NOTE]
    >  만드는 DLL 버전이 설치되는 MDT와 동일한 프로세서 플랫폼이어야 합니다. 예를 들어 64비트 버전의 MDT를 설치하는 경우 64비트 버전의 사용자 지정 UDI 작업을 빌드해야 합니다.  

4.  다음 예제와 비슷하게 UDI 마법사 디자이너 구성 파일의 **ValidatorLibrary** 요소 아래에서 [Validator](#Validator) 요소를 만듭니다.  

    ```  
    <Validator   
    <Validator DLL="" Description="Must follow a pre-defined pattern" Type="Microsoft.Wizard.Validation.RegEx" Name="NamedPattern">  
       <Param Description="Enter the message you want displayed when the text in this field doesn't match the pattern:" Name="Message" DisplayName="Message"/>  
       <Param Description="The name of a pre-defined regular expression pattern. Must be Username, ComputerName, or Workgroup" Name="NamedPattern" DisplayName="Named Pattern"/>  
    </Validator>  
    ```  

    > [!WARNING]
    >  모든 [Validator](#Validator) 요소는 **Message** 매개 변수를 포함해야 합니다. 유효성 검사기의 요구 사항에 따라 그 외의 모든 매개 변수를 지정합니다. 예를 들어 이전 예제에서는 미리 정의된 정규식 패턴의 이름에 대한 매개 변수를 지정하기 위해 **NamedPattern** 매개 변수를 사용했습니다.  

5.  이전 단계에서 만든 UDI 마법사 디자이너 구성 파일을 *installation_folder*\Bin\Config 폴더에 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더).  

6.  사용자 지정 작업의 DLL을 *installation_folder*\Templates\Distribution\Tools\ 플랫폼 폴더에 복사합니다(여기서 *installation_folder*는 MDT를 설치한 폴더이고, *플랫폼*은 32비트 버전인 경우 **x86**, 64비트 버전인 경우 **x64**).  

## <a name="udi-wizard-reference"></a>UDI 마법사 참조  

### <a name="wizard-page-components"></a>마법사 페이지 구성 요소  
 미리 작성된 여러 구성 요소를 사용하여 사용자 지정 페이지를 빌드할 수 있습니다.  

#### <a name="creating-component-instances"></a>구성 요소 인스턴스 만들기  
 UDI 마법사는 클래스 팩터리를 사용하여 사용자 대신 개체의 새 인스턴스를 만듭니다. 이러한 팩터리는 팩터리의 키로 문자열을 사용하여 팩터리 레지스트리에 등록됩니다. 예를 들어 **WmiRepository** 구성 요소는 IWmiRepository 헤더 파일에서 **ID_WmiRepository**로 사용할 수 있는 "Microsoft.Wizard.WmiRepository," 문자열을 통해 식별됩니다.  

 **WizardPageImpl**의 서브클래스로 페이지를 작성했다고 가정할 경우 다음과 같이 **WmiRepoistory**의 새 인스턴스를 만들 수 있습니다.  

```  
PWmiRepository pWmi;  
CreateInstance(Container(), ID_WmiRepository, &pWmi);  
```  

 **CreateInstance** 함수는 형식이 안전한 템플릿 함수로 구성 요소의 새 인스턴스를 만드는 데 사용됩니다. **PWmiRepository**는 스마트 포인터이므로 사용자를 대신하여 참조 계산을 처리합니다.  

#### <a name="creatable-components"></a>만들 수 있는 구성 요소  
 레지스트리에 등록할 수 있는 구성 요소 집합이 있습니다. 첫 번째 구성 요소 집합은 주 UDI 마법사 실행 파일에서 제공하는 것이므로 항상 등록됩니다. 다른 두 구성 요소 집합은 "선택적" Dll에 제공됩니다. 이러한 구성 요소를 사용하려면 DLL이 .config XML 파일의 **Dll** 섹션에 나열되어야 합니다. 어떤 실행 파일에 특정 구성 요소가 포함되어 있는지 코드가 알 필요는 없습니다.  

 표 3은 팩터리 레지스트리(OSDSetupWizard에 정의된)에 등록된 구성 요소의 구성 요소 ID 목록입니다(구성 요소 이름은 ID와 동일하지만 앞부분에 *ID_* 가 없음).  

### <a name="table-3-component-ids"></a>표 3. 구성 요소 ID  

|**ID**|**설명**|  
|-|-|  
|ID_ACPowerTask|(ITask IWizardComponent) 구성 요소가 배터리에서 홀로 실행되지 않게 해주는 실행 전 작업|  
|ID_AppDiscoveryTask|(ITask IWizardComponent) 컴퓨터에 설치된 소프트웨어 항목을 검색하는 특수 작업|  
|**ID_BackgroundTask**|(**IBackgroundTask**, **IWizardComponent**) 다른 스레드에서 작업을 실행하는 데 사용 가능|  
|**ID_CopyFilesTask**|(**ITask**, **IWizardComponent**) 하나 이상의 파일을 복사하는 작업|  
|**ID_FormController**|(**IFormController**) 페이지에서 자체 인스턴스를 수신하므로 사용자가 직접 인스턴스를 만들 일은 거의 없음|  
|**ID_InvalidCharactersValidator**|(**IValidator**) 유효성 검사기에 제공된 목록의 문자가 텍스트 필드에 포함되지 않게 해주는 역할|  
|**ID_Logger**|(**ILogger**) 페이지에서 공유 인스턴스에 대한 포인터를 수신하므로 사용자가 직접 인스턴스를 만들 일은 거의 없음|  
|**ID_NonEmptyValidator**|(**IValidator**) 필드가 비어 있지 않게 해주는 유효성 검사기|  
|**ID_PasswordValidator**|(**IValidator**) 두 텍스트 필드에 동일한 콘텐츠가 포함되지 않게 해주는 유효성 검사기|  
|**ID_Regex**|(**IRegEx**) 정규식을 평가하여 일치 항목 검색|  
|**ID_RegExValidator**|(**IValidator**) 정규식 또는 알려진 패턴의 유효성을 검사하는 유효성 검사기|  
|**ID_SimpleStringProperties**|(**IStringProperties**, **ISimpleStringProperties**) XML을 사용하지 않고 작업에 속성을 보내는 간단한 방법을 제공|  
|**ID_ShellExecuteTask**|(**ITask**, **IWizardComponent**) 외부 프로그램 실행|  
|**ID_SummaryBag**|(**ISummaryBag**) Form 메서드를 통해 페이지에서 간접적으로 사용 가능|  
|**ID_TaskManager**|(**ITaskManager**, **IBackgroundCallback**, **IWizardComponent**) 작업 및 UI 집합의 실행 관리|  
|**ID_WmiRepository**|(**IWmiRepository**, **IWizardComponent**) WMI(Windows Management Instrumentation) 쿼리를 실행할 수 있도록 허용|  
|**ID_IXmlDocument**|(**IXmlDocument**) XML 문서를 읽고 쓰기 위한 외관 제공|  

 정의된 OSDRefreshWizard.dll, 공유 페이지 및 기타 제어 구성 요소는 표 4 및 표 5에 나와 있습니다.  

### <a name="table-4-directory-controls"></a>표 4. 디렉터리 컨트롤  

|**ID**|**설명**|  
|-|-|  
|**ID_Directory**|(**IDirectory**) 파일 시스템에서 디렉터리 정보를 얻기 위한 외관|  

### <a name="table-5-defined-sharedpagesdll"></a>표 5. 정의된 SharedPages.dll  

|**ID**|**설명**|  
|-|-|  
|**ID_ADHelper**|(**IADHelper**) AD DS(Active Directory® Domain Services)의 제한된 기능 집합에 대한 외관을 제공합니다.|  
|**ID_CpuInfo**|(**ICpuInfo**) CPU가 32비트인지 아니면 64비트인지 확인|  
|**ID_DomainJoinValidator**|(**IDomainJoinValidator**) 자격 증명 집합이 도메인에 조인할 수 있는지 확인하는 몇 가지 메서드 제공|  
|**ID_DriveList**|(**IDriveList**, **IBindableList**, **IWizardComponent**) WMI를 사용하여 컴퓨터에 있는 드라이브 목록 획득|  
|**ID_WiredNetworkTask**|(**ITask**) 유선으로(무선 대신) 네트워크 어댑터에 연결되었는지 확인하는 작업|  

#### <a name="control-components"></a>컨트롤 구성 요소  
 표 6에 나열된 구성 요소 유형 중 하나에 대한 액세스를 제공하는 **GetControlWrapper** 템플릿 함수를 통해 페이지의 컨트롤과 상호 작용합니다.  

### <a name="table-6-components"></a>표 6. 구성 요소  

|**Dialog control types**|**설명**|  
|-|-|  
|**CONTROL_CHECK_BOX**|(**ICheckBox**) 확인란 컨트롤을 사용하기 위한 외관|  
|**CONTROL_COMBO_BOX**|(**IComboBox**) 콤보 상자 컨트롤에 대한 외관|  
|**CONTROL_GENERIC**|(**IControl**) 대부분의 컨트롤 형식을 사용하여 사용 및 표시 상태를 제어하도록 허용|  
|**CONTROL_LIST_VIEW**|(**IListView**) 목록 보기 컨트롤의 기능에 대한 액세스를 제공하는 외관|  
|**CONTROL_PROGRESS_BAR**|(**IProgressBar**) 진행률 표시줄 컨트롤의 위치를 작업하기 위한 외관|  
|**CONTROL_RADIO_BUTTON**|(**IRadioButton**) 라디오 단추 컨트롤을 사용하기 위한 외관|  
|**CONTROL_STATIC_TEXT**|(**IStaticText**) 레이블이나 텍스트 상자처럼 컨트롤의 텍스트에 대한 읽기/쓰기 권한을 제공하는 외관|  
|**CONTROL_TREE_VIEW**|(**ItreeView**) 트리 뷰 컨트롤을 사용하기 위한 외관|  

#### <a name="image-list-component"></a>이미지 목록 구성 요소  
 이 구성 요소는 페이지의 **ImageList** 컨트롤에 대한 외관입니다. 사용자는 **IListView** 또는 **ITreeView** 인터페이스를 통해 이미지 목록을 만듭니다.  

#### <a name="formcontroller-component"></a>FormController 구성 요소  
 마법사는 사용자 대신 이 구성 요소를 만들어서 페이지에 전달합니다. 사용자는 **WizardPageImpl** 기본 클래스가 구현하는 **Form** 메서드를 사용하여 페이지에서 이 구성 요소에 액세스합니다.  

#### <a name="invalidcharactervalidator-component"></a>InvalidCharacterValidator 구성 요소  
 페이지에 포함할 수 있는 형식의 유효성 검사기입니다. ID는 **ID_InvalidCharactersValidator**이고(IValidator.h에 정의됨), 텍스트 값은 "Microsoft.Wizard.Validation.InvalidChars"입니다.  

 이 유효성 검사기는 허용되지 않는 문자 목록인 **InvalidChars**라고 하는 단일 속성(.config 파일의 **Setter** 요소)을 찾습니다. 텍스트 상자의 문자를 검사하며, 만약 텍스트에 이 목록의 문자가 포함되어 있으면 구성 요소가 실패를 보고합니다.  

#### <a name="nonemptyvalidator-component"></a>NonEmptyValidator 구성 요소  
 페이지에 포함할 수 있는 형식의 유효성 검사기입니다. ID는 **ID_NonEmptyValidator**이고(IValidator.h에 정의됨), 텍스트 값은 "Microsoft.Wizard.Validation.NonEmpty"입니다.  

 텍스트 상자(또는 **IStaticText**를 지원하는 다른 컨트롤)에 빈 문자열 값이 있으면 이 유효성 검사기가 실패합니다.  

#### <a name="passwordvalidator-component"></a>PasswordValidator 구성 요소  
 페이지에 포함할 수 있는 형식의 유효성 검사기입니다. ID는 **ID_PasswordValidator**이고(IValidator.h에 정의됨), 텍스트 값은 "Microsoft.Wizard.Validation.Password"입니다.  

 이 유효성 검사기는 두 개의 텍스트 컨트롤(**IStaticText**를 지원하는 컨트롤)과 함께 작동하며 두 컨트롤에 포함된 값이 동일하지 않으면 실패를 보고합니다. 즉, **암호** 텍스트 상자와 **암호 확인** 텍스트 상자가 일치하지 않으면 실패합니다.  

 이 유효성 검사기에는 두 컨트롤이 필요하므로 다른 유효성 검사기보다 더 많은 설치가 필요합니다. 설치는 다음과 같습니다.  

```  
Form()->AddToGroup(IDC_EDIT_PASSWORD, IDC_EDIT_PASSWORD2);  
PValidator pValidator;  
Form()->AddValidator(IDC_EDIT_PASSWORD, ID_PasswordValidator, pMessage, &pValidator);  
PStaticText pPassword2;  
GetControlWrapper(View(), IDC_EDIT_PASSWORD2, CONTROL_STATIC_TEXT, &pPassword2);  
pValidator->SetProperty(0, pPassword2);  
```  

 먼저 **암호** 컨트롤의 자식으로 **암호 확인** 컨트롤을 정의합니다. 이 방식을 사용하면 양식 컨트롤러가 **암호** 컨트롤을 비활성화할 경우 **암호 확인** 컨트롤도 비활성화됩니다. 다음으로 암호 유효성 검사기를 양식에 추가합니다. 마지막으로 암호 유효성 검사기에 **암호 확인** 컨트롤에 대한 인터페이스를 제공합니다.  

 두 컨트롤에 대한 요구 사항 때문에 .config XML 파일 대신 코드를 사용하여 이 유효성 검사기를 설정해야 합니다.  

#### <a name="regexvalidator-component"></a>RegExValidator 구성 요소  
 페이지에 포함할 수 있는 형식의 유효성 검사기입니다. ID는 **ID_RegExValidator**이고(IValidator.h에 정의됨), 텍스트 값은 "Microsoft.Wizard.Validation.RegEx"입니다.  

 이 유효성 검사기는 텍스트 컨트롤(**IStaticText**를 지원하는 컨트롤)의 콘텐츠를 정규식과 비교하여 텍스트가 정규식과 일치하지 않으면 실패합니다.  

 또는 미리 정의된 명명된 패턴에 이 유효성 검사기를 사용할 수도 있습니다. 정규식을 사용하려면 XML에 **Pattern**이라는 setter 속성이 포함되어야 합니다. 명명된 패턴을 대신 사용하려면 표 7의 값 중 하나로 설정된 **NamedPattern**이라는 setter를 사용하세요.  

### <a name="table-7-named-pattern-setters"></a>표 7. 명명된 패턴 Setter  

|**Pattern**|**설명**|  
|-|-|  
|사용자 이름|텍스트가 양식 도메인/사용자인지 아니면 user@domain인지 확인합니다.|  
|ComputerName|이름은 1-15자 사이여야 하며 문자 집합(예: : 및 ?)을 포함하면 안 됩니다.|  
|작업 그룹|이름은 1-15자 사이여야 하며 문자 집합(예: =, + 및 ?)을 포함하면 안 됩니다.|  

#### <a name="factoryregistry-component"></a>FactoryRegistry 구성 요소  
 이 구성 요소는 모든 클래스 팩터리 및 서비스를 추적합니다. **IFactoryRegistry** 인터페이스를 구현하며 페이지의 **Container** 메서드를 통해 간접적으로 사용할 수 있습니다. 그리고 레지스트리는 확장 Dll을 로드합니다. 레지스트리는 DLL을 로드한 후 내보낸 함수 **RegisterFactories**를 찾습니다. 사용자는 이 함수를 구현하고 그 안에서 페이지, 작업 및 유효성 검사기(그리고 등록하려는 그 외의 모든 클래스 팩터리)에 대한 클래스 팩터리를 등록해야 합니다. 다음은 샘플 프로젝트의 예제입니다.  

```  
extern "C" __declspec(dllexport) void RegisterFactories(IFactoryRegistry *factories)  
{  
Register<LocationPageFactory>(ID_LocationPage, factories);  
}  
```  

#### <a name="logger-component"></a>로거 구성 요소  
 이 구성 요소는 **Logger** 메서드(**WizardPageImpl**을 통해 구현)를 통해 페이지에 제공됩니다. 사용자는 이 메서드를 사용하여 로그 파일에 항목을 씁니다. 로그 파일의 콘텐츠는 사용자가 UDI 마법사를 실행하는 동안 발생하는 문제 진단에 유용합니다.  

#### <a name="propertybag-component"></a>PropertyBag 구성 요소  
 *속성 모음*은 메모리 변수에 대한 컨테이너입니다. **Container()->Properties()** 를 사용하여 페이지에서 사용할 수 있습니다. 메모리 변수는 여러 페이지 간에 임시 데이터를 전달하는 데 유용합니다.  

#### <a name="tsvariablebag-and-tsrepository-components"></a>TSVariableBag 및 TSRepository 구성 요소  
 **TSVariableBag** 구성 요소를 사용하면 작업 순서 변수를 읽고 쓸 수 있습니다. 이 구성 요소는 기본적으로 사용자가 **마침**을 클릭할 때까지 메모리에 값을 유지합니다. 페이지의 **TSVariables** 메서드(**WizardPageImpl** 기본 클래스를 통해 구현)를 통해 **TSVariable** 모음에 액세스할 수 있습니다. 이러한 구성 요소는 작업 순서 변수의 모든 읽기 및 쓰기를 기록합니다.  

#### <a name="wmirepository-component"></a>WmiRepository 구성 요소  
 이 구성 요소는 WMI 쿼리를 작업하기 위한 외관을 제공합니다. **ID_WmiRepository**로 **CreateInstance** 도우미 함수를 호출하여 **IWmiRepository** 인터페이스를 지원하는 이 구성 요소의 인스턴스를 얻을 수 있습니다. 이 구성 요소는 **IWmiIterator** 인터페이스를 통해 결과 레코드를 반환합니다.  

###  <a name="WizardPageHelperClasses"></a> 마법사 페이지 도우미 클래스  
 UDI SDK와 함께 제공되는 기본 제공 도우미 클래스를 사용하여 사용자 지정 UDI 마법사 페이지를 만들 수 있습니다. 표 8에는 사용자 지정 마법사 페이지를 만드는 데 사용할 수 있는 도우미 클래스가 정리되어 있습니다.  

### <a name="table-8-helper-classes"></a>표 8. 도우미 클래스  

|**도우미 클래스**|**설명**|  
|-|-|  
|[ClassFactoryImpl 클래스](#ClassFactoryImplClass)|클래스 팩터리를 만든 후 팩터리 레지스트리에 등록할 수 있는 유용한 기본 클래스입니다.|  
|[인터페이스 템플릿 클래스](#InterfaceTemplateClass)|둘 이상의 인터페이스를 구현하는 구성 요소를 빌드하려는 경우 이 템플릿 클래스를 사용합니다.|  
|[경로 도우미 클래스](#PathHelperClass)|이 클래스는 공통 파일/디렉터리 작업을 제공합니다.|  
|[포인터 템플릿 클래스](#PointerTemplateClass)|이 클래스는 COM 구성 요소의 수명 관리에 대한 참조 계산을 제공합니다. 인터페이스 작업을 마친 후 인터페이스를 해제하는 것이 중요합니다. 이 템플릿 클래스는 수명을 자동으로 처리합니다.|  
|[PUnknown 클래스](#PUnkownClass)|이 클래스는 IUnknown 인터페이스만을 위한 스마트 포인터입니다. 그 외의 다른 인터페이스에는 Pointer 템플릿 클래스를 사용합니다.|  
|[StringUtil 도우미 클래스](#StringUtilHelperClass)|이 클래스는 문자열을 쉽게 작업할 수 있는 도우미 메서드를 제공합니다.|  
|[SubInterface 템플릿 클래스](#SubInterfaceTemplateClass)|이 기본 클래스를 사용하면 스스로 다른 인터페이스에서 상속하는 인터페이스를 지원하는 구성 요소를 간편하게 구현할 수 있습니다.|  
|[UnknownImpl 템플릿 클래스](#UnknownImplTemplateClass)|이 클래스는 COM 구성 요소 만들기의 세부 정보를 대부분 처리합니다.|  
|[WizardComponent 템플릿 클래스](#WizardComponentTemplateClass)|이 기본 클래스는 구성 요소 만들기 및 로깅처럼 마법사 서비스에 액세스해야 하는 구성 요소를 만드는 데 사용됩니다.|  
|[WizardPageImpl 템플릿 클래스](#WizardPageImplTemplateClass)|이 기본 클래스는 모든 사용자 지정 마법사 페이지의 기본 클래스로 사용해야 합니다.|  

####  <a name="ClassFactoryImplClass"></a> ClassFactoryImpl 클래스  
 클래스 팩터리를 만든 후 팩터리 레지스트리에 등록할 수 있는 유용한 기본 클래스입니다.  

 다음은 샘플 프로젝트의 LocationPage.h 파일에서 발췌한 것으로 **ClassFactoryImpl** 클래스를 정의합니다.  

```  
#pragma once  

#include "ClassFactoryImpl.h"  

class LocationPageFactory :public ClassFactoryImpl  
{  
protected:  
    IUnknown *CreateNewInstance();  
};  
```  

 다음은 샘플 마법사 페이지의 LocationPage.cpp 파일에서 발췌한 것으로 페이지의 클래스 팩터리를 정의하는 데 사용됩니다.  

```  
IUnknown *LocationPageFactory::CreateNewInstance()  
{  
    return static_cast<IWizardPage *>(new LocationPage);  
}  
```  

####  <a name="InterfaceTemplateClass"></a> 인터페이스 템플릿 클래스  
 둘 이상의 인터페이스를 구현하는 구성 요소를 빌드하려는 경우 이 템플릿 클래스를 사용합니다. 예를 들면 다음과 같습니다.  

```  
classLocationPage :public Interface<IFieldCallback, WizardPageImpl<IDD_LOCATION_PAGE>>  
```  

 이 코드는 **WizardPageImpl**에서 지원되는 **IFieldCalback** 및 인터페이스를 지원하는 기본 클래스 체인(**IWizardPage**)을 만듭니다.  

####  <a name="PathHelperClass"></a> 경로 도우미 클래스  
 이 클래스는 공통 파일/디렉터리 작업을 제공합니다.  

```  
static inline std::wstring GetModulePath(HINSTANCE hModule)  
```  

 또한 사용자가 이 메서드에 제공하는 인스턴스 핸들을 사용하여 .exe 또는 .dll 파일에 대한 전체 경로를 반환합니다.  

```  
static inline std::wstring GetModuleFilename(HINSTANCE hModule)  
```  

 이 클래스는 사용자가 이 메서드에 제공하는 인스턴스 핸들을 사용하여 .exe 또는 .dll 파일에 대한 전체 경로 및 파일 이름을 반환합니다.  

```  
static inline std::wstring GetDirecotryName(LPCWSTR fullName)  
```  

 을 참조하세요. 을 참조하세요. 을 참조하세요. 또는 파일 이름을 제거하는 동안 경로만:  

```  
static inline std::wstring GetFileName(LPCWSTR fullName)  
```  

 파일 이름과 함께 경로가 지정되면 경로 도우미 클래스는 파일 이름만 반환합니다.  

```  
static inline std::wstring Combine(LPCWSTR path, LPCWSTR name)  
```  

 마지막으로 이 클래스는 경로 및 파일 이름(또는 다른 경로)이 결합된 새로운 문자열을 반환합니다.  

####  <a name="PointerTemplateClass"></a> 포인터 템플릿 클래스  
 이 클래스는 Pointer.h에 정의됩니다. COM 구성 요소에서 수명 관리에 참조 계산을 사용하므로 항상 인터페이스 작업을 마친 후 인터페이스를 해제하는 것이 중요합니다. Microsoft에서는 수명을 자동으로 처리하는 템플릿 클래스를 제공합니다. 예를 들어 XML 인터페이스에 대한 스마트 포인터를 원하는 경우 다음과 같이 작성할 수 있습니다.  

```  
Pointer<IXMLDOMNode> pNewChild  
pXmlDom->CreateNode(NODE_ELEMENT, L"MyElement", L"", &pNewChild);  
```  

 첫 번째 줄은 스마트 포인터를 정의합니다. 두 번째 줄은 다른 호출을 통해 스마트 포인터를 검색하는 것을 보여줍니다. **&** 연산자는 인터페이스를 포함하고 있는 경우 항상 기존 인터페이스를 해제하고 내부 포인터에 대한 주소를 반환합니다. 이와 같이 포인터를 검색한 후에는 변수가 범위를 벗어나면 **포인터** 인스턴스가 사용자를 대신하여 **Release**를 호출합니다. Microsoft에서는 **AddRef** 및 **Release**를 직접 호출하는 대신 스마트 포인터를 사용할 것을 권장합니다.  

 또한 **Pointer** 스마트 포인터 클래스는 사용자를 대신하여 다른 인터페이스를 검색하는 **QueryInterface**를 호출합니다. 예를 들어 팩터리 레지스트리에서 새로운 구성 요소 인스턴스를 만들 때 코드는 다음과 같습니다.  

```  
PWizardComponent pComp = pUnknown;  
if (pComp != nullptr)  
    pComp->SetContainer(m_pContainer);  
```  

 첫 번째 줄은 **IWizardComponent** 인터페이스를 요청하는 **QueryInterface**를 백그라운드에서 호출합니다. 구성 요소에서 해당 인터페이스를 지원하지 않는 경우 그 결과로 얻게 되는 스마트 포인터는 **nullptr**입니다.  

####  <a name="PUnkownClass"></a> PUnknown 클래스  
 이 클래스는 **IUnknown** 인터페이스만을 위한 스마트 포인터입니다. 그 외의 다른 인터페이스에는 **포인터** 템플릿 클래스를 사용합니다.  

####  <a name="StringUtilHelperClass"></a> StringUtil 도우미 클래스  
 이 클래스는 Utilities.h에 정의되며 문자열을 쉽게 작업할 수 있는 도우미 메서드를 제공합니다.  

```  
static inline int CompareIgnore(LPCWSTR first, LPCWSTR second)  
```  

 이 메서드는 두 문자열을 비교하며 대/소문자를 무시합니다(표 9 참조).  

### <a name="table-9-stringutil-helper-class"></a>표 9. StringUtil 도우미 클래스  

|**Returns**|**설명**|  
|-|-|  
|**0**|문자열 일치, 대/소문자 무시|  
|**<0**|첫 번째 < 두 번째|  
|**>0**|첫 번째 > 두 번째|  

 그 예는 다음과 같습니다.  

```  
static inline std::wstring Format(LPCWSTR input, int index, LPCWSTR value)  
static inline std::wstring Format(LPCWSTR input, int index, DWORD value)  
```  

 이러한 메서드는 매개 변수가 **{0}** 형식이라는 점에서 Microsoft.NET **Format** 메서드와 약간 비슷합니다. 그러나 대체와 같은 입력 서식 지정을 수행하지 않습니다.  

```  
static inline std::wstring Printf(std::wstring format, I val)  
static inline std::wstring Printf(std::wstring format, I val1, J val2)  
static inline std::wstring Printf(std::wstring format, I val1, J val2, K val3)  
static inline std::wstring Printf(std::wstring format, I val1, J val2, K val3, L val4)  
```  

 **StringCchPrintf**와 관련된 래퍼로써 **wstring**을 반환하므로 사용자가 직접 문자열 또는 버퍼에 대한 메모리를 할당할 필요가 없습니다.  

####  <a name="SubInterfaceTemplateClass"></a> SubInterface 템플릿 클래스  
 이 기본 클래스를 사용하면 스스로 다른 인터페이스에서 상속하는 인터페이스를 지원하는 구성 요소를 간편하게 구현할 수 있습니다. 예를 들어 **ICheckBox** 인터페이스는 **IControl**에서 상속합니다. 이 클래스를 사용하여 **CheckBoxWrapper**를 정의하는 방법은 다음과 같습니다.  

```  
classCheckBoxWrapper :public SubInterface<IControl, UnknownImpl<ICheckBox> >  
```  

 기본 인터페이스는 첫 번째 매개 변수이고, 파생된 인터페이스는 두 번째 매개 변수입니다.  

####  <a name="UnknownImplTemplateClass"></a> UnknownImpl 템플릿 클래스  
 이 클래스는 UnknownImpl.h에 정의되며 COM 구성 요소 만들기의 세부 정보를 대부분 처리합니다. 다음은 이 기본 클래스를 사용하는 방법에 대한 예제입니다.  

```  
classDirectory :public UnknownImpl<IDirectory>  
```  

 이 코드는 **IDirectory** 인터페이스를 지원하는 클래스를 정의합니다.  

####  <a name="WizardComponentTemplateClass"></a> WizardComponent 템플릿 클래스  
 이 클래스는 IWizardComponent.h에 정의되며 구성 요소 만들기 및 로깅처럼 마법사 서비스에 액세스해야 하는 구성 요소를 만드는 데 사용되는 유용한 기본 클래스입니다.  

 예를 들어 **CopyFilesTask** 구성 요소는 다음과 같이 정의됩니다.  

```  
classCopyFilesTask :public WizardComponent<ITask>  
{  
    ...  
```  

 이 템플릿 클래스에 대한 매개 변수는 사용자가 구성 요소에 사용하려는 “기본” 인터페이스이며, 작업에서는 **ITask**입니다. **WizardComponent**를 사용한다는 것은 구성 요소가 사용자가 제공하는 인터페이스(이 예제에서는 **ITask**)와 **IWizardComponent**를 모두 지원한다는 의미입니다.  

 사용자가 클래스 팩터리 레지스트리를 사용하여 새 구성 요소를 만들 때마다 레지스트리에서 구성 요소의 **IWizardComponent->SetContainer** 메서드를 호출하여 구성 요소에 마법사 서비스에 대한 액세스를 제공합니다.  

####  <a name="WizardPageImplTemplateClass"></a> WizardPageImpl 템플릿 클래스  
 이 클래스는 사용자 지정 페이지의 기본 클래스로 사용되며 다음은 그 예입니다.  

```  
class LocationPage :public WizardPageImpl<IDD_LOCATION_PAGE>  
```  

 매개 변수는 대화 상자 템플릿의 리소스 ID입니다.  

###  <a name="WizardPageInterfaces"></a> 마법사 페이지 인터페이스  
 UDI 마법사는 인터페이스를 사용하여 페이지의 여러 컨트롤에 액세스합니다. 페이지 내에서 사용자는 **GetControlWrapper** 함수를 사용하여 컨트롤 래퍼를 검색합니다. 그 예는 다음과 같습니다.  

```  
PStaticText pFormat;  
GetControlWrapper(View(), IDC_CHECK_PARTITION, CONTROL_STATIC_TEXT, &pFormat);  
```  

 여기서 **PStaticText**는 **IStaticText** 인터페이스에 대한 스마트 포인터입니다. 스마트 포인터는 범위를 벗어나거나 사용자가 메서드에 변수의 주소(예: **&pFormat**)를 제공할 때 자동으로 COM **Release()** 메서드를 호출합니다.  

#### <a name="iadhelper-interface"></a>IADHelper 인터페이스  

```  
__interfaceIADHelper : IUnknown  
{  
    HRESULT Init(ILogger *pLogger);  
    HRESULT ValidLogon(LPCTSTR userName, LPCTSTR password, LPCTSTR domain);  
    HRESULT HasAccess(LPCTSTR username, LPCTSTR password, LPCTSTR domain, LPCTSTR computerName, LPCTSTR accountDomain);  
};  

```  

##### <a name="hresult-initilogger-plogger"></a>HRESULT Init(ILogger \*pLogger)  
 이 구성 요소를 초기화하고, 정보를 기록할 수 있도록 로거에 전달합니다.  

##### <a name="hresultvalidlogonlpctstr-username-lpctstr-password-lpctstr-domain"></a>HRESULTValidLogon(LPCTSTR userName, LPCTSTR password, LPCTSTR domain)  
 이 메서드는 표 10에 나와 있는 것처럼 자격 증명 집합이 유효한지 확인합니다.  

### <a name="table-10-hresultvalidlogon"></a>표 10. HResultValidLogon  

|**HResult**|**설명**|  
|-|-|  
|S_OK|자격 증명이 유효함|  
|S_FALSE|자격 증명이 유효하지 않음|  
|E_FAIL|도메인 컨트롤러를 찾을 수 없습니다. 자세한 내용은 로그를 확인하세요.|  

##### <a name="hresult-hasaccesslpctstr-username-lpctstr-password-lpctstr-domain-lpctstr-computername-lpctstr-accountdomain"></a>HRESULT HasAccess(LPCTSTR username, LPCTSTR password, LPCTSTR domain, LPCTSTR computerName, LPCTSTR accountDomain)  
 이 메서드는 표 11에 나와 있는 것처럼 자격 증명 집합이 AD DS의 컴퓨터 개체에 대한 읽기/쓰기 액세스 권한을 갖고 있는지 확인합니다.  

### <a name="table-11-hresult-hasaccess"></a>표 11. HResult HasAccess  

|**HRESULT**|**설명**|  
|-|-|  
|S_OK|사용자가 액세스 권한을 갖고 있음|  
|E_FAIL|사용자가 액세스 권한을 갖고 있지 않습니다. 추가 정보는 로그 파일을 확인하세요.|  

#### <a name="ibackgroundtask-interface"></a>IBackgroundTask 인터페이스  

```  
__interface IBackgroundTask : IUnknown  
{  
    HRESULT Init(ITask *pTask, int id, IBackgroundCallback *pCallback);  
    void Start(void);  
    BOOL Running(void);  
    HRESULT Wait(DWORD waitMilliseconds);  
    HRESULT Terminate(DWORD exitCode);  
    HRESULT GetExitCode(LPDWORD pCode, HRESULT *pHresult);  
    HRESULT Close(void);  
};  
```  

##### <a name="overview"></a>개요  
 **진행률** 페이지에서는 이 클래스를 사용하여 별도의 스레드에서 작업을 실행합니다. 또한 별도의 스레드에서 작업을 수행하고 싶을 때는 언제든지 이 클래스를 사용할 수 있습니다. *Tasks*는 **ITask** 인터페이스를 지원하는 모든 클래스입니다.  

 이 인터페이스는 **ID_BackgroundTask**("Microsoft.Wizard.BackgroundTask") 구성 요소를 통해 구현되고, IBackgroundTask.h 인터페이스에서 정의됩니다.  

##### <a name="hresult-inititask-ptask-int-id-ibackgroundcallback-pcallback"></a>HRESULT Init(ITask \*pTask, int id, IBackgroundCallback \*pCallback)  
 표 12에 나와 있는 것처럼 이 인터페이스는 구성 요소를 초기화합니다.  

### <a name="table-12-hresult-init"></a>표 12. HRESULT Init  

|**매개 변수**|**설명**|  
|-|-|  
|**pTask**|다른 스레드에서 실행하려는 코드를 포함하는 클래스에 대한 포인터|  
|**Id**|콜백에서 실행을 마친 작업을 알려주는 **Finished** 메서드에 사용할 수 있는 숫자로, 동일한 콜백 메서드를 사용하여 여러 작업을 시작하는 경우에 유용합니다.|  
|**pCallback**|작업에서 실행을 완료할 때마다 호출되는 **Finished** 메서드를 구현하는 클래스로, **Finished** 메서드 호출은 UI 스레드가 아닌 백그라운드 스레드에서 수행됩니다.|  

##### <a name="void-startvoid"></a>void Start(void)  
 이 메서드는 백그라운드 스레드에서 작업을 시작하고 표 13의 요소를 반환합니다.  

### <a name="table-13-return-background-thread"></a>표 13. 백그라운드 스레드 반환  

|**Returns**|**설명**|  
|-|-|  
|**E_INVALIDARG**|작업이 이미 실행 중이므로 지금은 작업을 시작할 수 없습니다.|  
|**E_FAIL**|스레드를 시작하는 데 문제가 있습니다.|  
|**S_OK**|스레드가 시작되었습니다.|  

##### <a name="bool-running"></a>BOOL Running()  
 백그라운드 작업이 현재 실행 중이면 이 메서드가 TRUE를 반환하고 실행 중이 아니면 FALSE를 반환합니다.  

##### <a name="hresult-waitdword-waitmilliseconds"></a>HRESULT Wait(DWORD waitMilliseconds)  
 이 메서드는 스레드가 실행을 중지하거나 시간(밀리초)이 경과할 때까지 대기합니다.  

##### <a name="hresult-terminatedword-exitcode"></a>HRESULT Terminate(DWORD exitCode)  
 이 메서드는 실행 중인 스레드를 종료합니다(표 14 및 15 참조). 이 메서드가 반환된 후 이 프로세스가 완료될 때까지 짧은 시간이 걸릴 수 있습니다.  

### <a name="table-14-hresult-terminate-exit-code"></a>표 14. HRESULT 마침 종료 코드  

|**매개 변수**|**설명**|  
|-|-|  
|**exitCode**|이 종료 코드는 Finished 콜백 메서드로 전송되어 **GetExitCode** 메서드에서도 사용할 수 있게 됩니다.|  

### <a name="table-15-termination-codes"></a>표 15. 종료 코드  

|**Returns**|**설명**|  
|-|-|  
|**E_FAIL**|종료 호출이 실패했습니다.|  
|**S_OK**|스레드 종료 요청이 성공했습니다.|  

##### <a name="hresult-getexitcodelpdword-pcode-hresult-phresult"></a>HRESULT GetExitCode(LPDWORD pCode, HRESULT \*pHresult)  
 백그라운드 스레드에서 작업을 실행한 결과를 가져오려면 이 메서드를 사용합니다(표 16 참조).  

### <a name="table-16-result-codes"></a>표 16. 결과 코드  

|**매개 변수**|**설명**|  
|-|-|  
|**pCode**|반환 시 설정되는 **DWORD**에 대한 포인터이거나 반환 값이 필요 없는 경우에는 **nullptr**에 대한 포인터입니다. 종료 시 이 매개 변수는 스레드가 실행 중이면 **STILL_ACTIVE**로 설정되고, 사용자가 해당 메서드를 호출하면 작업의 **Execute** 메서드에서 반환한 코드 또는 **Terminate** 메서드에 전달된 값으로 설정됩니다.|  
|**pHresult**|반환 시 설정되는 **HRESULT**에 대한 포인터이거나 **HRESULT** 값이 필요 없는 경우에는 **nullptr**에 대한 포인터입니다.|  

##### <a name="hresult-closevoid"></a>HRESULT Close(void)  
 이 메서드는 백그라운드 스레드를 해제합니다. 스레드가 현재 실행 중이면 **E_INVALIDARG**를 반환하고 그렇지 않으면 **S_OK**를 반환합니다.  

#### <a name="icheckbox-interface"></a>ICheckBox 인터페이스  

```  
__interface ICheckBox : IControl  
{  
    void Check(BOOL check);  
    BOOL IsButtonChecked();  
};  
```  

##### <a name="void-checkbool-check"></a>void Check(BOOL check)  
 확인란의 선택 상태를 설정합니다. 이 메서드가 TRUE이면 확인란이 선택된 것이고, FALSE이면 선택되지 않은 것입니다.  

##### <a name="bool-isbuttonchecked"></a>BOOL IsButtonChecked()  
 이 메서드는 확인란의 현재 선택 상태를 보고합니다.  

#### <a name="icombobox-interface"></a>IComboBox 인터페이스  

```  
__interface IComboBox : IControl  
{  
    HRESULT Bind([in] IBindableList *pList);  
    HRESULT Select(int index);  
    int Selected(void);  
    void Add([in] LPCTSTR caption);  
    HRESULT GetText([out, retval] LPBSTR pText);  
    void Clear();  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **CheckBoxWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_COMBO_BOX** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="hresult-bindin-ibindablelist-plist"></a>HRESULT Bind([in] IBindableList \*pList)  
 **IBindableList** 인터페이스를 구현하는 데이터 원본이 있는 경우 이 메서드를 사용합니다. 목록 상자는 콘텐츠를 이 목록의 캡션으로 초기화합니다.  

##### <a name="hresult-selectint-index"></a>HRESULT Select(int index)  
 인덱스의 콤보 상자에서 항목을 선택합니다.  

##### <a name="int-selectedvoid"></a>int Selected(void)  
 이 메서드는 선택한 항목의 인덱스를 반환하거나 아무 것도 선택하지 않으면 **-1**을 반환합니다.  

##### <a name="void-addin-lpctstr-caption"></a>void Add([in] LPCTSTR caption)  
 콤보 상자에 항목을 수동으로 추가합니다.  

##### <a name="hresult-gettextout-retval-lpbstr-ptext"></a>HRESULT GetText([out, retval] LPBSTR pText)  
 콤보 상자에서 현재 선택한 항목의 문자열을 검색합니다.  

##### <a name="void-clear"></a>void Clear()  
 콤보 상자에서 모든 항목을 제거합니다.  

#### <a name="icontrol-interface"></a>IControl 인터페이스  

```  
__interface IControl : IUnknown  
{  
    HRESULT SetEnable(BOOL enable);  
    BOOL IsEnabled(void);  
    HRESULT SetVisible(BOOL visible);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **ControlWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_GENERIC** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="hresult-setenablebool-enable"></a>HRESULT SetEnable(BOOL enable)  
 컨트롤을 사용하도록 또는 사용하지 않도록 설정합니다.  

##### <a name="bool-isenabledvoid"></a>BOOL IsEnabled(void)  
 컨트롤을 사용하도록 설정하면 TRUE를 반환하고 그렇지 않으면 FALSE를 반환합니다.  

##### <a name="hresult-setvisiblebool-visible"></a>HRESULT SetVisible(BOOL visible)  
 컨트롤을 표시하거나 숨깁니다.  

#### <a name="icpuinfo-interface"></a>ICpuInfo 인터페이스  

```  
__interface ICpuInfo : IUnknown  
{  
    BOOL Is64Bit(void);  
};  
```  

##### <a name="overview"></a>개요  
 새 **ID_CpuInfo** 구성 요소를 만들어서 이 인터페이스를 얻을 수 있습니다. 단일 메서드는 CPU가 32비트인지 아니면 64비트인지 보고합니다. 64비트 컴퓨터에서 32비트 운영 체제를 사용 중인 경우 이 메서드는 CPU의 너비(운영 체제가 아닌)만 보고하므로 TRUE를 반환합니다.  

##### <a name="idirectory-interface"></a>IDirectory 인터페이스  

```  
__interface IDirectory : IUnknown  
{  
    BOOL FileExists(LPCWSTR name);  
    BOOL FindFirst([in] LPCWSTR name);  
    HRESULT FoundName([out, retval] LPBSTR name);  
    DWORD FoundAttributes(void);  
    BOOL FindNext(void);  
    void FinishFind(void);  
};  
```  

###### <a name="overview"></a>개요  
 **ID_Directory**를 사용하여 만드는 **디렉터리** 구성 요소는 파일 시스템의 디렉터리를 작업하기 위한 외관을 제공합니다.  

###### <a name="bool-fileexistslpcwstr-name"></a>BOOL FileExists(LPCWSTR name)  
 사용자가 입력한 이름의 파일이 있는 경우 이 메서드는 TRUE를 반환합니다.  

###### <a name="bool-findfirstin-lpcwstr-name"></a>BOOL FindFirst([in] LPCWSTR name)  
 이 메서드는 사용자가 입력한 이름과 일치하는 첫 번째 일치 항목을 찾습니다. 와일드 카드 문자를 지원하고 파일 및 디렉터리 이름을 반환합니다. 이 메서드는 일치 항목이 발견되면 TRUE를 반환하고 그렇지 않으면 FALSE를 반환합니다.  

###### <a name="hresult-foundnameout-retval-lpbstr-name"></a>HRESULT FoundName([out, retval] LPBSTR name)  
 이 메서드는 **FindFirst** 또는 **FindNext**를 호출하여 찾은 파일 이름을 검색합니다.  

###### <a name="dword-foundattributesvoid"></a>DWORD FoundAttributes(void)  
 이 메서드는 최근에 찾은 파일 또는 디렉터리의 특성을 반환합니다. 다음과 같은 코드를 사용하여 디렉터리인지 테스트할 수 있습니다.  

```  
pDirectory->FoundAttributes() & FILE_ATTRIBUTE_DIRECTORY  
```  

###### <a name="bool-findnextvoid"></a>BOOL FindNext(void)  
 그 다음 항목을 찾습니다. 또 다른 일치 항목이 발견되면 이 메서드는 TRUE를 반환하고 그렇지 않으면 FALSE를 반환합니다.  

###### <a name="void-finishfindvoid"></a>void FinishFind(void)  
 이 메서드는 찾기 작업에 사용되는 리소스를 해제합니다.  

#### <a name="idomainjoinvalidator-interface"></a>IDomainJoinValidator 인터페이스  

```  
__interface IDomainJoinValidator : IUnknown  
{  
    HRESULT Init(ILogger *pLogger, IWizardPageContainer *pContainer, IStaticText *pUsername, IStaticText *pPassword, IStaticText *pComputerName);  
    HRESULT IsUsernameValid(LPCWSTR domainName);  
    BOOL CanModifyComputerAdEntry(LPCWSTR domainName);  
};  
```  

##### <a name="overview"></a>개요  
 **CreateInstance** 템플릿 함수에 **ID_DomainJoinValidator** 값을 사용하여 이 인터페이스의 인스턴스를 가져올 수 있습니다.  

##### <a name="hresult-initilogger-plogger-iwizardpagecontainer-pcontainer-istatictext-pusername-istatictext-ppassword-istatictext-pcomputername"></a>HRESULT Init(ILogger \*pLogger, IWizardPageContainer \*pContainer, IStaticText \*pUsername, IStaticText \*pPassword, IStaticText \*pComputerName)  
 표 17에 나와 있는 것처럼 인스턴스를 초기화합니다.  

### <a name="table-17-hresult-init---instance-initialization"></a>표 17. HRESULT Init - 인스턴스 초기화  

|**매개 변수**|**설명**|  
|-|-|  
|**pLogger**|페이지의 **Logger** 메서드를 통해 페이지에서 사용할 수 있는 로거 인스턴스|  
|**pContainer**|페이지의 **Container** 메서드의 결과를 전달|  
|**pUsername**|유효성을 검사할 사용자 이름을 포함하는 텍스트 상자|  
|**pPassword**|유효성을 검사할 암호를 포함하는 텍스트 상자|  
|**PComputerName**|최종적으로 도메인에 조인될 컴퓨터 이름을 포함하는 텍스트 상자|  

##### <a name="hresult-isusernamevalidlpcwstr-domainname"></a>HRESULT IsUsernameValid(LPCWSTR domainName)  
 이 메서드는 **IADHelper->ValidLogon** 메서드를 사용하여 작업을 수행합니다. 자세한 내용은 해당 메서드를 참조하세요.  

##### <a name="bool-canmodifycomputeradentrylpcwstr-domainname"></a>BOOL CanModifyComputerAdEntry(LPCWSTR domainName)  
 사용자에게 컴퓨터 항목을 수정할 권한이 있는지 확인합니다. 대부분의 작업은 **IADHelper HasAccess->** 를 통해 수행됩니다. 이 메서드가 FALSE를 반환하면 로그 파일에서 자세한 내용을 확인하세요.  

#### <a name="idrivelist-interface"></a>IDriveList 인터페이스  

```  
__interface IDriveList : IUnknown  
{  
    HRESULT Init(IWmiRepository *pWmi);  
    HRESULT SetWhereClause(LPCTSTR whereClause);  
    HRESULT SetMinimumDriveSize(__int64 size);  
    HRESULT Update(void);  
    HRESULT AddProperty(ENUM_DISK_QUERY_SECTION section, LPCTSTR propName, LPCTSTR propNameReturned);  

    size_t Count(void);  
    HRESULT GetProperty(size_t index, LPCTSTR propName,  LPVARIANT value);  
    HRESULT GetCaption(size_t index,  LPBSTR pCaption);  
}  
```  

##### <a name="hresult-initiwmirepository-pwmi"></a>HRESULT Init(IWmiRepository \*pWmi)  
 다른 구성 요소를 호출하기 전에 이 메서드를 호출해야 합니다. 이 메서드를 호출하려면 새 **WmiRepository**를 만들어야 합니다.  

##### <a name="hresult-setwhereclauselpctstr-whereclause"></a>HRESULT SetWhereClause(LPCTSTR whereClause)  
 이 메서드를 사용하면 쿼리에서 "where" 절로 표시되는 텍스트를 추가할 수 있습니다. 예를 들어 다음 줄은 USB 드라이브만 반환합니다.  

```  
pDrives->SetWhereClause(L"WHERE InterfaceType='USB'");  
```  

##### <a name="hresult-setminimumdrivesizeint64-size"></a>HRESULT SetMinimumDriveSize(\__int64 size)  
 쿼리에서 반환될 드라이브의 최소 드라이브 크기를 바이트 단위로 설정합니다.  

##### <a name="hresult-updatevoid"></a>HRESULT Update(void)  
 쿼리를 실행합니다. 이 메서드를 호출한 후 사용 가능한 드라이브 목록은 드라이브 문자순으로 정렬됩니다.  

##### <a name="hresult-addpropertyenumdiskquerysection-section-lpctstr-propname-lpctstr-propnamereturned"></a>HRESULT AddProperty(ENUM_DISK_QUERY_SECTION section, LPCTSTR propName, LPCTSTR propNameReturned)  
 이 메서드는 쿼리 결과에서 사용할 수 있게 만들려는 추가 속성의 이름을 추가합니다. **Update**를 호출하기 전에 이 메서드를 호출하세요. 표 18에는 세 가지 유용한 속성이 나와 있습니다.  

### <a name="table-18-hresult-addproperty-useful-properties"></a>표 18. HRESULT AddProperty: 유용한 속성  

|**섹션**|**속성**|**설명**|  
|-|-|-|  
|**DISKQUERY_LOGICALDISK**|**Size**|문자열로 표시되는 바이트 단위 크기|  
|**DISKQUERY_DISKPARTITION**|**DiskIndex**|0부터 시작하는 정수 디스크 번호|  
|**DISKQUERY_LOGICALDISK**|**VolumeName**|볼륨 레이블|  

##### <a name="sizet-countvoid"></a>size_t Count(void)  
 쿼리에서 반환하는 레코드 수. 이 메서드를 호출 하기 전에 **Update**를 호출하세요.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propname--lpvariant-value"></a>HRESULT GetProperty(size_t index, LPCTSTR propName,  LPVARIANT value)  
 이 메서드는 표 19에 나와 있는 것처럼 쿼리 결과에서 속성 값을 검색합니다.  

### <a name="table-19-hresult-getproperty"></a>표 19. HRESULT GetProperty  

|**매개 변수**|**설명**|  
|-|-|  
|**Index**|결과 레코드에 대한 0부터 시작하는 인덱스|  
|**propName**|속성 이름(예: “크기”)|  
|**값**|반환 시 이 매개 변수는 속성의 변형 값을 포함|  

##### <a name="hresult-getcaptionsizet-index--lpbstr-pcaption"></a>HRESULT GetCaption(size_t index,  LPBSTR pCaption)  
 이 메서드는 **Caption** 속성과 동일한 레코드에 대한 캡션을 검색합니다.  

#### <a name="iimagelist-interface"></a>IImageList 인터페이스  

```  
__interface IImageList  
{  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    HImageList GetImageList(void);  
    int AddImage(HInstance hInstance, int resourceId);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **ImageList** 구성 요소를 통해 구현됩니다. 이 구성 요소의 인스턴스는 **IListView** 인터페이스에서 검색합니다.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 이 구성 요소가 관리하는 새 이미지 목록을 만듭니다. 이 메서드는 한 번만 호출하면 됩니다.  

##### <a name="himagelist-getimagelistvoid"></a>HImageList GetImageList(void)  
 사용자가 이미지 목록에서 다른 작업을 수행해야 하는 경우 이 메서드는 이미지 목록에 대한 핸들을 반환합니다.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage(HInstance hInstance, int resourceId)  
 표 20과 같이 리소스의 이미지 목록에 새 이미지를 추가합니다.  

### <a name="table-20-hresult-iimagelist-interface"></a>표 20. HRESULT IImageList 인터페이스  

|**매개 변수**|**설명**|  
|-|-|  
|**hInstance**|비트맵 리소스를 포함하는 모듈의 인스턴스 핸들|  
|**resourceId**|이미지 목록에 로드할 리소스 ID|  

#### <a name="ilistview-interface"></a>IListView 인터페이스  

```  
__interface IListView : IControl  
{  
    int AddItem([in] LPCTSTR text);  
    int AddColumn(int width, [in] LPCTSTR text);  
    HRESULT SetSubItem(int index, int column, [in] LPCTSTR text);  
    int GetWidth(void);  
    void SetExtendedStyle(DWORD style);  
    int GetSelectedItem(void);  
    HRESULT SelectItem(int index);  
    BOOL IsItemChecked(int index);  
    int GetItemCount(void);  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    int AddImage(HINSTANCE hInstance, int resourceId);  
    HRESULT SetImage(int index, int imageIndex);  
    HRESULT Clear(void);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **ControlWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_LIST_VIEW** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="int-additemin-lpctstr-text"></a>int AddItem([in] LPCTSTR text)  
 목록 상자에 새 행을 추가합니다. 이 메서드는 방금 추가한 항목의 인덱스를 반환합니다.  

##### <a name="int-addcolumnint-width-in-lpctstr-text"></a>int AddColumn(int width, [in] LPCTSTR text)  
 목록 보기에 새 열을 추가합니다.  

##### <a name="hresult-setsubitemint-index-int-column-in-lpctstr-text"></a>HRESULT SetSubItem(int index, int column, [in] LPCTSTR text)  
 표 21에 나와 있는 것처럼 목록 상자의 첫 번째 열이 아닌 열에 텍스트를 설정합니다.  

### <a name="table-21-hresult-setsubitem"></a>표 21. HRESULT SetSubItem  

|**매개 변수**|**설명**|  
|-|-|  
|**index**|수정하려는 목록 항목의 인덱스|  
|**column**|업데이트하려는 열의 인덱스. 첫 번째 열은 **AddItem**을 사용하여 설정되고, 두 번째 열부터는 이 메서드를 사용하여 설정됩니다.|  
|**text**|열에 표시할 문자열|  

##### <a name="int-getwidthvoid"></a>int GetWidth(void)  
 이 메서드는 전체 텍스트 상자의 너비를 반환합니다.  

##### <a name="void-setextendedstyledword-style"></a>void SetExtendedStyle(DWORD style)  
 이 메서드를 사용하면 다음과 같이 목록 상자에서 확장된 스타일을 설정할 수 있습니다.  

```  
m_pList->SetExtendedStyle(LVS_EX_FULLROWSELECT);  
```  

##### <a name="int-getselecteditemvoid"></a>int GetSelectedItem(void)  
 이 메서드는 현재 선택된 목록 보기 항목의 인덱스를 반환합니다.  

##### <a name="hresult-selectitemint-index"></a>HRESULT SelectItem(int index)  
 목록에서 선택한 항목을 이 인덱스로 설정합니다.  

##### <a name="bool-isitemcheckedint-index"></a>BOOL IsItemChecked(int index)  
 목록에서 항목이 선택되면 이 메서드가 TRUE를 반환합니다. 이 메서드를 사용하려면 확인란 스타일을 설정하는 **SetExtendedStyle**을 호출해야 합니다.  

##### <a name="int-getitemcountvoid"></a>int GetItemCount(void)  
 이 메서드는 목록 보기에 있는 항목 수를 반환합니다.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 새 이미지 목록을 만들어서 목록 보기에 연결합니다.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage(HINSTANCE hInstance, int resourceId)  
 목록 보기의 이미지 목록에 이미지를 추가합니다. 먼저 **CreateImageList**를 호출해야 합니다.  

##### <a name="hresult-setimageint-index-int-imageindex"></a>HRESULT SetImage(int index, int imageIndex)  
 특정 목록 보기 항목의 왼쪽에 표시될 이미지를 설정합니다.  

##### <a name="hresult-clearvoid"></a>HRESULT Clear(void)  
 목록 보기에서 모든 항목을 제거합니다.  

#### <a name="iprogressbar-interface"></a>IProgressBar 인터페이스  

```  
__interface IProgressBar : IControl  
{  
    HRESULT SetPercentage(int position);  
    int GetPercentage(void);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **ProgressBarWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_PROGRESS_BAR** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="hresult-setpercentageint-position"></a>HRESULT SetPercentage(int position)  
 0-100 사이의 숫자를 사용하여 진행률 표시줄의 위치를 설정합니다. 기본적으로 새 Win32® 진행률 표시줄의 최대 범위는 100입니다.  

##### <a name="int-getpercentagevoid"></a>int GetPercentage(void)  
 이 메서드는 진행률의 현재 위치를 반환합니다.  

#### <a name="iradiobutton-interface"></a>IRadioButton 인터페이스  

```  
__interface IRadioButton : IControl  
{  
public:  
    void SetGroup(int firstId, int lastId);  
    void CheckRadio(int id);  
    BOOL IsButtonChecked(int id);  
    void EnableRadio(int id, BOOL enable);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **RadioButtonWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_RADIO_BUTTON** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="void-setgroupint-firstid-int-lastid"></a>void SetGroup(int firstId, int lastId)  
 래퍼에 그룹으로 처리해야 할 라디오 단추의 범위를 제공합니다. **CheckRadio**를 호출하기 전에 이 메서드를 먼저 호출해야 합니다.  

##### <a name="void-checkradioint-id"></a>void CheckRadio(int id)  
 선택한 라디오 단추 그룹에서 단일 단추가 될 특정 라디오 단추를 설정합니다. 이 메서드를 호출하기 전에 먼저 **SetGroup**을 호출해야 합니다.  

##### <a name="bool-isbuttoncheckedint-id"></a>BOOL IsButtonChecked(int id)  
 현재 라디오 단추가 선택되어 있으면 이 메서드가 TRUE를 반환하고 그렇지 않으면 FALSE를 반환합니다.  

##### <a name="void-enableradioint-id-bool-enable"></a>void EnableRadio(int id, BOOL enable)  
 이 메서드는 라디오 단추를 사용하도록 또는 사용하지 않도록 설정합니다.  

#### <a name="istatictext-interface"></a>IStaticText 인터페이스  

```  
__interface IStaticText : IControl  
{  
    HRESULT SetText([in] LPCTSTR pText);  
    HRESULT GetText([out, retval] LPBSTR pText);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **StaticTextWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_STATIC_TEXT** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="hresult-settextin-lpctstr-ptext"></a>HRESULT SetText([in] LPCTSTR pText)  
 컨트롤에 대한 텍스트를 설정합니다.  

##### <a name="hresult-gettextout-retval-lpbstr-ptext"></a>HRESULT GetText([out, retval] LPBSTR pText)  
 이 메서드는 컨트롤에 대한 텍스트의 현재 값을 반환합니다.  

####  <a name="ITaskinterface"></a> ITask 인터페이스  

```  
__interface IControl : IUnknown  
{  
    HRESULT Init(IStringProperties *pProperties, ISettingsProperties *pTaskSettings);  
    HRESULT Execute(LPDWORD pReturnCode);  
};  
```  

 실행 전 페이지에서 구성 요소를 작업으로 사용할 수 있게 하려는 경우 또는 **BackgroundTask** 구성 요소를 사용하여 백그라운드 스레드에서 작업을 수행하려는 경우 이 인터페이스를 구현합니다.  

 다음은 **ITask** 인터페이스를 구현하는 구성 요소입니다.  

-   ID_ShellExecuteTask, L"Microsoft.Wizard.ShellExecuteTask"  

-   ID_CopyFilesTask, L"Microsoft.Wizard.CopyFilesTask"  

-   ID_ACPowerTask, L"Microsoft.OSDRefresh.ACPowerTask"  

-   ID_WiredNetworkTask, L"Microsoft.SharedPages.WiredNetworkTask"  

##### <a name="init"></a>Init  

```  
HRESULT Init(IStringProperties *pProperties, ISettingsProperties *pTaskSettings)  
```  

 실행 전 페이지에 대한 작업을 작성하는 경우 이 메서드를 호출하여 작업을 초기화합니다. .config 파일에는 다음과 비슷한 XML이 포함되어 있습니다.  

```  
<Task DisplayName="Check Windows Scripting Host" Type="Microsoft.Wizard.ShellExecuteTask">  
  <Setter Property="filename">%windir%\system32\cscript.exe</Setter>  
  <Setter Property="parameters">Preflight\OSDCheckWSH.vbs</Setter>  
  <Setter Property="BitmapFilename">images\WinScriptHost.bmp</Setter>  
  <ExitCodes>  
    <ExitCode State="Success" Type="0" Value="0" Text="" />  
    <ExitCode State="Error" Type="-1" Value="*" Text="Windows Scripting Host not installed." />  
  </ExitCodes>  
</Task>  
```  

 **pProperties** 매개 변수는 세 setter 값에 대한 액세스를 제공하는 반면, **pTaskSettings** 매개 변수는 **Task** 요소 및 자식 요소에 대한 액세스를 제공합니다. 대부분의 작업은 **pProperties** 매개 변수에서 데이터를 읽기만 하면 됩니다.  

#####  <a name="Execute"></a> 실행  

```  
HRESULT Execute(LPDWORD pReturnCode)  
```  

 작업을 수행하는 코드를 작성하는 위치는 다음과 같습니다. 오류가 없으면 이 메서드가 **S_OK**를 반환해야 하고, 작업을 실행하는 동안 오류가 발생하면 이 메서드가 다른 **HRESULT**를 반환할 수 있습니다. 실행 전 페이지를 사용하는 경우 이 메서드가 반환하는 **S_OK** 이외의 값은 <ExitCodes\> 섹션의 <Error\> 요소에 매칭됩니다.  

 **pReturnCode** 매개 변수를 작업 상태를 보고하는 숫자로 업데이트해야 합니다. 이러한 값은 실행 전 페이지를 통해 <ExitCode\> 요소에 매칭됩니다.  

#### <a name="itreeview-interface"></a>ITreeView 인터페이스  

```  
__interface ITreeView : IControl  
{  
    void EnableCheckboxes(void);  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    int AddImage(HINSTANCE hInstance, int resourceId);  

    HTREEITEM AddItem(LPCTSTR text, HTREEITEM hParent = NULL);  
    void SetImage(HTREEITEM item, int image, int expandImage);  

    void Clear(void);  
    BOOL SetFirstVisible(HTREEITEM item);  
    BOOL SelectItem(HTREEITEM item);  
    void CheckItem(HTREEITEM item, UINT checkState);  
    HTREEITEM SelectedItem(void);  
    int SetItemHeight(SHORT height);  
    HRESULT EnableItem(HTREEITEM item, BOOL enable);  
    void Expand(HTREEITEM hItem, BOOL expand);  

    HTREEITEM GetChild(HTREEITEM hParent);  
    HTREEITEM GetParent(HTREEITEM hNode);  
    HTREEITEM GetNextItem(HTREEITEM hPrevious);  

    UINT IsChecked(HTREEITEM item);  
    BOOL IsEnabled(HTREEITEM item);  

    INT_PTR CommonControlEvent(WORD controlId, void* pInfo, BOOL *pCancel);  
    HRESULT SetEventHandler(ITreeViewEvent *pEventHandler);  

    void SetSelectedBackColor(COLORREF color);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **TreeViewWrapper** 구성 요소를 통해 구현됩니다. 사용자는 **CONTROL_TREE_VIEW** 형식의 **GetControlWrapper** 도우미 함수를 사용하여 이 구성 요소의 인스턴스를 검색합니다.  

##### <a name="void-enablecheckboxesvoid"></a>void EnableCheckboxes(void)  
 이 메서드는 **TVS_CHECKBOXES** 스타일을 설정하여 트리 뷰 컨트롤의 확인란을 켭니다.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 트리 뷰 컨트롤에 새 이미지 목록을 추가합니다. **flags** 매개 변수는 **ImageList_Create** Win32 함수 호출에 전달됩니다.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage(HINSTANCE hInstance, int resourceId)  
 인스턴스 핸들 **hInstance**를 사용하여 모듈에 있는 리소스(**resourceId**)의 이미지 목록에 이미지를 추가합니다.  

##### <a name="htreeitem-additemlpctstr-text-htreeitem-hparent--null"></a>HTREEITEM AddItem(LPCTSTR text, HTREEITEM hParent = NULL)  
 트리 뷰에 노드를 추가합니다. **hParent**가 NULL이면 새 노드는 최상위 수준에서 추가됩니다. 그렇지 않으면 새 항목을 추가하려는 부모 항목에 핸들을 제공합니다. 이 메서드는 새 항목에 핸들을 반환합니다.  

##### <a name="void-setimagehtreeitem-item-int-image-int-expandimage"></a>void SetImage(HTREEITEM item, int image, int expandImage)  
 트리 뷰 항목에 사용할 이미지를 설정합니다. 일반 이미지와 확장된 이미지를 모두 설정할 수 있습니다.  

##### <a name="void-clearvoid"></a>void Clear(void)  
 트리 뷰에서 모든 항목을 제거합니다.  

##### <a name="bool-setfirstvisiblehtreeitem-item"></a>BOOL SetFirstVisible(HTREEITEM item)  
 트리 뷰 항목이 표시되는지 확인합니다. 이 항목을 표시하기 위해 필요한 경우 트리 뷰가 스크롤됩니다.  

##### <a name="bool-selectitemhtreeitem-item"></a>BOOL SelectItem(HTREEITEM item)  
 현재 선택된 항목을 사용자가 제공하는 항목으로 설정합니다. 그 후 **SetFirstVisible**을 호출하여 새로 선택한 항목을 표시할 수 있습니다.  

##### <a name="void-checkitemhtreeitem-item-uint-checkstate"></a>void CheckItem(HTREEITEM item, UINT checkState)  
 이 메서드는 기본적으로 트리 뷰의 확인란에 표시될 이미지를 설정합니다. 이러한 이미지는 트리 뷰에서 관리하는 별도의 **ImageList** 컨트롤에 있습니다. 기본적으로 이 이미지 목록에는 표 22처럼 세 개의 이미지가 있습니다.  

### <a name="table-22void-checkitem-image-list-default"></a>표 22. void CheckItem 이미지 목록 기본값  

|**checkState**|**설명**|  
|-|-|  
|**0**|빈|  
|**1**|삭제됨|  
|**2**|선택됨|  

##### <a name="htreeitem-selecteditemvoid"></a>HTREEITEM SelectedItem(void)  
 이 메서드는 현재 선택된 트리 뷰 항목의 핸들을 반환합니다.  

##### <a name="int-setitemheightshort-height"></a>int SetItemHeight(SHORT height)  
 이 메서드는 트리 뷰 컨트롤에 있는 모든 항목의 높이를 픽셀 단위로 설정합니다. 이전 높이를 픽셀 단위로 반환합니다.  

##### <a name="hresult-enableitemhtreeitem-item-bool-enable"></a>HRESULT EnableItem(HTREEITEM item, BOOL enable)  
 이 메서드는 트리에서 단일 항목을 사용하도록 또는 사용하지 않도록 설정합니다. 자식이 있는 항목을 사용하지 않도록 설정해도 자식이 비활성화되지는 않습니다.  

##### <a name="void-expandhtreeitem-hitem-bool-expand"></a>void Expand(HTREEITEM hItem, BOOL expand)  
 이 메서드는 트리에서 노드를 확장하거나 축소합니다.  

##### <a name="htreeitem-getchildhtreeitem-hparent"></a>HTREEITEM GetChild(HTREEITEM hParent)  
 이 메서드는 트리 뷰 항목의 첫 번째 자식을 반환하거나 자식이 없는 경우 NULL을 반환합니다.  

##### <a name="htreeitem-getparenthtreeitem-hnode"></a>HTREEITEM GetParent(HTREEITEM hNode)  
 이 메서드는 트리 뷰의 모드에 대한 부모 핸들을 반환하거나 노드가 최상위 수준에 있는 경우 NULL을 반환합니다.  

##### <a name="htreeitem-getnextitemhtreeitem-hprevious"></a>HTREEITEM GetNextItem(HTREEITEM hPrevious)  
 노드의 모든 자식을 반복하도록 **GetChild**가 반환하는 핸들을 사용하여 이 메서드를 호출할 수 있습니다. 이 메서드는 동일한 부모를 공유하는 트리의 그 다음 형제를 반환합니다.  

##### <a name="uint-ischeckedhtreeitem-item"></a>UINT IsChecked(HTREEITEM item)  
 트리 뷰 노드가 선택되지 않았으면 이 메서드가 **0**을 반환하고 선택되었으면 **1**을 반환합니다.  

##### <a name="bool-isenabledhtreeitem-item"></a>BOOL IsEnabled(HTREEITEM item)  
 트리 뷰 노드를 사용하도록 설정된 경우 이 메서드가 TRUE를 반환하고 그렇지 않으면 FALSE를 반환합니다.  

##### <a name="intptr-commoncontroleventword-controlid-void-pinfo-bool-pcancel"></a>INT_PTR CommonControlEvent(WORD controlId, void* pInfo, BOOL \*pCancel)  
 이 메서드는 내부 전용입니다.  

##### <a name="hresult-seteventhandleritreeviewevent-peventhandler"></a>HRESULT SetEventHandler(ITreeViewEvent \*pEventHandler)  
 선택한 항목이 변경되거나 사용자가 트리 뷰 항목의 선택 상태를 변경할 때 알림을 받으려면 이 메서드를 호출합니다. 이러한 콜백을 수신하도록 구성 요소에 **ITreeViewEvent**를 구현해야 합니다.  

##### <a name="void-setselectedbackcolorcolorref-color"></a>void SetSelectedBackColor(COLORREF color)  
 선택한 항목에 사용할 배경색을 설정합니다.  

#### <a name="iwmiiteration-interface"></a>IWmiIteration 인터페이스  

```  
__interface IWmiIterator : IUnknown  
{  
    HRESULT Next(void);  
    HRESULT GetProperty(LPCTSTR propertyName, [out] LPVARIANT pValue);  
};  
```  

##### <a name="overview"></a>개요  
 일반적으로 WMI 호출을 작업할 때에는 **IWmiRepository**와 함께 이 인터페이스를 사용합니다. **IWmiIteration** 인터페이스를 사용하면 쿼리에서 반환하는 값을 반복할 수 있습니다.  

##### <a name="hresult-nextvoid"></a>HRESULT Next(void)  
 표 23에 나와 있는 것처럼 쿼리 결과의 다음 항목으로 이동합니다.  

### <a name="table-23-hresult-nextvoid-query-returns"></a>표 23. HRESULT Next(void) 쿼리 반환  

|**HRRESULT**|**설명**|  
|-|-|  
|**S_OK**|다음 결과로 이동합니다. **GetProperty**를 사용하여 해당 결과의 속성을 검색할 수 있습니다.|  
|**S_FALSE**|목록에 더 이상 항목이 없습니다.|  
|**E_NOT_SET**|쿼리 결과가 없습니다.|  

##### <a name="hresult-getpropertylpctstr-propertyname-out-lpvariant-pvalue"></a>HRESULT GetProperty(LPCTSTR propertyName, [out] LPVARIANT pValue)  
 이 메서드는 표 24 및 25에 나와 있는 것처럼 쿼리 결과 레코드에서 속성 값을 검색합니다.  

### <a name="table-24-hresult-getproperty"></a>표 24. HRESULT GetProperty  

|**매개 변수**|**설명**|  
|-|-|  
|**propertyName**|검색할 속성의 이름|  
|**pValue**|반환 시 속성 값을 포함하는 VARIANT 구조를 가리킵니다.|  

### <a name="table-25-hresult-getproperty-result"></a>표 25. HRESULT GetProperty 결과  

|**HRESULT**|**설명**|  
|-|-|  
|**S_OK**|속성 값이 검색되었습니다.|  
|**WBEM_E_NOT_FOUND**|이 이름의 속성이 없습니다.|  
|**E_NOT_VALID_STATE**|현재 레코드가 없습니다.|  

> [!NOTE]
>  **GetProperty** 메서드는 표 25에 나열되지 않은 다른 WMI 오류 코드를 반환할 수 있습니다. 나열된 값은 반환되는 일반적인 결과입니다.  

#### <a name="iwmirepository-interface"></a>IWmiRepository 인터페이스  

```  
__interface IWmiRepository : IUnknown  
{  
    HRESULT SetNamespace(LPCWSTR namespaceName);  
    HRESULT ExecQuery(LPCWSTR query, [out] IWmiIterator **ppIterator);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **WmiRepository** 구성 요소(**ID_WmiRepository**)를 통해 구현됩니다.  

##### <a name="hresult-setnamespacelpcwstr-namespacename"></a>HRESULT SetNamespace(LPCWSTR namespaceName)  
 이 메서드는 쿼리에 사용될 WMI 네임스페이스를 설정합니다. **ExecQuery**를 호출하기 전에 이 메서드를 먼저 호출해야 합니다. 이 메서드를 호출하지 않으면 네임스페이스는 root\cimv2가 됩니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

##### <a name="hresult-execquerylpcwstr-query-out-iwmiiterator-ppiterator"></a>HRESULT ExecQuery(LPCWSTR query, [out] IWmiIterator **ppIterator)  
 표 26 및 27에 나와 있는 것처럼 **SetNamespace**를 호출하여 설정된 WMI 네임스페이스에 대해 쿼리를 실행합니다.  

### <a name="table-26-hresult-execquery"></a>표 26. HRESULT ExecQuery  

|**매개 변수**|**설명**|  
|-|-|  
|**Query**|실행할 WMI 쿼리에 대한 문자열|  
|**ppIterator**|포인터를 인터페이스 포인터에 전달하며, 인터페이스 포인터는 반환 시 인터페이스로 채워져서 쿼리 결과에 대한 액세스를 제공합니다.|  

### <a name="table-27-hresult-query-result"></a>표 27. HRESULT 쿼리 결과  

|**HRESULT**|**설명**|  
|-|-|  
|**S_OK**|쿼리 성공|  
|**Other**|쿼리가 성공하지 못하면 WMI **HRESULT**를 반환|  

#### <a name="iformcontroller-interface"></a>IFormController 인터페이스  

```  
__interface IFormController : IUnknown  
{  
    Init(IWizardPageView *pView, IWizardPageContainer *pContainer);  
    SetPageInfo(ISettingsProperties *pPageInfo);  

    Validate(void);  

    AddToGroup(int groupControlId, int controlId);  
    UpdateCheckGroup(int groupControlId);  
    AddValidator(int controlId, IValidator *pValidator, IControl *pCOntrol = 0);  

    AddValidator(int controlId, LPCWSTR validatorId, LPCWSTR message, IValidator **ppValidator = nullptr);  
    DisableValidation(int controlId, BOOL disable);  

    AddField(LPCWSTR fieldName, int controlId, BOOL suppressLog, DialogControlTypes type);  
    AddRadioGroup(LPCWSTR groupName, int radioControlId);  
    EnableRadioGroup(LPCWSTR groupName, BOOL enable);  
    InitFields(IFieldCallback *pFieldCallback = nullptr);  
    SaveFields(IFieldCallback *pFieldCallback = nullptr);  
    BOOL IsFieldDisabled(int controlId);  

    InitSection(LPCWSTR key, LPCWSTR sectionCaption);  
    AddSummaryItem(LPCWSTR first, LPCWSTR second);  
    SuppressLogValue(LPCWSTR tsVariableName);  
    SaveText(int controlId, LPCWSTR tsVariableName, LPCWSTR summaryCaption);  
    LoadText(int controlId, LPCWSTR tsVariableName);  

    void ControlEvent(WORD eventId, WORD controlId);  
    BOOL IsValid(void);  
 };  
```  

##### <a name="overview"></a>개요  
 UDI 마법사의 각 페이지에는 이 인터페이스를 구현하는 자체 양식 컨트롤러가 있습니다. 이 컨트롤러를 사용하여 .config XML 파일의 필드 데이터를 페이지의 컨트롤에 연결합니다. 그러면 양식 컨트롤러가 사용자를 대신하여 대부분의 세부 정보를 처리합니다.  

#####  <a name="SettingUptheForm"></a> 양식 설정  
 일반적으로 페이지의 **OnWindowCreated** 메서드에서 양식 컨트롤러를 설정합니다. 이렇게 하려면 일반적으로 표 28처럼 메서드를 호출해야 합니다.  

### <a name="table-28-onwindowcreated-method"></a>표 28. OnWindowCreated 메서드  

|**방법**|**설명**|  
|-|-|  
|**Init**|양식 컨트롤러를 초기화|  
|**AddField**|문자열 이름인 .config XML 파일의 필드와 ID인 페이지 대화 상자의 컨트롤을 연결합니다.|  
|**AddRadioGroup**|라디오 단추를 대화 상자의 그룹 및 컨트롤에 연결하는 데 사용|  
|**AddToGroup**|사용하도록 또는 사용하지 않도록 설정된 "자식" 컨트롤을 부모와 함께 또는 선택된 라디오 단추에 따라 사용할 수 있도록 허용|  
|**InitFields**|양식을 설정하는 모든 **Add** 메서드를 호출한 후에 호출|  
|**Validate**|초기 유효성 검사를 수행|  

##### <a name="processing-form-events"></a>양식 이벤트 처리  
 **OnControlEvent** 메서드에 다음 호출을 추가:  

```  
Form()->ControlEvent(eventId, controlId);  
```  

 이 호출은 양식 관련 이벤트를 처리할 수 있도록 양식 컨트롤러에 이벤트를 전달합니다.  

##### <a name="save-form-data"></a>양식 데이터 저장  
 **OnNextClicked** 메서드에서 표 29의 양식 메서드를 호출합니다.  

### <a name="table-29-onnextclicked-method"></a>표 29. OnNextClicked 메서드  

|**방법**|**설명**|  
|-|-|  
|**InitSection**|이 페이지의 **요약** 페이지에 표시할 섹션 이름을 제공|  
|**SaveFields**|작업 순서 변수 및 **요약** 페이지에 필드 값 저장|  

#####  <a name="Init"></a> Init  

```  
HRESULT Init(IWizardPageView *pView, IWizardPageContainer *pContainer)  
```  

 일반적으로 페이지의 **OnWindowCreated** 메서드가 시작되는 부분에서 이 메서드를 호출합니다. 명령은 다음과 비슷합니다.  

```  
Form()->Init(View(), Container());  
```  

##### <a name="setpageinfo"></a>SetPageInfo  

```  
HRESULT SetPageInfo(ISettingsProperties *pPageInfo)  
```  

 이 메서드는 내부적으로 호출되므로 사용자가 직접 호출하면 안 됩니다. 양식 컨트롤러에 페이지의 XML을 제공합니다.  

##### <a name="validate"></a>Validate  

```  
HRESULT Validate(void)  
```  

 이 메서드는 컨트롤에 연결된 모든 유효성 검사기를 실행합니다. 유효성 검사기가 통과하지 못하는 경우 양식 컨트롤러는 경고 메시지를 표시하고 **다음** 단추를 비활성화한 다음, 유효성 검사기 처리를 중지합니다. 일반적으로 **OnWindowCreated** 메서드의 마지막 부분에서만 이 메서드를 호출하면 되며, 이 메서드는 항상 **S_OK**를 반환합니다.  

##### <a name="addtogroup"></a>AddToGroup  

```  
AddToGroup(int groupControlId, int controlId)  
```  

 이 메서드는 표 30에 나와 있는 것처럼 컨트롤을 확인란의 "자식"으로 또는 라디오 단추로 추가합니다. 부모 컨트롤을 선택하지 않으면 모든 자식 컨트롤이 비활성화됩니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

### <a name="table-30-addtogroup"></a>표 30. AddToGroup  

|**매개 변수**|**설명**|  
|-|-|  
|**groupControlId**|자식 컨트롤의 사용 상태를 제어하는 확인란 또는 라디오 단추의 ID|  
|**Controlld**|자식으로 추가하려면 컨트롤의 ID|  

##### <a name="updatecheckgroup"></a>UpdateCheckGroup  

```  
HRESULT UpdateCheckGroup(int groupControlId)  
```  

 이 메서드는 부모 컨트롤의 상태에 따라 그룹에 속한 자식 컨트롤의 활성화 또는 비활성화 상태를 업데이트합니다. 일반적으로 이 메서드는 양식 컨트롤러에서 알아서 호출하므로 사용자가 직접 호출할 필요가 없습니다.  

##### <a name="addvalidator"></a>AddValidator  

```  
HRESULT AddValidator(int controlId, IValidator *pValidator, IControl *pControl = 0)  
```  

 XML 대신 코드로 만들려는 유효성 검사기가 있는 경우에만 이 메서드를 호출하세요. 이 메서드는 항상 **S_OK**를 반환합니다.  

##### <a name="addvalidator"></a>AddValidator  

```  
HRESULT AddValidator(int controlId, LPCWSTR validatorId, LPCWSTR message, IValidator **ppValidator = nullptr)  
```  

 XML 대신 코드로 만들려는 유효성 검사기가 있는 경우에만 이 메서드를 호출하세요.  

##### <a name="disablevalidation"></a>DisableValidation  

```  
HRESULT DisableValidation(int controlId, BOOL disable)  
```  

 표 31처럼 컨트롤에 유효성 검사기를 사용하지 않도록 명시적으로 설정하거나 일반적인 유효성 검사를 복원하려는 경우 이 메서드를 호출합니다. 예를 들어 양식 유효성 검사의 범위에 포함되지 않는 컨트롤에 규칙을 사용하도록/사용하지 않도록 설정하고 컨트롤에 유효성 검사를 사용하지 않도록 설정해야 하는 경우에 이 메서드가 유용합니다. 다시 말해서, 사용자가 이 메서드를 호출할 일은 좀처럼 없습니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

### <a name="table-31-hresult-disablevalidation"></a>표 31. HRESULT DisableValidation  

|**매개 변수**|**설명**|  
|-|-|  
|**controlId**|유효성 검사를 사용하도록 또는 사용하지 않도록 설정하는 컨트롤|  
|**사용 안 함**|유효성 검사를 사용하지 않으려면 TRUE로 설정하고 일반 유효성 검사를 복원하려면 FALSE로 설정|  

#####  <a name="AddField"></a> AddField  

```  
HRESULT AddField(LPCWSTR fieldName, int controlId, BOOL suppressLog, DialogControlTypes type)  
```  

 표 32처럼 .config XML 파일의 **Field** 요소 이름과 페이지 대화 상자의 컨트롤 ID 사이에 컨트롤 매핑을 추가합니다. **InitFields** 메서드가 이 정보를 사용하므로 **InitFields**를 호출하려면 먼저 이 메서드를 호출해야 합니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

### <a name="table-32-hresult-addfield"></a>표 32. HRESULT AddField  

|**매개 변수**|**설명**|  
|-|-|  
|**Fieldname**|페이지의 XML에 표시되는 필드 이름|  
|**controlId**|페이지의 대화 상자 템플릿에 표시되는 컨트롤 ID|  
|**suppressLog**|이 필드의 값을 로그 파일에 기록하지 않으려면 TRUE로 설정합니다. 암호 또는 PIN 필드에 대해서는 이 매개 변수를 항상 TRUE로 설정합니다.|  
|**유형**|컨트롤 형식으로 다음 중 하나입니다.<br /><br /> -   **CONTROL_STATIC_TEXT**<br />-   **CONTROL_COMBO_BOX**<br />-   **CONTROL_LIST_VIEW**<br />-   **CONTROL_PROGRESS_BAR**<br />-   **CONTROL_GENERIC**<br />-   **CONTROL_RADIO_BUTTON**<br />-   **CONTROL_CHECK_BOX**<br />-   **CONTROL_TREE_VIEW**|  

#####  <a name="AddRadioGroup"></a> AddRadioGroup  

```  
HRESULT AddRadioGroup(LPCWSTR groupName, int radioControlId)  
```  

 이 메서드는 표 33처럼 명명된 라디오 단추 그룹에 컨트롤을 추가합니다. **InitFields** 메서드를 호출하기 전에 이 메서드를 호출해야 합니다. 이 메서드는 **RadioGroup** 요소의 특성을 사용하여 그룹 내 모든 라디오 단추 컨트롤의 설정을 제어하기 때문입니다. 예를 들어 모든 라디오 단추가 비활성화되도록 라디오 그룹을 잠글 수 있지만, 자식 컨트롤은 선택된 라디오 단추에 따라서만 활성화 또는 비활성화됩니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

### <a name="table-33-hresult-addradiogroup"></a>표 33. HRESULT AddRadioGroup  

|**매개 변수**|**설명**|  
|-|-|  
|**groupName**|이 페이지의 라디오 단추 그룹을 정의하는 문자열|  
|**radioControlId**|이 그룹에 추가할 단일 라디오 단추의 ID|  

##### <a name="enableradiogroup"></a>EnableRadioGroup  

```  
HRESULT EnableRadioGroup(LPCWSTR groupName, BOOL enable)  
```  

 이 메서드를 사용하면 전체 라디오 단추 그룹을 사용하거나 사용하지 않도록 설정할 수 있습니다. 라디오 그룹을 사용하지 않도록 설정하면 그룹 내 모든 라디오 단추 컨트롤뿐 아니라 **AddToGroup**을 사용하여 추가된 라디오 단추의 자식 컨트롤도 비활성화됩니다. 표 34 및 35를 참조하세요.  

### <a name="table-34-enableradiogroup"></a>표 34. EnableRadioGroup  

|**매개 변수**|**설명**|  
|-|-|  
|**groupName**|**AddRadioGroup**을 호출하여 이미 정의한 라디오 단추 그룹의 이름|  
|**사용**|라디오 단추 그룹을 사용하려면 TRUE로 설정하고 그룹을 사용하지 않으려면 FALSE로 설정|  

### <a name="table-35-hresult-enableradiogroup"></a>표 35. HRESULT EnableRadioGroup  

|**HRESULT**|**설명**|  
|-|-|  
|**S_OK**|그룹이 사용되거나 사용되지 않음|  
|**E_INVALIDARG**|사용자가 입력한 이름을 사용하는 라디오 단추 그룹이 없습니다.|  

#####  <a name="InitFields"></a> InitFields  

```  
HRESULT InitFields(IFieldCallback *pFieldCallback = nullptr)  
```  

 이 메서드를 호출하기 전에, XML이 제어할 수 있는 각 필드에 대해 **AddField**를 호출해야 합니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

 **pFieldCallback** 매개 변수는 선택 사항입니다. 이 매개 변수를 제공할 경우 양식 컨트롤러는 **CONTROL_STATIC_TEXT** 또는 **CONTROL_CHECK_BOX**가 아닌 컨트롤에 대해 **SetFieldDefault**를 호출합니다. 이 동작을 통해 XML에서 기본값을 검색하고 컨트롤에 직접 설정할 수 있습니다.  

#####  <a name="SaveFields"></a> SaveFields  

```  
HRESULT SaveFields(IFieldCallback *pFieldCallback = nullptr)  
```  

 이 메서드는 작업 순서 변수 및 **요약** 페이지에 표시되는 요약 데이터에 필드 값을 저장합니다. **pFieldCallback**에서 포인터를 제공하면 **CONTROL_STATIC_TEXT**를 지원하지 않는 컨트롤에 대한 값 저장을 처리할 수 있습니다.  

##### <a name="isfielddisabled"></a>IsFieldDisabled  

```  
BOOL IsFieldDisabled(int controlId)  
```  

 이 메서드를 사용하면 XML에서 필드가 사용되지 않는지 확인할 수 있습니다.  

#####  <a name="InitSection"></a> InitSection  

```  
HRESULT InitSection(LPCWSTR key, LPCWSTR sectionCaption)  
```  

 이 메서드는 표 36처럼 **요약** 페이지에 표시될 요약 데이터를 초기화합니다. **SaveFields**를 호출하기 전에 **OnNextClicked**에서 이 메서드를 호출해야 합니다. 이 메서드는 항상 **S_OK**를 반환합니다.  

### <a name="table-36-hresult-initsection"></a>표 36. HRESULT InitSection  

|**매개 변수**|**설명**|  
|-|-|  
|**Key**|이 매개 변수는 페이지에서 고유해야 합니다. 페이지마다 고유의 요약 정보를 제공하도록 보장하기 위해 사용됩니다.|  
|**sectionCaption**|이 페이지의 요약 정보를 제공하는 **요약** 페이지에 표시될 헤더입니다. 일반적으로 이 매개 변수의 값으로 **DisplayName()** 을 사용합니다.|  

##### <a name="addsummaryitem"></a>AddSummaryItem  

```  
HRESULT AddSummaryItem(LPCWSTR first, LPCWSTR second)  
```  

 이 메서드를 사용하면 XML로 설정한 항목보다 많은 **요약** 페이지에 요약 항목을 추가할 수 있습니다. 표 37을 참조하세요.  

### <a name="table-37-hresult-addsummaryitem"></a>표 37. HRESULT AddSummaryItem  

|**매개 변수**|**설명**|  
|-|-|  
|**First**|요약 항목에 대한 캡션으로, 왼쪽에 표시|  
|**Second**|오른쪽에 표시되는 값|  

##### <a name="suppresslogvalue"></a>SuppressLogValue  

```  
HRESULT SuppressLogValue(LPCWSTR tsVariableName)  
```  

 로그 파일에 값을 기록하지 않으려는 작업 순서 변수에 대해 이 메서드를 호출합니다. 암호, Pin 또는 사용자가 입력하는 기타 중요한 값을 저장하는 작업 순서 변수에 대해 이 메서드를 호출합니다.  

##### <a name="savetext"></a>SaveText  

```  
HRESULT SaveText(int controlId, LPCWSTR tsVariableName, LPCWSTR summaryCaption)  
```  

 이 메서드는 텍스트 컨트롤의 값을 작업 순서 변수 및 요약 섹션에 저장합니다. 일반적으로 양식 컨트롤러가 모든 필드에 대해 이 메서드를 알아서 호출하므로 사용자가 직접 호출할 필요는 없습니다. 표 38을 참조하세요.  

### <a name="table-38-hresult-savetext"></a>표 38. HRESULT SaveText  

|**매개 변수**|**설명**|  
|-|-|  
|**controlId**|저장하려는 값(또는 텍스트를 반환할 수 있는 기타 컨트롤)을 포함하고 있는 텍스트 상자의 ID|  
|**tsVariableName**|수정하려는 작업 순서 변수의 이름|  
|**summaryCaption**|이 값의 **요약** 페이지에 대한 캡션|  

##### <a name="loadtext"></a>LoadText  

```  
HRESULT LoadText(int controlId, LPCWSTR tsVariableName)  
```  

 이 메서드는 작업 순서 변수의 값을 읽고 텍스트 상자를 이 값으로 설정합니다.  

##### <a name="controlevent"></a>ControlEvent  

```  
void ControlEvent(WORD eventId, WORD controlId)  
```  

 양식 컨트롤러가 컨트롤 이벤트를 처리할 수 있도록 **OnControlEvent** 메서드에서 이 메서드를 호출합니다. 이렇게 해야 양식 컨트롤러가 올바르게 작동합니다. 사용자가 이 메서드에 전달하는 값은 **OnControlEvent** 메서드에 전달되는 값과 동일합니다.  

##### <a name="isvalid"></a>IsValid  

```  
BOOL IsValid(void)  
```  

 이 메서드는 가장 최근의 양식 유효성 검사 상태를 반환합니다. 컨트롤 유효성 검사기가 오류를 보고하면 이 메서드는 FALSE를 반환합니다. 즉, 페이지의 모든 컨트롤이 유효한 경우에만 TRUE를 반환합니다.  

#### <a name="ivalidator-interface"></a>IValidator 인터페이스  

```  
__interface IValidator : IUnknown  
{  
    HRESULT Init(IControl *pControl, LPCTSTR message);  
    HRESULT Init(IControl *pControl, IWizardPageContainer *pContainer, IStringProperties *pProperties);  
    BOOL, IsValid(LPBSTR pMessage);  
    HRESULT SetProperty(int propertyId, LPVARIANT pValue);  
    HRESULT SetProperty(int propertyId, IUnknown *pUnknown);  
    HRESULT SetProperty)(int propertyId, LPCTSTR pValue);  
};  
```  

##### <a name="overview"></a>개요  
 *유효성 검사기*는 페이지에 있는 단일 컨트롤의 유효성을 검사할 수 있는 구성 요소입니다. 유효성 검사기를 구현하는 가장 쉬운 방법은 유효성 검사기를 BaseValidator.h 헤더 파일에 정의된 **BaseValidator** 클래스의 서브클래스로 만드는 것입니다.  

##### <a name="hresult-initicontrol-pcontrol-lpctstr-message"></a>HRESULT Init(IControl \*pControl, LPCTSTR message)  
 코드로 유효성 검사기를 만드는 경우 이 메서드를 호출하여 유효성 검사기를 초기화할 수 있습니다. 표 39를 참조하세요.  

### <a name="table-39-hresult-init"></a>표 39. HRESULT Init  

|**매개 변수**|**설명**|  
|-|-|  
|**pControl**|유효성 검사기가 검사해야 하는 컨트롤|  
|**Message**|컨트롤이 유효하지 않은 경우 페이지에 표시할 메시지|  

##### <a name="hresult-initicontrol-pcontrol-iwizardpagecontainer-pcontainer-istringproperties-pproperties"></a>HRESULT Init(IControl \*pControl, IWizardPageContainer \*pContainer, IStringProperties \*pProperties)  
 양식 컨트롤러는 페이지의 XML에 따라 만드는 유효성 검사기를 초기화하기 위해 이 메서드를 호출합니다. 표 40을 참조하세요.  

### <a name="table-40-hresult-init-method"></a>표 40. HRESULT Init 메서드  

|**매개 변수**|**설명**|  
|-|-|  
|**pControl**|유효성 검사기가 검사해야 하는 컨트롤|  
|**pContainer**|유효성 검사기가 로거에 액세스해야 하거나 다른 구성 요소를 만들어야 하는 경우|  
|**pProperties**|유효성 검사기의 속성(setter 요소)에 대한 액세스 제공|  

##### <a name="bool-isvalidlpbstr-pmessage"></a>BOOL, IsValid(LPBSTR pMessage)  
 이 메서드는 컨트롤이 유효하면 TRUE를 반환하고 컨트롤이 잘못되었으면 FALSE를 반환합니다. 반환 시, **pMessage**는 컨트롤이 유효하지 않을 때 표시할 메시지를 포함하고 있는 새 **BSTR**로 채워져야 합니다.  

##### <a name="hresult-setpropertyint-propertyid-lpvariant-pvalue"></a>HRESULT SetProperty(int propertyId, LPVARIANT pValue)  
 XML에 제공되지 않은 추가 값이 필요한 경우 이 메서드를 구현하면 됩니다.  

##### <a name="hresult-setpropertyint-propertyid-iunknown-punknown"></a>HRESULT SetProperty(int propertyId, IUnknown \*pUnknown)  
 XML에 제공되지 않은 추가 값이 필요한 경우 이 메서드를 구현하면 됩니다.  

##### <a name="hresult-setpropertyint-propertyid-lpctstr-pvalue"></a>HRESULT SetProperty)(int propertyId, LPCTSTR pValue)  
 XML에 제공되지 않은 추가 값이 필요한 경우 이 메서드를 구현하면 됩니다.  

#### <a name="iregex-interface"></a>IRegEx 인터페이스  

```  
__interface IRegEx : IUnknown  
{  
    BOOL MatchesRegex(LPCTSTR input, LPCTSTR regex);  
    HRESULT GetMatch(size_t index, LPBSTR pValue);  
};  
```  

 이 메서드는 **ID_Regex** 구성 요소(IRegex.h)를 통해 구현되며 정규식 처리를 지원합니다.  

##### <a name="bool-matchesregexlpctstr-input-lpctstr-regex"></a>BOOL MatchesRegex(LPCTSTR input, LPCTSTR regex)  
 이 메서드는 입력된 텍스트에 대해 정규식을 실행합니다. C++ 표준 라이브러리의 **regex_match** 함수를 사용하여 실제 작업을 수행합니다. 이 메서드는 일치 항목이 있으면 TRUE를 반환하고 그렇지 않으면 FALSE를 반환합니다.  

##### <a name="hresult-getmatchsizet-index-lpbstr-pvalue"></a>HRESULT GetMatch(size_t index, LPBSTR pValue)  
 이 메서드를 사용하면 가장 최근의 **MatchesRegex** 호출에서 일치 항목을 검색할 수 있습니다. 이 메서드는 오류 처리가 없으며 **S_OK**를 반환하거나 예외를 throw합니다.  

#### <a name="isummaryinfo-interface"></a>ISummaryInfo 인터페이스  

```  
__interface ISummaryInfo : IUnknown  
{  
    size_t Count(void);  
    HRESULT Clear(void);  
    HRESULT AddInfo(LPCTSTR pFirst, LPCTSTR pSecond);  
    HRESULT GetInfo(size_t index, LPBSTR pFirst, LPBSTR pSecond);  
    HRESULT GetCaption(LPBSTR pCaption);  
    HRESULT SetCaption(LPCTSTR caption);  
};  
```  

 이 인터페이스를 직접 사용할 필요가 없습니다. 그 대신 **IFormController**를 사용합니다.  

#### <a name="isummarybag"></a>ISummaryBag  

```  
__interface ISummaryBag : IUnknown  
{  
    size_t Count(void);  
    HRESULT GetInfoByIndex(size_t index, [out] ISummaryInfo **ppSummary);  
    HRESULT GetInfoByKey(LPCTSTR key, [out] ISummaryInfo **ppSummary);  
};  
```  

 이 인터페이스를 직접 사용할 필요가 없습니다. 그 대신 **IFormController**를 사용합니다.  

#### <a name="itsvariablebag-interface"></a>ITSVariableBag 인터페이스  

```  
__interface ITSVariableBag : IUnknown  
{  
    void GetValue([in] LPCTSTR variableName, [out] LPBSTR pValue);  
    void SetValue([in] LPCTSTR variableName, [in] LPCTSTR pValue);  
    void Clear(void);  
    HRESULT Remove([in] LPCTSTR variableName);  
    HRESULT SuppressLogValue([in] LPCTSTR variableName);  
    void Save(void);  
};  
```  

 이 인터페이스는 작업 순서 변수에 대한 액세스를 제공합니다. 페이지의 **TSVariables()** 메서드를 사용하여 이 인터페이스에 액세스할 수 있습니다.  

##### <a name="void-getvaluein-lpctstr-variablename-out-lpbstr-pvalue"></a>void GetValue([in] LPCTSTR variableName, [out] LPBSTR pValue)  
 이 메서드는 작업 순서 변수의 값을 읽습니다.  

> [!NOTE]
>  값은 첫 번째 읽기 후에 캐시됩니다.  

##### <a name="void-setvaluein-lpctstr-variablename-in-lpctstr-pvalue"></a>void SetValue([in] LPCTSTR variableName, [in] LPCTSTR pValue)  
 이 메서드는 작업 순서 변수의 값을 설정합니다. 이 값은 메모리에 저장됩니다. UDI 마법사에서 **마침**을 클릭하면 작업 순서 값이 기록됩니다.  

##### <a name="void-clearvoid"></a>void Clear(void)  
 이 메서드는 메모리에 저장된 모든 작업 순서 값을 제거합니다.  

##### <a name="hresult-removein-lpctstr-variablename"></a>HRESULT Remove([in] LPCTSTR variableName)  
 이 메서드는 메모리에서 특정 작업 순서 값을 제거합니다. 다음에 동일한 작업 순서 이름으로 **GetValue**를 호출하면 이 메서드는 작업 순서에서 해당 값을 검색하려고 시도합니다.  

##### <a name="hresult-suppresslogvaluein-lpctstr-variablename"></a>HRESULT SuppressLogValue([in] LPCTSTR variableName)  
 UDI 마법사에서 **마침**을 클릭하는 경우처럼 작업 순서 변수가 기록될 때마다 로그 파일에 이름과 값이 기록됩니다. 특정 작업 순서 변수에 대해 암호 또는 Pin 같은 중요한 값을 기록하지 못하게 하려면 이 메서드를 호출하세요.  

##### <a name="void-savevoid"></a>void Save(void)  
 이 메서드는 **SetValue**를 호출하여 설정된 모든 작업 순서 값을 저장합니다.  

#### <a name="itsvariablerepository-interface"></a>ITSVariableRepository 인터페이스  

```  
__interface ITSVariableRepository : IUnknown  
{  
    void GetValue([in] LPCTSTR variableName, BOOL logValue, [out] LPBSTR pValue);  
    void SetValue([in] LPCTSTR variableName, BOOL logValue, [in] LPCTSTR value);  
};  
```  

 이 인터페이스는 **TSVariableBag**에서 작업 순서 변수를 읽고 쓰기 위한 내부용으로 사용됩니다.  

#### <a name="iwizardfinish-interface"></a>IWizardFinish 인터페이스  

```  
__interface IWizardFinish : IUnknown  
{  
    HRESULT Canceled(void);  
    HRESULT Finished(void);  
};  
```  

 이 인터페이스는 UDI 마법사에서 **마침** 또는 **취소**를 클릭하면 추가 처리가 수행되는 고급 시나리오를 구현할 때 유용합니다. UDI 마법사에는 **마침**을 클릭하면 작업 순서 변수를 저장하는 **마침** 작업이 포함되어 있습니다. 마법사를 취소하면 작업에서는 **OSDSetupWizCancelled** 작업 순서 변수만 TRUE로 설정하고 다른 작업 순서 변수의 변경 내용을 저장하지 않습니다.  

 사용자 고유의 완료 구성 요소를 만드는 경우 다음과 같은 코드에 구성 요소를 등록해야 합니다.  

```  
Register<MyFinishTaskFactory>(ID_MyFinishTask, pRegistry);  

PWizardFinish pFinish;  
CreateInstance(pRegistry, ID_MyFinishTask, &pFinish);  

PWizardFinishService pService;  
GetService<IWizardFinishService>(pRegistry, &pService);  

pService->Register(pFinish);  
```  

#### <a name="ibindablelist-interface"></a>IBindableList 인터페이스  

```  
__interface IBindableList : IUnknown  
{  
    size_t Count(void);  
    HRESULT GetCaption(size_t index, LPBSTR pCaption);  
};  
```  

 **Bind** 메서드를 호출하여 콤보 상자에 바인딩할 데이터 원본 구성 요소가 있는 경우 이 인터페이스를 구현하세요.  

##### <a name="sizet-countvoid"></a>size_t Count(void)  
 이 메서드는 목록의 항목 수를 반환합니다.  

##### <a name="hresult-getcaptionsizet-index-lpbstr-pcaption"></a>HRESULT GetCaption(size_t index, LPBSTR pCaption)  
 이 메서드는 특정 인덱스에 있는 항목의 캡션을 반환합니다.  

#### <a name="idatanodes-interface"></a>IDataNodes 인터페이스  

```  
__interface IDataNodes : IUnknown  
{  
    size_t Count();  
    HRESULT SetCaptionProperty(LPCTSTR captionProperty);  
    HRESULT GetProperty(size_t index, LPCTSTR propertyName, [out] LPBSTR propertyValue);  
    HRESULT GetNode(size_t index, [out] ISettingsProperties **ppNode);  
};  
```  

 이 인터페이스는 페이지에 저장할 수 있는 계층적 데이터에 대한 액세스를 제공합니다. 이 인터페이스는 **Settings** 메서드를 통해 페이지에 제공되는 **ISettingsProperties** 인터페이스의 메서드를 통해 얻을 수 있습니다.  

 페이지의 XML 데이터는 다음과 비슷합니다.  

```  
      <Data Name="Network">  
        <DataItem>  
          <Setter Property="DisplayName">Public</Setter>  
          <Setter Property="Share">\\servername\Share</Setter>  
        </DataItem>  
        <DataItem>  
          <Setter Property="DisplayName">Dev Team</Setter>  
          <Setter Property="Share">\\servername\DevShare</Setter>  
        </DataItem>  
      </Data>  
```  

 **Settings()->GetDataNode(L"Network", &pData)** 를 호출하면 두 데이터 항목(각 항목은 두 개 속성 포함)이 포함된 **IDataNodes** 인스턴스가 제공됩니다.  

##### <a name="sizet-count"></a>size_t Count()  
 이 메서드는 **DataItem** 요소 수를 반환합니다.  

##### <a name="hresult-setcaptionpropertylpctstr-captionproperty"></a>HRESULT SetCaptionProperty(LPCTSTR captionProperty)  
 이 인터페이스를 지원하는 구성 요소는 **IBindableList**도 지원하며, 따라서 콤보 상자를 페이지의 XML 데이터로 간편하게 채울 수 있습니다. 이 메서드는 이 바인딩에 사용할 각 **DataItem** 요소의 속성(setter)을 제어합니다. 예를 들어 **DisplayName**을 사용하여 이 메서드를 호출하면 데이터 바인딩에 해당 setter 속성이 사용됩니다. 그러면 콤보 상자에 **Public** 및 **Dev Team**이 항목으로 포함됩니다.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propertyname-out-lpbstr-propertyvalue"></a>HRESULT GetProperty(size_t index, LPCTSTR propertyName, [out] LPBSTR propertyValue)  
 이 메서드는 **DataItem** 요소 중 하나에서 속성을 가져옵니다. 표 41 및 42를 참조하세요.  

### <a name="table-41-dataitem-getproperty"></a>표 41. DataItem GetProperty  

|**매개 변수**|**설명**|  
|-|-|  
|**Index**|속성 값을 검색할 **DataItem**의 인덱스 값(0부터 시작)|  
|**propertyName**|값을 검색할 setter 속성의 이름|  
|**propertyValue**|반환 시 속성의 문자열 값을 포함|  

### <a name="table-42-hresult-getproperty"></a>표 42. HRESULT GetProperty  

|||  
|-|-|  
|**HRESULT**|**설명**|  
|**S_OK**|속성이 검색되었습니다.|  
|**E_INVALIDARG**|인덱스가 배열의 끝을 지났습니다.|  

##### <a name="hresult-getnodesizet-index-out-isettingsproperties-ppnode"></a>HRESULT GetNode(size_t index, [out] ISettingsProperties **ppNode)  
 이 메서드는 **GetProperty**와 비슷하지만, **DataItem**에서 값을 반환하는 대신  **ISettingsProperties** 인터페이스에 래핑된 전체 **DataItem**을 반환합니다. 표 43 및 44를 참조하세요.  

### <a name="table-43-hresult-getnode"></a>표 43. HRESULT GetNode  

|**매개 변수**|**설명**|  
|-|-|  
|인덱스|속성 값을 검색할 **DataItem**의 인덱스 값(0부터 시작)|  
|**ppNode**|종료 시 **DataItem** 노드를 래핑하는 **ISettingsProperties** 인터페이스|  

### <a name="table-44-hresult-getnode-results"></a>표 44. HRESULT GetNode 결과  

|**HRESULT**|**설명**|  
|-|-|  
|**S_OK**|노드가 검색되었습니다.|  
|**E_INVALIDARG**|인덱스가 배열의 끝을 지났습니다.|  

#### <a name="ifactoryregistry-interface"></a>IFactoryRegistry 인터페이스  

```  
__interface IFactoryRegistry : IUnknown  
{  
    void Register(LPCTSTR type,  IClassFactory *pFactory);  
    HRESULT LoadAndRegister(LPCTSTR dllName, ILogger *pLogger);  
    BOOL Contains(LPCTSTR type);  
    HRESULT GetFactory(LPCTSTR type,  IClassFactory **ppFactory);  
    HRESULT CreateInstance(LPCTSTR type,  IUnknown **ppInstance);  
    HRESULT SetContainer(IWizardPageContainer *pContainer);  
    HRESULT RegisterService(REFGUID iid, IUnknown *pService);  
    HRESULT GetService(REFGUID iid,  IUnknown **ppService);  
};  
```  

##### <a name="overview"></a>개요  
 새 사용자 지정 페이지를 만들 때 적어도 **IClassFactory**를 구현하는 클래스인 *페이지 팩터리*를 만들어야 합니다. (팩터리의 기본 클래스로 **ClassFactoryImpl**을 사용할 수 있습니다.)  

##### <a name="void-registerlpctstr-type--iclassfactory-pfactory"></a>void Register(LPCTSTR type,  IClassFactory \*pFactory)  
 이 메서드는 클래스 팩터리를 레지스트리에 등록합니다. 표 45를 참조하세요.  

### <a name="table-45-iclassfactory-void-register"></a>표 45. IClassFactory void 레지스터  

|**매개 변수**|**설명**|  
|-|-|  
|**유형**|사용자가 등록하는 팩터리를 식별하는 문자열로, 일반적으로 이 매개 변수는 고유해야 하므로 문자열에 회사 이름이 있어야 합니다.|  
|**pFactory**|클래스 팩터리 인스턴스에 대한 포인터|  

##### <a name="hresult-loadandregisterlpctstr-dllname-ilogger-plogger"></a>HRESULT LoadAndRegister(LPCTSTR dllName, ILogger \*pLogger)  
 이 메서드는 내부 전용입니다.  

##### <a name="bool-containslpctstr-type"></a>BOOL Contains(LPCTSTR type)  
 이 메서드는 일반적으로 내부용입니다. 클래스 팩터리가 형식에 대해 등록되었는지 여부를 확인합니다.  

##### <a name="hresult-getfactorylpctstr-type--iclassfactory-ppfactory"></a>HRESULT GetFactory(LPCTSTR type,  IClassFactory **ppFactory)  
 이 메서드를 사용하면 클래스 팩터리를 검색할 수 있습니다. 일반적으로 사용자는 **CreateInstance**를 호출합니다. 그러나 같은 구성 요소를 대량으로 만들려는 경우 팩터리를 검색한 후 사용자 대신 인스턴스를 만들라고 팩터리에 요청하는 것이 보다 효율적입니다.  

##### <a name="hresult-createinstancelpctstr-type--iunknown-ppinstance"></a>HRESULT CreateInstance(LPCTSTR type,  IUnknown **ppInstance)  
 이 메서드는 지정된 형식의 새로운 구성 요소 인스턴스를 만듭니다. 이 메서드 대신 형식이 안전한 개체를 만들 수 있는 **CreateInstance** 템플릿 메서드를 사용하세요.  

##### <a name="hresult-setcontaineriwizardpagecontainer-pcontainer"></a>HRESULT SetContainer(IWizardPageContainer \*pContainer)  
 이 메서드는 내부 전용입니다.  

##### <a name="hresult-registerservicerefguid-iid-iunknown-pservice"></a>HRESULT RegisterService(REFGUID iid, IUnknown \*pService)  
 *서비스*는 여러 위치에 사용할 수 있는 구성 요소의 단일 인스턴스입니다. 이 메서드를 사용하여 서비스를 한 페이지에서 등록한 후 다른 페이지에서 동일한 인스턴스를 검색할 수 있습니다.  

##### <a name="hresult-getservicerefguid-iid--iunknown-ppservice"></a>HRESULT GetService(REFGUID iid,  IUnknown **ppService)  
 이 메서드는 이전에 RegisterService를 호출하여 등록된 서비스를 검색합니다.  

##### <a name="hresult-setlanguagelangid-languageid"></a>HRESULT SetLanguage(LANGID languageId)  
 이 메서드는 UDI 마법사의 언어를 사용자가 **languageId** 매개 변수에서 입력한 언어 식별자로 설정합니다.  

##### <a name="langid-getlanguage"></a>LANGID GetLanguage()  
 이 메서드는 사용자가 UDI 마법사에 대해 **/locale** 명령줄 매개 변수를 사용하여 입력한 언어 식별자 값을 반환합니다. 이 메서드는 다음 값 중 하나를 반환합니다.  

-   **/locale** 명령줄 매개 변수를 사용하여 입력한 언어 식별자 값  

-   **/locale** 명령줄 매개 변수를 입력하지 않은 경우 0  

#### <a name="ilogger-interface"></a>ILogger 인터페이스  

```  
__interface ILogger : IUnknown  
{  
    HRESULT Init(LPCWSTR logFilename);  
    HRESULT MoveLog(LPCWSTR logFilename);  
    HRESULT LogBase(EMessageType messageType, LPCTSTR component, SYSTEMTIME eventTime, LPCTSTR message);  
    HRESULT Log(EMessageType messageType, LPCTSTR component, LPCTSTR message);  
    HRESULT Error(HRESULT error, LPCTSTR component, LPCTSTR message);  
    HRESULT Error2(HRESULT error, LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Normal(LPCTSTR component, LPCTSTR message);      
    HRESULT Normal2(LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Verbose(LPCTSTR component, LPCTSTR message);  
    HRESULT Verbose2(LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Debug(LPCWSTR component, LPCWSTR message);  
    HRESULT EnableDebug(BOOL debug);  
    HRESULT Close(void);  
    HRESULT GetLogFilename(LPBSTR pFilename);  
};  
```  

##### <a name="overview"></a>개요  
 UDI 마법사는 로그 파일에 정보를 기록하며, 이 정보는 필드에서 발견된 문제를 해결하는 데 도움이 됩니다. 페이지에서 정보를 기록하는 것이 좋습니다. 페이지의 **Logger()** 메서드를 사용하여 페이지 내에서 이 인터페이스에 대한 포인터를 얻을 수 있습니다. 로그 파일의 줄에는 오류, 정상, 자세한 정보 표시 또는 디버그 메시지를 나타내는 “수준”이 포함됩니다.  

> [!NOTE]
>  디버그 지원을 켜지 않으면 디버그 메시지가 로그 파일에 저장되지 않습니다. .config 파일의 **Style** 요소에 다음 줄을 추가하여 디버그 지원을 켤 수 있습니다.  

```  
<Setter Property="debug">true</Setter>  
```  

##### <a name="init"></a>Init  

```  
HRESULT Init(LPCWSTR logFilename)  
```  

 이 메서드는 내부 전용입니다.  

##### <a name="movelog"></a>MoveLog  

```  
HRESULT MoveLog(LPCWSTR logFilename)  
```  

 이 메서드는 내부 전용입니다.  

##### <a name="logbase"></a>LogBase  

```  
HRESULT LogBase(EMessageType messageType, LPCTSTR component, SYSTEMTIME eventTime, LPCTSTR message)  
```  

 이 메서드는 내부 전용입니다.  

##### <a name="log"></a>로그  

```  
HRESULT Log(EMessageType messageType, LPCTSTR component, LPCTSTR message)  
```  

 이 메서드는 내부 전용입니다.  

##### <a name="error"></a>오류  

```  
HRESULT Error(HRESULT error, LPCTSTR component, LPCTSTR message)  
```  

 오류에 대한 정보를 기록하려면 이 메서드를 호출합니다. 표 46을 참조하세요.  

### <a name="table-46-hresult-error"></a>표 46. HRESULT 오류  

|**매개 변수**|**설명**|  
|-|-|  
|**오류**|호출에서 반환된 오류 코드(이 코드는 로그 항목에 숫자로 표시됨)|  
|**구성 요소**|오류의 출처를 식별하는 문자열로, 오류의 출처는 일반적으로 사용자가 작성한 페이지 또는 구성 요소입니다.|  
|**Message**|오류의 원인을 설명하는 메시지|  

#####  <a name="Error2"></a> Error2  

```  
HRESULT Error2(HRESULT error, LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 이 메서드는 **Error** 메서드와 비슷하지만 사용자가 두 부분으로 구성된 메시지를 제공할 수 있습니다. 최종 메시지는 출력 파일에서 "message" 및 "message2"를 갖게 됩니다. 간단하고 편리한 메서드입니다.  

##### <a name="normal"></a>일반  

```  
HRESULT Normal(LPCTSTR component, LPCTSTR message)  
```  

 이 메서드는 일반 메시지를 기록합니다. 매개 변수에 대한 내용은 [Error](#Error) 메서드의 설명을 참조하세요.  

##### <a name="normal2"></a>Normal2  

```  
HRESULT Normal2(LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 이 메서드는 일반 메시지를 기록합니다. 매개 변수에 대한 내용은 [Error2](#Error2) 메서드의 설명을 참조하세요.  

##### <a name="verbose"></a>자세한 정보 표시  

```  
HRESULT Verbose(LPCTSTR component, LPCTSTR message)  
```  

 이 메서드는 자세한 정보 표시 메시지를 기록합니다. 매개 변수에 대한 내용은 [Error](#Error) 메서드의 설명을 참조하세요.  

##### <a name="verbose2"></a>Verbose2  

```  
HRESULT Verbose2(LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 이 메서드는 자세한 정보 표시 메시지를 기록합니다. 매개 변수에 대한 내용은 [Error2](#Error2) 메서드의 설명을 참조하세요.  

##### <a name="debug"></a>디버그  

```  
HRESULT Debug(LPCWSTR component, LPCWSTR message)  
```  

 이 메서드는 디버그 메시지를 기록합니다. 매개 변수에 대한 내용은 [Error](#Error) 메서드의 설명을 참조하세요. 디버그를 사용하도록 설정하지 않으면 디버그 메시지가 파일에 저장되지 않습니다. 자세한 내용은 개요 섹션을 참조하세요.  

##### <a name="enabledebug"></a>EnableDebug  

```  
HRESULT EnableDebug(BOOL debug)  
```  

 이 메서드는 내부 전용입니다.  

##### <a name="close"></a>닫기  

```  
HRESULT Close(void)  
```  

 이 메서드는 내부 전용입니다.  

##### <a name="getlogfilename"></a>GetLogFilename  

```  
HRESULT GetLogFilename(LPBSTR pFilename)  
```  

 이 메서드는 로그 파일의 이름을 검색합니다.  

#### <a name="iorientation-interface"></a>IOrientation 인터페이스  

```  
__interface IOrientation : IUnknown  
{  
    void SetController(IWizardDialogController *pController);  
    int AddPage(LPCTSTR name);  
    void SelectPage(int index);  
};  
```  

 이 인터페이스는 내부 전용입니다.  

#### <a name="isettings-interface"></a>ISettings 인터페이스  

```  
__interface ISettings : IUnknown  
{  
    int NumDlls();  
    int NumPages();  

    HRESULT SetStage(LPCWSTR stageName);  
    HRESULT GetDllName(long index, __out LPBSTR pDllName);  
    HRESULT GetPageInfo(long index, __out ISettingsProperties **ppPageInfo);  
    HRESULT GetStyle(__out ISettingsProperties **ppStyleInfo);  
};  
```  

 이 인터페이스는 내부 전용입니다.  

#### <a name="isettingsproperties-interface"></a>ISettingsProperties 인터페이스  

```  
__interface ISettingsProperties : IUnknown  
{  
    HRESULT GetAttribute(LPCTSTR attributeName, __out LPBSTR attributeValue);  
    IStringProperties * Properties();  
   RESULT SelectNodes(LPCTSTR xPath, __out IXMLDOMNodeList **ppList);  
    HRESULT SelectSingleNode(LPCTSTR xPath, __out IXMLDOMNode **ppNode);  
    HRESULT GetDataNode(LPCTSTR name, __out ISettingsProperties **ppNode);  
    HRESULT GetDataNodes(__out IDataNodes **ppNodes);  
    HRESULT GetChildDataNodes(LPCTSTR childeName, __out IDataNodes **ppNodes);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 페이지 데이터에 대한 액세스를 제공합니다. 페이지 데이터의 최상위 수준으로 이동하려면 페이지의 **Settings()** 메서드를 사용하세요.  

##### <a name="hresult-getattributelpctstr-attributename--lpbstr-attributevalue"></a>HRESULT GetAttribute(LPCTSTR attributeName,  LPBSTR attributeValue)  
 이 메서드를 사용하면 주 노드의 특성 값을 검색할 수 있으며, 주 노드는 페이지의 **Settings()** 메서드를 사용할 때 나타나는 **페이지** 노드입니다.  

##### <a name="istringproperties--properties"></a>IStringProperties * Properties()  
 이 메서드는 주 노드 아래의 setter 속성 값에 대한 액세스를 제공합니다. 페이지의 경우 최상위 속성입니다.  

##### <a name="hresult-selectnodeslpctstr-xpath--ixmldomnodelist-pplist"></a>HRESULT SelectNodes(LPCTSTR xPath,  IXMLDOMNodeList **ppList)  
 XPath 식을 사용하여 직접 XML 노드 목록을 가져오려면 이 메서드를 호출하세요. 가능하다면 다른 메서드 중 하나를 사용하는 것이 좋습니다. 노드로 이동할 다른 방법이 없는 경우에만 이 메서드를 사용하세요.  

##### <a name="hresult-selectsinglenodelpctstr-xpath--ixmldomnode-ppnode"></a>HRESULT SelectSingleNode(LPCTSTR xPath,  IXMLDOMNode **ppNode)  
 XPath 식을 사용하여 직접 단일 XML 노드를 가져오려면 이 메서드를 호출하세요. 가능하다면 다른 메서드 중 하나를 사용하는 것이 좋습니다. 노드로 이동할 다른 방법이 없는 경우에만 이 메서드를 사용해야 합니다.  

##### <a name="hresult-getdatanodelpctstr-name--isettingsproperties-ppnode"></a>HRESULT GetDataNode(LPCTSTR name,  ISettingsProperties **ppNode)  
 해당 요소의 **Name** 특성을 기반으로 **Data** 요소를 검색합니다.  

##### <a name="hresult-getdatanodesidatanodes-ppnodes"></a>HRESULT GetDataNodes(IDataNodes **ppNodes)  
 이 메서드는 현재 노드 아래에서 **DataItem** 요소 목록을 검색합니다. 페이지 수준에서 **GetDataNode**를 호출하여 데이터에 대한 **ISettingsProperty** 인터페이스를 검색합니다. 그런 다음, 해당 인스턴스에서 **GetDataNodes**를 호출하여 레코드 목록을 검색합니다. 이 XML을 예로 들 수 있습니다.  

```  
    <Page …>  
      <Data Name="Network">  
        <DataItem>  
          <Setter Property="DisplayName">Public</Setter>  
          <Setter Property="Share">\\servername\Share</Setter>  
        </DataItem>  
        <DataItem>  
          <Setter Property="DisplayName">Dev Team</Setter>  
          <Setter Property="Share">\\servername\DevShare</Setter>  
        </DataItem>  
      </Data>  

PSettingsProperties pData;  
Settings()->GetDataNode(L"Network", &pData);  
PDataNodes pNodes;  
pData->GetDataNodes(&pNodes);  
```  

##### <a name="hresult-getchilddatanodeslpctstr-childename--idatanodes-ppnodes"></a>HRESULT GetChildDataNodes(LPCTSTR childeName,  IDataNodes **ppNodes)  
 이 메서드를 사용하면 특정 **데이터** 노드 아래의 **DataItem** 노드 집합으로 신속하게 이동할 수 있습니다. **GetDataNodes** 예제의 XML을 사용하면, 다음 코드는 **GetDataNodes** 아래에서 예제의 코드 네 줄과 정확히 같은 작업을 수행하지만 오류를 검사합니다.  

```  
ISimpleStringProperties Interface  
```  

#### <a name="isimplestringproperties-interface"></a>ISimpleStringProperties 인터페이스  

```  
__interface ISimpleStringProperties : IStringProperties  
{  
void Add(LPCTSTR propertyName, LPCTSTR value);  
};  
```  

 이 인터페이스는 그 자체로는 유용하지 않을 수도 있습니다. 하지만 **ID_SimpleStringProperties** 구성 요소를 통해 구현되며, **IStringProperties** 인터페이스도 구현합니다. 작업처럼 속성 집합을 다른 구성 요소로 전달해야 하지만, XML 값을 사용하는 대신 프로그래밍 방식으로 값을 추가하려는 경우 이 구성 요소를 사용할 수 있습니다. 다음은 이 인터페이스를 사용하는 방법에 대한 예제입니다.  

```  
PSimpleStringProperties *pProperties;  
CreateInstance(Container(), ID_SimpleStringProperties, &pProperties);  
pProperties->Add(L"filename", L"%windir%\\system32\\cscript.exe");  
pTask->Init(pProperties, nullptr);  
IStringProperties  
__interface IStringProperties : IUnknown  
{  
    HRESULT Get(LPCTSTR propertyName, [out] LPBSTR pPropValue);  
};  
```  

 이 인터페이스를 사용하면 XML에서 제공하는 setter 요소 집합에 간단하게 액세스할 수 있습니다. 이 인터페이스는 **Settings()->Properties()** 를 사용하여 페이지의 속성에 제공됩니다.  

##### <a name="hresult-getlpctstr-propertyname-out-lpbstr-ppropvalue"></a>HRESULT Get(LPCTSTR propertyName, [out] LPBSTR pPropValue)  
 이 메서드는 단일 속성 값을 검색합니다. 표 47 및 48을 참조하세요.  

### <a name="table-47-ihresult-get-property-value"></a>표 47. IHRESULT 속성 값 가져오기  

|**매개 변수**|**설명**|  
|-|-|  
|**propertyName**|읽을 속성의 이름|  
|**pPropValue**|종료 시 속성 값을 문자열로 포함(속성이 없으면 이 값은 **nullptr**이 됩니다.)|  

### <a name="table-48-ihresult-get-property-value-results"></a>표 48. IHRESULT 속성 값 가져오기 결과  

|||  
|-|-|  
|**HRESULT**|**설명**|  
|**S_OK**|속성 값이 검색됩니다.|  
|**E_INVALIDARG**|사용자가 입력한 이름의 속성이 없습니다.|  

#### <a name="itaskmanager-interface"></a>ITaskManager 인터페이스  

```  
__interface ITaskManager : IUnknown  
{  
    HRESULT Init(IWizardPageView *pPageView, int idListView, int idMessage, int idRetryButton, ISettingsProperties *pPageInfo, ITaskManagerCallback *pCallback);  
    HRESULT SetFailMessage(LPCWSTR message);  

    HRESULT Start(void);  

    HRESULT GetTaskMessage(size_t index, LPBSTR message);  
    HRESULT GetResultType)(size_t index, LPBSTR type);  
    HRESULT GetProperty(size_t index, LPCTSTR propertyName, LPBSTR value);  
    int GetSelectedIndex(void);  
    HRESULT Wait(DWORD waitMilliseconds);  
    size_t FailedCount(void);  
    size_t WarningCount(void);  
    size_t SucceedCount(void);  
    size_t RunningCount(void);  

    void OnCommonControlEvent(WORD controlId, LPNMHDR pInfo);  
    void OnControlEvent(WORD eventId, WORD controlId);  
    void EnableButtons(BOOL enable);  
}  
```  

 이 인터페이스는 실행 전 페이지에서 작업을 실행하는 구성 요소인 **TaskManager** 구성 요소(ITaskManager.h의 **ID_TaskManager**)를 통해 구현됩니다. 실행 전 페이지를 직접 사용할 수도 있고(대부분의 작업을 사용자가 수행), 사용자 고유의 페이지를 빌드할 수도 있습니다(대부분의 작업을 이 구성 요소가 수행).  

##### <a name="hresult-initiwizardpageview-ppageview-int-idlistview-int-idmessage-int-idretrybutton-isettingsproperties-ppageinfo-itaskmanagercallback-pcallback"></a>HRESULT Init(IWizardPageView \*pPageView, int idListView, int idMessage, int idRetryButton, ISettingsProperties \*pPageInfo, ITaskManagerCallback \*pCallback)  
 다른 메서드를 호출하기 전에 이 메서드를 호출해야 합니다. 이 메서드는 **TaskManager** 구성 요소를 초기화합니다. 표 49를 참조하세요.  

### <a name="table-49-hresult-init"></a>표 49. HRESULT Init  

|**매개 변수**|**설명**|  
|-|-|  
|**pPageView**|작업을 실행할 페이지에 대한 액세스를 제공합니다(이 페이지에 특정 컨트롤 집합이 있어야 하며, 자세한 내용은 이후에 나오는 몇 가지 매개 변수에서 설명하겠습니다.)|  
|**idListView**|작업 목록과 이러한 작업의 상태를 표시하는 **ListView** 컨트롤의 컨트롤 ID|  
|**idMessage**|사용자가 선택하는 작업에 대한 메시지를 표시하는 데 사용되는 텍스트 상자의 컨트롤 ID|  
|**idRetryButton**|클릭하여 작업을 다시 실행할 수 있는 단추의 컨트롤 ID|  
|**pPageInfo**|페이지의 XML과 관련된 래퍼(**TaskManager**는 이 XML에서 실행할 작업 집합을 로드합니다.)|  
|**pCallback**|Null일 수 있습니다(이 매개 변수가 null이면 **TaskManager**는 작업을 시작할 때 **Started**를 호출하고 실행을 마치는 각 작업에 대해 **Finished** 메서드를 호출합니다.)|  

##### <a name="hresult-setfailmessagelpcwstr-message"></a>HRESULT SetFailMessage(LPCWSTR message)  
 이 메서드는 하나 이상의 작업이 실패할 때 표시되는 메시지를 설정합니다.  

##### <a name="hresult-startvoid"></a>HRESULT Start(void)  
 이 메서드는 모든 작업을 시작합니다. 각 작업은 별도의 스레드에서 시작됩니다.  

##### <a name="hresult-gettaskmessagesizet-index-lpbstr-message"></a>HRESULT GetTaskMessage(size_t index, LPBSTR message)  
 이 메서드는 내부 전용입니다. 작업 목록의 인덱스를 기준으로 작업에 대한 현재 메시지를 검색합니다.  

##### <a name="hresult-getresulttypesizet-index-lpbstr-type"></a>HRESULT GetResultType)(size_t index, LPBSTR type)  
 이 메서드는 작업의 현재 "형식"을 검색합니다. 표 50은 사용 가능한 형식을 보여줍니다.  

### <a name="table-50-hresult-getresulttype"></a>표 50. HRESULT GetResultType  

|**유형**|**설명**|  
|-|-|  
|**0**|성공한 작업을 나타냅니다.|  
|**1**|경고를 반환한 작업을 나타냅니다.|  
|**-1**|실패한 작업을 나타냅니다.|  

 작업의 종료 또는 오류 코드를 살펴보고 작업의 <ExitCodes\> XML 요소에서 일치 항목을 찾는 방법으로 형식을 검색합니다.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propertyname-lpbstr-value"></a>HRESULT GetProperty(size_t index, LPCTSTR propertyName, LPBSTR value)  
 이 메서드는 강조 표시되는 작업에 대한 메시지 옆에 이미지를 표시할 수 있도록 진행률 및 실행 전 페이지에서 **BitmapFilename** setter 속성을 검색하는 데 사용됩니다. 즉, 작업의 XML에 사용자 지정 setter를 추가한 후 이 메서드로 검색할 수 있습니다.  

##### <a name="int-getselectedindexvoid"></a>int GetSelectedIndex(void)  
 이 메서드는 현재 선택된 작업의 인덱스를 검색합니다. 선택한 작업에 표시할 작업에 대한 추가 정보를 검색(**GetProperty** 메서드 참조)하려는 경우에 유용합니다. 진행률 및 실행 전 페이지에서는 선택한 작업에 대한 이미지를 표시하기 위해 이 메서드를 사용합니다.  

##### <a name="hresult-waitdword-waitmilliseconds"></a>HRESULT Wait(DWORD waitMilliseconds)  
 이 메서드는 테스트에서 작업이 단위 테스트보다 먼저 완료될 수 있도록 주로 단위 테스트에 도움을 줍니다. 사용자가 이 메서드를 호출할 일은 좀처럼 없습니다. 이 메서드는 모든 작업이 실행을 완료하는 시간 또는 경과된 대기 시간을 반환합니다.  

##### <a name="sizet-failedcountvoid"></a>size_t FailedCount(void)  
 이 메서드는 현재 실패로 표시된 작업 수를 반환합니다.  

##### <a name="sizet-warningcountvoid"></a>size_t WarningCount(void)  
 이 메서드는 현재 경고로 표시된 작업 수를 반환합니다.  

##### <a name="sizet-succeedcountvoid"></a>size_t SucceedCount(void)  
 이 메서드는 현재 성공으로 표시된 작업 수를 반환합니다.  

##### <a name="sizet-runningcountvoid"></a>size_t RunningCount(void)  
 이 메서드는 현재 실행 중으로 표시된 작업 수를 반환합니다.  

##### <a name="void-oncommoncontroleventword-controlid-lpnmhdr-pinfo"></a>void OnCommonControlEvent(WORD controlId, LPNMHDR pInfo)  
 **TaskManager**가 필요한 이벤트를 처리할 수 있도록 페이지의 **OnCommonControlEvent**에서 이 메서드를 호출하세요.  

##### <a name="void-oncontroleventword-eventid-word-controlid"></a>void OnControlEvent(WORD eventId, WORD controlId)  
 **TaskManager**가 필요한 이벤트를 처리할 수 있도록 페이지의 **OnControlEvent**에서 이 메서드를 호출하세요.  

##### <a name="void-enablebuttonsbool-enable"></a>void EnableButtons(BOOL enable)  
 이 메서드는 내부 전용입니다.  

#### <a name="iwizardcomponent-interface"></a>IWizardComponent 인터페이스  

```  
__interface IWizardComponent : IUnknown  
{  
    HRESULT SetContainer(IWizardPageContainer *pContainer);  
};  
```  

##### <a name="overview"></a>개요  
 일반적으로 사용자가 이 인터페이스를 직접 구현하지는 않고 **WizardComponent** 템플릿 클래스를 통해 구현합니다. 구성 요소가 이 인터페이스를 구현하고 사용자가 클래스 팩터리를 레지스트리에 등록한 경우 **IWizardPageContainer** 인스턴스가 만들어지면 구성 요소는 이 인스턴스에 대한 포인터를 수신합니다. 이렇게 하면 구성 요소에 필요할 수 있는 다른 구성 요소를 만들기 위한 로거 또는 레지스트리에 액세스할 수 있습니다.  

#### <a name="iwizarddialogcontroller-interface"></a>IWizardDialogController 인터페이스  

```  
__interface IWizardDialogController : IUnknown  
{  
    void Initialize(ISettings *pSettings);  
    void InitPages(void);  
    void Start();  
    void Next();  
    void Finish();  
    void Previous();  
    int NumPages();  
    void Cancel();  

    HRESULT Focus(WizardButtons button);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage();  

    void ChangePage(size_t newIndex);  
    IUnknown *CurrentPage(void);  
    HRESULT GetCurrentTitle([out, retval] LPBSTR pDisplayName);  
};  
```  

 이 인터페이스는 내부 전용입니다.  

#### <a name="iwizarddialogview-interface"></a>IWizardDialogView 인터페이스  

```  
__interface IWizardDialogView : IUnknown  
{  
    HRESULT LoadBannerImage(LPCTSTR bannerFilename);  
    HRESULT LoadPage(LPCTSTR pageType, ISettingsProperties *pPageSettings, IWizardPageView **view);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    HRESULT Focus(WizardButtons button);  
    void EnableFinish(BOOL isFinish);  
    void Exit(int exitCode);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage(void);  
    void SetTitle(LPCTSTR title);  
    void SetPageTitle(LPCTSTR title);  
    int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType);  
    HWND GetHwnd(void);  
    void UpdateFocus(void);  
};  
```  

 이 인터페이스는 내부 전용입니다.  

####  <a name="IWizardPageInterface"></a> IWizardPage 인터페이스  

```  
__interface IWizardPage : IUnknown  
{  
    HRESULT SetPageSettings(ISettingsProperties *pPageSettings);  
    HINSTANCE GetInstanceHandle(void);  
    int GetDialogResourceId(void);  
    void WindowCreated(IWizardPageView *pView, IWizardPageContainer *pContainer);  
    void WindowShown(void);  
    void WindowHidden(void);  

    HRESULT NextClicked(void);  
    void ControlEvent(WORD eventId, WORD controlId);  
    void CommonControlEvent(WORD controlId, LPNMHDR pInfo, LPBOOL pCancel);  
    void UnhandledEvent(HWND hwnd, UINT message, WPARAM wParam, LPARAM lParam);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **WizardPageImpl**을 통해 구현되므로 일반적으로 사용자가 직접 구현하지 않습니다. 마법사는 사용자 지정 페이지와 상호 작용할 때 이러한 메서드를 모두 호출합니다.  

#### <a name="iwizardpagecontainer-interface"></a>IWizardPageContainer 인터페이스  

```  
__interface IWizardPageContainer : IUnknown  
{  
    ILogger * Logger(void);  
    IPropertyBag * Properties(void);  
    HRESULT CreateInstance(LPCTSTR type, [out] IUnknown **ppInstance);  
    HRESULT GetService(REFIID iid, [out] IUnknown **ppInstance);  
    HRESULT ReplaceVariables(LPCTSTR source, [out] LPBSTR pDest);  
    HRESULT GotoPage(LPCTSTR pageName);  
    int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType);  
    BOOL InPreview(void);  
    HWND GetHwnd(void);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 **Container** 메서드(**WizardPageImpl**을 통해 구현됨)를 통해 페이지에 제공되며 마법사의 다양한 서비스에 대한 액세스를 제공합니다.  

##### <a name="ilogger--loggervoid"></a>ILogger * Logger(void)  
 다음과 같이 로그 파일에 메시지를 쓸 때 이 메서드를 사용합니다.  

```  
Logger()->Verbose(s_component, L"Message for log file");  
```  

##### <a name="ipropertybag--propertiesvoid"></a>IPropertyBag * Properties(void)  
 이 메서드는 UDI 마법사가 실행 중인 동안 메모리에만 있는 속성인 "메모리" 변수에 대한 액세스를 제공합니다. 이러한 속성은 **$memoryVarName$** 구문을 사용하여 코드로 또는 XML로 다른 페이지에 제공됩니다.  

##### <a name="hresult-createinstancelpctstr-type-out-iunknown-ppinstance"></a>HRESULT CreateInstance(LPCTSTR type, [out] IUnknown **ppInstance)  
 이 메서드를 사용하면 등록된 구성 요소의 새 인스턴스를 만들 수 있습니다. 그러나 강력한 형식인 **CreateInstance** 템플릿 함수를 사용하는 것이 좋습니다.  

##### <a name="hresult-getservicerefiid-iid-out-iunknown-ppinstance"></a>HRESULT GetService(REFIID iid, [out] IUnknown **ppInstance)  
 이 메서드를 사용하면 등록된 서비스를 검색할 수 있습니다. 그러나 **IUnknown**을 사용하는 대신 강력한 형식인 **GetService** 템플릿 함수를 호출하는 것이 좋습니다.  

##### <a name="hresult-replacevariableslpctstr-source-out-lpbstr-pdest"></a>HRESULT ReplaceVariables(LPCTSTR source, [out] LPBSTR pDest)  
 이 메서드는 문자열 값 내의 변수 작업을 처리합니다. 표 51 및 52에 표시된 형식을 지원합니다.  

### <a name="table-51-hresult-replacevariables"></a>표 51. HRESULT ReplaceVariables  

|**형식**|**설명**|  
|-|-|  
|**$Name$**|이 이름을 가진 메모리 변수 값을 대체합니다. 이 이름을 가진 메모리 변수가 없는 경우 "토큰"이 제거됩니다.|  
|**%Name%**|작업 순서 변수이거나 환경 변수입니다. 순서는 다음과 같습니다.<br /><br /> 1.  작업 순서 변수 값을 사용합니다(있는 경우).<br />2.  환경 변수 값을 사용합니다(있는 경우).<br />3.  그렇지 않은 경우 문자열에서 이 텍스트를 제거합니다.|  

### <a name="table-52-hresult-parameter"></a>표 52. HRESULT 매개 변수  

|**매개 변수**|**설명**|  
|-|-|  
|**원본**|입력 문자열로, **$** 및 **%** 변수 조합을 포함할 수도 있고 아무 것도 포함하지 않을 수도 있습니다.|  
|**pDest**|반환 시 표 51에 따라 모든 토큰이 대체된 새 문자열|  

##### <a name="hresult-gotopagelpctstr-pagename"></a>HRESULT GotoPage(LPCTSTR pageName)  
 이 메서드는 완벽하게 테스트되지 않았습니다. .config XML 파일에 정의된 페이지 이름에 따라 특정 페이지로 직접 전환할 수 있다는 것이 핵심입니다. 이 메서드를 호출하면 페이지에서 **OnNextClicked**가 무시됩니다. 또한 이 메서드의 동작이 변경될 수 있으므로 사용자는 이 메서드를 사용할 때 위험을 감수해야 합니다.  

##### <a name="int-showmessageboxlpctstr-message-lpctstr-lpcaption-uint-utype"></a>int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType)  
 이 메서드는 사용자가 입력하는 텍스트 및 캡션이 포함된 메시지 상자를 표시합니다. **uType** 매개 변수는 사용자가 **MessageBox** Win32 함수에 전달할 수 있는 모든 값입니다.  

##### <a name="bool-inpreviewvoid"></a>BOOL InPreview(void)  
 사용자가 **/preview** 스위치를 제공하여 마법사를 "미리 보기" 모드로 실행하면 이 메서드가 TRUE를 반환합니다. 미리 보기 모드에서는 **다음** 단추가 절대로 비활성화되지 않습니다. 이 메서드를 사용하면 미리 보기 모드에서 코드를 무시할 수 있습니다. 예를 들어 페이지에 유효한 데이터가 없는 경우 문제를 일으킬 가능성이 있는 코드를 무시할 수 있습니다.  

##### <a name="hwnd-gethwndvoid"></a>HWND GetHwnd(void)  
 이 메서드는 주 대화 상자에 대한 **HWND**를 반환합니다. 이 메서드는 주의해서 사용해야 합니다. 일반적으로 UDI 마법사 응용 프로그래밍 인터페이스는 사용자가 절대로 창 핸들을 직접 작업하지 않도록 설계됩니다.  

#### <a name="iwizardpageview-interface"></a>IWizardPageView 인터페이스  

```  
__interface IWizardPageView : IUnknown  
{  
    HRESULT GetControlWrapper(int itemId, DialogControlTypes controlType, IUnknown **ppControl);  
    HWND GetHwnd(void);  
    HWND GetControl(int itemId);  
    HRESULT Show (void);  
    HRESULT Hide(void);  
    HRESULT Focus(int itemId);  
    IWizardPage * Page(void);  
    IFormController * Form(void);  

    HRESULT FocusWizardButton(WizardButtons button);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage(void);  
};  
```  

 이 인터페이스는 **View** 메서드(**WizardPageImpl**을 통해 구현됨)를 통해 페이지의 코드에 제공됩니다.  

##### <a name="hresult-getcontrolwrapperint-itemid-dialogcontroltypes-controltype-iunknown-ppcontrol"></a>HRESULT GetControlWrapper(int itemId, DialogControlTypes controlType, IUnknown \*ppControl)  
 UDI 마법사는 페이지의 컨트롤과 상호 작용하기 위한 외관인 *래퍼*를 사용합니다. 실제 컨트롤 대신 이러한 외관을 사용하면 테스트의 모의 외관을 제공할 수 있으므로 페이지에 대한 테스트를 훨씬 쉽게 작성할 수 있습니다.  

 이 메서드를 직접 사용하는 대신, 다음 예제와 같이 강력한 형식인 **GetControlWrapper** 템플릿 메서드를 사용하는 것이 좋습니다.  

```  
PComboBox m_pLanguagePackCombo;  
GetControlWrapper(View(), IDC_MY_COMBO, CONTROL_COMBO_BOX, &m_pCombo);  
```  

##### <a name="hwnd-gethwndvoid"></a>HWND GetHwnd(void)  
 이 메서드는 페이지의 창 핸들을 반환합니다. 일반적으로 이 창 핸들에 액세스할 일은 없습니다.  

##### <a name="hwnd-getcontrolint-itemid"></a>HWND GetControl(int itemId)  
 필요한 경우 이 메서드를 호출하여 페이지의 컨트롤에 대한 창 핸들을 가져올 수 있습니다. (**GetControlWrapper** 템플릿 함수를 호출하는 것이 더 좋습니다).  

##### <a name="hresult-show-void"></a>HRESULT Show (void)  
 이 메서드는 내부 전용입니다.  

##### <a name="hresult-hidevoid"></a>HRESULT Hide(void)  
 이 메서드는 내부 전용입니다.  

##### <a name="hresult-focusint-itemid"></a>HRESULT Focus(int itemId)  
 특정 컨트롤에 입력 포커스를 설정합니다.  

##### <a name="iwizardpage--pagevoid"></a>IWizardPage * Page(void)  
 이 메서드는 내부 전용입니다.  

##### <a name="iformcontroller--formvoid"></a>IFormController * Form(void)  
 이 메서드는 내부 전용입니다.  

##### <a name="hresult-focuswizardbuttonwizardbuttons-button"></a>HRESULT FocusWizardButton(WizardButtons button)  
 마법사의 단추 중 하나로 포커스를 설정합니다. **WizardButtons**의 값은 **BackButton** 및 **NextButton** 두 가지입니다.  

##### <a name="hresult-setenablewizardbuttons-button-bool-enable"></a>HRESULT SetEnable(WizardButtons button, BOOL enable)  
 마법사 단추 중 하나를 사용하도록 또는 사용하지 않도록 설정해 달라고 요청합니다. 단추가 사용자가 요청하는 상태와 일치하지 않을 수 있습니다. 예를 들어 **/preview** 스위치로 UDI 마법사를 실행하면 항상 단추가 사용됩니다. **WizardButtons**의 값은 **BackButton** 및 **NextButton** 두 가지입니다.  

##### <a name="void-showwarningmessagelpctstr-message"></a>void ShowWarningMessage(LPCTSTR message)  
 이 메서드는 페이지 콘텐츠 영역 아래쪽에 경고 메시지를 표시합니다. 사용자가 원하는 모든 텍스트를 이 메시지로 사용할 수 있습니다.  

##### <a name="void-hidewarningmessagevoid"></a>void HideWarningMessage(void)  
 **ShowWarningMessage**를 호출하여 표시한 경고 메시지를 숨깁니다.  

#### <a name="ixmldocument-interface"></a>IXmlDocument 인터페이스  

```  
__interface IXmlDocument : IUnknown  
    HRESULT Load(LPCTSTR filename);  
    HRESULT LoadXml(LPCTSTR xml);  
    HRESULT Save(LPCWSTR filename);  
    HRESULT GetParseErrorMessage(LPBSTR pMessage);  
    HRESULT SelectNodes(LPCTSTR xpath, IXMLDOMNodeList **ppNodes);  
    HRESULT SelectSingleNode(LPCTSTR xpath, IXMLDOMNode **ppNode);  
    HRESULT AddSchema(LPCTSTR filename, LPCTSTR ns);  
    HRESULT AddAttribute(IXMLDOMNode *pNode, LPCWSTR name, LPCWSTR value);  
    HRESULT CreateNode(DOMNodeType type, LPCWSTR name, LPCWSTR ns, IXMLDOMNode **ppNode);  
};  
```  

##### <a name="overview"></a>개요  
 이 인터페이스는 C++에서 XML 문서를 보다 쉽게 작업하기 위해 설계된 외관인 **ID_IXmlDocument** 구성 요소를 통해 구현됩니다.  

##### <a name="hresult-loadlpctstr-filename"></a>HRESULT Load(LPCTSTR filename)  
 이 메서드는 외부 파일에서 XML 문서를 로드합니다. 파일이 오류 없이 로드되면 **S_OK**를 반환하고 오류가 발생하면 **S_FALSE**를 반환합니다. 오류가 있으면 **GetParseErrorMessage**를 호출하여 오류 메시지를 가져올 수 있습니다.  

##### <a name="hresult-loadxmllpctstr-xml"></a>HRESULT LoadXml(LPCTSTR xml)  
 이 메서드는 외부 파일 대신 문자열에서 XML 문서를 로드합니다. XML을 읽기 위한 소스를 제외하고, **Load** 메서드와 동작이 똑같습니다.  

##### <a name="hresult-savelpcwstr-filename"></a>HRESULT Save(LPCWSTR filename)  
 이 메서드는 메모리에 있는 XML 문서를 외부 파일에 저장합니다.  

##### <a name="hresult-getparseerrormessagelpbstr-pmessage"></a>HRESULT GetParseErrorMessage(LPBSTR pMessage)  
 이 메서드는 XML 문서에서 로드한 오류 메시지와 함께 새 문자열을 반환합니다. 항상 **S_OK**를 반환합니다.  

##### <a name="hresult-selectnodeslpctstr-xpath-ixmldomnodelist-ppnodes"></a>HRESULT SelectNodes(LPCTSTR xpath, IXMLDOMNodeList \**ppNodes)  
 이 메서드를 사용하면 XPath 식을 사용하여 문서에서 노드 컬렉션을 검색할 수 있습니다. 항상 **S_OK**를 반환합니다.  

##### <a name="hresult-selectsinglenodelpctstr-xpath-ixmldomnode-ppnode"></a>HRESULT SelectSingleNode(LPCTSTR xpath, IXMLDOMNode \**ppNode)  
 이 메서드를 사용하면 XPath 식을 사용하여 문서에서 한 노드를 검색할 수 있습니다. 항상 **S_OK**를 반환합니다.  

##### <a name="hresult-addschemalpctstr-filename-lpctstr-ns"></a>HRESULT AddSchema(LPCTSTR filename, LPCTSTR ns)  
 이 메서드는 XML 문서의 스키마가 로드되면 유효성을 검사하는 데 사용되는 외부 스키마 파일의 이름을 추가합니다. 사용자가 제공하는 네임스페이스는 XPath 쿼리에 사용할 수 있는 문자열이지만, 여기서는 테스트하지 않겠습니다.  

##### <a name="hresult-addattributeixmldomnode-pnode-lpcwstr-name-lpcwstr-value"></a>HRESULT AddAttribute(IXMLDOMNode \*pNode, LPCWSTR name, LPCWSTR value)  
 이 메서드는 XML 문서의 기존 노드에 새 특성을 추가합니다. 표 53을 참조하세요.  

### <a name="table-53-hresult-addattribute"></a>표 53. HRESULT AddAttribute  

|**매개 변수**|**설명**|  
|-|-|  
|**pNode**|특성을 추가할 노드|  
|**Name**|새 특성의 이름|  
|**값**|새 특성의 값|  

##### <a name="hresult-createnodedomnodetype-type-lpcwstr-name-lpcwstr-ns-ixmldomnode-ppnode"></a>HRESULT CreateNode(DOMNodeType type, LPCWSTR name, LPCWSTR ns, IXMLDOMNode \**ppNode)  
 새 노드를 만들려면 이 메서드를 호출합니다.  

```  
Pointer<IXMLDOMNode> pNewChild  
pXmlDom->CreateNode(NODE_ELEMENT, L"MyElement", L"", &pNewChild);  
```  

 새 노드를 만든 후 부모의 **appendChild** 메서드를 호출하여 다른 노드에 자식으로 추가할 수 있습니다.  

### <a name="helper-functions"></a>도우미 함수  

#### <a name="createinstance-template-function"></a>CreateInstance 템플릿 함수  

```  
HRESULT CreateInstance(IWizardPageContainer *pContainer, LPCTSTR type, I **ppObject)  
```  

 이 함수는 IWizardPageContainer.h에 정의되며 다음 예제와 같이 **IWizardPageContainer->CreateInstance** 메서드에 대한 형식이 안전한 래퍼를 제공합니다.  

```  
CreateInstance<IDirectory>(Container(), ID_Directory, &pDirectory);  
```  

 이 코드는 해당 구성 요소의 **IDirectory** 인터페이스를 검색하는 새 **ID_Directory**를 만듭니다.  

#### <a name="getservice-template-function"></a>GetService 템플릿 함수  

```  
void GetService(IWizardPageContainer *pContainer, I **ppService)  
```  

 이 함수는 IWizardPageContainer.h에 정의되며 다음 예제와 같이 **IWizardPageContainer->GetService** 메서드에 대한 형식이 안전한 래퍼를 제공합니다.  

```  
GetService<ITSVariableBag>(Container(), &pTsBag);  
```  

 이 함수는 **ITSVariableBag** 인터페이스를 지원하는 작업 순서 구성 요소를 검색합니다. (**ITSVariableBag**의 경우 **WizardPageImpl** 클래스의 TSVariables 메서드를 대신 사용할 수 있습니다.)  

### <a name="udi-wizard-designer-configuration-file-schema-reference"></a>UDI 마법사 디자이너 구성 파일 스키마 참조  
 이 파일은 UDI 마법사 디자이너에서 사용합니다. 각 사용자 지정 .dll 파일에 대한 별도의 파일이 만들어지며, 이러한 파일은 사용자 지정 마법사 페이지 편집기, 사용자 지정 작업 또는 사용자 지정 유효성 검사기를 포함할 수 있습니다. 파일은 *.config*로 끝나야 하고 *installation_folder*\Bin\Config 폴더에 있어야 합니다(여기서 *installation_folder*는 MDT를 설치한 폴더).  

  표 54에는 UDI 마법사 디자이너 구성 파일의 요소 및 해당 설명이 나와 있습니다. **DesignerConfig** 요소는 이 참조의 루트 노드입니다.  

### <a name="table-54-elements-in-the-udi-wizard-designer-configuration-file-and-their-descriptions"></a>표 54. UDI 마법사 디자이너 구성 파일의 요소 및 해당 설명  

|**요소 이름**|**설명**|  
|-|-|  
|[DesignerConfig](#DesignerConfig)|다른 모든 요소의 루트를 지정합니다.|  
|[DesignerMappings](#DesignerMappings)|[Page](#Page)요소 집합을 그룹화합니다.|  
|[Page](#Page)|UDI 마법사 디자이너에서 로드할 마법사 페이지 편집기를 지정하며, 이 편집기는 마법사 페이지의 구성 설정을 편집하는 데 사용됩니다.|  
|[Param](#Param)|부모 [Task](#Task) 또는 [Validator](#Validator) 요소에 전달되는 매개 변수를 지정하며 UDI 마법사 구성 파일의 [Setter]() 요소에 해당합니다. **참고:** 부모가 [Task](#Task) 또는 [Validator](#Validator) 요소인 경우 이 요소의 특성이 다릅니다.|  
|[Task](#Task)|작업 라이브러리 내의 작업을 지정|  
|[TaskItem](#TaskItem)|작업에 전달되는 매개 변수 그룹을 지정|  
|[TaskLibrary](#TaskLibrary)|[Task](#Task)요소 집합을 그룹화|  
|[Validator](#Validator)|유효성 검사기 라이브러리 내의 유효성 검사기를 지정|  
|[ValidatorLibrary](#ValidatorLibrary)|[Validator](#Validator) 요소 집합을 그룹화|  

####  <a name="DesignerConfig"></a> DesignerConfig  
 이 요소는 다른 모든 요소의 루트를 지정합니다.  

##### <a name="element-information"></a>요소 정보  
  표 55는 [DesignerConfig](#DesignerConfig) 요소에 대한 정보를 제공합니다.  

### <a name="table-55-designerconfig-element-information"></a>표 55. DesignerConfig 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|1: 이 요소는 필수입니다.|  
|부모 요소|없음|  
|목차|**DesignerMappings**, **TaskLibrary**, **ValidatorLibrary**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<DesignerConfig>  
   + <TaskLibrary>  
   + <ValidatorLibrary>  
   + <DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="DesignerMappings"></a> DesignerMappings  
 이 요소는 [Page](#Page) 요소 집합을 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
  표 56은 [DesignerMappings](#DesignerMappings) 요소에 대한 정보를 제공합니다.  

### <a name="table-56-designermappings-element-information"></a>표 56. DesignerMappings 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[DesignerConfig](#DesignerConfig) 요소 내에서 0회 또는 1회(DLL에 이 UDI 마법사 디자이너 구성 파일에 해당하는 사용자 지정 마법사 페이지가 없는 경우 이 요소는 선택 사항입니다.)|  
|부모 요소|**DesignerConfig**|  
|목차|**Page**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<DesignerConfig>  
   + <TaskLibrary>  
   + <ValidatorLibrary>  
   - <DesignerMappings>  
        <Page DLL="SharedPages.dll"  
           Description="Used to display text that describes the current stagegroup"  
           Type="Microsoft.SharedPages.WelcomePage"  
           DisplayName="Welcome"   
           Image="Welcome_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.WelcomePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
        <Page DLL="OSDRefreshWizard.dll"  
           Description="Captures or restores user state data"  
           Type="Microsoft.OSDRefresh.UserStatePage"  
           DisplayName="User Data"  
           Image="UserState_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.UserStatePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
        <Page DLL="OSDRefreshWizard.dll"  
           Description="Allows selecting the image to install, target drive, and whether to format"  
           Type="Microsoft.OSDRefresh.VolumePage"  
           DisplayName="Volume"  
           Image="Volume_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.VolumePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
     </DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="Page"></a> Page  
 이 요소는 UDI 마법사 디자이너에서 로드할 마법사 페이지 편집기를 지정하며, 이 편집기는 마법사 페이지의 구성 설정을 편집하는 데 사용됩니다.  

##### <a name="element-information"></a>요소 정보  
표 57은 [Page](#Page) 요소에 대한 정보를 제공합니다.  

### <a name="table-57-page-element-information"></a>표 57. Page 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[DesignerMappings](#DesignerMappings) 요소에 정의된 각 마법사 페이지에 대해 1회 이상|  
|부모 요소|**DesignerMappings**|  
|목차|잘 구성된(Well-Formed) XML 모든 콘텐츠|  

##### <a name="element-attributes"></a>요소 특성  
표 58에는 [Page](#Page) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-58-attributes-and-corresponding-values-for-the-page-element"></a>표 58. Page 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**설명**|매개 변수에 대한 정보를 제공하는 텍스트를 지정하며, 이 텍스트는 UDI 마법사 디자이너에 표시됩니다.|  
|**DesignerAssembly**|마법사 페이지 편집기와 연결된 .dll 파일의 이름을 지정합니다(.dll 파일은 *installation_folder*\Bin 폴더에 있어야 하며, 여기서 *installation_folder*는 MDT를 설치한 폴더).|  
|**DesignerType**|**DesignerAssembly** 특성에 지정된 .dll 파일 내부의 마법사 페이지 편집기 이름을 지정합니다(마법사 페이지 편집기에 사용되는 Microsoft .NET 형식이며, 정규화된 Microsoft.NET 네임스페이스 포함).|  
|**DisplayName**|UDI 마법사 디자이너에 표시되는 페이지 편집기의 표시 이름을 지정합니다.|  
|**DLL**|마법사 페이지와 연결된 .dll 파일의 이름을 지정합니다(.dll 파일은 *installation_folder*\Templates\Distribution\Tools\\*platform* 폴더에 있어야 하며, 여기서 *installation_folder*는 MDT를 설치한 폴더이고 *플랫폼*은 32비트 버전인 경우 **x86**, 64비트 버전인 경우 **x64**). **참고:** DLL 프로세서 아키텍처가 설치된 MDT 프로세서 아키텍처와 일치하는지 확인합니다. 예를 들어 32비트 버전의 MDT를 설치한 경우 마법사 페이지에 32비트 DLL을 사용해야 합니다.|  
|**Image**|PNG(이동식 네트워크 그래픽) 형식의 페이지 이미지 이름을 지정합니다(.png 파일은 *installation_folder*\Bin\Images 폴더에 있어야 하며, 여기서 *installation_folder*는 MDT를 설치한 폴더).|  
|**유형**|마법사 페이지 편집기를 지정하며, 사용자 지정 페이지를 등록할 때 사용된 이름과 일치해야 합니다.|  

##### <a name="remarks"></a>주의  
 UDI 마법사 디자이너는 템플릿 같은 [Page](#Page) 요소를 사용하여 새 마법사의 초기 XML을 만듭니다. UDI 마법사 디자이너는 [Page](#Page) 및 자식 요소의 형식이 유효한지 확인하기 위해 스키마 유효성 검사를 수행합니다. 이 요소는 사용자 지정 페이지 편집기를 사용하여 UDI 마법사 페이지 형식과 UDI 마법사 디자이너가 편집해야 하는 정보 간의 매핑을 제공하고 이 형식의 페이지를 만듭니다.  

##### <a name="example"></a>예  
 없음  

####  <a name="Param"></a> Param  
 이 요소는 부모 [Task](#Task) 또는 [Validator](#Validator) 요소에 전달되는 매개 변수를 지정하며 UDI 마법사 구성 파일의 [Setter]() 요소에 해당합니다.  

> [!NOTE]
>  부모가 [Task](#Task) 또는 [Validator](#Validator) 요소인 경우 이 요소의 특성이 다릅니다.  

##### <a name="element-information"></a>요소 정보  
 표 59는 [Param](#Param) 요소에 대한 정보를 제공합니다.  

### <a name="table-59-param-element-information"></a>표 59. Param 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[TaskItem](#TaskItem) 또는 [Validator](#Validator) 부모 요소마다 1회 이상|  
|부모 요소|**TaskItem**, **Validator**|  
|목차|잘 구성된(Well-Formed) XML 모든 콘텐츠|  

##### <a name="element-attributes"></a>요소 특성  
  표 60에는 [Param](#Param) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-60-attributes-and-corresponding-values-for-the-param-element"></a>표 60. Param 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**설명**|매개 변수에 대한 정보를 제공하는 텍스트를 지정하며, 이 텍스트는 UDI 마법사 디자이너에 표시됩니다. **참고:** 이 특성은 [Validator](#Validator) 요소에만 유효합니다.|  
|**DisplayName**|UDI 마법사 디자이너의 해당 UDI 마법사 페이지에 대해 표시되는 유효성 검사기 매개 변수의 표시 이름을 지정합니다(이 이름은 일반적으로 **Name** 특성보다 구체적). **참고:** 이 특성은 [Validator](#Validator) 요소에 대해서만 유효합니다.|  
|**Name**|부모 요소에 따라 작업 또는 유효성 검사기에 전달되는 매개 변수 이름을 지정 합니다(이 특성은 UDI 마법사 요소 구성 파일의 [Setter]() 요소에서 **Property** 특성이 됨). **참고:** 이 매개 변수는 [TaskItem](#TaskItem) 및 [Validator](#Validator) 부모 요소에 모두 사용됩니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Task"></a> Task  
 이 요소는 작업 라이브러리 내의 작업을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
 표 61은 [Task](#Task) 요소에 대한 정보를 제공합니다.  

### <a name="table-61-task-element-information"></a>표 61. Task 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[TaskLibrary](#TaskLibrary) 요소 내에서 1회 이상(**TaskLibrary** 요소가 지정된 경우 이 요소는 선택 사항이 아닙니다.)|  
|부모 요소|**TaskLibrary**|  
|목차|**TaskItem**|  

##### <a name="element-attributes"></a>요소 특성  
  표 62에는 [Task](#Task) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-62-attributes-and-corresponding-values-for-the-task-element"></a>표 62. Task 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**설명**|작업에 대한 정보를 제공하는 텍스트를 지정하며, 이 텍스트는 UDI 마법사 디자이너에 표시됩니다.|  
|**DLL**|작업과 연결된 .dll 파일의 이름을 지정합니다(.dll 파일은 *installation_folder*\Templates\Distribution\Tools\\*platform* 폴더에 있어야 하며, 여기서 *installation_folder*는 MDT를 설치한 폴더이고 *플랫폼*은 32비트 버전인 경우 **x86**, 64비트 버전인 경우 **x64**).|  
|**Name**|해당 UDI 마법사 페이지 및 UDI 마법사 디자이너에 표시되는 작업의 이름을 지정합니다.|  
|**유형**|팩터리 레지스트리에 등록되고 .dll 파일 내에서 특정 작업을 호출하는 데 사용되는 작업 형식을 지정합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="TaskItem"></a> TaskItem  
 이 요소는 작업에 전달되는 매개 변수 그룹을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
  표 63은 [TaskItem](#TaskItem) 요소에 대한 정보를 제공합니다.  

### <a name="table-63-taskitem-element-information"></a>표 63. TaskItem 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 **TaskItem** 요소에 대해 1회 이상|  
|부모 요소|**Task**|  
|목차|**Param**|  

##### <a name="element-attributes"></a>요소 특성  
 표 64에는 [TaskItem](#TaskItem) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-64-attribute-and-corresponding-values-for-the-taskitem-element"></a>표 64. TaskItem 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**유형**|UDI 마법사 구성 파일에 만들 요소 형식을 지정합니다. 이 특성의 값에 해당하는 XML 요소가 만들어집니다. 예를 들어 이 특성의 값이 [File](#File)이면 UDI 마법사 구성 파일에 **File** 요소가 만들어집니다.<br /><br /> 현재 유일하게 지원되는 값은 다음과 같습니다.<br /><br /> [Param](#Param) 자식 요소 두 개가 필요한 -   **File**(한 **Param** 자식 요소는 **Name** 특성이 **Source**로 지정되고 다른 **Param** 자식 요소는 **Name** 특성이 **Dest**로 지정됨)<br />**Param** 자식 요소 한 개가 필요한 -   [Setter]()|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="TaskLibrary"></a> TaskLibrary  
 이 요소는 [Task](#Task) 요소 집합을 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
 표 65는 [TaskLibrary](#TaskLibrary) 요소에 대한 정보를 제공합니다.  

### <a name="table-65-tasklibrary-element-information"></a>표 65. TaskLibrary 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[DesignerConfig](#DesignerConfig) 요소 내에서 0회 또는 1회(DLL에 이 UDI 마법사 디자이너 구성 파일에 해당하는 사용자 지정 작업이 없는 경우 이 요소는 선택 사항입니다.)|  
|부모 요소|**DesignerConfig**|  
|목차|**Task**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<DesignerConfig>  
   - <TaskLibrary>  
        +<Task DLL="" Description="Executes a process with the given command line." Type="Microsoft.Wizard.ShellExecuteTask" Name="Shell Execute Task">  
        +<Task DLL="OSDRefreshWizard.dll" Description="Discovers supported applications for install." Type="Microsoft.OSDRefresh.AppDiscoveryTask" Name="Application Discovery">  
        +<Task DLL="SharedPages.dll" Description="Check to ensure a wired network connection is available." Type="Microsoft.SharedPages.WiredNetworkTask" Name="Wired Network Check">  
        +<Task DLL="OSDRefreshWizard.dll" Description="Check to ensure power source is AC (not battery)." Type="Microsoft.OSDRefresh.ACPowerTask" Name="AC Power Check">  
        +<Task DLL="" Description="Check to ensure power source is AC (not battery)." Type="Microsoft.Wizard.CopyFilesTask" Name="Copy Files Task">  
     </TaskLibrary>  
   + <ValidatorLibrary>  
   + <DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="Validator"></a> Validator  
 이 요소는 유효성 검사기 라이브러리 내의 유효성 검사기를 지정합니다.  

##### <a name="element-information"></a>요소 정보  
 표 66은 [Validator](#Validator) 요소에 대한 정보를 제공합니다.  

### <a name="table-66-validator-element-information"></a>표 66. Validator 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[ValidatorLibrary](#ValidatorLibrary) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**ValidatorLibrary**|  
|목차|**Param**|  

##### <a name="element-attributes"></a>요소 특성  
표 67에는 [Validator](#Validator) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-67-attributes-and-corresponding-values-for-the-validator-element"></a>표 67. Validator 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**설명**|유효성 검사기에 대한 정보를 제공하는 텍스트를 지정하며, 이 텍스트는 UDI 마법사 디자이너에 표시됩니다.|  
|**DisplayName**|UDI 마법사 디자이너에 표시되는 유효성 검사기 매개 변수의 표시 이름을 지정합니다(이 이름은 일반적으로 **Name** 특성보다 구체적).|  
|**DLL**|유효성 검사기와 연결된 .dll 파일의 이름을 지정합니다(.dll 파일은 *installation_folder*\Templates\Distribution\Tools\\*platform* 폴더에 있어야 하며, 여기서 *installation_folder*는 MDT를 설치한 폴더이고 *플랫폼*은 32비트 버전인 경우 **x86**, 64비트 버전인 경우 **x64**).|  
|**Name**|해당 UDI 마법사 페이지 및 UDI 마법사 디자이너에 표시되는 유효성 검사기의 이름을 지정합니다.|  
|**유형**|레지스트리 팩터리에 등록되고 .dll 파일 내에서 특정 유효성 검사기를 호출하는 데 사용되는 유효성 검사기 형식을 지정합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="ValidatorLibrary"></a> ValidatorLibrary  
 이 요소는 [Validator](#Validator) 요소 집합을 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
 표 68은 [ValidatorLibrary](#ValidatorLibrary) 요소에 대한 정보를 제공합니다.  

### <a name="table-68-validatorlibrary-element-information"></a>표 68. ValidatorLibrary 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[DesignerConfig](#DesignerConfig) 요소 내에서 0회 또는 1회(DLL에 이 UDI 마법사 디자이너 구성 파일에 해당하는 사용자 지정 유효성 검사기가 없는 경우 이 요소는 선택 사항입니다.)|  
|부모 요소|**DesignerConfig**|  
|목차|**Validator**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 <DesignerConfig\>   + <TaskLibrary\>   - <ValidatorLibrary\>        +<Validator DLL="" Description="Requires text in a field" Type="Microsoft.Wizard.Validation.NonEmpty" Name="NonEmpty"\>        +<Validator DLL="" Description="Doesn't allow certain characters to be in a field" Type="Microsoft.Wizard.Validation.InvalidChars" Name="InvalidChars"\>        +<Validator DLL="" Description="Must follow a pre-defined pattern" Type="Microsoft.Wizard.Validation.RegEx" Name="NamedPattern"\>        +<Validator DLL="" Description="Require the contents match a regular expression" Type="Microsoft.Wizard.Validation.RegEx" Name="RegEx"\>     </ValidatorLibrary\>   + <DesignerMappings\></DesignerConfig\>  

## <a name="udi-wizard-designer-reference"></a>UDI 마법사 디자이너 참조  

### <a name="controls"></a>컨트롤  
 UDI 마법사 디자이너에 사용할 사용자 지정 마법사 페이지 편집기를 만드는 데 사용되는 컨트롤은 WPF **UserControl** 인스턴스입니다. 표 69에는 사용자 지정 마법사 페이지 편집기를 만드는 데 사용할 수 있는 컨트롤이 나열되어 있습니다.  

### <a name="table-69-controls-that-can-be-used-to-create-custom-wizard-page-editors"></a>표 69. 사용자 지정 마법사 페이지 편집기를 만드는 데 사용할 수 있는 컨트롤  

|컨트롤|설명|  
|-|-|  
|[CollectionTControl](#CollectionTControl)|이 컨트롤은 [Page](#Page) 요소 내의 [Data](#Data) 요소에 저장된 데이터를 편집하는 데 사용됩니다.|  
|[FieldElementControl](#FieldElementControl)|이 컨트롤은 필드를 편집하는 데 사용되며, 일반적으로 .xaml 페이지의 TextBox 컨트롤에 연결됩니다.|  
|[SetterControl](#SetterControl)|이 컨트롤은 UDI 마법사 구성 파일의 [setter]() 요소 값을 수정하는 데 사용됩니다.|  

####  <a name="CollectionTControl"></a> CollectionTControl  
 이 컨트롤은 데이터 편집을 위한 여러 기능을 제공합니다. 이 컨트롤 사용 방법을 배우는 가장 좋은 방법은 페이지의 **Data** 요소 아래에서 데이터를 편집하는 방법을 보여주는 샘플을 살펴보는 것입니다. 특히 이 샘플은 이 컨트롤에서 항목을 추가, 제거 및 편집하는 방법을 보여줍니다.  

####  <a name="FieldElementControl"></a> FieldElementControl  
 이 컨트롤은 필드를 편집하는 데 사용되며, 일반적으로 .xaml 페이지의 **TextBox** 컨트롤에 연결됩니다.  

##### <a name="example"></a>예  
 .xaml 파일에서 발췌한 다음 구문은 자식 **TextBox** 컨트롤을 사용하여 마법사 페이지의 필드 기본값을 구성할 수 있는 **FieldElementControl** 사용 방법을 보여줍니다.  

```  
<Controls:FieldElementControl  
Width="450"  
Margin="0,5"  
FieldData="{Binding DataContext.Location, ElementName=ControlRoot}"  
HeaderText="Location Combo Box"  
InstructionText="Here you can configure the behavior of the location combo box."  
HideValidationTab="True">  

<TextBox Text="{Binding FieldData.DefaultValue,  
 UpdateSourceTrigger=PropertyChanged,  
 Mode=TwoWay}"/>  
</Controls:FieldElementControl>  
```  

##### <a name="properties"></a>속성  

###### <a name="fielddata"></a>FieldData  
 이 문자열 속성은 **FieldElementControl**을 필드의 기본 XML에 연결하는 방법에 대한 정보를 포함하고 있습니다. 연결은 페이지 편집기 인터페이스의 속성에 설정됩니다. .xaml 파일에서 발췌한 다음 구문은 **FieldData** 속성의 사용 방법을 보여줍니다.  

```  
FieldData="{Binding DataContext.Location, ElementName=ControlRoot}"  
```  

 이 구문에서는 페이지 편집기 인터페이스를 **ControlRoot**라 하고 **ElementName** 매개 변수에 지정됩니다. 바인딩은 **ControlRoot** 페이지 편집기 인터페이스의 **DataContext.Location** 속성에 수행됩니다. **DataContext**는 UDI 마법사 구성 파일 내부의 [Page](#Page) 요소를 가리키는 보기 모델입니다. **Location**은 가능한 위치 목록을 반환하는 보기 속성이며 UDI 마법사 구성 파일 내에서 [Data](#Data) 요소를 통해 정의됩니다. 각 위치는 UDI 마법사 구성 파일 내에서 [DataItem](#DataItem) 요소를 통해 정의됩니다.  

###### <a name="headertext"></a>HeaderText  
 이 문자열 속성을 사용하면 [FieldElementControl](#FieldElementControl) 컨트롤에 대한 헤더를 지정할 수 있습니다. 헤더는 컨트롤의 제목 역할을 하며 컨트롤 바로 위에 주황색 볼드 텍스트로 표시됩니다.  

###### <a name="instructiontext"></a>InstructionText  
 이 문자열 속성을 사용하면 [FieldElementControl](#FieldElementControl) 컨트롤에 대한 정보 텍스트를 지정할 수 있습니다. 일반적으로 텍스트는 필드에 대한 간단한 설명을 제공하고 빌드 구성이 해당 마법사 페이지에 미치는 영향을 설명하는 데 사용됩니다.  

###### <a name="hideenablebutton"></a>HideEnableButton  
 이 부울 속성을 사용하면 상태를 **잠금 해제됨** 및 **잠김**(설정 또는 해제) 사이에서 변경하는 단추의 표시 여부를 제어할 수 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 단추가 표시되지 않습니다.  

-   **False**로 설정하면 단추가 표시됩니다(기본값)  

###### <a name="hidedefaulttab"></a>HideDefaultTab  
 이 부울 속성을 사용하면 기본값을 설정하는 데 사용되는 컨트롤을 포함하고 있는 섹션의 표시 여부를 제어할 수 있습니다. 속성이 탭을 참조하지만, [FieldElementControl](#FieldElementControl)에는 탭은 없고 숨길 수 있는 섹션이 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 섹션이 표시되지 않습니다.  

-   **False**로 설정하면 섹션이 표시됩니다(기본값)  

###### <a name="hideborder"></a>HideBorder  
 이 부울 속성을 사용하면 필드 컨트롤 주변의 경계 표시 여부를 제어할 수 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 경계가 표시되지 않습니다.  

-   **False**로 설정하면 경계가 표시됩니다(기본값)  

###### <a name="hideimage"></a>HideImage  
 이 부울 속성을 사용하면 **FieldImageSource** 속성이 구성하는 이미지의 표시 여부를 제어할 수 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 이미지가 표시되지 않습니다.  

-   **False**로 설정하면 이미지가 표시됩니다(기본값)  

###### <a name="hidevalidationtab"></a>HideValidationTab  
 이 부울 속성을 사용하면 유효성 검사기 목록이 관리되는 섹션의 표시 여부를 제어할 수 있습니다. 속성이 탭을 참조하지만, [FieldElementControl](#FieldElementControl)에는 탭은 없고 숨길 수 있는 섹션이 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 섹션이 표시되지 않습니다.  

-   **False**로 설정하면 섹션이 표시됩니다(기본값)  

###### <a name="hidesummarytab"></a>HideSummaryTab  
 이 부울 속성을 사용하면 필드 요약 캡션을 구성하는 섹션의 표시 여부를 제어할 수 있습니다. 캡션 및 필드의 해당 값은 단계 흐름의 **SummaryPage** 마법사 페이지 형식에 표시됩니다. 속성이 탭을 참조하지만, [FieldElementControl](#FieldElementControl)에는 탭은 없고 숨길 수 있는 섹션이 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 섹션이 표시되지 않습니다.  

-   **False**로 설정하면 섹션이 표시됩니다(기본값)  

###### <a name="hidetasksequencetab"></a>HideTaskSequenceTab  
 이 부울 속성을 사용하면 필드에 해당하는 작업 순서 변수를 구성하는 섹션의 표시 여부를 제어할 수 있습니다. 속성이 탭을 참조하지만, [FieldElementControl](#FieldElementControl)에는 탭은 없고 숨길 수 있는 섹션이 있습니다. 설정 방법은 다음과 같습니다.  

-   **True**로 설정하면 섹션이 표시되지 않습니다.  

-   **False**로 설정하면 섹션이 표시됩니다(기본값)  


####  <a name="SetterControl"></a> SetterControl  
 UDI 마법사 구성 파일의 [Setter]() 요소 값을 수정하려면 이 컨트롤을 사용합니다. 이 컨트롤에는 **setter** 요소의 값을 수정하는 데 사용되는 자식 컨트롤이 포함되어 있습니다.  

##### <a name="example"></a>예  
 .xaml 파일에서 발췌한 다음 구문은 자식 **TextBox** 컨트롤을 사용하여 **KeyLocationSetter**라고 하는 [Setter]() 요소를 수정할 수 있는 **SetterControl** 사용 방법을 보여줍니다.  

```  
<Controls:SetterControl Margin="5"  
        Width="450"  
        HeaderText="Title text"  
        SetterData="{Binding KeyLocationSetter}"   
        InstructionText="What this means…"  
        HorizontalAlignment="Left">  

    <TextBox  
                   Margin="0,3"  
                   Text="{Binding SetterData.SetterValue, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"  
    />  

</Controls:SetterControl>  
```  

##### <a name="properties"></a>속성  

###### <a name="setterdata"></a>SetterData  
 setter에 연결하는 보기 또는 보기 모델의 속성에 바인딩해야 합니다. 바인딩 방법은 **FieldElementControl**에 대한 설명처럼 필드에 바인딩하는 방법과 비슷합니다.  

###### <a name="headertext"></a>HeaderText  
 이 속성을 사용하면 컨트롤 헤더에 표시될 텍스트를 설정할 수 있습니다. 이 속성을 컨트롤 제목으로 생각해 보세요. 기본적으로 제목은 주황색 볼드 텍스트로 표시됩니다.  

###### <a name="instructiontext"></a>InstructionText  
 이 속성을 헤더 아래에 표시할 텍스트로 설정합니다. 일반적으로 사용자 지정 편집기 사용자에게 필드 동작을 수정해야 하는 시기와 이유를 알려주는 지침 텍스트입니다.  

### <a name="interfaces"></a>인터페이스  
표 70에는 사용자 지정 마법사 페이지 편집기를 만드는 데 사용할 수 있는 인터페이스가 나열되어 있습니다.  

### <a name="table-70-interfaces-that-can-be-used-to-create-custom-wizard-page-editors"></a>표 70. 사용자 지정 마법사 페이지 편집기를 만드는 데 사용할 수 있는 인터페이스  

|**인터페이스**|**설명**|  
|-|-|  
|[IDataService](#IDataService)|UDI 마법사 구성 파일의 **Data** 요소에 필드를 연결하려면 이 인터페이스를 사용합니다.|  
|[IMessageBoxService](#IMessageBoxService)|이 인터페이스는 메시지 상자를 표시하는 데 사용할 수 있는 메서드에 대한 액세스를 제공합니다.|  

####  <a name="IDataService"></a> IDataService  
 이 인터페이스는 여러 속성 및 메서드를 포함하고 있지만, 사용자에게 필요한 속성은 하나뿐입니다. 여기에 그 속성에 대해 설명되어 있습니다.  

 클래스에 다음과 비슷한 코드를 사용하면 종속성 주입을 통해 이 인터페이스에 대한 포인터를 가져올 수 있습니다.  

```  
[Dependency]  
public IDataService DataService { get; set; }  
```  

##### <a name="properties"></a>속성  
 표 71에는 **IDataService** 인터페이스의 속성이 나열되어 있습니다.  

### <a name="table-71-properties-for-the-idataservice-interface"></a>표 71. IDataService 인터페이스의 속성  

|**인터페이스**|**설명**|  
|-|-|  
|[CurrentPage](#CurrentPage)|이 속성은 UDI 마법사 구성 파일에서 편집되고 있는 현재 페이지의 컨텍스트 하에 있는 XML 요소, 특성 및 값에 대한 액세스를 제공합니다.|  

######  <a name="CurrentPage"></a> CurrentPage  

```  
XElement CurrentPage { get; set; }  
```  

 이 속성은 현재 페이지의 XML에 대한 액세스를 제공합니다. 사용자가 이 속성을 설정할 일은 없지만, 페이지의 XML을 자유롭게 수정할 수 있습니다. 샘플 페이지 편집기는 XML 수정 예제를 보여줍니다. 이 속성은 사용자 지정 데이터가 있는 경우에 주로 사용됩니다. 필드 및 속성(setter)의 경우 모든 세부 정보를 처리하는 미리 빌드된 컨트롤을 사용할 수 있습니다.  

####  <a name="IMessageBoxService"></a> IMessageBoxService  
 이 인터페이스는 메시지 상자를 표시하는 데 사용할 수 있는 메서드에 대한 액세스를 제공합니다. 메시지 상자를 표시하려면 인터페이스가 필요한 이유를 궁금하게 생각하는 분들이 있습니다. 사실은 인터페이스가 꼭 필요하지는 않습니다. 이 인터페이스가 디자이너 페이지에 대한 자동화 테스트 작성을 도와주기 때문에 Microsoft에서는 이 인터페이스를 코드에 함께 사용합니다.  

 그러나 이러한 메서드를 사용하면 한 가지 이점이 있습니다. 대화 상자의 “소유자”가 항상 UDI 마법사로 설정되며, 따라서 주 창을 사용하여 대화 상자가 올바르게 그룹화됩니다.  

 클래스에 다음과 비슷한 코드를 사용하면 종속성 주입을 통해 이 인터페이스에 대한 포인터를 가져올 수 있습니다.  

```  
[Dependency]  
public IMessageBoxService MessageBoxes { get; set; }  
```  

##### <a name="methods"></a>방법  
 표 72에는 **IMessageBoxService** 인터페이스에 대한 메서드가 나열되어 있습니다.  

### <a name="table-72-methods-for-the-imessageboxservice-interface"></a>표 72. IMessageBoxService 인터페이스에 대한 메서드  

|**방법**|**설명**|  
|-|-|  
|[ShowMessageBox](#ShowMessageBox)|이 오버로드된 메서드는 다음 멤버가 포함된 메시지 상자를 표시합니다.<br /><br /> -   [ShowMessageBox(String message, String caption, MessageBoxImage icon)](#ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon)<br />-   [ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon)](#ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon)<br />-   [ShowMessageBox(Exception exception)](#ShowMessageBox_Exception_exception)|  
|[ShowDialogWindow](#ShowDialogWindow)|새 대화 상자를 만들려면 이 메서드를 사용합니다.|  
|[ShowWizardWindow](#ShowWizardWindow)|대화 상자 내부에 탐색을 위한 **다음** 및 **뒤로** 단추가 포함된 사용자 지정 편집기를 표시하려면 이 메서드를 사용합니다.|  

######  <a name="ShowMessageBox"></a> ShowMessageBox  
 이 메서드는 사용자 지정 마법사 페이지 편집기의 자식인 메시지 상자를 표시합니다. 이 멤버는 오버로드됩니다. 표 73에는 멤버 목록과 각각에 대한 간략한 설명이 포함되어 있습니다. 각 멤버에 대한 전체 정보(구문, 사용법 및 예제 포함)는 각 멤버에 해당하는 섹션을 참조하세요.  

### <a name="table-73-overloaded-members-for-the-showmessagbox-method"></a>표 73. ShowMessagBox 메서드에 대해 오버로드된 멤버  

|멤버|설명|  
|-|-|  
|[ShowMessageBox(String message, String caption, MessageBoxImage icon)](#ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon)|아이콘 및 **확인** 단추가 있는 메시지 상자를 표시합니다.|  
|[ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon)](#ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon)|아이콘 및 가능한 단추 조합이 있는 메시지 상자를 표시합니다.|  
|[ShowMessageBox(Exception exception)](#ShowMessageBox_Exception_exception)|예외에 대한 정보를 제공하고 **확인** 단추가 있는 메시지 상자를 표시합니다.|  

######  <a name="ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon"></a> ShowMessageBox(String message, String caption, MessageBoxImage icon)  

```  
void ShowMessageBox(String message, String caption, MessageBoxImage icon);  
```  

 이 메서드는 **확인** 단추가 있는 메시지 상자를 표시합니다. 표 74를 참조하세요.  

### <a name="table-74-parameters-for-the-showmessageboxstring-message-string-caption-messageboximage-icon-method"></a>표 74. ShowMessageBox(String message, String caption, MessageBoxImage icon) 메서드에 대한 매개 변수  

|**매개 변수**|**설명**|  
|-|-|  
|**message**|메시지 상자의 콘텐츠 영역에 표시할 메시지|  
|**caption**|대화 상자의 제목 표시줄에 표시할 텍스트|  
|**icon**|메시지 상자에 표시할 아이콘 형식|  

######  <a name="ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon"></a> ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon)  

```  
MessageBoxResult ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon);  
```  

 이 메서드는 표시하려는 단추 집합이 있는 메시지 상자를 표시하고 사용자가 클릭한 단추를 보고합니다. 표 75를 참조하세요.  

### <a name="table-75-parameters-for-the-showmessageboxstring-message-string-caption-messageboxbutton-button-messageboximage-icon-method"></a>표 75. ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon) 메서드에 대한 매개 변수  

|**매개 변수**|**설명**|  
|-|-|  
|**message**|메시지 상자의 콘텐츠 영역에 표시할 메시지|  
|**caption**|대화 상자의 제목 표시줄에 표시할 텍스트|  
|**button**|표시할 단추|  
|**icon**|메시지 상자에 표시할 아이콘 형식|  

######  <a name="ShowMessageBox_Exception_exception"></a> ShowMessageBox(Exception exception)  

```  
void ShowMessageBox(Exception exception);  
```  

 이 메서드는 예외에 대한 정보를 보고하는 메시지 상자를 표시합니다. 이 메시지 상자에는 **확인** 단추가 하나 있습니다. 표 76을 참조하세요.  

### <a name="table-76-parameters-for-the-showmessageboxexception-exception-method"></a>표 76. ShowMessageBox(Exception exception) 메서드에 대한 매개 변수  

|**매개 변수**|**설명**|  
|-|-|  
|**exception**|보고할 예외(대화 상자는 **exception.Message**를 콘텐츠로 사용)|  

######  <a name="ShowDialogWindow"></a> ShowDialogWindow  

```  
void ShowDialogWindow(Type viewType, DialogInteraction dialogPayload);  
```  

 이 메서드는 새 대화 상자를 만들며, 대화 상자의 내용은 사용자가 **viewType** 매개 변수에 제공하는 텍스트입니다. UDI 디자이너는 이 형식의 새 인스턴스를 만들어서 **확인** 및 **취소** 단추가 있는 대화 상자에 래핑합니다.  

 사용자는 dialogPayload 매개 변수를 사용하여 데이터를 컨트롤에 전달합니다. SDK 디렉터리의 **SampleEditor** 솔루션에 이 기능의 사용 방법 예제가 포함되어 있습니다.  

######  <a name="ShowWizardWindow"></a> ShowWizardWindow  

```  
void ShowWizardWindow(Type viewType, DialogInteraction dialogPayload);  
```  

 이 메서드를 사용하면 대화 상자 내부에 탐색을 위한 **다음** 및 **뒤로** 단추가 포함된 사용자 지정 편집기를 표시할 수 있습니다. Microsoft는 이 메서드를 사용하는 방법에 대한 샘플을 제공하지 않습니다.  

###  <a name="UDIWizardConfigurationFileSchemaReference"></a> UDI 마법사 구성 파일 스키마 참조  
 이 파일은 UDI 마법사에서 사용되고 UDI 마법사 디자이너를 통해 구성됩니다. 이 파일은 다음을 구성하는 데 사용됩니다.  

-   UDI 마법사에 표시되는 마법사 페이지  

-   UDI 마법사의 마법사 페이지 순서  

-   각 마법사 페이지의 필드에 대한 설정  

-   UDI 마법사 디자이너에서 사용할 수 있는 StageGroups  

-   UDI 마법사 디자이너의 각 배포 마법사 내에서 사용할 수 있는 단계  

  표 77에는 UDI 마법사 구성 파일의 요소 및 해당 설명이 나열되어 있습니다. **Wizard** 요소는 이 참조의 루트 노드입니다.  

### <a name="table-77-elements-in-the-udi-wizard-configuration-file-and-their-descriptions"></a>표 77. UDI 마법사 구성 파일의 요소 및 해당 설명  

|**요소 이름**|**설명**|  
|-|-|  
|[Data](#Data)|[Page](#Page) 요소 내의 개별 [DataItem](#DataItem) 요소를 그룹화하며 **Name** 특성을 통해 명명됩니다.|  
|[DataItem](#DataItem)|[Page](#Page) 요소 내의 개별 [Setter]() 요소를 그룹화합니다. [DataItem](#DataItem) 요소 내에 [Data](#Data) 요소를 하나 이상 포함하여 계층적 데이터를 만들 수 있습니다. 각 **DataItem** 요소는 개별 항목을 나타냅니다. 예를 들어 사용 가능한 드라이브 목록에는 표시 이름에 대한 **DataItem**과 해당 드라이브 문자에 대한 또 다른 **DataItem** 요소가 있을 수 있습니다.|  
|[기본값](#Default)|부모 [Field](#Field) 또는 [RadioGroup](#RadioGroup) 요소에 지정된 필드의 기본값을 지정합니다. 기본값은 이 요소로 묶인 값으로 설정됩니다.|  
|[DLL](#DLL)|UDI 마법사 및 UDI 마법사 디자이너에서 로드하여 참조할 DLL을 지정합니다.|  
|[DLLs](#DLLs)|개별 [DLL](#DLL) 요소를 그룹화합니다.|  
|[오류](#Error)|작업에서 반환할 수 있는 가능한 오류 코드를 지정합니다. 오류 코드의 값은 작업의 **HRESULT**를 통해 반환된 후 이 요소에 의해 트래핑되어 보다 구체적인 오류 정보를 제공합니다.|  
|[ExitCode](#ExitCode)|작업에 가능한 종료 코드를 지정합니다. 종료 코드는 작업에서 기대하는 반환 코드입니다. 가능한 각 종료 코드에 대해 **ExitCode** 요소를 만듭니다. 또는 다른 **ExitCode** 요소에 나열되지 않은 반환 코드를 처리하도록 **Value** 특성에서 별표(\*)를 지정해도 됩니다.|  
|[ExitCodes](#ExitCodes)|[Task](#Task) 요소 또는 **Error** 요소에 대한 [ExitCode](#ExitCode) 및 [Error](#Error) 요소 집합을 그룹화합니다.|  
|[Field](#Field)|[Page](#Page) 요소에서 XML로 사용자 지정을 제공하는 데 사용되는 컨트롤 인스턴스를 지정합니다. 모든 컨트롤이 XML로 사용자 지정을 제공할 수 있는 것은 아니고, [Field](#Field) 요소를 사용하는 컨트롤만 가능합니다.|  
|[Fields](#Fields)|[Page](#Page) 요소 내의 개별 [Field](#Field) 요소를 그룹화합니다.|  
|[File](#File)|**Microsoft.Wizard.CopyFilesTask** 작업 형식을 사용하여 파일 복사 작업의 원본 및 대상을 지정합니다. 단일 작업에서 두 개 이상의 파일을 복사하도록 별도의 **File** 요소를 포함할 수 있습니다.|  
|[Page](#Page)|페이지의 인스턴스를 지정하고 페이지에 대한 모든 구성 설정을 포함합니다.|  
|[PageRef](#PageRef)|[StageGroup](#StageGroup) 내부의 [Stage](#Stage) 내부에 있는 페이지의 인스턴스 참조를 지정합니다.|  
|[Pages](#Pages)|개별 [Page](#Page) 요소를 그룹화합니다.|  
|[RadioGroup](#RadioGroup)|[Field](#Field) 요소 내에서 라디오 단추 그룹을 지정합니다.|  
|[StageGroup](#StageGroup)|하나 이상의 단계 그룹을 지정합니다.|  
|[StageGroups](#StageGroups)|UDI 마법사 구성 파일 내에서 단계 그룹 집합을 그룹화합니다.|  
|[Setter]()|**Property** 속성에 명명된 속성의 값 속성 설정을 지정합니다.|  
|[Stage](#Stage)|[StageGroup](#StageGroup) 내에서 단계를 지정하고 하나 이상의 [PageRef](#PageRef) 요소를 포함합니다.|  
|[Style](#Style)|마법사 맨 위에 표시되는 제목과 UDI 마법사에 표시되는 배너 이미지를 포함하여 UDI 마법사의 모양과 느낌을 구성하는 개별 [setter]() 요소를 그룹화합니다.|  
|[Task](#Task)|부모 [Page](#Page) 요소에 지정된 페이지에서 실행할 작업을 지정합니다.|  
|[태스크](#Tasks)|[Page](#Page) 요소에 대한 작업 집합을 그룹화합니다.|  
|[Validator](#Validator)|부모 [Field](#Field) 요소에 지정된 필드 컨트롤에 대한 유효성 검사기를 지정합니다.|  
|[Wizard](#Wizard)|다른 모든 요소의 루트를 지정합니다.|  

####  <a name="Data"></a> Data  
 이 요소는 [Page](#Page) 요소 내의 개별 [DataItem](#DataItem) 요소를 그룹화하며 **Name** 특성을 통해 명명됩니다.  

##### <a name="element-information"></a>요소 정보  
표 78은 [Data](#Data) 요소에 대한 정보를 제공합니다.  

### <a name="table-78-data-element-information"></a>표 78. Data 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Page](#Page) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Page**, **DataItem**|  
|목차|**DataItem**, **Setter**|  

##### <a name="element-attributes"></a>요소 특성  
 표 79에는 [Data](#Data) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-79-attributes-and-corresponding-values-for-the-data-element"></a>표 79. Data 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**Name**|[Data](#Data) 요소의 이름을 지정합니다.|  

##### <a name="remarks"></a>주의  
 **Name** 특성을 사용하면 코드로 특정 데이터 집합을 검색할 수 있습니다.  

##### <a name="example"></a>예  
 없음  

####  <a name="DataItem"></a> DataItem  
 이 요소는 [Page](#Page) 요소 내의 개별 [Setter]() 요소를 그룹화합니다. [DataItem](#DataItem) 요소 내에 [Data](#Data) 요소를 하나 이상 포함하여 계층적 데이터를 만들 수 있습니다. 각 **DataItem** 요소는 개별 항목을 나타냅니다. 예를 들어 사용 가능한 드라이브 목록에는 표시 이름에 대한 **DataItem**과 해당 드라이브 문자에 대한 또 다른 **DataItem** 요소가 있을 수 있습니다.  

##### <a name="element-information"></a>요소 정보  
 표 80은 [DataItem](#DataItem) 요소에 대한 정보를 제공합니다.  

### <a name="table-80-dataitem-element-information"></a>표 80. DataItem 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Data](#Data) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Data**|  
|목차|**Data**, **Setter**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

#### <a name="default"></a>기본값  
 이 요소는 부모 [Field](#Field) 또는 [RadioGroup](#RadioGroup) 요소에 지정된 필드의 기본값을 지정합니다. 기본값은 이 요소로 묶인 값으로 설정됩니다.  

##### <a name="element-information"></a>요소 정보  
표 81은 [Default](#Default) 요소에 대한 정보를 제공합니다.  

### <a name="table-81-default-element-information"></a>표 81. Default 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수 |[Field](#Field) 또는 [RadioGroup](#RadioGroup) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Field**, **RadioGroup**|  
|목차|잘 구성된(Well-Formed) XML 콘텐츠라면 모두 가능하지만, 표준 텍스트가 일반적입니다.|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 다음 예제에서 **표준 시간대** 필드의 기본값은 "태평양 표준시"로 설정됩니다.  

```  
<Field Name="TimeZone" Enabled="true" VarName="OSDTimeZone" Summary="Time Zone:">  
  <Default>Pacific Standard Time</Default>  
```  

####  <a name="DLL"></a> DLL  
 이 요소는 UDI 마법사 및 UDI 마법사 디자이너가 로드하여 참조할 DLL을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 82는 [DLL](#DLL) 요소에 대한 정보를 제공합니다.  

### <a name="table-82-dll-element-information"></a>표 82. DLL 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[DLLs](#DLLs) 요소 내에서 1회 이상|  
|부모 요소|**DLLs**|  
|목차|이 요소에는 콘텐츠가 허용되지 않습니다.|  

##### <a name="element-attributes"></a>요소 특성  
 표 83에는 [DLL](#DLL) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-83-attributes-and-corresponding-values-for-the-dll-element"></a>표 83. DLL 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|Name|UDI 마법사 및 UDI 마법사 디자이너가 참조할 DLL 이름을 지정합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<DLLs>  
  <DLL Name="OSDRefreshWizard.dll" />   
  <DLL Name="SharedPages.dll" />  
</DLLs>  
```  

####  <a name="DLLs"></a> DLLs  
 이 요소는 개별 [DLL](#DLL) 요소를 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 84는 [DLLs](#DLLs) 요소에 대한 정보를 제공합니다.  

### <a name="table-84-dlls-element-information"></a>표 84. DLLs 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|1대|  
|부모 요소|**Wizard**|  
|목차|**DLL**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<DLLs>  
   <DLL Name="OSDRefreshWizard.dll" />  
   <DLL Name="SharedPages.dll" />   
</DLLs>  
```  

####  <a name="Error"></a> Error  
 이 요소는 작업에서 반환할 수 있는 가능한 오류 코드를 지정합니다. 오류 코드의 값은 작업의 **HRESULT**를 통해 반환 및 트래핑되어 보다 구체적인 오류 정보를 제공합니다.  

##### <a name="element-information"></a>요소 정보  
 표 85는 [Error](#Error) 요소에 대한 정보를 제공합니다.  

### <a name="table-85-error-element-information"></a>표 85. Error 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [ExitCode](#ExitCode) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**ExitCodes**|  
|목차|잘 구성된(Well-Formed) XML 모든 콘텐츠|  

##### <a name="element-attributes"></a>요소 특성  
 표 86에는 [Error](#Error) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

###  

|**특성**|**설명**|  
|-|-|  
|**상태**|오류가 발생한 작업의 반환 상태를 지정합니다. 일반적으로 이 특성의 값은 Error로 설정됩니다. 이 값은 UDI 마법사의 마법사 페이지에 있는 **상태** 열에 표시됩니다.|  
|**Text**|작업에서 발생하는 오류 조건에 대한 설명 텍스트를 지정합니다.|  
|**유형**|이 요소가 오류, 경고 또는 성공 중 무엇을 나타내는지 지정합니다. **유형**에 지정된 값은 [ExitCodes](#ExitCodes) 요소 내에서 고유해야 합니다. 이 요소에 유효한 값은 다음과 같습니다.<br /><br /> -   **0.** 요소가 성공을 나타냅니다.<br />-   **1.** 요소가 경고를 나타냅니다.<br />-   **-1.** 요소가 오류를 나타냅니다.|  
|**값**|작업에서 숫자 값으로 반환한 코드 값을 지정합니다. 별표(*) 값은 다른 [Error](#Error) 요소에 나열되지 않은 반환 코드에 대한 기본 요소를 나타냅니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="ExitCode"></a> ExitCode  
 이 요소는 작업에 가능한 종료 코드를 지정합니다. 종료 코드는 작업에서 기대하는 반환 코드입니다. 가능한 각 종료 코드에 대해 **ExitCode** 요소를 만듭니다. 또는 다른 **ExitCode** 요소에 나열되지 않은 반환 코드를 처리하도록 **Value** 특성에서 별표(\*)를 지정해도 됩니다.  

##### <a name="element-information"></a>요소 정보  
표 87은 [ExitCode](#ExitCode) 요소에 대한 정보를 제공합니다.  

### <a name="table-87-exitcode-element-information"></a>표 87. ExitCode 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [ExitCodes](#ExitCodes) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**ExitCodes**|  
|목차|하나 이상의 [ExitCode](#ExitCode) 요소와 0개 이상의 [오류](#Error) 요소|  

##### <a name="element-attributes"></a>요소 특성  
표 88에는 [ExitCode](#ExitCode) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-88-attributes-and-corresponding-values-for-the-exitcode-element"></a>표 88. ExitCode 요소의 특성 및 해당 값  

|**특성**|설명|  
|-|-|  
|**상태**|작업의 반환 상태를 지정합니다. 이 특성의 값은 UDI 마법사의 해당 마법사 페이지에 있는 **상태** 열에 표시됩니다. 작업에 의미가 있는 값이라면 어떤 값이라도 이 특성에 사용할 수 있습니다. 다음은 이 특성에 사용되는 일반적인 값입니다.<br /><br /> -   성공<br />-   경고<br />-   오류|  
|**Text**|작업의 기존 코드에 대한 설명 텍스트를 지정합니다.|  
|**유형**|이 요소가 오류, 경고 또는 성공 중 무엇을 나타내는지 지정합니다. 유형에 지정된 값은 [ExitCodes](#ExitCodes) 요소 내에서 고유해야 합니다. 이 요소에 유효한 값은 다음과 같습니다.<br /><br /> -   **0.** 요소가 성공을 나타냅니다.<br />-   **1.** 요소가 경고를 나타냅니다.<br />-   **-1.** 요소가 오류를 나타냅니다.|  
|**값**|작업에서 숫자 값으로 반환한 코드 값을 지정합니다. 별표(*) 값은 다른 [ExitCode](#ExitCode) 요소에 나열되지 않은 반환 코드에 대한 기본 요소를 나타냅니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="ExitCodes"></a> ExitCodes  
 이 요소는 [Task](#Task) 또는 **Error** 요소에 대한 [ExitCode](#ExitCode) 및 [Error](#Error) 요소 집합을 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 89는 [ExitCodes](#ExitCodes) 요소에 대한 정보를 제공합니다.  

### <a name="table-89-exitcodes-element-information"></a>표 89. ExitCodes 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Task](#Task) 요소 내에서 1회|  
|부모 요소|**Task**|  
|목차|**Error**, **ExitCode**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Field"></a> Field  
 이 요소는 [Page](#Page) 요소에서 XML로 사용자 지정을 제공하는 데 사용되는 컨트롤 인스턴스를 지정합니다. 모든 컨트롤이 XML로 사용자 지정을 제공할 수 있는 것은 아니고, [Field](#Field) 요소를 사용하는 컨트롤만 가능합니다.  

##### <a name="element-information"></a>요소 정보  
 표 90은 [Field](#Field) 요소에 대한 정보를 제공합니다.  

### <a name="table-90-field-element-information"></a>표 90. Field 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Field](#Field) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Fields**|  
|목차|**Default**, **Validator**|  

##### <a name="element-attributes"></a>요소 특성  
표 91에는 [Field](#Field) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-91-attributes-and-corresponding-values-for-the-field-element"></a>표 91. Field 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**Enabled**|사용자 입력에 필드를 사용할 수 있는지 여부를 지정합니다(특성을 True 또는 False로 설정 가능).|  
|**Name**|필드 이름을 지정합니다.|  
|**요약**|이 필드가 설정하는 값의 **요약** 마법사 페이지에 표시되는 설명 텍스트를 지정합니다.|  
|**VarName**|부모 [Field](#Field) 요소의 필드를 사용하여 읽거나 구성되는 작업 순서 변수 이름을 지정합니다.|  

##### <a name="remarks"></a>주의  
 이 요소는 0개 이상의 [Default](#Default) 요소와 0개 이상의 [Validator](#Validator) 요소를 포함할 수 있습니다.  

##### <a name="example"></a>예  
 없음  

####  <a name="Fields"></a> Fields  
 이 요소는 [Page](#Page) 요소 내의 개별 [Field](#Field) 요소를 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 92는 [Fields](#Fields) 요소에 대한 정보를 제공합니다.  

### <a name="table-92-fields-element-information"></a>표 92. Fields 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Page](#Page) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Page**|  
|목차|**Field**, **RadioGroup**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="File"></a> File  
 이 요소는 **Microsoft.Wizard.CopyFilesTask** 작업 형식을 사용하여 파일 복사 작업의 원본 및 대상을 지정합니다. 단일 작업에서 두 개 이상의 파일을 복사하도록 별도의 [File](#File) 요소를 포함할 수 있습니다.  

##### <a name="element-information"></a>요소 정보  
 표 93은 [File](#File) 요소에 대한 정보를 제공합니다.  

### <a name="table-93-file-element-information"></a>표 93. File 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|작업 형식이 **Microsoft.Wizard.CopyFilesTask**인 각 작업에 대해 1회 이상|  
|부모 요소|**Task**|  
|목차|없음|  

##### <a name="element-attributes"></a>요소 특성  
 표 94에는 [File](#File) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-94-attributes-and-corresponding-values-for-the-file-element"></a>표 94. File 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**Dest**|**Source** 특성에 지정된 파일의 대상 폴더에 대한 정규화된 경로 또는 상대 경로를 지정합니다. 환경 변수는 경로의 일부로 허용됩니다.|  
|**원본**|**Microsoft.Wizard.CopyFilesTask** 작업 형식에서 복사하는 원본 파일의 정규화된 경로 또는 상대 경로를 지정합니다. 이 특성은 [File](#File) 요소 하나로 여러 파일을 복사할 수 있도록 와일드 카드 문자를 지원합니다. 환경 변수는 경로의 일부로 허용됩니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="PageElement"></a> Page  
 이 요소는 페이지의 인스턴스를 지정하고 페이지에 대한 모든 구성 설정을 포함합니다.  

##### <a name="element-information"></a>요소 정보  
표 95는 [Page](#Page) 요소에 대한 정보를 제공합니다.  

### <a name="table-95-page-element-information"></a>표 95. Page 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Pages](#Pages) 요소 내에서 1회 이상|  
|부모 요소|**Pages**|  
|목차|**Data**, **Fields**, **Setter**, **Tasks**|  

##### <a name="element-attributes"></a>요소 특성  
표 96에는 [Page](#Page) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-96-attributes-and-corresponding-values-for-the-page-element"></a>표 96. Page 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**DisplayName**|UDI 마법사 디자이너에 표시되는 마법사 페이지의 표시 이름을 지정합니다. 이 이름은 일반적으로 **Name** 특성보다 구체적입니다.|  
|**Name**|UDI 마법사 디자이너에 표시되는 마법사 페이지의 이름을 지정합니다.|  
|**유형**|DLL 내의 특정 마법사 페이지와 직접 관련된 마법사 페이지의 유형을 지정합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="PageRef"></a> PageRef  
 이 요소는 [StageGroup](#StageGroup) 내부의 [Stage](#Stage) 내부에 있는 페이지의 인스턴스 참조를 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 97은 [PageRef](#PageRef) 요소에 대한 정보를 제공합니다.  

### <a name="table-97-pageref-element-information"></a>표 97. PageRef 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[Stage](#Stage) 요소 내에서 1회 이상|  
|부모 요소|**Stage**|  
|목차|없음|  

##### <a name="element-attributes"></a>요소 특성  
표 98에는 [PageRef](#PageRef) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-98-attributes-and-corresponding-values-for-the-pageref-element"></a>표 98. PageRef 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**Page**|[StageGroup](#StageGroup) 내부의 [Stage](#Stage) 내부에 있는 페이지 인스턴스를 지정합니다. 이 값을 [Page](#Page) 요소의 Name 특성으로 지정해야 합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Pages"></a> Pages  
 이 요소는 개별 [Page](#Page) 요소를 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 99는 [Pages](#Pages) 요소에 대한 정보를 제공합니다.  

### <a name="table-99-pages-element-information"></a>표 99. Pages 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|1대|  
|부모 요소|**Wizard**|  
|목차|**Page**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<Pages>  
   + <Page Name="WelcomePage" DisplayName="Welcome" Type="Microsoft.SharedPages.WelcomePage">  
   + <Page Name="ConfigScanPage" DisplayName="Deployment Readiness" Type="Microsoft.OSDRefresh.ConfigScanPage">  
   + <Page Name="ConfigScanBareMetal" DisplayName="Deployment Readiness" Type="Microsoft.OSDRefresh.ConfigScanPage">  
   + <Page Name="RebootPage" DisplayName="Reboot" Type="Microsoft.OSDRefresh.RebootPage">  
   + <Page Name="WelcomePageReplace" DisplayName="Welcome" Type="Microsoft.SharedPages.WelcomePage">  
   + <Page Name="VolumePage" DisplayName="Volume" Type="Microsoft.OSDRefresh.VolumePage">  
   + <Page Name="UserRestorePage" DisplayName="Select Target" Type="Microsoft.OSDRefresh.UserStatePage">  
   + <Page Name="ComputerPage" DisplayName="New Computer Details" Type="Microsoft.OSDRefresh.ComputerPage">  
   + <Page Name="AdminAccounts" DisplayName="Administrator Password" Type="Microsoft.SharedPages.AdminAccountsPage">  
   + <Page Name="UDAPage" DisplayName="User Device Affinity" Type="Microsoft.OSDRefresh.UDAPage">  
   + <Page Name="LanguagePage" DisplayName="Language" Type="Microsoft.OSDRefresh.LanguagePage">  
   + <Page Name="ApplicationPage" DisplayName="Install Programs" Type="Microsoft.OSDRefresh.ApplicationPage">  
     <Page Name="SummaryPage" DisplayName="Summary" Type="Microsoft.Shared.SummaryPage" />   
   + <Page Name="UserCapturePageOldPC" DisplayName="Select Target" Type="Microsoft.OSDRefresh.UserStatePage">  
   + <Page Name="ProgressPage" DisplayName="Capture Data" Type="Microsoft.OSDRefresh.ProgressPage">  
   + <Page Name="RebootAfterCapture" DisplayName="Reboot" Type="Microsoft.OSDRefresh.RebootPage">  
</Pages>  
```  

####  <a name="RadioGroup"></a> RadioGroup  
 이 요소는 [Field](#Field) 요소 내에서 라디오 단추 그룹을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 100은 [RadioGroup](#RadioGroup) 요소에 대한 정보를 제공합니다.  

### <a name="table-100-radiogroup-element-information"></a>표 100. RadioGroup 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[Field](#Fields) 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Fields**|  
|목차|**기본값**|  

##### <a name="element-attributes"></a>요소 특성  
 표 101에는 [RadioGroup](#RadioGroup) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-101-attributes-and-corresponding-values-for-the-radiogroup-element"></a>표 101. RadioGroup 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**Locked**|라디오 단추 그룹을 사용자 입력에 사용할 것인지 여부를 지정합니다. 특성을 다음 값으로 설정할 수 있습니다.<br /><br /> -   **True**. 라디오 단추가 사용되지 않으며 사용자가 그룹에서 라디오 단추를 선택할 수 없습니다.<br />-   **False**. 라디오 단추가 사용되며 사용자가 그룹에서 라디오 단추를 선택할 수 있습니다.|  
|**Name**|라디오 옵션 그룹의 이름을 지정합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="StageGroup"></a> StageGroup  
 이 요소는 배포 단계 그룹을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 102는 [StageGroup](#StageGroup) 요소에 대한 정보를 제공합니다.  

### <a name="table-102-stagegroup-element-information"></a>표 102. StageGroup 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[StageGroups](#StageGroups) 요소 내에서 1회 이상|  
|부모 요소|**StageGroups**|  
|목차|**Stage**|  

##### <a name="element-attributes"></a>요소 특성  
 표 103에는 [StageGroups](#StageGroup) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-103-attributes-and-corresponding-values-for-the-stagegroup-element"></a>표 103. StageGroups 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**DisplayName**|UDI 마법사 디자이너에 표시되는 단계 그룹의 표시 이름을 지정합니다. 이 이름은 일반적으로 **Name** 특성보다 구체적입니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="StageGroups"></a> StageGroups  
 이 요소는 UDI 마법사 구성 파일 내에서 단계 그룹 집합을 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 104는 [StageGroups](#StageGroups) 요소에 대한 정보를 제공합니다.  

### <a name="table-104-stagegroups-element-information"></a>표 104. StageGroups 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[Wizard](#Wizard) 요소 내에서 0회 또는 1회|  
|부모 요소|**Wizard**|  
|목차|**StageGroup**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Setter"></a> Setter  
 이 요소는 **Property** 속성에 명명된 속성의 값 속성 설정을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
 표 105는 [Setter]() 요소에 대한 정보를 제공합니다.  

### <a name="table-105-setter-element-information"></a>표 105. Setter 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 부모 요소 내에서 0회 이상(이 요소는 선택 사항입니다.)|  
|부모 요소|**Data**, **DataItem**, **Page**, **Style**, **Task**, **Validator**|  
|목차|**Property** 특성에 문자열 값을 포함합니다.|  

##### <a name="element-attributes"></a>요소 특성  
표 106에는 [Setter]() 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-106-attributes-and-corresponding-values-for-the-setter-element"></a>표 106. Setter 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**속성**|설정할 속성 이름을 지정합니다. 속성 이름은 이 특성으로 묶인 값으로 설정됩니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

#### <a name="stage"></a>단계  
 이 요소는 [StageGroup](#StageGroup) 내에서 [단계](#Stage)를 지정하고 하나 이상의 [PageRef](#PageRef) 요소를 포함합니다.  

##### <a name="element-information"></a>요소 정보  
표 107은 [Stage](#Stage) 요소에 대한 정보를 제공합니다.  

### <a name="table-107-stage-element-information"></a>표 107. Stage 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[StageGroup](#StageGroup) 요소 내에서 1회 이상|  
|부모 요소|**StageGroup**|  
|목차|**PageRef**|  

##### <a name="element-attributes"></a>요소 특성  
표 108에는 [Stage](#Stage) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-108-attributes-and-corresponding-values-for-the-stage-element"></a>표 108. Stage 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**DisplayName**|UDI 마법사 디자이너에 표시되는 마법사 페이지의 표시 이름을 지정합니다. 이 이름은 일반적으로 **Name** 특성보다 구체적입니다.|  
|**Name**|단계의 이름을 지정합니다. 이 요소의 값은 **/stage: name** 명령줄 매개 변수를 사용하여 UDI 마법사를 시작할 때 사용됩니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Style"></a> Style  
 이 요소는 마법사 맨 위에 표시되는 제목과 UDI 마법사에 표시되는 배너 이미지를 포함하여 UDI 마법사의 모양과 느낌을 구성하는 개별 [Setter]() 요소를 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 109는 Style 요소에 대한 정보를 제공합니다.  

### <a name="table-109-style-element-information"></a>표 109. Style 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|1대|  
|부모 요소|**Wizard**|  
|목차|**Setter**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<Style>  
  <Setter Property="bannerFilename">UDI_Wizard_Banner.bmp</Setter>   
  <Setter Property="title">Operating System Deployment (OSD) Refresh Wizard</Setter>   
</Style>  
```  

####  <a name="TaskElement"></a> Task  
 이 요소는 부모 [Page](#Page) 요소에 지정된 페이지에서 실행할 작업을 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 110은 [Task](#Task) 요소에 대한 정보를 제공합니다.  

### <a name="table-110-task-element-information"></a>표 110. Task 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[Tasks](#Tasks) 요소 내에서 1회 이상|  
|부모 요소|**태스크**|  
|목차|**ExitCodes**, **File**, **Setter**|  

##### <a name="element-attributes"></a>요소 특성  
표 111에는 [Task](#Task) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-111-attributes-and-corresponding-values-for-the-task-element"></a>표 111. Task 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**DependsOn**|작업이 다른 작업에 종속되는지 여부를 지정합니다. 이 특성의 값은 다른 [Task](#Task) 요소의 **Name** 특성으로 설정됩니다. **참고:** 이 특성은 UDI 마법사 디자이너를 사용하여 구성할 수 없습니다. 하지만 .xml 파일을 직접 수정하여 [Task](#Task) 요소에 이 특성을 수동으로 추가할 수 있습니다.|  
|**DisplayName**|UDI 마법사 디자이너에 표시되는 작업의 표시 이름을 지정합니다. 이 이름은 일반적으로 **Name** 특성보다 구체적입니다.|  
|**Name**|작업 이름을 지정합니다. 이 이름은 고유해야 합니다.|  
|유형|실행할 작업의 작업 형식을 지정하며, 작업을 포함하고 있는 DLL에 정의됩니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Tasks"></a> Tasks  
 이 요소는 [Page](#Page) 요소에 대한 작업 집합을 그룹화합니다.  

##### <a name="element-information"></a>요소 정보  
표 112는 [Tasks](#Tasks) 요소에 대한 정보를 제공합니다.  

### <a name="table-112-tasks-element-information"></a>표 112. Tasks 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|각 [Page](#Page) 요소 내에서 0회 또는 1회(이 요소는 선택 사항입니다.)|  
|부모 요소|**Page**|  
|목차|**Task**|  

##### <a name="element-attributes"></a>요소 특성  
표 113에는 [Tasks](#Tasks) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-113-attributes-and-corresponding-values-for-the-tasks-element"></a>표 113. Tasks 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|**NameTitle**|해당 마법사 페이지에서 작업 이름을 포함하는 열의 맨 위에 표시되는 캡션을 지정합니다.|  
|**StatusTitle**|해당 마법사 페이지에서 작업 상태를 포함하는 열의 맨 위에 표시되는 캡션을 지정합니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="ValidatorElement"></a> Validator  
 이 요소는 부모 [Field](#Field) 요소에 지정된 필드 컨트롤에 대한 유효성 검사기를 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 114는 [Validator](#Validator) 요소에 대한 정보를 제공합니다.  

### <a name="table-114-validator-element-information"></a>표 114. Validator 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|[Field](#Field) 요소 내에서 0회 또는 1회|  
|부모 요소|**Field**|  
|목차|**Setter**|  

##### <a name="element-attributes"></a>요소 특성  
표 115에는 [Validator](#Validator) 요소의 특성 및 해당 설명이 나열되어 있습니다.  

### <a name="table-115-attributes-and-corresponding-values-for-the-validator-element"></a>표 115. Validator 요소의 특성 및 해당 값  

|**특성**|**설명**|  
|-|-|  
|유형|유효성 검사기의 형식을 지정하며, 유효성 검사기를 포함하고 있는 DLL에 정의됩니다.|  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  
 없음  

####  <a name="Wizard"></a> Wizard  
 이 요소는 다른 모든 요소의 루트를 지정합니다.  

##### <a name="element-information"></a>요소 정보  
표 116은 [Wizard](#Wizard) 요소에 대한 정보를 제공합니다.  

### <a name="table-116-wizard-element-information"></a>표 116. Wizard 요소 정보  

|**특성**|**값**|  
|-|-|  
|발생 수|1대|  
|부모 요소|없음|  
|목차|**DLLs**, **Pages**, **StageGroups**, **Style**|  

##### <a name="element-attributes"></a>요소 특성  
 이 요소는 특성이 없습니다.  

##### <a name="remarks"></a>주의  
 없음  

##### <a name="example"></a>예  

```  
<Wizard>  
   + <DLLs>  
   + <Style>  
   + <Pages>  
   + <StageGroups>  
</Wizard>  
```
