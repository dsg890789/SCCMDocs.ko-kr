---
title: SQL 복제 문제 해결
titleSuffix: Configuration Manager
description: 이러한 다이어그램을 사용하여 Configuration Manager 사이트 간 SQL 복제를 이해하고 관련 문제를 해결할 수 있습니다.
ms.date: 02/05/2020
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 71d7430e-c5aa-485b-8dc0-c80fd8f29f17
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e8c2e6cc42e8945cf1cfc20f26f3c6dae6c6c989
ms.sourcegitcommit: 5ffa00d961b5b166cd723e732e4f0fd5325d584b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/06/2020
ms.locfileid: "77051369"
---
# <a name="troubleshoot-sql-replication"></a>SQL 복제 문제 해결

다중 사이트 계층에서 Configuration Manager는 SQL 복제를 사용하여 사이트 간에 데이터를 전송합니다. 자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

SQL 복제 관련 문제를 보다 잘 이해하고 해결하려면 다음 다이어그램을 사용합니다.

- [SQL 복제](/sccm/core/servers/manage/replication/sql-replication)
- [SQL 구성](/sccm/core/servers/manage/replication/sql-configuration)
- [SQL 성능](/sccm/core/servers/manage/replication/sql-performance)
- [SQL 복제 다시 초기화](/sccm/core/servers/manage/replication/sql-replication-reinit)
- [글로벌 데이터 다시 초기화](/sccm/core/servers/manage/replication/global-data-reinit)
- [사이트 데이터 다시 초기화](/sccm/core/servers/manage/replication/site-data-reinit)
- [누락 메시지 다시 초기화](/sccm/core/servers/manage/replication/reinit-missing-message)

이러한 문제 해결 다이어그램은 상호 연결되어 있습니다. 다음 다이어그램을 사용하여 해당 관계를 이해합니다.

![SQL 복제 문제 해결 프로세스의 개요 다이어그램](media/overview.png)

<!-- PNG used instead of SVG because of weird blankspace in the SVG. The SVG file exists in the same location. -->

자세한 내용은 Microsoft 지원에서 다음 블로그 시리즈를 참조하세요.

- [ConfigMgr DRS 동기화 내부](https://techcommunity.microsoft.com/t5/configuration-manager-archive/configmgr-drs-synchronization-internals/ba-p/1154317)
- [ConfigMgr 2012 DRS(데이터 복제 서비스) 제한 해제](https://techcommunity.microsoft.com/t5/configuration-manager-archive/configmgr-2012-data-replication-service-drs-unleashed/ba-p/339916)
- [ConfigMgr 2012 DRS – 문제 해결 FAQ](https://techcommunity.microsoft.com/t5/configuration-manager-archive/configmgr-2012-drs-troubleshooting-faqs/ba-p/339934)
- [ConfigMgr 2012 DRS 초기화 내부](https://techcommunity.microsoft.com/t5/configuration-manager-archive/configmgr-2012-drs-initialization-internals/ba-p/339948)
- [ConfigMgr 2012: DRS 및 SQL Service Broker 인증서 이슈](https://techcommunity.microsoft.com/t5/configuration-manager-archive/configmgr-2012-drs-and-sql-service-broker-certificate-issues/ba-p/339910)
