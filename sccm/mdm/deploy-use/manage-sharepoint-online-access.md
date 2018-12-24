---
title: SharePoint Online 액세스 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager SharePoint Online 조건부 액세스 정책을 사용하여 OneDrive에 대한 액세스를 관리하는 방법을 알아봅니다.
ms.date: 12/09/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 49cec466-1676-4fe2-a2fe-5004f01d735e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f723110abdb94dd96fb2ed7f52af681d27fccf87
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32351907"
---
# <a name="manage-sharepoint-online-access-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 SharePoint Online 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*


**SharePoint Online**의 Configuration Manager 조건부 액세스 정책은 SharePoint Online에 저장된 비즈니스용 OneDrive 파일에 대한 액세스를 관리합니다. 액세스는 지정한 조건을 기반으로 합니다.
나열된 플랫폼에 대해 다음 앱에서의 SharePoint Online에 대한 액세스를 제어할 수 있습니다.  

-   Microsoft Office Mobile(Android)  

-   Microsoft OneDrive(Android 및 iOS)  

-   Microsoft Word(Android 및 iOS)  

-   Microsoft Excel(Android 및 iOS)  

-   Microsoft PowerPoint(Android 및 iOS)  

-   Microsoft OneNote(Android 및 iOS)

Office 데스크톱 응용 프로그램은 다음을 실행하는 SharePoint Online에 액세스할 수 있습니다.  

-   [최신 인증](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) 이 사용되는 Office 데스크톱 2013 이상  

-   Windows 7.0 또는 Windows 8.1  

> [!NOTE]  
>  PC는 도메인에 가입되어 있거나 Intune에 설정된 정책을 준수해야 합니다.  



 대상 사용자가 자신의 디바이스에 있는 OneDrive와 같은 지원되는 앱을 사용하여 파일에 연결하려고 하면 다음 평가 작업이 수행됩니다.  

 ![ConditionalAccess8&#45;6](media/ConditionalAccess8-6.png)  

 필수 파일에 연결하려면 OneDrive를 실행 중인 디바이스에서 다음을 수행해야 합니다.  

-   Microsoft Intune에 등록되어 있거나 도메인에 가입된 PC여야 합니다.  

-   Azure AD(Azure Active Directory)에 디바이스를 등록합니다. 이 등록은 디바이스가 Intune에 등록될 때 자동으로 수행됩니다.  

     도메인에 가입된 PC의 경우 Azure AD에 [자동으로 등록](/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)되도록 설정해야 합니다.  

-   배포된 Configuration Manager 준수 정책을 준수해야 합니다.  

    Azure AD는 디바이스 상태를 저장합니다. 지정한 조건에 따라 파일에 대한 액세스를 허용하거나 차단합니다.  

    조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.  

-   디바이스를 Intune에 등록하지 않았거나 Azure AD에 등록하지 않은 경우, 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.  

-   디바이스가 호환되지 않으면 사용자를 Intune 웹 포털로 안내하는 메시지가 표시됩니다. 문제에 대한 정보와 이를 해결하는 방법을 찾을 수 있습니다.  

- 모바일 디바이스의 경우:

  **iOS** 및 **Android** 장치의 브라우저에서 액세스할 때 SharePoint Online에 대한 액세스를 제한할 수 있습니다. 규격 디바이스의 지원되는 브라우저에서만 액세스가 허용됩니다.  
    - Safari(iOS)
    - Chrome(Android)
    - 관리되는 브라우저(iOS 및 Android)  

    지원되지 않는 브라우저는 차단됩니다.  

-   PC의 경우:  


    -   정책이 도메인 가입을 요구하도록 설정되어 있지만 PC가 도메인에 가입되지 않은 경우 IT 관리자에게 문의하라는 메시지가 표시됩니다.  

    -   정책이 도메인 가입 또는 준수를 요구하도록 설정되어 있는 경우 PC가 요구 사항을 충족하지 못하면 회사 포털 앱을 설치하고 등록하는 방법에 대한 지침이 포함된 메시지가 표시됩니다.  

다음 앱의 SharePoint Online 액세스를 차단할 수 있습니다.  

-   Microsoft Office Mobile(Android)  

-   Microsoft OneDrive(Android 및 iOS)  

-   Microsoft Word(Android 및 iOS)  

-   Microsoft Excel(Android 및 iOS)  

-   Microsoft PowerPoint(Android 및 iOS)  

-   Microsoft OneNote(Android 및 iOS)  



## <a name="configure-conditional-access-for-sharepoint-online"></a>SharePoint Online에 대한 조건부 액세스 구성  

### <a name="step-1-configure-active-directory-security-groups"></a>1단계: Active Directory 보안 그룹 구성  
 시작하기 전에 조건부 액세스 정책에 대한 Azure AD 보안 그룹을 구성합니다. **Office 365 관리 센터**또는 **Intune 계정 포털**에서 이러한 그룹을 구성할 수 있습니다. 이러한 그룹에는 정책의 대상이 되거나 정책에서 제외된 사용자가 포함됩니다. 사용자가 정책의 대상인 경우 사용자가 사용하는 각 디바이스가 정책을 준수해야 리소스에 액세스할 수 있습니다.  

 SharePoint Online 정책에 두 그룹 유형을 지정할 수 있습니다.  

-   **대상 그룹**: 정책이 적용되는 사용자 그룹을 포함합니다.  

-   **제외된 그룹**: 정책에서 제외되는 사용자 그룹을 포함합니다(선택 사항).  

 사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2단계: 규정 준수 정책 구성 및 배포  
 SharePoint Online 정책의 대상이 되는 모든 디바이스에 대한 준수 정책을 만들고 배포합니다.  

> [!NOTE]   
>  준수 정책을 Intune 그룹 또는 Configuration Manager 컬렉션에 배포하는 동안에는 조건부 액세스 정책의 대상이 Azure AD 보안 그룹으로 지정됩니다.  

 준수 정책을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 디바이스 규정 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)를 참조하세요.  

