---
title: 사이트 서버 및 원격 사이트 시스템에서의 TLS(전송 계층 보안) 1.2 사용 설정
titleSuffix: Configuration Manager
description: Configuration Manager 사이트 서버에 대해 TLS 1.2를 사용하도록 설정하는 방법에 대한 정보입니다.
ms.date: 12/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 0ce9b428-cb0f-46f3-bf69-c465e6623d6f
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 148906504b77179757b38a87712d6629cc4b85d2
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198927"
---
# <a name="how-to-enable-tls-12-on-the-site-servers-and-remote-site-systems"></a>사이트 서버 및 원격 사이트 시스템에서의 TLS 1.2 사용 방법

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 환경에 대해 TLS 1.2를 사용 설정할 때는 먼저 [클라이언트에 대한 TLS 1.2 사용 설정](/sccm/core/plan-design/security/enable-tls-1-2-client)부터 시작합니다. 그리고 두 번째로는 사이트 서버와 원격 사이트의 시스템에서 TLS 1.2를 사용 설정합니다. 마지막으로는 서버 측에서 오래된 프로토콜을 사용하지 않도록 설정할 수도 있으므로 그 전에 클라이언트에서 사이트 시스템으로의 통신을 테스트합니다. 사이트 서버와 원격 사이트의 시스템에서 TLS 1.2를 사용 설정하려면 다음 작업이 필요합니다.

- TLS 1.2가 운영 체제 수준의 SChannel용 프로토콜로서 사용 설정되었는지의 여부 확인
- TLS 1.2 지원을 위한 .NET Framework 업데이트 및 구성
- SQL Server 및 클라이언트 구성 요소 업데이트
- WSUS(Windows Server Update Services) 업데이트

특정 Configuration Manager 기능 및 시나리오의 종속성에 대한 자세한 내용은 [TLS 1.2 사용 설정 소개](/sccm/core/plan-design/security/enable-tls-1-2)를 참조하세요. 

## <a name="bkmk_protocol"></a> TLS 1.2가 운영 체제 수준의 SChannel용 프로토콜로서 사용 설정되었는지의 여부 확인

[!INCLUDE [Enable TLS 1.2 protocol as a security provider](includes/enable-tls-1-2-protocol-security-provider.md)]

## <a name="bkmk_net"></a> TLS 1.2 지원을 위한 .NET Framework 업데이트 및 구성

[!INCLUDE [Update and configure the .NET framework to support TLS 1.2](includes/update-net-framework-to-support-tls-1-2.md)]


## <a name="bkmk_sql"></a> SQL Server 및 클라이언트 구성 요소 업데이트

Microsoft SQL Server 2016 이상은 TLS 1.1 및 TLS 1.2를 지원합니다. 이전 버전 및 종속 라이브러리를 업데이트해야 할 수 있습니다. 자세한 내용은 [KB 3135244: Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)을 참조하세요.

보조 사이트 서버는 적어도 SQL Server 2016 Express 서비스 팩 2(13.2.50.26) 이상을 사용해야 합니다.

### <a name="bkmk_sql-client"></a> SQL Server Native Client

> [!NOTE]
> [KB 3135244](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)에서도 SQL Server 클라이언트 구성 요소의 요구 사항을 설명합니다.

또한 SQL Server Native Client를 적어도 SQL 2012 SP4(11.*.7001.0) 버전으로 업데이트해야 합니다. 버전 1810부터 이 요구 사항은 [필수 구성 요소 검사(경고)](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client)입니다.

Configuration Manager는 다음 사이트 시스템 역할에서 SQL Server Native Client를 사용합니다.

- 사이트 데이터베이스 서버
- 사이트 서버: 중앙 관리 사이트, 주 사이트 또는 보조 사이트
- 관리 지점
- 디바이스 관리 지점
- 상태 마이그레이션 지점
- SMS 공급자
- 소프트웨어 업데이트 지점
- 멀티캐스트 사용 배포 지점
- Asset Intelligence 업데이트 서비스 지점
- 보고 서비스 지점
- 애플리케이션 카탈로그 웹 서비스
- 등록 지점
- Endpoint Protection 지점
- 서비스 연결 지점
- 인증서 등록 지점
- 데이터 웨어하우스 서비스 지점


## <a name="bkmk_wsus"></a> Windows Server Update Services(WSUS) 업데이트

이전 버전의 WSUS에서 TLS 1.2를 지원하려면 WSUS 서버에서 다음 업데이트를 설치하세요.

- Windows Server 2012를 실행하는 WSUS 서버의 경우 [업데이트 4022721](https://support.microsoft.com/help/4022721) 이상의 롤업 업데이트를 설치합니다.
- Windows Server 2012 R2를 실행하는 WSUS 서버의 경우 [업데이트 4022720](https://support.microsoft.com/help/4022720) 이상의 롤업 업데이트를 설치합니다.

Windows Server 2016부터는 TLS 1.2가 WSUS에 대해 기본적으로 지원됩니다.  TLS 1.2 업데이트는 Windows Server 2012 및 Windows Server 2012 R2 WSUS 서버에서만 필요합니다.

## <a name="next-steps"></a>다음 단계

- [TLS 1.2 사용 설정 시의 일반 문제](/sccm/core/plan-design/security/enable-tls-1-2-troubleshoot)
