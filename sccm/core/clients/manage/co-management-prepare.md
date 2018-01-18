---
title: "공동 관리를 위해 Windows 10 장치 준비"
description: "공동 관리를 위해 Windows 10 장치를 준비하는 방법을 알아봅니다."
keywords: 
author: dougeby
manager: angrobe
ms.date: 11/20/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: 
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: d605dd4770be6878b08f4ac61da6ab27e3b6d61f
ms.sourcegitcommit: ac9268e31440ffe91b133c2ba8405d885248d404
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/08/2018
---
# <a name="prepare-windows-10-devices-for-co-management"></a>공동 관리를 위해 Windows 10 장치 준비
AD 및 Azure AD에 조인하고, Intune과 Configuration Manager에서 클라이언트를 등록하는 Windows 10 장치에서 공동 관리를 사용할 수 있습니다. 새 Windows 10 장치 및 Intune에 이미 등록된 장치의 경우 공동 관리되기 전에 Configuration Manager 클라이언트를 설치합니다. Configuration Manager 클라이언트인 Windows 10 장치의 경우 Intune에서 장치를 등록하고 Configuration Manager 콘솔에서 공동 관리를 사용할 수 있습니다.

## <a name="command-line-to-install-configuration-manager-client"></a>Configuration Manager 클라이언트를 설치하는 명령줄
이미 Configuration Manager 클라이언트가 아닌 Windows 10 장치에 대한 앱을 Intune에서 만들어야 합니다. 다음 섹션에서 앱을 만들 때 다음 명령줄을 사용합니다.

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