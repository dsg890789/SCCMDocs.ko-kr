---
title: Mac 클라이언트 유지 관리
titleSuffix: Configuration Manager
description: Configuration Manager Mac 클라이언트에 대한 유지 관리 작업
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: cf6337a2-700c-47f3-b6f8-5814f9b81e59
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 32d36f041ed42ef0afa8fe0c0e052389587a2c8f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32335221"
---
# <a name="maintain-mac-clients"></a>Mac 클라이언트 유지 관리
*적용 대상: System Center Configuration Manager(현재 분기)*

Mac 클라이언트 제거하고 해당 인증서를 갱신하는 절차는 다음과 같습니다.

##  <a name="uninstalling-the-mac-client"></a>Mac 클라이언트 제거  

1.  Mac 컴퓨터에서 터미널 창을 열고 **macclient.dmg**가 포함된 폴더로 이동합니다.  

2.  Tools 폴더로 이동하여 다음 명령줄을 입력합니다.  

     **./CMUninstall -c**  

    > [!NOTE]  
    >  **–c** 속성을 지정하면 클라이언트 제거 시 클라이언트 충돌 로그 및 로그 파일도 제거됩니다. 클라이언트를 나중에 다시 설치하는 경우 혼동을 방지하려면 이 속성을 지정하는 것이 좋습니다.  

3.  필요한 경우 Configuration Manager에 사용되던 클라이언트 인증 인증서를 수동으로 제거하거나 해지합니다. CMUnistall은 이 인증서를 제거하거나 해지하지 않습니다.  

##  <a name="renewing-the-mac-client-certificate"></a>Mac 클라이언트 인증서 갱신  
 다음 방법 중 하나를 사용하여 Mac 클라이언트 인증서를 갱신할 수 있습니다.  

