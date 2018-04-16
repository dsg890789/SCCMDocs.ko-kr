---
title: CMG FAQ
description: 이 아티클을 사용하여 클라우드 관리 게이트웨이에 관련된 FAQ 정리
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 4c1a128d-22fb-49f1-8e0b-36513a8dc117
ms.openlocfilehash: 8615b28735165650a0ec25e3d3114263835803d6
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2018
---
# <a name="frequently-asked-questions-about-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 FAQ

*적용 대상: System Center Configuration Manager(현재 분기)*

이 아티클에서는 클라우드 관리 게이트웨이에 관련된 FAQ에 대답합니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.


## <a name="frequently-asked-questions"></a>질문과 대답

### <a name="what-certificates-do-i-need"></a>어떤 인증서가 필요한가요?

자세한 내용은 [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)를 참조하세요.


### <a name="do-i-need-azure-expressroute"></a>Azure ExpressRoute가 필요한가요?

[Azure ExpressRoute](/azure/expressroute/expressroute-introduction)를 통해 온-프레미스 네트워크를 Microsoft 클라우드로 확장할 수 있습니다. Configuration Manager 클라우드 관리 게이트웨이에 대해 ExpressRoute 또는 이러한 다른 가상 네트워크 연결이 필요하지 않습니다. 클라우드 관리 게이트웨이의 디자인을 통해 인터넷 기반 클라이언트가 추가 네트워크 구성 없이 Azure 서비스부터 온-프레미스 사이트 시스템까지 통신할 수 있습니다. 자세한 내용은 [클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을 참조하세요.

조직에서 ExpressRoute를 사용하는 경우 가장 좋은 보안 방법은 클라우드 관리 게이트웨이에 대한 Azure 구독을 격리하는 것입니다. 이 구성을 통해 클라우드 관리 게이트웨이 서비스가 이렇게 실수로 연결되지 않도록 합니다. 자세한 내용은 [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)를 참조하세요.


### <a name="do-i-need-to-maintain-the-azure-virtual-machines"></a>Azure 가상 머신을 유지 관리해야 하나요?

유지 관리가 필요하지 않습니다. 클라우드 관리 게이트웨이의 설계는 Azure PaaS(platform as a service)를 사용하는 것입니다. 제공한 구독을 사용하여 Configuration Manager는 필요한 VM(가상 머신), 저장소 및 네트워킹을 만듭니다. Azure에서는 가상 머신을 보호하고 업데이트합니다. 이러한 VM은 IaaS(infrastructure as a service)의 경우처럼 온-프레미스 환경의 일부가 아닙니다. 클라우드 관리 게이트웨이는 클라우드로 Configuration Manager 환경을 확장하는 PaaS입니다. 


### <a name="im-already-using-ibcm-if-i-add-cmg-how-do-clients-behave"></a>IBCM을 이미 사용하고 있습니다. CMG를 추가하면 클라이언트가 어떻게 될까요?

이미 IBCM([인터넷 기반 클라이언트 관리](/sccm/core/clients/manage/plan-internet-based-client-management))을 배포한 경우 클라우드 관리 게이트웨이도 배포할 수 있습니다. 클라이언트는 두 서비스에 대한 정책을 모두 수신합니다. 인터넷에서 로밍하는 경우 임의로 선택하고 다음 인터넷 기반 서비스 중 하나를 사용합니다.


## <a name="next-steps"></a>다음 단계

- [클라우드 관리 게이트웨이에 대한 계획](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이에 대한 보안 및 개인 정보](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [클라우드 관리 게이트웨이 크기 및 크기 조정 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)