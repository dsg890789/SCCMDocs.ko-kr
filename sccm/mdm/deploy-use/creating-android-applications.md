---
title: "Android 응용 프로그램 만들기 | Microsoft 문서"
description: "Android 장치용 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다."
ms.custom: na
ms.date: 03/05/2017
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
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 3d90b2cb1e255b9e8827a991779024ccecde9646
ms.lasthandoff: 03/06/2017

---
# <a name="create-android-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 Android 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 응용 프로그램에는 장치에 소프트웨어를 배포하는 데 필요한 설치 파일과 정보로 구성된 배포 유형이 하나 이상 포함되어 있습니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

 다음 방법을 사용하여 응용 프로그램을 만들 수 있습니다.  

-   응용 프로그램 설치 파일을 읽어 자동으로 응용 프로그램 및 배포 유형을 만듭니다.  

-   수동으로 응용 프로그램을 만든 다음 나중에 배포 유형을 추가합니다.  

-   파일에서 응용 프로그램을 가져옵니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 데 필요한 단계는 [응용 프로그램 만들기 마법사 시작](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard)을 참조하세요. 또한 Android 장치용 응용 프로그램을 만들고 배포할 때는 다음 사항을 고려하세요.  

## <a name="general-considerations"></a>일반적인 고려 사항

Configuration Manager는 다음과 같은 Android용 앱 유형의 배포를 지원합니다.

|장치 유형|지원되는 파일|
|-|-|
|Android|.apk|

다음 배포 작업이 지원됩니다.

|장치 유형|지원되는 작업|
|-|-|
|Android|**사용 가능**, **필수**. 사용자가 설치 및 제거에 모두 동의해야 합니다.

