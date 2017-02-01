---
title: "언어 팩 | Microsoft 문서"
description: "System Center Configuration Manager에서 제공되는 언어 지원에 대해 알아봅니다."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: e7075eb675353be130fdcc867d9e4dd1009dab35
ms.openlocfilehash: 47da3c531289ddf13d357bde8bbda85d79ed2803


---
# <a name="language-packs-in-system-center-configuration-manager"></a>System Center Configuration Manager의 언어 팩

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 System Center Configuration Manager의 언어 지원에 대한 기술적인 세부 정보를 제공합니다.  

## <a name="a-namebkmksuplanguagepacksa-supported-operating-system-languages"></a><a name="BKMK_SupLanguagePacks"></a> 지원되는 운영 체제 언어  
 중앙 관리 사이트와 기본 사이트에 **서버 언어 팩** 또는 **클라이언트 언어 팩**을 설치하여 다음 표의 표시 언어에 대한 지원을 설치할 수 있습니다. 사이트를 설치하는 동안 사이트에서 지원할 서버 및 클라이언트 언어를 사용 가능한 언어 팩 파일에서 선택합니다.

 필수 구성 요소 및 재배포 가능 파일 다운로드의 일부로 설치 프로그램을 실행하면 언어 팩 파일이 다운로드됩니다. [설치 다운로더](setup-downloader.md)를 사용하여 설치 프로그램을 실행하기 전에 이러한 파일을 다운로드할 수도 있습니다.   

 서버 또는 클라이언트 컴퓨터에서 지원하기 원하는 언어에 대한 로캘 ID를 파악하려면 다음 표를 참조하세요. 로캘 ID에 대한 자세한 내용은 [Locale IDs Assigned by Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=252609)를 참조하세요.  

### <a name="server-languages"></a>서버 언어  

|서버 언어|로캘 ID(LCID)|세 자리 코드|  
|---------------------|------------------------|-----------------------|  
|영어(기본값)|0409|ENU|  
|중국어(번체, 홍콩 특별 행정구)|0c04|ZHH|  
|중국어(간체)|0804|CHS|  
|중국어(번체, 대만)|0404|CHT|  
|체코어|0405|CSY|  
|네덜란드어 - 네덜란드|0413|NLD|  
|프랑스어|040c|FRA|  
|독일어|0407|DEU|  
|헝가리어|040e|HUN|  
|이탈리아어 - 이탈리아|0410|ITA|  
|일본어|0411|JPN|  
|한국어|0412|KOR|  
|폴란드어|0415|PLK|  
|포르투갈어 - 브라질|0416|PTB|  
|포르투갈어 - 포르투갈|0816|PTG|  
|러시아어|0419|RUS|  
|스페인어 - 스페인|0c0a|ESN|  
|스웨덴어|041d|SVE|  
|터키어|041f|TRK|  

### <a name="client-languages"></a>클라이언트 언어  

|클라이언트 언어|로캘 ID(LCID)|세 자리 코드|  
|---------------------|------------------------|-----------------------|  
|영어(기본값)|0409|ENG|  
|중국어(번체, 홍콩 특별 행정구)|0c04|ZHH|  
|중국어 - 간체|0804|CHS|  
|중국어(번체, 대만)|0404|CHT|  
|체코어|0405|CSY|  
|덴마크어|0406|DAN|  
|네덜란드어 - 네덜란드|0413|NLD|  
|핀란드어|040b|FIN|  
|프랑스어|040c|FRA|  
|독일어|0407|DEU|  
|그리스어|0408|ELL|  
|헝가리어|040e|HUN|  
|이탈리아어 - 이탈리아|0410|ITA|  
|일본어|0411|JPN|  
|한국어|0412|KOR|  
|노르웨이어|0414|NOR|  
|폴란드어|0415|PLK|  
|포르투갈어(브라질)|0416|PTB|  
|포르투갈어(포르투갈)|0816|PTG|  
|러시아어|0419|RUS|  
|스페인어 - 스페인|0c0a|ESN|  
|스웨덴어|041d|SVE|  
|터키어|041f|TRK|  

### <a name="mobile-device-client-languages"></a>모바일 장치 클라이언트 언어  
 모바일 장치 언어에 대한 지원을 추가하면 모든 지원되는 모바일 장치 클라이언트 언어가 포함됩니다. 모바일 장치 지원을 위한 개별 언어 팩을 선택할 수 없습니다.  

### <a name="identify-installed-language-packs"></a>설치된 언어 팩 확인  
Configuration Manager 클라이언트를 실행하는 컴퓨터에 설치된 언어 팩을 확인하려면 해당 컴퓨터의 레지스트리에서 설치된 언어 팩의 LCID(로캘 ID)를 찾습니다. 이 정보는 다음 위치에서 확인할 수 있습니다.

 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs**  

하드웨어 인벤토리를 사용하여 이 정보를 수집한 후에 사용자 지정 보고서를 작성하여 언어 세부 정보를 확인할 수 있습니다. 사용자 지정 하드웨어 인벤토리를 수집하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 구성하는 방법](../../../../core/clients/manage/inventory/configure-hardware-inventory.md)을 참조하세요. 보고서를 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 작업 및 유지 관리](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md) 항목에서 [Configuration Manager 보고서 관리](../../../../core/servers/manage/operations-and-maintenance-for-reporting.md#BKMK_ManageReports) 섹션을 참조하세요.  



<!--HONumber=Jan17_HO1-->


