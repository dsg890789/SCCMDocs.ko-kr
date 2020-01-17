---
title: 마이그레이션 계획
titleSuffix: Configuration Manager
description: Configuration Manager 현재 분기 대상 계층 구조로 데이터를 마이그레이션하기 전에 사이트 및 계층에 알아봅니다.
ms.date: 01/12/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b95147faab5a1e0c8a5b244f8e101ebc3c29bea6
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75803112"
---
# <a name="plan-for-migration-to-configuration-manager-current-branch"></a>Configuration Manager 현재 분기로 마이그레이션 계획

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 현재 분기 대상 계층 구조로 데이터를 마이그레이션하기 전에 Configuration Manager의 사이트 및 계층 구조를 알고 있어야 합니다. 사이트 및 계층 구조에 대한 자세한 내용은 [Configuration Manager의 기본 사항](../../core/understand/fundamentals.md)을 참조하세요.  

대상 계층 구조로 사용할 Configuration Manager 현재 분기 계층 구조를 설치하면 지원되는 원본 계층 구조에서 데이터를 마이그레이션할 수 있습니다.  

대상 계층 구조를 설치한 후 데이터 마이그레이션을 시작하기 전에 대상 계층 구조에서 사용할 관리 기능을 설정합니다.  

그 밖에 원본 계층과 대상 계층 간에 겹치는 부분도 계획해야 할 수 있습니다. 예를 들어 원본 계층 구조가 대상 계층 구조와 동일한 네트워크 위치나 경계를 사용하도록 구성한 다음 대상 계층 구조에 새 클라이언트를 설치하고 자동 사이트 할당을 사용할 수 있습니다. 이 시나리오에서는 새로 설치한 Configuration Manager 클라이언트가 둘 중 한 계층 구조에서 가입할 사이트를 선택할 수 있으므로 클라이언트가 원본 계층 구조에 잘못 할당할 수 있습니다. 따라서 자동 사이트 할당을 사용하는 대신 해당 계층 구조의 특정 사이트에 대상 계층 구조의 새 클라이언트를 할당하도록 계획합니다.  

사이트 할당에 대한 자세한 내용은 [서로 다른 버전의 Configuration Manager 간 상호 운용성](../../core/plan-design/hierarchy/interoperability-between-different-versions.md)에서 [클라이언트 사이트 할당 고려 사항](../../core/plan-design/hierarchy/interoperability-between-different-versions.md#BKMK_SupConfigSiteAssignment)을 참조하세요.  

다음 문서를 사용하여 지원되는 원본 계층을 Configuration Manager 대상 계층으로 마이그레이션하는 방법을 계획할 수 있습니다.

-   [마이그레이션을 위한 필수 조건](../../core/migration/prerequisites-for-migration.md)  

-   [마이그레이션 계획에 대한 관리자 검사 목록](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Configuration Manager 현재 분기로 데이터를 마이그레이션할지 여부 결정](../../core/migration/determine-whether-to-migrate-data.md)  

-   [원본 계층 구조 전략 계획](../../core/migration/planning-a-source-hierarchy-strategy.md)  

-   [마이그레이션 계획에 대한 관리자 검사 목록](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [클라이언트 마이그레이션 전략 계획](../../core/migration/planning-a-client-migration-strategy.md)  

-   [콘텐츠 배포 마이그레이션 전략 계획](../../core/migration/planning-a-content-deployment-migration-strategy.md)  

-   [Configuration Manager 개체를 Configuration Manager 현재 분기로 마이그레이션하도록 계획](../../core/migration/planning-for-the-migration-of-objects.md)  

-   [마이그레이션 작업 모니터링 계획](../../core/migration/planning-to-monitor-migration-activity.md)  

-   [마이그레이션 완료 계획](../../core/migration/planning-to-complete-migration.md)  
