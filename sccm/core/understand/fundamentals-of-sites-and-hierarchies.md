---
title: "사이트 및 계층 구조에 대한 기본 사항 | System Center Configuration Manager"
description: "System Center Configuration Manager 사이트 및 계층 구조에 대한 기본 정보를 가져옵니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 07e10ead8d4b147a4a96b1e5189597e1ac4d4f52


---
# <a name="fundamentals-of-sites-and-hierarchies-for-system-center-configuration-manager"></a>System Center Configuration Manager의 사이트 및 계층 구조에 대한 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 배포는 Active Directory 도메인에 설치해야 하며, 사이트 계층을 형성하는 하나 이상의 Configuration Manager 사이트의 기본 사항이 있습니다. 단일 사이트에서 여러 사이트 계층에 이르기까지, 설치하는 사이트 유형과 위치에 따라 필요한 경우 배포 범위를 확장하고, 관리되는 사용자와 장치에 대한 중요 서비스를 제공할 수 있습니다.

## <a name="hierarchies-of-sites"></a>사이트의 계층 구조
처음으로 System Center Configuration Manager를 설치하는 경우 설치하는 첫 번째 Configuration Manager 사이트에 따라 기업의 장치 및 사용자를 관리하는 기반인 계층의 범위가 결정됩니다. 첫 번째 사이트는 중앙 관리 사이트나 독립 실행형 기본 사이트여야 합니다.  

 **중앙 관리 사이트**는 대규모 배포에 적합하며 글로벌 네트워크 인프라를 통해 배포되는 장치를 지원할 수 있는 유연성과 중앙 관리 지점을 제공합니다. 중앙 관리 사이트를 설치한 후 하나 이상의 기본 사이트를 자식 사이트로 설치해야 합니다.  중앙 관리 사이트에서 기본 사이트의 기능인 장치의 관리를 직접 지원하지 않기 때문입니다. 중앙 관리 사이트는 장치를 직접 관리하고 장치가 지리적으로 서로 다른 위치에 있는 경우 네트워크 대역폭을 제어하는 데 사용하는 자식 기본 사이트를 여러 개 지원합니다.  

 **독립 실행형 기본 사이트**는 소규모 배포에 적합하며, 추가 사이트를 설치할 필요 없이 장치를 관리하는 데 사용할 수 있습니다. 독립 실행형 기본 사이트에서 배포의 크기를 제한할 수 있지만, 새 중앙 관리 사이트를 설치하여 나중에 계층을 확장하는 시나리오를 지원합니다. 이 사이트 확장 시나리오를 통해 독립 실행형 기본 사이트는 자식 기본 사이트가 되며 새 중앙 관리 사이트 아래에 추가 자식 기본 사이트를 설치할 수 있습니다.  그런 후 향후 기업의 성장을 대비하여 초기 배포를 확장할 수 있습니다.  

> [!TIP]  
>  독립 실행형 기본 사이트와 자식 기본 사이트는 실제로 기본 사이트의 사이트 유형과 동일합니다. 이름의 차이는 중앙 관리 사이트도 사용할 때 생성되는 계층 구조 관계를 기반으로 합니다.  이 계층 구조 관계는 Configuration Manager 기능을 확장하는 특정 사이트 시스템 역할의 설치를 제한할 수도 있습니다. 특정 사이트 시스템 역할은 계층 구조의 최상위 계층 사이트인 중앙 관리 사이트 또는 독립 실행형 기본 사이트에만 설치할 수 있기 때문입니다.  

 첫 번째 사이트를 설치한 후 추가 사이트를 설치할 수 있습니다.  첫 번째 사이트가 중앙 관리 사이트인 경우 하나 이상의 자식 기본 사이트를 설치할 수 있습니다.  기본 사이트(독립 실행형 또는 자식 기본)를 설치한 후 하나 이상의 보조 사이트를 설치할 수 있습니다.  

 **보조 사이트** 는 기본 사이트 아래의 자식 사이트로만 설치할 수 있습니다. 이 사이트 유형은 기본 사이트의 도달 범위를 확장하여 기본 사이트에 대한 네트워크 연결이 느린 위치에서 장치를 관리할 수 있습니다.   보조 사이트가 기본 사이트를 확장하지만 클라이언트는 여전히 기본 사이트에서 관리됩니다. 보조 사이트는 네트워크에 걸쳐 클라이언트에에 보내는(배포하는) 정보와 클라이언트에서 사이트에 다시 보내는 정보를 압축한 후 해당 정보의 전송을 관리하여 원격 위치의 장치에 대한 지원을 제공합니다.  

 다음 다이어그램은 사이트 디자인의 몇 가지 예를 보여 줍니다.  

 ![계층 구조 예](media/Hierarchy_examples.png)  

 자세한 내용은 다음 항목을 참조하세요.  

