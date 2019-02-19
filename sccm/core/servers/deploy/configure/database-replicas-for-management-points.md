---
title: 관리 지점 데이터베이스 복제본
titleSuffix: Configuration Manager
description: 데이터베이스 복제본을 사용하면 관리 지점에 의한 사이트 데이터베이스 서버의 CPU 부하를 줄일 수 있습니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b06f781b-ab25-4d9a-b128-02cbd7cbcffe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7ce8cff2be91950ee7e43cd96f03ab41990170c9
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56139622"
---
# <a name="database-replicas-for-management-points-for-system-center-configuration-manager"></a>System Center Configuration Manager의 관리 지점용 데이터베이스 복제본

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 기본 사이트는 데이터베이스 복제본을 사용하여 클라이언트의 요청을 처리하는 관리 지점이 사이트 데이터베이스 서버에 적용하는 CPU 부하를 줄일 수 있습니다.  

-   데이터베이스 복제본을 사용하는 관리 지점은 사이트 데이터베이스 서버가 아닌 데이터베이스 복제본을 호스트하는 SQL Server 컴퓨터에서 데이터를 요청합니다.  

-   따라서 클라이언트와 관련된 빈번한 처리 작업을 오프로드함으로써 사이트 데이터베이스 서버의 CPU 처리 요구 사항을 줄일 수 있습니다.  클라이언트에 대한 빈번한 처리 작업의 예로는 클라이언트 정책을 자주 요청하는 다수의 클라이언트가 있는 사이트를 들 수 있습니다.  


##  <a name="bkmk_Prepare"></a> 데이터베이스 복제본 사용 준비  
**관리 지점용 데이터베이스 복제본 정보:**  

-   복제본은 별도의 SQL Server 인스턴스로 복제되는 사이트 데이터베이스의 부분 복사본입니다.  

    -   기본 사이트는 사이트의 각 관리 지점에 대해 전용 데이터베이스 복제본을 지원합니다. 보조 사이트는 데이터베이스 복제본을 지원하지 않습니다.  

    -   같은 사이트에서 둘 이상의 관리 지점이 데이터베이스 복제본 하나를 사용할 수 있습니다.  

    -   각 관리 지점이 개별 SQL Server 인스턴스에서 실행된다면 SQL Server는 각기 다른 관리 지점에 사용할 여러 데이터베이스 복제본을 호스트할 수 있습니다.  

-   복제본은 이러한 용도로 사이트 데이터베이스 서버가 게시하는 데이터에서 고정된 일정으로 사이트 데이터베이스 복사본을 동기화합니다.  

-   관리 지점을 설치할 때 복제본을 사용하도록 구성할 수도 있고, 이전에 설치한 관리 지점이 데이터베이스 복제본을 사용하도록 나중에 다시 구성할 수도 있습니다.  

-   사이트 데이터베이스 서버와 각 데이터베이스 복제본 서버를 정기적으로 모니터링하여 이러한 서버 간에 복제가 이루어지는지, 그리고 데이터베이스 복제본 서버의 성능이 필요한 사이트 및 클라이언트 성능을 충분히 제공할 수 있는지를 확인해야 합니다.  

**데이터베이스 복제본의 필수 구성 요소:**  

