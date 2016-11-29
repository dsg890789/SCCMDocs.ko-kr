---
title: "하드웨어 인벤토리 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 컬렉션 또는 모든 클라이언트에 대한 하드웨어 인벤토리를 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
caps.latest.revision: 5
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 41bf42228e41785a05359c08e8dfedae48d50e30


---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>How to configure hardware inventory in System Center Configuration Manager

*적용 대상: System Center Configuration Manager(현재 분기)*

사이트에 대한 System Center Configuration Manager 하드웨어 인벤토리를 구성하려면 다음 단계를 수행하세요.  

 이 절차는 하드웨어 인벤토리에 대한 기본 클라이언트 설정을 구성하고 계층의 모든 클라이언트에 적용됩니다. 이러한 설정을 일부 클라이언트에만 적용하려면 사용자 지정 장치 클라이언트 설정을 만들고 이를 하드웨어 인벤토리를 사용하려는 장치가 포함된 컬렉션에 할당합니다. 사용자 지정 장치 설정을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

> [!NOTE]  
>  클라이언트 장치가 하드웨어 인벤토리 설정을 여러 클라이언트 설정 집합에서 받는 경우 각 설정 집합의 하드웨어 인벤토리 클래스는 클라이언트가 하드웨어 인벤토리를 보고할 때 병합됩니다.  

### <a name="to-configure-hardware-inventory"></a>하드웨어 인벤토리를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.  

3.  **기본 클라이언트 설정**을 클릭합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

5.  **기본 설정** 대화 상자에서 **하드웨어 인벤토리**를 클릭합니다.  

6.  **장치 설정** 목록에서 다음을 구성합니다.  

    -   **클라이언트에서 하드웨어 인벤토리 사용** - 드롭다운 목록에서 **True**를 선택합니다.  

    -   **하드웨어 인벤토리 일정** – 클라이언트에서 하드웨어 인벤토리를 수집하는 간격을 지정합니다. 기본값 **7일** 을 사용하거나 **일정** 을 클릭하여 사용자 지정 간격을 구성합니다.  

7.  필요한 다른 모든 클라이언트 설정을 구성합니다. 구성할 수 있는 하드웨어 인벤토리 클라이언트 설정의 목록은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../../core/clients/deploy/about-client-settings.md) 항목의 [하드웨어 인벤토리](../../../../core/clients/deploy/about-client-settings.md#BKMK_HardwareInventoryDeviceSettings) 섹션을 참조하세요.  

8.  **확인** 을 클릭하여 **기본 설정** 대화 상자를 닫습니다.  

 클라이언트 장치가 다음번에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  



<!--HONumber=Nov16_HO1-->


