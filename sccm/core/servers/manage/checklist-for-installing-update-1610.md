---
title: "1610에 대한 검사 목록 | System Center Configuration Manager"
description: "System Center Configuration Manager 버전 1610으로 업데이트하기 전에 수행할 작업에 대해 알아봅니다."
ms.custom: na
ms.date: 2/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b411cb0-4fd1-41f2-a2f6-33738a5bde96
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 30af3326578d39c6d995672071705bcaeb877e4d
ms.openlocfilehash: 640fc5ddb4e0a6828901b7f406ca72fc210b2970
ms.lasthandoff: 02/23/2017

---
# <a name="checklist-for-installing-update-1610-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 업데이트 1610을 설치하기 위한 검사 목록

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 현재 분기를 사용하는 경우 버전 1610에 대한 콘솔 내 업데이트를 설치하여 계층 구조를 버전 1606에서 업데이트할 수 있습니다. 계층 구조에서 버전 1511, 1602 또는 1606을 실행하는 경우 버전 1610으로 업데이트할 수 있습니다.

버전 1610에 대한 업데이트를 가져오려면 계층 구조의 최상위 사이트에서 서비스 연결 지점 사이트 시스템 역할을 사용해야 합니다. 온라인 또는 오프라인 모드에 있을 수 있습니다. 계층 구조에서 Microsoft에서 업데이트 패키지를 다운로드하면 콘솔의 **관리 &gt; 개요 &gt; 클라우드 서비스 &gt; 업데이트 및 서비스**에 표시됩니다.

