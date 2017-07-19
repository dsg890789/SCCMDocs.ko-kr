---
title: "가용성 그룹 구성 | Microsoft Docs"
description: "SCCM에서 SQL Server Always On 가용성 그룹을 설정하고 관리합니다."
ms.custom: na
ms.date: 5/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7e4ec207-bb49-401f-af1b-dd705ecb465d
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 138834b6cc64332202256961ad1d2f5ab6d176db
ms.contentlocale: ko-kr
ms.lasthandoff: 06/01/2017


---
# <a name="configure-sql-server-always-on-availability-groups-for-configuration-manager"></a>Configuration Manager용 SQL Server Always On 가용성 그룹 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 정보를 사용하여 Configuration Manager에서 사용하는 가용성 그룹을 구성하고 관리합니다.

시작하기 전에  
-   [Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)의 정보를 충분히 이해합니다.
-   가용성 그룹의 사용과 다음 시나리오를 완료하는 데 필요한 관련 절차를 다루는 SQL Server 설명서를 잘 숙지합니다.

> [!TIP]  
>  이 항목에 제공되는 SQL Server용 링크를 클릭하면 SQL Server 2016 관련 콘텐츠로 이동됩니다. 해당 버전의 SQL Server를 사용하지 않는 경우 사용 중인 버전에 대한 설명서를 참조합니다.

## <a name="create-and-configure-an-availability-group"></a>가용성 그룹 만들기 및 구성
다음 절차를 사용하여 가용성 그룹을 만들고 사이트 데이터베이스의 복사본을 해당 가용성 그룹으로 이동합니다.

이 절차를 완료하려면 사용하는 계정이 다음과 같아야 합니다.
-   가용성 그룹에 포함될 각 컴퓨터에 대한 **로컬 Administrator** 그룹의 구성원이어야 합니다.
-   사이트 데이터베이스를 호스트하는 각 SQL Server 인스턴스에서 **sysadmin**이어야 합니다.

