---
title: 사이트 백업
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 장애 또는 데이터 손실이 발생하기 전에 사이트를 백업하는 방법을 알아봅니다.
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b69789fe6e685e2fe42c260e50329f85f2eb421e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32350768"
---
# <a name="back-up-a-configuration-manager-site"></a>Configuration Manager 사이트 백업

*적용 대상: System Center Configuration Manager(현재 분기)*

데이터 손실을 방지하려면 백업 및 복구 방법을 준비합니다. Configuration Manager 사이트의 백업 및 복구 방법을 사용하면 데이터 손실을 최소화하면서 사이트 및 계층 구조를 더 신속하게 복구할 수 있습니다.  

이 항목의 섹션은 사이트 백업에 도움을 줍니다. 사이트를 복구하려면 [Configuration Manager 복구](/sccm/protect/understand/recover-sites)를 참조하세요.  

## <a name="considerations-before-creating-a-backup"></a>백업 전 고려 사항  
-   **SQL Server Always On 가용성 그룹을 사용하여 사이트 데이터베이스를 호스트하는 경우:**[SQL Server Always On 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-backup)에 설명된 대로 백업 및 복구 계획을 수정합니다.

-   Configuration Manager는 Configuration Manager 백업 유지 관리 작업 또는 다른 프로세스를 사용하여 만든 사이트 데이터베이스 백업에서 사이트 데이터베이스를 복구할 수 있습니다.   

    예를 들어 Microsoft SQL Server 유지 관리 계획의 일환으로 만든 백업에서 사이트 데이터베이스를 복원할 수 있습니다. 또한 DPM(Data Protection Manager)으로 만든 백업을 사용하여 사이트 데이터베이스를 백업할 수도 있습니다(DPM).

####  <a name="using-data-protection-manager-to-back-up-your-site-database"></a>Data Protection Manager를 사용하여 사이트 데이터베이스 백업
System Center 2012 Data Protection Manager(DPM)를 사용하여 사이트 데이터베이스를 백업할 수 있습니다.

