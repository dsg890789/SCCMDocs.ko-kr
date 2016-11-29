---
title: "소프트웨어 인벤토리 보기 | 리소스 탐색기 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 리소스 탐색기를 사용하여 소프트웨어 인벤토리를 볼 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4b7aa5f6-5ebd-49be-b7f3-4206caadc187
caps.latest.revision: 5
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: b4ecb27cfb119ae80d1ed7d90d84c61a87b183c8


---
# <a name="how-to-use-resource-explorer-to-view-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 리소스 탐색기를 사용하여 계층 구조의 컴퓨터에서 수집된 소프트웨어 인벤토리에 대한 정보를 볼 수 있습니다.  

> [!NOTE]  
>  리소스 탐색기는 소프트웨어 인벤토리 주기가 사용자가 연결하는 클라이언트에서 실행될 때까지 인벤토리 데이터를 표시하지 않습니다.  

 Configuration Manager의 리소스 탐색기에는 소프트웨어 인벤토리와 관련된 다음 섹션이 포함되어 있습니다.  

-   **소프트웨어** - 리소스 탐색기의 소프트웨어 섹션에는 4개의 섹션이 포함되어 있습니다.  

    -   **수집된 파일** - 소프트웨어 인벤토리 중 수집된 파일에 대한 정보를 표시합니다.  

    -   **파일 세부 정보** - 소프트웨어 인벤토리 중 인벤토리에 포함된 파일 중에서 특정 제품 또는 제조업체와 관련이 없는 파일에 대한 정보를 표시합니다.  

    -   **마지막 소프트웨어 검색** - 클라이언트 컴퓨터에서 실행된 마지막 소프트웨어 인벤토리 및 파일 컬렉션의 날짜 및 시간을 표시합니다.  

    -   **제품 세부 정보** - 제조업체별로 그룹화되고 소프트웨어 인벤토리를 통해 인벤토리에 포함된 소프트웨어 제품에 대한 정보를 표시합니다.  

## <a name="to-run-resource-explorer-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 리소스 탐색기를 실행하려면  
 다음 절차를 사용하여 Configuration Manager에서 리소스 탐색기를 실행할 수 있습니다.  

#### <a name="to-run-resource-explorer-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 리소스 탐색기를 실행하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **장치** 를 클릭하거나 장치를 표시하는 모든 컬렉션을 엽니다.  

3.  보려는 인벤토리가 포함된 컴퓨터를 클릭한 다음 **홈** 탭의 **장치** 그룹에서 **시작** 을 클릭하고 **리소스 탐색기**를 클릭합니다. **리소스 탐색기** 창이 열립니다.  

4.  리소스 탐색기 창의 오른쪽 창에 있는 항목을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하여 수집된 인벤토리 정보를 좀 더 읽기 쉬운 형식으로 볼 수 있는 *<항목 이름\>***속성** 대화 상자를 엽니다.  

5.  작업이 완료되면 **리소스 탐색기** 창을 닫습니다.  



<!--HONumber=Nov16_HO1-->


