---
title: "기술 미리 보기 1709"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager용 Technical Preview 버전 1709에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3ef6bdc-a204-4c4c-a02f-2bd03f35183e
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: f0acc5ae0d8207dce92c56a4c80e8321faf51393
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1709-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1709의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1709에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**이 Technical Preview의 알려진 문제:**
-   **수동 모드의 사이트 서버가 있는 경우 미리 보기 1709 버전에 대한 업데이트가 실패합니다**. 미리 보기 1706, 1707 또는 1708 버전을 실행하고 [수동 모드의 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 경우 미리 보기 사이트를 1709 버전으로 성공적으로 업데이트하려면 먼저 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 1709 버전을 실행한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="improved-vpn-profile-experience-in-configuration-manager-console"></a>Configuration Manager 콘솔에서 개선된 VPN 프로필
<!-- 1313282 -->
이 릴리스에서 선택된 플랫폼에 적절한 설정을 표시하기 위해 VPN 프로필 마법사 및 속성 페이지를 업데이트했습니다. 특히:

- 각 플랫폼에는 고유한 워크플로가 있습니다. 즉, 새 VPN 프로필에는 플랫폼에서 지원되는 설정만 포함됩니다.
- 이제 **지원되는 플랫폼** 페이지는 **일반** 페이지 뒤에 표시됩니다.  이제 속성 값을 설정하기 전에 플랫폼을 선택합니다.
- 플랫폼이 **Android**, **Android for Work** 또는 **Windows Phone 8.1**로 설정되면 **지원되는 플랫폼** 페이지는 필요하지 않으므로 표시되지 않습니다.
- Configuration Manager 클라이언트 기반 워크플로는 하이브리드 모바일 장치(MDM) 클라이언트 기반 Windows 10 워크플로와 결합되었습니다. 모두 동일한 설정을 지원합니다.
- 각 플랫폼 워크플로에는 해당 워크플로에 대한 적절한 설정만이 포함됩니다.  예를 들어, Android 워크플로에는 Android에 적절한 설정이 포함되고 iOS 또는 Windows 10 Mobile에 적절한 설정은 Android 워크플로에 더 이상 표시되지 않습니다.
- Windows 8.1 장치의 경우 Configuration Manager에서 관리하는 설정은 명확하게 표시됩니다.
- 자동 VPN 페이지는 사용되지 않으며 제거되었습니다.

이러한 변경 내용은 새 VPN 프로필에 적용됩니다.  

호환성 위험을 최소화하기 위해 기존 VPN 프로필은 변경되지 않습니다.  기존 프로필을 편집하는 경우 프로필을 만들 때와 마찬가지로 설정이 표시됩니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기

일반적인 프로세스를 사용하여 새 VPN 프로필을 만듭니다. VPN 프로필 마법사의 옵션에서 첫 번째 페이지가 변경되었습니다.

1.  **자산 및 준수** > **개요** > **규정 준수 설정** > **회사 리소스 액세스** > **VPN 프로필**로 이동한 후 **VPN 프로필 만들기**를 선택합니다.
2.  **일반** 페이지에서 이름을 입력하고 **만들려는 VPN 프로필의 유형 지정** 아래에서 다음 옵션 중 하나를 선택합니다.

    - Windows 10  
    - Windows 8.1  
    - Windows Phone 8.1  
    - iOS 및 macOS  
    - Android  
    - Android for Work  

3.  **Windows 8.1**을 선택하는 경우 **새 프로필 만들기** 또는 **파일에서 가져오기**에 대한 옵션도 제공됩니다.
4.  마법사를 완료하여 프로필 만들기를 완료합니다.

다른 플랫폼을 선택하면 선택한 플랫폼과 관련된 설정만 표시됩니다.

## <a name="co-management-for-windows-10-devices"></a>Windows 10 장치의 공동 관리    
<!-- 1350871 -->
고객은 보통 낮은 비용으로 간소화된 클라우드 기반 솔루션을 사용하여 모바일 장치를 관리하는 동일한 방식으로 Windows 10 장치를 관리하려고 합니다. 그러나 기존 관리에서 최신 관리로 전환하기가 어려울 수 있습니다. Windows 10 버전 1607(Anniversary Update라고도 함)부터는 Windows 10 장치를 온-프레미스 AD(Active Directory)와 클라우드 기반 Azure AD에 동시에 조인할 수 있습니다(하이브리드 Azure AD). 공동 관리에서는 이 향상된 기능을 사용하며 Configuration Manager 및 Intune을 둘 다 사용하여 Windows 10 장치를 동시에 관리할 수 있게 해줍니다. 이것은 기존 관리에서 최신 관리에 대한 연결을 제공하고 단계별 접근 방법을 사용하여 전환할 수 있는 경로를 제공하는 솔루션입니다. 

### <a name="prerequisites"></a>전제 조건
공동 관리를 활성화하기 전에 다음 필수 구성 요소를 준비해야 합니다. 기존 Configuration Manager 클라이언트 및 클라이언트가 아닌 장치에 대한 일반 전제 조건 및 다른 필수 구성 요소가 있습니다.

### <a name="known-issues"></a>알려진 문제
공동 관리 정책을 만든 후에 정책을 편집할 수 없습니다. 정책을 변경하려면 삭제한 다음 필요한 설정을 사용하여 다시 만듭니다. 

#### <a name="general-prerequisites"></a>일반 전제 조건
다음은 공동 관리를 사용하기 위한 일반 전제 조건입니다.  

- Configuration Manager용 Technical Preview 버전 1709
- Azure AD 
- 모든 사용자의 EMS 또는 Intune 라이선스
- **Intune**으로 설정된 Intune 구독 및 Intune의 MDM 기관

   > [!Note]  
   > 하이브리드 MDM 환경(Configuration Manager와 통합된 Intune)이 설정된 경우 공동 관리를 사용할 수 없습니다. Intune 독립 실행형으로 마이그레이션하는 방법을 알아보려면 [하이브리드 MDM에서 Intune 독립 실행형으로 마이그레이션 시작](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.

#### <a name="additional-prerequisites-for-existing-configuration-manager-clients"></a>기존 Configuration Manager 클라이언트용 추가 필수 구성 요소
- Windows 10, 버전 1709(가을 크리에이터 업데이트) 이상
- 하이브리드 Azure AD 조인(AD와 Azure AD에 조인)

#### <a name="additional-prerequisites-for-new-windows-10-devices"></a>새 Windows 10 장치용 추가 필수 구성 요소
- Windows 10, 버전 1709(가을 크리에이터 업데이트) 이상
- Configuration Manager의 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway)

### <a name="workloads-you-can-switch-to-intune"></a>Intune으로 전환할 수 있는 작업
공동 관리를 활성화한 후에 Configuration Manager가 계속 모든 워크로드를 관리합니다. 준비되었는지 결정할 때 Intune으로 사용 가능한 워크로드를 관리하기 시작할 수 있습니다. 이 릴리스에서 Intune으로 다음과 같은 워크로드를 관리할 수 있습니다.   

#### <a name="compliance-policies"></a>규정 준수 정책
규정 준수 정책은 장치가 조건부 액세스 정책을 준수하는 것으로 간주되기 위해 준수해야 하는 규칙 및 설정을 정의합니다. 준수 정책을 사용하여 조건부 액세스와 독립적으로 장치를 모니터링하고 준수 문제를 수정할 수도 있습니다. 자세한 내용은 [장치 규정 준수 정책](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/device-compliance-policies)를 참조하세요.  

#### <a name="windows-update-for-business-policies"></a>비즈니스용 Windows 업데이트 정책
비즈니스용 Windows 업데이트 정책을 통해 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 장치에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. 자세한 내용은 [비즈니스용 Windows 업데이트 지연 정책 구성](https://docs.microsoft.com/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies)을 참조하세요.  

### <a name="remote-actions-available-in-intune-on-azure-for-co-managed-devices"></a>Azure의 Intune에서 공동 관리 장치에 사용할 수 있는 원격 작업
Windows 10 장치가 공동 관리를 사용하도록 설정한 경우 Azure의 Intune에서 다음과 같은 원격 작업을 사용할 수 있습니다.  
- [초기화](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
- [선택적 초기화](https://docs.microsoft.com/intune/apps-selective-wipe)
- [장치 삭제](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
- [장치 다시 시작](https://docs.microsoft.com/intune/device-restart)
- [새로운 시작](https://docs.microsoft.com/intune/device-fresh-start)

### <a name="prepare-intune-for-co-management"></a>공동 관리를 위해 Intune 준비
Configuration Manager에서 Intune으로 워크로드를 전환하기 전에 Intune에서 장치를 계속 보호하기 위해 필요한 프로필 및 정책을 만듭니다.
Configuration Manager에 있는 개체를 기반으로 Intune에서 개체를 만들 수 있습니다. 또는 현재 전략이 레거시나 기존 관리를 기반으로 하는 경우 최신 관리에 필요한 정책 및 프로필을 재고하기 위해 단계를 뒤로 돌릴 수 있습니다. 다음 리소스를 사용하여 정책 및 프로필을 만듭니다.    
<!-- - [Device compliance policies](https://docs.microsoft.com/intune/compliance-policy-create-windows)  -->
- [비즈니스용 Windows 업데이트 정책](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
- [장치 구성 프로필](https://docs.microsoft.com/intune/device-profile-create)  

### <a name="architectural-overview-for-co-management"></a>공동 관리에 대한 아키텍처 개요
다음 다이어그램은 공동 관리의 아키텍처 개요 및 기존 구성 및 Intune 인프라에 맞추는 방법을 제공합니다.

![공동 관리 아키텍처 다이어그램](./media/co-management-arch-cm1709tp.svg)

### <a name="scenarios-to-enable-co-management"></a>공동 관리를 사용하도록 설정하는 시나리오  
공동 관리를 Microsoft Intune에 등록된 Windows 10 장치 및 기존 Windows 10 Configuration Manager 클라이언트 모두에서 사용할 수 있습니다. 두 시나리오는 Windows 10 장치를 Configuration Manager와 Intune에서 동시에 관리하고 AD와 Azure AD에 조인합니다.  

#### <a name="devices-enrolled-in-intune"></a>Intune에 등록된 장치  
Windows 10 장치를 Intune에 등록하는 경우 공동 관리를 위해 클라이언트를 준비하기 위해 (특정 명령줄 인수를 사용하여) 장치에 Configuration Manager 클라이언트를 설치할 수 있습니다. 그런 다음 Configuration Manager 콘솔에서 공동 관리를 사용하여 특정 Windows 10 장치의 Intune에 특정 워크로드를 이동하기 시작합니다.  

아직 Intune에 등록되지 않은 Windows 10 장치의 경우 Azure에서 자동 등록을 사용하여 장치를 등록할 수 있습니다. 새 Windows 10 장치의 경우 Windows AutoPilot를 사용하여 OOBE(Out of Box Experience)를 구성할 수 있습니다. 여기에는 Intune에서 장치를 등록하는 자동 등록을 포함합니다.  

#### <a name="configuration-manager-clients"></a>Configuration Manager 클라이언트
Windows 10 장치가 Configuration Manager 클라이언트에 있는 경우 이러한 장치를 등록하고 Configuration Manager 콘솔에서 공동 관리를 사용할 수 있습니다. Configuration Manager는 Azure AD 테넌트 정보에 따라 Intune에 자동 등록을 트리거합니다.  

### <a name="prepare-windows-10-devices-for-co-management"></a>공동 관리를 위해 Windows 10 장치 준비
AD 및 Azure AD에 조인하고, Intune과 Configuration Manager에서 클라이언트를 등록하는 Windows 10 장치에서 공동 관리를 사용할 수 있습니다. 새 Windows 10 장치 및 Intune에 이미 등록된 장치의 경우 공동 관리되기 전에 Configuration Manager 클라이언트를 설치합니다. Configuration Manager 클라이언트인 Windows 10 장치의 경우 Intune에서 장치를 등록하고 Configuration Manager 콘솔에서 공동 관리를 사용할 수 있습니다.

#### <a name="command-line-to-install-configuration-manager-client"></a>Configuration Manager 클라이언트를 설치하는 명령줄
Configuration Manager 클라이언트가 아닌 Windows 10 장치의 경우 Intune에서 앱을 만듭니다. 다음 섹션에서 앱을 만들 때 다음 명령줄을 사용합니다.

ccmsetup.msi CCMSETUPCMD="/mp:&#60;*클라우드 관리 게이트웨이 상호 인증 끝점의 URL*&#62;/ CCMHOSTNAME=&#60;*클라우드 관리 게이트웨이 상호 인증 끝점의 URL*&#62; SMSSiteCode=&#60;*Sitecode*&#62; SMSMP=https:&#47;/&#60;*MP의 FQDN*&#62; AADTENANTID=&#60;*AAD 테넌트 ID*&#62; AADTENANTNAME=&#60;*테넌트 이름*&#62; AADCLIENTAPPID=&#60;*AAD 통합용 Server AppID*&#62; AADRESOURCEURI=https:&#47;/&#60;*리소스 ID*&#62;”

예를 들어, 다음 값을 포함하는 경우:

- **클라우드 관리 게이트웨이 상호 인증 끝점의 URL**: https:/&#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    

   >[!Note]    
   >**클라우드 관리 게이트웨이 상호 인증 끝점의 URL** 값에 **vProxy_Roles** SQL 보기의 **MutualAuthPath** 값을 사용합니다.

- **MP(관리 지점)의 FQDN**: sccmmp.corp.contoso.com    
- **Sitecode**: PS1    
- **Azure AD 테넌트 ID**: 72F988BF-86F1-41AF-91AB-2D7CD011XXXX    
- **Azure AD 테넌트 이름**: contoso    
- **Azure AD 클라이언트 앱 ID**: bef323b3-042f-41a6-907a-f9faf0d1XXXX     
- **AAD 리소스 ID URI**: ConfigMgrServer    

  > [!Note]    
  > **AAD 리소스 ID URI** 값에 **vSMS_AAD_Application_Ex** SQL 보기에서 찾은 **IdentifierUri** 값을 사용합니다.

다음 명령줄을 사용합니다.

ccmsetup.msi CCMSETUPCMD="/mp:https:/&#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode=PS1 SMSMP=https:/&#47;sccmmp.corp.contoso.com AADTENANTID=72F988BF-86F1-41AF-91AB-2D7CD011XXXX AADTENANTNAME=contoso  AADCLIENTAPPID=bef323b3-042f-41a6-907a-f9faf0d1XXXX AADRESOURCEURI=https:/&#47;ConfigMgrServer”

> [!Tip]
>다음 단계를 사용하여 사이트에 대한 명령줄 매개 변수를 찾을 수 있습니다.     
> 1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.  
> 2. the Manage group의 the Home tab에서  **공동 관리 구성**을 선택하여 공동 관리 등록 마법사를 엽니다.    
> 3. 구독 페이지에서 **로그인**을 클릭하고 Intune 테넌트에 로그인하고 **다음**을 클릭합니다.    
> 4. 사용 페이지의 **Intune의 등록된 장치** 섹션에서 **복사**를 클릭하여 명령줄을 클립보드에 복사하고 명령줄을 저장하여 앱을 만드는 절차에서 사용합니다.  
> 5. **취소**를 클릭하여 마법사를 종료합니다.

#### <a name="new-windows-10-devices"></a>새 Windows 10 장치
새 Windows 10 장치에서는 Autopilot 서비스를 사용하여 기본 환경을 구성합니다. 여기에는 AD와 Azure AD에 장치를 조인하고 Intune에서 장치를 등록하는 작업이 포함됩니다. 그런 다음 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다.  
1. 새 Windows 10 장치에 AutoPilot을 사용합니다. 자세한 내용은 [Windows AutoPilot 개요](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot)를 참조하세요.  
2. 장치를 Intune에 자동으로 등록하도록 Azure AD에서 자동 등록을 구성합니다. 자세한 내용은  [Microsoft Intune에 Windows 장치 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.
3. Configuration Manager 클라이언트 패키지를 사용하여 Intune에서 앱을 만들고 공동 관리하려는 Windows 10 장치에 앱을 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.   

#### <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Intune 또는 Configuration Manager 클라이언트에 등록되지 않은 Windows 10 장치
Intune 또는 Configuration Manager 클라이언트에 등록되지 않은 Windows 10 장치의 경우 자동 등록을 사용하여 Intune에서 장치를 등록할 수 있습니다. 그런 다음 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다.
1. 장치를 Intune에 자동으로 등록하도록 Azure AD에서 자동 등록을 구성합니다. 자세한 내용은  [Microsoft Intune에 Windows 장치 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.  
2. Configuration Manager 클라이언트 패키지를 사용하여 Intune에서 앱을 만들고 공동 관리하려는 Windows 10 장치에 앱을 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.

#### <a name="windows-10-devices-enrolled-in-intune"></a>Intune에 등록된 Windows 10 장치
이미 Intune에 등록된 Windows 10 장치의 경우 Intune에서 앱을 만들어 Configuration Manager 클라이언트를 배포합니다. [Azure AD를 사용하여 인터넷에서 클라이언트를 설치](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 단계를 수행할 때 [Configuration Manager 클라이언트를 설치하는 명령줄](#command-line-to-install-configuration-manager-client)을 사용합니다.  

### <a name="switch-configuration-manager-workloads-to-intune"></a>Configuration Manager 워크로드를 Intune으로 전환
이전 섹션에서 공동 관리를 위해 Windows 10 장치를 준비했습니다. 이제 이러한 장치가 AD와 Azure AD에 조인되고 Intune에 등록되고 Configuration Manager 클라이언트를 포함합니다. Windows 10 장치가 AD에 조인되고 Configuration Manager 클라이언트를 포함했지만 Azure AD에 되거나 Intune에 등록되지 않았습니다. 다음 절차에서는 공동 관리를 사용하고, 공동 관리를 위해 나머지 Windows 10 장치(Intune에 등록되지 않은 Configuration Manager 클라이언트)를 준비하고, 특정 Configuration Manager 워크로드를 Intune으로 전환하기 시작할 수 있는 단계를 제공합니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.    
2. the Manage group의 the Home tab에서  **공동 관리 구성**을 선택하여 공동 관리 등록 마법사를 엽니다.    
3. 구독 페이지에서 **로그인**을 클릭하고 Intune 테넌트에 로그인하고 **다음**을 클릭합니다.   
4. 스테이징 페이지에서 다음 설정을 구성한 후에 **다음**을 클릭합니다.
    - **파일럿 그룹**: 파일럿 그룹에는 선택한 하나 이상의 컬렉션이 포함됩니다. 이 그룹을 공동 관리의 단계별 롤아웃 중 일부로 사용합니다. 작은 테스트 컬렉션을 시작하고, 공동 관리를 더 많은 사용자 및 장치에 롤아웃하는 경우 파일럿 그룹에 더 많은 컬렉션을 추가할 수 있습니다. 공동 관리 속성에서 언제든지 파일럿 그룹의 컬렉션을 변경할 수 있습니다.
    - **프로덕션**: 이 설정을 선택하면 지원되는 모든 Windows 10 장치가 공동 관리를 사용할 수 있습니다. 하나 이상의 컬렉션을 포함하여 **제외 그룹**을 구성합니다. 이 그룹에 있는 컬렉션의 멤버인 장치는 공동 관리를 사용하지 않도록 제외됩니다. 
5. 사용 페이지에서 (스테이징 페이지에 구성된 설정에 따라) **파일럿** 또는 **모두** 중 하나를 선택하여 Intune에 자동 등록을 활성화한 후 **다음**을 클릭합니다. **파일럿**을 선택하는 경우 파일럿 그룹의 멤버인 Configuration manager 클라이언트만이 Intune에서 자동으로 등록됩니다. 이 기능을 사용하면 클라이언트의 하위 집합에서 공동 관리를 사용하여 처음에 공동 관리를 테스트하고 단계적 접근을 사용하여 공동 관리를 롤아웃할 수 있습니다. 
6. 워크로드 페이지에서 Configuration Manager 워크로드를 Intune에서 관리하도록 전환할지를 선택하고 **다음**을 클릭합니다. 슬라이더를 사용하여 (스테이징 페이지에서 구성한 설정에 따라) 워크로드를 파일럿 그룹으로 전활할지 아니면 모든 Windows 10 클라이언트로 전환할지를 선택합니다. 
7. 공동 관리를 사용하려면 마법사를 완료합니다.  

<!--### Modify your co-management settings
After you enable co-management using the wizard, you can modify your target group and change the workloads that are managed by Configuration Manager and Intune.  
- In the Configuration Manager console, go to **Administration** > **Overview** > **Cloud Services** > **Co-management**.  
Select the co-management object, and then on the Home tab, click **Properties**. -->   

<!--### Monitor co-management
After you have enabled co-management, you can monitor which devices are managed by Configuration Manager and which are managed by Intune. You can also see which Configuration Manager workloads are managed by which product.-->

## <a name="see-also"></a>참고 항목
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요. 
