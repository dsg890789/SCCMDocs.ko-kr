---
title: "System Center Configuration Manager의 VPN 프로필 | System Center Configuration Manager"
description: "System Center Configuration Manager의 VPN 프로필을 사용하여 VPN 설정을 조직의 사용자에게 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/10/2016
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
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 0fbce476b8a9b91a88354fb4abfadfd2526ca5e8
ms.openlocfilehash: dda572392884c54b63af09a9fae79c1e73eb3d95


---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 VPN 프로필

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 VPN 프로필을 사용하여 VPN 설정을 조직의 사용자에게 배포할 수 있습니다. 이러한 설정을 배포하여 최종 사용자가 회사 네트워크에 있는 리소스에 연결하는 데 필요한 노력을 최소화할 수 있습니다.  

 예를 들어, 기업 네트워크의 파일 공유에 연결하는 데 필요한 설정을 사용하여 iOS 운영 체제를 실행하는 모든 장치를 프로비전하려고 합니다. 기업 네트워크에 연결하는 데 필요한 설정이 포함된 VPN 프로필을 만든 다음 이 프로필을 조직 계층에서 iOS를 실행하는 장치를 가진 모든 사용자에게 배포할 수 있습니다. iOS 장치 사용자는 사용 가능한 네트워크의 목록에서 VPN 연결을 확인하고 최소의 노력으로 이 네트워크에 연결할 수 있습니다.  

 VPN 프로필을 만들 때 System Center Configuration Manager 인증서 프로필을 사용하여 프로비전한 서버 유효성 검사 및 클라이언트 인증용 인증서를 포함한 다양한 보안 설정을 포함할 수 있습니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

 아래 섹션에서는 Configuration Manager를 사용하거나 Configuration Manager 및 Microsoft Intune을 사용하는 경우 VPN 프로필에서 구성할 수 있는 장치를 설명합니다.  

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

## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>Configuration Manager 및 Intune을 사용하는 경우의 VPN 프로필  
 iOS, Android, Windows Phone 및 Windows 8.1 장치에 프로필을 배포하려면 이러한 장치를 Microsoft Intune에 등록해야 합니다. 다른 플랫폼의 장치를 Intune에 등록할 수도 있습니다. 등록하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 모바일 장치 관리](https://technet.microsoft.com/en-us/library/dn646962.aspx)를 참조하세요. 이 표에서는 각 장치 플랫폼에 대해 지원되는 연결 형식을 보여 줍니다.  

|연결 유형|iOS 및 Mac OS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop 및 Mobile|  
|---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
|Cisco AnyConnect|예|예|아니요|아니요|아니요|아니요|예(OMA-URI)|  
|Pulse Secure|예|예|예|아니요|예|예|예|  
|F5 Edge Client|예|예|예|아니요|예|예|예|  
|Dell SonicWALL Mobile Connect|예|예|예|아니요|예|예|예|  
|검사점 모바일 VPN|예|예|예|아니요|예|예|예|  
|Microsoft SSL(SSTP)|아니요|아니요|예|예|예|아니요|아니요|  
|Microsoft 자동|아니요|아니요|예|예|예|아니요|예(OMA-URI)|  
|IKEv2|예(사용자 지정 정책)|아니요|예|예|예|예|예(OMA-URI)|  
|PPTP|예|아니요|예|예|예|아니요|예(OMA-URI)|  
|L2TP|예|아니요|예|예|예|아니요|예(OMA-URI)|  

### <a name="next-steps"></a>다음 단계  
 다음 항목에서는 Configuration Manager의 VPN 프로필을 계획, 구성, 운영 및 유지 관리하는 방법을 설명합니다.  

-   [System Center Configuration Manager에서 VPN 프로필에 대한 필수 조건](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [System Center Configuration Manager에서 VPN 프로필에 대한 보안 및 개인 정보](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)



<!--HONumber=Nov16_HO1-->


