---
title: 사이트 계층 구조 디자인
titleSuffix: Configuration Manager
description: Configuration Manager에서 사이트 계층 구조를 계획하는 데 사용할 수 있는 토폴로지 및 관리 옵션을 이해합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: eb7e4a6645514cedee382932adff76da14d0ba16
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385527"
---
# <a name="design-a-hierarchy-of-sites-for-configuration-manager"></a>Configuration Manager에 대한 사이트 계층 구조 디자인

*적용 대상: System Center Configuration Manager(현재 분기)*

새 Configuration Manager 계층 구조의 첫 번째 사이트를 설치하기 전에 다음 항목을 이해하는 것이 좋습니다.  

- Configuration Manager에 사용할 수 있는 토폴로지  

- 사용 가능한 사이트의 유형 및 서로 간의 관계  

- 각 유형의 사이트에서 제공하는 관리 범위  

- 설치해야 하는 사이트의 수를 줄일 수 있는 콘텐츠 관리 옵션  

그런 다음, 현재의 비즈니스 요구를 효율적으로 처리하고 향후의 성장을 관리하기 위해 나중에 확장할 수 있는 토폴로지를 계획합니다.  

계획할 때는 계층 구조 또는 독립 실행형 사이트에 추가 사이트를 추가하는 데 관련된 다음 제한 사항에 유의하세요.  

- 새 기본 사이트는 [지원되는 기본 사이트 수](/sccm/core/plan-design/configs/size-and-scale-numbers)까지 중앙 관리 사이트 아래에 설치합니다.  

- [독립 실행형 기본 사이트를 확장하여 새 중앙 관리 사이트를 설치](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand)한 다음, 추가 기본 사이트를 설치합니다.  

- 새 보조 사이트는 [기본 사이트 및 전체 계층 구조에 지원되는 제한](/sccm/core/plan-design/configs/size-and-scale-numbers)까지 기본 사이트 아래에 설치합니다.  

- 이전에 설치한 사이트를 기존 계층 구조에 추가하여 두 개의 독립 실행형 사이트를 병합할 수는 없습니다. Configuration Manager는 사이트의 기존 계층 구조에 새 사이트를 설치하는 기능만 지원합니다.  


> [!NOTE]  
> Configuration Manager의 새 설치를 계획할 때는 활성 버전의 현재 문제를 자세히 설명하는 [릴리스 정보](/sccm/core/servers/deploy/install/release-notes)에 대해 알아보세요. 릴리스 정보는 Configuration Manager의 모든 분기에 적용됩니다. [기술 미리 보기 분기](/sccm/core/get-started/technical-preview)를 사용하는 경우 각 버전의 기술 미리 보기 설명서에서 해당 분기와 관련된 문제를 찾습니다.  



##  <a name="bkmk_topology"></a> 계층 토폴로지  

계층 구조 토폴로지의 범위는 다음과 같습니다.  

- 가장 간단한 범위: 단일 독립 실행형 기본 사이트  

- 가장 복잡한 범위: 계층 구조의 최상위 사이트에 있는 중앙 관리 사이트와 연결된 기본 및 보조 사이트 그룹  

계층 구조에서 사용하는 사이트의 유형과 수에 대한 핵심 추진 요소는 일반적으로 지원해야 하는 디바이스의 유형과 수입니다.   

### <a name="standalone-primary-site"></a>독립 실행형 기본 사이트

독립 실행형 기본 사이트는 모든 디바이스 및 사용자의 관리를 지원할 수 있는 경우 사용합니다. 자세한 내용은 [크기 조정 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers)을 참조하세요. 또한 이 토폴로지는 단일 기본 사이트에서 회사의 지리적 위치를 제공할 수 있는 경우에도 적합합니다. 네트워크 트래픽을 관리하려면 경계 그룹의 여러 관리 지점과 신중하게 계획된 콘텐츠 인프라를 사용합니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/servers/deploy/configure/boundary-groups) 및 [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)을 참조하세요.  

