---
title: "다국어 기능 지원 | System Center Configuration Manager"
description: "특정 다국어 기능 요구 사항을 준수하도록 System Center Configuration Manager를 구성합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 592ae2b8fbf55fa59afe909071a81b6bd3159ef7


---
# <a name="international-support-in-system-center-configuration-manager"></a>System Center Configuration Manager의 다국어 기능 지원

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 섹션에서는 특정 다국어 기능 요구 사항을 준수하도록 System Center Configuration Manager를 구성하는 방법에 대한 기술적인 정보를 제공합니다.  

## <a name="gb18030-requirements"></a>GB18030 요건  
 Configuration Manager는 GB18030에 정의된 표준을 준수하므로 중국에서 Configuration Manager를 사용할 수 있습니다. GB18030 요구 사항을 준수하려면 Configuration Manager 배포가 다음 구성을 갖추어야 합니다.  

-   Configuration Manager에서 사용하는 각 사이트 서버 컴퓨터와 SQL Server 컴퓨터가 중국어 운영 체제를 사용해야 합니다.  

-   각 사이트 데이터베이스와 계층의 각 SQL Server 인스턴스의 정렬이 동일해야 하고 다음 중 하나여야 합니다.  

    -   Chinese_Simplified_Pinyin_100_CI_AI  

    -   Chinese_Simplified_Stroke_Order_100_CI_AI  

    > [!NOTE]  
    >  이러한 데이터베이스 정렬은 [System Center Configuration Manager에 대한 SQL Server 버전 지원](../../../core/plan-design/configs/support-for-sql-server-versions.md)에 설명된 요구 사항에 대한 예외입니다.  

-   계층에 있는 각 사이트 서버 컴퓨터 시스템 볼륨의 루트 폴더에 **GB18030.SMS** 라는 이름의 파일을 배치해야 합니다. 이 파일은 이 요구 사항을 충족하도록 이름이 지정된, 데이터가 없이 비어 있는 텍스트 파일일 수 있습니다.  



<!--HONumber=Nov16_HO1-->


