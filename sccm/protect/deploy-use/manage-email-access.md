---
title: "메일 액세스 관리 | System Center Configuration Manager"
description: "System Center Configuration Manager 조건부 액세스를 사용하여 Exchange 메일에 대한 액세스를 관리하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/04/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4544088a-4752-4e3a-aa0a-049f10d8f178
caps.latest.revision: 24
author: karthikaraman
ms.author: karaman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 5c6cf3c1697b49708aa5192b67b08b700da7dc72
ms.openlocfilehash: c1797910f2b7ceda451c2ccb23f66a4b2bd4b6ff


---
# <a name="manage-email-access-in-system-center-configuration-manager"></a>System Center Configuration Manager의 메일 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 조건부 액세스를 사용하면 지정한 조건에 따라 Exchange 메일에 대한 액세스를 관리할 수 있습니다.  

다음 전자 메일 프로그램에 대한 액세스를 관리할 수 있습니다.  

-   Microsoft Exchange 온-프레미스  

-   Microsoft Exchange Online  

-   Exchange Online Dedicated

기본 제공 전자 메일 클라이언트에서의 Exchange Online 및 Exchange 온-프레미스에 대한 액세스를 다음 플랫폼에서 제어할 수 있습니다.  

-   Android 4.0 이상, Samsung Knox Standard 4.0 이상  

-   iOS 7.1 이상  

-   Windows Phone 8.1 이상  

-   Windows 8.1 이상에 설치된 메일 응용 프로그램

Office 데스크톱 응용 프로그램은 다음을 실행하는 Exchange Online에 액세스할 수 있습니다.  

-   [최신 인증](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) 이 사용되는 Office 데스크톱 2013 이상  

-   Windows 7.0 또는 Windows 8.1  

> [!NOTE]  
>  PC는 도메인에 가입되어 있거나 Intune에 설정된 정책을 준수해야 합니다.  


## <a name="device-requirements"></a>장치 요구 사항
 조건부 액세스를 구성하면 사용자는 다음을 수행해야 자신의 전자 메일에 연결할 수 있습니다.  

-   Intune에 등록되어 있거나 도메인에 가입된 PC여야 합니다.  

-   Azure Active Directory에 장치를 등록해야 합니다(이 등록은 Intune을 사용하여 장치를 등록할 때 자동으로 이루어짐)(Exchange Online만 해당). 또한 Azure Active Directory를 사용하여 클라이언트 Exchange ID를 등록해야 합니다(Exchange 온-프레미스에 연결하는 Windows 및 Windows Phone 장치에는 적용되지 않음).  

     도메인에 가입된 PC의 경우 Azure Active Directory에 자동으로 등록하도록 설정해야 합니다.  [System Center Configuration Manager에서 서비스 액세스 관리](../../protect/deploy-use/manage-access-to-services.md) 항목의 **PC에 대한 조건부 액세스** 섹션에 PC에 대한 조건부 액세스를 사용하기 위한 전체 요구 사항 집합이 나열됩니다.  

-   장치가 해당 장치에 배포된 Configuration Manager 준수 정책을 준수해야 합니다.  

 조건부 액세스 조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.  

-   장치가 Intune에 등록되지 않았거나 Azure Active Directory에 등록되지 않은 경우, 회사 포털 앱을 설치하고 장치를 등록하고 (Android 및 iOS 장치의 경우) 메일을 활성화하여 Azure Active Directory에서 장치의 Exchange ActiveSync ID를 장치 기록과 연결하는 방법에 대한 지침이 포함된 메시지가 표시됩니다.  

-   장치가 정책을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Intune 웹 포털 및 문제를 해결하는 방법을 알려주는 메시지가 표시됩니다.  

**모바일 장치의 경우:**

**iOS** 및 **Android** 장치의 브라우저에서 액세스될 경우 Exchange Online에서 **OWA(Outlook Web Access)** 에 대한 액세스를 제한할 수 있습니다.  호환 장치의 지원되는 브라우저에서만 액세스할 수 있습니다.

* Safari(iOS)
* Chrome(Android)
* 관리되는 브라우저(iOS 및 Android)

