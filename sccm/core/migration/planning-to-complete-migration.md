---
title: "마이그레이션 완료 | Microsoft 문서"
description: "원본 계층에 더 이상 데이터가 없게 된 후 System Center Configuration Manager 대상 계층으로의 마이그레이션을 완료하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 5e3d3f4194b06442e34c10988a20fe9ca40ac5d7
ms.openlocfilehash: 0595ab87222aca543ae67a33c2b9fab780c6160f


---
# <a name="planning-to-complete-migration-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 마이그레이션 완료 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 원본 계층에 더 이상 대상 계층으로 마이그레이션할 데이터가 포함되어 있지 않으면 마이그레이션 프로세스를 완료할 수 있습니다. 마이그레이션을 완료하는 단계는 일반적으로 다음과 같습니다.  

-   필요한 데이터가 마이그레이션되었는지 확인합니다. 원본 계층에서 마이그레이션을 완료하기 전에 대상 계층에서 필요한 원본 계층의 모든 리소스가 성공적으로 마이그레이션되었는지 확인합니다. 이러한 리소스에는 데이터와 클라이언트가 포함될 수 있습니다.  

-   원본 사이트로부터 데이터 수집을 중지합니다. 원본 계층에서 마이그레이션을 완료하려면 먼저 원본 사이트로부터 데이터 수집을 중지해야 합니다.  

-   마이그레이션 데이터를 정리합니다. 원본 계층에 있는 모든 원본 사이트로부터 데이터 수집을 중지한 후에는 대상 계층의 데이터베이스에서 마이그레이션 프로세스 및 원본 계층 관련 데이터를 제거할 수 있습니다.  

-   원본 계층을 역할 해제합니다. 원본 계층에서 마이그레이션을 완료한 후 이 계층에 더 이상 관리할 리소스가 없는 경우 원본 계층에서 사이트를 역할 해제하고 현재의 환경에서 관련 인프라를 제거할 수 있습니다. 사이트 및 원본 계층을 역할 해제하는 방법에 대한 자세한 내용은 해당 Configuration Manager 버전용 설명서를 참조하세요.  

다음 섹션에서는 데이터 수집을 중지한 후 마이그레이션 데이터를 정리하는 방식으로 원본 계층에서 마이그레이션을 완료하는 방법에 대해 설명합니다.  

-   [데이터 수집 중지 계획](#Plan_to_Stop_Data_Gath)  

-   [마이그레이션 데이터 정리 계획](#Plan_to_clean_up)  

##  <a name="a-nameplantostopdatagatha-plan-to-stop-gathering-data"></a><a name="Plan_to_Stop_Data_Gath"></a> 데이터 수집 중지 계획  
 마이그레이션을 완료하고 마이그레이션 데이터를 정리하려면 먼저 원본 계층의 각 원본 사이트로부터 데이터 수집을 중지해야 합니다. 각 원본 사이트에서 데이터 수집을 중지하려면 맨 아래 계층 원본 사이트에서 **데이터 수집 중지** 명령을 실행한 다음 각 부모 사이트에서 이 프로세스를 반복해야 합니다. 원본 계층의 최상위 사이트는 데이터 수집을 중지하는 마지막 사이트가 되어야 합니다. 부모 사이트에서 이 명령을 실행하기 전에 각 자식 사이트에서 데이터 수집을 중지해야 합니다. 일반적으로 마이그레이션 프로세스를 완료할 준비가 된 경우에만 데이터 수집을 중지합니다.  

 원본 사이트에서 데이터 수집을 중지한 후에 해당 사이트의 공유 배포 지점은 클라이언트가 대상 계층에서 더 이상 콘텐츠 위치로 사용할 수 없습니다. 따라서, 다음 방법 중 하나를 사용하여 대상 계층의 클라이언트에서 액세스해야 할 마이그레이션된 콘텐츠가 사용 가능한 상태로 남아 있는지 확인해야 합니다.  

-   대상 계층에서 하나 이상의 배포 지점에 콘텐츠를 배포합니다.  

-   원본 사이트에서 데이터 수집을 중지하기 전에 필요한 콘텐츠가 있는 공유 배포 지점을 업그레이드하거나 재할당합니다. 공유 배포 지점 업그레이드 또는 재할당에 대한 자세한 내용은 [System Center Configuration Manager에서 콘텐츠 배포 마이그레이션 전략 계획](../../core/migration/planning-a-content-deployment-migration-strategy.md) 항목의 해당 섹션을 참조하세요.  

원본 계층에 있는 각 원본 사이트로부터 데이터 수집을 중지한 후에는 마이그레이션 데이터를 정리할 수 있습니다. 마이그레이션 데이터를 정리하기 전에는 실행되었거나 실행 예약된 각 마이그레이션 작업을 Configuration Manager 콘솔에서 계속 액세스할 수 있습니다.  

원본 사이트 및 데이터 수집에 대한 자세한 내용은 [System Center Configuration Manager에서 원본 계층 전략 계획](../../core/migration/planning-a-source-hierarchy-strategy.md)을 참조하세요.  

##  <a name="a-nameplantocleanupa-plan-to-clean-up-migration-data"></a><a name="Plan_to_clean_up"></a> 마이그레이션 데이터 정리 계획  
 마이그레이션을 완료하기 위한 마지막 단계는 마이그레이션 데이터를 정리하는 것입니다. 원본 계층의 각 원본 사이트에 대해 데이터 수집을 중지한 후에 **마이그레이션 데이터 정리** 명령을 사용할 수 있습니다. 이 작업은 선택 사항으로서 대상 계층의 데이터베이스에서 현재 원본 계층과 관련된 데이터를 제거합니다.  

 마이그레이션 데이터 정리를 수행하면 대상 계층의 데이터베이스에서 대부분의 마이그레이션 관련 데이터가 제거됩니다. 그러나 마이그레이션된 개체에 대한 세부 정보는 보존됩니다. 이러한 세부 정보와 더불어 **마이그레이션** 작업 영역을 사용하면 마이그레이션된 데이터를 포함하는 원본 계층을 재구성하여 해당 원본 계층에서 마이그레이션을 재시작하거나, 이전에 마이그레이션된 개체 및 해당 개체의 사이트 소유권을 검토할 수 있습니다.  



<!--HONumber=Dec16_HO3-->


