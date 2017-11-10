---
title: "보고 구성"
titleSuffix: Configuration Manager
description: "SQL Server Reporting Services에 대한 정보를 포함하여 Configuration Manager 계층 구조에서 보고를 설정하는 방법에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
caps.latest.revision: "6"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: be8c36c73478e232254185681546f5f52c7d701f
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="configuring-reporting-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 보고 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 콘솔에서 보고서를 만들고 수정하고 실행하려면 먼저 여러 가지 구성 작업을 수행해야 합니다. 이 항목의 다음 섹션에서는 Configuration Manager 계층 구조에서 보고를 구성하는 방법을 설명합니다.  

 계층에서 Reporting Services를 설치하고 구성하기 전에 먼저 다음 Configuration Manager 보고 항목을 검토하세요.  

-   [System Center Configuration Manager의 보고 소개](../../../core/servers/manage/introduction-to-reporting.md)  

-   [System Center Configuration Manager의 보고 계획](../../../core/servers/manage/planning-for-reporting.md)  

##  <a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services는 서버 기반의 보고 플랫폼으로서 다양한 데이터 원본에 대한 포괄적인 보고 기능을 제공합니다. Configuration Manager의 보고 서비스 지점은 SQL Server Reporting Services와 통신하여 Configuration Manager 보고서를 지정된 보고서 폴더에 복사하고 Reporting Services 설정을 구성하며 Reporting Services 보안 설정을 구성합니다. Reporting Services는 Configuration Manager 사이트 데이터베이스에 연결하여 보고서를 실행할 때 반환되는 데이터를 검색합니다.  

 Configuration Manager 사이트에 보고 서비스 지점을 설치하려면 먼저 보고 서비스 지점 사이트 시스템 역할을 호스트하는 사이트 시스템에서 SQL Server Reporting Services를 설치하고 구성해야 합니다. 보고 서비스 설치에 대한 자세한 내용은 [SQL Server TechNet Library](http://go.microsoft.com/fwlink/p/?LinkId=266389)를 참조하십시오.  

 SQL Server Reporting Services가 설치되어 제대로 실행되는지 확인하려면 다음 절차를 따르십시오.  

#### <a name="to-verify-that-sql-server-reporting-services-is-installed-and-running"></a>SQL Server Reporting Services가 설치되어 실행되고 있는지 확인하려면  

1.  바탕 화면에서 **시작**, **모든 프로그램**, **Microsoft SQL Server 2008 R2**, **구성 도구**, **Reporting Services Configuration Manager**를 차례로 클릭합니다.  

2.  **Reporting Services 구성 연결** 대화 상자에서 SQL Server Reporting Services를 호스팅하는 서버의 이름을 지정하고, 메뉴에서 SQL Reporting Services가 설치된 SQL Server 인스턴스를 선택한 후에 **연결**을 클릭합니다. Reporting Services Configuration Manager가 열립니다.  

3.  **보고서 서버 상태** 페이지에서 **보고서 서비스 상태** 가 **시작됨**으로 설정되어 있는지 확인합니다. 설정되어 있지 않은 경우 **시작**을 클릭합니다.  

4.  **웹 서비스 URL** 페이지에서 **보고서 서비스 웹 서비스 URL** 의 URL을 클릭하여 보고서 폴더에 대한 연결을 테스트합니다. **Windows 보안** 대화 상자가 열리고 보안 자격 증명을 입력하라는 메시지가 표시될 수 있습니다. 기본적으로 사용자 계정이 표시됩니다. 암호를 입력한 후에 **확인**을 클릭합니다. 웹 페이지가 성공적으로 열리는지 확인합니다. 브라우저 창을 닫습니다.  

5.  **데이터베이스** 페이지에서 **보고서 서버 모드** 설정이 **네이티브**를 사용하여 구성되어 있는지 확인합니다.  

6.  **보고서 관리자 URL** 페이지에서 **보고서 관리자 사이트 확인** 의 URL을 클릭하여 보고서 관리자의 가상 디렉터리에 대한 연결을 테스트합니다. **Windows 보안** 대화 상자가 열리고 보안 자격 증명을 입력하라는 메시지가 표시될 수 있습니다. 기본적으로 사용자 계정이 표시됩니다. 암호를 입력한 후에 **확인**을 클릭합니다. 웹 페이지가 성공적으로 열리는지 확인합니다. 브라우저 창을 닫습니다.  

    > [!NOTE]  
    >  Configuration Manager에서는 보고에 Reporting Services 보고서 관리자가 필요 없지만 인터넷 브라우저에 대한 보고서를 실행하거나 보고서 관리자를 사용하여 보고서를 관리하려는 경우 필요합니다.  

7.  **끝내기**를 클릭하여 Reporting Services Configuration Manager를 닫습니다.  

##  <a name="BKMK_ReportBuilder3"></a> 보고서 작성기 3.0을 사용하도록 보고 구성  

#### <a name="to-change-the-report-builder-manifest-name-to-report-builder-30"></a>보고서 작성기 이름을 보고서 작성기 3.0으로 변경하려면  

1.  Configuration Manager 콘솔을 실행하는 컴퓨터에서 Windows 레지스트리 편집기를 엽니다.  

2.  **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**으로 이동합니다.  

3.  값 데이터를 편집하도록 **ReportBuilderApplicationManifestName** 키를 두 번 클릭합니다.  

4.  **ReportBuilder_2_0_0_0.application** 을 **ReportBuilder_3_0_0_0.application**으로 변경하고 **확인**을 클릭합니다.  

5.  Windows 레지스트리 편집기를 닫습니다.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> 보고 서비스 지점 설치  
 사이트에서 보고서를 관리하려면 보고 서비스 지점을 사이트에 설치해야 합니다. 보고 서비스 지점에서는 보고서 폴더와 보고서를 SQL Server Reporting Services에 복사하고 보고서와 폴더에 대한 보안 정책을 적용하며 보고 서비스에서 구성 설정을 지정합니다. 먼저 보고 서비스 지점을 구성해야 Configuration Manager 콘솔에 보고서가 표시되고 Configuration Manager에서 보고서를 관리할 수 있습니다. 보고 서비스 지점은 Microsoft SQL Server Reporting Services가 설치되어 실행되는 서버에 구성해야 하는 사이트 시스템 역할입니다. 필수 조건에 대한 자세한 내용은 [보고에 대한 필수 조건](prerequisites-for-reporting.md)을 참조하세요.  

> [!IMPORTANT]  
>  보고 서비스 지점을 설치할 사이트를 선택할 때 보고서에 액세스할 사용자가 보고 서비스 지점이 설치되는 사이트와 동일한 보안 범위에 있어야 한다는 점에 유의하십시오.  

> [!NOTE]  
>  사이트 시스템에 보고 서비스 지점을 설치한 후에는 보고 서버의 URL을 변경하지 마십시오. 예를 들어 보고 서비스 지점을 만든 후에 Reporting Services Configuration Manager에서 보고서 서버의 URL을 수정할 경우 Configuration Manager 콘솔이 이전 URL을 계속 사용하므로 콘솔에서 보고서를 실행하거나 편집하거나 만들 수 없습니다. URL 보고서 서버를 변경해야 하는 경우 보고 서비스 지점을 제거하고 URL을 변경한 후에 보고 서비스 지점을 다시 설치하십시오.  

> [!IMPORTANT]    
> 보고 서비스 지점을 설치할 때 Reporting Services 지점 계정을 지정해야 합니다. 나중에 다른 도메인의 사용자가 보고서를 실행하려고 할 경우 도메인 간에 양방향 트러스트가 설정되지 않았으면 보고서를 실행할 수 없습니다.

 보고 서비스 지점을 설치하려면 다음 절차를 따르십시오.  

#### <a name="to-install-the-reporting-services-point-on-a-site-system"></a>사이트 시스템에 보고 서비스 지점을 설치하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.  

    > [!TIP]  
    >  보고 서비스 지점 사이트 역할을 호스팅하는 사이트 시스템만 나열하려면 **서버 및 사이트 시스템 역할** 을 마우스 오른쪽 단추로 클릭하고 **보고 서비스 지점**을 선택합니다.  

3.  다음 중 해당 단계를 사용하여 기존 또는 새 사이트 시스템 서버에 보고 서비스 지점 사이트 시스템 역할을 추가합니다.  

    > [!NOTE]  
    >  사이트 시스템 구성에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 시스템 역할 추가](../deploy/configure/add-site-system-roles.md)를 참조하세요.  

    -   **새 사이트 시스템**: **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 클릭합니다. **사이트 시스템 서버 만들기 마법사** 가 열립니다.  

    -   **기존 사이트 시스템**: 보고 서비스 지점 사이트 시스템 역할을 설치할 서버를 클릭합니다. 서버를 클릭하면 해당 서버에 이미 설치된 사이트 시스템 역할의 목록이 결과 창에 표시됩니다.  

         **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가**를 클릭합니다. **사이트 시스템 역할 추가 마법사** 가 열립니다.  

