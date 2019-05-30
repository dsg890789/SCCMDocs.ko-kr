---
title: SQL Server Always On
titleSuffix: Configuration Manager
description: Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 계획
ms.date: 08/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f70373f1fea7928e801c0ccdbbe75cf96e54d20
ms.sourcegitcommit: f531d0a622f220739710b2fe6644ea58d024064a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/20/2019
ms.locfileid: "65933534"
---
# <a name="prepare-to-use-sql-server-always-on-availability-groups-with-configuration-manager"></a>Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager에서 SQL Server Always On 가용성 그룹을 사용할 준비를 합니다. 이 기능은 사이트 데이터베이스에 대한 고가용성 및 재해 복구 솔루션을 제공합니다.  

Configuration Manager에서는 다음의 가용성 그룹 사용을 지원합니다.
- 기본 사이트 및 중앙 관리 사이트에서
- 온-프레미스 또는 Microsoft Azure에서

Microsoft Azure에서 가용성 그룹을 사용할 경우 *Azure 가용성 집합*을 사용하여 사이트 데이터베이스의 가용성을 더 늘릴 수 있습니다. Azure 가용성 집합에 대한 자세한 내용은 [가상 컴퓨터의 가용성 관리](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)를 참조하세요.

> [!Important]
>  계속하기 전에 SQL Server 및 SQL Server 가용성 그룹의 구성 방법을 숙지하세요. 다음에 나오는 정보는 SQL Server 설명서 라이브러리 및 절차를 참조합니다.



## <a name="supported-scenarios"></a>지원되는 시나리오

Configuration Manager에서의 가용성 그룹 사용을 위해 다음 시나리오가 지원됩니다. 각 시나리오에 대한 추가 정보 및 절차를 알려면 [Configuration Manager에 대한 가용성 그룹 구성](/sccm/core/servers/deploy/configure/configure-aoag)을 참조하세요.

