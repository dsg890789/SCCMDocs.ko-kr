---
title: "지원되는 LTSB 구성 "
titleSuffix: Configuration Manager
description: "System Center Configuration Manager의 장기 서비스 분기에서 작동하는 운영 체제 및 종속 제품을 이해합니다."
ms.custom: na
ms.date: 5/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f818d4-7f45-402f-8758-dc88bc024953
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: dad9ad1aba5390c24adc851349aa272aa54c0611
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="supported-configurations-for-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>System Center Configuration Manager의 장기 서비스 분기에 대해 지원되는 구성

*적용 대상: System Center Configuration Manager(장기 서비스 분기)*

이 항목의 정보를 사용하여 Configuration Manager의 LTSB(장기 서비스 분기)에서 지원하는 운영 체제 및 제품 종속을 이해할 수 있습니다.
이 항목이나 LTSB 관련 항목에서 달리 명시되지 않은 경우 현재 분기 버전 1606에 적용되는 것과 동일한 구성 및 제한 사항이 LTSB에 적용됩니다.  충돌이 발생하는 경우 사용 중인 버전에 적용되는 정보를 사용합니다. 일반적으로 LTSB가 현재 분기보다 좀 더 제한적입니다.

## <a name="general-statement-of-support"></a>일반적인 지원 정보
다음 제품 및 기술은 이 Configuration Manager 분기에서 지원됩니다. 그러나 이 내용에 포함되었다고 해서 개별 지원 주기가 끝난 제품 또는 버전의 지원이 명시적으로 확장되지는 않습니다. 즉, 지원 주기가 끝난 제품은 Configuration Manager에서 사용할 수 없습니다. 자세한 내용은 [Microsoft 지원 주기](http://go.microsoft.com/fwlink/p/?LinkId=208270) 웹 사이트 및 [Microsoft 지원 주기 정책 FAQ](http://go.microsoft.com/fwlink/p/?LinkId=31976)를 참조하세요.

또한 다음 항목에 나열되지 않은 제품 및 제품 버전은 [Enterprise Mobility + Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/)(Enterprise Mobility + 보안 블로그)에서 공지되지 않은 경우 지원되지 않습니다.

**이후 지원에 대한 제한 사항:** LTSB는 이후 서버 및 클라이언트 운영 체제와 제품 종속성에 대한 지원이 제한적입니다. LTSB에 대한 플랫폼 목록은 릴리스 수명 동안 다음과 같이 고정됩니다.

**Windows:**
- Windows에 대한 품질 및 보안 업데이트만 지원됩니다.
- Windows 10의 CB(현재 분기), CBB(비즈니스용 현재 분기) 또는 LTSB에 대한 지원은 추가되지 않습니다.
-   Windows Server의 새로운 주 버전은 지원되지 않습니다.

**SQL Server:**
- SQL Server에 대한 품질 및 보안 업데이트나 서비스 팩 등의 부 업그레이드만 지원됩니다.
- SQL Server의 새로운 주 버전은 지원되지 않습니다.  

## <a name="site-systems-and-servers"></a>사이트 시스템 및 서버
LTSB에서는 다음 Windows 컴퓨터 운영 체제를 사이트 시스템으로 사용할 수 있습니다.  각 운영 체제는 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)의 해당 항목과 동일한 요구 사항 및 제한 사항을 갖습니다.  예를 들어 Windows 2012 R2의 Server Core 설치는 x64 버전이어야 하며, 배포 지점을 호스트하기 위해서만 지원되며, PXE 또는 멀티캐스트를 지원하지 않습니다.

**지원되는 운영 체제:**
- Windows Server 2016
- Windows Server 2012 R2(x64): Standard, Datacenter
- Windows Server 2012(x64): Standard, Datacenter
- Windows Server 2008 R2 SP1(x64): Standard, Enterprise, Datacenter
- Windows Server 2008 SP2(x86, x64): Standard, Enterprise, Datacenter*(참고 1 참조)*
- Windows 10 Enterprise 2015 LTSB(x86, x64)
- Windows 10 Enterprise 2016 LTSB(x86, x64)
- Windows 8.1(x86, x64): Professional, Enterprise
- Windows 7 SP1(x86, x64): Professional, Enterprise, Ultimate
- Windows Server 2012의 Server Core 설치
- Windows Server 2012 R2의 Server Core 설치    