지원되지 않는 브라우저는 차단됩니다. IOS 및 Android 용 OWA 앱은 지원되지 않습니다.  이러한 브라우저는 ADFS 클레임 규칙을 통해 차단해야 합니다.
* 최신 인증 이외의 인증 프로토콜을 차단하도록 ADFS 클레임 규칙을 설정해야 합니다. 자세한 지침은 시나리오 3 - [브라우저 기반 응용 프로그램을 제외한 모든 O365 액세스 차단](https://technet.microsoft.com/library/dn592182.aspx)에서 제공됩니다.

 **PC의 경우:**  

-   조건부 액세스 정책 요구 사항이 **도메인에 가입** 또는 **규정**을 허용하는 경우 장치를 등록하는 방법에 대한 지침이 포함된 메시지가 표시됩니다. PC가 요구 사항을 하나라도 충족하지 않을 경우 장치를 Intune에 등록하라는 메시지가 표시됩니다.  

-   조건부 액세스 정책 요구 사항이 도메인에 가입된 Windows 장치만 허용하도록 설정된 경우 해당 장치가 차단되고 IT 관리자에게 문의하라는 메시지가 표시됩니다.  

 다음 플랫폼의 장치 기본 제공 Exchange ActiveSync 전자 메일 클라이언트에서 Exchange 전자 메일에 대 한 액세스를 차단할 수 있습니다.  

-   Android 4.0 이상, Samsung Knox Standard 4.0 이상  

-   iOS 7.1 이상  

-   Windows Phone 8.1 이상  

-   Windows 8.1 이상에 설치된 **메일** 응용 프로그램  

 iOS, Android 및 Outlook 데스크톱 2013 이상용 Outlook 앱은 Exchange Online에서만 지원됩니다.  

 조건부 액세스가 작동하려면 Configuration Manager와 Exchange 간의 **온-프레미스 Exchange 커넥터**가 필요합니다.  

 Exchange 온-프레미스에 대한 조건부 액세스 정책은 Configuration Manager 콘솔에서 구성할 수 있습니다. Exchange Online에 대한 조건부 액세스 정책을 구성할 때는 Configuration Manager 콘솔에서 프로세스를 시작할 수 있습니다. 이 경우 프로세스를 완료할 수 있는 Intune 콘솔이 시작됩니다.  

## <a name="configure-conditional-access"></a>조건부 액세스 구성
### <a name="step-1-evaluate-the-effect-of-the-conditional-access-policy"></a>1단계: 조건부 액세스 정책의 영향 평가  
 **온-프레미스 Exchange 커넥터**를 구성했으면 Configuration Manager의 **조건부 액세스 상태별 장치 목록 보고서**를 사용하여 조건부 액세스 정책을 구성한 후에 Exchange 액세스를 차단할 장치를 확인할 수 있습니다. 이 보고서를 사용하려면 다음 항목도 필요합니다.  

-   Intune 구독  

-   서비스 연결 지점을 구성하고 배포해야 함  

 보고서 매개 변수에서 평가할 Intune 그룹을 선택하고, 필요한 경우 정책을 적용할 장치 플랫폼을 선택합니다.  

 보고서 실행 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 기능](../../core/servers/manage/reporting.md)을 참조하세요.  

 보고서를 실행한 후 다음 네 열을 검토하여 사용자가 차단될지 여부를 결정합니다.  

-   **관리 채널** - 장치가 Intune, Exchange ActiveSync 또는 둘 다에 의해 관리되는지 여부를 나타냅니다.  

-   **AAD에 등록됨** - 장치가 Azure Active Directory에 등록(작업 공간 연결이라고도 함)되었는지 여부를 나타냅니다.  

-   **준수** - 장치가 배포한 모든 준수 정책을 준수하는지 여부를 나타냅니다.  

-   **EAS 활성화됨** - iOS 및 Android 장치의 경우 Exchange ActiveSync ID가 Azure Active Directory의 장치 등록 레코드에 연결되어 있어야 합니다. 사용자가 격리 전자 메일에서 **전자 메일 활성화** 링크를 클릭하면 이러한 연결이 설정됩니다.  

    > [!NOTE]  
    >  Windows Phone 장치는 항상 이 열에 값을 표시합니다.  

 대상 그룹 또는 컬렉션의 일부인 장치의 경우 열 값이 다음 표에 나와 있는 값과 일치하지 않으면 Exchange 액세스가 차단됩니다.  

