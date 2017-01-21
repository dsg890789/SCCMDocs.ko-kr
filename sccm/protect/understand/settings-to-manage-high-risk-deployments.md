---
title: "높은 위험 수준의 배포 관리 | System Center Configuration Manager"
description: "높은 위험 수준의 배포를 만드는 경우 관리자에게 경고하도록 System Center Configuration Manager에서 사이트 설정을 구성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: e265c2de8a1d29863d430e0e2b693c69ff4bda10


---
# <a name="settings-to-manage-high-risk-deployments-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대해 위험 수준이 높은 배포를 관리하기 위한 설정

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager에서는 관리자가 높은 위험 수준의 작업 순서 배포를 만드는 경우 관리자에게 경고하는 사이트 설정을 구성할 수 있습니다. 위험 수준이 높은 배포는 다음과 같습니다.  

-   자동으로 설치되는 배포  

-   예기치 않은 결과가 발생할 가능성이 있는 배포  

 예를 들어 용도가 **필수** 이며 운영 체제를 배포하는 작업 순서는 위험 수준이 높은 것으로 간주됩니다.  

 위험 수준이 높은 불필요한 배포가 수행될 위험을 줄이려는 경우 다음과 같은 배포 확인 설정에서 크기 제한을 구성할 수 있습니다.  

-   **컬렉션 크기 제한**: 배포를 만들 때 클라이언트가 제한보다 많이 포함된 컬렉션을 숨깁니다.  

    -   **기본 크기**: 이 설정은 배포를 만들 때 클라이언트가 제한보다 많이 포함된 컬렉션을 기본적으로 숨깁니다. 이러한 컬렉션은 배포를 만들 때 표시할 수 있지만 기본적으로는 숨겨집니다. 기본값은 100입니다. 이 설정을 무시하려면 값으로 0을 입력합니다.  

    -   **최대 크기**: 이 설정은 배포를 만들 때 클라이언트가 제한보다 많이 포함된 컬렉션을 항상 숨깁니다. 기본값은 0입니다(이 설정이 무시됨). **최대 크기** 값은 **기본 크기** 값보다 커야 합니다.  

     **기본 크기**를 100으로 설정하고 **최대 크기**를 1,000으로 설정하는 경우를 예로 들어 보겠습니다. 위험 수준이 높은 배포를 만들 때 **컬렉션 선택** 창에는 클라이언트 수가 100개 미만인 컬렉션만 표시됩니다. **사이트의 최소 크기 구성보다 많은 멤버 수가 포함된 컬렉션 숨기기** 설정의 선택을 취소하면 1,000개 미만의 클라이언트가 포함된 컬렉션이 창에 표시됩니다.  

-   **사이트 시스템 서버를 사용하는 컬렉션**: 대상 컬렉션에 사이트 시스템 역할을 사용하는 컴퓨터가 포함되어 있으면 배포를 차단하거나 배포를 만들기 전에 확인을 요청합니다. 배포가 차단되면 배포 확인 기준을 충족하는 다른 컬렉션을 선택해야 합니다.  

> [!NOTE]  
>  위험 수준이 높은 배포는 항상 사용자 지정 컬렉션, 직접 작성하는 컬렉션 및 기본적으로 제공되는 **알 수 없는 컴퓨터** 컬렉션으로 제한됩니다. 위험 수준이 높은 배포를 만드는 경우 **모든 시스템**같은 기본 제공 컬렉션을 선택할 수 없습니다.  

### <a name="to-configure-deployment-verification-for-a-site"></a>사이트에 대한 배포 확인을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** >**사이트 구성** > **사이트**를 선택한 다음 구성할 기본 사이트를 선택합니다.  

2.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택한 다음 **배포 확인** 탭을 선택합니다.  

3.  사용하려는 구성을 설정한 후 **확인**을 선택하여 구성을 저장합니다.  

### <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager에 대한 사이트 및 계층 구조 구성](../../core/servers/deploy/configure/configure-sites-and-hierarchies.md)



<!--HONumber=Nov16_HO1-->


