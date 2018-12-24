---
title: 하드웨어 인벤토리 구성
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 컬렉션 또는 모든 클라이언트에 대한 하드웨어 인벤토리를 설정합니다.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 1b632a9b7b7b20bc8d6653d35b267043dde6660d
ms.sourcegitcommit: 8791bb9be477fe6a029e8a7a76e2ca310acd92e0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50411003"
---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 하드웨어 인벤토리를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 절차는 하드웨어 인벤토리에 대한 기본 클라이언트 설정을 구성하고 계층의 모든 클라이언트에 적용됩니다. 이러한 설정을 일부 클라이언트에만 적용하려면 사용자 지정 디바이스 클라이언트 설정을 만들고 이를 하드웨어 인벤토리를 사용하려는 디바이스가 포함된 컬렉션에 할당합니다. [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

> [!NOTE]  
>  클라이언트 디바이스가 하드웨어 인벤토리 설정을 여러 클라이언트 설정 집합에서 받는 경우 각 설정 집합의 하드웨어 인벤토리 클래스는 클라이언트가 하드웨어 인벤토리를 보고할 때 병합됩니다. 또한 우선순위가 높은 사용자 지정 클라이언트 설정에서 클래스를 확인하지 않으면 클라이언트가 해당 클래스를 인벤토리에 보관할 수 없습니다. 

일부 시스템을 제외한 대부분의 시스템에서 특정 하드웨어 인벤토리 클래스를 사용하지 않도록 설정하려면 기본 클라이언트 설정에서 클래스를 선택 해제해야 합니다. 그런 다음, 사용자 지정 클라이언트 설정을 생성하여 클래스를 활성화하고 대상 시스템에 배포합니다.


### <a name="to-configure-hardware-inventory"></a>하드웨어 인벤토리를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **기본 설정** 대화 상자에서 **하드웨어 인벤토리**를 선택합니다.  

6.  **장치 설정** 목록에서 다음을 구성합니다.  

    -   **클라이언트에서 하드웨어 인벤토리 사용** - **예**를 선택합니다.  

    -   **하드웨어 인벤토리 일정** – **일정**을 클릭하여 클라이언트에서 하드웨어 인벤토리를 수집하는 간격을 지정합니다.  

7.  필요한 다른 [하드웨어 인벤토리 클라이언트 설정](../../../../core/clients/deploy/about-client-settings.md#hardware-inventory)을 구성합니다.  

클라이언트 디바이스가 다음번에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  