4.  **일반** 페이지에서 사이트 시스템 서버에 대한 일반 설정을 지정합니다. 기존 사이트 시스템 서버에 보고 서비스 지점을 추가할 때에는 이전에 구성된 값을 확인해야 합니다.  

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **보고 서비스 지점** 을 선택하고 **다음**을 클릭합니다.  

6.  **보고 서비스 지점** 페이지에서 다음 설정을 구성합니다.  

    -   **사이트 데이터베이스 서버 이름**: Configuration Manager 사이트 데이터베이스를 호스트하는 서버의 이름을 지정합니다. 일반적으로 마법사에서 서버의 FQDN(정규화된 도메인 이름)을 자동으로 검색합니다. 데이터베이스 인스턴스를 지정하려면 &lt;*서버 이름*>\&lt;*인스턴스 이름*> 형식을 사용합니다.  

    -   **데이터베이스 이름**: Configuration Manager 사이트 데이터베이스 이름을 지정하고 **확인**을 클릭하여 마법사에서 해당 사이트 데이터베이스에 액세스할 수 있는지 확인합니다.  

        > [!IMPORTANT]  
        >  보고 서비스 지점을 만드는 사용자 계정에 사이트 데이터베이스에 대한 **읽기** 권한이 있어야 합니다. 연결 테스트에 실패하면 빨간색 경고 아이콘이 표시됩니다. 이 아이콘 위로 커서를 이동하여 오류에 대한 세부 정보를 읽어 봅니다. 오류를 수정한 후 다시 **테스트** 를 클릭합니다.  

    -   **폴더 이름**: Reporting Services에서 Configuration Manager 보고서를 호스트하도록 만들어 사용하는 폴더 이름을 지정합니다.  

    -   **Reporting Services 서버 인스턴스**: 목록에서 SQL Server for Reporting Services 인스턴스를 선택합니다. 인스턴스가 하나만 있는 경우 기본적으로 해당 인스턴스가 나열되고 선택됩니다. 인스턴스가 하나도 없는 경우 SQL Server Reporting Services가 설치 및 구성되어 있고 사이트 시스템에서 SQL Server Reporting Services 서비스가 시작되었는지 확인합니다.  

        > [!IMPORTANT]  
        >  Configuration Manager는 선택된 사이트 시스템에서 현재 사용자의 컨텍스트에서 WMI(Windows Management Instrumentation)에 연결하여 SQL Server for Reporting Services 인스턴스를 검색합니다. 현재 사용자에게 사이트 시스템에서 WMI에 대한 **읽기** 권한이 있어야 하며, 그렇지 않으면 Reporting Services 인스턴스가 검색되지 않습니다.  

    -   **보고 서비스 지점 계정**: **설정**을 클릭한 후에 보고 서비스 지점의 SQL Server Reporting Services가 보고서에 표시되는 데이터를 검색하기 위해 Configuration Manager 사이트 데이터베이스에 연결할 때 사용할 계정을 선택합니다. **기존 계정**을 선택하여 이전에 Configuration Manager 계정으로 구성된 Windows 사용자 계정을 지정하거나 **새 계정**을 선택하여 현재 Configuration Manager 계정으로 구성되어 있지 않은 Windows 사용자 계정을 지정합니다. Configuration Manager에서는 사이트 데이터베이스에 대해 지정된 사용자 액세스 권한을 자동으로 부여합니다. 이 사용자는 **관리** 작업 영역에 있는 **보안** 노드의 **계정** 하위 폴더에 **ConfigMgr 보고 서비스 지점** 계정 이름으로 표시됩니다.  

         Reporting Services를 실행하는 계정은 도메인 로컬 보안 그룹인 **Windows Authorization Access Group**에 속해 있어야 하며, **tokenGroupsGlobalAndUniversal 읽기** 권한이 **허용**으로 설정되어야 합니다. 보고서를 성공적으로 실행하려면 Reporting Services 지점 계정과는 다른 도메인에서 사용자에 대해 양방향 트러스트 관계가 설정되어 있어야 합니다.

         지정된 Windows 사용자 계정과 암호는 암호화되어 보고 서비스 데이터베이스에 저장됩니다. 보고 서비스는 이 계정과 암호를 사용하여 사이트 데이터베이스에서 보고서에 대한 데이터를 검색합니다.  

        > [!IMPORTANT]  
        >  지정하는 계정은 보고 서비스 데이터베이스를 호스팅하는 컴퓨터에서 **로컬로 로그온** 권한을 가져야 합니다.  

