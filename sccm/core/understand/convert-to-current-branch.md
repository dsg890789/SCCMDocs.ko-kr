---
title: 현재 분기로 LTSB 업그레이드
titleSuffix: Configuration Manager
description: LTSB(장기 서비스 분기) 사이트를 현재 분기 사이트로 변환하는 방법을 알아봅니다.
ms.date: 02/8/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: ec5b54cf-62b7-4ed1-9bb3-e8c63b9641c8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56a85a86b047ffe0769fc175a79207c781e2cf23
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70891913"
---
# <a name="upgrade-the-long-term-servicing-branch-to-the-current-branch"></a>장기 서비스 분기를 현재 분기로 업그레이드

*적용 대상: System Center Configuration Manager(장기 서비스 분기)*

이 항목에서는 Configuration Manager의 LTSB(장기 서비스 분기)를 실행하는 사이트 및 계층 구조를 현재 분기로 업그레이드(변환)하는 방법을 알아봅니다.

현재 분기를 사용할 수 있는 권한을 부여하는 현재 Software Assurance 계약(또는 이와 유사한 라이선스 권한)이 있는 경우 설치를 LTSB에서 현재 분기로 변환할 수 있습니다.  현재 분기 사이트를 LTSB로 변환하는 지원은 없으므로 이 변환은 단방향 변환입니다.

여러 사이트가 있는 경우 계층 구조의 최상위 계층 사이트만 변환하면 됩니다. 최상위 계층 사이트를 변환하면
- 하위 기본 사이트가 자동으로 변환됩니다.
- Configuration Manager 콘솔 내에서 보조 사이트를 수동으로 업데이트해야 합니다.

## <a name="run-setup-to-convert-the-long-term-servicing-branch"></a>설치 프로그램을 실행하여 장기 서비스 분기 변환
계층 구조의 최상위 계층 사이트에서 정식 기준 미디어를 통해 Configuration Manager 설치 프로그램을 실행하고 **사이트 유지 관리**를 선택할 수 있습니다.  그런 다음 라이선스 페이지가 표시되면 현재 분기에 대한 옵션을 선택하고 마법사를 완료합니다.

사이트가 현재 분기로 변환되면, 이전에 사용할 수 없었던 기능과 특성을 사용할 수 있게 됩니다.

> [!NOTE]  
> 정식 기준 미디어는 LTSB 설치와 같거나 이후 버전인 미디어입니다.

예를 들어 LTSB가 버전 1606을 기반으로 하는 경우 1511 기준 미디어를 사용하여 현재 분기로 변환할 수 없습니다. 대신, LTSB 사이트를 설치할 때 사용한 것과 동일한 버전인 1606 기준 미디어에서 설치 프로그램을 실행하고 현재 분기에 대한 라이선스 옵션을 선택합니다.  또는 현재 분기의 이후 기준이 릴리스된 경우 해당 기준 미디어에서 설치 프로그램을 실행할 수 있습니다.

기준 버전 목록을 보려면 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)에서 **기준 및 업데이트 버전**을 참조하세요.

## <a name="use-the-configuration-manager-console-to-convert-the-long-term-servicing-branch"></a>Configuration Manager 콘솔을 사용하여 장기 서비스 분기 변환
사이트에서 LTSB를 실행하는 경우 Configuration Manager 콘솔에서 다음 옵션을 사용하여 현재 분기로 변환할 수 있습니다.

 1. 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동한 다음 **계층 설정**을 엽니다.  

 2. **계층 구조 설정**에서 **라이선스** 탭으로 전환합니다. 옵션을 선택하여 **현재 분기로 변환**한 다음, **적용**을 선택합니다.  

사이트가 현재 분기로 변환되면, 이전에 사용할 수 없었던 기능과 특성을 사용할 수 있게 됩니다.
