---
title: "Configuration Manager 버전 간의 상호 운용성 | Microsoft 문서"
description: "동일한 네트워크에 있는 여러 System Center Configuration Manager 계층 구조 간의 충돌을 방지하는 방법을 알아봅니다."
ms.custom: na
ms.date: 1/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1b458284961171f11acc3e84f82749addc1b6afb
ms.openlocfilehash: 890cc72f7ca0619b48ceae7c3a8c731a62341ef7
ms.lasthandoff: 02/28/2017


---
# <a name="interoperability-between-different-versions-of-system-center-configuration-manager"></a>서로 다른 버전의 System Center Configuration Manager 간 상호 운용성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 여러 독립적인 계층 구조를 동일한 네트워크에 설치하고 운영할 수 있습니다. 그러나 마이그레이션 프로세스 이외에는 Configuration Manager의 각 계층 구조가 상호 운용되지 않으므로 각 계층 구조 간에 충돌을 방지하도록 구성해야 합니다. 또한 관리하는 리소스가 올바른 계층 구조의 사이트 시스템과 상호 작용하도록 특정 구성을 만들 수 있습니다.  

 다음 섹션에서는 동일한 네트워크에서 다양한 버전의 Configuration Manager를 사용하는 방법에 대한 정보를 제공합니다.  

