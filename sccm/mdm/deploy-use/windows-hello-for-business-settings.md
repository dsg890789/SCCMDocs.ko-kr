---
title: "비즈니스용 Windows Hello 설정 | Microsoft 문서"
description: "System Center Configuration Manager와 비즈니스용 Windows Hello를 통합하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0593c07-5dd7-4d23-a0d8-d30165f49ef7
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 8c7bf901caa49c8585a9ed3913d4a5a2aac57013
ms.openlocfilehash: 7ac2baeb3c10ce90eb643fa28a953186b571d037
ms.lasthandoff: 03/21/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager-hybrid"></a>System Center Configuration Manager의 비즈니스용 Windows Hello 설정(하이브리드)

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 통해 Windows 10 장치의 대체 로그인 방법인 비즈니스용 Windows Hello(이전의 Microsoft Passport for Windows)와 통합할 수 있습니다. 비즈니스용 Windows Hello는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대체합니다.  

비즈니스용 Windows Hello를 통해 암호 대신 **사용자 제스처** 를 사용하여 로그인할 수 있습니다. 사용자 제스처는 단순 PIN, 생체 인식 인증 또는 외부 장치(예: 지문 판독기)일 수 있습니다.  

 Configuration Manager는 다음 두 가지 방법으로 비즈니스용 Windows Hello와 통합됩니다.  

-   Configuration Manager를 사용하여 사용자가 로그인하는 데 사용할 수 있는 제스처와 사용할 수 없는 제스처를 제어할 수 있습니다.  

-   비즈니스용 Windows Hello KSP(키 저장소 공급자)에 인증 인증서를 저장할 수 있습니다. 자세한 내용은 [인증서 프로필](create-pfx-certificate-profiles.md)을 참조하세요.  

