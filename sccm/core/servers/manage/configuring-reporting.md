---
title: 보고 구성
titleSuffix: Configuration Manager
description: SQL Server Reporting Services에 대한 정보를 포함하여 Configuration Manager 계층 구조에서 보고를 설정하는 방법.
ms.date: 08/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc84435b36fe413f9eab81ebdc0161b7cd64ab53
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "69999366"
---
# <a name="configure-reporting-in-configuration-manager"></a>Configuration Manager에서 보고 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 콘솔에서 보고서를 만들고 수정하고 실행하려면 먼저 완료해야 할 여러 가지 구성 작업이 있습니다. 이 문서를 통해 Configuration Manager 계층 구조에서 보고를 구성하는 데 도움을 얻을 수 있습니다.  

계층 구조에서 SQL Service Reporting Services를 설치하고 구성하기 전에 먼저 다음 Configuration Manager 보고 문서를 검토하세요.  

- [Configuration Manager의 보고 기능 소개](/sccm/core/servers/manage/introduction-to-reporting)  

- [Configuration Manager의 보고 계획](/sccm/core/servers/manage/planning-for-reporting)  

## <a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services

SQL Server Reporting Services는 서버 기반의 보고 플랫폼으로서 다양한 데이터 원본에 대한 포괄적인 보고 기능을 제공합니다. Configuration Manager의 보고 서비스 지점은 SQL Server Reporting Services와 통신하여 다음을 수행합니다.

- 지정한 보고서 폴더에 Configuration Manager 보고서 복사
- Reporting Services 설정 구성
- Reporting Services 보안 설정 구성

보고서를 실행하면 Reporting Services 구성 요소가 Configuration Manager 사이트 데이터베이스에 연결하여 데이터를 검색합니다.  

