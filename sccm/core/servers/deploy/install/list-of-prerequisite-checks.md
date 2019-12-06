---
title: 필수 구성 요소 확인
titleSuffix: Configuration Manager
description: 특정 필수 구성 요소의 참조는 Configuration Manager 업데이트를 검사합니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6a279624-ffc9-41aa-8132-df1809708dd5
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5b2904f7cd6945b6aa447f0404bf67a4caf4279
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810802"
---
# <a name="list-of-prerequisite-checks-for-configuration-manager"></a>Configuration Manager의 필수 구성 요소 검사 목록

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager를 설치하거나 업데이트할 때 실행되는 필수 구성 요소 검사에 대해 자세히 설명합니다. 자세한 내용은 [필수 구성 요소 검사기](/sccm/core/servers/deploy/install/prerequisite-checker)를 참조하세요.  



## <a name="errors"></a>오류

### <a name="active-migration-mappings-on-the-target-primary-site"></a>대상 기본 사이트에 대한 활성 마이그레이션 매핑

*적용 대상: 중앙 관리 사이트*

주 사이트에 대한 활성 마이그레이션 매핑이 없습니다.

### <a name="active-replica-mp"></a>활성 복제본 MP

*적용 대상: 주 사이트*

활성 관리 지점 복제본이 있습니다.

### <a name="administrative-rights-on-expand-primary-site"></a>확장 기본 사이트에 대한 관리 권한

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 설치 프로그램을 실행하는 사용자 계정에는 독립 실행형 주 사이트 서버에 대한 **관리자** 권한이 있습니다.

### <a name="administrative-rights-on-site-system"></a>사이트 시스템에 대한 관리 권한

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

Configuration Manager 설치 프로그램을 실행하는 사용자 계정에는 사이트 서버에 대한 **관리자** 권한이 있습니다.

### <a name="administrator-rights-on-central-administration-site"></a>중앙 관리 사이트에 대한 관리자 권한

*적용 대상: 주 사이트*

Configuration Manager 설치 프로그램을 실행하는 사용자 계정에는 중앙 관리 사이트 서버에 대한 **관리자** 권한이 있습니다.

### <a name="asset-intelligence-synchronization-point-on-the-expanded-primary-site"></a>확장된 주 사이트의 Asset Intelligence 동기화 지점

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 Asset Intelligence 동기화 지점 역할이 독립 실행형 주 사이트에 설치되지 않습니다.

### <a name="bits-enabled"></a>BITS 사용

*적용 대상: 관리 지점*

BITS(Background Intelligent Transfer Service)가 관리 지점에 설치됩니다. 이 검사가 실패할 수 있는 이유 중 하나는 다음과 같습니다.

- BITS가 설치되어 있지 않습니다.  

- IIS 7.0용 IIS 6.0 WMI 호환성 구성 요소가 서버 또는 원격 IIS 호스트에 설치되어 있지 않습니다.  

- 설치 프로그램에서 원격 IIS 설정을 확인할 수 없습니다. IIS 공통 구성 요소가 사이트 서버에 설치되어 있지 않습니다.  

### <a name="case-insensitive-collation-on-sql-server"></a>SQL Server에 대한 대소문자를 구분하지 않는 정렬

*적용 대상: 사이트 데이터베이스 서버*

SQL Server 설치에서 대/소문자를 구분하지 않는 데이터 정렬(예: **SQL_Latin1_General_CP1_CI_AS**)을 사용합니다.

### <a name="central-administration-site-server-administrative-rights-on-expand-primary-site"></a>확장 주 사이트에 대한 중앙 관리 사이트 서버 관리 권한

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 중앙 관리 사이트 서버의 컴퓨터 계정에는 독립 실행형 주 사이트 서버에 대한 **관리자** 권한이 있습니다.

### <a name="client-version-on-management-point-computer"></a>관리 지점 컴퓨터의 클라이언트 버전

*적용 대상: 관리 지점*

다른 버전의 Configuration Manager 클라이언트가 설치된 서버에 관리 지점을 설치합니다.

### <a name="cloud-management-gateway-on-the-expanded-primary-site"></a>확장된 기본 사이트의 클라우드 관리 게이트웨이

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 클라우드 관리 게이트웨이 역할이 독립 실행형 주 사이트에 설치되지 않습니다.

### <a name="connection-to-sql-server-on-central-administration-site"></a>중앙 관리 사이트의 SQL Server에 대한 연결

*적용 대상: 주 사이트*

기존 계층 구조에 조인할 주 사이트에서 Configuration Manager 설치 프로그램을 실행하는 사용자 계정에는 중앙 관리 사이트의 SQL Server 인스턴스에 대한 **sysadmin** 역할이 있습니다.

### <a name="custom-client-agent-settings-have-nap-enabled"></a>사용자 지정 클라이언트 에이전트 설정에서 NAP 사용

*적용 대상: 중앙 관리 사이트, 주 사이트*

사용자 지정 클라이언트 설정은 NAP(네트워크 액세스 보호)를 사용하도록 설정하지 않습니다.

### <a name="data-warehouse-service-point-on-the-expanded-primary-site"></a>확장된 기본 사이트의 데이터 웨어하우스 서비스 지점

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 데이터 웨어하우스 서비스 지점 역할이 독립 실행형 주 사이트에 설치되지 않습니다.

### <a name="dedicated-sql-server-instance"></a>전용 SQL Server 인스턴스

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

전용 SQL Server의 인스턴스에서 Configuration Manager 사이트 데이터베이스를 호스팅하도록 구성했습니다.

다른 사이트에서 인스턴스를 사용하는 경우 새 사이트에 대해 다른 인스턴스를 선택해야 합니다. 다른 사이트를 제거하거나 해당 데이터베이스를 SQL Server의 다른 인스턴스로 이동할 수도 있습니다.

