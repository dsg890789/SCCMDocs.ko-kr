---
title: SQL 복제
titleSuffix: Configuration Manager
description: 이 다이어그램을 사용하여 Configuration Manager 사이트 간 SQL 복제 문제 해결을 시작합니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: adb198c4-da3c-49c3-8fbd-6d1361272869
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 03c0652c88d78806f796946c8da19a455dc80f56
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793490"
---
# <a name="sql-replication"></a>SQL 복제

다중 사이트 계층에서 Configuration Manager는 SQL 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

다음 다이어그램을 사용하여 링크가 실패할 때 SQL 복제 문제 해결을 시작합니다.

![SQL 복제 문제 해결 다이어그램](media/sql-replication.svg)

## <a name="queries"></a>쿼리

이 다이어그램은 다음 쿼리를 사용합니다.

### <a name="check-if-the-replication-group-link-is-in-degraded-or-failed-state"></a>복제 그룹 링크가 저하되었거나 오류 상태인지 확인

```sql
SELECT * FROM RCM_ReplicationLinkStatus
WHERE Status IN (8, 9)
```

### <a name="check-if-replication-group-link-is-recently-calculated"></a>복제 그룹 링크가 최근에 계산되었는지 확인

```sql
DECLARE @cutoffTime DATETIME
SELECT @cutoffTime = DATEADD(minute, -30, GETUTCDATE())
SELECT * FROM RCM_ReplicationLinkStatus
WHERE UpdateTime >@cutoffTime
```

### <a name="check-sql-maintenance-mode"></a>SQL 유지 관리 모드 확인

```sql
SELECT * FROM ServerData
WHERE Status = 120
```

## <a name="next-steps"></a>다음 단계

- [SQL 복제 다시 초기화](/sccm/core/servers/manage/replication/sql-replication-reinit)
- [SQL 성능](/sccm/core/servers/manage/replication/sql-performance)
- [SQL 구성](/sccm/core/servers/manage/replication/sql-configuration)
