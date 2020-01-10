---
title: 콘텐츠 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔을 사용하여 분산 콘텐츠를 모니터링하는 방법을 이해합니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 82e8a693-9adf-4ca3-8484-7e101c34c7c1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0880d4767da94b032b66a0ef354f6ea354705c83
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75798636"
---
# <a name="monitor-content-you-distribute-with-configuration-manager"></a>Configuration Manager를 사용하여 배포하는 콘텐츠 모니터링

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 콘솔을 사용하여 다음을 포함하는 분산 콘텐츠를 모니터링합니다.  

- 연결된 배포 지점의 모든 패키지 유형의 상태  
- 패키지 내 콘텐츠의 콘텐츠 유효성 검사 상태  
- 특정 배포 지점 그룹에 할당된 콘텐츠의 상태  
- 배포 지점에 할당된 콘텐츠의 상태  
- 각 배포 지점에 대한 선택적 기능(콘텐츠 유효성 검사, PXE, 멀티캐스트)의 상태  

> [!NOTE]  
> Configuration Manager는 콘텐츠 라이브러리에 있는 배포 지점의 콘텐츠만 모니터링합니다. 패키지의 배포 지점이나 사용자 지정 공유에 저장된 콘텐츠는 모니터링하지 않습니다.  

## <a name="BKMK_ContentStatus"></a> 콘텐츠 상태 모니터링

**모니터링** 작업 영역의 **콘텐츠 상태** 노드에는 콘텐츠 패키지에 대한 정보가 제공됩니다. Configuration Manager 콘솔에서 다음과 같은 정보를 검토합니다.  

- 패키지 이름, 유형, ID
- 패키지가 전송된 배포 지점 수
- 준수 비율
- 패키지 작성 시간
- 원본 버전

다음을 포함하여 패키지의 자세한 상태 정보도 찾을 수 있습니다.  

- 배포 상태
- 오류 횟수
- 보류 중인 배포  
- 설치 횟수

또한 배포 지점에 대해 진행 중인 배포나 배포 지점으로 콘텐츠를 배포하지 못한 배포도 관리할 수 있습니다.  

- **자산 정보** 창에서 배포 지점에 대한 배포 작업의 배포 상태 메시지를 볼 때 콘텐츠를 취소하거나 다시 배포하는 옵션. 이 창은 **콘텐츠 상태** 노드의 **진행 중** 탭이나 **오류** 탭에서 찾을 수 있습니다.  
- 작업 세부 정보에는 **진행 중** 탭에서 작업 세부 정보를 볼 때 완료된 작업의 백분율도 표시됩니다. 작업 세부 정보에는 작업에 남아 있는 재시도 횟수도 표시됩니다. **오류** 탭에 표시되는 작업의 세부 정보는 다음 재시도까지 남은 시간도 보여 줍니다.  

아직 완료되지 않은 배포를 취소하면 해당 콘텐츠를 전송할 배포 작업이 중지됩니다.  

- 그러면 배포 상태가 업데이트되어, 배포가 실패했고 사용자 작업에 의해 취소되었음을 나타냅니다.  
- 이 새로운 상태는 **오류** 탭에 표시됩니다.  

> [!NOTE]  
> 배포가 거의 완료된 경우 해당 배포를 취소하는 작업은 배포 지점에 대한 배포가 완료되기 전에 처리되지 않을 수 있습니다. 이 경우 배포 취소가 무시되고 배포 상태가 성공으로 표시됩니다.  
>
> 사이트 서버에 있는 배포 지점에 대한 배포 취소 옵션은 선택 가능하지만 아무 효과가 없습니다. 이 동작의 원인은 사이트 서버와 사이트 서버의 배포 지점이 동일한 인스턴스 콘텐츠 저장소 하나를 공유하기 때문입니다. 즉, 취소할 실제 배포 작업이 없습니다.  

