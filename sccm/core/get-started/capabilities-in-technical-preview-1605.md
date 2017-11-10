---
title: "기술 미리 보기 1605의 기능"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager용 Technical Preview 버전 1605에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bafd028-1923-4463-9e3e-ee41bc0c437b
caps.latest.revision: "36"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8286b8d0f35717d1b1453fa76208c1539f3ffda4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1605-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1605의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1605에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.  

 **이 Technical Preview의 알려진 문제:**  

-   Technical Preview 1605에서는 설치 후 관리 지점의 속성을 업데이트하면 콘솔이 강제로 닫히는 콘솔 오류가 발생할 수 있습니다.  이 경우 관리 지점을 제거한 다음 원하는 설정을 사용하여 관리 지점을 다시 설치합니다. 또는 Technical Preview 1605를 설치하기 전에 관리 지점을 수정할 수 있습니다.  

-   Technical Preview 1604에서 비즈니스용 Windows 스토어 기능을 사용하다가 Technical Preview 1605로 업그레이드하는 경우 더 이상 온보딩 데이터를 볼 수 없습니다. 다른 모든 기능은 계속 작동합니다. Technical Preview 1604에 등록한 경우 Technical Preview 1605 설치 후에도 등록된 상태를 유지하므로 추가 조치를 취할 필요가 없습니다.  

 **다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

##  <a name="BKMK_PerAppVPN"></a> Windows 10 장치를 위한 앱당 VPN  
 Intune에서 Configuration Manager를 사용하여 관리되는 Windows 10 장치의 경우, Configuration Manager 관리 콘솔을 통해 구성한 VPN 연결을 자동으로 여는 앱 목록을 추가할 수 있습니다. 이러한 앱에 대한 VPN 트래픽을 제한하는 옵션이 있거나 VPN 연결을 통한 모든 트래픽을 계속 허용할 수 있습니다.  

 **요구 사항**:  

-   Configuration Manager와 Intune  

-   하나 이상의 장치에 배포된 Windows 10 VPN 프로필  

##  <a name="BKMK_InstallSU"></a> 소프트웨어 업데이트 설치 작업 순서의 향상 기능  
 소프트웨어 업데이트 설치 작업 순서가 다음과 같이 향상되었습니다.  

-   새 작업 순서 변수인 SMSTSSoftwareUpdateScanTimeout을 사용하여 소프트웨어 업데이트 설치 작업 순서 단계 중에 소프트웨어 업데이트 검사의 시간 제한을 제어할 수 있습니다. 기본값은 30분입니다.  

-   로깅 기능이 향상되었습니다. smsts.log 로그 파일에 소프트웨어 업데이트 설치 프로세스 중 문제를 해결할 수 있도록 하는 다른 로그 파일을 참조하는 새로운 로그 항목이 포함됩니다.  

##  <a name="BKMK_PrepareConfigMgrClient"></a> ConfigMgr 클라이언트 캡처 준비 작업 순서 단계의 향상 기능  
 이제 ConfigMgr 클라이언트 준비 단계에서 주요 정보만 제거하는 것이 아니라 Configuration Manager 클라이언트를 완전히 제거합니다. 작업 순서에서 운영 체제 캡처 이미지를 배포할 때마다 새 Configuration Manager 클라이언트가 설치됩니다.  

##  <a name="BKMK_Grace"></a> 필수 응용 프로그램 배포를 위한 유예 기간  
 간혹 구성한 마감일 이후에도 필수 응용 프로그램 배포를 설치할 수 있는 시간을 사용자에게 더 제공하고 싶을 경우가 있습니다. 예를 들어 최종 사용자가 휴가에서 막 돌아온 경우 지연된 응용 프로그램 배포를 설치하는 데 너무 오래 기다려야 할 수 있습니다. 하지만 언제든지 응용 프로그램을 즉시 설치할 수 있습니다.  

 이 문제를 해결하기 위해 이제 Configuration Manager 클라이언트 설정을 컬렉션에 배포하여 **유예 기간**을 정의할 수 있습니다.  

 유예 기간을 구성하려면 다음 작업을 수행합니다.  

1.  클라이언트 설정의 **컴퓨터 에이전트** 페이지에서 새 속성, **배포 최종 기한 이후 적용 유예 기간(시간)**을 **1**시간에서 **120**시간 사이의 값으로 구성합니다.  

