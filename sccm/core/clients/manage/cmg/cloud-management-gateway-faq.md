---
title: CMG FAQ
titleSuffix: Configuration Manager
description: 이 아티클을 사용하여 클라우드 관리 게이트웨이에 관련된 FAQ 정리
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 07/05/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 4c1a128d-22fb-49f1-8e0b-36513a8dc117
ms.collection: M365-identity-device-management
ms.openlocfilehash: 010cf8b244290090b8bb2143b0d280bd5c0fd4b4
ms.sourcegitcommit: b62de6c9cb1bc3e4c9ea5ab5ed3355d83e3a59bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894134"
---
# <a name="frequently-asked-questions-about-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 FAQ

*적용 대상: System Center Configuration Manager(현재 분기)*

이 아티클에서는 클라우드 관리 게이트웨이에 관련된 FAQ에 대답합니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.


## <a name="frequently-asked-questions"></a>자주 묻는 질문

### <a name="what-certificates-do-i-need"></a>어떤 인증서가 필요한가요?

자세한 내용은 [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)를 참조하세요.


### <a name="do-i-need-azure-expressroute"></a>Azure ExpressRoute가 필요한가요?

아니요. [Azure ExpressRoute](/azure/expressroute/expressroute-introduction)를 통해 온-프레미스 네트워크를 Microsoft 클라우드로 확장할 수 있습니다. Configuration Manager 클라우드 관리 게이트웨이에 대해 ExpressRoute 또는 이러한 다른 가상 네트워크 연결이 필요하지 않습니다. 클라우드 관리 게이트웨이의 디자인을 통해 인터넷 기반 클라이언트가 추가 네트워크 구성 없이 Azure 서비스부터 온-프레미스 사이트 시스템까지 통신할 수 있습니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.

<!-- SCCMDocs#1659 -->

### <a name="do-i-need-to-maintain-the-azure-virtual-machines"></a>Azure 가상 머신을 유지 관리해야 하나요?

유지 관리가 필요하지 않습니다. 클라우드 관리 게이트웨이의 설계는 Azure PaaS(platform as a service)를 사용하는 것입니다. 제공한 구독을 사용하여 Configuration Manager는 필요한 VM(가상 머신), 스토리지 및 네트워킹을 만듭니다. Azure에서는 가상 머신을 보호하고 업데이트합니다. 이러한 VM은 IaaS(infrastructure as a service)의 경우처럼 온-프레미스 환경의 일부가 아닙니다. 클라우드 관리 게이트웨이는 클라우드로 Configuration Manager 환경을 확장하는 PaaS입니다. 자세한 내용은 [PaaS 배포 보호](/azure/security/security-paas-deployments)를 참조하세요.


### <a name="how-can-i-ensure-service-continuity-during-service-updates"></a>서비스 업데이트 중에 서비스 연속성을 보장하려면 어떻게 해야 하나요?

두 개 이상의 인스턴스를 포함하도록 CMG를 확장하면 Azure에서 도메인 자동 업데이트의 이점을 누릴 수 있습니다. [클라우드 서비스 업데이트 방법](/azure/cloud-services/cloud-services-update-azure-service)을 참조하세요.


### <a name="im-already-using-ibcm-if-i-add-cmg-how-do-clients-behave"></a>IBCM을 이미 사용하고 있습니다. CMG를 추가하면 클라이언트가 어떻게 될까요?

이미 IBCM([인터넷 기반 클라이언트 관리](/sccm/core/clients/manage/plan-internet-based-client-management))을 배포한 경우 클라우드 관리 게이트웨이도 배포할 수 있습니다. 클라이언트는 두 서비스에 대한 정책을 모두 수신합니다. 인터넷에서 로밍하는 경우 임의로 선택하고 다음 인터넷 기반 서비스 중 하나를 사용합니다.


### <a name="do-the-user-accounts-have-to-be-in-the-same-azure-subscription-as-the-subscription-that-hosts-the-cmg-cloud-service"></a>사용자 계정이 CMG 클라우드 서비스를 호스팅하는 구독과 동일한 Azure 구독에 있어야 하나요?
<!--SCCMDocs-pr issue #2873-->
사용자 환경에 하나를 초과하는 구독이 있는 경우 Azure 클라우드 서비스를 호스팅하는 모든 구독에 CMG를 배포할 수 있습니다. 

이 문제는 다음과 같은 시나리오에서 일반적입니다.  

- 고유한 테스트 및 프로덕션 Active Directory와 Azure AD 환경이 있지만 단 하나의 중앙 집중화된 Azure 호스팅 구독이 있는 경우  

- Azure를 사용하면 서로 다른 팀 간에 유기적으로 성장  

Resource Manager 배포를 사용하는 경우 연결된 Azure AD 테넌트를 등록합니다. 이 연결을 통해 Configuration Manager가 Azure에 CMG를 만들고 배포하고 관리하도록 인증할 수 있습니다.  

CMG를 통해 관리되는 디바이스 및 사용자용 Azure AD 인증을 사용하는 경우 해당 Azure AD 테넌트를 등록합니다. 클라우드 관리를 위한 Azure 서비스에 대한 자세한 내용은 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)을 참조하세요. 각 Azure AD 테넌트를 등록하는 경우 단일 CMG가 호스팅 위치에 관계 없이 여러 테넌트에 대한 Azure AD 인증을 제공할 수 있습니다.

### <a name="how-does-cmg-affect-my-clients-connected-via-vpn"></a>CMG는 VPN을 통해 연결된 클라이언트에 어떤 영향을 주나요?

VPN 통해 사용자 환경에 연결하는 로밍 클라이언트는 일반적으로 인트라넷 연결로 검색됩니다. 관리 지점 및 배포 지점과 같은 온-프레미스 인프라에 연결하려고 시도합니다. 일부 고객은 VPN을 통해 연결된 경우에도 클라우드 서비스에서 이러한 로밍 클라우드를 관리하는 것을 선호합니다. 1902 버전부터 CMG를 경계 그룹과 연결합니다. 이 작업은 이러한 클라이언트가 온-프레미스 사이트 시스템을 사용하지 못하게 합니다. 자세한 내용은 [경계 그룹 구성](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#configure-boundary-groups)을 참조하세요.

### <a name="if-i-enable-a-cmg-will-my-clients-only-connect-to-the-cmg-enabled-management-point-when-theyre-connected-to-the-intranet"></a>CMG를 활성화하면 내 클라이언트가 인트라넷에 연결되어 있을 때 CMG 지원 관리 지점에만 연결되나요?

CMG를 통해 전송되는 중요한 트래픽을 보호하려면 HTTPS 관리 지점을 구성하거나 향상된 HTTP를 사용합니다.

CMG를 배포하고 CMG 지원 관리 지점에서 HTTPS 통신에 PKI 인증서를 사용하는 경우, 관리 지점 속성에서 **인터넷 전용 클라이언트 허용** 옵션을 선택합니다. 이 설정은 내부 클라이언트가 사용자 환경에서 HTTP 관리 지점을 계속 사용하도록 합니다.

향상된 HTTP를 사용하는 경우 이 설정을 구성할 필요가 없습니다. 클라이언트는 CMG 지원 관리 지점에 직접 통신할 때 HTTP를 계속 사용합니다. 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- [클라우드 관리 게이트웨이에 대한 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이 크기 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
