---
title: "지원되는 클라이언트 및 장치 | Microsoft 문서"
description: "System Center Configuration Manager에서 클라이언트 및 장치에 대해 지원하는 운영 체제를 알아봅니다."
ms.custom: na
ms.date: 8/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: "5"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: f9dd3b3e8f7a2878cd549bf289e1ee5536ee73fc
ms.sourcegitcommit: 974fbc4408028c8be28911e5cd646efcf47c7f15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>System Center Configuration Manager의 클라이언트 및 장치에 대해 지원되는 운영 체제

*적용 대상: System Center Configuration Manager(현재 분기)*


 System Center Configuration Manager에서는 다양한 Windows, Mac, Linux 및 UNIX 컴퓨터에 클라이언트 소프트웨어를 설치할 수 있습니다.  

 **모든 클라이언트에 대한 요구 사항 및 제한 사항:**  

-   Configuration Manager 서비스의 시작 유형 또는 **Log on as**(다음 계정으로 로그온) 설정 변경은 지원되지 않으며, 키 서비스가 제대로 실행되지 않을 수 있습니다.    

-   root 이외의 계정으로 실행하는 컴퓨터에서는 Linux/UNIX용 Configuration Manager 클라이언트나 Mac용 클라이언트를 설치 또는 실행은 지원되지 않습니다. 이러한 설정을 변경하면 주요 서비스가 정상적으로 실행되지 않을 수 있습니다.  

##  <a name="windows-computers"></a>Windows 컴퓨터  
 Configuration Manager에 포함된 Configuration Manager 클라이언트를 사용하여 다음 Windows 운영 체제를 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md)을 참조하세요.  

**지원되는 운영 체제:**  


-  **Windows Server 2016**: Standard, Datacenter <sup>1</sup>
  - 이 운영 체제는 Configuration Manager 버전 1606 및 KB3186654의 핫픽스 롤업(또는 2016년 10월에 릴리스된 1606의 기준 버전)부터 지원됩니다.  

