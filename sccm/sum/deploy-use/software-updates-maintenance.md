---
title: 소프트웨어 업데이트 유지 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 업데이트를 유지 관리하려면 WSUS 정리 태스크를 예약하거나 수동으로 실행할 수 있습니다.
author: mestew
ms.date: 12/17/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
manager: dougeby
ms.author: mstewart
ms.openlocfilehash: 258c5535623c0824e49f09c556d6ffe943f96414
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827386"
---
# <a name="software-updates-maintenance"></a>소프트웨어 업데이트 유지 관리

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 콘솔의 소프트웨어 업데이트 지점 구성 요소 속성에서 WSUS 정리 작업을 예약하고 실행할 수 있습니다. WSUS 정리 작업을 처음으로 실행하도록 선택하면 다음 소프트웨어 업데이트 동기화 후에 실행됩니다.  

## <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>WSUS 정리 작업을 예약하고 실행하려면

다음 단계를 실행하여 WSUS 정리 작업을 예약합니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.
2. Configuration Manager 계층 구조의 최상위 사이트를 선택합니다.

3. **설정** 그룹에서 **사이트 구성 요소 구성** 을 클릭하고 **소프트웨어 업데이트 지점** 을 클릭하여 소프트웨어 업데이트 지점 구성 요소 속성을 엽니다.  

4. **대체 동작**을 검토합니다. 필요한 경우 동작을 수정합니다.

   ![대체 동작 스크린샷](media/supersedence-behavior.png)

5. **대체 규칙** 탭을 클릭하고, **WSUS 정리 마법사 실행**을 선택합니다. 1806 버전에서는 옵션의 이름이 **Run WSUS cleanup after synchronization**(동기화 후 WSUS 정리 실행)으로 바뀝니다.

6. **확인**을 클릭합니다(1806 버전을 실행하는 경우 **닫기** 클릭).

## <a name="wsus-cleanup-behavior-in-version-1802-and-earlier"></a>1802 및 이전 버전의 WSUS 정리 동작

Configuration Manager 1806 버전 이전의 WSUS 정리 옵션에서 실행하는 항목은 다음과 같습니다.

- 최상위 사이트의 WSUS 서버에만 있는 WSUS 정리 마법사의 **만료된 업데이트** 옵션.

  ![WSUS 만료된 업데이트 정리 스크린샷](media/wsus-cleanup-expired.PNG)

- Configuration Manager 데이터베이스의 소프트웨어 업데이트 구성 항목 정리는 7일마다 발생하고 콘솔에서 불필요한 업데이트를 제거합니다.
  - 이 정리는 현재 배포된 Configuration Manager 콘솔에서 만료된 업데이트를 제거하지 않습니다.

최상위 WSUS 데이터베이스와 환경의 다른 모든 WSUS 데이터베이스에는 추가 유지 관리가 여전히 필요합니다. 자세한 내용과 지침은 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://support.microsoft.com/help/4490644/complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maint/) 블로그 게시물을 참조하세요.

## <a name="wsus-cleanup-behavior-starting-in-version-1806"></a>1806 버전부터 시작하는 WSUS 정리 동작

1806 버전부터 WSUS 정리 옵션은 동기화를 완료할 때마다 발생하고 정리 항목을 수행합니다.
<!--1357898 -->

- CAS 및 기본 사이트의 WSUS 서버에 대한 **만료된 업데이트** 옵션
  - 보조 사이트의 WSUS 서버는 만료된 업데이트에 대해 WSUS 정리를 실행하지 않습니다.
- Configuration Manager는 데이터베이스에서 대체된 업데이트 목록을 작성합니다. 목록은 소프트웨어 업데이트 지점 구성 요소 속성의 대체 동작을 기반으로 합니다.
  - 대체 동작 조건이 충족되는 업데이트 구성 항목은 Configuration Manager 콘솔에서 만료됩니다.
  - WSUS에서 CAS 및 기본 사이트에 대한 업데이트는 거부되지만, 보조 사이트에 대한 업데이트는 거부되지 않습니다.
