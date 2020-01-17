---
title: 인증서 프로필 소개
titleSuffix: Configuration Manager
description: Configuration Manager의 인증서 프로필이 Active Directory 인증서 서비스에서 작동하는 방식을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 1b3afee0219b93b120748c1078cfa0944b71946d
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75819576"
---
# <a name="introduction-to-certificate-profiles-in-configuration-manager"></a>Configuration Manager의 인증서 프로필 소개

*적용 대상: Configuration Manager(현재 분기)*

인증서 프로필은 Active Directory 인증서 서비스 및 NDES(네트워크 디바이스 등록 서비스) 역할에서 작동합니다. 사용자가 조직 리소스에 쉽게 액세스할 수 있도록 관리되는 디바이스에 대한 인증 인증서를 만들고 배포하세요. 예를 들어, 인증서 프로필을 만들고 배포하여 사용자가 VPN 및 무선 연결을 시작하는 데 필요한 인증서를 제공할 수 있습니다.

인증서 프로필은 Wi-fi 네트워크 및 VPN 서버와 같은 조직 리소스에 액세스 하기 위해 사용자 장치를 자동으로 구성할 수 있습니다. 사용자는 수동으로 인증서를 설치 하거나 대역 외 프로세스를 사용 하지 않고도 이러한 리소스에 액세스할 수 있습니다. 인증서 프로필은 PKI(공개 키 인프라)가 지원하는 보안 설정을 더 많이 사용할 수 있으므로 리소스를 보호하는 데 도움이 됩니다. 예를 들어 관리되는 디바이스에 필요한 인증서를 배포했기 때문에 모든 Wi-Fi 및 VPN 연결에 대해 서버 인증을 요구할 수 있습니다.

인증서 프로필이 제공하는 관리 기능  

- 다른 OS 유형 및 버전을 실행 하는 장치에 대 한 CA (인증 기관)에서 인증서 등록 및 갱신. 이후에 Wi-Fi 및 VPN 연결에 이러한 인증서를 사용할 수 있습니다.  

- 신뢰할 수 있는 루트 CA 인증서 및 중간 CA 인증서 배포. 이러한 인증서는 서버 인증이 필요한 경우 VPN 및 Wi-Fi 연결용 디바이스에서 신뢰 체인을 구성합니다.  

- 설치된 인증서를 모니터링하고 보고하는 기능  

**예 1**: 모든 직원이 여러 사무실 위치에서 wi-fi 핫스팟에 연결 해야 합니다. 사용자가 손쉽게 연결할 수 있도록 하려면 먼저 Wi-Fi에 연결하는 데 필요한 인증서를 배포합니다. 그런 다음, 인증서를 참조하는 Wi-Fi 프로필을 배포합니다.  

**예제 2**: 현재 PKI를 사용 중입니다. 더 유연하고 안전한 인증서 배포 방법으로 전환하려고 합니다. 사용자는 보안을 손상 시 키 지 않고 개인 장치에서 조직 리소스에 액세스 해야 합니다. 특정 디바이스 플랫폼을 지원하는 설정 및 프로토콜을 사용하여 인증서 프로필을 구성합니다. 그러고 나면 디바이스는 인터넷에 연결된 등록 서버에서 이 인증서를 자동으로 요청할 수 있습니다. 그런 다음 디바이스가 조직 리소스에 액세스할 수 있도록 VPN 프로필을 구성하여 이러한 인증서를 사용합니다.  

## <a name="types"></a>유형

인증서 프로필에는 다음과 같이 세 가지 유형이 있습니다.  

- **신뢰할 수 있는 CA 인증서**: 신뢰할 수 있는 루트 CA 또는 중간 CA 인증서를 배포합니다. 디바이스에서 서버를 인증해야 하는 경우 이러한 신뢰 체인을 형성합니다.  

