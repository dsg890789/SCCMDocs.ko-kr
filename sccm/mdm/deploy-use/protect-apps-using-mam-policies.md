---
title: 모바일 애플리케이션 관리 정책을 사용하여 앱 보호
titleSuffix: Configuration Manager
description: 회사 규정 준수 및 보안 정책에 맞도록 배포하는 앱의 기능을 수정합니다.
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 28115475-e563-4e16-bf30-f4c9fe704754
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e410e50d05a0f190e3dfdc87df066b5ebce92321
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32351169"
---
# <a name="protect-apps-using-mobile-application-management-policies-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 모바일 애플리케이션 관리 정책을 사용하여 앱 보호

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 애플리케이션 관리 정책을 사용하면 배포하는 앱의 기능을 회사의 규정 준수 및 보안 정책에 맞게 수정할 수 있습니다. 예를 들어 제한된 앱 내에서의 잘라내기/복사/붙여넣기 작업을 제한하거나 모든 URL을 Managed Browser 안에서 열도록 앱을 구성할 수 있습니다. 앱 관리 정책은 다음 장치를 지원합니다.  

-   Android 4 이상을 실행하는 디바이스  

-   iOS 9 이상을 실행하는 디바이스  

모바일 앱 관리 정책을 사용하여 Intune으로 관리되지 않는 디바이스의 앱을 보호할 수도 있습니다. 이 새 기능을 사용하여 Office 365 서비스에 연결하는 앱에 모바일 앱 관리 정책을 적용할 수 있습니다. 온-프레미스 Exchange 또는 SharePoint에 연결하는 앱에 대해서는 지원되지 않습니다.  

