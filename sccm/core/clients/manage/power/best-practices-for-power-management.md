---
title: 전원 관리에 대한 모범 사례
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 전원 관리에 대한 모범 사례를 확인합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 9f7142e1-c972-4384-853b-2da1568cb3e3
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 073ee14790c608a7f4f87c2dba3af2d445b0f27a
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56135156"
---
# <a name="best-practices-for-power-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 전원 관리에 대한 모범 사례

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 전원 관리에 대한 다음 모범 사례를 사용합니다.  

## <a name="perform-the-monitoring-phase-at-a-representative-time"></a>대표적인 시간에 모니터링 단계 수행  
 전원 관리의 모니터링 단계에서 조직의 컴퓨터의 전력 소비, 활동, 전원 관리 기능 및 환경 영향에 대한 정보가 제공됩니다. 모니터링 단계를 수행하려면 대표적인 시간을 선택해야 합니다. 예를 들어 공휴일에 모니터링 단계를 수행하게 되면 컴퓨터 전원 사용에 대한 현실적인 보고서가 제공되지 않습니다.  

## <a name="create-a-control-collection-of-computers-with-no-power-plans-applied"></a>전원 계획을 적용하지 않고 컴퓨터의 컨트롤 컬렉션을 만듭니다.  
 컴퓨터에 전원 계획을 적용하는 효과를 모니터링하기 위해 두 개의 컴퓨터 컬렉션을 만듭니다. 첫 번째 컬렉션에 전원 설정을 적용하려는 대부분의 컴퓨터를 포함해야 하고 다른 컬렉션(컨트롤 컬렉션)에는 나머지 컴퓨터를 포함해야 합니다. 대부분의 컴퓨터가 포함된 컬렉션에 필요한 전원 관리 계획을 적용합니다. 그런 다음 보고서를 실행하면 전원 설정을 적용한 컴퓨터의 전원 비용, 전원 사용 및 환경 영향을 전원 설정을 적용하지 않은 컨트롤 컬렉션과 비교할 수 있습니다.  

## <a name="run-the-power-settings-report-before-you-apply-a-power-management-plan"></a>전원 관리 계획을 적용하기 전에 전원 설정 보고서를 실행합니다.  
 컴퓨터의 컬렉션에 전원 관리 계획을 적용하기 전에 컬렉션의 컴퓨터에 이미 구성된 전원 관리 설정을 파악할 수 있도록 **전원 설정** 보고서를 실행합니다. 기존 설정을 먼저 검사하지 않고 컴퓨터에 새로운 전원 관리 설정을 적용하면 전력 소비가 늘어날 수 있습니다.  

## <a name="exclude-servers-from-power-management"></a>전원 관리에서 서버 제외  
 전원 사용 현황 데이터가 수집되기는 하지만 Windows Server를 실행하는 컴퓨터에 대한 전원 관리는 지원되지 않습니다. 컬렉션에 서버를 추가하고 전원 관리에서 제외해야 합니다.  

## <a name="exclude-computers-that-you-do-not-want-to-manage"></a>관리하지 않으려는 컴퓨터를 제외합니다.  
 전원 관리로 관리하지 않으려는 컴퓨터가 있는 경우 이를 컬렉션에 추가하고 해당 컬렉션이 전원 관리에서 제외되었는지 확인합니다.  

 전원 관리에서 제외하려는 컴퓨터의 예는 다음과 같습니다.  

- 켜진 상태를 유지해야 하는 컴퓨터  

- 사용자가 원격 데스크톱 연결을 사용하여 연결해야 하는 컴퓨터  

- 전원 관리를 사용할 수 없는 컴퓨터  

- 배포 지점 사이트 시스템 역할을 하는 컴퓨터  

- 컴퓨터 및 모니터가 항상 켜져 있어야 하는 키오스크 컴퓨터와 같은 공용 컴퓨터, 정보 디스플레이 또는 모니터링 콘솔  

  자세한 내용은 [System Center Configuration Manager에서 전원 관리 구성](../../../../core/clients/manage/power/configuring-power-management.md)을 참조하세요.  

## <a name="first-apply-power-plans-to-a-test-collection-of-computers"></a>먼저 전원 계획을 컴퓨터의 테스트 컬렉션에 적용합니다.  
 전원 계획을 더 큰 컴퓨터 컬렉션에 적용하기 전에 항상 먼저 컴퓨터의 테스트 컬렉션에서 전원 관리 계획을 적용한 효과를 테스트합니다.  

 Windows XP 또는 Windows Server 2003을 실행하는 컴퓨터에 적용된 전원 설정은 해당 컴퓨터를 전원 관리에서 제외하더라도 원래 값으로 되돌려지지 않습니다. 이후 버전의 Windows에서는 전원 관리에서 컴퓨터를 제외하면 모든 전원 설정이 원래 값으로 되돌아갑니다. 개별 전원 설정을 원래 값으로 되돌릴 수 없습니다.  

## <a name="apply-power-plan-settings-individually"></a>전원 계획 설정을 개별적으로 적용합니다.  
 각 설정이 필요한 효과를 갖고 있는지 확인하려면 다음 설정을 적용하기 전에 각 전원 설정을 적용한 효과를 모니터링합니다. 전원 계획 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 전원 계획을 만들고 적용하는 방법](../../../../core/clients/manage/power/create-and-apply-power-plans.md) 항목의 [사용 가능한 전원 관리 계획 설정](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans)을 참조하세요.  

## <a name="regularly-monitor-computers-to-see-if-they-have-multiple-power-plans-applied"></a>정기적으로 컴퓨터를 모니터링하여 여러 개의 전원 계획이 적용되었는지 확인합니다.  
 전원 관리에는 둘 이상의 전원 계획을 적용한 컴퓨터를 표시하는 보고서가 포함됩니다.  

 컴퓨터가 각각 다른 전원 계획을 적용하는 여러 컬렉션의 멤버인 경우 다음 작업이 수행됩니다.  

-   전원 계획: 전원 설정에 대해 여러 값이 컴퓨터에 적용된 경우 최소한의 제한 값이 사용됩니다.  

-   절전 모드 해제 시간: 여러 절전 모드 해제 시간이 데스크톱 컴퓨터에 적용된 경우 자정에 가장 가까운 시간이 사용됩니다.  

     자세한 내용은 [System Center Configuration Manager에서 전원 관리를 모니터링하고 계획하는 방법](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md) 항목의 [전원 계획이 여러 개인 컴퓨터](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Multiple)를 참조하세요. 전원 관리에서 충돌을 해결하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 전원 계획을 만들고 적용하는 방법](../../../../core/clients/manage/power/create-and-apply-power-plans.md)을 참조하세요.  

## <a name="save-or-export-power-management-information-during-the-monitoring-and-planning-phase-of-power-management"></a>전원 관리 단계를 모니터링하고 계획하는 동안 전원 관리 정보를 저장하거나 내보냅니다.  
 일일 보고서에 사용된 전원 관리 정보는 31일간 Configuration Manager 사이트 데이터베이스에 보존됩니다.  

 월별 보고서에 사용된 전원 관리 정보는 13개월간 Configuration Manager 사이트 데이터베이스에 보존됩니다.  

 전원 관리의 모니터링, 계획 및 준수 단계 중 보고서를 실행할 때 나중에 해당 결과가 Configuration Manager에서 제거된 경우 비교할 수 있도록 데이터를 보존하려는 보고서에서 결과를 저장하거나 내보냅니다.  
