---
title: Intune에 등록된 디바이스의 정책 원격 동기화
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔에서 Intune에 등록된 디바이스의 정책을 동기화하는 방법 알아보기
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 007674dadd04839c8bba608006166c750b79ad94
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67675842"
---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 Intune에 등록된 디바이스의 정책 원격 동기화

*적용 대상: System Center Configuration Manager(현재 분기)*


Intune에 등록된 디바이스 자체의 회사 포털 앱에서 동기화를 요청하는 대신 Configuration Manager 콘솔에서 디바이스에 대한 정책 동기화를 요청할 수 있습니다. 

가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

1. **자산 및 준수** > **개요** > **디바이스** 아래에서 디바이스를 선택합니다.
2. **원격 디바이스 작업** 메뉴에서 **동기화 요청 보내기**를 클릭합니다.


5~10분 후에 정책 변경 내용이 디바이스에 동기화됩니다. 각 디바이스에 대한 **속성** 대화 상자의 검색 데이터 섹션 및 **원격 동기화 상태**라는 디바이스 보기의 새 열에서 동기화 요청 상태 정보를 볼 수 있습니다.
