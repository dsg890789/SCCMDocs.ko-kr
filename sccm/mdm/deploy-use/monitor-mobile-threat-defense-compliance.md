---
title: Mobile Threat Defense 준수 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager 관리자 콘솔에서 Mobile Threat Defense 파트너 준수 상태를 모니터링합니다.
ms.date: 03/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 408190da-bea6-4122-9dd6-f90155040e88
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b77fabc6ea4f5823777e932011313c5e2de1acf
ms.sourcegitcommit: f42b9e802331273291ed498ec88f710110fea85a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67551338"
---
# <a name="monitor-mobile-threat-defense-compliance"></a>**Mobile Threat Defense 준수 모니터링**

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="to-monitor-the-overall-compliance-status"></a>전체 준수 상태를 모니터링하려면

Mobile Threat Defense 상태를 모니터링하려면:

1.  Configuration Manager 콘솔에서 **모니터링** 작업 영역을 클릭합니다.

2.  **모니터링** 작업 영역에서 **보안** 노드를 클릭합니다.

시각적 차트 형식으로 표시되는 여러 위협 수준이 포함된 준수 상태 요약을 볼 수 있습니다. 차트의 개별 섹션을 클릭하면 다음과 같은 자세한 정보를 볼 수 있습니다. 

- 플랫폼에서 비규격으로 보고되는 디바이스 수
- 디바이스 준수 상태에 관련된 모든 오류

![장치 위협 방지 대시보드](device-threat-protection-dashboard.png)

## <a name="to-monitor-the-individual-compliance-status"></a>개별 준수 상태를 모니터링하려면

개별 디바이스 상태를 확인할 수도 있습니다.

1.  Configuration Manager 콘솔에서 **자산 및 준수** 작업 영역을 클릭합니다.

2.  **디바이스**를 클릭합니다.

> [!TIP] 
> **디바이스 위협 준수** 및 **디바이스 위협 수준** 열을 추가하면 상태를 확인할 수 있습니다. 이러한 열은 기본적으로 표시되지 않습니다.

## <a name="device-threat-protection-tab"></a>디바이스 위협 방지 탭

또한 **디바이스** 화면에서 특정 디바이스를 선택하고 나서 디바이스 준수 상태에 대한 자세한 정보를 제공하는 **디바이스 위협 방지** 탭을 클릭할 수 있습니다. 아래에서 디바이스 준수 상태를 분석하는 데 유용한 열 설명과 예상 값을 찾을 수 있습니다.

> [!IMPORTANT] 
> [디바이스 위협 방지] 탭은 선택한 디바이스가 모바일 디바이스인 경우에만 표시됩니다.

|열 이름|기본적으로 표시|Description| 
|-|-|-|
|**설명**| 예 | Mobile Threat Defense 파트너가 제공하는 위협에 대한 세부 정보입니다. |
|**마지막 업데이트 시간**| 예 | Threat Defense 파트너가 위협에 대한 업데이트된 세부 정보를 Intune에 보낸 마지막 시간입니다. |
|**위협 심각도**| 예 | 위협 심각도는 Mobile Threat Defense 파트너 콘솔의 관리 구성에 따른 개별 위협에 대한 정의입니다. 세 값 중 하나 있습니다. **낮은**하십시오 **Medium** 또는 **높은** |
|**위협 상태**| 예 | 디바이스에 대한 위협의 현재 상태입니다. 가능한 상태: **Active**하십시오 **확인할** 또는 **무시:** 사용자가 장치에 대 한 위협을 무시 했지만 위협이 남아 있는지를 나타냅니다. |
|**위협 유형**| 예 | 위협의 Mobile Threat Defense 파트너 유형입니다. 가능한 값: **앱**하십시오 **파일** 또는 **OS** |
|**AAD 계정 ID**| 아니요 | Azure Active Directory 고유 식별자입니다. |
|**분류**| 예 | Mobile Threat Defense 파트너가 제공한 위협 분류입니다. 가능한 값: **루트 인에 블러, 리스크 웨어, 애드웨어, 체인 지 웨어, 데이터 누수, 트로이 목마, 웜, 바이러스, 악용, 백도어, 봇, 앱 드로 퍼, 클릭 사기, 스팸, 스파이웨어, 감시 웨어, 취약성, 알 수 없음, 루트 탈 옥, 연결성, 사기, 전화** |
|**디바이스 ID**| 아니요 | 위협 정보가 포함된 Workplace 조인 디바이스를 나타내는 Azure Active Directory 개체 ID입니다. |
|**위협 ID**| 아니요 | 위협에 대한 Mobile Threat Defense 파트너에서 생성된 고유 식별자입니다. 위협 ID는 해결 방법 추적에 사용됩니다. |
|**위협 URL**| 아니요 | 제공될 경우 위협 URL은 다시 이 특정 위협에 대한 Mobile Threat Defense 파트너의 관리 콘솔 보기로 연결됩니다. |

> [!TIP] 
> 디바이스의 Mobile Threat Defense 준수 상태에 대한 자세한 정보를 확인하려면 **기본적으로 표시**되지 않는 열을 사용하도록 설정해야 합니다.
