---
title: 단계적 배포 관리 및 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager에서 소프트웨어에 대한 단계적 배포를 관리 및 모니터링하는 방법을 이해합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: dc245916-bc11-4983-9c4d-015f655007c1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1889ba3ea19d27676089f2a9a24cef812c9f526c
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385864"
---
# <a name="manage-and-monitor-phased-deployments"></a>단계적 배포 관리 및 모니터링

이 문서에서는 단계적 배포를 관리 및 모니터링하는 방법을 설명합니다. 관리 작업은 수동으로 다음 단계 시작 및 단계 일시 중단 또는 다시 시작을 포함합니다. 

먼저 [단계적 배포를 만들](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)어야 합니다. 



## <a name="bkmk_move"></a> 다음 단계로 이동

**수동으로 배포의 두 번째 단계 시작** 설정을 선택하면 사이트는 성공 조건에 따라 다음 단계를 자동으로 시작하지 않습니다. 단계적 배포를 다음 단계로 이동해야 합니다.  

1. 이 작업을 시작하는 방법은 배포되는 소프트웨어의 종류에 따라 다릅니다.  

    - **응용 프로그램**(버전 1806 이상에서만): **소프트웨어 라이브러리**로 이동하여 **응용 프로그램 관리**를 확장하고 **응용 프로그램**을 선택합니다.   

    - **작업 순서**: **소프트웨어 라이브러리** 작업 영역으로 이동하여 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.   

2. 단계적 배포를 사용하여 소프트웨어를 선택합니다.  

3. 세부 정보 창에서 **단계적 배포** 탭으로 전환합니다.  

4. 단계적 배포를 선택하고, 리본 메뉴에서 **다음 단계로 이동**을 클릭합니다.  

    ![단계적 배포에 대한 작업을 표시하는 메뉴를 마우스 오른쪽 단추로 클릭](media/Suspend-phased-deployment.PNG)



## <a name="bkmk_suspend"></a> 단계 일시 중단 및 다시 시작 

단계적 배포를 수동으로 일시 중단 또는 다시 시작해야 합니다. 예를 들어 작업 순서에 대한 단계적 배포를 만듭니다. 파일럿 그룹에 단계를 모니터링하는 동안 많은 오류가 표시됩니다. 단계적 배포를 일시 중단하여 장치에서 작업 순서를 더 실행하지 않도록 합니다. 문제를 해결한 후 단계적 배포를 다시 시작하여 출시를 계속합니다. 

1. 이 작업을 시작하는 방법은 배포되는 소프트웨어의 종류에 따라 다릅니다.  

    - **응용 프로그램**(버전 1806 이상에서만): **소프트웨어 라이브러리**로 이동하여 **응용 프로그램 관리**를 확장하고 **응용 프로그램**을 선택합니다.   

    - **작업 순서**: **소프트웨어 라이브러리** 작업 영역으로 이동하여 **운영 체제**를 확장하고 **작업 순서**를 선택합니다. 기존 작업 순서를 선택한 다음, 리본에서 **단계별 배포 만들기**를 클릭합니다.  

2. 단계적 배포를 사용하여 소프트웨어를 선택합니다.  

3. 세부 정보 창에서 **단계적 배포** 탭으로 전환합니다.  

4. 단계적 배포를 선택하고, 리본 메뉴에서 **일시 중단** 또는 **다시 시작**을 클릭합니다.  

<!-- Removed for 1806, need to clarify behavior with engineering
When you suspend a phased deployment, it sets the available and deadline times on the active deployments to a future time. When you resume, it generates a new schedule based on when you resume the phased deployment. The new schedule helps to avoid problems if you resume after the original deadline. For example, the initial schedule has the required deadline seven days after the deployment is available. You suspend it on the second day. If you aren't ready to resume it until day eight, you don't want the deployment to be immediately past the deadline. So it generates a new deadline starting from when you resume the phased deployment on day eight. 
-->


## <a name="bkmk_monitor"></a> 모니터
<!--1358577-->

버전 1806부터 단계적 배포에서 기본 모니터링 환경을 제공합니다. **모니터링** 작업 영역의 **배포** 노드에서 단계적 배포를 선택한 다음, 리본에서 **단계적 배포 상태**를 클릭합니다.

![두 단계의 상태를 보여 주는 단계적 배포 상태 대시보드](media/1358577-phased-deployment-status.png)

이 대시보드에는 배포의 각 단계에 대해 다음과 같은 정보가 표시됩니다.  

- **총 장치 수**: 이 단계의 대상으로 지정된 장치의 수입니다.  

- **상태**: 이 단계의 현재 상태입니다. 각 단계는 다음 상태 중 하나일 수 있습니다.  

    - **배포가 생성됨**: 단계적 배포에서 이 단계의 컬렉션에 대한 소프트웨어 배포를 만들었습니다. 클라이언트가 이 소프트웨어에서 적극적으로 대상으로 지정됩니다.  

    - **대기 중**: 이전 단계가 배포의 성공 조건에 도달하지 못해 이 단계를 계속 진행합니다.  

    - **일시 중단됨**: 관리자가 배포를 일시 중단했습니다.  

- **진행률**: 클라이언트에서 색으로 구분된 배포 상태입니다. 예를 들어 성공, 진행 중, 오류, 요구 사항에 맞지 않음, 알 수 없음 등이 있습니다. 

#### <a name="success-criteria-tile"></a>성공 조건 타일

**단계 선택** 드롭다운 목록을 사용하여 **성공 조건** 타일의 표시를 변경합니다. 이 타일은 **단계 목표**를 배포의 현재 규정 준수와 비교합니다. 기본 설정으로 단계 목표는 95%입니다. 이 값은 배포가 다음 단계로 이동하는 데 95% 규정 준수가 필요함을 의미합니다. 

이 예제에서 단계 목표는 65%이며, 현재 규정 준수는 66.7%입니다. 첫 번째 단계가 성공 조건을 충족했으므로 단계적 배포는 두 번째 단계로 자동으로 이동했습니다.
![단계적 배포 상태에서 예제 성공 조건 타일](media/pod-status-success-criteria-tile.png)

단계 목표는 *다음* 단계에 대한 단계 설정의 **배포 성공률**과 동일합니다. 단계적 배포의 경우 다음 단계를 시작하기 위해 해당 두 번째 단계는 첫 번째 단계의 성공 조건을 정의합니다. 이 설정을 보려면: 

1. 소프트웨어에서 단계적 배포 개체로 이동하고, 단계적 배포 속성을 엽니다.  

2. **단계** 탭으로 전환합니다. **2단계**를 선택하고 **보기**를 클릭합니다.  

3. 단계 속성 창에서 **단계 설정** 탭으로 전환합니다.  

4. *이전 단계의 성공을 위한 조건* 그룹에서 **배포 성공률**에 대한 값을 봅니다.  

예를 들어 다음 속성은 조건이 65%인 위에 표시된 성공 조건 타일과 동일한 단계에 대한 것입니다.  
![단계 속성의 단계 설정 탭](media/phase-properties-phase-settings.png)