> [!IMPORTANT]  
>  준수 정책을 배포하지 않은 다음, SharePoint Online 정책을 사용하도록 설정하면 대상으로 지정된 모든 디바이스에 대한 액세스가 허용됩니다.  

   

###  <a name="BKMK_OneDrive"></a> 3단계: SharePoint Online 정책 구성  

 다음으로 관리되고 규정을 준수하는 디바이스만 SharePoint Online에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure AD에 저장됩니다.

 >[!NOTE]
 >Azure AD 관리 콘솔에서 조건부 액세스 정책을 만들 수도 있습니다. Azure AD 관리 콘솔을 사용하면 Intune 디바이스의 조건부 액세스 정책을 만들 수 있습니다. Azure AD는 이러한 정책을 디바이스 기반 조건부 액세스 정책으로 참조합니다. 다단계 인증과 같은 다른 조건부 액세스 정책을 만들 수도 있습니다. 포털에서 Azure AD가 지원하는 Salesforce, Box 등의 타사 엔터프라이즈 앱에 대한 조건부 액세스 정책을 설정할 수 있습니다. 자세한 내용은 [Azure AD 연결 응용 프로그램에 대한 액세스 제어를 위해 Azure AD 디바이스 기반 조건부 액세스 정책을 설정하는 방법](/azure/active-directory/active-directory-conditional-access-policy-connected-applications)을 참조하세요.  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **SharePoint Online에 대한 조건부 액세스 정책 사용**을 선택합니다.  

     ![IntuneSASharePointOnlineCAPolicy](media/IntuneSASharePointOnlineCAPolicy.png)  

