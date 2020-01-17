---
title: 계층 모니터링
titleSuffix: Configuration Manager
description: 콘솔의 모니터링 작업 영역을 사용하여 Configuration Manager에서 인프라를 모니터링하는 방법을 알아봅니다.
ms.date: 06/06/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 007dbb73-18a7-48a3-a489-97cf9fc4f140
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 93b2ab22b0503dd673a8f0ad85da91449e327185
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75794660"
---
# <a name="monitor-the-hierarchy"></a>계층 모니터링

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager에서 계층을 모니터링하려면 Configuration Manager 콘솔에서 **모니터링** 작업 영역을 사용합니다.  

> [!NOTE]  
> 이 위치의 예외는 사이트를 마이그레이션하는 경우입니다. **관리** 작업 영역의 **마이그레이션** 노드에서 이 프로세스를 모니터링했습니다. 자세한 내용은 [Configuration Manager 현재 분기로의 마이그레이션을 위한 작업](/sccm/core/migration/operations-for-migration)을 참조하세요.  

모니터링을 위한 Configuration Manager 콘솔 외에 다음 기능을 사용합니다.

- [보고](/sccm/core/servers/manage/reporting)
- [로그 파일](/sccm/core/plan-design/hierarchy/log-files).  

사이트를 모니터링할 때에는 조치가 필요한 문제를 나타내는 징후를 확인합니다. 예를 들면 다음과 같습니다.  

- 사이트 서버 또는 사이트 시스템에 있는 파일 백로그  

- 오류 또는 문제를 나타내는 상태 메시지  

- 사이트 간 통신 실패  

- 서버의 시스템 이벤트 로그에 있는 오류 및 경고 메시지  

- Microsoft SQL Server 오류 로그에 있는 오류 및 경고 메시지  

- 오랫동안 상태를 보고하지 않은 사이트 또는 클라이언트  

- SQL Server 데이터베이스에서 응답이 느림  

- 하드웨어 오류 증상  

모니터링 작업에서 문제의 징후가 확인되면 문제의 원인을 조사하세요. 그런 다음, 빠르게 복구하여 사이트 실패 위험을 최소화합니다.  


## <a name="BKMK_MonintorMgmtTasks"></a> 일반 관리 작업 모니터링

Configuration Manager는 Configuration Manager 콘솔 내에서 기본 제공 모니터링을 제공합니다.

### <a name="alerts"></a>경고

