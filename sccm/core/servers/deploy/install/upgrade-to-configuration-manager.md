---
title: 현재 분기로 업그레이드
titleSuffix: Configuration Manager
description: System Center 2012 Configuration Manager를 실행하는 사이트 및 계층 구조에서 현재 위치 업그레이드를 성공적으로 실행하기 위한 단계를 알아봅니다.
ms.date: 08/16/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e5799d35c8820379d42571b527b870fa7efb4252
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70888911"
---
# <a name="upgrade-to-configuration-manager-current-branch"></a>Configuration Manager 현재 분기로 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center 2012 Configuration Manager를 실행하는 사이트 및 계층 구조에서 Configuration Manager 현재 분기로 현재 위치 업그레이드를 실행하세요. System Center 2012 Configuration Manager에서 업그레이드하려면 먼저 사이트를 준비해야 합니다. 이 준비에서 성공적인 업그레이드에 방해가 될 수 있는 특정 구성을 제거해야 합니다. 그런 다음, 관련된 사이트가 두 개 이상일 경우 업그레이드 순서를 따릅니다.  

> [!TIP]  
> Configuration Manager 사이트 및 계층 인프라를 관리할 때 *업그레이드*, *업데이트* 및 *설치*라는 용어는 세 가지 별도의 개념을 설명하는 데 사용됩니다. 각 용어가 어떻게 사용되는지 알아보려면 [업그레이드, 업데이트 및 설치 정보](/sccm/core/understand/upgrade-update-install)를 참조하세요.



## <a name="bkmk_path"></a> 현재 위치 업그레이드 경로  

다음 옵션은 현재 지원되는 현재 위치 업그레이드 경로입니다.


### <a name="upgrade-to-version-1902"></a>버전 1902로 업그레이드

다음 제품은 System Center Configuration Manager 버전 1902의 정품 버전으로 업그레이드할 수 있습니다.   
- System Center Configuration Manager 버전 1902의 평가판 설치
- System Center 2012 Configuration Manager 서비스 팩 1
- System Center 2012 Configuration Manager 서비스 팩 2
- System Center 2012 R2 Configuration Manager
- System Center 2012 R2 Configuration Manager 서비스 팩 1

### <a name="upgrade-to-version-1802"></a>버전 1802로 업그레이드
다음 제품은 System Center Configuration Manager 버전 1802의 정품 버전으로 업그레이드할 수 있습니다.   
- System Center Configuration Manager 버전 1802의 평가판 설치
- System Center 2012 Configuration Manager 서비스 팩 1
- System Center 2012 Configuration Manager 서비스 팩 2
- System Center 2012 R2 Configuration Manager
- System Center 2012 R2 Configuration Manager 서비스 팩 1

자세한 내용은 [Configuration Manager 분기 및 라이선스에 대한 자주 묻는 질문](/sccm/core/understand/product-and-licensing-faq)을 참조하세요.

> [!TIP]  
>  System Center 2012 Configuration Manager 버전에서 현재 분기로 업그레이드하는 경우 업그레이드 프로세스를 효율적으로 수행할 수 있습니다. 자세한 내용은 다음을 참조하세요.  
>   
> - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)  
> - [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)  


### <a name="unsupported-paths"></a>지원되지 않는 경로

다음 경로 지원되지 않습니다.

- Technical Preview 분기는 정식 라이선스 설치로 업그레이드할 수 없습니다. Technical Preview 버전은 Technical Preview의 이후 버전으로만 업그레이드할 수 있습니다.  

- Technical Preview에서 정식 라이선스 버전으로 마이그레이션할 수 없습니다.  



##  <a name="bkmk_checklist"></a> 업그레이드 검사 목록  

다음 검사 목록은 Configuration Manager로의 성공적인 업그레이드를 계획하는 데 도움이 됩니다.  


### <a name="before-you-upgrade"></a>업그레이드하기 전에  

Configuration Manager로 업그레이드하기 전에 다음 단계를 검토하세요.


#### <a name="review-your-system-center-2012-configuration-manager-environment"></a>System Center 2012 Configuration Manager 환경 검토
다음 Microsoft 지원 문서에 설명된 대로 문제를 해결하세요. [Configuration Manager 클라이언트가 다시 시도 작업 되풀이로 인해 5시간 마다 재설치되고 의도치 않게 클라이언트 업그레이드가 발생할 수 있습니다](https://support.microsoft.com/help/4018655)에 설명된 대로 문제를 해결합니다.

#### <a name="make-sure-your-environment-meets-the-supported-configurations"></a>환경이 지원되는 구성을 충족하는지 확인

- 사이트 시스템 역할을 호스트하는 데 사용 중인 서버 OS 버전을 검토합니다.  

    - System Center 2012 Configuration Manager가 지원하는 일부 이전 운영 체제가 Configuration Manager 현재 분기에서 지원되지 않습니다. 업그레이드하기 전에 해당 OS 버전에서 사이트 시스템 역할을 제거하세요. 자세한 내용은 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)를 참조하세요.   

    - Configuration Manager의 필수 조건 검사기는 사이트 서버 또는 원격 사이트 시스템의 사이트 시스템 역할에 대한 필수 조건을 확인하지 않습니다.  

