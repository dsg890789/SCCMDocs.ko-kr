---
title: 온-프레미스 MDM에 대 한 앱 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)에 대 한 응용 프로그램을 관리 합니다.
ms.date: 01/13/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 660975049ef91ad19e08eb18fa6c557106fbe783
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76032695"
---
# <a name="manage-apps-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 앱 관리

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 장치를 관리 하는 경우 다음 응용 프로그램 유형을 관리할 수 있습니다.

- Windows Phone 앱 패키지(*.xap 파일)
- Windows Phone 앱 패키지(Windows Phone 스토어)
- MDM을 사용하는 Windows Installer
- 웹 애플리케이션

Configuration Manager 응용 프로그램 및 배포 유형을 관리 하는 방법에 대 한 일반적인 내용은 [Configuration Manager 응용 프로그램에 대 한 관리 작업](/configmgr/apps/deploy-use/management-tasks-applications)을 참조 하세요.

## <a name="bkmk_winphone"></a>Windows Phone 응용 프로그램 만들기

Configuration Manager 애플리케이션에는 하나 이상의 배포 유형이 있습니다. 배포 유형에는 소프트웨어를 디바이스에 배포하는 데 필요한 설치 파일 및 정보가 포함됩니다. 또한 배포 유형에는 소프트웨어 배포 시점 및 방법을 지정하는 규칙이 포함됩니다.

앱 및 배포 유형을 만드는 일반적인 단계는 [응용 프로그램 만들기](/configmgr/apps/deploy-use/create-applications#bkmk_create)를 참조 하세요.

Configuration Manager은 Windows mobile 장치에 대해 다음과 같은 앱 파일 형식을 지원 합니다.

|디바이스 유형|지원되는 파일 형식|
|-----------------|---------------------|
|Windows Phone 8|xap|
|WVPN 프로필dows Phone 8.1|xap, appx, appxbundle|
|Windows 10 Mobile|xap, appx, appxbundle|

Windows Phone 응용 프로그램은 **사용 가능** 또는 **필수**로 배포되며, 응용 프로그램을 제거하는 데에도 이 배포를 사용합니다.

## <a name="deploy-and-monitor-apps"></a>앱 배포 및 모니터링

데스크톱 및 서버와 같은 다른 장치에서 수행 하는 것과 동일 하 게 Configuration Manager에서 모바일 장치용 응용 프로그램을 배포 하 고 모니터링할 수 있습니다. 자세한 내용은 다음 아티클을 참조하세요.

- [애플리케이션 배포](/configmgr/apps/deploy-use/deploy-applications)
- [애플리케이션 모니터링](/configmgr/apps/deploy-use/monitor-applications-from-the-console)

모바일 장치와 관련 하 여 다음과 같은 제한 사항을 검토 합니다.

- MDM에 등록된 디바이스는 시뮬레이트된 배포, 사용자 환경 또는 일정 설정을 지원하지 않습니다.

- 단일 앱에 100 개 이상의 로캘을 추가 하지 마세요. 이 작업을 수행 하면 앱이 장치에 설치 되지 않습니다.

## <a name="next-step"></a>다음 단계

배포 된 응용 프로그램을 변경 하거나 제거 하거나 새 응용 프로그램으로 교체 하려면 Configuration Manager의 모든 앱과 동일 하 게 관리 합니다. 자세한 내용은 [애플리케이션 업데이트 및 사용 중지](/configmgr/apps/deploy-use/update-and-retire-applications)를 참조하세요.
