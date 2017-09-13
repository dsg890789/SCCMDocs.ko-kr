---
title: "System Center Configuration Manager의 VPN 프로필 | Microsoft 문서"
description: "System Center Configuration Manager의 모바일 장치에 대한 VPN 프로필"
ms.custom: na
ms.date: 07/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
caps.latest.revision: "18"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 23ff28189c8010c21ed8b23c35598746a4f09fe7
ms.sourcegitcommit: 13599667ea77c16db1aebe64f8a6748c268f0b45
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2017
---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>System Center Configuration Manager의 모바일 장치에 대한 VPN 프로필

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 VPN 프로필을 사용하여 조직의 모바일 장치 사용자에게 VPN 설정을 배포할 수 있습니다. 이러한 설정을 배포할 때 최종 사용자가 회사 네트워크에 있는 리소스에 연결하는 데 필요한 노력을 최소화할 수 있습니다.  

 예를 들어, 기업 네트워크의 파일 공유에 연결하는 데 필요한 설정을 사용하여 iOS 운영 체제를 실행하는 모든 장치를 설정하려고 합니다. 기업 네트워크에 연결하는 데 필요한 설정이 포함된 VPN 프로필을 만든 다음 이 프로필을 조직 계층에서 iOS를 실행하는 장치를 가진 모든 사용자에게 배포할 수 있습니다. iOS 장치 사용자는 사용 가능한 네트워크의 목록에서 VPN 연결을 확인하고 최소의 노력으로 이 네트워크에 연결할 수 있습니다.  

 VPN 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 예를 들어 System Center Configuration Manager 인증서 프로필을 사용하여 설정했던 서버 유효성 검사 및 클라이언트 인증용 인증서를 지정할 수 있습니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](../../protect/deploy-use/introduction-to-certificate-profiles.md)을 참조하세요.  

 ## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>Configuration Manager 및 Intune을 사용하는 경우의 VPN 프로필

 iOS, Android, Windows Phone 및 Windows 8.1 장치에 프로필을 배포하려면 이러한 장치를 Microsoft Intune에 등록해야 합니다. 다른 플랫폼의 장치를 Intune에 등록할 수도 있습니다. 등록하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 모바일 장치 관리](https://technet.microsoft.com/en-us/library/dn646962.aspx)를 참조하세요. 이 표에서는 각 장치 플랫폼에 대해 지원되는 연결 형식을 보여 줍니다.  

 |연결 유형|iOS 및 macOS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop 및 Mobile|  
 |---------------------|----------------------|-------------|-----------------|----------------|--------------------|-----------------------|-----------------------------------|  
 |Cisco AnyConnect|예|예|아니요|아니요|아니요|아니요|예|
 |Cisco(IPsec)|iOS에만 해당|아니요|아니요|아니요|아니요|아니요|아니요|  
 |Pulse Secure|예|예|예|아니요|예|예|예|  
 |F5 Edge Client|예|예|예|아니요|예|예|예|  
 |Dell SonicWALL Mobile Connect|예|예|예|아니요|예|예|예|  
 |검사점 모바일 VPN|예|예|예|아니요|예|예|예|  
 |Microsoft SSL(SSTP)|아니요|아니요|예|예|예|아니요|아니요|  
 |Microsoft 자동|아니요|아니요|예|예|예|아니요|예|  
 |IKEv2|예(사용자 지정 정책, iOS 9 이상)|아니요|예|예|예|예|예|  
 |PPTP|예|아니요|예|예|예|아니요|예|  
 |L2TP|예|아니요|예|예|예|아니요|예(OMA-URI)|  

## <a name="create-vpn-profiles"></a>VPN 프로필 만들기
[System Center Configuration Manager에서 VPN 프로필을 만드는 방법](../../protect/deploy-use/create-vpn-profiles.md)에서는 VPN 프로필을 만드는 방법에 대한 일반 정보를 제공합니다.

###   <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Intune에서 Configuration Manager를 사용할 때 사용할 수 있는 Windows 10 VPN 기능  


> [!NOTE]  
> Windows 10 VPN 기능을 사용하는 VPN 프로필의 이름은 유니코드일 수 없고 특수 문자를 포함할 수 없습니다.


|옵션|추가 정보|연결 유형|  
    |------------|----------------------|---------------------|  
    |**회사 Wi-Fi 네트워크에 연결된 경우 VPN 무시**|장치가 회사 Wi-Fi 네트워크에 연결된 경우 VPN 연결이 사용되지 않습니다. 장치가 회사 네트워크에 연결되어 있는지 확인하는 데 사용되는 신뢰할 수 있는 네트워크 이름을 입력합니다.|모두|  
    |**네트워크 트래픽 규칙**|VPN 연결에 대해 사용할 프로토콜, 로컬 포트, 원격 포트 및 주소 범위를 설정합니다.<br /><br /> **참고:** 네트워크 트래픽 규칙을 만들지 않으면 모든 프로토콜, 포트 및 주소 범위를 사용할 수 있습니다. 규칙을 만들고 나면 해당 규칙이나 추가 규칙에서 지정하는 프로토콜, 포트 및 주소 범위만 VPN 연결에 사용됩니다.|모두|  
    |**경로**|VPN 연결을 사용할 경로입니다. 경로가 60개를 초과하면 정책이 실패할 수 있습니다. |모두|  
    |**DNS 서버**|VPN 연결이 설정된 후 해당 연결에서 사용되는 DNS 서버입니다.|모두|  
    |**자동으로 VPN에 연결하는 앱**|자동으로 VPN 연결을 사용하는 앱을 추가하거나 앱의 목록을 가져올 수 있습니다. 앱의 유형에 따라 앱 식별자가 결정됩니다. 데스크톱 앱의 경우 앱의 파일 경로를 제공합니다. 유니버설 앱의 경우 PFN(패키지 패밀리 이름)을 제공합니다. 앱의 PFN을 찾는 방법은 [Find a package family name for per-app VPN](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md)(앱별 VPN에 대한 패키지 패밀리 이름 찾기)을 참조하세요. |모두|

> [!IMPORTANT]
> 앱별 VPN의 구성에서 사용하기 위해 컴파일하는 관련 앱의 모든 목록을 보호하는 것이 좋습니다. 권한이 없는 사용자가 목록을 변경하고 해당 목록을 앱별 VPN 앱 목록으로 가져오는 경우 액세스 권한이 부여되면 안 되는 앱에 VPN 액세스 권한을 잠재적으로 부여하게 됩니다. 앱 목록을 보호할 수 있는 한 가지 방법은 ACL(액세스 제어 목록)을 사용하는 것입니다.


1.  마법사의 **인증 방법** 페이지에서 다음을 지정합니다.  

    -   **인증 방법:** VPN 연결에 사용할 인증 방법을 선택합니다. 사용 가능한 방법은 이 표에 표시된 연결 형식에 따라 달라집니다.  

        |인증 방법|지원되는&nbsp;연결&nbsp;형식|  
        |---------------------------|--------------------------------|  
        |**인증서**<br /><br /> **참고:**<ul><li>클라이언트 인증서가 네트워크 정책 서버와 같은 RADIUS 서버를 인증하는 경우 인증서의 주체 대체 이름을 사용자 계정 이름으로 설정해야 합니다.</li><li>Android 배포의 경우 EKU 식별자 및 인증서 발급자 지문 해시 값을 선택합니다.  이렇게 하지 않으면 사용자가 적절한 인증서를 수동으로 선택해야 합니다.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> 검사점 모바일 VPN</li></ul>|  
        |**사용자 이름 및 암호**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> 검사점 모바일 VPN</li></ul>|  
        |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
        |**Microsoft 보호된 EAP(PEAP)**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**Microsoft 보안 암호(EAP-MSCHAP v2)**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**스마트 카드 또는 기타 인증서**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**MSCHAP v2**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**RSA SecurID** (iOS에만 해당)|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>PPTP</li><li>L2TP</li></ul>|  
        |**컴퓨터 인증서 사용**|<ul><li>IKEv2</li></ul>|  

         선택한 옵션에 따라 다음과 같은 추가 정보를 지정하라는 메시지가 표시될 수 있습니다.  

        -   **로그온할 때마다 사용자 자격 증명 기억**: 사용자가 연결할 때마다 자격 증명을 입력할 필요가 없도록 사용자 자격 증명이 기억됩니다.  

        -   **클라이언트 인증을 위해 클라이언트 인증서 선택** - VPN 연결을 인증하는 데 사용할 이전에 만든 클라이언트 [SCEP 인증서](create-pfx-certificate-profiles.md)를 선택합니다.   

            > [!NOTE]  
            >  iOS 장치의 경우 선택하는 SCEP 프로필이 VPN 프로필에 포함됩니다. 다른 플랫폼의 경우에는 인증서가 없거나 호환되지 않는 경우 VPN 프로필이 설치되지 않도록 적용 가능성 규칙이 추가됩니다.  
            >   
            >  배포되지 않았거나 호환되지 않는 SCEP 인증서를 지정하면 VPN 프로필이 장치에 설치되지 않습니다.
            >  
            >  iOS를 실행하는 장치는 연결 형식이 PPTP인 경우 인증 방법으로 RSA SecurID 및 MSCHAP v2만 지원합니다. 오류 보고를 방지하려면 iOS를 실행하는 장치에 별도의 PPTP VPN 프로필을 배포하세요.  

        - **조건부 액세스**
            - 연결 전에 VPN에 연결하는 장치의 조건부 액세스 준수를 테스트하려면 **이 VPN 연결에 조건부 액세스 사용**을 선택합니다. 준수 정책은 [System Center Configuration Manager의 장치 정책 준수 정책](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/device-compliance-policies.md)에서 설명합니다.
            - 장치 준수에 대해 VPN 인증 인증서 이외의 인증서를 선택하려면 **대체 인증서로 SSO(Single Sign-On) 사용**을 선택합니다. 이 옵션을 선택하는 경우 VPN 클라이언트가 찾아야 하는 올바른 인증서의 **EKU**(쉼표로 구분된 목록) 및 **발급자 해시**를 제공합니다.

         - **Windows Information Protection** - 엔터프라이즈에서 관리되는 회사 ID를 제공합니다. 일반적으로 조직의 기본 도메인(예: *contoso.com*)입니다. "|" 문자로 구분하여 조직에서 소유하는 여러 도메인을 지정할 수 있습니다. 예를 들어 *contoso.com|newcontoso.com*입니다.   
            Windows Information Protection에 대한 자세한 내용은 [Microsoft Intune을 사용하여 WIP(Windows Information Protection) 정책 만들기](https://technet.microsoft.com/en-us/itpro/windows/keep-secure/create-wip-policy-using-intune)를 참조하세요.   

         ![VPN에 대한 조건부 액세스 구성](media/vpn-conditional-access.png)

         Configuration Manager를 실행하는 Windows의 버전 _및_ 선택한 권한 부여 방법에서 지원하는 경우 **구성**을 선택하여 Windows 속성 대화 상자를 열고 인증 방법 속성을 구성할 수 있습니다.  **구성**이 사용하지 않도록 설정되어 있으면 다른 수단을 통해 인증 방법 속성을 구성합니다.

2.  VPN 연결에 프록시 서버가 사용되는 경우 **VPN 프로필 만들기 마법사**의 **프록시 설정**페이지에서 **이 VPN 프로필에 대한 프록시 설정 구성** 확인란을 선택합니다. 그런 다음 프록시 서버 정보를 제공합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.  

    > [!NOTE]  
    >  Windows 8.1 컴퓨터에서 VPN 프로필은 해당 컴퓨터를 사용하여 VPN에 연결할 때까지 프록시 정보를 표시하지 않습니다.  


3. 필요한 경우 추가 DNS 설정 구성  
 **자동 VPN 연결 구성** 페이지에서 다음을 구성할 수 있습니다.  

    -   **주문형 VPN 사용** – Windows Phone 8.1 장치에 대해 추가 DNS 설정을 구성하려는 경우 사용합니다. 이 설정은 Windows Phone 8.1 장치에만 적용되며 Windows Phone 8.1 장치에 배포하려는 VPN 프로필에만 사용하도록 설정되어야 합니다.

    -   **DNS 접미사 목록**(Windows Phone 8.1 장치에만 해당): VPN 연결을 설정할 도메인을 구성합니다. 지정하는 각 도메인에 대해 DNS 접미사, DNS 서버 주소 및 다음 주문형 작업 중 하나를 추가합니다.  

        -   **설정하지 않음**: VPN 연결을 열지 않습니다.  

        -   **필요한 경우 설정**: 장치를 리소스에 연결해야 하는 경우에만 VPN 연결을 엽니다.  

        -   **항상 설정**: VPN 연결을 항상 엽니다.  

    -   **병합**: 구성한 DNS 접미사를 **신뢰할 수 있는 네트워크 목록**에 복사합니다.  

    -   **신뢰할 수 있는 네트워크 목록**(Windows Phone 8.1 장치에만 해당): DNS 접미사를 한 줄에 하나씩 지정합니다. 장치가 신뢰할 수 있는 네트워크에 있는 경우 VPN 연결은 열리지 않습니다.  

    -   **접미사 검색 목록**(Windows Phone 8.1 장치에만 해당): DNS 접미사를 한 줄에 하나씩 지정합니다. 각 DNS 접미사는 짧은 이름을 사용하여 웹 사이트에 연결할 때 검색됩니다.  

     예를 들어, DNS 접미사 **domain1.contoso.com** 및 **domain2.contoso.com** 을 지정한 다음 URL **http://mywebsite**로 이동합니다. 다음 주소가 검색됩니다.  

    -   **http://mywebsite.domain1.contoso.com**  

    -   **http://mywebsite.domain2.contoso.com**  

    > [!NOTE]  
    >  Windows Phone 8.1 장치에만 해당하는 정보  
    >   
    >  *VPN 연결을 통해 모든 네트워크 트래픽 보내기* 옵션을 선택*했으며* VPN 연결이 전체 터널링을 사용 중인 경우 첫 번째 장치 프로필을 사용하여 VPN 연결이 자동으로 열립니다. 다른 프로필과의 연결을 열려면 원하는 프로필을 기본값으로 설정합니다.  
    >   
    >  *VPN 연결을 통해 모든 네트워크 트래픽 보내기* 옵션을 선택하지 *않았**으며* VPN 연결이 분할 터널링을 사용 중인 경우 구성된 경로 또는 연결별 DNS 접미사에 대해 VPN 연결이 자동으로 열립니다.  


4. **VPN 프로필 만들기 마법사** 의 **지원되는 플랫폼**페이지에서 VPN 프로필을 설치할 운영 체제를 선택하거나, 사용 가능한 모든 운영 체제에 VPN 프로필을 설치하려면 **모두 선택**을 선택합니다.  

5. 마법사를 마칩니다. 새로운 VPN 프로필이 **자산 및 호환성** 작업 영역의 **VPN 프로필** 노드에 새 VPN 프로필이 표시됩니다.  


**배포:** VPN 프로필 배포 방법에 대한 자세한 내용은 [Wi-Fi, VPN, 메일 및 인증서 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)를 참조하세요.

### <a name="next-steps"></a>다음 단계  
 다음 항목에서는 Configuration Manager의 VPN 프로필을 계획, 설정, 운영 및 유지 관리하는 방법을 설명합니다.  

-   [System Center Configuration Manager에서 VPN 프로필에 대한 필수 조건](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [System Center Configuration Manager에서 VPN 프로필에 대한 보안 및 개인 정보](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
