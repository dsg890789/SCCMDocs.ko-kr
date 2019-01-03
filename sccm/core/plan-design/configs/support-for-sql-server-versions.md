---
title: 지원되는 SQL Server 버전
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 데이터베이스를 호스트하기 위한 SQL Server 버전 및 구성 요구 사항을 가져옵니다.
ms.date: 08/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 43093f38a2769c46d3d96a51afbf47f33ed38b51
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53423799"
---
# <a name="supported-sql-server-versions-for-configuration-manager"></a>Configuration Manager에 대한 지원되는 SQL Server 버전

*적용 대상: System Center Configuration Manager(현재 분기)*

각 System Center Configuration Manager 사이트에는 사이트 데이터베이스를 호스트할 수 있는 SQL Server 버전 및 구성이 필요합니다.  



##  <a name="bkmk_Instances"></a> SQL Server 인스턴스 및 위치  
 
### <a name="central-administration-site-and-primary-sites"></a>중앙 관리 사이트 및 기본 사이트  
 사이트 데이터베이스에서는 SQL Server의 전체 설치를 사용해야 합니다.  

 SQL Server의 위치는 다음과 같을 수 있습니다.  

-   사이트 서버 컴퓨터.  
-   사이트 서버의 원격 컴퓨터.  

다음과 같은 경우가 지원됩니다.  

-   SQL Server의 기본/명명된 인스턴스.  
-   여러 인스턴스 구성.  
-   SQL Server 클러스터. [SQL Server 클러스터를 사용하여 사이트 데이터베이스 호스트](/sccm/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database)를 참조하세요.
-   SQL Server AlwaysOn 가용성 그룹. 자세한 내용은 [항상 사용 가능한 사이트 데이터베이스에 대한 SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)을 참조하세요.


### <a name="secondary-sites"></a>보조 사이트  
 사이트 데이터베이스에서는 전체 설치된 SQL Server 또는 SQL Server Express의 기본 인스턴스를 사용할 수 있습니다.  

 SQL Server는 사이트 서버 컴퓨터에 있어야 합니다.  


### <a name="limitations-to-support"></a>지원 제한 사항   
 다음 구성은 지원되지 않습니다.
 -   NLB(네트워크 부하 분산) 클러스터 구성의 SQL Server 클러스터
 -   CSV(클러스터 공유 볼륨)의 SQL Server 클러스터
 -   SQL Server 데이터베이스 미러링 기술과 피어 투 피어 복제

