---
title: "Dynamics CRM Online 액세스 관리 | Microsoft 문서"
description: "Microsoft Intune 조건부 액세스를 사용하여 iOS 및 Android 장치에서 Microsoft Dynamics CRM Online에 대한 액세스를 제어하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c7cec31-f78d-46b9-93ae-a12ae27a1de6
caps.latest.revision: 5
author: andredm7
ms.author: andredm
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: c13c6268fa76ade7feb0981f9c4a6e325e393aca
ms.openlocfilehash: 77bbe36b4662046b0f693fac6186f8b19615353a

---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Dynamics CRM Online 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 조건부 액세스를 사용하여 iOS 및 Android 장치에서 Microsoft Dynamics CRM Online에 대한 액세스를 제어할 수 있습니다.  Intune 조건부 액세스는 다음 두 가지 구성 요소로 이루어져 있습니다.
* [장치 준수 정책](../../protect/deploy-use/device-compliance-policies.md) - 장치가 규격으로 간주되기 위해 준수해야 하는 정책입니다.
* [조건부 액세스 정책](../../protect/deploy-use/manage-access-to-services.md) - 여기서 장치가 서비스에 액세스하기 위해 충족해야 하는 조건을 지정합니다.

조건부 액세스의 작동 방식을 자세히 알아보려면 [서비스에 대한 액세스 관리](../../protect/deploy-use/manage-access-to-services.md) 문서를 참조하세요.


대상 사용자가 장치에서 Dynamics CRM 앱을 사용하는 경우 다음과 같은 평가 작업이 수행됩니다.

![다이어그램은 장치의 서비스 액세스가 허용 또는 차단되는지를 확인하는 데 사용되는 의사 결정 지점을 보여 줍니다.](../media/mdm-ca-dynamics-crm-flow-diagram.png)

Dynamics CRM Online에 액세스해야 하는 장치는 다음과 같은 조건을 충족해야 합니다.
* **Android** 또는 **iOS** 장치여야 합니다.
* Microsoft Intune에 **등록**되어 있어야 합니다.
* 배포된 Microsoft Intune 준수 정책을 **준수**해야 합니다.

장치 상태는 지정된 조건에 따라 액세스를 부여하거나 차단하는 Azure Active Directory에 저장됩니다.

조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.
* 장치를 Microsoft Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우, 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.
* 장치가 정책을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Microsoft Intune 웹 포털 또는 회사 포털 앱과 문제를 해결하는 방법을 알려주는 메시지가 표시됩니다.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Dynamics CRM Online에 대한 조건부 액세스 구성  
### <a name="step-1-configure-active-directory-security-groups"></a>1단계: Active Directory 보안 그룹 구성

시작하기 전에 조건부 액세스 정책에 대한 Azure Active Directory 보안 그룹을 구성합니다. **Office 365 관리 센터**에서 이러한 그룹을 구성할 수 있습니다. 이 그룹은 정책에서 사용자를 대상으로 지정하거나 제외하는 데 사용됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 장치가 규정을 준수해야 리소스에 액세스할 수 있습니다.

Dynamics CRM 정책에 사용할 두 가지 그룹 유형을 지정할 수 있습니다.
* **대상 그룹** - 정책이 적용되는 사용자 그룹을 포함합니다.
* **제외된 그룹** - 정책에서 제외되는 사용자 그룹을 포함합니다.

사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2단계: 규정 준수 정책 구성 및 배포
정책의 영향을 받는 모든 장치에 준수 정책을 [만들어 배포](../../protect/deploy-use/device-compliance-policies.md)합니다. 이러한 모든 장치는 대상 그룹의 사용자가 사용합니다.

> [!NOTE]
> 준수 정책을 Microsoft Intune에 배포하는 동안 Azure Active Directory 보안 그룹을 조건부 액세스 정책의 대상으로 합니다.

> [!IMPORTANT]
> 준수 정책을 배포하지 않은 경우에는 장치가 규격으로 처리됩니다.

준비가 되었으면 3단계를 계속합니다.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>3단계: Dynamics CRM 정책 구성
다음에는 관리되고 정책을 준수하는 장치만 Dynamics CRM에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure Active Directory에 저장됩니다.

1.  Microsoft Intune 관리 콘솔에서 **정책 > 조건부 액세스 > Dynamics CRM Online 정책**을 선택합니다.

     ![Dynamics CRM Online 조건부 액세스 정책 페이지의 스크린샷](../media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  **조건부 액세스 정책 사용**을 선택합니다.
3.  **응용 프로그램 액세스**에서 다음 플랫폼에 조건부 액세스 정책을 적용하도록 선택할 수 있습니다.
  * **iOS**
  * **OWA(Outlook Web Access)**
4.  **대상 그룹**에서 **수정**을 선택하여 정책을 적용할 Azure Active Directory 보안 그룹을 선택합니다. 모든 사용자 또는 선택한 사용자 그룹을 대상으로 지정할 수 있습니다.
5.  **제외된 그룹**에서 필요에 따라 **수정**을 선택하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.
6.  작업이 끝나면 **저장**을 선택합니다.

이제 Dynamics CRM에 대한 조건부 액세스를 구성했습니다. 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>준수 및 조건부 액세스 정책 모니터링

**그룹** 작업 영역에서 장치의 조건부 액세스 상태를 확인할 수 있습니다.

모바일 장치 그룹을 선택하고 **장치** 탭에서 다음 **필터**중 하나를 선택합니다.
* **AAD에 등록되지 않은 장치** - 이러한 장치는 Dynamics CRM에서 차단됩니다.
* **정책을 준수하지 않는 장치** - 이러한 장치는 Dynamics CRM에서 차단됩니다.
* **AAD에 등록되어 있고 정책을 준수하는 장치** - 이러한 장치는 Dynamics CRM에 액세스할 수 있습니다.

###  <a name="see-also"></a>참고 항목
[메일에 대한 액세스 관리](../../protect/deploy-use/manage-email-access.md)

[SharePoint Online에 대한 액세스 관리](../../protect/deploy-use/manage-sharepoint-online-access.md)

[비즈니스용 Skype Online에 대한 액세스 관리](../../protect/deploy-use/manage-skype-for-business-online-access.md)



<!--HONumber=Dec16_HO3-->


