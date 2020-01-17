---
title: 비호환 코드
titleSuffix: Configuration Manager
description: BitLocker 정책을 준수 하지 않는 Configuration Manager 클라이언트에서 사용할 수 있는 코드에 대 한 기술 참조
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 6c28fa29-fc97-49ef-9fc3-cb062bdba908
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7e8b94a66cce2a6e8b4c5cc14e23ce8b8cdd655c
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75818981"
---
# <a name="non-compliance-codes"></a>비호환 코드

*적용 대상: Configuration Manager(현재 분기)*

<!--3601034-->

클라이언트의 WMI는 다음과 같은 비호환 코드를 제공 합니다. 또한 특정 장치가 비규격으로 보고 하는 이유를 설명 합니다.

다양 한 방법으로 WMI를 볼 수 있습니다. 예를 들어 다음 PowerShell 명령을 사용합니다.

``` PowerShell
(Get-WmiObject -Class mbam_Volume -Namespace root\microsoft\mbam).ReasonsForNoncompliance
```

> [!TIP]
> 장치가 규정을 준수 하는 경우이 명령은 아무것도 반환 하지 않습니다.
>
> 이 클래스의 `Compliant` 특성을 확인할 수도 있습니다 .이 클래스는 장치가 규격을 준수 하는 경우 `1`입니다.

|비준수 코드|비준수 이유|
|--- |--- |
|0|암호화 강도가 AES 256이 아닙니다.|
|1|BitLocker 정책에는이 볼륨을 암호화 해야 하지만는 그렇지 않습니다.|
|2|BitLocker 정책을 사용 하려면이 볼륨을 암호화 *하지 않아도* 됩니다.|
|3|BitLocker 정책에서이 볼륨은 TPM 보호기를 사용 해야 하지만, 그렇지 않습니다.|
|4|BitLocker 정책에서이 볼륨은 TPM + PIN 보호기를 사용 해야 하지만이는 그렇지 않습니다.|
|5|BitLocker 정책은 TPM이 아닌 컴퓨터에서 호환 되는 것으로 보고 하는 것을 허용 하지 않습니다.|
|6|볼륨에 TPM 보호기가 있지만 TPM이 표시 되지 않습니다.|
|7|BitLocker 정책을 사용 하려면이 볼륨에 암호 보호기를 사용 해야 합니다. 단, 하나는 없습니다.|
|8|BitLocker 정책에는이 볼륨이 암호 보호기를 사용 *하지 않는* 것이 필요 하지만 하나 있습니다.|
|9|BitLocker 정책에서이 볼륨은 자동 잠금 해제 보호기를 사용 하도록 요구 하지만 하나는 포함 하지 않습니다.|
|10|BitLocker 정책을 사용 하려면이 볼륨에 자동 잠금 해제 보호기를 사용 *하지 않아도* 됩니다.|
|11|BitLocker는 정책 충돌을 검색 하 여이 볼륨을 규격으로 보고 하지 못하도록 합니다.|
|12|OS 볼륨을 암호화 하는 데 시스템 볼륨이 필요 하지만 존재 하지 않습니다.|
|13|볼륨에 대 한 보호가 일시 중단 되었습니다.|
|14|OS 볼륨이 암호화 되지 않은 경우 자동 잠금 해제는 안전 하지 않습니다.|
|15|정책에는 최소 암호 강도 is 128 XTS 비트를 사용 해야 합니다. 실제 암호 강도는 더 취약 합니다.|
|16|정책에는 최소 암호 강도 is 256 XTS 비트를 사용 해야 합니다. 실제 암호 강도는 더 취약 합니다.|
