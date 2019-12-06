---
title: 설치 명령줄 옵션
titleSuffix: Configuration Manager
description: 명령줄을 사용하여 Configuration Manager를 설치하는 자동화 스크립트 만들기.
ms.date: 08/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0da167f1-52cf-4dfd-8f73-833ca3eb8478
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6b49f05708f824c16dd90cbb9c872f49ab484de8
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "69974719"
---
# <a name="command-line-options-for-configuration-manager-setup"></a>Configuration Manager 설치를 위한 명령줄 옵션

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 정보를 사용하여 명령줄에서 스크립트를 구성하거나 Configuration Manager를 설치할 수 있습니다.  

## <a name="bkmk_setup"></a> 설치용 명령줄 옵션

사이트 서버의 Configuration Manager 설치 경로 `\BIN\X64` 디렉터리에서 설치 프로그램을 실행합니다.

### `/DEINSTALL`

사이트를 제거합니다. 사이트 서버 컴퓨터에서 설치 프로그램을 실행합니다.  

### `/DONTSTARTSITECOMP`

사이트를 설치하지만 사이트 구성 요소 관리자 서비스가 시작되지 않도록 합니다. 사이트 구성 요소 관리자 서비스가 시작될 때까지 사이트는 활성화되지 않습니다. Site Component Manager는 SMS_Executive 서비스와 사이트의 추가 프로세스를 설치하고 시작합니다. 사이트 설치가 완료된 후에 Site Component Manager 서비스를 시작하면 SMS_Executive 서비스와 사이트 작동에 필요한 추가 프로세스가 설치됩니다.  

### `/HIDDEN`

설치하는 동안 사용자 인터페이스를 숨깁니다. 이 옵션은 **/SCRIPT** 옵션과 함께 사용해야 합니다. 무인 스크립트 파일에 필요한 모든 옵션을 지정해야 합니다. 지정하지 않으면 설치가 실패합니다.  

### `/NOUSERINPUT`

설치 시 사용자 입력을 사용하지 않도록 설정하지만 설치 마법사를 표시합니다. 이 옵션은 **/SCRIPT** 옵션과 함께 사용해야 합니다. 무인 스크립트 파일에 필요한 모든 옵션을 지정해야 합니다. 지정하지 않으면 설치가 실패합니다.  

### `/RESETSITE`

사이트의 데이터베이스 및 서비스 계정을 다시 설정하는 사이트 다시 설정을 실행합니다.

