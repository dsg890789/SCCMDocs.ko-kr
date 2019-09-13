---
title: 필수 구성 요소 검사기
titleSuffix: Configuration Manager
description: 필수 조건 검사기를 사용하여 사이트 또는 사이트 시스템 역할 설치를 차단하는 문제를 확인하고 해결하는 방법을 알아봅니다.
ms.date: 03/1/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: aaf13bb8-4ba2-4bd7-9fac-d36a9d88a1b6
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 19167ee3b25d838ad6d2268d2b67230968394ef5
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70888796"
---
# <a name="prerequisite-checker-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 필수 조건 검사기

*적용 대상: System Center Configuration Manager(현재 분기)*

 설치 프로그램을 실행하여 System Center Configuration Manager 사이트를 설치하거나 업그레이드하기 전에 또는 새 서버에 사이트 시스템 역할을 설치하기 전에 사용하려는 Configuration Manager 버전에서 이 독립 실행형 애플리케이션(**Prereqchk.exe**)을 시작하여 서버의 준비 상태를 확인할 수 있습니다. 필수 조건 검사기를 사용하여 사이트 또는 사이트 시스템 역할 설치를 차단하는 문제를 확인하고 해결할 수 있습니다.  

> [!NOTE]  
>  필수 조건 검사기는 설치 프로그램의 일부로 항상 실행됩니다.  

기본적으로 필수 조건 검사기를 실행하면 다음 작업이 수행됩니다.  

-   필수 조건 검사기를 실행하는 서버의 유효성을 검사합니다.  
-   로컬 컴퓨터에서 기존 사이트 서버를 검사하며 사이트에 해당하는 검사만 실행됩니다.  
-   기존 사이트가 검색되지 않는 경우 모든 필수 구성 요소 규칙이 실행됩니다.  
-   규칙을 검사하여 설치 프로그램에 필요한 소프트웨어와 설정만 설치되는지를 확인합니다. 필수 소프트웨어에 필수 조건 검사기가 확인하지 않는 추가 구성 또는 소프트웨어 업데이트가 필요할 수 있습니다.  
-   검사 결과는 컴퓨터 시스템 드라이브의 **ConfigMgrPrereq.log** 파일에 기록됩니다. 로그 파일에는 애플리케이션 인터페이스에 표시되지 않는 추가 정보가 포함될 수 있습니다.  

명령 프롬프트에서 필수 조건 검사기를 실행하고 특정 명령줄 옵션을 지정하면 다음 작업이 수행됩니다.  

-   필수 조건 검사기는 명령줄에서 지정한 사이트 서버 또는 사이트 시스템에 연결된 검사만 수행합니다.  
-   원격 컴퓨터를 검사하려면 사용자 계정에 원격 컴퓨터에 대한 관리자 권한이 있어야 합니다.  

필수 조건 검사기가 수행하는 검사에 대한 자세한 내용은 [System Center Configuration Manager에 대한 필수 조건 검사 목록](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md)을 참조하세요.  

## <a name="copy-prerequisite-checker-files-to-another-computer"></a>필수 조건 검사기 파일을 다른 컴퓨터로 복사  

1.  Windows 탐색기에서 다음 위치 중 하나로 이동합니다.  

    -   **&lt;*Configuration Manager 설치 미디어*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager 설치 경로*\>\BIN\X64**  

2.  다음 파일을 다른 컴퓨터의 대상 폴더에 복사합니다.  

    -   Prereqchk.exe  
    -   Prereqcore.dll  
    -   Basesql.dll  
    -   Basesvr.dll  
    -   Baseutil.dll  

##  <a name="run-prerequisite-checker-with-default-checks"></a>필수 조건 검사기를 실행하여 기본 검사 수행  

1.  Windows 탐색기에서 다음 위치 중 하나로 이동합니다.  

    -   **&lt;*Configuration Manager 설치 미디어*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager 설치 경로*\>\BIN\X64**  

