---
title: 인증 기관을 사용하여 PFX 인증서 프로필 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 PFX 파일을 사용하여 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성하는 방법을 알아봅니다.
ms.date: 11/01/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: d240a836-c49b-49ab-a920-784c062d6748
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a186e0b2c4b355cabcaaeb3b3124b65d3588fbc8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32350965"
---
# <a name="how-to-create-pfx-certificate-profiles-using-a-certificate-authority"></a>인증 기관을 사용하여 PFX 인증서 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

여기에서는 자격 증명을 위해 인증 기관을 사용하는 인증서 프로필을 만드는 방법을 알아봅니다.

[인증서 프로필](../../protect/deploy-use/introduction-to-certificate-profiles.md)에서는 인증서 프로필을 만들고 구성하는 방법에 대한 일반적인 내용을 소개합니다. 이 항목에서는 PFX 인증서와 관련된 인증서 프로필에 대한 몇 가지 특정 정보를 중점적으로 설명합니다.

## <a name="pfx-certificate-profiles"></a>PFX 인증서 프로필
System Center Configuration Manager에서 인증 기관에서 발급한 자격 증명을 사용하여 PFX 인증서 프로필을 만들 수 있습니다.  버전 1706부터 인증 기관으로 Microsoft 또는 Entrust를 선택할 수 있습니다.  사용자 장치에 배포하는 경우 개인 정보 교환(.pfx) 파일은 암호화된 데이터 교환을 지원하기 위해 사용자별 인증서를 생성합니다.

기존 인증서 파일에서 인증서 자격 증명을 가져오려면 [인증서 세부 정보를 가져와 PFX 인증서 프로필을 만드는 방법](../../mdm/deploy-use/import-pfx-certificate-profiles.md)을 참조하세요.

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>PFX(개인 정보 교환) 인증서 프로필 만들기 및 배포  

### <a name="get-started"></a>시작

1.  System Center Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.  
2.  **자산 및 호환성** 작업 영역에서 **호환성 설정** &gt; **회사 리소스 액세스** &gt; **인증서 프로필**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **인증서 프로필 만들기**를 선택합니다.

4.  **인증서 프로필 만들기** 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름**: 인증서 프로필의 고유한 이름을 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    -   **설명**: 인증서 프로필에 대한 개략적인 정보를 제공하는 설명과 System Center Configuration Manager 콘솔에서 해당 프로필을 식별하는 데 도움이 되는 기타 관련 정보를 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    -   **만들려는 인증서 프로필의 유형을 지정합니다.** 에서 **개인 정보 교환 - PKCS #12(PFX) 설정 - 만들기**를 선택한 후 드롭다운 목록에서 인증 기관을 선택합니다.  버전 1706부터 **Microsoft** 또는 **Entrust**를 선택할 수 있습니다.

### <a name="select-supported-platforms"></a>지원되는 플랫폼 선택

지원되는 플랫폼 페이지에는 인증서 프로필에서 지원하는 운영 체제 및 장치가 구분되어 있습니다.  

인증서 프로필이 여러 운영 체제 및 장치를 지원할 수 있으나 특정 운영 체제 또는 장치 조합에 다른 설정이 필요할 수도 있습니다.  이러한 경우 고유한 각 설정 고유 집합에 대해 별도 프로필을 만드는 것이 가장 좋습니다.  

버전 1710부터 다음 옵션을 사용할 수 있습니다.

- Windows 10
    - 모든 Windows 10(64비트)
    - 모든 Windows 10(32비트)
    - 모든 Windows 10(ARM64)
    - 모든 Windows 10 Holographic Enterprise 이상
    - 모든 Windows 10 Holographic K 이상
    - 모든 Windows 10 Team 이상
    - 모든 Windows 10 Mobile 이상
- iPhone
- iPad
- Android
- Android for Work

> [!Note]  
> MacOS/OSX 장치는 현재 지원되지 않습니다.  

