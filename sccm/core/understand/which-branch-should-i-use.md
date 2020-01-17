---
title: 사용해야 하는 분기
titleSuffix: Configuration Manager
description: Configuration Manager의 여러 분기 간의 차이점을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0d7949741ae9092e8f12b01c03ea864fb7075942
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75791847"
---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>사용해야 하는 Configuration Manager 분기

*적용 대상: Configuration Manager(현재 분기 및 기술 미리 보기 분기), System Center Configuration Manager(장기 서비스 분기)*

Configuration Manager에는 다음과 같은 세 가지 분기가 있습니다.

- 현재 분기
- 장기 서비스 분기
- 기술 미리 보기 분기

이 문서를 참고하여 올바른 분기를 선택하세요.

> [!TIP]  
> 계층 구조의 모든 사이트가 동일한 분기를 실행해야 합니다. 여러 사이트에 서로 다른 분기가 혼합되어 있는 계층 구조는 사용할 수 없습니다.

## <a name="current-branch"></a>현재 분기

이 분기는 프로덕션 환경에서 사용하도록 허가되어 있습니다. 이 분기를 사용하여 최신 기능 및 특성을 가져옵니다. 다음 라이선스 중 하나가 있는 경우 이 분기를 사용할 수 있습니다.  

- System Center Datacenter
- System Center Standard
- System Center Configuration Manager
- 동등한 구독 권한  

Software Assurance 및 라이선스 옵션에 대한 자세한 내용은 [Configuration Manager의 라이선스 및 분기](/sccm/core/understand/learn-more-editions) 및 [Configuration Manager 분기 및 라이선스에 대한 자주 묻는 질문](/sccm/core/understand/product-and-licensing-faq)을 참조하세요.

Microsoft는 1년에 몇 차례 Configuration Manager 현재 분기용 업데이트를 출시할 계획입니다. 각 업데이트 버전은 GA(일반 공급) 릴리스 날짜로부터 18개월 동안 지원됩니다. 기술 지원은 전체 지원 기간 동안 제공됩니다. 그러나 지원 구조는 최신 현재 분기 버전의 가용성에 따라 별도의 두 가지 서비스 단계로 발전하는 동적 구조입니다. 자세한 내용은 [Configuration Manager 현재 분기 버전 지원](/sccm/core/servers/manage/current-branch-versions-supported)을 참조하세요. 최신 버전에 대한 업데이트는 콘솔 내 업데이트로 제공됩니다.

