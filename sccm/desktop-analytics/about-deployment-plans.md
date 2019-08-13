---
title: 데스크톱 분석의 배포 계획
titleSuffix: Configuration Manager
description: 데스크톱 분석의 배포 계획에 대해 알아봅니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0f369f3a-f251-4f34-9302-1bdc6ea5d139
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2a1acd99ca1a4676c4397eee427cdcb8b795cf00
ms.sourcegitcommit: 6b5a003256305c1f0cb605e52aeaaf19c23af5a9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68956392"
---
# <a name="about-deployment-plans-in-desktop-analytics"></a>데스크톱 분석의 배포 계획 정보

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석은 조직에서 장치, 응용 프로그램 및 드라이버 데이터를 수집 하 고 분석 합니다. 이 분석과 사용자의 입력에 따라 서비스를 사용 하 여 Windows 10 용 배포 계획을 만들 수 있습니다. 배포 계획에는 다음과 같은 기능이 있습니다.  

- 파일럿에 포함할 장치를 자동으로 권장  

- 호환성 문제를 식별 하 고 완화 제안  

- 업데이트 전후에 배포 상태 평가  

- 배포 진행률 추적  

배포 계획의 일부로 다음 작업을 수행 합니다.  

- 배포할 Windows 10 버전을 정의 합니다.  

- 배포 하려는 장치 그룹 선택  

- 배포에 대 한 준비 규칙 만들기  

- 앱의 중요도 정의  

- 자동 권장 사항에 따라 파일럿 장치 선택  

- 데스크톱 분석의 권장 사항에 따라 앱 문제를 해결 하는 방법 결정  

기본적으로 Desktop Analytics는 매일 배포 계획 데이터를 새로 고칩니다. 앱에 중요도를 할당 하거나 파일럿에 포함할 장치를 선택 하는 등 배포 계획 내에서 수행 하는 모든 변경 내용은 처리 하는 데 최대 24 시간이 걸립니다. 이 프로세스의 속도를 높이려면 요청 시 데이터 새로 고침을 요청 합니다. 자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조 하세요.  

데스크톱 분석을 Configuration Manager에 연결한 후 배포 계획에서 컬렉션을 선택 합니다. 그러면이 통합을 통해 데스크톱 분석 데이터를 기반으로 컬렉션에 Windows를 배포할 수 있습니다.



## <a name="readiness-rules"></a>준비 규칙

배포 계획에서 사용할 수 있는 준비 규칙은 다음과 같습니다.

- 장치가 Windows 업데이트에서 드라이버를 자동으로 받을지 여부입니다. 장치가 Windows 업데이트에서 드라이버 업데이트를 수신 하는 경우 준비 평가의 일부로 식별 되는 모든 드라이버 문제가 자동으로 **준비**로 표시 됩니다.  

- Windows 앱에 대 한 낮은 설치 수 임계값입니다. 앱이이 임계값 보다 더 높은 비율의 컴퓨터에 설치 된 경우 배포 계획에서 앱을 **주목할 만한**것으로 표시 합니다. 이 태그는 파일럿 단계에서 앱이 테스트 하는 중요도를 결정할 수 있음을 의미 합니다.  


## <a name="plan-assets"></a>자산 계획

<!-- 4670224 -->

[자산](/sccm/desktop-analytics/about-assets) 영역에는 장치 및 앱도 표시 되지만 특정 배포 계획의 **계획 자산** 영역에는 추가 정보가 포함 됩니다.

### <a name="devices"></a>장치

배포 계획의 각 장치에 대 한 **Windows 업그레이드 결정** 을 참조 하세요.

**장치 교체** 에 대 한 Windows 업그레이드 결정은 다음 이유 중 하나 때문일 수 있습니다.

