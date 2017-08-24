---
title: "System Center Configuration Manager에서 응용 프로그램 관리 | Microsoft Docs"
description: "System Center Configuration Manager에서 응용 프로그램 관리"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: bc7bb99bc526ed0bbaaad15fc9af39fa8b7c3893
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="manage-applications-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 응용 프로그램 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 또는 Configuration Manager 온-프레미스 장치 관리를 통해 장치를 관리하는 경우 다음과 같은 추가 응용 프로그램 유형을 관리할 수 있습니다.
- Windows Phone 앱 패키지(*.xap 파일)
- iOS용 앱 패키지(*.ipa 파일)
- Android용 앱 패키지(*.apk 파일)
- Google Play의 Android용 앱 패키지
- Windows Phone 앱 패키지(Windows Phone 스토어)
- MDM을 사용하는 Windows Installer
- 웹 응용 프로그램

이 섹션에서는 하이브리드 MDM 또는 온-프레미스 MDM을 사용하여 응용 프로그램을 만들고 관리하는 방법에 대한 자세한 정보를 제공합니다.

[System Center Configuration Manager 응용 프로그램에 대한 관리 작업](../../apps/deploy-use/management-tasks-applications.md)에서는 System Center Configuration Manager 응용 프로그램 및 배포 유형을 관리하는 방법에 대한 보다 일반적인 정보를 제공합니다.

## <a name="deploying-and-monitoring-apps"></a>앱 배포 및 모니터링

System Center Configuration Manager에서 응용 프로그램을 배포하고 모니터링하는 프로세스는 해당 응용 프로그램이 랩톱 및 데스크톱과 같은 온사이트 장치용이므로 모바일 장치에 대한 프로세스와 동일합니다. 응용 프로그램 배포 및 모니터링에 대한 일반적인 내용은 다음 항목에서 확인할 수 있습니다.

- [System Center Configuration Manager에서 응용 프로그램 배포](../../apps/deploy-use/deploy-applications.md)
- [System Center Configuration Manager에서 응용 프로그램 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)

다음은 응용 프로그램을 배포하고 모니터링할 때 염두에 두어야 하는 모바일 장치 관리에 특정한 몇 가지 고려 사항입니다.

- MDM에 등록된 장치는 시뮬레이트된 배포, 사용자 환경 또는 일정 설정을 지원하지 않습니다.

- iOS 응용 프로그램 구성 정책을 이미 구성한 경우 이 정책에 배포를 연결할 수 있습니다. [앱 구성 정책을 사용하여 iOS 앱 구성](configure-ios-apps-with-app-configuration-policies.md)을 참조하세요.

### <a name="next-steps"></a>다음 단계

나중에 응용 프로그램을 변경하거나, 응용 프로그램을 제거하거나, 이미 배포된 응용 프로그램을 새 응용 프로그램으로 대체할 수 있습니다. 이러한 기능은 [System Center Configuration Manager를 사용하여 응용 프로그램 업데이트 및 사용 중지](../../apps/deploy-use/update-and-retire-applications.md)를 참조하세요.
