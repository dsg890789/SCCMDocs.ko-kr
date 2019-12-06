---
title: 데이터베이스 복제 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager 계층에서 SQL Server 복제를 모니터링하는 방법을 알아봅니다.
ms.date: 08/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 69550b35-bcdb-4b47-bbec-b3c8bc92bb7b
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8312202b4877ebcd9a30f5dd40858d119a123de
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "68957843"
---
# <a name="monitor-database-replication"></a>데이터베이스 복제 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 콘솔의 **모니터링** 작업 영역에서 **데이터베이스 복제** 노드를 사용하여 데이터베이스 복제의 세부 정보를 모니터링합니다. 사이트 간 복제 링크의 상태를 모니터링할 수 있습니다. 또한 연결된 사이트에 대한 복제 그룹의 초기화 및 복제도 표시합니다.  

> [!TIP]  
> **관리** 작업 영역의 **계층 구성** 노드 아래에도 **데이터베이스 복제** 노드가 나타나지만 이 위치에서는 데이터베이스 복제 링크의 복제 상태를 확인할 수 없습니다.  

## <a name="BKMK_MonitorReplicationLinks"></a> 복제 링크 상태  

사이트 간 데이터베이스 복제 시에는 *복제 그룹*이라는 여러 정보 집합의 복제가 이루어집니다. 각 복제 그룹은 우선 순위가 다른 데이터를 보내고 받습니다. 기본적으로 복제 그룹에 포함되는 데이터와 복제 빈도는 수정할 수 없습니다.  

복제 링크가 활성 상태이고 해당 상태가 실패 또는 저하됨이 아니면 모든 그룹은 빠르게 복제됩니다. 하나 이상의 그룹이 예상 기간 내에 복제를 완료하지 못할 경우 링크가 *저하됨*으로 표시됩니다. 저하된 링크는 여전히 작동할 수 있지만 모니터링을 통해 활성 상태로 복귀되는지 확인해야 합니다. 이러한 링크를 조사하여 추가 저하 또는 복제 실패가 발생하지 않는지 확인합니다.  

