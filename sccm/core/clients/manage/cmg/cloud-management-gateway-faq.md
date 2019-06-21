---
title: CMG FAQ
description: 이 아티클을 사용하여 클라우드 관리 게이트웨이에 관련된 FAQ 정리
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 06/19/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 4c1a128d-22fb-49f1-8e0b-36513a8dc117
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6a7b4350cbd220393318eb6c8b5eae2a5bee05fc
ms.sourcegitcommit: 3936b869d226cea41fa0090e2cbc92bd530db03a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67286795"
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



## <a name="next-steps"></a>다음 단계

- [클라우드 관리 게이트웨이에 대한 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이 크기 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
