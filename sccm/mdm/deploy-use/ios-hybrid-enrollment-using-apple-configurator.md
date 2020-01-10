---
title: 'Apple Configurator를 사용한 iOS 디바이스 등록 '
titleSuffix: Configuration Manager
descriptions: Pre-enroll iOS devices by using Apple Configurator with Configuration Manager.
ms.date: 08/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 61a19d95-83ff-4ad8-9a67-f304d2ba54f2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 8213b57dbec9d10505240325a173349880c8cd81
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821837"
---
# <a name="ios-hybrid-enrollment-using-apple-configurator-with-configuration-manager"></a>Configuration Manager에서 Apple Configurator를 사용한 iOS 하이브리드 등록

*적용 대상: Configuration Manager (현재 분기)*

직원이 사용할 iOS 디바이스를 구입한 회사는 Microsoft Intune을 사용하여 디바이스를 관리할 수 있습니다. 등록을 위해 회사 소유의 iOS 디바이스를 준비하려면 Configuration Manager 콘솔에서 등록 프로필을 구성한 다음 Apple Configurator에서 사용할 프로필 URL을 내보냅니다. USB 케이블로 Mac 컴퓨터에 연결하고 Apple Configurator를 통해 설정하여 등록할 iOS 디바이스를 준비합니다. Apple Configurator는 디바이스를 초기화하고, 사용자가 처음 전원을 켜고 설정 도우미 프로세스를 수행할 때 디바이스를 등록할 수 있도록 등록 프로필을 추가합니다.

디바이스를 사용하여 회사 메일과 앱, 데이터 등의 회사 리소스에 액세스하는 단일 사용자가 있는 전용 iOS 디바이스에는 다음 절차를 사용하는 것이 좋습니다.  

## <a name="prerequisites"></a>전제 조건  

-   IOS 디바이스에 대한 실제 액세스  