### <a name="default-client-agent-settings-have-nap-enabled"></a>기본 클라이언트 에이전트 설정에서 NAP 사용

*적용 대상: 중앙 관리 사이트, 주 사이트*

기본 클라이언트 설정은 NAP(네트워크 액세스 보호)를 사용하도록 설정하지 않습니다.

### <a name="domain-membership-error"></a>도메인 멤버 자격(오류)

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트, SMS 공급자, SQL Server*

Configuration Manager에서 컴퓨터가 Windows 도메인의 멤버입니다.

### <a name="endpoint-protection-point-on-the-expanded-primary-site"></a>확장된 주 사이트의 Endpoint Protection 지점

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 Endpoint Protection 지점 역할이 독립 실행형 주 사이트에 설치되지 않습니다.

### <a name="existing-configuration-manager-server-components-on-server"></a>서버의 기존 Configuration Manager 서버 구성 요소

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

사이트 서버 또는 사이트 시스템 역할은 사이트 설치를 위해 선택한 서버에 아직 설치되어 있지 않습니다.

### <a name="existing-stand-alone-primary-site-for-version-and-site-code"></a>기존 독립 실행형 주 사이트의 버전 및 사이트 코드

*적용 대상: 중앙 관리 사이트, 주 사이트*

확장하려는 주 사이트는 독립 실행형 주 사이트입니다. 이 사이트에는 동일한 버전의 Configuration Manager가 있지만 설치될 중앙 관리 사이트와 다른 사이트 코드가 있습니다.

### <a name="firewall-exception-for-sql-server"></a>SQL Server 대한 방화벽 예외

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트, 관리 지점*

Windows 방화벽이 사용되지 않거나 SQL Server에 대한 관련 Windows 방화벽 예외가 있습니다.

Sqlservr.exe 또는 필수 TCP 포트에 원격으로 액세스할 수 있도록 합니다. 기본적으로 SQL Server는 TCP 포트 1433에서 수신하고 SQL SSB(Server Service Broker)는 TCP 포트 4022를 사용합니다.

### <a name="free-disk-space-on-site-server"></a>사이트 서버의 사용 가능한 디스크 공간

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

사이트 서버를 설치하려면 15GB 이상의 사용 가능한 디스크 공간이 있어야 합니다. SMS 공급자를 동일한 서버에 설치하는 경우 1GB의 사용 가능한 공간이 추가로 필요합니다.

### <a name="iis-service-running"></a>IIS 서비스 실행 중

*적용 대상: 관리 지점, 배포 지점*

IIS가 관리 지점 또는 배포 지점에 대한 서버에 설치되어 실행되고 있습니다.

### <a name="incompatible-collection-references"></a>호환되지 않는 컬렉션 참조

*적용 대상: 중앙 관리 사이트*

업그레이드하는 동안 컬렉션에서 동일한 형식의 다른 컬렉션만 참조합니다.

### <a name="match-collation-of-expand-primary-site"></a>확장 주 사이트의 데이터 정렬 일치

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 독립 실행형 주 사이트의 사이트 데이터베이스에는 중앙 관리 사이트의 사이트 데이터베이스와 동일한 데이터 정렬이 있습니다.

### <a name="maximum-text-replication-size-for-sql-server-always-on-availability-groups"></a>SQL Server Always On 가용성 그룹에 대한 최대 텍스트 복제 크기

*적용 대상: 사이트 데이터베이스 서버*

SQL Server Always On을 사용하면 **최대 텍스트 복제 크기** 설정을 제대로 구성해야 합니다. 자세한 내용은 [Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)를 참조하세요.

### <a name="microsoft-intune-connector-on-the-expanded-primary-site"></a>확장된 주 사이트의 Microsoft Intune 커넥터

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 Microsoft Intune 커넥터 역할이 독립 실행형 주 사이트에 설치되지 않습니다.

### <a name="microsoft-remote-differential-compression-rdc-library-registered"></a>Microsoft RDC(원격 차등 압축) 라이브러리가 등록됨

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

RDC 라이브러리가 Configuration Manager 사이트 서버에 등록됩니다.

### <a name="microsoft-windows-installer"></a>Microsoft Windows Installer

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

Windows Installer 버전을 확인합니다.

이 검사가 실패하면 설치 프로그램에서 버전을 확인할 수 없거나 설치된 버전이 Windows Installer 4.5의 최소 요구 사항을 충족하지 않습니다.

### <a name="minimum-net-framework-version-for-configuration-manager-console"></a>Configuration Manager 콘솔에 대한 최소 .NET Framework 버전

*적용 대상: Configuration Manager 콘솔*

Microsoft .NET Framework 4.0이 Configuration Manager 콘솔 컴퓨터에 설치됩니다.

### <a name="minimum-net-framework-version-for-configuration-manager-site-server"></a>Configuration Manager 사이트 서버에 대한 최소 .NET Framework 버전

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

NET Framework 3.5가 Configuration Manager 사이트 서버에 설치되거나 사용하도록 설정됩니다.

### <a name="minimum-net-framework-version-for-sql-server-express-edition-installation-for-configuration-manager-secondary-site"></a>Configuration Manager 보조 사이트용 SQL Server Express Edition 설치를 위한 최소 .NET Framework 버전

*적용 대상: 보조 사이트*

.NET Framework 4.0이 Configuration Manager 보조 사이트 서버에 설치되거나 사용하도록 설정됩니다. 이 버전은 SQL Server Express에 필요합니다.

### <a name="parent-database-collation"></a>부모 데이터베이스 데이터 정렬

*적용 대상: 주 사이트, 보조 사이트*

