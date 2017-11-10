---
title: "Windows 서버 준비"
titleSuffix: Configuration Manager
description: "컴퓨터가 System Center Configuration Manager의 사이트 서버 또는 사이트 시스템 서버를 사용하기 위한 필수 조건을 충족하는지 확인합니다."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2aca914f-641e-4bc8-98d4-bbf0a2a5276f
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 77fee006aaf7c55c05fc66106fef1ecfc4d27d08
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="prepare-windows-servers-to-support-system-center-configuration-manager"></a>System Center Configuration Manager 지원을 위해 Windows 서버 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

Windows 컴퓨터를 System Center Configuration Manager용 사이트 시스템 서버로 사용하려면 해당 컴퓨터가 사이트 서버 또는 사이트 시스템 서버로 사용할 용도에 해당하는 필수 조건을 충족해야 합니다.  

-   이러한 필수 조건에는 컴퓨터의 서버 관리자를 통해 사용하도록 설정할 수 있는 하나 이상의 Windows 기능이나 역할이 포함되는 경우가 많습니다.  

-   Windows 기능 및 역할을 사용하도록 설정하는 방법은 운영 체제별로 다르므로 사용 중인 운영 체제를 설정하는 방법에 대한 자세한 내용은 해당 운영 체제의 설명서를 참조하세요.  

이 문서에서는 Configuration Manager 사이트 시스템 지원에 필요한 Windows 구성 유형에 대한 개요를 제공합니다. 특정 사이트 시스템 역할에 대한 구성 세부 정보는 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.

##  <a name="BKMK_WinFeatures"></a> Windows 기능 및 역할  
 컴퓨터에서 Windows 기능 및 역할을 설정할 때는 해당 구성을 완료하기 위해 컴퓨터를 다시 부팅해야 할 수 있습니다. 따라서 Configuration Manager 사이트 또는 사이트 시스템 서버를 설치하기 전에 특정 사이트 시스템 역할을 호스트할 컴퓨터를 식별해 두는 것이 좋습니다.
### <a name="features"></a>기능  
 특정 사이트 시스템 서버에서는 다음 Windows 기능이 필요하며, 해당 컴퓨터에 사이트 시스템 역할을 설치하기 전에 이러한 기능을 설정해야 합니다.  

-   **.NET Framework**: 다음을 포함합니다.  

    -   ASP.NET  
    -   HTTP 활성화  
    -   비HTTP 활성화  
    -   WCF(Windows Communication Foundation) 서비스  

    각 사이트 시스템 역할에는 각기 다른 버전의 .NET Framework가 필요합니다.  

    .NET Framework 4.0 이상 버전은 이전 버전과 호환되지 않아 3.5 이하 버전 대신 사용할 수 없으므로 다른 버전이 필수 버전으로 표시되면 같은 컴퓨터에서 각 버전을 사용할 수 있도록 계획합니다.  

-   **BITS(Background Intelligent Transfer Services)**: 관리 지점에서는 관리 장치와의 통신을 지원하기 위해 BITS 및 자동으로 선택되는 옵션을 사용해야 합니다.  

-   **BranchCache**: BranchCache를 사용하는 클라이언트를 지원하기 위해 BranchCache를 사용하여 배포 지점을 설정할 수 있습니다.  

-   **데이터 중복 제거**: 데이터 중복 제거로 배포 지점을 설정하여 해당 배포 지점에서 데이터 중복 제거 기능을 활용할 수 있습니다.  

-   **RDC(원격 차등 압축)**: 사이트 서버 또는 배포 지점을 호스트하는 각 컴퓨터에는 RDC가 필요합니다.   
    RDC는 패키지 서명을 생성하고 서명을 비교하는 데 사용됩니다.  

