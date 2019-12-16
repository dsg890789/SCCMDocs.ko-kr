---
title: Linux 및 UNIX 컴퓨터에 클라이언트 배포 계획
titleSuffix: Configuration Manager
description: Configuration Manager에서 Linux 및 UNIX 컴퓨터에 클라이언트 배포를 계획합니다.
ms.date: 03/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 44153689-70e8-42ad-9ae8-17ae35f6a2e3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: cfa2a2412744046ca1a16aad2721fcb9efcff38e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62202299"
---
# <a name="planning-for-client-deployment-to-linux-and-unix-computers-in-configuration-manager"></a>Configuration Manager에서 Linux 및 UNIX 컴퓨터에 클라이언트 배포 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Important]  
> 버전 1902부터 Configuration Manager는 Linux 또는 UNIX 클라이언트를 지원하지 않습니다. 
> 
> 따라서 Linux 서버를 관리하려면 Microsoft Azure 관리를 고려해야 합니다. Azure 솔루션은 대부분의 경우 Linux용 엔드투엔드 패치 관리를 포함하여 Configuration Manager 기능을 능가하는 광범위한 Linux 지원을 제공합니다.

Linux 또는 UNIX를 실행하는 컴퓨터에 Configuration Manager 클라이언트를 설치할 수 있습니다. 이 클라이언트는 작업 그룹 컴퓨터로 작동하는 서버를 위해 설계되었으며 로그온한 사용자와의 상호 작용은 지원하지 않습니다. 클라이언트 소프트웨어를 설치하고 클라이언트가 Configuration Manager 사이트와의 통신을 설정한 후 Configuration Manager 콘솔 및 보고서를 사용하여 클라이언트를 관리합니다.  

> [!NOTE]
>  Linux 및 UNIX 컴퓨터용 System Center Configuration Manager 클라이언트는 다음 관리 기능을 지원하지 않습니다.  
> 
> - 클라이언트 강제 설치  
>   -   운영 체제 배포  
>   -   애플리케이션 배포(대신, 패키지 및 프로그램을 사용한 소프트웨어 배포)  
>   -   소프트웨어 인벤토리  
>   -   소프트웨어 업데이트  
>   -   호환성 설정  
>   -   원격 제어  
>   -   전원 관리  
>   -   클라이언트 상태 클라이언트 검사 및 재구성  
>   -   인터넷 기반 클라이언트 관리  

 지원되는 Linux 및 UNIX 배포와, Linux 및 UNIX의 클라이언트를 지원하는 데 필요한 하드웨어에 대한 자세한 내용은 [System Center Configuration Manager에 권장되는 하드웨어](../../../../core/plan-design/configs/recommended-hardware.md)를 참조하세요.  

 이 문서의 정보를 통해 Linux 및 UNIX용 Configuration Manager 클라이언트 배포를 계획할 수 있습니다.  

##  <a name="BKMK_ClientDeployPrereqforLnU"></a> Linux 및 UNIX 서버에 클라이언트 배포에 대한 필수 조건  
 Linux 및 UNIX 용 클라이언트를 설치 하는 필수 구성 요소가 있어야 하는 위치에 성공적으로 확인 하려면 다음 정보를 사용 합니다.  

###  <a name="BKMK_ClientDeployExternalforLnU"></a> Configuration Manager 외부 종속성:  
 다음 표에서는 필수 UNIX 및 Linux 운영 체제 및 패키지 종속 파일을 설명합니다.  

 **Red Hat Enterprise Linux Server 릴리스 5.1(Tikanga)**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|glibc|C 표준 라이브러리|2.5-12|  
|Openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|0.9.8b-8.3.el5|  
|PAM|플러그 가능 인증 모듈|0.99.6.2-3.14.el5|  

 **Red Hat Enterprise Linux Server 릴리스 6**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|glibc|C 표준 라이브러리|2.12-1.7|  
|Openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|1.0.0-4|  
|PAM|플러그 가능 인증 모듈|1.1.1-4|  

 **Red Hat Enterprise Linux Server 릴리스 7**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|glibc|C 표준 라이브러리|2.17|  
|Openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|1.0.1|  
|PAM|플러그 가능 인증 모듈|1.1.1-4|  

 **Solaris 10 SPARC**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|필수 운영 체제 패치|PAM 메모리 손실|117463-05|  