사이트 데이터베이스의 데이터 정렬이 부모 사이트 데이터베이스의 데이터 정렬과 일치합니다. 계층의 모든 사이트가 동일한 데이터베이스 정렬을 사용해야 합니다.

### <a name="parent-site-replication-status"></a>부모 사이트 복제 상태

*적용 대상: 중앙 관리 사이트, 주 사이트*

부모 사이트의 복제 상태가 **복제 활성**(상태**125**)입니다.

### <a name="pending-system-restart"></a>시스템 다시 시작 보류 중

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

설치 프로그램을 실행하기 전에 다른 프로그램에서 서버를 다시 시작해야 합니다.

1810 버전부터 이 검사는 더 탄력적입니다. 컴퓨터가 다시 시작 보류 중 상태인지 확인하기 위해 다음 레지스트리 위치가 검사됩니다.<!--SCCMDocs-pr issue 3010-->  

- `HKLM:Software\Microsoft\Windows\CurrentVersion\Component Based Servicing\RebootPending`  

- `HKLM:SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\RebootRequired`  

- `HKLM:SYSTEM\CurrentControlSet\Control\Session Manager, PendingFileRenameOperations`  

- `HKLM:Software\Microsoft\ServerManager, CurrentRebootAttempts`  

### <a name="primary-fqdn"></a>기본 FQDN

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트, 사이트 데이터베이스 서버*

컴퓨터의 NetBIOS 이름이 FQDN(정규화된 도메인 이름)의 로컬 호스트 이름과 일치합니다.

### <a name="read-only-domain-controller"></a>읽기 전용 도메인 컨트롤러

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

사이트 데이터베이스 서버 및 보조 사이트 서버는 RODC(읽기 전용 도메인 컨트롤러)에서 지원되지 않습니다.

