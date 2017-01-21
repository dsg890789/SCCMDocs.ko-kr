---
title: "소프트웨어 인벤토리 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 소프트웨어 인벤토리 및 인벤토리 제외 폴더를 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: cc226259-0e28-410a-94d3-223bdc948818
caps.latest.revision: 4
caps.handback.revision: 0
author: nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 5f30eb754832fcc259caf853dc33ccfcb82cf8bc


---
# <a name="how-to-configure-software-inventory-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 인벤토리를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

**Skpswi.dat**라는 숨겨진 파일을 만들어 System Center Configuration Manager 소프트웨어 인벤토리에서 제외하기 위해 클라이언트 하드 드라이브의 루트에 배치합니다. 또한 소프트웨어 인벤토리에서 제외하려는 폴더 구조의 루트에 이 파일을 배치할 수 있습니다. 이 절차를 사용하여 단일 워크스테이션 또는 서버 클라이언트(예: 대규모 파일 서버)에서 소프트웨어 인벤토리를 사용하지 않도록 설정할 수 있습니다.  

> [!NOTE]  
>  클라이언트 컴퓨터의 드라이브에서 이 파일을 삭제하지 않는 한 소프트웨어 인벤토리가 클라이언트 드라이브를 다시 인벤토리에 포함하지 않습니다.  

### <a name="to-exclude-folders-from-software-inventory"></a>소프트웨어 인벤토리에서 폴더를 제외하려면  

1.  Notepad.exe를 사용하여 **Skpswi.dat**라는 빈 파일을 만듭니다.  

2.  **Skpswi.dat** 파일을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다. Skpswi.dat 파일에 대한 파일 속성에서 **숨김** 특성을 선택합니다.  

3.  소프트웨어 인벤토리에서 제외하려는 각 클라이언트 하드 드라이브 또는 폴더 구조의 루트에 **Skpswi.dat** 파일을 배치합니다.  



<!--HONumber=Nov16_HO1-->


