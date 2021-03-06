---
title: '하드웨어 인벤토리 '
titleSuffix: Configuration Manager
description: Configuration Manager에서 하드웨어 인벤토리 소개를 확인합니다.
ms.date: 05/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: e5770a3b12e7b0e3d0c28d59cb27a14a7a8f7a5e
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824302"
---
# <a name="introduction-to-hardware-inventory-in-configuration-manager"></a>Configuration Manager에서 하드웨어 인벤토리 소개

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager에서 하드웨어 인벤토리를 사용하여 조직의 클라이언트 디바이스 하드웨어 구성에 대한 정보를 수집할 수 있습니다. 하드웨어 인벤토리를 수집하려면 클라이언트 설정에서 **클라이언트에서 하드웨어 인벤토리 사용** 설정을 선택해야 합니다.  

 하드웨어 인벤토리를 사용하도록 설정하고 나면 클라이언트는 하드웨어 인벤토리 주기를 실행한 후 클라이언트 사이트의 관리 지점으로 정보를 보냅니다. 그러면 관리 지점이 인벤토리 정보를 Configuration Manager 사이트 서버에 전달하며 여기서 인벤토리 정보를 사이트 데이터베이스에 저장합니다. 하드웨어 인벤토리는 클라이언트 설정에서 지정하는 일정에 따라 클라이언트에서 실행됩니다.  
## <a name="view-hardware-inventory"></a>하드웨어 인벤토리 보기 

 다음을 비롯한 여러 가지 방법으로 Configuration Manager에서 수집하는 하드웨어 인벤토리 데이터를 볼 수 있습니다.  

- [특정 하드웨어 구성을 기반으로 하는 디바이스를 반환하는 쿼리를 만듭니다](../../../../core/servers/manage/introduction-to-queries.md).  

- [특정 하드웨어 구성을 기반으로 하는 쿼리 기반 컬렉션을 만듭니다](../../../../core/clients/manage/collections/introduction-to-collections.md). 쿼리 기반 컬렉션 멤버 자격이 일정에 따라 자동으로 업데이트됩니다. 소프트웨어 배포를 포함하여 여러 작업에 대한 컬렉션을 사용할 수 있습니다.

- [조직의 하드웨어 구성에 대한 특정 세부 정보를 표시하는 보고서를 실행합니다](../../../../core/servers/manage/reporting.md).

- [리소스 탐색기를 사용](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md)하여 클라이언트 디바이스에서 수집되는 하드웨어 인벤토리에 대한 자세한 정보를 볼 수 있습니다.

하드웨어 인벤토리가 클라이언트 디바이스에서 실행되는 경우 클라이언트가 반환하는 첫 번째 인벤토리 데이터는 항상 전체 인벤토리입니다. 후속 인벤토리 정보는 델타 인벤토리 데이터만 포함됩니다. 사이트 서버는 받은 순서대로 델타 인벤토리 정보를 처리합니다. 클라이언트에 대한 델타 정보가 없는 경우 사이트 서버에서는 추가 델타 정보를 거부하고 클라이언트에게 전체 인벤토리 주기를 실행하도록 지시합니다.  

 Configuration Manager에서는 이중 부팅 컴퓨터를 제한적으로 지원합니다. Configuration Manager에서 이중 부팅 컴퓨터를 검색할 수 있지만 인벤토리 주기가 실행될 때 활성화되었던 운영 체제의 인벤토리 정보만 반환합니다.  

> [!NOTE]  
>  Linux 및 UNIX를 실행하는 클라이언트에서 하드웨어 인벤토리를 사용하는 방법에 대한 자세한 내용은 [Linux 및 UNIX용 하드웨어 인벤토리](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md)를 참조하세요.  

## <a name="extending-configuration-manager-hardware-inventory"></a>Configuration Manager 하드웨어 인벤토리 확장  
 Configuration Manager의 기본 제공 하드웨어 인벤토리 외에도 이러한 방법 중 하나를 사용하여 하드웨어 인벤토리를 확장하고 자세한 정보를 수집할 수 있습니다.  

- Configuration Manager 콘솔에서 하드웨어 인벤토리에 대한 인벤토리 클래스를 사용하거나 사용하지 않도록 설정하고 추가 및 제거합니다.  
- NOIDMIF 파일을 사용하여 Configuration Manager에서 인벤토리에 포함할 수 없는 클라이언트 디바이스에 대한 정보를 수집합니다. 예를들어, 다음 레이블을 디바이스에만 존재 하는 디바이스 자산 번호 정보를 수집 하는 것이 좋습니다. NOIDMIF 인벤토리 클라이언트 디바이스에서 수집 된 자동으로 연결 됩니다.  
- IDMIF 파일을 사용하여 구성 관리자 클라이언트와 연결되지 않은 프로젝터, 복사기, 네트워크 프린터 등의 자산에 대한 정보를 수집합니다.


## <a name="next-steps"></a>다음 단계
이러한 방법을 사용하여 Configuration Manager 하드웨어 인벤토리를 확장하는 방법에 대한 자세한 내용은 [하드웨어 인벤토리를 구성하는 방법](../../../../core/clients/manage/inventory/configure-hardware-inventory.md)을 참조하세요.  
