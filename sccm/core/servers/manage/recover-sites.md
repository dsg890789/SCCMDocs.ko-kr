---
title: 사이트 복구
titleSuffix: Configuration Manager
description: Configuration Manager의 사이트 복구에 대해 알아봅니다.
ms.date: 08/23/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 19539f4d-1667-4b4c-99a1-9995f12cf5f7
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 594e5a069edbb742cf4348a9b1ef7d4d4da3cf96
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75794327"
---
# <a name="recover-a-configuration-manager-site"></a>Configuration Manager 사이트 복구

*적용 대상: Configuration Manager(현재 분기)*

사이트가 실패하거나 사이트 데이터베이스에서 데이터 손실이 발생한 후에 Configuration Manager 사이트 복구를 실행합니다. 데이터 복구 및 재동기화는 사이트 복구의 핵심 작업으로서 작업 중단을 방지하기 위해 필요합니다.

이 문서의 섹션에서는 Configuration Manager 사이트를 복구하는 데 도움이 될 수 있습니다. 백업을 만들려면 [Configuration Manager의 백업](/sccm/core/servers/manage/backup-and-recovery)을 참조하세요.

## <a name="considerations-before-recovering-a-site"></a>사이트 복구 전 고려 사항

> [!Important]  
> 이 정보는 사이트 복구 시나리오에만 적용됩니다. 온-프레미스 인프라를 업그레이드하고 실패한 사이트를 적극적으로 복구하지 않는 경우 다음 문서의 정보를 검토합니다.
>
> - [온-프레미스 인프라 업그레이드](/sccm/core/servers/manage/upgrade-on-premises-infrastructure)
> - [인프라 수정](/sccm/core/servers/manage/modify-your-infrastructure)

### <a name="prepare-the-server-hardware"></a>서버 하드웨어 준비

<!-- 2841893 -->

기존 구성이 사이트 서버에 존재하지 않아야 합니다. 이전 구성으로 인해 사이트 복구 프로세스 중에 충돌이 발생할 수 있습니다. 서버 하드웨어에는 다음 옵션 중 하나를 사용합니다.

- 일반적 요구 사항 및 복구 요구 사항을 충족하는 새 서버를 사용합니다.

- 디스크를 포맷하고 기존 서버에 OS를 다시 설치합니다. 일반적 요구 사항 및 복구 요구 사항을 충족하는지 확인합니다.

- 정리한 기존 서버 다시 사용

다음 절차 중 하나에 따라 기존 서버를 정리합니다.

#### <a name="clean-an-existing-server-for-site-server-recovery-only"></a>사이트 서버 복구만을 위해 기존 서버 정리

1. SMS 레지스트리 키 삭제: `HKLM\Software\Microsoft\SMS`
2. `SMS`로 시작하는 모든 레지스트리 항목을 `HKLM\System\CurrentControlSet\Services`에서 삭제합니다. 예를 들면 다음과 같습니다.
    - SMS_DISCOVERY_DATA_MANAGER
    - SMS_EXECUTIVE
    - SMS_INBOX_MONITOR
    - SMS_INVENTORY_DATA_LOADER
    - SMS_LAN_SENDER
    - SMS_MP_FILE_DISPATCH_MANAGER
    - SMS_SCHEDULER
    - SMS_SITE_BACKUP
    - SMS_SITE_COMPONENT_MANAGER
    - SMS_SITE_SQL_BACKUP
    - SMS_SITE_VSS_WRITER
    - SMS_SOFTWARE_METERING_PROCESSOR
    - SMS_STATE_SYSTEM
    - SMS_STATUS_MANAGER
    - SMS_WSUS_SYNC_MANAGER
    - SMSvcHost 3.0.0.0
    - SMSvcHost 4.0.0.0
3. Configuration Manager 콘솔 제거
4. 서버 다시 시작
5. 위의 레지스트리 키가 모두 삭제되었는지 확인합니다.

이제 서버에서 Configuration Manager 복원 절차를 수행할 준비가 되었습니다.

#### <a name="clean-an-existing-server-for-site-database-recovery-only"></a>사이트 데이터베이스 복구만을 위해 기존 서버 정리

1. 사이트 데이터베이스를 백업합니다. 또한 WSUS와 같은 다른 지원 데이터베이스를 백업합니다.
2. SQL Server 이름 및 인스턴스 이름 확인
3. SQL Server에서 수동으로 사이트 데이터베이스 삭제
4. SQL Server 다시 시작

이제 서버에서 Configuration Manager 복원 절차를 수행할 준비가 되었습니다.

#### <a name="clean-an-existing-server-for-full-recovery"></a>전체 복구를 위해 기존 서버 정리

