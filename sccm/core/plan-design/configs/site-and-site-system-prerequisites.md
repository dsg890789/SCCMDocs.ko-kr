---
title: "사이트 필수 조건"
titleSuffix: Configuration Manager
description: "Windows 컴퓨터를 System Center Configuration Manager 사이트 시스템 서버로 구성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 02/28/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1392797b-76cb-46b4-a3e4-8f349ccaa078
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 6d1be6375dde2df51aafe076e5613647ecca3c4c
ms.sourcegitcommit: d0fc79214bc35ca172fd2023dfa617b977ee865b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/28/2018
---
# <a name="site-and-site-system-prerequisites-for-system-center-configuration-manager"></a>System Center Configuration Manager의 사이트 및 사이트 시스템 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*


 Windows 기반 컴퓨터에서 System Center Configuration Manager 사이트 시스템 서버로서의 사용을 지원하려면 특정한 구성이 필요합니다.  

 
 WSUS(Windows Server Update Services)와 같은 일부 제품의 경우 소프트웨어 업데이트 지점에 대한 해당 제품 설명서를 참조하여 사용을 위한 추가 필수 구성 요소 및 제한 사항을 확인하세요. 여기에는 Configuration Manager에서 사용하는 경우에 직접 적용되는 구성만 포함되어 있습니다.   

> [!NOTE]  
>  2016년 1월에 .NET Framework 4.0, 4.5 및 4.5.1에 대한 지원이 만료되었습니다. 자세한 내용은 support.microsoft.com에서 [Microsoft .NET Framework 지원 기간 정책 FAQ](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)를 참조하세요.  

## <a name="bkmk_generalprerewq"></a> 일반적인 사이트 서버 요구 사항 및 제한 사항
**다음 사항은 모든 사이트 시스템 서버에 적용됩니다.**

-   각 사이트 시스템 서버는 64비트 운영 체제를 사용해야 합니다. 단, 일부 32비트 운영 체제에 설치할 수 있는 배포 지점 사이트 시스템 역할의 경우는 예외입니다.  

-   사이트 시스템은 모든 운영 체제의 Server Core 설치에서 지원되지 않습니다. 단, PXE 또는 멀티캐스트 지원 없이 Server Core 설치가 배포 지점 사이트 시스템 역할에 대해 지원되는 경우는 예외입니다.  

-   사이트 시스템 서버를 설치한 후에는 다음 항목을 변경할 수 없습니다.  

    -   사이트 시스템 컴퓨터가 있는 도메인의 도메인 이름(**도메인 이름 바꾸기**라고도 함).  

    -   컴퓨터의 도메인 멤버 자격.  

    -   컴퓨터의 이름.  

  이러한 항목 중 하나를 변경해야 하는 경우에는 먼저 컴퓨터에서 사이트 시스템 역할을 제거하고 변경을 완료한 후에 역할을 다시 설치해야 합니다. 이러한 변경이 사이트 서버 컴퓨터에 영향을 주는 경우에는 사이트를 제거하고 변경을 완료한 후에 사이트를 다시 설치해야 합니다.  

-   Windows Server 클러스터의 인스턴스에서는 사이트 시스템 역할이 지원되지 않습니다. 단, 사이트 데이터베이스 서버의 경우는 예외입니다.  

-   모든 Configuration Manager 서비스의 시작 유형 또는 다음 사용자로 “로그온” 설정은 변경할 수 없습니다. 이 설정을 변경하면 주요 서비스가 정상적으로 실행되지 않을 수 있습니다.  

##  <a name="bkmk_2012Prereq"></a> Windows Server 2012 이상 운영 체제의 필수 조건  
###  <a name="bkmk_2012sspreq"></a> 사이트 서버: 중앙 관리 사이트 및 기본 사이트  
  **Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상

-   원격 차등 압축  

**Windows ADK:**  

-   중앙 관리 사이트 또는 기본 사이트를 설치하거나 업그레이드하기 전에 설치하거나 업그레이드할 Configuration Manager 버전에서 요구하는 Windows ADK(평가 및 배포 키트) 버전을 설치해야 합니다. 클라이언트로 Windows 10 지원 문서의 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요.  

-   이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 사이트 서버를 설치하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   중앙 관리 사이트와 기본 사이트에는 해당하는 재배포 가능 패키지 파일의 x86 및 x64 버전이 모두 필요합니다.  

