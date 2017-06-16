---
title: "데이터 마이그레이션 | Microsoft 문서"
description: "원본 계층 구조에서 System Center Configuration Manager 대상 계층 구조로 데이터를 전송하는 방법을 알아봅니다."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf014eb0-f8c2-4d37-b8d7-368d63a10b89
caps.latest.revision: 11
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: a8959c72608a1531fb323176c33a848a4a669b1c
ms.openlocfilehash: dface33392c2a2a662522656eabf0936b52b28fc
ms.contentlocale: ko-kr
ms.lasthandoff: 12/30/2016


---
# <a name="migrate-data-between-hierarchies-in-system-center-configuration-manager"></a>System Center Configuration Manager의 계층 구조 간에 데이터 마이그레이션

*적용 대상: System Center Configuration Manager(현재 분기)*

마이그레이션을 사용하여 지원되는 원본 계층 구조에서 System Center Configuration Manager 대상 계층 구조로 데이터를 전송할 수 있습니다.  원본 계층 구조에서 데이터를 마이그레이션하는 경우  

-   원본 인프라에서 식별한 사이트 데이터베이스의 데이터에 액세스한 다음 현재 환경으로 해당 데이터를 전송합니다.  

-   마이그레이션을 수행할 때 원본 계층의 데이터는 변경되지 않으며 대신 데이터가 검색된 후 이 데이터의 복사본이 대상 계층의 데이터베이스에 저장됩니다.  

마이그레이션 전략을 계획할 때는 다음 사항을 고려하세요.  

-   기존 Configuration Manager 2007 SP2 인프라를 System Center Configuration Manager로 마이그레이션할 수 있습니다.  

-   지원되는 데이터 중 일부 또는 모두를 원본 사이트에서 마이그레이션할 수 있습니다.  

-   단일 원본 사이트에서 대상 계층 구조 내의 여러 사이트로 데이터를 마이그레이션할 수 있습니다.  

-   여러 원본 사이트에서 대상 계층 구조 내의 단일 사이트로 데이터를 이동할 수 있습니다.  

##  <a name="BKMK_MigrationConcepts"></a> 마이그레이션 관련 개념  
 마이그레이션을 사용할 때 다음과 같은 개념과 용어가 나올 수 있습니다.  

