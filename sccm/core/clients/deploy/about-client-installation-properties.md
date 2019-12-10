---
title: 클라이언트 설치 매개 변수 및 속성
titleSuffix: Configuration Manager
description: Configuration Manager 클라이언트를 설치하기 위한 ccmsetup 명령줄 매개 변수와 속성에 대해 알아봅니다.
ms.date: 03/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: c890fd27-7a8c-4f51-bbe2-f9908af1f42b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3758e7aa996a47b78e1d17864843cf0be70bdd8f
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70176508"
---
# <a name="about-client-installation-parameters-and-properties-in-system-center-configuration-manager"></a>System Center Configuration Manager의 클라이언트 설치 매개 변수 및 속성 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

CCMSetup.exe 명령을 사용하여 Configuration Manager 클라이언트를 설치합니다. 명령줄에서 제공하는 클라이언트 설치 매개 변수는 설치 동작을 수정합니다. 명령줄에서 제공하는 클라이언트 설치 속성은 설치된 클라이언트 에이전트의 초기 구성을 수정합니다.



##  <a name="aboutCCMSetup"></a> CCMSetup.exe 정보  
 CCMSetup.exe 명령은 관리 지점이나 원본 위치에서 클라이언트를 설치하는 데 필요한 파일을 다운로드합니다. 이러한 파일에는 다음이 포함될 수 있습니다.  

-   클라이언트 소프트웨어를 설치하는 Windows Installer 패키지 Client.msi입니다.  

-   Microsoft BITS(Background Intelligent Transfer Service) 설치 파일  

-   Windows Installer 설치 파일  

-   Configuration Manager 클라이언트의 업데이트 및 픽스  

