---
title: "클라이언트 업그레이드 제외 | Windows | System Center Configuration Manager"
description: "System Center Configuration Manager에서 Windows 클라이언트가 업그레이드되지 않도록 제외하는 방법을 알아봅니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cd6031f-8844-4d0b-8166-b24d6528a94e
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 364b1a87e4cf52f09164de6347105f0bb876f1a3
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-exclude-upgrading-clients-for-windows-computers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트 업그레이드를 제외하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1610부터 업데이트된 클라이언트 버전을 자동으로 설치하지 않도록 클라이언트 컬렉션을 제외할 수 있습니다. 이 설정은 자동 업그레이드 및 소프트웨어 업데이트 기반 업그레이드, 로그온 스크립트 및 그룹 정책 등에 적용됩니다. 클라이언트를 업그레이드할 때 주의가 필요한 컴퓨터 컬렉션에 이 설정을 사용할 수 있습니다. 제외된 컬렉션에 있는 클라이언트는 업데이트된 클라이언트 소프트웨어 설치 요청을 무시합니다.

## <a name="configure-exclusion-for-automatic-upgrades"></a>자동 업그레이드의 제외 구성

1. Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동한 다음 **계층 구조 설정**을 클릭합니다.

2. **클라이언트 업그레이드** 탭을 클릭합니다.

3. **Exclude specified clients from upgrade**(지정된 클라이언트를 업그레이드에서 제외) 확인란을 클릭하고 Exclusion collection(제외 컬렉션)에서 제외할 컬렉션을 선택합니다. 제외할 컬렉션은 하나만 선택할 수 있습니다.

4.  **확인**을 클릭하여 구성을 닫고 저장합니다. 그러면 클라이언트가 정책을 업데이트한 후 제외된 컬렉션의 클라이언트가 클라이언트 소프트웨어에 대한 업데이트를 더 이상 자동으로 설치하지 않습니다. 자세한 내용은 [Windows 컴퓨터에 대한 클라이언트를 업그레이드하는 방법](upgrade-clients-for-windows-computers.md)을 참조하세요.

![자동 업그레이드 제외에 대한 설정](media/automatic_upgrade_exclusion.png)



>[!NOTE]
>사용자 인터페이스에는 어떠한 방법으로도 클라이언트가 업그레이드되지 않는다고 명시되어 있지만 두 가지 방법을 통해 이러한 설정을 재정의할 수 있습니다. 클라이언트 강제 설치 및 수동 클라이언트 설치를 사용하여 이 구성을 재정의할 수 있습니다. 자세한 내용은 다음 섹션을 참조하세요.

## <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>제외된 컬렉션에 있는 클라이언트를 업그레이드하는 방법

컬렉션이 제외되도록 구성하면 해당 컬렉션의 멤버가 다음 두 가지 방법 중 하나를 사용하여 제외를 재정의해야만 클라이언트 소프트웨어를 업그레이드할 수 있습니다.
 - **클라이언트 강제 설치** – 클라이언트 강제 설치를 사용하여 제외된 컬렉션에 있는 클라이언트를 업그레이드할 수 있습니다. 이 방법은 관리자의 의도인 것으로 간주되고 전체 컬렉션을 제외에서 제거하지 않고 클라이언트를 업그레이드할 수 있습니다.       

 - **수동 클라이언트 설치** – ccmsetup과 명령줄 스위치 ***/ignoreskipupgrade***를 함께 사용하면 제외된 컬렉션에 있는 클라이언트를 수동으로 업그레이드할 수 있습니다.

  제외된 컬렉션의 멤버인 클라이언트를 수동으로 업그레이드할 때 이 스위치를 사용하지 않으면 새 클라이언트 소프트웨어가 설치되지 않습니다. 자세한 내용은 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)을 참조하세요.

클라이언트 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.
