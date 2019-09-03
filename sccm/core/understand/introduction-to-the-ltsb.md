---
title: LTSB 소개
titleSuffix: Configuration Manager
description: Configuration Manager의 장기 서비스 분기 관리에 대해 알아봅니다.
ms.date: 08/23/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 54d8efa798f10bff8bb80fea6aaf2b052c4d1419
ms.sourcegitcommit: 2d38de4846ea47a03cc884cbd3df27db48f64a6a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70109848"
---
# <a name="introduction-to-the-long-term-servicing-branch-of-configuration-manager"></a>Configuration Manager의 장기 서비스 분기 관리 소개

*적용 대상: System Center Configuration Manager(장기 서비스 분기)*

Configuration Manager의 LTSB(장기 서비스 분기)는 모든 고객이 사용할 수 있는 설치 옵션으로 설계된 고유한 분기입니다. 그러나 Configuration Manager에 대한 SA(Software Assurance) 또는 이와 동등한 구독 권한이 없는 고객에게는 유일한 옵션입니다.

Configuration Manager 버전 1606을 기준으로 Configuration Manager의 현재 분기와 비교할 때 LTSB의 기능이 줄어들었습니다.

> [!TIP]   
> Configuration Manager LTSB는 System Center 제품군 장기 서비스 채널(LTSC)과 관련이 없습니다. 자세한 내용은 [System Center 릴리스 옵션 개요](https://docs.microsoft.com/system-center/ltsc-and-sac-overview)를 참조하세요.

## <a name="features-that-arent-available"></a>사용할 수 없는 기능

Configuration Manager의 현재 분기는 LTSB에서는 사용할 수 없는 다음 기능을 지원합니다.

- 새로운 기능과 개선 사항을 추가하는 콘솔 내 업데이트
- 사이트 서버 및 클라이언트로 사용하기 위해 새로 릴리스된 운영 체제에 대한 지원
- Microsoft Intune 구독을 사용하여 다음 지원:
  - 하이브리드 MDM(모바일 디바이스 관리) 구성에서 Intune을 사용할 수 없음
  - 온-프레미스 MDM을 사용할 수 없음
- 최신 Windows 10 버전에 대한 지원을 포함한 Windows 10 서비스 대시보드 및 서비스 계획  
- Windows Server 및 Windows 10 LTSB의 향후 릴리스에 대한 지원
- Asset Intelligence
- 클라우드 기반 배포 지점
- Exchange Connector로 사용되는 Exchange Online    

LTSB에서 이러한 기능에 대한 지원을 사용할 수 없어도 일부 기능은 Configuration Manager 콘솔에 계속 표시됩니다. 하지만 선택하거나 사용할 수는 없습니다.

Configuration Manager 현재 분기 버전 1610 이상에 포함된 모든 기능 및 클라우드 통합은 LTSB에서 사용할 수 없습니다. 이러한 기능에는 다음을 비롯한 여러 가지가 포함됩니다.<!--SCCMDocs#1823-->

- 공동 관리
- Desktop Analytics
- 클라우드 관리 게이트웨이
- Azure Active Directory 통합
- 비즈니스용 Microsoft Store의 앱

## <a name="find-ltsb-documentation"></a>LTSB 설명서 찾기

LTSB는 현재 분기 버전 1606을 기반으로 합니다. LTSB에만 해당하는 주의 사항 및 제한 사항과 함께 [현재 분기 설명서](https://docs.microsoft.com/sccm/)를 사용합니다. 이러한 주의 사항과 제한 사항은 다음 문서에서 확인할 수 있습니다.

- [LTSB 설치](install-the-ltsb.md)
- [현재 분기로 LTSB 업그레이드](convert-to-current-branch.md)
- [지원되는 LTSB 구성](supported-configurations-for-ltsb.md)
- [Configuration Manager의 LTSB 관리](manage-the-ltsb.md)

LTSB에 대한 현재 분기 설명서를 참조할 때 버전 1606 이전에 적용되는 세부 정보가 LTSB에도 적용됩니다. 버전 1610 이상에 소개된 기능이나 세부 정보는 LTSB에서 지원하지 않습니다.

## <a name="licensing-overview-for-the-ltsb"></a>LTSB에 대한 라이선스 개요   

2016년 10월 1일 당시 System Center Configuration Manager 라이선스에 활성 SA(Software Assurance)가 있거나 이와 동등한 구독 권한이 있는 고객은 System Center Configuration Manager의 2016년 10월 버전 1606 릴리스를 사용할 수 있습니다. 2016년 10월 1일 이후에 System Center Configuration Manager에 대한 권한이 있는 고객에게는 설치 시 다음 두 가지 사용이 허가된 옵션이 있습니다. 현재 분기 및 LTSB(장기 서비스 분기).

System Center Configuration Manager에 대한 영구적인 권한이 있거나 10월 1일 이후에 SA 또는 구독 경과를 허용하는 고객은 경과 당시 최신 버전인 System Center Configuration Manager LTSB 버전을 설치할 수 있습니다.

이러한 라이선스에 대한 자세한 내용은 [Microsoft 볼륨 라이선스 프로그램을 통해 구입하는 제품의 전체 사용 약관](https://go.microsoft.com/fwlink/?LinkId=800052)을 참조하세요.

Configuration Manager 분기용 라이선스에 대한 자세한 내용은 [Configuration Manager 라이선스 및 분기](learn-more-editions.md)를 참조하세요.

## <a name="next-steps"></a>다음 단계

Configuration Manager LTSB가 사용자 환경에 맞는 분기인지 확인한 경우 [새 LTSB](/sccm/core/understand/install-the-ltsb#install-a-new-site) 사이트를 새 계층의 일부로 설치하거나, [System Center 2012 Configuration Manager 사이트](/sccm/core/understand/install-the-ltsb#upgrade-from-system-center-2012-configuration-manager) 및 계층 구조로 업그레이드합니다.
