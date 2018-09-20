---
title: 1806에 대한 검사 목록
titleSuffix: Configuration Manager
description: Configuration Manager 버전 1806으로 업데이트하기 전에 수행할 작업을 알아봅니다.
ms.date: 08/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bb0a87a6-fd65-440b-90a5-2fef35622c9d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d0f79053eba91ac7177fe117a79612d1c1988965
ms.sourcegitcommit: be8c0182db9ef55a948269fcbad7c0f34fd871eb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/23/2018
ms.locfileid: "42755779"
---
# <a name="checklist-for-installing-update-1806-for-configuration-manager"></a>Configuration Manager용 업데이트 1806을 설치하기 위한 검사 목록

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 현재 분기를 사용하는 경우 버전 1806용 콘솔 내 업데이트를 설치하여 이전 버전의 계층 구조를 업데이트할 수 있습니다. <!-- baseline only statement: (Because version 1802 is also available as [baseline media](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions), you can use the installation media to install the first site of a new hierarchy.)-->

버전 1806용 업데이트를 가져오려면 계층 구조의 최상위 사이트에서 서비스 연결점을 사용해야 합니다. 이 사이트 시스템 역할은 온라인 또는 오프라인 모드에 있을 수 있습니다. 계층 구조가 Microsoft에서 업데이트 패키지를 다운로드한 후 콘솔에서 찾습니다. **관리** 작업 영역에서 **업데이트 및 서비스** 노드를 선택합니다.