7.  **보고 서비스 지점** 페이지에서 **다음**을 클릭합니다.  

8.  **요약** 페이지에서 설정을 확인한 후에 **다음** 을 클릭하여 보고 서비스 지점을 설치합니다.  

     마법사가 완료되면 보고서 폴더가 만들어지고 Configuration Manager 보고서가 지정된 보고서 폴더로 복사됩니다.  

    > [!NOTE]  
    >  보고서 폴더가 만들어지고 보고서가 보고서 서버에 복사될 때 Configuration Manager에서는 개체의 해당 언어를 파악합니다. 해당 언어 팩이 사이트에 설치된 경우 Configuration Manager가 사이트에서 보고서 서버를 실행하는 운영 체제와 동일한 언어로 개체를 만듭니다. 해당 언어를 사용할 수 없는 경우 보고서가 영어로 만들어져서 표시됩니다. 언어 팩 없이 사이트에 보고 서비스 지점을 설치할 경우 보고서가 영어로 설치됩니다. 보고 서비스 지점을 설치한 후에 언어 팩을 설치하는 경우 보고 서비스 지점을 제거한 후에 다시 설치해야만 해당 언어 팩 언어로 보고서를 사용할 수 있습니다. 언어 팩에 대한 자세한 내용은 [System Center Configuration Manager의 언어 팩](../deploy/install/language-packs.md)을 참조하세요.  

