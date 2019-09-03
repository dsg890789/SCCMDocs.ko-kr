---
title: Windows용 클라이언트 업그레이드 제외
titleSuffix: Configuration Manager
description: Configuration Manager에서 Windows 클라이언트가 업그레이드되지 않도록 제외하는 방법을 알아봅니다.
ms.date: 08/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7a16bc859006b0253459259d354a68e2ff1dec83
ms.sourcegitcommit: 2d38de4846ea47a03cc884cbd3df27db48f64a6a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70110147"
---
# <a name="how-to-exclude-clients-from-upgrade-in-configuration-manager"></a>Configuration Manager에서 클라이언트를 업그레이드에서 제외하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

업데이트된 클라이언트 버전을 자동으로 설치하지 않도록 클라이언트 컬렉션을 제외할 수 있습니다. 클라이언트를 업그레이드할 때 주의가 필요한 컴퓨터 컬렉션에 이 제외를 사용하세요. 제외된 컬렉션에 있는 클라이언트는 업데이트된 클라이언트 소프트웨어 설치 요청을 무시합니다.

이 제외는 다음 방법에 적용됩니다.

- 자동 업그레이드
- 소프트웨어 업데이트 기반 업그레이드
- 로그온 스크립트
- 그룹 정책

> [!NOTE]
> 사용자 인터페이스에는 클라이언트가 어떤 방법으로도 업그레이드되지 않는다고 명시되어 있지만 두 가지 방법을 사용하여 이러한 설정을 재정의할 수 있습니다. 클라이언트 강제 설치 또는 수동 클라이언트 설치를 사용하여 이 구성을 재정의합니다. 자세한 내용은 [제외된 클라이언트를 업그레이드하는 방법](#bkmk_override)을 참조하세요.

## <a name="bkmk_exclude"></a> 제외 구성

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **사이트 구성**을 펼치고 **사이트** 노드를 선택한 다음 리본에서 **계층 구조 설정**을 선택합니다.

2. **클라이언트 업그레이드** 탭으로 전환합니다.

3. **지정한 클라이언트를 업그레이드에서 제외** 옵션을 선택합니다. 그런 다음 제외하려는 **제외 컬렉션**을 선택합니다. 제외할 컬렉션은 하나만 선택할 수 있습니다.

4. **확인**을 선택하여 구성을 닫고 저장합니다.

![자동 업그레이드 제외에 대한 설정](media/automatic_upgrade_exclusion.png)

제외된 컬렉션에 있는 클라이언트는 정책을 업데이트한 후에 자동으로 클라이언트 업데이트를 설치하지 않습니다. 자세한 내용은 [Windows 컴퓨터에 대한 클라이언트를 업그레이드하는 방법](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers)을 참조하세요.

> [!NOTE]
> 제외된 클라이언트는 여전히 Ccmsetup을 다운로드하여 실행하지만 업그레이드되지는 않습니다.

제외 컬렉션에서 제거된 클라이언트는 다음 자동 업그레이드 주기까지 자동으로 업그레이드되지 않습니다.

## <a name="bkmk_override"></a> 제외된 클라이언트를 업그레이드하는 방법

디바이스가 업그레이드에서 제외한 컬렉션의 멤버인 경우에도 다음 방법 중 하나를 사용하여 클라이언트를 업그레이드할 수 있습니다.

- **클라이언트 강제 설치**: Ccmsetup은 사용자가 직접 의도한 것이므로 클라이언트 강제 설치를 허용합니다. 이 방법을 사용하면 컬렉션에서 클라이언트를 제거하거나 전체 컬렉션을 제외에서 제거하지 않고 클라이언트를 업그레이드할 수 있습니다.

- **수동 클라이언트 설치**: Ccmsetup 명령줄 매개 변수 **/IgnoreSkipUpgrade**를 사용하여 제외된 클라이언트를 수동으로 업그레이드합니다.

    제외된 컬렉션의 멤버인 클라이언트를 수동으로 업그레이드하려 할 때 이 매개 변수를 사용하지 않으면 클라이언트 소프트웨어가 업그레이드되지 않습니다. 자세한 내용은 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients)

- [Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)

- [확장된 상호 운용성 클라이언트](/sccm/core/understand/interoperability-client)
