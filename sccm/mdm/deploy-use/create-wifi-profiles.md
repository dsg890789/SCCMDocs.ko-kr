---
title: "System Center Configuration Manager에서 Wi-Fi 프로필 만들기 | Microsoft Docs"
description: "Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 모바일 장치 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c72612d4-0b3d-4e71-b3c9-35782701b78a
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 6c6f56dd2b68b8c87d87842ab2b0f782e16c7f9c
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-create-wi-fi-profiles-for-mobile-devices-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 모바일 장치에 대한 Wi-Fi 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 모바일 장치 사용자에게 무선 네트워크 설정을 배포할 수 있습니다. 이러한 설정을 배포하면 사용자가 더 쉽게 Wi-Fi에 연결할 수 있습니다.  

Wi-Fi 프로필로 다음 모바일 장치 유형을 구성할 수 있습니다.  

-   Windows Phone 8.1을 실행하는 장치  

-   Windows 10 Desktop 또는 Mobile을 실행하는 장치  

-   iOS 5, iOS 6, iOS 7 및 iOS 8을 실행하는 IPhone 장치  

-   iOS 5, iOS 6, iOS 7 및 iOS 8을 실행하는 IPad 장치  

-   버전 4 이상을 실행하는 Android 장치

> [!IMPORTANT]  
>  Android, iOS, Windows Phone 및 등록된 Windows 8.1 이상 장치에 프로필을 배포하려면 이러한 장치를 Microsoft Intune에 등록해야 합니다. 장치를 등록하는 방법은 [Intune에서 관리할 장치 등록](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)을 참조하세요.  

[Wi-Fi 프로필 만들기](../../protect/deploy-use/create-wifi-profiles.md#create-a-wi-fi-profile)에서는 Configuration Manager의 Wi-Fi 프로필을 사용하여 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다.

Wi-Fi 프로필 배포에 대한 자세한 내용은 [Wi-Fi, VPN, 메일 및 인증서 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)를 참조하세요.

