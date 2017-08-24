---
title: "Windows 기능 지원 | Microsoft 문서"
description: "System Center Configuration Manager에서 지원하는 Windows 및 네트워킹 기능을 알아봅니다."
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: e040552dab21ba9a71e06a78f6acc2ffe1b0eb61
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>System Center Configuration Manager의 Windows 기능 및 네트워크 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 일반적인 Windows 및 네트워킹 기능에 대한 System Center Configuration Manager 지원을 식별합니다.  


##  <a name="bkmk_branchcache"></a> BranchCache  
배포 지점에서 BranchCache를 사용하도록 설정하고 분산 캐시 모드에서 BranchCache를 사용하도록 클라이언트를 구성하면 Configuration Manager에서 Windows BranchCache를 사용할 수 있습니다.

응용 프로그램의 배포 유형과 패키지 및 작업 순서 배포에 대해 BranchCache 설정을 구성할 수 있습니다.  

BranchCache에 대한 요구 사항이 충족되면 이 기능을 통해 원격 위치의 클라이언트가 콘텐츠의 현재 캐시가 있는 로컬 클라이언트에서 콘텐츠를 가져올 수 있습니다.  

예를 들어 첫 번째 BranchCache 사용 클라이언트 컴퓨터가 BranchCache 서버로 구성된 배포 지점에서 콘텐츠를 요청할 경우 이 클라이언트 컴퓨터는 콘텐츠를 다운로드하여 캐시합니다. 그런 다음 이 콘텐츠를 요청한 동일한 서브넷의 클라이언트에서 이 콘텐츠를 사용할 수 있습니다.

또한 이러한 클라이언트가 콘텐츠를 캐시합니다. 이러한 방식으로 인해 동일한 서브넷에 있는 후속 클라이언트는 배포 지점에서 콘텐츠를 다운로드하지 않아도 되며 콘텐츠가 여러 클라이언트에 배포되어 이후에 전송됩니다.  

**Configuration Manager에서 BranchCache를 지원하기 위한 요구 사항:**  
-   **배포 지점 구성:**  
    배포 지점으로 구성된 사이트 시스템 서버에 **Windows BranchCache** 기능을 추가합니다.    

    -   BranchCache를 지원하도록 구성된 서버의 배포 지점에서는 추가로 구성을 수행할 필요가 없습니다.   
    -   클라우드 기반 배포 지점에 Windows BranchCache를 추가할 수는 없지만 Windows BranchCache용으로 구성된 클라이언트는 클라우드 기반 배포 지점에서 콘텐츠를 다운로드할 수 있습니다.  