각 복제 링크에 대해 복제에 실패한 그룹이 다시 시도하는 횟수를 지정합니다. 이 횟수만큼 다시 시도하면 사이트에서 링크 상태가 저하됨 또는 실패로 설정됩니다. 하나를 제외한 모든 그룹이 성공적으로 복제되더라도 사이트는 링크 상태를 저하됨 또는 실패로 설정합니다. 한 복제 그룹이 지정된 시도 횟수 내에 복제를 완료하지 못하기 때문에 이 상태로 설정됩니다. 자세한 내용은 [데이터베이스 복제 임계값](/sccm/core/plan-design/hierarchy/database-replication#BKMK_DBRepThresholds)을 참조하세요.  

다음 정보를 사용하여 추가 조사가 필요할 수 있는 복제 링크 상태를 파악할 수 있습니다.  

### <a name="link-is-active"></a>링크가 활성화됨

문제가 감지되지 않았으며 링크 전체에 걸친 통신이 최신 상태입니다.

부모 사이트에서 새 버전으로 업그레이드를 진행 중일 때 자식 사이트에서 링크 상태를 보면 링크 상태가 활성화된 것으로 표시됩니다. 업데이트 후에 자식 사이트가 부모 사이트와 동일한 버전이 될 때까지는 부모 사이트에서 볼 때 링크 상태가 활성화된 것으로 표시됩니다. 자식 사이트에서 볼 때 구성 중인 것으로 표시됩니다.  

### <a name="link-is-degraded"></a>링크가 저하됨

복제가 작동하지만 하나 이상의 복제 개체 또는 그룹이 지연되었습니다. 이 상태의 링크를 모니터링합니다. 링크의 두 사이트 모두에서 정보를 검토하여 링크에 오류가 있을 수 있는지 확인합니다.

복제된 데이터를 받는 사이트가 데이터를 데이터베이스에 빠르게 커밋하지 못할 경우에도 링크에 저하됨 상태가 표시될 수 있습니다. 이 동작은 대량의 데이터가 복제되는 경우 발생할 수 있습니다. 예를 들어 소프트웨어 업데이트를 많은 수의 컴퓨터에 배포할 수 있습니다. 링크의 부모 사이트에서 복제된 이 데이터 볼륨을 처리하는 데 약간의 시간이 걸릴 수 있습니다. 부모 사이트에서 처리가 지연되어 데이터 백로그를 성공적으로 처리할 수 있을 때까지 링크 상태가 저하됨으로 설정됩니다.

### <a name="link-has-failed"></a>링크가 실패했음

복제가 작동하지 않습니다. 추가 조치 없이 복제 링크가 복구될 수도 있습니다. 이 링크의 복제 문제를 조사하고 해결하려면 Replication Link Analyzer를 사용합니다.

또한 이 상태는 복제 링크의 부모 사이트와 자식 사이트 간 실제 네트워크에 문제가 있음을 나타낼 수도 있습니다.


## <a name="BKMK_MonitorReplicationStatus"></a> 복제 모니터링 상태

**모니터링** 작업 영역의 **데이터베이스 복제** 노드를 사용하여 복제 링크의 상태를 볼 수 있습니다. 복제 링크의 각 사이트에 있는 데이터베이스에 대한 세부 정보를 확인합니다. 복제 그룹에 대한 세부 정보도 볼 수 있습니다. 이러한 세부 정보를 보려면 복제 링크를 선택한 후에 확인할 복제 상태의 해당 탭을 선택합니다.

다음 섹션에는 복제 상태와 관련한 여러 탭에 대한 자세한 정보가 나와 있습니다.

### <a name="summary"></a>요약

링크의 두 사이트 간 사이트 데이터와 글로벌 데이터의 복제에 대한 개략적인 정보를 확인합니다.  

**관련 기록 트래픽 데이터 보기**를 선택하여 링크에서 복제에 사용되는 네트워크 대역폭에 대한 세부 정보를 표시하는 보고서를 볼 수 있습니다.  

### <a name="parent-site"></a>부모 사이트

복제 링크의 부모 사이트에 대해 다음을 포함한 데이터베이스 세부 정보를 확인합니다.  

- SQL Server에 대한 방화벽 포트  

- 사용 가능한 디스크 공간  

- 데이터베이스 파일 위치  

- 인증서  

### <a name="child-site"></a>자식 사이트

복제 링크의 자식 사이트에 대해 다음을 포함한 데이터베이스 세부 정보를 확인합니다.  

- SQL Server에 대한 방화벽 포트  

- 사용 가능한 디스크 공간  

- 데이터베이스 파일 위치  

- 인증서  

### <a name="initialization-detail"></a>초기화 세부 정보

링크를 통해 복제되는 그룹의 초기화 상태를 확인합니다. 이 정보는 복제 데이터의 초기화가 진행 중이거나 실패한 경우를 파악하는 데 도움이 될 수 있습니다.  

이 정보를 사용하여 사이트가 *상호 운용성 모드*에 있는 경우를 파악합니다. 상호 운용성 모드는 하위 사이트가 상위 사이트와 동일한 버전의 Configuration Manager를 실행하지 않는 경우에 해당합니다.  

### <a name="replication-detail"></a>복제 세부 정보

링크를 통해 복제하는 각 그룹의 복제 상태를 봅니다. 이 정보를 사용하여 특정 데이터 복제와 관련된 문제나 지연을 식별할 수 있습니다. 이러한 정보는 이 링크의 적절한 데이터베이스 복제 임계값을 결정하는 데 유용할 수 있습니다. 자세한 내용은 [데이터베이스 복제 임계값](/sccm/core/plan-design/hierarchy/database-replication#BKMK_DBRepThresholds)을 참조하세요.  

> [!TIP]  
> 사이트 데이터의 복제 그룹은 자식 사이트에서 부모 사이트로만 전송됩니다. 글로벌 데이터의 복제 그룹은 두 방향으로 모두 복제됩니다.  


## <a name="BKMK_RLA"></a> Replication Link Analyzer

Configuration Manager에는 복제 이슈를 분석하고 복구하는 데 사용하는 RLA(**Replication Link Analyzer**)가 포함되어 있습니다. 복제가 실패하는 경우 RLA를 사용하여 링크 오류를 수정합니다. 이 기능은 복제 작동이 중지되었지만 사이트에서 아직 실패했다고 보고하지 않은 경우에도 유용합니다.

RLA를 사용하여 계층의 다음 컴퓨터 간 복제 문제를 수정합니다.  

- 사이트 서버와 사이트 데이터베이스 서버 간  

- 사이트 데이터베이스 서버와 다른 사이트 데이터베이스 서버 간(사이트 간 복제로도 알려져 있음)  

> [!Note]  
> 복제 오류의 방향은 중요하지 않습니다.

다음과 같이 Configuration Manager 콘솔이나 명령 프롬프트에서 RLA를 실행합니다.  

- Configuration Manager 콘솔에서 실행하려면 **모니터링** 작업 영역으로 이동하고, **데이터베이스 복제** 노드를 선택합니다. 분석할 복제 링크를 선택한 다음, 리본에서 **Replication Link Analyzer**를 선택합니다.  

- 명령 프롬프트에서 실행하려면 다음 명령을 입력합니다. `%ProgramFiles(x86)%\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManager.ReplicationLinkAnalyzer.Wizard.exe <source site server FQDN> <destination site server FQDN>`  

RLA를 실행하면 일련의 진단 규칙 및 검사를 사용하여 문제를 검색합니다. 이 도구가 식별하는 문제를 볼 수 있습니다. 문제 해결 지침이 있는 경우 표시됩니다. RLA에서 자동으로 문제를 수정할 수 있는 경우 해당 옵션이 제공됩니다.

RLA가 작업을 마치면 이 도구를 실행한 사용자의 바탕 화면에 있는 다음 XML 기반 보고서와 로그 파일에 결과가 저장됩니다.  

- ReplicationAnalysis.xml  

- ReplicationLinkAnalysis.log  

RLA는 일부 문제를 수정하는 동안 다음 서비스를 중지합니다. 수정이 완료되면 다음 서비스를 다시 시작합니다.  

- SMS_SITE_COMPONENT_MANAGER  

- SMS_EXECUTIVE  

RLA가 수정을 완료하지 못하는 경우 필요하면 사이트 서버에서 이러한 서비스를 다시 시작합니다.  

RLA는 모든 조사 및 수정 작업을 기록하여 마법사에 표시되지 않는 추가 세부 정보를 제공합니다.  

### <a name="rla-prerequisites"></a>RLA 전제 조건

RLA를 실행하는 데 사용하는 계정은 다음 사용 권한을 보유해야 합니다.

- 복제 링크와 관련된 각 컴퓨터에 대한 로컬 관리자 권한

- 복제 링크와 관련된 각 SQL Server 데이터베이스에 대한 Sysadmin 권한  

> [!Note]  
> 이 계정에 특정 Configuration Manager 역할 기반 관리 보안 역할은 필요하지 않습니다. **데이터베이스복제** 노드에 액세스할 수 있는 관리자는 Configuration Manager 콘솔에서 이 도구를 실행할 수 있습니다. 각 컴퓨터에 대한 충분한 권한이 있는 시스템 관리자는 명령 프롬프트에서 이 도구를 실행할 수 있습니다.  

### <a name="rla-known-issue"></a>RLA의 알려진 이슈

RLA는 System Center 2012 Configuration Manager에서 업그레이드된 기본 사이트에 대해 SQL SSB(Server Service Broker) 인증서 오류를 생성합니다. 이 문제는 Configuration Manager 현재 분기의 인증서 이름이 변경되었기 때문에 발생합니다. 이러한 오류는 무시해도 됩니다.  


## <a name="BKMK_ProcsforMonitoringReplication"></a> 데이터베이스 복제 모니터링  

### <a name="monitor-high-level-site-to-site-database-replication-status"></a>상위 사이트 간 데이터베이스 복제 상태 모니터링

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다.  

2. **사이트 계층** 노드를 선택하여 **계층 다이어그램** 보기를 엽니다.  

3. 두 사이트 사이의 줄에 마우스 포인터를 올려 놓습니다. 이러한 사이트의 글로벌 및 사이트 데이터 복제 상태를 확인합니다.  

### <a name="monitor-the-status-of-a-replication-link"></a>복제 링크의 상태 모니터링

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다.  

2. **데이터베이스복제** 노드를 선택하고 모니터링하려는 복제 링크를 선택합니다. 그런 다음, 적절한 탭을 선택하여 해당 링크의 복제 상태에 대한 여러 가지 서로 다른 정보를 봅니다.  
