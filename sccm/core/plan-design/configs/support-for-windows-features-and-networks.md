---
title: Windows 기능 지원
titleSuffix: Configuration Manager
description: Configuration Manager에서 지원하는 Windows 및 네트워킹 기능을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b2e5573ae4ec74db83dc895641af7b8fbc31a24
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "65499573"
---
# <a name="support-for-windows-features-and-networks-in-configuration-manager"></a>Configuration Manager의 Windows 기능 및 네트워크 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

이 아티클에서는 일반적인 Windows 및 네트워킹 기능에 대한 Configuration Manager 지원을 식별합니다.  



##  <a name="bkmk_branchcache"></a> BranchCache  

배포 지점에서 사용하도록 설정하는 경우 Configuration Manager와 함께 Windows BranchCache를 사용하고, 분산 캐시 모드에서 사용하도록 클라이언트를 구성합니다.

애플리케이션의 배포 유형과 패키지 및 작업 순서 배포에 대한 BranchCache 설정을 구성합니다. 버전 1802부터 BranchCache가 기본적으로 사용됩니다. 

BranchCache에 대한 요구 사항이 충족되면 이 기능을 통해 원격 위치의 클라이언트가 콘텐츠의 현재 캐시가 있는 로컬 클라이언트에서 콘텐츠를 가져올 수 있습니다.  

예를 들어 첫 번째 BranchCache 사용 클라이언트가 BranchCache 서버로 구성된 배포 지점에서 콘텐츠를 요청할 경우 이 클라이언트는 콘텐츠를 다운로드하여 캐시합니다. 그런 다음 이 콘텐츠를 요청한 동일한 서브넷의 클라이언트에서 이 콘텐츠를 사용할 수 있습니다.

또한 이러한 클라이언트가 콘텐츠를 캐시합니다. 동일한 서브넷에 있는 다른 클라이언트는 배포 지점에서 콘텐츠를 다운로드할 필요가 없습니다. 콘텐츠는 이후 전송에서 여러 클라이언트에 배포됩니다.  


### <a name="requirements-to-support-branchcache-with-configuration-manager"></a>Configuration Manager에서 BranchCache를 지원하기 위한 요구 사항

#### <a name="configure-distribution-points"></a>배포 지점 구성
배포 지점으로 구성된 사이트 시스템 서버에 **Windows BranchCache** 기능을 추가합니다.    
- BranchCache를 지원하도록 구성된 서버의 배포 지점에서는 추가로 구성을 수행할 필요가 없습니다.   
- 클라우드 기반 배포 지점에 Windows BranchCache를 추가할 수 없습니다. 클라우드 기반 배포 지점에서는 Windows BranchCache에 대해 구성된 콘텐츠를 클라이언트가 다운로드할 수 있도록 지원합니다.  

#### <a name="configure-clients"></a>클라이언트 구성    
- BranchCache를 지원할 수 있는 클라이언트를 BranchCache 분산 캐시 모드에 대해 구성해야 합니다.  
- BranchCache를 지원하려면 BITS 클라이언트 설정용 OS 설정을 사용하도록 설정해야 합니다.  

