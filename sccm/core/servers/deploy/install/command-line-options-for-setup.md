---
title: "설치 명령줄 옵션"
titleSuffix: Configuration Manager
description: "이 문서의 정보를 사용하여 명령줄에서 스크립트를 구성하거나 System Center Configuration Manager를 설치할 수 있습니다."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0da167f1-52cf-4dfd-8f73-833ca3eb8478
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 21b35888b6d3790736f204faca4458227fe0b6d3
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="command-line-options-for-setup-in-system-center-configuration-manager"></a>System Center Configuration Manager 설치를 위한 명령줄 옵션

*적용 대상: System Center Configuration Manager(현재 분기)*


 다음 정보를 사용하여 명령줄에서 스크립트를 구성하거나 System Center Configuration Manager를 설치할 수 있습니다.  

##  <a name="bkmk_setup"></a> 설치용 명령줄 옵션  
 **/DEINSTALL**  
 사이트를 제거합니다. 사이트 서버 컴퓨터에서 설치 프로그램을 실행해야 합니다.  

 **/DONTSTARTSITECOMP**  
 사이트를 설치하지만 Site Component Manager 서비스가 시작되지 않도록 합니다. Site Component Manager 서비스가 시작될 때까지 사이트는 활성화되지 않습니다. Site Component Manager는 SMS_Executive 서비스와 사이트의 추가 프로세스를 설치하고 시작합니다. 사이트 설치가 완료된 후에 Site Component Manager 서비스를 시작하면 SMS_Executive 서비스와 사이트 작동에 필요한 추가 프로세스가 설치됩니다.  

 **/HIDDEN**  
 설치하는 동안 사용자 인터페이스를 숨깁니다. 이 옵션은 **/SCRIPT** 옵션과 함께 사용해야 합니다. 무인 스크립트 파일에 필요한 모든 옵션을 지정해야 합니다. 지정하지 않으면 설치가 실패합니다.  

 **/NOUSERINPUT**  
 설치 시 사용자 입력을 사용하지 않도록 설정하지만 설치 마법사를 표시합니다. 이 옵션은 **/SCRIPT** 옵션과 함께 사용해야 합니다. 무인 스크립트 파일에 필요한 모든 옵션을 지정해야 합니다. 지정하지 않으면 설치가 실패합니다.  

 **/RESETSITE**  
 사이트의 데이터베이스 및 서비스 계정을 다시 설정하는 사이트 다시 설정을 수행합니다. 사이트 서버의 **<*Configuration Manager 설치 경로*>\BIN\X64**에서 설치 프로그램을 실행해야 합니다. 사이트 다시 설정에 대한 자세한 내용은 [System Center Configuration Manager 인프라 수정](../../../../core/servers/manage/modify-your-infrastructure.md)의 [사이트 다시 설정 실행](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_reset) 섹션을 참조하세요.  

 **/TESTDBUPGRADE <*인스턴스 이름*>\\<*데이터베이스 이름*>**  
 데이터베이스의 업그레이드 가능성을 확인하기 위해 사이트 데이터베이스의 백업에 대한 테스트를 수행합니다. 사이트 데이터베이스의 인스턴스 이름과 데이터베이스 이름을 지정해야 합니다. 데이터베이스 이름만 지정하면 설치 프로그램이 기본 인스턴스 이름을 사용합니다.  