###  <a name="bkmk_2012secpreq"></a> 사이트 서버: 보조 사이트  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상   

-   원격 차등 압축  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 사이트 서버를 설치하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   보조 사이트에는 x64 버전만 필요합니다.  

**기본 사이트 시스템 역할:**  

-   기본적으로 보조 사이트는 **관리 지점**과 **배포 지점**을 설치합니다.  

-   보조 사이트 서버는 이러한 사이트 시스템 역할에 대한 필수 구성 요소를 충족해야 합니다.  

###  <a name="bkmk_2012dbpreq"></a> 데이터베이스 서버  
**원격 레지스트리 서비스:**  

-   Configuration Manager 사이트를 설치하는 동안 사이트 데이터베이스를 호스트하는 컴퓨터에서 원격 레지스트리 서비스를 사용하도록 설정해야 합니다.  

**SQL Server:**  

-   중앙 관리 사이트 또는 기본 사이트를 설치하기 전에 사이트 데이터베이스를 호스트할 수 있는 버전의 SQL Server를 설치해야 합니다.  

-   보조 사이트를 설치하기 전에 이 버전의 SQL Server를 설치할 수 있습니다.  

-   Configuration Manager에서 보조 사이트 설치의 일부로 SQL Server Express를 설치하도록 선택한 경우 컴퓨터가 SQL Server Express를 실행하기 위한 요구 사항을 충족하는지 확인합니다.  

###  <a name="bkmk_2012smsprovpreq"></a> SMS 공급자 서버  
**Windows ADK:**  

-   SMS 공급자의 인스턴스를 설치하는 컴퓨터에는 설치하거나 업그레이드 중인 Configuration Manager 버전에서 요구하는 Windows ADK의 필수 버전이 있어야 합니다. 클라이언트로 Windows 10 지원 문서의 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요.

-   이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

###  <a name="bkmk_2012acwspreq"></a> 응용 프로그램 카탈로그 웹 사이트 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상:  

    -   ASP.NET 4.5  

**IIS 구성:**  

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

###  <a name="bkmk_2012ACwsitepreq"></a> 응용 프로그램 카탈로그 웹 서비스 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상:  

    -   ASP.NET 4.5:  

        -   HTTP 활성화 및 자동으로 선택된 옵션  

**IIS 구성:**  

-   일반 HTTP 기능:  

    -   기본 문서  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 4.5  

**컴퓨터 메모리:**  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최소값인 5%가 그대로 유지됩니다.  

###  <a name="bkmk_2012AIpreq"></a> Asset Intelligence 동기화 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 4.5.2 이상  

###  <a name="bkmk_2012crppreq"></a> 인증서 등록 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 4.5.2 이상:  

    -   HTTP 활성화  

**IIS 구성:**  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  

###  <a name="bkmk_2012dppreq"></a> 배포 지점  
**Windows Server 역할 및 기능:**  

-   원격 차등 압축  

**IIS 구성:**  

-   응용 프로그램 개발:  

    -   ISAPI 확장  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  

**PowerShell:**  

-   Windows Server 2012 이상에서는, 배포 지점을 설치하려면 먼저 PowerShell 3.0 또는 4.0이 있어야 합니다.  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   설치되는 버전은 컴퓨터 플랫폼(x86 또는 x64)에 따라 달라집니다.  

**Microsoft Azure:**  

-   Microsoft Azure의 클라우드 서비스를 사용하여 배포 지점을 호스트할 수 있습니다.  

**PXE 또는 멀티캐스트를 지원하려면**  

-   WDS(Windows 배포 서비스) Windows Server 역할을 설치 및 구성합니다.  

    > [!NOTE]  
    >  Windows Server 2012 이상을 실행하는 서버에서는 PXE 또는 멀티캐스트를 지원하도록 배포 지점을 구성할 때 WDS가 자동으로 설치되고 구성됩니다.  

<!--sms.503672 -Clarified BITS use-->
> [!NOTE]  
> 배포 지점은 콘텐츠를 전송할 때 Windows 운영 체제에 기본 제공되는 BITS(**Background Intelligent Transfer Service**)를 사용하여 전송합니다. 배포 지점 역할은 선택적인 BITS IIS 서버 확장 기능을 설치할 필요가 없는데, 클라이언트가 이 기능으로 정보를 업로드하지 않기 때문입니다.  

