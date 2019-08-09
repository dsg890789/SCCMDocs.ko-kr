---
title: TLS 1.2를 사용하도록 설정하는 방법
titleSuffix: Configuration Manager
description: Configuration Manager용 TLS 1.2를 사용하도록 설정하는 방법에 대한 정보입니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 31de47c9-891b-4de7-8d5e-fbbc1bff7c60
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b58f6d1441d338c121b67754989128944adcc923
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68536563"
---
# <a name="how-to-enable-tls-12"></a>TLS 1.2를 사용하도록 설정하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 개별 구성 요소를 비롯하여 Configuration Manager용 TLS 1.2를 사용하도록 설정하는 방법을 설명합니다. 일반적으로 사용하는 기능의 업데이트 요구 사항과 몇 가지 일반적인 문제 해결 방법도 이 문서에서 설명합니다.

Configuration Manager는 보안 통신을 위해 여러 다양한 구성 요소를 활용합니다. 지정된 연결에 사용하는 프로토콜은 모든 필수 구성 요소의 기능에 따라 좌우됩니다. 한 가지 구성 요소가 오래된 경우 통신에서 오래되고 덜 안전한 프로토콜이 사용될 수 있습니다.

TLS 1.2를 지원하도록 Configuration Manager를 올바르게 사용하도록 설정하려면 먼저 모든 필수 구성 요소에 대해 TLS 1.2를 사용하도록 설정합니다. 필수 구성 요소는 환경 및 사용하는 Configuration Manager 기능에 따라 다릅니다.

클라이언트(특히 이전 버전의 Windows)에서 이 프로세스를 시작합니다. Configuration Manager 서버에서 TLS 1.2를 사용하도록 설정하기 전에 모든 클라이언트가 TLS 1.2를 지원하는지 확인합니다. 그렇지 않으면 클라이언트는 서버와 통신할 수 없으며 분리될 수 있습니다.


## <a name="tasks-for-features-and-scenarios"></a>기능 및 시나리오에 대한 작업

Configuration Manager가 보안 통신을 위해 사용하는 구성 요소에 대해 TLS 1.2를 사용하도록 설정하려면 다음을 수행해야 합니다.