-   **SQL Server 요구 사항:**  

    -   데이터베이스 복제본을 호스트하는 SQL Server는 사이트 데이터베이스 서버와 같은 요구 사항을 충족해야 합니다. 그러나 복제본 서버는 지원되는 SQL Server 서버 및 에디션을 실행할 경우 사이트 데이터베이스 서버와 동일한 SQL Server 버전이나 에디션을 실행하지 않아도 됩니다. 자세한 내용은 [System Center Configuration Manager에 대한 SQL Server 버전 지원](../../../../core/plan-design/configs/support-for-sql-server-versions.md)을 참조하세요.  

    -   복제본 데이터베이스를 호스트하는 컴퓨터의 SQL Server 서비스는 **시스템** 계정으로 실행해야 합니다.  

    -   사이트 데이터베이스를 호스트하는 SQL Server 및 데이터베이스 복제본을 호스트하는 SQL Server에는 모두 **SQL Server 복제** 를 설치해야 합니다.  

    -   사이트 데이터베이스는 데이터베이스 복제본을 **게시** 해야 하고, 각 원격 데이터베이스 복제본 서버는 게시된 데이터베이스를 **구독** 해야 합니다.  

    -   사이트 데이터베이스를 호스트하는 SQL Server 및 데이터베이스 복제본을 호스트하는 SQL Server는 모두 **최대 텍스트 복제 크기** 2GB를 지원하도록 구성해야 합니다. SQL Server 2012에 대해 이를 구성하는 방법의 예는 [최대 텍스트 복제 크기 서버 구성 옵션 구성](http://go.microsoft.com/fwlink/p/?LinkId=273960)을 참조하세요.  

-   **자체 서명된 인증서**: 데이터베이스 복제본을 구성하려면 데이터베이스 복제본 서버에서 자체 서명된 인증서를 만들고 해당 데이터베이스 복제본 서버를 사용할 각 관리 지점에서 이 인증서를 사용할 수 있도록 해야 합니다.  

    -   데이터베이스 복제본 서버에 설치되는 관리 지점에서는 자동으로 인증서를 사용할 수 있습니다.  

    -   이 인증서를 원격 관리 지점에 제공하려면 인증서를 내보낸 다음 원격 관리 지점의 **신뢰할 수 있는 사용자** 인증서 저장소에 추가해야 합니다.  

-   **클라이언트 알림:** 관리 지점에 대한 데이터베이스 복제본으로 클라이언트 알림을 지원하려면 **SQL Server Service Broker**에 대한 사이트 데이터베이스 서버와 데이터베이스 복제 서버 간의 통신을 구성해야 합니다. 이렇게 하려면 다음을 수행해야 합니다.  

    -   다른 데이터베이스에 대한 정보로 각 데이터베이스 구성  

    -   안전한 통신을 위해 두 데이터베이스 간에 인증서 교환  

**데이터베이스 복제본 사용 시의 제한 사항:**  

-   데이터베이스 복제본을 게시하도록 사이트를 구성할 때는 일반적인 지침을 따르는 대신 다음 절차를 수행해야 합니다.  

    -   [데이터베이스 복제본을 게시하는 사이트 서버 제거](#BKMK_DBReplicaOps_Uninstall)  

    -   [데이터베이스 복제본을 게시하는 사이트 서버 데이터베이스 이동](#BKMK_DBReplicaOps_Move)  

-   **System Center Configuration Manager로 업그레이드**: 사이트를 System Center 2012 Configuration Manager에서 System Center Configuration Manager 현재 분기로 업그레이드하거나 Configuration Manager 현재 분기를 최신 릴리스로 업데이트하기 전에 관리 지점의 데이터베이스 복제본을 사용하지 않도록 설정해야 합니다.  사이트를 업그레이드한 후 관리 지점에 대해 데이터베이스 복제본을 다시 구성할 수 있습니다.  

-   **단일 SQL Server의 여러 복제본:**  관리 지점에 대해 여러 데이터베이스 복제본을 호스트하도록 데이터베이스 복제본 서버를 구성하는 경우(각 복제본은 개별 인스턴스에 있어야 함), 해당 서버에서 이전에 구성한 데이터베이스 복제본에서 사용되는 자체 서명된 인증서를 덮어쓰지 않도록 하려면 다음 섹션의 4단계에서 수정된 구성 스크립트를 사용해야 합니다.  

##  <a name="BKMK_DBReplica_Config"></a> 데이터베이스 복제본 구성  
데이터베이스 복제본을 사용하고 구성하려면 다음 단계를 수행해야 합니다.  

-   [1단계 - 데이터베이스 복제본을 게시하도록 사이트 데이터베이스 서버 구성](#BKMK_DBReplica_ConfigSiteDB)  

-   [2단계 - 데이터베이스 복제본 서버 구성](#BKMK_DBReplica_ConfigSrv)  

-   [3단계 - 관리 지점에서 데이터베이스 복제본을 사용하도록 구성](#BKMK_DBReplica_ConfigMP)  

-   [4단계 - 데이터베이스 복제본 서버용으로 자체 서명된 인증서 구성](#BKMK_DBReplica_Cert)  

-   [5단계 - 데이터베이스 복제본 서버에 대해 SQL Server Service Broker 구성](#BKMK_DBreplica_SSB)  

###  <a name="BKMK_DBReplica_ConfigSiteDB"></a> 1단계 - 데이터베이스 복제본을 게시하도록 사이트 데이터베이스 서버 구성  
 다음 절차는 Windows Server 2008 R2 컴퓨터에서 데이터베이스 복제본을 게시하도록 사이트 데이터베이스 서버를 구성하는 방법의 예입니다. 다른 운영 체제 버전을 사용하는 경우 해당 운영 체제 문서를 참조하여 필요한 대로 이 절차의 단계를 조정합니다.  

##### <a name="to-configure-the-site-database-server"></a>사이트 데이터베이스 서버를 구성하려면  

1.  사이트 데이터베이스 서버에서 SQL Server 에이전트가 자동으로 시작되도록 설정합니다.  

2.  사이트 데이터베이스 서버에서 **ConfigMgr_MPReplicaAccess**라는 이름의 로컬 사용자 그룹을 만듭니다. 데이터베이스 복제본 서버가 게시된 데이터베이스 복제본과 동기화될 수 있도록 이 사이트에서 사용하는 각 데이터베이스 복제본 서버의 컴퓨터 계정을 이 그룹에 추가해야 합니다.  

3.  사이트 데이터베이스 서버에서 **ConfigMgr_MPReplica**라는 이름의 파일 공유를 구성합니다.  

4.  **ConfigMgr_MPReplica** 공유에 다음 사용 권한을 추가합니다.  

    > [!NOTE]  
    >  SQL Server 에이전트에서 로컬 시스템 계정이 아닌 계정을 사용하는 경우 다음 목록에서 SYSTEM을 해당 계정 이름으로 대체합니다.  

    -   **공유 사용 권한**:  

        -   SYSTEM: **쓰기**  

        -   ConfigMgr_MPReplicaAccess: **읽기**  

    -   **NTFS 사용 권한**:  

        -   SYSTEM: **모든 권한**  

        -   ConfigMgr_MPReplicaAccess: **읽기**, **읽기 및 실행**, **폴더 콘텐츠 나열**  

5.  **SQL Server Management Studio** 를 사용하여 사이트 데이터베이스에 연결하고 **spCreateMPReplicaPublication**저장 프로시저를 쿼리로 실행합니다.  

저장 프로시저가 완료되면 사이트 데이터베이스 서버가 데이터베이스 복제본을 게시하도록 구성됩니다.  

###  <a name="BKMK_DBReplica_ConfigSrv"></a> 2단계 - 데이터베이스 복제본 서버 구성  
데이터베이스 복제본 서버는 SQL Server를 실행하고 관리 지점이 사용할 사이트 데이터베이스의 복제본을 호스팅하는 컴퓨터입니다. 데이터베이스 복제본 서버는 고정된 일정으로 사이트 데이터베이스 서버에서 게시되는 데이터베이스 복제본과 데이터베이스 복제본을 동기화합니다.  

데이터베이스 복제본 서버는 사이트 데이터베이스 서버와 동일한 요구 사항을 충족해야 합니다. 그러나 데이터베이스 복제본 서버는 사이트 데이터베이스 서버가 사용하는 것과 다른 에디션 또는 버전의 SQL Server를 실행할 수 있습니다. 지원되는 SQL Server의 버전에 대한 자세한 내용은 [System Center Configuration Manager에 대한 SQL Server 버전 지원](../../../../core/plan-design/configs/support-for-sql-server-versions.md)을 참조하세요.  

> [!IMPORTANT]  
>  복제본 데이터베이스를 호스팅하는 컴퓨터의 SQL Server Service는 System 계정으로 실행해야 합니다.  

다음 절차는 Windows Server 2008 R2 컴퓨터에서 데이터베이스 복제본 서버를 구성하는 방법의 예입니다. 다른 운영 체제 버전을 사용하는 경우 해당 운영 체제 문서를 참조하여 필요한 대로 이 절차의 단계를 조정합니다.  

##### <a name="to-configure-the-database-replica-server"></a>데이터베이스 복제본 서버를 구성하려면  

1. 데이터베이스 복제본 서버에서 SQL Server 에이전트가 자동으로 시작되도록 설정합니다.  

2. 데이터베이스 복제본 서버에서 **SQL Server Management Studio** 를 사용하여 로컬 서버에 연결하고 **복제** 폴더를 찾아 로컬 구독을 클릭하고 **새 구독** 을 선택하여 **새 구독 마법사**를 시작합니다.  

   1. **게시** 페이지의 **게시자** 목록 상자에서 **SQL Server 게시자 찾기**를 선택하고 사이트 데이터베이스 서버의 이름을 입력한 후에 **연결**을 클릭합니다.  

   2. **ConfigMgr_MPReplica**를 선택한 후에 **다음**을 클릭합니다.  

   3. **배포 에이전트 위치** 페이지에서 **각 에이전트를 해당 구독자(끌어오기 구독)에서 실행**을 선택하고 **다음**을 클릭합니다.  

   4. **구독자** 페이지에서 다음 중 하나를 수행합니다.  

      -   데이터베이스 복제본 서버에서 데이터베이스 복제본을 위해 사용할 기존 데이터베이스를 선택하고 **확인**을 클릭합니다.  

      -   **새 데이터베이스** 를 선택하여 데이터베이스 복제본을 위한 새 데이터베이스를 만듭니다. **새 데이터베이스** 페이지에서 데이터베이스 이름을 지정한 후에 **확인**을 클릭합니다.  

   5. **다음** 을 클릭하여 계속합니다.  

   6. **배포 에이전트 보안** 페이지에서 대화 상자의 구독자 연결 열에 있는 속성 단추 **(....)** 를 클릭하고 연결에 대한 보안 설정을 구성합니다.  

      > [!TIP]  
      >  속성 단추 **(....)** 는 표시 상자의 네 번째 열에 있습니다.  

      **보안 설정:**  

      - 배포 에이전트 프로세스를 실행하는 계정(프로세스 계정)을 구성합니다.  

        -   SQL Server 에이전트가 로컬 시스템으로 실행되는 경우 **SQL Server 에이전트 서비스 계정으로 실행(최상의 권장 보안 방법은 아님)** 을 선택합니다.  

        -   SQL Server 에이전트가 다른 계정을 사용하여 실행되는 경우 **다음 Windows 계정으로 실행**을 선택하고 해당 계정을 구성합니다. Windows 계정 또는 SQL Server 계정을 지정할 수 있습니다.  

        > [!IMPORTANT]  
        >  배포 에이전트 권한을 실행하는 계정을 끌어오기 구독으로 게시자에 할당해야 합니다. 이러한 권한을 구성하는 방법에 대한 자세한 내용은 SQL Server TechNet 라이브러리에서 [배포 에이전트 보안](http://go.microsoft.com/fwlink/p/?LinkId=238463) 을 참조하세요.  

      - **배포자에 연결**에 **프로세스 계정 가장**을 선택합니다.  

      - **구독자에 연결**에 **프로세스 계정 가장**을 선택합니다.  

        연결 보안 설정을 구성한 후에는 **확인** 을 클릭하여 저장하고 **다음**을 클릭합니다.  

   7. **동기화 일정** 페이지의 **에이전트 일정** 목록 상자에서 **일정 정의**를 선택하고 **새 작업 일정**을 구성합니다. 주기를 **일별**, 되풀이 간격을 **5분**으로 설정하고 기간을 **종료 날짜가 없습니다**로 설정합니다. **다음** 을 클릭하여 일정을 저장하고 다시 **다음** 을 클릭합니다.  

   8. **마법사 동작** 페이지에서 **구독 만들기**확인란을 선택하고 **다음**을 클릭합니다.  

   9. **마법사 완료** 페이지에서 **마침**을 클릭하고 **닫기** 를 클릭하여 마법사를 완료합니다.  

3. 새 구독 마법사를 완료하는 즉시 **SQL Server Management Studio** 를 사용하여 데이터베이스 복제본 서버 데이터베이스에 연결하고 다음 쿼리를 실행하여 TRUSTWORTHY 데이터베이스 속성을 사용하도록 설정합니다.  `ALTER DATABASE <MP Replica Database Name> SET TRUSTWORTHY ON;`  

4. 동기화 상태를 검토하여 구독이 성공적인지 확인합니다.  

   -   구독자 컴퓨터에서:  

       -   **SQL Server Management Studio**에서 데이터베이스 복제본 서버에 연결하고 **복제**를 확장합니다.  

       -   **로컬 구독**을 확장하고 사이트 데이터베이스 게시에 대한 구독을 마우스 오른쪽 단추로 클릭한 후에 **동기화 상태 보기**를 선택합니다.  

   -   게시자 컴퓨터에서:  

       -   **SQL Server Management Studio**에서 사이트 데이터베이스 컴퓨터에 연결하고 **복제** 폴더를 마우스 오른쪽 단추로 클릭한 후에 **복제 모니터 시작**을 선택합니다.  

5. 데이터베이스 복제본을 위한 CLR(공용 언어 런타임) 통합을 사용하도록 설정하려면 **SQL Server Management Studio** 를 사용하여 데이터베이스 복제본 서버의 데이터베이스 복제본에 연결하고 **exec sp_configure 'clr enabled', 1; RECONFIGURE WITH OVERRIDE**저장 프로시저를 쿼리로 실행합니다.  

6. 데이터베이스 복제본 서버를 사용하는 각 관리 지점에 대해 해당 관리 지점 컴퓨터 계정을 데이터베이스 복제본 서버의 로컬 **Administrators** 그룹에 추가합니다.  

   > [!TIP]  
   >  데이터베이스 복제본 서버에서 실행되는 관리 지점의 경우 이 단계가 필요 없습니다.  

   이제 데이터베이스 복제본을 관리 지점에 사용할 수 있습니다.  

###  <a name="BKMK_DBReplica_ConfigMP"></a> 3단계 - 관리 지점에서 데이터베이스 복제본을 사용하도록 구성  
 관리 지점 역할을 설치할 때 기본 사이트의 관리 지점이 데이터베이스 복제본을 사용하도록 구성하거나 기존 관리 지점이 데이터베이스 복제본을 사용하도록 구성할 수 있습니다.  

 관리 지점에서 데이터베이스 복제본을 사용하도록 구성하려면 다음 정보를 참고하세요.  

-   **새 관리 지점을 구성하려면:** 관리 지점을 설치하기 위해 사용하는 마법사의 **관리 지점 데이터베이스** 페이지에서 **데이터베이스 복제본 사용**을 선택하고 데이터베이스 복제본을 호스트하는 컴퓨터의 FQDN을 지정합니다. 그런 다음, 컴퓨터에 있는 데이터베이스 복제본의 데이터베이스 이름을 **ConfigMgr 사이트 데이터베이스 이름**에 지정합니다.  

-   **이전에 설치된 관리 지점을 구성하려면**: 관리 지점의 속성 페이지를 열고 **관리 지점 데이터베이스** 탭 및 **데이터베이스 복제본 사용**을 차례로 선택한 다음, 데이터베이스 복제본을 호스트하는 컴퓨터의 FQDN을 지정합니다. 그런 다음, 컴퓨터에 있는 데이터베이스 복제본의 데이터베이스 이름을 **ConfigMgr 사이트 데이터베이스 이름**에 지정합니다.  

-   **데이터베이스 복제본을 사용하는 각 관리 지점에 대해**관리 지점 서버의 컴퓨터 계정을 데이터베이스 복제본의 **db_datareader** 역할에 수동으로 추가해야 합니다.  

관리 지점에서 데이터베이스 복제본 서버를 사용하도록 구성하는 것 외에도 관리 지점에 대해 **IIS** 에서 **Windows 인증** 을 사용하도록 설정해야 합니다.  

1.  **IIS(인터넷 정보 서비스) 관리자**를 엽니다.  

2.  관리 지점에서 사용하는 웹 사이트를 선택하고 **인증**을 엽니다.  

3.  **Windows 인증** 을 **사용**으로 설정하고 **IIS(인터넷 정보 서비스) 관리자**를 닫습니다.  

###  <a name="BKMK_DBReplica_Cert"></a> 4단계 - 데이터베이스 복제본 서버용으로 자체 서명된 인증서 구성  
 데이터베이스 복제본 서버에 자체 서명된 인증서를 만들고 데이터베이스 복제본 서버를 사용하는 각 관리 지점에서 이 인증서를 사용할 수 있게 해야 합니다.  

 데이터베이스 복제본 서버에 설치되는 관리 지점에서는 자동으로 인증서를 사용할 수 있습니다. 그러나 이 인증서를 원격 관리 지점에서 사용할 수 있게 하려면 인증서를 내보낸 다음 원격 관리 지점의 신뢰할 수 있는 사용자 인증서 저장소에 추가해야 합니다.  

 다음 절차는 Windows Server 2008 R2 컴퓨터에서 데이터베이스 복제본 서버에 자체 서명된 인증서를 구성하는 방법의 예입니다. 다른 운영 체제 버전을 사용하는 경우 해당 운영 체제 문서를 참조하여 필요한 대로 이러한 절차의 단계를 조정합니다.  

##### <a name="to-configure-a-self-signed-certificate-for-the-database-replica-server"></a>데이터베이스 복제본 서버에 자체 서명된 인증서를 구성하려면  

1.  데이터베이스 복제본 서버에서 관리자 권한으로 PowerShell 명령 프롬프트를 열고 **set-executionpolicy UnRestricted**명령을 실행합니다.  

2.  다음 PowerShell 스크립트를 복사하여 **CreateMPReplicaCert.ps1**이라는 이름의 파일로 저장합니다. 이 파일의 복사본을 데이터베이스 복제본 서버의 시스템 파티션에 있는 루트 폴더에 넣습니다.  

    > [!IMPORTANT]  
    >  단일 SQL Server에서 둘 이상의 데이터베이스 복제본을 구성하는 경우에는 구성하는 각각의 후속 복제본에 대해 이 절차용으로 이 스크립트의 수정된 버전을 사용해야 합니다. [단일 SQL Server의 추가 데이터베이스 복제본용 보충 스크립트](#bkmk_supscript)항목을 참조하세요.  

    ```  
    # Script for creating a self-signed certificate for the local machine and configuring SQL Server to use it.  

    Param($SQLInstance)  

    $ConfigMgrCertFriendlyName = "ConfigMgr SQL Server Identification Certificate"  

    # Get local computer name  
    $computerName = "$env:computername"  

    # Get the sql server name  
    #$key="HKLM:\SOFTWARE\Microsoft\SMS\MP"  
    #$value="SQL Server Name"  
    #$sqlServerName= (Get-ItemProperty $key).$value  
    #$dbValue="Database Name"  
    #$sqlInstance_DB_Name= (Get-ItemProperty $key).$dbValue  

    $sqlServerName = [System.Net.Dns]::GetHostByName("localhost").HostName   
    $sqlInstanceName = "MSSQLSERVER"  
    $SQLServiceName = "MSSQLSERVER"  

    if ($SQLInstance -ne $Null)  
    {  
        $sqlInstanceName = $SQLInstance  
        $SQLServiceName = "MSSQL$" + $SQLInstance  
    }  

    # Delete existing cert if one exists  
    function Get-Certificate($storename, $storelocation)  
    {   
        $store=new-object System.Security.Cryptography.X509Certificates.X509Store($storename,$storelocation)   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Certificates   
    }   

    $cert = Get-Certificate "My" "LocalMachine" | ?{$_.FriendlyName -eq $ConfigMgrCertFriendlyName}   
    if($cert -is [Object])  
    {  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("My","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()  

        # Remove this cert from Trusted People too...  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("TrustedPeople","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()      
    }  

    # Create the new cert  
    $name = new-object -com "X509Enrollment.CX500DistinguishedName.1"  
    $name.Encode("CN=" + $sqlServerName, 0)  

    $key = new-object -com "X509Enrollment.CX509PrivateKey.1"  
    $key.ProviderName = "Microsoft RSA SChannel Cryptographic Provider"  
    $key.KeySpec = 1  
    $key.Length = 1024  
    $key.SecurityDescriptor = "D:PAI(A;;0xd01f01ff;;;SY)(A;;0xd01f01ff;;;BA)(A;;0x80120089;;;NS)"  
    $key.MachineContext = 1  
    $key.Create()  

    $serverauthoid = new-object -com "X509Enrollment.CObjectId.1"  
    $serverauthoid.InitializeFromValue("1.3.6.1.5.5.7.3.1")  
    $ekuoids = new-object -com "X509Enrollment.CObjectIds.1"  
    $ekuoids.add($serverauthoid)  
    $ekuext = new-object -com "X509Enrollment.CX509ExtensionEnhancedKeyUsage.1"  
    $ekuext.InitializeEncode($ekuoids)  

    $cert = new-object -com "X509Enrollment.CX509CertificateRequestCertificate.1"  
    $cert.InitializeFromPrivateKey(2, $key, "")  
    $cert.Subject = $name  
    $cert.Issuer = $cert.Subject  
    $cert.NotBefore = get-date  
    $cert.NotAfter = $cert.NotBefore.AddDays(3650)  
    $cert.X509Extensions.Add($ekuext)  
    $cert.Encode()  

    $enrollment = new-object -com "X509Enrollment.CX509Enrollment.1"  
    $enrollment.InitializeFromRequest($cert)  
    $enrollment.CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"  
    $certdata = $enrollment.CreateRequest(0x1)  
    $enrollment.InstallResponse(0x2, $certdata, 0x1, "")  

    # Add this cert to the trusted peoples store  
    [Byte[]]$bytes = [System.Convert]::FromBase64String($certdata)  

    $trustedPeople = new-object System.Security.Cryptography.X509certificates.X509Store "TrustedPeople", "LocalMachine"  
    $trustedPeople.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)  
    $trustedPeople.Add([Security.Cryptography.X509Certificates.X509Certificate2]$bytes)  
    $trustedPeople.Close()  

    # Get thumbprint from cert  
    $sha = new-object System.Security.Cryptography.SHA1CryptoServiceProvider  
    $certHash = $sha.ComputeHash($bytes)  
    $certHashCharArray = "";  
    $certThumbprint = "";  

    # Format the bytes into a hexadecimal string  
    foreach($byte in $certHash)  
    {  
        $temp = ($byte | % {"{0:x}" -f $_}) -join ""  
        $temp = ($temp | % {"{0,2}" -f $_})  
        $certHashCharArray = $certHashCharArray+ $temp;  
    }  
    $certHashCharArray = $certHashCharArray.Replace(' ', '0');  

    # SQL needs the thumbprint in lower case  
    foreach($char in $certHashCharArray)  
    {  
        [System.String]$myString = $char;  
        $certThumbprint = $certThumbprint + $myString.ToLower();  
    }  

    # Configure SQL to use this cert  
    $path = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\Instance Names\SQL"  
    $subKey = (Get-ItemProperty $path).$sqlInstanceName  
    $realPath = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\" + $subKey + "\MSSQLServer\SuperSocketNetLib"  
    $certKeyName = "Certificate"  
    Set-ItemProperty -path $realPath -name $certKeyName -Type string -Value $certThumbprint  

    # restart sql service  
    Restart-Service $SQLServiceName -Force  
    ```  

3.  데이터베이스 복제본 서버에서 해당 SQL Server 구성에 적용되는 명령을 실행합니다.  

    -   SQL Server의 기본 인스턴스: **CreateMPReplicaCert.ps1** 파일을 마우스 오른쪽 단추로 클릭하고 **PowerShell에서 실행**을 선택합니다. 스크립트가 실행되면 자체 서명된 인증서가 만들어지고 SQL Server에서 인증서를 사용하도록 구성됩니다.  

    -   SQL Server의 명명된 인스턴스: PowerShell을 사용하여 **%path%\CreateMPReplicaCert.ps1 xxxxxx** 명령을 실행합니다. 여기서 **xxxxxx**는 SQL Server 인스턴스의 이름입니다.  

    -   스크립트를 완료한 후 SQL Server 에이전트가 실행되고 있는지 확인합니다. 실행되고 있지 않으면 SQL Server 에이전트를 다시 시작합니다.  

##### <a name="to-configure-remote-management-points-to-use-the-self-signed-certificate-of-the-database-replica-server"></a>데이터베이스 복제 서버의 자체 서명된 인증서를 사용하도록 원격 관리 지점을 구성하려면  

1.  서버의 자체 서명된 인증서를 내보내려면 데이터베이스 복제 서버에서 다음 단계를 수행하세요.  

    1.  **시작**, **실행**을 차례로 클릭한 다음 **mmc.exe**를 입력합니다. 비어 있는 콘솔에서 **파일**을 클릭한 후 **스냅인 추가/제거**를 클릭합니다.  

    2.  **스냅인 추가/제거** 대화 상자의 **사용 가능한 스냅인** 목록에서 **인증서**를 선택하고 **추가**를 클릭합니다.  

    3.  **인증서 스냅인** 대화 상자에서 **컴퓨터 계정**을 선택한 후에 **다음**을 클릭합니다.  

    4.  **컴퓨터 선택** 대화 상자에서 **로컬 컴퓨터: (이 콘솔이 실행되고 있는 컴퓨터)** 가 선택되어 있는지 확인한 다음 **마침**을 클릭합니다.  

    5.  **스냅인 추가/제거** 대화 상자에서 **확인**을 클릭합니다.  

    6.  콘솔에서 **인증서(로컬 컴퓨터)** 를 확장하고 **개인**을 확장한 후 **인증서**를 선택합니다.  

    7.  이름이 **ConfigMgr SQL Server 식별 인증서**인 인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업**을 클릭한 후 **내보내기**를 선택합니다.  

    8.  기본 옵션을 사용하여 **인증서 내보내기 마법사** 를 완료하고 **.cer** 파일 이름 확장명으로 인증서를 저장합니다.  

2.  데이터베이스 복제 서버의 자체 서명된 인증서를 관리 지점의 신뢰할 수 있는 사용자 인증서 저장소에 추가하려면 관리 지점 컴퓨터에서 다음 단계를 수행하세요.  

    1.  앞의 1.a - 1.e 단계를 반복하여 관리 지점 컴퓨터의 MMC에서 **인증서** 스냅인을 구성합니다.  

    2.  콘솔에서 **인증서(로컬 컴퓨터)** 와 **신뢰할 수 있는 사용자**를 차례로 확장하고 **인증서**를 마우스 오른쪽 단추로 클릭한 다음 **모든 작업**을 선택하고 **가져오기** 를 선택하여 **인증서 가져오기 마법사**를 시작합니다.  

    3.  **가져올 파일** 페이지에서 1.h단계에서 저장한 인증서를 선택한 후 **다음**을 클릭합니다.  

    4.  **인증서 저장소** 페이지에서 **모든 인증서를 다음 저장소에 저장**을 선택하고 **인증서 저장소** 를 **신뢰할 수 있는 사용자**로 설정한 후 **다음**을 클릭합니다.  

    5.  **마침** 을 클릭하여 마법사를 닫고 관리 지점의 인증서 구성을 완료합니다.  

###  <a name="BKMK_DBreplica_SSB"></a> 5단계 - 데이터베이스 복제본 서버에 대해 SQL Server Service Broker 구성  
관리 지점의 데이터베이스 복제본으로 클라이언트 알림을 지원하려면 SQL Server Service Broker를 위해 사이트 데이터베이스 서버와 데이터베이스 복제 서버 간의 통신을 구성해야 합니다. 그러기 위해서는 다른 데이터베이스에 대한 정보를 사용하여 각 데이터베이스를 구성하고 보안 통신을 위해 두 데이터베이스 간에 인증서를 교환해야 합니다.  

> [!NOTE]  
>  다음 절차를 수행하기 전에 데이터베이스 복제 서버에서 사이트 데이터베이스 서버와의 초기 동기화를 성공적으로 완료해야 합니다.  

 다음 절차를 수행해도 SQL Server에서 사이트 데이터베이스 서버나 데이터베이스 복제 서버용으로 구성한 Service Broker 포트는 수정되지 않습니다. 대신 이 절차는 각 데이터베이스가 올바른 Service Broker 포트를 사용하여 다른 데이터베이스와 통신하도록 구성합니다.  

 사이트 데이터베이스 서버와 데이터베이스 복제 서버용으로 Service Broker를 구성하려면 다음 절차를 수행하세요.  

##### <a name="to-configure-the-service-broker-for-a-database-replica"></a>데이터베이스 복제용으로 Service Broker를 구성하려면  

1. **SQL Server Management Studio**를 사용하여 데이터베이스 복제 서버 데이터베이스에 연결한 다음, 다음 쿼리를 실행하여 데이터베이스 복제 서버에서 Service Broker를 사용하도록 설정합니다. **ALTER DATABASE &lt;복제 데이터베이스 이름\> SET ENABLE_BROKER, HONOR_BROKER_PRIORITY ON WITH ROLLBACK IMMEDIATE**  

2. 그 다음에는, 데이터베이스 복제 서버의 Service Broker에서 클라이언트 알림을 구성하고 Service Broker 인증서를 내보냅니다. 이렇게 하려면 한 번의 작업으로 Service Broker를 구성하고 인증서를 내보내는 SQL Server 저장 프로시저를 실행합니다. 저장 프로시저를 실행할 때 데이터베이스 복제 서버의 FQDN과 데이터베이스 복제 데이터베이스의 이름을 지정하고 인증서 파일을 내보낼 위치를 지정해야 합니다.  

    데이터베이스 복제 서버에서 필요한 세부 설정을 구성하려면 다음 쿼리를 실행하고 데이터베이스 복제 서버의 인증서를 내보냅니다. **EXEC sp_BgbConfigSSBForReplicaDB '&lt;복제 SQL Server FQDN\>', '&lt;복제 데이터베이스 이름\>', '&lt;인증서 백업 파일 경로\>'**  

   > [!NOTE]  
   >  데이터베이스 복제 서버가 SQL Server의 기본 인스턴스에 있지 않으면 이 단계에서 복제 데이터베이스 이름 외에 인스턴스 이름도 지정해야 합니다. 이렇게 하려면 **&lt;복제본 데이터베이스 이름\>** 을 **&lt;인스턴스 이름\\복제본 데이터베이스 이름\>** 으로 바꿉니다.  

    데이터베이스 복제 서버에서 인증서를 내보낸 후 인증서 사본을 기본 사이트 데이터베이스 서버에 저장합니다.  

3. **SQL Server Management Studio** 를 사용하여 기본 사이트 데이터베이스에 연결합니다. 기본 사이트 데이터베이스에 연결한 후 인증서를 가져오는 쿼리를 실행하고 데이터베이스 복제 서버에서 사용 중인 Service Broker 포트, 데이터베이스 복제 서버의 FQDN 및 데이터베이스 복제 데이터베이스의 이름을 지정합니다. 그러면 기본 사이트 데이터베이스가 Service Broker를 사용하여 데이터베이스 복제 서버의 데이터베이스와 통신하도록 구성됩니다.  

    다음 쿼리를 실행하여 데이터베이스 복제 서버에서 인증서를 가져오고 필요한 세부 설정을 지정합니다. **EXEC sp_BgbConfigSSBForRemoteService 'REPLICA', '&lt;SQL Service Broker 포트\>', '&lt;인증서 파일 경로\>', '&lt;복제 SQL Server FQDN\>', '&lt;복제 데이터베이스 이름\>'**  

   > [!NOTE]  
   >  데이터베이스 복제 서버가 SQL Server의 기본 인스턴스에 있지 않으면 이 단계에서 복제 데이터베이스 이름 외에 인스턴스 이름도 지정해야 합니다. 이렇게 하려면 **&lt;복제본 데이터베이스 이름\>** 을 **\인스턴스 이름\\복제본 데이터베이스 이름\>** 으로 바꿉니다.  

4. 그 다음에는, 사이트 데이터베이스 서버에서 다음 명령을 실행하여 사이트 데이터베이스 서버의 인증서를 내보냅니다. **EXEC sp_BgbCreateAndBackupSQLCert '&lt;인증서 백업 파일 경로\>'**  

    사이트 데이터베이스 서버에서 인증서를 내보낸 후 인증서 사본을 데이터베이스 복제 서버에 저장합니다.  

5. **SQL Server Management Studio** 를 사용하여 데이터베이스 복제 서버 데이터베이스에 연결합니다. 데이터베이스 복제 서버 데이터베이스에 연결한 후 인증서를 가져오는 쿼리를 실행하고 기본 사이트의 사이트 코드 및 사이트 데이터베이스 서버에서 사용 중인 Service Broker 포트를 지정합니다. 그러면 데이터베이스 복제 서버가 Service Broker를 사용하여 기본 사이트의 데이터베이스와 통신하도록 구성됩니다.  

    다음 쿼리를 실행하여 사이트 데이터베이스 서버에서 인증서를 가져옵니다. **EXEC sp_BgbConfigSSBForRemoteService '&lt;사이트 코드\>', '&lt;SQL Service Broker 포트\>', '&lt;인증서 파일 경로\>'**  

   사이트 데이터베이스와 데이터베이스 복제 데이터베이스의 구성을 완료한 후 몇 분이 지나면 기본 사이트의 알림 관리자가 기본 사이트 데이터베이스에서 데이터베이스 복제본으로의 클라이언트 알림을 위해 Service Broker 대화를 설정합니다.  

###  <a name="bkmk_supscript"></a> 단일 SQL Server의 추가 데이터베이스 복제본용 보충 스크립트  
 계속 사용하려는 데이터베이스 복제본이 이미 있는 SQL Server의 데이터베이스 복제본 서버에 대해 4단계의 스크립트를 사용하여 자체 서명된 인증서를 구성할 때는 수정된 원본 스크립트 버전을 사용해야 합니다. 스크립트를 다음과 같이 수정하면 서버의 기존 인증서가 삭제되지 않으며, 고유한 식별 이름을 사용하여 후속 스크립트가 작성됩니다.  원본 스크립트를 다음과 같이 편집합니다.  

-   스크립트 항목 **# Delete existing cert if one exists** 및 **# Create the new cert**사이의 각 줄을 주석으로 처리하여 실행을 차단합니다. 이렇게 하려면 해당하는 각 줄의 첫 문자로  **#**  을 추가합니다.  

-   각각의 후속 데이터베이스 복제본에 대해 이 스크립트를 사용하여 인증서의 이름을 구성하고 업데이트합니다.  이렇게 하려면 **$enrollment.CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"** 줄을 편집하고 **ConfigMgr SQL Server Identification Certificate** 를  **ConfigMgr SQL Server Identification Certificate1**과 같은 새 이름으로 바꿉니다.  

##  <a name="BKMK_DBReplicaOps"></a> 데이터베이스 복제본 구성 관리  
 사이트에서 데이터베이스 복제본을 사용할 때 다음 섹션의 정보를 사용하면 데이터베이스 복제본을 제거하거나, 데이터베이스 복제본을 사용하는 사이트를 제거하거나, 사이트 데이터베이스를 SQL Server의 새 설치로 이동하는 프로세스를 보완할 수 있습니다. 다음 섹션의 정보를 사용하여 게시를 삭제하는 경우 데이터베이스 복제본에 사용하는 SQL Server 버전의 트랜잭션 복제를 삭제하는 지침을 사용하세요. 예를 들어 SQL Server 2008 R2를 사용하는 경우 [방법: 게시 삭제(복제 Transact-SQL 프로그래밍)](http://go.microsoft.com/fwlink/p/?LinkId=273934)를 참조하세요.  

> [!NOTE]  
>  데이터베이스 복제본용으로 구성된 사이트 데이터베이스를 복원한 후에, 데이터베이스 복제본을 사용하려면 먼저 게시 및 구독을 모두 다시 만드는 것을 포함해 각 데이터베이스 복제본을 다시 구성해야 합니다.  

###  <a name="BKMK_UninstallDbReplica"></a> 데이터베이스 복제본 제거  
 관리 지점에 대한 데이터베이스 복제본을 사용하는 경우 일정 기간 동안 데이터베이스 복제본을 제거한 다음 다시 구성해야 사용할 수 있습니다. 예를 들어 Configuration Manager 사이트를 새 서비스 팩으로 업그레이드하기 전에 데이터베이스 복제본을 제거해야 합니다. 사이트 업그레이드를 완료한 후에 데이터베이스 복제본을 사용할 수 있도록 복원할 수 있습니다.  

 데이터베이스 복제본을 제거하려면 다음 단계를 수행하세요.  

1.  Configuration Manager 콘솔의 **관리** 작업 영역에서 **사이트 구성**을 확장한 다음 **서버 및 사이트 시스템 역할**을 선택하고 세부 정보 창에서 제거하려는 데이터베이스 복제본을 사용하는 관리 지점을 호스트하는 사이트 시스템 서버를 선택합니다.  

2.  **사이트 시스템 역할** 창에서 **관리 지점** 을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택합니다.  

3.  **관리 지점 데이터베이스** 탭에서 **사이트 데이터베이스 사용** 을 선택하여 데이터베이스 복제본 대신 사이트 데이터베이스를 사용하도록 관리 지점을 구성합니다. 그런 다음 **확인** 을 클릭하여 구성을 저장합니다.  

4.  그 다음에는 **SQL Server Management Studio** 를 사용하여 다음 작업을 수행합니다.  

    -   사이트 서버 데이터베이스에서 데이터베이스 복제본에 대한 게시를 삭제합니다.  

    -   데이터베이스 복제 서버에서 데이터베이스 복제본에 대한 구독을 삭제합니다.  

    -   데이터베이스 복제 서버에서 복제 데이터베이스를 삭제합니다.  

    -   사이트 데이터베이스 서버에서 게시 및 배포를 사용하지 않도록 설정합니다. 게시 및 배포를 사용하지 않도록 설정하려면 복제 폴더를 마우스 오른쪽 단추로 클릭하고 **게시 및 배포 해제**를 클릭합니다.  

5.  게시, 구독, 복제 데이터베이스를 삭제하고 사이트 서버 데이터베이스에서 게시를 사용하지 않도록 설정하면 데이터베이스 복제본이 제거됩니다.  

###  <a name="BKMK_DBReplicaOps_Uninstall"></a> 데이터베이스 복제본을 게시하는 사이트 서버 제거  
 데이터베이스 복제본을 게시하는 사이트를 제거하기 전에 다음 단계를 수행하여 게시 및 구독을 정리하세요.  

1.  **SQL Server Management Studio** 를 사용하여 사이트 서버 데이터베이스에서 데이터베이스 복제본 게시를 삭제합니다.  

2.  **SQL Server Management Studio** 를 사용하여 이 사이트의 데이터베이스 복제본을 호스팅하는 각 원격 SQL Server에서 데이터베이스 복제본 구독을 삭제합니다.  

3.  사이트를 제거합니다.  

###  <a name="BKMK_DBReplicaOps_Move"></a> 데이터베이스 복제본을 게시하는 사이트 서버 데이터베이스 이동  
 새 컴퓨터로 사이트 데이터베이스를 이동하는 경우 다음 단계를 수행하세요.  

1.  **SQL Server Management Studio** 를 사용하여 사이트 서버 데이터베이스에서 데이터베이스 복제본에 대한 게시를 삭제합니다.  

2.  **SQL Server Management Studio** 를 사용하여 이 사이트의 각 데이터베이스 복제 서버에서 데이터베이스 복제본에 대한 구독을 삭제합니다.  

3.  데이터베이스를 새 SQL Server 컴퓨터로 이동합니다. 자세한 내용은 [Modify the site database configuration](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_dbconfig) 항목의 [Modify your System Center Configuration Manager infrastructure](../../../../core/servers/manage/modify-your-infrastructure.md) 섹션을 참조하세요.  

4.  사이트 데이터베이스 서버에서 데이터베이스 복제본에 대한 게시를 다시 만듭니다. 자세한 내용은 이 항목의 [1단계 - 데이터베이스 복제본을 게시하도록 사이트 데이터베이스 서버 구성](#BKMK_DBReplica_ConfigSiteDB) 를 참조하세요.  

5.  각 데이터베이스 복제 서버에서 데이터베이스 복제본에 대한 구독을 다시 만듭니다. 자세한 내용은 이 항목의 [2단계 - 데이터베이스 복제본 서버 구성](#BKMK_DBReplica_ConfigSrv) 를 참조하십시오.  
