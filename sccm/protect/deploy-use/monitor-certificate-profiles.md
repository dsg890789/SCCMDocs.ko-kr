---
title: "인증서 프로필 모니터링 | System Center Configuration Manager"
description: "System Center Configuration Manager 인증서 프로필의 준수 상태를 모니터링하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98feaa06-64b1-4e86-a122-93017c97cd4f
caps.latest.revision: 7
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: bb72571596e77ce3069c1f6526fb3ba00fc9ecdc


---
# <a name="how-to-monitor-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 인증서 프로필을 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


계층 구조 내 사용자에게 System Center Configuration Manager 인증서 프로필을 배포한 후 다음 절차에 따라 인증서 프로필의 준수 상태를 모니터링할 수 있습니다.  

-   [Configuration Manager 콘솔에서 호환성 결과를 보는 방법](#BKMK_console)  

-   [보고서를 사용하여 호환성 결과를 보는 방법](#BKMK_Reports)  

##  <a name="a-namebkmkconsolea-how-to-view-compliance-results-in-the-configuration-manager-console"></a><a name="BKMK_console"></a> Configuration Manager 콘솔에서 호환성 결과를 보는 방법  
 다음 절차를 사용하여 System Center Configuration Manager 콘솔에서 배포된 인증서 프로필의 준수에 대한 자세한 내용을 봅니다.  

> [!NOTE]  
>  SCEP 인증서 호환성을 모니터링하려면 Configuration Manager 콘솔을 사용하지 말고 [How to View Compliance Results by Using Reports](#BKMK_Reports)에 설명된 대로 보고서를 사용하세요. 특히 **회사 리소스 액세스**보고서 노드에 있는 다음과 같은 인증서 보고서를 사용하세요.  
>   
>  -   인증서 발급 기록  
> -   만료 날짜에 가까운 인증서와 자산 목록  
> -   인증서 발급 상태별 자산 목록  

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 호환성 결과를 보려면  

1.  System Center Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **배포**를 클릭합니다.  

3.  **배포** 목록에서 호환성 정보를 검토할 인증서 프로필 배포를 선택합니다.  

4.  기본 페이지에서 인증서 프로필의 호환성에 대한 요약 정보를 검토할 수 있습니다. 더 자세한 정보를 보려면 인증서 프로필을 선택한 후 **홈** 탭의 **배포** 그룹에서 **상태 보기** 를 클릭하여 **배포 상태** 페이지를 엽니다.  

     **배포 상태** 페이지에는 다음 탭이 있습니다.  

    -   **호환성**: 영향받는 자산 수에 따라 인증서 프로필의 호환성을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 인증서 프로필과 호환되는 모든 사용자가 포함됩니다. **자산 정보** 창에도 이 프로필과 호환되는 사용자가 표시됩니다. 목록에서 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

        > [!IMPORTANT]  
        >  인증서 프로필이 클라이언트 장치에 적용되지 않는 경우에는 평가되지 않습니다. 그러나 해당 프로필은 호환 상태로 반환됩니다.  

    -   **오류**: 영향받는 자산 수에 따라 선택한 인증서 프로필 배포에 대한 모든 오류 목록을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 이 프로필과 관련하여 오류가 발생한 모든 사용자가 포함됩니다. 사용자를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

    -   **비준수**: 영향받는 자산 수에 따라 인증서 프로필 내에 있는 모든 비준수 규칙 목록을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 이 프로필과 호환되지 않는 모든 사용자가 포함됩니다. 사용자를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

    -   **알 수 없음**: 선택한 인증서 프로필 배포의 호환성과 장치의 현재 클라이언트 상태를 보고하지 않은 모든 사용자 목록을 표시합니다.  

5.  **배포 상태** 페이지에서 배포된 인증서 프로필의 호환성에 대한 자세한 정보를 검토할 수 있습니다. 이 정보를 나중에 빠르게 다시 찾을 수 있도록 임시 노드가 **배포** 노드 아래에 만들어집니다.  

     인증서의 등록 상태가 숫자로 표시됩니다. 다음 표를 사용하면 각 숫자의 의미를 이해할 수 있습니다.  

    |등록 상태|설명|  
    |-----------------------|-----------------|  
    |0x00000001|등록에 성공했으며 인증서가 발급되었습니다.|  
    |0x00000002|요청이 제출되었는데 등록이 보류 중이거나 요청이 대역 외에서 발급되었습니다.|  
    |0x00000004|등록이 지연되고 있습니다.|  
    |0x00000010|오류가 발생했습니다.|  
    |0x00000020|등록 상태를 알 수 없습니다.|  
    |0x00000040|상태 정보를 건너뛰었습니다. 이러한 현상은 "http://msdn.microsoft.com/ko-kr/windows/ms721572" \l "_security_certification_authority_gly" 인증 기관이 유효하지 않거나 모니터링용으로 선택되지 않은 경우 발생할 수 있습니다.|  
    |0x00000100|등록이 거부되었습니다.|  

##  <a name="a-namebkmkreportsa-how-to-view-compliance-results-by-using-reports"></a><a name="BKMK_Reports"></a> 보고서를 사용하여 호환성 결과를 보는 방법

 System Center Configuration Manager의 준수 설정에는 인증서 프로필에 대한 정보를 모니터링하는 데 사용할 수 있는 기본 제공 보고서가 포함됩니다. 이러한 보고서에는 **호환 및 설정 관리**라는 보고서 범주가 있습니다.  

> [!IMPORTANT]  
>  호환성 설정 보고서에서 **장치 필터** 및 **사용자 필터** 매개 변수를 사용할 경우 와일드카드(%) 문자를 사용해야 합니다.  

 System Center Configuration Manager에서 보고를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../core/servers/manage/reporting.md)를 참조하세요.  



<!--HONumber=Nov16_HO1-->


