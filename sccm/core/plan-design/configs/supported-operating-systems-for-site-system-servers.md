---
title: "지원되는 사이트 시스템 서버 | Microsoft 문서"
description: "System Center Configuration Manager 사이트 또는 사이트 시스템 역할을 호스트하는 데 사용할 수 있는 Windows 버전을 알아봅니다."
ms.custom: na
ms.date: 3/9/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17905b4c-3895-4ad4-a69c-5e0d0fc5a8c3
caps.latest.revision: 44
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 477ffa5d61d2dfaedf8a3a1f5687e2d72698ad28
ms.openlocfilehash: f175e11d9402e7c57c45edb4d5bbe969de5dcdf7
ms.lasthandoff: 03/10/2017


---
# <a name="supported-operating-systems-for-system-center-configuration-manager-site-system-servers"></a>System Center Configuration Manager 사이트 시스템 서버에 대해 지원되는 운영 체제

*적용 대상: System Center Configuration Manager(현재 분기)*


이 문서에서는 System Center Configuration Manager 사이트 또는 사이트 시스템 역할을 호스트하는 데 사용할 수 있는 Windows 버전에 대해 자세히 설명합니다.


이 항목의 정보를 다음 문서의 정보와 함께 참조하세요.
-   [Configuration Manager에 권장되는 하드웨어](../../../core/plan-design/configs/recommended-hardware.md)
-   [Configuration Manager의 사이트 및 사이트 시스템 필수 조건](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)
-   [Configuration Manager의 크기 조정 및 규모 숫자 값](../../../core/plan-design/configs/size-and-scale-numbers.md)



## <a name="windows-server-2016-standard-and-datacenter"></a>Windows Server 2016: Standard 및 Datacenter
KB3186654의 핫픽스 롤업이 포함된 1606 버전(또는 2016년 10월에 릴리스된 1606 기준 버전)부터 다음에 대해 이 운영 체제가 지원됩니다.

**사이트 서버:**  

-   중앙 관리 사이트  

-   기본 사이트  

-   보조 사이트  

**사이트 시스템 서버:**  

-   응용 프로그램 카탈로그 웹 서비스 지점  

-   응용 프로그램 카탈로그 웹 사이트 지점  

-   Asset Intelligence 동기화 지점  

-   인증서 등록 지점  

-   배포 지점  

     배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

-   Endpoint Protection 지점  

-   등록 지점  

-   등록 프록시 지점  

-   대체 상태 지점  

-   관리 지점

-   보고 서비스 지점  

-   서비스 연결 지점  