|개념 또는 용어|추가 정보|  
|---------------------|----------------------|  
|원본 계층|마이그레이션할 데이터를 포함하며 지원되는 Configuration Manager 버전을 실행하는 계층 구조입니다. 마이그레이션을 설정할 때 원본 계층의 최상위 사이트 지정 시 원본 계층을 확인합니다. 원본 계층을 지정하면 대상 계층의 최상위 사이트는 지정된 원본 사이트의 데이터베이스에서 데이터를 수집하여 마이그레이션할 수 있는 데이터를 확인합니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 원본 계층 전략 계획](../../core/migration/planning-a-source-hierarchy-strategy.md)에서 [원본 계층](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Hierarchies)을 참조하세요.|  
|원본 사이트|대상 계층으로 마이그레이션할 수 있는 데이터가 있는 원본 계층의 사이트입니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 원본 계층 전략 계획](../../core/migration/planning-a-source-hierarchy-strategy.md)에서 [원본 사이트](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Sites)를 참조하세요.|  
|대상 계층|원본 계층 구조에서 데이터를 가져오기 위해 마이그레이션을 실행하는 System Center Configuration Manager 계층 구조입니다.|  
|데이터 수집|원본 계층에서 대상 계층으로 마이그레이션할 수 있는 정보를 확인하는 지속적인 프로세스입니다. Configuration Manager에서는 이전에 마이그레이션했고 대상 계층 구조에서 업데이트하려는 원본 계층 구조 내 정보가 변경되었는지 확인하기 위해 일정에 따라 원본 계층 구조를 검사합니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 원본 계층 전략 계획](../../core/migration/planning-a-source-hierarchy-strategy.md)에서 [데이터 수집](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering)을 참조하세요.|  
|마이그레이션 작업|마이그레이션할 특정 개체를 구성한 다음 해당 개체를 대상 계층으로 마이그레이션하는 작업을 관리하는 프로세스입니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 마이그레이션 작업 전략 계획](../../core/migration/planning-a-migration-job-strategy.md)을 참조하세요.|  
|클라이언트 마이그레이션|클라이언트가 원본 사이트의 데이터베이스에서 사용하는 정보를 대상 계층의 데이터베이스로 전송하는 프로세스입니다. 이 데이터 마이그레이션 후에는 장치의 클라이언트 소프트웨어를 대상 계층의 클라이언트 소프트웨어로 업그레이드합니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 마이그레이션 작업 전략 계획](../../core/migration/planning-a-client-migration-strategy.md)항목을 참조하세요.|  
|공유 배포 지점|마이그레이션 기간 중 대상 계층과 공유되는 원본 계층의 배포 지점입니다.<br /><br /> 대상 계층의 사이트에 할당된 클라이언트는 마이그레이션 기간 중에 공유 배포 지점에서 콘텐츠를 가져올 수 있습니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 콘텐츠 배포 마이그레이션 전략 계획](../../core/migration/planning-a-content-deployment-migration-strategy.md)에서 [원본 계층과 대상 계층 간에 배포 지점 공유](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration)를 참조하세요.|  
|마이그레이션 모니터링|마이그레이션 작업을 모니터링하는 프로세스입니다. 마이그레이션 진행률 및 성공 여부는 **관리** 작업 영역의 **마이그레이션** 노드에서 모니터링할 수 있습니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 마이그레이션 작업 모니터링 계획](../../core/migration/planning-to-monitor-migration-activity.md)을 참조하세요.|  
|데이터 수집 중지|원본 사이트에서 데이터 수집을 중지하는 프로세스입니다. 더 이상 원본 계층에 마이그레이션할 데이터가 없거나 마이그레이션 관련 작업을 일시 중지하려는 경우 원본 계층에서 데이터 수집을 중지하도록 대상 계층을 구성할 수 있습니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 원본 계층 전략 계획](../../core/migration/planning-a-source-hierarchy-strategy.md)에서 [데이터 수집](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering)을 참조하세요.|  
|마이그레이션 데이터 정리|대상 계층 데이터베이스에서 마이그레이션에 대한 정보를 제거함으로써 원본 계층으로부터의 마이그레이션을 종료하는 프로세스입니다.<br /><br /> 자세한 내용은 [System Center Configuration Manager에서 마이그레이션 완료 계획](../../core/migration/planning-to-complete-migration.md)항목을 참조하세요.|  

## <a name="typical-workflow-for-migration"></a>일반적인 마이그레이션 워크플로  
마이그레이션 워크플로를 설정하려면:

1.  지원되는 원본 계층을 지정합니다.  

2.  데이터 수집을 설정합니다. Configuration Manager에서 데이터 수집을 통해 원본 계층 구조에서 마이그레이션할 수 있는 데이터에 대한 정보를 수집할 수 있습니다.  

     Configuration Manager의 데이터 수집 프로세스는 사용자가 중지하기 전까지 단순 일정에 따라 자동으로 반복됩니다. 기본적으로 데이터 수집 프로세스는 4시간마다 반복되므로 마이그레이션할 원본 계층 구조 내 데이터의 변경 내용을 Configuration Manager에서 확인할 수 있습니다. 데이터 수집은 원본 계층에서 대상 계층으로 배포 지점을 공유하기 위해서도 필요합니다.  

3.  원본 계층 및 대상 계층 사이에서 데이터를 마이그레이션하려면 마이그레이션 작업을 만드십시오.  

4.  데이터 수집 프로세스는 언제든지 **데이터 수집 중지** 명령을 사용하여 중지할 수 있습니다. 데이터 수집을 중지하면 Configuration Manager는 더 이상 원본 계층의 데이터 변경 내용을 확인하지 않으며 원본 계층과 대상 계층 간에 배포 지점을 공유할 수 없습니다. 일반적으로 이 작업은 원본 계층에서 더 이상 데이터를 마이그레이션하거나 배포 지점을 공유하지 않을 경우에 사용합니다.  

5.  원본 계층에 대한 모든 사이트에서 데이터 수집이 중지될 경우 필요하면 **마이그레이션 데이터 정리** 명령을 사용하여 마이그레이션 데이터를 정리할 수 있습니다. 이 명령을 실행하면 대상 계층의 데이터베이스에서 원본 계층 마이그레이션에 대한 기록 데이터가 삭제됩니다.  

