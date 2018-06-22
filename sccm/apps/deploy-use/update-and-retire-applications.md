---
title: 응용 프로그램 업데이트 및 사용 중지
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 배포된 응용 프로그램을 수정, 대체 또는 제거합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 68ac8a07-8e54-4a3c-91e3-e50dc1cabf5d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 831edd1d2c606253dcdc372a0a1503199734835c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32331593"
---
# <a name="update-and-retire-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 응용 프로그램 업데이트 및 사용 중지

*적용 대상: System Center Configuration Manager(현재 분기)*


나중에 응용 프로그램을 변경하거나, 응용 프로그램을 제거하거나, 이미 배포된 응용 프로그램을 새 응용 프로그램으로 대체할 가능성이 큽니다. System Center Configuration Manager는 응용 프로그램 업데이트 및 사용 중지에 도움이 되는 다음 기능을 제공합니다.  

-   **응용 프로그램 수정**. 응용 프로그램 또는 배포 유형을 변경하면 Configuration Manager에서 이러한 변경 내용의 기록을 유지 관리합니다. 언제든지 응용 프로그램을 이전 수정 버전으로 되돌릴 수 있습니다. 또한 각 수정 버전의 속성을 확인하고 이전의 응용 프로그램 수정 버전을 복원하거나, 이전 수정 버전을 삭제할 수 있습니다.  

  자세한 내용은 [응용 프로그램 수정 버전](revise-and-supersede-applications.md#application-revisions)을 참조하세요.  

-   **응용 프로그램 대체**. 교체 관계를 사용하여 기존 응용 프로그램을 업그레이드하거나 대체할 수 있습니다. 응용 프로그램을 교체할 때는 교체되는 응용 프로그램의 배포 유형을 대체할 새 배포 유형을 지정할 수 있습니다. 또한 대체 응용 프로그램을 설치하기 전에 대체 대상 응용 프로그램을 업그레이드할지 아니면 제거할지를 설정할 수 있습니다.  

  자세한 내용은 [응용 프로그램 대체](revise-and-supersede-applications.md#application-supersedence)를 참조하세요.  

-   **응용 프로그램 제거**. Configuration Manager를 사용하면 쉽게 응용 프로그램을 제거할 수 있습니다. 이 작업은 응용 프로그램 또는 장치 사용자의 개입 없이 자동으로 수행됩니다.  

  자세한 내용은 [응용 프로그램 제거](uninstall-applications.md)를 참조하세요.  
