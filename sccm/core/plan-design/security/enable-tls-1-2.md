---
title: TLS 1.2를 사용하도록 설정하는 방법
titleSuffix: Configuration Manager
description: Microsoft Configuration Manager용 TLS 1.2를 사용하도록 설정하는 방법에 대한 정보입니다.
ms.date: 05/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 31de47c9-891b-4de7-8d5e-fbbc1bff7c60
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3641c3a9adce23f24a80135d996da03e12e78907
ms.sourcegitcommit: 18a94eb78043cb565b05cd0e9469b939b29cccf0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355610"
---
# <a name="how-to-enable-tls-12-for-configuration-manager"></a>Configuration Manager에서 TLS 1.2를 사용하도록 설정하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 개별 구성 요소를 비롯하여 Configuration Manager용 TLS 1.2를 사용하도록 설정하는 방법을 설명합니다. 일반적으로 사용하는 기능의 업데이트 요구 사항과 몇 가지 일반적인 문제 해결 방법도 이 문서에서 설명합니다.

Configuration Manager는 보안 통신을 위해 여러 다양한 구성 요소를 활용합니다. 지정된 연결에 사용하는 프로토콜은 모든 필수 구성 요소의 기능에 따라 좌우됩니다. 한 가지 구성 요소가 오래된 경우 통신에서 오래되고 덜 안전한 프로토콜이 사용될 수 있습니다.

TLS 1.2를 지원하도록 Configuration Manager를 올바르게 사용하도록 설정하려면 모든 필수 구성 요소에 대해 TLS 1.2를 사용하도록 설정해야 합니다. 필수 구성 요소는 사용자 환경 및 사용하는 Configuration Manager 기능에 따라 다릅니다.


## <a name="to-enable-tls-12"></a>TLS 1.2를 사용하도록 설정하려면

TLS 1.2를 사용하도록 설정하려면 먼저, Configuration Manager를 실행하거나 상호 작용하는 각 컴퓨터의 보안 공급자로서 TLS 1.2를 사용하도록 설정해야 합니다. 그런 다음, Configuration Manager가 보안 통신을 위해 사용하는 구성 요소에 대해 TLS 1.2를 사용하도록 설정합니다.

### <a name="enable-the-tls-12-protocol-as-a-security-provider"></a>TLS 1.2 프로토콜을 보안 공급자로 사용하도록 설정

[.NET Framework를 사용하는 TLS(전송 계층 보안) 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry?)에 표시된 대로 "\SecurityProviders\SCHANNEL\Protocols" 레지스트리 하위 키 설정을 확인합니다.

> [!NOTE]
> 기본적으로 TLS 1.2가 사용하도록 설정됩니다. 따라서 이 프로토콜을 사용하도록 설정하기 위해 이러한 키를 변경할 필요는 없습니다. 이 문서에 제공된 나머지 지침을 수행하고 TLS 1.2만 사용하도록 설정하여 작업 환경이 잘 작동하는지 확인한 후에 프로토콜에서 설정을 변경하여 TLS 1.0 및 TLS 1.1을 사용하지 않도록 설정할 수 있습니다.

### <a name="enable-tls-12-for-dependent-components"></a>종속 구성 요소에 대해 TLS 1.2를 사용하도록 설정
Configuration Manager가 보안 통신을 위해 사용하는 종속 구성 요소에 대해 TLS 1.2를 사용하도록 설정하려면 다음을 수행해야 합니다.

