---
title: "관리 브라우저 정책을 사용하여 인터넷 액세스 관리 | Microsoft 문서"
description: "Intune Managed Browser를 배포하여 인터넷 액세스를 관리하고 제한합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 735c45b8-a545-4805-84e5-46204fabd1a6
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dcdaec52c9eafba3f7ce569f0dabb98921b4dc0a
ms.openlocfilehash: f870a98fa9e839df16d0ca9deb96a18128f35ba6


---
# <a name="manage-internet-access-using-managed-browser-policies-with-system-center-configuration-manager"></a>System Center Configuration Manager를 통해 관리 브라우저 정책을 사용하여 인터넷 액세스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 Intune Managed Browser(웹 검색 응용 프로그램)를 배포하고 관리 브라우저 정책과 연결할 수 있습니다. 관리 브라우저 정책은 관리 브라우저의 사용자가 이동할 수 있는 웹 사이트를 제한하는 허용 목록 또는 차단 목록을 설정합니다.  

 이 앱은 관리되는 앱이므로 잘라내기, 복사, 붙여넣기 사용 제어와 같은 모바일 응용 프로그램 관리 정책을 적용할 수도 있습니다. 이 경우 화면 캡처가 금지되며 콘텐츠 링크가 다른 관리되는 앱에서만 열립니다. 자세한 내용은 [모바일 응용 프로그램 관리 정책을 사용하여 앱 보호](../../apps/deploy-use/protect-apps-using-mam-policies.md)를 참조하세요.  

> [!IMPORTANT]  
>  사용자가 직접 관리 브라우저를 설치하는 경우 지정하는 정책에 의해 관리되지 않습니다. 브라우저가 Configuration Manager를 통해 관리되게 하려면 관리되는 앱으로 배포하려는 앱을 먼저 제거해야 합니다.  

 다음 장치 유형에 대한 관리 브라우저 정책을 만들 수 있습니다.  

-   Android 4 이상을 실행하는 장치  

-   iOS 7 이상을 실행하는 장치  

