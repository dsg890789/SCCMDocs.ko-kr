---
author: mestew
ms.author: mstewart
ms.prod: configuration-manager
ms.topic: include
ms.date: 12/13/2019
ms.openlocfilehash: 886eed4c3bd9911ffd8ebb0e14b375424c68d56a
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799257"
---
<!--## Enable Transport layer security (TLS) 1.2 protocol as a security provider Note: the heading in in the 2 articles (enable-tls-1-2-client & enable-tls-1-2-server) to better facilitate linking. -->

기본적으로 TLS 1.2가 사용되도록 설정됩니다. 따라서 이 프로토콜을 사용 설정하기 위해 이러한 키를 변경할 필요는 없습니다. 아티클에 제공된 나머지 지침을 수행하고 TLS 1.2가 사용 설정될 때만 작업 환경이 작동하는지 확인한 후에 `Protocols`에서 설정을 변경해 TLS 1.0 및 TLS 1.1을 사용하지 않도록 설정할 수 있습니다.

[.NET Framework를 사용하는 TLS(전송 계층 보안) 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry)에 표시된 대로 `\SecurityProviders\SCHANNEL\Protocols` 레지스트리 하위 키 설정을 확인합니다.

