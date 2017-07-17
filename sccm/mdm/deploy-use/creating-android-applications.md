---
title: "Android 응용 프로그램 만들기 | Microsoft 문서"
description: "Android 장치용 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: HT
ms.sourcegitcommit: 344b55aecd72479b759b40e8252e64a06c5eaba0
ms.openlocfilehash: 3bfb7364c3de5264a5fa8a684965d9aebeb84719
ms.contentlocale: ko-kr
ms.lasthandoff: 07/13/2017

---
# System Center Configuration Manager에서 Android 응용 프로그램 만들기
<a id="create-android-applications-with-system-center-configuration-manager" class="xliff"></a>

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 응용 프로그램에는 장치에 소프트웨어를 배포하는 데 필요한 설치 파일과 정보로 구성된 배포 유형이 하나 이상 포함되어 있습니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

 다음 방법을 사용하여 응용 프로그램을 만들 수 있습니다.  

-   응용 프로그램 설치 파일을 읽어 자동으로 응용 프로그램 및 배포 유형을 만듭니다.  
-   수동으로 응용 프로그램을 만든 다음 나중에 배포 유형을 추가합니다.  
-   파일에서 응용 프로그램을 가져옵니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 데 필요한 단계는 [응용 프로그램 만들기 마법사 시작](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard)을 참조하세요. 또한 Android 장치용 응용 프로그램을 만들고 배포할 때는 다음 사항을 고려하세요.  

## Android 앱에 대한 일반적인 고려 사항
<a id="general-considerations-for-android-apps" class="xliff"></a>

Configuration Manager는 다음과 같은 Android용 앱 유형의 배포를 지원합니다.

|장치 유형|지원되는 파일|
|-|-|
|Android|.apk|

다음 배포 작업이 지원됩니다.

|장치 유형|지원되는 작업|
|-|-|
|Android|**사용 가능**, **필수** 사용자가 설치 및 제거에 모두 동의해야 합니다.|
|Android for Work | **필수** |

## Android for Work 앱 승인 및 배포
<a id="approve-and-deploy-android-for-work-apps" class="xliff"></a>
Configuration Manager 관리자는 [Play for Work 웹 사이트](https://play.google.com/work)에서 앱을 승인 및 배포하고 해당 앱을 관리되는 Android for Work 장치에 배포할 수도 있습니다.

Play for Work 스토어에서 앱을 승인하고, Configuration Manager 콘솔과 동기화하고, 관리되는 Android for Work 장치에 배포하려면 다음 단계를 따르세요. 사용자의 작업 프로필에 앱을 배포하려면 Play for Work에서 앱을 승인한 다음 Configuration Manager 콘솔과 동기화해야 합니다.

1. 브라우저를 열고 https://play.google.com/work로 이동합니다.
2. Intune 테넌트에 제한된 Google 관리자 계정을 사용하여 로그인합니다.
3. 환경에 배포하려는 앱을 찾은 다음 각 앱에 대해 **승인**을 선택하여 Android for Work에서 앱을 사용 가능하도록 설정합니다.
4. Configuration Manager 콘솔에서 **관리자** > **개요** > **Cloud Services** > **Android for Work**로 이동한 다음 **동기화**를 선택합니다.
5. 앱이 동기화될 때까지 최대 10분 정도 기다린 다음 **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **스토어 앱에 대한 라이선스 정보**로 이동합니다.
6. Play for Work에서 동기화된 앱을 선택한 다음 **응용 프로그램 만들기**를 선택합니다.
7. 마법사를 완료하고 **닫기**를 선택합니다.
8. **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **응용 프로그램**으로 이동한 다음 Android for Work 앱을 선택하여 평소대로 배포합니다.

Play for Work 앱을 Configuration Manager와 동기화하려면 먼저 Play for Work 웹 사이트에서 앱을 하나 이상 승인해야 합니다.

