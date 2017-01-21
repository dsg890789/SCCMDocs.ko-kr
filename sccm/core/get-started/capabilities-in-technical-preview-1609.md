---
title: "System Center Configuration Manager용 Technical Preview 1609의 기능 | Microsoft 문서"
description: "System Center Configuration Manager용 Technical Preview 버전 1609에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: e2a59116-b2e5-4dd2-90eb-0b8a5eb50b56
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 3bf44f850722afdb8dfe5922c8ceff11c9b56d08
ms.openlocfilehash: 4ab022eda3367c79dbe698b6dab7017cb25b5e3a

---
# <a name="capabilities-in-technical-preview-1609-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1609의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*



이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1609에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    

**이 Technical Preview의 알려진 문제:**  
*  Configuration Manager 1609 Technical Preview로 업데이트하면 배포한 모든 버전 업그레이드 정책이 삭제됩니다. 이러한 정책을 계속 사용하려면 다시 만들어서 배포해야 합니다.


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="improvements-to-endpoint-protection"></a>Endpoint Protection 개선
Endpoint Protection 맬웨어 방지 정책 설정 개선 - Endpoint Protection 클라우드 보호 서비스가 의심스러운 파일을 차단하는 수준을 지정할 수 있습니다. 새 설정을 사용하면 관리자가 많은 양의 맬웨어가 발생한 "위험한" 컴퓨터를 지정할 수 있습니다.

## <a name="increased-number-of-enrolled-devices"></a>등록된 장치 수 증가
이제 관리자는 사용자가 Intune을 사용하여 최대 15개의 장치를 하이브리드 모바일 장치 관리에 등록하도록 설정할 수 있습니다. 이전에는 사용자당 장치 5대로 제한되었습니다.

## <a name="additional-apple-dep-settings"></a>추가 Apple DEP 설정

이제 관리자는 iOS 및 Mac 장치에 대한 DEP 프로필에서 다음 Apple DEP(장비 등록 프로그램) 설정을 구성할 수 있습니다.
- **터치 ID**
- **확대/축소**
- **Siri**

사용하도록 설정하면 Apple의 설정 길잡이가 장치 활성화 중 이 서비스를 사용할지 묻는 메시지를 표시합니다.

## <a name="integration-with-upgrade-analytics"></a>Upgrade Analytics 통합

Upgrade Analytics는 업그레이드를 더 쉽고 원활하게 수행할 수 있도록 Windows 10과의 호환성 및 장치 준비성을 평가 및 분석합니다. Upgrade Analytics와 Configuration Manager를 통합하면 Configuration Manager 관리 콘솔에서 업그레이드 호환성 데이터에 액세스한 다음 장치 목록에서 업그레이드 또는 수정할 대상 장치에 액세스할 수 있습니다.

