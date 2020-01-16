---
title: PFX 인증서 프로필 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 PFX 파일을 사용 하 여 암호화 된 데이터 교환을 지 원하는 사용자 관련 인증서를 생성 하는 방법에 대해 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: d240a836-c49b-49ab-a920-784c062d6748
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ba54eec13e86b1a21cad2b505484d7b32dfcaaed
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76035273"
---
# <a name="create-pfx-certificate-profiles-using-a-certificate-authority"></a>인증 기관을 사용하여 PFX 인증서 프로필 만들기

*적용 대상: Configuration Manager (현재 분기)*

자격 증명에 인증 기관을 사용 하는 인증서 프로필을 만드는 방법에 대해 알아봅니다. 이 문서에서는 PFX (개인 정보 교환) 인증서 프로필에 대 한 특정 정보를 강조 표시 합니다. 이러한 프로필을 만들고 구성 하는 방법에 대 한 자세한 내용은 [인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)을 참조 하세요.

Configuration Manager를 사용 하면 인증 기관에서 발급 한 자격 증명을 사용 하 여 PFX 인증서 프로필을 만들 수 있습니다. Microsoft 또는 Entrust를 인증 기관으로 선택할 수 있습니다. 사용자 장치에 배포 하는 경우 PFX 파일은 암호화 된 데이터 교환을 지원 하기 위한 사용자별 인증서를 생성 합니다.

기존 인증서 파일에서 인증서 자격 증명을 가져오려면 [PFX 인증서 프로필 가져오기](/configmgr/mdm/deploy-use/import-pfx-certificate-profiles)를 참조 하세요.

## <a name="prerequisites"></a>전제 조건

