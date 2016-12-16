---
title: "계층 구조 디자인 | System Center Configuration Manager"
description: "사이트 계층 구조를 계획할 수 있도록 System Center Configuration Manager에 대한 사용 가능한 토폴로지 및 관리 옵션을 이해합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
caps.latest.revision: 22
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 783fb4d61aab83ad64b9cec332e90d6c9de59f47
ms.openlocfilehash: b1ed3011356a794b7b0913a1c8f189230d8957b2


---
# <a name="design-a-hierarchy-of-sites-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 사이트 계층 구조 디자인

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 계층 구조의 첫 번째 사이트를 설치하려면 먼저 Configuration Manager에 사용 가능한 토폴로지와 토폴로지의 연관 관계, 각 사이트 유형에서 가능한 관리 범위를 이해해야 합니다. 그래야 설치해야 하는 사이트 수를 줄일 수 있는 콘텐츠 관리 옵션을 고려하여 현재 비즈니스 요구를 효율적으로 처리할 토폴로지를 계획할 수 있고, 향후의 크기 증가를 관리하도록 이후에 확장할 수도 있습니다.  

> [!NOTE]
> Configuration Manager의 새 설치를 계획할 때는 활성 버전의 현재 문제를 자세히 설명하는 [릴리스 정보]( /sccm/core/servers/deploy/install/release-notes)에 대해 알고 있어야 합니다. 릴리스 정보는 Configuration Manager의 모든 분기에 적용됩니다.  그러나 [Technical Preview Branch]( /sccm/core/get-started/technical-preview)를 사용하는 경우 각 Technical Preview 버전의 설명서에서 해당 분기와 관련된 문제를 확인할 수 있습니다.  

##  <a name="a-namebkmktopologya-hierarchy-topology"></a><a name="bkmk_topology"></a> 계층 토폴로지  
 계층 토폴로지의 범위는 단일 독립 실행형 기본 사이트에서 계층 구조의 최상위(상위 계층) 사이트에 있는 중앙 관리 사이트와 연결된 기본 및 보조 사이트 그룹까지입니다.    
계층 구조에서 사용하는 사이트 유형 및 수의 핵심 드라이버는 일반적으로 지원해야 하는 장치의 유형 및 수에 해당합니다.  

 **독립 실행형 기본 사이트:** 단일 기본 사이트로 모든 장치와 사용자를 관리할 수 있는 경우 독립 실행형 기본 사이트를 사용하세요([크기 조정 및 비율 값](/sccm/core/plan-design/configs/size-and-scale-numbers) 참조). 이 토폴로지는 회사의 여러 지리적 위치를 단일 기본 사이트에서 처리할 수 있는 경우에도 적합합니다.  네트워크 트래픽을 쉽게 관리하려면 선호하는 관리 지점과 신중하게 계획한 콘텐츠 인프라를 사용하세요([System Center Configuration Manager에서 콘텐츠 관리의 기본 개념](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) 참조).  

 이 토폴로지의 이점은 다음과 같습니다.  

-   관리 오버헤드를 간소화합니다.  

-   클라이언트 사이트 할당 및 사용 가능한 리소스 및 서비스 검색을 간소화합니다.  

-   사이트 간 데이터베이스 복제로 정의된 가능한 지연 시간을 제거합니다.  

-   이 선택 항목은 영구적이 아니며 독립 실행형 기본 계층 구조를 중앙 관리 사이트에서 더 큰 계층 구조로 확장할 수 있습니다. 이렇게 하면 새 기본 사이트를 설치하여 배포 규모를 확장할 수 있습니다.  


**자식 기본 사이트가 하나 이상 있는 중앙 관리 사이트:** 모든 장치 및 사용자를 관리하려면 기본 사이트가 두 개 이상 필요할 경우 이 토폴로지를 사용하세요.  이 토폴로지는 이점은 다음과 같습니다.  

-   두 개 이상의 단일 기본 사이트를 사용해야 하는 경우 필수  

-   계층 구조 규모를 확장할 수 있도록 최대 25개의 기본 사이트 지원  

-   이 선택 항목은 영구적입니다. 자식 기본 사이트를 분리하여 독립 실행형 기본 사이트로 설정할 수 없습니다. 따라서 사이트를 다시 설치하지 않는 경우 항상 중앙 관리 사이트를 사용합니다.  

 다음 섹션에서는 추가 사이트 대신 특정 사이트 또는 콘텐츠 관리 옵션을 사용할 시기를 이해하는 데 도움이 됩니다.  

##  <a name="a-namebkmkchoosecasa-determine-when-to-use-a-central-administration-site"></a><a name="BKMK_ChooseCAS"></a> 중앙 관리 사이트를 사용할 시기 결정  
 중앙 관리 사이트를 사용하면 계층 전체의 설정을 구성하고 계층의 모든 사이트와 개체를 모니터링할 수 있습니다. 이 사이트 유형은 클라이언트를 직접 관리하지는 않지만 계층 전반의 사이트 및 클라이언트 구성을 비롯한 사이트 간 데이터 복제를 조정합니다.  

