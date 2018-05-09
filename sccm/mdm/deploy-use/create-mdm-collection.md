---
title: MDM 컬렉션 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 MDM 컬렉션 만들기
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d271499baf48364fe24a8961cae767c46d05a332
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="create-an-mdm-collection-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune을 사용하여 MDM 컬렉션 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

관리에 장치를 등록할 수 있는 사용자를 지정하려면 Configuration Manager 사용자 컬렉션이 필요합니다. Intune 라이선스는 사용자에 의해 할당되기 때문에 장치 컬렉션이 아니라 사용자 컬렉션만 사용할 수 있습니다.

> [!NOTE]
> Intune에 장치를 등록하기 위해 Office 365 포털이나 Azure Active Directory 포털에서 사용자에게 라이선스를 할당할 필요가 없습니다. [이후 단계](configure-intune-subscription.md)에서 Intune 구독과 연결된 컬렉션에 사용자를 포함하면 됩니다.

테스트 목적으로 **직접 규칙**을 설정하고 장치를 등록할 수 있는 특정 사용자를 추가할 수 있습니다. Configuration Manager 콘솔에서 **자산 및 준수** > **사용자 컬렉션**을 차례로 선택하고 **홈** 탭 > **만들기** 그룹을 차례로 클릭한 다음 **사용자 컬렉션 만들기**를 클릭합니다. 광범위한 배포의 경우 **쿼리 규칙**을 사용하여 사용자를 정의해야 합니다. 컬렉션에 대한 자세한 내용은 [컬렉션을 만드는 방법](https://technet.microsoft.com/library/mt629371.aspx)을 참조하세요.

![MDM에 대한 사용자 컬렉션 만들기](../media/mdm-create-user-collection.png)

> [!div class="button"]
[다음 단계 >](confirm-dns.md)