|SUNWlibC|Sun Workshop Compilers Bundled libC(sparc)|5.10, REV=2004.12.22|  
|SUNWlibms|Math & Microtasking Libraries(Usr)(sparc)|5.10, REV=2004.11.23|  
|SUNWlibmsr|Math & Microtasking Libraries(Root)(sparc)|5.10, REV=2004.11.23|  
|SUNWcslr|Core Solaris Libraries(Root)(sparc)|11.10.0, REV=2005.01.21.15.53|  
|SUNWcsl|Core Solaris Libraries(Root)(sparc)|11.10.0, REV=2005.01.21.15.53|  
|Openssl|SUNopenssl-librararies(Usr)<br /><br /> Sun은 Solaris 10 SPARC용 OpenSSL 라이브러리를 제공합니다. 이러한 라이브러리는 운영 체제와 함께 제공됩니다.|11.10.0,REV=2005.01.21.15.53|  
|PAM|플러그 가능 인증 모듈<br /><br /> SUNWcsr, Core Solaris, (Root)(sparc)|11.10.0, REV=2005.01.21.15.53|  

 **Solaris 10 x86**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|필수 운영 체제 패치|PAM 메모리 손실|117464-04|  
|SUNWlibC|Sun 워크샵 컴파일러 번들로 libC (i386)|5.10,REV=2004.12.20|  
|SUNWlibmsr|Math & Microtasking 라이브러리(루트)(i386)|5.10, REV=2004.12.18|  
|SUNWcsl|Core Solaris (공유 Libs) (i386)|11.10.0,REV=2005.01.21.16.34|  
|SUNWcslr|Core Solaris 라이브러리 (루트) (i386)|11.10.0, REV=2005.01.21.16.34|  
|Openssl|SUNWopenssl 라이브러리입니다. OpenSSL 라이브러리 (사용자) (i386)|11.10.0, REV=2005.01.21.16.34|  
|PAM|플러그 가능 인증 모듈<br /><br /> SUNWcsr Core Solaris (Root)(i386)|11.10.0,REV=2005.01.21.16.34|  

 **Solaris 11 SPARC**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|SUNWlibC|Sun Workshop Compilers Bundled libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Math & Microtasking 라이브러리(루트)|5.11, REV=2011.04.11|  
|SUNWcslr|코어 Solaris 라이브러리(루트)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris(공유 라이브러리)|11.11, REV=2009.11.11|  
|SUNWcsr|코어 Solaris(루트)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL 라이브러리(사용자)|11.11.0,REV=2010.05.25.01.00|  

 **Solaris 11 x86**  

|필수 패키지|설명|최소 버전|  
|----------------|-----------|---------------|  
|SUNWlibC|Sun Workshop Compilers Bundled libC|5.11, REV=2011.04.11|  
|SUNWlibmsr|Math & Microtasking 라이브러리(루트)|5.11, REV=2011.04.11|  
|SUNWcslr|코어 Solaris 라이브러리(루트)|11.11, REV=2009.11.11|  
|SUNWcsl|Core Solaris(공유 라이브러리)|11.11, REV=2009.11.11|  
|SUNWcsr|코어 Solaris(루트)|11.11, REV=2009.11.11|  
|SUNWopenssl-libraries|OpenSSL 라이브러리(사용자)|11.11.0,REV=2010.05.25.01.00|  


 **SUSE Linux Enterprise Server 10 SP1(i586)**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|glibc-2.4-31.30|C 표준 공유 라이브러리|2.4-31.30|  
|Openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|0.9.8a-18.15|  
|PAM|플러그 가능 인증 모듈|0.99.6.3-28.8|  

 **SUSE Linux Enterprise Server 11(i586)**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|glibc-2.9-13.2|C 표준 공유 라이브러리|2.9-13.2|  
|PAM|플러그 가능 인증 모듈|pam-1.0.2-20.1|  

 **범용 Linux(Debian 패키지) Debian, Ubuntu Server**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|libc6|C 표준 공유 라이브러리|2.3.6|  
|Openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|0.9.8 또는 1.0|  
|PAM|플러그 가능 인증 모듈|0.79-3|  

 **범용 Linux(RPM 패키지) CentOS, Oracle Linux**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|glibc|C 표준 공유 라이브러리|2.5-12|  
|Openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|0.9.8 또는 1.0|  
|PAM|플러그 가능 인증 모듈|0.99.6.2-3.14|  


 **IBM AIX 6.1**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|OS 버전|운영 체제 버전|AIX 6.1: 모든 Technology Level 및 서비스 팩|  
|xlC.rte|XL C/C++ 런타임|9.0.0.5|  
|OpenSSL/openssl.base|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|0.9.8.4|  

 **IBM AIX 7.1(Power)**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|OS 버전|운영 체제 버전|AIX 7.1: 모든 Technology Level 및 서비스 팩|  
|xlC.rte|XL C/C++ 런타임||  
|OpenSSL/openssl.base|OpenSSL Libraries, 보안 네트워크 통신 프로토콜||  


 **HP-UX 11i v3 IA64**  

|필수 패키지|설명|최소 버전|  
|----------------------|-----------------|---------------------|  
|HPUX11i-OE|HP-UX 기본 운영 환경|B.11.31.0709|  
|OS-Core.MinimumRuntime.CORE-SHLIBS|특정 IA 개발 라이브러리|B.11.31|  
|SysMgmtMin|최소 소프트웨어 개발 도구|B.11.31.0709|  
|SysMgmtMin.openssl|OpenSSL Libraries, 보안 네트워크 통신 프로토콜|A.00.09.08d.002|  
|PAM|플러그 가능 인증 모듈|HP-UX에서 PAM은 핵심 운영 체제 구성 요소의 일부입니다. 다른 종속 파일은 없습니다.|  

 **Configuration Manager 종속성:** 다음 테이블에는 Linux 및 UNIX 클라이언트를 지 원하는 사이트 시스템 역할이 나열됩니다. 이러한 사이트 시스템 역할에 대한 자세한 내용은 [System Center Configuration Manager 클라이언트에 대한 사이트 시스템 역할 결정](../../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md)을 참조하세요.  

|Configuration Manager 사이트 시스템|추가 정보|  
|---------------------------------------|----------------------|  
|관리 지점|Linux 및 UNIX용 Configuration Manager 클라이언트를 설치하는 데 관리 지점이 필요하지는 않지만, 클라이언트 컴퓨터와 Configuration Manager 서버 간에 정보를 전송하려면 관리 지점이 있어야 합니다. 관리 지점이 없으면 클라이언트 컴퓨터를 관리할 수 없습니다.|  
|배포 지점|배포 지점은 Linux 및 UNIX용 Configuration Manager 클라이언트 설치에 필요하지 않습니다. 그러나 사이트 시스템 역할은 Linux 및 UNIX 서버에 소프트웨어를 배포 하는 경우 필요 합니다.<br /><br /> Linux 및 UNIX용 Configuration Manager 클라이언트는 SMB를 사용하는 통신을 지원하지 않으므로 클라이언트와 함께 사용하는 배포 지점에서 HTTP 또는 HTTPS 통신을 지원해야 합니다.|  
|대체 상태 지점|Linux 및 UNIX용 Configuration Manager 클라이언트를 설치하기 위해 대체 상태 지점은 필요하지 않습니다. 그러나 대체 상태 지점을 사용하면 Configuration Manager 사이트의 컴퓨터에서 관리 지점과 통신할 수 없는 경우에 대체 상태 지점을 통해 상태 메시지를 보낼 수 있습니다. 또한 클라이언트는 대체 상태 지점에 해당 설치 상태를 보낼 수 있습니다.|  

 **방화벽 요구 사항**: 방화벽에서 클라이언트 요청 포트를 지정하는 포트를 통한 통신을 차단하지 않아야 합니다. Linux 및 UNIX용 클라이언트는 관리 지점, 배포 지점 및 대체 상태 지점과 직접 통신합니다.  

 클라이언트 통신 및 요청 포트에 대한 자세한 내용은 [관리 지점을 찾도록 Linux 및 UNIX용 클라이언트 구성](../../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigClientMP)을 참조하세요.  