자세한 내용은 [사이트 다시 설정 실행](/sccm/core/servers/manage/modify-your-infrastructure#bkmk_reset)을 참조하세요.  

### `/TESTDBUPGRADE`

데이터베이스를 업그레이드할 수 있는지 확인하기 위해 사이트 데이터베이스의 백업에 대한 테스트를 실행합니다.

> [!IMPORTANT]  
> 프로덕션 사이트 데이터베이스에서는 이 명령줄 옵션을 실행하지 마세요. 프로덕션 사이트 데이터베이스에서 이 명령줄 옵션을 실행하면 사이트 데이터베이스가 업그레이드되어 사이트가 작동하지 않을 수 있습니다.

#### <a name="usage"></a>사용

사이트 데이터베이스의 인스턴스 이름과 데이터베이스 이름을 입력합니다. 데이터베이스 이름만 지정하면 설치 프로그램이 기본 인스턴스 이름을 사용합니다.  

`/TESTDBUPGRADE <Instance name>\<Database name>`

`/TESTDBUPGRADE CM_ABC`

`/TESTDBUPGRADE Named\CM_ABC`

### `/UPGRADE`

사이트의 무인 업그레이드를 실행합니다. 대시(`-`)를 포함하는 제품 키를 지정합니다. 또한 이전에 다운로드한 설치 필수 구성 요소 파일의 경로를 지정합니다.  

설치 필수 구성 요소 파일에 대한 자세한 내용은 [설치 다운로더](/sccm/core/servers/deploy/install/setup-downloader)를 참조하세요.  

#### <a name="usage"></a>사용

`setupwpf.exe /UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx <path to external component files>`  

### `/SCRIPT`

무인 설치를 실행합니다. 이 옵션이 있는 설치 초기화 파일을 사용합니다. 무인 설치를 실행하는 방법에 대한 자세한 내용은 [명령줄을 사용하여 System Center Configuration Manager 사이트 설치](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites)를 참조하세요.  

#### <a name="usage"></a>사용

`/SCRIPT <setup script path>`

### `/SDKINST`

지정된 컴퓨터에서 SMS 공급자를 설치합니다. SMS 공급자 컴퓨터의 FQDN(정규화된 도메인 이름)을 입력합니다. SMS 공급자에 대한 자세한 내용은 [SMS 공급자에 대한 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.  

#### <a name="usage"></a>사용

`/SDKINST <SMS Provider FQDN>`

### `/SDKDEINST`

지정된 컴퓨터에서 SMS 공급자를 제거합니다. SMS 공급자 컴퓨터의 FQDN을 입력합니다.  

#### <a name="usage"></a>사용

`/SDKDEINST <SMS Provider FQDN>`

### `/MANAGELANGS`

이전에 설치한 사이트에 설치된 언어를 관리합니다. 언어 설정이 포함된 언어 스크립트 파일의 위치를 입력합니다. 자세한 내용은 [언어를 관리하는 명령줄 옵션](#bkmk_Lang) 섹션을 참조하세요.  

#### <a name="usage"></a>사용

`/MANAGELANGS <Language script path>`


## <a name="bkmk_Lang"></a> 언어 관리용 명령줄 옵션

### <a name="identification"></a>Identification

- **키 이름:** 작업  

    - **필수:** 예  

    - **값:** `ManageLanguages`  

    - **세부 정보:** 사이트의 서버, 클라이언트 및 모바일 클라이언트 언어 지원을 관리합니다.  

### <a name="options"></a>Options

- **키 이름:** AddServerLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 사용할 수 있는 서버 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

- **키 이름:** AddClientLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 클라이언트 컴퓨터에 사용할 수 있는 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

- **키 이름:** DeleteServerLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 제거할 언어를 지정합니다. 해당 언어는 Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용 가능하며 제거할 수 없습니다.  

- **키 이름:** DeleteClientLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 제거할 언어를 지정합니다. 해당 언어는 클라이언트 컴퓨터에서 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용 가능하며 제거할 수 없습니다.  

- **키 이름:** MobileDeviceLanguage  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 모바일 디바이스 클라이언트 언어의 설치 여부를 지정합니다.  

- **키 이름:** PrerequisiteComp  

    - **필수:** 예  

    - **값:**

        - `0` = 다운로드  

        - `1` = 이미 다운로드됨  

    - **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 `0` 값을 사용하는 경우 설치 프로그램이 파일을 다운로드합니다.  

- **키 이름:** PrerequisitePath  

    - **필수:** 예  

    - **값:**  <*설치 필수 구성 요소 파일 경로*>  

    - **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  


## <a name="bkmk_Unattended"></a> 무인 설치 스크립트 파일 키

다음 섹션에서는 무인 설치를 위한 스크립트를 생성하는 방법을 설명합니다. 목록은 다음을 보여줍니다.

- 사용 가능한 설치 스크립트 키 및 해당 값
- 필요한 경우
- 사용 중인 설치 유형
- 키에 대한 간단한 설명

### <a name="unattended-install-for-a-central-administration-site-cas"></a>CAS(중앙 관리 사이트)의 무인 설치

다음에서는 무인 설치 스크립트 파일을 사용하여 CAS를 설치하는 방법을 설명합니다.  

#### <a name="identification"></a>Identification

- **키 이름:** 작업  

    - **필수:** 예  

    - **값:** `InstallCAS`  

    - **세부 정보:** CAS를 설치합니다.  

- **키 이름:** CDLatest  

    - **필수:** 예. CD.Latest 폴더의 미디어를 사용할 경우에만.

    - **값:**

        - `1` = CD.Latest의 미디어를 사용하고 있음

        - 1이 아닌 모든 값 = CD.Latest를 사용하고 있지 않음

    - **세부 정보:** 기본 사이트 또는 CA를 설치하거나 복구할 때 이 키 및 값을 포함하여 CD.Latest 폴더에서 설치 프로그램을 실행합니다. 이 값은 CD.Latest의 미디어를 사용하고 있음을 설치 프로그램에 알립니다.

#### <a name="options"></a>Options

- **키 이름:** ProductID  

    - **필수:** 예  

    - **값:**

        - `<xxxxx-xxxxx-xxxxx-xxxxx-xxxxx>` = 대시를 포함하는 유효한 제품 키

        - `Eval` = Configuration Manager의 평가 버전 설치

    - **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다.

- **키 이름:** SiteCode  

    - **필수:** 예  

    - **값:**  <*사이트 코드*>(예: `ABC`)

    - **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다.  

- **키 이름:** 사이트 이름  

    - **필수:** 예  

    - **값:**  <*사이트 이름*>  

    - **세부 정보:** 이 사이트의 이름을 지정합니다.  

- **키 이름:** SMSInstallDir  

    - **필수:** 예  

    - **값:**  <*Configuration Manager 설치 경로*>  

    - **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

- **키 이름:** SDKServer  

    - **필수:** 예  

    - **값:**  <*SMS 공급자 FQDN*>  

    - **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.  

- **키 이름:** PrerequisiteComp  

    - **필수:** 예  

    - **값:**

        - `0` = 다운로드  

        - `1` = 이미 다운로드됨  

    - **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 `0` 값을 사용하는 경우 설치 프로그램이 파일을 다운로드합니다.  

- **키 이름:** PrerequisitePath  

    - **필수:** 예  

    - **값:**  <*설치 필수 구성 요소 파일 경로*>  

    - **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

- **키 이름:** AdminConsole  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

- **키 이름:** JoinCEIP  

    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

    - **필수:** 예  

    - **값:**

        - `0` = 조인 안 함  

        - `1` = 조인  

    - **세부 정보:** CEIP(사용자 환경 개선 프로그램) 참여 여부를 지정합니다.  

- **키 이름:** AddServerLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 사용할 수 있는 서버 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

- **키 이름:** AddClientLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 클라이언트 컴퓨터에 사용할 수 있는 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

- **키 이름:** DeleteServerLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 사이트를 설치한 후 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용 가능하며 제거할 수 없습니다.  

- **키 이름:** DeleteClientLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 사이트를 설치한 후 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 클라이언트 컴퓨터에서 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용 가능하며 제거할 수 없습니다.  

- **키 이름:** MobileDeviceLanguage  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 모바일 디바이스 클라이언트 언어의 설치 여부를 지정합니다.  

#### <a name="sqlconfigoptions"></a>SQLConfigOptions

- **키 이름:** SQLServerName  

    - **필수:** 예  

    - **값:**  <*SQL Server 이름*>  

    - **세부 정보:** 사이트 데이터베이스를 호스트하려면 SQL Server가 실행 중인 클러스터된 인스턴스 또는 서버의 이름을 지정합니다.  

- **키 이름:** DatabaseName  

    - **필수:** 예  

    - **값:**  <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>  

    - **세부 정보:** 설치 프로그램에서 CAS 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다.  

        > [!IMPORTANT]  
        > 기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정합니다.  

- **키 이름:** SQLSSBPort  

    - **필수:** 아니요  

    - **값:**  <*SSB 포트 번호*>  

    - **세부 정보:** SQL Server가 사용하는 SQL SSB(Server Service Broker) 포트를 지정합니다. 기본적으로 SSB는 TCP 포트 4022를 사용하지만 다른 포트를 사용할 수도 있습니다.  

- **키 이름:** SQLDataFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .mdb 파일 경로*>  

    - **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

- **키 이름:** SQLLogFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .ldf 파일 경로*>  

    - **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

#### <a name="cloudconnectoroptions"></a>CloudConnectorOptions

- **키 이름:** CloudConnector  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 `1`이어야 합니다.  

- **키 이름:** CloudConnectorServer  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*서비스 연결 지점 서버 FQDN*>  

    - **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

- **키 이름:** UseProxy  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 서비스 연결점에서 프록시 서버를 사용할지 여부를 지정합니다.  

- **키 이름:** ProxyName  

    - **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    - **값:**  <*프록시 서버 FQDN*>  

    - **세부 정보:** 서비스 연결점에서 사용하는 프록시 서버의 FQDN을 지정합니다.  

- **키 이름:** ProxyPort  

    - **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    - **값:**  <*포트 번호*>  

    - **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  

#### <a name="sabranchoptions"></a>SABranchOptions

<!-- SCCMDocs#390 -->

- **키 이름:** SAActive

    - **필수:** 아니요

    - **값:**

        - `0` = Software Assurance가 없음

        - `1` = Software Assurance가 활성화됨

    - **세부 정보:** 활성 Software Assurance가 있는지 지정합니다. 자세한 내용은 [제품 및 라이선스 FAQ](/sccm/core/understand/product-and-licensing-faq)를 참조하세요.

- **키 이름:** CurrentBranch

    - **필수:** 아니요

    - **값:**

        - `0` = LTSB 설치

        - `1` = 현재 분기 설치

    - **세부 정보:** Configuration Manager 현재 분기 또는 LTSB(장기 서비스 분기)를 사용할지 여부를 지정합니다. 자세한 내용은 [사용해야 하는 Configuration Manager 분기](/sccm/core/understand/which-branch-should-i-use)를 참조하세요.

### <a name="unattended-install-for-a-primary-site"></a>기본 사이트의 무인 설치

다음에서는 무인 설치 스크립트 파일을 사용하여 기본 사이트를 설치하는 방법을 설명합니다.  

#### <a name="identification"></a>Identification

- **키 이름:** 작업  

    - **필수:** 예  

    - **값:** `InstallPrimarySite`  

    - **세부 정보:** 기본 사이트를 설치합니다.  

- **키 이름:** CDLatest  

    - **필수:** 예. CD.Latest 폴더의 미디어를 사용할 경우에만.

    - **값:**

        - `1` = CD.Latest의 미디어를 사용하고 있음

        - 1이 아닌 모든 값 = CD.Latest를 사용하고 있지 않음

    - **세부 정보:** 기본 사이트 또는 CA를 설치하거나 복구할 때 이 키 및 값을 포함하여 CD.Latest 폴더에서 설치 프로그램을 실행합니다. 이 값은 CD.Latest의 미디어를 사용하고 있음을 설치 프로그램에 알립니다.

#### <a name="options"></a>Options

- **키 이름:** ProductID  

    - **필수:** 예  

    - **값:**

        - `<xxxxx-xxxxx-xxxxx-xxxxx-xxxxx>` = 대시를 포함하는 유효한 제품 키

        - `Eval` = Configuration Manager의 평가 버전 설치

    - **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다.

- **키 이름:** SiteCode  

    - **필수:** 예  

    - **값:**  <*사이트 코드*>  

    - **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다.  

- **키 이름:** SiteName  

    - **필수:** 예  

    - **값:**  <*사이트 이름*>  

    - **세부 정보:** 이 사이트의 이름을 지정합니다.  

- **키 이름:** SMSInstallDir  

    - **필수:** 예  

    - **값:**  <*Configuration Manager 설치 경로*>

    - **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

- **키 이름:** SDKServer  

    - **필수:** 예  

    - **값:**  <*SMS 공급자 FQDN*>  

    - **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.  

- **키 이름:** PrerequisiteComp  

    - **필수:** 예  

    - **값:**

        - `0` = 다운로드  

        - `1` = 이미 다운로드됨  

    - **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 `0` 값을 사용하는 경우 설치 프로그램이 파일을 다운로드합니다.  

- **키 이름:** PrerequisitePath  

    - **필수:** 예  

    - **값:**  <*설치 필수 구성 요소 파일 경로*>  

    - **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

- **키 이름:** AdminConsole  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

- **키 이름:** JoinCEIP  

    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

    - **필수:** 예  

    - **값:**

        - `0` = 조인 안 함  

        - `1` = 조인  

    - **세부 정보:** CEIP에 참여할지 여부를 지정합니다.  

- **키 이름:** ManagementPoint  

    - **필수:** 아니요  

    - **값:**  <*관리 지점 사이트 서버 FQDN*>  

    - **세부 정보:** 관리 지점 사이트 시스템 역할을 호스트할 서버의 FQDN을 지정합니다.  

- **키 이름:** ManagementPointProtocol  

    - **필수:** 아니요  

    - **값:** `HTTPS` 또는 `HTTP`  

    - **세부 정보:** 관리 지점에 사용할 프로토콜을 지정합니다.  

- **키 이름:** DistributionPoint  

    - **필수:** 아니요  

    - **값:**  <*배포 지점 사이트 서버 FQDN*>  

    - **세부 정보:** 배포 지점 사이트 시스템 역할을 호스트할 서버의 FQDN을 지정합니다.  

- **키 이름:** DistributionPointProtocol  

    - **필수:** 아니요  

    - **값:** `HTTPS` 또는 `HTTP`  

    - **세부 정보:** 배포 지점에 사용할 프로토콜을 지정합니다.  

- **키 이름:** RoleCommunicationProtocol  

    - **필수:** 예  

    - **값:** `EnforceHTTPS` 또는 `HTTPorHTTPS`  

    - **세부 정보:** 클라이언트의 HTTPS 통신만 수락하도록 모든 사이트 시스템을 구성할지, 아니면 각 사이트 시스템 역할마다 다른 통신 방법을 구성할지를 지정합니다. `EnforceHTTPS`를 선택하는 경우 클라이언트에 클라이언트 인증을 위해 유효한 PKI(공개 키 인프라) 인증서가 있어야 합니다.  

- **키 이름:** ClientsUsePKICertificate  

    - **필수:** 예  

    - **값:**

        - `0` = 사용 안 함  

        - `1` = 사용  

    - **세부 정보:** 클라이언트가 클라이언트 PKI 인증서를 사용하여 사이트 시스템 역할과 통신할지 여부를 지정합니다.  

- **키 이름:** AddServerLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 사용할 수 있는 서버 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

- **키 이름:** AddClientLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 클라이언트 컴퓨터에 사용할 수 있는 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

- **키 이름:** DeleteServerLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 사이트를 설치한 후 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용 가능하며 제거할 수 없습니다.  

- **키 이름:** DeleteClientLanguages  

    - **필수:** 아니요  

    - **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK, or ZHH  

    - **세부 정보:** 사이트를 설치한 후 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 클라이언트 컴퓨터에서 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용 가능하며 제거할 수 없습니다.  

- **키 이름:** MobileDeviceLanguage  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 모바일 디바이스 클라이언트 언어의 설치 여부를 지정합니다.  

#### <a name="sqlconfigoptions"></a>SQLConfigOptions

- **키 이름:** SQLServerName  

    - **필수:** 예  

    - **값:**  <*SQL Server 이름*>  

    - **세부 정보:** 사이트 데이터베이스를 호스트하려면 SQL Server를 실행하는 클러스터된 인스턴스 또는 서버의 이름을 지정합니다.  

- **키 이름:** DatabaseName  

    - **필수:** 예  

    - **값:**  <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>  

    - **세부 정보:** 기본 사이트 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다.  

        > [!IMPORTANT]  
        > 기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정합니다.  

- **키 이름:** SQLSSBPort  

    - **필수:** 아니요  

    - **값:**  <*SSB 포트 번호*>  

    - **세부 정보:** SQL Server가 사용하는 SSB 포트를 지정합니다. 기본적으로 SSB는 TCP 포트 4022를 사용하지만 다른 포트를 사용할 수도 있습니다.  

- **키 이름:** SQLDataFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .mdb 파일 경로*>  

    - **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

- **키 이름:** SQLLogFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .ldf 파일 경로*>  

    - **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

#### <a name="hierarchyexpansionoption"></a>HierarchyExpansionOption

- **키 이름:** CCARSiteServer  

    - **필수:** 아니요  

    - **값:**  <*중앙 관리 사이트 FQDN*>  

    - **세부 정보:** 기본 사이트가 Configuration Manager 계층 구조에 조인할 때 연결하는 CAS를 지정합니다. 설치 중에 CAS를 지정합니다.  

- **키 이름:** CASRetryInterval  

    - **필수:** 아니요  

    - **값:**  <*간격(분)* >  

    - **세부 정보:** 연결에 실패한 후 CAS를 연결하려고 다시 시도하는 간격(분)을 지정합니다. 예를 들어 CAS에 연결하지 못한 기본 사이트는 **CASRetryInterval** 값으로 지정된 시간(분) 동안 기다렸다가 연결을 다시 시도합니다.  

- **키 이름:** WaitForCASTimeout  

    - **필수:** 아니요  

    - **값:**  <*시간 제한(0~100분)* >  

    - **세부 정보:** 기본 사이트가 CAS에 연결하는 최대 시간 제한 값(분)을 지정합니다. 예를 들어 기본 사이트가 CAS에 연결하지 못하면 **WaitForCASTimeout** 기간에 도달할 때까지 기본 사이트는 **CASRetryInterval** 값을 기반으로 CAS에 연결을 다시 시도합니다. `0` ~ `100` 값을 지정할 수 있습니다.  

#### <a name="cloudconnectoroptions"></a>CloudConnectorOptions

- **키 이름:** CloudConnector  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 `0`이어야 합니다.  

- **키 이름:** CloudConnectorServer  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*서비스 연결 지점 서버 FQDN*\>  

    - **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

- **키 이름:** UseProxy  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 서비스 연결점에서 프록시 서버를 사용할지 여부를 지정합니다.  

- **키 이름:** ProxyName  

    - **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    - **값:**  <*프록시 서버 FQDN*>  

    - **세부 정보:** 서비스 연결점에서 사용하는 프록시 서버의 FQDN을 지정합니다.  

- **키 이름:** ProxyPort  

    - **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    - **값:**  <*포트 번호*>  

    - **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  

#### <a name="sabranchoptions"></a>SABranchOptions

<!-- SCCMDocs#390 -->

- **키 이름:** SAActive

    - **필수:** 아니요

    - **값:**

        - `0` = Software Assurance가 없음

        - `1` = Software Assurance가 활성화됨

    - **세부 정보:** 활성 Software Assurance가 있는지 지정합니다. 자세한 내용은 [제품 및 라이선스 FAQ](/sccm/core/understand/product-and-licensing-faq)를 참조하세요.

- **키 이름:** CurrentBranch

    - **필수:** 아니요

    - **값:**

        - `0` = LTSB 설치

        - `1` = 현재 분기 설치

    - **세부 정보:** Configuration Manager 현재 분기 또는 LTSB(장기 서비스 분기)를 사용할지 여부를 지정합니다. 자세한 내용은 [사용해야 하는 Configuration Manager 분기](/sccm/core/understand/which-branch-should-i-use)를 참조하세요.

### <a name="unattended-recovery-for-a-cas"></a>CAS의 무인 복구

다음에서는 무인 설치 스크립트 파일을 사용하여 CAS를 복구하는 방법을 설명합니다.  

#### <a name="identification"></a>Identification

- **키 이름:** 작업  

    - **필수:** 예  

    - **값:** `RecoverCCAR`  

    - **세부 정보:** CAS를 복구합니다.  

- **키 이름:** CDLatest  

    - **필수:** 예. CD.Latest 폴더의 미디어를 사용할 경우에만.

    - **값:**

        - `1` = CD.Latest의 미디어를 사용하고 있음

        - 1이 아닌 모든 값 = CD.Latest를 사용하고 있지 않음

    - **세부 정보:** 기본 사이트 또는 CA를 설치하거나 복구할 때 이 키 및 값을 포함하여 CD.Latest 폴더에서 설치 프로그램을 실행합니다. 이 값은 CD.Latest의 미디어를 사용하고 있음을 설치 프로그램에 알립니다.

#### <a name="recoveryoptions"></a>RecoveryOptions

- **키 이름:** ServerRecoveryOptions  

    - **필수:** 예  

    - **값:**

        - `1` = 사이트 서버와 SQL Server 복구

        - `2` = 사이트 서버만 복구

        - `4` = SQL Server만 복구  

    - **세부 정보:** 설치 프로그램이 사이트 서버, SQL Server 또는 둘 다 복구하는지 여부를 지정합니다. 지정된 값에 따라 다음 옵션도 필요합니다.  

        - **1** 또는 **2**: 사이트 백업을 사용하여 사이트를 복구하려면 **SiteServerBackupLocation**의 값을 지정합니다. 값을 지정하지 않으면 설치 프로그램이 백업 세트에서 복원하지 않고 사이트를 다시 설치합니다.  

        - **4**: **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

- **키 이름:** DatabaseRecoveryOptions  

    - **필수:** **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.  

    - **값:**

        - `10` = 백업에서 사이트 데이터베이스 복원.  

        - `20` = 다른 방법을 사용하여 수동으로 복구한 사이트 데이터베이스 사용.  

        - `40` = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 사이트는 다른 사이트의 복제를 통해 글로벌 데이터 및 사이트 데이터를 복구합니다.  

        - `80` = 데이터베이스 복구 건너뛰기.  

    - **세부 정보:** SQL Server의 사이트 데이터베이스를 복구하는 방법을 지정합니다.  

- **키 이름:** ReferenceSite  

    - **필수:** DatabaseRecoveryOptions 설정 값이 **40**인 경우 이 키는 필수입니다.  

    - **값:**  <*참조 사이트 FQDN*>  

    - **세부 정보:** 데이터베이스 백업이 변경 내용 추적 보존 기간보다 오래 되었거나 백업 없이 사이트를 복구할 경우 CAS에서 글로벌 데이터를 복구하는 데 사용하는 참조 기본 사이트를 지정합니다.  

        참조 사이트를 지정하지 않았는데 백업이 변경 추적 보존 기간보다 오래된 경우 모든 기본 사이트는 CAS에서 복원된 데이터로 다시 초기화됩니다.  

        참조 사이트를 지정하지 않았지만 백업이 변경 추적 보존 기간 내에 있는 경우 백업 이후 적용된 변경 내용만 기본 사이트에서 복제됩니다. 서로 다른 기본 사이트 간에 충돌하는 변경 내용이 있으면 CAS에서는 가장 먼저 수신한 변경 내용을 사용합니다.  

- **키 이름:** SiteServerBackupLocation  

    - **필수:** 아니요  

    - **값:**  <*사이트 서버 백업 집합 경로*>  

    - **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 설치 프로그램이 백업 세트에서 복원하지 않고 사이트를 다시 설치합니다.  

- **키 이름:** BackupLocation  

    - **필수:** **ServerRecoveryOptions** 키 값을 **1** 또는 **4**로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10**으로 구성하는 경우 이 키는 필수입니다.  

    - **값:**  <*사이트 데이터베이스 백업 집합 경로*>  

    - **세부 정보:** 사이트 데이터베이스 백업 세트의 경로를 지정합니다.  

#### <a name="options"></a>Options

- **키 이름:** ProductID  

    - **필수:** 예  

    - **값:**

        - `<xxxxx-xxxxx-xxxxx-xxxxx-xxxxx>` = 대시를 포함하는 유효한 제품 키

        - `Eval` = Configuration Manager의 평가 버전 설치

    - **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다.

- **키 이름:** SiteCode  

    - **필수:** 예  

    - **값:**  <*사이트 코드*>  

    - **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다. 장애가 발생하기 전에 사이트에 사용되던 사이트 코드를 지정합니다.

- **키 이름:** SiteName  

    - **필수:** 아니요  

    - **값:**  <*사이트 이름*>  

    - **세부 정보:** 이 사이트의 이름을 지정합니다.  

- **키 이름:** SMSInstallDir  

    - **필수:** 예  

    - **값:**  <*Configuration Manager 설치 경로*>  

    - **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

- **키 이름:** SDKServer  

    - **필수:** 예  

    - **값:**  <*SMS 공급자 FQDN*>  

    - **세부 정보:** SMS 공급 기업을 호스트하는 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정합니다.  

        초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다. SMS 공급자에 대한 자세한 내용은 [SMS 공급자에 대한 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.  

- **키 이름:** PrerequisiteComp  

    - **필수:** 예  

    - **값:**

        - `0` = 다운로드  

        - `1` = 이미 다운로드됨  

    - **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0** 값을 사용하는 경우 파일이 다운로드됩니다.  

- **키 이름:** PrerequisitePath  

    - **필수:** 예  

    - **값:**  <*설치 필수 구성 요소 파일 경로*>  

    - **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

- **키 이름:** AdminConsole  

    - **필수:** ServerRecoveryOptions 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

- **키 이름:** JoinCEIP  

    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

    - **필수:** 예  

    - **값:**

        - `0` = 조인 안 함  

        - `1` = 조인  

    - **세부 정보:** CEIP에 참여할지 여부를 지정합니다.  

#### <a name="sqlconfigoptions"></a>SQLConfigOptions

- **키 이름:** SQLServerName  

    - **필수:** 예  

    - **값:**  <*SQL Server 이름*>  

    - **세부 정보:** 사이트 데이터베이스를 호스트하는 SQL Server가 실행 중인 클러스터된 인스턴스 또는 서버의 이름을 지정합니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정합니다.  

- **키 이름:** DatabaseName  

    - **필수:** 예  

    - **값:**  <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>  

    - **세부 정보:** CAS 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정합니다.  

        > [!IMPORTANT]  
        > 기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정합니다.  

- **키 이름:** SQLSSBPort  

    - **필수:** 예  

    - **값:**  <*SSB 포트 번호*>  

    - **세부 정보:** SQL Server가 사용하는 SSB 포트를 지정합니다. 기본적으로 SSB는 TCP 포트 4022를 사용합니다. 실패하기 전에 사용했던 SSB 포트를 지정합니다.  

- **키 이름:** SQLDataFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .mdb 파일 경로*>  

    - **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

- **키 이름:** SQLLogFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .ldf 파일 경로*>  

    - **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

#### <a name="cloudconnectoroptions"></a>CloudConnectorOptions

- **키 이름:** CloudConnector  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 **0**이어야 합니다.  

- **키 이름:** CloudConnectorServer  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*서비스 연결 지점 서버 FQDN*>  

    - **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

- **키 이름:** UseProxy  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 서비스 연결점에서 프록시 서버를 사용할지 여부를 지정합니다.  

- **키 이름:** ProxyName  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*프록시 서버 FQDN*>  

    - **세부 정보:** 서비스 연결점에서 사용하는 프록시 서버의 FQDN을 지정합니다.  

- **키 이름:** ProxyPort  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*포트 번호*>  

    - **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  

### <a name="unattended-recovery-for-a-primary-site"></a>기본 사이트의 무인 복구

다음에서는 무인 설치 스크립트 파일을 사용하여 기본 사이트를 복구하는 방법을 설명합니다.  

#### <a name="identification"></a>Identification

- **키 이름:** 작업  

    - **필수:** 예  

    - **값:** `RecoverPrimarySite`  

    - **세부 정보:** 기본 사이트 복구  

- **키 이름:** CDLatest  

    - **필수:** 예. CD.Latest 폴더의 미디어를 사용할 경우에만.

    - **값:**

        - `1` = CD.Latest의 미디어를 사용하고 있음

        - 1이 아닌 모든 값 = CD.Latest를 사용하고 있지 않음

    - **세부 정보:** 기본 사이트 또는 CA를 설치하거나 복구할 때 이 키 및 값을 포함하여 CD.Latest 폴더에서 설치 프로그램을 실행합니다. 이 값은 CD.Latest의 미디어를 사용하고 있음을 설치 프로그램에 알립니다.

#### <a name="recoveryoptions"></a>RecoveryOptions

- **키 이름:** ServerRecoveryOptions  

    - **필수:** 예  

    - **값:**

        - `1` = 사이트 서버와 SQL Server 복구

        - `2` = 사이트 서버만 복구

        - `4` = SQL Server만 복구  

    - **세부 정보:** 설치 프로그램이 사이트 서버, SQL Server 또는 둘 다 복구하는지 여부를 지정합니다. 지정된 값에 따라 다음 옵션도 필요합니다.  

        - **1** 또는 **2**: 사이트 백업을 사용하여 사이트를 복구하려면 **SiteServerBackupLocation**의 값을 지정합니다. 값을 지정하지 않으면 설치 프로그램이 백업 세트에서 복원하지 않고 사이트를 다시 설치합니다.  

        - **4**: **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

- **키 이름:** DatabaseRecoveryOptions  

    - **필수:** **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.  

    - **값:**

        - `10` = 백업에서 사이트 데이터베이스 복원.  

        - `20` = 다른 방법을 사용하여 수동으로 복구한 사이트 데이터베이스 사용.  

        - `40` = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 사이트는 다른 사이트의 복제를 통해 글로벌 데이터 및 사이트 데이터를 복구합니다.  

        - `80` = 데이터베이스 복구 건너뛰기.  

    - **세부 정보:** SQL Server의 사이트 데이터베이스를 복구하는 방법을 지정합니다.  

- **키 이름:** SiteServerBackupLocation  

    - **필수:** 아니요  

    - **값:**  <*사이트 서버 백업 집합 경로*>  

    - **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 설치 프로그램이 백업 세트에서 복원하지 않고 사이트를 다시 설치합니다.  

- **키 이름:** BackupLocation  

    - **필수:** **ServerRecoveryOptions** 키 값을 **1** 또는 **4**로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10**으로 구성하는 경우 이 키는 필수입니다.  

    - **값:**  <*사이트 데이터베이스 백업 집합 경로*>  

    - **세부 정보:** 사이트 데이터베이스 백업 세트의 경로를 지정합니다.  

#### <a name="options"></a>Options

- **키 이름:** ProductID  

    - **필수:** 예  

    - **값:**

        - `<xxxxx-xxxxx-xxxxx-xxxxx-xxxxx>` = 대시를 포함하는 유효한 제품 키

        - `Eval` = Configuration Manager의 평가 버전 설치

    - **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다.

- **키 이름:** SiteCode  

    - **필수:** 예  

    - **값:**  <*사이트 코드*>  

    - **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다. 장애가 발생하기 전에 사이트에 사용되던 사이트 코드를 지정합니다.

- **키 이름:** SiteName  

    - **필수:** 아니요  

    - **값:**  <*사이트 이름*>  

    - **세부 정보:** 이 사이트의 이름을 지정합니다.  

- **키 이름:** SMSInstallDir  

    - **필수:** 예  

    - **값:**  <*Configuration Manager 설치 경로*>  

    - **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

- **키 이름:** SDKServer  

    - **필수:** 예  

    - **값:**  <*SMS 공급자 FQDN*>  

    - **세부 정보:** SMS 공급 기업을 호스트하는 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정합니다. 초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다. SMS 공급자에 대한 자세한 내용은 [SMS 공급자에 대한 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.  

- **키 이름:** PrerequisiteComp  

    - **필수:** 예  

    - **값:**

        - `0` = 다운로드  

        - `1` = 이미 다운로드됨  

    - **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0** 값을 사용하는 경우 파일이 다운로드됩니다.  

- **키 이름:** PrerequisitePath  

    - **필수:** 예  

    - **값:**  <*설치 필수 구성 요소 파일 경로*>  

    - **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

- **키 이름:** AdminConsole  

    - **필수:** ServerRecoveryOptions 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

- **키 이름:** JoinCEIP  

    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

    - **필수:** 예  

    - **값:**

        - `0` = 조인 안 함  

        - `1` = 조인  

    - **세부 정보:** CEIP에 참여할지 여부를 지정합니다.  

#### <a name="sqlconfigoptions"></a>SQLConfigOptions

- **키 이름:** SQLServerName  

    - **필수:** 예  

    - **값:**  <*SQL Server 이름*>  

    - **세부 정보:** 사이트 데이터베이스를 호스트하려면 SQL Server를 실행하는 클러스터된 인스턴스 또는 서버의 이름을 지정합니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정합니다.  

- **키 이름:** DatabaseName  

    - **필수:** 예  

    - **값:**  <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>

    - **세부 정보:** CAS 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정합니다.  

        > [!IMPORTANT]  
        > 기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정합니다.  

- **키 이름:** SQLSSBPort  

    - **필수:** 예  

    - **값:**  <*SSB 포트 번호*>  

    - **세부 정보:** SQL Server가 사용하는 SSB 포트를 지정합니다. 기본적으로 SSB는 TCP 포트 4022를 사용합니다. 실패하기 전에 사용했던 SSB 포트를 지정합니다.  

- **키 이름:** SQLDataFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .mdb 파일 경로*>  

    - **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

- **키 이름:** SQLLogFilePath  

    - **필수:** 아니요  

    - **값:**  <*데이터베이스 .ldf 파일 경로*>  

    - **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

#### <a name="hierarchyexpansionoptions"></a>HierarchyExpansionOptions

- **키 이름:** CCARSiteServer  

    - **필수:** 세부 정보 참조  

    - **값:**  <*CAS의 사이트 코드*>  

    - **세부 정보:** 기본 사이트가 Configuration Manager 계층 구조에 조인할 때 연결하는 CAS를 지정합니다. 실패하기 전에 기본 사이트가 CAS에 연결되었던 경우 이 설정은 필수입니다. 실패하기 전에 CAS에서 사용했던 사이트 코드를 지정합니다.  

- **키 이름:** CASRetryInterval  

    - **필수:** 아니요  

    - **값:**  <*간격(분)* >  

    - **세부 정보:** 연결에 실패한 후 CAS를 연결하려고 다시 시도하는 간격(분)을 지정합니다. 예를 들어 CAS에 연결하지 못한 기본 사이트는 **CASRetryInterval** 값으로 지정된 시간(분) 동안 기다린 다음 연결을 다시 시도합니다.  

- **키 이름:** WaitForCASTimeout  

    - **필수:** 아니요  

    - **값:**  <*시간 제한(분)* >  

    - **세부 정보:** 기본 사이트가 CAS에 연결하는 최대 시간 제한 값(분)을 지정합니다. 예를 들어 기본 사이트가 CAS에 연결하지 못하면 **WaitForCASTimeout** 기간에 도달할 때까지 기본 사이트는 **CASRetryInterval** 값을 기반으로 CAS에 연결을 다시 시도합니다. `0` ~ `100` 값을 지정할 수 있습니다.  

#### <a name="cloudconnectoroptions"></a>CloudConnectorOptions

- **키 이름:** CloudConnector  

    - **필수:** 예  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 `0`이어야 합니다.  

- **키 이름:** CloudConnectorServer  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*서비스 연결 지점 서버 FQDN*>  

    - **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

- **키 이름:** UseProxy  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**

        - `0` = 설치 안 함  

        - `1` = 설치  

    - **세부 정보:** 서비스 연결점에서 프록시 서버를 사용할지 여부를 지정합니다.  

- **키 이름:** ProxyName  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*프록시 서버 FQDN*>  

    - **세부 정보:** 서비스 연결점에서 사용하는 프록시 서버의 FQDN을 지정합니다.  

- **키 이름:** ProxyPort  

    - **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    - **값:**  <*포트 번호*>  

    - **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  
