---
title: "Configuration Manager에서 Apple Configurator를 사용한 iOS 하이브리드 등록"
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
caps.latest.revision: 5
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 19f4880d6e7ba3da2e4bcfe725c1c806ee3b3334


---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>Configuration Manager에서 Apple Configurator를 사용한 iOS 하이브리드 등록

*적용 대상: System Center Configuration Manager(현재 분기)*

직원이 사용할 iOS 장치를 구입한 회사는 Microsoft Intune을 사용하여 장치를 관리할 수 있습니다. Apple Configurator를 실행하는 Mac PC에 iOS 장치를 USB로 연결하여 미리 등록할 수 있습니다. 등록하기 전에 Intune 관리 콘솔에서 Intune 회사 등록 장치 프로필을 준비한 다음 Mac PC로 내보내야 합니다. 등록 프로세스는 장치를 초기화하고 설정 도우미 프로세스를 통해 장치를 구성합니다. 장치를 사용하여 회사 메일과 앱, 데이터 등의 회사 리소스에 액세스하는 단일 사용자가 있는 전용 iOS 장치에는 다음 절차를 사용하는 것이 좋습니다.  

##  <a name="a-namebkmksaea-apple-configurator-enrollment-via-setup-assistant"></a><a name="BKMK_SAE"></a> 설정 도우미를 통한 Apple Configurator 등록  
 Apple 구성기를 사용하면 iOS 장치를 초기화하여 장치의 새 사용자가 설정할 수 있도록 준비할 수 있습니다.  이 방법을 사용하려면 iOS 장치를 Mac 컴퓨터에 USB로 연결하여 회사 등록을 설정해야 하며 사용자가 Apple Configurator 2.0을 사용하고 있는 것으로 간주됩니다.  

 **전제 조건**  

-   IOS 장치에 대한 실제 액세스  

