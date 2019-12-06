---
title: 지원되는 SQL Server 버전
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 데이터베이스를 호스트하기 위한 SQL Server 버전 및 구성 요구 사항을 가져옵니다.
ms.date: 08/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e9c84044705c014c547291ea70203e16f3eab004
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "68822486"
---
# <a name="supported-sql-server-versions-for-configuration-manager"></a>Configuration Manager에 대한 지원되는 SQL Server 버전

*적용 대상: System Center Configuration Manager(현재 분기)*

각 System Center Configuration Manager 사이트에는 사이트 데이터베이스를 호스트할 수 있는 SQL Server 버전 및 구성이 필요합니다.  

##  <a name="bkmk_Instances"></a> SQL Server 인스턴스 및 위치  
 
### <a name="central-administration-site-and-primary-sites"></a>중앙 관리 사이트 및 기본 사이트
 
사이트 데이터베이스에서는 SQL Server의 전체 설치를 사용해야 합니다.  

SQL Server의 위치는 다음과 같을 수 있습니다.  

- 사이트 서버 컴퓨터.  
- 사이트 서버의 원격 컴퓨터.  

다음과 같은 경우가 지원됩니다.  

- SQL Server의 기본/명명된 인스턴스.  
- 여러 인스턴스 구성.  
- SQL Server 클러스터. [SQL Server 클러스터를 사용하여 사이트 데이터베이스 호스트](/sccm/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database)를 참조하세요.
- SQL Server AlwaysOn 가용성 그룹. 자세한 내용은 [항상 사용 가능한 사이트 데이터베이스에 대한 SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)을 참조하세요.


### <a name="secondary-sites"></a>보조 사이트  
사이트 데이터베이스에서는 전체 설치된 SQL Server 또는 SQL Server Express의 기본 인스턴스를 사용할 수 있습니다.  

SQL Server는 사이트 서버 컴퓨터에 있어야 합니다.  

### <a name="limitations-to-support"></a>지원 제한 사항

다음 구성은 지원되지 않습니다.

- NLB(네트워크 부하 분산) 클러스터 구성의 SQL Server 클러스터
- CSV(클러스터 공유 볼륨)의 SQL Server 클러스터
- SQL Server 데이터베이스 미러링 기술과 피어 투 피어 복제

