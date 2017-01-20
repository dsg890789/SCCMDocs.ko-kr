---
title: "메일, Wi-Fi 및 VPN 프로필 모니터링 | Microsoft 문서"
description: "System Center Configuration Manager에서 메일, Wi-Fi 및 VPN 프로필의 준수 상태를 모니터링하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2315b8b-98bc-40e1-8ef9-bfb5e69ab109
caps.latest.revision: 4
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 73d941633d270cf9628f8be14e1e56f3c78624b6


---

# <a name="monitor-email-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 메일, Wi-Fi 및 VPN 프로필 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 메일, Wi-Fi 또는 VPN 프로필을 계층 구조 내 사용자에게 배포한 후 다음 절차에 따라 프로필의 준수 상태를 모니터링할 수 있습니다.  

-   [Configuration Manager 콘솔에서 호환성 결과를 보는 방법](#BKMK_console)  

-   [보고서를 사용하여 호환성 결과를 보는 방법](#BKMK_Reports)  

##  <a name="a-namebkmkconsolea-how-to-view-compliance-results-in-the-configuration-manager-console"></a><a name="BKMK_console"></a> Configuration Manager 콘솔에서 호환성 결과를 보는 방법  
 다음 절차를 사용하여 System Center Configuration Manager 콘솔에서 배포된 프로필의 준수에 대한 자세한 내용을 봅니다.  

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 호환성 결과를 보려면  

1.  System Center Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **배포**를 클릭합니다.  

3.  **배포** 목록에서 준수 정보를 검토할 프로필 배포를 선택합니다.  

4.  기본 페이지에서 프로필 배포의 준수에 대한 요약 정보를 검토할 수 있습니다. 더 자세한 정보를 보려면 프로필 배포를 선택한 다음 **홈** 탭의 **배포** 그룹에서 **상태 보기**를 클릭하여 **배포 상태** 페이지를 엽니다.  

     **배포 상태** 페이지에는 다음 탭이 있습니다.  

    -   **규격:** 영향받는 자산 수에 따라 프로필의 준수를 표시합니다. 규칙을 두 번 클릭하여 **자산 및 호환성** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 그러면 이 프로필과 호환되는 모든 사용자가 해당 노드에 포함됩니다. **자산 정보** 창에 프로필과 호환되는 사용자가 표시됩니다. 목록에서 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

        > [!IMPORTANT]  
        >  프로필이 클라이언트 장치에 적용되지 않는 경우에는 해당 프로필이 평가되지 않지만, 호환 상태로 반환됩니다.  

    -   **오류:** 영향받는 자산 수에 따라 선택한 프로필 배포의 모든 오류 목록을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 호환성** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 그러면 이 프로필에 대해 오류를 생성한 모든 사용자가 해당 노드에 포함됩니다. 사용자를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

    -   **비규격:** 영향받는 자산 수에 따라 프로필 내에 있는 모든 비규격 규칙의 목록을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 호환성** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 이 프로필과 호환되지 않는 모든 사용자가 포함됩니다. 사용자를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

    -   **알 수 없음:** 선택한 프로필 배포의 준수를 보고하지 않은 모든 사용자의 목록을 장치의 현재 클라이언트 상태와 함께 표시합니다.  

5.  **배포 상태** 페이지에서 배포된 프로필의 준수에 대한 자세한 정보를 검토할 수 있습니다. 이 정보를 나중에 빠르게 다시 찾을 수 있도록 임시 노드가 **배포** 노드 아래에 만들어집니다.  

##  <a name="a-namebkmkreportsa-how-to-view-compliance-results-by-using-reports"></a><a name="BKMK_Reports"></a> 보고서를 사용하여 호환성 결과를 보는 방법  
 준수 설정에는 System Center Configuration Manager의 프로필을 비롯하여 프로필 관련 정보를 모니터링할 수 있는 기본 제공 보고서도 많이 포함되어 있습니다. 이러한 보고서에는 **호환 및 설정 관리**라는 보고서 범주가 있습니다.  

> [!IMPORTANT]  
>  호환성 설정 보고서에서 **장치 필터** 및 **사용자 필터** 매개 변수를 사용할 때 와일드카드(%) 문자를 사용해야 합니다.  

 System Center Configuration Manager에서 보고를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../core/servers/manage/reporting.md)를 참조하세요.  



<!--HONumber=Dec16_HO3-->


