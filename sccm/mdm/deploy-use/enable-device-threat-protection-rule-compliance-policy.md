---
title: 준수 정책에서 Device Guard 규칙 사용
titleSuffix: Configuration Manager
description: 디바이스 규정 준수 정책에서 모바일 위협 방지 규칙을 활성화합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0bae054d3daa5aea8e343fef05aa4578221f17b6
ms.sourcegitcommit: 4e47f63a449f5cc2d90f9d68500dfcacab1f4dac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226830"
---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>준수 정책에서 디바이스 위협 방지 규칙 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

Lookout Mobile Threat Protection과 함께 Intune을 사용하면 모바일 위협을 탐지하고 디바이스에 대한 위험을 평가할 수 있습니다. 규격 디바이스의 경우 Configuration Manager에서 준수 정책 규칙을 만들어 확인할 위험 평가 항목을 포함할 수 있습니다. 그런 다음 디바이스 규정 준수에 따라 조건부 액세스 정책으로 Exchange, SharePoint 및 기타 서비스에 대한 액세스를 허용하거나 차단할 수 있습니다.

디바이스에 대한 규정 준수 정책이 Lookout의 위협 감지의 영향을 받으려면

* 규정 준수 정책에서 **디바이스 위협 방지** 규칙을 활성화해야 합니다.

* **Intune 관리자 콘솔**에서 **Lookout 상태** 페이지가 **활성**으로 표시되어야 합니다. Lookout 통합을 활성화하는 방법에 대한 자세한 내용과 지침은 [Intune에서 Lookout MTP 연결 사용](enable-lookout-connection-in-intune.md) 항목을 참조하세요.


규정 준수 정책에서 디바이스 위협 방지 규칙을 만들기 전에, [Lookout 디바이스 위협 방지 구독을 설정](set-up-your-subscription-with-lookout.md)하고 [Intune에서 Lookout을 연결](enable-lookout-connection-in-intune.md)하며 [Lookout for work 앱을 구성](configure-and-deploy-lookout-for-work-apps.md)하는 것이 좋습니다. 설정을 완료해야 준수 규칙이 적용됩니다.

디바이스 위협 방지 규칙을 활성화하려면 기존 규정 준수 정책을 사용하거나 새 규정 준수 정책을 만들면 됩니다.

[Lookout 콘솔](https://aad.lookout.com)에서 Lookout 디바이스 위협 장지를 설정하는 중에 다양한 위협을 높음, 보통, 낮음 수준으로 분류하는 정책을 만들었습니다. Intune 준수 정책에서는 해당 위협 수준을 사용하여 허용되는 최대 위협 수준을 설정합니다.

준수 정책 마법사의 **규칙** 페이지에서 다음 정보를 사용하여 새 규칙을 정의합니다.
  * 조건: 장치 위협 방지 최대 위험 수준입니다.
  * 값: 값 중 하나일 수 있습니다.
    * **없음 (보안 됨)**: 이 가장 안전 합니다. 디바이스에 어떤 위협도 있어서는 안 된다는 의미입니다. 위협 수준이 발견되면 디바이스가 규정을 준수하지 않는 것으로 평가됩니다.
    * **낮음**: 낮은 수준의 위협만 있는 장치가 규격으로 평가 됩니다. 더 높은 수준의 위협이 확인되는 디바이스는 비규격 상태로 설정됩니다.
    * **중간**: 장치는 장치가 있는 위협이 낮거나 중간 수준인 경우 장치가 규정 준수로 평가 됩니다. 높은 수준의 위협이 감지되면 디바이스가 규정 비준수로 결정됩니다.
    * **높은**: 이 보안이 가장 취약 합니다. 기본적으로 이 수준은 모든 위협 수준이 허용되며, 이 솔루션을 보고 전용으로 사용하는 경우에만 유용합니다.

Office 365 및 기타 서비스에 대한 조건부 액세스 정책을 만들 경우 위의 규정 준수 평가 사항을 고려하여 위협을 해결할 때까지 규정 비준수 디바이스는 회사 리소스 액세스가 차단됩니다.

디바이스 위협 방지 상태는 **모니터링** 작업 영역의 **보안** 노드에 표시됩니다.
다양한 위협 수준 상태의 요약 정보가 시각적 차트에 표시됩니다. 차트의 개별 섹션을 클릭하면 플랫폼에서 비규격으로 보고하는 디바이스의 수와 보고된 오류 등의 추가 정보를 확인할 수 있습니다.
**자산 및 호환성** 작업 영역의 **디바이스**에서 개별 디바이스 상태를 확인할 수도 있습니다.  **디바이스 위협 준수** 및 **디바이스 위협 수준** 열을 추가하면 상태를 확인할 수 있습니다.  이러한 열은 기본적으로 표시되지 않습니다.