- 사이트 시스템 역할을 호스트하는 각 컴퓨터에 대한 필수 조건을 검토합니다. 예를 들어 OS 배포를 위해 Configuration Manager에서는 Windows 10 ADK(평가 및 배포 키트)를 사용합니다. 설치 프로그램을 실행하기 전에 사이트 서버와 SMS 공급자 인스턴스가 실행되는 각 컴퓨터에 Windows 10 ADK를 다운로드하고 설치해야 합니다.  

지원되는 플랫폼과 필수 구성 요소 구성에 대한 자세한 내용은 [지원되는 구성](/sccm/core/plan-design/configs/supported-configurations)을 참조하세요.  

Configuration Manager에서 Windows ADK를 사용하는 방법에 대한 자세한 내용은 [OS 배포에 대한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

#### <a name="review-the-site-and-hierarchy-status-and-verify-that-there-are-no-unresolved-issues"></a>사이트 및 계층 구조 상태를 검토하고 해결되지 않은 문제가 있는지 확인:
사이트를 업그레이드하기 전에 원격 컴퓨터에 설치된 사이트 서버, 사이트 데이터베이스 서버 및 사이트 시스템 역할의 모든 작동 문제를 해결해야 합니다. 기존 작동 문제로 인해 사이트 업그레이드가 실패할 수 있습니다.  

#### <a name="install-all-applicable-critical-updates-for-operating-systems-on-computers-that-host-the-site-the-site-database-server-and-remote-site-system-roles"></a>사이트, 사이트 데이터베이스 서버 및 원격 사이트 시스템 역할을 호스트하는 컴퓨터에 모든 해당 중요 운영 체제 업데이트 설치:
사이트를 업그레이드하기 전에 각 해당 사이트 시스템에 대한 중요한 업데이트를 설치합니다. 설치하는 업데이트에 다시 시작이 필요한 경우 서비스 팩 업데이트를 시작하기 전에 해당 컴퓨터를 다시 시작합니다.  

#### <a name="uninstall-the-site-system-roles-not-supported-by-configuration-manager"></a>Configuration Manager에서 지원하지 않는 사이트 시스템 역할을 제거
다음 사이트 시스템 역할은 Configuration Manager에서 더 이상 사용되지 않습니다. System Center 2012 Configuration Manager에서 업그레이드하기 전에 제거하세요.  

- 대역 외 관리 지점  

- 시스템 상태 검사기 지점  

#### <a name="disable-database-replicas-for-management-points-at-primary-sites"></a>기본 사이트의 관리 지점에 데이터베이스 복제본을 사용하지 않도록 설정
Configuration Manager에서 관리 지점에 대한 데이터베이스 복제본이 있는 기본 사이트를 업그레이드할 수 없습니다. 데이터베이스 복제를 사용하지 않도록 설정한 후 다음을 수행합니다.  

- 데이터베이스 업그레이드를 테스트하기 위해 사이트 데이터베이스 백업 만들기  

- 프로덕션 사이트를 System Center Configuration Manager로 업그레이드  

자세한 내용은 다음 아티클을 참조하세요.  

- System Center 2012 Configuration Manager: [관리 지점에 대한 데이터베이스 복제본 구성](/sccm/core/servers/deploy/configure/database-replicas-for-management-points#BKMK_DBReplica_Config)  

- Configuration Manager 현재 분기: [관리 지점용 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)  

#### <a name="reconfigure-software-update-points-that-use-nlb"></a>NLB를 사용하는 소프트웨어 업데이트 지점 다시 구성
Configuration Manager에서는 NLB(네트워크 부하 분산) 클러스터를 사용하는 사이트를 소프트웨어 업데이트 지점을 호스트하도록 업그레이드할 수 없습니다.  

소프트웨어 업데이트 지점에 NLB 클러스터를 사용하는 경우 PowerShell을 사용하여 NLB 클러스터를 제거하세요. (System Center 2012 Configuration Manager SP1부터 NLB 클러스터를 구성할 수 있는 옵션이 Configuration Manager 콘솔에 없음)  

#### <a name="disable-all-site-maintenance-tasks-at-each-site-for-the-duration-of-that-sites-upgrade"></a>해당 사이트를 업그레이드하는 동안 각 사이트에서 모든 사이트 유지 관리 작업을 사용하지 않도록 설정
Configuration Manager로 업그레이드하기 전에 업그레이드 프로세스가 활성 상태인 동안 실행될 수 있는 모든 사이트 유지 관리 작업을 사용하지 않도록 설정합니다. 이러한 작업의 일부 예는 다음과 같습니다.  

- 백업 사이트 서버  
- 오래된 클라이언트 작업 삭제  
- 오래된 검색 데이터 삭제  

업그레이드 프로세스 동안 사이트 데이터베이스 유지 관리 작업을 실행하면 사이트 업그레이드에 실패할 수 있습니다.  

작업을 사용하지 않도록 설정하기 전에 작업 일정을 기록하세요. 그래야 사이트 업그레이드 완료 후에 해당 구성을 복원할 수 있습니다. 

사이트 유지 관리 작업에 대한 자세한 내용은 다음 문서를 참조하세요.  

- System Center 2012 Configuration Manager: [사이트 작업에 대한 계획](/sccm/core/plan-design/hierarchy/plan-for-the-site-database)  

- Configuration Manager 현재 분기: [유지 관리 작업에 대한 참조](/sccm/core/servers/manage/reference-for-maintenance-tasks)  

#### <a name="run-setup-prerequisite-checker"></a>설치 필수 구성 요소 검사기 실행
사이트를 업그레이드하기 전에 설치 프로그램과 별개로 **필수 구성 요소 검사기**를 실행하여 사이트가 필수 조건을 충족하는지 확인합니다. 나중에 사이트를 업그레이드하면 필수 구성 요소 검사기가 다시 실행됩니다.  

2016년 10월 릴리스의 버전 1606 기준 미디어를 사용하는 경우 독립적인 필수 구성 요소 검사에서 Configuration Manager의 현재 분기 및 LTSB(장기 서비스 분기) 둘 다로 업그레이드하기 위해 사이트를 평가합니다. 일부 기능은 LTSB에서 지원되지 않으므로 *ConfigMgrPrereq.log*에 다음 예와 유사한 항목이 표시될 수 있습니다.
- `INFO: The site is a LTSB edition.`
- `Unsupported site system role 'Asset Intelligence synchronization point' for the LTSB edition;    Error;    Configuration Manager has detected that the 'Asset Intelligence synchronization point' is installed. Asset Intelligence is not supported on the LTSB edition. You must uninstall the Asset Intelligence synchronization point site system role before you can continue.`

현재 분기로 업그레이드하려는 경우 LTSB 버전에 대한 오류를 무시해도 됩니다. 이러한 오류는 LTSB로 업그레이드하려는 경우에만 적용됩니다.

나중에 Configuration Manager 설치 프로그램을 실행하여 업그레이드를 수행할 때 필수 조건 검사가 다시 실행되고, (현재 분기 또는 LTSB) 설치를 위해 선택하는 Configuration Manager의 분기를 기준으로 사이트가 평가됩니다. 현재 분기로 업그레이드하는 경우 LTSB에서 지원되지 않는 기능에 대한 검사는 실행되지 않습니다.

자세한 내용은 [필수 조건 검사기](/sccm/core/servers/deploy/install/prerequisite-checker)와 [필수 조건 검사 목록](/sccm/core/servers/deploy/install/list-of-prerequisite-checks)을 참조하세요.  

#### <a name="download-prerequisite-files-and-redistributable-files-for-configuration-manager"></a>Configuration Manager에 대한 필수 조건 파일 및 재배포 가능 파일 다운로드
**설치 다운로더**를 사용하여 필수 조건 재배포 가능 파일, 언어 팩 및 Configuration Manager의 최신 제품 업데이트를 다운로드합니다.  

자세한 내용은 [설치 다운로더](/sccm/core/servers/deploy/install/setup-downloader)를 참조하세요.  

#### <a name="plan-to-manage-server-and-client-languages"></a>서버 및 클라이언트 언어 관리 계획
사이트를 업그레이드할 때 사이트 업그레이드는 업그레이드하는 동안 선택한 언어 팩 버전만 설치합니다.  

- 설치 프로그램이 사이트의 현재 언어 구성을 검토한 다음, 이전에 다운로드한 필수 조건 파일을 저장한 폴더에서 사용 가능한 언어 팩을 식별합니다.  

- 현재 서버와 클라이언트 언어 팩의 선택을 확인하거나 언어 지원을 추가하거나 제거하여 선택 항목을 변경할 수 있습니다.  

- 설치 프로그램을 실행할 때 사용할 수 있는 언어 팩만 선택할 수 있습니다.  

> [!NOTE]  
> System Center 2012 Configuration Manager의 언어 팩을 사용하여 Configuration Manager 현재 분기 사이트에 언어를 사용하도록 설정할 수 없습니다.  

언어 팩에 대한 자세한 내용은 [언어 팩](/sccm/core/servers/deploy/install/language-packs)을 참조하세요.  

#### <a name="review-considerations-for-site-upgrades"></a>사이트 업그레이드 고려 사항 검토
사이트를 업그레이드하는 경우 일부 기능과 구성이 기본 구성으로 다시 설정됩니다. 이러한 변경 및 관련 변경을 준비하는 데 도움이 필요한 경우 [업그레이드할 때의 고려 사항](#bkmk_considerations)을 참조하세요.  

#### <a name="create-a-backup-of-the-site-database-at-the-central-administration-site-and-primary-sites"></a>중앙 관리 사이트와 기본 사이트에서 사이트 데이터베이스 백업 만들기
사이트를 업그레이드하기 전에 사이트 데이터베이스를 백업하여 재해 복구에 사용할 백업을 갖추어야 합니다.  

자세한 내용은 [백업 및 복구](/sccm/core/servers/manage/backup-and-recovery)를 참조하세요.  

#### <a name="back-up-a-customized-configurationmof-file"></a>사용자 지정된 Configuration.mof 파일 백업
사용자 지정된 Configuration.mof 파일을 사용하여 하드웨어 인벤토리와 함께 사용하는 데이터 클래스를 정의하는 경우 이 파일의 백업을 만듭니다. 업그레이드한 후 사이트에 이 파일을 복원합니다. 자세한 내용은 [하드웨어 인벤토리를 확장하는 방법](/sccm/core/clients/manage/inventory/extend-hardware-inventory)을 참조하세요.  

#### <a name="test-the-database-upgrade-process-on-a-copy-of-the-most-recent-site-database-backup"></a>최신 사이트 데이터베이스 백업의 복사본에서 데이터베이스 업그레이드 프로세스 테스트
Configuration Manager 중앙 관리 사이트 또는 기본 사이트를 업그레이드하기 전에 사이트 데이터베이스 복사본을 사용하여 사이트 데이터베이스 업그레이드 프로세스를 테스트합니다.  

- 사이트 데이터베이스 업그레이드 프로세스를 테스트합니다. 사이트를 업그레이드할 때 사이트 데이터베이스가 수정될 수 있습니다.  

- 데이터베이스 업그레이드 테스트를 반드시 수행해야 하는 것은 아니지만, 수행할 경우 프로덕션 데이터베이스가 영향을 받기 전에 업그레이드 문제를 파악할 수 있습니다.  

- 사이트 데이터베이스 업그레이드에 실패하면 사이트 데이터베이스가 작동하지 않을 수 있고, 기능을 복원하기 위해 사이트 복구가 필요할 수도 있습니다.  

- 사이트 데이터베이스는 계층 구조의 여러 사이트 간에 공유되지만 사이트를 업그레이드하기 전에 각 해당 사이트에서 데이터베이스를 테스트합니다.  

- 기본 사이트의 관리 지점에 데이터베이스 복제본을 사용할 경우 사이트 데이터베이스 백업을 만들기 전에 복제를 사용하지 않도록 설정합니다.  

Configuration Manager는 보조 사이트의 백업과 보조 사이트 데이터베이스의 테스트 업그레이드를 지원하지 않습니다.  

프로덕션 사이트 데이터베이스에서 테스트 데이터베이스 업그레이드를 실행하는 것은 지원되지 않습니다. 이렇게 하면 사이트 데이터베이스가 업그레이드되어 사이트가 작동하지 않을 수 있습니다.  

자세한 내용은 [사이트 데이터베이스 업그레이드 테스트](#bkmk_test)항목을 참조하세요.  

#### <a name="restart-the-site-server-and-each-computer-that-hosts-a-site-system-role"></a>사이트 서버 및 사이트 시스템 역할을 호스트하는 각 컴퓨터 다시 시작
이 작업을 수행하여 최신 업그레이드 설치 또는 필수 구성 요소에서 보류된 작업이 없는지 확인합니다.  

#### <a name="upgrade-sites"></a>사이트 업그레이드
계층 구조의 최상위 사이트부터 시작하여 Configuration Manager 원본 미디어에서 Setup.exe를 실행합니다.  

최상위 사이트 업그레이드 후 각 하위 사이트의 업그레이드를 시작할 수 있습니다. 각 사이트의 업그레이드를 완료한 후에 다음 사이트의 업그레이드를 시작합니다.  

계층 구조의 모든 사이트가 Configuration Manager로 업그레이드될 때까지 계층 구조는 혼합 버전 모드로 작동합니다.  

업그레이드를 실행하는 방법에 대한 자세한 내용은 [사이트 업그레이드](#bkmk_upgrade)를 참조하세요.  


### <a name="after-you-upgrade"></a>업그레이드한 후  

Configuration Manager로 업그레이드한 후 다음 단계를 검토하세요.

#### <a name="upgrade-stand-alone-configuration-manager-consoles"></a>독립 실행형 Configuration Manager 콘솔 업그레이드
기본적으로 중앙 관리 사이트 또는 기본 사이트를 업그레이드하면 사이트 서버에 설치된 Configuration Manager 콘솔도 업그레이드됩니다. 사이트 서버가 아닌 컴퓨터에 설치된 각 콘솔은 수동으로 업그레이드합니다.  

> [!TIP]  
> 업그레이드를 시작하기 전에 열려 있는 각 콘솔을 닫습니다.  

자세한 내용은 [Configuration Manager 콘솔 설치](/sccm/core/servers/deploy/install/install-consoles)를 참조하세요.  

#### <a name="reconfigure-database-replicas-for-management-points-at-primary-sites"></a>기본 사이트의 관리 지점에 데이터베이스 복제본 다시 구성
기본 사이트의 관리 지점에 데이터베이스 복제본을 사용하는 경우 해당 사이트를 업그레이드하기 전에 데이터베이스 복제본을 제거합니다. 기본 사이트를 업그레이드한 후에는 관리 지점에 대해 데이터베이스 복제본을 다시 구성합니다.   

자세한 내용은 [관리 지점에 대한 데이터베이스 복제본](/sccm/core/servers/deploy/configure/database-replicas-for-management-points)을 참조하세요.  

#### <a name="reconfigure-any-database-maintenance-tasks-you-disabled-before-the-upgrade"></a>업그레이드 전에 사용하지 않도록 설정한 데이터베이스 유지 관리 작업 다시 구성
업그레이드 전에 사이트에서 데이터베이스 [유지 관리 작업](/sccm/core/servers/manage/reference-for-maintenance-tasks)을 사용하지 않도록 설정했으면 업그레이드 전에 사용하던 설정과 같은 설정을 사용하여 사이트에서 해당 작업을 다시 구성합니다.  

#### <a name="upgrade-clients"></a>클라이언트 업그레이드
모든 사이트를 Configuration Manager로 업그레이드한 후 클라이언트를 업그레이드합니다.  

클라이언트를 업그레이드할 때에는 현재 클라이언트 소프트웨어가 제거되고 새 클라이언트 소프트웨어 버전이 설치됩니다. 클라이언트를 업그레이드하기 위해 Configuration Manager에서 지원하는 모든 방법을 사용할 수 있습니다.  

> [!TIP]  
> 계층 구조의 최상위 사이트를 업그레이드하면 계층 구조의 각 배포 지점에 있는 클라이언트 설치 패키지도 업데이트됩니다. 기본 사이트를 업그레이드하면 해당 기본 사이트에서 제공되는 클라이언트 업그레이드 패키지가 업데이트됩니다.  

자세한 내용은 [Windows 컴퓨터에 대한 클라이언트를 업그레이드하는 방법](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers)을 참조하세요.  



## <a name="bkmk_considerations"></a> 업그레이드할 때의 고려 사항  


### <a name="automatic-actions"></a>자동 작업

Configuration Manager로 업그레이드하는 경우 다음 작업이 자동으로 수행됩니다.  

- 사이트 다시 설정. 이 작업에는 모든 사이트 시스템 역할의 다시 설치가 포함됩니다.  

- 사이트가 계층의 최상위 사이트인 경우 계층의 각 배포 지점에서 클라이언트 설치 패키지를 업데이트합니다. 이 사이트는 Windows 평가 및 배포 키트 10에 포함된 새 Windows PE 버전을 사용하도록 기본 부팅 이미지도 업데이트합니다. 그러나 업그레이드 시 이미지 배포와 함께 사용할 기존 미디어는 업그레이드되지 않습니다.  

- 사이트가 기본 사이트인 경우 해당 사이트에 대한 클라이언트 업그레이드 패키지를 업데이트합니다.  


### <a name="manual-actions-after-an-upgrade"></a>업그레이드 후 수동 작업

사이트를 업그레이드한 후에는 다음 작업을 수행해야 합니다.  

- 각 기본 사이트에 할당된 클라이언트에서 새 클라이언트 버전을 업그레이드하고 설치하는지 확인합니다.  

- 해당 사이트에 연결되고 사이트 서버에서 원격인 컴퓨터에서 실행되는 각 Configuration Manager 콘솔을 업그레이드합니다.  

- 관리 지점에 데이터베이스 복제본을 사용하는 기본 사이트에서 데이터베이스 복제본을 다시 구성합니다.  

- 사이트 업그레이드 후 CD, DVD 또는 USB 플래시 드라이브용 ISO 파일처럼 실제 미디어를 수동으로 업그레이드합니다. 여기에는 하드웨어 공급업체에 제공된 사전 준비된 미디어도 포함됩니다. 사이트 업그레이드에서는 기본 부팅 이미지를 업데이트하지만 이러한 미디어 파일 또는 Configuration Manager 외부에서 사용되는 디바이스를 업그레이드할 수는 없습니다.  

- 이전 버전의 Windows PE가 필요하지 않은 경우 사용자 지정 부팅 이미지를 업데이트하도록 계획합니다.  


### <a name="actions-that-affect-configurations-and-settings"></a>구성 및 설정에 영향을 주는 작업**   

사이트가 Configuration Manager로 업그레이드되면 업그레이드 후 일부 구성 및 설정이 유지되지 않습니다. 또한 일부 구성은 새 기본값으로 설정됩니다. 다음 목록에는 유지되지 않거나 변경되는 설정이 있습니다.  

- **소프트웨어 센터**  
    다음 소프트웨어 센터 항목이 기본값으로 다시 설정됩니다.  

    - **작업 정보** 가 월요일부터 금요일 **오전 5:00** 부터 **오후 10:00** 의 업무 시간으로 다시 설정됩니다.  

    - **컴퓨터 유지 관리** 의 값이 **내 컴퓨터가 프레젠테이션 모드일 때 소프트웨어 센터 활동 일시 중단**으로 설정됩니다.  
    
    - **원격 제어** 의 값이 컴퓨터에 할당된 클라이언트 설정의 값으로 설정됩니다.  

- **소프트웨어 업데이트 요약 일정**: 소프트웨어 업데이트 또는 소프트웨어 업데이트 그룹의 사용자 지정 요약 일정이 기본값인 1시간으로 다시 설정됩니다. 업그레이드가 완료된 후에는 사용자 지정 요약 값을 필요한 주기로 다시 설정합니다.  



## <a name="bkmk_test"></a> 사이트 데이터베이스 업그레이드 테스트  

다음 정보는 System Center 2012 Configuration Manager 등의 이전 버전을 Configuration Manager 현재 분기로 업그레이드하는 경우에만 적용됩니다.

사이트를 업그레이드하기 전에 해당 사이트의 데이터베이스 사본으로 업그레이드를 테스트합니다.  

데이터베이스에서 업그레이드를 테스트하려면 먼저 Configuration Manager 사이트를 호스트하지 않는 SQL Server의 인스턴스로 사이트 데이터베이스 사본을 복원합니다. 데이터베이스 사본을 호스트하는 데 사용되는 SQL Server 버전은 Configuration Manager에서 지원하는 SQL Server 버전이어야 합니다.  

사이트 데이터베이스를 복원했으면 SQL Server 컴퓨터에서 Configuration Manager의 원본 미디어 폴더에서 Configuration Manager 설치 프로그램을 실행합니다. `/TESTDBUPGRADE` 명령줄 옵션을 사용합니다.  

자세한 내용은 다음 아티클을 참조하세요.

- [Configuration Manager 사이트 백업](/sccm/core/servers/manage/backup-and-recovery)  

- [설치용 명령줄 옵션](/sccm/core/servers/deploy/install/command-line-options-for-setup#bkmk_setup)  

- [SQL Server 버전 지원](/sccm/core/plan-design/configs/support-for-sql-server-versions)  

> [!TIP]  
> Microsoft Intune을 Configuration Manager와 통합하는 경우:  
>   
>  5일 이상 경과한 사이트 데이터베이스 복사본을 사용하여 데이터베이스 업그레이드 테스트를 실행할 경우 다음 메시지 중 하나가 표시될 수 있습니다.  
>   
> - 경고: 업그레이드를 실행하면 클라우드에 전체 동기화가 강제로 적용됩니다.  
> - 오류: 데이터베이스 업그레이드를 실행하면 클라우드에 전체 동기화가 강제로 적용됩니다.  
>   
> 데이터베이스 업그레이드를 테스트하는 동안에는 둘 다 무시해도 됩니다. 이 경고와 오류는 테스트 업그레이드 실패 또는 문제를 나타내는 것은 아닙니다. 두 메시지는 실제 업그레이드 중에 **클라우드** 데이터베이스 복제 그룹의 데이터가 Microsoft Intune과 동기화될 수 있음을 나타냅니다.  


### <a name="test-a-site-database-for-upgrade"></a>사이트 데이터베이스 업그레이드 테스트  

업그레이드할 각 중앙 관리 사이트 및 기본 사이트에서 다음 절차를 수행하세요.  

1. 사이트 데이터베이스의 사본을 만듭니다. 그런 다음, 사이트 데이터베이스와 같은 버전을 사용하고 Configuration Manager 사이트를 호스트하지 않는 SQL Server의 인스턴스로 해당 사본을 복원합니다. 예를 들어 SQL Server Enterprise Edition의 인스턴스에서 사이트 데이터베이스를 실행하는 경우 마찬가지로 SQL Server Enterprise Edition을 실행하는 SQL Server의 인스턴스로 데이터베이스를 복원해야 합니다.  

2. 데이터베이스 사본을 복원한 후에 Configuration Manager 현재 분기의 원본 미디어에서 설치 프로그램을 실행합니다. 설치 프로그램을 실행할 때 `/TESTDBUPGRADE` 명령줄 옵션을 사용합니다. 데이터베이스 사본을 호스트하는 SQL Server 인스턴스가 기본 인스턴스가 아닌 경우 명령줄 인수도 제공하여 사이트 데이터베이스 사본을 호스트하는 인스턴스를 식별합니다.  

    예를 들어 SMS_ABC라는 데이터베이스 이름으로 사이트 데이터베이스를 업그레이드할 계획이라면 이 사이트 데이터베이스의 사본을 인스턴스 이름이 DBTest인 지원되는 SQL Server 인스턴스로 복원합니다. 사이트 데이터베이스의 이 사본을 테스트하려면 명령줄 `Setup.exe /TESTDBUPGRADE DBtest\CM_ABC`를 사용하세요.  

    Setup.exe는 Configuration Manager 원본 미디어의 `SMSSETUP\BIN\X64` 위치에 있습니다.  

3. 데이터베이스 업그레이드 테스트를 실행하는 SQL Server 인스턴스에서 시스템 드라이브 루트에 있는 ConfigMgrSetup.log를 보고 진행률 및 성공 여부를 모니터링합니다.  

    - 테스트 업그레이드가 실패하면 사이트 데이터베이스 업그레이드 실패와 관련된 문제를 해결합니다. 그런 다음 사이트 데이터베이스의 새 백업을 만들고 사이트 데이터베이스의 새 복사본에 대한 업그레이드를 테스트합니다.  

    - 프로세스가 성공한 후에는 데이터베이스 사본을 삭제할 수 있습니다.  

        > [!NOTE]  
        > 테스트 업그레이드에 사용하는 사이트 데이터베이스의 사본을 어떤 사이트에서나 사이트 데이터베이스로 사용하도록 복원할 수는 없습니다.  

사이트 데이터베이스의 사본을 업그레이드한 후에 Configuration Manager 사이트 및 해당 사이트 데이터베이스를 계속 업그레이드합니다.  



## <a name="bkmk_upgrade"></a> 사이트 업그레이드  

다음 작업을 완료했으면 Configuration Manager 사이트를 업그레이드할 준비가 되었습니다.
- 사이트의 업그레이드 전 구성
- 데이터베이스 사본에서 사이트 데이터베이스 업그레이드 테스트
- 설치하려는 버전에 대한 필수 파일과 언어 팩 다운로드

계층에서 사이트를 업그레이드하는 경우 먼저 계층의 최상위 사이트를 업그레이드합니다. 이 최상위 사이트는 중앙 관리 사이트나 독립 실행형 기본 사이트 중 하나입니다. 중앙 관리 사이트의 업그레이드를 완료한 후에는 하위 기본 사이트를 원하는 순서대로 업그레이드할 수 있습니다. 기본 사이트를 업그레이드한 후에는 사이트의 하위 보조 사이트를 업그레이드할 수도 있고 보조 사이트를 업그레이드하기 전에 다른 기본 사이트를 업그레이드할 수도 있습니다.  

중앙 관리 사이트 또는 기본 사이트를 업그레이드하려면 Configuration Manager 원본 미디어에서 설치 프로그램을 실행합니다. 보조 사이트 업그레이드에는 설치 프로그램을 실행하지 않습니다. 대신 기본 상위 사이트의 업그레이드를 완료한 후에 Configuration Manager 콘솔을 사용하여 보조 사이트를 업그레이드합니다.  

사이트를 업그레이드하기 전에, 사이트 서버에 있는 Configuration Manager 콘솔을 사이트 업그레이드가 완료될 때까지 닫아 둡니다. 사이트 서버가 아닌 컴퓨터에서 실행되는 각 Configuration Manager 콘솔도 닫습니다. 사이트 업그레이드가 완료된 후 콘솔에 다시 연결할 수 있습니다. 그러나 Configuration Manager 콘솔을 새 버전의 Configuration Manager로 업그레이드할 때까지는 새 버전의 Configuration Manager에서 사용할 수 있는 일부 개체 및 정보를 해당 콘솔에 표시할 수 없습니다.  


### <a name="upgrade-a-central-administration-site-or-primary-site"></a>중앙 관리 사이트나 기본 사이트 업그레이드  

1. 설치 프로그램을 실행하는 사용자에게 다음 보안 권한이 있는지 확인합니다.  

    - 사이트 서버에 대한 로컬 **관리자** 권한  

    - 사이트 데이터베이스 서버가 사이트 서버에서 원격인 경우 그에 대한 로컬 **관리자** 권한  

2. 사이트 서버에서 `<ConfigMgSourceMedia>\SMSSETUP\BIN\X64\Setup.exe` 프로그램을 엽니다. 이 작업으로 Configuration Manager 설치 마법사가 열립니다.  

3. **시작 하기 전에** 페이지에서 정보를 읽은 후 **다음**을 선택합니다.  

4. **시작** 페이지에서 **이 Configuration Manager 사이트 업그레이드**를 선택하고 **다음**을 선택합니다.  

5. **제품 키** 페이지에서 다음을 수행합니다.  

    이전에 Configuration Manager 평가 버전을 설치한 경우 **이 제품의 라이선스 버전 설치**를 선택할 수 있습니다. 그런 다음 Configuration Manager 전체 설치를 위한 제품 키를 입력하면 사이트가 정식 버전으로 변환됩니다.  

    사용권 계약의 **Software Assurance 만료 날짜**를 해당 날짜의 편리한 미리 알림으로 지정할 수도 있습니다. 설치 중에 이 값을 입력하지 않는 경우 나중에 Configuration Manager 콘솔 내에서 지정할 수 있습니다.  

    > [!NOTE]  
    > Microsoft는 입력된 만료 날짜의 유효성을 검사하지 않으며 이 날짜를 라이선스 유효성 검사에 사용하지 않습니다. 이 날짜는 만료 날짜 미리 알림으로 사용할 수 있습니다. Configuration Manager는 온라인에서 제공되는 새 소프트웨어 업데이트를 정기적으로 확인하며 이러한 추가 업데이트를 사용할 수 있으려면 Software Assurance 라이선스 상태는 현재여야 합니다.    

    자세한 내용은 [라이선스 및 분기](/sccm/core/understand/learn-more-editions)를 참조하세요.

6. **Microsoft 소프트웨어 사용 조건** 페이지에서 사용 조건을 읽고 동의한 후 **다음**을 선택합니다.  

7. **필수 구성 요소 사용권** 페이지에서 필수 구성 요소 소프트웨어의 사용 조건을 읽고 동의한 후 **다음**을 선택합니다. 소프트웨어가 필요한 경우 설치 프로그램이 사이트 시스템 또는 클라이언트에 자동으로 소프트웨어를 설치합니다. 모든 확인란에 동의해야 다음 페이지로 진행할 수 있습니다.  

8. **필수 다운로드** 페이지에서 이전에 다운로드한 파일을 사용할지 아니면 설치 프로그램이 인터넷에서 최신 콘텐츠를 다운로드하는지를 지정합니다. 이 콘텐츠는 필수 재배포 가능 파일, 언어 팩 및 최신 제품 업데이트를 포함합니다. 설치 다운로더를 사용하여 이전에 파일을 다운로드한 경우 **이전에 다운로드한 파일 사용** 을 선택하고 다운로드 폴더를 지정합니다. 자세한 내용은 [설치 다운로더](/sccm/core/servers/deploy/install/setup-downloader)를 참조하세요.  

    > [!NOTE]  
    > 이전에 다운로드한 파일을 사용하는 경우 다운로드 폴더의 경로에 최신 버전의 파일이 들어 있는지 확인합니다.  

9. **서버 언어 선택** 페이지에서 사이트에 현재 설치된 언어 목록을 봅니다. 이 사이트에서 Configuration Manager 콘솔 및 보고서에 사용할 수 있는 추가 언어를 선택합니다. 이 사이트에서 더 이상 지원하지 않을 언어는 지울 수도 있습니다. 기본적으로 영어가 선택되어 있으며 영어는 제거할 수 없습니다.  

    > [!IMPORTANT]  
    > 각 버전의 Configuration Manager는 이전 버전 Configuration Manager의 언어 팩을 사용할 수 없습니다. 업그레이드하는 Configuration Manager 사이트에서 언어에 대한 지원을 사용하도록 설정하려면 해당 새 버전의 언어 팩 버전을 사용해야 합니다. 예를 들어 System Center 2012 Configuration Manager에서 Configuration Manager 현재 분기로 업그레이드하는 동안 현재 분기 버전의 언어 팩이 다운로드한 필수 조건 파일과 함께 제공되지 않는 경우 해당 언어에 대한 지원을 설치할 수 없습니다.  

10. **클라이언트 언어 선택** 페이지에서 사이트에 현재 설치된 언어 목록을 봅니다. 클라이언트 컴퓨터에 대해 이 사이트에서 사용할 수 있는 다른 언어를 추가로 선택하거나 이 사이트에서 더 이상 지원하지 않으려는 언어를 선택 해제합니다. 모바일 디바이스 클라이언트에 모든 클라이언트 언어를 사용할지 여부를 지정하고 **다음**을 클릭합니다. 기본적으로 영어가 선택되어 있으며 영어는 제거할 수 없습니다.  

11. **설정 요약** 페이지에서 구성을 검토합니다. 준비가 되었으면 **다음**을 선택하여 필수 구성 요소 검사를 시작한 후 사이트 업그레이드를 위한 서버 준비 상태를 확인합니다.  

12. **필수 구성 요소 설치 검사** 페이지에 문제가 나열되지 않으면 **다음**을 선택하여 사이트 및 사이트 시스템 역할을 업그레이드합니다. 

    필수 구성 요소 검사기에서 문제를 발견하면 목록의 해당 항목을 선택하여 문제 해결 방법에 대한 세부 정보를 확인합니다. 설치 프로그램을 계속하기 전에 목록에서 **오류** 상태인 모든 항목을 해결합니다. 문제를 해결한 후 **확인 실행** 을 클릭하여 필수 구성 요소 확인을 다시 시작합니다. 또한 시스템 드라이브의 루트에 있는 ConfigMgrPrereq.log 파일을 열고 필수 구성 요소 검사기 결과를 검토할 수 있습니다. 로그 파일에는 사용자 인터페이스에 표시되지 않은 추가 정보가 포함되어 있습니다. 설치 필수 조건 규칙 및 설명 목록은 [필수 조건 검사기](/sccm/core/servers/deploy/install/list-of-prerequisite-checks)를 참조하세요.

**업그레이드** 페이지에서 설치 프로그램이 전체 진행률 상태를 표시합니다. 핵심 사이트 서버 및 사이트 시스템 설치가 완료되면 마법사를 닫아도 됩니다. 사이트 구성은 백그라운드에서 계속 실행됩니다.  


### <a name="upgrade-a-secondary-site"></a>보조 사이트 업그레이드  

1. 설치 프로그램을 실행하는 관리자에게 다음 보안 권한이 있는지 확인합니다.  

    - 보조 사이트 서버에 대한 로컬 **관리자** 권한  

    - 부모 기본 사이트에 대한 **인프라 관리자** 또는 **전체 관리자** 보안 역할  

    - 보조 사이트의 사이트 데이터베이스에 대한 **SA**(시스템 관리자) 권한  

2. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장한 다음, **사이트** 노드를 선택합니다.  

3. 업그레이드하려는 보조 사이트를 선택합니다. 리본의 **홈** 탭에 있는 **사이트** 그룹에서 **업그레이드**를 선택합니다.  

4. **예**를 선택하여 결정 내용을 확인하고 보조 사이트의 업그레이드를 시작합니다.  

보조 사이트 업그레이드는 백그라운드에서 실행됩니다. 업그레이드가 완료되면 Configuration Manager 콘솔의 상태를 확인합니다. 보조 사이트 서버를 선택한 다음, 리본의 **홈** 탭에 있는 **사이트** 그룹에서 **설치 상태 표시**를 선택합니다.  



## <a name="BKMK_PostUpgrade"></a> 업그레이드 후 작업  

사이트를 업그레이드한 후에는 업그레이드를 마치거나 사이트를 다시 구성하기 위해 추가 작업을 완료해야 할 수 있습니다. 이러한 작업에는 다음 항목이 포함될 수 있습니다. 
- Configuration Manager 클라이언트 업그레이드
- Configuration Manager 콘솔 업그레이드
- 관리 지점에 대한 데이터베이스 복제본 다시 사용
- 업그레이드 후에 유지되지 않지만 사용할 Configuration Manager 기능에 대한 설정 복원  

