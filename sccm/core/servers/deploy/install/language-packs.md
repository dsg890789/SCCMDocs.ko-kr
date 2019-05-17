---
title: 언어 팩
titleSuffix: Configuration Manager
description: Configuration Manager에서 제공되는 언어 지원에 대해 알아봅니다.
ms.date: 06/29/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: cd74e5f5-33f6-4566-8c9d-d6a93bfe71ed
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 238165dfe6822e05e64b725546837b3b4f0c496b
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65498024"
---
# <a name="language-packs-in-configuration-manager"></a>Configuration Manager의 언어 팩

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager의 언어 지원에 대한 기술적인 세부 정보를 제공합니다. Configuration Manager 사이트 서버 및 클라이언트는 언어 중립적인 것으로 간주됩니다. 중앙 관리 사이트와 기본 사이트에 **서버 언어 팩** 또는 **클라이언트 언어 팩**을 설치하여 표시 언어에 대한 지원을 추가합니다. 사이트를 설치하는 동안 사이트에서 지원할 서버 및 클라이언트 언어를 사용 가능한 언어 팩 파일에서 선택합니다.
 
각 사이트에 여러 언어를 설치합니다. 사용하는 언어만 설치해야 합니다.  

- 각 사이트는 Configuration Manager 콘솔에 여러 언어를 지원합니다.  

- 각 사이트에서 개별 클라이언트 언어 팩을 설치하여 지원하려는 클라이언트 언어에 대해서만 지원을 추가합니다.  

다음 구성 요소와 일치하는 언어에 대한 지원을 설치하는 경우:  

- 컴퓨터의 표시 언어: 해당 컴퓨터에서 실행되는 Configuration Manager 콘솔과 클라이언트 사용자 인터페이스 모두 해당 언어로 정보를 표시합니다.  

- 컴퓨터의 웹 브라우저에서 사용 중인 언어 기본 설정: 애플리케이션 카탈로그 또는 SQL Server Reporting Services를 포함하여 웹 기반 정보에 대한 연결이 해당 언어로 표시됩니다.  


Configuration Manager 설치 프로그램을 실행하면 필수 구성 요소 및 재배포 가능 파일의 일부로 언어 팩 파일이 다운로드됩니다. [설치 다운로더](setup-downloader.md)를 사용하여 설치 프로그램을 실행하기 전에 이러한 파일을 다운로드할 수도 있습니다.   



## <a name="server-languages"></a>서버 언어  

서버에서 지원하려는 언어에 대한 로캘 ID를 파악하려면 다음 표를 참조하세요. 로캘 ID에 대한 자세한 내용은 [Locale IDs Assigned by Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=252609)를 참조하세요.  

|서버 언어|로캘 ID(LCID)|세 자리 코드|  
|---------------------|------------------------|-----------------------|  
|영어(기본값)|0409|ENU|  
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



## <a name="client-languages"></a>클라이언트 언어  

클라이언트 컴퓨터에서 지원하려는 언어에 대한 로캘 ID를 파악하려면 다음 표를 참조하세요. 로캘 ID에 대한 자세한 내용은 [Locale IDs Assigned by Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=252609)를 참조하세요.  

|클라이언트 언어|로캘 ID(LCID)|세 자리 코드|  
|---------------------|------------------------|-----------------------|  
|영어(기본값)|0409|ENG|  
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


### <a name="mobile-device-client-languages"></a>모바일 디바이스 클라이언트 언어  
모바일 디바이스 언어에 대한 지원을 추가하면 모든 지원되는 모바일 디바이스 클라이언트 언어가 포함됩니다. 모바일 디바이스 지원을 위한 개별 언어 팩을 선택할 수 없습니다.  



## <a name="identify-installed-language-packs"></a>설치된 언어 팩 확인  
Configuration Manager 클라이언트를 실행하는 컴퓨터에 설치된 언어 팩을 확인하려면 해당 컴퓨터의 레지스트리에서 설치된 언어 팩의 LCID(로캘 ID)를 찾습니다. 이 정보는 다음 레지스트리 경로에서 사용할 수 있습니다.  

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs`  

하드웨어 인벤토리를 사용자 지정하여 이 정보를 수집합니다. 그런 다음, 사용자 지정 보고서를 작성하여 언어 세부 정보를 확인합니다. 사용자 지정 하드웨어 인벤토리 수집에 대한 자세한 내용은 [하드웨어 인벤토리를 구성하는 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요. 보고서 만들기에 대한 자세한 내용은 [Configuration Manager 보고서 관리](/sccm/core/servers/manage/operations-and-maintenance-for-reporting#BKMK_ManageReports)를 참조하세요.  