-   [System Center Configuration Manager 소개](../../core/understand/introduction.md)  

-   [System Center Configuration Manager에 대한 사이트 계층 구조 디자인](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)  

-   [System Center Configuration Manager 사이트 설치](/sccm/core/servers/deploy/install/installing-sites)  

## <a name="site-system-servers-and-site-system-roles"></a>사이트 시스템 서버 및 사이트 시스템 역할  
 각 Configuration Manager 사이트에서 관리 작업을 지원하는 **사이트 시스템 역할**을 설치합니다.  **사이트 서버** 역할(사이트를 설치하는 컴퓨터에 할당됨) 및 사이트 데이터베이스 서버 역할(사이트 데이터베이스를 호스트하는 SQL Server에 할당됨)과 같은 일부 역할은 기본적으로 사이트를 설치할 때 설치됩니다. 다른 사이트 시스템 역할은 선택 사항이며, 사이트 시스템 역할이 활성화하는 기능을 사용하려는 경우에만 사용됩니다.  사이트 시스템 역할을 호스트하는 모든 컴퓨터를 사이트 시스템 서버라고 합니다.  

 더 작은 규모의 Configuration Manager 배포의 경우 처음에 사이트 서버 컴퓨터에서 직접 사이트 시스템 역할을 모두 실행할 수 있습니다. 관리되는 환경을 확장해야 하는 경우 보다 많은 장치에 서비스를 제공한다는 측면에서 사이트 효율성을 개선하기 위해 추가 사이트 시스템 역할을 호스트할 사이트 시스템 서버를 추가로 설치할 수 있습니다.  

 다른 사이트 시스템 역할에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles)에서 [사이트 시스템 역할](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)을 참조하세요.  

## <a name="publishing-site-information-to-active-directory-domain-services"></a>Active Directory Domain Services에 사이트 정보 게시  
 Configuration Manager의 관리를 간소화하려면 Configuration Manager에서 사용하는 세부 정보를 지원하도록 Active Directory 스키마를 확장한 후 사이트를 통해 AD DS(Active Directory Domain Services)에 키 정보를 게시할 수 있습니다. 이렇게 하면 관리하려는 컴퓨터가 AD DS의 신뢰할 수 있는 원본에서 사이트 관련 정보를 안전하게 검색할 수 있습니다. 정보 클라이언트는 사용 가능한 사이트, 사이트 시스템 서버 및 해당 사이트 시스템 서버에서 제공하는 서비스를 검색할 수 있습니다.  

 **Active Directory 스키마 확장**은 포리스트당 한 번 수행되며, Configuration Manager를 설치하기 전이나 설치한 후에 수행할 수 있습니다.   스키마를 확장하는 경우 Configuration Manager 사이트를 포함하는 각 도메인에 **시스템 관리**라는 새 Active Directory 컨테이너를 만들어야 합니다. 이 컨테이너에 클라이언트에서 찾을 수 있도록 데이터가 게시됩니다. 자세한 내용은 [System Center Configuration Manager에 대한 Active Directory 스키마 확장](../../core/plan-design/network/extend-the-active-directory-schema.md)을 참조하세요.  

 **사이트 데이터를 게시**하면 Configuration Manager 계층 구조의 보안은 향상되고 관리 오버헤드는 줄이지만 기본 Configuration Manager 기능에는 이 작업이 필요하지 않습니다.  



<!--HONumber=Nov16_HO1-->


