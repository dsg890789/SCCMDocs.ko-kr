---
title: "조건부 액세스 | Microsoft 문서"
description: "System Center Configuration Manager에서 조건부 액세스를 사용하여 메일 및 기타 서비스를 보호하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b04727b-d563-422f-8d59-4dd66215d0b3
caps.latest.revision: 26
author: mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: ea9184cd4fdc87513ed489f0f568efa6d64c1caa
ms.lasthandoff: 03/06/2017


---

# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 서비스 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*


## <a name="conditional-access-in-system-center-configuration-manager"></a>System Center Configuration Manager의 조건부 액세스
**조건부 액세스**를 사용하여 지정한 조건에 따라 Microsoft Intune에 등록된 장치의 메일과 기타 서비스를 보호할 수 있습니다.  

 **System Center Configuration Manager로 관리되며 정책 준수 여부가 평가되는 PC의 조건부 액세스**에 대한 자세한 내용은 [System Center Configuration Manager에서 관리되는 PC용 O365 서비스에 대한 액세스 관리](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)를 참조하세요.  


 조건부 액세스에 대한 일반적인 흐름은 다음과 같을 수 있습니다.  

 ![ConditionalAccess4](media/ConditionalAccess4.png)  

 조건부 액세스를 사용하여 다음 서비스에 대한 액세스를 관리합니다.  

-   Microsoft Exchange 온-프레미스  

-   Microsoft Exchange Online  

-   Exchange Online Dedicated  

-   SharePoint Online  

-   비즈니스용 Skype Online

-   Dynamics CRM Online

 조건부 액세스를 구현하려면 Configuration Manager에서 다음의 두 가지 정책 유형을 구성합니다.  

-   **준수 정책** 은 사용자 컬렉션에 배포하고 다음과 같은 설정을 평가할 수 있는 선택적 정책입니다.  

    -   암호  

    -   암호화  

    -   장치의 무단 해제 또는 루팅 여부  

    -   Configuration Manager 또는 Intune 정책을 통해 장치의 메일을 관리하는지 여부  

     **장치에 준수 정책을 배포하지 않은 경우 적용 가능한 모든 조건부 액세스 정책이 장치를 규격으로 처리합니다**.  

-   **조건부 액세스 정책**은 특정 서비스에 대해 구성되며, 대상 또는 예외로 설정할 Azure Active Directory 보안 사용자 그룹 또는 Configuration Manager 사용자 컬렉션 등의 규칙을 정의합니다.  

     Configuration Manager 콘솔에서 온-프레미스 Exchange 조건부 액세스 정책을 구성합니다. 그러나 Exchange Online 또는 SharePoint Online 정책을 구성할 때는 정책을 구성할 수 있도록 Intune 관리 콘솔이 열립니다.  

     다른 Intune 또는 Configuration Manager 정책과 달리 조건부 액세스 정책은 사용자가 배포하지 않습니다. 대신 이러한 정책은 한 번 구성하면 대상으로 지정된 모든 사용자에게 적용됩니다.  

 구성한 조건을 장치가 충족하지 않는 경우 해당 사용자는 장치를 등록하고 규격에 맞지 않는 문제를 해결하는 과정으로 안내됩니다.  

조건부 액세스를 사용하기 **전에** **요구 사항**이 제대로 충족되었는지 확인합니다.  

## <a name="requirements-for-exchange-online-using-the-shared-multi-tenant-environment"></a>Exchange Online에 대한 요구 사항(공유 다중 테넌트 환경 사용)
Exchange Online에 대한 조건부 액세스에서는 다음을 실행하는 장치를 지원합니다.
-   Windows 8.1 이상(Intune에 등록된 경우)
-   Windows 7.0 또는 Windows 8.1(도메인에 가입된 경우)
-   Windows Phone 8.1 이상
-   iOS 7.1 이상
-   Android 4.0 이상, Samsung KNOX Standard 4.0 이상

 **추가 필수 조건**:
-   장치는 AAD DRS(Azure Active Directory Device Registration Service)에 장치를 등록하는 작업 공간에 연결되어 있어야 합니다.<br />     
- 도메인에 가입된 PC는 그룹 정책 또는 MSI를 통해 Azure Active Directory에 자동으로 등록되어야 합니다.

  PC에 대해 조건부 액세스를 사용하도록 설정하기 위한 모든 요구 사항은 이 항목의 **PC에 대한 조건부 액세스** 에 설명되어 있습니다.<br />     
  Intune 및 Office 365 고객의 경우에는 AAD DRS가 자동으로 활성화됩니다. ADFS 장치 등록 서비스를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 장치가 표시되지 않습니다.
