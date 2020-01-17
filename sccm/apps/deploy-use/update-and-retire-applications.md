---
title: 애플리케이션 업데이트 및 사용 중지
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 배포된 애플리케이션을 수정, 대체 또는 제거합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 68ac8a07-8e54-4a3c-91e3-e50dc1cabf5d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7770f1db0e311186a908890dc339401ed3cbeb4b
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75817825"
---
# <a name="update-and-retire-applications-with-configuration-manager"></a>Configuration Manager를 사용하여 애플리케이션 업데이트 및 사용 중지

*적용 대상: Configuration Manager(현재 분기)*


나중에 애플리케이션을 변경하거나, 애플리케이션을 제거하거나, 이미 배포된 애플리케이션을 새 애플리케이션으로 대체할 가능성이 큽니다. Configuration Manager는 애플리케이션 업데이트 및 사용 중지에 도움이 되는 다음 기능을 제공합니다.  

- **애플리케이션 수정**. 애플리케이션 또는 배포 유형을 변경하면 Configuration Manager에서 이러한 변경 내용의 기록을 유지 관리합니다. 언제든지 애플리케이션을 이전 수정 버전으로 되돌릴 수 있습니다. 또한 각 수정 버전의 속성을 확인하고 이전의 애플리케이션 수정 버전을 복원하거나, 이전 수정 버전을 삭제할 수 있습니다.  

  자세한 내용은 [애플리케이션 수정 버전](revise-and-supersede-applications.md#application-revisions)을 참조하세요.  

- **애플리케이션 대체**. 교체 관계를 사용하여 기존 애플리케이션을 업그레이드하거나 대체할 수 있습니다. 애플리케이션을 교체할 때는 교체되는 애플리케이션의 배포 유형을 대체할 새 배포 유형을 지정할 수 있습니다. 또한 대체 애플리케이션을 설치하기 전에 대체 대상 애플리케이션을 업그레이드할지 아니면 제거할지를 설정할 수 있습니다.  

  자세한 내용은 [애플리케이션 대체](revise-and-supersede-applications.md#application-supersedence)를 참조하세요.  

- **애플리케이션 제거**. Configuration Manager를 사용하면 쉽게 애플리케이션을 제거할 수 있습니다. 이 작업은 애플리케이션 또는 디바이스 사용자의 개입 없이 자동으로 수행됩니다.  

  자세한 내용은 [애플리케이션 제거](uninstall-applications.md)를 참조하세요.  
