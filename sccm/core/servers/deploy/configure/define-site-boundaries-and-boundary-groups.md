---
title: 경계 및 경계 그룹 사용
titleSuffix: Configuration Manager
description: 경계 및 경계 그룹을 사용하여 관리하는 디바이스에 대한 네트워크 위치 및 액세스 가능한 사이트 시스템을 정의합니다.
ms.date: 06/18/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 54aa20d5-791e-4416-9db4-5aaea472c0b7
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d160c6ab64c5ad097bf5986882b65171b0df4651
ms.sourcegitcommit: 60d45a5df135b84146f6cfea2bac7fd4921d0469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67194152"
---
# <a name="define-site-boundaries-and-boundary-groups"></a>사이트 경계 및 경계 그룹 정의

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 ‘경계’는 인트라넷의 네트워크 위치를 정의합니다.  이러한 위치로는 관리할 디바이스를 들 수 있습니다. ‘경계 그룹’은 구성하는 경계의 논리적 그룹입니다. 

계층 구조에 임의의 수의 경계 그룹이 포함될 수 있고, 각 경계 그룹에는 다음 경계 유형이 임의로 조합되어 포함될 수 있습니다.  

- IP 서브넷  
- Active Directory 사이트 이름  
- IPv6 접두사  
- IP 주소 범위  

인트라넷의 클라이언트는 현재 네트워크 위치를 평가한 다음 해당 정보를 사용하여 자신이 속한 경계 그룹을 식별합니다.  

클라이언트는 경계 그룹을 사용하여 다음 작업을 수행합니다.  

- **할당된 사이트 찾기:** 경계 그룹을 통해 클라이언트가 클라이언트 할당을 위한 기본 사이트를 찾을 수 있습니다. 이 동작을 ‘자동 사이트 할당’이라고도 합니다.   

- **클라이언트가 사용할 수 있는 특정 사이트 시스템 역할 찾기:** 경계 그룹을 특정 사이트 시스템 역할과 연결합니다. 그러면 사이트에서 클라이언트에 경계 그룹의 사이트 시스템 목록을 제공합니다. 클라이언트는 이러한 사이트 시스템을 콘텐츠나 근처 관리 지점 찾기와 같은 작업에 사용합니다.  

인터넷에 있거나 인터넷 전용 클라이언트로 구성된 클라이언트는 경계 정보를 사용하지 않습니다. 이러한 클라이언트는 자동 사이트 할당을 사용할 수 없고, 할당된 사이트의 인터넷 기반 배포 지점이나 클라우드 기반 배포 지점에서 콘텐츠를 다운로드할 수 있습니다.  

1902 버전부터 CMG(클라우드 관리 게이트웨이)를 경계 그룹과 연결할 수 있습니다. 자세한 내용은 [CMG 계층 구조 디자인](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#hierarchy-design)을 참조하세요.<!--3640932-->


## <a name="BKMK_BoundaryBestPractices"></a> 권장 사항

### <a name="use-a-mix-of-the-fewest-boundaries-that-meet-your-needs"></a>요구에 맞는 가장 적은 수의 경계를 혼합하여 사용합니다.

환경에서 작동하는 경계 유형이면 어느 것이든 사용합니다. 관리 작업을 간소화하려면 가장 적은 수의 경계를 사용할 수 있는 경계 유형을 사용합니다.

### <a name="avoid-overlapping-boundaries-for-automatic-site-assignment"></a>자동 사이트 할당의 경우 경계가 겹치면 안 됨

각 경계 그룹에서 사이트 할당과 사이트 시스템 참조를 모두 지원하지만 사이트 할당에만 사용할 경계 그룹 세트를 별도로 만듭니다. 경계 그룹의 각 경계는 다른 사이트 할당을 포함하는 다른 경계 그룹의 구성원이 아니어야 합니다.

- 단일 경계를 여러 경계 그룹에 포함할 수 있습니다.  

- 사이트 할당을 위해 각 경계 그룹을 다른 기본 사이트와 연결할 수 있습니다.  

- 다른 사이트 할당을 포함하는 다른 두 경계 그룹의 구성원인 경계의 경우 클라이언트는 조인할 사이트를 임의로 선택합니다. 이 동작은 클라이언트가 조인할 사이트에는 사용할 수 없습니다. 이러한 구성을 ‘겹치는 경계’라고 합니다.   

    겹치는 경계는 콘텐츠 위치와 관련해서는 문제가 되지 않으며, 사용할 수 있는 추가 리소스나 콘텐츠 위치를 클라이언트에 제공하는 유용한 구성일 수 있습니다.  


## <a name="next-steps"></a>다음 단계

- [네트워크 위치를 경계로 정의](/sccm/core/servers/deploy/configure/boundaries)

- [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups)
