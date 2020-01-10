---
title: 클라이언트에서의 TLS(전송 계층 보안) 1.2 사용 설정 방법
titleSuffix: Configuration Manager
description: Configuration Manager 클라이언트에 대해 TLS 1.2를 사용하도록 설정하는 방법에 대한 정보입니다.
ms.date: 12/13/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5b094a02-a425-4b67-81d3-8455e4265512
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 84832c895934e10f898f0fe6989f133c5fa95c75
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799304"
---
# <a name="how-to-enable-tls-12-on-clients"></a>클라이언트에서의 TLS 1.2 사용 설정 방법

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 환경에 대해 TLS 1.2를 사용 설정할 때는 먼저 클라이언트가 사용 가능하며 TLS 1.2를 사용하도록 올바로 구성되었는지 확인한 다음 사이트 서버와 원격 사이트의 시스템에서 TLS 1.2를 사용 설정하고 오래된 프로토콜은 사용하지 않도록 설정합니다. 클라이언트에서의 TLS 1.2 사용 설정에는 다음 세 가지 작업이 필요합니다.

- Windows 및 WinHTTP 업데이트
- TLS 1.2가 운영 체제 수준의 SChannel용 프로토콜로서 사용 설정되었는지의 여부 확인
- TLS 1.2 지원을 위한 .NET Framework 업데이트 및 구성

특정 Configuration Manager 기능 및 시나리오의 종속성에 대한 자세한 내용은 [TLS 1.2 사용 설정 소개](/sccm/core/plan-design/security/enable-tls-1-2)를 참조하세요.

## <a name="bkmk_winhttp"></a> Windows 및 WinHTTP 업데이트

Windows 8.1, Windows Server 2012 R2, Windows 10, Windows Server 2016 및 후속 버전의 Windows는 기본적으로 WinHTTP를 통한 클라이언트-서버 통신을 위해 TLS 1.2를 지원합니다. 

이전 버전의 Windows(예: Windows 7 또는 Windows Server 2012)는 WinHTTP를 사용하는 보안 통신에서 기본적으로 TLS 1.1 또는 TLS 1.2를 사용 설정하지 않습니다. 이전 버전의 Windows의 경우에는 [업데이트 3140245](https://support.microsoft.com/help/3140245)를 설치해 아래의 레지스트리 값을 활성화하는데, 이를 통해 WinHTTP의 기본 보안 프로토콜 목록에 TLS 1.1과 TLS 1.2를 추가하도록 설정할 수 있습니다. 패치가 설치되면 다음 레지스트리 값을 생성합니다.

> [!IMPORTANT]
> 이전 버전의 Windows에서 실행 중인 모든 클라이언트에서 이 설정을 활성화한 *다음* Configuration Manager 서버에서 TLS 1.2를 사용 설정하고 오래된 프로토콜은 사용하지 않도록 설정합니다. 그렇지 않으면 클라이언트를 실수로 분리할 수 있습니다.

다음과 같이 `DefaultSecureProtocols` 레지스트리 설정 값을 확인합니다.

``` Registry
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
```

이 값을 변경한 경우 컴퓨터를 다시 시작합니다.

위의 예제는 WinHTTP `DefaultSecureProtocols` 설정의 `0xAA0` 값을 보여 줍니다. [KB 3140245: Windows의 WinHTTP에서 TLS 1.1 및 TLS 1.2를 기본 보안 프로토콜로 사용하도록 설정하기 위한 업데이트](https://support.microsoft.com/help/3140245)에는 각 프로토콜에 대한 16진수 값이 표시됩니다. 기본적으로 Windows에서 WinHTTP에 대해 SSL 3.0 및 TLS 1.0을 사용하도록 설정하려면 이 값이 `0x0A0`이어야 합니다. 위의 예제에서는 이러한 기본값을 유지하며, WinHTTP에 대해 TLS 1.1 및 TLS 1.2를 사용하도록 설정합니다. 이와 같이 구성하면 해당 변경 내용이 여전히 SSL 3.0 또는 TLS 1.0에 의존할 수 있는 다른 애플리케이션을 중단하지 않게 됩니다. TLS 1.1 및 TLS 1.2만 사용하도록 설정하려면 `0xA00` 값을 사용할 수 있습니다. Configuration Manager는 Windows가 두 디바이스 간에 협상하는 가장 안전한 프로토콜을 지원합니다.

 SSL 3.0 및 TLS 1.0을 완전히 사용하지 않도록 설정하려는 경우 Windows에서 SChannel 해제 프로토콜 설정을 사용합니다. 자세한 내용은 [Schannel.dll에서 특정 암호화 알고리즘 및 프로토콜의 사용을 제한하는 방법](https://support.microsoft.com/help/245030/how-to-restrict-the-use-of-certain-cryptographic-algorithms-and-protoc)을 참조하세요.

## <a name="bkmk_protocol"></a> TLS 1.2가 운영 체제 수준의 SChannel용 프로토콜로서 사용 설정되었는지의 여부 확인

[!INCLUDE [Enable TLS 1.2 protocol as a security provider](includes/enable-tls-1-2-protocol-security-provider.md)]

## <a name="bkmk_net"></a> TLS 1.2 지원을 위한 .NET Framework 업데이트 및 구성

[!INCLUDE [Update and configure the .NET framework to support TLS 1.2](includes/update-net-framework-to-support-tls-1-2.md)]


## <a name="next-steps"></a>다음 단계

- [사이트 서버 및 원격 사이트 시스템에서의 TLS 1.2 사용 설정](/sccm/core/plan-design/security/enable-tls-1-2-server)
- [TLS 1.2 사용 설정 시의 일반 문제](/sccm/core/plan-design/security/enable-tls-1-2-troubleshoot)

