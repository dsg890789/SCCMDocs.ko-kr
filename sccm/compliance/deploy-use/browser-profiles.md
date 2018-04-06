---
title: Microsoft Edge 설정 구성
titleSuffix: Configuration Manager
description: Windows 10 클라이언트에서 Microsoft Edge 웹 브라우저 설정을 구성합니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 76477b4d-df41-4b25-8318-7d18d46ca2c6
ms.openlocfilehash: 57393c00faa0cc26d785d91ad1c6ecb9407ba5da
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/23/2018
---
# <a name="configure-microsoft-edge-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Microsoft Edge 설정 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

<!-- 1357310 -->
1802 버전부터 Windows 10 클라이언트에서 [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) 웹 브라우저를 사용하는 고객은 이제 Configuration Manager 준수 설정 정책을 만들어 여러 Microsoft Edge 설정을 구성합니다. 



## <a name="policy-settings"></a>정책 설정
이 정책에는 현재 다음 설정이 포함되어 있습니다.
- **Microsoft Edge 브라우저를 기본값으로 설정**: 웹 브라우저에 대한 Windows 10 기본 앱 설정을 Microsoft Edge로 구성합니다.
- **주소 표시줄 드롭다운 허용**: Windows 10 버전 1703 이상이 필요합니다. 자세한 내용은 [AllowAddressBarDropdown 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowaddressbardropdown)을 참조하세요.
- **Microsoft 브라우저 간 즐겨찾기 동기화 허용**: Windows 10 버전 1703 이상이 필요합니다. 자세한 내용은 [SyncFavoritesBetweenIEAndMicrosoftEdge 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-syncfavoritesbetweenieandmicrosoftedge)을 참조하세요.
- **종료 시 검색 데이터 지우기 허용**: Windows 10 버전 1703 이상이 필요합니다. 자세한 내용은 [ClearBrowsingDataOnExit 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-clearbrowsingdataonexit)을 참조하세요.
- **Do Not Track 헤더 허용**: 자세한 내용은 [AllowDoNotTrack 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack)을 참조하세요.
- **자동 채우기 허용**: 자세한 내용은 [AllowAutofill 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowautofill)을 참조하세요.
- **쿠키 허용**: 자세한 내용은 [AllowCookies 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowcookies)을 참조하세요.
- **팝업 차단 허용**: 자세한 내용은 [AllowPopups 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowpopups)을 참조하세요.
- **주소 표시줄에 검색 제안 허용**: 자세한 내용은 [AllowSearchSuggestionsinAddressBar 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar)을 참조하세요.
- **인트라넷 트래픽을 Internet Explorer에 전송 허용**: 자세한 내용은 [SendIntranetTraffictoInternetExplorer 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-sendintranettraffictointernetexplorer)을 참조하세요.
- **암호 관리자 허용**: 자세한 내용은 [AllowPasswordManager 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)을 참조하세요.
- **개발자 도구 허용**: 자세한 내용은 [AllowDeveloperTools 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowdevelopertools)을 참조하세요.
- **확장 허용**: 자세한 내용은 [AllowExtensions 브라우저 정책](/windows/client-management/mdm/policy-csp-browser#browser-allowextensions)을 참조하세요.



## <a name="create-the-microsoft-edge-browser-profile"></a>Microsoft Edge 브라우저 프로필 만들기

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다. **준수 설정**을 확장하고 새 **Microsoft Edge 브라우저 프로필** 노드를 선택합니다. **Microsoft Edge 브라우저 정책 만들기** 리본 옵션을 클릭합니다.
2. 정책의 **이름**을 지정하고 선택적으로 **설명**을 입력한 다음, **다음**을 클릭합니다.
3. **설정** 페이지에서 이 정책에 포함할 설정의 값을 **구성됨**으로 변경하고 **다음**을 클릭합니다.
4. **지원되는 플랫폼** 페이지에서 이 정책이 적용되는 운영 체제 버전 및 아키텍처를 선택하고 **다음**을 클릭합니다. 
5. 마법사를 완료합니다.



## <a name="deploy-the-policy"></a>정책 배포

1. 정책을 선택하고 **배포** 리본 옵션을 클릭합니다.
2. **찾아보기**를 클릭하여 정책을 배포할 사용자 또는 장치 컬렉션을 선택합니다. 
3. 필요에 따라 추가 옵션을 선택합니다. 
    a. 정책이 호환되지 않을 경우 경고를 생성합니다. 
    b. 클라이언트가 이 정책에 대한 장치의 준수를 평가하는 일정을 설정합니다.
4. **확인**을 클릭하여 배포를 만듭니다.



## <a name="next-steps"></a>다음 단계

준수 설정 정책과 마찬가지로 클라이언트는 지정된 일정에 따라 설정을 수정합니다. Configuration Manager 콘솔에서 [장치 준수를 모니터링하고 보고](/sccm/compliance/deploy-use/monitor-compliance-settings)합니다.