이전에 배포 지점으로 전송하지 못한 콘텐츠를 재배포하면 Configuration Manager에서 해당 콘텐츠를 배포 지점으로 즉시 재배포하기 시작합니다. Configuration Manager에서 배포 상태를 업데이트하여 진행 중인 재배포 상태를 반영합니다.  

### <a name="tasks-to-monitor-content"></a>콘텐츠 모니터링 작업

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **배포 상태**를 펼친 다음 **콘텐츠 상태** 노드를 선택합니다. 이 노드는 패키지를 표시합니다.  

2. 관리할 패키지를 선택합니다.  

3. 리본의 **홈** 탭에 있는 **콘텐츠** 그룹에서 **상태 보기**를 선택합니다. 패키지의 자세한 상태 정보가 콘솔에 표시됩니다.

다음 섹션 중 하나를 진행하여 추가 작업을 수행합니다.

#### <a name="cancel-a-distribution-that-remains-in-progress"></a>진행 중 상태로 남아 있는 배포 취소  

1. **진행 중** 탭으로 전환합니다.

2. **자산 세부 정보** 창에서 취소하려는 배포 항목을 마우스 오른쪽 단추로 클릭하고 **취소**를 선택합니다.  

3. **예**를 선택하여 작업을 확인하고 해당 배포 지점에 대한 배포 작업을 취소합니다.  

#### <a name="redistribute-content-that-failed-to-distribute"></a>배포에 실패한 콘텐츠 재배포  

1. **오류** 탭으로 전환합니다.

2. **자산 세부 정보** 창에서 재배포하려는 배포 항목을 마우스 오른쪽 단추로 클릭하고 **재배포**를 선택합니다.  

3. **예**를 선택하여 작업을 확인하고 해당 배포 지점에 대한 재배포 프로세스를 시작합니다.  


## <a name="distribution-point-group-status"></a>배포 지점 그룹 상태

**모니터링** 작업 영역의 **배포 지점 그룹 상태** 노드에는 배포 지점 그룹에 대한 정보가 제공됩니다. 다음과 같은 정보를 검토할 수 있습니다.  

- 배포 지점 그룹 이름, 설명, 상태
- 배포 지점 그룹의 구성원인 배포 지점 수
- 그룹에 할당된 패키지 수
- 준수 비율

다음과 같은 자세한 상태 정보도 볼 수 있습니다.  

- 배포 지점 그룹 오류  
- 진행 중인 배포 수
- 정상적으로 완료된 배포 수  

### <a name="monitor-distribution-point-group-status"></a>배포 지점 그룹 상태 모니터링  

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **배포 상태**를 펼친 다음 **배포 지점 그룹 상태** 노드를 선택합니다. 배포 지점 그룹이 표시됩니다.  

2. 자세한 상태 정보를 볼 배포 지점 그룹을 선택합니다.  

3. 리본의 **홈** 탭에서 **상태 보기**를 선택합니다. 배포 지점 그룹의 자세한 상태 정보가 표시됩니다.  


## <a name="distribution-point-configuration-status"></a>배포 지점 구성 상태

**모니터링** 작업 영역의 **배포 지점 구성 상태** 노드에는 배포 지점에 대한 정보가 제공됩니다. PXE, 멀티캐스트, 콘텐츠 유효성 검사 등 배포 지점에 사용하도록 설정된 특성이 무엇인지 검토할 수 있습니다. 배포 지점의 배포 상태도 검토하세요.

> [!WARNING]  
> 배포 지점 구성 상태는 지난 24시간을 기준으로 합니다. 배포 지점에 오류가 있는 경우 이를 복구하면 배포 지점을 복구한 후 최대 24시간 동안의 오류 상태가 표시될 수 있습니다.  

### <a name="monitor-distribution-point-configuration-status"></a>배포 지점 구성 상태 모니터링  

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **배포 상태**를 펼친 다음 **배포 지점 구성 상태** 노드를 선택합니다.  

