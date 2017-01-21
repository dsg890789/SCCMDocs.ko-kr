---
title: "장기 서비스 분기 소개 | System Center Configuration Manager"
description: "System Center Configuration Manager의 장기 서비스 분기에 대해 알아봅니다."
ms.custom: na
ms.date: 10/12/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 694bc29f-a7fd-4e06-815a-1a9c5e9ac563
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2a45cfb3e00d8078fbf45bdc8a2668b7dd0a62c6
ms.openlocfilehash: 926d1b1299e7851bd1d9168237859c5cd7a65abe


---
# <a name="introduction-to-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>System Center Configuration Manager의 장기 서비스 분기 소개

*적용 대상: System Center Configuration Manager(장기 서비스 분기)*

이 항목에서는 Configuration Manager의 LTSB(장기 서비스 분기)에 대해 알아보고 이 분기에 대한 문서를 이해합니다.


LTSB는 버전 1606의 현재 분기를 기반으로 하는 Configuration Manager의 고유 분기입니다. 현재 분기에 비해 LTSB는 [축소된 기능](#features-that-are-not-available-in-the-ltsb-of-configuration-manager)을 갖습니다. [SA(Software Assurance) 또는 동등한 구독 권한의 경과를 허용](/sccm/core/understand/learn-more-editions#software-assurance-and-the-ltsb)하는 고객을 위한 것입니다.

**라이선스 개요:**   
2016년 10월 1일 당시 System Center Configuration Manager 라이선스에 활성 SA(Software Assurance)가 있거나 이와 동등한 구독 권한이 있는 고객은 System Center Configuration Manager의 2016년 10월 버전 1606 릴리스를 사용할 수 있습니다. 2016년 10월 1일 이후에 System Center Configuration Manager에 대한 권한이 있는 고객은 설치 시 현재 분기 및 LTSB(장기 서비스 분기)라는 두 가지 사용이 허가된 옵션을 사용할 수 있습니다.

**라이선스 정보:**  
[Microsoft 볼륨 라이선스 프로그램을 통해 구입하는 제품에 대한 전체 계약조건은 여기서 확인할 수 있습니다](http://go.microsoft.com/fwlink/?LinkId=800052).

System Center Configuration Manager에 대한 영구적인 권한이 있거나 10월 1일 이후에 SA 또는 구독 경과를 허용하는 고객은 경과 당시 최신 버전인 System Center Configuration Manager LTSB 버전을 설치할 수 있습니다.
- System Center Configuration Manager의 Software Assurance 및 라이선스 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md)를 참조하세요.
-   다양한 분기의 차이점에 대한 자세한 내용은 [사용해야 하는 Configuration Manager 분기](which-branch-should-i-use.md)를 참조하세요.

새 사이트를 설치하거나 지원되는 System Center 2012 Configuration Manager 사이트에서 LTSB로 업그레이드하려면 버전 1606 기준 미디어를 사용합니다. 이 기준 미디어는 Microsoft System Center 2016의 일부로 DVD에서 사용하거나 System Center Configuration Manager(현재 분기 및 장기 서비스 분기 1606) 릴리스에서 사용할 수 있습니다. LTSB를 설치할 수 있는 기준 미디어를 사용하여 Configuration Manager의 현재 분기 버전 1606도 설치할 수 있습니다. 기준 미디어에 대해 알아보려면 [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#baseline-and-update-versions)을 참조하세요.

LTSB 사이트를 설치하는 방법에 대한 자세한 내용은 [장기 서비스 분기 설치 및 업그레이드](install-the-ltsb.md)를 참조하세요. System Center 2016을 가져오는 방법에 대한 자세한 내용은 [System Center 2016 문서](https:\technet.microsoft.com\system-center-docs\System-Center-2016)를 참조하세요.

> [!IMPORTANT]
> 계층 구조의 모든 사이트가 동일한 분기를 실행해야 합니다. 여러 사이트에 LTSB와 현재 분기가 혼합되어 있는 계층 구조는 사용할 수 없습니다.
>
> 마찬가지로, 복구를 사용하는 경우 사이트 또는 사이트 데이터베이스를 원래 분기로 복원해야 합니다. 현재 분기 사이트 데이터베이스를 LTSB 설치로 복구할 수 없으며, 그 반대의 경우도 마찬가지입니다.


## <a name="features-that-are-not-available-in-the-ltsb-of-configuration-manager"></a>Configuration Manager의 LTSB에서 사용할 수 없는 기능
현재 분기에 비해 LTSB에는 다음과 같은 지원 제한 사항이 있습니다.

- 새로운 기능에 대한 업데이트를 받지 않습니다.
- Microsoft Intune 구독 추가를 지원하지 않으며, 이로 인해 다음을 사용할 수 없습니다.
  - 하이브리드 MDM 구성에서 Intune을 사용할 수 없음
  - 온-프레미스 MDM을 사용할 수 없음
-   Windows 10 서비스 대시보드 및 서비스 계획의 사용을 지원하지 않으며, Windows 10 CB(현재 분기) 및 CBB(비즈니스용 현재 분기)도 지원하지 않습니다.
- Windows 10 LTSB 및 Windows Server의 이후 릴리스를 지원하지 않음
-   Asset Intelligence를 지원하지 않음
-   클라우드 기반 배포 지점을 지원하지 않음
-   Exchange Online을 Exchange 커넥터로 지원하지 않음
-   모든 시험판 기능을 지원하지 않음


LTSB에는 이러한 기능에 대한 지원이 포함되지 않아도 일부 기능은 Configuration Manager 콘솔에 계속 표시되지만 선택하거나 사용할 수 없습니다.

또한 현재 분기에서 지원되는 것으로 추가된 새 운영 체제가 LTSB에서는 지원되지 않습니다.

## <a name="documentation-for-the-ltsb"></a>LTSB에 대한 문서
LTSB는 버전 1606 현재 분기를 기반으로 하기 때문에 LTSB와 관련해서 사용되는 문서는 [현재 분기에 적용되는 온라인 문서](https://docs.microsoft.com/sccm/)로, 다음 항목에 설명된 LTSB 관련 주의 사항과 제한 사항을 포함합니다.  

-   [장기 서비스 분기 소개](introduction-to-the-ltsb.md) - (이 항목)

-   [사용해야 하는 Configuration Manager 분기](which-branch-should-i-use.md) – 요구에 맞는 최상의 분기를 설치할 수 있도록 다양한 System Center Configuration Manager 분기에 대한 정보입니다.

-   [장기 서비스 분기 설치](install-the-ltsb.md) - 새 LTSB 사이트를 설치하거나 System Center 2012 Configuration Manager 사이트를 LTSB로 업그레이드하는 방법입니다.

-   [장기 서비스 분기를 현재 분기로 업그레이드](convert-to-current-branch.md) - LTSB 설치를 현재 분기 설치로 변환하는 방법입니다.

-   [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md) – System Center Configuration Manager의 Software Assurance 및 관련 라이선스 요구 사항에 대한 정보입니다.
-   [장기 서비스 분기에 대해 지원되는 구성](supported-configurations-for-ltsb.md) - LTSB에 사용할 수 있는 운영 체제 및 SQL Server 등의 종속 제품에 대한 버전 및 요구 사항입니다.


특정 문서가 적용되는 분기를 구분하려면 다음 가이드를 사용합니다.  
-   제목이 *적용 대상: 현재 분기*인 항목은 현재 분기와 장기 서비스 분기 둘 다에 적용됩니다. 단, 항목의 일부 내용은 최신 버전의 현재 분기에만 적용될 수도 있습니다.

-   LTSB에 적용되지 않는 항목 부분을 확인하려면 버전 1606 이후의 현재 분기에 도입된 기능과 변경 내용은 '버전 1610부터 시작' 등의 단어로 식별됩니다. 이러한 기능은 1606 버전 이후의 현재 분기에서 도입되었으므로 LTSB에서 사용할 수 없습니다.

### <a name="similarities-between-the-current-branch-and-the-ltsb"></a>현재 분기와 LTSB 간의 유사점
LTSB는 현재 분기 버전 1606을 기반으로 하기 때문에(Intune 통합, 클라우드 관련 기능 등의 몇 가지 예외 포함), 두 분기에 대한 배포 계획, 구성 및 관리 작업은 대부분 동일합니다.

예를 들어 LTSB는 현재 분기와 동일한 사이트 수, 사이트 유형, 클라이언트 및 일반 인프라를 지원합니다. 따라서 현재 분기에 대한 사이트 및 계층 구조 계획 및 디자인 항목에 있는 지침을 사용합니다. 마찬가지로, 소프트웨어 업데이트 또는 운영 체제 배포와 같이 두 분기에서 모두 지원하는 기능의 경우 현재 분기 문서의 해당 섹션에 있는 지침을 사용합니다. 단, 1606 버전 이후의 현재 분기에서 도입된 변경 내용에 액세스하지 않도록 주의합니다.


## <a name="how-to-identify-your-branch-and-version"></a>분기 및 버전을 식별하는 방법
Configuration Manager 사이트에 대한 버전 정보를 보면 분기도 확인됩니다.

사이트 버전을 확인하려면 콘솔의 왼쪽 위에 있는 **System Center Configuration Manager 정보**로 이동합니다. **사이트 버전**이 **5.0.8412.1000**으로 표시됩니다.

사이트 분기를 LTSB 또는 현재 분기로 확인하려면 콘솔에서 **관리** > **사이트 구성** > **사이트**으로 이동한 다음 **계층 설정**을 엽니다.  현재 분기로 변환하는 옵션이 있고 활성 상태이면 사이트에서 LTSB 버전을 실행합니다. 사이트에서 현재 분기를 실행하는 경우에는 이 옵션이 회색으로 표시됩니다.

다양한 Configuration Manager 버전에 대한 자세한 내용은 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates) 항목에서 **기준 및 업데이트 버전**을 참조하세요.

## <a name="exceptions-for-using-the-ltsb"></a>LTSB 사용에 대한 예외
### <a name="updates-and-servicing-of-the-ltsb"></a>LTSB 업데이트 및 서비스
LTSB에서는 중요 보안 업데이트만 콘솔 내 업데이트로 제공됩니다.

그러나 후속 현재 분기 릴리스에 대한 정기 업데이트 정보가 콘솔에 표시됩니다. 이러한 업데이트는 LTSB에 제공되지 않으므로 다운로드되지 않으며 설치할 수 없습니다.

중요한 보안 픽스에 대해 콘솔 내 업데이트를 지원하려면 LTSB 사이트에서 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 사용해야 합니다. 현재 분기와 마찬가지로 이 사이트 시스템 역할을 오프라인 또는 온라인 모드로 구성할 수 있습니다. LTSB는 현재 분기와 동일한 원격 분석 및 사용 현황 데이터를 수집하고 제출합니다.

LTSB는 현재 분기에 대해 문서화된 대로 핫픽스 설치 관리자 및 업데이트 등록 도구의 사용을 지원합니다.

업데이트 및 서비스에 대한 일반적인 내용은 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.

### <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>사이트 확장 및 CD.Latest 폴더에 대한 변경 내용
LTSB를 실행하고 새 중앙 관리 사이트를 설치하여 독립 실행형 기본 사이트를 확장하는 경우 버전 1606 기준 미디어의 설치 프로그램 및 소스 파일을 사용해야 합니다.  현재 분기의 경우 CD.Latest 폴더에서 설치 프로그램을 실행하고 소스 파일을 사용합니다.

CD.Latest 폴더에서 사이트 확장을 위해 설치 프로그램을 실행하지 않더라도 CD.Latest 폴더는 사이트 복구에 계속 사용되며, 첫 번째 LTSB 사이트가 중앙 관리 사이트인 경우 새 하위 기본 사이트를 설치할 때도 사용됩니다.

사이트 확장에 대한 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites)에서 [독립 실행형 기본 사이트 확장](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site)을 참조하세요.
CD.Latest 폴더에 대한 자세한 내용은 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)를 참조하세요.



<!--HONumber=Nov16_HO1-->


