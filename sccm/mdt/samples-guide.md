---
title: MDT 샘플
titleSuffix: Microsoft Deployment Toolkit
description: 'Microsoft Deployment Toolkit 샘플입니다. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 2ff0100c-b7ef-4e09-8c96-fc1898390b6d
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 6b36da9f98749858829ab591571496532b26f290
ms.sourcegitcommit: 7198ec49d9ce68c6d55bfb9e2d537b5442a132cb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2018
ms.locfileid: "33915975"
---
# <a name="microsoft-deployment-toolkit-samples-guide"></a>Microsoft Deployment Toolkit 샘플 가이드  
 이 가이드는 MDT(Microsoft® Deployment Toolkit) 2013의 일부이며, 전문가 팀에 Windows 운영 체제 및 Microsoft Office를 배포하는 과정을 안내합니다. 특히 이 가이드는 특정 배포 시나리오에 대한 구성 설정 예제를 제공하도록 설계되었습니다.  

> [!NOTE]
>  이 문서에서 *Windows*는 달리 언급하지 않으면 Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 및 Windows Server 2008 R2 운영 체제에 적용됩니다. MDT는 ARM 프로세서 기반의 Windows 버전을 지원하지 않습니다. 마찬가지로, *MDT*도 달리 언급하지 않으면 MDT 2013을 나타냅니다.  

 **이 가이드를 사용하려면**  

 목차에서 시나리오 항목에 대한 목록을 검토합니다.  

1.  조직의 배포 목표에 가장 적합한 시나리오를 선택합니다.  

2.  선택한 시나리오에 대한 구성 설정 샘플을 검토합니다.  

3.  구성 설정 샘플을 사용자 환경의 구성 설정을 위한 기초로 사용합니다.  

4.  사용자 환경에 맞게 구성 설정 샘플을 사용자 지정합니다.  

 대부분의 경우 하나 이상의 시나리오를 통해 환경에 대한 구성 설정을 완료해야 할 수 있습니다.  

 이 가이드에는 구성 설정 예제만 포함되어 있으므로 다음 표에 나열된 가이드를 검토하면 환경의 구성 설정을 사용자 지정하는 데 도움이 될 수 있습니다.  

 |가이드|제공되는 지원|  
 |-|-|  
 |*Microsoft System Center 2012 R2 Configuration Manager 빠른 시작 가이드* |System Center 2012 R2 Configuration Manager를 사용하여 새 컴퓨터 배포 시나리오에서 Windows 8.1 운영 체제를 설치합니다.|  
 |*손쉬운 설치 빠른 시작 가이드* |새 컴퓨터 배포 시나리오에서 부팅 가능한 미디어를 사용하여 LTI(손쉬운 설치)를 통해 Windows 8.1 운영 체제를 설치합니다.|  
 |*사용자 구동 설치 빠른 시작 가이드* |새 컴퓨터 배포 시나리오에서 UDI(사용자 구동 설치) 및 System Center 2012 R2 Configuration Manager를 사용하여 Windows 8.1 운영 체제를 설치합니다.|  
 |*Microsoft Deployment Toolkit 사용* |ZTI(무인 자동 설치) 및 LTI 배포에 사용되는 구성 파일을 추가로 사용자 지정할 수 있습니다. 구성 설정에 대한 일반 구성 지침과 기술 참조도 제공합니다.|