|관리 채널|등록된 AAD|규정|EAS 활성화됨|결과 작업|  
|------------------------|--------------------|---------------|-------------------|----------------------|  
|**Microsoft Intune 및 Exchange ActiveSync에 의해 관리**|예|예|**예** 또는 **아니요** 가 표시됨|전자 메일 액세스 허용|  
|모든 다른 값|아니요|아니요|값이 표시되지 않음|전자 메일 액세스 차단|  

 보고서의 내용을 내보내고 **전자 메일 주소** 열을 사용하여 사용자에게 액세스 차단을 알릴 수 있습니다.  

### <a name="step-2-configure-user-groups-or-collections-for-the-conditional-access-policy"></a>2단계: 조건부 액세스 정책을 적용할 사용자 그룹 또는 컬렉션 구성  
 정책 유형에 따라 서로 다른 사용자 그룹 또는 컬렉션을 대상으로 조건부 액세스 정책을 구성합니다. 이러한 그룹에는 정책의 대상이 되거나 정책에서 제외되는 사용자가 포함됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 장치가 규정을 준수해야 전자 메일에 액세스할 수 있습니다.  

-   **Exchange Online 정책의 경우** - Azure Active Directory 보안 사용자 그룹을 대상으로 지정합니다. **Office 365 관리 센터**또는 **Intune 계정 포털**에서 이러한 그룹을 구성할 수 있습니다.  

-   **Exchange 온-프레미스 정책의 경우** – Configuration Manager 사용자 컬렉션을 대상으로 지정합니다. **자산 및 준수** 작업 영역에서 이러한 컬렉션을 구성할 수 있습니다.  

 각 정책에 두 그룹 유형을 지정할 수 있습니다.  

-   **대상이 지정된 그룹** - 정책이 적용되는 사용자 그룹 또는 컬렉션  

-   **제외된 그룹** - 정책에서 제외되는 사용자 그룹 또는 컬렉션(선택 사항)  

 사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.  

 조건부 액세스 정책의 대상인 그룹 또는 컬렉션에 대해서만 Exchange 액세스를 평가합니다.  

### <a name="step-3-configure-and-deploy-a-compliance-policy"></a>3단계: 준수 정책 구성 및 배포  
 규정 준수 정책을 만들고 Exchange 조건부 액세스 정책의 대상이 될 모든 장치에 배포해야 합니다.  

 준수 정책을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 장치 규정 준수 정책 관리](device-compliance-policies.md)를 참조하세요.  

> [!IMPORTANT]  
>  규정 준수 정책을 배포하지 않은 상태에서 Exchange 조건부 액세스 정책을 사용하도록 설정하면 대상으로 지정된 모든 장치에 액세스가 허용됩니다.  

 준비가 되었으면 **4단계**를 계속합니다.  

### <a name="step-4-configure-the-conditional-access-policy"></a>4단계: 조건부 액세스 정책 구성  

#### <a name="for-exchange-online-and-tenants-in-the-new-exchange-online-dedicated-environment"></a>Exchange Online(및 새 Exchange Online Dedicated 환경의 테넌트)의 경우

>[!NOTE]
>Azure AD 관리 콘솔에서 조건부 액세스 정책을 만들 수도 있습니다. Azure AD 관리 콘솔을 사용하면 다단계 인증 등의 다른 조건부 액세스 정책 외에도 Intune 장치 조건부 액세스 정책(Azure AD에서는 장치 기반 조건부 액세스 정책이라고 함)을 만들 수 있습니다. Azure AD에서 지원하는 Salesforce, Box 등의 타사 엔터프라이즈 앱에 대한 조건부 액세스 정책을 설정할 수도 있습니다. 자세한 내용은 [Azure Active Directory 연결 응용 프로그램에 대한 액세스 제어를 위해 Azure Active Directory 장치 기반 조건부 액세스 정책을 설정하는 방법](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/)을 참조하세요.

 다음과 같은 흐름을 사용하여 Exchange Online에 대한 조건부 액세스 정책에 의해 장치를 허용할지 또는 차단할지를 평가합니다.  

 ![ConditionalAccess-1](../media/ConditionalAccess8-1.png)  

 전자 메일에 액세스하려면 장치는 다음을 수행해야 합니다.  

