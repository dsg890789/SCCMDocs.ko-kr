---
title: 사이트 및 계층 구조 구성
titleSuffix: Configuration Manager
description: 사이트와 계층 모두에 영향을 주는 가장 일반적인 구성을 고려하려면 이 검사 목록을 참조하세요.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 051958c5fa524c97de0e42784cdab73288a24b82
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39383714"
---
# <a name="configure-sites-and-hierarchies-for-configuration-manager"></a>Configuration Manager에 대한 사이트 및 계층 구조 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

첫 번째 Configuration Manager 사이트를 설치하거나 계층 구조에 사이트를 더 추가한 후에는 이 검사 목록을 사용하여 사이트와 계층 구조 모두에 영향을 주는 가장 일반적인 구성을 고려해야 합니다.  

다음 구성 정보는 대부분의 배포에 적용됩니다.  

- Active Directory 포리스트 검색, 경계, 경계 그룹과 같이 서로를 기반으로 작성되는 옵션도 있습니다.  

- 몇 가지 구성에는 구성 변경 없이 최소한으로 시작할 수 있는 기본값이 있습니다.  

- 경계 그룹 및 배포 지점 그룹과 같은 다른 구성은 사용하기 전에 구성해야 합니다.  

| 작업 | 세부 정보 |  
|------------|-------------|  
| 역할 기반 관리 구성 | 관리 할당을 구분하여 Configuration Manager 환경의 여러 개체와 데이터를 보고 관리할 수 있는 관리자를 제어합니다.<br /><br /> 계층 구조의 모든 사이트가 역할 기반 관리의 구성을 공유합니다.   <br/><br/>자세한 내용은 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요. |  
| Active Directory Domain Services에 사이트 데이터 게시 | 클라이언트에서 서비스를 쉽게 찾고 사이트 리소스를 효율적으로 사용하도록 합니다.<br /><br /> 먼저 [Active Directory 스키마를 확장](/sccm/core/plan-design/network/extend-the-active-directory-schema)합니다. 그런 다음, [사이트 데이터를 게시](/sccm/core/servers/deploy/configure/publish-site-data)하도록 각 사이트를 개별적으로 구성합니다. |  
| 서비스 연결 지점 구성 | 계층 구조의 최상위 사이트에서 서비스 연결 지점을 설치하고 구성하도록 계획합니다. 자세한 내용은 [서비스 연결 지점 정보](/sccm/core/servers/deploy/configure/about-the-service-connection-point)를 참조하세요. |  
| 사이트 시스템 역할 추가 | 개별 사이트의 추가 사이트 시스템 역할을 하나 이상 설치합니다. 자세한 내용은 [사이트 시스템 역할 추가](/sccm/core/servers/deploy/configure/add-site-system-roles)를 참조하세요. |  
| 사이트 경계 및 경계 그룹 구성 | 관리할 장치를 포함할 수 있는 인트라넷의 네트워크 위치를 정의하는 경계를 지정합니다. 그런 다음 해당 네트워크 위치의 클라이언트에서 Configuration Manager 리소스를 찾을 수 있도록 경계 그룹을 구성합니다. 자세한 내용은 [사이트 경계 및 경계 그룹 정의](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups)를 참조하세요. |  
| 배포 지점 그룹 구성 | 배포를 쉽게 관리할 수 있도록 배포 지점의 논리적 그룹을 구성합니다. 자세한 내용은 [배포 지점 그룹 관리](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_manage)를 참조하세요. |  
| 검색 실행 | 검색을 실행하여 네트워크 인프라, 장치 및 사용자를 포함한 네트워크의 리소스를 찾습니다.<br /><br /> 자세한 내용은 [검색 실행](/sccm/core/servers/deploy/configure/run-discovery)을 참조하세요. |  
| 관리자를 위한 중복성 및 용량 추가 | 인프라를 관리하는 관리자용으로 용량을 확장하기 위해 추가 SMS 공급자 및 Configuration Manager 콘솔을 설치합니다.<br /><br /> 사이트에 콘솔 및 API 연결에 대한 중복성을 제공하려면 **추가 SMS 공급자를 설치**합니다. 자세한 내용은 [SMS 공급자 관리](/sccm/core/servers/manage/modify-your-infrastructure#BKMK_ManageSMSprovider)를 참조하세요.<br /><br /> 추가 관리자가 액세스할 수 있도록 **Configuration Manager 콘솔을 추가로 설치**합니다. 자세한 내용은 [Configuration Manager 콘솔 설치](/sccm/core/servers/deploy/install/install-consoles)를 참조하세요. |  
| 사이트 구성 요소 구성 | 사이트 시스템 역할 및 사이트 상태 보고의 동작을 수정하기 위해 각 사이트의 사이트 구성 요소를 구성합니다. 자세한 내용은 [사이트 구성 요소](/sccm/core/servers/deploy/configure/site-components)를 참조하세요. |  
| 사용자 지정 컬렉션 만들기 | 사이트에서 장치 및 사용자에 대해 검색한 정보를 사용하여 개체의 사용자 지정 개체 컬렉션을 만들면 이후의 관리 작업이 단순해집니다. 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요. |  
| 높은 위험 수준의 배포를 관리하는 설정 구성 | 관리자가 높은 위험 수준의 배포를 만들 때 경고하도록 사이트에서 설정을 구성합니다. 자세한 내용은 [높은 위험 수준의 배포를 관리하는 설정](/sccm/core/servers/manage/settings-to-manage-high-risk-deployments)을 참조하세요. |  
| 관리 지점에 대한 데이터베이스 복제본 구성 | 데이터베이스 복제본을 구성하면 클라이언트의 요청을 처리하는 관리 지점이 사이트 데이터베이스 서버에 적용하는 프로세서 부하를 줄일 수 있습니다. 자세한 내용은 [관리 지점에 대한 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 참조하세요. |  
| SQL Server Always On 가용성 그룹 구성 | 기본 사이트와 중앙 관리 사이트에서 사이트 데이터베이스를 호스팅하기 위한 고가용성 및 재해 복구 솔루션으로 가용성 그룹을 구성합니다. 자세한 내용은 [항상 사용 가능한 사이트 데이터베이스에 대한 SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)을 참조하세요. |  
| 사이트 간 복제 수정 | 다음 주제에 대해 알아보려면 [사이트 간 데이터 전송](/sccm/core/servers/manage/data-transfers-between-sites)을 참조하세요.<br /><br /> 보조 사이트 간에 [파일 기반 복제](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_fileroute) 구성<br /><br /> [데이터베이스 복제 링크](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_Dblinks)구성<br /><br /> [분산 보기](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_distviews)구성 |  
| 수동 모드에서 사이트 서버 구성 | 버전 1806부터 각 기본 사이트 및 중앙 관리 사이트에 수동 모드로 사이트 서버를 구성합니다. 이 기능은 항상 사용 가능한 사이트 서버를 제공합니다. 자세한 내용은 [사이트 서버 고가용성](/sccm/core/servers/deploy/configure/site-server-high-availability)을 참조하세요. |  
