---
title: Windows 10 업그레이드
titleSuffix: Configuration Manager
description: 공동 관리에 필요한 Windows 10 버전 1709 이상으로 디바이스 업그레이드
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 561eb5b6-f90c-485a-91c2-e45bb0ce7877
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bbc042975840e5b4e840928f01257785f4859dd4
ms.sourcegitcommit: 18ad7686d194d8cc9136a761b8153a1ead1cdc6b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66176834"
---
# <a name="upgrade-windows-10-for-co-management"></a>공동 관리를 위해 Windows 10 업그레이드

공동 관리에 조직을 등록하는 작업을 할 때 일부 고객에게는 최신 상태로 업그레이드하는 일이 상당한 난관입니다. 공동 관리에는 [Windows 10 버전 1709](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) 이상이 필요합니다. Windows를 업데이트하고 자동 등록을 구성하면 클라이언트가 공동 관리에 자동으로 등록됩니다.

다음 비디오에서는 수석 프로그램 관리자 Rob York와 제품 마케팅 관리자 Locky Ainley가 공동 관리를 위해 Windows 10으로 업그레이드에 관해 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Upgrading-to-Windows-10-to-Enable-Co-Management/player]



## <a name="why-upgrade"></a>업그레이드 이유

Windows 10 버전 1709 이상에서는 향상된 다른 플랫폼 기능 외에 자동 등록을 지원합니다. 이 동작을 통해 디바이스가 Azure AD(Azure Active Directory)에 가입되면 Intune에 자동으로 등록됩니다. 

자세한 내용은 [Windows 10 자동 등록 사용](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment)을 참조하세요.


## <a name="how-to-do-it"></a>방법

다음은 수천 명의 고객이 최신 상태로 빠르게 업그레이드하도록 도우면서 배운 몇 가지 팁입니다.

- 단계적 배포를 사용하여 이 업그레이드를 적합한 사용자에게 적절한 시기에 배포합니다. 자세한 내용은 [단계적 배포 만들기](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)를 참조하세요.  

- 사전 캐싱을 사용하여 사용자 대기 시간을 줄입니다. 자세한 내용은 [사전 캐시 콘텐츠 구성](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)을 참조하세요.  

- 기본 현재 위치 업그레이드 작업 순서 템플릿을 사용합니다. 그런 다음 업그레이드 전후를 위한 단계와 오류 동작을 구성합니다. 자세한 내용은 [사후 처리를 위한 권장되는 작업 순서 단계](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#recommended-task-sequence-steps-for-post-processing)를 참조하세요.  

- 외근이 잦은 모바일 인력이 있는 환경을 위해 Configuration Manager에서는 CMG(클라우드 관리 게이트웨이)를 통한 현재 위치 업그레이드를 지원합니다. 이 기능을 사용하면 인터넷 기반의 Windows 10 클라이언트를 업그레이드할 수 있습니다. CMG에 대한 자세한 내용은 [](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)을(를) 참조하세요.  

- 얼리어답터가 되기를 원하는 사용자에게는 공동 관리로 옵트인을 제공합니다. 이 접근 방식은 초기 채택을 앞당깁니다. 이러한 사용자를 사전에 식별하면 출시 초기에 혜택 범위를 늘릴 수 있습니다. 또한 변경에 만족하고 더 빈번한 출시에 관심이 있는 사용자의 검증과 의견을 받을 수 있습니다. 얼리어답터 프로그램은 새로운 기술에의 관심을 불러일으키고 시간에 따라 규모가 커집니다.  


## <a name="case-studies"></a>사례 연구

Microsoft IT는 Microsoft의 96,000명 분산 사용자에게 Windows 10을 배포했습니다. 이 배포에는 원격 사용자와 회사 네트워크의 사용자가 모두 포함되었습니다. 이 배포는 9주 이내에 완료되었습니다. Microsoft IT의 경험에 대한 자세한 내용은 [Microsoft에서 현재 위치 업그레이드로 Windows 10 배포](https://www.microsoft.com/itshowcase/deploying-windows-10-at-microsoft-as-an-in-place-upgrade)를 참조하세요.  

유럽의 한 대형 소프트웨어 제조업체는 얼리어답터 그룹을 성공적으로 사용합니다. 초기 테스트와 그룹 파일럿 실행 후 약 2,000명의 직원이 첫 번째 업데이트, 업그레이드 및 소프트웨어를 받습니다. 이 그룹에는 IT 직원과 옵트인 지원자가 포함됩니다. 사용자와의 이러한 수준의 참여를 통해 테스트할 때 신뢰 수준을 향상하고 대규모 출시를 시작할 때 신뢰도도 향상합니다.



## <a name="contact-fasttrack"></a>FastTrack에 문의

진행 도중 언제든 Windows 10 업그레이드 관련 지원이 필요하면 [Microsoft FastTrack](https://Microsoft.com/FastTrack/)으로 이동하여 로그인하고 지원을 요청하세요. 

자세한 내용은 [Get help from FastTrack](/sccm/comanage/quickstart-fasttrack)(FastTrack에서 도움받기)을 참조하세요. 

