---
title: 조건부 액세스
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 조건부 액세스를 사용하여 메일 및 기타 서비스를 보호하는 방법을 알아봅니다.
ms.date: 03/18/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b04727b-d563-422f-8d59-4dd66215d0b3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: da2c809c4aaf95de450570814a5b967ca563a2c2
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "68340286"
---
# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 서비스 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

조건부 액세스를 사용하여 Microsoft Intune에 등록된 디바이스의 메일과 기타 서비스를 보호할 수 있는 조건을 지정합니다.  

> [!Important]  
> 온-프레미스 조건부 액세스를 포함 하는 하이브리드 MDM은 [더 이상 사용 되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)입니다. 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  
> 
> Configuration Manager 클라이언트를 사용 하 여 관리 되는 장치에서 조건부 액세스를 사용 하는 경우 보호 되 고 있는지 확인 하려면 마이그레이션하기 전에 먼저 Intune에서 해당 장치에 대 한 조건부 액세스를 사용 하도록 설정 합니다. Configuration Manager에서 공동 관리를 사용 하도록 설정 하 고, 준수 정책 워크 로드를 Intune으로 이동한 후 intune 하이브리드에서 Intune 독립 실행형으로의 마이그레이션을 완료 합니다. 자세한 내용은 [공동 관리를 사용 하는 조건부 액세스](https://docs.microsoft.com/sccm/comanage/quickstart-conditional-access)를 참조 하세요. 


 Configuration Manager 클라이언트를 사용 하 여 관리 되는 장치의 조건부 액세스에 대 한 자세한 내용은 [System Center Configuration Manager에서 관리 하는 pc 용 Office 365 서비스에 대 한 액세스 관리](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)를 참조 하세요.  


 조건부 액세스에 대한 일반적인 흐름은 다음과 같을 수 있습니다.  

 ![ConditionalAccess4](media/ConditionalAccess4.png)  

 조건부 액세스를 사용하여 다음 서비스에 대한 액세스를 관리합니다.  

- Microsoft Exchange 온-프레미스  

- Microsoft Exchange Online  

- Exchange Online Dedicated  

- SharePoint Online  

- 비즈니스용 Skype Online

- Dynamics CRM Online

  조건부 액세스를 구현하려면 Configuration Manager에서 다음의 두 가지 정책 유형을 구성합니다.  

- **준수 정책** 은 사용자 컬렉션에 배포하고 다음과 같은 설정을 평가할 수 있는 선택적 정책입니다.  

  - 암호  

  - 암호화  

  - 디바이스의 무단 해제 또는 루팅 여부  

  - Configuration Manager 또는 Microsoft Intune 정책을 통해 디바이스의 메일을 관리하는지 여부  

    디바이스에 준수 정책을 배포하지 않는 경우 해당 디바이스는 적용 가능한 조건부 액세스 정책에 대한 준수 여부를 보고합니다.

- **조건부 액세스 정책**은 특정 서비스에 따라 다릅니다. 이러한 정책은 대상으로 하거나 제외할 Azure Active Directory 보안 사용자 그룹 또는 Configuration Manager 사용자 컬렉션을 등의 규칙을 정의합니다.  

   Configuration Manager 콘솔에서 온-프레미스 Exchange 조건부 액세스 정책을 구성합니다. 그러나 Exchange Online 또는 SharePoint Online 정책을 구성할 때 정책을 구성할 수 있도록 Microsoft Intune 콘솔이 열립니다.  

   다른 Microsoft Intune 또는 Configuration Manager 정책과 달리 조건부 액세스 정책은 사용자가 배포하지 않습니다. 대신 이러한 정책은 한 번 구성하면 대상으로 지정된 모든 사용자에게 적용됩니다.  

  디바이스가 구성된 조건을 충족하지 않는 경우 사용자에게 디바이스를 등록하고 디바이스 준수 문제를 해결하는 방법을 설명합니다.  

조건부 액세스를 사용하기 전에 요구 사항을 올바로 갖추었는지 확인합니다.  

## <a name="requirements-for-exchange-online-using-the-shared-multi-tenant-environment"></a>Exchange Online에 대한 요구 사항(공유 다중 테넌트 환경 사용)
Exchange Online에 대한 조건부 액세스에서는 다음을 실행하는 디바이스를 지원합니다.
- Windows 8.1 이상(Intune에 등록된 경우)
- Windows 7.0 또는 Windows 8.1(도메인에 가입된 경우)
- Windows Phone 8.1 이상
- iOS 7.1 이상
- Android 4.0 이상, Samsung KNOX Standard 4.0 이상

  **추가 필수 조건**:
- 디바이스는 AAD DRS(Azure Active Directory Device Registration Service)에 디바이스를 등록하는 작업 공간에 연결되어 있어야 합니다.<br />     
- 도메인에 가입된 PC는 그룹 정책 또는 MSI를 통해 Azure Active Directory에 자동으로 등록되어야 합니다.

  PC에 대해 조건부 액세스를 사용하도록 설정하기 위한 모든 요구 사항은 이 문서의 **PC에 대한 조건부 액세스** 섹션에 설명되어 있습니다.<br />     
  Microsoft Intune 및 Office 365 고객의 경우 AAD DRS가 자동으로 활성화됩니다. ADFS 디바이스 등록 서비스를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 디바이스가 표시되지 않습니다.
- E3 등의 Exchange Online을 포함하는 Office 365 구독을 사용합니다. 사용자에게 Exchange Online 라이선스가 있어야 합니다.
- Exchange Server 커넥터는 선택 사항이며 Configuration Manager를 Microsoft Exchange Online에 연결합니다. 이 커넥터를 사용하면 Configuration Manager 콘솔을 통해 디바이스 정보를 모니터링할 수 있습니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.
  커넥터가 준수 정책 또는 조건부 액세스 정책을 사용하지 않아도 됩니다. 조건부 액세스의 영향 보고서를 실행하려면 커넥터가 필요합니다.

## <a name="requirements-for-exchange-online-dedicated"></a>Exchange Online Dedicated에 대한 요구 사항
Exchange Online Dedicated에 대한 조건부 액세스는 다음을 실행하는 디바이스를 지원합니다.
- Windows 8 이상(Intune에 등록된 경우)
- Windows 7.0 또는 Windows 8.1(도메인에 가입된 경우)

  도메인에 가입된 PC에 대한 조건부 액세스(새 Exchange Online 전용 환경의 테넌트에만 해당)
- Windows Phone 8 이상
- EAS(Exchange ActiveSync) 전자 메일 클라이언트를 사용하는 모든 iOS 디바이스
- Android 4 이상
- 레거시 Exchange Online Dedicated 환경의 테넌트:    

  Configuration Manager를 Microsoft Exchange 온-프레미스에 연결하는 Exchange Server 커넥터를 사용합니다. 커넥터를 통해 모바일 디바이스를 관리하고 조건부 액세스를 사용하도록 설정할 수 있습니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.
- 새 Exchange Online Dedicated 환경의 테넌트:     
  Exchange Server 커넥터는 선택 사항이며 Configuration Manager를 Microsoft Exchange Online에 연결하고 디바이스 정보를 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요. 커넥터가 준수 정책 또는 조건부 액세스 정책을 사용하지 않아도 됩니다. 조건부 액세스의 영향 보고서를 실행하려면 커넥터가 필요합니다.  

## <a name="requirements-for-exchange-on-premises"></a>Exchange 온-프레미스에 대한 요구 사항
Exchange 온-프레미스에 대한 조건부 액세스는 다음을 지원합니다.
- Windows 8 이상(Intune에 등록된 경우)
- Windows Phone 8 이상
- iOS의 기본 메일 앱
- Android 4 이상의 기본 메일 앱
- Microsoft Outlook 앱은 지원되지 않습니다(Android 및 iOS).

**추가 필수 조건**:

- Exchange 버전은 Exchange 2010 이상이어야 합니다.
- Exchange Server CAS(클라이언트 액세스 서버) 배열이 지원됩니다.

> [!TIP]
> Exchange 환경이 CAS 서버 구성에 있다면 온-프레미스 Exchange 커넥터가 CAS 서버 중 하나를 가리키도록 구성해야 합니다.
> - Configuration Manager를 Microsoft Exchange 온-프레미스에 연결하는 Exchange Server 커넥터를 사용합니다. 커넥터를 통해 모바일 디바이스를 관리하고 조건부 액세스를 사용하도록 설정할 수 있습니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.
>   - 최신 버전의 온-프레미스 Exchange 커넥터를 사용하고 있는지 확인합니다. 온-프레미스 Exchange 커넥터를 Configuration Manager 콘솔을 통해 구성합니다. 자세한 연습 과정을 보려면 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.
>   - Configuration Manager 주 사이트에서만 커넥터를 구성합니다.

- Exchange ActiveSync는 인증서 기반 인증 또는 사용자 자격 증명 항목으로 구성할 수 있습니다.


## <a name="requirements-for-skype-for-business-online"></a>비즈니스용 Skype Online에 대한 요구 사항
Skype Online에 대한 조건부 액세스에서는 다음을 실행하는 디바이스를 지원합니다.
- iOS 7.1 이상
- Android 4.0 이상
- Samsung KNOX Standard 4.0 이상

비즈니스용 Skype Online에 대한 [최신 인증](https://aka.ms/SkypeModernAuth)을 사용하도록 설정합니다. 

모든 사용자가 비즈니스용 Skype Online을 사용해야 합니다. 비즈니스용 Skype Online과 온-프레미스 비즈니스용 Skype를 모두 배포한 경우 조건부 액세스 정책이 온-프레미스 사용자에게 적용되지 않습니다.

## <a name="requirements-for-sharepoint-online"></a>SharePoint Online에 대한 요구 사항
SharePoint Online에 대한 조건부 액세스에서는 다음을 실행하는 디바이스를 지원합니다.
- Windows 8.1 이상(Intune에 등록된 경우)
- Windows 7.0 또는 Windows 8.1(도메인에 가입된 경우)
- Windows Phone 8.1 이상
- iOS 7.1 이상
- Android 4.0 이상, Samsung KNOX Standard 4.0 이상

  **추가 필수 조건**:
- 디바이스는 AAD DRS(Azure Active Directory Device Registration Service)에 디바이스를 등록하는 작업 공간에 연결되어 있어야 합니다.

  도메인에 가입된 PC는 그룹 정책 또는 MSI를 통해 Azure Active Directory에 자동으로 등록되어야 합니다. PC에 대해 조건부 액세스를 사용하도록 설정하기 위한 모든 요구 사항은 이 문서의 **PC에 대한 조건부 액세스** 섹션에 설명되어 있습니다.

  Microsoft Intune 및 Office 365 고객의 경우 AAD DRS가 자동으로 활성화됩니다. ADFS 디바이스 등록 서비스를 이미 배포한 고객의 온-프레미스 Active Directory에는 등록된 디바이스가 표시되지 않습니다.
- SharePoint Online 구독이 필요하며 사용자는 SharePoint Online의 라이선스를 취득해야 합니다.

  ### <a name="conditional-access-for-pcs"></a>PC에 대한 조건부 액세스

  Office 데스크톱 애플리케이션을 실행하고 Exchange Online 또는 SharePoint Online에 액세스하는 PC에 조건부 액세스를 구성할 수 있습니다. PC는 다음과 같은 요구 사항을 충족해야 합니다.
- PC에서 Windows 7.0 또는 Windows 8.1을 실행해야 합니다.
- PC가 도메인에 가입되어 있거나 정책을 준수해야 합니다.

  PC가 정책을 준수하도록 하려면 Microsoft Intune에서 PC를 등록해야 하며 정책을 준수하도록 설정해야 합니다.

  도메인에 가입된 PC의 경우 Azure Active Directory에 [디바이스를 자동으로 등록](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) 하도록 설정해야 합니다.
- [Office 365 최신 인증을 사용](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/)하도록 설정해야 하며 최신 Office 업데이트를 모두 설치해야 합니다.<br />     최신 인증을 사용하는 경우 Office 2013 Windows 클라이언트에 ADAL(Active Directory 인증 라이브러리) 기반 로그인 기능이 제공되며, 다단계 인증 및 인증서 기반 인증과 같은 더욱 효율적인 보안 기능을 사용할 수 있습니다.
- 최신 인증 이외의 인증 프로토콜을 차단하도록 ADFS 클레임 규칙을 설정해야 합니다.  

## <a name="next-steps"></a>다음 단계  
 필요한 시나리오에 대해 준수 정책 및 조건부 액세스 정책을 구성하는 방법을 알아보려면 다음 항목을 읽어보세요.  

- [System Center Configuration Manager에서 디바이스 규정 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)  

- [System Center Configuration Manager에서 메일 액세스 관리](../../protect/deploy-use/manage-email-access.md)  

- [System Center Configuration Manager에서 SharePoint Online 액세스 관리](../../protect/deploy-use/manage-sharepoint-online-access.md)  

- [비즈니스용 Skype Online 액세스 관리](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>참고 항목  

 [System Center Configuration Manager에서 준수 설정 시작](../../compliance/get-started/get-started-with-compliance-settings.md)