- Configuration Manager 데이터베이스의 소프트웨어 업데이트 구성 항목 정리는 7일마다 발생하고 콘솔에서 불필요한 업데이트를 제거합니다.
  - 이 정리는 현재 배포된 Configuration Manager 콘솔에서 만료된 업데이트를 제거하지 않습니다.

> [!NOTE]
> "Months to wait before a superseded update is expired"(대체된 업데이트가 만료되기 전에 대기할 월 수)는 대체하는 업데이트를 만든 날짜를 기반으로 합니다. 예를 들어 이 설정으로 2개월을 사용하면 대체된 업데이트가 WSUS에서 거부되고, 대체하는 업데이트가 2개월이면 Configuration Manager에서 만료됩니다.

모든 WSUS 유지 관리는 보조 사이트 WSUS 데이터베이스에서 수동으로 실행해야 합니다. CAS 및 기본 사이트에서 실행되지 않는 **WSUS 서버 정리 마법사** 옵션은 다음과 같습니다.

- 사용되지 않는 업데이트 및 업데이트 수정 버전
- 서버에 연결되지 않은 컴퓨터
- 불필요한 업데이트 파일

  자세한 내용과 지침은 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://support.microsoft.com/help/4490644/complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maint/) 블로그 게시물을 참조하세요.

## <a name="wsus-cleanup-behavior-starting-in-version-1810"></a>1810 버전부터 시작하는 WSUS 정리 동작

1810 버전부터 소프트웨어 업데이트 지점 구성 요소 속성에서 비기능 업데이트와는 별도로 기능 업데이트에 대한 대체 규칙을 지정할 수 있습니다. WSUS 정리 옵션은 동기화를 완료할 때마다 발생하고 정리 항목을 수행합니다.
<!--2839349,3098809, 2977644-->

- CAS, 기본 사이트 및 보조 사이트의 WSUS 서버에 대한 **만료된 업데이트** 옵션입니다.
- Configuration Manager는 데이터베이스에서 대체된 업데이트 목록을 작성합니다. 목록은 소프트웨어 업데이트 지점 구성 요소 속성의 대체 동작을 기반으로 합니다.
  - 대체 동작 조건이 충족되는 업데이트 구성 항목은 Configuration Manager 콘솔에서 만료됩니다.
  - WSUS에서 CAS, 기본 사이트 및 보조 사이트에 대한 업데이트가 거부됩니다.
- Configuration Manager 데이터베이스의 소프트웨어 업데이트 구성 항목 정리는 7일마다 발생하고 콘솔에서 불필요한 업데이트를 제거합니다.
  - 이 정리는 현재 배포된 Configuration Manager 콘솔에서 만료된 업데이트를 제거하지 않습니다.

> [!NOTE]
> "Months to wait before a superseded update is expired"(대체된 업데이트가 만료되기 전에 대기할 월 수)는 대체하는 업데이트를 만든 날짜를 기반으로 합니다. 예를 들어 이 설정으로 2개월을 사용하면 대체된 업데이트가 WSUS에서 거부되고, 대체하는 업데이트가 2개월이면 Configuration Manager에서 만료됩니다.

다음 **WSUS 서버 정리 마법사** 옵션은 CAS, 기본 및 보조 사이트에서 실행되지 않습니다.

- 사용되지 않는 업데이트 및 업데이트 수정 버전
- 서버에 연결되지 않은 컴퓨터
- 불필요한 업데이트 파일

  자세한 내용과 지침은 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://support.microsoft.com/help/4490644/complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maint/) 블로그 게시물을 참조하세요.

## <a name="wsus-cleanup-starting-in-version-1906"></a>WSUS 정리 버전 1906부터
<!--41101009-->

 정상 소프트웨어 업데이트 지점을 유지 관리하기 위해 Configuration Manager가 실행할 수 있는 WSUS 유지 관리 작업이 추가되었습니다. Wsus에서 만료 된 업데이트를 거부 하는 것 외에도, wsus 데이터베이스에 비클러스터형 인덱스를 추가 하 고 WSUS 데이터베이스에서 사용 되지 않는 업데이트를 제거할 수 Configuration Manager. 모든 동기화 후 WSUS 유지 관리가 발생합니다.

