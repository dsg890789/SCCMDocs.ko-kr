---
title: "자식 구성 항목 만들기 | Microsoft 문서"
description: "System Center Configuration Manager에서 자식 구성 항목을 만듭니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 113984fa-6150-41a1-89ed-d2a83b979732
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 33d4a2d5a09af74e1d76ac9b34a42b749f5bf7ef


---
# <a name="how-to-create-child-configuration-items-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 자식 구성 항목을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 자식 구성 항목은 부모 구성 항목에서 원본 구성을 상속한다는 점에서 원본 구성 항목에 대한 관계를 유지하는 구성 항목의 복사본입니다.  

Configuration Manager 콘솔에서 자식 구성 항목의 속성을 볼 때 상속된 개체 및 설정과 해당 유효성 검사 기준은 편집할 수 없습니다. 그러나 추가 유효성 검사 조건을 자식 구성 항목에 추가하고 편집할 수 있으며 또한 자식 구성 항목에 새 개체 및 설정을 추가할 수도 있습니다.
자식 구성 항목을 만들고 편집하는 일반적인 목적은 원본 구성 항목을 구체화하여 비즈니스 요구 사항을 충족하기 위해서입니다.  

> [!NOTE]  
>  자식 구성 항목은 **Windows 데스크톱 및 서버(사용자 지정)**형식의 구성 항목에서만 만들 수 있습니다.  

## <a name="to-create-a-child-configuration-item"></a>자식 구성 항목을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 항목**을 클릭합니다.  

3.  **구성 항목** 목록에서 자식 구성 항목을 만들려는 구성 항목을 선택한 다음 **홈** 탭의 **구성 항목** 그룹에서 **자식 구성 항목 만들기**를 클릭합니다.  

4.  **자식 구성 항목 만들기 마법사** 의 **일반**페이지에서 자식을 만드는 데 사용할 부모 구성 항목의 특정 수정 버전을 선택할 수 있습니다. 이 마법사의 다른 단계는 표준 구성 항목을 만드는 데 사용하는 단계와 동일합니다. 자세한 내용은 [Windows 데스크톱 및 서버 컴퓨터에 대한 사용자 지정 구성 항목을 만드는 방법](../../compliance/deploy-use/create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-client.md)을 참조하세요.  

5.  마법사를 완료합니다. 새 자식 구성 항목은 **구성 항목** 목록에 표시됩니다.  



<!--HONumber=Dec16_HO3-->


