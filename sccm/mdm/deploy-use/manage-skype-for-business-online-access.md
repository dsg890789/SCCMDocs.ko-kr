---
title: "비즈니스용 Skype Online 액세스 관리 | Microsoft 문서"
description: "조건부 액세스 정책을 사용하여 비즈니스용 Skype Online에 대한 액세스를 관리하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
caps.latest.revision: 6
author: mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: c39303c2e1a30ff4d7f27bd617a85516dd4cd15d
ms.lasthandoff: 03/06/2017


---
# <a name="manage-skype-for-business-online-access"></a>비즈니스용 Skype Online 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*


**비즈니스용 Skype Online** 에 대한 조건부 액세스 정책을 사용하여 지정된 조건에 따라 비즈니스용 Skype Online에 대한 액세스를 관리할 수 있습니다.  


 대상 사용자가 장치에서 비즈니스용 Skype Online을 사용하는 경우 다음과 같은 평가 작업이 수행됩니다.![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>전제 조건  

-   비즈니스용 Skype Online에 대한 최신 인증을 사용하도록 설정합니다. 최신 인증 프로그램에 등록하려면 [Connect 양식](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) 을 작성하세요.  

-   모든 최종 사용자는 비즈니스용 Skype Online을 사용해야 합니다. 비즈니스용 Skype Online과 온-프레미스 비즈니스용 Skype를 모두 배포한 경우 조건부 액세스 정책이 최종 사용자에게 적용되지 않습니다.  

-   비즈니스용 Skype Online에 액세스해야 하는 장치는 다음과 같은 조건을 충족해야 합니다.  

    -   Android 또는 iOS 장치여야 합니다.  

    -   Intune에 등록되어 있어야 합니다.  

    -   배포된 Intune 규정 준수 정책을 준수해야 합니다.  

 장치 상태는 지정된 조건에 따라 액세스를 부여하거나 차단하는 Azure Active Directory에 저장됩니다.  
조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.  

-   장치를 Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우, 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.  

-   장치가 규정을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Intune 웹 포털 또는 회사 포털 앱과 문제의 해결 방법을 알려 주는 메시지가 표시됩니다.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>비즈니스용 Skype Online에 대한 조건부 액세스 구성  

### <a name="step-1-configure-active-directory-security-groups"></a>1단계: Active Directory 보안 그룹 구성  
 시작하기 전에 조건부 액세스 정책에 대한 Azure Active Directory 보안 그룹을 구성합니다. Office 365 관리 센터에서 이러한 그룹을 구성할 수 있습니다. 이러한 그룹에는 정책의 대상이 되거나 정책에서 제외되는 사용자가 포함됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 장치가 규정을 준수해야 리소스에 액세스할 수 있습니다.  

 비즈니스용 Skype 정책에 사용할 두 개의 그룹 유형을 지정할 수 있습니다.  

-   대상 그룹 - 정책이 적용되는 사용자 그룹을 포함합니다.  

-   제외된 그룹 - 정책에서 제외되는 사용자 그룹을 포함합니다(선택 사항).  
    사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2단계: 규정 준수 정책 구성 및 배포  
 규정 준수 정책을 만들고 비즈니스용 Skype Online 정책의 대상이 될 모든 장치에 배포해야 합니다.  

 준수 정책을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 장치 규정 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)를 참조하세요.  

> [!NOTE]  
>  준수 정책을 배포하지 않은 상태에서 비즈니스용 Skype Online 정책을 사용하도록 설정하면 Intune에 등록되어 있으며 대상으로 지정된 모든 장치에 대한 액세스가 허용됩니다.  

 준비가 되었으면 3단계를 계속합니다.  

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>3 단계: 비즈니스용 Skype Online 정책 구성  
 이제, 규정을 준수하는 관리 장치만 비즈니스용 Skype Online에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure Active Directory에 저장됩니다.  

1.  [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **조건부 액세스** > **Skype for Business Online 정책**를 참조하세요.  

     ![ConditionalAccess&#95;SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2.  **조건부 액세스 정책 사용**을 선택합니다.  

3.  **응용 프로그램 액세스**에서 다음 플랫폼에 조건부 액세스 정책을 적용하도록 선택할 수 있습니다.  

    -   iOS  

    -   Android  

4.  **대상 그룹**에서 **수정** 을 클릭하여 정책을 적용할 Azure Active Directory 보안 그룹을 선택합니다. 모든 사용자 또는 선택한 사용자 그룹을 대상으로 지정할 수 있습니다.  

5.  **제외된 그룹**에서 필요에 따라 **수정** 을 클릭하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.  

6.  작업이 끝나면 **저장**을 클릭합니다.  

 이제 비즈니스용 Skype Online에 대한 조건부 액세스를 구성했습니다. 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>준수 및 조건부 액세스 정책 모니터링  
 그룹 작업 영역에서 장치의 조건부 액세스 상태를 확인할 수 있습니다.  

 모바일 장치 그룹을 선택하고 **장치** 탭에서 다음 **필터**중 하나를 선택합니다.  

-   **AAD에 등록되지 않은 장치** - 이러한 장치는 비즈니스용 Skype Online에서 차단됩니다.  

-   **정책을 준수하지 않는 장치** - 이러한 장치는 비즈니스용 Skype Online에서 차단됩니다.  

-   **AAD에 등록되어 있고 정책을 준수하는 장치** - 이러한 장치는 비즈니스용 Skype Online에 액세스할 수 있습니다.  

### <a name="see-also"></a>참고 항목  

 [System Center Configuration Manager에서 장치 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)

