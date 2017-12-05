---
title: "클라이언트 마이그레이션 계획"
titleSuffix: Configuration Manager
description: "원본 계층에서 System Center Configuration Manager 대상 계층으로 클라이언트를 마이그레이션하는 작업에 대해 알아봅니다."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e27b0b7-7bd3-45cd-bc99-9c991606c637
caps.latest.revision: "6"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: a7e04e1bee4798e407f08084809a50076abbad56
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2017
---
# <a name="plan-a-client-migration-strategy-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트 마이그레이션 전략 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

원본 계층에서 System Center Configuration Manager 대상 계층으로 클라이언트를 마이그레이션하려면 두 가지 작업을 수행해야 합니다. 클라이언트와 연결된 개체를 마이그레이션해야 하고 원본 계층의 클라이언트를 대상 계층에 다시 설치하거나 재할당해야 합니다. 먼저 개체를 마이그레이션하여 클라이언트를 마이그레이션할 때 개체를 사용할 수 있도록 합니다. 클라이언트와 연결된 개체는 마이그레이션 작업을 사용하여 마이그레이션합니다. 클라이언트와 연결된 개체를 마이그레이션하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 마이그레이션 작업 전략 계획](../../core/migration/planning-a-migration-job-strategy.md)을 참조하세요.  

 클라이언트를 대상 계층에 마이그레이션하도록 계획하려면 다음 섹션을 참조하십시오.  

