---
title: 유지 관리 작업에 대한 참조
titleSuffix: Configuration Manager
description: 각 System Center Configuration Manager 사이트 유지 관리 작업에 대한 세부 정보와 이러한 작업이 기본적으로 사용되는지 여부를 알아봅니다.
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f8450308f0719903bc4b3f74d6c2ab1ca5e17c59
ms.sourcegitcommit: e0209e4549e9828eb74089313dbee323ece1fc2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/13/2018
ms.locfileid: "51598617"
---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 유지 관리 작업 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 각 System Center Configuration Manager 사이트 유지 관리 작업에 대한 세부 정보를 설명하고 작업을 사용할 수 있는 사이트 유형을 소개합니다. 각 항목에서는 작업이 기본적으로 사용되는지 여부도 나타냅니다. 유지 관리 작업을 실행하기 위해 사이트를 계획하고 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 유지 관리 작업](../../../core/servers/manage/maintenance-tasks.md)을 참조하세요.  

**사이트 서버 백업**: 이 작업을 사용하여 중요한 데이터의 복구를 준비합니다. 중요한 정보의 백업을 만들어 사이트와 Configuration Manager 데이터베이스를 복원할 수 있습니다. 자세한 내용은 [System Center Configuration Manager 백업 및 복구](../../../protect/understand/backup-and-recovery.md)를 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용 안 함    
-   보조 사이트: 사용할 수 없음  

**인벤토리 정보를 사용하여 응용 프로그램 타이틀 확인**: 이 작업을 사용하면 소프트웨어 인벤토리에 보고된 소프트웨어 타이틀과 Asset Intelligence 카탈로그에 있는 소프트웨어 타이틀 간의 일관성을 유지할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 Asset Intelligence 소개](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md)를 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**설치 플래그 지우기**: 이 작업을 사용하면 **클라이언트 다시 검색** 기간 중 하트비트 검색 레코드를 제출하지 않는 클라이언트에 대해 설치 플래그를 제거할 수 있습니다. 설치 플래그는 활성 Configuration Manager 클라이언트를 포함할 수 있는 컴퓨터에 대해 자동 클라이언트 강제 설치가 실행되지 않도록 방지합니다.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용 안 함    
-   보조 사이트: 사용할 수 없음  

**오래된 응용 프로그램 요청 데이터 삭제**: 이 작업을 사용하면 오래된 응용 프로그램 요청을 데이터베이스에서 삭제할 수 있습니다. 응용 프로그램 요청에 대한 자세한 내용은 [System Center Configuration Manager를 사용하여 응용 프로그램 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 클라이언트 다운로드 기록 삭제**: 이 작업을 사용하여 클라이언트에서 사용한 다운로드 원본에 대한 기록 데이터를 삭제합니다. 다운로드 원본 정보는 [클라이언트 데이터 원본 대시보드](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard)를 채우는 데 사용됩니다.  
-  중앙 관리 사이트 - 사용할 수 없음
-    **기본 사이트** - 사용
-  보조 사이트 - 사용할 수 없음

**오래된 클라이언트 작업 삭제**: 이 작업을 사용하면 클라이언트 작업에 대한 오래된 데이터를 사이트 데이터베이스에서 삭제할 수 있습니다. 예를 들어 오래되거나 만료된 클라이언트 알림(예: 컴퓨터 또는 사용자 정책에 대한 다운로드 요청) 데이터 및 Endpoint Protection에 대한 데이터(예: 검사를 실행하거나 업데이트된 정의를 다운로드하기 위한 클라이언트 관리자의 요청)가 여기에 포함됩니다.

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 클라이언트 상태 기록 삭제**: 클라이언트 알림에서 기록한 클라이언트의 온라인 상태에 대한 기록 정보가 지정된 시간보다 오래된 경우 이 작업을 사용하면 이런 기록 정보를 삭제할 수 있습니다. 클라이언트 알림에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트를 모니터링하는 방법](../../../core/clients/manage/monitor-clients.md)을 참조하세요.  

-   **중앙 관리 사이트**: 사용   
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 클라우드 관리 게이트웨이 트래픽 데이터 삭제**: 이 작업을 사용하여 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 통과하는 트래픽에 대한 오래된 데이터를 사이트 데이터베이스에서 모두 삭제합니다. 예를 들어 요청 수, 총 요청 바이트, 총 응답 바이트, 실패한 요청 수, 최대 동시 요청 수 등에 대한 데이터를 삭제할 수 있습니다.  
- **중앙 관리 사이트 서버** - 사용
- **기본 사이트** - 사용
- 보조 사이트 - 사용할 수 없음


