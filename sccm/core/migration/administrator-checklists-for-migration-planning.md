---
title: "마이그레이션 검사 목록 | Microsoft 문서"
description: "관리자 검사 목록을 사용하여 System Center Configuration Manager로의 마이그레이션 전략을 계획할 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 295fdf07-93cc-490c-acdd-ce3ee88cb36f
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 238ef5814c0c1b832c28d63c9f3879e21a6c439b
ms.openlocfilehash: 285d1111502ec25b3b75a64d834b65b6898128e8


---
# <a name="administrator-checklists-for-migration-planning-in-system-center-configuration-manager"></a>System Center Configuration Manager의 마이그레이션 계획에 대한 관리자 검사 목록

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 관리자 검사 목록을 사용하여 System Center Configuration Manager로의 마이그레이션 전략을 계획할 수 있습니다.  

-   [마이그레이션 계획을 위한 관리자 검사 목록](#Checklist_Migraiton_Planning)  

-   [계층 구조 마이그레이션을 위한 관리자 검사 목록](#Checklist_Hierarchy_for_migration)  

-   [마이그레이션을 위한 관리자 검사 목록](#Checklisit_Migration)  

##  <a name="a-namechecklistmigraitonplanninga-administrator-checklist-for-migration-planning"></a><a name="Checklist_Migraiton_Planning"></a> 마이그레이션 계획을 위한 관리자 검사 목록  
 사전 마이그레이션 계획 단계에서는 다음 검사 목록을 사용하십시오.  

-   **현재 환경을 평가합니다.**  

     원본 계층에서 충족되는 기존 비즈니스 요구 사항을 확인하고 대상 계층에서도 이러한 요구 사항을 계속 충족할 수 있도록 지원하는 계획을 개발합니다.  

-   **현재 사용 중인 Configuration Manager 버전에서 사용 가능한 기능과 변경 사항을 검토하고 이러한 정보를 활용하여 대상 계층을 설계합니다.**  

    자세한 내용은 [Fundamentals of System Center Configuration Manager](../../core/understand/fundamentals.md) 및 [What's new in System Center Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)항목을 참조하세요.  


-   **역할 기반 관리에 대해 사용할 관리 보안 모델을 결정합니다.**  

    자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../core/understand/fundamentals-of-role-based-administration.md)을 참조하세요.  

-   **사용자 네트워크 및 Active Directory 토폴로지를 평가합니다.**  

    기존 도메인 구조와 네트워크 토폴로지를 검토하고 이러한 구성이 계층 설계 및 마이그레이션 작업에 어떠한 영향을 미치는지 살펴봅니다.  

-   **대상 계층 설계를 완료합니다.**  

    중앙 관리 사이트, 기본 사이트, 보조 사이트의 배치 및 콘텐츠 배포 옵션에 대해 결정합니다.  

-   **현재 계층을 대상 계층의 사이트 및 사이트 서버에 대해 사용할 컴퓨터에 매핑합니다.**  

    대상 계층의 사이트 및 사이트 시스템 서버에서 사용할 컴퓨터를 확인하고 해당 컴퓨터에 기존 및 차후의 운영 요구 사항을 충족할 수 있는 충분한 용량이 있는지 확인합니다.  

-   **개체 마이그레이션 전략을 계획합니다.**  

    사이트 경계, 컬렉션, 보급 알림 및 배포 등과 같은 여러 개체를 마이그레이션하는 마이그레이션 작업의 사용을 계획합니다. 자세한 내용은 [Plann항목에서g a Migration Job Strategy 항목에서 System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md#Types_of_Migration) 항목에서 [Plann항목에서g a migration job strategy 항목에서 System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md)을 참조하세요.  

    Configuration Manager는 선택하는 개체만 마이그레이션합니다. 마이그레이션되지 않은 개체 중 대상 계층에 필요한 개체는 대상 계층에서 다시 만들어야 합니다.  

    마이그레이션 가능한 개체는 마이그레이션 작업을 구성할 때 표시됩니다.  

-   **클라이언트 마이그레이션 전략을 계획합니다.**  

    클라이언트의 마이그레이션을 계획합니다. 여기서는 클라이언트를 대상 계층으로 마이그레이션할 때 네트워크 대역폭 및 서버 처리 요구 사항을 제한하는 제어되는 방법을 사용합니다. 클라이언트 마이그레이션 전략을 계획하는 방법에 대한 자세한 내용은 [Planning a client migration strategy in System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md)섹션을 참조하세요.  

-   **인벤토리 및 준수 데이터를 계획합니다.**  

    Configuration Manager는 하드웨어 인벤토리, 소프트웨어 인벤토리, 소프트웨어 업데이트 또는 클라이언트에 대한 원하는 구성 관리 준수 데이터 등의 마이그레이션을 지원하지 않습니다.  

    대신 클라이언트가 대상 계층의 새 사이트로 마이그레이션되고 이러한 구성에 대한 정책을 받으면 이 클라이언트에서 해당 정보를 할당된 사이트에 제출합니다. 이 작업을 통해 대상 사이트 데이터베이스는 현재 인벤토리 및 호환성 데이터로 채워집니다.  

-   **원본 계층의 마이그레이션 완료에 대해 계획합니다.**  

    개체와 클라이언트가 마이그레이션되는 시점을 결정합니다. 마이그레이션이 완료되면 원본 계층에서 사이트 서버의 역할 해제를 계획할 수 있습니다.  

##  <a name="a-namechecklisthierarchyformigrationa-administrator-checklist-for-hierarchy-migration"></a><a name="Checklist_Hierarchy_for_migration"></a> 계층 구조 마이그레이션을 위한 관리자 검사 목록  
다음 검사 목록을 참고하여 마이그레이션을 시작하기 전에 대상 계층에 대해 계획할 수 있습니다.  

-   **대상 계층에서 사용할 컴퓨터를 확인합니다.**  

    Configuration Manager는 Configuration Manager 2007 인프라에서의 현재 위치 업그레이드를 지원하지 않습니다. 대신 Configuration Manager 2007에서 System Center Configuration Manager로 데이터를 이동하는 마이그레이션을 사용합니다. 이렇게 하려면 병렬 배포를 사용하고 새 컴퓨터에 System Center Configuration Manager를 설치해야 합니다.  

    마찬가지로 다른 System Center Configuration Manager 계층 구조에서 마이그레이션할 경우 원본 계층에 대한 병렬 배포를 위해 새 대상 계층을 설치해야 합니다.  

-   **대상 계층을 만듭니다.**  

    마이그레이션을 준비하기 위해 기본 사이트를 포함하는 System Center Configuration Manager 대상 계층 구조를 설치하고 구성합니다. 예를 들면 다음과 같습니다.  

    -   중앙 관리 사이트를 설치한 다음 하나 이상의 자식 기본 사이트를 설치합니다.  

    -   중앙 관리 사이트를 사용하지 않을 경우 독립 실행형 기본 사이트를 설치합니다.  

-   **소프트웨어 업데이트와 관련된 정보를 마이그레이션하려면 대상 계층에 소프트웨어 업데이트 지점을 구성한 후 소프트웨어 업데이트를 동기화합니다.**  

    먼저 대상 계층에서 소프트웨어 업데이트를 구성 및 동기화해야 원본 계층에서 소프트웨어 업데이트 정보를 마이그레이션할 수 있습니다.  


-   **대상 계층에 추가 사이트 시스템 역할을 설치하고 구성합니다.**  

    필요한 추가 사이트 시스템 역할 및 사이트 시스템을 구성합니다.  

-   **대상 계층에서 작동 기능을 확인합니다.**  

    다음 사항을 확인합니다.  

    -   대상 계층에 여러 사이트가 있는 경우 사이트 간에 데이터베이스 복제가 작동하고 있는지 확인합니다. 데이터베이스 복제는 독립 실행형 기본 사이트에는 적용되지 않습니다.  

    -   설치된 사이트 시스템 역할이 모두 제대로 작동하는지 확인합니다.  

    -   대상 계층에 설치한 Configuration Manager 클라이언트에서 할당된 사이트와 성공적으로 통신하는지 확인합니다.  


##  <a name="a-namechecklisitmigrationa-administrator-checklist-for-migration"></a><a name="Checklisit_Migration"></a> 마이그레이션을 위한 관리자 검사 목록  
다음 검사 목록을 참고하여 원본 계층에서 대상 계층으로 데이터를 마이그레이션할 수 있습니다.  

-   **대상 계층에서 마이그레이션을 사용하도록 설정합니다.**  

    원본 계층의 최상위 사이트를 지정하여 원본 계층을 구성합니다. 원본 사이트 지정에 대한 자세한 내용은 [Planning a source hierarchy strategy in System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md)섹션을 참조하세요.  

-   **원본 계층에서 Configuration Manager 2007 SP2를 실행하는 경우 해당 원본 계층에서 추가 사이트를 선택 및 구성합니다.**  

    데이터를 수집할 Configuration Manager 2007 SP2 원본 계층 내 각 추가 사이트에 대해 데이터 수집을 위한 자격 증명을 구성해야 합니다. 데이터 수집 프로세스는 각 원본 사이트를 구성하는 즉시 시작되어 관리자가 해당 사이트에 대한 데이터 수집을 중지할 때까지 마이그레이션 기간 동안 계속 실행됩니다. 데이터 수집을 통해 원본 계층에서 이전 데이터 수집 프로세스 이후에 업데이트되거나 추가된 개체를 마이그레이션할 수 있습니다.  

    > [!NOTE]  
    >  원본 계층에서 System Center 2012 Configuration Manager 이상을 실행하면 추가 원본 사이트를 구성할 필요가 없습니다.  

-   **배포 지점 공유를 구성합니다.**  

    두 계층 간에 배포 지점을 공유하면 마이그레이션하는 개체에 대한 콘텐츠를 대상 계층의 클라이언트에서 사용할 수 있습니다. 이렇게 하면 두 계층 모두에서 각 클라이언트는 동일한 콘텐츠를 계속 사용할 수 있고 관리자는 데이터 수집을 중지하고 마이그레이션을 완료할 때까지 이 콘텐츠를 유지 관리할 수 있습니다.  

    공유 배포 지점에 대한 자세한 내용은 *Share Distribution Points Between Source and Destination Hierarchies* 항목에서 [Planning a content deployment migration strategy in System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md) 섹션을 참조하세요.  

-   **원본 계층의 클라이언트와 연결된 개체를 마이그레이션하는 마이그레이션 작업을 만들고 실행합니다.**  

    계층 간에 개체를 마이그레이션할 마이그레이션 작업을 만듭니다. 각 마이그레이션 작업에 대한 필수 구성은 어떤 데이터가 마이그레이션되는지에 따라 달라집니다.  

    예를 들어 콘텐츠를 마이그레이션하는 경우 사용 중인 마이그레이션 작업에 상관없이 해당 콘텐츠의 관리를 소유할 대상 계층 내 사이트를 할당해야 합니다. 할당된 사이트는 콘텐츠에 대한 원래의 원본 파일 위치에 액세스하며 이 콘텐츠를 대상 계층의 배포 지점에 배포하는 작업을 담당합니다.  

    자세한 내용은 [Create and Edit Migration Jobs for System Center Configuration Manager](../../core/migration/operations-for-migration.md#Create_Edit_migration_Jobs) 항목의 [Operations for migrating to System Center Configuration Manager](../../core/migration/operations-for-migration.md) 섹션을 참조하세요.  

-   **클라이언트를 대상 계층으로 마이그레이션합니다.**  

    클라이언트를 마이그레이션하는 프로세스는 각 마이그레이션 시나리오에 따라 달라집니다.  

    -   대상 계층의 버전과 다른 버전의 클라이언트를 마이그레이션할 경우 클라이언트 소프트웨어를 업그레이드해야 합니다. 업그레이드하려면 현재 Configuration Manager 클라이언트를 제거하고 그 후 대상 사이트와 일치하는 새 클라이언트 버전을 설치해야 합니다.  

    -   대상 계층의 버전과 일치하는 버전의 클라이언트를 마이그레이션할 경우 클라이언트를 업그레이드하거나 다시 설치할 필요가 없습니다. 대신 클라이언트는 대상 계층의 기본 사이트에 재할당됩니다.  

    클라이언트를 대상 계층으로 마이그레이션할 때 이 클라이언트는 이전에 같은 대상 계층으로 마이그레이션된 클라이언트 데이터와 연결됩니다.  

    자세한 내용은 [Planning a client migration strategy in System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md)항목을 참조하세요.  

-   **공유 배포 지점을 업그레이드하거나 재할당합니다.**  

    원본 계층에서 더 이상 클라이언트를 지원할 필요가 없는 경우 Configuration Manager 2007 원본 사이트에서 공유 배포 지점을 업그레이드하거나 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 원본 사이트에서 공유 배포 지점을 재할당할 수 있습니다. 배포 지점을 업그레이드하거나 재할당하면 사이트 시스템 역할이 대상 계층의 기본 사이트에 전송되고 원본 계층의 원본 사이트에서 이 배포 지점이 제거됩니다. 공유 배포 지점을 업그레이드하거나 재할당할 경우 배포 지점 컴퓨터에 콘텐츠가 남아 있으며 대상 계층의 새 배포 지점에 다시 배포할 필요가 없습니다.  

    또한 Configuration Manager 2007 보조 사이트 서버에 함께 있는 배포 지점도 업그레이드할 수 있습니다. 이렇게 하면 보조 사이트는 제거되고 대상 계층의 배포 지점만 남습니다.  

    공유 배포 지점에 대한 자세한 내용은 [Share Distribution Points Between Source and Destination Hierarchies](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) 항목에서 [Planning a content deployment migration strategy in System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md) 섹션을 참조하세요.  

-   **마이그레이션을 완료합니다.**  

    원본 계층의 모든 사이트에서 데이터와 클라이언트를 마이그레이션하고 해당되는 배포 지점을 업그레이드한 후에는 마이그레이션을 완료할 수 있습니다. 마이그레이션을 완료하려면 원본 계층의 각 원본 사이트에 대해 데이터 수집을 중지해야 합니다. 그런 다음 필요 없는 마이그레이션 정보를 제거하고 원본 계층 인프라의 역할을 해제할 수 있습니다. 자세한 내용은 [Planning to complete migration in System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md)항목을 참조하세요.  



<!--HONumber=Dec16_HO3-->


