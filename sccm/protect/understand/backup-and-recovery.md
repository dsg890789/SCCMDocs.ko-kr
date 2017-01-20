---
title: "백업 및 복구 | Microsoft 문서"
description: "System Center Configuration Manager에서 사이트를 백업하고 장애 또는 데이터 손실이 발생할 경우 복구하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 828e2ac9a3f9bcea1571d24145a1021fdf1091f3
ms.openlocfilehash: ce73be3a9fa3876c587bbd7b7cb05acd36c2687e


---
# <a name="backup-and-recovery-for-system-center-configuration-manager"></a>System Center Configuration Manager 백업 및 복구

*적용 대상: System Center Configuration Manager(현재 분기)*

데이터 손실을 방지하려면 백업 및 복구 방법을 준비합니다. Configuration Manager 사이트의 백업 및 복구 방법을 사용하면 데이터 손실을 최소화하면서 사이트 및 계층 구조를 더 신속하게 복구할 수 있습니다. 이 항목의 섹션에서는 사이트를 백업하고 장애 또는 데이터 손실이 발생할 경우 사이트를 복구하는 방법을 설명합니다.  

-   [Configuration Manager 사이트 백업](#BKMK_SiteBackup)  

    -   [백업 유지 관리 작업](#BKMK_BackupMaintenanceTask)  

    -   [Data Protection Manager를 사용하여 사이트 데이터베이스 백업](#BKMK_DPMBackup)  

    -   [백업 스냅숏 보관](#BKMK_ArchivingBackupSnapshot)  

    -   [AfterBackup.bat 파일 사용](#BKMK_UsingAfterBackup)  

    -   [추가 백업 작업](#BKMK_SupplementalBackup)  

-   [Configuration Manager 사이트 복구](#BKMK_RecoverSite)  

    -   [복구 옵션 결정](#BKMK_DetermineRecoveryOptions)  

        -   [사이트 서버 복구 옵션](#BKMK_SiteServerRecoveryOptions)  

        -   [사이트 데이터베이스 복구 옵션](#BKMK_SiteDatabaseRecoveryOption)  

        -   [SQL Server 변경 내용 추적 보존 기간](#bkmk_SQLretention)  

        -   [사이트 또는 글로벌 데이터를 다시 초기화하는 프로세스](#bkmk_reinit)  

        -   [사이트 데이터베이스 복구 시나리오](#BKMK_SiteDBRecoveryScenarios)  

    -   [무인 사이트 복구 스크립트 파일 키](#BKMK_UnattendedSiteRecoveryKeys)  

    -   [복구 후 작업](#BKMK_PostRecovery)  

    -   [보조 사이트 복구](#BKMK_RecoverSecondarySite)  

-   [SMS 작성기 서비스](#BKMK_SMSWriterService)  

> [!NOTE]  
>  SQL Server AlwaysOn 가용성 그룹을 사용하여 사이트 데이터베이스를 호스트하는 경우 [System Center Configuration Manager용 항상 사용 가능한 사이트 데이터베이스를 위한 SQL Server AlwaysOn](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md) 항목의 [SQL Server AlwaysOn 가용성 그룹을 사용하는 경우 백업 및 복구의 변경 내용](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md#bkmk_BnR) 섹션에 설명된 대로 백업 및 복구 계획을 수정하세요.  

##  <a name="a-namebkmksitebackupa-back-up-a-configuration-manager-site"></a><a name="BKMK_SiteBackup"></a> Configuration Manager 사이트 백업  
 Configuration Manager에는 다음과 같은 백업 유지 관리 작업이 있습니다.  

-   일정에 따라 실행  

-   사이트 데이터베이스 백업  

-   특정 레지스트리 키 백업  

-   특정 폴더 및 파일 백업  

-   **CD.Latest** 폴더 백업([System Center Configuration Manager의 CD.Latest 폴더](../../core/servers/manage/the-cd.latest-folder.md) 참조)  

 최소한 5일마다 기본 사이트 백업 작업을 실행하도록 계획합니다. 이는 Configuration Manager에서 [SQL Server 변경 내용 추적 보존 기간](#bkmk_SQLretention)으로 5일을 사용하기 때문입니다.  

 백업 프로세스를 간소화하기 위해 **AfterBackup.bat** 파일을 만들어 백업 유지 관리 작업을 실행한 다음 백업 후 작업을 자동으로 수행할 수 있습니다. AfterBackup.bat 파일은 백업 스냅숏을 안전한 위치에 보관하기 위한 용도로 일반적으로 사용됩니다. AfterBackup.bat 파일을 사용하여 백업 폴더에 파일을 복사하고 다른 추가 백업 작업을 시작할 수도 있습니다.

다음 섹션의 내용을 참조하여 Configuration Manager 백업 전략을 만들 수 있습니다.  

> [!NOTE]  
>  Configuration Manager는 Configuration Manager 백업 유지 관리 작업 또는 다른 프로세스를 사용하여 만든 사이트 데이터베이스 백업에서 사이트 데이터베이스를 복구할 수 있습니다. 예를 들어 Microsoft SQL Server 유지 관리 계획의 일환으로 만든 백업에서 사이트 데이터베이스를 복원할 수 있습니다. System Center 2012 DPM(Data Protection Manager)을 사용하여 만든 백업에서 사이트 데이터베이스를 복원할 수 있습니다. 자세한 내용은 [Data Protection Manager를 사용하여 사이트 데이터베이스 백업](#BKMK_DPMBackup)을 참조하세요.  

###  <a name="a-namebkmkbackupmaintenancetaska-backup-maintenance-task"></a><a name="BKMK_BackupMaintenanceTask"></a> 백업 유지 관리 작업  
 미리 정의된 백업 사이트 서버 유지 관리 작업을 예약하여 Configuration Manager 사이트에 대한 백업을 자동화할 수 있습니다. 중앙 관리 사이트와 기본 사이트를 백업할 수 있지만 보조 사이트 또는 사이트 시스템 서버에 대한 백업은 지원되지 않습니다. Configuration Manager 백업 서비스가 실행될 때 이 서비스는 백업 제어 파일(**<ConfigMgrInstallationFolder\>\Inboxes\Smsbkup.box\Smsbkup.ctl**)에 정의된 지침을 따릅니다. 백업 제어 파일을 수정하여 백업 서비스의 동작을 변경할 수 있습니다. 사이트 백업 상태 정보는 **Smsbkup.log** 파일에 기록됩니다. 이 파일은 백업 사이트 서버 유지 관리 작업 속성에서 지정한 대상 폴더에 만들어집니다.  


##### <a name="to-enable-the-site-backup-maintenance-task"></a>사이트 백업 유지 관리 작업을 사용하도록 설정하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성**을 엽니다.  

     \> **사이트**.  

2.  사이트 백업 유지 관리 작업을 사용하도록 설정할 사이트를 선택합니다.  

3.  **홈** 탭의 **설정** 그룹에서 **사이트 유지 관리 작업**을 선택합니다.  

4.  **백업 사이트 서버**  >  **편집**을 선택합니다.  

5.  **이 작업 사용** > **경로 설정**을 선택하여 백업 대상을 지정합니다. 다음과 같은 옵션을 선택할 수 있습니다.  

    > [!IMPORTANT]  
    >  백업 파일의 변조를 방지하도록 파일을 안전한 위치에 저장해야 합니다. 가장 안전한 백업 경로는 폴더에 대한 NTFS 파일 시스템 사용 권한을 설정할 수 있는 로컬 드라이브입니다. Configuration Manager는 백업 경로에 저장된 백업 데이터를 암호화하지 않습니다.  

    -   **사이트 서버의 사이트 데이터 및 데이터베이스용 로컬 드라이브**: 사이트와 사이트 데이터베이스의 백업 파일을 사이트 서버의 로컬 디스크 드라이브의 지정된 경로에 저장하도록 지정합니다. 백업 작업이 실행되기 전에 로컬 폴더를 만들어야 합니다.   사이트 서버의 로컬 시스템 계정에 사이트 서버 백업의 로컬 폴더에 대한 **쓰기** NTFS 파일 시스템 권한이 있어야 합니다. SQL Server를 실행하는 컴퓨터의 로컬 시스템 계정에 사이트 데이터베이스 백업 폴더에 대한 **쓰기** NTFS 권한이 있어야 합니다.  

    -   **사이트 데이터 및 데이터베이스의 네트워크 경로(UNC 이름)**: 사이트와 사이트 데이터베이스의 백업 파일이 지정된 UNC 경로에 저장되도록 지정합니다. 백업 작업을 실행하기 전에 공유를 만들어야 합니다. 사이트 서버의 컴퓨터 계정과 SQL Server의 컴퓨터 계정(SQL Server가 다른 컴퓨터에 설치되어 있는 경우)에 공유 네트워크 폴더에 대한 **쓰기** NTFS 및 공유 권한이 있어야 합니다.  

    -   **사이트 서버 및 SQL Server의 로컬 드라이브**: 사이트의 백업 파일이 사이트 서버의 로컬 드라이브의 지정된 경로에 저장되고 사이트 데이터베이스의 백업 파일이 사이트 데이터베이스 서버의 로컬 드라이브의 지정된 경로에 저장되도록 지정합니다. 백업 작업이 실행되기 전에 로컬 폴더를 만들어야 합니다. 사이트 서버의 컴퓨터 계정에 사이트 서버에서 만든 폴더에 대한 **쓰기** NTFS 권한이 있어야 합니다. SQL Server의 컴퓨터 계정에 사이트 데이터베이스 서버에서 만든 폴더에 대한 **쓰기** NTFS 권한이 있어야 합니다. 이 옵션은 사이트 데이터베이스가 사이트 서버에 설치되지 않은 경우에만 사용할 수 있습니다.  

    > [!NOTE]  
    >   - 백업 대상을 찾는 옵션은 백업 대상의 UNC 경로를 지정하는 경우에만 사용할 수 있습니다.

    > - 백업 대상으로 사용되는 폴더 이름 또는 공유 이름은 유니코드 문자 사용을 지원하지 않습니다.  


6.  사이트 백업 작업의 일정을 구성합니다. 모범 사례에 따라 업무 외 시간으로 백업 일정을 정하는 것이 좋습니다. 계층이 있는 경우 사이트 장애 시 데이터를 최대한 보존할 수 있도록 일주일에 두 번 이상 실행되는 일정을 정하는 것이 좋습니다.  

    백업을 위해 구성한 사이트 서버에서 Configuration Manager 콘솔을 실행하는 경우 백업 사이트 서버 유지 관리 작업에서 현지 시간이 일정에 사용됩니다. 백업을 위해 구성한 사이트로부터 원격에 있는 컴퓨터에서 Configuration Manager 콘솔을 실행하는 경우 백업 사이트 서버 유지 관리 작업에서 UTC가 일정에 사용됩니다.  

7.  사이트 백업 작업이 실패할 경우 경고를 생성할지 여부를 선택하고 **확인**을 클릭한 다음 **확인**을 클릭합니다. 경고를 생성하도록 선택한 경우 Configuration Manager에서 백업 실패에 대한 중요한 경고를 생성하며, 이를 **모니터링** 작업 영역의 **경고** 노드에서 검토할 수 있습니다.  

 다음으로 백업 사이트 서버 유지 관리 작업이 실행 중인지 확인합니다. 백업이 만들어지고 있어야 합니다.  

##### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>백업 사이트 서버 유지 관리 작업이 실행되고 있는지 확인하려면  

-   다음을 검토하여 사이트 백업 유지 관리 작업이 실행되고 있는지 확인합니다.  

    -   작업에서 만든 백업 대상 폴더에 있는 파일의 타임스탬프를 확인합니다. 타임스탬프가 작업이 실행되도록 마지막으로 예약된 시간과 일치하는 시간으로 업데이트되었는지 확인합니다.  

    -   **모니터링** 작업 영역의 **구성 요소 상태** 노드에서 SMS_SITE_BACKUP의 상태 메시지를 검토합니다. 사이트 백업이 성공적으로 완료되면 사이트 백업이 오류 없이 완료되었음을 나타내는 메시지 ID 5035가 표시됩니다.  

    -   백업이 실패할 경우 경고를 생성하도록 백업 사이트 서버 유지 관리 작업이 구성된 경우 **모니터링** 작업 영역의 **경고** 노드에서 백업 실패 여부를 확인합니다.  

    -   <*Configuration Manager 설치 폴더*>\Logs에서 Smsbkup.log를 검토하여 경고와 오류를 확인합니다. 사이트 백업이 성공적으로 완료되면 타임스탬프 및 메시지 ID `Backup completed` 와 함께 `STATMSG: ID=5035`가 표시됩니다.  

    > [!TIP]  
    >  백업 유지 관리 작업이 실패할 경우 SMS_SITE_BACKUP 서비스를 중지하고 다시 시작하여 백업 작업을 다시 시작할 수 있습니다.  

###  <a name="a-namebkmkdpmbackupa-using-data-protection-manager-to-back-up-your-site-database"></a><a name="BKMK_DPMBackup"></a> Data Protection Manager를 사용하여 사이트 데이터베이스 백업  
 System Center 2012 Data Protection Manager(DPM)를 사용하여 사이트 데이터베이스를 백업할 수 있습니다. DPM에서 사이트 데이터베이스 컴퓨터에 대한 새 보호 그룹을 만들어야 합니다. 새 보호 그룹 만들기 마법사의 **그룹 구성원 선택** 페이지에서 데이터 원본 목록으로부터 SMS 작성기 서비스를 선택한 다음 사이트 데이터베이스를 적절한 구성원으로 선택합니다. DPM을 사용하여 사이트 데이터베이스를 백업하는 방법에 대한 자세한 내용은 TechNet의 [Data Protection Manager 문서 라이브러리](http://go.microsoft.com/fwlink/?LinkId=272772) 를 참조하세요.  

> [!IMPORTANT]  
>  Configuration Manager는 명명된 인스턴스를 사용하는 SQL Server 클러스터에 대한 DPM 백업을 지원하지 않지만 SQL Server의 기본 인스턴스를 사용하는 SQL Server 클러스터에 대한 DPM 백업은 지원합니다.  

 사이트 데이터베이스를 복원한 후에는 설치 프로그램의 단계를 따라 사이트를 복구합니다. Data Protection Manager를 사용하여 복구한 사이트 데이터베이스를 사용하려면 **수동으로 복구된 사이트 데이터베이스 사용** 복구 옵션을 선택합니다.  

###  <a name="a-namebkmkarchivingbackupsnapshota-archiving-the-backup-snapshot"></a><a name="BKMK_ArchivingBackupSnapshot"></a> 백업 스냅숏 보관  
 백업 사이트 서버 유지 관리 작업이 처음으로 실행될 때 백업 스냅숏이 만들어지며, 장애 시 이를 사용하여 사이트 서버를 복구할 수 있습니다. 이후 주기에서 백업 작업이 다시 실행될 때에는 새 백업 스냅숏이 만들어져 이전 스냅숏을 덮어씁니다. 따라서 사이트에 백업 스냅숏이 하나만 있게 되며 이전 백업 스냅숏을 찾아오는 방법이 없습니다.  

 다음과 같은 이유로 백업 스냅숏은 여러 보관본을 유지하는 것이 좋습니다.  

-   백업 미디어에 오류가 발생하고 백업 일부만 저장되거나, 백업 미디어가 잘못 배치되는 것은 흔한 일입니다. 실패한 독립 실행형 기본 사이트를 복구할 때 아무런 백업 없이 복구하는 것보다는 이전 백업에서 복구하는 편이 더 낫습니다. 계층 내 사이트 서버의 경우 백업은 SQL Server 변경 내용 추적 보존 기간 안에 있어야 하며, 그렇지 않으면 해당 백업은 필요가 없습니다.  

-   사이트 손상은 백업 주기가 수 회 경과하더라도 검색되지 않을 수 있습니다. 사이트가 손상되기 전의 백업 스냅숏을 사용해야 할 수 있습니다. 이 방법은 백업이 SQL Server 변경 내용 추적 보존 기간 내에 있는 독립 실행형 기본 사이트 및 계층 내 사이트에 적용됩니다.  

-   백업 사이트 서버 유지 관리 작업이 실패할 경우와 같이 사이트에 백업 스냅숏이 전혀 없을 수도 있습니다. 백업 작업은 현재 데이터의 백업을 시작하기 전에 이전의 백업 스냅숏을 제거하므로, 그와 같은 경우에는 유효한 백업 스냅숏이 존재하지 않을 것입니다.  

###  <a name="a-namebkmkusingafterbackupa-using-the-afterbackupbat-file"></a><a name="BKMK_UsingAfterBackup"></a> AfterBackup.bat 파일 사용  
 사이트를 백업한 후 백업 사이트 서버 작업에서는 AfterBackup.bat라는 파일을 자동으로 실행합니다. AfterBackup.bat 파일은 <*Configuration Manager 설치 폴더*>\Inboxes\Smsbkup에서 수동으로 만들어야 합니다. AfterBackup.bat 파일이 이미 올바른 폴더 안에 저장되어 있는 경우 백업 작업이 완료된 후 자동으로 실행됩니다. AfterBackup.bat 파일을 활용하면 백업 작업이 끝날 때마다 백업 스냅숏을 보관할 수 있고 백업 사이트 서버 유지 관리 작업에 속하지 않는 기타 백업 후 작업을 자동으로 수행할 수 있습니다. AfterBackup.bat 파일에 의해 보관 및 백업 작업이 통합되므로 새로운 백업 스냅숏은 모두 보관됩니다. AfterBackup.bat 파일이 없으면 백업 작업은 이 파일을 건너뛰며 백업 과정은 아무런 영향도 받지 않습니다. 사이트 백업 작업에서 AfterBackup.bat 파일을 성공적으로 실행했는지 확인하려면 **모니터링** 작업 영역에서 **구성 요소 상태** 노드를 확인하여 SMS_SITE_BACKUP에 대한 상태 메시지를 검토하세요. AfterBackup.bat 명령 파일이 성공적으로 시작된 경우 메시지 ID 5040이 표시됩니다.  

> [!TIP]  
>  사이트 서버 백업 파일을 보관할 AfterBackup.bat 파일을 만들려면 해당 배치 파일에서 Robocopy와 같은 복사 명령 도구를 사용해야 합니다. 예를 들어 AfterBackup.bat 파일을 만든 후 첫 번째 줄에 다음과 같은 내용을 추가하면 됩니다. `Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR` Robocopy에 대한 자세한 내용은 [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408) 명령줄 참조 웹 페이지를 참조하세요.  

 AfterBackup.bat 파일의 용도는 백업 스냅숏을 보관하는 것이지만, 백업 작업이 끝날 때마다 추가 작업을 수행할 목적으로 AfterBackup.bat 파일을 만들 수도 있습니다.  

###  <a name="a-namebkmksupplementalbackupa-supplemental-backup-tasks"></a><a name="BKMK_SupplementalBackup"></a> 추가 백업 작업  
 백업 사이트 서버 유지 관리 작업은 사이트 서버 파일 및 사이트 데이터베이스에 대한 백업 스냅숏을 제공하지만, 백업되지 않는 기타 항목도 존재하기 마련이며 이는 백업 전략을 수립할 때 반드시 고려해야 합니다. 다음 섹션의 내용을 사용하여 Configuration Manager 백업 전략을 완료할 수 있습니다.  

#### <a name="back-up-custom-reporting-services-reports"></a>사용자 지정 Reporting Services 보고서 백업  
 미리 정의하거나 만든 사용자 지정 Reporting Services 보고서를 수정한 경우, 보고서 서버 데이터베이스 파일의 백업을 만드는 작업은 백업 전략에서 중요한 부분을 차지합니다. 보고서 서버 백업에는 보고서 및 모델에 대한 원본 파일, 암호화 키, 사용자 지정 어셈블리 또는 확장, 구성 파일, 사용자 지정 보고서에 사용되는 사용자 지정 SQL Server 뷰, 사용자 지정 저장 프로시저 등의 백업이 포함되어야 합니다.  

> [!IMPORTANT]  
>  Configuration Manager가 새 버전으로 업데이트되면 새 보고서가 미리 정의된 보고서를 덮어쓸 수 있습니다. 미리 정의된 보고서를 수정하는 경우 보고서를 백업한 다음 Reporting Services에서 보고서를 복원합니다.  

 Reporting Services에서 사용자 지정 보고서를 백업하는 방법에 대한 자세한 내용은 SQL Server 2014 온라인 설명서에서 [Reporting Services 설치에 대한 백업 및 복원 작업](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) 을 참조하세요.  

#### <a name="backup-content-files"></a>콘텐츠 파일 백업  
 Configuration Manager의 콘텐츠 라이브러리는 소프트웨어 업데이트, 응용 프로그램, 운영 체제 배포 등에 대한 모든 콘텐츠 파일이 저장되는 위치입니다. 콘텐츠 라이브러리는 사이트 서버와 각 배포 지점에 위치합니다. 백업 사이트 서버 유지 관리 작업에는 콘텐츠 라이브러리 또는 패키지 원본 파일에 대한 백업이 포함되어 있지 않습니다. 사이트 서버가 작업에 실패하면 콘텐츠 라이브러리 파일 관련 정보는 사이트 데이터베이스에 복원되지만, 사이트 서버에 콘텐츠 라이브러리와 패키지 원본 파일을 복원해야 합니다.  

-   **콘텐츠 라이브러리**: 콘텐츠를 배포 지점에 재배포하려면 먼저 콘텐츠 라이브러리를 복원해야 합니다. 콘텐츠 재배포가 시작되면 Configuration Manager는 사이트 서버에 있는 콘텐츠 라이브러리의 파일을 배포 지점에 복사합니다. 사이트 서버에 대한 콘텐츠 라이브러리는 SCCMContentLib 폴더 안에 있으며 이 폴더는 보통 사이트가 설치된 시점에 사용 가능한 디스크 공간이 가장 많은 드라이브에 있습니다.  

-   **패키지 원본 파일**: 배포 지점에서 콘텐츠를 업데이트하려면 먼저 패키지 원본 파일을 복원해야 합니다. 콘텐츠 업데이트가 시작되면 Configuration Manager는 패키지 원본에서 새 파일 또는 수정된 파일을 콘텐츠 라이브러리에 복사하고, 곧이어 해당 파일은 연결된 배포 지점에 복사됩니다. SQL Server에서 다음 쿼리를 실행하면 모든 패키지 및 응용 프로그램에 대한 패키지 원본 위치를 검색할 수 있습니다. `SELECT * FROM v_Package` 패키지 ID의 처음 세 문자를 보면 패키지 원본 사이트를 식별할 수 있습니다. 예를 들어 패키지 ID가 CEN00001이면 원본 사이트의 사이트 코드는 CEN입니다. 패키지 원본 파일을 복원할 때는 해당 파일을 실패 전에 있었던 위치로 복원해야 합니다.  

 사이트 서버에 대한 파일 시스템 백업에 콘텐츠 라이브러리 및 패키지 원본 위치가 모두 포함되어 있는지 확인하세요.  

#### <a name="back-up-custom-software-updates"></a>사용자 지정 소프트웨어 업데이트 백업  
 독립 실행형 도구인 System Center Updates Publisher 2011을 사용하면 사용자 지정 소프트웨어 업데이트를 WSUS(Windows Server Update Services)에 게시하고, 소프트웨어 업데이트를 Configuration Manager에 동기화하고, 소프트웨어 업데이트 호환성을 평가하고, 사용자 지정 소프트웨어 업데이트를 클라이언트에 배포할 수 있습니다. Updates Publisher는 해당 소프트웨어 업데이트 리포지토리에 로컬 데이터베이스를 사용합니다. Updates Publisher를 사용하여 사용자 지정 소프트웨어 업데이트를 관리하는 경우 백업 계획에 Updates Publisher 데이터베이스를 포함해야 할지 여부를 결정합니다. Updates Publisher에 대한 자세한 내용은 System Center TechCenter 라이브러리에서 [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) 을 참조하세요.  

 다음 절차를 사용하여 Updates Publisher 데이터베이스를 백업합니다.  

###### <a name="to-back-up-the-updates-publisher-2011-database"></a>Updates Publisher 2011 데이터베이스를 백업하려면  

1.  Updates Publisher가 실행되는 컴퓨터의 %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\에서 Updates Publisher 데이터베이스 파일(Scupdb.sdf)을 찾습니다. Updates Publisher를 실행하는 각 사용자에 대해 서로 다른 데이터베이스 파일이 있습니다.  

2.  데이터베이스 파일을 백업 대상에 복사합니다. 예를 들어 백업 대상이 E:\ConfigMgr_Backup인 경우 Updates Publisher 데이터베이스 파일을 E:\ConfigMgr_Backup\SCUP2011에 복사하면 됩니다.  

    > [!TIP]  
    >  컴퓨터에 데이터베이스 파일이 둘 이상 있을 경우 해당 데이터베이스 파일이 연결된 사용자 프로필을 나타내는 하위 폴더에 파일을 저장하는 것을 고려하세요. 예를 들어, 데이터베이스 파일 하나를 E:\ConfigMgr_Backup\SCUP2011\User1에 저장하고 다른 데이터베이스 파일은 E:\ConfigMgr_Backup\SCUP2011\User2에 저장할 수 있습니다.  

### <a name="user-state-migration-data"></a>사용자 환경 마이그레이션 데이터  
 Configuration Manager 작업 순서를 사용하면 현재 운영 체제의 사용자 상태를 보존하려는 운영 체제 배포 시나리오에서 사용자 상태 데이터를 캡처 및 복원할 수 있습니다. 사용자 상태 데이터를 저장하는 폴더는 상태 마이그레이션 지점의 속성에 나열됩니다. 이 사용자 환경 마이그레이션 데이터는 사이트 서버 백업 유지 관리 작업의 일부로 백업되지 않습니다. 백업 계획의 일부로, 사용자 환경 마이그레이션 데이터를 저장하도록 지정한 폴더를 수동으로 백업해야 합니다.   

#### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>사용자 환경 마이그레이션 데이터 저장에 사용되는 폴더 결정  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 선택합니다.  

3.  상태 마이그레이션 역할을 호스트하는 사이트 시스템을 선택한 다음 **사이트 시스템 역할**에서 **상태 마이그레이션 지점**을 선택합니다.  

4.  **사이트 역할** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  사용자 환경 마이그레이션 데이터를 저장하는 폴더는 **일반** 탭의 **폴더 세부 정보** 섹션에 나열됩니다.  

##  <a name="a-namebkmkrecoversitea-recover-a-configuration-manager-site"></a><a name="BKMK_RecoverSite"></a> Configuration Manager 사이트 복구  
 Configuration Manager 사이트 복구는 Configuration Manager 사이트가 실패하거나 데이터 손실이 사이트 데이터베이스에서 발생할 때마다 수행해야 합니다. 데이터 복구 및 재동기화는 사이트 복구의 핵심 작업으로서 작업 중단을 방지하기 위해 필요합니다.  

> [!IMPORTANT]  
>  사이트의 데이터베이스를 복구하는 경우:  
>   
>  -   동일한 SQL Server 버전을 사용해야 합니다. 예를 들어 SQL Server 2012에서 실행했던 데이터베이스를 SQL Server 2014로 복원할 수 없습니다. 마찬가지로 SQL Server 2014 Standard Edition에서 실행했던 사이트 데이터베이스를 SQL Server 2014 Enterprise Edition으로 복원할 수는 없습니다.  
> -   SQL Server를 **단일 사용자 모드**로 설정하면 안 됩니다.  
> -   . MDF 및 .LDF 파일이 올바른지 확인합니다. 사이트를 복구할 때 복원하려는 파일의 상태는 확인되지 않습니다.  


 사이트 복구는 CD.Latest 폴더에서 Configuration Manager 설치 마법사를 실행하여 시작합니다.  무인 설치 스크립트를 구성한 후 설치 명령의 **/script** 옵션을 사용하여 동일한 CD.Latest 폴더에서 설치 프로그램을 실행할 수도 있습니다. 사용할 복구 옵션은 Configuration Manager 사이트 데이터베이스의 백업이 있는지 여부에 따라 달라집니다. 자세한 내용은 [System Center Configuration Manager의 CD.Latest 폴더](../../core/servers/manage/the-cd.latest-folder.md)를 참조하세요.  

> [!IMPORTANT]  
>  사이트 서버의 **시작** 메뉴에서 Configuration Manager 설치 프로그램을 실행하는 경우 **사이트 복구** 옵션을 사용할 수 없습니다.  
>   
>  백업을 수행하기 전에 Configuration Manager 콘솔 내에서 업데이트를 설치한 경우 설치 미디어나 Configuration Manager 설치 경로의 설치 프로그램을 사용하여 사이트를 다시 설치할 수 없습니다.  

> [!NOTE]  
>  데이터베이스 복제본용으로 구성된 사이트 데이터베이스를 복원한 후에, 데이터베이스 복제본을 사용하려면 먼저 게시 및 구독을 모두 다시 만드는 것을 포함해 각 데이터베이스 복제본을 다시 구성해야 합니다.  

###  <a name="a-namebkmkdeterminerecoveryoptionsa-determine-your-recovery-options"></a><a name="BKMK_DetermineRecoveryOptions"></a> 복구 옵션 결정  
 Configuration Manager 기본 사이트 서버 및 중앙 관리 사이트 복구를 수행하려면 사이트 서버 및 사이트 데이터베이스라는 두 가지 영역을 가장 기본적으로 고려해야 합니다. 다음 섹션에서는 복구 시나리오에서 선택해야 할 옵션을 결정하는 방법에 대해 설명합니다.  

> [!NOTE]  
>  이전 사이트 복구가 실패했거나 완전히 제거되지 않은 사이트의 복구를 시도할 경우, 먼저 설치 프로그램에서 **Configuration Manager 사이트 제거** 를 선택해야 사이트 복구를 선택할 수 있습니다. 자식 사이트가 포함된 실패한 사이트를 제거해야 할 경우, **Configuration Manager 사이트 제거** 옵션을 선택하기 전에 먼저 실패한 사이트에서 사이트 데이터베이스를 수동으로 삭제해야 하며 그렇지 않으면 제거 프로세스는 실패합니다.  

####  <a name="a-namebkmksiteserverrecoveryoptionsa-site-server-recovery-options"></a><a name="BKMK_SiteServerRecoveryOptions"></a> 사이트 서버 복구 옵션  
 Configuration Manager 설치 폴더 외부에 만든 CD.Latest 폴더의 복사본에서 설치 프로그램을 시작해야 합니다. 그런 다음 **사이트 복구** 옵션을 선택합니다. 설치 프로그램을 실행할 때 실패한 사이트 서버에 대해 다음과 같은 복구 옵션을 사용할 수 있습니다.  

-   **기존 백업을 사용하여 사이트 서버 복구**: 이 옵션은 사이트 오류 전에 **백업 사이트 서버** 유지 관리 작업의 일부로 사이트 서버에 만들어진 Configuration Manager 사이트 서버 백업이 있을 때 사용합니다. 백업된 사이트를 기준으로 사이트가 다시 설치되고 사이트 설정이 구성됩니다.  

-   **사이트 서버 다시 설치**: 이 옵션은 사이트 서버 백업이 없을 때 사용합니다. 사이트 서버가 다시 설치되며, 초기 설치 시 구성한 것처럼 사이트 설정을 지정해야 합니다. 실패한 사이트를 처음 설치했을 때 사용한 것과 동일한 사이트 코드 및 사이트 데이터베이스 이름을 사용해야 성공적으로 사이트를 복구할 수 있습니다.  

> [!NOTE]  
>  설치 프로그램이 서버에서 기존 Configuration Manager 사이트를 검색한 경우, 사이트 복구를 시작할 수는 있지만 사이트 서버에 대한 복구 옵션이 제한됩니다. 예를 들어 기존 사이트 서버에서 설치 프로그램을 실행하고 복구를 선택하면, 사이트 데이터베이스 서버를 복구할 수는 있지만 사이트 서버 복구를 위한 옵션은 사용할 수 없습니다.  

####  <a name="a-namebkmksitedatabaserecoveryoptiona-site-database-recovery-options"></a><a name="BKMK_SiteDatabaseRecoveryOption"></a> 사이트 데이터베이스 복구 옵션  
 설치 프로그램을 실행할 때 사이트 데이터베이스에 대해 다음과 같은 복구 옵션을 사용할 수 있습니다.  

-   **백업 집합을 사용하여 사이트 데이터베이스 복구**: 이 옵션은 사이트 데이터베이스 오류 전에 사이트에서 실행된 **백업 사이트 서버** 유지 관리 작업의 일부로 사이트 서버에 만들어진 Configuration Manager 사이트 데이터베이스 백업이 있을 때 사용합니다. 계층이 있을 때 마지막 사이트 데이터베이스 백업 후 사이트 데이터베이스에서 변경된 내용은 기본 사이트에 대해서는 중앙 관리 사이트, 또는 중앙 관리 사이트에 대해서는 참조 기본 사이트에서 검색됩니다. 독립 실행형 기본 사이트에 대한 사이트 데이터베이스를 복구하면 마지막 백업 이후의 사이트 변경 내용은 손실됩니다.  

     계층 내 사이트에 대한 사이트 데이터베이스를 복구할 경우 복구 동작은 중앙 관리 사이트 및 기본 사이트에 대해 서로 다르며 마지막 백업이 SQL Server 변경 내용 추적 보존 기간 내에 있는지 여부에 따라서도 다릅니다. 자세한 내용은 이 항목의 [사이트 데이터베이스 복구 시나리오](#BKMK_SiteDBRecoveryScenarios) 섹션을 참조하세요.  

    > [!NOTE]  
    >  백업 집합을 사용하여 사이트 데이터베이스를 복원하도록 선택했지만 사이트 데이터베이스가 이미 존재하는 경우 복구는 실패합니다.  

-   **이 사이트에 대한 새 데이터베이스 만들기**: 이 옵션은 Configuration Manager 사이트 데이터베이스 백업이 없을 때 사용합니다. 계층이 있을 때, 새 사이트 데이터베이스가 만들어지고 기본 사이트에 대해서는 중앙 관리 사이트에서, 또는 중앙 관리 사이트에 대해서는 참조 기본 사이트에서 복제된 데이터를 사용하여 데이터가 복구됩니다. 이 옵션은 독립 실행형 기본 사이트 또는 기본 사이트가 없는 중앙 관리 사이트를 복구할 경우에는 사용할 수 없습니다.  

-   **수동으로 복구된 사이트 데이터베이스 사용**: Configuration Manager 사이트 데이터베이스는 이미 복구했지만 복구 프로세스를 완료해야 하는 경우 이 옵션을 사용합니다. Configuration Manager는 Configuration Manager 백업 유지 관리 작업이나 DPM 또는 기타 프로세스를 사용하여 수행하는 사이트 데이터베이스 백업에서 사이트 데이터베이스를 복구할 수 있습니다. Configuration Manager 외부의 방법을 사용하여 사이트 데이터베이스를 복원한 후에는 설치 프로그램을 실행하고 이 옵션을 선택하여 사이트 데이터베이스 복구를 완료해야 합니다. 계층이 있을 때 마지막 사이트 데이터베이스 백업 후 사이트 데이터베이스에서 변경된 내용은 기본 사이트에 대해서는 중앙 관리 사이트, 또는 중앙 관리 사이트에 대해서는 참조 기본 사이트에서 검색됩니다. 독립 실행형 기본 사이트에 대한 사이트 데이터베이스를 복구하면 마지막 백업 이후의 사이트 변경 내용은 손실됩니다.  

    > [!NOTE]  
    >  DPM을 사용하여 사이트 데이터베이스를 백업할 경우, Configuration Manager에서 복원 프로세스를 계속하기 전에 먼저 DPM 프로시저를 사용하여 사이트 데이터베이스를 지정된 위치에 복원하세요. DPM에 대한 자세한 내용은 TechNet에서 [Data Protection Manager Documentation Library(Data Protection Manager)](http://go.microsoft.com/fwlink/?LinkId=272772) 를 참조하세요.  

-   **데이터베이스 복구 건너뛰기**: 이 옵션은 Configuration Manager 사이트 데이터베이스 서버에서 데이터 손실이 발생하지 않았을 때 사용합니다. 이 옵션은 사이트 데이터베이스가 현재 복구 중인 사이트 서버가 아닌 다른 컴퓨터에 있는 경우에만 유효합니다.  

####  <a name="a-namebkmksqlretentiona-sql-server-change-tracking-retention-period"></a><a name="bkmk_SQLretention"></a> SQL Server 변경 내용 추적 보존 기간  
 변경 내용 추적은 SQL Server에서 사이트 데이터베이스에 대해 사용하도록 설정됩니다. Configuration Manager는 변경 내용 추적을 통해 이전 시점 이후에 데이터베이스 테이블에서 변경된 내용에 관한 정보를 쿼리할 수 있습니다. 보존 기간은 변경 내용 추적 정보가 보존되는 기간을 지정합니다. 기본적으로 사이트 데이터베이스는 5일간의 보존 기간을 갖도록 구성됩니다. 사이트 데이터베이스를 복구할 때 백업이 보존 기간 내에 있느냐 없느냐에 따라 복구 프로세스는 다르게 진행됩니다. 예를 들어, 사이트 데이터베이스 서버가 실패하고 마지막 백업이 7일 경과한 경우 이 백업은 보존 기간을 벗어납니다.  

####  <a name="a-namebkmkreinita-process-to-reinitialize-site-or-global-data"></a><a name="bkmk_reinit"></a> 사이트 또는 글로벌 데이터를 다시 초기화하는 프로세스  
 사이트 또는 글로벌 데이터를 다시 초기화하는 프로세스는 사이트 데이터베이스 내 기존 데이터를 다른 사이트 데이터베이스의 데이터로 교체합니다. 예를 들어 사이트 ABC에서 사이트 XYZ의 데이터를 다시 초기화하면 다음 단계가 진행됩니다.  

-   데이터가 사이트 XYZ에서 사이트 ABC로 복사됩니다.  

-   사이트 XYZ에 대한 기존 데이터가 사이트 ABC의 사이트 데이터베이스에서 제거됩니다.  

-   사이트 XYZ에서 복사된 데이터는 사이트 ABC의 사이트 데이터베이스에 삽입됩니다.  

##### <a name="example-scenario-1"></a>예제 시나리오 1  
 **기본 사이트에서 중앙 관리 사이트의 글로벌 데이터를 다시 초기화**: 복구 프로세스에서 기본 사이트 데이터베이스에 있는 기본 사이트용 기존 글로벌 데이터를 제거하고 해당 데이터를 중앙 관리 사이트에서 복사된 글로벌 데이터로 교체합니다.  

##### <a name="example-scenario-2"></a>예제 시나리오 2  
 **중앙 관리 사이트에서 기본 사이트의 사이트 데이터를 다시 초기화**: 복구 프로세스에서 중앙 관리 사이트 데이터베이스에 있는 기본 사이트용 기존 사이트 데이터를 제거하고 해당 데이터를 기본 사이트에서 복사된 사이트 데이터로 교체합니다. 다른 기본 사이트에 대한 사이트 데이터는 영향을 받지 않습니다.  

####  <a name="a-namebkmksitedbrecoveryscenariosa-site-database-recovery-scenarios"></a><a name="BKMK_SiteDBRecoveryScenarios"></a> 사이트 데이터베이스 복구 시나리오  
 사이트 데이터베이스가 백업에서 복원되면 Configuration Manager에서는 마지막 데이터베이스 백업 이후에 사이트 및 글로벌 데이터에서 변경된 내용을 복원하려고 시도합니다. 다음에서는 사이트 데이터베이스가 백업에서 복원된 후에 Configuration Manager에서 시작하는 작업을 설명합니다.  

 **복구된 사이트가 중앙 관리 사이트인 경우:**  

-   **변경 내용 추적 보존 기간 내의 데이터베이스 백업**  

    -   **글로벌 데이터:** 백업 후의 글로벌 데이터 변경 내용은 모든 기본 사이트에서 복제됩니다.  

    -   **사이트 데이터:** 백업 후의 사이트 데이터 변경 내용은 모든 기본 사이트에서 복제됩니다.  

-   **변경 내용 추적 보존 기간보다 오래 된 데이터베이스 백업**  

    -   **글로벌 데이터:** 중앙 관리 사이트에서 참조 기본 사이트의 글로벌 데이터를 다시 초기화합니다(지정한 경우). 그런 다음 다른 모든 기본 사이트에서 중앙 관리 사이트의 글로벌 데이터를 다시 초기화합니다. 참조 사이트가 지정되지 않은 경우, 모든 기본 사이트에서 중앙 관리 사이트의 글로벌 데이터(백업에서 복원된 데이터)를 다시 초기화합니다.  

    -   **사이트 데이터:** 중앙 관리 사이트에서 각 기본 사이트의 사이트 데이터를 다시 초기화합니다.  

 **복구된 사이트가 기본 사이트인 경우:**  

-   **변경 내용 추적 보존 기간 내의 데이터베이스 백업**  

    -   **글로벌 데이터:** 백업 후의 글로벌 데이터 변경 내용은 중앙 관리 사이트에서 복제됩니다.  

    -   **사이트 데이터:** 중앙 관리 사이트에서 기본 사이트의 사이트 데이터를 다시 초기화합니다. 백업 후의 변경 내용은 손실되지만 대부분의 데이터는 기본 사이트에 정보를 보내는 클라이언트에 의해 다시 생성됩니다.  

-   **변경 내용 추적 보존 기간보다 오래 된 데이터베이스 백업**  

    -   **글로벌 데이터:** 기본 사이트에서 중앙 관리 사이트의 글로벌 데이터를 다시 초기화합니다.  

    -   **사이트 데이터:** 중앙 관리 사이트에서 기본 사이트의 사이트 데이터를 다시 초기화합니다. 백업 후의 변경 내용은 손실되지만 대부분의 데이터는 기본 사이트에 정보를 보내는 클라이언트에 의해 다시 생성됩니다.  

### <a name="site-recovery-procedures"></a>사이트 복구 절차  
 다음 절차 중 하나에 따라 사이트 서버와 사이트 데이터베이스를 복구할 수 있습니다.  

##### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>설치 마법사에서 사이트 복구를 시작하려면  

1.  CD.Latest 폴더를 Configuration Manager 설치 폴더 외부 위치로 복사합니다. ([System Center Configuration Manager의 CD.Latest 폴더](../../core/servers/manage/the-cd.latest-folder.md) 참조)  

     CD.Latest 폴더의 복사본에서 Configuration Manager 설치 마법사를 실행합니다.  

2.  **시작** 페이지에서 **사이트 복구**를 선택한 후 **다음**을 클릭합니다.  

3.  해당 사이트 복구에 적합한 옵션을 사용하여 마법사를 완료합니다.  

    > [!IMPORTANT]  
    >  복구 중에 설치 프로그램은 SQL Server에서 사용되는 SQL Server Service Broker(SSB) 포트를 식별합니다. 복구 중에 이 포트 설정을 변경하지 마세요. 만약 이 설정을 변경하면 복구가 완료된 후 데이터 복제가 올바르게 작동하지 않습니다.  

    > [!NOTE]  
    >  설치 마법사에서 Configuration Manager 설치에 사용할 원래 경로나 새 경로를 지정할 수 있습니다.  

##### <a name="to-start-an-unattended-site-recovery"></a>무인 사이트 복구를 시작하려면  

1.  사이트 복구에 필요한 옵션에 대해 무인 설치 스크립트를 준비합니다.  

2.  명령 **/script** 옵션을 사용하여 Configuration Manager 설치 프로그램을 실행합니다. 예를 들어 설치 초기화 파일의 이름을 ConfigMgrUnattend.ini로 지정하고 이 파일을 설치 프로그램이 실행 중인 컴퓨터의 C:\Temp 디렉터리에 저장한 경우, 해당 명령은 다음과 같습니다. **Setup /script C:\temp\ConfigMgrUnattend.ini**  

> [!NOTE]  
>  중앙 관리 사이트를 복구한 후 자식 사이트에서의 일부 사이트 데이터 복제가 설정되지 못할 수 있습니다. 여기에는 하드웨어 인벤토리, 소프트웨어 인벤토리 및 상태 메시지가 포함됩니다.  
>   
>  이 경우 데이터베이스 복제에 대해 **ConfigMgrDRSSiteQueue** 를 다시 초기화해야 합니다.  이를 위해 **SQL Server 관리자**를 사용하여 중앙 관리 사이트의 Configuration Manager 사이트 데이터베이스에 대해 다음 쿼리를 실행합니다.  
>   
>  **IF EXISTS (SELECT \* FROM sys.service_queues WHERE name = 'ConfigMgrDRSSiteQueue' AND is_receive_enabled = 0)**  
>   
>  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**  

###  <a name="a-namebkmkunattendedsiterecoverykeysa-unattended-site-recovery-script-file-keys"></a><a name="BKMK_UnattendedSiteRecoveryKeys"></a> 무인 사이트 복구 스크립트 파일 키  
 Configuration Manager 중앙 관리 사이트 또는 기본 사이트의 무인 복구를 수행하려는 경우, 무인 설치 스크립트를 만들고 /script 명령 옵션과 함께 설치 프로그램을 사용하면 됩니다. 이 스크립트는 기본 설정이 없다는 점만 제외하고 설치 마법사에서 요구하는 정보와 동일한 유형의 정보를 제공합니다. 사용 중인 복구 유형에 적용되는 설치 키에 대해 모든 값을 지정해야 합니다.  

 초기화 파일을 /script 설치 명령줄 옵션과 함께 사용하면 Configuration Manager 설치 프로그램을 무인 모드로 실행할 수 있습니다. 무인 설치는 Configuration Manager 중앙 관리 사이트 및 기본 사이트의 복구에 대해 지원됩니다. /script 설치 명령줄 옵션을 사용하려면 초기화 파일을 만들고 /script 설치 명령줄 옵션 뒤에 초기화 파일 이름을 지정해야 합니다. 파일 이름은 .ini 파일 이름 확장명만 붙이면 자유롭게 지정해도 됩니다. 명령줄에서 설치 초기화 파일을 참조할 때 파일의 전체 경로를 입력해야 합니다. 예를 들어 이름이 setup.ini인 설치 초기화 파일이 C:\setup 폴더에 저장되어 있는 경우 명령줄은 다음과 같습니다.  

 **setup /script c:\setup\setup.ini**.  

> [!IMPORTANT]  
>  설치 프로그램을 실행하려면 관리자 권한이 있어야 합니다. 무인 스크립트로 설치 프로그램을 실행할 경우 **관리자 권한으로 실행**을 사용하여 명령 프롬프트를 관리자 컨텍스트로 시작하세요.  

 스크립트에는 섹션 이름, 키 이름 및 값이 포함됩니다. 필요한 섹션 키 이름은 스크립트를 작성하는 복구 유형에 따라 다릅니다. 섹션 내의 키 순서와 파일 내의 섹션 순서는 중요하지 않습니다. 키는 대소문자를 구분하지 않습니다. 키에 값을 지정할 때에는 키 이름 뒤에 등호(=)를 추가하고 키 값을 입력해야 합니다.  

 다음 섹션에서는 무인 사이트 복구를 위한 스크립트를 만드는 방법에 대해 설명합니다. 이 표에는 사용 가능한 설치 스크립트 키, 해당 값, 필수 여부, 설치 유형, 키에 대한 간략한 설명이 나와 있습니다.  

#### <a name="recover-a-central-administration-site-unattended"></a>중앙 관리 사이트의 무인 복구  
 다음 정보를 참조하여 중앙 관리 사이트를 복구하도록 무인 설치 스크립트 파일을 구성할 수 있습니다.  

 **Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** RecoverCCAR  

    -   **세부 정보:** 중앙 관리 사이트를 복구합니다.  

**RecoveryOptions**  

-   **키 이름:** ServerRecoveryOptions  

    -   **필수:** 예  

    -   **값:** 1, 2 또는 4  

         1 = 사이트 서버와 SQL Server 복구  

         2 = 사이트 서버만 복구  

         4 = SQL Server만 복구  

    -   **세부 정보:** 설치 프로그램이 복구할 대상(사이트 서버, SQL Server, 둘 다)을 지정합니다. ServerRecoveryOptions 설정에 대해 다음 값을 설정하는 경우 연결된 키는 필수입니다.  

        -   **값 = 1** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

             **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

        -   **값 = 2** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

        -   **값 = 4** **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

-   **키 이름:** DatabaseRecoveryOptions  

    -   **필수:** 미정  

    -   **값:** 10, 20, 40, 80  

         10 = 백업에서 사이트 데이터베이스 복구  

         20 = 다른 방법을 사용하여 수동으로 복구된 사이트 데이터베이스 사용  

         40 = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 글로벌 데이터 및 사이트 데이터는 다른 사이트를 복제하여 복구됩니다.  

         80 = 데이터베이스 복구 건너뛰기  

    -   **세부 정보:** 설치 프로그램이 SQL Server에서 사이트 데이터베이스를 복구할 방법을 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.  

-   **키 이름:** ReferenceSite  

    -   **필수:** 미정  

    -   **값:** <ReferenceSiteFQDN\>  

    -   **세부 정보:** 데이터베이스 백업이 변경 내용 추적 보존 기간보다 오래 되었거나 백업 없이 사이트를 복구할 경우 중앙 관리 사이트에서 글로벌 데이터를 복구하는 데 사용하는 참조 기본 사이트를 지정합니다.  

         참조 사이트를 지정하지 않았는데 백업이 변경 추적 보존 기간보다 오래된 경우 모든 기본 사이트는 중앙 관리 사이트에서 복원된 데이터로 다시 초기화됩니다.  

         참조 사이트를 지정하지 않고 백업이 변경 내용 추적 보존 기간 내에 있는 경우, 백업 이후 변경된 내용만 기본 사이트에서 복제됩니다. 서로 다른 기본 사이트 간에 충돌하는 변경 내용이 있으면 중앙 관리 사이트에서는 가장 먼저 수신한 변경 내용을 사용합니다.  

         **DatabaseRecoveryOptions** 설정 값이 **40**인 경우 이 키는 필수입니다.  

-   **키 이름:** SiteServerBackupLocation  

    -   **필수:** 아니요  

    -   **값:** <PathToSiteServerBackupSet\>  

    -   **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

-   **키 이름:** BackupLocation  

    -   **필수:** 미정  

    -   **값:** <PathToSiteDatabaseBackupSet\>  

    -   **세부 정보:** 사이트 데이터베이스 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 키 값을 **1** 또는 **4** 로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하는 경우 **BackupLocation** 키는 필수입니다.  

**Options**  

-   **키 이름:** ProductID  

    -   **필수:** 예  

    -   **값:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         평가 버전  

    -   **세부 정보:** 대시를 포함한 Configuration Manager 설치 제품 키입니다. **Eval** 입력을 통해 Configuration Manager의 평가 버전을 설치할 수 있습니다.  

-   **키 이름:** SiteCode  

    -   **필수:** 예  

    -   **값:** <사이트 코드\>  

    -   **세부 정보:** 계층에서 사이트를 고유하게 식별하는 세 자리 영숫자입니다. 실패하기 전에 사이트에서 사용했던 사이트 코드를 지정해야 합니다.  

-   **키 이름:** SiteName  

    -   **필수:** 예  

    -   **값:** SiteName  

    -   **세부 정보:** 이 사이트에 대한 설명입니다.  

-   **키 이름:** SMSInstallDir  

    -   **필수:** 예  

    -   **값:** <*Configuration Manager 설치 경로*>  

    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

        > [!NOTE]  
        >  Configuration Manager 설치에 사용할 원래 경로 또는 새 경로를 지정할 수 있습니다.  

-   **키 이름:** SDKServer  

    -   **필수:** 예  

    -   **값:** <*SMS 공급자의 FQDNr*>  

    -   **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정해야 합니다.  

         초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 0 값을 사용하면 설치 프로그램이 파일을 다운로드합니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치를 위한 필수 파일의 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

-   **키 이름:** AdminConsole  

    -   **필수:** 미정  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다. **ServerRecoveryOptions** 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.  

-   **키 이름:** JoinCEIP  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 참여 안 함  

         1 = 참여  

    -   **세부 정보:** 사용자 환경 개선 프로그램에 참여할지 여부를 지정합니다.  

**SQLConfigOptions**  

-   **키 이름:** SQLServerName  

    -   **필수:** 예  

    -   **값:** *<SQL Server 이름\>*  

    -   **세부 정보:** 사이트 데이터베이스를 호스트할 SQL Server를 실행하는 서버 이름 또는 클러스터형 인스턴스 이름입니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정해야 합니다.  

-   **키 이름:** DatabaseName  

    -   **필수:** 예  

    -   **값:**  

         *&lt;사이트 데이터베이스 이름&gt;\>*  

         대화 상자에 있는  

         *<인스턴스 이름\>*\\*<사이트 데이터베이스 이름\>*  

    -   **세부 정보:** 중앙 관리 사이트 데이터베이스를 설치하기 위해 사용하거나 만들 SQL Server 데이터베이스의 이름입니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정해야 합니다.  

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.  

-   **키 이름:** SQLSSBPort  

    -   **필수:** 아니요  

    -   **값:** <*SSB 포트 번호*>  

    -   **세부 정보:** SQL Server에서 사용하는 SQL SSB(Server Service Broker) 포트를 지정합니다. 일반적으로, SSB는 TCP 포트 4022를 사용하도록 구성되지만 다른 포트도 지원됩니다. 실패하기 전에 사용했던 SSB 포트를 지정해야 합니다.  

#### <a name="recover-a-primary-site-unattended"></a>기본 사이트 무인 복구  
 다음 정보를 참조하여 중앙 관리 사이트를 복구하도록 무인 설치 스크립트 파일을 구성할 수 있습니다.  

 **Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** RecoverPrimarySite  

    -   **세부 정보:** 기본 사이트를 복구합니다.  

**RecoveryOptions**  

-   **키 이름:** ServerRecoveryOptions  

    -   **필수:** 예  

    -   **값:** 1, 2 또는 4  

         1 = 사이트 서버와 SQL Server 복구  

         2 = 사이트 서버만 복구  

         4 = SQL Server만 복구  

    -   **세부 정보:** 설치 프로그램이 복구할 대상(사이트 서버, SQL Server, 둘 다)을 지정합니다. ServerRecoveryOptions 설정에 대해 다음 값을 설정하는 경우 연결된 키는 필수입니다.  

        -   **값 = 1** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

             **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

        -   **값 = 2** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

        -   **값 = 4** **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

-   **키 이름:** DatabaseRecoveryOptions  

    -   **필수:** 미정  

    -   **값:** 10, 20, 40, 80  

         10 = 백업에서 사이트 데이터베이스 복구  

         20 = 다른 방법을 사용하여 수동으로 복구된 사이트 데이터베이스 사용  

         40 = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 글로벌 데이터 및 사이트 데이터는 다른 사이트를 복제하여 복구됩니다.  

         80 = 데이터베이스 복구 건너뛰기  

    -   **세부 정보:** 설치 프로그램이 SQL Server에서 사이트 데이터베이스를 복구할 방법을 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.  

-   **키 이름:** SiteServerBackupLocation  

    -   **필수:** 아니요  

    -   **값:** <PathToSiteServerBackupSet\>  

    -   **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

-   **키 이름:** BackupLocation  

    -   **필수:** 미정  

    -   **값:** <PathToSiteDatabaseBackupSet\>  

    -   **세부 정보:** 사이트 데이터베이스 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 키 값을 **1** 또는 **4** 로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하는 경우 **BackupLocation** 키는 필수입니다.  

**Options**  

-   **키 이름:** ProductID  

    -   **필수:** 예  

    -   **값:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         평가 버전  

    -   **세부 정보:** 대시를 포함한 Configuration Manager 설치 제품 키입니다. **Eval** 입력을 통해 Configuration Manager의 평가 버전을 설치할 수 있습니다.  

-   **키 이름:** SiteCode  

    -   **필수:** 예  

    -   **값:** <사이트 코드\>  

    -   **세부 정보:** 계층에서 사이트를 고유하게 식별하는 세 자리 영숫자입니다. 실패하기 전에 사이트에서 사용했던 사이트 코드를 지정해야 합니다.  

-   **키 이름:** SiteName  

    -   **필수:** 예  

    -   **값:** SiteName  

    -   **세부 정보:** 이 사이트에 대한 설명입니다.  

-   **키 이름:** SMSInstallDir  

    -   **필수:** 예  

    -   **값:** <*Configuration Manager 설치 경로*>  

    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

        > [!NOTE]  
        >  Configuration Manager 설치에 사용할 원래 경로 또는 새 경로를 지정할 수 있습니다.  

-   **키 이름:** SDKServer  

    -   **필수:** 예  

    -   **값:** <*SMS 공급자의 FQDNr*>  

    -   **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정해야 합니다.  

         초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 0 값을 사용하면 설치 프로그램이 파일을 다운로드합니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치를 위한 필수 파일의 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

-   **키 이름:** AdminConsole  

    -   **필수:** 미정  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다. **ServerRecoveryOptions** 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.  

-   **키 이름:** JoinCEIP  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 참여 안 함  

         1 = 참여  

    -   **세부 정보:** 사용자 환경 개선 프로그램에 참여할지 여부를 지정합니다.  

**SQLConfigOptions**  

-   **키 이름:** SQLServerName  

    -   **필수:** 예  

    -   **값:** *<SQL Server 이름\>*  

    -   **세부 정보:** 사이트 데이터베이스를 호스트할 SQL Server를 실행하는 서버 이름 또는 클러스터형 인스턴스 이름입니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정해야 합니다.  

-   **키 이름:** DatabaseName  

    -   **필수:** 예  

    -   **값:**  

         *&lt;사이트 데이터베이스 이름&gt;\>*  

         대화 상자에 있는  

         *<인스턴스 이름\>*\\*<사이트 데이터베이스 이름\>*  

    -   **세부 정보:** 중앙 관리 사이트 데이터베이스를 설치하기 위해 사용하거나 만들 SQL Server 데이터베이스의 이름입니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정해야 합니다.  

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.  

-   **키 이름:** SQLSSBPort  

    -   **필수:** 아니요  

    -   **값:** <*SSB 포트 번호*>  

    -   **세부 정보:** SQL Server에서 사용하는 SQL SSB(Server Service Broker) 포트를 지정합니다. 일반적으로, SSB는 TCP 포트 4022를 사용하도록 구성되지만 다른 포트도 지원됩니다. 실패하기 전에 사용했던 SSB 포트를 지정해야 합니다.  

**Hierarchy ExpansionOption**  

-   **키 이름:** CCARSiteServer  

    -   **필수:** 미정  

    -   **값:** <*중앙 관리 사이트의 사이트 코드*>  

    -   **세부 정보:** 기본 사이트가 Configuration Manager 계층 구조에 가입할 때 연결할 중앙 관리 사이트를 지정합니다. 실패하기 전에 기본 사이트가 중앙 관리 사이트에 연결되었던 경우 이 설정은 필수입니다. 실패하기 전에 중앙 관리 사이트에 사용했던 사이트 코드를 지정해야 합니다.  

-   **키 이름:** CASRetryInterval  

    -   **필수:** 아니요  

    -   **값:** <*간격*>  

    -   **세부 정보:** 연결에 실패한 후 중앙 관리 사이트를 연결하려고 다시 시도하는 간격(분)을 지정합니다. 예를 들어 기본 사이트가 중앙 관리 사이트에 연결하지 못하면 WaitForCASTimeout 기간에 도달할 때까지 기본 사이트는 CASRetryInterval 값에 기반하여 중앙 관리 사이트에 대한 연결을 다시 시도합니다.  

-   **키 이름:** WaitForCASTimeout  

    -   **필수:** 아니요  

    -   **값:** <*시간 제한*>  

    -   **세부 정보:** 기본 사이트가 중앙 관리 사이트에 연결하는 최대 시간 제한 값(분)을 지정합니다. 예를 들어 기본 사이트가 중앙 관리 사이트에 연결하지 못하면 WaitForCASTimeout 기간에 도달할 때까지 기본 사이트는 CASRetryInterval 값에 기반하여 중앙 관리 사이트에 대한 연결을 다시 시도합니다. 값은 0에서 100까지 지정할 수 있습니다.  

###  <a name="a-namebkmkpostrecoverya-post-recovery-tasks"></a><a name="BKMK_PostRecovery"></a> 복구 후 작업  
 사이트를 복구한 후에 사이트 복구가 완료되기 전에 고려해야 할 몇 가지 복구 후 작업이 있습니다. 사이트 복구 프로세스를 완료하려면 다음 섹션을 참조하세요.  

#### <a name="re-enter-user-account-passwords"></a>사용자 계정 암호 다시 입력  
 사이트에 대해 지정한 사용자 계정의 암호는 사이트 복구 중에 다시 설정되므로 사이트를 복구한 후에 해당 암호를 다시 입력해야 합니다. 계정은 사이트 복구가 완료된 후 설치 마법사의 **마침** 페이지에 나열되고 복구된 사이트 서버의 C:\ConfigMgrPostRecoveryActions.html에 저장됩니다.  

###### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>사이트 복구 후 사용자 계정 암호를 다시 입력하려면  

1.  Configuration Manager 콘솔을 열고 복구된 사이트에 연결합니다.  

2.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

3.  **관리** 작업 영역에서 **보안**을 확장한 후 **계정**을 클릭합니다.  

4.  암호를 다시 입력해야 하는 각 계정에 대해 다음 작업을 수행합니다.  

    1.  사이트 복구 후에 확인된 계정 목록에서 계정을 선택합니다. 이 목록은 복구된 사이트 서버의 C:\ConfigMgrPostRecoveryActions.html에서 찾을 수 있습니다.  

    2.  **홈** 탭의 **속성** 그룹에서 **속성** 을 클릭하여 계정 속성을 엽니다.  

    3.  **일반** 탭에서 **설정**을 클릭한 다음 계정의 암호를 다시 입력합니다.  

    4.  **확인**을 클릭하고 선택한 사용자 계정의 적절한 데이터 원본을 선택한 다음 **연결 테스트** 를 클릭하여 사용자 계정이 데이터 원본에 연결할 수 있는지 확인합니다.  

    5.  **확인** 을 클릭하여 암호 변경 내용을 저장하고 **확인**을 클릭합니다.  

#### <a name="re-enter-sideloading-keys"></a>테스트용 로드 키 다시 입력  
 사이트 서버 복구 후에 사이트 복구 중 테스트용 로드 키가 초기화되므로 사이트에 대해 지정된 Windows 테스트용 로드 키를 다시 입력해야 합니다. 테스트용 로드 키를 다시 입력한 후 Configuration Manager 콘솔에서 Windows 테스트용 로드 키의 **사용된 활성화 수** 열 수가 다시 설정됩니다. 예를 들어 사이트 오류 전에 장치에 **총 활성화 수**가 **100**으로 설정되어 있고 사용된 키의 수에 대한 **사용된 활성화 수**가 **90**이라고 가정해 봅니다. 사이트 복구 후 **총 활성화 수** 열은 여전히 **100**을 표시하지만 **사용된 활성화 수** 열은 값을 **0**으로 잘못 표시합니다. 그러나 10개의 새 장치에서 테스트용 로드 키를 사용한 후에는 남은 테스트용 로드 키가 없으며 다음 장치에서 테스트용 로드 키를 적용하지 못합니다.  

#### <a name="recreate-the-microsoft-intune-subscription"></a>Microsoft Intune 구독 다시 만들기  
 사이트 서버 컴퓨터를 이미지로 다시 설치한 후에 Configuration Manager 사이트 서버를 복구하는 경우 Microsoft Intune 구독이 복원되지 않습니다. 사이트를 복구한 후에 구독을 다시 만들어야 합니다. 자세한 내용은 [Configuring the Microsoft Intune subscription](../../mdm/deploy-use/setup-hybrid-mdm.md#step-3-configure-intune-subscription)을 참조하십시오.  

#### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>IIS를 사용하는 사이트 시스템 역할에 대해 SSL 구성  
 실패하기 전에 HTTPS에 대해 구성했던 IIS를 실행하는 사이트 시스템을 복구할 때 웹 서버 인증서를 사용하도록 IIS를 다시 구성해야 합니다.  

#### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>복구된 사이트 서버에 핫픽스 다시 설치  
 사이트 복구 후에 사이트 서버에 적용했던 모든 핫픽스를 다시 설치해야 합니다. 이전에 설치했던 핫픽스 목록은 사이트 복구 후 설치 마법사의 **마침** 페이지에 나열되고 복구된 사이트 서버의 **C:\ConfigMgrPostRecoveryActions.html** 에 저장됩니다.  

#### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Reporting Services를 실행하는 컴퓨터에서 사용자 지정 보고서 복구  
 사용자 지정 Reporting Services 보고서를 만들었는데 Reporting Services가 실패하는 경우 보고서 서버를 백업했다면 보고서를 복구할 수 있습니다. Reporting Services에서 사용자 지정 보고서를 복구하는 방법에 대한 자세한 내용은 SQL Server 2008 온라인 설명서의 [Reporting Services 설치에 대한 백업 및 복원 작업](http://go.microsoft.com/fwlink/p/?LinkId=228724) 을 참조하세요.  

#### <a name="recover-content-files"></a>콘텐츠 파일 복구  
 사이트 데이터베이스에는 콘텐츠 파일이 저장된 사이트 서버의 위치에 대한 정보가 포함되어 있지만 백업 및 복구 프로세스 중에 콘텐츠 파일이 백업되거나 복원되지는 않습니다. 콘텐츠 파일을 완전히 복구하려면 콘텐츠 라이브러리와 패키지 원본 파일을 원래 위치로 복원해야 합니다. 콘텐츠 파일을 복구하는 방법은 몇 가지가 있지만 가장 쉬운 방법은 사이트 서버의 파일 시스템 백업에서 파일을 복원하는 것입니다.  

 패키지 원본 파일의 파일 시스템 백업이 없는 경우 패키지를 처음 만들 때 했던 대로 수동으로 복사하거나 다운로드해야 합니다. SQL Server에서 다음 쿼리를 실행하면 모든 패키지 및 응용 프로그램에 대한 패키지 원본 위치를 검색할 수 있습니다. `SELECT * FROM v_Package` 패키지 ID의 처음 세 문자를 보면 패키지 원본 사이트를 식별할 수 있습니다. 예를 들어 패키지 ID가 CEN00001이면 원본 사이트의 사이트 코드는 CEN입니다. 패키지 원본 파일을 복원할 때는 해당 파일을 실패 전에 있었던 위치로 복원해야 합니다.  

 콘텐츠 라이브러리가 포함된 파일 시스템 백업이 없는 경우에는 다음과 같은 복원 옵션이 있습니다.  

-   **사전 준비된 콘텐츠 파일 가져오기**: Configuration Manager 계층이 있으면 다른 위치의 모든 패키지와 응용 프로그램으로 사전 준비된 콘텐츠 파일을 만든 다음 사전 준비된 콘텐츠 파일을 가져와 사이트 서버의 콘텐츠 라이브러리를 복구할 수 있습니다.  

-   **콘텐츠 업데이트**: 패키지 또는 응용 프로그램 배포 유형에 대해 콘텐츠 업데이트 작업을 시작하면 패키지 원본의 콘텐츠가 콘텐츠 라이브러리로 복사됩니다. 이 작업을 성공적으로 마치려면 패키지 원본 파일이 원래 위치에 있어야 합니다. 각 패키지와 응용 프로그램에 대해 이 작업을 수행해야 합니다.  

#### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Updates Publisher를 실행하는 컴퓨터에서 사용자 지정 소프트웨어 업데이트 복구  
 백업 계획에 Updates Publisher 데이터베이스 파일을 포함했다면 Updates Publisher가 실행되는 컴퓨터에 실패가 발생할 경우 데이터베이스를 복구할 수 있습니다. Updates Publisher에 대한 자세한 내용은 System Center TechCenter 라이브러리에서 [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) 을 참조하세요.  

 다음 절차를 사용하여 Updates Publisher 데이터베이스를 복원합니다.  

###### <a name="to-restore-the-updates-publisher-2011-database"></a>Updates Publisher 2011 데이터베이스를 복원하려면  

1.  복구된 컴퓨터에 Updates Publisher를 다시 설치합니다.  

2.  Updates Publisher가 실행되는 컴퓨터에서 데이터베이스 파일(Scupdb.sdf)을 백업 대상에서 %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\으로 복사합니다.  

3.  컴퓨터에서 둘 이상의 사용자가 Updates Publisher를 실행하는 경우 각 데이터베이스 파일을 해당 사용자 프로필 위치로 복사해야 합니다.  

#### <a name="user-state-migration-data"></a>사용자 환경 마이그레이션 데이터  
 상태 마이그레이션 지점 사이트 시스템 속성의 일부로 사용자 환경 마이그레이션 데이터가 저장되는 폴더를 지정합니다. 사용자 환경 마이그레이션 데이터가 저장된 폴더를 사용하여 서버를 복구한 후에는 서버에서 오류 전 데이터가 저장된 폴더로 사용자 환경 마이그레이션 데이터를 복원해야 합니다.  

#### <a name="regenerate-the-certificates-for-distribution-points"></a>배포 지점에 대한 인증서 다시 생성  
 사이트를 복원한 후 distmgr.log에는 하나 이상의 배포 지점에 대해 **Failed to decrypt cert PFX data**항목이 포함될 수 있습니다. 이 항목은 사이트에서 배포 지점 인증서 데이터를 암호 해독할 수 없는 것을 나타냅니다. 이 문제를 해결하려면 영향을 받는 배포 지점에 대한 인증서를 다시 생성하거나 다시 가져와야 합니다. [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx) PowerShell cmdlet을 사용하여 그렇게 할 수 있습니다.  

#### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>클라우드 기반 배포 지점에 사용되는 인증서 업데이트  
 Configuration Manager에는 클라우드 기반 배포 지점 통신을 위해 사이트 서버에 사용되는 관리 인증서가 필요합니다. 사이트 복구 후에 클라우드 기반 배포 지점에 대한 인증서를 업데이트해야 합니다.  

####  <a name="a-namebkmkrecoversecondarysitea-recover-a-secondary-site"></a><a name="BKMK_RecoverSecondarySite"></a> 보조 사이트 복구  
 Configuration Manager에서는 보조 사이트에서의 데이터베이스 백업을 지원하는 것이 아니라 보조 사이트를 다시 설치하여 복구하는 작업을 지원합니다. Configuration Manager 보조 사이트가 실패할 경우 보조 사이트 복구가 필요합니다. Configuration Manager 콘솔의 **사이트** 노드에서 **보조 사이트 복구** 작업을 사용하여 보조 사이트를 복구할 수 있습니다. 중앙 관리 사이트 또는 기본 사이트에 대한 복구와 달리, 보조 사이트에 대한 복구에서는 백업 파일을 사용하지 않고 대신 실패한 보조 사이트 컴퓨터에 보조 사이트 파일을 다시 설치합니다. 그러면 보조 사이트 데이터가 부모 기본 사이트의 데이터로 다시 초기화됩니다. 복구 프로세스 중에 Configuration Manager는 보조 사이트 컴퓨터에 콘텐츠 라이브러리가 존재하고 해당 콘텐츠를 사용할 수 있는지 확인합니다. 해당 콘텐츠가 있으면 보조 사이트에서 기존 콘텐츠 라이브러리를 사용합니다. 그렇지 않은 경우 복구된 보조 사이트의 콘텐츠 라이브러리를 복구하려면 복구된 해당 사이트에 콘텐츠를 다시 배포하거나 사전 준비해야 합니다. 보조 사이트에 없는 배포 지점의 경우 보조 사이트 복구 시 배포 지점을 다시 설치할 필요가 없습니다. 보조 사이트 복구 후에 사이트가 배포 지점과 자동으로 동기화됩니다.  

 Configuration Manager 콘솔의 **사이트** 노드에서 **설치 상태 표시** 작업을 사용하여 보조 사이트 복구 상태를 확인할 수 있습니다.  

> [!IMPORTANT]  
>  보조 사이트를 성공적으로 복구하려면 실패한 컴퓨터와 FQDN 등이 동일한 구성을 갖는 컴퓨터를 사용해야 합니다. 또한 컴퓨터가 보조 사이트의 모든 전제 조건을 충족하고 적절한 보안 권한으로 구성되어 있어야 합니다. 또한 실패한 사이트에 사용된 것과 동일한 설치 경로를 사용합니다.  

> [!IMPORTANT]  
>  보조 사이트 복구 시에는 컴퓨터에 SQL Server Express가 설치되어 있지 않더라도 Configuration Manager에서 SQL Server Express를 설치하지 않습니다. 따라서 보조 사이트를 복구하기 전에 수동으로 SQL Server Express 또는 SQL Server를 설치해야 합니다. 실패 전 보조 사이트 데이터베이스에 사용한 버전과 인스턴스의 SQL Server를 동일하게 사용해야 합니다.  

##  <a name="a-namebkmksmswriterservicea-sms-writer-service"></a><a name="BKMK_SMSWriterService"></a> SMS 작성기 서비스  
 SMS 작성기는 백업 과정에서 VSS(볼륨 섀도 복사본 서비스)와 상호 작용하는 서비스입니다. Configuration Manager 사이트 백업이 성공적으로 완료되려면 SMS 작성기 서비스가 실행되어야 합니다.  

### <a name="purpose"></a>용도  
 SMS 작성기는 VSS 서비스에 등록되어 VSS 서비스 인터페이스 및 이벤트에 바인딩됩니다. VSS가 이벤트를 브로드캐스팅하는 경우, 즉 SMS 작성기에 특정 알림을 보내는 경우 SMS 작성기가 알림에 응답하여 적절한 조치를 취합니다. SMS 작성기는 <*Configuration Manager 설치 경로*>\inboxes\smsbkup.box에 있는 백업 제어 파일(smsbkup.ctl)을 읽고 백업할 파일과 데이터를 결정합니다. SMS 작성기는 이 정보와 함께 SMS 레지스트리 키 및 하위 키의 특정 데이터를 기반으로 다양한 구성 요소로 이루어진 메타데이터를 작성합니다. 그리고 요청 시 VSS에 메타데이터를 보냅니다. 그러면 VSS가 요청하는 응용 프로그램(Configuration Manager 백업 관리자)에 메타데이터를 전송합니다. 백업 관리자는 백업되는 데이터를 선택한 후 이 데이터를 VSS를 통해 SMS 작성기에 보냅니다. SMS 작성기는 적절한 단계를 수행하여 백업을 준비합니다. 이후에 VSS가 스냅숏을 생성할 준비가 되면 이벤트를 보냅니다. 그러면 SMS 작성기가 모든 Configuration Manager 서비스를 중지하여 스냅숏이 생성되는 동안 Configuration Manager 작업이 고정되도록 보장합니다. 스냅숏이 완료된 후에 SMS 작성기는 서비스와 작업을 다시 시작합니다.  

 SMS 작성기 서비스는 자동으로 설치됩니다. VSS 응용 프로그램이 백업 또는 복원을 요청할 때 이 서비스가 실행되고 있어야 합니다.  

### <a name="writer-id"></a>작성기 ID  
 SMS 작성기의 작성기 ID는 03ba67dd-dc6d-4729-a038-251f7018463b입니다.  

### <a name="permissions"></a>사용 권한  
 SMS 작성기 서비스는 로컬 시스템 계정으로 실행되어야 합니다.  

### <a name="volume-shadow-copy-service"></a>볼륨 섀도 복사본 서비스  
 VSS는 시스템의 응용 프로그램이 볼륨에 쓰기를 계속하는 동안 볼륨 백업이 수행될 수 있도록 하는 프레임워크를 구현하는 일련의 COM API입니다. VSS는 디스크에 데이터를 업데이트하는 사용자 응용 프로그램(SMS 작성기 서비스)과 응용 프로그램을 백업하는 사용자 응용 프로그램(백업 관리자 서비스) 간에 조정이 이루어질 수 있도록 일관된 인터페이스를 제공합니다. VSS에 대한 자세한 내용은 Windows Server TechCenter의 [Volume Shadow Copy Service(볼륨 섀도 복사본 서비스)](http://go.microsoft.com/fwlink/p/?LinkId=241968) 항목을 참조하세요.  



<!--HONumber=Dec16_HO3-->