현재 분기를 새 사이트로 설치하려면 [기준 미디어](/sccm/core/servers/manage/updates#bkmk_Baselines)를 사용합니다. 또한 System Center 2012 Configuration Manager 서비스 팩 2 또는 System Center 2012 R2 Configuration Manager 서비스 팩 1에서 업그레이드하려면 기준 미디어를 사용합니다. 이 미디어에 대한 액세스는 조직에서 Configuration Manager에 라이선스를 부여한 방식에 따라 달라집니다.

기준 미디어를 사용하여 현재 분기의 평가판 버전으로 새 사이트를 설치할 수도 있습니다. 평가판은 라이선스가 필요하지 않습니다. 180일 평가판을 사용할 수 있습니다. 현재 분기의 라이선스 버전으로 업그레이드를 지원합니다. 평가판만 설치하려면 [TechNet 평가 센터](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection)에서 가져옵니다.

> [!NOTE]
> 기준 미디어를 사용하여 새 Configuration Manager 계층 구조의 사이트를 설치합니다. 기준 버전을 이전에 설치한 경우 콘솔 내 업데이트를 사용하여 새 버전으로 사이트를 업데이트합니다.  
>
> 콘솔 내 업데이트를 사용하여 업데이트된 사이트는 기준 미디어를 사용하여 설치된 새 사이트와 같습니다.
>
> 자세한 내용은 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.  

### <a name="features-of-the-current-branch"></a>현재 분기의 기능

- 새로운 기능을 사용할 수 있도록 하는 [콘솔 내 업데이트](/sccm/core/servers/manage/install-in-console-updates)를 받습니다.
- 기존 기능에 대한 보안 및 품질 수정을 제공하는 콘솔 내 업데이트를 받습니다.
- 필요한 경우 대역 외 업데이트를 지원합니다. 자세한 내요은 [업데이트 등록 도구 사용](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) 또는 [핫픽스 설치 관리자 사용](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates)을 참조하세요.
- 클라우드 기반 서비스와 통합됩니다.
- 다른 Configuration Manager 설치와의 [데이터 마이그레이션](/sccm/core/migration/migrate-data-between-hierarchies)를 지원합니다.
- 이전 버전의 Configuration Manager에서 업그레이드를 지원합니다.
- 평가판으로 설치를 지원하며, 나중에 정식 라이선스 설치로 업그레이드할 수 있습니다.

최신 버전이 릴리스되는 즉시 업데이트하는 것이 좋습니다. 최대 18개월까지 기다린 후에 최신 버전으로 업데이트하는 것이 가능합니다. 특정 업데이트를 건너뛰고 최신 버전을 설치하는 것도 가능합니다. 각 버전은 누적되므로 업데이트를 건너뛰고 최신 버전을 설치하는 경우에도 이전 버전의 모든 기능 및 향상된 기능에 액세스할 수 있습니다.

자세한 내용은 [현재 분기 버전 지원](/sccm/core/servers/manage/current-branch-versions-supported)을 참조하세요.

### <a name="current-branch-update-options"></a>현재 분기 업데이트 옵션

- 활성 Software Assurance를 사용하면 현재 분기 버전에 대한 콘솔 내 업데이트를 설치할 수 있습니다.  
- 현재 분기를 기술 미리 보기 분기로 변환하는 옵션은 없습니다. 기술 미리 보기 분기는 라이선스가 필요하지 않은 별도 설치입니다.
- 현재 분기를 LTSB(장기 서비스 분기)로 변환하는 옵션은 없습니다. 현재 분기를 제거한 다음, LTSB를 새 설치로 설치해야 합니다.

## <a name="long-term-servicing-branch"></a>장기 서비스 분기

이 분기는 현재 분기를 사용하며 Configuration Manager SA(Software Assurance) 또는 동등한 구독 권한이 2016년 10월 1일 이후에 만료되도록 허용한 Configuration Manager 고객이 프로덕션에서 사용하도록 허가된 분기입니다. Software Assurance 및 라이선스 옵션에 대한 자세한 내용은 [Configuration Manager의 라이선스 및 분기](learn-more-editions.md) 및 [Configuration Manager 분기 및 라이선스에 대한 자주 묻는 질문](/sccm/core/understand/product-and-licensing-faq)을 참조하세요.

LTSB는 버전 1606을 기반으로 합니다. 이 분기는 새로운 기능을 제공하거나 기존 기능을 업데이트하는 콘솔 내 업데이트를 받지 않습니다. 그러나 중요한 보안 수정이 제공됩니다. LTSB를 설치하려면 System Center 2016과 함께 제공되는 버전 1606 [기준 미디어](/sccm/core/servers/manage/updates#bkmk_Baselines)를 사용해야 합니다. 최신 기준 버전은 LTSB 설치를 지원하지 않습니다.

지원되는 System Center 2012 Configuration Manager 사이트에서 새 사이트나 업그레이드로 LTSB를 설치하려면 System Center 2016과 함께 제공되는 버전 1606 [기준 미디어](/sccm/core/servers/manage/updates#bkmk_Baselines)를 사용합니다. 기준 미디어를 사용하여 현재 분기의 버전 1606을 실행하는 새 사이트 또는 장기 서비스 분기를 실행하는 새 사이트를 설치할 수 있습니다.

> [!TIP]  
> System Center 2016에 대한 자세한 내용은 [System Center 2016 설명서](https://docs.microsoft.com/system-center/index)를 참조하세요. 이 설명서에서는 Microsoft 사용권 계약 또는 유사한 권한이 필요한 System Center 2016을 다운로드하는 방법도 설명합니다.  
>  
> VLSC(볼륨 라이선스 서비스 센터)에서 Configuration Manager 버전 1606을 찾으려면 [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx)의 **다운로드 및 키** 탭으로 이동하고 `System Center 2016`를 검색한 다음, **System Center 2016 Datacenter** 또는 **System Center 2016 Standard**를 선택합니다.  
>  
> [TechNet 평가 센터](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview)에서 System Center 2016 평가판을 다운로드할 수도 있습니다.  

### <a name="features-of-the-ltsb"></a>LTSB의 기능

- 중요한 보안 수정을 제공하는 콘솔 내 업데이트를 받습니다.
- Configuration Manager에 대한 SA 계약 또는 이와 동등한 권한이 만료된 경우의 설치 옵션을 제공합니다.
- Configuration Manager에 대한 현재 SA 계약 또는 이와 동등한 권한이 있는 경우 현재 분기로 업그레이드(변환)를 지원합니다.

### <a name="ltsb-limitations"></a>LTSB 제한 사항

LTSB는 현재 분기 버전 1606을 기반으로 하며 다음과 같은 제한 사항이 있습니다.

- LTSB는 일반 공급(2016년 10월) 후 10년 동안 중요 보안 업데이트가 지원되며, 그다음에는 이 분기에 대한 지원이 만료됩니다. 지원 수명 주기에 대한 자세한 내용은 [Microsoft 수명 주기 정책](https://support.microsoft.com/lifecycle)을 참조하세요.
- 서버 및 클라이언트 운영 체제와 관련 기술(예: SQL Server 버전)의 제한된 집합 목록을 지원합니다. 자세한 내용은 [장기 서비스 분기에 대해 지원되는 구성](supported-configurations-for-ltsb.md)을 참조하세요.
- 새로운 기능에 대한 업데이트를 받지 않습니다.
- 다음 기능을 지원하지 않습니다.
  - 공동 관리, Desktop Analytics와 같은 클라우드 부가 기능
  - 온-프레미스 MDM을 사용할 수 없음
  - Windows 10 서비스 대시보드, 서비스 계획 또는 Windows 10 반기 채널
  - Windows 10 LTSB 및 Windows Server의 향후 릴리스
  - Asset intelligence
  - 모든 시험판 기능

### <a name="ltsb-update-options"></a>LTSB 업데이트 옵션

- LTSB 설치를 현재 분기 설치로 변환할 수 있습니다. LTSB 지원이 만료되기 전이나 후에 현재 분기로 변환이 지원됩니다.

  변환하려면 Microsoft와 활성 Software Assurance 계약이 있어야 합니다. 자세한 내용은 다음 아티클을 참조하세요.

  - [장기 서비스 분기를 현재 분기로 업그레이드](convert-to-current-branch.md)
  - [Configuration Manager의 라이선스 및 분기](learn-more-editions.md)
  - [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)

- LTSB를 기술 미리 보기 분기로 변환하는 옵션은 없습니다. 기술 미리 보기 분기는 라이선스가 필요하지 않은 별도 설치입니다.

- 현재 분기의 평가판을 LTSB 설치로 업그레이드할 수 없습니다.

## <a name="technical-preview-branch"></a>기술 미리 보기 분기

기술 미리 보기는 랩 환경용입니다. Configuration Manager용으로 개발되고 있는 최신 기능을 알아보고 사용해봅니다. 프로덕션 환경에서 지원되지 않으며, Software Assurance 사용권 계약이 없어도 됩니다.

기술 미리 보기 분기를 실행하는 새 사이트를 설치하려면 최신 [기술 미리 보기 분기 기준 미디어](/sccm/core/get-started/technical-preview#bkmk_install)를 사용합니다. 기술 미리 보기 분기를 설치한 후에는 매달 콘솔 내 업데이트로 새 버전이 제공됩니다.

### <a name="features-of-the-technical-preview-branch"></a>기술 미리 보기 분기의 기능

- 현재 분기의 최신 기준 버전을 기반으로 함
- 최신 기술 미리 보기 분기 버전으로 설치를 업데이트하는 콘솔 내 업데이트를 받음
- Microsoft가 피드백을 받으려는, 개발 중인 새로운 기능을 포함
- 기술 미리 보기 분기에만 적용되는 업데이트를 받음

### <a name="technical-preview-limitations"></a>기술 미리 보기 제한 사항

- [지원이 제한](/sccm/core/get-started/technical-preview#bkmk_reqs)되며, 단일 기본 사이트와 최대 10개의 클라이언트만 포함합니다.  
- 현재 분기 또는 LTSB 설치로 업데이트하거나 마이그레이션할 수 없습니다.
- 다음 동작을 지원하지 않습니다.
  - 마이그레이션을 사용하여 다른 Configuration Manager 설치로 데이터 가져오기 또는 내보내기
  - 이전 버전의 Configuration Manager에서 업그레이드
  - 평가판 버전으로 설치

기술 미리 보기 분기에서 처음 도입된 기능이 이후 업데이트에서 현재 분기에 추가되는 경우가 많습니다. 각각의 새로운 기술 미리 보기 분기 버전에는 이러한 기능이 현재 분기에 추가된 후에도 이전 기술 미리 보기 분기의 기능을 포함합니다.

자세한 내용은 [Configuration Manager용 기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.

### <a name="technical-preview-update-options"></a>기술 미리 보기 업데이트 옵션

- 새 기술 미리 보기 분기 버전의 콘솔 내 업데이트를 설치할 수 있습니다.

- 기술 미리 보기 분기를 현재 분기 또는 LTSB로 변환하는 옵션이 없습니다.

## <a name="identify-your-version-and-branch"></a>버전 및 분기 확인

### <a name="version"></a>Version

사이트 버전을 확인하려면 콘솔의 왼쪽 위에 있는 **Configuration Manager 정보**로 이동합니다. 이 대화 상자에는 **사이트 버전**이 표시됩니다. 사이트 버전 목록은 [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)을 참조하세요.

### <a name="branch"></a>분기

사이트 분기를 확인하려면 콘솔에서 **관리** > **사이트 구성** > **사이트**으로 이동한 다음, **계층 설정**을 엽니다. 현재 분기로 변환하는 활성 옵션이 있는 경우 사이트에서 LTSB 버전을 실행합니다. 사이트가 현재 분기를 실행할 경우 콘솔이 이 옵션을 사용 안 함으로 설정합니다.

다양한 Configuration Manager 버전에 대한 자세한 내용은 [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#bkmk_Baselines)을 참조하세요.
