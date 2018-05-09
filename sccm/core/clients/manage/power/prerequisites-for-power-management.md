---
title: 전원 관리에 대한 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 전원 관리에 대한 필수 조건을 확인합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 9c062f13-3c1f-4621-9cae-de0e322aa03f
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: c6630ef07c0b7947875ea2adac4e6612143aaee8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-power-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 전원 관리에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 전원 관리에는 외부 종속성과 제품 내 종속성이 있습니다.  

## <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  
 다음 표에는 전원 관리 사용에 대한 Configuration Manager의 외부 종속성이 나열되어 있습니다.  

|종속성|추가 정보|  
|----------------|----------------------|  
|클라이언트 컴퓨터는 필요한 전원 상태를 지원할 수 있어야 합니다.|전원 관리의 모든 기능을 사용하려면 클라이언트 컴퓨터가 절전 모드, 최대 절전 모드, 절전 모드 해제 및 최대 절전 모드 해제 작업을 지원할 수 있어야 합니다. **전원 기능** 보고서에서 컴퓨터가 이러한 작업을 지원할 수 있는지 확인할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 전원 관리를 모니터링하고 계획하는 방법](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md) 항목의 [전원 기능 보고서](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Capabilites)를 참조하세요.|  

## <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  
 다음 표에는 전원 관리 사용에 대한 Configuration Manager 내의 종속성이 나열되어 있습니다.  

|종속성|추가 정보|  
|----------------|----------------------|  
|먼저 전원 관리를 사용하도록 설정해야 전원 계획을 만들고 모니터링할 수 있습니다.|전원 관리를 설정하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 전원 관리 구성](../../../../core/clients/manage/power/configuring-power-management.md)을 참조하세요.|  
|보고 서비스 지점|전원 관리 보고서를 보려면 먼저 보고 서비스 지점을 구성해야 합니다. 자세한 내용은 [System Center Configuration Manager의 보고](../../../../core/servers/manage/reporting.md)를 참조하세요.|  
