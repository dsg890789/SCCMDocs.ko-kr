---
title: Azure의 Configuration Manager
description: Azure 환경에서 Configuration Manager를 사용하는 방법에 대한 정보입니다.
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d24257d8-8136-47f4-8e0d-34021356dc37
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2b952e76fc21e3190430cdf34cb4a264918fd199
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32342599"
---
# <a name="configuration-manager-on-azure---frequently-asked-questions"></a>Azure의 Configuration Manager - 질문과 대답
*적용 대상: System Center Configuration Manager(현재 분기)*

다음 질문과 대답을 사용하여 Microsoft Azure에서 Configuration Manager를 사용하는 시기와 구성 방법을 이해할 수 있습니다.

## <a name="general-questions"></a>일반적인 질문
### <a name="my-company-is-trying-to-move-as-many-physical-servers-as-possible-to-microsoft-azure-can-i-move-configuration-manager-servers-to-azure"></a>회사에서 가능한 한 많은 물리적 서버를 Microsoft Azure로 이동하려고 합니다. Configuration Manager 서버를 Azure로 이동할 수 있나요?
물론입니다. 지원되는 시나리오입니다.  [System Center Configuration Manager에 대한 가상화 환경 지원](/sccm/core/plan-design/configs/support-for-virtualization-environments)을 참조하세요.

### <a name="great-my-environment-requires-multiple-sites-should-all-child-primary-sites-be-in-azure-with-the-central-administration-site-or-on-premises-what-about-secondary-sites"></a>좋습니다! 현재 환경에 여러 사이트가 필요합니다. 모든 하위 기본 사이트가 중앙 관리 사이트 또는 온-프레미스가 있는 Azure에 있어야 하나요? 보조 사이트의 경우는 어떤가요?
사이트 간 통신(파일 기반 및 데이터베이스 복제)은 Azure에 호스트 중인 근접 연결에 유용합니다. 그러나 트래픽과 관련된 모든 클라이언트는 사이트 서버 및 사이트 시스템의 원격 클라이언트가 됩니다. 무제한 데이터 요금제를 사용하고 Azure와 인트라넷 간에 빠르고 안정적인 네트워크 연결을 사용하는 경우 Azure의 모든 인프라를 호스트할 수 있습니다.

그러나 데이터 요금제를 사용하고 대역폭 또는 비용이 제한된 경우 또는 Azure와 인트라넷 간의 네트워크 연결이 빠르지 않거나 불안정한 경우, 특정 사이트(및 사이트 시스템)를 온-프레미스에 배치하고 Configuration Manager에서 기본으로 제공하는 대역폭 제어 기능을 사용하는 것이 좋습니다.

### <a name="is-having-configuration-manager-in-azure-a-saas-scenario-software-as-a-service"></a>Azure의 Configuration Manager에 SaaS(Software as a Service) 시나리오가 있나요?
아니요, Azure 가상 컴퓨터에서 Configuration Manager 인프라 서버를 호스트하기 때문에 IaaS(서비스 제공 인프라) 시나리오를 사용합니다.

### <a name="what-areas-should-i-pay-attention-to-when-considering-a-move-of-my-configuration-manager-infrastructure-to-azure"></a>Configuration Manager 인프라를 Azure로 이동할 때 주의해야 할 점은 무엇인가요?
좋은 질문입니다. 이 작업을 수행할 때 가장 중요한 점은 다음과 같으며 각각 이 항목의 별도의 섹션에서 설명합니다.
1.  네트워킹
2.  가용성
3.  성능
4.  비용
5.  사용자 환경