2.  새 응용 프로그램 배포 또는 기존 배포 속성의 **일정** 페이지에서, 클라이언트 설정에 정의된 유예 기간까지 **이 배포의 적용을 사용자 기본 설정에 따라 연기합니다.** 확인란을 선택합니다.  

     이 확인란이 선택되고 클라이언트 설정도 배포된 대상 장치의 모든 배포에서 이 유예 기간을 사용합니다.  

 이 릴리스에서는 구성하는 유예 기간을 클라이언트 장치에서 사용하지 않습니다. 유예 기간을 구성하고 확인란을 선택하면 마감일 이후 사용자가 구성한 첫 번째 업무 외 시간에서 응용 프로그램이 설치됩니다.  

 소프트웨어 업데이트 배포 마법사, 자동 배포 규칙 마법사 및 속성 페이지에 비슷한 옵션이 추가되었습니다. 하지만 이 Technical Preview에서는 현재 이러한 옵션이 구현되지 않습니다.  

##  <a name="BKMK_Remote"></a> 원격 장치 작업을 위한 새로운 환경  
 Configuration Manager 콘솔에서 원격 장치 작업을 수행하기 위한 환경이 개선되었습니다.  
이제 **자산 및 준수** 작업 영역에서 액세스되는 **원격 장치 작업** 메뉴에서 **사용 중지/초기화**, **암호 다시 설정**, **원격 잠금** 및 **활성화 잠금 바이패스** 등의 일반 작업을 찾을 수 있습니다.  

 ![새 원격 장치 작업 스크린샷](media/New-Remote-Device-Actions.png)  

 다음 위치에서 이러한 각 작업에 대한 상태를 찾을 수 있습니다.  

-   **장치** 노드에서 장치를 선택할 때의 세부 정보 창  

-   장치의 **속성** 페이지  

-   **장치** 노드의 기본 페이지(일부 열이 기본적으로 표시됨)  

 iOS 활성화 잠금 바이패스에 대한 자세한 내용은 [Configuration Manager의 활성화 잠금 바이패스를 사용하여 iOS 장치 보호](/sccm/mdm/deploy-use/manage-ios-activation-lock), 특히 **Configuration Manager Technical Preview의 활성화 잠금 무시에 대해 현재 알려진 문제** 섹션을 참조하세요.  

