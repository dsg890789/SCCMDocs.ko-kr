---
title: LTSB 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 LTSB에 대한 관리상의 차이점
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8da2887a-fd8e-438c-b926-849c121f7fdf
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 34e0ae19fc7bb3680a148fd5e4ac52feb294963f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56121314"
---
# <a name="manage-the-long-term-servicing-branch-of-configuration-manager"></a>Configuration Manager의 장기 서비스 분기 관리

*적용 대상: System Center Configuration Manager(장기 서비스 분기)*

System Center Configuration Manager의 LTSB(장기 서비스 분기)를 사용하는 경우 다음 내용은 인프라 관리 방법에 영향을 주는 중요한 변경 사항을 이해하는 데 도움이 됩니다.

LTSB는 Intune 통합 및 클라우드 관련 기능 등의 몇 가지 예외를 제외하고 현재 분기 버전 1606과 동일하기 때문에 계획, 배포, 구성 및 일상적인 관리에 사용되는 작업은 대부분 동일합니다.

예를 들어 LTSB는 현재 분기와 동일한 사이트 수, 사이트 유형, 클라이언트 및 일반 인프라를 지원합니다. 따라서 현재 분기에 대한 사이트 및 계층 구조 계획 및 디자인 항목에 있는 지침을 사용합니다. 마찬가지로, 소프트웨어 업데이트 또는 운영 체제 배포와 같이 두 분기에서 모두 지원하고 LTSB를 사용하는 기능의 경우 현재 분기 문서의 해당 섹션에 있는 지침을 사용합니다. 단, 1606 버전 이후의 현재 분기에서 도입된 기능 변경 내용에 액세스하지 않도록 주의합니다.

다음 섹션에서는 유사하지 않은 관리 작업에 대한 정보를 제공합니다.

## <a name="updates-and-servicing"></a>업데이트 및 서비스
LTSB에서는 중요 보안 업데이트만 콘솔 내 업데이트로 제공됩니다.  

후속 현재 분기 릴리스에 대한 정기 업데이트 정보가 콘솔에 표시되지만 LTSB에는 제공되지 않습니다. 다운로드되지 않으며 설치할 수 없습니다.

중요한 보안 픽스에 대해 콘솔 내 업데이트를 지원하려면 LTSB 사이트에서 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 사용해야 합니다. 현재 분기와 마찬가지로 이 사이트 시스템 역할을 오프라인 또는 온라인 모드로 구성할 수 있습니다. LTSB는 현재 분기와 동일한 원격 분석 및 사용 현황 데이터를 수집하고 제출합니다.

LTSB는 현재 분기에 대해 문서화된 대로 핫픽스 설치 관리자 및 업데이트 등록 도구의 사용을 지원합니다.

업데이트 및 서비스에 대한 일반적인 내용은 [Configuration Manager용 업데이트](/sccm/core/servers/manage/updates)를 참조하세요.


## <a name="changes-for-site-expansion-and-the-cdlatest-folder"></a>사이트 확장 및 CD.Latest 폴더에 대한 변경 내용
LTSB를 실행하고 새 중앙 관리 사이트를 설치하여 독립 실행형 기본 사이트를 확장하는 경우 버전 1606 기준 미디어의 설치 프로그램 및 소스 파일을 사용해야 합니다. 현재 분기의 경우 설치 프로그램을 실행하고 CD.Latest 폴더의 원본 파일을 사용합니다.

CD.Latest 폴더에서 사이트 확장을 위해 설치 프로그램을 실행하지 않더라도 CD.Latest 폴더는 사이트 복구에 계속 사용되며, 첫 번째 LTSB 사이트가 중앙 관리 사이트인 경우 새 하위 기본 사이트를 설치할 때도 사용됩니다.

사이트 확장에 대한 자세한 내용은 [독립 실행형 기본 사이트 확장](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#expand-a-stand-alone-primary-site)을 참조하세요. CD.Latest 폴더에 대한 자세한 내용은 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)를 참조하세요.


## <a name="recovery"></a>복구
사이트를 복구하는 경우 사이트 또는 사이트 데이터베이스를 원래 분기로 복원해야 합니다. 현재 분기 사이트 데이터베이스를 LTSB 설치로 복구할 수 없으며, 그 반대의 경우도 마찬가지입니다.