이 새 기능을 사용하려면 Azure Preview 포털을 사용해야 합니다. 다음 항목은 시작하는 데 도움이 될 수 있습니다.  
-   [Azure 포털에서 모바일 앱 관리 정책 시작](https://technet.microsoft.com/library/mt627830.aspx)  
-   [Microsoft Intune으로 모바일 앱 관리 정책 만들기 및 배포](https://technet.microsoft.com/library/mt627829.aspx)  

 애플리케이션 관리 정책은 Configuration Manager의 구성 항목 및 기준과 달리 직접 배포하지 않습니다. 대신 제한할 애플리케이션 배포 유형과 정책을 연결합니다. 디바이스에서 앱 배포 유형을 배포하고 설치하면 지정한 설정이 적용됩니다.  

앱에 제한을 적용하려면 Microsoft Intune 앱 SDK(소프트웨어 개발 키트)를 통합해야 합니다. 이러한 유형의 앱은 두 가지 방법으로 얻을 수 있습니다.  

-   **정책 관리 앱 사용**(Android 및 iOS): 이러한 앱에는 앱 SDK가 기본으로 제공됩니다. 이 유형의 앱을 추가하려면 iTunes 스토어, Google Play 등의 앱 스토어에 있는 앱의 링크를 지정합니다. 이러한 앱 유형은 추가로 처리할 필요가 없습니다. iOS 및 Android 디바이스에 대해 사용 가능한 정책 관리 앱의 목록은 [Microsoft Intune 모바일 응용 프로그램 관리 정책용 관리되는 앱](https://technet.microsoft.com/library/dn708489.aspx)을 참조하세요.  

-   **"래핑된" 앱 사용**(Android 및 iOS): 이러한 앱은 **Microsoft Intune 앱 래핑 도구**를 사용하여 앱 SDK를 포함하도록 다시 패키지됩니다. 이 도구는 일반적으로 사내에서 작성된 회사 앱을 처리하는 데 사용되며, 앱 스토어에서 다운로드한 앱을 처리하는 데 사용할 수는 없습니다. 자세한 내용은 다음 문서를 참조하세요.
    - [Microsoft Intune 앱 래핑 도구를 사용하여 모바일 응용 프로그램 관리용 iOS 앱 준비](https://technet.microsoft.com/library/dn878028.aspx)

    - [Microsoft Intune 앱 래핑 도구를 사용하여 모바일 응용 프로그램 관리용 Android 앱 준비](https://technet.microsoft.com/library/mt147413.aspx)  

## <a name="create-and-deploy-an-app-with-a-mobile-application-management-policy"></a>모바일 애플리케이션 관리 정책을 사용하여 앱 만들기 및 배포  

##  <a name="step-1-obtain-the-link-to-a-policy-managed-app-or-create-a-wrapped-app"></a>1단계: 정책으로 관리되는 앱의 링크를 가져오거나 래핑된 앱 만들기  

-   **정책으로 관리되는 앱의 링크를 가져오려면**: 배포하려는 정책으로 관리되는 앱의 URL을 앱 스토어에서 찾아서 적어 둡니다.  

     예를 들어 iPad용 Microsoft Word 앱의 URL은 **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**  

-   **래핑된 앱을 만들려면**: [Microsoft Intune 앱 래핑 도구를 사용한 모바일 응용 프로그램 관리를 위해 iOS 앱 준비](https://technet.microsoft.com/library/dn878028.aspx) 및 [Microsoft Intune 앱 래핑 도구를 사용한 모바일 응용 프로그램 관리를 위해 Android 앱 준비](https://technet.microsoft.com/library/mt147413.aspx) 항목의 정보에 따라 래핑된 앱을 만듭니다.  

     이 도구는 처리된 앱 및 연결된 매니페스트 파일을 만듭니다. 앱을 포함하는 Configuration Manager 애플리케이션을 만들 때 이러한 파일을 사용합니다.  

##  <a name="step-2-create-a-configuration-manager-application-that-contains-an-app"></a>2단계: 앱이 포함된 Configuration Manager 애플리케이션 만들기  
 Configuration Manager 애플리케이션을 만드는 절차는 정책 관리 앱(외부 링크)을 사용하는지 아니면 iOS용 Microsoft Intune 앱 래핑 도구(iOS용 앱 패키지)를 사용하여 만든 앱을 사용하는지에 따라 달라집니다. 다음 절차 중 하나에 따라 Configuration Manager 애플리케이션을 만듭니다.  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 선택하여 **응용 프로그램 만들기** 마법사를 엽니다.  

4.  **일반** 페이지에서 **설치 파일에서 이 응용 프로그램에 대한 정보 자동 검색**을 선택합니다.  

5.  **유형** 드롭다운 목록에서 **iOS용 앱 패키지(\*.ipa 파일)를 선택합니다.**  

6.  **찾아보기**를 선택하여 가져올 앱 패키지를 선택하고 **다음**을 선택합니다.  

7.  **일반 정보** 페이지에서 회사 포털에서 사용자에게 표시할 설명적 텍스트와 범주 정보를 입력합니다.  

8.  마법사를 완료합니다.  

 **소프트웨어 라이브러리** 작업 영역의 **응용 프로그램** 노드에 새 응용 프로그램이 표시됩니다.  

### <a name="create-an-application-that-contains-a-link-to-a-policy-managed-app"></a>정책 관리 앱의 링크를 포함하는 애플리케이션 만들기  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 선택하여 **응용 프로그램 만들기** 마법사를 엽니다.  

4.  **일반** 페이지에서 **설치 파일에서 이 응용 프로그램에 대한 정보 자동 검색**을 선택합니다.  

5.  **유형** 드롭다운 목록에서 다음 중 하나를 선택합니다.  

    -   iOS: **앱 스토어의 iOS용 앱 패키지**  

    -   Android: **Google Play의 Android용 앱 패키지**  

6.  1단계의 앱에 대해 URL을 입력하고 **다음**을 선택합니다.  

7.  **일반 정보** 페이지에서 회사 포털에서 사용자에게 표시할 설명적 텍스트와 범주 정보를 입력합니다.  

8.  마법사를 완료합니다.  

 **소프트웨어 라이브러리** 작업 영역의 **응용 프로그램** 노드에 새 응용 프로그램이 표시됩니다.  

##  <a name="step-3-create-an-application-management-policy"></a>3단계: 애플리케이션 관리 정책 만들기  
 다음으로는 애플리케이션과 연결할 애플리케이션 관리 정책을 만듭니다. 일반 정책 또는 관리 브라우저 정책을 만들 수 있습니다.  

1)  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램 관리 정책**을 선택합니다.  

2)  **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 관리 정책 만들기**를 선택합니다.  

3)  **일반** 페이지에서 정책의 이름과 설명을 입력하고 **다음**을 선택합니다.  

4)  **정책 형식** 페이지에서 이 정책의 정책 형식과 플랫폼을 선택하고 **다음**을 선택합니다. 다음과 같은 정책 형식을 사용할 수 있습니다.  

-   **일반**: 일반 정책을 사용하는 경우 회사 규정 준수 및 보안 정책에 맞도록 배포하는 앱의 기능을 수정할 수 있습니다. 예를 들어 제한된 앱 내의 잘라내기, 복사 및 붙여넣기 작업을 제한할 수 있습니다.  

-   **Managed Browser**: Managed Browser 정책을 사용하여 Managed Browser에서 URL 목록 열기를 허용할지 아니면 차단할지를 결정할 수 있습니다. 관리 브라우저 정책 형식을 사용하면 Intune Managed Browser 앱의 기능을 수정할 수 있습니다. 이 앱은 사용자가 방문할 수 있는 사이트 등 사용자가 수행할 수 있는 작업과, 브라우저 내 콘텐츠의 링크가 열리는 방법을 관리할 수 있는 웹 브라우저입니다. 자세한 내용은  [iOS용 Intune 관리 브라우저 앱](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8) 및 [Android용 Intune 관리 브라우저 앱](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en)을 참조하세요.

5)  **iOS 정책** 또는 **Android 정책** 페이지에서 아래 값을 필요한 대로 구성하고 **다음**을 선택합니다. 정책을 구성하는 디바이스 유형에 따라 옵션은 달라질 수 있습니다.  

|값|추가 정보|  
|-----------|----------------------|  
|**웹 콘텐츠가 회사에서 관리되는 브라우저에 표시되도록 제한**|앱의 모든 링크를 Managed Browser에서 열 수 있습니다. 이 옵션이 작동하려면 먼저 이 앱을 디바이스에 배포해야 합니다.|  
|**Android 백업 차단** 또는 **iTunes 및 iCloud 백업 차단**|앱의 정보를 백업할 수 없도록 설정합니다.|  
|**앱이 다른 앱으로 데이터를 전송하도록 허용**|이 앱이 데이터를 보낼 수 있는 앱을 지정합니다. 앱으로의 데이터 전송을 허용하지 않거나 다른 제한된 앱으로의 전송만을 허용하거나 어떤 앱으로든 전송하도록 허용할 수 있습니다.<br /><br /> iOS 디바이스의 경우 관리되는 앱과 관리되지 않는 앱 간의 문서 전송을 차단하려면 **관리되지 않는 다른 앱에서 관리되는 문서 허용**설정을 사용하지 않도록 설정하는 모바일 디바이스 보안 정책도 구성하고 배포해야 합니다.<br /><br /> 다른 제한된 앱으로의 전송만을 허용하도록 선택하면 개별 형식의 콘텐츠를 여는 데 Intune PDF 및 이미지 뷰어(배포한 경우)가 사용됩니다.|  
|**앱이 다른 앱의 데이터를 받도록 허용**|이 앱이 데이터를 받는 것이 가능한 앱을 지정합니다. 앱에서의 데이터 전송을 허용하지 않거나 다른 제한된 앱에서의 전송만을 허용하거나 모든 앱에서의 전송을 허용할 수 있습니다.|  
|**"다른 이름으로 저장" 차단**|이 정책을 사용하는 앱에서 **다른 이름으로 저장** 옵션을 사용할 수 없도록 설정합니다.|  
|**다른 앱에서 잘라내기, 복사 및 붙여넣기 제한**|앱에서 잘라내기, 복사 및 붙여넣기 작업을 사용할 수 있는 방법을 지정합니다. 다음 중에서 선택합니다.<br /><br /> **차단**: 이 앱과 다른 앱 간에 잘라내기, 복사 및 붙여넣기 작업을 허용하지 않습니다.<br /><br /> **정책으로 관리되는 앱**: 이 앱과 다른 제한된 앱 간에만 잘라내기, 복사 및 붙여넣기 작업을 허용합니다.<br /><br /> **정책으로 관리되는 앱에 붙여넣기**: 이 앱에서 잘라내거나 복사한 데이터를 다른 제한된 앱에 붙여넣는 작업만 허용합니다. 이 경우 모든 앱에서 잘라내거나 복사한 데이터를 이 앱에 붙여넣을 수 있습니다.<br /><br /> **모든 앱** – 이 앱에서 또는 이 앱에 대해 수행하는 잘라내기, 복사 및 붙여넣기 작업이 제한되지 않습니다.|  
|**액세스 시 단순 PIN 필요**|사용자가 이 앱을 사용하는 데 필요한 PIN을 입력해야 합니다. 사용자가 앱을 처음 실행할 때 PIN을 설정하라는 메시지가 표시됩니다.|  
|**PIN 다시 설정까지의 입력 시도 횟수**|사용자가 PIN을 다시 설정해야 하기 전까지 PIN을 입력할 수 있는 횟수를 지정합니다.|  
|**액세스 시 회사 자격 증명 필요**|사용자가 앱에 액세스하려면 회사 로그인 정보를 입력해야 합니다.|  
|**액세스 시 회사 정책을 준수하는 장치 필요**|디바이스를 무단 해제하거나 루팅하지 않은 경우에만 앱을 사용할 수 있습니다.|  
|**액세스 요구 사항을 다시 확인할 시간(분)**|**제한 시간** 필드에 앱 실행 후 앱의 액세스 요구 사항을 다시 확인하기 전까지의 기간을 지정합니다.<br /><br /> **오프라인 유예 기간** 필드에서 장치가 오프라인 상태인 경우 앱의 액세스 요구 사항을 다시 확인하기 전까지의 기간을 지정합니다.|  
|**앱 데이터 암호화**|SD 카드에 저장된 데이터 등 외부 위치에 저장된 데이터를 비롯하여 이 앱과 연결된 모든 데이터를 암호화하도록 지정합니다.<br /><br /> **iOS용 암호화**<br /><br /> Configuration Manager 모바일 응용 프로그램 관리 정책과 연결된 앱의 경우 데이터는 OS에서 제공하는 디바이스 수준 암호화를 사용하여 암호화된 상태로 보관됩니다. 이러한 암호화는 IT 관리자가 설정해야 하는 디바이스 PIN 정책을 통해 사용하도록 설정됩니다. PIN이 필요한 경우에는 모바일 애플리케이션 관리 정책의 설정에 따라 데이터가 암호화됩니다. Apple 설명서에 나와 있는 것처럼 [iOS 7에서 사용하는 모듈은 FIPS 140-2의 인증을 받았습니다](http://support.apple.com/en-us/HT202739).<br /><br /> **Android용 암호화**<br /><br /> Configuration Manager 모바일 애플리케이션 관리 정책과 연결된 앱의 경우에는 Microsoft에서 암호화 기능을 제공합니다. 데이터는 모바일 애플리케이션 관리 정책의 설정에 따라 파일 I/O 작업 중에 동기식으로 암호화됩니다. Android의 관리되는 앱은 플랫폼 암호화 라이브러리를 통해 CBC 모드에서 AES-128 암호화를 사용합니다. 이 암호화 방법은 FIPS 140-2의 인증을 받지 않았습니다. 디바이스 저장소의 콘텐츠는 항상 암호화됩니다.|  
    |**화면 캡처 차단** (Android 장치에만 해당)|이 앱을 사용할 때 디바이스의 화면 캡처 기능을 차단하도록 지정합니다.|  
    |**연락처 동기화 사용 안 함**| 버전 1710부터 이 옵션은 앱에서 디바이스의 네이티브 연락처 앱에 데이터를 저장하지 못하도록 방지합니다. 아니요를 선택하면 앱에서 디바이스의 네이티브 연락처 앱에 데이터를 저장할 수 있습니다.|  
    |**인쇄 사용 안 함**| 버전 1710부터 이 옵션은 앱에서 회사 또는 학교 데이터를 인쇄하지 못하도록 방지합니다. |  

6)  **Managed Browser** 페이지에서 Managed Browser가 목록의 URL만 열 수 있도록 허용할지, 아니면 목록의 URL을 열지 못하도록 차단할지를 선택하고 **다음**을 선택합니다.  
자세한 내용은 [관리 브라우저 정책을 사용하여 인터넷 액세스 관리](manage-internet-access-using-managed-browser-policies.md)를 참조하세요.  

7)  마법사를 완료합니다.  

 새 정책이 **소프트웨어 라이브러리** 작업 영역의 **애플리케이션 관리 정책** 노드에 표시됩니다.  

