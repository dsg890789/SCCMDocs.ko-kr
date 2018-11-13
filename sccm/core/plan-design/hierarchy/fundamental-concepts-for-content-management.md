---
title: 콘텐츠 관리의 기본 사항
titleSuffix: Configuration Manager
description: Configuration Manager에서 도구와 옵션을 사용하여 배포하는 콘텐츠를 관리합니다.
ms.date: 10/26/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b73ead1492b143260d327f428db5a6183f84434c
ms.sourcegitcommit: 8791bb9be477fe6a029e8a7a76e2ca310acd92e0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50411343"
---
# <a name="fundamental-concepts-for-content-management-in-configuration-manager"></a>Configuration Manager에서 콘텐츠 관리의 기본 개념

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager는 소프트웨어 콘텐츠를 관리하는 도구 및 옵션의 강력한 시스템을 지원합니다. 응용 프로그램, 패키지, 소프트웨어 업데이트 및 OS 배포와 같은 소프트웨어 배포에는 모두 콘텐츠가 필요합니다. Configuration Manager는 사이트 서버와 배포 지점 모두에 콘텐츠를 저장합니다. 이 콘텐츠는 위치 간에 전송할 때는 네트워크 대역폭이 많이 필요합니다. 콘텐츠 관리 인프라를 효과적으로 계획하고 사용하기 위해서 먼저 사용 가능한 옵션 및 구성을 파악해야 합니다. 그런 다음, 네트워킹 환경 및 콘텐츠 배포 요구 사항에 가장 적합하게 사용하는 방법을 고려합니다.  

