---
title: Windows Phone 응용 프로그램 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 Windows Phone 장치용 응용 프로그램을 만들고 배포하는 방법입니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 68fe11fa-5fb2-4b81-b0f5-b6f2392fb4ad
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 77eb0b750934641ceb66b2c8aa611544c654f54f
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385442"
---
# <a name="create-windows-phone-applications-in-configuration-manager"></a>Configuration Manager에서 Windows Phone 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 응용 프로그램에는 하나 이상의 배포 유형이 있습니다. 배포 유형에는 소프트웨어를 장치에 배포하는 데 필요한 설치 파일 및 정보가 포함됩니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 단계는 [응용 프로그램 만들기](/sccm/apps/deploy-use/create-applications#bkmk_create)를 참조하세요. 

Windows Phone 장치용 응용 프로그램을 만들고 배포할 때 고려해야 하는 사항은 다음과 같습니다.  


Configuration Manager는 다음과 같은 앱 파일 형식의 배포를 지원합니다.  

|장치 유형|지원되는 파일 형식|  
|-----------------|---------------------|  
|Windows Phone 8|xap|  
|Windows Phone 8.1|xap, appx, appxbundle|
|Windows 10 Mobile|xap, appx, appxbundle|

Windows Phone 응용 프로그램은 **사용 가능** 또는 **필수**로 배포되며, 응용 프로그램을 제거하는 데에도 이 배포를 사용합니다.  
