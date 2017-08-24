---
title: "System Center Configuration Manager 및 Microsoft Intune으로 Android 하이브리드 장치 관리 설정 | Microsoft 문서"
description: "Configuration Manager 및 Intune으로 Android 모바일 장치 관리 준비"
ms.custom: na
ms.date: 08/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: "9"
caps.handback.revision: "0"
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 53ecc86ecc000e0ab9e81f683e8e8171e9a66f35
ms.sourcegitcommit: 9a6f8e028fb5eb2e752da70f42a5b548339bd8f4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/14/2017
---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune으로 Android 하이브리드 장치 관리 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서 관리자는 Android 및 Android for Work 장치의 하이브리드 등록을 사용하도록 설정할 수 있습니다. 그런 다음 IT 관리자는 System Center Configuration Manger를 사용하여 구성된 Microsoft Intune 구독을 통해 장치를 관리할 수 있습니다. Google Play에서 사용자는 Android(Samsung KNOX Standard 포함) 및 Android for Work 장치를 등록할 수 있는 Android 회사 포털 앱을 다운로드할 수 있습니다.

Configuration Manager 관리자는 준수 설정을 관리하고, Android 장치를 초기화 또는 삭제하고, 앱을 배포하고, 소프트웨어 및 하드웨어 인벤토리를 수집할 수 있습니다. Android 회사 포털 앱이 Android 장치에 설치되지 않은 경우 인벤토리 및 준수 설정과 같은 일부 관리 기능을 사용할 수 없지만 Android 장치에 앱을 계속 배포할 수 있습니다.  

## <a name="enable-android-enrollment"></a>Android 등록 사용  
다음 단계를 수행하면 Configuration Manager가 회사 프로필 없이 Android 장치를 관리할 수 있습니다("클래식 Android" 등록).

