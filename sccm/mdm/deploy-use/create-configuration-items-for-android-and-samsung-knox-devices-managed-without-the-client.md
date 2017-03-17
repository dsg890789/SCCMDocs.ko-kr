---
title: "Intune으로 관리되는 Android 및 Samsung KNOX Standard 장치에 대한 구성 항목 만들기 | Microsoft Docs"
description: "System Center Configuration Manager Android 및 Samsung KNOX Standard 구성 항목을 사용하여 장치 설정을 관리할 수 있습니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b66f3c4-e3bb-4f6a-abd5-55be649ff90d
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 67ea4d2a7c9753aa406a84157930564213b6cc0a
ms.lasthandoff: 03/06/2017


---
# <a name="create-configuration-items-for-android-and-samsung-knox-standard-devices-managed-with-intune"></a>Intune으로 관리되는 Android 및 Samsung KNOX Standard 장치에 대한 구성 항목 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager **Android 및 Samsung KNOX** 구성 항목을 사용하여 Configuration Manager에서 온-프레미스로 관리되거나 Microsoft Intune에 등록된 Android 및 Samsung KNOX Standard 장치에 대한 설정을 관리할 수 있습니다.  

## <a name="create-an-android-and-samsung-knox-standard-configuration-item"></a>Android 및 Samsung KNOX Standard 구성 항목 만들기  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 항목**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **구성 항목 만들기**를 클릭합니다.  

4.  **구성 항목 만들기 마법사** 의 **일반**페이지에서 구성 항목에 대한 이름 및 선택적 설명을 지정합니다.  

5.  **만들려는 구성 항목 유형 지정**에서 **Android 및 Samsung KNOX**를 선택합니다.  

6.  Configuration Manager 콘솔에서 구성 항목을 검색하고 필터링하기 위해 범주를 만들고 할당하려면 **범주**를 클릭합니다.  

7.  **지원되는 플랫폼** 페이지에서 구성 항목을 평가할 특정 Android 또는 Samsung KNOX Standard 플랫폼을 선택합니다.  

