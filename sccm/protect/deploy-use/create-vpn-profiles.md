---
title: "System Center Configuration Manager에서 VPN 프로필을 만드는 방법"
description: "System Center Configuration Manager에서 VPN 프로필을 만드는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f338e4db-73b5-45ff-92f4-1b89a8ded989
caps.latest.revision: 15
caps.handback.revision: 0
ms.author: nbigman
ms.manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: e215b33ca24370ddd0e1b892d6ebe559023852a2
ms.openlocfilehash: ccea5cb46bf69dbb88f6fcb217a73c7939be0b02


---
# <a name="how-to-create-vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 VPN 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


> [!NOTE]  
>
> - 다양한 장치 플랫폼에서 사용할 수 있는 연결 형식에 대한 자세한 내용은 [System Center Configuration Manager의 VPN 프로필](../../protect/deploy-use/vpn-profiles.md)을 참조하세요.  
> - 타사 VPN 연결의 경우 VPN 프로필을 배포하기 전에 VPN 앱을 배포합니다. 앱을 배포하지 않고 VPN에 연결하려고 하면 앱을 배포하라는 메시지가 표시됩니다. 앱을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 배포](../../apps/deploy-use/deploy-applications)를 참조하세요.

### <a name="start-the-create-vpn-profile-wizard"></a>VPN 프로필 만들기 마법사 시작  

1.  System Center Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  

2.  System Center Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **준수 설정**, **회사 리소스 액세스**를 차례로 확장하고 **VPN 프로필**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **VPN 프로필 만들기**를 클릭합니다.  

### <a name="provide-general-information-about-the-vpn-profile"></a>VPN 프로필에 대한 일반 정보 제공  

1.  **VPN 프로필 만들기 마법사** 의 **일반**페이지에서 다음 정보를 지정합니다.  

    -   **이름** - VPN 프로필의 고유 이름을 입력합니다(최대 256자).  

        > [!IMPORTANT]  
        >  VPN 프로필 이름에 \\/:*?<>&#124; 문자나 공백 문자를 사용하지 마세요. 이러한 문자는 Windows Server VPN 프로필에서 지원되지 않기 때문입니다.  

    -   **설명** - System Center Configuration Manager 콘솔에서 프로필을 찾는 데 도움이 되는 설명을 입력합니다(최대 256자).  

    -   **파일에서 기존 VPN 프로필 항목 가져오기** – 이 옵션을 선택하면 **VPN 프로필 가져오기** 페이지가 표시됩니다. 이 페이지에서 이전에 XML 파일로 내보낸 VPN 프로필 정보를 가져올 수 있습니다(Windows 8.1 및 Windows RT 운영 체제에만 해당).  

### <a name="provide-connection-information-for-the-vpn-profile"></a>VPN 프로필에 대한 연결 정보 제공  