-   [System Center Configuration Manager와 이전 제품 버전 간 상호 운용성](#BKMK_SupConfigInterop)  

-   [Configuration Manager 콘솔에 대한 상호 운용성](#BKMK_ConsoleInterop)  

-   [혼합 버전 계층 구조의 Configuration Manager 제한 사항](#bkmk_mixed)  

##  <a name="BKMK_SupConfigInterop"></a> System Center Configuration Manager와 이전 제품 버전 간 상호 운용성  
 System Center 2012 Configuration Manager에서 System Center Configuration Manager로 업그레이드하거나 특정 System Center Configuration Manager 버전에서 최신 비전으로 업그레이드(콘솔 내 업데이트 사용)하는 경우를 제외하고 서로 다른 버전의 사이트가 동일한 계층 구조에 존재할 수 없습니다.   

 기존 System Center 2012 Configuration Manager 사이트 또는 계층 구조와 System Center Configuration Manager 사이트 및 계층 구조를 병렬로 배포할 수 있으므로 각 버전의 클라이언트가 다른 버전의 사이트에 연결하지 않도록 계획하는 것이 좋습니다.

예를 들어 둘 이상의 Configuration Manager 계층 구조에 동일한 네트워크 위치를 포함하는 겹치는 경계([겹치는 경계 정보](../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md#BKMK_BoundaryOverlap) 참조)가 있는 경우 자동 사이트 할당을 사용하지 않고 새 클라이언트를 각각 특정 사이트에 할당하는 것이 좋습니다. System Center 2012 Configuration Manager의 자동 사이트 할당에 대한 자세한 내용은 [System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법](../../../core/clients/deploy/assign-clients-to-a-site.md)을 참조하세요.  

 또한 System Center Configuration Manager의 사이트 시스템 역할을 호스트하는 컴퓨터에 System Center 2012 Configuration Manager의 클라이언트를 설치하거나, System Center 2012 Configuration Manager의 사이트 시스템 역할을 호스트하는 컴퓨터에 System Center Configuration Manager 클라이언트를 설치할 수 없습니다.  

 마찬가지로, 다음 클라이언트와 다음 VPN(가상 사설망) 연결은 지원되지 않습니다.  

-   System Center 2012 Configuration Manager 또는 이전 버전의 컴퓨터 클라이언트  

-   System Center 2012 Configuration Manager 또는 이전 버전의 장치 관리 클라이언트  

-   Windows CE Platform Builder 장치 관리 클라이언트(모든 버전)  

-   System Center Mobile Device Manager VPN 연결  

###  <a name="BKMK_SupConfigSiteAssignment"></a> 클라이언트 사이트 할당 고려 사항  
 System Center Configuration Manager 클라이언트는 단일 기본 사이트에만 할당될 수 있습니다. 클라이언트 설치 시 자동 사이트 할당을 사용하여 클라이언트를 사이트에 할당하고 둘 이상의 경계 그룹에 동일한 경계가 포함되어 있으며 경계 그룹에 할당된 사이트가 서로 다른 경우, 클라이언트의 실제 사이트 할당을 예측할 수 없습니다.  

 여러 Configuration Manager 사이트 및 계층 구조에서 경계가 겹치는 경우 클라이언트가 필요한 사이트에 할당되지 않거나 어떤 사이트에도 할당되지 않을 수 있습니다.  

 System Center Configuration Manager 클라이언트는 사이트 할당을 완료하기 전에 Configuration Manager 사이트의 버전을 확인하며 경계가 겹치는 경우 이전 버전의 사이트에 할당될 수 없습니다. 그러나 System Center 2012 Configuration Manager 클라이언트가 System Center Configuration Manager 사이트에 잘못 할당될 수도 있습니다.  

 두 계층 구조에서 경계가 겹치는 경우 클라이언트가 의도치 않게 잘못된 사이트에 할당되지 않도록 하려면 클라이언트를 특정 사이트에 할당하도록 Configuration Manager 클라이언트 설치 매개 변수를 구성하는 것이 좋습니다.  

##  <a name="bkmk_mixed"></a> 혼합 버전 계층 구조의 Configuration Manager 제한 사항  
 System Center Configuration Manager 사이트를 업그레이드하는 경우 각 사이트가 서로 다른 버전인 시기가 있습니다. 예를 들어 중앙 관리 사이트를 새 버전으로 업그레이드하는 경우 사이트 유지 관리 기간으로 인해 하나 이상의 기본 사이트가 이후 시간 및 날짜까지 업그레이드되지 않을 수 있습니다.  

 단일 계층 구조에 있는 여러 사이트가 서로 다른 버전을 실행하는 경우 일부 기능을 사용할 수 없습니다. 이는 Configuration Manager 콘솔에서 Configuration Manager 개체를 관리하는 방법 및 클라이언트에서 사용할 수 있는 기능에 영향을 줄 수 있습니다. 일반적으로 최신 버전의 Configuration Manager는 더 낮은 서비스 팩 버전을 실행하는 사이트 또는 클라이언트에서 액세스할 수 없습니다.  

### <a name="limitations-when-upgrading--configuration-manager"></a>Configuration Manager를 업그레이드할 때의 제한 사항  

|개체|세부 정보|  
|------------|-------------|  
|네트워크 액세스 계정|**System Center 2012 Configuration Manager에서 System Center Configuration Manager로 업그레이드하는 경우:** 중앙 관리 사이트에 연결되어 있으며 System Center Configuration Manager로 업데이트된 Configuration Manager 콘솔에서 네트워크 액세스 계정 정보를 보는 경우 System Center 2012 Configuration Manager를 실행하는 기본 사이트에 구성된 계정 정보는 콘솔에 표시되지 않습니다. 기본 사이트를 중앙 관리 사이트와 동일한 버전으로 업그레이드하면 계정 정보가 콘솔에 표시됩니다.<br /><br /> **System Center Configuration Manager 버전 간에 업그레이드하는 경우:** 중앙 관리 사이트에 연결되어 있으며 새 버전의 System Center Configuration Manager로 업데이트된 Configuration Manager 콘솔에서 네트워크 액세스 계정 정보를 보는 경우 이전 버전을 실행하는 기본 사이트에서 구성된 계정 정보는 콘솔에 표시되지 않습니다. 기본 사이트를 중앙 관리 사이트와 동일한 버전으로 업그레이드하면 계정 정보가 콘솔에 표시됩니다.|  
|운영 체제 배포를 위한 부팅 이미지|**System Center 2012 Configuration Manager에서 System Center Configuration Manager로 업그레이드하는 경우:** 계층 구조의 최상위 사이트를 System Center Configuration Manager로 업그레이드하는 경우 기본 부팅 이미지가 자동으로 Windows ADK(Windows Assessment and Deployment Kit) 10 기반 부팅 이미지로 업데이트됩니다. 이러한 부팅 이미지는 System Center Configuration Manager 사이트에 있는 클라이언트에 배포하는 경우에만 사용합니다. 자세한 내용은 [System Center Configuration Manager에서 운영 체제 배포 상호 운용성 계획](../../../osd/plan-design/planning-for-operating-system-deployment-interoperability.md)을 참조하세요.<br /><br /> **System Center Configuration Manager 버전 간에 업그레이드하는 경우:** 새 버전의 cm6long에서 사용 중인 Windows ADK 버전을 업데이트하지 않는 한, 부팅 이미지에는 영향을 주지 않습니다.|  
|새 작업 순서 단계|특정 버전의 Configuration Manager에서 도입되었으며 이전 버전에서 사용할 수 없었던 단계를 포함하는 작업 순서를 만드는 경우 다음과 같은 문제가 발생할 수 있습니다.<br /><br /> -- 이전 버전의 Configuration Manager를 실행하는 사이트에서 작업 순서를 편집하려고 하면 오류가 발생합니다.<br /><br /> -- 이전 버전의 Configuration Manager 클라이언트를 실행하는 컴퓨터에서 작업 순서가 실행되지 않습니다.|  
|클라이언트에서 하위 버전 관리 지점으로의 통신|클라이언트보다 낮은 버전을 실행하는 사이트의 관리 지점과 통신하는 Configuration Manager 클라이언트는 하위 버전의 Configuration Manager가 지원하는 기능만 사용할 수 있습니다. 예를 들어 최근에 업그레이드된 System Center Configuration Manager 사이트의 콘텐츠를 아직 해당 버전으로 업그레이드되지 않은 관리 지점과 통신하는 클라이언트에 배포하는 경우 이 클라이언트에서 최신 버전의 새로운 기능을 사용할 수 없습니다.|  

##  <a name="BKMK_ConsoleInterop"></a> Configuration Manager 콘솔에 대한 상호 운용성  
 다음 표에는 여러 버전의 Configuration Manager가 설치된 환경에서의 Configuration Manager 콘솔 사용에 대한 정보가 포함되어 있습니다.  

|상호 운용성 환경|추가 정보|  
|----------------------------------|----------------------|  
|System Center 2012 Configuration Manager 및 System Center Configuration Manager가 둘 다 포함된 환경|Configuration Manager 사이트를 관리하려면 콘솔 및 콘솔이 연결하는 사이트에서 동일한 버전의 Configuration Manager를 실행해야 합니다. 예를 들어 System Center 2012 Configuration Manager 콘솔을 사용하여 System Center Configuration Manager 사이트를 관리할 수 없으며, 그 반대의 경우도 마찬가지입니다.<br /><br /> System Center 2012 Configuration Manager 콘솔과 System Center Configuration Manager 콘솔을 동일한 컴퓨터에 설치할 수 없습니다.|  
|여러 버전의 System Center Configuration Manager가 설치된 환경|System Center Configuration Manager는 한 컴퓨터에서 둘 이상의 Configuration Manager 콘솔 설치를 지원하지 않습니다. 각기 다른 버전의 System Center Configuration Manager와 관련된 여러 콘솔을 사용하려면 각 콘솔을 별도의 컴퓨터에 설치해야 합니다.<br /><br /> 한 계층 구조의 사이트를 새 버전으로 업데이트하는 동안 최신 버전을 실행하는 사이트에 콘솔을 연결하고 해당 계층 구조의 다른 사이트에 대한 정보를 볼 수 있습니다. 그러나 콘솔 버전과 Configuration Manager 사이트 버전 간의 차이로 인해 데이터 문제가 발생할 수 있고 최신 제품 버전에서 사용 가능한 일부 기능을 콘솔에서 사용할 수 없기 때문에 이 구성은 사용하지 않는 것이 좋습니다. <br /></br /> 사이트 버전이 일치하지 않는 버전으로 콘솔을 사용하는 경우 사이트 관리가 지원되지 않습니다. 이렇게 하면 데이터의 손실이 발생할 수 있으며 사이트를 위험하게 할 수 있습니다. 예를 들어, 1606 버전을 실행하는 사이트를 관리하는 데 1610 버전의 콘솔 사용이 지원되지 않습니다. |