다른 옵션을 선택하지 않은 경우 **모두 선택** 확인란을 선택하면 사용 가능한 모든 옵션이 선택됩니다.  하나 이상의 옵션을 선택하는 경우 **모두 선택** 확인란을 선택하면 기존 선택이 취소됩니다. 

1.  인증서 프로필에서 지원하는 하나 이상의 플랫폼을 선택합니다.

1.  계속 진행하려면 **다음**을 선택합니다.  


### <a name="configure-certification-authorities"></a>인증 기관 구성

여기서 PFX 인증서를 처리할 CRP(인증서 등록 지점)를 선택합니다.  

1.  **기본 사이트** 목록에서 CA의 CRP 역할을 포함하는 서버를 선택합니다.
1.  **인증 기관** 목록에서 왼쪽열에 확인 표시를 하여 관련 CA를 선택합니다.
1.  계속 진행할 준비가 되면 **다음**을 선택합니다.

자세한 내용은 [인증서 인프라](../../protect/deploy-use/certificate-infrastructure.md)를 참조하세요.


### <a name="configure-certificate-settings-for-microsoft-ca"></a>Microsoft CA에 대한 인증서 설정 구성

Microsoft를 CA로 사용하는 경우 인증서 설정을 구성하려면

1.  **인증서 템플릿 이름** 드롭다운 목록에서 인증서 템플릿을 선택합니다.

1.  S/MIME 서명 또는 암호화를 위해 인증서 프로필을 사용하려면 **인증서 용도** 확인란을 사용하도록 설정합니다.

    Microsoft를 CA로 사용할 경우 이 옵션을 선택하면 대상 사용자와 연결된 모든 PFX 인증서가 사용자가 등록한 모든 장치로 배달됩니다.  이 확인란을 선택하지 않은 경우 각 장치는 고유한 인증서를 수신합니다.  

1.  **주체 이름 형식**을 **일반 이름** 또는 **정식 고유 이름**으로 설정합니다.  어떤 이름을 사용할지 잘 모르는 경우 인증 기관 관리자에게 문의하세요.

1.  **주체 대체 이름**으로 CA에 따라 **전자 메일 주소** 및 **UPN(사용자 계정 이름)** 을 사용하도록 설정합니다.

1.  **갱신 임계값**은 만료 전에 남은 시간 비율에 따라 인증서가 자동으로 갱신되는 시기를 결정합니다.

1.  **인증서 유효 기간**을 인증서의 수명으로 설정합니다.  이 기간은 숫자(1-100) 및 기간(년, 월 또는 일)을 설정하여 지정합니다.

1.  등록 지점이 Active Directory 자격 증명을 지정하는 경우 **Active Directory 게시**가 사용하도록 설정됩니다.  Active Directory에 인증서 프로필을 게시하는 옵션을 사용하도록 설정합니다.

1.  지원 플랫폼을 지정할 때 하나 이상의 Windows 10 플랫폼을 선택한 경우:

    1.  **Windows 인증서 저장소**를 **사용자**로 설정합니다.  (**로컬 컴퓨터**를 선택하면 인증서가 배포되지 않으므로 선택하지 않아야 합니다.)
    1.  다음 옵션 중 하나에서 **KSP(키 저장소 공급자)** 를 선택합니다.

        - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
        - **TPM(신뢰할 수 있는 플랫폼 모듈)에 설치, 그렇지 않으면 실패** 
        - **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패** 
        - **소프트웨어 키 저장소 공급자에 설치** 

1.  완료되면 **다음** 또는 **요약**을 선택합니다.

### <a name="configure-certificate-settings-for-entrust-ca"></a>Entrust CA에 대한 인증서 설정 구성

Entrust를 CA로 사용하는 경우 인증서 설정을 구성하려면

1.  **디지털 ID 구성** 드롭다운 목록에서 구성 프로필을 선택합니다.  디지털 ID 구성 옵션은 Entrust 관리자가 생성합니다.