1.  마법사의 **연결** 페이지에서 다음 정보를 지정합니다.  

    -   **연결 형식:** 드롭다운 목록에서 VPN 연결의 연결 형식을 선택합니다. 지원되는 플랫폼이 나와 있는 다음 표의 연결 형식 중에서 선택할 수 있습니다.  

        > [!IMPORTANT]  
        >  장치에 배포된 VPN 프로필을 사용하려면 먼저 필요한 타사 VPN 앱을 설치해야 합니다. [System Center Configuration Manager에서 응용 프로그램을 만드는 방법](../../apps/deploy-use/create-applications.md) 항목의 정보를 사용하면 System Center Configuration Manager를 사용하여 앱을 배포할 수 있습니다.  

    -   **서버 목록:** **추가** 를 클릭하여 VPN 연결에 사용할 새 서버를 추가합니다. 연결 형식에 따라 VPN 서버를 하나 이상 선택하고 지정한 서버 중에서 기본 서버로 사용할 서버를 지정할 수도 있습니다.  

        > [!NOTE]  
        >  iOS를 실행하는 장치에서는 여러 VPN 서버를 사용할 수 없습니다. 여러 VPN 서버를 구성한 후 VPN 프로필을 iOS 장치에 배포하는 경우 기본 서버만 사용됩니다.  

     선택한 연결 형식에 따라 다음 표의 옵션이 추가로 표시될 수도 있습니다. 자세한 내용은 VPN 서버 설명서를 참조하세요.  

    |옵션|추가 정보|연결 유형|  
    |------------|----------------------|---------------------|  
    |**영역**|사용하려는 인증 영역의 이름을 지정합니다. 인증 영역은 Pulse Secure 연결 유형에서 사용되는 인증 리소스 그룹입니다.|Pulse Secure|  
    |**역할**|이 연결에 대한 액세스 권한이 있는 사용자 역할의 이름을 지정합니다.|Pulse Secure|  
    |**로그인 그룹 또는 도메인**|연결하려는 로그인 그룹 또는 도메인의 이름을 지정합니다.|Dell SonicWALL Mobile Connect|  
    |**지문**|신뢰할 수 있는 VPN 서버를 확인하는 데 사용할 문자열(예: 'Contoso 지문 코드')을 지정합니다.<br /><br /> 지문은 다음과 같은 작업에 사용할 수 있습니다.<br /><br /> - 연결 시 동일한 지문을 제시하는 서버는 신뢰할 수 있다는 것을 알 수 있도록 클라이언트에 전송됩니다.<br /><br /> - 장치에 지문이 아직 없으면 사용자에게 지문을 보여 주면서 연결하려는 VPN 서버를 신뢰할 것인지 묻는 메시지가 표시됩니다. 사용자는 지문을 수동으로 확인한 후 연결 신뢰를 클릭합니다.|검사점 모바일 VPN|  
    |**VPN 연결을 통해 모든 네트워크 트래픽 보내기**|이 옵션을 선택하지 않는 경우 연결( **Microsoft SSL(SSTP)**, **Microsoft 자동**, **IKEv2**, **PPTP** 및 **L2TP** 연결 형식의 경우)에 대해 추가 경로를 지정할 수 있습니다. 이러한 경로를 분할 또는 VPN 터널링이라고 합니다.<br /><br /> 회사 네트워크에 대한 연결만 VPN 터널을 통해 보내집니다. VPN 터널링은 인터넷에 있는 리소스에 연결할 경우에는 사용되지 않습니다.|모두|  
    |**연결별 DNS 접미사**|선택적으로, 연결에 대해 연결별 DNS(Domain Name System) 접미사를 지정합니다.|- <br />                            Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - <br />                            IKEv2<br /><br /> - <br />                            PPTP<br /><br /> - <br />                            L2TP|  
    |**회사 Wi-Fi 네트워크에 연결된 경우 VPN 무시**|장치가 회사 Wi-Fi 네트워크에 연결된 경우 VPN 연결을 사용하지 않도록 지정합니다.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN<br /><br /> - Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - L2TP|  
    |**홈 Wi-Fi 네트워크 연결 시 VPN 건너뛰기**|장치가 가정용 Wi-Fi 네트워크에 연결된 경우 VPN 연결을 사용하지 않도록 지정합니다.|모두|  
    |**응용 프로그램 VPN(iOS 7 이상, Mac OS X 10.9 및 이후 버전)당**|앱이 실행될 때 연결이 열리도록 이 VPN 연결을 iOS 앱과 연결하려면 이 옵션을 선택합니다. 앱을 배포할 때 VPN 프로필을 앱과 연결할 수 있습니다.|- <br />                        Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN|  
    |**사용자 지정 XML(선택 사항)**|VPN 연결을 구성하는 사용자 지정 XML 명령을 지정할 수 있습니다.<br /><br /> 예제:<br /><br /> **Pulse Secure**의 경우:<br /><br /> **<pulse-schema><isSingleSignOnCredential\>true</isSingleSignOnCredential\></pulse-schema>**<br /><br /> **CheckPoint Mobile VPN**의 경우:<br /><br /> **&lt;CheckPointVPN port="443" name="CheckPointSelfhost" sso="true" debug="3" /\>**<br /><br /> **Dell SonicWALL Mobile Connect**의 경우:<br /><br /> **<MobileConnect\><Compression\>false</Compression\><debugLogging\>True</debugLogging\><packetCapture\>False</packetCapture\></MobileConnect\>**<br /><br /> **F5 Edge Client**의 경우:<br /><br /> **&lt;f5-vpn-conf&gt;&lt;single-sign-on-credential /&gt;&lt;/f5-vpn-conf&gt;**<br /><br /> 사용자 지정 XML 명령을 작성하는 방법에 대한 자세한 내용은 각 제조업체의 VPN 설명서를 참조하세요.|- Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN|  