> [!IMPORTANT]  
>  프로덕션 사이트 데이터베이스에서는 이 명령줄 옵션을 실행하지 마세요. 프로덕션 사이트 데이터베이스에서 이 명령줄 옵션을 실행하면 사이트 데이터베이스가 업그레이드되어 사이트가 작동하지 않을 수 있습니다.  

 **/UPGRADE**  
 사이트의 자동 업그레이드를 실행합니다. **/UPGRADE**를 사용하는 경우 대시(-)를 포함하여 제품 키를 지정해야 합니다. 또한 이전에 다운로드한 설치 필수 구성 요소 파일의 경로를 지정해야 합니다.  

 예: `setupwpf.exe /UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx <path to external component files>`  

 설치 필수 구성 요소 파일에 대한 자세한 내용은 [설치 다운로더](setup-downloader.md)를 참조하세요.  

 **/SCRIPT <*설치 스크립트 경로*>**  
 무인 설치를 수행합니다. **/SCRIPT** 옵션을 사용하는 경우 설치 초기화 파일이 필요합니다. 무인 설치를 실행하는 방법에 대한 자세한 내용은 [명령줄을 사용하여 System Center Configuration Manager 사이트 설치](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md)를 참조하세요.  

 **/SDKINST <*SMS 공급자 FQDN*>**  
 지정된 컴퓨터에서 SMS 공급자를 설치합니다. SMS 공급자 컴퓨터의 FQDN(정규화된 도메인 이름)을 입력해야 합니다. SMS 공급자에 대한 자세한 내용은 [System Center Configuration Manager용 SMS 공급자에 대한 계획](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)을 참조하세요.  

 **/SDKDEINST <*SMS 공급자 FQDN*>**  
 지정된 컴퓨터에서 SMS 공급자를 제거합니다. SMS 공급자 컴퓨터의 FQDN을 입력해야 합니다.  

 **/MANAGELANGS <*언어 스크립트 경로*>**  
 이전에 설치한 사이트에 설치된 언어를 관리합니다. 이 옵션을 사용하려면 사이트 서버의 **<*Configuration Manager 설치 경로*>\BIN\X64**에서 설치 프로그램을 실행하고 언어 설정이 포함된 언어 스크립트 파일의 위치를 지정해야 합니다. 언어 설정 스크립트 파일에서 사용할 수 있는 언어 옵션에 대한 자세한 내용은 이 항목에서 [언어 관리용 명령줄 옵션](#bkmk_Lang)을 참조하세요.  

##  <a name="bkmk_Lang"></a> 언어 관리용 명령줄 옵션  
 **Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** ManageLanguages  

    -   **세부 정보:** 사이트의 서버, 클라이언트 및 모바일 클라이언트 언어 지원을 관리합니다.  

**Options**  

-   **키 이름:** AddServerLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 사용할 수 있는 서버 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

-   **키 이름:** AddClientLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 클라이언트 컴퓨터에 사용할 수 있는 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

-   **키 이름:** DeleteServerLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 제거할 언어를 지정합니다. 해당 언어는 Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용할 수 있으며 제거할 수 없습니다.  

-   **키 이름:** DeleteClientLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 제거할 언어를 지정합니다. 해당 언어는 클라이언트 컴퓨터에서 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용할 수 있으며 제거할 수 없습니다.  

-   **키 이름:** MobileDeviceLanguage  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 모바일 장치 클라이언트 언어의 설치 여부를 지정합니다.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0**값을 사용하는 경우 파일이 다운로드됩니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치 필수 구성 요소 파일 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

##  <a name="bkmk_Unattended"></a> 무인 설치 스크립트 파일 키  
 다음 섹션에서는 무인 설치를 위한 스크립트를 생성하는 방법을 설명합니다. 목록에는 사용 가능한 설치 스크립트 키, 해당 값, 필수 여부, 설치 유형, 키에 대한 간략한 설명이 나와 있습니다.  

### <a name="unattended-install-for-a-central-administration-site"></a>중앙 관리 사이트의 무인 설치  
 다음에서는 무인 설치 스크립트 파일을 사용하여 중앙 관리 사이트를 설치하는 방법을 설명합니다.  

**Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** InstallCAS  

    -   **세부 정보:** 중앙 관리 사이트를 설치합니다.  

-   **키 이름:** CDLatest  

    -   **필수:** 예 – CD.Latest 폴더의 미디어를 사용할 경우에만.    

    -   **값:** 1 1이 아닌 임의 값은 CD.Latest를 사용하지 않는 것으로 간주합니다.

    -   **세부 정보:** 기본 또는 중앙 관리 사이트를 설치하거나 기본 또는 중앙 관리 사이트를 복구할 복적으로 CD.Latest 폴더에 있는 미디어의 설치 프로그램을 실행할 경우 키 및 값을 스크립트에 포함해야 합니다. 이 값은 미디어 양식 CD.Latest가 사용되고 있음을 설치 프로그램에 알립니다.

**Options**  

-   **키 이름:** ProductID  

    -   **필수:** 예  

    -   **값:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *또는* Eval  

    -   **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다. Configuration Manager의 평가 버전을 설치하려면 **Eval**을 입력합니다.  

-   **키 이름:** SiteCode  

    -   **필수:** 예  

    -   **값:** <*사이트 코드*>  

    -   **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다.  

-   **키 이름:** 사이트 이름  

    -   **필수:** 예  

    -   **값:** <*사이트 이름*>  

    -   **세부 정보:** 이 사이트의 이름을 지정합니다.  

-   **키 이름:** SMSInstallDir  

    -   **필수:** 예  

    -   **값:** <*Configuration Manager 설치 경로*>  

    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

-   **키 이름:** SDKServer  

    -   **필수:** 예  

    -   **값:** <*SMS 공급자 FQDN*>  

    -   **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0** 값을 사용하면 설치 프로그램이 파일을 다운로드합니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치 필수 구성 요소 파일 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

-   **키 이름:** AdminConsole  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

-   **키 이름:** JoinCEIP  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 참여 안 함  

         1 = 참여  

    -   **세부 정보:** CEIP(사용자 환경 개선 프로그램)에 참여할지 여부를 지정합니다.  

-   **키 이름:** AddServerLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 사용할 수 있는 서버 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

-   **키 이름:** AddClientLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 클라이언트 컴퓨터에 사용할 수 있는 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

-   **키 이름:** DeleteServerLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 사이트를 설치한 후 사이트를 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용할 수 있으며 제거할 수 없습니다.  

-   **키 이름:** DeleteClientLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 사이트를 설치한 후 사이트를 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 클라이언트 컴퓨터에서 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용할 수 있으며 제거할 수 없습니다.  

-   **키 이름:** MobileDeviceLanguage  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 모바일 장치 클라이언트 언어의 설치 여부를 지정합니다.  

**SQLConfigOptions**  

-   **키 이름:** SQLServerName  

    -   **필수:** 예  

    -   **값:** <*SQL Server 이름*>  

    -   **세부 정보:** 사이트 데이터베이스를 호스트할 SQL Server가 실행 중인 클러스터된 인스턴스 또는 서버의 이름을 지정합니다.  

-   **키 이름:** DatabaseName  

    -   **필수:** 예  

    -   **값:** <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>  

    -   **세부 정보:** 중앙 관리 사이트 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다.  

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.  

-   **키 이름:** SQLSSBPort  

    -   **필수:** 아니요  

    -   **값:** <*SSB 포트 번호*>  

    -   **세부 정보:** SQL Server가 사용하는 SSB(SQL Server Service Broker) 포트를 지정합니다. 일반적으로 SSB는 TCP 포트 4022를 사용하도록 구성되지만 다른 포트를 사용할 수도 있습니다.  

-   **키 이름:** SQLDataFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .mdb 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

-   **키 이름:** SQLLogFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .ldf 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

**CloudConnectorOptions**  

-   **키 이름:** CloudConnector  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 **0**이어야 합니다.  

-   **키 이름:** CloudConnectorServer  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*서비스 연결 지점 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

-   **키 이름:** UseProxy  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 서비스 연결 지점에서 프록시 서버를 사용할지 여부를 지정합니다.  

-   **키 이름:** ProxyName  

    -   **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    -   **값:** <*프록시 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할에서 사용할 프록시 서버의 FQDN을 지정합니다.  

-   **키 이름:** ProxyPort  

    -   **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    -   **값:** <*포트 번호*>  

    -   **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  

### <a name="unattended-install-for-a-primary-site"></a>기본 사이트의 무인 설치  
다음에서는 무인 설치 스크립트 파일을 사용하여 기본 사이트를 설치하는 방법을 설명합니다.  

**Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** InstallPrimarySite  

    -   **세부 정보:** 기본 사이트를 설치합니다.  

-   **키 이름:** CDLatest  

    -   **필수:** 예 – CD.Latest 폴더의 미디어를 사용할 경우에만.    

    -   **값:** 1 1이 아닌 임의 값은 CD.Latest를 사용하지 않는 것으로 간주합니다.

    -   **세부 정보:** 기본 또는 중앙 관리 사이트를 설치하거나 기본 또는 중앙 관리 사이트를 복구할 복적으로 CD.Latest 폴더에 있는 미디어의 설치 프로그램을 실행할 경우 키 및 값을 스크립트에 포함해야 합니다. 이 값은 미디어 양식 CD.Latest가 사용되고 있음을 설치 프로그램에 알립니다.

**Options**  

-   **키 이름:** ProductID  

    -   **필수:** 예  

    -   **값:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *또는* Eval  

    -   **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다. Configuration Manager의 평가 버전을 설치하려면 **Eval**을 입력합니다.  

-   **키 이름:** SiteCode  

    -   **필수:** 예  

    -   **값:** <*사이트 코드*>  

    -   **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다.  

-   **키 이름:** SiteName  

    -   **필수:** 예  

    -   **값:** <*사이트 이름*>  

    -   **세부 정보:** 이 사이트의 이름을 지정합니다.  

-   **키 이름:** SMSInstallDir  

    -   **필수:** 예  

    -   **값:** <*Configuration Manager 설치 경로*>

    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

-   **키 이름:** SDKServer  

    -   **필수:** 예  

    -   **값:** <*SMS 공급자 FQDN*>  

    -   **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0** 값을 사용하면 설치 프로그램이 파일을 다운로드합니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치 필수 구성 요소 파일 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

-   **키 이름:** AdminConsole  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

-   **키 이름:** JoinCEIP  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 참여 안 함  

         1 = 참여  

    -   **세부 정보:** CEIP에 참여할지 여부를 지정합니다.  

-   **키 이름:** ManagementPoint  

    -   **필수:** 아니요  

    -   **값:** <*관리 지점 사이트 서버 FQDN*>  

    -   **세부 정보:** 관리 지점 사이트 시스템 역할을 호스트할 서버의 FQDN을 지정합니다.  

-   **키 이름:** ManagementPointProtocol  

    -   **필수:** 아니요  

    -   **값:** HTTPS *또는* HTTP  

    -   **세부 정보:** 관리 지점에 사용할 프로토콜을 지정합니다.  

-   **키 이름:** DistributionPoint  

    -   **필수:** 아니요  

    -   **값:** <*배포 지점 사이트 서버 FQDN*>  

    -   **세부 정보:** 배포 지점에 사용할 프로토콜을 지정합니다.  

-   **키 이름:** DistributionPointProtocol  

    -   **필수:** 아니요  

    -   **값:** HTTPS *또는* HTTP  

    -   **세부 정보:** 배포 지점에 사용할 프로토콜을 지정합니다.  

-   **키 이름:** RoleCommunicationProtocol  

    -   **필수:** 예  

    -   **값:** EnforceHTTPS *또는*  HTTPorHTTPS  

    -   **세부 정보:** 클라이언트의 HTTPS 통신만 수락하도록 모든 사이트 시스템을 구성할지, 아니면 각 사이트 시스템 역할마다 다른 통신 방법을 구성할지를 지정합니다. **EnforceHTTPS**를 선택하는 경우 클라이언트 컴퓨터에 클라이언트 인증을 위해 유효한 PKI(공개 키 인프라) 인증서가 있어야 합니다.  

-   **키 이름:** ClientsUsePKICertificate  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 사용 안 함  

         1 = 사용  

    -   **세부 정보:** 클라이언트가 클라이언트 PKI 인증서를 사용하여 사이트 시스템 역할과 통신할지 여부를 지정합니다.  

-   **키 이름:** AddServerLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 사용할 수 있는 서버 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

-   **키 이름:** AddClientLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 클라이언트 컴퓨터에 사용할 수 있는 언어를 지정합니다. 영어는 기본적으로 사용할 수 있습니다.  

-   **키 이름:** DeleteServerLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 사이트를 설치한 후 사이트를 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 Configuration Manager 콘솔, 보고서 및 Configuration Manager 개체에 대해 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용할 수 있으며 제거할 수 없습니다.  

-   **키 이름:** DeleteClientLanguages  

    -   **필수:** 아니요  

    -   **값:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK 또는 ZHH  

    -   **세부 정보:** 사이트를 설치한 후 사이트를 수정합니다. 제거할 언어를 지정합니다. 해당 언어는 클라이언트 컴퓨터에서 더 이상 사용할 수 없습니다. 영어는 기본적으로 사용할 수 있으며 제거할 수 없습니다.  

-   **키 이름:** MobileDeviceLanguage  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 모바일 장치 클라이언트 언어의 설치 여부를 지정합니다.  

**SQLConfigOptions**  

-   **키 이름:** SQLServerName  

    -   **필수:** 예  

    -   **값:** <*SQL Server 이름*>  

    -   **세부 정보:** 사이트 데이터베이스를 호스트할 SQL Server가 실행 중인 클러스터된 인스턴스 또는 서버의 이름을 지정합니다.  

-   **키 이름:** DatabaseName  

    -   **필수:** 예  

    -   **값:** <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>  

    -   **세부 정보:** 기본 사이트 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다.  

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.  

-   **키 이름:** SQLSSBPort  

    -   **필수:** 아니요  

    -   **값:** <*SSB 포트 번호*>  

    -   **세부 정보:** SQL Server가 사용하는 SSB 포트를 지정합니다. 일반적으로 SSB는 TCP 포트 4022를 사용하도록 구성되지만 다른 포트를 사용할 수도 있습니다.  

-   **키 이름:** SQLDataFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .mdb 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

-   **키 이름:** SQLLogFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .ldf 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

**HierarchyExpansionOption**  

-   **키 이름:** CCARSiteServer  

    -   **필수:** 아니요  

    -   **값:** <*중앙 관리 사이트 FQDN*>  

    -   **세부 정보:** 기본 사이트가 Configuration Manager 계층 구조에 가입할 때 연결할 중앙 관리 사이트를 지정합니다. 중앙 관리 사이트는 설치하는 동안 지정해야 합니다.  

-   **키 이름:** CASRetryInterval  

    -   **필수:** 아니요  

    -   **값:** <*간격*>  

    -   **세부 정보:** 연결에 실패한 후 중앙 관리 사이트를 연결하려고 다시 시도하는 간격(분)을 지정합니다. 예를 들어 중앙 관리 사이트에 연결하지 못한 기본 사이트는 **CASRetryInterval** 값으로 지정된 시간(분) 동안 기다린 다음 연결을 다시 시도합니다.  

-   **키 이름:** WaitForCASTimeout  

    -   **필수:** 아니요  

    -   **값:** <*시간 제한*>  

         **0**~**100** 값  

    -   **세부 정보:** 기본 사이트가 중앙 관리 사이트에 연결하는 최대 시간 제한 값(분)을 지정합니다. 예를 들어 기본 사이트가 중앙 관리 사이트에 연결하지 못하면 **WaitForCASTimeout** 기간에 도달할 때까지 기본 사이트는 **CASRetryInterval** 값을 기반으로 중앙 관리 사이트에 연결하려고 다시 시도합니다. **0**~**100** 값을 지정할 수 있습니다.  

**CloudConnectorOptions**  

-   **키 이름:** CloudConnector  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 **0**이어야 합니다.  

-   **키 이름:** CloudConnectorServer  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*서비스 연결 지점 서버 FQDN*\>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

-   **키 이름:** UseProxy  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 서비스 연결 지점에서 프록시 서버를 사용할지 여부를 지정합니다.  

-   **키 이름:** ProxyName  

    -   **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    -   **값:** <*프록시 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할에서 사용할 프록시 서버의 FQDN을 지정합니다.  

-   **키 이름:** ProxyPort  

    -   **필수:** **UseProxy**가 1인 경우에 필수입니다.  

    -   **값:** <*포트 번호*>  

    -   **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  

### <a name="unattended-recovery-for-a-central-administration-site"></a>중앙 관리 사이트의 무인 복구  
 다음에서는 무인 설치 스크립트 파일을 사용하여 중앙 관리 사이트를 복구하는 방법에 대해 설명합니다.  

**Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** RecoverCCAR  

    -   **세부 정보:** 중앙 관리 사이트를 복구합니다.  

-   **키 이름:** CDLatest  

    -   **필수:** 예 – CD.Latest 폴더의 미디어를 사용할 경우에만.    

    -   **값:** 1 1이 아닌 임의 값은 CD.Latest를 사용하지 않는 것으로 간주합니다.

    -   **세부 정보:** 기본 또는 중앙 관리 사이트를 설치하거나 기본 또는 중앙 관리 사이트를 복구할 복적으로 CD.Latest 폴더에 있는 미디어의 설치 프로그램을 실행할 경우 키 및 값을 스크립트에 포함해야 합니다. 이 값은 미디어 양식 CD.Latest가 사용되고 있음을 설치 프로그램에 알립니다.

**RecoveryOptions**  

-   **키 이름:** ServerRecoveryOptions  

    -   **필수:** 예  

    -   **값:** 1, 2 또는 4  

         1 = 사이트 서버와 SQL Server 복구  

         2 = 사이트 서버만 복구  

         4 = SQL Server만 복구  

    -   **세부 정보:** 설치 프로그램이 복구할 대상(사이트 서버, SQL Server, 둘 다)을 지정합니다. **ServerRecoveryOptions** 설정에 대해 다음 값을 설정하는 경우 연결된 키는 필수입니다.  

        -   값 = 1: 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

        -   값 = 2: 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

        -   값 = 4: **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

-   **키 이름:** DatabaseRecoveryOptions  

    -   **필수:** **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.  

    -   **값:** 10, 20, 40 또는 80  

         10 = 백업에서 사이트 데이터베이스 복구  

         20 = 다른 방법을 사용하여 수동으로 복구된 사이트 데이터베이스 사용  

         40 = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 글로벌 데이터 및 사이트 데이터는 다른 사이트를 복제하여 복구됩니다.  

         80 = 데이터베이스 복구 건너뛰기  

    -   **세부 정보:** SQL Server의 사이트 데이터베이스를 복구하는 방법을 지정합니다.  

-   **키 이름:** ReferenceSite  

    -   **필수:** **DatabaseRecoveryOptions** 설정 값이 **40**인 경우 이 키는 필수입니다.  

    -   **값:** <*참조 사이트 FQDN*>  

    -   **세부 정보:** 데이터베이스 백업이 변경 내용 추적 보존 기간보다 오래 되었거나 백업 없이 사이트를 복구할 경우 중앙 관리 사이트에서 글로벌 데이터를 복구하는 데 사용하는 참조 기본 사이트를 지정합니다.  

         참조 사이트를 지정하지 않았는데 백업이 변경 추적 보존 기간보다 오래된 경우 모든 기본 사이트는 중앙 관리 사이트에서 복원된 데이터로 다시 초기화됩니다.  

         참조 사이트를 지정하지 않았지만 백업이 변경 추적 보존 기간 내에 있는 경우 백업 이후 적용된 변경 내용만 기본 사이트에 복제됩니다. 서로 다른 기본 사이트 간에 충돌하는 변경 내용이 있으면 중앙 관리 사이트에서는 가장 먼저 수신한 변경 내용을 사용합니다.  

-   **키 이름:** SiteServerBackupLocation  

    -   **필수:** 아니요  

    -   **값:** <*사이트 서버 백업 집합 경로*>  

    -   **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

-   **키 이름:** BackupLocation  

    -   **필수:** **ServerRecoveryOptions** 키 값을 **1** 또는 **4**로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10**으로 구성하는 경우 이 키는 필수입니다.  

    -   **값:** <*사이트 데이터베이스 백업 집합 경로*>  

    -   **세부 정보:** 사이트 데이터베이스 백업 집합의 경로를 지정합니다.  

**Options**  

-   **키 이름:** ProductID  

    -   **필수:** 예  

    -   **값:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *또는* Eval  

    -   **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다. Configuration Manager의 평가 버전을 설치하려면 **Eval**을 입력합니다.  

-   **키 이름:** SiteCode  

    -   **필수:** 예  

    -   **값:** <*사이트 코드*>  

    -   **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다. 장애가 발생하기 전에 사이트에 사용되던 사이트 코드를 지정해야 합니다.

-   **키 이름:** SiteName  

    -   **필수:** 아니요  

    -   **값:** <*사이트 이름*>  

    -   **세부 정보:** 이 사이트의 이름을 지정합니다.  

-   **키 이름:** SMSInstallDir  

    -   **필수:** 예  

    -   **값:** <*Configuration Manager 설치 경로*>  

    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

-   **키 이름:** SDKServer  

    -   **필수:** 예  

    -   **값:** <*SMS 공급자 FQDN*>  

    -   **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정해야 합니다.  

         초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다. SMS 공급자에 대한 자세한 내용은 [System Center Configuration Manager용 SMS 공급자에 대한 계획](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)을 참조하세요.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0**값을 사용하는 경우 파일이 다운로드됩니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치 필수 구성 요소 파일 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

-   **키 이름:** AdminConsole  

    -   **필수:** **ServerRecoveryOptions** 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

-   **키 이름:** JoinCEIP  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 참여 안 함  

         1 = 참여  

    -   **세부 정보:** CEIP에 참여할지 여부를 지정합니다.  

**SQLConfigOptions**  

-   **키 이름:** SQLServerName  

    -   **필수:** 예  

    -   **값:** <*SQL Server 이름*>  

    -   **세부 정보:** 사이트 데이터베이스를 호스트할 SQL Server가 실행 중인 클러스터된 인스턴스 또는 서버의 이름을 지정합니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정해야 합니다.  

-   **키 이름:** DatabaseName  

    -   **필수:** 예  

    -   **값:** <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>  

    -   **세부 정보:** 중앙 관리 사이트 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정해야 합니다.  

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.  

-   **키 이름:** SQLSSBPort  

    -   **필수:** 예  

    -   **값:** <*SSB 포트 번호*>  

    -   **세부 정보:** SQL Server가 사용하는 SSB 포트를 지정합니다. 일반적으로 SSB는 TCP 포트 4022를 사용하도록 구성됩니다. 실패하기 전에 사용했던 SSB 포트를 지정해야 합니다.  

-   **키 이름:** SQLDataFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .mdb 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

-   **키 이름:** SQLLogFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .ldf 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

**CloudConnectorOptions**  

-   **키 이름:** CloudConnector  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 **0**이어야 합니다.  

-   **키 이름:** CloudConnectorServer  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*서비스 연결 지점 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

-   **키 이름:** UseProxy  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 서비스 연결 지점에서 프록시 서버를 사용할지 여부를 지정합니다.  

-   **키 이름:** ProxyName  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*프록시 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할에서 사용할 프록시 서버의 FQDN을 지정합니다.  

-   **키 이름:** ProxyPort  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*포트 번호*>  

    -   **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  

### <a name="unattended-recovery-for-a-primary-site"></a>기본 사이트의 무인 복구  
 다음에서는 무인 설치 스크립트 파일을 사용하여 기본 사이트를 복구하는 방법을 설명합니다.  

**Identification**  

-   **키 이름:** Action  

    -   **필수:** 예  

    -   **값:** <*RecoverPrimarySite*>  

    -   **세부 정보:** 기본 사이트를 복구합니다.  

-   **키 이름:** CDLatest  

    -   **필수:** 예 – CD.Latest 폴더의 미디어를 사용할 경우에만.    

    -   **값:** 1 1이 아닌 임의 값은 CD.Latest를 사용하지 않는 것으로 간주합니다.

    -   **세부 정보:** 기본 또는 중앙 관리 사이트를 설치하거나 기본 또는 중앙 관리 사이트를 복구할 복적으로 CD.Latest 폴더에 있는 미디어의 설치 프로그램을 실행할 경우 키 및 값을 스크립트에 포함해야 합니다. 이 값은 미디어 양식 CD.Latest가 사용되고 있음을 설치 프로그램에 알립니다.    

**RecoveryOptions**  

-   **키 이름:** ServerRecoveryOptions  

    -   **필수:** 예  

    -   **값:** 1, 2 또는 4  

         1 = 사이트 서버와 SQL Server 복구  

         2 = 사이트 서버만 복구  

         4 = SQL Server만 복구  

    -   **세부 정보:** 설치 프로그램이 복구할 대상(사이트 서버, SQL Server, 둘 다)을 지정합니다. **ServerRecoveryOptions** 설정에 대해 다음 값을 설정하는 경우 연결된 키는 필수입니다.  

        -   값 = 1: 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

        -   값 = 2: 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

        -   값 = 4: **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.  

-   **키 이름:** DatabaseRecoveryOptions  

    -   **필수:** **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.  

    -   **값:** 10, 20, 40 또는 80  

         10 = 백업에서 사이트 데이터베이스 복구  

         20 = 다른 방법을 사용하여 수동으로 복구된 사이트 데이터베이스 사용  

         40 = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 글로벌 데이터 및 사이트 데이터는 다른 사이트를 복제하여 복구됩니다.  

         80 = 데이터베이스 복구 건너뛰기  

    -   **세부 정보:** SQL Server의 사이트 데이터베이스를 복구하는 방법을 지정합니다.  

-   **키 이름:** SiteServerBackupLocation  

    -   **필수:** 아니요  

    -   **값:** <*사이트 서버 백업 집합 경로*>  

    -   **세부 정보:**  

         사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.  

-   **키 이름:** BackupLocation  

    -   **필수:** **ServerRecoveryOptions** 키 값을 **1** 또는 **4**로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10**으로 구성하는 경우 이 키는 필수입니다.  

    -   **값:** <*사이트 데이터베이스 백업 집합 경로*>  

    -   **세부 정보:** 사이트 데이터베이스 백업 집합의 경로를 지정합니다.  

**Options**  

-   **키 이름:** ProductID  

    -   **필수:** 예  

    -   **값:** *xxxxx-xxxxx-xxxxx-xxxxx-xxxxx* 또는 *Eval*  

    -   **세부 정보:** 대시를 포함하여 Configuration Manager 설치 제품 키를 지정합니다. Configuration Manager의 평가 버전을 설치하려면 **Eval**을 입력합니다.  

-   **키 이름:** SiteCode  

    -   **필수:** 예  

    -   **값:** <*사이트 코드*>  

    -   **세부 정보:** 계층에서 사이트를 고유하게 식별하는 영숫자 3자를 지정합니다. 장애가 발생하기 전에 사이트에 사용되던 사이트 코드를 지정해야 합니다.

-   **키 이름:** SiteName  

    -   **필수:** 아니요  

    -   **값:** <*사이트 이름*>  

    -   **세부 정보:** 이 사이트의 이름을 지정합니다.  

-   **키 이름:** SMSInstallDir  

    -   **필수:** 예  

    -   **값:** <*Configuration Manager 설치 경로*>  

    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.  

-   **키 이름:** SDKServer  

    -   **필수:** 예  

    -   **값:** <*SMS 공급자 FQDN*>  

    -   **세부 정보:** SMS 공급자를 호스트할 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정해야 합니다. 초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다. SMS 공급자에 대한 자세한 내용은 [System Center Configuration Manager용 SMS 공급자에 대한 계획](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)을 참조하세요.  

-   **키 이름:** PrerequisiteComp  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 다운로드  

         1 = 이미 다운로드됨  

    -   **:** 설치를 위한 필수 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 **0**값을 사용하는 경우 파일이 다운로드됩니다.  

-   **키 이름:** PrerequisitePath  

    -   **필수:** 예  

    -   **값:** <*설치 필수 구성 요소 파일 경로*>  

    -   **세부 정보:** 설치를 위한 필수 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.  

-   **키 이름:** AdminConsole  

    -   **필수:** **ServerRecoveryOptions** 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다.  

-   **키 이름:** JoinCEIP  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 참여 안 함  

         1 = 참여  

    -   **세부 정보:** CEIP에 참여할지 여부를 지정합니다.  

**SQLConfigOptions**  

-   **키 이름:** SQLServerName  

    -   **필수:** 예  

    -   **값:** <*SQL Server 이름*>  

    -   **세부 정보:** 사이트 데이터베이스를 호스트할 SQL Server가 실행 중인 클러스터된 인스턴스 또는 서버의 이름을 지정합니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정해야 합니다.  

-   **키 이름:** DatabaseName  

    -   **필수:** 예  

    -   **값:**  <*사이트 데이터베이스 이름*> 또는 <*인스턴스 이름*>\\<*사이트 데이터베이스 이름*>

    -   **세부 정보:**  

         중앙 관리 사이트 데이터베이스를 설치할 때 사용하거나 만들 SQL Server 데이터베이스의 이름을 지정합니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정해야 합니다.  

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.  

-   **키 이름:** SQLSSBPort  

    -   **필수:** 예  

    -   **값:** <*SSB 포트 번호*>  

    -   **세부 정보:** SQL Server가 사용하는 SSB 포트를 지정합니다. 일반적으로 SSB는 TCP 포트 4022를 사용하도록 구성됩니다. 실패하기 전에 사용했던 SSB 포트를 지정해야 합니다.  

-   **키 이름:** SQLDataFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .mdb 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .mdb 파일을 만들 대체 위치를 지정합니다.  

-   **키 이름:** SQLLogFilePath  

    -   **필수:** 아니요  

    -   **값:** <*데이터베이스 .ldf 파일 경로*>  

    -   **세부 정보:** 데이터베이스 .ldf 파일을 만들 대체 위치를 지정합니다.  

**HierarchyExpansionOptions**  

-   **키 이름:** CCARSiteServer  

    -   **필수:** 세부 정보를 참조하세요.  

    -   **값:** <*중앙 관리 사이트의 사이트 코드*>  

    -   **세부 정보:** 기본 사이트가 Configuration Manager 계층에 가입할 때 연결할 중앙 관리 사이트를 지정합니다. 실패하기 전에 기본 사이트가 중앙 관리 사이트에 연결되었던 경우 이 설정은 필수입니다. 실패하기 전에 중앙 관리 사이트에 사용했던 사이트 코드를 지정해야 합니다.  

-   **키 이름:** CASRetryInterval  

    -   **필수:** 아니요  

    -   **값:** <*간격*>  

    -   **세부 정보:** 연결에 실패한 후 중앙 관리 사이트를 연결하려고 다시 시도하는 간격(분)을 지정합니다. 예를 들어 중앙 관리 사이트에 연결하지 못한 기본 사이트는 **CASRetryInterval** 값으로 지정된 시간(분) 동안 기다린 다음 연결을 다시 시도합니다.  

-   **키 이름:** WaitForCASTimeout  

    -   **필수:** 아니요  

    -   **값:** <*시간 제한*>  

    -   **세부 정보:** 기본 사이트가 중앙 관리 사이트에 연결하는 최대 시간 제한 값(분)을 지정합니다. 예를 들어 기본 사이트가 중앙 관리 사이트에 연결하지 못하면 **WaitForCASTimeout** 기간에 도달할 때까지 기본 사이트는 **CASRetryInterval** 값을 기반으로 중앙 관리 사이트에 연결하려고 다시 시도합니다. **0**~**100** 값을 지정할 수 있습니다.  

**CloudConnectorOptions**  

-   **키 이름:** CloudConnector  

    -   **필수:** 예  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 이 사이트에 서비스 연결 지점을 설치할지 여부를 지정합니다. 서비스 연결 지점은 계층 구조의 최상위 계층 사이트에만 설치할 수 있으므로 이 값은 자식 기본 사이트에 대해 **0**이어야 합니다.  

-   **키 이름:** CloudConnectorServer  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*서비스 연결 지점 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할을 호스트하는 서버의 FQDN을 지정합니다.  

-   **키 이름:** UseProxy  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** 0 또는 1  

         0 = 설치 안 함  

         1 = 설치  

    -   **세부 정보:** 서비스 연결 지점에서 프록시 서버를 사용할지 여부를 지정합니다.  

-   **키 이름:** ProxyName  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*프록시 서버 FQDN*>  

    -   **세부 정보:** 서비스 연결 지점 사이트 시스템 역할에서 사용할 프록시 서버의 FQDN을 지정합니다.  

-   **키 이름:** ProxyPort  

    -   **필수:** **CloudConnector**가 1인 경우에 필수입니다.  

    -   **값:** <*포트 번호*>  

    -   **세부 정보:** 프록시 포트에 사용할 포트 번호를 지정합니다.  
