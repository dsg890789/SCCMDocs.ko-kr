---
title: 공동 관리를 위해 Windows 10 준비
titleSuffix: Configuration Manager
description: 공동 관리를 위해 Windows 10 디바이스를 준비하는 방법을 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 09/10/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: ac7f67a02602473a7635d8c70e4b1b1dc04363bc
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53417050"
---
# <a name="prepare-windows-10-devices-for-co-management"></a>공동 관리를 위해 Windows 10 디바이스 준비
AD 및 Azure AD에 조인하고, Microsoft Intune과 Configuration Manager에서 클라이언트를 등록하는 Windows 10 디바이스에서 공동 관리를 사용할 수 있습니다. 새 Windows 10 디바이스 및 Intune에 이미 등록된 디바이스의 경우 공동 관리되기 전에 Configuration Manager 클라이언트를 설치합니다. Configuration Manager 클라이언트인 Windows 10 디바이스의 경우 Intune에서 디바이스를 등록하고 Configuration Manager 콘솔에서 공동 관리를 사용할 수 있습니다.

> [!IMPORTANT]
> Windows 10 모바일 디바이스는 공동 관리를 지원하지 않습니다.



## <a name="prerequisites"></a>필수 구성 요소

공동 관리를 활성화하기 전에 다음 필수 구성 요소를 준비해야 합니다. Configuration Manager 클라이언트가 있는 디바이스와 클라이언트가 설치되지 않은 디바이스에 대한 일반 필수 구성 요소 및 다른 필수 구성 요소가 있습니다.


### <a name="general-prerequisites"></a>일반 전제 조건

다음은 공동 관리를 사용하기 위한 일반 전제 조건입니다.  

- Configuration Manager 버전 1710 이상  

    - Configuration Manager 버전 1806부터 단일 Intune 테넌트에 여러 Configuration Manager 인스턴스를 연결할 수 있습니다. <!--1357944-->  

- [클라우드 관리를 위해 Azure AD에 등록된 사이트](/sccm/core/servers/deploy/configure/azure-services-wizard)  

- 모든 사용자의 EMS 또는 Intune 라이선스  

- 사용하도록 설정된 [Azure AD 자동 등록](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)  

- **Intune**으로 설정된 Intune 구독 및 Intune의 MDM 기관.  

    - [혼합 기관](/sccm/mdm/deploy-use/migrate-mixed-authority)을 사용 중인 경우 먼저 Intune 독립 실행형으로 마이그레이션을 완료합니다. 그런 다음, 공동 관리를 설정하기 전에 MDM 기관을 Intune으로 설정합니다.<!--SCCMDocs issue #797-->


> [!NOTE]
> 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. 그러나 사용자를 Intune 독립 실행형으로 마이그레이션하기 시작한 후 관련 Windows 10 디바이스에 공동 관리를 활성화할 수 있습니다. Intune 독립 실행형으로 마이그레이션하는 방법에 대한 자세한 정보는 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.


### <a name="prerequisite-azure-resource-manager-roles"></a>필수 Azure Resource Manager 역할
<!--SCCMDocs issue #667--> Azure 역할에 대한 자세한 내용은 [서로 다른 역할의 이해](https://docs.microsoft.com/azure/role-based-access-control/rbac-and-directory-admin-roles)를 참조하세요.

|작업|필요한 역할|
|----|----|
|클라우드 관리 게이트웨이 설정|Azure 구독 관리자|
|클라우드 배포 지점 설정|Azure 구독 관리자|
|Configuration Manager 콘솔에서 Azure Active Directory 앱 만들기|Azure Active Directory 글로벌 관리자|
|Configuration Manager 콘솔에서 Azure 클라이언트 및 서버 앱 가져오기| Configuration Manager 관리자, Azure 역할이 추가로 필요하지 않습니다.|
|공동 관리 마법사를 통한 공동 관리 설정| 모든 범위 권한이 있는 Configuration Manager 관리자 및 Azure Active Directory 사용자 권한 


### <a name="additional-prerequisites-for-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 있는 디바이스에 대한 추가 필수 구성 요소

- Windows 10, 버전 1709 이상  

