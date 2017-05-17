---
title: "원격 제어 사용 감사 | Microsoft 문서"
description: "System Center Configuration Manager에서 원격 제어 사용 감사"
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5c975e69-0cc0-4afd-b7fb-b7182162a933
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: e3082e1d608f60a539fc58b0129132e33c8af833
ms.contentlocale: ko-kr
ms.lasthandoff: 12/16/2016


---
# <a name="how-to-audit-remote-control-usage-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 원격 제어 사용을 감사하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 보고서를 사용하여 원격 제어에 대한 감사 정보를 볼 수 있습니다.  

 Configuration Manager에서 보고를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../../../core/servers/manage/reporting.md)를 참조하세요.  

 다음 두 보고서는 **상태 메시지 - 감사**범주에서 사용할 수 있습니다.  

-   **원격 제어 - 특정 사용자가 원격으로 제어하는 모든 컴퓨터** – 특정 사용자가 시작한 원격 제어 작업 요약을 표시합니다.  

-   **원격 제어 - 모든 원격 제어 정보** - 클라이언트 컴퓨터의 원격 제어에 대한 상태 메시지 요약을 표시합니다.  

### <a name="to-run-the-report-remote-control---all-computers-remote-controlled-by-a-specific-user"></a>원격 제어 - 특정 사용자가 원격으로 제어하는 모든 컴퓨터 보고서를 실행하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **보고**를 확장한 후 **보고서**를 클릭합니다.  

3.  **보고서** 노드에서 **범주** 열을 클릭하여 보고서를 정렬하면 **상태 메시지 - 감사**범주에서 보고서를 더 쉽게 찾을 수 있습니다.  

4.  **원격 제어 - 특정 사용자가 원격으로 제어하는 모든 컴퓨터**보고서를 선택한 다음 **홈** 탭의 **보고서 그룹**에서 **실행**을 클릭합니다.  

5.  **원격 제어 - 특정 사용자가 원격으로 제어하는 모든 컴퓨터** 의 **사용자 이름**목록에서 감사 정보를 보고할 사용자를 지정한 다음 **보고서 보기**를 클릭합니다.  

6.  보고서의 데이터를 다 보았으면 보고서 창을 닫습니다.  

### <a name="to-run-the-report-remote-control---all-remote-control-information"></a>원격 제어 - 모든 원격 제어 정보 보고서를 실행하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **보고**를 확장한 후 **보고서**를 클릭합니다.  

3.  **보고서** 노드에서 **범주** 열을 클릭하여 보고서를 정렬하면 **상태 메시지 - 감사**범주에서 보고서를 더 쉽게 찾을 수 있습니다.  

4.  보고서 **원격 제어 - 모든 원격 제어 정보**를 선택한 다음 **홈** 탭의 **보고서 그룹**에서 **실행** 을 클릭하여 **원격 제어 - 모든 원격 제어 정보** 창을 엽니다.  

5.  보고서의 데이터를 다 확인했으면 보고서 창을 닫습니다.  

