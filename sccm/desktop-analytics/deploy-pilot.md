---
title: 파일럿에 배포하는 방법
titleSuffix: Configuration Manager
description: Desktop Analytics 파일럿 그룹에 배포하는 방법에 대한 지침입니다.
ms.date: 06/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 637fbd8e-b8ea-4c7e-95ee-a60a323c496e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a8cbae87d0dce391ad8ad160f29a598ac044fece
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74190599"
---
# <a name="how-to-deploy-to-pilot-with-desktop-analytics"></a>Desktop Analytics를 사용하여 파일럿에 배포하는 방법

Desktop Analytics의 이점 중 하나는 가장 광범위한 요소의 적용 범위를 제공하는 가장 작은 디바이스 세트를 식별하는 데 도움을 주는 것입니다. Windows 업그레이드 및 업데이트의 파일럿에 가장 중요한 요소에 중점을 둡니다. 파일럿이 더 성공하도록 하면 프로덕션의 광범위한 배포로 더 빠르고 확실하게 이동할 수 있습니다.  

[!INCLUDE [Definition of pilot and production](includes/define-pilot-prod.md)]


## <a name="identify-devices"></a>디바이스 식별

첫 번째 단계는 파일럿에 포함할 디바이스를 식별하는 것입니다. Desktop Analytics에서는 보고된 데이터를 기반으로 디바이스를 권장하며, 이 목록에서 디바이스를 포함시키거나 바꿀 수 있습니다.

