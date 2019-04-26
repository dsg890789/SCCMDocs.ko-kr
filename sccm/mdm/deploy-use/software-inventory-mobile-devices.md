---
title: Microsoft Intune에서 등록한 모바일 디바이스를 위한 소프트웨어 인벤토리
titleSuffix: Configuration Manager
description: Microsoft Intune에서 등록한 모바일 디바이스를 위한 소프트웨어 인벤토리
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: a0eae17a-60a8-4132-91af-0b10ad338c92
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 91d298dae14c879e215b85483558898382c12055
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227882"
---
# <a name="software-inventory-for-mobile-devices-enrolled-with-microsoft-intune"></a>Microsoft Intune에서 등록한 모바일 디바이스를 위한 소프트웨어 인벤토리

*적용 대상: System Center Configuration Manager(현재 분기)*

 모바일 디바이스에 설치되는 앱에 대한 인벤토리를 수집할 수 있습니다. 인벤토리에 추가되는 앱은 디바이스가 회사 소유인지 또는 개인 소유인지에 따라 달라집니다. 개인 디바이스의 경우 Microsoft Intune에서 관리되는 앱만 인벤토리에 추가됩니다.  

> [!NOTE]  
>  모바일 디바이스에 설치된 앱의 인벤토리는 [하드웨어 인벤토리](mobile-device-hardware-inventory-hybrid.md) 프로세스의 일부로 수집됩니다.  

 다음은 개인 소유 또는 회사 소유의 디바이스에 대해 인벤토리에 포함되는 앱입니다.  

|플랫폼|개인 소유 디바이스|회사 소유 디바이스|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10(Configuration Manager 클라이언트 없음)|관리되는 앱만|관리되는 앱만|
|Windows 8.1(Configuration Manager 클라이언트 없음)|관리되는 앱만|관리되는 앱만|  
|Windows Phone 8|관리되는 앱만|관리되는 앱만|  
|Windows RT|관리되는 앱만|관리되는 앱만|  
|iOS|관리되는 앱만|디바이스에 설치되는 모든 앱|  
|Android|관리되는 앱만|디바이스에 설치되는 모든 앱|  

소프트웨어 인벤토리를 사용 클라이언트 디바이스에서 파일 정보를 수집하는 방법에 대한 자세한 내용은 [소프트웨어 인벤토리 소개](../../core/clients/manage/inventory/introduction-to-software-inventory.md) 및 [소프트웨어 인벤토리를 구성하는 방법](../../core/clients/manage/inventory/configure-software-inventory.md)을 참조하세요.
