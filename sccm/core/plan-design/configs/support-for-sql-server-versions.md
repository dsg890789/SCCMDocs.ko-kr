---
title: "지원되는 SQL Server 버전 | Microsoft 문서"
description: "System Center Configuration Manager 사이트 데이터베이스를 호스트하기 위한 SQL Server 버전 및 구성 요구 사항을 가져옵니다."
ms.custom: na
ms.date: 05/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 4166560602edf6eb299511c8b59dc3903e3bfffc
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017


---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 지원되는 SQL Server 버전

*적용 대상: System Center Configuration Manager(현재 분기)*

각 System Center Configuration Manager 사이트에는 사이트 데이터베이스를 호스트할 수 있는 SQL Server 버전 및 구성이 필요합니다.  

##  <a name="bkmk_Instances"></a> SQL Server 인스턴스 및 위치  
 **중앙 관리 사이트 및 기본 사이트**  
사이트 데이터베이스에서는 SQL Server의 전체 설치를 사용해야 합니다.  

 SQL Server의 위치는 다음과 같을 수 있습니다.  

-   사이트 서버 컴퓨터.  
-   사이트 서버의 원격 컴퓨터.  

다음과 같은 경우가 지원됩니다.  

-   SQL Server의 기본/명명된 인스턴스.  
-   여러 인스턴스 구성.  
-   SQL Server 클러스터. [SQL Server 클러스터를 사용하여 사이트 데이터베이스 호스트](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md)를 참조하세요.
-   SQL Server AlwaysOn 가용성 그룹. 이 옵션을 사용하려면 Configuration Manager 버전 1602 이상이 필요합니다. 자세한 내용은 [System Center Configuration Manager용 항상 사용 가능한 사이트 데이터베이스를 위한 SQL Server AlwaysOn](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md)을 참조하세요.


 **보조 사이트:**  
 사이트 데이터베이스에서는 전체 설치된 SQL Server 또는 SQL Server Express의 기본 인스턴스를 사용할 수 있습니다.  

 SQL Server는 사이트 서버 컴퓨터에 있어야 합니다.  

 **지원 제한 사항:**   
 다음 구성은 지원되지 않습니다.
 -   NLB(네트워크 부하 분산) 클러스터 구성의 SQL Server 클러스터
 -   CSV(클러스터 공유 볼륨)의 SQL Server 클러스터
 -   SQL Server 데이터베이스 미러링 기술과 피어 투 피어 복제