### <a name="add-non-clustered-indexes-to-the-wsus-database-to-improve-wsus-cleanup-performance"></a>비클러스터형 인덱스를 WSUS 데이터베이스에 추가하여 WSUS 정리 성능 개선

클러스터 되지 않은 인덱스를 추가 하면 Configuration Manager 하는 WSUS 정리 성능이 향상 됩니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.
2. Configuration Manager 계층 구조의 최상위 사이트를 선택합니다.
3. 설정 그룹에서 **사이트 구성 요소 구성**을 클릭하고 **소프트웨어 업데이트 지점**을 클릭하여 소프트웨어 업데이트 지점 구성 요소 속성을 엽니다.
4. **WSUS 유지 관리** 탭에서 **WSUS 데이터베이스에 비클러스터형 인덱스 추가**를 선택합니다.
5. Configuration Manager에서 사용하는 각 SUSDB에서 인덱스는 다음 테이블에 추가됩니다.
   - tbLocalizedPropertyForRevision
   - tbRevisionSupersedesUpdate

#### <a name="sql-permissions-for-creating-indexes"></a>인덱스를 만들기 위한 SQL 사용 권한

WSUS 데이터베이스가 원격 SQL Server인 경우 사이트 서버의 컴퓨터 계정에 다음 SQL 권한이 필요합니다.

