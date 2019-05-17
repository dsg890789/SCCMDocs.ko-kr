---
title: 온-프레미스 인프라 업그레이드
titleSuffix: Configuration Manager
description: SQL Server, 사이트 시스템의 OS 등의 인프라를 업그레이드하는 방법을 알아봅니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8ca970dd-e71c-404f-9435-d36e773a0db2
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ac4f22b6da6f0ed3c743848efc5477577376116b
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65500929"
---
# <a name="upgrade-on-premises-infrastructure-that-supports-configuration-manager"></a>Configuration Manager를 지원하는 온-프레미스 인프라 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 정보를 사용하여 Configuration Manager를 실행하는 서버 인프라를 업그레이드할 수 있습니다.  

- 이전 버전에서 현재 분기인 Configuration Manager로 *업그레이드*하려면 [Configuration Manager로 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)를 참조하세요.  

- Configuration Manager 인프라를 현재 분기인 새 버전으로 *업데이트*하려면 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.  



## <a name="BKMK_SupConfigUpgradeSiteSrv"> </a> 사이트 시스템의 OS 업그레이드  

Configuration Manager는 다음과 같은 상황에서 사이트 서버 및 사이트 시스템 역할을 호스트하는 서버 OS의 현재 위치 업그레이드를 지원합니다.  

- Configuration Manager에서 업그레이드 후 Windows의 서비스 팩 수준을 계속 지원하는 경우 상위 Windows Server 서비스 팩으로의 현재 위치 업그레이드를 지원합니다.  

- 현재 위치 업그레이드:  

    - Windows Server 2016에서 Windows Server 2019로 업그레이드   

    - Windows Server 2012 R2에서 Windows Server 2019로 업그레이드   

    - Windows Server 2012 R2에서 Windows Server 2016으로 업그레이드   

    - Windows Server 2012에서 Windows Server 2016으로 업그레이드   

    - Windows Server 2012에서 Windows Server 2012 R2로 업그레이드   

    - Windows Server 2008 R2에서 Windows Server 2012 R2로 업그레이드   

서버를 업그레이드하려면 업그레이드할 OS에서 제공하는 업그레이드 절차를 따르세요. 다음 문서를 참조하세요.  

