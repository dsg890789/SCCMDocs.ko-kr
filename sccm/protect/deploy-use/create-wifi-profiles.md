---
title: "Wi-Fi 프로필을 만드는 방법 | Microsoft 문서"
description: "System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 12/11/2016
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
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f1ae976899de1fd3efcbde0c7268f071a5d0218b
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017


---
# <a name="create-wi-fi-profiles"></a>Wi-Fi 프로필 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포할 수 있습니다. 이러한 설정을 배포하면 사용자가 더 쉽게 Wi-Fi에 연결할 수 있습니다.  

 모든 iOS 장치가 특정 Wi-Fi 네트워크에 연결할 수 있도록 설정하려는 경우를 예로 들어 보겠습니다. 이 경우 무선 네트워크에 연결하는 데 필요한 설정이 포함된 Wi-Fi 프로필을 만듭니다. 그런 다음 계층에서 iOS 장치를 소유한 모든 사용자에게 프로필을 배포합니다. iOS 장치의 사용자는 무선 네트워크 목록에서 회사 네트워크를 볼 수 있으며 이 네트워크에 쉽게 연결할 수 있습니다.  

 Wi-Fi 프로필로 다음 장치 유형을 구성할 수 있습니다.  

-   Windows 8.1 32비트를 실행하는 장치  

-   Windows 8.1 64비트를 실행하는 장치  

-   Windows RT 8.1을 실행하는 장치  

-   Windows 10 Desktop 또는 Mobile을 실행하는 장치  

[모바일 장치에 대한 Wi-Fi 프로필 만들기](../../mdm/deploy-use/create-wifi-profiles.md)에서는 Configuration Manager의 Wi-Fi 프로필을 사용하여 모바일 장치 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다.

> [!IMPORTANT]  
>  Android, iOS, Windows Phone 및 등록된 Windows 8.1 이상 장치에 프로필을 배포하려면 이러한 장치를 Microsoft Intune에 등록해야 합니다. 장치를 등록하는 방법은 [Intune에서 관리할 장치 등록](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)을 참조하세요.  

 Wi-Fi 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 여기에는 Configuration Manager 인증서 프로필을 사용하여 푸시했던 서버 유효성 검사 및 클라이언트 인증용 인증서가 포함됩니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

## <a name="create-a-wi-fi-profile"></a>Wi-Fi 프로필 만들기  

1.  Configuration Manager 콘솔에서 **자산 및 호환성** > **준수 설정** >  **회사 리소스 액세스** > **Wi-Fi 프로필**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **Wi-Fi 프로필 만들기**를 선택합니다.  

1.  **일반** 페이지에서 Wi-Fi 프로필의 고유 이름 및 설명을 입력합니다.  다른 Wi-Fi 프로필의 설정을 사용하려면 **파일에서 기존 Wi-Fi 프로필 항목 가져오기**를 선택합니다.  

    > [!IMPORTANT]  
    >  가져오는 Wi-Fi 프로필이 Wi-Fi 프로필에 유효한 XML을 포함하는지 확인합니다. Configuration Manager에서는 파일을 가져올 때 프로필 유효성을 검사하지 않습니다.  

3.  **보고할 비호환성 심각도**에서 클라이언트 장치에서 Wi-Fi 프로필이 비호환 상태로 확인된 경우(예: 프로필 설치가 실패한 경우) 보고되는 심각도를 지정합니다. 사용할 수 있는 심각도 수준은 다음과 같습니다.  

    -   **없음** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 오류 심각도를 보고하지 않습니다.  

    -   **정보** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **정보** 오류 심각도를 보고합니다.  

    -   **경고** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **경고** 오류 심각도를 보고합니다.  

    -   **위험** 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다.  

    -   **위험(이벤트 포함)** - 이 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다. 또한 이 심각도 수준은 응용 프로그램 이벤트 로그에 Windows 이벤트로 기록됩니다.  

1.  **Wi-Fi 프로필** 페이지에서 장치에서 네트워크 이름으로 표시할 이름을 입력합니다.  

    > [!IMPORTANT]  
    >  Configuration Manager에서는 네트워크 이름에 아포스트로피(**â€˜**) 또는 쉼표(**,**) 문자를 사용할 수 없습니다.  

2.  대/소문자를 구분하는 **SSID**를 지정합니다.
3.  기타 적절한 연결 옵션을 선택합니다.   예를 들어 SSID가 숨겨질 가능성이 있는 경우 **네트워크에서 이름(SSID)을 브로드캐스팅하지 않는 경우 연결**을 선택합니다.  

4.  **보안 구성** 페이지에서 무선 네트워크에 사용되는 보안 프로토콜을 선택하거나, 네트워크에 보안이 적용되지 않는 경우 **인증 안 함(개방형)**을 선택합니다.
    > [!IMPORTANT]  
    >  온\-프레미스 모바일 장치 관리에 대한 Wi-Fi 프로필을 만드는 경우 현재 분기의 Configuration Manager는 다음 Wi-Fi 보안 구성만 지원합니다.  
    >   
    >  보안 유형: **WPA2 엔터프라이즈** 또는 **WPA2 개인**  
    > 암호화 유형: **AES** 또는 **TKIP**  
    > EAP 유형: **스마트 카드 또는 기타 인증서** 또는 **PEAP**  

    > Android 장치의 경우 **WPA-개인**, **WPA2-개인** 및 **WEP** 보안 유형은 지원되지 않습니다.  

