---
title: "마이그레이션 모니터링"
titleSuffix: Configuration Manager
description: "Configuration Manager 콘솔을 사용하여 마이그레이션 작업의 진행률과 성공을 모니터링하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 1782e8abaf01cf8097393fa45db999a6a02c6cb5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="planning-to-monitor-migration-activity-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 마이그레이션 작업 모니터링 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 대상 계층 구조에 연결된 Configuration Manager 콘솔에서 마이그레이션을 모니터링할 수 있습니다. Configuration Manager 콘솔의 **관리** 작업 영역에서 **마이그레이션** 노드를 사용하여 마이그레이션 작업의 진행률과 성공을 모니터링할 수 있습니다. 마이그레이션한 개체, 아직 마이그레이션하지 않은 개체 및 마이그레이션 작업에서 제외된 개체 수를 식별하는 각 마이그레이션 작업에 대한 요약 정보를 볼 수 있습니다. 마이그레이션 문제에 대한 세부 정보도 볼 수 있습니다.  

## <a name="view-migration-progress"></a>마이그레이션 진행률 보기  
 마이그레이션 작업의 진행률을 보려면 다음 작업 중 하나를 수행하십시오.  

-   Configuration Manager 콘솔의 **관리** 작업 영역에서 **마이그레이션 작업** 노드를 확장하고 마이그레이션 작업을 선택한 후에 **작업에 포함된 개체** 탭을 선택합니다.  

-   Configuration Manager 로그 파일을 사용하여 마이그레이션 진행률을 검토하거나 문제를 확인합니다. 마이그레이션 관리자는 마이그레이션 작업을 추적하고 사이트 서버의 **\&lt;InstallationPath\>\\LOGS** 폴더에 있는 migmctrl.log 파일에 이러한 내용을 기록하는 Configuration Manager 프로세스입니다.  

    > [!NOTE]  
    >  마이그레이션 작업이 실패하면 최대한 빨리 migmctrl.log 파일의 정보를 검토하십시오. 마이그레이션 로그 항목은 계속 파일에 추가되어 이전 정보를 덮어씁니다. 항목을 덮어쓰면 마이그레이션된 개체에 발생할 수 있는 문제가 마이그레이션 문제와 관련이 있는지 여부를 확인하지 못할 수도 있습니다. 마이그레이션 작업은 마이그레이션을 구성할 때 Configuration Manager 콘솔에서 연결한 사이트와 상관없이 계층의 최상위 사이트에서 로깅됩니다.  

-   Configuration Manager 보고를 사용합니다. Configuration Manager에서 마이그레이션을 위해 제공하는 여러 기본 제공 보고서를 그대로 사용할 수도 있고 요구 사항에 맞게 편집할 수도 있습니다. Configuration Manager 보고서에 대한 자세한 내용은 [System Center Configuration Manager에서 보고](../../core/servers/manage/reporting.md)를 참조하세요.  