- [Windows Server 업그레이드 센터](http://aka.ms/upgradecenter)  

- [Windows Server 2016용 업그레이드 및 변환 옵션](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths)  

- [Windows Server 2012 R2용 업그레이드 옵션](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn303416(v=ws.11))   


### <a name="bkmk_2016-2019"></a> Windows Server 2016 또는 2019로 업그레이드

다음 업그레이드 시나리오에 대해 이 섹션의 단계를 사용합니다.  

- Windows Server 2012 R2 또는 Windows Server 2016을 Windows Server 2019로 업그레이드  

- Windows Server 2012 또는 Windows Server 2012 R2을 Windows Server 2016으로 업그레이드  


#### <a name="before-upgrade"></a>업그레이드 전  
- (Windows Server 2012 또는 Windows Server 2012 R2): SCEP(System Center Endpoint Protection) 클라이언트를 제거합니다. Windows Server에는 이제 SCEP 클라이언트를 대체하는 Windows Defender가 기본 제공됩니다. SCEP 클라이언트가 있으면 Windows Server로 업그레이드할 수 없습니다.  

- 서버에서 WSUS 역할을 제거합니다(설치된 경우). SUSDB를 유지하고, WSUS가 다시 설치된 후 SUSDB를 다시 연결할 수 있습니다.  

#### <a name="after-upgrade"></a>업그레이드 후   
- Windows Defender가 사용되고 자동 시작되도록 설정되었으며 실행되고 있는지 확인합니다.  

- 다음 Configuration Manager 서비스가 실행되고 있는지 확인합니다.  

    - SMS_EXECUTIVE  

    - SMS_SITE_COMPONENT_MANAGER  

- **Windows Process Activation** 및 **WWW/W3svc** 서비스가 사용되고 자동 시작되도록 설정되었는지 확인합니다. 업그레이드 프로세스는 이러한 서비스를 사용하지 않으므로 다음 사이트 시스템 역할에 대해 실행되고 있는지 확인합니다.  

    - 사이트 서버  

    - 관리 지점  

    - 애플리케이션 카탈로그 웹 서비스 지점  

    - 애플리케이션 카탈로그 웹 사이트 지점  

- 사이트 시스템 역할을 호스팅하는 각 서버가 계속 모든 [필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 충족하는지 확인합니다. 예를 들어 BITS 또는 WSUS를 다시 설치하거나 IIS에 대한 특정 설정을 구성해야 할 수 있습니다.  

- 누락된 필수 조건을 복원한 후 서버를 한 번 더 다시 시작하여 서비스가 시작되고 작동하는지 확인합니다.  

- 기본 사이트 서버를 업그레이드하는 경우 [사이트 다시 설정을 실행](/sccm/core/servers/manage/modify-your-infrastructure#bkmk_reset)합니다.  

#### <a name="known-issue-for-remote-configuration-manager-consoles"></a>원격 Configuration Manager 콘솔에 대해 알려진 문제   
사이트 서버 또는 SMS 공급 기업의 인스턴스를 업그레이드한 후에는 Configuration Manager 콘솔과 연결할 수 없습니다. 이 문제를 해결하려면 WMI에서 **SMS Admins** 그룹의 사용 권한을 수동으로 복원합니다. 사이트 서버 및 SMS 공급자 인스턴스를 호스트하는 각 원격 서버에서 사용 권한을 설정해야 합니다.

1. 해당 서버에서 MMC(Microsoft Management Console)를 열고 **WMI 컨트롤**용 스냅인을 추가한 다음 **로컬 컴퓨터**를 선택합니다.  

2. MMC에서 **WMI 컨트롤(로컬)** 의 **속성**을 열고 **보안** 탭을 선택합니다.  

3. 루트 아래의 트리를 확장하고 **SMS** 노드를 선택한 다음 **보안**을 선택합니다.  **SMS Admins** 그룹에 다음 사용 권한이 있는지 확인합니다.  

    - 계정 사용  

    - 원격 사용  

4. **보안 탭**의 **SMS** 노드 아래에서 **사이트_&lt;사이트 코드**> 노드를 선택한 후 **보안**을 선택합니다. **SMS Admins** 그룹에 다음 사용 권한이 있는지 확인합니다.  

    - 메서드 실행  

    - 공급자 쓰기  

    - 계정 사용  

    - 원격 사용  

5. 사용 권한을 저장하여 Configuration Manager 콘솔에 대한 액세스를 복원합니다.  


#### <a name="known-issue-for-remote-site-systems"></a>알려진 원격 사이트 시스템 문제
사이트 시스템 역할을 호스팅하는 서버가 업그레이드되면 `Software\Microsoft\SMS` 값이 `HKLM\SYSTEM\CurrentControlSet\Control\SecurePipeServers\Winreg\AllowedPaths` 레지스트리 키에서 누락되었을 수 있습니다. 

서버에서 Windows를 업그레이드 한 후 이 값이 누락되었으면 수동으로 추가합니다. 그렇지 않으면 사이트 시스템 역할에서 파일을 사이트 서버의 받은 편지함에 업로드하는 데 문제가 있을 수 있습니다.


### <a name="bkmk_2012r2"></a> Windows Server 2012 R2로 업그레이드

Windows Server 2008 R2 또는 Windows Server 2012에서 Windows Server 2012 R2로 업그레이드할 때 다음 조건이 적용됩니다.

#### <a name="before-upgrade"></a>업그레이드 전  
- Windows Server 2012: 서버에서 WSUS 역할을 제거합니다(설치된 경우). SUSDB를 유지하고, WSUS가 다시 설치된 후 SUSDB를 다시 연결할 수 있습니다.  

- Windows Server 2008 R2: Windows Server 2012 R2로 업그레이드하기 전에 서버에서 WSUS 3.2를 제거 해야 합니다. SUSDB를 유지하고, WSUS가 다시 설치된 후 SUSDB를 다시 연결할 수 있습니다. 자세한 내용은 [Windows Server Update Services Overview](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh852345(v=ws.11)#new-and-changed-functionality)(Windows Server Update Services 개요)를 참조하세요.  

#### <a name="after-upgrade"></a>업그레이드 후  
- 업그레이드 프로세스는 Windows 배포 서비스를 사용하지 않습니다. 이 서비스가 시작되고 다음 사이트 시스템 역할에 대해 실행되고 있는지 확인합니다.  

    - 사이트 서버  

    - 관리 지점  

    - 애플리케이션 카탈로그 웹 서비스 지점  

    - 애플리케이션 카탈로그 웹 사이트 지점  

- **Windows Process Activation** 및 **WWW/W3svc** 서비스가 사용되고 자동 시작되도록 설정되었는지 확인합니다 . 업그레이드 프로세스는 이러한 서비스를 사용하지 않으므로 다음 사이트 시스템 역할에 대해 실행되고 있는지 확인합니다.  

    - 사이트 서버  

    - 관리 지점  

    - 애플리케이션 카탈로그 웹 서비스 지점  

    - 애플리케이션 카탈로그 웹 사이트 지점  

- 사이트 시스템 역할을 호스팅하는 각 서버가 계속 모든 [필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 충족하는지 확인합니다. 예를 들어 BITS 또는 WSUS를 다시 설치하거나 IIS에 대한 특정 설정을 구성해야 할 수 있습니다.  

    누락된 필수 조건을 복원한 후 서버를 한 번 더 다시 시작하여 서비스가 시작되고 작동하는지 확인합니다.  


### <a name="unsupported-upgrade-scenarios"></a>지원되지 않는 업그레이드 시나리오

다음 Windows Server 업그레이드 시나리오는 자주 질문을 받지만 Configuration Manager에서 지원되지 않습니다.  

- Windows Server 2008에서 Windows Server 2012 이상으로 업그레이드  

- Windows Server 2008 R2에서 Windows Server 2012로 업그레이드  



##  <a name="BKMK_SupConfigUpgradeClient"></a> 클라이언트의 OS 업그레이드  

Configuration Manager는 다음과 같은 상황에서 Configuration Manager 클라이언트의 OS 현재 위치 업그레이드를 지원합니다.  

- Configuration Manager에서 업그레이드 후 서비스 팩 수준을 지원하는 경우 상위 Windows 서비스 팩으로의 현재 위치 업그레이드를 지원합니다.  

- 지원되는 버전에서 Windows 10로의 Windows 현재 위치 업그레이드. 자세한 내용은 [최신 버전으로 Windows 업그레이드](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)를 참조하세요.  

- Windows 10의 빌드 간 서비스 업그레이드. 자세한 내용은 [Windows as a Service 관리](/sccm/osd/deploy-use/manage-windows-as-a-service)를 참조하세요.  



##  <a name="BKMK_SupConfigUpgradeDBSrv"></a> SQL Server 업그레이드  

Configuration Manager는 사이트 데이터베이스 서버에서 SQL Server의 현재 위치 업그레이드를 지원합니다. 

Configuration Manager에서 지원하는 SQL Server 버전에 대한 자세한 내용은 [SQL Server 버전 지원](/sccm/core/plan-design/configs/support-for-sql-server-versions)을 참조하세요.  


### <a name="upgrade-the-service-pack-version-of-sql-server"></a>SQL Server의 서비스 팩 버전 업그레이드    

Configuration Manager는 업그레이드 후 SQL Server 서비스 팩 수준을 계속 지원하는 경우 상위 서비스 팩으로의 SQL Server 현재 위치 업그레이드를 지원합니다.

계층에 하나를 초과하는 Configuration Manager 사이트가 있는 경우 각 사이트는 다른 서비스 팩 버전의 SQL Server를 실행할 수 있습니다. 사이트가 SQL Server의 서비스 팩 버전을 업그레이드하는 순서에는 제한이 없습니다.


### <a name="upgrade-to-a-new-version-of-sql-server"></a>새 버전의 SQL Server로 업그레이드   

Configuration Manager는 다음 버전으로의 SQL Server 현재 위치 업그레이드를 지원합니다.

- SQL Server 2017  

- SQL Server 2016  

- SQL Server 2014  

사이트 데이터베이스를 호스트하는 SQL Server 버전을 업그레이드하는 경우 사이트에서 사용되는 SQL Server 버전을 다음과 같은 순서로 업그레이드해야 합니다.

1. 먼저 중앙 관리 사이트에서 SQL Server 업그레이드  

2. 보조 사이트의 상위 기본 사이트를 업그레이드하기 전에 보조 사이트 업그레이드  

3. 마지막으로 부모 기본 사이트를 업그레이드합니다. 이러한 사이트에는 중앙 관리 사이트에 보고를 하는 자식 기본 사이트와 계층의 최상위 사이트인 독립 실행형 기본 사이트가 모두 포함됩니다.  


### <a name="sql-server-cardinality-estimation-level"></a>SQL Server 카디널리티 추정 수준   

이전 버전의 SQL Server에서 사이트 데이터베이스를 업그레이드하는 경우 해당 SQL Server 인스턴스에 허용되는 최소값인 경우 데이터베이스는 기존 SQL 카디널리티 추정 수준을 유지합니다. 허용되는 수준보다 낮은 호환성 수준의 데이터베이스를 사용하여 SQL Server를 업그레이드하면 데이터베이스가 자동으로 SQL Server에서 허용되는 가장 낮은 호환성 수준으로 설정됩니다.

다음 표에서는 Configuration Manager 사이트 데이터베이스에 권장되는 호환성 수준을 식별합니다.

|SQL Server 버전 | 지원되는 호환성 수준 | 권장 수준 |
|----------------|--------------------|--------|
| SQL Server 2017 | 140, 130, 120, 110  | 140 |
| SQL Server 2016 | 130, 120, 110  | 130 |
| SQL Server 2014 | 120, 110      | 110 |

사이트 데이터베이스에 사용 중인 SQL Server 카디널리티 추정 호환성 수준을 식별하려면 사이트 데이터베이스 서버에서 다음 SQL 쿼리를 실행합니다.  
```SQL
SELECT name, compatibility_level FROM sys.databases
```

SQL CE 호환성 수준 및 설정 방법에 대한 자세한 내용은 [ALTER DATABASE 호환성 수준(Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-database-transact-sql-compatibility-level?view=sql-server-2017)을 참조하세요.


SQL Server 업그레이드에 대한 자세한 내용은 다음 SQL Server 문서를 참조하세요.  

- [SQL Server 2017로 업그레이드](https://docs.microsoft.com/sql/database-engine/install-windows/supported-version-and-edition-upgrades-2017)  

- [SQL Server 2016으로 업그레이드](https://docs.microsoft.com/sql/database-engine/install-windows/supported-version-and-edition-upgrades?view=sql-server-2016)  

- [SQL Server 2014로 업그레이드](https://docs.microsoft.com/sql/database-engine/install-windows/supported-version-and-edition-upgrades?view=sql-server-2014)  



### <a name="to-upgrade-sql-server-on-the-site-database-server"></a>사이트 데이터베이스 서버에서 SQL Server를 업그레이드하려면  

1. 사이트에서 모든 Configuration Manager 서비스 중지  

2. SQL Server를 지원되는 버전으로 업그레이드  

3. Configuration Manager 서비스 다시 시작  

> [!NOTE]  
> 중앙 관리 사이트에서 사용 중인 SQL Server 버전을 Standard에서 Datacenter 또는 Enterprise 버전으로 변경하는 경우 데이터베이스 파티션은 변경되지 않습니다. 이 데이터베이스 파티션은 계층에서 지원하는 클라이언트 수를 제한합니다.  
