---
title: "SQL Server 지원 | System Center Configuration Manager"
description: "System Center Configuration Manager 사이트 데이터베이스를 호스트하기 위한 SQL Server 버전 및 구성 요구 사항을 가져옵니다."
ms.custom: na
ms.date: 10/06/2016
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
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: b17720021f797d404a89933939427696dfafd7dc


---
# <a name="support-for-sql-server-versions-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 SQL Server 버전 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

각 System Center Configuration Manager 사이트에는 사이트 데이터베이스를 호스트할 수 있는 SQL Server 버전 및 구성이 필요합니다.  

##  <a name="a-namebkmkinstancesa-sql-server-instances-and-locations"></a><a name="bkmk_Instances"></a> SQL Server 인스턴스 및 위치  
 **중앙 관리 사이트 및 기본 사이트**  

사이트 데이터베이스에서는 SQL Server의 전체 설치를 사용해야 합니다.  

 SQL Server의 위치는 다음과 같을 수 있습니다.  

-   사이트 서버 컴퓨터  
-   사이트 서버의 원격 컴퓨터  

다음과 같은 경우가 지원됩니다.  

-   SQL Server의 기본/명명된 인스턴스  
-   여러 인스턴스 구성  
-   SQL Server 클러스터 - [SQL Server 클러스터를 사용하여 사이트 데이터베이스 호스트](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md) 참조
-   SQL Server AlwaysOn 가용성 그룹 - 이 옵션을 사용하려면 Configuration Manager 버전 1602 이상이 필요합니다. 자세한 내용은 [System Center Configuration Manager용 항상 사용 가능한 사이트 데이터베이스를 위한 SQL Server AlwaysOn](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md)을 참조하세요.  