##  <a name="BKMK_PlanningforCommunicationsforLnU"></a> Linux 및 UNIX 서버에 대한 포리스트 트러스트 간 통신 계획  
 Configuration Manager를 사용하여 관리하는 Linux 및 UNIX 서버는 작업 그룹 클라이언트로 작동하며 작업 그룹에 속한 Windows 기반 클라이언트와 유사한 구성이 필요합니다. 작업 그룹에 속한 컴퓨터의 통신에 대한 자세한 내용은 [Active Directory 포리스트 간 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints#Plan_Com_X-Forest)을 참조하세요.  

###  <a name="BKMK_ServiceLocationforLnU"></a> Linux 및 UNIX용 클라이언트에서 서비스 위치  
 클라이언트에 서비스를 제공 하는 사이트 시스템 서버를 찾는 작업은 서비스 위치 라고 합니다. Windows 기반 클라이언트와 달리 Linux 및 UNIX용 클라이언트는 서비스 위치에 Active Directory를 사용하지 않습니다. 또한 Linux 및 UNIX용 Configuration Manager 클라이언트는 관리 지점의 도메인 접미사를 지정하는 클라이언트 속성을 지원하지 않습니다. 대신, 클라이언트는 클라이언트 소프트웨어를 설치할 때 할당 된 알려진된 관리 지점에서 클라이언트에 서비스를 제공 하는 추가 사이트 시스템 서버에 대 한 알아냅니다.  

 자세한 내용은 [서비스 위치 및 클라이언트에서 자신의 할당된 관리 지점을 확인하는 방법](/sccm/core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services#BKMK_Plan_Service_Location)을 참조하세요.  

##  <a name="BKMK_SecurityforLnU"></a> Linux 및 UNIX 서버에 대한 보안 및 인증서 계획  
 Configuration Manager 사이트와의 안전하고 인증된 통신을 위해 Linux 및 UNIX용 Configuration Manager 클라이언트는 Windows용 Configuration Manager 클라이언트와 동일한 통신 모델을 사용합니다.  

 Linux 및 UNIX 클라이언트를 설치할 때 HTTPS를 사용하여 Configuration Manager 사이트와 통신할 수 있게 하는 PKI 인증서를 클라이언트에 할당할 수 있습니다. PKI 인증서를 할당하지 않은 경우 클라이언트는 자체 서명된 인증서를 만들고 HTTP를 통해서만 통신합니다.  

 PKI 인증서를 설치할 때 제공 하는 클라이언트 관리 지점과 통신을 HTTPS를 사용 합니다. 클라이언트를 지 원하는 HTTPS 관리 지점을 찾을 수 없을 때 제공 된 PKI 인증서와 함께 HTTP를 사용 하 여 다시 대체 됩니다.  

 Linux 또는 UNIX 클라이언트가 PKI 인증서를 사용하는 경우에는 승인할 필요가 없습니다. 클라이언트가 자체 서명된 인증서를 사용하는 경우 Configuration Manager 콘솔에서 클라이언트 승인에 대한 계층 구조 설정을 검토합니다. 클라이언트 승인 메서드가 없으면 **(권장 하지 않음) 하는 모든 컴퓨터를 자동으로 승인**, 클라이언트를 수동으로 승인 해야 합니다.  

 클라이언트를 수동으로 승인하는 방법에 대한 자세한 내용은 [디바이스 노드에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode)를 참조하세요.  

 Configuration Manager에서 인증서를 사용하는 방법에 대한 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

###  <a name="BKMK_AboutCertsforLnU"></a> Linux 및 UNIX 서버에서 사용할 인증서 정보  
 Linux 및 UNIX용 Configuration Manager 클라이언트는 Windows 기반 클라이언트와 마찬가지로 자체 서명된 인증서 또는 X.509 PKI 인증서를 사용합니다. Linux 및 UNIX 클라이언트를 관리하는 경우에도 Configuration Manager 사이트 시스템에 대한 PKI 요구 사항은 변경되지 않습니다.  

 Configuration Manager 사이트 시스템과 통신하는 Linux 및 UNIX 클라이언트에 사용할 인증서는 PKCS(Public Key Certificate Standard) #12 형식이어야 하며 PKI 인증서를 지정할 때 클라이언트에 지정할 수 있도록 암호를 알고 있어야 합니다.  

 Linux 및 UNIX용 Configuration Manager 클라이언트는 단일 PKI 인증서를 지원하며 여러 인증서를 지원하지 않습니다. 따라서 Configuration Manager 사이트에 대해 구성하는 인증서 선택 조건은 적용되지 않습니다.  

###  <a name="BKMK_ConfigCertsforLnU"></a> Linux 및 UNIX 서버에 대한 인증서 구성  
 HTTPS 통신을 사용하도록 Linux 및 UNIX 서버용 Configuration Manager 클라이언트를 구성하려면 클라이언트를 설치할 때 PKI 인증서를 사용하도록 클라이언트를 구성해야 합니다. 클라이언트 소프트웨어를 설치하기 전에는 인증서를 프로비저닝할 수 없습니다.  

 PKI 인증서를 사용하는 클라이언트를 설치할 때 명령줄 매개 변수 `-UsePKICert`를 사용하여 PKI 인증서가 포함된 PKCS#12 파일의 이름과 위치를 지정합니다. 또한 명령줄 매개 변수 `-certpw`를 사용하여 인증서 암호를 지정해야 합니다.  

 `-UsePKICert`를 지정하지 않으면 클라이언트가 자체 서명된 인증서를 생성하고 HTTP만 사용하여 사이트 시스템 서버에 통신을 시도합니다.  

##  <a name="BKMK_NoSHA-256"></a> SHA-256을 지원하지 않는 버전  
 Configuration Manager용 클라이언트로 지원되는 다음 Linux 및 UNIX 운영 체제는 SHA-256을 지원하지 않는 OpenSSL 버전과 함께 릴리스되었습니다.  

-   Solaris 버전 10(SPARC/x86)  


 Configuration Manager를 사용하여 이러한 운영 체제를 관리하려면 클라이언트에 SHA-256의 유효성 검사를 건너뛰도록 지시하는 명령줄 스위치로 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치해야 합니다. 이러한 운영 체제 버전에서 실행되는 Configuration Manager 클라이언트는 SHA-256을 지원하는 클라이언트보다 덜 안전한 모드로 작동합니다. 다음 동작을 포함 하는 작업의 보안성이 모드:  

-   클라이언트는 관리 지점에서 요청할 정책과 연결된 사이트 서버 서명의 유효성을 검사하지 않습니다.  

-   클라이언트는 배포 지점에서 다운로드하는 패키지에 대해 해시의 유효성을 검사하지 않습니다.  

> [!IMPORTANT]  
>  `ignoreSHA256validation` 옵션을 사용하면 보안 수준이 낮은 모드에서 Linux 및 UNIX 컴퓨터용 클라이언트를 실행할 수 있습니다. 이 s h A 256에 대 한 지원을 포함 하지 않는 오래 된 플랫폼에서 사용이 됩니다. 이 보안 재정의 및 Microsoft에서 권장 되지 않습니다 이지만 안전 하 고 신뢰할 수 있는 데이터 센터 환경에서 사용 하기 위해 지원 됩니다.  

 Linux 및 UNIX용 Configuration Manager 클라이언트를 설치할 때 설치 스크립트는 운영 체제 버전을 확인합니다. 기본적으로 운영 체제 버전이 SHA-256을 지원하는 OpenSSL 버전 없이 릴리스된 것으로 식별되면 Configuration Manager 클라이언트 설치에 실패합니다.  

 SHA-256을 지원하는 OpenSSL 버전과 함께 릴리스되지 않은 Linux 및 UNIX 운영 체제에 Configuration Manager 클라이언트를 설치하려면 설치 명령줄 스위치 `ignoreSHA256validation`을 사용해야 합니다. 적용 가능한 Linux 또는 UNIX 운영 체제에서 이 명령줄 옵션을 사용하면 Configuration Manager 클라이언트는 SHA-256 유효성 검사를 건너뛰며, 설치 후에 클라이언트에서 SHA-256을 사용하여 HTTP를 통해 사이트 시스템으로 전송하는 데이터에 서명하지 않습니다. 인증서를 사용하도록 Linux 및 UNIX 클라이언트를 구성하는 방법에 대한 자세한 내용은 [Linux 및 UNIX 서버에 대한 보안 및 인증서 계획](#BKMK_SecurityforLnU)을 참조하세요. SHA-256을 요구하는 방법에 대한 자세한 내용은 [서명 및 암호화 구성](/sccm/core/plan-design/security/configure-security#BKMK_ConfigureSigningEncryption)을 참조하세요.  

> [!NOTE]  
>  SHA-256을 지원하는 OpenSSL 버전과 함께 릴리스된 Linux 및 UNIX 버전을 실행하는 컴퓨터에서는 명령줄 옵션 `ignoreSHA256validation`이 무시됩니다.  
