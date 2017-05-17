---
title: "인터넷에서 클라이언트를 관리 - Configuration Manager | Microsoft 문서"
description: "Configuration Manager에서 클라우드 관리 게이트웨이 및 인터넷 기반 클라이언트 관리를 사용하여 클라이언트를 관리하는 방법을 알아봅니다."
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 3743c80b0c2b5142f3a537ba3855ffd14794d42b
ms.openlocfilehash: 6104107429184f31df12db84089f41df1ef81539
ms.contentlocale: ko-kr
ms.lasthandoff: 01/24/2017

---

# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Configuration Manager를 사용하여 인터넷에서 클라이언트 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

일반적으로 Configuration Manager에서 관리되는 대부분의 컴퓨터와 서버는 관리 기능을 수행하는 사이트 시스템 서버와 물리적으로 동일한 내부 개인 또는 회사 네트워크에 있습니다. 그러나 클라이언트가 가상 개인 네트워크를 통해 사이트 시스템 서버에 연결하도록 요구하지 않고 인터넷에 연결되어 있는 경우 회사 네트워크 외부의 클라이언트 컴퓨터를 관리할 수 있습니다.

Configuration Manager는 인터넷에 연결된 클라이언트를 관리하는 다음 두 가지 방법을 제공합니다.

-   클라우드 관리 게이트웨이

-   인터넷 기반 클라이언트 관리

## <a name="cloud-management-gateway"></a>클라우드 관리 게이트웨이

버전 1610부터Configuration Manager는 클라우드 관리 게이트웨이를 도입했습니다. 이 새로운 방법을 통해 Microsoft Azure에 배포된 클라우드 서비스 및 해당 서비스와 통신하는 새 사이트 시스템 역할의 조합을 사용하여 인터넷 기반 클라이언트를 관리할 수 있습니다. 클라이언트는 서비스를 사용하여 Configuration Manager와 통신합니다.

장점:

-   추가로 인프라에 투자할 필요가 없습니다.

-   온-프레미스 인프라를 인터넷에 노출하지 않습니다.

-   서비스를 실행하는 클라우드 가상 컴퓨터는 완벽하게 Azure에서 관리되며 유지 관리할 필요가 없습니다.

-   Configuration Manager 콘솔에서 쉽게 설정 및 구성됩니다.

단점:

-   클라우드 구독 비용

-   관리 데이터가 클라우드 서비스를 통해 전송됩니다.

자세한 내용은 [클라우드 관리 게이트웨이 계획](plan-cloud-management-gateway.md)을 참조하세요.

## <a name="internet-based-client-management"></a>인터넷 기반 클라이언트 관리

이 방법은 클라이언트가 관리 목적으로 통신하는 인터넷 연결 사이트 시스템 서버를 사용합니다. 이 방법을 사용하려면 인터넷 기반 관리를 위해 클라이언트 및 사이트 시스템 서버를 구성해야 합니다.

장점:

-   클라우드 서비스 종속성이 없습니다.

-   클라우드 구독과 연결된 추가 비용이 없습니다.

-   서비스를 제공하는 서버 및 역할의 모든 권한

단점:

-   추가 인프라 투자가 필요합니다.

-   추가 인프라의 오버헤드 및 운영 비용

-   인프라를 인터넷에 노출해야 합니다.

자세한 내용은 [인터넷 기반 클라이언트 관리 계획](plan-internet-based-client-management.md)을 참조하세요.

