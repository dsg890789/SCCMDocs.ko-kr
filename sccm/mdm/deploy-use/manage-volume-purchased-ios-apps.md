---
title: "대량 구매한 iOS 앱 관리 | Microsoft 문서"
description: "iOS App Store를 통해 구입한 앱의 라이선스를 배포, 관리 및 추적합니다."
ms.custom: na
ms.date: 05/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c3b9316-247b-490b-a363-8f8553821579
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: ce706e938f558406044f7890c80bb7156c3b262b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="manage-volume-purchased-ios-apps-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 대량 구매한 iOS 앱 관리

*적용 대상: System Center Configuration Manager(현재 분기)*



 iOS App Store를 통해 회사에서 실행하려는 앱의 라이선스를 여러 개 구입할 수 있습니다. 이 기능을 사용하면 구입한 앱의 여러 복사본을 추적하는 관리 오버헤드를 줄일 수 있습니다.  

 System Center Configuration Manager는 App Store에서 라이선스 정보를 가져오고 사용 중인 라이선스 수를 추적하여 프로그램을 통해 구매한 iOS 앱의 배포 및 관리를 지원합니다.  

## <a name="manage-volume-purchased-apps-for-ios-devices"></a>iOS 장치용 대량 구매 앱 관리  
 Apple VPP(대량 구매 프로그램)를 통해 iOS 앱의 라이선스를 여러 개 구입합니다. 이 경우 Apple 웹 사이트에서 Apple VPP 계정을 설정하고 다음 기능을 제공하는 Apple VPP 토큰을 Configuration Manager에 업로드해야 합니다.  

-   대량 구매 정보를 Configuration Manager와 동기화합니다. 
 
- 비즈니스용 Apple Volume Purchase Program 및 교육용 Apple Volume Purchase Program의 앱을 둘 다 동기화합니다.

- 여러 Apple Volume Purchase Program 토큰을 Configuration Manager와 연결합니다.

-   구입한 앱은 Configuration Manager 콘솔에 표시됩니다.  

-   앱을 배포 및 모니터링하고 사용된 각 앱의 라이선스 수를 추적할 수도 있습니다.  

-   필요한 경우 Configuration Manager를 통해 배포한 대량 구매 앱을 제거하여 라이선스를 회수할 수 있습니다.  

## <a name="before-you-start"></a>시작하기 전에  
 시작하기 전에 Apple에서 VPP 토큰 하나를 가져와 Configuration Manager에 업로드해야 합니다.  

-   기존 Apple VPP 계정에서 이전에 VPP 토큰을 다른 MDM 제품에 사용한 경우 Configuration Manager에 사용할 토큰을 새로 생성해야 합니다.  
-   각 토큰은 1년 동안 유효합니다.  
-   기본적으로 Configuration Manager는 하루에 두 번 Apple VPP 서비스와 동기화하여 라이선스가 Configuration Manager와 동기화되도록 합니다.  
      라이선스 변경 내용만 동기화됩니다. 그러나 7일마다 한 번 전체 동기화가 수행됩니다.  
      **동기화**를 선택하여 수동 동기화를 수행하는 경우 항상 전체 동기화가 수행됩니다.  
-   Configuration Manager 데이터베이스를 복구하거나 복원해야 하는 경우 나중에 수동 동기화를 수행하여 동기화된 라이선스 데이터를 최신 상태로 유지하는 것이 좋습니다.  
-   또한 앱 배포를 비롯한 iOS 장치를 관리할 수 있도록 Apple에서 유효한 APNs(Apple Push Notification Service) 인증서를 가져온 상태여야 합니다. 자세한 내용은 [iOS 하이브리드 장치 관리 설정](enroll-hybrid-ios-mac.md)을 참조하세요.  
-   Configuration Manager는 최대 3000개의 VPP 토큰을 추가하도록 지원합니다.

System Center Configuration Manager 1702부터 이제 사용이 허가된 앱을 사용자 및 장치에 배포할 수 있습니다. 장치 라이선싱을 지원하는 앱 기능에 따라 앱 배포 시 다음과 같이 적절한 라이선스가 청구됩니다.

|||||
|-|-|-|-|
|Configuration Manager 버전|앱이 장치 라이선싱을 지원하나요?|배포 컬렉션 유형|청구된 라이선스|
|1702 이전|예|사용자|사용자 라이선스|
|1702 이전|아니요|사용자|사용자 라이선스|
|1702 이전|예|장치|사용자 라이선스|
|1702 이전|아니요|장치|사용자 라이선스|
|1702 이상|예|사용자|사용자 라이선스|
|1702 이상|아니요|사용자|사용자 라이선스|
|1702 이상|예|장치|장치 라이선스|
|1702 이상|아니요|장치|사용자 라이선스|

## <a name="step-1---to-get-and-upload-an-apple-vpp-token"></a>1단계 - Apple VPP 토큰을 가져와 업로드하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라우드 서비스** > **Apple Volume Purchase Program 토큰**을 선택합니다.   

