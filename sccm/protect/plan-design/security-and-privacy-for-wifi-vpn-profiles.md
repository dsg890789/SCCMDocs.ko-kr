---
title: "Wi-Fi 및 VPN 프로필 보안 및 개인 정보 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 장치의 Wi-Fi 및 VPN 프로필 관리에 대한 보안 모범 사례를 알아봅니다."
ms.custom: na
ms.date: 10/19/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
caps.latest.revision: 4
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 32dff36aa8027b0563b999e7fe6ef41d0eb79020
ms.openlocfilehash: b9d70018708ab5932a3032134b03aef236ef9fda


---
# <a name="security-and-privacy-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Wi-Fi 및 VPN 프로필에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*


이 항목에는 System Center Configuration Manager의 Wi-Fi 및 VPN 프로필에 대한 보안 및 개인 정보가 포함되어 있습니다.  

##  <a name="a-namebkmksecurityremoteconnectionsa-security-best-practices-for-wi-fi-and-vpn-profiles"></a><a name="BKMK_Security_RemoteConnections"></a> Wi-Fi 및 VPN 프로필에 대한 보안 모범 사례  
 장치의 Wi-Fi 및 VPN 프로필을 관리하는 경우 다음 보안 모범 사례를 따르세요.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|가능하면 Wi-Fi 및 VPN 인프라 및 클라이언트 운영 체제에서 지원할 수 있는 가장 강력한 보안 옵션을 선택합니다.|Wi-Fi 및 VPN 프로필을 사용하면 장치에서 이미 지원하는 Wi-Fi 및 VPN 설정을 중앙에서 편리하게 배포하고 관리할 수 있습니다. System Center Configuration Manager는 Wi-Fi 및 VPN 기능을 추가하지 않습니다.<br /><br /> 장치와 인프라에 권장되는 모든 보안 모범 사례를 식별하여 구현하고 따르십시오.|  

## <a name="privacy-information-for-wi-fi-profiles"></a>Wi-Fi 프로필에 대한 개인 정보  
 Wi-Fi 및 VPN 프로필을 사용하여 클라이언트 장치를 Wi-Fi 및 VPN 서버에 연결하도록 구성하고 프로필을 적용한 후에 해당 장치가 호환되는지 여부를 평가할 수 있습니다. 관리 지점에서 호환성 정보를 사이트 서버로 보내며, 해당 정보는 사이트 데이터베이스에 저장됩니다. 장치에서 관리 지점으로 정보를 보낼 때 정보가 암호화되지만 사이트 데이터베이스에는 암호화된 형식으로 저장되지 않습니다. 이 데이터베이스는 사이트 유지 관리 작업인 **오래된 구성 관리 데이터 삭제** 에서 정보를 삭제할 때까지 해당 정보를 보존합니다. 기본 삭제 간격은 90일이지만 변경할 수 있습니다. 호환성 정보는 Microsoft로 전송되지 않습니다.  

 기본적으로 장치는 Wi-Fi 및 VPN 프로필을 평가하지 않습니다. 또한 프로필을 구성한 다음 사용자에게 배포해야 합니다.  

 Wi-Fi 및 VPN 프로필을 구성하려면 먼저 개인 정보 요구 사항을 고려합니다.  



<!--HONumber=Nov16_HO1-->


