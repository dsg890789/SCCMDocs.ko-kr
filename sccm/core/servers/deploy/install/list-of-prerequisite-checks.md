---
title: "필수 구성 요소 확인"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에 사용 가능한 필수 조건 검사를 검토합니다. 보안 권한 검사를 포함합니다."
ms.custom: na
ms.date: 4/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6a279624-ffc9-41aa-8132-df1809708dd5
caps.latest.revision: "12"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b26ec9626924da2a621999b37ee5c1979021bdec
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="list-of-prerequisite-checks-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 필수 조건 검사 목록

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 섹션에서는 사용 가능한 필수 구성 요소 검사에 대해 자세히 설명합니다.

필수 조건 검사기를 사용하는 방법에 대한 자세한 내용은 [필수 조건 검사기](prerequisite-checker.md)를 참조하세요.  

##  <a name="BKMK_Security"></a> 보안 권한의 필수 조건 검사  
다음 표에는 필수 조건 검사기가 보안 권한에 대해 수행하는 검사가 나와 있습니다.

|수행되는 검사|설명|심각도|사이트 적용 가능성|
|---|---|---|---|
|**중앙 관리 사이트에 대한 관리자 권한**|Configuration Manager 설치 프로그램을 실행하는 사용자 계정에 중앙 관리 사이트 컴퓨터에 대한 **관리자** 권한이 있는지 확인합니다. |오류|기본 사이트|
|**확장 기본 사이트에 대한 관리 권한**|설치 프로그램을 실행하는 사용자 계정에 확장할 독립 실행형 기본 사이트에 대한 로컬 **관리자** 권한이 있는지 확인합니다.|오류|중앙 관리 사이트|
|**사이트 시스템에 대한 관리 권한**|Configuration Manager 설치 프로그램을 실행하는 사용자 계정에 사이트 서버 컴퓨터에 대한 **관리자** 권한이 있는지 확인합니다. |오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**확장 기본 사이트에 대한 CAS 컴퓨터 관리 권한**|중앙 관리 사이트의 컴퓨터 계정에 확장할 독립 실행형 기본 사이트에 대한 **관리자** 권한이 있는지 확인합니다.|오류|중앙 관리 사이트|
|**중앙 관리 사이트의 SQL Server에 대한 연결**|기존 계층 구조에 조인할 기본 사이트에서 Configuration Manager 설치 프로그램을 실행하는 사용자 계정에 중앙 관리 사이트의 SQL Server 인스턴스에 대한 **sysadmin** 역할이 있는지 확인합니다.|오류|기본 사이트|
|**사이트 서버 컴퓨터 계정 관리 권한**|사이트 서버 컴퓨터 계정에 SQL Server 및 관리 지점 컴퓨터에 대한 **관리자** 권한이 있는지 확인합니다.|오류|기본 사이트, <br>SQL Server|
|**사이트 시스템에서 SQL Server로의 통신**| Configuration Manager 사이트 데이터베이스를 호스트하는 SQL Server 인스턴스용 SQL Server 서비스를 실행하도록 구성된 계정에 대해 유효한 SPN(서비스 사용자 이름)이 Active Directory Domain Services에 등록되었는지 확인합니다. Kerberos 인증을 지원하려면 올바른 SPN이 Active Directory Domain Services에 등록되어 있어야 합니다.|경고|보조 사이트, <br>관리 지점|
|**SQL Server 보안 모드**|SQL Server에 대해 Windows 인증 보안이 구성되었는지 확인합니다.|경고|SQL Server|
|**SQL Server sysadmin 권한**|Configuration Manager 설치 프로그램을 실행하는 사용자 계정에 사이트 데이터베이스 설치를 위해 선택한 SQL Server 인스턴스에 대한 **sysadmin** 역할이 있는지 확인합니다. 이 내용은 설치 프로그램이 사용 권한을 확인하기 위해 SQL Server의 인스턴스에 액세스할 수 없는 경우에도 확인할 수 없습니다.|오류|SQL Server|
|**참조 사이트에 대한 SQL Server sysadmin 권한**|Configuration Manager 설치 프로그램을 실행하는 사용자 계정에 참조 사이트 데이터베이스로 선택한 SQL Server 역할 인스턴스에 대한 **sysadmin** 역할이 있는지 확인합니다. 사이트 데이터베이스를 수정하려면 SQL Server **sysadmin** 역할 권한이 필요합니다.|오류|SQL Server|

