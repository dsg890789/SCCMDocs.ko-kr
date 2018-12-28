---
title: Dynamics CRM Online 액세스 관리
titleSuffix: Configuration Manager
description: Microsoft Intune 조건부 액세스를 사용하여 iOS 및 Android 디바이스에서 Microsoft Dynamics CRM Online에 대한 액세스를 제어하는 방법을 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 2bfc4c51-b25c-4c70-b81e-8a3b6ddf02c8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5e2c8ab4f8dc0b544a79b2113c278f97444357bf
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53420960"
---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Dynamics CRM Online 액세스 관리

*적용 대상: System Center Configuration Manager (현재 분기)*

Microsoft Intune 조건부 액세스가 설정된 iOS 및 Android 디바이스에서 Microsoft Dynamics CRM Online에 대한 액세스를 제어할 수 있습니다.  Intune 조건부 액세스는 다음 두 가지 구성 요소로 이루어져 있습니다.
* 디바이스를 준수로 간주하기 위해 디바이스가 준수해야 하는 [디바이스 규정 준수 정책](../../protect/deploy-use/device-compliance-policies.md)
* 디바이스에서 서비스에 액세스하기 위해 충족해야 하는 조건을 지정하는 [조건부 액세스 정책](../../protect/deploy-use/manage-access-to-services.md)

조건부 액세스의 작동 방식을 자세히 알아보려면 [서비스에 대한 액세스 관리](../../protect/deploy-use/manage-access-to-services.md) 문서를 참조하세요.


대상 사용자가 디바이스에서 Dynamics CRM 앱을 사용하려고 시도하는 경우 다음 평가가 발생합니다.

![디바이스에서 서비스에 대한 액세스가 허용 또는 차단되는지 여부를 결정하는 데 사용되는 결정 지점을 보여 주는 다이어그램](media/mdm-ca-dynamics-crm-flow-diagram.png)

Dynamics CRM Online에 액세스해야 하는 디바이스는 다음과 같아야 합니다.
* **Android** 또는 **iOS** 디바이스여야 합니다.
* Microsoft Intune에 **등록**되어 있어야 합니다.
* 배포된 Microsoft Intune 준수 정책을 **준수**해야 합니다.

디바이스 상태는 지정된 조건에 따라 액세스를 부여하거나 차단하는 Azure Active Directory에 저장됩니다.

조건이 충족되지 않으면 사용자가 로그인할 때 다음 메시지 중 하나가 표시됩니다.
* 디바이스를 Microsoft Intune에 등록하지 않았거나 Azure Active Directory에 등록하지 않은 경우, 회사 포털 앱을 설치하고 등록하는 방법에 관한 지침이 포함된 메시지가 표시됩니다.
* 디바이스가 규정을 준수하지 않으면 사용자가 문제에 관한 정보를 찾을 수 있는 Microsoft Intune 웹 포털 또는 회사 포털 앱과 문제의 해결 방법을 알려 주는 메시지가 표시됩니다.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Dynamics CRM Online에 대한 조건부 액세스 구성  
### <a name="step-1-configure-active-directory-security-groups"></a>1 단계: Active Directory 보안 그룹 구성

시작하기 전에 조건부 액세스 정책에 대한 Azure Active Directory 보안 그룹을 구성합니다. **Office 365 관리 센터**에서 이러한 그룹을 구성할 수 있습니다. 이 그룹은 정책에서 사용자를 대상으로 지정하거나 제외하는 데 사용됩니다. 사용자가 정책의 대상인 경우 해당 사용자가 사용하는 각 디바이스가 규정을 준수해야 리소스에 액세스할 수 있습니다.

Dynamics CRM 정책에 사용할 두 가지 그룹 유형을 지정할 수 있습니다.
* **대상 그룹** - 정책이 적용되는 사용자 그룹을 포함합니다.
* **제외된 그룹** - 정책에서 제외되는 사용자 그룹을 포함합니다.

사용자가 두 그룹에 모두 속한 경우에는 정책에서 제외됩니다.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>2 단계: 준수 정책 구성 및 배포
정책의 영향을 받는 모든 디바이스에 준수 정책을 [만들어 배포](../../protect/deploy-use/device-compliance-policies.md)합니다. 대상 그룹에서 사용자가 사용하는 모든 디바이스가 됩니다.

> [!NOTE]
> 준수 정책을 Microsoft Intune에 배포하는 동안 Azure Active Directory 보안 그룹을 조건부 액세스 정책의 대상으로 합니다.

> [!IMPORTANT]
> 규정 준수 정책을 배포하지 않은 경우 디바이스는 준수하는 것으로 간주됩니다.

준비가 되었으면 3단계를 계속합니다.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>3 단계: Dynamics CRM 정책 구성
다음으로 관리되고 규정을 준수하는 디바이스만 Dynamics CRM에 액세스할 수 있도록 요구하는 정책을 구성합니다. 이 정책은 Azure Active Directory에 저장됩니다.

1. Microsoft Intune 관리 콘솔에서 **정책 > 조건부 액세스 > Dynamics CRM Online 정책**을 선택합니다.

    ![Dynamics CRM Online 조건부 액세스 정책 페이지의 스크린샷](media/mdm-ca-dynamics-crm-policy-configuration.png)

2. **조건부 액세스 정책 사용**을 선택합니다.
3. **애플리케이션 액세스**에서 다음 플랫폼에 조건부 액세스 정책을 적용하도록 선택할 수 있습니다.
   * **Android**
   * **OWA(Outlook Web Access)**
4. **대상 그룹**에서 **수정**을 선택하여 정책을 적용할 Azure Active Directory 보안 그룹을 선택합니다. 모든 사용자 또는 선택한 사용자 그룹을 대상으로 지정할 수 있습니다.
5. **제외된 그룹**에서 필요에 따라 **수정**을 선택하여 이 정책에서 제외된 Azure Active Directory 보안 그룹을 선택합니다.
6. 작업이 끝나면 **저장**을 선택합니다.

이제 Dynamics CRM에 대한 조건부 액세스를 구성했습니다. 조건부 액세스 정책을 배포할 필요는 없으며, 즉시 적용됩니다.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>준수 및 조건부 액세스 정책 모니터링

**그룹** 작업 영역에서 디바이스의 조건부 액세스 상태를 볼 수 있습니다.

모바일 디바이스 그룹을 선택하고 **디바이스** 탭에서 다음 **필터**중 하나를 선택합니다.
* **AAD에 등록되지 않은 디바이스** – 이러한 디바이스는 Dynamics CRM에서 차단됩니다.
* **규정을 준수하지 않은 디바이스** – 이러한 디바이스는 Dynamics CRM에서 차단됩니다.
* **AAD에 등록되어 있고 규정을 준수하는 디바이스** – 이러한 디바이스 Dynamics CRM에 액세스할 수 있습니다.

###  <a name="see-also"></a>참고 항목
[메일에 대한 액세스 관리](../../protect/deploy-use/manage-email-access.md)

[SharePoint Online에 대한 액세스 관리](../../protect/deploy-use/manage-sharepoint-online-access.md)

[비즈니스용 Skype Online에 대한 액세스 관리](../../protect/deploy-use/manage-skype-for-business-online-access.md)