**오래된 수집 파일 삭제**: 이 작업을 사용하면 수집 파일에 대해 오래된 정보를 데이터베이스에서 삭제할 수 있습니다. 또한 이 작업은 선택한 사이트의 사이트 서버 폴더 구조에서 수집 파일을 삭제합니다. 기본적으로 수집된 파일의 복사본이 최신순으로 5개까지 사이트 서버의 **Inboxes\sinv.box\FileCol** 디렉터리에 저장됩니다. 자세한 내용은 [System Center Configuration Manager의 소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 컴퓨터 연결 데이터 삭제**: 이 작업을 사용하면 오래된 운영 체제 배포 컴퓨터 연결 데이터를 데이터베이스에서 삭제할 수 있습니다. 이 정보는 사용자 상태 복원을 완료하는 작업의 일부로 사용됩니다. 컴퓨터 연결에 대한 자세한 내용은 [System Center Configuration Manager의 사용자 상태 관리](../../../osd/get-started/manage-user-state.md)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 삭제 검색 데이터 삭제**: 이 작업을 사용하면 Extraction View로 만들어진 오래된 데이터를 데이터베이스에서 삭제할 수 있습니다. 기본적으로 Extraction View는 사용하지 않도록 설정됩니다. 사용하도록 설정하려면 Configuration Manager SDK를 사용해야 합니다. Extraction View를 사용하도록 설정하지 않는 한 이 작업에 대해 삭제할 데이터는 없습니다.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 장치 초기화 레코드 삭제**: 이 작업을 사용하면 모바일 장치 초기화 작업에 대한 오래된 데이터를 데이터베이스에서 삭제할 수 있습니다. 모바일 디바이스 초기화에 대한 자세한 내용은 [System Center Configuration Manager를 사용하여 원격 초기화, 잠금 또는 암호 재설정으로 데이터 보호](/sccm/mdm/deploy-use/wipe-lock-reset-devices)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**Exchange Server 커넥터에서 관리하는 오래된 장치 삭제**: 이 작업을 사용하면 Exchange Server 커넥터를 사용하여 관리되는 모바일 장치에 대한 오래된 데이터를 삭제할 수 있습니다. 이 데이터는 Exchange Server 커넥터 속성의 **검색** 탭에 있는 **다음 기간(일)을 초과해 비활성 상태인 모바일 디바이스 무시** 옵션에서 구성한 간격에 따라 삭제됩니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음   
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 검색 데이터 삭제**: 이 작업을 사용하면 오래된 검색 데이터를 데이터베이스에서 삭제할 수 있습니다. 이 데이터에는 하트비트 검색, 네트워크 검색, Active Directory Domain Services 검색 방법 등으로 검색되는 레코드(시스템, 사용자, 그룹)가 포함될 수 있습니다. 이 작업은 또한 서비스가 해제된 것으로 표시된 오래된 디바이스를 제거합니다. 사이트에서 이 작업을 실행하면 해당 사이트와 연결된 데이터는 삭제되고 관련 변경 내용은 다른 사이트에 복제됩니다. 검색에 대한 자세한 내용은 [System Center Configuration Manager에 대한 검색 실행](../../../core/servers/deploy/configure/run-discovery.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 배포 지점 사용량 데이터 삭제**: 이 작업을 사용하면 지정된 시간보다 오래 저장된 배포 지점 데이터의 오래된 데이터를 데이터베이스에서 삭제할 수 있습니다.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 Endpoint Protection 상태 기록 데이터 삭제**: 이 작업을 사용하면 Endpoint Protection에 대한 오래된 상태 정보를 데이터베이스에서 삭제할 수 있습니다. Endpoint Protection 상태 정보에 대한 자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection을 모니터링하는 방법](../../../protect/deploy-use/monitor-endpoint-protection.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 등록 장치 삭제**: 1602의 업데이트부터 이 작업은 기본적으로 사용하지 않도록 설정됩니다. 이 작업을 사용하면 지정된 시간 동안 사이트에 아무 정보도 보고하지 않은 모바일 디바이스의 오래된 데이터를 사이트 데이터베이스에서 삭제할 수 있습니다.

이 작업은 Microsoft Intune(하이브리드)을 사용하여 등록되었거나 온-프레미스 모바일 디바이스 관리에서 Configuration Manager에 등록된 디바이스에 적용됩니다. 자세한 내용은 [클라이언트 및 디바이스 지원 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS)를 참조하세요.

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용 안 함    
-   보조 사이트: 사용할 수 없음  

**오래된 인벤토리 기록 삭제**: 이 작업을 사용하면 지정된 시간보다 오래 저장되어 있는 인벤토리 데이터를 데이터베이스에서 삭제할 수 있습니다. 인벤토리 기록에 대한 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 로그 데이터 삭제**: 이 작업을 사용하면 문제 해결에 사용된 오래된 로그 데이터를 데이터베이스에서 삭제할 수 있습니다. 이 데이터는 Configuration Manager 구성 요소 작업과 관련이 없습니다.  

> [!IMPORTANT]  
> 기본적으로 이 작업은 각 사이트에서 매일 실행됩니다. 이 작업은 중앙 관리 사이트 및 기본 사이트에서 30일이 경과한 데이터를 삭제합니다. 보조 사이트에서 SQL Server Express를 사용할 경우 이 작업은 매일 실행되어야 하고 7일 동안 비활성 상태인 데이터를 삭제해야 합니다.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   **보조 사이트**: 사용  

**오래된 알림 작업 기록 삭제**: 지정한 시간 동안 클라이언트 알림 작업에 대한 정보가 업데이트되지 않은 경우 이 작업을 사용하면 이런 정보를 사이트 데이터베이스에서 삭제할 수 있습니다. 클라이언트 알림에 대한 자세한 내용은 [System Center Configuration Manager에 대한 클라이언트 배포 작업](../../../core/clients/manage/monitor-clients.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 복제 요약 데이터 삭제**: 지정한 시간 동안 오래된 복제 요약 데이터가 업데이트되지 않은 경우 이 작업을 사용하면 이런 데이터를 사이트 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 계층 및 복제 인프라 모니터링](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) 항목의 [데이터베이스 복제 링크 및 복제 상태를 모니터링하는 방법](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) 섹션을 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   **보조 사이트**: 사용  

**오래된 암호 기록 삭제**: 계층 구조의 최상위 사이트에서 이 작업을 사용하면 Android 및 Windows Phone 장치의 오래된 암호 재설정 데이터를 삭제할 수 있습니다. 암호 재설정 데이터는 암호화되지만 디바이스에 대한 PIN을 포함하고 있습니다. 기본적으로 이 작업은 사용하도록 설정되며 1일보다 오래된 데이터를 삭제합니다.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 복제 추적 데이터 삭제**: 이 작업을 사용하면 Configuration Manager 사이트 간 데이터베이스 복제에 대한 오래된 데이터를 데이터베이스에서 삭제할 수 있습니다. 이 유지 관리 작업의 구성을 변경하는 경우 구성은 계층 내에서 해당되는 각 사이트에 적용됩니다. 자세한 내용은 [System Center Configuration Manager에서 계층 및 복제 인프라 모니터링](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) 항목의 [데이터베이스 복제 링크 및 복제 상태를 모니터링하는 방법](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) 섹션을 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   **보조 사이트**: 사용  

**오래된 소프트웨어 계량 데이터 삭제**: 이 작업을 사용하면 지정된 시간보다 오래 저장되어 있는 오래된 소프트웨어 계량 관련 데이터를 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 소프트웨어 계량](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 소프트웨어 계량 요약 데이터 삭제**: 이 작업을 사용하면 지정된 시간보다 오래 저장되어 있는 오래된 소프트웨어 계량 관련 요약 데이터를 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 소프트웨어 계량](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 상태 메시지 삭제**: 이 작업을 사용하면 상태 필터 규칙에 구성된 대로 오래된 상태 메시지 데이터를 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에 대한 경고 및 상태 시스템 사용](../../../core/servers/manage/use-alerts-and-the-status-system.md) 항목의 Configuration Manager의 상태 시스템 모니터링 섹션을 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 위협 데이터 삭제**: 이 작업을 사용하면 지정된 시간보다 오래 저장되어 있는 오래된 Endpoint Protection 위협 데이터를 데이터베이스에서 삭제할 수 있습니다. Endpoint Protection에 대한 자세한 내용은 [System Center Configuration Manager의 Endpoint Protection 구성](../../../protect/deploy-use/endpoint-protection.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 알 수 없는 컴퓨터 삭제**: 지정한 시간 동안 컴퓨터에 대한 정보가 업데이트되지 않은 경우에 이 작업을 사용하면 알 수 없는 컴퓨터에 대한 정보를 사이트 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 알 수 없는 컴퓨터 배포 준비](../../../osd/get-started/prepare-for-unknown-computer-deployments.md)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**오래된 사용자 장치 선호도 데이터 삭제**: 이 작업을 사용하면 오래된 사용자 장치 선호도 데이터를 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**만료된 MDM 대량 등록 패키지 레코드 삭제**: 이 작업을 사용하면 등록 인증서가 만료된 후 이전 대량 등록 인증서와 해당 프로필을 삭제할 수 있습니다. 자세한 내용은 [인증서 프로필 만들기](/sccm/protect/deploy-use/create-certificate-profiles)를 참조하세요.
-   **중앙 관리 사이트**: 사용
-   **기본 사이트**: 사용
-   보조 사이트: 사용할 수 없음

**비활성 클라이언트 검색 데이터 삭제**: 이 작업을 사용하면 비활성 클라이언트에 대한 검색 데이터를 데이터베이스에서 삭제할 수 있습니다. 클라이언트가 더 이상 사용되지 않는 것으로 플래그가 지정되면 클라이언트 상태에 대한 구성을 통해 비활성으로 표시됩니다.

이 작업은 Configuration Manager 클라이언트 리소스에서만 작동합니다. 이 작업은 오래된 검색 데이터 레코드를 모두 삭제하는 **오래된 검색 데이터 삭제** 작업과는 다릅니다. 사이트 하나에서 이 작업이 실행되면 계층 내 모든 사이트의 데이터베이스에서 데이터가 제거됩니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 상태를 구성하는 방법](../../../core/clients/deploy/configure-client-status.md)항목을 참조하세요.  

