---
title: 데스크톱 Analytics에서 배포 계획
titleSuffix: Configuration Manager
description: 데스크톱 Analytics에서 배포 계획에 알아봅니다.
ms.date: 06/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0f369f3a-f251-4f34-9302-1bdc6ea5d139
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8080d89995b6ed10efd996b4ad757151e315c74
ms.sourcegitcommit: af207075c4a8bc59242a41d3192a4057452a0e55
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141042"
---
# <a name="about-deployment-plans-in-desktop-analytics"></a>데스크톱 Analytics에서 배포 계획에 대 한

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

수집 하 고 조직에서 장치, 응용 프로그램 및 드라이버 데이터를 분석 하는 데스크톱 분석 합니다. 이 분석 및 입력에 따라 Windows 10에 대 한 배포 계획을 만들려면 서비스를 사용할 수 있습니다. 배포 계획에는 다음과 같은 기능이 있습니다.  

- 자동으로 파일럿에 포함 장치를 것이 좋습니다.  

- 호환성 문제를 식별 하 고 완화 조치를 제안 합니다.  

- 이전, 도중 및 업데이트 이후 배포의 상태를 평가 합니다.  

- 배포의 진행 상태  

배포 계획의 일환으로, 다음 작업을 수행할 수 있습니다.  

- 배포 하려는 Windows 10의 버전을 정의 합니다.  

- 어떤 그룹을 배포 하려는 장치를 선택 합니다.  

- 배포에 대 한 준비 규칙 만들기  

- 앱의 중요도 정의 합니다.  

- 자동 권장 사항에 따라 파일럿 장치를 선택 합니다.  

- 데스크톱 Analytics에서 권장 사항에 따라 앱을 사용 하 여 문제를 해결 하는 방법 결정  

기본적으로 데스크톱 분석 데이터를 새로 고칩니다 배포 계획 매일입니다. 앱에 중요도 할당 하거나, 파일럿 실행에 포함할 장치 선택 등 배포 계획, 내에서 수행한 변경 내용 처리 하는 데 최대 24 시간이 됩니다. 이 프로세스를 신속 하 게 요청 시 데이터 새로 고침을 요청 합니다. 자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)합니다.  

데스크톱 Analytics를 Configuration Manager에 연결한 후 배포 계획에서 컬렉션을 선택 합니다. 이 통합 데스크톱 분석 데이터를 기반으로 컬렉션에 Windows를 배포할 수 있습니다.



## <a name="readiness-rules"></a>준비 규칙

다음 준비 상태 규칙은 배포 계획에 사용할 수 있습니다.

- 여부 장치가 Windows 업데이트에서 드라이버를 자동으로 받습니다. Windows Update에서 드라이버 업데이트를 수신 하는 장치의 경우 준비 상태 평가의 일부로 식별 하는 모든 드라이버 문제를 자동으로 표시 됩니다 **준비**합니다.  

- 낮은은 Windows 앱에 대 한 count 임계값을 설치 합니다. 앱이이 임계값 보다 높은 비율로 컴퓨터에 설치, 배포 계획으로 앱 표시 **Noteworthy**합니다. 이 태그는 파일럿 단계 동안 테스트 하려면이 얼마나 중요 한지를 결정할 수 있습니다 의미 합니다.  


## <a name="plan-assets"></a>자산 계획

<!-- 4670224 -->

하는 동안를 [자산](/sccm/desktop-analytics/about-assets) 영역 장치 및 앱에도 표시 합니다 **자산 계획** 특정 배포 계획 영역에 추가 정보가 포함 되어 있습니다.

### <a name="devices"></a>장치

참조 된 **Windows 업그레이드 결정** 배포 계획의 각 장치에 대 한 합니다.

Windows 업그레이드 하기로 **Replace 장치** 다음 이유 중 하나 때문일 수 있습니다.