-   Intune에 장치 등록  

-   PC가 도메인에 가입되었거나 등록되어 있어야 하며, Intune에 설정된 정책을 준수해야 합니다.  

-   장치를 Azure Active Directory에 등록해야 합니다(이 등록은 Intune에 장치를 등록하면 자동으로 수행됨).  

     도메인에 가입된 PC의 경우 Azure Active Directory에 [장치를 자동으로 등록](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) 하도록 설정해야 합니다.  

-   메일 활성화 - 장치의 Exchange ActiveSync ID를 Azure Active Directory의 장치 레코드와 연결합니다(iOS 및 Android 장치에만 적용됨).  

-   배포된 준수 정책을 준수해야 합니다.  

 장치 상태는 평가 대상 조건에 따라 전자 메일에 대한 액세스를 부여하거나 차단하는 Azure Active Directory에 저장됩니다.  

 조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.  

-   장치를 등록하지 않았거나 Azure Active Directory에 등록한 경우, 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.  

-   장치가 정책을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Intune 웹 포털 또는 회사 포털 앱과 문제를 해결하는 방법을 알려주는 메시지가 표시됩니다.  

-   PC의 경우:  

    -   정책이 도메인 가입을 요구하도록 설정되어 있지만 PC가 도메인에 가입되지 않은 경우 IT 관리자에게 문의하라는 메시지가 표시됩니다.  

    -   정책이 도메인 가입 또는 규정 준수를 요구하도록 설정되어 있는 경우 PC가 요구 사항을 충족하지 않으면 회사 포털 앱을 설치하고 등록하는 방법에 대한 지침이 포함된 메시지가 표시됩니다.  

 이 메시지는 Exchange Online 사용자의 장치 및 새 Exchange Online Dedicated 환경의 테넌트에 대해 표시되며, Exchange 온-프레미스 및 레거시 Exchange Online Dedicated 장치에 대한 사용자 전자 메일 받은 편지함에 배달됩니다.  

> [!NOTE]  
>  Configuration Manager 조건부 액세스 규칙은 Exchange Online 관리 콘솔에 정의된 규칙을 재정의, 허용, 차단 및 격리합니다.  

> [!NOTE]  
>  Intune 콘솔에서 조건부 액세스 정책을 구성해야 합니다. 다음 단계에서는 먼저 Configuration Manager를 통해 Intune 콘솔에 액세스합니다. 메시지가 표시되면 Configuration Manager와 Intune 간의 연결 지점을 설정하는 데 사용된 것과 동일한 자격 증명을 사용하여 로그인합니다.  

##### <a name="to-enable-the-exchange-online-policy"></a>Exchange Online 정책을 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  **호환성 설정**, **조건부 액세스**를 차례로 확장하고 **Exchange Online**을 클릭합니다.  

3.  **홈** 탭의 **링크** 그룹에서 **Intune 콘솔에서 조건부 액세스 정책 구성**을 클릭합니다. Intune 서비스의 전역 관리자와 Configuration Manager를 연결하는 데 사용할 계정의 사용자 이름과 암호를 제공해야 할 수 있습니다.  

     Intune 관리 콘솔이 열립니다.  

4.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **조건부 액세스** > **Exchange Online 정책**을 클릭합니다.  

     ![HybridOnlineSetupIntune](../media/HybridOnlineSetupIntune.png)  

5.  **Exchange Online 정책** 페이지에서 **Exchange Online에 대한 조건적 액세스 정책을 사용**을 선택합니다. 이 확인란을 선택하면 장치가 규정을 준수해야 합니다. 선택하지 않은 경우 조건부 액세스가 적용되지 않습니다.  

    > [!NOTE]  
    >  준수 정책을 배포하지 않은 상태에서 Exchange Online 정책을 사용하도록 설정하면 대상으로 지정된 모든 장치가 규격으로 보고됩니다.  
    >   
    >  준수 상태에 관계없이, 정책의 대상으로 지정된 모든 사용자는 자신의 장치를 Intune에 등록해야 합니다.  

