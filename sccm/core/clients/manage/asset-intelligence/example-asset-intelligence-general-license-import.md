---
title: Asset Intelligence 일반 라이선스 가져오기 파일 예제
titleSuffix: Configuration Manager
description: 샘플 Asset Intelligence 일반 라이선스 파일을 사용하여 System Center Configuration Manager의 소프트웨어 라이선스를 가져올 수 있도록 합니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e6258333-a783-440b-b1af-f8023b782fbc
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0ab8e241f9a1bacba7f8bcfbe0674fbfb513db2e
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65500023"
---
# <a name="example-asset-intelligence-general-license-import-file-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Asset Intelligence 일반 라이선스 가져오기 파일 예제

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 예제 정보는 샘플 일반 소프트웨어 라이선스 파일을 만들어 소프트웨어 라이선스 가져오기 마법사를 사용하여 소프트웨어 라이선스를 Asset Intelligence 카탈로그로 가져오는 데 사용할 수 있습니다. 테스트 목적으로 일반 소프트웨어 라이선스 가져오기 파일 예제로 사용하기 위해 다음 표를 복사하고 새 Microsoft Excel 스프레드시트에 붙여넣은 다음 .csv 파일 이름 확장명으로 저장할 수 있습니다. 라이선스 가져오기 파일을 만들 때 모든 헤더 필드가 필요하지만 스프레드시트에서는 Name, Publisher, Version 및 EffectiveQuantity 데이터 값만 필요합니다. Asset Intelligence 카탈로그에 소프트웨어 라이선스 가져오기에 대한 자세한 내용은 [System Center Configuration Manager에서 Asset Intelligence 구성](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md)을 참조하세요.  

|Name|게시자|Version|언어|EffectiveQuantity|PONumber|ResellerName|DateOfPurchase|SupportPurchased|SupportExpirationDate|설명|  
|----------|---------------|-------------|--------------|-----------------------|--------------|------------------|--------------------|----------------------|---------------------------|--------------|  
|소프트웨어 타이틀 1|소프트웨어 게시자|1.01|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 2|소프트웨어 게시자|1.02|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 3|소프트웨어 게시자|1.03|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 4|소프트웨어 게시자|1.04|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 5|소프트웨어 게시자|1.05|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 6|소프트웨어 게시자|1.06|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 7|소프트웨어 게시자|1.07|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 8|소프트웨어 게시자|1.08|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 9|소프트웨어 게시자|1.09|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
|소프트웨어 타이틀 10|소프트웨어 게시자|1.10|영어|1|구매 번호|재판매인 이름|10/10/2010|0|10/10/2012|설명|  
