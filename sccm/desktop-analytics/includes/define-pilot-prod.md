---
author: aczechowski
ms.author: aaroncz
ms.prod: configuration-manager
ms.topic: include
ms.date: 12/30/2018
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8305102657a5973c19ca161f65204587954b0232
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62231896"
---
아래의 정의를 참고하여 파일럿과 프로덕션을 구분하세요.  

- **파일럿**: 더 큰 세트에 배포하기 전에 유효성 검사를 진행하려는 디바이스의 하위 집합입니다. Desktop Analytics를 사용하여 디바이스를 파일럿 세트에 고유한 것으로 표시합니다. 파일럿에 포함된 디바이스는 차단하는 자산이 없는 경우 업그레이드될 준비가 되어 있습니다. 차단하는 자산은 *중요* 및 업그레이드 *불가*로 표시됩니다.  

- **프로덕션:** 파일럿에 있지 않은 Desktop Analytics에 등록된 다른 모든 있는 디바이스입니다. 프로덕션 디바이스는 모든 자산이 로그오프된 경우 업그레이드될 준비가 되어 있습니다. Desktop Analytics가 중요하지 않은 자산을 자동으로 로그오프합니다.  

