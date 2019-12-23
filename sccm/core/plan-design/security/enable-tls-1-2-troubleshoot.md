---
title: TLS(전송 계층 보안) 1.2 사용 설정 시의 일반 문제
titleSuffix: Configuration Manager
description: TLS(전송 계층 보안) 1.2 사용 설정 시 발생하는 일반적인 문제를 설명합니다
ms.date: 12/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 15083f28-8ff2-4e23-9f5e-b5dbd0859839
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 42c554bad7ed493a6c413bef950eb9dd68f27b7f
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198897"
---
# <a name="common-issues-when-enabling-tls-12"></a>TLS 1.2 사용 설정 시의 일반 문제

이 아티클에서는 Configuration Manager에서 TLS 1.2 지원을 사용하도록 설정할 때 발생하는 일반적인 문제에 대한 지침을 제공합니다.

## <a name="unsupported-platforms"></a>플랫폼이 지원되지 않는 경우

다음 클라이언트 플랫폼은 Configuration Manager에서 지원되지만 TLS 1.2 환경에서는 지원되지 않습니다.

- Windows Server 2008
- Windows CE
- Apple OS X
- 온-프레미스 MDM을 사용하는 관리형 Windows 10 디바이스

## <a name="reports-dont-show-in-the-console"></a>콘솔에서 보고서가 표시되지 않음

보고서가 Configuration Manager 콘솔에 표시되지 않으면 콘솔을 실행하는 컴퓨터를 업데이트해야 합니다. [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)하고 강력한 암호화를 사용하도록 설정하세요.

## <a name="fips-security-policy-enabled"></a>FIPS 보안 정책 사용

클라이언트 또는 서버에 대해 FIPS 보안 정책 설정을 사용하도록 설정하면 보안 채널(Schannel) 협상으로 인해 TLS 1.0이 사용될 수 있습니다. 이 동작은 레지스트리에서 이 프로토콜을 사용하지 않도록 설정하는 경우에도 발생합니다.

