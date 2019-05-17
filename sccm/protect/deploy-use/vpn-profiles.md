---
title: VPN 프로필
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 VPN 프로필을 사용하여 VPN 설정을 조직의 사용자에게 배포하는 방법을 알아봅니다.
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 505a4f3c00bc69e115b4130d422e11d8dec3fe30
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65500392"
---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 VPN 프로필

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1283610-->
조직의 사용자에게 VPN 설정을 배포하려면 Configuration Manager에서 VPN 프로필을 사용합니다. 이러한 설정을 배포하여 최종 사용자가 회사 네트워크에 있는 리소스에 연결하는 데 필요한 노력을 최소화할 수 있습니다.  

 예를 들어 기업 네트워크에서 파일 공유에 연결하는 데 필요한 설정을 사용하여 모든 Windows 10 디바이스를 구성하려고 할 수 있습니다. 기업 네트워크에 연결하는 데 필요한 설정을 사용하여 VPN 프로필을 만들 수 있습니다. 그런 다음, Windows 10을 실행하는 디바이스를 사용하는 모든 사용자에게 이 프로필을 배포합니다. 이러한 사용자에게 이용 가능한 네트워크 목록에 대한 VPN 연결이 표시되어 간편하게 연결할 수 있습니다.  

 VPN 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 이러한 설정에는 사용자가 Configuration Manager 인증서 프로필을 사용하여 프로비전하는 서버 유효성 검사 및 클라이언트 인증용 인증서가 포함됩니다. 자세한 내용은 [인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  


 Microsoft Intune과 함께 Configuration Manager를 사용하는 경우 구성할 수 있는 디바이스를 검토하려면 [모바일 디바이스의 VPN 프로필](/sccm/mdm/deploy-use/create-vpn-profiles)을 참조하세요.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>Configuration Manager를 사용하는 경우의 VPN 프로필  
 다음 표에서는 다양한 디바이스 플랫폼에 대해 구성할 수 있는 VPN 프로필을 설명합니다.  

|연결 유형|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|아니요|아니요|아니요|아니요|  
|**Pulse Secure**|예|아니요|예|예|  
|**F5 Edge Client**|예|아니요|예|예|  
|**Dell SonicWALL Mobile Connect**|예|아니요|예|예|  
|**Check Point Mobile VPN**|예|아니요|예|예|  
|**Microsoft SSL(SSTP)**|예|예|예|아니요|  
|**Microsoft Automatic**|예|예|예|아니요|  
|**IKEv2**|예|예|예|아니요|  
|**PPTP**|예|예|예|아니요|  
|**L2TP**|예|예|예|아니요|  

### <a name="next-steps"></a>다음 단계  
 다음 항목에서는 Configuration Manager의 VPN 프로필을 계획, 구성, 운영 및 유지 관리하는 방법을 설명합니다.  

-   [System Center Configuration Manager에서 VPN 프로필에 대한 필수 조건](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [System Center Configuration Manager에서 VPN 프로필에 대한 보안 및 개인 정보](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
