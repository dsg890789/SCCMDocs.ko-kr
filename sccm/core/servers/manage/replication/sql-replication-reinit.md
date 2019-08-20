---
title: SQL 복제 다시 초기화
titleSuffix: Configuration Manager
description: 이 다이어그램을 사용하여 Configuration Manager 사이트 간 SQL 복제 다시 초기화 문제 해결을 시작합니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: ce4a1ca8-6433-4447-819f-19dd5faa6f46
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ddc80fe039745930bfd5ecbdfedc5b028849f4d4
ms.sourcegitcommit: 6b5a003256305c1f0cb605e52aeaaf19c23af5a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957633"
---
# <a name="sql-replication-reinit"></a>SQL 복제 다시 초기화

다중 사이트 계층에서 Configuration Manager는 SQL 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

다음 다이어그램을 사용하여 SQL 복제 다시 초기화 문제 해결을 시작합니다.

![SQL 복제 다시 초기화 문제 해결 다이어그램](media/sql-replication-reinit.svg)

## <a name="queries"></a>쿼리

이 다이어그램은 다음 쿼리를 사용합니다.

### <a name="check-if-site-is-in-maintenance-mode"></a>사이트가 유지 관리 모드인지 확인

```sql
SELECT * FROM ServerData
WHERE Status = 120
```

### <a name="check-which-replication-group-hasnt-completed-reinit"></a>다시 초기화를 완료하지 않은 복제 그룹 확인

```sql
SELECT * FROM RCM_DrsInitializationTracking
WHERE InitializationStatus NOT IN (6,7)
```

### <a name="check-global-data"></a>글로벌 데이터 확인

```sql
SELECT * FROM RCM_DrsInitializationTracking dt
INNER JOIN ReplicationData rg
ON dt.ReplicationGroup = rg.ReplicationGroup
WHERE dt.InitializationStatus NOT IN (6,7)
AND rg.ReplicationPattern=N'GLOBAL'
```

### <a name="check-site-data"></a>사이트 데이터 확인

```sql
SELECT * FROM RCM_DrsInitializationTracking dt
INNER JOIN ReplicationData rg
ON dt.ReplicationGroup = rg.ReplicationGroup
WHERE dt.InitializationStatus NOT IN (6,7)
AND rg.ReplicationPattern=N'Site'
```

## <a name="next-steps"></a>다음 단계

- [글로벌 데이터 다시 초기화](/sccm/core/servers/manage/replication/global-data-reinit)
- [사이트 데이터 다시 초기화](/sccm/core/servers/manage/replication/site-data-reinit)
- [SQL 구성](/sccm/core/servers/manage/replication/sql-configuration)
