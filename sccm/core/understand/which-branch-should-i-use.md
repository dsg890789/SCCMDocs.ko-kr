---
title: "사용해야 하는 분기 | Microsoft 문서"
description: "사용 가능한 System Center Configuration Manager 분기 간의 차이점을 알아봅니다."
ms.custom: na
ms.date: 10/12/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 26a362b4e5f25414178cae6843869a54eb99028c
ms.openlocfilehash: b190b6116fba8080ad4e144e4e349e0926d1340b
ms.lasthandoff: 02/28/2017


---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>사용해야 하는 Configuration Manager 분기

*적용 대상: System Center Configuration Manager(현재 분기, 장기 서비스 분기 및 기술 미리 보기)*


2016년 10월부터, 세 가지 System Center Configuration Manager 분기를 사용할 수 있습니다. 이 항목은 올바른 분기를 선택하는 데 도움이 됩니다.

## <a name="current-branch-of-system-center-configuration-manager"></a>System Center Configuration Manager 현재 분기
최신 기능 및 특성을 가져오는 옵션을 원하는 프로덕션 환경에서 사용하기 위한 사용이 허가된 분기입니다. System Center 데이터 센터, System Center 표준, System Center Configuration Manager 또는 동등한 구독 권한 중 하나가 있을 경우 사용할 분기입니다. Software Assurance 및 라이선스 옵션에 대한 자세한 내용은 [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md)를 참조하세요.


>  [!TIP]
> 현재 분기를 라이선스가 필요하지 않은 평가판으로 설치할 수도 있습니다. 평가판은 180일 동안 사용할 수 있고 현재 분기의 라이선스 버전으로 업그레이드가 지원됩니다.

현재 분기는&1;년 여러 번 새로운 기능으로 업데이트됩니다. 각 업데이트 버전은 릴리스 후&1;년 동안 지원됩니다. 해당&1;년 기간이 만료되기 전에 현재 분기의 최신 버전으로 업데이트해야 합니다. 최신 버전에 대한 업데이트는 콘솔 내 업데이트로 제공됩니다.

