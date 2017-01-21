---
title: "온-프레미스 인프라 업그레이드 | System Center Configuration Manager"
description: "SQL Server, 사이트 시스템의 사이트 운영 체제 등의 인프라를 업그레이드하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ca970dd-e71c-404f-9435-d36e773a0db2
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: c8115fba0722fc902e60ce201d8a9914036c1245
ms.openlocfilehash: 1239bf81991bb233a9640606bb47f598a70d5e50


---
# <a name="upgrade-on-premises-infrastructure-that-supports-system-center-configuration-manager"></a>System Center Configuration Manager를 지원하는 온-프레미스 인프라 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 정보를 사용하여 System Center Configuration Manager를 실행하는 인프라를 업그레이드할 수 있습니다.  

##  <a name="a-namebkmksupconfigupgradesitesrva-upgrade-site-operating-system-of-site-systems"></a><a name="BKMK_SupConfigUpgradeSiteSrv"></a> 사이트 시스템의 사이트 운영 체제 업그레이드  
 Configuration Manager는 다음과 같은 상황에서 사이트 서버를 호스트하는 서버의 운영 체제 및 사이트 시스템 역할을 호스트하는 원격 서버의 현재 위치 업그레이드를 지원합니다.  

-   업그레이드 후 Windows의 서비스 팩 수준이 Configuration Manager에서 계속 지원되는 경우 상위 Windows Server 서비스 팩으로의 현재 위치 업그레이드  
-   현재 위치 업그레이드:
    - Windows Server 2012 R2에서 Windows Server 2016으로 업그레이드([추가 정보 참조](#upgrade-windows-server-2012-r2-to-2016))
    - Windows Server 2012에서 Windows Server 2012 R2로 업그레이드([추가 정보 참조](#upgrade-windows-server-2012-to-windows-server-2012-r2))
    - Configuration Manager 버전 1602 이상을 사용하는 경우 Windows Server 2008 R2를 Windows Server 2012 R2로 업그레이드할 수도 있습니다([추가 정보 참조](#upgrade-windows-server-2008-r2-to-windows-server-2012-r2)).

    > [!WARNING]  
    >  Windows Server 2012 R2로 업그레이드하기 전에 서버에서 **WSUS 3.2를 제거** 해야 합니다.  
    >   
    >  이 중요 단계에 대한 자세한 내용은 Windows Server 문서에서 [Windows Server Update Services 개요](https://technet.microsoft.com/library/hh852345.aspx) 새로운 기능 및 변경된 기능 섹션을 참조하세요.  

서버를 업그레이드하려면 업그레이드할 운영 체제에서 제공하는 업그레이드 절차를 따르세요.  다음을 참조하세요.
  -  Windows Server 문서에서 [Windows Server 2012 R2에 대한 업그레이드 옵션](https://technet.microsoft.com/library/dn303416.aspx)  
  - Windows Server 문서에서 [Windows Server 2016에 대한 업그레이드 및 변환 옵션](https://technet.microsoft.com/windows-server-docs/get-started/supported-upgrade-paths)

### <a name="upgrade-windows-server-2012-r2-to-2016"></a>Windows Server 2012 R2를 2016으로 업그레이드  
이 운영 체제 업그레이드 시나리오에는 다음과 같은 조건이 있습니다.

**업그레이드 전:**  
-   SCEP(System Center Endpoint Protection) 클라이언트를 제거합니다. Windows Server 2016에는 SCEP 클라이언트를 대체하는 Windows Defender가 기본 제공됩니다. SCEP 클라이언트가 있으면 Windows Server 2016으로 업그레이드할 수 없습니다.

**업그레이드 후:**
-   Windows Defender가 사용되고 자동 시작되도록 설정되었으며 실행되고 있는지 확인합니다.
-   다음 Configuration Manager 서비스가 실행되고 있는지 확인합니다.
  -     SMS_EXECUTIVE
  -     SMS_SITE_COMPONENT_MANAGER


-   **Windows 프로세스 활성화** 및 **WWW/W3svc** 서비스가 다음 사이트 시스템 역할에 대해 사용되고 자동 시작되도록 설정되었으며 실행되고 있는지 확인합니다(업그레이드 중에는 해당 서비스를 사용할 수 없음).
  -     사이트 서버
  -     관리 지점
  -     응용 프로그램 카탈로그 웹 서비스 지점
  -     응용 프로그램 카탈로그 웹 사이트 지점


-   사이트 시스템 역할을 호스트하는 각 서버가 해당 서버에서 실행되는 [사이트 시스템 역할에 대한 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 계속해서 모두 충족하는지 확인합니다. 예를 들어 BITS 또는 WSUS를 다시 설치하거나 IIS에 대한 특정 설정을 구성해야 할 수 있습니다.

  누락된 필수 조건을 복원한 후 서버를 한 번 더 다시 부팅하여 서비스가 시작되고 작동하도록 합니다.

**원격 Configuration Manager 콘솔에 대해 알려진 문제:**  
사이트 서버 또는 SMS_Provider 인스턴스를 호스트하는 서버를 Windows Server 2016으로 업그레이드한 후 관리자가 Configuration Manager 콘솔을 사이트에 연결하지 못할 수 있습니다. 이 문제를 해결하려면 WMI에서 SMS Admins 그룹의 사용 권한을 수동으로 복원해야 합니다. 사이트 서버 및 SMS 공급자 인스턴스를 호스트하는 각 원격 서버에서 사용 권한을 설정해야 합니다.

1. 해당 서버에서 MMC(Microsoft Management Console)를 열고 **WMI 컨트롤**용 스냅인을 추가한 다음 **로컬 컴퓨터**를 선택합니다.
2. MMC에서 **WMI 컨트롤(로컬)**의 **속성**을 열고 **보안** 탭을 선택합니다.
3. 루트 아래의 트리를 확장하고 **SMS** 노드를 선택한 다음 **보안**을 클릭합니다.  **SMS Admins** 그룹에 다음 사용 권한이 있는지 확인합니다.
  -     계정 사용
  -     원격 사용
4. **보안 탭**의 SMS 노드 아래에서 **사이트 _<sitecode>** 노드를 선택하고 **보안**을 클릭합니다. **SMS Admins** 그룹에 다음 사용 권한이 있는지 확인합니다.
  -   메서드 실행
  -   공급자 쓰기
  -   계정 사용
  -   원격 사용
5. 사용 권한을 저장하여 Configuration Manager 콘솔에 대한 액세스를 복원합니다.

### <a name="windows-server-2012-to-windows-server-2012-r2"></a>Windows Server 2012에서 Windows Server 2012 R2로 업그레이드

**업그레이드 전:**
-  다른 지원되는 시나리오와 달리 이 시나리오에서는 업그레이드 전에 추가 고려 사항이 필요하지 않습니다.

**업그레이드 후:**
  - 다음 사이트 시스템 역할에 대해 Windows 배포 서비스가 시작되어 실행되고 있는지 확인합니다(업그레이드 중에는 이 서비스가 중지됨).
    - 사이트 서버
    - 관리 지점
    - 응용 프로그램 카탈로그 웹 서비스 지점
    - 응용 프로그램 카탈로그 웹 사이트 지점


  -     **Windows 프로세스 활성화** 및 **WWW/W3svc** 서비스가 다음 사이트 시스템 역할에 대해 사용되고 자동 시작되도록 설정되었으며 실행되고 있는지 확인합니다(업그레이드 중에는 해당 서비스를 사용할 수 없음).
    -   사이트 서버
    -   관리 지점
    -   응용 프로그램 카탈로그 웹 서비스 지점
    -   응용 프로그램 카탈로그 웹 사이트 지점


  -     사이트 시스템 역할을 호스트하는 각 서버가 해당 서버에서 실행되는 [사이트 시스템 역할에 대한 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 계속해서 모두 충족하는지 확인합니다. 예를 들어 BITS 또는 WSUS를 다시 설치하거나 IIS에 대한 특정 설정을 구성해야 할 수 있습니다.

  누락된 필수 조건을 복원한 후 서버를 한 번 더 다시 부팅하여 서비스가 시작되고 작동하도록 합니다.

### <a name="upgrade-windows-server-2008-r2-to-windows-server-2012-r2"></a>Windows Server 2008 R2에서 Windows Server 2012 R2로 업그레이드
이 운영 체제 업그레이드 시나리오에는 다음과 같은 조건이 있습니다.  

**업그레이드 전:**
-   WSUS 3.2를 제거합니다.  
    서버 운영 체제를 Windows Server 2012 R2로 업그레이드하기 전에 서버에서 WSUS 3.2를 제거해야 합니다. 이 중요 단계에 대한 자세한 내용은 Windows Server 문서에서 Windows Server Update Services 개요의 새로운 기능 및 변경된 기능 섹션을 참조하세요.

**업그레이드 후:**
  - 다음 사이트 시스템 역할에 대해 Windows 배포 서비스가 시작되어 실행되고 있는지 확인합니다(업그레이드 중에는 이 서비스가 중지됨).
    - 사이트 서버
    - 관리 지점
    - 응용 프로그램 카탈로그 웹 서비스 지점
    - 응용 프로그램 카탈로그 웹 사이트 지점


  -     **Windows 프로세스 활성화** 및 **WWW/W3svc** 서비스가 다음 사이트 시스템 역할에 대해 사용되고 자동 시작되도록 설정되었으며 실행되고 있는지 확인합니다(업그레이드 중에는 해당 서비스를 사용할 수 없음).
    -   사이트 서버
    -   관리 지점
    -   응용 프로그램 카탈로그 웹 서비스 지점
    -   응용 프로그램 카탈로그 웹 사이트 지점


  -     사이트 시스템 역할을 호스트하는 각 서버가 해당 서버에서 실행되는 [사이트 시스템 역할에 대한 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 계속해서 모두 충족하는지 확인합니다. 예를 들어 BITS 또는 WSUS를 다시 설치하거나 IIS에 대한 특정 설정을 구성해야 할 수 있습니다.

  누락된 필수 조건을 복원한 후 서버를 한 번 더 다시 부팅하여 서비스가 시작되고 작동하도록 합니다.


### <a name="unsupported-upgrade-scenarios"></a>지원되지 않는 업그레이드 시나리오
다음 Windows Server 업그레이드 시나리오는 자주 질문을 받지만 Configuration Manager에서 지원되지 않습니다.  

-   Windows Server 2008에서 Windows Server 2012 이상으로 업그레이드  
-   Windows Server 2008 R2에서 Windows Server 2012로 업그레이드



##  <a name="a-namebkmksupconfigupgradeclienta-upgrade-the-operating-system-of-configuration-manager-clients"></a><a name="BKMK_SupConfigUpgradeClient"></a> Configuration Manager 클라이언트의 운영 체제 업그레이드  
 Configuration Manager는 다음과 같은 상황에서 Configuration Manager 클라이언트의 운영 체제 현재 위치 업그레이드를 지원합니다.  

-   업그레이드 후의 서비스 팩 수준이 Configuration Manager에서 계속 지원되는 경우 상위 Windows 서비스 팩으로의 현재 위치 업그레이드  

-   지원되는 버전에서 Windows 10로의 Windows 현재 위치 업그레이드. 자세한 내용은 [System Center Configuration Manager를 사용하여 Windows를 최신 버전으로 업그레이드](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md)를 참조하세요.  

-   Windows 10의 빌드 간 서비스 업그레이드.  자세한 내용은 [System Center Configuration Manager를 사용하여 Windows as a Service 관리](../../../osd/deploy-use/manage-windows-as-a-service.md)를 참조하세요.  

##  <a name="a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server"></a><a name="BKMK_SupConfigUpgradeDBSrv"></a> 사이트 데이터베이스 서버에서 SQL Server 업그레이드  
  Configuration Manager는 사이트 데이터베이스 서버에서 지원되는 SQL 버전의 SQL Server 현재 위치 업그레이드를 지원합니다. 다음은 Configuration Manager에서 지원하는 SQL Server 업그레이드 시나리오 및 각 시나리오의 요구 사항에 대한 세부 정보입니다.

 Configuration Manager에서 지원되는 SQL Server 버전에 대한 자세한 내용은 [System Center Configuration Manager에 대한 SQL Server 버전 지원](../../../core/plan-design/configs/support-for-sql-server-versions.md)을 참조하세요.  

 **SQL Server의 서비스 팩 버전 업그레이드:**    
 Configuration Manager는 업그레이드 후의 SQL Server 서비스 팩 수준이 Configuration Manager에서 계속 지원되는 경우 상위 서비스 팩으로의 SQL Server 현재 위치 업그레이드를 지원합니다.

 계층 구조에 Configuration Manager 사이트가 여러 개 있으면 각 사이트는 서로 다른 SQL Server 서비스 팩 버전을 실행할 수 있으며, 사이트가 사이트 데이터베이스에 사용되는 SQL Server 서비스 팩 버전을 업그레이드하는 순서에는 제한이 없습니다.

 **새 버전의 SQL Server로 업그레이드:**   
 Configuration Manager는 다음 버전으로의 SQL Server 현재 위치 업그레이드를 지원합니다.

 - SQL Server 2012  
 - SQL Server 2014  
 - SQL Server 2016  

사이트 데이터베이스를 호스트하는 SQL Server 버전을 업그레이드하는 경우 사이트에서 사용되는 SQL Server 버전을 다음과 같은 순서로 업그레이드해야 합니다.

 1. 먼저 중앙 관리 사이트에서 SQL Server를 업그레이드합니다.
 2. 보조 사이트의 상위 기본 사이트를 업그레이드하기 전에 보조 사이트를 업그레이드합니다.
 3. 마지막으로 부모 기본 사이트를 업그레이드합니다. 여기에는 중앙 관리 사이트에 보고를 하는 자식 기본 사이트와 계층의 최상위 사이트인 독립 실행형 기본 사이트가 모두 포함됩니다.



**SQL Server에 대한 자세한 내용은 TechNet에서 SQL Server 설명서를 참조하세요.**  
-   [SQL Server 2014로 업그레이드](http://technet.microsoft.com/library/ms143393\(v=sql.120))  
-   [SQL Server 2012로 업그레이드](http://technet.microsoft.com/library/ms143393\(v=sql.110))
-   [SQL Server 2016으로 업그레이드](https://technet.microsoft.com/library/bb677622(v=sql.130))



### <a name="to-upgrade-sql-server-on-the-site-database-server"></a>사이트 데이터베이스 서버에서 SQL Server를 업그레이드하려면  

1.  사이트에서 모든 Configuration Manager 서비스를 중지합니다.  
2.  SQL Server를 지원되는 버전으로 업그레이드합니다.  
3.  Configuration Manager 서비스를 다시 시작합니다.  

> [!NOTE]  
>  중앙 관리 사이트에서 사용 중인 SQL Server 버전을 Standard Edition에서 Datacenter 또는 Enterprise Edition으로 변경할 때 계층의 클라이언트 수를 제한하는 데이터베이스 파티션은 변경되지 않습니다.



<!--HONumber=Nov16_HO1-->


