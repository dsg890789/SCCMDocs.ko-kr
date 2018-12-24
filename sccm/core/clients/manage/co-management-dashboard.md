---
title: 공동 관리 대시보드
titleSuffix: Configuration Manager
description: 공동 관리 대시보드를 사용하여 공동 관리형 디바이스에 관한 정보를 검토합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e83a7b0d-b381-4b4a-8eca-850385abbebb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ad76140285df1c0125fcd2efab0f4794ed4881bf
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52455950"
---
# <a name="co-management-dashboard-in-configuration-manager"></a>Configuration Manager의 공동 관리 대시보드

*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1802부터는 공동 관리에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 대시보드를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 디바이스를 식별하는 데 도움이 될 수 있습니다.<!--1356648-->

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **공동 관리** 노드를 선택합니다.

1810 버전부터 공동 관리 대시보드가 좀 더 자세한 정보로 개선되었습니다. <!--1358980-->



## <a name="dashboard-tiles"></a>대시보드 타일 

공동 관리 대시보드는 사이트 버전에 따라 여러 타일을 보여줍니다. 


### <a name="co-managed-devices"></a>공동 관리형 디바이스

*버전 1802 및 1806에 적용*

환경 전체에서 공동 관리형 디바이스의 백분율을 표시합니다.
 ![공동 관리형 디바이스 타일](media\co-management-dashboard\Percent-Co-managed-graph.PNG)


### <a name="client-os-distribution"></a>클라이언트 OS 배포

*모든 버전에 적용* 

OS당 클라이언트 디바이스의 수를 버전별로 표시합니다. 다음과 같은 그룹화를 사용합니다.  
- Windows 7 & 8.x  
- 1709 이하의 Windows 10  
- Windows 10 1709 이상  

    > [!Tip]  
    > Windows 10, 1709 이상 버전은 공동 관리에 필수 구성 요소입니다.  

그래프 섹션을 마우스로 가리키면 OS 그룹에서 디바이스의 백분율이 표시됩니다.
 ![클라이언트 OS 배포 타일](media\co-management-dashboard\Co-management-OS-distribution-graph.PNG)


### <a name="co-management-status-donut"></a>공동 관리 상태(도넛형)

*버전 1802 및 1806에 적용*

다음 범주에 디바이스의 성공 또는 실패에 대한 분석 결과를 표시합니다.
- 성공, 하이브리드 Azure AD 조인됨  
- 성공, Azure AD 조인됨  
- 실패: 자동 등록 실패함  

그래프 섹션을 마우스로 가리키면 해당 범주에서 디바이스의 백분율이 표시됩니다. 
 ![공동 관리 상태(도넛형) 타일](media\co-management-dashboard\Co-management-status-graph.PNG)

해당 범주에 대한 디바이스 목록을 보려면 그래프 섹션을 선택합니다.
 ![등록 실패 디바이스 목록](media\co-management-dashboard\Enrollment-Failure_Device-List.PNG)


### <a name="co-management-status-funnel"></a>공동 관리 상태(깔대기형)

*버전 1810 이상에 적용*

등록 프로세스의 다음과 같은 상태를 사용하여 디바이스의 수를 표시하는 깔때기형 차트:  
- 적격 디바이스  
- 예약됨  
- 등록이 시작됨  
- 등록됨  

![공동 관리 상태(깔대기형) 타일](media\co-management-dashboard\1358980-status-funnel.png)


### <a name="co-management-enrollment-status"></a>공동 관리 등록 상태

*버전 1810 이상에 적용*

다음 범주에 디바이스 상태의 분석 결과를 표시합니다.
- 성공, 하이브리드 Azure AD 조인됨  
- 성공, Azure AD 조인됨  
- 등록 중, 하이브리드 Azure AD 조인됨  
- 실패, 하이브리드 Azure AD 조인됨  
- 실패, Azure AD 조인됨  
- 사용자 로그인 보류 중  

타일에서 상태를 선택하여 해당 상태의 디바이스 목록으로 드릴스루합니다.  

![공동 관리 등록 상태 타일](media\co-management-dashboard\1358980-enrollment-status.png)


### <a name="enrollment-errors"></a>등록 오류

*버전 1810 이상에 적용*

디바이스에서 등록 오류의 수를 표시하는 테이블입니다.  


### <a name="workload-transition"></a>워크로드 전환

*모든 버전에 적용*

사용 가능한 워크로드에 대해 Microsoft Intune으로 전환한 디바이스 수를 포함한 가로 막대형 차트를 표시합니다. (워크로드의 목록은 Configuration Manager의 버전에 따라 달라집니다. 자세한 내용은 [Intune으로 전환될 수 있는 워크로드](/sccm/core/clients/manage/co-management-switch-workloads#workloads-able-to-be-transitioned-to-intune)를 참조하세요.)

차트 섹션을 마우스로 가리키면 워크로드에 대해 전환된 디바이스 수가 표시됩니다. 
 ![워크로드 전환 막대 그래프](media\co-management-dashboard\Workload-Transition.PNG)


## <a name="next-steps"></a>다음 단계

공동 관리에 대한 자세한 내용은 다음을 참조하세요.
 - [Windows 10 장치에 대한 공동 관리](/sccm/core/clients/manage/co-management-overview)
 - [공동 관리를 위해 Windows 10 장치 준비](/sccm/core/clients/manage/co-management-prepare)

    