- Windows 10 필수 프로세서 검사에 실패 했습니다. 자세한 내용은 [최소 하드웨어 요구 사항](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview#31-processor)을 참조 하세요.
- BIOS 블록이 있습니다.
- 메모리가 부족 합니다.
- 시스템의 부팅에 중요 한 구성 요소에 차단 된 드라이버 있음
- 특정 제조업체 및 모델을 업그레이드할 수 없음
- 다음 특성을 모두 포함 하는 드라이버 블록을 포함 하는 표시 클래스 구성 요소가 있습니다.
    - 재정의 하지 않습니다.
    - 새 OS 버전에 드라이버가 없습니다.
    - 아직 Windows 업데이트 되지 않았습니다.
- 시스템에 업그레이드를 차단 하는 다른 플러그 앤 플레이 구성 요소가 있습니다.
- XP 에뮬레이션 드라이버를 사용 하는 무선 구성 요소가 있습니다.
- 활성 연결을 사용 하는 네트워크 구성 요소는 드라이버를 손실 합니다. 즉, 업그레이드 후 네트워크 연결이 끊어질 수 있습니다.

### <a name="apps"></a>앱

이 배포 계획에서이 앱에 대 한 **업그레이드 결정** 및 **중요도** 를 설정 합니다. 자세한 내용은 [배포 계획을 만드는 방법](/sccm/desktop-analytics/create-deployment-plans)을 참조 하세요.

앱의 세부 정보에서 다음 정보를 확인할 수도 있습니다. 권장 사항, 호환성 위험 요소 및 Microsoft의 알려진 문제입니다. 이 정보를 사용 하 여 **업그레이드 결정**을 쉽게 설정할 수 있습니다. 자세한 내용은 [호환성 평가](/sccm/desktop-analytics/compat-assessment)를 참조 하세요.

데스크톱 분석에서 *주목할 만한* 것으로 표시 되는 앱은 배포 계획의 준비 규칙에 대 한 낮은 설치 수 임계값을 기반으로 합니다. 자세한 내용은 [준비 규칙](/sccm/desktop-analytics/create-deployment-plans#readiness-rules)을 참조 하세요.

#### <a name="a-namebkmk_plan-autoapp--automatic-upgrade-decision-of-system-and-store-apps"></a><a name="bkmk_plan-autoapp" />시스템 및 스토어 앱의 자동 업그레이드 결정

<!-- 3587232 -->
데스크톱 분석 워크플로에서 중요 한 모든 앱에 대해 **중요도** 와 **업그레이드 결정** 을 확인 하는 것이 중요 합니다. 이러한 앱에 주석을 추가 하는 데 도움을 줄 수 있도록 특정 유형의 앱은 자동으로 *중요 하지 않은*것으로 표시 됩니다. 이러한 앱에 대 한 배포 계획 업그레이드 결정도 *준비*로 표시 됩니다. 다음 앱은 호환 되며 Windows를 업그레이드 한 후에도 계속 작동 해야 합니다.

- Microsoft에서 게시 한 시스템 앱 및 구성 요소

- Microsoft Store에서 관리 및 업데이트 된 앱

> [!Tip]
> 전역 수준 또는 배포 계획에 따라 모든 앱에 대 한 입력을 관리 합니다.
>
> 1. 데스크톱 분석 포털의 **관리** 메뉴에서 **자산**을 선택 합니다. 그런 다음 **앱**을 선택 합니다.
>
> 2. **유형** 및 **범주** 열을 사용 하 여 이러한 앱 범주를 관리 합니다.
>
>    - 스토어 앱의 경우 **형식** 을 **최신** 으로 필터링 합니다.
>    - 시스템 앱의 경우 **범주** 를 **백그라운드 프로세스** 또는 **Windows 구성 요소로** 필터링 합니다.


### <a name="drivers"></a>드라이버

이 배포 계획에 포함 된 드라이버 목록을 참조 하십시오. **업그레이드 결정**을 설정 하 고 Microsoft의 권장 사항을 검토 한 다음 호환성 위험 요소를 참조 하세요.


## <a name="importance"></a>중요도

배포 계획의 일부로 앱의 *중요도* 를 설정 합니다. 데스크톱 분석은 이러한 앱을 대상 장치에 설치 된 것으로 감지 합니다. 이 설정은 데스크톱 분석에서 배포의 파일럿 단계에 포함 하는 장치를 결정 하는 데 도움이 됩니다.

앱이 대상 장치의 2% 미만으로 설치 된 경우 **설치 수가 낮음**으로 표시 됩니다. 기본값은 2%입니다. 준비 설정에서 임계값을 0%에서 10%로 조정할 수 있습니다. Desktop Analytics는 이러한 앱을 **업그레이드 준비**로 자동으로 표시 합니다.  

앱의 경우 중요, **중요**또는 **중요 하지 않음**의 중요도를 선택 합니다. 하나를 중요 하거나 중요 한 것으로 표시 하는 경우 데스크톱 분석에는 해당 앱을 포함 하는 일부 장치가 파일럿 배포에 포함 됩니다. 이 서비스에는 중요 한 앱의 파일럿 추가 인스턴스가 포함 됩니다. 앱을 중요 하지 않은 것으로 표시 하면 데스크톱 분석에서 자동으로 **업그레이드 준비**로 설정 됩니다.



## <a name="pilot-devices"></a>파일럿 장치

데스크톱 분석은 중요 정보를 전역 파일럿 설정에 결합 합니다. 그런 다음 파일럿 배포의 일부로 사용할 장치에 대 한 권장 사항을 만듭니다. 권장 되는 파일럿 배포에는 다른 하드웨어 구성과 하나 이상의 중요 하 고 중요 한 앱 인스턴스를 포함 하는 장치가 포함 됩니다. 앱이 중요로 표시 된 경우이 서비스는 파일럿에서 해당 앱으로 더 많은 장치를 추천 합니다.



## <a name="deployment-plans-in-configuration-manager"></a>Configuration Manager의 배포 계획

배포 계획을 만든 후 Configuration Manager를 사용 하 여 제품을 배포 합니다. 배포가 시작 되 면 데스크톱 분석은 계획의 설정에 따라 배포를 모니터링 합니다.


## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 자산에 대 한 자세한 정보](/sccm/desktop-analytics/about-assets): 장치, 드라이버 및 앱  

- [보안 및 기능 업데이트에 대 한 자세한 정보](/sccm/desktop-analytics/about-updates)  

- [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