###  <a name="bkmk_2012EPPpreq"></a> Endpoint Protection 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 SP1 이상  

###  <a name="bkmk_2012Enrollpreq"></a> 등록 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 이상  

-   .NET Framework 4.5.2 이상:  

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

    -   HTTP 활성화 및 자동으로 선택된 옵션  

    -   ASP.NET 4.5  


**IIS 구성:**  

-   일반 HTTP 기능:  

    -   기본 문서  

-   응용 프로그램 개발:  

    -   ASP.NET 3.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 3.5  

    -   ASP.NET 4.5 및 자동으로 선택된 옵션  

    -   .NET 확장성 4.5  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

**컴퓨터 메모리:**  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최소값인 5%가 그대로 유지됩니다.  

###  <a name="bkmk_2012EnrollProxpreq"></a> 등록 프록시 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 이상  

-   .NET Framework 4.5.2 이상 

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

**IIS 구성:**  

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

**컴퓨터 메모리:**  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최소값인 5%가 그대로 유지됩니다.  

###  <a name="bkmk_2012FSPpreq"></a> 대체 상태 지점  
다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

###  <a name="bkmk_2012MPpreq"></a> 관리 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 4.5.2 이상 

-   BITS 서버 확장 및 자동으로 선택된 옵션이나 BITS(Background Intelligent Transfer Services) 및 자동으로 선택된 옵션  

**IIS 구성:**  

-   응용 프로그램 개발:  

    -   ISAPI 확장  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  

###  <a name="bkmk_2012RSpoint"></a> 보고 서비스 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 4.5.2 이상 

**SQL Server Reporting Services:**  

-   보고 서비스 지점을 설치하기 전에 SQL Server Reporting Services를 지원할 수 있는 SQL Server의 인스턴스를 하나 이상 설치하고 구성합니다.  

-   SQL Server Reporting Services에 사용하는 인스턴스는 사이트 데이터베이스에 사용하는 인스턴스와 동일할 수 있습니다.  

-   또한 다른 System Center 제품에 SQL Server 인스턴스 공유 관련 제한이 없는 경우 SQL Server Reporting Services에 사용하는 인스턴스를 다른 System Center 제품과 공유할 수 있습니다.  

###  <a name="bkmk_SCPpreq"></a> 서비스 연결 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 4.5.2 이상 

     이 사이트 시스템 역할을 설치하면 Configuration Manager에서 자동으로.NET Framework 4.5.2를 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   사이트 시스템 역할에는 x64 버전이 필요합니다.  

###  <a name="bkmk_2012SUPpreq"></a> 소프트웨어 업데이트 지점  
**Windows Server 역할 및 기능:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상 

기본 IIS 구성이 필요합니다.

**Windows Server Update Services:**  

-   소프트웨어 업데이트 지점을 설치하기 전에 컴퓨터에 Windows 서버 역할 Windows Server Update Services를 설치해야 합니다.  

-   자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](../../../sum/plan-design/plan-for-software-updates.md)을 참조하세요.  

### <a name="state-migration-point"></a>상태 마이그레이션 지점  
기본 IIS 구성이 필요합니다.  