-   **Windows Server 2012 R2**(x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012 R2**(x64)    

-   **Windows Server 2012**(x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012**(x64)    

-   **Windows Server 2008 R2 SP1**(x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2008 R2**(x86, x64): Workgroup, Standard, Enterprise    

-   **Windows Server 2008 SP2**(x86, x64): Standard, Enterprise, Datacenter <sup>1</sup>    

-   **Windows 10**: 여러 버전의 Configuration Manager에서 지원되는 Windows 10의 다양한 릴리스 버전에 대한 자세한 내용은 [Windows 10 버전에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)을 참조하세요.

-   **Windows 8.1**(x86, x64): Professional, Enterprise    

-   **Windows 8**(x86, x64): Professional, Enterprise    

-   **Windows 7 SP1**(x86, x64): Professional, Enterprise, Ultimate    

-   **Windows Server 2016의 Server Core 설치**(x64) <sup>2</sup>
  - 이 운영 체제는 KB3186654의 핫픽스 롤업이 포함된 1606 버전(또는 2016년 10월에 릴리스된 1606의 기준 버전)부터 지원됩니다.


-   **Windows Server 2012 R2의 Server Core 설치**(x64) <sup>2</sup>    

-   **Windows Server 2012의 Server Core 설치**(x64) <sup>2</sup>    

-   **Windows Server 2008 R2의 Server Core 설치**  
    **(서비스 팩 없음 또는 SP1)**(x64)    

-   **Windows Server 2008 SP2의 Server Core 설치**(x86, x64)  

 <sup>1</sup> Datacenter 릴리스는 Configuration Manager용으로 지원되지만 인증되지는 않았습니다. Windows Server Datacenter Edition 관련 문제에 대한 핫픽스 지원은 제공되지 않습니다.  

 <sup>2</sup> 클라이언트 강제 설치를 지원하려면 이 운영 체제 버전을 실행하는 컴퓨터에서 파일 및 저장소 서비스 서버 역할용으로 파일 서버 역할 서비스를 실행해야 합니다. Server Core 컴퓨터에 Windows 기능을 설치하는 방법에 대한 자세한 내용은 Windows Server 2012 TechNet 라이브러리에서 [Server Core 서버에 서버 역할 및 기능 설치](http://go.microsoft.com/fwlink/p/?LinkId=299359)를 참조하세요.  


##  <a name="windows-embedded-computers"></a>Windows Embedded 컴퓨터  
 장치에 Configuration Manager 클라이언트 소프트웨어를 설치하여 Windows Embedded 장치를 관리할 수 있습니다.  자세한 내용은 [System Center Configuration Manager에서 Windows Embedded 장치에 클라이언트 배포 계획](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md)을 참조하세요.  

**요구 사항 및 제한 사항:**  

-   쓰기 필터를 사용하도록 설정하지 않은 Windows Embedded 시스템에서는 모든 클라이언트 기능이 지원됩니다.  

-   다음 중 하나를 사용하는 클라이언트는 전원 관리를 제외한 모든 기능에 대해 지원됩니다.  

    -   강화된 쓰기 필터(EWF)    

    -   RAM FBWF(파일 기반 쓰기 필터)    

    -   통합 쓰기 필터(UWF)  

-   Windows Embedded 장치에는 응용 프로그램 카탈로그가 지원되지 않습니다.  

-   Windows XP를 기반으로 하는 Windows Embedded 장치에서 검색된 맬웨어를 모니터링하려면 장치에 Microsoft Windows WMI 스크립팅 패키지를 설치해야 합니다. 이 패키지를 설치하려면 Windows Embedded Target Designer를 사용합니다.
이 경우 **WBEMDISP.DLL** 및 **WBEMDISP.TLB** 파일이 있고 임베디드 장치의 **%windir%\System32\WBEM** 폴더에 등록되어 있어야 검색된 맬웨어가 보고됩니다.  

**지원되는 운영 체제:**  

-   **Windows 10 Enterprise**(x86, x64)  

-   **Windows 10 IoT Enterprise**(x86, x64)  

-   **Windows Embedded 8.1 Industry**(x86, x64)    

-   **Windows Embedded 8 Industry**(x86, x64)    

-   **Windows Embedded 8 Standard**(x86, x64)    

-   **Windows Embedded 8 Pro**(x86, x64)    

-   **Windows Thin PC**(x86, x64)    

-   **Windows Embedded POSReady 7**(x86, x64)    

-   **Windows Embedded Standard 7 SP1**(x86, x64)    

다음 운영 체제는 Windows XP Embedded에 기반하고 Configuration Manager 버전 1610 이전에서만 지원됩니다. [1702 버전부터 이러한 포함 운영 체제는 더 이상 지원되지 않습니다](/sccm/core/plan-design/changes/removed-and-deprecated-features#client-operating-systems).  

-   **WEPOS 1.1 SP3**(x86)    

-   **Windows Embedded POSReady 2009**(x86)    

-   **Windows Fundamentals for Legacy PCs(WinFLP)**(x86)    

-   **Windows XP Embedded SP3**(x86)    

-   **Windows Embedded Standard 2009**(x86)  

## <a name="windows-ce-computers"></a>Windows CE 컴퓨터
 Configuration Manager와 함께 제공되는 Configuration Manager 모바일 장치 레거시 클라이언트에서 Windows CE 장치를 관리할 수 있습니다.  

**요구 사항 및 제한 사항**  

-   모바일 장치 클라이언트를 설치하려면 0.78MB의 저장소 공간이 필요합니다. 로그인은 256KB의 추가 저장소 공간이 필요할 수 있습니다.    

-   이러한 모바일 장치의 기능은 플랫폼 및 클라이언트 유형별로 달라집니다. 지원하는 관리 기능에 대한 자세한 내용은 [System Center Configuration Manager용 장치 관리 솔루션 선택](../../../core/plan-design/choose-a-device-management-solution.md)을 참조하세요.  

**지원되는 운영 체제:**  

-   Windows CE 7.0(ARM 및 x86 프로세서)  

**지원되는 언어:**  

-   중국어(간체 및 번체)    

-   영어(미국)    

-   프랑스어(프랑스)    

-   독일어    

-   이탈리아어    

-   일본어  

-   한국어  

-   포르투갈어(브라질)  

-   러시아어  

-   스페인어(스페인)  

## <a name="mac-computers"></a>Mac 컴퓨터  
 Mac용 Configuration Manager 클라이언트에서 Mac OS X 컴퓨터를 관리할 수 있습니다.  

 Mac 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 **추가 운영 체제용 클라이언트**를 다운로드합니다.  

 자세한 내용은 [System Center Configuration Manager에서 Mac에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-macs.md)을 참조하세요.  

**지원되는 버전:**  

-   **Mac OS X 10.6**(Snow Leopard)

-   **Mac OS X 10.7**(Lion)

-   **Mac OS X 10.8**(Mountain Lion)

-   **Mac OS X 10.9**(Mavericks)

-   **Mac OS X 10.10**(Yosemite)  

-   **Mac OS X 10.11**(El Capitan)  

-   **Mac OS X 10.12**(macOS Sierra )

##  <a name="linux-and-unix-servers"></a>Linux 및 UNIX 서버  
 Linux 및 UNIX용 Configuration Manager 클라이언트에서 Linux 및 UNIX 서버를 관리할 수 있습니다.  

 Linux 및 UNIX 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 **추가 운영 체제용 클라이언트**를 다운로드합니다. 클라이언트 설치 패키지 외에도 클라이언트 다운로드에는 각 컴퓨터의 클라이언트 설치를 관리하는 스크립트가 들어 있습니다.  

**요구 사항 및 제한 사항:**  

-   Linux 및 UNIX용 클라이언트에 대한 운영 체제 파일 종속성을 검토하려면 [Linux 및 UNIX 서버에 클라이언트 배포를 위한 필수 조건](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU)을 참조하세요.  

-   Linux 또는 UNIX에 대해 지원되는 관리 기능의 개요는 [System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)을 참조하세요.  

-   Linux 및 UNIX에 대해 지원되는 버전의 경우 나열된 버전에는 모든 후속 부 버전이 포함됩니다. 예를 들어 CentOS 버전 6에는 CentOS 6.3이 포함됩니다. 마찬가지로 SUSE Linux Enterprise Server 11 SP1과 같이 서비스 팩을 사용하는 운영 체제에 대한 지원에는 해당 운영 체제 버전의 후속 서비스 팩이 포함됩니다.  

-   클라이언트 설치 패키지 및 유니버설 에이전트에 대한 자세한 내용은 [System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md)을 참조하세요.  

**지원되는 버전:** 다음 버전은 표시된 .tar 파일을 사용하여 지원됩니다.  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|버전 5.3(Power)|ccm-Aix53ppc.&lt;빌드\>.tar|  
|버전 6.1(Power)|ccm-Aix61ppc.&lt;빌드\>.tar|  
|버전 7.1(Power)|ccm-Aix71ppc.&lt;빌드\>.tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="debian"></a>Debian  

|||  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x 86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 8 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 8 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="hp-ux"></a>HP-UX  

|||  
|-|-|  
|버전 11iv2 IA64|ccm-HpuxB.11.23i64.&lt;빌드\>.tar|  
|버전 11iv2 PA-RISC|ccm-HpuxB.11.23PA.&lt;빌드\>.tar|  
|버전 11iv3 IA64|ccm-HpuxB.11.31i64.&lt;빌드\>.tar|  
|버전 11iv3 PA-RISC|ccm-HpuxB.11.31PA.&lt;빌드\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|버전 4 x86|ccm-RHEL4x86.&lt;빌드\>.tar|  
|버전 4 x64|ccm-RHEL4x64.&lt;빌드\>.tar|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|버전 9 SPARC|ccm-Sol9sparc.&lt;빌드\>.tar|  
|버전 10 x86|ccm-Sol10x86.&lt;빌드\>.tar|  
|버전 10 SPARC|ccm-Sol10sparc.&lt;빌드\>.tar|  
|버전 11 x86|ccm-Sol11x86.&lt;빌드\>.tar|  
|버전 11 SPARC|ccm-Sol11sparc.&lt;빌드\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|||  
|-|-|  
|버전 9 x86|ccm-SLES9x86.&lt;빌드\>.tar|  
|버전 10 SP1 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 10 SP1 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 11 SP1 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 11 SP1 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 12 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|버전 10.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 10.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 12.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 12.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 14.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 14.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  

##  <a name="mobile-devices-enrolled-by-microsoft-intune"></a>Microsoft Intune에서 등록한 모바일 장치  
 Configuration Manager에 Microsoft Intune을 통합할 때 관리할 수 있는 컴퓨터 및 장치에 대한 자세한 내용은 Microsoft Intune 문서 라이브러리에서 다음 두 항목을 참조하세요.  

-   [Microsoft Intune의 모바일 장치 관리 기능](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [Microsoft Intune의 Windows PC 관리 기능](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="bkmk_OnpremOS"></a> 온-프레미스 모바일 장치 관리  
 Configuration Manager에는 클라이언트 소프트웨어를 설치하지 않고 온-프레미스의 장치를 관리할 수 있는 기본 제공 기능이 있습니다.  자세한 내용은 [System Center Configuration Manager의 온-프레미스 인프라로 모바일 장치 관리](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md)를 참조하세요.  

 **요구 사항 및 제한 사항:**  

-   계층 구조의 최상위 계층 사이트에서 **서비스 연결 지점**을 구성해야 합니다.  

**지원되는 운영 체제:**  

- **Windows 10 Pro**(x86, x64)  

- **Windows 10 Pro Enterprise**(x86, x64)  

- **Windows 10 IoT Enterprise**(x86, x64)

- **Windows 10 Mobile**  

- **Windows 10 Mobile Enterprise**  

- **Windows 10 IoT Mobile Enterprise**

- **Windows 10 Team for Surface Hub**

##  <a name="bkmk_ExSrvConOS"></a> Exchange Server 커넥터  
Configuration Manager에서는 Configuration Manager 클라이언트를 설치하지 않고 Exchange Server에 연결하는 장치에 대한 제한적인 관리를 지원합니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)를 참조하세요.  

 **요구 사항 및 제한 사항:**  

-   Configuration Manager에서는 Exchange Server 또는 Exchange Online을 실행 중인 서버에 연결하는 Exchange Active Sync에 대해 Exchange Server 커넥터를 사용하는 장치를 사용하는 경우 모바일 장치용으로 제한적인 관리 기능을 제공합니다.  

-   Exchange Server 커넥터가 관리하는 모바일 장치에 대해 Configuration Manager가 지원하는 관리 기능에 대한 자세한 내용은 Configuration Manager에서 모바일 장치를 관리하는 방법 결정 항목을 참조하세요.  

**Exchange Server의 지원되는 버전:**  

-   **Exchange Server 2010 SP1**  

-   **Exchange Server 2010 SP2**  

-   **Exchange Server 2013**  

-   **Exchange Online(Office 365)**: 여기에는 Business Productivity Online Standard Suite가 포함됨  
