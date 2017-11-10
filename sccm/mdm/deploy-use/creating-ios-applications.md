---
title: "iOS 응용 프로그램 만들기"
titleSuffix: Configuration Manager
description: "iOS 장치용 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ff633013-5313-4cd3-949c-56d45e777280
caps.latest.revision: "10"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 2b21a50b18384740eda8744c3442fe060325fd15
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="create-ios-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 iOS 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 응용 프로그램에는 장치에 소프트웨어를 배포하는 데 필요한 설치 파일과 정보로 구성된 배포 유형이 하나 이상 포함되어 있습니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

 다음 방법을 사용하여 응용 프로그램을 만들 수 있습니다.  

-   응용 프로그램 설치 파일을 읽어 자동으로 응용 프로그램 및 배포 유형을 만듭니다.  

-   수동으로 응용 프로그램을 만든 다음 나중에 배포 유형을 추가합니다.  

-   파일에서 응용 프로그램을 가져옵니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 데 필요한 단계는 [응용 프로그램 만들기 마법사 시작](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard)을 참조하세요. 또한 iOS 장치용 응용 프로그램을 만들고 배포할 때는 다음 사항을 고려하세요.  

## <a name="general-considerations"></a>일반적인 고려 사항  
 Configuration Manager는 다음과 같은 앱 유형의 배포를 지원합니다.  

|장치 유형|지원되는 파일|  
|-----------------|---------------------|  
|iOS|*.ipa<br /><br /> System Center Configuration Manager에서는 iOS 앱을 가져올 때 속성 목록(.plist) 파일을 지정할 필요가 없습니다.|  

 다음 배포 작업이 지원됩니다.  

|장치 유형|지원되는 작업|  
|-----------------|-----------------------|  
|iOS|**사용 가능**, **필수**. 사용자가 설치 및 제거에 모두 동의해야 합니다.

> [!IMPORTANT]  
>  현재 최종 사용자는 iOS용 Microsoft Intune 회사 포털 앱에서 회사 앱을 설치할 수 없습니다. 이는 iOS 앱 스토어에 게시된 앱에 적용되는 제약 조건이 있기 때문입니다(앱 스토어 검토 지침, 섹션 2 참조). 사용자는 자신의 장치에서 Intune 웹 포털(portal.manage.microsoft.com)로 이동하여, 관리되는 앱 스토어 앱과 기간 업무 앱 패키지를 비롯한 회사 앱을 설치할 수 있습니다. Intune 회사 포털 앱을 사용하여 설정할 수 있는 모바일 관리 기능에 대한 자세한 내용은 [Microsoft Intune의 등록된 장치 관리 기능](https://technet.microsoft.com/library/dn600287.aspx)을 참조하세요.  