##  <a name="step-4-associate-the-application-management-policy-with-a-deployment-type"></a>4단계: 애플리케이션 관리 정책과 배포 유형 연결  

 애플리케이션 관리 정책이 필요한 앱에 대해 배포 유형을 만들면 Configuration Manager에서는 이 배포 유형을 인식하고 앱 관리 정책을 연결하라는 메시지를 표시합니다. Managed Browser의 경우에는 일반 정책과 Managed Browser 정책을 둘 다 연결해야 합니다. 자세한 내용은 [애플리케이션 만들기](create-applications.md)를 참조하세요.  

> [!IMPORTANT]  
>  애플리케이션을 이미 배포한 경우에는 이 연결을 설정할 때까지 새 배포 유형이 배포되지 않습니다. 애플리케이션 **속성** 의 **애플리케이션 관리** 탭에서 연결을 설정할 수 있습니다.  

> [!IMPORTANT]  
>  iOS 7.1 이전 운영 체제를 실행하는 디바이스의 경우에는 앱을 제거해도 연결된 정책이 제거되지 않습니다.  
>   
>  Configuration Manager에서 디바이스 등록을 취소해도 정책은 앱에서 제거되지 않습니다. 정책을 적용한 앱은 제거했다가 다시 설치하더라도 정책 설정을 그대로 유지합니다.  

