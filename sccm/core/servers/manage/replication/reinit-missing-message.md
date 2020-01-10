---
title: 누락 메시지 다시 초기화
titleSuffix: Configuration Manager
description: 이 다이어그램을 사용하여 Configuration Manager의 SQL 복제 다시 초기화에서 누락된 메시지 문제 해결을 시작할 수 있습니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 39a3001e-2df5-4b36-bd83-4f1d21dda335
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d24c35019b7a33fbe1d007817f4121fc1121b8d7
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793595"
---
# <a name="reinit-missing-message"></a>누락 메시지 다시 초기화

다중 사이트 계층에서 Configuration Manager는 SQL 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

다음 다이어그램을 사용하여 SQL 복제 다시 초기화에서 누락된 메시지 문제 해결을 시작할 수 있습니다.

![다시 초기화 누락 메시지 문제 해결 다이어그램](media/reinit-missing-message.svg)

## <a name="queries"></a>쿼리

이 다이어그램은 다음 쿼리를 사용합니다.

### <a name="check-if-site-replication-hasnt-finished-reinit"></a>사이트 복제의 다시 초기화가 완료되지 않았는지 확인

```sql
SELECT * FROM RCM_DrsInitializationTracking dt
INNER JOIN ReplicationData rg
ON dt.ReplicationGroup = rg.ReplicationGroup
WHERE dt.InitializationStatus NOT IN (6,7)
```

### <a name="get-the-trackingguid--status-from-subscriber-site"></a>구독자 사이트에서 TrackingGuid 및 상태 가져오기

```sql
SELECT RequestTrackingGUID, InitializationStatus
FROM RCM_DrsInitializationTracking dt
INNER JOIN ReplicationData rg
ON dt.ReplicationGroup = rg.ReplicationGroup
WHERE dt.InitializationStatus NOT IN (6,7)
```

### <a name="get-the-trackingguid--status-from-the-publishing-site"></a>게시 사이트에서 TrackingGuid 및 상태 가져오기

```sql
SELECT RequestTrackingGUID, InitializationStatus
FROM RCM_DrsInitializationTracking dt
WHERE RequestTrackingGUID=@trackingGuid
```

## <a name="remediation-actions"></a>수정 작업

### <a name="version-1902-and-later"></a>1902 이상 버전

이슈 및 다시 초기화를 검색하려면 [Replication Link Analyzer](/sccm/core/servers/manage/monitor-replication#BKMK_RLA)를 실행합니다.

### <a name="version-1810-and-earlier"></a>버전 1810 이하

다음 SQL 쿼리를 실행하여 `ReplicationGroupID`를 가져옵니다.

```sql
SELECT rd.ID AS ReplicationGroupID from ReplicationData rd
INNER JOIN RCM_DrsInitializationTracking it ON rd.ReplicationGroup = it.ReplicationGroup
WHERE it.RequestTrackingGUID=@trackingGuid
```

그런 후 다음 값을 사용하여 `SMS_ReplicationGroup` WMI 클래스에 대해 `InitializeData` 메서드를 사용합니다.

- ReplicationGroupID: 위의 SQL 쿼리
- SiteCode1: 부모 사이트
- SiteCode2: 자식 사이트

자세한 내용은 [클래스 SMS_ReplicationGroup의 InitializeData 메서드](/sccm/develop/reference/core/servers/configure/initializedata-method-in-class-sms_replicationgroup)를 참조하세요.

#### <a name="example"></a>예제

```PowerShell
Invoke-WmiMethod –Namespace "root\sms\site_CAS" -Class SMS_ReplicationGroup –Name InitializeData -ArgumentList "20", "CAS", "PR1"
```

## <a name="next-steps"></a>다음 단계

- [SQL 복제 다시 초기화](/sccm/core/servers/manage/replication/sql-replication-reinit)