### <a name="roles"></a>역할  
 소프트웨어 업데이트 및 운영 체제 배포와 같은 특정 기능을 지원하려면 다음과 같은 Windows 역할이 필요합니다. 반면, 대부분의 일반 사이트 시스템 역할에는 IIS가 필요합니다.  

 -   **네트워크 장치 등록 서비스**(Active Directory 인증서 서비스에서): 이 Windows 역할은 Configuration Manager의 인증서 프로필 사용을 위한 필수 조건입니다.  

 -   **웹 서버(IIS)**: 다음을 포함합니다.  
    -   일반 HTTP 기능 >  
        -   HTTP 리디렉션  
    -   응용 프로그램 개발 >  
        -   .NET 확장  
        -   ASP.NET  
        -   ISAPI 확장  
        -   ISAPI 필터  
    -   관리 도구 >  
        -   IIS 6 관리 호환성  
        -   IIS 6 메타데이터 호환성  
        -   IIS 6 WMI(Windows Management Instrumentation) 호환성  
    -   보안 >  
        -   요청 필터링  
        -   Windows 인증  

 다음 사이트 시스템 역할은 나열된 IIS 구성 중 하나 이상을 사용합니다.  
    -   응용 프로그램 카탈로그 웹 서비스 지점  
    -   응용 프로그램 카탈로그 웹 사이트 지점  
    -   배포 지점  
    -   등록 지점  
    -   등록 프록시 지점  
    -   대체 상태 지점  
    -   관리 지점  
    -   소프트웨어 업데이트 지점  
    -   상태 마이그레이션 지점     

    필요한 IIS의 최소 버전은 사이트 서버의 운영 체제와 함께 제공되는 버전입니다.  

    이러한 IIS 구성 외에 [배포 지점에 대한 IIS 요청 필터링](#BKMK_IISFiltering)도 설정해야 합니다.  

-   **Windows 배포 서비스**: 이 역할은 운영 체제 배포와 함께 사용됩니다.  
-   **Windows Server Update Services**: 이 역할은 소프트웨어 업데이트를 배포할 때 필요합니다.  

##  <a name="BKMK_IISFiltering"></a> 배포 지점에 대한 IIS 요청 필터링  
 기본적으로 IIS는 요청 필터링을 사용하여 HTTP 또는 HTTPS 통신을 통한 여러 파일 이름 확장명 및 폴더 위치 액세스를 차단합니다. 이러한 액세스 차단으로 인해 클라이언트는 배포 지점에서 차단된 확장명이나 폴더 위치가 있는 패키지를 다운로드할 수 없습니다.  

 패키지 원본 파일에 요청 필터링 구성에 의해 IIS에서 차단된 확장명이 있는 경우에는 해당 확장명을 허용하도록 요청 필터링을 설정해야 합니다. 이렇게 하려면 배포 지점 컴퓨터의 IIS 관리자에서 [요청 필터링 기능을 편집](https://technet.microsoft.com/library/hh831621.aspx) 합니다.  

 또한 Configuration Manager에서는 패키지와 응용 프로그램에 대해 다음 파일 이름 확장명이 사용됩니다. 요청 필터링 구성에서 이러한 파일 확장명을 차단하지 않아야 합니다.  

-   .PCK  
-   .PKG  
-   .STA  
-   .TAR  

예를 들어 소프트웨어 배포용 소스 파일에 **bin**이라는 폴더가 포함되거나 **.mdb** 파일 이름 확장명의 파일이 있을 수 있습니다.  

-   기본적으로 IIS 요청 필터링에서는 이러한 요소에 대한 액세스가 차단됩니다. 즉, **bin**은 숨겨진 세그먼트로 차단되고 **.mdb**는 파일 이름 확장명으로 차단됩니다.  

-   배포 지점에서 기본 IIS 구성을 사용하는 경우 BITS를 사용하는 클라이언트가 배포 지점에서 이 소프트웨어 배포를 다운로드하지 못하며 콘텐츠를 기다리고 있는 것으로 표시됩니다.  

-   클라이언트가 이 콘텐츠를 다운로드하게 하려면 해당하는 각 배포 지점에서 IIS 관리자의 **요청 필터링**을 편집해 배포 대상 패키지 및 응용 프로그램에 있는 파일 확장명과 폴더에 대한 액세스를 허용합니다.  

> [!IMPORTANT]  
>  요청 필터를 편집하면 컴퓨터의 공격에 대한 취약성이 증가할 수 있습니다.  
>   
>  -   서버 수준의 편집 내용은 서버의 모든 웹 사이트에 적용됩니다.  
> -   개별 웹 사이트에 대한 편집 내용은 해당 웹 사이트에만 적용됩니다.  
>   
>  보안 모범 사례는 전용 웹 서버에서 Configuration Manager를 실행하는 것입니다. 웹 서버에서 다른 응용 프로그램을 실행해야 하는 경우 Configuration Manager에 사용자 지정 웹 사이트를 사용합니다. 자세한 내용은 [System Center Configuration Manager의 사이트 시스템 서버용 웹 사이트](../../../core/plan-design/network/websites-for-site-system-servers.md)를 참조하세요.  

## <a name="http-verbs"></a>HTTP 동사
**관리 지점:** 클라이언트가 관리 지점과 성공적으로 통신하도록 하려면 관리 지점 서버에서 다음 HTTP 동사가 허용되어야 합니다.  
 - GET
 - POST
 - CCM_POST
 - HEAD
 - PROPFIND

**배포 지점:** 배포 지점에서는 다음 HTTP 동사가 허용되어야 합니다.
 - GET
 - HEAD
 - PROPFIND

요청 필터링 구성 방법에 대한 자세한 내용은 TechNet의 [IIS에서 요청 필터링 구성](https://technet.microsoft.com/library/hh831621.aspx#Verbs) 또는 관리 지점을 호스트하는 Windows Server 버전에 적용되는 유사한 문서를 참조하세요.
