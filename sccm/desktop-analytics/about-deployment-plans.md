---
title: Desktop Analytics의 배포 계획
titleSuffix: Configuration Manager
description: Desktop Analytics의 배포 계획에 대해 알아봅니다.
ms.date: 08/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0f369f3a-f251-4f34-9302-1bdc6ea5d139
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a36093b88887b6722d07c666dead67a9aa974b8a
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72387093"
---
# <a name="about-deployment-plans-in-desktop-analytics"></a>Desktop Analytics의 배포 계획에 대한 정보

Desktop Analytics는 조직에서 디바이스, 애플리케이션 및 드라이버 데이터를 수집하고 분석합니다. 이 분석과 사용자의 입력에 따라 서비스를 사용하여 Windows 10용 배포 계획을 만들 수 있습니다. 배포 계획에는 다음과 같은 기능이 있습니다.  

- 파일럿에 포함할 디바이스를 자동으로 권장  

- 호환성 문제를 식별하고 완화 제안  

- 업데이트 전, 진행 중 및 후에 배포 상태 평가  

- 배포 진행률 추적  

배포 계획의 일부로 다음 작업을 수행합니다.  

- 배포하려는 Windows 10 버전 정의  

- 배포하려는 디바이스 그룹 선택  

- 배포에 대한 준비 규칙 만들기  

- 앱의 중요도 정의  

- 자동 권장 사항에 따라 파일럿 디바이스 선택  

- Desktop Analytics의 권장 사항에 따라 앱 문제를 해결하는 방법 결정  