> [!NOTE]  
>  Configuration Manager에서 Client.msi 파일을 직접 실행할 수 없습니다.  

 CCMSetup.exe는 설치를 사용자 지정하는 [명령줄 매개 변수](#ccmsetupexe-command-line-parameters)를 제공합니다. 매개 변수는 앞에 백슬래시가 추가되며, 규칙에 따라 소문자로 되어 있습니다. 필요한 경우, 콜론 바로 뒤에 원하는 값을 사용하여 매개 변수 값을 지정합니다. CCMSetup.exe 명령줄에서 client.msi의 동작을 수정하는 속성을 제공할 수도 있습니다. 속성은 규칙에 따라 모두 대문자로 되어 있습니다. 등호 바로 뒤에 원하는 값을 사용하여 속성 값을 지정합니다.  

> [!IMPORTANT]  
>  client.msi의 속성을 지정하기 전에 CCMSetup 매개 변수를 지정합니다.  

 CCMSetup.exe와 지원 파일은 Configuration Manager 설치 폴더의 **Client** 폴더에 있는 사이트 서버에 있습니다. 이 폴더는 네트워크에서 **&lt;사이트 서버 이름\>\SMS_&lt;사이트 코드\>\Client**로 공유됩니다.  

 명령 프롬프트에서 CCMSetup.exe 명령은 다음 형식을 사용합니다.  

 `CCMSetup.exe [<Ccmsetup parameters>] [<client.msi setup properties>]`  

 예:  

   `CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=S01 FSP=SMSFSP01`  

 이 예제는 다음 작업을 수행합니다.  

-   SMSMP01이라는 관리 지점을 지정하여 클라이언트 설치 파일을 다운로드할 배포 지점 목록을 요청합니다.  

-   컴퓨터에 클라이언트 버전이 이미 있는 경우 설치를 중지하도록 지정합니다.  

-   사이트 코드 S01에 클라이언트를 할당하도록 client.msi에 지시합니다.  

-   SMSFP01이라는 대체 상태 지점을 사용하도록 client.msi에 지시합니다.  

> [!NOTE]  
>  매개 변수 값에 공백이 있는 경우 공백을 따옴표로 묶으세요.  


> [!IMPORTANT]  
>  Configuration Manager용의 Active Directory 스키마를 확장한 경우 사이트는 Active Directory 도메인 서비스에 여러 클라이언트 설치 속성을 게시합니다. Configuration Manager 클라이언트는 자동으로 이러한 속성을 읽습니다. 자세한 내용은 [Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](about-client-installation-properties-published-to-active-directory-domain-services.md) 참조  



##  <a name="ccmsetupexe-command-line-parameters"></a>CCMSetup.exe 명령줄 매개 변수  

### <a name=""></a>/?  

ccmsetup.exe의 명령줄 매개 변수를 보여 주는 **CCMSetup** 대화 상자를 엽니다.  

예: **ccmsetup.exe /?**  

### <a name="sourceltpath"></a>/source:&lt;경로\>  

 파일 다운로드 위치를 지정합니다. 로컬 또는 UNC 경로를 사용합니다. 파일은 SMB(서버 메시지 블록) 프로토콜을 사용하여 다운로드됩니다. **/source**를 사용하려면 클라이언트 설치를 위한 Windows 사용자 계정에 해당 위치에 대한 읽기 권한이 있어야 합니다.

> [!NOTE]  
>  명령줄에서 **/source** 매개 변수를 두 번 이상 사용하여 대체 다운로드 위치를 지정할 수 있습니다.  

 예: **ccmsetup.exe /source:"\\\컴퓨터\폴더"**  

### <a name="mpltserver"></a>/mp:&lt;Server\>

 연결할 컴퓨터에 대한 원본 관리 지점을 지정합니다. 컴퓨터는 이 관리 지점을 사용하여 설치 파일에 대한 가장 가까운 배포 지점을 찾습니다. 배포 지점이 없거나 4시간 후에 컴퓨터가 배포 지점에서 파일을 다운로드할 수 없으면 지정된 관리 지점에서 파일을 다운로드합니다.  

> [!IMPORTANT]  
>  이 매개 변수는 컴퓨터가 다운로드 원본을 찾을 수 있도록 초기 관리 지점을 지정하는 데 사용되며, 임의 사이트의 임의 관리 지점이 될 수 있습니다. 클라이언트를 관리 지점에 *할당*하지 않습니다.   

 컴퓨터는 클라이언트 연결의 사이트 시스템 역할 구성에 따라 HTTP 또는 HTTPS 연결을 통해 파일을 다운로드합니다. 구성된 경우 다운로드 시 BITS 제한을 사용합니다. 모든 배포 지점과 관리 지점이 HTTPS 클라이언트 연결 전용으로 구성된 경우 클라이언트 컴퓨터에 유효한 클라이언트 인증서가 있는지 확인합니다.  

**/mp** 명령줄 매개 변수를 사용하여 관리 지점을 두 개 이상 지정할 수 있습니다. 컴퓨터가 첫 번째 관리지점에 연결하지 못한 경우 지정된 목록에서 다음을 시도합니다. 여러 관리 지점을 지정할 때는 세미콜론으로 값을 구분합니다.

클라이언트가 HTTPS를 사용하여 관리 지점에 연결하는 경우 보통은 컴퓨터 이름이 아니라 FQDN을 지정해야 합니다. 값은 관리 지점의 PKI 인증서 주체 또는 주체 대체 이름과 일치해야 합니다. Configuration Manager에서는 인트라넷 연결의 인증서에 컴퓨터 이름을 사용할 수 있도록 지원하지만 FQDN을 사용하는 것이 좋습니다.

컴퓨터 이름을 사용하는 경우의 예: `ccmsetup.exe /mp:SMSMP01`  

FQDN을 사용하는 경우의 예: `ccmsetup.exe /mp:smsmp01.contoso.com`  

이 매개 변수는 클라우드 관리 게이트웨이의 URL을 지정할 수 있습니다. 인터넷 기반 디바이스에서 클라이언트를 설치하려면 이 URL을 사용합니다. 이 매개 변수의 값을 가져오려면 다음 단계를 사용합니다.
- 클라우드 관리 게이트웨이를 만듭니다.
- 활성 클라이언트에서 관리자 권한으로 Windows PowerShell 명령 프롬프트를 엽니다. 
- 다음 명령을 실행합니다. `(Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}).MP`
- **/mp** 매개 변수에 사용할 “https://” 접두사를 추가합니다.

클라우드 관리 게이트웨이 URL을 사용하는 경우에 대한 예제. `ccmsetup.exe /mp: https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057598037248100`

 > [!Important]
 > **/mp** 매개 변수에 대해 클라우드 관리 게이트웨이의 URL을 지정하는 경우 **https://** 로 시작해야 합니다.


### <a name="retryltminutes"></a>/retry:&lt;분\>

CCMSetup.exe가 설치 파일을 다운로드하지 못할 경우의 다시 시도 간격입니다. CCMSetup은 **downloadtimeout** 매개 변수에 지정된 제한에 도달할 때까지 계속 다시 시도합니다.  

예: `ccmsetup.exe /retry:20`  

### <a name="noservice"></a>/noservice

CCMSetup이 기본값인 서비스로 실행되지 않도록 합니다. CCMSetup이 서비스로서 실행되는 경우 컴퓨터의 로컬 시스템 계정의 컨텍스트에서 실행됩니다. 이 계정은 설치에 필요한 네트워크 리소스에 액세스할 권한이 충분하지 않을 수 있습니다. **/noservice**를 사용하면 CCMSetup.exe가 설치 시작에 사용하는 사용자 계정의 컨텍스트에서 실행됩니다. 또한 스크립트를 사용하여 **/service** 매개 변수로 CCMSetup.exe를 실행하는 경우 서비스가 시작된 후에 CCMSetup.exe가 종료되고 설치 정보를 올바르게 보고하지 않을 수 있습니다.   

예: `ccmsetup.exe /noservice`  

### <a name="service"></a>/service

CCMSetup을 로컬 시스템 계정을 사용하는 서비스로 실행하도록 지정합니다.  

예: `ccmsetup.exe /service`  

### <a name="uninstall"></a>/uninstall

클라이언트 소프트웨어를 제거하도록 지정합니다. 자세한 내용은 [클라이언트를 관리하는 방법](../manage/manage-clients.md)을 참조하세요.  

예: `ccmsetup.exe /uninstall`  

### <a name="logon"></a>/logon

클라이언트 버전이 이미 설치되어 있는 경우 이 매개 변수는 클라이언트 설치를 중지하도록 지정합니다.  

예: `ccmsetup.exe /logon`  

### <a name="forcereboot"></a>/forcereboot

 설치를 완료하기 위해 필요한 경우 CCMSetup이 클라이언트 컴퓨터를 강제로 다시 시작하도록 지정합니다. 이 매개 변수를 지정하지 않으면 다시 시작해야 할 때 CCMSetup이 종료됩니다. 다음 수동으로 다시 시작 후 계속합니다.  

 예: `CCMSetup.exe /forcereboot`  

### <a name="bitspriorityltpriority"></a>/BITSPriority:&lt;우선 순위\>

 HTTP 연결을 통해 클라이언트 설치 파일을 다운로드할 때의 다운로드 우선 순위를 지정합니다. 가능한 값은 다음과 같습니다.  

- FOREGROUND  

- HIGH  

- NORMAL  

- LOW  

  기본값은 NORMAL입니다.  

  예: `ccmsetup.exe /BITSPriority:HIGH`  

### <a name="downloadtimeoutltminutes"></a>/downloadtimeout:&lt;분\>

CCMSetup이 설치 파일 다운로드를 중지하기 전까지 시도할 시간(분)입니다. 기본값은 **1440**분(하루)입니다.  

예: `ccmsetup.exe /downloadtimeout:100`  

### <a name="usepkicert"></a>/UsePKICert

이 옵션을 지정하면 클라이언트 인증이 포함된 PKI 인증서를 사용할 수 있는 경우 클라이언트에서 이 인증서를 사용합니다. 클라이언트가 유효한 인증서를 찾을 수 없는 경우 자체 서명된 인증서가 있는 HTTP 연결을 사용 합니다. 이 매개 변수를 사용하지 않을 때도 이 동작은 동일합니다.

> [!NOTE]  
>  일부 시나리오에서는 클라이언트를 설치할 때 이 매개 변수를 지정할 필요가 없으며, 클라이언트 인증서를 계속 사용할 수 있습니다. 이러한 시나리오에는 클라이언트 강제 및 소프트웨어 업데이트 지점 기반 클라이언트 설치를 사용하여 클라이언트를 설치하는 경우가 포함됩니다. 그러나 수동으로 클라이언트를 설치할 때는 언제나 이 매개 변수를 지정해야 하고, **/mp** 매개 변수를 사용하여 HTTPS 클라이언트 연결만 허용하도록 구성된 관리 지점을 지정해야 합니다. 또한 인터넷 전용 통신을 위한 클라이언트를 설치할 때 이 매개 변수를 지정해야 합니다. 인터넷 기반 관리 지점(CCMHOSTNAME) 및 사이트 코드(SMSSITECODE)에 대한 속성과 함께 CCMALWAYSINF=1 속성을 사용합니다. 인터넷 기반 클라이언트 관리에 대한 자세한 내용은 [인터넷 또는 신뢰할 수 없는 포리스트에서의 클라이언트 통신에 대한 고려 사항](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan)을 참조하세요.  

 예: `CCMSetup.exe /UsePKICert`  

### <a name="nocrlcheck"></a>/NoCRLCheck

 PKI 인증서를 사용하여 HTTPS를 통해 통신할 때 클라이언트에서 CRL(인증서 해지 목록)을 확인하지 않도록 지정합니다.  

 이 옵션을 지정하지 않으면 HTTPS 연결을 설정하기 전에 클라이언트에서 CRL을 확인합니다.  

 클라이언트 CRL 확인 하는 방법에 대 한 자세한 내용은 [PKI 인증서 해지 계획](../../plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs)을 참조 합니다.  

 예: `CCMSetup.exe /UsePKICert /NoCRLCheck`  

### <a name="configltconfiguration-file"></a>/config:&lt;구성 파일\>

클라이언트 설치 속성을 나열한 텍스트 파일의 이름을 지정합니다.

- **/noservice** CCMSetup 매개 변수를 지정하지 않을 경우 이 파일은 CCMSetup 폴더(32비트/64비트 운영 체제의 경우 %Windir%\\Ccmsetup)에 있어야 합니다.
- **/noservice** 매개 변수를 지정할 경우, 이 파일은 CCMSetup.exe를 실행하는 폴더와 동일한 폴더에 있어야 합니다.  

예: `CCMSetup.exe /config:&lt;Configuration File Name.txt\>`  

올바른 파일 형식을 제공하려면 사이트 서버의 &lt;Configuration Manager 디렉터리\>\\bin\\&lt;플랫폼\> 폴더에 있는 mobileclienttemplate.tcf 파일을 사용합니다. 이 파일에는 또한 섹션에 대한 설명과 섹션 사용 방법이 있습니다. 클라이언트 설치 섹션에서 다음 텍스트 뒤에 클라이언트 설치 속성을 지정합니다. **Install=INSTALL=ALL**.  

[클라이언트 설치] 섹션 항목의 예: `Install=INSTALL=ALL SMSSITECODE=ABC SMSCACHESIZE=100`  

### <a name="skipprereqltfilename"></a>/skipprereq:&lt;파일 이름\>

 Configuration Manager 클라이언트를 설치할 때 CCMSetup.exe가 지정된 필수 구성 요소 프로그램을 설치하지 않도록 지정합니다. 이 매개 변수는 둘 이상의 값 입력을 지원합니다. 각 값을 구분하려면 세미콜론(;)을 사용합니다.  


 예: `CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe` 또는 `CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe;windowsupdateagent30_x86.exe`  

### <a name="forceinstall"></a>/forceinstall

 CCMSetup.exe가 기존 클라이언트를 제거하고 새 클라이언트를 설치하도록 지정합니다.  

### <a name="excludefeaturesltfeature"></a>/ExcludeFeatures:&lt;기능\>

클라이언트를 설치할 때 CCMSetup.exe가 지정된 기능을 설치하지 않도록 지정합니다.  

예: `CCMSetup.exe /ExcludeFeatures:ClientUI`는 클라이언트에 소프트웨어 센터를 설치하지 않습니다.  

> [!NOTE]  
>  **/ExcludeFeatures** 매개 변수에 지원되는 값은 **ClientUI**뿐입니다.  



##  <a name="ccmsetupReturnCodes"></a> CCMSetup.exe 반환 코드  
 CCMSetup.exe 명령은 다음과 같은 완료된 반환 코드를 제공합니다. 문제를 해결하려면 클라이언트 컴퓨터의 ccmsetup.log 파일을 검토하여 반환 코드에 대한 컨텍스트 및 추가 세부 정보를 확인합니다.  

|반환 코드|의미|  
|-----------------|-------------|  
|0|성공|  
|6|오류|  
|7|다시 부팅 필요|  
|8|설치 프로그램이 이미 실행 중임|  
|9|필수 조건 평가 오류|  
|10|설치 매니페스트 해시 유효성 검사 오류|  



## <a name="ccmsetupMsiProps"></a> Ccmsetup.msi 속성  
 다음 속성은 ccmsetup.msi의 설치 동작을 수정할 수 있습니다.

### <a name="ccmsetupcmd"></a>CCMSETUPCMD 

ccmsetup.msi로 설치된 후에 ccmsetup.exe에 전달되는 명령줄 매개 변수와 속성을 지정합니다. 따옴표 안에 다른 속성을 포함합니다. Intune MDM 설치 방법을 사용하여 Configuration Manager 클라이언트를 부트스트래핑할 때 이 속성을 사용합니다. 

예: `ccmsetup.msi CCMSETUPCMD="/mp: https://mp.contoso.com CCMHOSTNAME=mp.contoso.com"`

 > [!Tip]
 > Microsoft Intune은 명령줄을 1024자로 제한합니다. 



##  <a name="clientMsiProps"></a> Client.msi 속성  
 다음 속성은 client.msi의 설치 동작을 수정할 수 있습니다. 클라이언트 강제 설치 방법을 사용하는 경우에는 **클라이언트 강제 설치 속성** 대화 상자의 **클라이언트** 탭에서 속성을 지정할 수도 있습니다.  


### <a name="aadclientappid"></a>AADCLIENTAPPID

Azure AD(Azure Active Directory) 클라이언트 앱 식별자를 지정합니다. 클라우드 관리에 대한 [Azure 서비스를 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)할 때 클라이언트 앱을 만들거나 가져옵니다. Azure 관리자가 Azure Portal에서 이 속성에 대한 값을 가져올 수 있습니다. 자세한 내용은 [애플리케이션 ID 가져오기](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)를 참조하세요. **AADCLIENTAPPID** 속성의 경우 해당 애플리케이션 ID는 "원시" 애플리케이션 형식을 위한 것입니다.

예: `ccmsetup.exe AADCLIENTAPPID=aa28e7f1-b88a-43cd-a2e3-f88b257c863b`


### <a name="aadresourceuri"></a>AADRESOURCEURI

Azure AD 서버 앱 식별자를 지정합니다. 클라우드 관리에 대한 [Azure 서비스를 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)할 때 서버 앱을 만들거나 가져옵니다. 서버 앱을 만드는 경우 서버 애플리케이션을 만들기 대화 상자에서 해당 속성은 **앱 ID URI**입니다.

Azure 관리자가 Azure Portal에서 이 속성에 대한 값을 가져올 수 있습니다. **Azure Active Directory** 블레이드의 **앱 등록**에서 서버 앱을 찾습니다. 이 앱은 "웹앱 / API" 애플리케이션 형식입니다. 앱을 열고 **설정** 및 **속성**을 차례로 클릭합니다. 이 AADRESOURCEURI 클라이언트 설치 속성에 대한 **앱 ID URI** 값을 사용합니다.

예: `ccmsetup.exe AADRESOURCEURI=https://contososerver`


### <a name="aadtenantid"></a>AADTENANTID

Azure AD 테넌트 식별자를 지정합니다. 클라우드 관리를 위한 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)할 때 이 테넌트는 Configuration Manager에 연결됩니다. 이 속성에 대한 값을 가져오려면 다음 단계를 사용합니다.
- 동일한 Azure AD 테넌트에 가입된 Windows 10 디바이스에서 명령 프롬프트를 엽니다.
- 다음 명령을 실행합니다. `dsregcmd.exe /status`
- 디바이스 상태 섹션에서 **TenantId** 값을 찾습니다. 예를 들면 `TenantId : 607b7853-6f6f-4d5d-b3d4-811c33fdd49a`

  > [!Note]
  > Azure 관리자는 Azure Portal에서 이 값을 가져울 수도 있습니다. 자세한 내용은 [테넌트 ID 가져오기](/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in) 참조

