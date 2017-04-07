---
title: "비즈니스용 Windows Hello 설정 | Microsoft 문서"
description: "System Center Configuration Manager와 비즈니스용 Windows Hello를 통합하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/28/2017
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
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: c9a6842958e6fa3f740caabbaf20aabb9df4e8a8
ms.lasthandoff: 03/27/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager의 비즈니스용 Windows Hello 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager를 통해 Windows 10 장치의 대체 로그인 방법인 비즈니스용 Windows Hello(이전의 Microsoft Passport for Windows)와 통합할 수 있습니다. 비즈니스용 Windows Hello는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대체합니다.  

비즈니스용 Windows Hello를 통해 암호 대신 **사용자 제스처** 를 사용하여 로그인할 수 있습니다. 사용자 제스처는 단순 PIN, 생체 인식 인증 또는 외부 장치(예: 지문 판독기)일 수 있습니다.  

 Configuration Manager는 다음 두 가지 방법으로 비즈니스용 Windows Hello와 통합됩니다.  

-   Configuration Manager를 사용하여 사용자가 로그인하는 데 사용할 수 있는 제스처와 사용할 수 없는 제스처를 제어할 수 있습니다.  

-   비즈니스용 Windows Hello KSP(키 저장소 공급자)에 인증 인증서를 저장할 수 있습니다. 자세한 내용은 [인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

- Configuration Manager 클라이언트를 실행하는 도메인에 가입된 Windows 10 장치에 비즈니스용 Windows Hello 정책을 배포할 수 있습니다. 이 구성은 아래 [도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 구성](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices)에서 설명합니다. Intune과 함께 Configuration Manager를 사용하는 경우(하이브리드) Windows 10 및 Windows 10 Mobile 장치에서 이러한 설정을 구성할 수 있지만, Configuration Manager 클라이언트를 실행하는 도메인에 가입된 장치에서는 구성할 수 없습니다. 자세한 내용은 [비즈니스용 Windows Hello 설정(하이브리드) 구성](../../mdm/deploy-use/windows-hello-for-business-settings.md)을 참조하세요.

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 구성
다음 세 가지 방법으로 도메인에 가입된 Windows 10 장치에서 비즈니스용 Windows Hello 설정을 제어할 수 있습니다.

- 비즈니스용 Windows Hello 프로필을 만들고 배포할 수 있습니다. 이것이 권장 방법입니다.
- 그룹 정책을 사용할 수 있습니다.  
- PowerShell 스크립트를 사용할 수 있습니다.

이 구성뿐 아니라 [인증서 프로필 구성](#configure-a-certificate-profile)에 설명된 대로 인증서 프로필도 배포해야 합니다.

## <a name="recommended-approach----configure-a-windows-hello-for-business-profile"></a>권장 방법 - 비즈니스용 Windows Hello 프로필 구성  

Configuration Manager 콘솔의 **회사 리소스 액세스** 아래에서 **비즈니스용 Windows Hello 프로필**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**를 선택하여 프로필 마법사를 시작합니다. 마법사에서 요청된 설정을 제공하고 마지막 페이지에서 설정을 검토 및 확인한 다음 **닫기**를 클릭합니다. 설정이 표시되는 방식의 예는 다음과 같습니다.  

![비즈니스용 Windows Hello 설정](../media/Hello-for-Business-settings.png)

## <a name="configure-windows-hello-for-business-with-group-policy-in-active-directory"></a>Active Directory에서 그룹 정책을 사용하여 비즈니스용 Windows Hello 구성  

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

## <a name="configure-windows-hello-for-business-by-deploying-a-powershell-script-with-configuration-manager"></a>Configuration Manager로 PowerShell 스크립트를 배포하여 비즈니스용 Windows Hello 구성    
Configuration Manager 응용 프로그램 관리를 사용하여 다음 PowerShell 스크립트를 만들고 배포할 수 있습니다.    

**powershell.exe -ExecutionPolicy Bypass -NoLogo -NoProfile -Command "& {New-ItemProperty "HKLM:\Software\Policies\Microsoft\PassportForWork" -Name "Enabled" -Value 1 -PropertyType "DWord" -Force}"** 

Configuration Manager 응용 프로그램 관리에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.  

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Configuration Manager에서 비즈니스용 Windows Hello 등록 인증서를 등록하도록 인증서 프로필 구성  
 비즈니스용 Windows Hello 인증서 기반 로그온 또는 Microsoft Hello를 사용하려면 다음을 구성합니다.  

-   Configuration Manager 인증서 프로필.  

-   인증서 프로필에서 스마트 카드 로그온 EKU를 사용하는 템플릿을 선택합니다.  

-    인증서를 비즈니스용 Windows Hello 키 컨테이너에 저장하려고 하고 인증서 프로필에 **스마트 카드 로그온** EKU를 사용하는 경우 인증서가 제대로 유효성이 검사되었는지 확인하려면 키 등록에 대해 다음 사용 권한을 구성해야 합니다.
먼저 **키 관리** 그룹을 만들고 모든 Configuration Manager 관리 지점 컴퓨터를 멤버로 이 그룹에 추가해야 합니다.

    1.    도메인 관리자 또는 이와 동등한 자격 증명을 사용하여 도메인 컨트롤러 또는 관리 워크스테이션에 로그인합니다.
    2.    **Active Directory 사용자 및 컴퓨터**를 엽니다.
    3.    탐색 창에서 도메인 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.
    4.    *<domain name>* **속성** 대화 상자의 **보안** 탭에서 **고급**을 클릭합니다. **보안** 탭이 표시되지 않으면 **Active Directory 사용자 및 컴퓨터**의 **보기** 메뉴에서 **고급 기능**을 켭니다.
    5.    **추가**를 클릭합니다.
    6.    *<domain name>* **권한 항목** 대화 상자에서 **보안 주체 선택**을 클릭합니다.
    7.    **사용자, 컴퓨터, 서비스 계정 또는 그룹 선택** 대화 상자에서 **선택할 개체 이름 입력** 텍스트 상자에 **키 관리**를 입력합니다.  **확인**을 클릭합니다.
    8.    **적용 대상** 목록에서 **하위 사용자 개체**를 선택합니다.
    9.    페이지 아래쪽으로 스크롤하고 **모두 지우기**를 클릭합니다.
    10.    **속성** 섹션에서 **msDS-KeyCredentialLink 읽기**를 선택합니다.
    11.    **확인**을 세 번 클릭하여 작업을 완료합니다.


 자세한 내용은 [인증서 프로필](introduction-to-certificate-profiles.md)을 참조하세요.  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager를 사용하여 데이터 및 사이트 인프라 보호](../../protect/understand/protect-data-and-site-infrastructure.md)

 [비즈니스용 Windows Hello를 사용하여 ID 확인 관리](https://technet.microsoft.com/itpro/windows/keep-secure/manage-identity-verification-using-microsoft-passport)  