- [하이브리드 Azure 조인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)(AD 및 Azure AD에 조인) 또는 Azure AD 조인 전용(이 유형은 "클라우드 도메인 조인"이라고도 함).


### <a name="additional-prerequisites-for-devices-without-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 없는 디바이스에 대한 추가 필수 구성 요소

- Windows 10, 버전 1709 이상  

- Configuration Manager의 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway)(Intune을 사용하여 Configuration Manager 클라이언트를 설치하는 경우)  


> [!IMPORTANT]
> Windows 10 모바일 디바이스는 공동 관리를 지원하지 않습니다.



## <a name="command-line-to-install-configuration-manager-client"></a>Configuration Manager 클라이언트를 설치하는 명령줄

Configuration Manager 클라이언트가 아닌 Windows 10 디바이스의 경우 Intune에서 앱을 만듭니다. 이를 수행하려면 다음 단계를 따르십시오.

1. portal.azure.com으로 이동한 다음, Intune 블레이드를 엽니다.
2. **클라이언트 앱** > **앱** > **추가**를 클릭합니다. 
3. **기타**에서 **기간 업무 앱**을 선택합니다.
4. Ccmsetup.msi 앱 패키지 파일을 업로드합니다. (이 파일은 사이트 서버의 *<ConfigMgr 설치 디렉터리*\bin\i386 폴더에 있습니다.) 
5. 앱을 업데이트한 후 다음 명령줄 인수를 실행하여 앱 정보를 구성합니다.

`ccmsetup.msi CCMSETUPCMD="/mp:<URL of cloud management gateway mutual auth endpoint> CCMHOSTNAME=<URL of cloud management gateway mutual auth endpoint> SMSSiteCode=<Sitecode> SMSMP=https://<FQDN of MP> AADTENANTID=<AAD tenant ID> AADCLIENTAPPID=<Server AppID for AAD Integration> AADRESOURCEURI=https://<Resource ID>"`

#### <a name="example-command-line-input"></a>예제 명령줄 입력
다음 값이 있는 경우

- **클라우드 관리 게이트웨이 상호 인증 엔드포인트의 URL**: `https://contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500`    

   >[!NOTE]    
   >**클라우드 관리 게이트웨이 상호 인증 엔드포인트의 URL** 값에 **vProxy_Roles** SQL 보기의 **MutualAuthPath** 값을 사용합니다.  

- **MP(관리 지점)의 FQDN** : `mp1.contoso.com`    
- **Sitecode**: `PS1`    
- **Azure AD 테넌트 ID**: `44b5bdda-67f5-4850-bdf4-a8ef611109e0`    
- **Azure AD 클라이언트 앱 ID**: `51e781eb-aac6-4265-8030-4cd1ddaa9dd0`     
- **AAD 리소스 ID URI**: `ConfigMgrServer`    

  > [!NOTE]    
  > **AAD 리소스 ID URI** 값에 **vSMS_AAD_Application_Ex** SQL 보기에서 찾은 **IdentifierUri** 값을 사용합니다.  

그런 다음, 다음 명령줄을 사용합니다.

`ccmsetup.msi CCMSETUPCMD="/mp:https://contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500    CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=PS1 SMSMP=https://mp1.contoso.com AADTENANTID=44b5bdda-67f5-4850-bdf4-a8ef611109e0 AADCLIENTAPPID=51e781eb-aac6-4265-8030-4cd1ddaa9dd0 AADRESOURCEURI=https://ConfigMgrServer"`


<!--1358215--> 버전 1806부터 더 적은 명령줄 속성이 필요합니다.  

- 모든 시나리오에서 다음 명령줄 속성이 필요합니다.  
    - CCMHOSTNAME  
    - SMSSITECODE  

- 다음 속성은 PKI 기반의 클라이언트 인증 인증서 대신 클라이언트 인증용 Azure AD를 사용하는 경우 필요합니다.  
    - AADCLIENTAPPID  
    - AADRESOURCEURI  

- 클라이언트가 인트라넷으로 다시 로밍되는 경우 다음 속성이 필요합니다.  
    - SMSMP  

다음 예제에서는 위의 속성 모두를 포함합니다.   
`ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com`

