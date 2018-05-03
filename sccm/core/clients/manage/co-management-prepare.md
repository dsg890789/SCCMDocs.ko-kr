---
title: 공동 관리를 위해 Windows 10 준비
titleSuffix: Configuration Manager
description: 공동 관리를 위해 Windows 10 장치를 준비하는 방법을 알아봅니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology: ''
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: 93a991cb3fd78e44f5ae4434a9845a57450e1025
ms.sourcegitcommit: e4ca9fb1fad2caaf61bb46e0a12f4d6b96f15513
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2018
---
# <a name="prepare-windows-10-devices-for-co-management"></a>공동 관리를 위해 Windows 10 장치 준비
AD 및 Azure AD에 조인하고, Microsoft Intune과 Configuration Manager에서 클라이언트를 등록하는 Windows 10 장치에서 공동 관리를 사용할 수 있습니다. 새 Windows 10 장치 및 Intune에 이미 등록된 장치의 경우 공동 관리되기 전에 Configuration Manager 클라이언트를 설치합니다. Configuration Manager 클라이언트인 Windows 10 장치의 경우 Intune에서 장치를 등록하고 Configuration Manager 콘솔에서 공동 관리를 사용할 수 있습니다.

> [!IMPORTANT]
> Windows 10 모바일 장치는 공동 관리를 지원하지 않습니다.


## <a name="prerequisites"></a>필수 구성 요소
공동 관리를 활성화하기 전에 다음 필수 구성 요소를 준비해야 합니다. 일반 필수 구성 요소 및 Configuration Manager 클라이언트가 있는 장치와 클라이언트가 설치되지 않은 장치에 대한 다른 필수 구성 요소가 있습니다.
### <a name="general-prerequisites"></a>일반 전제 조건
다음은 공동 관리를 사용하기 위한 일반 전제 조건입니다.  

- Configuration Manager 버전 1710 이상
- Azure AD
- 모든 사용자의 EMS 또는 Intune 라이선스
- 사용하도록 설정된 [Azure AD 자동 등록](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)
- **Intune**으로 설정된 Intune 구독 및 Intune의 MDM 기관


   > [!Note]  
   > 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. 그러나 사용자를 Intune 독립 실행형으로 마이그레이션하기 시작한 후 관련 Windows 10 장치에 공동 관리를 활성화할 수 있습니다. Intune 독립 실행형으로 마이그레이션하는 방법에 대한 자세한 정보는 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.

### <a name="additional-prerequisites-for-devices-with-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 있는 장치에 대한 추가 필수 구성 요소
- Windows 10, 버전 1709 이상
- [조인된 하이브리드 Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)(AD와 Azure AD에 조인)

### <a name="additional-prerequisites-for-devices-without-the-configuration-manager-client"></a>Configuration Manager 클라이언트가 없는 장치에 대한 추가 필수 구성 요소
- Windows 10, 버전 1709 이상
- Configuration Manager의 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway)(Intune을 사용하여 Configuration Manager 클라이언트를 설치하는 경우)

> [!IMPORTANT]
> Windows 10 모바일 장치는 공동 관리를 지원하지 않습니다.


## <a name="command-line-to-install-configuration-manager-client"></a>Configuration Manager 클라이언트를 설치하는 명령줄
Configuration Manager 클라이언트가 아닌 Windows 10 장치의 경우 Intune에서 앱을 만듭니다. 다음 섹션에서 앱을 만들 때 다음 명령줄을 사용합니다.

`ccmsetup.msi CCMSETUPCMD="/mp:<URL of cloud management gateway mutual auth endpoint> CCMHOSTNAME=<URL of cloud management gateway mutual auth endpoint> SMSSiteCode=<Sitecode> SMSMP=https://<FQDN of MP> AADTENANTID=<AAD tenant ID> AADCLIENTAPPID=<Server AppID for AAD Integration> AADRESOURCEURI=https://<Resource ID>"`

예를 들어, 다음 값을 포함하는 경우:

- **클라우드 관리 게이트웨이 상호 인증 끝점의 URL**: https:/&#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500    

   >[!Note]    
   >**클라우드 관리 게이트웨이 상호 인증 끝점의 URL** 값에 **vProxy_Roles** SQL 보기의 **MutualAuthPath** 값을 사용합니다.

- **MP(관리 지점)의 FQDN**: mp1.contoso.com    
- **Sitecode**: PS1    
- **Azure AD 테넌트 ID**: 60a413f4-c606-4744-8adb-9476ae3XXXXX    
- **Azure AD 클라이언트 앱 ID**: 9fb9315f-4c42-405f-8664-ae63283XXXXX     
- **AAD 리소스 ID URI**: ConfigMgrServer    

  > [!Note]    
  > **AAD 리소스 ID URI** 값에 **vSMS_AAD_Application_Ex** SQL 보기에서 찾은 **IdentifierUri** 값을 사용합니다.