## <a name="networking"></a>네트워킹
### <a name="what-about-networking-requirements-should-i-use-expressroute-or-an-azure-vpn-gateway"></a>네트워킹 요구 사항은 무엇인가요? ExpressRoute 또는 Azure VPN Gateway를 사용해야 하나요?
네트워킹은 매우 중요한 결정 사항입니다. 네트워크 속도 및 대기 시간은 사이트 서버와 원격 사이트 시스템 간, 그리고 사이트 시스템에 대한 모든 클라이언트 통신 기능에 영향을 줄 수 있습니다. 가장 권장되는 방법은 ExpressRoute를 사용하는 것입니다. 하지만 Configuration Manager에서 Azure VPN Gateway 사용을 제한하는 것은 아닙니다. 이 인프라를 통해 요구 사항(성능, 패치, 소프트웨어 배포, 운영 체제 배포)을 신중하게 검토한 다음 결정해야 합니다. 각 솔루션에 대해 고려해야 할 사항은 다음과 같습니다.

 - **ExpressRoute**(권장)
  - 데이터 센터로 자연스러운 확장(여러 데이터 센터를 함께 연결할 수 있음)
  - Azure 데이터 센터와 인프라 간의 개인 연결
  - 공용 인터넷 사용 안 함
  - 안정성, 빠른 속도, 낮은 대기 시간, 높은 보안성 제공
  - 최대 10gbps 속도 및 무제한 데이터 요금제 옵션 제공
 - **VPN Gateway**
  - 사이트-사이트/지점-사이트 VPN
  - 공용 인터넷을 통한 트래픽
  - IPsec(인터넷 프로토콜 보안) 및 IKE(Internet Key Exchange) 사용

### <a name="expressroute-has-many-different-options-like-unlimited-vs-metered-different-speed-options-and-premium-add-on-which-should-i-choose"></a>ExpressRoute에는 무제한/데이터 요금제, 다양한 속도 옵션 및 프리미엄 추가 기능 등의 옵션을 제공합니다. 어떤 옵션을 선택해야 하나요?
선택할 옵션은 구현 중인 시나리오와 배포하려는 데이터의 양에 따라 달라집니다. Configuration Manager는 사이트 서버와 배포 지점 간의 데이터 전송은 제어할 수 있지만 사이트 서버 간의 통신은 제어할 수 없습니다.   데이터 요금제를 사용하는 경우 특정 사이트(및 사이트 시스템)를 온-프레미스에 배치하고 [Configuration Manager의 기본 대역폭 제어](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) 기능을 사용하면 Azure 사용 비용을 제어할 수 있습니다.

### <a name="what-about-installation-requirements-like-active-directory-domains-do-i-still-need-to-join-my-site-servers-to-an-active-directory-domain"></a>Active Directory 도메인 등의 설치 요구 사항은 어떤가요? 여전히 내 사이트 서버가 Active Directory 도메인에 가입되어야 하나요?
예. Azure로 이동할 때 Configuration Manager 설치를 위한 Active Directory 요구 사항 등 [지원되는 구성](/sccm/core/plan-design/configs/supported-configurations)은 동일합니다.

### <a name="i-understand-the-need-to-join-my-site-servers-to-an-active-directory-domain-but-can-i-use-azure-active-directory"></a>사이트 서버가 Active Directory 도메인에 가입되어야 하는 것은 알겠는데 Azure Active Directory를 사용할 수 있나요?
아니요, Azure Active Directory는 현재 지원되지 않습니다. 사이트 서버는 [Windows Active Directory 도메인](/sccm/core/plan-design/configs/support-for-active-directory-domains)의 구성원이어야 합니다.



## <a name="availability"></a>가용성
### <a name="one-of-the-reasons-i-am-moving-infrastructure-to-azure-is-the-promise-of-high-availability-can-i-take-advantage-of-high-availability-options-like-azure-vm-availability-sets-for-vms-that-i-will-use-for-configuration-manager"></a>인프라를 Azure로 이동하는 이유 중 하나는 고가용성입니다. Configuration Manager에 사용할 VM을 위해 Azure VM 가용성 집합과 같은 고가용성 옵션을 사용할 수 있나요?
예. Azure VM 가용성 집합을 배포 지점 또는 관리 지점 등의 중복 사이트 시스템 역할에 사용할 수 있습니다.

