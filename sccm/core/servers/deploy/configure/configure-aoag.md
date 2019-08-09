---
title: 가용성 그룹 구성
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 SQL Server Always On 가용성 그룹 설정 및 관리
ms.date: 7/19/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7e4ec207-bb49-401f-af1b-dd705ecb465d
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4cc514e37554b8238124255584f59647446baf44
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68536551"
---
# <a name="configure-sql-server-always-on-availability-groups-for-configuration-manager"></a>Configuration Manager용 SQL Server Always On 가용성 그룹 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 정보를 사용하여 Configuration Manager에서 사용하는 가용성 그룹을 구성하고 관리합니다.

시작하기 전에  

- [Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)의 정보를 충분히 이해합니다.
- 가용성 그룹의 사용과 관련 절차를 다루는 SQL Server 설명서를 잘 숙지합니다. 이 정보는 다음 시나리오를 완료하는 데 필요합니다.


## <a name="bkmk_create"></a> 가용성 그룹 만들기 및 구성

다음 절차를 사용하여 가용성 그룹을 만들고 사이트 데이터베이스의 복사본을 해당 가용성 그룹으로 이동합니다.

1. 다음 명령을 사용하여 Configuration Manager 사이트를 중지합니다.

    `preinst.exe /stopsite`

    자세한 내용은 [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 참조하세요.

2. 사이트 데이터베이스의 백업 모델을 **단순**에서 **전체**로 변경합니다.

    ```sql
    ALTER DATABASE [CM_xxx] SET RECOVERY FULL;
    ```

    가용성 그룹은 전체 백업 모델만 지원합니다. 자세한 내용은 [데이터베이스의 복구 모델 보기 또는 변경](https://docs.microsoft.com/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server)을 참조하세요.

3. SQL Server를 사용하여 사이트 데이터베이스의 전체 백업을 만듭니다. 다음 옵션 중 하나를 선택합니다.

    - **가용성 그룹의 구성원이 될 경우**: 이 서버를 가용성 그룹의 초기 기본 복제 구성원으로 사용하는 경우 사이트 데이터베이스의 복사본을 이 서버 또는 그룹의 다른 서버로 복원할 필요가 없습니다. 기본 복제본에 이미 데이터베이스가 있습니다. 이후 단계에서 SQL Server가 데이터베이스를 보조 복제본으로 복제합니다.  

    - **가용성 그룹의 구성원이 되지 않을 경우**: 그룹의 기본 복제본을 호스트하는 서버로 사이트 데이터베이스의 복사본을 복원합니다.

    자세한 내용은 SQL Server 설명서의 다음 문서를 참조하세요.

    - [전체 데이터베이스 백업 만들기](https://docs.microsoft.com/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server)
    - [SSMS를 사용하여 데이터베이스 백업 복원](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)

    > [!NOTE]  
    > 가용성 그룹에서 기본 복제본의 독립 실행형으로 이동하려는 경우 먼저 데이터베이스를 가용성 그룹에서 제거합니다.

4. 그룹의 초기 기본 복제본을 호스트하는 서버에서 [새 가용성 그룹 마법사](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio)를 사용하여 가용성 그룹을 만듭니다. 마법사에서:

    - **데이터베이스 선택** 페이지에서 Configuration Manager 사이트에 적합한 데이터베이스를 선택합니다.  

    - **복제본 지정** 페이지에서 다음을 구성합니다.

        - **복제본**: 보조 복제본을 호스팅하는 서버를 지정합니다.

        - **수신기**: **수신기 DNS 이름**을 전체 DNS 이름으로 지정합니다(예: `<listener_server>.fabrikam.com`). 가용성 그룹에서 데이터베이스를 사용하도록 Configuration Manager를 구성할 때 이 이름이 사용됩니다.

    - **초기 데이터 동기화 선택** 페이지에서 **전체**를 선택합니다. 가용성 그룹을 만든 후 마법사는 주 데이터베이스와 트랜잭션 로그를 백업합니다. 그런 후 보조 복제본을 호스트하는 각 서버에서 복원됩니다.

        > [!Note]  
        > 이 단계를 사용하지 않는 경우 사이트 데이터베이스의 복사본을 보조 복제본을 호스트하는 각 서버로 복원하세요. 그런 다음 해당 데이터베이스를 그룹에 수동으로 조인합니다.

5. 각 복제본에서 구성을 확인합니다.

    1. 사이트 서버의 컴퓨터 계정이 가용성 그룹의 구성원인 각 컴퓨터에서 로컬 **관리자** 그룹의 구성원인지 확인합니다.  

    2. [확인 스크립트](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites)를 실행하여 각 복제본의 사이트 데이터베이스가 올바르게 구성되어 있는지 확인합니다.

    3. 보조 복제본에서 구성을 설정해야 하는 경우 계속하기 전에 수동으로 기본 복제본을 보조 복제본으로 장애 조치(failover)합니다. 기본 복제본의 데이터베이스만 구성할 수 있기 때문입니다. 자세한 내용은 SQL Server 설명서의 [가용성 그룹의 계획된 수동 장애 조치(failover) 수행](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server)을 참조하세요.

6. 모든 복제본이 이러한 요구 사항을 충족할 경우 가용성 그룹을 Configuration Manager에서 사용할 수 있습니다.


## <a name="bkmk_configure"></a> 가용성 그룹 사용을 위한 사이트 구성

[가용성 그룹을 만들고 구성](#bkmk_create)한 후에 Configuration Manager 사이트 유지 관리를 사용하여 가용성 그룹이 호스트하는 데이터베이스를 사용하도록 사이트를 구성합니다.

가용성 그룹에 새 사이트를 해당 데이터베이스와 함께 설치하는 방식은 지원되지 않습니다. 예를 들어 기준 미디어를 사용하는 경우 SQL Server의 단일 인스턴스를 사용하여 사이트를 설치하세요. 사이트 설치 후 사이트 데이터베이스를 가용성 그룹으로 이동합니다.

1. Configuration Manager 사이트 설치 폴더에서 **Configuration Manager 설치 프로그램**: `\BIN\X64\setup.exe`를 실행합니다.

2. **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 선택합니다.

3. **SQL Server 구성 수정**을 선택한 후 **다음**을 선택합니다.

4. 사이트 데이터베이스의 다음 설정을 다시 구성합니다.

    - **SQL Server 이름**: 가용성 그룹 *수신기*의 가상 이름을 입력합니다. 이 수신기는 가용성 그룹을 만들 때 구성했습니다. 가상 이름은 `<Listener_Server>.fabrikam.com`과 같은 전체 DNS 이름이어야 합니다.  

    - **인스턴스:** 가용성 그룹의 *수신기* 기본 인스턴스를 지정하려면 이 값을 비워 두어야 합니다. 현재 사이트 데이터베이스가 명명된 인스턴스에서 실행되는 경우 현재 명명된 인스턴스를 제거하세요.

    - **데이터베이스:** 표시된 이름을 그대로 둡니다. 이 이름은 현재 사이트 데이터베이스의 이름입니다.

5. 새 데이터베이스 위치에 대한 정보를 제공한 후 일반적인 프로세스와 구성을 사용하여 설치 프로그램을 완료합니다.


## <a name="bkmk_sync"></a> 동기 복제본 구성원  

사이트 데이터베이스가 가용성 그룹에 호스트되는 경우 다음 절차에 따라 동기 복제 구성원을 추가하거나 제거합니다. 지원되는 복제본 유형 및 수에 대한 자세한 내용은 [가용성 그룹 구성](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#availability-group-configurations)을 참조하세요.

### <a name="bkmk_sync-add"></a> 새 동기 복제본 구성원 추가

<!--3127336-->
버전 1906부터 Configuration Manager 설치 프로그램을 실행하여 새 동기 복제본 구성원을 추가합니다.

1. [계층 구조 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 사용하여 사이트 중지: `preinst.exe /stopsite`

1. SQL Server 프로시저를 사용하여 가용성 그룹 수정:

    1. 주 복제본에서 사이트 데이터베이스의 [백업 복사본을 만듭니다](https://docs.microsoft.com/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server).

    1. [해당 백업](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)을 새 보조 복제본 서버에 복원합니다.

    1. SQL Management Studio의 상태를 확인합니다. 가용성 그룹이 정상 상태로 돌아올 때까지 기다립니다.

1. Configuration Manager 설치를 실행하고 사이트 수정 옵션을 선택합니다.

1. 가용성 그룹 수신기 이름을 데이터베이스 이름으로 지정합니다. 수신기가 비표준 네트워크 포트를 사용할 경우 함께 지정합니다. 이 작업을 통해 설치에서 각 노드가 제대로 구성되었는지 확인하게 됩니다. 또한 데이터베이스 복구 프로세스를 시작합니다.

Configuration Manager 설치 프로그램은 SQL 데이터베이스 이동 작업을 사용하며 노드가 올바르게 구성되었는지 확인합니다.

버전 1902 또는 이전 버전에서 이 프로세스를 수동으로 수행하는 자세한 방법은 [ConfigMgr 1702: 기존 SQL AO AG에 새 노드(보조 복제본) 추가](https://blogs.technet.microsoft.com/umairkhan/2017/07/17/configmgr-1702-adding-a-new-node-secondary-replica-to-an-existing-sql-ao-ag/)를 참조하세요.

### <a name="remove-a-replica-member"></a>복제본 구성원 제거

버전 1906부터 Configuration Manager 설치 프로그램을 사용하여 복제본 구성원을 제거할 수 있습니다. 같은 프로세스를 사용하여 [새 동기 복제본 구성원을 추가](#bkmk_sync-add)합니다.

버전 1902 또는 이전 버전에서 이 프로세스를 수동으로 수행하는 자세한 방법은 [가용성 그룹에서 보조 복제본 제거](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server)를 참조하세요.  


## <a name="bkmk_async"></a> 비동기 복제본

Configuration Manager에 사용하는 가용성 그룹에서 비동기 복제본을 사용할 수 있습니다. 사이트 데이터베이스에서는 비동기 복제본이 지원되지 않으므로 동기 복제본을 구성하는 데 필요한 구성 스크립트를 실행할 필요가 없습니다.

### <a name="configure-an-asynchronous-commit-replica"></a>비동기 커밋 복제본 구성

자세한 내용은 [가용성 그룹에 보조 복제본 추가](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server)를 참조하세요.

### <a name="use-the-asynchronous-replica-to-recover-your-site"></a>비동기 복제본을 사용하여 사이트 복구

비동기 복제본을 사용하여 사이트 데이터베이스를 복구합니다.

1. 사이트 데이터베이스에 대한 추가 쓰기를 방지하려면 활성 기본 사이트를 중지하세요. 사이트를 중지하려면 [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe): `preinst.exe /stopsite`를 사용합니다.

1. 사이트를 중지한 후에 [수동으로 복구된 데이터베이스](/sccm/core/servers/manage/recover-sites#use-a-site-database-that-has-been-manually-recovered) 대신 비동기 복제본을 사용하세요.


## <a name="bkmk_stop"></a> 가용성 그룹 사용 중지

더 이상 사이트 데이터베이스를 가용성 그룹에 호스트하지 않으려는 경우 다음 절차를 따르세요. 이 프로세스를 통해 사이트 데이터베이스가 SQL Server의 단일 인스턴스로 다시 이동됩니다.

1. `preinst.exe /stopsite` 명령을 사용하여 Configuration Manager 사이트를 중지합니다. 자세한 내용은 [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 참조하세요.

2. SQL Server를 사용하여 주 복제본에서 사이트 데이터베이스의 전체 백업을 만듭니다. 자세한 내용은 [전체 데이터베이스 백업 만들기](https://docs.microsoft.com/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server)를 참조하세요.

3. SQL Server를 사용하여 사이트 데이터베이스를 호스트하는 서버로 사이트 데이터베이스 백업을 복원합니다. 자세한 내용은 [SSMS를 사용하여 데이터베이스 백업 복원](https://docs.microsoft.com/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)을 참조하세요.

    > [!Note]  
    > 가용성 그룹의 주 복제본 서버에서 사이트 데이터베이스의 단일 인스턴스를 호스트할 경우 이 단계를 건너뜁니다.

4. 사이트 데이터베이스를 호스트할 서버에서 사이트 데이터베이스의 백업 모델을 **전체**에서 **단순**으로 변경합니다. 자세한 내용은 [데이터베이스의 복구 모델 보기 또는 변경](https://docs.microsoft.com/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server)을 참조하세요.

5. Configuration Manager 사이트 설치 폴더에서 **Configuration Manager 설치 프로그램**: `\BIN\X64\setup.exe`를 실행합니다.

6. **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 선택합니다.  

7. **SQL Server 구성 수정**을 선택한 후 **다음**을 선택합니다.  

8. 사이트 데이터베이스의 다음 설정을 다시 구성합니다.

    - **SQL Server 이름**: 이제 사이트 데이터베이스를 호스팅하는 서버의 이름을 입력합니다.

    - **인스턴스:** 사이트 데이터베이스를 호스트하는 명명된 인스턴스를 지정합니다. 데이터베이스가 기본 인스턴스에 있으면 이 필드를 비워 둡니다.

    - **데이터베이스:** 표시된 이름을 그대로 둡니다. 이 이름은 현재 사이트 데이터베이스의 이름입니다.

9. 새 데이터베이스 위치에 대한 정보를 제공한 후 일반적인 프로세스와 구성을 사용하여 설치 프로그램을 완료합니다. 설치가 완료되면 사이트가 다시 시작되고 새 데이터베이스 위치를 사용하기 시작합니다.

10. 가용성 그룹의 구성원이었던 서버를 정리하려면 [가용성 그룹 제거](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/remove-an-availability-group-sql-server)의 지침에 따릅니다.
