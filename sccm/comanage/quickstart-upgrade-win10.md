---
title: Windows 10 업그레이드
titleSuffix: Configuration Manager
description: Windows 10 버전 1709 장치를 업그레이드 하거나 공동 관리에는 나중에
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 561eb5b6-f90c-485a-91c2-e45bb0ce7877
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0815a974f3b1f29f664a2948eed33de24c6ecff3
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755298"
---
# <a name="upgrade-windows-10-for-co-management"></a>공동 관리를 위해 Windows 10 업그레이드

공동 관리에 조직 온 보 딩으로 작업 하는 동안 일부 고객에 게 큰 장애물이 현재 시작 합니다. 공동 관리에 필요 [Windows 10 버전 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 이상. Windows 업데이트를 자동 등록 구성 되 면 클라이언트 공동 관리에 자동으로 등록 됩니다.

다음 비디오에서는 수석 프로그램 관리자 Rob York 및 제품 마케팅 관리자 Locky Ainley 설명 및 공동 관리를 위해 Windows 10으로 업그레이드 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Upgrading-to-Windows-10-to-Enable-Co-Management/player]



## <a name="why-upgrade"></a>업그레이드가 필요한 이유

다른 플랫폼 향상 된 기능 중 Windows 10 버전 1709 이상 자동 등록을 지원합니다. 이 동작은 자동으로 Azure Active Directory (Azure AD)를 조인 하는 경우 Intune에 등록 된 장치를 만듭니다. 

자세한 내용은 [을 사용 하도록 설정 하는 Windows 10 자동 등록](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)합니다.


## <a name="how-to-do-it"></a>작업을 수행 하는 방법

다음은 수천 명의 고객이 현재 신속 하면서 알게 몇 가지 팁입니다.

- 단계적된 배포를 사용 하 여 오른쪽에 있는 적합 한 사람을이 업그레이드를 롤아웃 하려면 시간입니다. 자세한 내용은 [단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)를 참조하세요.  

- 사용자 대기 시간을 줄이기 위해 사전 캐시를 사용 합니다. 자세한 내용은 [사전 캐시 콘텐츠 구성](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)을 참조하세요.  

- 기본 전체 업그레이드 작업 순서 템플릿을 사용 합니다. 전처리 및 후 업그레이드 단계 및 오류 동작을 구성 합니다. 자세한 내용은 [사후 처리에 대 한 작업 순서 단계를 권장](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#recommended-task-sequence-steps-for-post-processing)합니다.  

- 환경의 모바일 작업자를 있으면 Configuration Manager 클라우드 관리 게이트웨이 (CMG)를 통해 현재 위치 업그레이드를 지원 합니다. 이 기능을 사용 하면 인터넷을 기반으로 하는 것이 있을 때 Windows 10 클라이언트를 업그레이드할 수 있습니다. CMG에 대 한 자세한 내용은 참조 하세요. [ ](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)합니다.  

- 얼 리 어 되도록 하려는 사용자에 대 한 공동 관리 하는 옵트인 제공 합니다. 이 방법은 초기 도입을 가속화합니다. 이러한 사용자를 사전에 식별 하 여 올바른 있는지 검사는 출시의 초기에 만들 수 있습니다. 또한 변경 만족 하며 더 자주 릴리스 관심이 있는 사용자의 유효성 검사 및 피드백 나타납니다. 새로운 기술에 관심을 생성 하 고 크기가 시간이 지남에 따라 증가 하는 초기 얼 리 어댑터 프로그램입니다.  


## <a name="case-studies"></a>사례 연구

Microsoft IT microsoft 96,000 분산된 사용자에 게 Windows 10을 배포 합니다. 배포에는 원격 사용자와 회사 네트워크의 사용자가 포함 되어 있습니다. 9 개의 주 후에 완료 된 배포 합니다. 경험에 대 한 자세한 내용은 참조 하세요. [현재 위치 업그레이드로는 Microsoft에서 Windows 10 배포](https://www.microsoft.com/download/details.aspx?id=50377)합니다.  

대규모 유럽 소프트웨어 제조업체는 초기 도입자로 서 그룹을 성공적으로 사용합니다. 초기 테스트 및 파일럿 그룹, 후 약 2,000 직원 첫 번째 업데이트, 업그레이드 및 소프트웨어를 수신 합니다. 이 그룹에는 IT 직원 및 옵트인 지원자 포함 됩니다. 이 수준의 사용자에 게 참여 하면 장치를 더 높은 수준의 신뢰도 테스트할 때 및 자세한 신뢰도 대용량 롤아웃을 시작 합니다.



## <a name="contact-fasttrack"></a>FastTrack에 문의 하세요

언제 든 지 프로세스에서 Windows 10 업그레이드를 사용 하 여 도움이 필요 하면로 이동 [Microsoft FastTrack](https://Microsoft.com/FastTrack/), 로그인 및 지원을 요청 합니다. 

자세한 내용은 [FastTrack에서 도움말을 얻고](/sccm/comanage/quickstart-fasttrack)합니다. 