조사하려면 보안 채널 이벤트 로깅을 사용하도록 설정한 후 시스템 로그에서 Schannel 이벤트를 검토합니다. 자세한 내용은 [Schannel.dll에서 특정 암호화 알고리즘 및 프로토콜의 사용을 제한하는 방법](https://support.microsoft.com/help/245030/how-to-restrict-the-use-of-certain-cryptographic-algorithms-and-protoc)을 참조하세요.

## <a name="sql-server-communication-failure"></a>SQL Server 통신 실패

SQL Server 통신이 실패하고 **SslSecurityError** 오류를 반환하는 경우 다음 설정을 확인합니다.

- [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_net)하고 각 머신에서 강력한 암호화를 사용하도록 설정
- 호스트 서버에서 [SQL Server 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql)
- SQL과 통신하는 모든 시스템에서 [SQL 클라이언트 구성 요소 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_sql-client). 예: 사이트 서버, SMS 공급자 및 사이트 역할 서버

## <a name="configuration-manager-client-communication-failures"></a>구성 관리자 클라이언트 통신 실패

구성 관리자 클라이언트가 사이트 역할과 통신하지 않을 경우 WinHTTP를 사용하여 클라이언트-서버 통신에 대해 TLS 1.2를 지원하도록 [Windows를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_winhttp)했는지 확인합니다. 일반적인 사이트 역할에는 배포 지점, 관리 지점 및 상태 마이그레이션 지점이 포함됩니다.

## <a name="reporting-services-point-fails-and-returns-an-expected-error"></a>보고 서비스 지점이 실패하고 예상되는 오류 반환

보고 서비스 지점이 보고서를 구성하지 않으면 **SRSRP.log**에서 다음 오류 항목을 확인합니다.

`The underlying connection was closed:`
`An expected error occurred on a receive.`

이 문제를 해결하려면 다음 단계를 수행하세요.

1. 모든 관련 컴퓨터에서 [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)하고 강력한 암호화를 사용하도록 설정합니다.

1. 모든 업데이트를 설치한 후 SMS_Executive 서비스를 다시 시작합니다.

## <a name="application-catalog-doesnt-initialize"></a>애플리케이션 카탈로그가 초기화되지 않음

> [!Important]  
> 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.

애플리케이션 카탈로그가 초기화되지 않으면 **ServicePortalWebSite.svclog** 파일에서 다름 오류 항목을 확인하세요.

`SOAP security negotiation failed. The client and server can't communicate because they don't share a common algorithm.`

이 문제를 해결하려면 다음 단계를 수행하세요.

1. 모든 관련 컴퓨터에서 [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)하고 강력한 암호화를 사용하도록 설정합니다.

1. 애플리케이션 카탈로그 서버의 `%WinDir%\System32\InetSrv` 폴더에서 다음 내용을 사용하여 **W2SP.exe.config** 파일을 만듭니다.

    ``` XML
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

## <a name="software-center-or-browser-doesnt-communicate-with-the-application-catalog"></a>소프트웨어 센터 또는 브라우저는 애플리케이션 카탈로그와 통신하지 않습니다.

> [!Important]  
> 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다. 자세한 내용은 [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요.

TLS 1.2 지원 사이트에서 사용자가 사용할 수 있는 앱에 소프트웨어 센터가 작동하도록 하는 최상의 방법은 애플리케이션 카탈로그 역할을 제거하는 것입니다. 그런 다음, 소프트웨어 센터가 관리 지점과 직접 통신하도록 합니다. 자세한 내용은 [애플리케이션 카탈로그 제거](/sccm/apps/plan-design/plan-for-and-configure-application-management#bkmk_remove-appcat)를 참조하세요.

애플리케이션 카탈로그와 소프트웨어 센터 간의 통신 오류를 해결해야 하는 경우 다음 조건을 확인합니다.

- [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)하고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정

- 변경을 수행한 후 영향을 받는 모든 컴퓨터를 다시 시작합니다.

<!-- - Configure the browser is configured to support TLS 1. Prior to Windows 10, this option was disabled by default. removing, Silverlight experience is out of support-->

## <a name="service-connection-point-upload-failures"></a>서비스 연결 지점 업로드 실패

서비스 연결 지점이 SCCMConnectedService에 데이터를 업로드하지 않으면 [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_net)하고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정합니다. 변경을 수행한 후 컴퓨터를 다시 시작해야 합니다.

## <a name="configuration-manager-console-displays-intune-onboarding-dialog-box"></a>Configuration Manager 콘솔에 Intune 온보딩 대화 상자 표시

콘솔에서 Intune 포털에 연결하려고 할 때 Intune 온보딩 대화 상자가 나타나면 [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-client#bkmk_net)하고 각 컴퓨터에서 강력한 암호화를 사용하도록 설정합니다. 변경을 수행한 후 컴퓨터를 다시 시작해야 합니다.

## <a name="configuration-manager-console-displays-failure-to-sign-in-to-azure"></a>Configuration Manager 콘솔에 Azure 로그인 실패 표시

Azure AD(Azure Active Directory)에서 애플리케이션을 만들려고 할 경우 **로그인**을 선택한 직후에 Azure 서비스 온보딩 대화 상자에서 오류가 발생하면 [.NET Framework를 업데이트](/sccm/core/plan-design/security/enable-tls-1-2-server#bkmk_net)하고 강력한 암호화를 사용하도록 설정합니다. 변경을 수행한 후 컴퓨터를 다시 시작해야 합니다.

## <a name="configuration-manager-cloud-services-and-tls-12"></a>Configuration Manager 클라우드 서비스 및 TLS 1.2

클라우드 관리 게이트웨이 및 클라우드 배포 지점에서 사용하는 Azure 가상 머신이 TLS 1.2를 지원합니다. 지원되는 클라이언트 버전은 자동으로 TLS 1.2를 사용합니다.

**SMSAdminui.log**에는 다음 예제와 비슷한 오류가 포함될 수 있습니다.

``` Log
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

## <a name="additional-resources"></a>추가 리소스

- [.NET Framework에 대한 TLS(전송 계층 보안) 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls#configuring-security-via-the-windows-registry)
- [KB 3135244: Microsoft SQL Server에 대한 TLS 1.2 지원](https://support.microsoft.com/help/3135244/tls-1-2-support-for-microsoft-sql-server)
- [암호화 컨트롤 기술 참조](cryptographic-controls-technical-reference.md)

## <a name="next-steps"></a>다음 단계

- [클라이언트에서의 TLS 1.2 사용 설정](/sccm/core/plan-design/security/enable-tls-1-2-client)
- [사이트 서버 및 원격 사이트 시스템에서의 TLS 1.2 사용 설정](/sccm/core/plan-design/security/enable-tls-1-2-server)