자세한 내용은 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties)을 참조합니다.


> [!TIP]
> 다음 단계를 사용하여 사이트에 대한 명령줄 매개 변수를 찾습니다.     
> 
> 1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다.  
> 
> 2. 리본 메뉴에서 **공동 관리 구성**을 선택하여 공동 관리 등록 마법사를 엽니다. (공동 관리를 이미 설정한 경우 **속성**을 선택합니다. 그런 다음, 4단계로 건너뜁니다.)    
> 
> 3. 구독 페이지에서 **로그인**을 선택합니다. Intune 테넌트에 로그인한 다음, **다음**을 클릭합니다.    
> 
> 4. 사용 여부 페이지에서 **복사**를 선택하여 명령줄을 클립보드에 복사합니다. 그런 다음, 앱을 만드는 절차에서 사용할 명령줄을 저장합니다.  
> 
> 5. **취소**를 클릭하여 마법사를 종료합니다.  

> [!IMPORTANT]    
> Configuration Manager 클라이언트를 설치하도록 명령줄을 사용자 지정하는 경우 명령줄은 1024자를 초과하지 말아야 합니다. 명령줄이 1024자를 넘는 경우 클라이언트 설치에 실패합니다.



## <a name="new-windows-10-devices"></a>새 Windows 10 디바이스

새 Windows 10 디바이스에서는 Autopilot 서비스를 사용하여 기본 환경을 구성합니다. 여기에는 AD와 Azure AD에 디바이스를 조인하고 Intune에서 디바이스를 등록하는 작업이 포함됩니다. 그런 다음 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다.  

1. 새 Windows 10 디바이스에 AutoPilot을 사용합니다. 자세한 내용은 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot)를 참조하세요.    

   > [!NOTE]   
   > 버전 1802부터 Configuration Manager를 사용하여 비즈니스 및 교육용 Microsoft Store에서 필요한 디바이스 정보를 수집하고 보고합니다. 이 정보에는 디바이스 일련 번호, Windows 제품 식별자 및 하드웨어 식별자가 포함됩니다. Configuration Manager 콘솔, **모니터링** 작업 영역에서 **보고** 노드, **보고서**를 차례로 확장하고 **하드웨어 - 일반** 노드를 선택합니다. 새 보고서인 **Windows AutoPilot 디바이스 정보**를 실행하고 결과를 확인합니다. 보고서 뷰어에서 **내보내기** 아이콘을 클릭하고 **CSV(쉼표로 구분)** 옵션을 선택합니다. 파일을 저장한 후 비즈니스 및 교육용 Microsoft 스토어에 데이터를 업로드합니다. 자세한 내용은 [비즈니스 및 교육용 Microsoft 스토어에 디바이스 추가](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile)를 참조하세요.

2. 디바이스를 Intune에 자동으로 등록하도록 Azure AD에서 자동 등록을 구성합니다. 자세한 내용은  [Microsoft Intune에 Windows 디바이스 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.  

3. Configuration Manager 클라이언트 패키지를 사용하여 Intune에서 앱을 만들고 공동 관리하려는 Windows 10 디바이스에 앱을 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.   



## <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Intune 또는 Configuration Manager 클라이언트에 등록되지 않은 Windows 10 디바이스

Intune에 등록되지 않았거나 Configuration Manager 클라이언트가 있는 Windows 10 디바이스의 경우 자동 등록을 사용하여 Intune에서 디바이스를 등록할 수 있습니다. 그런 다음 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다.

1. 디바이스를 Intune에 자동으로 등록하도록 Azure AD에서 자동 등록을 구성합니다. 자세한 내용은  [Microsoft Intune에 Windows 디바이스 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.  

2. Configuration Manager 클라이언트 패키지를 사용하여 Intune에서 앱을 만들고 공동 관리하려는 Windows 10 디바이스에 앱을 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.



## <a name="windows-10-devices-enrolled-in-intune"></a>Intune에 등록된 Windows 10 디바이스

이미 Intune에 등록된 Windows 10 디바이스의 경우 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.  



## <a name="next-steps"></a>다음 단계

[Configuration Manager 워크로드를 Intune으로 전환](co-management-switch-workloads.md)