-   업데이트가 **사용 가능**으로 나열되면 업데이트를 설치할 준비가 된 것입니다. 버전 1610을 설치하기 전에 [업데이트 1610 설치 정보](#about-installing-update-1610) 및 업데이트를 시작하기 전에 수행할 구성에 대한 [검사 목록](#checklist)의 정보를 검토합니다.

-   업데이트가 **다운로드 중**으로 표시되고 변경되지 않는 경우 **hman.log** 및 **dmpdownloader.log**에서 오류가 있는지 검토합니다.

    -   일반적으로 사이트 서버에서 **SMS_Executive** 서비스를 다시 시작하여 업데이트 재배포 파일의 다운로드를 다시 시작할 수도 있습니다.

    -   또 다른 일반적인 다운로드 문제는 프록시 서버 설정에서 <http://silverlight.dlservice.microsoft.com> 및 <http://download.microsoft.com>에서 다운로드를 차단하는 경우에 발생합니다.

업데이트 설치에 대한 자세한 내용은 [콘솔 내 업데이트 및 서비스](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing)를 참조하세요.

현재 분기 버전에 대한 자세한 내용은 [System Center Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)에서 [기준선 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)을 참조하세요.

## <a name="about-installing-update-1610"></a>업데이트 1610 설치 정보

**사이트:**  
업데이트 1610은 계층 구조의 최상위 사이트에만 설치할 수 있습니다. 즉, 중앙 관리 사이트(있는 경우) 또는 독립 실행형 기본 사이트에서 설치를 시작합니다. 최상위 계층 사이트에 업데이트가 설치되면 자식 사이트에서 다음과 같은 업데이트 동작이 나타납니다.

-   중앙 관리 사이트에서 업데이트 설치를 완료한 후 자식 기본 사이트가 업데이트를 자동으로 설치합니다. 서비스 창을 사용하여 사이트에서 업데이트를 설치하는 시기를 제어할 수 있습니다. 1606 이전 버전에서는 서비스 창을 유지 관리 창이라고 했습니다. 자세한 내용은 [사이트 서버에 대한 서비스 기간](/sccm/core/servers/manage/service-windows)을 참조하세요.

-   기본 상위 사이트에서 업데이트 설치를 완료한 후 Configuration Manager 콘솔 내에서 보조 사이트를 수동으로 업데이트해야 합니다. 보조 사이트 서버의 자동 업데이트는 지원되지 않습니다.

**사이트 시스템 역할:**  
사이트 서버에서 업데이트를 설치할 때 사이트 서버에 설치된 사이트 시스템 역할과 원격 컴퓨터에 설치된 사이트 시스템 역할이 자동으로 업데이트됩니다. 따라서 업데이트를 설치하기 전에 각 사이트 시스템 서버에서 새 업데이트 버전에 대한 작업의 새로운 필수 조건을 충족하는지 확인해야 합니다.

**Configuration Manager 콘솔:**   
업데이트가 완료된 후 처음으로 Configuration Manager 콘솔을 사용할 때 해당 콘솔을 업데이트하라는 메시지가 표시됩니다. 그렇게 하려면 콘솔을 호스트하는 컴퓨터에서 Configuration Manager 설치 프로그램을 실행하고 콘솔을 업데이트하는 옵션을 선택해야 합니다. 콘솔에 업데이트 설치를 연기하지 않는 것이 좋습니다.



## <a name="checklist"></a>확인 목록

**모든 사이트에서 System Center Configuration Manager의 지원되는 버전을 실행하는지 확인:** 업데이트 1610의 설치를 시작하려면 먼저 계층 구조의 각 사이트에서 System Center Configuration Manager 버전 1511, 1602 또는 1606을 실행해야 합니다.

**Software Assurance 또는 동등한 구독 권한의 상태 검토:**   
업데이트 1610을 설치하려면 활성 SA(Software Assurance) 계약이 있어야 합니다. 버전 1610을 설치하는 경우 **라이선스** 탭에 **Software Assurance 만료 날짜**를 확인하는 옵션이 있습니다.

이 값은 향후 업데이트를 설치할 때 표시되는 사용자 라이선스 만료 날짜에 대한 편리한 미리 알림으로 지정할 수 있는 선택적 값입니다. 버전 1606 기준 미디어에서 Configuration Manager를 설치한 경우 설치 중에 이 값을 지정했거나 사이트 설치 후 **계층 설정**의 **라이선스** 탭에서 이 값을 지정했을 수 있습니다.

자세한 내용은 [System Center Configuration Manager의 라이선스 및 분기](/sccm/core/understand/learn-more-editions)를 참조하세요.

**사이트 시스템 서버에 설치된 .NET 버전 검토:** 사이트에서 업데이트 1610을 설치할 때 .NET Framework 4.5 이상이 아직 설치되어 있지 않으면 Configuration Manager가 다음 사이트 시스템 역할 중 하나를 호스트하는 각 컴퓨터에 자동으로 .NET Framework 4.5.2 이상을 설치합니다.

-   등록 프록시 지점
-   등록 지점
-   관리 지점
-   서비스 연결 지점

이 설치는 사이트 시스템 서버를 다시 부팅 보류 중 상태로 전환하고 Configuration Manager 구성 요소 상태 뷰어에 오류를 보고할 수 있습니다. 또한, 서버가 다시 부팅될 때까지 서버의 .NET 응용 프로그램에서 임의의 오류가 발생할 수 있습니다.

자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.

**사이트 및 계층 구조 상태를 검토하고 해결되지 않은 문제가 있는지 확인:** 사이트를 업데이트하기 전에 원격 컴퓨터에 설치된 사이트 서버, 사이트 데이터베이스 서버 및 사이트 시스템 역할에 대한 모든 작동 문제를 해결합니다. 기존 작동 문제로 인해 사이트 업데이트가 실패할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에 대한 경고 및 상태 시스템 사용](/sccm/core/servers/manage/use-alerts-and-the-status-system)을 참조하세요.

**사이트 간의 파일 및 데이터 복제 검토:**   
사이트 간의 파일 및 데이터베이스 복제가 작동하고 최신 상태인지 확인합니다. 어떤 경우든 지연 또는 백로그는 원활한 업데이트 또는 성공적인 업데이트를 방해할 수 있습니다.
데이터베이스 복제의 경우 업데이트를 시작하기 전에 Replication Link Analyzer를 사용하여 문제를 해결할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에서 계층 구조 및 복제 인프라 모니터링](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) 항목에서 [Replication Link Analyzer 정보](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA)를 참조하세요.

**사이트, 사이트 데이터베이스 서버 및 원격 사이트 시스템 역할을 호스트하는 컴퓨터에서 해당하는 모든 중요한 운영 체제 업데이트 설치:** Configuration Manager에 대한 업데이트를 설치하기 전에 해당하는 각 사이트 시스템에 대한 모든 중요 업데이트를 설치합니다. 설치하는 업데이트에 다시 시작이 필요한 경우 Configuration Manager 업데이트를 시작하기 전에 해당 컴퓨터를 다시 시작합니다.