> [!IMPORTANT]  
> 이 작업을 사용하도록 설정한 경우 작업을 **하트비트 검색** 일정보다 더 긴 간격으로 실행되도록 구성합니다. 이렇게 하면 활성 클라이언트는 하트비트 검색 레코드를 보내 자체 클라이언트 레코드를 활성으로 표시할 수 있으므로 이 작업에 의해 삭제되지 않습니다.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용 안 함    
-   보조 사이트: 사용할 수 없음  

**사용되지 않는 경고 삭제**: 이 작업을 사용하면 지정된 시간보다 오래 저장되어 있는 만료된 경고를 데이터베이스에서 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에 대한 경고 및 상태 시스템 사용](../../../core/servers/manage/use-alerts-and-the-status-system.md)을 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**사용되지 않는 클라이언트 검색 데이터 삭제**: 이 작업을 사용하면 사용되지 않는 클라이언트 레코드를 데이터베이스에서 삭제할 수 있습니다. 사용되지 않음으로 표시된 레코드는 일반적으로 동일한 클라이언트에 대한 새 레코드로 교체됩니다. 새 레코드가 클라이언트의 현재 레코드가 됩니다. 검색에 대한 자세한 내용은 [System Center Configuration Manager에 대한 검색 실행](../../../core/servers/deploy/configure/run-discovery.md)을 참조하세요.  