## <a name="deploying-windows-8-applications-using-mdt"></a>MDT를 사용하여 Windows 8 애플리케이션 배포  
 MDT는 .appx 파일 확장명이 있는 Windows 8 애플리케이션 패키지를 배포할 수 있습니다. 이러한 애플리케이션 패키지는 Windows 8에 새로 추가되었습니다. 이러한 애플리케이션에 대한 자세한 내용은 [Windows 스토어 앱 개발](http://msdn.microsoft.com/windows/apps)을 참조하세요.  

 MDT를 사용하여 Windows 8 애플리케이션을 배포하려면 다음 단계를 수행합니다.  

-   [LTI를 사용하여 Windows 8 응용 프로그램 배포](#DeployWin8LTI)에서 설명한 대로 LTI를 사용하여 Windows 8 응용 프로그램을 배포합니다.  

-   [UDI를 사용하여 Windows 8 응용 프로그램 배포](#DeployWin8UDI)에서 설명한 대로 UDI(사용자 구동 설치)를 사용하여 Windows 8 응용 프로그램을 배포합니다.  

###  <a name="DeployWin8LTI"></a> LTI를 사용하여 Windows 8 응용 프로그램 배포  
 명령줄에서 설치 프로세스를 시작하는 다른 애플리케이션과 마찬가지로 LTI를 사용하여 Windows 8 애플리케이션을 배포할 수 있습니다. Deployment 워크벤치에 있는 애플리케이션 노드의 LTI 배포에 Windows 8 애플리케이션을 추가할 수 있습니다.  

 **LTI를 사용하여 Windows 8 응용 프로그램을 배포하려면**  

1.  애플리케이션이 저장될 네트워크 공유 폴더를 만듭니다.  

2.  이전 단계에서 만든 네트워크 공유 폴더에 Windows 8 애플리케이션을 복사합니다.  

     .appx Windows 8 애플리케이션 파일 및 애플리케이션 인증서가 포함된 다른 모든 필수 파일(예: .cer 파일)이 복사되었는지 확인합니다.  

3.  새 애플리케이션 마법사를 사용하여 Deployment 워크벤치의 애플리케이션 노드에 Windows 8 애플리케이션에 대한 LTI 애플리케이션 항목을 만듭니다.  

     새 애플리케이션 마법사를 수행하면서 **명령 정보** 마법사 페이지의 **명령줄**에서 **app_file_name**을 입력합니다. 여기서 *app_file_name*은 Windows 8 애플리케이션의 이름입니다.  

     Deployment 워크벤치에서 새 애플리케이션 마법사를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 다음 섹션을 참조하세요.  

    -   "배포 공유에서 배포되는 새 애플리케이션 만들기"  

    -   "다른 네트워크 공유 폴더에서 배포되는 새 애플리케이션 만들기"  

4.  LTI 작업 순서의 이전 단계에서 만든 LTI 애플리케이션 항목을 선택합니다.  

###  <a name="DeployWin8UDI"></a> UDI를 사용하여 Windows 8 응용 프로그램 배포  
 명령줄에서 설치 프로세스를 시작하는 다른 애플리케이션과 마찬가지로 UDI를 사용하여 Windows 8 애플리케이션을 배포할 수 있습니다. UDI 마법사 디자이너에서 **ApplicationPage** 마법사 페이지의 UDI 배포에 Windows 8 애플리케이션을 추가할 수 있습니다.  

> [!NOTE]
>  UDI를 사용하여 Windows 8 및 Windows 8 애플리케이션을 배포하려면 System Center 2012 R2 Configuration Manager가 필요합니다.  

 **UDI를 사용하여 Windows 8 응용 프로그램을 배포하려면**  

1.  애플리케이션이 저장될 네트워크 공유 폴더를 만듭니다.  

     이 폴더는 프로세스의 뒷부분에서 만들 Configuration Manager 애플리케이션의 원본 폴더가 됩니다.  

2.  이전 단계에서 만든 네트워크 공유 폴더에 Windows 8 애플리케이션을 복사합니다.  

     .appx Windows 8 애플리케이션 파일 및 애플리케이션 인증서가 포함된 다른 모든 필수 파일(예: .cer 파일)이 복사되었는지 확인합니다.  

3.  Windows 8 애플리케이션을 Configuration Manager 애플리케이션으로 추가합니다.  

4.  Configuration Manager 콘솔의 애플리케이션 만들기 마법사를 사용하여 Windows 8 애플리케이션에 대한 Configuration Manager 애플리케이션 항목을 만듭니다.  

     애플리케이션 만들기 마법사를 수행하면서 배포 유형 만들기 마법사를 사용하여 Windows 8 애플리케이션을 배포할 배포 유형을 만듭니다. 배포 유형 만들기 마법사에 있는 **콘텐츠** 페이지의 **설치 프로그램**에서 **app_file_name**을 입력합니다. 여기서 *app_file_name*은 Windows 8 애플리케이션의 이름입니다.  

     Configuration Manager 콘솔에서 애플리케이션 만들기 마법사를 수행하는 방법에 대한 자세한 내용은 Configuration Manager에 포함된 System Center 2012 Configuration Manager용 라이브러리 설명서에서 다음 섹션을 참조하세요.  

    -   [Configuration Manager에서 응용 프로그램을 만드는 방법](http://technet.microsoft.com/library/gg682159.aspx)  

    -   [Configuration Manager에서 배포 유형을 만드는 방법](http://technet.microsoft.com/library/gg682174.aspx#BKMK_Step3)  

    -   [Configuration Manager에서 응용 프로그램과 배포 유형을 관리하는 방법](http://technet.microsoft.com/library/gg682031)  

5.  Configuration Manager의 UDA(사용자 디바이스 선호도) 기능이 Configuration Manager 응용 프로그램 배포를 위해 사용자와 디바이스 간의 선호도를 지원하도록 제대로 구성되었는지 확인합니다.  

     Configuration Manager 응용 프로그램 배포를 지원하도록 UDA를 구성하는 방법에 대한 자세한 내용은 [Configuration Manager에서 사용자 디바이스 선호도를 관리하는 방법](http://technet.microsoft.com/library/gg699365)을 참조하세요.  

6.  대상 사용자에게 4단계에서 만든 애플리케이션을 배포합니다.  

     사용자에게 애플리케이션을 배포하는 방법에 대한 자세한 내용은 [Configuration Manager에서 애플리케이션을 배포하는 방법](http://technet.microsoft.com/library/gg682082)을 참조하세요.  

7.  UDI 마법사 디자이너를 사용하여 4단계에서 만든 Configuration Manager 애플리케이션이 포함되도록 **ApplicationPage** 마법사 페이지를 구성합니다.  

     UDI 마법사 디자이너를 사용하여 **ApplicationPage** 마법사 페이지를 구성하는 방법에 대한 자세한 내용은 *사용자 구동 설치 빠른 시작 가이드* MDT 문서에서 "5-11단계: 대상 컴퓨터에 대한 UDI 마법사 구성 파일 사용자 지정" 섹션을 참조하세요.  

8.  UDI 작업 순서의 이전 단계에서 만든 UDI 애플리케이션 항목을 선택합니다.  

    > [!NOTE]
    >  Windows 8 애플리케이션은 작업 순서에 따라 설치되지 않고, 사용자가 UDI의 사용자 중심 앱 설치 관리자 기능(AppInstall.exe)을 사용하여 대상 컴퓨터에 처음 로그온할 때 5단계에서 구성된 UDA 설정에 정의한 대로 설치됩니다.  

     UDI의 사용자 중심 앱 설치 관리자 기능에 대한 자세한 내용은 *Toolkit 참조* MDT 문서에서 "사용자 중심 앱 설치 관리자 참조" 섹션을 참조하세요.  

## <a name="managing-mdt-using-windows-powershell"></a>Windows PowerShell을 사용하여 MDT 관리  
 Deployment 워크벤치 및 Windows PowerShell을 사용하여 MDT 배포 공유를 관리할 수 있습니다. MDT에는 Windows PowerShell의 MDT 관련 기능을 사용하기 전에 로드해야 하는 Windows PowerShell™ 스냅인(Microsoft.BDD.SnapIn)이 포함되어 있습니다. MDT Windows PowerShell 스냅인에 포함된 항목은 다음과 같습니다.  

-   Windows PowerShell 공급자(MDTProvider) - 배포 공유의 콘텐츠에 대한 액세스를 제공합니다.  

-   MDT 배포 공유를 관리하는 기능을 제공하는 cmdlet  

 다음 단계를 수행하여 Windows PowerShell을 통해 MDT 배포 공유를 관리합니다.  

-   [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

-   [Windows PowerShell을 사용하여 배포 공유 만들기](#CreateDeployShare)에서 설명한 대로 Windows PowerShell을 사용하여 배포 공유를 만듭니다.  

-   [Windows PowerShell을 사용하여 배포 공유 속성 보기](#ViewDeployShareProp)에서 설명한 대로 Windows PowerShell을 사용하여 배포 공유 속성을 봅니다.  

-   [Windows PowerShell을 사용하여 배포 공유 목록 보기](#ViewListDeployShare)에서 설명한 대로 Windows PowerShell을 사용하여 배포 공유 목록을 봅니다.  

-   [Windows PowerShell을 사용하여 배포 공유 업데이트](#UpdateDeployShare)에서 설명한 대로 새 Windows PE(Windows 사전 설치 환경) 부팅 이미지를 생성하는 배포 공유를 업데이트합니다.  

-   [Windows PowerShell을 사용하여 연결된 배포 공유 업데이트](#UpdateLinkedDeployShare)에서 설명한 대로 배포 공유의 콘텐츠를 연결된 배포 공유로 복제하는 연결된 배포 공유를 업데이트합니다.  

-   [Windows PowerShell을 사용하여 배포 미디어 업데이트](#UpdateDeployMedia)에서 설명한 대로 배포 공유의 콘텐츠를 배포 미디어로 복제하는 배포 미디어를 업데이트한 다음, 새 부팅 가능 이미지를 생성합니다.  

-   [Windows PowerShell을 사용하여 배포 공유 항목 관리](#ManageItemDeployShare)에서 설명한 대로 배포 공유의 항목(예: 운영 체제, 운영 체제 패키지, 응용 프로그램 및 장치 드라이버)을 관리합니다.  

-   [배포 공유 채우기 자동화](#AutomatePopulateDeployShare)에서 설명한 대로 배포 공유의 항목 채우기(예: 운영 체제, 운영 체제 패키지, 응용 프로그램 및 장치 드라이버)를 자동화합니다.  

-   [Windows PowerShell을 사용하여 배포 공유 폴더 관리](#ManageDeployShareFolder)에서 설명한 대로 Windows PowerShell을 사용하여 배포 공유의 폴더를 관리합니다.  

###  <a name="LoadMDTSnapIn"></a> MDT Windows PowerShell 스냅인 로드  
 MDT cmdlet은 사용하기 전에 로드해야 하는 Windows PowerShell 스냅인(**Microsoft.BDD.SnapIn**)에 제공됩니다. 다음 방법 중 하나를 사용하여 MDT Windows PowerShell 스냅인을 로드할 수 있습니다.  

-   [시스템 모듈 가져오기 작업을 사용하여 MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapInImport)에서 설명한 대로 Window PowerShell 모듈 콘솔을 사용하여 MDT Windows PowerShell 스냅인을 로드합니다.  

-   [Add-PSSnapIn cmdlet을 사용하여 MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapInCmdlet)에서 설명한 대로 **Add-PSSnapIn** cmdlet을 사용하여 MDT Windows PowerShell 스냅인을 로드합니다.  

####  <a name="LoadMDTSnapInImport"></a>시스템 모듈 가져오기 작업을 사용하여 MDT Windows PowerShell 스냅인 로드  
 시스템 모듈 가져오기 작업에서는 %Windir%\System32\WindowsPowerShell\1.0\Modules 디렉터리의 모듈에 있는 모든 Windows PowerShell 모듈과 스냅인이 자동으로 포함됩니다. MDT는 MDT 설치 프로세스 중에 MDT Windows PowerShell 스냅인(**Microsoft.BDD.SnapIn**)을 해당 폴더에 자동으로 설치합니다.  

> [!NOTE]
>  시스템 모듈 가져오기 작업은 컴퓨터에 Windows PowerShell 3.0이 설치되지 않은 경우 Windows 7 및 Windows Server 2008 R2에서만 사용할 수 있습니다. Windows PowerShell 3.0부터 모듈에서 cmdlet을 처음 사용할 때 모듈을 자동으로 가져옵니다.  

 다음 절차 중 하나를 수행하여 시스템 모듈 가져오기 작업으로 Windows PowerShell 콘솔을 시작할 수 있습니다.  

-   작업 표시줄에서 **Windows PowerShell** 아이콘을 마우스 오른쪽 단추로 클릭한 다음, **시스템 모듈 가져오기**를 클릭합니다.  

-   **시작**을 클릭하고, **관리 도구**를 가리킨 다음, **Windows PowerShell 모듈**을 클릭합니다.  

 시스템 모듈 가져오기를 사용하여 Windows PowerShell 콘솔을 시작하는 방법에 대한 자세한 내용은 [시스템 모듈 가져오기를 사용하여 Windows PowerShell 시작](http://msdn.microsoft.com/library/windows/desktop/hh847866.aspx)을 참조하세요.  

####  <a name="LoadMDTSnapInCmdlet"></a> Add-PSSnapIn cmdlet을 사용하여 MDT Windows PowerShell 스냅인 로드  
 다음 예제와 같이 [Add-PSSnapIn](http://technet.microsoft.com/library/hh849705.aspx) cmdlet을 사용하여 모든 Windows PowerShell 환경에서 **Microsoft.BDD.PSSnapIn** MDT Windows PowerShell 스냅인을 로드할 수 있습니다.  

```  
Add-PSSnapin -Name Microsoft.BDD.PSSnapIn  
```  

###  <a name="CreateDeployShare"></a> Windows PowerShell을 사용하여 배포 공유 만들기  
 MDT Windows PowerShell cmdlet을 사용하여 배포 공유를 만들 수 있습니다. 배포 공유의 루트 폴더는 표준 Windows PowerShell cmdlet 및 WMI(Windows Management Instrumentation) 클래스 명령에 대한 호출을 사용하여 만들어지고 공유됩니다. 배포 공유는 MDTProvider Windows PowerShell 공급자 및 [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet을 사용하여 채워집니다. MDTProvider Windows PowerShell 드라이브는 **Add-MDTPersistentDrive** cmdlet을 사용하여 유지됩니다.  

 **MDT Windows PowerShell cmdlet을 사용하여 배포 공유를 준비하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 [New-Item cmdlet 사용](http://technet.microsoft.com/library/ee176914.aspx)에서 설명하는 **New-Item** cmdlet을 사용하여 새 배포 공유의 루트가 될 폴더를 만듭니다.  

    ```  
    New-Item "C:\MDTDeploymentShare$" -Type directory  
    ```  

     cmdlet에서 폴더가 성공적으로 만들어졌다고 표시합니다.  

3.  다음 예제와 같이 **WMI win32_share** 클래스를 사용하여 이전 단계에서 만든 폴더를 공유합니다.  

    ```  
    ([wmiclass]"win32_share").Create("C:\MDTDeploymentShare$", "MDTDeploymentShare$",0)  
    ```  

     **win32_share** 클래스를 호출하면 호출 결과가 반환됩니다. **ReturnValue**의 값이 영(0)이면 호출이 성공적으로 완료되었습니다.  

4.  다음 예제와 같이 [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) cmdlet을 사용하여 새 공유 폴더를 배포 공유로 지정합니다.  

    ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "C:\MDTDeploymentShare$" -Description "MDT Deployment Share Created with Cmdlets" -NetworkPath "\\WDG-MDT-01\MDTDeploymentShare$" -Verbose  
    ```  

     cmdlet에서 자동으로 배포 공유를 만들고 템플릿 배포 정보를 새 배포 공유에 복사하기 시작합니다. 복사 프로세스가 완료되면 cmdlet에서 새 배포 공유에 대한 정보를 표시합니다.  

    > [!NOTE]
    >  *Name* 매개 변수(DS002)에 제공되는 값은 고유해야 하며 기존 배포 공유 Windows PowerShell 드라이브와 같을 수 없습니다.  

5.  다음 예제와 같이 **dir** 명령을 사용하여 해당 배포 공유 폴더가 만들어졌는지 확인합니다.  

    ```  
    dir ds002:  
    ```  

     배포 공유의 루트에 있는 기본 폴더의 목록이 표시됩니다.  

6.  다음 예제와 같이 **Add-MDTPersistentDrive** cmdlet을 사용하여 지속형 MDT 배포 공유의 목록에 새 배포 공유를 추가합니다.  

    ```  
    $NewDS=Get-PSDrive "DS002"  
    Add-MDTPersistentDrive  -Name "DS002" -InputObject $NewDS Verbose  
    ```  

     이 예제에서는 *$NewDS* 변수를 사용하여 새 배포 공유에 대한 Windows PowerShell 드라이브 개체를 cmdlet에 전달합니다.  

     또는 다음 예제와 같이 [NewPSDrive](http://technet.microsoft.com/library/dd315340.aspx) 및 **Add-MDTPersistentDrive** cmdlet을 결합할 수도 있습니다.  

    ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "C:\MDTDeploymentShare$" -Description "MDT Deployment Share Created with Cmdlets" -NetworkPath "\\WDG-MDT-01\MDTDeploymentShare$" -Verbose | Add-MDTPersistentDrive -Verbose  
    ```  

     이전 예제에서 Windows PowerShell 파이프라인은 *Name* 및 *InputObject* 매개 변수를 모두 제공합니다.  

###  <a name="ViewDeployShareProp"></a> Windows PowerShell을 사용하여 배포 공유 속성 보기  
 [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet 및 MDTProvider Windows PowerShell 공급자를 사용하여 MDT 배포 공유의 속성을 볼 수 있습니다. 이러한 동일한 속성은 Deployment 워크벤치에서도 볼 수 있습니다.  

 **MDT Windows PowerShell cmdlet을 사용하여 배포 공유 속성을 보려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포가 올바르게 복원되었는지 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브의 목록이 나열됩니다.  

4.  다음 예제와 같이 [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet을 사용하여 배포 공유의 속성을 봅니다.  

    ```  
    Get-ItemProperty "DS002:"  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다. cmdlet은 배포 공유의 속성을 반환합니다.  

###  <a name="ViewListDeployShare"></a> Windows PowerShell을 사용하여 배포 공유 목록 보기  
 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet 및 MDTProvider Windows PowerShell 공급자를 사용하여 MDT 배포 공유의 목록을 볼 수 있습니다. Deployment 워크벤치에서도 동일한 배포 공유 목록을 볼 수 있습니다.  

 **MDT Windows PowerShell cmdlet을 사용하여 배포 공유 목록을 보려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포 목록을 각 배포 공유에 대해 하나씩 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브 목록이 각 배포 공유에 하나씩 나열됩니다.  

###  <a name="UpdateDeployShare"></a> Windows PowerShell을 사용하여 배포 공유 업데이트  
 **Update-MDTDeploymentShare** cmdlet 및 MDTProvider Windows PowerShell 공급자를 사용하여 배포 공유를 업데이트할 수 있습니다. 배포 공유를 업데이트하면 LTI 배포를 시작하는 데 필요한 Windows PE 부팅 이미지(WIM 및 ISO(국제 표준화 기구) 파일)가 만들어집니다. "Deployment 워크벤치에서 배포 공유 업데이트"에서 설명한 대로 Deployment 워크벤치를 사용하여 동일한 프로세스를 수행할 수 있습니다.  

 **Windows PowerShell을 사용하여 배포 공유를 업데이트하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포가 올바르게 복원되었는지 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브의 목록이 나열됩니다.  

4.  다음 예제와 같이 **Update-MDTDeploymentShare** cmdlet을 사용하여 배포 공유를 업데이트합니다.  

    ```  
    Update-MDTDeploymentShare -Path "DS002:" -Force  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

    > [!NOTE]
    >  배포 공유를 업데이트하는 데 시간이 오래 걸릴 수 있습니다. cmdlet의 진행 상태는 Windows PowerShell 콘솔의 위쪽에 표시됩니다.  

     업데이트가 성공하면 cmdlet이 출력 없이 반환됩니다.  

###  <a name="UpdateLinkedDeployShare"></a> Windows PowerShell을 사용하여 연결된 배포 공유 업데이트  
 **Update-MDTLinkedDS** cmdlet 및 MDTProvider Windows PowerShell 공급자를 사용하여 연결된 배포 공유를 업데이트(복제)할 수 있습니다. 연결된 배포 공유를 업데이트하면 원래 배포 공유의 콘텐츠가 연결된 배포 공유에 복제됩니다. "Deployment 워크벤치에서 연결된 배포 공유 복제"에서 설명한 대로 Deployment 워크벤치를 사용하여 동일한 프로세스를 수행할 수 있습니다.  

 **Windows PowerShell을 사용하여 연결된 배포 공유를 업데이트하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포가 올바르게 복원되었는지 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브의 목록이 나열됩니다.  

4.  다음 예제와 같이 **Update-MDTDeploymentShare** cmdlet을 사용하여 배포 공유를 업데이트합니다.  

    ```  
    Update-MDTLinkedDS -Path "DS002:\Linked Deployment Shares\LINKED002"  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

    > [!NOTE]
    >  연결된 배포 공유를 업데이트하는 데 시간이 오래 걸릴 수 있습니다. cmdlet의 진행 상태는 Windows PowerShell 콘솔의 위쪽에 표시됩니다.  

     업데이트가 성공하면 cmdlet이 출력 없이 반환됩니다.  

###  <a name="UpdateDeployMedia"></a> Windows PowerShell을 사용하여 배포 미디어 업데이트  
 **Update-MDTMedia** cmdlet 및 MDTProvider Windows PowerShell 공급자를 사용하여 배포 미디어를 업데이트(생성)할 수 있습니다. 배포 미디어를 업데이트하면 원래 배포 공유의 콘텐츠가 연결된 배포 공유에 복제된 다음, .iso 및 .wim 파일이 생성됩니다. "Deployment 워크벤치에서 미디어 이미지 생성"에서 설명한 대로 Deployment 워크벤치를 사용하여 동일한 프로세스를 수행할 수 있습니다.  

 **Update-MDTMedia** cmdlet이 완료되면 다음 파일이 만들어집니다.  

-   *media_folder* 폴더의 .iso 파일(여기서 *media_folder*는 미디어에 지정한 폴더의 이름임)  

     .iso 파일을 생성하는 옵션은 다음과 같이 구성할 수 있습니다.  

    -   **미디어 속성** 대화 상자의 **일반** 탭에서 **손쉬운 부팅 가능한 ISO 이미지 생성** 확인란을 선택합니다. .iso 파일에서 부팅 가능한 DVD를 만들거나 [VM] (가상 머신)을 시작해야 하는 경우가 아니면 미디어를 생성하는 데 필요한 시간을 줄이기 위해 이 확인란의 선택을 취소합니다.  

    -   [Set-ItemProperty](http://technet.microsoft.com/library/hh849844) cmdlet을 사용하여 동일한 속성을 설정합니다.  

-   *media_folder*\Content\Deploy\Boot 폴더의 WIM 파일(여기서 *media_folder*는 미디어에 지정한 폴더의 이름임)  

 **Windows PowerShell을 사용하여 연결된 배포 공유를 업데이트하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포가 올바르게 복원되었는지 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브의 목록이 나열됩니다.  

4.  다음 예제와 같이 **Update-MDTDeploymentShare** cmdlet을 사용하여 배포 공유를 업데이트합니다.  

    ```  
    Update-MDTLinkedDS -Path "DS002:\Linked Deployment Shares\LINKED002"  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

    > [!NOTE]
    >  연결된 배포 공유를 업데이트하는 데 시간이 오래 걸릴 수 있습니다. cmdlet의 진행 상태는 Windows PowerShell 콘솔의 위쪽에 표시됩니다.  

     업데이트가 성공하면 cmdlet이 출력 없이 반환됩니다.  

###  <a name="ManageItemDeployShare"></a> Windows PowerShell을 사용하여 배포 공유 항목 관리  
 배포 공유에는 운영 체제, 응용 프로그램, 디바이스 드라이버, 운영 체제 패키지 및 작업 순서와 같은 배포를 수행하는 데 사용되는 항목이 포함됩니다. 이러한 항목은 Windows PowerShell의 cmdlet과 MDT와 함께 제공되는 cmdlet을 사용하여 관리할 수 있습니다.  

 Windows PowerShell cmdlet을 사용하여 항목을 직접 조작하는 방법에 대한 자세한 내용은 [직접 항목 조작](http://technet.microsoft.com/library/dd315266.aspx)을 참조하세요. 또한 Windows PowerShell을 사용하여 배포 공유의 폴더 구조를 관리할 수도 있습니다. 자세한 내용은 [Windows PowerShell을 사용하여 배포 공유 폴더 관리](#ManageDeployShareFolder)를 참조하세요.  

####  <a name="ImportItemDeployShare"></a> 배포 공유로 항목 가져오기  
 MDT cmdlet을 사용하여 운영 체제, 응용 프로그램 또는 디바이스 드라이버와 같은 각 형식의 항목을 가져올 수 있습니다. 각 형식의 항목에는 특정 MDT cmdlet가 있습니다. Windows PowerShell을 사용하여 여러 항목을 배포 공유로 가져오려면 [배포 공유 채우기 자동화](#AutomatePopulateDeployShare)를 참조하세요.  

 다음 표에는 항목을 배포 공유로 가져오는 데 사용되는 MDT Windows PowerShell cmdlet 및 각 cmdlet에 대한 간단한 설명이 나와 있습니다. 각 cmdlet을 사용하는 방법의 예제는 각 cmdlet에 해당하는 섹션에서 제공됩니다.  

 |**cmdlet** | **설명** |  
 |-|-|  
 |**Import-MDTApplication** |애플리케이션을 배포 공유로 가져옵니다.|  
 |**Import-MDTDriver** |하나 이상의 디바이스 드라이버를 배포 공유로 가져옵니다.|  
 |**Import-MDTOperatingSystem** |하나 이상의 운영 체제를 배포 공유로 가져옵니다.|  
 |**Import-MDTPackage** |하나 이상의 운영 체제 패키지를 배포 공유로 가져옵니다.|  
 |**Import-MDTTaskSequence** |작업 순서를 배포 공유로 가져옵니다.|  

####  <a name="ViewPropertyDeployShare"></a> 배포 공유 항목의 속성 보기  
 배포 공유의 각 항목에는 서로 다른 속성 집합이 있습니다. [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet을 사용하여 배포 공유에 있는 항목의 속성을 볼 수 있습니다. Deployment 워크벤치에서 속성을 표시하는 것처럼 [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet은 MDTProvider를 사용하여 특정 항목에 대한 속성을 표시합니다.  

 Windows PowerShell을 사용하여 배포 공유에 있는 여러 항목의 속성을 보려면 [배포 공유 채우기 자동화](#AutomatePopulateDeployShare)를 참조하세요.  

 **Windows PowerShell을 사용하여 배포 공유에 있는 항목의 속성을 보려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음 예제와 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포가 올바르게 복원되었는지 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브의 목록이 나열됩니다.  

4.  다음 예제와 같이 [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet을 사용하여 속성을 보려는 항목의 형식에 대한 항목 목록을 반환합니다.  

    ```  
    Get-Item "DS001:\Operating Systems\*" | Format-List  
    ```  

     이전 예제에서 배포 공유에 있는 모든 운영 체제의 목록이 표시됩니다. 출력이 **Format-List** cmdlet에 파이프되어 운영 체제의 긴 이름을 볼 수 있습니다. **Format-List** cmdlet을 사용하는 방법에 대한 자세한 내용은 [Format-List cmdlet 사용](http://technet.microsoft.com/library/ee176830.aspx)을 참조하세요. 동일한 프로세스를 사용하여 다른 형식의 항목(예: 디바이스 드라이버 또는 응용 프로그램)에 대한 목록을 반환할 수 있습니다.  

    > [!TIP]
    >  [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet 대신 **dir** 명령을 사용하여 운영 체제 목록을 볼 수도 있습니다.  

5.  다음 예제와 같이 [Get-ItemProperty](http://technet.microsoft.com/library/hh849851.aspx) cmdlet을 사용하여 이전 단계에서 나열된 항목 중 하나의 속성을 봅니다.  

    ```  
    Get-ItemProperty -Path "DS002:\Operating Systems\Windows 8 in Windows 8 x64 install.wim"  
    ```  

     이 예제에서 *Path* 매개 변수의 값은 항목에 대해 정규화된 Windows PowerShell 경로(이전 단계에서 반환된 파일 이름 포함)입니다. 동일한 프로세스를 사용하여 다른 형식의 항목(예: 디바이스 드라이버 또는 응용 프로그램)에 대한 속성을 볼 수 있습니다.  

####  <a name="RemoveItemDeployShare"></a> 배포 공유에서 항목 제거  
 [Remove-Item](http://technet.microsoft.com/library/hh849765) cmdlet을 사용하여 배포 공유에서 항목을 제거할 수 있습니다. Deployment 워크벤치에서 항목을 제거할 수 있는 것처럼 [Remove-Item](http://technet.microsoft.com/library/hh849765) cmdlet은 MDTProvider를 사용하여 특정 항목을 제거합니다. Windows PowerShell을 사용하여 배포 공유에서 여러 항목을 제거하려면 [배포 공유 채우기 자동화](#AutomatePopulateDeployShare)를 참조하세요.  

> [!NOTE]
>  작업 순서에서 사용하는 항목을 제거하면 작업 순서가 실패합니다. 항목을 제거하기 전에 배포 공유의 다른 항목에서 해당 항목이 참조되지 않는지 확인합니다. 항목이 제거되면 복구할 수 없습니다.  

 **Windows PowerShell을 사용하여 배포 공유에서 항목을 제거하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음 예제와 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포가 올바르게 복원되었는지 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브의 목록이 나열됩니다.  

4.  다음 예제와 같이 [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet을 사용하여 속성을 보려는 항목의 형식에 대한 항목 목록을 반환합니다.  

    ```  
    Get-Item "DS001:\Operating Systems\*" | Format-List  
    ```  

     이전 예제에서 배포 공유에 있는 모든 운영 체제의 목록이 표시됩니다. 출력이 **Format-List** cmdlet에 파이프되어 운영 체제의 긴 이름을 볼 수 있습니다. **Format-List** cmdlet을 사용하는 방법에 대한 자세한 내용은 [Format-List cmdlet 사용](http://technet.microsoft.com/library/ee176830.aspx)을 참조하세요. 동일한 프로세스를 사용하여 다른 형식의 항목(예: 디바이스 드라이버 또는 응용 프로그램)에 대한 목록을 반환할 수 있습니다.  

    > [!TIP]
    >  [Get-Item](http://technet.microsoft.com/library/hh849788) cmdlet 대신 **dir** 명령을 사용하여 운영 체제 목록을 볼 수도 있습니다.  

5.  다음 예제와 같이 [Remove-Item](http://technet.microsoft.com/library/hh849765) cmdlet을 사용하여 이전 단계에서 나열된 항목 중 하나를 제거합니다.  

    ```  
    Remove-Item -Path "DS002:\Operating Systems\Windows 8 in Windows 8 x64 install.wim"  
    ```  

     이 예제에서 *Path* 매개 변수의 값은 항목에 대해 정규화된 Windows PowerShell 경로(이전 단계에서 반환된 파일 이름 포함)입니다.  

     동일한 프로세스를 사용하여 다른 형식의 항목(예: 디바이스 드라이버 또는 응용 프로그램)을 제거할 수 있습니다.  

    > [!NOTE]
    >  작업 순서에서 사용하는 항목을 제거하면 작업 순서가 실패합니다. 항목을 제거하기 전에 배포 공유의 다른 항목에서 해당 항목이 참조되지 않는지 확인합니다.  

###  <a name="AutomatePopulateDeployShare"></a> 배포 공유 채우기 자동화  
 MDT Windows PowerShell cmdlet을 사용하면 개별 항목을 관리할 수 있습니다. 그러나 Windows PowerShell의 스크립팅 기능 중 일부를 사용하여 cmdlet을 통해 배포 공유 채우기를 자동화할 수 있습니다.  

 예를 들어 조직에서 다른 사업부에 여러 배포 공유를 배포해야 하거나, 한 조직에서 다른 조직에 운영 체제 배포 서비스를 제공할 수 있습니다. 이러한 두 가지 예의 경우 조직에서 일관되게 구성된 배포 공유를 만들고 채울 수 있어야 합니다.  

 여러 항목을 관리하는 한 가지 방법은 [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet을 사용하여 배포 공유에서 관리하려는 모든 항목 에 대한 목록이 포함된 CSV(쉼표로 구분된 값) 파일을 사용하는 것입니다.  

 다음은 [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx), [ForEach-Object](http://technet.microsoft.com/library/hh849731) 및 **Import-MDTApplication** cmdlet을 사용하여 .csv 파일의 정보에 따라 애플리케이션 목록을 가져오는 Windows PowerShell 스크립트에서 발췌한 부분입니다.  

```  
$List=Import-CSV "C:\MDT\Import-MDT-Apps.csv"  
ForEach-Object ($App in $List) {  
Import-MDTApplication –path $App.ApplicationFolder -enable "True" –Name $App.DescriptiveName –ShortName $App.Shortname –Version $App.Version –Publisher $App.Publisher –Language $App.Language –CommandLine $App.CommandLine –WorkingDirectory $App.WorkingDirectory –ApplicationSourcePath $App.SourceFolder –DestinationFolder $App.DestinationFolder –Verbose  
}  
```  

 이 예제에서 C:\MDT\Import-MDT-Apps.csv 파일에는 애플리케이션을 가져오는 데 필요한 각 변수에 대한 필드가 포함되어 있습니다. [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet과 함께 사용할 .csv 파일을 만드는 방법에 대한 자세한 내용은 [Import-Csv cmdlet 사용](http://technet.microsoft.com/library/ee176874.aspx)을 참조하세요.  

 다음 단계를 수행하여 배포 공유에 있는 운영 체제, 디바이스 드라이버 및 다른 항목을 동일한 방법으로 가져올 수 있습니다.  

1.  채우려는 각 형식의 배포 공유 항목에 대한 .csv 파일을 만듭니다.  

2.  [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet과 함께 사용할 .csv 파일을 만드는 방법에 대한 자세한 내용은 [Import-Csv cmdlet 사용](http://technet.microsoft.com/library/ee176874.aspx)을 참조하세요.  

3.  배포 공유 채우기 자동화에 사용할 Windows PowerShell 스크립트 파일을 만듭니다.  

     Windows PowerShell 스크립트를 만드는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용한 스크립팅](http://technet.microsoft.com/scriptcenter/powershell.aspx)을 참조하세요.  

4.  배포 공유 항목을 가져오기 전에 배포 공유에 필요한 모든 필수 구성 요소 폴더 구조를 만듭니다.  

     자세한 내용은 [Windows PowerShell을 사용하여 배포 공유 폴더 관리](#ManageDeployShareFolder)를 참조하세요.  

5.  1단계에서 만든 .csv 파일 중 하나에 대한 [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet 줄을 추가합니다.  

     [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet에 대한 자세한 내용은 [Import-Csv cmdlet 사용](http://technet.microsoft.com/library/ee176874.aspx)을 참조하세요.  

6.  이전 단계의 [Import-CSV](http://technet.microsoft.com/library/dd347665.aspx) cmdlet에서 참조된 .csv 파일의 각 항목을 처리하는 [ForEach-Object](http://technet.microsoft.com/library/hh849731) cmdlet 루프를 만듭니다.  

     [ForEach-Object](http://technet.microsoft.com/library/hh849731) cmdlet에 대한 자세한 내용은 [ForEach-Object cmdlet 사용](http://technet.microsoft.com/library/ee176828)을 참조하세요.  

7.  이전 단계에서 만든 [ForEach-Object](http://technet.microsoft.com/library/hh849731) cmdlet 루프 내의 배포 공유 항목을 가져오기 위한 해당 MDT cmdlet을 추가합니다.  

     항목을 배포 공유로 가져오는 데 사용되는 MDT cmdlet에 대한 자세한 내용은 [배포 공유로 항목 가져오기](#ImportItemDeployShare)를 참조하세요.  

###  <a name="ManageDeployShareFolder"></a> Windows PowerShell을 사용하여 배포 공유 폴더 관리  
 **mkdir** 명령과 같은 명령줄 도구를 사용하거나 [New-Item](http://technet.microsoft.com/library/hh849795) cmdlet 및 MDTProvider Windows PowerShell 공급자와 같은 Windows PowerShell cmdlet을 사용하여 배포 공유의 폴더를 관리할 수 있습니다. 배포 공유의 폴더 구조도 Deployment 워크벤치에서 보고 관리할 수 있습니다. Windows PowerShell cmdlet을 사용하여 항목을 직접 조작하는 방법에 대한 자세한 내용은 [직접 항목 조작](http://technet.microsoft.com/library/dd315266.aspx)을 참조하세요.  

#### <a name="create-a-folder-in-a-deployment-share-using-windows-powershell"></a>Windows PowerShell을 사용하여 배포 공유에 폴더 만들기  
 **Windows PowerShell을 사용하여 배포 공유에 폴더를 만들려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포 목록을 각 배포 공유에 대해 하나씩 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브 목록이 각 배포 공유에 하나씩 나열됩니다.  

4.  다음 예제와 같이 **mkdir** 명령을 사용하여 배포 공유의 Operating Systems 폴더에 *Windows_8*이라는 폴더를 만듭니다.  

    ```  
    mkdir "DS002:\Operating Systems\Windows_8"  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

5.  다음 명령을 입력하여 폴더가 올바르게 만들어졌는지 확인합니다.  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Operating Systems 폴더에서 Windows_8 폴더 및 기존의 다른 모든 폴더가 표시됩니다.  

6.  다음 예제와 같이 [New-Item cmdlet 사용](http://technet.microsoft.com/library/ee176914.aspx)에서 설명하는 [New-Item](http://technet.microsoft.com/library/hh849795) cmdlet을 사용하여 배포 공유의 Operating Systems 폴더에 *Windows_7*이라는 폴더를 만듭니다.  

    ```  
    New-Item "DS002:\Operating Systems\Windows_7" -Type directory  
    ```  

     cmdlet에서 폴더가 성공적으로 만들어졌다고 표시합니다.  

7.  다음 명령을 입력하여 폴더가 올바르게 만들어졌는지 확인합니다.  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Operating Systems 폴더에서 Windows_7 폴더 및 기존의 다른 모든 폴더가 표시됩니다.  

#### <a name="delete-a-folder-in-a-deployment-share-using-windows-powershell"></a>Windows PowerShell을 사용하여 배포 공유의 폴더 삭제  
 **Windows PowerShell을 사용하여 배포 공유의 폴더를 삭제하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포 목록을 각 배포 공유에 대해 하나씩 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브 목록이 각 배포 공유에 하나씩 나열됩니다.  

4.  다음 예제와 같이 **mkdir** 명령을 사용하여 배포 공유의 Operating Systems 폴더에서 *Windows_8*이라는 폴더를 삭제(제거)합니다.  

    ```  
    rmdir "DS002:\Operating Systems\Windows_8"  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

5.  다음 명령을 입력하여 폴더가 올바르게 제거되었는지 확인합니다.  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_8 폴더가 더 이상 Operating Systems 폴더의 폴더 목록에 표시되지 않습니다.  

6.  다음 예제와 같이 [Remove-Item](http://technet.microsoft.com/library/hh849765) cmdlet을 사용하여 배포 공유의 Operating Systems 폴더에서 *Windows_7*이라는 폴더를 삭제(제거)합니다.  

    ```  
    Remove-Item "DS002:\Operating Systems\Windows_7"  
    ```  

     cmdlet에서 폴더가 성공적으로 제거되었다고 표시합니다.  

7.  다음 명령을 입력하여 폴더가 올바르게 만들어졌는지 확인합니다.  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_7 폴더가 더 이상 Operating Systems 폴더의 폴더 목록에 표시되지 않습니다.  

#### <a name="rename-a-folder-in-a-deployment-share-using-windows-powershell"></a>Windows PowerShell을 사용하여 배포 공유의 폴더 이름 바꾸기  
 **Windows PowerShell을 사용하여 배포 공유의 폴더 이름을 바꾸려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음과 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포 목록을 각 배포 공유에 대해 하나씩 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브 목록이 각 배포 공유에 하나씩 나열됩니다.  

4.  다음 예제와 같이 **ren** 명령을 사용하여 배포 공유의 Operating Systems 폴더에서 *Windows_8*이라는 폴더의 이름을 *Win_8*로 바꿉니다.  

    ```  
    ren "DS002:\Operating Systems\Windows_8" "Win_8"  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

5.  다음 명령을 입력하여 폴더가 올바르게 제거되었는지 확인합니다.  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_8 폴더의 이름이 *Win_8*로 바뀝니다.  

6.  다음 예제와 같이 [Rename-Item](http://technet.microsoft.com/library/hh849763) cmdlet을 사용하여 배포 공유의 Operating Systems 폴더에서 *Windows_7*이라는 폴더의 이름을 *Win-7*로 바꿉니다.  

    ```  
    Rename-Item "DS002:\Operating Systems\Windows_7" "Win_7"  
    ```  

     cmdlet에서 폴더 이름이 성공적으로 바뀌었다고 표시합니다.  

7.  다음 명령을 입력하여 폴더가 올바르게 만들어졌는지 확인합니다.  

    ```  
    dir "DS002:\Operating Systems"  
    ```  

     Windows_7 폴더의 이름이 *Win_7*로 바뀝니다.  

## <a name="automating-the-application-of-operating-system-service-packs-in-deployment-shares"></a>배포 공유에서 운영 체제 서비스 팩 애플리케이션 자동화  
 운영 체제 서비스 팩은 소프트웨어 수명 주기의 일반적인 부분입니다. 배포 공유의 기존 운영 체제를 이러한 서비스 팩으로 업데이트하여 새로 배포되거나 새로 고친 컴퓨터가 최신 보안 권장 사항 및 구성 설정으로 최신 상태를 유지하도록 합니다.  

 조직에서 각 배포 공유에 여러 운영 체제가 있는 배포 공유가 많은 경우 각 배포 공유의 운영 체제를 서비스 팩과 함께 수동으로 업데이트하는 프로세스에 시간이 많이 걸릴 수 있습니다. 배포 공유에서 운영 체제 서비스 팩의 애플리케이션을 자동화하는 방법은 다음과 같습니다.  

-   [업데이트된 원본 미디어에서 운영 체제 서비스 팩의 응용 프로그램 자동화](#AutomateAppFromUSM)에서 설명한 대로 서비스 팩이 이미 포함되어 있는 업데이트된 원본 콘텐츠(예: Windows 7 SP1 미디어)를 기존 운영 체제가 있는 배포 공유의 폴더에 복사합니다.  

-   [참조 컴퓨터 및 Windows PowerShell을 사용하여 운영 체제 서비스 팩의 응용 프로그램 자동화](#AutomateAppUsingRef)에서 설명한 대로 참조 컴퓨터에 서비스 팩을 적용한 다음, 참조 컴퓨터에서 업데이트된 이미지를 캡처합니다.  

###  <a name="AutomateAppFromUSM"></a> 업데이트된 원본 미디어에서 운영 체제 서비스 팩의 응용 프로그램 자동화  
 Windows 7 SP1이 이미 통합된 DVD가 있는 경우와 같이 서비스 팩이 포함된 원본 미디어가 있는 경우 Windows PowerShell을 사용하여 운영 체제 서비스 팩을 업데이트하는 프로세스를 자동화할 수 있습니다.  

 이 방법에서는 Windows PowerShell을 사용하여 서비스 팩이 있는 운영 체제 원본 미디어가 배포 공유에 서비스 팩이 없는 기존 운영 체제 파일에 복사됩니다.  

 **Windows PowerShell을 사용하여 업데이트 원본 미디어에서 운영 체제 서비스 팩의 응용 프로그램을 자동화하려면**  

1.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

2.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

3.  다음 예제와 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포 목록을 각 배포 공유에 대해 하나씩 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브 목록이 각 배포 공유에 하나씩 나열됩니다.  

4.  다음 예제와 같이 [Get-ChildItem](http://technet.microsoft.com/library/hh849800) 및 [Remove-Item](http://technet.microsoft.com/library/hh849765) cmdlet을 사용하여 배포 공유에서 기존 운영 체제의 폴더를 제거합니다.  

    ```  
    Get-ChildItem “DS002:\Operating Systems\Windows 7” –recurse | Remove-Item –recurse –force  
    ```  

     이 예제에서 *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

5.  다음 예제와 같이 [Copy-Item](http://technet.microsoft.com/library/hh849793) cmdlet을 사용하여 서비스 팩이 통합된 운영 체제 원본 파일의 내용을 복사합니다.  

    ```  
    Copy-Item "E:\*" -Destination "DS002:\Operating Systems\Windows 7"-Recurse -Force  
    ```  

     이 예제에서 운영 체제 원본 파일은 E 드라이브에 있고, *DS002:* 는 3단계에서 반환된 Windows PowerShell 드라이브의 이름입니다.  

6.  **Update-MDTMedia** cmdlet을 사용하여 배포 공유에 따라 모든 MDT 배포 미디어를 업데이트합니다.  

 **Update-MDTMedia** cmdlet을 사용하여 배포 공유에 따라 MDT 배포 미디어를 업데이트하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 배포 미디어 업데이트](#UpdateDeployMedia)를 참조하세요.  

###  <a name="AutomateAppUsingRef"></a> 참조 컴퓨터 및 Windows PowerShell을 사용하여 운영 체제 서비스 팩의 응용 프로그램 자동화  
 Windows 7용 SP1이 아직 Windows 7 이미지와 통합되지 않은 경우와 같이 운영 체제와 아직 통합되지 않은 서비스 팩만 있는 경우 Windows PowerShell을 사용하여 운영 체제 서비스 팩을 업데이트하는 프로세스를 자동화할 수 있습니다.  

 이 방법에서는 서비스 팩 없이 운영 체제를 참조 컴퓨터에 배포합니다. 그런 다음, 서비스 팩을 참조 컴퓨터에 적용합니다. 다음으로, 참조 컴퓨터의 운영 체제 이미지를 캡처합니다. 마지막으로, Windows PowerShell을 사용하여 배포 공유의 운영 체제에 있는 Install.wim 파일에 캡처한 .wim 파일을 복사합니다.  

 **Windows PowerShell을 사용하여 업데이트 원본 미디어에서 운영 체제 서비스 팩의 응용 프로그램을 자동화하려면**  

1.  대상 운영 체제를 참조 컴퓨터에 배포합니다.  

     참조 컴퓨터를 배포하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 다음 리소스를 참조하세요.  

    -   "참조 컴퓨터에 LTI 배포 준비"  

    -   "LTI에서 참조 컴퓨터의 이미지 배포 및 캡처"  

2.  원하는 서비스 팩을 참조 컴퓨터에 설치합니다.  

     서비스 팩을 설치하는 방법에 대한 자세한 내용은 서비스 팩과 함께 제공되는 설명서를 참조하세요.  

3.  **Sysprep 및 캡처** 작업 순서 템플릿에 따라 작업 순서를 만들고 배포하여 참조 컴퓨터의 이미지를 캡처합니다.  

     **Sysprep 및 캡처** 작업 순서 템플릿에 따라 작업 순서를 만드는 방법에 대한 자세한 내용은 "Deployment 워크벤치에서 새 작업 순서 만들기"를 참조하세요.  

4.  [MDT Windows PowerShell 스냅인 로드](#LoadMDTSnapIn)에서 설명한 대로 MDT Windows PowerShell 스냅인을 로드합니다.  

5.  다음 예제와 같이 **Restore-MDTPersistentDrive** cmdlet을 사용하여 MDT 배포 공유 Windows PowerShell 드라이브가 복원되었는지 확인합니다.  

    ```  
    Restore-MDTPersistentDrive -Verbose  
    ```  

    > [!NOTE]
    >  Windows PowerShell 드라이브를 공유하는 MDT 배포가 이미 복원된 경우 cmdlet에서 드라이브를 복원할 수 없음을 나타내는 경고 메시지가 표시됩니다.  

6.  다음 예제와 같이 [Get-PSDrive](http://technet.microsoft.com/library/hh849796) cmdlet을 사용하여 Windows PowerShell 드라이브를 공유하는 MDT 배포 목록을 각 배포 공유에 대해 하나씩 확인합니다.  

    ```  
    Get-PSDrive -PSProvider Microsoft.BDD.PSSnapIn\MDTProvider  
    ```  

     MDTProvider를 사용하여 제공되는 Windows PowerShell 드라이브 목록이 각 배포 공유에 하나씩 나열됩니다.  

7.  다음 예제와 같이 [Copy-Item](http://technet.microsoft.com/library/hh849793) cmdlet을 사용하여 3단계에서 캡처한 .wim 파일을 배포 공유의 운영 체제에 있는 Install.wim 파일에 복사합니다.  

    ```  
    Copy-Item "DS002:\Captures\Win7SP1.wim" -Destination "DS002:\Operating Systems\Windows 7\sources\Install.wim" Force  
    ```  

     이 예제에서 DS002: 공유의 Captures 폴더에 있는 캡처된 운영 체제 이미지 파일(Win7SP1.wim)는 6단계에서 반환된 Windows PowerShell 드라이브의 이름이며, 기존 Windows 7 운영 체제는 *Windows 7*이라는 폴더에 저장됩니다.  

8.  **Update-MDTMedia** cmdlet을 사용하여 배포 공유에 따라 모든 MDT 배포 미디어를 업데이트합니다.  

     **Update-MDTMedia** cmdlet을 사용하여 배포 공유에 따라 MDT 배포 미디어를 업데이트하는 방법에 대한 자세한 내용은 [Windows PowerShell을 사용하여 배포 미디어 업데이트](#UpdateDeployMedia)를 참조하세요.  

## <a name="customizing-deployment-based-on-chassis-type"></a>섀시 종류에 따라 배포 사용자 지정  
 컴퓨터의 섀시 종류에 따라 배포를 사용자 지정할 수 있습니다. 이 스크립트는 CustomSettings.ini 파일에서 처리할 수 있는 지역 변수를 만듭니다. `IsLaptop`, `IsDesktop` 및 `IsServer` 지역 변수는 각각 컴퓨터가 휴대용 컴퓨터, 데스크톱 컴퓨터 또는 서버인지를 나타냅니다.  

> [!NOTE]
>  이전 버전의 Deployment 워크벤치에서 `IsServer` 플래그는 기존 운영 체제가 서버 운영 체제(예: Windows Server 2003 Enterprise Edition)라고 나타내었습니다. 이 플래그의 이름이 `IsServerOS`로 바뀌었습니다.  

 **CustomSettings.ini 파일에서 지역 변수를 구현하려면**  

1.  `[Settings]` 섹션의 `Priority` 줄에서 사용자 지정 섹션을 추가하여 섀시 종류(다음 예제에서 `ByChassisType`이며, 여기서 *Chassis*는 컴퓨터 종류를 나타냄)에 따라 배포를 사용자 지정합니다.  

2.  1단계에서 정의한 사용자 지정 섹션(다음 예제에서 `ByChassisType`이며, 여기서 *Chassis*는 컴퓨터 종류를 나타냄)에 해당하는 사용자 지정 섹션을 만듭니다.  

3.  검색할 각 섀시 종류에 대한 하위 섹션(다음 예제의 `Subsection=Laptop-%IsLaptop%, Subsection=Desktop-%IsDesktop%, Subsection=Server-%IsServer%`)을 정의합니다.  

4.  3단계에서 정의한 각 하위 섹션의 `True` 및 `False` 상태에 대한 하위 섹션(예: 다음 예제의 `[Laptop-True], [Laptop-False], [Desktop-True], [Desktop-False]`)을 만듭니다.  

5.  각 `True` 및 `False` 하위 섹션에서 섀시 종류에 따라 적절한 설정을 추가합니다.  

 **목록 1. CustomSettings.ini 파일에서 섀시 종류에 따라 배포를 사용자 지정하는 예제**  

```  
[Settings]  

Priority=...,ByLaptopType,ByDesktopType,ByServerType  

[ByLaptopType]  
Subsection=Laptop-%IsLaptop%  

[ByDesktopType]  
Subsection=Desktop-%IsDesktop%  

[ByServerType]  
Subsection=Server-%IsServer%  
.  
.  
.  

[Laptop-True]  
.  
.  
.  

[Laptop-False]  
.  
.  
.  

[Desktop-True]  
.  
.  
.  

[Desktop-False]  
.  
.  
.  

[Server-True]  
.  
.  
.  

[Server-False]  
.  
.  
.  
```  

## <a name="deploying-applications-based-on-earlier-application-versions"></a>이전 애플리케이션 버전에 따라 애플리케이션 배포  
 기존 컴퓨터에 운영 체제를 설치할 때 컴퓨터에 설치한 것과 동일한 애플리케이션을 설치하게 되는 경우가 많습니다. 이 경우 MDT 스크립트(특히 ZTIGather.wsf)를 사용하여 별도의 두 가지 정보 원본을 쿼리합니다.  

-   **Configuration Manager 소프트웨어 인벤토리 기능.** Configuration Manager에서 컴퓨터를 마지막으로 인벤토리에 포함할 때 설치된 각 애플리케이션 패키지(이 경우 Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2의 [프로그램 및 기능]에 나열됨)에 대한 레코드가 하나씩 포함됩니다.  

-   **매핑 테이블.** [프로그램 및 기능] 또는 [프로그램 추가/제거] 레코드에서 애플리케이션을 설치한 패키지를 정확하게 지정하지 않아 인벤토리만으로 패키지를 자동으로 선택할 수 없으므로 각 레코드에 설치해야 하는 패키지와 프로그램을 설명합니다.  

 **컴퓨터 관련 응용 프로그램 설치를 동적으로 수행하려면**  

1.  MDT DB의 테이블을 사용하여 특정 패키지를 대상 운영 체제에 나열된 애플리케이션과 연결합니다.  

2.  해당 패키지를 [프로그램 및 기능] 또는 [프로그램 추가/제거]에 나열된 애플리케이션과 연결하는 데이터로 테이블을 채웁니다.

     **테이블을 채우는 SQL 쿼리**  

    ```  
    use [MDTDB]  
    go  
    INSERT INTO [PackageMapping] (ARPName, Packages) VALUES('Office12.0', 'XXX0000F:Install Office 2010 Professional Plus')  
    go  
    ```  

     삽입된 행은 `Office12.0` 입력 항목이 있는 모든 컴퓨터를 Microsoft Office 2010 Professional Plus 패키지와 연결합니다.  

     즉 Microsoft Office 2010 Professional Plus가 현재 2007 Microsoft Office 시스템(Office 12.0)을 실행하는 모든 컴퓨터에 설치됩니다. 다른 패키지에 대해 비슷한 항목을 추가합니다. 입력 항목이 없는 항목은 모두 무시됩니다(패키지가 설치되지 않음).  

3.  새 테이블의 정보와 인벤토리 데이터의 조인을 간소화하는 저장 프로시저를 만듭니다.  

    ```  
    use [MDTDB]  
    go  

    if exists (select * from dbo.sysobjects where id = object_id(N'[dbo].[RetrievePackages]') and OBJECTPROPERTY(id, N'IsProcedure') = 1)  
    drop procedure [dbo].[RetrievePackages]  
    go  

    CREATE PROCEDURE [dbo].[RetrievePackages]  
    @MacAddress CHAR(17)  
    AS  

    SET NOCOUNT ON  

    /* Select and return all the appropriate records based on current inventory */  
    SELECT * FROM PackageMapping  
    WHERE ARPName IN  
    (  
      SELECT ProdID0 FROM CM_DB.dbo.v_GS_ADD_REMOVE_PROGRAMS a, CM_DB.dbo.v_GS_NETWORK_ADAPTER n  
      WHERE a.ResourceID = n.ResourceID AND  
      MACAddress0 = @MacAddress  
    )  
    go  
    ```  

     이전 예제의 저장 프로시저에서는 SQL Server가 MDT DB로 실행되는 컴퓨터에 Configuration Manager 중앙 기본 사이트 데이터베이스가 있다고 가정합니다. 중앙 기본 사이트 데이터베이스가 다른 컴퓨터에 있는 경우 저장 프로시저를 적절하게 수정해야 합니다. 데이터베이스 이름(`CM_DB`)도 업데이트해야 합니다. 또한 Configuration Manager 데이터베이스의 **v_GS_ADD_REMOVE_PROGRAMS** 뷰에 대한 읽기 액세스 권한을 추가 계정에 부여하는 것도 고려해야 합니다.  

4.  데이터베이스 정보를 가리키는 섹션(**Priority** 목록의 `[DynamicPackages]`)의 이름을 지정하여 이 데이터베이스 테이블을 쿼리하도록 CustomSettings.ini 파일을 구성합니다.  

    ```  
    [Settings]  
    …  
    Priority=MacAddress, DefaultGateway, DynamicPackages, Default  
    …  
    ```  

5.  `[DynamicPackages]` 섹션을 만들어 데이터베이스 섹션의 이름을 지정합니다.  

    ```  
    [DynamicPackages]  
    SQLDefault=DB_DynamicPackages  
    ```  

6.  데이터베이스 섹션을 만들어 데이터베이스 정보 및 쿼리 세부 정보를 지정합니다.  

    ```  
    [DB_DynamicPackages]  
    SQLServer=SERVER1  
    Database=MDTDB  
    StoredProcedure=RetrievePackages  
    Parameters=MacAddress  
    SQLShare=Logs  
    Instance=SQLEnterprise2005  
    Port=1433  
    Netlib=DBNMPNTW  
    ```  

     이전 예제에서는 *SERVER1*이라는 이름으로 인스턴스화된 SQL Server가 실행되는 컴퓨터에서 *MDTDB*라는 MDT DB가 쿼리됩니다. 데이터베이스에 3단계에서 만든 `RetrievePackages`라는 저장 프로시저가 포함되어 있습니다.  

 ZTIGather.wsf가 실행되면 `SELECT` SQL(구조적 쿼리 언어) 문이 자동으로 생성되고, **MakeModelQuery** 사용자 지정 키의 값이 쿼리에 매개 변수로 전달됩니다.  

 ```  
 EXECUTE RetrievePackages ?  
 ```  

 **MACAddress** 사용자 지정 키의 실제 값이 해당 "?"로 대체됩니다.  이 쿼리는 2단계에서 입력한 행이 있는 레코드 집합을 반환합니다.  

 가변 개수의 인수는 저장 프로시저에 전달할 수 없습니다. 따라서 컴퓨터에 둘 이상의 MAC 주소가 있는 경우 모든 MAC 주소를 저장 프로시저에 전달할 수 있는 것은 아닙니다. 다른 방법으로 모든 MAC 주소 값을 전달하기 위해 저장 프로시저를 `IN` 절이 있는 `SELECT` 문으로 뷰를 쿼리할 수 있는 뷰로 바꿉니다.  

 여기서 제시한 시나리오에 따라 테이블에 삽입된 `Office12.0` 값(2단계)이 현재 컴퓨터에 있는 경우 한 행(`XXX0000F:Install Office 2010 Professional Plus`)이 반환됩니다. 이는 상태 복원 단계에서 ZTI 프로세스를 통해 XXX0000F:Install Office 2001 Professional Plus 패키지가 설치되었음을 나타냅니다.  

## <a name="fully-automated-lti-deployment-scenario"></a>완전히 자동화된 LTI 배포 시나리오  
 LTI의 주요 목적은 최대한 많은 배포 프로세스를 자동화하는 것입니다. ZTI는 MDT 스크립트와 Windows 배포 서비스를 사용하여 완전한 배포 자동화를 제공하지만, LTI는 인프라를 더 적게 요구하면서 작동하도록 설계되었습니다.  

 표시된 마법사 페이지를 줄이거나 제거하기 위해 LTI 배포 프로세스에서 사용되는 Windows 배포 마법사를 자동화할 수 있습니다. CustomSettings.ini에서 **SkipWizard** 속성을 지정하여 Windows 배포 마법사 전체를 건너뛸 수 있습니다. 마법사 페이지를 개별적으로 건너뛰려면 다음 속성을 사용합니다.  

-   **SkipAdminPassword**  

-   **SkipApplications**  

-   **SkipBDDWelcome**  

-   **SkipBitLocker**  

-   **SkipBitLockerDetails**  

-   **SkipTaskSequence**  

-   **SkipCapture**  

-   **SkipComputerBackup**  

-   **SkipComputerName**  

-   **SkipDomainMembership**  

-   **SkipFinalSummary**  

-   **SkipLocaleSelection**  

-   **SkipPackageDisplay**  

-   **SkipProductKey**  

-   **SkipSummary**  

-   **SkipTimeZone**  

-   **SkipUserData**  

이러한 개별 속성에 대한 자세한 내용은 *Toolkit 참조* MDT 문서에서 해당 속성을 참조하세요.  

건너뛴 마법사 페이지마다 CustomSettings.ini 및 BootStrap.ini 파일의 마법사 페이지를 통해 일반적으로 수집되는 해당 속성의 값을 제공합니다. 이러한 파일에 구성해야 하는 속성에 대한 자세한 내용은 *Toolkit 참조* MDT 문서에서 "건너뛴 배포 마법사 페이지에 대한 속성 제공" 섹션을 참조하세요.  

## <a name="fully-automated-lti-deployment-for-a-refresh-computer-scenario"></a>컴퓨터 새로 고침 시나리오에 대해 완전히 자동화된 LTI 배포  
 다음은 컴퓨터 새로 고침 시나리오에서 모든 Windows 배포 마법사 페이지를 건너뛰는 데 사용되는 CustomSettings.ini 파일을 보여 줍니다. 이 샘플에서는 마법사 페이지를 건너뛸 때 제공하는 속성이 마법사 페이지를 건너뛰는 속성 바로 아래에 있습니다.  

```  
[Settings]  
Priority=Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac /lae  
SkipCapture=YES  
SkipAdminPassword=YES  
SkipProductKey=YES  

DeploymentType=REFRESH  

SkipDomainMembership=YES  
JoinDomain=DomainName  
DomainAdmin=Administrator  
DomainAdminDomain=DomainName  
DomainAdminPassword=a_secure_password  

SkipUserData=yes  
UserDataLocation=AUTO  
UDShare=\\Servername\Sharename\Directory  
UDDir=%ComputerName%  

SkipComputerBackup=YES  
ComputerBackuplocation=AUTO  
BackupShare=\\Servername\Backupsharename  
BackupDir=%ComputerName%  

SkipTaskSequence=YES  
TaskSequenceID=Enterprise  

SkipComputerName=YES  
OSDComputerName=%ComputerName%  

SkipPackageDisplay=YES  
LanguagePacks001={3af4e3ce-8122-41a2-9cf9-892145521660}  
LanguagePacks002={84fc70d4-db4b-40dc-a660-d546a50bf226}  

SkipLocaleSelection=YES  
UILanguage=en-US  
UserLocale=en-CA  
KeyboardLocale=0409:00000409  

SkipTimeZone=YES  
TimeZoneName=China Standard Time  

SkipApplications=YES  
Applications001={a26c6358-8db9-4615-90ff-d4511dc2feff}  
Applications002={7e9d10a0-42ef-4a0a-9ee2-90eb2f4e4b98}  
UserID=Administrator  
UserDomain=DomainName  
UserPassword=P@ssw0rd  

SkipBitLocker=YES  
SkipSummary=YES  
Powerusers001=DomainName\Username  
```  

## <a name="fully-automated-lti-deployment-for-a-new-computer-scenario"></a>새 컴퓨터 시나리오에 대해 완전히 자동화된 LTI 배포  
 다음은 새 컴퓨터 시나리오에서 모든 Windows 배포 마법사 페이지를 건너뛰는 데 사용되는 CustomSettings.ini 파일의 예제입니다. 이 샘플에서는 마법사 페이지를 건너뛸 때 제공하는 속성이 마법사 페이지를 건너뛰는 속성 바로 아래에 있습니다.  

```  
[Settings]  
Priority=Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac /lae  

SkipCapture=YES  
ComputerBackupLocation=\\WDG-MDT-01\Backup$\  
BackupFile=MyCustomImage.wim  

SkipAdminPassword=YES  
SkipProductKey=YES  

SkipDomainMembership=YES  
JoinDomain=WOODGROVEBANK  
DomainAdmin=Administrator  
DomainAdminDomain=WOODGROVEBANK  
DomainAdminPassword=P@ssw0rd  

SkipUserData=Yes  
UserDataLocation=\\WDG-MDT-01\UserData$\Directory\usmtdata  

SkipTaskSequence=YES  
TaskSequenceID=Enterprise  

SkipComputerName=YES  
OSDComputerName=%SerialNumber%  

SkipPackageDisplay=YES  
LanguagePacks001={3af4e3ce-8122-41a2-9cf9-892145521660}  
LanguagePacks002={84fc70d4-db4b-40dc-a660-d546a50bf226}  

SkipLocaleSelection=YES  
UILanguage=en-US  
UserLocale=en-CA  
KeyboardLocale=0409:00000409  

SkipTimeZone=YES  
TimeZoneName=China Standard Time  

SkipApplications=YES  
Applications001={a26c6358-8db9-4615-90ff-d4511dc2feff}  
Applications002={7e9d10a0-42ef-4a0a-9ee2-90eb2f4e4b98}  

SkipBitLocker=YES  
SkipSummary=YES  
Powerusers001=WOODGROVEBANK\PilarA  
CaptureGroups=YES  
SLShare=\\WDG-MDT-01\UserData$\Logs  
Home_page=http://www.microsoft.com/NewComputer  
```  

## <a name="calling-web-services-in-mdt"></a>MDT에서 웹 서비스 호출  
 이전 버전의 MDT에서는 일반적으로 WMI를 사용하여 로컬 컴퓨터에서 CustomSettings.ini 및 데이터베이스를 통해 값을 검색할 수 있는 규칙 처리가 지원되었으므로 배포 중에 각 컴퓨터에서 수행해야 하는 작업을 결정할 수 있었습니다. 또한 SQL 쿼리 및 저장 프로시저 호출을 수행하여 외부 데이터베이스에서 추가 정보를 검색할 수 있었습니다. 해당 접근 방식, 특히 보안 SQL 연결을 수행하는 것과 관련된 어려운 문제가 있었습니다.  

 이 문제를 해결하기 위해 MDT에는 CustomSettings.ini에 정의된 간단한 규칙에 따라 웹 서비스 호출을 수행할 수 있는 기능이 있습니다. 이러한 웹 서비스 요청은 특별한 보안 컨텍스트가 필요하지 않으며 방화벽 구성을 간소화하는 데 필요한 모든 TCP/IP 포트를 사용할 수 있습니다.  

 다음은 특정 웹 서비스를 호출하도록 CustomSettings.ini를 구성하는 방법을 보여 줍니다. 이 시나리오에서 웹 서비스는 인터넷 검색에서 임의로 선택됩니다. 우편 번호를 입력으로 사용하고 지정된 우편 번호에 대한 시/군/구, 시/도, 지역 번호 및 표준 시간대를 문자로 반환합니다.  

```  
[Settings]  
Priority=Default, USZipService  
Properties=USZip, City, State, Zip, Area_Code, Time_Zones   
[Default]  
USZip=98052   
[USZipService]  
WebService=http://www.webservicex.net/uszip.asmx/GetInfoByZIP  
Parameters=USZip  
```  

 이 코드를 실행하면 다음과 비슷한 출력이 생성됩니다.
```  
Added new custom property USZIP  
Added new custom property CITY  
Added new custom property STATE  
Added new custom property ZIP  
Added new custom property AREA_CODE  
Added new custom property TIME_ZONES  
Using from [Settings]: Rule Priority = DEFAULT, USZIPSERVICE  
------ Processing the [DEFAULT] section ------  
Property USZIP is now = 98052  
Using from [DEFAULT]: USZIP = 98052  
------ Processing the [USZIPSERVICE] section ------  
Using COMMAND LINE ARG: Ini file = CustomSettings.ini  
CHECKING the [USZIPSERVICE] section  
About to execute web service call to http://www.webservicex.net/uszip.asmx/GetInfoByZIP: USZip=98052  
Response from web service: 200 OK  
Successfully executed the web service.  
Property CITY is now = Redmond  
Obtained CITY value from web service:  CITY = Redmond  
Property STATE is now = WA  
Obtained STATE value from web service:  STATE = WA  
Property ZIP is now = 98052  
Obtained ZIP value from web service:  ZIP = 98052  
Property AREA_CODE is now = 425  
Obtained AREA_CODE value from web service:  AREA_CODE = 425  
------ Done processing CustomSettings.ini ------  
```  

 웹 서비스를 실행할 때 주의해야 할 몇 가지 사소한 문제가 있습니다.  

-   프록시 서버와 관련된 어떤 특별한 작업도 수행하지 않습니다. 익명 프록시가 있으면 이 프록시를 사용하지만, 프록시를 인증하는 경우 문제가 발생할 수 있습니다. 대부분의 경우 웹 서비스는 호출되지 않습니다.  

-   CustomSettings.ini 또는 ZTIGather.xml은 데이터베이스 쿼리 또는 다른 규칙과 마찬가지로 웹 서비스 호출의 결과로 반환되는 XML 태그에 정의된 속성을 검색합니다. 그러나 XML 검색은 대/소문자를 구분합니다. 다행히도 여기서 설명하는 웹 서비스는 ZTIGather.xml에 필요한 모든 대문자 속성 이름을 반환합니다. 소문자 또는 대/소문자가 혼합된 입력 항목을 다시 매핑하여 이 문제를 해결할 수 있습니다.  

-   웹 서비스에 대한 `POST` 요청이 권장되므로 웹 서비스 호출에서 `POST`를 지원할 수 있어야 합니다.  

## <a name="connecting-to-network-resources"></a>네트워크 리소스에 연결  
 LTI 및 ZTI 배포 프로세스 중에 배포 공유를 호스팅하는 서버와 다른 서버에서 네트워크 리소스에 액세스해야 할 수 있습니다. 다른 서버에서 인증을 받아야 공유 폴더 또는 서비스에 액세스할 수 있습니다. 예를 들어 MDT 스크립트에서 사용하는 배포 공유를 호스팅하는 서버가 아닌 다른 서버의 공유 폴더에서 애플리케이션을 설치할 수 있습니다.  

> [!NOTE]
>  배포 공유를 호스팅하는 서버가 아닌 다른 서버에서 호스팅되는 SQL Server 데이터베이스를 쿼리하려면, *Toolkit 참조* MDT 문서에서 **Database**, **DBID**, **DBPwd**, **Instance**, **NetLib**, **Order**, **Parameters**, **ParameterCondition**, **SQLServer**, **SQLShare** 및 **Table** 속성을 참조하세요.  

 ZTIConnect.wsf 스크립트를 사용하면 다른 서버에 연결하고 해당 서버의 리소스에 액세스할 수 있습니다. ZTIConnect.wsf 스크립트의 구문은 다음과 같습니다. 여기서 *unc_path*는 서버에 연결하기 위한 UNC(범용 명명 규칙) 경로입니다.  

```  
Cscript.exe “%SCRIPTROOT%\ZTIConnect.wsf” /uncpath:unc_path  
```  

 대부분의 경우 ZTIConnect.wsf 스크립트를 작업 시퀀서 작업으로 실행합니다. 배포 공유를 호스팅하는 서버가 아닌 다른 서버에 대한 액세스가 필요한 작업을 수행하기 전에 ZTIConnect.wsf 스크립트를 실행합니다.  

 **빌드의 작업 순서에 ZTIConnect.wsf 스크립트를 작업으로 추가하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  세부 정보 창에서 ***task_sequence***를 클릭합니다. 여기서 *task_sequence*는 수정할 작업 순서입니다.  

4.  [작업] 창에서 **속성**을 클릭합니다.  

5.  [작업 순서] 탭을 클릭하고, **group**(여기서 *group*은 ZTIConnec.wsf 스크립트를 실행할 그룹임)으로 이동한 다음, **추가**를 클릭합니다. **일반**을 클릭한 다음, **명령줄 실행**을 클릭합니다.  

    > [!NOTE]
    >  대상 서버의 리소스에 액세스해야 하는 작업을 추가하기 전에 작업을 추가합니다.  

6.  다음 정보를 사용하여 새 작업의 **속성** 탭을 완성합니다.

    |**입력란** |**수행할 작업** |  
    |-|-|  
    |**Name** |**server에 연결**에 입력합니다. 여기서 server는 연결할 서버의 이름입니다.|  
    |**설명** |연결을 설정해야 하는 이유를 설명하는 텍스트를 입력합니다.|  
    |**명령** |**Cscript.exe “%SCRIPTROOT%\ZTIConnect.wsf” /uncpath:unc_path**를 입력합니다. 여기서 *unc_path*는 서버의 공유 폴더에 대한 UNC 경로입니다.|  

7.  다음 정보를 사용하여 새 작업의 **옵션** 탭을 완성합니다. 지정하지 않으면 기본값을 적용한 다음, **확인**을 클릭합니다.  

    |**입력란** |**수행할 작업** |  
    |-|-|  
    |**성공 코드** |**0 3010**을 입력합니다. (성공적으로 완료되면 ZTIConnect.wsf 스크립트에서 이러한 코드를 반환합니다.)|  
    |**조건 목록 상자** |필요한 조건을 모두 추가합니다. (대부분의 경우 이 작업에는 조건이 필요하지 않습니다.)|  

 ZTIConnect.wsf 스크립트를 실행할 작업을 추가한 후 후속 작업에서 ZTIConnect.wsf 스크립트의 **/uncpath** 옵션에 지정된 서버의 네트워크 리소스에 액세스할 수 있습니다.  

## <a name="deploying-the-correct-device-drivers-to-computers-with-the-same-hardware-devices-but-different-make-and-model"></a>동일한 하드웨어 디바이스가 있지만 제조업체와 모델이 다른 컴퓨터에 적절한 디바이스 드라이버 배포  
 모델 번호와 이름의 변형은 드라이버 집합에서 거의 차이가 없을 수 있습니다. 모델 번호와 이름의 이러한 변형은 지정된 모델에 대해 여러 데이터베이스 항목을 만드는 데 걸리는 시간을 불필요하게 늘릴 수 있습니다. 다음 절차에서는 모델 번호의 부분 문자열을 반환하는 사용자 종료 함수 호출을 사용하여 새 속성을 정의하는 방법을 보여 줍니다.  

 **모델 별칭을 만들려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **속성** 대화 상자에서 **규칙** 탭을 클릭합니다.  

5.  MDT DB의 Make 및 Model 섹션에서 하드웨어 종류에 대한 별칭을 만듭니다. 모델 이름의 "("(여는 괄호)에서 모델 유형을 자릅니다. 예를 들어 *HP DL360 (G112)* 은 *HP DL360*이 됩니다.  

6.  **ModelAlias** 사용자 지정 변수를 각 섹션에 추가합니다.  

7.  `[SetModel]` 섹션을 새로 만듭니다.  

8.  `[SetModel]` 섹션을 `[Settings]` 섹션의 **Priority** 설정에 추가합니다.  

9. "("에서 모델 이름을 자를 사용자 종료 스크립트를 참조하는 줄을 `ModelAlias` 섹션에 추가합니다.  

10. **ModelAlias**가 **Model**과 동일한 **MMApplications** 데이터베이스 조회를 만듭니다.  

11. 사용자 종료 스크립트를 만들고 이를 CustomSettings.ini 파일과 동일한 디렉터리에 배치하여 모델 이름을 자릅니다.  

    다음은 각각 CustomSettings.ini 및 사용자 종료 스크립트를 보여 줍니다.  

     **CustomSettings.ini**:  

    ```  
    [Settings]   
    Priority=SetModel, MMApplications, Default   
    Properties= ModelAlias   
    [SetModel]   
    ModelAlias=#SetModelAlias()#   
    Userexit=Userexit.vbs   
    [MMApplications]   
    SQLServer=Server1  
    Database=MDTDB   
    Netlib=DBNMPNTW   
    SQLShare=logs   
    Table= MakeModelSettings    
    Parameters=Make, ModelAlias   
    ModelAlias=Model   
    Order=Sequence  
    ```  

     **사용자 종료 스크립트**:  

    ```  
    Function UserExit(sType, sWhen, sDetail, bSkip)   
      UserExit = Success   
    End Function   

    Function SetModelAlias()   
      If Instr(oEnvironment.Item("Model"), "(") <> 0 Then   
        SetModelAlias = Left(oEnvironment.Item("Model"), _  
                          Instr(oEnvironment.Item("Model"), _  
                            "(") - 1)   
        oLogging.CreateEntry "USEREXIT – " & _  
          "ModelAlias has been set to " & SetModelAlias, _  
          LogTypeInfo  
      Else   
        SetModelAlias = oEnvironment.Item("Model")   
        oLogging.CreateEntry " USEREXIT - " & _  
          "ModelAlias has not been changed.", LogTypeInfo   
      End if   
    End Function  
    ```  

## <a name="configuring-conditional-task-sequence-steps"></a>조건부 작업 순서 단계 구성  
 일부 시나리오에서는 정의된 기준에 따라 조건부로 작업 순서 단계를 실행하는 것이 좋습니다. 이러한 조건의 조합을 추가하여 작업 순서 단계를 실행해야 하는지 여부를 결정할 수 있습니다. 예를 들어 작업 순서 변수 값과 레지스트리 설정 값을 사용하여 작업 순서 단계를 실행해야 하는지 여부를 결정합니다.  

 MDT를 사용하여 다음 기준에 따라 조건부로 작업 순서를 실행합니다.  

-   하나 이상의 **IF** 문  

-   작업 순서 변수  

-   대상 운영 체제의 버전  

-   WMI 쿼리의 부울 결과  

-   레지스트리 설정  

-   대상 컴퓨터에 설치된 소프트웨어  

-   폴더의 속성  

-   파일의 속성  

### <a name="configuring-a-conditional-task-sequence-step"></a>조건부 작업 순서 단계 구성  
 조건부 작업 순서 단계는 Deployment 워크벤치에 있는 작업 순서 단계에 대한 **옵션** 탭에서 구성됩니다. 작업 순서 단계에 하나 이상의 조건을 추가하여 단계를 실행하거나 실행하지 않을 적절한 조건을 만들 수 있습니다.  

> [!NOTE]
>  모든 조건부 작업 순서 단계에는 하나 이상의 **IF** 문이 필요합니다.  

 **작업 순서 단계에 대한 옵션 탭을 보려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  세부 정보 창에서 **task_sequence**를 클릭합니다. 여기서 *task_sequence*는 구성할 작업 순서의 이름입니다.  

4.  [작업] 창에서 **속성**을 클릭합니다.  

5.  ***task_sequence*** **속성** 대화 상자의 **작업 순서** 탭에서 ***step***(여기서 *step*은 구성할 작업 순서 단계의 이름임)을 클릭한 다음, **옵션** 탭을 클릭합니다.  

 작업 순서 단계의 **옵션** 탭에서 다음 작업을 수행합니다.  

-   **추가** 작업 순서 단계에 조건을 추가하려면 이 단추를 클릭합니다.  

-   **제거** 작업 순서 단계에서 기존 조건을 제거하려면 이 단추를 클릭합니다.  

-   **편집** 작업 순서 단계에서 기존 조건을 수정하려면 이 단추를 클릭합니다.  

### <a name="if-statements-in-conditions"></a>조건의 IF 문  
 모든 작업 순서 조건에는 하나 이상의 **IF** 문이 포함됩니다. **IF** 문은 조건부 작업 순서 단계를 만들기 위한 기초입니다. 작업 순서 단계 조건에는 하나의 **IF** 문만 포함될 수 있지만, 최상위 **IF** 문 아래에 여러 개의 **IF** 문을 중첩하여 더 복잡한 조건을 만들 수 있습니다.  

 **IF** 문은 다음 표에 나열된 조건을 기반으로 할 수 있으며, 이러한 조건은 **IF 문 속성** 대화 상자에서 구성됩니다.  

 |**조건** |**작업 순서를 실행하기 위해 이 옵션을 선택하게 되는 경우** |  
 |-|-|  
 |**모든 조건** |이 **IF** 문 아래의 모든 조건이 true여야 합니다.|  
 |**특정 조건** |이 **IF** 문 아래의 특정 조건이 true여야 합니다.|  
 |**없음** |이 **IF** 문 아래에서 true인 조건이 없습니다.|  

 조건에 다른 기준(예: 작업 순서 변수 또는 레지스트리 설정 값)을 추가하여 작업 순서 단계를 실행하기 위한 조건을 완성합니다.  

 **IF 문 조건을 작업 순서 단계에 추가하려면**  

1.  ***step*** **옵션** 탭(여기서 *step*은 구성할 작업 순서 단계의 이름임)에서 **추가**를 클릭한 다음, **If 문**을 클릭합니다.  

2.  **If 문 속성** 대화 상자에서 **condition**(여기서 *condition*은 이전 표에 나열된 조건 중 하나임)을 클릭한 다음, **확인**을 클릭합니다.  

### <a name="task-sequence-variables-in-conditions"></a>조건의 작업 순서 변수  
 **작업 순서 변수** 조건을 사용하여 **작업 순서 변수 설정** 작업 또는 작업 순서의 모든 작업에서 만들어진 작업 순서 변수를 평가합니다. 예를 들어 도메인의 일부인 Windows XP 클라이언트 컴퓨터와 작업 그룹에 속한 Windows XP 클라이언트 컴퓨터가 있는 네트워크를 가정해 보겠습니다. 현재 도메인 정책에 따라 모든 사용자 설정이 네트워크에 저장되므로 도메인에 속하지 않은 컴퓨터, 즉 작업 그룹에 속한 컴퓨터에 대해서만 사용자 설정을 저장해야 할 수도 있습니다. 이 경우 작업 그룹의 컴퓨터를 대상으로 하는 **사용자 파일 및 설정 캡처** 작업에 조건을 추가합니다.  

 **작업 순서 변수를 기반으로 하는 조건을 추가하려면**  

1.  ***step*** **옵션** 탭(여기서 *step*은 구성할 작업 순서 단계의 이름임)에서 **조건 추가**를 클릭한 다음, **작업 순서 변수**를 클릭합니다.  

2.  **작업 순서 변수** 조건 대화 상자의 **변수** 상자에서 **OSDJoinType**을 입력합니다.  

    > [!NOTE]
    >  이 변수는 도메인 조인 컴퓨터에 대해 **0**으로 , 작업 그룹에 대해 **1**로 설정합니다.  

3.  **조건** 상자에서 **같음**을 클릭합니다.  

4.  **값** 상자에서 **1**을 입력한 다음, **확인**을 클릭합니다.  

### <a name="operating-system-version-in-conditions"></a>조건의 운영 체제 버전  
 **운영 체제 버전** 조건을 사용하여 대상 컴퓨터 또는 기존 클라이언트의 기존 운영 체제 버전을 확인합니다(이미지 캡처 시). 예를 들어 Windows Server 2003에서 Windows Server 2008로 업그레이드할 여러 서버가 있는 네트워크를 가정해 보겠습니다. 네트워크 설정은 Windows Server 2003을 실행하는 서버에만 복사하여 적용해야 합니다. 다른 모든 서버에는 Windows Server 2008에서 사용하는 기본 네트워크 설정이 있습니다.  

 **운영 체제 버전을 기반으로 하는 조건을 추가하려면**  

1.  작업 순서 편집기에서 **네트워크 설정 캡처** 작업을 클릭합니다.  

2.  **조건 추가**를 클릭한 다음, **운영 체제 버전**을 클릭합니다.  

3.  **아키텍처** 상자에서 관련 서버를 클릭합니다. 이 예에서는 **x86**을 클릭합니다.  

4.  **운영 체제** 상자에서 조건을 설정할 운영 체제 및 버전을 클릭합니다. 이 예에서는 **x86 Windows 2003**을 클릭합니다.  

5.  **조건** 상자에서 관련 조건을 클릭한 다음, **확인**을 클릭합니다.  

### <a name="file-properties-in-conditions"></a>조건의 파일 속성  
 지정된 파일의 버전 및/또는 타임스탬프를 확인하는 **파일 속성** 조건을 사용하여 작업 또는 작업 그룹을 실행할지 여부를 결정합니다. 이 예에서 프로덕션 환경에는 네트워크에 추가되는 모든 새 서버에 대해 지속적으로 업데이트되고 사용되는 Windows Server 2003 이미지가 포함되어 있습니다. 환경의 모든 서버 컴퓨터는 DAO(디지털 액세스 개체) API(애플리케이션 프로그래밍 인터페이스) 버전 3.60.6815가 필요한 사용자 지정 애플리케이션을 실행합니다.  

 기존 서버가 모두 제대로 작동하고 있습니다. 그러나 이미지가 있는 네트워크에 새로 추가된 각 서버는 애플리케이션을 실행할 수 없습니다. 다른 그룹에서 이미지를 유지 관리하고 업데이트하기 때문에 이미지와 함께 배포된 기존 버전의 DAO가 올바르지 않으면 배포 작업 순서를 변경하여 관련 버전의 DAO를 설치해야 합니다.  

 **Configuration Manager 2007 R3의 작업 순서 단계에 파일 속성 조건을 추가하려면**  

1.  Configuration Manager 2007 R3에서 DAO 3.60.6815를 설치할 패키지를 만듭니다. *InstallDAO*라는 프로그램으로 이 *DAO* 패키지를 호출합니다. 패키지를 만드는 방법에 대한 자세한 내용은 [패키지를 만드는 방법](http://technet.microsoft.com/library/bb693627.aspx)을 참조하세요.  

2.  DAO 패키지를 배포하는 **소프트웨어 설치** 단계를 만듭니다.  

3.  2단계에서 만든 **소프트웨어 설치** 작업 순서 단계를 클릭한 다음, **옵션** 탭을 클릭합니다.  

4.  **조건 추가**를 클릭한 다음, **파일 속성**을 클릭합니다.  

5.  **경로** 상자에서 **C:\Program Files\Microsoft Shared\DAO\dao360.dll**을 입력합니다.  

6.  **버전 확인** 확인란을 선택한 다음, 조건에 대해 **같지 않음**을 클릭합니다.  

7.  **버전** 상자에서 **3.60.6815**를 입력합니다.  

8.  이 경우 **타임스탬프 확인** 확인란의 선택을 취소한 다음, **확인**을 클릭합니다.  

### <a name="folder-properties-in-conditions"></a>조건의 폴더 속성  
 지정된 폴더의 타임스탬프를 확인하는 **폴더 속성** 조건을 사용하여 작업 또는 작업 그룹을 실행할지 여부를 결정합니다. 예를 들어 내부적으로 개발된 애플리케이션이 Windows 8을 사용하도록 업데이트되는 상황을 가정해 보겠습니다. 그러나 네트워크의 모든 컴퓨터에 최신 버전의 애플리케이션이 설치되어 있는 것은 아니며, 먼저 데이터 변환 프로세스를 수행한 후에 애플리케이션을 업그레이드해야 합니다.  

 애플리케이션이 설치된 폴더의 타임스탬프가 2007년 12월 31일 또는 그 이전인 경우, 대상 컴퓨터는 호환되지 않는 버전의 애플리케이션을 실행하고 있으며 대상 컴퓨터에서 데이터 변환 프로세스를 실행해야 합니다. 작업 순서 단계를 조건부로 실행하여 이전 버전의 애플리케이션이 있는 컴퓨터에서 데이터 변환 프로세스를 실행합니다.  

 **작업 순서 단계에 폴더 속성 조건을 추가하려면**  

1.  Configuration Manager 콘솔 또는 Deployment 워크벤치의 작업 순서 편집기에서 ***task_sequence***를 편집합니다. 여기서 *task_sequence*는 편집하려는 작업 순서입니다.  

2.  데이터 변환 프로세스를 수행하는 **명령줄** 작업을 만듭니다.  

3.  1단계에서 만든 작업을 클릭합니다.  

4.  **조건 추가**를 클릭한 다음, **폴더 속성**을 클릭합니다.  

5.  **경로** 상자에서 응용 프로그램이 있는 폴더의 경로를 입력합니다.  

6.  **타임스탬프 확인** 확인란을 선택합니다.  

7.  조건에 대해 **작거나 같음**을 클릭합니다.  

8.  **날짜** 상자에서 **12/31/2007**을 클릭합니다.  

9. **시간** 상자에서 **12:00:00 AM**을 클릭한 다음, **확인**을 클릭합니다.  

### <a name="registry-settings-in-conditions"></a>조건의 레지스트리 설정  
 **레지스트리 설정** 조건을 사용하여 레지스트리의 키와 값 및 레지스트리 값에 저장된 해당 데이터가 있는지 확인합니다. 예를 들어 작은 컴퓨터 집합에서 현재 사용되는 애플리케이션을 Windows 8에서 실행할 수 없고 현재 Windows XP를 실행하는 컴퓨터를 업그레이드하기 위한 Windows 8 배포가 준비되어 있는 경우를 가정해 보겠습니다. 호환되지 않는 애플리케이션에 대한 항목을 레지스트리에서 확인하고 이 항목이 있는 경우 해당 컴퓨터에 대한 배포 프로세스를 중단하는 조건을 순서의 첫 번째 작업에 만듭니다.  

 **작업 순서 단계에 레지스트리 설정 조건을 추가하려면**  

1.  Configuration Manager 콘솔 또는 Deployment 워크벤치의 작업 순서 편집기에서 ***task_sequence***를 편집합니다. 여기서 *task_sequence*는 Windows 8을 배포하는 작업 순서입니다.  

2.  순서의 첫 번째 작업을 클릭한 다음, **옵션** 탭을 클릭합니다.  

3.  **조건 추가**를 클릭한 다음, **레지스트리 설정**을 클릭합니다.  

4.  **루트 키** 목록에서 **HKEY_LOCAL_MACHINE**을 클릭합니다.  

5.  **키** 상자에서 **SOFTWARE\WOODGROVE**를 입력합니다.  

6.  조건에 대해 **없음**을 클릭합니다. 이 경우 작업이 실행되고 키가 없는 경우에만 순서가 계속됩니다.  

7.  값 이름이 **값 이름** 상자에 입력되어 있는 경우 필요에 따라 조건에서 값이 있는지 여부를 확인할 수 있습니다.  

8.  **있음/없음** 이외의 조건이 사용된 경우 값과 값 형식을 지정합니다.  

9. **확인**을 클릭합니다.  

### <a name="wmi-queries-in-conditions"></a>조건의 WMI 쿼리  
 WMI 쿼리를 실행하는 **WMI 쿼리** 조건을 사용합니다. 쿼리에서 하나 이상의 결과가 반환되면 조건이 True로 평가됩니다. 예를 들어 배포 팀에서 지정된 모델인 Dell 1950의 모든 서버 운영 체제를 업그레이드해야 한다고 가정해 보겠습니다. WMI 쿼리를 사용하여 각 컴퓨터의 모델을 확인하고 적합한 모델이 있는 경우에만 배포를 진행할 수 있습니다.  

 **작업 순서 단계에 WMI 쿼리 조건을 추가하려면**  

1.  Configuration Manager 콘솔 또는 Deployment 워크벤치의 작업 순서 편집기에서 ***task_sequence***를 편집합니다. 여기서 *task_sequence*는 서버를 업그레이드하는 작업 순서입니다.  

2.  순서의 첫 번째 작업을 클릭한 다음, **옵션** 탭을 클릭합니다.  

3.  **조건 추가**를 클릭한 다음, **WMI 쿼리**를 클릭합니다.  

4.  **WMI 네임스페이스** 상자에서 **root\cimv2**를 입력합니다.  

5.  **WQL 쿼리** 상자에서 **Select \* From Win32_ComputerSystem WHERE Model LIKE "%Dell%%1950%"** 를 입력합니다. **확인**을 클릭합니다.  

### <a name="installed-software-in-conditions"></a>조건의 설치된 소프트웨어  
 **설치된 소프트웨어** 조건을 사용하여 특정 소프트웨어가 현재 대상 컴퓨터에 설치되어 있는지 확인합니다. 이 조건을 사용하여 MSI(Microsoft Installer) 파일을 사용하여 설치된 소프트웨어만 평가할 수 있습니다. 예를 들어 Microsoft SQL Server 2012를 실행하는 서버를 제외한 모든 서버의 운영 체제를 업그레이드한다고 가정해 보겠습니다.  

 **작업 순서 단계에 설치된 소프트웨어 조건을 추가하려면**  

1.  Configuration Manager 콘솔 또는 Deployment 워크벤치의 작업 순서 편집기에서 ***task_sequence***를 편집합니다. 여기서 *task_sequence*는 서버를 업그레이드하는 작업 순서입니다.  

2.  순서의 첫 번째 작업을 클릭한 다음, **옵션** 탭을 클릭합니다.  

3.  **조건 추가**를 클릭한 다음, **설치된 소프트웨어**를 클릭합니다.  

4.  **찾아보기**를 클릭한 다음, SQL Server 2012에 대한 MSI 파일을 클릭합니다.  

5.  SQL Server 2012가 있고 다른 버전이 아닌 컴퓨터만 이 쿼리에서 검색해야 하는 대상 컴퓨터가 되도록 **이 특정 제품 일치** 확인란을 선택합니다.  

6.  **확인**을 클릭합니다.  

### <a name="complex-conditions"></a>복합 조건  
 **IF** 문을 사용하여 여러 조건을 그룹화하여 복합 조건을 만들 수 있습니다. 예를 들어 Windows Server 2003 또는 Windows Server 2008을 실행하는 Contoso 1950 컴퓨터에 대해서만 특정 단계를 실행해야 한다고 가정해 보겠습니다. 프로그래밍 방식의 **IF** 문으로 작성하면 다음과 비슷합니다.  

```  
IF ((Computer Model IS “Contoso 1950”) AND (operating system=2003 OR operating system=2008))  
```  

 **복합 조건을 추가하려면**  

1.  Configuration Manager 콘솔 또는 Deployment 워크벤치의 작업 순서 편집기에서 ***task_sequence***를 편집합니다. 여기서 *task_sequence*는 서버를 업그레이드하는 작업 순서입니다.  

2.  조건을 추가할 작업 순서 단계를 클릭한 다음, **옵션** 탭을 클릭합니다.  

3.  **조건 추가**를 클릭하고, **If 문**을 클릭한 다음, **모든 조건**을 클릭합니다. **확인**을 클릭합니다.  

4.  조건문을 클릭하고, **조건 추가**를 클릭한 다음, **WMI 쿼리**를 클릭합니다.  

5.  **root\cimv2**가 WMI 네임스페이스로 지정되었는지 확인한 다음, **WQL 쿼리** 상자에서 **SELECT \* FROM Win32_ComputerSystem WHERE ComputerModel LIKE "%Contoso%1950%"** 를 입력합니다. **확인**을 클릭합니다.  

6.  **IF** 문을 클릭한 다음, **조건 추가**를 클릭합니다. **If 문**을 클릭한 다음, **특정 조건**을 클릭합니다. **확인**을 클릭합니다.  

7.  두 번째 **IF** 문을 클릭합니다. **조건 추가**를 클릭한 다음, **운영 체제 버전**을 클릭합니다.  

8.  **아키텍처** 상자에서 서버의 아키텍처를 클릭합니다. 이 예에서는 **x86**을 클릭합니다.  

9. **운영 체제** 상자에서 운영 체제 및 버전을 클릭합니다. 이 예에서는 **x86 Windows 2003 원본 릴리스**를 클릭합니다. **확인**을 클릭합니다.  

10. 두 번째 **IF** 문을 클릭합니다. **조건 추가**를 클릭한 다음, **운영 체제 버전**을 클릭합니다.  

11. **아키텍처** 상자에서 서버의 아키텍처를 클릭합니다. 이 예에서는 **x86**을 클릭합니다.  

12. **운영 체제** 상자에서 운영 체제 및 버전을 클릭합니다. 이 예에서는 **x86 Windows 2008 원본 릴리스**를 클릭합니다. **확인**을 클릭합니다.  

## <a name="creating-a-highly-scalable-lti-deployment-infrastructure"></a>확장성 있는 LTI 배포 인프라 만들기  
 이 시나리오에서는 배포 인프라에 전자 소프트웨어 배포를 활용할 수 없으므로 MDT를 사용하여 완전히 자동화된 LTI 배포 인프라를 구축합니다. 확장성 있는 LTI 인프라는 SQL Server, Windows 배포 서비스 및 Windows Server 2003 DFS-R(분산 파일 시스템 복제) 기술을 사용합니다.  

 LTI 인프라의 크기를 조정하려면 다음을 수행합니다.  

-   [적절한 인프라가 있는지 확인하는 방법](#EnsureInfrastructure)에서 설명한 대로 적절한 인프라가 있는지 확인합니다.  

-   [MDT에 콘텐츠 추가](#AddContent)에서 설명한 대로 MDT에 콘텐츠를 추가합니다.  

-   [Windows 배포 서비스 준비](#PrepareDeployment)에서 설명한 대로 Windows 배포 서비스를 준비합니다.  

-   [분산 파일 시스템 복제 구성](#ConfigureFileReplication)에서 설명한 대로 DFS-R을 구성합니다.  

-   [SQL Server 복제 준비](#PrepareSQLReplication)에서 설명한 대로 SQL Server 복제를 준비합니다.  

-   [SQL Server 복제 구성](#ConfigureSQLReplication)에서 설명한 대로 SQL Server 복제를 구성합니다.  

 이 시나리오에서는 이 문서의 시작 부분에서 설명한 대로 MDT가 마스터 배포 서버에 구성되어 있고 MDT DB 구성이 이미 완료되었다고 가정합니다.  

###  <a name="EnsureInfrastructure"></a> 적절한 인프라가 있는지 확인  
 확장성 있는 LTI 배포 인프라는 콘텐츠 복제에 허브 및 스포크 토폴로지를 사용합니다. 따라서 먼저 마스터 배포 서버의 역할을 수행할 프로덕션 환경에 배포 서버를 지정합니다.  다음은 마스터 배포 서버에 대한 필수 구성 요소를 나열한 목록입니다.  

 |**필수 구성 요소** |**용도/설명** |  
 |-|-|  
 |Windows Server 2003 R2|DFS-R을 지원하는 데 필요합니다.|  
 |MDT |배포 공유의 마스터 복사본이 포함되어 있습니다.|  
 |SQL Server 2005|MDT DB의 복제를 허용하려면 정식 버전이어야 합니다.|  
 |DFS-R |배포 공유를 복제하는 데 필요합니다.|  
 |Windows 배포 서비스 |네트워크 PXE 기반 설치를 시작할 수 있도록 하는 데 필요합니다.|  

 마스터 배포 서버를 선택한 경우 LTI 배포를 지원하기 위해 각 사이트에 추가 서버를 프로비전합니다.  다음은 자식 배포 서버에 대한 필수 구성 요소를 나열한 목록입니다.  

 |**필수 구성 요소** |**용도/설명** |  
 |-|-|  
 |Windows Server 2003 R2|DFS-R을 지원하는 데 필요합니다.|  
 |Microsoft SQL Server 2005 Express Edition |복제된 MDT DB 복사본을 받습니다.|  
 |DFS-R |배포 공유를 복제하는 데 필요합니다.|  
 |Windows 배포 서비스 |네트워크 PXE 기반 설치를 시작할 수 있도록 하는 데 필요합니다.|  

> [!NOTE]
>  Windows 배포 서비스는 각 자식 서버에서 설정 및 구성해야 하지만 부팅 또는 설치 이미지를 추가할 필요가 없습니다.  

###  <a name="AddContent"></a> MDT에 콘텐츠 추가  
 Deployment 워크벤치를 사용하여 마스터 배포 서버에 콘텐츠를 채우고 다음 섹션에서 설명한 대로 MDT DB를 만들고 채웁니다. 데이터베이스에 채워지는 콘텐츠에 대한 내용은 다음과 같습니다.  

-   애플리케이션과 관련하여 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 애플리케이션 구성" 섹션을 참조하세요.  

-   운영 체제와 관련하여 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 운영 체제 구성" 섹션을 참조하세요.  

-   운영 체제 패키지와 관련하여 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 패키지 구성" 섹션을 참조하세요.  

-   디바이스 드라이버와 관련하여 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 디바이스 드라이버 구성" 섹션을 참조하세요.  

-   작업 순서와 관련하여 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 작업 순서 구성" 섹션을 참조하세요.  

> [!NOTE]
>  배포 공유가 업데이트될 때 만들어진 LiteTouchPE_x86.wim 파일이 Windows 배포 서비스에 추가되었는지 확인하세요.  

###  <a name="PrepareDeployment"></a> Windows 배포 서비스 준비  
 LiteTouchPE_x86.wim 파일은 DFS-R 복제 그룹을 통해 정기적으로 복제되므로, 새로 복제된 Windows PE 환경을 반영하도록 부팅 구성 데이터 저장소를 정기적으로 업데이트해야 합니다. 각 배포 서버에서 다음 단계를 수행합니다.  

 **Windows 배포 서비스를 준비하려면**  

1.  명령 프롬프트 창을 엽니다.  

2.  **WDSUtil/set-server/BCDRefreshPolicy/Enabled:yes/RefreshPeriod:60**을 입력한 다음, Enter 키를 누릅니다.  

> [!NOTE]
>  여기서 제시한 예에서 새로 고침 간격은 60분으로 설정됩니다. 그러나 이 값은 DFS-R과 동일한 기간 동안 복제하도록 구성할 수 있습니다.  

###  <a name="ConfigureFileReplication"></a> 분산 파일 시스템 복제 구성  
 LTI 배포 아키텍처의 크기를 조정하는 경우, MDT 배포 공유와 Windows PE 손쉬운 부팅 환경의 콘텐츠 및 마스터 배포 서버의 콘텐츠 모두를 자식 배포 서버에 복제하기 위한 기초로 DFS-R을 사용합니다.  

> [!NOTE]
>  먼저 DFS-R이 설치되어 있는지 확인한 후에 다음 단계를 수행하세요.  

 **배포 콘텐츠를 복제하도록 DFS-R을 구성하려면**  

1.  DFS 관리 콘솔을 엽니다.  

2.  DFS 관리 콘솔에서 DFS 관리를 확장합니다.  

3.  **복제**를 마우스 오른쪽 단추로 클릭한 다음, **새 복제 그룹**을 클릭합니다.  

4.  새 복제 그룹 마법사의 **복제 그룹 유형** 페이지에서 **새 다목적 복제 그룹**을 클릭합니다.  

5.  **다음**을 클릭합니다.  

6.  **이름 및 도메인** 페이지에서 다음 정보를 입력합니다.  

    -   **복제 그룹 이름** 상자에서 복제 그룹에 대한 이름(예: **MDT 2010 복제 그룹**)을 입력합니다.  

    -   **복제 그룹에 대한 선택적 설명** 상자에서 복제 그룹에 대한 설명(예: **MDT 2010 데이터를 복제하는 그룹**)을 입력합니다.  

    -   **도메인** 상자에서 올바른 도메인 이름이 포함되어 있는지 확인합니다.  

7.  **다음**을 클릭합니다.  

8.  **복제 그룹 구성원** 페이지에서 다음 단계를 수행합니다.  

    1.  **추가**를 클릭합니다.  

    2.  이 복제 그룹의 구성원이 될 모든 서버(예: 모든 자식 배포 서버 및 마스터 배포 서버)의 이름을 입력합니다.  

    3.  **확인**을 클릭합니다.  

9. **다음**을 클릭합니다.  

10. **토폴로지 선택** 페이지에서 **허브 및 스포크**를 클릭하고, **다음**을 클릭합니다.  

11. **허브 구성원** 페이지에서 마스터 배포 서버를 클릭한 다음, **추가**를 클릭합니다.  

12. **다음**을 클릭합니다.  

13. **허브 및 스포크 연결** 페이지에서 각 자식 배포 서버에 대해 나열된 마스터 배포 서버가 **필수 허브 구성원**인지 확인합니다.  

14. **다음**을 클릭합니다.  

15. **복제 그룹 일정 및 대역폭** 페이지에서 서버 간에 콘텐츠를 복제할 일정을 지정합니다.  

16. **다음**을 클릭합니다.  

17. **주 구성원** 페이지의 **주 구성원** 상자에서 마스터 배포 서버를 클릭합니다.  

18. **다음**을 클릭합니다.  

19. **복제할 폴더** 페이지에서 **추가**를 클릭하고, 다음 단계를 수행합니다.  

    1.  **복제할 폴더의 로컬 경로** 상자에서 **찾아보기**를 클릭하여 *X:\\*Deployment 폴더로 이동합니다. 여기서 *X*는 배포 서버의 드라이브 문자입니다.  

    2.  **경로 기반 이름 사용**을 클릭합니다.  

    3.  **확인**을 클릭합니다.  

    4.  **추가**를 클릭합니다.  

    5.  **복제할 폴더 추가** 대화 상자에서 **찾아보기**를 클릭하여 *X:* \RemoteInstall\Boot 폴더로 이동합니다.  

    6.  **경로 기반 이름 사용**을 클릭합니다.  

20. **다음**을 클릭합니다.  

21. **다른 구성원에 대한 로컬 배포 경로** 페이지에서 다음 단계를 수행합니다.  

    1.  배포 그룹의 모든 구성원을 선택한 다음, **편집**을 클릭합니다.  

    2.  **로컬 경로 편집** 대화 상자에서 **사용**을 클릭합니다.  

    3.  Deployment Share 폴더가 자식 배포 서버에 저장되어야 하는 경로를 입력합니다(예: ***X:\Deployment***, 여기서 *X*는 배포 서버의 드라이브 문자임).  

    4.  **확인**을 클릭합니다.  

22. **다음**을 클릭합니다.  

23. **다른 구성원에 대한 로컬 부팅 경로** 페이지에서 다음 단계를 수행합니다.  

    1.  배포 그룹의 모든 구성원을 선택한 다음, **편집**을 클릭합니다.  

    2.  **로컬 경로 편집** 대화 상자에서 **사용**을 클릭합니다.  

    3.  Boot 폴더가 자식 배포 서버에 저장되어야 하는 경로를 입력합니다(***X:\RemoteInstall\Boot***, 여기서 *X*는 배포 서버의 드라이브 문자임).  

    4.  **확인**을 클릭합니다.  

24. **다음**을 클릭합니다.  

25. **원격 설정 및 복제 그룹 만들기** 페이지에서 **만들기**를 클릭하여 새 복제 그룹 마법사를 완료합니다.  

26. **확인** 페이지에서 **닫기**를 클릭하여 마법사를 닫습니다.  

> [!NOTE]
>  이제 새 복제 그룹이 복제 노드 아래에 나열되어 있는지 확인하세요.  

###  <a name="PrepareSQLReplication"></a> SQL Server 복제 준비  
 SQL Server 복제를 구성하기 전에 먼저 몇 가지 사전 구성 단계를 완료하여 배포 서버가 올바르게 구성되어 있는지 확인합니다.  

 **마스터 배포 서버에서 SQL Server 복제를 준비하려면**  

1.  데이터베이스 스냅숏을 저장할 폴더를 만든 다음, 이 폴더를 공유로 구성합니다.  

    > [!NOTE]
    >  스냅숏 폴더 보안에 대한 자세한 내용은 [스냅숏 폴더 보안 설정](http://msdn2.microsoft.com/library/ms151151.aspx)을 참조하세요.  

2.  SQL Server Browser 서비스가 사용되고 [자동]으로 설정되어 있는지 확인합니다.  

3.  **SQL Server 노출 영역 구성** 상자에서 **로컬 및 원격 연결**을 클릭합니다.  

 **자식 배포 서버에서 SQL Server 복제를 준비하려면**  

1.  **SQL Server 노출 영역 구성** 상자에서 **로컬 및 원격 연결**을 클릭합니다.  

2.  필요에 따라 복제된 MDT DB를 호스팅할 빈 데이터베이스를 만듭니다.  

> [!NOTE]
>  이 데이터베이스에는 마스터 배포 서버의 MDT DB와 동일한 이름을 지정해야 합니다. 예를 들어 마스터 배포 서버의 MDT DB가 *MDTDB*라고 하면 자식 배포 서버에 *MDTDB*라는 빈 데이터베이스를 만듭니다.  

###  <a name="ConfigureSQLReplication"></a> SQL Server 복제 구성  
 배포 인프라를 구축하는 데 필요한 파일 및 폴더의 복제를 구성한 후에는 MDT DB를 복제하도록 SQL Server를 구성합니다.  

> [!NOTE]
>  단일 중앙 MDT DB만 유지 관리할 수도 있습니다. 그러나 복제된 버전의 MDT DB를 유지 관리하면 WAN(광역 네트워크)을 통해 전송되는 데이터에 대해 더 많이 제어할 수 있습니다.  

 SQL Server 2005는 다음과 같이 잡지 배포 모델과 비슷한 복제 모델을 사용합니다.  

1.  *게시자*는 *잡지*를 사용(게시)할 수 있게 합니다.  

2.  *배포자*는 게시를 배포하는 데 사용됩니다.  

3.  *읽기 권한자*는 게시를 구독하여 구독자에게 해당 게시를 정기적으로 배달할 수 있습니다(*밀어넣기 구독*).  

 이 용어는 SQL Server 복제 설치 및 구성 마법사를 통해 사용됩니다.  

#### <a name="configure-a-sql-server-publisher"></a>SQL Server 게시자 구성  
 마스터 배포 서버를 SQL Server 게시자로 구성하려면 다음 단계를 수행합니다.  

1.  SQL Server Management Studio를 엽니다.  

2.  **복제** 노드를 마우스 오른쪽 단추로 클릭한 다음, **배포 구성**을 클릭합니다.  

3.  배포 구성 마법사에서 **다음**을 클릭합니다.  

4.  **배포자** 페이지에서 **자체 배포자로 사용합니다. SQL Server에서 배포 데이터베이스와 로그를 만듭니다**를 클릭하고, **다음**을 클릭합니다.  

5.  **스냅숏 폴더** 페이지의 **SQL Server 복제 준비** 섹션에서 만든 스냅숏 폴더에 대한 UNC 경로를 입력합니다.  

6.  **배포 데이터베이스** 페이지에서 **다음**을 클릭합니다.  

7.  **게시자** 페이지에서 마스터 배포 서버를 클릭하여 배포자로 설정하고, **다음**을 클릭합니다.  

8.  **마법사 동작** 페이지에서 **배포 구성**을 클릭하고, **다음**을 클릭합니다.  

9. **마침**을 클릭한 다음, 마법사가 완료되면 **닫기**를 클릭합니다.  

#### <a name="enable-the-mdt-db-for-replication"></a>복제에 MDT DB를 사용하도록 설정  
 마스터 배포 서버에서 복제에 MDT DB를 사용하도록 설정하려면 다음 단계를 수행합니다.  

1.  SQL Server Management Studio에서 **복제** 노드를 마우스 오른쪽 단추로 클릭한 다음, **게시자 속성**을 클릭합니다.  

2.  **게시자 속성** 페이지에서 다음 단계를 수행합니다.  

    1.  **게시자 데이터베이스**를 클릭합니다.  

    2.  MDT DB를 클릭한 다음, **트랜잭션**을 클릭합니다.  

    3.  **확인**을 클릭합니다.  

 이제 트랜잭션 및 스냅숏 복제를 위해 MDT DB가 구성되었습니다.  

#### <a name="create-a-publication-of-the-mdt-db"></a>MDT DB 게시 만들기  
 자식 배포 서버에서 구독할 수 있는 MDT DB의 게시를 만들려면 다음 단계를 수행합니다.  

1.  SQL Server Management Studio에서 [복제]를 펼치고, **로컬 게시**를 마우스 오른쪽 단추로 클릭한 다음, **새 게시**를 클릭합니다.  

2.  새 게시 마법사에서 **다음**을 클릭합니다.  

3.  **게시 데이터베이스** 페이지에서 MDT DB를 클릭하고, **다음**을 클릭합니다.  

4.  **게시 유형** 페이지에서 **스냅숏 게시**를 클릭하고, **다음**을 클릭합니다.  

5.  **아티클** 페이지에서 **테이블, 저장 프로시저** 및 **보기**를 모두 선택하고, **다음**을 클릭합니다.  

6.  **아티클 발급** 페이지에서 **다음**을 클릭합니다.  

7.  **테이블 행 필터** 페이지에서 **다음**을 클릭합니다.  

8.  **스냅숏 에이전트** 페이지에서 다음 단계를 수행합니다.  

    1.  **즉시 스냅숏을 만들고 구독 초기화에 사용할 수 있도록 유지합니다**를 선택합니다.  

    2.  **스냅숏 에이전트 실행 시간 예약**을 클릭합니다.  

    3.  **변경**을 클릭합니다.  

    > [!NOTE]
    >  데이터베이스가 복제되기 전에 1시간 동안 수행될 일정을 지정합니다.  

9. **다음**을 클릭합니다.  

10. **에이전트 보안** 페이지에서 스냅숏 에이전트가 실행될 계정을 클릭하고, **다음**을 클릭합니다.  

11. **마법사 동작** 페이지에서 **게시 만들기**를 클릭하고, **다음**을 클릭합니다.  

12. **마법사 완료** 페이지의 **게시 이름** 상자에서 설명이 포함된 게시 이름을 입력합니다.  

13. **마침**을 클릭하여 마법사를 완료한 다음, 마법사에서 게시가 만들어지면 **닫기**를 클릭합니다.  

    > [!NOTE]
    >  이제 게시가 SQL Server Management Studio의 로컬 게시 노드 아래에 표시됩니다.  

#### <a name="subscribe-child-deployment-servers-to-the-published-mdt-db"></a>게시된 MDT DB에 자식 배포 서버 가입  
 이제 MDT DB가 게시되었으므로 이 배포에 자식 배포 서버를 구독자로 추가할 수 있습니다. 즉, 배포 중에 클라이언트 컴퓨터에서 WAN을 통해 이동하는 대신 네트워크에 로컬인 데이터베이스를 쿼리할 수 있도록 일정에 따라 데이터베이스 복사본을 받게 됩니다.  

 **자식 배포 서버를 MDT DB 게시에 가입시키려면**  

1.  SQL Server Management Studio에서 [복제/로컬 게시]로 이동합니다.  

2.  이전 섹션에서 만든 게시를 마우스 오른쪽 단추로 클릭한 다음, **새 구독**을 클릭합니다.  

3.  새 구독 마법사에서 **다음**을 클릭합니다.  

4.  **게시** 페이지에서 이전 섹션에서 만든 게시를 클릭합니다.  

5.  **배포 에이전트 위치** 페이지에서 **SERVERNAME 배포자에서 모든 에이전트 실행(밀어넣기 구독)** 을 클릭하고, **다음**을 클릭합니다.  

6.  **구독자** 페이지에서 다음 단계를 수행하여 각 자식 배포 서버를 추가합니다.  

    1.  **구독자 추가**를 클릭한 다음, **SQL Server 구독자 추가**를 클릭합니다.  

    2.  각 자식 배포 서버를 추가합니다.  

    3.  **구독 데이터베이스** 상자에서 추가된 각 자식 배포 서버에 대해 해당 자식 배포 서버의 빈 MDT DB를 클릭합니다.  

    > [!NOTE]
    >  빈 MDT DB가 아직 만들어지지 않은 경우 **구독 데이터베이스** 상자에서 새 데이터베이스를 만드는 옵션을 선택합니다.  

    > [!NOTE]
    >  이 데이터베이스에는 마스터 배포 서버의 MDT DB와 동일한 이름을 지정해야 합니다. 예를 들어 마스터 배포 서버의 MDT DB가 *MDTDB*라고 하면 자식 배포 서버에 *MDTDB*라는 빈 데이터베이스를 만듭니다.  

7.  **다음**을 클릭합니다.  

8.  **배포 에이전트 보안** 페이지에서 **...** 를 클릭하여 **배포 에이전트 보안** 대화 상자를 엽니다.  

9. 배포 에이전트에 사용할 계정의 세부 정보를 입력하고, **다음**을 클릭합니다.  

10. **동기화 일정** 페이지에서 다음 단계를 수행합니다.  

    1.  **에이전트 일정** 상자에서 **<일정 정의\>** 를 클릭합니다.  

    2.  마스터 및 자식 배포 서버 간에 데이터베이스를 복제하는 데 사용할 일정을 지정하고, **다음**을 클릭합니다.  

11. **구독 초기화** 페이지에서 **다음**을 클릭합니다.  

12. **마법사 동작** 페이지에서 **구독 만들기**를 클릭하고, **다음**을 클릭합니다.  

13. **마침**을 클릭한 다음, 마법사가 성공적으로 완료되면 **닫기**를 클릭합니다.  

 이제 SQL Server 복제가 구성되었고, MDT DB가 정기적으로 마스터 배포 서버에서 가입된 모든 자식 배포 서버로 복제됩니다.  

#### <a name="configure-customsettingsini"></a>CustomSettings.ini 구성  
 이제 LTI 배포 인프라가 성공적으로 만들어졌으며 각 위치에는 다음과 같은 복제된 복사본이 있는 LTI 배포 서버가 포함되어 있습니다.  

-   배포 공유  

-   MDT DB  

-   Windows 배포 서비스에 추가된 LiteTouchPE_x86 Windows PE 환경  

 이제 Windows 배포 서비스를 통해 LiteTouchPE_x86.wim 환경을 제공하는 서버인 로컬 배포 서버에서 배포 콘텐츠(배포 공유 및 데이터베이스)를 사용하도록 배포 공유에 대한 CustomSettings.ini 파일을 구성할 수 있습니다.  

 Windows 배포 서비스에서 LiteTouchPE_x86.wim 파일을 배달하면 레지스트리 키가 사용 중인 Windows 배포 서비스 서버의 이름으로 구성됩니다. MDT는 CustomSettings.ini를 구성하는 데 사용할 수 있는 변수(%WDSServer%)에서 이 서버 이름을 캡처합니다.  

 **항상 로컬 LTI 배포 서버를 사용하려면**  

> [!NOTE]
>  다음 절차에서는 배포 공유가 만들어져 Deployment$ 공유로 설정되었다고 가정합니다.  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **규칙** 탭을 클릭한 다음, CustomSettings.ini 파일을 수정하여 다음 속성을 구성합니다.  

    -   추가된 각 SQL Server 섹션에 대해 **%WDSServer%—** 서버 이름을 사용하도록 **SQLServer**를 구성합니다(예: **SQLServer=%WDSServer%**).  

    -   **DeployRoot**를 구성하는 경우 **%WDSServer%** 변수를 사용하도록 **DeployRoot**를 구성합니다(예: **DeployRoot=\\\\%WDSServer%\Deployment$**).  

5.  **Bootstrap.ini 편집**을 클릭합니다.  

6.  **DeployRoot** 값을 **DeployRoot=\\\\%WDSServer%\Deployment$** 에 추가하거나 변경하여 **%WDSServer%** 속성을 사용하도록 BootStrap.ini를 구성합니다.  

7.  **파일**을 클릭한 다음, **저장**을 클릭하여 BootStrap.ini 파일의 변경 내용을 저장합니다.  

8.  **확인**을 클릭합니다.  

     배포 공유 및 LiteTouchPE_x86.wim Windows PE 환경을 업데이트해야 합니다.  

9. [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

10. **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

11. **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

12. **확인** 페이지에서 **마침**을 클릭합니다.  

 다음 예제에서는 이 섹션에서 설명한 단계를 수행한 후의 CustomSettings.ini를 보여 줍니다.  

 **확장 가능한 LTI 배포 인프라에 맞게 구성된 CustomSettings.ini 예제**  

```  
[Settings]  
Priority=CSettings,CPackages, CApps, CAdmins, CRoles, Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  
ScanStateArgs=/v:5 /o /c  
LoadStateArgs=/v:5 /c /lac  

[CSettings]  
SQLServer=%WDSServer%  
Instance=  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerSettings  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  

[CPackages]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerPackages  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
Order=Sequence  

[CApps]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerApplications  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
Order=Sequence  

[CAdmins]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerAdministrators  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  

[CRoles]  
SQLServer=%WDSServer%  
Database=MDTDB  
Netlib=DBNMPNTW  
SQLShare=  
Table=ComputerRoles  
Parameters=UUID, AssetTag, SerialNumber, MacAddress  
ParameterCondition=OR  
```  

## <a name="selecting-a-local-mdt-server-when-multiple-servers-exist"></a>여러 서버가 있는 경우 로컬 MDT 서버 선택  
 이 시나리오에서는 여러 MDT 서버를 사용하여 대량의 동시 배포 및 여러 사이트에 대한 배포를 지원합니다. LTI 배포가 초기화되면 기본 동작은 MDT 서버의 경로를 요청하여 연결하고 필요한 파일에 액세스하여 배포 프로세스를 시작하는 것입니다.  

 Windows 배포 마법사는 LocalServer.xml 파일을 사용하여 각 위치에 대해 알려진 배포 서버를 선택할 수 있습니다.  

 LocationServer.xml 파일을 사용하려면 다음을 수행합니다.  

-   [LocationServer.xml 이해](#UnderstandingLocationServer)에서 설명한 대로 LocationServer.xml의 용도와 사용을 숙지합니다.  

-   [LocationServer.xml 파일 만들기](#CreateLocationServer)에서 설명한 대로 LocationServer.xml 파일을 만듭니다.  

-   'Extra Files 디렉터리에 LocationServer.xml 파일 추가'에서 설명한 대로 Extra Files 디렉터리에 LocationServer.xml 파일을 추가합니다.  

-   [BootStrap.ini 파일 업데이트](#UpdateBootstrap)에서 설명한 대로 BootStrap.ini 파일을 업데이트합니다.  

-   [배포 공유 업데이트](#UpdateDeploymentShare)에서 설명한 대로 배포 공유를 업데이트합니다.  

 이 시나리오에서는 MDT가 배포 서버에 구성되어 있다고 가정합니다.  

###  <a name="UnderstandingLocationServer"></a> LocationServer.xml 이해  
 먼저 MDT에서 LocationServer.xml을 사용하는 방법을 이해해야 합니다. LTI를 수행하는 동안 MDT 스크립트에서 BootStrap.ini 파일을 읽고 처리하여 배포에 대한 초기 정보를 수집합니다. 이는 배포 서버에 연결되기 전에 발생합니다. 따라서 **DeployRoot** 속성은 일반적으로 BootStrap.ini 파일에서 연결을 만들어야 하는 배포 서버를 지정하는 데 사용됩니다.  

 BootStrap.ini 파일에 **DeployRoot** 속성이 없으면 MDT 스크립트에서 사용자에게 배포 서버에 대한 경로를 묻는 마법사 페이지를 로드합니다. **HTA(HTML 응용 프로그램)** 마법사 페이지가 초기화되는 동안 MDT 스크립트에서 LocationServer.xml 파일의 존재 여부를 확인하고, 있는 경우 LocationServer.xml을 사용하여 사용 가능한 배포 서버를 표시합니다.  

#### <a name="understand-when-to-use-locationserverxml"></a>LocationServer.xml을 사용하는 경우에 대한 이해  
 MDT는 LTI 배포 시 연결할 서버를 결정할 수 있는 여러 가지 방법을 제공합니다. 배포 서버를 찾는 다양한 방법은 여러 가지 시나리오에 가장 적합합니다. 따라서 LocationServer.xml을 사용해야 하는 경우를 잘 알고 있어야 합니다.  

 MDT는 가장 적합한 배포 서버를 자동으로 검색하고 사용하는 몇 가지 방법을 제공합니다. 다음 표에는 이러한 방법이 나와 있습니다.

 |**방법** |**세부 정보** |  
 |-|-|  
 |**%WDSServer%** |MDT 서버가 Windows 배포 서비스 서버에서 공동 호스팅되는 경우에 사용됩니다.<br /><br /> Windows 배포 서비스에서 LTI 배포가 시작되면 %WDSServer% 환경 변수가 만들어지고 Windows 배포 서비스 서버의 이름으로 채워집니다.<br /><br /> **DeployRoot** 변수에서 이 변수를 사용하여 Windows 배포 서비스 서버의 배포 공유에 자동으로 연결합니다. 예를 들어 다음과 같습니다.<br /><br /> **DeployRoot=\\\\%WDSServer%\Deployment$** |  
 |**위치 기반 자동화** |MDT에서 위치 기반 자동화를 BootStrap.ini 파일에 사용하여 배포해야 하는 서버를 결정할 수 있습니다.<br /><br /> **기본 게이트웨이** 속성을 사용하여 서로 다른 위치를 구분합니다. **기본 게이트웨이**마다 다른 MDT 서버가 지정됩니다.<br /><br /> 위치 기반 자동화 사용에 대한 자세한 내용은 "구성 설정을 적용하는 방법 선택"을 참조하세요.|  

 앞의 표에서 나열한 각각의 방법은 특정 시나리오에 대해 지정된 위치에 있는 배포 서버를 자동으로 선택하는 한 가지 방법을 제공합니다. 이러한 방법은 특정 시나리오(예: MDT 서버가 Windows 배포 서비스와 공동으로 호스팅되는 경우)를 대상으로 합니다.  

 이러한 방법이 적합하지 않은 다른 시나리오가 있습니다. 예를 들어 위치를 결정할 수 있을 만큼 네트워크가 충분히 세분화되지 않았거나 MDT 서버가 Windows 배포 서비스와 분리되지 않은 경우와 같이 지정된 위치에 여러 개의 배포 서버가 있거나 자동화 논리를 사용할 수 없는 경우가 있습니다.  

 이러한 시나리오에서 LocationServer.xml 파일은 배포 시 서버 이름과 배포 공유 이름을 알고 있지 않아도 이 정보를 제공하는 유연한 방법을 제공합니다.  

###  <a name="CreateLocationServer"></a> LocationServer.xml 파일 만들기  
 LTI 배포 중에 사용 가능한 배포 서버 목록을 표시하려면 각 서버에 대한 세부 정보가 포함되는 LocationServer.xml 파일을 만듭니다. MDT에는 기본 LocationServer.xml 파일이 없으므로 다음 지침을 사용하여 이 파일을 만듭니다.  

#### <a name="create-a-locationserverxml-file-to-support-multiple-locations"></a>여러 위치를 지원하도록 LocationServer.xml 파일 만들기  
 LocationServer.xml을 만들고 사용하는 가장 간단한 방법은 LocationServer.xml 파일을 만들고 환경에 있는 각 배포 서버에 대한 항목을 추가하는 것입니다. 이러한 서버는 동일하거나 다른 위치에 있을 수 있습니다.  

 각 서버에 대한 새 섹션을 만들고 다음 정보를 추가하여 LocationServer.xml 파일을 만듭니다.  

-   고유 식별자  

-   해당 위치를 쉽게 식별할 수 있는 이름을 표시하는 데 사용되는 위치 이름  

-   해당 위치의 MDT 서버에 대한 UNC 경로  

 다음은 여러 위치로 구성된 LocationServer.xml 파일 샘플을 사용하여 이러한 속성을 각각 사용하여 LocationServer.xml 파일을 만드는 방법을 보여 줍니다.  

 **여러 위치를 지원하는 LocationServer.xml 파일 예제**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS01\Deployment$</UNCPath>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso NYC, New York, USA  
        </friendlyname>  
        <UNCPath>\\NYCDS01\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

 다음 예제와 같이 이 형식을 사용하여 각 위치에 대해 다른 서버 항목을 지정하거나 단일 위치에 여러 서버가 있는 상황에서 해당 위치의 각 서버에 대해 다른 서버 항목을 지정합니다.   

 **서로 다른 위치에 있는 여러 서버를 지원하는 LocationServer.xml 파일 예제**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ DS1, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS01\Deployment$</UNCPath>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso HQ DS2, Seattle, USA  
        </friendlyname>  
        <UNCPath>\\STLDS02\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

#### <a name="create-a-locationserverxml-file-to-load-balance-multiple-servers-at-different-locations"></a>여러 위치에 있는 여러 서버의 부하를 분산하도록 LocationServer.xml 파일 만들기  
 LocationServer.xml을 사용하여 위치 항목별로 여러 서버를 지정한 다음, 위치가 선택되면 MDT가 사용 가능한 서버 목록에서 배포 서버를 자동으로 선택하도록 기본 부하 분산을 수행합니다. 이 기능을 제공하기 위해 LocationServer.xml 파일은 가중치 메트릭을 지정할 수 있도록 지원합니다.  

 다음은 서로 다른 위치에 있는 여러 서버에 대해 구성된 LocationServer.xml 파일 샘플을 보여 줍니다.  

 **여러 위치에 대한 LocationServer.xml 파일 예제**  

```  
<?xml version="1.0" encoding="utf-8" ?>  
<servers>  
    <QueryDefault></QueryDefault>  
    <server>  
        <serverid>1</serverid>  
        <friendlyname>  
          Contoso HQ, Seattle, USA  
        </friendlyname>  
        <Server1>\\STLDS01\Deployment$</Server1>  
        <Server2>\\STLDS02\Deployment$</Server2>  
        <Server3>\\STLDS03\Deployment$</Server3>  
        <Server weight=”1”>\\STLDS01\Deployment$</Server>  
        <Server weight=”2”>\\STLDS02\Deployment$</Server>  
        <Server weight=”4”>\\STLDS03\Deployment$</Server>  
    </server>  
    <server>  
        <serverid>2</serverid>  
        <friendlyname>  
          Contoso NYC, New York, USA  
        </friendlyname>  
        <UNCPath>\\NYCDS01\Deployment$</UNCPath>  
    </server>   
</servers>  
```  

 MDT가 서버 선택 프로세스에서 사용하는 <server weight\> 태그를 사용하여 가중치 메트릭을 지정합니다. 서버를 선택할 가능성은 다음과 같이 계산됩니다.  

 **서버 가중치/모든 서버 가중치의 합계**  

 앞의 예제에서 Contoso HQ의 세 서버는 1, 2 및 4로 나열됩니다. 가중치가 2인 서버를 선택할 가능성은 2/7입니다. 따라서 가중치 시스템을 사용하려면, 한 위치에서 사용할 수 있는 서버의 용량을 결정하고 각 서버를 서버의 용량으로 다른 각 서버와 비교하여 가중치를 부여합니다.  

### <a name="adding-the-locationserverxml-file-to-the-extra-files-directory"></a>Extra Files 디렉터리에 LocationServer.xml 파일 추가  
 LocationServer.xml 파일이 만들어지면 ***X:\\Deploy\Control 폴더***의 LiteTouch_x86 및 LiteTouch_x64 Windows PE 부팅 이미지에 이 파일을 추가합니다. Deployment 워크벤치를 사용하여 배포 공유 속성에 추가할 추가 디렉터리를 지정하여 이러한 Windows PE 이미지에 다른 파일과 폴더를 추가합니다.  

 **배포 공유에 LocationServer.xml을 추가하려면**  

1.  루트 배포 공유 폴더에 *Extra Files*라는 폴더를 만듭니다(예: D:\Production Deployment Share\Extra Files).  

2.  추가 파일이 있어야 하는 Windows PE 위치를 미러링하는 Extra Files 폴더에 폴더 구조를 만듭니다.  

     예를 들어 LocationServer.xml 파일은 Windows PE의 \Deploy\Control 폴더에 있어야 합니다. 따라서 Extra Files 아래에 동일한 폴더 구조를 만듭니다(예: D:\Production Deployment Share\Extra Files\Deploy\Control).  

3.  LocationServer.xml을 *deployment_share*\Extra Files\Deploy\Control 폴더에 복사합니다. 여기서 *deployment_share*는 배포 공유의 루트 폴더에 대한 정규화된 경로입니다.  

4.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

5.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

6.  [작업] 창에서 **속성**을 클릭합니다.  

7.  ***deployment_shareProperties*** 대화 상자(여기서 deployment_share는 배포 공유의 이름임)에서 다음 단계를 수행합니다.  

    1.  **Windows PE platform 설정** 탭을 클릭합니다. 여기서 *platform*은 구성할 Windows PE 이미지의 아키텍처입니다.  

    2.  **Windows PE 사용자 지정** 섹션의 **추가할 추가 디렉터리** 상자에서 ***path***를 입력한 다음(여기서 *path*는 Extra Files 폴더에 대한 정규화된 경로임(예: D:\Production Deployment Share\Extra Files)), **확인**을 클릭합니다.  

###  <a name="UpdateBootstrap"></a> BootStrap.ini 파일 업데이트  
 Deployment 워크벤치를 사용하여 배포 공유를 만들면 **DeployRoot** 속성이 자동으로 만들어져 BootStrap.ini 파일에 채워집니다. LocationServer.xml 파일은 **DeployRoot** 속성을 채우는 데 사용되므로 BootStrap.ini 파일에서 이 값을 제거해야 합니다.  

 **BootStrap.ini에서 DeployRoot 속성을 제거하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  ***deployment_shareProperties*** 대화 상자(여기서 *deployment_share*는 배포 공유 이름임)에서 **규칙** 탭을 클릭한 다음, **BootStrap.ini 편집**을 클릭합니다.  

5.  **DeployRoot** 값을 제거합니다(예: **DeployRoot=\\\Server\Deployment$**).  

6.  **파일**을 클릭한 다음, **저장**을 클릭하여 BootStrap.ini 파일의 변경 내용을 저장합니다.  

7.  **확인**을 클릭하여 변경 내용을 제출합니다.  

###  <a name="UpdateDeploymentShare"></a> 배포 공유 업데이트  
 LocationServer.xml 파일과 업데이트된 BootStrap.ini 파일이 포함된 새로운 LiteTouch_x86 및 LiteTouch_x64 부팅 환경을 생성하려면 배포 공유를 업데이트해야 합니다.  

 **배포 공유를 업데이트하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

4.  **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

5.  **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

6.  **확인** 페이지에서 **마침**을 클릭합니다.  

> [!NOTE]
>  업데이트 프로세스가 완료되면 새 LiteTouch_x86 및 LiteTouch_x64 Windows PE 환경을 Windows 배포 서비스에 다시 추가하거나 배포 시 사용할 부팅 미디어로 굽습니다.  

## <a name="replacing-an-existing-computer-with-a-new-computer-using-lite-touch-installation"></a>LTI를 사용하여 기존 컴퓨터를 새 컴퓨터로 바꾸기  
 MDT를 사용하여 엔터프라이즈 아키텍처의 기존 컴퓨터를 대체할 새 컴퓨터에 이미지를 배포할 수 있습니다. 이러한 상황은 운영 체제 간에 업그레이드하거나(새 운영 체제에 새 하드웨어가 필요할 수 있음) 조직에서 기존 애플리케이션에 대해 더 새롭고 빠른 컴퓨터가 필요한 경우에 발생할 수 있습니다.  

 기존 컴퓨터를 새 컴퓨터로 대체할 때 사용자 계정 및 사용자 상태 데이터와 같이 컴퓨터 간에 마이그레이션할 모든 설정을 고려하는 것이 좋습니다. 또한 마이그레이션이 실패하는 경우에 대비하여 복구 솔루션도 만들어야 합니다.  

 이 샘플 배포에서는 기존 컴퓨터(WDG-EXIST-01)의 사용자 상태 데이터를 캡처하고 네트워크 공유에 저장하여 CORP 도메인에서 WDG-EXIST-01을 새 컴퓨터(WDG-NEW-02)로 대체합니다. 그런 다음, 기존 이미지를 WDG-NEW-02에 배포하고, 마지막으로 캡처한 사용자 상태 데이터를 WDG-NEW-02로 복원합니다. 배포는 배포 서버(WDG-MDT-01)에서 수행됩니다.  

 MDT에서 표준 클라이언트 바꾸기 작업 순서 템플릿을 사용하여 필요한 모든 배포 작업을 수행할 작업 순서를 만듭니다.  

 이 데모에서는 다음을 가정합니다.  

-   MDT가 배포 서버(WDG MDT 01)에 설치되었습니다.  

-   운영 체제 이미지, 응용 프로그램 및 디바이스 드라이버를 포함하여 배포 공유가 이미 만들어져 채워졌습니다.  

-   참조 컴퓨터 이미지가 이미 캡처되었고 새 컴퓨터(WDG NEW 02)에 배포됩니다.  

-   적절한 공유 권한을 사용하여 배포 서버(WDG MDT 01)에 네트워크 공유 폴더(UserStateCapture$)가 만들어지고 공유되었습니다.  

 이 샘플을 시작하기 전에 배포 공유가 있어야 합니다. 배포 공유를 만드는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 배포 공유 관리" 섹션을 참조하세요.  

### <a name="step-1-create-a-task-sequence-to-capture-the-user-state"></a>1단계: 사용자 상태를 캡처하는 작업 순서 만들기  
 새 작업 순서 마법사를 사용하여 Deployment 워크벤치의 작업 순서 노드에 MDT 작업 순서를 만듭니다. 컴퓨터 바꾸기 배포 시나리오의 첫 번째 부분(기존 컴퓨터의 사용자 상태 캡처)을 수행하려면 새 작업 순서 마법사에서 표준 클라이언트 바꾸기 작업 순서 템플릿을 선택합니다.  

 **컴퓨터 바꾸기 배포 시나리오에서 사용자 상태를 캡처하는 작업 순서를 만들려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **새 작업 순서**를 클릭합니다.  

     새 작업 순서 마법사가 시작됩니다.  

4.  다음 정보를 사용하여 새 작업 순서 마법사를 완성합니다. 달리 지정하지 않으면 기본값을 적용합니다.  

    |**마법사 페이지** |**수행할 작업** |  
    |-|-|  
    |**일반 설정** |1.  **작업 순서 ID**에서 **VISTA_EXIST**를 입력합니다.<br />2.  **작업 순서 이름**에서 **기존 컴퓨터에서 컴퓨터 시나리오 바꾸기 수행**을 입력합니다.<br />3.  **다음**을 클릭합니다.|  
    |**템플릿 선택** |**다음 작업 순서 템플릿을 사용할 수 있습니다**. **시작 지점으로 사용하려는 템플릿을 선택하십시오.** 에서 **표준 클라이언트 작업 순서 바꾸기**를 선택하고, **다음**을 클릭합니다.|  
    |**요약** |구성 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.|  
    |**확인** |**마침**을 클릭합니다.|  

 새 작업 순서 마법사가 완료되고 **VISTA_EXIST** 작업 순서가 작업 순서 목록에 추가됩니다.  

### <a name="step-2-create-a-task-sequence-to-deploy-operating-system-and-restore-the-user-state"></a>2단계: 운영 체제 배포 및 사용자 상태 복원 작업 순서 만들기  
 새 작업 순서 마법사를 사용하여 Deployment 워크벤치의 작업 순서 노드에 MDT 작업 순서를 만듭니다. 컴퓨터 바꾸기 배포 시나리오의 두 번째 부분(운영 체제 배포 및 기존 컴퓨터의 사용자 상태 복원)을 수행하려면 새 작업 순서 마법사에서 표준 클라이언트 작업 순서 템플릿을 선택합니다.  

 **컴퓨터 바꾸기 배포 시나리오에서 사용자 상태를 배포하는 작업 순서를 만들려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **새 작업 순서**를 클릭합니다.  

     새 작업 순서 마법사가 시작됩니다.  

4.  다음 정보를 사용하여 새 작업 순서 마법사를 완성합니다. 달리 지정하지 않으면 기본값을 적용합니다.  

    |**마법사 페이지**|**수행할 작업**|  
    |-|-|  
    |**일반 설정**|1.  **작업 순서 ID**에서 **VISTA_NEW**를 입력합니다.<br />2.  **작업 순서 이름**에서 **새 컴퓨터에서 컴퓨터 바꾸기 시나리오 수행**을 입력합니다.<br />3.  **다음**을 클릭합니다.|  
    |**템플릿 선택**|**다음 작업 순서 템플릿을 사용할 수 있습니다**. **시작 지점으로 사용하려는 템플릿을 선택하십시오.** 에서 **표준 클라이언트 작업 순서**를 선택하고, **다음**을 클릭합니다.|  
    |**OS 선택**|**다음 운영 체제 이미지는 이 작업 순서를 사용하여 배포할 수 있습니다**. [사용할 이미지를 선택하십시오.]에서 ***captured_vista_image***를 선택하고(여기서 *captured_vista_image*는 Deployment 워크벤치의 운영 체제 노드에 참조 컴퓨터를 추가한 캡처 이미지임), *다음*을 클릭합니다.|  
    |**제품 키 지정**|**지금 제품 키 지정 안 함**을 선택하고, **다음**을 클릭합니다.|  
    |OS 설정|1.  **전체 이름**에서 **Woodgrove 직원**을 입력합니다.<br />2.  **조직**에서 **Woodgrove 은행**을 입력합니다.<br />3.  **Internet Explorer 홈 페이지**에서 **http://www.woodgrovebank.com**을 입력합니다.<br />4.  **다음**을 클릭합니다.|  
    |**관리자 암호**|**관리자 암호** 및 **관리자 암호 확인**에서 **P@ssw0rd**를 입력한 다음, **마침**을 클릭합니다.|  
    |**확인**|**마침**을 클릭합니다.|  

 새 작업 순서 마법사가 완료되고 **VISTA_NEW** 작업 순서가 작업 순서 목록에 추가됩니다.  

### <a name="step-3-customize-the-mdt-configuration-files"></a>3단계: MDT 구성 파일 사용자 지정  
 MDT 작업 순서가 만들어지면 사용자 상태 정보를 캡처하기 위한 구성 설정을 제공하는 MDT 구성 파일을 사용자 지정합니다. 특히 배포 프로세스의 앞부분에서 만든 배포 공유의 속성에서 파일을 수정하여 CustomSettings.ini 파일을 사용자 지정합니다. 이후 단계에서는 배포 공유에서 구성 파일이 업데이트되도록 배포 공유가 업데이트됩니다.  

 **사용자 상태 정보를 캡처하도록 MDT 구성 파일을 사용자 지정하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

     **속성** 대화 상자가 표시됩니다.  

4.  **속성** 대화 상자에서 **규칙** 탭을 클릭합니다.  

5.  **규칙** 탭에서 다음 예제와 같이 필요한 변경 내용을 반영하도록 CustomSettings.ini 파일을 수정합니다. 환경에 필요한 추가 수정 작업을 수행합니다.  

     **사용자 지정된 CustomSettings.ini 파일**  

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  

    UDShare=\\WDG-MDT-01\UserStateCapture$  
    UDDir=%OSDCOMPUTERNAME%  
    UserDataLocation=NETWORK  
    SkipCapture=NO  
    SkipAdminPassword=YES  
    SkipProductKey=YES  

    ```  

6.  **속성** 대화 상자에서 **확인**을 클릭합니다.  

7.  열려 있는 모든 창 및 대화 상자를 닫습니다.  

### <a name="step-4-configure-the-windows-pe-options-for-the-deployment-share"></a>4단계: 배포 공유에 대한 Windows PE 옵션 구성  
 Deployment 워크벤치의 배포 공유 노드에서 배포 공유에 대한 Windows PE 옵션을 구성합니다.  

> [!NOTE]
>  기존 컴퓨터(WDG-EXIST-01) 및 새 컴퓨터(WDG-NEW-01)용 디바이스 드라이버가 Windows Vista에 포함되어 있는 경우 이 단계를 건너뛰고 다음 단계로 진행합니다.  

 **배포 공유에 대한 Windows PE 옵션을 구성하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

     **속성** 대화 상자가 표시됩니다.  

4.  **속성** 대화 상자에 있는 **Windows PE *platform* 구성 요소** 탭(여기서 *platform*은 구성할 Windows PE 이미지의 아키텍처임)의 **선택 프로필**에서 ***device_drivers***를 선택한 다음(여기서 *device_drivers*는 장치 드라이버 선택 프로필의 이름임), **확인**을 클릭합니다.  

### <a name="step-5-update-the-deployment-share"></a>5단계: 배포 공유 업데이트  
 배포 공유에 대한 Windows PE 옵션이 구성되면 배포 공유를 업데이트합니다. 배포 공유를 업데이트하면 모든 MDT 구성 파일이 업데이트되고 Windows PE의 사용자 지정 버전이 생성됩니다. 사용자 지정 버전의 Windows PE는 참조 컴퓨터를 시작하고 LTI 배포 프로세스를 시작하는 데 사용됩니다.  

 **Deployment 워크벤치에서 배포 공유를 업데이트하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

4.  **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

5.  **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

6.  **확인** 페이지에서 **마침**을 클릭합니다.  

 Deployment 워크벤치에서 배포 공유 업데이트를 시작합니다. Deployment 워크벤치는 *deployment_share*\Boot 폴더에 LiteTouchPE_x86.iso 및 LiteTouchPE_x86.wim 파일(32비트 대상 컴퓨터용) 또는 LiteTouchPE_x64.iso 및 LiteTouchPE_x64.wim 파일(64비트 대상 컴퓨터용)을 만듭니다. 여기서 *deployment_share*는 배포 공유로 사용되는 공유 폴더입니다.  

### <a name="step-6-create-the-lti-bootable-media"></a>6단계: LTI 부팅 가능한 미디어 만들기  
 배포 공유가 업데이트되면 만들어진 Windows PE의 사용자 지정 버전으로 컴퓨터를 시작하는 방법을 제공합니다. Deployment 워크벤치는 *deployment_share*\Boot 폴더에 LiteTouchPE_x86.iso 및 LiteTouchPE_x86.wim 파일(32비트 대상 컴퓨터용) 또는 LiteTouchPE_x64.iso 및 LiteTouchPE_x64.wim 파일(64비트 대상 컴퓨터용)을 만듭니다. 여기서 *deployment_share*는 배포 공유로 사용되는 공유 폴더입니다. 이러한 이미지 중 하나에서 적절한 LTI 부팅 가능한 미디어를 만듭니다.  

 **LTI 부팅 가능한 미디어를 만들려면**  

1.  Windows 탐색기에서 *deployment_share*\Boot 폴더로 이동합니다. 여기서 *deployment_share*는 배포 공유로 사용되는 공유 폴더입니다.  

2.  기존 컴퓨터(WDG-EXIST-01) 및 새 컴퓨터(WDG-NEW-02)에 사용된 컴퓨터 종류에 따라 다음 작업 중 하나를 수행합니다.  

    -   참조 컴퓨터가 물리적 컴퓨터인 경우 ISO 파일의 CD 또는 DVD를 만듭니다.  

    -   참조 컴퓨터가 VM인 경우 ISO 파일 또는 ISO 파일의 CD 또는 DVD에서 직접 VM을 시작합니다.  

### <a name="step-7-start-the-existing-computer-with-the-lti-bootable-media"></a>7단계: LTI 부팅 가능한 미디어로 기존 컴퓨터 시작  
 프로세스의 앞부분에서 만든 LTI 부팅 가능한 미디어를 사용하여 기존 컴퓨터(WDG-EXIST-01)를 시작합니다. 이 CD는 기존 컴퓨터에서 Windows PE를 시작하고 MDT 배포 프로세스를 시작합니다. MDT 배포 프로세스가 완료되면 사용자 상태 마이그레이션 정보가 UserStateCapture$ 공유 폴더에 저장됩니다.  

> [!NOTE]
>  Windows 배포 서비스에서 대상 컴퓨터를 시작하여 MDT 프로세스를 시작할 수도 있습니다. 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Windows 배포 서비스 준비" 섹션을 참조하세요.  

 **LTI 부팅 가능한 미디어로 기존 컴퓨터를 시작하려면**  

1.  프로세스의 앞부분에서 만든 LTI 부팅 가능한 미디어를 사용하여 WDG-EXIST-01을 시작합니다.  

     Windows PE가 시작된 다음, Windows 배포 마법사가 시작됩니다.  

2.  다음 정보를 사용하여 Windows 배포 마법사를 완성합니다. 달리 지정하지 않으면 기본값을 적용합니다.  

    |**마법사 페이지**|**수행할 작업**|  
    |-|-|  
    |**배포 시작**|**배포 마법사 실행**을 클릭하여 새 운영 체제를 설치하고, **다음**을 클릭합니다.|  
    |**네트워크 공유에 연결할 자격 증명을 지정하십시오.**|1.  **사용자 이름**에서 **관리자**를 클릭합니다.<br />2.  **암호**에서 **P@ssw0rd**를 입력합니다.<br />3.  **도메인**에서 **CORP**를 입력합니다.<br />4.  **확인**을 클릭합니다.|  
    |**이 컴퓨터에서 실행할 작업 순서를 선택하십시오.**|*기존 컴퓨터에서 컴퓨터 시나리오 바꾸기 수행*을 클릭하고, **다음**을 클릭합니다.|  
    |**데이터 및 설정을 저장할 위치 지정**|**다음**을 클릭합니다.|  
    |**전체 컴퓨터 백업을 저장할 위치 지정**|**기존 컴퓨터 백업 안 함**을 클릭하고, **다음**을 클릭합니다.|  
    |**시작할 준비가 되었습니다.**|**시작**을 클릭합니다.|  

     오류 또는 경고가 발생하면 *참조 문제 해결* MDT 문서를 참조하세요.  

3.  **배포 요약** 대화 상자에서 **세부 정보**를 클릭합니다.  

     오류 또는 경고가 발생하면 해당 오류 또는 경고를 검토하고 진단 정보를 기록합니다.  

4.  **배포 요약** 대화 상자에서 **마침**을 클릭합니다.  

 사용자 상태 마이그레이션 정보가 캡처되고 프로세스의 앞부분에서 만든 네트워크 공유 폴더(UserStateCapture$)에 저장됩니다.  

### <a name="step-8-start-the-new-computer-with-the-lti-bootable-media"></a>8단계: LTI 부팅 가능한 미디어로 새 컴퓨터 시작  
 프로세스의 앞부분에서 만든 LTI 부팅 가능한 미디어를 사용하여 새 컴퓨터(WDG-NEW-02)를 시작합니다. 이 CD는 참조 컴퓨터에서 Windows PE를 시작하고 MDT 배포 프로세스를 시작합니다. MDT 배포 프로세스가 완료되면 Windows Vista가 새 컴퓨터에 배포되고 캡처된 사용자 상태 마이그레이션 정보가 새 컴퓨터에 복원됩니다.  

> [!NOTE]
>  Windows 배포 서비스에서 대상 컴퓨터를 시작하여 MDT 프로세스를 시작할 수도 있습니다. 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Windows 배포 서비스 준비" 섹션을 참조하세요.  

 **LTI 부팅 가능한 미디어로 새 컴퓨터를 시작하려면**  

1.  프로세스의 앞부분에서 만든 LTI 부팅 가능한 미디어를 사용하여 WDG-NEW-02를 시작합니다.  

     Windows PE가 시작된 다음, Windows 배포 마법사가 시작됩니다.  

2.  다음 정보를 사용하여 Windows 배포 마법사를 완성합니다. 달리 지정하지 않으면 기본값을 적용합니다.  

    |**마법사 페이지**|**수행할 작업**|  
    |--|--|
    |**배포 시작**|**배포 마법사를 실행하여 새 운영 체제를 설치합니다.** 를 클릭하고, **다음**을 클릭합니다.|  
    |**네트워크 공유에 연결할 자격 증명을 지정하십시오.**|1.  **사용자 이름**에서 **관리자**를 클릭합니다.<br />2.  **암호**에서 **P@ssw0rd**를 입력합니다.<br />3.  **도메인**에서 **CORP**를 입력합니다.<br />4.  **확인**을 클릭합니다.|  
    |**이 컴퓨터에서 실행할 작업 순서를 선택하십시오.**|**새 컴퓨터에서 컴퓨터 시나리오 바꾸기 수행**을 클릭하고, **다음**을 클릭합니다.|  
    |**컴퓨터 이름 구성**|**컴퓨터 이름**에서 **WDG-NEW-02**를 입력하고, **다음**을 클릭합니다.|  
    |**도메인 또는 작업 그룹에 컴퓨터 조인**|**다음**을 클릭합니다.|  
    |**사용자 데이터 복원 여부 지정**|1.  **위치 지정**을 클릭합니다.<br />2.  **위치**에서 **\\\WDG-MDT-01\UserStateCapture$\WDG-EXIST-01**을 입력합니다.<br />3.  **다음**을 클릭합니다.|  
    |**로캘 선택**|**다음**을 클릭합니다.|  
    |**표준 시간대 설정**|**다음**을 클릭합니다.|  
    |**이미지 캡처 여부 지정**|**이 컴퓨터의 이미지 캡처 안 함**을 클릭하고, **다음**을 클릭합니다.|  
    |**BitLocker 구성 지정**|**이 컴퓨터에 대해 BitLocker 사용 안 함**을 클릭하고, **다음**을 클릭합니다.|  
    |**시작할 준비가 되었습니다.**|**시작**을 클릭합니다.|  

     오류 또는 경고가 발생하면 *참조 문제 해결* MDT 문서를 참조하세요.  

3.  **배포 요약** 대화 상자에서 **세부 정보**를 클릭합니다.  

     오류 또는 경고가 발생하면 해당 오류 또는 경고를 검토하고 진단 정보를 기록합니다.  

4.  **배포 요약** 대화 상자에서 **마침**을 클릭합니다.  

 이제 Windows Vista가 새 컴퓨터에 설치되고 캡처된 사용자 상태 마이그레이션 정보도 복원됩니다.  

## <a name="integrating-custom-deployment-code-into-mdt"></a>MDT에 사용자 지정 배포 코드 통합  
 일반적으로 배포 팀에는 Deployment 워크벤치의 미리 정의된 작업 순서 동작 또는 기본 MDT 구성 파일에서 충족되지 않는 대상 환경 특정의 복잡한 요구 사항이 있습니다. 이 경우 해당 요구 사항에 맞게 사용자 지정 코드를 구현합니다.  

 MDT에 사용자 지정 배포 코드를 통합하려면 다음을 수행합니다.  

-   [적절한 스크립팅 언어 선택](#ChooseAppropLanguage)에서 설명한 대로 스크립팅 언어를 선택합니다.  

-   [ZTIUtility 활용 방법 이해](#UnderstandLeverageZTI)에서 설명한 대로 ZTIUtility.vbs를 활용합니다.  

-   [사용자 지정 배포 코드 통합](#IntegrateCustomDeploy)에서 설명한 대로 사용자 지정 배포 코드를 통합합니다.  

 다음 섹션에서는 MDT가 배포 서버에 구성되어 있다고 가정합니다.  

###  <a name="ChooseAppropLanguage"></a> 적절한 스크립팅 언어 선택  
 Windows 또는 Windows PE에서 실행될 수 있는 코드는 애플리케이션 설치 또는 MDT 작업 순서 단계를 통해 호출할 수 있지만 .vbs 또는 .wsf 파일 형식의 스크립트를 사용하는 것이 좋습니다.  

 .wsf 파일을 사용할 때의 이점은 이미 ZTI 및 LTI 프로세스에서 사용하는 미리 정의된 일부 함수 외에도 기본 제공되는 로깅에 있습니다. 이러한 함수는 MDT와 함께 배포되는 ZTIUtility 스크립트에서 사용할 수 있습니다.  

 ZTIUtility 스크립트는 사용자 지정 스크립트에서 참조될 때 MDT 환경과 설치 클래스를 초기화합니다. 사용할 수 있는 클래스는 다음과 같습니다.  

-   **Logging**. 이 클래스는 모든 MDT 스크립트에서 사용하는 로깅 기능을 제공합니다. 또한 배포 중에 실행되는 각 스크립트에 대한 단일 로그 파일과 모든 스크립트에 대한 통합된 로그 파일을 만듭니다. 이러한 로그 파일은 TRACE32에서 읽을 수 있도록 설계된 형식으로 만들어집니다. 이 도구는 [System Center Configuration Manager 2007 Toolkit V2](https://www.microsoft.com/download/en/details.aspx?id=9257)에서 사용할 수 있습니다.  

-   **Environment**. 이 클래스는 WMI 및 MDT 규칙 처리를 통해 수집된 환경 변수를 구성하고 스크립트에서 직접 참조할 수 있게 합니다. 이렇게 하면 배포 속성을 읽을 수 있으므로 ZTI 및 LTI 프로세스에서 사용하는 모든 구성 정보에 액세스할 수 있습니다.  

-   **Utility**. 이 클래스는 ZTI 및 LTI 스크립트 전체에 사용되는 일반 유틸리티를 제공합니다. 사용자 지정 코드가 개발될 때마다 이 클래스를 검토하여 코드를 단순히 다시 사용할 수 있는지 확인하는 것이 좋습니다. 이 클래스에서 제공되는 일부 기능에 대한 추가 정보는 이 섹션의 뒷부분에 나와 있습니다.  

-   **Database**. 이 클래스는 데이터베이스에 연결하고 데이터베이스에서 정보를 읽는 것과 같은 함수를 수행합니다. 일반적으로 데이터베이스 클래스에 직접 액세스하는 것은 권장되지 않습니다. 대신 데이터베이스 조회를 수행하는 데 규칙 처리를 사용해야 합니다.  

-   **Strings**. 이 클래스는 구분된 항목 목록 만들기, 16진수 값 표시, 문자열에서 공백 제거, 문자열 오른쪽 맞춤, 문자열 왼쪽 맞춤, 문자열 정렬, 값을 문자열 형식으로 강제 적용, 값을 배열 형식으로 강제 적용, 임의의 GUID(Globally Unique Identifier) 생성 및 Base64 변환과 같은 일반적인 문자열 처리 루틴을 수행합니다.  

-   **FileHandling**. 이 클래스는 경로 정규화, 파일 및 폴더 복사, 이동 및 삭제와 같은 함수를 수행합니다.  

-   **clsRegEx**. 이 클래스는 정규식 함수를 수행합니다.  

 MDT에서 클라이언트 Microsoft VBScript(Visual Basic® Scripting Edition)를 더 강력하고 신뢰할 수 있게 만들기 위해 몇 가지 변경 내용이 스크립트 아키텍처에 구현되었습니다. 이러한 변경 내용은 다음과 같습니다.  

-   새 API 및 향상된 오류 처리를 포함하여 ZTIUtility.vbs(주 스크립트 라이브러리)에 대한 광범위한 변경  

-   ZTI_*xxx*.wsf 스크립트의 전체 구조에 대한 새로운 관점  

 MDT 스크립트의 전체 구조도 변경되었습니다. 대부분의 MDT 스크립트는 이제 VBScript **Class** 개체 내에 캡슐화됩니다. 클래스는 **RunNewInstance** 함수로 초기화되고 호출됩니다.  

> [!NOTE]
>  대부분의 MDT 스크립트에 ZTIUtility.vbs가 포함되어 있으므로 ZTIUtility.vbs가 광범위하게 변경되는 경우에도 대부분의 기존 MDT 2008 업데이트 1 스크립트는 MDT에서 있는 그대로 작동합니다.  

###  <a name="UnderstandLeverageZTI"></a> ZTIUtility 활용 방법 이해  
 ZTIUtility.vbs 파일에는 사용자 지정 코드에서 활용할 수 있는 개체 클래스가 포함되어 있습니다. 다음을 사용하여 MDT와 사용자 지정 코드를 통합합니다.  

-   [ZTIUtility Logging 클래스 사용](#UseZTILogging)에서 설명한 대로 ZTIUtility.vbs에 정의된 Logging 클래스  

-   [ZTIUtility Environment 클래스 사용](#UseZTIEnvironment)에서 설명한 대로 ZTIUtility.vbs에 정의된 Environment 클래스  

-   [ZTIUtility Utility 클래스 사용](#UseZTIUtility)에서 설명한 대로 ZTIUtility.vbs에 정의된 Utility 클래스  

####  <a name="UseZTILogging"></a> ZTIUtility Logging 클래스 사용  
 ZTIUtiliy.vbs의 Logging 클래스는 사용자 지정 코드가 ZTI 또는 LTI 배포 중에 다른 스크립트와 동일한 방식으로 상태 정보, 경고 및 오류를 기록하는 간단한 메커니즘을 제공합니다. 또한 이 표준화는 **LTI 배포 요약** 대화 상자에서 실행되는 사용자 지정 코드의 상태를 올바르게 보고하도록 합니다.  

 다음은 **oLogging.CreateEntry** 및 **TestAndFail** 함수를 사용하여 다양한 스크립트 작업의 결과에 따라 다양한 유형의 메시지를 기록하는 사용자 지정 코드 스크립트 예제를 보여 줍니다.  

 **ZTIUtility Logging을 사용한 스크립트 예제: ZTI_Example.wsf**  

```  
<job id="ZTI_Example">  
<script language="VBScript" src="ZTIUtility.vbs"/>  
<script language="VBScript">  

' //*******************************************************  
' //  
' // Copyright (c) Microsoft Corporation.  All rights reserved  
' // Microsoft Deployment Toolkit Solution Accelerator  
' // File: ZTI_Example.wsf  
' //  
' // Purpose: Example of scripting with the  
' //          Microsoft Deployment Toolkit.  
' //  
' // Usage: cscript ZTI_Example.wsf [/debug:true]  
' //  
' //*******************************************************  

Option Explicit  
RunNewInstance  

'//--------------------------------------------------------  
'// Main Class  
'//--------------------------------------------------------  
Class ZTI_Example  

'//--------------------------------------------------------  
'// Main routine  
'//--------------------------------------------------------  

Function Main()  

  Dim iRetVal  
  Dim sScriptPath  

  iRetVal = SUCCESS  

  oLogging.CreateEntry "Begin example script…", _  
    LogTypeInfo  

  ' %ServerA% is a generic variable available within  
  ' every CustomSettings.ini file.  

  sScriptPath = "\\" & oEnvironment.Item("ServerA") & _  
    "\public\products\Applications\User\Technet\USEnglish"  

  ' Validate a connection to server, net connect with  
  ' credentials if necessary.  
  iRetVal = oUtility.ValidateConnection( sScriptPath )  
  TestAndFail iRetVal, 9991, "Validate Connection to [" & _  
    sScriptPath & "]"  

  'Run Setup Program  

  iRetVal = oUtility.RunWithHeartbeat( """" & _  
    sScriptPath & "\setup.exe"" /?" )  
  TestAndFail iRetVal, 9991, "RunWithHeartbeat [" & _  
    sScriptPath & "]"  

  'Perform any cleanup from installation process  

  oShell.RegWrite "HKLM\Software\Microsoft\SomeValue", _  
    "Done with Execution of XXX.", "REG_SZ"  

  Main = iRetVal  

End Function  

End Class  

</script>  
</job>  
```  

> [!NOTE]
>  **ZTIProcess()** 를 호출하는 스크립트를 **ProcessResults()** 와 함께 계속 사용하려면 그렇게 계속 사용할 수 있습니다. 그러나 향상된 오류 처리 기능 중 일부는 사용할 수 없게 됩니다.  

####  <a name="UseZTIEnvironment"></a> ZTIUtility Environment 클래스 사용  
 ZTIUtiliy.vbs의 Environment 클래스는 MDT 속성에 대한 액세스와 업데이트 기능을 제공합니다. 앞의 예제에서 **oEnvironment.Item("Memory")** 은 사용 가능한 RAM의 크기를 검색하는 데 사용됩니다. 또한 *Toolkit 참조* MDT 문서에 설명된 속성의 값을 검색하는데도 사용할 수 있습니다.  

####  <a name="UseZTIUtility"></a> ZTIUtility Utility 클래스 사용  
 ZTIUtility.vbs 스크립트에는 사용자 지정 배포 스크립트에서 일반적으로 사용할 수 있는 다양한 유틸리티가 포함되어 있습니다. 이러한 유틸리티는 **oLogging** 및 **oEnvironment** 클래스와 동일한 방식으로 모든 스크립트에 추가할 수 있습니다.  

다음 표에서는 사용 가능한 몇 가지 유용한 함수와 해당 출력에 대해 자세히 설명합니다. 사용 가능한 함수의 전체 목록은 ZTIUtility.vbs 파일을 참조하세요.  

|**함수**|**출력**|  
|-|-|
|**oUtility.LocalRootPath**|대상 컴퓨터에서 배포 프로세스에 사용되는 루트 폴더의 경로를 반환합니다. 예: C:\MININT|  
|**oUtility.BootDevice**|시스템 부팅 디바이스를 반환합니다. 예: MULTI(0)DISK(0)RDISK(0)PARTITION(1)|  
|**oUtility.LogPath**|배포 중에 사용되는 로그 폴더의 경로를 반환합니다. 예: C:\MININT\SMSOSD\OSDLOGS|  
|**oUtility.StatePath**|현재 구성된 상태 저장소의 경로를 반환합니다. 예: C:\MININT\StateStore|  
|**oUtility.ScriptName**|함수를 호출하는 스크립트의 이름을 반환합니다. 예: Z-RAMTest|  
|**oUtility.ScriptDir**|함수를 호출하는 스크립트의 경로를 반환합니다. 예: \\\server_name\Deployment$\Scripts|  
|**oUtility.ComputerName**|빌드 프로세스 중에 사용할 컴퓨터 이름을 결정합니다. 예: computer_name|  
|**oUtility.ReadIni(file, section, item)**|지정된 항목을 .ini 파일에서 읽을 수 있도록 합니다.|  
|**oUtility.WriteIni(file, section, item, value)**|지정된 항목을 .ini 파일에 쓸 수 있도록 합니다.|  
|**oUtility.Sections(file)**|.ini 파일의 섹션을 읽고 이 섹션을 참조용으로 개체에 저장합니다.|  
|**oUtility.SectionContents(file, section)**|지정된 .ini 파일의 내용을 읽고 이 내용을 개체에 저장합니다.|  
|**oUtility.RunWithHeartbeat(sCmd)**|명령이 실행되면 0.5초마다 하트비트 정보를 로그에 기록합니다|  
|**oUtility.FindFile**<br /><br /> **(sFilename,sFoundPath)**|Servicing, USMT, Templates, Scripts 및 Control을 포함하여 DeployRoot 폴더와 표준 하위 폴더에 지정된 파일을 검색합니다.|  
|**oUtility.findMappedDrive(sServerUNC)**|드라이브가 지정된 UNC 경로에 매핑되어 있는지 확인하고 드라이브 문자를 반환합니다.|  
|**oUtility.ValidateConnection(sServerUNC)**|지정된 서버에 대한 기존 연결이 있는지 여부를 확인하고, 없는 경우 새 연결을 만들려고 시도합니다.|  
|**MapNetworkDrive**<br /><br /> **(sShare, SDomID, sDomPwd)**|드라이브 문자를 공유로 지정된 UNC 경로에 매핑하고, 사용된 드라이브 문자를 반환합니다. 실패하는 경우 오류를 반환합니다.|  
|**VerifyPathExists(strPath)**|지정된 경로가 있는지 여부를 확인합니다.|  
|**oEnvironment.Substitute(sVal)**|문자열이 지정되면 해당 문자열 내의 모든 변수 또는 함수를 확장합니다.|  
|**oEnvironment.Item**<br /><br /> **(sName)**|영구 저장소에서 변수를 읽거나 씁니다.|  
|**oEnvironment.Exists**<br /><br /> **(sName)**|변수가 있는지 여부를 테스트합니다.|  
|**oEnvironment.ListItem**<br /><br /> **(sName)**|영구 저장소에서 **배열** 형식의 변수를 읽거나 씁니다.|  
|**oLogging.ReportFailure**<br /><br /> **(sMessage, iError)**|복구할 수 없는 오류가 검색되는 경우 구조적 종료를 수행하는 데 사용됩니다.|  
|**oLogging.CreateEvent**<br /><br /> **(iEventID, iType, sMessage, arrParms)**|로그 파일에 메시지를 쓰고 이벤트를 정의된 서버에 게시합니다.|  
|**oLogging.CreateEntry**<br /><br /> **(sLogMsg, iType)**|로그 파일에 메시지를 씁니다.|  
|**TestAndFail(iRc, iError, sMessage)**|**iRc**가 거짓이거나 실패하는 경우 **iError**를 사용하여 스크립트를 종료합니다.|  
|**TestAndLog(iRc , sMessage)**|**iRc**가 거짓이거나 실패하는 경우에만 경고를 기록합니다.|  

###  <a name="IntegrateCustomDeploy"></a> 사용자 지정 배포 코드 통합  
 사용자 지정 배포 코드는 여러 가지 방법으로 MDT 프로세스에 통합될 수 있습니다. 그러나 사용된 방법에 관계없이 다음 두 가지 규칙을 충족해야 합니다.  

-   사용자 지정 배포 코드 스크립트 이름은 항상 Z 문자로 시작해야 합니다.  

-   사용자 지정 배포 코드는 배포 공유의 Scripts 폴더에 배치해야 합니다(예: D:\Production Deployment Share\Scripts).  

 또한 일관된 로깅을 보장하는 사용자 지정 코드를 통합하는 데 가장 자주 사용되는 방법은 다음과 같습니다.  

-   MDT 애플리케이션으로 코드 배포  

-   MDT 작업 순서 명령으로 코드 시작  

-   사용자 종료 스크립트로 코드 시작  

#### <a name="deploy-custom-code-as-an-mdt-application"></a>MDT 애플리케이션으로 사용자 지정 코드 배포  
 사용자 지정 배포 코드는 Deployment 워크벤치로 가져와 다른 애플리케이션과 동일한 방식으로 관리할 수 있습니다.  

 **사용자 지정 배포 코드를 실행하는 새 응용 프로그램을 만들려면**  

1.  사용자 지정 배포 코드를 *deployment_share*\Scripts 폴더에 복사합니다. 여기서 *deployment_share*는 배포 공유에 대한 정규화된 경로입니다.  

2.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

3.  Deployment 워크벤치 콘솔 트리에서 Deployment Shares/*deployment_share*/Applications로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

4.  [작업] 창에서 **새 애플리케이션**을 클릭합니다.  

     새 애플리케이션 마법사가 시작됩니다.  

5.  다음 정보를 사용하여 새 애플리케이션 마법사를 완성합니다. 달리 지정하지 않으면 기본값을 적용합니다.  

    |**마법사 페이지**|**수행할 작업**|  
    |-|-|  
    |**응용 프로그램 종류**|**원본 파일이 없는 응용 프로그램 또는 네트워크의 다른 위치**를 클릭하고, **다음**을 클릭합니다.|  
    |**세부 정보**|애플리케이션의 정보에 따라 이 페이지를 완성하고 **다음**을 클릭합니다.|  
    |**명령 정보**|1.  **명령줄** 상자에서 **cscript.exe %SCRIPTROOT%\custom_code**를 입력합니다. 여기서 *custom_code*는 개발된 사용자 지정 코드의 이름입니다.<br />2.  **작업 디렉터리** 상자에서 ***working_directory***를 입력합니다. 여기서 working_directory는 사용자 지정 코드의 작업 디렉터리 이름이며, 일반적으로 **명령줄** 상자에 지정된 것과 동일한 폴더입니다.<br />3.  **다음**을 클릭합니다.|  
    |**요약**|구성 설정이 올바른지 확인하고, **다음**을 클릭합니다.|  
    |**확인**|**마침**을 클릭합니다.|  

 애플리케이션이 Deployment 워크벤치의 애플리케이션 노드에 표시됩니다.  

#### <a name="add-the-custom-code-as-a-task-sequence-step"></a>사용자 지정 코드를 작업 순서 단계로 추가  
 사용자 지정 배포 코드는 작업 순서 내의 임의의 지점에서 직접 호출할 수 있습니다. 이렇게 하면 일반적인 작업 순서 규칙 및 옵션에 액세스할 수 있습니다.  

 **기존 작업 순서에 사용자 지정 배포 코드를 추가하려면**  

1.  사용자 지정 배포 코드를 *deployment_share*\Scripts 폴더에 복사합니다. 여기서 *deployment_share*는 배포 공유에 대한 정규화된 경로입니다.  

2.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

3.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share/Task Sequences*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

4.  세부 정보 창에서 ***task_sequence***를 클릭합니다. 여기서 *task_sequence*는 사용자 지정 코드를 실행하는 작업 순서의 이름입니다.  

5.  [작업] 창에서 **속성**을 클릭합니다.  

6.  ***task_sequenceProperties*** 대화 상자에서 **작업 순서**를 클릭합니다.  

7.  콘솔 트리에서 *group*으로 이동합니다. 여기서 *group*은 작업 순서 단계를 추가할 그룹입니다.  

8.  **추가**, **일반**, **명령줄 실행**을 차례로 클릭합니다.  

9. 콘솔 트리에서 **명령줄 실행**을 클릭한 다음, **속성** 탭을 클릭합니다.  

10. **이름** 상자에서 ***이름***을 입력합니다. 여기서 *이름*은 사용자 지정 코드를 설명하는 이름입니다.  

11. **속성** 탭의 **명령줄** 상자에서 ***command_line***을 입력합니다. 여기서 *command_line*은 사용자 지정 코드를 실행하는 명령입니다(예: **cscript.exe %SCRIPTROOT%\CustomCode.vbs**).  

12. **시작 위치** 상자에서 ***path***(여기서*path*는 사용자 지정 코드의 작업 폴더에 대한 정규화된 경로이며, 일반적으로 **명령줄** 상자에 지정된 경로와 동일함)를 입력한 다음, **확인**을 클릭합니다.  

 새로 만든 작업 순서 단계가 작업 순서 단계 목록에 표시됩니다.  

#### <a name="run-custom-code-as-a-user-exit-script"></a>사용자 지정 코드를 사용자 종료 코드로 실행  
 **UserExit** 지시문을 사용하여 CustomSettings.ini의 사용자 지정 스크립트를 사용자 종료 스크립트로 실행할 수도 있습니다. 이는 CustomSettings.ini 규칙 유효성 검사 프로세스에 정보를 전달하는 메커니즘을 제공하며 MDT 속성의 동적 업데이트를 제공합니다.  

 사용자 종료 스크립트 및 **UserExit** 지시문에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "CustomSettings.ini 파일의 사용자 종료 스크립트" 섹션을 참조하세요.  

## <a name="installing-device-drivers-using-various-installation-methods"></a>다양한 설치 방법을 사용하여 디바이스 드라이버 설치  
 이 시나리오에서는 MDT를 사용하여 여러 종류의 하드웨어에 운영 체제를 배포합니다. 배포 프로세스의 일환으로 각 하드웨어 종류가 제대로 작동하도록 디바이스 드라이버를 확인하고 설치합니다. 디바이스 드라이버에는 두 가지 주요 유형이 있으며, 각각은 배포 프로세스 중에 다르게 처리되어야 합니다.  

-   디바이스 드라이버를 Deployment 워크벤치로 가져오는 데 사용할 수 있는 .inf 파일이 포함된 디바이스 드라이버  

-   응용 프로그램으로 패키지되고 설치되어야 하는 디바이스 드라이버  

 MDT를 사용하면 운영 체제 배포의 일부로 두 유형의 드라이버를 모두 처리할 수 있습니다.  

 디바이스 드라이버를 설치하려면 다음을 수행합니다.  

-   [장치 드라이버를 설치하는 데 사용할 방법 결정](#WhichMethodtoInstallDriver)에서 설명한 대로 각 장치 드라이버를 설치하는 방법을 결정합니다.  

-   [기본 제공 드라이버 방법을 사용하여 장치 드라이버 설치](#InstallOutofBoxDrivers)에서 설명한 대로 기본 제공 드라이버 방법을 사용합니다.  

-   [응용 프로그램으로 장치 드라이버 설치](#InstallDriversasApplications)에서 설명한 대로 장치 드라이버를 응용 프로그램으로 설치합니다.  

 이 시나리오에서는 MDT가 배포 서버에서 실행되고 있다고 가정합니다.  

###  <a name="WhichMethodtoInstallDriver"></a> 장치 드라이버를 설치하는 데 사용할 방법 결정  
 하드웨어 제조업체는 다음 두 가지 형식 중 하나로 디바이스 드라이버를 출시합니다.  

-   압축을 풀 수 있고 드라이버를 Deployment 워크벤치에 가져오는 데 사용되는 .inf 파일이 포함된 패키지  

-   기존 애플리케이션 설치 프로세스를 사용하여 설치해야 하는 애플리케이션  

 .inf 파일에 액세스하기 위해 추출할 수 있는 디바이스 드라이버 패키지는 먼저 Deployment 워크벤치의 기본 제공 노드에 드라이버를 가져와서 MDT 자동 드라이버 검색 및 설치 프로세스를 사용할 수 있습니다.  

 .inf 파일을 격리하기 위해 추출할 수 없거나 처음에 응용 프로그램 설치 관리자(예: MSI 또는 Setup.exe 파일)를 통해 설치하지 않아 제대로 작동하지 않는 디바이스 드라이버 패키지는 MDT 설치 응용 프로그램 기능을 사용하고 일반적인 응용 프로그램과 마찬가지로 배포 프로세스 중에 디바이스 드라이버를 설치할 수 있습니다.  

###  <a name="InstallOutofBoxDrivers"></a> 기본 제공 드라이버 방법을 사용하여 장치 드라이버 설치  
 .inf 파일이 포함된 디바이스 드라이버 패키지는 Deployment 워크벤치로 가져와서 배포 프로세스의 일부로 자동으로 설치할 수 있습니다. 이 유형의 디바이스 드라이버 배포를 구현하려면 먼저 디바이스 드라이버를 Deployment 워크벤치에 추가합니다.  

 **Deployment 워크벤치에 장치 드라이버를 추가하려면**  

1.  배포할 하드웨어 종류에 필요한 디바이스 드라이버를 다운로드하고 디바이스 드라이버 패키지를 임시 위치에 추출합니다.  

2.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

3.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Out-of-Box Drivers로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

4.  [작업 ]창에서 **드라이버 가져오기**를 클릭합니다.  

     디바이스 드라이버 가져오기 마법사가 시작됩니다.  

5.  **디렉터리 지정** 페이지의 **드라이브 원본** 디렉터리 섹션에서 **찾아보기**를 클릭하여 새 장치 드라이버가 포함된 폴더로 이동하고, **다음**을 클릭합니다.  

    > [!NOTE]
    >  새 디바이스 드라이버 마법사에서 드라이버 원본 디렉터리의 모든 하위 디렉터리를 검색합니다. 따라서 설치할 드라이버가 여러 개인 경우, 동일한 루트 디렉터리 내의 폴더로 압축을 풀고, 드라이버 원본 디렉터리를 모든 드라이버 원본 폴더를 포함하는 루트 디렉터리로 설정합니다.  

6.  **요약** 페이지에서 설정이 올바른지 확인하고 **다음**을 클릭하여 드라이버를 Deployment 워크벤치로 가져옵니다.  

7.  **확인** 페이지에서 **마침**을 클릭합니다.  

 디바이스 드라이버에 대용량 저장소 또는 네트워크 클래스 드라이버와 같은 부팅 필요 드라이버가 포함된 경우, 새 드라이버가 포함된 새로운 LiteTouch_x86 및 LiteTouch_x64 부팅 환경을 생성하려면 배포 공유를 다음에 업데이트해야 합니다.  

 **LiteTouch Windows PE 이미지에 장치 드라이버를 추가하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

4.  **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

5.  **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

6.  **확인** 페이지에서 **마침**을 클릭합니다.  

###  <a name="InstallDriversasApplications"></a> 응용 프로그램으로 장치 드라이버 설치  
 응용 프로그램으로 패키지되고 드라이버 파일과 .inf 파일이 포함된 폴더로 추출할 수 없는 디바이스 드라이버는 배포 프로세스 중에 설치할 응용 프로그램으로 Deployment 워크벤치에 추가해야 합니다.  

 응용 프로그램은 작업 순서 단계로 지정되거나 CustomSettings.ini에 지정될 수 있습니다. 그러나 디바이스 드라이버 응용 프로그램은 디바이스가 있는 컴퓨터에서 작업 순서를 실행할 때만 설치해야 합니다. 이렇게 하려면 관련 디바이스 드라이버 응용 프로그램을 조건부 작업 순서 단계로 배포하기 위한 작업 순서 단계를 실행합니다. 조건부 기준은 대상 컴퓨터의 디바이스에 대한 WMI 쿼리를 사용하여 작업 순서 단계를 실행하도록 지정할 수 있습니다.  

#### <a name="add-the-device-driver-application-to-the-deployment-workbench"></a>Deployment 워크벤치에 디바이스 드라이버 응용 프로그램 추가  
 먼저 각 디바이스 드라이버 응용 프로그램을 Deployment 워크벤치로 가져와야 합니다.  

> [!NOTE]
>  **배포 마법사에서 이 응용 프로그램 숨기기** 확인란을 선택하거나 선택 취소하여 배포 중에 응용 프로그램의 **속성** 대화 상자에 응용 프로그램을 표시해야 하는지 여부를 구성합니다. 배포 중에 사용되는 각 디바이스 드라이버 응용 프로그램에 대해 이 프로세스를 반복합니다.  

 **Deployment 워크벤치에 장치 드라이버 응용 프로그램을 추가하려면**  

1.  디바이스 드라이버 응용 프로그램을 다운로드하여 임시 위치에 저장합니다.  

2.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

3.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Applications로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

4.  [작업] 창에서 **새 애플리케이션**을 클릭합니다.  

     새 애플리케이션 마법사가 시작됩니다.  

5.  **응용 프로그램 유형** 페이지에서 **원본 파일이 있는 응용 프로그램**을 클릭하고, **다음**을 클릭합니다.  

6.  **세부 정보** 페이지에서 응용 프로그램에 대한 관련 세부 정보를 입력하고, **다음**을 클릭합니다.  

7.  **원본** 페이지의 **원본 디렉터리** 섹션에서 **찾아보기**를 클릭하여 이동한 다음, 장치 드라이버 응용 프로그램 원본 파일이 포함된 디렉터리를 클릭합니다. **확인**을 클릭합니다.  

8.  **다음**을 클릭합니다.  

9. **대상** 페이지에서 대상 디렉터리에 대한 이름을 입력하고, **다음**을 클릭합니다.  

10. **명령 정보** 페이지의 **명령줄** 섹션에서 장치 드라이버 응용 프로그램의 자동 설치를 허용하는 명령을 입력합니다.  

11. **요약** 페이지에서 설정이 올바른지 확인하고 **다음**을 클릭하여 장치 드라이버 응용 프로그램을 Deployment 워크벤치로 가져옵니다.  

12. **확인** 페이지에서 **마침**을 클릭합니다.  

 애플리케이션을 Deployment 워크벤치로 가져온 후 올바른 하드웨어에서 실행될 때만 애플리케이션이 설치되도록 적절한 논리를 사용하여 배포 프로세스에 추가합니다. 이를 달성하기 위한 여러 가지 방법은 다음과 같습니다.  

-   디바이스 드라이버 응용 프로그램을 배포 작업 순서의 일부로 지정합니다.  

-   CustomSettings.ini에 디바이스 드라이버 응용 프로그램을 지정합니다.  

-   MDT DB에 디바이스 드라이버 응용 프로그램을 지정합니다.  

 다음 섹션에서는 각 방법에 대해 자세히 설명합니다.  

####  <a name="SpecifyDeviceAppTask"></a> 작업 순서의 일부로 장치 드라이버 응용 프로그램 지정  
 배포 프로세스에 디바이스 드라이버 응용 프로그램을 추가하기 위한 첫 번째 방법은 작업 순서를 사용하여 각 디바이스 드라이버 응용 프로그램에 대한 단계를 추가하는 것입니다.  

 작업 순서에서 디바이스 드라이버 응용 프로그램을 관리하는 두 가지 주요 방법은 다음과 같습니다.  

-   각 하드웨어 모델에 대해 새 작업 순서 그룹을 만든 다음, 컴퓨터가 특정 하드웨어 종류와 일치하는 경우 해당 작업 그룹을 실행하는 쿼리를 추가합니다.  

-   하드웨어 관련 애플리케이션에 대한 작업 순서 그룹을 만든 다음, 각 작업 순서 동작에 대한 쿼리를 추가하여 각 작업 순서 단계가 하드웨어 종류에 대해 평가되고 일치하는 항목이 있는 경우에만 실행됩니다.  

 **각 하드웨어 종류에 대한 새 작업 순서 그룹을 만들려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  세부 정보 창에서 ***task_sequence***를 클릭합니다. 여기서 *task_sequence*는 디바이스 드라이버 응용 프로그램을 설치하는 데 필요한 배포 작업 순서입니다.  

4.  [작업] 창에서 **속성**을 클릭합니다.  

5.  ***task_sequenceProperties*** 대화 상자에 있는 **작업 순서** 탭의 세부 정보 창에서 상태 복원/Windows 업데이트(사전 응용 프로그램 설치)로 이동합니다.  

6.  **작업 순서** 탭에서 **추가**를 클릭한 다음, **새 그룹**을 클릭합니다.  

     이렇게 하면 작업 순서에 새 작업 순서 그룹이 만들어집니다. 이 새 작업 순서 그룹을 사용하여 하드웨어 관련 디바이스 드라이버 응용 프로그램을 설치하는 단계를 만듭니다.  

7.  세부 정보 창에서 **새 그룹**을 클릭합니다.  

8.  **속성** 탭의 **이름** 상자에서 ***group_name***을 입력합니다. 여기서 *group_name*은 그룹의 이름입니다(예: *하드웨어 관련 응용 프로그램 - Dell Computer Corporation*).  

9. **옵션** 탭에서 **추가**를 클릭한 다음, **WMI 쿼리**을 클릭합니다.  

10. **작업 순서 WMI 조건** 대화 상자에서 다음 정보를 입력합니다.  

    -   **WMI 네임스페이스** 상자에서 **root\cimv2**를 입력합니다.  

    -   **WQL 쿼리** 상자에서 특정 응용 프로그램 종류에 대한 응용 프로그램만 설치되도록 **Win32_ComputerSystem** 클래스를 사용하여 WQL(WMI Query Language) 쿼리를 입력합니다. 예를 들어 다음과 같습니다.  

         **Select \* FROM Win32_ComputerSystem WHERE Model LIKE *%hardware_model%* AND Manufacturer LIKE *%hardware_manufacturer%***  

         이 예제에서 *hardware_model*은 컴퓨터 모델의 이름(예: Latitude D620)이고, *hardware_manufacturer*는 컴퓨터 제조업체의 이름(예: Dell Corporation)입니다.  

         **%** 기호는 관리자가 ***hardware_model*** 또는 ***hardware_manufacturer***에 대해 지정된 값이 포함된 컴퓨터 모델 또는 제조업체를 반환할 수 있도록 이름에 포함되는 와일드카드 문자입니다.  

     WMI 및 WQL 쿼리에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서의 "작업 순서 단계 조건에 WMI 쿼리 추가" 섹션 및 [WQL을 사용하여 쿼리](http://msdn.microsoft.com/library/aa392902.aspx)를 참조하세요.  

11. **확인**을 클릭하여 쿼리를 제출한 다음, **확인**을 클릭하여 작업 순서에 대한 변경 내용을 제출합니다.  

> [!NOTE]
>  이 프로세스는 설치할 각 디바이스 드라이버 응용 프로그램의 각 하드웨어 종류에 대해 반복해야 합니다.  

 하드웨어 관련 작업 순서 그룹이 만들어지면 디바이스 드라이버 응용 프로그램을 각 그룹에 추가할 수 있습니다.  

 **하드웨어 관련 작업 순서 그룹에 장치 드라이버 응용 프로그램을 추가하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  세부 정보 창에서 ***task_sequence***를 클릭합니다. 여기서 *task_sequence*는 디바이스 드라이버 응용 프로그램을 설치하는 데 필요한 배포 작업 순서입니다.  

4.  [작업] 창에서 **속성**을 클릭합니다.  

5.  ***task_sequenceProperties*** 대화 상자에서 **작업 순서**를 클릭합니다.  

6.  세부 정보 창에서 상태 복원/*hardware_specific_group*으로 이동합니다. 여기서 *hardware_specific_group*은 디바이스 드라이버 응용 프로그램을 설치하기 위해 작업 순서 단계가 추가될 하드웨어 관련 그룹의 이름입니다.  

7.  **작업 순서** 탭에서 **추가**, **일반**, **응용 프로그램 설치**를 차례로 클릭합니다.  

     **응용 프로그램 설치** 작업 순서 단계가 세부 정보 창에 표시됩니다.  

8.  세부 정보 창에서 **애플리케이션 설치**를 클릭합니다.  

9. **속성** 탭에서 **단일 응용 프로그램 설치**를 클릭하고, **응용 프로그램 설치** 목록에서 ***hardware_application***을 선택합니다. 여기서 *hardware_application*은 하드웨어 관련 응용 프로그램을 설치하는 응용 프로그램입니다.  

> [!NOTE]
>  이 프로세스는 배포 중에 사용해야 하는 각 디바이스 드라이버 응용 프로그램에 대해 반복해야 합니다.  

#### <a name="specify-the-device-driver-application-in-customsettingsini"></a>CustomSettings.ini에 디바이스 드라이버 응용 프로그램 지정  
 LTI 또는 ZTI 배포가 시작되면 완료할 첫 번째 작업 중 하나는 BootStrap.ini 및 CustomSettings.ini 제어 파일을 처리하는 것입니다. 이러한 파일에는 모두 배포를 동적으로 사용자 지정하는 데 사용할 수 있는 규칙이 포함되어 있습니다.  

 MDT에서 CustomSettings.ini 파일을 처리하는 방식으로 인해 특정 조건에 따라 애플리케이션을 추가하는 데 사용할 수 있습니다. 이 논리는 특정 하드웨어 종류에 따라 배포하는 동안 디바이스 드라이버 관련 응용 프로그램을 추가하는 데 사용됩니다. 애플리케이션은 CustomSettings.ini에서 배포 공유의 Applications.xml 파일에 있는 애플리케이션의 GUID를 통해 참조됩니다.  

 **가져온 응용 프로그램의 GUID를 찾으려면**  

1.  배포 서버의 배포 공유에서 Control 폴더(예: D:\Production Deployment Share\Control)를 엽니다.  

2.  Application.xml 파일을 찾아서 엽니다.  

3.  필요한 애플리케이션을 찾습니다.  

4.  애플리케이션 `<guid>` 태그를 묶은 줄(예: `<application guid={c303fa6e-3a4d-425e-8102-77db9310e4d0}>`)을 찾아 애플리케이션 GUID를 찾습니다.  

 초기화 프로세스의 일환으로 LTI 및 ZTI 프로세스는 모두 실행 중인 컴퓨터에 대한 정보를 수집합니다. 이 프로세스의 일부로 WMI 쿼리가 수행되고, 제조업체와 모델에 대한 **Win32_ComputerSystem** 클래스의 값이 각각 **%Make%** 및 **%Model%** 변수로 채워집니다.  

 CustomSettings.ini 파일을 처리하는 동안 이러한 값을 사용하여 검색된 제조업체와 모델에 따라 파일의 섹션을 동적으로 읽을 수 있습니다.  다음 샘플에서는 CustomSettings.ini 파일의 예제를 보여 줍니다.  

 **하드웨어 관련 응용 프로그램을 설치하도록 구성된 CustomSettings.ini 예제**  

```  
[Settings]  
Priority=Make, Default  
Properties=MyCustomProperty  

[Default]  
OSInstall=Y  

[Dell Computer Corporation]  
Subsection=Dell-%Model%  

[Dell-Latitude D620]  
MandatoryApplications001={1D7DF331-47B7-472C-87B3-442597EC2F7D}  

[Dell-Latitude D610]  
MandatoryApplications001={c303fa6e-3a4d-425e-8102-77db9310e4d0}  
```  

 다음 속성을 사용하여 애플리케이션을 CustomSettings.ini에 지정합니다.  

-   **Applications**. 배포 관리자가 CustomSettings.ini에서 **SkipApplications=YES**를 지정하여 배포 프로세스의 일부로 애플리케이션 마법사를 표시하지 않으려는 경우에 이 속성을 사용할 수 있습니다.  

-   **MandatoryApplications**. 배포 관리자가 배포 중에 애플리케이션 마법사를 표시하여 배포 엔지니어가 배포 중에 추가 애플리케이션을 선택할 수 있도록 하려는 경우에 이 속성을 사용할 수 있습니다.  

     **MandatoryApplications** 속성(예: **SkipApplications=NO**) 없이 응용 프로그램 마법사를 사용하면 **Applications** 속성으로 지정된 응용 프로그램을 덮어쓰게 됩니다.  

     이전 샘플에서는 **%Make%** 및 **%Model%** 변수 값을 사용하여 애플리케이션 목록을 작성하는 방법을 동적으로 조작하는 방법을 보여 줍니다. 각 하드웨어 종류의 제조업체 및 모델에 대한 값은 다음 방법 중 하나를 사용하여 찾을 수 있습니다.  

-   **시스템 정보 도구**. 이 도구의 시스템 요약 노드를 사용하여 **시스템 제조업체**(make) 및 **시스템 모델**(model)을 식별합니다.  

-   **Windows PowerShell**. **Get-WMIObject –class Win32_ComputerSystem** cmdlet을 사용하여 컴퓨터의 제조업체와 모델을 결정합니다.  

-   **Windows Management Instrumentation 명령줄**. **CSProduct Get Name, Vendor**를 사용하여 컴퓨터의 이름(model) 및 공급업체(make)를 반환합니다.  

 **하드웨어 관련 논리를 추가하도록 CustomSettings.ini를 수정하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **규칙** 탭을 클릭합니다.  

5.  이 탭에 입력한 정보는 CustomSettings.ini 파일에 저장됩니다. [작업 순서의 일부로 장치 드라이버 응용 프로그램 지정](#SpecifyDeviceAppTask)에서 설명한 대로 장치 드라이버 관련 응용 프로그램이 있는 각 하드웨어 모델에 대한 논리를 추가하도록 CustomSettings.ini 파일 항목을 수정합니다.  

6.  **확인**을 클릭하여 변경 내용을 제출합니다.  

7.  세부 정보 창에서 *deployment_share*를 클릭합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

8.  [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

9. **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

10. **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

11. **확인** 페이지에서 **마침**을 클릭합니다.  

 기본적으로 사용 가능한 모든 애플리케이션은 LTI 배포 중에 Windows 배포 마법사에 표시됩니다. 디바이스 드라이버 관련 응용 프로그램은 특정 하드웨어 종류에만 적용되므로 항상 표시되지 않을 수도 있습니다. CustomSettings.ini에 디바이스 드라이버 관련 응용 프로그램 패키지를 지정하면, 응용 프로그램 구성의 **배포 마법사에서 응용 프로그램 숨기기** 옵션을 사용하여 응용 프로그램을 숨길 수 있습니다.  

 **배포 마법사에서 응용 프로그램을 숨기려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Applications로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  세부 정보 창에서 ***device_driver_application***을 클릭합니다. 여기서 *device_driver_application*은 배포 마법사에서 숨길 애플리케이션입니다.  

4.  [작업] 창에서 **속성**을 클릭합니다.  

5.  **일반** 탭에서 **배포 마법사에서 응용 프로그램 숨기기** 확인란을 선택합니다.  

6.  **적용**을 클릭한 다음, **속성** 대화 상자를 닫습니다.  

#### <a name="specify-the-device-driver-application-in-the-mdt-db"></a>MDT DB에 디바이스 드라이버 응용 프로그램 지정  
 MDT DB는 CustomSettings.ini 파일의 데이터베이스 버전이며, 배포 중에 사용할 정보를 배포 시에 쿼리할 수 있습니다. MDT DB를 사용하는 방법에 대한 자세한 내용은 "구성 설정을 적용하는 방법 선택"을 참조하세요.  

 배포 시 MDT DB를 쿼리하는 경우 대상 컴퓨터를 식별하는 데 다음 세 가지 방법을 사용할 수 있습니다.  

-   개별 컴퓨터를 검색합니다(MAC 주소, 자산 태그 또는 유사 항목 사용).  

-   컴퓨터의 위치를 검색합니다(기본 게이트웨이 사용).  

-   WMI 제조업체(make) 및 모델 쿼리를 사용하여 컴퓨터의 제조업체 및 모델을 검색합니다.  

 만든 각 데이터베이스 항목에 대해 배포 속성, 애플리케이션, Configuration Manager 패키지 사용 여부 및 관리자를 지정할 수 있습니다. 데이터베이스에 제조업체 및 모델 항목을 만들면 필요한 하드웨어 관련 디바이스 드라이버 응용 프로그램을 추가할 수 있습니다.  

 **장치 드라이버 응용 프로그램을 설치할 수 있도록 MDT DB에 항목을 만들려면**  

> [!NOTE]
>  디바이스 드라이버 응용 프로그램이 필요한 각 하드웨어 제조업체 및 모델에 대해 이 프로세스를 반복합니다.  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/**deployment_share**/Advanced Configuration/Database/Make and Model로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **새로 만들기**를 클릭합니다.  

4.  **속성** 대화 상자에 있는 **ID** 탭의 **제조업체** 상자에서 ***make_name***을 입력합니다. 여기서 *make_name*은 대상 컴퓨터의 제조업체와 연결하는 데 쉽게 식별되는 이름입니다.  

5.  **모델** 상자에 ***model_name***을 입력합니다. 여기서 *model_name*은 대상 컴퓨터의 모델과 연결하는 데 쉽게 식별되는 이름입니다.  

6.  **응용 프로그램** 탭에서 해당 하드웨어 모델에 필요한 각 장치 드라이버 응용 프로그램을 추가합니다.  

## <a name="initiating-mdt-using-windows-deployment-services"></a>Windows 배포 서비스를 사용하여 MDT 시작  
 Windows Server 2008에서는 Windows 배포 서비스를 Windows Server 2003 SP2의 기본 배포 도구인 원격 설치 서비스의 업데이트되고 다시 디자인된 버전으로 사용합니다. Windows 배포 서비스를 사용하면 컴퓨터의 PXE 지원 네트워크 어댑터 또는 부팅 미디어를 사용하여 네트워크를 통해 Windows 운영 체제, 특히 Windows 7, Windows Server 2008 이상 운영 체제를 배포할 수 있습니다.  

 Windows 배포 서비스를 배포하기 전에 다음 통합 옵션 중에서 사용자 환경에 가장 적합한 옵션을 결정합니다.  

-   옵션 1. PXE의 컴퓨터를 부팅하여 LTI 프로세스를 시작합니다.  

-   옵션 2. Windows 배포 서비스 이미지 저장소에서 운영 체제 이미지를 배포합니다.  

-   옵션 3. MDT 및 Windows Server 2008 Windows 배포 서비스 서버 역할과 함께 멀티캐스팅을 사용합니다.  

### <a name="option-1-boot-computers-in-pxe-to-initiate-the-lti-process"></a>옵션 1: PXE의 컴퓨터를 부팅하여 LTI 프로세스 시작  
 동적 호스트 구성 프로토콜과 함께 Windows 배포 서비스를 사용하여 MDT 배포 프로세스를 시작하면 운영 체제 배포에 대한 관리 비용을 최소화할 수 있습니다. 이렇게 하면 각 대상 컴퓨터에 부팅 가능한 미디어를 만들고 배포할 필요가 없습니다.  

#### <a name="create-and-import-the-deployment-workbench-windows-pe-image-into-windows-deployment-services"></a>Deployment 워크벤치 Windows PE 이미지를 만들고 Windows 배포 서비스에 가져오기  
 새 MDT 배포 공유를 만들거나 기존 MDT 배포 공유를 수정하는 경우 사용자 지정 Windows PE 부팅 이미지를 만들 수 있습니다. 배포 공유가 업데이트되면 Windows PE 부팅 이미지가 자동으로 생성되고, 배포 공유에 대한 정보로 업데이트되며, 배포 공유 구성 중에 지정된 추가 드라이버 또는 구성 요소가 모두 주입됩니다.  

 Windows PE 부팅 이미지는 CD 또는 DVD에 쓸 수 있는 ISO 이미지 파일 및 부팅 가능한 WIM 파일 모두로 생성됩니다. PXE로 부팅할 수 있는 컴퓨터에서 설치를 초기화하는 데 사용되는 네트워크를 통해 LTI Windows PE 부팅 이미지를 다운로드하고 실행할 수 있도록 WIM 파일을 Windows 배포 서비스로 가져올 수 있습니다.  

 **Deployment 워크벤치에서 부팅 가능한 Windows PE 이미지를 만들려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

     ***deployment_shareProperties*** 대화 상자에서 **Windows PE *platform* 설정** 탭을 클릭합니다. 여기서 platform은 구성할 Windows PE 이미지의 아키텍처입니다.  

4.  **손쉬운 부팅 이미지 설정** 영역에서 **손쉬운 부팅 가능한 RAM 디스크 ISO 이미지 생성** 확인란을 선택합니다.  

5.  **Windows PE *platform* 구성 요소** 탭을 클릭합니다. 여기서 *platform*은 구성할 Windows PE 이미지의 아키텍처입니다.  

6.  **드라이버 추가** 섹션에서 포함할 적절한 드라이버 종류를 클릭합니다.  

    > [!NOTE]
    >  필요한 디바이스 드라이버가 Windows PE에 이미 포함되어 있는 경우 이 단계가 필요하지 않습니다.  

7.  **드라이버 추가** 섹션의 **선택 프로필** 목록에서 적절한 드라이버 선택 프로필을 선택합니다.  

8.  **속성** 대화 상자에서 **확인**을 클릭합니다.  

    > [!NOTE]
    >  필요한 디바이스 드라이버가 Windows PE에 이미 포함되어 있는 경우 이 단계가 필요하지 않습니다.  

9. 세부 정보 창에서 ***deployment_share***를 클릭합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

10. [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

11. **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

12. **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

13. **확인** 페이지에서 **마침**을 클릭합니다.  

     이 프로세스가 완료되면 배포 공유의 Boot 폴더에 여러 가지 부팅 이미지가 포함됩니다. 예를 들어 다음과 같습니다.  

     D:\Production Deployment Share\Boot\LiteTouchPE_x64.iso  

     D:\Production Deployment Share\Boot\LiteTouchPE_x64.wim  

     D:\Production Deployment Share\Boot\LiteTouchPE_x86.iso  

     D:\Production Deployment Share\Boot\LiteTouchPE_x86.wim  

 CD 또는 DVD에 직접 생성된 ISO 파일을 작성하거나 새 하드웨어에서 LTI 프로세스를 초기화하는 데 사용할 수 있습니다. 실제 미디어가 없어도 새 컴퓨터에서 LTI 배포 프로세스를 초기화할 수 있도록 부팅 WIM 파일을 Windows 배포 서비스로 가져올 수도 있습니다.  

 **Windows PE 이미지를 Windows 배포 서비스로 가져오려면**  

1.  Windows 배포 서비스 콘솔을 시작한 다음, Windows 배포 서비스에 연결합니다.  

2.  콘솔 트리에서 **부팅 이미지**를 마우스 오른쪽 단추로 클릭한 다음, **부팅 이미지 추가**를 클릭합니다.  

3.  가져올 WIM 이미지를 찾습니다(예: D:\Production Deployment Share\Boot\LiteTouchPE_x86.wim).  

4.  가져오기 프로세스는 부팅 이미지에서 메타데이터를 자동으로 읽지만, **이미지 이름** 및 **이미지 설명** 값을 편집할 수도 있습니다. 클라이언트가 PXE로 부팅할 때 **이미지 이름**은 Windows 부팅 관리자에서 표시하는 부팅 옵션 정보에 영향을 줍니다.  

5.  부팅 이미지를 가져오면 PXE로 부팅되고 Windows 배포 서비스에서 회신을 받는 컴퓨터는 모두 LTI 부팅 이미지를 다운로드하고 LTI 설치를 시작할 수 있습니다.  

 Windows 배포 서비스의 설치 및 구성에 대해서는 이 가이드에서 다루지 않습니다. Windows 배포 서비스에 대한 자세한 내용은 [Windows 배포 서비스 가이드](http://technet.microsoft.com/library/cc265612.aspx)를 참조하세요.  

#### <a name="use-windows-deployment-services-to-automatically-detect-the-deployment-server"></a>Windows 배포 서비스를 사용하여 배포 서버를 자동으로 검색  
 MDT 배포 공유가 Windows 배포 서비스와 동일한 서버에서 호스팅되는 경우 Windows 배포 서비스를 사용하여 MDT 부팅 이미지를 호스팅할 때 추가 옵션을 사용할 수 있습니다.  

 PXE 클라이언트에서 MDT 부팅 이미지를 로드하면 부팅 이미지를 호스팅하는 Windows 배포 서비스 서버의 이름이 캡처되어 **WDSServer** MDT 속성에 저장됩니다. 그러면 부팅 이미지의 BootStrap.ini 파일 및 배포 공유의 CustomSettings.ini 파일에서 **DeployRoot** 속성을 기준으로 이 속성을 참조할 수 있습니다. 이렇게 하면 클라이언트가 Windows 배포 서비스 서버에서 호스팅되는 배포 공유를 사용하여 Windows 배포 서비스에서 자동으로 부팅됩니다. 따라서 모든 구성 파일에 서버 이름을 지정할 필요가 없습니다.  

 **로컬 Windows 배포 서비스 서버를 배포 서버로 설정하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Advanced Configuration/Database로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **규칙** 탭을 클릭합니다.  

     이 탭에 입력한 정보는 CustomSettings.ini 파일에 저장됩니다.  

5.  **%WDSServer%** 변수를 사용하도록 **DeployRoot** 속성을 구성합니다(예: **DeployRoot=\\\\%WDSServer%\Deployment$**).  

6.  **Bootstrap.ini 편집**을 클릭합니다.  

7.  **DeployRoot** 값을 **DeployRoot=\\\\%WDSServer%\Deployment$** 에 추가하거나 변경하여 **%WDSServer%** 속성을 사용하도록 BootStrap.ini를 구성합니다.  

8.  **파일** 메뉴에서 **저장**을 클릭하여 BootStrap.ini 파일의 변경 내용을 저장합니다.  

9. **확인**을 클릭합니다.  

     배포 공유를 업데이트해야 합니다.  

10. 세부 정보 창에서 **deployment_share**를 클릭합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

11. [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

12. **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

13. **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

14. **확인** 페이지에서 **마침**을 클릭합니다.  

15. 업데이트된 부팅 WIM을 Windows 배포 서비스로 가져옵니다.  

### <a name="option-2-deploy-an-operating-system-image-from-the-windows-deployment-services-store"></a>옵션 2: Windows 배포 서비스 저장소에서 운영 체제 이미지 배포  
 운영 체제 배포에 Windows 배포 서비스를 이미 사용하고 있는 경우, 자체 저장소를 사용하는 대신 이미 사용 중인 Windows 배포 서비스 운영 체제 이미지를 참조하고, 드라이버 관리, 애플리케이션 배포, 업데이트 설치, 규칙 처리 및 기타 MDT 기능으로 Windows 배포 서비스 배포를 보완하도록 구성하여 MDT 기능을 확장합니다. MDT에서 Windows 배포 서비스 운영 체제 이미지를 참조한 후에는 MDT 배포 공유에 준비된 모든 운영 체제처럼 이를 처리할 수 있습니다.  

 **Windows 배포 서비스 운영 체제 이미지를 참조하려면**  

> [!NOTE]
>  다음 단계를 수행하려면 먼저 하나 이상의 운영 체제 이미지를 Windows 배포 서비스 서버로 가져와야 합니다.  

1.  다음 파일을 Windows 미디어의 Sources 폴더에서 Windows 배포 서비스 서버의 C:\Program Files\Microsoft Deployment Toolkit\bin 폴더에 복사하여 Windows 배포 서비스 이미지에 액세스할 수 있도록 MDT를 업데이트합니다.  

    -   Wdsclientapi.dll  

    -   Wdscsl.dll  

    -   Wdsimage.dll  

    -   Wdstptc.dll(Windows Server 2008 원본 디렉터리에서 복사하는 경우에만 해당)  

    > [!NOTE]
    >  사용 중인 Windows 원본 디렉터리는 MDT가 설치된 컴퓨터에서 실행되는 운영 체제의 플랫폼과 일치해야 합니다.  

2.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

3.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Operating Systems로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

4.  [작업] 창에서 **운영 체제 가져오기**를 클릭합니다.  

     새 OS 마법사가 시작됩니다.  

5.  **OS 유형** 페이지에서 **Windows 배포 서비스 이미지**를 클릭하고, **다음**을 클릭합니다.  

6.  **WDS 서버** 페이지에서 참조할 Windows 배포 서비스 서버의 이름(예: **WDSSvr001**)을 입력하고, **다음**을 클릭합니다.  

7.  **요약** 페이지에서 설정이 올바른지 확인하고, **다음**을 클릭합니다.  

8.  **확인** 페이지에서 **마침**을 클릭합니다.  

     이제 Windows 배포 서비스 서버에서 사용할 수 있는 모든 이미지를 MDT 작업 순서에 사용할 수 있습니다.  

> [!NOTE]
>  Windows 배포 서비스에서 이미지를 가져오면 Windows 배포 서비스 서버의 원본 파일이 배포 공유로 복사되지 않습니다. MDT는 원래 위치에서 원본 파일을 계속 사용합니다.  

### <a name="option-3-use-multicasting-with-mdt-and-the-windows-server-2008-windows-deployment-services-role"></a>옵션 3: MDT 및 Windows Server 2008 Windows 배포 서비스 역할과 함께 멀티캐스팅 사용  
 Windows Server 2008 출시와 함께 Windows 배포 서비스는 멀티캐스트 전송을 사용하여 이미지 배포를 지원하도록 향상되었습니다. MDT에는 MDT와 Windows 배포 서비스의 멀티캐스팅을 통합하는 업데이트도 포함되어 있습니다.  

 또한 업데이트된 Windows AIK(Windows 자동 설치 키트) 버전 1.1에는 Wdsmcast.exe가 포함되어 있습니다. 이렇게 하면 멀티캐스트 세션을 수동으로 조인할 수 있으며, 클라이언트에서 Wdsmcast.exe를 시작하여 활성 멀티캐스트 세션에서 파일을 복사할 수 있습니다.  

 LTIApply.wsf 스크립트는 배포 공유에서 운영 체제 원본 파일에 액세스할 때 Wdsmcast.exe를 사용합니다. LTIApply.wsf는 실행 중인 Windows PE 버전에 따라 *deployment_share*\Tools\x86 또는 *deployment_share*\Tools\x64 폴더(여기서 *deployment_share*는 배포 공유가 포함된 파일 시스템 폴더의 이름임)의 배포 공유에서 Wdsmcast.exe를 찾습니다.  

 LTIApply.wsf가 실행되면 항상 기존의 멀티캐스트 스트림에서 WIM 이미지에 액세스하여 다운로드하려고 하지만, 멀티캐스트 스트림이 없는 경우 표준 파일 복사본으로 대체(fallback)합니다.  

> [!NOTE]
>  이 프로세스는 WIM 이미지 파일에만 적용됩니다.  

 MDT 멀티캐스팅을 준비하기 위한 배포 서버 필수 구성 요소는 다음과 같습니다.  

-   배포 서버는 Windows Server 2008 이상을 실행해야 합니다.  

-   Windows 배포 서비스 역할은 서버 관리 콘솔에서 설치해야 합니다.  

-   Windows Server 2008용 Windows AIK 1.1이 설치되어 있어야 합니다.  

-   MDT가 설치되어야 합니다.  

-   MDT를 사용하는 모든 배포와 마찬가지로, 하나 이상의 운영 체제 WIM 이미지를 원본 파일의 전체 집합 또는 설치 파일이 있는 사용자 지정 이미지로 가져와야 합니다  

> [!NOTE]
>  멀티캐스팅에는 최신 버전의 Windows AIK를 사용해야 합니다. 이는 이전 버전의 Windows AIK(예: Windows AIK 1.0)에 포함된 Windows PE 복사본은 멀티캐스트 서버에서 다운로드하도록 지원하지 않기 때문입니다.  

 **기존 배포 공유에서 멀티캐스팅하도록 MDT를 구성하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*로 이동합니다. 여기서 *deployment_share*는 구성할 배포 공유의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **일반** 탭에서 **이 배포 공유에 멀티캐스트 사용(Windows Server 2008 Windows 배포 서비스 필요)** 확인란을 선택합니다.  

5.  **확인**을 클릭합니다.  

6.  [작업] 창에서 **배포 공유 업데이트**를 클릭합니다.  

     배포 공유 업데이트 마법사가 시작됩니다.  

7.  **옵션** 페이지에서 배포 공유를 업데이트하는 데 필요한 옵션을 선택하고, **다음**을 클릭합니다.  

8.  **요약** 페이지에서 세부 정보가 올바른지 확인하고, **다음**을 클릭합니다.  

9. **확인** 페이지에서 **마침**을 클릭합니다.  

 Windows 배포 서비스 멀티캐스트 전송에 대한 배포 공유가 구성되었습니다.  

 이 프로세스는 기존 MDT 배포 공유를 직접 사용하는 Windows 배포 서비스 자동 캐스트 전송을 만듭니다. MDT는 예약된 캐스트 전송을 만들지 않습니다. 또한 Windows PE가 실행될 때까지 멀티캐스트 클라이언트를 로드할 수 없으므로, 추가 이미지를 Windows 배포 서비스로 가져오지 않고 부팅 이미지에 멀티캐스트를 사용할 수 없습니다.  

 **Windows 배포 서비스에서 멀티캐스트 전송이 생성되었는지 확인하려면**  

1.  **시작**을 클릭하고, **관리 도구**를 가리킨 다음, **Windows 배포 서비스**를 클릭합니다.  

2.  Windows 배포 서비스 콘솔 트리에서 **서버**를 마우스 오른쪽 단추로 클릭한 다음, **서버 추가**를 클릭합니다.  

3.  **서버 추가** 대화 상자에서 **로컬 컴퓨터**를 클릭한 다음, **확인**을 클릭합니다.  

4.  Windows 배포 서비스 콘솔 트리에서 **서버**를 클릭한 다음, ***server_name***을 클릭합니다. 여기서 *server_name*은 Windows 배포 서비스를 실행하는 컴퓨터의 이름입니다. **멀티캐스트 전송**을 클릭합니다.  

5.  세부 정보 창에서 배포 공유에 대한 새 자동 캐스트 전송이 나열됩니다(예: **BDD Share Deployment$**).  

6.  **BDD Share Deployment$** 자동 캐스트 전송의 상태가 **활성**으로 설정되어 있는지 확인합니다.  

 컴퓨터가 배포되면 \Windows\Temp\DeploymentLogs 폴더의 BDD.log 파일을 검사하여 운영 체제가 멀티캐스트 전송에서 다운로드되었는지 확인합니다.  

 로그 폴더에는 모두 **멀티캐스트 전송**으로 시작하는 두 개의 항목이 있습니다. 두 항목을 확인하여 전송이 성공적으로 수행되었는지 확인합니다. MDT 및 Windows 배포 서비스를 사용하는 멀티캐스트 전송에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "LTI 배포에 Windows 배포 서비스 멀티캐스트 배포 사용" 섹션을 참조하세요.  

## <a name="performing-staged-deployments-using-mdt-oem-preload"></a>MDT를 사용하여 준비된 배포 수행(OEM 미리 로드)  
 대부분의 조직에서는 프로덕션 네트워크에 배포하기 전에 컴퓨터에 운영 체제 이미지가 로드되어 있습니다. 경우에 따라 스테이징 환경에서 컴퓨터를 구축해야 하는 조직 내의 팀에서 운영 체제 이미지 로드를 수행합니다. 다른 경우에는 *OEM*(주문자 상표 부착 방식)이라고도 하는 컴퓨터 하드웨어 공급업체에서 운영 체제 이미지 로드를 수행합니다.  

> [!NOTE]
>  OEM 미리 로드 프로세스는 LTI를 사용하여 수행되는 배포에 대해서만 MDT에서 지원됩니다. Configuration Manager의 경우 미리 준비된 미디어 기능을 사용합니다.  

### <a name="overview-of-the-oem-preload-process-in-mdt"></a>MDT의 OEM 미리 로드 프로세스 개요  
 OEM 미리 로드 프로세스는 다음 세 가지 단계로 구분됩니다.  

-   **1단계**. 스테이징 환경에 적용할 참조 컴퓨터의 미디어 기반 이미지를 만듭니다.  

-   **2단계**. 스테이징 환경에서 참조 컴퓨터 이미지를 대상 컴퓨터에 적용합니다.  

-   **3단계**. 프로덕션 환경에서 대상 컴퓨터의 배포를 완료합니다.  

 1단계 및 3단계는 일반적으로 배포 조직에서 수행합니다. 조직의 OEM 미리 로드 프로세스 사용에 따라 조직 또는 컴퓨터를 공급하는 컴퓨터 하드웨어 공급업체에서 2단계를 수행할 수 있습니다. 조직에서 2단계를 수행하는 경우 스테이징 환경은 조직 내에 있습니다. OEM에서 2단계를 수행하는 경우 스테이징 환경은 OEM의 환경에 있습니다.  

#### <a name="overview-of-mdt-configuration-files-in-the-oem-preload-process"></a>OEM 미리 로드 프로세스의 MDT 구성 파일 개요  
 별도의 MDT 구성 파일(CustomSettings.ini 및 Bootstrap.ini)이 OEM 미리 로드 프로세스의 1단계 및 3단계에서 실행되는 작업 순서에서 사용됩니다. 그러나 두 구성 파일은 동시에 서로 다른 폴더 구조에 있습니다.  

 1단계에서 구성 파일은 참조 컴퓨터를 만드는 동안 사용되며 해당 단계에서 사용되는 작업 순서와 관련된 폴더에 저장됩니다. OEM 미리 로드 프로세스의 3단계와 마지막 단계에서 사용되는 구성 파일은 해당 단계에서 사용된 작업 순서와 관련된 폴더에 저장됩니다.  

 구성 파일을 수정하는 경우 각각의 OEM 미리 로드 프로세스 단계에서 해당 작업 순서와 부합하는 구성 파일의 변경 내용이 적용되었는지 확인합니다.  

#### <a name="overview-of-mdt-log-files-in-the-oem-preload-process"></a>OEM 미리 로드 프로세스의 MDT 로그 파일 개요  
 별도의 MDT 로그 파일이 OEM 미리 로드 프로세스의 1단계 및 3단계에서 생성됩니다.  

-   1단계의 MDT 로그 파일은 C:\MININT 및 C:\SMSTSLog 폴더에 저장됩니다.  

-   3단계의 MDT 로그 파일은 x86 기반 배포의 경우 %WINDIR%\System32\CCM\Logs 폴더 또는 x64 기반 배포의 경우 %WINDIR%\SysWow64\CCM\Logs 폴더에 저장됩니다.  

 MDT 관련 배포 문제를 진단하거나 문제를 해결하는 경우 적절한 폴더를 사용합니다.  

### <a name="staged-deployments-using-lti"></a>LTI를 통한 준비된 배포  
 LTI 배포의 경우 *이동식 미디어(미디어)* 배포 공유 유형을 사용하여 OEM 미리 로드 프로세스를 수행합니다. OEM 미리 로드 프로세스에는 다른 배포 공유 유형이 지원되지 않습니다.  

 OEM 미리 로드 프로세스를 수행하려면, 대상 운영 체제를 배포하는 데 사용할 작업 순서 외에도 Litetouch OEM 작업 순서 작업 순서 템플릿을 기반으로 하는 작업 순서를 만듭니다. 그런 다음, 배포 공유 콘텐츠의 ISO 파일, 특히 대상 컴퓨터의 프로세서 플랫폼에 따라 LiteTouchPE_x86.iso 파일 또는 LiteTouchPE_x64.iso 파일을 최종적으로 만드는 *이동식 미디어(미디어)* 배포 공유를 만듭니다. 또한 배포 공유 업데이트 프로세스는 범용 디스크 형식 미디어를 만드는 데 사용할 수 있는 폴더 구조도 만듭니다.  

#### <a name="lti-oem-preload-processphase-1-create-a-media-based-image"></a>LTI OEM 미리 로드 프로세스 - 1단계: 미디어 기반 이미지 만들기  
 배포 조직에서 OEM 미리 로드 프로세스의 1단계를 수행합니다. 이 단계의 최종 결과물은 OEM 또는 배포 조직 내의 스테이징 환경으로 전송되는 부팅 가능한 이미지(예: ISO 파일) 또는 미디어(예: DVD)입니다. 이러한 단계의 대부분은 Deployment 워크벤치에서 수행됩니다.  

 **OEM 또는 배포 조직 내의 스테이징 환경으로 배달할 미디어 기반 이미지를 만들려면**  

1.  Deployment 워크벤치에서 배포 공유에 대해 채울 노드는 다음과 같습니다.  

    -   운영 체제  

    -   애플리케이션  

    -   패키지  

    -   기본 제공 드라이버  

     이 단계를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 배포 공유 관리" 섹션을 참조하세요.  

2.  Deployment 워크벤치에서 Litetouch OEM 작업 순서 작업 순서 템플릿을 기반으로 하는 새 작업 순서를 만듭니다.  

     이 단계를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 작업 순서 구성" 섹션을 참조하세요.  

3.  프로덕션 환경에 배포한 후 대상 컴퓨터에 대상 운영 체제를 배포하는 데 사용할 하나 이상의 작업 순서를 만듭니다.  

     이 단계를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "Deployment 워크벤치에서 작업 순서 구성" 섹션을 참조하세요.  

4.  OEM 배포에 필요한 애플리케이션, 운영 체제, 드라이버, 패키지 및 작업 순서가 포함된 선택 프로필을 만듭니다.  

     이 단계를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "선택 프로필 관리" 섹션을 참조하세요.  

5.  배포 미디어를 만듭니다.  

     이 단계를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "LTI 배포 미디어 관리" 섹션을 참조하세요.  

6.  이전 단계의 Deployment 워크벤치에서 만든 배포 미디어를 업데이트합니다.  

     배포 미디어를 업데이트하는 경우 Deployment 워크벤치에서 LiteTouchMedia.iso 파일을 만듭니다. 이 단계를 수행하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "LTI 배포 미디어 관리" 섹션을 참조하세요.  

7.  이전 단계에서 만든 LiteTouchMedia.iso 파일의 DVD를 굽습니다.  

    > [!NOTE]
    >  OEM 또는 조직의 스테이징 환경에 ISO 파일을 배달하는 경우 이 단계가 필요하지 않습니다.  

8.  OEM 또는 조직의 스테이징 환경에 ISO 파일 또는 DVD를 배달합니다.  

#### <a name="lti-oem-preload-processphase-2-apply-the-image-to-the-target-computer"></a>LTI OEM 미리 로드 프로세스 - 2단계: 대상 컴퓨터에 이미지 적용  
 OEM 미리 로드 프로세스의 2단계는 OEM 또는 배포 조직의 스테이징 환경에 있는 배포 팀에서 수행합니다. 이 프로세스 단계에서는 1단계에서 만든 .iso 파일 또는 DVD가 대상 컴퓨터에 적용됩니다. 이 단계의 결과물은 프로덕션 환경에서 배포할 준비가 되도록 대상 컴퓨터에 배포된 이미지입니다.  

 **대상 컴퓨터에 이미지를 적용하려면**  

1.  1단계에서 만든 미디어를 사용하여 대상 컴퓨터를 시작합니다.  

     Windows PE가 시작된 다음, Windows 배포 마법사가 시작됩니다.  

2.  Windows 배포 마법사에서 **스테이징 환경에 대한 OEM 사전 설치 작업 순서**를 클릭합니다.  

     작업 순서가 시작되고 부팅 가능한 미디어의 내용이 대상 컴퓨터의 로컬 하드 디스크에 복사됩니다.  

3.  **스테이징 환경에 대한 OEM 사전 설치 작업 순서** 작업 순서에 대한 Windows 배포 마법사가 완료되면, 하드 디스크에서 운영 체제를 배포하는 데 사용되는 다른 작업 순서에 대한 Windows 배포 마법사를 실행하여 나머지 배포 프로세스를 시작할 준비가 됩니다.  

     **스테이징 환경에 대한 OEM 사전 설치 작업 순서** 작업 순서는 대상 컴퓨터에 이미지를 배포하고 LTI 프로세스를 시작하는 작업을 담당합니다. Windows 배포 마법사가 다시 시작되어 대상 컴퓨터에 운영 체제를 배포하는 데 사용되는 작업 순서가 실행됩니다.  

4.  필요에 따라 스테이징 환경의 여러 대상 컴퓨터에 첫 번째 하드 디스크의 콘텐츠를 복제합니다.  

5.  대상 컴퓨터는 배포를 위해 프로덕션 환경으로 배달됩니다.  

#### <a name="lti-oem-preload-processphase-3-complete-target-computer-deployment"></a>LTI OEM 미리 로드 프로세스 - 3단계: 대상 컴퓨터 배포 완료  
 OEM 미리 로드 프로세스의 3단계와 마지막 단계는 배포 조직의 프로덕션 환경에서 수행됩니다. 이 프로세스 단계에서는 대상 컴퓨터가 시작되고, 이전 단계에서 스테이징 환경의 하드 디스크에 배치된 부팅 가능한 미디어 이미지가 시작됩니다.  

 **프로덕션 환경에서 대상 컴퓨터의 배포를 완료하려면**  

1.  대상 컴퓨터를 시작합니다.  

     Windows PE가 시작된 다음, Windows 배포 마법사가 시작됩니다.  

2.  각 대상 컴퓨터에 대한 특정 구성 정보를 사용하여 Windows 배포 마법사를 완료합니다.  

     이 단계를 완료하는 방법에 대한 자세한 내용은 *Microsoft Deployment Toolkit 사용* MDT 문서에서 "배포 마법사 실행" 섹션을 참조하세요.  

 이 단계가 완료되면 대상 컴퓨터가 프로덕션 환경에서 사용할 준비가 됩니다.  

## <a name="using-windows-powershell-to-perform-common-tasks"></a>Windows PowerShell을 사용하여 일반적인 작업 수행  
 Deployment 워크벤치의 MDT 관리 작업은 다음 섹션과 같은 관리 작업을 자동화하는 데 사용할 수 있는 기본 Windows PowerShell cmdlet을 통해 수행됩니다.  

 MDT 관리를 자동화하려면 다음 단계를 수행합니다.  

-   [새 배포 공유 만들기](#CreateNewDeployShare)에서 설명한 대로 새 배포 공유를 만듭니다.  

-   [폴더 만들기](#CreateFolder)에서 설명한 대로 배포 공유에 폴더를 만듭니다.  

-   [폴더 삭제](#DeleteFolder)에서 설명한 대로 배포 공유에서 폴더를 삭제합니다.  

-   [장치 드라이버 가져오기](#ImportDeviceDriver)에서 설명한 대로 장치 드라이버를 배포 공유로 가져옵니다.  

-   [장치 드라이버 삭제](#DeleteDeviceDriver)에서 설명한 대로 배포 공유에서 장치 드라이버를 삭제합니다.  

-   [운영 체제 패키지 가져오기](#ImportOpSysPackage)에서 설명한 대로 운영 체제 패키지를 배포 공유로 가져옵니다.  

-   [운영 체제 패키지 삭제](#DeleteOpSysPackage)에서 설명한 대로 배포 공유에서 운영 체제 패키지를 삭제합니다.  

-   [운영 체제 가져오기](#ImportOpSys)에서 설명한 대로 운영 체제를 배포 공유로 가져옵니다.  

-   [운영 체제 삭제](#DeleteOpSys)에서 설명한 대로 배포 공유에서 운영 체제를 삭제합니다.  

-   [응용 프로그램 만들기](#CreateApplication)에서 설명한 대로 배포 공유에 응용 프로그램을 만듭니다.  

-   [응용 프로그램 삭제](#DeleteApplication)에서 설명한 대로 배포 공유에서 응용 프로그램을 삭제합니다.  

-   [작업 순서 만들기](#CreateTaskSequence)에서 설명한 대로 배포 공유에 작업 순서를 만듭니다.  

-   [작업 순서 삭제](#DeleteTaskSequence)에서 설명한 대로 배포 공유에서 작업 순서를 삭제합니다.  

-   [MDT DB 만들기](#CreateMDTDB)에서 설명한 대로 MDT DB를 만듭니다.  

-   [선택 프로필 만들기](#CreateSelectProfile)에서 설명한 대로 선택 프로필을 만듭니다.  

-   [배포 공유 업데이트](#UpdatingDeployShare)에서 설명한 대로 배포 공유를 업데이트합니다.  

-   [연결된 배포 공유 만들기](#CreateLinkedDeployShare)에서 설명한 대로 연결된 배포 공유를 만듭니다.  

-   [연결된 배포 공유 업데이트](#UpdatingLinkedDeployShare)에서 설명한 대로 연결된 배포 공유를 업데이트합니다.  

-   [연결된 배포 공유 삭제](#DeleteLinkedDeployShare)에서 설명한 대로 연결된 배포 공유를 삭제합니다.  

-   [미디어 만들기](#CreateMedia)에서 설명한 대로 배포 미디어를 만듭니다.  

-   [미디어 생성](#GenerateMedia)에서 설명한 대로 배포 미디어를 생성합니다.  

-   [미디어 삭제](#DeleteMedia)에서 설명한 대로 배포 미디어를 삭제합니다.  

###  <a name="CreateNewDeployShare"></a> 새 배포 공유 만들기  
 다음 Windows PowerShell 명령은 D:\Production Deployment Share에서 *Production$* 라는 새 배포 공유를 만듭니다. Deployment 워크벤치에 새 배포 공유가 Production으로 표시됩니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider "MDTProvider" -Root "D:\Production Deployment Share" -Description "Production" -NetworkPath "\\Deployment_Server\Production$" -Verbose | add-MDTPersistentDrive -Verbose  
    ```  

###  <a name="CreateFolder"></a> 폴더 만들기  
 다음 Windows PowerShell 명령은 Deployment 워크벤치 콘솔 트리의 Deployment Workbench\/Deployment Shares\/Production\/Applications에 Adobe 폴더를 만듭니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Applications" -enable "True" -Name "Adobe" -Comments "This folder contains Adobe software" -ItemType "folder" -Verbose remove-psdrive DS001 -Verbose  
    ```  

    > [!NOTE]
    >  스크립트에 "`remove-psdrive`"를 추가하면 계속하기 전에 백그라운드 프로세스가 완료됩니다.  

###  <a name="DeleteFolder"></a> 폴더 삭제  
 다음 Windows PowerShell 명령은 \/Deployment Shares\/Production\/Applications\/Adobe 폴더를 삭제합니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Remove-item -path "DS002:\Applications\Adobe" -Verbose  
    ```  

> [!NOTE]
>  폴더가 비어 있지 않으면 스크립트가 실패합니다.  

###  <a name="ImportDeviceDriver"></a> 장치 드라이버 가져오기  
 다음 Windows PowerShell 명령은 Dell 2407 WFP 모니터 디바이스 드라이버를 프로덕션 배포 공유로 가져옵니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtdriver -path "DS002:\Out-of-Box Drivers\Monitor" -SourcePath "D:\Drivers\Dell\2407 WFP" -Verbose  
    ```  

###  <a name="DeleteDeviceDriver"></a> 장치 드라이버 삭제  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에서 Dell 2407 WFP 모니터 드라이버를 삭제합니다.  

```  
Remove-item -path "DS002:\Out-of-Box Drivers\Dell Inc. Monitor 2407WFP.INF 1.0" -Verbose  
```  

###  <a name="ImportOpSysPackage"></a> 운영 체제 패키지 가져오기  
 다음 Windows PowerShell 명령은 D:\\Updates\\Microsoft\\Vista 아래에 있는 모든 운영 체제 패키지를 가져옵니다. 이러한 운영 체제 패키지는 D:\\Production Deployment Share에 있는 프로덕션 배포 공유에 저장됩니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtpackage -path "DS002:\Packages" -SourcePath "D:\Updates\Microsoft\Vista" -Verbose  
    ```  

###  <a name="DeleteOpSysPackage"></a> 운영 체제 패키지 삭제  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에서 지정된 운영 체제 패키지를 삭제합니다.  

```  
Remove-item -path "DS002:\Packages\Package_1_for_KB940105 neutral x86 6.0.1.0 KB940105" -Verbose  
```  

###  <a name="ImportOpSys"></a> 운영 체제 가져오기  
 다음 Windows PowerShell 명령은 D:\\Operating Systems\\Windows Vista x86에 있는 Windows Vista 운영 체제를 가져옵니다. 운영 체제는 D:\\Production Deployment Share에 있는 프로덕션 배포 공유에 저장됩니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdtoperatingsystem -path "DS002:\Operating Systems" -SourcePath "D:\Operating Systems\Windows Vista x86" -DestinationFolder "Windows Vista x86" -Verbose  
    ```  

###  <a name="DeleteOpSys"></a> 운영 체제 삭제  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에서 Windows Vista HOMEBASIC 운영 체제를 삭제합니다.  

```  
Remove-item -path "DS002:\Operating Systems\Windows Vista HOMEBASIC in Windows Vista x86 install.wim" -Verbose  
```  

###  <a name="CreateApplication"></a> 응용 프로그램 만들기  
 다음 Windows PowerShell 명령은 D:\\Software\\Adobe\\Reader 9의 원본 파일을 사용하여 Adobe Reader 9 애플리케이션을 만듭니다. 애플리케이션은 D:\\Production Deployment Share에 있는 프로덕션 배포 공유에 저장됩니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-MDTApplication -path "DS002:\Applications" -enable "True" -Name "Adobe Reader 9" -ShortName "Reader" -Version "9" -Publisher "Adobe" -Language "" -CommandLine "setup.exe" -WorkingDirectory ".\Applications\Adobe Reader 9" -ApplicationSourcePath "D:\Software\Adobe\Reader 9" -DestinationFolder "Adobe Reader 9" -Source ".\Applications\Adobe Reader 9" -Verbose  
    ```  

###  <a name="DeleteApplication"></a> 응용 프로그램 삭제  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에서 Adobe Reader 9 애플리케이션을 삭제합니다.  

```  
Remove-item -path "DS002:\Applications\Adobe Reader 9" -Verbose  
```  

###  <a name="CreateTaskSequence"></a> 작업 순서 만들기  
 다음 Windows PowerShell 명령은 D:\\Production Deployment Share에 있는 프로덕션 배포 공유에 **Windows Vista 프로덕션 빌드** 작업 순서를 만듭니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Import-mdttasksequence -path "DS002:\Task Sequences" -Name "Windows Vista Business Production Build" -Template "Client.xml" -Comments "Approved for use in the production environment.  This task sequence uses the Standard Client task sequence template" -ID "Vista_Ref" -Version "1.0" -OperatingSystemPath "DS002:\Operating Systems\Windows Vista BUSINESS in Windows Vista x86 install.wim" -FullName "Fabrikam User" -OrgName "Fabrikam" -HomePage "http://www.Fabrikam.com" -AdminPassword "secure_password" -Verbose  
    ```  

###  <a name="DeleteTaskSequence"></a> 작업 순서 삭제  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에서 **Windows Vista 프로덕션 빌드** 작업 순서를 삭제합니다.  

```  
Remove-item -path "DS002:\Task Sequences\Windows Vista Business Production Build" -force -Verbose  
```  

###  <a name="CreateMDTDB"></a> MDT DB 만들기  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에 대한 새 MDT DB를 *deployment\_server* 서버에 만듭니다. 데이터베이스 연결은 TCP\/IP를 통해 연결됩니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-MDTDatabase -path "DS002:" -SQLServer "DeploymentServer" -Netlib "DBMSSOCN" -Database "MDT2010" -SQLShare "DB_Connect" -Force -Verbose  
    ```  

###  <a name="CreateSelectProfile"></a> 선택 프로필 만들기  
 다음 Windows PowerShell 명령은 새 애플리케이션 선택 프로필을 만듭니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Selection Profiles" -enable "True" -Name "Applications" -Comments "" -Definition "<SelectionProfile><Include path="Applications" /></SelectionProfile>" -ReadOnly "False" -Verbose  
    ```  

###  <a name="UpdatingDeployShare"></a> 배포 공유 업데이트  
 다음 Windows PowerShell 명령은 D:\\Production Deployment Share에 있는 프로덕션 배포 공유를 업데이트합니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  
    
-   ```
    Update\-MDTDeploymentShare \-path "DS002:" \-Verbose  
    ```
    
###  <a name="CreateLinkedDeployShare"></a> 연결된 배포 공유 만들기  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에 연결되고 \\\\*remote\_server\_name*\\Deployment$ 공유 아래에 있는 배포 공유를 만듭니다. [모든 항목] 선택 프로필은 연결된 배포 공유에 복제되는 콘텐츠를 결정하는 데 사용됩니다. 프로덕션 배포 공유의 콘텐츠는 \\\\*remote\_server\_name*\\Deployment$ 공유에 이미 있는 콘텐츠와 병합됩니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Linked Deployment Shares" -enable "True" -Name "LINKED001" -Comments "" -Root "\\RemoteServerName\Deployment$" -SelectionProfile "Everything" -Replace "False" -Verbose  
    ```  

###  <a name="UpdatingLinkedDeployShare"></a> 연결된 배포 공유 업데이트  
 다음 Windows PowerShell 명령은 LINKED001 배포 공유를 업데이트합니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Replicate-MDTContent -path "DS002:\Linked Deployment Shares\LINKED001" -Verbose  
    ```  

###  <a name="DeleteLinkedDeployShare"></a> 연결된 배포 공유 삭제  
 다음 Windows PowerShell 명령은 LINKED001 배포 공유를 삭제합니다.  

-   Add\-PSSnapIn Microsoft.BDD.PSSnapIn  

-   ```  
    Remove-item -path "DS002:\Linked Deployment Shares\LINKED001" -Verbose  
    ```  

###  <a name="CreateMedia"></a> 미디어 만들기  
 다음 Windows PowerShell 명령은 부팅 가능한 미디어를 만드는 데 사용되는 콘텐츠가 포함되는 원본 폴더를 만듭니다. 프로덕션 배포 공유가 원본으로 사용됩니다. [모든 항목] 선택 프로필은 미디어 콘텐츠 폴더에 배치할 콘텐츠를 결정합니다. 미디어가 생성되면 LiteTouchMedia.iso 파일이 만들어집니다. 미디어는 x86 및 x64 플랫폼을 모두 지원합니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    New-item -path "DS002:\Media" -enable "True" -Name "MEDIA001" -Comments "some comment here" -Root "D:\Media" -SelectionProfile "Everything" -SupportX86 "True" -SupportX64 "True" -GenerateISO "True" -ISOName "LiteTouchMedia.iso" -Verbose  
    ```  

-   ```  
    New-PSDrive -Name "MEDIA001" -PSProvider "MDTProvider" -Root "D:\Media\Content" -Description "Embedded media deployment share" -Force -Verbose  
    ```  

###  <a name="GenerateMedia"></a> 미디어 생성  
 다음 Windows PowerShell 명령은 D:\\Media에 LiteTouchMedia.iso 파일을 만들고 MEDIA001 미디어 원본 폴더의 콘텐츠를 사용합니다.  

-   ```  
    Add-PSSnapIn Microsoft.BDD.PSSnapIn  
    ```  

-   ```  
    New-PSDrive -Name "DS002" -PSProvider MDTProvider -Root "D:\Production Deployment Share"  
    ```  

-   ```  
    Generate-MDTMedia -path "DS002:\Media\MEDIA001" -Verbose  
    ```  

###  <a name="DeleteMedia"></a> 미디어 삭제  
 다음 Windows PowerShell 명령은 프로덕션 배포 공유에서 MEDIA001 미디어를 삭제합니다.  

```  
Remove-item -path "DS002:\Media\MEDIA001" -Verbos  
```  

## <a name="delaying-domain-join-to-avoid-application-of-group-policy-objects"></a>그룹 정책 개체를 적용하지 않도록 방지하기 위해 도메인 조인 지연  
 그룹 정책은 중앙 집중식 일대다 모델을 통해 많은 수의 AD DS(Active Directory Domain Services) 컴퓨터 및 사용자 개체를 효율적으로 관리할 수 있는 기능을 제공하는 풍부하고 유연한 기술입니다. 그룹 정책 설정은 GPO(그룹 정책 개체)에 포함되어 있으며, 하나 이상의 AD DS 서비스 컨테이너(사이트, 도메인 및 OU(조직 구성 단위))에 연결됩니다.  

 일부 조직에는 제한적인 그룹 정책 설정이 있으며, 이로 인해 운영 체제 배포 시 문제가 발생할 수 있습니다. 예를 들어 자동화된 로그온 프로세스를 방해할 수 있는 그룹 정책 설정은 다음과 같습니다.  

-   자동 로그온 제한  

-   관리자 계정 이름 바꾸기  

-   법적 배너 및 캡션  

-   제한적인 보안 정책(예: SSLF(Specialized Security - Limited Functionality) 정책)  

 배포 중에 GPO로 인해 발생할 수 있는 문제를 해결할 수 있는 한 가지 옵션은 배포 프로세스에서 컴퓨터를 최대한 늦게 도메인에 조인하는 것입니다. 이 조인은 ZTIDomainJoin.wsf 스크립트를 실행하는 사용자 지정 작업 순서 단계를 사용하여 수행할 수 있습니다.  

 ZTIDomainJoin.wsf 스크립트는 대상 컴퓨터를 도메인에 조인하기 위해 **DomainAdmin**, **DomainAdminDomain**, **DomainAdminPassword**, **JoinDomain** 및 **MachineObjectOU** 속성을 사용합니다. 이러한 속성은 Windows 배포 마법사, 배포 공유 규칙, MDT DB 및 Configuration Manager 컴퓨터 및 수집 규칙을 사용하여 선언할 수 있습니다. 사용되는 계정에는 도메인에서 컴퓨터 개체를 만들고 삭제하는 데 필요한 권한이 있어야 합니다.  

 일반적으로 ZTIConfigure.wsf 스크립트는 이러한 속성으로 지정된 값을 사용하여 Unattend.xml 또는 Unattend.txt 파일을 업데이트합니다. 이러한 설정은 Windows 설치 프로그램에서 구문 분석되며, 시스템은 배포 프로세스 초기에 도메인에 조인하려고 합니다. 이렇게 하면 대상 컴퓨터에서 도메인 GPO에 지정된 설정을 따르고 배포 프로세스가 실패할 수 있습니다.  

 배포 프로세스 중에 대상 컴퓨터를 도메인에 조인하는 것을 의도적으로 지연시키려면 Unattend.xml 파일에서 특정 요소를 제거하면 됩니다. 관련 속성 요소가 파일에서 누락된 경우 ZTIConfigure.wsf 스크립트는 Unattend.xml 파일에 속성을 덮어쓰는 것을 건너뜁니다.  

> [!NOTE]
>  이 샘플 해결 방법은 Windows 7, Windows Server 2008 또는 Windows Server 2008 R2 운영 체제를 배포할 때만 유효합니다.  

 **Windows 설치 시 대상 컴퓨터가 도메인에 조인하지 못하도록 unattend.xml 파일 준비**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences/*task_sequence*로 이동합니다. 여기서 *deployment_share*는 배포 공유의 이름이고, *task_sequence*는 구성할 작업 순서의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **OS 정보** 탭에서 **Unattend.xml 편집**을 클릭합니다.  

     Windows SIM(Windows 시스템 이미지 관리자)이 시작됩니다.  

5.  **응답 파일** 창에서**4 specialize/Identification/Credentials**로 이동합니다. **자격 증명**을 마우스 오른쪽 단추로 클릭한 다음, **삭제**를 클릭합니다.  

6.  **예**를 클릭합니다.  

7.  응답 파일을 저장한 다음, Windows SIM을 종료합니다.  

8.  작업 순서 **속성** 대화 상자에서 **확인**을 클릭합니다.  

 unattend.xml 파일에서 `Credentials` 요소가 누락되면 ZTIConfigure.wsf 스크립트에서 Unattend.xml 파일에 도메인 조인 정보를 채울 수 없습니다. 이로 인해 Windows 설치 프로그램에서 도메인에 조인하려고 시도하지 못하게 됩니다.  

 **대상 컴퓨터를 도메인에 조인하는 작업 순서 단계를 추가하려면**  

1.  **시작**을 클릭한 다음, **모든 프로그램**을 가리킵니다. **Microsoft Deployment Toolkit**를 가리킨 다음, **Deployment 워크벤치**를 클릭합니다.  

2.  Deployment 워크벤치 콘솔 트리에서 Deployment Workbench/Deployment Shares/*deployment_share*/Task Sequences/*task_sequence*로 이동합니다. 여기서 *deployment_share*는 배포 공유의 이름이고, *task_sequence*는 구성할 작업 순서의 이름입니다.  

3.  [작업] 창에서 **속성**을 클릭합니다.  

4.  **작업 순서** 탭에서 [상태 복원] 노드로 이동하여 펼칩니다.  

5.  **도메인에서 복구** 작업 순서 단계가 있는지 확인합니다. 있는 경우 9단계로 진행합니다.  

6.  작업 순서 **속성** 대화 상자에서 **추가**를 클릭하고, **설정**으로 이동한 다음, **도메인에서 복구**를 클릭합니다.  

7.  **도메인에서 복구** 작업 순서 단계를 작업 순서 편집기에 추가합니다. 단계가 작업 순서의 원하는 위치에 있는지 확인합니다.  

8.  **도메인에서 복구** 작업 순서 단계에 대한 설정이 요구 사항에 맞게 구성되어 있는지 확인합니다.  

9. 작업 순서 **속성** 대화 상자에서 **확인**을 클릭하여 작업 순서를 저장합니다.