1. 사이트 데이터베이스를 백업합니다. 또한 WSUS와 같은 다른 지원 데이터베이스를 백업합니다.
2. 콘텐츠 라이브러리의 복사본 만들기
3. SQL Server에서 수동으로 사이트 데이터베이스 삭제
4. Configuration Manager 사이트 제거
5. Configuration Manager 설치 폴더 및 기타 Configuration Manager 폴더를 수동으로 삭제
6. 서버 다시 시작
7. 콘텐츠 라이브러리 및 WSUS와 같은 기타 데이터베이스 복원

이제 서버에서 Configuration Manager 복원 절차를 수행할 준비가 되었습니다.

### <a name="use-a-supported-version-and-same-edition-of-sql-server"></a>지원되는 버전 및 동일한 버전의 SQL Server 사용

<!-- SCCMDocs#751 -->

가능하면 동일한 버전의 SQL Server를 사용합니다. 그러나 데이터베이스를 최신 버전으로 복원하는 것은 지원됩니다.

SQL Server 버전을 변경하지 마세요. Standard Edition에서 Enterprise Edition으로의 복원은 지원되지 않습니다.

추가 SQL Server 구성 요구 사항:

- SQL Server를 **단일 사용자 모드**로 설정할 수 없습니다.
- MDF 및 LDF 파일이 올바른지 확인합니다. 사이트를 복구할 때 파일의 상태는 확인되지 않습니다.  

### <a name="sql-server-always-on-availability-groups"></a>SQL Server Always On 가용성 그룹

SQL Server Always On 가용성 그룹을 사용하여 사이트 데이터베이스를 호스트하는 경우 [SQL Server Always On 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-recovery)에 설명된 대로 복구 계획을 수정합니다.

### <a name="database-replicas"></a>데이터베이스 복제본

데이터베이스 복제본에 대해 구성한 사이트 데이터베이스를 복원한 후 각 복제본을 다시 구성합니다. 데이터베이스 복제본을 사용하기 전에 게시 및 구독을 모두 다시 만듭니다.

## <a name="determine-your-recovery-options"></a>복구 옵션 결정

Configuration Manager 기본 사이트 서버 및 중앙 관리 사이트(CAS) 복구를 수행하려면 **사이트 서버** 및 **사이트 데이터베이스**라는 두 가지 영역을 가장 기본적으로 고려해야 합니다.
다음 섹션은 복구 시나리오에 가장 적합한 옵션을 선택하는 데 도움이 됩니다.

> [!NOTE]  
> Configuration Manager 설치 프로그램이 서버에서 기존 사이트를 검색한 경우 사이트 복구를 시작할 수는 있지만 사이트 서버에 대한 복구 옵션이 제한됩니다. 예를 들어 기존 사이트 서버에서 설치 프로그램을 실행하고 복구를 선택하면, 사이트 데이터베이스 서버를 복구할 수는 있지만 사이트 서버 복구를 위한 옵션은 사용할 수 없습니다.

### <a name="site-server-recovery-options"></a>사이트 서버 복구 옵션

Configuration Manager 설치 폴더 외부에 만든 **CD.Latest** 폴더의 복사본에서 Configuration Manager 설치 프로그램을 시작합니다.  

- 사이트 서버의 **시작** 메뉴에서 설치 프로그램을 실행하는 경우 **사이트 복구** 옵션을 사용할 수 없습니다.  

- 백업을 수행하기 전에 Configuration Manager 콘솔 내에서 업데이트를 설치한 경우 다음 위치의 설치 프로그램을 사용하여 사이트를 다시 설치할 수 없습니다.

  - 설치 미디어
  - Configuration Manager 설치 경로

그런 다음 **사이트 복구** 옵션을 선택합니다. 실패한 사이트 서버에 대해 다음과 같은 복구 옵션을 사용할 수 있습니다.  

#### <a name="recover-the-site-server-using-an-existing-backup"></a>기존 백업을 사용하여 사이트 서버 복구

사이트 오류 전부터 사이트 서버의 Configuration Manager 백업이 있는 경우 이 옵션을 사용합니다. 사이트는 **백업 사이트 서버** 유지 관리 작업의 일부로 이 백업을 만듭니다. 백업된 사이트를 기준으로 사이트가 다시 설치되고 사이트 설정이 구성됩니다.  

#### <a name="reinstall-the-site-server"></a>사이트 서버 다시 설치

이 옵션은 사이트 서버 백업이 없을 때 사용합니다. 사이트 서버가 다시 설치되며, 초기 설치 시 구성한 것처럼 사이트 설정을 지정해야 합니다.  

- 실패한 사이트를 처음 설치했을 때 사용한 것과 동일한 사이트 코드 및 사이트 데이터베이스 이름을 사용합니다.  

- 새 OS 버전을 실행하는 새 컴퓨터에 사이트를 다시 설치할 수 있습니다.  

- 서버는 동일한 호스트 이름 및 원본 사이트 서버의 정규화된 도메인 이름 (FQDN)을 사용해야 합니다.

