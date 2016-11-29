---
title: "설치 하이브리드 MDM | System Center Configuration Manager 및 Microsoft Intune"
description: "Configuration Manager 및 Intune을 사용하여 하이브리드 장치 등록을 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
caps.latest.revision: 34
caps.handback.revision: 0
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 44c0947fcb7abdc4369fe0b4f47409b49d068861

---

# <a name="setup-hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune을 사용하여 하이브리드 MDM(모바일 장치 관리) 설정

*적용 대상: System Center Configuration Manager(현재 분기)*


Configuration Manager를 사용하여 iOS, Windows 및 Android 장치를 관리하려면 먼저 Intune에 등록해야 합니다. Configuration Manager 및 Intune을 사용하여 하이브리드 장치 등록을 설정하려면 다음 단계를 따르세요. 다음 단계를 완료하면 사용자에 대해 BYOD("Bring Your Own Device") 등록을 사용하도록 설정됩니다. 이 단계는 [회사 소유 장치 등록](enroll-company-owned-devices.md)의 필수 조건이기도 합니다.

 |단계|세부 정보|  
 |-----------|-------------|  
 |**1단계:** [MDM 컬렉션 만들기](#step-1-create-an-mdm-collection)|해당 장치를 등록할 수 있는 사용자를 포함하는 Configuration Manager 사용자 컬렉션을 만듭니다.|  
 |**2단계:** [도메인 이름 요구 사항](#step-2-domain-name-requirements)|조직의 DNS(도메인 이름 서비스) 및 Active Directory 사용자 관리가 MDM 요구 사항을 충족하는지 확인합니다.|
 |**3단계:** [Intune 구독 구성](#step-3-configure-intune-subscription)|Intune 서비스를 사용하면 인터넷을 통해 장치를 관리할 수 있습니다.|  
 |**4단계:** [계약조건 추가](#step-4-add-terms-and-conditions)| 회사 포털 앱을 사용하기 전에 사용자가 동의해야 하는 계약조건을 만듭니다.|
 |**5단계:** [서비스 연결 지점 만들기](#step-5-create-service-connection-point)|서비스 연결 지점은 설정과 소프트웨어 배포 정보를 Configuration Manager에 전송하고 모바일 장치에서 상태 및 인벤토리 메시지를 검색합니다. |  
 |**6단계:** [플랫폼 등록 사용](#step-6-enable-platform-enrollment)|[iOS](#ios-and-mac-enrollment-setup) 및 [Windows](#windows-enrollment-setup) 장치에 대한 MDM 등록에는 서비스와 장치 간의 통신을 위한 추가 단계가 필요합니다. Android에는 추가 구성이 필요하지 않습니다.|  
 |**7단계:** [추가 관리 설정](#step-7-set-up-additional-management)|(선택 사항) 등록된 장치에 대한 구성 항목 및 조건부 액세스를 설정합니다.|
 |**8단계:** [MDM 구성 확인](#step-8-verify-mdm-configuration)|로그 파일을 보고 서비스 연결 지점이 성공적으로 만들어졌는지, 그리고 사용자 계정이 동기화되고 있는지 확인합니다.|
 |**9단계:** [장치 등록](#step-9-enroll-devices)|조직의 요구 사항에 맞게 장치를 등록하거나 회사 소유 장치 등록을 시작하는 방법을 사용자에게 알려줍니다.|

Configuration Manager 없이 Intune을 사용하고 싶으세요?
> [!div class="button"]
[Intune 문서 보기 >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)

## <a name="step-1-create-an-mdm-collection"></a>1단계: MDM 컬렉션 만들기
관리에 장치를 등록할 수 있는 사용자를 지정하려면 Configuration Manager 사용자 컬렉션이 필요합니다. Intune 라이선스가 사용자에게 할당되기 때문에 사용자 컬렉션만 대상으로 지정할 수 있습니다. 테스트 목적으로 **직접 규칙**을 설정하고 장치를 등록할 수 있는 특정 사용자를 추가할 수 있습니다. Configuration Manager 콘솔에서 **자산 및 준수** > **사용자 컬렉션**을 선택하고 **홈** 탭 > **만들기** 그룹을 클릭한 다음 **사용자 컬렉션 만들기**를 클릭합니다. 광범위한 배포의 경우 **쿼리 규칙**을 사용하여 사용자를 정의해야 합니다. 컬렉션에 대한 자세한 내용은 [컬렉션을 만드는 방법](https://technet.microsoft.com/library/mt629371.aspx)을 참조하세요.

![MDM에 대한 사용자 컬렉션 만들기](../media/mdm-create-user-collection.png)

## <a name="step-2-domain-name-requirements"></a>2단계: 도메인 이름 요구 사항

필요한 경우 다음 단계를 수행하여 Configuration Manager 외부 종속성을 충족합니다.

1. 장치를 등록하려면 각 사용자에게 Intune 라이선스가 할당되어야 합니다. Intune 라이선스를 사용자에 연결하려면 각 사용자에게 공개적으로 확인할 수 있는 UPN(사용자 계정 이름)(예: johndoe@contoso.com) 또는 Azure Active Directory에 구성된 대체 로그인 ID)이 있어야 합니다. 대체 로그인 ID를 구성하면 해당 UPN이 NetBIOS 형식(예: CONTOSO\johndoe)인 사용자도 메일 주소를 사용하여 로그인할 수 있습니다.

  - 회사에서 공개적으로 확인할 수 있는 UPN(즉, johndoe@contoso.com),)을 사용하는 경우에는 추가 구성이 필요하지 않습니다.
  - 회사에서 확인할 수 없는 UPN(즉, CONTOSO\johndoe)을 사용하는 경우 [Azure Active Directory에서 대체 ID를 구성](https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-custom/#pages-under-the-section-sync)해야 합니다.

2.  AD FS(Active Directory Federated Services)를 배포 및 구성합니다. (선택적)

     Single Sign-On을 설정하면 사용자가 회사 자격 증명에 로그인하여 Intune의 서비스에 액세스할 수 있습니다.

     자세한 내용은 다음 항목을 참조하세요.
    -   [Single Sign-On 준비](http://go.microsoft.com/fwlink/?LinkID=271124)
    -   [Single Sign-On을 사용할 AD FS 2.0 계획 및 배포](http://go.microsoft.com/fwlink/?LinkID=271125)

3.  디렉터리 동기화 배포 및 구성

     디렉터리 동기화를 사용하면 동기화된 사용자 계정으로 Intune을 채울 수 있습니다. 동기화된 사용자 계정 및 보안 그룹은 Intune에 추가됩니다. 디렉터리 동기화를 사용하도록 설정하지 않으면 Configuration Manager MDM with Microsoft Intune을 설정할 때 보통 장치에서 등록할 수 없습니다.

     자세한 내용은 Active Directory 문서 라이브러리의 [디렉터리 통합](http://go.microsoft.com/fwlink/?LinkID=271120) 을 참조하세요.

4.  선택 사항이며 권장되지 않는 단계: ADFS(Active Directory Federation Services)를 사용하지 않을 경우 사용자의 Microsoft Online 암호를 다시 설정합니다.

     AD FS를 사용하지 않을 경우 각 사용자의 Microsoft Online 암호를 설정해야 합니다.

## <a name="step-3-configure-intune-subscription"></a>3단계: Intune 구독 구성
 Intune 구독을 사용하면 인터넷을 통해 장치를 관리할 수 있습니다. 여기에는 장치를 등록할 수 있는 사용자 컬렉션 지정 및 사용자에게 표시되는 정보 정의가 포함됩니다. Intune 구독은 다음을 수행합니다.

-   서비스 연결 지점이 Intue 서비스에 연결하는 데 필요한 인증서 검색
-   사용자가 모바일 장치를 등록할 수 있는 사용자 컬렉션 정의
-   지원할 모바일 플랫폼 정의 및 구성

> [!IMPORTANT]
>  Configuration Manager에서 Microsoft Intune에 대한 구독을 만들면 사이트의 서비스 연결 지점이 "온라인 모드"가 됩니다. [System Center Configuration Manager의 서비스 연결 지점 정보](../../core/servers/deploy/configure/about-the-service-connection-point.md)를 참조하세요.

### <a name="to-create-the-microsoft-intune-subscription"></a>Microsoft Intune 구독을 만들려면

1.  아직 그렇게 하지 않은 경우 [Microsoft Intune](http://go.microsoft.com/fwlink/?LinkID=258216)에서 Microsoft Intune 계정을 등록합니다.  Intune 계정을 만든 후에는 Intune 계정에 사용자를 추가하거나 추가 설정 구성을 수행할 필요가 없습니다.

2.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

3.  **관리** 작업 영역에서 **클라우드 서비스**를 확장하고 **Microsoft Intune 구독**을 클릭합니다. **홈** 탭에서 **Microsoft Intune 구독 추가**를 클릭합니다.

![Intune 구독 만들기](../media/mdm-set-intune.png)

4.  Microsoft Intune 구독 만들기 마법사의 **소개** 페이지에서 텍스트를 검토하고 **다음**을 클릭합니다.

5.  **구독** 페이지에서 **로그인** 을 클릭하고 회사 또는 학교 계정을 사용하여 로그인합니다. **모바일 장치 관리 기관 설정** 대화 상자에서 Configuration Manager 콘솔을 통해 Configuration Manager를 사용하는 방법으로만 모바일 장치를 관리하려면 확인란을 선택합니다. 구독을 계속하려면 이 옵션을 선택해야 합니다.

    > [!IMPORTANT]
    >  Configuration Manager를 관리 기관으로 선택한 후에는 향후에 관리 기관을 Microsoft Intune으로 변경할 수 없습니다.

6.  개인 정보 취급 방침 링크를 클릭하여 검토하고 **다음**을 클릭합니다.

7.  **일반** 페이지에서 다음 옵션을 지정한 후 **다음**을 클릭합니다.

  -   **컬렉션**: 모바일 장치를 등록할 사용자가 포함된 사용자 컬렉션을 지정합니다.

      > [!NOTE]
      >  사용자가 컬렉션에서 제거될 경우 사용자 데이터베이스에서 사용자 레코드가 제거되면 최대 24시간 동안 사용자 장치가 계속 관리됩니다.

  -   **회사 이름**: 회사 이름을 지정합니다.

  -   **회사 개인 정보 취급 방침 문서의 URL**: 인터넷에서 액세스할 수 있는 링크에 회사 개인 정보 취급 방침을 게시하는 경우 사용자가 회사 포털에서 이 방침에 액세스할 수 있는 링크를 제공합니다(예: http://www.contoso.com/CP_privacy.html). 개인 정보 취급 방침 정보에는 사용자가 회사와 공유할 수 있는 정보가 명시될 수 있습니다.

  -   **회사 포털의 색 구성표**: 선택적으로 회사 포털의 기본 색상인 파란색을 변경합니다.

  -   **Configuration Manager 사이트 코드**: 모바일 장치를 관리할 기본 사이트의 사이트 코드를 지정합니다.

    > [!NOTE]
    >  사이트 코드를 변경하면 새 등록만 영향을 받으며 기존에 등록된 장치는 영향을 받지 않습니다.

8.  **회사 연락처 정보** 페이지에서 회사 포털 앱의 **IT 문의** 아래에 표시되는 회사 연락처 정보를 지정합니다. 회사에 대한 연락처 정보를 제공하고 **다음**을 클릭합니다.

9. **회사 로고** 페이지에서 회사 포털에 로고를 표시할지 여부를 선택하고 **다음**을 클릭할 수 있습니다.

10. 마법사를 완료합니다.

## <a name="step-4-add-terms-and-conditions"></a>4단계: 계약조건 추가
 모바일 장치에 대한 Intune 관리를 구성한 경우 **사용 약관**을 만들 수 있습니다. 장치를 등록할 때 발생하는 상황을 사용 약관을 통해 설명합니다. 사용자는 장치를 등록하려면 먼저 사용 약관에 동의해야 합니다. Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **준수 설정** > **계약조건**으로 이동한 다음 **계약조건 만들기**를 클릭합니다. [System Center Configuration Manager의 사용 약관](terms-and-conditions.md)을 참조하세요.

##  <a name="step-5-create-service-connection-point"></a>5단계: 서비스 연결 지점 만들기
구독을 만든 후에는 Intue 서비스에 연결하는 데 사용할 수 있는 서비스 연결 지점 사이트 시스템 역할을 설치할 수 있습니다. 이 사이트 시스템 역할은 Intue 서비스에 설정 및 응용 프로그램을 푸시합니다.

 서비스 연결 지점은 설정과 소프트웨어 배포 정보를 Configuration Manager에 전송하고 모바일 장치에서 상태 및 인벤토리 메시지를 검색합니다. Configuration Manager 서비스는 게이트웨이 역할을 하며 모바일 장치와 통신하고 설정을 저장합니다.

> [!NOTE]
>  서비스 연결 지점 사이트 시스템 역할은 중앙 관리 사이트 또는 독립 실행형 기본 사이트에만 설치할 수 있습니다. 서비스 연결 지점에는 인터넷 액세스가 있어야 합니다.


### <a name="configure-the-service-connection-point-role"></a>서비스 연결 지점 역할 구성

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **사이트**를 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.

3.  다음 중 해당 단계를 사용하여 새 또는 기존 사이트 시스템 서버에 **서비스 연결 지점** 역할을 추가합니다.

    -   새 사이트 시스템 서버: **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기** 를 클릭하여 사이트 시스템 서버 만들기 마법사를 시작합니다.

    -   기존 사이트 시스템 서버: 서비스 연결 지점 역할을 설치할 서버를 클릭합니다. 그런 다음 **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가** 를 클릭하여 사이트 시스템 역할 추가 마법사를 시작합니다.

4.  **시스템 역할 선택** 페이지에서 **서비스 연결 지점**을 선택하고 **다음**을 클릭합니다.

![서비스 연결 지점 만들기](../media/mdm-service-connection-point.png)

5.  마법사를 완료합니다.

### <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>서비스 연결 지점이 Microsoft Intune 서비스를 인증하는 방법
 서비스 연결 지점은 인터넷을 통해 모바일 장치를 관리하는 클라우드 기반 Intune 서비스에 대한 연결을 설정하여 Configuration Manager를 확장합니다. 서비스 연결 지점은 Intune 서비스를 다음과 같이 인증합니다.

1.  Configuration Manager 콘솔에서 Intune 구독을 만들 때 Configuration Manager 관리자가 Azure Active Directory에 연결하여 인증을 받습니다. 그러면 개별 ADFS 서버로 리디렉션되어 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다. 해당 정보를 입력하면 Intune에서 테넌트에 인증서를 발급합니다.

2.  1단계에서 발급된 인증서가 서비스 연결 지점 사이트 역할에 설치되며 Microsoft Intune 서비스와의 이후 모든 통신을 인증하고 권한을 부여하는 데 사용됩니다.

## <a name="step-6-enable-platform-enrollment"></a>6단계: 플랫폼 등록 사용
  장치 등록을 사용하려면 각 장치 플랫폼마다 추가 구성이 필요합니다.
  - [iOS 및 Mac 등록 설정](#ios-and-mac-enrollment-setup): Apple MDM 푸시 인증서를 가져옵니다.
  - [Windows 등록 설정](#windows-enrollment-setup): DNS를 구성하고 Windows PC, Windows 10 Mobile 및 Windows Phone 장치에 대해 등록을 사용하도록 설정합니다.
  - Android: Android 장치는 등록을 사용하도록 설정하기 위한 추가 단계가 필요하지 않습니다.


### <a name="ios-and-mac-enrollment-setup"></a>iOS 및 Mac 등록 설정
  다음 단계에서는 Intune 서비스에 Apple MDM 푸시 인증서를 업로드하여 Apple 장치에 대해 관리를 사용하도록 설정합니다.

  1.  **인증서 서명 요청 다운로드** - Apple에서 APNs 인증서를 요청하려면 인증서 서명 요청 파일(.csr)이 필요합니다.  

      1.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스**> **Microsoft Intune 구독**으로 이동합니다.  

      2.  **홈** 탭에서 **APNs 인증서 요청 만들기**를 클릭합니다. **APNs CSR(인증서 서명 요청) 요청** 대화 상자가 열립니다.  

      3.  **찾아보기** 를 클릭하여 새 인증서 서명 요청(.csr) 파일을 저장할 경로를 찾습니다. 인증서 서명 요청(.csr) 파일을 로컬로 저장합니다.  

      4.  **다운로드**를 클릭합니다. 새 Microsoft Intune .csr 파일이 다운로드되고 Configuration Manager에 의해 저장됩니다. .csr 파일은 APC(Apple Push Certificate) 포털에서 트러스터 관계 인증서를 요청하는 데 사용됩니다.  

  2.  **Apple에서 APNs 인증서 요청** - APNs(Apple Push Notification Service) 인증서를 사용하면 관리 서비스, Intune 및 등록된 iOS 모바일 장치 간에 트러스트 관계를 설정할 수 있습니다.  

      1.  브라우저에서 [Apple Push Certificates 포털](http://go.microsoft.com/fwlink/?LinkId=269844) 로 이동한 다음 회사 Apple ID로 로그인합니다. 나중에 APNs 인증서를 갱신하기 위해 이 Apple ID를 사용해야 합니다.  

      2.  인증서 서명 요청(.csr) 파일을 사용하여 마법사를 완료합니다. APNs 인증서를 다운로드하고 .pem 파일을 로컬로 저장합니다. 이 APNs 인증서(.pem) 파일은 APN(Apple Push Notification) 서버와 Intune의 모바일 장치 관리 기관 간의 트러스트 관계를 설정하는 데 사용됩니다.  

  3.  **등록을 사용하도록 설정하고 APNs 인증서 업로드** - iOS 등록을 사용하도록 설정하려면 APNs 인증서를 업로드합니다.  

      1.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  

      2.  **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **iOS**를 클릭합니다.  

          > [!NOTE]  
          >  구성 관리자 콘솔에서 iOS 등록을 사용하도록 설정할 때까지 APNs(Apple Push Notification service) 인증서를 업로드하지 마세요.  

      3.  **Microsoft Intune 구독 속성** 대화 상자에서 **iOS** 탭을 선택하고 **iOS 등록 사용** 확인란을 클릭하여 선택합니다.  

      4.  **찾아보기**를 클릭하고 Apple에서 다운로드한 APNs 인증서(.cer) 파일이 있는 위치로 이동합니다. Configuration Manager가 APNs 인증서 정보를 표시합니다. **확인** 을 클릭하여 APN 인증서를 Intune에 저장합니다.    


자세한 내용은 [iOS 및 Mac 등록](enroll-hybrid-ios-mac.md)을 참조하세요.

### <a name="windows-enrollment-setup"></a>Windows 등록 설정  
Intune과 Configuration Manager를 사용하여 데스크톱, 노트북 및 Windows를 실행하는 다른 장치를 모바일 장치로 관리할 수 있습니다. 해당 장치에서 회사 또는 학교 계정을 추가하여 [Azure Active Directory에 가입할 때 자동으로 등록](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/enroll-hybrid-windows#azure-active-directory-enrollment)되도록 Windows 10 장치를 구성할 수도 있습니다.

DNS 별칭(CNAME 레코드 종류)을 사용하면 장치를 등록하는 동안 서버 이름이 자동으로 채워지므로 사용자가 보다 쉽게 장치를 등록할 수 있습니다. 그런 다음 Windows PC 모바일 장치에 대해 등록을 사용하도록 설정할 수 있습니다.  

1. Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동한 후 다음을 수행합니다.  
  - **Windows PC:** **홈** 탭에서 **플랫폼 구성**, **Windows Phone**을 차례로 클릭합니다. **일반** 탭에서 **Windows 등록 사용**을 선택합니다.  
  - **Windows 10 Mobile 및 Windows Phone:** **홈** 탭에서 **플랫폼 구성**을 클릭한 다음 **Windows Phone**을 클릭합니다.  **일반** 탭에서  **Windows Phone 8.1 및 Windows 10 Mobile**을 선택합니다.

2.  또한 회사 포털 앱을 사용하여 등록을 단순화하도록 Configuration Manager를 구성할 수 있습니다.
(선택 사항) 회사의 DNS 레코드에서, 회사의 도메인에 있는 URL로 전송된 요청을 Microsoft의 클라우드 서비스 서버로 리디렉션하는 DNS 별칭(CNAME 레코드 종류)을 만듭니다.  예를 들어 회사의 도메인이 contoso.com인 경우 DNS에 EnterpriseEnrollment.contoso.com을 EnterpriseEnrollment-s.manage.microsoft.com으로 리디렉션하는 CNAME을 만들어야 합니다.  

|유형|호스트 이름|지시 대상|  
|----------|---------------|---------------|  
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|  
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|  

자세한 내용은 [Windows 등록](enroll-hybrid-windows.md)을 참조하세요.

### <a name="android-enrollment-setup"></a>Android 등록 설정
Configuration Manager 및 Intune을 사용하여 Android를 실행하는 휴대폰과 태블릿을 관리할 수 있습니다.
1.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  

2.  **홈** 탭의 **구독** 그룹에서 **플랫폼 구성** > **Android**를 클릭합니다.  

3.  **Microsoft Intune 구독 속성** 대화 상자에서 **Android** 탭을 선택하고 클릭하여 **Android 등록 사용** 확인란을 선택합니다.

자세한 내용은 [Android](enroll-hybrid-android.md)를 참조하세요.

## <a name="step-7-set-up-additional-management"></a>7단계: 추가 관리 설정
(선택 사항) 장치가 등록되기 전에 추가 관리를 설정할 수 있습니다. 장치가 등록된 후에 이러한 관리 솔루션을 만들고 배포할 수도 있지만 대부분의 조직에서는 장치가 관리에 추가될 때 배포하려고 합니다.

**구성 항목**을 사용하면 장치 플랫폼에 따라 등록된 장치에서 PIN 요구 또는 암호화 요구 등의 설정을 관리할 수 있습니다.
- [Windows 10 및 Windows 8.1 장치](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)
- [Windows Phone 장치](/sccm/compliance/deploy-use/create-configuration-items-for-windows-phone-devices-managed-without-the-client)
- [iOS 및 Mac 장치](/sccm/compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)
- [Android 및 삼성 KNOX 장치](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client)

**응용 프로그램**을 관리 장치에 배포할 수 있습니다.
- [iOS 응용 프로그램](/sccm/apps/get-started/creating-ios-applications)
- [Mac 응용 프로그램](/sccm/apps/get-started/creating-mac-computer-applications)
- [Windows PC 응용 프로그램](/sccm/apps/get-started/creating-windows-applications)
- [Windows Phone 응용 프로그램](/sccm/apps/get-started/creating-windows-phone-applications)
- [Android 응용 프로그램](/sccm/apps/get-started/creating-android-applications)

**조건부 액세스**를 사용하면 다음을 비롯한 회사 리소스에 대한 액세스를 관리할 수 있습니다.  
- [메일 액세스](/sccm/protect/deploy-use/manage-email-access)
- [SharePoint 액세스](/sccm/protect/deploy-use/manage-sharepoint-online-access)
- [비즈니스용 Skype 액세스](/sccm/protect/deploy-use/manage-skype-for-business-online-access)
- [Dynamic CRM Online](/sccm/protect/deploy-use/manage-dynamics-crm-online-access)

## <a name="step-8-verify-mdm-configuration"></a>8단계: MDM 구성 확인

 다음 로그 파일을 확인하여 특정 장치 관리 구성 요소를 확인할 수 있습니다.

-   Cloudusersync.log에서 사용자 계정이 제대로 동기화되었는지 확인합니다.

-   Sitecomp.log에서 서비스 연결 지점이 제대로 만들어졌는지 확인합니다.

## <a name="step-9-enroll-devices"></a>9단계: 장치 등록
이제 하이브리드 설정이 완료되었습니다. Configuration Manager에서 다음과 같은 다양한 방법으로 장치를 등록할 수 있습니다.
- 사용자 소유(BYOD) 장치: [사용자에게 장치 등록 방법을 알림](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) - 등록 지침은 Intune 하이브리드 관리 장치와 동일합니다.
- 회사 소유(COD) 장치: [회사 소유 장치 등록](enroll-company-owned-devices.md)에서는 회사 소유 장치를 등록하는 다양한 플랫폼별 방법에 대한 지침을 제공합니다.

### <a name="managing-intune-subscriptions-associated-with-configuration-manager"></a>Configuration Manager와 연결된 Intune 구독 관리
 Microsoft Intune(평가판 구독 또는 유료 구독)을 Configuration Manager에 추가하고 다른 Intune 구독으로 전환해야 하는 경우 새 구독을 추가하려면 먼저 Configuration Manager 콘솔에서 **Microsoft Intune 구독** 및 **서비스 연결 지점**을 모두 삭제해야 합니다.

#### <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Configuration Manager에서 Intune 구독을 삭제하는 방법

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **개요**를 확장하고 **클라우드 서비스**로 이동하고 **Microsoft Intune 구독**을 클릭합니다.

3.  **Microsoft Intune 구독**을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다. **Microsoft Intune 구독**

    > [!IMPORTANT]
    >  Intune 평가판 구독을 위해 구성된 사용자 등록, 정책 및 앱 배포를 포함하는 모든 콘텐츠는 손실됩니다.

4.  **관리** 작업 영역에서 **개요**를 확장하고 **사이트 구성**으로 이동하고 **서버 및 사이트 시스템 역할**을 클릭합니다.

5.  **서비스 연결 지점** 역할을 호스트하는 서버를 선택합니다.

6.  **사이트 시스템 역할** 목록에서 **서비스 연결 지점**을 선택한 후 리본 메뉴에서 **역할 제거**를 클릭합니다. 역할을 제거할 것을 확인합니다. 서비스 연결 지점이 삭제됩니다.

7.  이제 새 서비스 연결 지점을 만들고, 새 Intune 구독을 Configuration Manager에 추가하고, Configuration Manager를 MDM 기관으로 설정할 수 있습니다.



<!--HONumber=Nov16_HO1-->