6.  최신 인증을 사용하는 앱 및 Outlook용 **응용 프로그램 액세스**에서 각 플랫폼에 대한 규정을 준수하는 장치에만 액세스를 제한하도록 선택할 수 있습니다.  Windows 장치가 도메인에 가입되어 있거나, Intune에 등록되어 있고 규격을 준수해야 합니다.  

    > [!TIP]  
    >  **최신 인증** 을 사용하는 경우 Office 클라이언트에서 ADAL(Active Directory Authentication Library) 기반 로그인이 가능합니다.  
    >   
    >  -   ADAL 기반 인증을 사용하면 Office 클라이언트가 브라우저 기반 인증(수동 인증이라고도 함)을 수행할 수 있게 됩니다.  사용자는 인증 시 로그인 웹 페이지로 이동됩니다.  
    > -   이 새로운 로그인 방법을 적용하는 경우 **장치 준수** 및 **다단계 인증** 수행 여부에 따라 조건부 액세스 등의 새로운 시나리오를 사용할 수 있습니다.  
    >   
    >  이 [문서](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) 에는 최신 인증의 작동 방식이 자세히 나와 있습니다.  

     Configuration Manager 및 Intune과 함께 Exchange Online을 사용하면 조건부 액세스를 사용하여 모바일 장치를 관리할 수 있을 뿐 아니라 데스크톱 컴퓨터도 관리할 수 있습니다. PC가 도메인에 가입되어 있거나, Intune에 등록되어 있고 규정을 준수해야 합니다. 다음 요구 사항을 설정할 수 있습니다.  

    -   **장치가 도메인에 가입되어 있거나 규정을 준수해야 합니다.** PC가 도메인에 가입되어 있거나 정책을 따라야 합니다. PC가 이러한 요구 사항을 하나라도 충족하지 않을 경우 Intune에 장치를 등록하라는 메시지가 표시됩니다.  

    -   **장치가 도메인에 가입되어 있어야 합니다.** Exchange Online에 액세스하려면 PC가 도메인에 가입되어 있어야 합니다. PC가 도메인에 가입되지 않은 경우 메일 액세스가 차단되고 IT 관리자에게 문의하라는 메시지가 표시됩니다.  

    -   **장치가 규정을 준수해야 합니다.** PC가 Intune에 등록되어 있어야 하며 정책을 준수해야 합니다. PC가 등록되지 않은 경우 등록 방법에 대한 지침이 포함된 메시지가 표시됩니다.  

7.  **OWA(Outlook Web Access)**에서 지원되는 브라우저[예: Safari(iOS) 및 Chrome(Android)]를 통한 Exchange Online 액세스만 허용하도록 선택할 수 있습니다. 다른 브라우저에서의 액세스는 차단됩니다. Outlook에의 응용 프로그램 액세스에 대해 선택한 것과 동일한 플랫폼 제한 사항이 여기에도 적용됩니다.

    **Android** 장치에서는, 사용자가 브라우저 액세스를 사용하도록 설정해야 합니다.  이를 위해서 최종 사용자가 등록된 장치에서 다음과 같이 "브라우저 액세스 사용" 옵션을 사용하도록 설정해야 합니다.
     1. **회사 포털 앱**을 시작합니다.
     2. 세 개의 점(...) 또는 하드웨어 메뉴 단추에서 **설정** 페이지로 이동합니다.
      3.    **브라우저 액세스 사용** 단추를 누릅니다.
      4.    Chrome 브라우저에서, Office 365에서 로그아웃하고 Chrome을 다시 시작합니다.

     **iOS 및 Android** 플랫폼에서, 서비스에 액세스하는 데 사용되는 장치를 식별하기 위해 Azure Active Directory는 TLS(전송 계층 보안) 인증서를 장치에 발급합니다.  아래 스크린샷과 같이 장치에서 최종 사용자에게 인증서를 선택하라는 메시지와 함께 인증서를 표시합니다. 최종 사용자가 이 인증서를 선택해야 브라우저를 계속 사용할 수 있습니다.

     **Android**

     ![iPad에서 인증서 프롬프트에 대한 스크린샷](../media/mdm-browser-ca-ios-cert-prompt_v2.png)

    **OWA(Outlook Web Access)**

    ![Android 장치에서 인증서 프롬프트에 대한 스크린샷](../media/mdm-browser-ca-android-cert-prompt.png)