3.  최신 인증을 사용하는 앱 및 Outlook용 **응용 프로그램 액세스**에서 각 플랫폼에 대한 규정을 준수하는 디바이스에만 액세스를 제한하도록 선택할 수 있습니다.  

    > [!TIP]  
    >  **최신 인증**을 사용하는 경우 Office 클라이언트에서 ADAL(Active Directory Authentication Library) 기반 로그인이 가능합니다.  
    >   
    >  -   ADAL 기반 인증을 사용하면 Office 클라이언트가 브라우저 기반 인증(수동 인증이라고도 함)을 수행할 수 있게 됩니다. 사용자는 인증 시 로그인 웹 페이지로 이동됩니다.  
    > -   이 새로운 로그인 방법을 적용하는 경우 **디바이스 준수** 및 **다단계 인증** 수행 여부에 따라 조건부 액세스 등의 새로운 시나리오를 사용할 수 있습니다.  
    >   
    >  자세한 내용은 [Office 2013및 Office 2016 클라이언트 앱의 최신 인증 작동 방식](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517)을 참조하세요.  

     Windows PC의 경우 해당 PC가 도메인에 가입되어 있거나 Intune에 등록되어 있고 정책을 준수해야 합니다. 다음 요구 사항을 설정할 수 있습니다.  

    -   **장치가 도메인에 가입되거나 규정을 준수해야 함**: PC가 도메인에 가입되어 있거나 Intune에 설정된 정책을 준수해야 합니다. PC가 이러한 요구 사항을 하나라도 충족하지 않을 경우 Intune에 디바이스를 등록하라는 메시지가 표시됩니다.  

    -   **장치가 도메인에 가입되어 있어야 함**: PC가 도메인에 가입되어 있어야 Exchange Online에 액세스할 수 있습니다. PC가 도메인에 가입되지 않은 경우, 이메일 액세스가 차단되고 IT 관리자에게 문의하라는 메시지가 사용자에게 표시됩니다.  

    -   **장치가 규정을 준수해야 함**: PC가 Intune에 등록되어 있고 규정을 준수해야 합니다. PC가 등록되어 있지 않은 경우 등록 방법에 대한 지침이 포함된 메시지가 표시됩니다.  

4.  SharePoint Online 및 비즈니스용 OneDrive에 대한 **브라우저 액세스**에서, 지원되는 브라우저인 Safari(iOS) 및 Chrome(Android)을 통해서만 Exchange Online에 대한 액세스를 허용하도록 선택할 수 있습니다. 다른 브라우저에서의 액세스는 차단됩니다. OneDrive에 대한 응용 프로그램 액세스에 선택한 것과 동일한 플랫폼 제한 사항이 여기에도 적용됩니다.

    **Android** 장치에서 사용자는 다음과 같이 등록된 장치에서 **브라우저 액세스 사용** 옵션을 사용해야 합니다.
    1.  **회사 포털 앱**을 시작합니다.
    2.  세 개의 점(...) 또는 하드웨어 메뉴 단추에서 **설정** 페이지로 이동합니다.
    3.  **브라우저 액세스 사용** 단추를 누릅니다.
    4.  Chrome 브라우저에서, Office 365에서 로그아웃하고 Chrome을 다시 시작합니다.

    **iOS 및 Android** 플랫폼에서는 Azure AD가 서비스에 액세스하는 데 사용되는 장치를 식별하기 위해 TLS 인증서를 장치에 발급합니다. 이 디바이스는 다음 스크린샷과 같이 인증서를 표시하면서 최종 사용자에게 해당 인증서를 선택하라는 메시지를 표시합니다. 최종 사용자는 이 인증서를 선택해야 브라우저를 계속 사용할 수 있습니다.

     **Android**

     ![iPad에서 인증서 프롬프트에 대한 스크린샷](media/mdm-browser-ca-ios-cert-prompt_v2.png)

     **OWA(Outlook Web Access)**

      ![Android 디바이스에서 인증서 프롬프트에 대한 스크린샷](media/mdm-browser-ca-android-cert-prompt.png)

4.  **홈** 탭의 **링크** 그룹에서 **Intune 콘솔에서 조건부 액세스 정책 구성**을 클릭합니다. Configuration Manager와 Intune을 연결하는 데 사용되는 계정의 사용자 이름과 암호를 입력해야 할 수 있습니다.  

     Intune 관리 콘솔이 열립니다.  

5.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **조건부 액세스** > **SharePoint Online 정책**을 클릭합니다.  

6.  **장치가 정책을 준수하지 않는 경우 앱의 SharePoint Online 액세스 차단**을 선택합니다.  

7.  **대상 그룹**에서 **수정**을 클릭하여 정책을 적용할 Azure AD 보안 그룹을 선택합니다.  

8.  **제외된 그룹**에서 필요에 따라 **수정**을 클릭하여 이 정책에서 제외된 Azure AD 보안 그룹을 선택합니다.  

9. 작업이 끝나면 **저장**을 클릭합니다.  

 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.  

 Intune 콘솔에서 정책을 모니터링하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용한 SharePoint Online 액세스 관리](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)를 참조하세요.  

### <a name="see-also"></a>참고 항목  

 [System Center Configuration Manager에서 서비스 액세스 관리](../../protect/deploy-use/manage-access-to-services.md)
