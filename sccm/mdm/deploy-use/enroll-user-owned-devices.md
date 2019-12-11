---
title: 하이브리드 배포를 위해 사용자 소유의 디바이스 등록
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 하이브리드 배포를 위해 사용자 소유 디바이스를 등록하는 다양한 방법을 알아봅니다.
ms.date: 09/08/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 2bdaa8a7-6a64-4b0e-b617-309dcd912c45
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b6d56309238acc2889ac39ab39d5982fb8d535c
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62282412"
---
# <a name="enroll-user-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Configuration Manager를 사용하는 하이브리드 배포를 위해 사용자 소유 디바이스 등록

*적용 대상: System Center Configuration Manager(현재 분기)*

“자체 디바이스 가져오기(BYOD, Bring Your Own Devices)”라고도 하는 프로세스를 통해 사용자 소유 디바이스를 등록하여 관리로 가져올 수 있습니다. 사용자는 회사 포털 앱을 설치하고 디바이스(iOS, macOS 및 Android)에 로그인하거나, 직장 또는 학교 계정을 디바이스에 추가하고 도메인에 연결하여(Windows) 이 작업을 수행합니다. 이 프로세스에서는 디바이스를 Intune에 등록하여 사용자에게 Intune으로 관리되는 리소스에 대한 액세스를 부여하고 Intune이 PIN 요구 등과 같은 특정 디바이스 설정을 관리하게 합니다.

디바이스를 관리로 가져오려면 먼저 관리자가 [모바일 디바이스 관리를 설정하고](setup-hybrid-mdm.md)[등록을 활성화](enable-platform-enrollment.md)합니다. 등록이 활성화되면 사용자가 자체 디바이스를 등록할 수 있습니다. 사용자와의 공유에 대한 고려 사항과 절차는 [Microsoft Intune에 대한 최종 사용자 교육 방법](https://docs.microsoft.com/intune/end-user-educate)을 참조하세요.

디바이스를 구매한 회사 또는 학교에서는 [회사 소유 디바이스의 관리](enroll-company-owned-devices.md)를 제공하는 프로그램을 활용할 수 있습니다.
