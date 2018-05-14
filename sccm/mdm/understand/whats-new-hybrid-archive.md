---
title: 새로운 기능 하이브리드 MDM 보관
titleSuffix: Configuration Manager
description: System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 과거 모바일 장치 관리 기능의 보관 파일입니다.
ms.date: 02/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 4c27b161-9eb7-4cdd-b469-d8eb27e71aea
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: 88b005ad90625592a4fccfa1d98abfcb8b930a75
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="past-hybrid-features-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune을 사용하는 이전 하이브리드 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 과거 MDM(모바일 장치 관리) 기능에 대한 세부 정보를 제공합니다.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Configuration Manager 버전과 호환성  

 이 문서의 각 섹션에서는 세 가지 범주로 하이브리드 기능이 나열되어 있습니다. 각 범주의 기능과 다양한 Configuration Manager 버전 간의 호환성을 확인하려면 다음 지침을 따르세요.  

|기능 범주|
|-|  
|**Microsoft Intune의 새로운 기능** - 일반적으로 이 범주 아래에 나열된 모든 기능은 Intune 서비스만 필요하고 Configuration Manager의 추가 기능이 필요하지 않으므로 System Center 2012 R2 Configuration Manager 릴리스를 비롯한 모든 Configuration Manager 릴리스에서 사용할 수 있어야 합니다.<br /><br /> **Configuration Manager Technical Preview의 새로운 기능** - 이 범주 아래에 나열된 모든 기능은 지정된 기술 미리 보기 릴리스에서만 사용할 수 있습니다. 이러한 기능을 시험해보려면 기능 설명에 지정된 기술 미리 보기 버전을 설치해야 합니다. 자세한 내용은 [System Center Configuration Manager Technical Preview](../../core/get-started/technical-preview.md)를 참조하세요.<br /><br /> **Configuration Manager(현재 분기)의 새로운 기능** - 이 범주 아래에 나열된 모든 기능은 지정된 버전의 Configuration Manager(현재 분기)(예: 버전 1511 또는 1602)에서만 사용할 수 있습니다. 하이브리드 배포에 이전 버전의 Configuration Manager를 사용하는 경우 기능 설명에 지정된 Configuration Manager(현재 분기) 버전으로 업그레이드해야 합니다. 자세한 내용은 [System Center Configuration Manager 업그레이드](../../core/servers/deploy/install/upgrade-to-configuration-manager.md)를 참조하세요.|  



