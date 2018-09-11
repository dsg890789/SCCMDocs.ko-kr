---
title: 인터넷에서 클라이언트 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라우드 관리 게이트웨이 및 인터넷 기반 클라이언트 관리를 사용하여 클라이언트를 관리하는 방법을 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.topic: conceptual
ms.technology: configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 198b044a66bf81ea846d5e4febe655b78c04dd13
ms.sourcegitcommit: 316899b08f2ef372993909e08e069f7edfed1d33
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44111079"
---
# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Configuration Manager를 사용하여 인터넷에서 클라이언트 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

일반적으로 Configuration Manager에서 대부분의 관리 컴퓨터와 서버는 관리 기능을 수행하는 사이트 시스템 서버와 물리적으로 동일한 내부 네트워크에 있습니다. 그러나 인터넷에 연결된 경우 내부 네트워크의 외부에서 클라이언트를 관리할 수 있습니다. 이 기능에서는 클라이언트가 사이트 시스템 서버에 연결하기 위해 VPN을 통해 연결하지 않아도 됩니다.

Configuration Manager는 인터넷에 연결된 클라이언트를 관리하는 다음 두 가지 방법을 제공합니다.

-   클라우드 관리 게이트웨이

-   인터넷 기반 클라이언트 관리


## <a name="cloud-management-gateway"></a>클라우드 관리 게이트웨이

CMG(클라우드 관리 게이트웨이)는 인터넷 기반 클라이언트의 관리를 제공합니다. Microsoft Azure 클라우드 서비스 및 해당 서비스와 통신하는 새로운 사이트 시스템 역할의 조합을 사용합니다. 인터넷 기반 클라이언트는 클라우드 서비스를 사용하여 온-프레미스 Configuration Manager와 통신합니다.

#### <a name="advantages"></a>장점  

-   추가로 인프라에 투자할 필요가 없습니다.  

-   온-프레미스 인프라를 인터넷에 노출하지 않습니다.  

-   서비스를 실행하는 클라우드 가상 컴퓨터는 완벽하게 Azure에서 관리되며 유지 관리할 필요가 없습니다.  

-   Configuration Manager 콘솔에서 쉽게 설정 및 구성됩니다.  

#### <a name="disadvantages"></a>단점  

-   클라우드 구독 비용  

-   관리 데이터가 클라우드 서비스를 통해 전송됩니다.  

자세한 내용은 [클라우드 관리 게이트웨이 계획](plan-cloud-management-gateway.md)을 참조하세요.  



## <a name="internet-based-client-management"></a>인터넷 기반 클라이언트 관리

이 메서드는 클라이언트가 관리 목적으로 통신하는 인터넷 연결 사이트 시스템 서버를 사용합니다. 여기에서는 인터넷 기반 관리를 위해 클라이언트 및 사이트 시스템 서버를 구성해야 합니다.

#### <a name="advantages"></a>장점  

-   클라우드 서비스 종속성이 없습니다.  

-   클라우드 구독과 연결된 추가 비용이 없습니다.  

-   서비스를 제공하는 서버 및 역할의 모든 권한  

#### <a name="disadvantages"></a>단점  

-   추가 인프라 투자가 필요합니다.  

-   추가 인프라의 오버헤드 및 운영 비용  

-   인프라를 인터넷에 노출해야 합니다.  

자세한 내용은 [인터넷 기반 클라이언트 관리 계획](plan-internet-based-client-management.md)을 참조하세요.  
