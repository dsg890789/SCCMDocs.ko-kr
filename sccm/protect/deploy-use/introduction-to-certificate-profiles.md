---
title: "인증서 프로필 소개 | Microsoft 문서"
description: "System Center Configuration Manager의 인증서 프로필이 Active Directory 인증서 서비스에서 작동하는 방식을 알아봅니다."
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 41dcc259-f147-4420-bff2-b65bdf8cff77
caps.latest.revision: 7
author: arob98
ms.author: angrobe
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 8a5dc7361da34f3e6b926acd35c72c0c0767ce70
ms.openlocfilehash: d51670b47aab77cc4e630a6aeaa0744f916bf3b9
ms.lasthandoff: 12/30/2016


---
# <a name="introduction-to-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 인증서 프로필 소개

*적용 대상: System Center Configuration Manager(현재 분기)*


인증서 프로필은 사용자가 회사 리소스에 원활하게 액세스할 수 있도록 Active Directory 인증서 서비스 및 네트워크 장치 등록 서비스 역할과 연동하여 관리되는 장치에 인증 인증서를 프로비전합니다. 예를 들어, 인증서 프로필을 만들고 배포하여 사용자가 VPN 및 무선 연결을 시작하는 데 필요한 인증서를 제공할 수 있습니다. 

인증서 프로필은 수동으로 인증서를 설치하거나 대역 외 프로세스를 사용하지 않고도 Wi-Fi 네트워크 및 VPN 서버와 같은 회사 리소스에 액세스할 수 있도록 자동으로 사용자 장치를 구성할 수 있습니다. 인증서 프로필은 엔터프라이즈 PKI(공개 키 인프라)가 지원하는 안전한 설정을 더 많이 사용할 수 있으므로 회사 리소스를 안전하게 유지하는 데도 도움이 됩니다. 예를 들어, 관리되는 장치에 필요한 인증서를 프로비전했기 때문에 모든 Wi-Fi 및 VPN 연결에 대해 서버 인증을 요구할 수 있습니다.   

인증서 프로필이 제공하는 관리 기능  

-   iOS, Windows 8.1, Windows RT 8.1, Windows 10 Desktop 및 Mobile, Android를 실행하는 장치의 엔터프라이즈 CA(인증 기관)에서 인증서 등록 및 갱신. 이후에 Wi-Fi 및 VPN 연결에 이러한 인증서를 사용할 수 있습니다.  

-   서버 인증이 필요한 경우 VPN 및 Wi-Fi 연결용 장치에서 신뢰 체인을 구성할 수 있도록 신뢰할 수 있는 루트 CA 인증서 및 중간 CA 인증서 배포  

-   설치된 인증서를 모니터링하고 보고하는 기능  

**예:** 모든 직원이 회사의 여러 위치에서 Wi-Fi 핫스폿에 연결할 수 있어야 합니다. Wi-Fi 연결에 필요한 인증서를 배포하고, 사용자를 원활하게 연결하기 위해 인증서를 참조하는 Wi-Fi 프로필을 배포합니다.  

**예:** PKI를 보유하고 있으며, 보안 수준을 그대로 유지하면서 사용자가 개인 장치에서 회사 리소스에 액세스할 수 있는 보다 유연하고 안전한 인증서 프로비전 방법으로 바꾸려는 경우. 특정 장치 플랫폼을 지원하는 설정 및 프로토콜을 사용하여 인증서 프로필을 구성합니다. 그러고 나면 장치는 인터넷에 연결된 등록 서버에서 이 인증서를 자동으로 요청할 수 있습니다. 그런 다음 장치가 회사 리소스에 액세스할 수 있도록 VPN 프로필을 구성하여 이러한 인증서를 사용합니다.  

## <a name="types-of-certificate-profiles"></a>인증서 프로필 유형  
 인증서 프로필에는 다음과 같이 세 가지 유형이 있습니다.  

-   **신뢰할 수 있는 CA 인증서** - 장치에서 서버를 인증해야 할 경우 신뢰할 수 있는 루트 CA 또는 중간 CA 인증서를 배포하여 인증서 신뢰 체인을 형성할 수 있습니다.  

