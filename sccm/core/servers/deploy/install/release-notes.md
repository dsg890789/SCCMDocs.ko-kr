---
title: "릴리스 정보 | Microsoft 문서"
description: "Microsoft 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해서는 이 정보를 참조하세요."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 41
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: ea723a6694feb2c9584b35498aa9c3519383f08d
ms.openlocfilehash: a9dc046a54c15d9d299664cd1f2a149383f53489


---
# <a name="release-notes-for-system-center-configuration-manager"></a>System Center Configuration Manager의 릴리스 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 제품에서 수정되지 않은 긴급한 문제(콘솔 내 업데이트를 통해 사용 가능) 또는 Microsoft 기술 자료 문서에 자세히 설명되지 않은 긴급한 문제로 제품 릴리스 정보가 제한됩니다.  

 핵심 시나리오에 영향을 주는 알려진 문제의 경우 이 정보는 System Center Configuration Manager 문서 라이브러리의 온라인 제품 설명서에 포함되어 있습니다.  

> [!TIP]  
>  이 항목에는 System Center Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. System Center Configuration Manager의 Technical Preview의 경우 [System Center Configuration Manager용 Technical Preview](../../../../core/get-started/technical-preview.md)를 참조하세요.  

## <a name="setup-and-upgrade"></a>설치 및 업그레이드  

### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>버전 1606을 사용하여 장기 서비스 분기 사이트를 설치하는 경우 현재 분기 사이트가 설치됨
2016년 10월 릴리스의 버전 1606 기준 미디어를 사용하여 LTSB(장기 서비스 분기) 사이트를 설치하는 경우 현재 분기 사이트가 대신 설치됩니다. 이 문제는 사이트 설치를 사용하여 서비스 연결 지점을 설치하는 옵션을 선택하지 않았기 때문에 발생합니다.

 - 서비스 연결 지점이 필요하지 않더라도 LTSB 사이트를 설치하려면 설치 중에 선택해야 합니다.

설치가 완료된 후 서비스 연결 지점을 제거할 수 있습니다.  그러나 원격 분석 데이터를 제출하고 현재 분기 및 LTSB 사이트 둘 다에 대한 보안 업데이트를 가져오려면 오프라인 또는 온라인 모드의 서비스 연결 지점이 있어야 합니다.