-   [인증서 갱신 마법사](#renew-certificate-wizard)  

-   [수동으로 인증서 갱신](#renew-certificate-manually)  

###  <a name="renew-certificate-wizard"></a>인증서 갱신 마법사  

1.  ccmclient.plist 파일에서 인증서 갱신 마법사가 열리는 시기를 제어하는 값을 다음과 같이 *문자열*로 구성합니다.  

 -   **RenewalPeriod1** – 사용자가 인증서를 갱신할 수 있는 첫 번째 갱신 기간(초)을 지정합니다. 기본값은 3,888,000초(45일)입니다. 300 미만의 값은 구성하지 마세요. 그럴 경우 기간이 기본값으로 되돌아갑니다. 

 -   **RenewalPeriod2** – 사용자가 인증서를 갱신할 수 있는 두 번째 갱신 기간(초)을 지정합니다. 기본값은 259,200초(3일)입니다. 이 값이 구성되었으며 300초 이상이면서 **RenewalPeriod1** 이하인 경우 해당 값이 사용됩니다. **RenewalPeriod1** 가 3일보다 크면 **RenewalPeriod2**에 대해 값으로 3일이 사용됩니다.  **RenewalPeriod1** 3일보다 작은 경우에는 **RenewalPeriod2** 가 **RenewalPeriod1**과 같은 값으로 설정됩니다.  

 -   **RenewalReminderInterval1** – 첫 번째 갱신 기간 중 인증서 갱신 마법사가 사용자에게 표시하는 빈도(초)를 지정합니다. 기본값은 86,400초(1일)입니다. **RenewalReminderInterval1** 이 300초보다 크고 **RenewalPeriod1**에 대해 구성된 값보다 작은 경우 구성된 값이 사용됩니다. 그렇지 않은 경우 1일의 기본값이 사용됩니다.  

 -   **RenewalReminderInterval2** – 두 번째 갱신 기간 중 인증서 갱신 마법사가 사용자에게 표시하는 빈도(초)를 지정합니다. 기본값은 28,800초(8시간)입니다. **RenewalReminderInterval2** 가 300초보다 크고 **RenewalReminderInterval1** 및 **RenewalPeriod2**이하인 경우에는 구성된 값이 사용됩니다. 그렇지 않은 경우에는 값으로 8시간이 사용됩니다.  

     **예제:** 값을 기본값으로 유지하는 경우 인증서 만료 45일 전에 마법사가 24시간마다 열립니다.  인증서 만료 3일 전부터는 마법사가 8시간마다 열립니다.  

     **예제:** 다음 명령줄 또는 스크립트를 사용하여 첫 번째 갱신 기간을 20일로 설정할 수 있습니다.  

     `sudo defaults write com.microsoft.ccmclient RenewalPeriod1 1728000`  

2.  인증서 갱신 마법사가 열릴 때 **사용자 이름** 및 **서버 이름** 필드가 일반적으로 미리 채워지며 사용자는 암호만 입력하여 인증서를 갱신할 수 있습니다.  

    > [!NOTE]  
    >  마법사가 열리지 않거나 마법사를 실수로 닫은 경우 **Configuration Manager** 기본 설정 페이지에서 **갱신** 을 클릭하여 마법사를 엽니다.  

###  <a name="renew-certificate-manually"></a>수동으로 인증서 갱신  
 Mac 클라이언트 인증서의 일반적인 유효 기간은 1년입니다. Configuration Manager에서는 등록 중에 요청하는 사용자 인증서를 자동으로 갱신하지 않으므로 다음 절차에 따라 인증서를 수동으로 갱신해야 합니다.  

> [!IMPORTANT]  
>  인증서가 만료된 경우 인증서를 제거하고 다시 설치한 후 Mac 클라이언트를 다시 등록해야 합니다.  

 이 절차는 동일한 Mac 컴퓨터에 대한 새 인증서를 요청하는 데 필요한 SMSID를 제거합니다. SMSID를 제거하고 대체할 경우 Configuration Manager 콘솔에서 클라이언트를 삭제한 후에 인벤토리와 같은 저장된 클라이언트 기록이 삭제됩니다.  

1.  사용자 인증서를 갱신해야 하는 Mac 컴퓨터에 대한 장치 컬렉션을 만들고 채웁니다.  

    > [!WARNING]  
    >  Configuration Manager에서는 Mac 컴퓨터에 등록되는 인증서의 유효 기간을 모니터링하지 않습니다. 이 컬렉션을 추가할 Mac 컴퓨터를 식별하려면 Configuration Manager에서 별도로 이를 모니터링해야 합니다.  

2.  **자산 및 호환성** 작업 영역에서 **구성 항목 만들기 마법사**를 시작합니다.  

3.  **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **유형:Mac OS X**  

4.  **지원되는 플랫폼** 페이지에서 모든 Mac OS X 버전이 선택되어 있는지 확인합니다.  

5.  **설정** 페이지에서 **새로 만들기**를 선택하고 **설정 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **설정 유형:스크립트**  

    -   **데이터 형식:문자열**  

6.  **설정 만들기** 대화 상자의 **검색 스크립트**에 대해 **스크립트 추가**를 선택하여 SMSID가 구성된 Mac 컴퓨터를 검색하는 스크립트를 지정합니다.  

7.  **검색 스크립트 편집** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  **확인**을 선택하여 **검색 스크립트 편집** 대화 상자를 닫습니다.  

9. **설정 만들기** 대화 상자의 **재구성 스크립트(옵션)** 에 대해 **스크립트 추가**를 선택하여 Mac 컴퓨터에서 발견된 SMSID를 제거하는 스크립트를 지정합니다.  

10. **재구성 스크립트 만들기** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. **확인**을 선택하여 **재구성 스크립트 만들기** 대화 상자를 닫습니다.  

12. 마법사의 **호환성 규칙** 페이지에서 **새로 만들기**를 클릭하고 **규칙 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **선택한 설정:** **찾아보기**를 선택하고 이전에 지정한 검색 스크립트를 선택합니다.  

    -   **다음 값** 필드에 **(com.microsoft.ccmclient, SMSID)의 도메인/기본값 쌍이 존재하지 않음**를 입력합니다.  

    -   **이 설정이 규칙과 호환되지 않는 경우 지정한 재구성 스크립트 실행**옵션을 사용하도록 설정합니다.  

13. 구성 항목 만들기 마법사를 완료합니다.  

14. 방금 만든 구성 항목을 포함하는 구성 기준을 만들고 이를 1단계에서 만든 장치 컬렉션에 배포합니다.  

     구성 기준을 만들고 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 구성 기준을 만드는 방법](../../../compliance/deploy-use/create-configuration-baselines.md) 및 [System Center Configuration Manager에서 구성 기준을 배포하는 방법](../../../compliance/deploy-use/deploy-configuration-baselines.md)을 참조하세요.  

15. SMSID가 제거된 Mac 컴퓨터에서 다음 명령을 실행하여 새 인증서를 설치합니다.  

    ```  
    sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u <'user name'>  
    ```  

     메시지가 나타나면 명령을 실행할 슈퍼 사용자 계정의 암호를 지정한 후 Active Directory 사용자 계정의 암호를 지정합니다.  

16. 등록된 인증서를 Configuration Manager로 제한하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    a.  **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**명령을 입력합니다.  

    b.  **Keychain Access**(키 집합 접근) 대화 상자의 **Keychains**(키 집합) 섹션에서 **System**(시스템)을 선택한 다음 **Category**(범주) 섹션에서 **Keys**(키)를 선택합니다.  

    c.  클라이언트 인증서를 보려면 해당 키를 확장합니다. 방금 설치한 인증서를 개인 키로 식별한 경우 키를 두 번 클릭합니다.  

    d.  **Access Control**(액세스 제어) 탭에서 **접근 허용 전 확인**을 선택합니다.  

    e.  **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 선택합니다.  

    f.  **변경사항 저장**을 선택하고 **키 집합 접근** 대화 상자를 닫습니다.  

17. Mac 컴퓨터를 다시 시작합니다.  