> [!IMPORTANT]  
> 이 작업을 사용하도록 설정한 경우 작업을 하트비트 검색 일정보다 더 긴 간격으로 실행되도록 구성합니다. 이렇게 하면 클라이언트는 사용되지 않음 상태를 올바르게 설정하는 하트비트 검색 레코드를 보낼 수 있습니다.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용 안 함    
-   보조 사이트: 사용할 수 없음  

**사용되지 않는 포리스트 검색 사이트 및 서브넷 삭제**: 이 작업을 사용하면 지난 30일 안에 Active Directory 포리스트 검색 방법으로 검색되지 않은 Active Directory 사이트, 서브넷 및 도메인에 대한 데이터를 삭제할 수 있습니다. 이 경우 검색 데이터는 제거되지만 이 검색 데이터에서 만든 경계는 영향을 받지 않습니다. 자세한 내용은 [System Center Configuration Manager에 대한 검색 실행](../../../core/servers/deploy/configure/run-discovery.md)을 참조하세요.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**분리된 클라이언트 배포 상태 레코드 삭제**: 이 작업을 사용하여 클라이언트 배포 상태 정보가 포함된 테이블을 주기적으로 제거합니다. 이 작업은 사용되지 않거나 폐기된 디바이스와 연결된 레코드를 정리합니다.  
-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음

