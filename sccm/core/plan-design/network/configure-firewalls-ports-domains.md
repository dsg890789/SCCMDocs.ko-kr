---
title: 네트워크 인프라
titleSuffix: Configuration Manager
description: Configuration Manager 통신을 준비하기 위해 방화벽, 포트 및 도메인을 설정합니다.
ms.date: 06/19/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 60a24e06d650b0e25007fb8490eb0c7d8c1996a1
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67285608"
---
# <a name="network-infrastructure-considerations-for-configuration-manager"></a>Configuration Manager의 네트워크 인프라 고려 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 지원하도록 네트워크를 준비하려면 일부 인프라 구성 요소를 구성해야 할 수 있습니다. 예를 들어 Configuration Manager에서 사용하는 통신을 전달하도록 방화벽 포트를 열어야 합니다.  

## <a name="ports-and-protocols"></a>포트 및 프로토콜

Configuration Manager 기능에 따라 사용하는 네트워크 포트가 다릅니다. 일부 포트는 필수이며 일부는 사용자 지정할 수 있습니다.

대부분의 Configuration Manager 통신에서는 HTTP용 포트 80 또는 HTTPS용 443과 같은 일반 포트를 사용합니다. 일부 사이트 시스템 역할은 사용자 지정 웹 사이트 및 사용자 지정 포트 사용을 지원합니다. 자세한 내용은 [사이트 시스템 서버용 웹 사이트](/sccm/core/plan-design/network/websites-for-site-system-servers)를 참조하세요.

Configuration Manager를 배포하기 전에 사용할 포트를 식별하고 방화벽을 필요에 맞게 설정합니다.

Configuration Manager를 설치한 후 포트를 변경해야 하는 경우에는 디바이스와 네트워크에서 방화벽을 업데이트해야 합니다. Configuration Manager에서 포트의 구성도 변경해야 합니다.

자세한 내용은 다음 아티클을 참조하세요.

- [클라이언트 통신 포트를 구성하는 방법](/sccm/core/clients/deploy/configure-client-communication-ports)
- [Configuration Manager에서 사용되는 포트](/sccm/core/plan-design/hierarchy/ports)


## <a name="internet-access-requirements"></a>인터넷 액세스 요구 사항

일부 Configuration Manager 기능이 완벽히 작동하기 위해서는 인터넷 연결이 필요합니다. 조직에서 방화벽 또는 프록시 디바이스를 사용하여 인터넷과의 네트워크 통신을 제한하는 경우 필수 엔드포인트를 허용해야 합니다.

자세한 내용은 [Internet access requirements](/sccm/core/plan-design/network/internet-endpoints)(인터넷 액세스 요구 사항)를 참조하세요.


## <a name="proxy-servers"></a>프록시 서버

여러 사이트 시스템 서버와 클라이언트에 대해 각기 다른 프록시 서버를 지정할 수 있습니다. 사이트 시스템 역할 또는 클라이언트를 설치하거나 나중에 필요에 따라 변경하는 경우 이렇게 구성합니다.

자세한 내용은 [프록시 서버 지원](/sccm/core/plan-design/network/proxy-server-support)을 참조하세요.
