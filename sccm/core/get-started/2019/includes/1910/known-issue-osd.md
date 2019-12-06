---
author: aczechowski
ms.author: aaroncz
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: include
ms.date: 10/17/2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1a92c149de02087d7dec586769ec770f50190329
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72694430"
---
### <a name="ki_osd"></a> 작업 순서는 PXE 또는 미디어에서 사용할 수 없습니다.

<!--5578298-->
PXE 또는 미디어(USB 또는 DVD) 작업 순서를 배포하는 경우 클라이언트는 정책을 받지 않습니다. 다음 메시지는 **smsts.log**에 있습니다.

`There are no task sequences available to this computer.`

#### <a name="workaround"></a>해결 방법

소프트웨어 센터에서 작업 순서를 시작합니다.
