---
title: 사이트 간 데이터 전송
titleSuffix: Configuration Manager
description: Configuration Manager에서 사이트 간 데이터를 이동하는 방법과 네트워크를 통해 해당 데이터의 전송을 관리할 수 있는 방법에 대해 알아봅니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: dc526e8d-fac3-4bb5-b206-03ad29b0ae11
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: e3f1d954194397d3e1c64ba108a660c351d9747a
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75800341"
---
# <a name="data-transfers-between-sites"></a>사이트 간 데이터 전송

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager는 *파일 기반 복제* 및 *데이터베이스 복제*를 사용하여 사이트 간에 여러 유형의 정보를 전송합니다. Configuration Manager에서 사이트 간 데이터를 이동하는 방법과 네트워크를 통해 해당 데이터의 전송을 관리할 수 있는 방법에 대해 알아봅니다.  

## <a name="types-of-replication"></a>복제의 유형

### <a name="a-namebkmk_fileroute--file-based-replication"></a><a name="bkmk_fileroute" /> 파일 기반 복제

Configuration Manager는 파일 기반 복제를 사용하여 계층 내의 사이트 간에 파일 기반 데이터를 전송합니다. 이 데이터에는 하위 사이트의 배포 지점에 배포하려는 애플리케이션과 패키지가 포함됩니다. 또한 사이트에서 상위 사이트로 전송한 후 처리하는 미처리 검색 데이터 기록도 처리합니다.  

자세한 내용은 [파일 기반 복제](/sccm/core/plan-design/hierarchy/file-based-replication)를 참조하세요.

### <a name="a-namebkmk_dbrep--database-replication"></a><a name="bkmk_dbrep" /> 데이터베이스 복제

Configuration Manager 데이터베이스 복제에서 SQL Server를 사용하여 데이터를 전송합니다. 이 방법을 사용하여 사이트 데이터베이스의 변경 내용을 계층의 다른 사이트에 있는 데이터베이스의 정보와 병합합니다.

자세한 내용은 [데이터베이스 복제](/sccm/core/plan-design/hierarchy/database-replication)를 참조하세요.

SQL 복제 문제 해결에 대한 도움말을 보려면 [SQL 복제 문제 해결](/sccm/core/servers/manage/replication/overview)을 참조하세요.

## <a name="see-also"></a>참고 항목

[복제 모니터링](/sccm/core/servers/manage/monitor-replication)
