---
title: 프로비저닝 모드
titleSuffix: Configuration Manager
description: Configuration Manager 작업 순서 중에 클라이언트 프로비저닝 모드에 대해 알아봅니다.
ms.date: 05/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 3e3ff3a4-7a75-41bb-bdf9-33ede9c0e3a3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f0e5a313bb5afd0501f0d6027d42b5a51a7e8946
ms.sourcegitcommit: 7b111cd8a797877031378349898810c3dd0a3750
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631951"
---
# <a name="provisioning-mode"></a>프로비저닝 모드

*적용 대상: System Center Configuration Manager(현재 분기)*

OS 배포 작업 순서 중에 Configuration Manager는 클라이언트를 프로비전 모드에 배치합니다. (OS 배포 작업 순서에는 Windows 10으로 전체 업그레이드가 포함되어 있습니다.) 이 상태의 클라이언트는 사이트에서 정책을 처리하지 않습니다. 이 동작은 클라이언트에서 실행되는 추가 배포의 위험 없이 실행할 작업 순서를 허용합니다. 성공하든 또는 실패하든 작업 순서가 완료되면 클라이언트 프로비전 모드가 종료됩니다.

작업 순서가 예기치 않게 실패하는 경우 프로비전 모드로 클라이언트를 유지할 수 있습니다. 예를 들어 작업 순서 처리 중에 디바이스가 다시 시작되고 복구될 수 없는 경우. 관리자는 이 상태의 클라이언트를 수동으로 식별하고 수정해야 합니다.


## <a name="manually-remove-provisioning-mode"></a>프로비저닝 모드를 수동으로 제거

클라이언트가 프로비저닝 모드로 남아 있는 경우 이 수동 프로세스를 사용하여 클라이언트를 정상 작동 상태로 되돌립니다.

```PowerShell
Invoke-WmiMethod -Namespace root\CCM -Class SMS_Client -Name SetClientProvisioningMode -ArgumentList $false
```

> [!Important]  
> 이 WMI 메서드가 변경한 사항 중 하나는 레지스트리 값을 설정하는 것이지만 다른 변경도 수행합니다. 레지스트리 값을 변경해도 클라이언트가 프로비저닝 모드에서 완전히 벗어나는 것은 아닙니다. 레지스트리를 수동으로 편집하면 클라이언트가 예기치 않은 동작이 발생할 수 있습니다.  


## <a name="client-provisioning-mode-timeout"></a>클라이언트 프로비전 모드 시간 제한

버전 1902부터 작업 순서가 클라이언트를 프로비저닝 모드에 배치하는 경우 타임스탬프를 설정합니다. 60분마다 프로비저닝 모드의 클라이언트는 타임스탬프 이후의 기간을 확인합니다. 48시간을 초과하는 프로비전 모드에 있는 경우 클라이언트는 자동으로 프로비전 모드를 종료하고 해당 프로세스를 다시 시작합니다.

48시간은 기본 프로비전 모드 시간 제한 값입니다. 다음 레지스트리 키 값 `HKLM\Software\Microsoft\CCM\CcmExec`에서 **ProvisioningMaxMinutes** 값을 설정하여 디바이스에서 이 타이머를 조정할 수 있습니다. 이 값이 존재하지 않거나 `0`인 경우, 클라이언트는 기본 48시간을 사용합니다.

Timestamp **ProvisioningEnabledTime** 는 다음 레지스트리 키 `HKLM\Software\Microsoft\CCM\CcmExec`에 있습니다. 타임 스탬프는 컴퓨터에서 프로 비전 모드를 마지막으로 시작한 시간 값을 갖습니다. 형식은 epoch (Unix 타임 스탬프) 이며 UTC입니다.

이 타임 스탬프는 다음 명령을 사용 하 여 수동으로 컴퓨터를 프로 비전 모드로 전환 하는 경우에도 현재 시간으로 다시 설정 됩니다.

```powershell
Invoke-WmiMethod -Namespace root\CCM -Class SMS_Client -Name SetClientProvisioningMode -ArgumentList $true
```

## <a name="process-flow-diagrams"></a>프로세스 흐름 다이어그램

이러한 다이어그램은 작업 순서 및 클라이언트의 프로세스 흐름을 보여줍니다.

### <a name="task-sequence"></a>작업 순서

다음 다이어그램은 작업 순서가 프로비저닝 모드를 설정하는 방법을 보여줍니다.

![작업 순서 설정 프로비저닝 모드의 흐름 다이어그램](media/3197824-ts-flow.png)

### <a name="client-remediation"></a>클라이언트 재구성

다음 다이어그램은 클라이언트가 프로비저닝 모드를 종료하는 방법을 보여줍니다.

![프로비저닝 모드를 종료하는 클라이언트의 흐름 다이어그램](media/3197824-client-flow.png)


## <a name="see-also"></a>참고 항목

[Windows 및 ConfigMgr 설치](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr)

[운영 체제 업그레이드](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS)
