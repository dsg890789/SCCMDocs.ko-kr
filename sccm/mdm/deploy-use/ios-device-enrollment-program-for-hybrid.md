---
title: "DEP(장치 등록 프로그램)를 사용하여 iOS 장치 등록 - Configuration Manager | Microsoft 문서"
description: "Configuration Manager 및 Intune에서 하이브리드 배포를 위해 iOS DEP(장치 등록 프로그램) 등록을 사용하도록 설정합니다."
ms.custom: na
ms.date: 09/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: "9"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: f34f7527c14e1be6229212bfb2d8fd022ee6defe
ms.sourcegitcommit: 8faf42135a8dc9c384407e64f3f8ba204fb15847
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2017
---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>Configuration Manager에서의 하이브리드 배포를 위한 iOS DEP(장치 등록 프로그램) 등록

*적용 대상: System Center Configuration Manager(현재 분기)*

회사에서 Apple 장비 등록 프로그램을 통해 iOS 장치를 구입한 다음 Microsoft Intune을 사용하여 관리할 수 있습니다. Apple DEP(장치 등록 프로그램)를 사용하여 회사 소유 iOS 장치를 관리하려는 회사에서는 Apple에서 요구하는 단계를 완료하여 프로그램에 참여하고 해당 프로그램을 통해 장치를 가져와야 합니다. 해당 프로세스의 세부 정보는  [https://deploy.apple.com](https://deploy.apple.com)으로 관리할 수 있습니다. 이 프로그램의 이점 중 하나는 USB로 각 장치를 컴퓨터에 연결하지 않고도 장치를 자동 설치할 수 있다는 것입니다.  

 회사 소유 iOS 장치를 DEP에 등록하려면 Apple의 DEP 토큰이 필요합니다. Intune에서는 이 토큰을 통해 회사에서 소유한 DEP 참가 장치에 대한 정보를 동기화할 수 있습니다. 또한 Intune에서 등록 프로필을 Apple에 업로드하고 해당 프로필에 장치를 할당할 수 있게 합니다.  

## <a name="apple-dep-enrollment-for-ios-devices"></a>Apple DEP로 iOS 장치 등록  
 다음 절차에서는 Apple DEP를 통해 구입한 iOS 장치를 Intune에서 관리되는 회사 소유 장치로 지정하는 방법을 설명합니다. 사용자가 장치 전원을 처음 켤 때 DEP 관리 프로필이 수신되고 설정 도우미가 실행되며 관리가 적용됩니다.  

##  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>Configuration Manager와 Intune에서 DEP 등록 사용  

1.  **Configuration Manager로 iOS 장치 관리 시작**   
    iOS DEP(장치 등록 프로그램) 장치를 등록하려면 먼저 [iOS 등록 지원 단계](../deploy-use/enroll-hybrid-ios-mac.md)를 포함하여 [하이브리드 모바일 장치 관리 설정](../../mdm/deploy-use/setup-hybrid-mdm.md) 단계를 완료해야 합니다.
2.  **DEP 토큰 요청 만들기**   
    Configuration Manager 콘솔의 **관리** 작업 영역에서 **계층 구성**, **클라우드 서비스**를 차례로 확장하고 **Microsoft Intune 구독**을 클릭합니다. **홈** 탭에서 **DEP 토큰 요청 만들기** 를 클릭하고 **찾아보기** 를 클릭하여 DEP 토큰 요청에 대한 다운로드 위치를 지정한 후에 **다운로드**를 클릭합니다. DEP 토큰 요청(.pem) 파일을 로컬로 저장합니다. .pem 파일은 Apple 장치 등록 프로그램 포털에서 신뢰할 수 있는 토큰(.p7m)을 요청하는 데 사용됩니다.  
3.  **장치 등록 프로그램 토큰 가져오기**   
    [장치 등록 프로그램 포털](https://deploy.apple.com) (https://deploy.apple.com) 로 이동하고 회사 Apple ID로 로그인합니다. 나중에 DEP 토큰을 갱신하려면 이 Apple ID를 사용해야 합니다.  
    1.  [장치 등록 프로그램 포털](https://deploy.apple.com)에서 **장치 등록 프로그램** > **서버 관리**로 이동한 후 **MDM 서버 추가**를 클릭합니다.  
    ![장비 등록 프로그램 포털에서 MDM 서버 추가 스크린샷](../media/enrollment-program-token-add-server.png)
    2.  **MDM 서버 이름**을 입력한 다음 **다음**을 클릭합니다. 서버 이름은 참조용으로 MDM 서버를 식별하기 위한 것으로, Intune 또는 Configuration Manager 서버의 URL이나 이름이 아닙니다.  
    3.  **<ServerName\> 추가** 대화 상자가 열립니다. **파일 선택... 클릭하여** 을 클릭하여 이전 단계에서 만든 .pem 파일을 업로드하고 **다음**.  
    4.  **<ServerName\> 추가** 대화 상자에 **내 서버 토큰** 링크가 표시됩니다. 컴퓨터에 서버 토큰(으로 관리할 수 있습니다.p7m) 파일을 다운로드한 후 **완료**으로 관리할 수 있습니다.  

     이 인증서(.p7m) 파일은 Intune과 Apple 장치 등록 프로그램 서버 간에 트러스트 관계를 설정하는 데 사용됩니다.  
4.  **Configuration Manager에 DEP 토큰 추가**   
    Configuration Manager 콘솔의 **관리** 작업 영역에서 **계층 구성**을 확장하고 **Windows Intune 구독**을 클릭합니다. **홈** 탭에서 **플랫폼 구성** 을 클릭하고 **iOS**를 클릭합니다. **장치 등록 프로그램 사용**을 선택하고 인증서(.p7m) 파일을 찾은 다음 **열기**, **업로드**, **확인**을 차례로 클릭합니다.  

## <a name="add-a-corporate-device-enrollment-policy"></a>회사 장치 등록 정책 추가  

1. Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **개요**, **회사가 소유한 모든 장치**, **iOS**를 차례로 확장하고 **등록 프로필**을 클릭합니다. **홈** 탭에서 **프로필 만들기** 를 클릭하여 프로필 만들기 마법사를 엽니다. 다음 페이지에서 설정을 구성합니다.  
2. **일반** 페이지에서 다음 정보를 지정한 후에 **다음**을 클릭합니다.  
  -   **이름** – 장치 등록 프로필의 이름입니다. (사용자에게는 보이지 않음)  
  -   **설명** – 장치 등록 프로필에 대한 설명입니다. 사용자에게는 표시되지 않습니다.  
  -   **사용자 선호도** – 장치의 등록 방식을 지정합니다. [Configuration Manager의 하이브리드 관리 장치에 대한 사용자 선호도](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md)를 참조하세요.  

      -  **사용자 선호도 확인**: 초기 설치 작업을 진행할 때 장치에 사용자 정보를 등록해야 합니다. 그러면 장치가 해당 사용자 자격으로 회사 데이터와 메일에 액세스할 수 있게 됩니다.  사용자에게 속해 있으며 회사 포털을 사용해야 하는(즉, 앱을 설치해야 하는) DEP 관리 장치에 대한 사용자 선호도를 구성해야 합니다.  
      > [!NOTE]
      > 사용자 선호도 포함 DEP에서 사용자 토큰을 요청하려면 ADFS WS-Trust 1.3 사용자 이름/혼합 끝점을 사용하도록 설정해야 합니다.

      -   **사용자 선호도 없음**: 장치에 사용자 정보를 등록하지 않습니다. 로컬 사용자 데이터에 액세스하지 않고도 작업을 수행하는 장치에 대해 이 정보를 사용합니다. 사용자 정보를 필요로 하는 앱이 작동하지 않습니다.  
    ![DEP 프로필 이름, 설명 및 사용자 선호도 프롬프트 스크린샷](../media/dep-general.png)

3. **장치 등록 프로그램 설정** 페이지에서 아래 정보를 지정하고 **다음**을 클릭합니다.  
    -   **부서** - 이 정보는 활성화하는 동안 사용자가 "구성 정보"를 탭할 때 나타납니다.  
    -   **지원 전화 번호** - 활성화하는 동안 사용자가 **도움 요청** 단추를 클릭할 때 표시됩니다.
       ![iOS 장치에 DEP 프로필 할당 스크린샷](../media/dep-settings.png)

    - **준비 모드** - 이 상태는 활성화하는 동안 설정되며 장치를 초기화하지 않으면 변경할 수 없습니다.  
        -   **감독되지 않음** - 관리 기능이 제한됩니다.  
        -   **감독됨** - 더 많은 관리 옵션을 사용할 수 있으며 기본적으로 활성화 잠금이 해제됩니다.  
    - **장치에 등록 프로필 잠금** - 이 상태는 활성화하는 동안 설정되며 초기화하지 않으면 변경할 수 없습니다.  
      -   **사용 안 함** - **설정** 메뉴에서 관리 프로필을 제거할 수 있습니다.  
      -   **사용** - (**준비 모드** = **감독됨** 필요) 관리 프로필 제거를 허용하는 iOS 설정이 해제됩니다.  

4.  **설정 도우미** 페이지에서 장치를 처음 켤 때 시작되는 iOS 설정 도우미를 사용자 지정하는 설정을 구성하고 **다음**을 클릭합니다. 이러한 설정은 다음과 같습니다.  
  -   **암호** - 활성화하는 동안 암호를 확인하는 메시지가 표시됩니다. 장치 보안이 유지되거나 다른 방식(즉, 장치를 하나의 앱으로 제한하는 키오스크 모드)으로 액세스가 제어되지 않는 경우 항상 암호가 필요합니다.  
  -   **위치 서비스** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 서비스를 확인하는 메시지가 표시됩니다.  
  -   **복원** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 iCloud 백업을 확인하는 메시지가 표시됩니다.  
  -   **Apple ID** - Intune에 의해 설치된 앱을 포함하여 iOS App Store 앱을 다운로드하려면 Apple ID가 필요합니다. 이 옵션을 사용하도록 설정하면 Intune에서 ID 없이 앱을 설치하려고 할 때 iOS에서 Apple ID를 확인하는 메시지가 표시됩니다.  
  -   **계약조건** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 Apple 계약조건에 동의하라는 메시지가 표시됩니다.  
  -   **터치 ID** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.
  -   **Apple Pay** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.
  -   **확대/축소** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.
  -   **Siri** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.  
  -   **Apple에 진단 데이터 보내기** - 이 옵션을 사용하도록 설정하면 활성화하는 동안 설정 도우미에서 이 서비스를 확인하는 메시지가 표시됩니다.  
    ![iOS 장치에 DEP 프로필 할당 스크린샷](../media/dep-setup-assistant.png)
5.  **추가 관리** 페이지에서 USB 연결을 추가 관리 설정에 사용할 수 있는지 여부를 지정합니다. **인증서 필요**를 선택하는 경우 이 프로필에 사용할 Apple 구성기 관리 인증서를 가져와야 합니다.  **허용 안 함**으로 설정하면 iTunes와 파일을 공유하거나 Apple Configurator를 통해 관리할 수 없습니다. 이 설정을 통해 인증서를 사용하거나 사용하지 않는 수동 배포를 허용하는 대신 **허용 안 함**으로 설정하고 Apple Configurator에서 추가 구성을 내보낸 다음 사용자 지정 iOS 구성 프로필로 배포하는 것이 좋습니다.  

  -   **허용 안 함** - 장치가 USB를 통해 통신할 수 없도록 합니다(연결 사용 안 함).  
  -   **허용** - 장치가 USB 연결을 통해 모든 PC 또는 Mac과 통신할 수 있습니다.  
  -   **인증서 필요**- 등록 프로필로 가져온 인증서를 사용하여 Mac에 연결할 수 있습니다.  

## <a name="assign-dep-devices-for-management"></a>관리할 DEP 장치 할당

1. [장치 등록 프로그램 포털](https://deploy.apple.com) (https://deploy.apple.com) 로 이동하고 회사 Apple ID로 로그인합니다.
2. **배포 프로그램** > **장치 등록 프로그램** > **장치 관리**으로 관리할 수 있습니다. **장치 선택**방법을 지정하고, 장치 정보를 제공한 다음 장치 **일련번호**, **주문 번호**또는 **CSV 파일 업로드**에 따라 세부 정보를 지정합니다. **서버에 할당**을 선택하고 3단계에서 지정한 <*서버 이름*>을 선택한 후 **확인**을 클릭합니다.  
![장치를 추가하는 Apple 장비 등록 프로그램 포털 스크린샷](../media/enrollment-program-token-specify-serial.png)

3.  **DEP 관리 장치 동기화**   
    **자산 및 준수** 작업 영역에서 **회사가 소유한 모든 장치** > **미리 선언된 장치**로 이동합니다. **홈** 탭에서 **DEP 동기화**를 클릭합니다. 동기화 요청이 Apple에 전송됩니다. 동기화가 완료되고 나면 DEP에서 관리하는 장치가 표시됩니다.

    > [!NOTE]
    > 하이브리드 구성에서 Configuration Manager의 **DEP 동기화**를 클릭하여 DEP 동기화 작업이 수동으로 트리거됩니다.

4.  **DEP 프로필 할당**<br>**자산 및 준수** 작업 영역에서 **회사가 소유한 모든 장치** > **iOS** > **등록 프로필**로 이동합니다. DEP 등록 프로필을 선택한 다음 **홈** 탭에서 **장치에 할당**을 클릭합니다. 이 등록 프로필을 사용할 장치를 선택하고 **추가**를 클릭한 다음 **확인**을 클릭합니다.   
     ![iOS 장치에 DEP 프로필 할당 스크린샷](../media/dep-assign-profile.png)

## <a name="distribute-devices-to-users"></a>사용자에게 장치 배포
이제 회사 소유 장치를 사용자에게 제공할 수 있습니다. 장치를 켜고 설정 도우미를 실행하여 장치를 등록할 때까지는 관리되는 장치의 **등록 상태** 가 **연결되지 않음** 으로 표시됩니다. IOS 장치를 설정하는 경우에 Intune에 관리용으로 등록됩니다.