> [!TIP]    
> 콘텐츠 배포 프로세스에 대한 자세한 내용을 알아보고 일반적인 콘텐츠 배포 문제를 진단하고 해결하는 데 도움을 받으려면 [Microsoft Configuration Manager에서 콘텐츠 배포의 이해와 문제 해결](https://support.microsoft.com/help/4000401/content-distribution-in-mcm)을 참조하세요.

다음 토픽은 콘텐츠 관리를 위한 주요 개념입니다. 추가 정보나 복잡한 정보를 파악해야 하는 개념의 경우 해당하는 세부 정보를 확인할 수 있도록 링크가 제공됩니다.



## <a name="accounts-used-for-content-management"></a>콘텐츠 관리에 사용되는 계정  
 콘텐츠 관리에는 다음과 같은 계정을 사용할 수 있습니다.  

#### <a name="network-access-account"></a>네트워크 액세스 계정
클라이언트에서 배포 지점에 연결하고 콘텐츠에 액세스하는 데 사용하는 계정입니다. 기본적으로 컴퓨터 계정이 먼저 시도됩니다.  

풀(pull) 배포 지점이 원격 포리스트의 원본 배포 지점에서 콘텐츠를 다운로드할 때도 이 계정이 사용됩니다.  

버전 1806부터 일부 시나리오에서는 더 이상 액세스 계정이 필요하지 않습니다. 사이트에서 Azure Active Directory 인증으로 고급 HTTP를 사용하도록 설정할 수 있습니다.<!--1358228--> 

자세한 내용은 [네트워크 액세스 계정](/sccm/core/plan-design/hierarchy/accounts#network-access-account)을 참조하세요.

#### <a name="package-access-account"></a>패키지 액세스 계정
기본적으로 Configuration Manager는 일반 액세스 계정인 사용자 및 관리자에게 배포 지점의 콘텐츠에 대한 액세스 권한을 부여합니다. 그러나 추가 권한을 구성하여 액세스를 제한할 수 있습니다.   

자세한 내용은 [패키지 액세스 계정](/sccm/core/plan-design/hierarchy/accounts#package-access-account)을 참조하세요.



## <a name="bandwidth-throttling-and-scheduling"></a>대역폭 제한 및 예약  
 제한 및 예약은 사이트 서버에서 배포 지점으로 콘텐츠를 배포하는 시기를 제어하는 데 사용할 수 있는 옵션입니다. 이러한 기능은 사이트 간 파일 기반 복제용 대역폭 제어와 비슷하기는 하지만 직접적인 관련은 없습니다.  

 자세한 내용은 [네트워크 대역폭 관리](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)를 참조하세요.



## <a name="binary-differential-replication"></a>이진 차등 복제  
 BDR(이진 차등 복제)은 배포 지점에 대한 필수 구성 요소입니다. 이는 델타 복제라고도 합니다. 이전에 다른 사이트 또는 원격 배포 지점에 배포한 콘텐츠에 업데이트를 배포하는 경우 대역폭을 줄이는 데 자동으로 BDR이 사용됩니다.  

 BDR은 분산된 콘텐츠의 업데이트를 전송하는 데 사용되는 네트워크 대역폭을 최소화합니다. 해당 파일을 변경할 때마다 콘텐츠 원본 파일의 전체 집합을 전송하지 않고 새롭거나 변경된 콘텐츠만 다시 보냅니다.  

 BDR을 사용하는 경우 Configuration Manager는 이전에 배포한 각 콘텐츠 집합에 대한 원본 파일에서 변경된 부분을 식별합니다.  

-   원본 콘텐츠의 파일이 변경되면 해당 사이트는 콘텐츠의 새로운 증분 버전을 만듭니다. 그런 다음, 변경된 파일만 대상 사이트와 배포 지점으로 복제합니다. 파일의 이름이 변경되었거나 파일이 이동된 경우 또는 파일 콘텐츠가 변경된 경우 파일이 변경되었다고 간주됩니다. 예를 들어 이전에 여러 사이트에 배포한 드라이버 패키지에서 단일 드라이버 파일이 바뀐 경우 변경된 드라이버 파일만 복제됩니다.  

-   Configuration Manager는 전체 콘텐츠 집합을 다시 보내기 전에 콘텐츠 집합의 증분 버전을 5개까지 지원합니다. 5번째 업데이트 이후 콘텐츠 집합에 대해 다음 변경을 수행하면 사이트에서 콘텐츠 집합의 새로운 버전을 만듭니다. Configuration Manager에서는 새 콘텐츠 집합 버전을 배포하여 이전 집합과 모든 증분 버전을 바꿉니다. 새 콘텐츠 집합이 배포된 후에 원본 파일의 후속 증분 변경 내용은 BDR을 통해 다시 복제됩니다.  

BDR은 계층 내 각 부모 및 자식 사이트 간에 지원됩니다. 사이트 내에서는 사이트 서버와 해당 일반 배포 지점 간에 BDR이 지원됩니다. 단, 풀(pull) 배포 지점 및 클라우드 배포 지점은 콘텐츠를 전송하는 데 BDR을 지원하지 않습니다. 풀(pull) 배포 지점은 새 파일을 전송하는 파일 수준 델타를 지원하지만 파일 내 블록은 지원하지 않습니다.

응용 프로그램은 항상 이진 차등 복제를 사용합니다. BDR은 패키지에 대한 선택 사항이며 기본적으로 활성화되어 있지 않습니다. 패키지에서 BDR을 사용하려면 각 패키지에 대해 이 기능을 사용하도록 설정합니다. 패키지를 만들거나 편집할 때 **이진 차등 복제 사용** 옵션을 선택합니다.   



## <a name="branchcache"></a>BranchCache  
 [BranchCache](https://docs.microsoft.com/windows-server/networking/branchcache/branchcache)는 Windows 기술입니다. 클라이언트는 BranchCache를 지원하며 BranchCache용으로 구성된 배포를 다운로드한 클라이언트를 다른 BranchCache 사용 클라이언트에 대한 콘텐츠 원본으로 사용할 수 있도록 합니다.  

 예를 들어 Windows Server 2012 이상을 실행하는 배포 지점은 BranchCache 서버로 구성됩니다. 첫 번째 BranchCache 사용 클라이언트가 이 서버에서 콘텐츠를 요청하는 경우 클라이언트는 해당 콘텐츠를 다운로드하고 캐시합니다.  

- 그런 다음, 해당 클라이언트는 같은 서브넷에 있는 추가 BranchCache 사용 클라이언트에 대해 콘텐츠를 제공하며 이러한 클라이언트도 콘텐츠를 캐시합니다.  
- 동일한 서브넷에 있는 다른 클라이언트는 배포 지점에서 콘텐츠를 다운로드할 필요가 없습니다.  
- 콘텐츠는 이후 전송에서 여러 클라이언트에 배포됩니다.  

자세한 내용은 [Windows BranchCache에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#bkmk_branchcache)을 참조하세요.



## <a name="delivery-optimization"></a>배달 최적화
<!-- 1324696 --> Configuration Manager 경계 그룹을 사용하여 회사 네트워크 및 원격 사무실에 대한 콘텐츠 배포를 정의하고 규정합니다. [Windows 배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)는 Windows 10 장치 간에 콘텐츠를 공유하는 클라우드 기반의 피어 투 피어 기술입니다. 1802 버전부터 피어 간에 콘텐츠를 공유하는 경우 경계 그룹을 사용하도록 배달 최적화를 구성합니다. 클라이언트 설정은 경계 그룹 식별자를 클라이언트의 배달 최적화 그룹 식별자로 적용합니다. 클라이언트는 배달 최적화 클라우드 서비스와 통신할 때 이 식별자를 사용하여 원하는 콘텐츠가 있는 피어를 찾습니다. 자세한 내용은 [배달 최적화](/sccm/core/clients/deploy/about-client-settings#delivery-optimization) 클라이언트 설정을 참조하세요.

배달 최적화는 Windows 10 품질 업데이트용 빠른 설치 파일의 [Windows 10 업데이트 배달 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)에 권장되는 기술입니다.



## <a name="windows-ledbat"></a>Windows LEDBAT
<!--1358112--> Windows LEDBAT(Low Extra Delay Background Transport)는 백그라운드 네트워크 전송을 관리하는 데 유용한 Windows Server의 네트워크 정체 제어 기능입니다. 지원되는 Windows Server 버전에서 실행되는 배포 지점의 경우 네트워크 트래픽을 조정하는 데 유용한 옵션을 사용할 수 있습니다. 그런 다음, 클라이언트는 사용 가능한 경우에만 네트워크 대역폭을 사용합니다. 

전반적인 Windows LEDBAT에 대한 자세한 정보는 [새로운 전송 개선 사항](https://blogs.technet.microsoft.com/networking/2016/07/18/announcing-new-transport-advancements-in-the-anniversary-update-for-windows-10-and-windows-server-2016/) 블로그 게시물을 참조하세요.

Configuration Manager 배포 지점에 Windows LEDBAT를 사용하는 방법에 대한 자세한 내용은 [배포 지점의 일반 설정을 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-general)하는 경우 **사용하지 않는 네트워크 대역폭을 사용하도록 다운로드 속도 조정(Windows LEDBAT)** 에 대한 설정을 참조하세요.



## <a name="peer-cache"></a>피어 캐시
클라이언트 피어 캐시는 원격 위치의 클라이언트에 대한 콘텐츠 배포를 관리하는 데 도움이 됩니다. 피어 캐시는 클라이언트가 로컬 캐시의 콘텐츠를 다른 클라이언트와 직접 공유할 수 있도록 하는 기본 제공 Configuration Manager 솔루션입니다.

피어 캐시를 사용하도록 설정하는 클라이언트 설정을 먼저 컬렉션에 배포합니다. 그런 다음, 컬렉션의 멤버는 동일한 경계 그룹에 있는 다른 클라이언트에 대한 피어 콘텐츠 원본 역할을 합니다.

1806 버전부터 클라이언트 피어 캐시 원본은 콘텐츠를 여러 부분으로 나눌 수 있습니다. 이러한 부분은 네트워크 전송을 최소화하여 WAN 사용률을 줄입니다. 관리 지점은 콘텐츠 부분의 더 자세한 추적을 제공합니다. 경계 그룹별로 동일한 콘텐츠의 2회 이상 다운로드를 제거하려고 시도합니다.<!--1357346-->

자세한 내용은 [Configuration Manager 클라이언트용 피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)를 참조하세요.



## <a name="windows-pe-peer-cache"></a>Windows PE 피어 캐시
Configuration Manager로 새로운 OS를 배포하면 작업 순서를 실행하는 컴퓨터는 Windows PE 피어 캐시를 사용할 수 있습니다. 배포 지점에서 아닌 피어 캐시 원본에서 콘텐츠를 다운로드합니다. 이 동작은 로컬 배포 지점이 없는 지점 시나리오에서 WAN 트래픽을 최소화하는 데 유용합니다.

자세한 내용은 [Windows PE 피어 캐시](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic)를 참조하세요.



## <a name="client-locations"></a>클라이언트 위치  
 클라이언트가 콘텐츠에 액세스하는 위치는 다음과 같습니다.  

-   **인트라넷** (온-프레미스):  

    -   배포 지점은 HTTP 또는 HTTPS를 사용할 수 있습니다.  

    -   클라우드 배포 지점은 온-프레미스 배포 지점을 사용할 수 없는 경우의 대체 옵션으로만 사용합니다.  

-   **인터넷**:  

    -   인터넷 연결 배포 지점이 HTTPS를 허용해야 합니다.  

    -   클라우드 배포 지점을 사용할 수 있습니다.  

-   **작업 그룹**:  

    -   배포 지점이 HTTPS를 허용해야 합니다.  

    -   클라우드 배포 지점을 사용할 수 있습니다.  



## <a name="content-source-priority"></a>콘텐츠 원본 우선 순위

클라이언트에 콘텐츠가 필요한 경우 관리 지점에 콘텐츠 위치 요청을 수행합니다. 관리 지점은 요청된 콘텐츠에 대해 유효한 원본 위치의 목록을 반환합니다. 이 목록은 특정 시나리오, 사용되는 기술, 사이트 디자인, 경계 그룹 및 배포 설정에 따라 달라집니다. 다음 목록에는 우선 순위를 지정하는 순서로 클라이언트가 사용할 수 있는 가능한 모든 콘텐츠 원본 위치가 포함됩니다.  

1.  클라이언트와 동일한 컴퓨터에 있는 배포 지점
2.  동일한 네트워크 서브넷의 피어 원본
3.  동일한 네트워크 서브넷의 배포 지점
4.  동일한 경계 그룹의 피어 원본
5.  현재 경계 그룹의 배포 지점
6.  대체용으로 구성된 인접 경계 그룹의 배포 지점
9.  기본 사이트 경계 그룹의 배포 지점 
10. Windows 업데이트 클라우드 서비스
11. 인터넷 연결 배포 지점
12. Azure의 클라우드 배포 지점



## <a name="content-library"></a>콘텐츠 라이브러리  
 콘텐츠 라이브러리는 Configuration Manager에서 콘텐츠의 단일 인스턴스 저장소입니다. 이 라이브러리는 배포하는 콘텐츠의 전체 크기를 줄입니다.  

- [콘텐츠 라이브러리](/sccm/core/plan-design/hierarchy/the-content-library)에 대해 자세히 알아봅니다.
- [콘텐츠 라이브러리 정리 도구](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool)를 사용하여 더 이상 응용 프로그램과 연결되지 않는 콘텐츠를 제거합니다.  



## <a name="distribution-points"></a>배포 지점  
 Configuration Manager는 배포 지점을 사용하여 클라이언트 컴퓨터에서 소프트웨어를 실행하는 데 필요한 파일을 저장합니다. 클라이언트에는 배포하는 콘텐츠의 파일을 다운로드할 수 있는 배포 지점 하나 이상에 대한 액세스 권한이 있어야 합니다.  

 특수하지 않은 기본 배포 지점을 보통 표준 배포 지점이라고 합니다. 표준 배포 지점에는 특별히 주의해야 하는 두 가지 변형이 있습니다.  

-   **풀(pull) 배포 지점**: 배포 지점이 다른 배포 지점(원본 배포 지점)에서 콘텐츠를 가져오는 배포 지점의 변형입니다. 이 프로세스는 클라이언트가 배포 지점에서 콘텐츠를 다운로드하는 방법과 비슷합니다. 풀(pull) 배포 지점을 사용하면 사이트 서버가 각 배포 지점에 콘텐츠를 직접 배포해야 하는 경우 발생하는 네트워크 대역폭 병목 현상을 방지할 수 있습니다. [풀(pull) 배포 지점을 사용합니다](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **클라우드 기반 배포 지점**: Microsoft Azure에 설치된 배포 지점의 변형입니다. [클라우드 배포 지점을 사용하는 방법을 알아봅니다](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point).  


표준 배포 지점은 다양한 구성 및 기능을 지원합니다.  

- **일정** 또는 **대역폭 제한**과 같은 컨트롤을 사용하여 이 전송을 제어할 수 있습니다.  

- **사전 준비된 콘텐츠** 및 **풀(pull) 배포 지점**을 비롯한 다른 옵션을 사용하여 네트워크 사용을 최소화하고 제어할 수 있습니다.  

- **BranchCache**, **피어 캐시** 및 **배달 최적화**는 콘텐츠를 배포할 때 사용되는 네트워크 대역폭을 줄이는 피어 투 피어 기술입니다.  

- OS 배포의 경우 **[PXE](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_PXEDistributionPoint)** 및 **[멀티 캐스트](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_DPMulticast)** 와 같은 여러 구성이 있습니다.  

- **모바일 장치**에 대한 옵션   
  
클라우드 및 풀(pull) 배포 지점은 다수의 동일한 구성을 지원하지만 각 배포 지점 변형과 관련된 몇 가지 제한 사항이 있습니다.  



## <a name="distribution-point-groups"></a>배포 지점 그룹  
 배포 지점 그룹은 콘텐츠 배포를 간소화할 수 있는 배포 지점의 논리적 그룹입니다.  

 자세한 내용은 [배포 지점 그룹 관리](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_manage)를 참조하세요.



## <a name="distribution-point-priority"></a>배포 지점 우선 순위  
 배포 지점 우선 순위 값은 이전 배포를 해당 배포 지점으로 전송하는 데 걸린 시간을 기준으로 합니다.  

-   이 값은 자체 조정됩니다. Configuration Manager가 더 많은 배포 지점에 콘텐츠를 더 신속하게 전송할 수 있도록 각 배포 지점에서 설정됩니다.  

-   동시에 여러 배포 지점 또는 배포 지점 그룹에 콘텐츠를 배포하는 경우 사이트는 우선 순위가 가장 높은 서버에 먼저 콘텐츠를 보냅니다. 그런 다음, 우선 순위가 낮은 배포 지점으로 동일한 콘텐츠를 보냅니다.  

-   배포 지점의 우선 순위는 패키지에 대한 배포 우선 순위를 대체하지 않습니다. 패키지 우선 순위는 사이트가 다른 콘텐츠를 전송하는 시기를 결정하는 요소가 됩니다.  

예를 들어 패키지 우선 순위가 높은 패키지가 있습니다. 배포 지점 우선 순위가 낮은 서버에 배포하는 경우, 이 높은 우선 순위의 패키지는 항상 더 낮은 우선 순위의 패키지보다 먼저 전송됩니다. 패키지 우선 순위는 배포 지점 우선 순위가 더 높은 서버로 더 낮을 우선 순위 패키지를 배포하는 경우에도 적용됩니다.

패키지의 우선 순위가 높으면 Configuration Manager가 우선 순위가 낮은 패키지에 전송하기 전에 해당 콘텐츠를 배포 지점으로 배포하도록 합니다.  

> [!NOTE]  
>  또한 풀(pull) 배포 지점은 우선 순위 개념을 사용하여 원본 배포 지점의 순서를 결정합니다.  
>   
>  -   서버에 콘텐츠를 전송하기 위한 배포 지점 우선 순위는 풀(pull) 배포 지점에서 사용하는 우선 순위와는 구별됩니다. 풀(pull) 배포 지점은 원본 배포 지점의 콘텐츠를 검색할 때 해당 우선 순위를 사용합니다.  
>  -   자세한 내용은 [풀(pull) 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)을 참조하세요.  



## <a name="fallback"></a>대체  
 Configuration Manager 현재 분기에서는 대체(fallback)를 포함하여 콘텐츠가 있는 배포 지점을 클라이언트가 찾는 방법에서 몇 가지 사항이 변경되었습니다. 

현재 경계 그룹과 연결된 배포 지점에서 콘텐츠를 찾을 수 없는 클라이언트는 인접 경계 그룹과 연결된 콘텐츠 원본 위치를 사용하도록 대체(fallback)할 수 있습니다. 대체에 사용하려면 인접 경계 그룹에 클라이언트의 현재 경계 그룹과 정의된 관계가 있어야 합니다. 이 관계에는 로컬에서 콘텐츠를 찾을 수 없는 클라이언트가 인접 경계 그룹의 콘텐츠 원본을 검색의 일부로 포함할 수 있기 전에 경과해야 하는 구성된 시간이 포함됩니다.

기본 배포 지점의 개념은 더 이상 사용되지 않으며, **콘텐츠에 대한 대체 원본 위치 허용** 설정을 더 이상 사용하거나 적용할 수 없습니다.

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.



## <a name="network-bandwidth"></a>네트워크 대역폭  
 다음 옵션을 사용하면 콘텐츠를 배포할 때 사용되는 네트워크 대역폭의 양을 관리할 수 있습니다.  

-   **사전 준비된 콘텐츠**: 네트워크 전체에 콘텐츠를 배포하는 방식을 사용하는 대신 배포 지점에 콘텐츠를 전송합니다.  

-   **일정 및 제한**: 콘텐츠를 배포 지점으로 배포하는 시기와 방법을 제어하는 데 사용할 수 있는 구성입니다.  

자세한 내용은 [네트워크 대역폭 관리](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)를 참조하세요.



## <a name="network-connection-speed-to-content-source"></a>콘텐츠 원본에 대한 네트워크 연결 속도  
 Configuration Manager 현재 분기에서는 콘텐츠가 있는 배포 지점을 클라이언트가 찾는 방법에서 몇 가지 사항이 변경되었습니다. 이러한 변경에는 콘텐츠 원본에 대한 네트워크 속도가 포함됩니다. 

배포 지점을 **고속** 또는 **저속**으로 정의하는 네트워크 연결 속도는 더 이상 사용되지 않습니다. 대신 경계 그룹과 연결된 각 사이트 시스템이 동일하게 처리됩니다.

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.



## <a name="on-demand-content-distribution"></a>주문형 콘텐츠 배포  
 주문형 콘텐츠 배포는 개별 응용 프로그램 및 패키지 배포에 대한 옵션입니다. 이 옵션을 사용하면 기본 설정 서버로 주문형 콘텐츠 배포를 수행할 수 있습니다.  

-   배포에 이 설정을 사용하려면 **기본 배포 지점으로 이 패키지의 콘텐츠 배포**를 사용하도록 설정합니다.  

-   배포에 대해 이 옵션을 사용하도록 설정하고 클라이언트가 해당 콘텐츠를 요청하였으나 클라이언트의 기본 배포 지점에서 해당 콘텐츠를 사용할 수 없는 경우 Configuration Manager에서 클라이언트의 기본 배포 지점에 해당 콘텐츠를 자동으로 배포합니다.  

-   이때 Configuration Manager에서 클라이언트의 기본 배포 지점에 콘텐츠를 자동으로 배포하지만, 클라이언트의 기본 배포 지점이 배포를 받기 전에 클라이언트가 다른 배포 지점에서 해당 콘텐츠를 가져올 수도 있습니다. 이 동작이 발생하는 경우 콘텐츠는 해당 배포를 찾고 있는 다음 클라이언트가 사용할 수 있도록 해당 배포 지점에 표시됩니다.  

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.



## <a name="package-transfer-manager"></a>패키지 전송 관리자  
 패키지 전송 관리자는 다른 컴퓨터의 배포 지점에 콘텐츠를 전송하는 사이트 서버 구성 요소입니다.  

 자세한 내용은 [패키지 전송 관리자](/sccm/core/plan-design/hierarchy/package-transfer-manager)를 참조하세요.  



## <a name="prestage-content"></a>콘텐츠 사전 준비  
 사전 준비된 콘텐츠는 네트워크 전체에 콘텐츠를 배포하는 방식을 사용하는 대신 배포 지점에 콘텐츠를 전송하는 프로세스입니다.  

 자세한 내용은 [네트워크 대역폭 관리](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)를 참조하세요.