예: `ccmsetup.exe AADTENANTID=607b7853-6f6f-4d5d-b3d4-811c33fdd49a`

<!-- 
### AADTENANTNAME

Specifies the Azure AD tenant name. This tenant is linked to Configuration Manager when you [configure Azure services](/sccm/core/servers/deploy/configure/azure-services-wizard) for Cloud Management. To obtain the value for this property, use the following steps:
- On a Windows 10 device that is joined to the same Azure AD tenant, open a command prompt.
- Run the following command: `dsregcmd.exe /status`
- In the Device State section, find the **TenantName** value. For example, `TenantName : Contoso`

Example: `ccmsetup.exe AADTENANTNAME=Contoso`
-->

### <a name="ccmadmins"></a>CCMADMINS  

클라이언트 설정 및 정책에 대한 액세스를 부여할 하나 이상의 Windows 사용자 계정 또는 그룹을 지정합니다. 이 속성은 Configuration Manager 관리자에게 클라이언트 컴퓨터에 대한 로컬 관리자 자격 증명이 없는 경우에 유용합니다. 세미콜론으로 구분되는 계정 목록을 지정합니다.  

예: `CCMSetup.exe CCMADMINS="Domain\Account1;Domain\Group1"`  

### <a name="ccmallowsilentreboot"></a>CCMALLOWSILENTREBOOT