Configuration Manager 사이트 서버에도 사용할 수 있습니다. 예를 들어 중앙 관리 사이트 및 기본 사이트의 가용성 집합은 동일하므로 동시에 다시 부팅되지 않습니다.

### <a name="how-can-i-make-my-database-highly-available-can-i-use-azure-sql-database-or-do-i-have-to-use-microsoft-sql-server-in-a-vm"></a>데이터베이스의 가용성을 높이려면 어떻게 해야 하나요? Azure SQL Database를 사용할 수 있나요? 아니면 VM에서 Microsoft SQL Server를 사용해야 하나요?
VM에서 Microsoft SQL Server를 사용해야 합니다. Configuration Manager는 현재 Azure SQL Server를 지원하지 않습니다. 그러나 AlwaysOn 가용성 그룹 등의 기능을 SQL Server에 사용할 수 있습니다. [AlwaysOn 가용성 그룹](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)은 권장 사항이며 Configuration Manager 버전 1602에서 공식적으로 지원됩니다.

### <a name="can-i-use-azure-load-balancers-with-site-system-roles-like-management-points--or-software-update-points"></a>Azure 부하 분산 장치를 관리 지점 또는 소프트웨어 업데이트 지점과 같은 사이트 시스템 역할과 함께 사용할 수 있나요?
Configuration Manager는 Azure 부하 분산 장치에서 테스트되지 않았지만 기능이 애플리케이션에 투명한 경우 정상적인 작동에 부정적인 영향을 주지 않아야 합니다.


## <a name="performance"></a>성능
### <a name="what-factors-affect-performance-in-this-scenario"></a>이 시나리오에서 성능에 영향을 주는 요소는 무엇인가요?
[Azure VM 크기 및 형식](https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs), Azure VM 디스크(Premium Storage 권장, 특히 SQL Server의 경우), 네트워킹 대기 시간 및 속도가 가장 중요한 요인입니다.

### <a name="so-tell-me-more-about-azure-virtual-machines-what-size-vms-should-i-use"></a>그럼 Azure Virtual Machines에 대해 자세히 알고 싶습니다. 어떤 크기의 VM을 사용해야 하나요?
일반적으로 컴퓨터 성능(CPU 및 메모리)은 [System Center Configuration Manager의 하드웨어 권장 사항](/sccm/core/plan-design/configs/recommended-hardware)을 만족해야 합니다. 그러나 일반적인 컴퓨터 하드웨어와 Azure VM 간에는 약간의 차이가 있습니다. 특히 이러한 VM이 사용하는 디스크가 다릅니다.  사용할 VM의 크기는 해당 환경의 크기에 따라 달라지지만 다음 권장 사항을 참조할 수 있습니다.
- 대용량 크기의 프로덕션 배포의 경우 “**S**” 클래스 Azure VM을 권장합니다. 이는 Premium Storage 디스크를 이용할 수 있기 때문입니다.  “S” 클래스가 아닌 VM은 Blob Storage를 사용하는데 이 저장소는 일반적으로 수용 가능한 프로덕션 환경의 성능 요구 사항을 만족하지 않습니다.
- 확장성을 향상시키려면 여러 개의 Premium Storage 디스크를 사용해야 합니다. 최대 IOPS를 위해서는 Windows 디스크 관리 콘솔에서 스트라이프해야 합니다.  
- 초기 사이트 배포 중 더 나은 또는 여러 개의 프리미엄 디스크를 사용하는 것이 좋습니다(예: P20보다 P30, 1xP30보다 스트라이프 볼륨의 2xP30). 그런 다음 나중에 추가 로드로 인해 VM 크기를 확장해야 할 경우 더 큰 VM 크기가 제공하는 추가 CPU 및 메모리를 사용할 수 있습니다. 또한 이미 배치된 디스크가 더 큰 VM 크기에서 허용하는 추가 IOPS 처리량을 사용하게 될 수 있습니다.



