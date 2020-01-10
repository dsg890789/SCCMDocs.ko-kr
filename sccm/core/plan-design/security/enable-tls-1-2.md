---
title: TLS(전송 계층 보안) 1.2 사용 설정 개요
titleSuffix: Configuration Manager
description: Configuration Manager에 대해 TLS 1.2 사용 설정 방법을 간략하게 설명합니다.
ms.date: 12/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 31de47c9-891b-4de7-8d5e-fbbc1bff7c60
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: ccb9c241f79268b5571d3b18fa36783a092a0781
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799202"
---
# <a name="how-to-enable-tls-12"></a>TLS 1.2를 사용하도록 설정하는 방법

*적용 대상: Configuration Manager(현재 분기)*

TLS(전송 계층 보안)는 SSL(보안 소켓 계층)과 마찬가지로 네트워크에서 전송되는 데이터를 보호하고자 마련된 암호화 프로토콜입니다. 이 아티클에서는 Configuration Manager 보안 통신에서 TLS 1.2 프로토콜을 사용하도록 설정하는 데 필요한 단계를 설명합니다. 또한 이 아티클에서는 일반적으로 사용되는 구성 요소의 업데이트 요건과 공통적 문제 해결 방안도 소개합니다.

## <a name="enabling-tls-12"></a>TLS 1.2 사용 설정

Configuration Manager는 보안 통신을 위해 여러 다양한 구성 요소를 활용합니다. 특정 연결에 사용되는 프로토콜은 클라이언트 측과 서버 측의 관련 구성 요소가 가진 기능에 따라 좌우됩니다. 한 가지 구성 요소가 오래되었거나 구성이 올바르지 않다면 오래되고 덜 안전한 프로토콜이 통신에 사용될 수 있습니다. 모든 보안 통신에서 TLS 1.2를 지원할 수 있도록 Configuration Manager를 올바르게 사용 설정하려면 모든 필수 구성 요소에 대해 TLS 1.2를 사용하도록 설정해야 합니다. 필수 구성 요소는 환경 및 사용하는 Configuration Manager 기능에 따라 다릅니다.

> [!IMPORTANT]
> 클라이언트(특히 이전 버전의 Windows)에서 이 프로세스를 시작합니다. Configuration Manager 서버에서 TLS 1.2를 사용하고 오래된 프로토콜은 사용하지 않도록 설정하기 전에 모든 클라이언트가 TLS 1.2를 지원하는지 확인합니다. 그렇지 않으면 클라이언트는 서버와 통신할 수 없으며 분리될 수 있습니다.


## <a name="tasks-for-configuration-manager-clients-site-servers-and-remote-site-systems"></a>Configuration Manager 클라이언트, 사이트 서버, 원격 사이트 시스템 관련 작업

보안 통신에서 Configuration Manager에 영향을 주는 구성 요소에 대해 TLS 1.2를 사용 설정하려면 클라이언트 측과 사이트 서버 측 양쪽에서 여러 작업을 수행해야 합니다.

### <a name="enable-tls-12-for-configuration-manager-clients"></a>Configuration Manager 클라이언트에 대한 TLS 1.2 사용 설정

- [Windows 8.0, Windows Server 2012(R2 이외) 및 이전 버전에서 Windows 및 WinHTTP 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_winhttp)
- [TLS 1.2가 운영 체제 수준의 SChannel용 프로토콜로서 사용 설정되었는지의 여부 확인](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_protocol)
- [TLS 1.2 지원을 위한 .NET Framework 업데이트 및 구성](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)


### <a name="enable-tls-12-for-configuration-manager-site-servers-and-remote-site-systems"></a>Configuration Manager 사이트 서버 및 원격 사이트 시스템에 대한 TLS 1.2 사용 설정

- [TLS 1.2가 운영 체제 수준의 SChannel용 프로토콜로서 사용 설정되었는지의 여부 확인](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_protocol)
- [TLS 1.2 지원을 위한 .NET Framework 업데이트 및 구성](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_net)
- [SQL Server 및 SQL Native Client 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql)
- [WSUS(Windows Server Update Services) 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_wsus)


## <a name="features-and-scenario-dependencies"></a>기능 및 시나리오 종속성

이 섹션에서는 특정 Configuration Manager 기능 및 시나리오에 대한 종속성을 설명합니다. 다음 단계를 확인하려면 사용자 환경에 적용되는 항목을 찾습니다.