###  <a name="BKMK_FileInstallationAndSecurity"></a> 파일 설치 및 보고서 폴더 보안 권한  
 Configuration Manager에서는 보고 서비스 지점을 설치하고 Reporting Services를 구성하기 위해 다음과 같은 작업을 수행합니다.  

> [!IMPORTANT]  
>  SMS_Executive 서비스를 위해 구성된 계정의 자격 증명을 사용하여 다음 목록의 작업이 수행됩니다. 이 계정은 대개 사이트 서버 로컬 시스템 계정입니다.  

-   보고 서비스 지점 사이트 역할을 설치합니다.  

-   마법사에서 지정한 저장된 자격 증명을 사용하여 보고 서비스의 데이터 원본을 만듭니다. 이는 보고서를 실행할 때 보고 서비스가 사이트 데이터베이스에 연결하는 데 사용하는 Windows 사용자 계정과 암호입니다.  

-   Reporting Services에서 Configuration Manager 루트 폴더를 만듭니다.  

-   보고 서비스에서 **ConfigMgr 보고서 사용자** 및 **ConfigMgr 보고서 관리자** 보안 역할을 추가합니다.  

-   하위 폴더를 만들어 %ProgramFiles%\SMS_SRSRP의 Configuration Manager 보고서를 Reporting Services에 배포합니다.  

