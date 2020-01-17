---
title: 쿼리에 대한 보안 및 개인 정보
titleSuffix: Configuration Manager
description: 사이트 데이터베이스에서 정보를 쿼리할 때 보안 및 개인 정보에 대한 모범 사례를 이해합니다.
ms.date: 05/08/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 30080620-20d3-4c38-b8dd-db5516e1acae
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 3bb2647f8914ed45d77c1d6718ee258f8d8f373d
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793463"
---
# <a name="security-and-privacy-for-queries-in-configuration-manager"></a>Configuration Manager에서 쿼리를 위한 보안 및 개인 정보

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 쿼리를 사용하여 지정하는 기준에 따라 사이트 데이터베이스에서 정보를 검색할 수 있습니다. Configuration Manager에서 표준 작업 중에 사이트 데이터베이스 정보를 수집합니다. 예를 들어 검색 또는 인벤토리 중에 수집된 정보를 사용하여 지정된 기준을 충족하는 디바이스를 식별하는 쿼리를 구성할 수 있습니다.  

 쿼리에 대한 자세한 내용은 [쿼리 소개](../../../core/servers/manage/introduction-to-queries.md)를 참조하세요. 쿼리를 사용하여 검색할 수 있는 데이터를 수집하는 Configuration Manager 작업에 대해 보안 모범 사례 및 개인 정보에 대해서는 [Configuration Manager의 보안 및 개인 정보](../../../core/plan-design/security/security-and-privacy.md)를 참조하세요.  

## <a name="security-best-practices-for-queries"></a>쿼리에 대한 보안 모범 사례

 쿼리의 경우 다음 보안 모범 사례를 따르세요.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|네트워크 위치에 저장된 쿼리를 가져오거나 내보내는 경우 해당 위치와 네트워크 채널을 보호합니다.|네트워크 폴더에 액세스할 수 있는 사용자를 제한합니다.<br /><br /> 쿼리 데이터를 가져오기 전에 공격자가 변조하지 못하도록 네트워크 위치와 사이트 서버 간에 SMB(서버 메시지 블록) 서명 또는 IPsec(인터넷 프로토콜 보안)을 사용합니다.|  

## <a name="next-steps"></a>다음 단계
  
[Configuration Manager에 대한 보안 및 개인 정보](../../../core/plan-design/security/security-and-privacy.md)