-   **SCEP(단순 인증서 등록 프로토콜)** - Windows Server 2012 R2를 실행하는 서버의 네트워크 장치 등록 서비스 및 SCEP 프로토콜을 사용하여 장치 또는 사용자에 대한 인증서를 요청할 수 있습니다.
-   -   **개인 정보 교환(.pfx)** - 장치 또는 사용자에 대한 .pfx(PKCS #12라고도 함) 인증서를 요청할 수 있습니다.

    > [!NOTE]  
    >  **SCEP(단순 인증서 등록 프로토콜)** 인증서 프로필을 만들려면 먼저 **신뢰할 수 있는 CA 인증서** 유형의 인증서 프로필을 만들어야 합니다.  

## <a name="requirements-and-supported-platforms"></a>요구 사항 및 지원되는 플랫폼  
 SCEP를 사용하는 인증서 프로필을 배포하려면 중앙 관리 사이트나 기본 사이트의 사이트 시스템 서버에 인증서 등록 지점을 설치해야 합니다. 작동 중인 NDES(인증서를 요구하는 장치에 액세스 가능) 및 Active Directory 인증서 서비스 역할과 함께 Windows Server 2012 R2를 실행하는 서버에 NDES용 정책 모듈인, Configuration Manager 정책 모듈도 설치해야 합니다. Microsoft Intune에서 등록된 장치의 경우 NDES를 인터넷(예: DMZ라고도 하는 스크린된 서브넷)에서 액세스할 수 있어야 합니다.  

 Configuration Manager가 인증서를 배포할 수 있도록 네트워크 장치 등록 서비스에서 정책 모듈을 지원하는 방법에 대한 자세한 내용은 [네트워크 장치 등록 서비스와 함께 정책 모듈 사용](http://go.microsoft.com/fwlink/p/?LinkId=328657)을 참조하세요.  

 Configuration Manager에서는 요구 사항, 장치 유형 및 운영 체제에 따라 여러 인증서 저장소에 인증서를 배포할 수 있습니다. 다음 장치 및 운영 체제가 지원됩니다.  

-   Windows RT 8.1  

-   Windows 8.1  

-   Windows Phone 8.1  

-   Windows 10 Desktop 및 Mobile  

-   iOS  

-   Android  

> [!IMPORTANT]  
>  Android, iOS, Windows Phone 및 등록된 Windows 8.1 이상 장치에 프로필을 배포하려면 이러한 장치를 [Microsoft Intune에 등록](https://technet.microsoft.com/en-us/library/dn646962.aspx)해야 합니다.   

System Center Configuration Manager의 일반적인 시나리오는 연결 시 EAP-TLS, EAP-TTLS 및 PEAP 인증 프로토콜과 IKEv2, L2TP/IPsec 및 Cisco IPsec VPN 터널링 프로토콜을 사용할 경우 Wi-Fi 및 VPN 서버를 인증할 신뢰할 수 있는 루트 CA 인증서를 설치하는 것입니다.  

장치에서 SCEP 인증서 프로필을 사용하여 인증서를 요청하려면 먼저 장치에 엔터프라이즈 루트 CA 인증서가 설치되어 있어야 합니다.  

여러 환경 또는 연결 요구 사항에 맞게 사용자 지정된 인증서를 요청할 수 있도록 SCEP 인증서 프로필에서 여러 가지 설정을 지정할 수 있습니다. **인증서 프로필 만들기 마법사** 에는 등록 매개 변수에 대한 두 페이지가 포함되어 있습니다. 먼저 **SCEP 등록**에는 등록 요청 및 인증서를 설치할 위치에 대한 설정이 포함되어 있습니다. 두 번째 페이지인 **인증서 속성**에서는 요청된 인증서 자체에 대해 설명합니다.  

## <a name="deploying-certificate-profiles"></a>인증서 프로필 배포  
 인증서 프로필을 배포할 때 프로필 내의 인증서 파일이 클라이언트 장치에 설치됩니다. 모든 SCEP 매개 변수도 배포되고 SCEP 요청이 클라이언트 장치에서 처리됩니다. 사용자 또는 장치 컬렉션에 인증서 프로필을 배포하고 각 인증서의 대상 저장소를 지정할 수 있습니다. 적용 가능성 규칙은 장치에 인증서를 설치할 수 있는지 여부를 결정합니다. 인증서 프로필을 사용자 컬렉션에 배포하면 사용자 장치 선호도에 따라 인증서를 설치할 사용자 장치가 결정됩니다. 사용자 인증서가 포함된 인증서 프로필을 장치 컬렉션에 배포하면 기본적으로 사용자의 각 기본 장치에 인증서가 설치됩니다. **인증서 프로필 만들기 마법사**의 **SCEP 등록** 페이지에서 사용자의 장치에 인증서를 설치하도록 이 동작을 수정할 수 있습니다. 또한, 장치가 작업 그룹 컴퓨터인 경우 사용자 인증서가 장치에 배포되지 않습니다.  

## <a name="monitoring-certificate-profiles"></a>인증서 프로필 모니터링  

준수 결과 또는 보고서를 확인하여 인증서 프로필 배포를 모니터링할 수 있습니다. 이러한 접근법은 [인증서 프로필을 모니터링하는 방법](/sccm/protect/deploy-use/monitor-certificate-profiles)에서 설명합니다.


## <a name="automatic-revocation-of-certificates"></a>인증서 자동 해지  
 System Center Configuration Manager는 다음과 같은 상황에서 인증서 프로필을 사용하여 배포된 사용자 및 컴퓨터 인증서를 자동으로 해지합니다.  

-   System Center Configuration Manager 관리에서 장치 사용이 중지되었습니다.  

-   장치가 선택적으로 초기화됩니다.  

-   장치가 System Center Configuration Manager 계층 구조에서 차단되었습니다.  

 인증서를 해지하기 위해 사이트 서버가 발급 인증 기관으로 해지 명령을 보냅니다. 해지의 원인은 **사용 중단**입니다.  

