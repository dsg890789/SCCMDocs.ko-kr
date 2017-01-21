---
title: "새로운 하이브리드 MDM 기능 | Microsoft 문서"
description: "System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 새 모바일 장치 관리 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 11/18/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
caps.latest.revision: 40
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 9f3088e90c3259adc3c3b9c6873978d1db4dd1d8
ms.openlocfilehash: 05e4a9687d29c5377303afd8b08352a6a77fa58e

---
# <a name="whats-new-in-hybrid-mobile-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 모바일 장치 관리의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 새 MDM(모바일 장치 관리) 기능에 대한 세부 정보를 제공합니다.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Configuration Manager 버전과 호환성  

 이 문서의 각 섹션에서는 세 가지 범주로 하이브리드 기능이 나열되어 있습니다. 각 범주의 기능과 다양한 Configuration Manager 버전 간의 호환성을 확인하려면 다음 지침을 따르세요.  

|기능 범주|설명|
|-|-|
|**Microsoft Intune의 새로운 기능** | 일반적으로 이 범주 아래에 나열된 모든 기능은 Intune 서비스만 필요하고 Configuration Manager의 추가 기능이 필요하지 않으므로 System Center 2012 R2 Configuration Manager 릴리스를 비롯한 모든 Configuration Manager 릴리스에서 사용할 수 있어야 합니다.|
|**Configuration Manager Technical Preview의 새로운 기능**| 이 범주 아래에 나열된 모든 기능은 지정된 Technical Preview 릴리스에서만 사용할 수 있습니다. 이러한 기능을 시험해보려면 기능 설명에 지정된 기술 미리 보기 버전을 설치해야 합니다. 자세한 내용은 [System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md)를 참조하세요.|
|**Configuration Manager(현재 분기)의 새로운 기능**| 이 범주 아래에 나열된 모든 기능은 지정된 버전의 Configuration Manager(현재 분기)(예: 버전 1511 또는 1602)에서만 사용할 수 있습니다. 하이브리드 배포에 이전 버전의 Configuration Manager를 사용하는 경우 기능 설명에 지정된 Configuration Manager(현재 분기) 버전으로 업그레이드해야 합니다. 자세한 내용은 [System Center Configuration Manager 업그레이드](../../core/servers/deploy/install/upgrade-to-configuration-manager.md)를 참조하세요.|