-   사이트 데이터베이스 서버  

     RODC(읽기 전용 도메인 컨트롤러)에서는 사이트 데이터베이스 서버가 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료의 [도메인 컨트롤러에 SQL Server 설치할 때 문제가 발생할 수 있습니다.](http://go.microsoft.com/fwlink/p/?LinkId=264856) 를 참조하세요. 또한 모든 도메인 컨트롤러에서 보조 사이트 서버가 지원되지 않습니다.  

-   SMS_Provider  

-   소프트웨어 업데이트 지점  

-   상태 마이그레이션 지점

## <a name="windows-server-2012-r2-x64-standard-and-datacenter"></a>Windows Server 2012 R2(x64): Standard 및 Datacenter  
**사이트 서버:**  

-   중앙 관리 사이트  

-   기본 사이트  

-   보조 사이트  

**사이트 시스템 서버:**  

-   응용 프로그램 카탈로그 웹 서비스 지점  

-   응용 프로그램 카탈로그 웹 사이트 지점  

-   Asset Intelligence 동기화 지점  

-   인증서 등록 지점  

-   배포 지점  

     배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

-   Endpoint Protection 지점  

-   등록 지점  

-   등록 프록시 지점  

-   대체 상태 지점  

-   관리 지점

-   보고 서비스 지점  

-   서비스 연결 지점  

-   사이트 데이터베이스 서버  

     RODC(읽기 전용 도메인 컨트롤러)에서는 사이트 데이터베이스 서버가 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료의 [도메인 컨트롤러에 SQL Server 설치할 때 문제가 발생할 수 있습니다.](http://go.microsoft.com/fwlink/p/?LinkId=264856) 를 참조하세요. 또한 모든 도메인 컨트롤러에서 보조 사이트 서버가 지원되지 않습니다.  

-   SMS_Provider  

-   소프트웨어 업데이트 지점  

-   상태 마이그레이션 지점  

## <a name="windows-server-2012-x64-standard-and-datacenter"></a>Windows Server 2012(x64): Standard 및 Datacenter  
**사이트 서버:**  

-   중앙 관리 사이트  

-   기본 사이트  

-   보조 사이트  

**사이트 시스템 서버:**  

-   응용 프로그램 카탈로그 웹 서비스 지점  

-   응용 프로그램 카탈로그 웹 사이트 지점  

-   Asset Intelligence 동기화 지점  

-   인증서 등록 지점  

-   배포 지점  

     배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

-   Endpoint Protection 지점  

-   등록 지점  

-   등록 프록시 지점  

-   대체 상태 지점  

-   관리 지점

-   보고 서비스 지점  

-   서비스 연결 지점  

-   사이트 데이터베이스 서버  

     RODC(읽기 전용 도메인 컨트롤러)에서는 사이트 데이터베이스 서버가 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료의 [도메인 컨트롤러에 SQL Server 설치할 때 문제가 발생할 수 있습니다.](http://go.microsoft.com/fwlink/p/?LinkId=264856) 를 참조하세요. 또한 모든 도메인 컨트롤러에서 보조 사이트 서버가 지원되지 않습니다.  

-   SMS_Provider  

-   소프트웨어 업데이트 지점  

-   상태 마이그레이션 지점  

## <a name="windows-server-2008-r2-with-sp1-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 R2 with SP1(x64): Standard, Enterprise 및 Datacenter  
 [Microsoft 지원 기간](https://support.microsoft.com/lifecycle)에 설명된 대로 Windows Server 2008 R2는 현재 추가 지원 상태이며 더 이상 일반 지원에 속하지 않습니다. 향후에 Configuration Manager에서 이러한 운영 체제를 사이트 시스템 서버로 사용할 수 있는지에 대한 자세한 내용은 [System Center Configuration Manager에서 제거되는 기능과 사용되지 않는 기능](../../../core/plan-design/changes/removed-and-deprecated-features.md)을 참조하세요.  

**사이트 서버:**  

-   중앙 관리 사이트  

-   기본 사이트  

-   보조 사이트  

**사이트 시스템 서버:**  

-   응용 프로그램 카탈로그 웹 서비스 지점  

-   응용 프로그램 카탈로그 웹 사이트 지점  

-   Asset Intelligence 동기화 지점  

-   인증서 등록 지점  

-   배포 지점  

     배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

-   Endpoint Protection 지점  

-   등록 지점  

-   등록 프록시 지점  

-   대체 상태 지점  

-   관리 지점

-   보고 서비스 지점  

-   서비스 연결 지점  

-   사이트 데이터베이스 서버  

     RODC(읽기 전용 도메인 컨트롤러)에서는 사이트 데이터베이스 서버가 지원되지 않습니다. 자세한 내용은 Microsoft 기술 자료의 [도메인 컨트롤러에 SQL Server 설치할 때 문제가 발생할 수 있습니다.](http://go.microsoft.com/fwlink/p/?LinkId=264856) 를 참조하세요. 또한 모든 도메인 컨트롤러에서 보조 사이트 서버가 지원되지 않습니다.  

-   SMS_Provider  

-   소프트웨어 업데이트 지점  

-   상태 마이그레이션 지점  

## <a name="windows-server-2008-with-sp2-x86-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 SP2(x86, x64): Standard, Enterprise 및 Datacenter  
 [Microsoft 지원 기간](https://support.microsoft.com/lifecycle)에 설명된 대로 Windows Server 2008은 현재 추가 지원 상태이며 더 이상 일반 지원에 속하지 않습니다. 향후에 Configuration Manager에서 이러한 운영 체제를 사이트 시스템 서버로 사용할 수 있는지에 대한 자세한 내용은 [System Center Configuration Manager에서 제거되는 기능과 사용되지 않는 기능](../../../core/plan-design/changes/removed-and-deprecated-features.md)을 참조하세요.  

배포 지점 및 풀(pull) 배포 지점을 제외하고, 이 운영 체제는 사이트 서버 또는 사이트 시스템 역할에 대해 지원되지 않습니다. 이 지원의 중단이 발표되거나 이 운영 체제의 추가 지원 기간이 만료될 때까지 이 운영 체제를 배포 지점으로 계속 사용할 수 있습니다. 자세한 내용은 [Installation of System Center Configuration Manager CB and LTSB fails on Windows Server 2008](https://support.microsoft.com/help/4015095)(Windows Server 2008에서 System Center Configuration Manager CB 및 LTSB 설치 실패)을 참조하세요.

**사이트 시스템 서버:**  
-   배포 지점  

    -   이 운영 체제의 배포 지점은 멀티캐스트를 지원하지 않습니다.  

    -   이 운영 체제 버전의 배포 지점은 PXE용으로 지원되지만 EFI 모드의 클라이언트 컴퓨터 네트워크 부팅은 지원하지 않습니다. 레거시 모드에서 EFI 부팅 또는 BIOS를 사용하는 클라이언트 컴퓨터는 지원됩니다.  

    -   배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  



## <a name="windows-10-x86-x64-pro-and-enterprise"></a>Windows 10(x86, x64): Pro 및 Enterprise  
**사이트 시스템 서버:**  

-   배포 지점  

    -   이 운영 체제의 배포 지점은 PXE용으로 지원되지 않습니다.  

    -   이 운영 체제의 배포 지점은 멀티캐스트를 지원하지 않습니다.  

    -   배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

## <a name="windows-81-x86-x64-professional-and-enterprise"></a>Windows 8.1(x86, x64): Professional 및 Enterprise  
**사이트 시스템 서버:**  

-   배포 지점  

    -   이 운영 체제의 배포 지점은 PXE용으로 지원되지 않습니다.  

    -   이 운영 체제의 배포 지점은 멀티캐스트를 지원하지 않습니다.  

    -   배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

## <a name="windows-8-x86-x64-professional-and-enterprise"></a>Windows 8(x86, x64): Professional 및 Enterprise
**사이트 시스템 서버:**  

-   배포 지점  

    -   이 운영 체제의 배포 지점은 PXE용으로 지원되지 않습니다.  

    -   이 운영 체제의 배포 지점은 멀티캐스트를 지원하지 않습니다.  

    -   배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

## <a name="windows-7-with-sp1-x86-x64-professional-enterprise-and-ultimate"></a>Windows 7 SP1(x86, x64): Professional, Enterprise 및 Ultimate  
**사이트 시스템 서버:**  

-   배포 지점  

    -   이 운영 체제의 배포 지점은 PXE용으로 지원되지 않습니다.  

    -   이 운영 체제의 배포 지점은 멀티캐스트를 지원하지 않습니다.  

    -   배포 지점은 각기 요구 사항이 다른 여러 구성을 지원합니다. 경우에 따라 이러한 구성은 서버뿐만 아니라 클라이언트 운영 체제에 대한 설치도 지원합니다. 배포 지점에 사용할 수 있는 옵션에 대한 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  


## <a name="the-server-core-installation-of-windows-server-2016"></a>Windows Server 2016의 Server Core 설치
KB3186654의 핫픽스 롤업이 포함된 1606 버전(또는 2016년 10월에 릴리스된 1606 기준 버전)부터 이 운영 체제를 배포 지점으로 사용할 수 있으며, 그럴 경우 다음과 같은 제한 사항이 적용됩니다.  
  -   x64비트 버전만 지원됩니다.
  -   이 운영 체제의 배포 지점은 PXE 또는 멀티캐스트를 지원하지 않습니다.  


## <a name="the-server-core-installation-of-windows-server-2012-r2"></a>Windows Server 2012 R2의 Server Core 설치  
 나열된 이전 운영 체제 외에도, Windows Server 2012 R2의 Server Core 설치를 다음과 같은 제한 사항이 있는 배포 지점으로 사용할 수도 있습니다.  

-   x64비트 버전만 지원됩니다.

-   이 운영 체제의 배포 지점은 PXE 또는 멀티캐스트를 지원하지 않습니다.  

## <a name="the-server-core-installation-of-windows-server-2012"></a>Windows Server 2012의 Server Core 설치  
 나열된 이전 운영 체제 외에도, Windows Server 2012의 Server Core 설치를 다음과 같은 제한 사항이 있는 배포 지점으로 사용할 수도 있습니다.  

-   64비트 버전만 지원됩니다.  

-   이 운영 체제의 배포 지점은 PXE 또는 멀티캐스트를 지원하지 않습니다.