2.  **prereqchk.exe** 를 실행하여 필수 구성 요소 검사기를 시작합니다.   
    필수 구성 요소 검사기는 기존 사이트를 검색하고, 기존 사이트가 있는 경우 업그레이드 준비 상태 검사를 수행합니다. 사이트가 발견되지 않으면 모든 검사가 수행됩니다. **사이트 유형** 열에는 규칙과 연관된 사이트 서버 또는 사이트 시스템에 대한 정보가 제공됩니다.  

##  <a name="run-prerequisite-checker-from-a-command-prompt-for-all-default-checks"></a>명령 프롬프트에서 필수 조건 검사기를 실행하여 모든 기본 검사 수행  

1.  명령 프롬프트 창을 열고 디렉터리를 다음 위치 중 하나로 변경합니다.  

    -   **&lt;*Configuration Manager 설치 미디어*\>\SMSSETUP\BIN\X64**  
    -   **&lt;*Configuration Manager 설치 경로*\>\BIN\X64**  

2.  **prereqchk.exe /LOCAL** 을 입력하여 필수 구성 요소 검사기를 시작하고 서버에서 모든 필수 구성 요소 검사를 실행합니다.  

## <a name="run-prerequisite-checker-from-a-command-prompt-to-use-options"></a>명령 프롬프트에서 필수 조건 검사기를 실행하여 옵션 사용  

1. 명령 프롬프트 창을 열고 디렉터리를 다음 위치 중 하나로 변경합니다.  

   -   **&lt;*Configuration Manager 설치 미디어*\>\SMSSETUP\BIN\X64**  
   -   **&lt;*Configuration Manager 설치 경로*\>\BIN\X64**  