2. 배포 지점을 선택합니다.  

3. 결과 창에서 **세부 정보** 탭으로 전환합니다. 배포 지점의 상태 정보가 표시됩니다.  


## <a name="client-data-sources-dashboard"></a>클라이언트 데이터 원본 대시보드

환경에서 클라이언트가 콘텐츠를 가져오는 위치를 보다 잘 이해하려면 **클라이언트 데이터 원본** 대시보드를 사용하세요. 대시보드는 클라이언트에서 콘텐츠를 다운로드하고 해당 정보를 다시 사이트에 보고한 후 데이터를 표시하기 시작합니다. 이 프로세스는 최대 24시간이 소요될 수 있습니다.

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. **클라이언트 피어 캐시** 기능을 사용하려면 먼저 해당 기능을 사용하도록 설정해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **배포 상태**를 펼친 다음 **클라이언트 데이터 원본** 노드를 선택합니다. 대시보드에 적용할 기간을 선택합니다. 그런 다음 정보를 보려는 경계 그룹을 선택합니다. 타일을 마우스 커서로 가리키면 다양한 콘텐츠 또는 정책 원본에 대한 더 많은 세부 정보를 볼 수 있습니다.

또한 **클라이언트 데이터 원본: 요약** 보고서를 사용하여 각 경계 그룹에 대한 클라이언트 데이터 원본의 요약을 볼 수 있습니다.

### <a name="dashboard-tiles"></a>대시보드 타일

이 대시보드에는 다음과 같은 타일이 있습니다.  

#### <a name="client-content-sources"></a>클라이언트 콘텐츠 원본

클라이언트가 콘텐츠를 가져오는 다음 원본을 표시합니다.

- 배포 지점
- [클라우드 배포 지점](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)
- [BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#bkmk_branchcache)
- [피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)
- [배달 최적화](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization)(버전 1906부터)<sup>[참고 1](#bkmk_note1)</sup>
- Microsoft 업데이트: Configuration Manager 클라이언트가 Microsoft 클라우드 서비스로부터 소프트웨어 업데이트를 다운로드할 때 디바이스가 이 원본을 보고합니다. 이러한 서비스는 Microsoft 업데이트와 Office 365를 포함합니다.

![대시보드의 클라이언트 콘텐츠 원본 타일](media/3555759-do-source.png)

<a name="bkmk_note1"></a>

> [!Note]  
> 버전 1906부터<!--3555759-->이 대시보드에 배달 최적화를 포함하려면 다음 작업을 수행합니다.
>
> - 소프트웨서 업데이트 그룹에서 **클라이언트에서 빠른 업데이트 설치 사용** 클라이언트 설정 구성
>
> - Windows 10 빠른 업데이트 배포
>
> 자세한 내용은 [Windows 10 업데이트에 대한 빠른 설치 파일 관리](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)를 참조하세요.

#### <a name="distribution-points"></a>배포 지점

선택된 경계 그룹에 속한 배포 지점 수를 표시합니다.

#### <a name="clients-that-used-a-distribution-point"></a>배포 지점을 사용한 클라이언트

이 타일은 선택된 경계 그룹에 포함된 클라이언트 수 중에서 콘텐츠를 가져오기 위해 사용된 배포 지점 수를 표시합니다.

#### <a name="peer-cache-sources"></a>피어 캐시 원본

선택된 경계 그룹의 경우 이 타일은 보고된 다운로드 기록이 있는 피어 캐시 원본 수를 표시합니다.

#### <a name="clients-that-used-a-peer"></a>피어를 사용한 클라이언트

이 타일은 선택된 경계 그룹에 포함된 클라이언트 수 중에서 콘텐츠를 가져오기 위해 사용된 피어 캐시 원본 수를 표시합니다.

#### <a name="top-distributed-content"></a>가장 많이 배포된 콘텐츠

원본 유형별 가장 분산된 패키지