> [!NOTE]  
>  NLB(네트워크 부하 분산) 클러스터 구성의 SQL Server 클러스터는 지원되지 않습니다. 또한 SQL Server 데이터베이스 미러링 기술과 피어 투 피어 복제도 지원되지 않습니다. SQL Server 표준 트랜잭션 복제는 [데이터베이스 복제본](https://technet.microsoft.com/library/mt608546.aspx)을 사용하도록 구성된 관리 지점에 개체를 복제하는 데에만 사용할 수 있습니다.  


 **보조 사이트:**  

 사이트 데이터베이스에서는 SQL Server 또는 SQL Server Express의 전체 설치의 기본 인스턴스를 사용할 수 있습니다.  

 SQL Server의 위치는 사이트 서버 컴퓨터에 있어야 합니다.  

##  <a name="a-namebkmksqlversionsa-supported-versions-of-sql-server"></a><a name="bkmk_SQLVersions"></a> 지원되는 SQL Server 버전  
 여러 사이트가 있는 계층에서는 사용 중인 SQL Server 버전이 Configuration Manager에서 지원되는 경우 사이트마다 다른 SQL Server 버전을 사용하여 사이트 데이터베이스를 호스트할 수 있습니다.  

 다음 버전의 SQL Server는 System Center Configuration Manager 버전 1511 이상에서 지원됩니다.  

> [!IMPORTANT]  
>  중앙 관리 사이트의 데이터베이스에 대해 SQL Server Standard를 사용하는 경우에는 계층 구조가 지원할 수 있는 총 클라이언트 수가 제한됩니다. [크기 조정 및 규모 숫자 값](../../../core/plan-design/configs/size-and-scale-numbers.md)을 참조하세요.

### <a name="sql-server-2016---standard-enterprise"></a>SQL Server 2016 - Standard, Enterprise  

버전 1606에서 사용할 수 있습니다.   
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  


### <a name="sql-server-2014-sp2---standard-enterprise"></a>SQL Server 2014 SP2 - Standard, Enterprise  

버전 1511 이상에서 지원됩니다.  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  



### <a name="sql-server-2014-sp1---standard-enterprise"></a>SQL Server 2014 SP1 - Standard, Enterprise  

버전 1511 이상에서 지원됩니다.  
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  


### <a name="sql-server-2012-sp3---standard-enterprise"></a>SQL Server 2012 SP3 - Standard, Enterprise  

버전 1511 이상에서 지원됩니다.  
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  


### <a name="sql-server-2012-sp2---standard-enterprise"></a>SQL Server 2012 SP2 - Standard, Enterprise  

버전 1511 이상에서 지원됩니다.  
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  


### <a name="sql-server-2008-r2-sp3---standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3 - Standard, Enterprise, Datacenter  

버전 1511 이상에서 지원됩니다.    
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

### <a name="sql-server-2016-express"></a>SQL Server 2016 Express
버전 1606에서 사용할 수 있습니다.  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.
-   보조 사이트

### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 Express SP2  
버전 1511 이상에서 사용할 수 있습니다.  
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1  
 버전 1511 이상에서 사용할 수 있습니다.   
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
버전 1511 이상에서 사용할 수 있습니다.   
다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

### <a name="sql-server-2012-express-sp2"></a>SQL Server 2012 Express SP2  
 버전 1511 이상에서 사용할 수 있습니다.  
 다음에 대한 최소 누적 업데이트 없이 이 버전의 SQL Server를 사용할 수 있습니다.  

-   보조 사이트  

##  <a name="a-namebkmksqlconfiga-required-configurations-for-sql-server"></a><a name="bkmk_SQLConfig"></a> SQL Server에 대한 필수 구성  
 다음은 사이트 데이터베이스에 사용할 모든 SQL Server 설치(SQL Server Express 포함)에 필요합니다. Configuration Manager에서 보조 사이트 설치의 일부로 SQL Server Express를 설치하는 경우 이러한 구성은 자동으로 수행됩니다.  

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
 SQL Server의 메모리는 SQL Server Management Studio를 사용하여 **서버 메모리 옵션** 의 **최소 서버 메모리**설정을 통해 예약합니다. 고정된 양의 메모리를 설정하는 방법에 대한 자세한 내용은 [방법: 고정된 양의 메모리 설정(SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759)을 참조하세요.  

-   **사이트 서버와 동일한 컴퓨터에 설치된 데이터베이스 서버** : SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 50~80%로 제한합니다.  

-   **전용 데이터베이스 서버(사이트 서버에서 원격):** - SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 80~90%로 제한합니다.  

-   **사용 중인 각 SQL Server 인스턴스의 버퍼 풀에 대한 메모리 예약:**  

    -   중앙 관리 사이트: 최소 8GB  
    -   기본 사이트: 최소 8GB  
    -   보조 사이트: 최소 4GB  

 **SQL 중첩 트리거:**  

 [SQL 중첩 트리거](http://go.microsoft.com/fwlink/?LinkId=528802) 를 사용하도록 설정해야 합니다.  

 **SQL Server CLR 통합**  

  사이트 데이터베이스를 사용하려면 SQL Server CLR(공용 언어 런타임)을 활성화해야 합니다. CLR은 Configuration Manager를 설치할 때 자동으로 사용됩니다. CLR에 대한 자세한 내용은 [SQL Server CLR 통합 소개](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx)를 참조하세요.  

##  <a name="a-namebkmkoptionala-optional-configurations-for-sql-server"></a><a name="bkmk_optional"></a> SQL Server에 대한 선택적 구성  
 전체 SQL Server 설치를 사용하는 각 데이터베이스에 대해 필요한 경우 다음 항목을 구성할 수 있습니다.  

 **SQL Server 서비스:**  
 다음을 사용하여 SQL Server 서비스를 실행하도록 구성할 수 있습니다.  

-   **도메인 로컬 사용자** 계정:  

    -   이 계정을 사용하는 것이 가장 좋습니다. 이때 계정의 SPN(서비스 사용자 이름)을 수동으로 등록해야 할 수 있습니다.  

-   SQL Server를 실행하는 컴퓨터의**로컬 시스템** 계정:  

    -   구성 프로세스를 간단하게 수행하려면 로컬 시스템 계정을 사용합니다.  
    -   로컬 시스템 계정을 사용할 때 Configuration Manager에서는 SQL Server 서비스에 대해 SPN을 자동으로 등록합니다.  
    -   그러나 SQL Server 서비스에 대해 로컬 시스템 계정을 사용하는 것이 SQL Server 모범 사례는 아닙니다.  

SQL Server에서 SQL Server 서비스를 실행하기 위해 컴퓨터 로컬 시스템 계정을 사용하지 않는 경우에는 Active Directory Domain Services에서 SQL Server 서비스를 실행하는 계정의 SPN(서비스 사용자 이름)을 구성해야 합니다. 시스템 계정을 사용할 때는 SPN이 자동으로 등록됩니다.

사이트 데이터베이스의 SPN에 대한 자세한 내용은 [System Center Configuration Manager 인프라 수정](../../../core/servers/manage/modify-your-infrastructure.md) 항목에서 [사이트 데이터베이스 서버에 대한 SPN 관리](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN)를 참조하세요.  

SQL 서비스에서 사용하는 계정을 변경하는 방법에 대한 자세한 내용은 [방법: SQL Server용 서비스 시작 계정 변경(SQL Server 구성 관리자)](http://go.microsoft.com/fwlink/p/?LinkId=237661)을 참조하세요.  

**SQL Server Reporting Services:**  
보고서를 실행할 수 있는 보고 서비스 지점을 설치하는 데 필요합니다.  

**SQL Server 포트:**  
SQL Server 데이터베이스 엔진에 대한 통신 및 사이트 간 복제의 경우 기본 SQL Server 포트 구성을 사용하거나 다음과 같이 사용자 지정 포트를 지정할 수 있습니다.  

-   **사이트 간 통신** 은 SQL Server Service Broker를 사용하며 기본적으로 포트 TCP 4022를 사용합니다.  
-   SQL Server 데이터베이스 엔진 및 다양한 Configuration Manager 사이트 시스템 역할 사이에서 **사이트 간 통신**은 기본적으로 포트 TCP 1433을 사용합니다. 다음 사이트 시스템 역할은 SQL Server 데이터베이스와 직접 통신합니다.  

    -   관리 지점  
    -   SMS 공급자 컴퓨터  
    -   보고 서비스 지점  
    -   사이트 서버  

SQL Server가 둘 이상의 사이트에 있는 데이터베이스를 호스트하는 경우 각 데이터베이스는 개별 SQL Server 인스턴스를 사용해야 하며 각 인스턴스는 고유 포트 집합을 사용하도록 구성해야 합니다.  

> [!WARNING]  
>  Configuration Manager는 동적 포트를 지원하지 않습니다. 기본적으로 SQL Server 명명된 인스턴스는 데이터베이스 엔진에 대한 연결에 동적 포트를 사용하므로 명명된 인스턴스를 사용하는 경우 사이트 간 통신에 사용하려는 정적 포트를 수동으로 구성해야 합니다.  

SQL Server를 실행하는 컴퓨터에서 방화벽이 사용하도록 설정되어 있는 경우에는 SQL Server와 통신하는 컴퓨터 간의 네트워크에 있는 모든 위치에서 배포에서 사용 중인 포트를 허용하도록 방화벽이 구성되어 있는지 확인해야 합니다.  

특정 포트를 사용하도록 SQL Server를 구성하는 방법의 예제는 SQL Server TechNet 라이브러리에서 [방법: 특정 TCP 포트로 수신하도록 서버 구성(SQL Server 구성 관리자)](http://go.microsoft.com/fwlink/p/?LinkID=226349) 을 참조하세요.  



<!--HONumber=Nov16_HO1-->