## <a name="february-2017"></a>2017년 2월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **회사 포털 웹 사이트 현대화**

  회사 포털 웹 사이트는 관리되는 장치가 없는 사용자를 대상으로 하는 앱을 지원합니다. 이 웹 사이트는 새로운 고대비 색 구성표, 동적 그림, 기술 지원팀 연락처 세부 정보 및 기존 관리되는 장치에 대한 정보를 포함하는 “햄버거 메뉴”를 사용하여 다른 Microsoft 제품 및 서비스에 맞춥니다. 방문 페이지는 추천 및 최근에 업데이트된 앱에 대한 슬라이드를 포함하여 사용자가 사용할 수 있는 앱을 강조하도록 재조정됩니다. [UI 업데이트](https://docs.microsoft.com/intune/whats-new-app-ui) 페이지에서 사용 가능한 이전 및 이후 이미지를 찾을 수 있습니다.

- **Windows 장치의 새 MDM 서버 주소**

  Windows 및 Windows Phone 장치 등록을 위한 MDM 서버 주소가 manage.microsoft.com에서 enrollment.manage.microsoft.com으로 변경되었습니다. 사용자에게 Windows 또는 Windows Phone 장치를 등록하는 동안 MDM 서버 주소를 입력하라는 메시지가 표시되면 enrollment.manage.microsoft.com을 사용하라고 알리세요. 이 업데이트에는 또한 EnterpriseEnrollment.contoso.com을 manage.microsoft.com으로 리디렉션하는 DNS의 CNAME이 필요하며, 이 manage.microsoft.com은 EnterpriseEnrollment.contoso.com을 EnterpriseEnrollment-s.manage.microsoft.com으로 리디렉션하는 DNS의 CNAME으로 대체됩니다. 이 변경에 대한 추가 정보는 http://aka.ms/intuneenrollsvrchange에서 찾을 수 있습니다.

### <a name="new-in-configuration-manager-technical-preview-1702"></a>Configuration Manager Technical Preview 1702의 새로운 기능

- **Android for Work 지원**

  이제 Configuration Manager Technical Preview 1702를 사용하여 하이브리드 MDM 환경에서 Android for Work를 통해 Android 장치를 관리할 수 있습니다. 이제 지원되는 Android 장치를 Android for Work 장치로 등록할 수 있으며, Play for Work에서 승인된 앱을 배포할 수 있는 장치에 작업 프로필이 생성됩니다. 이러한 장치에 대한 구성 항목, 준수 정책 및 리소스 액세스 프로필을 구성하고 배포할 수도 있습니다. 자세한 내용은 [Android for Work 지원](/sccm/core/get-started/capabilities-in-technical-preview-1702#android-for-work-support)을 참조하세요.

- **비규격 앱 준수 설정**

  이제 준수 정책에서 Android 및 iOS 앱에 대한 비규격 앱 규칙을 만들 수 있습니다. 장치에 지정한 응용 프로그램이 설치되어 있으면 “비준수”로 표시되며, 적용된 조건부 액세스 정책에 따라 회사 리소스에 액세스할 수 없게 됩니다. 자세한 내용은 [조건부 액세스 장치 준수 정책 개선](/sccm/core/get-started/capabilities-in-technical-preview-1702#conditional-access-device-compliance-policy-improvements)을 참조하세요.

- **PFX 인증서 만들기 및 배포와 S/MIME 지원**

  이제 하이브리드 환경에서 PFX 인증서를 만들고 사용자에게 배포할 수 있습니다. 그러면 사용자가 등록한 장치에서 이 인증서를 S/MIME 메일 암호화 및 암호 해독에 사용할 수 있습니다. 자세한 내용은 [S MIME을 지원하는 PFX 인증서 만들기](/sccm/core/get-started/capabilities-in-technical-preview-1702#create-pfx-certificates-with-s-mime-support)를 참조하세요.

- **추가 iOS 구성 설정에 대한 지원**
   
    이제 구성 항목의 일부로 구성할 수 있는 42개의 추가 iOS 설정이 있습니다. 감독된 iOS 장치에 대해 대부분의 설정(전체 중 35개)이 추가되었습니다. 자세한 내용은 [iOS 장치에 대한 새 준수 설정](/sccm/core/get-started/capabilities-in-technical-preview-1702#new-compliance-settings-for-ios-devices)을 참조하세요.



## <a name="january-2017"></a>2017년 1월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **Android 7.1.1 지원**

  이제 Intune에서 Android 7.1.1을 완벽하게 지원하고 관리합니다.

- **iOS 장치가 비활성 상태이거나 관리 콘솔이 장치와 통신할 수 없는 문제 해결**

  사용자 장치와 Intune의 연결이 끊어진 경우 회사 리소스에 다시 액세스할 수 있도록 지원할 새로운 문제 해결 단계를 제공할 수 있습니다. [장치가 비활성 상태이거나 관리 콘솔이 장치와 통신할 수 없음](https://docs.microsoft.com/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)을 참조하세요.

### <a name="new-in-configuration-manager-technical-preview-1701"></a>Configuration Manager Technical Preview 1701의 새로운 기능

- **Android 및 iOS 버전은 하이브리드 MDM 만들기 마법사에서 대상 지정이 가능하지 않음**

  하이브리드 MDM(모바일 장치 관리)에 대한 Technical Preview 1701부터 Intune 관리 장치에 대한 새 정책 및 프로필을 만들 때 특정 버전의 Android 및 iOS를 대상으로 지정할 필요가 없습니다. 이러한 변경으로 인해 하이브리드 배포에서 새 Configuration Manager 릴리스나 확장 없이 새 Android 및 iOS 버전을 더 빠르게 지원할 수 있습니다. 자세한 내용은 [Android 및 iOS 버전은 만들기 마법사에서 대상 지정이 가능하지 않음](/sccm/core/get-started/capabilities-in-technical-preview-1701#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm)을 참조하세요.



## <a name="december-2016"></a>2016년 12월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **등록 시의 MFA(Multi-Factor Authentication) 과정이 Azure Portal로 이전됨**

  이전에는 Intune 등록용으로 MFA를 설정하려면 Intune 콘솔 또는 Configuration Manager 콘솔로 이동해야 했습니다. 지금은 이 기능이 업데이트되어 [Microsoft Azure Portal](https://manage.windowsazure.com)에 Intune 자격 증명으로 로그인하고 Azure AD를 통해 MFA 설정을 구성합니다. 자세한 내용은 [Microsoft Intune용 Multi-Factor Authentication](https://aka.ms/mfa_ad)을 참조하세요.

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


## <a name="november-2016"></a>2016년 11월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **Windows 10 장치에 사용할 수 있는 새로운 Microsoft Intune 회사 포털**

  Microsoft에서 새로운 [Windows 10 장치용 회사 포털 앱](https://www.microsoft.com/store/apps/9wzdncrfj3pz)을 출시했습니다. 새로운 Windows 10 유니버설 형식을 활용하는 이 앱은 모든 Windows 10 장치(PC 및 모바일)에서 동일한 업데이트된 사용자 환경을 제공합니다. 이전 회사 포털 앱에서 제공되었던 것과 동일한 기능도 모두 계속 사용할 수 있습니다.

  새로운 앱은 Windows 10 장치에서 SSO(Single Sign-On) 및 인증서 기반 인증과 같은 플랫폼 기능을 활용합니다. 이 앱은 Windows 스토어에서 설치되는 기존 Windows 8.1 회사 포털 및 Windows Phone 8.1 회사 포털의 업그레이드로 제공됩니다. 추가 세부 정보를 확인하려면 [Intune 지원 팀 블로그](http://aka.ms/intunecp_universalapp)를 방문하세요.

  새로운 회사 포털 앱에는 Configuration Manager 콘솔에 **사용 가능**으로 표시되는 비즈니스용 Windows 스토어 응용 프로그램도 표시됩니다.


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

이전에 Configuration Manager Technical Preview 릴리스에서 사용할 수 있었던 다음 기능을 이제 Intune과 Configuration Manager(현재 분기) 버전 1610을 포함하는 하이브리드 배포에서 사용할 수 있습니다.

* [구성 항목에 대한 추가 설정 및 향상된 환경](/sccm/core/plan-design/changes/whats-new-in-version-1610#new-compliance-settings-for-configuration-items)
* [DEP 프로필에 대한 추가 설정](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [비즈니스용 Windows 스토어의 유료 앱](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Windows 10 VPN 프로필에 대한 네이티브 연결 형식](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
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

## <a name="october-2016"></a>2016년 10월

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

## <a name="september-2016"></a>2016년 9월

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

## <a name="august-2016"></a>2016년 8월

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

## <a name="july-2016"></a>2016년 7월

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

* Configuration Manager 콘솔에서 Windows 10 장치에 대한 비즈니스용 Windows 스토어 앱 찾기, 관리 및 배포([1604](#new-in-1604-technical-preview))
*   Android 장치에 대한 SmartLock 설정([1604](#new-in-1604-technical-preview))
*   Windows 10 장치를 위한 앱 트리거 VPN([1605](#new-in-1605-technical-preview))
*   원격 장치 작업을 위한 새로운 환경([1605](#new-in-1605-technical-preview))
*   비즈니스용 Windows 스토어 앱([1605](#new-in-1605-technical-preview))
*   대량 구매 앱의 일반적인 향상 기능([1605](#new-in-1605-technical-preview))
*   WIP(Windows Information Protection)([1605](#new-in-1605-technical-preview))
*   IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언([1605](#new-in-1605-technical-preview))
*   컬렉션으로 장치 자동 분류([1606](#new-in-1606-technical-preview))

새로운 기능에 대한 자세한 내용은 지정된 기술 미리 보기 릴리스에 대한 설명서를 참조하세요.

## <a name="june-2016"></a>2016년 6월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능
2016년 6월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **Intune 서비스 상태** Intune에 대한 서비스 상태 정보가 다른 Microsoft 서비스와 함께 중앙 위치로 이동되었습니다. 이제 Office 365 관리 포털의 서비스 상태 아래에서 이 정보를 확인할 수 있습니다. 자세한 내용은 이 [블로그 게시물](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/)을 참조하세요.

- **향상된 Windows 10 Enterprise 데이터 정책 구성 환경**

  이제 Intune에 Windows 10 Information Protection 정책을 구성하기 위한 향상된 환경이 있습니다. 향상된 기능에는 앱 규칙을 만들고, 네트워크 경계 정의 및 기타 Windows Information Protection 설정을 지정하는 더 나은 방법이 포함됩니다. 자세한 내용은 [Microsoft Intune을 사용하여 WIP(Windows Information Protection) 정책 만들기](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune)를 참조하세요.

- **Intune에 대한 Cisco ISE 네트워크 액세스 제어 정책**

  Cisco ISE(Identity Service Engine) 2.1을 사용하고 Microsoft Intune도 사용하는 고객은 ISE에서 네트워크 액세스 제어 정책을 설정할 수 있습니다. 이 정책을 사용하는 경우 WiFi 또는 VPN을 통해 네트워크에 연결해야 하는 장치는 다음 조건을 충족해야 액세스가 허용됩니다.

  - Intune에서 관리해야 함
  - 배포된 Intune 준수 정책을 준수해야 함

  비규격 장치의 최종 사용자는 액세스하기 위해 등록하고 준수 문제를 해결하라는 메시지가 표시됩니다.

- **브라우저에 대한 조건부 액세스**

  관리되는 규격 iOS 및 Android 장치의 지원되는 웹 브라우저에서만 액세스할 수 있도록 Exchange Online 및 SharePoint Online에 대한 조건부 액세스 정책을 설정할 수 있습니다. iOS 및 Android 장치를 사용하여 OWA(Outlook Web Access) 및 SharePoint 사이트에 로그인하려는 최종 사용자에게는 Intune에 장치를 등록하고 비준수 문제를 해결해야 로그인을 완료할 수 있다는 메시지가 표시됩니다. 자세한 내용은

  * [Intune을 사용하여 Exchange Online 및 새 Exchange Online Dedicated에 대한 메일 액세스 제한](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
  * [Microsoft Intune을 사용하여 SharePoint Online에 대한 액세스 제한](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

- **Dynamics CRM Online에서 조건부 액세스 지원**

  관리되는 규격 iOS 및 Android 장치에서만 액세스할 수 있도록 Dynamics CRM Online에 대한 조건부 액세스 정책을 설정할 수 있습니다. iOS 및 Android의 Dynamics CRM 모바일 앱에 로그인하려는 최종 사용자에게는 Intune에 등록하고 비준수 문제를 해결해야 로그인을 완료할 수 있다는 메시지가 표시됩니다. 자세한 내용은 [Microsoft Intune을 사용하여 Dynamics CRM Online에 대한 액세스 제한](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune)을 참조하세요.

- **Android 회사 포털 앱에 대한 업데이트**

  이제 Intune에 Android 회사 포털 사용자에게 영향을 주는 다음과 같은 새 정책이 있습니다.   

  정책  |사용자에 미치는 영향  
  ---------|---------
  장치가 알 수 없는 소스의 앱 설치를 방지해야 함(Android 4.0 이상)     |  Android 4.0 이상 장치를 사용하는 최종 사용자에게는 "알 수 없는 소스의 설치를 사용하지 않도록 설정해야 합니다."라는 메시지가 표시됩니다. 사용자는 해당 장치에서 **설정 > 보안**으로 이동한 다음 **알 수 없는 소스**를 꺼야 합니다. 사용자는 준수 메시지에 있는 링크를 통해 메시지에 대한 자세한 정보와 설정을 꺼야 하는 이유를 확인할 수 있습니다.
  장치가 알 수 없는 소스의 앱 설치를 방지해야 함(Android 4.0 이상)  |    Android 4.0 이상 장치를 사용하는 최종 사용자에게는 "장치의 보안 위협 검색"이라는 메시지가 표시됩니다. 사용자가 해당 장치에서 **설정 > Google > 보안**으로 이동한 다음 **장치의 보안 위협 검색**을 켜야 합니다. 사용자는 준수 메시지에 있는 링크를 통해 메시지에 대한 자세한 정보와 설정을 켜야 하는 이유를 확인할 수 있습니다.     
  USB 디버깅을 사용하지 않도록 설정되어야 함(Android 4.2 이상)  | Android 4.2 이상 장치를 사용하는 최종 사용자에게는 "USB 디버깅을 사용하지 않도록 설정해야 합니다."라는 메시지가 표시됩니다. 사용자는 해당 장치에서 **설정 > 개발자 옵션**으로 이동한 다음 **USB 디버깅**을 꺼야 합니다. 사용자는 준수 메시지에 있는 링크를 통해 메시지에 대한 자세한 정보와 설정을 꺼야 하는 이유를 확인할 수 있습니다.
  최소 Android 보안 패치 수준(Android 6.0 이상)  | Android 6.0 이상 장치를 사용하는 최종 사용자에게는 "이 장치는 최소 Android 보안 패치 수준을 충족하지 않습니다."라는 메시지가 표시됩니다. 사용자가 필요한 보안 패치를 설치해야 합니다. 사용자는 준수 메시지에 있는 링크를 통해 필요한 보안 패치를 설치하는 방법에 대한 자세한 정보를 얻고 현재 설치된 보안 패치를 확인할 수 있습니다.

- **iOS 회사 포털 앱에 대한 업데이트**

  * 이제 최종 사용자가 LOB(기간 업무) 앱을 설치할 때 향상된 앱 설치 환경이 표시됩니다. 앱 설치에 오랜 시간이 걸리는 경우 사용자가 장치를 수동으로 동기화하여 동기화 프로세스를 강제로 다시 시작할 수 있습니다. 최종 사용자 지침을 검토하려면 iOS 장치 수동 동기화를 참조하세요.
  * iOS용 Microsoft Intune 회사 포털 앱은 iOS 버전 8.0 이상을 지원하도록 업데이트되었습니다. 이 업데이트를 사용하면 장치가 iOS 버전 8.0 이상을 실행하는 경우 최종 사용자가 회사 포털 앱을 설치하고 Intune에 새 장치를 등록할 수 있습니다. 지원되지 않는 iOS 버전을 실행 중이고 이미 등록된 장치가 있는 사용자는 자신의 장치에 있는 회사 포털 앱을 계속 사용할 수 있습니다.


### <a name="new-in-1606-technical-preview"></a>1606 기술 미리 보기의 새로운 기능
2016년 6월에 도입된 다음 새로운 기능은 Intune과 Configuration Manager Technical Preview 1606을 포함하는 하이브리드 배포에서 사용할 수 있습니다.

- **컬렉션으로 장치 자동 분류**

  Intune에서 Configuration Manager를 사용하는 경우 장치 컬렉션에 장치를 자동으로 배치하는 데 사용할 수 있는 장치 범주를 만들 수 있습니다. 그런 다음 사용자는 Intune에 장치를 등록할 때 장치 범주를 선택해야 합니다. 또한 Configuration Manager 콘솔에서 장치의 범주를 변경할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 Technical Preview 1606의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1606)에서 [컬렉션으로 장치 자동 분류](/sccm/core/get-started/capabilities-in-technical-preview-1606#dmp_category)를 참조하세요.

  > [!IMPORTANT]
  > 이 기능은 Microsoft Intune의 2016년 6월 릴리스에 작동합니다. 이러한 절차를 시도하기 전에 이 릴리스로 업데이트했는지 확인합니다.

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능
Configuration Manager(현재 분기) 2016년 6월에 도입된 새로운 하이브리드 기능은 없습니다.

##  <a name="may-2016"></a>2016년 5월  

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능  
 2016년 5월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **MAM SDK: PIN 길이 구성 지원**

  이제 장치 PIN과 유사한 PIN 길이를 MAM 앱에 지정할 수 있습니다. 이 경우 최종 사용자가 설정된 새로운 제한 사항을 준수해야 합니다. PIN 화면이 더 긴 입력을 수용하기 위해 약간 수정되었습니다. 자세한 내용은 [Android에 대한 MAM 정책 설정](https://docs.microsoft.com/intune/deploy-use/android-mam-policy-settings) 및 [iOS에 대한 MAM 정책 설정](https://docs.microsoft.com/intune/deploy-use/ios-mam-policy-settings)을 참조하세요.  

- **iOS 및 Android의 비즈니스용 Skype**

  이제 [등록 정책을 사용하지 않는 MAM](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune)을 통해 비즈니스용 Skype의 대상을 지정할 수 있습니다. 사용자가 로그인하면 MAM 정책이 적용됩니다.  

- **MAM 정책을 사용한 관리를 위해 제공되는 새 앱**

  이제 Android용 Microsoft Word, Excel 및 PowerPoint 앱을 Intune에 등록되지 않은 장치의 MAM 정책과 연결할 수 있습니다. 지원되는 앱의 전체 목록을 보려면 [Microsoft Intune 응용 프로그램 파트너](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) 페이지의 Microsoft Intune 모바일 응용 프로그램 갤러리로 이동합니다.  

- **Android 회사 포털 앱: 최종 사용자 알림 메시지**

  최종 사용자가 장치를 등록하거나 회사 포털에서 제거하면 Android 회사 포털 앱의 알림 메시지가 나타납니다.  

- **회사 포털 웹 사이트: 장치 식별 배너에서 최종 사용자에게 자세한 정보를 제공함**

  이제 최종 사용자가 회사 포털 웹 사이트를 사용할 때 선택한 장치를 보다 쉽게 식별할 수 있습니다. 잘못된 장치를 선택한 경우 홈페이지 배너의 **여기를 탭하세요.** 링크를 탭하여 올바른 장치를 선택할 수 있습니다.  


### <a name="new-in-1605-technical-preview"></a>1605 기술 미리 보기의 새로운 기능  
 2016년 5월에 도입된 다음 새로운 기능은 Intune과 Configuration Manager Technical Preview 1605를 포함하는 하이브리드 배포에서 사용할 수 있습니다. 이러한 기능은 Configuration Manager 콘솔을 사용하여 구성 및 관리해야 합니다.  

- **Windows 10 장치를 위한 앱 트리거 VPN**

  Intune에서 Configuration Manager를 사용하여 관리되는 Windows 10 장치의 경우, Configuration Manager 관리 콘솔을 통해 구성한 VPN 연결을 자동으로 여는 앱 목록을 추가할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 Technical Preview 1605의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1605)에서 [Windows 10 장치를 위한 앱 트리거 VPN](/sccm/core/get-started/capabilities-in-technical-preview-1605)을 참조하세요.  

- **원격 장치 작업을 위한 새로운 환경**

  Configuration Manager 콘솔에서 원격 장치 작업을 수행하기 위한 환경이 개선되었습니다.

  이제 **자산 및 준수** 작업 영역에서 액세스되는 **원격 장치 작업** 메뉴에서 **사용 중지/초기화**, **암호 다시 설정**, **원격 잠금** 및 **활성화 잠금 무시** 등의 일반 작업을 찾을 수 있습니다.

  자세한 내용은 [System Center Configuration Manager용 Technical Preview 1605의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1605)에서 [원격 장치 작업을 위한 새로운 환경](/sccm/core/get-started/capabilities-in-technical-preview-1605#new-experience-for-remote-device-actions)을 참조하세요.  

- **비즈니스용 Windows 스토어 앱**

  [비즈니스용 Windows 스토어](https://www.microsoft.com/en-us/business-store)에서 조직을 위한 앱을 찾아서 개별적으로 또는 대량으로 구매할 수 있습니다. 스토어를 Configuration Manager에 연결하여 Configuration Manager 콘솔에서 대량 구매 앱을 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 Technical Preview 1605의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1605)에서 [비즈니스용 Windows 스토어 앱](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#windows-store-for-business-apps)을 참조하세요.  

- **대량 구매 앱의 일반적인 향상 기능**

  비즈니스용 Windows 스토어와 iOS App Store의 대량 구매 앱이 동일한 보기, **스토어 앱에 대한 라이선스 정보**로 통합되었습니다. 또한 iOS용 대량 구매 앱을 만드는 방식으로 향상되었습니다. 자세한 내용은 [System Center Configuration Manager용 Technical Preview 1605의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1605)에서 [대량 구매 앱에 대한 일반적인 향상 기능](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#general-improvements-for-volume-purchased-apps)을 참조하세요.  

- **IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언**

  이제 IMEI(International station Mobile Equipment Identity) 번호를 가져와서 회사 소유 장치를 식별할 수 있습니다. 장치 IMEI 번호를 포함한 쉼표로 구분된 값(.csv) 파일을 업로드하거나 장치 정보를 수동으로 입력할 수 있습니다.  또한 iOS 장치의 일련 번호를 가져올 수 있습니다.  자세한 내용은 [System Center Configuration Manager용 Technical Preview 1605의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1605)에서 [IMEI 또는 iOS 일련 번호로 회사 소유 장치 미리 선언](../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_IMEI)을 참조하세요.  

- **WIP(Windows Information Protection)**

  보호된 앱, WIP 보호 수준 및 네트워크에서 엔터프라이즈 데이터를 찾는 방법을 선택하는 항목을 포함하여 WIP(Windows Information Protection) 정책을 배포할 수 있는 구성 항목을 만들 수 있습니다. WIP에 대한 자세한 내용은 다음 항목을 참조하세요.  

  -   [WIP(Windows Information Protection)를 사용하여 엔터프라이즈 데이터 보호](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)  

  -   [System Center Configuration Manager를 사용하여 WIP(Windows Information Protection) 정책 만들기 및 배포](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-sccm)  

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능  
 Configuration Manager(현재 분기) 2016년 5월에 도입된 새로운 하이브리드 기능은 없습니다.  

##  <a name="april-2016"></a>2016년 4월  

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능  
 2016년 4월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.  

- **MAM 사용자 준수**

  이제 AAD(Azure Active Directory) 테넌트의 사용자에 대한 응용 프로그램 관리 정책의 상태를 볼 수 있습니다.  자세한 내용은 Intune 라이브러리에서 [Microsoft Intune으로 모바일 앱 관리 정책 모니터링](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)을 참조하세요.  

- **Outlook 연락처 동기화를 방지하는 MAM 컨트롤(Android)**

  응용 프로그램이 Android 장치의 기본 주소록에 연락처를 동기화할 수 없도록 하는 새로운 설정을 사용할 수 있습니다. 이 새로운 설정은 처음에 Android 장치의 Outlook 응용 프로그램에서 지원됩니다. 자세한 내용은 Intune 라이브러리에서 [Microsoft Intune으로 모바일 앱 관리 정책 만들기 및 배포](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)를 참조하세요.  

- **회사 포털 웹 사이트의 향상된 기능**

  Windows 10 Mobile 및 Windows Phone 8.1 사용자가 LOB(기간 업무) 앱을 설치하는 경우 이제 설치 상태에 대한 자세한 정보를 제공하는 다음과 같은 새 상태가 표시됩니다.  

  -   **장치가 동기화될 때까지 기다리는 중** – 사용자가 "설치"를 탭했으며 이제 장치에서 Intune 인프라와 동기화하려고 합니다. 먼저 동기화해야 설치를 완료할 수 있습니다. "장치가 동기화될 때까지 기다리는 중" 메시지는 동기화 프로세스가 시간이 오래 걸리거나 정지될 경우 수동으로 Intune과 장치를 동기화하는 방법에 대한 지침을 보기 위해 사용자가 탭할 수 있는 링크이기도 합니다.  

  -   **다운로드 중** - 사용자의 다운로드 요청이 처리되고 있으며 장치에서 앱을 다운로드하여 설치 중입니다.  

- **Android 회사 포털 앱에 대한 향상된 기능**

  Intune에 장치를 등록하지 않았으며 올바른 인증서가 설치되어 있지 않은 사용자는 Android 회사 포털 앱에 로그인할 수 없으며 "필요한 인증서가 장치에 없으므로 로그인할 수 없습니다."라는 메시지가 표시됩니다. 메시지에는 사용자가 인증서 설치 지침을 보기 위해 탭할 수 있는 "이 문제를 해결하는 방법" 링크가 포함되어 있습니다. 최종 사용자가 문제를 해결하기 위해 수행할 단계를 보려면 Intune 라이브러리에서 [장치에 필요한 인증서가 없는 경우](/intune/enduser/using-your-android-device-with-intune)를 참조하세요.  

- **iOS 회사 포털 앱에 대한 향상된 기능**

  앱 목록, 장치 목록 및 IT 연락처 정보를 포함하는 홈 화면의 콘텐츠를 새로 고치기 위한 끌어오기-새로 고침 작업에 대한 지원이 추가되었습니다. 끌어오기-새로 고침 작업은 현재 장치에 대한 타일을 선택하고 **동기화** 단추를 탭하여 수행할 수 있는 준수 또는 정책 정보를 확인하지 않습니다.  

- **Windows 10 Mobile 및 Windows Phone 8.1 회사 포털 앱에 대한 향상된 기능**

  이제 최종 사용자가 LOB(기간 업무) 앱을 설치할 때 향상된 앱 설치 환경이 표시됩니다. 앱 설치에 오랜 시간이 걸리는 경우 사용자가 장치를 수동으로 동기화하여 동기화 프로세스를 강제로 다시 시작할 수 있습니다. 최종 사용자 지침을 검토하려면 Intune 라이브러리에서 [장치를 수동으로 동기화하여 앱 설치 속도 향상](/intune/enduser/using-your-windows-device-with-intune)을 참조하세요.  

###  <a name="new-in-1604-technical-preview"></a>1604 기술 미리 보기의 새로운 기능
 2016년 4월에 도입된 다음 새로운 기능은 Intune과 Configuration Manager Technical Preview 1604를 포함하는 하이브리드 배포에서 사용할 수 있습니다. 이러한 기능은 Configuration Manager 콘솔을 사용하여 구성 및 관리해야 합니다.  

- **Configuration Manager 콘솔에서 Windows 10 장치에 대한 비즈니스용 Windows 스토어 앱 찾기, 관리 및 배포**


  Configuration Manager Technical Preview 1604에서는 관리하는 Windows 10 장치에 대한 앱을 찾고 관리 및 배포할 수 있도록 도와주는 비즈니스용 Windows 스토어에 대한 지원을 사용할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 Technical Preview 1604의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1604)에서 [비즈니스용 Windows 스토어에서 대량 구매 앱 관리](/sccm/core/get-started/capabilities-in-technical-preview-1604#manage-volume-purchased-apps-from-the-windows-store-for-business)를 참조하세요.  

- **Android 장치에 대한 SmartLock 설정**

  새 설정이 Android 및 Samsung KNOX Standard 구성 항목에 추가되었습니다. 이를 통해 호환되는 Android 장치에서 SmartLock 기능을 제어할 수 있습니다.  이 설정을 사용하면 최종 사용자가 SmartLock을 구성하지 않도록 방지할 수 있습니다. [System Center Configuration Manager용 Technical Preview 1604의 기능](/sccm/core/get-started/capabilities-in-technical-preview-1604.md)에서 [Android 장치에 대한 SmartLock 설정](/sccm/get-started/capabilities-in-technical-preview-1604#smartlock-setting-for-android-devices)을 참조하세요.  

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능  
 Configuration Manager(현재 분기) 2016년 4월에 도입된 새로운 하이브리드 기능은 없습니다.  

##  <a name="march-2016"></a>2016년 3월  

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능  
 2016년 3월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.  

- **Outlook 연락처 동기화를 방지하는 MAM 컨트롤(iOS)**

  응용 프로그램이 iOS 장치의 기본 주소록에 연락처를 동기화할 수 없도록 하는 새로운 설정을 사용할 수 있습니다. 이 새로운 설정은 iOS 장치의 Outlook 응용 프로그램에서 지원됩니다. 이 설정 및 기타 설정에 대한 자세한 내용은 Intune 라이브러리에서 [MAM 정책 만들기 및 배포](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune)를 참조하세요.  

- **비즈니스용 Skype Online에서 조건부 액세스 지원**

  관리되는 규격 iOS 및 Android 장치에서만 액세스할 수 있도록 비즈니스용 Skype Online에 대한 조건부 액세스 정책을 설정할 수 있습니다.  자세한 내용은 Intune 라이브러리에서 [비즈니스용 Skype Online에 대한 액세스 관리](/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune)를 참조하세요.  

- **iOS 9.3에 대한 지원**

  3월 21일 월요일에 Apple은 iOS 9.3의 가용성을 발표했습니다. 현재 iOS 장치 관리에 사용할 수 있는 기존의 모든 Intune 기능은 사용자가 장치를 iOS 9.3으로 업그레이드할 때도 계속 원활하게 작동합니다.  

- **회사 포털 웹 사이트에서 직접 사용할 수 있는 Windows 앱 패키지**

  이제 Windows 8, Windows 8.1 및 Windows RT PC 사용자가 회사 포털 웹 사이트에서 직접 Windows 앱 패키지(.appx 확장명 사용)을 설치할 수 있습니다. 이전에는 관리자가 배포하거나, 사용자가 앱을 설치할 장치에 회사 포털 앱을 설치해야 했습니다.  

- **사용자가 회사 포털 웹 사이트에서 원격으로 장치를 잠글 수 있음**

  사용자가 장치를 분실하거나 도난당한 경우 포털에서 원격으로 장치를 잠글 수 있도록 하는 새로운 원격 잠금 옵션이 회사 포털 웹 사이트에 추가되었습니다.  

- **타사 MDM 솔루션에 등록된 장치에 대해 iOS "다음에서 열기" 관리 활용**

  타사 MDM(모바일 장치 관리) 공급업체를 사용하여 iOS "다음에서 열기" 관리를 활용할 수 있습니다. 구성 프로필 설정에서 제한을 설정하고 MDM 소프트웨어를 사용하여 앱을 배포할 수 있습니다. 사용자가 관리되는 앱을 설치하면 제한 사항이 적용됩니다. 자세한 내용은 Intune 라이브러리에서 [Microsoft Intune 모바일 앱 관리 정책 및 iOS 다음에서 열기](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune)를 참조하세요.  

- **MAM을 지원하는 Microsoft 앱**

  Intune 모바일 응용 프로그램 관리 정책과 함께 사용할 수 있는 Microsoft 앱 목록이 최신 앱을 포함하도록 업데이트되었습니다(Intune에 등록된 장치에만 해당).  

- **엔터프라이즈의 Intune 관리 iOS 장치에 Microsoft Intune용 Adobe Reader 배포**

  이제 Intune 모바일 응용 프로그램 관리 정책에 등록된 장치에서 iOS용 Adobe Reader 앱을 관리할 수 있습니다.  

- Android에 대해 Rights Management 공유 앱이 지원됨

  IT에서 Intune을 사용하여 장치를 관리하는지 여부에 관계없이 최종 사용자가 이미지, AV 및 PDF 파일을 보다 안전하게 볼 수 있도록 IT 관리자가 모바일 응용 프로그램 관리 정책을 배포할 수 있습니다.  

- **Android 및 iOS 회사 포털 앱에 대한 향상된 기능**

  -   사용자가 MAM(모바일 응용 프로그램 관리)에서 관리되는 앱을 실행하는 경우 앱이 회사에서 관리된다고 알리는 메시지가 표시됩니다. 이제 사용자가 "자세한 정보" 링크를 탭하여 "관리되는 앱"의 의미에 대한 자세한 정보를 여기서 확인할 수 있습니다. 앱을 실행할 때 메시지는 더 이상 표시되지 않도록 "다시 표시 안 함"을 탭할 수도 있습니다.  

  -   사용자에게 등록 과정을 안내하고 사용자가 등록해야 이유 및 IT 관리자가 등록된 장치에서 볼 수 있는 사항과 볼 수 없는 사항에 대한 자세한 정보를 제공하는 새 화면이 추가되었습니다.  

  -   이제 등록 오류 메시지가 회사 포털 앱에 표시됩니다.  

### <a name="new-in-configuration-manager-technical-preview"></a>Configuration Manager Technical Preview의 새로운 기능  
 Configuration Manager Technical Preview의 2016년 3월에 도입된 새로운 하이브리드 기능은 없습니다.  

### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능  
 2016년 3월에 도입된 다음 새로운 기능은 Intune과 Configuration Manager(현재 분기) 버전 1602를 포함하는 하이브리드 배포에서 사용할 수 있습니다. 이러한 기능은 Configuration Manager 콘솔을 사용하여 구성 및 관리해야 합니다.  

- **iOS 앱 구성 정책**

  Configuration Manager(현재 분기) 버전 1602에서는 앱 구성 정책을 사용하여 사용자가 iOS 앱을 실행할 때 필요할 수 있는 설정을 제공할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 앱 구성 정책을 사용하여 iOS 앱 구성](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies)을 참조하세요.  

- **대량 구매한 iOS 앱 관리**

  버전 1602의 Configuration Manager(현재 분기)를 통해 앱 스토어에서 라이선스 정보를 가져오고 사용한 라이선스 수를 추적하여 Apple VPP(Volume-Purchase Program)에서 대량 구매한 앱을 배포하고 관리할 수 있습니다. 자세한 내용은 [System Center Configuration Manager를 사용하여 대량 구매한 iOS 앱 관리](/sccm/apps/deploy-use/manage-volume-purchased-ios-apps)를 참조하세요.  

- **Office 모바일 앱의 자동 만들기**

  Configuration Manager(현재 분기) 버전 1602부터, 버전 1511에서 업그레이드할 때 다음과 같은 Android 및 iOS용 Microsoft Office 모바일 앱이 생성됩니다.  

  -   Microsoft Word  
  -   Microsoft Excel  
  -   Microsoft PowerPoint  
  -   Microsoft OneDrive  
  -   Microsoft OneNote(iOS만 해당)  
  -   Microsoft Outlook  

  이러한 앱은 Configuration Manager 콘솔의 응용 프로그램 노드에 있습니다. 응용 프로그램을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 응용 프로그램을 배포하는 방법](../../apps/deploy-use/deploy-applications.md)을 참조하세요.  

- **Android Samsung KNOX Standard 장치에 대한 키오스크 모드 설정**

  키오스크 모드에서는 장치를 잠가 특정 기능만 작동하도록 허용할 수 있습니다.  Configuration Manager(현재 분기) 버전 1602부터, 이제 Samsung KNOX Standard 장치에 대한 키오스크 모드 설정을 지정할 수 있습니다. 자세한 내용은 [System Center Configuration Manager 클라이언트 없이 관리되는 Android 및 Samsung KNOX Standard 장치에 대한 구성 항목을 만드는 방법](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client)을 참조하세요.  

- **iOS 활성화 잠금**

  Configuration Manager(현재 분기) 버전 1602부터, iOS 7.1 이상 장치용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금은 장치에서 나의 iPhone 찾기 앱을 사용할 때 자동으로 사용하도록 설정됩니다.  자세한 내용은 [System Center Configuration Manager에 대한 iOS 활성화 잠금 무시 관리](/sccm/mdm/deploy-use/manage-ios-activation-lock#bypass-activation-lock)를 참조하세요.  



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