- 인덱스를 만들려면 테이블이나 뷰에 대해 `ALTER` 권한이 있어야 합니다. 사이트 서버의 컴퓨터 계정은 `sysadmin` 고정 서버 역할 또는 `db_ddladmin` 및 `db_owner` 고정 데이터베이스 역할의 구성원이어야 합니다. 인덱스 만들기 및 권한에 대한 자세한 내용은 [인덱스 만들기(Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/create-index-transact-sql?view=sql-server-2017#permissions)를 참조하세요.
- `CONNECT SQL` 서버 권한을 사이트 서버의 컴퓨터 계정에 부여해야 합니다. 자세한 내용은 [GRANT 서버 권한(Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/grant-server-permissions-transact-sql?view=sql-server-2017)을 참조하세요. 

> [!NOTE]  
>  WSUS 데이터베이스가 기본이 아닌 포트를 사용하는 원격 SQL Server에 있으면 인덱스를 추가할 수 없습니다. 이 시나리오의 경우 [SQL Server 구성 관리자를 사용하여 서버 별칭](https://docs.microsoft.com/sql/database-engine/configure-windows/create-or-delete-a-server-alias-for-use-by-a-client?view=sql-server-2017)을 만들 수 있습니다. 별칭이 추가되고 Configuration Manager가 WSUS 데이터베이스에 연결할 수 있으면, 인덱스가 추가됩니다.

### <a name="remove-obsolete-updates-from-the-wsus-database"></a>사용되지 않는 업데이트를 WSUS 데이터베이스에서 제거

사용 되지 않는 업데이트는 WSUS 데이터베이스에서 사용 되지 않는 업데이트 및 업데이트 수정 버전입니다. 일반적으로 [Microsoft 업데이트 카탈로그](https://www.catalog.update.microsoft.com/) 에는 없는 경우 업데이트는 사용 되지 않는 것으로 간주 되 고, 필수 구성 요소 또는 종속성으로 다른 업데이트에는 필요 하지 않습니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.
2. Configuration Manager 계층 구조의 최상위 사이트를 선택합니다.
3. 설정 그룹에서 **사이트 구성 요소 구성**을 클릭하고 **소프트웨어 업데이트 지점**을 클릭하여 소프트웨어 업데이트 지점 구성 요소 속성을 엽니다.
4. **WSUS 유지 관리** 탭에서 **WSUS 데이터베이스에서 사용되지 않는 업데이트 제거**를 선택합니다.
   - 사용되지 않는 업데이트 제거는 중지되기 전까지 최대 30분 동안 실행이 허용됩니다. 다음 동기화가 발생한 후 다시 시작됩니다.  

#### <a name="sql-permissions-for-removing-obsolete-updates"></a>사용 되지 않는 업데이트 제거에 대 한 SQL 사용 권한

WSUS 데이터베이스가 원격 SQL Server인 경우 사이트 서버의 컴퓨터 계정에 다음 SQL 권한이 필요합니다.

- `db_datareader` 및 `db_datawriter` 고정 데이터베이스 역할. 자세한 내용은 [데이터베이스 수준 역할](https://docs.microsoft.com/sql/relational-databases/security/authentication-access/database-level-roles?view=sql-server-2017#fixed-database-roles)을 참조하세요.
- `CONNECT SQL` 서버 권한을 사이트 서버의 컴퓨터 계정에 부여해야 합니다. 자세한 내용은 [GRANT 서버 권한(Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/grant-server-permissions-transact-sql?view=sql-server-2017)을 참조하세요.

#### <a name="wsus-cleanup-wizard"></a>WSUS 정리 마법사

1906 버전부터 다음 **WSUS 서버 정리 마법사** 옵션은 CAS, 기본 및 보조 사이트에서 실행되지 않습니다.

- 서버에 연결되지 않은 컴퓨터
- 불필요한 업데이트 파일

  자세한 내용과 지침은 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://support.microsoft.com/help/4490644/complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maint/) 블로그 게시물을 참조하세요.


### <a name="known-issues-for-version-1906"></a>1906 버전의 알려진 문제

다음 스키마를 살펴보세요.
<!--5418148-->
- Configuration Manager 버전 1906을 사용 하 고 있습니다.
- Windows 내부 데이터베이스를 사용 하는 원격 소프트웨어 업데이트 지점이 있습니다.
- **소프트웨어 업데이트 지점 구성 요소 속성**의 **WSUS 유지 관리** 탭에서 다음 옵션 중 하나를 선택할 수 있습니다.
   - WSUS 데이터베이스에 비클러스터형 인덱스 추가
   - 사용되지 않는 업데이트를 WSUS 데이터베이스에서 제거

이 시나리오에서 Configuration Manager는 Windows 내부 데이터베이스를 사용 하 여 원격 소프트웨어 업데이트 지점의 경우 위의 WSUS 유지 관리 작업을 수행할 수 없습니다. 이 문제는 Windows 내부 데이터베이스에서 원격 연결을 허용 하지 않기 때문에 발생 합니다. 사이트 서버의 `WSyncMgr.log`에 다음과 같은 오류가 표시 됩니다.

```text
Indexing Failed. Could not connect to SUSDB.
SqlException thrown while connect to SUSDB in Server: <SUP.CONTOSO.COM>. Error Message: A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server)
...
Could not Delete Obselete Updates because ConfigManager could not connect to SUSDB: A network-related or instance-specific error occurred while establishing a connection to SQL Server. The server was not found or was not accessible. Verify that the instance name is correct and that SQL Server is configured to allow remote connections. (provider: Named Pipes Provider, error: 40 - Could not open a connection to SQL Server) UpdateServer: <SUP.CONTOSO.COM>
```

이 문제를 해결 하기 위해 Windows 내부 데이터베이스를 사용 하 여 원격 소프트웨어 업데이트 지점의 WSUS 유지 관리를 자동화할 수 있습니다. 자세한 내용과 단계는 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://support.microsoft.com/help/4490644/complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maint)를 참조하세요.

## <a name="updates-cleanup-log-entries"></a>정리 로그 항목 업데이트

이 정리를 확인하기 위해 wsyncmgr.log에서 검토할 수 있는 항목은 다음과 같습니다.

- `Cleanup processed <number> total updates and declined <number>`: 이 로그 항목이 표시되면 WSUS에서 대체된 업데이트가 거부됩니다.
- `Calling WSUS Cleanup.`: 이 항목이 표시되면 WSUS 정리가 시작됩니다.
- `Successfully completed WSUS Cleanup.`: 이 항목이 표시되면 만료된 업데이트에 대한 WSUS 정리가 완료됩니다.
- `Deleting old expired updates...`: 이 항목이 표시되면 Configuration Manager 만료된 업데이트 구성 항목 정리가 시작됩니다.
- `Deleted <number> expired updates total`: 이 항목이 표시되면 Configuration Manager 만료된 업데이트 구성 항목 정리가 완료됩니다.
