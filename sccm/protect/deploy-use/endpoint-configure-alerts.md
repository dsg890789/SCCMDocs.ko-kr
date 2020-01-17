---
title: Endpoint Protection 경고 구성
titleSuffix: Configuration Manager
description: Endpoint Protection 경고를 Configuration Manager에서 구성하는 방법을 알아봅니다.
ms.date: 03/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: f504de3e-4caf-455c-80d7-a63f13f4c5d9
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 55877923ae2e9a7aa47b3ebe774f7dc0e4ea21a4
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75820052"
---
#  <a name="configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection에 대한 경고를 구성하는 방법

*적용 대상: Configuration Manager(현재 분기)*

 Microsoft Configuration Manager에서 Endpoint Protection 경고를 구성하여 계층 구조에 맬웨어 감염 등 특정 이벤트가 발생하는 경우 관리자에게 알릴 수 있습니다. **모니터링** 작업 영역의 **경고** 노드에 있는 Configuration Manager 콘솔의 Endpoint Protection 대시보드에 알림이 표시되거나 지정된 사용자에게 메일을 보낼 수 있습니다.

 이 항목에서 다음 단계와 보완 절차를 사용하여 Configuration Manager에서 Endpoint Protection에 대한 경고를 구성합니다.

> [!IMPORTANT]
>  Endpoint Protection 경고를 구성하려면 컬렉션에 대한 **보안 적용** 권한이 있어야 합니다.

## <a name="steps-to-configure-alerts-for-endpoint-protection-in-configuration-manager"></a>Configuration Manager에서 Endpoint Protection에 대한 경고를 구성하는 단계

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.

2.  **자산 및 호환성** 작업 영역에서 **디바이스 컬렉션**을 클릭합니다.

3.  **디바이스 컬렉션** 목록에서 경고를 구성할 컬렉션을 선택하고 **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.

    > [!NOTE]
    >  사용자 컬렉션에 대해서는 경고를 구성할 수 없습니다.

4.  Configuration Manager 콘솔의 **모니터링** 작업 영역에서 이 컬렉션에 대한 맬웨어 방지 작업 정보를 보려는 경우 _<컬렉션 이름\>_ **속성** 대화 상자의 **경고** 탭에서 **Endpoint Protection 대시보드에서 이 컬렉션 보기**를 선택합니다.

    > [!NOTE]
    >  이 옵션은 **모든 시스템** 컬렉션에 사용할 수 없습니다.

5.  _<컬렉션 이름\>_ **속성** 대화 상자의 **경고** 탭에서 **추가**를 클릭합니다.

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

9. **확인**을 클릭하여 _<컬렉션 이름\>_ **속성** 대화 상자를 닫습니다.  

## <a name="alert-for-outdated-malware-client"></a>오래된 맬웨어 클라이언트에 대한 경고

Configuration Manager 버전 1702부터 Endpoint Protection 클라이언트가 오래되지 않았는지 확인하도록 경고를 구성할 수 있습니다. 디바이스 컬렉션에서 이제 특성 **맬웨어 방지 클라이언트 버전** 및 **Endpoint Protection 배포 상태**의 목록에 열을 추가할 수 있습니다. 예를 들어, 콘솔에서 **자산 및 준수** > **개요** > **디바이스 컬렉션** > **모든 데스크톱 및 서버 클라이언트**로 이동합니다. 열 머리글을 마우스 오른쪽 단추로 클릭하고 추가할 열을 선택합니다. 경고를 확인하려면 **모니터링** 작업 영역에서 **경고**를 봅니다. 만료된 버전의 맬웨어 방지 소프트웨어를 실행하는 관리되는 클라이언트가 20%를 초과할 경우 [맬웨어 방지 클라이언트 버전이 오래되었습니다.] 경고가 표시됩니다. 이 경고는 **모니터링** > **개요** 탭에 표시되지 않습니다. 만료된 맬웨어 방지 클라이언트를 업데이트하려면 맬웨어 방지 클라이언트에 대한 소프트웨어 업데이트를 사용하도록 설정합니다.

경고가 생성되는 백분율을 구성하려면 **모니터링** > **경고** > **모든 경고**를 확장하고 **맬웨어 방지 클라이언트가 오래됨**을 두 번 클릭한 다음 **오래된 버전의 맬웨어 방지 클라이언트로 관리되는 클라이언트의 비율이 다음 이상인 경우 경고 생성** 옵션을 수정합니다.

> [!div class="button"]
> [다음 단계 >](endpoint-definition-updates.md)
> 
> [!div class="button"]
> [뒤로 >](endpoint-protection-site-role.md)
