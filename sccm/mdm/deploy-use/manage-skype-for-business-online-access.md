---
title: 비즈니스용 Skype Online 액세스 관리
titleSuffix: Configuration Manager
description: 조건부 액세스 정책을 사용하여 비즈니스용 Skype Online에 대한 액세스를 관리하는 방법을 알아봅니다.
ms.date: 03/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 55d882542f8b830ca3ae8a739f60c797c6b7ea80
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75826903"
---
# <a name="manage-skype-for-business-online-access"></a>비즈니스용 Skype Online 액세스 관리

*적용 대상: Configuration Manager (현재 분기)*


비즈니스용 Skype Online에 대한 조건부 액세스 정책을 사용하여 지정된 조건에 따라 비즈니스용 Skype Online에 대한 액세스를 관리할 수 있습니다.  


 대상 사용자가 디바이스에서 비즈니스용 Skype Online을 사용하는 경우 다음과 같은 평가 작업이 수행됩니다.![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>전제 조건  

- 비즈니스용 Skype Online에 대한 [최신 인증](https://aka.ms/SkypeModernAuth)을 사용하도록 설정합니다.   

- 모든 사용자가 비즈니스용 Skype Online을 사용해야 합니다. 비즈니스용 Skype Online과 온-프레미스 비즈니스용 Skype를 모두 배포한 경우 조건부 액세스 정책이 온-프레미스 사용자에게 적용되지 않습니다.  

- 비즈니스용 Skype Online에 액세스해야 하는 디바이스는 다음과 같은 조건을 충족해야 합니다.  

  -   Android 또는 iOS 디바이스여야 합니다.

  -   Microsoft Intune에 등록되어 있어야 합니다.

  -   배포된 Microsoft Intune 준수 정책을 준수해야 합니다.

  Azure Active Directory는 지정된 조건에 따라 액세스를 부여하거나 차단하는 디바이스 상태를 저장합니다.  
  조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.  

- 디바이스를 Microsoft Intune에 등록하지 않거나 Azure Active Directory에 등록하지 않은 경우 사용자에게 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 표시됩니다.  

- 디바이스가 호환되지 않으면 사용자에게 회사 포털 웹 사이트 또는 회사 포털 앱을 가리키는 메시지가 표시됩니다. 회사 포털에는 문제 및 해결 방법에 대한 정보가 있습니다.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>비즈니스용 Skype Online에 대한 조건부 액세스 구성  

### <a name="step-1-configure-active-directory-security-groups"></a>1단계: Active Directory 보안 그룹 구성  
 시작하기 전에 조건부 액세스 정책에 대한 Azure Active Directory 보안 그룹을 구성합니다. Microsoft 365 관리 센터에서 이러한 그룹을 구성 합니다. 이러한 그룹에는 대상으로 지정한 사용자 또는 정책에서 제외된 사용자가 포함됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 디바이스가 규정을 준수해야 리소스에 액세스할 수 있습니다.  

 비즈니스용 Skype 정책에 사용할 두 가지 그룹 유형을 지정할 수 있습니다.  

-   **대상 그룹**에는 정책이 적용되는 사용자가 포함됩니다.  

-   **제외된 그룹**에는 정책에서 제외된 사용자가 포함됩니다.  
    사용자가 두 그룹에 모두 있으면 제외됩니다.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2단계: 준수 정책 구성 및 배포  
 준수 정책을 만들고 비즈니스용 Skype Online 정책의 대상이 되는 모든 디바이스에 배포합니다.  

 준수 정책을 구성하는 방법에 대한 자세한 내용은 [디바이스 규정 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)를 참조하세요.  

> [!NOTE]  
>  준수 정책을 배포하지 않은 상태에서 비즈니스용 Skype Online 정책을 사용하도록 설정하면 Microsoft Intune에 등록되어 있는 경우 대상으로 지정된 모든 디바이스에 대한 액세스가 허용됩니다.  


### <a name="step-3-configure-the-skype-for-business-online-policy"></a>3단계: 비즈니스용 Skype Online 정책 구성  
 규정을 준수하는 관리 디바이스만 비즈니스용 Skype Online에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure Active Directory에 저장됩니다.  

1. [Microsoft Intune 관리 콘솔](https://manage.microsoft.com)에서 **정책** > **조건부 액세스** > **Skype for Business Online 정책**를 참조하세요.  

    ![ConditionalAccess&#95;SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2. **조건부 액세스 정책 사용**을 선택합니다.  

3. **애플리케이션 액세스** 아래에서 다음 플랫폼에 조건부 액세스 정책을 적용하도록 선택할 수 있습니다.  

   -   iOS  

   -   Android  

4. **대상 그룹**에서 **수정**을 클릭하여 정책을 적용할 Azure Active Directory 보안 그룹을 선택합니다. 모든 사용자 또는 선택한 사용자 그룹에 이 정책을 대상으로 지정할 수 있습니다.  

5. **제외된 그룹**에서 필요에 따라 **수정** 을 클릭하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.  

6. 작업이 끝나면 **저장**을 클릭합니다.  

   이제 비즈니스용 Skype Online에 대한 조건부 액세스를 구성했습니다. 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>준수 및 조건부 액세스 정책 모니터링  
 그룹 작업 영역에서 디바이스의 조건부 액세스 상태를 확인할 수 있습니다.  

 모바일 디바이스 그룹을 선택하고 **디바이스** 탭에서 다음 **필터**중 하나를 선택합니다.  

-   **AAD에 등록되지 않은 디바이스**는 비즈니스용 Skype Online에서 차단됩니다.

-   **호환되지 않는 디바이스**는 비즈니스용 Skype Online에서 차단됩니다.  

-   **AAD에 등록되어 있고 규정을 준수하는 디바이스**는 비즈니스용 Skype Online에 액세스할 수 있습니다.  

### <a name="see-also"></a>참고 항목  

 [장치 준수 정책 관리](../../protect/deploy-use/device-compliance-policies.md)
