---
title: 'VPN 프로필을 만드는 방법 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 VPN 프로필을 만드는 방법을 알아봅니다.
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bb5814860389de28294c44f367920a2da9b72fbe
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53419430"
---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 VPN 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

다양한 디바이스 플랫폼에서 사용할 수 있는 연결 형식에 대한 자세한 내용은 [System Center Configuration Manager의 VPN 프로필](../../protect/deploy-use/vpn-profiles.md)을 참조하세요.  

타사 VPN 연결의 경우 VPN 프로필을 배포하기 전에 VPN 앱을 배포합니다. 앱을 배포하지 않고 VPN에 연결하려고 하면 앱을 배포하라는 메시지가 표시됩니다. 앱을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.

### <a name="create-a-vpn-profile"></a>VPN 프로필 만들기   

1. Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **회사 리소스 액세스** > **VPN 프로필**을 선택합니다.  

2. **홈** 탭의 **만들기** 그룹에서 **VPN 프로필 만들기**를 선택합니다.  


3. **일반** 페이지를 완료합니다. 다음 사항에 유의하십시오.  

   - 적절한 **플랫폼**을 선택합니다.

      - Windows 8.1 플랫폼을 선택하면 **파일에서 기존 VPN 프로필 항목 가져오기**를 선택하여 XML 파일로 내보낸 VPN 프로필 정보를 가져오는 옵션이 있습니다.

   - VPN 프로필 이름에 \\/:*?&lt;>&#124; 문자나 공백 문자를 사용하지 마세요. 이러한 문자는 Windows Server VPN 프로필에서 지원되지 않습니다.  


4. **연결** 페이지에서 다음을 지정합니다.  

   - 연결 유형 VPN 연결 형식을 선택 합니다. 다음 표에 있는 연결 형식 중에서 선택할 수 있습니다.  

   - **서버 목록**: VPN 연결에 사용할 새 서버를 추가합니다. 연결 형식에 따라 VPN 서버를 하나 이상 선택하고 기본 서버를 지정할 수 있습니다.  

     > [!NOTE]  
     >  iOS를 실행하는 디바이스에서는 여러 VPN 서버를 사용할 수 없습니다. 여러 VPN 서버를 구성한 후 VPN 프로필을 iOS 디바이스에 배포하는 경우 기본 서버만 사용됩니다.  

     이 표에서는 연결 형식 옵션을 제공합니다. 자세한 내용은 VPN 서버 설명서를 참조하세요.