자세한 내용은 [도메인 컨트롤러에 SQL Server를 설치할 때 발생하는 문제](https://support.microsoft.com/help/2032911)에 대한 Microsoft 지원 아티클을 참조하세요.

### <a name="required-sql-server-collation"></a>필요한 SQL Server 데이터 정렬

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

SQL Server에 대한 인스턴스가 **SQL_Latin1_General_CP1_CI_AS** 데이터 정렬을 사용하도록 구성됩니다.

Configuration Manager 사이트 데이터베이스가 이미 설치된 경우 이 검사는 데이터베이스에도 적용됩니다. SQL Server 인스턴스와 데이터베이스 데이터 정렬을 변경하는 방법에 대한 자세한 내용은 [SQL 데이터 정렬 및 유니코드 지원](https://docs.microsoft.com/sql/relational-databases/collations/collation-and-unicode-support)을 참조하세요.

중국어 OS를 사용하고 GB18030 지원이 필요한 경우 이 검사가 적용되지 않습니다. GB18030 지원을 사용하는 방법에 대한 자세한 내용은 [다국어 지원](/sccm/core/plan-design/hierarchy/international-support)을 참조하세요.

### <a name="server-service-is-running"></a>서버 서비스 실행 중

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

서버 서비스가 시작되어 실행되고 있습니다.

### <a name="setup-source-folder"></a>설치 프로그램 원본 폴더

*적용 대상: 보조 사이트*

보조 사이트에 대한 컴퓨터 계정에 있는 설치 프로그램 원본 폴더 및 공유에 대한 권한은 다음과 같습니다.

- **읽기** NTFS 파일 시스템 권한  

- **읽기** 공유 권한  

> [!Note]  
> 관리 공유(예: C$ 및 D$)를 사용하는 경우 보조 사이트 컴퓨터 계정은 서버의 **관리자**여야 합니다.  

### <a name="setup-source-version"></a>설치 프로그램 원본 버전

*적용 대상: 보조 사이트*

보조 사이트 설치를 위해 지정한 원본 폴더의 Configuration Manager 버전이 주 사이트의 Configuration Manager 버전과 일치합니다.

### <a name="site-code-in-use"></a>사용 중인 사이트 코드

*적용 대상: 주 사이트*

지정된 사이트 코드는 Configuration Manager 계층 구조에서 아직 사용되지 않습니다. 이 사이트에 대한 고유한 사이트 코드를 지정합니다.

### <a name="site-server-computer-account-administrative-rights"></a>사이트 서버 컴퓨터 계정 관리 권한

*적용 대상: 주 사이트, 사이트 데이터베이스 서버*

사이트 서버 컴퓨터 계정에는 SQL Server 및 관리 지점에 대한 **관리자** 권한이 있습니다.

### <a name="site-server-fqdn-length"></a>사이트 서버 FQDN 길이

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

사이트 서버의 FQDN 길이입니다.

### <a name="site-server-in-passive-mode-on-the-expanded-primary-site"></a>확장된 기본 사이트에 있는 수동 모드의 사이트 서버

*적용 대상: 중앙 관리 사이트*

주 사이트를 계층 구조로 확장하면 수동 모드의 사이트 서버 역할이 독립 실행형 주 사이트에 설치되지 않습니다.

### <a name="sms-provider-in-same-domain-as-site-server"></a>사이트 서버와 동일한 도메인에 있는 SMS 공급자 컴퓨터

*적용 대상: SMS 공급자*

SMS 공급자의 모든 인스턴스는 사이트 서버와 동일한 도메인에 있습니다.

### <a name="software-update-point-in-nlb-configuration"></a>NLB 구성의 소프트웨어 업데이트 지점

*적용 대상: 소프트웨어 업데이트 지점*

사이트는 활성 소프트웨어 업데이트 지점에 대해 가상 위치를 포함한 NLB(네트워크 부하 분산)를 사용하지 않습니다.

### <a name="software-update-point-using-a-load-balancer"></a>부하 분산 장치를 사용한 소프트웨어 업데이트 지점

*적용 대상: 소프트웨어 업데이트 지점*

Configuration Manager는 네트워크(NLB) 또는 하드웨어 부하 분산 장치(HLB)에서 소프트웨어 업데이트 지점을 지원하지 않습니다.

### <a name="sql-server-always-on-availability-groups"></a>SQL Server Always On 가용성 그룹

*적용 대상: 사이트 데이터베이스 서버*

SQL Server Always On을 사용하면 가용성 그룹을 호스트하기 위한 최소 요구 사항을 충족해야 합니다. 자세한 내용은 [Configuration Manager에서 SQL Server Always On 가용성 그룹 사용 준비](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)를 참조하세요.

### <a name="sql-server-availability-group-configured-for-readable-secondaries"></a>읽을 수 있는 보조 복제본에 대해 SQL Server 가용성 그룹 구성

*적용 대상: 사이트 데이터베이스 서버*

SQL Server Always On을 사용하면 가용성 그룹 복제본의 보조 읽기 상태를 확인합니다.

### <a name="sql-server-availability-group-configured-for-manual-failover"></a>수동 장애 조치(failover)를 위해 SQL Server 가용성 그룹 구성

*적용 대상: 사이트 데이터베이스 서버*

SQL Server Always On을 사용하면 가용성 그룹 복제본은 수동 장애 조치에 대해 구성됩니다.

### <a name="sql-server-availability-group-replicas-on-default-instance"></a>기본 인스턴스의 SQL Server 가용성 그룹 복제본

*적용 대상: 사이트 데이터베이스 서버*

SQL Server Always On을 사용하면 가용성 그룹 복제본은 기본 인스턴스에 위치합니다.

### <a name="sql-availability-group-replicas-must-all-have-the-same-seeding-mode"></a>SQL 가용성 그룹 복제본은 시딩 모드가 모두 동일해야 합니다.

<!-- SCCMDocs-pr#3899 -->
*적용 대상: 사이트 데이터베이스 서버*

1906년 버전부터 SQL Server Always On을 사용할 때 동일한 [시딩 모드](https://docs.microsoft.com/sql/database-engine/availability-groups/windows/automatic-seeding-secondary-replicas)의 가용성 그룹 복제본을 구성해야 합니다.

### <a name="sql-availability-group-replicas-must-be-healthy"></a>SQL 가용성 그룹 복제본이 정상 상태여야 합니다.

<!-- SCCMDocs-pr#3899 -->
*적용 대상: 사이트 데이터베이스 서버*

버전 1906부터 SQL Server Always On을 사용하면 가용성 그룹 복제본은 수동 장애 조치에 대해 구성됩니다.

### <a name="sql-server-configuration-for-site-upgrade"></a>사이트 업그레이드에 대한 SQL Server 구성

*적용 대상: 사이트 데이터베이스 서버*

SQL Server가 사이트 업그레이드에 대한 최소 요구 사항을 충족해야 합니다. 자세한 내용은 [지원되는 SQL Server 버전](/sccm/core/plan-design/configs/support-for-sql-server-versions)을 참조하세요.

### <a name="sql-server-edition"></a>SQL Server 버전

*적용 대상: 사이트 데이터베이스 서버*

사이트의 SQL Server가 SQL Server Express가 아닙니다.

### <a name="sql-server-express-on-secondary-site"></a>보조 사이트의 SQL Server Express

*적용 대상: 보조 사이트*

SQL Server Express가 보조 사이트 서버에 성공적으로 설치할 수 있습니다.

### <a name="sql-server-on-the-secondary-site-server"></a>보조 사이트 서버의 SQL Server

*적용 대상: 보조 사이트*

SQL Server가 보조 사이트 서버에 설치됩니다. 보조 사이트의 원격 사이트 시스템에는 SQL Server를 설치할 수 없습니다.

> [!Warning]  
> 설치 프로그램에서 SQL Server의 기존 인스턴스를 사용하도록 선택한 경우에만 이 검사가 적용됩니다.  

### <a name="sql-server-service-running-account"></a>SQL Server 서비스 실행 계정

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

SQL Server 서비스의 로그온 계정이 로컬 사용자 계정 또는 **LOCAL SERVICE**가 아닙니다.

올바른 **NETWORK SERVICE** 또는 **LOCAL SYSTEM** 도메인 계정을 사용하도록 SQL Server 서비스를 구성합니다.

### <a name="sql-server-site-database-consistency"></a>SQL Server 사이트 데이터베이스 일관성

*적용 대상: 사이트 데이터베이스 서버*

데이터베이스 일관성을 확인합니다.

### <a name="sql-server-sysadmin-rights"></a>SQL Server sysadmin 권한

*적용 대상: 사이트 데이터베이스 서버*

Configuration Manager 설치 프로그램을 실행하는 사용자 계정에는 사이트 데이터베이스 설치를 위해 선택한 SQL Server 인스턴스에 대한 **sysadmin** 역할이 있습니다. 또한 설치 프로그램에서 권한을 확인하기 위해 SQL Server의 인스턴스에 액세스할 수 없는 경우에도 이 검사가 실패합니다.

### <a name="sql-server-sysadmin-rights-for-reference-site"></a>참조 사이트에 대한 SQL Server sysadmin 권한

*적용 대상: 사이트 데이터베이스 서버*

Configuration Manager 설치 프로그램을 실행하는 사용자 계정에는 참조 사이트 데이터베이스로 선택한 SQL Server 역할 인스턴스에 대한 **sysadmin** 역할이 있습니다. 사이트 데이터베이스를 수정하려면 SQL Server **sysadmin** 역할 권한이 필요합니다.

### <a name="sql-server-tcp-port"></a>SQL Server TCP 포트

*적용 대상: 사이트 데이터베이스 서버*

SQL Server 인스턴스에 TCP가 사용되고 있고 TCP가 정적 포트를 사용하도록 설정됩니다.

### <a name="sql-server-version"></a>SQL Server 버전

*적용 대상: 사이트 데이터베이스 서버*

지원되는 버전의 SQL Server가 지정된 사이트 데이터베이스 서버에 설치됩니다.

자세한 내용은 [SQL Server 버전에 대한 지원](/sccm/core/plan-design/configs/support-for-sql-server-versions)을 참조하세요.

### <a name="unsupported-os-for-configuration-manager-console"></a>Configuration Manager 콘솔에 대해 지원되지 않는 OS

*적용 대상: Configuration Manager 콘솔*

지원되는 OS 버전을 실행하는 컴퓨터에 Configuration Manager 콘솔을 설치합니다.

자세한 내용은 [Configuration Manager 콘솔에 대해 지원되는 OS](/sccm/core/plan-design/configs/supported-operating-systems-consoles)를 참조하세요.

### <a name="unsupported-os-for-site-server"></a>사이트 서버에 지원되지 않는 OS

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트, Configuration Manager 콘솔, 관리 지점, 배포 지점*

서버에서 지원되는 OS 버전을 실행합니다.

자세한 내용은 [Configuration Manager 사이트 시스템 서버에 대해 지원되는 OS 버전](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)을 참조하세요.

### <a name="unsupported-site-system-role-out-of-band-service-point"></a>지원되지 않는 사이트 시스템 역할: 대역 외 서비스 지점

*적용 대상: 주 사이트*

대역 외 서비스 지점 사이트 시스템 역할이 설치되지 않습니다.

### <a name="unsupported-site-system-role-system-health-validation-point"></a>지원되지 않는 사이트 시스템 역할: 시스템 상태 유효성 검사 지점

*적용 대상: 주 사이트*

시스템 상태 유효성 검사 지점 사이트 시스템 역할이 설치되지 않습니다.

### <a name="unsupported-upgrade-path"></a>지원되지 않는 업그레이드 경로

*적용 대상: 중앙 관리 사이트, 주 사이트*

계층의 모든 사이트 서버가 업그레이드에 필요한 Configuration Manager 최소 버전을 충족합니다.

### <a name="usmt-installed"></a>USMT 설치됨

*적용 대상: 중앙 관리 사이트, 주 사이트(독립 실행형에만 해당)*

Windows용 Windows ADK(Assessment and Deployment Kit)의 USMT(사용자 환경 마이그레이션 도구) 구성 요소가 설치됩니다.

### <a name="validate-fqdn-of-sql-server"></a>SQL Server 컴퓨터의 FQDN 확인

*적용 대상: 사이트 데이터베이스 서버*

SQL Server 컴퓨터에 올바른 FQDN을 지정했습니다.

### <a name="verify-central-administration-site-version"></a>중앙 관리 사이트 버전 확인

*적용 대상: 주 사이트*

중앙 관리 사이트에는 동일한 버전의 Configuration Manager가 있습니다.

### <a name="verify-database-consistency"></a>데이터베이스 일관성 확인

*적용 대상: 중앙 관리 사이트, 주 사이트*

SQL Server에서 사이트 데이터베이스의 일관성을 확인합니다.  

### <a name="windows-deployment-tools-installed"></a>Windows 배포 도구 설치됨

*적용 대상: SMS 공급자*

Windows ADK의 Windows 배포 도구 구성 요소가 설치됩니다.

### <a name="windows-failover-cluster"></a>Windows 장애 조치(failover) 클러스터

*적용 대상: 사이트 서버, 관리 지점, 배포 지점*

사이트 서버, 관리 지점 또는 배포 지점 역할이 있는 서버는 Windows 클러스터의 일부가 아닙니다.

1810 버전부터 Configuration Manager 설치 프로세스는 더 이상 장애 조치 클러스터링을 위한 Windows 역할이 있는 컴퓨터에 사이트 서버 역할의 설치를 차단하지 않습니다. SQL Always On에는 이 역할이 필요하므로 이전에는 사이트 서버에 사이트 데이터베이스를 공동 배치할 수 없었습니다. 이 변경을 사용하면 SQL Always On 및 사이트 서버를 수동 모드에서 사용하여 더 적은 수의 서버로 고가용성 사이트를 만들 수 있습니다. 자세한 내용은 [고가용성 옵션](/sccm/core/servers/deploy/configure/high-availability-options)을 참조하세요. <!--1359132-->  

### <a name="windows-pe-installed"></a>Windows PE 설치

*적용 대상: SMS 공급자*

Windows ADK의 Windows PE(사전 설치 환경) 구성 요소가 설치됩니다.



## <a name="warnings"></a>경고

### <a name="active-directory-domain-functional-level"></a>Active Directory 도메인 기능 수준

*적용 대상: 중앙 관리 사이트, 주 사이트*

Active Directory 도메인 및 포리스트 기능 수준은 최소 Windows Server 2008 R2 이상입니다. 자세한 내용은 [Active Directory 도메인 지원](/sccm/core/plan-design/configs/support-for-active-directory-domains)을 참조하세요.

### <a name="administrative-rights-on-distribution-point"></a>배포 지점에 대한 관리 권한

*적용 대상: 배포 지점*

설치 프로그램을 실행하는 사용자 계정에는 배포 지점에 대한 **관리자** 권한이 있습니다.

### <a name="administrative-rights-on-management-point"></a>관리 지점에 대한 관리 권한

*적용 대상: 관리 지점, 배포 지점*

사이트 서버의 컴퓨터 계정에는 관리 지점 및 배포 지점에 대한 **관리자** 권한이 있습니다.

### <a name="administrative-share-site-system"></a>관리자 공유(사이트 시스템)

*적용 대상: 관리 지점*

필요한 관리자 공유가 사이트 시스템 컴퓨터에 있습니다.

### <a name="application-compatibility"></a>애플리케이션 호환성

*적용 대상: 중앙 관리 사이트, 주 사이트*

현재 애플리케이션이 애플리케이션 스키마와 호환됩니다.현재 애플리케이션이 애플리케이션 스키마와 호환됩니다.

### <a name="backlogged-inboxes"></a>백로깅된 수신함

*적용 대상: 중앙 관리 사이트, 주 사이트*

사이트 서버는 적시에 중요한 받은 편지함을 처리하고 있습니다. 받은 편지함에는 하루가 지난 파일이 포함되지 않습니다.

다음과 같은 받은 편지함 폴더를 확인합니다.

- `despoolr.box\receive\*.i??`

- `despoolr.box\receive\*.s??`

- `despoolr.box\receive\*.nil`

- `schedule.box\requests\*.sr?`

이 경고를 해결하려면 디스풀러 및 스케줄러 사이트 시스템 구성 요소가 실행 중인지 확인합니다.

### <a name="bits-installed"></a>BITS 설치됨

*적용 대상: 관리 지점*

BITS(Background Intelligent Transfer Service)가 IIS에 설치되고 사용하도록 설정됩니다.

### <a name="cloud-management-gateway-requires-either-token-based-authentication-or-an-https-management-point"></a>클라우드 관리 게이트웨이에는 토큰 기반 인증 또는 HTTPS 관리 지점이 필요합니다.

*적용 대상: 클라우드 관리 게이트웨이*

일부 버전의 Configuration Manager를 사용하면 CMG(클라우드 관리 게이트웨이)에서 HTTP 관리 지점을 사용할 수 없습니다. HTTPS에 대해 CMG를 구성하거나 향상된 HTTP에 대해 사이트를 구성합니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.

### <a name="configuration-for-sql-server-memory-usage"></a>SQL Server 메모리 사용에 대한 구성

*적용 대상: 사이트 데이터베이스 서버*

SQL Server가 메모리를 무제한 사용하도록 구성됩니다. SQL Server 메모리를 최대 한도로 구성합니다.

### <a name="distribution-point-package-version"></a>배포 지점 패키지 버전

*적용 대상: 배포 지점*

사이트의 모든 배포 지점에 최신 버전의 소프트웨어 배포 패키지가 있습니다.

### <a name="domain-membership-warning"></a>도메인 멤버 자격(경고)

*적용 대상: 관리 지점, 배포 지점*

Configuration Manager에서 컴퓨터가 Windows 도메인의 멤버입니다.

### <a name="firewall-exception-for-sql-server-standalone-primary-site"></a>SQL Server에 대한 방화벽 예외(독립 실행형 주 사이트)

*적용 대상: 주 사이트(독립 실행형에만 해당)*

Windows 방화벽이 사용되지 않거나 SQL Server에 대한 관련 Windows 방화벽 예외가 있습니다.

Sqlservr.exe 또는 필수 TCP 포트에 원격으로 액세스할 수 있도록 합니다. 기본적으로 SQL Server는 1433 TCP 포트에서 수신 대기하고, SSB(Server Service Broker)는 4022 TCP 포트를 사용합니다.

### <a name="firewall-exception-for-sql-server-for-management-point"></a>관리 지점의 SQL Server에 대한 방화벽 예외

*적용 대상: 관리 지점*

Windows 방화벽이 사용되지 않거나 SQL Server에 대한 관련 Windows 방화벽 예외가 있습니다.

### <a name="iis-https-configuration"></a>IIS HTTPS 구성

*적용 대상: 관리 지점, 배포 지점*

IIS 웹 사이트에는 HTTPS 통신 프로토콜에 대한 바인딩이 있습니다.

HTTPS가 필요한 사이트 역할을 설치하는 경우 유효한 PKI(공개 키 인프라) 인증서가 있는 지정된 서버에서 IIS 사이트 바인딩을 구성합니다.

### <a name="microsoft-xml-core-services-60-msxml60"></a>Microsoft XML Core Services 6.0(MSXML60)

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트, Configuration Manager 콘솔, 관리 지점, 배포 지점*

MSXML 버전 6.0 이상이 설치되어 있는지 확인합니다.

### <a name="network-access-protection-nap-is-no-longer-supported"></a>NAP(네트워크 액세스 보호)가 더 이상 지원되지 않습니다.

*적용 대상: 주 사이트*

NAP에서 사용 가능한 소프트웨어 업데이트가 없습니다.

### <a name="ntfs-drive-on-site-server"></a>사이트 서버의 NTFS 드라이브

*적용 대상: 주 사이트*

디스크 드라이브가 NTFS 파일 시스템으로 포맷됩니다. 보안 수준을 높이려면 NTFS 파일 시스템으로 포맷된 디스크 드라이브에 사이트 서버 구성 요소를 설치합니다.

### <a name="bkmk_pending-policy"></a> 구성 항목 정책 업데이트 보류 중

<!--SCCMDocs-pr issue 2814-->

*적용 대상: 주 사이트*

1706 버전 이상에서 업데이트하는 경우 1806 버전부터는 많은 애플리케이션을 배포해야 하고, 이 중 하나 이상에 승인이 필요한 경우 이 경고가 표시될 수 있습니다.

다음과 같은 두 가지 옵션이 있습니다.  

- 경고를 무시하고 업그레이드를 계속합니다. 이 작업은 업데이트하는 동안 정책을 처리할 때 사이트 서버에서 처리 속도가 더 증가합니다. 업데이트 후에 관리 지점에서 추가 프로세서 부하가 나타날 수도 있습니다.  

- 요구 사항 또는 특정 OS 요구 사항이 없는 애플리케이션 중 하나를 수정합니다. 해당 시점에 사이트 서버에 대한 부하의 일부를 미리 처리합니다. **objreplmgr.log**를 검토한 다음, 관리 지점에서 프로세서를 모니터링합니다. 처리를 완료한 후에 사이트를 업데이트합니다. 업데이트 후에 일부가 추가로 처리될 수 있지만 첫 번째 옵션에서 경고를 무시하는 경우보다는 적습니다.  

### <a name="pending-system-restart-on-the-remote-sql-server"></a>원격 SQL Server에서 시스템 다시 시작 보류 중

*적용 대상: 버전 1902 이상, 원격 SQL Server*

설치 프로그램을 실행하기 전에 다른 프로그램에서 서버를 다시 시작해야 합니다.

컴퓨터가 다시 시작 보류 중 상태인지 확인하기 위해 다음 레지스트리 위치가 검사됩니다.<!--SCCMDocs-pr issue 3377-->  

- `HKLM:Software\Microsoft\Windows\CurrentVersion\Component Based Servicing\RebootPending`  

- `HKLM:SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\RebootRequired`  

- `HKLM:SYSTEM\CurrentControlSet\Control\Session Manager, PendingFileRenameOperations`  

- `HKLM:Software\Microsoft\ServerManager, CurrentRebootAttempts`  

### <a name="powershell-20-on-site-server"></a>사이트 서버의 PowerShell 2.0

*적용 대상: Exchange 커넥터가 있는 주 사이트*

Windows PowerShell 버전 2.0 이상이 Configuration Manager Exchange 커넥터용 사이트 서버에 설치됩니다.

### <a name="remote-connection-to-wmi-on-secondary-site"></a>보조 사이트의 WMI에 대한 원격 연결

*적용 대상: 보조 사이트*

설치 프로그램에서 보조 사이트 서버의 서 WMI에 대한 원격 연결을 설정할 수 있습니다.

### <a name="schema-extensions"></a>스키마 확장

*적용 대상: 중앙 관리 사이트, 주 사이트*

Active Directory 스키마가 확장되었습니다. 확장된 경우 사용된 스키마 확장의 버전입니다.

Configuration Manager는 사이트 서버 설치에 Active Directory 스키마 확장이 필요하지 않습니다. Microsoft는 모든 Configuration Manager 기능을 완전히 사용하도록 추천합니다. 스키마 확장의 이점에 대한 자세한 내용은 [사이트 게시를 위해 Active Directory 준비](/sccm/core/plan-design/network/extend-the-active-directory-schema)를 참조하세요.

### <a name="share-name-in-package"></a>패키지의 공유 이름

*적용 대상: 중앙 관리 사이트, 주 사이트*

패키지에는 `#`과 같이 공유 이름의 잘못된 문자가 포함되지 않습니다.

### <a name="site-system-to-sql-server-communication"></a>사이트 시스템에서 SQL Server로의 통신

*적용 대상: 보조 사이트, 관리 지점*

사이트 데이터베이스 인스턴스에 대해 SQL Server 서비스를 실행하도록 구성한 계정에는 Active Directory 도메인 서비스에 유효한 SPN(서비스 사용자 이름)이 있습니다. Kerberos 인증을 지원하는 Active Directory에 유효한 SPN을 등록합니다.

### <a name="bkmk_changetracking"></a> SQL Server 변경 내용 추적 정리

*적용 대상: 사이트 데이터베이스 서버*

1810 버전부터 사이트 데이터베이스에 SQL 변경 추적 데이터의 백로그가 있는지 확인합니다.<!--SCCMDocs-pr issue 3023-->  

사이트 데이터베이스에서 진단 저장 프로시저를 실행하여 이 검사를 수동으로 확인합니다. 먼저 사이트 데이터베이스에 대한 [진단 연결](https://docs.microsoft.com/sql/database-engine/configure-windows/diagnostic-connection-for-database-administrators?view=sql-server-2017)을 만듭니다. 가장 쉬운 방법은 SQL Server Management Studio 데이터베이스 엔진 쿼리 편집기를 사용하여 `admin:<instance name>`에 연결하는 것입니다.

전용 관리자 연결 쿼리 창에서 다음 명령을 실행합니다.

```SQL
USE <ConfigMgr database name>
EXEC spDiagChangeTracking
```

이 저장 프로시저는 데이터베이스 크기와 백로그 크기에 따라 몇 분 또는 몇 시간 내에 실행될 수 있습니다. 쿼리가 완료되면 백로그와 관련된 두 개의 데이터 섹션이 표시됩니다. 먼저 **CT_Days_Old**를 살펴보겠습니다. 이 값은 syscommittab 테이블에서 가장 오래된 항목의 보존 기간(일)을 알려줍니다. Configuration Manager 기본값인 5일이어야 합니다. 이 기본값은 변경하지 마세요. 데이터 처리 또는 복제가 많은 경우 syscommittab에서 가장 오래된 항목은 5일을 초과할 수 있습니다. 이 값이 7일을 초과하면 변경 추적 데이터의 수동 정리를 실행합니다.  

변경 추적 데이터를 정리하려면 전용 관리 연결에서 다음 명령을 실행합니다.

```SQL
USE <ConfigMgr database name>
EXEC spDiagChangeTracking @CleanupChangeTracking = 1
```

이 명령은 syscommittab 및 연결된 쪽의 모든 테이블에 대한 정리를 시작합니다. 몇 분 또는 몇 시간 내에 실행될 수 있습니다. 진행률을 모니터링하려면 **vLogs** 보기를 쿼리합니다. 현재 진행률을 보려면 다음 쿼리를 실행합니다.

```SQL
SELECT * FROM vLogs WHERE ProcedureName = 'spDiagChangeTracking'
```

### <a name="sql-server-native-client"></a>SQL Server Native Client

<!--SCCMDocs-pr issue 3094-->

새 사이트를 설치하면 Configuration Manager에서 SQL Server Native Client를 재배포 가능한 구성 요소로 자동으로 설치합니다. 사이트를 설치한 후 Configuration Manager는 SQL Server Native Client를 업그레이드하지 않습니다. SQL Server Native Client를 업데이트하려면 사이트 설치 프로세스에 영향을 줄 수 있도록 다시 시작해야 합니다.

이 검사에서는 지원되는 버전의 SQL Native Client가 사이트에 있는지 확인합니다. 1810 버전부터 최소 버전은 SQL 2012 SP4(`11.*.7001.0`)입니다.

이 SQL Native Client 버전은 TLS 1.2를 지원합니다. 자세한 내용은 다음 아티클을 참조하세요.

- [Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)  

- [Configuration Manager에서 TLS 1.2를 사용하도록 설정하는 방법](/sccm/core/plan-design/security/enable-tls-1-2)  

Configuration Manager는 다음 사이트 시스템 역할에서 SQL Server Native Client를 사용합니다.<!-- SCCMDocs issue 1150 -->

- 사이트 데이터베이스 서버
- 사이트 서버: 중앙 관리 사이트, 주 사이트 또는 보조 사이트
- 관리 지점
- 디바이스 관리 지점
- 상태 마이그레이션 지점
- SMS 공급자
- 소프트웨어 업데이트 지점
- 멀티캐스트 사용 배포 지점
- Asset Intelligence 업데이트 서비스 지점
- 보고 서비스 지점
- 애플리케이션 카탈로그 웹 서비스
- 등록 지점
- Endpoint Protection 지점
- 서비스 연결 지점
- 인증서 등록 지점
- 데이터 웨어하우스 서비스 지점

### <a name="sql-server-process-memory-allocation"></a>SQL Server 프로세스 메모리 할당

*적용 대상: 사이트 데이터베이스 서버*

SQL Server에서 중앙 관리 사이트 및 주 사이트에 대해 8GB 이상의 메모리를 예약하고, 보조 사이트에 대해 4GB 이상의 메모리를 예약합니다.

자세한 내용은 [SQL Server Management Studio를 사용하여 메모리 옵션을 구성하는 방법](https://docs.microsoft.com/sql/database-engine/configure-windows/server-memory-server-configuration-options#how-to-configure-memory-options-using-)을 참조하세요.

> [!NOTE]  
> 이 검사가 보조 사이트의 SQL Server Express에는 적용되지 않습니다. 이 버전에서는 예약 메모리를 1GB로 제한합니다.  

### <a name="sql-server-security-mode"></a>SQL Server 보안 모드

*적용 대상: 사이트 데이터베이스 서버*

SQL Server가 Windows 인증 보안에 대해 구성됩니다.

### <a name="unsupported-site-system-os-version-for-upgrade"></a>업그레이드에 지원되지 않는 사이트 시스템의 OS 버전

*적용 대상: 주 사이트, 보조 사이트*

배포 지점 이외의 사이트 시스템 역할이 Windows 서버 2012 이상을 실행하는 서버에 설치됩니다.

자세한 내용은 [Configuration Manager 사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)를 참조하세요.

> [!NOTE]  
> 이 검사는 Azure에 설치된 사이트 시스템 역할 또는 Microsoft Intune에서 사용되는 클라우드 스토리지에 대한 상태를 확인할 수 없습니다. 이러한 역할에 대한 경고는 가양성으로 무시하세요.

### <a name="upgrade-assessment-toolkit-is-unsupported"></a>업그레이드 평가 도구 키트가 지원되지 않습니다.

*적용 대상: 중앙 관리 사이트, 주 사이트*

업그레이드 평가 도구 키트가 설치되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.

### <a name="verify-site-server-permissions-to-publish-to-active-directory"></a>Active Directory에 게시할 사이트 서버 권한 확인

*적용 대상: 중앙 관리 사이트, 주 사이트, 보조 사이트*

사이트 서버에 대한 컴퓨터 계정에는 Active Directory 도메인의 **시스템 관리** 컨테이너에 대한 **모든 권한**이 있습니다.

자세한 내용은 [사이트 게시를 위해 Active Directory 준비](/sccm/core/plan-design/network/extend-the-active-directory-schema)를 참조하세요.

> [!NOTE]  
> 권한을 수동으로 확인하는 경우 이 경고는 무시할 수 있습니다.

### <a name="windows-remote-management-winrm-v11"></a>WinRM(Windows Remote Management) v1.1

*적용 대상: 주 사이트, Configuration Manager 콘솔*

WinRM 1.1이 대역 외 관리 콘솔을 실행할 주 사이트 서버 또는 Configuration Manager 콘솔 컴퓨터에 설치됩니다.

WinRM 1.1을 다운로드하는 방법에 대한 자세한 내용은 [936059 지원 문서](https://support.microsoft.com/help/936059)를 참조하세요.

### <a name="wsus-on-site-server"></a>사이트 서버의 WSUS

*적용 대상: 중앙 관리 사이트, 주 사이트*

지원되는 버전의 WSUS(Windows Server Update Services)가 사이트 서버에 설치됩니다.

사이트 서버가 아닌 다른 서버에서 소프트웨어 업데이트 지점을 사용하는 경우 WSUS 관리 콘솔을 사이트 서버에 설치해야 합니다. WSUS에 대한 자세한 내용은 [Windows Server Update Services](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)를 참조하세요.
