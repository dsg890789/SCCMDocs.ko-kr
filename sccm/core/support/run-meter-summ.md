---
title: 측정기 요약 도구 실행
titleSuffix: Configuration Manager
description: 측정기 요약 도구 실행을 사용하여 Configuration Manager에서 소프트웨어 계량 요약 작업을 트리거합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d27f88fe-817f-4af4-b290-c16f2e46cf31
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4815b308b1a4c93e3bc9271a3ec3af2f637b11cf
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39386354"
---
# <a name="run-meter-summarization-tool"></a>측정기 요약 도구 실행

*적용 대상: System Center Configuration Manager(현재 분기)*

측정기 요약 도구 실행은 [Configuration Manager 도구](/sccm/core/support/tools)에 속합니다. 이 도구를 사용하여 기본 사이트에 대한 소프트웨어 계량 요약 유지 관리 작업을 즉시 트리거합니다. 기본적으로 이러한 작업은 매일 오전 12시 이후에 시작하는 **사이트 유지 관리** 작업에 예약된 대로 실행됩니다. 

이러한 작업은 **MeterData** SQL 테이블에서 데이터를 요약하고, **FileUsageSummary** 및 **MonthlyUsageSummary** 테이블에 요약 결과를 기록합니다. 그러면 소프트웨어 계량 보고서에 요약된 결과가 표시됩니다. 기본 사이트 데이터베이스에 연결할 수 있는 모든 Configuration Manager 관리자가 이 도구를 사용하여 요약을 실행할 수 있습니다. 

이 도구는 **파일 사용량 요약** 및 **월간 사용량 요약** 소프트웨어 계량 데이터 요약 작업을 실행합니다. 이 도구는 보통 12시간의 대기 기간 없이 모든 기존의 측정기 데이터를 요약합니다. 사이트 데이터베이스를 호스트하는 SQL Server에서 이 도구를 실행합니다. 요약이 성공한 경우 종료 코드를 `0`로 설정합니다. 오류가 있는 경우 종료 코드는 `1`입니다.



## <a name="usage"></a>용도

### <a name="command-line"></a>명령줄

`runmetersumm  [sms database name]  <delay in hours for summarization <default=0>>`


### <a name="options"></a>Options

#### <a name="database-name"></a>데이터베이스 이름
SQL Server의 사이트 데이터베이스 이름.

#### <a name="delay-in-hours-for-summarization"></a>요약 지연 시간
이 도구는 지연 전에 생성된 소프트웨어 계량 사용량을 요약합니다. 기본적으로 이 지연은 0입니다.


### <a name="example"></a>예

#### <a name="summarize-the-software-metering-usage-generated-12-hours-ago"></a>12시간 전에 생성된 소프트웨어 계량 사용량 요약

`runmetersumm CCM_ABC <12>`



## <a name="see-also"></a>참고 항목

- [유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks)
- [소프트웨어 계량을 사용하여 앱 사용 현황 모니터링](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)