다음 표에는 다양한 크기의 설치를 위해 기본 및 중앙 관리 사이트를 활용하는 데 권장되는 초기 디스크 수가 나열되어 있습니다.

**같은 위치에 배치된 사이트 데이터베이스** - 사이트 서버에 사이트 데이터베이스와 함께 기본 또는 중앙 관리 사이트 배치:

| 데스크톱 클라이언트    |권장 VM 크기|권장 디스크|
|--------------------|-------------------|-----------------|
|**최대 25,000**       |   DS4_V2          |2xP30(스트라이프)  |
|**25,000 - 50,000**      |   DS13_V2         |2xP30(스트라이프)  |
|**50,000 - 100,000**     |   DS14_V2         |3xP30(스트라이프)  |


**원격 사이트 데이터베이스** - 원격 서버에 사이트 데이터베이스와 함께 기본 또는 중앙 관리 사이트 배치:

| 데스크톱 클라이언트    |권장 VM 크기|권장 디스크 |
|--------------------|-------------------|------------------|
|**최대 25,000**       | 사이트 서버: F4S </br>데이터베이스 서버: DS12_V2 | 사이트 서버: 1xP30 </br>데이터베이스 서버: 2xP30(스트라이프)  |
|**25,000 - 50,000**      | 사이트 서버: F4S </br>데이터베이스 서버: DS13_V2 | 사이트 서버: 1xP30 </br>데이터베이스 서버: 2xP30(스트라이프)   |
|**50,000 - 100,000**     | 사이트 서버: F8S </br>데이터베이스 서버: DS14_V2 | 사이트 서버: 2xP30(스트라이프)   </br>데이터베이스 서버: 3xP30(스트라이프)   |

다음은 Configuration Manager 설치 및 데이터베이스 파일에 대한 별도의 논리적 볼륨이 있고, 스트라이프 볼륨에 3xP30개 디스크가 포함된 DS14_V2의 50,000-100,000개 클라이언트에 대한 예제 구성입니다. ![VM) 디스크](media/vm_disks.png)  



## <a name="user-experience"></a>사용자 환경
### <a name="you-mention-that-user-experience-is-one-of-the-main-areas-of-importance-why-is-that"></a>사용자 환경이 중요한 요소 중 하나인 이유는 무엇인가요?
네트워킹, 가용성, 성능 및 Configuration Manager 사이트 서버를 배치할 위치에 대한 결정은 사용자에게 직접 영향을 줄 수 있습니다. Azure로의 이동은 일상적인 Configuration Manager 작업에 영향을 주지 않도록 사용자에게 투명해야 합니다.

### <a name="ok-i-get-it-i-plan-to-install-a-single-stand-alone-primary-site-on-an-azure-virtual-machine-and-i-want-to-make-sure-my-costs-are-low-should-i-place-remote-site-systems-like-management-points-distribution-points-and-software-update-points-on-azure-virtual-machines-as-well-or-on-premises"></a>예, 알겠습니다. 단일 독립 실행형 기본 사이트를 Azure 가상 머신에 설치하여 비용을 절약하려고 합니다. 관리 지점, 배포 지점 및 소프트웨어 업데이트 지점 등의 (원격) 사이트 시스템을 온-프레미스뿐 아니라 Azure 가상 컴퓨터에 배치해야 하나요?
사이트 서버에서 배포 지점으로 향하는 통신을 제외하고, 이러한 사이트 내 서버 간 통신은 언제든지 발생할 수 있으며 네트워크 대역폭 사용을 제어하는 메커니즘을 사용하지 않습니다. 사이트 시스템 간의 통신을 제어할 수 없으므로 이러한 통신과 관련된 모든 비용을 고려해야 합니다.

