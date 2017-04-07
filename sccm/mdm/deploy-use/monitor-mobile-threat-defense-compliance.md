---
title: "Mobile Threat Defense 준수 모니터링 | System Center Configuration Manager"
description: "Configuration Manager 관리자 콘솔에서 Mobile Threat Defense 파트너 준수 상태를 모니터링합니다."
ms.custom: na
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: fa5919b72114d71e1fbad74418c662d199827690
ms.lasthandoff: 03/27/2017


---

# <a name="monitor-mobile-threat-defense-compliance"></a>**Mobile Threat Defense 준수 모니터링**

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="to-monitor-the-overall-compliance-status"></a>전체 준수 상태를 모니터링하려면

Mobile Threat Defense 상태를 모니터링하려면:

1.  Configuration Manager 콘솔에서 **모니터링** 작업 영역을 클릭합니다.

2.  **모니터링** 작업 영역에서 **보안** 노드를 클릭합니다.

시각적 차트 형식으로 표시되는 여러 위협 수준이 포함된 준수 상태 요약을 볼 수 있습니다. 차트의 개별 섹션을 클릭하면 다음과 같은 자세한 정보를 볼 수 있습니다. 

- 플랫폼에서 비규격으로 보고되는 장치 수
- 장치 준수 상태에 관련된 모든 오류

![](http://i.imgur.com/bmPsiWk.png)

## <a name="to-monitor-the-individual-compliance-status"></a>개별 준수 상태를 모니터링하려면

개별 장치 상태를 확인할 수도 있습니다.

1.  Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역을 클릭합니다.

2.  **장치**를 클릭합니다.

> [!TIP] 
> **장치 위협 준수** 및 **장치 위협 수준** 열을 추가하면 상태를 확인할 수 있습니다. 이러한 열은 기본적으로 표시되지 않습니다.

## <a name="device-threat-protection-tab"></a>장치 위협 방지 탭

또한 **장치** 화면에서 특정 장치를 선택하고 나서 장치 준수 상태에 대한 자세한 정보를 제공하는 **장치 위협 방지** 탭을 클릭할 수 있습니다. 아래에서 장치 준수 상태를 분석하는 데 유용한 열 설명과 예상 값을 찾을 수 있습니다.

> [!IMPORTANT] 
> [장치 위협 방지] 탭은 선택한 장치가 모바일 장치인 경우에만 표시됩니다.

|열 이름|기본적으로 표시|설명| 
|-|-|-|
|**설명**| 예 | Mobile Threat Defense 파트너가 제공하는 위협에 대한 세부 정보입니다. |
|**마지막 업데이트 시간**| 예 | Threat Defense 파트너가 위협에 대한 업데이트된 세부 정보를 Intune에 보낸 마지막 시간입니다. |
|**위협 심각도**| 예 | 위협 심각도는 Mobile Threat Defense 파트너 콘솔의 관리 구성에 따른 개별 위협에 대한 정의입니다. 세 가지 값 **낮음**, **보통** 또는 **높음** 중 하나를 사용합니다. |
|**위협 상태**| 예 | 장치에 대한 위협의 현재 상태입니다. 가능한 상태: **활성**, **해결됨** 또는 **무시됨:** 사용자가 장치에 대한 위협을 무시했지만 위협이 계속 존재함을 나타냅니다. |
|**위협 유형**| 예 | 위협의 Mobile Threat Defense 파트너 유형입니다. 가능한 값: **앱**, **파일** 또는 **OS** |
|**AAD 계정 ID**| 아니요 | Azure Active Directory 고유 식별자입니다. |
|**분류**| 예 | Mobile Threat Defense 파트너가 제공한 위협 분류입니다. 가능한 값: **루트 인에이블러, 리스크웨어, 애드웨어, 체인지웨어, 데이터 누수, 트로이 목마, 웜, 바이러스, 익스플로잇, 백도어, 봇, 앱 드로퍼, 클릭 사기, 스팸, 스파이웨어, 감시 웨어, 취약성, 알 수 없음, 루트 탈옥, 연결성, 전화 사기, 사이드로드된 앱** |
|**장치 ID**| 아니요 | 위협 정보가 포함된 Workplace 조인 장치를 나타내는 Azure Active Directory 개체 ID입니다. |
|**위협 ID**| 아니요 | 위협에 대한 Mobile Threat Defense 파트너에서 생성된 고유 식별자입니다. 위협 ID는 해결 방법 추적에 사용됩니다. |
|**위협 URL**| 아니요 | 제공될 경우 위협 URL은 다시 이 특정 위협에 대한 Mobile Threat Defense 파트너의 관리 콘솔 보기로 연결됩니다. |

> [!TIP] 
> 장치의 Mobile Threat Defense 준수 상태에 대한 자세한 정보를 확인하려면 **기본적으로 표시**되지 않는 열을 사용하도록 설정해야 합니다.
