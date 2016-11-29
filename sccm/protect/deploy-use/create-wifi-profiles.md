---
title: "Wi-Fi 프로필 만들기 | System Center Configuration Manager"
description: "System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 321b19b2-a093-4b8f-995f-41f74b886eb5
caps.latest.revision: 13
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 295ccc2ce7c1dae55c45113cc8ff826e30f7079a


---
# <a name="how-to-create-wi-fi-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Wi-Fi 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포할 수 있습니다. 이러한 설정을 배포하면 사용자가 더 쉽게 Wi-Fi에 연결할 수 있습니다.  

 예를 들어 **Contoso Wi-Fi**라는 새 Wi-Fi 네트워크를 설치했습니다. 이제 이 네트워크에 연결하는 데 필요한 설정을 사용하여 iOS 운영 체제를 실행하는 모든 장치를 프로비전하려고 합니다. **Contoso Wi-Fi** 무선 네트워크에 연결하는 데 필요한 설정이 포함된 Wi-Fi 프로필을 만들 수 있습니다. 그런 다음 계층 구조에서 iOS를 실행하는 장치를 보유한 모든 사용자에게 이 프로필을 배포할 수 있습니다. iOS 장치의 사용자는 무선 네트워크 목록에서 회사 네트워크를 볼 수 있으며 이 네트워크에 쉽게 연결할 수 있습니다.  

 Wi-Fi 프로필로 다음 장치 유형을 구성할 수 있습니다.  

-   Windows 8.1 32비트를 실행하는 장치  

-   Windows 8.1 64비트를 실행하는 장치  

-   Windows RT 8.1을 실행하는 장치  

-   Windows Phone 8.1을 실행하는 장치  

-   Windows 10 Desktop 또는 Mobile을 실행하는 장치  

-   iOS 5, iOS 6, iOS 7 및 iOS 8을 실행하는 IPhone 장치  

-   iOS 5, iOS 6, iOS 7 및 iOS 8을 실행하는 IPad 장치  

-   버전 4를 실행하는 Android 장치  

> [!IMPORTANT]  
>  Android, iOS, Windows Phone 및 등록된 Windows 8.1 장치에 프로필을 배포하려면 이러한 장치를 Microsoft Intune에 등록해야 합니다. 장치를 등록하는 방법은 [Intune에서 관리할 장치 등록](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)을 참조하세요.  

 Wi-Fi 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 여기에는 Configuration Manager 인증서 프로필을 사용하여 프로비전했던 서버 유효성 검사 및 클라이언트 인증용 인증서가 포함됩니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

## <a name="steps-to-create-a-wi-fi-profile"></a>Wi-Fi 프로필을 만드는 단계  
 **Wi-Fi 프로필 만들기 마법사**를 사용하여 Wi-Fi 프로필을 만들려면 다음 필수 단계를 따르세요.  

