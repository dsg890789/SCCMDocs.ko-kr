---
title: "하드웨어 인벤토리 - Configuration Manager | Microsoft 문서"
description: "System Center Configuration Manager의 하드웨어 인벤토리를 소개합니다."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: c64f0b42bff25e8e91cf9101d6fbb538634eab15
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-hardware-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager의 하드웨어 인벤토리 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 하드웨어 인벤토리를 사용하여 조직의 클라이언트 장치 하드웨어 구성에 대한 정보를 수집할 수 있습니다. 하드웨어 인벤토리를 수집하려면 클라이언트 설정에서 **클라이언트에서 하드웨어 인벤토리 사용** 설정을 사용하도록 설정해야 합니다.  

 하드웨어 인벤토리를 사용하도록 설정하고 나면 클라이언트는 하드웨어 인벤토리 주기를 실행한 후 클라이언트 사이트의 관리 지점으로 정보를 보냅니다. 그러면 관리 지점이 인벤토리 정보를 Configuration Manager 사이트 서버에 전달하며 여기서 인벤토리 정보를 사이트 데이터베이스에 저장합니다. 하드웨어 인벤토리는 클라이언트 설정에서 지정하는 일정에 따라 클라이언트에서 실행됩니다.  

 여러 가지 방법으로 Configuration Manager에서 수집하는 하드웨어 인벤토리 데이터를 볼 수 있습니다. 여기에는 다음이 포함됩니다.  

-   [특정 하드웨어 구성을 기반으로 하는 장치를 반환하는 쿼리를 만듭니다](../../../../core/servers/manage/queries-technical-reference.md).  

-   [특정 하드웨어 구성을 기반으로 하는 쿼리 기반 컬렉션을 만듭니다](../../../../core/clients/manage/collections/introduction-to-collections.md). 쿼리 기반 컬렉션 멤버 자격이 일정에 따라 자동으로 업데이트됩니다. 소프트웨어 배포를 포함하여 여러 작업에 대한 컬렉션을 사용할 수 있습니다. .  

-   [조직의 하드웨어 구성에 대한 특정 세부 정보를 표시하는 보고서를 실행합니다](../../../../core/servers/manage/reporting.md).   

-   [리소스 탐색기를 사용](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md)하여 클라이언트 장치에서 수집되는 하드웨어 인벤토리에 대한 자세한 정보를 볼 수 있습니다.   

 하드웨어 인벤토리가 클라이언트 장치에서 실행되는 경우 클라이언트가 반환하는 첫 번째 인벤토리 데이터는 항상 전체 인벤토리입니다. 후속 인벤토리 정보는 델타 인벤토리 정보만 포함됩니다. 사이트 서버는 받은 순서대로 델타 인벤토리 정보를 처리합니다. 클라이언트에 대한 델타 정보가 없는 경우 사이트 서버에서는 추가 델타 정보를 거부하고 클라이언트에게 전체 인벤토리 주기를 실행하도록 지시합니다.  

 Configuration Manager에서는 이중 부팅 컴퓨터를 제한적으로 지원합니다. Configuration Manager에서 이중 부팅 컴퓨터를 검색할 수 있지만 인벤토리 주기가 실행될 때 활성화되었던 운영 체제의 인벤토리 정보만 반환합니다.  

> [!NOTE]  
>  Linux 및 UNIX를 실행하는 클라이언트에서 하드웨어 인벤토리를 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 Linux 및 UNIX용 하드웨어 인벤토리](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md)를 참조하세요.  

## <a name="extending-configuration-manager-hardware-inventory"></a>Configuration Manager 하드웨어 인벤토리 확장  
 Configuration Manager의 기본 제공 하드웨어 인벤토리 외에도 다음 방법 중 하나를 사용하여 하드웨어 인벤토리를 확장하고 추가 정보를 수집할 수 있습니다.  

- Configuration Manager 콘솔에서 하드웨어 인벤토리에 대한 인벤토리 클래스를 사용하거나 사용하지 않도록 설정하고 추가 및 제거할 수 있습니다.|  
- NOIDMIF 파일을 사용하여 Configuration Manager에서 인벤토리에 포함할 수 없는 클라이언트 장치에 대한 정보를 수집합니다. 예를들어, 다음 레이블을 장치에만 존재 하는 장치 자산 번호 정보를 수집 하는 것이 좋습니다. NOIDMIF 인벤토리 클라이언트 장치에서 수집 된 자동으로 연결 됩니다.  
- IDMIF 파일을 사용하여 Configuration Manager 클라이언트와 연결되지 않은 프로젝터, 복사기, 네트워크 프린터 등의 자산에 대한 정보를 수집합니다.  

 이러한 방법을 사용하여 Configuration Manager 하드웨어 인벤토리를 확장하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 구성하는 방법](../../../../core/clients/manage/inventory/configure-hardware-inventory.md)을 참조하세요.  
