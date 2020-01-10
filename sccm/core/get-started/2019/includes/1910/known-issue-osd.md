---
author: aczechowski
ms.author: aaroncz
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: include
ms.date: 10/17/2019
ms.openlocfilehash: 01f38845992f79d49e141c5a326c0cea1c721605
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75805972"
---
### <a name="ki_osd"></a> 작업 순서는 PXE 또는 미디어에서 사용할 수 없습니다.

<!--5578298-->
PXE 또는 미디어(USB 또는 DVD) 작업 순서를 배포하는 경우 클라이언트는 정책을 받지 않습니다. 다음 메시지는 **smsts.log**에 있습니다.

`There are no task sequences available to this computer.`

#### <a name="workaround"></a>해결 방법

소프트웨어 센터에서 작업 순서를 시작합니다.
