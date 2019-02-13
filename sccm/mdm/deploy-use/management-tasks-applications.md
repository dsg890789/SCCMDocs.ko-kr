---
title: 애플리케이션 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 애플리케이션 관리
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4ff166d93812b07c37c31228ca395f0cfcf94de6
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56156960"
---
# <a name="manage-applications-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 애플리케이션 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 또는 Configuration Manager 온-프레미스 장치 관리를 통해 장치를 관리하는 경우 다음과 같은 추가 애플리케이션 유형을 관리할 수 있습니다.
- Windows Phone 앱 패키지(*.xap 파일)
- iOS용 앱 패키지(*.ipa 파일)
- Android용 앱 패키지(*.apk 파일)
- Google Play의 Android용 앱 패키지
- Windows Phone 앱 패키지(Windows Phone 스토어)
- MDM을 사용하는 Windows Installer
- 웹 애플리케이션

이 섹션에서는 하이브리드 MDM 또는 온-프레미스 MDM을 사용하여 애플리케이션을 만들고 관리하는 방법에 대한 자세한 정보를 제공합니다.

[System Center Configuration Manager 애플리케이션에 대한 관리 작업](../../apps/deploy-use/management-tasks-applications.md)에서는 System Center Configuration Manager 애플리케이션 및 배포 유형을 관리하는 방법에 대한 보다 일반적인 정보를 제공합니다.

## <a name="deploying-and-monitoring-apps"></a>앱 배포 및 모니터링

System Center Configuration Manager에서 애플리케이션을 배포하고 모니터링하는 프로세스는 해당 애플리케이션이 랩톱 및 데스크톱과 같은 온사이트 장치용이므로 모바일 장치에 대한 프로세스와 동일합니다. 애플리케이션 배포 및 모니터링에 대한 일반적인 내용은 다음 항목에서 확인할 수 있습니다.

- [System Center Configuration Manager에서 애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)
- [System Center Configuration Manager에서 애플리케이션 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)

다음은 애플리케이션을 배포하고 모니터링할 때 염두에 두어야 하는 모바일 장치 관리에 특정한 몇 가지 고려 사항입니다.

- MDM에 등록된 디바이스는 시뮬레이트된 배포, 사용자 환경 또는 일정 설정을 지원하지 않습니다.

- iOS 응용 프로그램 구성 정책을 이미 구성한 경우 이 정책에 배포를 연결할 수 있습니다. [앱 구성 정책을 사용하여 iOS 앱 구성](configure-ios-apps-with-app-configuration-policies.md)을 참조하세요.

### <a name="next-steps"></a>다음 단계

나중에 애플리케이션을 변경하거나, 애플리케이션을 제거하거나, 이미 배포된 애플리케이션을 새 애플리케이션으로 대체할 수 있습니다. 이러한 기능은 [System Center Configuration Manager를 사용하여 애플리케이션 업데이트 및 사용 중지](../../apps/deploy-use/update-and-retire-applications.md)를 참조하세요.