**다음 정보는 중앙 관리 사이트를 설치할 시기를 결정하는 데 도움이 됩니다.**  

-   중앙 관리 사이트는 계층의 최상위 사이트입니다.  

-   기본 사이트가 둘 이상 있는 계층을 구성하는 경우 중앙 관리 사이트를 반드시 설치해야 하며, 중앙 관리 사이트가 설치하는 첫 번째 사이트여야 합니다.  

-   중앙 관리 사이트는 기본 사이트를 하위 사이트로서만 지원합니다.  

-   중앙 관리 사이트에는 클라이언트를 할당할 수 없습니다.  

-   중앙 관리 사이트는 관리 지점 및 배포 지점과 같이 클라이언트를 직접 지원하는 사이트 시스템 역할을 지원하지 않습니다.  

-   중앙 관리 사이트에 연결된 Configuration Manager 콘솔을 사용하는 경우 계층의 모든 클라이언트를 관리하고 모든 클라이언트 사이트에 대한 사이트 관리 작업을 수행할 수 있습니다. 이러한 작업에는 자식 기본 사이트 또는 보조 사이트에 관리 지점 또는 기타 사이트 시스템 역할을 설치하는 작업이 포함될 수 있습니다.  

-   중앙 관리 사이트를 사용하는 경우 중앙 관리 사이트에서만 해당 계층 구조의 모든 사이트의 사이트 데이터를 볼 수 있습니다. 이러한 데이터에는 인벤토리 데이터 및 상태 메시지와 같은 정보가 포함됩니다.  

-   개별 사이트에서 실행되는 검색 방법을 할당하여 중앙 관리 사이트에서 계층 전반의 검색 작업을 구성할 수 있습니다.  

-   관리자에 따라 다양한 보안 역할, 보안 범위 및 컬렉션을 할당하여 계층 전반의 보안을 관리할 수 있습니다. 이러한 구성은 계층의 각 사이트에 적용됩니다.  

-   파일 복제 및 데이터베이스 복제 시 계층의 사이트 간 통신을 제어하도록 구성할 수 있습니다. 예를 들어 사이트 데이터에 대한 데이터베이스 복제를 예약하거나, 사이트 간 파일 기반 데이터 전송 시 대역폭을 관리할 수 있습니다.  

##  <a name="a-namebkmkchoosepriimarya-determine-when-to-use-a-primary-site"></a><a name="BKMK_ChoosePriimary"></a> 기본 사이트를 사용할 시기 결정  
 기본 사이트는 클라이언트를 관리하는 데 사용됩니다. 기본 사이트를 중앙 관리 사이트 아래에 자식 기본 사이트로 설치하거나 새 계층 구조의 첫 번째 사이트로 설치할 수 있습니다. 계층의 첫 번째 사이트로 설치하는 기본 사이트는 독립 실행형 기본 사이트를 만듭니다. 자식 기본 사이트와 독립 실행형 기본 사이트는 모두 보조 사이트를 기본 사이트의 자식 사이트로 지원합니다.  

 기본 사이트는 다음과 같은 목적으로 사용하는 것이 좋습니다.  

-   장치 및 사용자를 관리하기 위해  

-   단일 계층 구조를 사용하여 관리할 수 있는 장치 수를 늘리기 위해  

-   배포 관리를 위한 추가 연결 지점을 제공하기 위해  

-   조직의 관리 요구 사항을 충족하기 위해 예를 들어 원격 위치에 기본 사이트를 설치하여 대역폭이 낮은 네트워크를 통한 배포 콘텐츠 전송을 관리할 수 있습니다. 그러나 System Center Configuration Manager에서는 데이터를 배포 지점으로 전송할 때 네트워크 대역폭 사용을 제한하는 옵션을 사용할 수 있으며, 이러한 콘텐츠 관리 기능 덕분에 추가 사이트를 설치하지 않아도 되는 경우가 있습니다.  


**다음 정보는 기본 사이트를 설치할 시기를 결정하는 데 도움이 됩니다.**  

-   기본 사이트는 독립 실행형 기본 사이트이거나 더 큰 계층의 자식 기본 사이트가 될 수 있습니다. 기본 사이트가 중앙 관리 사이트를 포함하는 계층의 구성원인 경우 이 사이트는 데이터베이스 복제본을 사용하여 사이트 간에 데이터를 복제합니다. 단일 사이트에서 지원할 수 있는 것보다 많은 클라이언트 및 장치를 지원해야 하는 경우가 아니라면 독립 실행형 기본 사이트를 설치해 볼 수 있습니다.  독립 실행형 기본 사이트를 설치하고 나면 해당 사이트를 확장하여 배포를 강화하도록 새 중앙 관리 사이트에 보고할 수 있습니다.  

