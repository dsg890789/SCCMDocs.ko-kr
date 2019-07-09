---
title: 상태 모니터링
titleSuffix: Configuration Manager
description: 데스크톱 Analytics에서 상태 모니터링의 작동 방식에 대해 알아봅니다.
ms.date: 04/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 343dbe2a-597c-4719-b7ac-45b1f39b49ee
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4b32105304354e9b9d4473451a32f52162f80d02
ms.sourcegitcommit: 20bbb870baf624c7809d3972f2d09a8d2df79cda
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/08/2019
ms.locfileid: "67623329"
---
# <a name="health-status-monitoring-in-desktop-analytics"></a>데스크톱 Analytics의 모니터링 상태

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

것 [프로덕션에 업데이트를 배포](/sccm/desktop-analytics/deploy-prod), 데스크톱 Analytics 장치 상태를 모니터링 하는 데 사용 합니다. 이 문서는 상태 모니터링의 작동 방식을 자세히 설명 합니다.

이 기능을 사용 하는 방법에 대 한 자세한 내용은 참조 하세요. [업데이트 된 장치의 상태를 모니터링](/sccm/desktop-analytics/deploy-prod#bkmk_monitor)합니다.

![데스크톱 분석의 상태 모니터링 페이지의 스크린샷](media/monitor-health.png)

> [!NOTE]  
> 데스크톱 분석만 분모로 사용할 수 있습니다 사용 현황 데이터를 제공 하는 장치에서 상태 데이터를 수집 합니다. 즉, 고급 (제한적) 수준에서 진단 데이터를 공유로 설정 되지 않은 Windows 7 및 Windows 10을 실행 하는 장치를 포함 하지 않습니다. Windows 10을 실행 하는 장치 10% 이상이 고급 (제한적) 이외의 수준에서 진단 데이터를 공유 하도록 설정 된 경우는 **상태를 모니터링** 페이지 배너 영역에 경고를 표시 합니다.  

특정 앱에 대 한 자세한 정보를 보려면 목록에서 선택 합니다.



## <a name="apps"></a>앱

![데스크톱 분석에서 앱에 대 한 상태 상태 요소](media/monitor-health-status-factors.png)

데스크톱 분석 앱에 대 한 상태 요소를 다음 상태를 모니터링합니다.

- **충돌을 사용 하 여 % 장치**: 지난 2 주에 대 한이 특정 앱에서 반복적인 충돌이 발생 하는 장치 수가 앱에 사용 된 장치 수로 나눈 값입니다. 이 보기에는 앱 안정성이 늘어나거나 감소 새 OS 버전에 있는지 여부를 확인할 수 있습니다. 다음 집합에 대 한이 비율을 계산 하는 데스크톱 분석:  

    - **업데이트 후**: 배포 계획에 지정 된 대상 OS 버전으로 업데이트 된 장치. 데스크톱 Analytics 수가 부족 하 여 데이터를 사용 하 여 자산을 줄이기 위해 모든 업데이트 된 장치에 대 한이 데이터를 수집 합니다. 이 집합에서 배포 계획에 없는 해당 장치를 포함합니다.  

    - **업데이트 전에**: 배포 계획에 지정 된 이전 OS 버전에 있는 장치입니다. 이 목록에는 Windows 7을 실행 하는 장치 포함 되지 않습니다.  

    - **상업용 평균**: 평균 (avg) 모든 상용 장치에서 속도가 충돌 합니다. 이 평균을 계산할 *모든* 앱의 버전입니다. 상업용 평균 초과 크래시 속도 표시 하는 버전에 있을 수 있습니다 더 안정적인 버전을 사용할 수 있습니다.  

- **충돌을 사용 하 여 세션 %** : 계속 있지만 지난 두 주 동안의 세션의 백분율 충돌 횟수과 유사 합니다.  

앱의 상태를 확인 하려면 데스크톱 분석 20 개 이상의 장치에서 데이터를 필요 합니다. 그렇지 않으면 보고 **데이터가 부족 하 게** 앱에 대 한 합니다. 서비스 상태를 기반으로 계산 합니다 *세션 충돌 속도가* 이러한 장치에서. 장치 충돌 속도가 참고용 으로만 제공 됩니다. 상태 상태 계산에 사용 되지 않습니다.

앱 세부 정보 페이지의 맨 아래에 다음 세 개의 탭 도움이 될 수 있습니다 문제를 해결 합니다.

- **다른 버전**: 이 앱의 다른 버전의 목록입니다. 각 버전에 대해 내 조직과 상업적 평균 크래시 요금이 상대 변경 내용을 보여 줍니다. 이후 버전 충돌 속도가 낮은 사용 하 여 앱의 경우, 앱을 업데이트 도움이 될 수 있습니다.  

    버전이 있는 경우는 수도 표시 됩니다는 **준비에 대 한 Windows** 신호입니다. 자세한 내용은 [Compatibility assessment](compat-assessment.md#driver-risk-assessment)합니다.  

- **문제를 상위**: 목록 인스턴스 수에 따라 가장 자주 실패 Id입니다. 오류 ID 관련 작동 중단 된 스택 추적을 식별 합니다. 지원에 대 한 앱 공급 업체를 호출할 때이 ID를 사용할 수 있습니다.  

- **최근 크래시**:  목록에는 앱을 최근에 작동이 중단 된 장치입니다. 오류 ID 및 기타 조건 별로 필터링 할 수 있습니다. 이 정보를 사용 하 여 로그를 수집 하거나 광범위 한 배포를 시도 하기 전에 특정 장치에서 수정 하 여 문제를 해결 합니다.  

심각한 상태 회귀 문제를 해결 하려면 수 있는 경우, 앱의 변경 **업그레이드 결정** 하 **없습니다**합니다. 이 그러면이이 자산을 사용 하 여 장치에 업데이트의 향후 배포를 차단합니다.


## <a name="see-also"></a>참고 항목

- [데스크톱 분석의 호환성 평가](/sccm/desktop-analytics/compat-assessment)  

- [데스크톱 Analytics를 사용 하 여 프로덕션에 배포 하는 방법](/sccm/desktop-analytics/deploy-prod)  
