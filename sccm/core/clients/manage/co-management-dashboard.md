---
title: 공동 관리 대시보드
titleSuffix: Configuration Manager
description: 대시보드를 사용하여 공동 관리에 대한 정보를 검토합니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e83a7b0d-b381-4b4a-8eca-850385abbebb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 72b42aec2b50e229b90e9a642343386e8588aab7
ms.sourcegitcommit: 2cc635835709fb8d86cdb63ea34233b36c94d4d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52259007"
---
# <a name="co-management-dashboard-in-system-center-configuration-manager"></a>System Center Configuration Manager의 공동 관리 대시보드
*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1802부터는 공동 관리에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 대시보드를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 장치를 식별하는 데 도움이 될 수 있습니다.<!--1356648-->

## <a name="open-the-co-management-dashboard"></a>공동 관리 대시보드 열기
공동 관리 대시보드를 열려면 다음 단계를 사용합니다. 

1. Configuration Manager 콘솔을 엽니다. 
2. **모니터링** 노드를 클릭합니다. 
3. 대시보드를 로드하려면 **공동 관리**를 클릭합니다.

## <a name="reviewing-information-in-the-co-management-dashboard"></a>공동 관리 대시보드의 정보 검토

공동 관리 대시보드에서는 환경에 대한 4개의 그래프를 표시합니다. 

- **공동 관리 장치** - 환경 전체에서 공동 관리 장치의 백분율을 제공합니다.

    ![공동 관리 장치 그래프](media\co-management-dashboard\Percent-Co-managed-graph.PNG)

- **클라이언트 OS 배포** - 버전에서 OS당 클라이언트 장치의 수를 표시합니다. 다음 그룹을 사용합니다. </br>
    - Windows 7 & 8.x
    - 1709 이하의 Windows 10
    - Windows 10 1709 이상

         > [!NOTE] 
         > Windows 10, 1709 이상 버전은 공동 관리에 필수 구성 요소입니다.

     그래프 섹션을 마우스로 가리키면 선택한 OS 그룹에서 장치의 백분율을 제공합니다.

     ![클라이언트 OS 배포의 그래프](media\co-management-dashboard\Co-management-OS-distribution-graph.PNG)

- **공동 관리 상태** - 다음 범주에서 장치의 성공 또는 실패를 분류합니다.
    - 성공, 하이브리드 Azure AD 조인됨
    - 성공, Azure AD 조인됨
    - 실패: 자동 등록 실패함
    
     그래프 섹션을 마우스로 가리키면 범주에서 장치의 백분율을 제공합니다. 

     ![공동 관리에 대한 상태 그래프](media\co-management-dashboard\Co-management-status-graph.PNG)

     그래프 섹션을 클릭하면 범주에 대한 장치 목록으로 이동합니다.
 
     ![등록 실패 장치 목록](media\co-management-dashboard\Enrollment-Failure_Device-List.PNG)


- **워크로드 전환** - 사용 가능한 네 가지 작업 부하에 대해 Microsoft Intune으로 전환한 장치 수를 포함한 가로 막대형 차트를 표시합니다.
    - 규정 준수 정책
    - 리소스 액세스
    - Windows Update for Business
    - Endpoint Protection

     차트 섹션을 마우스로 가리키면 워크로드에 대해 전환된 장치 수를 제공합니다. 
     ![워크로드 전환 막대 그래프](media\co-management-dashboard\Workload-Transition.PNG)


## <a name="next-steps"></a>다음 단계

공동 관리에 대한 자세한 내용은 다음을 참조하세요.
 - [Windows 10 장치에 대한 공동 관리](/sccm/core/clients/manage/co-management-overview)
 - [공동 관리를 위해 Windows 10 장치 준비](/sccm/core/clients/manage/co-management-prepare)

    
