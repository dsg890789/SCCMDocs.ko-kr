---
title: "System Center Configuration Manager의 VPN 프로필 | Microsoft 문서"
description: "System Center Configuration Manager의 VPN 프로필을 사용하여 VPN 설정을 조직의 사용자에게 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: c11440556abc11d2c19ee0ff3c2bc9e518951e49
ms.contentlocale: ko-kr
ms.lasthandoff: 03/04/2017


---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 VPN 프로필

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager(ConfigMgr 또는 SCCM이라고도 함)의 VPN 프로필을 사용하여 VPN 설정을 조직의 사용자에게 배포할 수 있습니다. 이러한 설정을 배포하여 최종 사용자가 회사 네트워크에 있는 리소스에 연결하는 데 필요한 노력을 최소화할 수 있습니다.  

 예를 들어, 기업 네트워크의 파일 공유에 연결하는 데 필요한 설정을 사용하여 Windows RT 운영 체제를 실행하는 모든 장치를 프로비전하려고 합니다. 기업 네트워크에 연결하는 데 필요한 설정이 포함된 VPN 프로필을 만든 다음 이 프로필을 조직 계층에서 Windows RT를 실행하는 장치를 가진 모든 사용자에게 배포할 수 있습니다. Windows RT 장치 사용자는 사용 가능한 네트워크의 목록에서 VPN 연결을 확인하고 최소의 노력으로 이 네트워크에 연결할 수 있습니다.  

 VPN 프로필을 만들 때 System Center Configuration Manager 인증서 프로필을 사용하여 프로비전한 서버 유효성 검사 및 클라이언트 인증용 인증서를 포함한 다양한 보안 설정을 포함할 수 있습니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

 아래 섹션에서는 Configuration Manager를 사용하는 경우 VPN 프로필에서 구성할 수 있는 장치를 설명합니다.

 Microsoft Intune과 함께 Configuration Manager를 사용하는 경우 구성할 수 있는 장치를 검토하려면 [모바일 장치의 VPN 프로필](/sccm/mdm/deploy-use/create-vpn-profiles)을 참조하세요.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>Configuration Manager를 사용하는 경우의 VPN 프로필  
 다음 표에서는 다양한 장치 플랫폼에 대해 구성할 수 있는 VPN 프로필을 설명합니다.  

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

