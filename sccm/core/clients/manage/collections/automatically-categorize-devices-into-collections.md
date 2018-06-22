---
title: 컬렉션으로 장치 자동 분류
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 컬렉션으로 장치를 자동으로 분류합니다.
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: fcffc48431045fab2b2f69e112258c844ad184bb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32334796"
---
# <a name="automatically-categorize-devices-into-collections-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 컬렉션으로 장치 자동 분류

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune에서 Configuration Manager를 사용하는 경우 장치 컬렉션에 장치를 자동으로 배치하는 데 사용할 수 있는 장치 범주를 만들 수 있습니다. 그런 다음 사용자는 Intune에 장치를 등록할 때 장치 범주를 선택해야 합니다. Configuration Manager 콘솔에서 장치 범주를 변경할 수 있습니다.

> [!IMPORTANT]  
    >  이 기능은 Microsoft Intune의 **2016년 6월** 이상 릴리스에서 작동합니다. 이러한 절차를 시도하기 전에 이 릴리스로 업데이트했는지 확인합니다.

## <a name="create-device-categories"></a>장치 범주 만들기

1.  **자산 및 준수** > **개요** > **장치 컬렉션**으로 이동합니다.
2.  **홈** 탭의 **장치 컬렉션** 그룹에서 **장치 범주 관리**를 선택합니다.
3.  범주를 만들거나, 편집 또는 제거합니다.

## <a name="associate-a-collection-with-a-device-category"></a>컬렉션을 장치 범주에 연결

컬렉션을 장치 범주에 연결하면 해당 범주의 모든 장치가 컬렉션에 추가됩니다. **모든 시스템**과 같은 기본 제공 컬렉션에 장치 범주 규칙을 추가할 수 없습니다.

1.  장치 컬렉션에 대한 **속성** 대화 상자의 **멤버 관리 규칙** 탭에서 **규칙 추가** > **장치 범주 규칙**을 선택합니다.
2.  **장치 범주 선택** 대화 상자에서 컬렉션의 모든 장치에 적용될 하나 이상의 장치 범주를 선택합니다.

## <a name="change-the-category-of-a-device"></a>장치의 범주 변경

1.  **자산 및 준수** > **개요** > **장치**의 **장치** 목록에서 장치를 선택합니다.
2.  **홈** 탭의 **장치** 그룹에서 **범주 변경**을 선택합니다.
3.  범주를 선택하고 나서 **확인**을 선택합니다.

## <a name="view-which-category-a-device-belongs-to"></a>장치가 속한 범주를 확인합니다.

**자산 및 준수** > **개요** > **장치**의 **장치** 목록에서 범주는 **장치 범주** 열에 표시됩니다.

**장치 범주** 열이 표시되지 않는 경우 **장치** 목록(예: **이름**)에서 하나의 열 제목을 마우스 오른쪽 단추로 클릭한 다음 **장치 범주**를 선택합니다.

장치를 범주에 할당하고 이후에 범주를 삭제하는 경우 **Microsoft Intune에 사용자별로 등록된 장치 목록** 보고서에서 **장치 범주** 열에 범주 이름 대신 GUID가 표시됩니다.
