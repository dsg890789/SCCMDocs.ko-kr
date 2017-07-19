---
title: "관리되는 PC용 O365 서비스에 대한 액세스 관리 | Microsoft 문서"
description: "System Center Configuration Manager에서 관리되는 PC에 대한 조건부 액세스를 구성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34024741-edfa-4088-8599-d6bafc331e62
caps.latest.revision: 15
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: c8717925dba42451b1e241a7c2f59e43896d7d99
ms.openlocfilehash: e78fe989b7ff445717c8320c4eae3900eb46baea
ms.contentlocale: ko-kr
ms.lasthandoff: 06/19/2017


---
# <a name="manage-access-to-o365-services-for-pcs-managed-by-system-center-configuration-manager"></a>System Center Configuration Manager에서 관리되는 PC용 O365 서비스에 대한 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 버전 1602부터 System Center Configuration Manager에서 관리되는 PC에 대한 조건부 액세스를 구성할 수 있습니다.  

> [!IMPORTANT]  
> 이 기능은 업데이트 1602, 업데이트 1606 및 업데이트 1610에서 사용할 수 있는 시험판 기능입니다. 시험판 기능은 프로덕션 환경의 초기 테스트를 위한 제품에 포함되었지만 이러한 기능은 프로덕션 준비가 된 것으로 간주되지 않아야 합니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease)을 참조하세요.
> - 업데이트 1602를 설치하면 기능 유형이 시험판 버전임에도 출시됨으로 표시됩니다.
> - 그런 다음 1602에서 1606으로 업데이트하면 기능 유형이 여전히 시험판인 경우에도 출시됨으로 표시됩니다.
> - 버전 1511에서 1606으로 바로 업데이트하면 기능 유형이 시험판으로 표시됩니다.

Intune을 통해 등록하여 관리하는 장치 또는 도메인에 가입되었으며 준수 여부가 평가되지 않은 PC에 대한 조건부 액세스를 구성하는 방법에 관한 자세한 내용을 원하는 경우 [System Center Configuration Manager에서 서비스에 대한 액세스 관리](../../protect/deploy-use/manage-access-to-services.md)를 참조하세요.

## <a name="supported-services"></a>지원되는 서비스  

-   Exchange Online
-   SharePoint Online

## <a name="supported-pcs"></a>지원되는 PC  

-   Windows 7
-   Windows 8.1
-   Windows 10 

## <a name="configure-conditional-access"></a>조건부 액세스 구성  
 조건부 액세스를 설정하려면 먼저 규정 준수 정책을 만들고 조건부 액세스 정책을 구성해야 합니다. PC에 대한 조건부 액세스 정책을 설정할 때 Exchange Online 및 SharePoint Online 서비스에 액세스하기 위해 PC가 준수 정책을 준수하도록 요구할 수 있습니다.  

### <a name="prerequisites"></a>전제 조건  

-   ADFS 동기화 및 O365 구독. O365 구독은 Exchange Online 및 SharePoint Online을 설정하는 데 사용됩니다.  

-   Microsoft Intune 구독 Microsoft Intune 구독은 Configuration Manager 콘솔에서 구성해야 합니다. Intune 구독은 장치 준수 상태를 Azure Active Directory에 릴레이하고 사용자 사용을 허가하는 데 사용됩니다.  

 PC는 다음과 같은 요구 사항을 충족해야 합니다.  

-   Azure Active Directory에 자동 장치 등록의[필수 조건](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)   

     규정 준수 정책을 통해 Azure AD에 PC를 등록할 수 있습니다.  

    -   Windows 8.1 및 Windows 10 PC의 경우 Active Directory 그룹 정책을 사용하여 Azure AD에 자동으로 등록되도록 장치를 구성할 수 있습니다.  

    -   o   Windows 7 PC의 경우 System Center Configuration Manager를 통해 Windows 7 PC에 장치 등록 소프트웨어 패키지를 배포해야 합니다. [Windows 도메인에 가입된 장치의 Azure Active Directory 자동 장치 등록](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) 항목에서 자세한 내용을 제공합니다.  

-   최신 인증을 [사용](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)하는 상태에서 Office 2013 또는 Office 2016을 사용해야 합니다.  

 아래에 설명된 단계는 Exchange Online 및 SharePoint Online에 적용됩니다.  

### <a name="step-1-configure-compliance-policy"></a>1단계. 준수 정책 구성  
 Configuration Manager 콘솔에서 다음 규칙으로 준수 정책을 만듭니다.  

-   Azure Active Directory에서 등록 필요: 이 규칙은 사용자 장치가 Azure AD에 연결된 작업 공간인지 확인합니다. 연결되지 않은 경우 장치가 Azure AD에 자동으로 등록됩니다. 자동 등록은 Windows 8.1에서만 지원됩니다. Windows 7 PC의 경우 자동 등록을 수행하기 위해 MSI를 배포합니다. 자세한 내용은 [Azure Active Directory에 자동 장치 등록](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)을 참조하세요.  

-   **마감일이 다음 기간보다 오래된 필수 업데이트가 모두 설치됨:** 이 규칙은 마감일 및 사용자가 지정한 유예 기간 내에 사용자 장치에 모든 필수 업데이트(필수 자동 업데이트 규칙에 지정)가 설치되는지 확인하고 보류 중인 모든 필수 업데이트를 자동으로 설치합니다.  