-   **사이트 읽기** 권한이 있는 Configuration Manager의 모든 사용자 계정의 루트 폴더에 Reporting Services의 **ConfigMgr 보고서 사용자** 역할을 추가합니다.  

-   **사이트 수정** 권한이 있는 Configuration Manager의 모든 사용자 계정의 루트 폴더에 Reporting Services의 **ConfigMgr 보고서 관리자** 역할을 추가합니다.  

-   보고서 폴더와 Configuration Manager 보안 개체 유형(Configuration Manager 사이트 데이터베이스에서 유지 관리됨) 간의 매핑을 검색합니다.  

-   Reporting Services의 특정 보고서 폴더에 대한 Configuration Manager 관리자의 다음 권한을 구성합니다.  

    -   사용자를 추가하고 Configuration Manager 개체에 대한 **보고서 실행** 권한이 있는 관리자에 대해 연결된 보고서 폴더에 **ConfigMgr 보고서 사용자** 역할을 할당합니다.  

    -   사용자를 추가하고 Configuration Manager 개체에 대한 **보고서 수정** 권한이 있는 관리자에 대해 연결된 보고서 폴더에 **ConfigMgr 보고서 관리자** 역할을 할당합니다.  

     Configuration Manager에서 Reporting Services에 연결하고 Configuration Manager 및 Reporting Services 루트 폴더와 특정 보고서 폴더의 사용자에 대한 권한을 설정합니다. 보고 서비스 지점을 처음 설치하면 Configuration Manager에서 10분 간격으로 Reporting Services에 연결하여 보고서 폴더에 구성된 사용자 권한이 Configuration Manager 사용자에 대해 설정된 연결된 권한인지 확인합니다. Reporting Services 보고서 관리자를 사용하여 보고서 폴더에서 사용자를 추가하거나 사용자 권한을 수정하면 Configuration Manager에서 사이트 데이터베이스에 저장된 역할 기반 할당을 사용하여 해당 변경 내용을 덮어씁니다. 또한 Configuration Manager는 Configuration Manager에서 보고 권한이 없는 사용자를 제거합니다.  

##  <a name="BKMK_SecurityRoles"></a> Configuration Manager의 보고 서비스 보안 역할  
 Configuration Manager에서 보고 서비스 지점을 설치하면 Reporting Services에 다음 보안 역할이 추가됩니다.  

-   **ConfigMgr 보고서 사용자**: 이 보안 역할이 할당된 사용자만 Configuration Manager 보고서를 실행할 수 있습니다.  

-   **ConfigMgr 보고서 관리자**: 이 보안 역할이 할당된 사용자는 Configuration Manager에서 보고와 관련된 모든 작업을 수행할 수 있습니다.  

##  <a name="BKMK_VerifyReportingServicesPointInstallation"></a> 보고 서비스 지점 설치 확인  
 보고 서비스 지점 사이트 역할을 추가하면 특정 상태 메시지와 로그 파일 항목을 보고 설치를 확인할 수 있습니다. 보고 서비스 지점 설치가 제대로 수행되었는지 확인하려면 다음 절차를 수행하십시오.  

> [!WARNING]  
>  Configuration Manager 콘솔의 **모니터링** 작업 영역에 있는 **보고** 노드 **보고서** 하위 폴더에 보고서가 표시되면 이 절차를 건너뛰어도 됩니다.  

#### <a name="to-verify-the-reporting-services-point-installation"></a>보고 서비스 지점 설치를 확인하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **시스템 상태**를 확장한 후 **구성 요소 상태**를 클릭합니다.  

3.  구성 요소 목록에서 **SMS_SRS_REPORTING_POINT** 를 클릭합니다.  

