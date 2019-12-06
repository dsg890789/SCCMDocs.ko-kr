---
title: 유지 관리 작업에 대한 참조
titleSuffix: Configuration Manager
description: 각 Configuration Manager 사이트 유지 관리 작업의 세부 정보
ms.date: 09/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e32e96063f6c65a77e398c8434ce6b833c7be890
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70379721"
---
# <a name="reference-for-maintenance-tasks-in-configuration-manager"></a>Configuration Manager의 유지 관리 작업 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 각 Configuration Manager 사이트 유지 관리 작업의 세부 정보를 나열합니다. 각 항목은 작업을 사용할 수 있는 사이트 유형과 기본적으로 사용되는지 여부를 지정합니다.

자세한 내용은 [유지 관리 작업 설정](/sccm/core/servers/manage/maintenance-tasks#set-up-maintenance-tasks)을 참조하세요.  

## <a name="tasks"></a>작업

### <a name="backup-site-server"></a>백업 사이트 서버

이 작업으로 중요한 정보의 백업을 만들어 사이트와 Configuration Manager 데이터베이스를 복원할 수 있습니다. 자세한 내용은 [Configuration Manager 사이트 백업](/sccm/core/servers/manage/backup-and-recovery)을 참조하세요.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용 안 함|
|보조 사이트|사용할 수 없음|

### <a name="check-application-title-with-inventory-information"></a>인벤토리 정보를 사용하여 응용 프로그램 타이틀 확인

이 작업을 사용하면 소프트웨어 인벤토리 및 Asset Intelligence 카탈로그에 있는 소프트웨어 타이틀 간의 일관성을 유지할 수 있습니다. 자세한 내용은 [Asset Intelligence 소개](/sccm/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence)를 참조하세요.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|기본 사이트|사용할 수 없음|
|보조 사이트|사용할 수 없음|

### <a name="clear-undiscovered-clients"></a>검색되지 않은 클라이언트 지우기

> [!Tip]
> 콘솔에서 **설치 플래그 지우기**라는 이 작업을 확인할 수도 있습니다.

이 작업을 사용하면 **클라이언트 다시 검색** 기간 중 하트비트 검색 레코드를 제출하지 않은 클라이언트에 대해 설치 플래그를 제거할 수 있습니다. 설치 플래그는 활성 Configuration Manager 클라이언트를 포함할 수 있는 컴퓨터에 대해 자동 클라이언트 강제 설치가 실행되지 않도록 방지합니다.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용 안 함|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-application-request-data"></a>오래된 애플리케이션 요청 데이터 삭제

이 작업을 사용하면 데이터베이스에서 오래된 애플리케이션 요청을 삭제할 수 있습니다. 자세한 내용은 [애플리케이션 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)를 참조하세요.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-application-revisions"></a>오래된 애플리케이션 수정 버전 삭제

이 작업을 사용하면 더 이상 참조되지 않는 애플리케이션 수정 버전을 삭제할 수 있습니다. 자세한 내용은 [애플리케이션을 수정하고 교체하는 방법](/sccm/apps/deploy-use/revise-and-supersede-applications)을 참조하세요.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-client-download-history"></a>오래된 클라이언트 다운로드 기록 삭제

이 작업을 사용하여 클라이언트에서 사용한 다운로드 원본에 대한 기록 데이터를 삭제합니다. 이 사이트는 다운로드 원본 정보를 사용하여 [클라이언트 데이터 원본 대시보드](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)를 채웁니다.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-client-operations"></a>오래된 클라이언트 작업 삭제

이 작업을 사용하면 클라이언트 작업의 오래된 데이터를 사이트 데이터베이스에서 모두 삭제할 수 있습니다. 예를 들어 이 데이터에는 다음 작업이 포함됩니다.

- 컴퓨터 또는 사용자 정책에 대한 다운로드 요청 등 오래되었거나 만료된 클라이언트 알림
- 관리자가 검사를 실행하거나 업데이트된 정의를 다운로드하기 위해 클라이언트에 대해 만든 요청 등의 Endpoint Protection

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-client-presence-history"></a>오래된 클라이언트 상태 기록 삭제
<!-- not listed in dogfood for either primary or CAS, was it renamed? -->
이 작업을 사용하면 클라이언트 알림에서 기록한 클라이언트의 온라인 상태에 대한 기록 정보를 삭제할 수 있습니다. 지정된 시간보다 오래된 상태의 클라이언트에 대한 정보를 삭제합니다. 자세한 내용은 [클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)을 참조하세요.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-cloud-management-gateway-traffic-data"></a>오래된 클라우드 관리 게이트웨이 트래픽 데이터 삭제

이 작업을 사용하여 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 통과하는 트래픽에 대한 오래된 데이터를 사이트 데이터베이스에서 모두 삭제합니다. 이러한 데이터는 다음과 같습니다.

- 요청 수
- 전체 요청 바이트
- 전체 응답 바이트
- 실패한 요청 수
- 최대 동시 요청 수

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-cmpivot-results"></a>오래된 CMPivot 결과 삭제

이 작업을 사용하면 CMPivot 쿼리에서 클라이언트의 오래된 정보를 사이트 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [실시간 데이터용 CMPivot](/sccm/core/servers/manage/cmpivot)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-collected-files"></a>오래된 수집 파일 삭제

이 작업을 사용하면 데이터베이스에서 수집한 파일과 관련된 오래된 정보를 삭제할 수 있습니다. 또한 이 작업은 선택한 사이트의 사이트 서버 폴더 구조에서 수집 파일을 삭제합니다. 기본적으로 수집된 파일의 복사본이 최신순으로 5개까지 사이트 서버의 **Inboxes\sinv.box\FileCol** 디렉터리에 저장됩니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-computer-association-data"></a>오래된 컴퓨터 연결 데이터 삭제

이 작업을 사용하면 데이터베이스에서 오래된 OS 배포 컴퓨터 연결 데이터를 삭제할 수 있습니다. 이 정보는 작업 순서 중에 사용자 상태를 복원할 때 사용됩니다. 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-console-connection-data"></a>오래된 콘솔 연결 데이터 삭제

이 작업은 사이트 데이터베이스에서 사이트에 대한 콘솔 연결 관련 데이터를 삭제합니다.<!-- SCCMDocs#528 -->

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-delete-detection-data"></a>오래된 삭제 검색 데이터 삭제

이 작업을 사용하면 데이터베이스에서 Extraction View로 만들어진 오래된 데이터를 삭제할 수 있습니다. 데이터베이스에서 데이터를 추출하는 외부 시스템이 사용하는 오래된 데이터 변경 정보를 삭제합니다.<!--SCCMDocs#1590--><!--By default, Extraction Views are disabled. You only enable them by using the Configuration Manager SDK. Unless Extraction Views are enabled, there is no data for this task to delete.-->

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-device-wipe-record"></a>오래된 디바이스 초기화 레코드 삭제

이 작업을 사용하면 데이터베이스에서 모바일 디바이스 초기화 작업에 대한 오래된 데이터를 삭제할 수 있습니다. 자세한 내용은 [원격 초기화, 잠금 또는 암호 재설정으로 데이터 보호](/sccm/mdm/deploy-use/wipe-lock-reset-devices)를 참조하세요.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-discovery-data"></a>오래된 검색 데이터 삭제

이 작업을 사용하면 데이터베이스에서 오래된 검색 데이터를 삭제할 수 있습니다. 이 데이터는 다음의 레코드를 포함할 수 있습니다.

- 하트비트 검색
- 네트워크 검색
- Active Directory 검색 방법: 시스템, 사용자 및 그룹

이 작업은 또한 서비스가 해제된 것으로 표시된 오래된 디바이스를 제거합니다. 사이트에서 이 작업을 실행하면 해당 사이트와 연결된 데이터는 삭제되고 관련 변경 내용은 다른 사이트에 복제됩니다. 자세한 내용은 [검색 실행](/sccm/core/servers/deploy/configure/run-discovery)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-distribution-point-usage-stats"></a>오래된 배포 지점 사용량 통계 삭제

이 작업을 사용하여 지정된 시간보다 오래 저장된 배포 지점 데이터를 데이터베이스에서 삭제할 수 있습니다.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-enrolled-devices"></a>오래된 등록 디바이스 삭제

이 작업을 사용하면 지정된 시간 동안 사이트에 아무 정보도 보고하지 않은 모바일 디바이스의 오래된 데이터를 사이트 데이터베이스에서 삭제할 수 있습니다.

이 작업은 Configuration Manager [온-프레미스 MDM](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)에 등록된 디바이스에 적용됩니다. 이 디바이스에 대한 자세한 내용은 [클라이언트 및 디바이스 지원 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS)를 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용 안 함|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-ep-health-status-history-data"></a>오래된 EP 상태 기록 데이터 삭제

이 작업을 사용하면 데이터베이스에서 Endpoint Protection(EP)에 대한 오래된 상태 정보를 삭제할 수 있습니다. 자세한 내용은 [Endpoint Protection 모니터링 방법](/sccm/protect/deploy-use/monitor-endpoint-protection)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-exchange-partnership"></a>오래된 Exchange 파트너 삭제

> [!Tip]
> > 콘솔에서 Exchange Server 커넥터가 관리하는 **오래된 관리 디바이스 삭제** 작업을 확인할 수도 있습니다.

이 작업을 사용하면 Exchange Server 커넥터를 사용하여 관리되는 모바일 디바이스에 대한 오래된 데이터를 삭제할 수 있습니다. 해당 사이트는 Exchange Server 커넥터 속성의 **검색** 탭에 있는 **다음 기간(일)을 초과해 비활성 상태인 모바일 디바이스 무시** 설정에 따라 이 데이터를 삭제합니다. 자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-inventory-history"></a>오래된 인벤토리 기록 삭제

이 작업을 사용하면 데이터베이스에서 지정된 시간보다 오래 저장된 인벤토리 데이터를 삭제할 수 있습니다. 자세한 내용은 [하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-log-data"></a>오래된 로그 데이터 삭제

이 작업을 사용하면 데이터베이스에서 문제 해결에 사용된 오래된 로그 데이터를 삭제할 수 있습니다. 이 데이터는 Configuration Manager 구성 요소 작업과 관련이 없습니다.  

> [!IMPORTANT]  
> 기본적으로 이 작업은 각 사이트에서 매일 실행됩니다. 이 작업은 중앙 관리 사이트 및 기본 사이트에서 30일이 경과한 데이터를 삭제합니다. 보조 사이트에서 SQL Server Express를 사용할 경우 이 작업은 매일 실행되어야 하고 7일 동안 비활성 상태인 데이터를 삭제해야 합니다.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|**보조 사이트**|사용|

### <a name="delete-aged-metering-data"></a>오래된 미터링 데이터 삭제

이 작업을 사용하면 데이터베이스에서 지정된 시간보다 오래 저장된 오래된 소프트웨어 계량 관련 데이터를 삭제할 수 있습니다. 자세한 내용은 [소프트웨어 계량](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-metering-summary-data"></a>오래된 계량 요약 데이터 삭제

이 작업을 사용하면 데이터베이스에서 지정된 시간보다 오래 저장된 오래된 소프트웨어 계량 요약 데이터를 삭제할 수 있습니다. 자세한 내용은 [소프트웨어 계량](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-notification-server-history"></a>오래된 알림 서버 기록 삭제

이 작업은 오래된 클라이언트 상태 기록을 삭제합니다.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-notification-task-history"></a>오래된 알림 작업 기록 삭제

이 작업을 사용하면 사이트 데이터베이스에서 클라이언트 알림 작업에 대한 정보를 삭제할 수 있습니다. 이 작업은 지정된 시간 동안 업데이트되지 않은 데이터에 적용됩니다. 자세한 내용은 [클라이언트 알림](/sccm/core/clients/manage/client-notification)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-passcode-records"></a>오래된 암호 기록 삭제

계층 구조의 최상위 사이트에서 이 작업을 사용하면 Android 및 Windows Phone 디바이스의 오래된 암호 재설정 데이터를 삭제할 수 있습니다. 암호 재설정 데이터는 암호화되지만 디바이스에 대한 PIN을 포함하고 있습니다. 기본적으로 이 작업은 사용하도록 설정되며 1일보다 오래된 데이터를 삭제합니다.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-replication-data"></a>오래된 복제 데이터 삭제

이 작업을 사용하면 데이터베이스에서 Configuration Manager 사이트 간 데이터베이스 복제에 대한 오래된 데이터를 삭제할 수 있습니다. 이 유지 관리 작업의 구성을 변경하는 경우 구성은 계층 내에서 해당되는 각 사이트에 적용됩니다. 자세한 내용은 [데이터베이스 복제 모니터링](/sccm/core/servers/manage/monitor-replication)을 참조하세요.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|**보조 사이트**|사용|

### <a name="delete-aged-replication-summary-data"></a>오래된 복제 요약 데이터 삭제

이 작업을 사용하면 지정한 시간 동안 오래된 복제 요약 데이터가 업데이트되지 않은 경우 사이트 데이터베이스에서 해당 데이터를 삭제할 수 있습니다. 자세한 내용은 [데이터베이스 복제 모니터링](/sccm/core/servers/manage/monitor-replication)을 참조하세요.  

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|**보조 사이트**|사용|

### <a name="delete-aged-status-messages"></a>오래된 상태 메시지 삭제

이 작업을 사용하면 데이터베이스에서 상태 필터 규칙에 구성된 대로 오래된 상태 메시지 데이터를 삭제할 수 있습니다. 자세한 내용은 [Configuration Manager의 상태 시스템 모니터링](/sccm/core/servers/manage/use-alerts-and-the-status-system#BKMK_MonitorSystemStatus)을 참조하세요.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-threat-data"></a>오래된 위협 데이터 삭제

이 작업을 사용하면 데이터베이스에서 지정된 시간보다 오래 저장된 오래된 Endpoint Protection 위협 데이터를 삭제할 수 있습니다. 자세한 내용은 [Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-unknown-computers"></a>오래된 알 수 없는 컴퓨터 삭제

지정한 시간 동안 알 수 없는 컴퓨터에 대한 정보가 업데이트되지 않은 경우 이 작업을 사용하여 사이트 데이터베이스에서 해당 정보를 삭제합니다. 자세한 내용은 [알 수 없는 컴퓨터 배포 준비](/sccm/osd/get-started/prepare-for-unknown-computer-deployments)를 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-aged-user-device-affinity-data"></a>오래된 사용자 디바이스 선호도 데이터 삭제

이 작업을 사용하면 데이터베이스에서 오래된 사용자 디바이스 선호도 데이터를 삭제할 수 있습니다. 자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-duplicate-system-discovery-data"></a>중복된 시스템 검색 데이터 삭제

이 작업을 사용하면 시스템 검색에서 생성된 모든 중복 레코드를 사이트 데이터베이스에서 삭제할 수 있습니다.<!-- SCCMDocs#1339 -->

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|기본 사이트|사용할 수 없음|
|보조 사이트|사용할 수 없음|

### <a name="delete-expired-mdm-bulk-enroll-package-records"></a>만료된 MDM 대량 등록 패키지 레코드 삭제

이 작업을 사용하면 등록 인증서가 만료된 후 이전 대량 등록 인증서와 해당 프로필을 삭제할 수 있습니다. 자세한 내용은 [인증서 프로필 만들기](/sccm/protect/deploy-use/create-certificate-profiles)를 참조하세요.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-inactive-client-discovery-data"></a>비활성 클라이언트 검색 데이터 삭제

이 작업을 사용하면 데이터베이스에서 비활성 클라이언트에 대한 검색 데이터를 삭제할 수 있습니다. 클라이언트가 더 이상 사용되지 않는 것으로 플래그가 지정되면 해당 사이트에서 클라이언트 상태에 대한 구성을 통해 비활성으로 표시합니다.

이 작업은 Configuration Manager 클라이언트 리소스에서만 작동합니다. 이 작업은 오래된 검색 데이터 레코드를 모두 삭제하는 **오래된 검색 데이터 삭제** 작업과는 다릅니다. 사이트 하나에서 이 작업이 실행되면 계층 내 모든 사이트의 데이터베이스에서 데이터가 제거됩니다. 자세한 내용은 [클라이언트 상태를 구성하는 방법](/sccm/core/clients/deploy/configure-client-status)을 참조하세요.

> [!IMPORTANT]  
> 이 작업을 사용하도록 설정한 경우 작업을 **하트비트 검색** 일정보다 더 긴 간격으로 실행되도록 구성합니다. 이 구성을 통해 활성 클라이언트는 하트비트 검색 레코드를 보내 자체 클라이언트 레코드를 활성으로 표시할 수 있으므로 이 작업에 의해 삭제되지 않습니다.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용 안 함|
|보조 사이트|사용할 수 없음|

### <a name="delete-obsolete-alerts"></a>사용되지 않는 경고 삭제

이 작업을 사용하면 데이터베이스에서 지정된 시간보다 오래 저장된 만료된 경고를 삭제할 수 있습니다. 자세한 내용은 [경고 및 상태 시스템 사용](/sccm/core/servers/manage/use-alerts-and-the-status-system)을 참조하세요.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-obsolete-client-discovery-data"></a>사용되지 않는 클라이언트 검색 데이터 삭제

이 작업을 사용하면 데이터베이스에서 사용되지 않는 클라이언트 레코드를 삭제할 수 있습니다. 사용되지 않음으로 표시된 레코드는 일반적으로 동일한 클라이언트에 대한 새 레코드로 교체됩니다. 새 레코드가 클라이언트의 현재 레코드가 됩니다. 검색에 대한 자세한 내용은 [검색 실행](/sccm/core/servers/deploy/configure/run-discovery)을 참조하세요.

> [!IMPORTANT]  
> 이 작업을 사용하도록 설정한 경우 작업을 하트비트 검색 일정보다 더 긴 간격으로 실행되도록 구성합니다. 이 구성을 통해 클라이언트는 사용되지 않음 상태를 올바르게 설정하는 하트비트 검색 레코드를 보낼 수 있습니다.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용 안 함|
|보조 사이트|사용할 수 없음|

### <a name="delete-obsolete-forest-discovery-sites-and-subnets"></a>사용되지 않는 포리스트 검색 사이트 및 서브넷 삭제

이 작업을 사용하면 Active Directory 사이트, 서브넷 및 도메인에 대한 데이터를 삭제할 수 있습니다. 최근 30일 동안 사이트에서 Active Directory 포리스트 검색 방법으로 검색하지 않은 데이터를 제거합니다. 이 작업은 검색 데이터를 제거하지만 이 검색 데이터에서 만든 경계는 영향을 받지 않습니다. 자세한 내용은 [검색 실행](/sccm/core/servers/deploy/configure/run-discovery)을 참조하세요.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="delete-orphaned-client-deployment-state-records"></a>분리된 클라이언트 배포 상태 레코드 삭제

이 작업을 사용하여 클라이언트 배포 상태 정보가 포함된 테이블을 주기적으로 제거합니다. 이 작업은 사용되지 않거나 폐기된 디바이스와 연결된 레코드를 정리합니다.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="evaluate-collection-members"></a>컬렉션 구성원 평가

컬렉션 멤버 자격 평가는 사이트 구성 요소로 구성합니다. 자세한 내용은 [사이트 구성 요소](/sccm/core/servers/deploy/configure/site-components)를 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="monitor-keys"></a>키 모니터링

이 작업을 사용하면 Configuration Manager 데이터베이스 기본 키의 무결성을 모니터링할 수 있습니다. 기본 키는 하나의 행을 고유하게 식별하는 열 또는 열의 조합입니다. 키는 Microsoft SQL Server 데이터베이스 테이블의 행을 다른 행과 구분합니다.

|||
|---------|---------|
|**중앙 관리 사이트**|사용|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="rebuild-indexes"></a>인덱스 다시 작성

이 작업을 사용하면 Configuration Manager 데이터베이스 인덱스를 다시 빌드할 수 있습니다. 인덱스는 데이터 검색 속도를 높이기 위해 데이터베이스 테이블에 만들어지는 데이터베이스 구조입니다. 예를 들어 인덱스된 열을 검색하는 것이 인덱스되지 않은 열을 검색하는 것보다 훨씬 빠른 경우가 많습니다.

성능을 높이기 위해 Configuration Manager 데이터베이스 인덱스는 끊임없이 변하면서 데이터베이스에 저장되는 데이터와 동기화 상태를 유지하기 위해 자주 업데이트됩니다. 수행할 작업:

- 50% 이상의 고유한 데이터베이스 열에 인덱스를 만듭니다.
- 50% 미만의 고유한 열에 인덱스를 삭제합니다.
- 데이터 고유성 조건을 충족하는 모든 기존 인덱스를 다시 빌드합니다.

|||
|---------|---------|
|**중앙 관리 사이트**|사용 안 함|
|**기본 사이트**|사용 안 함|
|**보조 사이트**|사용 안 함|

### <a name="summarize-file-usage-metering-data"></a>파일 사용랑 계량 데이터 요약

이 작업을 사용하면 소프트웨어 계량 파일 사용량에 대한 여러 레코드의 데이터가 단일 일반 레코드로 요약됩니다. 데이터 요약을 통해 Configuration Manager 데이터베이스에 저장된 데이터 양이 압축될 수 있습니다.

이 작업과 **소프트웨어 계량 월간 사용량 데이터 요약** 작업을 함께 사용하여 소프트웨어 계량 데이터를 요약하고 데이터베이스의 디스크 공간을 절약할 수 있습니다. 자세한 내용은 [소프트웨어 계량](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="summarize-installed-software-data"></a>설치된 소프트웨어 데이터 요약

이 작업을 사용하면 설치된 소프트웨어에 대한 여러 레코드의 데이터가 단일 일반 레코드로 요약됩니다. 데이터 요약을 통해 Configuration Manager 데이터베이스에 저장된 데이터 양이 압축될 수 있습니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="summarize-monthly-usage-metering-data"></a>월별 사용량 계량 데이터 요약

이 작업을 사용하면 소프트웨어 계량 월간 사용량에 대한 여러 레코드의 데이터가 단일 일반 레코드로 요약됩니다. 데이터 요약을 통해 Configuration Manager 데이터베이스에 저장된 데이터 양이 압축될 수 있습니다.

이 작업과 **소프트웨어 계량 파일 사용량 데이터 요약** 작업을 함께 사용하여 소프트웨어 계량 데이터를 요약하고 데이터베이스의 공간을 절약할 수 있습니다. 자세한 내용은 [소프트웨어 계량](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering)을 참조하세요.

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="update-application-available-targeting"></a>대상 지정이 가능한 애플리케이션 업데이트

이 작업을 사용하면 Configuration Manager에서 컬렉션의 리소스에 대한 정책 및 애플리케이션 배포의 매핑을 다시 계산합니다. 컬렉션에 정책 또는 애플리케이션을 배포하면 Configuration Manager에서 배포되는 개체와 컬렉션 멤버 간의 초기 매핑을 만듭니다.

이러한 매핑은 빠른 참조에 대한 테이블에 저장됩니다. 컬렉션 멤버 자격이 변경되면 해당 사이트에서 저장된 매핑이 변경 내용을 반영하도록 업데이트합니다. 그러나 이러한 매핑이 동기화되지 않을 수 있습니다. 예를 들어 사이트에서 알림 파일을 제대로 처리하지 못하면 매핑의 변경에 이 변경 사항이 반영되지 않을 수 있습니다. 이 작업은 현재 컬렉션 멤버 자격에 따라 해당 매핑을 새로 고칩니다.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|

### <a name="update-application-catalog-tables"></a>애플리케이션 카탈로그 테이블 업데이트

이 작업을 사용하여 애플리케이션 카탈로그 웹 사이트 데이터베이스 캐시와 최신 애플리케이션 정보를 동기화합니다. 이 유지 관리 작업의 구성을 변경하는 경우 계층 내에서 해당되는 각 사이트에 적용됩니다.  

|||
|---------|---------|
|중앙 관리 사이트|사용할 수 없음|
|**기본 사이트**|사용|
|보조 사이트|사용할 수 없음|


## <a name="see-also"></a>참고 항목

[유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks)
