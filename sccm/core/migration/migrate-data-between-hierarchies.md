---
title: 데이터 마이그레이션
titleSuffix: Configuration Manager
description: 원본 계층 구조에서 Configuration Manager 대상 계층 구조로 데이터를 전송하는 방법을 알아봅니다.
ms.date: 11/05/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: cf014eb0-f8c2-4d37-b8d7-368d63a10b89
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e0c9cf9d0e1be301f43d9f48a396e7f673396e26
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75803214"
---
# <a name="migrate-data-between-hierarchies-in-configuration-manager"></a>Configuration Manager에서 계층 구조 간에 데이터 마이그레이션

*적용 대상: Configuration Manager(현재 분기)*

마이그레이션을 사용하여 지원되는 원본 계층 구조에서 Configuration Manager(현재 분기) 대상 계층 구조로 데이터를 전송합니다. 원본 계층 구조에서 데이터를 마이그레이션하는 경우  

- 원본 인프라에서 사이트 데이터베이스의 데이터에 액세스한 다음, 현재 환경으로 해당 데이터를 전송합니다.  

- 마이그레이션은 원본 계층 구조의 데이터를 변경하지 않습니다. 대신 데이터를 검색하고 복사본을 대상 계층 구조의 데이터베이스에 저장합니다.  

마이그레이션 전략을 계획할 때는 다음 사항을 고려하세요.  

- 기존 Configuration Manager 2007 SP2 인프라를 Configuration Manager(현재 분기)로 마이그레이션할 수 있습니다.  

- 지원되는 데이터 중 일부 또는 모두를 원본 사이트에서 마이그레이션할 수 있습니다.  

- 단일 원본 사이트에서 대상 계층 구조 내의 여러 사이트로 데이터를 마이그레이션할 수 있습니다.  

- 여러 원본 사이트에서 대상 계층 구조 내의 단일 사이트로 데이터를 이동할 수 있습니다.  


