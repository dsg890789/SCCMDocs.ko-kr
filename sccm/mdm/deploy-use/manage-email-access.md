---
title: 전자 메일 액세스 관리
titleSuffix: Configuration Manager
description: Configuration Manager 조건부 액세스를 사용 하 여 Exchange 메일에 대 한 액세스를 관리 하는 방법에 알아봅니다.
ms.date: 03/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: fa648e73-5fb8-4818-ab57-7466ffaf888e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ee4ed8f102507b4d62a1ccbfe1cc38240e85df9
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260552"
---
# <a name="manage-email-access-in-configuration-manager"></a>Configuration Manager에서 메일 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

지정한 조건에 따라 Exchange 메일에 대 한 액세스 관리를 사용 하 여 Configuration Manager 조건부 액세스.  

다음 전자 메일 프로그램에 대한 액세스를 관리할 수 있습니다.  

- Microsoft Exchange 온-프레미스  

- Microsoft Exchange Online  

- Exchange Online Dedicated  

기본 제공 전자 메일 클라이언트에서의 Exchange Online 및 Exchange 온-프레미스에 대한 액세스를 다음 플랫폼에서 제어할 수 있습니다.  

- Android 4.0 이상, Samsung KNOX Standard 4.0 이상  

- iOS 9.0 이상  

- Windows Phone 8.1 이상  

- Windows 8.1 이상에 설치된 메일 애플리케이션  

Office 데스크톱 애플리케이션은 다음을 실행하는 Exchange Online에 액세스할 수 있습니다.  

- [최신 인증](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) 이 사용되는 Office 데스크톱 2013 이상  

- Windows 7.0 또는 Windows 8.1  

> [!NOTE]  
> Pc는 도메인에 가입 되도록 하거나 Intune에서 설정 된 정책 준수 해야 합니다.  


## <a name="device-requirements"></a>디바이스 요구 사항
조건부 액세스를 구성하면 사용자는 다음을 수행해야 자신의 전자 메일에 연결할 수 있습니다.  

- Intune에 등록되어 있거나 도메인에 가입된 PC여야 합니다.  

- Azure Active Directory에 디바이스를 등록해야 합니다(이 등록은 Intune을 사용하여 디바이스를 등록할 때 자동으로 이루어짐)(Exchange Online만 해당). 또한 Azure Active Directory를 사용하여 클라이언트 Exchange ID를 등록해야 합니다(Exchange 온-프레미스에 연결하는 Windows 및 Windows Phone 디바이스에는 적용되지 않음).  

    도메인에 가입된 PC의 경우 Azure Active Directory에 자동으로 등록하도록 설정해야 합니다. **Pc에 대 한 조건부 액세스** 섹션을 [서비스에 대 한 액세스를 관리](../../protect/deploy-use/manage-access-to-services.md) 문서에는 전체 Pc에 대 한 조건부 액세스를 사용 하기 위한 요구 사항 집합이 나열 합니다.  

- 디바이스가 해당 디바이스에 배포된 Configuration Manager 준수 정책을 준수해야 합니다.  

    조건부 액세스 조건이 충족 되지 않으면, 사용자 로그인 할 때 다음 메시지 중 하나를 사용 하 여 표시 됩니다.  

- 회사 포털 앱을 설치 하 고 장치를 등록 (Android 및 iOS 장치용)에 연결 하는 전자 메일을 활성화 하는 방법에 대 한 지침을 사용 하 여 메시지가 표시 됩니다 장치를 Intune에 등록 되어 있지 않고, Azure Active Directory에 등록 하지 않은 경우는 Azure Active Directory의 장치 레코드를 사용 하 여 장치의 Exchange ActiveSync ID입니다.  

- 장치가 규정을 준수 하지 않으면, 문제에 대 한 정보 및 해결 방법을 찾을 수 있는 Intune 웹 포털에 사용자가 알려주는 메시지가 표시 됩니다.  

#### <a name="for-mobile-devices"></a>모바일 장치에 대 한

**iOS** 및 **Android** 디바이스의 브라우저에서 액세스될 경우 Exchange Online에서 **OWA(Outlook Web Access)** 에 대한 액세스를 제한할 수 있습니다. 호환 디바이스의 지원되는 브라우저에서만 액세스할 수 있습니다.  

