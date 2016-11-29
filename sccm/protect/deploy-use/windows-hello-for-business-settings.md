---
title: "비즈니스용 Windows Hello 설정 | System Center Configuration Manager"
description: "System Center Configuration Manager와 비즈니스용 Windows Hello를 통합하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/10/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2a45cfb3e00d8078fbf45bdc8a2668b7dd0a62c6
ms.openlocfilehash: 80f586763d034891aac9b87dcb38120602aa2b85


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager의 비즈니스용 Windows Hello 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 통해 Windows 10 장치의 대체 로그인 방법인 비즈니스용 Windows Hello(이전의 Microsoft Passport for Windows)와 통합할 수 있습니다. 비즈니스용 Windows Hello는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대체합니다.  

비즈니스용 Windows Hello를 통해 암호 대신 **사용자 제스처** 를 사용하여 로그인할 수 있습니다. 사용자 제스처는 단순 PIN, 생체 인식 인증 또는 외부 장치(예: 지문 판독기)일 수 있습니다.  

 Configuration Manager는 다음 두 가지 방법으로 비즈니스용 Windows Hello와 통합됩니다.  

-   Configuration Manager를 사용하여 사용자가 로그인하는 데 사용할 수 있는 제스처와 사용할 수 없는 제스처를 제어할 수 있습니다.  