7.  **Exchange ActiveSync 메일 앱**의 경우 장치가 규격을 준수하지 않으면 메일이 Exchange Online에 액세스할 수 없게 차단하도록 선택하고, Intune에서 장치를 관리할 수 없으면 메일에 대한 액세스를 허용하거나 차단할 것인지 여부를 선택할 수 있습니다.  

8.  **대상 그룹**아래에서 정책을 적용할 사용자의 Active Directory 보안 그룹을 선택합니다.  

    > [!NOTE]  
    >  대상이 지정된 그룹에 포함된 사용자의 경우 Exchange 규칙 및 정책 대신 Intune 정책이 적용됩니다.  
    >   
    >  Exchange는 Exchange 허용, 차단, 격리 규칙만 적용하며 다음과 같은 경우 Exchange 정책이 적용됩니다.  
    >   
    >  -   사용자에게 Intune 사용이 허가되지 않은 경우  
    > -   사용자에게 Intune 사용이 허가되었지만 사용자가 조건부 액세스 정책에서 대상으로 지정된 보안 그룹에 속하지 않는 경우  

9. **제외된 그룹**아래에서 이 정책에서 제외된 사용자의 Active Directory 보안 그룹을 선택합니다. 사용자가 대상 그룹 및 제외된 그룹에 모두 속할 경우 정책에서 제외되며 그룹의 메일에 액세스할 수 있습니다.  

10. 작업을 마쳤으면 **저장**을 클릭합니다.  

-   조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.  

-   사용자가 전자 메일 계정을 만들고 나면 장치가 즉시 차단됩니다.  

-   차단된 사용자가 장치를 Intune에 등록하거나 정책 위반을 수정하면 2분 내에 메일 액세스 차단이 해제됩니다.  

-   사용자가 장치 등록을 취소하면 약 6시간 후에 메일이 차단됩니다.  

### <a name="for-exchange-on-premises-and-tenants-in-the-legacy-exchange-online-dedicated-environment"></a>Exchange 온-프레미스(및 새 Exchange Online Dedicated 환경의 테넌트)의 경우  
 다음 흐름을 사용하여 Exchange 온-프레미스 및 레거시 Exchange Online Dedicated 환경의 테넌트에 대한 조건부 액세스 정책에 의해 장치를 허용할지 또는 차단할지를 평가합니다.  

 ![ConditionalAccess-2](../media/ConditionalAccess8-2.png)  

##### <a name="to-enable-the-exchange-on-premises-policy"></a>Exchange 온-프레미스 정책을 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  **호환성 설정**, **조건부 액세스**를 차례로 확장하고 **온-프레미스 Exchange**를 클릭합니다.  

3.  **홈** 탭의 **온-프레미스 Exchange** 그룹에서 **조건부 액세스 정책 구성**을 클릭합니다.  