**기본 사이트의 관리 지점에 데이터베이스 복제본을 사용하지 않도록 설정:**   
Configuration Manager에서 관리 지점에 대한 데이터베이스 복제본이 사용하도록 설정된 기본 사이트를 성공적으로 업데이트할 수 없습니다. 데이터베이스 복제를 사용하지 않도록 설정한 후 다음을 수행합니다.

-   데이터베이스 업그레이드를 테스트하기 위해 사이트 데이터베이스 백업 만들기
-   Configuration Manager에 대한 업데이트 설치

자세한 내용은 [System Center Configuration Manager의 관리 지점용 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 참조하세요.

**SQL Server AlwaysOn 가용성 그룹을 수동 장애 조치(failover)로 설정:**   
버전 1610과 같은 업데이트를 설치하기 전에 가용성 그룹이 수동 장애 조치로 설정되어 있는지 확인합니다. 사이트를 업데이트한 후에 장애 조치를 자동으로 되돌릴 수 있습니다. 자세한 내용은 [사이트 데이터베이스에 대한 SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)을 참조하세요.

**NLB를 사용하는 소프트웨어 업데이트 지점 다시 구성:**   
Configuration Manager에서는 NLB(네트워크 부하 분산) 클러스터를 사용하는 사이트를 소프트웨어 업데이트 지점을 호스트하도록 업데이트할 수 없습니다.

소프트웨어 업데이트 지점에 NLB 클러스터를 사용하는 경우 Windows PowerShell을 사용하여 NLB 클러스터를 제거하세요.
자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates)을 참조하세요.

**해당 사이트에 업데이트를 설치하는 동안 각 사이트에서 모든 사이트 유지 관리 작업을 사용하지 않도록 설정**   
업데이트를 설치하기 전에 업데이트 프로세스가 활성 상태인 동안 실행될 수 있는 모든 사이트 유지 관리 작업을 사용하지 않도록 설정합니다. 이러한 작업의 일부 예는 다음과 같습니다.

-   백업 사이트 서버
-   오래된 클라이언트 작업 삭제
-   오래된 검색 데이터 삭제

업데이트를 설치하는 동안 사이트 데이터베이스 유지 관리 작업이 실행되면 업데이트 설치가 실패할 수 있습니다. 작업을 사용하지 않도록 설정하기 전에 작업 일정을 기록하세요. 그래야 업데이트가 설치된 후에 해당 구성을 복원할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에 대한 유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks) 및 [System Center Configuration Manager에 대한 유지 관리 작업 참조](/sccm/core/servers/manage/reference-for-maintenance-tasks)를 참조하세요.

**중앙 관리 사이트 및 기본 사이트에서 사이트 데이터베이스의 백업 만들기:** 사이트를 업데이트하기 전에 사이트 데이터베이스를 백업하여 재해 복구에 사용할 성공적인 백업을 생성해야 합니다.

자세한 내용은 [System Center Configuration Manager 백업 및 복구](/sccm/protect/understand/backup-and-recovery)를 참조하세요.

**최신 사이트 데이터베이스 백업의 복사본에서 데이터베이스 업그레이드 테스트:** System Center Configuration Manager 중앙 관리 사이트 또는 기본 사이트를 업데이트하기 전에 사이트 데이터베이스의 복사본에서 사이트 데이터베이스 업그레이드 프로세스를 테스트합니다.

-   사이트를 업그레이드할 때 사이트 데이터베이스가 수정될 수 있기 때문에 사이트 데이터베이스 업그레이드 프로세스를 테스트하는 것이 좋습니다.

-   데이터베이스 업그레이드 테스트를 반드시 수행해야 하는 것은 아니지만, 수행할 경우 프로덕션 데이터베이스가 영향을 받기 전에 업그레이드 문제를 파악할 수 있습니다.

-   사이트 데이터베이스 업그레이드가 실패하면 사이트 데이터베이스가 작동 불가능해질 수 있고 기능을 복원하기 위해 사이트 복구가 필요할 수 있습니다.