- Configuration Manager 클라이언트를 실행하는 도메인에 가입된 Windows 10 장치에 비즈니스용 Windows Hello 정책을 배포할 수 있습니다. 이 구성은 [도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 구성](../../protect/deploy-use/windows-hello-for-business-settings.md#configure-windows-hello-for-business-on-domain-joined-windows-10-devices)에서 설명합니다. Intune과 함께 Configuration Manager를 사용하는 경우(하이브리드) Windows 10 및 Windows 10 Mobile 장치에서 이러한 설정을 구성할 수 있지만, Configuration Manager 클라이언트를 실행하는 도메인에 가입된 장치에서는 구성할 수 없습니다.   

비즈니스용 Windows Hello 설정을 구성하는 방법에 대한 일반적인 내용은 [System Center Configuration Manager의 비즈니스용 Windows Hello 설정](../../protect/deploy-use/windows-hello-for-business-settings.md)을 참조하세요.

## <a name="configure-windows-hello-for-business-settings-hybrid"></a>비즈니스용 Windows Hello 설정(하이브리드) 구성  

1.  Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **Microsoft Intune 구독**을 클릭합니다.  

3.  목록에서 Microsoft Intune 구독을 선택하고 **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **Windows(MDM)**를 클릭합니다.  

4.  **Microsoft Intune 구독 속성** 대화 상자의 **비즈니스용 Windows Hello** 탭에서, 다음 값 중에서 등록된 모든 Windows 10 및 Windows 10 Mobile 장치에 영향을 주는 값을 선택합니다.  

    -   **등록된 장치에서 비즈니스용 Windows Hello 사용 안 함** 또는 **등록된 장치에 비즈니스용 Windows Hello 사용** - 등록된 모든 Windows 10 및 Windows 10 모바일 장치에서 비즈니스용 Windows Hello를 사용하거나 사용하지 않습니다.  

    -   **TPM(신뢰할 수 있는 플랫폼 모듈) 사용** - TPM(신뢰할 수 있는 플랫폼 모듈) 칩은 추가적인 데이터 보안 계층을 제공합니다. 다음 값 중 하나를 선택합니다.  

        -   **필수** (기본값) - 액세스할 수 있는 TPM이 있는 장치만 비즈니스용 Windows Hello를 프로비전할 수 있습니다.  

        -   **기본 설정** - 장치는 먼저 TPM을 사용하려고 합니다. 사용할 수 없는 경우 소프트웨어 암호화를 사용할 수 있습니다.  

    -   **최소 PIN 길이 필요** - 비즈니스용 Windows Hello PIN에 필요한 최소 문자 수를 지정합니다. 4자 이상을 사용해야 합니다(기본값 6자).  

    -   **최대 PIN 길이 필요** - 비즈니스용 Windows Hello PIN에 허용되는 최대 문자 수를 지정합니다. 최대 127자를 사용할 수 있습니다.  

    -   **PIN에 소문자 필요** - 비즈니스용 Windows Hello PIN에 소문자를 사용해야 하는지 여부를 지정합니다. 다음 중에서 선택합니다.  

        -   **허용** - PIN에 소문자를 사용할 수 있습니다.  

        -   **필수** - PIN에 소문자를 하나 이상 포함해야 합니다.  

        -   **허용되지 않음** (기본값) - PIN에서 소문자를 사용하지 않아야 합니다.  

    -   **PIN에 대문자 필요** - 비즈니스용 Windows Hello PIN에 대문자를 사용해야 하는지 여부를 지정합니다. 다음 중에서 선택합니다.  

        -   **허용** - PIN에 대문자를 사용할 수 있습니다.  

        -   **필수** - PIN에 대문자를 하나 이상 포함해야 합니다.  

        -   **허용되지 않음** (기본값) - PIN에서 대문자를 사용하지 않아야 합니다.  

    -   **특수 문자 필요** - PIN에 특수 문자의 사용을 지정합니다. 다음 중에서 선택합니다.  

        -   **허용** - PIN에 특수 문자를 사용할 수 있습니다.  

        -   **필수** - PIN에 특수 문자를 하나 이상 포함해야 합니다.  

        -   **허용되지 않음** (기본값) - PIN에 특수 문자를 사용하지 않아야 합니다(설정이 구성되지 않은 경우에도 이 동작 수행).  

         특수 문자에는 다음이 포함됩니다. **! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ _ ` { &#124; } ~**  

    -   **PIN 만료(일) 필요** - 장치 PIN을 변경해야 할 때까지의 기간(일)을 지정합니다. 기본값은 41일입니다.  

    -   **이전 PIN의 재사용 방지** - 이전에 사용된 PIN을 다시 사용하지 않도록 제한하려면 이 설정을 사용합니다. 기본값은 마지막으로 사용한 5개 PIN을 다시 사용할 수 없는 것입니다.  

    -   **생체 인식 제스처 사용** - 비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 사용합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다.  

         **사용**으로 설정되면 비즈니스용 Windows Hello에서 생체 인식 인증을 허용합니다.  **사용 안 함**으로 설정되면 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.  

    -   **사용 가능한 경우 향상된 스푸핑 방지 사용** - 향상된 스푸핑 방지 기능을 지원하는 장치에서 이 기능을 사용할지 여부를 구성합니다.  

         **사용**으로 설정되면 지원될 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.  

    -   **원격 Passport 사용** - 이 옵션이 **사용**으로 설정되면 원격 비즈니스용 Windows Hello를 데스크톱 컴퓨터 인증을 위한 휴대용 포함 장치로 사용할 수 있습니다. 데스크톱 컴퓨터가 Azure Active Directory에 가입되어 있어야 하고 해당 포함 장치는 비즈니스용 Windows Hello PIN으로 구성되어야 합니다.  

5.  작업을 마쳤으면 **확인**을 클릭합니다.  

### <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager를 사용하여 데이터 및 사이트 인프라 보호](../../protect/understand/protect-data-and-site-infrastructure.md)

 [비즈니스용 Windows Hello를 사용하여 ID 확인 관리](https://technet.microsoft.com/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport)  