| &nbsp;&nbsp;옵션&nbsp;&nbsp; | 추가 정보 | &nbsp;&nbsp;연결&nbsp;유형&nbsp;&nbsp; |  
|----------------|----------------------|---------------------|  
|**영역**     |사용하려는 인증 영역. 인증 영역은 Pulse Secure 연결 유형에서 사용되는 인증 리소스 그룹입니다.|Pulse Secure|    
|**역할**        |이 연결에 대한 액세스 권한이 있는 사용자 역할. |Pulse Secure|  
|**로그인 그룹 또는 도메인** |연결하려는 로그인 그룹 또는 도메인의 이름.|Dell SonicWALL Mobile Connect|  
|**지문**  |신뢰할 수 있는 VPN 서버를 확인하는 데 사용할 문자열(예: 'Contoso 지문 코드').<br /><br /> 지문은 다음과 같은 작업에 사용할 수 있습니다.<br /><br /> - 연결 시 동일한 지문을 제시하는 서버는 신뢰할 수 있다는 것을 알 수 있도록 클라이언트에 전송됩니다.<br /><br /> - 디바이스에 지문이 아직 없으면 사용자에게 지문을 보여주면서 연결하려는 VPN 서버를 신뢰할 것인지 묻는 메시지가 표시됩니다. 사용자는 지문을 수동으로 확인한 후 연결 **신뢰**를 선택합니다.|검사점 모바일 VPN|  
|**VPN 연결을 통해 모든 네트워크 트래픽 보내기** |이 옵션을 선택하지 않는 경우 연결( **Microsoft SSL(SSTP)**, **Microsoft 자동**, **IKEv2**, **PPTP** 및 **L2TP** 연결 형식의 경우)에 대해 추가 경로를 지정할 수 있습니다. 이러한 경로를 분할 또는 VPN 터널링이라고 합니다.<br /><br /> 회사 네트워크에 대한 연결만 VPN 터널을 통해 보내집니다. VPN 터널링은 인터넷에 있는 리소스에 연결할 경우에는 사용되지 않습니다. |모두|  
|**연결별 DNS 접미사** |연결에 대해 연결별 DNS(Domain Name System) 접미사.|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
|**회사 Wi-Fi 네트워크에 연결된 경우 VPN 무시**  |디바이스가 회사 Wi-Fi 네트워크에 연결된 경우 VPN 연결이 사용되지 않습니다.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN<br /><br /> - Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - L2TP|  
|**홈 Wi-Fi 네트워크 연결 시 VPN 건너뛰기**  |디바이스가 가정용 Wi-Fi 네트워크에 연결된 경우 VPN 연결이 사용되지 않습니다.|모두|  
|**응용 프로그램 VPN(iOS 7 이상, Mac OS X 10.9 및 이후 버전)당** |앱이 실행될 때 연결이 열리도록 이 VPN 연결을 iOS 앱과 연결합니다. 앱을 배포할 때 VPN 프로필을 앱과 연결할 수 있습니다.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN|  
|**사용자 지정 XML(선택 사항)** |VPN 연결을 구성하는 사용자 지정 XML 명령을 지정합니다.<br /><br /> 예제:<br /><br /> **Pulse Secure**의 경우:<br /><br /> **&lt;pulse-schema><br /> &nbsp; &lt;isSingleSignOnCredential>true&lt;/isSingleSignOnCredential\><br />&lt;/pulse-schema>**<br /><br /> **CheckPoint Mobile VPN**의 경우:<br /><br /> **&lt;CheckPointVPN <br /> &nbsp; port="443" name="CheckPointSelfhost" <br /> &nbsp; sso="true" <br /> &nbsp; debug="3"<br />/>**<br /><br /> **Dell SonicWALL Mobile Connect**의 경우:<br /><br /> **&lt;MobileConnect\><br />&nbsp; &nbsp; &lt;Compression\>false&lt;/Compression\><br />&nbsp; &nbsp; &lt;debugLogging\>True&lt;/debugLogging\><br />&nbsp; &nbsp; &lt;packetCapture\>False&lt;/packetCapture\><br />&lt;/MobileConnect\>**<br /><br /> **F5 Edge Client**의 경우:<br /><br /> **&lt;f5-vpn-conf>&lt;single-sign-on-credential>&lt;/f5-vpn-conf>**<br /><br /> 사용자 지정 XML 명령을 작성하는 방법에 대한 자세한 내용은 각 제조업체의 VPN 설명서를 참조하세요.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN|  

> [!NOTE]  
>  모바일 디바이스에 대한 VPN 프로필 만들기에 특정한 정보는 [VPN 프로필 만들기](../../mdm/deploy-use/create-vpn-profiles.md)를 참조하세요.  

마법사를 완료합니다. 새로운 VPN 프로필이 **자산 및 호환성** 작업 영역의 **VPN 프로필** 노드에 표시됩니다.

### <a name="next-steps"></a>다음 단계

- 타사 VPN 연결의 경우 VPN 프로필을 배포하기 전에 VPN 앱을 배포합니다. 앱을 배포하지 않고 VPN에 연결하려고 하면 앱을 배포하라는 메시지가 표시됩니다. 앱을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.

- [System Center Configuration Manager에서 프로필을 배포하는 방법](deploy-wifi-vpn-email-cert-profiles.md)에 설명된 대로 VPN 프로필을 배포합니다.  
