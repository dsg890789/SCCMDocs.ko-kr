---
title: "새로운 하이브리드 MDM 기능 | Microsoft 문서"
description: "System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 새 모바일 장치 관리 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 01/12/2017
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
ms.sourcegitcommit: 7327c969402b9b467cfb50d1dd3255797a9d4c4e
ms.openlocfilehash: 27b75831f28860ca435b4a53aad31abd15b9e451

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

## <a name="new-hybrid-features-in-january-2017"></a>2017년 1월의 새로운 하이브리드 기능

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

2017년 1월에 도입된 다음 Intune 기능은 하이브리드 배포에서 사용할 수 있습니다.

- **Android 7.1.1 지원**

  이제 Intune에서 Android 7.1.1을 완벽하게 지원하고 관리합니다.

- **iOS 장치가 비활성 상태이거나 관리 콘솔이 장치와 통신할 수 없는 문제 해결**

  사용자 장치와 Intune의 연결이 끊어진 경우 회사 리소스에 다시 액세스할 수 있도록 지원할 새로운 문제 해결 단계를 제공할 수 있습니다. [장치가 비활성 상태이거나 관리 콘솔이 장치와 통신할 수 없음](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them)을 참조하세요.


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