이 토폴로지는 다음과 같은 이점을 제공합니다.  

- 관리 오버헤드를 간소화합니다.  

- 클라이언트 사이트 할당 및 사용 가능한 리소스 및 서비스 검색을 간소화합니다.  

- 사이트 간 데이터베이스 복제에 도입된 가능한 지연을 제거합니다.  

- 중앙 관리 사이트를 사용하여 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장할 수 있는 옵션이 있습니다. 이 옵션을 사용하면 새 기본 사이트를 설치하여 배포 규모를 확장할 수 있습니다.  


### <a name="central-administration-site-with-one-or-more-child-primary-sites"></a>자식 기본 사이트가 하나 이상 있는 중앙 관리 사이트 

이 토폴로지는 모든 디바이스 및 사용자의 관리를 지원하기 위해 기본 사이트가 둘 이상 필요한 경우 사용합니다. 두 개 이상의 단일 기본 사이트를 사용해야 하는 경우 필수입니다. 

이 토폴로지는 다음과 같은 이점을 제공합니다.  

- 계층 구조 규모를 확장할 수 있도록 최대 25개의 기본 사이트를 지원합니다.    

- 사이트를 다시 설치하지 않으면 항상 중앙 관리 사이트를 사용합니다. 이 옵션은 영구적입니다. 자식 기본 사이트는 분리하여 독립 실행형 기본 사이트로 만들 수 없습니다.  



##  <a name="BKMK_ChooseCAS"></a> 중앙 관리 사이트를 사용할 시기 결정  

중앙 관리 사이트를 사용하면 계층 전체의 설정을 구성하고 계층의 모든 사이트와 개체를 모니터링할 수 있습니다. 이 사이트 유형은 클라이언트를 직접 관리하지 않습니다. 계층 구조 전체의 사이트 및 클라이언트 구성을 포함한 사이트 간 데이터 복제를 조정합니다.  

다음 정보는 중앙 관리 사이트를 설치할 시기를 결정하는 데 도움이 됩니다.  

- 중앙 관리 사이트는 계층의 최상위 사이트입니다.  

- 기본 사이트가 둘 이상 있는 계층 구조를 구성하는 경우 중앙 관리 사이트를 설치합니다.  

     - 둘 이상의 기본 사이트가 즉시 필요한 경우 중앙 관리 사이트를 먼저 설치합니다.  

     - 기본 사이트가 이미 있고 중앙 관리 사이트를 설치하려는 경우 [독립 실행형 기본 사이트를 확장](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand)하여 중앙 관리 사이트를 설치합니다.  

- 중앙 관리 사이트는 기본 사이트를 자식 사이트로서만 지원합니다.  

- 중앙 관리 사이트에는 클라이언트를 할당할 수 없습니다.  

- 중앙 관리 사이트는 관리 지점 및 배포 지점과 같이 클라이언트를 직접 지원하는 사이트 시스템 역할을 지원하지 않습니다.  

- 계층 구조의 모든 클라이언트를 관리하고 중앙 관리 사이트에 연결된 Configuration Manager 콘솔에서 모든 사이트 관리 작업을 수행합니다. 이러한 작업에는 관리 지점 또는 다른 사이트 시스템 역할을 자식 기본 사이트 또는 보조 사이트에 설치하는 작업이 포함됩니다.  

- 중앙 관리 사이트를 사용하는 경우 이는 계층 구조의 모든 사이트에서 사이트 데이터를 볼 수 있는 유일한 위치입니다. 이러한 데이터에는 인벤토리 데이터 및 상태 메시지와 같은 정보가 포함됩니다.  

- 중앙 관리 사이트에서 계층 구조 전체의 검색 작업을 구성합니다. 중앙 관리 사이트에서 검색 방법을 할당하여 개별 기본 사이트에서 실행합니다.  

