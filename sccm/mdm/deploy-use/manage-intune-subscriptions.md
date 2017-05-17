---
title: "System Center Configuration Manager와 연결된 Intune 구독 관리 | Microsoft Docs"
description: "System Center Configuration Manager와 연결된 Intune 구독 관리"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 2e0b3cd1070d0f8adb1219acd33c3126d2758a49
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017

---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>System Center Configuration Manager와 연결된 Intune 구독 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune(평가판 구독 또는 유료 구독)을 Configuration Manager에 추가하고 다른 Intune 구독으로 전환해야 하는 경우 새 구독을 추가하려면 먼저 Configuration Manager 콘솔에서 **Microsoft Intune 구독** 및 **서비스 연결 지점**을 모두 삭제해야 합니다.

> [!NOTE]
> 하이브리드 모바일 장치 관리에서는 한 번에 하나의 Intune 구독만 구성할 수 있습니다.

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Configuration Manager에서 Intune 구독을 삭제하는 방법

> [!IMPORTANT]
>  구독을 삭제하면 Intune 구독을 통해 관리되는 장치에 구성된 사용자 등록, 정책 및 앱 배포를 포함한 모든 콘텐츠가 제거됩니다.

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.

2.  나열된 **Microsoft Intune 구독**을 마우스 오른쪽 단추로 클릭하고 **삭제**를 클릭합니다.

3.   마법사에서 **Configuration Manager에서 Microsoft Intune 구독 제거**, **다음**, **다음**을 차례로 클릭하여 구독을 제거합니다.


## <a name="how-to-remove-the-service-connection-point-role"></a>서비스 연결 지점 역할을 제거하는 방법

1.  **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동합니다.

2.  **서비스 연결 지점** 역할을 호스트하는 서버를 선택합니다.

3.  **사이트 시스템 역할** 목록에서 **서비스 연결 지점**을 선택한 후 리본 메뉴에서 **역할 제거**를 클릭합니다. 역할을 제거할 것을 확인합니다. 서비스 연결 지점이 삭제됩니다.

이제 새 서비스 연결 지점을 만들고, 새 Intune 구독을 Configuration Manager에 추가하고, Configuration Manager를 MDM 기관으로 설정할 수 있습니다.

## <a name="how-to-change-mdm-authority-to-intune"></a>MDM 기관을 Intune으로 변경하는 방법

버전 1610부터 MDM 기관을 Configuration Manager에서 Intune으로 전환할 수 있습니다. 이 기능에 대한 정보는 곧 제공될 예정입니다.

