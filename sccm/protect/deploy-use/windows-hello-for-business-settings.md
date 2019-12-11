---
title: 비즈니스용 Windows Hello 설정
titleSuffix: Configuration Manager
description: Configuration Manager와 비즈니스용 Windows Hello를 통합하는 방법을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2fa638c292755dafbb03262680a240103e082ad9
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74660865"
---
# <a name="windows-hello-for-business-settings-in-configuration-manager"></a>Configuration Manager의 비즈니스용 Windows Hello 설정

*적용 대상: Configuration Manager (현재 분기)*

<!--1245704-->
Configuration Manager는 비즈니스용 Windows Hello와 통합됩니다. (이 기능은 이전에 Microsoft Passport for Work로 알려져 있었습니다.) 비즈니스용 windows Hello는 Windows 10 장치에 대 한 대체 로그인 방법입니다. 이는 Active Directory 또는 Azure AD(Azure Active Directory) 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대체합니다. 비즈니스용 Hello를 통해 암호 대신 *사용자 제스처* 를 사용하여 로그인할 수 있습니다. 사용자 제스처는 PIN, 생체 인식 인증 또는 외부 디바이스(예: 지문 판독기)일 수 있습니다.

> [!Important]  
> 버전 1910부터 Configuration Manager에서 비즈니스용 Windows Hello 설정을 사용 하는 인증서 기반 인증은 지원 되지 않습니다. 자세한 내용은 [사용되지 않는 기능](/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)을 참조하세요. 키 기반 인증은 여전히 유효 합니다.
>
> ADFS RA(Active Directory Federation Services 등록 기관) 배포는 좀 더 간단하며, 더 나은 사용자 환경을 제공하고, 보다 명확한 인증서 등록 환경을 제공합니다. 비즈니스용 Windows Hello에서 인증서 기반 인증에 ADFS RA를 사용 합니다.
>
> 공동 관리 되는 장치의 경우 [ **리소스 액세스 정책** 워크 로드](/configmgr/comanage/workloads#resource-access-policies) 를 Intune으로 이동 하는 것이 좋습니다. 그런 다음 Intune 정책을 사용 하 여 이러한 인증서를 관리 합니다. 자세한 내용은 [워크로드를 전환하는 방법을](/configmgr/comanage/how-to-switch-workloads)을 참조하세요.

자세한 내용은 [비즈니스용 Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)를 참조하세요.

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/configmgr/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  

Configuration Manager는 다음과 같은 방법으로 비즈니스용 Windows Hello와 통합됩니다.  

- 사용자가 로그인 하는 데 사용할 수 있는 제스처와 사용할 수 없는 제스처를 제어 합니다.  

- 비즈니스용 Windows Hello KSP(키 스토리지 공급자)에 인증 인증서를 저장합니다. 자세한 내용은 [인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)을 참조하세요.  

- Configuration Manager 클라이언트를 실행 하는 도메인에 가입 된 Windows 10 장치에서 설정을 제어 하는 비즈니스용 Windows Hello 프로필을 만들고 배포 합니다. 버전 1910부터 인증서 기반 인증을 사용할 수 없습니다. 키 기반 인증을 사용하는 경우 인증서 프로필을 배포할 필요가 없습니다.

## <a name="configure-a-profile"></a>프로필 구성  

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다. **준수 설정**, **회사 리소스 액세스**를 차례로 확장 하 고 **비즈니스용 Windows Hello 프로필** 노드를 선택 합니다.

1. 리본에서 **비즈니스용 Windows Hello 프로필 만들기** 를 선택 하 여 프로필 마법사를 시작 합니다.

1. **일반** 페이지에서이 프로필에 대 한 이름 및 설명 (선택 사항)을 지정 합니다.

1. **지원 되는 플랫폼** 페이지에서이 프로필을 적용할 OS 버전을 선택 합니다.

1. **설정** 페이지에서 다음 설정을 구성합니다.

    - **비즈니스용 Windows Hello 구성**:이 프로필에서 비즈니스용 hello를 사용 하거나 사용 하지 않도록 설정 하거나 구성 하지 않을 지 여부를 지정 합니다.

    - **TPM(신뢰할 수 있는 플랫폼 모듈) 사용**: TPM은 추가적인 데이터 보안 계층을 제공합니다. 다음 값 중 하나를 선택합니다.  

      - **필수**: 액세스할 수 있는 TPM이 있는 디바이스만 비즈니스용 Windows Hello를 프로비전할 수 있습니다.  

      - **기본 설정**: 디바이스는 먼저 TPM을 사용하려고 합니다. 사용할 수 없는 경우 소프트웨어 암호화를 사용할 수 있습니다.

    - **인증 방법**:이 옵션을 **구성 안 함** 또는 **키 기반**으로 설정 합니다.

        > [!NOTE]
        > 버전 1910부터 Configuration Manager에서 비즈니스용 Windows Hello 설정을 사용 하는 인증서 기반 인증은 지원 되지 않습니다.

    - **최소 pin 길이 구성**: 사용자 PIN의 최소 길이를 요구 하려는 경우이 옵션을 사용 하도록 설정 하 고 값을 지정 합니다. 사용 하도록 설정 하는 경우 기본값은 `4`입니다.

    - **최대 pin 길이 구성**: 사용자 PIN의 최대 길이를 요구 하려는 경우이 옵션을 사용 하도록 설정 하 고 값을 지정 합니다. 사용 하도록 설정 하는 경우 기본값은 `127`입니다.

    - **PIN 만료(일) 필요**: 디바이스 PIN을 변경해야 할 때까지의 기간(일)을 지정합니다.

    - **이전 pin 다시 사용 안 함**: 사용자가 이전에 사용한 pin을 사용 하도록 허용 하지 않습니다.

    - **PIN에 대문자 필요**: 비즈니스용 Windows Hello PIN에 대문자를 사용해야 하는지 여부를 지정합니다. 다음 중에서 선택합니다.  

      - **허용**: PIN에 대문자를 사용할 수 있지만, 사용하지 않아도 됩니다.

      - **필수**: PIN에 대문자를 하나 이상 포함해야 합니다.  

      - **허용 안 함**: PIN에 대문자를 사용할 수 없습니다.  

    - **PIN에 소문자 필요** - 비즈니스용 Windows Hello PIN에 소문자를 사용해야 하는지 여부를 지정합니다. 다음 중에서 선택합니다.  

      - **허용**: PIN에 소문자를 사용할 수 있지만, 사용하지 않아도 됩니다.

      - **필수**: PIN에 소문자를 하나 이상 포함해야 합니다.  

      - **허용 안 함**: PIN에 소문자를 사용할 수 없습니다.  

    - **특수 문자 구성**: PIN에 특수 문자의 사용을 지정합니다. 다음 중에서 선택합니다.  

        > [!NOTE]
        > 특수 문자에는 다음 집합이 포함 됩니다.
        >
        > ``` characters
        > ! " # $ % & ' ( ) * + , - . / : ; < = > ? @ [ \ ] ^ _ ` { | } ~
        > ```

      - **허용**: 사용자가 PIN에 특수 문자를 사용할 수 있지만 반드시 필요 하지는 않습니다.  

      - **필수**: PIN에 특수 문자를 하나 이상 포함해야 합니다.  

      - **허용 안 함**: PIN에 특수 문자를 사용할 수 없습니다. 설정이 **구성 되지 않은**경우에도이 동작이 발생 합니다.  

    - **Pin에서 숫자 사용 구성**: pin의 숫자 사용을 지정 합니다. 다음 중에서 선택합니다.

      - **허용**: 사용자가 PIN에서 숫자를 사용할 수 있지만 반드시 필요 하지는 않습니다.  

      - **필수**: 사용자의 PIN에 하나 이상의 숫자를 포함 해야 합니다.  

      - **허용 되지 않음**: 사용자가 PIN에서 숫자를 사용할 수 없습니다.

    - **생체 인식 제스처 사용**: 얼굴 인식 또는 지문과 같은 생체 인식 인증을 사용 합니다. 이러한 모드는 비즈니스용 Windows Hello에 대 한 PIN의 대안입니다. 사용자는 생체 인식 인증에 실패하는 경우 PIN을 구성합니다.  

      **예**로 설정된 경우, 비즈니스용 Windows Hello에서 생체 인식 인증을 허용합니다. **아니요**로 설정된 경우, 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.  

    - **향상 된 스푸핑 방지 사용**:이를 지 원하는 장치에서 향상 된 스푸핑 방지를 구성 합니다. **예**로 설정하면, 지원되는 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.  

    - **휴대폰 로그인 사용**: 휴대 전화를 사용 하 여 2 단계 인증을 구성 합니다.

1. 마법사를 완료합니다.

다음 스크린샷은 비즈니스용 Windows Hello 프로필 설정의 예입니다.  

![사용 가능한 설정 목록을 보여 주는 비즈니스용 Windows Hello 정책 마법사](../media/hello-for-business-settings.png)

## <a name="configure-permissions"></a>사용 권한 구성

1. 도메인 관리자 또는 이와 동등한 자격 증명으로, 다음과 같은 선택적 기능이 설치 된 안전한 관리 워크스테이션에 로그인 합니다. RSAT: Active Directory Domain Services 및 Lightweight Directory Services 도구

1. **Active Directory 사용자 및 컴퓨터** 콘솔을 엽니다.

1. 도메인을 선택 하 고 **동작** 메뉴로 이동 하 여 **속성**을 선택 합니다.

1. **보안** 탭으로 전환 하 고 **고급**을 선택 합니다.

    > [!TIP]
    > **보안** 탭이 표시 되지 않으면 속성 창을 닫습니다. **보기** 메뉴로 이동 하 고 **고급 기능**을 선택 합니다.

1. **추가**를 선택합니다.

1. **보안 주체 선택** 을 선택 하 고 `Key Admins`을 입력 합니다.

1. **적용 대상** 목록에서 **하위 사용자 개체**를 선택합니다.

1. 페이지 맨 아래에서 **모두 지우기**를 선택 합니다.

1. **속성** 섹션에서 **msDS-KeyCredentialLink 읽기**를 선택합니다.

1. **확인** 을 선택 하 여 변경 내용을 저장 하 고 모든 창을 닫습니다.

## <a name="next-steps"></a>다음 단계

[인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)
