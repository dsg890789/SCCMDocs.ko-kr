---
title: "Endpoint Protection 경고 구성 | Microsoft 문서"
description: "Microsoft System Center 2012 Configuration Manager에서 Endpoint Protection 경고를 구성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 7ade196766d036f5dbca2b39efad380c7895847c


---

#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection에 대한 경고를 구성하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

 Microsoft System Center Configuration Manager에서 Endpoint Protection 경고를 구성하여 계층 구조에 맬웨어 감염 등 특정 이벤트가 발생하는 경우 관리자에게 알릴 수 있습니다. **모니터링** 작업 영역의 **경고** 노드에 있는 Configuration Manager 콘솔의 Endpoint Protection 대시보드에 알림이 표시되거나 지정된 사용자에게 메일을 보낼 수 있습니다.

 이 항목에서 다음 단계와 보완 절차를 사용하여 Configuration Manager에서 Endpoint Protection에 대한 경고를 구성합니다.

> [!IMPORTANT]
>  Endpoint Protection 경고를 구성하려면 컬렉션에 대한 **보안 적용** 권한이 있어야 합니다.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection에 대한 경고를 구성하는 단계

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.

2.  **자산 및 호환성** 작업 영역에서 **장치 컬렉션**을 클릭합니다.

3.  **장치 컬렉션** 목록에서 경고를 구성할 컬렉션을 선택하고 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.

    > [!NOTE]
    >  사용자 컬렉션에 대해서는 경고를 구성할 수 없습니다.

4.  Configuration Manager 콘솔의 **모니터링** 작업 영역에서 이 컬렉션에 대한 맬웨어 방지 작업 정보를 보려는 경우 *<컬렉션 이름\>***속성** 대화 상자의 **경고** 탭에서 **Endpoint Protection 대시보드에서 이 컬렉션 보기**를 선택합니다.

    > [!NOTE]
    >  이 옵션은 **모든 시스템** 컬렉션에 사용할 수 없습니다.

5.  *<컬렉션 이름\>***속성** 대화 상자의 **경고** 탭에서 **추가**를 클릭합니다.

6.  **새 컬렉션 경고 추가** 대화 상자의 **이러한 조건이 적용되는 경우 경고 생성** 섹션에서 지정된 Endpoint Protection 이벤트가 발생할 때 Configuration Manager에서 생성하려는 경고를 선택하고 **확인**을 클릭합니다.

7.  **경고** 탭의 **조건** 목록에서 각 Endpoint Protection 경고를 선택하고 다음 정보를 지정합니다.

    -   **경고 이름** – 경고에 기본 이름을 적용하거나 새 이름을 입력합니다.

    -   **경고 심각도** - 목록에서 Configuration Manager 콘솔에 표시할 경고 수준을 선택합니다.

8.  선택한 경고에 따라 다음과 같은 추가 정보를 지정합니다.

    -   **맬웨어 검색** - 이 경고는 모니터링하는 컬렉션의 컴퓨터에서 맬웨어가 검색될 경우 생성됩니다. **맬웨어 검색 임계값** - 이 경고가 생성되는 맬웨어 검색 수준을 지정합니다.

        -   **높음 - 모든 검색** - Endpoint Protection 클라이언트에서 수행하는 작업에 관계없이 지정된 컬렉션에 맬웨어가 검색된 컴퓨터가 하나 이상 있으면 경고가 생성됩니다.

        -   **중간 - 검색됨, 대기 중인 작업** - 지정된 컬렉션에 맬웨어가 검색된 컴퓨터가 하나 이상 있고 맬웨어를 수동으로 제거해야 하면 경고가 생성됩니다.

        -   **낮음 - 검색됨, 활성** - 지정된 컬렉션에 맬웨어가 검색되었으며 여전히 활성 상태인 컴퓨터가 하나 이상 있으면 경고가 생성됩니다.

    -   **맬웨어 발생** - 이 경고는 모니터링하는 컬렉션에서 지정된 맬웨어가 검색된 컴퓨터가 지정된 백분율을 초과할 경우 생성됩니다.

        -   **맬웨어가 검색된 컴퓨터 백분율** - 컬렉션에서 검색된 맬웨어가 있는 컴퓨터의 백분율이 지정한 백분율을 초과하면 경고가 생성됩니다. **1** 에서 **99**사이의 백분율을 지정합니다.

            > [!NOTE]
            >  백분율 값은 컬렉션에 있는 컴퓨터 수를 기반으로 하지만 Configuration Manager 클라이언트가 설치되지 않은 컴퓨터는 제외됩니다. 아직 Endpoint Protection 클라이언트가 설치되지 않은 컴퓨터를 포함합니다.

    -   **반복적인 맬웨어 검색** - 이 경고는 모니터링하는 컬렉션의 컴퓨터에서 지정된 시간 동안 특정 맬웨어가 검색된 횟수가 지정된 횟수를 초과할 경우 생성됩니다. 이 경고를 구성하려면 다음 정보를 지정합니다.

        -   **맬웨어가 검색된 횟수:** 컬렉션의 컴퓨터에서 동일한 맬웨어가 검색된 횟수가 지정된 횟수를 초과하면 경고가 생성됩니다. **2** 에서 **32**사이의 숫자를 지정합니다.

        -   **검색 간격(시간):** 맬웨어 검색 횟수가 발생해야 하는 검색 간격(시간)을 지정합니다. **1** 에서 **168**사이의 숫자를 지정합니다.

    -   **여러 맬웨어 검색** - 이 경고는 모니터링하는 컬렉션의 컴퓨터에서 지정된 시간 동안 검색된 맬웨어 유형 수가 지정된 개수를 초과할 경우 생성됩니다. 이 경고를 구성하려면 다음 정보를 지정합니다.

        -   **검색된 맬웨어 유형 수:** 컬렉션의 컴퓨터에서 지정된 개수의 맬웨어 유형이 검색되면 경고가 생성됩니다. **2** 에서 **32**사이의 숫자를 지정합니다.

        -   **검색 간격(시간):** 맬웨어 검색 횟수가 발생해야 하는 검색 간격(시간)을 지정합니다. **1** 에서 **168**사이의 숫자를 지정합니다.

9. **확인**을 클릭하여 *<컬렉션 이름\>***속성** 대화 상자를 닫습니다.  

> [!div class="button"]
[다음 단계 >](endpoint-definition-updates.md)

> [!div class="button"]
[뒤로 >](endpoint-protection-site-role.md)



<!--HONumber=Dec16_HO3-->


