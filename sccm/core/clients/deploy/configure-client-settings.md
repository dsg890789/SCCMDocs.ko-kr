---
title: "클라이언트 설정 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager의 클라이언트 설정을 선택합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 95e9858a-bad4-4651-9e61-2e31dc5050fa
caps.latest.revision: 5
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 9e3162e04da90748379145e37f6b378badab97d3

---
# <a name="how-to-configure-client-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

모든 클라이언트 설정은 Configuration Manager 콘솔의 **관리** 작업 영역에 있는 **클라이언트 설정** 노드의 System Center Configuration Manager에서 관리합니다. 계층에서 사용자 지정 설정이 적용되지 않은 모든 사용자 및 장치에 대한 설정을 구성하려면 기본 설정을 수정하세요. 일부 사용자 또는 장치에만 다른 설정을 적용하려면 사용자 지정 설정을 만들어 컬렉션에 배포하세요.  

> [!NOTE]  
>  또한 클라이언트를 관리할 구성 항목을 사용하여 장치의 구성 호환성을 평가, 추적 및 재구성할 수 있습니다. 자세한 내용은 [System Center Configuration Manager를 사용하여 장치 준수 확인](../../../compliance/understand/ensure-device-compliance.md)을 참조하세요.  

##  <a name="a-namebkmkdefaultclientsettingsa-how-to-configure-the-default-client-settings"></a><a name="BKMK_DefaultClientSettings"></a> 기본 클라이언트 설정을 구성하는 방법  

 계층의 모든 클라이언트에 대한 기본 클라이언트 설정을 구성하려면 다음 절차를 따르세요.  

#### <a name="to-configure-the-default-client-settings"></a>기본 클라이언트 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭한 후 **기본 클라이언트 설정**을 선택합니다.  

3.  **홈** 탭에서 **속성**을 클릭합니다.  

4.  탐색 창에서 각 설정 그룹의 클라이언트 설정을 보고 구성합니다. 각 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../core/clients/deploy/about-client-settings.md)를 참조하세요.  

5.  **확인** 을 클릭하여 **기본 클라이언트 설정** 대화 상자를 닫습니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대해 정책 검색을 시작하려면 [System Center Configuration Manager의 클라이언트 관리 방법](../../../core/clients/manage/manage-clients.md)에서 [Configuration Manager 클라이언트에 대한 정책 검색 시작](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval)을 참조하세요.  

##  <a name="a-namebkmkcustomclientsettingsa-how-to-create-and-deploy-custom-client-settings"></a><a name="BKMK_CustomClientSettings"></a> 사용자 지정 클라이언트 설정을 만들고 배포하는 방법  
 선택한 사용자 또는 장치 컬렉션의 사용자 지정 설정을 구성하고 배포하려면 다음 절차를 수행하세요. 이러한 사용자 지정 설정을 배포하면 기본 클라이언트 설정이 재정의됩니다.  

> [!NOTE]  
>  이 절차를 시작하기 전에 이러한 사용자 지정 클라이언트 설정이 필요한 사용자 또는 장치가 포함된 컬렉션이 있는지 확인하세요.  

#### <a name="to-configure-and-deploy-custom-client-settings"></a>사용자 지정 클라이언트 설정을 구성하고 배포하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **사용자 지정 클라이언트 설정 만들기**를 클릭한 다음 사용자 지정 클라이언트 설정을 만들려는 대상이 장치인지 또는 사용자인지에 따라 다음 옵션 중 하나를 클릭합니다.  

    -   **사용자 지정 클라이언트 장치 설정 만들기**  

    -   **사용자 지정 클라이언트 사용자 설정 만들기**  

4.  **사용자 지정 장치 설정 만들기** 또는 **사용자 지정 사용자 설정 만들기** 대화 상자에서 사용자 지정 설정의 고유 이름과 설명(옵션)을 지정합니다.  

5.  설정 그룹을 표시하는 사용 가능한 확인란 중 하나 이상을 선택합니다.  

6.  탐색 창에서 첫 번째 그룹 설정을 클릭한 다음 사용 가능한 사용자 지정 설정을 보고 구성합니다. 나머지 그룹 설정에 대해서도 이 프로세스를 반복합니다. 각 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설정 정보](../../../core/clients/deploy/about-client-settings.md)를 참조하세요.  

7.  **확인** 을 클릭하여 **사용자 지정 장치 설정 만들기** 또는 **사용자 지정 사용자 설정 만들기** 대화 상자를 닫습니다.  

8.  방금 만든 사용자 지정 클라이언트 설정을 선택합니다. **홈** 탭의 **클라이언트 설정** 그룹에서 **배포**를 클릭합니다.  

9. **컬렉션 선택** 대화 상자에서 사용자 지정 설정으로 구성할 장치 또는 사용자가 포함된 컬렉션을 선택한 다음 **확인**을 클릭합니다. 세부 정보 창에서 **배포** 탭을 클릭하면 선택한 컬렉션을 확인할 수 있습니다.  

10. 방금 만든 사용자 지정 클라이언트 설정 순서를 봅니다. 사용자 지정 클라이언트 설정이 여러 개인 경우 해당 순서 번호에 따라 적용됩니다. 충돌이 있는 경우 순서 번호가 가장 낮은 설정이 다른 설정을 재정의합니다. 순서를 변경하려면 **홈** 탭의 **클라이언트 설정** 그룹에서 **위로 항목 이동** 또는 **아래로 항목 이동**을 클릭합니다.  

 클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대해 정책 검색을 시작하려면 [System Center Configuration Manager의 클라이언트 관리 방법](../../../core/clients/manage/manage-clients.md)에서 [Configuration Manager 클라이언트에 대한 정책 검색 시작](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval)을 참조하세요.  

##  <a name="a-namebkmkresultantclientsettingsa-how-to-view-resultant-client-settings"></a><a name="BKMK_ResultantClientSettings"></a> 결과 클라이언트 설정을 확인하는 방법  
 같은 장치, 사용자 또는 사용자 그룹에 여러 클라이언트 설정을 배포한 경우 설정의 우선 순위 및 조합이 복잡할 수 있습니다. 계산된 결과 클라이언트 설정을 보려면 다음 절차를 수행하세요.  

#### <a name="to-view-the-resultant-client-settings"></a>결과 클라이언트 설정을 보려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 호환성** 작업 영역에서 **장치**, **사용자**또는 **사용자 컬렉션**을 클릭합니다.  

3.  장치, 사용자 또는 사용자 그룹을 선택하고 **클라이언트 설정** 그룹에서 **결과 클라이언트 설정**을 선택합니다.  또는 장치, 사용자 또는 사용자 그룹을 마우스 오른쪽 단추로 클릭하고 **클라이언트 설정**과 **결과 클라이언트 설정**을 차례로 선택할 수 있습니다.  

4.  왼쪽 창에서 클라이언트 설정을 선택하면 결과 설정이 표시됩니다.  

    > [!NOTE]  
    >  결과 클라이언트 설정을 보려면 로그온한 사용자에게 [클라이언트 설정]에 대한 읽기 액세스 권한이 있어야 합니다.  

    > [!NOTE]  
    >  표시되는 결과 설정은 읽기 전용입니다. 설정을 수정하려면 위의 절차를 수행하세요.  



<!--HONumber=Nov16_HO1-->