##  <a name="BKMK_WSFB"></a> 비즈니스용 Windows 스토어 앱  
 [비즈니스용 Windows 스토어](https://www.microsoft.com/business-store)에서 조직을 위한 앱을 찾아서 개별적으로 또는 대량으로 구매할 수 있습니다. 예를 들어 스토어를 Configuration Manager에 연결하여 Configuration Manager 콘솔에서 대량 구매 앱을 관리할 수 있습니다.  

-   구매한 앱 목록을 Configuration Manager와 동기화할 수 있습니다.  

-   동기화되는 앱은 Configuration Manager 콘솔에 표시되며 다른 앱과 유사하게 해당 앱을 배포할 수 있습니다.  

-   Configuration Manager가 24시간마다 스토어에서 앱 라이선스 정보를 다운로드하여 Configuration Manager 콘솔에서 이 정보를 검토할 수 있습니다.  

 1604 Technical Preview 릴리스에서는 Configuration Manager 콘솔에서 비즈니스용 Windows 스토어의 앱을 동기화하고 볼 수 있습니다. 이 릴리스에는 동기화된 스토어 앱에서 Configuration Manager 응용 프로그램을 만들고 배포하는 기능이 추가되었습니다.  

### <a name="set-up-windows-store-for-business-synchronization"></a>비즈니스용 Windows 스토어 동기화 설정  

1.  Azure Active Directory에서 Configuration Manager를 "웹 응용 프로그램 및/또는 웹 API" 관리 도구로 등록합니다. 이렇게 하면 나중에 필요한 클라이언트 ID가 제공됩니다.  

    1.  [https://manage.windowsazure.com](https://manage.windowsazure.com)의 Active Directory 노드에서 Azure Active Directory를 선택한 후 **응용 프로그램** > **추가**를 클릭합니다.  

    2.  **조직에서 개발 중인 응용 프로그램 추가**를 클릭합니다.  

    3.  응용 프로그램의 이름을 입력하고, **웹 응용 프로그램** 및/또는 **웹 API**를 선택한 후 **다음** 화살표를 클릭합니다.  

    4.  **로그온 URL** 및 **앱 ID URI** 모두에 대해 동일한 URL을 입력합니다. URL은 어떤 문자열이든 될 수 있으며, 실제 주소로 확인할 필요는 없습니다. 예를 들어 **https://&lt;yourdomain>/sccm**을 입력할 수 있습니다.  

    5.  마법사를 완료합니다.  

2.  Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.  

    1.  방금 만든 응용 프로그램을 강조 표시하고 **구성**을 클릭합니다.  

    2.  **키** 아래의 목록에서 기간을 선택하고 **저장**을 클릭합니다. 그러면 새 클라이언트 키가 생성됩니다. 비즈니스용 Windows 스토어를 Configuration Manager에 성공적으로 등록할 때까지 이 페이지에서 이동하지 마세요.  

3.  비즈니스용 Windows 스토어에서 Configuration Manager를 저장소 관리 도구로 구성합니다.  

    1.  [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/managementtools)를 열고 메시지가 표시되면 로그인합니다.  

    2.  필요한 경우 사용 약관에 동의합니다.  

    3.  **관리 도구**에서 **관리 도구 추가**를 클릭합니다.  

    4.  **이름별 도구 검색**에서 이전에 AAD에서 만든 응용 프로그램의 이름을 입력한 후 **추가**를 클릭합니다.  

    5.  방금 가져온 응용 프로그램 옆에 있는 **활성화**를 클릭합니다.  

    6.  **오프라인 라이선스 앱 표시** 마법사에서, 오프라인 라이선스 응용 프로그램을 구매할 수 있도록 허용하려면 **예**를 클릭합니다.  

4.  비즈니스용 Windows 스토어에서 앱을 하나 이상 구매합니다.  

5.  Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장한 후 **비즈니스용 Windows 스토어**를 클릭합니다.  

6.  **홈** 탭의 **만들기** 그룹에서 **비즈니스용 Windows 스토어 계정 추가**를 클릭합니다.  

7.  Azure Active Directory의 테넌트 ID, 클라이언트 ID 및 클라이언트 키를 추가한 후 마법사를 완료합니다.  

8.  완료한 후에는 Configuration Manager 콘솔의 **비즈니스용 Windows 스토어 계정** 목록에서 구성한 계정이 표시됩니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료해 보고 어떻게 작동하는지 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) 페이지에서 사용자 의견 양식을 사용하여 알려주세요.  

 비즈니스용 Windows 스토어 사용이 허가된 오프라인 앱에서 Configuration Manager 응용 프로그램을 만들고 배포합니다.  

1.  Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.  

2.  배포하려는 앱을 선택한 후 **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 클릭합니다.  

 비즈니스용 Windows 스토어 앱을 포함하여 Configuration Manager 응용 프로그램이 만들어집니다. 그런 다음 이 응용 프로그램을 원하는 Configuration Manager 응용 프로그램으로 배포 및 모니터링할 수 있습니다.  

> [!IMPORTANT]  
>  사용이 허가된 오프라인 앱에서 단일 배포 유형으로 Configuration Manager 응용 프로그램을 만들 경우 MDM 관리 장치 및 Configuration Manager 클라이언트 관리 장치에도 이 응용 프로그램을 배포할 수 있습니다. 여러 배포 유형으로 앱을 배포하려고 하면 설치에 실패합니다.  
>   
>  현재 Configuration Manager에서 사용이 허가된 온라인 앱을 배포할 수 없습니다.  

##  <a name="BKMK_VPP2"></a> 대량 구매 앱의 일반적인 향상 기능  

-   이 릴리스에서는 비즈니스용 Windows 스토어와 iOS App Store의 대량 구매 앱이 동일한 보기, **스토어 앱에 대한 라이선스 정보**로 통합되었습니다.  

-   iOS 대량 구매 앱의 경우 응용 프로그램 만들기 마법사의 **iOS용 앱 패키지 브라우저** 대화 상자에서 Apple Volume Purchase Program 탭이 제거되었습니다. iOS용 대량 구매 앱을 만들려면 다음 단계를 수행합니다.  

    1.  1.  Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.  

    2.  2.  배포하려는 앱을 선택한 후 **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 클릭합니다.  

-   Configuration Manager 콘솔에서 대량 구매 앱의 Apple VPP 토큰을 가져오고 업로드하는 데 사용하는 위치가 변경되었습니다. 이제 **클라우드 서비스** > **Apple Volume Purchase Program 토큰** 노드의 **관리자** 작업 영역에서 이 작업을 수행할 수 있습니다.  

##  <a name="BKMK_VPP"></a> EDP(엔터프라이즈 데이터 보호)  
 보호된 앱, EDP 보호 수준 및 네트워크에서 엔터프라이즈 데이터를 찾는 방법을 선택하는 항목을 포함하여 EDP(엔터프라이즈 데이터 보호) 정책을 배포할 수 있는 구성 항목을 만들 수 있습니다. EDP에 대한 자세한 내용은 다음 항목을 참조하세요.  

-   [EDP(엔터프라이즈 데이터 보호)를 사용한 엔터프라이즈 데이터 보호](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)  

-   [System Center Configuration Manager를 사용하여 EDP(엔터프라이즈 데이터 보호) 정책 만들기 및 배포](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-sccm)  

##  <a name="BKMK_End"></a> 최종 사용자가 회사 포털에서 앱을 설치할 수 있습니다.  
 System Center Configuration Manager 버전 1511에 온-프레미스 MDM이 도입되었습니다. 이전 버전에서는 온-프레미스 MDM 관리 장치에 대해 **필수** 설치 배포 용도로 MDM 관리 Windows 10 장치에 응용 프로그램을 배포할 수 있었습니다.  

 이 릴리스에서는 이제 온-프레미스 MDM 관리 Windows 10 컴퓨터 사용자에게 **사용 가능** 배포 용도로 앱을 배포할 수 있으며, 사용자가 회사 포털에서 이 앱을 스스로 설치할 수 있습니다.
이 Technical Preview에서 회사 포털이 15분보다 오래 열려 있으면 최종 사용자에게 오류 메시지가 표시됩니다. 문제를 해결하려면 회사 포털을 다시 시작합니다.  

### <a name="before-you-start"></a>시작하기 전에  

#### <a name="server-prerequisites"></a>서버 필수 구성 요소  

-   .NET 4.5 이상(다시 시작 필요)  

-   PowerShell 3.0 구성 스크립트(다시 시작 필요)  

#### <a name="client-prerequisites"></a>클라이언트 필수 조건  

-   Windows 10 Desktop 1511(OS 빌드 10586.218) 이상  

#### <a name="general-prerequisites"></a>일반 전제 조건  

-   [온-프레미스 모바일 장치 관리에 대한 준비 단계](https://technet.microsoft.com/library/mt613153.aspx)를 완료하고 [장치를 등록](https://technet.microsoft.com/library/mt627870.aspx)해야 합니다.  

-   회사 포털 사용 시 최상의 응용 프로그램 설치 환경을 위해 Configuration Manager에 Microsoft Intune에 대한 활성 연결이 있어야 합니다.  

-   대량 등록 옵션을 선택할 경우 이 시나리오를 수행하기 전에 등록된 장치에 대한 사용자 장치 선호도를 구성합니다.  

### <a name="configuration-steps"></a>구성 단계  

#### <a name="install-the-application-catalog-roles-and-enable-mobile-device-management-support"></a>응용 프로그램 카탈로그 역할 설치 및 모바일 장치 관리 지원 활성화  

1.  응용 프로그램 카탈로그 웹 서비스 및 웹 사이트 역할 추가  

    1.  **HTTPS 모드** 및 **모바일 장치가 이 응용 프로그램 카탈로그 웹 서비스 지점을 사용하도록 허용** 옵션을 선택합니다.  

    2.  이 Technical Preview의 제한 사항:  

        -   모바일 장치의 연결을 허용하는 옵션을 선택하기 전에 모든 기존 응용 프로그램 카탈로그 역할을 제거해야 합니다.  

        -   하나의 응용 프로그램 카탈로그 역할 집합만 있어야 하며 그 역할은 등록 지점 및 등록 프록시 지점 역할과 같은 사이트 시스템에 함께 배치해야 합니다.  

2.  다음 구성 요소가 Configuration Manager 콘솔의 구성 요소 상태 노드에서 작동하는지 확인합니다.  

    -   **SMS_AWEBSVC_CONTROL_MANAGER**  

    -   **SMS_DMAPPSVC_CONTROL_MANAGER**  

    -   **SMS_DMCONTENTSVC_CONTROL_MANAGER**  

    -   **SMS_PORTALWEB_CONTROL_MANAGER**  

### <a name="configure-boundaries"></a>경계 구성  
 인트라넷 전용 배포 지점에 대한 필수 경계를 구성합니다.  

> [!NOTE]  
>  이번에는 모바일 장치 관리에서 IPv4 범위 경계만 지원됩니다.  

### <a name="deploy-the-company-portal-application-and-configuration"></a>회사 포털 응용 프로그램 및 구성 배포  

1.  Technical Preview에 포함된 구성 스크립트를 사용하여 다음과 같이 회사 포털 배포 및 구성을 준비합니다.  

    1.  관리자 권한 PowerShell 명령 창을 엽니다.  

    2.  **set-executionPolicy RemoteSigned** 실행  

    3.  **&lt;SCCM 설치 디렉터리\>\cd.latest\SMSSETUP\TOOLS\MDM** 폴더에서 **.\ConfigurationScript.ps1** 실행  

     구성 스크립트는 다음을 수행합니다.  

    1.  같은 폴더에 있는 **CompanyPortalOnPremisesMDM.appx**를 사용하여 Windows 앱 패키지 배포 유형으로 Configuration Manager 응용 프로그램을 만듭니다.  

    2.  회사 포털을 구성하는 구성 항목 및 구성 기준을 만듭니다.  

    3.  구성 기준과 응용 프로그램을 모두 배포하고 모든 배포 지점에 응용 프로그램을 추가합니다.  

    > [!NOTE]  
    >  응용 프로그램 카탈로그 역할을 기본 사이트와 함께 배치하지 않은 경우 다음 작업을 수행합니다.  
    >   
    >  -   **자산 및 준수** 작업 영역에서 **OnPremMDM 포털 구성 CI - 서버 url** 구성 항목을 찾습니다.  
    > -   **준수 규칙** 값을 응용 프로그램 카탈로그 역할이 있는 사이트 시스템의 정규화된 도메인 이름으로 변경합니다.  

2.  회사 포털 응용 프로그램 및 해당 구성을 모두 배포한 후 Configuration Manager 콘솔의 **배포** 섹션을 사용하여 응용 프로그램 및 구성 기준이 지정된 장치와 호환되는지 확인합니다. 회사 포털은 장치의 시작 메뉴에 **회사 포털(Technical Preview)**로 표시됩니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료해 보고 어떻게 작동하는지 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) 페이지에서 사용자 의견 양식을 사용하여 알려주세요.  

1.  배포 용도가 **사용 가능**인 사용자 컬렉션에 지원되는 배포 유형으로 여러 응용 프로그램을 배포합니다. 이 Technical Preview의 경우 관리자 승인이 필요한 응용 프로그램이 지원되지 않으며 회사 포털에 표시되지 않습니다.  

2.  사용자가 회사 포털에서 앱을 검색한 후 설치할 수 있습니다.  

     회사 포털을 연 후 **System Center Configuration Manager**라는 이름의 인증 대화 상자가 나타나면 사용자의 Active Directory 자격 증명(user@domain 또는 domain\user 중 하나)을 지정하여 로그인합니다.  

##  <a name="BKMK_SW1"></a> 소프트웨어 센터의 업데이트 및 운영 체제에 대한 새로운 탭  
 이 릴리스에서는 소프트웨어 센터 응용 프로그램의 레이아웃을 개선하기 위해 다음과 같이 변경되었습니다.  

-   **응용 프로그램** 탭이 세 개의 별도 탭(**업데이트**, **운영 체제**(이전에는 둘 다 **필터** 목록에 있었음) 및 **응용 프로그램**)으로 분리되었습니다.  

##  <a name="BKMK_ServerGroups"></a> 서버 그룹 제공  
 System Center Configuration Manager용 Technical Preview 버전 1511은 컬렉션을 만드는 기능을 포함하고 있으며 여기서 컬렉션의 모든 장치는 서버 그룹을 구성합니다. 서버 그룹에 소프트웨어 업데이트를 배포할 때 사용할 서버 그룹 설정을 구성하고, 지정된 시간에 업데이트되는 컴퓨터의 백분율을 제어할 수 있으며, 사용자 지정 작업을 실행하도록 배포 전/배포 후 PowerShell 스크립트를 구성할 수 있습니다.  

 System Center Configuration Manager용 Technical Preview 버전 1605에서는 정의하는 특정 순서대로 서버 그룹의 컴퓨터를 업데이트하는 기능이 추가되고, 서버 그룹의 컴퓨터 상태를 볼 수 있도록 모니터링 기능이 향상되었으며, 클라이언트가 소프트웨어 업데이트를 설치하지 못하거나 다른 클라이언트가 해당 소프트웨어 업데이트를 설치하지 않도록 하는 경우에 유용한 배포 잠금을 제거하는 기능이 제공됩니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료해 보고 어떻게 작동하는지 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) 페이지에서 사용자 의견 양식을 사용하여 알려주세요.  