-   [클라이언트를 대상 계층 구조로 마이그레이션하도록 계획](#Planning_for_Client_Agent_Migration)  

-   [마이그레이션 중에 클라이언트에 유지 관리되는 데이터를 처리하도록 계획](#Planning_for_Client_Data_Migration)  

-   [마이그레이션 중에 인벤토리 및 준수 데이터 계획](#Planning_for_Inventory_data_migration)  

##  <a name="Planning_for_Client_Agent_Migration"></a> 클라이언트를 대상 계층 구조로 마이그레이션하도록 계획  
 원본 계층의 클라이언트를 마이그레이션하면 클라이언트 컴퓨터의 클라이언트 소프트웨어가 업그레이드되어 대상 계층의 제품 버전과 일치하게 됩니다.  

-   **Configuration Manager 2007 원본 계층:** 지원되는 Configuration Manager 버전을 실행하는 원본 계층의 클라이언트를 마이그레이션하면 클라이언트 소프트웨어가 대상 계층의 클라이언트 버전으로 업그레이드됩니다.  

-   **System Center 2012 Configuration Manager 이상 원본 계층:** 제품 버전이 같은 계층 간에 클라이언트를 마이그레이션하면 클라이언트 소프트웨어가 변경되거나 업그레이드되지 않습니다. 대신 클라이언트가 원본 계층에서 대상 계층의 사이트로 재할당됩니다.  

    > [!NOTE]  
    >  계층의 제품 버전이 대상 계층으로의 마이그레이션을 지원하지 않는 경우 원본 계층의 모든 사이트와 클라이언트를 호환되는 제품 버전으로 업그레이드하십시오. 원본 계층이 지원되는 제품 버전으로 업그레이드되면 계층 간에 마이그레이션할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 마이그레이션을 수행하기 위한 필수 조건](../../core/migration/prerequisites-for-migration.md)의 [마이그레이션에 지원되는 Configuration Manager 버전](../../core/migration/prerequisites-for-migration.md#BKMK_SupportedMigrationVersions)을 참조하세요.  

클라이언트 마이그레이션을 계획하려면 다음 정보를 참조하십시오.  

-   원본 계층에서 대상 계층으로 업그레이드하거나 재할당하기 위해 대상 계층의 클라이언트 배포에 지원되는 클라이언트 배포 방법을 사용할 수 있습니다. 일반적인 클라이언트 배포 방법으로는 클라이언트 강제 설치, 소프트웨어 배포, 그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치 등이 있습니다. 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 방법](../../core/clients/deploy/plan/client-installation-methods.md)을 참조하세요.  

-   원본 계층에서 클라이언트 소프트웨어를 실행하는 장치는 최소 하드웨어 요구 사항을 충족하고 대상 계층의 Configuration Manager 버전에서 지원하는 운영 체제를 실행해야 합니다.  

-   클라이언트를 마이그레이션하기 전에 마이그레이션 작업을 실행하여 대상 계층의 클라이언트가 사용할 정보를 마이그레이션합니다.  

-   업그레이드하는 클라이언트에는 배포 실행 기록이 보존됩니다. 이 덕분에 대상 계층에서 배포가 불필요하게 다시 실행되지 않습니다.  

    -   Configuration Manager 2007 클라이언트의 경우 보급 알림 실행 기록이 보존됩니다.  

    -   System Center 2012 Configuration Manager 또는 System Center Configuration Manager의 클라이언트에 대한 배포 실행 기록이 보존됩니다.  

-   원본 계층의 사이트에서 클라이언트를 선택한 순서대로 마이그레이션할 수 있습니다. 그러나 한 번에 많은 클라이언트를 마이그레이션하는 것보다 제한된 수의 클라이언트를 단계적으로 마이그레이션하는 것이 좋습니다. 단계적으로 마이그레이션하면 새로 업그레이드한 각 클라이언트에서 최초의 전체 인벤토리 및 호환 데이터를 할당된 사이트로 전송할 때 네트워크 대역폭 요구 사항 및 서버 처리를 줄일 수 있습니다.  

-   Configuration Manager 2007 클라이언트를 마이그레이션하는 경우 클라이언트 컴퓨터에서 기존 클라이언트 소프트웨어가 제거되고 새 클라이언트 소프트웨어가 설치됩니다.  

-   App-V 클라이언트 버전이 4.6 SP1 이상이 아닌 경우에는 Configuration Manager에서 App-V 클라이언트가 설치된 Configuration Manager 2007 클라이언트를 마이그레이션할 수 없습니다.  

Configuration Manager 콘솔에 있는 **관리** 작업 영역의 **마이그레이션** 노드에서 클라이언트 마이그레이션 프로세스를 모니터링할 수 있습니다.  

클라이언트를 대상 계층으로 마이그레이션한 후에는 더 이상 원본 계층을 사용하여 해당 장치를 관리할 수 없으며 원본 계층에서 클라이언트를 제거하는 것이 좋습니다. 계층을 마이그레이션할 때 필수 요구 사항은 아니지만, 원본 계층 보고서에 마이그레이션된 클라이언트가 표시되지 않도록 하거나 마이그레이션 중에 두 계층 간의 리소스 수가 잘못 표시되지 않도록 할 수 있습니다. 예를 들어 마이그레이션된 클라이언트가 원본 사이트 데이터베이스에 남아 있으면 이제 대상 계층에서 관리되는 컴퓨터를 관리되지 않는 리소스로 잘못 식별하는 소프트웨어 업데이트 보고서를 실행할 수 있습니다.  

##  <a name="Planning_for_Client_Data_Migration"></a> 마이그레이션 중에 클라이언트에 유지 관리되는 데이터를 처리하도록 계획  
원본 계층에서 대상 계층으로 클라이언트를 마이그레이션하면 일부 정보는 장치에 보존되지만 일부 다른 정보는 마이그레이션 후에 장치에서 사용할 수 없게 됩니다.  

다음 정보는 클라이언트 장치에 보존됩니다.  

-   고유 식별자(GUID) - 클라이언트를 Configuration Manager 데이터베이스의 해당 정보와 연결합니다.  

-   보급 알림 또는 배포 기록 - 클라이언트가 대상 계층에서 불필요하게 보급 알림 또는 배포를 다시 실행하지 않도록 합니다.  

다음 정보는 클라이언트 장치에 보존되지 않습니다.  

-   클라이언트 캐시의 파일 - 클라이언트에서 소프트웨어를 설치하는 데 이러한 파일이 필요한 경우 클라이언트가 대상 계층에서 다시 다운로드합니다.  

-   아직 실행하지 않은 보급 알림 또는 배포에 대한 원본 계층의 정보 - 클라이언트에서 마이그레이션 후에 보급 알림 또는 배포를 실행하도록 하려면 보급 알림 또는 배포를 대상 계층의 클라이언트에 다시 배포해야 합니다.  

-   인벤토리에 대한 정보 - 클라이언트에서 마이그레이션하고 새 클라이언트 데이터가 생성된 후 클라이언트에서 대상 계층의 할당된 사이트로 이 정보를 다시 보냅니다.  

-   호환 데이터 - 클라이언트에서 마이그레이션하고 새 클라이언트 데이터가 생성된 후 클라이언트에서 대상 계층의 할당된 사이트로 이 정보를 다시 보냅니다.  

클라이언트에서 마이그레이션할 때 Configuration Manager 클라이언트 레지스트리 및 파일 경로에 저장된 정보는 보존되지 않습니다. 마이그레이션 후에 이러한 설정을 다시 적용합니다. 일반적인 설정은 다음과 같습니다.  

-   전원 구성표  

-   로깅 설정  

-   로컬 정책 설정  

또한, 일부 응용 프로그램은 다시 설치해야 할 수 있습니다.  

##  <a name="Planning_for_Inventory_data_migration"></a> 마이그레이션 중에 인벤토리 및 준수 데이터 계획  
클라이언트를 대상 계층으로 마이그레이션할 때 클라이언트 인벤토리 및 호환 데이터는 저장되지 않습니다. 대신 이 정보는 클라이언트에서 할당된 사이트에 해당 정보를 처음 보낼 때 대상 계층에서 다시 만들어집니다. 그로 인한 네트워크 대역폭 요구 사항 및 서버 처리를 줄이려면 한 번에 많은 클라이언트를 마이그레이션하는 것보다 적은 수의 클라이언트를 단계적으로 마이그레이션하는 것이 좋습니다.  

 또한, 하드웨어 인벤토리의 사용자 지정은 원본 계층에서 마이그레이션할 수 없습니다. 이러한 설정은 마이그레이션과 별도로 대상 계층에 적용해야 합니다. 하드웨어 인벤토리 확장에 대한 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 구성하는 방법](../../core/clients/manage/inventory/configure-hardware-inventory.md)을 참조하세요.  
