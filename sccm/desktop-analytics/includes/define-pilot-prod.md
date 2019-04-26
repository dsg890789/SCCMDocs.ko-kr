---
author: aczechowski
ms.author: aaroncz
ms.prod: configuration-manager
ms.topic: include
ms.date: 12/30/2018
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8305102657a5973c19ca161f65204587954b0232
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231896"
---
파일럿 및 프로덕션 구분 하려면 다음 정의 사용 합니다.  

- **파일럿**: 더 큰 집합에 배포 하기 전에 유효성을 검사 하려는 장치의 하위 집합입니다. 파일럿 집합에 고유 하 게 장치를 표시 하려면 데스크톱 Analytics를 사용 합니다. 파일럿에 대 한 장치 자산이 없습니다 차단 하는 경우 업그레이드 준비가 되었습니다. 차단 자산으로 표시 됩니다 *중요 한* 하 고 *없습니다* 업그레이드 합니다.  

- **프로덕션:** 다른 모든 장치 파일럿에 없는 데스크톱 Analytics에 등록 합니다. 프로덕션 장치의 모든 자산은 로그 오프 되 면 업그레이드 준비가 되었습니다. 모든 중요 하지 않은 자산 데스크톱 Analytics 자동으로 서명 합니다.  