필요한 경우 클라이언트 설치 후에 컴퓨터를 다시 시작할 수 있도록 지정합니다.  

> [!IMPORTANT]  
>  사용자가 로그온되어 있더라도 경고 없이 컴퓨터가 다시 시작됩니다.  

예제: **CCMSetup.exe  CCMALLOWSILENTREBOOT**  

### <a name="ccmalwaysinf"></a>CCMALWAYSINF

 클라이언트가 항상 인터넷 기반으로 연결되고 인트라넷에 연결되지 않도록 지정하려면 **1**로 설정합니다. 클라이언트 연결 유형이 **항상 인터넷**으로 표시됩니다.  

 이 속성은 인터넷 기반 관리 지점의 FQDN을 지정하는 CCMHOSTNAME과 함께 사용합니다. 또한 CCMSetup 매개 변수 /UsePKICert 및 사이트 코드와 함께 사용합니다.  

 인터넷 기반 클라이언트 관리에 대한 자세한 내용은 [인터넷 또는 신뢰할 수 없는 포리스트에서의 클라이언트 통신에 대한 고려 사항](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan)을 참조하세요.  

 예: `CCMSetup.exe /UsePKICert  CCMALWAYSINF=1 CCMHOSTNAME=SERVER3.CONTOSO.COM SMSSITECODE=ABC`  

### <a name="ccmcertissuers"></a>CCMCERTISSUERS

 Configuration Manager 사이트에서 신뢰하는 신뢰할 수 있는 루트 CA(인증 기관) 인증서 목록인 인증서 발급자 목록을 지정합니다.  

 인증서 발급자 목록 및 클라이언트에서 인증서 선택 프로세스 중에 이 목록을 사용하는 방법에 대한 자세한 내용은 [PKI 클라이언트 인증서 선택 계획](../../plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection)을 참조하세요.  

 이 값은 루트 CA 인증서에 있는 주체 특성에 대해 대/소문자를 구분합니다. 특성은 쉼표(,) 또는 세미콜론(;)으로 구분할 수 있습니다. 구분줄을 사용하여 1 초과 루트 CA 인증서를 지정합니다. 예제:  

 `CCMCERTISSUERS="CN=Contoso Root CA; OU=Servers; O=Contoso, Ltd; C=US | CN=Litware Corporate Root CA; O=Litware, Inc."`  

> [!TIP]  
>  사이트에 대한 **CertificateIssuers=&lt;문자열\>** 을 복사하려면 사이트 서버 컴퓨터의 &lt;Configuration Manager 디렉터리\>\bin\\&lt;플랫폼\> 폴더에 있는 mobileclient.tcf 파일을 참조합니다.  