- 서로 다른 보안 역할, 보안 범위 및 컬렉션을 다른 관리 사용자에게 할당하여 계층 구조 전체의 보안을 관리합니다. 이러한 구성은 계층의 각 사이트에 적용됩니다.  

- 계층 구조의 사이트 간 통신을 제어하도록 복제를 구성합니다. 사이트 데이터에 대한 데이터베이스 복제를 예약하고, 사이트 간에 파일 기반 데이터를 전송하기 위한 대역폭을 관리합니다.  



##  <a name="BKMK_ChoosePriimary"></a> 기본 사이트를 사용할 시기 결정  

기본 사이트는 클라이언트를 관리하는 데 사용됩니다. 기본 사이트를 자식 사이트로 중앙 관리 사이트 아래에 설치하거나 새 계층 구조의 첫 번째 사이트로 설치합니다. 계층 구조의 첫 번째 사이트인 기본 사이트에서 독립 실행형 기본 사이트를 만듭니다. 자식 기본 사이트와 독립 실행형 기본 사이트에서 모두 보조 사이트를 지원합니다.  

다음과 같은 이유로 추가 기본 사이트를 추가하는 것이 좋습니다.  

- 디바이스 수를 늘리기 위해 단일 계층 구조로 관리합니다.  

- 조직의 관리 요구 사항을 충족하기 위해 예를 들어 원격 위치에 기본 사이트를 설치하여 대역폭이 낮은 네트워크를 통한 배포 콘텐츠 전송을 관리할 수 있습니다.  

     - 대신 데이터를 배포 지점으로 전송할 때 옵션을 사용하여 네트워크 대역폭을 제한하는 방법을 고려합니다. 이러한 콘텐츠 관리 기능 덕분에 추가 사이트를 설치하지 않아도 되는 경우가 있습니다.  


기본 사이트를 설치할 시기를 결정하는 데 도움이 되는 정보는 다음과 같습니다.  

- 기본 사이트는 독립 실행형 기본 사이트 또는 더 큰 계층 구조의 자식 기본 사이트가 될 수 있습니다. 기본 사이트가 중앙 관리 사이트를 포함하는 계층의 구성원인 경우 이 사이트는 데이터베이스 복제본을 사용하여 사이트 간에 데이터를 복제합니다. 단일 사이트에서 지원하는 것보다 많은 클라이언트 및 디바이스를 지원해야 하는 경우가 아니면 독립 실행형 기본 사이트를 설치하는 것이 좋습니다. 독립 실행형 기본 사이트를 설치한 후 나중에 필요한 경우 이를 확장하여 새 중앙 관리 사이트에 배포를 확장하도록 보고합니다.  

- 기본 사이트는 중앙 관리 사이트를 부모 사이트로만 지원합니다.  

- 기본 사이트는 보조 사이트를 자식 사이트로만 지원하며 여러 보조 사이트를 지원합니다.  

- 기본 사이트는 할당된 클라이언트의 모든 클라이언트 데이터를 처리합니다.  

- 기본 사이트에서는 데이터베이스 복제를 사용하여 중앙 관리 사이트와 직접 통신합니다. 이 동작은 새 사이트를 설치할 때 자동으로 구성됩니다.  



##  <a name="BKMK_ChooseSecondary"></a> 보조 사이트를 사용할 시기 결정  

낮은 대역폭 네트워크를 통한 배포 콘텐츠 및 클라이언트 데이터의 전송을 관리하려면 보조 사이트를 사용합니다.  

보조 사이트는 중앙 관리 사이트 또는 보조 사이트의 직계 부모 기본 사이트에서 관리할 수 있습니다. 보조 사이트는 기본 사이트에 연결됩니다. 보조 사이트를 제거한 다음, 새 기본 사이트 아래에 자식 사이트로 다시 설치해야 다른 부모 사이트로 이동할 수 있습니다.

