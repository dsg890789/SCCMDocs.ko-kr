---
title: "콘텐츠 관리의 기본 사항 | Microsoft 문서"
description: "System Center Configuration Manager에서 도구와 옵션을 사용하여 배포하는 콘텐츠를 관리합니다."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: 28
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: f73dde64e0e8a0fc49f45b3afb3b8f00c926a820
ms.contentlocale: ko-kr
ms.lasthandoff: 05/05/2017


---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 콘텐츠 관리의 기본 개념

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 응용 프로그램, 패키지, 소프트웨어 업데이트 및 운영 체제 배포로 배포하는 콘텐츠를 관리하기 위한 강력한 도구 및 옵션 시스템을 지원합니다.  

배포하는 콘텐츠는 사이트 서버와 배포 지점 사이트 시스템 서버 둘 다에 저장됩니다. 이 콘텐츠를 위치 간에 전송할 때는 네트워크 대역폭이 많이 필요할 수 있습니다. 콘텐츠 관리 인프라를 효율적으로 계획하고 사용하려면 사용 가능한 옵션 및 구성을 파악한 다음, 현재 사용 중인 네트워킹 환경과 콘텐츠 배포 요구에 가장 적합하게 사용하는 방법을 고려하는 것이 좋습니다.  

> [!TIP]    
> 콘텐츠 배포 프로세스에 대한 자세한 내용을 알아보고 일반적인 콘텐츠 배포 문제를 진단하고 해결하는 데 필요한 도움말을 찾을 수 있습니다. support.microsoft.com에서 [Understanding and Troubleshooting Content Distribution in Microsoft Configuration Manager](https://support.microsoft.com/help/4000401/content-distribution-in-mcm)(Microsoft Configuration Manager에서 콘텐츠 배포 이해 및 문제 해결)를 참조하세요.

다음은 콘텐츠 관리를 위한 주요 개념입니다. 추가 정보나 복잡한 정보를 파악해야 하는 개념의 경우 해당하는 세부 정보를 확인할 수 있도록 링크가 제공됩니다.

## <a name="accounts-used-for-content-management"></a>콘텐츠 관리에 사용되는 계정  
 콘텐츠 관리에는 다음과 같은 계정을 사용할 수 있습니다.  

-   **네트워크 액세스 계정**: 클라이언트에서 배포 지점에 연결하고 콘텐츠에 액세스하는 데 사용하는 계정입니다. 기본적으로 컴퓨터 계정이 먼저 시도됩니다.  

     풀(pull) 배포 지점이 원격 포리스트의 원본 배포 지점에서 콘텐츠를 가져올 때도 이 계정이 사용됩니다.  

-   **패키지 액세스 계정**: 기본적으로 Configuration Manager는 일반 액세스 계정인 사용자 및 관리자에 대해 배포 지점의 콘텐츠 액세스 권한을 부여합니다. 그러나 추가 권한을 구성하여 액세스를 제한할 수 있습니다.   

-   **멀티캐스트 연결 계정**: 운영 체제 배포에 사용되는 계정입니다.  

이러한 계정에 대한 자세한 내용은 [콘텐츠에 액세스하기 위한 계정 관리](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md)를 참조하세요.

## <a name="bandwidth-throttling-and-scheduling"></a>대역폭 제한 및 예약  
 제한 및 예약은 사이트 서버에서 배포 지점으로 콘텐츠를 배포하는 시기를 제어하는 데 사용할 수 있는 옵션입니다. 이러한 옵션은 사이트 간 파일 기반 복제용 대역폭 제어와 비슷하기는 하지만 직접적인 관련은 없습니다.  

 자세한 내용은 [네트워크 대역폭 관리](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)를 참조하세요.

## <a name="binary-differential-replication"></a>이진 차등 복제  
 배포 지점의 필수 조건이며 델타 복제라고도 하는 BDR(이진 차등 복제)은 이전에 다른 사이트 또는 원격 배포 지점에 배포한 콘텐츠에 대한 업데이트를 배포할 때 대역폭 사용량을 줄이기 위해 자동으로 사용됩니다.  

 BDR에서는 파일이 변경될 때마다 콘텐츠 원본 파일의 전체 집합을 전송하지 않고 새롭거나 변경된 콘텐츠만 다시 전송하므로, 배포된 콘텐츠의 업데이트를 전송하는 데 사용되는 네트워크 대역폭이 최소화됩니다.  

 이진 차등 복제를 사용하는 경우 Configuration Manager는 이전에 배포된 각 콘텐츠 집합의 원본 파일에서 변경된 부분을 식별합니다.  

-   원본 콘텐츠의 파일이 변경된 경우 Configuration Manager는 새 증분 버전의 콘텐츠 집합을 만들고 변경된 파일만 대상 사이트와 배포 지점에 복제합니다. 파일의 이름이 변경되었거나 파일이 이동된 경우 또는 파일 내용이 변경된 경우 파일이 변경되었다고 간주됩니다. 예를 들어 이전에 여러 사이트에 배포한 운영 체제 배포 패키지에서 단일 드라이버 파일이 바뀐 경우 변경된 드라이버 파일만 해당 대상 사이트에 복제됩니다.  

-   Configuration Manager는 전체 콘텐츠 집합을 다시 보내기 전에 콘텐츠 집합의 증분 버전을 5개까지 지원합니다. 5번째 업데이트 이후 콘텐츠 집합에 대해 다음 변경을 수행하면 Configuration Manager에서 새 콘텐츠 집합 버전을 만듭니다. Configuration Manager에서는 새 콘텐츠 집합 버전을 배포하여 이전 집합과 모든 증분 버전을 바꿉니다. 새 콘텐츠 집합이 배포된 후에 원본 파일의 후속 증분 변경 내용은 이진 차등 복제를 통해 다시 복제됩니다.  


BDR은 계층 내 각 부모 및 자식 사이트 간에 지원됩니다. 사이트 내에서는 사이트 서버와 해당 일반 배포 지점 간에 BDR이 지원됩니다. 단, 풀(pull) 배포 지점 및 클라우드 기반 배포 지점은 콘텐츠를 전송하는 데 이진 차등 복제를 지원하지 않습니다. 풀(pull) 배포 지점은 새 파일을 전송하는 파일 수준 델타를 지원하지만 파일 내 블록은 지원하지 않습니다.

응용 프로그램은 항상 이진 차등 복제를 사용합니다. 패키지의 경우 이진 차등 복제는 선택 사항이며 기본적으로 사용하도록 설정되어 있지 않습니다. 패키지에 대해 이진 차등 복제를 사용하려면 각 패키지에 대해 이 기능을 사용하도록 설정해야 합니다. 그러려면 새 패키지를 만드는 경우 또는 패키지 속성의 **데이터 원본** 탭을 편집하는 경우 **이진 차등 복제 사용** 옵션을 선택해야 합니다.  

## <a name="branchcache"></a>BranchCache  
 BranchCache는 BranchCache를 지원하며 BranchCache용으로 구성된 배포를 다운로드한 클라이언트를 다른 BranchCache 사용 클라이언트에 대한 콘텐츠 원본으로 사용할 수 있도록 하는 Windows 기술입니다.  

 예를 들어 Windows Server 2012를 실행하고 BranchCache 서버로 구성된 배포 지점에서 콘텐츠를 요청하는 첫 번째 BranchCache 사용 클라이언트 컴퓨터는 해당 콘텐츠를 다운로드하여 캐시합니다.  

-   해당 클라이언트 컴퓨터는 같은 서브넷에 있는 추가 BranchCache 사용 클라이언트에 대해 콘텐츠를 제공하며 이러한 클라이언트도 콘텐츠를 캐시합니다.  

-   이렇게 해서 동일한 서브넷에 있는 후속 클라이언트가 배포 지점에서 콘텐츠를 다운로드하지 않아도 되며 콘텐츠가 여러 클라이언트에 배포되어 이후에 전송됩니다.  

## <a name="peer-cache"></a>피어 캐시
버전 1610부터 클라이언트 피어 캐시는 원격 위치의 클라이언트에 대한 콘텐츠 배포를 관리하는 데 도움이 됩니다. 피어 캐시는 클라이언트가 로컬 캐시의 콘텐츠를 다른 클라이언트와 직접 공유할 수 있도록 하는 기본 제공 Configuration Manager 솔루션입니다.

피어 캐시를 사용하도록 설정된 클라이언트 설정을 컬렉션에 배포하고 나면 해당 컬렉션의 멤버가 동일 경계 그룹에서 다른 클라이언트의 피어 콘텐츠 원본 역할을 할 수 있습니다.

자세한 내용은 [Configuration Manager 클라이언트에 대한 피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)를 참조하세요.


## <a name="windows-pe-peer-cache"></a>Windows PE 피어 캐시
System Center Configuration Manager에서 새 운영 체제를 배포할 때 작업 순서를 실행하는 컴퓨터가 배포 지점에서 콘텐츠를 다운로드하는 대신 Windows PE 피어 캐시를 사용하여 로컬 피어(피어 캐시 원본)에서 콘텐츠를 가져올 수 있습니다. 따라서 로컬 배포 지점이 없는 지점 시나리오에서 WAN(광역 네트워크) 트래픽을 최소화할 수 있습니다.

자세한 내용은 [Windows PE 피어 캐시](../../../osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md)를 참조하세요.


## <a name="client-locations"></a>클라이언트 위치  
 클라이언트가 콘텐츠에 액세스하는 위치는 다음과 같습니다.  

-   **인트라넷** (온-프레미스):  

    -   배포 지점은 HTTP 또는 HTTPS를 사용할 수 있습니다.  

    -   클라우드 기반 배포 지점은 온-프레미스 배포 지점을 사용할 수 없는 경우의 대체 옵션으로만 사용합니다.  

-   **인터넷**:  

    -   배포 지점이 HTTPS를 허용해야 합니다.  

    -   대체 옵션으로 클라우드 기반 배포 지점을 사용할 수 있습니다.  

-   **작업 그룹**:  

    -   배포 지점이 HTTPS를 허용해야 합니다.  

    -   대체 옵션으로 클라우드 기반 배포 지점을 사용할 수 있습니다.  



## <a name="content-library"></a>콘텐츠 라이브러리  
 콘텐츠 라이브러리는 배포하는 콘텐츠의 결합된 본문 전체 크기를 줄이기 위해 Configuration Manager에서 사용하는 콘텐츠의 단일 인스턴스 저장소입니다.  

- [콘텐츠 라이브러리](../../../core/plan-design/hierarchy/the-content-library.md)에 대해 자세히 알아봅니다.
- [콘텐츠 라이브러리 정리 도구](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool)를 사용하여 더 이상 응용 프로그램과 연결되지 않는 콘텐츠를 제거합니다.  


## <a name="distribution-points"></a>배포 지점  
 Configuration Manager는 배포 지점을 사용하여 클라이언트 컴퓨터에서 소프트웨어를 실행하는 데 필요한 파일을 저장합니다. 클라이언트에는 배포하는 콘텐츠의 파일을 다운로드할 수 있는 배포 지점 하나 이상에 대한 액세스 권한이 있어야 합니다.  

 특수하지 않은 기본 배포 지점을 보통 표준 배포 지점이라고 합니다. 표준 배포 지점에는 특별히 주의해야 하는 두 가지 변형이 있습니다.  

-   **풀(pull) 배포 지점**: 배포 지점이 다른 배포 지점(원본 배포 지점)에서 콘텐츠를 가져오는 배포 지점의 변형입니다. 이 프로세스는 클라이언트가 배포 지점에서 콘텐츠를 다운로드하는 방법과 비슷합니다. 풀(pull) 배포 지점을 사용하면 사이트 서버가 각 배포 지점에 콘텐츠를 직접 배포해야 하는 경우 발생하는 네트워크 대역폭 병목 현상을 방지할 수 있습니다.  [System Center Configuration Manager에서 풀 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **클라우드 기반 배포 지점**: Microsoft Azure에 설치되는 배포 지점의 한 변형입니다. [System Center Configuration Manager에서 클라우드 기반 배포 지점을 사용하는 방법을 알아봅니다](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


표준 배포 지점은 제한 및 예약, PXE 및 멀티캐스트 또는 사전 준비된 콘텐츠와 같은 다양한 구성 및 기능을 지원합니다.  

-   **일정** 또는 **대역폭 제한**과 같은 컨트롤을 사용하여 이 전송을 제어할 수 있습니다.  

-   **사전 준비된 콘텐츠** 및 **풀(pull) 배포 지점**을 포함하여 다른 옵션을 사용할 수도 있습니다. 또한 **BranchCache**를 활용하여 콘텐츠를 배포할 때 사용되는 네트워크 대역폭을 줄일 수 있습니다.  

-   배포 지점에서는 운영 체제 배포를 위한 **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)** 및 **[멀티캐스트](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)** 같은 다양한 구성 또는 **모바일 장치**를 위한 구성을 지원합니다.  

 클라우드 기반 배포 지점과 풀(pull) 배포 지점은 다수의 동일한 구성을 지원하지만 각 배포 지점 변형과 관련된 몇 가지 제한 사항이 있습니다.  

## <a name="distribution-point-groups"></a>배포 지점 그룹  
 배포 지점 그룹은 콘텐츠 배포를 간소화할 수 있는 배포 지점의 논리적 그룹입니다.  

 자세한 내용은 [배포 지점 그룹 관리](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage)를 참조하세요.

## <a name="distribution-point-priority"></a>배포 지점 우선 순위  
 배포 지점 우선 순위 값은 이전 배포를 해당 배포 지점으로 전송하는 데 걸린 시간을 기준으로 합니다.  

-   이 값은 배포 지점에 할당되는 자체 조정 값이며, Configuration Manager에서 콘텐츠를 더 많은 배포 지점에 전송하는 시간을 단축하는 데 도움이 됩니다.  

-   동시에 여러 배포 지점에 콘텐츠를 배포하거나 단일 배포 지점 그룹에 배포하는 경우 Configuration Manager는 우선 순위가 가장 높은 배포 지점에 콘텐츠를 전송한 후 그 다음으로 낮은 우선 순위의 배포 지점에 동일한 콘텐츠를 전송합니다.  

-   이 우선 순위는 여러 배포가 전송될 때 전송 순서를 결정하는 요소로 계속 사용되는 패키지의 배포 우선 순위 대신 사용되지 않습니다.  


예를 들어 높은 배포 우선 순위의 콘텐츠를 낮은 배포 지점 우선 순위의 배포 지점에 배포하는 경우 이 높은 배포 우선 순위의 패키지가 항상 더 낮은 배포 우선 순위의 패키지보다 먼저 전송됩니다. 이는 더 낮은 배포 우선 순위의 패키지가 더 높은 배포 지점 우선 순위의 배포 지점에 배포되는 경우에도 적용됩니다.

패키지의 배포 우선 순위가 높으면 Configuration Manager가 해당 패키지의 콘텐츠를 적용되는 배포 지점에 먼저 배포하고, 그 다음으로 더 낮은 배포 우선 순위의 패키지가 전송됩니다.  

> [!NOTE]  
>  또한 풀(pull) 배포 지점은 우선 순위 개념을 사용하여 원본 배포 지점의 순서를 결정합니다.  
>   
>  -   콘텐츠를 배포 지점에 전송하는 배포 지점 우선 순위는 풀(pull) 배포 지점이 원본 배포 지점에서 콘텐츠를 검색할 때 사용하는 우선 순위와 다릅니다.  
>  -   자세한 내용은 [System Center Configuration Manager에서 풀 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)을 참조하세요.  


## <a name="fallback"></a>대체  
 버전 1610부터 클라이언트에서 대체(fallback)를 포함하여 콘텐츠가 있는 배포 지점을 검색하는 방법의 몇 가지 사항이 변경되었습니다. 사용하는 버전에 적용되는 다음 정보를 사용하세요.

**버전 1610 이상:**   
현재 경계 그룹과 연결된 배포 지점에서 콘텐츠를 찾을 수 없는 클라이언트는 인접 경계 그룹과 연결된 콘텐츠 원본 위치를 사용하도록 대체(fallback)할 수 있습니다. 대체에 사용하려면 인접 경계 그룹에 클라이언트의 현재 경계 그룹과 정의된 관계가 있어야 합니다. 이 관계에는 로컬에서 콘텐츠를 찾을 수 없는 클라이언트가 인접 경계 그룹의 콘텐츠 원본을 검색의 일부로 포함할 수 있기 전에 경과해야 하는 구성된 시간이 포함됩니다.

기본 배포 지점의 개념은 더 이상 사용되지 않으며, **콘텐츠에 대한 대체 원본 위치 허용** 설정을 더 이상 사용하거나 적용할 수 없습니다.

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.


**버전 1511, 1602 및 1606**   
대체 설정은 **기본 배포 지점** 사용 및 클라이언트에서 사용되는 콘텐츠 원본 위치와 관련된 설정입니다.

-   기본적으로 클라이언트는 기본 배포 지점, 즉 클라이언트 경계 그룹에 연결된 배포 지점에서만 콘텐츠를 다운로드합니다.  

-   그러나 **클라이언트가 콘텐츠에 대한 대체 원본 위치로 이 사이트 시스템을 사용하도록 허용**을 사용하여 배포 지점을 구성한 경우에는 기본 배포 지점 중 하나에서 배포를 가져올 수 없는 클라이언트에 대해서만 유효한 콘텐츠 원본으로 해당 배포 지점을 제공할 수 있습니다.  


다양한 콘텐츠 위치 및 대체 시나리오에 대한 자세한 내용은 [콘텐츠 원본 위치 시나리오](../../../core/plan-design/hierarchy/content-source-location-scenarios.md)를 참조하세요. 경계 그룹에 대한 자세한 내용은 [버전 1511,1602 및 1606에 대한 경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606)을 참조하세요.

## <a name="network-bandwidth"></a>네트워크 대역폭  
 다음 옵션을 사용하면 콘텐츠를 배포할 때 사용되는 네트워크 대역폭의 양을 관리할 수 있습니다.  

-   **사전 준비된 콘텐츠**: Configuration Manager를 사용하여 네트워크 전체에 콘텐츠를 배포하지 않고 배포 지점에 콘텐츠를 전송하는 프로세스입니다.  

-   **일정 및 제한**: 콘텐츠를 배포 지점으로 배포하는 시기와 방법을 제어하는 데 사용할 수 있는 구성입니다.  

자세한 내용은 [네트워크 대역폭 관리](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)를 참조하세요.

## <a name="network-connection-speed-to-content-source"></a>콘텐츠 원본에 대한 네트워크 연결 속도  
버전 1610부터 클라이언트에서 콘텐츠 원본에 대한 네트워크 연결 속도를 포함하여 콘텐츠가 있는 배포 지점을 검색하는 방법의 몇 가지 사항이 변경되었습니다. 사용하는 버전에 적용되는 다음 정보를 사용하세요.

**버전 1610 이상:**   
배포 지점을 **고속** 또는 **저속**으로 정의하는 네트워크 연결 속도는 더 이상 사용되지 않습니다. 대신 경계 그룹과 연결된 각 사이트 시스템이 동일하게 처리됩니다.

자세한 내용은 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.


**버전 1511, 1602 및 1606**   
 경계 그룹에서 각 배포 지점의 네트워크 연결 속도를 구성할 수 있습니다.  

-   클라이언트에서 배포 지점에 연결할 때 이 값을 사용합니다.

-   네트워크 연결 속도는 기본적으로 **고속**으로 구성되어 있지만 **저속**으로 설정할 수도 있습니다.  

-   **네트워크 연결 속도** 및 배포 구성에 따라 연결된 경계 그룹에 있는 클라이언트가 배포 지점에서 콘텐츠를 다운로드할 수 있는지 여부가 결정됩니다.  

다양한 콘텐츠 위치 및 대체 시나리오에 대한 자세한 내용은 [콘텐츠 원본 위치 시나리오](../../../core/plan-design/hierarchy/content-source-location-scenarios.md)를 참조하세요. 경계 그룹에 대한 자세한 내용은 [버전 1511,1602 및 1606에 대한 경계 그룹](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606)을 참조하세요.

## <a name="on-demand-content-distribution"></a>주문형 콘텐츠 배포  
 주문형 콘텐츠 배포는 기본 배포 지점에 대한 주문형 콘텐츠 배포를 사용할 수 있도록 개별 응용 프로그램 및 패키지(배포)에 대해 설정할 수 있는 옵션입니다.  

-   배포에 이 옵션을 사용하려면 **기본 배포 지점으로 이 패키지의 콘텐츠 배포**를 사용하도록 설정합니다.  

-   배포에 대해 이 옵션을 사용하도록 설정한 경우 클라이언트가 해당 콘텐츠 요청을 시도할 때 클라이언트의 기본 배포 지점에서 해당 콘텐츠를 사용할 수 없으면 Configuration Manager에서 클라이언트의 기본 배포 지점에 해당 콘텐츠를 자동으로 배포합니다.  

-   이때 Configuration Manager에서 클라이언트의 기본 배포 지점에 콘텐츠를 자동으로 배포하지만, 클라이언트의 기본 배포 지점이 배포를 받기 전에 클라이언트가 다른 배포 지점에서 해당 콘텐츠를 가져올 수도 있습니다. 이 경우 콘텐츠는 해당 배포를 찾고 있는 다음 클라이언트가 사용할 수 있도록 해당 배포 지점에 표시됩니다.  

버전 1610 이상을 사용하는 경우 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.
버전 1511, 1602 또는 1606을 사용하는 경우 다양한 콘텐츠 위치 및 대체 시나리오에 대한 자세한 내용은 [콘텐츠 원본 위치 시나리오](../../../core/plan-design/hierarchy/content-source-location-scenarios.md)를 참조하세요.  



## <a name="package-transfer-manager"></a>패키지 전송 관리자  
 패키지 전송 관리자는 다른 컴퓨터의 배포 지점에 콘텐츠를 전송하는 사이트 서버 구성 요소입니다.  

 [패키지 전송 관리자](../../../core/plan-design/hierarchy/package-transfer-manager.md)에 대해 자세히 알아봅니다.  

## <a name="preferred-distribution-point"></a>기본 배포 지점  
 기본 배포 지점에는 클라이언트의 현재 경계 그룹에 연결된 배포 지점이 포함됩니다.  

 각 배포 지점을 하나 이상의 경계 그룹과 연결할 수 있습니다.  

-   이렇게 연결하면 클라이언트가 콘텐츠를 다운로드할 수 있는 배포 지점을 식별할 수 있습니다.  
-   기본적으로 클라이언트는 기본 배포 지점의 콘텐츠만 다운로드할 수 있습니다.  


자세한 내용을 보려면 다음을 수행하십시오.
 - 버전 1610 이상을 사용하는 경우 [경계 그룹](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups)을 참조하세요.
 - 버전 1511, 1602 또는 1606을 사용하는 경우 [콘텐츠 원본 위치 시나리오](../../../core/plan-design/hierarchy/content-source-location-scenarios.md)를 참조하세요.

## <a name="prestage-content"></a>콘텐츠 사전 준비  
 콘텐츠 사전 준비는 Configuration Manager를 사용하여 네트워크 전체에 콘텐츠를 배포하지 않고 배포 지점에 콘텐츠를 전송하는 프로세스입니다.  

 자세한 내용은 [네트워크 대역폭 관리](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)를 참조하세요.