인증서 프로필 만들기를 시작 하기 전에 필요한 필수 구성 요소가 준비 되어 있는지 확인 합니다. 자세한 내용은 [인증서 프로필에 대 한 필수 조건](/configmgr/protect/plan-design/prerequisites-for-certificate-profiles)을 참조 하세요. 예를 들어 PFX 인증서 프로필의 경우 [인증서 등록 지점](/configmgr/protect/deploy-use/certificate-infrastructure#step-2---install-and-configure-the-certificate-registration-point) 사이트 시스템 역할이 필요 합니다.

## <a name="create-a-profile"></a>프로필 만들기  

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **준수 설정**, **회사 리소스 액세스**를 차례로 확장 한 다음 **인증서 프로필**을 선택 합니다.

1. 리본의 **홈** 탭에 있는 **만들기** 그룹에서 **인증서 프로필 만들기**를 선택합니다.

1. **인증서 프로필 만들기 마법사**의 **일반** 페이지에서 다음 정보를 지정 합니다.  

    - **이름**: 인증서 프로필의 고유한 이름을 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    - **설명**: Configuration Manager 콘솔에서 식별 하는 데 도움이 되는 인증서 프로필의 개요를 제공 하는 설명을 제공 합니다. 최대 256자까지 사용할 수 있습니다.  

1. **개인 정보 교환-PKCS #12 (PFX) 설정-만들기**를 선택 합니다. 이 옵션은 연결 된 온-프레미스 CA (인증 기관)에서 사용자를 대신 하 여 인증서를 요청 합니다. 인증 기관 ( **Microsoft** 또는 **Entrust Datacard**)을 선택 합니다.

    > [!NOTE]
    > **가져오기** 옵션은 인증서 프로필을 만들기 위해 기존 인증서에서 정보를 가져옵니다. 자세한 내용은 [PFX 인증서 프로필 가져오기](/configmgr/mdm/deploy-use/import-pfx-certificate-profiles)를 참조 하세요.

1. **지원 되는 플랫폼** 페이지에서이 인증서 프로필이 지 원하는 OS 버전을 선택 합니다. Configuration Manager 버전의 지원 되는 OS 버전에 대 한 자세한 내용은 [클라이언트 및 장치에 대해 지원 되는 os 버전](/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)을 참조 하세요.

1. **인증 기관** 페이지에서 인증서 등록 지점 (CRP)을 선택 하 여 PFX 인증서를 처리 합니다.

    1. **기본 사이트**: CA의 CRP 역할이 포함 된 서버를 선택 합니다.
    1. **인증 기관**: 관련 CA를 선택 합니다.

    자세한 내용은 [인증서 인프라](/configmgr/protect/deploy-use/certificate-infrastructure)를 참조하세요.

**PFX 인증서** 페이지의 설정은 **일반** 페이지의 선택 된 CA에 따라 달라 집니다.

- [Microsoft CA](#bkmk_microsoft)
- [Entrust Datacard CA](#bkmk_entrust)

### <a name="bkmk_microsoft"></a>Microsoft CA에 대 한 **PFX 인증서** 설정 구성

1. **인증서 템플릿 이름**에서 인증서 템플릿을 선택 합니다.

1. S/MIME 서명 또는 암호화에 대 한 인증서 프로필을 사용 하려면 **인증서 사용**을 사용 하도록 설정 합니다.

    이 옵션을 사용 하도록 설정 하면 대상 사용자와 연결 된 모든 PFX 인증서가 모든 장치에 전달 됩니다. 이 옵션을 사용 하지 않는 경우 각 장치는 고유한 인증서를 수신 합니다.  

1. **주체 이름 형식**을 **일반 이름** 또는 **정식 고유 이름**으로 설정합니다. 사용할 항목을 잘 모르겠으면 CA 관리자에 게 문의 하세요.

1. **주체 대체 이름**에 대해 **전자 메일 주소** 및 **UPN (사용자 계정 이름)** 을 CA에 적합 하 게 사용 하도록 설정 합니다.

1. **갱신 임계값**: 만료 전 남은 시간 비율에 따라 인증서가 자동으로 갱신 되는 시기를 결정 합니다.

1. **인증서 유효 기간**을 인증서의 수명으로 설정합니다.

1. 인증서 등록 지점에서 Active Directory 자격 증명을 지정 하는 경우 **Active Directory 게시**를 사용 하도록 설정 합니다.

1. 하나 이상의 Windows 10 지원 플랫폼을 선택한 경우:

    1. **Windows 인증서 저장소** 를 **사용자**로 설정 합니다. ( **로컬 컴퓨터** 옵션은 인증서를 배포 하지 않고 인증서를 선택 하지 않습니다.)

    1. 다음 **KSP (키 저장소 공급자)** 중 하나를 선택 합니다.

        - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
        - **신뢰할 수 있는 플랫폼 모듈 (TPM)에 설치, 그렇지 않으면 실패**
        - **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패**
        - **소프트웨어 키 스토리지 공급자에 설치**

1. 마법사 완료

### <a name="bkmk_entrust"></a>Entrust Datacard CA에 대 한 **PFX 인증서** 설정 구성

1. **디지털 ID 구성**의 경우 구성 프로필을 선택 합니다. Entrust 관리자가 디지털 ID 구성 옵션을 만듭니다.

1. S/MIME 서명 또는 암호화에 대 한 인증서 프로필을 사용 하려면 **인증서 사용**을 사용 하도록 설정 합니다.

    이 옵션을 사용 하도록 설정 하면 대상 사용자와 연결 된 모든 PFX 인증서가 모든 장치에 전달 됩니다. 이 옵션을 사용 하지 않는 경우 각 장치는 고유한 인증서를 수신 합니다.  

1. Entrust **Subject name 형식** 토큰을 Configuration Manager 필드에 매핑하려면 **서식**을 선택 합니다.

    **인증서 이름 서식** 대화 상자에는 Entrust 디지털 ID 구성 변수가 표시됩니다. 각 Entrust 변수에 대해 적절 한 Configuration Manager 필드를 선택 합니다.

1. Entrust **주체 대체 이름** 토큰을 지원 되는 LDAP 변수에 매핑하려면 **형식**을 선택 합니다.

    **인증서 이름 서식** 대화 상자에는 Entrust 디지털 ID 구성 변수가 표시됩니다. 각 Entrust 변수에 대해 적절 한 LDAP 변수를 선택 합니다.

1. **갱신 임계값**: 만료 전 남은 시간 비율에 따라 인증서가 자동으로 갱신 되는 시기를 결정 합니다.

1. **인증서 유효 기간**을 인증서의 수명으로 설정합니다.

1. 인증서 등록 지점에서 Active Directory 자격 증명을 지정 하는 경우 **Active Directory 게시**를 사용 하도록 설정 합니다.

1. 하나 이상의 Windows 10 지원 플랫폼을 선택한 경우:

    1. **Windows 인증서 저장소** 를 **사용자**로 설정 합니다. ( **로컬 컴퓨터** 옵션은 인증서를 배포 하지 않고 인증서를 선택 하지 않습니다.)

    1. 다음 **KSP (키 저장소 공급자)** 중 하나를 선택 합니다.

        - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
        - **신뢰할 수 있는 플랫폼 모듈 (TPM)에 설치, 그렇지 않으면 실패**
        - **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패**
        - **소프트웨어 키 스토리지 공급자에 설치**

1. 마법사 완료

## <a name="deploy-the-profile"></a>프로필 배포

인증서 프로필을 만든 후에는 **인증서 프로필** 노드에서 사용할 수 있습니다. 배포 하는 방법에 대 한 자세한 내용은 [리소스 액세스 프로필 배포](/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)를 참조 하세요.

## <a name="see-also"></a>참고 항목

[새 인증서 프로필 만들기](/configmgr/protect/deploy-use/create-certificate-profiles)

[PFX 인증서 프로필 가져오다](/configmgr/mdm/deploy-use/import-pfx-certificate-profiles)

[Wi-Fi, VPN, 메일 및 인증서 프로필 배포](/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)
