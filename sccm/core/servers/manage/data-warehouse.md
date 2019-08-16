---
title: 데이터 웨어하우스
titleSuffix: Configuration Manager
description: Configuration Manager에 대한 데이터 웨어하우스 서비스 지점 및 데이터베이스
ms.date: 05/09/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: aaf43e69-68b4-469a-ad58-9b66deb29057
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 95641ed36bb3847a3f7d39c4ad8d7296ecd11e77
ms.sourcegitcommit: 6b5a003256305c1f0cb605e52aeaaf19c23af5a9
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68956298"
---
#  <a name="the-data-warehouse-service-point-for-configuration-manager"></a>Configuration Manager에 대한 데이터 웨어하우스 서비스 지점

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1277922-->
데이터 웨어하우스 서비스 지점을 사용하여 Configuration Manager 배포에 대한 장기 기록 데이터를 저장하고 보고할 수 있습니다.

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  


데이터 웨어하우스는 최대 2TB의 데이터를 지원하며 변경 내용 추적을 위한 타임스탬프가 있습니다. 데이터 웨어하우스는 Configuration Manager 사이트 데이터베이스의 데이터를 데이터 웨어하우스 데이터베이스에 자동으로 동기화하여 데이터를 저장합니다. 그러면 이 정보를 보고 서비스 지점에서 액세스할 수 있습니다. 데이터 웨어하우스 데이터베이스에 동기화된 데이터는 3년 동안 유지됩니다. 주기적으로 기본 제공 작업은 3년보다 오래된 데이터를 제거합니다.

동기화되는 데이터에는 전역 데이터 및 사이트 데이터 그룹의 다음 항목이 포함됩니다.
- 인프라 상태
- 보안
- 준수
- 맬웨어   
- 소프트웨어 배포
- 인벤토리 세부 정보(그러나 인벤토리 기록은 동기화되지 않음)

사이트 시스템 역할을 설치하면 데이터 웨어하우스 데이터베이스가 설치 및 구성됩니다. 또한 여러 보고서가 설치되므로 이 데이터를 쉽게 검색하고 보고할 수 있습니다.

1810 버전부터 더 많은 테이블을 사이트 데이터베이스에서 데이터 웨어하우스로 동기화할 수 있습니다. 이렇게 변경하면 비즈니스 요구 사항에 따라 더 많은 보고서를 만들 수 있습니다.<!--1358870--> 



## <a name="prerequisites"></a>필수 구성 요소

- 이러한 데이터 웨어하우스 사이트 시스템 역할은 계층의 최상위 계층 사이트에서만 지원됩니다. 중앙 관리 사이트 또는 독립 기본 사이트를 예로 들 수 있습니다.  

- 사이트 시스템 역할을 설치하는 컴퓨터에 .NET Framework 4.5.2 이상 버전이 필요합니다.  

- **보고 서비스 지점 계정**에 데이터 웨어하우스 데이터베이스에 대한 **db_datareader** 권한을 부여합니다.  

- 데이터 웨어하우스 데이터베이스와 데이터를 동기화하기 위해 Configuration Manager는 사이트 시스템 역할의 계퓨터 계정을 사용합니다. 이 계정에는 다음 권한이 있어야 합니다.  

    - 데이터 웨어하우스 데이터베이스를 호스트하는 컴퓨터의 **Administrator**  

    - 데이터 웨어하우스 데이터베이스에 대한 **DB_Creator** 권한  

    - 최상위 계층 사이트의 데이터베이스에 대한 **실행** 권한이 있는 **DB_owner** 또는 **DB_reader**  

- 데이터 웨어하우스 데이터베이스에는 SQL Server 2012 이상이 필요합니다. 해당 버전은 Standard, Enterprise 또는 Datacenter일 수 있습니다. 데이터 웨어하우스에 대한 SQL Server 버전이 사이트 데이터베이스 서버와 같을 필요는 없습니다.<!--SCCMDocs issue 662-->  

