---
title: "SQL Server AlwaysOn | Microsoft 문서"
ms.custom: na
ms.date: 1/4/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: aaaab003ddd22f18160d4be63cfeab3a7e7f6b03
ms.lasthandoff: 03/27/2017


---
# <a name="sql-server-alwayson-for-a-highly-available-site-database-for-system-center-configuration-manager"></a>System Center Configuration Manager용 항상 사용 가능한 사이트 데이터베이스를 위한 SQL Server AlwaysOn

*적용 대상: System Center Configuration Manager(현재 분기)*


 System Center Configuration Manager 버전 1602부터, SQL Server [AlwaysOn 가용성 그룹](https://msdn.microsoft.com/library/hh510230\(v=sql.120\).aspx) 을 사용하여 기본 사이트와 중앙 관리 사이트에서 사이트 데이터베이스를 고가용성 및 재해 복구 솔루션으로 호스트할 수 있습니다. 가용성 그룹은 온-프레미스 또는 Microsoft Azure에서 호스트될 수 있습니다.  

 Microsoft Azure를 사용하여 가용성 그룹을 호스트하는 경우 Azure 가용성 집합과 함께 SQL Server AlwaysOn 가용성 그룹을 사용하여 사이트 데이터베이스의 가용성을 더 늘릴 수 있습니다. Azure 가용성 집합에 대한 자세한 내용은 [가상 컴퓨터의 가용성 관리](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)를 참조하세요.  

 Configuration Manager에서는 내부 또는 외부 부하 분산 장치 뒤에 있는 SQL 가용성 그룹에 사이트 데이터베이스를 호스트할 수 있습니다. 이를 위해서는 각 복제본에서 방화벽 예외를 구성하는 것 외에 다음 포트에 대해 부하 분산 규칙을 추가해야 합니다.
  - SQL over TCP: TCP 1433
  - SQL Server Service Broker: TCP 4022
  - SMB(서버 메시지 블록): TCP 445
  - RPC 끝점 매퍼: TCP 135


다음은 가용성 그룹에 대해 지원되는 시나리오입니다.  

-   가용성 그룹의 기본 인스턴스로 사이트 데이터베이스를 이동할 수 있습니다.  

-   사이트 데이터베이스를 호스트하는 가용성 그룹에서 복제 구성원을 추가하거나 제거할 수 있습니다.  

-   독립 실행형 SQL Server의 기본 또는 명명된 인스턴스로 가용성 그룹의 사이트 데이터베이스를 이동할 수 있습니다.  

> [!Important]  
> Microsoft Intune 및 Configuration Manager를 하이브리드 구성으로 사용할 경우 사이트 데이터베이스를 가용성 그룹으로/으로부터 이동하면 데이터가 클라우드와 다시 동기화됩니다. 이 작업은 피할 수 없습니다. 



> [!NOTE]  
>  성공적인 구성 및 가용성 그룹의 사용을 위해서는 SQL Server 및 SQL Server 가용성 그룹 구성에 대해 잘 알고 있어야 합니다. 이 항목의 System Center Configuration Manager 관련 절차에서는 SQL Server 문서 라이브러리에 있는 추가 문서 및 절차를 사용합니다.  

 **Configuration Manager에서 AlwaysOn 가용성 그룹을 사용하는 경우 알려진 문제:**  

-   **가용성 그룹을 사용하도록 Configuration Manager를 설정할 때 모든 복제본 서버에서 동일한 파일 경로가 필요함:**  

    -   Configuration Manager 설치 프로그램을 실행하여 가용성 그룹의 데이터베이스를 사용하도록 사이트를 리디렉션할 때 그룹의 각 보조 복제본 서버에는 현재 기본 복제본의 사이트 데이터베이스 파일을 호스트하는 데 사용된 파일 경로와 동일한 파일 경로가 있어야 합니다. 동일한 경로가 보조 복제본에 없는 경우 설치 프로그램에서 가용성 그룹 인스턴스를 사이트 데이터베이스의 새 위치로 추가하지 못합니다.  

         또한 각 보조 복제본 서버의 로컬 SQL Server 서비스 계정에 이 폴더에 대한 **모든 권한** 이 있어야 합니다.  

         설치 프로그램을 사용하여 가용성 그룹에서 데이터베이스 인스턴스를 지정하는 동안에만 보조 복제본 서버에 이 파일 경로가 필요합니다.  설치 프로그램이 가용성 그룹의 사이트 데이터베이스를 사용하기 위한 변경을 완료한 후 보조 데이터베이스에서 사용되지 않는 경로를 삭제할 수 있습니다.  

         예를 들어 다음 시나리오를 고려할 수 있습니다.  

        -   3개의 SQL Server를 사용하는 가용성 그룹을 만듭니다.  

        -   주 복제본 서버는 SQL Server 2014의 새로운 설치입니다.  기본적으로 데이터베이스 .MDF 및 .LDF 파일은 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA에 저장됩니다.  

        -   보조 복제본 서버 둘 다를 이전 버전에서 SQL Server 2014로 업그레이드하고 데이터베이스 파일을 저장하는 원래 파일 경로인 C:\Program Files\Microsoft SQL Server\MSSQL10.MSSQLSERVER\MSSQL\DATA를 유지합니다.  

        -   이 가용성 그룹으로 사이트 데이터베이스를 이동하기 전에 각 보조 복제본 서버에서 보조 복제본이 다음 파일 위치를 사용하지 않는 경우에도 다음 파일 경로를 만들어야 합니다. C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA(주 복제본에서 사용되는 경로와 동일함)  

        -   그런 후 각 보조 복제본의 SQL Server 서비스 계정에 해당 서버에서 새로 생성된 파일 위치에 대한 모든 권한을 부여합니다.  

        -   이제 Configuration Manager 설치 프로그램을 성공적으로 실행하여 사이트에 가용성 그룹의 사이트 데이터베이스를 사용하도록 지시할 수 있습니다.  

-   **설치 프로그램이 실행되어 사이트 데이터베이스에 가용성 그룹을 사용하도록 지시하면 다음과 유사한 오류가 ConfigMgrSetup.log에 로깅될 수 있음:**  

    -   오류: SQL Server 오류: [25000][3906][Microsoft][SQL Server Native Client 11.0] [SQL Server] 데이터베이스 "CM_AAA"은(는) 읽기 전용이므로 업데이트할 수 없습니다.   Configuration Manager Setup 1/21/2016 4:54:59 PM  7344 (0x1CB0)  

     설치 프로그램이 가용성 그룹의 보조 복제본에서 데이터베이스 역할을 처리하려고 할 때 이러한 오류가 로깅됩니다. 이러한 오류는 무시해도 됩니다.
- **추가 가용성 그룹을 호스트하는 SQL Server:**

  버전 1610을 설치하기 전에 가용성 그룹을 사용한 다음 Configuration Manager 설치 프로그램을 실행하거나 Configuration Manager 업데이트를 설치하는 경우 Configuration Manager 가용성 그룹을 호스트하는 SQL Server의 각 추가 가용성 그룹에 있는 각 복제본에 다음과 같은 구성이 있어야 합니다.
    - **수동 장애 조치**
    - **모든 읽기 전용 연결을 허용**


##  <a name="bkmk_BnR"></a> SQL Server AlwaysOn 가용성 그룹을 사용하는 경우 백업 및 복구의 변경 내용  
 **백업:**  

 사이트 데이터베이스가 가용성 그룹에서 실행될 때 기본 제공된 **백업 사이트** 서버 유지 관리 작업을 계속 실행하여 공통 Configuration Manager 설정 및 파일을 백업해야 하지만 해당 백업에서 생성된 .MDF 또는 .LDF 파일을 사용하지 않도록 계획해야 합니다. 대신, SQL Server를 사용하여 사이트 데이터베이스에 대한 직접 백업을 만들도록 계획합니다.  

 또한 데이터베이스의 복구 모델이 전체로 설정되어 있으므로 사이트 데이터베이스 트랜잭션 로그의 크기를 모니터링하고 유지 관리를 계획해야 합니다.  전체 복구 모델에서 데이터베이스 또는 트랜잭션 로그의 전체 백업이 생성될 때까지 트랜잭션은 확정되지 않습니다. 전체 복구 모델은 가용성 그룹에서 사이트 데이터베이스를 사용하기 위한 요구 사항이며 Configuration Manager에 사용할 그룹을 구성할 때 설정됩니다. SQL Server 백업 및 복원 방법에 대한 자세한 내용은 [SQL Server 문서의 SQL Server 데이터베이스의 백업 및 복원](https://msdn.microsoft.com/library/ms187048\(v=sql.120\).aspx) 을 참조하세요.  

 **복구:**  

 사이트 복구 중, 가용성 그룹의 한 노드가 계속 작동하는 한 사이트 복구 옵션인 **데이터베이스 복구 건너뛰기(사이트 데이터베이스가 영향을 받지 않는 경우 이 옵션 사용)**를 사용할 수 있습니다.  

 그러나 가용성 그룹의 모든 노드가 손실된 경우 사이트를 복구하려면 먼저 가용성 그룹을 다시 만들어야 합니다(System Center Configuration Manager에서 가용성 노드를 다시 생성하거나 복원할 수 없음).  백업을 복원하고 다시 구성하여 그룹을 다시 만든 후 사이트 복구 옵션인 **데이터베이스 복구 건너뛰기(사이트 데이터베이스가 영향을 받지 않는 경우 이 옵션 사용)**를 사용할 수 있습니다.  

 백업 및 복구에 대한 자세한 내용은 [System Center Configuration Manager 백업 및 복구](../../../../protect/understand/backup-and-recovery.md)를 참조하세요.  

##  <a name="bkmk_create"></a> Configuration Manager에서 사용하도록 가용성 그룹 구성  
 다음 절차를 시작하기 전에 이 구성을 완료하는 데 필요한 SQL Server 절차와 Configuration Manager에서 사용하도록 구성하는 가용성 그룹에 적용되는 다음 세부 사항을 잘 알고 있어야 합니다.  

 **System Center Configuration Manager에서 사용하는 AlwaysOn 가용성 그룹에 대한 요구 사항:**  

-  *버전*: 가용성 그룹의 각 노드(또는 복제본)는 System Center Configuration Manager에서 지원하는 SQL Server 버전을 실행해야 합니다. SQL Server에서 지원될 경우 가용성 그룹의 노드별로 다른 SQL Server 버전을 실행할 수 있습니다.   

- *Edition*: SQL Server의 Enterprise Edition을 사용해야 합니다.  SQL Server 2016 Standard Edition은 Configuration Manager에서 지원되지 않는 기본 가용성 그룹을 소개합니다.


-   가용성 그룹에는 주 복제본이 하나 있어야 하며 동기 보조 복제본이 2개까지 포함될 수 있습니다.  

-  가용성 그룹에 데이터베이스를 추가한 후에는 주 복제본을 보조 복제본으로 장애 조치하고(새 주 복제본으로 설정됨) 다음과 같이 데이터베이스를 구성해야 합니다.
    - 신뢰성을 사용하도록 설정: True와 같음
    - Service Broker을 사용하도록 설정: True와 같음
    - dbowner 설정: SA와 같음

    다음 스크립트를 실행하여 이러한 설정을 구성할 수 있습니다. 여기서 cm_ABC는 사이트 데이터베이스의 이름입니다.  

    >     USE master  
    >     ALTER DATABASE cm_ABC SET NEW_BROKER   
    >     ALTER DATABASE cm_ABC SET ENABLE_BROKER  
    >     ALTER DATABASE cm_ABC SET TRUSTWORTHY ON;  
    >     USE cm_ABC  
    >     EXEC sp_changedbowner 'sa'  
    >     Exec sp_configure 'max text repl size (B)', 2147483647 reconfigure



-   가용성 그룹에는 **가용성 그룹 수신기**가 하나 이상 있어야 합니다.  이 수신기의 가상 이름은 가용성 그룹의 사이트 데이터베이스를 사용하도록 Configuration Manager를 구성할 때 사용됩니다. 가용성 그룹에 수신기가 여러 개 포함될 수 있지만 Configuration Manager에서는 수신기를 하나만 사용할 수 있습니다.  

-   각 기본 및 보조 복제본은 다음과 같아야 합니다.  
    - **모든 읽기 전용 연결을 허용**하도록 설정해야 합니다.
    - **기본 인스턴스**를 사용해야 합니다.
    - **수동 장애 조치**가 설정되어야 합니다.  

        > [!TIP]  
        >  System Center Configuration Manager에서는 자동 장애 조치로 설정된 가용성 그룹 복제본을 사용할 수 있습니다. 하지만 설치 프로그램을 실행하여 가용성 그룹에서 사이트 데이터베이스의 사용을 지정할 때 그리고 Configuration Manager로의 업데이트(사이트 데이터베이스에 적용되는 업데이트가 아님)를 설치할 때 수동 장애 조치를 설정해야 합니다.  

  **가용성 그룹에 대한 제한 사항**
   - SQL Server 2016 Standard Edition에서 소개된 기본 가용성 그룹은 지원되지 않습니다. 이는 Configuration Manager에서 사용하기 위한 요구 사항인 보조 복제본에 대한 읽기 액세스를 기본 가용성 그룹이 지원하지 않기 때문입니다. 자세한 내용은 [기본 가용성 그룹(Always On 가용성 그룹)](https://msdn.microsoft.com/en-us/library/mt614935.aspx)을 참조하세요.

   - 가용성 그룹은 사이트 데이터베이스에 대해서만 지원됩니다 소프트웨어 업데이트 데이터베이스 또는 보고 데이터베이스에 대해서는 지원되지 않습니다.   
   - 가용성 그룹을 사용하면 가용성 그룹 수신기가 아니라 현재 주 복제본을 사용하도록 보고 지점을 수동으로 구성해야 합니다. 주 복제본이 다른 복제본으로 장애 조치되는 경우에는 새 주 복제본을 사용할 수 있도록 보고 지점을 다시 구성해야 합니다.  
   - 버전 1606과 같이 업데이트를 설치하기 전에 가용성 그룹이 수동 장애 조치로 설정되어 있는지 확인합니다. 사이트를 업데이트 한 후에는 장애 조치를 자동으로 복원할 수 있습니다.



 **가용성 그룹을 구성하고 사용하기 위해 필요한 권한:**  

-   사이트 서버의 컴퓨터 계정은 가용성 그룹의 구성원인 각 컴퓨터에서 **로컬 관리자** 그룹의 구성원이어야 합니다.  

#### <a name="to-configure-an-availability-group-to-host-a-site-database"></a>사이트 데이터베이스를 호스트하는 가용성 그룹을 구성하려면  

1.  다음 명령을 사용하여 Configuration Manager 사이트를 중지합니다.  
     **Preinst.exe /stopsite**  

     Preinst.exe를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)를 참조하세요.  

2.  사이트 데이터베이스의 백업 모델을 **단순** 에서 **전체**로 변경합니다.  

     SQL Server 문서에서 [데이터베이스의 복구 모델 보기 또는 변경](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) 을 참조하세요. 가용성 그룹은 전체만 지원합니다.  

3.  그룹의 주 복제본을 호스트하는 서버에서 **새 가용성 그룹 마법사** 를 사용하여 가용성 그룹을 만듭니다. 마법사에서:  

    -   **데이터베이스 선택** 페이지에서 Configuration Manager 사이트에 적합한 데이터베이스를 선택합니다.  

    -   **복제본 지정** 페이지에서 다음을 구성합니다.  

        -   **복제본**: 보조 복제본을 호스트하는 서버를 지정합니다.  

        -   **수신기**: **수신기 DNS 이름**을 정식 DNS 이름(예: **&lt;수신기_서버>.fabrikam.com**)으로 지정합니다. 이 이름은 가용성 그룹에서 데이터베이스를 사용하도록 Configuration Manager를 구성할 때 사용됩니다.

    -   **초기 데이터 동기화 선택** 페이지에서 **전체**를 선택합니다. 가용성 그룹을 생성하면 주 데이터베이스 및 트랜잭션 로그가 백업되고 보조 복제본을 호스트하는 각 서버에서 복원됩니다. 이 단계를 사용하지 않는 경우 보조 복제본을 호스트하는 각 서버로 사이트 데이터베이스의 복사본을 복원하고 그룹에 해당 데이터베이스를 수동으로 가입해야 합니다.  

    자세한 내용은 SQL Server 문서의 [가용성 그룹 마법사 사용](https://msdn.microsoft.com/library/hh403415\(v=sql.120\).aspx) 을 참조하세요.  

4.  가용성 그룹이 구성된 후 주 복제본에서 **TRUSTWORTHY** 속성을 사용하여 사이트 데이터베이스를 구성한 후 **CLR 통합을 사용**합니다. 이들을 구성하는 방법에 대해서는 SQL Server 문서의 [TRUSTWORTHY 데이터베이스 속성](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) 및  [CLR 통합 사용](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx) 을 참조하세요.  

5.  다음 작업을 수행하여 가용성 그룹에서 각 보조 복제본을 구성합니다.  

    1.  현재 주 복제본을 보조 복제본으로 수동으로 장애 조치합니다. SQL Server 문서에서 [가용성 그룹의 계획된 수동 장애 조치(Failover) 수행](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) 을 참조하세요.  

    2.  새로운 주 복제본의 데이터베이스를 **TRUSTWORTHY** 속성을 사용하여 사이트 데이터베이스를 구성한 후 **CLR 통합을 사용**합니다.  

6.  모든 복제본이 주 복제본으로 승격되고 데이터베이스가 구성되면 가용성 그룹을 Configuration Manager에서 사용할 준비가 된 것입니다.  





##  <a name="bkmk_direct"></a> 가용성 그룹으로 사이트 데이터베이스 이동  
 이전에 설치한 사이트의 사이트 데이터베이스를 가용성 그룹으로 이동할 수 있습니다. 먼저 가용성 그룹을 만든 다음 가용성 그룹에서 작업에 대한 데이터베이스를 구성해야 합니다.  

 이 절차를 완료하려면 Configuration Manager 설치 프로그램을 실행하는 사용자 계정은 가용성 그룹의 구성원인 각 컴퓨터에서 **로컬 관리자** 그룹의 구성원이어야 합니다.  

#### <a name="to-move-a-site-database-to-an-availability-group"></a>가용성 그룹으로 사이트 데이터베이스를 이동하려면  

1.  **&lt;Configuration Manager 사이트 설치 폴더\>\BIN\X64\setup.exe**에서 **Configuration Manager 설치 프로그램**을 실행합니다.  

2.  **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.  

3.  **SQL Server 구성 수정** 옵션을 선택한 후 **다음**을 클릭합니다.  

4.  사이트 데이터베이스에 대해 다음을 다시 구성합니다.  

    -   **SQL Server 이름** : 가용성 그룹을 만들 때 구성한 가용성 그룹 수신기의 가상 이름을 입력합니다. 가상 이름은 **&lt;endpointServer\>.fabrikam.com**과 같은 전체 DNS 이름이어야 합니다.  

    -   **인스턴스:** 가용성 그룹의 가용성 그룹 수신기에 대한 기본 인스턴스를 지정하려면 이 값을 비워두어야 합니다.  현재 사이트 데이터베이스가 명명된 인스턴스에 설치된 경우 명명된 인스턴스가 나열되므로 이를 제거해야 합니다.  

    -   **데이터베이스:** 표시되는 이름을 그대로 둡니다. 이 이름은 현재 사이트 데이터베이스의 이름입니다.  

5.  새 데이터베이스 위치에 대한 정보를 제공한 후 일반적인 프로세스와 구성을 사용하여 설치 프로그램을 완료합니다.  

##  <a name="bkmk_change"></a> 현재 가용성 그룹의 구성원 추가 또는 제거  
 Configuration Manager가 가용성 그룹에 호스트되는 사이트 데이터베이스를 사용한 후 복제본 구성원을 제거하거나 복제 구성원을 더 추가할 수 있습니다(주 노드 하나와 보조 노드 두 개를 초과하지 않음).  

#### <a name="to-add-a-new-replica-member"></a>새 복제본 구성원을 추가하려면  

1.  보조 복제본으로 새 서버를 가용성 그룹에 추가합니다. SQL Server 문서 라이브러리에서  [가용성 그룹에 보조 복제본 추가(SQL Server)](https://msdn.microsoft.com/library/hh213247\(v=sql.120\).aspx)를 참조하세요.  

2.  **Preinst.exe /stopsite**를 실행하여 Configuration Manager 사이트를 중지합니다. [System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)를 참조하세요.  

3.  각 보조 복제본을 구성합니다. 가용성 그룹에 있는 각 보조 복제본에 대해 다음 작업을 수행합니다.  

    1.  주 복제본을 새 보조 복제본으로 수동으로 장애 조치합니다. SQL Server 문서에서 [가용성 그룹의 계획된 수동 장애 조치(Failover) 수행](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) 을 참조하세요.  

    2.  새 서버의 데이터베이스를 Trustworthy로 구성하고 CLR 통합을 사용하도록 설정합니다. SQL Server 문서의 [TRUSTWORTHY 데이터베이스 속성](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) 및  [CLR 통합 사용](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx)을 참조하세요.  

4.  사이트 구성 요소 관리자(**sitecomp**) 및 **SMS_Executive** 서비스를 시작하여 사이트를 다시 시작합니다.  

#### <a name="to-remove-a-replica-member-from-the-availability-group"></a>가용성 그룹에서 복제본 구성원을 제거하려면  

-   SQL Server 문서의 [가용성 그룹에서 보조 복제본 제거](https://msdn.microsoft.com/library/hh213149\(v=sql.120\).aspx) 에 나와 있는 정보를 사용합니다.  

##  <a name="bkmk_remove"></a> 가용성 그룹에서 단일 SQL Server 인스턴스로 사이트 데이터베이스 다시 이동  
 더 이상 사이트 데이터베이스를 가용성 그룹에 호스트하지 않으려는 경우 다음 절차를 따르세요.  

#### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>사이트 데이터베이스를 가용성 그룹에서 단일 SQL Server 인스턴스를 다시 가용성 그룹에서 단일 SQL Server 인스턴스로 사이트 데이터베이스를 다시 이동하려면  

1.  다음 명령을 사용하여 Configuration Manager 사이트를 중지합니다.  
     **Preinst.exe /stopsite**  자세한 내용은 [System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)를 참조하세요.  

2.  SQL Server를 사용하여 주 복제본에서 사이트 데이터베이스의 전체 백업을 만듭니다. 이 단계를 완료하는 방법에 대해서는 [SQL Server 문서의 전체 데이터베이스 백업 만들기](https://msdn.microsoft.com/library/ms187510\(v=sql.120\).aspx) 를 참조하세요.  

3.  가용성 그룹의 주 복제본을 호스트하는 서버에서 이제 사이트 데이터베이스의 단일 인스턴스를 호스트할 경우 이 단계를 건너뛸 수 있습니다.  

    -   SQL Server를 사용하여 사이트 데이터베이스를 호스트하는 서버로 사이트 데이터베이스 백업을 복원합니다.  SQL Server 문서의 [데이터베이스 백업 복원(SQL Server Management Studio)](https://msdn.microsoft.com/library/ms177429\(v=sql.120\).aspx) 을 참조하세요.  

4.  복원된 사이트 데이터베이스에서 사이트 데이터베이스에 대한 백업 모델을 **전체** 에서 **단순**으로 변경합니다.  SQL Server 문서에서 [데이터베이스의 복구 모델 보기 또는 변경](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) 을 참조하세요.  

5.  **&lt;Configuration Manager 사이트 설치 폴더\>\BIN\X64\setup.exe**에서 **Configuration Manager 설치 프로그램**을 실행합니다.  

6.  **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.  

7.  **SQL Server 구성 수정** 옵션을 선택한 후 **다음**을 클릭합니다.  

8.  사이트 데이터베이스에 대해 다음을 다시 구성합니다.  

    -   **SQL Server 이름:** 이제 사이트 데이터베이스를 호스트하는 서버의 이름을 입력합니다.  

    -   **인스턴스:** 사이트 데이터베이스를 호스트하는 명명된 인스턴스를 지정하거나 데이터베이스가 기본 인스턴스에 있으면 이 필드를 공백으로 둡니다.  

    -   **데이터베이스:** 표시되는 이름을 그대로 둡니다. 이 이름은 현재 사이트 데이터베이스의 이름입니다.  

9. 새 데이터베이스 위치에 대한 정보를 제공한 후 일반적인 프로세스와 구성을 사용하여 설치 프로그램을 완료합니다. 설치가 완료되면 사이트가 다시 시작되고 새 데이터베이스 위치를 사용합니다.  

10. 가용성 그룹의 구성원인 서버를 정리하려면 SQL Server 문서에 있는 [가용성 그룹 제거](https://msdn.microsoft.com/library/ff878113\(v=sql.120\).aspx) 항목의 지침을 따릅니다.

