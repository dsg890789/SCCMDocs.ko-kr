---
title: 소프트웨어 인벤토리
titleSuffix: Configuration Manager
description: Configuration Manager의 소프트웨어 인벤토리를 소개합니다.
ms.date: 04/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 71ca3ab9a2bcb3233bcf134ad82117838f9f0208
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76033970"
---
# <a name="introduction-to-software-inventory-in-configuration-manager"></a>Configuration Manager에서 소프트웨어 인벤토리 소개

*적용 대상: Configuration Manager(현재 분기)*

소프트웨어 인벤토리를 사용하여 클라이언트 디바이스의 파일에 대한 정보를 수집합니다. 또한 소프트웨어 인벤토리는 클라이언트 디바이스에서 파일을 수집하고 사이트 서버에 저장할 수 있습니다. 소프트웨어 인벤토리는 클라이언트 설정에서 **클라이언트에서 소프트웨어 인벤토리 사용** 설정을 선택할 때 수집됩니다. 또한 클라이언트 설정에서 이 작업을 예약할 수도 있습니다.  

소프트웨어 인벤토리를 사용하도록 설정하는 경우 클라이언트는 소프트웨어 인벤토리 주기를 실행한 후 정보를 클라이언트 사이트의 관리 지점으로 보냅니다. 그러면 관리 지점이 인벤토리 정보를 Configuration Manager 사이트 서버에 전달하며 여기서 정보를 사이트 데이터베이스에 저장합니다.

 다음과 같은 몇 가지 방법으로 소프트웨어 인벤토리 정보를 볼 수 있습니다.  

- 지정된 파일이 포함된 디바이스를 반환하는 [쿼리를 만듭니다](../../../../core/servers/manage/create-queries.md).   

- 지정된 파일이 포함된 디바이스를 포함하는 [쿼리 기반 컬렉션](../../../../core/clients/manage/collections/introduction-to-collections.md)을 만듭니다.   

- 디바이스의 파일에 대한 세부 정보를 제공하는 [보고서를 실행합니다](../../../../core/servers/manage/reporting.md).

- [리소스 탐색기](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md)를 사용하여 클라이언트 디바이스에서 인벤토리에 포함되고 수집된 파일에 대한 자세한 정보를 검사합니다.   

 소프트웨어 인벤토리가 클라이언트 디바이스에서 실행되는 경우 첫 번째 인벤토리 보고서는 전체 인벤토리입니다. 후속 보고서는 델타 인벤토리 정보만 포함합니다. 사이트 서버는 받은 순서대로 델타 정보를 처리합니다. 클라이언트에 대한 델타 정보가 없는 경우 사이트 서버에서는 추가 델타 정보를 거부하고 클라이언트에게 전체 인벤토리를 실행하도록 지시합니다.  

 Configuration Manager에서 이중 부팅 컴퓨터를 검색할 수 있지만 인벤토리 시 활성화되었던 운영 체제의 인벤토리 정보만 반환합니다.  