-   기본 사이트는 중앙 관리 사이트를 상위 사이트로만 지원합니다.  

-   기본 사이트는 하위 사이트로 보조 사이트만 지원하며, 여러 보조 하위 사이트를 지원할 수 있습니다.  

-   기본 사이트는 할당된 클라이언트의 모든 클라이언트 데이터를 처리합니다.  

-   기본 사이트에서는 데이터베이스 복제를 사용하여 중앙 관리 사이트(새로운 사이트를 설치할 때 자동으로 구성됨)와 직접 통신합니다.  

##  <a name="a-namebkmkchoosesecondarya-determine-when-to-use-a-secondary-site"></a><a name="BKMK_ChooseSecondary"></a> 보조 사이트를 사용할 시기 결정  
 낮은 대역폭 네트워크를 통한 배포 콘텐츠 및 클라이언트 데이터의 전송을 관리하려면 보조 사이트를 사용합니다.  

 보조 사이트는 중앙 관리 사이트 또는 보조 사이트의 직계 부모 기본 사이트에서 관리할 수 있습니다. 보조 사이트는 기본 사이트에 연결해야 합니다. 기본 사이트에 연결된 보조 사이트는 다른 상위 사이트로 이동할 수 없으며, 이동하려면 먼저 제거한 다음 새 기본 사이트 아래에 하위 사이트로 다시 설치해야 합니다. 그러나 두 개의 피어 보조 사이트 간에 콘텐츠의 경로를 지정하는 방식으로 배포 콘텐츠의 파일 기반 복제를 관리할 수 있습니다. 보조 사이트에서 클라이언트 데이터를 기본 사이트에 전송하기 위해 파일 기반 복제를 사용합니다. 보조 사이트에서는 부모 기본 사이트와 통신하기 위해 데이터베이스 복제도 사용합니다.  

 다음 조건 중 하나라도 충족할 경우 보조 사이트를 설치하는 것이 좋습니다.  

-   관리자에 대한 로컬 연결 지점이 필요하지 않습니다.  

-   배포 콘텐츠를 계층 구조의 하위 사이트로 전송하는 작업을 관리해야 합니다.  

