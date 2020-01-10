---
title: 전원 관리 권장 사항
titleSuffix: Configuration Manager
description: Configuration Manager의 전원 관리에 관한 Microsoft 권장 사항을 알아봅니다.
ms.date: 09/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 9f7142e1-c972-4384-853b-2da1568cb3e3
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 129dcb4560c8697f018bf05f62e65e74e5869466
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824013"
---
# <a name="recommendations-for-power-management-in-configuration-manager"></a>Configuration Manager의 전원 관리 권장 사항

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 전원 관리에 다음 권장 사항을 사용합니다.  

## <a name="monitor-at-a-representative-time"></a>대표적인 시간에 모니터링

전원 관리의 모니터링 단계는 조직의 컴퓨터에서 다음 정보를 제공합니다.

- 전력 소비
- 활동
- 전원 관리 기능
- 환경 영향

디바이스를 모니터링할 대표적인 시간을 선택합니다. 예를 들어 공휴일에 모니터링하게 되면 컴퓨터 전원 사용량에 관한 현실적인 보고서가 제공되지 않습니다.

## <a name="create-a-control-collection"></a>컨트롤 컬렉션 만들기

컴퓨터에 전원 계획을 적용하는 효과를 모니터링하기 위해 두 개의 컴퓨터 컬렉션을 만듭니다. 첫 번째 컬렉션에 전원 설정을 적용하려는 대부분의 컴퓨터를 포함해야 합니다. ‘컨트롤 컬렉션’에는 나머지 컴퓨터를 포함해야 합니다.  첫 번째 컬렉션에 필요한 전원 관리 계획을 적용합니다. 그런 다음, 보고서를 실행하여 두 컬렉션 간의 영향을 비교합니다.  

## <a name="run-reports-before-you-apply-a-plan"></a>계획을 적용하기 전에 보고서 실행

컴퓨터의 컬렉션에 전원 관리 계획을 적용하기 전에 **전원 설정** 보고서를 실행합니다. 이 보고서를 사용하여 컬렉션의 컴퓨터에 이미 구성된 전원 관리 설정을 파악할 수 있습니다. 기존 설정을 먼저 검사하지 않고 컴퓨터에 새로운 전원 관리 설정을 적용하면 전력 소비가 늘어날 수 있습니다.  

## <a name="exclude-servers"></a>서버 제외

Windows Server를 실행하는 컴퓨터의 전원 관리는 지원되지 않습니다. 컬렉션에 서버를 추가하고 전원 관리에서 제외합니다.  

> [!NOTE]
> Configuration Manager는 Windows Server의 전원 관리를 지원하지 않지만 분석 및 보고를 위해 전원 사용량 데이터를 계속 수집합니다.

## <a name="exclude-other-computers"></a>다른 컴퓨터 제외

전원 관리로 관리하지 않으려는 컴퓨터가 있는 경우 이 컴퓨터를 제외 컬렉션에 추가합니다.  

전원 관리에서 다음과 같은 유형의 컴퓨터를 제외할 수 있습니다.

- 켜진 상태를 유지해야 하는 컴퓨터  

- 사용자가 원격으로 연결해야 하는 컴퓨터  

- 전원 관리를 사용할 수 없는 컴퓨터  

- 배포 지점 사이트 시스템 역할을 하는 컴퓨터  

- 컴퓨터 및 모니터가 항상 켜져 있어야 하는 키오스크 컴퓨터와 같은 공용 컴퓨터, 정보 디스플레이 또는 모니터링 콘솔  

자세한 내용은 [전원 관리 구성](/sccm/core/clients/manage/power/configuring-power-management)을 참조하세요.  

## <a name="apply-power-plans-to-a-test-collection"></a>테스트 컬렉션에 전원 계획 적용

전원 계획을 더 큰 컴퓨터 컬렉션에 적용하기 전에 항상 먼저 컴퓨터의 테스트 컬렉션에서 전원 관리 계획을 적용한 효과를 테스트합니다.  

전원 관리에서 컴퓨터를 제외하면 모든 전원 설정이 원래 값으로 되돌아갑니다. 개별 전원 설정을 원래 값으로 되돌릴 수 없습니다.  

## <a name="apply-power-plan-settings-individually"></a>전원 계획 설정을 개별적으로 적용합니다.

다음 설정을 적용하기 전에 각 전원 설정을 적용한 효과를 모니터링합니다. 이 프로세스는 각 설정이 필요한 효과를 나타내는지 확인합니다. 전원 계획 설정에 관한 자세한 내용은 [사용할 수 있는 전원 관리 계획 설정](/sccm/core/clients/manage/power/create-and-apply-power-plans#BKMK_Plans)을 참조하세요.  

## <a name="regularly-monitor-computers-for-multiple-power-plans"></a>여러 전원 계획이 적용된 컴퓨터를 정기적으로 모니터링

전원 관리에는 둘 이상의 전원 계획을 적용한 컴퓨터를 표시하는 보고서가 포함됩니다. **전원 계획이 여러 개인 컴퓨터**.

컴퓨터가 각각 서로 다른 전원 계획을 적용하는 여러 컬렉션의 멤버인 경우 다음 동작이 적용됩니다.  

- **전원 계획**: 컴퓨터에 전원 설정의 여러 값을 적용하면 최소한의 제한 값이 사용됩니다.  

- **절전 모드 해제 시간**: 데스크톱 컴퓨터에 여러 절전 모드 해제 시간을 적용하면 자정에 가장 가까운 시간이 사용됩니다.  

자세한 내용은 [전원 계획이 여러 개인 컴퓨터](/sccm/core/clients/manage/power/monitor-and-plan-for-power-management#BKMK_Multiple)를 참조하세요.  

## <a name="save-or-export-power-management-information"></a>전원 관리 정보 저장 또는 내보내기

모니터링 및 규정 준수 단계에서 보고서를 실행하는 경우 결과를 저장하거나 내보냅니다. Configuration Manager가 나중에 데이터를 제거하는 경우 나중에 비교할 수 있도록 데이터를 유지합니다.  

Configuration Manager는 다음 전원 관리 정보를 사이트 데이터베이스에 유지합니다.

- 일일 보고서에 사용된 전원 관리 정보: 31일

- 월별 보고서에 사용되는 전원 관리 정보: 13개월