1.  이 옵션을 선택하면 **인증서 용도**에서 S/MIME 서명 또는 암호화를 위해 해당 인증서 프로필을 사용합니다.

    Entrust를 CA로 사용할 경우 대상 사용자와 연결된 모든 PFX 인증서가 사용자가 등록한 모든 장치로 배달됩니다.    이 옵션을 선택하지 *않은* 경우 각 장치는 고유한 인증서를 수신합니다.  (다른 CA의 경우에는 동작이 달라집니다. 자세한 내용은 해당 섹션을 참조하세요.)

1.  **형식** 단추를 사용하여 Entrust **주체 이름 형식** 토큰을 ConfigMgr 필드에 매핑합니다.  

    **인증서 이름 서식** 대화 상자에는 Entrust 디지털 ID 구성 변수가 표시됩니다.  각 Entrust 변수에 대해 관련된 드롭다운 목록에서 적절한 LDAP 변수를 선택합니다.

1.  **형식** 단추를 사용하여 Entrust **주체 대체 이름** 토큰을 지원되는 LDAP 변수에 매핑합니다.  

    **인증서 이름 서식** 대화 상자에는 Entrust 디지털 ID 구성 변수가 표시됩니다.  각 Entrust 변수에 대해 관련된 드롭다운 목록에서 적절한 LDAP 변수를 선택합니다.

1.  **갱신 임계값**은 만료 전에 남은 시간 비율에 따라 인증서가 자동으로 갱신되는 시기를 결정합니다.

1.  **인증서 유효 기간**을 인증서의 수명으로 설정합니다.  이 기간은 숫자(1-100) 및 기간(년, 월 또는 일)을 설정하여 지정합니다.

1.  등록 지점이 Active Directory 자격 증명을 지정하는 경우 **Active Directory 게시**가 사용하도록 설정됩니다.  Active Directory에 인증서 프로필을 게시하는 옵션을 사용하도록 설정합니다.

1.  지원 플랫폼을 지정할 때 하나 이상의 Windows 10 플랫폼을 선택한 경우:

    1.  **Windows 인증서 저장소**를 **사용자**로 설정합니다.  (**로컬 컴퓨터**를 선택하면 인증서가 배포되지 않으므로 선택하지 않아야 합니다.)
    1.  다음 옵션 중 하나에서 **KSP(키 저장소 공급자)** 를 선택합니다.

        - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
        - **TPM(신뢰할 수 있는 플랫폼 모듈)에 설치, 그렇지 않으면 실패** 
        - **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패** 
        - **소프트웨어 키 저장소 공급자에 설치** 

1.  완료되면 **다음** 또는 **요약**을 선택합니다.


### <a name="finish-up"></a>끝내기

1.  요약 페이지에서 선택 내용을 검토하고 확인합니다.

1.  준비가 되면 **다음**을 선택하여 프로필을 만듭니다.  

1.  이제 PFX 파일을 포함하는 인증 프로필을 **인증서 프로필** 작업 영역에서 사용할 수 있습니다. 

1.  프로필을 배포하려면

    1. **자산 및 호환성** 작업 영역을 엽니다.
    1. **준수 설정** > **회사 리소스 액세스** > **인증서 프로필**을 선택합니다.
    1. 원하는 인증서 프로필을 마우스 오른쪽 단추로 클릭한 다음 **배포**를 선택합니다. 


## <a name="see-also"></a>참고 항목
[새 인증서 프로필 만들기](../../protect/deploy-use/create-certificate-profiles.md)에서는 인증서 프로필 만들기 마법사를 단계별로 안내합니다.

[인증서 세부 정보를 가져와 PFX 인증서 프로필을 만드는 방법](../../mdm/deploy-use/import-pfx-certificate-profiles.md)

[Wi-Fi, VPN, 메일 및 인증서 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)에서는 인증서 프로필 배포 방법을 설명합니다.