### <a name="to-create-and-configure-an-availability-group-for-configuration-manager"></a>Configuration Manager용 가용성 그룹을 만들고 구성하려면  
1.    다음 명령을 사용하여 Configuration Manager 사이트를 중지합니다. **Preinst.exe /stopsite** Preinst.exe 사용에 대한 자세한 내용은 [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 참조하세요.

2.    사이트 데이터베이스의 백업 모델을 **단순** 에서 **전체**로 변경합니다.
SQL Server 문서에서 [데이터베이스의 복구 모델 보기 또는 변경](/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server) 을 참조하세요. 가용성 그룹은 전체만 지원합니다.

3.    SQL Server를 사용하여 사이트 데이터베이스의 전체 백업을 만들고, 사이트 데이터베이스를 호스트하는 서버가 새 가용성 그룹의 복제 구성원인지 여부에 따라 다음 중 하나를 수행합니다.
    -   **가용성 그룹의 구성원이 될 경우:**  
        이 서버를 가용성 그룹의 초기 기본 복제 구성원으로 사용하는 경우 사이트 데이터베이스의 복사본을 이 서버 또는 그룹의 다른 서버로 복원할 필요가 없습니다. 데이터베이스가 이미 기본 복제본에 배치되며, SQL Server는 이후 단계에서 데이터베이스를 보조 복제본으로 복제합니다.  

      -    **가용성 그룹의 구성원이 되지 않을 경우:**   
    그룹의 기본 복제본을 호스트하는 서버로 사이트 데이터베이스의 복사본을 복원해야 합니다.

    이 단계를 완료하는 방법에 대해서는 SQL Server 문서의 [전체 데이터베이스 백업 만들기](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) 및 [SSMS를 사용하여 데이터베이스 백업 복원](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)을 참조하세요.

4.    그룹의 초기 기본 복제본을 호스트하는 서버에서 [새 가용성 그룹 마법사](/sql/database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio)를 사용하여 가용성 그룹을 만듭니다. 마법사에서:
      -    **데이터베이스 선택** 페이지에서 Configuration Manager 사이트에 적합한 데이터베이스를 선택합니다.  

      -    **복제본 지정** 페이지에서 다음을 구성합니다.
          -    **복제본**: 보조 복제본을 호스트하는 서버를 지정합니다.

          -    **수신기**: **수신기 DNS 이름**을 정식 DNS 이름(예: **&lt;수신기_서버>.fabrikam.com**)으로 지정합니다. 이 이름은 가용성 그룹에서 데이터베이스를 사용하도록 Configuration Manager를 구성할 때 사용됩니다.

      -    **초기 데이터 동기화 선택** 페이지에서 **전체**를 선택합니다. 가용성 그룹을 생성하면 주 데이터베이스 및 트랜잭션 로그가 백업되고 보조 복제본을 호스트하는 각 서버에서 복원됩니다. 이 단계를 사용하지 않는 경우 보조 복제본을 호스트하는 각 서버로 사이트 데이터베이스의 복사본을 복원하고 그룹에 해당 데이터베이스를 수동으로 가입해야 합니다.   

5.    각 복제본에서 구성을 확인합니다.   
  1.    사이트 서버의 컴퓨터 계정이 가용성 그룹의 구성원인 각 컴퓨터에서 **로컬 관리자** 그룹의 구성원인지 확인합니다.  

  2.  필수 구성 요소에서 [확인 스크립트](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites)를 실행하여 각 복제본의 사이트 데이터베이스가 올바르게 구성되어 있는지 확인합니다.

  3.    보조 복제본에서 구성을 설정해야 하는 경우 기본 복제본의 데이터베이스만 구성할 수 있으므로 계속하기 전에 수동으로 기본 복제본을 보조 복제본으로 장애 조치(failover)해야 합니다. 자세한 내용은 SQL Server 설명서의 [가용성 그룹의 계획된 수동 장애 조치(Failover) 수행](/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server)을 참조하세요.

6.    모든 복제본이 이러한 요구 사항을 충족할 경우 가용성 그룹을 Configuration Manager에서 사용할 수 있습니다.

## <a name="configure-a-site-to-use-the-database-in-the-availability-group"></a>가용성 그룹에서 데이터베이스를 사용하도록 사이트 구성
[가용성 그룹을 만들고 구성](#create-and-configure-an-availability-group)한 후에 Configuration Manager 사이트 유지 관리를 사용하여 가용성 그룹에 의해 호스트되는 데이터베이스를 사용하도록 사이트를 구성합니다.

가용성 그룹에 해당 데이터베이스와 새 사이트를 함께 설치하는 것은 지원되지 않습니다. 예를 들어 기본 1702 미디어를 사용하는 경우 SQL Server의 단일 인스턴스를 사용하여 사이트를 설치해야 합니다. 사이트가 설치된 후에 사이트 데이터베이스를 가용성 그룹으로 이동할 수 있습니다.

이 절차를 완료하려면 Configuration Manager 설치 프로그램 실행에 사용하는 계정이 다음과 같아야 합니다.
-   가용성 그룹에 포함될 각 컴퓨터에 대한 **로컬 Administrator** 그룹의 구성원이어야 합니다.
-   사이트 데이터베이스를 호스트하는 각 SQL Server 인스턴스에 대한 **sysadmin** 권한

> [!IMPORTANT]
> Microsoft Intune 및 Configuration Manager를 하이브리드 구성으로 사용할 경우 사이트 데이터베이스를 가용성 그룹으로/으로부터 이동하면 데이터가 클라우드와 다시 동기화됩니다. 이 작업은 피할 수 없습니다.

### <a name="to-configure-a-site-to-use-the-availability-group"></a>가용성 그룹을 사용하도록 사이트를 구성하려면
1.    **&lt;*Configuration Manager 사이트 설치 폴더*>\BIN\X64\setup.exe**에서 **Configuration Manager 설치 프로그램**을 실행합니다.

2.    **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.

3.    **SQL Server 구성 수정** 옵션을 선택한 후 **다음**을 클릭합니다.

4.    사이트 데이터베이스에 대해 다음을 다시 구성합니다.
    -   **SQL Server 이름** : 가용성 그룹을 만들 때 구성한 가용성 그룹 **수신기**의 가상 이름을 입력합니다. 가상 이름은 **&lt;*endpointServer*>.fabrikam.com**과 같은 전체 DNS 이름이어야 합니다.  

    -   **인스턴스:** 가용성 그룹의 *수신기*에 대한 기본 인스턴스를 지정하려면 이 값을 비워두어야 합니다. 현재 사이트 데이터베이스가 명명된 인스턴스에 설치된 경우 명명된 인스턴스가 나열되므로 이를 제거해야 합니다.

    -   **데이터베이스:** 표시되는 이름을 그대로 둡니다. 이 이름은 현재 사이트 데이터베이스의 이름입니다.

5.    새 데이터베이스 위치에 대한 정보를 제공한 후 일반적인 프로세스와 구성을 사용하여 설치 프로그램을 완료합니다.



## <a name="add-and-remove-replica-members"></a>복제 구성원 추가 및 제거  
사이트 데이터베이스가 가용성 그룹에 호스트되는 경우 다음 절차에 따라 복제 구성원을 추가하거나 제거합니다. Configuration Manager는 기본 노드 1개와 최대 2개의 보조 노드를 지원합니다.

다음 절차를 완료하려면 사용하는 계정이 다음과 같아야 합니다.
-   가용성 그룹에 포함될 각 컴퓨터에 대한 **로컬 Administrator** 그룹의 구성원이어야 합니다.
-   사이트 데이터베이스를 호스트하거나 호스트할 각 SQL Server에서 **sysadmin**이어야 합니다.


### <a name="to-add-a-new-replica-member"></a>새 복제본 구성원을 추가하려면
1.    보조 복제본으로 새 서버를 가용성 그룹에 추가합니다. SQL Server 문서 라이브러리에서 [가용성 그룹에 보조 복제본 추가(SQL Server)](/sql/database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server)를 참조하세요.

2.    **Preinst.exe /stopsite**를 실행하여 Configuration Manager 사이트를 중지합니다. [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 참조하세요.

3.    SQL Server를 사용하여 주 복제본에서 사이트 데이터베이스의 백업을 만든 후 새로운 보조 복제본 서버로 해당 백업을 복원합니다. SQL Server 문서의 [전체 데이터베이스 백업 만들기](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) 및 [SSMS를 사용하여 데이터베이스 백업 복원](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)을 참조하세요.

4.    각 보조 복제본을 구성합니다. 가용성 그룹에 있는 각 보조 복제본에 대해 다음 작업을 수행합니다.

    1.    사이트 서버의 컴퓨터 계정이 가용성 그룹의 구성원인 각 컴퓨터에서 **로컬 관리자** 그룹의 구성원인지 확인합니다.

    2.    필수 구성 요소에서 [확인 스크립트](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites)를 실행하여 각 복제본의 사이트 데이터베이스가 올바르게 구성되어 있는지 확인합니다.

    3.    새 복제본을 구성해야 하는 경우 수동으로 기본 복제본을 새로운 보조 복제본으로 장애 조치(failover)한 후 필요한 설정을 수행합니다. SQL Server 문서에서 [가용성 그룹의 계획된 수동 장애 조치(Failover) 수행](/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server) 을 참조하세요.

5.    사이트 구성 요소 관리자(**sitecomp**) 및 **SMS_Executive** 서비스를 시작하여 사이트를 다시 시작합니다.

### <a name="to-remove-a-replica-member"></a>복제 구성원을 제거하려면
이 절차에서는 SQL Server 문서의 [가용성 그룹에서 보조 복제본 제거](/sql/database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server)에 나와 있는 정보를 사용합니다.

## <a name="stop-using-an-availability-group"></a>가용성 그룹 사용 중지
더 이상 사이트 데이터베이스를 가용성 그룹에 호스트하지 않으려는 경우 다음 절차를 따르세요. 이 절차를 진행하면 사이트 데이터베이스가 SQL Server의 단일 인스턴스로 다시 이동됩니다.

이 절차를 완료하려면 사용하는 계정이 다음과 같아야 합니다.
-   가용성 그룹에 포함될 각 컴퓨터에 대한 **로컬 Administrator** 그룹의 구성원이어야 합니다.
-   사이트 데이터베이스를 호스트하는 각 SQL Server 인스턴스에 대한 **sysadmin** 권한

> [!IMPORTANT]  
> Microsoft Intune 및 Configuration Manager를 하이브리드 구성으로 사용할 경우 사이트 데이터베이스를 가용성 그룹으로/으로부터 이동하면 데이터가 클라우드와 다시 동기화됩니다. 이 작업은 피할 수 없습니다.

### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>사이트 데이터베이스를 가용성 그룹에서 단일 SQL Server 인스턴스를 다시 가용성 그룹에서 단일 SQL Server 인스턴스로 사이트 데이터베이스를 다시 이동하려면
1.    다음 명령을 사용하여 Configuration Manager 사이트를 중지합니다. **Preinst.exe /stopsite** 자세한 내용은 [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 참조하세요.

2.    SQL Server를 사용하여 주 복제본에서 사이트 데이터베이스의 전체 백업을 만듭니다. 이 단계를 완료하는 방법에 대해서는 [SQL Server 문서의 전체 데이터베이스 백업 만들기](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) 를 참조하세요.

3.    가용성 그룹의 기본 복제본인 서버에서 사이트 데이터베이스의 단일 인스턴스를 호스트할 경우 이 단계를 건너뛸 수 있습니다.  

    -   SQL Server를 사용하여 사이트 데이터베이스를 호스트하는 서버로 사이트 데이터베이스 백업을 복원합니다. SQL Server 설명서의 [SSMS를 사용하여 데이터베이스 백업 복원](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)을 참조하세요.   <br />  <br />

4.    사이트 데이터베이스를 호스트하는 서버(기본 복제본 또는 사이트 데이터베이스를 복원한 서버)에서 사이트 데이터베이스의 백업 모델을 **전체**에서 **간단**으로 변경합니다. SQL Server 문서에서 [데이터베이스의 복구 모델 보기 또는 변경](/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server) 을 참조하세요.  

5.    **&lt;*Configuration Manager 사이트 설치 폴더>*\BIN\X64\setup.exe**에서 **Configuration Manager 설치 프로그램**을 실행합니다.

6.    **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.  

7.    **SQL Server 구성 수정** 옵션을 선택한 후 **다음**을 클릭합니다.  

8.    사이트 데이터베이스에 대해 다음을 다시 구성합니다.
    -   **SQL Server 이름:** 이제 사이트 데이터베이스를 호스트하는 서버의 이름을 입력합니다.

    -   **인스턴스:** 사이트 데이터베이스를 호스트하는 명명된 인스턴스를 지정하거나 데이터베이스가 기본 인스턴스에 있으면 이 필드를 공백으로 둡니다.

    -   **데이터베이스:** 표시되는 이름을 그대로 둡니다. 이 이름은 현재 사이트 데이터베이스의 이름입니다.    

9.    새 데이터베이스 위치에 대한 정보를 제공한 후 일반적인 프로세스와 구성을 사용하여 설치 프로그램을 완료합니다. 설치가 완료되면 사이트가 다시 시작되고 새 데이터베이스 위치를 사용합니다.    

10.    가용성 그룹의 구성원인 서버를 정리하려면 SQL Server 문서에 있는 [가용성 그룹 제거](/sql/database-engine/availability-groups/windows/remove-an-availability-group-sql-server) 항목의 지침을 따릅니다.