## <a name="new-hybrid-features-in-december-2016"></a>2016년 12월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2016년 12월에 도입될 예정인 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **등록 시의 MFA(Multi-Factor Authentication) 과정이 Azure Portal로 이전됨**

  이전에는 Intune 등록용으로 MFA를 설정하려면 Intune 콘솔 또는 Configuration Manager 콘솔로 이동해야 했습니다. 이제는 이 업데이트된 기능을 통해 Intune 자격 증명을 사용하여 [Microsoft Azure Portal](https://manage.windowsazure.com)에 로그인한 다음 Azure AD를 통해 MFA 설정을 구성할 수 있습니다. 자세한 내용은 [Microsoft Intune용 Multi-Factor Authentication]을 참조하세요(https://aka.ms/mfa_ad).

- **이제 중국에서 Android용 회사 포털 앱 사용 가능**

  이제 중국에서 Android용 회사 포털 앱을 사용할 수 있습니다. 중국에는 Google Play 스토어를 사용할 수 없으므로 Android 장치 사용자는 중국 앱 마켓플레이스에서 앱을 다운로드해야 합니다. 다음 스토어에서 Android용 회사 포털 앱을 다운로드할 수 있습니다.

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

  Android 용 회사 포털 앱은 Google Play 서비스를 사용하여 Microsoft Intune 서비스와 통신합니다. Google Play 서비스는 중국에서 아직 제공되지 않으므로 다음 작업을 수행하는 경우 완료하는 데 최대 8시간이 걸릴 수 있습니다.

  | Configuration Manager 관리 콘솔 | Android용 Intune 회사 포털 앱 | Intune 회사 포털 웹 사이트 |
  |----|----|----|      
  | 사용 중지/초기화(모든 데이터 제거)   | 원격 장치 제거 | 장치 제거(로컬 및 원격) |
  | 사용 중지/초기화(회사 데이터 제거)   | 장치 재설정 | 장치 재설정|
  | 신규 또는 업데이트된 앱 배포 | 사용 가능한 LOB(기간 업무) 앱 설치 | 장치 암호 재설정|
  | 원격 잠금 | | |
  | 암호 재설정 | | |        


## <a name="new-hybrid-features-in-november-2016"></a>2016년 11월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2016년 11월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **Windows 10 장치에 사용할 수 있는 새로운 Microsoft Intune 회사 포털**

  Microsoft에서 새로운 [Windows 10 장치용 회사 포털 앱](https://www.microsoft.com/store/apps/9wzdncrfj3pz)을 출시했습니다. 새로운 Windows 10 유니버설 형식을 활용하는 이 앱은 모든 Windows 10 장치(PC 및 모바일)에서 동일한 업데이트된 사용자 환경을 제공합니다. 이전 회사 포털 앱에서 제공되었던 것과 동일한 기능도 모두 계속 사용할 수 있습니다.

  새로운 앱은 Windows 10 장치에서 SSO(Single Sign-On) 및 인증서 기반 인증과 같은 플랫폼 기능을 활용합니다. 이 앱은 Windows 스토어에서 설치되는 기존 Windows 8.1 회사 포털 및 Windows Phone 8.1 회사 포털의 업그레이드로 제공됩니다. 추가 세부 정보를 확인하려면 [Intune 지원 팀 블로그](http://aka.ms/intunecp_universalapp)를 방문하세요.

  새로운 회사 포털 앱에는 Configuration Manager 콘솔에 **사용 가능**으로 표시되는 비즈니스용 Windows 스토어 응용 프로그램도 표시됩니다.


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

이전에 Configuration Manager Technical Preview 릴리스에서 사용할 수 있었던 다음 기능을 이제 Intune과 Configuration Manager(현재 분기) 버전 1610을 포함하는 하이브리드 배포에서 사용할 수 있습니다.

* [구성 항목에 대한 추가 설정 및 향상된 환경](/sccm/core/plan-design/changes/whats-new-in-version-1610?branch=sccm-1610-release#new-compliance-settings-for-configuration-items)
* [DEP 프로필에 대한 추가 설정](#new-in-configuration-manager-technical-preview-1609)
* [비즈니스용 Windows 스토어의 유료 앱](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Windows 10 VPN 프로필에 대한 네이티브 연결 형식](#new-in-configuration-manager-technical-preview-1609)
* [Intune 준수 차트](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)
* [콘솔의 동기화 정책 요청](/sccm/mdm/deploy-use/sync-intune-device)
* [Windows Defender 구성 설정](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#windows-defender)

Configuration Manager(현재 분기)의 버전 1610에는 다음과 같은 추가 하이브리드 기능도 포함되어 있습니다.

- **등록된 장치 수 증가**

  이제 사용자가 최대 15개의 장치를 등록하도록 설정할 수 있습니다. 이전에는 사용자당 장치가 5대로 제한되었습니다.


- **추가 보안 지원**

  이제는 전체 관리자 권한 외에 다음과 같은 기본 제공 보안 역할도 회사가 소유한 모든 장치 노드의 항목(미리 선언된 장치, iOS 등록 프로필, Windows 등록 프로필 포함)에 대한 모든 권한을 소유합니다.

    - 자산 관리자
    - 회사 리소스 액세스 관리자

  읽기 전용 분석가 역할에는 이러한 Configuration Manager 콘솔 영역에 대한 읽기 전용 권한이 계속 부여됩니다.

- **Windows Information Protection 앱에서 VPN 액세스 자동 트리거**

  Windows Information Protection 주 도메인을 Windows 10 VPN 프로필에 추가할 수 있습니다. 이렇게 하면 모든 관련 앱이 장치에서 실행될 때 VPN 연결을 자동으로 트리거합니다. 이 옵션은 네이티브 연결 유형을 선택할 때만 사용 가능합니다.

- **Windows 10 VPN 프로필에 대한 조건부 액세스**

    이제 Azure Active Directory에 등록된 Windows 10 장치가 Configuration Manager 콘솔에서 작성된 Windows 10 VPN 프로필을 통해 VPN에 액세스하려면 규정을 준수해야 하도록 지정할 수 있습니다. 이렇게 하려면 Windows 10 VPN 프로필의 VPN 프로필 속성과 VPN 프로필 마법사의 인증 방법 페이지에서 새로운 **이 VPN 연결에 조건부 액세스 사용** 확인란을 사용합니다. 이 옵션은 네이티브 연결 유형을 선택할 때만 사용 가능합니다.

    프로필에 대한 조건부 액세스를 사용하도록 설정하는 경우 SSO(Single Sign-On) 인증용으로 별도의 인증서를 지정할 수도 있습니다.

## <a name="new-hybrid-features-in-october-2016"></a>2016년 10월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2016년 10월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **모바일 응용 프로그램 관리에 대한 조건부 액세스**

  Outlook 등의 Intune 모바일 응용 프로그램 관리 정책을 지원하는 앱에서만 액세스할 수 있도록 Exchange Online에 대한 액세스를 제한할 수 있습니다. [이 새로운 기능](/intune/deploy-use/allow-policy-managed-apps-access-to-o365)은 기본 제공 메일 클라이언트 또는 Intune MAM 정책으로 구성되지 않은 다른 앱에 대한 액세스를 차단할 수 있도록 Intune MAM(모바일 앱 관리) 정책과 완벽하게 연결됩니다. 이렇게 하면 사용자가 Intune MAM으로 보호할 수 있는 앱을 사용하여 조직의 데이터에 액세스합니다. Azure Portal을 통해 Intune 모바일 앱 관리를 시작할 수 있습니다. "설정" 블레이드에서 새 조건부 액세스 섹션을 찾습니다.

-   **Android용 Intune 앱 래핑 도구**

  Intune 앱 래핑 도구를 통해 앱이 Intune MAM(모바일 응용 프로그램 관리) 정책을 사용할 수 있도록 설정할 수 있습니다.

- **Intune과 Android 삼성 KNOX Standard 호환성**

  특정 모델의 삼성 Galaxy Ace 휴대폰은 Intune에서 삼성 KNOX Standard 장치로 관리할 수 없습니다. 이러한 장치를 Intune에 등록하면 대신 표준 Android 장치로 관리됩니다.

  영향을 받는 모델 번호는 다음과 같습니다.

  - SM-G313HU
  - SM-G313HY
  - SM-G313M
  - SM-G313MY
  - SM-G313U

  관리자와 최종 사용자가 추가 작업을 수행할 필요는 없습니다. 자세한 내용은 삼성 KNOX 웹 사이트를 참조하세요.

### <a name="new-in-configuration-manager-technical-preview-1610"></a>Configuration Manager Technical Preview 1610의 새로운 기능

Configuration Manager Technical Preview 1610의 2016년 10월에 도입된 새로운 하이브리드 기능은 다음과 같습니다.

- **관리 콘솔에서 정책 동기화 요청**

  장치 자체의 회사 포털 앱에서 동기화를 요청할 필요 없이 Configuration Manager 콘솔에서 등록된 모바일 장치에 대한 정책 동기화를 요청할 수 있습니다. 이 새로운 동작은 원격 장치 작업 메뉴의 **동기화 요청 보내기**로, 장치 노드에서 모바일 장치를 선택할 때 리본에 표시됩니다.

- **Windows Defender 구성 설정**

  이제 Configuration Manager 콘솔에서 구성 항목을 사용하여 Intune에 등록된 Windows 10 컴퓨터에 대한 Windows Defender 클라이언트 설정을 구성할 수 있습니다. 구성 항목 마법사에 **Windows Defender**라는 새로운 설정 그룹이 있습니다. 이 그룹은 Windows 10 버전 1511 이상에서만 지원됩니다.


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

Configuration Manager(현재 분기) 2016년 8월에 도입된 새로운 하이브리드 기능은 없습니다.

## <a name="new-hybrid-features-in-september-2016"></a>2016년 9월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2016년 9월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **Android용 회사 포털에 "알림" 추가**

  홈페이지의 Android용 회사 포털에 새 알림 아이콘이 추가되었습니다. 이 아이콘을 탭하면 장치 비준수, 등록 업데이트, 등록 활성화 등 회사 포털 앱에서 주의가 필요한 모든 항목을 최종 사용자에게 보여 주는 알림 페이지에 액세스할 수 있습니다. iOS 회사 포털 앱에는 이 알림 환경이 이미 있습니다. 새 알림 페이지가 있으므로 장치가 이미 등록되어 있으면 사용자가 회사 포털을 실행하거나 다시 시작할 때마다 회사 액세스 설정 페이지가 표시되지 않습니다. 고유한 최종 사용자 지침을 만든 경우 이 변경 내용을 반영하도록 문서를 업데이트하는 것이 좋습니다. 업데이트된 스크린샷은 [여기](https://aka.ms/androidcpupdate)서 확인할 수 있습니다.

- **iOS 회사 포털 앱에 대한 지원 변경 내용**

  이제 iOS용 Microsoft Intune 회사 포털 앱의 모든 사용자가 최신 버전을 사용해야 합니다. 새 사용자는 최신 버전만 다운로드할 수 있고 현재 사용자는 최신 버전으로 업데이트해야 합니다. 최신 버전에는 iOS 8.0 이상이 필요하므로 장치를 iOS 8.0 이상으로 업데이트한 다음 회사 포털 앱을 최신 버전으로 업데이트할 때까지 이전 iOS 버전을 실행하는 장치는 회사 포털을 사용하거나 등록할 수 없습니다. iOS 8.0 이전 버전을 실행하는 등록된 장치는 Intune 관리 콘솔에서 계속 관리되고 표시됩니다.

- **Windows Phone 8.1 회사 포털 앱에 피드백 단추 추가됨**

  Windows Phone 8.1 회사 포털 앱에서는 최종 사용자가 새 "사용자 의견 보내기" 단추를 사용하여 앱에 대한 피드백을 보낼 수 있습니다. 단추를 찾으려면 회사 포털 앱 화면의 오른쪽 아래에 있는 "3개의 점" 메뉴를 탭한 다음 **사용자 의견 보내기**를 탭합니다. 익명으로 수집된 피드백은 Microsoft에서 사용자의 회사 포털 앱 환경을 개선하는 데 도움이 됩니다.

### <a name="new-in-configuration-manager-technical-preview-1609"></a>Configuration Manager Technical Preview 1609의 새로운 기능

Configuration Manager Technical Preview 1609의 2016년 9월에 도입된 새로운 하이브리드 기능은 다음과 같습니다.

- **구성 항목 설정에 대한 추가 설정 및 향상된 환경**

  Android, iOS 및 Windows에 대한 새 설정이 추가되었으며, 지원되는 플랫폼 페이지에서 선택한 플랫폼에 적용되는 설정만 마법사에 표시됩니다. 자세한 내용은 [TP 1609에서 구성 항목의 새 준수 설정](/sccm/core/get-started/capabilities-in-technical-preview-1609#new-compliance-settings-for-configuration-items)을 참조하세요.

- **DEP 프로필에 대한 추가 설정**

  TouchID, ApplePay 및 확대/축소가 iOS 장치용 DEP 프로필에 구성 가능한 설정으로 추가되었습니다.

- **비즈니스용 Windows 스토어의 유료 앱**

  이제 비즈니스용 Windows 스토어에 유료 및 무료 응용 프로그램을 추가하고 조직의 사용자에게 배포할 수 있습니다. 자세한 내용은 [TP 1609에서 비즈니스용 Windows 스토어의 향상된 기능](/sccm/core/get-started/capabilities-in-technical-preview-1609#enhancements-to-windows-store-for-business-integration-with-configuration-manager)을 참조하세요.

- **Windows 10 VPN 프로필에 대한 네이티브 연결 형식**

  이제 OMA-URI를 사용하지 않고 Configuration Manager 콘솔에서 Microsoft Automatic, IKEv2 및 PPTP 연결 형식을 사용하여 MDM용 Windows 10 VPN 프로필을 만들 수 있습니다.

- **Intune 준수 차트**

  모니터링 작업 영역 아래에 있는 새 차트를 사용하여 전반적인 장치 준수 및 주요 비준수 이유에 대한 간략한 보기를 볼 수 있습니다. 자세한 내용은 [TP 1609의 Intune 준수 차트](/sccm/core/get-started/capabilities-in-technical-preview-1609#intune-compliance-charts)를 참조하세요.

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

2016년 9월에 도입된 다음 새로운 기능은 Microsoft Intune과 Configuration Manager 버전 1606(현재 분기)을 포함하는 하이브리드 배포에서 사용할 수 있습니다.

- **iOS 10 지원**

  모든 iOS 플랫폼을 대상으로 하는 프로필 또는 구성 항목이 있는 경우 해당 항목도 iOS 10에 푸시됩니다. iOS 10을 포함하는 개별 iOS 플랫폼을 프로필 및 구성 항목의 대상으로 지정할 수 있는 Configuration Manager 버전 1606에 대한 업데이트도 릴리스되었습니다. Configuration Manager 관리 콘솔의 **관리 > 개요 > 클라우드 서비스 > 업데이트 및 서비스**에서 업데이트를 설치할 수 있습니다. 업데이트에 대한 자세한 내용은 [http://support.microsoft.com/kb/3192616](http://support.microsoft.com/kb/3192616)에서 확인할 수 있습니다.

## <a name="new-hybrid-features-in-august-2016"></a>2016년 8월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2016년 8월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **회사 포털 앱의 Android 7 지원**

  Android용 Intune 회사 포털 앱은 곧 출시 예정인 모바일 장치용 Android 7.0 운영 체제에 대해 "0일" 지원을 제공합니다.

- **Google에서 Android 7.0 장치의 원격 암호 다시 설정 기능 제거**

  Google은 Android 7.0 장치의 암호를 원격으로 다시 설정하는 IT 관리자와 최종 사용자의 기능을 제거합니다. 이전에는 IT 관리자가 사용자 암호를 원격으로 다시 설정할 수 있고, 최종 사용자가 회사 포털 웹 사이트에서 자신의 암호를 다시 설정할 수 있었습니다.

- **삼성 KNOX Standard 장치에 대한 허용 및 차단된 앱 정책**

  이제 다음 중 하나를 만들 수 있는 삼성 KNOX Standard 장치에 대한 사용자 지정 정책을 구성할 수 있습니다.

  - 장치에서 실행이 차단된 앱 목록입니다. 차단된 목록에 정의된 앱은 설치된 경우에도 장치에서 활성화할 수 없습니다.
  - 장치의 사용자가 Google Play 스토어에서 설치할 수 있는 앱 목록입니다. 다른 앱은 스토어에서 설치할 수 없습니다.

  이러한 설정은 삼성 KNOX Standard를 실행하는 장치에서만 사용할 수 있습니다. 자세한 내용은 [사용자 지정 정책을 사용하여 삼성 KNOX Standard 장치용 앱 허용 및 차단](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps)을 참조하세요.

- **회사 포털에서 Microsoft로 연결되는 피드백 링크**

   최종 사용자는 회사 포털 웹 사이트에서 페이지 맨 아래에 있는 새 "사용자 의견" 링크를 탭하여 사이트 경험에 대한 피드백을 Microsoft에 보낼 수 있습니다. 익명으로 수집된 피드백은 Microsoft에서 사용자의 회사 포털 웹 사이트 환경을 개선하는 데 도움이 됩니다.

- **최소 iOS Managed Browser 버전이 8.0으로 업데이트됨**

  iOS용 Microsoft Intune Managed Browser 앱이 iOS 8.0 이상을 실행하는 장치를 지원하도록 업데이트되었습니다. iOS 7.1 장치는 기존 Managed Browser 앱을 계속 사용할 수 있지만 새 Managed Browser 기능을 액세스하고 완전히 활용하려면 iOS 8.0 이상으로 업데이트하도록 사용자에게 권장합니다.

### <a name="new-in-configuration-manager-technical-preview"></a>Configuration Manager Technical Preview의 새로운 기능

Configuration Manager Technical Preview 2016년 8월에 도입된 새로운 하이브리드 기능은 없습니다.

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

Configuration Manager(현재 분기) 2016년 8월에 도입된 새로운 하이브리드 기능은 없습니다.

## <a name="new-hybrid-features-in-july-2016"></a>2016년 7월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2016년 7월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **Intune 앱용 Xamarin SDK를 사용할 수 있음**

  Intune 앱 SDK Xamarin 구성 요소를 사용하면 Xamarin으로 빌드된 모바일 iOS 및 Android 앱에서 Intune 모바일 앱 관리 기능을 사용하도록 설정할 수 있습니다. 이 구성 요소는 [Xamarin 스토어](https://components.xamarin.com/view/Microsoft.Intune.MAM) 또는 [Microsoft Intune Github 페이지](https://github.com/msintuneappsdk)에서 찾을 수 있습니다.

- **Windows 장치를 등록할 때 최종 사용자 환경 개선**

  조건부 액세스를 사용하는 경우 Windows 8.1, Windows 10 Desktop 및 Windows 10 Mobile에 대한 등록 단계가 회사 포털 웹 사이트에 설명되어 있습니다. 이제 사용자에게 별도의 **장치 등록** 및 **작업 공간 연결** 단계가 표시되므로 보다 쉽게 장치 상태를 확인하고 WPJ(작업 공간 연결) 오류가 발생할 경우 프로세스를 완료할 수 있습니다. 또한 별도 단계는 IT 관리자의 문제 해결 프로세스를 간소화합니다. 이전에는 최종 사용자가 등록하려 할 때 WPJ를 제외한 모든 등록 단계가 성공한 경우 등록된 장치가 사용자 식별 장치 목록에 표시되지 않아 사용자에게 혼동을 주었습니다.

 - **이제 Windows 10 장치에 전체 초기화를 사용할 수 있음**

    모바일 장치로 등록된 Windows 10 PC 및 노트북을 초기화하여 장치를 하는 랩톱을 공장 설정으로 초기화할 수 있습니다. 자세한 내용은 [원격 초기화를 사용하여 장치를 보호하는 방법](/sccm/mdm/deploy-use/wipe-lock-reset)을 참조하세요.

- **iOS 회사 포털 앱에서 장치 등록 관리자 계정에 대한 변경 내용**

  성능 및 확장성을 개선하기 위해 Intune은 iOS 회사 포털 앱의 내 장치 창에 모든 DEM(장치 등록 관리자) 장치를 더 이상 표시하지 않습니다. 앱을 실행하는 로컬 장치만 표시되며, 회사 포털 앱을 통해 등록된 경우에만 표시됩니다.

  DEM 사용자는 로컬 장치에서 작업을 수행할 수 있지만 다른 등록된 장치의 원격 관리는 Intune 관리 콘솔에서만 수행할 수 있습니다. 또한 Intune은 Apple 장비 등록 프로그램 또는 Apple Configurator 도구에서 DEM 계정 사용을 더 이상 지원하지 않습니다. 두 등록 방법은 모두 공유 iOS 장치에 대한 사용자가 지정되지 않은 등록을 이미 지원합니다.

  공유 장치에 대한 사용자가 지정되지 않은 등록을 사용할 수 없는 경우만 DEM 계정을 사용합니다. 자세한 내용은 [Microsoft Intune에서 장치 등록 관리자를 사용하여 회사 소유 장치 등록](../deploy-use/enroll-devices-with-device-enrollment-manager.md)을 참조하세요.

- **Android 회사 포털 앱에 대한 변경 내용**

  Android 최종 사용자에게 장치에 필요한 인증서가 없다는 오류 메시지가 표시될 경우 "이 문제를 해결하는 방법" 단추를 탭하여 누락된 인증서를 설치하는 단계를 확인할 수 있습니다. 사용자가 단계를 완료해도 "누락된 인증서" 오류 메시지가 추가로 표시되는 경우 IT 관리자에게 문의하고 이 링크를 제공하도록 요청됩니다. 이 링크에는 IT 관리자가 인증서 문제를 해결하는 데 사용할 수 있는 단계가 포함되어 있습니다.

- **테스트용으로 로드된 앱 설치를 등록된 Android 장치로 제한**

  장치가 Android용 Intune 회사 포털 앱을 사용하여 Intune에 등록된 경우가 아니면 Android 장치는 더 이상 회사 포털 웹 사이트를 통해 응용 프로그램을 설치할 수 없습니다.


### <a name="new-in-configuration-manager-technical-preview"></a>Configuration Manager Technical Preview의 새로운 기능

Configuration Manager Technical Preview 2016년 7월에 새로 도입된 하이브리드 기능은 없습니다.

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

이전에 Configuration Manager Technical Preview 릴리스에서 사용할 수 있었던 다음 기능을 이제 Intune과 Configuration Manager(현재 분기) 버전 1606을 포함하는 하이브리드 배포에서 사용할 수 있습니다.

* Configuration Manager 콘솔에서 Windows 10 장치에 대한 비즈니스용 Windows 스토어 앱 찾기, 관리 및 배포([1604](whats-new-hybrid-archive.md#new-in-1604-technical-preview))
*   Android 장치에 대한 SmartLock 설정([1604](whats-new-hybrid-archive.md#new-in-1604-technical-preview))
*   Windows 10 장치를 위한 앱 트리거 VPN([1605](whats-new-hybrid-archive.md#new-in-1605-technical-preview))
*   원격 장치 작업을 위한 새로운 환경([1605](whats-new-hybrid-archive.md#new-in-1605-technical-preview))
*   비즈니스용 Windows 스토어 앱([1605](whats-new-hybrid-archive.md#new-in-1605-technical-preview))
*   대량 구매 앱의 일반적인 향상 기능([1605](whats-new-hybrid-archive.md#new-in-1605-technical-preview))
*   WIP(Windows Information Protection)([1605](whats-new-hybrid-archive.md#new-in-1605-technical-preview))
*   IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언([1605](whats-new-hybrid-archive.md#new-in-1605-technical-preview))
*   컬렉션으로 장치 자동 분류([1606](whats-new-hybrid-archive.md#new-in-1606-technical-preview))

새로운 기능에 대한 자세한 내용은 지정된 기술 미리 보기 릴리스에 대한 설명서를 참조하세요.

## <a name="notices"></a>알림

### <a name="system-center-2012-configuration-sp1-and-system-center-2012-r2-configuration-manager-rtm-support-for-hybrid-mobile-device-management-ending-on-april-10-2017"></a>System Center 2012 Configuration SP1 및 System Center 2012 R2 Configuration Manager(RTM): 하이브리드 모바일 장치 관리에 대한 지원이 2017년 4월 10일에 종료됩니다.

*2017년 1월 11일*

System Center 2012 Configuration Manager SP1 및 System Center 2012 R2 Configuration Manager RTM에 대한 지원이 2016년 7월 12일에 종료됩니다. 그 이후 Microsoft Intune 서비스에 연결하는 이러한 릴리스의 하이브리드 MDM에 대한 지원이 2017년 4월 10일에 종료됩니다. 이 날짜 이후에는 이러한 릴리스에서 하이브리드 MDM의 작동이 중지됩니다. Intune 커넥터가 더 이상 Intune 서비스에 연결되지 않으므로 관리되는 장치는 기본적으로 관리되지 않습니다. 업그레이드가 발생할 때까지 Configuration Manager 데이터(예: 정책 및 응용 프로그램)가 Intune으로 이동하지 않으며 관리되는 장치 데이터가 Configuration Manager로 이동하지 않습니다.

Configuration Manager 2012 SP1 또는 R2 RTM과 함께 하이브리드 배포를 실행하는 경우 2017년 4월 10일 이전에 Configuration Manager(현재 분기)로 업그레이드하거나 Configuration Manager 2012의 지원되는 최신 서비스 팩(R2 SP1 또는 SP2)으로 업그레이드하여 서비스 중단을 방지하는 것이 좋습니다.

추가 리소스:
-   [System Center Configuration Manager(현재 분기)로 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
-   [System Center 2012 R2 Configuration Manager SP1로의 업그레이드 계획](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningR2SP1Upgrade)
-   [System Center 2012 Configuration Manager SP2로의 업그레이드 계획](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningSP2Upgrade)

### <a name="windows-phone-8-company-portal-upload-deprecated"></a>Windows Phone 8 회사 포털 업로드가 사용되지 않음
*2016년 10월 25일*

Windows 8, Windows Phone 8 및 Windows RT에 대한 Intune 지원이 중단되고 Windows Phone 8 회사 포털에 대한 지원이 9월에 종료되므로 서명된 회사 포털 앱을 업로드하는 기능이 Configuration Manager 콘솔에서 제거되었습니다.  이미 등록된 Windows 8, Windows Phone 8 및 Windows RT 장치는 계속 지원되지만 이러한 플랫폼에 추가 장치를 등록할 수 없습니다.


## <a name="see-also"></a>참고 항목

- [과거 하이브리드 MDM 기능](whats-new-hybrid-archive.md)
- [System Center 2012 Configuration Manager의 새로운 MDM 기능](https://technet.microsoft.com/library/mt445560.aspx)



<!--HONumber=Jan17_HO2-->