사이트가 현재 분기 사이트로 설치되었지만 LTSB를 설치하려는 경우 사이트를 제거한 후 다시 설치할 수 있습니다. 또는 [Microsoft 도움말 및 지원](http://go.microsoft.com/fwlink/?LinkId=243064)에 도움을 요청할 수 있습니다.  

설치된 분기를 확인하려면 콘솔의 **관리** > **사이트 구성** > **사이트**에서 **계층 설정**을 엽니다. 사이트를 현재 분기 사이트로 변환하는 옵션은 사이트에서 LTSB를 실행하는 경우에만 사용할 수 있습니다.  

**해결 방법:**  없습니다.   





### <a name="the--sql-server-backup-model-in-use-by-configuration-manager-can-change-from-full-to-simple"></a>Configuration Manager에서 사용 중인 SQL Server 백업 모델을 전체에서 단순으로 변경할 수 있습니다.  
 System Center Configuration Manager 버전 1511로 업그레이드하면 Configuration Manager에서 사용 중인 SQL Server 백업 모델이 전체에서 단순으로 변경될 수 있습니다.  

-   Configuration Manager의 기본 제공 백업 작업 대신 전체 백업 모델로 사용자 지정 SQL Server 백업 작업을 사용하는 경우 업그레이드 중에 백업 모델이 전체에서 단순으로 변경될 수 있습니다.  

**해결 방법**: 버전 1511로 업그레이드한 후 SQL Server 구성을 검토하고 필요한 경우 전체로 복원합니다.  

### <a name="when-you-add-a-service-window-to-a-new-site-server-service-windows-that-were---configured-for-another-site-server-are-deleted"></a>새 사이트 서버에 서비스 창을 추가한 경우 다른 사이트 서버에 대해 구성된 서비스 창이 삭제되었습니다.  
 System Center Configuration Manager 버전 1511에서 서비스 창을 사용하는 경우 계층에서 단일 사이트 서버에 대한 서비스 창만 구성할 수 있습니다. 한 서버에서 서비스 창을 구성한 후 두 번째 사이트 서버에서 서비스 창을 구성하면 첫 번째 사이트 서버의 서비스 창이 경고 또는 오류 없이 자동으로 삭제됩니다.  

**해결 방법**: [Microsoft 기술 자료 문서 3142341](http://support.microsoft.com/kb/3142341)에서 핫픽스를 설치합니다. System Center Configuration Manager의 1602 업데이트를 설치하는 경우 이 문제도 해결됩니다.  

### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Configuration Manager 콘솔의 업데이트 및 서비스 노드에서 업데이트가 다운로드 중 상태로 고정됩니다.  
온라인 서비스 연결 지점을 통해 업데이트를 자동으로 다운로드하는 동안 업데이트가 다운로드 중 상태로 고정될 수 있습니다. 업데이트의 다운로드가 고정되면 걸려 표시된 로그 파일에 다음과 유사한 항목이 표시됩니다.  

DMPdownloader 로그:  

-   ERROR: Failed to download redist for 037cd17e-4d7b-40e1-802b-14bb682364c7 with command  /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 /RedistVersion 112015 /NoUI  "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Error: failed to verify 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi' authenticode signature.  

-   Error: file signature check failed for 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi  

**해결 방법**: 사이트 서버에서 다음 레지스트리 키를 다음과 일치하도록 수정한 후 SMS_Executive 서비스를 다시 시작하거나 다음 자동 다운로드 주기를 위해 최대 24시간 동안 대기합니다.  

-   **편집할 키**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software Publishing  

-   **상태 값**: **146944** 10진수 또는 **0x00023e00** 16진수로 설정  

### <a name="pre-release-features-introduced-in-system-center-configuration-manager-1602"></a>System Center Configuration Manager 1602에 도입된 시험판 기능  

시험판 기능은 프로덕션 환경의 초기 테스트를 위한 제품에 포함되었지만 이러한 기능은 프로덕션 준비가 된 것으로 간주되지 않아야 합니다.  

업데이트 1606부터 시험판 기능을 사용하려면 먼저 동의해야 합니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](../../../../core/servers/manage/install-in-console-updates.md)을 참조하세요.

System Center Configuration Manager 버전 1602에서는 다음과 같은 두 시험판 기능을 제공합니다.  

-   System Center Configuration Manager에서 관리되는 PC에 대한 조건부 액세스 자세한 내용은 [System Center Configuration Manager에서 관리되는 PC용 O365 서비스에 대한 액세스 관리](../../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)를 참조하세요.
    - 업데이트 1602를 설치하면 기능 유형이 시험판 버전임에도 출시됨으로 표시됩니다.
    - 그런 다음 1602에서 1606으로 업데이트하면 기능 유형이 여전히 시험판인 경우에도 출시됨으로 표시됩니다.
    - 버전 1511에서 1606으로 바로 업데이트하면 기능 유형이 시험판으로 표시됩니다.


-   클러스터 인식 컬렉션 서비스 제공. 자세한 내용은 [System Center Configuration Manager의 Technical Preview 1605 기능](../../../../core/get-started/capabilities-in-technical-preview-1605.md)의 [서버 그룹 처리](../../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)를 참조하세요.  




### <a name="recovery-options-for-a-secondary-site-are-not-available-in-the-console"></a>보조 사이트를 위한 복구 옵션은 콘솔에서 사용할 수 없습니다.  
보조 사이트 복구에 실패하면 옵션 **보조 사이트 복구**를 Configuration Manager 콘솔에서 더는 사용하지 못할 수 있습니다.  

System Center Configuration Manager 버전 1511 및 1602에 영향을 주는 이 문제는 향후 업데이트에서 해결할 예정입니다.  

**해결 방법**: 다음 방법 중 하나를 사용하여 보조 사이트 복구(다시 설치)  

-   **Preinst.exe** 및 **/delsite** 명령을 사용하여 보조 사이트를 제거한 다음 보조 사이트를 다시 설치합니다. Preinst.exe에 대한 내용은 [System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)를 참조하세요.  

-   다음 스크립트를 실행하여 보조 사이트 복구를 시작합니다. 복구할 보조 사이트의 기본 상위 사이트에 있는 데이터베이스에서 이 스크립트를 실행합니다.  

    ```  
    declare @SiteCode NVARCHAR(3)=N'<replace with secondary site code>'   

    UPDATE Sites SET Status = 9  
                    , DetailedStatus = 3  
    FROM Sites WHERE SiteCode = @SiteCode  

    UPDATE SCP SET SCP.Value1 = 9  
                    , SCP.Value2 = N'3'  
    FROM SC_SiteDefinition_Property SCP INNER JOIN SC_SiteDefinition SC ON SC.SiteNumber = SCP.SiteNumber  
    WHERE SC.SiteCode = @SiteCode AND SCP.[Name] = N'Requested Status'  
  ```  

###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>CD.Latest 폴더에서 재배포 파일을 사용하는 경우 매니페스트 확인 오류와 함께 설치가 실패합니다.
1606 버전에 대해 만든 CD.Latest 폴더에서 설치 프로그램을 실행하고 그 CD.Latest 폴더에 포함된 재배포 파일을 사용하는 경우 Configuration Manager 설치 로그에서 다음 오류와 함께 설치가 실패합니다.

  - 오류: defaultcategories.dll에 대해 파일 해시를 확인하지 못했습니다.
  - 오류: 매니페스트를 확인하지 못했습니다. 잘못된 매니페스트 버전인가요?

**해결 방법:** 다음 방법 중 하나를 사용합니다.
 - 설치 시 CD.Latest 폴더에 포함된 재배포 파일을 사용하는 대신 Microsoft에서 최신 재배포 파일을 다운로드하도록 선택합니다.
 - 수동으로 *cd.latest\redist\languagepack\zhh* 폴더를 삭제한 다음 설치 프로그램을 다시 실행합니다.

### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>SQL Server가 원격이거나 공유 메모리가 사용되지 않는 경우 서비스 연결 도구에서 예외가 발생합니다.
버전 1606부터 서비스 연결 도구는 다음 중 하나가 충족될 경우 예외를 생성합니다.  
 -  사이트 데이터베이스가 서비스 연결 지점을 호스트하고 비표준 포트(1433 이외의 포트)를 사용하는 컴퓨터에서 원격인 경우
 -  사이트 데이터베이스가 서비스 연결 지점과 동일한 서버에 있지만 SQL 프로토콜 **공유 메모리**가 사용되지 않는 경우

예외는 다음과 유사합니다.
 - *처리되지 않은 예외: System.Data.SqlClient.SqlException: SQL Server에 대한 연결을 설정하는 동안 네트워크 관련 또는 인스턴스 관련 오류가 발생했습니다. 서버를 찾을 수 없거나 액세스할 수 없습니다. 인스턴스 이름이 올바르고 SQL Server가 원격 연결을 허용하도록 구성되었는지 확인합니다. (공급자: 명명된 파이프 공급자, 오류: 40 - SQL Server에 대한 연결을 열 수 없음) - *

**해결 방법**: 도구를 사용하는 동안 SQL Server 포트에 대한 정보를 포함하도록 서비스 연결 지점을 호스트하는 서버의 레지스트리를 수정해야 합니다.

   1.   도구를 사용하기 전에 다음 레지스트리 키를 편집하고 사용 중인 포트 번호를 SQL Server의 이름에 추가합니다.
    - 키: HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - 값: &lt;SQL Server 이름>
    - 추가: **,&lt;포트>**

    예를 들어 *testserver.test.net*이라는 서버에 *15001* 포트를 추가하려는 경우 결과로 생성되는 키는 ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.net,15001***입니다.

   2.   레지스트리에 포트를 추가하면 도구기 정상적으로 작동합니다.  

   3.   도구 사용이 완료되면 **-connect** 및 **-import** 단계 둘 다에서 레지스트리 키를 원래 값으로 다시 변경합니다.  






## <a name="backup-and-recovery"></a>백업 및 복구
### <a name="pre-production-client-is-not-available-after-a-site-restore"></a>사이트 복원 후 사전 프로덕션 클라이언트를 사용할 수 없음
버전 1602와 함께 사전 프로덕션 클라이언트를 사용할 때 계층 구조의 최상위 계층 사이트를 백업에서 복원하면 사이트 복원 후 사전 프로덕션 클라이언트 버전을 사용할 수 없게 됩니다.  

**해결 방법:** 계층 구조의 최상위 계층 사이트를 복원한 후에 수동으로 사전 프로덕션 클라이언트 파일을 복사해야 합니다. 그러면 Configuration Manager가 그 파일을 처리하고 사용할 수 있도록 복원할 수 있습니다.
1. 최상위 계층 사이트 서버 컴퓨터에서*&lt;CM_Install_Location\>\\Client* 폴더의 내용을 *&lt;CM_Install_Location\>\\StagingClient* 폴더에 복사합니다.

2. **client.acu**라는 빈 파일을 만들고 이 파일을 사이트 서버의 *&lt;CM_Install_Location\>\\Inboxes\\hman.box* 폴더에 복사합니다. 이 파일은 이제 txt 확장명이 없기 때문에 이름이 변경된 텍스트 파일일 수 있습니다. 이 파일을 hman.box 폴더에 놓으면 사이트 서버에서 Hierarchy Manager가 시작하여 클라이언트 파일을 처리하고 사용할 사전 프로덕션 클라이언트 파일을 복원합니다.

이 문제는 버전 1606에서 해결되었습니다.


## <a name="client-deployment-and-upgrade"></a>클라이언트 배포 및 업그레이드  

### <a name="expansion-to-central-administration-site-stops-automatic-client-upgrades"></a>중앙 관리 사이트로 확장하면 자동 클라이언트 업그레이드가 중지됩니다.  
버전 1511에서만, 기본 사이트에서 중앙 관리 사이트로 확장되는 모든 사이트에 대해 자동 클라이언트 업그레이드를 실행할 수 없습니다. 사이트가 확장될 때 클라이언트 업그레이드 패키지의 신뢰할 수 있는 사이트가 새 중앙 관리 사이트로 올바르게 설정되지 않아서, 자동 클라이언트 업그레이드 작업이 성공적으로 실행되지 않습니다. 이 문제는 1511 버전에만 존재합니다. 1602 이상 버전에서는 이 문제가 해결되었습니다.  

**해결 방법**: 중앙 관리 사이트 데이터베이스에서 다음 SQL 스크립트를 실행합니다. 스크립트를 실행한 후에는 자동 클라이언트 업그레이드가 정상적으로 실행됩니다.  

  ```  
  DECLARE @RootSite AS NVARCHAR(3)  
  DECLARE @SourceServer AS NVARCHAR(255)  
  DECLARE @FullClientPkgSource AS NVARCHAR(255)  
  DECLARE @UpgradePkgSource AS NVARCHAR(255)  

  SELECT @RootSite = SiteCode, @SourceServer = SiteServer  
  FROM sites  
  WHERE ISNULL(ReportToSite, N'') = N''  

  SELECT @FullClientPkgSource = N'\\' + @SourceServer + N'\SMS_' + @RootSite + N'\Client'  
  SELECT @UpgradePkgSource = N'\\' + @SourceServer + N'\SMS_' + @RootSite + N'\ClientUpgrade'  

  UPDATE SMSPackages_G  
  SET Source = @FullClientPkgSource, SourceSite = @RootSite  
  WHERE PkgID IN  
      (SELECT FullPackageID FROM ClientDeploymentSettings)  

  UPDATE SMSPackages_G  
  SET Source = @UpgradePkgSource, SourceSite = @RootSite  
  WHERE PkgID IN  
      (SELECT UpgradePackageID FROM ClientDeploymentSettings)  

  UPDATE ProgramOffers_G  
  SET SourceSite = @RootSite  
  WHERE OfferID IN  
      (SELECT UpgradeAdvertisementID FROM ClientDeploymentSettings)  
  ```  

## <a name="operating-system-deployment"></a>운영 체제 배포  

### <a name="issue-with-the-windows-adk-for-windows-10-version-1511"></a>Windows 10용 Windows ADK 버전 1511 문제  
Windows ADK 10 버전 1511에서 Windows PE v.10.0.10586 부팅 이미지를 사용하는 소프트웨어 센터에서 작업 순서를 실행하는 경우 컴퓨터가 Windows PE로 다시 시작되면 "하드웨어 장치를 초기화하는 중" 다음과 같은 오류로 인해 실패합니다. **0x80220014 오류 코드로 인해 Windows PE를 초기화하지 못했습니다.**  

**해결 방법**: 원래 Windows 10 ADK를 사용합니다. 자세한 내용은 다음 System Center Configuration Manager 팀 블로그를 참조하세요. [Issue with the Windows ADK for Windows 10](http://blogs.technet.com/b/configmgrteam/archive/2015/11/20/issue-with-the-windows-adk-for-windows-10-version-1511.aspx)(Windows 10용 Windows ADK 문제)  

### <a name="dynamic-application-installation-fails-during-task-sequence-which-successfully-completes"></a>성공적으로 완료되는 작업 순서 중 동적 응용 프로그램 설치가 실패합니다.  
**동적 변수 목록에 따라 응용 프로그램 설치**옵션을 사용하는 작업 순서를 배포하지만 어떤 이유로든 응용 프로그램 중 하나가 설치하지 못한 경우에도 작업 순서에서 성공을 보고합니다. 다음 옵션을 구성하는 방법과 상관없이 이런 상황이 발생합니다.  

-   **오류 발생 시 계속** (응용 프로그램 설치 단계의 옵션 탭에서)  

-   **응용 프로그램 설치가 실패할 경우 목록의 다른 응용 프로그램 설치 계속** (응용 프로그램 설치 단계의 속성 탭에서)  

smsts.log에서 응용 프로그램이 설치에 실패하는지 여부를 확인할 수 있습니다.  

**해결 방법**: 동적 응용 프로그램 중 하나에서 오류가 발생하는 경우 작업 순서 실패 조건이 포함된 작업 순서의 후속 단계에서 조건으로 **_TSAppInstallStatus** 변수를 사용합니다.  

### <a name="smb-might-not-work-properly-after-you-use-a-task-sequence-to-install-windows-10"></a>작업 순서를 사용하여 Windows 10을 설치한 후 SMB가 제대로 작동하지 않습니다.  
작업 순서를 사용하여 Windows 10 이미지를 설치하면 Configuration Manager 클라이언트가 설치된 후 SMB가 제대로 작동하지 않을 수 있습니다. 예를 들어 다음 작업 순서 단계가 실패할 수 있습니다.  

-   상태 마이그레이션 지점에서 사용하는 경우 사용자 상태 복원  

-   네트워크 폴더에 연결  

F8 관리자 명령 프롬프트에서 예를 들어 컴퓨터를 Ping할 수 있지만 모든 SMB 네트워크 트래픽(예: 명령 프롬프트의 NET USE)이 1231 오류로 실패할 수 있습니다. 즉, 네트워크 위치에 연결할 수 없습니다.  

**해결 방법**:  
Windows 및 ConfigMgr 설치 작업 순서 단계를 중지한 후 명령줄 실행 작업 순서 단계를 추가한 후 다음과 같이 워크스테이션 서비스를 시작합니다.    
**net stop workstation /y & net start workstation**  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>서비스 계획에서 기본적으로 중복 소프트웨어 업데이트 그룹을 많이 만들고 배포합니다.  
기본적으로 서비스 계획 만들기 마법사는 현재 소프트웨어 업데이트를 동기화한 후마다 실행됩니다. 마법사가 실행될 때마다 새 소프트웨어 업데이트 그룹 및 배포가 생성됩니다. 예를 들어 하루에 여러 번 실행되는 소프트웨어 업데이트 동기화 일정을 사용하는 경우 계획 서비스 만들기 마법사에서 매일 거의 동일한 소프트웨어 업데이트 그룹 및 배포를 여러 개 만듭니다.  

**해결 방법**:    
서비스 계획을 만든 후 서비스 계획에 대한 속성을 열고, **평가 일정** 탭으로 이동하고, **일정에 따라 규칙 실행**을 선택하고, **사용자 지정**을 클릭하여 사용자 지정 일정을 만듭니다. 예를 들어 60일마다 실행하는 서비스 계획이 있을 수 있습니다.  

## <a name="mobile-device-management"></a>모바일 장치 관리  

### <a name="cannot-create-an-enrollment-profile-on-a-primary-site"></a>기본 사이트에 등록 프로필을 만들 수 없습니다.  
관리자가 기본 사이트에 연결하는 System Center Configuration Manager 관리 콘솔에서 등록 프로필을 만들 수 없습니다. 등록하려고 시도할 때 등록 프로필 마법사에서 "DEP 토큰이 업데이트되지 않았습니다. DEP 토큰을 업로드하세요." 오류가 관리자에게 표시됩니다. 유효한 DEP 토큰이 중앙 관리 사이트에 업로드된 경우에도 이 오류가 발생합니다.  

**해결 방법**: 중앙 관리 사이트에 연결하는 System Center Configuration Manager 콘솔에서 등록 프로필을 만듭니다.  

### <a name="dep-cannot-use-non-alpha-numeric-characters-in-enrollment-profiles"></a>DEP에서 등록 프로필에 영숫자가 아닌 문자를 사용할 수 없습니다.  
DEP(장치 등록 프로필)가 사용되는 경우 Apple의 DEP와 연결된 등록 프로필의 **이름**, **설명**, **부서** 및 **전화 번호** 필드에서 영숫자가 아닌 문자를 사용할 수 없습니다. 이러한 필드에 영숫자가 아닌 문자를 사용하면 등록 프로필이 만들어지지만 프로필을 Apple에 업로드할 수 없습니다. Apple 서버에서 오류 메시지 또는 경고를 제공하지 않으며 프로필이 DEP 관리 장치에 배포되지 않습니다.  

**해결 방법** :없음

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>전체 초기화를 진행하면 RAM이 4GB 미만인 Windows 10 장치를 사용하지 못하게 됩니다.

RAM이 4GB 미만인 Windows 10 RTM 장치(버전 1511보다 이전 버전)에 전체 초기화를 진행하면 장치가 사용할 수 없는 상태가 됩니다. 장치 초기화를 시도하면 장치는 시작 불능 상태가 되어 응답이 불가능합니다.

**해결 방법**: Windows 10 RTM PC에 전체 초기화를 진행하기 전에 장치의 가용 RAM이 4GB 이상인지 확인하세요. Windows 10 장치의 버전 번호를 보려면 명령 프롬프트에서 'winver'를 입력합니다. 장치가 이미 초기화되어 이제 응답하지 않는 경우 부팅 가능 Windows 10 USB 드라이브를 사용하여 장치에 대한 액세스를 시작하여 복구합니다.

### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>계약조건 정책이 배포된 둘 이상의 사용자 컬렉션에 속한 사용자에게 동일한 사용 약관의 여러 집합이 표시됩니다.  

관리자가 여러 사용자 컬렉션에 사용 약관 집합을 배포하며 사용자가 이러한 컬렉션 중 둘 이상의 멤버인 경우 회사 포털을 열 때 해당 사용자에게 동일한 사용 약관의 여러 복사본이 표시됩니다.  예를 들어 "SampleUser"라는 사용자가 "CompanyEmployeesFTE"와 "CompanyEmployeesNA"라는 두 개의 서로 다른 사용자 컬렉션의 멤버이고, "CompanyTerms"라는 계약조건이 CompanyEmployeesFTE와 CompanyEmployeesNA 모두에 배포된 경우 사용 약관 동의 페이지에서 CompanyTerms의 동일한 집합 두 개가 SampleUser에게 표시됩니다. 사용자는 모든 사용 약관을 수락하거나 거절할 수만 있으므로 사용자가 사용 약관을 수락도 하고 거절도 하게 되는 모호한 동의 상태가 될 위험은 없습니다. 사용 약관 동의 보고서에는 사용자의 각 약관이 단일 행에 표시되므로 보고서에 오류가 나타나지 않습니다. 유일한 영향은 동의 페이지에서 두 개의 사용 약관 집합이 사용자에게 표시된다는 것입니다.  

**해결 방법**: 각 사용자가 사용 약관이 배포된 한 컬렉션에만 포함되어 있는지 확인합니다.  

## <a name="reports-and-monitoring"></a>보고서 및 모니터링  

### <a name="the-health-attestation-report-is-empty-even-though-health-attestation-data-was-previously-collected"></a>상태 증명 데이터가 이전에 수집된 경우에 상태 증명 보고서가 비어 있습니다.  
**상태 증명** 권한 그룹에 대한 **읽기** 권한을 포함하는 보안 역할이 있는 관리자가 상태 증명 보고서를 볼 때 보고서는 비어 있으며 데이터를 표시하지 못합니다. 증명 상태 보고서의 데이터를 볼 수 있는 권한이 상태 증명 권한 그룹이 아닌 **사용자 장치 선호도** 권한에 연결되기 때문입니다.  

System Center Configuration Manager 버전 업데이트 1602에 영향을 주는 이 문제는 향후 업데이트에서 해결할 예정입니다.  

**해결 방법**: **사용자 장치 선호도** 권한 그룹에 대한 **읽기** 권한을 포함하는 보안 그룹에 관리자를 할당합니다.  

### <a name="conditional-access"></a>조건부 액세스  

#### <a name="the-same-user-collection-is-not-blocked-from-being-added-to-both-exempted-and-targeted-collections"></a>동일한 사용자 컬렉션은 예외 컬렉션 및 대상 컬렉션 모두에 추가되지 않습니다.  
**대상 컬렉션** 페이지에 **사용자 컬렉션**을 추가하기 전에 **예외 컬렉션** 페이지에 동일한 사용자 컬렉션을 추가하는 경우에만 이런 상황이 발생합니다.  먼저 **대상 컬렉션** 페이지에 **사용자 컬렉션**을 추가한 후 **예외 컬렉션** 페이지에 동일한 **사용자 컬렉션**을 추가하면 일반적인 차단 메시지가 표시됩니다.  

이 문제는 업데이트 1602가 설치된 **Exchange 온-프레미스**에 대한 System Center Configuration Manager 조건부 액세스에 영향을 주며, 향후 업데이트에서 해결될 것으로 예상됩니다.  

**해결 방법**: **예외 컬렉션** 페이지에서 **사용자 컬렉션**을 선택하기 전에 **대상 컬렉션** 페이지에 **사용자 컬렉션**을 추가하거나 대상 및 예외 컬렉션 모두에 동일한 **사용자 컬렉션**을 추가하지 않았는지 확인합니다.



<!--HONumber=Dec16_HO3-->