-   Exchange Online(예: E3)을 포함하는 Office 365 구독을 사용해야 하고 사용자는 Exchange Online의 라이선스를 취득해야 합니다.
-   필요한 경우 사용할 수 있는 선택 사항인 **Exchange Server 커넥터**는 Configuration Manager를 Microsoft Exchange Online에 연결하며, Configuration Manager 콘솔을 통해 장치 정보를 모니터링하는 데 사용할 수 있습니다([System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) 참조).
커넥터는 준수 정책 또는 조건부 액세스 정책을 사용하려는 경우 필요가 없지만 조건부 액세스의 영향을 평가하는 보고서를 실행하려는 경우에는 필요합니다.

## <a name="requirements-for-exchange-online-dedicated"></a>Exchange Online Dedicated에 대한 요구 사항
Exchange Online Dedicated에 대한 조건부 액세스는 다음을 실행하는 장치를 지원합니다.
-   Windows 8 이상(Intune에 등록된 경우)
-   Windows 7.0 또는 Windows 8.1(도메인에 가입된 경우)

  도메인에 가입된 PC에 대한 조건부 액세스(새 Exchange Online 전용 환경의 테넌트에만 해당)
-   Windows Phone 8 이상
-   EAS(Exchange ActiveSync) 전자 메일 클라이언트를 사용하는 모든 iOS 장치
-   Android 4 이상
-   **레거시 Exchange Online Dedicated 환경**의 테넌트:    

  Configuration Manager를 Microsoft Exchange 온-프레미스에 연결하는 **Exchange Server 커넥터**를 사용해야 합니다. 그러면 모바일 장치를 관리하고 조건부 액세스를 사용할 수 있습니다([System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) 참조).
-   **새 Exchange Online Dedicated 환경**의 테넌트:     
  선택 사항인 **Exchange Server 커넥터**는 Configuration Manager를 Microsoft Exchange Online에 연결하며, 장치 정보를 관리하는 데 사용할 수 있습니다([System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) 참조). 커넥터는 준수 정책 또는 조건부 액세스 정책을 사용하려는 경우 필요가 없지만 조건부 액세스의 영향을 평가하는 보고서를 실행하려는 경우에는 필요합니다.  

## <a name="requirements-for-exchange-on-premises"></a>Exchange 온-프레미스에 대한 요구 사항
Exchange 온-프레미스에 대한 조건부 액세스는 다음을 지원합니다.
-   Windows 8 이상(Intune에 등록된 경우)
-   Windows Phone 8 이상
-   iOS의 기본 메일 앱
-   Android 4 이상의 기본 메일 앱
-   Microsoft Outlook 앱은 지원되지 않습니다(Android 및 iOS).

**추가 필수 조건**:

-  Exchange 버전은 Exchange 2010 이상이어야 합니다. Exchange Server CAS(클라이언트 액세스 서버) 배열이 지원됩니다.

> [!TIP]
> Exchange 환경이 CAS 서버 구성에 있다면 온-프레미스 Exchange 커넥터가 CAS 서버 중 하나를 가리키도록 구성해야 합니다.
- Configuration Manager를 Microsoft Exchange 온-프레미스에 연결하는 **Exchange Server 커넥터**를 사용해야 합니다. 그러면 모바일 장치를 관리하고 조건부 액세스를 사용할 수 있습니다([System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md) 참조).
  - 최신 버전의 **온-프레미스 Exchange 커넥터**를 사용하고 있는지 확인합니다. 온-프레미스 Exchange 커넥터를 Configuration Manager 콘솔을 통해 구성해야 합니다. 자세한 연습 과정을 보려면 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.
  - System Center Configuration Manager 주 사이트에만 커넥터를 구성해야 합니다.</li><li>이 커넥터는 Exchange CAS 환경을 지원합니다. <br />        커넥터를 구성할 때는 커넥터가 Exchange CAS 서버 중 하나와 통신하도록 설정해야 합니다.

- Exchange ActiveSync는 인증서 기반 인증 또는 사용자 자격 증명 항목으로 구성할 수 있습니다.


