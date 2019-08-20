---
title: SQL 구성
titleSuffix: Configuration Manager
description: 이 다이어그램을 사용하여 Configuration Manager에 대한 SQL 구성 문제 해결을 시작합니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 95ab8cbd-0807-4422-823a-f5f9314ba623
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 515f3ef86dff0d60f16aa908759e785a4c8e4e0b
ms.sourcegitcommit: 6b5a003256305c1f0cb605e52aeaaf19c23af5a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957623"
---
# <a name="sql-configuration"></a>SQL 구성

다중 사이트 계층에서 Configuration Manager는 SQL 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

다음 다이어그램을 사용하여 SQL Service Broker 관련 SQL 구성 문제 해결을 시작합니다.

![SQL 구성 문제 해결 다이어그램](media/sql-configuration.svg)

## <a name="queries"></a>쿼리

이 다이어그램에는 다음과 같은 쿼리 및 작업이 있습니다.

### <a name="check-if-sql-can-deliver-ssb-messages"></a>SQL에서 SSB 메시지를 배달할 수 있는지 확인

```sql
SELECT transmission_status, *
FROM sys.transmission_queue
ORDER BY enqueue_time DESC
```

## <a name="remediation-actions"></a>수정 작업

### <a name="remediate-the-issues-reported-from-transmission_status"></a>transmission_status에서 보고된 이슈 수정

일반적인 문제:

- 방화벽 구성
- 네트워크 구성
- SSB 인증서가 잘못 구성됨

### <a name="run-sql-profiler-to-trace-ssb-events"></a>SQL Profiler를 실행하여 SSB 이벤트 추적

CAS 및 기본 사이트 데이터베이스에서 SQL Profiler를 실행하여 SQL Service Broker 관련 이벤트를 추적합니다.

- **Audit Broker 로그인**
- **Audit Broker 대화**
- **Broker** 범주의 이벤트
