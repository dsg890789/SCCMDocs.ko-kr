---
title: "현재 분기에서 Configuration Manager 확장된 상호 운용성 클라이언트 사용 | Microsoft Docs"
description: "현재 분기 사이트에서 Configuration Manager 장기 서비스 분기의 클라이언트를 사용하는 방법을 알아봅니다."
ms.custom: na
ms.date: 08/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: "0"
author: robstackmsft
ms.author: robstack
ms.openlocfilehash: 6487a7c0eb958c74ca4c6a7233747966110eceb9
ms.sourcegitcommit: b41d3e5c7f0c87f9af29e02de3e6cc9301eeafc4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2017
---
# <a name="use-the-configuration-manager-client-software-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>이후 버전의 현재 분기 사이트와 확장된 상호 운용성을 위해 버Configuration Manager 클라이언트 소프트웨어 사용

*적용 대상: System Center Configuration Manager(현재 분기), (장기 서비스 분기)*  

경우에 따라 회사 정책을 사용하면 일부 PC에서 Configuration Manager 클라이언트를 정기적으로 업데이트할 수 없을 수도 있습니다. 예를 들어, 변경 관리 정책을 준수해야 합니다. 그렇지 않으면 장치는 중요 업무용일 수 있습니다.

대부분의 Configuration Manager에서 가능하면 자동 클라이언트 업그레이드를 계속 사용해야 하는 반면 Configuration Manager 업데이트 1610부터는 장기간 사용을 위해 EIC(확장된 상호 운용성 클라이언트)라고 하는 새 클라이언트를 설치하여 이러한 요구 사항을 수용할 수 있습니다.

EIC는 1610 이후 버전을 실행하는 Configuration Manager 사이트와 호환할 수 있습니다. EIC는 키오스크 또는 POS 장치와 같이 자주 업데이트할 수 없는 특정 PC에만 사용해야 합니다. 다른 모든 PC에서 가장 최근의 Configuration Manager 클라이언트를 사용합니다.

## <a name="how-this-scenario-works"></a>이 시나리오 작동 방법

일반적으로 현재 분기에 대한 새 콘솔 내 업데이트를 설치하는 경우 클라이언트에서 해당 클라이언트 소프트웨어를 자동으로 업데이트하므로 새로운 기능을 사용할 수 있습니다.

이 시나리오에서는 현재 분기를 사용하고 새로운 기능 및 업데이트를 수신합니다. 대부분의 클라이언트는 현재 분기에서 클라이언트 소프트웨어를 실행하며, 해당 클라이언트 소프트웨어를 설치되는 각 버전 업데이트로 업데이트할 수 있습니다. 그러나 클라이언트 소프트웨어 업데이트를 수신하지 않으려는 일부 중요 시스템에는 확장된 상호 운용성 클라이언트를 설치합니다. 이러한 클라이언트는 새 버전의 클라이언트 소프트웨어가 명시적으로 배포될 때까지 새 클라이언트 소프트웨어를 설치하지 않습니다.

>[!IMPORTANT]
>현재 분기 사이트에서 버전 1610 이상을 실행해야 합니다.

## <a name="how-to-use-the-eic"></a>EIC 사용 방법

1. Configuration Manager 1606 업데이트 설치 미디어의 \SMSSETUP\Client 폴더에서 EIC(클라이언트 버전 5.00.8412)를 가져옵니다. 폴더의 전체 내용을 복사했는지 확인합니다.
2. 해당 장치에서 EIC를 수동으로 설치합니다. [수동으로 클라이언트를 설치하는 방법에 대한 자세한 내용을 참고하세요](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).
3. 클라이언트 업그레이드에서 해당 컬렉션을 제외합니다.

>[!TIP]
>VLSC(볼륨 라이선스 서비스 센터)에서 System Center Configuration Manager 버전 1606을 찾으려면 [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx)의 **다운로드 및 키** 탭으로 이동하고 "system center config"를 검색한 다음 **System Center Config Mgr(현재 분기 및 LTSB)**을 선택합니다.

## <a name="the-extended-interoperability-client-software"></a>확장된 상호 운용성 클라이언트 소프트웨어

현재 EIC는 적어도 2018년 11월 18일까지 업데이트된 버전의 Configuration Manager 현재 분기에서 계속 지원됩니다. 이 시간 이후 EIC의 새로운 세부 정보 또는 기존 EIC에 대한 지원 확장은 이 페이지를 확인하세요.

>[!TIP]
>EIC는 릴리스 날짜로부터 2년 동안 지원됩니다([System Center Configuration Manager 현재 분기 버전에 대한 지원](/sccm/core/servers/manage/current-branch-versions-supported)을 참조). 예를 들어, 현재 EIC에 대한 지원은 1610의 릴리스 이후 2년이 되는 날짜인 2018년 11월 18일까지입니다.

클라이언트 지원이 만료되기 전에 현재 분기에서 관리하는 장치의 확장된 상호 운용성 클라이언트의 업데이트를 계획합니다. 이렇게 하려면 Microsoft에서 새 버전의 클라이언트를 다운로드한 다음 현재 확장된 상호 운용성 클라이언트를 사용하는 장치에 업데이트된 클라이언트 소프트웨어를 배포합니다.

## <a name="limitations-of-the-extended-interoperability-client"></a>확장된 상호 운용성 클라이언트의 제한 사항

- 콘솔 내 업데이트를 사용하는 경우 확장된 상호 운용성 클라이언트 소프트웨어에 대한 업데이트를 사용할 수 없습니다. 업데이트된 클라이언트가 릴리스될 때 업데이트된 클라이언트 소프트웨어 배포에 대한 추가 정보가 제공됩니다.
- EIC는 소프트웨어 업데이트, 인벤토리 및 패키지와 프로그램만을 지원합니다.

## <a name="next-steps"></a>다음 단계

[클라이언트를 모니터링하는 방법](/sccm/core/clients/manage/monitor-clients)의 정보를 사용하여 클라이언트가 원하는 장치에 제대로 설치되어 있도록 합니다.