### <a name="ccmcertsel"></a>CCMCERTSEL

 클라이언트에 HTTPS 통신용 1 초과 인증서가 있는 경우 인증서 선택 기준을 지정합니다. 이 인증서는 클라이언트 인증 기능을 포함하는 유효한 인증서입니다.  

 정확하게 일치하는 항목( **Subject:** 사용) 또는 부분적으로 일치하는 항목( **SubjectStr: 사용)** 을 검색할 수 있습니다. 예제:  

 `CCMCERTSEL="Subject:computer1.contoso.com"`은 주체 이름 또는 주체 대체 이름에서 컴퓨터 이름 "computer1.contoso.com"과 정확히 일치하는 인증서를 검색합니다.  

 `CCMCERTSEL="SubjectStr:contoso.com"`은 주체 이름 또는 주체 대체 이름에 "contoso.com"이 포함된 인증서를 검색합니다.  

 또한 주체 이름 또는 주체 대체 이름 특성에 OID(개체 식별자) 또는 고유 이름 특성을 사용할 수도 있습니다.  

 `CCMCERTSEL="SubjectAttr:2.5.4.11 = Computers"`은(는) 개체 식별자와 명명된 컴퓨터로 표시된 부서 특성을 검색합니다.  

 `CCMCERTSEL="SubjectAttr:OU = Computers"`은(는) 고유 이름과 명명된 컴퓨터로 표시된 조직 구성 단위 특성을 검색합니다.  

