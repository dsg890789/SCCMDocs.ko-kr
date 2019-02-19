---
title: 보고 계획
titleSuffix: Configuration Manager
description: 설치 세부 정보부터 보안 및 네트워크 대역폭에 이르기까지 Configuration Manager의 보고 계획은 중요합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ff920c84-d5c8-458c-b67f-bc7219b05690
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9920b8b16f076fe9f0ebf807f4231e262fcabf33
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56123157"
---
# <a name="planning-for-reporting-in-system-center-configuration-manager"></a>System Center Configuration Manager의 보고 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 보고는 SQL Server Reporting Services의 고급 보고 기능을 사용하는 데 도움이 되는 일련의 도구와 리소스를 제공합니다. 다음 섹션을 사용하여 Configuration Manager의 보고를 계획할 수 있습니다.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> 보고 서비스 지점을 설치할 위치 결정  
 사이트에서 Configuration Manager 보고서를 실행하는 경우 보고서가 연결되는 사이트 데이터베이스에 있는 정보에 액세스할 수 있습니다. 다음 섹션에서는 보고 서비스 지점을 설치할 위치와 사용할 데이터 원본을 결정하는 방법을 설명합니다.  

> [!NOTE]  
>  Configuration Manager에서 사이트 시스템을 계획하는 방법에 대한 자세한 내용은 [사이트 시스템 역할 추가](../deploy/configure/add-site-system-roles.md)를 참조하세요.  

###  <a name="BKMK_SupportedSiteServers"></a> 지원되는 사이트 시스템 서버  
 중앙 관리 사이트와 기본 사이트에서 한 사이트의 여러 사이트 시스템과 계층의 다른 시스템에 보고 서비스 지점을 설치할 수 있습니다. 보조 사이트에서는 보고 서비스 지점이 지원되지 않습니다. 사이트의 첫 번째 보고 서비스 지점이 기본 보고 서버로 구성됩니다. 사이트에 보고 서비스 지점을 더 추가할 수 있지만 각 사이트의 기본 보고 서버가 Configuration Manager 보고서에 자동으로 사용됩니다. 사이트 서버 또는 원격 사이트 시스템에 보고 서비스 지점을 설치할 수 있는데, 성능 최적화를 위해서는 원격 사이트 시스템 서버에 보고 서비스를 사용하는 것이 좋습니다.  

###  <a name="BKMK_DataReplication"></a> 데이터 복제 시 고려 사항  
 Configuration Manager에서는 복제하는 데이터를 글로벌 데이터와 사이트 데이터로 분류합니다. 글로벌 데이터는 관리자가 만들어서 계층의 모든 사이트에 복제한 개체를 나타냅니다. 단, 보조 사이트에서는 일부 글로벌 데이터만 받습니다. 글로벌 데이터의 예로는 소프트웨어 배포, 소프트웨어 업데이트, 컬렉션, 역할 기반 관리 보안 범위 등이 있습니다. 사이트 데이터는 Configuration Manager 기본 사이트 및 기본 사이트에 보고하는 클라이언트에서 만드는 작업 정보를 나타냅니다. 사이트 데이터는 중앙 관리 사이트에 복제되지만 다른 기본 사이트에는 복제되지 않습니다. 사이트 데이터의 예로는 하드웨어 인벤토리 데이터, 상태 메시지, 경고, 쿼리 기반 컬렉션 결과 등이 있습니다. 사이트 데이터는 중앙 관리 사이트와 데이터가 원래 있던 기본 사이트에서만 표시됩니다.  

 보고 서비스 지점을 설치할 위치를 결정할 때에는 다음 요인을 고려하십시오.  

-   중앙 관리 사이트 데이터베이스를 보고 데이터 원본으로 사용하는 보고 서비스 지점에서는 Configuration Manager 계층의 모든 글로벌 데이터와 사이트 데이터에 액세스할 수 있습니다. 계층의 여러 사이트에 대한 사이트 데이터가 포함된 보고서가 필요한 경우 중앙 관리 사이트의 사이트 시스템에 보고 서비스 지점을 설치하고 중앙 관리 사이트의 데이터베이스를 보고 데이터 원본으로 사용합니다.  

