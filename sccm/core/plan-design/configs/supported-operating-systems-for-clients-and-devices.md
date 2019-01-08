---
title: 지원되는 클라이언트 및 디바이스
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라이언트 및 디바이스에 대해 지원하는 OS 버전을 알아봅니다.
ms.date: 10/02/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6f60d7f3a8c3bd81f4de38b2ce4080f54756de14
ms.sourcegitcommit: c60e057075a83f07d1ca2577c3de1c7d7c8e9cec
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626466"
---
# <a name="supported-os-versions-for-clients-and-devices-for-configuration-manager"></a>Configuration Manager의 클라이언트 및 디바이스에 대해 지원되는 OS 버전

*적용 대상: System Center Configuration Manager(현재 분기)*

 Configuration Manager에서는 Windows, Mac, Linux 및 UNIX 컴퓨터에 클라이언트 소프트웨어를 설치할 수 있습니다.  

#### <a name="requirements-and-limitations-for-all-clients"></a>모든 클라이언트에 대한 요구 사항 및 제한 사항  

-   모든 Configuration Manager 서비스의 시작 유형 또는 **다음 사용자로 로그온** 설정은 변경할 수 없습니다. 변경하면 주요 서비스가 정상적으로 실행되지 않을 수 있습니다.    

-   root 이외의 계정으로 실행하는 컴퓨터에서는 Linux/UNIX용 구성 관리자 클라이언트나 Mac용 클라이언트를 설치 또는 실행은 지원되지 않습니다. 이러한 설정을 변경하면 주요 서비스가 정상적으로 실행되지 않을 수 있습니다.  