-   업데이트가 **사용 가능**으로 나열되면 업데이트를 설치할 준비가 된 것입니다. 버전 1806을 설치하기 전에 [업데이트 1806 설치 정보](#about-installing-update-1806) 및 업데이트를 시작하기 전에 수행할 구성에 대한 [검사 목록](#checklist)을 검토합니다.

-   업데이트가 **다운로드 중**으로 표시되고 변경되지 않는 경우 **hman.log** 및 **dmpdownloader.log**에서 오류가 있는지 검토합니다.

    -   dmpdownloader.log는 dmpdownloader 프로세스가 업데이트를 확인하기 전에 간격을 기다리고 있음을 나타낼 수 있습니다. 업데이트 재배포 파일의 다운로드를 다시 시작하기 위해 사이트 서버에서 **SMS_Executive** 서비스를 다시 시작합니다.

    -   프록시 서버 설정이 http://silverlight.dlservice.microsoft.com 및 http://download.microsoft.com에서 다운로드하지 않도록 방지하는 경우 또 다른 일반적인 다운로드 문제가 발생합니다.

업데이트 설치에 대한 자세한 내용은 [콘솔 내 업데이트 및 서비스](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing)를 참조하세요.

편재 분기 버전에 대한 자세한 내용은 [기준선 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)을 참조하세요.



## <a name="about-installing-update-1806"></a>업데이트 1806 설치 정보

#### <a name="sites"></a>사이트
업데이트 1806을 계층 구조의 최상위 사이트에 설치합니다. 중앙 관리 사이트 또는 독립 실행형 기본 사이트에서 설치를 시작합니다. 최상위 사이트에 업데이트가 설치되면 자식 사이트에서 다음과 같은 업데이트 동작이 나타납니다.

-   중앙 관리 사이트에서 업데이트 설치를 완료한 후 자식 기본 사이트가 업데이트를 자동으로 설치합니다. 서비스 창을 사용하여 사이트에서 업데이트를 설치하는 시기를 제어할 수 있습니다. 자세한 내용은 [사이트 서버에 대한 서비스 기간](/sccm/core/servers/manage/service-windows)을 참조하세요.

-   기본 상위 사이트에서 업데이트 설치를 완료한 후 Configuration Manager 콘솔 내에서 각 보조 사이트를 수동으로 업데이트합니다. 보조 사이트 서버의 자동 업데이트는 지원되지 않습니다.

#### <a name="site-system-roles"></a>사이트 시스템 역할
사이트 서버에서 업데이트를 설치할 때 모든 사이트 시스템 역할을 자동으로 업데이트합니다. 이러한 역할은 사이트 서버에 있거나 원격 서버에 설치됩니다. 업데이트를 설치하기 전에 각 사이트 시스템 서버에서 새 업데이트 버전에 대한 현재 필수 구성 요소를 충족하는지 확인해야 합니다.

#### <a name="configuration-manager-consoles"></a>Configuration Manager 콘솔   
업데이트가 완료된 후 처음으로 Configuration Manager 콘솔을 사용할 때 해당 콘솔을 업데이트하라는 메시지가 표시됩니다. 콘솔을 호스트하는 컴퓨터에서 Configuration Manager 설치를 실행하고, 콘솔을 업데이트하는 옵션을 선택할 수 있습니다. 가능한 빨리 콘솔에 업데이트를 설치합니다. 자세한 내용은 [Configuration Manager 콘솔 설치](/sccm/core/servers/deploy/install/install-consoles)를 참조하세요.

> [!IMPORTANT]  
> 중앙 관리 사이트에서 업데이트를 설치할 경우 다음 제한 사항과 모든 자식 기본 사이트가 업데이트 설치를 완료할 때까지 존재하는 지연에 유의하세요.    
> - **클라이언트 업그레이드**가 시작되지 않습니다. 여기에는 클라이언트 및 프로덕션 전 클라이언트의 자동 업데이트가 포함됩니다. 또한 마지막 사이트에서 업데이트 설치가 완료될 때까지 프로덕션 전 클라이언트를 프로덕션으로 수준을 올릴 수 없습니다. 마지막 사이트에서 업데이트 설치가 완료되면 구성 옵션에 따라 클라이언트 업그레이드가 시작됩니다.   
> - 업데이트를 통해 제공되는 **새로운 기능**을 사용할 수 없습니다. 이는 해당 기능에 관련된 데이터 복제가 해당 기능에 대한 지원이 아직 설치되지 않은 사이트로 전송되지 못하도록 차단하는 것입니다. 모든 기본 사이트에서 업데이트를 설치한 후 기능을 사용할 수 있습니다.   
> - 중앙 관리 사이트와 자식 기본 사이트 간의 **복제 링크**가 업그레이드되지 않음으로 표시됩니다. 이는 업데이트 팩 설치 상태에 완료 상태로 표시되고 복제 초기화 모니터링에 대한 경고가 나타납니다. 콘솔의 모니터링 노드에서 이는 *링크 구성 중*으로 표시됩니다.


## <a name="checklist"></a>확인 목록

#### <a name="all-sites-run-a-supported-version-of-configuration-manager"></a>모든 사이트에서 지원되는 Configuration Manager 버전 실행  
업데이트 1806의 설치를 시작하기 전에 계층의 각 사이트 서버에서 동일한 버전의 Configuration Manager를 실행해야 합니다. 1806으로 업데이트하려면 버전 1706, 1710 또는 1802를 사용해야 합니다.

#### <a name="review-the-status-of-your-product-licensing"></a>제품 라이선스의 상태 검토 
이 업데이트를 설치하기 위한 활성 SA(Software Assurance) 규약 또는 동등한 구독 권한이 있어야 합니다. 사이트를 업데이트할 때 **라이선싱** 페이지에서는 **Software Assurance 만료 날짜**를 확인하는 옵션을 제공합니다.

이 값은 선택 사항입니다. 라이선스 만료 날짜의 편리한 미리 알림으로 지정할 수 있습니다. 이 날짜는 미래 업데이트를 설치할 때 표시됩니다. 업데이트 설정 또는 설치 중에 이 값을 이전에 지정했을 수 있습니다. Configuration Manager 콘솔에서 이 값을 지정할 수도 있습니다. **관리** 작업 영역에서 **사이트 구성**을 확장하고, **사이트**를 선택합니다. 리본에서 **계층 구조 설정**을 클릭하고, **라이선스** 탭으로 전환합니다.

자세한 내용은 [라이선스 및 분기](/sccm/core/understand/learn-more-editions)를 참조하세요.

#### <a name="review-microsoft-net-versions"></a>Microsoft .NET 버전 검토 
사이트에서 이 업데이트를 설치할 때 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 필수 구성 요소가 이미 설치되지 않은 경우 사이트는 다음 사이트 시스템 역할 중 하나를 호스트하는 각 서버에 설치합니다.

-   관리 지점
-   서비스 연결 지점
-   등록 프록시 지점
-   등록 지점

이 설치는 사이트 시스템 서버를 다시 부팅 보류 중 상태로 전환하고 Configuration Manager 구성 요소 상태 뷰어에 오류를 보고할 수 있습니다. 또한, 서버가 다시 부팅될 때까지 서버의 .NET 응용 프로그램에서 임의의 오류가 발생할 수 있습니다.

자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.

#### <a name="review-the-version-of-the-windows-adk-for-windows-10"></a>Windows 10용 Windows ADK 버전 검토
Windows 10 ADK(평가 및 배포 키트)의 버전은 Configuration Manager 버전 1806에 대해 지원되어야 합니다. 지원되는 Windows ADK 버전에 대한 자세한 내용은 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요. Windows ADK를 업데이트해야 할 경우에는 Configuration Manager의 업데이트를 시작하기 전에 업데이트합니다. 이렇게 하면 기본 부팅 이미지가 자동으로 최신 버전의 Windows PE로 업데이트됩니다. 사이트를 업데이트한 후 사용자 지정 부팅 이미지를 수동으로 업데이트합니다.

Windows ADK를 업데이트하기 전에 사이트를 업데이트하는 경우 [부팅 이미지를 사용하여 배포 지점 업데이트](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image)를 참조하세요.

#### <a name="review-the-site-and-hierarchy-status-for-unresolved-issues"></a>해결되지 않은 문제에 대해 사이트 및 계층 구조 상태 검토 
사이트를 업데이트하기 전에 원격 컴퓨터에 설치된 사이트 서버, 사이트 데이터베이스 서버 및 사이트 시스템 역할의 모든 작동 문제를 해결합니다. 기존 작동 문제로 인해 사이트 업데이트가 실패할 수 있습니다.

자세한 내용은 [경고 및 상태 시스템 사용](/sccm/core/servers/manage/use-alerts-and-the-status-system)을 참조하세요.

#### <a name="review-file-and-data-replication-between-sites"></a>사이트 간의 파일 및 데이터 복제 검토   
사이트 간의 파일 및 데이터베이스 복제가 작동하고 최신 상태인지 확인합니다. 어떤 경우든 지연 또는 백로그는 원활한 업데이트 또는 성공적인 업데이트를 방해할 수 있습니다. 데이터베이스 복제의 경우 업데이트를 시작하기 전에 Replication Link Analyzer를 사용하여 문제를 해결할 수 있습니다.

자세한 내용은 [Replication Link Analyzer 정보](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA)를 참조하세요.

#### <a name="install-all-applicable-critical-windows-updates"></a>모든 적용 가능한 중요 Windows 업데이트 설치
Configuration Manager에 대한 업데이트를 설치하기 전에 각 해당 사이트 시스템에 대한 중요한 OS 업데이트를 설치합니다. 이러한 서버는 사이트 서버, 사이트 데이터베이스 서버 및 원격 사이트 시스템 역할을 포함합니다. 설치하는 업데이트에서 다시 시작하도록 요구하는 경우 업그레이드를 시작하기 전에 해당 서버를 다시 시작합니다.

#### <a name="disable-database-replicas-for-management-points-at-primary-sites"></a>기본 사이트의 관리 지점에 데이터베이스 복제본을 사용하지 않도록 설정   
Configuration Manager에서 관리 지점에 대한 데이터베이스 복제본이 사용하도록 설정된 기본 사이트를 성공적으로 업데이트할 수 없습니다. Configuration Manager용 업데이트를 설치하기 전에 데이터베이스 복제를 사용하지 않도록 설정합니다.

자세한 내용은 [관리 지점에 대한 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 참조하세요.

#### <a name="set-sql-server-alwayson-availability-groups-to-manual-failover"></a>SQL Server AlwaysOn 가용성 그룹을 수동 장애 조치(failover)로 설정   
가용성 그룹을 사용할 경우 업데이트 설치를 시작하기 전에 가용성 그룹이 수동 장애 조치(failover)로 설정되어 있는지 확인합니다. 사이트를 업데이트한 후에 장애 조치(failover)를 자동으로 복원할 수 있습니다. 자세한 내용은 [사이트 데이터베이스에 대한 SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)을 참조하세요.

#### <a name="disable-site-maintenance-tasks-at-each-site"></a>각 사이트에서 사이트 유지 관리 작업을 사용하지 않도록 설정
업데이트를 설치하기 전에 업데이트 프로세스가 활성 상태인 동안 실행될 수 있는 모든 사이트 유지 관리 작업을 사용하지 않도록 설정합니다. 예를 들어 다음이 있지만, 이에 국한되지는 않습니다.

-   백업 사이트 서버
-   오래된 클라이언트 작업 삭제
-   오래된 검색 데이터 삭제

업데이트를 설치하는 동안 사이트 데이터베이스 유지 관리 작업이 실행되면 업데이트 설치가 실패할 수 있습니다. 작업을 사용하지 않도록 설정하기 전에 작업 일정을 기록하세요. 그래야 업데이트가 설치된 후에 해당 구성을 복원할 수 있습니다.

자세한 내용은 [유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks) 및 [유지 관리 작업에 대한 참조](/sccm/core/servers/manage/reference-for-maintenance-tasks)를 참조하세요.

#### <a name="temporarily-stop-any-antivirus-software"></a>바이러스 백신 소프트웨어를 일시적으로 중지 
사이트를 업데이트하기 전에 Configuration Manager 서버에서 바이러스 백신 소프트웨어를 중지합니다. <!--SMS.503481--> 

#### <a name="create-a-backup-of-the-site-database"></a>사이트 데이터베이스의 백업 만들기 
사이트를 업데이트하기 전에 중앙 관리 사이트 및 기본 사이트에서 사이트 데이터베이스를 백업합니다. 이 백업은 재해 복구에 사용할 성공적인 백업이 있는지 확인합니다.

자세한 내용은 [백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 참조하세요.

#### <a name="plan-for-client-piloting"></a>클라이언트 파일럿에 대한 계획   
클라이언트를 업데이트하는 업데이트를 설치할 때 모든 활성 클라이언트를 배포하고 업그레이드하기 전에 사전 프로덕션 환경에서 새로운 클라이언트 업데이트를 테스트할 수 있습니다. 이 옵션을 활용하려면 업데이트의 설치를 시작하기 전에 사전 프로덕션에 대한 자동 업그레이드를 지원하도록 사이트를 구성해야 합니다.

자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients) 및 [사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](/sccm/core/clients/manage/upgrade/test-client-upgrades)을 참조하세요.

#### <a name="plan-to-use-service-windows"></a>서비스 창 사용 계획   
사이트 서버에 업데이트를 설치할 수 있는 기간을 정의하려면 서비스 기간을 사용합니다. 이를 통해 계층 구조의 사이트에서 업데이트를 설치하는 시기를 제어할 수 있습니다. 자세한 내용은 [사이트 서버에 대한 서비스 기간](/sccm/core/servers/manage/service-windows)을 참조하세요.

#### <a name="review-supported-extensions"></a>지원되는 확장 검토
<!--SCCMdocs#587--> Microsoft 또는 Microsoft 파트너에서 다른 제품으로 Configuration Manager를 확장하는 경우 해당 제품이 버전 1806을 지원하는지 확인합니다. 이 정보는 제품 공급업체를 통해 확인합니다. 예를 들어 Microsoft Deployment Toolkit [릴리스 정보](/sccm/mdt/release-notes)를 참조합니다.

#### <a name="run-the-setup-prerequisite-checker"></a>설치 필수 구성 요소 검사기 실행   
업데이트가 콘솔에 **사용 가능**으로 표시되는 경우 업데이트를 설치하기 전에 독립적으로 필수 구성 요소 검사기를 실행할 수 있습니다. 사이트에 업데이트를 설치할 때 필수 조건 검사가 다시 실행됩니다.

콘솔에서 필수 구성 요소 검사를 실행하려면 **관리**작업 영역으로 이동하여 **업데이트 및 서비스**를 선택합니다. **Configuration Manager 1806** 업데이트 패키지를 선택하고, 리본 메뉴에서 **필수 구성 요소 검사 실행**을 클릭합니다.

자세한 내용은 [콘솔 내 업데이트를 설치하기 전에](/sccm/core/servers/manage/install-in-console-updates#bkmk_beforeinstall)에서  **업데이트를 설치하기 전에 필수 구성 요소 검사기 실행**에 대한 섹션을 참조하세요.

> [!IMPORTANT]  
> 필수 구성 요소 검사기가 실행되면 프로세스에서 사이트 유지 관리 작업에 사용되는 일부 제품 소스 파일을 업데이트합니다. 따라서 필수 구성 요소 검사기를 실행한 후 업데이트를 설치하기 전에 사이트 유지 관리 작업을 수행해야 하는 경우 사이트 서버의 CD.Latest 폴더에서 **Setupwpf.exe**(Configuration Manager 설치 프로그램)를 실행합니다.

#### <a name="update-sites"></a>사이트 업데이트   
이제 계층 구조에 대한 업데이트 설치를 시작할 수 있습니다. 업데이트 설치에 대한 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)를 참조하세요.

일상적인 업무 시간 외에 업데이트를 설치하도록 계획할 수 있습니다. 프로세스가 비즈니스 작업에 최소한의 영향을 주는 시기를 확인합니다. 업데이트를 설치하면 해당 작업에서 사이트 구성 요소 및 사이트 시스템 역할을 다시 설치합니다.

자세한 내용은 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.



## <a name="post-update-checklist"></a>업데이트 후 검사 목록

사이트를 업데이트한 후에 다음 검사 목록을 사용하여 일반 작업 및 구성을 완료하세요.


#### <a name="confirm-version-and-restart-if-necessary"></a>버전 확인 및 다시 시작(필요한 경우)
각 사이트 서버 및 사이트 시스템 역할이 버전 1806으로 업데이트되었는지 확인합니다. 콘솔에서 **버전** 열을 **관리** 작업 영역의 **사이트** 및 **배포 지점** 노드에 추가합니다. 필요한 경우 사이트 시스템 역할이 새 버전에 대한 업데이트를 자동으로 다시 설치합니다. 

처음에 성공적으로 업데이트되지 않은 원격 사이트 시스템을 다시 시작하는 것이 좋습니다. 사이트 인프라를 검토하고, 적용 가능한 사이트 서버 및 원격 사이트 시스템 서버가 성공적으로 다시 시작되었는지 확인합니다. 일반적으로, Configuration Manager에서 사이트 시스템 역할의 필수 조건으로 .NET을 설치하는 경우에만 사이트 서버가 다시 시작됩니다.


#### <a name="confirm-site-to-site-replication-is-active"></a>사이트 간 복제가 활성 상태인지 확인
Configuration Manager 콘솔에서 다음 위치로 이동하여 상태를 보고, 복제가 활성 상태인지 확인합니다.  

-   **모니터링** 작업 영역, **사이트 계층** 노드  

-   **모니터링** 작업 영역, **데이터베이스 복제** 노드  

자세한 내용은 다음 아티클을 참조하세요.  
- [계층 구조 및 복제 인프라 모니터링](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure)
- [Replication Link Analyzer 정보](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA)  


#### <a name="update-configuration-manager-consoles"></a>Configuration Manager 콘솔 업데이트
모든 원격 Configuration Manager 콘솔을 동일한 버전으로 업데이트합니다. 콘솔을 업데이트하라는 메시지가 표시되는 경우는 다음과 같습니다.  

-   콘솔을 여는 경우  

-   콘솔에서 새 노드로 이동하는 경우  


#### <a name="reconfigure-database-replicas-for-management-points"></a>관리 지점에 대한 데이터베이스 복제본 다시 구성
기본 사이트를 업데이트한 후에는 사이트를 업데이트하기 전에 설치한 관리 지점에 대한 데이터베이스 복제본을 다시 구성합니다. 자세한 내용은 [관리 지점에 대한 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 참조하세요.  


#### <a name="reconfigure-any-disabled-maintenance-tasks"></a>사용하지 않도록 설정된 유지 관리 작업 다시 구성
업데이트를 설치하기 전에 사이트에서 데이터베이스 [유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks)을 사용하지 않도록 설정한 경우 해당 작업을 다시 구성합니다. 업데이트 전에 사용하던 설정과 동일한 설정을 사용합니다.  


#### <a name="update-clients"></a>클라이언트 업데이트
특히 업데이트를 설치하기 전에 클라이언트 파일럿을 구성한 경우 직접 만든 계획에 따라 클라이언트를 업데이트하세요. 자세한 내용은 [Windows 컴퓨터에 대한 클라이언트를 업그레이드하는 방법](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers)을 참조하세요.  


#### <a name="third-party-extensions"></a>타사 확장
Configuration Manager 확장을 사용하는 경우 Configuration Manager 버전 1806을 지원하는 최신 버전으로 업데이트합니다. 


#### <a name="update-custom-boot-images-and-media"></a>사용자 지정 부팅 이미지 및 미디어 업데이트
<!--SCCMDocs issue 775-->

기본 부팅 이미지와 사용자 지정 부팅 이미지 중 어느 것을 사용하든 사용하는 부팅 이미지에 대해 **배포 지점 업데이트** 작업을 사용하세요. 이 작업을 사용하면 클라이언트가 최신 버전을 사용할 수 있습니다. Windows ADK의 새 버전이 없더라도 업데이트로 구성 관리자 클라이언트 구성 요소가 변경될 수 있습니다. 부팅 이미지와 미디어를 업데이트하지 않으면, 장치에서 작업 순서 배포가 실패할 수 있습니다. 

사이트를 업데이트하면 Configuration Manager가 *기본* 부팅 이미지를 자동으로 업데이트합니다. 업데이트된 콘텐츠를 배포 지점에 자동으로 배포하지는 않습니다. 네트워크를 통해 이 콘텐츠를 배포할 준비가 되면 특정 부팅 이미지에 대해 **배포 지점 업데이트** 작업을 사용하세요. 

사이트를 업데이트한 후 *사용자 지정* 부팅 이미지를 수동으로 업데이트합니다. 이 작업에서는 필요할 경우 최신 클라이언트 구성 요소를 사용하여 부팅 이미지를 업데이트하고, 경우에 따라 현재 Windows PE 버전을 사용하여 부팅 이미지를 다시 로드하며, 콘텐츠를 배포 지점에 다시 배포합니다. 

자세한 내용은 [부팅 이미지를 사용하여 배포 지점 업데이트](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image)를 참조하세요. 