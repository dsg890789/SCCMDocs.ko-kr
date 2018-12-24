---
title: 구성 데이터 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 구성 항목 및 기준을 만든 후 다른 명령을 사용하여 다양한 작업을 수행할 수 있습니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: b48c693c-d2b0-4707-a5dd-fe92172c49fe
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: d4602a2dbee04259d5953873485cdbccdc58167d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32333663"
---
# <a name="manage-configuration-data-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 구성 데이터 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 구성 항목 및 구성 기준을 만든 후 추가 명령을 사용하여 다양한 작업을 수행할 수 있습니다.  

## <a name="manage-configuration-items"></a>구성 항목 관리  

-   **자산 및 준수** 작업 영역에서 **준수 설정** > **구성 항목**을 확장하고 관리할 구성 항목을 선택한 다음 관리 작업을 선택합니다.  

|관리 작업|세부 정보|  
|---------------------|-------------|  
|**자식 구성 항목 만들기**|선택한 구성 항목에서 자식 구성 항목을 만들 수 있는 **자식 구성 항목 만들기 마법사** 를 엽니다.<br /><br /> 모바일 디바이스 구성 항목에서는 자식 구성 항목을 만들 수 없습니다.<br /><br /> 자세한 내용은 [하위 구성 항목 만들기](../../compliance/deploy-use/create-child-configuration-items.md)를 참조하세요.|  
|**수정 기록**|선택한 구성 항목의 이전 수정 버전을 보고 관리할 수 있는 **구성 항목 수정 기록** 대화 상자를 엽니다.|  
|**XML 정의 보기**|새 창에서 선택한 구성 항목에 대한 XML 정의 파일이 표시됩니다. 이 정보는 구성 데이터를 수동으로 작성 하려고 할 때 유용할 수 있습니다.|  
|**내보내기**|구성 항목을 해당 사이트에서 만들어졌다는 정보 제공과 함께 캐비닛(.cab) 파일 형식으로 내보냅니다. 그런 다음 동일한 사이트 또는 다른 Configuration Manager 사이트로 가져올 수 있습니다. 구성 데이터가 DCM 다이제스트로 변환됩니다.|  
|**복사**|지정하는 이름을 사용하여 선택한 구성 항목 사본을 만듭니다. 새 구성 항목이 원본 구성 항목에 대한 관계를 유지하지 않습니다. 즉, 중복 된 구성 항목은 원래 구성 항목에서 구성 정보를 상속 하도록 계속 되지 않습니다.|  
|**삭제**|이 구성 항목에 참조를 검토할 수 있는 **구성 항목 삭제** 대화 상자를 엽니다.<br /><br /> 구성 항목을 삭제하려면 먼저 구성 항목에 대한 모든 참조를 제거해야 합니다.|  

## <a name="manage-configuration-baselines"></a>구성 기준 관리  

-   **자산 및 준수** 작업 영역에서 **준수 설정** > **구성 기준**을 확장하고 관리할 구성 기준을 선택한 다음 관리 작업을 선택합니다.  


|관리 작업|세부 정보|  
|---------------------|-------------|  
|**멤버 표시**|구성 기준에서 참조된 모든 구성 항목을 표시합니다.|  
|**요약 일정**|Configuration Manager 콘솔의 **구성 기준** 노드에 나와 있는 데이터가 사이트 데이터베이스의 최신 정보를 사용하여 업데이트되는 일정을 구성합니다.|  
|**요약 실행**|요약을 통해 **구성 기준** 노드의 데이터가 사이트 데이터베이스의 최신 데이터로 새로 고쳐집니다. 이 작업을 완료하는 데 몇 분 정도 걸릴 수 있습니다. 콘솔에서 최신 데이터를 보려면 **새로 고침** 을 클릭해야 할 수 있습니다.|  
|**XML 정의 보기**|새 창에서 선택한 구성 기준에 대한 XML 정의 파일을 표시합니다. 이 정보는 구성 데이터를 수동으로 작성 하려고 할 때 유용할 수 있습니다.|  
|**사용**|규정 준수를 모니터링 하기 위한 구성 기준을 수 있습니다.|  
|**사용 안 함**|구성 기준을 사용하지 않으므로 클라이언트 컴퓨터에서 준수 여부가 더 이상 평가되지 않습니다. 이 구성 기준 참조 하는 구성 기준도 비활성화 됩니다.|  
|**내보내기**|구성 기준을 해당 사이트에서 만들어졌다는 정보 제공과 함께 캐비닛(.cab) 파일 형식으로 내보냅니다. 그런 다음 동일한 사이트 또는 다른 Configuration Manager 사이트로 가져올 수 있습니다. 구성 데이터가 DCM 다이제스트로 변환됩니다.<br /><br /> 구성 데이터를 가져오는 방법에 대한 자세한 내용은 [구성 데이터 가져오기](../../compliance/deploy-use/import-configuration-data.md)를 참조하세요.|  
|**복사**|지정한 이름을 사용하여 선택한 구성 기준의 복사본을 만듭니다. 새 구성 기준을 원래 구성 기준에 모든 관계를 유지 하지 않습니다.|  
|**삭제**|이 구성 기준에 대한 참조를 검토할 수 있는 **구성 기준 삭제** 대화 상자를 엽니다.<br /><br /> 구성 기준을 삭제하려면 먼저 구성 기준에 대한 모든 참조를 제거해야 합니다.|  
|**배포**|하나 이상의 구성 기준을 계층의 디바이스에 배포할 수 있는 **구성 기준 배포** 대화 상자를 엽니다.<br /><br /> 자세한 내용은 [구성 기준 배포](../../compliance/deploy-use/deploy-configuration-baselines.md)를 참조하세요.|  
