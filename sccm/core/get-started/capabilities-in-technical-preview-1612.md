---
title: 기술 미리 보기 1612의 기능
titleSuffix: Configuration Manager
description: Configuration Manager용 Technical Preview 버전 1612에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bceab2e8-2f05-4a17-9ac8-a7a558670fb7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 67ced156211acad8ce27b3f043cbab7aa0adc2f6
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75805050"
---
# <a name="capabilities-in-technical-preview-1612-for-configuration-manager"></a>Configuration Manager용 Technical Preview 1612의 기능

*적용 대상: Configuration Manager(기술 미리 보기 분기)*



이 문서에서는 Configuration Manager용 Technical Preview 버전 1612에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대한 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="the-data-warehouse-service-point"></a>데이터 웨어하우스 서비스 지점
Technical Preview 버전 1612부터 데이터 웨어하우스 서비스 지점을 사용하여 Configuration Manager 배포에 대한 장기 기록 데이터를 저장하고 보고할 수 있습니다. 이 작업은 Configuration Manager 사이트 데이터베이스에서 데이터 웨어하우스 데이터베이스로의 자동화된 동기화를 통해 수행됩니다. 이 정보는 보고 서비스 지점에서 액세스할 수 있습니다.

기본적으로 새 사이트 시스템 역할을 설치하면 Configuration Manager에서 지정한 SQL Server 인스턴스에 데이터 웨어하우스 데이터베이스를 자동으로 만듭니다. 데이터 웨어하우스는 최대 2TB의 데이터를 지원하며 변경 내용 추적을 위한 타임스탬프가 있습니다.  기본적으로 사이트 데이터베이스에서 동기화되는 데이터에는 글로벌 데이터, 사이트 데이터, Global_Proxy, 클라우드 데이터 및 데이터베이스 뷰에 대한 데이터 그룹이 포함됩니다. 동기화되는 항목을 수정하여 추가 테이블을 포함하거나 기본 복제 집합에서 특정 테이블을 제외할 수도 있습니다.
동기화되는 기본 데이터에는 다음에 대한 정보가 포함됩니다.
- 인프라 상태
- 보안
- 준수
- 맬웨어   
- 소프트웨어 배포
- 인벤토리 세부 정보(그러나 인벤토리 기록은 동기화되지 않음)

데이터 웨어하우스 데이터베이스 설치 및 구성 외에도, 이 데이터를 쉽게 검색하고 보고할 수 있도록 몇 가지 새 보고서가 설치됩니다.

### <a name="data-warehouse-dataflow"></a>데이터 웨어하우스 데이터 흐름   
![Datawarehouse_flow](./media/datawarehouse.png)

| 단계         | 세부 정보  |
|:------:|-----------|  
| **1** | 사이트 서버는 데이터를 전송하고 사이트 데이터베이스에 저장합니다.  |  
| **2** | 일정 및 구성에 따라 데이터 웨어하우스 서비스 지점은 사이트 데이터베이스에서 데이터를 가져옵니다.  |  
| **3** | 데이터 웨어하우스 서비스 지점은 동기화된 데이터 복사본을 전송하고 데이터 웨어하우스 데이터베이스에 저장합니다. |  
| **A** | 기본 제공 보고서를 사용하여 SQL Server Reporting Services를 통해 Reporting Services에 전달되는 데이터 요청이 수행됩니다. |  
| **B** | 대부분의 보고서는 현재 정보에 대한 것이며, 사이트 데이터베이스에 대해 이러한 요청이 실행됩니다. |  
| **C** | 보고서에서 기록 데이터를 요청하는 경우 *범주*가 **데이터 웨어하우스**인 보고서 중 하나를 사용하여 데이터 웨어하우스 데이터베이스에 대해 요청이 실행됩니다.   |  

### <a name="prerequisites-for-the-data-warehouse-service-point-and-database"></a>데이터 웨어하우스 서비스 지점 및 데이터베이스에 대한 필수 조건
- 계층 구조에 Reporting Services 지점 사이트 시스템 역할이 설치되어 있어야 합니다.
- 사이트 시스템 역할을 설치하는 컴퓨터에 .NET Framework 4.5.2 이상 버전이 필요합니다.
- 사이트 시스템 역할을 설치하는 컴퓨터의 컴퓨터 계정에 데이터 웨어하우스 데이터베이스를 호스트하는 컴퓨터에 대한 로컬 관리자 권한이 있어야 합니다.
- 사이트 시스템 역할을 설치하는 데 사용하는 관리 계정은 데이터 웨어하우스 데이터베이스를 호스트할 SQL Server 인스턴스에서 DBO여야 합니다.  
- 다음 데이터베이스가 지원됩니다.
  - SQL Server 2012 이상, Enterprise 또는 Datacenter Edition
  - 기본 또는 명명된 인스턴스
  - *SQL Server 클러스터* 이 구성은 작동해야 하지만 테스트되지 않았으며 최대한 지원하려고 시도될 뿐입니다.
  - 사이트 데이터베이스 또는 Reporting Services 지점 데이터베이스와 함께 배치된 경우. 그러나 별도 서버에 설치하는 것이 좋습니다.  