-   **BitLocker 드라이브 암호화 필요:** 장치의 기본 드라이브(예: C:\\)가 BitLocker로 암호화되어 있는지 확인합니다. 기본 장치에서 Bitlocker 암호화가 사용되도록 설정되지 않으면 메일 및 SharePoint 서비스에 대한 액세스가 차단됩니다.  

-   **맬웨어 방지 필요:** 맬웨어 방지 프로그램(System Center Endpoint Protection 또는 Windows Defender만)이 사용되도록 설정되고 실행 중인지 확인합니다. 사용되도록 설정되지 않았으면 메일 및 SharePoint 서비스에 대한 액세스가 차단됩니다.  

### <a name="step-2-evaluate-the-effect-of-conditional-access"></a>2단계. 조건부 액세스의 영향 평가  
 조건부 액세스 규정 준수 보고서를 실행합니다. 이 보고서는 모니터링 섹션에서 보고서 > 호환 및 설정 관리에서 찾을 수 있습니다. 이 보고서를 실행하면 모든 장치에 대한 준수 상태가 표시됩니다.  규격이 아닌 것으로 보고되는 장치는 Exchange Online 및 SharePoint Online에 액세스하지 못하도록 차단됩니다.  

 ![CA&#95;준수&#95;보고서](media/CA_compliance_report.png)  

### <a name="configure-active-directory-security-groups"></a>Active Directory 보안 그룹 구성  
 정책 유형에 따라 사용자 그룹을 대상으로 조건부 액세스 정책을 구성합니다. 이러한 그룹에는 정책의 대상이 되거나 정책에서 제외되는 사용자가 포함됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 장치가 규정을 준수해야 서비스에 액세스할 수 있습니다.  

 Active Directory 보안 사용자 그룹입니다. 이러한 사용자 그룹은 Azure Active Directory와 동기화되어야 합니다. Office 365 관리 센터 또는 Intune 계정 포털에서 이러한 그룹을 구성할 수도 있습니다.  

 각 정책에 두 그룹 유형을 지정할 수 있습니다. :  

-   **대상 그룹** - 정책이 적용되는 사용자 그룹 준수 및 조건부 액세스 정책 둘 다에 동일한 그룹을 사용해야 합니다.  

-   **제외된 그룹** - 정책에서 제외되는 사용자 그룹(선택 사항)  
    사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.  

     조건부 액세스 정책의 대상인 그룹만이 평가됩니다.  

### <a name="step-3--create-a-conditional-access-policy-for-exchange-online-and-sharepoint-online"></a>3단계:  Exchange Online 및 SharePoint Online에 대한 조건부 액세스 정책 만들기  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  Exchange Online에 대한 정책을 만들려면 **Exchange Online에 대한 조건적 액세스 정책 사용**을 선택합니다.  

     SharePoint Online에 대한 정책을 만들려면 **Exchange Online에 대한 조건적 액세스 정책 사용**을 선택합니다.  

3.  **홈** 탭의 **링크** 그룹에서 **Intune 콘솔에서 조건부 액세스 정책 구성**을 클릭합니다. Configuration Manager와 Intune을 연결하는 데 사용되는 계정의 사용자 이름과 암호를 입력해야 할 수 있습니다.  

     Intune 관리 콘솔이 열립니다.  

4.  Exchange Online의 경우 Microsoft Intune 관리 콘솔에서 **정책 > 조건부 액세스 > Exchange Online 정책**을 클릭합니다.  

     SharePoint Online의 경우 Microsoft Intune 관리 콘솔에서 **정책 > 조건부 액세스 > SharePoint Online 정책**을 클릭합니다.  

5.  Windows PC 요구 사항을**장치가 호환되어야 함 옵션**으로 설정합니다.  

6.  **대상 그룹**에서 **수정** 을 클릭하여 정책을 적용할 Azure Active Directory 보안 그룹을 선택합니다.  

    > [!NOTE]  
    >  준수 정책 및 조건부 액세스 정책의 대상 그룹을 배포하는 데 동일한 보안 사용자 그룹을 사용해야 합니다.  

     **제외된 그룹**에서 필요에 따라 **수정** 을 클릭하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.  

7.  **저장** 을 클릭하여 정책을 만들고 저장합니다.  

 비준수로 인해 차단된 최종 사용자는 System Center Configuration Manager 소프트웨어 센터에서 호환성 정보를 확인하고 호환성 문제가 해결되면 새로운 정책 평가를 시작합니다.  

<!---
##  <a name="bkmk_KnownIssues"></a> Known issues  
 You may see the following issues when using this feature:  

-   In this 1602 update,  the 5 day compliance is not enforced. Even if compliance check on the end-user's device has happened more than 5 days ago, users still can access Office 365 and SharePoint online.  

-   When a device is not compliant with the compliance policy, the reason is not automatically displayed. The end- user must go to the new Software Center to find the reason for non-compliance. The reason is displayed in the Device compliance section of the Software Center.  

-   Windows 10 users may see multiple access failures when trying to reach O365 and/or SharePoint online resources. Note that conditional access is not fully supported for Windows 10.  
--->
## <a name="see-also"></a>참고 항목

- [System Center Configuration Manager를 사용하여 데이터 및 사이트 인프라 보호](../../protect/understand/protect-data-and-site-infrastructure.md)
- [Configuration Manager에 대한 조건부 액세스 문제 해결 순서도](https://gallery.technet.microsoft.com/Conditional-access-fd747c1a?redir=0)