8.  **장치 설정** 페이지에서 구성하려는 설정 그룹을 선택합니다. 이 항목에서 [Android 및 Samsung KNOX Standard 구성 항목 설정 참조](#android-and-samsung-knox-standard-configuration-item-settings-reference)를 확인한 후에 **다음**을 클릭합니다.  

    > [!TIP]  
    >  원하는 설정이 나열되지 않은 경우 **기본 설정 그룹에 없는 추가 설정 구성 확인란**을 선택합니다.  

9. 각 설정 페이지에서 필요한 설정과 장치에서 준수되지 않는 경우 수정 여부(지원되는 경우)를 구성합니다.  

10. 각 설정 그룹에 대해 구성 항목이 비규격인 것으로 확인되는 경우 Configuration Manager 보고서에서 보고될 심각도를 구성할 수도 있습니다.  

    -   **없음** - 이 준수 규칙에 실패한 장치가 오류 심각도를 보고하지 않습니다.  

    -   **정보** - 이 준수 규칙에 실패한 장치가 **정보**의 오류 심각도를 보고합니다.  

    -   **경고** - 이 준수 규칙에 실패한 장치가 **경고** 오류 심각도를 보고합니다.  

    -   **위험** - 이 준수 규칙에 실패한 장치가 **위험** 오류 심각도를 보고합니다.  

    -   **위험(이벤트 포함)** - 이 준수 규칙에 실패한 장치가 **위험** 오류 심각도를 보고합니다.   

11. **플랫폼 적용 여부 가능성** 페이지에서 이전에 선택한 지원되는 플랫폼과 호환되지 않는 설정을 검토합니다. 뒤로 돌아가서 이러한 설정을 제거하거나 계속할 수 있습니다.  

    > [!TIP]  
    >  지원되지 않는 설정은 준수 여부에 대해 평가되지 않습니다.  

12. 마법사를 완료합니다.  

 **자산 및 준수** 작업 영역의 **구성 항목** 노드에서 새 구성 항목을 볼 수 있습니다.  

##  <a name="android-and-samsung-knox-standard-configuration-item-settings-reference"></a>Android 및 Samsung KNOX Standard 구성 항목 설정 참조  

### <a name="password"></a>암호  
 이러한 설정은 Android 및 Samsung KNOX Standard 장치 둘 다에 적용됩니다.  

|설정|세부 정보|  
|-------------|-------------|  
|**장치에 암호 설정 필요**|지원되는 장치에는 암호가 필요합니다.|  
|**최소 암호 길이(문자 수)**|암호의 최소 길이입니다.|  
|**다음 기간 후 암호 만료(일)**|암호를 변경해야 할 때까지의 기간(일)입니다.|  
|**저장한 암호 수**|이전에 사용한 암호를 다시 사용하지 못하도록 설정합니다.|  
|**다음 로그온 실패 횟수 후 장치 초기화**|이 횟수만큼 로그인에 실패하면 장치를 초기화합니다.|  
|**다음 유휴 시간 후 장치 잠그기**|장치를 사용하지 않는 경우 잠기기 전까지의 시간을 선택합니다.|
|**암호 품질**|필요한 암호 복잡도 수준과 생체 인식 장치 사용 가능 여부를 선택합니다.|  
|**Smart Lock 및 기타 신뢰 에이전트 허용**|호환 가능한 Android 장치에 대한 Smart Lock 기능을 제어할 수 있습니다. 신뢰 에이전트라고도 하는 이 전화 기능을 통해 장치가 특정 Bluetooth 장치에 연결된 경우 또는 NFC 태그에 가까이 있는 경우와 같이 신뢰할 수 있는 위치에 있는 경우 장치 잠금 화면 암호를 사용하지 않도록 설정하거나 무시할 수 있습니다. 이 설정을 사용하면 최종 사용자가 스마트 잠금을 구성하지 않도록 방지할 수 있습니다.|
|잠금 해제에 사용할 지문(KNOX 5.0 이상)|사용자가 지문을 사용하여 호환 장치의 잠금을 해제할 수 있습니다.|

###  <a name="device"></a>장치  
 이러한 설정은 Samsung KNOX Standard 장치에만 적용됩니다.  

|설정 이름|세부 정보|  
|------------------|-------------|
|**음성 전화 걸기**|장치에서 음성 전화 걸기 기능을 사용하거나 사용하지 않도록 설정할 수 있습니다.|
|**음성 도우미**|장치에서 음성 도우미 소프트웨어를 사용할 수 있습니다.|
|**화면 캡처**|사용자가 화면 콘텐츠를 이미지로 캡처할 수 있습니다.|
|**진단 데이터 전송**|장치가 진단 정보를 Google에 전송할 수 있습니다.|
|**지리적 위치**|장치가 위치 정보를 활용할 수 있습니다.|
|**복사 및 붙여넣기**|장치의 복사 및 붙여넣기 기능을 사용할 수 있습니다.|  
|**초기화**|사용자가 장치를 출하 시 설정으로 초기화할 수 있습니다.|  
|**응용 프로그램 간 클립보드 공유**|클립보드를 사용하여 앱 간에 복사 및 붙여넣기를 수행합니다.|
|**Bluetooth**|장치의 Bluetooth 기능을 사용할 수 있습니다.|

### <a name="store"></a>스토어
|설정|세부 정보|  
|-------------|-------------|  
|**앱 스토어**|장치에서 Google Play 스토어 앱에 액세스할 수 있습니다.|

### <a name="browser"></a>브라우저
|설정|세부 정보|  
|-------------|-------------|
|**웹 브라우저 허용**|장치의 기본 웹 브라우저 사용 가능 여부를 지정합니다.|
|**자동 채우기**|웹 브라우저의 자동 채우기 기능을 사용할 수 있습니다.|
|**액티브 스크립팅**|장치 웹 브라우저가 액티브 스크립팅을 사용할 수 있습니다.|
|**팝업 차단**|웹 브라우저에서 팝업 차단을 사용할 수 있습니다.|
|**쿠키**|장치 웹 브라우저가 쿠키를 사용할 수 있습니다.|

### <a name="cloud"></a>클라우드  
 이러한 설정은 Samsung KNOX Standard 장치에만 적용됩니다.  

|설정|세부 정보|  
|-------------|-------------|  
|**Google 백업**|Google 백업에 사용할 수 있습니다.|  
|**Google 계정 자동 동기화**|Google 계정 설정을 자동으로 동기화할 수 있습니다.|  



### <a name="security"></a>보안  

|설정|세부 정보|  
|-------------|-------------|  
|**SMS 및 MMS 메시징**|장치에서 SMS 및 MMS 메시징을 사용할 수 있습니다.|
|**이동식 저장소**|장치가 SD 카드와 같은 이동식 저장소를 사용할 수 있습니다.|
|**카메라**|장치 카메라를 사용할 수 있습니다.<br /><br /> Android 및 Samsung KNOX Standard 장치에 적용됩니다.|  
|**NFC(근거리 통신)**|장치에서 지원하는 경우 근거리 통신을 사용하는 작업을 수행할 수 있습니다.|
|**YouTube**|장치에 YouTube 앱을 사용할 수 있습니다.<br /><br /> Samsung KNOX Standard 장치에만 적용됩니다.|  
|**전원 끄기**|장치 전원을 끌 수 있습니다.<br /><br /> Samsung KNOX Standard 장치에만 적용됩니다.|

### <a name="roaming"></a>로밍
|설정|세부 정보|  
|-------------|-------------|
|**음성 로밍**|장치가 셀룰러 네트워크에 있을 때 음성 로밍을 허용합니다.|
|**데이터 로밍**|장치가 셀룰러 네트워크에 있을 때 데이터 로밍을 허용합니다.|

### <a name="encryption"></a>암호화  
 이러한 설정은 Android 및 Samsung KNOX Standard 장치 둘 다에 적용됩니다.  

|설정|세부 정보|  
|-------------|-------------|  
|**메모리 카드 암호화**|장치 저장소 카드를 암호화해야 하는지 여부를 지정합니다.|
|**장치에 파일 암호화**|모바일 장치의 파일을 암호화해야 합니다.|  

### <a name="wireless-communications"></a>무선 통신
|설정|세부 정보|  
|-------------|-------------|
|**무선 네트워크 연결**|장치의 Wi-Fi 기능을 사용할 수 있습니다.|
|**Wi-Fi 테더링**|장치의 Wi-Fi 테더링을 사용할 수 있습니다.|


### <a name="kiosk-mode-samsung-knox-standard-only"></a>키오스크 모드(Samsung KNOX Standard에만 해당)  
 키오스크 모드에서는 장치를 잠가 특정 기능만 작동하도록 허용할 수 있습니다. 예를 들어, 장치에서 지정된 관리되는 앱만 실행할 수 있게 하거나 장치에서 볼륨 단추를 사용되지 않도록 설정할 수 있습니다. 이러한 설정은 POS 장치와 같이 한 가지 기능만 수행하도록 지정된 장치 또는 장치의 데모 모델에 사용할 수 있습니다.  

#### <a name="to-configure-kiosk-mode-for-a-samsung-knox-standard-device"></a>Samsung KNOX Standard 장치에 대한 키오스크 모드를 구성하려면  

**구성 항목 만들기 마법사**의 **Samsung KNOX 장치에 대한 키오스크 모드 설정 구성** 페이지에서 다음 정보를 지정합니다.  

- **앱 선택** - **찾아보기**를 클릭하여 장치가 키오스크 모드일 때 실행할 수 있는 Configuration Manager Android 응용 프로그램(확장명이 **.apk**임)을 선택합니다. 다른 앱은 장치에서 실행할 수 없습니다.
- **볼륨 단추** - 장치에서 볼륨 단추를 사용하거나 사용하지 않도록 설정합니다.
- **화면 절전 모드 및 절전 모드 해제 단추** - 장치에서 화면 절전 모드 해제 단추를 사용하거나 사용하지 않도록 설정합니다.|  

###  <a name="compliant-and-noncompliant-apps-android"></a>규격 및 비규격 앱(Android)  
 회사의 규격 또는 비규격 Android 앱 목록을 지정할 수 있습니다. 그런 다음 보고서를 사용하여 비호환 앱이 설치된 장치와 관련 사용자를 표시할 수 있습니다.  

 같은 구성 항목에서 호환 앱과 비호환 앱을 모두 지정할 수는 없습니다.  

#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>호환 또는 비호환 앱 목록을 지정하려면  

1.  **호환 및 비호환 앱(Android)** 페이지에서 다음 정보를 지정합니다.  

    |설정|추가 정보|  
    |-------------|----------------------|  
    |**비규격 앱 목록**|사용자가 설치하는 경우 호환되지 않는 것으로 보고되도록 할 앱 목록을 지정하려면 이 옵션을 선택합니다.|  
    |**규격 앱 목록**|사용자가 설치할 수 있는 앱 목록을 지정하려면 이 옵션을 선택합니다. 설치된 앱 중 이 목록에 포함되어 있지 않은 기타 모든 앱은 호환되지 않는 앱으로 보고됩니다.|  
    |**추가**|앱을 선택한 목록에 추가합니다. 원하는 이름, 앱 게시자(선택 사항) 및 앱 스토어의 앱 URL을 지정합니다.<br /><br /> URL을 지정하려면 [Google Play의 앱 섹션](https://play.google.com/store/apps)에서 사용할 앱을 검색합니다.<br /><br /> 앱 페이지를 열고 클립보드에 URL을 복사합니다. 이제 규격 또는 비규격 앱 목록의 URL로 사용할 수 있습니다.<br /><br /> **예:** Google Play에서 **Microsoft Office Mobile**을 검색합니다. 사용하는 URL이 **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**가 됩니다.|  
    |**편집**|선택한 앱의 이름, 게시자 및 URL을 편집할 수 있습니다.|  
    |**제거**|목록에서 선택한 앱을 삭제합니다.|  
    |**가져오기**|지정한 앱 목록을 쉼표로 구분된 값 파일로 가져옵니다. 파일의 형식, 응용 프로그램 이름, 게시자, 앱 URL을 사용합니다.|  

2.  작업을 완료한 경우 **다음**을 클릭합니다. 규격 및 비규격 앱 설정을 포함하는 구성 항목은 사용자 컬렉션에 배포해야 합니다.

 다음 보고서 모니터 규격 및 비규격 앱 중 하나를 사용할 수 있습니다.  

-   **지정한 사용자에 대한 호환되지 않는 앱 및 장치 목록** - 지정한 정책과 호환되지 않는 앱을 설치한 장치 및 사용자에 대한 정보가 표시됩니다.  

-   **호환되지 않는 앱을 설치한 사용자 요약** - 지정한 정책과 호환되지 않는 앱을 설치한 사용자에 대한 정보가 표시됩니다.  

 보고서를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 기능](../../core/servers/manage/reporting.md)을 참조하세요.  

