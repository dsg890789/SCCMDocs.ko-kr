---
title: Wi-Fi 프로필을 만드는 방법
titleSuffix: Configuration Manager
description: Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포하는 방법을 알아봅니다.
ms.date: 01/14/2020
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 321b19b2-a093-4b8f-995f-41f74b886eb5
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: e03d49b64a9a2d5b20816e43c17f2be05e41bc6e
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76032651"
---
# <a name="create-wi-fi-profiles"></a>Wi-Fi 프로필 만들기

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 Wi-Fi 프로필을 사용하여 조직의 사용자에게 무선 네트워크 설정을 배포합니다. 이러한 설정을 배포하면 사용자가 더 쉽게 Wi-Fi에 연결할 수 있습니다.  

모든 Windows 노트북을 특정 Wi-Fi 네트워크에 연결할 수 있도록 설정하려는 경우를 예로 들어 보겠습니다. 이 경우 무선 네트워크에 연결하는 데 필요한 설정이 포함된 Wi-Fi 프로필을 만듭니다. 그런 다음 계층에서 Windows 노트북을 소유한 모든 사용자에게 프로필을 배포합니다. 이러한 디바이스의 사용자는 무선 네트워크 목록에서 해당 네트워크를 볼 수 있으며 이 네트워크에 쉽게 연결할 수 있습니다.  

다음 OS 버전에 대한 Wi-Fi 프로필을 구성할 수 있습니다.

- Windows 8.1, 32비트 또는 64비트

- Windows RT 8.1

- Windows 10 또는 Windows 10 Mobile

또한 Configuration Manager를 사용하여 온-프레미스 MDM(모바일 디바이스 관리)을 사용하는 모바일 디바이스에 무선 네트워크 설정을 배포할 수 있습니다. 좀 더 일반적인 정보는 [온-프레미스 MDM 이란?](/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)을 참조하세요.

Wi-Fi 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 이러한 설정에는 Configuration Manager 인증서 프로필을 사용하여 푸시했던 서버 유효성 검사 및 클라이언트 인증용 인증서가 포함됩니다. 인증서 프로필에 대한 자세한 내용은 [인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)을 참조하세요.

## <a name="create-a-wi-fi-profile"></a>Wi-Fi 프로필 만들기

1. Configuration Manager 콘솔의 **자산 및 규정 준수** 작업 영역으로 가서 **규정 준수 설정**, **회사 리소스 액세스**를 차례로 확장하고 **Wi-Fi 프로필** 노드를 선택합니다.

1. **홈** 탭의 **만들기** 그룹에서 **Wi-Fi 프로필 만들기**를 선택합니다.

1. Wi-Fi 프로필 만들기 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.

    - **이름**: 콘솔에서 프로필을 식별하는 고유한 이름을 입력합니다.

    - **설명**: 필요에 따라 Wi-Fi 프로필에 대한 추가 정보를 제공하는 설명을 입력합니다.

    - **파일에서 기존 Wi-Fi 프로필 항목 가져오기**: 다른 Wi-Fi 프로필의 설정을 사용하려면 이 옵션을 선택합니다. 이 옵션을 선택하면 마법사의 나머지 페이지는 **Wi-Fi 프로필 가져오기** 및 **지원되는 플랫폼**의 두 페이지로 간소화됩니다.

        > [!IMPORTANT]
        > 가져오는 Wi-Fi 프로필이 Wi-Fi 프로필에 유효한 XML을 포함하는지 확인합니다. Configuration Manager에서는 파일을 가져올 때 프로필 유효성을 검사하지 않습니다.

    - **보고할 비준수 심각도**: Wi-Fi 프로필을 비호환으로 평가하는 경우 디바이스가 보고하는 다음 심각도 수준 중 하나를 선택합니다. 예를 들어, 프로필 설치가 실패하는 경우 호환되지 않습니다.

        - **없음**: 이 호환성 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 오류 심각도를 보고하지 않습니다.

        - **정보**

        - **경고**

        - **위험**

        - **위험(이벤트 포함)** : 이 규정 준수 규칙에 실패한 컴퓨터가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다. 또한 디바이스가 비호환성 상태를 애플리케이션 이벤트 로그에 Windows 이벤트로 기록합니다.

