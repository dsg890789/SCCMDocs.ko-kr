---
title: 쿼리 관리
titleSuffix: Configuration Manager
description: 쿼리를 관리하는 방법을 알아봅니다. 자세한 참조를 위한 표를 포함합니다.
ms.date: 04/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e562e2a0-8df8-4952-952f-e8c38461c612
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 456289520e25fe94da7e94f6a795537f68ba069e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "67561971"
---
# <a name="how-to-manage-queries-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 쿼리를 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서를 참조하여 System Center Configuration Manager에서 쿼리를 보다 쉽게 관리할 수 있습니다.  

 쿼리를 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 쿼리를 만드는 방법](../../../core/servers/manage/create-queries.md)을 참조하세요.  

## <a name="manage-queries"></a>쿼리 관리
 **모니터링** 작업 영역에서 **쿼리**를 선택하고 관리할 쿼리를 선택한 다음 관리 작업을 선택합니다.  

 다음 표에서는 관리 작업에 대한 정보를 제공합니다.  

|관리 작업|세부 정보| 
|---------------------|-------------|
|**실행**|선택한 쿼리를 실행하고 Configuration Manager 콘솔에서 결과를 표시합니다.|
|**클라이언트 설치**|선택한 쿼리에서 반환하는 컴퓨터에 구성 관리자 클라이언트를 설치할 수 있는 **클라이언트 설치 마법사**를 엽니다.<br /><br /> 이 옵션은 모바일 디바이스, 사용자 또는 사용자 그룹을 반환하는 쿼리에 사용할 수 없습니다. <br /><br /> 클라이언트 강제를 사용하여 Configuration Manager 클라이언트를 설치하는 방법에 대한 자세한 내용은 [Windows 컴퓨터에 클라이언트 배포](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)를 참조하세요.| 
|**내보내기**|**개체 내보내기 마법사**를 엽니다. 이 마법사에서는 MOF(Managed Object Format) 파일로 쿼리를 내보낸 후 다른 사이트에서 가져올 수 있습니다.
|**이동**|**선택한 항목 이동** 대화 상자를 엽니다. 이 대화 상자에서는 선택한 쿼리를 **쿼리** 노드 아래의 이전에 만든 폴더로 이동할 수 있습니다.|

## <a name="next-steps"></a>다음 단계 
 [System Center Configuration Manager에서 쿼리 만들기](../../../core/servers/manage/create-queries.md)