####   <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Intune에서 Configuration Manager를 사용할 때 사용할 수 있는 Windows 10 VPN 기능  


> [!NOTE]  
> Windows 10 VPN 기능을 사용하는 VPN 프로필의 이름은 유니코드일 수 없고 특수 문자를 포함할 수 없습니다.


|옵션|추가 정보|연결 유형|  
|------------|----------------------|---------------------|  
|**회사 Wi-Fi 네트워크에 연결된 경우 VPN 무시**|장치가 회사 Wi-Fi 네트워크에 연결된 경우 VPN 연결을 사용하지 않도록 지정합니다. 장치가 회사 네트워크에 연결되어 있는지 확인하는 데 사용되는 신뢰할 수 있는 네트워크 이름을 입력합니다.|모두|  
|**네트워크 트래픽 규칙**|VPN 연결에 대해 사용할 프로토콜, 로컬/원격 포트와 주소 범위를 설정합니다.<br /><br /> **참고:** 네트워크 트래픽 규칙을 만들지 않으면 모든 프로토콜, 포트 및 주소 범위를 사용할 수 있습니다. 규칙을 만들고 나면 해당 규칙이나 추가 규칙에서 지정하는 프로토콜, 포트 및 주소 범위만 VPN 연결에 사용됩니다.|모두|  
|**경로**|VPN 연결을 사용할 경로입니다. 경로가 60개를 초과하면 정책이 실패할 수 있습니다. |모두|  
|**DNS 서버**|VPN 연결이 설정된 후 해당 연결에서 사용되는 DNS 서버입니다.|모두|  
|**자동으로 VPN에 연결하는 앱**|자동으로 VPN 연결을 사용하는 앱을 추가하거나 앱의 목록을 가져올 수 있습니다. 앱의 유형에 따라 앱 식별자가 결정됩니다. 데스크톱 앱의 경우 앱의 파일 경로를 제공합니다. 유니버설 앱의 경우 PFN(패키지 패밀리 이름)을 제공합니다. 앱의 PFN을 찾는 방법은 [Find a package family name for per-app VPN](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md)(앱별 VPN에 대한 패키지 패밀리 이름 찾기)을 참조하세요. |모두|

> [!IMPORTANT]
> 앱별 VPN의 구성에서 사용하기 위해 컴파일하는 관련 앱의 모든 목록을 보호하는 것이 좋습니다. 권한이 없는 사용자가 목록을 수정하고 해당 목록을 앱별 VPN 앱 목록으로 가져오는 경우 액세스 권한이 부여되면 안 되는 앱에 VPN 액세스 권한을 잠재적으로 부여하게 됩니다. 앱 목록을 보호할 수 있는 한 가지 방법은 ACL(액세스 제어 목록)을 사용하는 것입니다.


### <a name="configure-the-authentication-method-for-the-vpn-profile"></a>VPN 프로필에 대한 인증 방법 구성  

