---
title: 지원되는 사이트 시스템 서버
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 또는 사이트 시스템 역할을 호스트하는 데 사용할 수 있는 Windows 버전을 알아봅니다.
ms.date: 10/02/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 17905b4c-3895-4ad4-a69c-5e0d0fc5a8c3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3fd8e815ab57730ad2186a7e75cd51f21012383a
ms.sourcegitcommit: 265d38d55ca0db043e3a7131a56f123e1d98aa5b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48236177"
---
# <a name="supported-operating-systems-for-configuration-manager-site-system-servers"></a>Configuration Manager 사이트 시스템 서버에 대해 지원되는 운영 체제

*적용 대상: System Center Configuration Manager(현재 분기)*


이 문서에서는 Configuration Manager 사이트 또는 사이트 시스템 역할을 호스트하는 데 사용할 수 있는 Windows 버전에 대해 자세히 설명합니다.


다음 문서의 정보와 함께 이 문서의 정보를 참조하세요.
-   [Configuration Manager에 권장되는 하드웨어](/sccm/core/plan-design/configs/recommended-hardware)
-   [Configuration Manager의 사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
-   [Configuration Manager의 크기 조정 및 규모 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers)



## <a name="bkmk_2016"></a> Windows Server 2016: Standard 및 Datacenter

Configuration Manager 버전 1606([KB3186654](https://support.microsoft.com/help/3186654))용 업데이트 롤업 1을 사용하면 이 OS 버전이 다음 역할에 대해 지원됩니다.

#### <a name="site-servers"></a>사이트 서버

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

#### <a name="site-system-servers"></a>사이트 시스템 서버

-   응용 프로그램 카탈로그 웹 서비스 지점  
-   응용 프로그램 카탈로그 웹 사이트 지점  
-   Asset Intelligence 동기화 지점  
-   인증서 등록 지점  
-   클라우드 관리 게이트웨이 연결점  
-   데이터 웨어하우스 서비스 지점  
-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  
-   Endpoint Protection 지점  
-   등록 지점  
-   등록 프록시 지점  
-   대체 상태 지점  
-   관리 지점
-   보고 서비스 지점  
-   서비스 연결 지점  
-   사이트 데이터베이스 서버 <sup>[참고 2](#bkmk_note2)</sup>  
-   SMS_Provider  
-   소프트웨어 업데이트 지점  
-   상태 마이그레이션 지점



## <a name="bkmk_stor2016"></a> Windows Storage Server 2016

#### <a name="site-system-server"></a>사이트 시스템 서버

-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  



## <a name="bkmk_2012r2"></a> Windows Server 2012 R2(x64): Standard 및 Datacenter  

#### <a name="site-servers"></a>사이트 서버

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

#### <a name="site-system-servers"></a>사이트 시스템 서버

-   응용 프로그램 카탈로그 웹 서비스 지점  
-   응용 프로그램 카탈로그 웹 사이트 지점  
-   Asset Intelligence 동기화 지점  
-   인증서 등록 지점  
-   클라우드 관리 게이트웨이 연결점  
-   데이터 웨어하우스 서비스 지점  
-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  
-   Endpoint Protection 지점  
-   등록 지점  
-   등록 프록시 지점  
-   대체 상태 지점  
-   관리 지점
-   보고 서비스 지점  
-   서비스 연결 지점  
-   사이트 데이터베이스 서버 <sup>[참고 2](#bkmk_note2)</sup>  
-   SMS_Provider  
-   소프트웨어 업데이트 지점  
-   상태 마이그레이션 지점  



## <a name="bkmk_2012"></a> Windows Server 2012(x64): Standard 및 Datacenter  

#### <a name="site-servers"></a>사이트 서버

-   중앙 관리 사이트  
-   기본 사이트  
-   보조 사이트  

#### <a name="site-system-servers"></a>사이트 시스템 서버

-   응용 프로그램 카탈로그 웹 서비스 지점  
-   응용 프로그램 카탈로그 웹 사이트 지점  
-   Asset Intelligence 동기화 지점  
-   인증서 등록 지점  
-   클라우드 관리 게이트웨이 연결점  
-   데이터 웨어하우스 서비스 지점  
-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  
-   Endpoint Protection 지점  
-   등록 지점  
-   등록 프록시 지점  
-   대체 상태 지점  
-   관리 지점
-   보고 서비스 지점  
-   서비스 연결 지점  
-   사이트 데이터베이스 서버 <sup>[참고 2](#bkmk_note2)</sup>  
-   SMS_Provider  
-   소프트웨어 업데이트 지점  
-   상태 마이그레이션 지점  



## <a name="bkmk_2008r2sp1"></a> Windows Server 2008 R2 SP1(x64): Standard, Enterprise 및 Datacenter  

[Microsoft 지원 기간](https://support.microsoft.com/lifecycle)에 설명된 대로 Windows Server 2008 R2는 현재 추가 지원 상태이며 더 이상 일반 지원에 속하지 않습니다. 향후에 Configuration Manager에서 이러한 운영 체제를 사이트 시스템 서버로 사용할 수 있는지에 대한 자세한 내용은 [사용되지 않는 서버 운영 체제](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems)를 참조하세요.  

이 OS는 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 지원되지 않습니다. 풀(pull) 배포 지점을 포함한 배포 지점 사이트 시스템 역할 및 PXE와 멀티캐스트에 대해서는 계속 지원됩니다.

#### <a name="site-system-servers"></a>사이트 시스템 서버
-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  

    - 이 OS의 배포 지점은 PXE 및 멀티캐스트를 지원합니다.  



## <a name="bkmk_2008sp2"></a> Windows Server 2008 SP2(x86, x64): Standard, Enterprise 및 Datacenter  

[Microsoft 지원 기간](https://support.microsoft.com/lifecycle)에 설명된 대로 Windows Server 2008은 현재 추가 지원 상태이며 더 이상 일반 지원에 속하지 않습니다. 향후에 Configuration Manager에서 이러한 운영 체제를 사이트 시스템 서버로 사용할 수 있는지에 대한 자세한 내용은 [사용되지 않는 서버 운영 체제](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems)를 참조하세요.  

OS는 배포 지점 및 풀(pull) 배포 지점을 제외하고, 사이트 서버 또는 사이트 시스템 역할에 대해 지원되지 않습니다. 이 지원의 중단이 발표되거나 이 OS의 추가 지원 기간이 만료될 때까지 이 OS를 배포 지점으로 계속 사용할 수 있습니다. 자세한 내용은 [Installation of System Center Configuration Manager CB and LTSB fails on Windows Server 2008](https://support.microsoft.com/help/4015095)(Windows Server 2008에서 System Center Configuration Manager CB 및 LTSB 설치 실패)을 참조하세요.

#### <a name="site-system-servers"></a>사이트 시스템 서버
-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  

    -   이 OS의 배포 지점은 PXE 및 멀티캐스트를 지원합니다.  

    -   이 OS 버전의 배포 지점은 EFI 모드의 클라이언트 컴퓨터 네트워크 부팅을 지원하지 않습니다. 레거시 모드에서 EFI 부팅 또는 BIOS를 사용하는 클라이언트 컴퓨터는 지원됩니다.  



## <a name="bkmk_win10"></a> Windows 10(x86, x64): Pro 및 Enterprise  

#### <a name="site-system-servers"></a>사이트 시스템 서버

-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  

    -   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE에 대해 지원되지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  

    -   이 OS 버전의 배포 지점은 멀티캐스트를 지원하지 않습니다.  



## <a name="bkmk_win81"></a> Windows 8.1(x86, x64): Professional 및 Enterprise  

#### <a name="site-system-servers"></a>사이트 시스템 서버

-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  

    -   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE에 대해 지원되지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  

    -   이 OS 버전의 배포 지점은 멀티캐스트를 지원하지 않습니다.  



## <a name="bkmk_win7sp1"></a> Windows 7 SP1(x86, x64): Professional, Enterprise 및 Ultimate  

#### <a name="site-system-servers"></a>사이트 시스템 서버

-   배포 지점 <sup>[참고 1](#bkmk_note1)</sup>  

    -   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE에 대해 지원되지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  

    -   이 OS 버전의 배포 지점은 멀티캐스트를 지원하지 않습니다.  



## <a name="bkmk_core1803"></a> Windows Server 버전 1803의 Server Core 설치
<!--503702--> Configuration Manager 1802부터 [Windows Server 버전 1803](https://docs.microsoft.com/windows-server/get-started/get-started-with-1803)은 다음과 같은 제한 사항이 있는 배포 지점으로 사용할 수 있습니다.  

  -   x64비트 버전만 지원됩니다.  

  -   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE 또는 멀티캐스트를 지원하지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  



## <a name="bkmk_core1709"></a> Windows Server 버전 1709의 Server Core 설치

Configuration Manager 1710부터 [Windows Server 버전 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709)는 다음과 같은 제한 사항이 있는 배포 지점으로 사용할 수 있습니다.  

  -   x64비트 버전만 지원됩니다.  

  -   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE 또는 멀티캐스트를 지원하지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  



## <a name="bkmk_core2016"></a> Windows Server 2016의 Server Core 설치

구성 관리자 버전 1606용 업데이트 롤업 1([KB3186654](https://support.microsoft.com/help/3186654))을 사용하면 이 OS 버전을 다음 제한 사항이 있는 배포 지점으로 사용할 수 있습니다.  

  -   x64비트 버전만 지원됩니다.  

  -   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE 또는 멀티캐스트를 지원하지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  



## <a name="bkmk_core2012r2"></a> Windows Server 2012 R2의 Server Core 설치  

Windows Server 2012 R2의 Server Core 설치를 다음과 같은 제한 사항이 있는 배포 지점으로 사용할 수 있습니다.  

-   x64비트 버전만 지원됩니다.

-   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE 또는 멀티캐스트를 지원하지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.  



## <a name="bkmk_core2012"></a> Windows Server 2012의 Server Core 설치  

Windows Server 2012의 Server Core 설치를 다음과 같은 제한 사항이 있는 배포 지점으로 사용할 수 있습니다.  

-   64비트 버전만 지원됩니다.  

-   이 OS의 배포 지점은 기본 Windows 배포 서비스를 사용하는 PXE 또는 멀티캐스트를 지원하지 않습니다. 1806 버전부터는 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 사용하여 이 OS에서 PXE 사용 배포 지점을 사용하도록 설정할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.



## <a name="general-notes"></a>일반 참고 사항

#### <a name="bkmk_note1"></a> 참고 1: 배포 지점
배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  

#### <a name="bkmk_note2"> </a> 참고 2: 사이트 데이터베이스 서버
RODC(읽기 전용 도메인 컨트롤러)에서는 사이트 데이터베이스 서버가 지원되지 않습니다. 자세한 내용은 Microsoft 지원 기사: [도메인 컨트롤러에 SQL Server 설치할 때 문제가 발생할 수 있습니다](https://support.microsoft.com/help/2032911)를 참조하세요. 

또한 모든 도메인 컨트롤러에서 보조 사이트 서버가 지원되지 않습니다.  