##  <a name="BKMK_Dependencies"></a> Configuration Manager 종속성의 필수 조건 검사
다음 표에는 필수 조건 검사기가 Configuration Manager 종속성에 대해 수행하는 검사가 나와 있습니다.

|수행되는 검사|설명|심각도|사이트 적용 가능성|
|---|---|---|---|
|**대상 기본 사이트에 대한 활성 마이그레이션 매핑**|기본 사이트에 대한 활성 마이그레이션 매핑이 없는지 확인합니다.|오류|중앙 관리 사이트|
|**활성 복제본 MP**|활성 관리 지점 복제본을 확인합니다.|오류|기본 사이트|
|**배포 지점에 대한 관리 권한**|설치 프로그램을 실행하는 사용자 계정에 배포 지점 컴퓨터에 대한 **관리자** 권한이 있는지 확인합니다.|경고|배포 지점|
|**관리 지점에 대한 관리 권한**|사이트 서버의 컴퓨터 계정에 관리 지점 및 배포 지점 컴퓨터에 대한 **관리자** 권한이 있는지 확인합니다.|경고|관리 지점|
|**관리자 공유(사이트 시스템)**|사이트 시스템 컴퓨터에 필요한 관리자 공유가 있는지 확인합니다.|경고|관리 지점|
|**응용 프로그램 호환성**|현재 응용 프로그램이 응용 프로그램 스키마와 호환되는지 확인합니다.|경고|중앙 관리 사이트, <br>기본 사이트|
|**BITS 사용**|관리 지점 사이트 시스템 컴퓨터에 BITS(Background Intelligent Transfer Service)가 설치되었는지 확인합니다. 이 검사가 실패하면 BITS가 설치되지 않았거나, 컴퓨터 또는 원격 IIS 호스트에 IIS 7.0용 IIS(인터넷 정보 서비스) 6.0 WMI(Windows Management Instrumentation) 호환성 구성 요소가 설치되지 않았거나, 사이트 서버 컴퓨터에 IIS 공통 구성 요소가 설치되지 않았기 때문에 설치 프로그램에서 원격 IIS 설정을 확인할 수 없는 것입니다.|오류|관리 지점|
|**BITS 설치됨**|IIS에 BITS가 설치되었는지 확인합니다.|경고|관리 지점|
|**SQL Server에 대한 대/소문자를 구분하지 않는 데이터 정렬**|SQL Server 설치 시 대소문자를 구분하지 않는 정렬(예: SQL_Latin1_General_CP1_CI_AS)을 사용하는지 확인합니다.|오류|SQL Server|
|**기존 독립 실행형 기본 사이트의 버전 및 사이트 코드 확인**|확장할 계획인 기본 사이트가 독립 실행형 기본 사이트인지, 그리고 설치할 중앙 관리 사이트와 Configuration Manager 버전은 같지만 사이트 코드는 다른지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트|
|**호환되지 않는 컬렉션 참조에 대한 확인**|업그레이드하는 동안 이 검사는 컬렉션에서 동일한 유형의 다른 컬렉션만 참조하는지를 확인합니다.|오류|중앙 관리 사이트|  
|**관리 지점 컴퓨터의 클라이언트 버전**|다른 버전의 Configuration Manager 클라이언트가 설치된 컴퓨터에 관리 지점을 설치하는지 확인합니다.|오류|관리 지점|
|**SQL Server 메모리 사용에 대한 구성**|SQL Server가 메모리를 무제한 사용하도록 구성되어 있는지 확인합니다. SQL Server 메모리의 한도를 최대로 구성해야 합니다.|경고|SQL Server|
|**전용 SQL Server 인스턴스**|전용 SQL Server 인스턴스가 Configuration Manager 사이트 데이터베이스를 호스트하도록 구성되었는지 확인합니다. 다른 사이트에서 인스턴스를 사용하는 경우 새 사이트에서 사용할 다른 인스턴스를 선택해야 합니다. 또는 다른 사이트를 제거하거나 해당 데이터베이스를 SQL Server의 다른 인스턴스로 이동할 수 있습니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**서버의 기존 Configuration Manager 서버 구성 요소**|사이트 설치용으로 선택한 컴퓨터에 사이트 서버 또는 사이트 시스템 역할이 아직 설치되지 않았는지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**SQL Server 대한 방화벽 예외**|Windows 방화벽이 사용되지 않거나 SQL Server에 대한 적절한 Windows 방화벽 예외가 있는지 확인합니다. Sqlservr.exe 또는 필수 TCP 포트를 원격으로 액세스하도록 허용해야 합니다. 기본적으로 SQL Server는 TCP 포트 1433에서 수신하고 SQL SSB(Server Service Broker)는 TCP 포트 4022를 사용합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트, <br>관리 지점|
|**SQL Server에 대한 방화벽 예외(독립 실행형 기본 사이트)**|Windows 방화벽이 사용되지 않거나 SQL Server에 대한 적절한 Windows 방화벽 예외가 있는지 확인합니다. Sqlservr.exe 또는 필수 TCP 포트를 원격으로 액세스하도록 허용해야 합니다. 기본적으로 SQL Server는 TCP 포트 1433에서 수신하고 SSB는 TCP 포트 4022를 사용합니다.|경고|기본 사이트(독립 실행형만 해당)|
|**관리 지점의 SQL Server에 대한 방화벽 예외**|Windows 방화벽이 사용되지 않거나 SQL Server에 대한 적절한 Windows 방화벽 예외가 있는지 확인합니다.|경고|관리 지점|
|**IIS HTTPS 구성**|HTTPS 통신 프로토콜에 대한 IIS 웹 사이트 바인딩을 확인합니다. HTTPS가 필요한 사이트 역할을 설치하는 경우 유효한 PKI(공개 키 인프라) 인증서가 있는 지정된 서버에서 IIS 사이트 바인딩을 구성해야 합니다.|경고|관리 지점, <br>배포 지점|
|**IIS 서비스 실행 중**|관리 지점이나 배포 지점을 설치할 컴퓨터에서 IIS를 설치하여 실행 중인지 확인합니다.|오류|관리 지점, <br> 배포 지점|
|**확장 기본 사이트의 데이터 정렬 일치**|확장할 독립 실행형 기본 사이트의 사이트 데이터베이스 정렬이 중앙 관리 사이트의 사이트 데이터베이스 데이터 정렬과 같은지 확인합니다.|오류|중앙 관리 사이트|
|**Microsoft RDC(원격 차등 압축) 라이브러리가 등록됨**|RDC 라이브러리가 Configuration Manager 사이트 서버에 등록되어 있는지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**Microsoft Windows Installer**|Windows Installer 버전을 확인합니다. 확인할 수 없다면 설치 프로그램에서 버전을 확인할 수 없거나 설치된 버전이 Windows Installer 4.5의 최소 요구 사항을 충족하지 않는 것입니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**Microsoft XML Core Services 6.0(MSXML60)**|컴퓨터에 MSXML 6.0 이상이 설치되어 있는지 확인합니다.|경고|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트, <br>Configuration Manager 콘솔, <br>관리 지점, <br>배포 지점|
|**Configuration Manager 콘솔에 대한 최소 .NET Framework 버전**|Configuration Manager 콘솔 컴퓨터에 Microsoft .NET Framework 4.0이 설치되어 있는지 확인합니다. .NET Framework 4.0은 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/p/?LinkId=189149)에서 다운로드할 수 있습니다.|오류|Configuration Manager 콘솔|
|**Configuration Manager 사이트 서버에 대한 최소 .NET Framework 버전**|Configuration Manager 사이트 서버에 .NET Framework 3.5가 설치되어 있는지 확인합니다. Windows Server 2008의 경우 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/p/?LinkId=185604)에서 Microsoft .NET Framework 3.5를 다운로드할 수 있습니다. Windows Server 2008 R2의 경우 .NET Framework 3.5를 Server Manager 내부 기능으로 사용할 수 있습니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**Configuration Manager 보조 사이트용 SQL Server Express Edition 설치를 위한 최소 .NET Framework 버전**|SQL Server Express를 설치하기 위해 .NET Framework 4.0이 Configuration Manager 보조 사이트 컴퓨터에 설치되어 있는지 확인합니다.|오류|보조 사이트|
|**부모/자식 데이터베이스 데이터 정렬**|사이트 데이터베이스의 정렬이 상위 사이트 데이터베이스의 정렬과 일치하는지 확인합니다. 계층의 모든 사이트가 동일한 데이터베이스 정렬을 사용해야 합니다.|오류|기본 사이트, <br>보조 사이트|
|**사이트 서버의 PowerShell 2.0**|Configuration Manager Exchange 커넥터용 사이트 서버에 Windows PowerShell 2.0 이상 버전이 설치되어 있는지 확인합니다. PowerShell 2.0에 대한 자세한 내용은 Microsoft 기술 자료의 [문서 968930](http://go.microsoft.com/fwlink/p/?LinkId=226450) 을 참조하세요.|경고|기본 사이트|
|**기본 FQDN**|FQDN(정규화된 도메인 이름)을 사용하여 컴퓨터의 NetBIOS 이름이 컴퓨터의 로컬 호스트 이름(FQDN의 첫 번째 레이블)과 일치하는지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트, <br>SQL Server|
|**보조 사이트의 WMI에 대한 원격 연결**|설치 프로그램에서 보조 사이트의 WMI에 대한 원격 연결을 설정할 수 있는지 확인합니다.|경고|보조 사이트|
|**필요한 SQL Server 데이터 정렬**|중국어 운영 체제를 사용하며 GB18030 지원이 필요한 경우가 아니라면 SQL Server의 인스턴스와 Configuration Manager 사이트 데이터베이스(설치된 경우)가 SQL_Latin1_General_CP1_CI_AS 데이터 정렬을 사용하도록 구성되었는지 확인합니다.<br><br>SQL Server 인스턴스와 데이터베이스 데이터 정렬을 변경하는 방법에 대한 자세한 내용은 SQL Server 2008 R2 온라인 설명서의 [데이터 정렬 설정 및 변경](http://go.microsoft.com/fwlink/p/?LinkID=234541)을 참조하세요.  GB18030 지원에 대한 자세한 내용은 [System Center Configuration Manager의 다국어 기능 지원](../../../../core/plan-design/hierarchy/international-support.md)을 참조하세요.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**설치 원본 폴더**|보조 사이트의 컴퓨터 계정에 설치 원본 폴더 및 공유에 대한 **읽기** NTFS 파일 시스템 권한 및 **읽기** 공유 권한이 있는지 확인합니다.<br><br>**참고**: 관리 공유(예: C$ 및 D$)를 사용하는 경우 보조 사이트 컴퓨터 계정은 컴퓨터의 **관리자** 사용자여야 합니다.|오류|보조 사이트|
|**설치 프로그램 원본 버전**|보조 사이트 설치를 위해 지정한 원본 폴더의 Configuration Manager 버전이 기본 사이트의 Configuration Manager 버전과 일치하는지 확인합니다.|오류|보조 사이트|
|**사용 중인 사이트 코드**|지정한 사이트 코드가 Configuration Manager 계층 구조에서 아직 사용되지 않는지 확인합니다. 이 사이트의 고유한 사이트 코드를 지정해야 합니다.|오류|기본 사이트|
|**SMS 공급자 컴퓨터의 도메인이 사이트 서버와 동일함**|SMS 공급자의 인스턴스를 실행하는 컴퓨터의 도메인이 사이트 서버와 동일한지 확인합니다.|오류|사이트 데이터베이스|
|**SQL Server Edition**|사이트의 SQL Server 버전이 SQL Server Express가 아닌지 확인합니다.|오류|SQL Server|
|**보조 사이트의 SQL Server Express**|SQL Server Express를 보조 사이트의 사이트 서버 컴퓨터에 설치할 수 있는지 확인합니다.|오류|보조 사이트|
|**보조 사이트 컴퓨터의 SQL Server**|보조 사이트 컴퓨터에 SQL Server가 설치되어 있는지 확인합니다. 원격 사이트 시스템에는 SQL Server를 설치할 수 없습니다.<br><br>**경고**: 이 확인은 설치 프로그램이 SQL Server의 기존 인스턴스를 사용하도록 선택할 경우에만 적용됩니다.|오류|보조 사이트|
|**SQL Server 프로세스 메모리 할당**|SQL Server에서 중앙 관리 사이트 및 기본 사이트를 위해 최소 8GB의 메모리를 예약하고 보조 사이트를 위해 최소 4GB의 메모리를 예약했는지 확인합니다. SQL Server Management Studio를 사용하여 고정된 양의 메모리를 설정하는 방법에 대한 자세한 내용은 [고정된 메모리 양을 설정하는 방법(SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759)을 참조하세요.<br><br>**참고**: 예약된 메모리가 1GB인 보조 사이트의 SQL Server Express에는 이 확인이 적용되지 않습니다.|경고|SQL Server|
|**SQL Server 서비스 실행 계정**|SQL Server 서비스의 로그온 계정이 로컬 사용자 계정 또는 LOCAL SERVICE가 아닌지 확인합니다. 올바른 도메인 계정 NETWORK SERVICE 또는 LOCAL SYSTEM을 사용하도록 SQL Server 서비스를 구성해야 합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**SQL Server TCP 포트**|SQL Server 인스턴스에 TCP가 사용되고 있고 TCP가 정적 포트를 사용하도록 설정되었는지 확인합니다.|오류|SQL Server|
|**SQL Server 버전**|지정된 사이트 데이터베이스 서버에 지원되는 버전의 SQL Server가 설치되어 있는지 확인합니다. 자세한 내용은 [System Center Configuration Manager에 대한 SQL Server 버전 지원](../../../../core/plan-design/configs/support-for-sql-server-versions.md)을 참조하세요.|오류|SQL Server|
|**업그레이드할 수 없는 사이트 시스템의 운영 체제 버전**|업그레이드하는 동안 이 규칙은 배포 지점이 아닌 사이트 시스템 역할이 Windows Server 2008 이전 버전을 실행하는 컴퓨터에 설치되어 있는지 확인합니다.<br><br>**참고**: Configuration Manager에 Intune을 통합할 때 이 검사가 Azure에 설치된 사이트 시스템 역할 또는 Microsoft Intune에서 사용하는 클라우드 저장소의 상태를 확인할 수 없기 때문에 이러한 역할에 대한 경고를 가양성으로 무시할 수 있습니다.|경고|기본 사이트, <br>보조 사이트|
|**확장된 기본 사이트에서 지원되지 않는 사이트 시스템 역할 'Asset Intelligence 동기화 지점'**|확장하는 독립 실행형 기본 사이트에 Asset Intelligence 동기화 지점 사이트 시스템 역할이 설치되지 않았는지 확인합니다.|오류|중앙 관리 사이트|
|**확장된 기본 사이트에서 지원되지 않는 사이트 시스템 역할 'Endpoint Protection 지점'**|확장하는 독립 실행형 기본 사이트에 Endpoint Protection 지점 사이트 시스템 역할이 설치되지 않았는지 확인합니다.|오류|중앙 관리 사이트|
|**확장된 기본 사이트에서 지원되지 않는 사이트 시스템 역할 'Microsoft Intune 커넥터'**|확장하는 독립 실행형 기본 사이트에 Microsoft Intune 커넥터 사이트 시스템 역할이 설치되지 않았는지 확인합니다.|오류|중앙 관리 사이트|
|**USMT(사용자 환경 마이그레이션 도구) 설치됨**|Windows 8.1용 Windows ADK(평가 및 배포 키트)의 USMT(사용자 환경 마이그레이션 도구) 구성 요소가 설치되어 있는지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트(독립 실행형만 해당)|  
|**SQL Server 컴퓨터의 FQDN 확인**|SQL Server 컴퓨터에 대해 지정한 FQDN이 올바른지 확인합니다.|오류|SQL Server|
|**중앙 관리 사이트 버전 확인**|중앙 관리 사이트에 동일한 버전의 Configuration Manager가 있는지 확인합니다.|오류|기본 사이트|
|**Active Directory에 게시할 수 있는 사이트 서버 권한 확인**|사이트 서버의 컴퓨터 계정에 Active Directory 도메인의 **시스템 관리** 컨테이너에 대한 **모든 권한** 이 있는지 확인합니다. 필요한 권한을 구성하는 옵션에 대한 자세한 내용은 [사이트 게시를 위해 Active Directory 준비](../../../../core/plan-design/network/extend-the-active-directory-schema.md)를 참조하세요.<br><br>**참고**: 수동으로 사용 권한을 확인한 경우 이 경고를 무시해도 됩니다.|경고|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**Windows 배포 도구 설치됨**|Windows 10용 Windows ADK의 Windows 배포 도구 구성 요소가 설치되어 있는지 확인합니다.|오류|사이트 데이터베이스|
|**Windows 장애 조치(failover) 클러스터**|관리 지점 또는 배포 지점이 있는 컴퓨터가 Windows 클러스터의 일부가 아닌지 확인합니다.|오류|관리 지점<br>배포 지점|
|**Windows 사전 설치 환경 설치됨**|Windows 10용 Windows ADK의 Windows 사전 설치 환경 구성 요소가 설치되어 있는지 확인합니다.|오류|사이트 데이터베이스|
|**WinRM(Windows Remote Management) v1.1**|대역 외 관리 콘솔을 실행할 기본 사이트 서버 또는 Configuration Manager 콘솔 컴퓨터에 WinRM 1.1이 설치되어 있는지 확인합니다. WinRM 1.1을 다운로드하는 방법에 대한 자세한 내용은 Microsoft 기술 자료에서 [문서 936059](https://support.microsoft.com/en-us/kb/936059) 를 참조하세요.|경고|기본 사이트, <br>Configuration Manager 콘솔|
|**사이트 서버의 WSUS**|사이트 서버에 WSUS(Windows Server Update Services) 3.0 SP2(서비스 팩 2)가 설치되어 있는지 확인합니다. 사이트 서버가 아닌 컴퓨터의 소프트웨어 업데이트 지점을 사용할 경우 사이트 서버에 WSUS 관리 콘솔을 설치해야 합니다. WSUS에 대한 자세한 내용은 [Windows Server Update Services](http://go.microsoft.com/fwlink/p/?LinkID=79477)를 참조하세요.|경고|중앙 관리 사이트, <br>기본 사이트|  

##  <a name="BKMK_Requirements"></a> 시스템 요구 사항의 필수 조건 검사  
다음 표에는 필수 조건 검사가 시스템 요구 사항에 대해 수행하는 필수 조건 검사 목록이 나와 있습니다.  

|수행되는 검사|설명|심각도|사이트 적용 가능성|
|---|---|---|---|
|**Active Directory 도메인 기능 수준 확인**|Active Directory 도메인 기능 수준이 최소 수준인 Windows Server 2008 R2인지 확인합니다.|경고|중앙 관리 사이트, <br>기본 사이트|
|**서버 서비스가 실행 중인지 확인**|서버 서비스가 시작되었는지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|  
|**도메인 멤버 자격**|Configuration Manager에서 컴퓨터가 Windows 도메인의 구성원인지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트, <br>SMS 공급자, <br>SQL Server|
|**도메인 멤버 자격**|Configuration Manager에서 컴퓨터가 Windows 도메인의 구성원인지 확인합니다.|경고|관리 지점, <br>배포 지점|
|**사이트 서버의 FAT 드라이브**|디스크 드라이브가 FAT 파일 시스템으로 포맷되었는지 확인합니다. 보안 수준을 높이려면 NTFS 파일 시스템으로 포맷된 디스크 드라이브에 사이트 서버 구성 요소를 설치합니다.|경고|기본 사이트|
|**사이트 서버의 사용 가능한 디스크 공간**|사이트 서버를 설치하려면 사이트 서버 컴퓨터에서 사용 가능한 디스크 공간이 15GB 이상이어야 합니다. 같은 컴퓨터에 SMS 공급자 사이트 시스템 역할을 설치할 경우 추가로 사용 가능한 디스크 공간이 1GB 있어야 합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**시스템 다시 시작 보류 중**|설치 프로그램을 실행하기 전에 다른 프로그램을 위해 서버를 다시 시작해야 하는지 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트, <br>Configuration Manager 콘솔, <br>SMS 공급자, <br>SQL Server, <br>관리 지점, <br>배포 지점|
|**읽기 전용 도메인 컨트롤러**|RODC(읽기 전용 도메인 컨트롤러)에서는 사이트 데이터베이스 서버 및 보조 사이트 서버가 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료의 [도메인 컨트롤러에 SQL Server 설치할 때 발생하는 문제](http://go.microsoft.com/fwlink/p/?LinkId=264856)를 참조하세요.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**스키마 확장**|Active Directory 도메인 서비스 스키마가 확장되었는지 여부 및 확장된 경우 사용된 스키마 확장의 버전은 무엇인지 확인합니다. 사이트 서버를 설치하기 위해 Configuration Manager Active Directory 스키마 확장이 필요하지는 않지만 모든 Configuration Manager 기능을 완전히 활용하려면 스키마를 확장하는 것이 좋습니다. 스키마 확장의 이점에 대한 자세한 내용은 [사이트 게시를 위해 Active Directory 준비](../../../../core/plan-design/network/extend-the-active-directory-schema.md)를 참조하세요.|경고|중앙 관리 사이트, <br>기본 사이트|
|**사이트 서버 FQDN 길이**|사이트 서버 컴퓨터의 FQDN 길이를 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트|
|**지원되지 않는 Configuration Manager 콘솔 운영 체제**|지원되는 운영 체제 버전을 실행하는 컴퓨터에 Configuration Manager 콘솔을 설치할 수 있는지 확인합니다. 자세한 내용은 [System Center Configuration Manager 콘솔에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-consoles)를 참조하세요.|오류|Configuration Manager 콘솔|
|**설치 프로그램에서 지원되지 않는 사이트 서버 운영 체제 버전**|서버에서 지원되지 않는 운영 체제를 실행하고 있는지 확인합니다. 자세한 내용은 [System Center Configuration Manager 사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)를 참조하세요.|오류|중앙 관리 사이트, <br>기본 사이트, <br>보조 사이트, <br>Configuration Manager 콘솔, <br>관리 지점, <br>배포 지점|
|**데이터베이스 일관성 확인**|버전 1602부터 이 검사는 데이터베이스 일관성을 확인합니다.|오류|중앙 관리 사이트, <br>기본 사이트|  