DPM에서 사이트 데이터베이스 컴퓨터에 대한 새 보호 그룹을 만들어야 합니다. 새 보호 그룹 만들기 마법사의 **그룹 구성원 선택** 페이지에서 데이터 원본 목록으로부터 SMS 작성기 서비스를 선택한 다음 사이트 데이터베이스를 적절한 구성원으로 선택합니다. DPM을 사용하여 사이트 데이터베이스를 백업하는 방법에 대한 자세한 내용은 TechNet의 [Data Protection Manager 문서 라이브러리](http://go.microsoft.com/fwlink/?LinkId=272772) 를 참조하세요.  

> [!IMPORTANT]  
>  Configuration Manager는 명명된 인스턴스를 사용하는 SQL Server 클러스터에 대한 DPM 백업을 지원하지 않지만 SQL Server의 기본 인스턴스를 사용하는 SQL Server 클러스터에 대한 DPM 백업은 지원합니다.  

 사이트 데이터베이스를 복원한 후에는 설치 프로그램의 단계를 따라 사이트를 복구합니다. Data Protection Manager를 사용하여 복구한 사이트 데이터베이스를 사용하려면 **수동으로 복구된 사이트 데이터베이스 사용** 복구 옵션을 선택합니다.  

## <a name="backup-maintenance-task"></a>백업 유지 관리 작업
미리 정의된 백업 사이트 서버 유지 관리 작업을 예약하여 Configuration Manager 사이트에 대한 백업을 자동화할 수 있습니다. 수행할 작업:

-   일정에 따라 실행
-   사이트 데이터베이스 백업
-   특정 레지스트리 키 백업
-   특정 폴더 및 파일 백업
-   [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder) 백업   

최소한 5일마다 기본 사이트 백업 작업을 실행하도록 계획합니다. 이는 Configuration Manager에서 *SQL Server 변경 내용 추적 보존 기간*으로 5일을 사용하기 때문입니다.  (사이트 복구 항목에서 [SQL Server 변경 내용 추적 보존 기간](/sccm/protect/understand/recover-sites#bkmk_SQLretention)을 참조하세요.)

백업 프로세스를 간소화하기 위해 **AfterBackup.bat** 파일을 만들어 백업 유지 관리 작업을 실행한 다음 백업 후 작업을 자동으로 수행할 수 있습니다. AfterBackup.bat 파일은 백업 스냅숏을 안전한 위치에 보관하기 위한 용도로 일반적으로 사용됩니다. AfterBackup.bat 파일을 사용하여 백업 폴더에 파일을 복사하고 다른 추가 백업 작업을 시작할 수도 있습니다.  

중앙 관리 사이트와 기본 사이트를 백업할 수 있지만 보조 사이트 또는 사이트 시스템 서버에 대한 백업은 지원되지 않습니다.

Configuration Manager 백업 서비스가 실행될 때 이 서비스는 백업 제어 파일(**&lt;Configuration Manager 설치 폴더\>\Inboxes\Smsbkup.box\Smsbkup.ctl**)에 정의된 지침을 따릅니다. 백업 제어 파일을 수정하여 백업 서비스의 동작을 변경할 수 있습니다.  

사이트 백업 상태 정보는 **Smsbkup.log** 파일에 기록됩니다. 이 파일은 백업 사이트 서버 유지 관리 작업 속성에서 지정한 대상 폴더에 만들어집니다.  

#### <a name="to-enable-the-site-backup-maintenance-task"></a>사이트 백업 유지 관리 작업을 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 엽니다.  

2.  사이트 백업 유지 관리 작업을 사용하도록 설정할 사이트를 선택합니다.  

3.  **홈** 탭의 **설정** 그룹에서 **사이트 유지 관리 작업**을 선택합니다.  

4.  **백업 사이트 서버**  >  **편집**을 선택합니다.  

5.  **이 작업 사용** > **경로 설정**을 선택하여 백업 대상을 지정합니다. 다음과 같은 옵션을 선택할 수 있습니다.  

    > [!IMPORTANT]  
    >  백업 파일의 변조를 방지하도록 파일을 안전한 위치에 저장해야 합니다. 가장 안전한 백업 경로는 폴더에 대한 NTFS 파일 시스템 사용 권한을 설정할 수 있는 로컬 드라이브입니다. Configuration Manager는 백업 경로에 저장된 백업 데이터를 암호화하지 않습니다.  

    -   **사이트 서버의 사이트 데이터 및 데이터베이스용 로컬 드라이브**: 사이트와 사이트 데이터베이스의 백업 파일을 사이트 서버의 로컬 디스크 드라이브의 지정된 경로에 저장하도록 지정합니다. 백업 작업이 실행되기 전에 로컬 폴더를 만들어야 합니다. 사이트 서버의 로컬 시스템 계정에 사이트 서버 백업의 로컬 폴더에 대한 **쓰기** NTFS 파일 시스템 권한이 있어야 합니다. SQL Server를 실행하는 컴퓨터의 로컬 시스템 계정에 사이트 데이터베이스 백업 폴더에 대한 **쓰기** NTFS 권한이 있어야 합니다.  

    -   **사이트 데이터 및 데이터베이스의 네트워크 경로(UNC 이름)**: 사이트와 사이트 데이터베이스의 백업 파일이 지정된 UNC 경로에 저장되도록 지정합니다. 백업 작업이 실행되기 전에 공유를 만들어야 합니다. 사이트 서버의 컴퓨터 계정과 SQL Server의 컴퓨터 계정(SQL Server가 다른 컴퓨터에 설치되어 있는 경우)에 공유 네트워크 폴더에 대한 **쓰기** NTFS 및 공유 권한이 있어야 합니다.  

    -   **사이트 서버 및 SQL Server의 로컬 드라이브**: 사이트의 백업 파일이 사이트 서버의 로컬 드라이브의 지정된 경로에 저장되고 사이트 데이터베이스의 백업 파일이 사이트 데이터베이스 서버의 로컬 드라이브의 지정된 경로에 저장되도록 지정합니다. 백업 작업이 실행되기 전에 로컬 폴더를 만들어야 합니다. 사이트 서버의 컴퓨터 계정에 사이트 서버에서 만든 폴더에 대한 **쓰기** NTFS 권한이 있어야 합니다. SQL Server의 컴퓨터 계정에 사이트 데이터베이스 서버에서 만든 폴더에 대한 **쓰기** NTFS 권한이 있어야 합니다. 이 옵션은 사이트 데이터베이스가 사이트 서버에 설치되지 않은 경우에만 사용할 수 있습니다.  

    > [!NOTE]  
    >   백업 대상을 찾는 옵션은 백업 대상의 UNC 경로를 지정하는 경우에만 사용할 수 있습니다.

    > 백업 대상으로 사용되는 폴더 이름 또는 공유 이름은 유니코드 문자 사용을 지원하지 않습니다.  

6.  사이트 백업 작업의 일정을 구성합니다. 모범 사례에 따라 업무 외 시간으로 백업 일정을 정하는 것이 좋습니다. 계층이 있는 경우 사이트 장애 시 데이터를 최대한 보존할 수 있도록 일주일에 두 번 이상 실행되는 일정을 정하는 것이 좋습니다.  

    백업을 위해 구성한 사이트 서버에서 Configuration Manager 콘솔을 실행하는 경우 백업 사이트 서버 유지 관리 작업에서 현지 시간이 일정에 사용됩니다. 백업을 위해 구성한 사이트로부터 원격에 있는 컴퓨터에서 Configuration Manager 콘솔을 실행하는 경우 백업 사이트 서버 유지 관리 작업에서 UTC가 일정에 사용됩니다.  

7.  사이트 백업 작업이 실패할 경우 경고를 생성할지 여부를 선택하고 **확인**을 클릭한 다음 **확인**을 클릭합니다. 경고를 생성하도록 선택한 경우 Configuration Manager에서 백업 실패에 대한 중요한 경고를 생성하며, 이를 **모니터링** 작업 영역의 **경고** 노드에서 검토할 수 있습니다.  

 다음으로 백업 사이트 서버 유지 관리 작업이 실행 중인지 확인합니다. 백업이 만들어지고 있어야 합니다.  

#### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>백업 사이트 서버 유지 관리 작업이 실행되고 있는지 확인하려면  
다음을 검토하여 사이트 백업 유지 관리 작업이 실행되고 있는지 확인합니다.  

-   작업에서 만든 백업 대상 폴더에 있는 파일의 타임스탬프를 확인합니다. 타임스탬프가 작업이 실행되도록 마지막으로 예약된 시간과 일치하는 시간으로 업데이트되었는지 확인합니다.  

-   **모니터링** 작업 영역의 **구성 요소 상태** 노드에서 SMS_SITE_BACKUP의 상태 메시지를 검토합니다. 사이트 백업이 성공적으로 완료되면 사이트 백업이 오류 없이 완료되었음을 나타내는 메시지 ID 5035가 표시됩니다.  

-   백업이 실패할 경우 경고를 생성하도록 백업 사이트 서버 유지 관리 작업이 구성된 경우 **모니터링** 작업 영역의 **경고** 노드에서 백업 실패 여부를 확인합니다.  

-   &lt;Configuration Manager 설치 폴더>\Logs에서 Smsbkup.log를 검토하여 경고와 오류를 확인합니다. 사이트 백업이 성공적으로 완료되면 타임스탬프 및 메시지 ID `Backup completed` 와 함께 `STATMSG: ID=5035`가 표시됩니다.  

    > [!TIP]  
    >  백업 유지 관리 작업이 실패할 경우 SMS_SITE_BACKUP 서비스를 중지하고 다시 시작하여 백업 작업을 다시 시작할 수 있습니다.  

## <a name="archive-the-backup-snapshot"></a>백업 스냅숏 보관  
백업 사이트 서버 유지 관리 작업이 처음으로 실행될 때 백업 스냅숏이 만들어지며, 장애 시 이를 사용하여 사이트 서버를 복구할 수 있습니다. 이후 주기에서 백업 작업이 다시 실행될 때에는 새 백업 스냅숏이 만들어져 이전 스냅숏을 덮어씁니다. 따라서 사이트에 백업 스냅숏이 하나만 있게 되며 이전 백업 스냅숏을 찾아오는 방법이 없습니다.  

다음과 같은 이유로 백업 스냅숏은 여러 보관본을 유지하는 것이 좋습니다.  

-   백업 미디어에 오류가 발생하고 백업 일부만 저장되거나, 백업 미디어가 잘못 배치되는 것은 흔한 일입니다. 실패한 독립 실행형 기본 사이트를 복구할 때 아무런 백업 없이 복구하는 것보다는 이전 백업에서 복구하는 편이 더 낫습니다. 계층 내 사이트 서버의 경우 백업은 SQL Server 변경 내용 추적 보존 기간 안에 있어야 하며, 그렇지 않으면 해당 백업은 필요가 없습니다.  

-   사이트 손상은 백업 주기가 수 회 경과하더라도 검색되지 않을 수 있습니다. 사이트가 손상되기 전의 백업 스냅숏을 사용해야 할 수 있습니다. 이 방법은 백업이 SQL Server 변경 내용 추적 보존 기간 내에 있는 독립 실행형 기본 사이트 및 계층 내 사이트에 적용됩니다.  

-   백업 사이트 서버 유지 관리 작업이 실패할 경우와 같이 사이트에 백업 스냅숏이 전혀 없을 수도 있습니다. 백업 작업은 현재 데이터의 백업을 시작하기 전에 이전의 백업 스냅숏을 제거하므로, 그와 같은 경우에는 유효한 백업 스냅숏이 존재하지 않을 것입니다.  

## <a name="using-the-afterbackupbat-file"></a>AfterBackup.bat 파일 사용  
사이트를 백업한 후 백업 사이트 서버 작업에서는 AfterBackup.bat라는 파일을 자동으로 실행합니다. AfterBackup.bat 파일은 &lt;Configuration Manager 설치 폴더>\Inboxes\Smsbkup에서 수동으로 만들어야 합니다. AfterBackup.bat 파일이 이미 올바른 폴더 안에 저장되어 있는 경우 백업 작업이 완료된 후 자동으로 실행됩니다.

AfterBackup.bat 파일을 활용하면 백업 작업이 끝날 때마다 백업 스냅숏을 보관할 수 있고 백업 사이트 서버 유지 관리 작업에 속하지 않는 기타 백업 후 작업을 자동으로 수행할 수 있습니다. AfterBackup.bat 파일에 의해 보관 및 백업 작업이 통합되므로 새로운 백업 스냅숏은 모두 보관됩니다.

AfterBackup.bat 파일이 없으면 백업 작업은 이 파일을 건너뛰며 백업 과정은 아무런 영향도 받지 않습니다. 사이트 백업 작업에서 AfterBackup.bat 파일을 성공적으로 실행했는지 확인하려면 **모니터링** 작업 영역에서 **구성 요소 상태** 노드를 확인하여 SMS_SITE_BACKUP에 대한 상태 메시지를 검토하세요. AfterBackup.bat 명령 파일이 성공적으로 시작된 경우 메시지 ID 5040이 표시됩니다.  

> [!TIP]  
>  사이트 서버 백업 파일을 보관할 AfterBackup.bat 파일을 만들려면 해당 배치 파일에서 [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408)와 같은 복사 명령 도구를 사용해야 합니다. 예를 들어 AfterBackup.bat 파일을 만든 후 첫 번째 줄에 다음과 같은 내용을 추가하면 됩니다. `Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR`  

 AfterBackup.bat 파일의 용도는 백업 스냅숏을 보관하는 것이지만, 백업 작업이 끝날 때마다 추가 작업을 수행할 목적으로 AfterBackup.bat 파일을 만들 수도 있습니다.  

##  <a name="supplemental-backup-tasks"></a>추가 백업 작업  
백업 사이트 서버 유지 관리 작업은 사이트 서버 파일 및 사이트 데이터베이스에 대한 백업 스냅숏을 제공하지만, 백업되지 않는 기타 항목도 존재하기 마련이며 이는 백업 전략을 수립할 때 반드시 고려해야 합니다. 다음 섹션의 내용을 사용하여 Configuration Manager 백업 전략을 완료할 수 있습니다.  

### <a name="back-up-custom-reporting-services-reports"></a>사용자 지정 Reporting Services 보고서 백업  
미리 정의하거나 만든 사용자 지정 Reporting Services 보고서를 수정한 경우, 보고서 서버 데이터베이스 파일의 백업을 만드는 작업은 백업 전략에서 중요한 부분을 차지합니다. 보고서 서버 백업에는 보고서 및 모델에 대한 원본 파일, 암호화 키, 사용자 지정 어셈블리 또는 확장, 구성 파일, 사용자 지정 보고서에 사용되는 사용자 지정 SQL Server 뷰, 사용자 지정 저장 프로시저 등의 백업이 포함되어야 합니다.  

> [!IMPORTANT]  
>  Configuration Manager가 새 버전으로 업데이트되면 새 보고서가 미리 정의된 보고서를 덮어쓸 수 있습니다. 미리 정의된 보고서를 수정하는 경우 보고서를 백업한 다음 Reporting Services에서 보고서를 복원합니다.  

 Reporting Services에서 사용자 지정 보고서를 백업하는 방법에 대한 자세한 내용은 SQL Server 2014 온라인 설명서에서 [Reporting Services 설치에 대한 백업 및 복원 작업](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) 을 참조하세요.  

### <a name="back-up-content-files"></a>콘텐츠 파일 백업  
Configuration Manager의 콘텐츠 라이브러리는 소프트웨어 업데이트, 응용 프로그램, 운영 체제 배포 등에 대한 모든 콘텐츠 파일이 저장되는 위치입니다. 콘텐츠 라이브러리는 사이트 서버와 각 배포 지점에 위치합니다. 백업 사이트 서버 유지 관리 작업에는 콘텐츠 라이브러리 또는 패키지 원본 파일에 대한 백업이 포함되어 있지 않습니다. 사이트 서버가 작업에 실패하면 콘텐츠 라이브러리 파일 관련 정보는 사이트 데이터베이스에 복원되지만, 사이트 서버에 콘텐츠 라이브러리와 패키지 원본 파일을 복원해야 합니다.  

-   **콘텐츠 라이브러리**: 콘텐츠를 배포 지점에 재배포하려면 먼저 콘텐츠 라이브러리를 복원해야 합니다. 콘텐츠 재배포가 시작되면 Configuration Manager는 사이트 서버에 있는 콘텐츠 라이브러리의 파일을 배포 지점에 복사합니다. 사이트 서버에 대한 콘텐츠 라이브러리는 SCCMContentLib 폴더 안에 있으며 이 폴더는 보통 사이트가 설치된 시점에 사용 가능한 디스크 공간이 가장 많은 드라이브에 있습니다.  

-   **패키지 원본 파일**: 배포 지점에서 콘텐츠를 업데이트하려면 먼저 패키지 원본 파일을 복원해야 합니다. 콘텐츠 업데이트가 시작되면 Configuration Manager는 패키지 원본에서 새 파일 또는 수정된 파일을 콘텐츠 라이브러리에 복사하고, 곧이어 해당 파일은 연결된 배포 지점에 복사됩니다. SQL Server에서 다음 쿼리를 실행하면 모든 패키지 및 응용 프로그램에 대한 패키지 원본 위치를 검색할 수 있습니다. `SELECT * FROM v_Package` 패키지 ID의 처음 세 문자를 보면 패키지 원본 사이트를 식별할 수 있습니다. 예를 들어 패키지 ID가 CEN00001이면 원본 사이트의 사이트 코드는 CEN입니다. 패키지 원본 파일을 복원할 때는 해당 파일을 실패 전에 있었던 위치로 복원해야 합니다.  

 사이트 서버에 대한 파일 시스템 백업에 콘텐츠 라이브러리 및 패키지 원본 위치가 모두 포함되어 있는지 확인하세요.  

### <a name="back-up-custom-software-updates"></a>사용자 지정 소프트웨어 업데이트 백업  
 독립 실행형 도구인 System Center Updates Publisher 2011을 사용하면 사용자 지정 소프트웨어 업데이트를 WSUS(Windows Server Update Services)에 게시하고, 소프트웨어 업데이트를 Configuration Manager에 동기화하고, 소프트웨어 업데이트 호환성을 평가하고, 사용자 지정 소프트웨어 업데이트를 클라이언트에 배포할 수 있습니다. Updates Publisher는 해당 소프트웨어 업데이트 리포지토리에 로컬 데이터베이스를 사용합니다. Updates Publisher를 사용하여 사용자 지정 소프트웨어 업데이트를 관리하는 경우 백업 계획에 Updates Publisher 데이터베이스를 포함해야 할지 여부를 결정합니다. Updates Publisher에 대한 자세한 내용은 System Center TechCenter 라이브러리에서 [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) 을 참조하세요.  

 다음 절차를 사용하여 Updates Publisher 데이터베이스를 백업합니다.  

#### <a name="to-back-up-the-updates-publisher-2011-database"></a>Updates Publisher 2011 데이터베이스를 백업하려면  

1.  Updates Publisher가 실행되는 컴퓨터의 %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\에서 Updates Publisher 데이터베이스 파일(Scupdb.sdf)을 찾습니다. Updates Publisher를 실행하는 각 사용자에 대해 서로 다른 데이터베이스 파일이 있습니다.  

2.  데이터베이스 파일을 백업 대상에 복사합니다. 예를 들어 백업 대상이 E:\ConfigMgr_Backup인 경우 Updates Publisher 데이터베이스 파일을 E:\ConfigMgr_Backup\SCUP2011에 복사하면 됩니다.  

    > [!TIP]  
    >  컴퓨터에 데이터베이스 파일이 둘 이상 있을 경우 해당 데이터베이스 파일이 연결된 사용자 프로필을 나타내는 하위 폴더에 파일을 저장하는 것을 고려하세요. 예를 들어, 데이터베이스 파일 하나를 E:\ConfigMgr_Backup\SCUP2011\User1에 저장하고 다른 데이터베이스 파일은 E:\ConfigMgr_Backup\SCUP2011\User2에 저장할 수 있습니다.  

## <a name="user-state-migration-data"></a>사용자 환경 마이그레이션 데이터  
Configuration Manager 작업 순서를 사용하면 현재 운영 체제의 사용자 상태를 보존하려는 운영 체제 배포 시나리오에서 사용자 상태 데이터를 캡처 및 복원할 수 있습니다. 사용자 상태 데이터를 저장하는 폴더는 상태 마이그레이션 지점의 속성에 나열됩니다. 이 사용자 환경 마이그레이션 데이터는 사이트 서버 백업 유지 관리 작업의 일부로 백업되지 않습니다. 백업 계획의 일부로, 사용자 환경 마이그레이션 데이터를 저장하도록 지정한 폴더를 수동으로 백업해야 합니다.   

### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>사용자 환경 마이그레이션 데이터 저장에 사용되는 폴더 결정  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 선택합니다.  

3.  상태 마이그레이션 역할을 호스트하는 사이트 시스템을 선택한 다음 **사이트 시스템 역할**에서 **상태 마이그레이션 지점**을 선택합니다.  


4.  **사이트 역할** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  
5.  사용자 환경 마이그레이션 데이터를 저장하는 폴더는 **일반** 탭의 **폴더 세부 정보** 섹션에 나열됩니다.  



## <a name="about-the-sms-writer-service"></a>SMS 작성기 서비스 정보  
SMS 작성기는 백업 과정에서 VSS(볼륨 섀도 복사본 서비스)와 상호 작용하는 서비스입니다. Configuration Manager 사이트 백업이 성공적으로 완료되려면 SMS 작성기 서비스가 실행되어야 합니다.  

### <a name="purpose"></a>용도  
SMS 작성기는 VSS 서비스에 등록되어 VSS 서비스 인터페이스 및 이벤트에 바인딩됩니다. VSS가 이벤트를 브로드캐스팅하는 경우, 즉 SMS 작성기에 특정 알림을 보내는 경우 SMS 작성기가 알림에 응답하여 적절한 조치를 취합니다. SMS 작성기는 &lt;*Configuration Manager 설치 경로*>\inboxes\smsbkup.box에 있는 백업 제어 파일(smsbkup.ctl)을 읽고 백업할 파일과 데이터를 결정합니다. SMS 작성기는 이 정보와 함께 SMS 레지스트리 키 및 하위 키의 특정 데이터를 기반으로 다양한 구성 요소로 이루어진 메타데이터를 작성합니다. 그리고 요청 시 VSS에 메타데이터를 보냅니다. 그러면 VSS가 요청하는 응용 프로그램(Configuration Manager 백업 관리자)에 메타데이터를 전송합니다. 백업 관리자는 백업되는 데이터를 선택한 후 이 데이터를 VSS를 통해 SMS 작성기에 보냅니다. SMS 작성기는 적절한 단계를 수행하여 백업을 준비합니다. 이후에 VSS가 스냅숏을 생성할 준비가 되면 이벤트를 보냅니다. 그러면 SMS 작성기가 모든 Configuration Manager 서비스를 중지하여 스냅숏이 생성되는 동안 Configuration Manager 작업이 고정되도록 보장합니다. 스냅숏이 완료된 후에 SMS 작성기는 서비스와 작업을 다시 시작합니다.  

SMS 작성기 서비스는 자동으로 설치됩니다. VSS 응용 프로그램이 백업 또는 복원을 요청할 때 이 서비스가 실행되고 있어야 합니다.  

### <a name="writer-id"></a>작성기 ID  
SMS 작성기의 작성기 ID는 03ba67dd-dc6d-4729-a038-251f7018463b입니다.  

### <a name="permissions"></a>사용 권한  
SMS 작성기 서비스는 로컬 시스템 계정으로 실행되어야 합니다.  

### <a name="volume-shadow-copy-service"></a>볼륨 섀도 복사본 서비스  
VSS는 시스템의 응용 프로그램이 볼륨에 쓰기를 계속하는 동안 볼륨 백업이 수행될 수 있도록 하는 프레임워크를 구현하는 일련의 COM API입니다. VSS는 디스크에 데이터를 업데이트하는 사용자 응용 프로그램(SMS 작성기 서비스)과 응용 프로그램을 백업하는 사용자 응용 프로그램(백업 관리자 서비스) 간에 조정이 이루어질 수 있도록 일관된 인터페이스를 제공합니다. 자세한 내용은 Windows Server TechCenter의 [볼륨 섀도 복사본 서비스](http://go.microsoft.com/fwlink/p/?LinkId=241968) 항목을 참조하세요.  

## <a name="next-steps"></a>다음 단계
백업을 만든 후 해당 백업으로 [사이트 복구](/sccm/protect/understand/recover-sites)를 연습해봅니다. 이렇게 하면 복구 프로세스에 미리 익숙해지고 원할 때 백업을 성공적으로 수행할 수 있게 됩니다.  