네트워크 속도 및 대기 시간도 고려해야 할 요인입니다. 네트워크 속도가 느리거나 불안정하면 사이트 서버와 원격 사이트 시스템 간의 통신, 그리고 사이트 시스템에 대한 모든 클라이언트 통신 기능에 영향을 줄 수 있습니다. 특정 사이트 시스템을 사용하는 관리 클라이언트 수와 자주 사용하는 기능도 고려해야 합니다.
일반적으로 WAN 링크로 연결되고 사이트 시스템을 시작점으로 사용하는 일반 지침을 사용할 수 있습니다. 이상적으로는 Azure와 인트라넷 간에 선택하고 수신하는 네트워크 처리량은 고속 네트워크로 연결된 WAN과 동일합니다.

### <a name="what-about-content-distribution-and-content-management-should-standard-distribution-points-be-in-azure-or-on-premises-and-should-i-use-branchcache-or-pull-distribution-points-on-premises-or-should-i-make-exclusive-use-of-cloud-distribution-points"></a>콘텐츠 배포 및 콘텐츠 관리란 무엇인가요? 표준 배포 지점은 Azure 또는 온-프레미스에 있어야 하고 BranchCache 또는 전체 배포 지점 온-프레미스를 사용해야 하나요? 아니면 클라우드 배포 지점을 단독으로 사용해야 하나요?
콘텐츠 관리를 위한 방법은 사이트 서버 및 사이트 시스템의 경우와 거의 동일합니다.
- 무제한 데이터 요금제를 사용하고 Azure와 인트라넷 간에 빠르고 안정적인 네트워크 연결을 사용하는 경우 Azure의 표준 배포 지점을 호스트할 수 있습니다.
-  데이터 요금제를 사용하고 대역폭 비용이 제한되거나 Azure와 인트라넷 간의 네트워크 연결이 느리거나 불안정한 경우 다른 방법을 생각해 볼 수 있습니다. BranchCache를 사용하거나 표준 또는 풀(pull) 배포 지점을 온-프레미스에 배치하는 방법을 고려할 수 있습니다. 클라우드 기반의 배포 지점 사용을 선택할 수 있지만 지원되는 콘텐츠 형식이 약간 제한됩니다. 예를 들어 소프트웨어 업데이트 패키지가 지원되지 않습니다.

