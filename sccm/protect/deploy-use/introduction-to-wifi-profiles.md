---
title: "Wi-Fi 프로필 소개 | System Center Configuration Manager"
description: "System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 86725460-c2f3-49ed-90aa-6b2724d34d69
caps.latest.revision: 8
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 30fefb291a6fccb630d5e3272ce7266339c9139c


---
# <a name="introduction-to-wi-fi-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 Wi-Fi 프로필 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포할 수 있습니다. 이러한 설정을 배포하여 최종 사용자가 무선 네트워크에 연결하는 데 필요한 노력을 최소화할 수 있습니다.  

 예를 들어 **Contoso Wi-Fi**라는 새 Wi-Fi 네트워크를 설치했습니다. 이제 이 네트워크에 연결하는 데 필요한 설정을 사용하여 iOS 운영 체제를 실행하는 모든 장치를 프로비전하려고 합니다. **Contoso Wi-Fi** 무선 네트워크에 연결하는 데 필요한 설정이 포함된 Wi-Fi 프로필을 만들 수 있습니다. 그런 다음 계층 구조에서 iOS를 실행하는 장치를 보유한 모든 사용자에게 이 프로필을 배포할 수 있습니다. iOS 장치의 사용자는 무선 네트워크 목록에서 회사 네트워크를 볼 수 있으며 이 네트워크에 쉽게 연결할 수 있습니다.  

 Wi-Fi 프로필로 다음 장치 유형을 구성할 수 있습니다.  

-   Windows 8.1 32비트를 실행하는 장치  

-   Windows 8.1 64비트를 실행하는 장치  

-   Windows RT 8.1을 실행하는 장치  

-   Windows Phone 8.1을 실행하는 장치  

-   Windows 10 Desktop 또는 Mobile을 실행하는 장치  

-   iOS 5, iOS 6, iOS 7 및 iOS 8을 실행하는 IPhone 장치  

-   iOS 5, iOS 6, iOS 7 및 iOS 8을 실행하는 IPad 장치  

-   버전 4를 실행하는 Android 장치  

> [!IMPORTANT]  
>  Android, iOS, Windows Phone 및 등록된 Windows 8.1 장치에 프로필을 배포하려면 이러한 장치를 Microsoft Intune에 등록해야 합니다. 장치를 등록하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 모바일 장치 관리](https://technet.microsoft.com/library/dn646962.aspx)를 참조하세요.  

 Wi-Fi 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 여기에는 Configuration Manager 인증서 프로필을 사용하여 프로비전했던 서버 유효성 검사 및 클라이언트 인증용 인증서가 포함됩니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  



<!--HONumber=Nov16_HO1-->


