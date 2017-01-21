---
title: "사이트 제거 | System Center Configuration Manager"
description: "System Center Configuration Manager 사이트를 제거해야 하는 경우 다음 세부 정보를 지침으로 사용합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d466edd2-97f0-44c1-a73e-d71abbdbf4a8
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: db203f6b8b76df28b2cd03f5ebd931c520294ba6


---
# <a name="uninstall-sites-and-hierarchies-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 사이트 및 계층 제거

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 사이트를 제거해야 하는 경우 다음 세부 정보를 지침으로 사용합니다.  

여러 사이트가 있는 계층을 해제하려면 제거의 순서가 중요합니다.  

-   계층의 맨 아래에 있는 사이트를 제거하기 시작하여 위쪽으로 이동합니다.  

-   먼저 기본 사이트에 연결된 보조 사이트를 제거합니다.  

-   그런 다음 기본 사이트를 제거합니다.  

-   모든 기본 사이트가 제거된 후 중앙 관리 사이트를 제거할 수 있습니다.  


##  <a name="a-namebkmkremovesecondarysitea-remove-a-secondary-site-from-a-hierarchy"></a><a name="BKMK_RemoveSecondarysite"></a> 계층에서 보조 사이트 제거  
보조 사이트는 새 부모 기본 사이트로 이동하거나 재할당할 수 없습니다. 계층에서 보조 사이트를 제거하려면 직계 부모 사이트에서 삭제해야 합니다. 보조 사이트를 제거하려면 Configuration Manager 콘솔에서 보조 사이트 삭제 마법사를 사용합니다. 보조 사이트를 제거하는 경우 보조 사이트를 삭제할지 또는 설치를 제거할지 선택해야 합니다.  

-   **보조 사이트 제거**: 네트워크에서 액세스할 수 있는 기능적 보조 사이트를 제거하려면 이 옵션을 사용합니다. 이 옵션은 보조 사이트 서버에서 Configuration Manager를 제거한 다음 사이트 및 관련 리소스에 대한 모든 정보를 Configuration Manager 계층 구조에서 삭제합니다. Configuration Manager에서 보조 사이트를 설치하는 동안 SQL Server Express를 설치한 경우 보조 사이트를 제거하는 동안 Configuration Manager에서 SQL Express도 제거합니다. 보조 사이트를 설치하기 전에 SQL Server Express가 설치되었던 경우 Configuration Manager는 SQL Server Express를 제거하지 않습니다.  

-   **보조 사이트 삭제**: 다음 중 하나에 해당하는 경우 이 옵션을 사용합니다.  

    -   보조 사이트를 설치하지 못했습니다.  

    -   보조 사이트를 제거한 후에도 Configuration Manager 콘솔에 보조 사이트가 계속 표시됩니다.  

    이 옵션은 Configuration Manager 계층 구조에서 사이트 및 관련 리소스에 대한 모든 정보를 삭제하지만 보조 사이트 서버에 설치된 Configuration Manager는 그대로 둡니다.  

    > [!NOTE]  
    >  계층 유지 관리 도구 및 **/DELSITE** 옵션을 사용하여 보조 사이트를 삭제할 수도 있습니다. 자세한 내용은 [System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)를 참조하세요.  

#### <a name="to-uninstall-or-delete-a-secondary-site"></a>보조 사이트를 제거 또는 삭제하려면  

1.  설치 프로그램을 실행하는 관리자에게 다음 보안 권한이 있는지 확인합니다.  

    -   보조 사이트 컴퓨터에 대한 관리 권한  

    -   기본 사이트의 원격 사이트 데이터베이스 서버에 대한 로컬 관리자 권한(데이터베이스 서버가 원격인 경우)  

    -   부모 기본 사이트에 대한 인프라 관리자 또는 전체 관리자 보안 역할  

    -   보조 사이트의 사이트 데이터베이스에 대한 Sysadmin 권한  

2.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

3.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.  

4.  제거할 보조 사이트 서버를 선택합니다.  

5.  **홈** 탭의 **사이트** 그룹에서 **삭제**를 클릭합니다.  

6.  **일반** 페이지에서 보조 사이트를 제거할지 또는 삭제할지를 선택하고 **다음**을 클릭합니다.  