3.  **홈** 탭의 **Apple Volume Purchase Program 토큰** 그룹에서 **Apple Volume Purchase Program 토큰 추가**를 선택합니다.  

4.  **Apple Volume Purchase Program 토큰 추가** 마법사의 **일반** 페이지에서 다음을 구성합니다.   

    -   **이름** - Configuration Manager 콘솔에 표시되는 이 토큰의 이름을 입력합니다.  

    -   **토큰** - **찾아보기**를 선택한 다음 Apple 웹 사이트에서 다운로드한 VPP 토큰을 선택합니다.  

         **Apple VPP 계정 보기** 링크를 선택하고 비즈니스 또는 교육용 대량 구매 프로그램에 등록합니다(아직 수행하지 않은 경우). 등록한 후 계정에 대한 Apple VPP 토큰을 다운로드합니다.  

    -   **설명** - 필요에 따라 Configuration Manager 콘솔에서 이 VPP 토큰을 식별하는 데 도움이 되는 설명을 입력합니다.  

    -   **검색 및 필터링을 개선하기 위해 할당된 범주** - 필요에 따라 Configuration Manager 콘솔에서 검색하기 쉽도록 VPP 토큰에 범주를 할당할 수 있습니다.  
    -   **Apple ID** - VPP 토큰과 연결된 Apple 메일 ID를 입력합니다.
    -   **토큰 유형** - 사용할 VPP 토큰 유형을 선택합니다. **비즈니스** 및 **EDU** 토큰 유형을 선택할 수 있습니다.

5.  **다음**을 선택한 다음 마법사를 완료합니다.  

이제 **Apple Volume Purchase Program 토큰** 노드에서 마지막으로 업데이트된 시간, 예상 만료 시간 및 마지막으로 동기화된 시간을 포함하여 Apple VPP 토큰에 대한 정보를 볼 수 있습니다.

언제든지 **홈** 탭의 **동기화** 그룹에서 **동기화**를 선택하여 Apple에서 보유한 데이터를 Configuration Manager와 전체 동기화할 수 있습니다.  

## <a name="step-2---deploy-a-volume-purchased-app"></a>2단계 - 대량 구매 앱 배포  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **스토어 앱에 대한 라이선스 정보**를 선택합니다.  

3.  배포하려는 앱을 선택한 후 **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 선택합니다.
비즈니스용 Windows 스토어 앱을 포함하여 Configuration Manager 응용 프로그램이 만들어집니다. 그런 다음 이 응용 프로그램을 원하는 Configuration Manager 응용 프로그램으로 배포 및 모니터링할 수 있습니다.

    > [!IMPORTANT]  
    > 배포 목적으로 **필수**를 선택해야 합니다. 사용 가능한 설치는 현재 지원되지 않습니다.

 앱을 배포하면 각 사용자가 라이선스 하나를 사용하고 장치 설치의 경우 앱을 설치하는 장치가 라이선스 하나를 사용합니다.  장치 라이선싱을 지원하는 앱을 통해 장치 컬렉션을 대상으로 지정하면 장치 라이선스가 청구됩니다.  장치 라이선싱을 지원하지 않는 앱을 통해 장치 컬렉션을 대상으로 지정하면 사용자 라이선스가 청구됩니다. 

 **스토어 앱에 대한 라이선스 정보** 노드에서 앱을 만들면 앱은 선택한 앱에 대한 토큰의 라이선스와 연결됩니다.  예를 들어 노드에 같은 앱의 두 가지 버전이 표시될 수 있습니다. 이는 앱의 각 버전이 서로 다른 Apple VPP 토큰과 연결되기 때문입니다.  이후 각 토큰에서 앱을 만들고 개별적으로 배포할 수 있습니다.

 라이선스를 회수하려면 배포 작업을 **제거**로 해서 앱의 새 배포를 만들어야 합니다. 원래 배포의 배포 작업은 변경할 수 없습니다. 앱을 제거하면 라이선스가 회수됩니다.  

## <a name="step-3---monitor-ios-vpp-apps"></a>3단계 - iOS VPP 앱 모니터링  
 **소프트웨어 라이브러리** 작업 영역의 **스토어 앱에 대한 라이선스 정보** 노드에는 대량 구매한 iOS 앱에 대한 정보가 표시됩니다. 이 정보에는 각 앱에 대해 소유한 총 라이선스 수, 배포된 개수 등이 포함됩니다. 또한 보기에는 앱이 연결된 VPP 토큰 및 토큰 유형이 표시됩니다.

 **라이선스 수가 포함된 iOS용 Apple Volume Purchase Program 앱** 보고서를 사용하여 구입한 모든 VPP 앱의 라이선스 사용을 모니터링할 수도 있습니다.  

 이 보고서에는 각 응용 프로그램의 이름, 구입한 라이선스의 총수, 사용 가능한 라이선스 수 등이 표시됩니다.  

 Configuration Manager 보고서를 실행하는 방법에 대한 도움말은 [System Center Configuration Manager에서 보고](../../core/servers/manage/reporting.md)를 참조하세요.  
