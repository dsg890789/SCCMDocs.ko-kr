---
title: "준수 정책에서 장치 보호 규칙 사용 | System Center Configuration Manager"
description: "장치 준수 정책에서 모바일 위협 검색 규칙을 사용하도록 설정하는 방법을 설명합니다."
ms.custom: na
ms.date: 12/9/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 020f43e8-738e-4a82-91be-27b10cda9665
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 498b8c02dbf1391e6331c8b9ad7b6ef0fdef22d0
ms.openlocfilehash: 319289c9b211935ba10cb6d3da386ffed3c0153e
ms.lasthandoff: 02/23/2017


---
# <a name="create-a-lookout-device-threat-protection-rule"></a>Lookout 장치 위협 방지 규칙 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="before-you-begin"></a>시작하기 전에

Lookout Mobile Threat Protection이 설치되어 있는 Intune에서는 장치의 모바일 위협을 검색하고 위험을 평가할 수 있습니다. 규격 장치의 경우 Configuration Manager에서 준수 정책 규칙을 만들어 확인할 위험 평가 항목을 포함할 수 있습니다. 그런 후에 조건부 액세스 정책을 사용하여 장치의 규격 준수 여부에 따라 Exchange, SharePoint 및 기타 서비스 액세스를 허용하거나 차단할 수 있습니다.

장치의 준수 정책에 Lookout 장치 위협 방지가 적용되도록 하려면 다음 조건을 충족해야 합니다.

-   준수 정책에서 **장치 위협 방지** 규칙을 사용하도록 설정해야 합니다.

-   **Intune 관리자 콘솔**에서 **Lookout 상태** 페이지가 **활성**으로 표시되어야 합니다. Lookout 통합을 활성화하는 방법에 대한 자세한 내용과 지침은 [Intune에서 Lookout MTP 연결 사용](https://docs.microsoft.com/sccm/protect/deploy-use/enable-lookout-connection-in-intune) 항목을 참조하세요.

준수 정책에 장치 위협 방지 규칙을 만들기 전에 다음을 수행하는 것이 좋습니다.

1.  [Lookout 장치 위협 방지를 사용하여 구독 설정](https://docs.microsoft.com/sccm/protect/deploy-use/set-up-your-subscription-with-lookout)

2.  [Intune에서 Lookout 연결 사용](https://docs.microsoft.com/sccm/protect/deploy-use/enable-lookout-connection-in-intune)

3.  [Lookout for Work 앱 구성](https://docs.microsoft.com/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps)

>[!NOTE]
>설정을 완료해야 준수 규칙이 적용됩니다.

## <a name="to-create-a-device-threat-protection-rule"></a>장치 위협 방지 규칙을 만들려면

Lookout 장치 위협 방지 설정의 일부분으로 [Lookout 콘솔](https://aad.lookout.com)에서 다양한 위협의 수준을 높음, 보통, 낮음으로 분류하는 정책을 만들었을 것입니다. Intune 준수 정책에서는 해당 위협 수준을 사용하여 허용되는 최대 위협 수준을 설정합니다.

Lookout 장치 위협 방지 규칙을 만들려면

1.  Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역을 클릭합니다.

2.  **자산 및 준수**에서 **준수 정책**을 확장합니다.

3.  **준수 정책**을 마우스 오른쪽 단추로 클릭하고 **준수 정책 만들기**를 선택합니다.

4.  준수 정책 이름을 입력하고 **Configuration Manager 클라이언트 없이 관리되는 장치에 대한 준수 규칙**을 선택합니다.

5.  이 준수 정책을 사용하여 프로비전할 OS 플랫폼을 선택합니다(Android 4.1 이상 및/또는 iOS 8 이상).

6.  **규칙** 페이지에서 **새로 만들기**를 클릭하여 준수 장치에 대한 규칙을 지정합니다.

7.  **규칙 추가** 페이지에서 다음 정보를 사용하여 새 규칙을 정의합니다.
    1.  조건: 장치 위협 방지 최대 위험 수준
    
    2.  값: 값은 다음 중 하나일 수 있습니다.
        1.  **없음(보안됨)**: 가장 안전한 수준입니다. 장치에서 위협이 발생하지 않음을 의미합니다. 수준에 관계없이 위협이 확인되는 장치는 비규격으로 평가됩니다.
        2.  **낮음**: 낮은 수준의 위협만 있는 장치가 규격으로 평가됩니다. 더 높은 수준의 위협이 확인되는 장치는 비규격 상태로 설정됩니다.
        3.  **보통**: 낮음 또는 보통 수준의 위협이 발견되는 장치가 규격으로 평가됩니다. 높은 수준의 위협이 검색되는 장치는 비규격으로 간주됩니다.
        4.  **높음**: 안전성이 가장 낮은 수준입니다. 기본적으로 이 수준은 모든 위협 수준이 허용되며, 이 솔루션을 보고 전용으로 사용하는 경우에만 유용합니다.

>[!IMPORTANT]
>Office 365 및 기타 서비스용으로 조건부 액세스 정책을 만드는 경우 위의 준수 평가를 고려하며, 비규격 장치의 경우 위협을 해결할 때까지 회사 리소스의 액세스가 차단됩니다.