4.  **홈** 탭의 **구성 요소** 그룹에서 **메시지 표시**를 클릭한 다음 **모두**를 클릭합니다.  

5.  보고 서비스 지점을 설치하기 전의 기간에 대한 날짜와 시간을 지정하고 **확인**을 클릭합니다.  

6.  보고 서비스 지점이 제대로 설치되었음을 나타내는 상태 메시지 ID 1015가 표시되는지 확인합니다. 또는 &lt;*ConfigMgr 설치 경로*>\Logs에 있는 Srsrp.log 파일을 열고 **설치를 완료했습니다.**를 찾아도 됩니다.  

     Windows 탐색기에서 &lt;*ConfigMgr 설치 경로*>Logs로 이동합니다.  

7.  Srsrp.log를 열고 보고 서비스 지점이 설치된 시점부터 로그 파일의 내용을 차례차례 검토합니다. 보고서 폴더가 만들어졌는지, 보고서가 배포되었는지, 각 폴더의 보안 정책이 확인되었는지 확인합니다. 보안 정책 확인 내용의 마지막 줄 다음에 **SRS 웹 서비스가 서버에서 상태가 성공적으로 체크** 를 찾아 봅니다.  

##  <a name="BKMK_Certificate"></a> Configuration Manager 콘솔 컴퓨터용 자체 서명된 인증서 구성  
 SQL Server Reporting Services 보고서를 제작하는 데 필요한 여러 옵션이 있습니다. Configuration Manager 콘솔에서 보고서를 만들거나 편집할 때 Configuration Manager에서 보고서 작성기가 열려 제작 환경으로 사용됩니다. Configuration Manager 보고서를 작성하는 방법에 관계없이 사이트 데이터베이스 서버에 대한 서버 인증용으로 자체 서명된 인증서가 필요합니다. Configuration Manager에서는 SMS 공급자가 설치된 컴퓨터와 사이트 서버에 인증서를 자동으로 설치합니다. 그러므로 이러한 컴퓨터 중 하나에서 실행할 때 Configuration Manager 콘솔에서 보고서를 만들거나 편집할 수 있습니다. 그러나 다른 컴퓨터에 설치된 Configuration Manager 콘솔에서 보고서를 만들거나 수정할 때는 사이트 서버에서 인증서를 내보낸 다음 Configuration Manager 콘솔을 실행하는 컴퓨터의 **신뢰된 사용자** 인증서 저장소에 추가해야 합니다.  

