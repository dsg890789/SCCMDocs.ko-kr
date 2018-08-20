---
title: iOS 응용 프로그램 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 iOS 장치용 응용 프로그램을 만들고 배포하는 방법입니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 246ca26b8fab3a1006e8d72b803c298fe48df9df
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385238"
---
# <a name="create-ios-applications-in-configuration-manager"></a>Configuration Manager에서 iOS 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 응용 프로그램에는 장치에 소프트웨어를 배포하는 데 필요한 설치 파일과 정보로 구성된 배포 유형이 하나 이상 포함되어 있습니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 데 필요한 단계는 [응용 프로그램 만들기](/sccm/apps/deploy-use/create-applications#bkmk_create)를 참조하세요. 

iOS 장치용 응용 프로그램을 만들고 배포할 때는 다음 사항을 고려하세요.  

- Configuration Manager는 iOS .ipa 패키지 배포를 지원합니다. iOS 앱을 가져올 때 속성 목록(.plist) 파일을 지정할 필요가 없습니다. 

- iOS 응용 프로그램을 **사용 가능** 또는 **필수**로 배포합니다. 사용자가 설치 및 제거에 모두 동의해야 합니다.

> [!IMPORTANT]  
>  현재 최종 사용자는 iOS용 Microsoft Intune 회사 포털 앱에서 회사 앱을 설치할 수 없습니다. 이 제한은 iOS App Store에 게시된 앱에 대한 제한이 있기 때문입니다. (App Store 검토 지침, 섹션 2 참조) 사용자는 자신의 장치에서 Intune 포털로 이동하여 회사 앱을 설치할 수 있습니다. 이러한 앱에는 관리되는 App Store 앱 및 기간 업무 앱 패키지가 포함됩니다. Intune 회사 포털 앱이 활성화하는 모바일 관리 기능에 대한 자세한 내용은 [Microsoft Intune의 등록된 장치 관리 기능](https://docs.microsoft.com/intune/device-enrollment)을 참조하세요.  
