---
title: 사이트 데이터 다시 초기화
titleSuffix: Configuration Manager
description: 이 다이어그램을 사용하여 Configuration Manager 계층의 사이트 데이터에 대한 SQL 복제 다시 초기화 문제 해결을 시작합니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 19741d45-2d42-438e-a9f3-15bb365d63ca
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 50d50bdc15d0aac73126c68ed2e6e79f2d0a9379
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75826274"
---
# <a name="troubleshoot-site-data-reinit"></a>사이트 데이터 다시 초기화 문제 해결

다중 사이트 계층에서 Configuration Manager는 SQL 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

다음 다이어그램을 사용하여 Configuration Manager 계층의 사이트 데이터에 대한 SQL 복제 다시 초기화 문제 해결을 시작합니다.

![사이트 데이터 다시 초기화 문제 해결 다이어그램](media/site-data-reinit.svg)

## <a name="queries"></a>쿼리

이 다이어그램은 다음 쿼리를 사용합니다.

### <a name="check-if-site-replication-hasnt-finished-reinit"></a>사이트 복제의 다시 초기화가 완료되지 않았는지 확인

```sql
SELECT * FROM RCM_DrsInitializationTracking dt
INNER JOIN ReplicationData rg
ON dt.ReplicationGroup = rg.ReplicationGroup
WHERE dt.InitializationStatus NOT IN (6,7)
AND rg.ReplicationPattern=N`Site'
```

### <a name="get-the-trackingguid--status-from-the-cas"></a>CAS에서 TrackingGuid 및 상태 가져오기

```sql
SELECT RequestTrackingGUID, InitializationStatus
FROM RCM_DrsInitializationTracking dt
INNER JOIN ReplicationData rg
ON dt.ReplicationGroup = rg.ReplicationGroup
WHERE dt.InitializationStatus NOT IN (6,7)
AND rg.ReplicationPattern=N'Site'
```

### <a name="get-the-trackingguid--status-from-the-primary-site"></a>기본 사이트에서 TrackingGuid 및 상태 가져오기

```sql
SELECT RequestTrackingGUID, InitializationStatus
FROM RCM_DrsInitializationTracking dt
WHERE RequestTrackingGUID=@trackingGuid
```

### <a name="check-primary-site-isnt-in-maintenance-mode"></a>기본 사이트가 유지 관리 모드가 아닌지 확인

```sql
SELECT * FROM ServerData
WHERE SiteStatus = 125
AND SiteCode=dbo.fnGetSiteCode()
AND ServerRole=N'Peer'
```

### <a name="check-request-status-for-the-tracking-id"></a>추적 ID의 요청 상태 확인

```sql
SELECT Status FROM RCM_InitPackageRequest
WHERE RequestTrackingGUID=@trackGuid
```

## <a name="next-steps"></a>다음 단계

- [누락 메시지 다시 초기화](/sccm/core/servers/manage/replication/reinit-missing-message)
- [글로벌 데이터 다시 초기화](/sccm/core/servers/manage/replication/global-data-reinit)
