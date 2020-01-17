---
title: 컬렉션 보안 및 개인 정보
titleSuffix: Configuration Manager
description: Configuration Manager에서 컬렉션의 보안 및 개인 정보에 대한 모범 사례를 확인합니다.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 30bf2451-5415-4be2-ba8d-21759370cd83
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 42345ee91baaad7dcc82eab537fbeb697d6cd7ab
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824404"
---
# <a name="security-and-privacy-for-collections-in-configuration-manager"></a>Configuration Manager의 컬렉션을 위한 보안 및 개인 정보

*적용 대상: Configuration Manager(현재 분기)*

이 항목에는 Configuration Manager에서 컬렉션에 대한 보안 모범 사례 및 개인 정보가 포함되어 있습니다.  

 Configuration Manager에 컬렉션 전용의 개인 정보가 없습니다. 컬렉션은 사용자 및 디바이스와 같은 리소스에 대한 컨테이너입니다. 컬렉션 멤버 자격은 종종 표준 작업 중에 Configuration Manager에서 수집하는 정보에 따라 달라집니다. 예를 들어 검색 또는 인벤토리에서 수집된 자원 정보를 사용하여 지정된 기준을 충족하는 디바이스를 포함하도록 컬렉션을 구성할 수 있습니다. 또한 컬렉션은 소프트웨어 배포 및 준수 확인 등과 같은 클라이언트 관리 작업에 대한 현재 상태 정보를 기반으로 합니다. 이러한 쿼리 기반 컬렉션 외에도 관리자가 리소스를 추가할 수도 컬렉션에 있습니다.  

 컬렉션에 대한 자세한 내용은 [컬렉션 소개](../../../../core/clients/manage/collections/introduction-to-collections.md)를 참조하세요. 컬렉션 멤버 자격을 구성하는 데 사용할 수 있는 Configuration Manager 작업에 대한 보안 모범 사례 및 개인 정보에 대한 자세한 내용은 [Configuration Manager의 보안 모범 사례 및 개인 정보](../../../../core/plan-design/security/security-best-practices-and-privacy-information.md)를 참조하세요.  

## <a name="security-best-practices-for-collections"></a>컬렉션에 대한 보안 모범 사례  
 컬렉션의 경우 다음 보안 모범 사례를 따르세요.  

|보안 모범 사례|추가 정보|  
|----------------------------|----------------------|  
|네트워크 위치에 저장되는 MOF(Managed Object Format) 파일을 사용하여 컬렉션을 내보내거나 가져오는 경우 해당 위치와 네트워크 채널을 보호합니다.|네트워크 폴더에 액세스할 수 있는 사용자를 제한합니다.<br /><br /> 공격자가 내보낸 컬렉션 데이터를 변조하지 못하도록 네트워크 위치와 사이트 서버 간에 SMB(서버 메시지 블록) 서명 또는 IPsec(인터넷 프로토콜 보안)를 사용합니다. IPsec를 사용해서 네트워크상의 데이터를 암호화하여 정보 유출을 방지합니다.|  

### <a name="security-issues-for-collections"></a>컬렉션에 대한 보안 문제  
 컬렉션에 다음과 같은 보안 문제가 있습니다.  

-   컬렉션 변수를 사용하는 경우 잠재적으로 로컬 관리자가 중요 정보를 읽을 수 있습니다.  

     운영 체제를 배포할 때 컬렉션 변수가 사용될 수 있습니다.  