SQL Server 트랜잭션 복제는 [데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 사용하도록 구성된 관리 지점에 개체를 복제하는 데에만 사용할 수 있습니다.  

##  <a name="bkmk_SQLVersions"></a> 지원되는 SQL Server 버전

여러 사이트가 있는 계층 구조에서 다음과 같은 경우 사이트마다 다른 SQL Server 버전을 사용하여 사이트 데이터베이스를 호스트할 수 있습니다.

- Configuration Manager는 사용하는 SQL Server 버전을 지원합니다.
- 사용하는 SQL Server 버전은 Microsoft에서 계속 지원합니다.
- SQL Server는 두 가지 버전의 SQL Server 간 복제를 지원합니다. 자세한 내용은 [SQL Server 복제 이전 버전과의 호환성](https://docs.microsoft.com/sql/relational-databases/replication/replication-backward-compatibility)을 참조하세요.

SQL Server 2016 및 이전 버전의 경우 각 SQL 버전 및 서비스 팩에 대한 지원은 [Microsoft 수명 주기 정책](https://aka.ms/sqllifecycle)을 따릅니다. 누적 업데이트가 기본 서비스 팩 버전에 대한 호환성을 되돌리지 않으면 특정 SQL Server 서비스 팩에 대한 지원에는 해당 누적 업데이트가 포함됩니다. SQL Server 2017부터 서비스 팩은 [최신 서비싱 모델](https://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-the-modern-servicing-model-for-sql-server/)을 따르므로 릴리스되지 않습니다. SQL Server 팀은 사용 가능한 [누적 업데이트를 지속적으로 사전 설치](https://blogs.msdn.microsoft.com/sqlreleaseservices/announcing-updates-to-the-sql-server-incremental-servicing-model-ism/)하도록 권장합니다.


별도로 지정되지 않은 경우 다음 버전의 SQL Server는 Configuration Manager의 모든 활성 버전에서 지원됩니다. 새 SQL Server 버전에 대한 지원이 추가되면 해당 지원을 추가하는 Configuration Manager 버전이 표시됩니다. 마찬가지로 더 이상 지원이 제공되지 않는 경우에는 Configuration Manager의 영향 받는 버전에 대한 세부 정보를 검색합니다.

> [!IMPORTANT]  
> 중앙 관리 사이트의 데이터베이스에 대해 SQL Server Standard를 사용하는 경우에는 계층 구조가 지원할 수 있는 총 클라이언트 수를 제한합니다. [크기 조정 및 규모 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers)을 참조하세요.

### <a name="sql-server-2017-standard-enterprise"></a>SQL Server 2017: Standard, Enterprise

누적 업데이트 버전이 SQL 수명 주기에 의해 지원되는 경우 이 버전은 [누적 업데이트 버전 2](https://support.microsoft.com/help/4052574) 이상과 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 중앙 관리 사이트  
- 기본 사이트  
- 보조 사이트  
  <!--SMS.498506-->

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Standard, Enterprise  
<!--514985-->
이 버전은 SQL 수명 주기에서 지원되는 최소 서비스 팩 및 누적 업데이트와 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 중앙 관리 사이트  
- 기본 사이트  
- 보조 사이트  

### <a name="sql-server-2014-standard-enterprise"></a>SQL Server 2014: Standard, Enterprise

이 버전은 SQL 수명 주기에서 지원되는 최소 서비스 팩 및 누적 업데이트와 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 중앙 관리 사이트  
- 기본 사이트  
- 보조 사이트

### <a name="sql-server-2012-standard-enterprise"></a>SQL Server 2012: Standard, Enterprise

이 버전은 SQL 수명 주기에서 지원되는 최소 서비스 팩 및 누적 업데이트와 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 중앙 관리 사이트  
- 기본 사이트  
- 보조 사이트  

### <a name="sql-server-2017-express"></a>SQL Server 2017 Express

누적 업데이트 버전이 SQL 수명 주기에 의해 지원되는 경우 이 버전은 [누적 업데이트 버전 2](https://support.microsoft.com/help/4052574) 이상과 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 보조 사이트
<!--SMS.498506-->

### <a name="sql-server-2016-express"></a>SQL Server 2016 Express

이 버전은 SQL 수명 주기에서 지원되는 최소 서비스 팩 및 누적 업데이트와 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 보조 사이트

### <a name="sql-server-2014-express"></a>SQL Server 2014 Express

이 버전은 SQL 수명 주기에서 지원되는 최소 서비스 팩 및 누적 업데이트와 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 보조 사이트  

### <a name="sql-server-2012-express"></a>SQL Server 2012 Express

이 버전은 SQL 수명 주기에서 지원되는 최소 서비스 팩 및 누적 업데이트와 함께 사용할 수 있습니다. 이 버전의 SQL은 다음 사이트에서 사용할 수 있습니다.

- 보조 사이트  

## <a name="bkmk_SQLConfig"></a> SQL Server에 대한 필수 구성

다음 구성은 사이트 데이터베이스에 사용할 모든 SQL Server 설치(SQL Server Express 포함)에 필요합니다. Configuration Manager는 보조 사이트 설치의 일부로 SQL Server Express를 설치할 때 이러한 구성을 자동으로 만듭니다.  

### <a name="sql-server-architecture-version"></a>SQL Server 아키텍처 버전

Configuration Manager에서 사이트 데이터베이스를 호스트하려면 64비트 버전의 SQL Server가 필요합니다.  

### <a name="database-collation"></a>데이터베이스 데이터 정렬

각 사이트에서 사이트에 사용되는 SQL 서버의 인스턴스와 사이트 데이터베이스에 사용되는 SQL Server의 인스턴스는 모두 다음 데이터 정렬을 사용해야 합니다. **SQL_Latin1_General_CP1_CI_AS**.  

Configuration Manager는 중국 GB18030 표준을 위한 이 데이터 정렬의 두 가지 예외를 지원합니다. 자세한 내용은 [다국어 기능 지원](/sccm/core/plan-design/hierarchy/international-support)을 참조하세요.  

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

SQL Server Management Studio를 사용하여 SQL Server를 위한 메모리를 예약합니다. **서버 메모리 옵션**에서 **최소 서버 메모리** 설정을 설정합니다. 이 설정을 구성하는 방법에 대한 자세한 내용은 [SQL Server 메모리 서버 구성 옵션](https://docs.microsoft.com/sql/database-engine/configure-windows/server-memory-server-configuration-options)을 참조하세요.  

- **사이트 서버와 동일한 컴퓨터에 설치하는 데이터베이스 서버**: SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 50~80%로 제한합니다.  

- **사이트 서버의 원격 서버인 전용 데이터베이스 서버**: SQL Server의 메모리를 사용 가능한 주소 지정 가능 시스템 메모리의 80~90%로 제한합니다.  

- **사용 중인 각 SQL Server 인스턴스의 버퍼 풀에 대한 메모리 예약**:  

  - 중앙 관리 사이트: 최소 8GB를 설정합니다.  
  - 기본 사이트: 최소 8GB를 설정합니다.  
  - 보조 사이트: 최소 4GB를 설정합니다.  

### <a name="sql-nested-triggers"></a>SQL 중첩 트리거

SQL 중첩 트리거를 사용하도록 설정해야 합니다. 자세한 내용은 [중첩 트리거 서버 구성 옵션 구성](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option)을 참조하세요.

### <a name="sql-server-clr-integration"></a>SQL Server CLR 통합

사이트 데이터베이스를 사용하려면 SQL Server CLR(공용 언어 런타임)을 활성화해야 합니다. 이 옵션은 Configuration Manager를 설치할 때 자동으로 사용하도록 설정됩니다. CLR에 대한 자세한 내용은 [SQL Server CLR 통합 소개](https://docs.microsoft.com/dotnet/framework/data/adonet/sql/introduction-to-sql-server-clr-integration)를 참조하세요.  

### <a name="sql-server-service-broker-ssb"></a>SQL SSB(Server Service Broker)

SQL Server Service Broker는 사이트 간 복제와 단일 주 사이트에 모두 필요합니다.

### <a name="trustworthy-setting"></a>TRUSTWORTHY 설정

Configuration Manager는 SQL [TRUSTWORTHY 데이터베이스 속성](https://docs.microsoft.com/sql/relational-databases/security/trustworthy-database-property)을 자동으로 사용하도록 설정합니다. Configuration Manager가 **켜져** 있으려면 이 속성이 필요합니다.


##  <a name="bkmk_optional"></a> SQL Server에 대한 선택적 구성  
전체 SQL Server 설치를 사용하는 각 데이터베이스에 대해 필요한 경우 다음 항목을 구성할 수 있습니다.  

### <a name="sql-server-service"></a>SQL Server 서비스  
다음을 사용하여 SQL Server 서비스를 실행하도록 구성할 수 있습니다.  

- *제한된 권한의 도메인 사용자* 계정:  

  - 이 구성을 사용하는 것이 가장 좋습니다. 이때 계정의 SPN(서비스 사용자 이름)을 수동으로 등록해야 할 수 있습니다.  

- SQL Server를 실행하는 컴퓨터의**로컬 시스템** 계정:  

  - 구성 프로세스를 간단하게 수행하려면 로컬 시스템 계정을 사용합니다.  
  - 로컬 시스템 계정을 사용할 때 Configuration Manager에서는 SQL Server 서비스에 대해 SPN을 자동으로 등록합니다.  
  - SQL Server 서비스에 대해 로컬 시스템 계정을 사용하는 것이 SQL Server 모범 사례는 아닙니다.  

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

- **사이트 간 통신**은 SQL Server Service Broker를 사용하며 기본적으로 포트 TCP 4022를 사용합니다.  
- SQL Server 데이터베이스 엔진 및 다양한 Configuration Manager 사이트 시스템 역할 사이에서 **사이트 간 통신**은 기본적으로 포트 TCP 1433을 사용합니다. 다음 사이트 시스템 역할은 SQL Server 데이터베이스와 직접 통신합니다.  

  - 관리 지점  
  - SMS 공급자 컴퓨터  
  - 보고 서비스 지점  
  - 사이트 서버  

SQL Server를 실행하는 컴퓨터는 둘 이상의 사이트에 있는 데이터베이스를 호스트하는 경우 각 데이터베이스는 별도의 SQL Server 인스턴스를 사용해야 합니다. 또한 각 인스턴스는 고유 포트 집합을 사용하도록 구성해야 합니다.  

> [!WARNING]  
> Configuration Manager는 동적 포트를 지원하지 않습니다. 기본적으로 SQL Server 명명된 인스턴스는 데이터베이스 엔진에 대한 연결에 동적 포트를 사용하므로 명명된 인스턴스를 사용하는 경우 사이트 간 통신에 사용하려는 정적 포트를 수동으로 구성해야 합니다.  

SQL Server를 실행하는 컴퓨터에서 방화벽을 사용하도록 설정되어 있는 경우에는 배포에서, 그리고 SQL Server와 통신하는 여러 컴퓨터 간의 네트워크상에 있는 모든 위치에서 사용 중인 포트를 허용하도록 방화벽이 구성되어 있는지 확인해야 합니다.  

특정 포트를 사용하도록 SQL Server를 구성하는 방법에 대한 예는 [특정 TCP 포트로 수신하도록 서버 구성](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-a-server-to-listen-on-a-specific-tcp-port)을 참조하세요.  


## <a name="upgrade-options-for-sql-server"></a>SQL Server 업그레이드 옵션

SQL Server 버전을 업그레이드해야 하는 경우, 쉬운 경우부터 시작해서 복잡한 경우까지 순차적으로 다음 방법을 사용하세요.  

- [SQL Server 현재 위치 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#to-upgrade-sql-server-on-the-site-database-server)(권장)  

- SQL Server의 새 버전을 새 컴퓨터에 설치하고 Configuration Manager 설치 프로그램의 [데이터베이스 이동 옵션을 사용](/sccm/core/servers/manage/modify-your-infrastructure#bkmk_dbconfig)하여 사이트 서버가 새 SQL Server를 가리키도록 합니다.  

- [백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 사용합니다. SQL 업그레이드 시나리오에 백업 및 복구를 사용할 수 있습니다. [사이트 복구 전 고려 사항](/sccm/protect/understand/recover-sites#considerations-before-recovering-a-site)을 검토할 때 SQL 버전 관리 요구 사항을 무시할 수 있습니다.
