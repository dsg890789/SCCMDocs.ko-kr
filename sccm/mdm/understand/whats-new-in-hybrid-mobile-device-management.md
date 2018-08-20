---
title: 하이브리드 MDM의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager를 포함하는 하이브리드 배포에 사용할 수 있는 새 모바일 장치 관리 기능에 대해 알아봅니다.
ms.date: 08/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cdb5720778366cea951476ad9b314b69bdd0c492
ms.sourcegitcommit: 6e0e5b4b7779ce03e2b56b3b5f68f4ace1acedd8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467609"
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 모바일 장치 관리의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 새 MDM(모바일 장치 관리) 기능에 대한 세부 정보를 제공합니다.     

> [!Note]    
> Azure의 Intune은 Microsoft에서 권장하는 MDM 솔루션입니다.     
> - Intune 독립 실행형에서 새로운 기능 및 업데이트에 대한 세부 정보는 [Intune의 새로운 기능](https://docs.microsoft.com/intune/whats-new)을 참조하세요.    
> - Intune 독립 실행형을 마이그레이션하는 방법에 대한 세부 정보는 [하이브리드 MDM 사용자 및 장치를 Intune 독립 실행형으로 마이그레이션](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.
> - Intune과 하이브리드 MDM의 UI 업데이트에 대한 세부 정보는 [Intune 최종 사용자 앱의 UI 업데이트](https://docs.microsoft.com/intune/whats-new-app-ui)를 참조하세요. 



##  <a name="compatibility-with-configuration-manager-versions"></a>Configuration Manager 버전과 호환성  

이 문서의 각 섹션에서는 세 가지 범주로 하이브리드 기능이 나열되어 있습니다. 각 범주의 기능과 다양한 Configuration Manager 버전 간의 호환성을 확인하려면 다음 지침을 따르세요.  

|기능 범주|설명|
|-|-|
|**Microsoft Intune의 새로운 기능** | 일반적으로 이 범주 아래에 나열된 모든 기능은 Intune 서비스만 필요하고 Configuration Manager의 추가 기능이 필요하지 않으므로 System Center 2012 R2 Configuration Manager 릴리스를 비롯한 모든 Configuration Manager 릴리스에서 사용할 수 있어야 합니다.|
|**Configuration Manager Technical Preview의 새로운 기능**| 이 범주 아래에 나열된 모든 기능은 지정된 Technical Preview 분기에서만 사용할 수 있습니다. 이러한 기능을 시험해보려면 기능 설명에 지정된 기술 미리 보기 버전을 설치해야 합니다. 자세한 내용은 [Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.|
|**Configuration Manager(현재 분기)의 새로운 기능**| 이 범주 아래에 나열된 모든 기능은 지정된 버전의 Configuration Manager(현재 분기)에서만 사용할 수 있습니다. 하이브리드 배포에 이전 버전의 Configuration Manager를 사용하는 경우 기능 설명에 지정된 Configuration Manager(현재 분기) 버전으로 업그레이드합니다. 자세한 내용은 [Configuration Manager로 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)를 참조하세요.|



## <a name="july-2018"></a>2018년 7월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="support-for-security-enhancement-in-intune-service"></a>Intune 서비스의 보안 강화 지원
<!--2520152--> 이제 모든 할당된 준수 정책이 없는 장치가 하이브리드에서 준수되지 않음을 지정할 수 있습니다. Azure Portal의 Intune에서 이 설정을 구성합니다. 이 기능을 사용하여 내부 리소스를 보호하는 것이 좋습니다.

이 기능은 하이브리드 테넌트에서는 기본적으로 해제되어 있습니다. 이 기능을 활성화하면 할당된 준수 정책이 없는 장치는 비준수로 간주됩니다. 조건부 액세스도 활성화하면 이러한 장치는 내부 리소스에 액세스할 수 없게 됩니다. 이러한 리소스는 사용자 환경의 조건부 액세스 정책에 따라 Outlook 또는 SharePoint일 수 있습니다. 이 설정을 해제해도 이러한 장치는 현재와 동일한 수준의 액세스 권한을 유지합니다.

이 기능에 미치는 영향을 확인하는 데 도움이 되도록 [TechNet 갤러리의 스크립트](https://gallery.technet.microsoft.com/SQL-Query-for-Hybrid-MDM-5bcb8695)가 제공되었습니다. Configuration Manager 데이터베이스에 대해 이 스크립트를 실행하면 준수 정책의 대상이 아닌 장치가 나열됩니다.

자세한 내용은 다음 아티클을 참조하세요.
- [Intune 서비스의 보안 강화 기능](https://aka.ms/compliance_policies) 블로그 게시물 
- [Configuration Manager의 장치 준수 정책](/sccm/mdm/deploy-use/device-compliance-policies)

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app"></a>회사 포털 앱에서 규정에 맞지 않는 메시지에 대한 업데이트 
<!--1832222--> 장치가 규정에 맞지 않는 경우 장치 사용자에게 표시되는 메시지를 수정합니다. 메시지의 원래 의미는 유지하지만 기술 용어를 줄이고 더 친근한 언어로 업데이트합니다. 설명서와 수정 단계에 대한 링크도 새로 고쳐서 최신 상태로 유지합니다.  

다음의 텍스트는 표시되는 메시지의 개선 내용 중 한 가지 예입니다.  

- 이전: *이 장치는 IT 관리자가 요구한 지정된 기간 내에 Intune 서비스를 연결하지 않았습니다. 이 문제를 해결하려면 장치에서 회사 포털 앱을 열고 준수 확인 단추를 클릭하세요.*  

- 이후: *장치가 조직에서 한동안 체크 인되지 않았습니다. 연결을 다시 설정하려면 장치에서 회사 포털 앱을 열고 장치의 설정 확인을 탭하세요.*  

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings"></a>회사 또는 학교 액세스 설정을 사용하여 장치 범주 선택 
<!--1058963--> [장치 그룹 매핑](https://docs.microsoft.com/intune/device-group-mapping)을 사용하도록 설정한 경우 이제 Windows 10에서 사용자가 **설정** > **계정** > **회사 또는 학교 액세스**의 **연결** 단추를 통해 등록할 때 장치 범주를 선택하라는 메시지가 표시됩니다.  

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱의 새 검색 환경 
<!--2317227--> 이제 Windows용 회사 포털 앱에서 앱을 검색하거나 탐색하는 경우 기존 **타일** 보기 및 새로 추가한 **세부 정보** 보기 사이를 토글합니다. 새 보기는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 응용 프로그램 세부 정보를 나열합니다. 

**앱** 페이지의 **설치된** 보기를 사용하면 완료 및 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있습니다. 새 보기의 모습을 보려면 [UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)을 참조하세요.

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 더 많은 동기화 기회  
<!--2683177--> 이제 Windows용 회사 포털 앱을 사용하면 Windows 작업 표시줄 및 시작 메뉴에서 직접 동기화를 시작할 수 있습니다. 이 기능은 유일한 작업이 장치를 동기화하고 회사 리소스에 대한 액세스 권한을 얻는 것인 경우 특히 유용합니다. 새로운 기능에 액세스하려면 시작 메뉴 또는 작업 표시줄에 고정된 회사 포털 아이콘을 마우스 오른쪽 단추로 클릭합니다. 메뉴 옵션에서 **이 장치 동기화**를 선택합니다. (이 메뉴는 점프 목록이라고도 합니다.) 회사 포털은 **설정** 페이지에서 열리고 동기화를 시작합니다. 업데이트 프로시저는 [수동으로 Windows 장치 동기화](https://docs.microsoft.com/intune/intune-user-help/sync-your-device-manually-windows#sync-from-device-taskbar-or-start-menu)를 참조하세요.



## <a name="june-2018"></a>2018년 6월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="access-to-macos-company-portal-pre-release-build"></a>macOS 회사 포털 시험판 빌드에 액세스 
<!--1734766--> Microsoft 자동 업데이트를 사용하여 등록하고 Insider 프로그램에 참여하여 빌드를 조기에 받으세요. 등록하면 업데이트된 회사 포털을 사용해 본 이후에 최종 사용자에게 제공할 수 있습니다.

#### <a name="intune-app-protection-policies-and-microsoft-edge"></a>Intune 앱 보호 정책 및 Microsoft Edge 
<!--1818968,1818969--> 모바일 장치(iOS 및 Android)용 Microsoft Edge 브라우저는 Microsoft Intune 앱 보호 정책을 지원합니다. Edge응용 프로그램에서 회사 Azure Active Directory 계정으로 로그인하는 iOS 및 Android 장치의 사용자는 Intune에서 보호합니다. IOS 장치에서 **웹 콘텐츠에 대해 관리되는 브라우저 요구** 정책은 관리되는 경우 사용자가 Edge에서 링크를 열 수 있게 합니다.



## <a name="may-2018"></a>2018년 5월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="requesting-help-in-the-company-portal-for-windows-10"></a>Windows 10용 회사 포털에서 도움말 요청 
<!--1874137--> 이제 사용자가 문제에 대한 도움을 받기 위해 워크플로를 시작할 때 Windows 10용 회사 포털에서 Microsoft로 직접 앱 로그를 보낼 수 있습니다. 이 동작을 통해 Microsoft에 제기되는 문제를 더욱 쉽게 해결할 수 있습니다.  


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

#### <a name="android-for-work-and-lookout-onboarding-moved-to-intune-on-azure"></a>Azure에서 Intune으로 이동된 Android for Work 및 Lookout 온보딩
<!--2355022,2357366--> 최신 Intune 업데이트를 사용하여 Azure Portal의 Intune의 하이브리드 모바일 장치 관리 테넌트에서 Android for Work 통합 및 Lookout 모바일 위협 방어 통합을 사용하도록 설정하고 관리할 수 있습니다. 업데이트 전에 이러한 설정은 Intune 클래식(Silverlight) 포털에서만 구성할 수 있었습니다.
 
참고: Lookout은 하이브리드 환경에서 지원되는 유일한 MTD(모바일 위협 방어) 공급자입니다. 전에 다른 모든 MTD 공급자와 통합한 경우 Azure Portal의 Intune에 계속 표시됩니다. 커넥터를 삭제하는 경우 다시 추가할 수 없습니다.
 
이러한 변경은 기존 기능에 영향을 주지 않습니다. 관련 앱, 보고 및 정책을 관리하려면 Configuration Manager 콘솔을 계속 사용합니다.
 
자세한 내용은 다음 아티클을 참조하세요.
- [Android 하이브리드 장치 관리 설정](/sccm/mdm/deploy-use/enroll-hybrid-android)
- [장치, 네트워크 및 응용 프로그램 위험에 따라 회사 리소스에 대한 액세스 관리](/sccm/mdm/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)


#### <a name="support-for-new-versions-of-cisco-anyconnect-client-for-ios"></a>새 버전의 iOS용 Cisco AnyConnect 클라이언트 지원
<!--1357393--> iOS 버전 4.0.7 이상을 위한 Cisco AnyConnect를 지원할 수 있습니다. 이렇게 할 경우 기존 Cisco AnyConnect VPN 프로필에 **Cisco Legacy AnyConnect**라는 레이블이 지정되고, 계속해서 이전처럼 작동합니다. **Cisco AnyConnect** 옵션은 iOS 버전 4.0.7 이상에서 Cisco AnyConnect와 함께 작동하는 새 VPN 프로필에 사용됩니다.

  > [!Tip]  
  > iOS용 Cisco AnyConnect 4.0.07x 이상은 버전 1802에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 도입되었습니다. [업데이트 4163547](https://support.microsoft.com/help/4163547)에서 버전 1802부터 이 기능은 더 이상 시험판 기능이 아닙니다.  

> [!Note]  
> macOS VPN 프로필에는 계속해서 **Cisco Legacy AnyConnect** 옵션을 사용하세요. 



## <a name="april-2018"></a>2018년 4월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10"></a>Windows 10용 회사 포털 앱에서 Intune이 Fluent Design System에 맞게 조정됨 
<!--1195010--> Windows 10용 Intune 회사 포털 앱이 [Fluent Design System의 탐색 보기](/windows/uwp/design/basics/navigation-basics)로 업데이트되었습니다. 앱의 옆쪽에 모든 최상위 페이지의 정적 세로 목록이 표시됩니다. 링크를 클릭하여 빠르게 페이지를 보고 페이지 간에 전환할 수 있습니다. 이 업데이트는 Intune에서 더욱 공감할 수 있고 친숙한 적응형 환경을 만들려는 Microsoft의 지속적인 노력의 일부로 여러 업데이트 중 첫 번째로 선보이는 것입니다. 업데이트된 형태를 보려면 [앱 UI의 새로운 기능](/intune/whats-new-app-ui)으로 이동하세요.

#### <a name="improved-device-tiles-in-the-windows-10-company-portal"></a>Windows 10 회사 포털의 개선된 장치 타일
<!--2213364--> 저시력 사용자가 더 쉽게 액세스할 수 있고 화면 읽기 도구의 성능이 개선되도록 타일이 업데이트되었습니다.


#### <a name="test-the-company-portal-for-macos-on-virtual-machines"></a>가상 머신에서 macOS용 회사 포털 테스트
<!--2216679--> Microsoft에서는 IT 관리자가 Parallels Desktop 및 VMware Fusion에서 가상 머신의 macOS용 회사 포털 앱을 테스트하는 데 도움이 되는 지침을 게시했습니다. 자세한 내용은 [테스트를 위해 macOS 가상 머신 등록](/intune/macos-enroll#enroll-virtual-macos-machines-for-testing)을 참조하세요.


#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos"></a>macOS용 회사 포털 앱에 진단 보고서 보내기
<!--2216677--> 사용자가 Intune 관련 오류를 보고하는 방법을 개선하기 위해 macOS 장치용 회사 포털 앱이 업데이트되었습니다. 회사 포털 앱에서 직원은 다음을 수행할 수 있습니다.

- Microsoft 개발자 팀에 직접 진단 보고서를 업로드합니다.
- 인시던트 ID를 회사의 IT 지원 팀에게 이메일로 전송합니다.


#### <a name="updated-help-experience-on-company-portal-app-for-android"></a>Android용 회사 포털 앱의 도움말 환경 업데이트 
<!--1631531--> Android 플랫폼에 대한 모범 사례에 맞게 Android용 회사 포털 앱의 도움말 환경을 업데이트했습니다. 이제 앱에서 문제가 발생하면 **메뉴** >  **도움말**를 탭하고 다음을 수행할 수 있습니다.
- 진단 로그를 Microsoft에 업로드합니다.
- 회사 지원 담당자에게 문제와 인시던트 ID를 설명하는 메일을 보냅니다.


#### <a name="update-where-to-configure-your-app-protection-policies"></a>앱 보호 정책을 구성하는 위치 업데이트 
<!--2144597--> Microsoft Intune 서비스의 Azure Portal에서는 **Intune 앱 보호** 영역에서 **모바일 앱** 섹션으로 일시적으로 리디렉션됩니다. 모든 앱 보호 정책은 앱 구성 아래 Intune의 **모바일 앱** 섹션에 이미 있습니다. Intune 앱 보호로 이동하는 대신 바로 Intune으로 이동하세요. 2018년 4월에 리디렉션을 중지하고 **Intune 앱 보호**를 완전히 제거합니다. 이 시간 이후로는 Intune 내 앱 보호 정책의 위치가 하나만 있게 됩니다. 

**이 변경 사항은 어떤 영향을 미치나요?** 이 변경 사항은 Intune 독립형 고객과 하이브리드(Configuration Manager와 Intune) 고객 모두에 영향을 줍니다. 이 통합은 클라우드 관리 관리를 단순화하는 데 도움이 됩니다.

**이러한 변경에 대비하려면 어떻게 해야 하나요?** **Intune 앱 보호** 대신 **Intune**을 즐겨찾기로 태그합니다. Intune 내의 **모바일 앱** 영역에서 앱 보호 정책 워크플로를 숙지합니다. 짧은 기간 동안 리디렉션한 다음, **앱 보호**를 제거합니다. 모든 앱 보호 정책은 이미 Intune에 있으며 조건부 액세스 정책을 수정할 수 있습니다. 조건부 액세스 정책 수정에 대한 자세한 내용은 [Azure Active Directory의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)를 참조하세요. 자세한 내용은 [앱 보호 정책이란?](https://docs.microsoft.com/intune/app-protection-policy)을 참조하세요. 




#### <a name="user-experience-update-for-the-company-portal-app-for-ios"></a>iOS용 회사 포털 앱의 사용자 환경 업데이트 
<!--1412866--> iOS용 회사 포털 앱에 대한 주요 사용자 환경 업데이트가 릴리스되었습니다. 이 업데이트는 현대적인 모양과 느낌을 포함하여 시각적으로 완전히 새롭게 설계했습니다. 앱의 기능은 유지하면서도 유용성과 접근성을 향상시켰습니다.  

또한 다음을 확인할 수 있습니다.
- iPhone X 지원.
- 더 빨라진 앱 시작과 응답 로드로 사용자 시간 단축.
- 사용자에게 최신 상태 정보를 제공하는 추가 진행률 표시줄.
- 사용자가 로그를 업로드하는 방식의 향상으로, 문제 발생 시 이를 보고하기가 더 쉬워짐.  

업데이트된 형태를 보려면 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)으로 이동하세요.



## <a name="march-2018"></a>2018년 3월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="windows-company-portal-send-feedback-option-may-no-longer-work"></a>Windows 회사 포털 피드백 보내기 옵션이 더 이상 작동하지 않을 수 있음
<!--2070166--> Windows 회사 포털 앱에는 사용자가 앱에 대한 피드백을 Microsoft에 보낼 수 있는 '피드백 보내기' 옵션이 있습니다. 2018년 4월 30일부터 이 옵션은 Windows 10 버전 1607 이상에서 실행되는 Windows 10 회사 포털 앱에서만 계속 지원됩니다.   

**이 변경 사항은 어떤 영향을 미치나요?**

최종 사용자용 Windows 회사 포털 앱이 설치되지 않은 경우 이 메시지를 무시해 주세요.

최종 사용자가 회사 포털 앱을 사용 중인 경우 4월 30일부터 다음 시나리오에서 앱의 '피드백 보내기' 단추가 더 이상 작동하지 않습니다.  

 - Windows 10 버전 1507 및 버전 1511의 Windows 10 회사 포털 앱  

 - Windows Phone 8.1 회사 포털 앱  

관련 장치에서 '피드백 보내기' 옵션을 사용하면 오류가 발생하고 다시 시도하더라도 마찬가지입니다. 이러한 플랫폼의 경험에 대한 피드백을 Microsoft로 보내려면 아래에 나열된 대체 피드백 채널을 사용합니다.

**이러한 변경에 대비하려면 어떻게 해야 하나요?**

이 변경 사항을 최종 사용자에게 알리고 필요한 경우 모든 사용자 지침을 업데이트하세요. 

Windows Phone 8.1, Windows 10 버전 1507 및 Windows 10 버전 1511에서 회사 포털을 사용하는 최종 사용자에게 두 가지 대체 피드백 채널을 사용할 수 있음을 알리세요. 최종 사용자는 다음과 같이 할 수 있습니다.  

- Windows 10에서 피드백 허브 앱 사용  
- WinCPfeedback@microsoft.com으로 이메일 보내기  

Windows 10 버전 1607 이상의 최종 사용자에게 Microsoft Store에 있는 Windows 회사 포털의 최신 버전으로 업데이트하도록 요청하세요.



#### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview"></a>Azure Active Directory 웹 사이트는 Intune Managed Browser 앱이 필요하고 Managed Browser(공개 미리 보기)에 대한 Single Sign-On을 지원할 수 있습니다.
<!-- 710595 --> 이제 Azure AD(Azure Active Directory)를 사용하여 모바일 장치의 Intune Managed Browser 앱에 대한 웹 사이트 액세스를 제한할 수 있습니다. Managed Browser에서 웹 사이트 데이터는 안전하게 유지되고 최종 사용자 개인 데이터와 분리됩니다. 또한 Managed Browser는 Azure AD가 보호하는 사이트에 대해 Single Sign-On 기능을 지원합니다. Intune에서 관리하는 다른 앱이 있는 장치에서 Managed Browser를 사용하거나 Managed Browser에 로그인하면 Managed Browser가 Azure AD로 보호되는 회사 사이트에 액세스할 수 있으며 사용자는 자격 증명을 입력하지 않아도 됩니다. 이 기능은 OWA(Outlook Web Access) 및 SharePoint Online과 같은 사이트뿐만 아니라 Azure App Proxy를 통해 액세스되는 인트라넷 리소스와 같은 다른 회사 사이트에도 적용됩니다.



## <a name="february-2018"></a>2018년 2월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **장치 등록 관리자를 사용하는 등록에 대한 macOS 회사 포털 지원**  
    이제 macOS 회사 포털에 등록할 때 사용자가 장치 등록 관리자를 사용할 수 있습니다.
    <!-- 1352411 -->


## <a name="january-2018"></a>2018년 1월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **Android for Work용 회사 포털 앱 승인**  
  조직에서 Android for Work를 사용하는 경우 Android용 회사 포털 앱을 수동으로 승인하세요. 그런 다음, 관리되는 Google Play 스토어에서 자동 업데이트를 계속 받습니다.
  <!--1797090 -->  

- **Azure Portal에서만 Intune에 대한 조건부 액세스 정책 사용 가능**   
  이 릴리스부터 [Azure Portal](https://portal.azure.com)의 **Azure Active Directory** > **조건부 액세스**에서 조건부 액세스 정책을 구성하고 관리해야 합니다. 편의를 위해 **Intune** > **조건부 액세스**를 통해 Azure Portal의 Intune에서 이러한 설정에도 액세스할 수 있습니다.
  <!-- 1737088 1634311 --> 

- **호환성 메일에 대한 업데이트**    
  비호환 장치를 보고하는 이메일이 전송되는 경우 비호환 장치에 대한 세부 정보가 포함됩니다. 
  <!--1637547 -->

- **Android 장치의 “해결” 작업을 위한 새로운 기능**    
  Android용 회사 포털 앱은 **장치 설정 업데이트**에 대한 "해결" 작업을 확장하여 [장치 암호화 문제](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android)를 해결합니다.
  <!--1583480-->

- **Windows 10용 회사 포털 앱에서 원격 잠금 사용 가능**    
  이제 최종 사용자가 Windows 10용 회사 포털 앱에서 자신의 장치를 원격으로 잠글 수 있습니다. 이 작업은 현재 사용 중인 로컬 장치에는 표시되지 않습니다.
  <!--676506-->

- **Windows 10용 회사 포털 앱의 규정 준수 문제를 간단하게 해결**   
  Windows 장치를 사용하는 최종 사용자는 회사 포털 앱에서 비준수 이유를 탭할 수 있습니다. 이 경우 가능하면 설정 앱의 올바른 위치로 바로 이동하여 문제를 해결합니다.
  <!--676546-->    



## <a name="december-2017"></a>2017년 12월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **이제 Android Enterprise에 사용 가능한 응용 프로그램 배포가 지원됩니다.**    
  이제 Android Enterprise(이전의 Android for Work) 앱을 **필수** 외에도 **사용 가능**으로 배포할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Android 응용 프로그램 만들기](/sccm/mdm/deploy-use/creating-android-applications)를 참조하세요.



## <a name="november-2017"></a>2017년 11월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **관리되는 앱에서 텍스트 프로토콜 허용**  
  Intune 앱 SDK로 관리되는 앱에서 SMS 메시지를 보낼 수 있습니다.
  <!-- 1414050  -->   

- **macOS용 회사 포털 앱 사용 가능**   
  macOS용 Intune 회사 포털에는 업데이트된 환경이 있습니다. 이 환경은 사용자가 등록한 모든 장치에 필요한 모든 정보 및 준수 알림을 분명히 표시하도록 최적화되었습니다. 또한 Intune 회사 포털이 장치에 배포되면 macOS용 Microsoft 자동 업데이트에서 해당 업데이트를 제공합니다. macOS 장치에서 Intune 회사 포털 웹 사이트에 로그인하여 새 macOS용 Intune 회사 포털을 다운로드하세요.
  <!--1541700-->   

- **Microsoft Planner가 이제 승인된 앱의 MAM(모바일 앱 관리) 목록에 포함됨**    
  iOS 및 Android용 Microsoft Planner 앱이 이제 MAM(모바일 앱 관리)의 승인된 앱에 포함됩니다. Azure Portal의 Intune 앱 보호에서 모든 테넌트까지 앱을 구성합니다. 자세한 내용은 [승인된 앱의 MAM 목록](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 참조하세요.
  <!-- 1248473 -->    

- **iOS의 관리되는 앱 로그에 액세스**    
  관리되는 브라우저를 설치한 최종 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있고 관리된 iOS 앱 문제를 해결하도록 로그를 보낼 수 있습니다.
  <!-- 1469920 -->    

  iOS 장치의 Managed Browser에서 문제 해결 모드를 사용하도록 설정하는 방법을 알아보려면 [iOS의 Managed Browser를 사용하여 관리되는 앱 로그에 액세스하는 방법](https://docs.microsoft.com/intune/app-configuration-managed-browser#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)을 참조하세요.

- **버전 2.9.0의 iOS용 회사 포털의 장치 설정 워크플로 개선**    
  iOS용 회사 포털 앱의 장치 설정 워크플로가 개선되었습니다. 언어가 사용자에게 더 친숙하고 가능한 경우 화면을 합쳤습니다. 또한 설정 텍스트 전체에서 회사 이름을 사용하여 회사에 대한 언어의 관련성을 높였습니다. 이 업데이트된 워크플로는 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-november-13-2017) 페이지에서 확인할 수 있습니다.

- **Android용 회사 포털 앱의 피드백 프롬프트**    
  Android용 회사 포털 앱에서 이제 최종 사용자 피드백을 요청합니다. 이 피드백은 Microsoft로 바로 전송되며, 최종 사용자에게 공개 Google Play 스토어에서 앱을 검토할 기회를 제공합니다. 피드백은 필수는 아니며, 사용자가 앱을 계속 사용할 수 있도록 쉽게 해제할 수 있습니다. 
  <!--1165249-->    

- **Windows 10 장치에 대해 표시되는 장치 정보를 최종 사용자에게 알리기**    
  Windows 10용 회사 포털 앱의 장치 세부 정보 화면에 **소유권 유형**이 추가되었습니다. 이 정보를 통해 사용자는 Intune 최종 사용자 문서에서 바로 개인 정보에 대한 자세한 내용을 찾을 수 있습니다. **정보** 화면에서도 이 정보를 찾을 수 있습니다.
  <!--1337920-->    

- **Android 장치에서 사용할 수 있는 새로운 ‘해결’ 작업**    
  Android용 회사 포털 앱은 _장치 설정 업데이트_ 페이지에서 ‘해결’ 작업을 소개하고 있습니다. 이 옵션을 선택하면 최종 사용자가 장치를 비준수 상태로 만든 설정으로 바로 이동됩니다. Android용 회사 포털 앱은 현재 [장치 암호](https://docs.microsoft.com/intune-user-help/set-your-pin-or-password-android), [장치 암호화](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android), [USB 디버깅](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-usb-debugging-android) 및 [알 수 없는 소스](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-unknown-sources-android) 설정에 대해 이 작업을 지원합니다. 
  <!--1583480-->    


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

- **비준수에 대한 작업**    
  이제 규정을 준수하지 않는 장치에 적용되는 작업을 시간 순으로 구성할 수 있습니다. 예를 들어 전자 메일을 통해 사용자에게 비준수 장치를 알리거나 해당 장치를 비준수 장치로 표시할 수 있습니다. 자세한 내용은 [비준수에 대한 작업 설정](/sccm/mdm/deploy-use/actions-for-noncompliance)을 참조하세요.
  <!--1321366 -->

- **새 모바일 응용 프로그램 관리 정책 설정**     
  모바일 응용 프로그램 관리 정책 설정에 다음과 같은 설정이 추가되었습니다.
  - **연락처 동기화 사용 안 함:** 앱에서 장치의 네이티브 연락처 앱에 데이터를 저장하지 않도록 방지합니다.
  - **인쇄 사용 안 함:** 앱에서 회사 또는 학교 데이터를 인쇄하지 않도록 방지합니다.
  <!-- 1324760 -->    

  새로운 앱 보호 정책 설정을 사용하려면 [Configuration Manager에서 앱 보호 정책을 사용하여 앱 보호](/sccm/mdm/deploy-use/protect-apps-using-mam-policies)를 참조하세요.

- **Windows 10 ARM64 장치 지원**     
  하이브리드 MDM(모바일 장치 관리) 시나리오는 이러한 장치를 사용할 수 있을 때 Windows 10을 실행하는 ARM64 장치에서 지원됩니다. 자세한 내용은 [Windows 10 ARM64 장치 지원](/sccm/core/plan-design/changes/whats-new-in-version-1710#windows-10-arm64-device-support)을 참조하세요.
  <!-- 1355000 -->    

- **Configuration Manager 콘솔의 VPN 프로필 환경 개선**     
  이 릴리스에서는 VPN 프로필 마법사 및 속성 페이지를 업데이트하여 선택한 플랫폼에 적절한 설정을 표시했습니다. 이 기능은 이전에 Configuration Manager Configuration Manager Technical Preview 1709에서 사용할 수 있었으며, 이제 Intune과 Configuration Manager(현재 분기) 버전 1710을 포함하는 하이브리드 배포에서 사용할 수 있습니다. 자세한 내용은 [Configuration Manager 콘솔의 VPN 프로필 환경 개선](/sccm/core/plan-design/changes/whats-new-in-version-1710#improved-vpn-profile-experience-in-configuration-manager-console)을 참조하세요.
  <!-- 1318232 -->


### <a name="new-in-configuration-manger-technical-preview-1711"></a>Configuration Manager Technical Preview 1711의 새로운 기능

- **Windows 10에 대한 새로운 준수 정책 옵션**   
  이제 Windows 10 장치의 준수 정책에 대한 새 옵션을 구성할 수 있습니다. 새 설정에는 방화벽, 사용자 계정 컨트롤, Windows Defender 바이러스 백신 및 OS 빌드 버전 관리에 대한 정책이 포함됩니다. 자세한 내용은 [Windows 10에 대한 새로운 준수 정책 옵션](/sccm/core/get-started/capabilities-in-technical-preview-1711#new-compliance-policy-options-for-windows-10)을 참조하세요.



## <a name="october-2017"></a>2017년 10월

### <a name="new-in-configuration-manager-technical-preview-1709"></a>Configuration Manager Technical Preview 1709의 새로운 기능

- **Configuration Manager 콘솔의 VPN 프로필 환경 개선**      
  이제 VPN 프로필 설정이 플랫폼에 따라 필터링됩니다. 새 VPN 프로필을 만들면 지원되는 각 플랫폼에는 플랫폼에 적합한 설정만 포함됩니다. 기존 VPN 프로필은 영향을 받지 않습니다. 이 변경에 대한 자세한 내용을 보려면 [여기](/sccm/core/get-started/capabilities-in-technical-preview-1709#improved-vpn-profile-experience-in-configuration-manager-console)를 클릭하세요.
  <!-- 1313282 -->


### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능  

- **사용자가 Android용 회사 포털 앱을 사용하여 스스로 해결책을 찾도록 지원**     
  사용자의 이해를 돕고 새로운 사용 사례에서 자체적으로 해결할 수 있도록 최종 사용자를 위한 지침이 Android용 회사 포털 앱에 추가되었습니다.
    - 최종 사용자는 추가가 허용된 장치의 최댓수에 도달한 경우, 장치를 제거하도록 [Azure Active Directory 포털](https://account.activedirectory.windowsazure.com/r/#/profile)로 안내됩니다.
    - 최종 사용자에게는 [Samsung Knox 장치에서 활성화 오류를 수정](https://go.microsoft.com/fwlink/?linkid=859718)하는 데 유용한 단계 또는 [절전 모드 끄기](https://docs.microsoft.com/intune-user-help/power-saving-mode-android)에 대한 단계가 제공됩니다. 그러한 해결책이 문제를 해결하지 못하는 경우 [Microsoft에 로그를 제출](https://docs.microsoft.com/intune-user-help/send-logs-to-microsoft-android)하는 방법에 대한 설명이 제공됩니다.
  <!-- 1573324, 1573150, 1558616, 1564878 -->      

- **Android 회사 포털의 장치 설정 진행률 표시기**    
  Android용 회사 포털 앱은 사용자가 장치를 등록하는 동안 장치 설정 진행률 표시기를 표시합니다. 이 표시기에는 “장치 설정 중...”부터 “장치 등록 중...”, “장치 등록 완료 중...”, “장치 설정 완료 중...”까지 차례로 새로운 상태가 표시됩니다.  
  <!--1565657-->    

- **iOS용 회사 포털에서 인증서 기반 인증 지원**    
  iOS용 회사 포털 앱에 CBA(인증서 기반 인증)에 대한 지원이 추가되었습니다. CBA가 있는 사용자는 사용자 이름을 입력한 다음, “인증서를 사용하여 로그인” 링크를 탭합니다. Android 및 Windows용 회사 포털 앱에는 CBA가 이미 지원됩니다. 자세한 내용은 [회사 포털 앱에 로그인](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) 페이지를 참조하세요.
  <!--1029830-->   

- **회사 포털에서 장치 설정 워크플로 개선**     
  Android용 회사 포털 앱에서 장치 설정 워크플로를 개선했습니다. 언어는 귀사를 위해 더욱 친숙하고 구체적으로 변경되었으며, 가능한 한 화면을 합쳤습니다. [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-october-2-2017) 페이지에서 이러한 개선 사항을 확인할 수 있습니다.
  <!--1490692-->     

- **Android 장치에서 연락처 액세스 요청에 대한 지침 개선**     
  최종 사용자가 Android용 회사 포털 앱을 사용하려면 연락처 권한을 수락해야 합니다. 최종 사용자가 이 액세스를 거절하는 경우 조건부 액세스 권한을 부여한다고 경고하는 앱 내 알림이 표시됩니다. 
  <!--1484985-->     

- **안전한 Android 시작을 위한 수정 사항**     
  Android 장치를 사용하는 최종 사용자는 회사 포털 앱에서 비준수 이유를 탭할 수 있습니다. 이 경우 가능하면 설정 앱의 올바른 위치로 바로 이동하여 문제를 해결합니다. 
  <!--1490712-->    

- **Android Oreo용 회사 포털 앱의 최종 사용자를 위한 추가 푸시 알림**    
  최종 사용자에게 Intune 서비스의 정책 검색처럼 Android Oreo용 회사 포털 앱이 백그라운드 작업을 수행하는 시기를 알리는 추가 알림이 표시됩니다. 이 알림을 통해 회사 포털이 장치에서 관리 작업을 수행하는 시기에 대해 최종 사용자에 대한 투명성이 증가됩니다. 이러한 기능 향상은 Android Oreo용 회사 포털 앱에 대한 전반적인 [회사 포털 UI 최적화](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)의 일부입니다. 
  <!--1475932 -->     

- **회사 프로필을 포함한 Android용 회사 포털 앱에 대한 새 동작**     
  회사 프로필을 포함한 Android for Work 장치를 등록하면 장치에서 관리 작업을 수행하는 것은 회사 프로필의 회사 포털 앱입니다. 

  개인 프로필에서 MAM 기반 앱을 사용하는 경우가 아니면 Android용 회사 포털 앱을 더 이상 사용할 수 없습니다. 회사 프로필 환경을 개선하기 위해 Intune은 회사 프로필을 등록한 후 개인 회사 포털 앱을 자동으로 숨깁니다.

  [Play 스토어에서 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)을 찾아 **사용**을 탭하여 개인 프로필에서 언제든 Android용 회사 포털 앱을 사용 설정할 수 있습니다.
  <!--1485783-->    

- **Windows 8.1 및 Windows Phone 8.1용 회사 포털이 지속 모드로 전환**    
  Windows 8.1 및 Windows Phone 8.1용 회사 포털 앱이 지속 모드로 이동 중임을 알리는 알림이 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.  
  <!--1428681-->    

- **지원되지 않는 Samsung Knox 장치 등록 차단**   
  회사 포털 앱은 지원되는 Samsung Knox 장치만 등록하려고 합니다. MDM 등록을 방해하는 KNOX 정품 인증 오류를 방지하기 위해 [Samsung이 공개한 장치 목록](https://www.samsungknox.com/knox-supported-devices/knox-workspace)에 나타나는 장치만 등록이 시도됩니다. Samsung 장치에는 다른 장치에는 없는 KNOX를 지원하는 모델 번호가 있을 수 있습니다. 구입 및 배포 전에 장치 대리점에 Knox 호환 여부를 확인하세요. 검증된 장치 목록은 [Android 및 Samsung KNOX 표준 정책 설정](https://docs.microsoft.com/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#supported-samsung-knox-standard-devices)을 참조하세요.
  <!-- 1490695 -->     

- **Android 4.3 이하에 대한 지원 종료**     
  Android 4.3 이하에 대한 지원 종료 알림이 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.
  <!--1171126, 1326920 -->     

- **등록된 장치에 표시되는 장치 정보를 최종 사용자에게 알리기**     
  모든 회사 포털 앱의 장치 세부 정보 화면에 **소유권 유형**을 추가하고 있습니다. 이 정보를 통해 사용자는 [회사가 볼 수 있는 정보](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) 문서에서 바로 개인 정보에 대한 자세한 내용을 찾을 수 있습니다. 이러한 기능 향상은 머지않아 모든 회사 포털 앱에 적용됩니다. [9월](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)에는 iOS에 대한 이 기능을 발표했습니다. 
  <!--1165314-->     



## <a name="september-2017"></a>2017년 9월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능     

- **Windows 10용 회사 포털 앱에 추가된 새로 고침 작업**    
    사용자는 Windows 10용 회사 포털 앱을 사용하여 새로 고침으로 끌어오거나 데스크톱에서 F5 키를 눌러서 앱에서 데이터를 새로 고칠 수 있습니다.
    <!-- 1132468 -->     

- **iOS에 대해 표시되는 장치 정보를 최종 사용자에게 알리기**   
    iOS용 회사 포털 앱의 [장치 세부 정보] 화면에 **소유권 유형**이 추가되었습니다. 이 정보를 통해 사용자는 Intune 최종 사용자 문서에서 바로 개인 정보에 대한 자세한 내용을 찾을 수 있습니다. [정보] 화면에서도 이 정보를 찾을 수 있습니다. 
    <!--739894-->    

- **Android용 회사 포털 앱의 구문을 쉽게 이해**   
    최종 사용자가 더 쉽게 등록할 수 있도록 만드는 새로운 텍스트를 사용하여 Android용 회사 포털 앱에 대한 등록 프로세스가 간소화되었습니다. 사용자 지정 등록 설명서가 있는 경우 새 화면을 반영하도록 업데이트합니다. [Intune 최종 사용자 앱 UI 업데이트](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017) 페이지에서 샘플 이미지를 확인할 수 있습니다.
    <!---1396349-->    

- **Windows 10 회사 포털 앱이 Windows Information Protection 허용 정책에 추가됨**    
    Windows 10 회사 포털 앱이 WIP(Windows Information Protection)를 지원하도록 업데이트되었습니다. WIP 허용 정책에 앱을 추가할 수 있습니다. 이러한 변경으로 이제 더 이상 앱을 **예외** 목록에 추가하지 않아도 됩니다. 

    단일 WIP 구성 항목만 장치에 전달할 수 있습니다. 두 개의 WIP 구성 항목이 동일한 장치를 대상으로 하는 경우 어던 WIP 정책도 적용되지 않습니다.
    <!-- 677129 -->    

- **iOS 8.0에 대한 지원 종료 알림이 추가됨**    
    iOS 8.0에 대한 지원 종료 알림이 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.



## <a name="august-2017"></a>2017년 8월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능     

- **Android 회사 포털 사용자와 앱 보호 정책 사용자의 새로운 로그인 환경**    
  이제 최종 사용자가 Android 장치를 등록하지 않고도 Android 회사 포털 앱을 사용하여 앱을 찾아보고 장치를 관리하고 IT 연락처 정보를 볼 수 있습니다. 최종 사용자가 Intune 앱 보호 정책으로 보호된 앱을 이미 사용하고 Android 회사 포털을 시작한 경우, 장치를 등록하라는 메시지도 더 이상 표시되지 않습니다.
  <!-- 621669 -->



## <a name="july-2017"></a>2017년 7월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **Android 및 Windows Phone에 대한 지원 종료 알림이 추가됨**    
    Android 및 Windows Phone 버전에 대한 지원 종료 알림이 새로 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

다음 기능은 이전에 Configuration Manager Technical Preview 릴리스에서 사용할 수 있었으며, 이제 Intune 및 Configuration Manager(현재 분기) 버전 1706을 포함하는 하이브리드 배포에서 사용할 수 있습니다.

- [Entrust 인증 기관에 대한 Entrust 지원](/sccm/core/get-started/capabilities-in-technical-preview-1706#support-for-entrust-certification-authorities)
- [새 모바일 응용 프로그램 관리 정책 설정](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-mobile-application-management-policy-settings)
- [Android for Work 공유 구성에 대한 업데이트](/sccm/core/plan-design/changes/whats-new-in-version-1706#updates-to-android-for-work-sharing-configuration)
- [새 장치 준수 정책 규칙](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-device-compliance-policy-rules)
- [Configuration Manager 클라이언트에서 관리되지 않는 Windows 10 장치에 대한 새 구성 설정](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client)
- [macOS VPN 프로필에 대한 Cisco(IPsec) 지원](/sccm/core/get-started/capabilities-in-technical-preview-1706#cisco-ipsec-support-for-macos-vpn-profiles)
- [Android 및 iOS 등록 제한](/sccm/core/plan-design/changes/whats-new-in-version-1706#android-and-ios-enrollment-restrictions) 



## <a name="june-2017"></a>2017년 6월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **MDM 기관 변경**    
  Configuration Manager 버전 1610부터 Microsoft 지원에 문의하지 않고 MDM 기관을 변경할 수 있습니다. 또한 기존 관리 장치를 등록 취소했다가 다시 등록할 필요가 없습니다. 자세한 내용은 [MDM 기관 변경](/sccm/mdm/deploy-use/change-mdm-authority)을 참조하세요.

- **Managed Browser 및 앱 프록시 통합**    
  Intune Managed Browser는 이제 Azure AD 응용 프로그램 프록시 서비스와 통합되어 사용자가 원격으로 작업하는 동안에도 내부 웹 사이트에 액세스하도록 할 수 있습니다. 브라우저의 사용자는 평소와 같이 사이트 URL을 입력하면 관리되는 브라우저에서 응용 프로그램 프록시 웹 게이트웨이를 통해 요청을 라우팅합니다. 자세한 내용은 [관리되는 브라우저 정책을 사용하여 인터넷 액세스 관리](https://docs.microsoft.com/intune/app-configuration-managed-browser)를 참조하세요.

- **Android용 회사 포털 앱에서 앱 보호 정책에 대해 새로운 최종 사용자 환경 제공**  
  고객의 의견에 따라, **회사 콘텐츠 액세스** 단추를 표시하도록 Android용 회사 포털 앱을 수정하고 있습니다. 이러한 작업은 최종 사용자가 Intune 모바일 응용 프로그램 관리의 기능인 앱 보호 정책을 지원하는 앱에만 액세스하면 될 경우 불필요하게 등록 프로세스를 거치지 않도록 하기 위한 것입니다. [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui) 페이지에서 이러한 변경 내용을 확인할 수 있습니다.

- **회사 포털을 쉽게 제거하기 위한 새 메뉴 작업**  
  사용자의 의견에 따라 Android용 회사 포털 앱에는 장치에서 회사 포털 제거를 시작하기 위한 새 메뉴 작업이 추가되었습니다. 이 작업은 사용자가 장치에서 앱을 제거할 수 있도록 Intune 관리에서 장치를 제거합니다. 이러한 변경 내용은 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui) 페이지 및 [Android 최종 사용자 설명서](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android)에서 확인할 수 있습니다.

- **Windows 10 크리에이터스 업데이트와의 앱 동기화 개선**  
  이제 Windows 10용 회사 포털 앱에서는 Windows 10 크리에이터스 업데이트(버전 1703)와의 장치에 대한 앱 설치 요청 동기화가 자동으로 시작됩니다. 이 동작으로 “동기화 보류 중” 상태일 때 앱 설치가 중단되는 문제가 줄어듭니다. 사용자는 앱 내에서 수동으로 동기화를 시작할 수도 있습니다. [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui) 페이지에서 이러한 변경 내용을 확인할 수 있습니다.

- **Windows 10 회사 포털에 대한 새로운 단계별 환경**  
  Windows 10용 회사 포털 앱에 식별되거나 등록되지 않은 장치에 대한 단계별 Intune 연습 환경이 포함됩니다. 이 새로운 환경은 Azure Active Directory에 등록(조건부 액세스 기능에 필요)하고 MDM 등록(장치 관리 기능에 필요)을 진행하는 과정을 안내하는 단계별 지침을 제공합니다. 이 단계별 안내 환경은 회사 포털 홈페이지에서 액세스할 수 있습니다. 사용자는 등록을 완료하지 않아도 앱을 계속 사용할 수 있지만 제한된 기능만 사용할 수 있습니다.

  이 업데이트는 Windows 10 1주년 업데이트(빌드 1607) 이상을 실행하는 장치에서만 볼 수 있습니다. [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui) 페이지에서 이러한 변경 내용을 확인할 수 있습니다.

- **iOS용 회사 포털 앱의 앱 타일 기능 개선**  
  회사 포털에 대해 설정한 브랜딩 색에 맞게 홈페이지의 앱 타일 디자인이 업데이트되었습니다. 자세한 내용은 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)을 참조하세요.

- **iOS용 회사 포털 앱에서 계정 선택 기능 사용 가능**  
  iOS 장치 사용자가 회사 또는 학교 계정을 사용하여 다른 Microsoft 앱에 로그인한 경우, 회사 포털에 로그인하면 새 계정 선택 기능이 표시될 수 있습니다. 자세한 내용은 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)을 참조하세요.

### <a name="new-in-configuration-manager-technical-preview-1706"></a>Configuration Manager Technical Preview 1706의 새로운 기능

- **새 Windows 구성 항목 설정**      
  새 Windows 구성 항목은 암호, 장치, 저장소 및 Microsoft Edge 설정 범주에 사용할 수 있습니다. 자세한 내용은 [새 Windows 구성 항목 설정](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-windows-configuration-item-settings)을 참조하세요.
  <!-- 1354715 -->

- **새 장치 준수 정책 규칙**   
  이전에는 Intune 독립 실행형에서만 사용할 수 있었던 준수 정책에 대해 새 옵션을 구성할 수 있습니다. 자세한 내용은 [향상된 장치 준수 정책](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-device-compliance-policy-rules)을 참조하세요.

- **Android 및 iOS 등록 제한**       
  관리자는 이제 사용자가 하이브리드 환경에서 개인 Android 또는 iOS 장치를 등록할 수 없도록 지정할 수 있습니다. 이렇게 하면 등록된 장치를 미리 선언된 회사 소유 장치 또는 장비 등록 프로그램에 등록된 iOS 장치로만 제한할 수 있습니다. 자세한 내용은 [Android 및 iOS 등록 제한](/sccm/core/get-started/capabilities-in-technical-preview-1706#android-and-ios-enrollment-restrictions)을 참조하세요.
  <!-- 1290826 -->

- **Entrust 인증 기관에 대한 지원**      
  이제 Configuration Manager가 Entrust 인증 기관을 지원합니다. 이 지원을 통해 Microsoft Intune에 등록된 장치로 PFX 인증서를 제공할 수 있습니다.    
  <!-- 1350740 -->

  Configuration Manager에서 인증서 등록 지점 역할을 추가할 때 Entrust를 인증 기관으로 구성할 수 있습니다. PFX 인증서를 발급하는 새 인증서 프로필을 추가할 때는 Microsoft 또는 Entrust 인증 기관을 선택할 수 있습니다.

  **알려진 문제**: 1706 Technical Preview에서는 PFX 인증서가 Microsoft 인증 기관에 대해 발급되지 않습니다. 이 문제는 가져온 PFX 인증서 또는 SCEP 프로필에 영향을 주지 않습니다.

- **macOS VPN 프로필에 대한 Cisco(IPSec) 지원**      
  연결 유형으로 Cisco(IPsec)를 사용하여 macOS VPN 프로필을 만들 수 있습니다. 자세한 내용은 [VPN 프로필 만들기](/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles)를 참조하세요.
  <!-- 1321367 -->



## <a name="notices"></a>알림

### <a name="plan-for-change-upcoming-macos-and-intune-password-enforcement-change"></a>변경 계획: 예정된 macOS 및 Intune 암호 강제 변경
<!--1873216--> 9월 서비스 릴리스에서 Intune은 Apple에서 새로 릴리스한 macOS 버전 10.13 이상을 실행하는 장치에 대한 "다음 인증 시 암호 변경" 설정을 통합할 계획입니다. 이 설정이 도입되기 전에는 MDM 공급자는 장치에서 규정 준수를 준수하도록 암호를 변경한 적이 있는지 확인할 방법이 없었습니다. Intune의 구성 및 규정 준수 정책은 장치에서 암호를 변경한 다음에 규정 준수로 표시되는지 유효성을 검사합니다. macOS 사용자는 해당 암호가 이미 규정을 준수하는 경우라도 이 새로운 Apple 기능을 통합하면 해당 암호를 업데이트하라는 요청을 받게 됩니다.

#### <a name="how-does-this-change-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이 변경 사항은 macOS 장치 정책이 있는 Intune 독립 실행형 또는 하이브리드 MDM 고객에게만 영향을 미칩니다. Apple은 새 인증 설정 시 암호 변경을 도입했습니다. 이제 Intune은 암호 정책을 푸시하는 경우 사용자의 암호를 규정을 준수하는 암호로 업데이트하도록 강제할 수 있습니다. 장치가 규정 준수로 표시될 때까지 회사 리소스를 차단하면 최종 사용자는 암호를 재설정할 때까지 이메일 또는 SharePoint 사이트와 같은 회사 리소스에 액세스하는 것이 차단될 수 있습니다. 나중에 구성 및 규정 준수 정책으로 모두 업데이트하면 대상 사용자에게 자신의 암호를 업데이트하도록 강제할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
기술 지원팀에게 알리려고 할 수 있습니다. 이 macOS 장치 정책을 적용하지 않으려는 경우 기존 macOS 정책을 삭제하거나 할당을 취소합니다. 이 변경 구현 전에 이뤄진 자체 고객 조사에서는 대부분의 고객이 이 변경으로 영향을 받지 않을 것이라고 나타났습니다. 최종 사용자는 일반적으로 암호를 사용하여 등록하라는 요청을 받은 후 해당 암호를 업데이트하거나 암호를 다시 설정하여 준수 상태를 유지합니다.  


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september-2018"></a>변경 계획: 2018년 9월에 Intune이 iOS 10 이상 지원으로 전환 
<!--2454656-->

2018년 9월에 Apple에서 iOS 12를 출시할 예정입니다. 출시 직후 Microsoft에서는 iOS 10 이상을 지원하도록 Intune 등록, 회사 포털 및 관리되는 브라우저를 전환할 예정입니다.

#### <a name="how-does-this-change-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?

Office 365 모바일 앱이 iOS 10 이상에서 지원되므로 OS나 장치를 이미 업그레이드했을 수도 있습니다. 그럴 경우 이 전환에 따른 영향을 없습니다.

하지만 아래 나열된 장치가 있거나 아래 나열된 장치를 등록하려는 경우 이런 장치는 iOS 9 이전 버전만 지원합니다. Intune 회사 포털에 계속 액세스하려면 9월까지 이러한 장치를 iOS 10 이상을 지원하는 장치로 업그레이드해야 합니다. 

- iPhone 4S
- iPod Touch 
- iPad 2
- iPad(3세대)
- iPad Mini(1세대)

7월부터 iOS 9 및 회사 포털이 있는 MDM 등록 장치에는 OS나 장치를 업그레이드하라는 메시지가 표시됩니다. 앱 보호 정책을 사용하는 경우에는 "최소 iOS 운영 체제 필요(경고)" 액세스 설정을 설정할 수도 있습니다.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?

조직에 영향을 받는 장치나 사용자가 있는지 확인합니다. Azure Portal의 Intune에서 **장치** > **모든 장치**로 이동하고 **OS**를 기준으로 필터링합니다.  **열**을 클릭하여 OS 버전과 같은 세부 정보를 표시합니다. 사용자에게 9월 전에 장치를 지원되는 OS 버전으로 업그레이드하도록 요청합니다.


### <a name="plan-for-change-intune-moving-to-tls-12"></a>변경 계획: Intune이 TLS 1.2로 전환

2018년 10월 31일부터 Intune에서 동급 최고의 암호화를 제공하고, 기본적으로 더 안전한 서비스를 지원하고, Microsoft Office 365 같은 다른 Microsoft 서비스에 맞추기 위해 TLS(전송 계층 보안) 프로토콜 버전 1.2를 지원합니다. Office는 이 변경 사항을 MC128929에서 전달했습니다.

#### <a name="how-does-this-change-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?

2018년 10월 31일부터 Intune에서는 TLS 프로토콜 버전 1.0 또는 1.1을 더 이상 지원하지 않습니다. 클라이언트-서버와 브라우저-서버의 어느 조합이든 Intune에 문제 없이 연결하려면 TLS 버전 1.2를 사용해야 합니다. 이 변경 사항은 Intune에서 지원하지 않지만 여전히 Intune을 통해 정책을 수신하고 TLS 버전 1.2를 사용할 수 없는 최종 사용자 장치에 영향을 미칩니다. 이러한 장치에는 Android 4.3 이전 버전을 실행하는 장치도 포함됩니다. 영향을 받는 장치 및 브라우저의 목록은 아래 링크를 참조하세요.

2018년 10월 31일 이후 이전 TLS 버전 사용과 관련된 문제가 발생하면 해결의 일환으로 TLS 1.2로 업데이트하거나 TLS 1.2를 지원하는 장치로 업데이트합니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?

사전에 환경에서 TLS 1.0 및 1.1 종속성을 제거하고 가능한 경우 운영 체제 수준에서 TLS 1.0 및 1.1을 사용하지 않도록 설정하는 것이 좋습니다. 지금 바로 TLS 1.2로의 마이그레이션 계획을 시작하세요. 현재 Intune에서 지원하지 않지만 여전히 정책을 수신할 수 있고 TLS 버전 1.2를 사용하여 통신할 수 없는 장치 목록은 아래 지원 블로그 게시물을 확인하세요. 해당 최종 사용자에게 회사 리소스에 액세스할 수 없게 된다고 알려야 합니다.

자세한 내용은 [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)(Intune이 암호화를 위해 TLS 1.2로 전환)을 참조하세요.


### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode"></a>Windows 8.1 및 Windows Phone 8.1용 회사 포털이 지속 모드로 전환 
<!--1428681-->
*2017년 10월 6일*   
 
2017년 10월부터 Windows 8.1 및 Windows Phone 8.1용 회사 포털 앱이 지속 모드로 전환됩니다. 이 모드는 앱과 기존 시나리오(예: 등록 및 준수)가 이러한 플랫폼에 대해 계속 지원됨을 의미합니다. 이러한 앱은 Microsoft Store와 같은 기존 릴리스 채널을 통해 계속 다운로드할 수 있습니다. 

지속 모드에서 이러한 앱은 중요 보안 업데이트만 받게 됩니다. 이러한 앱에 대한 추가 업데이트나 기능은 릴리스되지 않습니다. 새로운 기능을 보려면 장치를 Windows 10 또는 Windows 10 Mobile로 업데이트하는 것이 좋습니다. 

### <a name="end-of-support-for-ios-80"></a>iOS 8.0에 대한 지원 종료 
<!---1164477---> iOS용 회사 포털 앱과 관리되는 앱에서 회사 리소스에 액세스하려면 iOS 9.0 이상이 필요합니다. 9월 전에 업데이트되지 않은 장치는 회사 포털이나 이러한 앱에 더 이상 액세스할 수 없습니다. 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>플랫폼 지원 알림: Windows Phone 8.1 기본 지원은 2017년 7월 11일에 종료됩니다.
<!-- 1327781 -->
*2017년 7월 11일*

Windows Phone 8.1 플랫폼 기본 지원이 종료되어 갑니다. Windows 8.1 PC 지원은 영향을 받지 않습니다.

하이브리드 MDM에 등록된 장치를 포함하여 Intune 서비스가 관리하는 Windows Phone 8.1 장치에는 즉각적인 영향이 없습니다. 등록된 장치는 계속 작동합니다. 모든 정책, 구성 및 앱은 예상대로 작동합니다. Intune 서비스 내의 Windows Phone 8.1 플랫폼과 Windows Phone 8.1 회사 포털 앱을 대상으로 하는 향상된 기능은 없습니다.

가능하면 빨리 적합한 Windows Phone 8.1 장치를 Windows 10 Mobile로 업그레이드하는 것이 좋습니다.  

### <a name="end-of-support-for-android-43-and-lower"></a>Android 4.3 이하에 대한 지원 종료
<!---1171127--->
*2017년 7월 6일*

Android용 회사 포털 앱과 관리되는 앱이 회사 리소스에 액세스하려면 Android 4.4 이상이 필요합니다. 10월 초 이전에 업데이트되지 않은 장치는 회사 포털이나 이러한 앱에 더 이상 액세스할 수 없습니다. 12월까지 등록된 모든 장치는 12월에 강제로 사용 중지되어 회사 리소스에 액세스할 수 없게 됩니다. MDM 없이 앱 보호 정책을 사용 중인 경우 앱이 업데이트를 받지 못하며 해당 환경 품질이 시간이 흐름에 따라 저하됩니다.



## <a name="see-also"></a>참고 항목

- [과거 하이브리드 MDM 기능 및 알림](whats-new-hybrid-archive.md)
- [System Center 2012 Configuration Manager의 새로운 MDM 기능](https://technet.microsoft.com/library/mt445560.aspx)