-   장치 일련 번호 - [iOS 일련 번호를 가져오는 방법](https://support.apple.com/en-us/HT204308)  

-   USB 연결 케이블  

-   [Apple Configurator 2.0](http://go.microsoft.com/fwlink/?LinkId=518017)이 있는 Mac 컴퓨터  

#### <a name="enable-setup-assistant-enrollment-with-configuration-manager-and-intune"></a>Configuration Manager 및 Intune에 설치 도우미 등록 사용  

1.  **회사 장치 등록 프로필 추가**   
    Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **개요**, **회사가 소유한 모든 장치**, **iOS**를 차례로 확장하고 **등록 프로필**을 클릭합니다. **홈** 탭에서 **프로필 만들기** 를 클릭하여 프로필 만들기 마법사를 엽니다. 다음 페이지에서 설정을 구성합니다.  

    1.  **일반** 페이지에서 다음 정보를 지정한 후에 **다음**을 클릭합니다.  

        -   **이름** – 장치 등록 프로필의 이름입니다. (사용자에게는 보이지 않음)  

        -   **설명** – 장치 등록 프로필에 대한 설명입니다. 사용자에게는 표시되지 않습니다.  

        -   **사용자 선호도** – 장치의 등록 방식을 지정합니다. 대부분의 설치 도우미 시나리오의 경우 **사용자 선호도 확인**을 사용합니다.  

            -   **사용자 선호도 확인**: 초기 설치 작업을 진행할 때 장치에 사용자 정보를 등록해야 합니다. 그러면 장치가 해당 사용자 자격으로 회사 데이터와 메일에 액세스할 수 있게 됩니다.  

            -   **사용자 선호도 없음**: 장치에 사용자 정보를 등록하지 않습니다. 로컬 사용자 데이터에 액세스하지 않고도 작업을 수행하는 장치에 대해 이 정보를 사용합니다. 사용자 정보를 필요로 하는 앱이 작동하지 않습니다.  

    2.  **장치 등록 프로그램** 페이지에서 **이 프로필에 대한 장치 등록 프로그램 설정을 구성합니다.** 확인란을 선택 취소하고 **다음**을 클릭합니다.  

    3.  요약 내용을 검토하고 네트워크를 클릭합니다.  

2.  **설정 도우미를 사용하여 등록할 iOS 장치 추가**   
    Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **개요**, **회사가 소유한 모든 장치**, **iOS**를 차례로 확장하고 **장치 정보**를 클릭합니다. 그런 후 **장치 추가**를 클릭합니다. 두 가지 방법으로 장치를 추가할 수 있습니다.  

    - **일련 번호가 포함된 CSV 파일 업로드** – 헤더 없이 두 열로 이루어진 쉼표로 구분된 값 목록을 만듭니다. csv 파일당 장치 5,000대 또는 용량 5MB로 제한됩니다. 각 행에서 첫 번째 셀은 장치 일련 번호이고, 두 번째 셀은 장치 세부 정보(선택 사항)입니다.

  이.csv 파일을 텍스트 편집기에서 보면 다음과 같이 표시됩니다.  

    ```  
    0000000,PO 1234  
    111111111,PO 1234  
    ```  

    - **수동으로 일련 번호 및 세부 정보 추가** - 최대 5개 장치에 대한 일련 번호와 장치 세부 정보를 입력합니다.  

    그리고 **다음**을 클릭합니다.  

3.  **등록할 장치 선택**   
    등록할 장치를 확인합니다. 이미 등록되어 있거나 다른 방식으로 등록된 일련 번호는 가져올 수 없습니다. **다음** 을 클릭하여 계속합니다.  

4.  **프로필 할당**   
    사용할 수 있는 프로필 목록에서 추가된 장치에 할당할 프로필을 지정하고 **등록 프로필 세부 정보**를 클릭한 후 **마침**을 클릭합니다. 수동으로 추가한 장치는 어떤 등록 프로필에나 할당할 수 있지만 DEP와 동기화된 장치는 DEP 지원 프로필에 할당해야 합니다.  

5.  **iOS 장치에 배포할 프로필 선택**   
    Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **개요**, **회사가 소유한 모든 장치**, **iOS**를 차례로 확장하고 **등록 프로필**을 클릭한 다음 모바일 장치에 배포할 장치 프로필을 선택합니다. 작업 표시줄에서 **내보내기...** 를 클릭합니다. **프로필 URL**을 복사하고 저장합니다. iOS 장치에서 사용하는 Intune 프로필을 정의하기 위해 나중에 Apple Configurator에서 업로드합니다.  등록 프로필 URL은 내보낸 후 2주 동안 유효합니다. 2주 후에는 iOS 장치를 등록할 새 URL 파일을 내보내야 합니다.  

     Apple 구성기 2를 지원하려면 2.0 프로필 URL을 편집해야 합니다. 다음을  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     다음으로 바꿉니다.  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```  

6.  **Apple Configurator를 사용하여 장치 준비**   
    iOS 장치는 Mac 컴퓨터에 연결되고 모바일 장치 관리를 위해 등록됩니다.  

    > [!WARNING]  
    >  장치는 등록 프로세스 중에 공장 설정으로 다시 복원됩니다.  

    1.  Mac 컴퓨터에서 **Apple Configurator 2**를 엽니다.  메뉴 모음에서 **Apple Configurator 2**, **기본 설정**을 차례로 클릭합니다.  

    2.  기본 설정 창에서 **서버**를 선택하고 왼쪽 창 아래에 있는 "+" 기호를 클릭하여 MDM 서버 마법사를 시작합니다. **다음**을 클릭합니다.  

    3.  위 5단계의 MDM 서버에 대한 **이름** 및 **등록 URL**을 입력합니다. **다음**을 클릭합니다.  

         Apple TV에 대한 트러스트 프로필 요구 사항에 대한 경고가 표시되면 회색 "X"를 클릭하여 **신뢰 프로필** 옵션을 안전하게 취소할 수 있습니다. 또한 앵커 인증서 경고도 안전하게 무시할 수 있습니다. 계속하려면 마법사가 완료될 때까지 **다음**을 클릭합니다.  

    4.  **서버** 창에서 새 서버 프로필 옆에 있는 "편집"을 클릭합니다. 등록 URL이 Intune에서 내보낸 URL과 정확하게 일치하는지 확인합니다. 두 URL이 다른 경우 원래 URL을 다시 입력하고 Intune에서 내보낸 등록 프로필을 **저장**합니다.  

    5.  USB 어댑터를 사용하여 Apple 컴퓨터에 iOS 모바일 장치를 연결합니다.  

        > [!WARNING]  
        >  장치는 등록 프로세스 중에 공장 설정으로 다시 복원됩니다. 모범 사례에 따라 장치를 다시 설정하고 전원을 켭니다. 모범 사례에 따르면 설정 도우미를 시작할 때 Hello 화면에 장치가 있습니다.  

    6.  **준비**를 클릭합니다. **iOS 장치 준비** 창에서 **수동**을 선택하고 **다음**을 클릭합니다.  

    7.  **MDM 서버에 등록** 창에서 앞서 생성한 서버 이름을 선택하고 **다음**을 클릭합니다.  

    8.  **MDM 서버에 등록** 창에서 앞서 생성한 서버 이름을 선택하고 **다음**을 클릭합니다.  

    9. **조직 만들기** 창에서 **조직**을 선택하거나 새 조직을 만든 후 **다음**을 클릭합니다.  

    10. **iOS 설정 도우미 구성** 창에서 사용자에게 제공할 단계를 선택하고 **준비**를 클릭합니다. 메시지가 표시되면 신뢰 설정을 업데이트하도록 인증합니다.  

    11. IOS 장치가 준비를 완료하면 USB 케이블 연결을 끊을 수 있습니다.  

7.  **장치 배포**   
    이제 장치를 회사에 등록할 준비가 되었습니다. 장치를 끈 다음 사용자에게 배포합니다. 장치를 켜면 설치 도우미가 시작되고 회사 또는 학교 계정을 입력하라는 메시지가 표시됩니다.



<!--HONumber=Nov16_HO1-->