- 필요한 Windows 10 프로세서 확인에 실패 했습니다. 자세한 내용은 [최소 하드웨어 요구 사항](https://docs.microsoft.com/windows-hardware/design/minimum/minimum-hardware-requirements-overview#31-processor)합니다.
- BIOS 블록이
- 충분 한 메모리가 없습니다
- 시스템에서 부팅 중요 한 구성 요소에는 차단 된 드라이버가 있습니다.
- 특정 제조업체 및 모델을 업그레이드할 수 없습니다.
- 다음 특성의 모든 드라이버 블록 표시 클래스 요소인:
    - 재정의 안 함
    - 새 OS 버전에 드라이버가 없습니다.
    - 아직 없는 Windows 업데이트
- 업그레이드를 차단 하는 시스템에서 다른 플러그 앤 플레이 구성 요소가
- XP 에뮬레이트된 드라이버를 사용 하는 무선 구성 요소는
- 활성 연결이 있는 네트워크 구성 요소는 해당 드라이버를 잃게 됩니다. 즉, 업그레이드 후 네트워크 연결이 끊어질 수 있습니다.

### <a name="apps"></a>앱

설정 된 **업그레이드 결정** 뿐만 **중요도** 이 앱이 배포 계획에 대 한 합니다. 자세한 내용은 [배포 계획을 만드는 방법을](/sccm/desktop-analytics/create-deployment-plans)합니다.

앱의 세부 정보를 다음 정보를 확인할 수 있습니다. 권장 사항, 호환성 위험 요소 및 Microsoft의 알려진 문제 이 정보를 사용 하 여 도움말 집합은 **업그레이드 결정**합니다. 자세한 내용은 [Compatibility assessment](/sccm/desktop-analytics/compat-assessment)합니다.

데스크톱 분석으로 표시 하는 앱 *주목할 만한* 배포 계획의 준비 상태 규칙에 대 한 낮은 설치 수 임계값을 기반으로 합니다. 자세한 내용은 [준비 규칙](/sccm/desktop-analytics/create-deployment-plans#readiness-rules)합니다.

### <a name="drivers"></a>드라이버

이 배포 계획에 포함 된 드라이버 목록을 참조 하세요. 설정 된 **업그레이드 결정**에서 Microsoft의 권장 사항을 검토 하 고 호환성 위험 요소를 참조 하세요.


## <a name="importance"></a>중요도

배포 계획의 일부로 설정 합니다 *중요도* 앱. 데스크톱 분석 대상 장치에 설치 되어 이러한 앱을 검색 합니다. 이 설정은 데스크톱 Analytics 배포 파일럿 단계에 포함 하는 장치를 확인할 수 있습니다.

표시 된 앱의 대상된 장치 2% 미만에 설치 되어 있으면 **낮은 설치 수**입니다. 두 % 기본 값입니다. 10% 0%에서 준비 설정에 대 한 임계값을 조정할 수 있습니다. 데스크톱 분석에 따라 이러한 앱을 자동으로 표시 **업그레이드할 준비가**합니다.  

앱의 중요성을 선택할 **위험**를 **중요**, 또는 **중요 하지 않은**합니다. 중요 하거나 중요 한으로 하나를 표시 하는 경우 데스크톱 분석 해당 앱을 사용 하 여 일부 장치를 파일럿 배포에 포함 합니다. 서비스는 중요 한 앱의 인스턴스를 더 파일럿에 포함합니다. 중요 하지 않은 것으로 앱을 표시 하는 경우 데스크톱 Analytics 자동으로로 설정 합니다 **업그레이드할 준비가**합니다.



## <a name="pilot-devices"></a>파일럿 장치

데스크톱 분석 전역 파일럿 설정 사용 하 여 중요 정보를 결합합니다. 그런 다음 장치 파일럿 배포 중 이어야 합니다 하는 권장 사항을 만듭니다. 권장 되는 파일럿 배포에는 여러 하드웨어 구성 사용 하 여 장치 및 모든 중대 및 중요 앱의 인스턴스가 하나 이상 포함 됩니다. 앱 위험으로 표시 된 경우 서비스는 파일럿에서 해당 앱을 사용 하 여 더 많은 장치를 권장 합니다.



## <a name="deployment-plans-in-configuration-manager"></a>Configuration Manager에서 배포 계획

배포 계획을 만든 후 제품을 배포 하려면 Configuration Manager를 사용 합니다. 한 번 배포 시작 데스크톱 분석 계획의 설정에 따라 배포를 모니터링 합니다.


## <a name="next-steps"></a>다음 단계

- [데스크톱 분석 자산에 대 한 알아봅니다](/sccm/desktop-analytics/about-assets): 장치, 드라이버 및 앱  

- [보안 및 기능 업데이트에 알아봅니다](/sccm/desktop-analytics/about-updates)  

- [배포 계획 만들기](/sccm/desktop-analytics/create-deployment-plans)  