Upgrade Analytics에 대한 자세한 내용은 [Get started with Upgrade Analytics](https://technet.microsoft.com/itpro/windows/deploy/upgrade-analytics-get-started)(Upgrade Analytics 시작)를 참조하세요.

## <a name="native-connection-types-for-windows-10-vpn-hybrid-profiles"></a>Windows 10 VPN 하이브리드 프로필에 대한 네이티브 연결 형식

Configuration Manager를 Intune과 함께 사용할 경우 OMA-URI를 사용하지 않고 Configuration Manager 콘솔에서 Microsoft Automatic, IKEv2, PPTP 및 L2TP 연결 유형을 사용하여 Windows 10 VPN 프로필을 만들 수 있습니다.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Configuration Manager와 비즈니스용 Windows 스토어 통합 향상

이 릴리스에서는 [비즈니스용 Windows 스토어 통합](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)을 새로운 기능으로 업데이트했습니다.

**업데이트:** 현재 Technical Preview 릴리스에서는 즉시 동기화 기능을 사용할 수 없습니다.

- 이전에는 비즈니스용 Windows 스토어에서 무료 앱만 배포할 수 있었습니다. 이제 Configuration Manager에서 사용이 허가된 유료 온라인 앱 배포를 추가로 지원합니다(Intune에 등록된 장치에 한함).
- 이제 비즈니스용 Windows 스토어와 Configuration Manager 간의 즉시 동기화를 시작할 수 있습니다.
- 이제 Azure Active Directory에서 얻은 클라이언트 비밀 키를 수정할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

#### <a name="purchase-and-sync-a-paid-online-licensed-app"></a>사용이 허가된 유료 온라인 앱 구매 및 동기화

1. 비즈니스용 Windows 스토어에서 사용이 허가된 유료 온라인 앱을 구매합니다.
2. Configuration Manager 콘솔의 **관리** 작업 영역에서 **클라우드 서비스** > **업데이트 및 서비스** > **비즈니스용 Windows 스토어**를 클릭합니다.
3. **홈** 탭의 **동기화** 그룹에서 **지금 동기화**를 클릭합니다.
4. 구매한 앱이 **응용 프로그램 관리** 작업 영역의 **스토어 앱에 대한 라이선스 정보** 노드에 나타납니다.

#### <a name="create-and-deploy-a-configuration-manager-application-from-the-synchronized-app-data"></a>동기화된 앱 데이터에서 Configuration Manager 응용 프로그램 만들기 및 배포

유료 스토어 앱에서 Configuration Manager 응용 프로그램을 만들고 배포하는 절차는 무료 앱에서 응용 프로그램을 만들 때와 동일합니다. [System Center Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)의 **비즈니스용 Windows 스토어에서 앱에서 Configuration Manager 응용 프로그램 만들기 및 배포**를 참조하세요.


#### <a name="modify-the-client-secret-key-from-azure-active-directory"></a>Azure Active Directory에서 클라이언트 암호 키 수정

1. Configuration Manager 콘솔의 **관리** 작업 영역에서 **클라우드 서비스** > **업데이트 및 서비스** > **비즈니스용 Windows 스토어**를 클릭합니다.
2. 비즈니스용 Windows 스토어 계정을 선택하고 **속성**을 클릭합니다.
3. **비즈니스용 Windows 스토어 계정 속성** 대화 상자의 **클라이언트 암호 키** 필드에 새 키를 입력하고 **확인**을 클릭합니다. 확인한 다음 **적용**을 클릭하고 대화 상자를 닫습니다.


## <a name="new-compliance-settings-for-configuration-items"></a>구성 항목의 새 준수 설정

다양한 장치 플랫폼의 구성 항목에 사용할 수 있는 여러 가지 새로운 설정을 추가했습니다.
이러한 설정은 이전에 Microsoft Intune의 독립 실행형 구성에 있던 설정이며 이제 Intune과 Configuration Manager를 사용할 때 제공됩니다.
이러한 설정 사용에 대한 도움이 필요한 경우 [Microsoft Intune 정책을 사용하여 장치의 설정 및 기능 관리](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies)를 열고 원하는 플랫폼에 대한 설정 하위 항목을 선택합니다.


### <a name="new-settings-for-android-devices"></a>Android 장치에 대한 새로운 설정

#### <a name="password-settings"></a>암호 설정

- **암호 기록 기억**
- **지문 잠금 해제 허용**

#### <a name="security-settings"></a>보안 설정

- **메모리 카드 암호화 필요**
- **화면 캡처 허용**
- **진단 데이터 제출 허용**

#### <a name="browser-settings"></a>브라우저 설정

- **웹 브라우저 허용**
- **자동 채우기 허용**
- **팝업 차단 허용**
- **쿠키 허용**
- **액티브 스크립팅 허용**

#### <a name="app-settings"></a>앱 설정

- **Google Play 스토어 사용 가능**

#### <a name="device-capability-settings"></a>장치 기능 설정

- **이동식 저장소 허용**
- **Wi-Fi 테더링 허용**
- **지리적 위치 허용**
- **NFC 허용**
- **Bluetooth 허용**
- **음성 로밍 허용**
- **데이터 로밍 허용**
- **SMS/MMS 메시지 허용**
- **음성 지원 허용**
- **음성 전화 걸기 허용**
- **복사 및 붙여넣기 허용**


### <a name="new-settings-for-ios-devices"></a>iOS 장치에 대한 새 설정

#### <a name="password-settings"></a>암호 설정

- **암호에 필요한 복합 문자 수**
- **단순 암호 허용**
- **암호를 요구하기 전까지 비활성 시간(분)**
- **암호 기록 기억**

### <a name="new-settings-for-mac-os-x-devices"></a>Mac OS X 장치에 대한 새 설정

#### <a name="password-settings"></a>암호 설정

- **암호에 필요한 복합 문자 수**
- **단순 암호 허용**
- **암호 기록 기억**
- **화면 보호기가 활성화되기까지의 비활성 시간(분)**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Windows 10 Desktop 및 모바일 장치에 대한 새로운 설정

#### <a name="password-settings"></a>암호 설정

- **최소 문자 집합 수**
- **암호 기록 기억**
- **장치가 유휴 상태에서 되돌아오는 경우 암호 필요**

#### <a name="security-settings"></a>보안 설정

- **모바일 장치 암호화 필요**
- **수동 등록 취소 허용**

#### <a name="device-capability-settings"></a>장치 기능 설정

- **셀룰러에서 VPN 허용**
- **셀룰러에서 VPN 로밍 허용**
- **휴대폰 초기화 허용**
- **USB 연결 허용**
- **Cortana 허용**
- **알림 센터 알림 허용**

### <a name="new-settings-for-windows-10-team-devices"></a>Windows 10 Team 장치에 대한 새 설정

#### <a name="device-settings"></a>장치 설정

- **Azure Operational Insights 사용**
- **Miracast 무선 프로젝션 사용**
- **시작 화면에 표시되는 모임 정보 선택**
- **잠금 화면 배경 이미지 URL**


### <a name="new-settings-for-windows-81-devices"></a>Windows 8.1 장치의 새로운 설정

#### <a name="applicability-settings"></a>적용 가능성 설정

- **Windows 10에 모든 구성 적용**

#### <a name="password-settings"></a>암호 설정

- **필수 암호 유형**
- **최소 문자 집합 수**
- **최소 암호 길이**
- **장치를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수**
- **화면이 잠기기 전까지 비활성 시간(분)**
- **암호 만료(일)**
- **암호 기록 기억**
- **이전 암호 다시 사용 방지**
- **사진 암호 및 PIN 허용**

#### <a name="browser-settings"></a>브라우저 설정

- **인트라넷 네트워크의 자동 검색 허용**


### <a name="new-settings-for-windows-phone-81-devices"></a>Windows Phone 8.1 장치에 대한 새로운 설정

#### <a name="applicability-settings"></a>적용 가능성 설정

- **Windows 10에 모든 구성 적용**

#### <a name="password-settings"></a>암호 설정

- **최소 문자 집합 수**
- **단순 암호 허용**
- **암호 기록 기억**

#### <a name="device-capability-settings"></a>장치 기능 설정

- **무료 Wi-Fi 핫스팟에 자동 연결 허용**


## <a name="improvements-for-boundary-groups"></a>경계 그룹의 향상된 기능
이 미리 보기는 경계 그룹에 대한 중요 변경 사항 및 배포 지점과 함께 사용하는 방식을 소개합니다. 이러한 변경 사항을 통해 콘텐츠 인프라 디자인이 간편해졌을 뿐 아니라 클라이언트가 콘텐츠 원본 위치로 추가 배포 지점을 검색하기 위해 대체하는 방법과 시기를 제어할 수 있습니다. 여기에는 온-프레미스와 클라우드 기반 배포 지점이 모두 포함됩니다.

이러한 향상된 기능은 현재 익숙한 개념과 동작(배포 지점을 빠름 또는 느림으로 구성)을 대체하고 설치 및 유지 관리가 더 쉬운 새 모델로 바꿉니다. 또한 경계 그룹에 연결할 다른 사이트 시스템 역할을 향상시키는 추가 변경 사항의 기반이 됩니다.  

1609로 업그레이드하는 동안 이러한 변경 사항이 콘텐츠 배포 구성을 방해하지 않도록 새 모델에 맞게 현재 경계 그룹 구성이 변환됩니다([기존 경계 그룹을 새 모델로 업데이트](/sccm/core/get-started/capabilities-in-technical-preview-1609#bkmk_update) 참조).

다음 섹션에서는 이 미리 보기에 소개된 변경 내용, 새 모델의 작동 방식 및 이미 경계 그룹이 구성된 사이트를 업그레이드할 때 예상되는 작업에 대해 자세히 설명합니다.



### <a name="changes-in-ui-and-behavior-for-boundary-groups-and-content-locations"></a>경계 그룹과 콘텐츠 위치에 대한 동작 및 UI 변경 내용
다음은 경계 그룹 및 클라이언트에서 콘텐츠를 검색하는 방법에 대한 주요 변경 내용입니다. 이러한 많은 변경 내용 및 개념은 함께 작동합니다.
-   **빠름 또는 느림 구성 제거됨:** 개별 배포 지점을 더 이상 빠름 또는 느림으로 구성하지 않습니다.  대신 경계 그룹과 연결된 각 사이트 시스템이 동일하게 처리됩니다. 이러한 변경으로 인해 경계 그룹 속성의 **참조** 탭에서 더 이상 빠름 또는 느림 구성을 지원하지 않습니다.
-   **각 사이트의 새 기본 경계 그룹:** 각 기본 사이트에는 ***Default-Site-Boundary-Group\<sitecode>***라는 새 기본 경계 그룹이 있습니다.  경계 그룹에 지정된 네트워크 위치에 없는 클라이언트는 지정된 사이트의 기본 그룹과 연결된 사이트 시스템을 사용합니다. 이 경계 그룹을 대체 콘텐츠 위치의 개념 대신 사용합니다.    
 -  **‘콘텐츠에 대해 대체 원본 위치 허용’** 제거됨: 더 이상 대체에 사용할 배포 지점을 명시적으로 구성하지 않으며 이 기능을 설정하는 옵션이 UI에서 제거되었습니다.

    또한 응용 프로그램의 배포 유형에서 **클라이언트가 콘텐츠에 대한 대체 원본 위치를 사용하도록 허용** 설정의 결과가 변경되었습니다. 이제 배포 유형에서 이 설정을 사용하면 클라이언트가 기본 사이트 경계 그룹을 콘텐츠 원본 위치로 사용할 수 있습니다.

 -  **경계 그룹 관계:** 각 경계 그룹은 하나 이상의 추가 경계 그룹에 연결할 수 있습니다. 이러한 링크는 **관계**라는 새 경계 그룹 속성 탭에서 관계를 구성합니다.
    -   클라이언트가 직접 연결된 각 경계 그룹을 **현재** 경계 그룹이라고 합니다.  
    -   클라이언트의 *현재* 경계 그룹과 다른 그룹 간의 연결로 클라이언트에서 사용할 수 있는 경계 그룹을 **인접** 경계 그룹이라고 합니다.
    -  *인접* 경계 그룹으로 사용할 수 있는 경계 그룹을 추가하려면 **관계** 탭을 사용합니다. *현재* 그룹의 배포 지점에서 콘텐츠를 찾지 못한 클라이언트가 이러한 *인접* 경계 그룹에서 콘텐츠 위치 검색을 시작할 시간(분)을 구성할 수도 있습니다.

        경계 그룹 구성을 추가하거나 변경할 때 현재 구성 중인 그룹이 해당 경계 그룹으로 대체되지 않도록 차단할 수 있습니다.

    새 구성을 사용하려면 한 경계 그룹에서 다른 경계 그룹으로 명시적 연결(링크)을 정의하고 연결된 그룹의 모든 배포 지점을 동일한 시간(분)으로 구성합니다. 구성하는 시간에 따라 *현재* 경계 그룹에서 콘텐츠 원본을 찾지 못한 클라이언트가 해당 인접 경계 그룹에서 콘텐츠 원본을 검색하기 시작하는 시간이 결정됩니다.

    각 경계 그룹에는 명시적으로 구성한 경계 그룹 외에도 기본 사이트 경계 그룹에 대한 암시적 링크가 있습니다. 기본 사이트 경계 그룹이 인접 경계 그룹이 되면 120분 뒤에 이 링크가 활성화됩니다. 그러면 클라이언트에서 해당 경계 그룹과 연결된 배포 지점을 콘텐츠 원본 위치로 사용할 수 있습니다.

    이 동작을 이전에는 콘텐츠 대체라고 했습니다.  기본 사이트 경계 그룹을 *현재* 그룹에 명시적으로 연결하고 특정 시간(분)을 설정하거나 대체를 완전히 차단하여 사용하지 못하도록 설정하여 이 기본 동작(120분)을 재정의할 수 있습니다.


-   **클라이언트가 최대 2분 동안 각 배포 지점에서 콘텐츠 가져오기 시도:** 클라이언트는 콘텐츠 원본 위치를 검색할 때 각 배포 지점을 2분 동안 액세스한 다음 다른 배포 지점을 검색합니다. 이전 버전에서는 클라이언트가 최대 2시간 동안 배포 지점 연결을 시도했습니다.

    - 클라이언트가 사용하려는 첫 번째 배포 지점은 클라이언트의 *현재* 경계 그룹에서 사용 가능한 배포 지점 풀 중에서 임의로 선택됩니다.

    - 2분 후 클라이언트가 콘텐츠를 찾지 못하면 새 배포 지점으로 전환하여 해당 서버에서 콘텐츠 가져오기를 시도합니다. 이 프로세스는 클라이언트가 콘텐츠를 찾거나 해당 풀의 마지막 서버에 도달할 때까지 2분마다 반복됩니다.

    - 클라이언트가 *인접* 경계 그룹으로 대체되는 기간 전에 *현재* 풀에서 유효한 콘텐츠 원본 위치를 찾지 못하면 해당 *인접* 그룹의 배포 지점을 현재 목록의 끝에 추가한 다음 두 경계 그룹의 배포 지점을 포함하는 확장된 원본 위치 그룹을 검색합니다.

        > [!TIP]  
        > 현재 경계 그룹에서 기본 사이트 경계 그룹으로 명시적 링크를 만들고 인접 경계 그룹에 대한 링크의 대체 시간보다 짧게 대체 시간을 정의하면 클라이언트가 인접 그룹을 포함하기 전에 기본 사이트 경계 그룹에서 원본 위치 검색을 시작합니다.

    - 클라이언트가 풀의 마지막 서버에서 콘텐츠를 가져올 수 없으면 프로세스가 다시 시작됩니다.


### <a name="how-the-new-model-works"></a>새 모델의 작동 방식
경계 그룹을 구성할 때 경계(네트워크 위치)와 사이트 시스템 역할(예: 배포 지점)을 경계 그룹에 연결합니다. 그러면 네트워크에서 클라이언트 근처에 있는 배포 지점과 같은 사이트 시스템 서버에 클라이언트를 연결할 수 있습니다.   
-   여러 경계 그룹에 동일한 경계를 할당할 수 있습니다.
-   많은 네트워크 위치에서 사용할 수 있도록 배포 지점 등의 사이트 시스템 서버를 여러 경계 그룹에 연결할 수 있습니다.
-   배포 지점이 경계 그룹에 연결되어 있지 않으면 클라이언트가 해당 배포 지점을 콘텐츠 원본 위치로 사용할 수 없습니다.

이 Technical Preview부터는 경계 그룹 관계를 정의하여 콘텐츠 원본 위치에 대한 대체 동작을 구성합니다. 이 새로운 동작은 경계 그룹 속성의 새 **관계** 탭에서 구성되며, 사이트 시스템을 빠름 또는 느림으로 구성하고 콘텐츠에 대한 대체 원본 위치를 허용하도록 경계 그룹을 구성하는 작업을 대체합니다.

관계 탭에서 다른 경계 그룹을 추가하여 이러한 그룹에 대한 관계를 구성할 수 있습니다. 각 관계는 **현재** 경계 그룹에서 추가한 **인접** 경계 그룹으로의 단방향 링크입니다. 만들어진 각 링크마다 대체 시간(분)이 지정된 배포 지점을 구성할 수 있습니다. 이 시간은 *현재* 경계 그룹의 클라이언트가 현재 경계 그룹에서 유효한 콘텐츠 원본 위치를 찾지 못한 경우 *인접* 경계 그룹의 배포 지점 사용을 시작할 수 있는 때까지의 시간을 결정합니다.

콘텐츠를 찾지 못한 클라이언트가 인접 경계 그룹에서 위치 검색을 시작하면 제어된 방식으로 해당 클라이언트에 대해 사용할 수 있는 배포 지점의 풀이 커집니다.  

-   경계 그룹에 둘 이상의 관계를 구성할 수 있습니다. 이렇게 하면 서로 다르게 지정된 시간이 지난 후 다른 인접 대체가 발생하도록 구성할 수 있습니다.
-   클라이언트는 현재 경계 그룹의 직접 인접인 경계 그룹으로만 대체합니다.
-   클라이언트가 여러 경계 그룹의 구성원인 경우 현재 경계 그룹이 모든 클라이언트 경계 그룹의 연합으로 정의됩니다.  그러면 해당 클라이언트가 이러한 원래 경계 그룹의 인접으로 대체할 수 있습니다.

정의한 링크 외에도, 직접 만든 경계 그룹과 각 사이트에 대해 자동으로 만들어지는 기본 경계 그룹 간에 자동으로 만들어지는 암시적 링크가 있습니다. 이 자동 링크의 특징은 다음과 같습니다.
-   계층의 경계 그룹과 연결된 경계에 있지 않은 클라이언트에서 할당된 사이트의 기본 경계 그룹을 자동으로 사용하여 유효한 콘텐츠 원본 위치를 식별합니다.   
-   현재 경계 그룹에서 120분 후에 사용되는 사이트 기본 경계 그룹으로 대체되는 기본 대체 옵션입니다.

**새 모델 사용 예제:**     
경계 또는 사이트 시스템 서버를 공유하지 않는 세 가지 경계 그룹을 만듭니다.
-   배포 지점 DP_A1 및 DP_A2가 연결된 그룹 BG_A
-   배포 지점 DP_B1 및 DP_B2가 연결된 그룹 BG_B
-   배포 지점 DP_C1 및 DP_C2가 연결된 그룹 BG_C

클라이언트의 네트워크 위치를 BG_A 경계 그룹에만 경계로 추가한 다음 해당 경계 그룹에서 다른 두 경계 그룹으로의 관계를 구성합니다.
-   10분 후 사용할 첫 번째 *인접* 그룹(BG_B)에 대한 배포 지점을 구성합니다. 이 그룹에는 배포 지점 DP_B1 및 DP_B2가 포함됩니다. 둘 다 첫 번째 그룹 경계 위치에 연결됩니다.
-   20분 후에 사용할 두 번째 *인접* 그룹(BG_C)을 구성합니다. 이 그룹에는 배포 지점 DP_C1 및 DP_C2가 포함됩니다. 둘 다 다른 두 경계 그룹에서 WAN을 통해 연결됩니다.
-   또한 사이트 서버에 있는 추가 배포 지점을 사이트 기본 사이트 경계 그룹에 추가합니다. 이 위치는 가장 선호되지 않는 콘텐츠 원본 위치이지만 모든 경계 그룹 중앙에 위치합니다.

    경계 그룹 및 대체 시간 예제:

     ![BG_Fallack](media/BG_Fallback.png)


이 구성을 사용하면:
-   클라이언트는 *현재* 경계 그룹(BG_A)의 배포 지점에서 콘텐츠 검색을 시작하고 각 배포 지점에서 2분 동안 검색한 다음 경계 그룹의 다음 배포 지점으로 전환합니다. 올바른 콘텐츠 원본 위치의 클라이언트 풀에는 DP_A1 및 DP_A2가 포함됩니다.
-   클라이언트가 *현재* 경계 그룹에서 10분 동안 콘텐츠를 찾지 못하면 BG_B 경계 그룹의 배포 지점이 해당 검색에 추가됩니다. 그런 다음 이제 두 BG_A와 BG_B 경계 그룹의 배포 지점을 포함하는 결합된 배포 지점 풀에 있는 배포 지점에서 콘텐츠를 검색합니다. 클라이언트는 각 배포 지점을 2분 동안 연결한 다음 해당 풀의 다음 배포 지점으로 전환합니다. 올바른 콘텐츠 원본 위치의 클라이언트 풀에는 DP_A1, DP_A2, DP_B1 및 DP_B2가 포함됩니다.
-   그 후 10분 뒤(총 20분)에도 클라이언트가 콘텐츠가 있는 배포 지점을 찾지 못하면 두 번째 *인접* 그룹인 경계 그룹 BG_C의 배포 지점을 포함하도록 사용 가능한 배포 지점 풀을 확장합니다. 이제 클라이언트는 검색할 배포 지점이 총 6개(DP_A1, DP_A2, DP_B2, DP_B2, DP_C1 및 DP_C2)이며 콘텐츠를 찾을 때까지 2분 간격으로 새 배포 지점으로 변경합니다.
-   총 120분 후 클라이언트가 콘텐츠를 찾지 못하면 *기본 사이트 경계 그룹*을 연속 검색의 일부로 포함하도록 대체합니다. 이제 배포 지점 풀에는 3개의 구성된 경계 그룹의 모든 배포 지점과 사이트 서버 컴퓨터에 있는 최종 배포 지점이 포함됩니다.  클라이언트는 콘텐츠를 계속 검색하고 콘텐츠를 찾을 때까지 2분마다 배포 지점을 변경합니다.

서로 다른 시간에 사용할 수 있는 여러 인접 그룹을 구성하여 특정 배포 지점이 콘텐츠 원본 위치로 추가되는 시기를 제어하고, 클라이언트가 기본 사이트 경계 그룹을 다른 위치에서 사용할 수 없는 콘텐츠를 위한 안전망으로 대체할지 여부 또는 그 시기를 제어합니다.


### <a name="a-namebkmkupdateaupdate-existing-boundary-groups-to-the-new-model"></a><a name="bkmk_update"></a>기존 경계 그룹을 새 모델로 업데이트
버전 1609를 설치하고 사이트를 업데이트하면 다음 구성이 자동으로 만들어집니다. 그 이유는 새 경계 그룹 및 관계를 구성할 때까지 현재 대체 동작을 계속 사용할 수 있도록 하기 위해서입니다.  
-   사이트에서 보호되지 않은 배포 지점이 해당 사이트의 *Default-Site-Boundary-Group\<sitecode>* 경계 그룹에 추가됩니다.
-   느린 연결로 구성된 사이트 서버가 포함된 각각의 기존 경계 그룹 복사본이 만들어집니다. 새 그룹의 이름은 ***\<원래 경계 그룹 이름>-Slow-Tmp***입니다.  
    -   빠른 연결이 있는 사이트 시스템은 원래 경계 그룹에 남아 있습니다.
    -   느린 연결이 있는 사이트 시스템의 복사본이 경계 그룹 복사본에 추가됩니다. 느린 연결로 구성된 원래 사이트 시스템은 이전 버전과의 호환성을 위해 원래 경계 그룹에 남아 있지만 해당 경계 그룹에서 사용되지 않습니다.
    -   이 경계 그룹에는 연결된 경계가 없습니다. 그러나 원래 그룹과 대체 시간이 0으로 설정된 새 경계 그룹 복사본 사이에 대체 링크가 만들어집니다.

 다음 표에서는 원래 배포 설정과 배포 지점 구성의 조합에서 사용할 수 있는 새 대체 동작을 식별합니다.

느린 네트워크의 "프로그램 실행 안 함"에 대한 원래 배포 구성  |"클라이언트에서 콘텐츠에 대한 대체 원본 위치를 사용하도록 허용"에 대한 원래 배포 지점 구성  |새 대체 동작  
---------|---------|---------
선택됨     |  선택됨    |  **대체 없음** - 현재 경계 그룹에 있는 배포 지점만 사용합니다.       
선택됨     |  선택되지 않음|  **대체 없음** - 현재 경계 그룹에 있는 배포 지점만 사용합니다.       
선택되지 않음 |  선택되지 않음|  **인접으로 대체** - 현재 경계 그룹의 배포 지점을 사용한 다음 인접 경계 그룹의 배포 지점을 추가합니다. 기본 사이트 경계 그룹에 대한 명시적 링크를 구성하지 않으면 클라이언트가 해당 그룹으로 대체하지 않습니다.    
선택되지 않음 | 선택됨     |   **기본 대체** - 현재 경계 그룹의 배포 지점을 사용한 다음 인접 및 사이트 기본 경계 그룹의 배포 지점을 사용합니다.

 다른 모든 배포 구성은 **일반 대체**가 됩니다.  



## <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드  
Configuration Manager 1609 Technical Preview에서는 새로운 대시보드를 소개합니다. 대시보드를 보려면 Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.
>[!NOTE]
>Configuration Manager 콘솔의 **새로운 기능** 작업 영역에서 새 대시보드의 이름이 **Office 365 서비스 대시보드**로 잘못 지정되어 있습니다.

대시보드는 다음에 대한 차트를 표시합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널     
자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](https://technet.microsoft.com/library/mt455210.aspx)를 참조하세요.
- 사용 가능한 제품 집합에서 Office 365 클라이언트를 선택한 자동 배포 규칙입니다.

대시보드에서 다음 작업을 수행할 수 있습니다.
- 대시보드 맨 위에 있는 **컬렉션** 드롭다운 설정을 사용하여 특정 컬렉션 멤버별로 대시보드 데이터를 필터링합니다.
- 대시보드 오른쪽 위에서 **Office 365 설치 관리자**를 클릭하여 Office 365 클라이언트 설치 마법사를 시작하고 Office 365 앱을 클라이언트에 배포합니다. 자세한 내용은 [클라이언트에 Office 365 앱 배포](#deploy-office-365-apps-to-clients)를 참조하세요.
- 대시보드의 오른쪽 가운데에서 **ADR 만들기**를 클릭하여 자동 배포 규칙 마법사를 열고 새 ADR(자동 배포 규칙)을 만듭니다. Office 365 앱에 대한 ADR을 만들려면 제품을 선택할 때 **Office 365 클라이언트**를 선택합니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)를 참조하세요.
- 대시보드 오른쪽 아래에서 **클라이언트 에이전트 설정 만들기**를 클릭하여 클라이언트 에이전트 설정을 엽니다. 자세한 내용은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings)를 참조하세요.



Office 365 ProPlus 업데이트에 대한 자세한 내용은 [Manage Office 365 ProPlus updates with Configuration Manager](/sccm/sum/deploy-use/manage-office-365-proplus-updates)(Configuration Manager에서 Office 365 ProPlus 업데이트 관리)를 참조하세요.

## <a name="deploy-office-365-apps-to-clients"></a>클라이언트에 Office 365 앱 배포
이 릴리스에서는 Office 365 클라이언트 관리 대시보드에서 Office 365 설치 설정을 구성할 수 있는 Office 365 설치 관리자를 시작하고, Office CDN(Content Delivery Network)에서 파일을 다운로드하고, 파일을 Configuration Manager의 응용 프로그램으로 배포할 수 있습니다.

### <a name="limitations-of-office-365-deployment"></a>Office 365 배포의 제한 사항
- Office 365 앱 설치 마법사에서 기존 클라이언트 설정(XML)을 가져오려고 할 때 문제가 발생할 수 있습니다. 클라이언트 설정을 문제 없이 수동으로 구성할 수 있습니다.

#### <a name="to-deploy-office-365-apps-to-clients"></a>클라이언트에 Office 365 앱을 배포하려면
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다.
2. 오른쪽 위 창에서 **Office 365 설치 관리자**를 클릭합니다. Office 365 클라이언트 설치 마법사가 열립니다.
3. **응용 프로그램 설정** 페이지에서 앱에 대한 이름과 설명을 제공하고 파일에 대한 다운로드 위치를 입력한 후 **다음**을 클릭합니다. 위치는 &#92;&#92;*server*&#92;*share* 형식으로 지정해야 합니다.
4. **클라이언트 설정 가져오기** 페이지에서, 기존 XML 구성 파일에서 Office 365 클라이언트 설정을 가져올지 아니면 설정을 수동으로 지정할지 여부를 지정하고 **다음**을 클릭합니다.
기존 구성 파일이 있는 경우 해당 파일의 위치를 입력하고 7단계로 건너뜁니다. 위치는 &#92;&#92;*server*&#92;*share*&#92;*filename*.XML 형식으로 지정해야 합니다.

    > [!IMPORTANT]
    >이 Technical Preview에서 기존 클라이언트 설정(XML)을 가져오려고 할 때 문제가 발생할 수 있습니다.

5. **클라이언트 제품** 페이지에서 사용할 Office 365 제품군을 선택하고, 포함할 응용 프로그램을 선택하고, 포함할 추가 Office 제품을 선택한 후 **다음**을 클릭합니다.
6. **클라이언트 설정** 페이지에서 포함할 설정을 선택하고 **다음**을 클릭합니다.
7. **배포** 페이지에서 응용 프로그램을 배포할지 여부를 선택하고 **다음**을 클릭합니다.
마법사에서 패키지를 배포하지 않도록 선택한 경우 9단계로 건너뜁니다.
8. 마법사 페이지의 나머지 부분을 일반적인 응용 프로그램 배포와 마찬가지로 구성합니다. 자세한 내용은 [응용 프로그램 만들기 및 배포](/sccm/apps/get-started/create-and-deploy-an-application)를 참조하세요.
9. 마법사를 완료합니다.
10. Configuration Manager의 **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **응용 프로그램**에서 다른 응용 프로그램과 마찬가지로 응용 프로그램을 배포 또는 편집할 수 있습니다.

>[!NOTE]
>Office 365 앱을 배포한 후 앱을 유지 관리하기 위한 자동 배포 규칙을 만들 수 있습니다. Office 365 앱에 대한 ADR을 만들려면 제품을 선택할 때 **ADR 만들기**를 클릭하고 **Office 365 클라이언트**를 선택합니다. 자세한 내용은 [소프트웨어 업데이트 자동 배포](/sccm/sum/deploy-use/automatically-deploy-software-updates)를 참조하세요.

## <a name="a-namebkmkueficonversionaimprovements-for-bios-to-uefi-conversion"></a><a name="BKMK_UEFIConversion"></a>BIOS-UEFI 변환의 향상된 기능
이제 새로운 변수인 TSUEFIDrive를 사용하여 운영 체제 배포 작업 순서를 사용자 지정하여 UEFI로 전환하기 위해 컴퓨터 다시 시작 단계에서 하드 드라이브의 FAT32 파티션을 준비하도록 할 수 있습니다. 다음 절차는 BIOS-UEFI 변환을 위해 하드 드라이브를 준비하기 위한 작업 순서 단계를 만드는 방법의 예를 제공합니다.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>UEFI로 변환하기 위해 FAT32 파티션을 준비하려면:
운영 체제를 설치하는 기존 작업 순서에서 BIOS-UEFI 변환을 수행하는 단계가 포함된 새 그룹을 추가합니다.

1. 파일 및 설정을 캡처하는 단계와 운영 체제 단계 사이에 새 작업 순서 그룹을 만듭니다. 예를 들어 **파일 및 설정 캡처**라는 그룹 뒤에 **BIOS-UEFI**라는 그룹을 만듭니다.
2. 새 그룹의 **옵션** 탭에서 새 작업 순서 변수를 **_SMSTSBootUEFI**가 **true**와 **같지 않음**인 조건으로 추가합니다. 이렇게 하면 컴퓨터가 이미 UEFI 모드에서 실행 중인 경우 이 그룹의 단계가 실행되지 않습니다.
![BIOS-UEFI 그룹](media/BIOS-to-UEFI-group.png)
3. 새 그룹 아래에 **컴퓨터 다시 시작** 작업 순서 단계를 추가합니다. **다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.**에서 **이 작업 순서에 할당된 부팅 이미지**를 선택하여 Windows PE에서 컴퓨터를 시작합니다.  
4. **옵션** 탭에서 작업 순서 변수를 **_SMSTSInWinPE = false**인 조건으로 추가합니다. 이렇게 하면 컴퓨터가 이미 Windows PE에서 실행 중인 경우 이 단계가 실행되지 않습니다.

    ![컴퓨터 다시 시작 단계](media/Restart-in-Windows-PE.png)
5. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구를 시작하는 단계를 추가합니다. 이 단계는 일반적으로 명령줄을 사용하여 OEM 도구를 시작하는 **명령줄 실행** 작업 순서 단계가 됩니다.
5.  하드 드라이브의 파티션을 나누고 포맷하는 디스크 포맷 및 파티션 만들기 작업 순서 단계를 추가합니다. 이 단계에서 다음을 수행합니다.
    1.  운영 체제를 설치하기 전에 UEFI로 변환하는 FAT32 파티션을 만듭니다. **디스크 유형**에 대해 **GPT**를 선택합니다.
    ![디스크 포맷 및 파티션 만들기 단계](media/Format-and-partition-disk.png)
    2.  FAT32 파티션의 속성으로 이동합니다. **변수** 필드에 **TSUEFIDrive**를 입력합니다. 작업 순서에서 이 변수를 발견하면 컴퓨터를 다시 시작하기 전에 UEFI 변환을 준비합니다.
    ![파티션 속성](media/Partition-properties.png)
    3. 작업 순서 엔진이 상태를 저장하고 로그 파일을 저장하는 데 사용할 NTFS 파티션을 만듭니다.
6.  **컴퓨터 다시 시작** 작업 순서 단계를 추가합니다. **다시 시작한 후에 실행할 응용 프로그램을 지정하십시오.**에서 **이 작업 순서에 할당된 부팅 이미지**를 선택하여 Windows PE에서 컴퓨터를 시작합니다.  




## <a name="intune-compliance-charts"></a>Intune 준수 차트
이 릴리스에서는 Configuration Manager 콘솔의 **모니터링 작업 영역** 아래에 있는 새 차트를 사용하여 장치의 전체 준수 및 주요 비준수 이유에 대한 간략한 보기를 볼 수 있습니다.

#### <a name="to-view-the-intune-compliance-charts"></a>Intune 준수 차트를 보려면
1. Configuration Manager 콘솔에서 **모니터링** > **개요** > **준수 설정**으로 이동합니다.
2. **전체 장치 준수** 차트가 표시됩니다.
3. **준수 정책** 노드를 클릭하여 **전체 장치 준수** 및 **주요 비준수 이유** 차트를 표시합니다.

### <a name="limitations-of-intune-compliance-charts-in-tp-1609"></a>TP 1609의 Intune 준수 차트 제한 사항
- 현재 **전체 장치 준수** 차트에 대해 드릴다운을 실행하면 오류가 발생합니다.
- **주요 비준수 이유** 차트에는 정책 이름이 나열되며 개별 비준수 이유는 나열되지 않습니다. 드릴다운할 정책을 클릭하여 해당 정책을 준수하지 않는 장치를 볼 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
다음 섹션을 순서대로 완료합니다.

#### <a name="check-overall-compliance-chart"></a>전체 준수 차트 확인
1. Configuration Manager에 두 개의 iOS 준수 정책을 추가합니다. 하나의 정책에는 장치에 대한 하나의 설정 집합(예: PIN 길이를 6으로 설정)이 있어야 합니다. 다른 정책에는 다른 설정 집합(예: PIN 복잡도)이 있어야 합니다. 정책 설정이 겹치거나 충돌하지 않아야 합니다.
2. 사용자 집합에 두 개의 정책을 배포합니다.
3. 동일한 사용자 계정 및 이전 단계에서 정책을 받은 계정을 사용하여 Intune에 두 개의 iOS 장치를 등록합니다. 장치가 준수 정책 기준을 충족하지 않아야 합니다.
4. Configuration Manager에서 **전체 장치 준수** 차트를 확인합니다. 두 장치가 비규격으로 보고되어야 합니다.
<!-- 5. Click the **Non-compliant** section of the chart. Both devices should appear in the filtered view under **Assets and Compliance** > **Overview** > **Device**. -->

#### <a name="check-the-top-non-compliance-reasons-chart"></a>주요 비준수 이유 차트 확인
5. **주요 비준수 이유** 차트를 확인합니다. 이 차트에는 5가지 주요 비준수 이유가 나열되지만 정책에 두 개의 준수 설정만 있는 경우 2개의 주요 비준수 이유만 표시됩니다.
6. 차트의 섹션 중 하나를 클릭합니다. 두 장치 모두 **자산 및 준수** > **개요** > **장치**의 필터링된 뷰에 나타납니다.

#### <a name="make-devices-compliant-and-check-the-charts"></a>장치를 준수하도록 만들고 차트를 확인합니다.
7. 장치 중 하나가 정책 중 하나를 준수하도록 만듭니다. **전체 장치 준수** 차트를 다시 확인합니다. 차트에 하나의 준수 장치와 하나의 비준수 장치가 표시되어야 합니다.
8. 다른 장치가 동일한 정책을 준수하도록 만듭니다. 이렇게 하면 두 정책을 준수하는 장치 하나와 정책 중 하나만 준수하는 장치 하나가 만들어집니다.
9. **주요 비준수 이유** 차트를 확인합니다. 비준수 이유가 하나만 나열되어야 합니다.
<!--7. Click the **Compliant** section of the chart. Only the compliant device should appear in the filtered view. -->





## <a name="see-also"></a>참고 항목
[System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)



<!--HONumber=Dec16_HO3-->