현재 분기를 새 사이트로 설치하거나 System Center 2012 Configuration Manager 서비스 팩 2 또는 System Center 2012 R2 Configuration Manager 서비스 팩 1에서 업그레이드로 설치하려면 System Cener 2016과 함께 DVD로 제공되거나 System Center Configuration Manager 독립 실행형 릴리스의 일부로 제공되는 System Center Configuration Manager의 [기준 미디어](/sccm/core/servers/manage/updates#baseline-and-update-versions)를 사용합니다. 이 미디어에 대한 액세스는 System Center Configuration Manager 사용이 허가된 방식에 따라 달라집니다.

기준 미디어를 사용하여 현재 분기의 평가판 버전으로 새 사이트를 설치할 수도 있습니다. 평가판만 설치하려는 경우 [TechNet 평가 센터](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection) 웹 사이트에서 소프트웨어를 다운로드할 수 있습니다.

>  [!NOTE]
> 기준 미디어를 사용하여 새 Configuration Manager 계층 구조의 사이트를 설치합니다. 버전 1511 등의 기준 버전을 이전에 설치한 경우 콘솔 내 업데이트를 사용하여 1606 등의 새 버전으로 사이트를 업데이트합니다.
>
> 콘솔 내 업데이트를 사용하여 업데이트된 사이트는 기준 미디어를 사용하여 설치된 새 사이트와 같습니다.
>
> 자세한 내용은 [System Center Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.

**현재 분기의 기능**
- 새로운 기능을 사용할 수 있도록 하는 [콘솔 내 업데이트](/sccm/core/servers/manage/install-in-console-updates)를 받습니다.
- 기존 기능에 대한 보안 및 품질 수정을 제공하는 콘솔 내 업데이트를 받습니다.
- 필요한 경우 대역 외 업데이트를 지원합니다. [업데이트 등록 도구 사용](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) 또는 [핫픽스 설치 관리자 사용](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates)을 참조하세요.
- Microsoft Intune 및 다른 클라우드 기반 서비스 및 인프라와 상호 운용할 수 있습니다.
- 다른 Configuration Manager 설치와의 [데이터 마이그레이션](/sccm/core/migration/migrate-data-between-hierarchies)를 지원합니다.
- 이전 버전의 Configuration Manager에서 업그레이드를 지원합니다.
- 평가판으로 설치를 지원하며, 나중에 정식 라이선스 설치로 업그레이드할 수 있습니다.

현재 분기의 초기 릴리스는 버전 1511이었습니다. 후속 업데이트에는 버전 1602, 1606 등이 포함됩니다. 각 버전은&1;년 동안 지원되며, 릴리스 후 즉시 최신 버전으로 업데이트하는 것이 좋습니다. 최신 버전으로 업데이트하기 전에 최대&1;년 동안 기다릴 수 있으며, 사용 가능한 최신 버전을 설치하기 위해 업데이트를 건너뛸 수도 있습니다. 각 버전은 누적되므로 업데이트를 건너뛰고 최신 버전을 설치하는 경우에도 이전 버전의 모든 기능 및 향상된 기능에 액세스할 수 있습니다.

자세한 내용은 [현재 분기 버전 지원](/sccm/core/servers/manage/current-branch-versions-supported)을 참조하세요.

**업데이트 옵션**
- 활성 Software Assurance를 사용하면 현재 분기 버전에 대한 콘솔 내 업데이트를 설치할 수 있습니다.  
- 현재 분기를 기술 미리 보기로 변환하는 옵션은 없습니다. 기술 미리 보기는 라이선스가 필요하지 않은 별도 설치입니다.
- 현재 분기를 LTSB(장기 서비스 분기)로 변환하는 옵션은 없습니다. 현재 분기를 제거한 다음 LTSB를 새 설치로 설치해야 합니다.

##  <a name="long-term-servicing-branch-of-system-center-configuration"></a>System Center 구성의 장기 서비스 분기
현재 분기를 사용하며 Configuration Manager SA(Software Assurance) 또는 동등한 구독 권한이 2016년 10월 1일 후에 만료되도록 허용한 Configuration Manager 고객이 프로덕션에서 사용하도록 허가된 분기입니다. Software Assurance 및 라이선스 옵션에 대한 자세한 내용은 [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md)를 참조하세요.

LTSB는 새로운 기능을 제공하거나 기존 기능을 업데이트하는 콘솔 내 업데이트를 받지 않습니다. 그러나 중요한 보안 수정이 제공됩니다.

LTSB를 새 사이트로 설치하거나 지원되는 Configuration Manager 2012 사이트에서 업그레이드로 설치하려면 System Center 2016 또는 System Center Configuration Manager(현재 분기 및 장기 서비스 분기 1606) 릴리스와 함께 DVD로 제공되는 버전 1606 [기준 미디어](/sccm/core/servers/manage/updates#baseline-and-update-versions)를 사용합니다. 기준 미디어를 사용하여 현재 분기의 버전 1606을 실행하는 새 사이트 또는 장기 서비스 분기를 실행하는 새 사이트를 설치할 수 있습니다.

> [!TIP]  
> System Center 2016에 대한 자세한 내용은 [System Center 2016 설명서](https://technet.microsoft.com/system-center-docs/system-center)를 참조하세요. 이 설명서에서는 Microsoft 사용권 계약 또는 유사한 권한이 필요한 System Center 2016을 다운로드하는 방법도 설명합니다.

> VLSC(볼륨 라이선스 서비스 센터)에서 System Center Configuration Manager 버전 1606을 찾으려면 [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx)의 **다운로드 및 키** 탭으로 이동하고 "system center config"를 검색한 다음 **System Center Config Mgr(현재 분기 및 LTSB 1606)**을 선택합니다.

> [TechNet 평가 센터](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview)에서 System Center 2016 평가판을 다운로드할 수도 있습니다.

**LTSB의 기능**
-    중요한 보안 수정을 제공하는 콘솔 내 업데이트를 받습니다.
- Configuration Manager에 대한 SA 계약 또는 이와 동등한 권한이 만료된 경우의 설치 옵션을 제공합니다.
- Configuration Manager에 대한 현재 SA 계약 또는 이와 동등한 권한이 있는 경우 현재 분기로 업그레이드(변환)를 지원합니다.

**제한 사항**  
LTSB는 현재 분기 버전 1606을 기반으로 하며 다음과 같은 제한 사항이 있습니다.
- LTSB는 일반 공급(2016년 10월) 후 10년 동안 중요 보안 업데이트가 지원되며, 그다음에는 이 분기에 대한 지원이 만료됩니다. 지원 수명 주기에 대한 자세한 내용은 [Microsoft 수명 주기 정책](https://support.microsoft.com/en-us/lifecycle)을 참조하세요.
- 서버 및 클라이언트 운영 체제와 관련 기술(예: SQL Server 버전)의 제한된 집합 목록을 지원합니다. 이 분기에서 지원되는 사항에 대한 자세한 내용은 [장기 서비스 분기에 대해 지원되는 구성](supported-configurations-for-ltsb.md)을 참조하세요.
- 새로운 기능에 대한 업데이트를 받지 않습니다.
- Microsoft Intune 구독 추가를 지원하지 않으며, 이로 인해 다음을 사용할 수 없습니다.
  -    하이브리드 MDM 구성에서 Intune을 사용할 수 없음
 - 온-프레미스 MDM을 사용할 수 없음
-    Windows 10 서비스 대시보드, 서비스 계획, Windows 10 CB(현재 분기) 또는 CBB(비즈니스용 현재 분기)의 사용을 지원하지 않습니다.
- Windows 10 LTSB 및 Windows Server의 이후 릴리스를 지원하지 않습니다.
-    Asset Intelligence를 지원하지 않습니다.
-    클라우드 기반 배포 지점을 지원하지 않습니다.
-    Exchange Online을 Exchange 커넥터로 지원하지 않습니다.
-    모든 시험판 기능을 지원하지 않습니다.



**업데이트 옵션**
- LTSB 설치를 현재 분기 설치로 변환할 수 있습니다. LTSB 지원이 만료되기 전이나 후에 현재 분기로 변환이 지원됩니다.

  변환하려면 Microsoft와 활성 Software Assurance 계약이 있어야 합니다. 자세한 내용은 다음 링크를 참조하세요.
  - [장기 서비스 분기를 현재 분기로 업그레이드](convert-to-current-branch.md)
  - [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md)
  - [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)에서 [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#baseline-and-update-versions)
- LTSB를 기술 미리 보기로 변환하는 옵션은 없습니다. 기술 미리 보기는 라이선스가 필요하지 않은 별도 설치입니다.
-    현재 분기의 평가판을 LTSB 설치로 업그레이드할 수 없습니다.


## <a name="technical-preview-for-system-center-configuration-manager"></a>System Center Configuration Manager Technical Preview
기술 미리 보기는 Configuration Manager용으로 개발 중인 최신 기능을 알아보고 시험해보려는 랩 환경에서 사용됩니다. 기술 미리 보기는 프로덕션 환경에서 지원되지 않으며, Software Assurance 사용권 계약이 없어도 됩니다.

기술 미리 보기를 실행하는 새 사이트를 설치하려면 최신 [System Center Configuration Manager Technical Preview 기준 미디어](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview)를 사용합니다. 기술 미리 보기를 설치한 후에는 매달 콘솔 내 업데이트로 새 버전이 제공됩니다.

**기술 미리 보기의 기능**
-  현재 분기의 최신 기준 버전을 기반으로 합니다.
-  최신 기술 미리 보기 버전으로 설치를 업데이트하는 콘솔 내 업데이트를 받습니다.
-  개발자가 피드백을 받으려 하는, 개발 중인 새로운 기능을 포함합니다.
-  기술 미리 보기 분기에만 적용되는 업데이트를 받습니다.

**제한 사항**
-  [지원이 제한](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview)되며, 단일 기본 사이트와 최대 10개의 클라이언트만 포함합니다.  
-  현재 분기 또는 LTSB로 업그레이드할 수 없습니다.
-  마이그레이션을 사용하여 다른 Configuration Manager 설치로 데이터 가져오기 또는 내보내기를 지원하지 않습니다.
-  이전 버전의 Configuration Manager에서 업그레이드를 지원하지 않습니다.
-  평가판으로 설치를 지원하지 않습니다.

기술 미리 보기에서 처음 도입된 기능이 이후 업데이트에서 현재 분기에 추가되는 경우가 많습니다. 각각의 새로운 기술 미리 보기 버전에는 이러한 기능이 현재 분기에 추가된 후에도 이전 기술 미리 보기의 기능을 포함합니다.

자세한 내용은 [System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.

**업데이트 옵션**
-    새 기술 미리 보기 버전의 콘솔 내 업데이트를 설치할 수 있습니다.
-    기술 미리 보기를 현재 분기 또는 LTSB로 변환하는 옵션이 없습니다.

