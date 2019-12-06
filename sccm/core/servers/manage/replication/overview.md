---
title: SQL 복제 문제 해결
titleSuffix: Configuration Manager
description: 이러한 다이어그램을 사용하여 Configuration Manager 사이트 간 SQL 복제를 이해하고 관련 문제를 해결할 수 있습니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 71d7430e-c5aa-485b-8dc0-c80fd8f29f17
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e4f1506ce7931fdb95a447695fbd9bf0c12146e0
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "68957803"
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

- [ConfigMgr DRS 동기화 내부](https://blogs.technet.microsoft.com/umairkhan/2019/06/01/configmgr-drs-synchronization-internals/)
- [ConfigMgr 2012 DRS(데이터 복제 서비스) 제한 해제](https://blogs.technet.microsoft.com/umairkhan/2014/02/17/configmgr-2012-data-replication-service-drs-unleashed/)
- [ConfigMgr 2012 DRS – 문제 해결 FAQ](https://blogs.technet.microsoft.com/umairkhan/2014/03/24/configmgr-2012-drs-troubleshooting-faqs/)
- [ConfigMgr 2012 DRS 초기화 내부](https://blogs.technet.microsoft.com/umairkhan/2015/01/21/configmgr-2012-drs-initialization-internals/)
- [ConfigMgr 2012: DRS 및 SQL Service Broker 인증서 이슈](https://blogs.technet.microsoft.com/umairkhan/2013/12/12/configmgr-2012-drs-and-sql-service-broker-certificate-issues/)