2.  무선 네트워크에 사용되는 암호화 방법을 선택합니다.  

3.  무선 네트워크를 인증하는 데 사용되는 EAP 방식을 선택합니다.  

     Windows Phone 장치에만 해당: **LEAP** 및 **EAP FAST** EAP 방식은 지원되지 않습니다.  

4.  **구성** 을 클릭하여 선택한 EAP 방식의 속성을 지정할 수 있습니다. 선택한 일부 EAP 방식에 대해서는 이 옵션을 사용하지 못할 수 있습니다.  

    > [!IMPORTANT]  
    >  **구성**을 클릭할 때 열리는 대화 상자는 Windows 대화 상자입니다. 이런 이유로, Configuration Manager 콘솔을 실행하는 컴퓨터의 운영 체제가 선택한 EAP 방식을 구성하는 작업을 지원하는지 확인해야 합니다.  
    >   
    >  iOS 장치의 경우 인증에 EAP 이외의 방법을 선택했다면 선택한 방법에 관계없이 MS-CHAT v2가 연결에 사용됩니다.  

5.  사용자가 로그온할 때마다 자격 증명을 입력하지 않아도 되도록 사용자 자격 증명을 저장하려는 경우 **로그온할 때마다 사용자 자격 증명 기억**을 선택합니다.  

6. **iOS 장치에만 해당:**  
 Wi-Fi 연결에 필요한 인증서 정보를 구성합니다. 클라이언트 인증서를 비롯하여 신뢰할 수 있는 서버 인증서 이름 또는 루트 인증서를 다음과 같이 구성해야 합니다.  

    -   **신뢰할 수 있는 서버 인증서 이름**: 장치와 연결되는 서버가 서버 인증 인증서를 사용하여 서버를 식별하고 통신 채널을 보호하는 경우 해당 인증서의 주체 이름 또는 주체 대체 이름에 있는 이름을 하나 이상 입력합니다. 이름은 일반적으로 서버의 정규화된 도메인 이름입니다. 예를 들어 서버 인증서의 인증서 주체 일반 이름이 srv1.contoso.com인 경우 **srv1.contoso.com**을 입력합니다. 서버 인증서의 주체 대체 이름에 여러 이름이 지정된 경우 각 이름을 세미콜론으로 구분하여 입력합니다.  

    > [!TIP]  
    >  EAP에 대해 선택한 클라이언트 인증서나 iOS 장치에 대해 선택한 클라이언트 인증이 네트워크 정책 서버와 같은 RADIUS(Remote Authentication Dial-In User Service) 서버에 인증하는 데 사용되는 경우 주체 대체 이름을 사용자 계정 이름으로 설정해야 합니다.  

    -   **서버 유효성 검사에 사용할 루트 인증서 선택**: 장치와 연결되는 서버가 장치에서 신뢰할 수 없는 서버 인증 인증서를 사용하는 경우 장치에서 인증서 신뢰 체인을 만들 수 있도록 서버 인증서에 대한 루트 인증서가 포함된 인증서 프로필을 선택합니다.  

    -   **클라이언트 인증을 위해 클라이언트 인증서 선택**: 연결된 장치를 인증하기 위해 서버 또는 네트워크 장치에 클라이언트 인증서가 필요한 경우 클라이언트 인증 인증서가 포함된 인증서 프로필을 선택합니다.  

    > [!NOTE]  
    >  루트 인증서 및 클라이언트 인증서를 선택하려면 먼저 해당 인증서를 인증서 프로필로 구성하고 배포해야 합니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

7.  **고급 설정** 페이지에서 인증 모드, Single Sign-On, FIPS(Federal Information Processing Standard) 준수 등 Wi-Fi 프로필의 고급 설정을 지정합니다. 이러한 옵션에 대한 자세한 내용은 Windows 설명서를 참조하세요. 고급 설정은 마법사의 **보안 구성** 페이지에서 선택한 옵션에 따라 달라지거나 사용하지 못할 수 있습니다.  

1.  무선 네트워크에 프록시 서버가 사용되는 경우 **프록시 설정** 페이지에서 **이 Wi-Fi 프로필의 프록시 설정 구성** 확인란을 선택하고 구성 정보를 입력합니다.  

2. **지원되는 플랫폼** 페이지에서 Wi-Fi 프로필을 설치하려는 운영 체제를 선택합니다. 또는 **모두 선택** 을 클릭하여 사용 가능한 모든 운영 체제에 Wi-Fi 프로필을 설치합니다.  

### <a name="next-steps"></a>다음 단계
 Wi-Fi 프로필을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Wi-Fi 프로필을 배포하는 방법](deploy-wifi-vpn-email-cert-profiles.md)을 참조하세요.  