현재 환경을 관리하는 데 더 이상 사용하지 않을 Configuration Manager 원본 계층에서 데이터를 마이그레이션한 후 이 원본 계층 및 인프라를 해제할 수 있습니다.  

##  <a name="BKMK_MigrationScenarios"></a> 마이그레이션 시나리오  
 Configuration Manager에서 지원하는 마이그레이션 시나리오는 다음과 같습니다.  

> [!NOTE]  
>  독립 사이트가 있는 계층 구조의 중앙 관리 사이트가 있는 계층 구조로의 확장은 마이그레이션으로 분류되지 않습니다. 계층 구조 확장에 대한 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md)에서 [독립 실행형 기본 사이트 확장](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand)을 참조하세요.  

### <a name="migration-from-configuration-manager-2007-hierarchies"></a>Configuration Manager 2007 계층 구조에서 마이그레이션  
 마이그레이션을 사용하여 Configuration Manager 2007에서 데이터를 마이그레이션하는 경우 기존 사이트 인프라에 대한 투자를 그대로 보존하고 다음과 같은 이점을 얻을 수 있습니다.  

|이점|추가 정보|  
|-------------|----------------------|  
|사이트 데이터베이스 향상|System Center Configuration Manager 데이터베이스는 전체 유니코드를 지원합니다.|  
|사이트 간 데이터베이스 복제|System Center Configuration Manager의 복제는 Microsoft SQL Server를 기반으로 합니다. 따라서 사이트 간 데이터 전송의 성능이 향상됩니다.|  
|사용자 중심 관리|사용자는 System Center Configuration Manager에서 관리 작업의 핵심입니다. 예를 들어 사용자의 장치 이름을 알지 못하더라도 해당 사용자에게 소프트웨어를 배포할 수 있습니다. 또한 System Center Configuration Manager에서 사용자는 장치에 설치되는 소프트웨어 및 이 소프트웨어가 설치되는 시점을 더 효과적으로 제어할 수 있습니다.|  
|계층 구조 단순화|System Center Configuration Manager에서는 중앙 관리 사이트 유형이 사용되며 기본 사이트와 보조 사이트의 동작이 변경되어 네트워크 대역폭을 더 적게 사용하고 필요한 서버 수도 더 적은 보다 단순한 사이트 계층 구조를 구축할 수 있습니다.|  
|역할 기반 관리|System Center Configuration Manager의 이러한 중앙 보안 모델은 관리 및 비즈니스 요구 사항을 충족하는 계층 구조 전체의 보안과 관리 기능을 제공합니다.|  

> [!NOTE]  
>  System Center 2012 Configuration Manager에서 처음 도입된 디자인 변경 때문에 Configuration Manager 2007 인프라를 System Center Configuration Manager로 업그레이드할 수 없습니다. System Center 2012 Configuration Manager에서 System Center Configuration Manager로의 현재 위치 업그레이드는 지원됩니다.  

### <a name="migration-from-configuration-manager-2012-or-another-system-center-configuration-manager-hierarchy"></a>Configuration Manager 2012 또는 다른 System Center Configuration Manager 계층 구조에서 마이그레이션  
 System Center 2012 Configuration Manager 또는 System Center Configuration Manager 계층 구조에서 데이터를 마이그레이션하는 과정은 동일합니다. 여기에는 회사가 Configuration Manager에서 이미 관리되고 있는 추가 리소스를 가져오는 경우처럼 여러 원본 계층에서 단일 대상 계층으로 데이터를 마이그레이션하는 작업이 포함됩니다. 또한 테스트 환경에서 Configuration Manager 프로덕션 환경으로 데이터를 마이그레이션할 수 있습니다. 이렇게 하면 Configuration Manager 테스트 환경에 대한 기존 투자를 보존할 수 있습니다.  

## <a name="additional-topics-for-migration"></a>마이그레이션 관련 추가 항목:  

-   [System Center Configuration Manager로 마이그레이션 계획](../../core/migration/planning-for-migration.md)  

-   [System Center Configuration Manager로 마이그레이션할 원본 계층 구조 및 원본 사이트 구성](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

-   [System Center Configuration Manager로 마이그레이션을 위한 작업](../../core/migration/operations-for-migration.md)  

-   [System Center Configuration Manager로의 마이그레이션에 대한 보안 및 개인 정보](../../core/migration/security-and-privacy-for-migration.md)  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager 사용 시작](../../core/servers/deploy/start-using.md)

