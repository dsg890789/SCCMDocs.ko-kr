---
title: Windows 10 업데이트 배달 최적화
titleSuffix: Configuration Manager
description: Configuration Manager로 업데이트 콘텐츠를 관리하여 Windows 10으로 최신 상태를 유지하는 방법을 알아봅니다.
ms.date: 12/17/2019
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: b670cfaf-96a4-4fcb-9caa-0f2e8c2c6198
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 1c6a2c20685703e9d47016b8e5ba914438064b28
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827352"
---
# <a name="optimize-windows-10-update-delivery-with-configuration-manager"></a>Configuration Manager로 Windows 10 업데이트 배달 최적화

*적용 대상: Configuration Manager(현재 분기)*

많은 고객이 Windows 10 월별 업데이트로 최신 상태를 유지하는 성공적인 방법은 Configuration Manager를 사용하는 뛰어난 콘텐츠 배포 전략에서 시작됩니다. 대규모 조직의 경우 월별 품질 업데이트의 크기가 문제가 될 수 있습니다. 업데이트 배달을 최적화하는 데 필요한 대역폭 및 네트워크 부하를 줄이는 데 도움이 되는 몇 가지 기술을 사용할 수 있습니다. 이 문서에서는 이러한 기술에 대해 설명하고, 이러한 기술을 비교하며, 사용할 기술을 결정하는 데 도움이 되는 권장 사항을 제공합니다.  
 
