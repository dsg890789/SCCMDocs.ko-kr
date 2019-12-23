---
author: mestew
ms.author: mstewart
ms.prod: configuration-manager
ms.topic: include
ms.date: 12/13/2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: f12f42583237d40a03f6969455e9751f6be6fff7
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198937"
---
<!-- ## Update and configure the .NET Framework to support TLS 1.2 Note: the heading in in the 2 articles (enable-tls-1-2-client & enable-tls-1-2-server) to better facilitate linking. -->

### <a name="determine-net-version"></a>.NET 버전 확인

먼저 설치된 .NET 버전을 확인합니다. 자세한 내용은 [설치된 Microsoft .NET Framework의 버전 및 서비스 팩 수준을 확인하는 방법](https://support.microsoft.com/help/318785/how-to-determine-which-versions-and-service-pack-levels-of-the-microso)을 참조하세요.

### <a name="install-net-updates"></a>.NET 업데이트 설치

강력한 암호화 지원을 위해 .NET 업데이트를 설치합니다. 일부 버전의 .NET Framework에서는 강력한 암호화를 위해 업데이트가 필요할 수 있습니다. 다음 지침을 따르세요.

- .NET Framework 4.6.2 이상은 TLS 1.1 및 TLS 1.2를 지원합니다. 레지스트리 설정을 확인하지만 추가 변경은 필요하지 않습니다.

- TLS 1.1 및 TLS 1.2를 지원하도록 NET Framework 4.6 및 이전 버전을 업데이트합니다. 자세한 내용은 [.NET Framework 버전 및 종속성](https://docs.microsoft.com/dotnet/framework/migration-guide/versions-and-dependencies)을 참조하세요.

- Windows 8.1 또는 Windows Server 2012에서 .NET Framework 4.5.1 또는 4.5.2를 사용하는 경우 관련 업데이트 및 세부 정보도 [다운로드 센터](https://www.microsoft.com/download/details.aspx?id=42883)에서 다운로드할 수 있습니다.


### <a name="configure-for-strong-cryptography"></a>강력한 암호화를 위해 구성

강력한 암호화를 지원하도록 .NET Framework를 구성합니다. `SchUseStrongCrypto` 레지스트리 설정을 `DWORD:00000001`로 설정합니다. 이 값은 RC4 스트림 암호를 사용하지 않도록 설정하며, 값을 적용하기 위해 시스템을 다시 시작해야 합니다. 이 설정에 대한 자세한 내용은 [Microsoft 보안 공지 296038](https://docs.microsoft.com/security-updates/SecurityAdvisories/2015/2960358)을 참조하세요.

네트워크를 통해 TLS 1.2 지원 시스템과 통신하는 모든 컴퓨터에서 다음 레지스트리 키를 설정해야 합니다. 그 예로는 Configuration Manager 클라이언트와 사이트 서버에 설치되지 않은 원격 사이트 시스템 역할, 사이트 서버 자체를 들 수 있습니다.

32비트 OS에서 실행되는 32비트 애플리케이션과 64비트 OS에서 실행되는 64비트 애플리케이션의 경우 다음 하위 키 값을 업데이트합니다.

``` Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
```

64비트 OS에서 실행되는 32비트 애플리케이션의 경우 다음 하위 키 값을 업데이트합니다.

``` Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
```

> [!Note]  
> `SchUseStrongCrypto` 설정을 지정하면 .NET에서 TLS 1.1 및 TLS 1.2를 사용할 수 있습니다. `SystemDefaultTlsVersions` 설정을 지정하면 .NET에서 OS 구성을 사용할 수 있습니다. 자세한 내용은 [.NET Framework에 대한 TLS 모범 사례](https://docs.microsoft.com/dotnet/framework/network-programming/tls)를 참조하세요.
