---
title: 소프트웨어 센터에서 애플리케이션 공유
titleSuffix: Configuration Manager
description: Configuration Manager의 소프트웨어 센터에서 애플리케이션에 대한 링크를 공유합니다.
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b7ec7fa8ef5fae89f8d1ac2c2535b3c67612a032
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75817961"
---
# <a name="share-an-application-from-software-center"></a>소프트웨어 센터에서 애플리케이션 공유

*적용 대상: Configuration Manager(현재 분기)* <!-- 1706 -->

애플리케이션 세부 정보 보기의 ![공유](media/share15.png) **공유** 단추를 사용하여 소프트웨어 센터에서 애플리케이션으로 하이퍼링크를 복사할 수 있습니다. 애플리케이션에 대한 하이퍼링크만 공유할 수 있습니다. 애플리케이션을 사용할 수 없게 되면 하이퍼링크는 애플리케이션 사용할 수 없음 메시지를 표시하는 창을 엽니다.

1. **애플리케이션**을 선택하고 해당 애플리케이션을 선택합니다.
2. ![공유](media/share15.png) **공유** 단추를 클릭합니다.
3. 창에서 **복사**를 클릭합니다.
4. 해당 URL을 전자 메일로 복사하여 애플리케이션을 공유합니다.  

> [!TIP]  
>  Outlook 이메일에 링크를 만들려면 **CTRL** + **K**를 누른 다음, URL을 붙여넣습니다.  
>  
> 기본적으로 Outlook은 수신자가 링크를 클릭하면 소프트웨어 센터 프로토콜에 대한 보안 경고를 표시합니다. 신뢰할 수 있는 프로토콜 키를 레지스트리에 추가하여 사용자 환경에서 이를 방지합니다. 예, `HKCU\Software\Policies\Microsoft\Office\16.0\Common\Security\Trusted Protocols\All Applications\softwarecenter:`  
