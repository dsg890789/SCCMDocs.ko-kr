---
title: 리소스 탐색기 사용 방법
titleSuffix: Configuration Manager
description: 리소스 탐색기를 사용하여 Configuration Manager에서 하드웨어 인벤토리를 확인합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c55b7b5bc4effdb1bf1f13dbe0248aa56ad2abe1
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65499968"
---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-configuration-manager"></a>리소스 탐색기를 사용하여 Configuration Manager에서 하드웨어 인벤토리를 확인하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 리소스 탐색기를 사용하여 하드웨어 인벤토리에 대한 정보를 확인합니다. 사이트는 계층 구조의 클라이언트에서 이 정보를 수집합니다.  

> [!Tip]  
>  리소스 탐색기는 사용자가 연결한 클라이언트에서 하드웨어 인벤토리 주기가 실행될 때까지 모든 데이터를 표시하지 않습니다.  



## <a name="overview"></a>개요

리소스 탐색기에는 하드웨어 인벤토리와 관련된 다음 섹션이 있습니다.  

- **하드웨어**: 지정된 클라이언트 디바이스에서 수집된 가장 최근 하드웨어 인벤토리가 표시됩니다.  

    - **워크스테이션 상태** 노드는 디바이스에서 마지막 하드웨어 인벤토리의 날짜 및 시간을 보여 줍니다.  

- **하드웨어 기록**: 마지막 하드웨어 인벤토리 주기 이후 변경된 인벤토리 포함 항목의 기록입니다.  

    - 보려는 항목을 확장하여 **현재** 노드와 하나 이상의 노드를 기록 날짜와 함께 확인합니다. 현재 노드의 정보를 기록 노드 중 하나와 비교하여 변경된 항목을 확인합니다.  

> [!NOTE]  
> 기본적으로 Configuration Manager는 90일 동안 비활성화된 하드웨어 인벤토리 데이터를 삭제합니다. 이 일 수는 **오래된 인벤토리 기록 삭제** 사이트 유지 관리 작업에서 조정합니다. 자세한 내용은 [유지 관리 작업](/sccm/core/servers/manage/maintenance-tasks)을 참조하세요.  



## <a name="bkmk_open"></a> 리소스 탐색기를 여는 방법   

1.  Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동하고 **디바이스** 노드를 선택합니다. **디바이스 컬렉션** 노드에서 모든 컬렉션을 선택할 수도 있습니다.  

2.  디바이스를 선택합니다. 리본에 있는 **홈** 탭 및 **디바이스** 그룹에서 **시작**을 클릭한 다음, **리소스 탐색기**를 선택합니다.   

> [!Tip]  
> 리소스 탐색기에서 추가 작업에 대한 올바른 결과 창에서 항목을 마우스 오른쪽 단추로 클릭합니다. 해당 항목을 다른 형식으로 보려면 **속성**을 클릭합니다.  



## <a name="bkmk_bigint"></a> 큰 정수 값 사용
<!--1357880-->
Configuration Manager 버전 1802 이전 버전에서 하드웨어 인벤토리는 4,294,967,296(2^32)보다 큰 정수로 제한됩니다. 하드 드라이브 크기(바이트)와 같은 특성의 경우 이 제한에 도달할 수 있습니다. 관리 지점은 이 제한을 초과하는 정수 값을 처리하지 않으므로 값이 데이터베이스에 저장되지 않습니다. 

1806 버전부터 제한은 18,446,744,073,709,551,616(2^64)으로 증가되었습니다. 

전체 디스크 크기와 같이 변경되지 않는 값을 가진 속성의 경우 사이트를 업그레이드한 후 바로 값이 표시되지 않을 수 있습니다. 대부분의 하드웨어 인벤토리는 델타 보고서입니다. 클라이언트는 변경되는 값만 전송합니다. 이 동작을 해결하려면 동일한 클래스에 다른 속성을 추가하세요. 이 작업을 수행하면 클라이언트가 변경된 클래스에서 모든 속성을 업데이트합니다. 



## <a name="see-also"></a>참고 항목

Linux 및 UNIX를 실행하는 클라이언트에서 하드웨어 인벤토리를 보는 방법에 대한 자세한 내용은 [Linux 및 UNIX 서버용 클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients-for-linux-and-unix-servers)을 참조하세요.  

리소스 탐색기는 소프트웨어 인벤토리도 표시합니다. 자세한 내용은 [소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory)을 참조하세요.
