---
title: Active Directory 도메인 지원
titleSuffix: Configuration Manager
description: Active Directory 도메인의 Configuration Manager 사이트 시스템에 대한 요구 사항에 대해 알아봅니다.
ms.date: 10/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8c5a13f8-42d5-4898-b7b6-e594dae8b335
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a04928afc64c16cf5d200abc94008ea29fc73197
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72810773"
---
# <a name="support-for-active-directory-domains-in-configuration-manager"></a>Configuration Manager에서 Active Directory 도메인 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

모든 Configuration Manager 사이트 시스템은 지원되는 Active Directory 도메인의 구성원이어야 합니다. Configuration Manager 클라이언트 컴퓨터는 도메인 구성원 또는 작업 그룹 구성원일 수 있습니다.  

## <a name="requirements-and-limitations"></a>요구 사항 및 제한 사항:

- 도메인 멤버 자격은 경계 네트워크에서 인터넷 기반 클라이언트 관리를 지 원하는 사이트 시스템에도 적용됩니다. (이러한 네트워크를 DMZ, 완충 영역 및 스크린된 서브넷이라고도 합니다.)  

- 사이트 시스템 역할을 호스트하는 컴퓨터에 대해 다음을 변경할 수는 없습니다.  

  - 도메인 멤버 자격(도메인에서 사이트 시스템을 제거한 다음 동일한 도메인에 다시 가입하는 경우 포함).

  - 도메인 이름  

  - 컴퓨터 이름  

  이러한 변경 작업을 수행하기 전에 사이트 시스템 역할을 제거합니다. 사이트 서버를 변경하려면 먼저 사이트를 제거합니다. 또한 [수동 모드에서 사이트 서버](/sccm/core/servers/deploy/configure/site-server-high-availability)를 만드는 것이 좋습니다. 이를 통해 사이트 서버에서 이 변경을 쉽게 관리할 수 있습니다.

- Configuration Manager는 Windows Server 2008 R2 이상에서 도메인 및 포리스트 기능 수준을 지원합니다.<!-- SCCMDocs#1853 -->

## <a name="bkmk_Disjoint"></a> 비연속 네임스페이스

‘비연속 네임스페이스’를 포함하는 도메인에 Configuration Manager 사이트 시스템과 클라이언트를 설치할 수 있습니다.   

비연속 네임스페이스에서 컴퓨터의 주 DNS 접미사는 해당 컴퓨터의 Active Directory DNS 도메인 이름과 일치하지 않습니다. 비연속 네임스페이스의 또 다른 시나리오로는 도메인 컨트롤러의 NetBIOS 도메인 이름이 Active Directory DNS 도메인 이름과 일치하지 않는 경우를 들 수 있습니다.  

### <a name="disjoint-scenarios"></a>비연속 시나리오

다음 섹션에는 비연속 네임스페이스에 대해 지원되는 시나리오가 나와 있습니다.  

#### <a name="scenario-1"></a>시나리오 1

도메인 컨트롤러의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 다릅니다. 도메인의 구성원인 컴퓨터는 비연속일 수도 있고 비연속이 아닐 수도 있습니다.

이 시나리오에서는 도메인 컨트롤러가 비연속입니다. 사이트 서버 및 컴퓨터와 같은 도메인의 구성원인 컴퓨터는 다음에 일치하는 주 DNS 접미사를 사용할 수 있습니다.

- 도메인 컨트롤러의 주 DNS 접미사
- Active Directory DNS 도메인 이름

#### <a name="scenario-2"></a>시나리오 2

도메인 컨트롤러는 비연속이 아니더라도 Active Directory 도메인의 구성원 컴퓨터가 비연속입니다.

이 시나리오에서는 사이트 시스템 컨트롤러의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 다릅니다. 도메인 컨트롤러의 주 DNS 접미사가 Active Directory DNS 도메인 이름과 같습니다. Configuration Manager 클라이언트의 구성원 컴퓨터는 다음과 일치하는 주 DNS 접미사를 사용할 수 있습니다.

- 비연속 사이트 시스템 서버의 주 DNS 접미사
- Active Directory DNS 도메인 이름

### <a name="configure-disjoint-namespace"></a>비연속 네임스페이스 구성

컴퓨터가 비연속 도메인 컨트롤러에 액세스할 수 있도록 하려면 도메인 개체 컨테이너에서 **msDS-AllowedDNSSuffixes** Active Directory 특성을 변경합니다. 두 DNS 접미사를 모두 특성에 추가합니다.  

‘DNS 접미사 검색 목록’이 조직의 모든 DNS 네임스페이스를 포함하는지 확인하려면 분리형 도메인의 각 컴퓨터에 대해 검색 목록을 구성합니다.  네임스페이스 목록에 다음 접미사를 포함합니다.

- 도메인 컨트롤러의 주 DNS 접미사
- DNS 도메인 이름
- Configuration Manager와 통신할 수 있는 다른 서버의 추가 네임스페이스

그룹 정책을 사용하여 **DNS (Domain Name System) 접미사 검색** 목록을 구성할 수 있습니다.  

> [!IMPORTANT]  
> Configuration Manager에서 컴퓨터를 참조하는 경우 해당 주 DNS 접미사를 사용하여 컴퓨터를 입력합니다. 이 접미사는 Active Directory 도메인에 **dnsHostName** 특성으로 등록되어 있는 정규화된 도메인 이름 및 시스템과 연결된 서비스 주체 이름과 일치해야 합니다.  

## <a name="bkmk_SLD"></a> 단일 레이블 도메인

Configuration Manager에서는 다음 기준이 충족될 경우 단일 레이블 도메인의 사이트 시스템 및 클라이언트를 지원합니다.  

- 유효한 최상위 도메인이 있는 비연속 DNS 네임스페이스를 사용하여 Active Directory Domain Services의 단일 레이블 도메인을 구성합니다.  

  **예를 들면 다음과 같습니다.** Contoso의 단일 레이블 도메인이 contoso.com의 DNS에서 비연속 네임스페이스를 포함하도록 구성되어 있습니다. Contoso 도메인의 컴퓨터에 대해 Configuration Manager에서 DNS 접미사를 지정할 때는 “Contoso”가 아닌 “Contoso.com”을 지정합니다.  

- Kerberos 인증을 사용하여 사이트 서버와 시스템 컨텍스트 간의 DCOM(Distributed Component Object Model) 연결을 설정할 수 있어야 합니다.  