-   디바이스 일련 번호 - [iOS 일련 번호를 가져오는 방법](https://support.apple.com/en-us/HT204308)  

-   [Apple Configurator 2.0](https://go.microsoft.com/fwlink/?LinkId=518017)이 있는 Mac 컴퓨터  

-   Mac 컴퓨터에 디바이스를 연결하기 위한 USB 케이블  

## <a name="add-a-corporate-owned-device-enrollment-profile"></a>회사 소유 디바이스 등록 프로필 추가

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **모든 회사 소유 디바이스** > **iOS** > **등록 프로필**로 이동합니다. **프로필 만들기**를 클릭하여 프로필 만들기 마법사를 엽니다. 다음 페이지에서 설정을 구성합니다.  

2.  **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름**(사용자에게는 보이지 않음)  

    -   **설명**(사용자에게는 보이지 않음)  

    -   **사용자 선호도** – 디바이스의 등록 방식을 지정합니다. 대부분의 설정 도우미 시나리오에서 **사용자 선호도 확인**을 사용합니다.  

        -   **사용자 선호도 확인**: 초기 설치 작업을 진행할 때 디바이스에 사용자 정보를 등록해야 합니다. 그러면 디바이스가 해당 사용자 자격으로 회사 데이터와 메일에 액세스할 수 있게 됩니다.  

        -   **사용자 선호도 없음**: 디바이스에 사용자 정보를 등록하지 않습니다. 로컬 사용자 데이터에 액세스하지 않고도 작업을 수행하는 디바이스에 대해 이 정보를 사용합니다. 사용자 정보를 필요로 하는 앱이 작동하지 않습니다.

    **다음** 을 클릭하여 계속합니다.  

3.  **디바이스 등록 프로그램** 페이지에서 **이 프로필에 대한 디바이스 등록 프로그램 설정을 구성합니다.** 확인란을 선택 취소하고 **다음**을 클릭합니다.  

4.  요약 내용을 검토하고 **다음**을 클릭하여 등록 프로필을 만듭니다. **닫기**를 클릭하여 마법사를 종료합니다. 이제 등록하려는 디바이스에 대한 IMEI 번호 또는 일련 번호를 추가할 준비가 되었습니다.  

## <a name="predeclare-devices-to-enroll-with-setup-assistant"></a>설정 도우미를 사용하여 등록할 디바이스 미리 선언

이 단계에서는 하드웨어 식별자(IMEI 또는 일련 번호) 목록을 제공하여 디바이스를 회사 소유로 미리 선언합니다.

자세한 내용은 [IMEI 및 iOS 일련 번호로 디바이스 미리 선언](predeclare-devices-with-hardware-id.md)을 참조하세요. 해당 작업을 마쳤으면 이 페이지로 돌아가서 다음 단계를 계속합니다.

## <a name="export-the-profile-to-deploy-to-ios-devices"></a>iOS 디바이스에 배포할 프로필 내보내기

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **모든 회사 소유 디바이스** > **iOS** > **등록 프로필**로 이동합니다.

2.  모바일 디바이스에 배포할 등록 프로필을 선택하고 **내보내기...** 를 클릭합니다.

3.  **프로필 URL**을 복사하고 편집할 수 있는 파일에 저장합니다.   

4.  Apple Configurator 2를 지원하려면 2.0 프로필 URL을 편집해야 합니다. URL의 다음 부분을 바꿉니다.  

    ```  
    https://manage.microsoft.com/EnrollmentServer/Discovery.svc/iOS/ESProxy?id=  

    ```  

     다음으로 바꿉니다.  

    ```  
    https://appleconfigurator2.manage.microsoft.com/MDMServiceConfig?id=  

    ```

5.  편집한 프로필 URL을 저장합니다. [다음 섹션](#prepare-the-device-with-apple-configurator)에서 이 URL을 사용하여 Apple Configurator에서 등록 프로필 URL을 추가합니다.  

> [!NOTE]
> 등록 프로필 URL은 내보낸 날부터 2주 동안 유효합니다. 2주 후에는 iOS 디바이스를 등록할 새 URL을 내보내야 합니다.

## <a name="prepare-the-device-with-apple-configurator"></a>Apple Configurator를 사용하여 디바이스 준비

등록할 iOS 디바이스를 준비하려면 각 디바이스를 Mac 컴퓨터에 연결하고 등록 프로필을 업로드합니다.  

> [!WARNING]  
>  Apple Configurator는 디바이스를 공장 설정으로 초기화합니다.  

1. Mac 컴퓨터에서 **Apple Configurator 2**를 엽니다.  

2. 메뉴 모음에서 **Apple Configurator 2** > **기본 설정**을 클릭합니다.  

3. 기본 설정 창에서 **서버**를 선택하고 왼쪽 창 아래에 있는 "+" 기호를 클릭하여 MDM 서버 마법사를 시작합니다. **다음**을 클릭합니다.  

4. [이전](#export-the-profile-to-deploy-to-ios-devices)에 저장한 **이름** 및 **등록 URL**을 입력합니다. **다음**을 클릭합니다.  

   > [!NOTE]
   > Apple TV에 대한 트러스트 프로필 요구 사항에 대한 경고가 표시되면 회색 "X"를 클릭하여 **신뢰 프로필** 옵션을 안전하게 취소할 수 있습니다. 또한 앵커 인증서 경고도 안전하게 무시할 수 있습니다.

   계속하려면 마법사가 완료될 때까지 **다음**을 클릭합니다.  

5. **서버** 창에서 새 서버 프로필 옆에 있는 "편집"을 클릭합니다. 등록 URL이 이전에 입력한 URL과 정확하게 일치하는지 확인합니다. 다른 경우 URL을 다시 입력하고 **저장**을 클릭합니다.  

6. USB 케이블을 사용하여 iOS 디바이스를 Mac 컴퓨터에 연결합니다.  

   > [!WARNING]  
   >  이 프로세스는 디바이스를 공장 설정으로 초기화합니다. 디바이스를 연결하기 전에 디바이스를 초기화하고 전원을 켭니다. 모범 사례로, 계속하기 전에 디바이스가 Hello 화면에 있어야 합니다.  

7. **준비**를 클릭합니다. **iOS 디바이스 준비** 창에서 **수동**을 선택하고 **다음**을 클릭합니다.  

8. **MDM 서버에 등록** 창에서 앞서 생성한 서버 이름을 선택하고 **다음**을 클릭합니다.  

9. **조직 만들기** 창에서 **조직**을 선택하거나 새 조직을 만든 후 **다음**을 클릭합니다.  

10. **iOS 설정 도우미 구성** 창에서 사용자에게 제공할 단계를 선택하고 **준비**를 클릭합니다. 메시지가 표시되면 신뢰 설정을 업데이트하도록 인증합니다.  

11. 완료되면 USB 케이블 연결을 끊을 수 있습니다.  

등록을 위해 준비할 모든 디바이스에 대해 이러한 단계를 반복합니다.

## <a name="distribute-devices"></a>디바이스 배포

이제 디바이스를 회사에 등록할 준비가 되었습니다. 디바이스를 끈 다음 사용자에게 배포합니다. 디바이스를 켜면 설치 도우미가 시작되고 등록을 시작하기 위해 회사 또는 학교 계정을 입력하라는 메시지가 표시됩니다.
