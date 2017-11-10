---
title: SQL Server Always On
titleSuffix: Configuration Manager
description: "SCCM에서 SQL Server Always On 가용성 그룹 사용 계획"
ms.custom: na
ms.date: 09/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
caps.latest.revision: "16"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 24eaa33f1f9b333894817f089149e2cbed35df75
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="prepare-to-use-sql-server-always-on-availability-groups-with-configuration-manager"></a>Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

SQL Server Always On 가용성 그룹을 사이트 데이터베이스에 대한 고가용성 및 재해 복구 솔루션으로 사용하도록 System Center Configuration Manager를 준비합니다.  
Configuration Manager에서는 다음의 가용성 그룹 사용을 지원합니다.
-     기본 사이트 및 중앙 관리 사이트에서
-     온-프레미스 또는 Microsoft Azure에서

Microsoft Azure에서 가용성 그룹을 사용할 경우 *Azure 가용성 집합*을 사용하여 사이트 데이터베이스의 가용성을 더 늘릴 수 있습니다. Azure 가용성 집합에 대한 자세한 내용은 [가상 컴퓨터의 가용성 관리](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)를 참조하세요.

>  [!Important]   
>  계속하기 전에 SQL Server 및 SQL Server 가용성 그룹의 구성 방법을 숙지하세요. 다음에 나오는 정보는 SQL Server 설명서 라이브러리 및 절차를 참조합니다.

## <a name="supported-scenarios"></a>지원되는 시나리오
다음은 Configuration Manager에서 지원되는 가용성 그룹 사용 시나리오입니다. 각각에 대한 세부 정보 및 절차는 [Configuration Manager에 대한 가용성 그룹 구성](/sccm/core/servers/deploy/configure/configure-aoag)에서 확인할 수 있습니다 .