4.  **Configuration Manager 버전 1602부터** **조건부 액세스 정책 마법사 구성** 의 **일반**페이지에서, Exchange Active Sync 기본 규칙을 재정의할 것인지 여부를 지정합니다. 기본 규칙이 격리 또는 액세스 차단으로 설정된 경우에도 등록된 규격 장치에서 항상 메일에 액스세할 수 있도록 하려면 이 옵션을 클릭합니다.  

    > [!NOTE]  
    >  Android 장치에 대한 기본 재정의 문제가 있습니다. Exchange 서버의 기본 액세스 규칙이 **차단** 으로 설정되어 있고 Exchange 조건부 액세스 정책이 기본 규칙 재정의 옵션으로 활성화된 경우 장치가 Intune에 등록되고 규정을 준수하더라도 대상 사용자의 Android 장치가 차단 해제되지 않을 수 있습니다.  이 문제를 해결하려면 Exchange 기본 액세스 규칙을 **격리**로 설정합니다. 이 장치는 기본적으로 Exchange에 대한 액세스권한을 얻지 못하며, 관리자가 격리 중인 장치 목록의 Exchange 서버에서 보고서를 가져올 수 있습니다.  

     Exchange 커넥터를 설정할 때 알림 메일 계정을 설정하지 않은 경우 이 페이지에 경고가 표시되며 **다음** 단추가 비활성화됩니다.  계속하려면 먼저 Exchange 커넥터에서 알림 메일 설정을 구성한 후 **조건부 액세스 정책 구성 마법사** 로 돌아가 프로세스를 완료합니다.  

     ![HybridCondAccessWiz1](../media/HybridCondAccessWiz1.PNG)  

     **다음**을 클릭합니다.  

5.  **대상이 지정된 컬렉션** 페이지에서 사용자 컬렉션을 하나 이상 추가합니다. Exchange에 액세스하려면 이러한 컬렉션의 사용자가 장치를 Intune에 등록해야 하며 배포한 준수 정책을 준수해야 합니다.  

     ![HybridCondAccessWiz2](../media/HybridCondAccessWiz2.PNG)  

     **다음**을 클릭합니다.  

6.  **제외 컬렉션** 페이지에서 조건부 액세스 정책에서 제외할 사용자 컬렉션을 추가합니다. 이러한 그룹의 사용자는 Exchange에 액세스하기 위해 장치를 Intune에 등록할 필요가 없으며 배포된 준수 정책을 준수하지 않아도 됩니다.  

     ![HybridCondAccessWiz3](../media/HybridCondAccessWiz3.png)  

     대상으로 지정된 목록과 제외된 목록에 모두 표시되는 사용자는 조건부 액세스 정책에서 제외됩니다.  

     **다음**을 클릭합니다.  

7.  **사용자 알림 편집** 페이지에서 Intune이 Exchange에서 전송하는 메일 외에 장치 차단을 해제하는 방법에 대한 지침을 사용자에게 보내는 메일을 구성합니다.  

     기본 메시지를 편집하고 HTML 태그를 사용하여 텍스트가 나타나는 방법에 대한 서식을 지정할 수 있습니다. 예정된 변경에 대해 알리고 장치 등록에 대한 지침을 제공하는 메일을 미리 직원에게 보낼 수도 있습니다.  

     ![HybridCondAccessWiz4](../media/HybridCondAccessWiz4.PNG)  

    > [!NOTE]  
    >  관리 지침이 포함된 Intune 알림 메일은 사용자의 Exchange 사서함에 배달되므로, 사용자가 메일 메시지를 받기 전에 해당 사용자의 장치가 차단된 경우 차단 해제된 장치 또는 다른 방법을 통해 Exchange에 액세스하여 메시지를 볼 수 있습니다.  

    > [!NOTE]  
    >  Exchange가 알림 전자 메일을 보낼 수 있도록 하려면 알림 전자 메일을 보내는 데 사용할 계정을 구성해야 합니다. Exchange Server 커넥터의 속성을 구성할 때 이 작업을 수행합니다.  
    >   
    >  자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

     **다음**을 클릭합니다.  

8.  **요약** 페이지에서 설정을 검토하고 마법사를 완료합니다.  

-   조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.  

-   사용자가 Exchange ActiveSync 프로필을 설정한 후에 장치가 차단되기까지 1~3시간이 걸릴 수 있습니다(Intune에서 관리되지 않는 경우).  

-   그런 다음 차단된 사용자가 장치를 Intune에 등록하거나 정책 위반을 수정하면 2분 내에 메일 액세스 차단이 해제됩니다.  

-   사용자가 Intune에서 등록을 취소되면 장치가 차단되기까지 1~3시간이 걸릴 수 있습니다.  

### <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager에서 서비스 액세스 관리](../../protect/deploy-use/manage-access-to-services.md)



<!--HONumber=Nov16_HO1-->


