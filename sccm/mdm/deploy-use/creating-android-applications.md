---
title: Android 애플리케이션 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 Android 디바이스용 응용 프로그램을 만들고 배포하는 방법입니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: e025c48c-1514-4ab7-836c-e0635aaa993a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ef070186112642d204aade24039da87c0e3a22f0
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56139673"
---
# <a name="create-android-applications-in-configuration-manager"></a>Configuration Manager에서 Android 애플리케이션 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 애플리케이션에는 하나 이상의 배포 유형이 있습니다. 배포 유형은 디바이스에 소프트웨어를 배포하는 데 필요한 설치 파일 및 정보로 구성됩니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 데 필요한 단계는 [응용 프로그램 만들기](/sccm/apps/deploy-use/create-applications#bkmk_create)를 참조하세요. 

Android 디바이스용 응용 프로그램을 만들고 배포할 때는 다음 사항을 고려하세요.  



## <a name="general-considerations-for-android-apps"></a>Android 앱에 대한 일반적인 고려 사항

Configuration Manager는 Android .apk 패키지를 지원합니다. 

다음 배포 작업이 지원됩니다.

|디바이스 유형|지원되는 작업|
|-|-|
|Android|**사용 가능한**하십시오 **필요한**: 사용자가 설치 및 제거에 모두 동의해야 합니다.|
|Android for Work |**사용 가능**, **필수** |



## <a name="approve-and-deploy-android-for-work-apps"></a>Android for Work 앱 승인 및 배포

또한 Configuration Manager 관리자는 [Play for Work 웹 사이트](https://play.google.com/work)에서 앱을 승인할 수 있습니다. 그런 다음, 관리되는 Android for Work 디바이스에 해당 앱을 배포합니다.

Play for Work 스토어에서 앱을 승인하고, Configuration Manager 콘솔과 동기화하고, 관리되는 Android for Work 디바이스에 배포하려면 다음 단계를 따르세요. 앱을 사용자의 작업 프로필에 배포하려면 Play for Work에서 앱을 승인해야 합니다. 그런 다음, Configuration Manager 콘솔을 사용하여 앱을 동기화합니다.

1. 브라우저를 열고 https://play.google.com/work로 이동합니다.  

2. Microsoft Intune 테넌트에 제한된 Google 관리자 계정을 사용하여 로그인합니다.  

3. 환경에 배포하려는 앱을 찾아봅니다. 앱을 Android for Work에서 사용할 수 있도록 각 앱에 대해 **승인**을 선택합니다.  

4. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 후, **Android for Work** 노드를 선택합니다.  

5. 리본에서 **동기화**를 클릭합니다.  

6. 앱을 동기화하는 데 최대 10분 동안 기다리십시오. 그런 다음, **소프트웨어 라이브러리** 작업 영역으로 이동하고, **애플리케이션 관리**를 확장한 후, **스토어 앱에 대한 라이선스 정보**를 선택합니다.  

7. Play for Work에서 동기화된 앱을 선택한 다음, **응용 프로그램 만들기**를 클릭합니다.  

8. 마법사를 완료합니다.  

9. **소프트웨어 라이브러리** 작업 영역으로 이동하고 **응용 프로그램 관리**를 확장한 후, **응용 프로그램** 노드를 선택합니다. Android for Work 앱을 선택하고 평소대로 배포합니다.  

Play for Work 앱을 Configuration Manager와 동기화하려면 먼저 Play for Work 웹 사이트에서 앱을 하나 이상 승인합니다.

**사용 가능**으로 배포된 앱은 회사 포털 대신 직장 배지가 달린 Google Play 앱에 표시됩니다. 이렇게 하면 신뢰할 수 있는 원본의 앱을 배포할 수 있습니다. 직장 배지가 달린 Google Play 앱은 신뢰할 수 있는 원본입니다. 신뢰할 수 없는 원본의 앱은 허용할 필요가 없습니다.
