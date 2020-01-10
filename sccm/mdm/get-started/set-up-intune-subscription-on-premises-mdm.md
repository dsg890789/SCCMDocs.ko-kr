---
title: Intune 구독 설정
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 모바일 장치 관리에 대 한 라이선스를 추적 하도록 Intune 구독 설정
ms.date: 03/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1f90b4088f066132e61d7dd60e3fe259eb945f96
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821616"
---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 Microsoft Intune 구독 설정

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하려면 라이선스를 추적 하기 위한 Microsoft Intune 구독이 필요 합니다. Intune 서비스는 장치를 관리 하거나 관리 정보를 저장 하는 데 사용 되지 않습니다. 온-프레미스 MDM의 경우 모든 장치 관리가 Configuration Manager 인프라에 의해 처리 됩니다.  

온-프레미스 MDM에 필요한 사이트 시스템 역할을 설치 하기 전에 Intune 구독을 설정 합니다. 이 작업은 새로 설치 된 사이트 시스템 역할이 작동 하는 데 필요한 시간을 최소화 합니다.  

> [!Note]  
> 버전 1810부터는 Intune 연결이 새로운 온-프레미스 MDM 배포에 더 이상 필요하지 않습니다.<!--3607730, fka 1359124--> 조직에서 이 기능을 사용하려면 여전히 Intune 라이선스가 필요합니다. 현재 기존 온-프레미스 MDM 배포에서 Intune 연결을 제거할 수 없습니다. 자세한 내용은 [Intune 지원 블로그 게시물](https://techcommunity.microsoft.com/t5/Intune-Customer-Success/Move-from-Hybrid-Mobile-Device-Management-to-Intune-on-Azure/ba-p/280150)을 참조하세요.  



##  <a name="sign-up-for-microsoft-intune"></a>Microsoft Intune에 등록  

Intune은 온-프레미스 MDM 기능을 수행 하는 데 필요 합니다. 평가판 또는 유료 구독에 [등록](https://docs.microsoft.com/intune/free-trial-sign-up) 합니다. 그런 다음 Configuration Manager에 구독을 추가 하려면 다음 단계로 이동 합니다.  



##  <a name="add-the-intune-subscription-to-configuration-manager"></a>Configuration Manager에 Intune 구독 추가  

Configuration Manager에 구독을 추가 하려면 Intune을 사용 하 여 하이브리드 MDM에 대 한 구독을 추가할 때와 동일한 기본 단계를 따릅니다. 특정 차이점에 대한 아래의 참고를 읽은 다음 [Intune 구독 구성](/sccm/mdm/deploy-use/configure-intune-subscription)의 지침을 사용합니다.  

> [!NOTE]
>  Intune 구독을 추가할 때 다음 사항에 유의 하세요.  
> 
> - Microsoft Intune 구독 추가 마법사에서 지정한 컬렉션은 온-프레미스 MDM 사용자 권한 위임에 사용 되지 않습니다. Intune을 사용한 모바일 장치 관리에만 사용 됩니다. 그러나 마법사를 진행 하려면 컬렉션을 지정 해야 합니다.  
> 
> - 마법사에서 지정한 사이트 코드는 온-프레미스 MDM에 대해 무시 됩니다. 사용자에 게 장치를 등록할 수 있는 권한을 부여 하는 등록 프로필에서 지정한 사이트 코드를 사용 합니다.  
> 
> - Multi-factor authentication을 사용 하지 않습니다. 온-프레미스 MDM에서는 지원 되지 않습니다.  



##  <a name="configure-the-intune-subscription-for-on-premises-mdm"></a>온-프레미스 MDM에 대 한 Intune 구독 구성  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동 하 여 **Cloud Services**를 확장 하 고 **Microsoft Intune 구독** 노드를 선택 합니다. 구독을 선택한 다음 리본에서 **속성** 을 선택 합니다.   

    1. **일반** 페이지의 맨 아래에 있는 온-프레미스 모바일 장치 관리 섹션에서 다음 옵션 중 하나를 선택 합니다.

        - 장치가 온-프레미스에서 관리 되는 경우에만 온 **-프레미스 장치를 관리**하는 옵션을 선택 합니다.  

            > [!NOTE]  
            > 이 옵션을 사용 하도록 설정 하는 경우 모든 관리 정보를 온-프레미스로 유지 하도록 Intune 구독을 구성 합니다. 장치 관리 데이터가 클라우드에 복제 되지 않습니다.  

        - Intune과 Configuration Manager 온-프레미스 모두에서 장치를 관리 하려는 경우이 옵션을 구성 하지 마십시오.  

    **확인** 을 선택 하 여 구독 속성을 닫습니다.

2. Windows 10 모바일 장치를 관리 하려는 경우 목록에서 구독을 선택 하 고 리본 메뉴에서 **플랫폼 구성** 을 선택한 다음 **Windows Phone**를 선택 합니다.  

    1. **Windows Phone 8.1 및 Windows 10 Mobile**에 대 한 옵션을 선택한 다음 **확인**을 선택 합니다.  

3. Windows 10 데스크톱 컴퓨터를 관리 하려면 목록에서 구독을 선택 하 고 리본 메뉴에서 **플랫폼 구성** 을 선택한 다음 **Windows**를 선택 합니다.  

    1. **Windows 등록을 사용 하도록 설정**하는 옵션을 선택한 다음 **확인**을 선택 합니다.  

