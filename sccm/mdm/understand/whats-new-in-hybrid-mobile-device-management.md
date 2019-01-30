---
title: 하이브리드 MDM의 새로운 기능
titleSuffix: Configuration Manager
description: Configuration Manager를 포함하는 하이브리드 배포에 사용할 수 있는 새 모바일 디바이스 관리 기능에 대해 알아봅니다.
ms.date: 01/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 84c244a959bb9a087d33410fe0605bc6ddcadfbc
ms.sourcegitcommit: a2ecd84d93f431ee77848134386fec14031aed6a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/29/2019
ms.locfileid: "55230905"
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-configuration-manager-and-microsoft-intune"></a>Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 모바일 디바이스 관리의 새로운 기능

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 System Center Configuration Manager 및 Intune을 포함하는 하이브리드 배포에 사용할 수 있는 새 MDM(모바일 디바이스 관리) 기능에 대한 세부 정보를 제공합니다.     

> [!Important]  
> 2018년 8월 14일부터 하이브리드 모바일 디바이스 관리 [기능은 사용되지 않습니다](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). 자세한 내용은 [하이브리드 MDM의 개념](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.<!--Intune feature 2683117-->  


> [!Note]    
> Azure의 Intune은 Microsoft에서 권장하는 MDM 솔루션입니다.     
> - Intune 독립 실행형에서 새로운 기능 및 업데이트에 대한 세부 정보는 [Intune의 새로운 기능](https://docs.microsoft.com/intune/whats-new)을 참조하세요.    
> - Intune 독립 실행형을 마이그레이션하는 방법에 대한 세부 정보는 [하이브리드 MDM 사용자 및 디바이스를 Intune 독립 실행형으로 마이그레이션](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)을 참조하세요.
> - Intune과 하이브리드 MDM의 UI 업데이트에 대한 세부 정보는 [Intune 최종 사용자 앱의 UI 업데이트](https://docs.microsoft.com/intune/whats-new-app-ui)를 참조하세요. 



##  <a name="compatibility-with-configuration-manager-versions"></a>Configuration Manager 버전과 호환성  

이 문서의 각 섹션에서는 세 가지 범주로 하이브리드 기능이 나열되어 있습니다. 각 범주의 기능과 다양한 Configuration Manager 버전 간의 호환성을 확인하려면 다음 지침을 따르세요.  

|기능 범주|Description|
|-|-|
|**Microsoft Intune의 새로운 기능** | 일반적으로 이 범주 아래에 나열된 모든 기능은 Intune 서비스만 필요하고 Configuration Manager의 추가 기능이 필요하지 않으므로 System Center 2012 R2 Configuration Manager 릴리스를 비롯한 모든 Configuration Manager 릴리스에서 사용할 수 있어야 합니다.|
|**Configuration Manager Technical Preview의 새로운 기능**| 이 범주 아래에 나열된 모든 기능은 지정된 Technical Preview 분기에서만 사용할 수 있습니다. 이러한 기능을 시험해보려면 기능 설명에 지정된 기술 미리 보기 버전을 설치해야 합니다. 자세한 내용은 [Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.|
|**Configuration Manager(현재 분기)의 새로운 기능**| 이 범주 아래에 나열된 모든 기능은 지정된 버전의 Configuration Manager(현재 분기)에서만 사용할 수 있습니다. 하이브리드 배포에 이전 버전의 Configuration Manager를 사용하는 경우 기능 설명에 지정된 Configuration Manager(현재 분기) 버전으로 업그레이드합니다. 자세한 내용은 [Configuration Manager로 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)를 참조하세요.|



## <a name="january-2019"></a>2019 년 1 월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="intune-app-protection-policies-ui-update"></a>Intune 앱 보호 정책 UI 업데이트 
<!--3251427--> 설정에 대 한 레이블 및 각 쉽게 이해할 수 있도록 Intune 앱 보호에 대 한 단추 변경 했습니다. 변경 내용 중 일부는 다음과 같습니다.  

- 컨트롤에서 변경 됩니다 **예** / **없음** 컨트롤을 주로 **블록** / **허용** 및**사용 안 함** / **사용** 컨트롤입니다. 레이블이 업데이트 됩니다.  

- 설정 변경, 설정 및 레이블을 side-by-side-되므로 컨트롤 더 나은 탐색을 제공 합니다.   

기본 설정 및 설정 수가 동일 하지만이 변경 이해, 탐색 하 고, 선택한 앱 보호 정책을 적용할 쉽게 자세한 설정을 활용할 수 있습니다. 자세한 내용은 [iOS 설정](https://docs.microsoft.com/intune/app-protection-policy-settings-ios#access-requirements) 하 고 [Android 설정](https://docs.microsoft.com/intune/app-protection-policy-settings-android#access-requirements)합니다.

#### <a name="tenant-status-dashboard"></a>테 넌 트 상태 대시보드
<!--1124854--> 새 [테 넌 트 상태 페이지](https://docs.microsoft.com/intune/tenant-status) 테 넌 트에 대 한 상태와 관련된 세부 정보를 볼 수 있는 단일 위치를 제공 합니다. 대시보드는 네 가지 영역으로 구분 됩니다.

- **세부 정보를 테 넌 트**: 에 테 넌 트 이름 및 위치를 MDM 기관에 포함 된 정보를 표시 총 테 넌 트에서 장치 등록 및 라이선스 수를 계산 합니다. 또한이 섹션에서는 테 넌 트에 대 한 현재 서비스 릴리스를 나열합니다.  

- **커넥터 상태**: 사용 가능한 커넥터를 구성 했 고 아직 설정 하지 않은 경우에 해당 나열할 수도 있습니다에 대 한 정보를 표시 합니다.  

    각 커넥터의 현재 상태에 따라 플래그가 표시 되며 정상, 경고 또는 비정상으로 합니다. 드릴스루 및 자세한 내용을 보거나,에 대 한 추가 정보를 구성 하려면 커넥터를 선택 합니다.  

- **Intune Service Health**: 테 넌 트에 대 한 활성 인시던트 또는 중단 하는 방법에 대 한 세부 정보를 표시합니다. 이 섹션의 정보는 Office 메시지 센터에서 직접 검색 됩니다.  

- **Intune 뉴스**: 테 넌 트의 활성 메시지를 표시합니다. 테 넌 트 최신 Intune 기능을 받으면 메시지 알림 등을 포함 합니다.  이 섹션의 정보는 Office 메시지 센터에서 직접 검색 됩니다.  

#### <a name="new-help-and-support-experience-in-company-portal-for-windows-10"></a>새 도움말 및 지원 환경을 Windows 10 용 회사 포털 
<!--1488939--> 새 회사 포털 도움말 및 지원 페이지는 사용자가 문제를 해결 하 고 앱 및 액세스 문제에 대 한 도움을 요청 하는 데 도움이 됩니다. 새 페이지에서 오류 및 진단 로그 세부 정보를 전자 메일 수 있으며 조직의 기술 지원팀 세부 정보를 찾습니다. 또한 관련 Intune 설명서에 대 한 링크를 사용 하 여 FAQ 섹션을 찾을 수 있습니다. 자세한 내용 및 스크린샷을 참조 하세요 [도움말 및 Windows 10 용 회사 포털에서에서 지원 받기](https://docs.microsoft.com/intune-user-help/help-and-support-windows-cpapp)합니다.

#### <a name="some-bitlocker-settings-support-windows-10-pro-edition"></a>Windows 10 Pro edition을 지원 하는 일부 BitLocker 설정
<!--2727036--> BitLocker를 포함 하 여 Windows 10 장치에서 endpoint protection 설정을 설정 하는 구성 항목을 만들 수 있습니다. 이 업데이트에는 일부 BitLocker 설정에 대 한 Windows 10 Professional edition에 대 한 지원을 추가합니다.

자세한 내용은 [Windows 10에 대 한 암호화 설정을](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#encryption)합니다.



## <a name="december-2018"></a>2018 년 12 월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="microsoft-auto-update-version-450-required-for-macos-devices"></a>MacOS 장치에 필요한 Microsoft 자동 업데이트 버전 4.5.0
<!--3503442--> 회사 포털 및 기타 Office 응용 프로그램에 대 한 업데이트를 받는 작업을 계속 하려면 Microsoft 자동 업데이트 4.5.0 macOS 장치를 Intune에서 관리 되는 업그레이드 해야 합니다. 사용자가 Office 앱에 대 한이 버전을 이미 있을 수도 있습니다.

#### <a name="the-intune-app-sdk-will-support-256-bit-encryption-keys"></a>Intune 앱 SDK는 256 비트 암호화 키 지원 
<!--1832174--> Android 용 Intune 앱 SDK는 이제 앱 보호 정책에 의해 암호화가 설정 된 경우 256 비트 암호화 키를 사용 합니다. 콘텐츠 및 이전 SDK 버전을 사용 하는 앱을 사용 하 여 호환성을 위해 128 비트 키의 지원을 제공 하기 위해 SDK는 계속 됩니다.

#### <a name="intune-requires-macos-1012-or-later"></a>Intune에 macOS를 10.12 이상 필요합니다. 
<!--2827778--> 이제 Intune에 macOS 10.12 이상 버전에 필요 합니다. 이전 macOS 버전을 사용 하 여 장치를 Intune에 등록 하려면 회사 포털을 사용할 수 없습니다. 지원 및 새로운 기능을 받으려면 사용자가 장치 macOS 10.12 이상으로 업그레이드 하 고 회사 포털을 최신 버전으로 업그레이드 해야 합니다.

자세한 내용은 참조 하세요. [변경 계획: Intune은 12 월에 macOS 10.12 이상을 지원](#plan-for-change-intune-supports-macos-1012-and-higher-in-december)합니다.



## <a name="november-2018"></a>2018년 11월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="new-intune-device-subscription-sku"></a>새 Intune 장치 구독 SKU
<!--3312071--> 하는 데 낮은 비용의 기업에서 장치를 관리 하는 새 장치 기반 구독 SKU 출시 되었습니다. 이 Intune 장치 SKU는 월별로 장치당 사용이 허가 됩니다. 가격 라이선스 프로그램에 따라 다릅니다. 이 제품은 직접 채널, EA (기업 계약), Microsoft 제품 및 mpsa 서비스 프로그램 (포함), 및 오픈 클라우드 솔루션 공급자 (CSP)입니다.

#### <a name="new-apps-support-with-app-protection-policies"></a>앱 보호 정책을 사용 하 여 새 앱을 지원합니다. 
<!--3330037--> 사용 하 여 다음 앱을 관리할 수 있습니다 [Intune 앱 보호 정책을](https://docs.microsoft.com/intune/app-protection-policies):

- Stream (iOS)  
- 할 일 (Android, iOS)  
- PowerApps (Android, iOS)  
- 흐름 (Android, iOS)  

다른 Intune 정책 관리 앱과 같은 이러한 앱에 대 한 회사 데이터 및 제어 데이터 전송을 보호 하기 위해 사용 하 여 앱 보호 정책입니다. 

> [!Note]  
> 흐름을 콘솔에 표시 아직 없는 경우 만들거나 모든 앱 보호 정책을 편집할 때 흐름을 추가 합니다. 선택 **더 많은 앱**를 지정 합니다 *앱 ID* 입력된 필드의 흐름에 대 한 합니다. Android 용도로 `com.microsoft.flow`를 사용 하 여 iOS 및 `com.microsoft.procsimo`합니다.  



## <a name="october-2018"></a>2018년 10월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="updates-for-application-transport-security"></a>애플리케이션 전송 보안 업데이트 
<!--748318--> Microsoft Intune은 TLS(전송 계층 보안) 1.2 이상을 지원하여 동급 최고의 암호화 기능을 제공하고, Intune의 보안을 기본적으로 강화하며, Microsoft Office 365와 같은 다른 Microsoft 서비스와 호환될 수 있도록 합니다. 이 요구 사항을 충족하기 위해 iOS 및 macOS 회사 포털은 Apple의 업데이트된 ATS(애플리케이션 전송 보안) 요구 사항(TLS 1.2 이상도 필요)을 적용합니다. ATS는 HTTPS를 통한 모든 앱 통신에 더 엄격한 보안을 적용하는 데 사용됩니다. 이 변경 사항은 iOS 및 macOS 회사 포털 앱을 사용하는 Intune 고객에게 영향을 줍니다. 자세한 내용은 [Intune moving to TLS 1.2 for encryption](https://blogs.technet.microsoft.com/intunesupport/2018/06/05/intune-moving-to-tls-1-2-for-encryption/)(Intune이 암호화를 위해 TLS 1.2로 전환)을 참조하세요.

#### <a name="remove-an-email-profile-from-a-device-even-when-theres-only-one-email-profile"></a>하나의 이메일 프로필만 있는 경우에도 디바이스에서 이메일 프로필 제거 
<!--1818139--> 이전에는 장치에 있는 유일한 이메일 프로필을 제거할 수 없었습니다. 이 업데이트를 통해 이 동작이 변경됩니다. 이제는 디바이스에 이메일 프로필이 유일한 경우에도 이메일 프로필을 삭제할 수 있습니다. 

#### <a name="remove-pkcs-and-scep-certificates-from-your-devices"></a>디바이스에서 PKCS 및 SCEP 인증서 제거 
<!--3218390--> 일부 시나리오에서는 그룹에서 정책을 제거하거나, 구성 또는 규정 준수 배포를 삭제하거나, 관리자가 기존 SCEP 및 PKCS 프로필을 업데이트하는 경우에도 PKCS 및 SCEP 인증서가 장치에 남아 있습니다. 

이 업데이트를 통해 이 동작이 변경됩니다. PKCS 및 SCEP 인증서가 디바이스에서 제거되는 경우와 이러한 인증서가 디바이스에 남아있는 시나리오가 있습니다. 

#### <a name="access-to-key-profile-properties-using-the-company-portal-app"></a>회사 포털 앱을 사용하여 주요 프로필 속성 액세스
<!--772203-->  
최종 사용자는 이제 회사 포털 앱에서 암호 재설정과 같은 주요 계정 속성 및 작업에 액세스할 수 있습니다. 

#### <a name="pin-prompt-when-you-change-fingerprints-or-face-id-on-an-ios-device"></a>iOS 디바이스에서 지문 또는 얼굴 ID를 변경할 때 표시되는 PIN 프롬프트  
<!--2637704-->  
이제 iOS 디바이스에서 생체 인식 내용을 변경한 후 PIN을 입력하라는 메시지가 사용자에게 표시됩니다. 여기에는 등록된 지문 또는 얼굴 ID의 변경이 포함됩니다. 프롬프트의 타이밍은 ‘다음 시간 이후에 액세스 요구 사항 다시 확인:’ 시간 제한의 구성 방법에 따라 다릅니다.  PIN이 설정되지 않은 경우에는 설정하라는 메시지가 사용자에게 표시됩니다.  

이 기능은 iOS에만 제공되고 iOS용 Intune 앱 SDK, 버전 8.1.1 이상을 통합하는 애플리케이션의 참여가 필요합니다. 대상 애플리케이션에 동작이 적용될 수 있도록 SDK의 통합이 필요합니다. 이 통합은 롤링 기반으로 특정 애플리케이션 팀에서 수행합니다. 참여하는 일부 앱에는 WXP, Outlook, Managed Browser 및 Yammer가 포함됩니다.

#### <a name="end-user-device-and-app-content-menu"></a>최종 사용자 디바이스 및 앱 콘텐츠 메뉴 
<!--2771453-->  
최종 사용자는 이제 디바이스와 앱에서 상황에 맞는 메뉴를 사용하여 디바이스 이름 바꾸기 또는 준수 확인 같은 일반적인 작업을 트리거할 수 있습니다. 

#### <a name="windows-company-portal-keyboard-shortcuts"></a>Windows 회사 포털 바로 가기 키
<!--2771518-->  
최종 사용자는 이제 바로 가기 키(액셀러레이터 키)를 사용하여 Windows 회사 포털에서 앱 및 디바이스 작업을 트리거할 수 있습니다.



## <a name="august-2018"></a>2018년 8월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="new-user-experience-update-for-the-company-portal-website"></a>회사 포털 웹 사이트의 새로운 사용자 환경 업데이트
<!--2000968--> 고객 피드백을 바탕으로 회사 포털 웹 사이트에 새 기능이 추가되었습니다. Android, iOS 및 Windows 디바이스의 기존 기능과 유용성이 크게 향상됩니다. 사이트의 여러 영역에 새롭고 현대화된 반응형 디자인이 적용되었습니다. 이들 영역에는 디바이스 세부 정보, 피드백 및 지원, 디바이스 개요가 들어 있습니다. 다음과 같은 개선 사항도 볼 수 있습니다.

- 모든 디바이스 플랫폼에서 간소화된 워크플로
- 향상된 디바이스 식별 및 등록 흐름
- 오류 메시지의 효율성 향상
- 전문 기술 용어는 줄이고 친근한 언어 사용
- 앱에 대한 직접 링크를 공유하는 기능
- 대규모 앱 카탈로그의 성능 개선
- 모든 사용자의 접근성 향상



## <a name="july-2018"></a>2018년 7월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="updated-intune-app-sdk-for-android-is-now-available"></a>업데이트된 Android용 Intune 앱 SDK 사용 가능
<!--2744271--> Android 9 Pie 릴리스를 지원하는 업데이트된 버전의 Android용 Intune 앱 SDK를 사용할 수 있습니다. 앱 개발자이며 Android용 Intune SDK를 사용하는 경우 업데이트된 버전의 Intune 앱 SDK를 설치하세요. 이 업데이트를 통해 Android 앱의 Intune 기능이 Android 9 Pie 디바이스에서도 예상대로 작동하도록 할 수 있습니다. 이 버전의 Intune 앱 SDK에서는 SDK 업데이트를 수행하는 기본 제공 플러그 인을 제공합니다. 통합된 기존 코드를 다시 쓸 필요가 없습니다. 자세한 내용은 [Intune SDK for Android](https://github.com/msintuneappsdk/ms-intune-app-sdk-android)(Android용 Intune SDK)를 참조하세요. 

Intune의 이전 배지 스타일을 사용하고 있는 경우 서류 가방 아이콘을 사용하도록 전환하세요. 브랜딩에 대한 자세한 내용은 [Intune App Badging System](https://github.com/msintuneappsdk/intune-app-partner-badge)(Intune 앱 배지 시스템)을 참조하세요.


#### <a name="support-for-security-enhancement-in-intune-service"></a>Intune 서비스의 보안 강화 지원
<!--2520152--> 이제 모든 할당된 준수 정책이 없는 장치가 하이브리드에서 준수되지 않음을 지정할 수 있습니다. Azure Portal의 Intune에서 이 설정을 구성합니다. 이 기능을 사용하여 내부 리소스를 보호하는 것이 좋습니다.

이 기능은 하이브리드 테넌트에서는 기본적으로 해제되어 있습니다. 이 기능을 활성화하면 할당된 준수 정책이 없는 디바이스는 비준수로 간주됩니다. 조건부 액세스도 활성화하면 이러한 디바이스는 내부 리소스에 액세스할 수 없게 됩니다. 이러한 리소스는 사용자 환경의 조건부 액세스 정책에 따라 Outlook 또는 SharePoint일 수 있습니다. 이 설정을 해제해도 이러한 디바이스는 현재와 동일한 수준의 액세스 권한을 유지합니다.

이 기능에 미치는 영향을 확인하는 데 도움이 되도록 [TechNet 갤러리의 스크립트](https://gallery.technet.microsoft.com/SQL-Query-for-Hybrid-MDM-5bcb8695)가 제공되었습니다. Configuration Manager 데이터베이스에 대해 이 스크립트를 실행하면 준수 정책의 대상이 아닌 디바이스가 나열됩니다.

자세한 내용은 다음 아티클을 참조하세요.
- [Intune 서비스의 보안 강화 기능](https://aka.ms/compliance_policies) 블로그 게시물 
- [Configuration Manager의 장치 준수 정책](/sccm/mdm/deploy-use/device-compliance-policies)

#### <a name="updates-to-out-of-compliance-messages-in-company-portal-app"></a>회사 포털 앱에서 규정에 맞지 않는 메시지에 대한 업데이트 
<!--1832222--> 장치가 규정에 맞지 않는 경우 장치 사용자에게 표시되는 메시지를 수정합니다. 메시지의 원래 의미는 유지하지만 기술 용어를 줄이고 더 친근한 언어로 업데이트합니다. 설명서와 수정 단계에 대한 링크도 새로 고쳐서 최신 상태로 유지합니다.  

다음의 텍스트는 표시되는 메시지의 개선 내용 중 한 가지 예입니다.  

- 이전: *이 장치에서 IT 관리자에 필요한 지정 된 기간 동안 Intune 서비스를 연결 하지 않았습니다. 이 문제를 해결하려면 디바이스에서 회사 포털 앱을 열고 준수 확인 단추를 클릭합니다.*  

- 이후: *장치에 로그인 한 동안 조직 검사 되지 않습니다. 연결을 다시 설정하려면 디바이스에서 회사 포털 앱을 열고 디바이스의 설정 확인을 탭하세요.*  

#### <a name="select-device-categories-by-using-the-access-work-or-school-settings"></a>회사 또는 학교 액세스 설정을 사용하여 디바이스 범주 선택 
<!--1058963--> [장치 그룹 매핑](https://docs.microsoft.com/intune/device-group-mapping)을 사용하도록 설정한 경우 이제 Windows 10에서 사용자가 **설정** > **계정** > **회사 또는 학교 액세스**의 **연결** 단추를 통해 등록할 때 장치 범주를 선택하라는 메시지가 표시됩니다.  

#### <a name="new-browsing-experiences-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱의 새 검색 환경 
<!--2317227--> 이제 Windows용 회사 포털 앱에서 앱을 검색하거나 탐색하는 경우 기존 **타일** 보기 및 새로 추가한 **세부 정보** 보기 사이를 토글합니다. 새 보기는 이름, 게시자, 게시 날짜 및 설치 상태와 같은 애플리케이션 세부 정보를 나열합니다. 

**앱** 페이지의 **설치된** 보기를 사용하면 완료 및 진행 중인 앱 설치에 대한 세부 정보를 볼 수 있습니다. 새 보기의 모습을 보려면 [UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui)을 참조하세요.

#### <a name="more-opportunities-to-sync-in-the-company-portal-app-for-windows"></a>Windows용 회사 포털 앱에서 더 많은 동기화 기회  
<!--2683177--> 이제 Windows용 회사 포털 앱을 사용하면 Windows 작업 표시줄 및 시작 메뉴에서 직접 동기화를 시작할 수 있습니다. 이 기능은 디바이스를 동기화하고 회사 리소스에 액세스하는 작업만 수행하는 경우에 특히 유용합니다. 새로운 기능에 액세스하려면 시작 메뉴 또는 작업 표시줄에 고정된 회사 포털 아이콘을 마우스 오른쪽 단추로 클릭합니다. 메뉴 옵션에서 **이 디바이스 동기화**를 선택합니다. (이 메뉴는 점프 목록이라고도 합니다.) 회사 포털은 **설정** 페이지에서 열리고 동기화를 시작합니다. 업데이트 프로시저는 [수동으로 Windows 디바이스 동기화](https://docs.microsoft.com/intune/intune-user-help/sync-your-device-manually-windows#sync-from-device-taskbar-or-start-menu)를 참조하세요.



## <a name="june-2018"></a>2018년 6월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="access-to-macos-company-portal-pre-release-build"></a>macOS 회사 포털 시험판 빌드에 액세스 
<!--1734766--> Microsoft 자동 업데이트를 사용하여 등록하고 Insider 프로그램에 참여하여 빌드를 조기에 받으세요. 등록하면 업데이트된 회사 포털을 사용해 본 이후에 최종 사용자에게 제공할 수 있습니다.

#### <a name="intune-app-protection-policies-and-microsoft-edge"></a>Intune 앱 보호 정책 및 Microsoft Edge 
<!--1818968,1818969--> 모바일 장치(iOS 및 Android)용 Microsoft Edge 브라우저는 Microsoft Intune 앱 보호 정책을 지원합니다. Edge응용 프로그램에서 회사 Azure Active Directory 계정으로 로그인하는 iOS 및 Android 디바이스의 사용자는 Intune에서 보호합니다. IOS 디바이스에서 **웹 콘텐츠에 대해 관리되는 브라우저 요구** 정책은 관리되는 경우 사용자가 Edge에서 링크를 열 수 있게 합니다.



## <a name="may-2018"></a>2018년 5월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

#### <a name="requesting-help-in-the-company-portal-for-windows-10"></a>Windows 10용 회사 포털에서 도움말 요청 
<!--1874137--> 이제 사용자가 문제에 대한 도움을 받기 위해 워크플로를 시작할 때 Windows 10용 회사 포털에서 Microsoft로 직접 앱 로그를 보낼 수 있습니다. 이 동작을 통해 Microsoft에 제기되는 문제를 더욱 쉽게 해결할 수 있습니다.  


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

#### <a name="android-for-work-and-lookout-onboarding-moved-to-intune-on-azure"></a>Azure에서 Intune으로 이동된 Android for Work 및 Lookout 온보딩
<!--2355022,2357366--> 최신 Intune 업데이트를 사용하여 Azure Portal의 Intune의 하이브리드 모바일 장치 관리 테넌트에서 Android for Work 통합 및 Lookout 모바일 위협 방어 통합을 사용하도록 설정하고 관리할 수 있습니다. 업데이트 전에 이러한 설정은 Intune 클래식(Silverlight) 포털에서만 구성할 수 있었습니다.
 
참고: Lookout에 하이브리드에 지원 되는 모바일 위협 defense (MTD) 공급자입니다. 전에 다른 모든 MTD 공급자와 통합한 경우 Azure Portal의 Intune에 계속 표시됩니다. 커넥터를 삭제하는 경우 다시 추가할 수 없습니다.
 
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

#### <a name="improved-device-tiles-in-the-windows-10-company-portal"></a>Windows 10 회사 포털의 개선된 디바이스 타일
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

관련 디바이스에서 '피드백 보내기' 옵션을 사용하면 오류가 발생하고 다시 시도하더라도 마찬가지입니다. 이러한 플랫폼의 경험에 대한 피드백을 Microsoft로 보내려면 아래에 나열된 대체 피드백 채널을 사용합니다.

**이러한 변경에 대비하려면 어떻게 해야 하나요?**

이 변경 사항을 최종 사용자에게 알리고 필요한 경우 모든 사용자 지침을 업데이트하세요. 

Windows Phone 8.1, Windows 10 버전 1507 및 Windows 10 버전 1511에서 회사 포털을 사용하는 최종 사용자에게 두 가지 대체 피드백 채널을 사용할 수 있음을 알리세요. 최종 사용자는 다음과 같이 할 수 있습니다.  

- Windows 10에서 피드백 허브 앱 사용  
- WinCPfeedback@microsoft.com으로 이메일 보내기  

Windows 10 버전 1607 이상의 최종 사용자에게 Microsoft Store에 있는 Windows 회사 포털의 최신 버전으로 업데이트하도록 요청하세요.



#### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview"></a>Azure Active Directory 웹 사이트는 Intune Managed Browser 앱이 필요하고 Managed Browser(공개 미리 보기)에 대한 Single Sign-On을 지원할 수 있습니다.
<!-- 710595 --> 이제 Azure AD(Azure Active Directory)를 사용하여 모바일 장치의 Intune Managed Browser 앱에 대한 웹 사이트 액세스를 제한할 수 있습니다. Managed Browser에서 웹 사이트 데이터는 안전하게 유지되고 최종 사용자 개인 데이터와 분리됩니다. 또한 Managed Browser는 Azure AD가 보호하는 사이트에 대해 Single Sign-On 기능을 지원합니다. Managed Browser에 로그인하거나 Intune에서 관리하는 다른 앱과 함께 디바이스에서 Managed Browser를 사용하면 사용자에게 자격 증명을 입력하지 않고도 Azure AD에서 보호되는 회사 사이트에 액세스할 수 있습니다. 이 기능은 OWA(Outlook Web Access) 및 SharePoint Online과 같은 사이트뿐만 아니라 Azure App Proxy를 통해 액세스되는 인트라넷 리소스와 같은 다른 회사 사이트에도 적용됩니다.



## <a name="february-2018"></a>2018년 2월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **장치 등록 관리자를 사용하는 등록에 대한 macOS 회사 포털 지원**  
    사용자는 macOS 회사 포털에 등록할 때 디바이스 등록 관리자를 사용할 수 있습니다.
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
  비준수 디바이스를 보고하기 위해 메일을 보낼 때 비준수 디바이스에 대한 세부 정보가 포함됩니다. 
  <!--1637547 -->

- **Android 장치의 “해결” 작업을 위한 새로운 기능**    
  Android용 회사 포털 앱은 **디바이스 설정 업데이트**에 대한 "해결" 작업을 확장하여 [디바이스 암호화 문제](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android)를 해결합니다.
  <!--1583480-->

- **Windows 10용 회사 포털 앱에서 원격 잠금 사용 가능**    
  이제 최종 사용자가 Windows 10용 회사 포털 앱에서 자신의 디바이스를 원격으로 잠글 수 있습니다. 이 작업은 현재 사용 중인 로컬 디바이스에는 표시되지 않습니다.
  <!--676506-->

- **Windows 10용 회사 포털 앱의 규정 준수 문제를 간단하게 해결**   
  Windows 디바이스를 사용하는 최종 사용자는 회사 포털 앱에서 비준수 이유를 탭할 수 있습니다. 이 경우 가능하면 설정 앱의 올바른 위치로 바로 이동하여 문제를 해결합니다.
  <!--676546-->    



## <a name="december-2017"></a>2017년 12월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **이제 Android Enterprise에 사용 가능한 응용 프로그램 배포가 지원됩니다.**    
  이제 Android Enterprise(이전의 Android for Work) 앱을 **필수** 외에도 **사용 가능**으로 배포할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Android 애플리케이션 만들기](/sccm/mdm/deploy-use/creating-android-applications)를 참조하세요.



## <a name="november-2017"></a>2017년 11월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능

- **관리되는 앱에서 텍스트 프로토콜 허용**  
  Intune 앱 SDK로 관리되는 앱에서 SMS 메시지를 보낼 수 있습니다.
  <!-- 1414050  -->   

- **macOS용 회사 포털 앱 사용 가능**   
  macOS용 Intune 회사 포털에는 업데이트된 환경이 있습니다. 이 환경은 사용자가 등록한 모든 디바이스에 필요한 모든 정보 및 준수 알림을 분명히 표시하도록 최적화되었습니다. 또한 Intune 회사 포털이 디바이스에 배포되면 macOS용 Microsoft 자동 업데이트에서 해당 업데이트를 제공합니다. macOS 디바이스에서 Intune 회사 포털 웹 사이트에 로그인하여 새 macOS용 Intune 회사 포털을 다운로드하세요.
  <!--1541700-->   

- **Microsoft Planner가 이제 승인된 앱의 MAM(모바일 앱 관리) 목록에 포함됨**    
  iOS 및 Android용 Microsoft Planner 앱이 이제 MAM(모바일 앱 관리)의 승인된 앱에 포함됩니다. Azure Portal의 Intune 앱 보호에서 모든 테넌트까지 앱을 구성합니다. 자세한 내용은 [승인된 앱의 MAM 목록](https://www.microsoft.com/cloud-platform/microsoft-intune-apps)을 참조하세요.
  <!-- 1248473 -->    

- **iOS의 관리되는 앱 로그에 액세스**    
  관리되는 브라우저를 설치한 최종 사용자는 Microsoft에서 게시한 모든 앱의 관리 상태를 볼 수 있고 관리된 iOS 앱 문제를 해결하도록 로그를 보낼 수 있습니다.
  <!-- 1469920 -->    

  iOS 디바이스의 Managed Browser에서 문제 해결 모드를 사용하도록 설정하는 방법을 알아보려면 [iOS의 Managed Browser를 사용하여 관리되는 앱 로그에 액세스하는 방법](https://docs.microsoft.com/intune/app-configuration-managed-browser#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios)을 참조하세요.

- **버전 2.9.0의 iOS용 회사 포털의 장치 설정 워크플로 개선**    
  iOS용 회사 포털 앱에서 디바이스 설정 워크플로를 개선했습니다. 언어가 사용자에게 더 친숙하고 가능한 경우 화면을 합쳤습니다. 또한 설정 텍스트 전체에서 회사 이름을 사용하여 회사에 대한 언어의 관련성을 높였습니다. 이 업데이트된 워크플로는 [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-november-13-2017) 페이지에서 확인할 수 있습니다.

- **Android용 회사 포털 앱의 피드백 프롬프트**    
  Android용 회사 포털 앱에서 이제 최종 사용자 피드백을 요청합니다. 이 피드백은 Microsoft로 바로 전송되며, 최종 사용자에게 공개 Google Play 스토어에서 앱을 검토할 기회를 제공합니다. 피드백은 필수는 아니며, 사용자가 앱을 계속 사용할 수 있도록 쉽게 해제할 수 있습니다. 
  <!--1165249-->    

- **Windows 10 장치에 대해 표시되는 장치 정보를 최종 사용자에게 알리기**    
  Windows 10용 회사 포털 앱에서 디바이스 세부 정보 화면에 **소유권 형식**을 추가했습니다. 이 정보를 통해 사용자는 Intune 최종 사용자 문서에서 바로 개인 정보에 대한 자세한 내용을 찾을 수 있습니다. **정보** 화면에서도 이 정보를 찾을 수 있습니다.
  <!--1337920-->    

- **Android 장치에서 사용할 수 있는 새로운 ‘해결’ 작업**    
  Android용 회사 포털 앱은 _디바이스 설정 업데이트_ 페이지에서 ‘해결’ 작업을 소개하고 있습니다. 이 옵션을 선택하면 최종 사용자가 디바이스를 비준수 상태로 만든 설정으로 바로 이동됩니다. Android용 회사 포털 앱은 현재 이 작업을 [디바이스 암호](https://docs.microsoft.com/intune-user-help/set-your-pin-or-password-android), [디바이스 암호화](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android), [USB 디버깅](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-usb-debugging-android) 및 [알 수 없는 소스](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-unknown-sources-android) 설정에 지원합니다. 
  <!--1583480-->    


### <a name="new-in-configuration-manager-current-branch"></a>Configuration Manager(현재 분기)의 새로운 기능

- **비준수에 대한 작업**    
  이제 규정을 준수하지 않는 디바이스에 적용되는 작업을 시간 순으로 구성할 수 있습니다. 예를 들어 전자 메일을 통해 사용자에게 비준수 디바이스를 알리거나 해당 디바이스를 비준수 디바이스로 표시할 수 있습니다. 자세한 내용은 [비준수에 대한 작업 설정](/sccm/mdm/deploy-use/actions-for-noncompliance)을 참조하세요.
  <!--1321366 -->

- **새 모바일 응용 프로그램 관리 정책 설정**     
  모바일 애플리케이션 관리 정책 설정에 다음과 같은 설정이 추가되었습니다.
  - **연락처 동기화 사용 안 함**: 앱에서 디바이스의 네이티브 연락처 앱에 데이터를 저장하지 않도록 방지합니다.
  - **인쇄 사용 안 함**: 앱에서 회사 또는 학교 데이터를 인쇄하지 않도록 방지합니다.
  <!-- 1324760 -->    

  새로운 앱 보호 정책 설정을 사용하려면 [Configuration Manager에서 앱 보호 정책을 사용하여 앱 보호](/sccm/mdm/deploy-use/protect-apps-using-mam-policies)를 참조하세요.

- **Windows 10 ARM64 장치 지원**     
  하이브리드 MDM(모바일 디바이스 관리) 시나리오는 이러한 디바이스를 사용할 수 있을 때 Windows 10을 실행하는 ARM64 디바이스에서 지원됩니다. 자세한 내용은 [Windows 10 ARM64 디바이스 지원](/sccm/core/plan-design/changes/whats-new-in-version-1710#windows-10-arm64-device-support)을 참조하세요.
  <!-- 1355000 -->    

- **Configuration Manager 콘솔의 VPN 프로필 환경 개선**     
  이 릴리스에서는 VPN 프로필 마법사 및 속성 페이지를 업데이트하여 선택한 플랫폼에 적절한 설정을 표시했습니다. 이 기능은 이전에 Configuration Manager Configuration Manager Technical Preview 1709에서 사용할 수 있었으며, 이제 Intune과 Configuration Manager(현재 분기) 버전 1710을 포함하는 하이브리드 배포에서 사용할 수 있습니다. 자세한 내용은 [Configuration Manager 콘솔의 VPN 프로필 환경 개선](/sccm/core/plan-design/changes/whats-new-in-version-1710#improved-vpn-profile-experience-in-configuration-manager-console)을 참조하세요.
  <!-- 1318232 -->


### <a name="new-in-configuration-manger-technical-preview-1711"></a>Configuration Manager Technical Preview 1711의 새로운 기능

- **Windows 10에 대한 새로운 준수 정책 옵션**   
  이제 Windows 10 디바이스의 준수 정책에 대한 새 옵션을 구성할 수 있습니다. 새 설정에는 방화벽, 사용자 계정 컨트롤, Windows Defender 바이러스 백신 및 OS 빌드 버전 관리에 대한 정책이 포함됩니다. 자세한 내용은 [Windows 10에 대한 새로운 준수 정책 옵션](/sccm/core/get-started/capabilities-in-technical-preview-1711#new-compliance-policy-options-for-windows-10)을 참조하세요.



## <a name="october-2017"></a>2017년 10월

### <a name="new-in-configuration-manager-technical-preview-1709"></a>Configuration Manager Technical Preview 1709의 새로운 기능

- **Configuration Manager 콘솔의 VPN 프로필 환경 개선**      
  이제 VPN 프로필 설정이 플랫폼에 따라 필터링됩니다. 새 VPN 프로필을 만들면 지원되는 각 플랫폼에는 플랫폼에 적합한 설정만 포함됩니다. 기존 VPN 프로필은 영향을 받지 않습니다. 이 변경에 대한 자세한 내용을 보려면 [여기](/sccm/core/get-started/capabilities-in-technical-preview-1709#improved-vpn-profile-experience-in-configuration-manager-console)를 클릭하세요.
  <!-- 1313282 -->


### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능  

- **사용자가 Android용 회사 포털 앱을 사용하여 스스로 해결책을 찾도록 지원**     
  사용자의 이해를 돕고 새로운 사용 사례에서 자체적으로 해결할 수 있도록 최종 사용자를 위한 지침이 Android용 회사 포털 앱에 추가되었습니다.
    - 최종 사용자는 추가가 허용된 디바이스의 최댓수에 도달한 경우, 디바이스를 제거하도록 [Azure Active Directory 포털](https://account.activedirectory.windowsazure.com/r/#/profile)로 안내됩니다.
    - 최종 사용자에게는 [Samsung Knox 디바이스에서 활성화 오류 수정](https://go.microsoft.com/fwlink/?linkid=859718) 또는 [절전 모드 끄기](https://docs.microsoft.com/intune-user-help/power-saving-mode-android)에 유용한 단계가 제공됩니다. 그러한 해결책이 문제를 해결하지 못하는 경우 [Microsoft에 로그를 제출](https://docs.microsoft.com/intune-user-help/send-logs-to-microsoft-android)하는 방법에 대한 설명이 제공됩니다.
  <!-- 1573324, 1573150, 1558616, 1564878 -->      

- **Android 회사 포털의 장치 설정 진행률 표시기**    
  Android용 회사 포털 앱은 사용자가 디바이스를 등록하는 동안 디바이스 설정 진행률 표시기를 표시합니다. 이 표시기에는 “디바이스 설정 중...”부터 “디바이스 등록 중...”, “디바이스 등록 완료 중...”, “디바이스 설정 완료 중...”까지 차례로 새로운 상태가 표시됩니다.  
  <!--1565657-->    

- **iOS용 회사 포털에서 인증서 기반 인증 지원**    
  iOS용 회사 포털 앱에 CBA(인증서 기반 인증)에 대한 지원이 추가되었습니다. CBA가 있는 사용자는 사용자 이름을 입력한 다음, “인증서를 사용하여 로그인” 링크를 탭합니다. Android 및 Windows용 회사 포털 앱에는 CBA가 이미 지원됩니다. 자세한 내용은 [회사 포털 앱에 로그인](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) 페이지를 참조하세요.
  <!--1029830-->   

- **회사 포털에서 장치 설정 워크플로 개선**     
  Android용 회사 포털 앱에서 디바이스 설치 워크플로를 개선했습니다. 언어는 귀사를 위해 더욱 친숙하고 구체적으로 변경되었으며, 가능한 한 화면을 합쳤습니다. [앱 UI의 새로운 기능](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-october-2-2017) 페이지에서 이러한 개선 사항을 확인할 수 있습니다.
  <!--1490692-->     

- **Android 장치에서 연락처 액세스 요청에 대한 지침 개선**     
  최종 사용자가 Android용 회사 포털 앱을 사용하려면 연락처 권한을 수락해야 합니다. 최종 사용자가 이 액세스를 거절하는 경우 조건부 액세스 권한을 부여한다고 경고하는 앱 내 알림이 표시됩니다. 
  <!--1484985-->     

- **안전한 Android 시작을 위한 수정 사항**     
  Android 디바이스를 사용하는 최종 사용자는 회사 포털 앱에서 비준수 이유를 탭할 수 있습니다. 이 경우 가능하면 설정 앱의 올바른 위치로 바로 이동하여 문제를 해결합니다. 
  <!--1490712-->    

- **Android Oreo용 회사 포털 앱의 최종 사용자를 위한 추가 푸시 알림**    
  최종 사용자에게 Intune 서비스의 정책 검색처럼 Android Oreo용 회사 포털 앱이 백그라운드 작업을 수행하는 시기를 알리는 추가 알림이 표시됩니다. 이 알림을 통해 회사 포털이 디바이스에서 관리 작업을 수행하는 시기에 대해 최종 사용자에 대한 투명성이 증가됩니다. 이러한 기능 향상은 Android Oreo용 회사 포털 앱에 대한 전반적인 [회사 포털 UI 최적화](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune)의 일부입니다. 
  <!--1475932 -->     

- **회사 프로필을 포함한 Android용 회사 포털 앱에 대한 새 동작**     
  회사 프로필을 사용하여 Android for Work 디바이스를 등록하면 회사 프로필의 회사 포털 앱이 디바이스에서 관리 작업을 수행합니다. 

  개인 프로필에서 MAM 기반 앱을 사용하는 경우가 아니면 Android용 회사 포털 앱을 더 이상 사용할 수 없습니다. 회사 프로필 환경을 개선하기 위해 Intune은 회사 프로필을 등록한 후 개인 회사 포털 앱을 자동으로 숨깁니다.

  [Play 스토어에서 회사 포털](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal)을 찾아 **사용**을 탭하여 개인 프로필에서 언제든 Android용 회사 포털 앱을 사용 설정할 수 있습니다.
  <!--1485783-->    

- **Windows 8.1 및 Windows Phone 8.1용 회사 포털이 지속 모드로 전환**    
  Windows 8.1 및 Windows Phone 8.1용 회사 포털 앱이 지속 모드로 이동 중임을 알리는 알림이 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.  
  <!--1428681-->    

- **지원되지 않는 Samsung Knox 장치 등록 차단**   
  회사 포털 앱은 지원되는 Samsung KNOX 디바이스만을 등록하려고 합니다. KNOX 정품 인증 오류로 인해 MDM 등록을 방해하지 않도록 방지하기 위해 디바이스가 [Samsung에서 게시한 디바이스 목록](https://www.samsungknox.com/knox-supported-devices/knox-workspace)을 표시하는 경우에만 디바이스 등록을 시도합니다. 일부 Samsung 디바이스에는 KNOX를 지원하는 모델 번호가 있을 수 있습니다. 구매하고 배포하기 전에 디바이스 재판매인과 함께 KNOX 호환성을 검사합니다. [Android 및 Samsung KNOX 표준 정책 설정](https://docs.microsoft.com/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#supported-samsung-knox-standard-devices)에서 확인된 디바이스의 전체 목록을 찾을 수 있습니다.
  <!-- 1490695 -->     

- **Android 4.3 이하에 대한 지원 종료**     
  Android 4.3 이하에 대한 지원 종료 알림이 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.
  <!--1171126, 1326920 -->     

- **등록된 장치에 표시되는 장치 정보를 최종 사용자에게 알리기**     
  모든 회사 포털 앱의 디바이스 세부 정보 화면에 **소유권 유형**을 추가하고 있습니다. 이 정보를 통해 사용자는 [회사가 볼 수 있는 정보](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) 문서에서 바로 개인 정보에 대한 자세한 내용을 찾을 수 있습니다. 이러한 기능 향상은 머지않아 모든 회사 포털 앱에 적용됩니다. [9월](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017)에는 iOS에 대한 이 기능을 발표했습니다. 
  <!--1165314-->     



## <a name="september-2017"></a>2017년 9월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능     

- **Windows 10용 회사 포털 앱에 추가된 새로 고침 작업**    
    사용자는 Windows 10용 회사 포털 앱을 사용하여 새로 고침으로 끌어오거나 데스크톱에서 F5 키를 눌러서 앱에서 데이터를 새로 고칠 수 있습니다.
    <!-- 1132468 -->     

- **iOS에 대해 표시되는 장치 정보를 최종 사용자에게 알리기**   
    추가한 **소유권 유형** iOS 용 회사 포털 앱에서 장치 세부 정보 화면. 이 정보를 통해 사용자는 Intune 최종 사용자 문서에서 바로 개인 정보에 대한 자세한 내용을 찾을 수 있습니다. [정보] 화면에서도 이 정보를 찾을 수 있습니다. 
    <!--739894-->    

- **Android용 회사 포털 앱의 구문을 쉽게 이해**   
    최종 사용자가 더 쉽게 등록할 수 있도록 만드는 새로운 텍스트를 사용하여 Android용 회사 포털 앱에 대한 등록 프로세스가 간소화되었습니다. 사용자 지정 등록 설명서가 있는 경우 새 화면을 반영하도록 업데이트합니다. [Intune 최종 사용자 앱 UI 업데이트](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017) 페이지에서 샘플 이미지를 확인할 수 있습니다.
    <!---1396349-->    

- **Windows 10 회사 포털 앱이 Windows Information Protection 허용 정책에 추가됨**    
    Windows 10 회사 포털 앱이 WIP(Windows Information Protection)를 지원하도록 업데이트되었습니다. WIP 허용 정책에 앱을 추가할 수 있습니다. 이러한 변경으로 이제 더 이상 앱을 **예외** 목록에 추가하지 않아도 됩니다. 

    단일 WIP 구성 항목만 디바이스에 전달할 수 있습니다. 두 개의 WIP 구성 항목이 동일한 디바이스를 대상으로 하는 경우 어던 WIP 정책도 적용되지 않습니다.
    <!-- 677129 -->    

- **iOS 8.0에 대한 지원 종료 알림이 추가됨**    
    iOS 8.0에 대한 지원 종료 알림이 추가되었습니다. 자세한 내용은 [알림](#notices)을 참조하세요.



## <a name="august-2017"></a>2017년 8월

### <a name="new-in-microsoft-intune"></a>Microsoft Intune의 새로운 기능     

- **Android 회사 포털 사용자와 앱 보호 정책 사용자의 새로운 로그인 환경**    
  이제 최종 사용자가 Android 디바이스를 등록하지 않고 Android 회사 포털 앱을 사용하여 앱을 찾아보고, 디바이스를 관리하며, IT 연락처 정보를 볼 수 있습니다. 최종 사용자가 Intune 앱 보호 정책으로 보호된 앱을 이미 사용하고 Android 회사 포털을 시작한 경우, 디바이스를 등록하라는 메시지도 더 이상 표시되지 않습니다.
  <!-- 621669 -->



## <a name="notices"></a>알림

### <a name="plan-for-change-intune-supports-macos-1012-and-higher-in-december"></a>변경 계획: Intune은 12 월에 macOS 10.12 이상을 지원합니다 
<!--2970975--> 

Apple이 macOS 10.14를 출시하므로 2018년 12월부터 Intune은 macOS 10.12 이상을 지원합니다. 

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?

12월부터 macOS 10.11 이하를 사용하는 디바이스의 사용자는 회사 포털에서는 Intune에 등록할 수 없습니다. 지원 및 새로운 기능을 계속 받으려면 macOS 10.12 이상으로 해당 디바이스를 업그레이드하고 회사 포털 앱을 최신 버전으로 업그레이드해야 합니다. 

MacOS 버전 10.12 이상은 현재 다음에서 지원됩니다. 
- MacBook(2009년 후반 이후)  
- iMac(2009년 후반 이후)
- MacBook Air(2010년 후반 이후)  
- MacBook Pro(2010년 후반 이후)  
- Mac Mini(2010년 후반 이후)  
- Mac Pro(2010년 후반 이후)  

12월 이후 위에 나열된 것 이외의 디바이스를 보유한 최종 사용자는 최신 버전의 macOS용 회사 포털 앱에 액세스할 수 없습니다. 지원되지 않는 macOS 10.12 이하 버전을 실행하는 기존에 등록된 디바이스는 계속 관리할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?

- 사용자에게 2018년 12월 전에 지원되는 OS 버전으로 디바이스를 업그레이드하도록 요청합니다.  
- 디바이스 또는 사용자가 받을 수 있는 영향에 대해 알아보려면 Azure Portal의 Intune 보고를 확인하세요. **장치** > **모든 장치**로 이동하고 **OS**를 기준으로 필터링합니다. 추가 열에 추가하면 macOS 10.11을 실행하는 디바이스를 가진 조직의 사용자를 식별하는 데 도움이 됩니다.  
- 하이브리드 MDM(모바일 디바이스 관리)를 사용 중인 경우 Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동하고 **디바이스** 노드를 선택합니다. 열을 마우스 오른쪽 단추로 클릭하고 **운영 체제** 및 **클라이언트 버전** 열을 추가합니다. 그런 다음, OS 버전별로 정렬합니다. 해당 하이브리드 MDM은 이제 사용되지 않으며, 가능한 빠른 시일 내에 Azure의 Intune으로 이동해야 합니다. 
 
#### <a name="additional-information"></a>추가 정보
자세한 내용은 [회사 포털 앱을 사용하여 Intune에서 macOS 디바이스 등록](https://docs.microsoft.com/intune-user-help/enroll-your-device-in-intune-macos-cp)을 참조하세요.


### <a name="intune-support-experience-for-premier-customers-now-in-azure-instead-of-mpo"></a>Intune 지원 MPO 대신 Azure에서 이제 고객은 프리미어 경험  
<!--2828727-->

9 월 12 월에 Microsoft 프리미어 온라인 (MPO) 포털 (premier.microsoft.com)에서 Intune 지원 요청을 만들 수는 제거할 것에 MC147649에서 발표 했습니다. 이제 약간의 지연 후 1 월의 끝에 리디렉션됩니다 지원 요청을 만드는 Azure의 Intune에만 합니다.

#### <a name="how-does-this-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
프리미어 향상을 계속 하려면 January, 종료 된 후 환경을 지원 MPO에서 지원 요청을 만들 수 없습니다. 이 작업을 수행 하려고 할 때 Azure에서 Intune로 리디렉션하는 중에 해제할 수 없습니다는 프롬프트를 표시 됩니다. 여기에 Intune 전용 Microsoft 지원에 라우팅되는 지원 요청을 만들 수 있습니다. 이러한 지원 엔지니어를 진단 하 고 적절 한 시기에 문제를 해결 합니다. MPO 포털에서 만든 Azure portal에서 지원 요청을 볼 수 없습니다.

Azure portal에는 새로운 지원 환경이 MC171941에서 최근에 발표 했습니다. 자세한 내용은 [Microsoft Intune에 대 한 지원을 받는 방법](https://aka.ms/new_support_experience)합니다.

하이브리드 MDM 또는 공동 관리를 사용 하는 경우 계속 MPO Configuration Manager에 대 한 지원 요청을 만들려면 사용 합니다. Intune에 대 한 지원 요청을 만들려면 Azure portal을 사용 합니다. 하이브리드 MDM은 이제 사용되지 않으며, 가능한 빠른 시일 내에 Azure의 Intune으로 이동해야 함을 기억하세요. 자세한 내용은 [하이브리드 모바일 디바이스 관리를 Azure의 Intune으로 이동](https://aka.ms/hybrid_notification)을 참조하세요.

전역 관리자, Intune 서비스 관리자 및 서비스 지원 관리자 역할이 있는 사용자만 Azure portal에서 지원 티켓을 만들 수 있습니다.

#### <a name="what-can-i-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
- Intune 관련 지원 요청에 MPO 사용을 중지합니다. Azure의 Intune을 사용하여 모든 Intune 지원 요청을 만들고 관리합니다.  
- 필요한 경우 해당 기술 지원팀에게 알리고 설명서를 업데이트합니다.  
- 사용자를 전역 관리자 또는 Intune 서비스 관리자 역할을 현재 MPO에서 지원 요청을 만드는 경우 Azure Active Directory에서 서비스 지원 관리자 역할을 할당 합니다. 사용자가 Azure Portal에서 지원 티켓을 만들려면 이러한 역할 중 하나가 필요합니다.  

#### <a name="additional-information"></a>추가 정보
자세한 내용은 [Microsoft Intune 지원 팀 블로그 게시물](https://aka.ms/IntuneSupport_MPO_to_Azure)을 참조하세요.


### <a name="plan-for-change-use-intune-on-azure-now-for-your-mdm-management"></a>변경 계획: MDM 관리를 위해 Azure에서 Intune 사용 
<!--1227338--> 1년 전, [Azure의 Intune 공개 미리 보기](https://cloudblogs.microsoft.com/enterprisemobility/2016/12/07/public-preview-of-intune-on-azure/)를 발표했으며, 6개월 전에는 Intune에 대한 [새 관리자 환경 일반 공급](https://cloudblogs.microsoft.com/enterprisemobility/2017/06/08/the-new-intune-and-conditional-access-admin-consoles-are-ga/)을 발표했습니다. 2018년 8월 31일부터는 Intune 독립 실행형을 사용하는 고객에 대해 클래식 Silverlight 콘솔에서 MDM(모바일 디바이스 관리) 기능을 해제합니다. 대신, MDM 요구 사항에 [Azure의 Intune](https://aka.ms/Intune_on_Azure)을 사용합니다. MDM용 클래식 콘솔을 아직 사용 중이라면 사용을 중지하고 Azure의 Intune을 숙지하세요. 이러한 변경으로 최종 사용자에게 어떤 영향이 있지는 않을 것입니다. Intune을 사용하는 클래식 PC 관리는 Silverlight에서 그대로 유지됩니다. 자세한 내용은 [Intune 지원 팀 블로그 게시물](https://aka.ms/Intune_on_Azure_mdm)을 참조하세요.


### <a name="plan-for-change-upcoming-macos-and-intune-password-enforcement-change"></a>변경 계획: 예정 된 macOS 및 Intune 암호 적용 변경
<!--1873216--> 9월 서비스 릴리스에서 Intune은 Apple에서 새로 릴리스한 macOS 버전 10.13 이상을 실행하는 장치에 대한 "다음 인증 시 암호 변경" 설정을 통합할 계획입니다. 이 설정이 도입되기 전에는 MDM 공급자는 디바이스에서 규정 준수를 준수하도록 암호를 변경한 적이 있는지 확인할 방법이 없었습니다. Intune의 구성 및 규정 준수 정책은 디바이스에서 암호를 변경한 다음에 규정 준수로 표시되는지 유효성을 검사합니다. macOS 사용자는 해당 암호가 이미 규정을 준수하는 경우라도 이 새로운 Apple 기능을 통합하면 해당 암호를 업데이트하라는 요청을 받게 됩니다.

#### <a name="how-does-this-change-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?
이 변경 사항은 macOS 디바이스 정책이 있는 Intune 독립 실행형 또는 하이브리드 MDM 고객에게만 영향을 미칩니다. Apple은 새 인증 설정 시 암호 변경을 도입했습니다. 이제 Intune은 암호 정책을 푸시하는 경우 사용자의 암호를 규정을 준수하는 암호로 업데이트하도록 강제할 수 있습니다. 디바이스가 규정 준수로 표시될 때까지 회사 리소스를 차단하면 최종 사용자는 암호를 재설정할 때까지 이메일 또는 SharePoint 사이트와 같은 회사 리소스에 액세스하는 것이 차단될 수 있습니다. 나중에 구성 및 규정 준수 정책으로 모두 업데이트하면 대상 사용자에게 자신의 암호를 업데이트하도록 강제할 수 있습니다.

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?
기술 지원팀에게 알리려고 할 수 있습니다. 이 macOS 디바이스 정책을 적용하지 않으려는 경우 기존 macOS 정책을 삭제하거나 할당을 취소합니다. 이 변경 구현 전에 이뤄진 자체 고객 조사에서는 대부분의 고객이 이 변경으로 영향을 받지 않을 것이라고 나타났습니다. 최종 사용자는 일반적으로 암호를 사용하여 등록하라는 요청을 받은 후 해당 암호를 업데이트하거나 암호를 다시 설정하여 준수 상태를 유지합니다.  


### <a name="plan-for-change-intune-moving-to-support-ios-10-and-later-in-september-2018"></a>변경 계획: 2018 년 9 월에에서 iOS 10 이상이 지원 이동 Intune 
<!--2454656-->

2018년 9월에 Apple에서 iOS 12를 출시할 예정입니다. 출시 직후 Microsoft에서는 iOS 10 이상을 지원하도록 Intune 등록, 회사 포털 및 관리되는 브라우저를 전환할 예정입니다.

#### <a name="how-does-this-change-affect-me"></a>이 변경 사항은 어떤 영향을 미치나요?

Office 365 모바일 앱은 iOS 10 이상에서 지원되므로 OS 또는 디바이스를 이미 업그레이드했을 수도 있습니다. 그럴 경우 이 전환에 따른 영향을 없습니다.

하지만 아래 나열된 디바이스가 있거나 아래 나열된 디바이스를 등록하려는 경우 이런 디바이스는 iOS 9 이전 버전만 지원합니다. Intune 회사 포털에 계속 액세스하려면 9월까지 이러한 디바이스를 iOS 10 이상을 지원하는 디바이스로 업그레이드해야 합니다. 

- iPhone 4S
- iPod Touch 
- iPad 2
- iPad(3세대)
- iPad Mini(1세대)

7월부터 iOS 9 및 회사 포털 모두를 사용하는 MDM 등록 디바이스에는 해당 OS 또는 디바이스를 업그레이드하라는 메시지가 표시됩니다. 앱 보호 정책을 사용하는 경우에는 "최소 iOS 운영 체제 필요(경고)" 액세스 설정을 설정할 수도 있습니다.  

#### <a name="what-do-i-need-to-do-to-prepare-for-this-change"></a>이러한 변경에 대비하려면 어떻게 해야 하나요?

조직에서 영향을 받는 디바이스 또는 사용자를 확인합니다. Azure Portal의 Intune에서 **디바이스** > **모든 디바이스**로 이동하고 **OS**를 기준으로 필터링합니다.  **열**을 클릭하여 OS 버전과 같은 세부 정보를 표시합니다. 사용자는 9월 전에 지원되는 OS 버전으로 자신의 디바이스를 업그레이드하도록 요청합니다.


### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode"></a>Windows 8.1 및 Windows Phone 8.1용 회사 포털이 지속 모드로 전환 
<!--1428681-->
*2017년 10월 6일*   
 
2017년 10월부터 Windows 8.1 및 Windows Phone 8.1용 회사 포털 앱이 지속 모드로 전환됩니다. 이 모드는 앱과 기존 시나리오(예: 등록 및 준수)가 이러한 플랫폼에 대해 계속 지원됨을 의미합니다. 이러한 앱은 Microsoft Store와 같은 기존 릴리스 채널을 통해 계속 다운로드할 수 있습니다. 

지속 모드에서 이러한 앱은 중요 보안 업데이트만 받게 됩니다. 이러한 앱에 대한 추가 업데이트나 기능은 릴리스되지 않습니다. 새 기능의 경우 디바이스를 Windows 10 또는 Windows 10 Mobile로 업데이트하는 것이 좋습니다. 

### <a name="end-of-support-for-ios-80"></a>iOS 8.0에 대한 지원 종료 
<!---1164477---> iOS용 회사 포털 앱과 관리되는 앱에서 회사 리소스에 액세스하려면 iOS 9.0 이상이 필요합니다. 9월 전에 업데이트되지 않은 디바이스는 회사 포털이나 이러한 앱에 더 이상 액세스할 수 없습니다. 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>플랫폼 지원 미리 알림: Windows Phone 8.1 기본 지원이 2017 년 7 월 11 일 종료
<!-- 1327781 -->
*2017년 7월 11일*

Windows Phone 8.1 플랫폼 기본 지원이 종료되어 갑니다. Windows 8.1 PC 지원은 영향을 받지 않습니다.

하이브리드 MDM에 등록된 디바이스를 포함하여 Intune 서비스가 관리하는 Windows Phone 8.1 디바이스에는 즉각적인 영향이 없습니다. 등록된 디바이스는 계속 작동합니다. 모든 정책, 구성 및 앱은 예상대로 작동합니다. Intune 서비스 내의 Windows Phone 8.1 플랫폼과 Windows Phone 8.1 회사 포털 앱을 대상으로 하는 향상된 기능은 없습니다.

가능하면 빨리 해당 Windows Phone 8.1 디바이스를 Windows 10 Mobile로 업그레이드하는 것이 좋습니다.  

### <a name="end-of-support-for-android-43-and-lower"></a>Android 4.3 이하에 대한 지원 종료
<!---1171127--->
*2017년 7월 6일*

Android용 회사 포털 앱과 관리되는 앱이 회사 리소스에 액세스하려면 Android 4.4 이상이 필요합니다. 10월 초 이전에 업데이트되지 않은 디바이스는 회사 포털이나 이러한 앱에 더 이상 액세스할 수 없습니다. 12월까지 등록된 모든 디바이스는 12월에 강제로 사용 중지되어 회사 리소스에 액세스할 수 없게 됩니다. MDM 없이 앱 보호 정책을 사용 중인 경우 앱이 업데이트를 받지 못하며 해당 환경 품질이 시간이 흐름에 따라 저하됩니다.



## <a name="see-also"></a>관련 항목

- [과거 하이브리드 MDM 기능 및 알림](whats-new-hybrid-archive.md)
- [System Center 2012 Configuration Manager의 새로운 MDM 기능](https://technet.microsoft.com/library/mt445560.aspx)