7.  **요약** 페이지에서 설정을 확인하고 **다음**을 클릭합니다.  

8.  **완료** 페이지에서 **닫기** 를 클릭하여 마법사를 종료합니다.  

##  <a name="a-namebkmkuninstallprimarya-uninstall-a-primary-site"></a><a name="BKMK_UninstallPrimary"></a> 기본 사이트 제거  
Configuration Manager 설치 프로그램을 실행하여 연결된 보조 사이트가 없는 기본 사이트를 제거할 수 있습니다. 기본 사이트를 제거하기 전에 다음 사항을 고려해야 합니다.  

-   Configuration Manager 클라이언트가 사이트에 구성된 경계 내에 있고 기본 사이트가 Configuration Manager 계층 구조의 일부인 경우 기본 사이트를 제거하기 전에 경계를 계층 구조의 다른 기본 사이트에 추가하는 것이 좋습니다.  

-   기본 사이트 서버를 더 이상 사용할 수 없는 경우 중앙 관리 사이트에서 계층 유지 관리 도구를 사용하여 사이트 데이터베이스에서 기본 사이트를 삭제해야 합니다. 자세한 내용은 [System Center Configuration Manager용 계층 구조 유지 관리 도구(Preinst.exe)](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md)를 참조하세요.  

기본 사이트를 제거하려면 다음 절차를 참조합니다.  

#### <a name="to-uninstall-a-primary-site"></a>기본 사이트 제거하려면  

1.  설치 프로그램을 실행하는 관리자에게 다음 보안 권한이 있는지 확인합니다.  

    -   중앙 관리 사이트 서버에 대한 로컬 관리자 권한  

    -   중앙 관리 사이트의 원격 사이트 데이터베이스 서버에 대한 로컬 관리자 권한(데이터베이스 서버가 원격인 경우)  

    -   중앙 관리 사이트의 사이트 데이터베이스에 대한 Sysadmin 권한  

    -   기본 사이트 컴퓨터에 대한 로컬 관리자 권한  

    -   기본 사이트의 원격 사이트 데이터베이스 서버에 대한 로컬 관리자 권한(데이터베이스 서버가 원격인 경우)  

    -   중앙 관리 사이트에 대한 인프라 관리자 또는 전체 관리자 보안 역할에 연결된 사용자 이름  

2.  다음 방법 중 하나를 사용하여 기본 사이트 서버에서 Configuration Manager 설치 프로그램을 시작합니다.  

    -   **시작**에서 **Configuration Manager 설치**를 클릭합니다.  

    -   &lt;*Configuration Manager 설치 미디어*>\SMSSETUP\BIN\X64에서 Setup.exe를 엽니다.  

    -   &lt;*Configuration Manager 설치 경로*>\BIN\X64에서 Setup.exe를 엽니다.  

3.  **시작하기 전에** 페이지에서 **다음**을 클릭합니다.  

4.  **시작** 페이지에서 **Configuration Manager 사이트 제거**를 선택하고 **다음**을 클릭합니다.  

5.  **Configuration Manager 사이트 제거**에서 기본 사이트 서버의 사이트 데이터베이스를 제거할지 여부와 Configuration Manager 콘솔을 제거할지 여부를 지정합니다. 기본적으로, 두 항목 모두 제거됩니다.  

    > [!IMPORTANT]  
    >  기본 사이트에 보조 사이트가 연결되어 있는 경우 기본 사이트를 제거하기 전에 보조 사이트를 제거해야 합니다.  

6.  **예**를 클릭하여 Configuration Manager 기본 사이트 제거를 확인합니다.  

##  <a name="a-namebkmkuninstallprimarydistviewsa-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a><a name="BKMK_UninstallPrimaryDistViews"></a> 분산 보기에 구성된 기본 사이트 제거  
 분산 보기가 중앙 관리 사이트에 대한 복제 링크에 구성된 자식 기본 사이트를 제거하려면 먼저 계층에서 분산 보기를 사용하지 않도록 설정해야 합니다. 기본 사이트를 제거하기 전에 분산 보기를 사용하지 않도록 설정하려면 다음 정보를 참조합니다.  