##  <a name="windows-computers"></a>Windows 컴퓨터  

 다음 Windows OS 버전을 관리하려면 Configuration Manager에 포함된 클라이언트를 사용하세요. 자세한 내용은 [Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.  


### <a name="supported-client-os-versions"></a>지원되는 클라이언트 OS 버전

-   **Windows 10**  

    자세한 내용은 [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)을 참조하세요.  

-   **Windows 8.1**(x86, x64): Professional, Enterprise    

-   **Windows 7 SP1**(x86, x64): Professional, Enterprise 및 Ultimate    


### <a name="supported-server-os-versions"></a>지원되는 서버 OS 버전

-  **Windows Server 2019**: Standard, Datacenter <sup>[참고 1](#bkmk_note1)</sup>  
    (Configuration Manager 1806 버전부터 시작)

-  **Windows Server 2016**: Standard, Datacenter <sup>[참고 1](#bkmk_note1)</sup>  

-   **Windows Storage Server 2016**: Workgroup, Standard  

-   **Windows Server 2012 R2**(x64): Standard, Datacenter <sup>[참고 1](#bkmk_note1)</sup>    

-   **Windows Storage Server 2012 R2**(x64)    

-   **Windows Server 2012**(x64): Standard, Datacenter <sup>[참고 1](#bkmk_note1)</sup>    

-   **Windows Storage Server 2012**(x64)    

-   **Windows Server 2008 R2 SP1**(x64): Standard, Enterprise, Datacenter <sup>[참고 1](#bkmk_note1)</sup>    

-   **Windows Storage Server 2008 R2**(x86, x64): Workgroup, Standard, Enterprise    

-   **Windows Server 2008 SP2**(x86, x64): Standard, Enterprise, Datacenter <sup>[참고 1](#bkmk_note1)</sup>    


#### <a name="server-core"></a>Server Core
특히 다음 버전은 OS의 Server Core 설치를 참조하세요. <sup>[참고 3](#bkmk_note3)</sup>  

Windows Server 반기 채널 버전은 Windows Server 버전 1809 같은 Server Core 설치입니다. 구성 관리자 클라이언트로서 연결된 Windows 10 반기 채널 버전과 동일하게 지원됩니다. 자세한 내용은 [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)을 참조하세요.


-   **Windows Server 2019**(x64) <sup>[참고 2](#bkmk_note2)</sup>  

-   **Windows Server 2016**(x64) <sup>[참고 2](#bkmk_note2)</sup>   

-   **Windows Server 2012 R2**(x64) <sup>[참고 2](#bkmk_note2)</sup>     

-   **Windows Server 2012**(x64) <sup>[참고 2](#bkmk_note2)</sup>     

-   **Windows Server 2008 R2**(서비스 팩 없음, SP1(x64))     

-   **Windows Server 2008 SP2**(x86, x64)   

#### <a name="bkmk_note1"></a> 참고 1
 Configuration Manager는 Windows Server Datacenter 버전을 테스트하고 지원하지만 Windows Server에 대한 공식 인증을 받지 않았습니다. Windows Server Datacenter Edition 관련 문제에 대한 Configuration Manager 핫픽스 지원은 제공되지 않습니다. Windows Server 인증 프로그램에 대한 자세한 내용은 [Windows Server Catalog](https://www.windowsservercatalog.com/)(Windows Server 카탈로그)를 참조하세요. 

#### <a name="bkmk_note2"></a> 참고 2
 [클라이언트 강제 설치](/sccm/core/clients/deploy/plan/client-installation-methods#client-push-installation)를 지원하려면 파일 및 스토리지 서비스 서버 역할의 파일 서버 서비스를 추가하세요. Server Core에 Windows 기능을 설치하는 방법에 대한 자세한 내용은 [Install roles, role services, and features by using Windows PowerShell cmdlets](https://docs.microsoft.com/windows-server/administration/server-manager/install-or-uninstall-roles-role-services-or-features#BKMK_installwps)(Windows PowerShell cmdlet을 사용하여 역할, 역할 서비스 및 기능 설치)를 참조하세요.  

#### <a name="bkmk_note3"></a> 참고 3
 새 소프트웨어 센터 앱은 모든 Windows Server Core 버전에서 지원되지 않습니다.<!--SCCMDocs issue 683-->



##  <a name="windows-embedded-computers"></a>Windows Embedded 컴퓨터  

 디바이스에 Configuration Manager 클라이언트를 설치하여 Windows Embedded 디바이스를 관리할 수 있습니다. 자세한 내용은 [Windows Embedded 디바이스에 클라이언트 배포 계획](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices)을 참조하세요.  


### <a name="requirements-and-limitations"></a>요구 사항 및 제한 사항:

-   쓰기 필터를 사용하도록 설정하지 않은 Windows Embedded 시스템에서는 모든 클라이언트 기능이 지원됩니다.  

-   다음 중 하나를 사용하는 클라이언트는 전원 관리를 제외한 모든 기능에 대해 지원됩니다.  

    -   강화된 쓰기 필터(EWF)    

    -   RAM FBWF(파일 기반 쓰기 필터)    

    -   통합 쓰기 필터(UWF)  

-   Windows Embedded 장치에는 애플리케이션 카탈로그가 지원되지 않습니다.  


### <a name="supported-os-versions"></a>지원된 OS 버전  

-   **Windows 10 Enterprise**(x86, x64)  

-   **Windows 10 IoT Enterprise**(x86, x64)  
    이 버전에는 LTSC(장기 서비스 채널)가 포함됩니다. 자세한 내용은 [Overview of Windows 10 IoT Enterprise](https://docs.microsoft.com/windows/iot-core/windows-iot-enterprise)\(Windows 10 IoT Enterprise 개요\)를 참조하세요.<!--SCCMDocs issue 560-->  

-   **Windows Embedded 8.1 Industry**(x86, x64)    

-   **Windows Embedded 8 Standard**(x86, x64)    

-   **Windows Thin PC**(x86, x64)    

-   **Windows Embedded POSReady 7**(x86, x64)    

-   **Windows Embedded Standard 7 SP1**(x86, x64)    



## <a name="windows-ce-computers"></a>Windows CE 컴퓨터

 Configuration Manager와 함께 제공되는 Configuration Manager 모바일 디바이스 레거시 클라이언트에서 Windows CE 디바이스를 관리할 수 있습니다.  


### <a name="requirements-and-limitations"></a>요구 사항 및 제한 사항:  

-   모바일 디바이스 클라이언트를 설치하려면 0.78MB의 저장소 공간이 필요합니다. 로그인은 256KB의 추가 저장소 공간이 필요할 수 있습니다.    

-   이러한 모바일 디바이스의 기능은 플랫폼 및 클라이언트 유형별로 달라집니다. 지원되는 관리 기능에 대한 자세한 내용은 [디바이스 관리 솔루션 선택](/sccm/core/plan-design/choose-a-device-management-solution)을 참조하세요.  


### <a name="supported-os-versions"></a>지원된 OS 버전  

-   Windows CE 7.0(ARM 및 x86 프로세서)  

#### <a name="supported-languages-include"></a>지원되는 언어

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

 Mac용 구성 관리자 클라이언트에서 macOS 컴퓨터를 관리하세요.  

 Mac 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 **추가 운영 체제용 클라이언트**를 다운로드합니다.  

 자세한 내용은 [How to deploy clients to Macs](/sccm/core/clients/deploy/deploy-clients-to-macs)(Mac에 클라이언트를 배포하는 방법)를 참조하세요.  


### <a name="supported-versions"></a>지원되는 버전

-   **Mac OS X 10.6**(Snow Leopard)

-   **Mac OS X 10.7**(Lion)

-   **Mac OS X 10.8**(Mountain Lion)

-   **Mac OS X 10.9**(Mavericks)

-   **Mac OS X 10.10**(Yosemite)  

-   **Mac OS X 10.11**(El Capitan)  

-   **Mac OS X 10.12**(macOS Sierra)

-   **Mac OS X 10.13**(macOS High Sierra)

- **macOS Mojave(10.14)** 


##  <a name="linux-and-unix-servers"></a>Linux 및 UNIX 서버  

> [!Important]  
> 2018년 3월 22일을 기준으로 Configuration Manager용 Linux 및 UNIX 클라이언트가 사용되지 않습니다. 자세한 내용은 [Linux 및 Unix 클라이언트 지원에 대한 사용 중단 알림](/sccm/core/plan-design/changes/whats-new-in-version-1802#deprecation-announcement-for-linux-and-unix-client-support)을 참조하세요.  

 Linux 및 UNIX용 구성 관리자 클라이언트에서 Linux 및 UNIX 서버를 관리하세요.  

 Linux 및 UNIX 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 **추가 운영 체제용 클라이언트**를 다운로드합니다. 클라이언트 설치 패키지 외에도 클라이언트 다운로드에는 각 컴퓨터의 클라이언트 설치를 관리하는 스크립트가 들어 있습니다.  


### <a name="requirements-and-limitations"></a>요구 사항 및 제한 사항:

-   Linux 및 UNIX용 클라이언트에 대한 OS 파일 종속성을 검토하려면 [Linux 및 UNIX 서버에 클라이언트 배포를 위한 필수 조건](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#BKMK_ClientDeployPrereqforLnU)을 참조하세요.  

-   Linux 또는 UNIX에 대해 지원되는 관리 기능의 개요는 [UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers)을 참조하세요.  

-   Linux 및 UNIX에 대해 지원되는 버전의 경우 나열된 버전에는 모든 후속 부 버전이 포함됩니다. 예를 들어 CentOS 버전 6에는 CentOS 6.3이 포함됩니다. 마찬가지로 SUSE Linux Enterprise Server 11 SP1과 같이 서비스 팩을 사용하는 OS에 대한 지원에는 해당 OS 버전의 후속 서비스 팩이 포함됩니다.  

-   클라이언트 설치 패키지 및 유니버설 에이전트에 대한 자세한 내용은 [UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers)을 참조하세요.  


### <a name="supported-versions"></a>지원되는 버전

다음 버전은 표시된 .tar 파일을 사용하여 지원됩니다.  

#### <a name="aix"></a>AIX  

|Version|TAR 파일|  
|-|-|  
|버전 6.1(Power)|ccm-Aix61ppc.&lt;빌드\>.tar|  
|버전 7.1(Power)|ccm-Aix71ppc.&lt;빌드\>.tar|  

#### <a name="centos"></a>CentOS  

|Version|TAR 파일|  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

#### <a name="debian"></a>Debian  

|Version|TAR 파일|  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 8 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 8 x64|ccm-Universalx64.&lt;빌드\>.tar|  

#### <a name="hp-ux"></a>HP-UX  

|Version|TAR 파일|  
|-|-|  
|버전 11iv3 IA64|ccm-HpuxB.11.31i64.&lt;빌드\>.tar|  

#### <a name="oracle-linux"></a>Oracle Linux  

|Version|TAR 파일|  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

#### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|Version|TAR 파일|  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

#### <a name="solaris"></a>Solaris  

|Version|TAR 파일|  
|-|-|  
|버전 10 x86|ccm-Sol10x86.&lt;빌드\>.tar|  
|버전 10 SPARC|ccm-Sol10sparc.&lt;빌드\>.tar|  
|버전 11 x86|ccm-Sol11x86.&lt;빌드\>.tar|  
|버전 11 SPARC|ccm-Sol11sparc.&lt;빌드\>.tar|  

#### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|Version|TAR 파일|  
|-|-|  
|버전 10 SP1 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 10 SP1 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 11 SP1 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 11 SP1 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 12 x64|ccm-Universalx64.&lt;빌드\>.tar|  

#### <a name="ubuntu"></a>Ubuntu  

|Version|TAR 파일|  
|-|-|  
|버전 10.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 10.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 12.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 12.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 14.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 14.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 16.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 16.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  



##  <a name="bkmk_OnpremOS"></a> 온-프레미스 모바일 디바이스 관리  

 Configuration Manager에는 클라이언트 소프트웨어를 설치하지 않고 온-프레미스의 디바이스를 관리할 수 있는 기본 제공 기능이 있습니다. 자세한 내용은 [온-프레미스 인프라로 모바일 디바이스 관리](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)를 참조하세요.  


### <a name="requirements-and-limitations"></a>요구 사항 및 제한 사항:

-   계층 구조의 최상위 계층 사이트에서 **서비스 연결점**을 구성해야 합니다.  


### <a name="supported-operating-systems"></a>지원되는 운영 체제

- **Windows 10 Pro**(x86, x64)  

- **Windows 10 Pro Enterprise**(x86, x64)  

- **Windows 10 IoT Enterprise**(x86, x64)  
    이 버전에는 LTSC(장기 서비스 채널)가 포함됩니다. 자세한 내용은 [Overview of Windows 10 IoT Enterprise](https://docs.microsoft.com/windows/iot-core/windows-iot-enterprise)\(Windows 10 IoT Enterprise 개요\)를 참조하세요.<!--SCCMDocs issue 560-->  

- **Windows 10 Mobile**  

- **Windows 10 Mobile Enterprise**  

- **Windows 10 IoT Mobile Enterprise**  

- **Windows 10 Team for Surface Hub**  



##  <a name="bkmk_ExSrvConOS"></a> Exchange Server 커넥터  

Configuration Manager에서는 Configuration Manager 클라이언트를 설치하지 않고 Exchange Server에 연결하는 디바이스에 대한 제한적인 관리를 지원합니다. 자세한 내용은 [Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.  


### <a name="supported-versions-of-exchange-server"></a>Exchange Server의 지원되는 버전

- **Exchange Online(Office 365)**: 이 버전에는 Business Productivity Online Standard Suite가 포함되어 있습니다.  

- **Exchange Server 2016**(1802 버전부터 시작)  

- **Exchange Server 2013**  

- **Exchange Server 2010 SP1** 또는 **Exchange Server 2010 SP2** 
