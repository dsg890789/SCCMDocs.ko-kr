---
title: 복제 모니터링
titleSuffix: Configuration Manager
description: 콘솔의 모니터링 작업 영역을 사용하여 Configuration Manager에서 인프라 및 작업을 모니터링하는 방법을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3fab4d67-8d2a-45ce-8b06-471280102cf6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7a9fcf06630c76fc3e1123fa56861c4de224521
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56129377"
---
# <a name="monitor-hierarchy-and-replication-infrastructure-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 계층 및 복제 인프라 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 인프라 및 작업을 모니터링하려면 Configuration Manager 콘솔의 **모니터링** 작업 영역을 사용합니다.  

> [!NOTE]  
>  마이그레이션의 경우 이 위치가 아니라 **관리** 작업 영역의 **마이그레이션** 노드에서 직접 모니터링됩니다. 자세한 내용은 [System Center Configuration Manager로 마이그레이션을 위한 작업](../../../core/migration/operations-for-migration.md)을 참조하세요.  

 Configuration Manager 콘솔을 모니터링에 사용하는 것 외에도 Configuration Manager 보고서를 사용하거나 Configuration Manager 구성 요소에 대한 Configuration Manager 로그 파일을 볼 수 있습니다. 보고서에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../../core/servers/manage/reporting.md)를 참조하세요. 로그 파일에 대한 자세한 내용은 [System Center Configuration Manager의 로그 파일](../../../core/plan-design/hierarchy/log-files.md)을 참조하세요.  

 사이트를 모니터링할 때에는 조치가 필요한 문제를 나타내는 징후를 확인합니다. 예:  

-   사이트 서버 또는 사이트 시스템에 있는 파일 백로그  

-   오류 또는 문제를 나타내는 상태 메시지  

-   사이트 간 통신 실패  

-   서버의 시스템 이벤트 로그에 있는 오류 및 경고 메시지  

-   Microsoft SQL Server 오류 로그에 있는 오류 및 경고 메시지  

-   오랫동안 보고되지 않은 사이트 또는 클라이언트  

-   SQL Server 데이터베이스에서 응답이 느림  

-   하드웨어 오류 증상  

사이트 오류 위험을 최소화하려면 모니터링 작업을 통해 문제 징후가 발견될 때 문제의 원인을 조사하여 최대한 빨리 해결해야 합니다.  