- [TLS 1.2를 지원하도록 .NET Framework 업데이트](#update-net-framework-to-support-tls-12)
- [SQL Server 및 클라이언트 구성 요소 업데이트](#update-sql-server-and-client-components)
- [Windows 8.0, Windows Server 2012 R2 및 이전 버전에서 Windows 및 WinHTTP 업데이트](#update-windows-and-winhttp)
- [WSUS(Windows Server Update Services) 업데이트](#update-windows-server-update-services)

#### <a name="update-net-framework-to-support-tls-12"></a>TLS 1.2를 지원하도록 .NET Framework 업데이트
TLS 1.2를 지원하도록 .NET Framework를 업데이트하려면 먼저 .NET 버전 번호를 확인합니다. 도움말을 보려면 [설치된 Microsoft .NET Framework의 버전 및 서비스 팩 수준을 확인하는 방법](https://support.microsoft.com/help/318785/how-to-determine-which-versions-and-service-pack-levels-of-the-microso)을 참조하세요.

이전 버전의 .NET Framework에서는 강력한 암호화를 위해 업데이트 또는 레지스트리 변경이 필요할 수 있습니다. 다음 지침을 따르세요.

- .NET Framework 4.6.2는 TLS 1.1 및 TLS 1.2를 지원합니다.  추가 변경은 필요하지 않습니다.
- TLS 1.1 및 TLS 1.2를 지원하려면 .NET Framework 4.6 및 이전 버전을 [업데이트해야 합니다](https://docs.microsoft.com/dotnet/framework/migration-guide/versions-and-dependencies).

Windows 8.1, Windows RT 8.1 또는 Windows Server 2012에서 .NET Framework 4.5.1 또는 4.5.2를 사용하는 경우 관련 업데이트 및 세부 정보도 [다운로드 센터](https://www.microsoft.com/download/details.aspx?id=42883)에서 다운로드할 수 있습니다.
-  강력한 암호화를 지원하도록 .NET Framework를 구성해야 합니다. `SchUseStrongCrypto` 레지스트리 설정을 `DWORD:00000001`로 설정합니다. 이 경우 RC4 스트림 암호가 사용하지 않도록 설정되며 시스템을 다시 시작해야 합니다. 이 설정에 대한 자세한 내용은 [Microsoft 보안 공지 296038](https://docs.microsoft.com/security-updates/SecurityAdvisories/2015/2960358)을 참조하세요.

32비트 시스템에서 실행되는 32비트 애플리케이션 또는 64비트 시스템에서 실행되는 64비트 애플리케이션의 경우 다음 하위 키 값을 업데이트합니다.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\
   Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions"=dword:00000001
      "SchUseStrongCrypto" = (DWORD): 00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\
   Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions"=dword:00000001
      "SchUseStrongCrypto"=dword:00000001
```
64비트 시스템에서 실행되는 32비트 애플리케이션의 경우 다음 하위 키 값을 업데이트합니다.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\
   Wow6432Node\Microsoft\.NETFramework\\v2.0.50727]
      "SystemDefaultTlsVersions"=dword:00000001
      "SchUseStrongCrypto" = (DWORD): 00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\
   WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions"=dword:00000001
      "SchUseStrongCrypto"=dword:00000001
```
#### <a name="update-sql-server-and-client-components"></a>SQL Server 및 클라이언트 구성 요소 업데이트

Microsoft SQL Server 2016은 TLS 1.1 및 TLS 1.2를 지원합니다.
이전 버전 및 종속 라이브러리를 업데이트해야 할 수 있습니다. 자세한 내용은 [KB 3135244: Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)을 참조하세요.

> [!NOTE]
> KB 3135244에서도 SQL Server 클라이언트 구성 요소의 요구 사항을 설명합니다. 사용자 환경에서 사용되는 각 구성 요소를 업데이트합니다.

#### <a name="update-windows-and-winhttp"></a>Windows 및 WinHTTP 업데이트

Windows 10, Windows 8.1, Windows Server 2016 및 Windows Server 2012 R2는 기본적으로 WinHTTP를 통한 클라이언트-서버 통신을 위해 TLS 1.2를 지원합니다.

Windows 8.0, Windows Server 2012 및 이전 버전의 Windows는 HTTPS를 통한 클라이언트-서버 통신을 위해 기본적으로 TLS 1.1 또는 1.2를 사용하도록 설정하지 않습니다. 이러한 이전 버전의 Windows에서는 [업데이트 3140245](https://support.microsoft.com/help/3140245)를 설치하여 Windows의 WinHTTP에서 기본 보안 프로토콜로 TLS 1.1 및 TLS 1.2를 사용하도록 설정하고 다음 레지스트리 값을 설정해야 합니다.

> [!IMPORTANT]
> TLS 1.2를 사용하도록 설정하기 **전에** 모든 하위 수준 클라이언트에서 먼저 이 작업을 실행해야 합니다. 그렇지 않으면 의도치 않게 해당 클라이언트가 분리될 수 있습니다.

다음과 같이 `DefaultSecureProtocols` 레지스트리 설정이 `0xAA0`인지 확인합니다.

```
HKEY_LOCAL_MACHINE\SOFTWARE\
   \Microsoft\Windows\CurrentVersion\
      Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
HKEY_LOCAL_MACHINE\SOFTWARE\
   Wow6432Node\Microsoft\Windows\CurrentVersion\
      Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
```
> [!NOTE]
> 이 변경 작업을 위해 시스템을 다시 시작해야 합니다.

#### <a name="update-windows-server-update-services"></a>Windows Server Update Services 업데이트

Windows Server 2012 및 Windows Server 2012 R2의 WSUS에서 클라이언트-서버 통신을 위해 TLS 1.2를 지원하려면 WSUS 서버에서 다음 업데이트를 적용해야 합니다.
- Windows Server 2012를 실행하는 WSUS 서버의 경우 [업데이트 4022721](https://support.microsoft.com/help/4022721) 이상의 업데이트를 적용합니다.
- Windows Server 2012 R2를 실행하는 WSUS 서버의 경우 [업데이트 4022720](https://support.microsoft.com/help/4022720) 이상의 업데이트를 적용합니다.

## <a name="tasks-required-for-configuration-manager-features-and-scenarios"></a>Configuration Manager 기능 및 시나리오에 필요한 작업
이 섹션에서는 특정 Configuration Manager 기능 및 시나리오에 대한 종속성을 설명합니다. 다음 단계를 확인하려면 사용자 환경에 적용되는 항목을 찾은 후 [종속 구성 요소에 대해 TLS 1.2를 사용하도록 설정](#enable-tls-12-for-dependent-components)의 앞부분에 제공된 단계를 사용하여 종속성을 확인합니다.

|기능 또는 시나리오|작업 업데이트|
|--- |--- |
|사이트 서버(중앙, 주 또는 보조)|[.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화 설정을 확인합니다.|
|사이트 데이터베이스|각 SMS 공급자에 적절하게 [SQL Server 및 클라이언트 구성 요소를 업데이트](#update-sql-server-and-client-components)합니다.|
|사이트 시스템 역할|[.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화 설정을 확인합니다. [SQL Server 및 해당 클라이언트 구성 요소를 업데이트](#update-sql-server-and-client-components)합니다.|
|서비스 연결점 애플리케이션 카탈로그|[.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화 설정을 확인합니다.|
|SRS 보고 지점|사이트 서버 및 SRS 서버에서 [.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)합니다. 필요에 따라 SMS_Executive 서비스를 다시 시작합니다.|
|Configuration Manager 콘솔|[.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화 설정을 확인합니다.|
|HTTPS 사이트 시스템 역할이 있는 SCCM 클라이언트|[WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 Windows를 업데이트](#update-windows-and-winhttp)합니다.|
|소프트웨어 센터|[.NET Framework를 업데이트](#update-net-framework-to-support-tls-12)하고 강력한 암호화 설정을 확인합니다.|
|소프트웨어 업데이트 지점|[WSUS를 업데이트](#update-windows-server-update-services)합니다.|
|관리 지점|Configuration Manager가 최신 TLS 1.2 사용 SQL Server 구성 요소에 연결할 수 있도록 하려면 최신 SQL Server Native Client로 업데이트합니다. [Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244)에서 "클라이언트 구성 요소 다운로드" 표를 참조하세요.|

## <a name="known-issues"></a>알려진 문제

이 섹션에서는 TLS 1.2 지원을 사용하도록 설정할 때 발생하는 일반적인 문제에 대한 지침을 제공합니다.

### <a name="fips-security-policy-enabled"></a>FIPS 보안 정책 사용

클라이언트 또는 서버에 대해 FIPS 보안 정책 설정을 사용하도록 설정하면, 레지스트리를 사용하여 프로토콜을 사용하지 않도록 설정한 경우에도 보안 채널(Schannel) 협상으로 인해 TLS 1.0이 사용될 수 있습니다.

조사하려면 보안 채널 이벤트 로깅을 사용하도록 설정한 후 시스템 로그에서 Schannel 이벤트를 검토합니다. 관련 정보에 대해서는 [Schannel.dll에서 특정 암호화 알고리즘 및 프로토콜의 사용을 제한하는 방법](https://support.microsoft.com/help/245030/how-to-restrict-the-use-of-certain-cryptographic-algorithms-and-protoc)을 참조하세요.

### <a name="sql-server-communication-failure"></a>SQL Server 통신 실패

SQL Server 통신이 실패하고 **SslSecurityError** 오류를 반환하는 경우 다음을 확인합니다.
- .NET Framework가 업데이트되고 각 머신에서 강력한 암호화가 사용하도록 설정되었습니다.
- SQL Server가 호스트 서버에서 업데이트되었습니다.
- SQL 클라이언트 구성 요소가 사이트 서버, SMS 공급자, 사이트 역할 서버 및 SQL Server와 통신하는 다른 모든 시스템에서 업데이트되었습니다.

### <a name="configuration-manager-client-communication-failures"></a>구성 관리자 클라이언트 통신 실패

구성 관리자 클라이언트가 사이트 역할 엔드포인트(예: 배포 지점, 관리 지점 및 상태 마이그레이션 지점)와 통신하지 않는 경우 WinHTTP를 사용하여 클라이언트-서버 통신을 위해 TLS 1.2를 지원하도록 Windows를 업데이트했는지 확인합니다.

### <a name="srs-reporting-point-fails-and-returns-an-expected-error"></a>SRS 보고 지점이 실패하고 예상되는 오류 반환

SRS 보고 지점이 보고서를 구성하지 않으면 *SRSRP.log*에서 다음 오류 항목을 확인합니다.

`The underlying connection was closed:`
`An expected error occurred on a receive.`

이 문제를 해결하려면 다음 단계를 수행하세요.

1. .NET Framework가 업데이트되고 모든 관련 컴퓨터에서 강력한 암호화가 사용하도록 설정되었는지 확인합니다.
1. 모든 업데이트가 설치된 후 SMS_Executive 서비스가 다시 시작되었는지 확인합니다.

### <a name="application-catalog-doesnt-initialize"></a>애플리케이션 카탈로그가 초기화되지 않음

애플리케이션 카탈로그가 초기화되지 않으면 *ServicePortalWebSite.svclog* 파일에서 다름 오류 항목을 확인하세요.

`SOAP security negotiation failed. The client and server can't communicate because they don't share a common algorithm.`

이 문제를 해결하려면 다음 단계를 수행하세요.
1. .NET Framework가 업데이트되고 모든 관련 컴퓨터에서 강력한 암호화가 사용하도록 설정되었는지 확인합니다.
1. 애플리케이션 카탈로그 서버의 C:\Windows\System32\InetSrv 폴더에서 다음 스크립트를 실행하여 *W2SP.exe.config* 파일을 만듭니다. 

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

   > [!NOTE]
   > 애플리케이션 카탈로그 역할에 대해 HTTP 메시지 보안을 사용할 경우 WCF는 SSL 3.0 및 TLS 1.0만 사용하도록 하드 코드됩니다. 이로 인해 TLS 1.2를 사용할 수 없게 됩니다.
1. 변경 작업이 끝나면 컴퓨터를 다시 시작합니다.


### <a name="software-center-or-browser-doesnt-communicate-with-application-catalog"></a>소프트웨어 센터 또는 브라우저는 애플리케이션 카탈로그와 통신하지 않습니다.

애플리케이션 카탈로그와 소프트웨어 센터 또는 브라우저 간의 통신 오류를 해결하려면 다음 조건을 확인합니다.

- .NET Framework가 업데이트되고 각 컴퓨터에서 강력한 암호화가 사용하도록 설정되었습니다.
- 브라우저는 TLS 1을 지원하도록 구성됩니다. Windows 10 이전에서는 이 옵션이 기본적으로 사용할 수 없게 설정되어 있습니다.
- 변경을 수행한 후 모든 컴퓨터가 다시 시작되었습니다.

   > [!NOTE]
   > 소프트웨어 센터가 사용자용 앱에 대한 TLS 1.2 적용 서버에 작동하도록 하려면 앱 카탈로그 역할을 제거하고 소프트웨어 센터가 관리 지점과 통신할 수 있도록 하는 것이 좋습니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.

### <a name="service-connection-point-upload-failures"></a>서비스 연결점 업로드 실패

서비스 연결점이 SCCMConnectedService에 데이터를 업로드하지 않으면 각 서버에서 .NET Framework가 업데이트되었는지와 강력한 암호화를 사용하도록 설정했는지 확인합니다. 변경이 수행된 후 컴퓨터를 다시 시작해야 합니다.

### <a name="configuration-manager-console-displays-intune-onboarding-dialog-box"></a>Configuration Manager 콘솔에 Intune 온보딩 대화 상자 표시

콘솔에서 Intune 포털에 연결하려고 할 때 Intune 온보딩 대화 상자가 나타나면 .NET Framework가 업데이트되고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정했는지 확인합니다.  변경이 수행된 후 컴퓨터를 다시 시작해야 합니다.

### <a name="configuration-manager-console-displays-failure-to-sign-in-to-azure"></a>Configuration Manager 콘솔에 Azure 로그인 실패 표시

Azure AD 애플리케이션을 만들 때 **로그인**을 선택한 직후에 Azure 서비스 온보딩 대화 상자에서 오류가 발생하면 .NET Framework가 업데이트되었는지와 강력한 암호화를 사용하도록 설정했는지 확인합니다. 이러한 변경 내용을 적용하려면 다시 시작해야 합니다.

## <a name="see-also"></a>참고 항목

[암호화 컨트롤 기술 참조](cryptographic-controls-technical-reference.md)