##  <a name="step-5-monitor-the-app-deployment"></a>5단계: 앱 배포 모니터링  
 모바일 애플리케이션 관리 정책과 연결된 앱을 만들고 배포한 후에는 앱을 모니터링하고 정책 충돌을 해결할 수 있습니다.  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **배포**를 선택합니다.  

3.  직접 만든 배포를 선택합니다. 그런 다음 **홈** 탭에서 **속성**을 선택합니다.  

4.  배포의 세부 정보 창에서 **관련 개체** 아래의 **애플리케이션 관리 정책**을 선택합니다.  

 애플리케이션 모니터링에 대한 자세한 내용은 [애플리케이션 모니터링](/sccm/apps/deploy-use/monitor-applications-from-the-console)을 참조하세요.  

##  <a name="learn-how-policy-conflicts-are-resolved"></a>정책 충돌을 해결하는 방법 알아보기  
 사용자나 디바이스에 대한 첫 번째 배포에서 모바일 응용 프로그램 관리 정책이 충돌하면 앱에 배포된 정책에서 충돌한 특정 설정 값이 제거되며 앱은 기본 제공 충돌 값을 사용합니다.  

 그 이후의 앱 또는 사용자에 대한 배포에서 모바일 앱 관리 정책이 충돌하는 경우에는 충돌한 특정 설정 값이 앱에 배포된 모바일 앱 관리 정책에 업데이트되지 않으며 앱은 해당 설정의 기본 값을 사용합니다.  

 디바이스나 사용자가 충돌하는 두 정책을 받는 경우에는 다음 동작이 적용됩니다.  

-   정책이 디바이스에 이미 배포된 경우에는 기존 정책 설정을 덮어쓰지 않습니다.  

-   디바이스에 아직 배포된 정책이 없는 상태에서 충돌하는 두 설정이 배포되면 디바이스에서 기본 제공되는 설정이 사용됩니다.  

##  <a name="see-a-list-of-available-policy-managed-apps"></a>사용 가능한 정책으로 관리되는 앱 목록 참조  
 iOS 및 Android 디바이스에 대해 사용 가능한 정책 관리 앱의 목록은 [Microsoft Intune 응용 프로그램 파트너](https://www.microsoft.com/cloud-platform/microsoft-intune-partners)를 참조하세요.  
