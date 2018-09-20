---
title: 사이트 필수 조건
titleSuffix: Configuration Manager
description: Windows 컴퓨터를 Configuration Manager 사이트 시스템 서버로 구성하는 방법을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 10dfebccd997a42f4c79e5d88bdf05e26585aebb
ms.sourcegitcommit: 7eebd112a9862bf98359c1914bb0c86affc5dbc0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589875"
---
# <a name="site-and-site-system-prerequisites-for-configuration-manager"></a>Configuration Manager의 사이트 및 사이트 시스템 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

Windows 기반 컴퓨터에서 Configuration Manager 사이트 시스템 서버로서의 사용을 지원하려면 특정한 구성이 필요합니다. 

이 문서에서는 주로 [Windows Server 2012 이상](#bkmk_2012Prereq)을 중점적으로 다룹니다. [Windows Server 2008 R2 및 Windows Server 2008](#bkmk_2008)은 배포 지점 사이트 시스템 역할에 대해 지원됩니다. 자세한 내용은 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)를 참조하세요. 

WSUS(Windows Server Update Services)와 같은 일부 제품의 경우 소프트웨어 업데이트 지점에 대한 해당 제품 설명서를 참조하여 사용을 위한 추가 필수 구성 요소 및 제한 사항을 확인하세요. 여기에는 Configuration Manager에서 사용하는 경우에 직접 적용되는 구성만 포함되어 있습니다.   

> [!NOTE]  
>  2016년 1월에 .NET Framework 4.0, 4.5 및 4.5.1에 대한 지원이 만료되었습니다. 자세한 내용은 [Microsoft .NET Framework 지원 기간 정책 FAQ](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)를 참조하세요.  



## <a name="bkmk_generalprerewq"></a> 일반 요구 사항 및 제한 사항

다음 요구 사항은 모든 사이트 시스템 서버에 적용됩니다.

- 각 사이트 시스템 서버는 64비트 OS를 사용해야 합니다. 단, 일부 32비트 운영 체제에 설치할 수 있는 배포 지점 사이트 시스템 역할의 경우는 예외입니다.  

- 사이트 시스템은 모든 운영 체제의 Server Core 설치에서 지원되지 않습니다. Server Core 설치가 배포 지점 사이트 시스템 역할에 대해 지원되는 경우는 예외입니다. 자세한 내용은 [Configuration Manager 사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)를 참조하세요.  

- 사이트 시스템 서버를 설치한 후에는 다음 항목을 변경할 수 없습니다.  

    - 사이트 시스템 컴퓨터가 있는 도메인의 도메인 이름(**도메인 이름 바꾸기**라고도 함).  

    - 컴퓨터의 도메인 멤버 자격.  

    - 컴퓨터의 이름.  

  이러한 항목을 변경해야 하는 경우 먼저 컴퓨터에서 사이트 시스템 역할을 제거합니다. 그런 다음, 변경이 완료되면 역할을 다시 설치합니다. 사이트 서버에 영향을 주는 변경 내용의 경우 먼저 사이트를 제거합니다. 그런 다음, 변경이 완료되면 사이트를 다시 설치합니다.  

- Windows Server 클러스터의 인스턴스에서는 사이트 시스템 역할이 지원되지 않습니다. 단, 사이트 데이터베이스 서버의 경우는 예외입니다. 자세한 내용은 [Configuration Manager 사이트 데이터베이스에 SQL Server 클러스터 사용](/sccm/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database)을 참조하세요.  

- 모든 Configuration Manager 서비스의 시작 유형 또는 다음 사용자로 “로그온” 설정은 변경할 수 없습니다. 이 설정을 변경하면 주요 서비스가 정상적으로 실행되지 않을 수 있습니다.  


###  <a name="bkmk_2012Prereq"></a> Windows Server 2012 이상 운영 체제의 필수 조건  

Windows Server 2012 이상에서 사이트 시스템 서버 및 역할의 특정 필수 구성 요소에 대한 이 문서의 주요 섹션을 참조하세요.

- [중앙 관리 사이트 및 기본 사이트 서버](#bkmk_2012sspreq)
- [보조 사이트 서버](#bkmk_2012secpreq)
- [데이터베이스 서버](#bkmk_2012dbpreq)
- [SMS 공급자 서버](#bkmk_2012smsprovpreq)
- [응용 프로그램 카탈로그 웹 사이트 지점](#bkmk_2012acwspreq)
- [응용 프로그램 카탈로그 웹 서비스 지점](#bkmk_2012ACwsitepreq)
- [Asset Intelligence 동기화 지점](#bkmk_2012AIpreq)
- [인증서 등록 지점](#bkmk_2012crppreq)
- [배포 지점](#bkmk_2012dppreq)
- [Endpoint Protection 지점](#bkmk_2012EPPpreq)
- [등록 지점](#bkmk_2012Enrollpreq)
- [등록 프록시 지점](#bkmk_2012EnrollProxpreq)
- [대체 상태 지점](#bkmk_2012FSPpreq)
- [관리 지점](#bkmk_2012MPpreq)
- [보고 지점](#bkmk_2012RSpoint)
- [서비스 연결 지점](#bkmk_SCPpreq)
- [소프트웨어 업데이트 지점](#bkmk_2012SUPpreq)
- [상태 마이그레이션 지점](#bkmk_2012SMPpreq)

##  <a name="bkmk_2012sspreq"></a> 중앙 관리 사이트 및 기본 사이트 서버 

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

- .NET Framework 3.5 SP1 이상  

- .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2  

    - .Net Framework 버전에 대한 자세한 내용은 [.NET Framework 버전 및 종속성](https://docs.microsoft.com/dotnet/framework/migration-guide/versions-and-dependencies)을 참조하세요.

- 원격 차등 압축  

#### <a name="windows-adk"></a>Windows ADK  

- 중앙 관리 사이트 또는 기본 사이트를 설치하거나 업그레이드하기 전에 설치하거나 업그레이드할 Configuration Manager 버전에서 요구하는 Windows ADK(평가 및 배포 키트) 버전을 설치합니다. 자세한 내용은 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요.  

- 이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

#### <a name="visual-c-redistributable"></a>Visual C++ 재배포 가능 패키지  

- Configuration Manager는 사이트 서버를 설치하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

- 중앙 관리 사이트와 기본 사이트에는 해당하는 재배포 가능 패키지 파일의 x86 및 x64 버전이 모두 필요합니다.  



##  <a name="bkmk_2012secpreq"></a> 보조 사이트 서버   

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

- .NET Framework 3.5 SP1 이상  

- .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2  

    - .Net Framework 버전에 대한 자세한 내용은 [.NET Framework 버전 및 종속성](https://docs.microsoft.com/dotnet/framework/migration-guide/versions-and-dependencies)을 참조하세요.  

- 원격 차등 압축  

#### <a name="visual-c-redistributable"></a>Visual C++ 재배포 가능 패키지  

- Configuration Manager는 사이트 서버를 설치하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

- 보조 사이트에는 x64 버전만 필요합니다.  

#### <a name="default-site-system-roles"></a>기본 사이트 시스템 역할  

- 기본적으로 보조 사이트는 **관리 지점**과 **배포 지점**을 설치합니다.  

- 보조 사이트 서버는 이러한 사이트 시스템 역할에 대한 필수 구성 요소를 충족해야 합니다.  



##  <a name="bkmk_2012dbpreq"></a> 데이터베이스 서버  

#### <a name="remote-registry-service"></a>원격 레지스트리 서비스를  

- Configuration Manager 사이트를 설치하는 동안 사이트 데이터베이스를 호스트하는 컴퓨터에서 **원격 레지스트리** 서비스를 사용하도록 설정합니다.  

#### <a name="sql-server"></a>SQL Server  

- 중앙 관리 사이트 또는 기본 사이트를 설치하기 전에 사이트 데이터베이스를 호스트할 수 있는 버전의 SQL Server를 설치합니다. 자세한 내용은 [지원되는 SQL Server 버전](/sccm/core/plan-design/configs/support-for-sql-server-versions)을 참조하세요.  

- 보조 사이트를 설치하기 전에 이 버전의 SQL Server를 설치할 수 있습니다.  

- Configuration Manager에서 보조 사이트 설치의 일부로 SQL Server Express를 설치하도록 선택한 경우 컴퓨터가 SQL Server Express를 실행하기 위한 요구 사항을 충족하는지 확인합니다.  



##  <a name="bkmk_2012smsprovpreq"></a> SMS 공급자 서버  

#### <a name="windows-adk"></a>Windows ADK  

- SMS 공급자의 인스턴스를 설치하는 컴퓨터에는 설치하거나 업그레이드 중인 Configuration Manager 버전에서 요구하는 Windows ADK의 필수 버전이 있어야 합니다. 자세한 내용은 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요.  

- 이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  



##  <a name="bkmk_2012acwspreq"></a> 응용 프로그램 카탈로그 웹 사이트 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

- .NET Framework 3.5 SP1 이상  

- .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2  

    - ASP.NET 4.5  

    - .Net Framework 버전에 대한 자세한 내용은 [.NET Framework 버전 및 종속성](https://docs.microsoft.com/dotnet/framework/migration-guide/versions-and-dependencies)을 참조하세요.  


#### <a name="iis-configuration"></a>IIS 구성  

-   일반 HTTP 기능:  

    -   기본 문서  

    -   정적 콘텐츠  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   .NET 확장성 4.5  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  



##  <a name="bkmk_2012ACwsitepreq"></a> 응용 프로그램 카탈로그 웹 서비스 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2:  

    -   ASP.NET 4.5:  

        -   HTTP 활성화 및 자동으로 선택된 옵션  

#### <a name="iis-configuration"></a>IIS 구성  

-   일반 HTTP 기능:  

    -   기본 문서  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 4.5  

#### <a name="computer-memory"></a>컴퓨터 메모리  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최솟값인 5%가 그대로 유지됩니다.  



##  <a name="bkmk_2012AIpreq"></a> Asset Intelligence 동기화 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2 



##  <a name="bkmk_2012crppreq"></a> 인증서 등록 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2:  

    -   HTTP 활성화  

#### <a name="iis-configuration"></a>IIS 구성  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  



##  <a name="bkmk_2012dppreq"></a> 배포 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   원격 차등 압축  

#### <a name="iis-configuration"></a>IIS 구성  

-   응용 프로그램 개발:  

    -   ISAPI 확장  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  

#### <a name="powershell"></a>PowerShell  

-   Windows Server 2012 이상에서는, 배포 지점을 설치하려면 먼저 PowerShell 3.0 또는 4.0이 있어야 합니다.  

#### <a name="visual-c-redistributable"></a>Visual C++ 재배포 가능 패키지  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   설치되는 버전은 컴퓨터 플랫폼(x86 또는 x64)에 따라 달라집니다.  

#### <a name="microsoft-azure"></a>Microsoft Azure  

-   Microsoft Azure의 클라우드 서비스를 사용하여 배포 지점을 호스트할 수 있습니다.  

#### <a name="to-support-pxe-or-multicast"></a>PXE 또는 멀티캐스트를 지원하려면  

-   WDS(Windows 배포 서비스) Windows Server 역할을 설치 및 구성합니다.  

    > [!NOTE]  
    >  Windows Server 2012 이상을 실행하는 서버에서는 PXE 또는 멀티캐스트를 지원하도록 배포 지점을 구성할 때 WDS가 자동으로 설치되고 구성됩니다.  

-   버전 1806부터 Windows 배포 서비스가 없는 배포 지점에서 PXE 응답기를 사용하도록 설정합니다.  

자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.

<!--sms.503672 -Clarified BITS use-->
> [!NOTE]  
> 배포 지점은 콘텐츠를 전송할 때 Windows에 기본 제공되는 BITS(**Background Intelligent Transfer Service**)를 사용하여 전송합니다. 배포 지점 역할은 선택적인 BITS IIS 서버 확장 기능을 설치할 필요가 없는데, 클라이언트가 이 기능으로 정보를 업로드하지 않기 때문입니다.  



##  <a name="bkmk_2012EPPpreq"></a> Endpoint Protection 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 3.5 SP1 이상  



##  <a name="bkmk_2012Enrollpreq"></a> 등록 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 3.5 이상  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2:  

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

    -   HTTP 활성화 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5  

#### <a name="iis-configuration"></a>IIS 구성  

-   일반 HTTP 기능:  

    -   기본 문서  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 4.5  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

#### <a name="computer-memory"></a>컴퓨터 메모리  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최솟값인 5%가 그대로 유지됩니다.  



##  <a name="bkmk_2012EnrollProxpreq"></a> 등록 프록시 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 3.5 이상  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2 

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

#### <a name="iis-configuration"></a>IIS 구성  

-   일반 HTTP 기능:  

    -   기본 문서  

    -   정적 콘텐츠  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   .NET 확장성 4.5  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

#### <a name="computer-memory"></a>컴퓨터 메모리  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최솟값인 5%가 그대로 유지됩니다.  



##  <a name="bkmk_2012FSPpreq"></a> 대체 상태 지점  

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  



##  <a name="bkmk_2012MPpreq"></a> 관리 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2 

-   BITS 서버 확장 및 자동으로 선택된 옵션이나 BITS(Background Intelligent Transfer Services) 및 자동으로 선택된 옵션  

#### <a name="iis-configuration"></a>IIS 구성  

-   응용 프로그램 개발:  

    -   ISAPI 확장  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  



##  <a name="bkmk_2012RSpoint"></a> 보고 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2 

#### <a name="sql-server-reporting-services"></a>SQL Server Reporting Services  

-   보고 지점을 설치하기 전에 SQL Server Reporting Services를 지원할 수 있는 SQL Server의 인스턴스를 하나 이상 설치하고 구성합니다.  

-   SQL Server Reporting Services에 사용하는 인스턴스는 사이트 데이터베이스에 사용하는 인스턴스와 동일할 수 있습니다.  

-   또한 다른 System Center 제품에 SQL Server 인스턴스 공유 관련 제한이 없는 경우 SQL Server Reporting Services에 사용하는 인스턴스를 다른 System Center 제품과 공유할 수 있습니다.  



##  <a name="bkmk_SCPpreq"></a> 서비스 연결 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2 

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

#### <a name="visual-c-redistributable"></a>Visual C++ 재배포 가능 패키지  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   사이트 시스템 역할에는 x64 버전이 필요합니다.  



##  <a name="bkmk_2012SUPpreq"></a> 소프트웨어 업데이트 지점  

#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2 

기본 IIS 구성이 필요합니다.

#### <a name="windows-server-update-services"></a>Windows Server Update Services  

-   소프트웨어 업데이트 지점을 설치하기 전에 컴퓨터에 Windows 서버 역할 Windows Server Update Services를 설치합니다.  

-   자세한 내용은 [소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates)을 참조하세요.  



##  <a name="bkmk_2012SMPpreq"></a> 상태 마이그레이션 지점  
<!--SCCMDocs issue 645-->
#### <a name="windows-server-roles-and-features"></a>Windows Server 역할 및 기능  

-   .NET Framework 3.5 이상  

-   .NET Framework 4.5.2, 4.6.1, 4.6.2, 4.7, 4.7.1 또는 4.7.2:  

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

    -   HTTP 활성화 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5  

#### <a name="iis-configuration"></a>IIS 구성  

-   일반 HTTP 기능:  

    -   기본 문서  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 4.5  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  



##  <a name="bkmk_2008"></a> Windows Server 2008 R2 및 Windows Server 2008에 대한 필수 조건  

[Microsoft 지원 기간](https://support.microsoft.com/lifecycle)에 설명된 대로 Windows Server 2008 및 Windows Server 2008 R2는 현재 추가 지원 상태이며 더 이상 일반 지원에 속하지 않습니다. 향후에 Configuration Manager에서 이러한 운영 체제를 사이트 시스템 서버로 사용할 수 있는지에 대한 자세한 내용은 [제거되고 사용되지 않는 서버 운영 체제](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems)를 참조하세요.  

이러한 OS 버전은 사이트 서버 또는 대부분의 사이트 시스템 역할에 대해 지원되지 않습니다. 풀(pull) 배포 지점을 포함한 배포 지점 사이트 시스템 역할 및 PXE와 멀티캐스트에 대해서는 계속 지원됩니다.


###  <a name="bkmk_2008dppreq"></a> 배포 지점  

#### <a name="iis-configuration"></a>IIS 구성

기본 IIS 구성 또는 사용자 지정 구성을 사용할 수 있습니다. 사용자 지정 IIS 구성을 사용하려면 IIS에 대해 다음 옵션을 사용하도록 설정해야 합니다.  

-   응용 프로그램 개발:  

    -   ISAPI 확장  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  

사용자 지정 IIS 구성을 사용하는 경우 다음과 같이 불필요한 옵션을 제거할 수 있습니다.  

-   일반 HTTP 기능:  

    -   HTTP 리디렉션  

-   IIS 관리 스크립트 및 도구  

#### <a name="windows-feature"></a>Windows 기능  

-   원격 차등 압축  

#### <a name="visual-c-redistributable"></a>Visual C++ 재배포 가능 패키지  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   설치되는 버전은 컴퓨터 플랫폼(x86 또는 x64)에 따라 달라집니다.  

#### <a name="microsoft-azure"></a>Microsoft Azure  

-   Azure의 클라우드 서비스를 사용하여 배포 지점을 호스트할 수 있습니다.  

#### <a name="to-support-pxe-or-multicast"></a>PXE 또는 멀티캐스트를 지원하려면  

-   WDS(Windows 배포 서비스) Windows Server 역할을 설치 및 구성합니다.  

    > [!NOTE]  
    >  Windows Server 2012 이상을 실행하는 서버에서는 PXE 또는 멀티캐스트를 지원하도록 배포 지점을 구성할 때 WDS가 자동으로 설치되고 구성됩니다.  

-   버전 1806부터 Windows 배포 서비스가 없는 배포 지점에서 PXE 응답기를 사용하도록 설정합니다.  

자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.

<!--sms.503672 -Clarified BITS use-->
> [!NOTE]  
> 배포 지점은 콘텐츠를 전송할 때 Windows 운영 체제에 기본 제공되는 BITS(**Background Intelligent Transfer Service**)를 사용하여 전송합니다. 배포 지점 역할은 선택적인 BITS IIS 서버 확장 기능을 설치할 필요가 없는데, 클라이언트가 이 기능으로 정보를 업로드하지 않기 때문입니다.   