> [!NOTE]  
>  Intune Managed Browser 앱을 다운로드하고 자세한 내용을 보려면 iOS의 경우 [iTunes](https://itunes.apple.com/us/app/microsoft-intune-managed-browser/id943264951?mt=8)를 참조하고, Android의 경우 [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.intune.mam.managedbrowser&hl=en)를 참조하세요.  

## <a name="create-a-managed-browser-policy"></a>관리 브라우저 정책 만들기  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **응용 프로그램 관리 정책**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 관리 정책 만들기**를 선택합니다.  

4.  **일반** 페이지에서 정책의 이름과 설명을 입력하고 **다음**을 선택합니다.  

5.  **정책 형식** 페이지에서 플랫폼을 선택하고 정책 형식에 대해 **관리 브라우저**를 선택한 후에 **다음**을 선택합니다.  

     **관리 브라우저** 페이지에서 다음 옵션 중 하나를 선택합니다.  

    -   **관리 브라우저가 아래에 나열된 URL만 열도록 허용** – 관리 브라우저에서 열 수 있는 URL 목록을 지정합니다.  

    -   **관리 브라우저가 아래에 나열된 URL을 열지 못하도록 차단** – 관리 브라우저에서 열 수 있는 URL 목록을 지정합니다.  

    > [!NOTE]  
    >  동일한 관리 브라우저 정책에 허용 URL과 차단 URL을 함께 포함시킬 수 없습니다.  

     지정할 수 있는 URL에 대한 자세한 내용은 이 문서에서 허용 및 차단 URL에 대한 URL 형식을 참조하세요.  

    > [!NOTE]  
    >  일반 정책을 사용하는 경우 회사 규정 준수 및 보안 정책에 맞도록 배포하는 앱의 기능을 변경할 수 있습니다. 예를 들어 제한된 앱 내의 잘라내기, 복사 및 붙여넣기 작업을 제한할 수 있습니다. 일반 정책 유형에 대한 자세한 내용은 [모바일 응용 프로그램 관리 정책을 사용하여 앱 보호](../../apps/deploy-use/protect-apps-using-mam-policies.md)를 참조하세요.  

6.  마법사를 마칩니다.  

새 정책이 **소프트웨어 라이브러리** 작업 영역의 **응용 프로그램 관리 정책** 노드에 표시됩니다.  

## <a name="create-a-software-deployment-for-the-managed-browser-app"></a>관리 브라우저 앱에 대한 소프트웨어 배포 만들기  
 관리 브라우저 정책을 만든 후에는 Managed Browser 앱에 대한 소프트웨어 배포 유형을 만들 수 있습니다. Managed Browser 앱의 경우 일반 정책과 관리 브라우저 정책을 모두 연결해야 합니다.  

 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.  

## <a name="security-and-privacy-for-the-managed-browser"></a>관리 브라우저에 대한 보안 및 개인 정보  

-   iOS 장치에서 만료되었거나 신뢰할 수 없는 인증서를 가진 웹 사이트는 열 수 없습니다.  

-   사용자가 자신의 장치에서 기본 제공 브라우저에 대해 구성하는 설정은 관리 브라우저에서 사용되지 않습니다. Managed Browser는 이러한 설정에 액세스할 수 없습니다.  

-   Managed Browser와 연결된 모바일 응용 프로그램 관리 정책에서 **액세스하려면 단순 PIN 필요** 또는 **액세스하려면 회사 자격 증명 필요** 옵션을 설정한 경우 사용자가 인증 페이지에서 도움말을 클릭한 다음 Managed Browser 정책의 차단 목록에 추가된 사이트를 포함하여 모든 페이지로 이동할 수 있습니다.  

-   관리 브라우저는 직접 액세스하는 사이트에 대한 액세스만 차단할 수 있습니다. 중간 서비스(변환 서비스 등)를 사용하여 사이트에 액세스하는 경우 액세스를 차단할 수 없습니다.  

## <a name="reference-information"></a>참조 정보  

###  <a name="url-format-for-allowed-and-blocked-urls"></a>허용 및 차단 URL에 대한 URL 형식  

다음 정보를 사용하여 허용 및 차단 목록에 URL을 지정할 때 사용할 수 있는 형식 및 와일드카드에 대해 알아볼 수 있습니다.  

-   아래와 같은 허용 패턴 목록의 규칙에 따라 와일드 카드 기호 '**\***'를 사용할 수 있습니다.  

-   URL을 목록에 입력할 때 모든 URL의 앞에 **http** 또는 **https** 를 덧붙여야 합니다.  

-   주소에 포트 번호를 지정할 수 있습니다. 포트 번호를 지정하지 않은 경우 다음 값이 사용됩니다.  

    -   http의 경우 포트 80  

    -   https의 경우 포트 443  

     **http://www.contoso.com:\*** 및 **http://www.contoso.com: /\***처럼 포트 번호에 와일드 카드는 사용할 수 없습니다.  

-   다음 표를 사용하여 URL을 지정할 때 사용할 수 있는 패턴에 대해 알아볼 수 있습니다.  

    |URL|일치하는 항목|일치하지 않는 항목|  
    |---------|-------------|--------------------|  
    |http://www.contoso.com<br /><br /> 단일 페이지와 일치|www.contoso.com|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> contoso.com/|  
    |http://contoso.com<br /><br /> 단일 페이지와 일치|contoso.com/|host.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com|  
    |http://www.contoso.com/*<br /><br /> www.contoso.com으로 시작하는 모든 URL과 일치|www.contoso.com<br /><br /> www.contoso.com/images<br /><br /> www.contoso.com/videos/tvshows|host.contoso.com<br /><br /> host.contoso.com/images|  
    |http://*.contoso.com/\*<br /><br /> contoso.com 아래의 모든 하위 도메인과 일치|developer.contoso.com/resources<br /><br /> news.contoso.com/images<br /><br /> news.contoso.com/videos|contoso.host.com|  
    |http://www.contoso.com/images<br /><br /> 단일 폴더와 일치|www.contoso.com/images|www.contoso.com/images/dogs|  
    |http://www.contoso.com:80<br /><br /> 포트 번호를 사용하여 단일 페이지와 일치|http://www.contoso.com:80||  
    |https://www.contoso.com<br /><br /> 안전한 단일 페이지와 일치|https://www.contoso.com|http://www.contoso.com|  
    |http://www.contoso.com/images/*<br /><br /> 단일 폴더 및 모든 하위 폴더와 일치|www.contoso.com/images/dogs<br /><br /> www.contoso.com/images/cats|www.contoso.com/videos|  

-   다음은 지정할 수 없는 몇몇 입력의 예입니다.  

    -   *.com  

    -   *.contoso/\*  

    -   www.contoso.com/*images  

    -   www.contoso.com/*images\*pigs  

    -   www.contoso.com/page*  

    -   IP 주소  

    -   https://*  

    -   http://*  

    -   http://www.contoso.com:*  

    -   http://www.contoso.com:/*  

> [!NOTE]  
>  *.microsoft.com은 항상 허용됩니다.  

### <a name="how-conflicts-between-the-allow-and-block-list-are-resolved"></a>허용 목록과 차단 목록 간의 충돌을 해결하는 방법  
 여러 관리 브라우저 정책을 장치에 배포했는데 설정이 충돌하면 모드(허용 또는 차단)와 URL 목록에 대해 모두 충돌을 평가합니다. 충돌이 발생할 경우 다음 동작이 적용됩니다.  

-   각 정책의 모듈이 같지만 URL 목록이 서로 다르면 해당 장치에 URL이 적용되지 않습니다.  

-   각 정책의 모듈이 서로 다르지만 URL 목록이 같으면 해당 장치에 URL이 적용되지 않습니다.  

-   장치가 처음으로 관리 브라우저 정책을 받고 있는데 두 정책이 충돌하면 해당 장치에 URL이 적용되지 않습니다. **정책** 작업 영역의 **정책 충돌** 노드를 사용하여 충돌을 볼 수 있습니다.  

-   장치가 관리 브라우저 정책을 이미 받았는데 두 번째 정책이 충돌하는 설정을 가지고 배포되는 경우 원래 설정은 해당 장치에 유지됩니다. **정책** 작업 영역의 **정책 충돌** 노드를 사용하여 충돌을 볼 수 있습니다.  



<!--HONumber=Dec16_HO3-->