**사용되지 않은 응용 프로그램 수정 버전 삭제**: 이 작업을 사용하면 더 이상 참조되지 않는 응용 프로그램 수정 버전을 삭제할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램을 수정하고 대체하는 방법](../../../apps/deploy-use/revise-and-supersede-applications.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**컬렉션 멤버 평가**: 컬렉션 멤버 평가를 사이트 구성 요소로 구성합니다. 사이트 구성 요소에 대한 자세한 내용은 [System Center Configuration Manager의 사이트 구성 요소](../../../core/servers/deploy/configure/site-components.md)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**키 모니터링**: 이 작업을 사용하면 Configuration Manager 데이터베이스 기본 키의 무결성을 모니터링할 수 있습니다. 기본 키는 Microsoft SQL Server 데이터베이스 테이블에서 행을 고유하게 식별하고 다른 행과 구분하는 열 또는 열 조합입니다.  

-   **중앙 관리 사이트**: 사용    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**인덱스 다시 작성**: 이 작업을 사용하면 Configuration Manager 데이터베이스 인덱스를 다시 작성할 수 있습니다. 인덱스는 데이터 검색 속도를 높이기 위해 데이터베이스 테이블에 만들어지는 데이터베이스 구조입니다. 예를 들어 인덱스된 열을 검색하는 것이 인덱스되지 않은 열을 검색하는 것보다 훨씬 빠른 경우가 많습니다.

성능을 높이기 위해 Configuration Manager 데이터베이스 인덱스는 끊임없이 변하면서 데이터베이스에 저장되는 데이터와 동기화 상태를 유지하기 위해 자주 업데이트됩니다. 이 작업을 통해 고유성이 50% 이상인 인덱스는 데이터베이스 열에 만들어지고, 고유성이 50% 미만인 인덱스는 열에 삭제되며, 데이터베이스 고유성 기준을 충족하는 모든 기존 인덱스는 다시 작성됩니다.  

-   **중앙 관리 사이트 서버**: 사용 안 함    
-   **기본 사이트**: 사용 안 함    
-   **보조 사이트**: 사용 안 함  

**설치된 소프트웨어 데이터 요약**: 이 작업을 사용하면 설치된 소프트웨어에 대한 여러 레코드의 데이터가 단일 일반 레코드로 요약됩니다. 데이터 요약을 통해 Configuration Manager 데이터베이스에 저장된 데이터 양이 압축될 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 소프트웨어 인벤토리 소개](../../clients/manage/inventory\introduction-to-software-inventory.md)를 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**소프트웨어 계량 파일 사용량 데이터 요약**: 이 작업을 사용하면 소프트웨어 계량 파일 사용량에 대한 여러 레코드의 데이터가 단일 일반 레코드로 요약됩니다. 데이터 요약을 통해 Configuration Manager 데이터베이스에 저장된 데이터 양이 압축될 수 있습니다.

이 작업과 **소프트웨어 계량 월간 사용량 데이터 요약** 작업을 함께 사용하여 소프트웨어 계량 데이터를 요약하고 Configuration Manager 데이터베이스의 디스크 공간을 절약할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 소프트웨어 계량](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**소프트웨어 계량 월간 사용량 데이터 요약**: 이 작업을 사용하면 소프트웨어 계량 월간 사용량에 대한 여러 레코드의 데이터가 단일 일반 레코드로 요약됩니다. 데이터 요약을 통해 Configuration Manager 데이터베이스에 저장된 데이터 양이 압축될 수 있습니다.

이 작업과 **소프트웨어 계량 파일 사용량 데이터 요약** 작업을 함께 사용하여 소프트웨어 계량 데이터를 요약하고 Configuration Manager 데이터베이스의 공간을 절약할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 소프트웨어 계량](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**대상 지정이 가능한 응용 프로그램 업데이트**: 이 작업을 사용하면 Configuration Manager에서 컬렉션의 리소스와 정책 및 응용 프로그램 배포 간의 매핑을 다시 계산합니다. 컬렉션에 정책 또는 응용 프로그램을 배포하면 Configuration Manager에서 배포되는 개체와 컬렉션 멤버 간의 초기 매핑을 만듭니다.

이러한 매핑은 빠른 참조에 대한 테이블에 저장됩니다. 컬렉션 멤버 자격이 변경되면 저장된 매핑이 변경 내용을 반영하도록 업데이트됩니다. 그러나 이러한 매핑이 동기화되지 않을 수 있습니다. 예를 들어 사이트에서 알림 파일을 제대로 처리하지 못하면 매핑의 변경에 이 변경 사항이 반영되지 않을 수 있습니다. 이 작업은 현재 컬렉션 멤버 자격에 따라 해당 매핑을 새로 고칩니다.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  

**응용 프로그램 카탈로그 테이블 업데이트**: 이 작업을 사용하면 응용 프로그램 카탈로그 웹 사이트 데이터베이스 캐시와 최신 응용 프로그램 정보를 동기화할 수 있습니다. 이 유지 관리 작업의 구성을 변경하는 경우 구성은 계층 내에서 해당되는 각 사이트에 적용됩니다.  

-   중앙 관리 사이트: 사용할 수 없음    
-   **기본 사이트**: 사용    
-   보조 사이트: 사용할 수 없음  
