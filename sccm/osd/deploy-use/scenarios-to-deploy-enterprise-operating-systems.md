---
title: 엔터프라이즈 운영 체제를 배포하는 시나리오
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 엔터프라이즈 운영 체제를 배포하는 여러 시나리오에 대해 알아봅니다.
ms.date: 02/22/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: f74fdb86-c7c2-447f-91f6-b42df6370d7f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f6d34c3d8dfa753934f03337d68e989a8bf8fcd7
ms.sourcegitcommit: ef2960bd91655c741450774e512dd0a9be610625
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56838704"
---
# <a name="scenarios-to-deploy-enterprise-operating-systems-with-configuration-manager"></a>Configuration Manager를 사용하여 엔터프라이즈 운영 체제를 배포하는 시나리오

*적용 대상: System Center Configuration Manager(현재 분기)*

다음 OS 배포 시나리오를 Configuration Manager에서 사용할 수 있습니다.  

#### <a name="upgrade-windows-to-the-latest-version"></a>최신 버전으로 Windows 업그레이드
이 시나리오에서는 현재 Windows 7, Windows 8.1 또는 Windows 10을 실행하는 컴퓨터의 OS를 업그레이드합니다. 이 업그레이드 프로세스는 컴퓨터의 애플리케이션, 설정 및 사용자 데이터를 그대로 유지합니다. Windows ADK와 같은 외부 종속성이 없습니다. 이 프로세스를 사용하면 기존 OS 배포보다 속도 및 복원력을 더 향상시킬 수 있습니다.  

자세한 내용은 [최신 버전으로 Windows 업그레이드](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version)를 참조하세요.


#### <a name="windows-autopilot-for-existing-devices"></a>기존 디바이스에 대한 Windows Autopilot
<!--3607717, fka 1358333--> 버전 1810부터 기존 디바이스에 대한 Windows Autopilot은 Windows 10 버전 1809 이상에서 사용할 수 있습니다. 이 기능을 사용하면 단일 Configuration Manager 작업 순서를 사용하여 Windows Autopilot 사용자 기반 모드용으로 Windows 7 디바이스를 이미지로 다시 설치하고 프로비전할 수 있습니다.

자세한 내용은 [기존 디바이스에 대한 Windows Autopilot](/sccm/osd/deploy-use/windows-autopilot-for-existing-devices)을 참조하세요.


#### <a name="refresh-an-existing-computer-with-a-new-version-of-windows"></a>새 버전의 Windows로 기존 컴퓨터 새로 고침
이 시나리오에서는 기존 컴퓨터를 파티션으로 나누고 포맷(초기화)한 다음, 해당 컴퓨터에 새 OS를 설치합니다. OS가 설치된 후 설정 및 사용자 데이터를 마이그레이션할 수 있습니다.  

자세한 내용은 [새 버전의 Windows로 기존 컴퓨터 새로 고침](/sccm/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)을 참조하세요.


#### <a name="install-a-new-version-of-windows-on-a-new-computer-bare-metal"></a>새 컴퓨터에 새 버전의 Windows 설치(완전 복구)
이 시나리오에서는 새 컴퓨터에 OS를 설치합니다. 이 시나리오를 사용하면 OS가 새로 설치되며 설정 또는 사용자 데이터 마이그레이션은 포함되지 않습니다.  

자세한 내용은 [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](/sccm/osd/deploy-use/install-new-windows-version-new-computer-bare-metal)를 참조하세요.


#### <a name="replace-an-existing-computer-and-transfer-settings"></a>기존 컴퓨터 바꾸기 및 설정 전송
이 시나리오에서는 새 컴퓨터에 OS를 설치합니다. 필요에 따라 이전 컴퓨터의 설정 및 사용자 데이터를 새 컴퓨터로 마이그레이션할 수 있습니다.  

자세한 내용은 [기존 컴퓨터 바꾸기 및 설정 전송](/sccm/osd/deploy-use/replace-an-existing-computer-and-transfer-settings)을 참조하세요.


