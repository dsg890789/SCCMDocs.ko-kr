---
title: 확장된 상호 운용성 클라이언트
titleSuffix: Configuration Manager
description: 현재 분기 사이트를 통한 정적 Configuration Manager 클라이언트의 장기 지원을 위해 확장된 상호 운용성 클라이언트를 사용하는 방법에 대해 알아봅니다.
ms.date: 08/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6bff382c4252eb99f35bad0cca05352e23705104
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70109893"
---
# <a name="use-the-configuration-manager-client-software-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>이후 버전의 현재 분기 사이트와 확장된 상호 운용성을 위해 버Configuration Manager 클라이언트 소프트웨어 사용

*적용 대상: System Center Configuration Manager(현재 분기)*  

비즈니스 요구 사항으로 인해 일부 디바이스에서 Configuration Manager 클라이언트를 정기적으로 업데이트하지 못할 수도 있습니다. 예를 들어, 변경 관리 정책을 따라야 하거나 디바이스가 중요 업무용일 경우입니다. EIC(확장된 상호 운용성 클라이언트)라는 새 클라이언트를 장기간 사용을 위해 설치하여 이러한 요구를 수용할 수 있습니다. EIC는 키오스크 또는 POS 디바이스와 같이 자주 업데이트할 수 없는 특정 디바이스에만 사용됩니다. 대부분의 클라이언트를 위해 [자동 클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#bkmk_autoupdate)를 계속 사용합니다.

## <a name="how-it-works"></a>작동 방식

일반적으로 Configuration Manager에 대한 새 [콘솔 내 업데이트](/sccm/core/servers/manage/install-in-console-updates)를 설치하는 경우 클라이언트에서 해당 클라이언트 소프트웨어를 자동으로 업데이트하므로 이러한 새로운 기능을 사용할 수 있습니다. 이 시나리오를 사용하여 현재 분기를 계속 업데이트하면서 새로운 기능 및 업데이트를 수신합니다. 대부분의 디바이스는 설치할 각 버전 업데이트를 통해 Configuration Manager 클라이언트 소프트웨어를 업데이트합니다. 그러나 클라이언트 소프트웨어 업데이트를 수신하지 않으려는 일부 중요 시스템에는 확장된 상호 운용성 클라이언트를 설치합니다. 이러한 클라이언트는 새 버전의 클라이언트 소프트웨어가 명시적으로 배포될 때까지 새 클라이언트 소프트웨어를 설치하지 않습니다.

## <a name="supported-versions"></a>지원되는 버전

다음 표에서는 이 시나리오에 대해 지원되는 Configuration Manager 클라이언트 버전을 보여 줍니다.

| Version | 가용일 | 지원 종료 날짜 |
|---------|---------|---------|
| 1902<br/>5.00.8790 | 2019년 3월 27일 | 2021년 3월 27일 이후 |
| 1802<br/>5.00.8634 | 2018년 5월 1일 | 2020년 5월 1일 이후 |
| 1606<br/>5.00.8412 | 2016년 11월 18일 | 2019 년 5 월 1일 |

> [!TIP]  
> EIC는 릴리스 날짜로부터 최소 2년 간 지원됩니다. 릴리스 날짜에 대한 자세한 내용은 [Configuration Manager 현재 분기 버전 지원](/sccm/core/servers/manage/current-branch-versions-supported)을 참조하세요.  

클라이언트 지원이 만료되기 전에 현재 분기에서 관리하는 디바이스의 확장된 상호 운용성 클라이언트의 업데이트를 계획합니다. 이렇게 하려면 Microsoft에서 새 버전의 클라이언트를 다운로드한 다음, 현재 확장된 상호 운용성 클라이언트를 사용하는 디바이스에 업데이트된 클라이언트 소프트웨어를 배포합니다.

## <a name="how-to-use-the-eic"></a>EIC 사용 방법

1. 이러한 디바이스를 컬렉션에 추가하고 해당 컬렉션을 자동 클라이언트 업그레이드에서 제외합니다. 자세한 내용은 [업그레이드에서 클라이언트를 제외하는 방법](/sccm/core/clients/manage/upgrade/exclude-clients-windows)을 참조하세요.  

1. Configuration Manager 업데이트 설치 미디어의 `\SMSSETUP\Client` 폴더에서 지원되는 버전의 EIC를 가져옵니다. 폴더의 전체 내용을 복사했는지 확인합니다.  

    > [!TIP]  
    > [VLSC(볼륨 라이선스 서비스 센터)](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx)에서 Configuration Manager 미디어를 찾으려면 **다운로드 및 키** 탭으로 이동하고 `System Center Config`를 검색한 다음, **System Center Config Mgr(현재 분기)** 을 선택합니다.

1. 해당 디바이스에서 EIC를 수동으로 설치합니다. 자세한 내용은 [수동으로 클라이언트 설치](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)를 참조하세요.  

    > [!Important]  
    > 버전 1606 클라이언트를 버전 1802로 업그레이드할 경우 CCMSETUP 옵션( **/AlwaysExcludeUpgrade:True**)을 사용합니다. 그렇지 않으면 클라이언트는 제외 정책 전에 자동으로 업그레이드할 관리 지점에서 정책을 받을 수 있습니다.  

## <a name="limitations"></a>제한 사항

- 콘솔 내 업데이트를 사용하는 경우 확장된 상호 운용성 클라이언트 소프트웨어에 대한 업데이트를 사용할 수 없습니다. EIC를 업데이트하는 방법에 대한 자세한 내용은 [제외된 클라이언트를 업그레이드하는 방법](/sccm/core/clients/manage/upgrade/exclude-clients-windows#bkmk_override)을 참조하세요.  

- EIC는 다음의 기능만 지원합니다.  

  - 소프트웨어 업데이트  
  - 하드웨어 및 소프트웨어 인벤토리
  - 패키지 및 프로그램

## <a name="next-steps"></a>다음 단계

[업그레이드에서 클라이언트를 제외하는 방법](/sccm/core/clients/manage/upgrade/exclude-clients-windows)

클라이언트가 원하는 디바이스에 제대로 설치되었는지 확인하려면 [클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)을 참조합니다.