기본적으로 Desktop Analytics는 매일 배포 계획 데이터를 새로 고칩니다. 앱에 중요도를 할당하거나 파일럿에 포함할 디바이스를 선택하는 등 배포 계획 내에서 수행하는 모든 변경 내용은 처리하는 데 최대 24시간이 걸립니다. 이 프로세스의 속도를 높이려면 요청 시 데이터 새로 고침을 요청합니다. 자세한 내용은 [Desktop Analytics FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조하세요.  

Desktop Analytics를 Configuration Manager에 연결한 후 배포 계획에서 컬렉션을 선택합니다. 그러면, 이 통합을 통해 Desktop Analytics 데이터를 기반으로 컬렉션에 Windows를 배포할 수 있습니다.



## <a name="readiness-rules"></a>준비 규칙

배포 계획에서 사용할 수 있는 준비 규칙은 다음과 같습니다.

- 디바이스가 Windows 업데이트에서 드라이버를 자동으로 받을지 여부 디바이스가 Windows 업데이트에서 드라이버 업데이트를 받는 경우 준비 평가의 일부로 식별되는 모든 드라이버 문제는 자동으로 **준비**로 표시됩니다.  

- Windows 앱에 대한 낮은 설치 수 임계값 앱이 이 임계값보다 더 높은 비율의 컴퓨터에 설치된 경우 배포 계획에서 앱을 **중요**로 표시합니다. 이 태그는 파일럿 단계에서 앱의 중요도를 결정할 수 있음을 의미합니다.  


## <a name="plan-assets"></a>자산 계획

<!-- 4670224 -->

[자산](/sccm/desktop-analytics/about-assets) 영역에는 디바이스 및 앱도 표시되지만 특정 배포 계획의 **자산 계획** 영역에는 추가 정보가 포함됩니다.

### <a name="devices"></a>디바이스

배포 계획의 각 디바이스에 대한 **Windows 업그레이드 결정**을 참조하세요.

**디바이스 교체**에 대한 Windows 업그레이드 결정의 원인은 다음 이유 중 하나일 수 있습니다.

- Windows 10 필수 프로세서 검사에 실패했습니다. 자세한 내용은 [최소 하드웨어 요구 사항](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview#31-processor)을 참조하세요.
- BIOS 블록이 있음
- 메모리가 부족함
- 시스템의 부팅에 중요한 구성 요소에 차단된 드라이버가 있음
- 특정 제조업체 및 모델을 업그레이드할 수 없음
- 다음 특성을 모두 포함하는 드라이버 블록이 있는 표시 클래스 구성 요소가 있음
    - 재정의하지 않음
    - 새 OS 버전에 드라이버가 없음
    - Windows 업데이트에 아직 없음
- 업그레이드를 차단하는 시스템에 다른 플러그 앤 플레이 구성 요소가 있음
- XP 에뮬레이트된 드라이버를 사용하는 무선 구성 요소가 있음
- 활성 연결이 있는 네트워크 구성 요소는 해당 드라이버를 손실합니다. 즉, 업그레이드 후 네트워크 연결이 끊어질 수 있습니다.

### <a name="apps"></a>앱

이 배포 계획에서 이 앱에 대한 **업그레이드 결정** 및 **중요도**를 설정합니다. 자세한 내용은 [배포 계획을 만드는 방법](/sccm/desktop-analytics/create-deployment-plans)을 참조하세요.

앱의 세부 정보에서 다음 정보를 확인할 수도 있습니다. 권장 사항, 호환성 위험 요소 및 Microsoft의 알려진 문제 이 정보를 사용하여 **업그레이드 결정**을 설정할 수 있습니다. 자세한 내용은 [호환성 평가](/sccm/desktop-analytics/compat-assessment)를 참조하세요.

Desktop Analytics에서 *중요*로 표시하는 앱은 배포 계획의 준비 규칙에 대한 낮은 설치 수 임계값을 기반으로 합니다. 자세한 내용은 [준비 규칙](/sccm/desktop-analytics/create-deployment-plans#readiness-rules)을 참조하세요.

   > [!Tip]
   > "중요하지 않은" 앱 범주에 대한 자세한 내용은 [시스템 및 스토어 앱의 자동 업그레이드 결정](/sccm/desktop-analytics/about-assets#bkmk_plan-autoapp)을 참조하세요. <!-- 3587232 -->


### <a name="drivers"></a>드라이버

이 배포 계획에 포함된 드라이버 목록을 참조하세요. **업그레이드 결정**을 설정하고, Microsoft의 권장 사항을 검토하고, 호환성 위험 요소를 확인합니다.


## <a name="importance"></a>중요도

배포 계획의 일부로 앱의 *중요도*를 설정합니다. Desktop Analytics는 이러한 앱을 대상 디바이스에 설치된 것으로 감지합니다. 이 설정은 Desktop Analytics에서 배포의 파일럿 단계에 포함하는 디바이스를 결정하는 데 도움이 됩니다.

앱이 대상 디바이스의 2% 미만으로 설치되는 경우 **낮은 설치 수**로 표시됩니다. 기본값은 2%입니다. 준비 설정에서 임계값을 0%에서 10%로 조정할 수 있습니다. Desktop Analytics에서는 이러한 앱을 자동으로 **업그레이드 준비 완료**로 표시합니다.  

앱의 경우 **긴급**, **중요** 또는 **중요하지 않음**의 중요도를 선택합니다. 하나를 긴급하거나 중요한 것으로 표시하는 경우 Desktop Analytics에는 해당 앱을 포함하는 일부 디바이스가 파일럿 배포에 포함됩니다. 이 서비스는 긴급한 앱의 더 많은 인스턴스를 파일럿에 포함합니다. 앱을 중요하지 않은 것으로 표시하는 경우 Desktop Analytics에서 자동으로 **업그레이드 준비 완료**로 설정합니다.



## <a name="pilot-devices"></a>파일럿 디바이스

Desktop Analytics는 중요도 정보를 글로벌 파일럿 설정과 결합합니다. 그런 다음, 파일럿 배포의 일부가 되어야 하는 디바이스에 대한 권장 사항을 만듭니다. 권장되는 파일럿 배포에는 다른 하드웨어 구성과 모든 긴급하고 중요한 앱의 하나 이상의 인스턴스가 있는 디바이스가 포함됩니다. 앱이 긴급으로 표시된 경우 이 서비스는 파일럿에서 해당 앱이 있는 더 많은 디바이스를 권장합니다.



## <a name="deployment-plans-in-configuration-manager"></a>Configuration Manager의 배포 계획

배포 계획을 만든 후 Configuration Manager를 사용하여 제품을 배포합니다. 배포가 시작되면 Desktop Analytics는 계획의 설정에 따라 배포를 모니터링합니다.


## <a name="next-steps"></a>다음 단계

- [Desktop Analytics 자산에 대해 알아보기](/sccm/desktop-analytics/about-assets): 디바이스, 드라이버 및 앱  

- [보안 및 기능 업데이트에 대한 자세한 정보](/sccm/desktop-analytics/about-updates)  

- [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
