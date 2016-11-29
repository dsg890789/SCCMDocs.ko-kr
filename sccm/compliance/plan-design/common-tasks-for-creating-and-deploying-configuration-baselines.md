---
title: "System Center Configuration Manager에서 구성 기준을 만들고 배포하기 위한 일반 작업 | System Center Configuration Manager"
description: "System Center Configuration Manager 구성 기준을 만들고 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4bb6afeb-d267-4f9b-ade2-26e5400c223b
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 0d66240408dcd65576954ffb27395d3f05f5a41e


---
# <a name="common-tasks-for-creating-and-deploying-configuration-baselines-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 구성 기준을 만들고 배포하기 위한 일반 작업

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager 구성 기준을 만들고 배포하는 방법을 배울 수 있는 일반 시나리오가 있습니다.  

 준수 설정에 이미 익숙한 경우 사용할 수 있는 모든 기능에 대한 자세한 설명은 [Create configuration baselines](../../compliance/deploy-use/create-configuration-baselines.md)(구성 기준 만들기) 및 [Deploy configuration baselines](../../compliance/deploy-use/deploy-configuration-baselines.md)(구성 기준 배포) 항목을 참조하세요.  

 시작하기 전에 [System Center Configuration Manager에서 준수 설정 시작](../../compliance/get-started/get-started-with-compliance-settings.md)을 읽어 준수 설정에 대한 일부 기본 지식을 익히고 [준수 설정 계획 및 구성](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)을 읽어 필수 전제 조건을 구현합니다.  

## <a name="create-a-configuration-baseline"></a>구성 기준 만들기  
 이 예제에서는 Configuration Manager 클라이언트를 실행하는 Windows 10 PC 전용 구성 항목을 만들었습니다.  

 이 구성 항목은 Windows 10 PC에서 6자 이상의 필수 암호를 적용합니다. 구성 항목의 이름은 **Windows 10 암호 적용**입니다.  

다음 절차에서는 배포에 대해 준비되도록 이 구성 항목을 구성 기준에 추가하는 방법을 알아봅니다.  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **구성 기준 만들기**를 클릭합니다.  

4.  **구성 기준 만들기** 대화 상자에서 다음을 구성합니다.  

    -   **이름** - **Windows 10 암호** (또는 원하는 다른 이름)를 입력합니다.  

5.  **추가** > **구성 항목**입니다.  

6.  **구성 항목 추가** 대화 상자에서 이전에 만든 **Windows 10 암호 적용** 구성 항목을 선택한 다음 **추가**를 클릭합니다.  

7.  확인을 클릭하여 **구성 항목 추가** 대화 상자를 닫고 이 스크린샷과 유사하게 표시되어야 하는 **구성 기준 만들기** 대화 상자로 돌아갑니다.  

     ![구성 기준 만들기 대화 상자](/sccm/compliance/plan-design/media/Create-Configuration-Baseline.png)  

8.  **확인** 을 클릭하여 **구성 기준 만들기** 대화 상자를 닫습니다.  

 이제 Configuration Manager 콘솔의 **구성 기준** 노드에서 방금 만든 구성 기준을 볼 수 있습니다.  

## <a name="deploy-the-configuration-baseline"></a>구성 기준 배포  
 이 예제에서는 이전 절차에서 만든 구성 기준을 컴퓨터의 컬렉션에 배포합니다.  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**을 클릭합니다.  

3.  구성 기준 목록에서 **Windows 10 암호**를 선택합니다.  

4.  **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

5.  **구성 기준 배포** 대화 상자에서 다음을 구성합니다.  

    -   **선택한 구성 기준** - **Windows 10 암호** 구성 기준이 이 목록에 자동으로 추가되었는지 확인합니다.  

    -   **지원되는 경우 비규격 규칙 재구성** - 대상 장치에 올바른 설정이 없을 때 해당 설정이 Configuration Manager에서 재구성되게 하려면 이 상자를 선택합니다.  

    -   **컬렉션** - 준수 여부에 대해 구성 기준을 평가하고 재구성할 컴퓨터의 컬렉션을 선택하려면 **찾아보기** 를 클릭합니다. 이 예제에서는 구성 기준이 기본 제공 **모든 데스크톱 및 서버 클라이언트** 컬렉션에 배포되었습니다.  

        > [!TIP]  
        >  선택하는 컬렉션에 Windows 10을 실행하지 않는 컴퓨터 또는 장치가 포함되어 있어도 걱정할 필요가 없습니다. 만든 구성 항목에서 지원되는 플랫폼을 구성했다면 Windows 10 PC만 준수 여부를 검사합니다.  

    -   필요한 경우 구성 기준을 평가하는 일정을 구성합니다. 그렇지 않은 경우 기본값인 **7일**을 그대로 둡니다.  

6.  이제 대화 상자가 다음과 같이 표시됩니다.  

     ![구성 기준 배포 대화 상자](/sccm/compliance/plan-design/media/Deploy-configuration-baselines.png)  

7.  **확인** 을 클릭하여 **구성 기준 배포** 대화 상자를 만들고 배포를 만듭니다.  

 이 배포에 대한 준수 통계를 간단히 살펴보려면 **모니터링** 작업 영역에서 **배포**를 클릭합니다. 화면 맨 아래에 **준수 통계** 차트가 표시됩니다.  

 구성 기준을 모니터링하는 방법에 대한 자세한 내용은 [Monitor compliance settings](../../compliance/deploy-use/monitor-compliance-settings.md)(준수 설정 모니터링)를 참조하세요.  



<!--HONumber=Nov16_HO1-->


