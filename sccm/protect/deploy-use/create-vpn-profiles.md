---
title: VPN 프로필을 만드는 방법
titleSuffix: Configuration Manager
description: Configuration Manager에서 VPN 프로필을 만드는 방법에 대해 알아봅니다.
ms.date: 01/14/2020
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: b16d9d41b1f560a2ac6384c822788ad7461cc2d9
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035134"
---
# <a name="how-to-create-vpn-profiles-in-configuration-manager"></a>Configuration Manager에서 VPN 프로필을 만드는 방법

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager는 여러 VPN 연결 형식을 지원합니다. 다양한 디바이스 플랫폼에서 사용할 수 있는 연결 형식에 대한 자세한 내용은 [VPN 프로필](/configmgr/protect/deploy-use/vpn-profiles)을 참조하세요.

타사 VPN 연결의 경우 VPN 프로필을 배포하기 전에 VPN 앱을 배포합니다. 앱을 배포하지 않고 VPN에 연결하려고 하면 앱을 배포하라는 메시지가 표시됩니다. 자세한 내용은 [애플리케이션 배포](/configmgr/apps/deploy-use/deploy-applications)를 참조하세요.

## <a name="create-a-vpn-profile"></a>VPN 프로필 만들기

1. Configuration Manager 콘솔의 **자산 및 규정 준수** 작업 영역으로 가서 **규정 준수 설정**, **회사 리소스 액세스**를 차례로 확장하고 **VPN 프로필** 노드를 선택합니다.

1. 리본 메뉴에 있는 **홈** 탭의 **만들기** 그룹에서 **VPN 프로필 만들기**를 선택합니다.

1. VPN 프로필 만들기 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.

    - **이름**: 콘솔에서 VPN 프로필을 식별하는 고유한 이름을 입력합니다.

        > [!NOTE]
        > VPN 프로필 이름에 `\/:*?<>|; ` 문자를 사용하지 않습니다. Windows VPN 프로필은 이러한 특수 문자를 지원하지 않습니다.

    - **설명**: 필요에 따라 VPN 프로필에 대한 추가 정보를 제공하는 설명을 입력합니다.

    - **VPN 프로필 유형**: 적절한 플랫폼을 선택합니다.

        **Windows 8.1** 플랫폼을 선택하는 경우 **파일에서 가져오기** 할 수도 있습니다. 이 작업은 XML 파일에서 VPN 프로필 정보를 가져옵니다. 이 옵션을 선택하면 마법사의 나머지 부분에서 **지원되는 플랫폼** 및 **VPN 프로필 가져오기** 페이지가 간단해집니다.

1. **지원되는 플랫폼** 페이지에서 이 VPN 프로필이 지원하는 OS 버전을 선택합니다.

1. **콘텐츠** 페이지에서 다음 정보를 지정합니다.

    - **연결 형식**: VPN 연결 형식을 선택합니다. 지원되는 형식에 대한 자세한 내용은 [VPN 프로필](/configmgr/protect/deploy-use/vpn-profiles)을 참조하세요.

    - **서버 목록**: VPN 연결에 사용할 새 서버를 추가합니다. 연결 형식에 따라 VPN 서버를 하나 이상 선택하고 어떤 서버가 기본인지 지정할 수 있습니다.

    - **회사 네트워크에 연결된 경우 VPN 사용 안 함**: 내부 네트워크에 있는 VPN을 사용하지 않도록 클라이언트를 구성합니다. 필요한 경우 연결별로 DNS 이름을 지정합니다.

