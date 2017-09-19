---
title: "전원 관리 소개 | Microsoft 문서"
description: "System Center Configuration Manager의 전원 관리를 소개합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ddff2a7-99eb-4ef8-b969-f3f7f24053db
caps.latest.revision: "4"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: d7baabf1b223498f17f60de344e1c1d30f5a8120
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="introduction-to-power-management-in-system-center-configuration-manager"></a>System Center Configuration Manager 전원 관리 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 전원 관리를 통해 많은 조직이 컴퓨터의 전력 소비를 모니터링하고 줄여야 하는 필요성을 해결할 수 있습니다. 이 기능은 Windows에 기본 제공되는 전원 관리 기능을 이용하여 조직의 컴퓨터에 적절하고 일관성 있는 설정을 적용합니다. 업무 시간 및 업무 외 시간 동안 컴퓨터에 다른 전원 설정을 적용할 수 있습니다. 예를 들어 업무 외 시간 동안 더 제한적인 전원 계획을 컴퓨터에 적용할 수 있습니다. 컴퓨터가 항상 켜져 있어야 하는 경우 전원 관리 설정이 적용되지 않도록 차단할 수 있습니다.  

 Configuration Manager의 전원 관리에는 조직의 전력 소비 및 컴퓨터 전원 설정을 분석할 수 있는 여러 보고서가 포함됩니다. 또한 보고서를 사용하여 전원 관리 문제를 해결할 수 있습니다.  

 전원 관리를 구성 및 사용하는 방법에 대한 자세한 워크플로는 [System Center Configuration Manager의 전원 관리를 위한 관리자 검사 목록](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md)을 참조하세요.  

> [!IMPORTANT]  
>  가상 컴퓨터에서는 Configuration Manager 전원 관리가 지원되지 않습니다. 가상 컴퓨터에 전원 관리 옵션을 적용할 수 없으며 가상 컴퓨터의 전원 데이터 보고서를 받을 수도 없습니다.  

## <a name="the-power-management-workflow"></a>전원 관리 워크플로  
 다음 세 단계를 사용하여 Configuration Manager에서 전원 관리를 계획하고 구현할 수 있습니다.  

### <a name="monitoring-and-planning-phase"></a>모니터링 및 계획 단계  
 전원 관리는 Configuration Manager 하드웨어 인벤토리를 사용하여 사이트의 컴퓨터 사용 및 전원 설정에 대한 데이터를 수집합니다. 이 데이터를 분석하여 컴퓨터에 대한 최적화된 전원 관리 설정을 결정하는 데 사용할 수 있는 여러 보고서가 있습니다. 예를 들어 전원 관리 워크플로의 모니터링 및 계획 단계 동안 **전원 기능** 보고서에 포함된 데이터에 따라 컬렉션을 만들고 해당 데이터를 사용하여 전원 관리가 가능하지 않은 컴퓨터를 식별할 수 있습니다. 그런 다음 해당 컴퓨터를 전원 관리에서 제외시킬 수 있습니다.  

> [!IMPORTANT]  
>  클라이언트 컴퓨터에서 전원 데이터를 수집하여 분석하기 전까지 사이트의 컴퓨터에 전원 관리 옵션을 적용하지 마세요. 기존 설정을 먼저 검사하지 않고 컴퓨터에 새 전원 관리 설정을 적용하는 경우 전력 소비가 증가할 수 있습니다.  

### <a name="enforcement-phase"></a>적용 단계  
 전원 관리를 사용하면 사이트의 컴퓨터 컬렉션에 적용할 수 있는 전원 관리 옵션을 만들 수 있습니다. 이러한 전원 관리 옵션으로 컴퓨터에서 Windows 전원 관리 설정이 구성됩니다. Configuration Manager에 포함된 전원 관리 옵션을 사용하거나 사용자 지정 전원 관리 옵션을 직접 구성할 수 있습니다. 모니터링 및 계획 단계에서 수집된 전원 데이터를 기준으로 사용하여 컴퓨터에 전원 계획을 적용한 후 절감한 전력을 평가할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 전원 관리를 위한 관리자 검사 목록](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md)을 참조하세요.  

### <a name="compliance-phase"></a>준수 단계  
 준수 단계에서 보고서를 실행하여 조직의 전력 사용량 및 전력 비용 절감을 평가할 수 있습니다. 또한 컴퓨터에서 생성된 CO2 양에 대한 개선 사항을 설명하는 보고서를 실행할 수 있습니다. 보고서는 전원 설정이 컴퓨터에 올바르게 적용되었는지 확인하고 전원 관리 기능 문제를 해결하는 데 사용할 수도 있습니다.  