> [!NOTE]  
>  SQL Server Reporting Services의 다른 보고서 제작 환경에 대한 자세한 내용은 SQL Server 2008 온라인 설명서의 [보고서 제작 환경 비교](http://go.microsoft.com/fwlink/p/?LinkId=242805) 를 참조하십시오.  

 사이트 서버와 Configuration Manager 콘솔을 실행하는 다른 컴퓨터가 모두 Windows Server 2008 R2를 실행하는 경우 사이트 서버에서 다른 컴퓨터로 자체 서명된 인증서의 사본을 전송하는 방법의 예로 다음 절차를 사용합니다. 운영 체제 버전이 달라서 이 절차를 따를 수 없는 경우 사용 중인 운영 체제 설명서에서 해당 절차를 참조하십시오.  

#### <a name="to-transfer-a-copy-of-self-signed-certificate-from-the-site-server-to-another-computer"></a>사이트 서버에서 다른 컴퓨터로 자체 서명된 인증서의 사본을 전송하려면  

1.  자체 서명된 인증서를 내보낼 사이트 서버에서 다음 단계를 수행하십시오.  

    1.  **시작**, **실행**을 차례로 클릭한 다음 **mmc.exe**를 입력합니다. 비어 있는 콘솔에서 **파일**을 클릭한 후 **스냅인 추가/제거**를 클릭합니다.  

    2.  **스냅인 추가/제거** 대화 상자의 **사용 가능한 스냅인** 목록에서 **인증서**를 선택하고 **추가**를 클릭합니다.  

    3.  **인증서 스냅인** 대화 상자에서 **컴퓨터 계정**을 선택한 후에 **다음**을 클릭합니다.  

    4.  **컴퓨터 선택** 대화 상자에서 **로컬 컴퓨터: (이 콘솔이 실행되고 있는 컴퓨터)** 가 선택되어 있는지 확인한 다음 **마침**을 클릭합니다.  

    5.  **스냅인 추가/제거** 대화 상자에서 **확인**을 클릭합니다.  

    6.  콘솔에서 **인증서(로컬 컴퓨터)**를 확장하고 **신뢰할 수 있는 사용자**를 확장한 후 **인증서**를 선택합니다.  

    7.  식별 이름이 &lt;*사이트 서버의 FQDN*>인 인증서를 마우스 오른쪽 단추로 클릭하고 **모든 작업**을 클릭한 후 **내보내기**를 선택합니다.  

    8.  기본 옵션을 사용하여 **인증서 내보내기 마법사** 를 완료하고 **.cer** 파일 이름 확장명으로 인증서를 저장합니다.  

2.  Configuration Manager 콘솔을 실행하는 컴퓨터에서 다음 단계를 수행하여 자체 서명된 인증서를 신뢰할 수 있는 사용자 인증서 저장소에 추가합니다.  

    1.  앞의 1.a - 1.e 단계를 반복하여 관리 지점 컴퓨터의 MMC에서 **인증서** 스냅인을 구성합니다.  

    2.  콘솔에서 **인증서(로컬 컴퓨터)**와 **신뢰할 수 있는 사용자**를 차례로 확장하고 **인증서**를 마우스 오른쪽 단추로 클릭한 다음 **모든 작업**을 선택하고 **가져오기** 를 선택하여 **인증서 가져오기 마법사**를 시작합니다.  

    3.  **가져올 파일** 페이지에서 1.h단계에서 저장한 인증서를 선택한 후 **다음**을 클릭합니다.  

    4.  **인증서 저장소** 페이지에서 **모든 인증서를 다음 저장소에 저장**을 선택하고 **인증서 저장소** 를 **신뢰할 수 있는 사용자**로 설정한 후 **다음**을 클릭합니다.  

    5.  **마침** 을 클릭하여 마법사를 닫고 컴퓨터의 인증서 구성을 완료합니다.  

##  <a name="BKMK_ModifyReportingServicesPoint"></a> 보고 서비스 지점 설정 수정  
 보고 서비스 지점을 설치하면 보고 서비스 지점 속성에서 사이트 데이터베이스 연결 및 인증 설정을 수정할 수 있습니다. 보고 서비스 지점 설정을 수정하려면 다음 절차를 수행하십시오.  

#### <a name="to-modify-reporting-services-point-settings"></a>보고 서비스 지점 설정을 수정하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할** 을 클릭하여 사이트 시스템을 나열합니다.  

    > [!TIP]  
    >  보고 서비스 지점 사이트 역할을 호스팅하는 사이트 시스템만 나열하려면 **서버 및 사이트 시스템 역할** 을 마우스 오른쪽 단추로 클릭하고 **보고 서비스 지점**을 선택합니다.  

3.  설정을 수정할 보고 서비스 지점을 호스팅하는 사이트 시스템을 선택하고 **사이트 시스템 역할** 에서 **보고 서비스 지점**을 선택합니다.  

4.  **사이트 역할** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  **보고 서비스 지점 속성** 대화 상자에서 다음 설정을 수정할 수 있습니다.  

    -   **사이트 데이터베이스 서버 이름**: Configuration Manager 사이트 데이터베이스를 호스트하는 서버의 이름을 지정합니다. 일반적으로 마법사에서 서버의 FQDN(정규화된 도메인 이름)을 자동으로 검색합니다. 데이터베이스 인스턴스를 지정하려면 &lt;*서버 이름*>\&lt;*인스턴스 이름*> 형식을 사용합니다.  

    -   **데이터베이스 이름**: System Center 2012 Configuration Manager 사이트 데이터베이스 이름을 지정하고 **확인**을 클릭하여 마법사에서 해당 사이트 데이터베이스에 액세스할 수 있는지 확인합니다.  

        > [!IMPORTANT]  
        >  보고 서비스 지점을 만드는 사용자 계정에 사이트 데이터베이스에 대한 읽기 권한이 있어야 합니다. 연결 테스트에 실패하면 빨간색 경고 아이콘이 표시됩니다. 이 아이콘 위로 커서를 이동하여 오류에 대한 세부 정보를 읽어 봅니다. 오류를 수정한 후 다시 **테스트** 를 클릭합니다.  

    -   **사용자 계정**: **설정**을 클릭한 다음, 보고 서비스 지점의 SQL Server Reporting Services가 Configuration Manager 사이트 데이터베이스에 연결하여 보고서에 표시된 데이터를 검색할 때 사용되는 계정을 선택합니다. **기존 계정**을 선택하여 기존 Configuration Manager 권한이 있는 Windows 사용자 계정을 지정하거나 **새 계정**을 선택하여 현재 Configuration Manager에서 권한이 없는 Windows 사용자 계정을 지정합니다. Configuration Manager에서는 사이트 데이터베이스에 대해 지정된 사용자 계정 액세스 권한을 자동으로 부여합니다. 이 계정은 **관리** 작업 영역에 있는 **보안** 노드의 **계정** 하위 폴더에 **ConfigMgr SRS 보고 지점** 계정으로 표시됩니다.  

         지정된 Windows 사용자 계정과 암호는 암호화되어 보고 서비스 데이터베이스에 저장됩니다. 보고 서비스는 이 계정과 암호를 사용하여 사이트 데이터베이스에서 보고서에 대한 데이터를 검색합니다.  

        > [!IMPORTANT]  
        >  사이트 데이터베이스가 원격 사이트 시스템에 있는 경우 지정한 계정에 컴퓨터에 대한 **로컬로 로그온** 권한이 있어야 합니다.  

6.  **확인** 을 클릭하여 변경 내용을 저장하고 대화 상자를 닫습니다.  

## <a name="upgrading-sql-server"></a>SQL Server 업그레이드  
 SQL Server와 보고 서비스 지점의 데이터 원본으로 사용되는 SQL Server Reporting Services를 업그레이드하면 Configuration Manager 콘솔에서 보고서를 실행하거나 편집할 때 오류가 나타날 수 있습니다. Configuration Manager 콘솔에서 보고가 제대로 작동하려면 사이트의 보고 서비스 지점 사이트 시스템 역할을 제거하고 다시 설치해야 합니다. 그러나 업그레이드한 후에도 계속 인터넷 브라우저에서 보고서를 실행하고 편집할 수 있습니다.  

##  <a name="BKMK_ConfigureReportOptions"></a> 보고서 옵션 구성  
 Configuration Manager 사이트의 보고서 옵션을 사용하여 보고서를 관리하는 데 사용되는 기본 보고 서비스 지점을 선택합니다. 사이트에 보고 서비스 지점이 둘 이상 있을 수 있지만 보고서 옵션에서 선택한 기본 보고서 서버만 보고서를 관리하는 데 사용됩니다. 사이트에 대한 보고서 옵션을 구성하려면 다음 절차를 수행하십시오.  

#### <a name="to-configure-report-options"></a>보고서 옵션을 구성하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **보고**를 확장한 후 **보고서**를 클릭합니다.  

3.  **홈** 탭의 **설정** 그룹에서 **보고서 옵션**을 클릭합니다.  

4.  목록에서 기본 보고서 서버를 선택한 다음 **확인**을 클릭합니다. 목록에 보고 서비스 지점이 표시되지 않으면 사이트에서 보고 서비스 지점을 제대로 설치하고 구성했는지 확인하십시오.  

## <a name="next-steps"></a>다음 단계
[보고 작업 및 유지 관리](operations-and-maintenance-for-reporting.md)