> [!NOTE]
>  PXE 지원이 필요한 경우 온-프레미스 배포 지점(표준 또는 풀(pull))을 사용하여 부팅 요청에 응답해야 합니다. [WDS는 현재 Azure VM에서의 실행이 지원되지 않습니다](https://technet.microsoft.com/library/hh831764(v=ws.11).aspx).


### <a name="while-i-am-ok-with-the-limitations-of-cloud-based-distribution-points-i-dont-want-to-put-my-management-point-into-a-dmz-even-though-that-is-needed-to-support-my-internet-based-clients-do-i-have-any-other-options"></a>클라우드 기반 배포 지점의 제한은 괜찮지만 내 인터넷 기반 클라이언트 지원에 필요하더라도 관리 지점을 DMZ에 배치하고 싶지 않습니다. 다른 방법은 없나요?
예. Configuration Manager 버전 1610과 함께 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway)를 시험판 기능으로 도입했습니다. (이 기능은 Technical Preview 버전 1606에 [클라우드 프록시 서비스](/sccm/core/get-started/capabilities-in-technical-preview-1606#a-namecloudproxyacloud-proxy-service-for-managing-clients-on-the-internet)로 처음 표시되었습니다).

**클라우드 관리 게이트웨이**는 인터넷에서 Configuration Manager 클라이언트를 관리할 수 있는 간단한 방법을 제공합니다. Microsoft Azure에 배포되고 Azure 구독이 필요한 서비스는 클라우드 관리 게이트웨이 연결점이라는 새 역할을 사용하여 온-프레미스 Configuration Manager 인프라에 연결합니다. 배포 및 구성된 클라이언트는 내부 개인 네트워크 또는 인터넷에 연결되었는지 여부에 관계없이 온-프레미스 Configuration Manager 사이트 시스템 역할에 액세스할 수 있습니다.

사용자의 환경에서 클라우드 관리 게이트웨이를 사용한 다음 제품 개선을 위해 이에 대한 피드백을 제출할 수 있습니다. 시험판 기능에 대한 자세한 내용은 [업데이트에서 시험판 기능 사용](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkprereleasea-use-pre-release-features-from-updates)을 참조하세요.

### <a name="i-also-heard-that-you-have-another-new-feature-called-peer-cache-introduced-as-a-pre-release-feature-in-version-1610-is-that-different-than-branchcache-which-one-should-i-choose"></a>버전 1610의 시험판 기능으로 추가된 피어 캐시라는 또 다른 새로운 기능이 있다고 들었습니다. BranchCache와 다른가요? 어떤 것을 선택해야 하나요?
예, 전혀 다릅니다. [피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)는 Configuration Manager의 기본 기술이지만 BranchCache는 Windows 기능입니다. 두 가지 모두 유용합니다. BranchCache는 브로드캐스트를 사용하여 필요한 콘텐츠를 찾는 반면, 피어 캐시는 Configuration Managers 일반 배포 워크플로 및 경계 그룹 설정을 사용합니다.

모든 클라이언트는 피어 캐시 원본으로 구성할 수 있습니다. 그런 다음 관리 지점에서 콘텐츠 원본 위치에 대한 클라이언트 정보를 제공할 때 해당 클라이언트에 필요한 콘텐츠가 있는 모든 피어 캐시 원본 및 배포 지점에 대한 세부 정보를 제공합니다.


## <a name="cost"></a>비용
### <a name="ok-tell-me-a-bit-about-the-cost-will-this-be-a-cost-effective-solution-for-me"></a>비용에 대해 알고 싶어요. 이 방법이 비용 효율적인 솔루션인가요?
환경마다 다르기 때문에 단언하기 어렵습니다. 가장 좋은 방법은 Microsoft Azure 가격 계산기를 사용하여 환경의 비용을 계산해 보는 것입니다: https://azure.microsoft.com/pricing/calculator/

## <a name="additional-resources"></a>추가 리소스
**기본 항목:** http://azure.microsoft.com/documentation/articles/fundamentals-introduction-to-azure/

**Azure VM 컴퓨터 유형:**
 - 가상 머신 크기: https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs/  
 - VM 가격 책정: http://azure.microsoft.com/pricing/details/virtual-machines/  
 - 저장소 가격 책정: http://azure.microsoft.com/pricing/details/storage/

**디스크 성능 고려 사항:**    
 - 프리미엄 디스크 소개: http://azure.microsoft.com/blog/2014/12/11/introducing-premium-storage-high-performance-storage-for-azure-virtual-machine-workloads/  
 - 자세한 프리미엄 디스크 정보: http://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/   
 - 저장소용 최대 크기 및 성능 대상에 대한 차트의 간편한 컬렉션: https://azure.microsoft.com/documentation/articles/storage-scalability-targets/  
 - Premium Storage에 대한 기타 소개 및 원리에 대한 유용한 데이터: http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2/

**가용성:**
 - Azure IaaS 작동 시간 SLA: https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/  
 - 가용성 집합 설명: https://azure.microsoft.com/documentation/articles/virtual-machines-manage-availability/

**연결:**
 - Express 경로 및 Azure VPN: http://azure.microsoft.com/blog/2014/06/10/expressroute-or-virtual-network-vpn-whats-right-for-me/
 - Express 경로 가격 책정: http://azure.microsoft.com/pricing/details/expressroute/
 - Express 경로에 대해 자세히: http://azure.microsoft.com/documentation/articles/expressroute-introduction/

 
