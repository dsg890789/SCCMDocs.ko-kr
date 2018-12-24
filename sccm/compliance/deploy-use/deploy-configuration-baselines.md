---
title: 구성 기준 배포
titleSuffix: Configuration Manager
description: 구성 기준을 배포하여 구성 기준 배포를 정의하고 배포에서 구성 기준을 추가하거나 제거합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: c55382bf1fc377fd7e86f433a0cb92a5240eafa1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32334711"
---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 구성 기준을 배포하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

해당 컬렉션의 클라이언트 디바이스가 구성 기준의 규격 준수 여부를 평가하려면 System Center Configuration Manager의 구성 기준이 하나 이상의 사용자 또는 디바이스 컬렉션에 배포되어야 합니다.  

**구성 기준 배포** 대화 상자를 사용하여 구성 기준 배포를 정의합니다. 여기에는 평가 일정 지정 외에도 배포에서 구성 기준 추가 또는 제거가 포함됩니다.  

## <a name="deploy-a-configuration-baseline"></a>구성 기준 배포  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**을 클릭합니다.  

3.  **구성 기준** 목록에서 배포하려는 구성 기준을 선택한 다음 **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

4.  **구성 기준 배포** 대화 상자의 **사용 가능한 구성 기준** 목록에서 배포하려는 구성 기준을 선택합니다. **추가** 를 클릭하여 **선택한 구성 기준** 목록에 선택한 구성 기준을 추가합니다.  

    > [!IMPORTANT]  
    >  배포된 구성 기준에 추가된 구성 항목을 변경하는 경우 수정된 구성 항목은 다음에 예정된 평가 시간까지 준수 여부가 평가되지 않습니다.  

5.  다음과 같은 추가 정보를 지정합니다.  

    -   **지원되는 경우 비규격 규칙 재구성** – Configuration Manager에서 등록된 모바일 장치의 레지스트리, 스크립트 및 모든 설정, WMI(Windows Management Instrumentation)에 대해 규격을 준수하지 않는 규칙을 자동으로 수정합니다.  

    -   **유지 관리 기간을 벗어나도 수정 허용** - 구성 기준을 배포할 컬렉션에 대해 유지 관리 기간이 구성된 경우 유지 관리 기간 외의 기간에 준수 설정이 값을 수정할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다. 유지 관리 기간에 대한 자세한 내용은 [유지 관리 기간을 사용하는 방법](/sccm/core/clients/manage/collections/use-maintenance-windows)을 참조하세요.  

6.  **경고 생성** - 지정된 날짜 및 시간을 기준으로 구성 기준 준수가 지정된 비율에 못 미치는 경우에 생성되는 경고를 구성합니다. 경고를 System Center Operations Manager로 전송할지 여부도 지정할 수 있습니다.  

7.  **컬렉션** – **찾아보기** 를 클릭하여 구성 기준을 배포할 컬렉션을 선택합니다.  

8.  **이 구성 기준에 대한 준수 여부 평가 일정 지정** 클라이언트 컴퓨터에서 배포된 구성 기준을 평가할 일정을 지정합니다. 단순 일정 또는 사용자 지정 일정 중에서 지정할 수 있습니다.  

    > [!NOTE]  
    >  구성 기준이 컴퓨터에 배포되면 예약한 시작 시간의 2시간 이내에 준수 여부가 평가됩니다. 사용자에게 배포된 경우 사용자가 로그온할 때 준수 여부가 평가됩니다.  

9. **확인** 을 클릭하여 **구성 기준 배포** 대화 상자를 닫고 배포를 만듭니다. 배포를 모니터링하는 방법에 대한 자세한 내용은 [Monitor compliance settings](/sccm/compliance/deploy-use/monitor-compliance-settings)(준수 설정 모니터링)를 참조하세요.  