-   [1단계: Wi-Fi 프로필 만들기 마법사 시작](#BKMK_Step1)  

-   [2단계: Wi-Fi 프로필에 대한 일반 정보 제공](#BKMK_Step2)  

-   [3단계: 무선 네트워크에 대한 정보 제공](#BKMK_Step3)  

-   [4단계: Wi-Fi 프로필에 대한 보안 구성](#BKMK_Step4)  

-   [5단계: Wi-Fi 프로필에 대한 고급 설정 구성](#BKMK_Step5)  

-   [6단계: Wi-Fi 프로필에 대한 프록시 설정 구성](#BKMK_Step6)  

-   [7단계: Wi-Fi 프로필에 지원되는 플랫폼 구성](#BKMK_Step7)  

-   [8단계: 마법사 완료](#BKMK_Step8)  

##  <a name="a-namebkmkstep1a-step-1-start-the-create-wi-fi-profile-wizard"></a><a name="BKMK_Step1"></a> 1단계: Wi-Fi 프로필 만들기 마법사 시작  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 호환성** 작업 영역에서 **호환성 설정**을 확장하고 **회사 리소스 액세스**를 확장한 후 **Wi-Fi 프로필**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **Wi-Fi 프로필 만들기**를 클릭합니다.  

##  <a name="a-namebkmkstep2a-step-2-provide-general-information-about-the-wi-fi-profile"></a><a name="BKMK_Step2"></a> 2단계: Wi-Fi 프로필에 대한 일반 정보 제공  

1.  Wi-Fi 프로필 만들기 마법사의 **일반** 페이지에서 Wi-Fi 프로필의 고유 이름 및 설명을 입력합니다. 최대 256자까지 사용할 수 있습니다.  

2.  다른 Wi-Fi 프로필의 설정을 사용하려면 **파일에서 기존 Wi-Fi 프로필 항목 가져오기**를 선택합니다.  

    > [!IMPORTANT]  
    >  가져오는 Wi-Fi 프로필이 Wi-Fi 프로필에 유효한 XML을 포함하는지 확인합니다. Configuration Manager에서는 파일을 가져올 때 프로필 유효성을 검사하지 않습니다.  

3.  글로벌 조건은  
                            **보고할 비준수 심각도**: 클라이언트 장치에서 Wi-Fi 프로필이 비호환 상태로 확인된 경우(예: 프로필 설치가 실패한 경우) 보고되는 심각도 수준을 지정합니다. 사용할 수 있는 심각도 수준은 다음과 같습니다.  

    -   **없음** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 오류 심각도를 보고하지 않습니다.  

    -   **정보** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **정보** 오류 심각도를 보고합니다.  

    -   **경고** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **경고** 오류 심각도를 보고합니다.  

    -   **위험** 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다.  

    -   **위험(이벤트 포함)** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다. 또한 이 심각도 수준은 응용 프로그램 이벤트 로그에 Windows 이벤트로 기록됩니다.  

##  <a name="a-namebkmkstep3a-step-3-provide-information-about-the-wireless-network"></a><a name="BKMK_Step3"></a> 3단계: 무선 네트워크에 대한 정보 제공  

1.  Wi-Fi 프로필 만들기 마법사의 **Wi-Fi 프로필** 페이지에서 최대 32자까지 사용하여 무선 인터넷 연결에 대해 설명이 포함된 이름을 지정합니다. 이 이름은 장치에서 네트워크 이름으로 표시됩니다.  

    > [!IMPORTANT]  
    >  Configuration Manager에서는 네트워크 이름에 아포스트로피(**â€˜**) 또는 쉼표(**,**) 문자를 사용할 수 없습니다.  

2.  **SSID**에서 장치가 연결할 수 있는 무선 네트워크의 이름(SSID)을 지정합니다. 이름은 32자까지 사용할 수 있습니다. SSID 이름은 대/소문자를 구분하므로 구성된 대로 정확히 입력해야 합니다.  

3.  장치가 범위 내에 있는 무선 네트워크에 자동으로 다시 연결하도록 하려면 **이 네트워크가 범위 내에 있을 때 자동으로 연결**을 선택합니다.  

4.  장치가 이 네트워크에 연결될 때 다른 무선 네트워크를 계속 검색할 수 있게 하려면  
                            **이 네트워크에 연결된 동안 다른 무선 네트워크를 찾습니다.**  

5.  장치가 네트워크 목록에 표시되지 않는 네트워크(숨겨져 있으며 이름을 브로드캐스트하지 않음)에 연결할 수 있게 하려면 **네트워크에서 이름(SSID)을 브로드캐스팅하지 않는 경우 연결**을 선택합니다.  

##  <a name="a-namebkmkstep4a-step-4-configure-security-for-the-wi-fi-profile"></a><a name="BKMK_Step4"></a> 4단계: Wi-Fi 프로필에 대한 보안 구성  

> [!IMPORTANT]  
>  온\-프레미스 모바일 장치 관리에 대한 Wi-Fi 프로필을 만드는 경우 현재 분기의 Configuration Manager는 다음 Wi-Fi 보안 구성만 지원합니다.  
>   
>  보안 유형: **WPA2 엔터프라이즈** 또는 **WPA2 개인**  
> 암호화 유형: **AES** 또는 **TKIP**  
> EAP 유형: **스마트 카드 또는 기타 인증서** 또는 **PEAP**  

1.  Wi-Fi 프로필 만들기 마법사의 **보안 구성** 페이지에서 무선 네트워크에 사용되는 보안 프로토콜을 선택하거나, 네트워크에 보안이 적용되지 않는 경우 **인증 안 함(개방형)** 을 선택합니다.  

     Android 장치에 해당: 보안 유형 **WPA – 개인**, **WPA2 – 개인** 및 **WEP** 는 지원되지 않습니다.  

2.  무선 네트워크에 사용되는 암호화 방법을 선택합니다.  

3.  무선 네트워크를 인증하는 데 사용되는 EAP 방식을 선택합니다.  

     Windows Phone 장치에만 해당: **LEAP** 및 **EAP FAST** EAP 방식은 지원되지 않습니다.  

4.  **구성** 을 클릭하여 선택한 EAP 방식의 속성을 지정할 수 있습니다. 선택한 일부 EAP 방식에 대해서는 이 옵션을 사용하지 못할 수 있습니다.  

    > [!IMPORTANT]  
    >  **구성**을 클릭할 때 열리는 대화 상자는 Windows 대화 상자입니다. 이런 이유로, Configuration Manager 콘솔을 실행하는 컴퓨터의 운영 체제가 선택한 EAP 방식을 구성하는 작업을 지원하는지 확인해야 합니다.  
    >   
    >  iOS 장치의 경우 인증에 EAP 이외의 방법을 선택했다면 선택한 방법에 관계없이 MS-CHAT v2가 연결에 사용됩니다.  

5.  사용자가 로그온할 때마다 자격 증명을 입력하지 않아도 되도록 사용자 자격 증명을 저장하려는 경우 **로그온할 때마다 사용자 자격 증명 기억**을 선택합니다.  

### <a name="for-ios-devices-only"></a>iOS 장치에만 해당:  
 Wi-Fi 연결에 필요한 인증서 정보를 구성합니다. 클라이언트 인증서를 비롯하여 신뢰할 수 있는 서버 인증서 이름 또는 루트 인증서를 다음과 같이 구성해야 합니다.  

-   **신뢰할 수 있는 서버 인증서 이름**: 장치와 연결되는 서버가 서버 인증 인증서를 사용하여 서버를 식별하고 통신 채널을 보호하는 경우 해당 인증서의 주체 이름 또는 주체 대체 이름에 있는 이름을 하나 이상 입력합니다. 이름은 일반적으로 서버의 정규화된 도메인 이름입니다. 예를 들어 서버 인증서의 인증서 주체 일반 이름이 srv1.contoso.com인 경우 **srv1.contoso.com**을 입력합니다. 서버 인증서의 주체 대체 이름에 여러 이름이 지정된 경우 각 이름을 세미콜론으로 구분하여 입력합니다.  

    > [!TIP]  
    >  EAP에 대해 선택한 클라이언트 인증서나 iOS 장치에 대해 선택한 클라이언트 인증이 네트워크 정책 서버와 같은 RADIUS(Remote Authentication Dial-In User Service) 서버에 인증하는 데 사용되는 경우 주체 대체 이름을 사용자 계정 이름으로 설정해야 합니다.  

-   **서버 유효성 검사에 사용할 루트 인증서 선택**: 장치와 연결되는 서버가 장치에서 신뢰할 수 없는 서버 인증 인증서를 사용하는 경우 장치에서 인증서 신뢰 체인을 만들 수 있도록 서버 인증서에 대한 루트 인증서가 포함된 인증서 프로필을 선택합니다.  

-   **클라이언트 인증을 위해 클라이언트 인증서 선택**: 연결된 장치를 인증하기 위해 서버 또는 네트워크 장치에 클라이언트 인증서가 필요한 경우 클라이언트 인증 인증서가 포함된 인증서 프로필을 선택합니다.  

> [!NOTE]  
>  루트 인증서 및 클라이언트 인증서를 선택하려면 먼저 해당 인증서를 인증서 프로필로 구성하고 배포해야 합니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

##  <a name="a-namebkmkstep5a-step-5-configure-advanced-settings-for-the-wi-fi-profile"></a><a name="BKMK_Step5"></a> 5단계: Wi-Fi 프로필에 대한 고급 설정 구성  
 Wi-Fi 프로필 만들기 마법사의 **고급 설정** 페이지에서 인증 모드, Single Sign-On, FIPS(Federal Information Processing Standard) 준수 등 Wi-Fi 프로필의 고급 설정을 지정합니다. 이러한 옵션에 대한 자세한 내용은 Windows 설명서를 참조하세요.  

> [!NOTE]  
>  고급 설정은 마법사의 **보안 구성** 페이지에서 선택한 옵션에 따라 달라지거나 사용하지 못할 수 있습니다.  

##  <a name="a-namebkmkstep6a-step-6-configure-proxy-settings-for-the-wi-fi-profile"></a><a name="BKMK_Step6"></a> 6단계: Wi-Fi 프로필에 대한 프록시 설정 구성  

1.  무선 네트워크에 프록시 서버가 사용되는 경우 Wi-Fi 프로필 만들기 마법사의 **프록시 설정** 페이지에서 **이 Wi-Fi 프로필의 프록시 설정 구성** 확인란을 선택합니다.  

2.  프록시 서버에 대한 세부 정보와 설정을 지정합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.  

##  <a name="a-namebkmkstep7a-step-7-configure-supported-platforms-for-the-wi-fi-profile"></a><a name="BKMK_Step7"></a> 7단계: Wi-Fi 프로필에 지원되는 플랫폼 구성  
 Wi-Fi 프로필 만들기 마법사의 **지원되는 플랫폼** 페이지에서 Wi-Fi 프로필을 설치하려는 운영 체제를 선택합니다. 또는 **모두 선택** 을 클릭하여 사용 가능한 모든 운영 체제에 Wi-Fi 프로필을 설치합니다.  

##  <a name="a-namebkmkstep8a-step-8-complete-the-wizard"></a><a name="BKMK_Step8"></a> 8단계: 마법사 완료  
 마법사의 **요약** 페이지에서 마법사가 수행할 작업을 검토한 후 마법사를 완료합니다. 새로운 Wi-Fi 프로필이 **자산 및 호환성** 작업 영역의 **Wi-Fi 프로필** 노드에 표시됩니다.  

 Wi-Fi 프로필을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Wi-Fi 프로필을 배포하는 방법](deploy-wifi-vpn-email-cert-profiles.md)을 참조하세요.  



<!--HONumber=Nov16_HO1-->