1. 마법사의 **Wi-Fi 프로필** 페이지에서 다음 정보를 지정합니다.

    - **네트워크 이름**: 네트워크 이름으로 표시되는 디바이스 이름을 제공합니다.

        > [!IMPORTANT]
        > Configuration Manager에서는 네트워크 이름에 아포스트로피(`'`) 또는 쉼표(`,`) 문자를 사용할 수 없습니다.

    - **SSID**: 무선 네트워크의 대/소문자를 구분하는 ID를 지정합니다.

    - **이 네트워크가 범위 내에 있을 때 자동으로 연결**
    - **이 네트워크에 연결된 동안 다른 무선 네트워크 찾기**
    - **네트워크에서 네트워크 이름(SSID)을 브로드캐스트하지 않는 경우에도 연결**

1. **보안 구성** 페이지에서 다음 정보를 지정합니다.

    > [!IMPORTANT]
    > [온-프레미스 MDM](/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)에 대한 Wi-Fi 프로필을 만드는 경우 현재 분기의 Configuration Manager는 다음 Wi-Fi 보안 구성만 지원합니다.  
    >
    > - 보안 유형: **WPA2 Enterprise** 또는 **WPA2 Personal**  
    > - 암호화 유형: **AES** 또는 **TKIP**  
    > - EAP 유형: **스마트 카드 또는 기타 인증서** 또는 **PEAP**  

    - **보안 유형**: 무선 네트워크에 사용되는 보안 프로토콜을 선택하거나, 네트워크에 보안이 적용되지 않는 경우 **인증 안 함(개방형)** 을 선택합니다.

    - **암호화**: 보안 유형이 지원하는 경우 무선 네트워크에 대한 암호화 방법을 설정합니다.

    - **EAP 유형**: 선택한 암호화 방법에 대한 인증 프로토콜을 선택합니다.

        > [!NOTE]
        > Windows Phone 디바이스에만 해당: EAP 방식 **LEAP** 및 **EAP FAST**는 지원되지 않습니다.

        **구성**을 선택하여 선택한 EAP 방식의 속성을 지정할 수 있습니다. 선택한 일부 EAP 방식에 대해서는 이 옵션을 사용할 수 없습니다.

        > [!IMPORTANT]
        > EAP 유형 구성창은 Windows에서 가져온 것입니다. 선택한 EAP 종류를 지원하는 컴퓨터에서 Configuration Manager 콘솔을 실행해야 합니다.

    - **로그온할 때마다 사용자 자격 증명을 기억합니다**: 사용자가 Windows에 로그인할 때마다 무선 네트워크 자격 증명을 입력할 필요가 없도록 사용자 자격 증명을 저장하려면 이 옵션을 선택합니다.

1. 마법사의 **고급 설정** 페이지에서 Wi-Fi 프로필에 대한 추가 설정을 지정합니다. 고급 설정은 마법사의 **보안 구성** 페이지에서 선택한 옵션에 따라 달라지거나 사용하지 못할 수 있습니다. 예를 들면 인증 모드 또는 Single Sign-On 옵션이 있습니다.

1. **프록시 설정** 페이지에서 무선 네트워크가 프록시 서버를 사용하는 경우 **이 Wi-Fi 프로필에 대한 프록시 설정을 구성** 옵션을 선택합니다. 그런 다음 프록시에 대한 구성 정보를 제공합니다.

1. **지원되는 플랫폼** 페이지에서 이 Wi-Fi 프로필을 적용할 수 있는 OS 버전을 선택합니다.

1. 마법사를 완료합니다.

## <a name="next-step"></a>다음 단계

> [!div class="nextstepaction"]
> [Wi-Fi 프로필을 배포하는 방법](/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)
