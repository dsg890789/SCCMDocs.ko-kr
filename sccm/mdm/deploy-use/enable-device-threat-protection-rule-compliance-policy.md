---
title: "준수 정책에서 Device Guard 규칙 사용"
titleSuffix: Configuration Manager
description: "장치 준수 정책에서 모바일 위협 검색 규칙을 사용하도록 설정하는 방법을 설명합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
caps.latest.revision: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d74360ce800f030e85e2b87defc1de3376c6aee5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>준수 정책에서 장치 위협 방지 규칙 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

Lookout Mobile Threat Protection이 설치되어 있는 Intune에서는 장치의 모바일 위협을 검색하고 위험을 평가할 수 있습니다. 규격 장치의 경우 Configuration Manager에서 준수 정책 규칙을 만들어 확인할 위험 평가 항목을 포함할 수 있습니다. 그런 후에 조건부 액세스 정책을 사용하여 장치의 규격 준수 여부에 따라 Exchange, SharePoint 및 기타 서비스 액세스를 허용하거나 차단할 수 있습니다.

장치의 준수 정책에 Lookout 장치 위협 방지가 적용되도록 하려면 다음 조건을 충족해야 합니다.

* 준수 정책에서 **장치 위협 방지** 규칙을 사용하도록 설정해야 합니다.

* **Intune 관리자 콘솔**에서 **Lookout 상태** 페이지가 **활성**으로 표시되어야 합니다. Lookout 통합을 활성화하는 방법에 대한 자세한 내용과 지침은 [Intune에서 Lookout MTP 연결 사용](enable-lookout-connection-in-intune.md) 항목을 참조하세요.


준수 정책에서 장치 위협 방지 규칙을 만들기 전에 [Lookout 장치 위협 방지를 포함하는 구독을 설정](set-up-your-subscription-with-lookout.md)하고, [Intune에서 Lookout 연결을 사용하도록 설정](enable-lookout-connection-in-intune.md)하고, [Lookout for Work 앱을 구성](configure-and-deploy-lookout-for-work-apps.md)하는 것이 좋습니다. 설정을 완료해야 준수 규칙이 적용됩니다.

장치 위협 방지 규칙을 사용하도록 설정하려는 경우 기존 준수 정책을 사용할 수도 있고 새 정책을 만들 수도 있습니다.

Lookout 장치 위협 방지 설정의 일부분으로 [Lookout 콘솔](https://aad.lookout.com)에서 다양한 위협의 수준을 높음, 보통, 낮음으로 분류하는 정책을 만들었을 것입니다. Intune 준수 정책에서는 해당 위협 수준을 사용하여 허용되는 최대 위협 수준을 설정합니다.

준수 정책 마법사의 **규칙** 페이지에서 다음 정보를 사용하여 새 규칙을 정의합니다.
  * 조건: 장치 위협 방지 최대 위험 수준
  * 값: 값은 다음 중 하나일 수 있습니다.
    * **없음(보안됨)**: 가장 안전한 수준입니다. 장치에서 위협이 발생하지 않음을 의미합니다. 수준에 관계없이 위협이 확인되는 장치는 비규격으로 평가됩니다.
    * **낮음**: 낮은 수준의 위협만 있는 장치가 규격으로 평가됩니다. 더 높은 수준의 위협이 확인되는 장치는 비규격 상태로 설정됩니다.
    * **보통**: 낮음 또는 보통 수준의 위협이 발견되는 장치가 규격으로 평가됩니다. 높은 수준의 위협이 검색되는 장치는 비규격으로 간주됩니다.
    * **높음**: 안전성이 가장 낮은 수준입니다. 기본적으로 이 수준은 모든 위협 수준이 허용되며, 이 솔루션을 보고 전용으로 사용하는 경우에만 유용합니다.

Office 365 및 기타 서비스용으로 조건부 액세스 정책을 만드는 경우 위의 준수 평가를 고려하며, 비규격 장치의 경우 위협을 해결할 때까지 회사 리소스의 액세스가 차단됩니다.

장치 위협 방지 상태는 **모니터링** 작업 영역의 **보안** 노드에 표시됩니다.
다양한 위협 수준 상태의 요약 정보가 시각적 차트에 표시됩니다. 차트의 개별 섹션을 클릭하면 플랫폼에서 비규격으로 보고하는 장치의 수와 보고된 오류 등의 추가 정보를 확인할 수 있습니다.
**자산 및 호환성** 작업 영역의 **장치**에서 개별 장치 상태를 확인할 수도 있습니다.  **장치 위협 준수** 및 **장치 위협 수준** 열을 추가하면 상태를 확인할 수 있습니다.  이러한 열은 기본적으로 표시되지 않습니다.