1. [Desktop Analytics 포털](https://aka.ms/desktopanalytics)로 이동하고, 관리 그룹에서 **배포 계획**를 선택합니다.

1. 배포 모델을 선택합니다.

1. 배포 계획 메뉴의 준비 그룹에서 **파일럿 식별**을 선택합니다.

Desktop Analytics의 데이터를 보면 최적의 검사를 위해 포함할 것이 권장되는 디바이스 수가 표시됩니다. 이 알고리즘은 주로 중요한 앱의 사용과 하드웨어 구성의 범위를 기반으로 합니다.

추가 권장 디바이스 목록에 대해 다음 작업을 수행합니다.

- **파일럿에 모두 추가**: 권장되는 모든 디바이스를 파일럿 그룹에 추가합니다.
- **파일럿에 추가**: 개별 디바이스만 추가합니다.
- 파일럿에서 특정 디바이스 **바꾸기**
- 변경 작업이 완료되면 **다시 계산**

## <a name="global-pilot"></a>글로벌 파일럿

또한 파일럿에서 포함하거나 제외할 Configuration Manager 컬렉션에 대해 시스템 차원의 결정을 내릴 수 있습니다. 주 Desktop Analytics 메뉴의 글로벌 설정 그룹에서 **글로벌 파일럿**을 선택합니다.

### <a name="example"></a>예

- **모든 시스템** 컬렉션을 대상으로 하도록 Configuration Manager의 Desktop Analytics 연결을 구성합니다. 이 작업을 통해 모든 클라이언트가 서비스에 등록됩니다.
- Desktop Analytics와 동기화할 추가 컬렉션도 구성합니다.
    - 모든 Windows 10 클라이언트
    - 모든 IT 디바이스
    - CEO 사무실
- **글로벌 파일럿** 설정에서 **모든 IT 디바이스** 컬렉션을 포함시킵니다. **CEO 사무실** 컬렉션을 제외시킵니다.
- 배포 계획을 만들고 **모든 Windows 10 클라이언트** 컬렉션을 **대상 그룹**으로 선택합니다.
- **파일럿 디바이스 포함** 목록에는 **대상 그룹**: **모든 Windows 10 클라이언트**(글로벌 파일럿 *포함* 목록: **모든 IT 디바이스**에도 있음)의 디바이스 하위 세트가 포함되어 있습니다.  
- **추가 권장 디바이스** 목록에는 중요한 자산의 중복 및 최대의 적용 범위를 제공하는 **대상 그룹**의 디바이스 세트가 포함되어 있습니다.  Desktop Analytics는 글로벌 파일럿 *제외* 목록: **CEO 사무실**의 모든 디바이스를 이 목록에서 제외합니다.


## <a name="address-issues"></a>문제 해결

Desktop Analytics 포털을 사용하여 배포를 차단할 수 있는 자산에 대해 보고된 문제를 검토합니다. 그런 다음, 제안된 수정 사항을 승인, 거부 또는 수정합니다. 파일럿 배포를 시작하기 전에 모든 항목이 **준비 완료** 또는 **업데이트 관리 준비 완료**로 표시되어야 합니다.

1. [Desktop Analytics 포털](https://aka.ms/desktopanalytics)로 이동하고, 관리 그룹에서 **배포 계획**를 선택합니다.  

2. 배포 모델을 선택합니다.  

3. 배포 계획 메뉴의 준비 그룹에서 **파일럿 준비**를 선택합니다.  

4. **앱** 탭에서 입력이 필요한 앱을 검토합니다.  

5. 각 앱에 대해 앱 이름을 선택합니다. 정보 창에서 권장 사항을 검토하고 업그레이드 결정을 선택합니다. **검토되지 않음** 또는 **불가능**을 선택하는 경우 Desktop Analytics는 파일럿 배포에 이 앱이 있는 디바이스를 포함시키지 않습니다. **업데이트 관리 준비 완료**를 선택하는 경우 **업데이트 관리 정보**를 사용하여 문제를 해결하기 위해 수행할 작업(예: *다시 설치* 또는 *제조업체의 권장 버전 찾기*)을 캡처합니다.

6. 다른 자산에 대해 이 검토를 반복합니다.  


## <a name="create-software"></a>소프트웨어 만들기

Windows를 배포하기 전에 먼저 Configuration Manager에서 소프트웨어 개체를 만듭니다. 자세한 내용은 [Windows 10 현재 위치 업그레이드 작업 순서](https://docs.microsoft.com/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)를 참조하세요.


## <a name="deploy-to-pilot-devices"></a>파일럿 디바이스에 배포

Configuration Manager는 Desktop Analytics의 데이터를 사용하여 파일럿 및 프로덕션 배포를 위한 컬렉션을 만듭니다. 각 배포 단계 이후 디바이스가 정상 상태인지 확인하려면 다음 절차를 사용하여 Desktop Analytics 통합 단계별 배포를 만듭니다.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**로 이동하여 **Desktop Analytics Servicing**을 확장시킨 후, **배포 계획** 노드를 선택합니다.  

2. 배포 계획을 선택한 다음, 리본에서 **배포 계획 세부 정보**를 선택합니다.  

3. 리본에서 **단계적 배포 만들기**를 선택합니다. 그러면 단계적 배포 만들기 마법사가 시작됩니다.

    > [!Tip]  
    > 파일럿 컬렉션에 대해서만 클래식 작업 순서 배포를 만들려면 **파일럿 상태** 타일에서 **배포**를 선택합니다. 그러면 배포 소프트웨어 마법사가 시작됩니다. 자세한 내용은 [Deploy a task sequence](/sccm/osd/deploy-use/deploy-a-task-sequence)항목을 참조하세요.  

4. 배포에 사용할 이름을 입력하고 사용할 작업 순서를 선택합니다. 옵션을 사용하여 **기본 두 단계 배포를 자동으로 만든** 다음, 다음과 같은 컬렉션을 구성합니다.  

    - **첫 번째 컬렉션**: 이 배포 계획에 대한 **파일럿** 컬렉션을 찾아 선택합니다. 이 컬렉션에 대한 표준 명명 규칙은 `<deployment plan name> (Pilot)`입니다.

    - **두 번째 컬렉션**: 이 배포 계획에 대한 **프로덕션** 컬렉션을 찾아 선택합니다. 이 컬렉션에 대한 표준 명명 규칙은 `<deployment plan name> (Production)`입니다.

    > [!Note]  
    > Desktop Analytics 통합을 사용하면 Configuration Manager에서 배포 계획에 대한 파일럿 및 프로덕션 컬렉션을 자동으로 생성합니다. 이러한 컬렉션을 동기화하여 사용할 수 있을 때까지 시간이 걸릴 수 있습니다. 자세한 내용은 [문제 해결 - 데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조하세요.<!-- 4984639 -->
    >
    > 이러한 컬렉션은 Desktop Analytics 배포 계획 디바이스용으로 예약되어 있습니다. 이러한 컬렉션에 대한 수동 변경은 지원되지 않습니다.<!-- 3866460, SCCMDocs-pr 3544 -->  

5. 단계적 배포를 구성하는 마법사를 완료합니다. 자세한 내용은 [단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)를 참조하세요.

    > [!Note]  
    > 기본 설정을 사용하여 **지연 기간(일) 후 자동으로 이 단계를 시작**합니다. 두 번째 단계를 시작하려면 다음 조건을 충족해야 합니다.
    >
    > 1. 첫 번째 단계는 성공에 필요한 **배포 성공 비율** 조건에 도달합니다. 단계적 배포에서 이 설정을 구성합니다.
    > 1. Desktop Analytics에서 업그레이드 결정을 검토하고 수행하여 중요한 자산을 *준비*로 표시해야 합니다. 자세한 내용은 [업그레이드 결정이 필요한 자산 검토](/sccm/desktop-analytics/deploy-prod#bkmk_review)를 참조하세요.
    > 1. Desktop Analytics는 *준비 완료* 조건을 충족하는 프로덕션 디바이스와 Configuration Manager 컬렉션을 동기화합니다.

> [!Important]  
> 이러한 컬렉션은 멤버 자격이 변경됨에 따라 계속 동기화됩니다. 예를 들어 자산에 있는 문제를 식별하여 이를 **불가능**으로 표시하면 해당 자산이 포함된 디바이스는 더 이상 *준비 완료* 기준을 충족하지 않습니다. 이러한 디바이스는 프로덕션 배포 컬렉션에서 삭제됩니다.


## <a name="monitor"></a>모니터

### <a name="configuration-manager-console"></a>Configuration Manager 콘솔

배포 계획을 엽니다. **업그레이드 결정 준비 - 전체 상태** 타일은 배포 계획의 상태에 대한 요약을 제공합니다. 이 상태는 파일럿 및 프로덕션 컬렉션 모두에 대한 상태입니다. 디바이스는 다음 범주 중 하나에 속합니다.

- **최신 상태**: 이 배포 계획에 대한 대상 Windows 버전으로 디바이스를 업그레이드했습니다.

- **업그레이드 결정 완료**: 다음과 같은 상태 중 하나:
    - **준비 완료** 또는 **업데이트 관리 준비 완료**인 중요한 자산이 있는 디바이스
    - 디바이스 상태가 **차단**, [**디바이스 바꾸기**](/sccm/desktop-analytics/about-deployment-plans#plan-assets) 또는 **디바이스 다시 설치**임

- **검토되지 않음**: **검토되지 않음** 또는 **검토 진행 중**인 중요한 자산이 있는 디바이스

다음 작업을 통해 **파일럿 상태** 및 **프로덕션 상태** 타일에서 디바이스 상태가 업데이트됩니다.

- 호환성 평가에 대한 변경을 수행
- 디바이스가 대상 버전의 Windows로 업그레이드됨
- 배포 진행

또한 다른 작업 순서 배포와 동일하게 Configuration Manager 배포 모니터링을 사용할 수 있습니다. 자세한 내용은 [OS 배포 모니터링](/sccm/osd/deploy-use/monitor-operating-system-deployments)을 참조하세요.


### <a name="desktop-analytics-portal"></a>Desktop Analytics 포털

[Desktop Analytics 포털](https://aka.ms/desktopanalytics)을 사용하여 배포 계획의 상태를 봅니다. 배포 계획을 선택한 다음, **계획 개요**를 선택합니다.

![Desktop Analytics의 배포 계획 개요 스크린샷](media/deployment-plan-overview.png)

**파일럿** 타일을 선택합니다. 파일럿 배포의 현재 상태를 요약합니다. 이 타일에는 시작되지 않음, 진행 중, 완료됨 또는 문제 반환 디바이스 수에 대한 데이터도 표시됩니다.

오류 또는 기타 문제를 보고하는 모든 디바이스는 오른쪽의 파일럿 세부 정보 영역에도 나열됩니다. 보고된 문제에 대한 자세한 내용을 보려면 **검토**를 선택합니다. 이 작업을 수행하면 보기가 **배포 상태** 페이지로 변경됩니다.

**배포 상태** 페이지에는 다음 범주의 디바이스가 나열됩니다.

- 시작 안 됨
- 진행 중
- 완료
- 주의 필요 - 디바이스
- 주의 필요 - 문제

**주의 필요** 범주는 동일한 정보를 표시하지만 다르게 정렬됩니다.

검색된 문제에 대한 자세한 정보를 보려면 각 보기에서 특정 목록을 선택합니다.

이러한 배포 문제를 해결하는 동안 대시보드에는 계속해서 디바이스의 진행 상황이 표시됩니다. 디바이스가 **주의 필요**에서 **완료됨**으로 이동하면 업데이트됩니다.


## <a name="next-steps"></a>다음 단계

작업 데이터를 수집하는 동안 파일럿을 실행할 수 있습니다. 파일럿 디바이스의 사용자가 앱을 테스트하도록 권장합니다.

파일럿 배포가 성공 조건을 충족하는 경우 다음 문서로 이동하여 프로덕션에 배포합니다.
> [!div class="nextstepaction"]  
> [프로덕션에 배포](/sccm/desktop-analytics/deploy-prod)  