-      [Configuration Manager에서 사용하기 위해 가용성 그룹 만들기](/sccm/core/servers/deploy/configure/configure-aoag#create-and-configure-an-availability-group).
-     [가용성 그룹을 사용하도록 사이트 구성](/sccm/core/servers/deploy/configure/configure-aoag#configure-a-site-to-use-the-database-in-the-availability-group)
-     [사이트 데이터베이스를 호스트하는 가용성 그룹에서 동기 복제 구성원 추가 또는 제거](/sccm/core/servers/deploy/configure/configure-aoag#add-and-remove-synchronous-replica-members)
-     [비동기 커밋 복제본 구성](/sccm/core/servers/deploy/configure/configure-aoag#configure-an-asynchronous-commit-repilca)(Configuration Manager 버전 1706 이상 필요)
-     [비동기 커밋 복제본에서 사이트 복구](/sccm/core/servers/deploy/configure/configure-aoag#use-the-asynchronous-replica-to-recover-your-site)(Configuration Manager 버전 1706 이상 필요)
-     [독립 실행형 SQL Server의 기본 또는 명명된 인스턴스로 가용성 그룹의 사이트 데이터베이스 이동](/sccm/core/servers/deploy/configure/configure-aoag#stop-using-an-availability-group).


## <a name="prerequisites"></a>전제 조건
다음과 같은 필수 구성 요소가 모든 시나리오에 적용됩니다. 추가 필수 구성 요소가 특정 시나리오에 적용될 경우 해당 시나리오와 함께 자세히 설명됩니다.   

### <a name="configuration-manager-accounts-and-permissions"></a>Configuration Manager 계정 및 권한
**복제 구성원에 대한 사이트 서버 액세스:**   
사이트 서버의 컴퓨터 계정은 가용성 그룹의 구성원인 각 컴퓨터에서 **로컬 관리자** 그룹의 구성원이어야 합니다.

### <a name="sql-server"></a>SQL Server
**버전:**  
가용성 그룹의 각 복제본은 사용하는 Configuration Manager 버전에서 지원하는 SQL Server 버전을 실행해야 합니다. SQL Server에서 지원될 경우 가용성 그룹의 노드별로 다른 SQL Server 버전을 실행할 수 있습니다.

**에디션:**  
SQL Server의 *Enterprise* Edition을 사용해야 합니다.

**계정:**  
SQL Server의 각 인스턴스는 도메인 사용자 계정(**서비스 계정**) 또는 비도메인 계정에서 실행될 수 있습니다. 그룹의 각 복제본은 구성이 다를 수 있습니다. [SQL Server 모범 사례](/sql/sql-server/install/security-considerations-for-a-sql-server-installation#before-installing-includessnoversionincludesssnoversion-mdmd)에 따라, 가장 낮은 사용자 권한을 가진 계정을 사용합니다.

-   SQL Server 2016에 대한 서비스 계정 및 사용 권한을 구성하려면 MSDN의 [Windows 서비스 계정 및 권한 구성](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions)을 참조하세요.
-   비도메인 계정을 사용하려면 인증서를 사용해야 합니다. 자세한 내용은 [데이터베이스 미러링 끝점에 인증서 사용(Transact SQL)](https://docs.microsoft.com/sql/database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql)을 참조하세요.


자세한 내용은 [Always On 가용성 그룹에 대한 데이터베이스 미러링 끝점 만들기](/sql/database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell)를 참조하세요.

### <a name="availability-group-configurations"></a>가용성 그룹 구성
**복제 구성원:**  
-   가용성 그룹에는 하나의 기본 복제본이 있어야 합니다.
-   버전 1706 이전에서는 최대 2개의 동기 보조 복제본을 사용할 수 있습니다.
-   버전 1706부터 사용 중인 SQL Server 버전에서 지원하는 것과 같은 개수 및 유형의 복제본을 가용성 그룹에서 사용할 수 있습니다.

-   버전 1706부터는 비동기 커밋 복제본을 사용하여 동기 복제본을 복구할 수 있습니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 백업 및 복구 항목에서 [사이트 데이터베이스 복구 옵션]( /sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption)을 참조하세요.
    > [!CAUTION]  
    > Configuration Manager에서는 비동기 커밋 복제본을 사이트 데이터베이스로 사용하기 위한 장애 조치를 지원하지 않습니다.
Configuration Manager는 비동기 커밋 복제본의 상태가 현재 상태인지 확인하지 않으며 [의도적으로 이러한 복제본은 동기화되지 않을 수 있으므로]( https://msdn.microsoft.com/library/ff877884(SQL.120).aspx(d=robot)#Availability%20Modes) 비동기 커밋 복제본을 사이트 데이터베이스로 사용하면 사이트와 데이터의 무결성이 손상될 수 있습니다.

각 복제 구성원은 다음을 수행해야 합니다.
-   **기본 인스턴스**를 사용해야 합니다.  
    *버전 1702부터* ***명명된 인스턴스***를 사용할 수 있습니다.

-     **주 역할의 연결**을 **예**로 설정합니다.
-     **읽기 가능한 보조**를 **예**로 설정합니다.  
-     **수동 장애 조치**가 설정되어야 합니다.      

    >  [!TIP]
    >  Configuration Manager에서는 **자동 장애 조치**로 설정된 가용성 그룹 동기 복제본을 사용할 수 있습니다. 그러나 다음 경우에는 **수동 장애 조치**를 설정해야 합니다.
    >  -  설치 프로그램을 실행하여 가용성 그룹의 사이트 데이터베이스 사용을 지정합니다.
    >  -  Configuration Manager에 모든 업데이트를 설치합니다(사이트 데이터베이스에 적용되는 업데이트만이 아님).  

**복제 구성원 위치:**  
가용성 그룹의 모든 복제본은 온-프레미스에 호스트되거나 Microsoft Azure에 호스트되어야 합니다. 온-프레미스 구성원 및 Azure의 구성원을 포함하는 그룹은 지원되지 않습니다.     

Azure에서 가용성 그룹을 설정하고, 해당 그룹이 내부 또는 외부 부하 분산 장치 뒤에 있는 경우 설치 프로그램이 각 복제본에 액세스할 수 있도록 하기 위해 열어야 하는 기본 포트는 다음과 같습니다.   

-     RPC 끝점 매퍼 - **TCP 135**   
-     서버 메시지 블록 – **TCP 445**  
    *데이터베이스 이동을 완료한 후 이 포트를 제거할 수 있습니다. 버전 1702부터는 이 포트가 더 이상 필요하지 않습니다.*
-     SQL Server Service Broker -  **TCP 4022**
-     SQL over TCP – **TCP 1433**   

설치가 완료된 후에도 다음 포트에는 계속 액세스할 수 있어야 합니다.
-     SQL Server Service Broker -  **TCP 4022**
-     SQL over TCP – **TCP 1433**

버전 1702부터 이러한 구성에 사용자 지정 포트를 사용할 수 있습니다. 같은 포트를 끝점 및 가용성 그룹의 모든 복제본에서 사용해야 합니다.


**수신기:**   
가용성 그룹에는 **가용성 그룹 수신기**가 하나 이상 있어야 합니다. 이 수신기의 가상 이름은 가용성 그룹의 사이트 데이터베이스를 사용하도록 Configuration Manager를 구성할 때 사용됩니다. 가용성 그룹에 수신기가 여러 개 포함될 수 있지만 Configuration Manager에서는 수신기를 하나만 사용할 수 있습니다. 자세한 내용은 [가용성 그룹 수신기 만들기 또는 구성(SQL Server)](/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server)을 참조하세요.

**파일 경로:**   
Configuration Manager 설치 프로그램을 실행하여 가용성 그룹의 데이터베이스를 사용하도록 사이트를 구성할 때 각 보조 복제본 서버에는 현재 기본 복제본에 있는 사이트 데이터베이스 파일에 대한 파일 경로와 동일한 SQL Server 파일 경로가 있어야 합니다.
-   동일한 경로가 없는 경우 설치 프로그램에서 가용성 그룹 인스턴스를 사이트 데이터베이스의 새 위치로 추가하지 못합니다.
-   또한 로컬 SQL Server 서비스 계정에 이 폴더에 대한 **모든 권한** 이 있어야 합니다.

설치 프로그램을 사용하여 가용성 그룹에서 데이터베이스 인스턴스를 지정하는 동안에만 보조 복제본 서버에 이 파일 경로가 필요합니다. 설치 프로그램이 가용성 그룹의 사이트 데이터베이스 구성을 완료한 후 보조 데이터베이스에서 사용되지 않는 경로를 삭제할 수 있습니다.

예를 들어 다음 시나리오를 고려할 수 있습니다.
-   3개의 SQL Server를 사용하는 가용성 그룹을 만듭니다.

-   주 복제본 서버는 SQL Server 2014의 새로운 설치입니다. 기본적으로 데이터베이스 .MDF 및 .LDF 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA에 저장됩니다.

-   보조 복제본 서버 둘 다를 이전 버전에서 SQL Server 2014로 업그레이드하고 데이터베이스 파일을 저장하는 원래 파일 경로인 C:\Program Files\Microsoft SQL Server\MSSQL10.MSSQLSERVER\MSSQL\DATA를 유지합니다.

-   이 가용성 그룹으로 사이트 데이터베이스를 이동하기 전에 각 보조 복제본 서버에서 보조 복제본이 다음 파일 위치를 사용하지 않는 경우에도 다음 파일 경로를 만들어야 합니다. C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA(주 복제본에서 사용되는 경로와 동일함)

-   그런 후 각 보조 복제본의 SQL Server 서비스 계정에 해당 서버에서 새로 생성된 파일 위치에 대한 모든 권한을 부여합니다.

-   이제 Configuration Manager 설치 프로그램을 성공적으로 실행하여 사이트에 가용성 그룹의 사이트 데이터베이스를 사용하도록 구성할 수 있습니다.

**새 복제본에서 데이터베이스 구성:**   
 각 복제본의 데이터베이스를 다음과 같이 설정해야 합니다.
-   **CLR 통합**은 *사용*으로 설정해야 합니다.
-     **Max text repl size**는 *2147483647*이어야 합니다.
-     데이터베이스 소유자는 *SA 계정*이어야 합니다.
-     **신뢰**는 **설정**이어야 합니다.
-     **Service Broker**는 *사용*이어야 합니다.

이러한 구성은 기본 복제본에서만 수행할 수 있습니다. 보조 복제본을 구성하려면 먼저 기본 복제본을 보조 복제본으로 장애 조치하여 보조 복제본을 새로운 기본 복제본으로 만들어야 합니다.   

설정을 구성하는 데 도움이 필요한 경우 SQL Server 설명서를 사용합니다. 예를 들어 SQL Server 설명서에서 [신뢰](/sql/relational-databases/security/trustworthy-database-property) 또는 [CLR 통합](/sql/relational-databases/clr-integration/clr-integration-enabling) 있습니다.

### <a name="verification-script"></a>확인 스크립트
다음 스크립트를 실행하여 기본 및 보조 복제본에 대한 데이터베이스 구성을 확인할 수 있습니다. 보조 복제본에서 문제를 해결하려면 먼저 해당 보조 복제본을 기본 복제본으로 변경해야 합니다.

    SET NOCOUNT ON

    DECLARE @dbname NVARCHAR(128)

    SELECT @dbname = sd.name FROM sys.sysdatabases sd WHERE sd.dbid = DB_ID()

    IF (@dbname = N'master' OR @dbname = N'model' OR @dbname = N'msdb' OR @dbname = N'tempdb' OR @dbname = N'distribution' ) BEGIN
    RAISERROR(N'ERROR: Script is targetting a system database.  It should be targeting the DB you created instead.', 0, 1)
    GOTO Branch_Exit;
    END ELSE
    PRINT N'INFO: Targetted database is ' + @dbname + N'.'

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

## <a name="limitations-and-known-issues"></a>제한 사항 및 알려진 문제
모든 시나리오에 적용되는 제한 사항은 다음과 같습니다.   

**지원되지 않는 SQL Server 옵션 및 구성:**
- **기본 가용성 그룹**  
  SQL Server 2016 Standard Edition에 도입된 [기본 가용성 그룹](https://msdn.microsoft.com/library/mt614935.aspx)은 Configuration Manager에서 사용하기 위한 요구 사항인 보조 복제본에 대한 읽기 액세스를 지원하지 않습니다.
- **장애 조치 클러스터 인스턴스**  
  [장애 조치 클러스터 인스턴스](/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server)는 Configuration Manager에서 사용하는 복제본에 지원되지 않습니다.

**추가 가용성 그룹을 호스트하는 SQL Server:**   
Configuration Manager 버전 1610 이전에서는 SQL Server의 가용성 그룹이 Configuration Manager에 사용하는 그룹 외에, 하나 이상의 가용성 그룹을 호스트할 경우 이러한 추가 가용성 그룹의 각 복제본은 Configuration Manager 설치 프로그램을 실행하거나 Configuration Manager 업데이트를 설치할 때 다음과 같은 구성이 설정되어 있어야 합니다.
-   **수동 장애 조치**
-   **모든 읽기 전용 연결을 허용**

**지원되지 않는 데이터베이스 사용:**
-   **Configuration Manager는 가용성 그룹에서 사이트 데이터베이스에만 지원합니다.** 다음은 지원되지 않습니다.
    -   보고 데이터베이스
    -   WSUS 데이터베이스
-   **기존 데이터베이스:** 복제본에 만든 새 데이터베이스는 사용할 수 없습니다. 대신, 가용성 그룹을 구성할 때 기존 Configuration Manager 데이터베이스의 복사본을 주 복제본으로 복원해야 합니다.

**ConfigMgrSetup.log의 설치 오류:**  
설치 프로그램을 실행하여 사이트 데이터베이스를 가용성 그룹으로 이동할 경우 설치 프로그램은 가용성 그룹의 보조 복제본에서 데이터베이스 역할을 처리하려고 하며 다음과 같은 오류를 로깅합니다.
-   오류: SQL Server 오류: [25000][3906][Microsoft][SQL Server Native Client 11.0] [SQL Server] 데이터베이스 "CM_AAA"은(는) 읽기 전용이므로 업데이트할 수 없습니다. Configuration Manager Setup 1/21/2016 4:54:59 PM 7344 (0x1CB0)  

이러한 오류는 무시해도 됩니다.

## <a name="changes-for-site-backup"></a>사이트 백업 변경 내용
**데이터베이스 파일 백업:**  
사이트 데이터베이스가 가용성 그룹에서 실행될 때 기본 제공된 **백업 사이트** 서버 유지 관리 작업을 실행하여 공통 Configuration Manager 설정 및 파일을 백업해야 합니다. 그렇지만 해당 백업에서 생성된 .MDF 또는 .LDF 파일은 사용하지 않도록 합니다. 대신, SQL Server를 사용하여 이러한 데이터베이스 파일의 직접 백업을 만듭니다.

**트랜잭션 로그:**  
사이트 데이터베이스의 복구 모델을 **전체**(가용성 그룹에서 사용하는 데 필요)로 설정해야 합니다. 이 구성을 사용하는 경우 사이트 데이터베이스 트랜잭션 로그의 크기를 모니터링하고 유지하도록 계획합니다. 전체 복구 모델에서 데이터베이스 또는 트랜잭션 로그의 전체 백업이 생성될 때까지 트랜잭션은 확정되지 않습니다. 자세한 내용은 SQL Server 설명서의 [SQL Server 데이터베이스의 백업 및 복원](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases)을 참조하세요.

## <a name="changes-for-site-recovery"></a>사이트 복구 변경 내용
가용성 그룹의 노드 하나 이상이 계속 작동하는 경우 사이트 복구 옵션인 **데이터베이스 복구 건너뛰기(사이트 데이터베이스가 영향을 받지 않는 경우 이 옵션 사용)**를 사용할 수 있습니다.

 가용성 그룹의 모든 노드가 손실된 경우 사이트를 복구하려면 먼저 가용성 그룹을 다시 만들어야 합니다. Configuration Manager에서 가용성 노드를 다시 작성하거나 복원할 수 없습니다. 백업을 복원하고 다시 구성하여 그룹을 다시 만든 후 사이트 복구 옵션인 **데이터베이스 복구 건너뛰기(사이트 데이터베이스가 영향을 받지 않는 경우 이 옵션 사용)**를 사용할 수 있습니다.

자세한 내용은 [System Center Configuration Manager 백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 참조하세요.

## <a name="changes-for-reporting"></a>보고 변경 내용
**보고 서비스 지점 설치:**  
보고 서비스 지점에서는 가용성 그룹의 수신기 가상 이름을 사용할 수 없고 SQL Server Always On 가용성 그룹에 보고 서비스 데이터베이스를 호스트할 수 없습니다.
-   기본적으로 보고 서비스 지점을 설치하면 **사이트 데이터베이스 서버 이름**이 가상 이름으로 설정되며 이 이름이 수신기로 지정됩니다. 이 이름을 변경하여 가용성 그룹에 포함된 복제본의 컴퓨터 이름 및 인스턴스로 지정합니다.
-   복제본 노드가 오프라인 상태일 때 보고 부하를 오프로드하고 가용성을 높이려면 각 복제 노드에 보고 서비스 지점을 추가로 설치하고 각 보고 서비스 지점이 자체 컴퓨터 이름에 가리키도록 구성하는 것이 좋습니다.

가용성 그룹의 각 복제본에 보고 서비스 지점을 설치하면 보고 기능이 항상 활성 보고 지점 서버에 연결될 수 있습니다.

**콘솔에서 사용되는 보고 서비스 지점 전환:**  
보고서를 실행하려면 콘솔에서 **모니터링** > **개요** > **보고** > **보고서**로 이동한 후 **보고서 옵션**을 선택합니다. 보고서 옵션 대화 상자에서 원하는 보고 서비스 지점을 선택합니다.

## <a name="next-steps"></a>다음 단계
가용성 그룹을 사용할 때 필요한 필수 구성 요소, 제한 사항 및 일반 작업에 대한 변경 내용을 이해한 후에는 [Configuration Manager에 대한 가용성 그룹 구성](/sccm/core/servers/deploy/configure/configure-aoag)에서 가용성 그룹을 사용하도록 사이트를 설정 및 구성하기 위한 절차를 참조하세요.