자세한 내용은 Windows 설명서의 [BranchCache의 클라이언트 구성](https://docs.microsoft.com/windows/deployment/update/waas-branchcache#configure-clients-for-branchcache)을 참조하세요.


### <a name="configuration-manager-supported-os-versions-with-windows-branchcache"></a>Windows BranchCache와 Configuration Manager 지원 OS 버전

|운영&nbsp;체제|지원 세부 정보|  
|----------------------|---------------------|  
|Windows 7 SP1|기본적으로 지원됨|  
|Windows 8|기본적으로 지원됨|  
|Windows 8.1|기본적으로 지원됨|  
|Windows 10|기본적으로 지원됨|  
|Windows Server 2008 SP2|**BITS 4.0 필요**: 소프트웨어 업데이트 또는 소프트웨어 배포를 사용하여 Configuration Manager 클라이언트에 BITS 4.0 릴리스를 설치합니다. 자세한 내용은 [Windows Management Framework](https://support.microsoft.com/help/968929/windows-management-framework-windows-powershell-2-0-winrm-2-0-and-bits)를 참조하세요.<br /><br /> 이 OS에서는 네트워크에서 실행되는 소프트웨어 배포 또는 SMB 파일 전송에 대해 BranchCache 클라이언트 기능이 지원되지 않습니다. 또한 이 OS는 클라우드 기반 배포 지점에서 BranchCache 기능을 사용할 수 없습니다.|  
|Windows Server 2008 R2|기본적으로 지원됨|  
|Windows Server 2012|기본적으로 지원됨|  
|Windows Server 2012 R2|기본적으로 지원됨|  
|Windows Server 2016|기본적으로 지원됨|  

자세한 내용은 Windows Server 설명서에서 [Windows의 BranchCache](https://docs.microsoft.com/windows-server/networking/branchcache/branchcache)를 참조하세요.  



##  <a name="bkmk_Workgroups"></a> 작업 그룹의 컴퓨터  

Configuration Manager는 작업 그룹의 클라이언트를 지원합니다.  

- Configuration Manager에서는 클라이언트를 작업 그룹에서 도메인으로 이동하거나 도메인에서 작업 그룹으로 이동할 수 있습니다. 자세한 내용은 [작업 그룹 컴퓨터에 Configuration Manager 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientWorkgroup)을 참조하세요.  

> [!NOTE]  
>  작업 그룹의 클라이언트가 지원되기는 하지만 모든 사이트 시스템은 지원되는 Active Directory 도메인의 구성원이어야 합니다.  



##  <a name="bkmmk_datadedup"></a> 데이터 중복 제거  

Configuration Manager는 다음 운영 체제의 배포 지점에 대해 데이터 중복 제거를 사용할 수 있도록 지원합니다.  

-   Windows Server 2016
-   Windows Server 2012 R2  
-   Windows Server 2012  


> [!IMPORTANT]  
>  패키지 원본 파일을 호스트하는 볼륨은 데이터 중복 제거용으로 표시할 수 없습니다. 데이터 중복 제거가 재분석 지점을 사용하기 때문에 제한합니다. Configuration Manager에서는 재분석 지점에 저장된 파일을 포함하는 콘텐츠 원본 위치를 사용하도록 지원하지 않습니다.  

자세한 내용은 Configuration Manager 팀 블로그의 [Configuration Manager 배포 지점 및 Windows Server 2012 데이터 중복 제거 ](https://cloudblogs.microsoft.com/enterprisemobility/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication/)와 Windows Server 설명서의 [데이터 중복 제거 개요](https://docs.microsoft.com/windows-server/storage/data-deduplication/overview)를 참조하세요.  



##  <a name="bkmk_DA"></a> DirectAccess  

Configuration Manager에서는 클라이언트와 사이트 시스템 서버 간 통신을 위해 DirectAccess 기능을 지원합니다.  

- DirectAccess에 대한 요구 사항이 모두 충족되면 인터넷의 Configuration Manager 클라이언트를 사용하여 인트라넷에 있는 것처럼 할당된 사이트와 통신할 수 있습니다.  

- 원격 제어 및 클라이언트 강제 설치 등의 서버 시작 작업의 경우 시작하는 컴퓨터는 IPv6을 실행 중이어야 합니다. 이 프로토콜은 모든 중간 네트워킹 디바이스에서 지원되어야 합니다.  

Configuration Manager에서는 DirectAccess를 통해 다음과 같은 기능을 지원하지 않습니다.  

-   OS 배포   

-   Configuration Manager 사이트 간의 통신  

-   사이트 내 Configuration Manager 사이트 시스템 서버 간의 통신  



##  <a name="bkmk_dualboot"></a> 이중 부팅 컴퓨터  

Configuration Manager는 단일 컴퓨터에서 둘 이상의 OS를 관리할 수 없습니다. 관리할 컴퓨터에 둘 이상의 OS가 설치되어 있는 경우 사이트의 검색 및 클라이언트 설치 메서드를 조정하여 관리되어야 하는 OS에만 Configuration Manager 클라이언트를 설치하도록 합니다.  



##  <a name="bkmk_IPv6"></a> IPv6  

Configuration Manager에서는 IPv4(인터넷 프로토콜 버전 4) 외에도, 다음과 같은 예외를 제외하고 IPv6(인터넷 프로토콜 버전 6)을 지원합니다.  

|기능| IPv6 지원에 대한 예외|  
|--------------|-------------------------------|  
|클라우드 기반 배포 지점|Microsoft Azure 및 클라우드 기반 배포 지점을 지원하려면 IPv4를 사용해야 합니다.|  
|클라우드 관리 게이트웨이|Microsoft Azure 및 클라우드 관리 게이트웨이를 지원하려면 IPv4를 사용해야 합니다.|  
|Microsoft Intune 및 Microsoft 서비스 커넥터를 통해 등록된 모바일 디바이스|Microsoft Intune 및 Microsoft 서비스 커넥터를 통해 등록된 모바일 디바이스를 지원하려면 IPv4를 사용해야 합니다.|  
|네트워크 검색|DHCP 서버가 네트워크 검색에서 검색을 하도록 구성할 때는 IPv4를 사용해야 합니다.|  
|OS 배포|1802 이하 버전에서는 OS 배포를 지원하려면 IPv4가 필요합니다.  </br> </br> 버전 1806부터 Windows 배포 서비스가 없는 배포 지점에서 PXE 응답기를 사용하도록 설정합니다. 이 새로운 PXE 응답기 서비스는 IPv6를 지원합니다. 작업 순서 중 고정 IP 주소 캡처 또는 설정과 같은 OS 배포 기능의 다른 측면에서는 IPv4가 계속 필요합니다. |  
|절전 모드 해제 프록시 통신|클라이언트 절전 모드 해제 프록시 패킷을 지원하려면 IPv4를 사용해야 합니다.|  
|Windows CE|Windows CE 디바이스에서 Configuration Manager 클라이언트를 지원하려면 IPv4를 사용해야 합니다.|  



##  <a name="bkmk_NAT"></a> Network Address Translation  

사이트가 인터넷에 있는 클라이언트를 지원하며 클라이언트가 인터넷에 연결되어 있음을 검색하는 경우가 아니면 NAT(네트워크 주소 변환)는 Configuration Manager에서 지원되지 않습니다. 인터넷 기반 클라이언트 관리에 대한 자세한 내용은 [인터넷 기반 클라이언트 관리 계획](/sccm/core/clients/deploy/plan/plan-for-managing-internet-based-clients)을 참조하세요.  



##  <a name="bkmk_storage"></a> 특수 스토리지 기술  

Configuration Manager는 Configuration Manager 구성 요소가 설치된 OS 버전에 대해 Windows 하드웨어 호환성 목록에 인증되어 있는 모든 하드웨어에서 작동합니다.

Configuration Manager가 디렉터리 및 파일 권한을 설정할 수 있도록 사이트 서버 역할에는 NTFS가 필요합니다. Configuration Manager에는 논리 드라이브의 완전한 소유권이 있다고 가정합니다. 별도 컴퓨터에서 실행되는 사이트 시스템은 스토리지 기술에 대한 논리 파티션을 공유할 수 없습니다. 그러나 각 컴퓨터는 공유 스토리지 디바이스의 같은 실제 파티션에서 별도의 논리 파티션을 사용할 수 있습니다.  

### <a name="support-considerations"></a>지원 고려 사항

- **SAN**: SAN(스토리지 영역 네트워크)은 SAN을 통해 호스트되는 볼륨에 지원되는 Windows 기반 서버가 직접 연결되어 있으면 지원됩니다.  

- **SIS**:  Configuration Manager에서는 SIS(단일 인스턴스 스토리지) 사용 볼륨에 배포 지점 패키지 및 서명 폴더를 구성할 수 없습니다.  

     또한 Configuration Manager 클라이언트의 캐시는 SIS 지원 볼륨에서 지원되지 않습니다.  

- **이동식 디스크 드라이브**: Configuration Manager는 이동식 디스크 드라이브에 Configuration Manager 사이트 시스템 또는 클라이언트를 설치하도록 지원하지 않습니다.  