1. 마법사의 **인증 방법** 페이지에서 연결 형식으로 지원되는 방법을 선택합니다. 이 페이지의 설정 및 사용 가능한 옵션은 선택한 연결 형식에 따라 달라집니다. 자세한 내용은 [인증 방법 참조](#bkmk_auth)를 참조하세요.

1. **프록시 설정** 페이지에서 VPN이 프록시 서버를 사용하는 경우 환경에 적합한 옵션 중 하나를 선택합니다. 그런 다음 프록시에 대한 구성 정보를 제공합니다.

1. **애플리케이션** 페이지는 Windows 10 프로필에만 적용됩니다. 이 VPN에 자동으로 연결되는 데스크톱 및 유니버설 앱을 추가합니다. 앱 형식에 따라 앱 식별자가 결정됩니다.

    - *데스크톱 앱*의 경우 앱의 파일 경로를 제공합니다.

    - *유니버설 앱*의 경우 PFN(패키지 패밀리 이름)을 제공합니다. 앱의 PFN을 찾는 방법은 [Find a package family name for per-app VPN](/configmgr/protect/deploy-use/find-a-pfn-for-per-app-vpn)(앱별 VPN에 대한 패키지 패밀리 이름 찾기)을 참조하세요.

    **나열된 앱만 이 VPN을 사용할 수 있도록** 옵션을 구성할 수도 있습니다.

    > [!IMPORTANT]
    > 앱별 VPN 구성을 위해 컴파일하는 모든 관련 앱 목록을 보호해야 합니다. 권한이 없는 사용자가 목록을 변경하고 해당 목록을 앱별 VPN 앱 목록으로 가져오는 경우 액세스 권한이 부여되면 안 되는 앱에 VPN 액세스 권한을 잠재적으로 부여하게 됩니다.

1. **경계** 페이지는 VPN 경계를 구성하는 Windows 10 프로필에만 적용됩니다. 다음 옵션을 추가할 수 있습니다.

    - **네트워크 트래픽 규칙**: VPN 연결에 사용할 프로토콜, 로컬 포트, 원격 포트 및 주소 범위를 설정합니다.  

        > [!Note]
        > 네트워크 트래픽 규칙을 만들지 않으면 모든 프로토콜, 포트 및 주소 범위를 사용할 수 있습니다. 규칙을 만들고 나면 해당 규칙이나 추가 규칙에서 지정하는 프로토콜, 포트 및 주소 범위만 VPN 연결에 사용됩니다.

    - **DNS 이름 및 서버**: 디바이스에서 연결을 설정한 후 VPN 연결에 사용되는 DNS 서버입니다.

    - **경로**: VPN 연결을 사용하는 네트워크 경로입니다. 경로가 60개를 초과하면 정책이 실패할 수 있습니다.

1. 마법사를 완료합니다.

새로운 VPN 프로필이 **자산 및 호환성** 작업 영역의 **VPN 프로필** 노드에 표시됩니다.

## <a name="bkmk_auth"></a>인증 방법 참조

사용 가능한 VPN 인증 방법은 연결 형식에 따라 달라집니다.

### <a name="certificates"></a>인증서

클라이언트 인증서가 네트워크 정책 서버와 같은 RADIUS 서버를 인증하는 경우 인증서의 주체 대체 이름을 사용자 계정 이름으로 설정합니다.

지원되는 연결 형식:

- Pulse Secure
- F5 Edge Client
- Dell SonicWALL Mobile Connect
- 검사점 모바일 VPN

### <a name="username-and-password"></a>사용자 이름 및 암호

지원되는 연결 형식:

- Pulse Secure
- F5 Edge Client
- Dell SonicWALL Mobile Connect
- 검사점 모바일 VPN

### <a name="microsoft-eap-ttls"></a>Microsoft EAP-TTLS

지원되는 연결 형식:

- Microsoft SSL(SSTP)
- Microsoft 자동
- PPTP
- IKEv2
- L2TP

### <a name="microsoft-protected-eap-peap"></a>Microsoft 보호된 EAP(PEAP

지원되는 연결 형식:

- Microsoft SSL(SSTP)
- Microsoft 자동
- IKEv2
- PPTP
- L2TP

### <a name="microsoft-secured-password-eap-mschap-v2"></a>Microsoft 보안 암호(EAP-MSCHAP v2)

지원되는 연결 형식:

- Microsoft SSL(SSTP)
- Microsoft 자동
- IKEv2
- PPTP
- L2TP

### <a name="smart-card-or-other-certificate"></a>스마트 카드 또는 기타 인증서

지원되는 연결 형식:

- Microsoft SSL(SSTP)
- Microsoft 자동
- IKEv2
- PPTP
- L2TP

### <a name="mschap-v2"></a>MSCHAP v2

지원되는 연결 형식:

- Microsoft SSL(SSTP)
- Microsoft 자동
- IKEv2
- PPTP
- L2TP

### <a name="use-machine-certificates"></a>컴퓨터 인증서 사용

지원되는 연결 형식:

- IKEv2

### <a name="additional-authentication-options"></a>추가 인증 옵션

Windows 클라이언트 버전에서 지원하는 경우 인증 방법을 **구성**하는 옵션을 사용할 수 있습니다. 이 옵션은 인증 방법을 구성하는 Windows 속성 창을 엽니다.

선택한 옵션에 따라 다음과 같은 추가 정보를 지정하라는 메시지가 표시될 수 있습니다.

- **로그온할 때마다 사용자 자격 증명 기억**: 사용자가 연결할 때마다 자격 증명을 입력할 필요가 없도록 사용자 자격 증명이 기억됩니다.  

- **클라이언트 인증을 위해 클라이언트 인증서 선택**: VPN 연결을 인증하기 위해 이전에 만든 클라이언트 SCEP 인증서를 선택합니다. 자세한 내용은 [PFX 인증서 프로필 만들기](/configmgr/protect/deploy-use/create-pfx-certificate-profiles)를 참조하세요.

## <a name="next-steps"></a>다음 단계

- 타사 VPN 연결의 경우 VPN 프로필을 배포하기 전에 VPN 앱을 배포합니다. 앱을 배포하지 않고 VPN에 연결하려고 하면 앱을 배포하라는 메시지가 표시됩니다. 자세한 내용은 [애플리케이션 배포](/configmgr/apps/deploy-use/deploy-applications)를 참조하세요.

- VPN 프로필을 배포합니다. 자세한 내용은 [프로필 배포 방법](/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)을 참조하세요.