*참고 1*: 배포 지점 및 풀(pull) 배포 지점을 제외하고, 이 운영 체제는 사이트 서버 또는 사이트 시스템 역할에 대해 지원되지 않습니다. 이 지원의 중단이 발표되거나 이 운영 체제의 추가 지원 기간이 만료될 때까지 이 운영 체제를 배포 지점으로 계속 사용할 수 있습니다. 자세한 내용은 [Installation of System Center Configuration Manager CB and LTSB fails on Windows Server 2008](https://support.microsoft.com/help/4015095)(Windows Server 2008에서 System Center Configuration Manager CB 및 LTSB 설치 실패)을 참조하세요.

## <a name="client-management"></a>클라이언트 관리
다음 섹션에서는 LTSB를 사용하여 관리할 수 있는 클라이언트 운영 체제를 식별합니다. LTSB에서는 새 운영 체제를 지원되는 클라이언트로 추가할 수 없습니다.

### <a name="windows-computers"></a>Windows 컴퓨터
LTSB를 사용하여 Configuration Manager에 포함된 Configuration Manager 클라이언트 소프트웨어를 통해 다음 Windows 컴퓨터 운영 체제를 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.

**지원되는 운영 체제:**
- Windows Server 2016
- Windows Server 2012 R2(x64): Standard, Datacenter(참고 1)
- Windows Server 2012(x64): Standard, Datacenter(참고 1)
- Windows Storage Server 2012 R2(x64)
- Windows Storage Server 2012(x64)
- Windows Server 2008 R2 SP1(x64): Standard, Enterprise, Datacenter(참고 1)
- Windows Storage Server 2008 R2(x86, x64): Workgroup, Standard, Enterprise
- Windows Server 2008 SP2(x86, x64): Standard, Enterprise, Datacenter(참고 1)
- Windows 10 Enterprise 2015 LTSB(x86, x64)
- Windows 10 Enterprise 2016 LTSB(x86, x64)
- Windows 8.1(x86, x64): Professional, Enterprise
- Windows 7 SP1(x86, x64): Professional, Enterprise, Ultimate
- Windows Server 2012 R2의 Server Core 설치(x64)(참고 2)
- Windows Server 2012의 Server Core 설치(x64)(참고 2)
- Windows Server 2008 R2 SP1의 Server Core 설치(x64)
- Windows Server 2008 SP2의 Server Core 설치(x86, x64)

**(참고 1)** Datacenter 릴리스는 Configuration Manager용으로 지원되지만 인증되지는 않았습니다.  
**(참고 2)** 클라이언트 강제 설치를 지원하려면 이 운영 체제 버전을 실행하는 컴퓨터에서 파일 및 저장소 서비스 서버 역할용으로 파일 서버 역할 서비스를 실행해야 합니다. Server Core 컴퓨터에 Windows 기능을 설치하는 방법에 대한 자세한 내용은 Windows Server 2012 TechNet 라이브러리에서 [Server Core 서버에 서버 역할 및 기능 설치](https://technet.microsoft.com/library/jj574158(v=ws.11).aspx)를 참조하세요.

### <a name="windows-embedded"></a>Windows Embedded
장치에 클라이언트 소프트웨어를 설치하면 LTSB를 사용하여 다음 Windows Embedded 장치를 관리할 수 있습니다.  자세한 내용은 [System Center Configuration Manager에서 Windows Embedded 장치에 클라이언트 배포 계획](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices)을 참조하세요.

**요구 사항 및 제한 사항:**  

-   쓰기 필터를 사용하도록 설정하지 않은, 지원되는 Windows Embedded 시스템에서는 모든 클라이언트 기능이 지원됩니다.  

-   다음 중 하나를 사용하는 클라이언트는 전원 관리를 제외한 모든 기능에 대해 지원됩니다.  

    -   강화된 쓰기 필터(EWF)    

    -   RAM FBWF(파일 기반 쓰기 필터)    

    -   통합 쓰기 필터(UWF)  

-   Windows Embedded 장치에는 응용 프로그램 카탈로그가 지원되지 않습니다.  

-   Windows XP를 기반으로 하는 Windows Embedded 장치에서는 검색된 맬웨어를 모니터링할 수 있으므로 임베디드 장치에 Microsoft Windows WMI 스크립팅 패키지를 설치해야 합니다. 이 패키지를 설치하려면 Windows Embedded Target Designer를 사용합니다. 이 경우 *WBEMDISP.DLL* 및 *WBEMDISP.TLB* 파일이 있고 포함된 장치의 %windir%\System32\WBEM 폴더에 등록되어 있어야 검색된 맬웨어가 보고됩니다.  

**지원되는 운영 체제:**  
-   Windows 10 Enterprise 2016 LTSB(x86, x64)  
-   Windows 10 Enterprise 2015 LTSB(x86, x64)  
-   Windows Embedded 8.1 Industry(x86, x64)    
-   Windows Thin PC(x86, x64)    
-   Windows Embedded POSReady 7(x86, x64)    
-   Windows Embedded Standard 7 SP1(x86, x64)    
-   Windows Embedded POSReady 2009(x86)   
-   Windows Embedded Standard 2009(x86)  

### <a name="windows-ce"></a>Windows CE  
 Configuration Manager와 함께 제공되는 Configuration Manager 모바일 장치 레거시 클라이언트에서 Windows CE 장치를 관리할 수 있습니다.  

**요구 사항 및 제한 사항:**  

-   모바일 장치 클라이언트를 설치하려면 0.78MB의 저장소 공간이 필요합니다. 모바일 장치에서 로그인하려면 최대 256KB의 추가 저장소 공간이 필요할 수 있습니다.    

-   이러한 모바일 장치의 기능은 플랫폼 및 클라이언트 유형별로 달라집니다. Configuration Manager에서 모바일 장치 레거시 클라이언트에 대해 지원하는 관리 기능 종류에 대한 자세한 내용은 [System Center Configuration Manager용 장치 관리 솔루션 선택](/sccm/core/plan-design/choose-a-device-management-solution)을 참조하세요.  

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

### <a name="mac-computers"></a>Mac 컴퓨터  
 LTSB를 사용하여 Mac용 Configuration Manager 클라이언트에서 Mac OS X 컴퓨터를 관리할 수 있습니다.

Mac 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 "추가 운영 체제용 클라이언트" 다운로드의 일부로 다운로드할 수 있습니다.  

Mac 운영 체제에 대한 지원은 이 섹션에 나열된 운영 체제로 제한됩니다. 현재 분기에 대한 Mac 클라이언트 설치 패키지의 이후 업데이트에서 지원될 수 있는 추가 운영 체제는 지원에 포함되지 않습니다.

자세한 내용은 [System Center Configuration Manager에서 Mac에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-macs)을 참조하세요.

**지원되는 버전:**  
-   Mac OS X 10.9(Mavericks)  
-   Mac OS X 10.10(Yosemite)  
-   Mac OS X 10.11(El Capitan)  

## <a name="linux-and-unix-servers"></a>Linux 및 UNIX 서버
LTSB를 사용하여 Linux 및 UNIX용 Configuration Manager 클라이언트에서 Linux 및 UNIX 서버를 관리할 수 있습니다.

Linux 및 UNIX 클라이언트 설치 패키지는 Configuration Manager 미디어와 함께 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 "추가 운영 체제용 클라이언트" 다운로드의 일부로 다운로드할 수 있습니다. 클라이언트 설치 패키지 외에도 클라이언트 다운로드에는 각 컴퓨터의 클라이언트 설치를 관리하는 install 스크립트가 들어 있습니다.

Linux 및 UNIX 운영 체제에 대한 지원은 이 섹션에 나열된 운영 체제로 제한됩니다. 현재 분기에 대한 Linux 및 UNIX 클라이언트 패키지의 이후 업데이트에서 지원될 수 있는 추가 운영 체제는 지원에 포함되지 않습니다.

**요구 사항 및 제한 사항:**  

-   Linux 및 UNIX용 클라이언트에 대한 운영 체제 파일 종속성을 검토하려면 [Linux 및 UNIX 서버에 클라이언트 배포를 위한 필수 조건](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#bkmk_clientdeployprereqforlnu)을 참조하세요.  
-   Linux 또는 UNIX를 실행하는 컴퓨터에 대해 지원되는 관리 기능의 개요는 [System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers)을 참조하세요.  
-   Linux 및 UNIX에 대해 지원되는 버전의 경우 나열된 버전에는 모든 후속 부 버전이 포함됩니다. 예를 들어 CentOS 버전 6이 지원되는 것으로 나와 있는 경우 여기에는 CentOS 6.3과 같은 CentOS 6의 후속 부 버전도 포함됩니다. 마찬가지로 SUSE Linux Enterprise Server 11 SP1과 같이 서비스 팩을 사용하는 운영 체제가 지원되는 것으로 나와 있는 경우에는 해당 운영 체제 버전의 후속 서비스 팩도 지원 대상에 포함됩니다.
-   클라이언트 설치 패키지 및 유니버설 에이전트에 대한 자세한 내용은 [System Center Configuration Manager에서 UNIX 및 Linux 서버에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers)을 참조하세요.


**지원되는 버전:**   
다음 버전은 표시된 .tar 파일을 사용하여 지원됩니다.  
### <a name="aix"></a>AIX  

|버전|파일|  
|-|-|  
|버전 5.3(Power)|ccm-Aix53ppc.&lt;빌드\>.tar|  
|버전 6.1(Power)|ccm-Aix61ppc.&lt;빌드\>.tar|  
|버전 7.1(Power)|ccm-Aix71ppc.&lt;빌드\>.tar|  

### <a name="centos"></a>CentOS  

|버전|파일|  
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="debian"></a>Debian  

|버전|파일|    
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

|버전|파일|  
|-|-|  
|버전 11iv2 IA64|ccm-HpuxB.11.23i64.&lt;빌드\>.tar|  
|버전 11iv2 PA-RISC|ccm-HpuxB.11.23PA.&lt;빌드\>.tar|  
|버전 11iv3 IA64|ccm-HpuxB.11.31i64.&lt;빌드\>.tar|  
|버전 11iv3 PA-RISC|ccm-HpuxB.11.31PA.&lt;빌드\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|버전|파일|    
|-|-|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|버전|파일|  
|-|-|  
|버전 4 x86|ccm-RHEL4x86.&lt;빌드\>.tar|  
|버전 4 x64|ccm-RHEL4x64.&lt;빌드\>.tar|  
|버전 5 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 5 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 6 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 6 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 7 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="solaris"></a>Solaris  

|버전|파일|   
|-|-|  
|버전 9 SPARC|ccm-Sol9sparc.&lt;빌드\>.tar|  
|버전 10 x86|ccm-Sol10x86.&lt;빌드\>.tar|  
|버전 10 SPARC|ccm-Sol10sparc.&lt;빌드\>.tar|  
|버전 11 x86|ccm-Sol11x86.&lt;빌드\>.tar|  
|버전 11 SPARC|ccm-Sol11sparc.&lt;빌드\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|버전|파일|  
|-|-|  
|버전 9 x86|ccm-SLES9x86.&lt;빌드\>.tar|  
|버전 10 SP1 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 10 SP1 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 11 SP1 x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 11 SP1 x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 12 x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|버전|파일|    
|-|-|  
|버전 10.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 10.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 12.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 12.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  
|버전 14.04 LTS x86|ccm-Universalx86.&lt;빌드\>.tar|  
|버전 14.04 LTS x64|ccm-Universalx64.&lt;빌드\>.tar|  

### <a name="exchange-server-connector"></a>Exchange Server 커넥터
 LTSB에서는 클라이언트 소프트웨어를 설치하지 않고 Exchange Sever 인스턴스에 연결하는 장치에 대해 제한적인 관리를 지원합니다. 자세한 내용은 [System Center Configuration Manager와 Exchange를 사용하여 모바일 장치 관리](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync)를 참조하세요.

 **요구 사항 및 제한 사항:**  

-   Configuration Manager는 모바일 장치에 대해 제한적인 관리 기능을 제공합니다. Exchange Server 또는 Exchange Online을 실행하는 서버에 연결하는 EAS(Exchange Active Sync) 사용 가능 장치에 대해 Exchange Server 커넥터를 사용하는 경우 제한적인 관리 기능을 사용할 수 있습니다.  

-   Exchange Server 커넥터가 관리하는 모바일 장치에 대해 Configuration Manager가 지원하는 관리 기능에 대한 자세한 내용은 [System Center Configuration Manager에 대한 장치 관리 솔루션 선택](/sccm/core/plan-design/choose-a-device-management-solution)을 참조하세요.  

**Exchange Server의 지원되는 버전:**  
-   Exchange Server 2010 SP1  
-   Exchange Server 2010 SP2  
-   Exchange Server 2013  

> [!NOTE]
> LTSB는 Exchange Online(Office 365)과 같은 온라인 서비스를 통해 연결하는 장치 관리를 지원하지 않습니다.


## <a name="configuration-manager-console"></a>Configuration Manager 콘솔
LTSB는 다음 운영 체제에서 Configuration Manager 콘솔을 실행하도록 지원합니다. 콘솔을 호스트하는 각 컴퓨터에 최소 .NET Framework 버전 4.5.2가 있어야 합니다(.NET Framework 4.6이 필요한 Windows 10 제외).

**지원되는 운영 체제:**
- Windows Server 2016
- Windows Server 2012 R2(x64): Standard, Datacenter
- Windows Server 2012(x64): Standard, Datacenter
- Windows Server 2008 R2 SP1(x64): Standard, Enterprise, Datacenter
- Windows Server 2008 SP2(x86, x64): Standard, Enterprise, Datacenter
- Windows 10 Enterprise 2016 LTSB(x86, x64)
- Windows 10 Enterprise 2015 LTSB(x86, x64)
- Windows 8.1(x86, x64): Professional, Enterprise
- Windows 7 SP1(x86, x64): Professional, Enterprise, Ultimate


## <a name="sql-server-versions-supported-for-the-site-database-and-reporting-point"></a>사이트 데이터베이스 및 보고 지점에 대해 지원되는 SQL Server 버전
LTSB는 다음 SQL Server 버전에서 사이트 데이터베이스 및 보고 지점을 호스트하도록 지원합니다. 지원되는 각 버전에서 현재 분기에 대한 [SQL Server 버전 지원](/sccm/core/plan-design/configs/support-for-sql-server-versions)에 표시되는 것과 동일한 구성 요구 사항 및 제한 사항이 LTSB에 적용됩니다.  여기에는 SQL Server 클러스터 또는 SQL Server AlwaysOn 가용성 그룹의 사용이 포함됩니다.  

**지원되는 버전:**

- SQL Server 2016: Standard, Enterprise
- SQL Server 2014 SP2: Standard, Enterprise
- SQL Server 2014 SP1: Standard, Enterprise
- SQL Server 2012 SP3: Standard, Enterprise
- SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter
- SQL Server 2016 Express
- SQL Server 2014 Express SP2
- SQL Server 2014 Express SP1
- SQL Server 2012 Express SP3

## <a name="support-for-active-directory-domains"></a>Active Directory 도메인 지원
모든 LTSB 사이트 시스템은 지원되는 Windows Active Directory 도메인의 구성원이어야 합니다. Active Directory 도메인 지원은 [Active Directory 도메인 지원](/sccm/core/plan-design/configs/support-for-active-directory-domains)에 표시되는 것과 동일한 요구 사항 및 제한 사항을 갖지만 다음 도메인 기능 수준으로 제한됩니다.

**지원되는 수준:**
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2

## <a name="additional-support-topics-that-apply-to-the-long-term-servicing-branch"></a>장기 서비스 지점에 적용되는 추가 지원 항목
다음 현재 분기 항목의 정보는 LTSB에 적용됩니다.
- [크기 조정 및 규모 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers)
- [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
- [고가용성 옵션](/sccm/protect/understand/high-availability-options)
- [권장 하드웨어](/sccm/core/plan-design/configs/recommended-hardware)
- [Windows 기능 및 네트워크 지원](/sccm/core/plan-design/configs/support-for-windows-features-and-networks)
- [가상화 환경 지원](/sccm/core/plan-design/configs/support-for-virtualization-environments)
