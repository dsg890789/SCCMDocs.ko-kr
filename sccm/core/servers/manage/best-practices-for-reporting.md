---
title: 모범 사례 보고
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 보고 기능 사용에 대한 몇 가지 유용한 팁을 참조하세요.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
author: mestew
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: f17e8ede7185892e226d576c532ad460d7cd4f32
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198407"
---
# <a name="best-practices-for-reporting-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 보고에 대한 모범 사례

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 보고에 대한 다음 모범 사례를 사용합니다.  

## <a name="for-best-performance-install-the-reporting-services-point-on-a-remote-site-system-server"></a>최고의 성능을 위해 원격 사이트 시스템 서버에 보고 서비스 지점 설치  
사이트 서버나 원격 사이트 시스템에 보고 서비스 지점을 설치할 수 있지만 원격 사이트 시스템 서버에 보고 서비스 지점을 설치하면 성능이 향상됩니다.  

## <a name="optimize-sql-server-reporting-services-queries"></a>SQL Server Reporting Services 쿼리 최적화  
일반적으로 모든 보고 지연은 쿼리를 실행하고 결과를 검색하는 데 걸리는 시간 때문에 발생합니다. Microsoft SQL Server를 사용하는 경우 Query Analyzer 및 Profiler와 같은 도구를 사용하면 쿼리를 최적화할 수 있습니다.  

## <a name="schedule-report-subscription-processing-to-run-outside-standard-office-hours"></a>보고서 구독 처리를 일반 근무 시간 외에 실행하도록 예약  
가능한 경우 보고서 구독 처리를 일반 근무 시간 외에 실행하도록 예약하여 Configuration Manager 사이트 데이터베이스 서버의 CPU 처리를 최소화합니다. 이 방법을 사용하면 예상치 못한 보고서 요청의 가용성도 향상됩니다.  

## <a name="updating-built-in-reports"></a>기본 제공 보고서 업데이트
표준 보고서를 수정하는 경우 사이트가 업데이트될 때 밑줄 접두사(`_`)를 사용하여 보고서의 이름을 바꿉니다. 이 동작은 사이트 업데이트가 표준 보고서에 의해 수정된 보고서를 덮어쓰지 않도록 합니다.

## <a name="next-steps"></a>다음 단계
[보고 구성](configuring-reporting.md)