- [Configuration Manager에서 사용하기 위해 가용성 그룹 만들기](/sccm/core/servers/deploy/configure/configure-aoag#create-and-configure-an-availability-group)  
- [가용성 그룹을 사용하도록 사이트 구성](/sccm/core/servers/deploy/configure/configure-aoag#configure-a-site-to-use-the-database-in-the-availability-group)  
- [사이트 데이터베이스를 호스트하는 가용성 그룹에서 동기 복제 구성원 추가 또는 제거](/sccm/core/servers/deploy/configure/configure-aoag#add-and-remove-synchronous-replica-members)  
- [비동기 커밋 복제본 구성](/sccm/core/servers/deploy/configure/configure-aoag#configure-an-asynchronous-commit-repilca)  
- [비동기 커밋 복제본에서 사이트 복구](/sccm/core/servers/deploy/configure/configure-aoag#use-the-asynchronous-replica-to-recover-your-site)  
- [독립 실행형 SQL Server의 기본 또는 명명된 인스턴스로 가용성 그룹의 사이트 데이터베이스 이동](/sccm/core/servers/deploy/configure/configure-aoag#stop-using-an-availability-group)  



## <a name="prerequisites"></a>필수 구성 요소

다음과 같은 필수 구성 요소가 모든 시나리오에 적용됩니다. 추가 필수 구성 요소가 특정 시나리오에 적용될 경우 해당 시나리오와 함께 자세히 설명됩니다.   

### <a name="configuration-manager-accounts-and-permissions"></a>Configuration Manager 계정 및 권한

#### <a name="site-server-to-replica-member-access"></a>복제 구성원에 대한 사이트 서버 액세스   
사이트 서버의 컴퓨터 계정은 가용성 그룹의 구성원인 각 컴퓨터에서 **로컬 관리자** 그룹의 구성원이어야 합니다.


### <a name="sql-server"></a>SQL Server

#### <a name="version"></a>Version  
가용성 그룹의 각 복제본은 사용하는 Configuration Manager 버전에서 지원하는 SQL Server 버전을 실행해야 합니다. SQL Server에서 지원될 경우 가용성 그룹의 노드별로 다른 SQL Server 버전을 실행할 수 있습니다. 자세한 내용은 [Configuration Manager에 대한 지원되는 SQL Server 버전](/sccm/core/plan-design/configs/support-for-sql-server-versions)을 참조하세요.<!--SCCMDocs issue 656-->

#### <a name="edition"></a>버전  
SQL Server의 ‘Enterprise’ Edition을 사용합니다. 

#### <a name="account"></a>계정  
SQL Server의 각 인스턴스는 도메인 사용자 계정(**서비스 계정**) 또는 비도메인 계정에서 실행될 수 있습니다. 그룹의 각 복제본은 구성이 다를 수 있습니다. 

- 가장 낮은 사용자 권한을 가진 계정을 사용합니다. 자세한 내용은 [SQL Server 설치에 대한 보안 고려 사항](https://docs.microsoft.com/sql/sql-server/install/security-considerations-for-a-sql-server-installation)을 참조하세요.  

- SQL Server에 대한 서비스 계정 및 사용 권한에 대한 자세한 내용은 [Windows 서비스 계정 및 권한 구성](https://docs.microsoft.com/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)을 참조하세요.  

- 비도메인 계정을 사용하려면 인증서를 사용해야 합니다. 자세한 내용은 [데이터베이스 미러링 엔드포인트에 인증서 사용(Transact-SQL)](https://docs.microsoft.com/sql/database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql)을 참조하세요.  

- 자세한 내용은 [Always On 가용성 그룹에 대한 데이터베이스 미러링 엔드포인트 만들기](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell)를 참조하세요.  


### <a name="availability-group-configurations"></a>가용성 그룹 구성

#### <a name="replica-members"></a>복제본 구성원  
- 가용성 그룹에는 하나의 기본 복제본이 있어야 합니다.  

- 사용 중인 SQL Server 버전에서 지원하는 동일한 개수와 유형의 복제본을 가용성 그룹에서 사용하세요.

- 비동기 커밋 복제본을 사용하여 동기 복제본을 복구할 수 있습니다. 자세한 내용은 [사이트 데이터베이스 복구 옵션](/sccm/core/servers/manage/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption)을 참조하세요.  

    > [!Warning]  
    > Configuration Manager에서는 비동기 커밋 복제본을 사이트 데이터베이스로 사용하기 위한 *장애 조치*를 지원하지 않습니다. 자세한 내용은 [장애 조치(Failover) 및 장애 조치(Failover) 모드(Always On 가용성 그룹)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/failover-and-failover-modes-always-on-availability-groups?view=sql-server-2014)를 참조하세요.  

Configuration Manager에서는 비동기 커밋 복제본의 상태를 확인하여 최신임을 확인하지 않습니다. 비동기 커밋 복제본을 사이트 데이터베이스로 사용하면 사이트와 데이터의 무결성이 위험해질 수 있습니다. 설계 상, 이러한 복제본은 동기화되지 않을 수 있습니다. 자세한 내용은 [AlwaysOn 가용성 그룹 개요(SQL Server)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server)를 참조하세요.

각 복제 구성원에는 다음 항목이 구성되어 있어야 합니다.

- ‘기본 인스턴스’나 ‘명명된 인스턴스’를 사용합니다.    

- **주 역할의 연결** 설정은 **모든 연결 허용**입니다.  

- **읽을 수 있는 보조** 설정은 **예**입니다.  

- **수동 장애 조치**가 설정되어 있습니다.     

  > [!TIP]
  >  Configuration Manager에서는 **자동 장애 조치**로 설정된 가용성 그룹 동기 복제본을 사용할 수 있습니다. 다음의 경우 **수동 장애 조치**를 설정합니다.
  >  -  Configuration Manager 설치 프로그램을 실행하여 가용성 그룹의 사이트 데이터베이스 사용을 지정합니다.  
  >  -  Configuration Manager에 대한 업데이트를 설치합니다. (사이트 데이터베이스에 적용되는 업데이트뿐만 아님)  

#### <a name="replica-member-location"></a>복제 구성원 위치
가용성 그룹의 모든 복제본은 온-프레미스에 호스트하거나 Microsoft Azure에 호스트합니다. 온-프레미스 구성원 및 Azure의 구성원을 포함하는 그룹은 지원되지 않습니다.     

Configuration Manager 설치 프로그램은 각 복제본에 연결해야 합니다. Azure에서 가용성 그룹을 설정하고, 해당 그룹이 내부 또는 외부 부하 분산 장치 뒤에 있는 경우에는 다음의 기본 포트를 엽니다.   

- RPC 엔드포인트 매퍼: **TCP 135**   

- SQL Server Service Broker: **TCP 4022**  

- SQL over TCP: **TCP 1433**   


설치가 완료된 후에도 다음 포트는 Configuration Manager용으로 계속 열려 있어야 합니다.  

- SQL Server Service Broker: **TCP 4022**  

- SQL over TCP: **TCP 1433**  

이러한 구성에 사용자 지정 포트를 사용할 수 있습니다. 같은 사용자 지정 포트를 엔드포인트 및 가용성 그룹의 모든 복제본에서 사용하세요.


#### <a name="listener"></a>수신기   
가용성 그룹에는 *가용성 그룹 수신기*가 하나 이상 있어야 합니다. 가용성 그룹의 사이트 데이터베이스를 사용하도록 Configuration Manager를 구성하면 이 수신기의 가상 이름이 사용됩니다. 가용성 그룹에 수신기가 여러 개 포함될 수 있지만 Configuration Manager에서는 수신기를 하나만 사용할 수 있습니다. 자세한 내용은 [가용성 그룹 수신기 만들기 또는 구성(SQL Server)](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server)을 참조하세요.

#### <a name="file-paths"></a>파일 경로   
Configuration Manager 설치 프로그램을 실행하여 가용성 그룹의 데이터베이스를 사용하도록 사이트를 구성할 때 각 보조 복제본 서버에는 현재 주 복제본에 있는 사이트 데이터베이스 파일에 대한 파일 경로와 동일한 SQL Server 파일 경로가 있어야 합니다. 동일한 경로가 없는 경우 설치 프로그램에서 가용성 그룹 인스턴스를 사이트 데이터베이스의 새 위치로 추가하지 못합니다.  

로컬 SQL Server 서비스 계정에 이 폴더에 대한 **모든 권한** 이 있어야 합니다.

Configuration Manager 설치 프로그램을 사용하여 가용성 그룹에서 데이터베이스 인스턴스를 지정하는 동안에만 보조 복제본 서버에 이 파일 경로가 필요합니다. 설치 프로그램이 가용성 그룹의 사이트 데이터베이스 구성을 완료한 후 보조 복제본 서버에서 사용되지 않는 경로를 삭제할 수 있습니다.

예를 들어 다음 시나리오를 고려할 수 있습니다.

- 3개의 SQL Server를 사용하는 가용성 그룹을 만듭니다.  

- 주 복제본 서버는 SQL Server 2014의 새로운 설치입니다. 기본적으로 이 서버는 데이터베이스 .MDF 및 .LDF 파일을 `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA`에 저장합니다.  

- 보조 복제본 서버를 둘 다 이전 버전에서 SQL Server 2014로 업그레이드했습니다. 이 업그레이드로 인해 이 서버는 데이터베이스 파일을 저장할 원본 파일 경로 `C:\Program Files\Microsoft SQL Server\MSSQL10.MSSQLSERVER\MSSQL\DATA`를 유지합니다.  

- 사이트 데이터베이스를 가용성 그룹으로 이동하기 전에 각 보조 복제본 서버에서 `C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA` 파일 경로를 만듭니다. 이 경로는 보조 복제본이 이 파일 위치를 사용하지 않더라도 주 복제본에서 사용 중인 경로와 중복됩니다.  

- 그런 후 각 보조 복제본의 SQL Server 서비스 계정에 해당 서버에서 새로 생성된 파일 위치에 대한 모든 권한을 부여합니다.  

- 이제 Configuration Manager 설치 프로그램을 성공적으로 실행하여 사이트에 가용성 그룹의 사이트 데이터베이스를 사용하도록 구성할 수 있습니다.  

#### <a name="configure-the-database-on-a-new-replica"></a>새 복제본에서 데이터베이스 구성   
 다음 설정을 사용하여 각 복제본의 데이터베이스를 구성합니다.  

- **CLR 통합**을 사용합니다. 자세한 내용은 [CLR 통합](https://docs.microsoft.com/sql/relational-databases/clr-integration/clr-integration-enabling)을 참조하세요.  

- **Max text repl size**는 `2147483647`로 설정합니다.  

- 데이터베이스 소유자를 ‘SA 계정’으로 설정합니다.   

- **TRUSTWORTY** 설정을 **ON**으로 지정합니다. 자세한 내용은 [TRUSTWORTHY 데이터베이스 속성](https://docs.microsoft.com/sql/relational-databases/security/trustworthy-database-property)을 참조하세요.   

- **Service Broker**를 사용합니다.  

이러한 구성은 주 복제본에서만 수행합니다. 보조 복제본을 구성하려면 먼저 주 복제본을 보조 복제본으로 장애 조치하세요. 그러면 보조 복제본이 새 주 복제본이 됩니다.   


### <a name="verification-script"></a>확인 스크립트

다음 SQL 스크립트를 실행하여 주 및 보조 복제본에 대한 데이터베이스 구성을 확인하세요. 보조 복제본에서 문제를 해결하려면 먼저 해당 보조 복제본을 주 복제본으로 변경합니다.

```SQL
    SET NOCOUNT ON

    DECLARE @dbname NVARCHAR(128)

    SELECT @dbname = sd.name FROM sys.sysdatabases sd WHERE sd.dbid = DB_ID()

    IF (@dbname = N'master' OR @dbname = N'model' OR @dbname = N'msdb' OR @dbname = N'tempdb' OR @dbname = N'distribution' ) BEGIN
    RAISERROR(N'ERROR: Script is targetting a system database.  It should be targeting the DB you created instead.', 0, 1)
    GOTO Branch_Exit;
    END ELSE
    PRINT N'INFO: Targeted database is ' + @dbname + N'.'

    PRINT N'INFO: Running verifications....'

    IF NOT EXISTS (SELECT * FROM sys.configurations c WHERE c.name = 'clr enabled' AND c.value_in_use = 1)
    PRINT N'ERROR: CLR is not enabled!'
    ELSE
    PRINT N'PASS: CLR is enabled.'

    DECLARE @repltable TABLE (
    name nvarchar(max),
    minimum int,
    maximum int,
    config_value int,
    run_value int )

    INSERT INTO @repltable
    EXEC sp_configure 'max text repl size (B)'

    IF NOT EXISTS(SELECT * from @repltable where config_value = 2147483647 and run_value = 2147483647 )
    PRINT N'ERROR: Max text repl size is not correct!'
    ELSE
    PRINT N'PASS: Max text repl size is correct.'

    IF NOT EXISTS (SELECT db.owner_sid FROM sys.databases db WHERE db.database_id = DB_ID() AND db.owner_sid = 0x01)
    PRINT N'ERROR: Database owner is not sa account!'
    ELSE
    PRINT N'PASS: Database owner is sa account.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_trustworthy_on = 1 )
    PRINT N'ERROR: Trustworthy bit is not on!'
    ELSE
    PRINT N'PASS: Trustworthy bit is on.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_broker_enabled = 1 )
    PRINT N'ERROR: Service broker is not enabled!'
    ELSE
    PRINT N'PASS: Service broker is enabled.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_honor_broker_priority_on = 1 )
    PRINT N'ERROR: Service broker priority is not set!'
    ELSE
    PRINT N'PASS: Service broker priority is set.'

    PRINT N'Done!'

    Branch_Exit:
```



## <a name="limitations-and-known-issues"></a>제한 사항 및 알려진 문제

모든 시나리오에 적용되는 제한 사항은 다음과 같습니다.   

#### <a name="unsupported-sql-server-options-and-configurations"></a>지원되지 않는 SQL Server 옵션 및 구성

- **기본 가용성 그룹**: SQL Server 2016 Standard 버전에 도입된 기본 가용성 그룹은 보조 복제본에 대한 읽기 권한을 지원하지 않습니다. 구성하려면 이 액세스가 필요합니다. 자세한 내용은 [기본 SQL Server 가용성 그룹](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups?view=sql-server-2017)을 참조하세요.  

- **장애 조치 클러스터 인스턴스**: 장애 조치 클러스터 인스턴스는 Configuration Manager에서 사용하는 복제본에 지원되지 않습니다. 자세한 내용은 [Always On 장애 조치(failover) 클러스터 인스턴스(SQL Server)](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server)를 참조하세요.  

- **MultiSubnetFailover**: 다중 서브넷 구성에서 가용성 그룹을 Configuration Manager에 사용하는 것은 지원되지 않습니다. [MutliSubnetFailover](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server#MultiSubnetFailover) 키워드 연결 문자열도 사용할 수 없습니다.  

#### <a name="sql-servers-that-host-additional-availability-groups"></a>추가 가용성 그룹을 호스트하는 SQL Server
<!--SCCMDocs issue 649-->
SQL Server에서 Configuration Manager에 사용하는 그룹 외에도 하나 이상의 가용성 그룹을 호스트하는 경우 Configuration Manager 설치 프로그램을 실행할 때 특정 설정을 수행해야 합니다. 이 설정은 Configuration Manager에 대한 업데이트를 설치하는 데에도 필요합니다. 각 가용성 그룹의 각 복제본에는 다음 항목이 구성되어 있어야 합니다.

- 수동 장애 조치  
- 모든 읽기 전용 연결을 허용  

#### <a name="unsupported-database-use"></a>지원되지 않는 데이터베이스 사용

- **Configuration Manager에서 가용성 그룹의 사이트 데이터베이스만 지원:** SQL Server Always On 가용성 그룹의 Configuration Manager에서 지원되지 않는 데이터베이스는 다음과 같습니다.  
    - 보고 데이터베이스  
    - WSUS 데이터베이스  

- **기존 데이터베이스:** 복제본에 만든 새 데이터베이스는 사용할 수 없습니다. 가용성 그룹을 구성할 때 기존 Configuration Manager 데이터베이스의 복사본을 주 복제본으로 복원하세요.  

#### <a name="setup-errors-in-configmgrsetuplog"></a>ConfigMgrSetup.log의 설치 오류  
Configuration Manager 설치 프로그램을 실행하여 사이트 데이터베이스를 가용성 그룹으로 이동할 경우 설치 프로그램은 가용성 그룹의 보조 복제본에서 데이터베이스 역할을 처리하려고 합니다. **ConfigMgrSetup.log** 파일은 다음 오류를 표시합니다.  

`ERROR: SQL Server error: [25000][3906][Microsoft][SQL Server Native Client 11.0][SQL Server]Failed to update database "CM_AAA" because the database is read-only. Configuration Manager Setup 1/21/2016 4:54:59 PM 7344 (0x1CB0)`  

이러한 오류는 무시해도 됩니다.

#### <a name="site-expansion"></a>사이트 확장
<!--SCCMDocs issue 568-->
SQL Always On을 사용하도록 독립 실행형 기본 사이트용 사이트 데이터베이스를 구성하는 경우 중앙 관리 사이트를 포함 하도록 사이트를 확장할 수 없습니다. 이 프로세스를 시도하면 실패합니다. 사이트를 확장하려면 가용성 그룹에서 기본 사이트 데이터베이스를 일시적으로 제거하세요.



## <a name="changes-for-site-backup"></a>사이트 백업 변경 내용

### <a name="backup-database-files"></a>데이터베이스 파일 백업
  
사이트 데이터베이스가 가용성 그룹을 사용할 때에는 기본 제공된 **백업 사이트 서버** 유지 관리 작업을 실행하여 공통 Configuration Manager 설정 및 파일을 백업하세요. 해당 백업에서 생성된 .MDF 또는 .LDF 파일은 사용하면 안 됩니다. 대신, SQL Server를 사용하여 이러한 데이터베이스 파일의 직접 백업을 만듭니다.


### <a name="transaction-log"></a>트랜잭션 로그  

사이트 데이터베이스의 복구 모델은 **전체**로 설정하세요. 이 구성은 가용성 그룹에서 Configuration Manager를 사용하기 위한 요구 사항입니다. 사이트 데이터베이스 트랜잭션 로그의 크기를 모니터링하고 유지하도록 계획하세요. 전체 복구 모델에서 데이터베이스 또는 트랜잭션 로그의 전체 백업을 생성하기 전까지 트랜잭션은 확정되지 않습니다. 자세한 내용은 [SQL Server 데이터베이스의 백업 및 복원](https://docs.microsoft.com/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)을 참조하세요.



## <a name="changes-for-site-recovery"></a>사이트 복구 변경 내용

가용성 그룹의 노드 하나 이상이 여전히 작동하는 경우 사이트 복구 옵션인 **데이터베이스 복구 건너뛰기(사이트 데이터베이스가 영향을 받지 않는 경우 이 옵션 사용)** 를 사용하세요.

가용성 그룹의 모든 노드가 손실된 경우 사이트를 복구하려면 먼저 가용성 그룹을 다시 만들어야 합니다. Configuration Manager에서 가용성 노드를 다시 빌드하거나 복원할 수 없습니다. 그룹을 다시 생성하고 백업을 복원하고 SQL을 다시 구성하세요. 그런 다음 사이트 복구 옵션인 **데이터베이스 복구 건너뛰기(사이트 데이터베이스가 영향을 받지 않는 경우 이 옵션 사용)** 를 사용하세요.

자세한 내용은 [백업 및 복구](/sccm/core/servers/manage/backup-and-recovery)를 참조하세요.



## <a name="changes-for-reporting"></a>보고 변경 내용

### <a name="install-the-reporting-service-point"></a>보고 서비스 지점 설치

보고 서비스 지점은 가용성 그룹의 수신기 가상 이름 사용을 지원하지 않으며, SQL Server Always On 가용성 그룹에서의 해당 데이터베이스 호스트도 지원하지 않습니다.  

- 기본적으로 보고 서비스 지점을 설치하면 **사이트 데이터베이스 서버 이름**이 가상 이름으로 설정되며 이 이름이 수신기로 지정됩니다. 이 설정을 변경하여 가용성 그룹에 포함된 복제본의 컴퓨터 이름 및 인스턴스로 지정합니다.  

- 복제본 노드가 오프라인 상태일 때 보고 부하를 오프로드하고 가용성을 높이려면 각 복제 노드에 보고 서비스 지점을 추가로 설치해 보세요. 그런 다음 자체 컴퓨터 이름을 사용하도록 각 보고 서비스 지점을 구성합니다. 가용성 그룹의 각 복제본에 보고 서비스 지점을 설치하면 보고 기능이 항상 활성 보고 지점 서버에 연결될 수 있습니다.  


### <a name="switch-the-reporting-services-point-used-by-the-console"></a>콘솔에서 사용되는 보고 서비스 지점 전환

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다.  

2. **보고**를 확장하고 **보고서**를 선택합니다.  

3. **보고서 옵션**을 클릭합니다.  

4. [보고서 옵션] 대화 상자에서 사용할 보고 서비스 지점을 선택합니다.  



## <a name="next-steps"></a>다음 단계

이 문서에서는 가용성 그룹을 사용할 때 Configuration Manager에서 요구하는 필수 구성 요소, 제한 사항 및 일반적인 작업에 대한 변경 내용을 설명했습니다. 가용성 그룹을 사용하도록 사이트를 설정 및 구성하기 위한 절차에 대해서는 [가용성 그룹 구성](/sccm/core/servers/deploy/configure/configure-aoag)을 참조하세요.