Windows 10은 여러 가지 형식의 업데이트를 제공합니다. 자세한 내용은 [비즈니스용 Windows 업데이트의 업데이트 형식](/windows/deployment/update/waas-manage-updates-wufb#types-of-updates-managed-by-windows-update-for-business)을 참조하세요. 이 문서에서는 Configuration Manager를 사용하는 Windows 10 *품질* 업데이트를 중점적으로 다룹니다. 


## <a name="express-update-delivery"></a>Express 업데이트 배달

Windows 10 품질 업데이트 다운로드는 매우 클 수 있습니다. 일관성 및 간소화를 보장하기 위해 이전에 릴리스된 모든 수정 사항이 모든 패키지에 포함됩니다. Microsoft는 각 클라이언트가 Express라는 기능으로 다운로드하는 Windows 10 업데이트 콘텐츠의 크기를 줄일 수 있습니다. 오늘날 Express는 Windows 업데이트 서비스에서 직접 업데이트를 가져오는 수백만 개의 디바이스에서 사용되며 다운로드 크기를 현저하게 줄입니다. 이 혜택은 클라이언트가 Windows 업데이트 서비스에서 직접 다운로드하지 않는 고객도 이용할 수 있습니다. 

Configuration Manager는 버전 1702에서 Windows 10 품질 업데이트의 [빠른 설치 파일](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)에 대한 지원을 추가했습니다. 그러나 최상의 환경을 위해서는 Configuration Manager 버전 1802 이상을 사용하는 것이 좋습니다. 또한 최상의 다운로드 속도 성능을 위해서는 Windows 10 버전 1703 이상을 사용하는 것이 좋습니다. 

> [!NOTE]  
> Express 버전 콘텐츠는 전체 파일 버전보다 훨씬 더 큽니다. 빠른 설치 파일에는 업데이트하려는 각 파일에 가능한 모든 변형이 포함되어 있습니다. 따라서 Configuration Manager에서 빠른 지원을 사용하도록 설정하면 업데이트 패키지 원본 및 배포 지점에서 업데이트에 필요한 디스크 공간의 크기가 증가합니다. 배포 지점의 디스크 공간 요구 사항이 증가하더라도 이러한 배포 지점에서 클라이언트가 다운로드하는 콘텐츠 크기는 감소합니다. 클라이언트는 전체 업데이트가 아니라 필요한 비트(델타)만 다운로드합니다.


## <a name="peer-to-peer-content-distribution"></a>피어 투 피어 콘텐츠 배포

클라이언트에서 필요한 콘텐츠의 일부만 다운로드하더라도 피어 투 피어 콘텐츠 배포를 활용하면 사용자 환경에서 Windows 업데이트가 빠르게 진행됩니다. 피어를 품질 업데이트의 다운로드 원본으로 활용하면 로컬 배포 지점이 원격 사무실에 없는 환경에 도움이 될 수 있습니다. 이 동작은 모든 클라이언트가 느린 WAN 링크를 통해 원격 배포 지점에서 콘텐츠를 다운로드할 필요가 없도록 합니다. 또한 피어를 사용하면 클라이언트가 Windows 업데이트 서비스로 대체되는 경우에도 도움이 됩니다. 다른 디바이스에서 사용할 수 있도록 하기 전에 클라우드에서 업데이트 콘텐츠를 다운로드하는 데는 하나의 피어만 필요합니다.

Configuration Manager는 다음을 포함하여 많은 피어 투 피어 기술을 지원합니다.
- Windows 배달 최적화
- Configuration Manager 피어 캐시
- Windows BranchCache  

다음 섹션에서는 이러한 기술에 대한 추가 정보를 제공합니다.

### <a name="windows-delivery-optimization"></a>Windows 배달 최적화

[배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization)는 Windows 10에 기본 제공되는 주요 다운로드 기술 및 피어 투 피어 배포 방법입니다. Windows 10 클라이언트는 동일한 업데이트를 다운로드하는 로컬 네트워크의 다른 디바이스에서 콘텐츠를 가져올 수 있습니다. [배달 최적화에 사용 가능한 Windows 옵션](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#delivery-optimization-options)을 사용하여 클라이언트를 그룹으로 구성할 수 있습니다. 이 그룹화를 통해 조직은 피어 투 피어 요청을 수행하는 최상의 후보가 될 수 있는 디바이스를 식별할 수 있습니다. 배달 최적화를 사용하면 다운로드 시간을 단축하는 동시에 디바이스를 최신 상태로 유지하는 데 사용되는 전체 대역폭을 현저하게 줄일 수 있습니다.

> [!NOTE]  
> 배달 최적화는 클라우드 관리 솔루션입니다. 피어 투 피어 기능을 활용하려면 배달 최적화 클라우드 서비스에 대한 인터넷 액세스가 필요합니다. 필요한 인터넷 엔드포인트에 대한 자세한 내용은 [배달 최적화에 대한 질문과 대답](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#frequently-asked-questions)을 참조하세요. 

최상의 결과를 얻으려면 배달 최적화 [다운로드 모드](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#download-mode)를 **그룹(2)** 로 설정하고 *그룹 ID*를 정의해야 합니다. 그룹 모드에서 피어링은 원격 사무실의 디바이스를 포함하여 동일한 그룹에 속한 디바이스 간 내부 서브넷을 교차할 수 있습니다. [그룹 ID 옵션](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference#select-the-source-of-group-ids)을 사용하여 도메인 및 AD DS 사이트와 별개로 공유한 사용자 지정 그룹을 만듭니다. 그룹 다운로드 모드는 배달 최적화를 사용하여 최상의 대역폭 최적화를 달성하려는 대부분의 조직에 권장되는 옵션입니다.

클라이언트가 여러 네트워크에서 로밍되는 경우에는 이러한 그룹 ID를 수동으로 구성하기가 어렵습니다. Configuration Manager 버전 1802에서는 [경계 그룹을 배달 최적화와 통합](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization)하여 이 프로세스의 관리를 간소화하는 새 기능을 추가했습니다. 클라이언트가 절전 모드에서 해제되면 관리 지점과 통신하여 정책을 가져오고 네트워크 및 경계 그룹 정보를 제공합니다. Configuration Manager는 모든 경계 그룹에 대해 고유한 ID를 만듭니다. 사이트에서는 클라이언트의 위치 정보를 사용하여 Configuration Manager 경계 ID로 클라이언트의 배달 최적화 그룹 ID를 자동으로 구성합니다. 클라이언트가 다른 경계 그룹으로 로밍되면 해당 관리 지점과 통신하고 새 경계 그룹 ID로 자동으로 다시 구성됩니다. 이 통합을 통해 배달 최적화는 Configuration Manager 경계 그룹 정보를 활용하여 업데이트를 다운로드할 피어를 찾을 수 있습니다.

### <a name="bkmk_DO-1910"></a> 배달 최적화(버전 1910부터)
<!--4699118-->
Configuration Manager 버전 1910부터 빠른 설치 파일만이 아닌 Windows 10 버전 1709 이상을 실행 하는 클라이언트에 대해 모든 Windows 업데이트 콘텐츠를 배포 하기 위해 배달 최적화를 사용할 수 있습니다.

모든 Windows 업데이트 설치 파일에 대 한 배달 최적화를 사용 하려면 다음 [소프트웨어 업데이트 클라이언트 설정을](/sccm/core/clients/deploy/about-client-settings#software-updates)사용 하도록 설정 합니다.

- **클라이언트가 사용 가능한 경우 델타 콘텐츠를 다운할 수 있도록 허용**을 **예**로 설정합니다.
- **델타 콘텐츠에 대한 요청을 받기 위해 클라이언트가 사용하는 포트**를 8005(기본값) 또는 사용자 지정 포트 번호로 설정합니다.

> [!IMPORTANT]
> - 배달 최적화를 사용하도록 설정(기본값)하고 무시하지 않아야 합니다. 자세한 내용은 [Windows 제공 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization-reference)를 참조하세요.
> - 델타 콘텐츠에 대 한 [소프트웨어 업데이트 클라이언트 설정을](/sccm/core/clients/deploy/about-client-settings#software-updates) 변경할 때 [배달 최적화 클라이언트 설정을](/sccm/core/clients/deploy/about-client-settings#delivery-optimization) 확인 합니다.



### <a name="configuration-manager-peer-cache"></a>Configuration Manager 피어 캐시

[피어 캐시](/sccm/core/plan-design/hierarchy/client-peer-cache)는 클라이언트가 로컬 Configuration Manager 캐시에서 직접 다른 클라이언트와 콘텐츠를 공유할 수 있도록 하는 Configuration Manager의 기능입니다. 피어 캐시는 Windows BranchCache와 같은 다른 피어 캐싱 솔루션의 사용을 대체하지 않습니다. 피어 캐시는 다른 솔루션과 함께 작동하여 배포 지점과 같은 기존의 콘텐츠 배포 솔루션을 확장하기 위한 옵션을 더 많이 제공합니다. 피어 캐시는 BranchCache를 사용하지 않습니다. BranchCache를 사용하도록 설정하거나 사용하지 않는 경우에도 피어 캐시는 계속 작동합니다.

> [!NOTE]  
> 클라이언트는 현재 경계 그룹에 있는 피어 캐시 클라이언트의 콘텐츠만 다운로드할 수 있습니다.  


### <a name="windows-branchcache"></a>Windows BranchCache
[BranchCache](https://docs.microsoft.com/windows-server/networking/branchcache/branchcache)는 Windows의 대역폭 최적화 기술입니다. 각 클라이언트에는 캐시가 있으며 콘텐츠의 대체 원본 역할을 합니다. 동일한 네트워크에 있는 디바이스에서 이 콘텐츠를 요청할 수 있습니다. [Configuration Manager는 BranchCache를 사용](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#bkmk_branchcache)하여 피어가 서로의 원본 콘텐츠를 허용하도록 하고 항상 배포 지점을 연결하도록 할 수 있습니다. BranchCache를 사용하면 파일이 각 개별 클라이언트에서 캐시되며 다른 클라이언트에서 필요에 따라 검색할 수 있습니다. 이 방법은 단일 검색 지점을 사용하지 않고 캐시를 배포합니다. 이 동작은 상당한 양의 대역폭을 절약하는 동시에 클라이언트가 요청한 콘텐츠를 수신하는 시간을 단축합니다.



## <a name="selecting-the-right-peer-caching-technology"></a>적합한 피어 캐싱 기술 선택

빠른 설치 파일에 적합한 피어 캐싱 기술 선택은 환경 및 요구 사항에 따라 달라집니다. Configuration Manager에서 위의 모든 피어 투 피어 기술을 지원하는 경우에도 사용자 환경에 가장 적합한 기술을 사용해야 합니다. 클라이언트가 배달 최적화를 위한 인터넷 요구 사항을 충족한다고 가정할 경우, 대부분의 고객에게는 배달 최적화를 사용하는 Windows 10의 기본 제공 피어 캐싱이면 충분합니다. 클라이언트가 이러한 인터넷 요구 사항을 충족할 수 없는 경우, Configuration Manager 피어 캐시 기능을 사용하는 것이 좋습니다. 현재 Configuration Manager와 함께 BranchCache를 사용하고 있으며 모든 요구 사항을 충족하는 경우, BranchCache를 사용하는 빠른 파일이 적합한 옵션이 될 수 있습니다. 

### <a name="peer-cache-comparison-chart"></a>피어 캐시 비교 차트


| 기능  | 배달 최적화  | 피어 캐시  | BranchCache  |
|---------|---------|---------|---------|
| 서브넷에서 지원됨 | 예 | 예 | 아니요 |
| 대역폭 제한 | 예(기본) | 예(BITS 사용) | 예(BITS 사용) |
| 일부 콘텐츠 지원 | 예,이 열의 다음 행에 나열 된 모든 지원 되는 콘텐츠 형식에 대해 지원 됩니다. | Office 365 및 Express 업데이트에만 해당 | 예,이 열의 다음 행에 나열 된 모든 지원 되는 콘텐츠 형식에 대해 지원 됩니다. |
| 지원되는 콘텐츠 유형 | **ConfigMgr:** </br> -Express 업데이트 </br> -모든 Windows 업데이트 (버전 1910부터) 여기에는 Office 업데이트가 포함 되지 않습니다.</br> </br> **Microsoft 클라우드를 통해:**</br> - Windows 및 보안 업데이트</br> - 드라이버</br> - Windows 스토어 앱</br> - 비즈니스용 Windows 스토어 앱 | 모든 ConfigMgr 콘텐츠 유형([Windows PE](/sccm/osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic)에서 다운로드한 이미지 포함) | 모든 ConfigMgr 콘텐츠 유형(이미지 제외) |
| 디스크의 캐시 크기 제어 | 예 | 예 | 예 |
| 피어 원본의 검색 | 자동 | 수동(클라이언트 에이전트 설정) | 자동 |
| 피어 검색 | 배달 최적화 클라우드 서비스 사용(인터넷 액세스 필요) | 관리 지점 사용(클라이언트 경계 그룹 기반) | 멀티캐스트 |
| 보고 | 예(Windows Analytics 사용) | ConfigMgr 클라이언트 데이터 원본 대시보드 | ConfigMgr 클라이언트 데이터 원본 대시보드 |
| WAN 사용량 제어 | 예(기본, 그룹 정책 설정을 통해 제어할 수 있음) | 경계 그룹 | 서브넷 지원만 |
| ConfigMgr를 통한 관리 | 일부(클라이언트 에이전트 설정) | 예(클라이언트 에이전트 설정) | 예(클라이언트 에이전트 설정) |



## <a name="conclusion"></a>결론

Microsoft는 필요에 따라 빠른 설치 파일 및 피어 캐싱 기술과 함께 Configuration Manager를 사용하여 Windows 10 품질 업데이트 배달을 최적화할 것을 권장합니다. 이 방법을 사용하면 품질 업데이트를 설치하기 위해 많은 콘텐츠를 다운로드하는 Windows 10 디바이스와 관련된 문제가 완화됩니다. 또한 매달 품질 업데이트를 배포하여 Windows 10 디바이스를 최신 상태로 유지하는 것이 좋습니다. 이 방법을 사용하면 매월 디바이스에 필요한 품질 업데이트 콘텐츠의 델타가 줄어듭니다. 이 콘텐츠 델타를 줄이면 배포 지점이나 피어 원본에서 다운로드 크기가 더 작아집니다. 

빠른 설치 파일의 특성으로 인해 해당 콘텐츠 크기가 기존의 자체 포함 파일보다 훨씬 더 큽니다. 이 크기로 인해 Windows 업데이트 서비스에서 Configuration Manager 사이트 서버로의 업데이트 다운로드 시간이 더 길어집니다. 사이트 서버와 배포 지점에 필요한 디스크 공간의 크기도 증가합니다. 품질 업데이트를 다운로드하고 배포하는 데 필요한 총 시간이 더 길어질 수 있습니다. 그러나 Windows 10 디바이스에 의한 품질 업데이트의 다운로드 및 설치 중 디바이스 쪽 혜택은 주목할 만합니다. 자세한 내용은 [빠른 설치 파일 사용](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc708456(v=ws.10)?#using-express-installation-files)을 참조 하세요.

업데이트 크기가 더 큰 서버 쪽 단점으로 인해 빠른 지원 채택은 차단되지만 디바이스 쪽 혜택이 비즈니스 및 환경에 중요한 경우, Microsoft는 Configuration Manager와 함께 [비즈니스용 Windows 업데이트](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10)를 사용할 것을 권장합니다. 비즈니스용 Windows 업데이트는 환경 전체에서 빠른 설치 파일을 다운로드, 저장 및 배포할 필요 없이 Express의 모든 혜택을 제공합니다. 클라이언트는 Windows 업데이트 서비스에서 직접 콘텐츠를 다운로드하므로 배달 최적화를 계속 사용할 수 있습니다.



## <a name="bkmk_faq"></a> 질문과 대답

#### <a name="how-do-windows-express-downloads-work-with-configuration-manager"></a>Windows 빠른 다운로드는 Configuration Manager에서 어떻게 작동하나요?

WUA(Windows 업데이트 에이전트)에서 먼저 빠른 콘텐츠를 요청합니다. 빠른 업데이트를 설치하지 못하면 전체 파일 업데이트로 대체될 수 있습니다.  

1. Configuration Manager 클라이언트에서 업데이트 콘텐츠를 다운로드하도록 WUA에 지시합니다. WUA에서 빠른 다운로드를 시작하면 빠른 패키지의 일부인 스텁(예: `Windows10.0-KB1234567-<platform>-express.cab`)을 먼저 다운로드합니다.  

2. WUA는 이 스텁을 Windows 업데이트 설치 관리자 CBS(구성 요소 기반 서비스)에 전달합니다. CBS는 이 스텁을 사용하여 로컬 인벤토리를 수행하고 디바이스에 있는 파일의 델타를 제공되는 파일의 최신 버전에 연결하는 데 필요한 델타와 비교합니다.  

3. 그런 다음, CBS는 하나 이상의 빠른 .psf 파일에서 필요한 범위를 다운로드하도록 WUA에 요청합니다.  

4. 배달 최적화는 Configuration Manager와 함께 조정되며 사용 가능한 경우, 로컬 배포 지점 또는 피어에서 범위를 다운로드합니다. 배달 최적화가 사용하지 않도록 설정된 경우, BITS(Background Intelligent Transfer Service)가 피어 캐시 원본을 조정하는 Configuration Manager에서 동일한 방식으로 사용됩니다. 배달 최적화 또는 BITS에서 범위를 WUA로 전달하여 CBS에서 적용하고 설치하는 데 사용할 수 있도록 합니다.  


#### <a name="why-are-the-express-files-psf-so-large-when-stored-on-configuration-manager-peer-sources-in-the-ccmcache-folder"></a>ccmcache 폴더의 Configuration Manager 피어 원본에 저장될 때 빠른 파일(.psf)이 그렇게 큰 이유는 무엇인가요?

빠른 파일(.psf)은 스파스 파일입니다. 디스크에서 파일에 의해 사용되는 실제 공간을 확인하려면 파일의 **디스크 크기** 속성을 확인합니다. 디스크 크기 속성은 크기 값보다 훨씬 더 작아야 합니다.  


#### <a name="does-configuration-manager-support-express-installation-files-with-windows-10-feature-updates"></a>Configuration Manager가 Windows 10 기능 업데이트에서 빠른 설치 파일을 지원하나요?

아니요, Configuration Manager는 현재 Windows 10 품질 업데이트에서만 빠른 설치 파일을 지원합니다.  


#### <a name="how-much-disk-space-is-needed-per-quality-update-on-the-site-server-and-distribution-points"></a>사이트 서버 및 배포 지점에서 품질 업데이트당 필요한 디스크 공간은 어느 정도인가요?

경우에 따라 다릅니다. 각 품질 업데이트에 대해 업데이트의 전체 파일 및 빠른 버전이 모두 서버에 저장됩니다. Windows 10 품질 업데이트는 누적되므로 이러한 파일의 크기는 매월 증가합니다. 언어별 업데이트당 최소 5GB를 계획하세요. 


#### <a name="do-configuration-manager-clients-still-benefit-from-express-installation-files-when-falling-back-to-the-windows-update-service"></a>Configuration Manager 클라이언트는 Windows 업데이트 서비스로 대체되는 경우에도 빠른 설치 파일을 계속 활용하나요?

예. 다음과 같은 소프트웨어 업데이트 배포 옵션을 사용하는 경우 클라이언트는 클라우드 서비스로 대체될 때도 빠른 업데이트 및 배달 최적화를 사용합니다.  

**현재, 인접 또는 사이트 그룹의 배포 지점에서 소프트웨어 업데이트를 사용할 수 없는 경우 Microsoft Update에서 콘텐츠를 다운로드합니다.**


#### <a name="why-is-express-file-content-not-downloaded-for-existing-updates-after-i-enable-express-file-support"></a>빠른 파일 지원을 사용하도록 설정한 후 기존 업데이트에 대해 빠른 파일 콘텐츠가 다운로드되지 않는 이유는 무엇인가요? 

변경 내용은 지원을 사용하도록 설정한 후 동기화되고 배포된 새 업데이트에 대해서만 적용됩니다.


#### <a name="is-there-any-way-to-see-how-much-content-is-downloaded-from-peers-using-delivery-optimization"></a>배달 최적화를 사용하여 피어에서 다운로드되는 콘텐츠의 양을 확인할 방법이 있나요?
Windows 10 버전 1703 이상에는 **Get-DeliveryOptimizationPerfSnap** 및 **Get-DeliveryOptimizationStatus**의 새 PowerShell cmdlet 두 개가 포함됩니다. 이러한 cmdlet은 배달 최적화 및 캐시 사용에 대한 더 많은 인사이트를 제공합니다. 자세한 내용은 [Windows 10 업데이트 배달 최적화](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#the-cloud-service-doesnt-see-other-peers-on-the-network)를 참조하세요.


#### <a name="how-do-clients-communicate-with-delivery-optimization-over-the-network"></a>클라이언트는 네트워크를 통해 배달 최적화와 어떻게 통신하나요?
방화벽의 네트워크 포트, 프록시 요구 사항 및 호스트 이름에 대한 자세한 내용은 [배달 최적화 FAQ](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization#frequently-asked-questions)를 참조하세요.

## <a name="log-files"></a>로그 파일

델타 다운로드를 모니터링 하려면 다음 로그 파일을 사용 합니다.

- WUAHandler.log
- DeltaDownload.log

## <a name="next-steps"></a>다음 단계

- [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)
- [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)
