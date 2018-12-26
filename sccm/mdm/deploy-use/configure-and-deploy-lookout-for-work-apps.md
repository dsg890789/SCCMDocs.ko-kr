---
title: Lookout for Work 앱 배포
titleSuffix: Configuration Manager
description: Lookout for Work 앱을 구성하고 배포합니다.
ms.date: 05/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 3f62b763-4347-453d-b0a7-1f4a0d1d4105
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 87ad7a768128cb11a1fc361c90a6eccac454a28c
ms.sourcegitcommit: 9cff0702c2cc0f214173b47ec241f7e5a40f84e6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752593"
---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Lookout for Work 앱 구성 및 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Android 및 iOS 디바이스에서 Lookout for Work 앱을 구성하고 배포하는 방법을 설명합니다.



## <a name="android-google-play-store-app"></a>Android(Google Play 스토어 앱)
1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램**을 클릭합니다.  

2.  소프트웨어 배포 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  
    - 유형: **Google Play의 Android용 앱 패키지**를 선택합니다.
    - 위치: Google Play 스토어에서 Lookout for Work 앱 링크를 복사하여 여기에 붙여넣습니다.
    - 게시자: Lookout Mobile Security
    - 이름: Lookout for Work
    - 설명: Lookout에서는 디바이스를 안전하게 유지하도록 모바일 위협에 대한 최상의 보호를 제공합니다. Lookout 앱이 설치되면 앱이 위협으로부터 디바이스를 보호합니다. 위협이 발견되면 사용자와 IT 관리자에게 경고합니다.
    - 관리 범주: 컴퓨터 관리  

    성공적으로 완료되면 애플리케이션 목록에 Lookout for Work 앱이 표시됩니다.  

3.  **홈** 탭의 **배포** 그룹에서 **배포**를 선택하여 Lookout for Work 앱을 사용자에게 배포합니다.   
    >[!IMPORTANT]  
    >Lookout MTP 콘솔의 등록 관리 옵션에 추가된 사용자와 동일한 사용자를 선택해야 합니다.  

    **필수 설치** 옵션을 선택하세요. 이 옵션을 사용하려면 사용자의 디바이스에 Lookout 앱을 설치해야 합니다.  



## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS(Lookout 앱의 엔터프라이즈 서명 버전)

1. iOS 관리가 디바이스에 설정되어 있는지 확인합니다. iOS 관리용으로 디바이스를 설정하는 방법에 대한 자세한 내용은 [iOS 및 Mac 디바이스 관리 설정](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac)을 참조하세요.  

2. Lookout for Work iOS 앱을 다시 서명합니다. Lookout은 iOS App Store 외부에 Lookout for Work iOS 앱을 배포합니다. 앱을 배포하기 전에 iOS 엔터프라이즈 개발자 인증서를 사용하여 앱에 다시 서명해야 합니다. Lookout for Work iOS 앱에 다시 서명하는 방법에 대한 자세한 지침은 Lookout 사이트에서 [Lookout for Work iOS 앱 다시 서명 프로세스](https://personal.support.lookout.com/hc/articles/114094038714)를 참조하세요.  

3. iOS 사용자에 대해 Azure AD(Azure Active Directory) 인증을 사용하도록 설정합니다.
   1.  [Azure Portal의 Azure AD 블레이드](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview)에 로그인하고 앱 등록 페이지로 이동합니다.  
   2.  **Lookout for Work iOS 앱**으로 이름을 지정하고 응용 프로그램 유형으로 **네이티브**를 선택합니다.  
  ![네이티브 클라이언트 앱 옵션을 보여 주는 앱 추가 대화 상자 스크린샷](media/aad-add-app-reg.png)

   3.  이 리디렉션 URI의 경우 다음 형식 `lookoutwork://com.lookout.enterprise.<yourcompanyname>`을 사용하여 `<yourcompanyname>`을 회사 이름으로 대체합니다. 예를 들면 다음과 같습니다. `lookoutwork://com.lookout.enterprise.contoso`
   4. **만들기**를 클릭하여 웹을 만듭니다. 
   5.  새 앱을 열고 **설정을** 클릭하고 추가 리디렉션 URI를 추가합니다. `<originalURI>`가 원래 리디렉션 URI의 URL로 인코딩된 버전인 다음 형식 `companyportal://code/<originalURI>`를 사용합니다. 예를 들면 `companyportal://code/lookoutwork%3A%2F%2Fcom.lookout.enterprise.contoso`
   6.  앱 설정에서 **필요한 권한**으로 이동하여 **추가**를 클릭합니다. 다음의 위임된 권한을 선택합니다.  

       | API  | 사용 권한  |
       |---------|---------|
       | Lookout MTP     | Lookout MTP 액세스         |
       | Microsoft Graph     | 로그인 및 사용자 프로필 읽기        |  

   자세한 내용은 [네이티브 클라이언트 애플리케이션 구성](/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application)을 참조하세요.  


4. Configuration Manager에서 다시 서명된 .ipa 파일을 업로드합니다. 최소 OS 버전을 iOS 8.0 이상으로 설정합니다. 자세한 내용은 [iOS 애플리케이션 만들기](/sccm/apps/get-started/creating-ios-applications)를 참조하세요.   


5. 관리되는 앱 구성 정책을 만듭니다. 자세한 내용은 [모바일 앱 구성 정책을 사용하여 iOS 앱 구성](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies)을 참조하세요.  


6. Lookout for Work 앱 구성을 사용자에게 배포합니다. 자세한 내용은 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.  

  Lookout 콘솔의 등록 관리 옵션에 추가된 사용자와 동일한 사용자를 선택합니다. **필수 설치** 옵션을 선택하세요. 이 옵션을 사용하려면 사용자의 디바이스에 Lookout 앱을 설치해야 합니다.



## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>디바이스에서 배포된 앱을 열 때 수행되는 작업

사용자가 디바이스에서 Lookout for Work를 열 때 앱을 활성화하라는 메시지가 표시됩니다. Azure AD 옵션을 사용하여 로그인하도록 선택해야 합니다. 최종 사용자 흐름을 사용하는 자세한 연습은 다음 아티클에 나와 있습니다.

- [Android 장치에 Lookout for Work를 설치하라는 메시지가 표시됨](/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)

- [Lookout for Work가 Android 장치에서 발견한 위협을 해결해야 함](/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)



## <a name="next-steps"></a>다음 단계
- [준수 정책에서 장치 위협 방지 규칙 사용](enable-device-threat-protection-rule-compliance-policy.md)