|기능 또는 시나리오|작업 업데이트|
|--- |--- |
|사이트 서버(중앙, 주 또는 보조)| - [.NET Framework 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server##bkmk_net)<br/> - 강력한 암호화 설정 확인|
|사이트 데이터베이스 서버|[SQL Server 및 해당 클라이언트 구성 요소 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql)|
|보조 사이트 서버|규격 버전의 SQL Express로 [SQL Server 및 해당 클라이언트 구성 요소를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql)|
|사이트 시스템 역할| - [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_net)하고 강력한 암호화 설정 확인 <br/> - [SQL Server 및 해당 클라이언트 구성 요소](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql)를 필요로 하는 역할에서 업데이트([SQL Server Native Client](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql-client) 포함)|
|보고 서비스 지점|- [.NET Framework](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_net)를 사이트 서버, SQL Reporting Services 서버 및 콘솔이 있는 모든 컴퓨터에서 업데이트<br/> - 필요에 따라 SMS_Executive 서비스 다시 시작|
|소프트웨어 업데이트 지점|[WSUS 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_wsus)|
|클라우드 관리 게이트웨이|[TLS 1.2 적용](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway#bkmk_tls)|
|Configuration Manager 콘솔| - [.NET Framework 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)<br/> - 강력한 암호화 설정 확인|
|HTTPS 사이트 시스템 역할이 있는 구성 관리자 클라이언트|[WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 Windows 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_winhttp)|
|소프트웨어 센터| - [.NET Framework 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)<br/> - 강력한 암호화 설정 확인|
|Windows 7 클라이언트| 서버 구성 요소에서 TLS 1.2를 사용하도록 설정하기 ‘전에’ [WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 Windows를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_winhttp)합니다.  먼저 서버 구성 요소에서 TLS 1.2를 사용하도록 설정하는 경우 이전 버전의 클라이언트를 분리할 수 있습니다.|

## <a name="frequently-asked-questions"></a>자주 묻는 질문

### <a name="why-use-tls-12-with-configuration-manager"></a>Configuration Manager에서 TLS 1.2를 사용하는 이유

TLS 1.2는 SSL 2.0, SSL 3.0, TLS 1.0, and TLS 1.1 등의 이전 암호화 프로토콜보다 안전합니다. 기본적으로 TLS 1.2는 네트워크에서 전송되는 데이터를 더욱 안전하게 보호합니다.

### <a name="where-does-configuration-manager-use-encryption-protocols-like-tls-12"></a>Configuration Manager에서 TLS 1.2 같은 암호화 프로토콜을 사용하는 이유는 무엇입니까?

Configuration Manager에서 TLS 1.2 같은 암호화 프로토콜을 사용하는 분야는 기본적으로 다섯 가지입니다.

- 첫 번째는 IIS 기반 사이트 서버 역할이 HTTPS를 사용하도록 구성될 경우의 클라이언트에서 해당 역할로의 통신입니다. 이러한 역할의 예로는 배포 지점, 소프트웨어 업데이트 지점, 관리 지점이 포함됩니다.
- 두 번째는 관리 지점, SMS Executive, SMS 공급자와 SQL의 통신입니다. SQL 통신은 Configuration Manager에서 항상 암호화합니다.
- 세 번째는 WSUS가 HTTPS를 사용하도록 구성될 경우의 사이트 서버에서 WSUS로의 통신입니다.
- 네 번째는 SSRS(SQL Reporting Services)가 HTTPS를 사용하도록 구성될 경우의 Configuration Manager에서 SSRS로의 통신입니다.
- 다섯 번째는 인터넷 기반 서비스로의 모든 연결입니다. 그 사례로는 Microsoft Update의 업데이트 메타데이터 동기화, 서비스 연결점 동기화, CMG(클라우드 관리 게이트웨이)가 포함됩니다.

### <a name="what-determines-which-encryption-protocol-is-used"></a>사용될 암호화 프로토콜은 무엇에 따라 결정됩니까?

HTTPS는 항상 암호화된 대화의 클라이언트와 서버 양쪽에서 지원되는 가장 높은 버전의 프로토콜을 협상합니다. 연결 설정 시 클라이언트는 사용 가능한 가장 높은 버전의 프로토콜의 서버로 메시지를 보냅니다. 서버에서 동일한 버전을 지원할 경우에는 해당 버전을 사용하는 메시지를 보냅니다. 이처럼 협상된 버전은 연결에 사용되는 버전입니다. 서버에서 클라이언트 제공 버전을 지원하지 않을 경우에는 서버 메시지에서 사용 가능한 가장 높은 버전을 지정합니다. TLS 핸드셰이크 프로토콜에 대한 자세한 내용은 [TLS를 사용한 보안 세션 설정](https://docs.microsoft.com/windows/win32/secauthn/tls-handshake-protocol#establishing-a-secure-session-by-using-tls)을 참조하세요.

### <a name="what-determines-which-protocol-version-the-client-and-server-can-use"></a>클라이언트와 서버에서 사용 가능한 프로토콜 버전은 무엇에 따라 결정됩니까?

사용될 프로토콜 버전은 일반적으로 다음 항목에 따라 결정됩니다.

- 애플리케이션에서 협상할 특정 프로토콜 버전을 지정할 수 있습니다.
  - 모범 사례를 보면 애플리케이션 수준의 특정 프로토콜 버전 하드 코딩은 지양하고 구성 요소 및 운영 체제 프로토콜 수준으로 정의된 구성을 따르도록 안내되어 있습니다.
  - Configuration Manager는 이 모범 사례를 따릅니다.
- .NET Framework로 작성된 애플리케이션의 경우에는 기본 프로토콜 버전이 프로토콜 컴파일링 기반 프레임워크의 버전에 따라 달라집니다.  
  - 4\.6.3 이전의 .NET 버전은 기본적으로 협상을 위한 프로토콜 목록에서 TLS 1.1과 1.2를 포함하지 않았습니다.
- HTTPS 통신에 WinHTTP를 사용하는 애플리케이션은 Configuration Manager와 마찬가지로 운영 체제, 패치 수준, 프로토콜 버전 지원을 위한 구성에 따라 달라집니다.


## <a name="additional-resources"></a>추가 리소스

- [암호화 컨트롤 기술 참조](cryptographic-controls-technical-reference.md)
- [.NET Framework에 대한 TLS(전송 계층 보안) 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry)
- [KB 3135244: Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)

## <a name="next-steps"></a>다음 단계

- [클라이언트에서의 TLS 1.2 사용 설정](/sccm/core/plan-design/security/enable-tls-1-2-client)
- [사이트 서버에서의 TLS 1.2 사용 설정](/sccm/core/plan-design/security/enable-tls-1-2-server)
