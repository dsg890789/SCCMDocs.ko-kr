---
title: "App-V 가상 환경 만들기 | System Center Configuration Manager"
description: "앱이 데이터를 서로 공유할 수 있도록 Microsoft Application Virtualization을 사용하여 가상 환경을 만듭니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b6b86078-fcc4-46cf-87d6-4b52b914b712
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 625ea93d855089f6dbbdcc8368032e61b8a1ba0b


---
# <a name="create-app-v-virtual-environments-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 App-V 가상 환경 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Microsoft Application Virtualization(App-V) 가상 환경에서는 배포된 가상 응용 프로그램이 클라이언트 Windows PC에 있는 동일한 파일 시스템과 레지스트리를 공유할 수 있습니다. 즉, 일반 가상 응용 프로그램과 달리 이러한 응용 프로그램은 서로 데이터를 공유할 수 있습니다. 응용 프로그램이 설치되거나 클라이언트에서 다음번에 설치된 응용 프로그램을 평가할 때 클라이언트 PC에서 가상 환경이 만들어지거나 수정됩니다. 여러 응용 프로그램이 파일시스템 또는 레지스트리 값을 수정하려는 경우 우선 순위가 가장 높은 응용 프로그램이 우선권을 가질 수 있도록 이러한 응용 프로그램의 순서를 지정할 수 있습니다.  

> [!IMPORTANT]  
>  App-V 가상 환경을 사용하여 예를 들어 맬웨어로부터의 보안 보호를 제공해서는 안 됩니다.  

 Configuration Manager에서 App-V 가상 환경을 만들려면 다음 절차를 따르세요.  

## <a name="create-an-app-v-virtual-environment"></a>App-V 가상 환경 만들기  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **App-V 가상 환경**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **가상 환경 만들기**를 클릭합니다.  

4.  **가상 환경 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름** - 가상 환경의 고유한 이름을 최대 128자로 지정합니다.  

    -   **설명** - 선택적으로 가상 환경에 대한 설명을 지정합니다.  

5.  **추가** 를 클릭하여 새 배포 유형을 가상 환경에 추가합니다. 하나 이상의 배포 유형을 추가해야 합니다.  

6.  **응용 프로그램 추가** 대화 상자에서 가상 환경에 추가할 이 응용 프로그램 그룹을 참조하는 데 사용할 **그룹 이름** 을 최대 128자로 지정합니다.  

7.  **추가**를 클릭하고 그룹에 추가할 App-V 5 응용 프로그램과 배포 유형을 선택한 후에 **확인**을 클릭합니다.  

8.  **응용 프로그램 추가** 대화 상자에서 **순서 높이기** 또는 **순서 낮추기** 를 클릭하여, 여러 응용 프로그램이 동일한 가상 환경에서 파일 시스템 또는 레지스트리 설정을 수정할 경우에 우선 순위를 가질 응용 프로그램을 지정할 수 있습니다.  

9. **확인** 을 클릭하여 **가상 환경 만들기** 대화 상자로 돌아갑니다.  

10. 그룹 추가를 완료한 후에 **확인** 을 클릭하여 가상 환경을 만듭니다. Configuration Manager 콘솔의 **App-V 가상 환경** 노드에 새 가상 환경이 표시됩니다. **App-V 가상 환경 상태**보고서를 사용하여 가상 환경의 상태를 모니터링할 수 있습니다.  

    > [!NOTE]  
    >  응용 프로그램이 설치되거나 클라이언트에서 다음번에 설치된 응용 프로그램을 평가할 때 클라이언트 PC에서 가상 환경이 추가되거나 수정됩니다.  



<!--HONumber=Nov16_HO1-->


