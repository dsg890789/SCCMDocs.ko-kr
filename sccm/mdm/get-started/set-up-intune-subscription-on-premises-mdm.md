---
title: "Intune 구독 설정 | 온-프레미스 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 온-프레미스 모바일 장치 관리에 대한 라이선스를 추적하도록 Microsoft Intune 구독을 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: 8
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 4daf5d6ea30aa1fb4aa189ef6da9b364fe197805


---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager의 온-프레미스 모바일 장치 관리를 위해 Microsoft Intune 구독 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 온\-프레미스 모바일 장치 관리를 사용하려면 Microsoft Intune 구독을 통해 라이선스를 추적해야 합니다. Intune 서비스는 장치를 관리하거나 관리 정보를 저장하는 데 사용되지 않습니다. 온\-프레미스 모바일 장치 관리의 경우 모든 장치 관리가 Configuration Manager 인프라에서 처리됩니다.  

> [!IMPORTANT]  
>  Configuration Manager는 Microsoft Intune과 온-프레미스 Configuration Manager 인프라를 동시에 관리 기관으로 사용할 수 없습니다. 따라서 온-프레미스 관리에 대한 Intune 구독을 설정할 때 Intune 관리를 사용하지 않도록 설정하는 것이 효과적입니다.  

 Intune 서비스가 온\-프레미스 모바일 장치 관리에서 작동하도록 설정하는 작업에는 다음과 같은 개략적인 단계가 포함됩니다.  

-   [Microsoft Intune에 등록](#bkmk_signup)  

-   [Configuration Manager에 Intune 구독 추가](#bkmk_addSub)  

-   [온-프레미스 모바일 장치 관리를 위한 Intune 구독 구성](#bkmk_configure)  

> [!TIP]  
>  온\-프레미스 모바일 장치 관리에 대한 Intune 구독을 먼저 설정한 다음 필수 사이트 시스템 역할을 설치하여 새로 설치된 사이트 시스템 역할이 작동하는 데 필요한 시간을 최소화하는 것이 좋습니다.  

##  <a name="a-namebkmksignupa-sign-up-for-microsoft-intune"></a><a name="bkmk_signup"></a> Microsoft Intune에 등록  
 온\-프레미스 모바일 장치 관리가 작동하려면 Intune이 필요합니다. 평가판 또는 유료 구독을 [등록](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/)하고 다음 단계로 이동하여 Configuration Manager에 구독을 추가하면 됩니다.  

##  <a name="a-namebkmkaddsuba-add-the-intune-subscription-to-configuration-manager"></a><a name="bkmk_addSub"></a> Configuration Manager에 Intune 구독 추가  
 Configuration Manager에 구독을 추가하려면 Intune을 사용하여 모바일 장치 관리에 대한 구독을 추가할 때와 동일한 기본 단계를 따릅니다. 특정 차이점에 대한 아래 참고 내용을 읽은 다음 [System Center Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 장치 관리)](../../mdm/plan-design/hybrid-mobile-device-management.md)에서 [Microsoft Intune 구독을 만들려면](../../mdm/plan-design/hybrid-mobile-device-management.md#bkmk_subscription)의 지침을 따르세요.  

> [!NOTE]  
>  Intune 구독을 추가할 때는 다음 사항에 유의하세요.  
>   
>  -   Microsoft Intune 구독 추가 마법사에서 지정한 컬렉션은 온\-프레미스 모바일 장치 관리 사용자 권한 위임에 사용되지 않습니다. Intune을 사용한 모바일 장치 관리에만 사용됩니다. 그러나 마법사를 진행하려면 컬렉션을 지정해야 합니다.  
> -   마법사에서 지정한 사이트 코드 설정은 온\-프레미스 모바일 장치 관리에 대해 무시됩니다. 사용되는 사이트 코드는 사용자에게 장치를 등록할 수 있는 권한을 부여하는 등록 프로필에 지정하는 코드입니다.  
> -   다단계 인증을 사용하지 마세요. 온\-프레미스 모바일 장치 관리에서 지원되지 않습니다.  

##  <a name="a-namebkmkconfigurea-configure-the-intune-subscription-for-on-premises-mobile-device-management"></a><a name="bkmk_configure"></a> 온-프레미스 모바일 장치 관리를 위한 Intune 구독 구성  

1.  Configuration Manager 콘솔에서 **Microsoft Intune 구독**을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.  

2.  온-프레미스 모바일 장치 관리에 상자에서 **온-프레미스 장치만 관리**옆의 확인란을 클릭하고 **확인**을 클릭합니다.  

    > [!NOTE]  
    >  이 확인란을 클릭하면 모든 온-프레미스 관리 정보가 유지되고 데이터가 클라우드로 복제되지 않도록 Intune 구독을 구성할 수 있습니다.  

3.  Windows 10 모바일 장치를 관리하려면 **Microsoft Intune 구독**을 마우스 오른쪽 단추로 클릭하고, **플랫폼 구성**및  **Windows Phone**을 차례로 클릭합니다.  

4.  **Windows Phone 8.1 및 Windows 10 Mobile**옆의 확인란을 클릭한 다음 **확인**을 클릭합니다.  

5.  Windows 10 데스크톱 컴퓨터를 관리하려면 **Microsoft Intune 구독**을 마우스 오른쪽 단추로 클릭하고, **플랫폼 구성**및 **Windows 등록 사용**을 차례로 클릭합니다.  

6.  **Windows 등록 사용**옆의 확인란을 클릭한 다음 **확인**을 클릭합니다.  



<!--HONumber=Nov16_HO1-->


