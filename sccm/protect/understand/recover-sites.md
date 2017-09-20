---
title: "사이트 복구 | Microsoft Docs"
description: "System Center Configuration Manager의 사이트 복구에 대해 알아봅니다."
ms.custom: na
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19539f4d-1667-4b4c-99a1-9995f12cf5f7
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: f5aff56e9948536944140fbadb0539c7a4e20f26
ms.sourcegitcommit: 5ca89204716750eaaceb01bba40b35b85c7122ba
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/18/2017
---
#  <a name="recover-a-configuration-manager-site"></a>Configuration Manager 사이트 복구

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 사이트가 실패하거나 사이트 데이터베이스에서 데이터 손실이 발생한 후에 Configuration Manager 사이트 복구를 실행합니다. 데이터 복구 및 재동기화는 사이트 복구의 핵심 작업으로서 작업 중단을 방지하기 위해 필요합니다.

이 항목의 섹션에서는 Configuration Manager 사이트를 복구하는 데 도움이 될 수 있습니다. 백업을 만들려면 [Configuration Manager의 백업](/sccm/protect/understand/backup-and-recovery)을 참조하세요.

## <a name="considerations-before-recovering-a-site"></a>사이트 복구 전 고려 사항
**동일한 버전 및 에디션의 SQL Server를 사용해야 합니다.** 예를 들어 SQL Server 2014에서 실행되던 데이터베이스를 SQL Server 2016으로 복원하는 것은 지원되지 않습니다. 마찬가지로 SQL Server 2016 Standard Edition에서 실행되던 사이트 데이터베이스를 SQL Server 2016 Enterprise Edition으로 복원할 수 없습니다.
-   SQL Server를 **단일 사용자 모드**로 설정하면 안 됩니다.
-   . MDF 및 .LDF 파일이 올바른지 확인합니다. 사이트를 복구할 때 복원하려는 파일의 상태는 확인되지 않습니다.

**SQL Server Always On 가용성 그룹을 사용하여 사이트 데이터베이스를 호스트하는 경우:**[SQL Server Always On 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-recovery)에 설명된 대로 복구 계획을 수정합니다.

**데이터베이스 복제본을 사용하는 경우:** 데이터베이스 복제본용으로 구성된 사이트 데이터베이스를 복원한 후에 데이터베이스 복제본을 사용하려면 먼저 게시 및 구독을 모두 다시 만드는 것을 포함해 각 데이터베이스 복제본을 다시 구성해야 합니다.

## <a name="determine-your-recovery-options"></a>복구 옵션 결정
Configuration Manager 기본 사이트 서버 및 중앙 관리 사이트 복구를 수행하려면 **사이트 서버** 및 **사이트 데이터베이스**라는 두 가지 영역을 가장 기본적으로 고려해야 합니다.
다음 섹션은 복구 시나리오에 가장 적합한 옵션을 선택하는 데 도움이 됩니다.

> [!NOTE]   
> 설치 프로그램이 서버에서 기존 Configuration Manager 사이트를 검색한 경우, 사이트 복구를 시작할 수는 있지만 사이트 서버에 대한 복구 옵션이 제한됩니다. 예를 들어 기존 사이트 서버에서 설치 프로그램을 실행하고 복구를 선택하면, 사이트 데이터베이스 서버를 복구할 수는 있지만 사이트 서버 복구를 위한 옵션은 사용할 수 없습니다.

### <a name="site-server-recovery-options"></a>사이트 서버 복구 옵션
Configuration Manager 설치 폴더 외부에 만든 **CD.Latest** 폴더의 복사본에서 설치 프로그램을 시작합니다.
-   사이트 서버의 **시작** 메뉴에서 Configuration Manager 설치 프로그램을 실행하는 경우 **사이트 복구** 옵션을 사용할 수 없습니다.
-   백업을 수행하기 전에 Configuration Manager 콘솔 내에서 업데이트를 설치한 경우 설치 미디어나 Configuration Manager 설치 경로의 설치 프로그램을 사용하여 사이트를 다시 설치할 수 없습니다.