그러나 두 개의 피어 보조 사이트 간에 콘텐츠의 경로를 지정하는 방식으로 배포 콘텐츠의 파일 기반 복제를 관리할 수 있습니다. 보조 사이트에서 클라이언트 데이터를 기본 사이트에 전송하기 위해 파일 기반 복제를 사용합니다. 보조 사이트에서는 부모 기본 사이트와 통신하기 위해 데이터베이스 복제도 사용합니다.  

다음 조건 중 하나라도 충족할 경우 보조 사이트를 설치하는 것이 좋습니다.  

- 관리자에 대한 로컬 연결 지점이 필요하지 않습니다.  

- 배포 콘텐츠를 계층 구조의 하위 사이트로 전송하는 작업을 관리해야 합니다.  

- 계층 구조의 상위 사이트로 전송되는 클라이언트 정보를 관리해야 합니다.  

보조 사이트를 설치하지 않으려고 하고 원격 위치에 클라이언트가 있는 경우 다음 옵션을 고려합니다.  

- Windows BranchCache와 같은 피어 투 피어 기술을 사용합니다.  

- 대역폭 제어 및 예약에 위한 배포 지점 사용을 사용합니다.   

이러한 콘텐츠 관리 옵션은 보조 사이트의 유무에 관계없이 사용하며, Configuration Manager 인프라의 크기를 줄이는 데 도움이 됩니다. Configuration Manager의 콘텐츠 관리 옵션에 대한 자세한 내용은 [콘텐츠 관리 옵션을 사용할 시기 결정](#BKMK_ChooseSecondaryorDP)을 참조하세요.  


다음 정보를 사용하여 보조 사이트를 설치할 시기를 결정할 수 있습니다.  

- SQL Server의 로컬 인스턴스를 사용할 수 없는 경우 보조 사이트 서버에서 사이트 설치 중에 SQL Server Express를 자동으로 설치합니다.  

- 보조 사이트 설치는 컴퓨터에서 직접 설치를 실행하는 대신 Configuration Manager 콘솔에서 시작됩니다.  

- 보조 사이트는 사이트 데이터베이스의 정보 하위 집합을 사용합니다. 이 동작은 SQL에서 부모 기본 사이트와 보조 사이트 간에 복제하는 데이터의 양을 줄입니다.  

- 보조 사이트는 공통 부모 기본 사이트를 공유하는 다른 보조 사이트로 파일 기반 콘텐츠를 라우팅하는 기능을 지원합니다.  

- 보조 사이트 설치는 관리 지점 및 배포 지점 사이트 시스템 역할을 보조 사이트 서버에 자동으로 설치합니다.  



##  <a name="BKMK_ChooseSecondaryorDP"></a> 콘텐츠 관리 옵션을 사용할 시기 결정  

원격 네트워크 위치에 클라이언트가 있는 경우 기본 사이트 또는 보조 사이트 대신 하나 이상의 콘텐츠 관리 옵션을 사용하는 것이 좋습니다. 다음 옵션을 사용하면 경우에 따라 사이트를 설치할 필요가 없습니다.  

- Windows 10 배달 최적화  

- Configuration Manager 피어 캐시  

- Windows BranchCache  

- 대역폭 제어에 대한 배포 지점 구성  

- 수동으로 배포 지점에 콘텐츠 복사(콘텐츠 사전 준비)  


다음 조건 중 하나라도 충족되면 다른 사이트를 설치하는 대신 배포 지점을 배포하는 것이 좋습니다.  

- 네트워크 대역폭이 원격 위치의 클라이언트 컴퓨터에서 기본 사이트의 관리 지점과 통신하는 데 충분합니다. 클라이언트에서 관리 지점과 통신하여 클라이언트 정책을 다운로드하고, 인벤토리를 보내며, 보고 상태를 보내고, 검색 정보를 보냅니다.  

- BITS(Background Intelligent Transfer Service)에서 네트워크 요구 사항에 충분한 대역폭 제어를 제공하지 않습니다.  

Configuration Manager의 콘텐츠 관리 옵션에 대한 자세한 내용은 [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)을 참조하세요.  



##  <a name="bkmk_beyond"></a> 계층 토폴로지 외의 다른 사항들  

초기 계층 구조 토폴로지와 함께 다음 질문도 고려합니다.  

- 계층 구조의 여러 사이트에서 서비스 또는 기능을 제공하는 사이트 시스템 역할은 무엇인가요?  

- 인프라에서 계층 구조 전체의 구성 및 기능을 관리하려면 어떻게 하나요?  


별도의 문서에서 다루는 일반적인 고려 사항은 다음과 같습니다. 이 정보는 계층 구조 디자인에서 영향을 주거나 받는 데 중요합니다.  

- [컴퓨터 및 장치 관리](/sccm/core/clients/manage/manage-clients)를 준비할 때 장치가 온-프레미스 또는 클라우드에 있는지, 아니면 사용자 소유 장치(BYOD)가 포함되는지 고려합니다. 또한 여러 관리 옵션을 지원하는 디바이스를 관리하는 방법도 고려합니다. 예를 들어 Configuration Manager를 사용하거나 Microsoft Intune과 통합하여 Windows 10 디바이스를 관리합니다. 자세한 내용은 [디바이스 관리 솔루션 선택](/sccm/core/plan-design/choose-a-device-management-solution)을 참조하세요.  

- 사용 가능한 네트워크 인프라에서 원격 위치 간의 데이터 흐름에 영향을 주는 방식을 이해합니다. 자세한 내용은 [네트워크 환경 준비](/sccm/core/plan-design/network/configure-firewalls-ports-domains)를 참조하세요. 또한 사용자 및 디바이스의 지리적 위치와 온-프레미스 네트워크 또는 인터넷을 통해 인프라에 액세스하는지 여부도 고려합니다.  

- 콘텐츠 인프라에서 배포하는 콘텐츠를 관리하는 디바이스에 효율적으로 배포하도록 계획합니다. 이 콘텐츠는 애플리케이션, 소프트웨어 업데이트 또는 운영 체제일 수 있습니다. 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  

- 사용하려는 [Configuration Manager의 특징과 기능](/sccm/core/plan-design/changes/features-and-capabilities)을 결정합니다. 기능마다 서로 다른 사이트 시스템 역할 또는 Windows 인프라가 필요합니다. 다중 사이트 계층 구조에서 네트워크 및 서버 리소스를 가장 효율적으로 사용할 수 있도록 배포 위치를 결정합니다.  

- PKI(공개 키 인프라) 사용을 포함하여 데이터 및 디바이스에 대한 보안을 고려합니다. 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  


사이트별 구성과 관련하여 다음 리소스를 검토합니다.  

- [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)  

- [사이트 데이터베이스 계획](/sccm/core/plan-design/hierarchy/plan-for-the-site-database)  

- [사이트 시스템 서버 및 사이트 시스템 역할에 대한 계획](/sccm/core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles)  

- [보안 계획](/sccm/core/plan-design/security/plan-for-security)  

- 사이트 내에서 콘텐츠를 배포할 때[Managing network bandwidth](/sccm/core/plan-design/hierarchy/manage-network-bandwidth)  


사이트 및 계층 구조에 대한 구성 고려 사항  

- 사이트 및 계층 구조에 대한 [고가용성 옵션](/sccm/protect/understand/high-availability-options)

- [Active Directory 스키마 확장](/sccm/core/plan-design/network/extend-the-active-directory-schema) 및 [사이트 데이터를 게시](/sccm/core/servers/deploy/configure/publish-site-data)하도록 사이트 구성  

- [사이트 간 데이터 전송](/sccm/core/servers/manage/data-transfers-between-sites)  

- [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)  

- [인터넷에서 클라이언트 관리](/sccm/core/clients/manage/manage-clients-internet)  

