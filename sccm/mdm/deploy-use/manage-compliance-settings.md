---
title: Intune으로 관리되는 디바이스에 대한 준수 관리
titleSuffix: Configuration Manager
description: 몇 가지 일반적인 시나리오를 진행하여 System Center Configuration Manager의 준수 설정에 대해 알아봅니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9e83007f-e81c-4b7e-b47e-b01d7b19cfbc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 012539cd5879691f0e42910c72cb03052e77b722
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32351448"
---
# <a name="managing-compliance-on-devices-managed-with-intune"></a>Intune으로 관리되는 디바이스에 대한 준수 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

이 시나리오에서는 일반적으로 발생할 수 있는 몇 가지 시나리오를 살펴보면서 System Center Configuration Manager 준수 설정을 사용하는 방법을 소개합니다.  

 준수 설정에 이미 익숙한 경우 사용할 수 있는 모든 기능에 대한 자세한 설명은 [Intune으로 관리되는 디바이스의 구성 항목](#configuration-items-for-devices-managed-with-intune) 섹션을 참조하세요.  

 [준수 설정 시작](../../compliance/get-started/get-started-with-compliance-settings.md)에서는 준수 설정에 대한 기본 사항을 제공하고, [준수 설정 계획 및 구성](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)에서는 필수 구성 요소를 구현하도록 도와줍니다.  

## <a name="general-information-for-each-scenario"></a>각 시나리오에 대한 일반 정보  
 각 시나리오에서는 특정 작업을 수행하는 구성 항목을 만듭니다. 구성 항목 만들기 마법사를 열고, 다음 단계를 따르세요.  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 항목**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **구성 항목 만들기**를 클릭합니다.  

4.  아래와 같은 구성 항목 만들기 마법사의 **일반** 탭에서, 구성 항목에 대한 이름 및 설명을 지정한 다음 이 항목의 각 시나리오에 대한 적절한 구성 항목 유형을 선택합니다.  

     ![구성 항목 만들기 마법사의 일반 페이지를 보여 줍니다.](media/Compliance-Settings-Wizard---1.png)  

## <a name="scenarios-for-windows-81-and-windows-10-devices-managed-with-intune"></a>Intune으로 관리되는 Windows 8.1 및 Windows 10 디바이스에 대한 시나리오  

### <a name="scenario-restrict-access-to-the-app-store-on-all-windows-pcs"></a>시나리오: 모든 Windows PC에서 앱 스토어에 대한 액세스 제한  
 이 시나리오에서는 매우 중요한 정보를 처리하는 회사 IT 관리자를 예로 듭니다. 매우 중요한 정보를 처리하기 때문에 사용자가 설치할 수 있는 앱을 제한합니다. 다음 작업을 수행하기 위해 모든 Windows 10 PC의 사용자가 Windows 스토어에서 앱을 다운로드하는 것을 중지할 수 있습니다.  

1.  구성 항목 만들기 마법사의 **일반** 페이지에서 **Windows 8.1 및 Windows 10** 구성 항목 유형을 선택하고 **다음**을 클릭합니다.  

2.  **지원되는 플랫폼**에서 모든 Windows 10 플랫폼을 선택합니다.  

3.  **장치 설정** 페이지에서 **스토어**를 선택하고 **다음**을 클릭합니다.  

4.  **스토어** 페이지에서 **앱 스토어** 의 값으로 **허용 안 함**을 선택합니다.  

5.  **비호환 설정 재구성** 을 선택하여 모든 PC에 변경 내용이 적용되도록 합니다.  

6.  마법사를 완료하여 구성 항목을 만듭니다.  

 이제 [구성 기준 만들기 및 배포에 대한 일반 작업](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) 항목의 내용을 참조하여, 만든 구성을 디바이스에 쉽게 배포할 수 있습니다.  

## <a name="scenarios-for-windows-phone-devices-managed-with-intune"></a>Intune으로 관리되는 Windows Phone 디바이스에 대한 시나리오  

### <a name="scenario-disable-the-use-of-screen-capture-on-a-windows-phone"></a>시나리오: Windows Phone에서 화면 캡처를 사용하지 않도록 설정  
 이 시나리오에서는, 회사에서 Windows Phone 8.1 디바이스를 사용합니다. 이러한 디바이스는 중요한 정보를 포함하는 판매 앱을 실행합니다. 회사를 보호하기 위해 회사 외부에서 중요한 정보를 전송하는 데 사용할 수 있는 디바이스에서 화면 캡처를 사용하지 않도록 설정할 수 있습니다.  

1.  구성 항목 만들기 마법사의 **일반** 페이지에서 **Windows Phone** 구성 항목 유형을 선택하고 **다음**을 클릭합니다.  

2.  **지원되는 플랫폼** 페이지에서 **모든 Windows Phone 8.1** 플랫폼을 선택합니다.  

3.  **장치 설정** 페이지에서 **장치**를 선택하고 **다음**을 클릭합니다.  

4.  **장치** 페이지에서 **화면 캡처** 의 값으로 **사용 안 함**을 선택합니다.  

5.  **비호환 설정 재구성** 을 선택하여 모든 Windows Phone 8.1 장치에 변경 내용이 적용되도록 합니다.  

6.  마법사를 완료하여 구성 항목을 만듭니다.  

 이제 [System Center Configuration Manager에서 구성 기준을 만들고 배포하기 위한 일반 작업](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) 항목의 내용을 참조하여, 만든 구성을 디바이스에 쉽게 배포할 수 있습니다.  

## <a name="scenarios-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Intune으로 관리되는 iOS 및 Mac OS X 디바이스에 대한 시나리오  

### <a name="scenario-disable-the-camera-on-ios-devices"></a>시나리오: iOS 디바이스에서 카메라 사용 안 함  
 이 시나리오에서 회사는 새로운 제품 설계에 대한 청사진을 생성합니다. 여기에는 누출되어서는 안 되는 중요한 정보가 포함되어 있습니다. 회사에서 모든 직원에게 iPhone 또는 iPad를 발급하므로, 이러한 디바이스의 카메라를 사용하여 청사진을 촬영하는 것을 방지하기 위해 카메라 사용을 비활성화할 수 있습니다.  

1.  구성 항목 만들기 마법사의 **일반** 페이지에서 **iOS 및 Mac OS X** 구성 항목 유형을 선택하고 **다음**을 클릭합니다.  

2.  **지원되는 플랫폼** 페이지에서 모든 iPhone 및 모든 iPad 장치 플랫폼을 선택합니다.  

3.  **장치 설정** 페이지에서 **보안**을 선택하고 **다음**을 클릭합니다.  

4.  **보안** 페이지에서 **카메라** 의 값으로 **허용 안 함**을 선택합니다.  

5.  **비호환 설정 재구성** 을 선택하여 모든 iOS 장치에 변경 내용이 적용되도록 합니다.  

6.  마법사를 완료하여 구성 항목을 만듭니다.  

 이제 [System Center Configuration Manager에서 구성 기준을 만들고 배포하기 위한 일반 작업](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) 항목의 내용을 참조하여, 만든 구성을 디바이스에 쉽게 배포할 수 있습니다.  

## <a name="scenarios-for-android-and-samsung-knox-standard-devices-managed-with-intune"></a>Intune으로 관리되는 Android 및 Samsung KNOX Standard 디바이스에 대한 시나리오  

### <a name="scenario-require-a-password-on-all-android-5-devices"></a>시나리오: 모든 Android 5 디바이스에서 암호 필요  
 이 시나리오에서는 사용자가 자신의 디바이스에서 6자 이상의 암호를 구성하도록 요구하는 Android 5 디바이스에 대한 구성 항목을 만듭니다. 또한 사용자가 잘못된 암호를 5회 입력하면 디바이스가 초기화됩니다.  

1.  구성 항목 만들기 마법사의 **일반** 페이지에서 **Android 및 삼성 KNOX** 구성 항목 유형을 선택하고 **다음**을 클릭합니다.  

2.  설정이 해당 플랫폼에만 적용되도록 **지원되는 플랫폼** 페이지에서 **Android 5**만 선택합니다.  

3.  **장치 설정** 페이지에서 **암호**를 선택하고 **다음**을 클릭합니다.  

4.  **암호** 페이지에서 다음 설정을 구성합니다.  

    -   **장치에 암호 설정 필요** > **필수**  

    -   **최소 암호 길이(문자 수)** > **6**  

    -   **다음 로그온 실패 횟수 후 장치 초기화** > **5**  

5.  마법사를 완료하여 구성 항목을 만듭니다.  

 이제 [구성 기준 만들기 및 배포에 대한 일반 작업](../../compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md) 항목의 내용을 참조하여, 만든 구성을 디바이스에 쉽게 배포할 수 있습니다.  

## <a name="configuration-items-for-devices-managed-with-intune"></a>Intune으로 관리되는 디바이스에 대한 구성 항목

다음 System Center Configuration Manager 구성 항목은 Configuration Manager 클라이언트로 관리되지 않는 디바이스(예: Microsoft Intune에 등록된 디바이스)에 사용할 수 있습니다.  

 -   [Intune으로 Windows 8.1 및 Windows 10 장치에 대한 구성 항목을 만드는 방법](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)  

 -   [Intune으로 관리되는 Windows Phone 장치에 대한 구성 항목을 만드는 방법](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)  

 -   [Intune으로 관리되는 iOS 및 Mac OS X 장치에 대한 구성 항목을 만드는 방법](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)  

 -   [Intune으로 관리되는 Android 및 Samsung KNOX Standard 장치에 대한 구성 항목을 만드는 방법](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)  
