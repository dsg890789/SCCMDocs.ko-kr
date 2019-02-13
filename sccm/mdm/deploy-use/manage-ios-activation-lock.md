---
title: iOS 활성화 잠금 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager로 iOS 활성화 잠금을 관리합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: e2745bac-e1b4-4dac-8ac7-32f1c820bc9c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8a695a0b777f4adf3d2fb336df6aced8702e9dab
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56125258"
---
# <a name="manage-ios-activation-lock-with-system-center-configuration-manager"></a>System Center Configuration Manager로 iOS 활성화 잠금 관리

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager를 사용하면 iOS 7.1 이상 디바이스용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금이 설정되면 사용자의 Apple ID와 암호를 입력해야 다음 작업을 수행할 수 있습니다.

- 나의 iPhone 찾기 끄기
- 디바이스의 콘텐츠 지우기
- 디바이스 다시 활성화

**감독되지 않은** 디바이스에서, 활성화 잠금은 나의 iPhone 찾기 앱을 사용할 때 자동으로 사용하도록 설정됩니다.

**감독된** 디바이스에서, Configuration Manager 준수 설정을 사용하여 활성화 잠금을 활성화해야 합니다.

> [!TIP]
> iOS 디바이스에 대해 감독 모드를 사용하면 Apple Configurator Tool을 통해 디바이스를 잠가 특정 업무용으로 기능을 제한할 수 있습니다. 감독 모드는 대개 회사가 소유한 디바이스에서만 사용됩니다.

활성화 잠금 기능을 사용하면 iOS 디바이스를 보호하고, 디바이스 손실 및 도난 시 복구 가능성을 높일 수는 있지만 IT 관리자의 경우에는 여러 가지 문제를 해결해야 할 수도 있습니다. 예:

- 사용자 중 한 명이 디바이스에서 활성화 잠금을 설정합니다. 해당 사용자가 퇴사하게 되어 디바이스를 반납합니다. 이 경우 해당 사용자의 Apple ID와 암호가 없으면 디바이스를 초기화해도 다시 활성화할 수 없습니다.
- 활성화 잠금을 사용하도록 설정한 모든 디바이스의 보고서를 작성해야 합니다.
- 조직에서 디바이스를 새로 고칠 때 일부 디바이스를 다른 부서에 다시 할당해야 하는 경우가 있습니다. 이때 활성화 잠금이 사용하도록 설정되지 않은 디바이스만 다시 할당할 수 있습니다.


이러한 문제를 해결할 수 있도록 Apple은 iOS 7.1에 활성화 잠금 무시 기능을 도입했습니다. 이 기능을 통해 사용자의 Apple ID와 암호가 없어도 감독된 디바이스에서 활성화 잠금을 제거할 수 있습니다. 감독된 디바이스는 디바이스별 활성화 잠금 무시 코드를 생성할 수 있으며, 이 코드는 Apple 활성화 서버에 저장됩니다.

활성화 잠금에 대한 자세한 내용은 [여기](https://support.apple.com/HT201365)에서 확인할 수 있습니다.

## <a name="how-configuration-manager-helps-you-manage-activation-lock"></a>Configuration Manager가 활성화 잠금을 지원하는 방식

다음 두 가지 방법으로 Configuration Manager에서 활성화 잠금 관리를 지원할 수 있습니다.

1. 감독된 디바이스에서 활성화 잠금을 사용합니다.
2. 감독된 디바이스에서 활성화 잠금을 무시합니다.

> [!IMPORTANT]
> 감독되지 않은 디바이스에서는 활성화 잠금을 무시할 수 없습니다.

회사 소유 디바이스에서 이러한 방식의 비즈니스 이점은 다음과 같습니다.



- 사용자가 나의 iPhone 찾기 앱의 보안 이점을 활용할 수 있습니다.
- 디바이스의 용도를 다시 설정해야 하는 경우 디바이스를 사용 중지하거나 잠금 해제할 수 있으므로 사용자가 안심하고 디바이스에서 작업을 할 수 있습니다.


## <a name="enable-activation-lock-on-supervised-devices"></a>감독된 디바이스에서 활성화 잠금 사용

Configuration Manager 준수 설정을 사용해 **iOS 및 Mac OS X** 형식의 구성 항목을 만들고 배포하여 다음과 같이 감독된 디바이스에서 활성화 잠금을 사용할 수 있습니다.

1. [System Center Configuration Manager 클라이언트 없이 관리되는 iOS 및 Mac OS X 디바이스에 대해 구성 항목을 만드는 방법](/sccm/compliance/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client) 항목의 정보를 사용하여 **iOS 및 Mac OS X**형식의 구성 항목을 만듭니다.
2. 구성 항목 만들기 마법사의 **시스템 보안** 페이지에서 **활성화 잠금 허용(감독자 모드만)** 설정을 **허용됨**으로 구성합니다.
3. [구성 기준에 구성 항목을 추가합니다](/sccm/compliance/deploy-use/create-configuration-baselines).
4. 활성화 잠금을 사용하도록 설정하려는 iOS 디바이스를 포함하는 컬렉션에[이 구성 기준을 배포](/sccm/compliance/deploy-use/deploy-configuration-baselines) 합니다.

> [!IMPORTANT]
> 이 절차를 수행하려면 먼저 디바이스를 실제로 소유해야 합니다. 디바이스를 소유하지 않은 경우 활성화 잠금이 무시되며, 디바이스를 소유하는 사람은 누구든 디바이스에 대해 모든 권한을 보유하므로 나의 iPhone 찾기 끄기, 디바이스의 콘텐츠 지우기 또는 디바이스 다시 활성화를 수행할 수 있습니다.

감독된 디바이스에서만 활성화 잠금을 무시하거나 활성화 잠금 무시 코드를 검색할 수 있습니다. 감독되지 않은 디바이스에서 활성화 잠금을 무시하거나 무시 코드를 보려고 하면 오류가 발생합니다.



## <a name="view-the-activation-lock-bypass-code"></a>활성화 잠금 무시 코드 보기

1. Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.
2. **자산 및 호환성** 작업 영역에서 **디바이스**를 클릭합니다.
3. 활성화 잠금을 사용할 수 있는 감독 모드에 있는 등록된 디바이스를 선택합니다.
4. **홈** 탭의 **디바이스** 그룹에서 **원격 디바이스 작업** > **활성화 잠금 무시 코드 보기**를 클릭합니다.
5. **활성화 잠금 무시 코드** 대화 상자에 선택한 디바이스에 대한 무시 코드가 표시됩니다.

## <a name="bypass-activation-lock"></a>활성화 잠금 무시

1. Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.
2. **자산 및 호환성** 작업 영역에서 **디바이스**를 클릭합니다.
3. 활성화 잠금을 사용할 수 있는 감독 모드에 있는 등록된 디바이스를 선택합니다.
3. **홈** 탭의 **디바이스** 그룹에서 **원격 디바이스 작업** > **활성화 잠금 무시**를 클릭합니다.
5. 경고 대화 상자에서 메시지를 읽고 진행할 준비가 되면 **예** 를 클릭합니다.
6. 다음에서 잠금 해제 요청의 상태를 검사할 수 있습니다.

    - 디바이스 속성 대화 상자의 디바이스에 대한 검색 데이터
    - **디바이스** 보기의 **활성화 잠금 무시 상태** 열(이 열은 기본적으로 숨겨져 있음)
    - 세부 정보 창의 **요약** 탭에 있는 **원격 디바이스 작업 정보** 섹션(디바이스를 선택한 경우)