- 웨어하우스 데이터베이스는 다음 SQL Server 구성을 지원합니다.  

    - 기본 또는 명명된 인스턴스  

    - SQL Server Always On 가용성 그룹  

    - SQL Server 장애 조치(failover) 클러스터  

- [분산 보기](/sccm/core/plan-design/hierarchy/database-replication#bkmk_distviews)를 사용하는 경우 데이터 웨어하우스 서비스 지점은 중앙 관리 사이트의 데이터베이스를 호스트하는 동일한 서버에 설치되어야 합니다.  

SQL Server 라이선스에 대한 자세한 내용은 [제품 및 라이선스 FAQ](/sccm/core/understand/product-and-licensing-faq)를 참조하세요. <!-- sms500967 -->

데이터 웨어하우스 데이터베이스의 크기를 사이트 데이터베이스와 동일하게 지정합니다. 데이터 웨어하우스는 처음에는 더 작지만 시간에 따라 커집니다. <!--SCCMDocs issue 756-->



## <a name="install"></a>설치

각 계층 구조는 해당 최상위 계층 사이트의 사이트 시스템에서 이 역할의 단일 인스턴스를 지원합니다. 웨어하우스에 대한 데이터베이스를 호스트하는 SQL Server는 사이트 시스템 역할에 로컬이거나 원격일 수 있습니다. 데이터 웨어하우스는 동일한 사이트에 설치된 보고 서비스 지점에서 작동합니다. 동일한 서버에 두 개의 사이트 시스템 역할을 설치할 필요가 없습니다.   

역할을 설치하려면 **사이트 시스템 역할 추가 마법사** 또는 **사이트 시스템 서버 만들기 마법사**를 사용합니다. 자세한 내용은 [사이트 시스템 역할 설치](/sccm/core/servers/deploy/configure/install-site-system-roles)를 참조하세요. 마법사의 **시스템 역할 선택** 페이지에서 **데이터 웨어하우스 서비스 지점** 역할을 선택합니다. 

역할을 설치하면 Configuration Manager에서 지정한 SQL Server 인스턴스에 데이터 웨어하우스 데이터베이스를 자동으로 만듭니다. 기존 데이터베이스의 이름을 지정하는 경우에는 Configuration Manager가 새 데이터베이스를 만들지 않습니다. 대신 사용자가 지정한 데이터베이스를 사용합니다. 이 프로세스는 [새 SQL Server로 데이터 웨어하우스 데이터베이스를 이동할 때](#move-the-database)와 같습니다.


### <a name="configure-properties"></a>속성 구성

#### <a name="general-page"></a>일반 페이지

- **SQL Server의 정규화된 도메인 이름**: 데이터 웨어하우스 서비스 지점 데이터베이스를 호스트하는 서버의 FQDN(정규화된 도메인 이름)을 지정합니다.  

- **SQL Server 인스턴스 이름(적용되는 경우)** : SQL Server의 기본 인스턴스를 사용하지 않는 경우 명명된 인스턴스를 지정합니다.  

- **데이터베이스 이름**: 데이터 웨어하우스 데이터베이스의 이름을 지정합니다. Configuration Manager는 이 이름으로 데이터 웨어하우스 데이터베이스를 만듭니다. SQL Server 인스턴스에 이미 존재하는 데이터베이스 이름을 지정하면 Configuration Manager는 해당 데이터베이스를 사용합니다.  

- **연결에 사용되는 SQL Server 포트**: 데이터 웨어하우스 데이터베이스를 호스트하는 SQL Server에서 사용된 TCP/IP 포트 번호를 지정합니다. 데이터 웨어하우스 동기화 서비스는 이 포트를 사용하여 데이터 웨어하우스 데이터베이스에 연결합니다. 기본적으로 SQL Server 포트 **1433**을 통신에 사용합니다.  

- **데이터 웨어하우스 서비스 지점 계정**: 1802 버전부터, 데이터 웨어하우스 데이터베이스에 연결할 때 SQL Server Reporting Services가 사용하는 **사용자 이름**을 설정합니다.  


#### <a name="synchronization-schedule-page"></a>동기화 일정 페이지
*1806 및 그 이전 버전에 적용*

- **시작 시간**: 데이터 웨어하우스 동기화를 시작할 시간을 지정합니다.  

- **되풀이 패턴**

    - **매일**: 동기화가 매일 실행되도록 지정합니다.  

    - **매주**: 매주 동기화를 되풀이할 요일을 지정합니다.


#### <a name="synchronization-settings-page"></a>동기화 설정 페이지
*버전 1810 이상에 적용*

- **데이터 동기화 사용자 지정 설정**: **테이블 선택** 옵션을 선택합니다. [데이터베이스 테이블] 창에서 데이터 웨어하우스 데이터베이스에 동기화할 테이블 이름을 선택합니다. 필터를 사용하여 이름별로 검색하거나 드롭다운 목록을 선택하여 특정 그룹을 선택합니다. 저장을 마치면 **확인**을 선택합니다.  

    > [!Note]  
    > 역할에서 기본적으로 선택하는 테이블은 제거할 수 없습니다.  

- **시작 시간**: 데이터 웨어하우스 동기화를 시작할 시간을 지정합니다.  

- **되풀이 패턴**

    - **매일**: 동기화가 매일 실행되도록 지정합니다.  

    - **매주**: 매주 동기화를 되풀이할 요일을 지정합니다.



## <a name="reporting"></a>보고

데이터 웨어하우스 서비스 지점을 설치하면 사이트에 대한 보고 서비스 지점에서 여러 보고서를 사용할 수 있습니다. 보고 서비스 지점을 설치하기 전에 데이터 웨어하우스 서비스 지점을 설치하는 경우 나중에 보고 서비스 지점을 설치할 때 보고서가 자동으로 추가됩니다.

> [!WARNING]  
> 1802 버전부터 데이터 웨어하우스 지점이 대체 자격 증명을 지원합니다.<!--507334--> 이전 버전의 Configuration Manager에서 업그레이드한 경우 SQL Server Reporting Services가 데이터 웨어하우스 데이터베이스에 연결하는 데 사용할 자격 증명을 지정해야 합니다. 자격 증명을 추가해야 데이터 웨어하우스 보고서가 열립니다. 
> 
> 계정을 지정하려면 역할 속성에서 데이터 웨어하우스 서비스 지점 계정에 대해 **사용자 이름**을 설정합니다. 자세한 내용은 [속성 구성](#configure-properties)을 참조하세요. 

데이터 웨어하우스 사이트 시스템 역할에는 **데이터 웨어하우스** 범주에 속한 다음 보고서가 포함됩니다.  

- **애플리케이션 배포 - 기록**: 특정 애플리케이션 및 컴퓨터에 대한 애플리케이션 배포 정보를 확인합니다.  

- **Endpoint Protection 및 소프트웨어 업데이트 규정 준수 - 기록**: 소프트웨어 업데이트가 누락된 컴퓨터를 확인합니다.  

- **일반 하드웨어 인벤토리 - 기록**: 특정 컴퓨터에 대한 모든 하드웨어 인벤토리를 확인합니다.  

- **일반 소프트웨어 인벤토리 - 기록**: 특정 컴퓨터에 대한 모든 소프트웨어 인벤토리를 확인합니다.  

- **인프라 상태 개요 - 기록**: Configuration Manager 인프라의 상태 개요를 표시합니다.  

- **검색된 맬웨어 목록 - 기록**: 조직에서 검색된 맬웨어를 확인합니다.  

- **소프트웨어 배포 요약 - 기록**: 특정 보급 알림 및 컴퓨터에 대한 소프트웨어 배포 요약입니다.  



## <a name="site-expansion"></a>사이트 확장

기존 독립 실행형 기본 사이트를 확장하기 위해 중앙 관리 사이트를 설치하려면 먼저 데이터 웨어하우스 서비스 지점 역할을 제거합니다. 중앙 관리 사이트를 설치한 후 중앙 관리 사이트에서 사이트 시스템 역할을 설치할 수 있습니다.  

이 경우 데이터 웨어하우스 데이터베이스의 이동과 달리 기본 사이트에서 이전에 동기화한 기록 데이터가 손실됩니다. 기본 사이트에서 데이터베이스를 백업하여 중앙 관리 사이트에서 복원하는 기능은 지원되지 않습니다.



## <a name="move-the-database"></a>데이터베이스 이동

데이터 웨어하우스 데이터베이스를 새 SQL Server로 이동하려면 다음 단계를 사용합니다.  

1. SQL Server Management Studio를 사용하여 데이터 웨어하우스 데이터베이스를 백업합니다. 그런 다음 데이터 웨어하우스를 호스트하는 새 컴퓨터의 SQL Server에 해당 데이터베이스를 복원합니다.  

    > [!NOTE]  
    > 데이터베이스를 새 서버로 복원한 후 새 데이터 웨어하우스 데이터베이스의 데이터베이스 액세스 권한이 원래 데이터 웨어하우스 데이터베이스와 동일한지 확인합니다.  

2. Configuration Manager 콘솔을 사용하여 현재 서버에서 데이터 웨어하우스 서비스 지점 역할을 제거합니다.  

3. 데이터 웨어하우스 서비스 지점을 다시 설치합니다. 복원한 데이터 웨어하우스 데이터베이스를 호스트하는 새 SQL Server 및 인스턴스의 이름을 지정합니다.  

4. 사이트 시스템 역할이 설치된 후 이동이 완료됩니다.  



## <a name="troubleshooting"></a>문제 해결 

### <a name="log-files"></a>로그 파일 

다음 로그를 사용하여 데이터 웨어하우스 서비스 지점 설치 또는 데이터 동기화 문제를 조사할 수 있습니다.

- **DWSSMSI.log** 및 **DWSSSetup.log**: 데이터 웨어하우스 서비스 지점을 설치할 때 발생하는 오류를 조사하려면 이러한 로그를 사용합니다.  

- **Microsoft.ConfigMgrDataWarehouse.log**: 사이트 데이터베이스와 데이터 웨어하우스 데이터베이스 간의 데이터 동기화를 조사하려면 이 로그를 사용합니다.  


### <a name="set-up-failure"></a>설치 실패 

데이터 웨어하우스 서비스 지점 역할이 원격 서버에 설치한 첫 번째 항목인 경우 데이터 웨어하우스에 대해 설치가 실패합니다.  

#### <a name="workaround"></a>해결 방법 
데이터 웨어하우스 서비스 지점을 설치하려는 컴퓨터가 이미 하나 이상의 다른 역할을 호스트하고 있는지 확인합니다.  


### <a name="synchronization-failed-to-populate-schema-objects"></a>동기화에서 스키마 개체를 채우지 못함 

**Microsoft.ConfigMgrDataWarehouse.log**에 다음 메시지가 표시되고 동기화에 실패함: `failed to populate schema objects`

#### <a name="workaround"></a>해결 방법 
사이트 시스템 역할의 컴퓨터 계정이 데이터 웨어하우스 데이터베이스에 대한 **db_owner**인지 확인합니다.


### <a name="reports-fail-to-open"></a>보고서를 열지 못함

데이터 웨어하우스 데이터베이스 및 보고 서비스 지점이 서로 다른 사이트 시스템에 있는 경우 데이터 웨어하우스 보고서가 열리지 않습니다.  

#### <a name="workaround"></a>해결 방법
**보고 서비스 지점 계정**에 데이터 웨어하우스 데이터베이스에 대한 **db_datareader** 권한을 부여합니다.


### <a name="error-opening-reports"></a>보고서 열기 오류

데이터 웨어하우스 보고서를 열 때 다음 오류가 반환됩니다.

```
An error has occurred during report processing. (rsProcessingAborted)
Cannot create a connection to data source 'AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_'. (rsErrorOpeningConnection)
A connection was successfully established with the server, but then an error occurred during the pre-login handshake. (provider: SSL Provider, error: 0 - The certificate chain was issued by an authority that is not trusted.)
```

#### <a name="workaround"></a>해결 방법 
다음 단계에 따라 인증서를 구성합니다.

1. 데이터 웨어하우스 데이터베이스를 호스트하는 컴퓨터에서 다음을 수행합니다.  

    1. IIS를 열고 **서버 인증서**를 선택한 다음, **자체 서명된 인증서 만들기**를 마우스 오른쪽 단추로 클릭합니다. 그런 다음, "알기 쉬운" 인증서 이름을 **데이터 웨어하우스 SQL Server 식별 인증서**로 지정합니다. 인증서 저장소를 **개인**으로 선택합니다.  

    2. **SQL Server 구성 관리자**를 엽니다. **SQL Server 네트워크 구성**에서 **MSSQLSERVER 용 프로토콜** 아래의 **속성**을 마우스 오른쪽 단추로 클릭하여 선택합니다. **인증서** 탭에서 **데이터 웨어하우스 SQL Server 식별 인증서**를 인증서로 선택하고 변경 내용을 저장합니다.  

    3. **SQL Server 구성 관리자**의 **SQL Server 서비스**에서 **SQL Server 서비스**를 다시 시작합니다. SQL Reporting Services가 또한 데이터 웨어하우스 데이터베이스를 호스트하는 서버에 설치된 경우 **Reporting Services** 서비스도 다시 시작합니다.  

    4. MMC(Microsoft Management Console)를 열고 **인증서** 스냅인을 추가합니다. 로컬 머신의 **컴퓨터 계정**을 선택합니다. **개인** 폴더를 확장하고 **인증서**를 선택합니다. **데이터 웨어하우스 SQL Server 식별 인증서**를 **DER로 인코딩된 이진 X.509(.CER)** 파일로 내보냅니다.  

2. SQL Server Reporting Services를 호스트하는 컴퓨터에서 MMC를 열고 **인증서** 스냅인을 추가합니다. **컴퓨터 계정**을 선택합니다. **신뢰할 수 있는 루트 인증 기관** 폴더에서 **데이터 웨어하우스 SQL Server 식별 인증서**를 가져옵니다.  



## <a name="data-flow"></a>데이터 흐름   

![데이터 웨어하우스의 사이트 구성 요소 간의 논리적 데이터 흐름을 보여 주는 다이어그램](./media/datawarehouse.png)

#### <a name="data-storage-and-synchronization"></a>데이터 스토리지 및 동기화

| 단계   | 세부 정보  |
|--------|----------|  
| **1**  | 사이트 서버는 데이터를 전송하고 사이트 데이터베이스에 저장합니다. |  
| **2**  | 일정 및 구성에 따라 데이터 웨어하우스 서비스 지점은 사이트 데이터베이스에서 데이터를 가져옵니다. |  
| **3**  | 데이터 웨어하우스 서비스 지점은 동기화된 데이터 복사본을 전송하고 데이터 웨어하우스 데이터베이스에 저장합니다. |  


#### <a name="reporting"></a>보고

| 단계   | 세부 정보  |
|--------|----------|  
| **A**  | 사용자는 기본 제공 보고서를 사용하여 데이터를 요청합니다. 이 요청은 SQL Server Reporting Services를 통해 보고 서비스 지점에 전달됩니다. |  
| **B**  | 대부분의 보고서는 현재 정보에 대한 것이며, 사이트 데이터베이스에 대해 이러한 요청이 실행됩니다. |  
| **C**  | 보고서에서 기록 데이터를 요청하는 경우 *범주*가 **데이터 웨어하우스**인 보고서 중 하나를 사용하여 데이터 웨어하우스 데이터베이스에 대해 요청이 실행됩니다. |  