#### <a name="to-uninstall-a-primary-site-that-is-configured-with-distributed-views"></a>분산 보기에 구성된 기본 사이트를 제거하려면  

1.  기본 사이트를 제거하기 전에 중앙 관리 사이트와 기본 사이트 간 계층의 각 링크에서 분산 보기를 사용하지 않도록 설정해야 합니다.  

2.  각 링크에서 분산 보기를 사용하지 않도록 설정한 후 기본 사이트의 데이터가 중앙 관리 사이트에서 다시 초기화되는 작업이 완료되었는지 확인합니다. Configuration Manager 콘솔에서 **모니터링** 작업 영역의 **데이터베이스 복제** 노드에 있는 링크를 확인할 때 데이터 초기화를 모니터링할 수 있습니다.  

3.  중앙 관리 사이트에서 데이터 재초기화가 성공적으로 완료되면 기본 사이트를 제거할 수 있습니다. 기본 사이트를 제거하려면 이 항목에서 [기본 사이트 제거](#BKMK_UninstallPrimary) 섹션을 참조하세요.  

4.  기본 사이트를 완전히 제거한 후 기본 사이트에 대한 링크의 분산 보기를 다시 구성할 수 있습니다.  

    > [!IMPORTANT]  
    >  각 사이트에서 분산 보기를 사용하지 않도록 설정하기 전에 기본 사이트를 제거하는 경우 또는 중앙 관리 사이트에서 기본 사이트 데이터의 재초기화가 성공적으로 완료되기 전에 기본 사이트를 제거하는 경우 기본 사이트와 중앙 관리 사이트 간 데이터 복제가 실패할 수 있습니다. 이러한 경우 계층의 각 링크에 대한 분산 보기를 사용하지 않도록 설정한 다음 중앙 관리 사이트에서 데이터 재초기화가 성공적으로 완료되면 분산 보기를 구성할 수 있습니다.  

##  <a name="a-namebkmkuninstallcasa-uninstall-the-central-administration-site"></a><a name="BKMK_UninstallCAS"></a> 중앙 관리 사이트 제거  
 Configuration Manager 설치 프로그램을 실행하여 하위 기본 사이트가 없는 중앙 관리 사이트를 제거할 수 있습니다. 중앙 관리 사이트를 제거하려면 다음 절차를 참조합니다.  

#### <a name="to-uninstall-a-central-administration-site"></a>중앙 관리 사이트를 제거하려면  

1.  설치 프로그램을 실행하는 관리자에게 다음 보안 권한이 있는지 확인합니다.  

    -   중앙 관리 사이트 서버에 대한 로컬 관리자 권한  

    -   중앙 관리 사이트의 사이트 데이터베이스 서버에 대한 로컬 관리자 권한(사이트 데이터베이스 서버가 사이트 서버에 설치되어 있지 않은 경우)  

2.  다음 방법 중 하나를 사용하여 중앙 관리 사이트 서버에서 Configuration Manager 설치 프로그램을 시작합니다.  

    -   **시작**에서 **Configuration Manager 설치**를 클릭합니다.  

    -   &lt;*Configuration Manager 설치 미디어*>\SMSSETUP\BIN\X64에서 Setup.exe를 엽니다.  

    -   &lt;*Configuration Manager 설치 경로*>\BIN\X64에서 Setup.exe를 엽니다.  

3.  **시작하기 전에** 페이지에서 **다음**을 클릭합니다.  

4.  **시작** 페이지에서 **Configuration Manager 사이트 제거**를 선택하고 **다음**을 클릭합니다.  

5.  **Configuration Manager 사이트 제거**에서 중앙 관리 사이트 서버의 사이트 데이터베이스를 제거할지 여부와 Configuration Manager 콘솔을 제거할지 여부를 지정합니다. 기본적으로, 두 항목 모두 제거됩니다.  

    > [!IMPORTANT]  
    >  중앙 관리 사이트에 기본 사이트가 연결되어 있는 경우 중앙 관리 사이트를 제거하기 전에 기본 사이트를 제거해야 합니다.  

6.  **예**를 클릭하여 Configuration Manager 중앙 관리 사이트 제거를 확인합니다.  



<!--HONumber=Nov16_HO1-->


