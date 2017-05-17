---
title: "Endpoint Protection 상태 모니터링 | Microsoft 문서"
description: "System Center Configuration Manager 계층 구조에서 Endpoint Protection을 모니터링하는 방법을 알아봅니다."
ms.custom: na
ms.date: 03/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4a1335c-bb3d-493e-a124-83a32a107dc8
caps.latest.revision: 8
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 0fa837c68eb073d2ceaf48c938137a94141a102e
ms.openlocfilehash: 99e266e44f718d97c2a6e61e8e6816752751ed7b
ms.contentlocale: ko-kr
ms.lasthandoff: 01/24/2017


---
# <a name="how-to-monitor-endpoint-protection-status"></a>Endpoint Protection 상태를 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

**모니터링** 작업 영역 **보안** 아래의 **Endpoint Protection 상태** 노드, **자산 및 호환성** 작업 영역의 **Endpoint Protection** 노드 및 보고서를 사용하여 Microsoft System Center Configuration Manager 계층에서 Endpoint Protection을 모니터링할 수 있습니다.  

##  <a name="BKMK_1"></a> Endpoint Protection 상태 노드를 사용하여 Endpoint Protection을 모니터링하는 방법  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **보안**을 확장한 다음 **Endpoint Protection 상태**를 클릭합니다.  

3.  에 **컬렉션** 목록에서 상태 정보를 보려는 컬렉션을 선택 합니다.  

    > [!IMPORTANT]  
    >  컬렉션은 다음과 같은 경우에는 선택할 수 있습니다.  
    >   
    >  -   *<컬렉션 이름\>***속성** 대화 상자의 **경고** 탭에 **Endpoint Protection 대시보드에서 이 컬렉션 보기**를 선택한 경우  
    > -   Endpoint Protection 맬웨어 방지 정책을 컬렉션에 배포하는 경우  
    > -   Endpoint Protection 클라이언트 설정을 사용하도록 설정하고 컬렉션에 배포하는 경우.  

4.  에 표시 되는 정보를 검토 하 여 **보안 상태** 및 **작동 상태** 섹션. 임시 컬렉션을 만들를 상태 링크를 클릭할 수는 **장치** 에서 노드는 **자산 및 준수** 작업 영역입니다. 임시 컬렉션 선택 된 상태를 사용 하 여 컴퓨터를 포함합니다.  

    > [!IMPORTANT]  
    >  **상태** 노드에 표시되는 정보는 Configuration Manager 데이터베이스에서 마지막으로 요약된 데이터를 기반으로 하며 최신 정보가 아닐 수도 있습니다. 최신 데이터를 검색하려는 경우 **홈** 탭에서 **요약 실행**을 클릭하거나 **요약 일정** 을 클릭하여 요약 간격을 조정합니다.  

##  <a name="BKMK_2"></a> 자산 및 준수 작업 영역에서 Endpoint Protection을 모니터링하는 방법  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  에 **자산 및 준수** 작업 영역에서 다음 작업 중 하나를 수행 합니다.  

    -   클릭 하 여 **장치**. 에 **장치** 목록 컴퓨터를 선택한 다음 클릭는 **맬웨어 세부** 탭 합니다.  

    -   클릭 하 여 **장치 컬렉션**. **장치 컬렉션** 목록에서 모니터링할 컴퓨터가 포함된 컬렉션을 선택한 후 **홈** 탭의 **컬렉션** 그룹에서 **멤버 표시**를 클릭합니다.  

3.  *<컬렉션 이름\>* 목록에서 컴퓨터를 선택하고 **맬웨어 세부 정보** 탭을 클릭합니다.  

##  <a name="BKMK_3"></a> 보고서를 사용하여 Endpoint Protection을 모니터링하는 방법  
 계층 구조의 Endpoint Protection에 대한 정보를 보려면 다음 보고서를 참조하세요. 이러한 보고서를 사용하여 Endpoint Protection 문제를 해결할 수도 있습니다. Configuration Manager에서 보고를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../core/servers/manage/reporting.md) 및 [System Center Configuration Manager의 로그 파일](../../core/plan-design/hierarchy/log-files.md)을 참조하세요. Endpoint Protection 보고서는 Endpoint Protection 폴더에 있습니다.  

|보고서 이름|설명|  
|-----------------|-----------------|  
|**맬웨어 방지 활동 보고서**|지정된 된 컬렉션에 대 한 맬웨어 방지 활동에 대 한 개요를 표시합니다.|  
|**감염 된 컴퓨터**|지정한 위협을 검색 하는 컴퓨터의 목록이 표시 됩니다.|  
|**위협 하 여 상위 사용자**|검색 된 위협의 최대값을 보유 하는 사용자의 목록을 표시합니다.|  
|**사용자 위협 목록**|지정된 된 사용자 계정에 대해 발견 된 위협 목록에 표시 됩니다.|  

## <a name="malware-alert-levels"></a>맬웨어 경고 수준  
 보고서나 Configuration Manager 콘솔에 표시될 수 있는 다양한 Endpoint Protection 경고 수준을 식별하려면 다음 표를 참조하세요.  

|경고 수준|설명|  
|-----------------|-----------------|  
|**실패**|Endpoint Protection에서 맬웨어를 수정하지 못했습니다. 오류의 세부 정보에 대 한 로그를 확인 합니다.<br /><br /> **참고:** Configuration Manager 및 Endpoint Protection 로그 파일 목록은 [System Center Configuration Manager의 로그 파일](../../core/plan-design/hierarchy/log-files.md) 항목에서 "Endpoint Protection" 섹션을 참조하세요.|  
|**제거됨**|Endpoint Protection에서 맬웨어를 제거했습니다.|  
|**격리됨**|Endpoint Protection에서 맬웨어를 안전한 위치로 이동하고, 제거하거나 실행을 허용할 때까지 실행되지 않도록 차단했습니다.|  
|**치료됨**|맬웨어 감염된 된 파일에서 정리 되었습니다.|  
|**허용**|관리 사용자 실행 하는 맬웨어를 포함 하는 소프트웨어를 허용 하도록 선택 합니다.|  
|**작업 없음**|Endpoint Protection에서 맬웨어에 대해 아무 작업도 수행하지 않았습니다. 맬웨어가 검색 되 고 맬웨어가 더 이상 감지; 후 컴퓨터를 다시 시작한 경우 발생할 수 없습니다. 예 매핑된 네트워크 드라이브에 있는 경우 어떤 맬웨어가 검색 되는 다시 연결 되지 컴퓨터를 다시 시작 합니다.|  
|**차단**|Endpoint Protection에서 맬웨어가 실행되지 않도록 차단했습니다. 이 맬웨어를 포함 하는 컴퓨터의 프로세스에 없는 경우에 발생할 수 있습니다.|

