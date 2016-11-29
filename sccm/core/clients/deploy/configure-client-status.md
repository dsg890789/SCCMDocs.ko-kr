---
title: "클라이언트 상태 구성 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 클라이언트 상태 설정을 선택합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a2275ba2-c83d-43e7-90ed-418963a707fe
caps.latest.revision: 6
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 98d78ff0ef641baeef1323243f8f389fa5e95057


---
# <a name="how-to-configure-client-status-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트 상태를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 클라이언트 상태를 모니터링하고 발견되는 문제를 재구성하려면 먼저 사이트를 구성하여 클라이언트를 비활성으로 표시하는 데 사용할 매개 변수를 지정하고 클라이언트 활동이 지정된 임계값 미만으로 떨어질 경우 경고하는 옵션을 구성해야 합니다. 또한 컴퓨터에서 클라이언트 상태를 통해 발견되는 문제를 자동으로 해결하지 않도록 설정할 수 있습니다.  

##  <a name="a-namebkmk1a-to-configure-client-status"></a><a name="BKMK_1"></a> 클라이언트 상태를 구성하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **클라이언트 상태**를 클릭한 다음 **홈** 탭의 **클라이언트 상태** 그룹에서 **클라이언트 상태 설정**을 클릭합니다.  

3.  **클라이언트 상태 설정 속성** 대화 상자에서 클라이언트 활동을 결정하기 위한 다음 값을 지정합니다.  

    > [!NOTE]  
    >  이러한 설정 중 아무 것도 충족되지 않으면 클라이언트가 비활성으로 표시됩니다.  

    -   **다음 기간(일) 동안의 클라이언트 정책 요청:** 클라이언트가 정책을 요청한 이후의 일 수를 지정합니다. 기본값은 **7** 일입니다.  

    -   **다음 기간(일) 동안의 하트비트 검색:** 클라이언트 컴퓨터가 사이트 데이터베이스에 하트비트 검색 레코드를 전송한 이후의 일 수를 지정합니다. 기본값은 **7** 일입니다.  

    -   **다음 기간(일) 동안의 하드웨어 인벤토리:** 클라이언트 컴퓨터가 사이트 데이터베이스에 하드웨어 인벤토리 레코드를 전송한 이후의 일 수를 지정합니다. 기본값은 **7** 일입니다.  

    -   **다음 기간(일) 동안의 소프트웨어 인벤토리:** 클라이언트 컴퓨터가 사이트 데이터베이스에 소프트웨어 인벤토리 레코드를 전송한 이후의 일 수를 지정합니다. 기본값은 **7** 일입니다.  

    -   **다음 기간(일) 동안의 상태 메시지:** 클라이언트 컴퓨터가 사이트 데이터베이스에 상태 메시지를 전송한 이후의 일 수를 지정합니다. 기본값은 **7** 일입니다.  

4.  **클라이언트 상태 설정 속성** 대화 상자에서 클라이언트 상태 기록 데이터가 유지되는 기간을 결정하기 위한 다음 값을 지정합니다.  

    -   **다음 기간(일) 동안 클라이언트 상태 기록 유지:** 사이트 데이터베이스에 클라이언트 상태 기록을 유지할 기간을 지정합니다. 기본값은 **31** 일입니다.  

5.  **확인** 을 클릭하여 속성을 저장하고 **클라이언트 상태 설정 속성** 대화 상자를 닫습니다.  

##  <a name="a-namebkmkschedulea-to-configure-the-schedule-for-client-status"></a><a name="BKMK_Schedule"></a> 클라이언트 상태에 대한 일정을 구성하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **클라이언트 상태**를 클릭한 다음 **홈** 탭의 **클라이언트 상태** 그룹에서 **클라이언트 상태 업데이트 일정**을 클릭합니다.  

3.  **클라이언트 상태 업데이트 일정** 대화 상자에서 클라이언트 상태를 업데이트할 간격을 구성하고 확인을 클릭합니다.  

    > [!NOTE]  
    >  클라이언트 상태 업데이트 일정을 변경하는 경우 이전에 구성된 일정에 따라 예약된 다음 번 클라이언트 상태 업데이트까지 업데이트가 적용되지 않습니다.  

##  <a name="a-namebkmk2a-to-configure-alerts-for-client-status"></a><a name="BKMK_2"></a> 클라이언트 상태에 대한 경고를 구성하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.  

2.  **자산 및 호환성** 작업 영역에서 **장치 컬렉션**을 클릭합니다.  

3.  **장치 컬렉션** 목록에서 경고를 구성할 컬렉션을 선택하고 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  

    > [!NOTE]  
    >  사용자 컬렉션에 대해서는 경고를 구성할 수 없습니다.  

4.  *&lt;컬렉션 이름\>***속성** 대화 상자의 **경고** 탭에서 **추가**를 클릭합니다.  

    > [!NOTE]  
    >  **경고** 탭은 연결된 보안 역할에 경고 권한이 있는 경우에만 표시됩니다.  

5.  **새 컬렉션 경고 추가** 대화 상자에서 클라이언트 상태 임계값이 특정 값 미만으로 떨어질 때 생성할 경고를 선택하고 **확인**을 클릭합니다.  

6.  **경고** 탭의 **조건** 목록에서 각 클라이언트 상태 경고를 선택하고 다음 정보를 지정합니다.  

    -   **경고 이름** – 경고에 기본 이름을 적용하거나 새 이름을 입력합니다.  

    -   **경고 심각도** – 드롭다운 목록에서 Configuration Manager 콘솔에 표시할 경고 수준을 선택합니다.  

    -   **경고 생성** – 경고의 임계값 백분율을 지정합니다.  

7.  **확인**을 클릭하여 *&lt;컬렉션 이름\>***속성** 대화 상자를 닫습니다.  

##  <a name="a-namebkmk3a-to-exclude-computers-from-automatic-remediation"></a><a name="BKMK_3"></a> 컴퓨터를 자동 문제 해결에서 제외하려면  

1.  자동 문제 해결을 사용하지 않도록 설정할 클라이언트 컴퓨터에서 레지스트리 편집기를 엽니다.  

    > [!WARNING]  
    >  레지스트리 편집기를 잘못 사용할 경우 운영 체제를 다시 설치해야 하는 심각한 문제가 발생할 수 있습니다. 레지스트리 편집기를 잘못 사용하여 발생하는 문제는 해결할 수 있다는 보장이 없습니다. 레지스트리 편집기 사용에 따른 결과는 사용자의 책임입니다.  

2.  **HKEY_LOCAL_MACHINE\Software\Microsoft\CCM\CcmEval\NotifyOnly**로 이동합니다.  

3.  이 레지스트리 키에 다음 값 중 하나를 입력합니다.  

    -   **True** – 발견되는 문제가 클라이언트 컴퓨터에서 자동으로 해결되지 않습니다. 그러나 이 클라이언트의 문제에 대한 경고가 **모니터링** 작업 영역에 표시됩니다.  

    -   **False** – 발견되는 문제가 클라이언트 컴퓨터에서 자동으로 해결되고 **모니터링** 작업 영역에 경고가 표시됩니다. 이것이 기본 설정입니다.  

4.  레지스트리 편집기를 닫습니다.  

 또한 CCMSetup **NotifyOnly** 설치 속성을 사용하여 클라이언트를 설치함으로써 자동 문제 해결에서 클라이언트를 제외할 수도 있습니다. 클라이언트 설치 속성에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  



<!--HONumber=Nov16_HO1-->


