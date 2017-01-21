---
title: "하드웨어 인벤토리 보기 | 리소스 탐색기 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 리소스 탐색기를 사용하여 하드웨어 인벤토리를 볼 수 있습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
caps.latest.revision: 7
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 12bf49b6a68d277c7f505ddfe37556363d0e3e53


---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 리소스 탐색기를 사용하여 계층 구조의 클라이언트에서 수집된 하드웨어 인벤토리에 대한 정보를 볼 수 있습니다.  

> [!NOTE]  
>  리소스 탐색기는 클라이언트에서 하드웨어 인벤토리 주기가 실행 될 때까지 데이터에 연결 하는 모든 인벤토리를 표시 하지 않습니다.  

 Configuration Manager의 리소스 탐색기에는 하드웨어 인벤토리와 관련된 다음 섹션이 포함되어 있습니다.  

-   **하드웨어** - 지정된 Configuration Manager 클라이언트 장치에서 수집된 가장 최근 하드웨어 인벤토리가 포함됩니다. 재고 항목을 검토할 수 **워크스테이션 상태** 장치 하드웨어 인벤토리를 마지막 수행할 때 날짜와 시간을 검색 합니다.  

-   **하드웨어 기록** – 마지막 하드웨어 인벤토리가 수행된 이후 변경된 인벤토리 포함 항목의 기록이 포함됩니다. 목록의 각 항목에는 **현재** 노드와 하나 이상의 *<date\>* 노드가 포함됩니다. 클라이언트 컴퓨터의 하드웨어 인벤토리에서 변경 된 항목을 검색 하려면 기록 노드 중 하나에 현재 노드에서 정보를 비교할 수 있습니다.  

    > [!NOTE]  
    >  Configuration Manager에는 **오래된 인벤토리 기록 삭제** 사이트 유지 관리 작업에서 사용자가 지정하는 일수 동안 하드웨어 인벤토리 기록을 유지합니다.  

> [!NOTE]  
>  Linux 및 UNIX를 실행하는 클라이언트에서 하드웨어 인벤토리를 보는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 모니터링하는 방법](../../../../core/clients/manage/monitor-clients-for-linux-and-unix-servers.md)을 참조하세요.  

### <a name="how-to-run-resource-explorer-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 리소스 탐색기를 실행하는 방법  

1.  Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **장치** 를 클릭하거나 장치를 표시하는 모든 컬렉션을 엽니다.  

3.  보려는 인벤토리가 포함된 컴퓨터를 클릭한 다음 **홈** 탭의 **장치** 그룹에서 **시작** 을 클릭하고 **리소스 탐색기**를 클릭합니다. **리소스 탐색기** 창이 열립니다.  

4.  **리소스 탐색기** 창의 오른쪽 창에 있는 항목을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭하여 수집된 인벤토리 정보를 좀 더 읽기 쉬운 형식으로 볼 수 있는 *<항목 이름\>***속성** 대화 상자를 엽니다.  

5.  작업이 완료되면 **리소스 탐색기** 창을 닫습니다.  



<!--HONumber=Nov16_HO1-->