> [!IMPORTANT]
>  주체 이름 상자를 사용할 경우 **Subject:** 는 대/소문자를 구분하고 **SubjectStr:** 은 대/소문자를 구분하지 않습니다.  
> 
>  주체 대체 이름 상자를 사용할 경우 <strong>Subject:</strong>와 **SubjectStr:** 은 대/소문자를 구분하지 않습니다.  

 인증서 선택에 사용할 수 있는 전체 특성 목록은 [PKI 인증서 선택 기준에 지원되는 특성 값](#BKMK_attributevalues)항목에 나와 있습니다.  

 검색 결과 일치하는 인증서가 둘 이상 있고 CCMFIRSTCERT 속성이 1로 설정된 경우 유효 기간이 가장 긴 인증서가 선택됩니다.  

### <a name="ccmcertstore"></a>CCMCERTSTORE

 HTTPS용 클라이언트 인증서가 컴퓨터 저장소의 기본 **개인** 인증서 저장소에 없는 경우 대체 인증서 저장소 이름을 지정합니다.  

 예: `CCMSetup.exe /UsePKICert CCMCERTSTORE="ConfigMgr"`  

### <a name="ccmdebuglogging"></a>CCMDEBUGLOGGING

  디버그 로깅을 사용합니다. 0(해제, 기본값) 또는 1(설정) 값을 설정할 수 있습니다. 이 속성은 클라이언트에서 문제 해결에 대한 하위 수준 정보를 기록하게 합니다. 모범 사례로, 프로덕션 사이트에서는 이 속성을 사용하지 마십시오. 과도한 로깅이 발생해 로그 파일에서 관련 정보를 찾기 어렵게 될 수 있습니다. 디버그 로깅을 사용하려면 CCMENABLELOGGING를 TRUE로 설정합니다.  

  예: `CCMSetup.exe CCMDEBUGLOGGING=1`  

### <a name="ccmenablelogging"></a>CCMENABLELOGGING

  기본적으로 로깅을 사용하려면 이 속성을 TRUE로 설정합니다. 로그 파일은 Configuration Manager 클라이언트 설치 폴더의 **Logs** 폴더에 저장됩니다. 기본적으로 이 폴더는 %Windir%\CCM\Logs입니다.  

  예: `CCMSetup.exe CCMENABLELOGGING=TRUE`  

### <a name="ccmevalinterval"></a>CCMEVALINTERVAL  

 클라이언트 상태 평가 도구(ccmeval.exe)가 실행되는 주기입니다. **1**~**1440**분일 수 있습니다. 기본적으로 하루에 한 번 실행합니다.  

### <a name="ccmevalhour"></a>CCMEVALHOUR

 클라이언트 상태 평가 도구(ccmeval.exe)가 실행되는 시간으로, **0**(자정)~**23**(오후 11기) 사이입니다. 기본적으로 자정에 실행합니다.  

### <a name="ccmfirstcert"></a>CCMFIRSTCERT

 이 속성이 1로 설정되면 클라이언트에서 유효 기간이 가장 긴 PKI 인증서가 선택됩니다.  

 예: `CCMSetup.exe /UsePKICert CCMFIRSTCERT=1`  


### <a name="ccmhostname"></a>CCMHOSTNAME

 클라이언트가 인터넷을 통해 관리되는 경우 이 속성은 인터넷 기반 관리 지점의 FQDN을 지정합니다.  

 설치 속성 SMSSITECODE=AUTO를 사용하여 이 옵션을 지정하지 마세요. 인터넷 기반 클라이언트가 인터넷 기반 사이트에 직접 할당되어야 합니다.  

 예: `CCMSetup.exe  /UsePKICert CCMHOSTNAME="SMSMP01.corp.contoso.com"`  

이 속성은 클라우드 관리 게이트웨이의 주소를 지정할 수 있습니다. 이 속성에 대한 값을 가져오려면 다음 단계를 사용합니다.
- 클라우드 관리 게이트웨이를 만듭니다.
- 활성 클라이언트에서 관리자 권한으로 Windows PowerShell 명령 프롬프트를 엽니다. 
- 다음 명령을 실행합니다. `(Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}).MP`
- 반환된 값을 있는 그대로 **CCMHOSTNAME** 속성과 함께 사용합니다.

`ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057598037248100`

 > [!Important]
 > **CCMHOSTNAME** 속성에 대한 클라우드 관리 게이트웨이 주소를 지정하는 경우 **https://** 같은 접두사를 추가하지 *마십시오*. 이 접두사는 오직 클라우드 관리 게이트웨이의 **/mp** URL과 함께 사용됩니다.



### <a name="ccmhttpport"></a>CCMHTTPPORT

 클라이언트가 HTTP를 통해 사이트 시스템 서버와 통신할 때 사용할 포트를 지정합니다. 기본적으로 포트 80으로 설정합니다.  

 예: `CCMSetup.exe CCMHTTPPORT=80`  

### <a name="ccmhttpsport"></a>CCMHTTPSPORT

클라이언트가 HTTPS를 통해 사이트 시스템 서버와 통신할 때 사용할 포트를 지정합니다. 기본적으로 포트 443으로 설정합니다.  

예: `CCMSetup.exe /UsePKICert CCMHTTPSPORT=443`  

### <a name="ccminstalldir"></a>CCMINSTALLDIR

 Configuration Manager 클라이언트 파일이 설치되는 폴더를 식별하고, 기본적으로 *%Windir%* \CCM입니다. 이러한 파일이 설치되는 위치에 관계없이 Ccmcore.dll 파일은 항상 *%Windir%\System32* 폴더에 설치됩니다. 또한 64비트 운영 체제에서 Ccmcore.dll 파일의 복사본은 항상 *%Windir%* \SysWOW64 폴더에 설치됩니다. 이 파일은 Configuration Manager SDK에서 32비트 버전의 클라이언트 API를 사용하는 32비트 애플리케이션을 지원합니다.  

 예: `CCMSetup.exe CCMINSTALLDIR="C:\ConfigMgr"`  

### <a name="ccmloglevel"></a>CCMLOGLEVEL

Configuration Manager 로그 파일에 쓸 세부 정보 수준을 지정합니다. 0~3의 정수를 지정합니다. 여기서 0은 가장 자세한 정보를 로깅하며, 3은 오류만 로깅합니다. 기본값은 1입니다.  

예: `CCMSetup.exe CCMLOGLEVEL=3`  

### <a name="ccmlogmaxhistory"></a>CCMLOGMAXHISTORY

Configuration Manager 로그 파일이 최대 크기에 도달하면 클라이언트는 백업으로 이름을 바꾸고 새 로그 파일을 만듭니다. 최대 크기는 기본적으로 250,000바이트 또는 CCMLOGMAXSIZE 속성에서 지정한 값입니다.

이 속성은 유지할 이전 버전의 로그 파일 수를 지정합니다. 기본값은 1입니다. 값을 0으로 설정하면 이전 로그 파일이 유지되지 않습니다.  

예: `CCMSetup.exe CCMLOGMAXHISTORY=0`  

### <a name="ccmlogmaxsize"></a>CCMLOGMAXSIZE

최대 로그 파일 크기(바이트)입니다. 로그가 지정된 크기로 성장하면 클라이언트는 기록 파일로 이름을 바꾸고 새 파일을 만듭니다. 이 속성은 10,000바이트 이상으로 설정해야 합니다. 기본값은 250,000바이트입니다.  

예: `CCMSetup.exe CCMLOGMAXSIZE=300000`  

### <a name="disablesiteopt"></a>DISABLESITEOPT

 TRUE로 설정된 경우 이 속성은 관리자의 능력이 **Configuration Manager** 제어판에서 할당된 사이트를 변경하지 못하게 합니다.  

 예제: **CCMSetup.exe DISABLESITEOPT=TRUE**  

### <a name="disablecacheopt"></a>DISABLECACHEOPT

TRUE로 설정된 경우 이 속성은 관리자의 능력이 **Configuration Manager** 제어판에서 클라리어트 캐시 폴더 설정을 변경하지 못하게 합니다.  

예: `CCMSetup.exe DISABLECACHEOPT=TRUE`  

### <a name="dnssuffix"></a>DNSSUFFIX

 DNS에 게시된 관리 지점을 찾으려면 클라이언트의 DNS 도메인을 지정합니다. 관리 지점을 찾으면 계층의 다른 관리 지점에 대한 정보를 클라이언트에 알립니다. 이 속성은 DNS 게시를 사용하여 찾은 관리 지점은 클라이언트 사이트에 있을 필요가 없지만 계층에 있는 어떠한 관리 지점일 수 있다는 것을 의미합니다.  

> [!NOTE]  
>  클라이언트가 게시된 관리 지점과 동일한 도메인에 있으면 이 속성을 지정하지 않아도 됩니다. 이 경우, 관리 지점의 DNS를 검색하는 데 자동으로 클라이언트의 도메인이 사용됩니다.  

 Configuration Manager 클라이언트에 대한 서비스 위치 방법으로 DNS 게시에 대한 자세한 내용은 [서비스 위치 및 클라이언트에서 자신의 할당된 관리 지점을 확인하는 방법](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location)을 참조하세요.  

> [!NOTE]  
>  기본적으로 DNS 게시는 Configuration Manager에서 사용되지 않습니다.  

 예: `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=contoso.com`  

### <a name="fsp"></a>FSP

Configuration Manager 클라이언트 컴퓨터에서 전송한 상태 메시지를 받아서 처리하는 대체 상태 지점을 지정합니다.  

대체 상태 지점에 대한 자세한 내용은 [대체 상태 지점 필요 여부 결정](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#fallback-status-point)을 참조하세요.  

예: `CCMSetup.exe FSP=SMSFP01`  

### <a name="ignoreappvversioncheck"></a>IGNOREAPPVVERSIONCHECK

 클라이언트 설치 전에 Microsoft App-V(Application Virtualization)의 최소 필수 버전을 확인하지 않도록 지정합니다.  

> [!IMPORTANT]  
>  App-V를 설치하지 않고 Configuration Manager 클라이언트를 설치하면 가상 애플리케이션을 배포할 수 없습니다.  

 예: `CCMSetup.exe IGNOREAPPVVERSIONCHECK=TRUE`  

### <a name="notifyonly"></a>NOTIFYONLY

클라이언트가 상태를 보고하지만 발견되는 문제를 해결하지 않도록 지정합니다.  

예: `CCMSetup.exe NOTIFYONLY=TRUE`  

자세한 내용은 [클라이언트 상태를 구성하는 방법](configure-client-status.md)을 참조하세요.  

### <a name="resetkeyinformation"></a>RESETKEYINFORMATION

 클라이언트에 잘못된 Configuration Manager의 신뢰할 수 있는 루트 키가 있고 신뢰할 수 있는 관리 지점에 연결하여 새 신뢰할 수 있는 루트 키를 받을 수 없는 경우, 이 속성을 사용하여 이전 신뢰할 수 있는 루트 키를 수동으로 제거합니다. 이 상황은 한 사이트 계층 구조에서 다른 사이트 계층 구조로 클라이언트를 이동하는 경우 발생할 수 있습니다. 이 속성은 HTTP 및 HTTPS 클라이언트 통신을 사용하는 클라이언트에 적용됩니다.  

 예: `CCMSetup.exe RESETKEYINFORMATION=TRUE`  

### <a name="sitereassign"></a>SITEREASSIGN

[SMSSITECODE](#smssitecode)=AUTO와 함께 사용할 경우 클라이언트 업그레이드에 자동 사이트 다시 할당을 사용하도록 설정합니다.

예: `CCMSetup.exe SMSSITECODE=AUTO SITEREASSIGN=TRUE`

### <a name="smscachedir"></a>SMSCACHEDIR

임시 파일을 저장하는 클라이언트 컴퓨터에 클라이언트 캐시 폴더의 위치를 지정합니다. 기본적으로 위치는 *%Windir \ccmcache*입니다.  

예: `CCMSetup.exe SMSCACHEDIR="C:\Temp"`  

이 속성은 SMSCACHEFLAGS 속성과 함께 사용되어 클라이언트 캐시 폴더의 위치를 제어할 수 있습니다.  

예: `CCMSetup.exe SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE`는 사용 가능한 가장 큰 클라이언트 디스크 드라이브에 클라이언트 캐시 폴더를 설치합니다.  

### <a name="smscacheflags"></a>SMSCACHEFLAGS

클라이언트 캐시 폴더에 대한 추가적인 설치 세부 정보를 지정합니다. SMSCACHEFLAGS 속성은 개별적으로 사용하거나 세미콜론으로 구분하여 함께 사용할 수 있습니다. 이 속성이 지정되지 않으면 SMSCACHEDIR 속성에 따라 클라이언트 캐시 폴더가 설치되고, 폴더가 압축되지 않으며, SMSCACHESIZE 값이 폴더 크기(MB)로 사용됩니다.  

기존 클라이언트를 업그레이드하는 경우 이 설정이 무시됩니다.  

속성:  

-   PERCENTDISKSPACE: 총 디스크 공간의 백분율로 폴더 크기를 지정합니다. 이 속성을 지정하는 경우 사용할 백분율 값으로 SMSCACHESIZE 속성도 지정해야 합니다.  

-   PERCENTFREEDISKSPACE: 사용 가능한 디스크 공간의 백분율로 폴더 크기를 지정합니다. 이 속성을 지정하는 경우 사용할 백분율 값으로 SMSCACHESIZE 속성도 지정해야 합니다. 예를 들어 디스크에 사용 가능한 공간이 10MB이고 SMSCACHESIZE가 50으로 지정되어 있으면 폴더 크기가 5MB로 설정됩니다. 이 속성은 PERCENTDISKSPACE 속성과 함께 사용할 수 없습니다.  

-   MAXDRIVE: 사용 가능한 가장 큰 디스크에 폴더를 설치하도록 지정합니다. SMSCACHEDIR 속성을 사용하여 경로가 지정된 경우 이 값이 무시됩니다.  

-   MAXDRIVESPACE: 사용 가능한 공간이 가장 많은 디스크 드라이브에 폴더를 설치하도록 지정합니다. SMSCACHEDIR 속성을 사용하여 경로가 지정된 경우 이 값이 무시됩니다.  

-   NTFSONLY: NTFS 디스크 드라이브에만 폴더를 설치할 수 있도록 지정합니다. SMSCACHEDIR 속성을 사용하여 경로가 지정된 경우 이 값이 무시됩니다.  

-   COMPRESS: 폴더를 압축된 형태로 저장하도록 지정합니다.  

-   FAILIFNOSPACE: 폴더를 설치할 공간이 부족할 경우 클라이언트 소프트웨어를 제거하도록 지정합니다.  

예: `CCMSetup.exe SMSCACHEFLAGS=NTFSONLY;COMPRESS`  


### <a name="smscachesize"></a>SMSCACHESIZE

> [!IMPORTANT]
> 클라이언트 캐시 폴더 크기를 지정하는 데 클라이언트 설정을 사용할 수 있습니다. 이러한 클라이언트 설정이 추가되면서 client.msi 속성으로 SMSCACHESIZE를 사용하여 클라이언트 캐시의 크기를 지정할 필요가 없어졌습니다. 자세한 내용은 [캐시 크기에 대한 클라이언트 설정](about-client-settings.md#client-cache-settings)을 참조하세요.  

<!-- For 1602 and earlier, SMSCACHESIZE specifies the size of the client cache folder in megabyte (MB) or as a percentage when used with the PERCENTDISKSPACE or PERCENTFREEDISKSPACE property. If this property isn't set, the folder defaults to a maximum size of 5120 MB. The lowest value that you can specify is 1 MB.  -->

> [!NOTE]  
>  다운로드해야 할 새 패키지로 인해 폴더가 최대 크기를 초과하고 사용 가능한 공간을 충분히 확보하기 위해 폴더를 제거할 수 없는 경우 패키지 다운로드가 실패하고 프로그램 또는 애플리케이션이 실행되지 않습니다.  

이 설정은 기존 클라이언트를 업그레이드하고 클라이언트에서 소프트웨어 업데이트를 다운로드하는 경우 무시됩니다.  

예: `CCMSetup.exe SMSCACHESIZE=100`  

> [!NOTE]  
>  클라이언트를 다시 설치하는 경우 SMSCACHESIZE 또는 SMSCACHEFLAGS 설치 속성을 사용하여 이전보다 더 작게 캐시 크기를 설정할 수 없습니다. 이 작업을 수행하려고 하면 해당 값이 무시됩니다. 캐시 크기가 자동으로 이전 크기로 설정됩니다.  

### <a name="smsconfigsource"></a>SMSCONFIGSOURCE

Configuration Manager 설치 관리자가 구성 설정을 확인하는 위치와 순서를 지정합니다. 이 속성은 하나 이상의 문자의 문자열이며, 각 문자가 특정 구성 원본을 정의합니다. 문자 값 R, P, M, U를 따로 또는 함께 사용합니다.  

- R: 레지스트리에서 구성 설정을 확인합니다.  

  자세한 내용은 [레지스트리에 클라이언트 설치 속성을 저장하는 방법에 대한 정보](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Provision)를 참조하세요.  

- P: 명령 프롬프트에 제공된 설치 속성에서 구성 설정을 확인합니다.  

- M: 이전 클라이언트를 Configuration Manager 클라이언트 소프트웨어로 업그레이드할 때 기존 설정을 확인합니다.  

- U: 설치된 클라이언트를 최신 버전으로 업그레이드하고 할당된 사이트 코드를 사용합니다.  

  기본적으로 클라이언트 설치 시 `PU` 가 사용되어 먼저 설치 속성이 확인된 다음 기존 속성이 확인됩니다.  

  예: `CCMSetup.exe SMSCONFIGSOURCE=RP`  

### <a name="smsdirectorylookup"></a>SMSDIRECTORYLOOKUP

 클라이언트에서 HTTP 연결을 수락하는 관리 지점을 찾기 위해 WINS(Windows Internet Name Service)를 사용할 수 있는지 여부를 지정합니다. 클라이언트는 Active Directory Domain Services 또는 DNS에서 관리 지점을 찾을 수 없는 경우 이 방법을 사용합니다.  

 이 속성은 클라이언트가 이름 확인을 위해 WINS를 사용하는지 여부에 영향을 주지 않습니다.  

 이 속성에 두 가지 모드를 구성할 수 있습니다.  

-   NOWINS: 이 값은 이 속성에 대한 가장 안전한 설정으로서 클라이언트가 WINS에서 관리 지점을 찾을 수 없게 합니다. 이 설정을 사용하는 경우 클라이언트에서 인트라넷의 관리 지점을 찾기 위한 다른 방법(예: Active Directory Domain Services 또는 DNS 게시 사용)을 갖추어야 합니다.  

-   WINSSECURE(기본값): 이 모드에서는 HTTP 통신을 사용하는 클라이언트가 WINS를 통해 관리 지점을 찾을 수 있습니다. 그러나 클라이언트가 관리 지점에 성공적으로 연결할 수 있으려면 신뢰할 수 있는 루트 키의 복사본이 있어야 합니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK)을 참조하세요.  


 예: `CCMSetup.exe SMSDIRECTORYLOOKUP=NOWINS`  

### <a name="smsmp"></a>SMSMP

Configuration Manager 클라이언트가 사용할 초기 관리 지점을 지정합니다.  

> [!IMPORTANT]  
>  관리 지점에서 HTTPS를 통한 클라이언트 연결만 수락하는 경우 관리 지점 이름 앞에 https://를 붙여야 합니다.  

예: `CCMSetup.exe SMSMP=smsmp01.contoso.com`

예: `CCMSetup.exe SMSMP=https://smsmp01.contoso.com`  


### <a name="smspublicrootkey"></a>SMSPUBLICROOTKEY

 Active Directory Domain Services에서 검색할 수 없는 Configuration Manager의 신뢰할 수 있는 루트 키를 지정합니다. 이 속성은 HTTP 및 HTTPS 클라이언트 통신을 사용하는 클라이언트에 적용됩니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK)을 참조하세요.  

 예: `CCMSetup.exe SMSPUBLICROOTKEY=&lt;key\>`  

### <a name="smsrootkeypath"></a>SMSROOTKEYPATH

 Configuration Manager의 신뢰할 수 있는 루트 키를 다시 설치하는 데 사용됩니다. 신뢰할 수 있는 루트 키를 포함하는 파일의 전체 경로 및 파일 이름을 지정합니다. 이 속성은 HTTP 및 HTTPS 클라이언트 통신을 사용하는 클라이언트에 적용됩니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK)을 참조하세요.  

 예제: 'CCMSetup.exe SMSROOTKEYPATH=&lt;전체 경로 및 파일 이름\>`  

### <a name="smssigncert"></a>SMSSIGNCERT

 사이트 서버에서 내보낸 자체 서명된 인증서의 전체 경로와 .cer 파일 이름을 지정합니다.  

 이 인증서는 **SMS** 인증서 저장소에 저장되어 있으며 주체 이름이 **사이트 서버** 이고 이름이 **사이트 서버 서명 인증서**입니다.  

 예제: **CCMSetup.exe /UsePKICert SMSSIGNCERT=&lt;전체 경로 및 파일 이름\>**  

### <a name="smssitecode"></a>SMSSITECODE

 클라이언트를 할당할 Configuration Manager 사이트를 지정합니다. 이 값은 3자리 사이트 코드 또는 AUTO라는 단어가 될 수 있습니다. AUTO를 지정하거나 이 속성을 지정하지 않는 경우 클라이언트는 Active Directory 도메인 서비스 또는 지정된 관리 지점에서 해당 사이트 할당을 파악하려고 합니다. 클라이언트 업그레이드에 AUTO를 사용하려면 [SITEREASSIGN](#sitereassign)도 TRUE로 설정해야 합니다.    

> [!NOTE]  
>  인터넷 기반 관리 지점(CCMHOSTNAME)도 지정하는 경우 AUTO를 사용하지 마세요. 이 경우, 클라이언트를 사이트에 직접 할당해야 합니다.  

 예: `CCMSetup.exe SMSSITECODE=XZY`  

##  <a name="BKMK_attributevalues"></a> PKI 인증서 선택 기준에 지원되는 특성 값  
 Configuration Manager는 PKI 인증서 선택 기준에 다음 특성 값을 지원합니다.  

|OID 특성|고유 이름 특성|특성 정의|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|도메인 구성 요소|  
|1.2.840.113549.1.9.1|E 또는 E-mail|전자 메일 주소|  
|2.5.4.3|CN|일반 이름|  
|2.5.4.4|SN|주체 이름|  
|2.5.4.5|SERIALNUMBER|일련 번호|  
|2.5.4.6|C|국가 코드|  
|2.5.4.7|L|소재지|  
|2.5.4.8|S 또는 St.|시/도 이름|  
|2.5.4.9|STREET|주소|  
|2.5.4.10|O|조직 이름|  
|2.5.4.11|OU|조직 구성 단위|  
|2.5.4.12|T 또는 Title|제목|  
|2.5.4.42|G 또는 GN 또는 GivenName|이름|  
|2.5.4.43|I 또는 Initials|이니셜|  
|2.5.29.17|(값 없음)|주체 대체 이름|  