1.  마법사의 **인증 방법** 페이지에서 다음 정보를 지정합니다.  

    -   **인증 방법:** 드롭다운 목록에서 VPN 연결에 사용할 인증 방법을 선택합니다. 이전에 선택한 연결 형식에 따라 드롭다운 목록의 항목이 다를 수도 있습니다. 사용할 수 있는 인증 방법과 지원되는 연결 형식이 다음 표에 정리되어 있습니다.  

        |인증 방법|지원되는 연결 형식|  
        |---------------------------|--------------------------------|  
        |**인증서**<br /><br /> **참고:** 클라이언트 인증서가 네트워크 정책 서버와 같은 RADIUS 서버에 인증하는 데 사용되는 경우 인증서의 주체 대체 이름을 사용자 계정 이름으로 설정해야 합니다.|- <br />                            Cisco AnyConnect<br /><br /> - Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN|  
        |**사용자 이름 및 암호**|- <br />                            Pulse Secure<br /><br /> - F5 Edge Client<br /><br /> - Dell SonicWALL Mobile Connect<br /><br /> - 검사점 모바일 VPN|  
        |**Microsoft EAP-TTLS**|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - PPTP<br /><br /> - IKEv2<br /><br /> - L2TP|  
        |**Microsoft 보호된 EAP(PEAP)**|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
        |**Microsoft 보안 암호(EAP-MSCHAP v2)**|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
        |**스마트 카드 또는 기타 인증서**|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
        |**MSCHAP v2**|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - IKEv2<br /><br /> - PPTP<br /><br /> - L2TP|  
        |**RSA SecurID** (iOS에만 해당)|- Microsoft SSL(SSTP)<br /><br /> - Microsoft 자동<br /><br /> - PPTP<br /><br /> - L2TP|  
        |**컴퓨터 인증서 사용**|IKEv2|  

         선택하는 옵션에 따라 다음과 같은 추가 정보를 지정하라는 메시지가 표시될 수 있습니다.  

        -   **로그온 시 사용자 자격 증명 기억**: 연결을 설정할 때마다 사용자가 자격 증명을 입력하지 않아도 되도록 사용자 자격 증명을 저장하려면 이 옵션을 선택합니다.  

        -   **클라이언트 인증을 위해 클라이언트 인증서 선택** - VPN 연결을 인증하는 데 사용할 이전에 만든 클라이언트 SCEP 인증서를 선택합니다. System Center Configuration Manager에서 인증서 프로필을 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

            > [!NOTE]  
            >  iOS 장치의 경우 선택하는 SCEP 프로필이 VPN 프로필에 포함됩니다. 다른 플랫폼의 경우에는 인증서가 없거나 호환되지 않는 경우 VPN 프로필이 설치되지 않도록 적용 가능성 규칙이 추가됩니다.  
            >   
            >  배포되지 않았거나 호환되지 않는 SCEP 인증서를 지정하면 VPN 프로필이 장치에 설치되지 않습니다.
            >  
            >  iOS를 실행하는 장치는 연결 형식이 PPTP인 경우 인증 방법으로 RSA SecurID 및 MSCHAP v2만 지원합니다. 오류 보고를 방지하려면 iOS를 실행하는 장치에 별도의 PPTP VPN 프로필을 배포하세요.  

               - **조건부 액세스** 및 **엔터프라이즈 데이터 보호 주 도메인** 설정은 Intune 없이 Configuration Manager를 사용하는 경우에만 지원되며 **고급**을 선택하여 액세스할 수 있습니다.
        
        ![VPN에 대한 조건부 액세스 구성](../media/vpn-conditional-access.png)

        -   일부 인증 방법의 경우 **구성**을 클릭하여 Windows 속성 대화 상자를 열고 인증 방법의 속성을 구성할 수 있습니다(System Center Configuration Manager 콘솔을 실행 중인 Windows 버전에서 해당 인증 방법을 지원하는 경우).  

### <a name="configure-proxy-settings-for-the-vpn-profile"></a>VPN 프로필에 대한 프록시 설정 구성  

1.  VPN 연결에 프록시 서버가 사용되는 경우 **VPN 프로필 만들기 마법사** 의 **프록시 설정**페이지에서 **이 VPN 프로필에 대한 프록시 설정 구성** 확인란을 선택합니다.  

2.  프록시 서버에 대한 세부 정보와 설정을 지정합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.  

> [!NOTE]  
>  Windows 8.1 컴퓨터에서 VPN 프로필은 해당 컴퓨터를 사용하여 VPN에 연결할 때까지 프록시 정보를 표시하지 않습니다.  


### <a name="configure-further-dns-settings-if-required"></a>필요한 경우 추가 DNS 설정 구성  
 마법사의 **자동 VPN 연결 구성** 페이지에서 다음 설정을 구성할 수 있습니다.  

-   **주문형 VPN 사용** – Windows Phone 8.1 장치에 대해 마법사의 이 페이지에서 추가 DNS 설정을 구성하려는 경우 이 옵션을 선택합니다.

