---
title: 공동 관리에 연결된 클라우드
titleSuffix: Configuration Manager
description: 공동 관리는 사용하도록 설정하면 즉치 값을 제공합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 8d878443-90e7-46e4-9cd3-99e2a19b2ad0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 29d91b7b915a381be1ea26f1f0b4fa4395c99dcb
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75816941"
---
# <a name="cloud-connecting-with-co-management"></a>공동 관리에 연결된 클라우드

![Blastoff 시리즈 배너](media/blastoff-banner.png)

공동 관리는 이미 작업하는 방식을 변경하지 않고 기존 Configuration Manager 배포에 새 기능을 추가합니다. 공동 관리를 사용하도록 설정하면 즉시 클라우드를 활용할 수 있습니다. 이 가치를 기존 관리 인프라와 프로세스에 적용할 수 있습니다.

이 공동 관리 빠른 시작 시리즈에서 새로운 관리 가치를 창출하는 방법을 확인하세요. 공동 관리는 지금 바로 사용할 수 있는 기능과 도구를 만들기 위해 설계되었습니다.


다음 비디오에서는 Microsoft 부사장 Brad Anderson이 다음 공동 관리 시리즈를 소개합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Cloud-Connecting-with-Co-Management/player]


| 즉치 값 | 시작하기 |
|-----------------|-----------------|
| - [조건부 액세스](#bkmk_ca)<br> - [Intune에서 원격 작업](#bkmk_remote)<br> - [클라이언트 상태](#bkmk_client-health)<br> - [하이브리드 Azure AD](#bkmk_hybrid-aad)<br> - [Windows Autopilot](#bkmk_autopilot) | - [공동 관리 경로](#bkmk_paths)<br> - [하이브리드 Azure AD 설정](#bkmk_setup-hybrid-aad)<br> - [Windows 10으로 업그레이드](#bkmk_upgrade-win10)<br> - [하이브리드 MDM에서 마이그레이션](#bkmk_migrate-hybrid-mdm)<br> - [FastTrack에서 도움받기](#bkmk_fasttrack) | 



## <a name="immediate-value"></a>즉치 값

| | | |
|-|-|-|
| <a name="bkmk_ca"></a>**디바이스 준수를 사용한 조건부 액세스** | Intune의 준수 규칙에 따라 회사 리소스에 대한 사용자 액세스 제어 | [![조건부 액세스 비디오 썸네일](media/thumbnail-conditional-access.png)](/sccm/comanage/quickstart-conditional-access) |
| <a name="bkmk_remote"></a>**Intune에서 원격 작업** | Intune에서 공동 관리하는 디바이스의 원격 작업 실행. 예: 디바이스 초기화 및 재설정과 등록 및 계정 유지 관리 | [![원격 작업 비디오 썸네일](media/thumbnail-remote-action.png)](/sccm/comanage/quickstart-remote-actions) |
| <a name="bkmk_client-health"></a>**Configuration Manager 클라이언트 상태** | Azure Portal의 Intune에서 Configuration Manager 클라이언트 상태의 표시 여부 관리 | [![클라이언트 상태 비디오 썸네일](media/thumbnail-client-health.png)](/sccm/comanage/quickstart-client-health) |
| <a name="bkmk_hybrid-aad"></a>**Azure AD(Azure Active Directory)** | Azure AD를 사용하면 클라우드와 온-프레미스 환경 모두에서 사용자의 생산성과 리소스의 보안을 향상할 수 있음 | [![하이브리드 Azure AD 비디오 썸네일](media/thumbnail-azure-ad.png)](/sccm/comanage/quickstart-hybrid-aad) |
| <a name="bkmk_autopilot"></a>**Windows Autopilot** | 디바이스 배포, 관리 및 사용 중지 또는 재생과 관련된 시간, 리소스 및 복잡성 줄임. Autopilot은 최종 사용자의 환경을 향상하기도 함 | [![Windows Autopilot 비디오 썸네일](media/thumbnail-autopilot.png)](/sccm/comanage/quickstart-autopilot) |



## <a name="getting-started"></a>시작하기

공동 관리를 사용하도록 설정하려면 먼저 아래의 기술 요구 사항을 확인하고 필요한 지원을 받으세요.

| | | |
|-|-|-|
| <a name="bkmk_paths"></a>**공동 관리 경로** | 공동 관리를 설정하는 두 가지 기본 방법이 있으며 각 경로의 필수 조건을 이해하는 것이 중요합니다.  각 경로에는 Azure AD, ConfigMgr, Intune 및 Windows 클라이언트의 몇 가지 조합이 필요합니다. | [![공동 관리 경로 슬라이드 썸네일](media/thumbnail-paths.png)](/sccm/comanage/quickstart-paths) |
| <a name="bkmk_setup-hybrid-aad"></a>**하이브리드 Azure AD 설정** | 사용자 환경에 현재 도메인에 가입된 Windows 10 디바이스가 있는 경우 공동 관리를 사용하도록 설정하려면 먼저 하이브리드 Azure AD를 설정합니다. | [![하이브리드 Azure AD 설정 비디오 썸네일](media/thumbnail-setup-azure-ad.png)](/sccm/comanage/quickstart-setup-hybrid-aad) |
| <a name="bkmk_upgrade-win10"></a>**Windows 10으로 업그레이드** | 공동 관리에는 Windows 10 버전 1709 이상이 필요합니다. | [![Windows 10 업그레이드 비디오 썸네일](media/thumbnail-upgrade-win10.png)](/sccm/comanage/quickstart-upgrade-win10) |
| <a name="bkmk_migrate-hybrid-mdm"></a>**하이브리드 MDM에서 마이그레이션** | 하이브리드 MDM(Configuration Manager와 통합된 Intune)은 사용되지 않습니다. 공동 관리를 위해서는 Intune 독립 실행형이 필요합니다. | [![하이브리드 MDM에서 마이그레이션 비디오 썸네일](media/thumbnail-migrate-hybrid-mdm.png)](/sccm/comanage/quickstart-migrate-hybrid-mdm) |
| <a name="bkmk_fasttrack"></a>**FastTrack에서 도움받기** | FastTrack 조직은 모든 유형의 조직이 공동 관리 설정을 포함하여 Microsoft 365 앱을 배포하도록 돕는 것을 전문으로 하는 대규모 Microsoft 엔지니어 집합입니다. | [![FastTrack 비디오 썸네일](media/thumbnail-fasttrack.png)](/sccm/comanage/quickstart-fasttrack) |

