---
title: Intune 구독 설정
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 모바일 장치 관리에 대 한 라이선스를 추적 하려면 Intune 구독 설정
ms.date: 03/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: aff4fcc67325645387aea1e57354321769a515ca
ms.sourcegitcommit: f3dd8405018fe1043434386be15c16752c1a4a3c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/07/2019
ms.locfileid: "57558068"
---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 Microsoft Intune 구독 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 온-프레미스 모바일 장치 관리 (MDM) 라이선스를 추적 하려면 Microsoft Intune 구독이 필요 합니다. Intune 서비스는 장치를 관리 하거나 관리 정보를 저장을 사용 하지 않습니다. 온-프레미스 MDM에 대 한 모든 장치 관리는 Configuration Manager 인프라에 의해 처리 됩니다.  

온-프레미스 MDM에 대 한 필수 사이트 시스템 역할을 설치 하기 전에 Intune 구독을 설정 합니다. 이 동작은 새로 설치 된 사이트 시스템 역할이 작동 하는 데 필요한 시간을 최소화 합니다.  

> [!Note]  
> 1810 버전부터 Intune 연결을 새 온-프레미스 MDM 배포에 필요 하지 않습니다.<!--3607730, fka 1359124--> 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 현재 기존 온-프레미스 MDM 배포에서 Intune 연결을 제거할 수 없습니다. 자세한 내용은 [Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)을 참조하세요.  



##  <a name="sign-up-for-microsoft-intune"></a>Microsoft Intune에 등록  

Intune은 온-프레미스 MDM을 작동할 수 있도록 해야 합니다. [등록](https://docs.microsoft.com/intune/free-trial-sign-up) 평가판 또는 유료 구독에 대 한 합니다. Configuration Manager에 구독을 추가 하려면 다음 단계를 이동 합니다.  



##  <a name="add-the-intune-subscription-to-configuration-manager"></a>Configuration Manager에 Intune 구독 추가  

구독을 Configuration Manager에 추가 하려면 Intune와 함께 하이브리드 MDM에 대 한 구독을 추가할 때와 동일한 기본 단계를 따릅니다. 특정 차이점에 대한 아래의 참고를 읽은 다음 [Intune 구독 구성](/sccm/mdm/deploy-use/configure-intune-subscription)의 지침을 사용합니다.  

> [!NOTE]
>  Intune 구독에 추가 하는 경우 아래의 참고 사항에 유의 해야 합니다.  
> 
> - Microsoft Intune 구독 추가 마법사에서 지정한 컬렉션은 온-프레미스 MDM 사용자 권한 위임에 대 한 사용 되지 않습니다. Intune 사용한 모바일 장치 관리에만 사용 됩니다. 그러나 마법사를 진행 하려면 컬렉션을 지정 해야 하 고 있습니다.  
> 
> - 온-프레미스 MDM.에 대 한 마법사에서 지정한 사이트 코드는 무시 됩니다. 등록에서 지정 하는 사이트 코드를 사용 하 여 사용자가 장치를 등록 하는 권한을 부여 하는 프로필입니다.  
> 
> - Multi-factor authentication을 사용 하지 마십시오. 온-프레미스 MDM.에서 지원 되지 않습니다.  



##  <a name="configure-the-intune-subscription-for-on-premises-mdm"></a>온-프레미스 MDM에 대 한 Intune 구독 구성  

1. Configuration Manager 콘솔에서로 이동 합니다 **관리** 작업 영역에서 확장 **Cloud Services**, 선택는 **Microsoft Intune 구독** 노드. 구독을 선택 하 고 선택한 **속성** 리본 메뉴에 있습니다.   

    1. 프레미스 모바일 장치 관리 섹션의 맨 아래에 **일반** 페이지에서 다음 옵션 중 하나를 선택 합니다.

        - 관리 되는 온-프레미스 장치만 포함 하려는 경우이 옵션을 선택 **만 온-프레미스 장치를 관리할**합니다.  

            > [!NOTE]  
            > 이 옵션을 사용 하도록 설정 하면 모든 온-프레미스 관리 정보가 유지 하려면 Intune 구독을 구성 합니다. 장치 관리 데이터가 클라우드로 복제 됩니다.  

        - Intune 및 Configuration Manager 온-프레미스에서 관리 하는 장치를 보유 하려는 경우이 옵션을 구성 하지 마세요.  

    선택 **확인** 구독 속성을 닫습니다.

2. Windows 10 Mobile 장치를 관리 하려는 경우 선택 목록에서 구독을 선택 **플랫폼 구성** 에서 리본 메뉴를 선택 합니다 **Windows Phone**합니다.  

    1. 에 대 한 옵션을 선택 **Windows Phone 8.1 및 Windows 10 Mobile**를 선택한 후 **확인**합니다.  

3. Windows 10 데스크톱 컴퓨터를 관리 하려는 경우 선택 목록에서 구독을 선택 **플랫폼 구성** 에서 리본 메뉴를 선택 합니다 **Windows**합니다.  

    1. 옵션을 선택 **을 사용 하도록 설정 하는 Windows 등록**를 선택한 후 **확인**합니다.  

