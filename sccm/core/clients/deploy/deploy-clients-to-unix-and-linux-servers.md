---
title: "UNIX/Linux 클라이언트 배포 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 UNIX 또는 Linux 서버에 클라이언트를 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 15a4e323-9f42-4fea-bb14-f2b905d1f77c
caps.latest.revision: 9
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 77a0825346b461cdc3b36e5aabcb1e4e83135d6e


---
# <a name="how-to-deploy-clients-to-unix-and-linux-servers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 사용하여 Linux 또는 UNIX 서버를 관리하려면 먼저 각 Linux 또는 UNIX 서버에 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치해야 합니다. 각 컴퓨터에서 수동으로 클라이언트를 설치하거나 원격으로 클라이언트를 설치하는 셸 스크립트를 사용할 수 있습니다. Configuration Manager는 Linux 또는 UNIX 서버에 대한 클라이언트 강제 설치 사용을 지원하지 않습니다. 필요에 따라 Linux 또는 UNIX 서버에 자동으로 클라이언트를 설치하도록 System Center Orchestrator Runbook을 구성할 수 있습니다.  

 사용하는 설치 방법에 관계없이 설치 프로세스에서 **install** 이라는 스크립트를 사용하여 설치 프로세스를 관리해야 합니다. Linux 및 UNIX 용 클라이언트를 다운로드 하는 경우이 스크립트를 포함 됩니다.  

 Linux 및 UNIX용 Configuration Manager 클라이언트의 설치 스크립트는 명령줄 속성을 지원합니다. 일부 명령줄 속성은 필수 필드 이며 나머지는 선택 사항입니다. 예를들어, 클라이언트를 설치할 때 사이트와 해당 초기 연락처에 대 한 Linux 또는 UNIX 서버에 의해 사용 되는 사이트에서 관리 지점을 지정 해야 합니다. 명령줄 속성의 전체 목록은 [Linux 및 UNIX 서버에 클라이언트를 설치하기 위한 명령줄 속성](#BKMK_CmdLineInstallLnUClient)항목을 참조하세요.  

 클라이언트를 설치한 후 Configuration Manager 콘솔에서 클라이언트 설정을 지정하여 Windows 기반 클라이언트와 동일한 방식으로 클라이언트 에이전트를 구성합니다. 자세한 내용은 [Linux 및 UNIX 서버에 대한 클라이언트 설정](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ClientSettingsforLnU)을 참조하세요.  

##  <a name="a-namebkmkaboutinstallpackagesa-about-client-installation-packages-and-the-universal-agent"></a><a name="BKMK_AboutInstallPackages"></a> 클라이언트 설치 패키지 및 유니버설 에이전트에 대 한  
 특정 플랫폼에 Linux 및 UNIX용 클라이언트를 설치하려면 클라이언트를 설치할 컴퓨터에 해당하는 클라이언트 설치 패키지를 사용해야 합니다. 해당하는 클라이언트 설치 패키지는 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)의 각 클라이언트 다운로드에 포함되어 있습니다. 클라이언트 설치 패키지 외에도 클라이언트 다운로드에는 각 컴퓨터의 클라이언트 설치를 관리하는 **install** 스크립트가 들어 있습니다.  

 클라이언트를 설치할 때 사용 하면 클라이언트 설치 패키지에 관계 없이 동일한 프로세스 및 명령줄 속성을 사용할 수 있습니다.  

 각 Linux 및 UNIX용 Configuration Manager 클라이언트 릴리스에서 지원하는 운영 체제, 플랫폼 및 클라이언트 설치 패키지에 대한 자세한 내용은 [Linux 및 UNIX 서버](../../plan-design/configs/supported-operating-systems-for-clients-and-devices.md#bkmk_LinuxOS)를 참조하세요.  

##  <a name="a-namebkmkinstalllnuclienta-install-the-client-on-linux-and-unix-servers"></a><a name="BKMK_InstallLnUClient"></a> Linux 및 UNIX 서버에 클라이언트를 설치 합니다.  
 Linux 및 UNIX 용 클라이언트를 설치 하려면 각 Linux 또는 UNIX 컴퓨터에서 스크립트를 실행 합니다. 스크립트 라는 **설치** 설치 동작을 수정 하 고 클라이언트 설치 패키지를 참조 하는 명령줄 속성을 지원 합니다. 설치 스크립트 및 클라이언트 설치 패키지는 클라이언트에 위치 해야 합니다. 클라이언트 설치 패키지에는 특정 Linux 또는 UNIX 운영 체제 및 플랫폼에 대한 Configuration Manager 클라이언트 파일이 들어 있습니다.
각 클라이언트 설치 패키지는 클라이언트 설치를 완료 하는데 필요한 모든 파일을 포함 하며 달리 Windows 기반 컴퓨터에서 다운로드 하지 않습니다 추가 파일 관리 지점 또는 다른 원본 위치 합니다.  

 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치한 후 컴퓨터를 다시 부팅하지 않아도 됩니다. 소프트웨어 설치가 완료 되 면 즉시 클라이언트는 작동 합니다. 컴퓨터를 다시 부팅하는 경우 Configuration Manager 클라이언트는 자동으로 다시 시작합니다.  

 설치 된 클라이언트 루트 자격 증명으로 실행 됩니다. 하드웨어 인벤토리를 수집하고 소프트웨어 배포를 수행하려면 루트 자격 증명이 필요합니다.  

 명령 형식은 다음과 같습니다.  

 **./install -mp &lt;컴퓨터\> -sitecode &lt;사이트 코드\> &lt;속성 #1> &lt;속성 #2> &lt;클라이언트 설치 패키지\>**  

-   **설치** Linux 및 UNIX 용 클라이언트를 설치 하는 스크립트 파일의 이름입니다. 이 파일은 클라이언트 소프트웨어와 함께 제공 됩니다.  

-   **-mp &lt;컴퓨터**는 클라이언트에서 사용하는 초기 관리 지점을 지정합니다.  

     예: smsmp.contoso.com  

-   **-sitecode &lt;사이트 코드\>**는 클라이언트에 할당되는 사이트 코드를 지정합니다.  

     예: S01  

-   &lt;속성 #1> &lt;속성 #2>는 설치 스크립트에 사용할 명령줄 속성을 지정합니다.  

    > [!NOTE]  
    >  자세한 내용은 [Linux 및 UNIX 서버에 클라이언트를 설치하기 위한 명령줄 속성](#BKMK_CmdLineInstallLnUClient)  

-   **클라이언트 설치 패키지** 는 이 컴퓨터 운영 체제, 버전 및 CPU 아키텍처에 대한 클라이언트 설치 .tar 패키지의 이름입니다. 클라이언트 설치.tar 파일의 마지막에 지정 해야 합니다.  

     예: ccm-Universal-x64.&lt;build\>.tar  

###  <a name="a-namebkmktoinstalllnuclinenta-to-install-the-configuration-manager-client-on-linux-and-unix-servers"></a><a name="BKMK_ToInstallLnUClinent"></a> Linux 및 UNIX 서버에 Configuration Manager 클라이언트를 설치 하려면  

1.  Windows 컴퓨터에서 관리하려는 [Linux 또는 UNIX 서버의 적절한 클라이언트 파일을 다운로드](http://go.microsoft.com/fwlink/?LinkID=525184) 합니다.  

2.  Windows 컴퓨터에서 설치 스크립트를 추출하는 자동 압축 풀기.exe 파일 및 클라이언트 설치.tar 파일을 실행합니다.  

3.  관리하려는 서버의 폴더로 **설치** 스크립트 및 .tar 파일을 복사합니다.  

4.  UNIX 또는 Linux 서버에서 다음 명령을 실행하여 스크립트를 프로그램으로 실행할 수 있도록 합니다. **chmod +x install**  

    > [!IMPORTANT]  
    >  루트 자격 증명을 사용 하 여 클라이언트를 설치 해야 합니다.  

5.  다음으로, Configuration Manager 클라이언트를 설치하려면 **./install -mp &lt;호스트 이름\> -sitecode &lt;코드\> ccm-Universal-x64.&lt;빌드\>.tar** 명령을 실행합니다.  

     이 명령을 입력 하는 경우 필요한 추가 명령줄 속성을 사용 합니다.  명령줄 속성의 목록은 [Linux 및 UNIX 서버에 클라이언트를 설치하기 위한 명령줄 속성](#BKMK_CmdLineInstallLnUClient)을 참조하세요.  

6.  스크립트가 실행된 후 **/var/opt/microsoft/scxcm.log** 파일을 검토하여 설치의 유효성을 검사합니다. 또한 Configuration Manager 콘솔, **자산 및 준수** 작업 영역의 **장치** 노드에서 클라이언트 세부 정보를 통해 클라이언트가 설치되고 사이트와 통신하고 있는지 확인할 수 있습니다.  

###  <a name="a-namebkmkcmdlineinstalllnuclienta-command-line-properties-for-installing-the-client-on-linux-and-unix-servers"></a><a name="BKMK_CmdLineInstallLnUClient"></a> Linux 및 UNIX 서버에 클라이언트를 설치하기 위한 명령줄 속성  
 다음 속성은 설치 스크립트의 동작을 수정하는 데 사용할 수 있습니다.  

> [!NOTE]  
>  속성을 사용 하 여 **-h** 이 지원 되는 속성이 목록을 표시 합니다.  

-   **-mp &lt;서버 FQDN\>**  

     필수. FQDN, 클라이언트는 초기 연결 지점으로 사용 하는 관리 지점 서버를 지정 합니다.  

    > [!IMPORTANT]  
    >  이 속성은 설치 후에 클라이언트를 할당할 관리 지점은 지정하지 않습니다.  

    > [!NOTE]  
    >  **-mp** 속성을 사용하여 HTTPS 클라이언트 연결만 허용하도록 구성된 관리 지점을 지정하는 경우 **-UsePKICert** 속성도 사용해야 합니다.  

-   **-sitecode &lt;사이트 코드\>**  

     필수. Configuration Manager 클라이언트를 할당할 Configuration Manager 기본 사이트를 지정합니다.  

     예: -sitecode S01  

-   **-fsp &lt;server_FQDN>**  

     선택 사항입니다. FQDN, 상태 메시지를 전송 하는 클라이언트를 사용 하는 대체 상태 지점 서버를 지정 합니다.  

     대체 상태 지점에 대한 자세한 내용은 [대체 상태 지점 필요 여부 결정](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md#BKMK_Determine_FSP)을 참조하세요.  

-   **-dir &lt;디렉터리\>**  

     선택 사항입니다. Configuration Manager 클라이언트 파일을 설치할 대체 위치를 지정합니다.  

     기본적으로 클라이언트는 다음 위치에 설치: **/opt/microsoft**.  

-   **-nostart**  

     선택 사항입니다. 클라이언트 설치가 완료된 후 Configuration Manager 클라이언트 서비스 **ccmexec.bin**이 자동으로 시작되지 않도록 합니다.  

     클라이언트를 설치한 후 클라이언트 서비스를 수동으로 시작 해야 합니다.  

     기본적으로 클라이언트 서비스는 클라이언트 설치를 완료 하 고 컴퓨터를 다시 시작할 때마다 후 시작 합니다.  

-   **-정리**  

     선택 사항입니다. 새 설치를 시작 하기 전에 Linux 및 UNIX를 실행 하는 것에 대 한 모든 클라이언트 파일 및 이전에 설치 된 클라이언트에서 데이터의 제거를 지정 합니다. 이 클라이언트의 데이터베이스 및 인증서 저장소를 제거합니다.  

-   **-keepdb**  

     선택 사항입니다. 로컬 클라이언트 데이터베이스를 유지 하 고 클라이언트를 다시 설치할 때 다시 사용을 지정 합니다. 기본적으로 클라이언트를 다시 설치할 때이 데이터베이스가 삭제 됩니다.  

-   **-UsePKICert &lt;매개 변수\>**  

     선택 사항입니다. 공용 키 인증서 표준 (PKCS #12) 형식에 X.509 PKI 인증서에 전체 경로 파일 이름을 지정합니다. 이 인증서는 클라이언트 인증을 위해 사용 됩니다. 설치 중에 인증서를 지정하지 않았으며 인증서를 추가하거나 변경해야 하는 경우 **certutil** 유틸리티를 사용합니다. certutil에 대한 자세한 내용은 [Linux 및 UNIX용 클라이언트에서 인증서를 관리하는 방법](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts)을 참조하세요.  

     **-UsePKICert**를 사용하는 경우 **-certpw** 명령줄 매개 변수를 사용하여 PKCS #12 파일과 관련된 암호도 입력해야 합니다.  

     PKI 인증서를 지정 하려면이 속성을 사용 하지 않는 경우 자체 서명 된 인증서를 사용 하는 클라이언트 및 사이트 시스템에 대 한 모든 통신은 HTTP를 통해.  

     에 잘못 된 인증서를 지정 하는 경우 클라이언트 설치 명령줄, 오류가 반환 되지 않습니다. 인증서 유효성 검사는 클라이언트를 설치한 후 발생 때문입니다. 클라이언트 시작, 인증서는 관리 지점과 유효성이 검사 되 고 인증서 유효성 검사에 실패 하는 경우 다음 메시지가 나타납니다에 때 **scxcm.log**, Unix 및 Linux Configuration Manager 클라이언트 로그 파일: **실패 관리 지점에 대 한 인증서의 유효성을 검사**. 기본 로그 파일 위치는  **/var/opt/microsoft/scxcm.log**입니다.  

    > [!NOTE]  
    >  클라이언트를 설치할 때는 이 속성을 지정해야 하며, **-mp** 속성을 사용하여 HTTPS 클라이언트 연결만 허용하도록 구성된 관리 지점을 지정해야 합니다.  

     예: -UsePKICert &lt;전체 경로 및 파일 이름\> -certpw &lt;암호\>  

-   **-certpw &lt;매개 변수\>**  

     선택 사항입니다. 지정한 PKCS #12 파일을 사용 하 여 연관 된 암호를 지정 된 **-UsePKICert** 속성입니다.  

     예: -UsePKICert &lt;전체 경로 및 파일 이름\> -certpw &lt;암호\>  

-   **-NoCRLCheck**  

     선택 사항입니다. 클라이언트 PKI 인증서를 사용 하 여 HTTPS를 통해 통신할 때 (CRL)의 인증서 해지 목록 확인 하지 않도록 지정 합니다. 이 옵션을 지정 하지 않으면 클라이언트 PKI 인증서를 사용 하 여 HTTPS 연결을 설정 하기 전에 CRL을 확인 합니다. 클라이언트 CRL 확인 하는 방법에 대 한 자세한 내용은 PKI 인증서 해지 계획을 참조 합니다.  

     예: -UsePKICert &lt;전체 경로 및 파일 이름\> -certpw &lt;암호\> -NoCRLCheck  

-   **-rootkeypath &lt;파일 위치\>**  

     선택 사항입니다. Configuration Manager의 신뢰할 수 있는 루트 키에 대한 전체 경로와 파일 이름을 지정합니다. Configuration Manager 신뢰할 수 있는 루트 키는 Linux 및 UNIX 클라이언트에서 올바른 계층 구조에 속하는 사이트 시스템에 연결되어 있는지 확인하는 데 사용하는 메커니즘을 제공합니다.  

     명령줄에서 신뢰할 수 있는 루트 키를 지정하지 않으면 클라이언트는 통신하는 첫 번째 관리 지점을 신뢰하고 해당 관리 지점에서 신뢰할 수 있는 루트 키를 자동으로 검색합니다.  

     자세한 내용은 [신뢰할 수 있는 루트 키 계획](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK)을 참조하세요.  

     예: -rootkeypath &lt;전체 경로 및 파일 이름\>  

-   **-httpport &lt;포트\>**  

     선택 사항입니다. 관리 지점에 HTTP를 통해 통신할 때 클라이언트가 사용 하는 관리 지점에 구성 된 포트를 지정 합니다. 포트를 지정 하지 않으면 기본값인 80이 사용 됩니다.  

     예: -httpport 80  

-   **-httpsport &lt;포트\>**  

     선택 사항입니다. 관리 지점에 HTTPS를 통해 통신할 때 클라이언트가 사용 하는 관리 지점에 구성 된 포트를 지정 합니다. 포트를 지정 하지 않으면 기본값인 443이 사용 됩니다.  

     예: -UsePKICert &lt;전체 경로 및 인증서 이름\> -httpsport 443  

-   **-ignoreSHA256validation**  

     선택 사항입니다. 클라이언트 설치 s h A-256 유효성 검사를 건너뜁니다 지정 합니다. SHA-256을 지원하는 OpenSSL 버전과 함께 릴리스되지 않은 클라이언트를 운영 체제에 설치할 때 이 옵션을 사용합니다. 자세한 내용은 [SHA-256을 지원하지 않는 Linux 및 UNIX 운영 체제 정보](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_NoSHA-256)를 참조하세요.  

-   **-signcertpath &lt;파일 위치\>**  

     선택 사항입니다. 전체 경로 지정 하 고 **.cer** 사이트 서버의 내보낸된 자체 서명 된 인증서의 파일 이름입니다. PKI 인증서를 사용할 수 없는 경우 Configuration Manager 사이트 서버에서 자체 서명된 인증서를 자동으로 생성합니다.  

     이러한 인증서는 관리 지점에서 다운로드 하는 클라이언트 정책이 의도 한 사이트에서 보낸 유효성을 검사 하는데 사용 됩니다. 설치 중에 자체 서명된 인증서를 지정하지 않았거나 인증서를 변경해야 하는 경우 **certutil** 유틸리티를 사용합니다. certutil에 대한 자세한 내용은 [Linux 및 UNIX용 클라이언트에서 인증서를 관리하는 방법](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_ManageLinuxCerts)을 참조하세요.  

     이 인증서는 **SMS** 인증서 저장소를 통해 검색할 수 있으며 주체 이름이 **사이트 서버** 이고 이름이 **사이트 서버 서명 인증서**입니다.  

     설치 하는 동안이 옵션을 지정 하지 않으면, Linux 및 UNIX 클라이언트가 해당 관리 지점에서 서명 인증서를 자동으로 검색 됩니다와 통신 하는 첫번째 관리 지점을 신뢰 합니다.  

     예: -signcertpath &lt;전체 경로 및 파일 이름\>  

-   **-rootcerts**  

     선택 사항입니다. 가져올 관리 지점 인증 기관 (CA) 계층의 일부분이 아닌 추가 PKI 인증서를 지정 합니다. 명령줄에서 여러 인증서를 지정 하면 쉼표로 구분 된 수 있어야 합니다.  

     사이트 관리 지점이 신뢰할 수 있는 루트 CA 인증서에 연결 되지 않은 PKI 클라이언트 인증서를 사용 하는 경우이 옵션을 사용 합니다. 클라이언트 인증서가 사이트의 인증서 발급자 목록에 있는 신뢰할 수 있는 루트 인증서에 연결되지 않은 경우 관리 지점에서 클라이언트를 거부합니다.  

     Linux 및 UNIX 클라이언트에 있는 인증서를 사용 하 여 신뢰 계층 구조는 확인이 옵션을 사용 하지 않는 경우는 **-UsePKICert** 옵션입니다.  

     예: -rootcerts &lt;전체 경로 및 파일 이름\>,&lt;전체 경로 및 파일 이름\>  

###  <a name="a-namebkmkuninstalllnuclienta-uninstalling-the-client-from-linux-and-unix-servers"></a><a name="BKMK_UninstallLnUClient"></a> Linux 및 UNIX 서버에서 클라이언트 제거  
 UNIX 및 Linux용 Configuration Manager 클라이언트를 제거하려면 제거 유틸리티인 **uninstall**을 사용합니다. 기본적으로이 파일의 위치는 **/opt/microsoft/configmgr/bin/** 클라이언트 컴퓨터의 폴더입니다. 제거 명령을이 모든 명령줄 매개 변수를 지원 하지 않으며 서버에서 클라이언트 소프트웨어와 관련 된 모든 파일을 제거 합니다.  

 클라이언트를 제거 하려면 다음 명령줄을 사용 하 여: **/opt/microsoft/configmgr/bin/uninstall**  

 Linux 및 UNIX용 Configuration Manager 클라이언트를 제거한 후 컴퓨터를 다시 부팅하지 않아도 됩니다.  

##  <a name="a-namebkmkconfiglnuclientcommuincationsa-configure-request-ports-for-the-client-for-linux-and-unix"></a><a name="BKMK_ConfigLnUClientCommuincations"></a> Linux 및 UNIX 용 클라이언트에 대 한 요청 포트 구성  
 Windows 기반 클라이언트와 마찬가지로 Linux 및 UNIX용 Configuration Manager 클라이언트는 HTTP 및 HTTPS를 사용하여 Configuration Manager 사이트 시스템과 통신합니다. Configuration Manager 클라이언트에서 통신에 사용하는 포트를 요청 포트라고 합니다.  

 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치할 때 **-httpport** 및 **-httpsport** 설치 속성을 지정하여 클라이언트 기본 요청 포트를 변경할 수 있습니다. 설치 속성 및 사용자 지정 값을 지정 하지 않으면 클라이언트는 기본값을 사용 합니다. 기본값은 **80** HTTP 트래픽의 및 **443** HTTPS 트래픽에 대 한 합니다.  

 클라이언트를 설치한 후 해당 요청 포트 구성을 변경할 수 없습니다. 대신, 포트 구성을 변경 하려면 클라이언트를 다시 설치 하 고 새 포트 구성을 지정 해야 합니다. 요청 포트 번호를 변경 하려면 클라이언트를 다시 설치 하면 실행은 **설치** 의 추가 명령줄 속성을 사용 하지만 새 클라이언트 설치에 유사한 명령 **-keepdb**. 이 스위치는 클라이언트 데이터베이스와 클라이언트 GUID 및 인증서 저장소를 포함 하 여 파일을 유지 하려면 설치 하도록 지시 합니다.  

 클라이언트 통신 포트 번호에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 통신 포트를 구성하는 방법](../../../core/clients/deploy/configure-client-communication-ports.md)을 참조하세요.  

##  <a name="a-namebkmkconfigclientmpa-configure-the-client-for-linux-and-unix-to-locate-management-points"></a><a name="BKMK_ConfigClientMP"></a> 관리 지점을 찾기위해 Linux 및 UNIX 용 클라이언트를 구성 합니다.  
 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치하는 경우 초기 연결 지점으로 사용할 관리 지점을 지정해야 합니다.  

 Linux 및 UNIX용 Configuration Manager 클라이언트는 클라이언트 설치 시 이 관리 지점에 연결합니다. 클라이언트가 관리 지점에 연결하지 못하면 성공할 때까지 클라이언트 소프트웨어에서 계속 다시 시도합니다.  

 클라이언트가 관리 지점을 찾는 방법에 대한 자세한 내용은 [관리 지점 찾기](../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_LocatingMPs)를 참조하세요.



<!--HONumber=Nov16_HO1-->


