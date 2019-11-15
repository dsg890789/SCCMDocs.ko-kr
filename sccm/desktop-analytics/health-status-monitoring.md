---
title: 상태 모니터링
titleSuffix: Configuration Manager
description: Desktop Analytics에서 상태 모니터링이 작동하는 방식에 대해 알아봅니다.
ms.date: 04/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 343dbe2a-597c-4719-b7ac-45b1f39b49ee
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b27238ea4a77879c353a882c860959d028b81adb
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72384947"
---
# <a name="health-status-monitoring-in-desktop-analytics"></a>Desktop Analytics의 상태 모니터링

[프로덕션에 업데이트를 배포](/sccm/desktop-analytics/deploy-prod)할 때 Desktop Analytics를 사용하여 디바이스의 상태를 모니터링할 수 있습니다. 이 문서에서는 상태 모니터링이 작동하는 방식에 대해 자세히 설명합니다.

이 기능을 사용하는 방법에 대한 자세한 내용은 [업데이트된 디바이스의 상태 모니터링](/sccm/desktop-analytics/deploy-prod#bkmk_monitor)을 참조하세요.

![Desktop Analytics의 상태 모니터링 페이지 스크린샷](media/monitor-health.png)

> [!NOTE]  
> Desktop Analytics는 분모로 사용할 수 있는 사용량 데이터를 제공하는 디바이스에서만 상태 데이터를 수집합니다. 즉, 향상된(제한된) 수준에서 진단 데이터를 공유하도록 설정되지 않은 Windows 7 및 Windows 10을 실행하는 디바이스는 포함되지 않습니다. Windows 10을 실행하는 디바이스 중 10% 이상이 향상된(제한됨) 이외의 수준에서 진단 데이터를 공유하도록 설정된 경우 **상태 모니터링** 페이지에서 배너 영역에 경고를 표시합니다.  

특정 앱에 대한 자세한 정보를 보려면 목록에서 선택합니다.



## <a name="apps"></a>앱

![Desktop Analytics에서 앱에 대한 상태 요소](media/monitor-health-status-factors.png)

Desktop Analytics는 앱에 대한 다음 상태 요소를 모니터링합니다.

- **% 디바이스에서 작동 중단 발생**: 지난 2주 동안 이 특정 앱이 작동 중단하는 디바이스의 수는 앱이 사용된 디바이스의 수로 나눈 값입니다. 이 보기를 사용하면 새 OS 버전에서 앱 안정성이 증가 또는 감소되었는지 확인할 수 있습니다. Desktop Analytics는 다음 세트에 대해 이 비율을 계산합니다.  

    - **업데이트 후**: 배포 계획에 지정된 대상 OS 버전으로 업데이트된 디바이스입니다. 데이터가 충분하지 않은 자산 수를 줄이기 위해 Desktop Analytics는 업데이트된 모든 디바이스에 대해 이 데이터를 수집합니다. 이 세트에는 배포 계획에 없는 디바이스가 포함됩니다.  

    - **업데이트 전**: 배포 계획에 지정된 것보다 이전 버전의 OS에 있는 디바이스입니다. 이 목록에는 Windows 7을 실행하는 디바이스가 포함되지 않습니다.  

    - **상업용 평균**: 모든 상업용 디바이스에서 평균(avg) 중단율입니다. 이 평균은 *모든* 버전의 앱에서 계산됩니다. 버전이 중단율을 상업적 평균 이상으로 표시하는 경우 더 안정된 버전을 사용할 수 있습니다.  

- **% 세션에서 작동 중단 발생**: 앞과 유사하지만 지난 2주 동안 중단이 발생한 세션의 비율을 계산합니다.  

앱의 상태를 확인하기 위해 Desktop Analytics에는 20개 이상의 디바이스에 있는 데이터가 필요합니다. 그렇지 않으면 앱에 대한 **데이터 부족**을 보고합니다. 이 서비스는 이러한 디바이스에서 *세션 중단율*을 기준으로 상태를 계산합니다. 디바이스 중단율은 정보 제공용으로만 제공됩니다. 상태 계산에는 사용되지 않습니다.

앱 세부 정보 페이지의 아래쪽에서 다음 세 개의 탭을 통해 문제를 해결할 수 있습니다.

- **다른 버전**: 이 앱의 대체 버전 목록입니다. 각 버전에 대해 조직 내의 중단율과 상업적 평균에 대한 상대적 변경을 보여 줍니다. 낮은 중단율의 최신 버전의 앱을 찾으면 앱을 업데이트하는 것이 도움이 될 수 있습니다.  

    또한 버전에 **Windows용으로 준비** 신호가 있는지 여부를 보여 줍니다. 자세한 내용은 [호환성 평가](compat-assessment.md#driver-risk-assessment)를 참조하세요.  

- **주요 문제**: 인스턴스 수에 따른 가장 자주 발생하는 오류 ID 목록입니다. 오류 ID는 중단과 관련된 스택 추적을 식별합니다. 앱 공급 업체에 지원을 요청하는 경우 이 ID를 사용할 수 있습니다.  

- **최근 중단**:  앱이 최근에 중단된 디바이스 목록입니다. 오류 ID 및 기타 조건을 기준으로 필터링할 수 있습니다. 이 정보를 사용하여 광범위한 배포를 시도하기 전에 로그를 수집하거나 특정 디바이스에서 수정을 시도하여 문제를 해결할 수 있습니다.  

해결할 수 없는 심각한 상태 회귀를 발견한 경우 앱의 **업그레이드 결정**을 **할 수 없음**으로 변경합니다. 이 작업을 수행하면 이 자산이 포함된 디바이스에 대한 업데이트의 향후 배포를 방지합니다.


## <a name="see-also"></a>참고 항목

- [Desktop Analytics의 호환성 평가](/sccm/desktop-analytics/compat-assessment)  

- [Desktop Analytics를 사용하여 프로덕션에 배포하는 방법](/sccm/desktop-analytics/deploy-prod)  