-   비즈니스용 Windows Hello KSP(키 저장소 공급자)에 인증 인증서를 저장할 수 있습니다. 자세한 내용은 [인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

- Configuration Manager 클라이언트를 실행하는 도메인에 가입된 Windows 10 장치에 비즈니스용 Windows Hello 정책을 배포할 수 있습니다. 이 구성은 아래 [도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 구성](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices)에서 설명합니다. Intune과 함께 Configuration Manager를 사용하는 경우(하이브리드) Windows 10 및 Windows 10 Mobile 장치에서 이러한 설정을 구성할 수 있지만, Configuration Manager 클라이언트를 실행하는 도메인에 가입된 장치에서는 구성할 수 없습니다.   

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

         특수 문자에는 다음이 포함됩니다. **! " # $ % & ' ( ) \* + , - . / : ; < = > ? @ [ \ ] ^ _ ` { &#124; } ~**.  

    -   **PIN 만료(일) 필요** - 장치 PIN을 변경해야 할 때까지의 기간(일)을 지정합니다. 기본값은 41일입니다.  

    -   **이전 PIN의 재사용 방지** - 이전에 사용된 PIN을 다시 사용하지 않도록 제한하려면 이 설정을 사용합니다. 기본값은 마지막으로 사용한 5개 PIN을 다시 사용할 수 없는 것입니다.  

    -   **생체 인식 제스처 사용** - 비즈니스용 Windows Hello PIN 대신 안면 인식 또는 지문과 같은 생체 인식 인증을 사용합니다. 사용자는 생체 인식 인증에 실패하는 경우 작업 PIN을 구성해야 합니다.  

         **사용**으로 설정되면 비즈니스용 Windows Hello에서 생체 인식 인증을 허용합니다.  **사용 안 함**으로 설정되면 비즈니스용 Windows Hello에서 모든 계정 유형에 대해 생체 인식 인증을 금지합니다.  

    -   **사용 가능한 경우 향상된 스푸핑 방지 사용** - 향상된 스푸핑 방지 기능을 지원하는 장치에서 이 기능을 사용할지 여부를 구성합니다.  

         **사용**으로 설정되면 지원될 경우 모든 사용자는 안면에 대해 스푸핑 방지 기능을 사용하도록 요구됩니다.  

    -   **원격 Passport 사용** - 이 옵션이 **사용**으로 설정되면 원격 비즈니스용 Windows Hello를 데스크톱 컴퓨터 인증을 위한 휴대용 포함 장치로 사용할 수 있습니다. 데스크톱 컴퓨터가 Azure Active Directory에 가입되어 있어야 하고 해당 포함 장치는 비즈니스용 Windows Hello PIN으로 구성되어야 합니다.  

5.  작업을 마쳤으면 **확인**을 클릭합니다.  


## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 구성
다음 세 가지 방법으로 도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 설정을 제어할 수 있습니다.

- 비즈니스용 Windows Hello 프로필을 만들고 배포할 수 있습니다. 이것이 권장 방법입니다.
- 그룹 정책을 사용할 수 있습니다.  
- PowerShell 스크립트를 사용할 수 있습니다.

이 구성뿐 아니라 [인증서 프로필 구성](#configure-a-certificate-profile)에 설명된 대로 인증서 프로필도 배포해야 합니다.

### <a name="recommended-approach---configure-a-windows-hello-for-business-profile"></a>권장 방법 - 비즈니스용 Windows Hello 프로필 구성  

관리 콘솔의 **회사 리소스 액세스** 아래에서 **비즈니스용 Windows Hello 프로필**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 선택하여 프로필 마법사를 시작합니다. 마법사에서 요청된 설정을 제공하고 마지막 페이지에서 설정을 검토 및 확인한 다음 **닫기**를 클릭합니다. 설정이 표시되는 방식의 예는 다음과 같습니다.  

![비즈니스용 Windows Hello 설정](../media/Hello-for-Business-settings.png)

### <a name="configure-windows-hello-for-business-with-group-policy-in-active-directory"></a>Active Directory에서 그룹 정책을 사용하여 비즈니스용 Windows Hello 구성  

Active Directory 그룹 정책을 사용하여 사용자가 Windows에 로그인할 때 사용자의 비즈니스용 Hello 자격 증명을 프로비전하도록 Windows 10 도메인 연결 장치를 구성할 수 있습니다.

1.  Windows Server 컴퓨터에서 서버 관리자를 열고 **도구** > **그룹 정책 관리**로 이동합니다.    

2.  **그룹 정책 관리** 대화 상자에서 자동 작업 영역 연결을 사용하도록 설정할 도메인을 확장합니다.    

3.  **그룹 정책 개체**를 마우스 오른쪽 단추로 클릭한 다음 **새로 만들기**를 클릭합니다.  

4.  **새 GPO** 대화 상자에서 **비즈니스용 Hello 사용**과 같은 새 그룹 정책 개체의 이름을 입력하고 **확인**을 클릭합니다.  

5.  **그룹 정책 개체** 노드에서 방금 만든 개체를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.  

6.  **그룹 정책 관리 편집기** 대화 상자에서 **컴퓨터 구성** > **정책** > **관리 템플릿** > **Windows 구성 요소** > **비즈니스용 Windows Hello**로 이동합니다.  

7.  **비즈니스용 Windows Hello**를 마우스 오른쪽 단추로 클릭하고 **편집**을 클릭합니다.   

8.  **사용**을 선택하고 **적용**을 클릭한 후 **확인**을 클릭합니다.

이제 사용자가 방금 만든 그룹 정책 개체를 선택한 위치에 연결할 수 있습니다. 예를 들면 다음과 같습니다.    

   Windows 10 도메인 연결 컴퓨터가 배치될 AD의 특정 OU(조직 구성 단위)    

   Azure AD에 자동으로 등록될 Windows 10 도메인 연결 컴퓨터를 포함하는 특정 보안 그룹    

#### <a name="configure-windows-hello-for-business-by-deploying-a-powershell-script-with-configuration-manager"></a>Configuration Manager로 PowerShell 스크립트를 배포하여 비즈니스용 Windows Hello 구성    
Configuration Manager 응용 프로그램 관리를 사용하여 다음 PowerShell 스크립트를 만들고 배포할 수 있습니다.    

```    
powershell.exe -ExecutionPolicy Bypass -NoLogo -NoProfile -Command "& {New-ItemProperty "HKLM:\Software\Policies\Microsoft\PassportForWork" -Name "Enabled" -Value 1 -PropertyType "DWord" -Force}"  
```  

Configuration Manager 응용 프로그램 관리에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.  

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Configuration Manager에서 비즈니스용 Windows Hello 등록 인증서를 등록하도록 인증서 프로필 구성  
 비즈니스용 Windows Hello 인증서 기반 로그온 또는 Microsoft Hello를 사용하려면 다음을 구성합니다.  

-   Configuration Manager 인증서 프로필.  

-   인증서 프로필에서 스마트 카드 로그온 EKU를 사용하는 템플릿을 선택합니다.  

 자세한 내용은 [인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

### <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager를 사용하여 데이터 및 사이트 인프라 보호](../../protect/understand/protect-data-and-site-infrastructure.md)

 [비즈니스용 Windows Hello를 사용하여 ID 확인 관리](https://technet.microsoft.com/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport)  



<!--HONumber=Nov16_HO1-->