그런 다음 **사이트 복구** 옵션을 선택합니다. 실패한 사이트 서버에 대해 다음과 같은 복구 옵션을 사용할 수 있습니다.

-   **기존 백업을 사용하여 사이트 서버 복구**: 이 옵션은 사이트 오류 전에 **백업 사이트 서버** 유지 관리 작업의 일부로 사이트 서버에 만들어진 Configuration Manager 사이트 서버 백업이 있을 때 사용합니다. 백업된 사이트를 기준으로 사이트가 다시 설치되고 사이트 설정이 구성됩니다.
-   **사이트 서버 다시 설치**: 이 옵션은 사이트 서버 백업이 없을 때 사용합니다. 사이트 서버가 다시 설치되며, 초기 설치 시 구성한 것처럼 사이트 설정을 지정해야 합니다.
  -   실패한 사이트를 처음 설치했을 때 사용한 것과 동일한 사이트 코드 및 사이트 데이터베이스 이름을 사용해야 합니다.
  -   새 운영 체제를 실행하는 새 컴퓨터에 사이트를 다시 설치할 수 있습니다.
  -   컴퓨터는 원본 사이트 서버의 같은 이름인 FQDN을 사용해야 합니다.   

### <a name="site-database-recovery-options"></a>사이트 데이터베이스 복구 옵션
설치 프로그램을 실행할 때 사이트 데이터베이스에 대해 다음과 같은 복구 옵션을 사용할 수 있습니다.
-   **백업 집합을 사용하여 사이트 데이터베이스 복구**: 이 옵션은 사이트 데이터베이스 오류 전에 사이트에서 실행된 **백업 사이트 서버** 유지 관리 작업의 일부로 사이트 서버에 만들어진 Configuration Manager 사이트 데이터베이스 백업이 있을 때 사용합니다. 계층이 있을 때 마지막 사이트 데이터베이스 백업 후 사이트 데이터베이스에서 변경된 내용은 기본 사이트에 대해서는 중앙 관리 사이트, 또는 중앙 관리 사이트에 대해서는 참조 기본 사이트에서 검색됩니다. 독립 실행형 기본 사이트에 대한 사이트 데이터베이스를 복구하면 마지막 백업 이후의 사이트 변경 내용은 손실됩니다.

   계층 내 사이트에 대한 사이트 데이터베이스를 복구할 경우 복구 동작은 중앙 관리 사이트 및 기본 사이트에 대해 서로 다르며 마지막 백업이 SQL Server 변경 내용 추적 보존 기간 내에 있는지 여부에 따라서도 다릅니다. 자세한 내용은 이 항목의 [사이트 데이터베이스 복구 시나리오](##site-database-recovery-scenarios) 섹션을 참조하세요.
  > [!NOTE]   
  > 백업 집합을 사용하여 사이트 데이터베이스를 복원하도록 선택했지만 사이트 데이터베이스가 이미 존재하는 경우 복구는 실패합니다.  

-   **이 사이트에 대한 새 데이터베이스 만들기**: 이 옵션은 Configuration Manager 사이트 데이터베이스 백업이 없을 때 사용합니다. 계층이 있을 때, 새 사이트 데이터베이스가 만들어지고 기본 사이트에 대해서는 중앙 관리 사이트에서, 또는 중앙 관리 사이트에 대해서는 참조 기본 사이트에서 복제된 데이터를 사용하여 데이터가 복구됩니다. 이 옵션은 독립 실행형 기본 사이트 또는 기본 사이트가 없는 중앙 관리 사이트를 복구할 경우에는 사용할 수 없습니다.

-   **수동으로 복구된 사이트 데이터베이스 사용**: Configuration Manager 사이트 데이터베이스는 이미 복구했지만 복구 프로세스를 완료해야 하는 경우 이 옵션을 사용합니다.
    -   Configuration Manager는 Configuration Manager 백업 유지 관리 작업이나 DPM 또는 기타 프로세스를 사용하여 수행하는 사이트 데이터베이스 백업에서 사이트 데이터베이스를 복구할 수 있습니다. Configuration Manager 외부의 방법을 사용하여 사이트 데이터베이스를 복원한 후에는 설치 프로그램을 실행하고 이 옵션을 선택하여 사이트 데이터베이스 복구를 완료해야 합니다.

    > [!NOTE]   
    > DPM을 사용하여 사이트 데이터베이스를 백업할 경우, Configuration Manager에서 복원 프로세스를 계속하기 전에 먼저 DPM 프로시저를 사용하여 사이트 데이터베이스를 지정된 위치에 복원하세요. DPM에 대한 자세한 내용은 TechNet에서 [Data Protection Manager Documentation Library(Data Protection Manager)]() 를 참조하세요.    

    -   계층이 있을 때 마지막 사이트 데이터베이스 백업 후 사이트 데이터베이스에서 변경된 내용은 기본 사이트에 대해서는 중앙 관리 사이트, 또는 중앙 관리 사이트에 대해서는 참조 기본 사이트에서 검색됩니다. 독립 실행형 기본 사이트에 대한 사이트 데이터베이스를 복구하면 마지막 백업 이후의 사이트 변경 내용은 손실됩니다.     


-   **데이터베이스 복구 건너뛰기**: 이 옵션은 Configuration Manager 사이트 데이터베이스 서버에서 데이터 손실이 발생하지 않았을 때 사용합니다. 이 옵션은 사이트 데이터베이스가 현재 복구 중인 사이트 서버가 아닌 다른 컴퓨터에 있는 경우에만 유효합니다.

### <a name="sql-server-change-tracking-retention-period"></a>SQL Server 변경 내용 추적 보존 기간
변경 내용 추적은 SQL Server에서 사이트 데이터베이스에 대해 사용하도록 설정됩니다. Configuration Manager는 변경 내용 추적을 통해 이전 시점 이후에 데이터베이스 테이블에서 변경된 내용에 관한 정보를 쿼리할 수 있습니다. 보존 기간은 변경 내용 추적 정보가 보존되는 기간을 지정합니다. 기본적으로 사이트 데이터베이스는 5일간의 보존 기간을 갖도록 구성됩니다. 사이트 데이터베이스를 복구할 때 백업이 보존 기간 내에 있느냐 없느냐에 따라 복구 프로세스는 다르게 진행됩니다. 예를 들어, 사이트 데이터베이스 서버가 실패하고 마지막 백업이 7일 경과한 경우 이 백업은 보존 기간을 벗어납니다.

SQL Server 변경 내용 추적 내부에 대한 자세한 내용은 SQL Server 팀의 [변경 내용 추적 정리-1부](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1/) 및 [변경 내용 추적 정리-2부](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2) 블로그를 참조하세요.

### <a name="reinitialization-of-site-or-global-data"></a>사이트 또는 전역 데이터 다시 초기화
사이트 또는 글로벌 데이터를 다시 초기화하는 프로세스는 사이트 데이터베이스 내 기존 데이터를 다른 사이트 데이터베이스의 데이터로 교체합니다. 예를 들어 사이트 ABC에서 사이트 XYZ의 데이터를 다시 초기화하면 다음 단계가 진행됩니다.
-   데이터가 사이트 XYZ에서 사이트 ABC로 복사됩니다.
-   사이트 XYZ에 대한 기존 데이터가 사이트 ABC의 사이트 데이터베이스에서 제거됩니다.
-   사이트 XYZ에서 복사된 데이터는 사이트 ABC의 사이트 데이터베이스에 삽입됩니다.

#### <a name="example-scenario-1"></a>예제 시나리오 1
**기본 사이트에서 중앙 관리 사이트의 전역 데이터를 다시 초기화**: 복구 프로세스에서 기본 사이트 데이터베이스에 있는 기본 사이트용 기존 전역 데이터를 제거하고 해당 데이터를 중앙 관리 사이트에서 복사된 전역 데이터로 교체합니다.

#### <a name="example-scenario-2"></a>예제 시나리오 2
**중앙 관리 사이트에서 기본 사이트의 사이트 데이터를 다시 초기화**: 복구 프로세스에서 중앙 관리 사이트 데이터베이스에 있는 기본 사이트용 기존 사이트 데이터를 제거하고 해당 데이터를 기본 사이트에서 복사된 사이트 데이터로 교체합니다. 다른 기본 사이트에 대한 사이트 데이터는 영향을 받지 않습니다.

### <a name="site-database-recovery-scenarios"></a>사이트 데이터베이스 복구 시나리오
사이트 데이터베이스가 백업에서 복원되면 Configuration Manager에서는 마지막 데이터베이스 백업 이후에 사이트 및 글로벌 데이터에서 변경된 내용을 복원하려고 시도합니다. 다음에서는 사이트 데이터베이스가 백업에서 복원된 후에 Configuration Manager에서 시작하는 작업을 설명합니다.

**복구된 사이트가 중앙 관리 사이트인 경우:**
-   **변경 내용 추적 보존 기간 내의 데이터베이스 백업**
    -   **글로벌 데이터:** 백업 후의 글로벌 데이터 변경 내용은 모든 기본 사이트에서 복제됩니다.
    -   **사이트 데이터:** 백업 후의 사이트 데이터 변경 내용은 모든 기본 사이트에서 복제됩니다.


-   **변경 내용 추적 보존 기간보다 오래 된 데이터베이스 백업**
    -   **전역 데이터:** 중앙 관리 사이트에서 참조 기본 사이트의 전역 데이터를 다시 초기화합니다(지정한 경우). 그런 다음 다른 모든 기본 사이트에서 중앙 관리 사이트의 글로벌 데이터를 다시 초기화합니다. 참조 사이트가 지정되지 않은 경우, 모든 기본 사이트에서 중앙 관리 사이트의 글로벌 데이터(백업에서 복원된 데이터)를 다시 초기화합니다.
    -   **사이트 데이터:** 중앙 관리 사이트에서 각 기본 사이트의 사이트 데이터를 다시 초기화합니다.


**복구된 사이트가 기본 사이트인 경우:**
-   **변경 내용 추적 보존 기간 내의 데이터베이스 백업**
    -   **글로벌 데이터:** 백업 후의 글로벌 데이터 변경 내용은 중앙 관리 사이트에서 복제됩니다.
    -   **사이트 데이터:** 중앙 관리 사이트에서 기본 사이트의 사이트 데이터를 다시 초기화합니다. 백업 후의 변경 내용은 손실되지만 대부분의 데이터는 기본 사이트에 정보를 보내는 클라이언트에 의해 다시 생성됩니다.


-   **변경 내용 추적 보존 기간보다 오래 된 데이터베이스 백업**
    -   **글로벌 데이터:** 기본 사이트에서 중앙 관리 사이트의 글로벌 데이터를 다시 초기화합니다.
    -   **사이트 데이터:** 중앙 관리 사이트에서 기본 사이트의 사이트 데이터를 다시 초기화합니다. 백업 후의 변경 내용은 손실되지만 대부분의 데이터는 기본 사이트에 정보를 보내는 클라이언트에 의해 다시 생성됩니다.

## <a name="site-recovery-procedures"></a>사이트 복구 절차
다음 절차 중 하나에 따라 사이트 서버와 사이트 데이터베이스를 복구할 수 있습니다.

### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>설치 마법사에서 사이트 복구를 시작하려면
1.  [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folde)를 Configuration Manager 설치 폴더 외부 위치로 복사합니다.
CD.Latest 폴더의 복사본에서 Configuration Manager 설치 마법사를 실행합니다.

2.  **시작** 페이지에서 **사이트 복구**를 선택한 후 **다음**을 클릭합니다.

3.  해당 사이트 복구에 적합한 옵션을 사용하여 마법사를 완료합니다.

  -   복구 중에 설치 프로그램은 SQL Server에서 사용되는 SQL Server Service Broker(SSB) 포트를 식별합니다. 복구 중에 이 포트 설정을 변경하지 마세요. 만약 이 설정을 변경하면 복구가 완료된 후 데이터 복제가 올바르게 작동하지 않습니다.

  -   설치 마법사에서 Configuration Manager 설치에 사용할 원래 경로나 새 경로를 지정할 수 있습니다.

### <a name="to-start-an-unattended-site-recovery"></a>무인 사이트 복구를 시작하려면
  1.    사이트 복구에 필요한 옵션에 대해 무인 설치 스크립트를 준비합니다.  [무인 사이트 복구 스크립트 파일 키](/sccm/protect/understand/unattended-site-recovery-script-file-keys)를 참조하세요.

  2.    명령 **/script** 옵션을 사용하여 Configuration Manager 설치 프로그램을 실행합니다. 예를 들어 설치 초기화 파일의 이름을 ConfigMgrUnattend.ini로 지정하고 이 파일을 설치 프로그램이 실행 중인 컴퓨터의 C:\Temp 디렉터리에 저장한 경우, 해당 명령은 다음과 같습니다. **Setup /script C:\temp\ConfigMgrUnattend.ini**

  > [!NOTE]   
  >  중앙 관리 사이트를 복구한 후 자식 사이트에서의 일부 사이트 데이터 복제가 설정되지 못할 수 있습니다. 여기에는 하드웨어 인벤토리, 소프트웨어 인벤토리 및 상태 메시지가 포함됩니다.
  >
  >  이 경우 데이터베이스 복제에 대해 **ConfigMgrDRSSiteQueue** 를 다시 초기화해야 합니다.  이를 위해 **SQL Server 관리자**를 사용하여 중앙 관리 사이트의 Configuration Manager 사이트 데이터베이스에 대해 다음 쿼리를 실행합니다.
  >
  >  **IF EXISTS (SELECT \* FROM sys.service_queues WHERE name = 'ConfigMgrDRSSiteQueue' AND is_receive_enabled = 0)**
  >
  >  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**


## <a name="post-recovery-tasks"></a>복구 후 작업
사이트를 복구한 후에 사이트 복구가 완료되기 전에 고려해야 할 몇 가지 복구 후 작업이 있습니다. 사이트 복구 프로세스를 완료하려면 다음 섹션을 참조하세요.

### <a name="re-enter-user-account-passwords"></a>사용자 계정 암호 다시 입력
사이트에 대해 지정한 사용자 계정의 암호는 사이트 복구 중에 다시 설정되므로 사이트를 복구한 후에 해당 암호를 다시 입력해야 합니다. 계정은 사이트 복구가 완료된 후 설치 마법사의 **마침** 페이지에 나열되고 복구된 사이트 서버의 C:\ConfigMgrPostRecoveryActions.html에 저장됩니다.

#### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>사이트 복구 후 사용자 계정 암호를 다시 입력하려면

1.  Configuration Manager 콘솔을 열고 복구된 사이트에 연결합니다.

2.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

3.  **관리** 작업 영역에서 **보안**을 확장한 후 **계정**을 클릭합니다.

4.  암호를 다시 입력해야 하는 각 계정에 대해 다음 작업을 수행합니다.

    1.  사이트 복구 후에 확인된 계정 목록에서 계정을 선택합니다. 이 목록은 복구된 사이트 서버의 C:\ConfigMgrPostRecoveryActions.html에서 찾을 수 있습니다.

    2.  **홈** 탭의 **속성** 그룹에서 **속성** 을 클릭하여 계정 속성을 엽니다.

    3.  **일반** 탭에서 **설정**을 클릭한 다음 계정의 암호를 다시 입력합니다.

    4.  **확인**을 클릭하고 선택한 사용자 계정의 적절한 데이터 원본을 선택한 다음 **연결 테스트** 를 클릭하여 사용자 계정이 데이터 원본에 연결할 수 있는지 확인합니다.

    5.  **확인** 을 클릭하여 암호 변경 내용을 저장하고 **확인**을 클릭합니다.

### <a name="re-enter-sideloading-keys"></a>테스트용 로드 키 다시 입력
사이트 서버 복구 후에 사이트 복구 중 테스트용 로드 키가 초기화되므로 사이트에 대해 지정된 Windows 테스트용 로드 키를 다시 입력해야 합니다. 테스트용 로드 키를 다시 입력한 후 Configuration Manager 콘솔에서 Windows 테스트용 로드 키의 **사용된 활성화 수** 열 수가 다시 설정됩니다. 예를 들어 사이트 오류 전에 장치에 **총 활성화 수**가 **100**으로 설정되어 있고 사용된 키의 수에 대한 **사용된 활성화 수**가 **90**이라고 가정해 봅니다. 사이트 복구 후 **총 활성화 수** 열은 여전히 **100**을 표시하지만 **사용된 활성화 수** 열은 값을 **0**으로 잘못 표시합니다. 그러나 10개의 새 장치에서 테스트용 로드 키를 사용한 후에는 남은 테스트용 로드 키가 없으며 다음 장치에서 테스트용 로드 키를 적용하지 못합니다.

### <a name="recreate-the-microsoft-intune-subscription"></a>Microsoft Intune 구독 다시 만들기
 사이트 서버 컴퓨터를 이미지로 다시 설치한 후에 Configuration Manager 사이트 서버를 복구하는 경우 Microsoft Intune 구독이 복원되지 않습니다. 사이트를 복구한 후 구독을 다시 연결 해야 합니다.  새 APN 요청을 만드는 대신, iOS 관리가 마지막으로 구성 또는 갱신될 때 업로드된 현재 유효한 .pem 파일을 업로드하세요. 자세한 내용은 [Configuring the Microsoft Intune subscription](/sccm/mdm/deploy-use/configure-intune-subscription)을 참조하십시오.

### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>IIS를 사용하는 사이트 시스템 역할에 대해 SSL 구성
실패하기 전에 HTTPS에 대해 구성했던 IIS를 실행하는 사이트 시스템을 복구할 때 웹 서버 인증서를 사용하도록 IIS를 다시 구성해야 합니다.

### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>복구된 사이트 서버에 핫픽스 다시 설치
사이트 복구 후에 사이트 서버에 적용했던 모든 핫픽스를 다시 설치해야 합니다. 사이트 복구 후 설치 마법사의 **마침** 페이지에서 이전에 설치한 핫픽스 목록을 확인합니다. 이 목록은 복구된 사이트 서버의 **C:\ConfigMgrPostRecoveryActions.html**에도 저장되어 있습니다.

### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Reporting Services를 실행하는 컴퓨터에서 사용자 지정 보고서 복구
사용자 지정 Reporting Services 보고서를 만들었는데 Reporting Services가 실패하는 경우 보고서 서버를 백업했다면 보고서를 복구할 수 있습니다. Reporting Services에서 사용자 지정 보고서를 복구하는 방법에 대한 자세한 내용은 SQL Server 2008 온라인 설명서의 [Reporting Services 설치에 대한 백업 및 복원 작업](http://go.microsoft.com/fwlink/p/?LinkId=228724) 을 참조하세요.

### <a name="recover-content-files"></a>콘텐츠 파일 복구
 사이트 데이터베이스에는 콘텐츠 파일이 저장된 사이트 서버의 위치에 대한 정보가 포함되어 있지만 백업 및 복구 프로세스 중에 콘텐츠 파일이 백업되거나 복원되지는 않습니다. 콘텐츠 파일을 완전히 복구하려면 콘텐츠 라이브러리와 패키지 원본 파일을 원래 위치로 복원해야 합니다. 콘텐츠 파일을 복구하는 방법은 몇 가지가 있지만 가장 쉬운 방법은 사이트 서버의 파일 시스템 백업에서 파일을 복원하는 것입니다.

 패키지 원본 파일의 파일 시스템 백업이 없는 경우 패키지를 처음 만들 때 했던 대로 수동으로 복사하거나 다운로드해야 합니다. SQL Server에서 다음 쿼리를 실행하면 모든 패키지 및 응용 프로그램에 대한 패키지 원본 위치를 검색할 수 있습니다. `SELECT * FROM v_Package` 패키지 ID의 처음 세 문자를 보면 패키지 원본 사이트를 식별할 수 있습니다. 예를 들어 패키지 ID가 CEN00001이면 원본 사이트의 사이트 코드는 CEN입니다. 패키지 원본 파일을 복원할 때는 해당 파일을 실패 전에 있었던 위치로 복원해야 합니다.

 콘텐츠 라이브러리가 포함된 파일 시스템 백업이 없는 경우에는 다음과 같은 복원 옵션이 있습니다.

-   **사전 준비된 콘텐츠 파일 가져오기**: Configuration Manager 계층이 있으면 다른 위치의 모든 패키지와 응용 프로그램으로 사전 준비된 콘텐츠 파일을 만든 다음 사전 준비된 콘텐츠 파일을 가져와 사이트 서버의 콘텐츠 라이브러리를 복구할 수 있습니다.

-   **콘텐츠 업데이트**: 패키지 또는 응용 프로그램 배포 유형에 대해 콘텐츠 업데이트 작업을 시작하면 패키지 원본의 콘텐츠가 콘텐츠 라이브러리로 복사됩니다. 이 작업을 성공적으로 마치려면 패키지 원본 파일이 원래 위치에 있어야 합니다. 각 패키지와 응용 프로그램에 대해 이 작업을 수행해야 합니다.

### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Updates Publisher를 실행하는 컴퓨터에서 사용자 지정 소프트웨어 업데이트 복구
백업 계획에 Updates Publisher 데이터베이스 파일을 포함했다면 Updates Publisher가 실행되는 컴퓨터에 실패가 발생할 경우 데이터베이스를 복구할 수 있습니다. Updates Publisher에 대한 자세한 내용은 System Center TechCenter 라이브러리에서 [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) 을 참조하세요.

다음 절차를 사용하여 Updates Publisher 데이터베이스를 복원합니다.

#### <a name="to-restore-the-updates-publisher-2011-database"></a>Updates Publisher 2011 데이터베이스를 복원하려면
1.  복구된 컴퓨터에 Updates Publisher를 다시 설치합니다.

2.  Updates Publisher가 실행되는 컴퓨터에서 데이터베이스 파일(Scupdb.sdf)을 백업 대상에서 %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\으로 복사합니다.

3.  컴퓨터에서 둘 이상의 사용자가 Updates Publisher를 실행하는 경우 각 데이터베이스 파일을 해당 사용자 프로필 위치로 복사해야 합니다.

### <a name="user-state-migration-data"></a>사용자 환경 마이그레이션 데이터
상태 마이그레이션 지점 사이트 시스템 속성의 일부로 사용자 환경 마이그레이션 데이터가 저장되는 폴더를 지정합니다. 사용자 환경 마이그레이션 데이터가 저장된 폴더를 사용하여 서버를 복구한 후에는 서버에서 오류 전 데이터가 저장된 폴더로 사용자 환경 마이그레이션 데이터를 복원해야 합니다.

### <a name="regenerate-the-certificates-for-distribution-points"></a>배포 지점에 대한 인증서 다시 생성
사이트를 복원한 후 distmgr.log에는 하나 이상의 배포 지점에 대해 **Failed to decrypt cert PFX data**항목이 포함될 수 있습니다. 이 항목은 사이트에서 배포 지점 인증서 데이터를 암호 해독할 수 없는 것을 나타냅니다. 이 문제를 해결하려면 영향을 받는 배포 지점에 대한 인증서를 다시 생성하거나 다시 가져와야 합니다. [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx) PowerShell cmdlet을 사용하여 그렇게 할 수 있습니다.

### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>클라우드 기반 배포 지점에 사용되는 인증서 업데이트
 Configuration Manager에는 클라우드 기반 배포 지점 통신을 위해 사이트 서버에 사용되는 관리 인증서가 필요합니다. 사이트 복구 후에 클라우드 기반 배포 지점에 대한 인증서를 업데이트해야 합니다.

## <a name="recover-a-secondary-site"></a>보조 사이트 복구
 Configuration Manager에서는 보조 사이트에서의 데이터베이스 백업을 지원하는 것이 아니라 보조 사이트를 다시 설치하여 복구하는 작업을 지원합니다. Configuration Manager 보조 사이트가 실패할 경우 보조 사이트 복구가 필요합니다.

### <a name="requirements-for-reinstalling-a-secondary-site"></a>보조 사이트를 다시 설치하기 위한 요구 사항
-   컴퓨터가 보조 사이트의 모든 전제 조건을 충족하고 적절한 보안 권한으로 구성되어 있어야 합니다.
-   실패한 사이트에 사용된 것과 동일한 설치 경로를 사용해야 합니다.
-   보조 사이트를 성공적으로 복구하려면 실패한 컴퓨터와 FQDN 등이 동일한 구성을 갖는 컴퓨터를 사용해야 합니다.
-   컴퓨터에는 실패한 사이트와 동일한 SQL Server 구성이 있어야 합니다.
  -   보조 사이트 복구 시에는 컴퓨터에 SQL Server Express가 아직 설치되어 있지 않더라도 Configuration Manager에서 SQL Server Express를 설치하지 않습니다.
  -   실패 전 보조 사이트 데이터베이스에 사용한 버전과 인스턴스의 SQL Server를 동일하게 사용해야 합니다.

### <a name="to-recover-a-secondary-site"></a>보조 사이트를 복구하려면
보조 사이트를 복구하려면 Configuration Manager 콘솔의 **사이트** 노드에서 **보조 사이트 복구** 작업을 사용합니다. 중앙 관리 사이트 또는 기본 사이트에 대한 복구와 달리, 보조 사이트에 대한 복구에서는 백업 파일을 사용하지 않고 대신 실패한 보조 사이트 컴퓨터에 보조 사이트 파일을 다시 설치합니다. 사이트가 다시 설치되면 보조 사이트 데이터가 부모 기본 사이트의 데이터로 다시 초기화됩니다.

복구 프로세스 중에 Configuration Manager는 보조 사이트 컴퓨터에 콘텐츠 라이브러리가 존재하고 해당 콘텐츠를 사용할 수 있는지 확인합니다. 해당 콘텐츠가 있으면 보조 사이트에서 기존 콘텐츠 라이브러리를 사용합니다. 그렇지 않은 경우 복구된 보조 사이트의 콘텐츠 라이브러리를 복구하려면 복구된 해당 사이트에 콘텐츠를 다시 배포하거나 사전 준비해야 합니다.

보조 사이트에 없는 배포 지점의 경우 보조 사이트 복구 시 배포 지점을 다시 설치할 필요가 없습니다. 보조 사이트 복구 후에 사이트가 배포 지점과 자동으로 동기화됩니다.

Configuration Manager 콘솔의 **사이트** 노드에서 **설치 상태 표시** 작업을 사용하여 보조 사이트 복구 상태를 확인할 수 있습니다.
