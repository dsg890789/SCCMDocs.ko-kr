---
title: 소프트웨어 인벤토리
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 소프트웨어 인벤토리를 소개합니다.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4fe27423391cbdc4767e18a06c73b23cbb302ab5
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32332513"
---
# <a name="introduction-to-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager의 소프트웨어 인벤토리 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

소프트웨어 인벤토리를 사용하여 클라이언트 장치의 파일에 대한 정보를 수집합니다. 또한 소프트웨어 인벤토리는 클라이언트 장치에서 파일을 수집하고 사이트 서버에 저장할 수 있습니다. 소프트웨어 인벤토리는 작업을 예약할 수 있는 클라이언트 설정에서 **클라이언트에서 소프트웨어 인벤토리 사용** 설정을 선택하는 경우 수집됩니다.  

소프트웨어 인벤토리가 사용되는 경우 클라이언트는 소프트웨어 인벤토리 주기를 실행한 후 정보를 클라이언트 사이트의 관리 지점으로 보냅니다. 그러면 관리 지점이 인벤토리 정보를 Configuration Manager 사이트 서버에 전달하며 여기서 정보를 사이트 데이터베이스에 저장합니다.   

 소프트웨어 인벤토리 정보를 보는 방법은 다음과 같습니다.  

-   지정된 파일이 포함된 장치를 반환하는 [쿼리를 만듭니다](../../../../core/servers/manage/queries-technical-reference.md).   

-   지정된 파일이 포함된 장치를 포함하는 [쿼리 기반 컬렉션](../../../../core/clients/manage/collections/introduction-to-collections.md)을 만듭니다.   

-   장치의 파일에 대한 세부 정보를 제공하는 [보고서를 실행합니다](../../../../core/servers/manage/reporting.md).

-   [리소스 탐색기](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md)를 사용하여 클라이언트 장치에서 인벤토리에 포함되고 수집된 파일에 대한 자세한 정보를 검사합니다.   

 소프트웨어 인벤토리가 클라이언트 장치에서 실행되는 경우 첫 번째 인벤토리 보고서는 전체 인벤토리입니다. 후속 보고서는 델타 인벤토리 정보만 포함합니다. 사이트 서버는 받은 순서대로 델타 정보를 처리합니다. 클라이언트에 대한 델타 정보가 없는 경우 사이트 서버에서는 추가 델타 정보를 거부하고 클라이언트에게 전체 인벤토리를 실행하도록 지시합니다.  

 Configuration Manager에서 이중 부팅 컴퓨터를 검색할 수 있지만 인벤토리 시 활성화되었던 운영 체제의 인벤토리 정보만 반환합니다.  

**모바일 장치의 경우:** 모바일 장치에 설치된 앱에 대한 인벤토리를 수집하는 방법은 [Microsoft Intune에서 등록한 모바일 장치를 위한 소프트웨어 인벤토리](../../../../mdm/deploy-use/software-inventory-mobile-devices.md)를 참조하세요.