다음 비디오에서는 두 가지 일반적인 [마이그레이션 시나리오](#BKMK_MigrationScenarios)에 대해 설명하고 보여줍니다. 마이그레이션 계획에 Microsoft Azure를 포함할 수 있는 옵션도 포함되어 있습니다.
> [!VIDEO https://www.youtube.com/embed/6_0EwW-5b4E]



##  <a name="BKMK_MigrationConcepts"></a> 개념  

 Configuration Manager는 마이그레이션 중에 다음 개념과 용어를 사용합니다.  

#### <a name="source-hierarchy"></a>원본 계층
마이그레이션할 데이터를 포함하며 지원되는 Configuration Manager 버전을 실행하는 계층 구조입니다. 마이그레이션을 설정할 때 원본 계층의 최상위 사이트 지정 시 원본 계층을 확인합니다. 원본 계층을 지정하면 대상 계층의 최상위 사이트는 지정된 원본 사이트의 데이터베이스에서 데이터를 수집하여 마이그레이션할 수 있는 데이터를 확인합니다. 

자세한 내용은 [원본 계층 구조](/sccm/core/migration/planning-a-source-hierarchy-strategy#BKMK_Source_Hierarchies)를 참조하세요.

#### <a name="source-sites"></a>원본 사이트
대상 계층으로 마이그레이션할 수 있는 데이터가 있는 원본 계층의 사이트입니다. 

자세한 내용은 [원본 사이트](/sccm/core/migration/planning-a-source-hierarchy-strategy#BKMK_Source_Sites)를 참조하세요.

#### <a name="destination-hierarchy"></a>대상 계층
원본 계층 구조에서 데이터를 가져오기 위해 마이그레이션을 실행하는 Configuration Manager(현재 분기) 계층 구조입니다.

#### <a name="data-gathering"></a>데이터 수집
원본 계층에서 대상 계층으로 마이그레이션할 수 있는 정보를 확인하는 지속적인 프로세스입니다. Configuration Manager는 일정에 따라 원본 계층 구조를 검사합니다. 이 프로세스에서는 이전에 마이그레이션했고 대상 계층 구조에서 업데이트하려는 원본 계층 구조의 정보가 변경되었는지 확인합니다.

자세한 내용은 [데이터 수집](/sccm/core/migration/planning-a-source-hierarchy-strategy#BKMK_Data_Gathering)을 참조하세요.

#### <a name="migration-jobs"></a>마이그레이션 작업
마이그레이션할 특정 개체를 구성한 다음 해당 개체를 대상 계층으로 마이그레이션하는 작업을 관리하는 프로세스입니다.

자세한 내용은 [마이그레이션 작업 전략 계획](/sccm/core/migration/planning-a-migration-job-strategy)을 참조하세요.

#### <a name="client-migration"></a>클라이언트 마이그레이션
클라이언트가 원본 사이트의 데이터베이스에서 사용하는 정보를 대상 계층의 데이터베이스로 전송하는 프로세스입니다. 이 데이터 마이그레이션 후에는 디바이스의 클라이언트 소프트웨어를 대상 계층 구조의 클라이언트 소프트웨어 버전으로 업그레이드합니다.

자세한 내용은 [클라이언트 마이그레이션 전략 계획](/sccm/core/migration/planning-a-client-migration-strategy)을 참조하세요.

#### <a name="shared-distribution-points"></a>공유 배포 지점
마이그레이션 기간 중 Configuration Manager가 대상 계층 구조와 공유되는 원본 계층 구조의 배포 지점입니다.

대상 계층의 사이트에 할당된 클라이언트는 마이그레이션 기간 중에 공유 배포 지점에서 콘텐츠를 가져올 수 있습니다.

자세한 내용은 [원본 계층 구조와 대상 계층 구조 간에 배포 지점 공유](/sccm/core/migration/planning-a-content-deployment-migration-strategy#About_Shared_DPs_in_Migration)를 참조하세요.

#### <a name="monitoring-migration"></a>마이그레이션 모니터링
마이그레이션 작업을 모니터링하는 프로세스입니다. 마이그레이션 진행률 및 성공 여부는 **관리** 작업 영역의 **마이그레이션** 노드에서 모니터링할 수 있습니다.

자세한 내용은 [마이그레이션 작업 모니터링 계획](/sccm/core/migration/planning-to-monitor-migration-activity)을 참조하세요.

#### <a name="stop-gathering-data"></a>데이터 수집 중지
원본 사이트에서 데이터 수집을 중지하는 프로세스입니다. 더 이상 원본 계층에 마이그레이션할 데이터가 없거나 마이그레이션 관련 작업을 일시 중지하려는 경우 원본 계층에서 데이터 수집을 중지하도록 대상 계층을 구성할 수 있습니다.

자세한 내용은 [데이터 수집](/sccm/core/migration/planning-a-source-hierarchy-strategy#BKMK_Data_Gathering)을 참조하세요.

#### <a name="clean-up-migration-data"></a>마이그레이션 데이터 정리
대상 계층 데이터베이스에서 마이그레이션에 대한 정보를 제거함으로써 원본 계층으로부터의 마이그레이션을 종료하는 프로세스입니다.

자세한 내용은 [마이그레이션 완료 계획](/sccm/core/migration/planning-to-complete-migration)을 참조하세요.



## <a name="typical-workflow"></a>일반적인 워크플로  

마이그레이션 워크플로를 설정하려면:

1.  지원되는 원본 계층을 지정합니다.  

2.  데이터 수집을 설정합니다. Configuration Manager에서 데이터 수집을 통해 원본 계층 구조에서 마이그레이션할 수 있는 데이터에 대한 정보를 수집할 수 있습니다.  

     Configuration Manager의 데이터 수집 프로세스는 사용자가 중지하기 전까지 단순 일정에 따라 자동으로 반복됩니다. 기본적으로 데이터 수집 프로세스는 4시간마다 반복되므로 Configuration Manager가 원본 계층 구조 내 데이터의 변경 내용을 식별할 수 있습니다. 데이터 수집은 배포 지점을 공유하기 위해서도 필요합니다.  

3.  원본 계층 및 대상 계층 사이에서 데이터를 마이그레이션하려면 마이그레이션 작업을 만드십시오.  

4.  데이터 수집 프로세스는 언제든지 **데이터 수집 중지** 작업을 사용하여 중지할 수 있습니다. 데이터 수집을 중지하면 Configuration Manager는 더 이상 원본 계층의 데이터 변경 내용을 식별하지 않으며 더 이상 배포 지점을 공유할 수 없습니다. 일반적으로 이 작업은 원본 계층에서 더 이상 데이터를 마이그레이션하거나 배포 지점을 공유하지 않을 경우에 사용합니다.  

5.  원본 계층에 대한 모든 사이트에서 데이터 수집이 중지될 경우 필요하면 **마이그레이션 데이터 정리** 작업을 사용하여 마이그레이션 데이터를 정리할 수 있습니다. 이 작업을 실행하면 대상 계층의 데이터베이스에서 원본 계층 마이그레이션에 대한 기록 데이터가 삭제됩니다.  

데이터를 마이그레이션하고 환경의 디바이스를 관리하기 위해 원본 계층이 더 이상 필요하지 않으면 해당 원본 계층 및 인프라를 해제할 수 있습니다.  



##  <a name="BKMK_MigrationScenarios"></a> 시나리오  

 Configuration Manager에서 지원하는 마이그레이션 시나리오는 다음과 같습니다.
- [Configuration Manager 2007 계층에서 마이그레이션](#bkmk_2007)  
- [Configuration Manager 2012 또는 다른 Configuration Manager 계층 구조에서 마이그레이션](#bkmk_2012)

> [!NOTE]  
>  독립 사이트가 있는 계층 구조의 중앙 관리 사이트가 있는 계층 구조로의 확장은 마이그레이션으로 분류되지 않습니다. 계층 구조 확장에 대한 정보는 [독립 실행형 기본 사이트 확장](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_expand)을 참조하세요.  


### <a name="bkmk_2007"></a> Configuration Manager 2007 계층에서 마이그레이션  

 마이그레이션을 사용하여 Configuration Manager 2007에서 데이터를 마이그레이션하는 경우 기존 사이트 인프라에 대한 투자를 그대로 보존하고 다음과 같은 이점을 얻을 수 있습니다.  

#### <a name="site-database-improvements"></a>사이트 데이터베이스 향상
Configuration Manager(현재 분기) 데이터베이스는 전체 유니코드를 지원합니다.

#### <a name="database-replication-between-sites"></a>사이트 간 데이터베이스 복제
Configuration Manager(현재 분기)의 복제는 Microsoft SQL Server를 기반으로 합니다. 이 동작은 사이트 간 데이터 전송 성능을 향상시킵니다.

#### <a name="user-centric-management"></a>사용자 중심 관리
사용자는 Configuration Manager(현재 분기)에서 관리 작업의 핵심입니다. 예를 들어 해당 사용자의 디바이스 이름을 알지 못하더라도 사용자에게 소프트웨어를 배포할 수 있습니다. 또한 Configuration Manager에서 사용자는 디바이스에 설치되는 소프트웨어 및 해당 소프트웨어가 설치되는 시점을 더 효과적으로 제어할 수 있습니다.

#### <a name="hierarchy-simplification"></a>계층 구조 단순화
Configuration Manager(현재 분기)를 사용하면 더 단순한 사이트 계층 구조를 빌드할 수 있습니다. 이러한 개선 사항은 중앙 관리 사이트 유형이 도입되고 기본 사이트와 보조 사이트의 동작이 변경되었기 때문입니다. Configuration Manager(현재 분기)는 네트워크 대역폭을 덜 사용하고 이전 버전보다 적은 수의 서버를 필요로 합니다.

#### <a name="role-based-administration"></a>역할 기반 관리
Configuration Manager(현재 분기)의 이러한 중앙 보안 모델은 관리 및 비즈니스 요구 사항을 충족하는 계층 구조 전체의 보안과 관리 기능을 제공합니다.

> [!NOTE]  
>  System Center 2012 Configuration Manager에서 처음 도입된 디자인 변경 때문에 Configuration Manager 2007을 Configuration Manager(현재 분기)로 업그레이드할 수 없습니다. System Center 2012 Configuration Manager에서 Configuration Manager(현재 분기)로의 현재 위치 업그레이드는 지원됩니다.  


### <a name="bkmk_2012"></a> Configuration Manager 2012 또는 다른 Configuration Manager 계층 구조에서 마이그레이션  
 System Center 2012 Configuration Manager 또는 Configuration Manager 계층 구조에서 데이터를 마이그레이션하는 과정은 동일합니다. 이 프로세스에는 여러 원본 계층 구조에서 단일 대상 계층 구조로 데이터를 마이그레이션하는 작업이 포함됩니다. 회사에서 이미 Configuration Manager가 관리하는 추가 리소스를 가져오는 경우 이 프로세스를 사용할 수 있습니다. 또한 테스트 환경에서 Configuration Manager 프로덕션 환경으로 데이터를 마이그레이션할 수 있습니다. 이 프로세스를 통해 Configuration Manager 테스트 환경에 대한 투자를 보존할 수 있습니다.  



## <a name="see-also"></a>참고 항목  

-   [Configuration Manager로 마이그레이션 계획](/sccm/core/migration/planning-for-migration)  

-   [마이그레이션할 원본 계층 구조 및 원본 사이트 구성](/sccm/core/migration/configuring-source-hierarchies-and-source-sites-for-migration)  

-   [마이그레이션 작업](/sccm/core/migration/operations-for-migration)  

-   [마이그레이션에 대한 보안 및 개인 정보](/sccm/core/migration/security-and-privacy-for-migration)  

-   [Configuration Manager 사용 시작](/sccm/core/servers/deploy/start-using)