- [TLS 1.2 프로토콜을 보안 공급자로 사용하도록 설정](#enable-tls-12-protocol-as-a-security-provider)
- [TLS 1.2를 지원하도록 .NET Framework 업데이트](#update-net-framework-to-support-tls-12)
- [SQL Server 및 클라이언트 구성 요소 업데이트](#update-sql-server-and-client-components)
- [Windows 8.0, Windows Server 2012 R2 및 이전 버전에서 Windows 및 WinHTTP 업데이트](#update-windows-and-winhttp)
- [WSUS(Windows Server Update Services) 업데이트](#update-windows-server-update-services-wsus)

이 섹션에서는 특정 Configuration Manager 기능 및 시나리오에 대한 종속성을 설명합니다. 다음 단계를 확인하려면 사용자 환경에 적용되는 항목을 찾습니다.

|기능 또는 시나리오|작업 업데이트|
|--- |--- |
|사이트 서버(중앙, 주 또는 보조)| - [.NET Framework 업데이트](#update-net-framework-to-support-tls-12)<br/> - 강력한 암호화 설정 확인|
|사이트 데이터베이스 서버|[SQL Server 및 해당 클라이언트 구성 요소 업데이트](#update-sql-server-and-client-components)|
|보조 사이트 서버|규격 버전의 SQL Express로 [SQL Server 및 해당 클라이언트 구성 요소를 업데이트](#update-sql-server-and-client-components)|
|사이트 시스템 역할| - [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화 설정 확인 <br/> - [SQL Server 및 해당 클라이언트 구성 요소](#update-sql-server-and-client-components)를 필요로 하는 역할에서 업데이트([SQL Server Native Client](#sql-server-native-client) 포함)|
|보고 서비스 지점|- [.NET Framework](#update-net-framework-to-support-tls-12)를 사이트 서버, SQL Reporting Services 서버 및 콘솔이 있는 모든 컴퓨터에서 업데이트<br/> - 필요에 따라 SMS_Executive 서비스 다시 시작|
|소프트웨어 업데이트 지점|[WSUS 업데이트](#update-windows-server-update-services-wsus)|
|클라우드 관리 게이트웨이|[TLS 1.2 적용](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway#bkmk_tls)|
|Configuration Manager 콘솔| - [.NET Framework 업데이트](#update-net-framework-to-support-tls-12)<br/> - 강력한 암호화 설정 확인|
|HTTPS 사이트 시스템 역할이 있는 구성 관리자 클라이언트|[WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 Windows 업데이트](#update-windows-and-winhttp)|
|소프트웨어 센터| - [.NET Framework 업데이트](#update-net-framework-to-support-tls-12)<br/> - 강력한 암호화 설정 확인|
|Windows 7 클라이언트| 서버 구성 요소에서 TLS 1.2를 사용하도록 설정하기 ‘전에’ [WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 Windows를 업데이트](#update-windows-and-winhttp)합니다.  먼저 서버 구성 요소에서 TLS 1.2를 사용하도록 설정하는 경우 이전 버전의 클라이언트를 분리할 수 있습니다.|


## <a name="enable-tls-12-protocol-as-a-security-provider"></a>TLS 1.2 프로토콜을 보안 공급자로 사용하도록 설정

[.NET Framework를 사용하는 TLS(전송 계층 보안) 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry)에 표시된 대로 `\SecurityProviders\SCHANNEL\Protocols` 레지스트리 하위 키 설정을 확인합니다.

> [!NOTE]
> 기본적으로 TLS 1.2가 사용하도록 설정됩니다. 따라서 이 프로토콜을 사용하도록 설정하기 위해 이러한 키를 변경할 필요는 없습니다. 이 문서에 제공된 나머지 지침을 수행하고 TLS 1.2만 사용하도록 설정하여 작업 환경이 잘 작동하는지 확인한 후에 프로토콜에서 설정을 변경하여 TLS 1.0 및 TLS 1.1을 사용하지 않도록 설정할 수 있습니다.


## <a name="update-net-framework-to-support-tls-12"></a>TLS 1.2를 지원하도록 .NET Framework 업데이트

### <a name="determine-net-version"></a>.NET 버전 확인

먼저 .NET 버전 번호를 확인합니다. 자세한 내용은 [설치된 Microsoft .NET Framework의 버전 및 서비스 팩 수준을 확인하는 방법](https://support.microsoft.com/help/318785/how-to-determine-which-versions-and-service-pack-levels-of-the-microso)을 참조하세요.

### <a name="install-net-updates"></a>.NET 업데이트 설치

일부 버전의 .NET Framework에서는 강력한 암호화를 위해 업데이트가 필요할 수 있습니다. 다음 지침을 따르세요.

- .NET Framework 4.6.2 이상은 TLS 1.1 및 TLS 1.2를 지원합니다. 레지스트리 설정을 확인하지만 추가 변경은 필요하지 않습니다.

- TLS 1.1 및 TLS 1.2를 지원하도록 NET Framework 4.6 및 이전 버전을 업데이트합니다. 자세한 내용은 [.NET Framework 버전 및 종속성](https://docs.microsoft.com/dotnet/framework/migration-guide/versions-and-dependencies)을 참조하세요.

- Windows 8.1 또는 Windows Server 2012에서 .NET Framework 4.5.1 또는 4.5.2를 사용하는 경우 관련 업데이트 및 세부 정보도 [다운로드 센터](https://www.microsoft.com/download/details.aspx?id=42883)에서 다운로드할 수 있습니다.

### <a name="configure-for-strong-cryptography"></a>강력한 암호화를 위해 구성

강력한 암호화를 지원하도록 .NET Framework를 구성합니다. `SchUseStrongCrypto` 레지스트리 설정을 `DWORD:00000001`로 설정합니다. 이 값은 RC4 스트림 암호를 사용하지 않도록 설정하며, 값을 적용하기 위해 시스템을 다시 시작해야 합니다. 이 설정에 대한 자세한 내용은 [Microsoft 보안 공지 296038](https://docs.microsoft.com/security-updates/SecurityAdvisories/2015/2960358)을 참조하세요.

네트워크를 통해 TLS 1.2 지원 시스템과 통신하는 모든 컴퓨터에서 다음 레지스트리 키를 설정해야 합니다. 예를 들어, 구성 관리자 클라이언트 또는 사이트 서버에 설치되지 않은 모든 원격 사이트 시스템 역할.

32비트 시스템에서 실행되는 32비트 애플리케이션 또는 64비트 시스템에서 실행되는 64비트 애플리케이션의 경우 다음 하위 키 값을 업데이트합니다.

```Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
```

64비트 시스템에서 실행되는 32비트 애플리케이션의 경우 다음 하위 키 값을 업데이트합니다.

```Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
```

> [!Note]  
> `SchUseStrongCrypto` 설정을 지정하면 .NET에서 TLS 1.1 및 TLS 1.2를 사용할 수 있습니다. `SystemDefaultTlsVersions` 설정을 지정하면 .NET에서 OS 구성을 사용할 수 있습니다. 자세한 내용은 [.NET Framework에 대한 TLS 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls)를 참조하세요.


## <a name="update-sql-server-and-client-components"></a>SQL Server 및 클라이언트 구성 요소 업데이트

Microsoft SQL Server 2016 이상은 TLS 1.1 및 TLS 1.2를 지원합니다. 이전 버전 및 종속 라이브러리를 업데이트해야 할 수 있습니다. 자세한 내용은 [KB 3135244: Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)을 참조하세요.

보조 사이트 서버는 적어도 SQL Server 2016 Express 서비스 팩 2(13.2.50.26) 이상을 사용해야 합니다.

### <a name="sql-server-native-client"></a>SQL Server Native Client

> [!NOTE]
> [KB 3135244](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)에서도 SQL Server 클라이언트 구성 요소의 요구 사항을 설명합니다.

또한 SQL Server Native Client를 적어도 SQL 2012 SP4(11.*.7001.0) 버전으로 업데이트해야 합니다. 버전 1810부터 이 요구 사항은 [필수 구성 요소 검사(경고)](/sccm/core/servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client)입니다.

Configuration Manager는 다음 사이트 시스템 역할에서 SQL Server Native Client를 사용합니다.

- 사이트 데이터베이스 서버
- 사이트 서버: 중앙 관리 사이트, 주 사이트 또는 보조 사이트
- 관리 지점
- 디바이스 관리 지점
- 상태 마이그레이션 지점
- 사이트 데이터베이스
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


## <a name="update-windows-and-winhttp"></a>Windows 및 WinHTTP 업데이트

Windows 8.1, Windows Server 2012 R2, Windows 10, Windows Server 2016 및 후속 버전의 Windows는 기본적으로 WinHTTP를 통한 클라이언트-서버 통신을 위해 TLS 1.2를 지원합니다.

이전 버전의 Windows(예: Windows 7 또는 Windows Server 2012)는 HTTPS를 통한 클라이언트-서버 통신을 위해 기본적으로 TLS 1.1 또는 1.2를 사용하도록 설정하지 않습니다. 이러한 이전 버전의 Windows에서는 [업데이트 3140245](https://support.microsoft.com/help/3140245)를 설치하여 Windows의 WinHTTP에서 기본 보안 프로토콜로 TLS 1.1 및 TLS 1.2를 사용하도록 설정합니다. 그런 후 다음 레지스트리 값을 설정합니다.

> [!IMPORTANT]
> Configuration Manager 서버에서 TLS 1.2를 사용하도록 설정하기 ‘전에’ 모든 클라이언트에서 이러한 설정을 사용하도록 설정합니다.  그렇지 않으면 클라이언트를 실수로 분리할 수 있습니다.

다음과 같이 `DefaultSecureProtocols` 레지스트리 설정 값을 확인합니다.

```Registry
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
```

이 값을 변경한 경우 컴퓨터를 다시 시작합니다.

> [!Note]  
> 위의 예제는 WinHTTP `DefaultSecureProtocols` 설정의 `0xAA0` 값을 보여 줍니다. [KB 3140245: Windows의 WinHTTP에서 TLS 1.1 및 TLS 1.2를 기본 보안 프로토콜로 사용하도록 설정하기 위한 업데이트](https://support.microsoft.com/help/3140245)에는 각 프로토콜에 대한 16진수 값이 표시됩니다. 기본적으로 Windows에서 WinHTTP에 대해 SSL 3.0 및 TLS 1.0을 사용하도록 설정하려면 이 값이 `0x0A0`이어야 합니다. 위의 예제에서는 이러한 기본값을 유지하며, WinHTTP에 대해 TLS 1.1 및 TLS 1.2를 사용하도록 설정합니다. 이와 같이 구성하면 해당 변경 내용이 여전히 SSL 3.0 또는 TLS 1.0에 의존할 수 있는 다른 애플리케이션을 중단하지 않게 됩니다. TLS 1.1 및 TLS 1.2만 사용하도록 설정하려면 `0xA00` 값을 사용할 수 있습니다. Configuration Manager는 Windows가 두 디바이스 간에 협상하는 가장 안전한 프로토콜을 지원합니다.
>
> SSL 3.0 및 TLS 1.0을 완전히 사용하지 않도록 설정하려는 경우 Windows에서 SChannel 해제 프로토콜 설정을 사용합니다. 자세한 내용은 [Schannel.dll에서 특정 암호화 알고리즘 및 프로토콜의 사용을 제한하는 방법](https://support.microsoft.com/help/245030/how-to-restrict-the-use-of-certain-cryptographic-algorithms-and-protoc)을 참조하세요.


## <a name="update-windows-server-update-services-wsus"></a>WSUS(Windows Server Update Services) 업데이트

Windows Server 2012 및 Windows Server 2012 R2의 WSUS에서 클라이언트-서버 통신을 위해 TLS 1.2를 지원하려면 WSUS 서버에서 다음 업데이트를 설치합니다.

- Windows Server 2012를 실행하는 WSUS 서버의 경우 [업데이트 4022721](https://support.microsoft.com/help/4022721) 이상의 업데이트를 설치합니다.
- Windows Server 2012 R2를 실행하는 WSUS 서버의 경우 [업데이트 4022720](https://support.microsoft.com/help/4022720) 이상의 업데이트를 설치합니다.


## <a name="known-issues"></a>알려진 문제

이 섹션에서는 TLS 1.2 지원을 사용하도록 설정할 때 발생하는 일반적인 문제에 대한 지침을 제공합니다.

### <a name="unsupported-platforms"></a>플랫폼이 지원되지 않는 경우

다음 클라이언트 플랫폼은 Configuration Manager에서 지원되지만 TLS 1.2 환경에서는 지원되지 않습니다.

- Windows Server 2008
- Windows CE
- Apple OS X
- 온-프레미스 MDM을 사용하여 관리형 Windows 10 디바이스

### <a name="reports-dont-show-in-the-console"></a>콘솔에서 보고서가 표시되지 않음

보고서가 Configuration Manager 콘솔에 표시되지 않으면 콘솔을 실행하는 컴퓨터를 업데이트해야 합니다. [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화를 사용하도록 설정해야 합니다.

### <a name="fips-security-policy-enabled"></a>FIPS 보안 정책 사용

클라이언트 또는 서버에 대해 FIPS 보안 정책 설정을 사용하도록 설정하면 보안 채널(Schannel) 협상으로 인해 TLS 1.0이 사용될 수 있습니다. 이 동작은 레지스트리에서 이 프로토콜을 사용하지 않도록 설정하는 경우에도 발생합니다.

조사하려면 보안 채널 이벤트 로깅을 사용하도록 설정한 후 시스템 로그에서 Schannel 이벤트를 검토합니다. 자세한 내용은 [Schannel.dll에서 특정 암호화 알고리즘 및 프로토콜의 사용을 제한하는 방법](https://support.microsoft.com/help/245030/how-to-restrict-the-use-of-certain-cryptographic-algorithms-and-protoc)을 참조하세요.

### <a name="sql-server-communication-failure"></a>SQL Server 통신 실패

SQL Server 통신이 실패하고 **SslSecurityError** 오류를 반환하는 경우 다음 설정을 확인합니다.

- [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 각 머신에서 강력한 암호화를 사용하도록 설정
- 호스트 서버에서 [SQL Server 업데이트](#update-sql-server-and-client-components)
- SQL과 통신하는 모든 시스템에서 [SQL 클라이언트 구성 요소 업데이트](#update-sql-server-and-client-components). 예: 사이트 서버, SMS 공급자 및 사이트 역할 서버

### <a name="configuration-manager-client-communication-failures"></a>구성 관리자 클라이언트 통신 실패

구성 관리자 클라이언트가 사이트 역할과 통신하지 않을 경우 WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 [Windows를 업데이트](#update-windows-and-winhttp)했는지 확인합니다. 일반적인 사이트 역할에는 배포 지점, 관리 지점 및 상태 마이그레이션 지점이 포함됩니다.

### <a name="reporting-services-point-fails-and-returns-an-expected-error"></a>보고 서비스 지점이 실패하고 예상되는 오류 반환

보고 서비스 지점이 보고서를 구성하지 않으면 **SRSRP.log**에서 다음 오류 항목을 확인합니다.

`The underlying connection was closed:`
`An expected error occurred on a receive.`

이 문제를 해결하려면 다음 단계를 수행하세요.

1. 모든 관련 컴퓨터에서 [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화를 사용하도록 설정합니다.

1. 모든 업데이트를 설치한 후 SMS_Executive 서비스를 다시 시작합니다.

### <a name="application-catalog-doesnt-initialize"></a>애플리케이션 카탈로그가 초기화되지 않음

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.

애플리케이션 카탈로그가 초기화되지 않으면 **ServicePortalWebSite.svclog** 파일에서 다름 오류 항목을 확인하세요.

`SOAP security negotiation failed. The client and server can't communicate because they don't share a common algorithm.`

이 문제를 해결하려면 다음 단계를 수행하세요.

1. 모든 관련 컴퓨터에서 [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화를 사용하도록 설정합니다.

1. 애플리케이션 카탈로그 서버의 `%WinDir%\System32\InetSrv` 폴더에서 다음 내용을 사용하여 **W2SP.exe.config** 파일을 만듭니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <runtime>
      <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
      </runtime>
    </configuration>
    ```

    > [!NOTE]
    > 이 파일은 애플리케이션이 .NET Framework 4.6.3을 사용하여 빌드된 경우 생성되는 기본 파일입니다.

1. 애플리케이션 카탈로그 역할에 대해 HTTPS 전송 보안을 사용합니다.

    > [!Important]
    > 애플리케이션 카탈로그 역할에 대해 HTTP 메시지 보안을 사용할 경우 WCF는 SSL 3.0 및 TLS 1.0만 사용하도록 하드 코드됩니다. 이로 인해 TLS 1.2를 사용할 수 없게 됩니다.

1. 필요한 사항을 변경한 경우 컴퓨터를 다시 시작합니다.

### <a name="software-center-or-browser-doesnt-communicate-with-the-application-catalog"></a>소프트웨어 센터 또는 브라우저는 애플리케이션 카탈로그와 통신하지 않습니다.

> [!Important]  
> 애플리케이션 카탈로그는 사용되지 않습니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.

TLS 1.2 지원 사이트에서 사용자가 사용할 수 있는 앱에 소프트웨어 센터가 작동하도록 하는 최상의 방법은 애플리케이션 카탈로그 역할을 제거하는 것입니다. 그런 다음, 소프트웨어 센터가 관리 지점과 직접 통신하도록 합니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.

애플리케이션 카탈로그와 소프트웨어 센터 간의 통신 오류를 해결해야 하는 경우 다음 조건을 확인합니다.

- [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정

- 변경을 수행한 후 영향을 받는 모든 컴퓨터를 다시 시작합니다.

<!-- - Configure the browser is configured to support TLS 1. Prior to Windows 10, this option was disabled by default. removing, Silverlight experience is out of support-->

### <a name="service-connection-point-upload-failures"></a>서비스 연결 지점 업로드 실패

서비스 연결 지점이 SCCMConnectedService에 데이터를 업로드하지 않으면 [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정합니다. 변경을 수행한 후 컴퓨터를 다시 시작해야 합니다.

### <a name="configuration-manager-console-displays-intune-onboarding-dialog-box"></a>Configuration Manager 콘솔에 Intune 온보딩 대화 상자 표시

콘솔에서 Intune 포털에 연결하려고 할 때 Intune 온보딩 대화 상자가 나타나면 [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정합니다. 변경을 수행한 후 컴퓨터를 다시 시작해야 합니다.

### <a name="configuration-manager-console-displays-failure-to-sign-in-to-azure"></a>Configuration Manager 콘솔에 Azure 로그인 실패 표시

Azure AD(Azure Active Directory)에서 애플리케이션을 만들려고 할 경우 **로그인**을 선택한 직후에 Azure 서비스 온보딩 대화 상자에서 오류가 발생하면 [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화를 사용하도록 설정합니다. 변경을 수행한 후 컴퓨터를 다시 시작해야 합니다.

### <a name="configuration-manager-cloud-services-and-tls-12"></a>Configuration Manager 클라우드 서비스 및 TLS 1.2

버전 1802부터 클라우드 관리 게이트웨이 및 클라우드 배포 지점에서 사용하는 Azure 가상 머신은 TLS 1.2를 지원합니다. 버전 1802 이상에서 지원되는 클라이언트는 자동으로 TLS 1.2를 사용합니다.

**SMSAdminui.log**에는 다음 예제와 비슷한 오류가 포함될 수 있습니다.

```
Microsoft.ConfigurationManager.CloudBase.AAD.AADAuthenticationException
Service returned error. Check InnerException for more details
at Microsoft.ConfigurationManager.CloudBase.AAD.AADAuthenticationContext.GetAADAuthResultObject
...
Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException
Service returned error. Check InnerException for more details
at Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext.RunAsyncTask
...
System.Net.WebException
The underlying connection was closed: An unexpected error occurred on a receive.
at System.Net.HttpWebRequest.GetResponse
```

System EventLog에서 다음 설명과 함께 SChannel EventID 36874가 로깅될 수 있습니다. `An TLS 1.2 connection request was received from a remote client application, but none of the cipher suites supported by the client application are supported by the server. The TLS connection request has failed.`
<!--SCCMDocs issue #1608-->


## <a name="see-also"></a>참고 항목

- [.NET Framework에 대한 TLS(전송 계층 보안) 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry)

- [KB 3135244: Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)

- [암호화 컨트롤 기술 참조](cryptographic-controls-technical-reference.md)
