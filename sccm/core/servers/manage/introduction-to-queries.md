---
title: "쿼리 소개 | Microsoft 문서"
description: "쿼리를 만들고 실행하여 쿼리 조건과 일치하는 개체를 System Center Configuration Manager 계층 구조에서 찾습니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: f84d518670c0ece3c08c890d2293335518f7f8e9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-queries-in-system-center-configuration-manager"></a>System Center Configuration Manager의 쿼리 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

쿼리를 만들고 실행하여 쿼리 조건과 일치하는 개체를 System Center Configuration Manager 계층 구조에서 찾을 수 있습니다. 이러한 개체에는 특정 유형의 컴퓨터 또는 사용자 그룹과 같은 항목이 포함됩니다. 쿼리는 사이트, 컬렉션, 응용 프로그램 및 인벤토리 데이터 등을 포함한 대부분의 Configuration Manager 개체 형식을 반환할 수 있습니다.  

 쿼리를 만들 때, 검색할 위치와 검색할 개체와 같이 최소 두 개의 매개 변수를 지정해야 합니다. 예를 들어 Configuration Manager 사이트의 모든 컴퓨터에서 사용 가능한 하드 디스크 공간의 크기를 확인하려면 **논리 디스크** 특성 클래스 및 **사용 가능한 공간(MB)** 특성에서 사용 가능한 하드 디스크 공간을 검색하는 쿼리를 만들 수 있습니다.  

 초기 쿼리를 만든 후 추가 쿼리 조건을 지정할 수 있습니다. 예를 들어 쿼리 결과가 지정된 사이트에 할당된 컴퓨터만 포함되도록 지정할 수 있습니다. 또한 결과가 표시되는 방법을 수정하여 의미 있는 순서대로 결과를 볼 수 있습니다. 예를 들어 사용 가능한 하드 디스크 공간을 기준으로 오름차순이나 내림차순으로 결과를 정렬하도록 지정할 수 있습니다.  

 쿼리를 만들면 Configuration Manager에서 저장되고 **모니터링** 작업 영역의 **쿼리** 노드에 표시됩니다. 이 위치에서 새 쿼리를 만든 다음 기존 쿼리를 실행, 업데이트 또는 관리할 수 있습니다.  

 쿼리를 Configuration Manager 컬렉션의 쿼리 규칙으로 가져올 수도 있습니다. 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../core/clients/manage/collections/create-collections.md)을 참조하세요.  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager에 대한 쿼리 기술 참조](../../../core/servers/manage/queries-technical-reference.md)
