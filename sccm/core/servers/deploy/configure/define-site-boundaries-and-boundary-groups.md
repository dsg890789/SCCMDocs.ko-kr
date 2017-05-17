---
title: "경계 및 경계 그룹 사용 | Microsoft 문서"
description: "경계 및 경계 그룹을 사용하여 관리하는 장치에 대한 네트워크 위치 및 액세스 가능한 사이트 시스템을 정의합니다."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54aa20d5-791e-4416-9db4-5aaea472c0b7
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 0fea1dece0768a2b7bcd3fcedc2288ea2d52e73d
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017


---
# <a name="define-site-boundaries-and-boundary-groups-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 사이트 경계 및 경계 그룹 정의

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 경계는 관리하려는 장치를 포함할 수 있는 인트라넷의 네트워크 위치를 정의합니다. 경계 그룹은 구성하는 경계의 논리적 그룹입니다.

 계층 구조는 경계 그룹을 원하는 개수만큼 포함할 수 있으며, 각 경계 그룹은 다음 경계 유형의 모든 조합을 포함할 수 있습니다.  

-   IP 서브넷  
-   Active Directory 사이트 이름  
-   IPv6 접두사  
-   IP 주소 범위  

인트라넷의 클라이언트는 현재 네트워크 위치를 평가한 다음 해당 정보를 사용하여 자신이 속한 경계 그룹을 식별합니다.  

 클라이언트는 경계 그룹을 사용하여 다음 작업을 수행합니다.  
-   **할당된 사이트 찾기:** 클라이언트는 경계 그룹을 통해 클라이언트 할당(자동 사이트 할당)을 위한 기본 사이트를 찾을 수 있습니다.  
-   **클라이언트가 사용할 수 있는 특정 사이트 시스템 역할 찾기:** 특정 사이트 시스템 역할과 연결하는 경계 그룹은 콘텐츠를 찾는 동안, 그리고 기본 관리 지점으로 사용할 수 있도록 사이트 시스템 목록을 클라이언트에 제공합니다.  

인터넷에 있거나 인터넷 전용 클라이언트로 구성된 클라이언트는 경계 정보를 사용하지 않습니다. 이러한 클라이언트는 자동 사이트 할당을 사용할 수 없고, 배포 지점이 인터넷에서 클라이언트 연결을 허용하도록 구성된 경우 항상 할당된 사이트의 배포 지점에서 콘텐츠를 다운로드할 수 있습니다.  

**시작하려면:**
- 먼저 [네트워크 위치를 경계로 정의](/sccm/core/servers/deploy/configure/boundaries)합니다.
- 그런 다음 계속해서 [경계 그룹을 구성](/sccm/core/servers/deploy/configure/boundary-groups)하여 해당 경계에 있는 클라이언트를 사용 가능한 사이트 시스템 서버에 연결합니다.



##  <a name="BKMK_BoundaryBestPractices"></a> 경계 및 경계 그룹에 대한 모범 사례  

-   **요구에 맞는 가장 적은 경계의 혼합을 사용합니다.**  
   이전에는 다른 경계 유형보다 특정 경계 유형을 사용하도록 권장했습니다. 성능 향상을 위한 변경 내용이 도입되었으므로 이제 사용자 환경에 맞고 변경 내용으로 관리 작업을 단순화하기 위해 최대한 적은 개수의 경계를 사용할 수 있는 선택한 경계 유형을 사용하는 것이 좋습니다.      

-   **자동 사이트 할당에 대해 겹치는 경계를 사용해서는 안 됩니다.**  
     각 경계 그룹은 사이트 할당 구성과 콘텐츠 위치용 구성을 모두 지원하지만 사이트 할당에만 사용할 별도의 경계 그룹 집합을 만드는 것이 좋습니다. 경계 그룹의 각 경계는 다른 사이트 할당을 포함하는 다른 경계 그룹의 구성원이 아닙니다. 그 이유는 다음과 같습니다.  

    -   단일 경계를 여러 경계 그룹에 포함할 수 있습니다.  

    -   사이트 할당을 위해 각 경계 그룹을 다른 기본 사이트와 연결할 수 있습니다.  

    -   다른 사이트 할당을 포함하는 서로 다른 두 경계 그룹의 구성원인 경계의 클라이언트는 연결할 사이트를 임의로 선택하는데 이 사이트는 클라이언트가 연결하도록 할 사이트가 아닐 수 있습니다.  이러한 구성을 겹치는 경계라고 합니다.  

     겹치는 경계는 콘텐츠 위치 측면에서는 문제가 되지 않으며 클라이언트가 사용할 수 있는 리소스 또는 콘텐츠 위치를 추가로 제공하는 적절한 구성인 경우가 많습니다.  