-   자식 기본 사이트 데이터베이스를 보고 데이터 원본으로 사용하는 보고 서비스 지점에서는 해당 로컬 기본 사이트와 모든 자식 보조 사이트에 대한 글로벌 데이터와 사이트 데이서에만 액세스할 수 있습니다. Configuration Manager 계층의 다른 기본 사이트에 대한 사이트 데이터는 기본 사이트에 복제되지 않으므로 Reporting Services에서 액세스할 수 없습니다. 특정 기본 사이트에 대한 사이트 데이터 또는 글로벌 데이터가 포함된 보고서가 필요하지만 보고서 사용자가 다른 기본 사이트에서 사이트 데이터에 액세스하는 것을 원하지 않을 경우, 기본 사이트의 사이트 시스템에 보고 서비스 지점을 설치하고 기본 사이트의 데이터베이스를 보고 데이터 원본으로 사용합니다.  

###  <a name="BKMK_NetworkBandwidth"></a> 네트워크 대역폭 고려 사항  
 한 사이트 내에 있는 사이트 시스템 서버는 사이트 구성 방식에 따라 SMB(서버 메시지 블록), HTTP 또는 HTTPS를 사용하여 서로 통신합니다. 이러한 통신은 관리되지 않으며 네트워크 대역폭 제어 없이 언제든지 이루어질 수 있으므로 사이트 시스템에 보고 서비스 지점 역할을 설치하기 전에 사용 가능한 네트워크 대역폭을 검토하십시오.  

> [!NOTE]  
>  사이트 시스템 계획에 대한 자세한 내용은 [사이트 시스템 역할 추가](../deploy/configure/add-site-system-roles.md)를 참조하세요.  

##  <a name="BKMK_RoleBaseAdministration"></a> 보고서에 대한 역할 기반 관리 계획  
 보고에 대한 보안은 Configuration Manager의 다른 개체에 대한 보안과 거의 비슷합니다. 즉, 관리자에게 보안 역할과 권한을 할당할 수 있습니다. 관리자는 해당 보안 권한이 있는 보고서만 실행 및 수정할 수 있습니다. Configuration Manager 콘솔에서 보고서를 실행하려면 **사이트** 권한과 특정 개체에 대해 구성된 권한에 대한 **읽기** 권한이 있어야 합니다.  

 그러나 Configuration Manager의 다른 개체와 달리 Configuration Manager 콘솔에서 관리자에 대해 설정하는 보안 권한을 Reporting Services에도 구성해야 합니다. Configuration Manager 콘솔에서 보안 권한을 구성하면 보고 서비스 지점이 Reporting Services에 연결하여 보고서에 대한 적절한 권한을 설정합니다. 예를 들어 **소프트웨어 업데이트 관리자** 보안 역할은 이 역할에 연결된 **보고서 실행** 및 **보고서 수정** 권한을 갖습니다. **소프트웨어 업데이트 관리자** 역할만 할당된 관리자는 소프트웨어 업데이트에 대한 보고서만 실행하고 수정할 수 있습니다. 다른 개체에 대한 보고서는 Configuration Manager 콘솔에 표시되지 않습니다. 이에 대한 예외로, 일부 보고서는 특정 Configuration Manager 보안 개체와 연결되지 않습니다. 이러한 보고서에 대해 관리자가 보고서를 실행하려면 **사이트** 권한에 대한 **수정** 권한이 필요하고, 보고서를 수정하려면 **사이트** 권한에 대한 **수정** 권한이 필요합니다.  

 모든 보고서 기능을 역할 기반 관리에 사용할 수 있습니다. Configuration Manager에 포함된 모든 보고서의 데이터는 보고서를 실행하는 관리자의 권한에 따라 필터링됩니다. 특정 역할의 관리자는 해당 역할에 대해 정의된 정보만 볼 수 있습니다.  

 보고를 위한 보안 권한에 대한 자세한 내용은 [보고 구성](configuring-reporting.md)을 참조하세요.  

 Configuration Manager에서 역할 기반 관리에 대한 자세한 내용은 [역할 기반 관리 구성](../deploy/configure/configure-role-based-administration.md)을 참조하세요.  

## <a name="next-steps"></a>다음 단계  
 다음 추가 항목에서는 Configuration Manager의 보고를 계획하는 데 도움이 되는 정보를 제공합니다.  

-   [System Center Configuration Manager에서 보고에 대한 필수 조건](../../../core/servers/manage/prerequisites-for-reporting.md)  
-   [System Center Configuration Manager에서 보고에 대한 모범 사례](../../../core/servers/manage/best-practices-for-reporting.md)  