> [!Note]  
> 이 설정은 Windows Phone 8.1 장치에만 적용되며 Windows Phone 8.1 장치에 배포하려는 VPN 프로필에만 활성화해야 합니다.


-   DNS 접미사 목록(Windows Phone 8.1 장치에만 해당) - VPN 연결을 설정할 도메인을 구성합니다. 지정하는 각 도메인에 대해 DNS 접미사, DNS 서버 주소 및 다음 주문형 작업 중 하나를 추가합니다.  

    -   **설정하지 않음** – VPN 연결을 열지 않습니다.  

    -   **필요한 경우 설정** – 장치를 리소스에 연결해야 하는 경우에만 VPN 연결을 엽니다.  

    -   **항상 설정** – VPN 연결을 항상 엽니다.  

-   **병합** – 구성한 DNS 접미사를 **신뢰할 수 있는 네트워크 목록**에 복사합니다.  

-   **신뢰할 수 있는 네트워크 목록** (Windows Phone 8.1 장치에만 해당) - DNS 접미사를 한 줄에 하나씩 지정합니다. 장치가 신뢰할 수 있는 네트워크에 있는 경우 VPN 연결은 열리지 않습니다.  

-   **접미사 검색 목록** (Windows Phone 8.1 장치에만 해당) - DNS 접미사를 한 줄에 하나씩 지정합니다. 지정하는 각 DNS 접미사는 짧은 이름을 사용하여 웹 사이트에 연결할 때 검색됩니다.  

     예를 들어, DNS 접미사 **domain1.contoso.com** 및 **domain2.contoso.com** 을 지정한 다음 URL **http://mywebsite**를 방문합니다. 다음 주소가 검색됩니다.  

    -   **http://mywebsite.domain1.contoso.com**  

    -   **http://mywebsite.domain2.contoso.com**  

> [!NOTE]  
>  Windows Phone 8.1 장치에만 해당하는 정보  
>   
>  VPN 연결이 전체 터널링을 사용 중인 상태에서 **VPN 연결을 통해 모든 네트워크 트래픽 보내기** 옵션을 선택하는 경우 장치에서 프로비전되는 첫 번째 프로필에 대해 VPN 연결이 자동으로 열립니다. 다른 프로필이 연결을 자동으로 열도록 하려면 장치에서 해당 프로필을 기본 프로필로 지정해야 합니다.  
>   
>  VPN 연결이 분할 터널링을 사용 중인 상태에서 **VPN 연결을 통해 모든 네트워크 트래픽 보내기** 옵션을 선택하지 않는 경우 경로 또는 연결별 DNS 접미사를 구성하면 VPN 연결을 자동으로 열 수 있습니다.  


### <a name="configure-supported-platforms-for-the-vpn-profile"></a>VPN 프로필에 지원되는 플랫폼 구성  
 지원되는 플랫폼은 VPN 프로필을 설치할 운영 체제입니다.  

**VPN 프로필 만들기 마법사** 의 **지원되는 플랫폼**페이지에서 VPN 프로필을 설치할 운영 체제를 선택하거나, 사용 가능한 모든 운영 체제에 VPN 프로필을 설치하려면 **모두 선택** 을 클릭합니다.  

### <a name="complete-the-wizard"></a>마법사 완료  
 마법사의 **요약** 페이지에서 수행할 작업을 검토한 후 **완료**를 선택합니다. 새로운 VPN 프로필이 **자산 및 호환성** 작업 영역의 **VPN 프로필** 노드에 표시됩니다.  

### <a name="next-steps"></a>다음 단계

- 타사 VPN 연결의 경우 VPN 프로필을 배포하기 전에 VPN 앱을 배포합니다. 앱을 배포하지 않고 VPN에 연결하려고 하면 앱을 배포하라는 메시지가 표시됩니다. 앱을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 배포](../../apps/deploy-use/deploy-applications)를 참조하세요.

- [System Center Configuration Manager에서 프로필을 배포하는 방법](deploy-wifi-vpn-email-cert-profiles.md)에 설명된 대로 VPN 프로필을 배포합니다.  



<!--HONumber=Nov16_HO1-->


