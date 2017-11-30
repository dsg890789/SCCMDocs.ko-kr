---
title: "비준수에 대한 작업"
titleSuffix: Configuration Manager
description: "Configuration Manager를 준수하지 않는 작업을 설정하는 방법을 알아봅니다."
ms.custom: na
ms.date: 11/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
caps.latest.revision: "18"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 1dd10d9452fae85f2ecc3d3077fba420454ef337
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="set-up-actions-for-non-compliance"></a>비준수에 대한 작업 설정

**비준수에 대한 작업**을 사용하면 준수하지 않는 장치에 적용되는 작업의 시간 순서를 구성할 수 있습니다. 예를 들어 비준수 장치의 최종 사용자에게 전자 메일을 보내거나 해당 장치를 비준수 장치로 표시할 수 있습니다.

## <a name="before-you-begin"></a>시작하기 전에

> [!IMPORTANT]
> 비준수에 대한 작업을 설정하려면 하나 이상의 장치 준수 정책을 작성해야 합니다.

지원되는 비준수에 대한 작업은 다음과 같습니다.

- 최종 사용자에게 전자 메일 보내기
- 비준수 장치 표시

### <a name="send-e-mail-to-end-user"></a>최종 사용자에게 전자 메일 보내기

미리 만든 기본 전자 메일 템플릿에서 선택하거나 완전히 사용자 지정된 전자 메일 알림을 만들 수 있습니다. Configuration Manager는 회사 로고, 연락처 정보 및 추가 받는 사람을 포함하여 사용자 지정된 제목, 메시지 본문을 제공합니다.

### <a name="mark-devices-non-compliant"></a>비준수 장치 표시

장치에서 회사 리소스에 액세스하지 못하도록 차단해야 하는 기간(일) 일정을 결정할 수 있습니다. 이는 즉시 지정할 수 있지만 사용자가 장치 준수 정책을 준수할 때까지 기다리는 유예 기간을 제공할 수도 있습니다.

### <a name="supported-platforms"></a>지원되는 플랫폼

[Intune을 통해 관리되는 모든 플랫폼](https://docs.microsoft.com/intune/supported-devices-browsers)에서 지원됩니다.

## <a name="to-add-an-email-template"></a>전자 메일 템플릿 추가

Configuration Manager에서 전자 메일 템플릿을 제공하지만 직접 만들 수도 있습니다. 전자 메일 템플릿은 나중에 사용자와 통신하기 위해 비준수에 대한 작업을 만드는 과정에서 사용됩니다.

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.

2. **자산 및 준수** 작업 영역에서 **준수 설정**을 펼친 다음 **준수 알림 템플릿**을 선택합니다.

3. **홈** 탭의 **준수 알림 템플릿 만들기**에서

4. 다음 정보를 입력해야 합니다. a. 이름: 전자 메일 템플릿의 이름입니다.
    b. 보낸 사람: 전자 메일 알림을 보내는 전자 메일 주소입니다.
    c. 제목: 보내는 전자 메일 알림을 설명하는 제목입니다.
    d. 메시지 본문: 전자 메일 알림에 포함된 자세한 내용입니다.

    > [!TIP] 
    > 회사 로고가 포함된 **전자 메일 머리글** 및 회사 이름과 연락처 정보가 포함될 수 있는 전자 메일 바닥글도 포함할 수 있습니다. Intune 구독의 속성에서 이를 편집할 수도 있습니다.

5. **확인**을 클릭하여 새 전자 메일 템플릿을 저장합니다.

6. **작업 추가** 페이지의 목록에서 새 전자 메일 템플릿을 선택할 수 있습니다.

7. 전자 메일 템플릿을 선택했으면 **확인**을 클릭합니다.

## <a name="to-create-actions-for-non-compliance"></a>비준수에 대한 작업 만들기

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.

2. **자산 및 준수** 작업 영역에서 **준수 설정**을 확장한 다음 **준수 정책**을 선택합니다.

3. **홈** 탭의 **만들기** 그룹에서 **준수 정책 만들기**를 선택합니다.

4. 원하는 대로 **지원되는 플랫폼**을 선택하고 **다음**을 두 번 클릭합니다. **규칙** 페이지는 건너뛸 수 있습니다.

5. **비준수 작업** 페이지에서 비준수 장치가 되면 수행할 작업을 정의하고 **새로 만들기**를 클릭합니다.
6. 두 가지 옵션, 즉 **최종 사용자에게 전자 메일 보내기** 또는 **비준수 장치 표시**를 선택할 수 있습니다.

7. **최종 사용자에게 전자 메일 보내기**를 선택하는 경우 다음을 입력해야 합니다. **유예 기간(일):** 0-365일을 입력할 수 있습니다.
    b. **추가 받는 사람(전자 메일을 통해)** c. **메시지 템플릿 선택:** 기본 전자 메일 템플릿 또는 사용자가 추가한 사용자 지정 템플릿을 선택할 수 있습니다.
    
    > [!TIP] 
    > **작업 추가** 페이지에서 **새로 만들기:**를 클릭하여 **최종 사용자에게 전자 메일 보내기** 작업을 추가할 때 새 전자 메일 템플릿을 추가할 수도 있습니다.

8. **비준수 장치 표시**를 선택하는 경우 다음을 입력해야 합니다. **유예 기간(일):** 0-365일을 입력할 수 있습니다.

9. 작업을 선택하고 설정을 입력했으면 **다음**을 두 번 클릭하고 **닫기**를 클릭합니다.


