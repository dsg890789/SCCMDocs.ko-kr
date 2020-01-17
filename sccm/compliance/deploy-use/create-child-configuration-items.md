---
title: 하위 구성 항목 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 자식 구성 항목을 만듭니다.
ms.date: 05/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: d194d9e80c037a13dde3d694793b695dfa5902e8
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75816618"
---
# <a name="how-to-create-child-configuration-items-in-configuration-manager"></a>Configuration Manager에서 자식 구성 항목을 만드는 방법

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 자식 구성 항목은 부모 구성 항목에서 원본 구성을 상속한다는 점에서 원본 구성 항목에 대한 관계를 유지하는 구성 항목의 복사본입니다.  

Configuration Manager 콘솔에서 자식 구성 항목의 속성을 볼 때 상속된 개체 및 설정과 해당 유효성 검사 기준은 편집할 수 없습니다. 그러나 추가 유효성 검사 조건을 자식 구성 항목에 추가하고 편집할 수 있으며 또한 자식 구성 항목에 새 개체 및 설정을 추가할 수도 있습니다.
자식 구성 항목을 만들고 편집하는 한 가지 예는 원본 구성 항목을 구체화하여 비즈니스 요구 사항을 충족하는 경우입니다.  

> [!NOTE]  
>  자식 구성 항목은 **Windows 데스크톱 및 서버(사용자 지정)** 형식의 구성 항목에서만 만들 수 있습니다.  

## <a name="to-create-a-child-configuration-item"></a>자식 구성 항목을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 항목**을 클릭합니다.  

3.  **구성 항목** 목록에서 자식 구성 항목을 만들려는 구성 항목을 선택한 다음 **홈** 탭의 **구성 항목** 그룹에서 **자식 구성 항목 만들기**를 클릭합니다.  

4.  **자식 구성 항목 만들기 마법사** 의 **일반**페이지에서 자식을 만드는 데 사용할 부모 구성 항목의 특정 수정 버전을 선택할 수 있습니다. 이 마법사의 다른 단계는 표준 구성 항목을 만드는 데 사용하는 단계와 동일합니다. 자세한 내용은 [Windows 데스크톱 및 서버 컴퓨터에 대한 사용자 지정 구성 항목을 만드는 방법](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md)을 참조하세요.  

5.  마법사를 완료합니다. 새 자식 구성 항목은 **구성 항목** 목록에 표시됩니다.  