- *보고 서비스 지점 계정*으로 사용되는 계정은 데이터 웨어하우스 데이터베이스에 대한 **db_datareader** 권한이 있어야 합니다.  
- *SQL Server AlwaysOn 가용성 그룹*에서는 데이터베이스가 지원되지 않습니다.

### <a name="install-the-data-warehouse"></a>데이터 웨어하우스 설치
**사이트 시스템 역할 추가 마법사** 또는 **사이트 시스템 서버 만들기 마법사**를 사용하여 중앙 관리 사이트 또는 기본 사이트에 데이터 웨어하우스 사이트 시스템 역할을 설치합니다. 자세한 내용은 [사이트 시스템 역할 설치](/sccm/core/servers/deploy/configure/install-site-system-roles)를 참조하세요. 계층 구조는 이 역할의 여러 인스턴스를 지원하지만 각 사이트에서 하나의 인스턴스만 지원됩니다.  

역할을 설치하면 Configuration Manager에서 지정한 SQL Server 인스턴스에 데이터 웨어하우스 데이터베이스를 자동으로 만듭니다. [데이터 웨어하우스 데이터베이스를 새 SQL Server로 이동](#move-the-data-warehouse-database)하는 경우와 같이 기존 데이터베이스의 이름을 지정하는 경우 Configuration Manager는 새 데이터베이스를 생성하지 않고 지정한 데이터베이스를 대신 사용합니다.

#### <a name="configurations-used-during-installation"></a>설치 중에 사용되는 구성
다음 정보를 사용하여 사이트 시스템 역할 설치를 완료할 수 있습니다.

**시스템 역할 선택** 페이지:  
마법사에서 데이터 웨어하우스 서비스 지점을 선택하고 설치하는 옵션이 표시되려면 Reporting Services 지점을 설치한 상태여야 합니다.

**일반** 페이지: 다음 일반적인 정보가 필요합니다.
- **Configuration Manager 데이터베이스 설정:**   
  - **서버 이름** - 사이트 데이터베이스를 호스트하는 서버의 FQDN을 지정합니다. SQL Server의 기본 인스턴스를 사용하지 않는 경우 FQDN 뒤에 인스턴스를 다음과 같은 형식으로 지정해야 합니다. ***&lt;Sqlserver_FQDN>\&lt;Instance_name>***
  - **데이터베이스 이름** - 사이트 데이터베이스의 이름을 지정합니다.
  - **확인** - 사이트 데이터베이스에 대한 연결이 성공했는지 확인하려면 **확인**을 클릭합니다.
</br></br>
- **데이터 웨어하우스 데이터베이스 설정:**
  - **서버 이름** - 데이터 웨어하우스 서비스 지점 및 데이터베이스를 호스트하는 서버의 FQDN을 지정합니다. SQL Server의 기본 인스턴스를 사용하지 않는 경우 FQDN 뒤에 인스턴스를 다음과 같은 형식으로 지정해야 합니다. ***&lt;Sqlserver_FQDN>\&lt;Instance_name>***
  - **데이터베이스 이름** - 데이터 웨어하우스 데이터베이스의 FQDN을 지정합니다.  Configuration Manager는 이 이름으로 데이터베이스를 만듭니다. SQL Server 인스턴스에 이미 존재하는 데이터베이스 이름을 지정하면 Configuration Manager는 해당 데이터베이스를 사용합니다.
  - **확인** - 사이트 데이터베이스에 대한 연결이 성공했는지 확인하려면 **확인**을 클릭합니다.

**동기화 설정** 페이지:   
- **데이터 설정:**
  - **동기화할 복제 그룹** – 동기화할 데이터 그룹을 선택합니다. 다양한 유형의 데이터 그룹에 대한 자세한 내용은 [사이트 간 데이터 전송](/sccm/core/servers/manage/data-transfers-between-sites)에서 [데이터베이스 복제](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_dbrep) 및 **분산 뷰**를 참조하세요.
  - **동기화에 포함되는 테이블** – 동기화할 각 추가 테이블의 이름을 지정합니다. 여러 테이블을 구분하려면 쉼표를 사용합니다. 이러한 테이블은 선택한 복제 그룹 외에도 사이트 데이터베이스에서 동기화됩니다.
  - **동기화에서 제외되는 테이블** -동기화하는 복제 그룹의 개별 테이블 이름을 지정합니다. 지정한 테이블이 제외됩니다. 여러 테이블을 구분하려면 쉼표를 사용합니다.
- **동기화 설정:**
  - **동기화 간격(분)** - 값을 분 단위로 지정합니다. 간격에 도달하면 새 동기화가 시작됩니다. 60분에서 1440분(24시간) 사이의 범위가 지원됩니다.
  - **일정** - 동기화를 실행하려는 날짜를 지정합니다.

**보고 지점 액세스**:   
데이터 웨어하우스 역할이 설치된 후 *보고 서비스 지점 계정*으로 사용되는 계정에게 데이터 웨어하우스 데이터베이스에 대한 **db_datareader** 권한이 있는지 확인합니다.

#### <a name="troubleshoot-installation-and-data-synchronization"></a>설치 및 데이터 동기화 문제 해결
다음 로그를 사용하여 데이터 웨어하우스 서비스 지점 설치 또는 데이터 동기화 문제를 조사할 수 있습니다.
- **DWSSMSI.log** 및 **DWSSSetup.log** - 데이터 웨어하우스 서비스 지점을 설치할 때 발생하는 오류를 조사하려면 이 로그를 사용합니다.
- **Microsoft.ConfigMgrDataWarehouse.log** - 사이트 데이터베이스와 데이터 웨어하우스 데이터베이스 간의 데이터 동기화를 조사하려면 이 로그를 사용합니다.

### <a name="reporting"></a>보고
데이터 웨어하우스 사이트 시스템 역할을 설치한 후 *범주*가 **데이터 웨어하우스**인 Reporting Services 지점에 대해 다음 보고서를 사용할 수 있습니다.

|보고서                   | 세부 정보                                  |
|-------------------------|------------------------------------------|
| **애플리케이션 배포 보고서** | 특정 애플리케이션 및 컴퓨터에 대한 애플리케이션 배포 정보를 확인합니다.|
| **Endpoint Protection 및 소프트웨어 업데이트 준수 보고서**   | 소프트웨어 업데이트가 누락된 컴퓨터를 확인합니다.|
| **일반 하드웨어 인벤토리 보고서**  | 특정 컴퓨터에 대한 모든 하드웨어 인벤토리를 확인합니다.|
| **일반 소프트웨어 인벤토리 보고서**  | 특정 컴퓨터에 대한 모든 소프트웨어 인벤토리를 확인합니다.|
| **인프라 상태 개요**  |Configuration Manager 인프라의 상태 개요를 표시합니다.|
| **검색된 맬웨어 목록**  |조직에서 검색된 맬웨어를 확인합니다.|
| **소프트웨어 배포 요약 보고서** | 특정 보급 알림 및 컴퓨터에 대한 소프트웨어 배포 요약입니다.|

### <a name="move-the-data-warehouse-database"></a>데이터 웨어하우스 데이터베이스 이동
데이터 웨어하우스 데이터베이스를 새 SQL Server로 이동하려면 다음 단계를 사용합니다.

1. 현재 데이터베이스 구성을 검토하고 다음을 비롯한 구성 세부 정보를 기록합니다.  
   - 동기화하는 데이터 그룹
   - 동기화에 포함하거나 제외하는 테이블       

   데이터베이스를 새 서버로 복원하고 사이트 시스템 역할을 다시 설치한 후 이러한 데이터 그룹 및 테이블을 다시 구성합니다.  

2. SQL Server Management Studio를 사용하여 데이터 웨어하우스 데이터베이스를 백업한 다음 데이터 웨어하우스를 호스트할 새 컴퓨터에서 해당 데이터베이스를 SQL Server로 복원합니다.

   데이터베이스를 새 서버로 복원한 후 새 데이터 웨어하우스 데이터베이스의 데이터베이스 액세스 권한이 원래 데이터 웨어하우스 데이터베이스와 동일한지 확인합니다.

3. Configuration Manager 콘솔을 사용하여 현재 서버에서 데이터 웨어하우스 서비스 지점 사이트 시스템 역할을 제거합니다.

4. 새 데이터 웨어하우스 서비스 지점을 설치하고 복원한 데이터 웨어하우스 데이터베이스를 호스트하는 새 SQL Server 및 인스턴스의 이름을 지정합니다.

5. 사이트 시스템 역할이 설치된 후 이동이 완료됩니다.

다음 Configuration Manager 로그를 검토하여 사이트 시스템 역할이 성공적으로 다시 설치되었는지 확인할 수 있습니다.  
- **DWSSMSI.log** 및 **DWSSSetup.log** - 데이터 웨어하우스 서비스 지점을 설치할 때 발생하는 오류를 조사하려면 이 로그를 사용합니다.
- **Microsoft.ConfigMgrDataWarehouse.log** - 사이트 데이터베이스와 데이터 웨어하우스 데이터베이스 간의 데이터 동기화를 조사하려면 이 로그를 사용합니다.


## <a name="content-library-cleanup-tool"></a>콘텐츠 라이브러리 정리 도구
Technical Preview 버전 1612부터 새로운 명령줄 도구(**ContentLibraryCleanup.exe**)를 사용하여 배포 지점의 패키지 또는 애플리케이션과 더 이상 연결되지 않은 콘텐츠(분리된 콘텐츠)를 제거할 수 있습니다. 이 도구를 콘텐츠 라이브러리 정리 도구라고 합니다.

이 도구는 도구를 실행할 때 지정한 배포 지점의 콘텐츠에만 영향을 주며 사이트 서버의 콘텐츠 라이브러리에서 콘텐츠를 제거할 수 없습니다.

Technical Preview 1612를 설치한 후 Technical Preview 사이트 서버의 \*%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* 폴더에서 **ContentLibraryCleanup.exe**를 찾을 수 있습니다.

이 Technical Preview와 함께 릴리스된 도구는 이전 Configuration Manager 제품에 대해 릴리스된 이전 버전의 유사 도구를 대체합니다. 이 도구 버전은 2017년 3월 1일 후에 작동이 중단되지만 이 도구가 현재 분기 또는 프로덕션 준비 대역 외 릴리스의 일부로 릴리스될 때까지 이후 Technical Preview와 함께 새 버전이 릴리스됩니다.

### <a name="requirements"></a>요구 사항  
- 이 도구는 배포 지점을 호스트하는 컴퓨터에서 직접 실행하거나 다른 서버에서 원격으로 실행할 수 있습니다. 한 번에 하나의 배포 지점에 대해서만 도구를 실행할 수 있습니다.
- 도구를 실행하는 사용자 계정에 직접 Configuration Manager 계층 구조의 전체 관리자와 동일한 역할 기반 관리 권한이 있어야 합니다.  사용자 계정에 전체 관리자 권한이 있는 Windows 보안 그룹의 구성원으로 권한이 부여된 경우에는 도구가 작동하지 않습니다.

### <a name="modes-of-operation"></a>작동 모드
다음 두 가지 모드로 도구를 실행할 수 있습니다.
1. **What-If 모드**:   
   **/delete** 스위치를 지정하지 않을 경우 도구는 What-If 모드로 실행되며 배포 지점에서 삭제되는 콘텐츠를 식별하지만 실제로 데이터를 삭제하지는 않습니다.

   - 이 모드로 도구를 실행하면 삭제되는 콘텐츠에 대한 정보가 도구 로그 파일에 자동으로 기록됩니다. 각 잠재적 삭제를 확인하는 메시지가 사용자에게 표시되지 않습니다.
   - 기본적으로 로그 파일은 도구를 실행하는 컴퓨터의 사용자 temp 폴더에 기록되지만 /log 스위치를 사용하여 로그 파일을 다른 위치로 리디렉션할 수 있습니다.  
   </br>

   /delete 스위치와 함께 도구를 실행하기 전에 이 모드로 도구를 실행하고 결과 로그 파일을 검토하는 것이 좋습니다.  

2. **삭제 모드**: **/delete** 스위치와 함께 도구를 실행하면 도구가 삭제 모드에서 실행됩니다.

   - 이 모드로 도구를 실행하는 경우 지정한 배포 지점에서 발견된 분리된 콘텐츠를 배포 지점의 콘텐츠 라이브러리에서 삭제할 수 있습니다.
   -  각 파일을 삭제하기 전에 파일을 삭제할 것인지 확인하는 메시지가 사용자에게 표시됩니다.  **Y**(예) 또는 **N**(아니요)을 선택하거나, 추가 메시지를 건너뛰고 분리된 콘텐츠를 모두 삭제하려면 **모두 예**를 선택할 수 있습니다.  
   </br>

   /delete 스위치와 함께 도구를 실행하기 전에 What-If 모드로 도구를 실행하고 결과 로그 파일을 검토하는 것이 좋습니다.  

두 모드 중 하나로 콘텐츠 라이브러리 정리 도구를 실행하면 도구가 실행되는 모드, 배포 지점 이름, 작업 날짜 및 시간을 포함하는 이름의 로그가 자동으로 생성됩니다. 도구가 완료되면 로그 파일이 자동으로 열립니다. 기본적으로 이 로그는 도구를 실행하는 컴퓨터의 사용자 **temp** 폴더에 기록되지만 명령줄 스위치를 사용하여 로그 파일을 네트워크 공유 등의 다른 위치로 리디렉션할 수 있습니다.   


### <a name="run-the-tool"></a>도구 실행
도구를 실행하려면:
1. 관리 명령 프롬프트를 **ContentLibraryCleanup.exe**가 포함된 폴더로 엽니다.  
2. 필수 명령줄 스위치와 사용할 선택적 스위치를 포함하는 명령줄을 입력합니다.

**알려진 문제** 도구가 실행되면 패키지 또는 배포가 실패했거나 진행 중인 경우 다음과 같은 오류가 반환될 수 있습니다.
-  *System.InvalidOperationException: \<packageID> 패키지가 완전히 설치되지 않으므로 이 콘텐츠 라이브러리가 바로 정리될 수 없습니다.*

**해결 방법:** 없음 콘텐츠가 진행 중이거나 배포에 실패한 경우 도구는 분리된 파일을 안정적으로 식별할 수 없습니다. 따라서 해당 문제가 해결될 때까지 도구를 통해 콘텐츠를 정리할 수 없습니다.



### <a name="command-line-switches"></a>명령줄 스위치  
다음 명령줄 스위치를 순서에 관계없이 사용할 수 있습니다.   

|스위치|세부 정보|
|---------|-------|
|**/delete**  |**선택 사항** </br> 배포 지점에서 콘텐츠를 삭제하려는 경우 이 스위치를 사용합니다. 콘텐츠를 삭제하기 전에 확인 메시지가 표시됩니다. </br></br> 이 스위치를 사용하지 않으면 도구는 삭제되는 콘텐츠에 대한 결과를 기록하지만 배포 지점에서 콘텐츠를 삭제하지는 않습니다. </br></br> 예제: ***ContentLibraryCleanup.exe /dp server1.contoso.com /delete*** |
| **/q**       |**선택 사항** </br> 모든 메시지(예: 콘텐츠를 삭제할 때 표시되는 메시지)를 표시하지 않는 자동 모드로 도구를 실행하고 자동으로 로그 파일을 열지 않습니다. </br></br> 예제: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;배포 지점 FQDN>**  | **필수** </br> 정리하려는 배포 지점의 FQDN(정규화된 도메인 이름)을 지정합니다. </br></br> 예제:  ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/ps &lt;기본 사이트 FQDN>**       | 기본 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **선택 사항**입니다.</br>보조 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **필수**입니다. </br></br> 배포 지점이 속하는 기본 사이트 또는 배포 지점이 보조 사이트에 있는 경우 부모 기본 사이트의 FQDN을 지정합니다. </br></br> 예제: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;기본 사이트 코드>**  | 기본 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **선택 사항**입니다.</br>보조 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **필수**입니다. </br></br> 배포 지점이 속하는 기본 사이트 또는 배포 지점이 보조 사이트에 있는 경우 부모 기본 사이트의 사이트 코드를 지정합니다.</br></br> 예제: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/log \<log file directory>**       |**선택 사항** </br> 로그 파일을 배치할 디렉터리를 지정합니다. 로컬 드라이브 또는 네트워크 공유일 수 있습니다.</br></br> 이 스위치를 사용하지 않으면 로그 파일은 자동으로 사용자 temp 폴더에 배치됩니다.</br></br> 로컬 드라이브의 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /log C:\Users\Administrator\Desktop*** </br></br>네트워크 공유의 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /log \\&lt;share>\&lt;folder>***|


## <a name="improvements-for-in-console-search"></a>콘솔 내 검색의 향상된 기능
User Voice 피드백에 따라 콘솔 내 검색에 대한 다음과 같은 향상 기능이 추가되었습니다.
- **개체 경로:**  
  이제 많은 개체가 **개체 경로**라는 새 열을 지원합니다.  이 열을 검색하고 표시 결과에 포함하는 경우 각 개체의 경로를 볼 수 있습니다. 예를 들어 애플리케이션 노드에서 앱 검색을 실행하고 하위 노드도 검색하는 경우 결과 창의 *개체 경로* 열에 반환된 각 개체의 경로가 표시됩니다.   

- **검색 텍스트 보존:**  
  검색 텍스트 상자에 텍스트를 입력한 후 하위 노드 및 현재 노드 검색 간을 전환하는 경우 입력한 텍스트가 이제 보존되어 다시 입력하지 않고 새 검색에 사용할 수 있습니다.

- **하위 노드 검색 결정 보존:**  
  이제 *현재 노드* 또는 *모든 하위 노드* 검색에 대해 선택한 옵션이 작업하는 노드를 변경할 때 유지됩니다.   이 새로운 동작으로 인해 콘솔 내에서 이동할 때 지속적으로 결정을 다시 설정할 필요가 없습니다.  기본적으로 콘솔을 열 때 옵션은 현재 노드만 검색입니다.

## <a name="prevent-installation-of-an-application-if-a-specified-program-is-running"></a>지정한 프로그램이 실행되는 경우 애플리케이션 설치를 차단합니다.
이제 배포 유형 속성에서 실행할 경우 애플리케이션 설치를 차단하는 실행 파일 목록(확장명 .exe)을 구성할 수 있습니다. 설치를 시도한 후 설치를 차단하는 프로세스를 닫을지 묻는 대화 상자가 사용자에게 표시됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
실행 파일 목록을 구성하려면
1. 배포 유형의 속성 페이지에서 **설치 관리자 처리** 탭을 선택합니다.
2. **추가**를 클릭하여 다른 실행 파일 중 하나를 목록에 추가합니다(예: **Edge.exe**).
3. **확인**을 클릭하여 배포 유형 속성 대화 상자를 닫습니다.

이제 사용자 또는 디바이스에 이 애플리케이션을 배포하고 추가한 실행 파일 중 하나가 실행되는 경우 애플리케이션이 실행 중이므로 설치에 실패했다고 알리는 소프트웨어 센터 대화 상자가 최종 사용자에게 표시됩니다.

## <a name="new-windows-hello-for-business-notification-for-end-users"></a>최종 사용자에 대한 새 비즈니스용 Windows Hello 알림

새 Windows 10 알림은 비즈니스용 Windows Hello 설치를 완료하기 위해 추가 작업(예: PIN 설정)을 수행해야 한다고 최종 사용자에게 알립니다.

## <a name="windows-store-for-business-support-in-configuration-manager"></a>Configuration Manager의 비즈니스용 Windows 스토어 지원

이제 배포 목적이 **사용 가능**인 온라인에서 사용이 허가된 앱을 비즈니스용 Windows 스토어에서 Configuration Manager 클라이언트를 실행하는 PC로 배포할 수 있습니다.
자세한 내용은 [Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱 관리](https://docs.microsoft.com/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)를 참조하세요.

이 기능에 대한 지원은 현재 Windows 10 RS2 미리 보기 빌드를 실행하는 PC에만 제공됩니다.

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>작업 순서가 실패할 경우 이전 페이지로 돌아가기
이제 작업 순서를 실행하고 오류가 발생할 때 이전 페이지로 돌아갈 수 있습니다. 이 릴리스 이전에는 오류가 발생할 경우 작업 순서를 다시 시작해야 했습니다. 예를 들어 다음 시나리오에서 **이전** 단추를 사용할 수 있습니다.

- Windows PE에서 컴퓨터를 시작할 경우 작업 순서가 제공되기 전에 작업 순서 부트스트랩 대화 상자가 표시될 수 있습니다. 이 시나리오에서 다음을 클릭하면 사용 가능한 작업 순서가 없다는 메시지와 함께 작업 순서의 최종 페이지가 표시됩니다. 이제 **이전**을 클릭하여 사용 가능한 작업 순서를 다시 검색할 수 있습니다. 작업 순서를 사용할 수 있을 때까지 이 프로세스를 반복할 수 있습니다.
- 작업 순서를 실행하지만 배포 지점에서 종속 콘텐츠 패키지를 아직 사용할 수 없는 경우 작업 순서가 실패합니다. 이제 누락된 콘텐츠를 배포하거나(아직 배포되지 않은 경우) 배포 지점에서 콘텐츠를 사용할 수 있을 때까지 기다린 다음 **이전**을 클릭하여 작업 순서에서 콘텐츠를 다시 검색하도록 할 수 있습니다.

## <a name="express-installation-files-support-for-windows-10-updates"></a>Windows 10 업데이트에 대한 빠른 설치 파일 지원
Configuration Manager에 Windows 10 업데이트에 대한 빠른 설치 파일 지원이 추가되었습니다. 지원되는 버전의 Windows 10을 사용하는 경우 이제 Configuration Manager 설정을 사용하여 현재 월의 Windows 10 누적 업데이트와 이전 월의 업데이트 간 델타만 다운로드할 수 있습니다. 현재 Configuration Manager 현재 분기에서는 전체 Windows 10 누적 업데이트(이전 월의 모든 업데이트 포함)가 매달 다운로드됩니다. 빠른 설치 파일을 사용하면 다운로드 크기가 감소하고 클라이언트에서 설치 시간이 단축됩니다.

> [!IMPORTANT]
> Configuration Manager에서 빠른 설치 파일의 사용을 지원하는 설정을 사용할 수 있지만, 이 기능은 2017년 1월 10일에 릴리스된 업데이트(Patch Tuesday)에 포함된 Windows 업데이트 에이전트 업데이트가 설치된 Windows 10 버전 1607에서만 지원됩니다. 이러한 업데이트에 대한 자세한 내용은 [지원 문서 3213986](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693)을 참조하세요. 2017년 2월 14일에 다음 업데이트 집합이 릴리스될 때 빠른 설치 파일을 활용할 수 있습니다. 업데이트가 설치되지 않은 Windows 10 버전 1607과 이전 버전에서는 빠른 설치 파일이 지원되지 않습니다.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>서버에서 Windows 10 업데이트에 대한 빠른 설치 파일의 다운로드를 사용하도록 설정하려면
Windows 10 빠른 설치 파일에 대한 메타데이터 동기화를 시작하려면 소프트웨어 업데이트 지점 속성에서 사용하도록 설정해야 합니다.
1. Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동합니다.
2. 중앙 관리 사이트나 독립 실행형 기본 사이트를 선택합니다.
3. **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성**과 **소프트웨어 업데이트 지점**을 차례로 클릭합니다. **업데이트 파일** 탭에서 **승인된 모든 업데이트에 대한 전체 파일 및 Windows 10용 빠른 설치 파일 다운로드**를 선택합니다.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>클라이언트가 빠른 설치 파일을 다운로드 및 설치할 수 있는 지원을 사용하려면
클라이언트에서 빠른 설치 파일 지원을 사용하려면 클라이언트에서 클라이언트 설정의 소프트웨어 업데이트 섹션을 통해 빠른 설치 파일을 사용하도록 설정해야 합니다. 이렇게 하면 지정한 포트에서 빠른 설치 파일을 다운로드하는 요청을 수신 대기하는 새 HTTP 수신기가 생성됩니다. 클라이언트에 이 기능을 사용하도록 설정하는 클라이언트 설정을 배포하면 현재 월의 Windows 10 누적 업데이트와 이전 월의 업데이트 간 델타 다운로드를 시도합니다(클라이언트에서 빠른 설치 파일을 지원하는 Windows 10 버전을 실행해야 함).
1. 소프트웨어 업데이트 지점 구성 요소 속성에서 빠른 설치 파일 지원을 사용하도록 설정합니다(이전 절차).
2. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동합니다.
3. 적절한 클라이언트 설정을 선택한 다음 **홈** 탭에서 **속성**을 클릭합니다.
4. **소프트웨어 업데이트** 페이지를 선택하고 **클라이언트에서 Express 업데이트 설치 사용** 설정에 대해 **예**를 구성하고 **Express 업데이트 콘텐츠를 다운로드하는 데 사용할 포트**에 대해 클라이언트의 HTTP 수신기에서 사용되는 포트를 구성합니다.


## <a name="odata-endpoint-data-access"></a>OData 엔드포인트 데이터 액세스

 이제 Configuration Manager에서 Configuration Manager 데이터 액세스를 위한 RESTful OData 엔드포인트를 제공합니다. 엔드포인트는 Excel 및 Power BI와 같은 도구가 단일 엔드포인트를 통해 Configuration Manager 데이터에 쉽게 액세스할 수 있도록 하는 Odata 버전 4와 호환됩니다. Technical Preview 1612는 Configuration Manager에서 개체에 대한 읽기 권한만 지원합니다.  

이제 새 OData RESTful 엔드포인트를 사용하여 [Configuration Manager WMI 공급자](/sccm/develop/reference/configuration-manager-reference)에서 현재 사용할 수 있는 데이터에 액세스할 수도 있습니다. OData 엔드포인트에서 노출되는 엔터티 집합을 사용하면 WMI 공급자를 통해 쿼리할 수 있는 것과 동일한 데이터를 열거할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

OData 엔드포인트를 사용하려면 먼저 사이트에 대해 사용하도록 설정해야 합니다.

1.  **관리** > **사이트 구성** > **사이트**로 이동합니다.
2.  기본 사이트를 선택하고 **속성**을 클릭합니다.
3.  기본 사이트 속성 시트의 일반 탭에서 **이 사이트의 모든 공급자에 대해 REST 엔드포인트 사용**을 클릭한 다음 **확인**을 클릭합니다.

즐겨 찾는 OData 쿼리 뷰어에서 다음 예제와 유사한 쿼리를 시도하여 Configuration Manager의 다양한 개체를 반환해 보세요.

| 용도 | OData 쿼리 |
|---|---|
| 모든 컬렉션 가져오기 | `http://localhost/CMRestProvider/Collection` |
| 컬렉션 가져오기 | `http://localhost/CMRestProvider/Collection('SMS00001')`
| 컬렉션의 상위 100개 디바이스 가져오기 | `http://localhost/CMRestProvider/Collection('SMS00001')/Device?$top=100` |
| 컬렉션의 디바이스 및 리소스 ID 가져오기 | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)` |
| 컬렉션의 디바이스 운영 체제 가져오기 | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)/OPERATING_SYSTEM` |
| 컬렉션의 사용자 가져오기 | `http://localhost/CMRestProvider/Collection('SMS00001')/User` |

> [!NOTE]
> 표에 나와 있는 예제 쿼리는 *localhost*를 URL에 호스트 이름으로 사용하며, SMS 공급자를 실행하는 컴퓨터에서 사용할 수 있습니다. 다른 컴퓨터에서 쿼리를 실행하는 경우 localhost를 SMS 공급자가 설치된 서버의 FQDN으로 바꿉니다.

## <a name="azure-active-directory-onboarding"></a>Azure Active Directory 등록

Azure AD(Active Directory) 등록은 다른 클라우드 서비스에서 사용할 Configuration Manager 및 Azure Active Directory 간의 연결을 만듭니다. 현재 이 등록을 사용하여 클라우드 관리 게이트웨이에 필요한 연결을 만들 수 있습니다.

Azure 관리자 자격 증명이 필요하므로 Azure 관리자를 사용하여 이 작업을 수행합니다.

#### <a name="to-create-the-connection"></a>연결을 만들려면

2. **관리** 작업 영역에서 **클라우드 서비스** > **Azure Active Directory** > **Azure Active Directory 추가**를 선택합니다.
2. **로그인**을 선택하여 Azure AD와의 연결을 만듭니다.

#### <a name="configuration-manager-client-requirements"></a>Configuration Manager 클라이언트 요구 사항

클라우드 관리 게이트웨이에서 사용자 정책을 만들기 위한 몇 가지 요구 사항이 있습니다.

- Azure AD 등록 프로세스를 완료해야 하며, 연결 정보를 가져오기 위해 클라이언트가 처음에 회사 네트워크에 연결되어 있어야 합니다.
- 클라이언트는 도메인(Active Directory에 등록됨) 및 클라우드 도메인(Azure AD에 등록됨)에 가입되어 있어야 합니다.
- [Active Directory 사용자 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser)을 실행해야 합니다.
- 인터넷을 통한 사용자 정책 요청을 허용하도록 Configuration Manager 클라이언트를 수정하고 변경 내용을 클라이언트에 배포해야 합니다. 클라이언트에 대한 이 변경은 *클라이언트 디바이스*에서 발생하기 때문에 사용자 정책에 필요한 구성 변경을 완료하지 않은 경우에도 클라우드 관리 게이트웨이를 통해 배포할 수 있습니다.
- HTTPS를 사용하여 네트워크의 토큰을 보호하도록 관리 지점을 구성해야 하며 .Net 4.5가 설치되어 있어야 합니다.

이러한 구성 변경을 수행한 후 사용자 정책을 만들고 클라이언트를 인터넷으로 이동하여 정책을 테스트할 수 있습니다. 클라우드 관리 게이트웨이를 통한 사용자 정책 요청은 Azure AD 토큰 기반 인증을 사용하여 인증됩니다.

## <a name="change-to-configuring-multi-factor-authentication-for-device-enrollment"></a>디바이스 등록에 대한 다단계 인증 구성 변경

이제 Azure Portal에서 디바이스 등록에 MFA(다단계 인증)를 설정할 수 있으므로 Configuration Manager 콘솔에서 MFA 옵션이 제거되었습니다. 등록에 MFA를 설정하는 방법에 대한 자세한 내용은 [이 Microsoft Intune 항목](https://docs.microsoft.com/intune/deploy-use/multi-factor-authentication-azure-active-directory)을 참조하세요.