-   서버 그룹을 나타내는 컬렉션을 만들 수 있습니다. 이 테스트를 위해 이 컬렉션의 컴퓨터 2대를 포함하도록 구성원 자격 수집 규칙을 구성할 수 있습니다.   

-   서버 그룹의 컴퓨터가 컬렉션의 서버 그룹 설정에 따라 특정 순서대로 소프트웨어 업데이트를 설치하도록 지정할 수 있습니다. 배포 전/배포 후 스크립트를 지정하려면 아래 절차의 샘플 스크립트를 사용합니다.  

-   이 컬렉션에 소프트웨어 업데이트를 배포할 수 있습니다. C:\temp의 start.txt 및 end.txt 파일(샘플 스크립트에서 생성됨)을 검토하여 서버 그룹 내 컴퓨터의 배포 시작 시간과 종료 시간을 확인합니다. 자세한 내용은 UpdatesDeployment.log 파일을 검토하세요.  

#### <a name="to-create-a-collection-for-a-server-group"></a>서버 그룹의 컬렉션을 만들려면  

1.  서버 그룹의 컴퓨터를 포함하는 [장치 컬렉션을 만듭니다](https://technet.microsoft.com/library/gg712295.aspx).  

2.  **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 클릭하고 서버 그룹에서 컴퓨터를 포함하는 컬렉션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  

3.  **일반** 탭에서 **모든 장치가 동일한 서버 그룹에 속함**을 선택한 다음 **설정**을 클릭합니다.  

4.  **서버 그룹 설정** 페이지에서 다음 설정 중 하나를 지정합니다.  

    -   **일정 비율의 컴퓨터가 동시에 업데이트되도록 허용**: 특정 비율의 클라이언트만 한 번에 업데이트되도록 지정합니다. 예를 들어 컬렉션에 10개의 클라이언트가 있고 클라이언트의 30%를 동시에 업데이트하도록 컬렉션을 구성하는 경우에는 지정된 시간에 3개의 클라이언트만 소프트웨어 업데이트를 설치합니다.  

    -   **여러 컴퓨터가 동시에 업데이트되도록 허용**: 특정 수의 클라이언트만 한 번에 업데이트되도록 지정합니다.  

    -   **유지 관리 순서 지정**: 컬렉션의 클라이언트가 구성 순서대로 한 번에 하나씩 업데이트되도록 지정합니다. 클라이언트는 목록에서 앞의 클라이언트가 해당 소프트웨어 업데이트 설치를 완료하고 난 다음에야 소프트웨어 업데이트를 설치합니다.  

5.  배포 전(노드 드레이닝) 또는 배포 후(노드 다시 시작) 스크립트 사용 여부를 지정합니다.  

    > [!TIP]  
    >  다음은 텍스트 파일에 현재 시간을 작성하는 배포 전/배포 후 스크립트를 테스트하는 데 사용할 수 있는 예제입니다.  
    >   
    >  **배포 전**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **배포 후**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-group-and-monitor-status"></a>서버 그룹에 소프트웨어 업데이트를 배포하고 상태를 모니터링하려면  

1.  서버 그룹 컬렉션에 [소프트웨어 업데이트를 배포](https://technet.microsoft.com/library/gg712304.aspx)합니다.  

2.  [소프트웨어 업데이트 배포를 모니터링](https://technet.microsoft.com/library/gg712304.aspx)합니다. 클라이언트가 소프트웨어 업데이트 설치 차례를 기다리고 있을 때 소프트웨어 업데이트 배포에 대한 표준 모니터링 보기 외에도 새 상태 설명이 표시됩니다. 이 새 상태는 **잠금 대기 중**이라고 표시됩니다.  

#### <a name="to-clear-the-deployment-locks-for-computers-in-a-server-group"></a>서버 그룹의 컴퓨터에 대한 배포 잠금을 제거하려면  

1.  **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 클릭하고 배포 잠금을 제거할 컬렉션을 클릭합니다.  

2.  **홈** 탭의 **배포** 그룹에서 **서버 그룹 배포 잠금 제거**를 클릭합니다. 클라이언트가 소프트웨어 업데이트를 설치하지 못한 경우와 다른 클라이언트가 해당 소프트웨어 업데이트를 설치하지 못하도록 하는 경우 배포 잠금을 수동으로 제거할 수 있습니다.  

##  <a name="BKMK_ATP"></a> Windows Defender Advanced Threat Protection 서비스에 대한 지원  
 Windows Defender ATP(Advanced Threat Protection)는 엔터프라이즈의 검색, 조사 및 네트워크에 대한 고급 공격에 대응하는 데 도움이 되는 새로운 서비스입니다. [Windows Defender ATP](https://blogs.windows.com/windowsexperience/2016/03/01/announcing-windows-defender-advanced-threat-protection)에 대해 자세히 알아봅니다. Configuration Manager는 관리되는 Windows 10 Anniversary Edition 클라이언트 장치를 등록하고 모니터링하는 데 도움이 될 수 있습니다.  

### <a name="try-it-now"></a>지금 직접 사용해 보세요!  
 다음 작업을 완료해 보고 어떻게 작동하는지 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) 페이지에서 사용자 의견 양식을 사용하여 알려주세요.  

-   Windows Defender ATP(Advanced Threat Protection) 온라인 서비스에 장치 온보딩  

-   관리되는 장치에 Windows Defender ATP 배포 모니터링  

 **전제 조건**  

-   Windows Defender Advanced Threat Protection 온라인 서비스에 대한 구독  

-   Windows 10 Anniversary Edition(빌드 14328 이상)을 실행하는 클라이언트  

-   클라이언트 온보딩 구성 파일 만들기  

    ##### <a name="how-to-create-an-onboarding-configuration-file"></a>온보딩 구성 파일을 만드는 방법  

    1.  Windows Defender ATP 온라인 서비스에 로그온합니다.  

    2.  **클라이언트 온보딩** 메뉴 항목을 클릭합니다.  

    3.  **System Center Configuration Manager**를 선택하고 **패키지 다운로드**를 클릭합니다.  

    4.  압축된 보관 파일(.zip)을 다운로드하고 압축을 풉니다.  


##### <a name="onboard-devices-for-windows-defender-atp"></a>Windows Defender ATP 장치 온보딩  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **Endpoint Protection** > **Windows Defender ATP 정책**으로 이동하고 **Windows Defender ATP 정책 만들기**를 클릭합니다. Windows Defender ATP 정책 마법사가 열립니다.  

2.  Windows Defender ATP 정책의 **이름** 및 **설명**을 입력하고 **온보딩**을 선택합니다. 다음을 클릭합니다.  

3.  조직의 Windows Defender ATP 클라우드 서비스 테넌트에서 제공하는 구성 파일을 **찾습니다**. **다음**을 클릭합니다.  

4.  분석을 위해 관리되는 장치에서 수집 및 공유되는 파일 샘플을 지정합니다.  

    -   **없음** – 분석을 위해 수집된 샘플 파일이 없습니다.  

    -   **이식 가능한 실행 파일** – 프로그램 파일(.exe), 동적 라이브러리 링크 파일(.dll), 글꼴 파일 등과 사이버 공격에서 악용될 수 있는 유사한 파일이 분석을 위해 수집되고 공유됩니다.  

     **다음**을 클릭합니다.  

5.  요약을 검토하고 마법사를 완료합니다.  

6.  이제 **배포**를 클릭하면 관리되는 클라이언트 컴퓨터에 Windows Defender ATP 정책을 배포할 수 있습니다.  

##### <a name="monitor-windows-defender-atp"></a>Windows Defender ATP 모니터링  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **보안**으로 이동한 다음 **Windows Defender ATP**를 클릭합니다.  

2.  Windows Defender Advanced Threat Protection 대시보드를 검토합니다.  

    -   **Windows Defender 에이전트 배포 상태** – 활성 Windows Defender ATP 정책이 온보딩된 적합한 관리되는 클라이언트 컴퓨터 수 및 백분율  

    -   **Windows Defender ATP 에이전트 상태** – Windows Defender ATP 에이전트에 대한 상태를 보고하는 컴퓨터 클라이언트의 백분율  

        -   **정상** - 정상적으로 작동  

        -   **비활성** - 기간 동안 서비스로 보내는 데이터가 없음  

        -   **에이전트 상태** - Windows에서 에이전트에 대한 시스템 서비스가 실행되지 않음  

        -   **온보딩되지 않음** - 정책이 적용되었지만 에이전트가 온보딩된 정책을 보고하지 않음  

##  <a name="BKMK_DHA"></a> 온-프레미스 장치 상태 증명  
 이제 온-프레미스 인프라를 사용하여 통신하도록 Windows 10 장치에 대한 상태 증명을 구성할 수 있습니다. 관리자는 보고를 클라우드를 통해 또는 온-프레미스 리소스를 통해 수행할지 여부를 지정할 수 있습니다. 상태 증명 보고를 위해 온-프레미스를 선택한 경우 서비스에 대해 URL을 지정할 수 있습니다. 이를 통해 인터넷에 액세스할 수 없는 클라이언트 PC에서 상태 증명을 사용하여 장치를 활성화하고 관리할 수 있습니다.  

### <a name="enable-health-attestation-for-on-premises-devices"></a>온-프레미스 장치에 상태 증명 사용  
 1605에서는 Technical Preview 1604 버전에서 발견된 몇 가지 버그가 수정되었습니다.  사용해 보려면 클라이언트 에이전트 설정을 사용하여 온-프레미스 상태 증명 서비스를 구성합니다.  

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**으로 이동한 후 **온-프레미스 정상 증명 서비스 사용**을 **예**로 설정합니다.  

2.  **온-프레미스 상태 증명 서비스 URL**을 지정하고 **확인**을 클릭합니다.  

##  <a name="BKMK_RestartOptions"></a> 소프트웨어 업데이트 설치 후 Windows 10 클라이언트의 새로운 다시 시작 옵션  
 Configuration Manager를 사용하여 다시 시작이 필요한 소프트웨어 업데이트를 배포하고 컴퓨터에 설치한 경우 다시 시작 보류가 예약되고 다시 시작 대화 상자가 표시됩니다. 현재 Windows 8 이상에서 다시 시작 대화 상자에서가 아니라 Windows 전원 옵션을 사용하여 컴퓨터를 종료하거나 다시 시작하는 경우, 컴퓨터를 다시 시작한 후에도 다시 시작 대화 상자가 계속 남아 있으며 구성된 마감일에 컴퓨터를 다시 시작해야 합니다. 이 Technical Preview에서는 Configuration Manager 소프트웨어 업데이트에 대해 보류 중인 다시 시작이 있으면 언제든지 **업데이트 및 다시 시작**과 **업데이트 및 종료** 옵션을 Windows 10 컴퓨터의 Windows 전원 옵션에서 사용할 수 있습니다. 이러한 옵션 중 하나를 사용한 후 컴퓨터를 다시 시작하면 다시 시작 대화 상자가 표시되지 않습니다.  

##  <a name="BKMK_IMEI"></a> IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언  
 이제 IMEI(International station Mobile Equipment Identity) 번호를 가져와서 회사 소유 장치를 식별할 수 있습니다. 장치 IMEI 번호를 포함한 쉼표로 구분된 값(.csv) 파일을 업로드하거나 장치 정보를 수동으로 입력할 수 있습니다.  또한 iOS 장치의 일련 번호를 가져올 수 있습니다.  가져온 정보에 따라 "회사"로 등록된 장치의 소유권이 설정됩니다.  서비스에 액세스하는 각 사용자는 Intune 라이선스가 여전히 필요합니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료해 보고 어떻게 작동하는지 Microsoft Connect 사이트의 [Configuration Manager 사용자 의견 프로그램](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) 페이지에서 사용자 의견 양식을 사용하여 알려주세요.  

-   .csv 파일에서 IMEI 숫자 집합을 가져옵니다. 각 행에서 세부 정보 필드 앞에 IMEI 번호를 포함할 수 있습니다.  

-   Configuration Manager 콘솔에서 수동으로 IMEI 번호를 가져옵니다.  

-   .csv 파일에서 iOS 일련 번호 집합을 가져옵니다. 마찬가지로 각 행에서 장치의 세부 정보 앞에 번호를 포함할 수 있습니다.  

##### <a name="pre-declare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **회사가 소유한 모든 장치** > **미리 선언된 장치**로 이동한 다음 **미리 선언된 장치 만들기**를 클릭합니다. 미리 선언된 장치 마법사가 열립니다.  

2.  다음과 같이 장치 정보를 추가할 방법을 지정합니다.  

    -   **IMEI 번호 및 세부 정보를 포함하는 .csv 파일 업로드** - 숫자 목록을 업로드하려면 3단계를 참조하세요.  

    -   **수동으로 IMEI 번호 및 세부 정보 추가** - 정보를 수동으로 입력하려면 IMEI 번호 또는 iOS 일련 번호 및 장치의 세부 정보를 입력한 후 4단계를 진행합니다.  

3.  업로드된 파일의 경우 정보가 포함된 .csv 파일을 찾아 회사 소유의 장치를 미리 선언합니다. 파일은 다음 형식이어야 합니다(참조용으로만 제공되는 맨 위 행은 제외).  

    |**IMEI #**|**iOS 일련 번호**|**OS**|**세부 정보**|
    |---|---|---|---|
    |123456789012345||WINDOWS|회사 소유 Windows 장치|
    |123456789012|A0BCD0EFGH0J|IOS|회사 소유 iOS 장치|
    |123456789012346||ANDROID|회사 소유 Android 장치|

     **열:**  

    -   열 1: IMEI 번호 – 각 행에 IMEI 번호 또는 iOS 일련 번호 중 하나가 필요합니다.  

    -   열 2: iOS 일련 번호 - iOS 일련 번호만 미리 선언할 수 있습니다. 다른 장치 플랫폼에는 IMEI 번호를 사용합니다.  

    -   열 3: 장치의 운영 체제(대문자 표시 필수):  

        -   IOS - 모든 iOS 장치  

        -   WINDOWS - Windows Phone, Window 10 Mobile 및 Windows PC 포함  

        -   ANDROID - 모든 Android 장치  

    -   열 4: 세부 정보 – Configuration Manager 콘솔에 표시되는 추가 장치 정보입니다.  

     **다음**을 클릭합니다.  

4.  파일 가져오기 결과를 검토합니다. 이전에 가져온 IMEI 또는 일련 번호의 세부 정보는 새로운 세부 정보로 업데이트됩니다.  **다음**을 클릭하여 계속하거나 **뒤로**를 클릭하여 업데이트된 세부 정보를 유지한 다음 마법사를 완료합니다.  