자세한 내용은 [경고 모니터링](/sccm/core/servers/manage/use-alerts-and-the-status-system#BKMK_MonitorAlerts)을 참조하세요.  

### <a name="compliance-settings"></a>호환성 설정

자세한 내용은 [준수 설정을 모니터링하는 방법](/sccm/compliance/deploy-use/monitor-compliance-settings)을 참조하세요.

### <a name="content"></a>Content

콘텐츠를 모니터링하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  

특정 유형의 콘텐츠를 모니터링하는 방법에 대한 정보:

- [애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)

- [패키지 및 프로그램 모니터링](/sccm/apps/deploy-use/packages-and-programs#monitor-packages-and-programs)  

- [소프트웨어 업데이트에 대한 콘텐츠 모니터링](/sccm/sum/deploy-use/monitor-software-updates#BKMK_MonitorContent)

- [OS 배포에 대한 콘텐츠 모니터링](/sccm/osd/deploy-use/monitor-operating-system-deployments#BKMK_MonitorContent)

### <a name="endpoint-protection"></a>Endpoint Protection

자세한 내용은 [Endpoint Protection 모니터링 방법](/sccm/protect/deploy-use/monitor-endpoint-protection)을 참조하세요.  

### <a name="os-deployment"></a>OS 배포

자세한 내용은 [OS 배포 모니터링](/sccm/osd/deploy-use/monitor-operating-system-deployments)을 참조하세요.

### <a name="monitor-power-management"></a>전원 관리 모니터링

자세한 내용은 [전원 관리를 모니터링하고 계획하는 방법](/sccm/core/clients/manage/power/monitor-and-plan-for-power-management)을 참조하세요.  

### <a name="monitor-software-metering"></a>소프트웨어 계량 모니터링

자세한 내용은 [소프트웨어 계량을 사용하여 앱 사용 모니터링](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)을 참조하세요.  

### <a name="monitor-software-updates"></a>소프트웨어 업데이트 모니터링

자세한 내용은 [소프트웨어 업데이트 모니터링](/sccm/sum/deploy-use/monitor-software-updates)을 참조하세요.  


## <a name="BKMK_SH_Node"></a> 사이트 계층 구조 모니터링

**모니터링** 작업 영역의 **사이트 계층** 노드에서는 Configuration Manager 계층 구조 및 사이트 간 링크의 개요를 제공합니다. 두 가지 보기를 사용할 수 있습니다.  

- **계층 다이어그램**: 중요한 정보만 표시하는 단순화된 토폴로지 맵으로 계층을 표시합니다. 자세한 내용은 [계층 다이어그램](#hierarchy-diagram)을 참조하세요.  

- **지리적 보기**: 구성된 사이트 위치를 보여 주는 지리적 맵에 사이트를 표시합니다. 자세한 내용은 [지리적 보기](#geographical-view)를 참조하세요.  

**사이트 계층** 노드를 사용하여 각 사이트의 상태를 모니터링합니다. 또한 사이트 간 복제 링크 및 외부 요소와의 관계(예: 지리적 위치)를 모니터링합니다.  

사이트 상태 및 사이트 간 링크 상태는 모두 글로벌 데이터가 아닌 사이트 데이터로 복제됩니다. Configuration Manager 콘솔을 하위 기본 사이트에 연결할 때 다른 기본 사이트 또는 하위 보조 사이트의 사이트 또는 링크 상태를 볼 수 없습니다. 예를 들어, 기본 사이트를 여러 개 포함하는 계층에서 콘솔을 기본 사이트에 연결할 때 자식 보조 사이트, 기본 사이트 및 중앙 관리 사이트의 상태를 볼 수 있습니다. 이 보기에서는 중앙 관리 사이트 아래에 있는 다른 사이트의 상태를 볼 수 없습니다.  

**사이트 계층** 노드의 표시를 제어하려면 **설정 구성** 작업을 사용합니다. 계층은 이 노드에서 구성하는 설정을 복제합니다.  

### <a name="hierarchy-diagram"></a>계층 다이어그램

계층 다이어그램에는 토폴로지 맵의 사이트가 표시됩니다. 사이트를 선택하고 해당 사이트의 상태 메시지 요약을 확인합니다. 드릴다운하여 상태 메시지를 확인하고 사이트 **속성**에 액세스합니다.  

사이트 또는 사이트 간 복제 링크의 고급 상태를 보려면 마우스 포인터로 개체를 가리킵니다. 복제 링크 상태는 전역적으로 복제되지 않습니다. 계층 내 모든 기본 사이트 간의 복제 링크 세부 정보를 보려면 콘솔을 중앙 관리 사이트에 연결합니다.  

다음 옵션을 통해 계층 다이어그램을 수정할 수 있습니다.  

#### <a name="groups"></a>Groups

계층 다이어그램 변경을 트리거하는 기본 사이트 및 보조 사이트 수를 구성합니다. 이와 같이 표시가 변경되면 사이트가 단일 개체로 결합됩니다. 그러면 전체 사이트 수와 상태 메시지 및 사이트 상태의 개략적인 롤업을 볼 수 있습니다. 그룹 구성은 지리적 보기에 영향을 주지 않습니다.  

#### <a name="favorite-sites"></a>즐겨찾기 사이트

개별 사이트를 즐겨찾기 사이트로 지정합니다. 별표 아이콘은 계층 다이어그램에서 즐겨찾기 사이트를 나타냅니다. 즐겨찾기 사이트는 그룹을 사용할 때 다른 사이트와 결합되지 않습니다. 항상 개별적으로 표시됩니다.  

### <a name="geographical-view"></a>지리적 보기

지리적 보기는 지리적 맵에 각 사이트의 위치를 표시합니다. 특정 위치를 사용하여 구성하는 사이트만 표시됩니다. 이 보기에서 사이트를 선택하면 부모 또는 자식 사이트에 대한 복제 링크가 표시됩니다. 계층 다이어그램 보기와 달리 이 보기에서는 사이트 상태 메시지 또는 복제 링크 세부 정보를 표시할 수 없습니다.  

> [!NOTE]  
> 지리적 보기를 사용하려면 Configuration Manager 콘솔이 연결하는 컴퓨터에 Internet Explorer가 설치되어 있고 이 컴퓨터에서 HTTP 프로토콜을 사용하여 Bing Maps에 액세스할 수 있어야 합니다.  

다음 옵션을 사용하여 지리적 보기를 수정할 수 있습니다.  

#### <a name="site-location"></a>사이트 위치

다음 유형 중 하나를 사용하여 각 사이트의 지리적 위치를 지정합니다.

- 주소
- 장소 이름(예: 도시 이름)
- 위도 및 경도 좌표

예를 들어 워싱턴주 레드몬드의 위도와 경도를 사용하려면 **N 47 40 26.3572 W 122 7 17.4432** 를 사이트 위치로 지정합니다. 위도나 경도의 도, 분 또는 초 기호는 지정하지 않아도 됩니다. Configuration Manager에서는 Bing 지도를 사용하여 지리적 위치 보기에서 위치를 표시합니다. 그런 다음, 지리적 위치를 사용하여 계층을 볼 수 있습니다. 이 보기에서는 특정 사이트 또는 사이트 간 복제에 영향을 줄 수 있는 지역별 문제를 파악할 수 있습니다.  

위치를 지정할 때에는 **위치** 상자를 사용하여 계층의 특정 사이트를 검색할 수 있습니다. 사이트가 선택된 상태에서 **위치** 열에 위치를 구/군/시 이름 또는 주소로 입력합니다. Configuration Manager에서는 Bing 지도를 사용하여 위치를 확인합니다.  

<a name="BKMK_MonitorRepLinksAndStatuss"></a>

## <a name="next-steps"></a>다음 단계

[데이터베이스 복제 모니터링](/sccm/core/servers/manage/monitor-replication)