- **SCEP(단순 인증서 등록 프로토콜)** : SCEP 프로토콜을 사용하여 디바이스 또는 사용자에 대한 인증서를 요청합니다. 이 유형의 경우 Windows Server 2012 R2 이상을 실행 중인 서버에 대한 NDES(네트워크 디바이스 등록 서비스) 역할이 필요합니다.

    **SCEP(단순 인증서 등록 프로토콜)** 인증서 프로필을 만들려면 먼저 **신뢰할 수 있는 CA 인증서** 프로필을 만듭니다.

- **개인 정보 교환(.pfx)** : 디바이스 또는 사용자에 대한 .pfx(PKCS #12라고도 함) 인증서를 요청합니다.<!--1321368--> PFX 인증서 프로필을 만드는 방법에는 두 가지가 있습니다.

  - 기존 인증서에서 [자격 증명 가져오기](/configmgr/mdm/deploy-use/import-pfx-certificate-profiles)
  - 요청을 처리할 [인증 기관 정의](/configmgr/mdm/deploy-use/create-pfx-certificate-profiles)

  > [!Note]  
  > Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/configmgr/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  

  Microsoft 또는 Entrust를 **개인 정보 교환(.pfx)** 인증서의 인증 기관으로 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항

SCEP를 사용하는 인증서 프로필을 배포하려면 사이트 시스템 서버에 인증서 등록 지점을 설치해야 합니다. 또한 Windows Server 2012 R2 이상을 실행하는 서버에 NDES용 정책 모듈인 Configuration Manager 정책 모듈을 설치해야 합니다. 이 서버에는 Active Directory 인증서 서비스 역할이 필요 합니다. 또한 인증서가 필요한 장치에 액세스할 수 있는 작업 NDES가 필요 합니다. 장치가 인터넷에서 인증서를 등록 해야 하는 경우 인터넷에서 NDES 서버에 액세스할 수 있어야 합니다. 예를 들어 인터넷에서 NDES 서버에 대 한 트래픽을 안전 하 게 사용 하도록 설정 하려면 [Azure 애플리케이션 프록시](https://docs.microsoft.com/azure/active-directory/manage-apps/application-proxy)를 사용할 수 있습니다.

PFX 인증서에 인증서 등록 지점도 필요합니다. 또한 인증서에 대한 CA(인증 기관)를 지정하고 관련 액세스 자격 증명을 지정해야 합니다. Microsoft 또는 Entrust를 인증 기관으로 지정할 수 있습니다.  

Configuration Manager가 인증서를 배포할 수 있도록 NDES에서 정책 모듈을 지원하는 방법에 대한 자세한 내용은 [네트워크 디바이스 등록 서비스와 함께 정책 모듈 사용](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn473016\(v=ws.11\))을 참조하세요.

Configuration Manager에서는 요구 사항에 따라 다양한 디바이스 유형 및 운영 체제의 여러 인증서 저장소에 대한 인증서 배포를 지원합니다. 다음 디바이스 및 운영 체제가 지원됩니다.  

- Windows 10

- Windows 10 Mobile

- Windows 8.1  

- Windows Phone 8.1  

> [!NOTE]  
> Configuration Manager 온-프레미스 MDM을 사용 하 여 Windows Phone 8.1 및 Windows 10 Mobile을 관리 합니다. 자세한 내용은 [온-프레미스 MDM](/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)을 참조하세요.

Configuration Manager에 대 한 일반적인 시나리오는 Wi-fi 및 VPN 서버를 인증 하기 위해 신뢰할 수 있는 루트 CA 인증서를 설치 하는 것입니다. 일반적인 연결은 다음 프로토콜을 사용 합니다.

- 인증 프로토콜: eap-tls, EAP-TTLS 및 PEAP
- VPN 터널링 프로토콜: IKEv2, L2TP/IPsec 및 Cisco IPsec

디바이스에서 SCEP 인증서 프로필을 사용하여 인증서를 요청하려면 먼저 디바이스에 엔터프라이즈 루트 CA 인증서가 설치되어 있어야 합니다.  

여러 환경 또는 연결 요구 사항에 맞게 사용자 지정된 인증서를 요청할 수 있도록 SCEP 인증서 프로필에서 설정을 지정할 수 있습니다. **인증서 프로필 만들기 마법사**에는 등록 매개 변수에 대한 두 페이지가 있습니다. 먼저 **SCEP 등록**에는 등록 요청 및 인증서를 설치할 위치에 대한 설정이 포함되어 있습니다. 두 번째 페이지인 **인증서 속성**에서는 요청된 인증서 자체에 대해 설명합니다.  

## <a name="deploy"></a>배포

SCEP 인증서 프로필을 배포할 때 Configuration Manager 클라이언트는 정책을 처리 합니다. 그런 다음 관리 지점에서 SCEP 챌린지 암호를 요청 합니다. 장치에서 공개/개인 키 쌍을 만들고 CSR (인증서 서명 요청)을 생성 합니다. NDES 서버에이 요청을 보냅니다. NDES 서버는 NDES 정책 모듈을 통해 인증서 등록 지점 사이트 시스템에 요청을 전달 합니다. 인증서 등록 지점은 요청의 유효성을 검사 하 고 SCEP 챌린지 암호를 확인 한 후 요청이 변조 되지 않았는지 확인 합니다. 그런 다음 요청을 승인 하거나 거부 합니다. 승인 되 면 NDES 서버는 서명 요청을 서명 하기 위해 연결 된 CA (인증 기관)로 보냅니다. CA는 요청에 서명한 다음 요청 하는 장치에 인증서를 반환 합니다.

사용자 또는 장치 컬렉션에 인증서 프로필을 배포 합니다. 각 인증서의 대상 저장소를 지정할 수 있습니다. 적용 가능성 규칙은 장치에서 인증서를 설치할 수 있는지 여부를 결정 합니다.

인증서 프로필을 사용자 컬렉션에 배포하면 [사용자 디바이스 선호도](/configmgr/apps/deploy-use/link-users-and-devices-with-user-device-affinity)에 따라 인증서를 설치할 사용자 디바이스가 결정됩니다. 사용자 인증서가 포함 된 인증서 프로필을 장치 컬렉션에 배포 하는 경우 기본적으로 각 사용자의 기본 장치에서 인증서를 설치 합니다. 사용자의 디바이스에 인증서를 설치하려면 **인증서 프로필 만들기 마법사**의 **SCEP 등록** 페이지에서 이 동작을 변경합니다. 장치가 작업 그룹에 있는 경우 Configuration Manager 사용자 인증서를 배포 하지 않습니다.  

## <a name="monitor"></a>모니터

준수 결과 또는 보고서를 확인하여 인증서 프로필 배포를 모니터링할 수 있습니다. 자세한 내용은 [인증서 프로필을 모니터링 하는 방법](/configmgr/protect/deploy-use/monitor-certificate-profiles)을 참조 하세요.

## <a name="automatic-revocation"></a>자동 해지

Configuration Manager는 다음과 같은 상황에서 인증서 프로필을 사용하여 배포된 사용자 및 컴퓨터 인증서를 자동으로 해지합니다.  

- 장치가 Configuration Manager 관리에서 사용 중지 됩니다.  

- 디바이스가 Configuration Manager 계층 구조에서 차단되었습니다.  

인증서를 해지하기 위해 사이트 서버가 발급 인증 기관으로 해지 명령을 보냅니다. 해지의 원인은 **사용 중단**입니다.

> [!NOTE]
> 인증서를 올바르게 해지 하려면 계층의 최상위 사이트에 대 한 컴퓨터 계정에 CA에서 **인증서를 발급 하 고 관리** 하기 위한 사용 권한이 있어야 합니다.
>
> 보안 향상을 위해 CA 관리자를 제한할 수도 있습니다. 그런 다음 사이트의 SCEP 프로필에 사용 하는 특정 인증서 템플릿에 대해이 계정 권한만 제공 합니다.

## <a name="next-steps"></a>다음 단계

- [인증서 프로필 만들기](/configmgr/protect/deploy-use/create-certificate-profiles)

- [인증서 인프라 구성](/configmgr/protect/deploy-use/certificate-infrastructure)