SQL Server 트랜잭션 복제는 [데이터베이스 복제본](https://technet.microsoft.com/library/mt608546.aspx)을 사용하도록 구성된 관리 지점에 개체를 복제하는 데에만 사용할 수 있습니다.  

##  <a name="bkmk_SQLVersions"></a> 지원되는 SQL Server 버전  
 여러 사이트가 있는 계층 구조에서 다음과 같은 경우 사이트마다 다른 SQL Server 버전을 사용하여 사이트 데이터베이스를 호스트할 수 있습니다.
 -  Configuration Manager는 사용하는 SQL Server 버전을 지원합니다.
 -  사용하는 SQL Server 버전은 Microsoft에서 계속 지원합니다.
 -  SQL Server는 두 가지 버전의 SQL Server 간 복제를 지원합니다.  예를 들어 [SQL Server는 SQL Server 2008 R2와 SQL Server 2016 간의 복제를 지원하지 않습니다](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 별도로 지정되지 않은 경우 다음 버전의 SQL Server는 System Center Configuration Manager의 모든 활성 버전에서 지원됩니다. 새 SQL Server 버전이나 서비스 팩에 대한 지원이 추가되면 해당 지원을 추가하는 Configuration Manager 버전이 표시됩니다. 마찬가지로 더 이상 지원이 제공되지 않는 경우에는 Configuration Manager의 영향받는 버전에 대한 세부 정보를 검색합니다.   

누적 업데이트가 기본 서비스 팩 버전으로 돌아가지 않는 한 특정 SQL Server 서비스 팩 지원에는 해당 서비스 팩에 대한 누적 업데이트가 포함됩니다. 서비스 팩 버전이 표시되지 않으면 서비스 팩이 없는 SQL Server의 해당 버전이 지원됩니다. 이후 해당 버전에 대한 서비스 팩이 릴리스된 경우 새 서비스 팩 버전이 지원되기 전에 개별 지원 정보가 선언됩니다.


> [!IMPORTANT]  
>  중앙 관리 사이트의 데이터베이스에 대해 SQL Server Standard를 사용하는 경우에는 계층 구조가 지원할 수 있는 총 클라이언트 수를 제한합니다. [크기 조정 및 규모 숫자 값](../../../core/plan-design/configs/size-and-scale-numbers.md)을 참조하세요.

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 SP1: Standard, Enterprise  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Standard, Enterprise  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  


### <a name="sql-server-2014-sp2-standard-enterprise"></a>SQL Server 2014 SP2: Standard, Enterprise  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트



### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Standard, Enterprise  
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트


### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 SP3: Standard, Enterprise  
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

<!-- Support for this service pack version has been dropped by Microsoft    
### SQL Server 2012 SP2: Standard, Enterprise   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A central administration site  
-   A primary site  
-   A secondary site  
-->

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter     
  [버전 1702부터](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database) 이 SQL Server 버전이 지원되지 않습니다.  
 Configuration Manager의 1702 이전 버전을 사용할 경우 이 SQL Server 버전은 계속 지원됩니다.

사용 중인 Configuration Manager 버전에서 지원될 경우 다음에 대한 최소 누적 업데이트 버전 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트
-   보조 사이트



### <a name="sql-server-2016-express-sp1"></a>SQL Server 2016 Express SP1  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트

### <a name="sql-server-2016-express"></a>SQL Server 2016 Express
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트


### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 Express SP2   
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

<!-- Support for this service pack version has been dropped by Microsoft   
### SQL Server 2012 Express SP2   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A secondary site  
-->


##  <a name="bkmk_SQLConfig"></a> SQL Server에 대한 필수 구성  
 다음은 사이트 데이터베이스에 사용할 모든 SQL Server 설치(SQL Server Express 포함)에 필요합니다. Configuration Manager에서 보조 사이트 설치의 일부로 SQL Server Express를 설치하는 경우 이러한 구성은 자동으로 만들어집니다.  

 **SQL Server 아키텍처 버전:**  
 Configuration Manager에서 사이트 데이터베이스를 호스트하려면 64비트 버전의 SQL Server가 필요합니다.  

 **데이터베이스 데이터 정렬:**  
 각 사이트에서 사이트와 사이트 데이터베이스에 사용되는 두 SQL Server 인스턴스는 모두 **SQL_Latin1_General_CP1_CI_AS**데이터 정렬을 사용해야 합니다.  

 Configuration Manager에서는 중국에서 사용하도록 GB18030으로 정의된 표준을 충족하기 위해 이 데이터 정렬에 대한 두 가지 예외를 지원합니다. 자세한 내용은 [System Center Configuration Manager의 다국어 기능 지원](../../../core/plan-design/hierarchy/international-support.md)을 참조하세요.  

 **SQL Server 기능:**  
 각 사이트 서버에는 **데이터베이스 엔진 서비스** 기능만 있으면 됩니다.  

 Configuration Manager 데이터베이스 복제를 수행할 때는 **SQL Server 복제** 기능이 필요하지 않습니다. 그러나 이 SQL Server 구성은 [System Center Configuration Manager의 관리 지점용 데이터베이스 복제본](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)을 사용할 때 필요합니다.  

 **Windows 인증:**  
 Configuration Manager에서 데이터베이스에 대한 연결의 유효성을 검사하려면 **Windows 인증**을 수행해야 합니다.  

 **SQL Server 인스턴스:**  
 각 사이트에 대해 SQL Server의 전용 인스턴스를 사용해야 합니다. 이 인스턴스는 **명명된 인스턴스** 또는 **기본 인스턴스**일 수 있습니다.  

 **SQL Server 메모리:**  
 SQL Server의 메모리는 SQL Server Management Studio를 사용하여 **서버 메모리 옵션**의 **최소 서버 메모리** 설정을 통해 예약합니다. 고정된 양의 메모리를 설정하는 방법에 대한 자세한 내용은 [방법: 고정된 양의 메모리 설정(SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759)을 참조하세요.  

-   **사이트 서버와 동일한 컴퓨터에 설치된 데이터베이스 서버:** SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 50~80%로 제한합니다.  

-   **전용 데이터베이스 서버(사이트 서버에서 원격):** SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 80~90%로 제한합니다.  

-   **사용 중인 각 SQL Server 인스턴스의 버퍼 풀에 대한 메모리 예약:**  

    -   중앙 관리 사이트: 최소 8GB를 설정합니다.  
    -   기본 사이트: 최소 8GB를 설정합니다.  
    -   보조 사이트: 최소 4GB를 설정합니다.  

**SQL 중첩 트리거:**  
 [SQL 중첩 트리거](http://go.microsoft.com/fwlink/?LinkId=528802) 를 사용하도록 설정해야 합니다.  

 **SQL Server CLR 통합**  
  사이트 데이터베이스를 사용하려면 SQL Server CLR(공용 언어 런타임)을 활성화해야 합니다. CLR은 Configuration Manager를 설치할 때 자동으로 사용됩니다. CLR에 대한 자세한 내용은 [SQL Server CLR 통합 소개](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx)를 참조하세요.  

##  <a name="bkmk_optional"></a> SQL Server에 대한 선택적 구성  
 전체 SQL Server 설치를 사용하는 각 데이터베이스에 대해 필요한 경우 다음 항목을 구성할 수 있습니다.  

 **SQL Server 서비스:**  
 다음을 사용하여 SQL Server 서비스를 실행하도록 구성할 수 있습니다.  

-   **도메인 로컬 사용자** 계정:  

    -   이 계정을 사용하는 것이 가장 좋습니다. 이때 계정의 SPN(서비스 사용자 이름)을 수동으로 등록해야 할 수 있습니다.  

-   SQL Server를 실행하는 컴퓨터의**로컬 시스템** 계정:  

    -   구성 프로세스를 간단하게 수행하려면 로컬 시스템 계정을 사용합니다.  
    -   로컬 시스템 계정을 사용할 때 Configuration Manager에서는 SQL Server 서비스에 대해 SPN을 자동으로 등록합니다.  
    -   그러나 SQL Server 서비스에 대해 로컬 시스템 계정을 사용하는 것이 SQL Server 모범 사례는 아닙니다.  

SQL Server를 실행하는 컴퓨터에서 SQL Server 서비스를 실행하기 위해 로컬 시스템 계정을 사용하지 않는 경우에는 Active Directory Domain Services에서 SQL Server 서비스를 실행하는 계정의 SPN을 구성해야 합니다. 시스템 계정을 사용할 때는 SPN이 자동으로 등록됩니다.

사이트 데이터베이스의 SPN에 대한 자세한 내용은 [System Center Configuration Manager 인프라 수정](../../../core/servers/manage/modify-your-infrastructure.md) 항목에서 [사이트 데이터베이스 서버에 대한 SPN 관리](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN)를 참조하세요.  

SQL Server 서비스에서 사용하는 계정을 변경하는 방법에 대한 자세한 내용은 [방법: SQL Server용 서비스 시작 계정 변경(SQL Server 구성 관리자)](http://go.microsoft.com/fwlink/p/?LinkId=237661)을 참조하세요.  

**SQL Server Reporting Services:**  
SQL Server Reporting Services는 보고서를 실행할 수 있는 보고 서비스 지점을 설치하는 데 필요합니다.  

> [!IMPORTANT]  
> 이전 버전에서 SQL Server를 업그레이드한 후 다음과 같은 오류가 표시될 수 있습니다. *보고서 작성기가 없습니다*.    
> 이 오류를 해결하려면 보고 서비스 지점 사이트 시스템 역할을 다시 설치해야 합니다.

**SQL Server 포트:**  
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

SQL Server를 실행하는 컴퓨터에서 방화벽이 사용하도록 설정되어 있는 경우에는 SQL Server와 통신하는 컴퓨터 간의 네트워크에 있는 모든 위치에서 배포에서 사용 중인 포트를 허용하도록 방화벽이 구성되어 있는지 확인해야 합니다.  

특정 포트를 사용하도록 SQL Server를 구성하는 방법의 예제는 SQL Server TechNet 라이브러리에서 [방법: 특정 TCP 포트로 수신하도록 서버 구성(SQL Server 구성 관리자)](http://go.microsoft.com/fwlink/p/?LinkID=226349) 을 참조하세요.  

## <a name="upgrade-options-for-sql-server"></a>SQL Server 업그레이드 옵션
SQL Server 버전을 업그레이드해야 할 경우, 쉬운 경우부터 더 복잡한 경우까지 다음 방법을 권장합니다.
1. [SQL Server 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server)(권장).
2. SQL Server의 새 버전을 새 컴퓨터에 설치하고 Configuration Manager 설치 프로그램의 [데이터베이스 이동 옵션을 사용](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration)하여 사이트 서버에서 새 SQL Server를 가리킵니다.
3. [백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 사용합니다.

