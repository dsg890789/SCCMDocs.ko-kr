---
title: "하드웨어 인벤토리 구성"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에서 컬렉션 또는 모든 클라이언트에 대한 하드웨어 인벤토리를 설정합니다."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 91f17e4ab9f828576ac1b11076a008289ff588a0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>How to configure hardware inventory in System Center Configuration Manager

*적용 대상: System Center Configuration Manager(현재 분기)*

이 절차는 하드웨어 인벤토리에 대한 기본 클라이언트 설정을 구성하고 계층의 모든 클라이언트에 적용됩니다. 이러한 설정을 일부 클라이언트에만 적용하려면 사용자 지정 장치 클라이언트 설정을 만들고 이를 하드웨어 인벤토리를 사용하려는 장치가 포함된 컬렉션에 할당합니다. [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

> [!NOTE]  
>  클라이언트 장치가 하드웨어 인벤토리 설정을 여러 클라이언트 설정 집합에서 받는 경우 각 설정 집합의 하드웨어 인벤토리 클래스는 클라이언트가 하드웨어 인벤토리를 보고할 때 병합됩니다.  

### <a name="to-configure-hardware-inventory"></a>하드웨어 인벤토리를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **기본 설정** 대화 상자에서 **하드웨어 인벤토리**를 선택합니다.  

6.  **장치 설정** 목록에서 다음을 구성합니다.  

    -   **클라이언트에서 하드웨어 인벤토리 사용** - **True**를 선택합니다.  

    -   **하드웨어 인벤토리 일정** – **일정**을 클릭하여 클라이언트에서 하드웨어 인벤토리를 수집하는 간격을 지정합니다.  

7.  필요한 다른 [하드웨어 인벤토리 클라이언트 설정](../../../../core/clients/deploy/about-client-settings.md#hardware-inventory)을 구성합니다.  

클라이언트 장치가 다음번에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../../../core/clients/manage/manage-clients.md)을 참조하세요.  