-   **클라이언트 구성:**    
    -   BranchCache를 지원할 수 있는 클라이언트를 BranchCache 분산 캐시 모드에 대해 구성해야 합니다.  
    -   BranchCache를 지원하려면 BITS 클라이언트 설정용 운영 체제 설정을 사용하도록 설정해야 합니다.   <br /> <br />
        
    BranchCache를 지원하도록 클라이언트를 구성하는 방법에 대한 자세한 내용은 [Windows 10 업데이트에 맞게 BranchCache 구성](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache)의 [클라이언트 구성](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache#configure-clients-for-branchcache) 섹션을 참조하세요.


**Configuration Manager는 다음 클라이언트 운영 체제에서 Windows BranchCache를 지원합니다.**  

|운영 체제|지원 세부 정보|  
|----------------------|---------------------|  
|Windows 7 SP1|기본적으로 지원됨|  
|Windows 8|기본적으로 지원됨|  
|Windows 8.1|기본적으로 지원됨|  
|Windows 10|기본적으로 지원됨|  
|Windows Server 2008 SP2|**BITS 4.0 필요**: 소프트웨어 업데이트 또는 소프트웨어 배포를 사용하여 Configuration Manager 클라이언트에 BITS 4.0 릴리스를 설치할 수 있습니다. BITS 4.0 릴리스에 대한 자세한 내용은 [Windows Management Framework](http://go.microsoft.com/fwlink/p/?LinkId=181979)항목을 참조하세요.<br /><br /> 이 운영 체제에서는 네트워크에서 실행되는 소프트웨어 배포 또는 SMB 파일 전송에 대해 BranchCache 클라이언트 기능이 지원되지 않습니다. 또한 이 운영 체제는 클라우드 기반 배포 지점에서 BranchCache 기능을 사용할 수 없습니다.|  
|Windows Server 2008 R2|기본적으로 지원됨|  
|Windows Server 2012|기본적으로 지원됨|  
|Windows Server 2012 R2|기본적으로 지원됨|  

 BranchCache에 대한 자세한 내용은 Windows Server 설명서에서 [Windows용 BranchCache](http://go.microsoft.com/fwlink/p/?LinkId=177945) 를 참조하세요.  

##  <a name="bkmk_Workgroups"></a> 작업 그룹의 컴퓨터  
Configuration Manager는 작업 그룹의 클라이언트를 지원합니다.  

-   Configuration Manager에서는 클라이언트를 작업 그룹에서 도메인으로 이동하거나 도메인에서 작업 그룹으로 이동할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) 항목에서 [작업 그룹 컴퓨터에 Configuration Manager 클라이언트를 설치하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup)을 참조하세요.  

> [!NOTE]  
>  작업 그룹의 클라이언트가 지원되기는 하지만 모든 사이트 시스템은 지원되는 Active Directory 도메인의 구성원이어야 합니다.  


##  <a name="bkmmk_datadedup"></a> 데이터 중복 제거  
Configuration Manager는 다음 운영 체제의 배포 지점에 대해 데이터 중복 제거를 사용할 수 있도록 지원합니다.  

-   Windows Server 2012  

-   Windows Server 2012 R2  

> [!IMPORTANT]  
>  패키지 원본 파일을 호스트하는 볼륨은 데이터 중복 제거용으로 표시할 수 없습니다. 데이터 중복 제거에서는 재분석 지점을 사용하는데, Configuration Manager에서 재분석 지점에 저장된 파일을 포함하는 콘텐츠 원본 위치를 사용할 수 없기 때문입니다.  

자세한 내용은 Configuration Manager 팀 블로그의 [Configuration Manager 배포 지점 및 Windows Server 2012 데이터 중복 제거 ](http://blogs.technet.com/b/configmgrteam/archive/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication.aspx)와 Windows Server TechNet 라이브러리의 [데이터 중복 제거 개요](http://technet.microsoft.com/library/hh831602.aspx)를 참조하세요.  

##  <a name="bkmk_DA"></a> DirectAccess  
Configuration Manager에서는 클라이언트와 사이트 시스템 서버 간 통신을 위해 Windows Server 2008 R2 이상의 DirectAccess 기능을 지원합니다.  

-   DirectAccess에 대한 요구 사항이 모두 충족되면 인터넷의 Configuration Manager 클라이언트가 DirectAccess를 사용하여 인트라넷에 있는 것처럼 할당된 사이트와 통신할 수 있습니다.  

-   원격 제어 및 클라이언트 강제 설치 등의 서버에서 시작하는 작업의 경우 작업을 시작하는 컴퓨터(예: 사이트 서버)는 IPv6을 실행해야 하며 해당 작업에 사용되는 모든 네트워킹 장치에서 이 프로토콜이 지원되어야 합니다.  

Configuration Manager에서는 DirectAccess를 통해 다음을 지원하지 않습니다.  

-   운영 체제 배포  

-   Configuration Manager 사이트 간의 통신  

-   사이트 내 Configuration Manager 사이트 시스템 서버 간의 통신  

##  <a name="bkmk_dualboot"></a> 이중 부팅 컴퓨터  
 Configuration Manager는 단일 컴퓨터에서 둘 이상의 운영 체제를 관리할 수 없습니다. 관리해야 하는 컴퓨터에 둘 이상의 운영 체제가 설치되어 있는 경우 관리해야 하는 운영 체제에만 Configuration Manager 클라이언트가 설치되도록 사용하는 검색 및 설치 방법을 조정합니다.  

##  <a name="bkmk_IPv6"></a> 인터넷 프로토콜 버전 6  
 Configuration Manager에서는 IPv4(인터넷 프로토콜 버전 4) 외에 IPv6(인터넷 프로토콜 버전 6)도 지원합니다.  

|기능| IPv6 지원에 대한 예외|  
|--------------|-------------------------------|  
|클라우드 기반 배포 지점|Microsoft Azure 및 클라우드 기반 배포 지점을 지원하려면 IPv4를 사용해야 합니다.|  
|Microsoft Intune 및 Microsoft 서비스 커넥터를 통해 등록된 모바일 장치|Microsoft Intune 및 Microsoft 서비스 커넥터를 통해 등록된 모바일 장치를 지원하려면 IPv4를 사용해야 합니다.|  
|네트워크 검색|DHCP 서버가 네트워크 검색에서 검색을 하도록 구성할 때는 IPv4를 사용해야 합니다.|  
|운영 체제 배포|운영 체제 배포를 지원하려면 IPv4를 사용해야 합니다.|  
|절전 모드 해제 프록시 통신|클라이언트 절전 모드 해제 프록시 패킷을 지원하려면 IPv4를 사용해야 합니다.|  
|Windows CE|Windows CE 장치에서 Configuration Manager 클라이언트를 지원하려면 IPv4를 사용해야 합니다.|  

##  <a name="bkmk_NAT"></a> Network Address Translation  
 사이트가 인터넷에 있는 클라이언트를 지원하며 클라이언트가 인터넷에 연결되어 있음을 검색하는 경우가 아니면 NAT(네트워크 주소 변환)는 Configuration Manager에서 지원되지 않습니다. 인터넷 기반 클라이언트 관리에 대한 자세한 내용은 [인터넷 기반 클라이언트 관리 계획](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md)을 참조하세요.  

##  <a name="bkmk_storage"></a> 특수 저장소 기술  
 Configuration Manager는 Configuration Manager 구성 요소가 설치된 운영 체제 버전에 대해 Windows 하드웨어 호환성 목록에 인증되어 있는 모든 하드웨어에서 작동합니다.

사이트 서버 역할을 사용하려면 디렉터리 및 파일 권한을 설정할 수 있도록 NTFS 파일 시스템이 필요합니다. Configuration Manager는 논리 드라이브에 대한 완전한 소유권을 가진다고 가정하므로 별도의 컴퓨터에서 실행되는 사이트 시스템은 저장소 기술의 논리 파티션을 공유할 수 없습니다. 그러나 각 컴퓨터는 공유 저장소 장치의 같은 실제 파티션에서 별도의 논리 파티션을 사용할 수 있습니다.  

 **지원 고려 사항:**  

-   **저장 영역 네트워크**: SAN(저장 영역 네트워크)은 SAN을 통해 호스트되는 볼륨에 지원되는 Windows 기반 서버가 직접 연결되어 있으면 지원됩니다.  

-   **단일 인스턴스 저장소**: Configuration Manager에서는 SIS(단일 인스턴스 저장소) 사용 볼륨에 배포 지점 패키지 및 서명 폴더를 구성할 수 없습니다.  

     또한 Configuration Manager 클라이언트의 캐시는 SIS 지원 볼륨에서 지원되지 않습니다.  

-   **이동식 디스크 드라이브**: Configuration Manager는 이동식 디스크 드라이브에 Configuration Manager 사이트 시스템 또는 클라이언트를 설치하도록 지원하지 않습니다.  