##  <a name="bkmk_2008"></a> Windows Server 2008 R2 및 Windows Server 2008에 대한 필수 조건  
[Microsoft 지원 기간](https://support.microsoft.com/lifecycle)에 설명된 대로 Windows Server 2008 및 Windows Server 2008 R2는 현재 추가 지원 상태이며 더 이상 일반 지원에 속하지 않습니다. 향후에 Configuration Manager에서 이러한 운영 체제를 사이트 시스템 서버로 사용할 수 있는지에 대한 자세한 내용은 [제거되고 사용되지 않는 서버 운영 체제](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems)를 참조하세요.  

**다음은 모든 .NET Framework 요구 사항에 적용됩니다.**  

-   사이트 시스템 역할을 설치하기 전에 .NET Framework의 정식 버전을 설치합니다. 예를 들어 [Microsoft .NET Framework 4(독립 실행형 설치 관리자)](http://go.microsoft.com/fwlink/p/?LinkId=193048)를 참조하세요. .NET Framework 4 Client Profile을 설치하는 경우 이 요구 사항을 충족할 수 없습니다.  

**다음은 모든 WCF(Windows Communication Foundation) 활성화 요구 사항에 적용됩니다.**  

-   사이트 시스템 서버에서 .NET Framework Windows 기능의 일부로 WCF 활성화를 구성할 수 있습니다. 예를 들어 Windows Server 2008 R2에서는 **기능 추가 마법사**를 실행하여 서버에 추가 기능을 설치합니다. **기능 선택** 페이지에서 **NET Framework 3.5.1 기능**을 확장하고 **WCF 활성화**를 확장합니다. 이러한 옵션을 사용하려면 **HTTP 활성화** 및 **비HTTP 활성화** 확인란을 모두 선택합니다.  

###  <a name="bkmk_2008sspreq"></a> 사이트 서버: 중앙 관리 사이트 및 기본 사이트  
**.NET Framework:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상 

**Windows 기능:**  

-   원격 차등 압축  

**Windows ADK:**  

-   중앙 관리 사이트 또는 기본 사이트를 설치하거나 업그레이드하기 전에 설치하거나 업그레이드할 Configuration Manager 버전에서 요구하는 Windows ADK 버전을 설치해야 합니다.  클라이언트로 Windows 10 지원 문서의 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요.  

-   이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 사이트 서버를 설치하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   중앙 관리 사이트와 기본 사이트에는 해당하는 재배포 가능 패키지 파일의 x86 및 x64 버전이 모두 필요합니다.  

###  <a name="bkmk_2008secpreq"></a> 사이트 서버: 보조 사이트  
**.NET Framework:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 사이트 서버를 설치하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   보조 사이트에는 x64 버전만 필요합니다.  

**기본 사이트 시스템 역할:**  

-   기본적으로 보조 사이트는 **관리 지점**과 **배포 지점**을 설치합니다.  

-   보조 사이트 서버는 이러한 사이트 시스템 역할에 대한 필수 구성 요소를 충족해야 합니다.  

###  <a name="bkmk_2008dbpreq"></a> 데이터베이스 서버  
**원격 레지스트리 서비스:**  

-   Configuration Manager 사이트를 설치하는 동안 사이트 데이터베이스를 호스트하는 컴퓨터에서 원격 레지스트리 서비스를 사용하도록 설정해야 합니다.  

**SQL Server:**  

-   중앙 관리 사이트 또는 기본 사이트를 설치하기 전에 사이트 데이터베이스를 호스트할 수 있는 버전의 SQL Server를 설치해야 합니다.  

-   보조 사이트를 설치하기 전에 이 버전의 SQL Server를 설치할 수 있습니다.  

-   Configuration Manager에서 보조 사이트 설치의 일부로 SQL Server Express를 설치하도록 선택한 경우 컴퓨터가 SQL Server Express를 실행하기 위한 요구 사항을 충족하는지 확인합니다.  

###  <a name="bkmk_2008smsprovpreq"></a> SMS 공급자 서버  
**Windows ADK:**  

-   SMS 공급자의 인스턴스를 설치하는 컴퓨터에는 설치하거나 업그레이드 중인 Configuration Manager 버전에서 요구하는 Windows ADK의 필수 버전이 있어야 합니다. 클라이언트로 Windows 10 지원 문서의 [Windows 10 ADK](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)를 참조하세요.  

-   이 요구 사항에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment)을 참조하세요.  

###  <a name="bkmk_2008acwspreq"></a> 응용 프로그램 카탈로그 웹 사이트 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상 

**IIS 구성:**

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   일반 HTTP 기능:  

    -   정적 콘텐츠  

    -   기본 문서  

-   응용 프로그램 개발:  

    -   ASP.NET 및 자동으로 선택된 옵션  

         .NET Framework 버전 4.5.2를 설치한 후 IIS를 설치하거나 다시 구성하는 등의 일부 시나리오에서는 ASP.NET 버전 4.5를 명시적으로 사용하도록 설정해야 합니다. 예를 들어 .NET Framework 버전 4.0.30319를 실행하는 64비트 컴퓨터에서 다음 명령을 실행합니다. **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

-   보안:  

    -   Windows 인증  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

###  <a name="bkmk_2008ACwsitepreq"></a> 응용 프로그램 카탈로그 웹 서비스 지점  
**.NET Framework:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상 

**WCF(Windows Communication Foundation) 활성화:**  

-   HTTP 활성화  

-   비HTTP 활성화  

**IIS 구성:**

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   응용 프로그램 개발:  

    -   ASP.NET 및 자동으로 선택된 옵션  

         .NET Framework 버전 4.5.2를 설치한 후 IIS를 설치하거나 다시 구성하는 등의 일부 시나리오에서는 ASP.NET 버전 4.5를 명시적으로 사용하도록 설정해야 합니다. 예를 들어 .NET Framework 버전 4.0.30319를 실행하는 64비트 컴퓨터에서 다음 명령을 실행합니다. **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

**컴퓨터 메모리:**  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최소값인 5%가 그대로 유지됩니다.  

###  <a name="bkmk_2008AIpreq"></a> Asset Intelligence 동기화 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상 

###  <a name="bkmk_2008crppreq"></a> 인증서 등록 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상 

-   HTTP 활성화  

**IIS 구성:**

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

    -   IIS 6 WMI 호환성  

###  <a name="bkmk_2008dppreq"></a> 배포 지점  
**IIS 구성:**

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

**Windows 기능:**  

-   원격 차등 압축  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   설치되는 버전은 컴퓨터 플랫폼(x86 또는 x64)에 따라 달라집니다.  

**Microsoft Azure:**  

-   Azure의 클라우드 서비스를 사용하여 배포 지점을 호스트할 수 있습니다.  

**PXE 또는 멀티캐스트를 지원하려면**  

-   WDS(Windows 배포 서비스) Windows Server 역할을 설치 및 구성합니다.  

    > [!NOTE]  
    >  Windows Server 2012 이상을 실행하는 서버에서는 PXE 또는 멀티캐스트를 지원하도록 배포 지점을 구성할 때 WDS가 자동으로 설치되고 구성됩니다.  

<!--sms.503672 -Clarified BITS use-->
> [!NOTE]  
> 배포 지점은 콘텐츠를 전송할 때 Windows 운영 체제에 기본 제공되는 BITS(**Background Intelligent Transfer Service**)를 사용하여 전송합니다. 배포 지점 역할은 선택적인 BITS IIS 서버 확장 기능을 설치할 필요가 없는데, 클라이언트가 이 기능으로 정보를 업로드하지 않기 때문입니다.   


###  <a name="bkmk_2008EPPpreq"></a> Endpoint Protection 지점  
**.NET Framework:**  

-   .NET Framework 3.5 SP1 이상  

###  <a name="bkmk_2008Enrollpreq"></a> 등록 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상 

     이 사이트 시스템 역할을 설치할 때 서버에 지원되는 버전의 .NET Framework가 아직 설치되어 있지 않은 경우 Configuration Manager에서 .NET Framework 4.5.2를 자동으로 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

**WCF(Windows Communication Foundation) 활성화:**  

-   HTTP 활성화  

-   비HTTP 활성화  

**IIS 구성:**

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   응용 프로그램 개발:  

    -   ASP.NET 및 자동으로 선택된 옵션  

         .NET Framework 버전 4.5.2를 설치한 후 IIS를 설치하거나 다시 구성하는 등의 일부 시나리오에서는 ASP.NET 버전 4.5를 명시적으로 사용하도록 설정해야 합니다. 예를 들어 .NET Framework 버전 4.0.30319를 실행하는 64비트 컴퓨터에서 다음 명령을 실행합니다. **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

**컴퓨터 메모리:**  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최소값인 5%가 그대로 유지됩니다.  

###  <a name="bkmk_2008EnrollProxpreq"></a> 등록 프록시 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상 

     이 사이트 시스템 역할을 설치할 때 서버에 지원되는 버전의 .NET Framework가 아직 설치되어 있지 않은 경우 Configuration Manager에서 .NET Framework 4.5.2를 자동으로 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

**WCF(Windows Communication Foundation) 활성화:**  

-   HTTP 활성화  

-   비HTTP 활성화  

**IIS 구성:**

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   응용 프로그램 개발:  

    -   ASP.NET 및 자동으로 선택된 옵션  

         .NET Framework 버전 4.5.2를 설치한 후 IIS를 설치하거나 다시 구성하는 등의 일부 시나리오에서는 ASP.NET 버전 4.5를 명시적으로 사용하도록 설정해야 합니다. 예를 들어 .NET Framework 버전 4.0.30319를 실행하는 64비트 컴퓨터에서 다음 명령을 실행합니다. **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  

**컴퓨터 메모리:**  

-   이 사이트 시스템 역할을 호스트하는 컴퓨터가 해당 컴퓨터의 사용 가능한 메모리 중 5% 이상을 사용할 수 있어야 사이트 시스템 역할이 요청을 처리할 수 있습니다.  

-   이 요구 사항이 동일하게 적용되는 다른 사이트 시스템 역할과 함께 이 사이트 시스템 역할을 배치해도 컴퓨터에 대한 이 메모리 요구 사항이 증가하지는 않으며 최소값인 5%가 그대로 유지됩니다.  

###  <a name="bkmk_2008FSPpreq"></a> 대체 상태 지점  
**IIS 구성:**

다음 항목이 추가된 기본 IIS 구성이 필요합니다.  

-   IIS 6 관리 호환성:  

    -   IIS 6 메타데이터 호환성  

###  <a name="bkmk_2008MPpreq"></a> 관리 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상

**IIS 구성:**

기본 IIS 구성 또는 사용자 지정 구성을 사용할 수 있습니다. 모바일 장치를 지원할 수 있는 각 관리 지점에서는 ASP.NET용 추가 IIS 구성 및 자동으로 선택된 옵션을 사용해야 합니다.

.NET Framework 버전 4.5.2를 설치한 후 IIS를 설치하거나 다시 구성하는 등의 일부 시나리오에서는 ASP.NET 버전 4.5를 명시적으로 사용하도록 설정해야 합니다. 예를 들어 .NET Framework 버전 4.0.30319를 실행하는 64비트 컴퓨터에서 다음 명령을 실행합니다. **%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe -i -enable**  


사용자 지정 IIS 구성을 사용하려면 IIS에 대해 다음 옵션을 사용하도록 설정해야 합니다.  

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

**Windows 기능:**  

-   BITS 서버 확장 및 자동으로 선택된 옵션이나 BITS(Background Intelligent Transfer Services) 및 자동으로 선택된 옵션  

###  <a name="bkmk_2008RSpoint"></a> 보고 서비스 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상  

**SQL Server Reporting Services:**  

-   보고 서비스 지점을 설치하기 전에 SQL Server Reporting Services를 지원할 수 있는 SQL Server의 인스턴스를 하나 이상 설치하고 구성합니다.  

-   SQL Server Reporting Services에 사용하는 인스턴스는 사이트 데이터베이스에 사용하는 인스턴스와 동일할 수 있습니다.  

-   또한 다른 System Center 제품에 SQL Server 인스턴스 공유 관련 제한이 없는 경우 SQL Server Reporting Services에 사용하는 인스턴스를 다른 System Center 제품과 공유할 수 있습니다.  

###  <a name="bkmk_2008SCPpreq"></a> 서비스 연결 지점  
**.NET Framework:**  

-   .NET Framework 4.5.2 이상 

     이 사이트 시스템 역할을 설치할 때 서버에 지원되는 버전의 .NET Framework가 아직 설치되어 있지 않은 경우 Configuration Manager에서 .NET Framework 4.5.2를 자동으로 설치합니다. 이 설치로 인해 서버가 다시 부팅 보류 중 상태가 될 수 있습니다. .NET Framework에 대한 다시 부팅이 보류 중인 경우 서버가 다시 부팅되어 설치를 완료할 때까지 .NET 응용 프로그램이 실패할 수 있습니다.  

**Visual C++ 재배포 가능 패키지:**  

-   Configuration Manager는 배포 지점을 호스트하는 각 컴퓨터에 Microsoft Visual C++ 2013 재배포 가능 패키지를 설치합니다.  

-   사이트 시스템 역할에는 x64 버전이 필요합니다.  

###  <a name="bkmk_2008SUPpreq"></a> 소프트웨어 업데이트 지점  
**.NET Framework:**  

-   .NET Framework 3.5 SP1 이상  

-   .NET Framework 4.5.2 이상 

**IIS 구성:**

기본 IIS 구성이 필요합니다.  

**Windows Server Update Services:**  

-   소프트웨어 업데이트 지점을 설치하기 전에 컴퓨터에 Windows 서버 역할 Windows Server Update Services를 설치해야 합니다.  

-   자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](../../../sum/plan-design/plan-for-software-updates.md)을 참조하세요.

###  <a name="bkmk_2008SMPpreq"></a> 상태 마이그레이션 지점  
**IIS 구성:**

기본 IIS 구성이 필요합니다.  