## <a name="requirements-for-skype-for-business-online"></a>비즈니스용 Skype Online에 대한 요구 사항
SharePoint Online에 대한 조건부 액세스에서는 다음을 실행하는 장치를 지원합니다.
 -   iOS 7.1 이상
 -   Android 4.0 이상
 -   Samsung KNOX Standard 4.0 이상

**또한** 비즈니스용 Skype Online에 최신 인증을 사용해야 합니다. 최신 인증 프로그램에 등록하려면 [Connect 양식](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) 을 작성하세요.

모든 최종 사용자는 비즈니스용 Skype Online을 사용해야 합니다. 비즈니스용 Skype Online와 온-프레미스 비즈니스용 Skype를 모두 배포한 경우 조건부 액세스 정책이 온-프레미스 배포에 속한 최종 사용자에게는 적용되지 않습니다.

## <a name="requirements-for-sharepoint-online"></a>SharePoint Online에 대한 요구 사항
SharePoint Online에 대한 조건부 액세스에서는 다음을 실행하는 장치를 지원합니다.
 -   Windows 8.1 이상(Intune에 등록된 경우)
 -   Windows 7.0 또는 Windows 8.1(도메인에 가입된 경우)
 -   Windows Phone 8.1 이상
 -   iOS 7.1 이상
 -   Android 4.0 이상, Samsung KNOX Standard 4.0 이상

 **추가 필수 조건**:
 -   장치는 AAD DRS(Azure Active Directory Device Registration Service)에 장치를 등록하는 작업 공간에 연결되어 있어야 합니다.

 도메인에 가입된 PC는 그룹 정책 또는 MSI를 통해 Azure Active Directory에 자동으로 등록되어야 합니다. PC에 대해 조건부 액세스를 사용하도록 설정하기 위한 모든 요구 사항은 이 항목의 **PC에 대한 조건부 액세스** 에 설명되어 있습니다.

 Intune 및 Office 365 고객의 경우에는 AAD DRS가 자동으로 활성화됩니다. ADFS 장치 등록 서비스를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 장치가 표시되지 않습니다.
 -   SharePoint Online 구독이 필요하며 사용자는 SharePoint Online의 라이선스를 취득해야 합니다.

 ### <a name="conditional-access-for-pcs"></a>PC에 대한 조건부 액세스

 다음 요구 사항을 충족하는 PC에 대해 Office 데스크톱 응용 프로그램을 사용하여 **Exchange Online** 및 **SharePoint Online** 에 액세스하는 PC용 조건부 액세스를 설정할 수 있습니다.
 -   PC에서 Windows 7.0 또는 Windows 8.1을 실행해야 합니다.
 -   PC가 도메인에 가입되어 있거나 정책을 준수해야 합니다.

 PC가 정책을 준수하도록 하려면 Intune에서 PC를 등록해야 하며 정책을 준수하도록 설정해야 합니다.

 도메인에 가입된 PC의 경우 Azure Active Directory에 [장치를 자동으로 등록](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) 하도록 설정해야 합니다.
 -   [Office 365 최신 인증을 사용](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)하도록 설정해야 하며 최신 Office 업데이트를 모두 설치해야 합니다.<br />     최신 인증을 사용하는 경우 Office 2013 Windows 클라이언트에 ADAL(Active Directory 인증 라이브러리) 기반 로그인 기능이 제공되며, **다단계 인증**및 **인증서 기반 인증**과 같은 더욱 효율적인 보안 기능을 사용할 수 있습니다.
 -   최신 인증 이외의 인증 프로토콜을 차단하도록 ADFS 클레임 규칙을 설정해야 합니다.  

## <a name="next-steps"></a>다음 단계  
 필요한 시나리오에 대해 준수 정책 및 조건부 액세스 정책을 구성하는 방법을 알아보려면 다음 항목을 읽어보세요.  

-   [System Center Configuration Manager에서 장치 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)  

-   [System Center Configuration Manager에서 메일 액세스 관리](../../protect/deploy-use/manage-email-access.md)  

-   [System Center Configuration Manager에서 SharePoint Online 액세스 관리](../../protect/deploy-use/manage-sharepoint-online-access.md)  

-   [비즈니스용 Skype Online 액세스 관리](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>참고 항목  

 [System Center Configuration Manager에서 준수 설정 시작](../../compliance/get-started/get-started-with-compliance-settings.md)