2. 다음 명령줄 옵션 중 하나 이상과 함께 **prereqchk.exe**를 입력합니다.  

   예를 들어 기본 사이트를 검사하려면 다음 명령을 사용할 수 있습니다.  

      **prereqchk.exe [/NOUI] /PRI /SQL &lt;SQL Server의 FQDN\> /SDK &lt;SMS 공급자의 FQDN\> [/JOIN &lt;중앙 관리 사이트의 FQDN\>] [/MP &lt;관리 포트의 FQDN\>] [/DP &lt;배포 지점의 FQDN\>]**  

   **중앙 관리 사이트 서버:**  

   -   **/NOUI**  

        필수 아님. 사용자 인터페이스를 표시하지 않고 필수 구성 요소 검사기를 시작합니다. 명령줄에서 다른 옵션 앞에 이 옵션을 지정해야 합니다.  

   -   **/CAS**  

        필수. 로컬 컴퓨터가 중앙 관리 사이트의 요구 사항을 충족하는지를 확인합니다.  

   -   **/SQL &lt;*SQL Server의 FQDN*>**  

        필수. FQDN(정규화된 도메인 이름)을 사용하여 지정한 컴퓨터가 Configuration Manager 사이트 데이터베이스를 호스트할 SQL Server에 대한 요구 사항을 충족하는지 확인합니다.  

   -   **/SDK &lt;*SMS 공급자의 FQDN*>**  

        필수. 지정한 컴퓨터가 SMS 공급자의 요구 사항을 충족하는지를 확인합니다.  

   -   **/Ssbport**  

        필수 아님. SSB(SQL Server Service Broker) 포트의 통신을 허용하는 방화벽 예외가 적용되어 있는지 확인합니다. 기본 SSB 포트는 4022입니다.  

   -   **InstallDir &lt;*Configuration Manager 설치 경로*>**  

        필수 아님. 사이트 설치에 필요한 최소 디스크 공간을 확인합니다.  

   **기본 사이트 서버:**  

   -   **/NOUI**  

       필수 아님. 사용자 인터페이스를 표시하지 않고 필수 구성 요소 검사기를 시작합니다. 명령줄에서 다른 옵션 앞에 이 옵션을 지정해야 합니다.  

   -   **/PRI**  

        필수. 로컬 컴퓨터가 기본 사이트의 요구 사항을 충족하는지를 확인합니다.  

   -   **/SQL &lt;*SQL Server의 FQDN*>**  

        필수. 지정한 컴퓨터가 SQL Server의 요구 사항을 충족하여 Configuration Manager 사이트 데이터베이스를 호스트할 수 있는지를 확인합니다.  

   -   **/SDK &lt;*SMS 공급자의 FQDN*>**  

        필수. 지정한 컴퓨터가 SMS 공급자의 요구 사항을 충족하는지를 확인합니다.  

   -   **/JOIN &lt;*중앙 관리 사이트의 FQDN*>**  

        필수 아님. 로컬 컴퓨터가 중앙 관리 사이트 서버에 연결하는 데 필요한 요구 사항을 충족하는지를 확인합니다.  

   -   **/MP &lt;*관리 지점의 FQDN*>**  

        필수 아님. 지정한 컴퓨터가 관리 지점 사이트 시스템 역할의 요구 사항을 충족하는지를 확인합니다. 이 옵션은 **/PRI** 옵션을 사용하는 경우에만 지원됩니다.  

   -   **/DP &lt;*배포 지점의 FQDN*>**  

        필수 아님. 지정한 컴퓨터가 배포 지점 사이트 시스템 역할의 요구 사항을 충족하는지를 확인합니다. 이 옵션은 **/PRI** 옵션을 사용하는 경우에만 지원됩니다.  

   -   **/Ssbport**  

        필수 아님. SSB 포트의 통신을 허용하는 방화벽 예외가 적용되어 있는지 확인합니다. 기본 SSB 포트는 4022입니다.  

   -   **InstallDir &lt;*Configuration Manager 설치 경로*>**  

        필수 아님. 사이트 설치에 필요한 최소 디스크 공간을 확인합니다.  

   **보조 사이트 서버**  

   -   **/NOUI**  

        필수 아님. 사용자 인터페이스를 표시하지 않고 필수 구성 요소 검사기를 시작합니다. 명령줄에서 다른 옵션 앞에 이 옵션을 지정해야 합니다.  

   -   **/SEC &lt;*보조 사이트 서버의 FQDN*>**  

        필수. 지정한 컴퓨터가 보조 사이트의 요구 사항을 충족하는지를 확인합니다.  

   -   **/INSTALLSQLEXPRESS**  

        필수 아님. 지정한 컴퓨터에 SQL Server Express를 설치할 수 있는지 확인합니다.  

   -   **/Ssbport**  

        필수 아님. SSB 포트의 통신을 허용하는 방화벽 예외가 적용되어 있는지 확인합니다. 기본 SSB 포트는 4022입니다.  

   -   **/Sqlport**  

        필수 아님. 방화벽 예외가 SQL Server 서비스 포트의 통신을 허용하도록 구성되었으며 포트가 다른 명명된 SQL Server의 인스턴스에서 사용되고 있지 않음을 확인합니다. 기본 포트는 1433입니다.  

   -   **InstallDir &lt;*Configuration Manager 설치 경로*>**  

        필수 아님. 사이트 설치에 필요한 최소 디스크 공간을 확인합니다.  

   -   **/SourceDir**  

        필수 아님. 보조 사이트의 컴퓨터 계정이 설치 프로그램의 원본 파일을 호스팅하는 폴더에 액세스할 수 있는지 확인합니다.  

   **Configuration Manager 콘솔:**  

   -   **/Adminui**  

        필수. 로컬 컴퓨터가 Configuration Manager 설치를 위한 요구 사항을 충족하는지를 확인합니다.  

3. 필수 조건 검사기는 필수 조건 검사기 사용자 인터페이스의 **필수 조건 결과** 섹션에 검색된 문제 목록을 만듭니다.  

   -   목록에서 항목을 클릭하면 문제를 해결하는 방법에 대한 자세한 정보가 나타납니다.  
   -   사이트 서버, 사이트 시스템 또는 Configuration Manager 콘솔을 설치하기 전에 **오류** 상태가 있는 모든 목록의 항목을 해결해야 합니다.  
   -   또한 시스템 드라이브의 루트에 있는 **ConfigMgrPrereq.log** 파일을 열고 필수 조건 검사기 결과를 검토할 수 있습니다. 로그 파일에는 필수 조건 검사기 사용자 인터페이스에 표시되지 않은 추가 정보가 있을 수 있습니다.  