1. 플랫폼에 대한 등록을 설정하려면 먼저 [하이브리드 MDM 설정](setup-hybrid-mdm.md)에서 필수 조건 및 절차를 완료합니다.  
2. Configuration Manager 콘솔의 **관리** 작업 영역에서 **개요** > **Cloud Services** > **Microsoft Intune 구독**을 선택하고 Intune 구독을 선택합니다.  
3. **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **Android**를 선택합니다.  
4. **Microsoft Intune 구독 속성** 대화 상자에서 **Android** 탭을 선택하고 **Android 등록 사용** 확인란을 선택합니다. **개인적으로 소유한 장치 차단**을 선택하여 [미리 선언된 장치](predeclare-devices-with-hardware-id.md)에 대한 등록을 제한할 수 있습니다.

 설정한 후에는 사용자에게 장치를 등록하는 방법을 알려 주어야 합니다. [장치 등록에 대해 최종 사용자에게 알릴 내용](https://docs.microsoft.com/intune/end-user-educate)을 참조하세요. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 장치에 적용됩니다.

## <a name="enable-android-for-work-enrollment"></a>Android for Work 등록 사용
다음 단계를 수행하면 Configuration Manager에서 회사 프로필을 사용하여 Android 장치를 관리할 수 있습니다.

1. https://accounts.google.com/SignUp에서 Google 계정을 만들어 Android for Work 관리자 계정으로 사용합니다. 또는 이 Intune 테넌트에 대해 모든 Android for Work 관리 작업과 연결되는 계정으로 로그인합니다. 이 계정은 Android 장치를 관리하는 관리자 간에 공유되는 Google 계정일 수 있습니다. 또한 조직이 Play for Work 콘솔에서 앱을 관리하고 게시하는 데 사용하는 Google 계정입니다. 이 계정을 사용하여 Play for Work 스토어에서 앱을 승인하므로 계정 이름과 암호를 추적합니다.
2. Configuration Manager에서 관리되는 Intune 테넌트에 Google 계정을 바인딩하여 Android 등록을 사용하도록 설정합니다.
   1. Configuration Manager 콘솔의 **관리** 작업 영역에서 **개요** > **Cloud Services** > **Microsoft Intune 구독**을 선택하고 Intune 구독을 선택합니다.
   2. **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **Android for Work**를 선택합니다.
   3. 대화 상자에서 **Intune 콘솔에서 Android for Work 구성**을 선택합니다. Intune 콘솔이 웹 브라우저에서 열립니다.
   4. Intune 관리자 자격 증명을 사용하여 Intune 포털에 로그인합니다.
   5. **구성**을 선택하여 Google Play의 Android for Work 웹 사이트를 엽니다.
   6. Google의 로그인 페이지에서 1단계의 Google 계정 자격 증명을 입력한 다음 회사 정보를 제공합니다.
3. Intune 포털로 돌아오면 Android for Work이 사용되며, Android for Work 장치에 대한 세 가지 등록 옵션이 있습니다.
   - **Manage all devices as Android**(Android로 모든 장치 관리)(사용 안 함). Android for Work를 지원하는 장치를 포함하여 모든 Android 장치가 기존 Android 장치로 등록됩니다.
   - **Manage supported devices as Android for Work**(지원되는 장치를 Android for Work로 관리)(사용). Android for Work를 지원하는 모든 장치가 Android for Work 장치로 등록됩니다. Android for Work를 지원하지 않는 Android 장치는 기존 Android 장치로 등록됩니다.
   - **Manage supported devices for users only in these groups as Android for Work**(이러한 그룹의 사용자에 대해서만 지원되는 장치를 Android for Work로 관리)(일부 그룹에 대해서만 사용). Android for Work 관리 대상을 제한된 사용자 집합으로 지정할 수 있습니다. Android for Work를 지원하는 장치는 선택된 그룹의 구성원이 등록하는 경우에만 Android for Work 장치로 등록됩니다. 다른 모든 장치는 Android 장치로 등록됩니다.

> [!NOTE]
> 알려진 문제로 인해 **Manage supported devices for users only in these groups as Android for Work**(이 그룹의 사용자만을 위해 지원되는 장치를 Android for Work로 관리) 옵션이 제대로 작동되지 않습니다. 지정된 Azure AD 그룹의 사용자 장치가 Android for Work 대신 Android로 등록됩니다. Android for Work를 사용하도록 설정하려면 **Manage all supported devices as Android for Work**(지원되는 장치를 모두 Android for Work로 관리) 옵션을 사용해야 합니다.


설정한 후에는 사용자에게 장치를 등록하는 방법을 알려 주어야 합니다. [장치 등록에 대해 최종 사용자에게 알릴 내용](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)을 참조하세요. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 장치에 적용됩니다.

바인딩이 완료되면 계정 이름 및 조직 이름이 Intune 포털에 표시됩니다. 그러면 두 브라우저를 닫아도 됩니다.

### <a name="enroll-an-android-for-work-device"></a>Android for Work 장치 등록
사용자가 Android for Work 장치를 등록하는 방법은 Android 등록과 비슷합니다. 사용자는 모바일 장치에서 Android용 회사 포털 앱을 다운로드하여 설치할 수 있습니다. 앱에서 등록 프로세스의 일부로 회사 프로필을 만들라는 메시지를 표시합니다. 회사 프로필을 만든 후 사용자는 관리되는 버전의 회사 포털로 전환해야 합니다. 관리되는 회사 포털은 오른쪽 아래에 작은 주황색 서류 가방이 태그로 지정되어 있습니다.

### <a name="manage-android-for-work-devices"></a>Android for Work 장치 관리
Android for Work 등록을 사용하도록 설정한 후 Android for Work 장치에 대한 다음 관리 작업을 수행할 수 있습니다.
- [앱 승인](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [구성 항목 만들기](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [준수 설정 관리](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client)
- [메일 프로필 관리](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [회사 프로필 선택적 초기화](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)

> [!div class="button"]
[< 이전 단계](create-service-connection-point.md)  [다음 단계 >](set-up-additional-management.md)