-   계층 구조의 상위 사이트로 전송되는 클라이언트 정보를 관리해야 합니다.  

 보조 사이트의 설치를 원하지 않으며 원격 위치에 클라이언트가 있는 경우 Windows BranchCache를 사용하거나 대역폭 제어 및 일정에 사용할 수 있는 배포 지점을 설치하는 것이 좋습니다. 이러한 콘텐츠 관리 옵션은 보조 사이트 유무에 관계없이 사용할 수 있고 이를 통해 설치해야 할 사이트 및 서버의 수를 줄일 수 있습니다. Configuration Manager의 콘텐츠 관리 옵션에 대한 내용은 [콘텐츠 관리 옵션을 사용할 시기 결정](#BKMK_ChooseSecondaryorDP)을 참조하세요.  


**다음 정보를 사용하여 보조 사이트를 설치할 시기를 결정할 수 있습니다.**  

-   SQL Server의 로컬 인스턴스를 사용할 수 없는 경우 보조 사이트 설치 과정에서 SQL Server Express가 자동으로 설치됩니다.  

-   보조 사이트 설치는 Configuration Manager 설치를 컴퓨터에서 직접 실행하는 대신 Configuration Manager 콘솔에서 시작됩니다.  

-   보조 사이트에서는 사이트 데이터베이스에 있는 정보의 하위 집합을 사용하여 부모 기본 사이트와 보조 사이트 간 데이터베이스 복제를 통해 복제하는 데이터의 크기를 줄입니다.  

-   보조 사이트는 공통 부모 기본 사이트를 공유하는 다른 보조 사이트로 파일 기반 콘텐츠를 라우팅하는 기능을 지원합니다.  

-   보조 사이트를 설치할 때 보조 사이트 서버에 있는 관리 지점 및 배포 지점이 자동으로 배포됩니다.  

##  <a name="a-namebkmkchoosesecondaryordpa-determine-when-to-use-content-management-options"></a><a name="BKMK_ChooseSecondaryorDP"></a> 콘텐츠 관리 옵션을 사용할 시기 결정  
 원격 네트워크 위치에 클라이언트가 있는 경우 기본 사이트 또는 보조 사이트 대신 하나 이상의 콘텐츠 관리 옵션을 사용하는 것이 좋습니다. Windows BranchCache를 사용하거나, 대역폭 제어를 위한 배포 지점을 구성하거나, 콘텐츠를 배포 지점에 수동으로 복사(콘텐츠 준비)하는 경우에는 일반적으로 사이트를 설치하지 않아도 됩니다.  


**다음 조건 중 하나라도 충족할 경우 다른 사이트를 설치하는 대신 배포 지점을 배포하는 것이 좋습니다.**  

-   네트워크 대역폭이 원격 위치의 클라이언트 컴퓨터가 관리 지점과 통신하여 클라이언트 정책을 다운로드하고 인벤토리, 보고 상태 및 검색 정보를 보내는 데 충분합니다.  

-   BITS(Background Intelligent Transfer Service)는 네트워크 요구 사항에 충분한 대역폭 제어 기능을 제공하지 않습니다.  

 Configuration Manager의 콘텐츠 관리 옵션에 대한 자세한 내용은 [System Center Configuration Manager에서 콘텐츠 관리의 기본 개념](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)을 참조하세요.  

##  <a name="a-namebkmkbeyonda-beyond-hierarchy-topology"></a><a name="bkmk_beyond"></a> 계층 토폴로지 외의 다른 사항들  
 초기 계층 구조 토폴로지 이외에도 계층 구조의 다양한 사이트에서 사용할 수 있는 서비스 또는 기능(사이트 시스템 역할) 및 계층 구조 전체 구성과 기능을 인프라에서 관리하는 방법을 고려합니다. 다음은 일반적인 고려 사항으로 별도의 항목에서 다룹니다. 다음은 계층 구조 설계와 영향을 주거나 영향을 받을 수 있으므로 고려해야 합니다.  

-   [System Center Configuration Manager로 컴퓨터 및 장치 관리](/sccm/core/clients/manage/manage-clients)를 준비할 때 관리하는 장치가 온-프레미스에 있는지 클라우드에 있는지 또는 사용자 소유의 장치(BYOD)를 포함하는지 고려합니다.  또한 Configuration Manager로 직접 관리하거나 Microsoft Intune과의 통합을 통해 관리할 수 있는 Windows 10 컴퓨터와 같이 여러 관리 옵션으로 지원되는 장치를 어떻게 관리할지 고려합니다.  

-   사용 가능한 네트워크 인프라가 원격 위치 간의 데이터 흐름에 어떤 영향을 줄지 이해합니다([System Center Configuration Manager에 대한 네트워크 환경 준비](/sccm/core/plan-design/network/configure-firewalls-ports-domains) 참조). 또한 관리하는 사용자 및 장치의 지리적 위치 및 인프라에 회사 도메인을 통해 액세스할지 또는 인터넷에서 액세스할지를 고려합니다.  

-   배포 정보(파일 및 앱)를 관리하는 장치에 효과적으로 분배하도록 콘텐츠 인프라를 계획합니다([System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md) 참조).  

-   사용할 [System Center Configuration Manager의 특징과 기능](../../../core/plan-design/changes/features-and-capabilities.md) 및 필요한 사이트 시스템 역할 또는 Windows 인프라를 확인하고 네트워크 및 서버 리소스를 가장 효율적으로 사용하기 위해 여러 사이트 계층 구조의 사이트 중에서 어느 사이트에서 배포할지 결정합니다.  

-   PKI의 사용을 비롯하여 데이터 및 장치에 대한 보안을 고려합니다. [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../core/plan-design/network/pki-certificate-requirements.md)  


**사이트별 구성과 관련한 다음 리소스 검토:**  

-   [System Center Configuration Manager용 SMS 공급자에 대한 계획](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)  

-   [System Center Configuration Manager용 사이트 데이터베이스에 대한 계획](../../../core/plan-design/hierarchy/plan-for-the-site-database.md)  

-   [System Center Configuration Manager에 대한 사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)  

-   [System Center Configuration Manager에서 보안 계획](../../../core/plan-design/security/plan-for-security.md)  

-   사이트 내에서 콘텐츠를 배포할 때[Managing network bandwidth](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#bkmk_bandwidth)  


**사이트 및 계층 구조에 대한 구성 고려 사항:**  

-   [System Center Configuration Manager의 사이트 및 계층에 사용할 수 있는 고가용성 옵션](/sccm/protect/understand/high-availability-options)   

-   [System Center Configuration Manager에 대한 Active Directory 스키마를 확장](../../../core/plan-design/network/extend-the-active-directory-schema.md)한 후 [System Center Configuration Manager용으로 사이트 데이터를 게시](../../../core/servers/deploy/configure/publish-site-data.md)하도록 사이트를 구성할 것인가요?  

-   계층 구조 내 사이트 간의 네트워크 대역폭을 관리하려면 [System Center Configuration Manager의 사이트 간 데이터 전송](../../../core/servers/manage/data-transfers-between-sites.md)을 참조하세요.  

-   [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../../core/understand/fundamentals-of-role-based-administration.md)  



<!--HONumber=Nov16_HO1-->


