---
title: "사이트 구성 | System Center Configuration Manager"
description: "사이트와 계층 모두에 영향을 주는 가장 일반적인 구성을 고려하려면 이 검사 목록을 참조하세요."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 470efc428045398588345f4546eb27831837715c


---
# <a name="configure-sites-and-hierarchies-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 사이트 및 계층 구조 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

첫 번째 System Center Configuration Manager 사이트를 설치하거나 계층 구조에 사이트를 더 추가한 후에는 다음 검사 목록을 참조하여 사이트와 계층에 모두 영향을 주는 가장 일반적인 구성을 고려해야 합니다.  

## <a name="checklist-of-common-configurations-for-new-and-additional-sites"></a>신규 사이트 및 추가 사이트의 일반 구성 검사 목록  
 대부분의 배포에서는 다음 옵션을 특정 순서로 구성하지 않아도 됩니다.  

-   Active Directory 포리스트 검색, 경계, 경계 그룹 등 서로를 기반으로 작성되는 옵션도 있습니다.  

-   또한 구성을 변경하지 않고 사용 가능한 기본값(일시적으로 사용 가능한 기본값도 포함됨)이 있는 구성도 많습니다.  

-   경계 그룹 및 배포 지점 그룹과 같이 사용하기 전에 구성해야 하는 구성도 있습니다.  

|작업|세부 정보|  
|------------|-------------|  
|역할 기반 관리 구성|역할 기반 관리에서는 관리 할당을 구분하여 Configuration Manager 환경의 여러 개체와 데이터를 보고 관리할 수 있는 관리자를 제어할 수 있습니다.<br /><br /> 계층 구조의 모든 사이트가 역할 기반 관리의 구성을 공유합니다.   <br />자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.|  
|AD DS(Active Directory Domain Services)에 사이트 데이터 게시|AD DS에 사이트 데이터를 게시하면 클라이언트가 서비스를 쉽게 찾고 사이트 리소스를 효율적으로 사용할 수 있습니다.<br /><br /> 먼저 [System Center Configuration Manager에 대한 Active Directory 스키마를 확장](../../../../core/plan-design/network/extend-the-active-directory-schema.md)한 후 각 사이트를 [System Center Configuration Manager용으로 사이트 데이터를 게시](../../../../core/servers/deploy/configure/publish-site-data.md)하도록 개별적으로 구성해야 합니다.|  
|서비스 연결 지점 구성|계층 구조의 최상위 계층 사이트에서 서비스 연결 지점 설치 및 구성을 계획해야 합니다. 자세한 내용은 [System Center Configuration Manager의 서비스 연결 지점 정보](../../../../core/servers/deploy/configure/about-the-service-connection-point.md)를 참조하세요.|  
|사이트 시스템 역할 추가|개별 사이트에 하나 이상의 추가 사이트 시스템 역할을 설치합니다.  [Add site system roles for System Center Configuration Manager](../../../../core/servers/deploy/configure/add-site-system-roles.md)섹션을 참조하세요.|  
|사이트 경계 및 경계 그룹 구성|관리하려는 장치를 포함할 수 있는 인트라넷의 네트워크 위치를 정의하는 경계를 지정한 다음 해당 네트워크 위치의 클라이언트가 Configuration Manager 서비스 리소스를 찾을 수 있도록 경계 그룹을 구성합니다. [System Center Configuration Manager에 대한 사이트 경계 및 경계 그룹 정의](../../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md)를 참조하세요.|  
|배포 지점 그룹 구성|배포를 쉽게 관리할 수 있도록 배포 지점의 논리적 그룹을 구성합니다. [System Center Configuration Manager의 배포 지점 설치 및 구성](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md)에서 [배포 지점 그룹 관리](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage)를 참조하세요.|  
|검색 실행|검색을 실행하여 네트워크 인프라, 장치 및 사용자를 포함한 네트워크의 리소스를 찾습니다.<br /><br /> [Run discovery for System Center Configuration Manager](../../../../core/servers/deploy/configure/run-discovery.md)섹션을 참조하세요.|  
|인프라를 관리하는 사용자를 위해 중복 항목 및 용량 추가|인프라를 관리하는 관리자용으로 용량을 확장하기 위해 추가 SMS 공급자 및 Configuration Manager 콘솔을 설치할 수 있습니다.<br /><br /> **여러 SMS 공급자를 설치** 하면 사이트와 계층 구조를 관리하는 연결 지점에 중복성을 구현할 수 있습니다. [Modify your System Center Configuration Manager 항목에서frastructure](../../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) 항목에서 [Modify your System Center Configuration Manager 항목에서frastructure](../../../../core/servers/manage/modify-your-infrastructure.md)를 참조하세요.<br /><br /> 추가 관리자가 동시에 액세스할 수 있도록**Configuration Manager 콘솔을 추가로 설치** 합니다. [Configuration Manager 콘솔 설치](../../../../core/servers/deploy/install/install-consoles.md)를 참조하세요.|  
|사이트 구성 요소 구성|사이트 시스템 역할 및 사이트 상태 보고의 동작을 수정하기 위해 각 사이트의 사이트 구성 요소를 구성할 수 있습니다. [Site components for System Center Configuration Manager](../../../../core/servers/deploy/configure/site-components.md)섹션을 참조하세요.|  
|사용자 지정 컬렉션 만들기|장치 및 사용자에 대해 검색되는 정보를 사용하여 사용자 지정 개체 컬렉션을 만들면 이후의 관리 작업이 단순해집니다. [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)을 참조하세요.|  
|높은 위험 수준의 배포를 관리하는 설정 구성|관리자가 높은 위험 수준의 작업 순서 배포를 만들 때 경고를 표시하는 설정을 사이트에서 구성합니다.  [Settings to manage high-risk deployments for System Center Configuration Manager](../../../../protect/understand/settings-to-manage-high-risk-deployments.md)섹션을 참조하세요.|  
|관리 지점에 대한 데이터베이스 복제본 구성|데이터베이스 복제본을 구성하면 클라이언트의 요청을 처리하는 관리 지점이 사이트 데이터베이스 서버에 적용하는 CPU 부하를 줄일 수 있습니다. [Database replicas for management points for System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md)섹션을 참조하세요.|  
|사이트 데이터베이스를 호스트하도록 SQL Server AlwaysOn 가용성 그룹 구성|1602 버전부터, 기본 사이트와 중앙 관리 사이트에서 사이트 데이터베이스를 호스트하기 위한 고가용성 및 재해 복구 솔루션으로 가용성 그룹을 구성할 수 있습니다. [System Center Configuration Manager용 항상 사용 가능한 사이트 데이터베이스를 위한 SQL Server AlwaysOn](../../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md)을 참조하세요.|  
|사이트 간 복제 수정|[System Center Configuration Manager의 사이트 간 데이터 전송](../../../../core/servers/manage/data-transfers-between-sites.md)에서 다음 주제에 대해 자세히 알아보세요.<br /><br /> 보조 사이트 간에 [File-based replication](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_fileroute) 구성<br /><br /> [Database replication links](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_Dblinks)구성<br /><br /> [Distributed views](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_distviews)구성|  



<!--HONumber=Nov16_HO1-->