##  <a name="BKMK_MonintorMgmtTasks"></a> Configuration Manager의 일반 관리 작업 모니터링  
 Configuration Manager는 Configuration Manager 콘솔 내에서 기본 제공 모니터링을 제공합니다. 소프트웨어 업데이트, 전원 관리 및 계층 전체에 콘텐츠 배포와 관련된 작업을 포함한 여러 작업을 모니터링할 수 있습니다.  

 일반적인 Configuration Manager 작업을 모니터링하려면 다음 정보를 참조하세요.  

 **경고**  
   [System Center Configuration Manager에 대한 경고 및 상태 시스템 사용](../../../core/servers/manage/use-alerts-and-the-status-system.md)에서 [경고 모니터링](../../../core/servers/manage/use-alerts-and-the-status-system.md#BKMK_MonitorAlerts)을 참조하세요.  

 **호환성 설정**  
   [System Center Configuration Manager에서 준수 설정을 모니터링하는 방법](../../../compliance/deploy-use/monitor-compliance-settings.md)을 참조하세요.  

 **콘텐츠 배포**  
   콘텐츠를 모니터링하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

특정 유형의 콘텐츠 배포를 모니터링하는 방법에 대한 정보:
-   애플리케이션을 모니터링하려면 [System Center Configuration Manager에서 애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)을 참조하세요.  

-   패키지 및 프로그램을 모니터링하려면 [System Center Configuration Manager의 패키지 및 프로그램](../../../apps/deploy-use/packages-and-programs.md)에서 패키지와 프로그램을 관리하는 방법을 참조하세요.  

**Endpoint Protection**  
   [System Center Configuration Manager에서 Endpoint Protection을 모니터링하는 방법](../../../protect/deploy-use/monitor-endpoint-protection.md)을 참조하세요.  

**전원 관리 모니터링**  
 [System Center Configuration Manager에서 전원 관리를 모니터링하고 계획하는 방법](../../../core/clients/manage/power/monitor-and-plan-for-power-management.md)을 참조하세요.  

**소프트웨어 계량 모니터링**  
[System Center Configuration Manager의 소프트웨어 계량을 사용하여 앱 사용 모니터링](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.  

**소프트웨어 업데이트 모니터링**  
 [System Center Configuration Manager에서 소프트웨어 업데이트 모니터링](../../../sum/deploy-use/monitor-software-updates.md)을 참조하세요.  


##  <a name="BKMK_MonitorInfrastructure"></a> Configuration Manager의 계층 인프라 모니터링  
Configuration Manager에서는 여러 가지 방법으로 계층 구조의 상태와 작업을 모니터링할 수 있습니다. 계층 전체에 있는 사이트의 시스템 상태를 확인하고, 사이트 계층 또는 지리적 위치 보기에서 사이트 간 복제를 모니터링하고, 데이터베이스 복제를 위한 사이트 간 복제 링크를 모니터링하고, Replication Link Analyzer 툴을 사용하여 복제 문제를 해결할 수 있습니다.  

###  <a name="BKMK_SH_Node"></a> 사이트 계층 노드 정보  
**모니터링** 작업 영역의 **사이트 계층** 노드에서는 Configuration Manager 계층 구조 및 사이트 간 링크의 개요를 제공합니다. 두 가지 보기를 사용할 수 있습니다.  

-   **계층 다이어그램**: 이 보기는 중요한 정보만 표시하는 단순화된 토폴로지 맵으로 계층을 표시합니다.  

-   **지리적 보기**: 이 보기는 구성된 사이트 위치를 보여 주는 지리적 맵에 사이트를 표시합니다.  

각 사이트의 상태와 사이트 간 복제 링크 및 외부 요소와의 관계(예: 지리적 위치)를 모니터링하려면 **사이트 계층** 노드를 사용합니다.  

사이트 상태 및 사이트 간 링크는 글로벌 데이터가 아닌 사이트 데이터로 복제되므로 Configuration Manager 콘솔을 하위 기본 사이트에 연결할 때 다른 기본 사이트 또는 하위 보조 사이트의 사이트 또는 링크 상태를 볼 수 없습니다. 예를 들어 다중 기본 사이트 계층 구조에서 Configuration Manager 콘솔이 기본 사이트에 연결되는 경우 하위 기본 사이트, 기본 사이트 및 중앙 관리 사이트의 상태를 볼 수 있지만 중앙 관리 사이트 아래 계층 구조에 있는 다른 노드의 상태는 볼 수 없습니다.  

 사이트 계층 표시가 렌더링되는 방식을 제어하려면 **설정 구성** 명령을 사용합니다. Configuration Manager 콘솔이 한 사이트에 연결되어 있을 때 지정한 **사이트 계층** 노드에 대한 구성은 다른 모든 사이트에 복제됩니다.  

#### <a name="hierarchy-diagram"></a>계층 다이어그램  
 계층 다이어그램에는 토폴로지 맵의 사이트가 표시됩니다. 이 보기에서는 사이트를 선택하고, 해당 사이트의 상태 메시지 요약을 보고, 상태 메시지를 자세히 확인하고, 사이트의 **속성** 대화 상자에 액세스할 수 있습니다.  

 또한 사이트 또는 사이트 간 복제 링크에 마우스 포인터를 놓고 해당 개체의 개략적인 상태를 확인할 수 있습니다. 복제 링크 상태는 전역적으로 복제되지 않기 때문에 기본 사이트가 여러 개 있는 계층 구조에서는 모든 사이트 간의 복제 링크 세부 정보를 보기 위해 Configuration Manager 콘솔을 중앙 관리 사이트에 연결해야 합니다.  

 다음 옵션을 통해 계층 다이어그램을 수정할 수 있습니다.  

-   **그룹**: 여러 사이트를 단일 개체로 결합하도록 계층 다이어그램 표시를 변경하기 위해 기본 사이트와 보조 사이트 수를 구성할 수 있습니다. 사이트가 단일 개체로 결합되면 전체 사이트 수와 상태 메시지 및 사이트 상태의 개략적인 롤업을 볼 수 있습니다. 그룹 구성은 지리적 보기에 영향을 주지 않습니다.  

-   **즐겨찾기 사이트**: 개별 사이트를 즐겨찾기 사이트로 지정할 수 있습니다. 별표 아이콘은 계층 다이어그램에서 즐겨찾기 사이트를 나타냅니다. 즐겨찾기 사이트는 그룹을 사용할 때 다른 사이트와 결합되지 않으며 항상 개별적으로 표시됩니다.  

#### <a name="geographical-view"></a>지리적 보기  
 지리적 보기는 지리적 맵에 각 사이트의 위치를 표시합니다. 특정 위치를 사용하여 구성하는 사이트만 표시됩니다. 이 보기에서 사이트를 선택하면 부모 또는 자식 사이트에 대한 복제 링크가 표시됩니다. 계층 다이어그램 보기와 달리 이 보기에서는 사이트 상태 메시지 또는 복제 링크 세부 정보를 표시할 수 없습니다.  

> [!NOTE]  
>  지리적 보기를 사용하려면 Configuration Manager 콘솔이 연결하는 컴퓨터에 Internet Explorer가 설치되어 있고 이 컴퓨터에서 HTTP 프로토콜을 사용하여 Bing Maps에 액세스할 수 있어야 합니다.  

다음 옵션을 사용하여 지리적 보기를 수정할 수 있습니다.  

-   **사이트 위치**: 각 사이트의 지리적 위치를 지정할 수 있습니다. 주소, 도시 이름과 같은 지역 이름 또는 위도와 경도 좌표로 위치를 지정할 수 있습니다. 예를 들어 워싱턴주 레드몬드의 위도와 경도를 사용하려면 **N 47 40 26.3572 W 122 7 17.4432** 를 사이트 위치로 지정합니다. 위도나 경도의 도, 분 또는 초 기호는 지정하지 않아도 됩니다. Configuration Manager에서는 Bing 지도를 사용하여 지리적 위치 보기에서 위치를 표시합니다. 이를 통해 지리적 위치와 관련하여 계층을 확인함으로써 특정 사이트 또는 사이트 간 복제에 영향을 미칠 수 있는 지역별 문제를 파악할 수 있습니다.  

     위치를 지정할 때에는 **위치** 상자를 사용하여 계층의 특정 사이트를 검색할 수 있습니다. 사이트가 선택된 상태에서 **위치** 열에 위치를 구/군/시 이름 또는 주소로 입력합니다. Configuration Manager에서는 Bing 지도를 사용하여 위치를 확인합니다.  

###  <a name="BKMK_MonitorRepLinksAndStatuss"></a> 데이터베이스 복제 링크 및 복제 상태를 모니터링하는 방법  
 **모니터링** 작업 영역의 **사이트 계층** 노드에서 액세스할 수 있는 높은 수준의 세부 정보 외에 **모니터링** 작업 영역에서 **데이터베이스 복제** 를 사용하는 경우 데이터베이스 복제에 대한 세부 정보도 모니터링할 수 있습니다. **데이터베이스 복제**에서 사이트 간 복제 링크의 상태와 Configuration Manager 콘솔이 연결되는 사이트에 있는 복제 그룹의 초기화 정보 및 복제 정보를 모니터링할 수 있습니다.  

> [!TIP]  
>  **관리** 작업 영역의 **계층 구성** 노드 아래에도 **데이터베이스 복제** 노드가 나타나지만 이 위치에서는 데이터베이스 복제 링크의 복제 상태를 확인할 수 없습니다.  

####  <a name="BKMK_MonitorReplicationLinks"></a> 복제 링크 상태  
사이트 간 데이터베이스 복제 시에는 복제 그룹이라는 여러 정보 집합의 복제가 이루어집니다. 각 복제 그룹은 서로 다른 복제 우선 순위를 가지고 복제됩니다. 기본적으로 복제 그룹에 포함되는 데이터와 복제 빈도는 수정할 수 없습니다.  

 복제 링크가 활성화되어 있고 실패 또는 저하됨 상태를 갖지 않는 경우 모든 복제 그룹이 적시에 복제됩니다. 하나 이상의 복제 그룹이 예상 기간 내에 복제를 완료하지 못할 경우 링크가 저하됨으로 표시됩니다. 저하된 링크는 여전히 작동할 수 있지만 모니터링을 통해 활성 상태로 복귀되는 것을 확인하거나, 조사를 통해 추가 저하 또는 복제 실패가 발생하지 않도록 해야 합니다.  

 각 복제 링크의 경우 링크 상태가 저하됨 또는 실패로 설정되기 전에 복제에 실패한 복제 그룹이 복제를 다시 시도하는 횟수를 지정할 수 있습니다. 하나를 제외한 모든 복제 그룹이 성공적으로 복제되더라도 이 하나의 복제 그룹이 지정된 횟수 내에 복제를 완료하지 못하면 링크 상태가 저하됨 또는 실패로 설정됩니다. 복제 임계값에 대한 자세한 내용은 [System Center Configuration Manager의 사이트 간 데이터 전송](../../../core/servers/manage/data-transfers-between-sites.md)에서 [데이터베이스 복제 임계값](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) 섹션을 참조하세요.  

 다음 표에서는 추가 조사가 필요할 수 있는 복제 링크 상태를 파악하는 데 도움이 되는 정보를 제공합니다.  

|링크 설명|추가 정보|  
|----------------------|----------------------|  
|**링크가 활성화됨**|문제가 감지되지 않았으며 링크 전체에 걸친 통신이 최신 상태입니다.|  
|**링크가 저하됨**|복제가 작동하지만 하나 이상의 복제 개체 또는 그룹이 지연되었습니다. 이 상태의 링크를 모니터링하고 링크의 두 사이트 모두에서 정보를 검토하여 링크에 오류가 있을 수 있는지 확인합니다.<br /><br /> 복제된 데이터를 받는 사이트가 데이터를 데이터베이스에 빠르게 커밋하지 못할 경우에도 링크에 저하됨 상태가 표시될 수 있습니다. 이는 대량의 데이터가 복제되는 경우 발생할 수 있습니다. 예를 들어 소프트웨어 업데이트를 다수의 컴퓨터에 배포하는 경우 링크의 부모 사이트에서 복제되는 데이터 양이 처리되는 데 약간의 시간이 걸릴 수 있습니다. 부모 사이트에서의 처리 지연으로 인해 부모 사이트에서 데이터 백로그를 성공적으로 처리할 수 있을 때까지 링크 상태가 저하됨으로 설정될 수 있습니다.|  
|**링크가 실패했음**|복제가 작동하지 않습니다. 추가 조치 없이 복제 링크가 복구될 수도 있습니다. Replication Link Analyzer를 사용하여 이 링크의 복제 문제를 조사하고 해결할 수 있습니다.<br /><br /> 또한 이 상태는 복제 링크의 부모 사이트와 자식 사이트 간 실제 네트워크에 문제가 있음을 나타낼 수도 있습니다.|  

 부모 사이트에서 새 서비스 팩으로의 업그레이드를 진행 중일 때 자식 사이트에서 링크 상태를 보면 링크 상태가 활성화된 것으로 표시됩니다. 업그레이드 후에 자식 사이트가 부모 사이트와 동일한 서비스 팩을 사용할 때까지는 부모 사이트에서 볼 때 링크 상태가 활성화된 것으로 표시되고, 자식 사이트에서 볼 때는 링크 상태가 구성 중인 것으로 표시됩니다.  

####  <a name="BKMK_MonitorReplicationStatus"></a> 복제 상태  
 **모니터링** 작업 영역의 **데이터베이스 복제** 노드를 사용하여 복제 링크의 복제 상태를 확인하고 복제 링크의 각 사이트에 있는 사이트 데이터베이스에 대한 세부 정보를 볼 수 있습니다. 복제 그룹에 대한 세부 정보도 볼 수 있습니다. 세부 정보를 보려면 복제 링크를 선택한 후에 확인할 복제 상태의 해당 탭을 선택합니다. 다음에는 복제 상태와 관련한 여러 탭에 대한 자세한 정보가 나와 있습니다.  

 **요약**  
 링크의 두 사이트 간 사이트 데이터와 글로벌 데이터의 복제에 대한 개략적인 정보를 확인합니다.  

 또한 **관련 기록 트래픽 데이터 보기** 를 클릭하여 복제 링크에서 복제에 사용되는 네트워크 대역폭에 대한 세부 정보를 표시하는 보고서를 볼 수 있습니다.  

 **부모 사이트**  
 복제 링크의 부모 사이트에 대해 다음을 포함한 데이터베이스 세부 정보를 확인합니다.  

-   SQL Server에 대한 방화벽 포트  

-   사용 가능한 디스크 공간  

-   데이터베이스 파일 위치  

-   인증서  

**자식 사이트**  
 복제 링크의 자식 사이트에 대해 다음을 포함한 데이터베이스 세부 정보를 확인합니다.  

-   SQL Server에 대한 방화벽 포트  

-   사용 가능한 디스크 공간  

-   데이터베이스 파일 위치  

-   인증서  

**초기화 세부 정보**    
 복제 링크를 통해 복제되는 복제 그룹의 초기화 상태를 확인합니다. 이 정보는 복제 데이터의 초기화가 진행 중이거나 실패한 경우를 파악하는 데 도움이 될 수 있습니다.  

 또한 이 정보를 사용하여 사이트가 상호 운용성 모드에 있는 경우를 파악할 수 있습니다. 상호 운용성 모드는 하위 사이트가 상위 사이트와 동일한 버전의 Configuration Manager를 실행하지 않는 경우에 발생합니다.  

**복제 세부 정보**    
 링크를 통해 복제하는 각 복제 그룹의 복제 상태를 봅니다. 이 정보를 사용하면 특정 데이터의 복제에 대한 문제나 지연을 식별하고, 이 링크의 적절한 데이터베이스 복제 임계값을 결정할 수 있습니다. 데이터베이스 복제 임계값에 대한 자세한 내용은 [System Center Configuration Manager의 사이트 간 데이터 전송](../../../core/servers/manage/data-transfers-between-sites.md)에서 [데이터베이스 복제 임계값](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) 섹션을 참조하세요.  

> [!TIP]  
>  사이트 데이터의 복제 그룹은 자식 사이트에서 부모 사이트로만 전송됩니다. 글로벌 데이터의 복제 그룹은 두 방향으로 모두 복제됩니다.  

###  <a name="BKMK_RLA"></a> Replication Link Analyzer 정보  
 Configuration Manager에는 복제 문제를 분석하고 복구하는 데 사용하는 **Replication Link Analyzer**가 포함되어 있습니다. Replication Link Analyzer를 사용하면 복제가 실패했을 때와 복제가 중지되었지만 아직 실패된 것으로 보고되지는 않았을 때 복제 링크 오류를 재구성할 수 있습니다. Replication Link Analyzer는 Configuration Manager 계층 구조의 다음 컴퓨터 간의 복제 문제를 해결하는 데 사용할 수 있습니다(복제 오류의 방향은 중요하지 않음).  

-   사이트 서버와 사이트 데이터베이스 서버 간  

-   사이트 데이터베이스 서버와 다른 사이트 데이터베이스 컴퓨터 간(사이트 간 복제)  

Configuration Manager 콘솔이나 명령 프롬프트에서 Replication Link Analyzer를 실행할 수 있습니다.  

-   Configuration Manager 콘솔에서 실행하려면 **모니터링** 작업 영역에서 **데이터베이스 복제** 노드를 클릭하고 분석할 복제 링크를 선택한 다음, **홈** 탭의 **데이터베이스 복제** 그룹에서 **Replication Link Analyzer**를 선택합니다.  

-   명령 프롬프트를 실행하려면 **%path%\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManager.ReplicationLinkAnalyzer.Wizard.exe &lt;원본 사이트 서버 FQDN\> &lt;대상 사이트 서버 FQDN\>** 명령을 입력합니다.  

Replication Link Analyzer를 실행하면 Replication Link Analyzer에서 일련의 진단 규칙 및 검사를 사용하여 문제를 검색합니다. 이 도구를 실행하면 이 도구가 식별하는 문제를 볼 수 있습니다. 문제 해결을 위한 지침이 알려져 있으면 표시됩니다. Replication Link Analyzer에서 자동으로 문제를 재구성할 수 있으면 해당 옵션이 표시됩니다. Replication Link Analyzer가 작업을 마치면 이 도구를 실행한 사용자의 바탕 화면에 있는 다음 XML 기반 보고서와 로그 파일에 결과가 저장됩니다.  

-   ReplicationAnalysis.xml  

-   ReplicationLinkAnalysis.log  

Replication Link Analyzer를 실행하면 몇 가지 문제를 재구성하는 동안 다음 서비스가 중지되었다가 재구성이 완료되면 이러한 서비스가 다시 시작됩니다.  

-   SMS_SITE_COMPONENT_MANAGER  

-   SMS_EXECUTIVE  

Replication Link Analyzer가 재구성을 완료하지 못하면 사이트 서버를 검토하고 이러한 서비스가 중지된 경우 해당 서비스를 다시 시작합니다.  

성공하거나 성공하지 못한 조사 및 재구성 작업이 로깅되어 도구 인터페이스에 표시되지 않은 추가 세부 정보를 제공합니다.  

**Replication Link Analyzer 사용을 위한 필수 조건**  

-   Replication Link Analyzer를 실행하는 데 사용할 계정에 복제 링크와 관련된 각 컴퓨터에 대한 로컬 관리자 권한이 있어야 합니다. 이 계정에 특정 역할 기반 관리 보안 역할은 필요하지 않습니다. 그러므로 **데이터베이스 복제** 노드에 액세스할 수 있는 관리자는 Configuration Manager 콘솔에서 이 도구를 실행할 수 있고, 각 컴퓨터에 대해 충분한 권한이 있는 시스템 관리자는 명령 프롬프트에서 이 도구를 실행할 수 있습니다.  

-   Replication Link Analyzer를 실행하는 데 사용할 계정에 복제 링크와 관련된 각 SQL Server 데이터베이스에 대한 sysadmin 권한이 있어야 합니다.  

**Replication Link Analyzer에 대한 알려진 문제:**  

-   System Center Configuration Manager 버전 1511 릴리스에서 Replication Link Analyzer가 System Center 2012 Configuration Manager에서 업그레이드된 기본 사이트에 대해 SQL Server Service Broker 인증서 오류를 생성합니다. 이는 Replication Link Analyzer가 아직 업데이트되지 않은 1511 버전으로 지정한 인증서의 이름이 변경되었기 때문입니다. 이러한 오류는 무시해도 됩니다.  

###  <a name="BKMK_ProcsforMonitoringReplication"></a> 데이터베이스 복제 모니터링 절차  

##### <a name="to-monitor-high-level-site-to-site-database-replication-status"></a>상위 사이트 간 데이터베이스 복제 상태를 모니터링하려면    
1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **사이트 계층** 을 클릭하여 **계층 다이어그램** 보기를 엽니다.  

3.  두 사이트 사이의 줄에 마우스 포인터를 잠시 멈춰 이러한 사이트의 글로벌 데이터 복제 및 사이트 데이터 복제 상태를 봅니다.  

##### <a name="to-monitor-the-replication-status-for-a-replication-link"></a>복제 링크의 복제 상태를 모니터링하려면    
1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **데이터베이스 복제**를 클릭한 다음 모니터링할 링크의 복제 링크를 선택합니다. 그런 다음 작업 영역에서 적절한 탭을 선택하여 해당 링크의 복제 상태에 대한 여러 가지 서로 다른 정보를 봅니다.  