SQL Server 트랜잭션 복제는 [데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 사용하도록 구성된 관리 지점에 개체를 복제하는 데에만 사용할 수 있습니다.  



##  <a name="bkmk_SQLVersions"></a> 지원되는 SQL Server 버전  
 여러 사이트가 있는 계층 구조에서 다음과 같은 경우 사이트마다 다른 SQL Server 버전을 사용하여 사이트 데이터베이스를 호스트할 수 있습니다.
 -  Configuration Manager는 사용하는 SQL Server 버전을 지원합니다.
 -  사용하는 SQL Server 버전은 Microsoft에서 계속 지원합니다.
 -  SQL Server는 두 가지 버전의 SQL Server 간 복제를 지원합니다. 예를 들어 SQL Server는 SQL Server 2008 R2와 SQL Server 2016 간의 복제를 지원하지 않습니다. 자세한 내용은 [SQL Server 복제에서 사용되지 않는 기능](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication)을 참조하세요.



 별도로 지정되지 않은 경우 다음 버전의 SQL Server는 Configuration Manager의 모든 활성 버전에서 지원됩니다. 새 SQL Server 버전이나 서비스 팩에 대한 지원이 추가되면 해당 지원을 추가하는 Configuration Manager 버전이 표시됩니다. 마찬가지로 더 이상 지원이 제공되지 않는 경우에는 Configuration Manager의 영향 받는 버전에 대한 세부 정보를 검색합니다.   

누적 업데이트가 기본 서비스 팩 버전에 대한 호환성을 되돌리지 않으면 특정 SQL Server 서비스 팩에 대한 지원에는 해당 누적 업데이트가 포함됩니다. 서비스 팩 버전이 표시되지 않으면 서비스 팩이 없는 SQL Server의 해당 버전이 지원됩니다. 나중에 SQL Server 버전에 대한 서비스 팩이 릴리스되면 새 서비스 팩 버전이 지원되기 전에 별도의 지원 정보가 선언됩니다.


> [!IMPORTANT]  
>  중앙 관리 사이트의 데이터베이스에 대해 SQL Server Standard를 사용하는 경우에는 계층 구조가 지원할 수 있는 총 클라이언트 수를 제한합니다. [크기 조정 및 규모 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers)을 참조하세요.

### <a name="sql-server-2017-standard-enterprise"></a>SQL Server 2017: Standard, Enterprise  
다음 사이트의 경우 [Configuration Manager 버전1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)에서부터 최소 [누적 업데이트 버전 2](https://support.microsoft.com/help/4052574)에서 이 버전의 SQL Server를 사용할 수 있습니다. 

- 중앙 관리 사이트  
- 기본 사이트  
- 보조 사이트  
  <!--SMS.498506-->

### <a name="sql-server-2016-sp2-standard-enterprise"></a>SQL Server 2016 SP2: Standard, Enterprise  
<!--514985--> 다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 SP1: Standard, Enterprise  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Standard, Enterprise  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2014-sp3-standard-enterprise"></a>SQL Server 2014 SP3: Standard, Enterprise  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트

### <a name="sql-server-2014-sp2-standard-enterprise"></a>SQL Server 2014 SP2: Standard, Enterprise  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트

### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Standard, Enterprise  
 다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트

### <a name="sql-server-2012-sp4-standard-enterprise"></a>SQL Server 2012 SP4: Standard, Enterprise  
 다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 SP3: Standard, Enterprise  
 다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter     
  이 버전의 SQL Server는 지원되지 않습니다. 자세한 내용은 [사이트 데이터베이스인 SQL Server 버전에 대해 사용되지 않는 지원](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-support-for-sql-server-versions-as-a-site-database)을 참조하세요.  

### <a name="sql-server-2017-express"></a>SQL Server 2017 Express   
다음 사이트의 경우 [Configuration Manager 버전1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)에서부터 최소 [누적 업데이트 버전 2](https://support.microsoft.com/help/4052574)에서 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트 <!--SMS.498506-->

### <a name="sql-server-2016-express-sp2"></a>SQL Server 2016 Express SP2  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트

### <a name="sql-server-2016-express-sp1"></a>SQL Server 2016 Express SP1  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트

### <a name="sql-server-2016-express"></a>SQL Server 2016 Express
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트

### <a name="sql-server-2014-express-sp3"></a>SQL Server 2014 Express SP3   
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 Express SP2   
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
다음 사이트의 경우 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  



##  <a name="bkmk_SQLConfig"></a> SQL Server에 대한 필수 구성  
 다음은 사이트 데이터베이스에 사용할 모든 SQL Server 설치(SQL Server Express 포함)에 필요합니다. Configuration Manager에서 보조 사이트 설치의 일부로 SQL Server Express를 설치하는 경우 이러한 구성은 자동으로 만들어집니다.  

### <a name="sql-server-architecture-version"></a>SQL Server 아키텍처 버전  
 Configuration Manager에서 사이트 데이터베이스를 호스트하려면 64비트 버전의 SQL Server가 필요합니다.  

### <a name="database-collation"></a>데이터베이스 데이터 정렬  
 각 사이트에서 사이트와 사이트 데이터베이스에 사용되는 두 SQL Server 인스턴스는 모두 다음 데이터 정렬을 사용해야 합니다. **SQL_Latin1_General_CP1_CI_AS**.  

 Configuration Manager에서는 중국에서 사용하도록 GB18030으로 정의된 표준을 충족하기 위해 이 데이터 정렬에 대한 두 가지 예외를 지원합니다. 자세한 내용은 [다국어 기능 지원](/sccm/core/plan-design/hierarchy/international-support)을 참조하세요.  

### <a name="database-compatibility-level"></a>데이터베이스 호환성 수준   
 Configuration Manager를 사용하려면 사이트 데이터베이스에 대한 호환성 수준이 Configuration Manager 버전에 대해 지원되는 최저 SQL Server 버전과 같거나 더 높아야 합니다. 예를 들어 버전 1702부터는 [데이터베이스 호환성 수준](https://docs.microsoft.com/sql/relational-databases/databases/view-or-change-the-compatibility-level-of-a-database)이 110보다 크거나 같아야 합니다. <!-- SMS.506266--> 

### <a name="sql-server-features"></a>SQL Server 기능  
 각 사이트 서버에는 **데이터베이스 엔진 서비스** 기능만 있으면 됩니다.  

 Configuration Manager 데이터베이스 복제를 수행할 때는 **SQL Server 복제** 기능이 필요하지 않습니다. 그러나 이 SQL Server 구성은 [관리 지점용 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 사용할 때 필요합니다.  

### <a name="windows-authentication"></a>Windows 인증  
 Configuration Manager에서 데이터베이스에 대한 연결의 유효성을 검사하려면 **Windows 인증**을 수행해야 합니다.  

### <a name="sql-server-instance"></a>SQL Server 인스턴스  
 각 사이트에 대해 SQL Server의 전용 인스턴스를 사용해야 합니다. 인스턴스는 **명명된 인스턴스** 또는 **기본 인스턴스**일 수 있습니다.  

### <a name="sql-server-memory"></a>SQL Server 메모리  
 SQL Server의 메모리는 SQL Server Management Studio를 사용하여 **서버 메모리 옵션**의 **최소 서버 메모리** 설정을 통해 예약합니다. 이 설정을 구성하는 방법에 대한 자세한 내용은 [SQL Server 메모리 서버 구성 옵션](https://docs.microsoft.com/sql/database-engine/configure-windows/server-memory-server-configuration-options)을 참조하세요.  

-   **사이트 서버와 동일한 컴퓨터에 설치된 데이터베이스 서버:** SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 50~80%로 제한합니다.  

-   **전용 데이터베이스 서버(사이트 서버의 원격 서버)**: SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 80~90%로 제한합니다.  

-   **사용 중인 각 SQL Server 인스턴스의 버퍼 풀에 대한 메모리 예약**:  

    -   중앙 관리 사이트: 최소 8GB(기가바이트)를 설정합니다.  
    -   기본 사이트: 최소 8GB(기가바이트)를 설정합니다.  
    -   보조 사이트: 최소 4GB(기가바이트)를 설정합니다.  

### <a name="sql-nested-triggers"></a>SQL 중첩 트리거  
 SQL 중첩 트리거를 사용하도록 설정해야 합니다. 자세한 내용은 [중첩 트리거 서버 구성 옵션 구성](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option)을 참조하세요. 

### <a name="sql-server-clr-integration"></a>SQL Server CLR 통합  
  사이트 데이터베이스를 사용하려면 SQL Server CLR(공용 언어 런타임)을 활성화해야 합니다. 이 옵션은 Configuration Manager를 설치할 때 자동으로 사용하도록 설정됩니다. CLR에 대한 자세한 내용은 [SQL Server CLR 통합 소개](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration)를 참조하세요.  



##  <a name="bkmk_optional"></a> SQL Server에 대한 선택적 구성  
 전체 SQL Server 설치를 사용하는 각 데이터베이스에 대해 필요한 경우 다음 항목을 구성할 수 있습니다.  

### <a name="sql-server-service"></a>SQL Server 서비스  
 다음을 사용하여 SQL Server 서비스를 실행하도록 구성할 수 있습니다.  

-   *제한된 권한의 도메인 사용자* 계정:  

    -   이 구성을 사용하는 것이 가장 좋습니다. 이때 계정의 SPN(서비스 사용자 이름)을 수동으로 등록해야 할 수 있습니다.  

-   SQL Server를 실행하는 컴퓨터의**로컬 시스템** 계정:  

    -   구성 프로세스를 간단하게 수행하려면 로컬 시스템 계정을 사용합니다.  
    -   로컬 시스템 계정을 사용할 때 Configuration Manager에서는 SQL Server 서비스에 대해 SPN을 자동으로 등록합니다.  
    -   SQL Server 서비스에 대해 로컬 시스템 계정을 사용하는 것이 SQL Server 모범 사례는 아닙니다.  

SQL Server를 실행하는 컴퓨터에서 SQL Server 서비스를 실행하기 위해 로컬 시스템 계정을 사용하지 않는 경우에는 Active Directory Domain Services에서 SQL Server 서비스를 실행하는 계정의 SPN을 구성해야 합니다. 시스템 계정을 사용할 때는 SPN이 자동으로 등록됩니다.

사이트 데이터베이스의 SPN에 대한 자세한 내용은 [사이트 데이터베이스 서버에 대한 SPN 관리](/sccm/core/servers/manage/modify-your-infrastructure#bkmk_SPN)를 참조하세요.  

SQL Server 서비스에서 사용하는 계정을 변경하는 방법에 대한 자세한 내용은 [SCM Services - 서비스 시작 계정 변경](https://docs.microsoft.com/sql/database-engine/configure-windows/scm-services-change-the-service-startup-account)을 참조하세요.  

### <a name="sql-server-reporting-services"></a>SQL Server Reporting Services  
SQL Server Reporting Services는 보고서를 실행할 수 있는 보고 서비스 지점을 설치하는 데 필요합니다.  

> [!IMPORTANT]  
> 이전 버전에서 SQL Server를 업그레이드한 후 다음과 같은 오류가 표시될 수 있습니다.  ‘보고서 작성기가 없습니다.’  
> 이 오류를 해결하려면 보고 서비스 지점 사이트 시스템 역할을 다시 설치해야 합니다.  

### <a name="sql-server-ports"></a>SQL Server 포트  
SQL Server 데이터베이스 엔진에 대한 통신 및 사이트 간 복제의 경우 기본 SQL Server 포트 구성을 사용하거나 다음과 같이 사용자 지정 포트를 지정할 수 있습니다.  

-   **사이트 간 통신**은 SQL Server Service Broker를 사용하며 기본적으로 포트 TCP 4022를 사용합니다.  
-   SQL Server 데이터베이스 엔진 및 다양한 Configuration Manager 사이트 시스템 역할 사이에서 **사이트 간 통신**은 기본적으로 포트 TCP 1433을 사용합니다. 다음 사이트 시스템 역할은 SQL Server 데이터베이스와 직접 통신합니다.  

    -   관리 지점  
    -   SMS 공급자 컴퓨터  
    -   보고 서비스 지점  
    -   사이트 서버  

SQL Server를 실행하는 컴퓨터는 둘 이상의 사이트에 있는 데이터베이스를 호스트하는 경우 각 데이터베이스는 별도의 SQL Server 인스턴스를 사용해야 합니다. 또한 각 인스턴스는 고유 포트 집합을 사용하도록 구성해야 합니다.  

> [!WARNING]  
>  Configuration Manager는 동적 포트를 지원하지 않습니다. 기본적으로 SQL Server 명명된 인스턴스는 데이터베이스 엔진에 대한 연결에 동적 포트를 사용하므로 명명된 인스턴스를 사용하는 경우 사이트 간 통신에 사용하려는 정적 포트를 수동으로 구성해야 합니다.  

SQL Server를 실행하는 컴퓨터에서 방화벽을 사용하도록 설정되어 있는 경우에는 배포에서, 그리고 SQL Server와 통신하는 여러 컴퓨터 간의 네트워크상에 있는 모든 위치에서 사용 중인 포트를 허용하도록 방화벽이 구성되어 있는지 확인해야 합니다.  

특정 포트를 사용하도록 SQL Server를 구성하는 방법에 대한 예는 [특정 TCP 포트로 수신하도록 서버 구성](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port)을 참조하세요.  



## <a name="upgrade-options-for-sql-server"></a>SQL Server 업그레이드 옵션

SQL Server 버전을 업그레이드해야 하는 경우, 쉬운 경우부터 시작해서 복잡한 경우까지 순차적으로 다음 방법을 사용하세요.  

- [SQL Server 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server)(권장)  

- SQL Server의 새 버전을 새 컴퓨터에 설치하고 Configuration Manager 설치 프로그램의 [데이터베이스 이동 옵션을 사용](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration)하여 사이트 서버가 새 SQL Server를 가리키도록 합니다.  

- [백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 사용합니다. SQL 업그레이드 시나리오에 백업 및 복구를 사용할 수 있습니다. [사이트 복구 전 고려 사항](/sccm/protect/understand/recover-sites#considerations-before-recovering-a-site)을 검토할 때 SQL 버전 관리 요구 사항을 무시할 수 있습니다. 