- Safari(iOS)  
- Chrome(Android)  
- 관리되는 브라우저(iOS 및 Android)  

지원되지 않는 브라우저는 차단됩니다. IOS 및 Android 용 OWA 앱은 지원 되지 않습니다. 이러한 브라우저는 ADFS 클레임 규칙을 통해 차단해야 합니다.  

- 최신 인증 이외의 인증 프로토콜을 차단하도록 ADFS 클레임 규칙을 설정해야 합니다. 자세한 지침은 시나리오 3에에서 나와 [브라우저 기반 응용 프로그램을 제외한 Office 365에 대 한 모든 액세스를 차단](https://technet.microsoft.com/library/dn592182.aspx)합니다.  

#### <a name="for-pcs"></a>Pc에 대 한

- 조건부 액세스 정책 요구 사항이 **도메인에 가입** 또는 **규정**을 허용하는 경우 디바이스를 등록하는 방법에 대한 지침이 포함된 메시지가 표시됩니다. PC가 요구 사항을 하나라도 충족하지 않을 경우 디바이스를 Intune에 등록하라는 메시지가 표시됩니다.  

- 조건부 액세스 정책 요구 사항이 도메인에 가입된 Windows 디바이스만 허용하도록 설정된 경우 해당 디바이스가 차단되고 IT 관리자에게 문의하라는 메시지가 표시됩니다.  

다음 플랫폼의 디바이스 기본 제공 Exchange ActiveSync 전자 메일 클라이언트에서 Exchange 전자 메일에 대 한 액세스를 차단할 수 있습니다.  

- Android 4.0 이상, Samsung KNOX Standard 4.0 이상  

- iOS 9.0 이상  

- Windows Phone 8.1 이상  

- Windows 8.1 이상에 설치된 **메일** 애플리케이션  

iOS, Android 및 Outlook 데스크톱 2013 이상용 Outlook 앱은 Exchange Online에서만 지원됩니다.  

조건부 액세스가 작동하려면 Configuration Manager와 Exchange 간의 **온-프레미스 Exchange 커넥터**가 필요합니다.  

Exchange 온-프레미스에 대한 조건부 액세스 정책은 Configuration Manager 콘솔에서 구성할 수 있습니다. Exchange Online에 대한 조건부 액세스 정책을 구성할 때는 Configuration Manager 콘솔에서 프로세스를 시작할 수 있습니다. 이 경우 프로세스를 완료할 수 있는 Intune 콘솔이 시작됩니다.  



## <a name="configure-conditional-access"></a>조건부 액세스 구성

### <a name="step-1-evaluate-the-effect-of-the-conditional-access-policy"></a>1단계: 조건부 액세스 정책의 영향 평가  

구성한 후 합니다 **온-프레미스 Exchange connector**, Configuration Manager를 사용할 수 있습니다 **조건부 액세스 상태별 장치 목록** 에서 차단할 장치를 식별 하는 보고서 조건부 액세스 정책을 구성한 후 Exchange에 액세스 합니다. 이 보고서를 사용하려면 다음 항목도 필요합니다.  

- Intune 구독  

- 서비스 연결 지점을 구성하고 배포해야 함  

보고서 매개 변수에서 평가할 Intune 그룹을 선택하고, 필요한 경우 정책을 적용할 디바이스 플랫폼을 선택합니다.  

보고서 실행 방법에 대한 자세한 내용은 [Reporting in Configuration Manager](/sccm/core/servers/manage/reporting)를 참조하세요.  

보고서를 실행한 후 다음 네 열을 검토하여 사용자가 차단될지 여부를 결정합니다.  

- **관리 채널**: 장치가는 Intune, Exchange ActiveSync 또는 둘 다에 의해 관리 됩니다.  

- **AAD에 등록**: Azure Active Directory (작업 공간 연결 이라고 함)를 사용 하 여 장치 등록 됩니다.  

- **규격**: 장치가 배포한 모든 준수 정책을 준수 합니다.  

- **EAS 활성화 됨**: iOS 및 Android 장치에서 Azure Active Directory 장치 등록 레코드와 연결 된 Exchange ActiveSync ID가 있어야 하는 데 필요한 됩니다. 사용자가 격리 전자 메일에서 **전자 메일 활성화** 링크를 클릭하면 이러한 연결이 설정됩니다.  

    > [!NOTE]  
    > Windows Phone 디바이스는 항상 이 열에 값을 표시합니다.  

대상 그룹 또는 컬렉션의 일부인 디바이스의 경우 열 값이 다음 표에 나와 있는 값과 일치하지 않으면 Exchange 액세스가 차단됩니다.  

|관리 채널|등록된 AAD|규정|EAS 활성화됨|결과 작업|  
|------------------------|--------------------|---------------|-------------------|----------------------|  
|**Microsoft Intune 및 Exchange ActiveSync에 의해 관리**|예|예|**예** 또는 **아니요** 가 표시됨|전자 메일 액세스 허용|  
|모든 다른 값|아니요|아니요|값이 표시되지 않음|전자 메일 액세스 차단|  

보고서의 내용을 내보내고 **전자 메일 주소** 열을 사용하여 사용자에게 액세스 차단을 알릴 수 있습니다.  


### <a name="step-2-configure-user-groups-or-collections-for-the-conditional-access-policy"></a>2단계: 사용자 그룹 또는 조건부 액세스 정책 컬렉션 구성  

정책 유형에 따라 서로 다른 사용자 그룹 또는 컬렉션을 대상으로 조건부 액세스 정책을 구성합니다. 이러한 그룹에는 정책의 대상이 되거나 정책에서 제외되는 사용자가 포함됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 디바이스가 규정을 준수해야 전자 메일에 액세스할 수 있습니다.  

- **Exchange Online 정책의**: Azure Active Directory 보안 사용자 그룹입니다. 이러한 그룹을 구성할 수 있습니다 합니다 **Microsoft 365 관리 센터**, 또는 **Intune 계정 포털**합니다.  

- **Exchange 온-프레미스 정책의 경우**: Configuration Manager 사용자 컬렉션에 있습니다. **자산 및 준수** 작업 영역에서 이러한 컬렉션을 구성할 수 있습니다.  

각 정책에 두 그룹 유형을 지정할 수 있습니다.  

- **대상 그룹**: 정책이 적용 되는 사용자 그룹 또는 컬렉션  

- **제외 된 그룹**: (선택 사항) 정책에서 제외 되는 사용자 그룹 또는 컬렉션  

사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.  

조건부 액세스 정책의 대상인 그룹 또는 컬렉션에 대해서만 Exchange 액세스를 평가합니다.  


### <a name="step-3-configure-and-deploy-a-compliance-policy"></a>3단계: 준수 정책 구성 및 배포  

규정 준수 정책을 만들고 Exchange 조건부 액세스 정책의 대상이 될 모든 디바이스에 배포해야 합니다.  

준수 정책을 구성하는 방법에 대한 자세한 내용은 [디바이스 규정 준수 정책 관리](device-compliance-policies.md)를 참조하세요.  

> [!IMPORTANT]  
> 준수 정책을 배포 하지 않은 하 고 다음에서 Exchange 조건부 액세스 정책을 사용 하도록 설정 하는 경우 모든 대상된 장치는 액세스할을 수 있습니다.  


### <a name="step-4-configure-the-conditional-access-policy"></a>4단계: 조건부 액세스 정책 구성  

#### <a name="for-exchange-online-and-tenants-in-the-new-exchange-online-dedicated-environment"></a>Exchange Online(및 새 Exchange Online Dedicated 환경의 테넌트)의 경우

> [!NOTE]  
> Azure AD 관리 콘솔에서 조건부 액세스 정책을 만들 수도 있습니다. Azure AD 관리 콘솔을 사용하면 다단계 인증 등의 다른 조건부 액세스 정책 외에도 Intune 디바이스 조건부 액세스 정책(Azure AD에서는 디바이스 기반 조건부 액세스 정책이라고 함)을 만들 수 있습니다. Azure AD에서 지원하는 Salesforce, Box 등의 타사 엔터프라이즈 앱에 대한 조건부 액세스 정책을 설정할 수도 있습니다. 자세한 내용은 참조 하세요. [방법: Require managed devices for cloud app access with conditional access](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)(방법: 조건부 액세스를 사용한 클라우드 앱 액세스를 위해 관리형 디바이스 필요)를 참조하세요.  

다음과 같은 흐름을 사용하여 Exchange Online에 대한 조건부 액세스 정책에 의해 디바이스를 허용할지 또는 차단할지를 평가합니다.  

![조건부 액세스 흐름](media/ConditionalAccess8-1.png)  

전자 메일에 액세스하려면 디바이스는 다음을 수행해야 합니다.  

- Intune에 장치 등록  

- Pc는 도메인 가입 되도록 하거나 Intune에 설정 된 정책을 사용 하 여 등록 및 규격 수  

- Azure AD에 장치를 등록 합니다. 이런 자동으로 Intune을 사용 하 여 장치를 등록 하면 됩니다. 도메인에 가입 된 Pc를 설정 해야 최대 [자동으로 장치를 등록](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-manual-steps) Azure AD를 사용 하 여 합니다.  

- 메일 활성화 - 디바이스의 Exchange ActiveSync ID를 Azure Active Directory의 디바이스 레코드와 연결합니다(iOS 및 Android 디바이스에만 적용됨).  

- 배포된 준수 정책을 준수해야 합니다.  

디바이스 상태는 평가 대상 조건에 따라 전자 메일에 대한 액세스를 부여하거나 차단하는 Azure Active Directory에 저장됩니다.  

조건이 충족 되지 않으면, 사용자 로그인 할 때 다음 메시지 중 하나를 사용 하 여 표시 됩니다.  

- 회사 포털 앱을 설치 하 고 등록 하는 방법에 대 한 지침을 사용 하 여 메시지가 표시 됩니다 장치가 등록 되지 않습니다 또는 Azure AD에 등록 하는 경우  

- 장치가 규정을 준수 하지 않으면, 문제에 대 한 정보 및 해결 방법을 찾을 수 있는 Intune 회사 포털 웹 사이트 또는 회사 포털 앱을 사용자에 게 알려 주는 메시지가 표시 됩니다.  

- PC의 경우:  

    - 정책이 도메인 가입을 요구 하도록 설정 되어 도메인에 가입 된 PC 없는 경우 IT 관리자에 게 문의 하 라는 메시지가 표시 됩니다.  

    - 정책이 도메인 가입을 요구 하도록 설정 된 경우 또는 규정 준수를 PC가 요구 사항을 충족 하지 않습니다, 회사 포털 앱을 설치 하 고 등록 하는 방법에 대 한 지침을 사용 하 여 메시지가 표시 됩니다.  

이 메시지는 Exchange Online 사용자의 디바이스 및 새 Exchange Online Dedicated 환경의 테넌트에 대해 표시되며, Exchange 온-프레미스 및 레거시 Exchange Online Dedicated 디바이스에 대한 사용자 전자 메일 받은 편지함에 배달됩니다.  

> [!NOTE]  
> Configuration Manager 조건부 액세스 규칙은 Exchange Online 관리 콘솔에 정의된 규칙을 재정의, 허용, 차단 및 격리합니다.  
> 
> Intune 콘솔에서 조건부 액세스 정책을 구성해야 합니다. 다음 단계에서는 먼저 Configuration Manager를 통해 Intune 콘솔에 액세스합니다. 메시지가 표시 되 면 Configuration Manager와 Intune 간의 서비스 연결 지점을 설정 하는 데 사용한 동일한 자격 증명을 사용 하 여 로그인 합니다.  

##### <a name="to-enable-the-exchange-online-policy"></a>Exchange Online 정책을 사용하도록 설정하려면  

1. Configuration Manager 콘솔에서 선택 **자산 및 준수**합니다.  

2. 확장 **준수 설정**를 확장 하 고 **조건부 액세스**를 선택한 후 **Exchange Online**.  

3. 에 **홈** 탭의 **링크** 그룹을 선택 **Intune 콘솔에서 조건부 액세스 정책 구성**합니다. Intune 서비스의 전역 관리자와 Configuration Manager를 연결하는 데 사용할 계정의 사용자 이름과 암호를 제공해야 할 수 있습니다. Intune 관리 콘솔이 열립니다.  

4. Microsoft Intune 포털에서 선택 **정책** > **조건부 액세스** > **Exchange Online 정책**합니다.  

    ![HybridOnlineSetupIntune](media/HybridOnlineSetupIntune.png)  

5. **Exchange Online 정책** 페이지에서 **Exchange Online에 대한 조건적 액세스 정책을 사용**을 선택합니다. 이 확인란을 선택하면 디바이스가 규정을 준수해야 합니다. 선택 하지 않은 경우이 조건부 액세스 적용 되지 않습니다.  

    > [!NOTE]  
    > 준수 정책을 배포 하지 않은 상태에서 Exchange Online 정책을 사용 하도록 설정 하는 경우 모든 대상된 장치를 규격으로 보고 됩니다.  
   >   
   >  준수 상태에 관계없이, 정책의 대상으로 지정된 모든 사용자는 자신의 디바이스를 Intune에 등록해야 합니다.  

6. 아래 **응용 프로그램 액세스**, Outlook 및 다른 최신 인증을 사용 하 여 앱에는 각 플랫폼에 대 한 준수 하는 장치에만 액세스를 제한 하도록 선택할 수 있습니다. Windows 디바이스가 도메인에 가입되어 있거나, Intune에 등록되어 있고 규격을 준수해야 합니다.  

    > [!TIP]  
    > **최신 인증** 을 사용하는 경우 Office 클라이언트에서 ADAL(Active Directory Authentication Library) 기반 로그인이 가능합니다.  
    > 
    > - ADAL 기반 인증을 사용하면 Office 클라이언트가 브라우저 기반 인증(수동 인증이라고도 함)을 수행할 수 있게 됩니다. 사용자는 인증 시 로그인 웹 페이지로 이동됩니다.  
    > - 이 새로운 로그인 방법을 적용하는 경우 **디바이스 준수** 및 **다단계 인증** 수행 여부에 따라 조건부 액세스 등의 새로운 시나리오를 사용할 수 있습니다.  
    > 
    >  자세한 내용은 [Office 2013및 Office 2016 클라이언트 앱의 최신 인증 작동 방식](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016)을 참조하세요.  

    Configuration Manager 및 Intune과 함께 Exchange Online을 사용하면 조건부 액세스를 사용하여 모바일 디바이스를 관리할 수 있을 뿐 아니라 데스크톱 컴퓨터도 관리할 수 있습니다. Pc는 도메인 가입 되도록 하거나 Intune에 등록 하 고 규정을 준수 해야 합니다. 다음 요구 사항을 설정할 수 있습니다.  

    - **디바이스가 도메인에 가입되어 있거나 규정을 준수해야 합니다.** Pc는 도메인에 가입 되어 있거나 정책을 준수 해야 합니다. PC 이러한 요구 사항을 하나라도 충족 하지 않습니다, 경우 Intune 사용 하 여 장치를 등록 하는 메시지가 표시 됩니다.  

    - **디바이스가 도메인에 가입되어 있어야 합니다.** Pc에는 Exchange Online에 액세스 하려면 도메인에 가입 되어 있어야 합니다. 전자 메일에는 액세스가 차단 되 고 사용자는 IT 관리자에 게 문의 하 라는 메시지가 표시 되는 PC가 도메인에 가입 되지 않은, 경우  

    - **디바이스가 규정을 준수해야 합니다.** PC가 Intune에 등록되어 있어야 하며 정책을 준수해야 합니다. PC가 등록 되지 않은 경우 등록 하는 방법에 대 한 지침을 사용 하 여 메시지가 표시 됩니다.  

7. 아래 **Outlook web access (OWA)**, 지원 되는 브라우저를 통해서만 Exchange Online에 대 한 액세스를 허용 하도록 선택할 수 있습니다. Safari (iOS) 및 Chrome (Android). 다른 브라우저에서의 액세스는 차단됩니다. Outlook에의 애플리케이션 액세스에 대해 선택한 것과 동일한 플랫폼 제한 사항이 여기에도 적용됩니다.  

    - **Android** 디바이스에서는, 사용자가 브라우저 액세스를 사용하도록 설정해야 합니다. 이 작업을 위해 사용자에서 등록된 된 장치에서 "브라우저 액세스 사용" 옵션을 다음과 같이 설정 해야 합니다.  

        1. **회사 포털 앱**을 시작합니다.  

        2. 세 개의 점(...) 또는 하드웨어 메뉴 단추에서 **설정** 페이지로 이동합니다.  

        3. **브라우저 액세스 사용** 단추를 누릅니다.  

        4. Chrome 브라우저에서, Office 365에서 로그아웃하고 Chrome을 다시 시작합니다.  

    - 온 **iOS 및 Android** 플랫폼에서 Azure AD 서비스에 액세스 하는 데 사용 되는 장치를 식별 하는 장치에 TLS 인증서를 발급 합니다. 아래 스크린샷에서 같이 인증서를 사용자에 게 프롬프트를 사용 하 여 인증서를 표시 하는 장치입니다. 사용자는 브라우저를 사용 하는 동안 계속 수행할 수 있습니다이 인증서를 선택 해야 합니다.  

        - **Android**  

        ![iPad에서 인증서 프롬프트에 대한 스크린샷](media/mdm-browser-ca-ios-cert-prompt_v2.png)  

        - **OWA(Outlook Web Access)**  

        ![Android 디바이스에서 인증서 프롬프트에 대한 스크린샷](media/mdm-browser-ca-android-cert-prompt.png)  

8. **Exchange ActiveSync 메일 앱**의 경우 디바이스가 규격을 준수하지 않으면 메일이 Exchange Online에 액세스할 수 없게 차단하도록 선택하고, Intune에서 디바이스를 관리할 수 없으면 메일에 대한 액세스를 허용하거나 차단할 것인지 여부를 선택할 수 있습니다.  

9. **대상 그룹**아래에서 정책을 적용할 사용자의 Active Directory 보안 그룹을 선택합니다.  

    > [!NOTE]  
    > 대상된 그룹에 있는 사용자에 대 한 Intune 정책이 적용 됩니다 Exchange 규칙 및 정책 대신 합니다.  
    > 
    > Exchange는 Exchange 허용, 차단, 격리 규칙만 적용하며 다음과 같은 경우 Exchange 정책이 적용됩니다.  
    > 
    > - 사용자에게 Intune 사용이 허가되지 않은 경우  
    > - 사용자가 Intune에 대 한 허가 하지만 사용자는 조건부 액세스 정책의 대상인 모든 보안 그룹에 속하지 않습니다.  

10. **제외된 그룹**아래에서 이 정책에서 제외된 사용자의 Active Directory 보안 그룹을 선택합니다. 대상 그룹과 제외 된 그룹의 사용자 인 경우 정책에서 제외 됩니다 하며 전자 메일에 액세스할 수 있습니다.  

11. 작업을 마쳤으면 **저장**을 클릭합니다.  


이 정책에 대 한 다음 정보를 검토 합니다.  

- 조건부 액세스 정책에 배포할 필요가 없습니다. 즉시 적용이 됩니다.  

- 사용자가 전자 메일 계정을 만들고 나면 디바이스가 즉시 차단됩니다.  

- 차단된 사용자가 디바이스를 Intune에 등록하거나 정책 위반을 수정하면 2분 내에 메일 액세스 차단이 해제됩니다.  

- 사용자가 디바이스 등록을 취소하면 약 6시간 후에 메일이 차단됩니다.  


### <a name="for-exchange-on-premises-and-tenants-in-the-legacy-exchange-online-dedicated-environment"></a>Exchange 온-프레미스(및 새 Exchange Online Dedicated 환경의 테넌트)의 경우  
다음 흐름을 사용하여 Exchange 온-프레미스 및 레거시 Exchange Online Dedicated 환경의 테넌트에 대한 조건부 액세스 정책에 의해 디바이스를 허용할지 또는 차단할지를 평가합니다.  

![ConditionalAccess-2](media/ConditionalAccess8-2.png)  

#### <a name="to-enable-the-exchange-on-premises-policy"></a>Exchange 온-프레미스 정책을 사용하도록 설정하려면  

1. Configuration Manager 콘솔에서 선택 **자산 및 준수**합니다.  

2. 확장 **준수 설정**를 확장 하 고 **조건부 액세스**를 선택한 후 **온-프레미스 Exchange**.  

3. 에 **홈** 탭의 **온-프레미스 Exchange** 그룹을 선택 **조건부 액세스 정책 구성**합니다.  

4. 에 **일반** 페이지의 **조건부 액세스 정책 마법사 구성**, Exchange Active Sync 기본 규칙을 재정의할 것인지 여부를 지정 합니다. 등록 및 규격 장치를 항상 메일에 액세스할 수, 기본 규칙이 격리 또는 차단으로 설정 된 경우에 액세스 하는 경우이 옵션을 선택 합니다.  

    > [!NOTE]  
    > Android 장치에 대 한 기본 재정의 문제가 있습니다. Exchange 서버의 기본 액세스 규칙이 **차단** 으로 설정되어 있고 Exchange 조건부 액세스 정책이 기본 규칙 재정의 옵션으로 활성화된 경우 디바이스가 Intune에 등록되고 규정을 준수하더라도 대상 사용자의 Android 디바이스가 차단 해제되지 않을 수 있습니다. 이 문제를 해결하려면 Exchange 기본 액세스 규칙을 **격리**로 설정합니다. 장치는 기본적으로 Exchange에 대 한 액세스를 수신 하지 않습니다 하 고 관리자가 격리 중인 장치 목록에서 Exchange 서버에서 보고서를 가져올 수 있습니다.  

    이 페이지에서는 경고가 표시 됩니다 하지 않은 경우 설치 알림 메일 계정을 Exchange connector를 설정할 때, 및 **다음** 단추가 비활성화 됩니다.  계속하려면 먼저 Exchange 커넥터에서 알림 메일 설정을 구성한 후 **조건부 액세스 정책 구성 마법사** 로 돌아가 프로세스를 완료합니다.  

     ![HybridCondAccessWiz1](media/HybridCondAccessWiz1.PNG)  

5. **대상이 지정된 컬렉션** 페이지에서 사용자 컬렉션을 하나 이상 추가합니다. Exchange에 액세스하려면 이러한 컬렉션의 사용자가 디바이스를 Intune에 등록해야 하며 배포한 준수 정책을 준수해야 합니다.  

     ![HybridCondAccessWiz2](media/HybridCondAccessWiz2.PNG)  

6. **제외 컬렉션** 페이지에서 조건부 액세스 정책에서 제외할 사용자 컬렉션을 추가합니다. 이러한 그룹의 사용자 필요 없는 및 Intune 사용 하 여 장치를 등록 하려면 않아도 Exchange에 액세스 하기 위해 배포 된 준수 정책을 준수 해야 됩니다.  

     ![HybridCondAccessWiz3](media/HybridCondAccessWiz3.png)  

    대상으로 지정된 목록과 제외된 목록에 모두 표시되는 사용자는 조건부 액세스 정책에서 제외됩니다.  

7. **사용자 알림 편집** 페이지에서 Intune이 Exchange에서 전송하는 메일 외에 디바이스 차단을 해제하는 방법에 대한 지침을 사용자에게 보내는 메일을 구성합니다.  

    기본 메시지를 편집하고 HTML 태그를 사용하여 텍스트가 나타나는 방법에 대한 서식을 지정할 수 있습니다. 예정된 변경에 대해 알리고 디바이스 등록에 대한 지침을 제공하는 메일을 미리 직원에게 보낼 수도 있습니다.  

     ![HybridCondAccessWiz4](media/HybridCondAccessWiz4.PNG)  

    > [!NOTE]  
    > 관리 지침이 포함된 Intune 알림 메일은 사용자의 Exchange 사서함에 배달되므로, 사용자가 메일 메시지를 받기 전에 해당 사용자의 디바이스가 차단된 경우 차단 해제된 디바이스 또는 다른 방법을 통해 Exchange에 액세스하여 메시지를 볼 수 있습니다.  
    > 
    > 알림 전자 메일을 보낼 교환에 대 한 알림 메일을 보내는 데 사용할 계정을 구성 합니다. Exchange Server 커넥터의 속성을 구성할 때 이 작업을 수행합니다.  
    >   
    > 자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  

8. 에 **요약** 페이지에서 설정을 검토 하 고 다음 마법사를 완료 합니다.  


이 정책에 대 한 다음 정보를 검토 합니다.  

- 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.  

- 사용자가 Exchange ActiveSync 프로필을 설정한 후 (Intune에서 관리 되지 않는) 하는 경우 차단 된 장치에 대 한 1 ~ 3 시간이 걸릴 수 있습니다.  

- 차단 된 사용자 다음 Intune 사용 하 여 장치를 등록 (또는 미준수) 하는 경우 전자 메일 액세스 차단이 해제 됩니다 2 분 이내입니다.  

- 경우는 사용자 취소-차단 장치에 대 한 1 ~ 3 시간이 걸릴 수 있습니다 하는 Intune에서 등록 합니다.  


## <a name="see-also"></a>참고 항목  

[서비스에 대한 액세스 관리](/sccm/protect/deploy-use/manage-access-to-services)
