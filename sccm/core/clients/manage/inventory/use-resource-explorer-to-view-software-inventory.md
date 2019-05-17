---
title: 리소스 탐색기를 사용하여 소프트웨어 인벤토리 보기
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 리소스 탐색기를 사용하여 소프트웨어 인벤토리를 볼 수 있습니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 4b7aa5f6-5ebd-49be-b7f3-4206caadc187
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4aa4b118b87015389762ca4ec6ea79ba5ea2034f
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65499655"
---
# <a name="how-to-use-resource-explorer-to-view-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 리소스 탐색기를 사용하여 계층 구조의 컴퓨터에서 수집된 소프트웨어 인벤토리에 대한 정보를 볼 수 있습니다.  

> [!NOTE]  
>  리소스 탐색기는 소프트웨어 인벤토리 주기가 클라이언트에서 실행될 때까지 인벤토리 데이터를 표시하지 않습니다.  

 리소스 탐색기에서는 다음 소프트웨어 인벤토리 정보를 제공합니다.  

-   **소프트웨어**:  

    -   **수집된 파일**: 소프트웨어 인벤토리 중 수집된 파일.  

    -   **파일 세부 정보**: 소프트웨어 인벤토리 중 인벤토리에 포함된 파일 중에서 특정 제품 또는 제조업체와 관련이 없는 파일.  

    -   **마지막 소프트웨어 검색**: 클라이언트 컴퓨터에 대한 마지막 소프트웨어 인벤토리 및 파일 컬렉션의 날짜 및 시간.  

    -   **제품 세부 정보**: 제조업체별로 그룹화되고 소프트웨어 인벤토리를 통해 인벤토리에 포함된 소프트웨어 제품.  

## <a name="to-run-resource-explorer-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 리소스 탐색기를 실행하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.

2.  **자산 및 준수** 작업 영역에서 **디바이스** 를 선택하거나 디바이스를 표시하는 모든 컬렉션을 엽니다.  

3.  보려는 인벤토리가 포함된 컴퓨터를 선택한 다음 **홈** 탭 &gt; **디바이스** 그룹에서 **시작** > **리소스 탐색기**를 선택합니다.

4.  리소스 탐색기 창의 오른쪽 창에 있는 항목을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 선택하여 수집된 인벤토리 정보를 좀 더 읽기 쉬운 형식으로 볼 수 있습니다.  
 
