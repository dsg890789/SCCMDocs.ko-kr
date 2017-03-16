---
title: "Windows Phone 응용 프로그램 만들기 | Microsoft 문서"
description: "Windows Phone 장치용 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68fe11fa-5fb2-4b81-b0f5-b6f2392fb4ad
caps.latest.revision: 10
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 6d5d5eb9e4bf0297e2d86bf591dab5b3f42c95fa
ms.lasthandoff: 03/06/2017


---
# <a name="create-windows-phone-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows Phone 응용 프로그램 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 응용 프로그램에는 장치에 소프트웨어를 배포하는 데 필요한 설치 파일과 정보로 구성된 배포 유형이 하나 이상 포함되어 있습니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.  

 다음 방법을 사용하여 응용 프로그램을 만들 수 있습니다.  

-   응용 프로그램 설치 파일을 읽어 자동으로 응용 프로그램 및 배포 유형을 만듭니다.  

-   수동으로 응용 프로그램을 만든 다음 나중에 배포 유형을 추가합니다.  

-   파일에서 응용 프로그램을 가져옵니다.  

Configuration Manager 응용 프로그램 및 배포 유형을 만드는 데 필요한 단계는 [응용 프로그램 만들기 마법사 시작](../../apps/deploy-use/create-applications.md#start-the-create-application-wizard)을 참조하세요. 또한 Windows Phone 장치용 응용 프로그램을 만들고 배포할 때는 다음 사항을 고려하세요.  

## <a name="general-considerations"></a>일반적인 고려 사항  
 Configuration Manager는 다음과 같은 앱 파일 형식의 배포를 지원합니다.  

|장치 유형|지원되는 파일 형식|  
|-----------------|---------------------|  
|Windows Phone 8|*.xap|  
|Windows Phone 8.1|*.xap, *.appx, *.appxbundle|
|Windows 10 Mobile|*.xap, *.appx, *.appxbundle|

 다음 배포 작업이 지원됩니다.  

|장치 유형|지원되는 작업|  
|-----------------|-----------------------|  
|Windows Phone 8, Windows Phone 8.1 및 Windows 10 Mobile|사용 가능, 필수, 제거|  

## <a name="steps-to-deploy-the-latest-windows-phone-company-portal-app-with-supersedence"></a>교체를 통해 최신 Windows Phone 회사 포털 앱을 배포하는 단계  
 다음 표에는 최신 Windows Phone 8 회사 포털 앱을 만들어 배포하기 위한 단계, 세부 정보 및 추가 정보가 나와 있습니다.  

|단계|추가 정보|  
|----------|----------------------|  
|**1단계:** 최신 회사 포털 앱을 가져옵니다.|[Windows Phone 8 회사 포털 앱](http://go.microsoft.com/fwlink/?LinkId=268440)을 다운로드합니다.|  
|**2단계:** Symantec 인증서로 회사 포털 앱에 서명을 합니다.|회사 포털 앱에 서명하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 및 Microsoft Intune에서 Windows Phone 및 Windows 10 Mobile 하이브리드 장치 관리 설정](../../mdm/deploy-use/enroll-hybrid-windows.md)을 참조하세요.|  
|**3단계:** 최신 버전의 회사 포털 앱을 사용하여 새 응용 프로그램을 만들고 교체 관계를 지정합니다.|자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md) 및 [응용 프로그램 수정 및 대체](../../apps/deploy-use/revise-and-supersede-applications.md)를 참조하세요.|  
|**4단계:** Microsoft Intune 구독 마법사에 응용 프로그램을 추가합니다.|자세한 내용은 [System Center Configuration Manager 및 Microsoft Intune에서 Windows Phone 및 Windows 10 Mobile 하이브리드 장치 관리 설정](../../mdm/deploy-use/enroll-hybrid-windows.md)을 참조하세요.|  
|**단계 5:** Microsoft Intune 구독 마법사에 회사 포털 앱을 추가했을 때 자동으로 생성된 배포를 삭제합니다.|Microsoft Intune 구독 마법사에서 이 앱의 자동 배포를 만들었는데 이 배포는 대체를 지원하지 않습니다.|  
|**6단계:** 응용 프로그램의 새 배포를 만듭니다. **소프트웨어 배포 마법사**의 **배포 설정** 페이지에서 **이 응용 프로그램의 대체된 버전을 자동으로 업그레이드**를 선택합니다.|교체 관계로 만든 응용 프로그램을 사용하여 교체가 포함된 새 배포를 만듭니다.|  
|**7단계(선택 사항):** 교체하는 앱은 기본적으로 7일 후에 장치에 설치됩니다. 이전에 등록된 장치에 더 빠르게 회사 포털 앱을 배포하려면 **배포의 재평가 일정** 설정을 더 낮은 값으로 변경합니다.<br /><br /> 이 값을 기본값보다 낮게 설정하면 네트워크 및 클라이언트 컴퓨터의 성능에 부정적인 영향을 미칠 수 있습니다.|추가 정보가 없습니다.|  

