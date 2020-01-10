---
title: 애플리케이션 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 응용 프로그램을 관리 합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f31de77387e4203840b1a93169321c66013da6cf
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75826835"
---
# <a name="manage-applications-in-configuration-manager"></a>Configuration Manager에서 응용 프로그램 관리

*적용 대상: Configuration Manager (현재 분기)*

Microsoft Intune 또는 Configuration Manager 온-프레미스 디바이스 관리를 통해 디바이스를 관리하는 경우 다음과 같은 추가 애플리케이션 유형을 관리할 수 있습니다.
- Windows Phone 앱 패키지(*.xap 파일)
- iOS용 앱 패키지(*.ipa 파일)
- Android용 앱 패키지(*.apk 파일)
- Google Play의 Android용 앱 패키지
- Windows Phone 앱 패키지(Windows Phone 스토어)
- MDM을 사용하는 Windows Installer
- 웹 애플리케이션

이 섹션에서는 하이브리드 MDM 또는 온-프레미스 MDM을 사용하여 애플리케이션을 만들고 관리하는 방법에 대한 자세한 정보를 제공합니다.

[Configuration Manager 응용 프로그램에 대 한 관리 작업](../../apps/deploy-use/management-tasks-applications.md) 은 Configuration Manager 응용 프로그램 및 배포 유형 관리에 대 한 보다 일반적인 정보를 제공 합니다.

## <a name="deploying-and-monitoring-apps"></a>앱 배포 및 모니터링

Configuration Manager에서 응용 프로그램을 배포 하 고 모니터링 하는 것은 랩톱, 데스크톱 등의 온사이트 장치에 대 한 모바일 장치에 대 한 프로세스와 동일 합니다. 애플리케이션 배포 및 모니터링에 대한 일반적인 내용은 다음 항목에서 확인할 수 있습니다.

- [애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)
- [애플리케이션 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)

다음은 애플리케이션을 배포하고 모니터링할 때 염두에 두어야 하는 모바일 디바이스 관리에 특정한 몇 가지 고려 사항입니다.

- MDM에 등록된 디바이스는 시뮬레이트된 배포, 사용자 환경 또는 일정 설정을 지원하지 않습니다.

- 단일 앱에 100 개 이상의 로캘을 추가 하지 마세요. 100 개를 초과 하는 로캘을 추가 하면 앱이 Intune과 동기화 되지 않습니다. 이 작업을 수행 하면 앱이 장치에 설치 되거나 설치 되는 것을 방지할 수도 있습니다.

- iOS 응용 프로그램 구성 정책을 이미 구성한 경우 이 정책에 배포를 연결할 수 있습니다. [앱 구성 정책을 사용하여 iOS 앱 구성](configure-ios-apps-with-app-configuration-policies.md)을 참조하세요.

### <a name="next-steps"></a>다음 단계

나중에 애플리케이션을 변경하거나, 애플리케이션을 제거하거나, 이미 배포된 애플리케이션을 새 애플리케이션으로 대체할 수 있습니다. 이러한 기능을 이해 하려면 [Configuration Manager를 사용 하 여 응용 프로그램 업데이트 및 사용 중지](../../apps/deploy-use/update-and-retire-applications.md) 를 참조 하세요.