다음 명령줄을 사용합니다.

`ccmsetup.msi CCMSETUPCMD="/mp:https://contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500    CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=PS1 SMSMP=https://mp1.contoso.com AADTENANTID=60a413f4-c606-4744-8adb-9476ae3XXXXX AADCLIENTAPPID=9fb9315f-4c42-405f-8664-ae63283XXXXX AADRESOURCEURI=https://ConfigMgrServer"`

> [!Tip]
> 다음 단계를 사용하여 사이트에 대한 명령줄 매개 변수를 찾을 수 있습니다.     
> 1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.  
> 2. the Manage group의 the Home tab에서  **공동 관리 구성**을 선택하여 공동 관리 등록 마법사를 엽니다.    
> 3. 구독 페이지에서 **로그인**을 클릭하고 Intune 테넌트에 로그인하고 **다음**을 클릭합니다.    
> 4. 사용 페이지의 **Intune의 등록된 장치** 섹션에서 **복사**를 클릭하여 명령줄을 클립보드에 복사하고 명령줄을 저장하여 앱을 만드는 절차에서 사용합니다.  
> 5. **취소**를 클릭하여 마법사를 종료합니다.

> [!Important]    
> Configuration Manager 클라이언트를 설치하도록 명령줄을 사용자 지정하는 경우 명령줄은 1024자를 초과하지 않아야 합니다. 명령줄이 1024자를 넘는 경우 클라이언트 설치에 실패합니다.


## <a name="new-windows-10-devices"></a>새 Windows 10 장치
새 Windows 10 장치에서는 Autopilot 서비스를 사용하여 기본 환경을 구성합니다. 여기에는 AD와 Azure AD에 장치를 조인하고 Intune에서 장치를 등록하는 작업이 포함됩니다. 그런 다음 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다.  
1. 새 Windows 10 장치에 AutoPilot을 사용합니다. 자세한 내용은 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot)를 참조하세요.    

   > [!NOTE]   
   > 버전 1802부터 Configuration Manager를 사용하여 비즈니스 및 교육용 Microsoft Store에서 필요한 장치 정보를 수집하고 보고합니다. 이 정보에는 장치 일련 번호, Windows 제품 식별자 및 하드웨어 식별자가 포함됩니다. Configuration Manager 콘솔, **모니터링** 작업 영역에서 **보고** 노드, **보고서**를 차례로 확장하고 **하드웨어 - 일반** 노드를 선택합니다. 새 보고서인 **Windows AutoPilot 장치 정보**를 실행하고 결과를 확인합니다. 보고서 뷰어에서 **내보내기** 아이콘을 클릭하고 **CSV(쉼표로 구분)** 옵션을 선택합니다. 파일을 저장한 후 비즈니스 및 교육용 Microsoft 스토어에 데이터를 업로드합니다. 자세한 내용은 [비즈니스 및 교육용 Microsoft 스토어에 장치 추가](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile)를 참조하세요.

2. 장치를 Intune에 자동으로 등록하도록 Azure AD에서 자동 등록을 구성합니다. 자세한 내용은  [Microsoft Intune에 Windows 장치 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.
3. Configuration Manager 클라이언트 패키지를 사용하여 Intune에서 앱을 만들고 공동 관리하려는 Windows 10 장치에 앱을 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.   

## <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Intune 또는 Configuration Manager 클라이언트에 등록되지 않은 Windows 10 장치
Intune 또는 Configuration Manager 클라이언트에 등록되지 않은 Windows 10 장치의 경우 자동 등록을 사용하여 Intune에서 장치를 등록할 수 있습니다. 그런 다음 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다.
1. 장치를 Intune에 자동으로 등록하도록 Azure AD에서 자동 등록을 구성합니다. 자세한 내용은  [Microsoft Intune에 Windows 장치 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.  
2. Configuration Manager 클라이언트 패키지를 사용하여 Intune에서 앱을 만들고 공동 관리하려는 Windows 10 장치에 앱을 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.

## <a name="windows-10-devices-enrolled-in-intune"></a>Intune에 등록된 Windows 10 장치
이미 Intune에 등록된 Windows 10 장치의 경우 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.  

## <a name="next-steps"></a>다음 단계
[Configuration Manager 워크로드를 Intune으로 전환](co-management-switch-workloads.md)