---
title: 공동 관리를 사용 하 여 연결 하는 클라우드
titleSuffix: Configuration Manager
description: 공동 관리는 사용 하도록 설정 하면 즉각적인 가치를 제공 합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 8d878443-90e7-46e4-9cd3-99e2a19b2ad0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ed92d6249e4459f1902f639840b142977994df9e
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755355"
---
# <a name="cloud-connecting-with-co-management"></a>공동 관리를 사용 하 여 연결 하는 클라우드

![Blastoff 시리즈 배너](media/blastoff-banner.png)

공동 관리를 사용 하면 기존 Configuration Manager 배포에 새 기능을 추가 하는 이미 작동 하는 방법을 변경 하지 않고 있습니다. 공동 관리를 사용 하도록 설정 하면 즉시 클라우드에서 애플리케이션을 합니다. 기존 관리 인프라 및 프로세스에 해당 값을 적용할 수 있습니다.

공동 관리 빠른 시작 시리즈에서는 새 관리 값을 신속 하 게 실현할 수 있습니다 하는 방법을 참조 하세요. 공동 관리 기능을 만들고 지금 바로 사용할 수 있는 도구에 빌드됩니다.


다음 비디오에서 Microsoft 회사 부사장 인 Brad Anderson이 공동 관리 시리즈를 제공합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Cloud-Connecting-with-Co-Management/player]


| 즉치 값 | 시작 |
|-----------------|-----------------|
| - [조건부 액세스](#bkmk_ca)<br> - [Intune에서 원격 작업](#bkmk_remote)<br> - [클라이언트 상태](#bkmk_client-health)<br> - [Hybrid Azure AD](#bkmk_hybrid-aad)<br> - [Windows Autopilot](#bkmk_autopilot) | - [공동 관리에 대 한 경로](#bkmk_paths)<br> - [하이브리드 Azure AD 설정](#bkmk_setup-hybrid-aad)<br> - [Windows 10으로 업그레이드](#bkmk_upgrade-win10)<br> - [하이브리드 MDM에서 마이그레이션](#bkmk_migrate-hybrid-mdm)<br> - [FastTrack에서 도움 받기](#bkmk_fasttrack) | 



## <a name="immediate-value"></a>즉치 값

| | | |
|-|-|-|
| <a name="bkmk_ca"></a>**장치 준수를 사용 하 여 조건부 액세스** | Intune에서 규정 준수 규칙에 따라 회사 리소스에 대 한 사용자 액세스 제어 | [![조건부 액세스 비디오 썸네일](media/thumbnail-conditional-access.png)](/sccm/comanage/quickstart-conditional-access) |
| <a name="bkmk_remote"></a>**Intune에서 원격 작업** | Intune에서 공동 관리 장치에 대 한 원격 작업을 실행 합니다. 예를 들어, 초기화 및 장치를 다시 설정 및 등록 및 계정 유지 관리 | [![원격 작업 비디오의 미리 보기](media/thumbnail-remote-action.png)](/sccm/comanage/quickstart-remote-actions) |
| <a name="bkmk_client-health"></a>**Configuration Manager 클라이언트 상태** | Azure portal의 Intune에서 Configuration Manager 클라이언트 상태 표시를 유지 관리 | [![클라이언트 상태 비디오의 미리 보기](media/thumbnail-client-health.png)](/sccm/comanage/quickstart-client-health) |
| <a name="bkmk_hybrid-aad"></a>**Azure Active Directory (Azure AD)** | Azure AD를 사용 하 여 있습니다 활용 향상 된 생산성의 사용자 및 보안에 대 한 리소스에 대 한 클라우드 및 온-프레미스 환경에서 | [![하이브리드 Azure AD 비디오 썸네일](media/thumbnail-azure-ad.png)](/sccm/comanage/quickstart-hybrid-aad) |
| <a name="bkmk_autopilot"></a>**Windows Autopilot** | 시간, 리소스 및 관련 배포, 관리 및 사용 중지 하거나 장치를 재활용 된 복잡성을 줄입니다. Autopilot 최종 사용자는 더 나은 환경을 만듭니다. | [![Windows Autopilot 비디오 썸네일](media/thumbnail-autopilot.png)](/sccm/comanage/quickstart-autopilot) |



## <a name="getting-started"></a>시작

공동 관리를 사용 하도록 설정 하려는 경우 했을 수 있습니다 기술적인 문제 차단을 해제 하려면 여기서 시작 합니다.

| | | |
|-|-|-|
| <a name="bkmk_paths"></a>**공동 관리에 대 한 경로** | 두 가지 기본 공동 관리를 설정 하 고 각 경로 대 한 필수 구성 요소를 이해 해야 합니다.  각 경로 필요한 Azure AD의 몇 가지 조합 ConfigMgr, Intune 및 Windows 클라이언트입니다. | [![공동 관리 경로 슬라이드의 미리 보기](media/thumbnail-paths.png)](/sccm/comanage/quickstart-paths) |
| <a name="bkmk_setup-hybrid-aad"></a>**하이브리드 Azure AD 설정** | 사용자 환경에는 현재 도메인에 가입 된 Windows 10 장치에, 경우 공동 관리를 사용 하려면 먼저 Azure AD 하이브리드 설정 | [![하이브리드 Azure AD의 미리 보기 비디오를 설정](media/thumbnail-setup-azure-ad.png)](/sccm/comanage/quickstart-setup-hybrid-aad) |
| <a name="bkmk_upgrade-win10"></a>**Windows 10으로 업그레이드** | 공동 관리를 위해 Windows 10 버전 1709 이상이 필요 | [![업그레이드 하는 Windows 10 비디오 썸네일](media/thumbnail-upgrade-win10.png)](/sccm/comanage/quickstart-upgrade-win10) |
| <a name="bkmk_migrate-hybrid-mdm"></a>**하이브리드 MDM에서 마이그레이션** | 하이브리드 MDM (Configuration Manager와 통합 된 Intune)는 사용 되지 않습니다. Intune 독립 실행형은 공동 관리를 위해 필요 합니다. | [![미리 보기 마이그레이션 하이브리드 MDM 비디오](media/thumbnail-migrate-hybrid-mdm.png)](/sccm/comanage/quickstart-migrate-hybrid-mdm) |
| <a name="bkmk_fasttrack"></a>**FastTrack에서 도움 받기** | FastTrack 구성은 모든 유형의 조직 공동 관리를 설정 하는 등 Microsoft 365 앱을 배포할 수 있도록 지 원하는 전문 Microsoft 엔지니어의 큰 그룹입니다. | [![FastTrack 비디오 썸네일](media/thumbnail-fasttrack.png)](/sccm/comanage/quickstart-fasttrack) |