-   사이트 데이터베이스는 계층의 여러 사이트 간에 공유되지만 사이트를 업그레이드하기 전에 각 해당 사이트에서 데이터베이스를 테스트하세요.

-   기본 사이트의 관리 지점에 데이터베이스 복제본을 사용할 경우 사이트 데이터베이스 백업을 만들기 전에 복제본을 사용하지 않도록 설정합니다.

Configuration Manager는 보조 사이트의 백업을 지원하지 않으며, 보조 사이트 데이터베이스의 테스트 업그레이드도 지원하지 않습니다.

프로덕션 사이트 데이터베이스에서 테스트 데이터베이스 업그레이드를 실행해서는 안 됩니다. 이렇게 하면 사이트 데이터베이스가 업데이트되어 사이트가 작동하지 않을 수 있습니다. 자세한 내용은 **콘솔 업데이트를 설치하기 전에**에서 [2단계: 업데이트를 설치하기 전에 데이터베이스 업그레이드 테스트](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2)를 참조하세요.

**클라이언트 파일럿에 대한 계획:**   
클라이언트를 업데이트하는 업데이트를 설치할 때 모든 활성 클라이언트를 배포하고 업그레이드하기 전에 사전 프로덕션 환경에서 새로운 클라이언트 업데이트를 테스트할 수 있습니다.

이 옵션을 활용하려면 업데이트의 설치를 시작하기 전에 사전 프로덕션에 대한 자동 업그레이드를 지원하도록 사이트를 구성해야 합니다.

자세한 내용은 [System Center Configuration Manager에서 클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients) 및 [System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](/sccm/core/clients/manage/upgrade/test-client-upgrades)을 참조하세요.

**서비스 기간을 사용하여 사이트 서버에서 업데이트를 설치하는 시기를 제어하도록 계획:**   
서비스 기간을 사용하여 사이트 서버에 업데이트를 설치할 수 있는 기간을 정의할 수 있습니다.

이를 통해 계층의 사이트에서 업데이트를 설치하는 시기를 제어할 수 있습니다. 1606 이전 버전에서는 서비스 창을 유지 관리 창이라고 했습니다. 자세한 내용은 [사이트 서버에 대한 서비스 기간](/sccm/core/servers/manage/service-windows)을 참조하세요.

**설치 필수 구성 요소 검사기 실행:**   
업데이트가 콘솔에 **사용 가능**으로 표시되는 경우 업데이트를 설치하기 전에 독립적으로 필수 구성 요소 검사기를 실행할 수 있습니다. 사이트에 업데이트를 설치할 때 필수 조건 검사가 다시 실행됩니다.

콘솔에서 필수 구성 요소 검사를 실행 하려면 **관리 > 개요 > 클라우드 서비스 > 업데이트 및 서비스**로 이동합니다. 다음으로 **Configuration Manager 1610 업데이트 패키지**를 마우스 오른쪽 단추로 클릭한 후 **필수 구성 요소 검사 실행**을 선택합니다.

필수 구성 요소 검사를 시작 및 모니터링하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates) 항목에서 **3단계: 업데이트를 설치하기 전에 필수 구성 요소 검사기 실행**을 참조하세요.

> [!IMPORTANT]  
> 필수 조건 검사가 독립적으로 또는 업데이트 설치의 일부로 실행되면 프로세스에서 사이트 유지 관리 작업에 사용되는 일부 제품 소스 파일을 업데이트합니다. 따라서 필수 구성 요소 검사기를 실행한 후 1610 업데이트를 설치하기 전에 사이트 유지 관리 작업을 수행해야 하는 경우 사이트 서버의 CD.Latest 폴더에서 **Setupwpf.exe**(Configuration Manager 설치 프로그램)를 실행합니다.

**사이트 업데이트:**   
이제 계층 구조에 대한 업데이트 설치를 시작할 수 있습니다. 업데이트 설치에 대한 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)를 참조하세요.

각 사이트에 대한 일상적인 업무 시간 외(업데이트를 설치하는 프로세스와 사이트 구성 요소 및 사이트 시스템 역할을 다시 설치하는 작업이 비즈니스 운영에 가장 영향을 덜 주는 시기)에 업데이트를 설치하도록 계획하는 것이 좋습니다.

자세한 내용은 [System Center Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.

