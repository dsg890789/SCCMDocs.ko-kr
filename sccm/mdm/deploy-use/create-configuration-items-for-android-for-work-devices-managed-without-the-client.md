---
title: Intune으로 관리되는 Android for Work 디바이스에 대한 구성 항목을 만드는 방법
titleSuffix: Configuration Manager
ms.date: 2017-07-31
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ab6784fd-8c57-4be9-858f-50fe39f2ff5f
author: aczechowski
ms.author: aaroncz
ms.openlocfilehash: ba70e4d3a87f2a305312449907730174c62c4775
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32351278"
---
# <a name="how-to-create-configuration-items-for-android-for-work-devices-managed-with-intune"></a>Intune으로 관리되는 Android for Work 디바이스에 대한 구성 항목을 만드는 방법

 System Center Configuration Manager **Android for Work** 구성 항목을 사용하여 Configuration Manager에서 온-프레미스로 관리되거나 Microsoft Intune에 등록된 Android for Work 디바이스에 대한 설정을 관리할 수 있습니다.  

### <a name="to-create-an-android-for-work-configuration-item"></a>Android for Work 구성 항목을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **준수 설정**을 확장하고 **구성 항목**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **구성 항목 만들기**를 클릭합니다.  

4.  **구성 항목 만들기 마법사** 의 **일반**페이지에서 구성 항목에 대한 이름 및 선택적 설명을 지정합니다.  

5.  **만들려는 구성 항목 유형 지정**에서 **Android for Work**를 선택합니다.  

6.  Configuration Manager 콘솔에서 구성 항목을 검색하고 필터링하기 위해 범주를 만들고 할당하려면 **범주**를 선택합니다.  

  **다음**을 클릭합니다.

7.  마법사의 **디바이스 설정** 페이지에서 구성하려는 설정 그룹을 선택합니다. [Android for Work 구성 항목 설정](#android-for-work-configuration-item-settings-reference)에서 자세한 내용을 참조한 후 **다음**을 클릭합니다.  

  > [!TIP]  
  >  원하는 설정이 나열되지 않은 경우 **기본 설정 그룹에 없는 추가 설정 구성 확인란**을 선택합니다.  

9. 각 설정 페이지에서 필요한 설정과 디바이스에서 준수되지 않는 경우 수정 여부(지원되는 경우)를 구성합니다.  

10. 각 설정 그룹에 대해 구성 항목이 비규격인 것으로 확인되는 경우 보고될 심각성을 구성할 수도 있습니다.  

    -   **없음** - 이 준수 규칙에 실패한 장치가 Configuration Manager 보고서에 오류 심각도를 보고하지 않습니다.  

    -   **정보** - 이 준수 규칙에 실패한 장치가 Configuration Manager 보고서에 **정보** 오류 심각도를 보고합니다.  

    -   **경고** - 이 준수 규칙에 실패한 장치가 Configuration Manager 보고서에 **경고** 오류 심각도를 보고합니다.  

    -   **위험** - 이 준수 규칙에 실패한 장치가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다.  

    -   **위험(이벤트 포함)** - 이 준수 규칙에 실패한 장치가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다. 이 심각도 수준은 애플리케이션 이벤트 로그에 이벤트를 Windows 이벤트로 기록 됩니다.  

11. 마법사의 **플랫폼 적용 여부 가능성** 페이지에서 이전에 선택한 지원되는 플랫폼과 호환되지 않는 설정을 검토합니다. 뒤로 돌아가서 이러한 설정을 제거하거나 계속할 수 있습니다.  

    > [!TIP]  
    >  지원되지 않는 설정은 준수 여부에 대해 평가되지 않습니다.  

12. 마법사를 완료합니다.  

 **자산 및 준수** 작업 영역의 **구성 항목** 노드에서 새 구성 항목을 볼 수 있습니다.  

##  <a name="android-for-work-configuration-item-settings-reference"></a>Android for Work 구성 항목 설정 참조  

### <a name="password"></a>암호  

|설정|세부 정보|  
|-------------|-------------|  
|**장치에 암호 설정 필요**|지원되는 디바이스에는 암호가 필요합니다.|  
|**최소 암호 길이(문자 수)**|암호의 최소 길이입니다.|  
|**다음 기간 후 암호 만료(일)**|암호를 변경해야 할 때까지의 기간(일)입니다.|  
|**저장한 암호 수**|최근에 사용한 암호가 다시 사용되지 않도록 합니다.|  
|**다음 로그온 실패 횟수 후 장치 초기화**|이 횟수만큼 로그인에 실패하면 디바이스를 초기화합니다.|  
|**다음 유휴 시간 후 장치 잠그기**|잠그기 전까지 디바이스를 사용하지 않은 기간을 선택합니다.|
|**암호 품질**|필요한 암호 복잡도 수준과 생체 인식 디바이스 사용 가능 여부를 선택합니다.|  
|**Smart Lock 및 기타 신뢰 에이전트 허용**|호환되는 Android 디바이스의 스마트 잠금 기능을 제어해 보겠습니다. 신뢰 에이전트라고도 하는 이 전화 기능을 통해 디바이스가 특정 Bluetooth 디바이스에 연결된 경우 또는 NFC 태그에 가까이 있는 경우와 같이 신뢰할 수 있는 위치에 있는 경우 디바이스 잠금 화면 암호를 사용하지 않도록 설정하거나 무시할 수 있습니다. 이 설정을 사용하면 최종 사용자가 스마트 잠금을 구성하지 않도록 방지할 수 있습니다.|
|**잠금 해제 지문**|&nbsp;|

###  <a name="work-profile"></a>작업 프로필  
 이러한 설정은 삼성 KNOX 디바이스에만 적용됩니다.  

|설정 이름|세부 정보|  
|------------------|-------------|  
|**회사 프로필과 개인 프로필 간의 데이터 공유 허용**|다음 중에서 선택합니다.<br>- **구성되지 않음**<br>- **기본 공유 제한 사항**<br>- **회사 프로필의 앱에서 개인 프로필의 요청을 처리할 수 있음**<br>- **개인 프로필의 앱에서 회사 프로필의 요청을 처리할 수 있음**<br><br>(사용자 지정 URI를 사용한 [복사하여 붙여넣기 설정](#copy-paste-configuration-item-settings) 참조)|  
|**장치가 잠겼을 때 회사 프로필 알림 숨김(Android 6.0 이상)**||
|**기본 앱 사용 권한 정책 설정(Android 6.0 이상)**|다음 중에서 선택합니다.<br>- **구성되지 않음**<br>- **항상 메시지 표시**<br>- **자동 허용**<br>- **자동 거부**|

### <a name="copy-paste-configuration-item-settings"></a>복사하여 붙여넣기 구성 항목 설정
**회사 프로필과 개인 프로필 간의 데이터 공유 허용** 옵션으로는 복사하여 붙여넣기 동작을 금지할 수 없습니다. 복사하여 붙여넣기를 방지하도록 구성할 수 있는 사용자 지정 설정을 사용합니다. 이 설정은 사용자 지정 URI를 통해 지정할 수 있습니다.

- OMA-URI: ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste
- 값 형식: 부울

DisallowCrossProfileCopyPaste을 true로 설정하면 Android for Work 개인 및 회사 프로필 간에 복사-붙여넣기 동작이 방지됩니다.

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager 클라이언트 없이 관리되는 장치에 대한 구성 항목](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