### <a name="site-database-recovery-options"></a>사이트 데이터베이스 복구 옵션

Configuration Manager 설치 프로그램을 실행할 때 사이트 데이터베이스에 대해 다음과 같은 복구 옵션을 사용할 수 있습니다.  

#### <a name="recover-the-site-database-using-a-backup-set"></a>백업 집합을 사용하여 사이트 데이터베이스 복구

데이터베이스 오류 전부터 사이트 데이터베이스의 Configuration Manager 백업이 있는 경우 이 옵션을 사용합니다. 사이트는 **백업 사이트 서버** 유지 관리 작업의 일부로 이 백업을 만듭니다. 계층 구조에서는 기본 사이트를 복원할 때 복구 프로세스가 마지막 백업 후 사이트 데이터베이스에 수행된 모든 변경을 CAS에서 검색합니다. CAS를 복원할 경우 복구 프로세스는 이러한 변경을 참조 기본 사이트에서 검색합니다. 독립 실행형 기본 사이트에 대한 사이트 데이터베이스를 복구하면 마지막 백업 이후의 사이트 변경 내용은 손실됩니다.  

계층 구조 내 사이트의 사이트 데이터베이스를 복구할 경우 CAS 복구 동작과 기본 사이트 복구 동작이 다릅니다. 이 복구 동작은 마지막 백업이 SQL Server 변경 내용 추적 보존 기간 내에 있는지 여부에 따라서도 다릅니다. 자세한 내용은 이 문서의 [사이트 데이터베이스 복구 시나리오](#site-database-recovery-scenarios) 섹션을 참조하세요.  

> [!NOTE]  
> 백업 집합을 사용하여 사이트 데이터베이스를 복원하도록 선택했지만 사이트 데이터베이스가 이미 존재하는 경우 복구는 실패합니다.  

#### <a name="create-a-new-database-for-this-site"></a>이 사이트에 대한 새 데이터베이스 만들기

이 옵션은 사이트 데이터베이스 백업이 없을 때 사용합니다. 계층에서 복구 프로세스는 새 사이트 데이터베이스를 만듭니다. 자식 기본 사이트를 복원할 때는 CAS에서 복제하여 데이터를 복구합니다. CAS를 복원할 때는 참조 기본 사이트에서 데이터를 복제합니다. 이 옵션은 독립 실행형 기본 사이트 또는 기본 사이트가 없는 CAS를 복구할 경우에는 사용할 수 없습니다.  

#### <a name="use-a-site-database-that-has-been-manually-recovered"></a>수동으로 복구된 사이트 데이터베이스 사용

Configuration Manager 사이트 데이터베이스는 이미 복구했지만 복구 프로세스를 완료해야 하는 경우 이 옵션을 사용합니다.  

- Configuration Manager는 다음 프로세스에서 사이트 데이터베이스를 복구할 수 있습니다.  

  - Configuration Manager 백업 유지 관리 작업  
  - DPM(Data Protection Manager)을 사용하여 사이트 데이터베이스 백업  
  - 다른 백업 프로세스  

    Configuration Manager 외부의 방법을 사용하여 사이트 데이터베이스를 복원한 후에는 설치 프로그램을 실행하고 이 옵션을 선택하여 사이트 데이터베이스 복구를 완료합니다.  

    > [!NOTE]  
    > DPM을 사용하여 사이트 데이터베이스를 백업할 경우, Configuration Manager에서 복원 프로세스를 계속하기 전에 먼저 DPM 프로시저를 사용하여 사이트 데이터베이스를 지정된 위치에 복원하세요. DPM에 대한 자세한 내용은 [Data Protection Manager](https://docs.microsoft.com/system-center/dpm) 문서 라이브러리를 참조하세요.  

- 계층 구조에서는 기본 사이트 데이터베이스를 복구할 때 복구 프로세스가 마지막 백업 후 사이트 데이터베이스에 수행된 모든 변경을 CAS에서 검색합니다. CAS를 복원할 경우 복구 프로세스는 이러한 변경을 참조 기본 사이트에서 검색합니다. 독립 실행형 기본 사이트에 대한 사이트 데이터베이스를 복구하면 마지막 백업 이후의 사이트 변경 내용은 손실됩니다.  

#### <a name="skip-database-recovery"></a>데이터베이스 복구 건너뛰기

이 옵션은 Configuration Manager 사이트 데이터베이스 서버에서 데이터 손실이 발생하지 않았을 때 사용합니다. 이 옵션은 사이트 데이터베이스가 현재 복구 중인 사이트 서버가 아닌 다른 컴퓨터에 있는 경우에만 유효합니다.  

### <a name="sql-server-change-tracking-retention-period"></a>SQL Server 변경 내용 추적 보존 기간

Configuration Manager를 사용하면 SQL Server에서 사이트 데이터베이스에 대한 변경 내용을 추적할 수 있습니다. 변경 내용 추적을 통해 Configuration Manager는 이전 시점 이후에 데이터베이스 테이블에 수행된 변경 내용에 관한 정보를 쿼리할 수 있습니다. 보존 기간은 변경 내용 추적 정보가 보존되는 기간을 지정합니다. 기본적으로 사이트 데이터베이스는 5일간의 보존 기간을 갖도록 구성됩니다. 사이트 데이터베이스를 복구할 때 백업이 보존 기간 내에 있느냐 없느냐에 따라 복구 프로세스는 다르게 진행됩니다. 예를 들어 SQL 서버가 실패하고 마지막 백업이 7일이 경과한 경우 이 백업은 보존 기간을 벗어납니다.

SQL Server 변경 내용 추적 내부에 대한 자세한 내용은 SQL Server 팀의 블로그 게시물, [변경 내용 추적 정리 - 1부](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1/) 및 [변경 내용 추적 정리 - 2부](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2)를 참조하세요.

### <a name="reinitialization-of-site-or-global-data"></a>사이트 또는 전역 데이터 다시 초기화

사이트 또는 글로벌 데이터를 다시 초기화하는 프로세스는 사이트 데이터베이스 내 기존 데이터를 다른 사이트 데이터베이스의 데이터로 교체합니다. 예를 들어 사이트 ABC에서 사이트 XYZ의 데이터를 다시 초기화하면 다음 단계가 진행됩니다.

- 데이터가 사이트 XYZ에서 사이트 ABC로 복사됩니다.
- 사이트 XYZ에 대한 기존 데이터가 사이트 ABC의 사이트 데이터베이스에서 제거됩니다.
- 사이트 XYZ에서 복사된 데이터는 사이트 ABC의 사이트 데이터베이스에 삽입됩니다.

#### <a name="example-scenario-1-the-primary-site-reinitializes-the-global-data-from-the-cas"></a>예제 시나리오 1: 기본 사이트에서 CAS의 글로벌 데이터 다시 초기화

복구 프로세스에서 기본 사이트 데이터베이스에 있는 기본 사이트용 기존 글로벌 데이터를 제거하고 해당 데이터를 CAS에서 복사된 글로벌 데이터로 교체합니다.

#### <a name="example-scenario-2-the-cas-reinitializes-the-site-data-from-a-primary-site"></a>예제 시나리오 2: CAS가 기본 사이트의 사이트 데이터를 다시 초기화

복구 프로세스에서 CAS 데이터베이스에 있는 기본 사이트용 기존 사이트 데이터를 제거하고 해당 데이터를 기본 사이트에서 복사된 사이트 데이터로 교체합니다. 다른 기본 사이트에 대한 사이트 데이터는 영향을 받지 않습니다.

### <a name="site-database-recovery-scenarios"></a>사이트 데이터베이스 복구 시나리오

사이트 데이터베이스가 백업에서 복원되면 Configuration Manager에서는 마지막 데이터베이스 백업 이후에 사이트 및 글로벌 데이터에서 변경 내용을 복원하려고 시도합니다. 사이트 데이터베이스가 백업에서 복원된 후에 Configuration Manager에서 다음 작업을 시작합니다.  

#### <a name="recovered-site-is-a-cas"></a>복구된 사이트가 CAS인 경우

- 변경 내용 추적 보존 기간 내의 데이터베이스 백업  

  - **글로벌 데이터**: 백업 후의 글로벌 데이터 변경 내용은 모든 기본 사이트에서 복제됩니다.  

  - **사이트 데이터**: 백업 후의 사이트 데이터 변경 내용은 모든 기본 사이트에서 복제됩니다.  

- 변경 내용 추적 보존 기간보다 오래 된 데이터베이스 백업  

  - **글로벌 데이터**: CAS에서 참조 기본 사이트의 글로벌 데이터를 다시 초기화합니다(지정한 경우). 그런 다음 다른 모든 기본 사이트에서 CAS의 글로벌 데이터를 다시 초기화합니다. 참조 사이트를 지정하지 않은 경우 모든 기본 사이트에서 CAS의 글로벌 데이터를 다시 초기화합니다. 이 데이터는 백업에서 복원한 것입니다.  

  - **사이트 데이터**: CAS가 각 기본 사이트의 사이트 데이터를 다시 초기화합니다.  

#### <a name="recovered-site-is-a-primary-site"></a>복구된 사이트가 기본 사이트인 경우

- 변경 내용 추적 보존 기간 내의 데이터베이스 백업  

  - **글로벌 데이터**: 백업 후 글로벌 데이터의 변경 내용은 CAS에서 복제됩니다.  

  - **사이트 데이터**: CAS가 기본 사이트의 사이트 데이터를 다시 초기화합니다. 백업 후의 변경 내용은 손실됩니다. 클라이언트는 기본 사이트에 정보를 보낼 때 대부분의 데이터를 다시 생성합니다.  

- 변경 내용 추적 보존 기간보다 오래 된 데이터베이스 백업  

  - **글로벌 데이터**: 기본 사이트에서 CAS의 글로벌 데이터를 다시 초기화합니다.  

  - **사이트 데이터**: CAS가 기본 사이트의 사이트 데이터를 다시 초기화합니다. 백업 후의 변경 내용은 손실됩니다. 클라이언트는 기본 사이트에 정보를 보낼 때 대부분의 데이터를 다시 생성합니다.  

## <a name="site-recovery-procedures"></a>사이트 복구 절차

다음 절차 중 하나에 따라 사이트 서버와 사이트 데이터베이스를 복구할 수 있습니다.

### <a name="start-a-site-recovery-in-the-setup-wizard"></a>설치 마법사에서 사이트 복구 시작

1. [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)를 Configuration Manager 설치 폴더 외부 위치로 복사합니다. CD.Latest 폴더의 복사본에서 Configuration Manager 설치 마법사를 실행합니다.  

2. **시작** 페이지에서 **사이트 복구**를 선택한 후 **다음**을 선택합니다.  

3. 해당 사이트 복구에 적합한 옵션을 사용하여 마법사를 완료합니다.  

     - 복구 중에 설치 프로그램은 SQL Server에서 사용하는 SQL Server Service Broker(SSB) 포트를 식별합니다. 복구 중에 이 포트 설정을 변경하지 마세요. 만약 이 설정을 변경하면 복구가 완료된 후 데이터 복제가 올바로 작동하지 않습니다.  

     - 설치 마법사에서 Configuration Manager 설치에 사용할 원래 경로나 새 경로를 지정할 수 있습니다.  

### <a name="start-an-unattended-site-recovery"></a>무인 사이트 복구 시작

1. 사이트 복구에 필요한 옵션에 대해 무인 설치 스크립트를 준비합니다. 자세한 내용은 [무인 사이트 복구](/sccm/core/servers/manage/unattended-recovery)를 참조하세요.  

2. `/script` 명령줄 옵션을 사용하여 Configuration Manager 설치 프로그램을 실행합니다. 예를 들어 설치 초기화 파일**ConfigMgrUnattend.ini**을 만들 수 있습니다. 이 파일을 설치 프로그램을 실행하는 컴퓨터의 `C:\Temp` 디렉터리에 저장합니다. 다음 명령을 사용합니다.  

    `setup.exe /script C:\temp\ConfigMgrUnattend.ini`  

> [!NOTE]  
> CAS를 복구한 후 자식 사이트에서의 일부 사이트 데이터 복제가 설정되지 못할 수 있습니다. 이 데이터에는 하드웨어 인벤토리, 소프트웨어 인벤토리 및 상태 메시지가 포함될 수 있습니다.
>
> 이 문제가 발생한 경우 데이터베이스 복제에 대해 **ConfigMgrDRSSiteQueue**를 다시 초기화합니다. **SQL Server 관리자**를 사용하여 CAS의 사이트 데이터베이스에 대해 다음 쿼리를 실행합니다.
>
> ``` SQL
> IF EXISTS (SELECT * FROM sys.service_queues WHERE name = 'ConfigMgrDRSSiteQueue' AND is_receive_enabled = 0)  
>  
> ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON
> ```

## <a name="post-recovery-tasks"></a>복구 후 작업

사이트를 복구한 후에 사이트 복구가 완료되기 전에 고려할 몇 가지 복구 후 작업이 있습니다. 사이트 복구 프로세스를 완료하려면 다음 섹션을 참조하세요.

### <a name="reenter-user-account-passwords"></a>사용자 계정 암호 다시 입력

사이트 서버 복구 후 모든 사용자 계정의 암호를 사이트에 다시 입력합니다. 이러한 암호는 사이트 복구 동안 다시 설정됩니다. 사이트 복구가 완료된 후 설치 마법사의 **마침** 페이지에 계정이 나열됩니다. 목록은 복구된 사이트 서버의 `C:\ConfigMgrPostRecoveryActions.html`에 저장됩니다.

#### <a name="reenter-user-account-passwords-after-site-recovery"></a>사이트 복구 후 사용자 계정 암호를 다시 입력

1. Configuration Manager 콘솔을 열고 복구된 사이트에 연결합니다.  

2. **관리** 작업 영역으로 이동하여 **보안**을 펼친 다음 **계정**을 선택합니다.  

3. 각 계정에 대해 암호를 다시 입력하는 다음 단계를 수행합니다.  

     1. 사이트 복구 후에 확인된 목록에서 계정을 선택합니다.  

     2. 리본에서 **속성**을 선택합니다.  

     3. **일반** 탭에서 **설정**을 클릭한 다음 계정의 암호를 다시 입력합니다.  

     4. **확인**을 클릭하고 선택한 사용자 계정의 적절한 데이터 원본을 선택한 다음 **연결 테스트**를 선택합니다. 이 단계에서는 사용자 계정이 데이터 원본에 연결할 수 있는지 테스트하고 자격 증명을 확인합니다.  

     5. **확인**을 선택하여 암호 변경 내용을 저장한 다음 **확인**을 선택하여 계정 속성 페이지를 닫습니다.  

#### <a name="reenter-pxe-passwords"></a>PXE 암호 다시 입력

<!-- SCCMDocs#1683 -->

1. Configuration Manager 콘솔에서 **관리** 작업 공간으로 이동하여 **배포 지점** 노드를 선택합니다. **PXE** 열에 **예**가 있는 온-프레미스 배포 지점은 PXE에 대해 사용하도록 설정되고, 다시 입력할 암호가 있을 수 있습니다.

1. PXE 사용 배포 지점을 선택하고 리본에서 **속성**을 선택합니다.

1. **PXE** 탭으로 전환합니다.

1. **컴퓨터가 PXE를 사용할 경우 암호 요구** 옵션이 사용하도록 설정된 경우 암호를 입력하고 확인합니다.

1. **확인**을 선택하여 속성을 저장하고 닫습니다.

다른 PXE 사용 온-프레미스 배포 지점에 이 프로세스를 반복합니다.

#### <a name="reenter-task-sequence-passwords"></a>작업 순서 암호 다시 입력

<!-- SCCMDocs#1683 -->

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장하고 **작업 순서** 노드를 선택합니다.

1. 작업 순서를 선택한 다음 리본에서 **편집**을 선택합니다.

1. 암호를 다시 입력하려면 다음 단계를 검토합니다.

    - **Windows 설정 적용**: 로컬 관리자 암호를 사용하도록 설정하고 지정한 경우 암호를 다시 입력하고 확인합니다.

    - **네트워크 설정 적용**: 도메인에 가입할 수 있는 권한이 있는 계정의 경우 **설정**을 선택합니다. 암호를 입력하고 확인한 다음 **확인**을 선택합니다.

    - **운영 체제 이미지 캡처**: 대상에 액세스하는 데 사용되는 계정의 경우 **설정**을 선택합니다. 암호를 입력하고 확인한 다음 **확인**을 선택합니다.

    - **네트워크 폴더에 연결**: 네트워크에 연결하는 데 사용되는 계정의 경우 **설정**을 선택합니다. 암호를 입력하고 확인한 다음 **확인**을 선택합니다.

    - **BitLocker 사용**: 키 관리 옵션 **TPM 및 PIN**을 사용하는 경우 PIN을 다시 입력합니다.

    - **도메인 또는 작업 그룹 가입**: 도메인에 가입할 수 있는 권한이 있는 계정의 경우 **설정**을 선택합니다. 암호를 입력하고 확인한 다음 **확인**을 선택합니다.

    - **명령줄 실행**: **이 단계를 다음 계정으로 실행** 옵션을 사용하는 경우 **설정**을 선택합니다. 암호를 입력하고 확인한 다음 **확인**을 선택합니다.

    - **PowerShell 스크립트 실행**: **이 단계를 다음 계정으로 실행** 옵션을 사용하는 경우 **설정**을 선택합니다. 암호를 입력하고 확인한 다음 **확인**을 선택합니다.

모든 작업 순서에 대해 이 프로세스를 반복합니다.

### <a name="reenter-sideloading-keys"></a>테스트용 로드 키 다시 입력

사이트 서버 복구 후 사이트에 대해 지정된 Windows 테스트용 로드 키를 다시 입력합니다. 이러한 키는 사이트 복구 동안 다시 설정됩니다. 테스트용 로드 키를 다시 입력한 후 사이트가 Windows 테스트용 로드 키에 **사용된 활성화** 열 수를 다시 설정합니다.

예를 들어 사이트 오류 전에 **총 활성화** 수는 **100**으로 표시됩니다. 디바이스가 사용한 키의 수 또는 **사용된 활성화** 수는 **90**입니다. 사이트 복구 후 **총 활성화** 값은 여전히 **100**으로 표시되지만 **사용된 활성화** 열은 **0**으로 잘못 표시됩니다. 10개의 새 디바이스에서 테스트용 로드 키를 사용한 후에는 더 이상 테스트용 로드 키가 없으며 11번째 디바이스에서 테스트용 로드 키를 적용하지 못합니다.

### <a name="recreate-the-microsoft-intune-subscription"></a>Microsoft Intune 구독 다시 만들기

사이트 서버를 이미지로 다시 설치한 후에 Configuration Manager 사이트 서버를 복구하는 경우 Microsoft Intune 구독이 복원되지 않습니다. 사이트를 복구한 후 구독을 다시 연결합니다. 새 APN 요청을 만들지 않습니다. 대신 현재 유효한 PEM 파일을 업로드합니다. 마지막으로 iOS 관리를 구성하거나 갱신한 뒤 업로드한 동일한 파일을 사용합니다. 자세한 내용은 [Configuring the Microsoft Intune subscription](/sccm/mdm/deploy-use/configure-intune-subscription)을 참조하십시오.

### <a name="recreate-azure-services"></a>Azure 서비스 다시 만들기

<!-- SCCMDocs#1022 -->

Configuration Manager 버전 1806에서 사이트 복구 후 cloudmgr.log에 다음 오류가 표시됩니다.

`Index (zero-based) must be greater than or equal to zero`

이 문제를 해결하려면 각 Azure 테넌트 연결의 [비밀 키를 갱신](/sccm/core/servers/deploy/configure/azure-services-wizard#bkmk_renew)합니다.

### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>IIS를 사용하는 사이트 시스템 역할에 대해 SSL 구성

HTTPS에 대해 구성했던 IIS를 실행하는 사이트 시스템을 복구할 때 웹 서버 인증서를 사용하도록 IIS를 다시 구성합니다.

### <a name="reinstall-hotfixes"></a>핫픽스 다시 설치

사이트 복구 후에 사이트 서버에 적용했던 모든 [대역 외 핫픽스](/sccm/core/servers/manage/updates#bkmk_outofband)를 다시 설치해야 합니다. 사이트 복구 후 설치 마법사의 **마침** 페이지에서 이전에 설치한 핫픽스 목록을 확인합니다. 이 목록은 복구된 사이트 서버의 `C:\ConfigMgrPostRecoveryActions.html`에 저장됩니다.

### <a name="recover-custom-reports"></a>사용자 지정 보고서 복구

일부 고객은 SQL Server Reporting Services의 사용자 지정 보고서를 만듭니다. 이 구성 요소가 실패하면 보고서 서버의 백업에서 보고서를 복구합니다. Reporting Services에서 사용자 지정 보고서를 복원하는 방법에 대한 자세한 내용은 [Reporting Services에 대한 백업 및 복원 작업](https://docs.microsoft.com/sql/reporting-services/install-windows/backup-and-restore-operations-for-reporting-services) 을 참조하세요.

### <a name="recover-content-files"></a>콘텐츠 파일 복구

사이트 데이터베이스가 사이트 서버에서 콘텐츠 파일을 저장하는 위치를 추적합니다. 콘텐츠 파일 자체는 백업 및 복구 프로세스의 일부로 백업 또는 복원되지 않습니다. 콘텐츠 파일을 완전히 복구하려면 콘텐츠 라이브러리와 패키지 원본 파일을 원래 위치로 복원합니다. 콘텐츠 파일을 복구하는 방법에는 여러 가지가 있습니다. 가장 쉬운 방법은 사이트 서버의 파일 시스템 백업에서 파일을 복원하는 것입니다.

패키지 원본 파일의 파일 시스템 백업이 없는 경우 수동으로 파일을 복사하거나 다운로드합니다. 이 프로세스는 원래 패키지를 만드는 경우와 비슷합니다. SQL Server에서 다음 쿼리를 실행하여 모든 패키지 및 애플리케이션에 대한 패키지 원본 위치를 검색합니다. `SELECT * FROM v_Package` 패키지 ID의 처음 세 문자를 보면 패키지 원본 사이트를 식별할 수 있습니다. 예를 들어 패키지 ID가 CEN00001이면 원본 사이트의 사이트 코드는 CEN입니다. 패키지 원본 파일을 복원할 때는 해당 파일을 실패 전에 있었던 위치로 복원해야 합니다.

콘텐츠 라이브러리가 포함된 파일 시스템 백업이 없는 경우에는 다음과 같은 복원 옵션이 있습니다.  

- **사전 준비된 콘텐츠 파일 가져오기**: Configuration Manager 계층 구조의 다른 위치에서 모든 패키지와 애플리케이션을 사용하여 사전 준비된 콘텐츠 파일을 만들 수 있습니다. 그런 다음, 사이트 서버에서 콘텐츠 라이브러리를 복구하려면 사전 준비된 콘텐츠 파일을 가져옵니다.  

- **콘텐츠 업데이트**: Configuration Manager는 패키지 원본에서 콘텐츠를 콘텐츠 라이브러리에 복사합니다. 이 작업을 성공적으로 마치려면 패키지 원본 파일을 원래 위치에서 사용할 수 있어야 합니다. 각 패키지와 애플리케이션에 대해 이 작업을 수행합니다.

### <a name="recover-custom-software-updates"></a>사용자 지정 소프트웨어 업데이트 복구

백업 계획에 System Center Updates Publisher 데이터베이스 파일이 포함돼 있으면 Updates Publisher 컴퓨터가 실패할 경우 데이터베이스를 복구할 수 있습니다. Updates Publisher에 대한 자세한 내용은 [System Center Updates Publisher](/sccm/sum/tools/updates-publisher)를 참조하세요.

#### <a name="restore-the-updates-publisher-database"></a>Updates Publisher 데이터베이스 복원

1. 복구된 컴퓨터에 Updates Publisher를 다시 설치합니다.  

2. Updates Publisher를 실행하는 컴퓨터에서 데이터베이스 파일**Scupdb.sdf**을 백업 대상에서 `%USERPROFILE%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\`으로 복사합니다.  

3. 컴퓨터에서 둘 이상의 사용자가 Updates Publisher를 실행하는 경우 해당 사용자 프로필 위치로 각 데이터베이스 파일을 복사합니다.  

### <a name="user-state-migration-data"></a>사용자 환경 마이그레이션 데이터

상태 마이그레이션 지점 속성의 일부로 사용자 상태 데이터가 저장되는 폴더를 지정합니다. 상태 마이그레이션 지점을 복구한 후 서버에서 사용자 상태 데이터를 수동으로 복원합니다. 실패하기 전에 데이터가 저장된 동일한 폴더에 해당 데이터를 복원합니다.

### <a name="regenerate-the-certificates-for-distribution-points"></a>배포 지점에 대한 인증서 다시 생성

사이트를 복원한 후 **distmgr.log**는 하나 이상의 배포 지점에 대해 `Failed to decrypt cert PFX data` 항목을 나열할 수 있습니다. 이 항목은 사이트에서 배포 지점 인증서 데이터를 암호 해독할 수 없다는 것을 나타냅니다. 이 문제를 해결하려면 영향을 받는 배포 지점에 대한 인증서를 다시 생성하거나 다시 가져옵니다. [Set-CMDistributionPoint](https://docs.microsoft.com/powershell/module/configurationmanager/set-cmdistributionpoint) PowerShell cmdlet을 사용합니다.

### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>클라우드 기반 배포 지점에 사용되는 인증서 업데이트

Configuration Manager는 클라우드 기반 배포 지점과 통신하려면 사이트 서버에 대한 Azure 관리 인증서가 필요합니다. 사이트 복구 후에 클라우드 기반 배포 지점에 대한 인증서를 업데이트합니다.

## <a name="recover-a-secondary-site"></a>보조 사이트 복구

Configuration Manager에서는 보조 사이트에서의 데이터베이스 백업을 지원하는 것이 아니라 보조 사이트를 다시 설치하여 복구 작업을 지원합니다. Configuration Manager 보조 사이트가 실패할 경우 보조 사이트 복구가 필요합니다.

### <a name="requirements"></a>요구 사항

- 서버가 보조 사이트의 모든 전제 조건을 충족하고 적절한 보안 권한으로 구성되어 있어야 합니다.  

- 실패한 사이트에 사용된 것과 동일한 설치 경로를 사용합니다.  

- 실패한 서버와 동일한 구성으로 서버를 사용합니다. 이 구성에는 해당 정규화된 도메인 이름(FQDN)이 포함됩니다.  

- 서버에는 실패한 사이트와 동일한 SQL Server 구성이 있어야 합니다.  

  - 보조 사이트 복구 시에는 컴퓨터에 SQL Server Express가 아직 설치되어 있지 않더라도 Configuration Manager에서 SQL Server Express를 설치하지 않습니다.  

  - 실패 전 보조 사이트 데이터베이스에 사용한 것과 동일한 버전과 인스턴스의 SQL Server를 사용합니다.  

### <a name="procedure"></a>절차

Configuration Manager 콘솔의 **사이트** 노드에서 **보조 사이트 복구** 작업을 사용합니다. 다른 유형의 사이트와 달리, 보조 사이트의 복구에는 백업 파일을 사용하지 않습니다. 이 프로세스에서는 실패한 서버에 보조 사이트 파일을 다시 설치합니다. 사이트가 다시 설치되면 보조 사이트 데이터가 부모 기본 사이트에서 다시 초기화됩니다.

복구 프로세스 동안 Configuration Manager는 보조 사이트 서버에 콘텐츠 라이브러리가 존재하는지 확인합니다. 또한 해당 콘텐츠를 사용할 수 있는지도 확인합니다. 해당 콘텐츠가 있으면 보조 사이트에서 기존 콘텐츠 라이브러리를 사용합니다. 그렇지 않은 경우 보조 사이트의 콘텐츠 라이브러리를 복구하려면 서버에 콘텐츠를 재배포하거나 사전 준비해야 합니다.

보조 사이트 서버에 없는 배포 지점이 있는 경우 보조 사이트 복구 동안 배포 지점을 다시 설치할 필요 없습니다. 보조 사이트 복구 후에 사이트가 배포 지점과 자동으로 동기화됩니다.

Configuration Manager 콘솔의 **사이트** 노드에서 **설치 상태 표시** 작업을 사용하여 보조 사이트 복구 상태를 확인할 수 있습니다.