Configuration Manager 사이트에 보고 서비스 지점을 설치하려면 먼저 대상 사이트 시스템에서 SQL Server Reporting Services를 설치하고 구성해야 합니다. 자세한 내용은 [SQL Server Reporting Services 설치](https://docs.microsoft.com/sql/reporting-services/install-windows/install-reporting-services)를 참조하세요.  

SQL Server Reporting Services가 설치되어 제대로 실행되는지 확인하려면 다음 절차를 따르십시오.  

1. 사이트 시스템에서 **시작** 메뉴로 이동하고 **Reporting Services 구성 관리자**를 엽니다. **Microsoft SQL Server** 그룹의 **구성 도구** 섹션에서 찾을 수 있습니다.

2. **Reporting Services 구성 연결** 창에서 SQL Server Reporting Services를 호스트하는 서버의 이름을 입력합니다. SQL Reporting Services를 설치한 SQL Server의 인스턴스를 선택합니다. 그런 다음 **연결**을 선택해 Reporting Services 구성 관리자를 엽니다.  

3. **보고서 서버 상태** 페이지에서 **보고서 서비스 상태**가 **시작됨**인지 확인합니다. 이 상태가 아닌 경우 **시작**을 선택합니다.  

4. **웹 서비스 URL** 페이지의 **보고서 서비스 웹 서비스 URL**에서 URL을 선택합니다. 이 작업은 보고서 폴더에 대한 연결을 테스트합니다. 브라우저에서 자격 증명을 묻는 메시지를 표시할 수 있습니다. 웹 페이지가 성공적으로 열리는지 확인합니다.

5. **데이터베이스** 페이지에서 **보고서 서버 모드**가 **네이티브**로 설정되어 있는지 확인합니다.  

6. **보고서 관리자 URL** 페이지의 **보고서 관리자 사이트 ID**에서 URL을 선택합니다. 이 작업은 보고서 관리자의 가상 디렉터리에 대한 연결을 테스트합니다. 브라우저에서 자격 증명을 묻는 메시지를 표시할 수 있습니다. 웹 페이지가 성공적으로 열리는지 확인합니다.

    > [!NOTE]  
    > Configuration Manager에서의 보고에는 Reporting Services 보고서 관리자가 필요하지 않습니다. Reporting Services 보고서 관리자는 브라우저에서 보고서를 실행하거나 보고서 관리자를 사용하여 보고서를 관리하려는 경우에만 필요합니다.  

7. **끝내기**를 선택하여 Reporting Services 구성 관리자를 닫습니다.  

## <a name="BKMK_ReportBuilder3"></a> 보고서 작성기 3.0을 사용하도록 보고 구성

1. Configuration Manager 콘솔을 실행하는 컴퓨터에서 Windows 레지스트리 편집기를 엽니다.  

2. **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**으로 이동합니다.  

3. **ReportBuilderApplicationManifestName** 키를 열어 값 데이터를 편집합니다.  

4. **ReportBuilder_2_0_0_0.application**을 **ReportBuilder_3_0_0_0.application**으로 변경한 다음 **확인**을 선택합니다.  

5. Windows 레지스트리 편집기를 닫습니다.  

## <a name="BKMK_InstallReportingServicesPoint"></a> 보고 서비스 지점 설치

사이트에서 보고서를 관리하려면 보고 서비스 지점을 설치합니다. 보고 서비스 지점은 다음을 수행합니다.

- 보고서 폴더와 보고서를 SQL Server Reporting Services에 복사
- 보고서 및 폴더에 대한 보안 정책 적용
- Reporting Services에서 구성 설정을 설정

### <a name="a-namebkmk_requirements--requirements-and-limitations"></a><a name="bkmk_requirements" /> 요구 사항 및 제한 사항

Configuration Manager 콘솔에서 보고서를 보거나 관리하려면 먼저 보고 서비스 지점이 필요합니다. Microsoft SQL Server Reporting Services를 사용하여 서버에서 이 사이트 시스템 역할을 구성합니다. 자세한 내용은 [보고 필수 구성 요소](/sccm/core/servers/manage/prerequisites-for-reporting)를 참조하세요.  

- 보고 서비스 지점을 설치할 사이트를 선택할 때 보고서에 액세스할 사용자는 역할이 설치되는 사이트와 동일한 보안 범위에 있어야 합니다.  

- 사이트 시스템에 보고 서비스 지점을 설치한 후에는 보고서 서버의 URL을 변경하지 마세요.

    예를 들어 보고 서비스 지점을 만든 다음 Reporting Services 구성 관리자에서 보고서 서버의 URL을 수정합니다. Configuration Manager 콘솔은 이전 URL을 계속 사용합니다. 콘솔에서는 보고서를 실행하거나 편집하거나 만들 수 없습니다.

    보고서 서버 URL을 변경해야 하는 경우 먼저 기존 보고 서비스 지점을 제거하세요. URL을 변경한 다음 보고 서비스 지점을 다시 설치합니다.  

- 보고 서비스 지점을 설치할 때 [보고 서비스 지점 계정](/sccm/core/plan-design/hierarchy/accounts#reporting-services-point-account)을 지정합니다. 다른 도메인의 사용자가 보고서를 실행하려면 도메인 간에 양방향 트러스트를 만듭니다. 그렇지 않으면 보고서가 실행되지 않습니다.

### <a name="a-namebkmk_install--install-the-reporting-services-point-on-a-site-system"></a><a name="bkmk_install" /> 사이트 시스템에 보고 서비스 지점 설치  

사이트 시스템 구성에 대한 자세한 내용은 [사이트 시스템 역할 설치](/sccm/core/servers/deploy/configure/install-site-system-roles)를 참조하세요.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 펼친 다음 **서버 및 사이트 시스템 역할** 노드를 선택합니다.  

1. 새 사이트 시스템 서버 또는 기존 사이트 시스템 서버에 보고 서비스 지점을 추가합니다.  

    - *새 사이트 시스템*: 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 선택합니다. **사이트 시스템 서버 만들기 마법사** 가 열립니다.  

    - *기존 사이트 시스템*: 대상 서버를 선택합니다. 리본의 **홈** 탭에 있는 **서버** 그룹에서 **사이트 시스템 역할 추가**를 선택합니다. **사이트 시스템 역할 추가 마법사** 가 열립니다.  

1. **일반** 페이지에서 사이트 시스템 서버에 대한 일반 설정을 지정합니다. 기존 서버에 보고 서비스 지점을 추가할 때는 이전에 구성한 값을 확인합니다.  

1. **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **보고 서비스 지점**을 선택하고 **다음**을 선택합니다.  

1. **보고 서비스 지점** 페이지에서 다음 설정을 구성합니다.  

    - **사이트 데이터베이스 서버 이름**: Configuration Manager 사이트 데이터베이스를 호스트하는 서버의 이름을 지정합니다. 마법사는 일반적으로 서버의 FQDN(정규화된 도메인 이름)을 자동으로 검색합니다. 데이터베이스 인스턴스를 지정하려면 &lt;*서버 이름*>\&lt;*인스턴스 이름*> 형식을 사용합니다. 예: `sqlserver\named1`

    - **데이터베이스 이름**: Configuration Manager 사이트 데이터베이스 이름을 지정합니다. **확인**을 선택하여 마법사가 사이트 데이터베이스에 액세스할 수 있다고 확인합니다.  

        > [!IMPORTANT]  
        > 보고 서비스 지점을 만드는 데 사용하는 사용자 계정은 사이트 데이터베이스에 대한 **읽기** 액세스 권한이 있어야 합니다. 연결 테스트에 실패하면 빨간색 경고 아이콘이 표시됩니다. 아이콘을 가리키면 표시되는 상황별 텍스트에서 오류에 대한 세부 정보를 확인할 수 있습니다. 오류를 수정한 후 다시 **테스트**를 클릭합니다.  

    - **폴더 이름**: Reporting Services에서 만들어 Configuration Manager 보고서에 사용할 폴더 이름을 지정합니다.  

    - **Reporting Services 서버 인스턴스**: Reporting Services의 SQL Server 인스턴스를 선택합니다. 이 페이지에 인스턴스가 나열되지 않으면 SQL Server Reporting Services가 설치, 구성, 시작되었는지 확인합니다.  

        > [!IMPORTANT]  
        > Configuration Manager는 선택한 사이트 시스템의 WMI에 대한 현재 사용자의 컨텍스트에서 연결을 만듭니다. Configuration Manager는 이 연결을 사용하여 Reporting Services의 SQL Server 인스턴스를 검색합니다. 현재 사용자에게 사이트 시스템의 WMI에 대한 **읽기** 액세스 권한이 있어야 하며, 그렇지 않으면 마법사가 Reporting Services 인스턴스를 검색할 수 없습니다.  

    - **보고 서비스 지점 계정**: **설정**을 선택한 다음 사용할 계정을 선택합니다. 보고 서비스 지점의 SQL Server Reporting Services는 이 계정을 사용하여 Configuration Manager 사이트 데이터베이스에 연결합니다. 이 연결은 보고서의 데이터를 검색하기 위한 것입니다. 이전에 Configuration Manager 계정으로 구성한 Windows 사용자 계정을 지정하려면 **기존 계정**을 선택합니다. 현재 사용하도록 구성되지 않은 Windows 사용자 계정을 지정하려면 **새 계정**을 선택합니다. Configuration Manager에서는 사이트 데이터베이스에 대해 지정된 사용자 액세스 권한을 자동으로 부여합니다.  

        Reporting Services를 실행하는 계정은 도메인 로컬 보안 그룹인 **Windows Authorization Access Group**에 속해야 합니다. 또한 **Read tokenGroupsGlobalAndUniversal** 권한이 **허용**으로 설정되어야 합니다. 보고서를 성공적으로 실행하려면 보고 서비스 지점 계정과는 다른 도메인의 사용자에게 도메인 간 양방향 트러스트가 필요합니다.

        지정된 Windows 사용자 계정과 암호는 암호화되어 보고 서비스 데이터베이스에 저장됩니다. 보고 서비스는 이 계정과 암호를 사용하여 사이트 데이터베이스에서 보고서에 대한 데이터를 검색합니다.  

        > [!IMPORTANT]  
        > 지정하는 계정은 Reporting Services 데이터베이스를 호스트하는 서버에서 **로컬로 로그온** 권한을 가져야 합니다.  

1. 마법사를 완료합니다.

마법사가 완료된 후 Configuration Manager는 Reporting Services에 보고서 폴더를 만듭니다. 그런 다음 지정된 보고서 폴더에 보고서를 복사합니다.  

> [!TIP]  
> 보고 서비스 지점 사이트 역할을 호스트하는 사이트 시스템만 나열하려면 **서버 및 사이트 시스템 역할**을 마우스 오른쪽 단추로 클릭하고 **보고 서비스 지점**을 선택합니다.  

### <a name="a-namebkmk_languages--languages-for-reports"></a><a name="bkmk_languages" /> 보고서 언어

<!-- SCCMDocs#1067 -->

Configuration Manager는 보고서 폴더를 만들고 보고서를 보고서 서버에 복사할 때 개체에 적절한 언어를 결정합니다.

- 보고서 폴더 만들기, 보고서 복사

  - 사이트 서버 OS의 로캘을 사용하여 개체 만들기

  - 특정 언어 팩을 사용할 수 없는 경우 기본값은 영어(ENU)로 설정

- 웹 브라우저에서 보고서 보기

  - 폴더 및 보고서 이름: 사이트 서버와 동일한 로캘
  
  - 보고서 콘텐츠: 브라우저 로캘에 따라 동적으로 설정

- Configuration Manager 콘솔에서 보고서 보기

  - 폴더 및 보고서 이름: 콘솔의 로캘에 따라 동적으로 설정
  
  - 보고서 콘텐츠: 콘솔의 로캘에 따라 동적으로 설정

언어 팩 없이 사이트에 보고 서비스 지점을 설치할 경우 보고서가 영어로 설치됩니다. 보고 서비스 지점을 설치한 후에 언어 팩을 설치하는 경우 보고 서비스 지점을 제거한 후에 다시 설치해야만 해당 언어 팩 언어로 보고서를 사용할 수 있습니다.  

자세한 내용은 [언어 팩](/sccm/core/servers/deploy/install/language-packs)을 참조하세요.

### <a name="BKMK_FileInstallationAndSecurity"></a> 파일 설치 및 보고서 폴더 보안 권한

Configuration Manager는 보고 서비스 지점을 설치하고 Reporting Services를 구성하기 위해 다음과 같은 작업을 수행합니다.  

> [!IMPORTANT]  
> 사이트는 SMS_Executive 서비스에 대해 구성된 계정의 컨텍스트에서 이러한 작업을 수행합니다. 일반적으로 이 계정은 사이트 서버 로컬 시스템 계정입니다.  

- 보고 서비스 지점 사이트 역할을 설치합니다.  

- 마법사에서 지정한 저장된 자격 증명을 사용하여 Reporting Services에 데이터 원본을 만듭니다. 이 계정은 보고서를 실행할 때 Reportins Services가 사이트 데이터베이스에 연결하는 데 사용하는 Windows 사용자 계정과 암호입니다.  

- Reporting Services에서 Configuration Manager 루트 폴더를 만듭니다.  

- Reporting Services에서 **ConfigMgr 보고서 사용자** 및 **ConfigMgr 보고서 관리자** 보안 역할을 추가합니다.  

- 하위 폴더를 만든 다음 사이트 서버의 `%ProgramFiles%\SMS_SRSRP`에서 Configuration Manager 보고서를 Reporting Services에 배포합니다.  

- **사이트 읽기** 권한이 있는 Configuration Manager의 모든 사용자 계정의 루트 폴더에 Reporting Services의 **ConfigMgr 보고서 사용자** 역할을 추가합니다.  

- **사이트 수정** 권한이 있는 Configuration Manager의 모든 사용자 계정의 루트 폴더에 Reporting Services의 **ConfigMgr 보고서 관리자** 역할을 추가합니다.  

- 보고서 폴더와 Configuration Manager 보안 개체 유형 간의 매핑을 검색합니다. Configuration Manager는 사이트 데이터베이스에서 이 맵을 유지 관리합니다.  

- Reporting Services의 특정 보고서 폴더에 대한 Configuration Manager 관리자의 다음 권한을 구성합니다.  

  - 사용자를 추가하고 Configuration Manager 개체에 대한 **보고서 실행** 권한이 있는 관리자의 연결된 보고서 폴더에 **ConfigMgr 보고서 사용자** 역할을 할당합니다.  

  - 사용자를 추가하고 Configuration Manager 개체에 대한 **보고서 수정** 권한이 있는 관리자의 연결된 보고서 폴더에 **ConfigMgr 보고서 관리자** 역할을 할당합니다.  

Configuration Manager에서 Reporting Services에 연결하고 Configuration Manager 및 Reporting Services 루트 폴더와 특정 보고서 폴더의 사용자에 대한 권한을 설정합니다. 보고 서비스 지점을 처음 설치하면 Configuration Manager에서 10분마다 Reporting Services에 연결하여 보고서 폴더에서 구성된 사용자 권한이 Configuration Manager 사용자에 대해 설정된 연결된 권한인지 확인합니다. Reporting Services 보고서 관리자를 사용하여 보고서 폴더에서 사용자를 추가하거나 사용자 권한을 수정하면 Configuration Manager에서 사이트 데이터베이스에 저장된 역할 기반 할당을 사용하여 해당 변경 내용을 덮어씁니다. 또한 Configuration Manager는 Configuration Manager에서 보고 권한이 없는 사용자를 제거합니다.  

### <a name="BKMK_SecurityRoles"></a> Reporting Services 보안 역할

Configuration Manager는 보고 서비스 지점을 설치할 때 Reporting Services에 다음 보안 역할을 추가합니다.  

- **ConfigMgr 보고서 사용자**: 이 보안 역할이 할당된 사용자만 Configuration Manager 보고서를 실행할 수 있습니다.  

- **ConfigMgr 보고서 관리자**: 이 보안 역할이 할당된 사용자는 Configuration Manager에서 보고와 관련된 모든 작업을 수행할 수 있습니다.  

## <a name="BKMK_VerifyReportingServicesPointInstallation"></a> 설치 확인

특정 상태 메시지와 로그 파일 항목을 살펴보아 보고 서비스 지점의 설치를 확인합니다. 보고 서비스 지점 설치가 제대로 수행되었는지 확인하려면 다음 절차를 수행하십시오.  

> [!Note]  
> Configuration Manager 콘솔의 **모니터링** 작업 영역에 있는 **보고** 노드의 **보고서** 하위 폴더에 보고서가 표시되면 이 절차를 건너뛰어도 됩니다.

### <a name="verify-installation-by-status-message"></a>상태 메시지로 설치 확인

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고, **시스템 상태**를 확장하고, **구성 요소 상태** 노드를 선택합니다.  

1. **SMS_SRS_REPORTING_POINT** 구성 요소를 선택합니다.  

1. 리본의 **홈** 탭에 있는 **구성 요소** 그룹에서 **메시지 표시**를 선택한 다음 **모두**를 선택합니다.  

1. 보고 서비스 지점을 설치하기 전 기간의 날짜와 시간을 지정한 다음 **확인**을 선택합니다.  

1. 상태 메시지 ID **1015**를 확인합니다. 이 상태 메시지는 보고 서비스 지점이 성공적으로 설치되었음을 나타냅니다.

### <a name="verify-installation-by-log-file"></a>로그 파일로 설치 확인

Configuration Manager 설치 경로의 **Logs** 디렉터리에 있는 **Srsrp.log** 파일을 엽니다. `Installation was successful` 문자열을 찾습니다.

보고 서비스 지점이 성공적으로 설치된 시점부터 이 로그 파일을 단계별로 실행합니다. 보고서 폴더가 만들어졌는지, 보고서가 배포되었는지, 각 폴더의 보안 정책이 확인되었는지 확인합니다. 보안 정책의 마지막 줄을 확인한 후 `Successfully checked that the SRS web service is healthy on server` 문자열을 찾습니다.  

## <a name="BKMK_Certificate"></a> 보고서를 제작하도록 인증서 구성

SQL Server Reporting Services에는 보고서를 제작할 수 있는 여러 옵션이 있습니다. Configuration Manager 콘솔에서 보고서를 만들거나 편집할 때 Configuration Manager에서 보고서 작성기가 열려 제작 환경으로 사용됩니다. Configuration Manager 보고서를 제작하는 방법에 관계없이 사이트 데이터베이스 서버에 대한 서버 인증용으로 자체 서명된 인증서가 필요합니다.

> [!NOTE]  
> SQL Server Reporting Services를 사용하여 보고서를 제작하는 방법에 대한 자세한 내용은 [보고서 작성기 제작 환경](https://docs.microsoft.com/sql/reporting-services/tools/report-builder-authoring-environment-ssrs)을 참조하세요.  

Configuration Manager는 자동으로 사이트 서버에 인증서를 설치하고 모든 SMS 공급자 역할을 설치합니다. 이러한 서버 중 하나에서 Configuration Manager를 실행할 때 Configuration Manager 콘솔에서 보고서를 만들거나 편집할 수 있습니다.

다른 컴퓨터의 Configuration Manager 콘솔에서 보고서를 만들거나 수정할 때는 사이트 서버에서 인증서를 내보냅니다. 특정 인증서의 식별 이름은 로컬 컴퓨터의 **신뢰할 수 있는 사용자** 인증서 저장소에 있는 사이트 서버의 FQDN입니다. Configuration Manager 콘솔을 실행하는 컴퓨터에서 이 인증서를 **신뢰할 수 있는 사용자** 인증서 저장소에 추가합니다.  

## <a name="BKMK_ModifyReportingServicesPoint"></a> 보고 서비스 지점 설정 수정

이 역할을 설치한 후 보고 서비스 지점 속성에서 사이트 데이터베이스 연결과 인증 설정을 수정할 수 있습니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장한 다음 **서버 및 사이트 시스템 역할** 노드를 선택합니다.  

    > [!TIP]  
    > 보고 서비스 지점을 호스트하는 사이트 시스템만 나열하려면 **서버 및 사이트 시스템 역할** 노드를 마우스 오른쪽 단추로 클릭하고 **보고 서비스 지점**을 선택합니다.  

1. 보고 서비스 지점을 호스트하는 사이트 시스템을 선택합니다. 그런 다음 세부 정보 창에서 **보고 서비스 지점** 사이트 시스템 역할을 선택합니다.

1. 리본의 **사이트 역할** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

1. **보고 서비스 지점 속성**에서 다음 설정을 수정할 수 있습니다.  

    - **사이트 데이터베이스 서버 이름**

    - **데이터베이스 이름**

    - **사용자 계정**

1. **확인**을 선택하여 변경 내용을 저장하고 속성을 닫습니다.  

이러한 설정에 대한 자세한 내용은 섹션의 설명서를 참조하여 [사이트 시스템에 보고 서비스 지점을 설치](#bkmk_install)합니다.

## <a name="a-namebkmk_upgradesql--upgrade-sql-server"></a><a name="bkmk_upgradesql" /> SQL Server 업그레이드

SQL Server와 SQL Server Reporting Services를 업그레이드하려면 먼저 사이트에서 보고 서비스 지점을 제거합니다. SQL Server를 업그레이드한 다음 Configuration Manager에서 보고 서비스 지점을 다시 설치합니다.

이 프로세스를 따르지 않으면 Configuration Manager 콘솔에서 보고서를 실행하거나 편집할 때 오류가 표시됩니다. 웹 브라우저에서 보고서를 계속 실행하고 편집할 수 있습니다.  

## <a name="BKMK_ConfigureReportOptions"></a> 보고서 옵션 구성

보고서 관리에 사용하는 기본 보고 서비스 지점을 선택할 수 있습니다. 사이트에는 둘 이상의 보고 서비스 지점이 있을 수 있지만 사이트는 기본 서버만 사용하여 보고서를 관리합니다. 사이트에 대한 보고서 옵션을 구성하려면 다음 절차를 수행하십시오.  

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하여 **보고**를 펼친 다음 **보고서** 노드를 선택합니다.  

1. 리본의 **홈** 탭에 있는 **설정** 그룹에서 **보고서 옵션**을 선택합니다.  

1. 목록에서 기본 보고서 서버를 선택한 다음 **확인**을 선택합니다.

서버가 표시되지 않으면 사이트에 보고 서비스 지점을 설치하고 구성했는지 확인합니다. 자세한 내용은 [설치 확인](#BKMK_VerifyReportingServicesPointInstallation)을 참조하세요.

컴퓨터가 실행하는 SQL Server 보고서 작성기 버전은 보고서 서버에 사용하는 SQL Server 버전과 일치해야 합니다. 그렇지 않으면 오류가 표시되고, 기본 보고서 서버가 저장을 하지 않으며, 보고서를 만들거나 편집할 수 없습니다.<!-- SCCMDocs#791 -->

## <a name="next-steps"></a>다음 단계

[보고 작업 및 유지 관리](/sccm/core/servers/manage/operations-and-maintenance-for-reporting)
