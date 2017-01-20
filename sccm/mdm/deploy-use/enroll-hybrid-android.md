---
title: "System Center Configuration Manager 및 Microsoft Intune으로 Android 하이브리드 장치 관리 설정 | Microsoft 문서"
description: "Configuration Manager 및 Intune으로 Android 모바일 장치 관리 준비"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c517fe34-0130-465b-a020-bdb555878778
caps.latest.revision: 9
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 55c953f312a9fb31e7276dde2fdd59f8183b4e4d
ms.openlocfilehash: ab892174643e7565ad9a74abc4f83f2f152669bd


---
# <a name="set-up-android-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune으로 Android 하이브리드 장치 관리 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 경우 사용자가 Android(Samsung KNOX Standard 포함) 장치를 등록할 수 있는 Google Play에서 Android 회사 포털 앱을 다운로드할 수 있습니다. Android 회사 포털 앱을 사용하여 준수 설정을 관리하고, Android 장치를 초기화 또는 삭제하고, 앱을 배포하고, 소프트웨어 및 하드웨어 인벤토리를 수집할 수 있습니다. Android 회사 포털 앱이 Android 장치에 설치되지 않은 경우 인벤토리 및 준수 설정과 같은 일부 관리 기능을 사용할 수 없지만 Android 장치에 앱을 계속 배포할 수 있습니다.  

## <a name="prepare-to-manage-android-mobile-devices-with-configuration-manager-and-intune"></a>Configuration Manager 및 Intune으로 Android 모바일 장치 관리 준비  
 다음 단계를 수행하면 Configuration Manager에서 Android 장치를 관리할 수 있습니다.  

#### <a name="to-enable-android-enrollment"></a>Android 등록을 사용하려면  

1.  **필수 조건** - 플랫폼에 대한 등록을 설정하려면 먼저 [하이브리드 MDM 설정](setup-hybrid-mdm.md)에서 필수 조건 및 절차를 완료합니다.  

2.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  

3.  **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **Android**를 클릭합니다.  

4.  **Microsoft Intune 구독 속성** 대화 상자에서 **Android** 탭을 선택하고 클릭하여 **Android 등록 사용** 확인란을 선택합니다.  

 설정한 후에는 사용자에게 장치를 등록하는 방법을 알려 주어야 합니다. [장치 등록에 대해 최종 사용자에게 알릴 내용](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)을 참조하세요. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 장치에 적용됩니다.



<!--HONumber=Dec16_HO3-->


