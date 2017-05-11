---
title: "1606 기준 미디어를 사용하여 사이트 설치 | Microsoft 문서"
description: "System Center Configuration Manager용 LTSB를 설치하거나 업그레이드합니다."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4f9a5fd-f573-4b99-ad93-b2c76812e922
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 39653604ba5fd8e1fe9dd4d42889221d983f9bec
ms.contentlocale: ko-kr
ms.lasthandoff: 05/02/2017


---
# <a name="install-and-upgrade-with-the-version-1606-baseline-media-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 버전 1606 기준 미디어를 사용하여 설치 및 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기), (장기 서비스 분기)*

Configuration Manager용 버전 1606 기준 미디어에서 설치 프로그램을 실행하면 System Center Configuration Manager의 장기 서비스 분기 또는 현재 분기 사이트를 설치할 수 있습니다.

기준 미디어는 Microsoft System Center 2016의 일부로 DVD에서 사용하거나 System Center Configuration Manager(현재 분기 및 장기 서비스 분기 1606) 릴리스에서 사용할 수 있습니다. 기준 미디어에 대해 알아보려면 [기준 및 업데이트 버전](/sccm/core/servers/manage/updates#baseline-and-udpate-versions)을 참조하세요.


버전 1606 기준선 미디어를 사용하는 경우 설치 또는 업그레이드되는 사이트는 다음과 같습니다.
- *현재 분기 사이트* - 1511 기준선 미디어를 사용하여 처음 설치된 다음 버전 1606 및 1606 핫픽스 롤업 - KB3186654로 업데이트된 사이트에 해당합니다.
-    *LTSB 사이트* - 버전 1606 및 1606 핫픽스 롤업 - KB3186654를 실행하는 현재 분기 사이트에 해당합니다. 기준선 미디어에 핫픽스 롤업이 이미 포함되어 있습니다.  그러나 LTSB는 [System Center Configuration Manager의 장기 서비스 분기 소개](introduction-to-the-ltsb.md)에 자세히 설명된 대로 현재 분기에서 사용할 수 있는 일부 기능이나 특성을 지원하지 않습니다.

System Center Configuration Manager의 다양한 분기에 대해 잘 모르겠으면 [사용해야 하는 Configuration Manager 분기](which-branch-should-i-use.md)를 참조하세요.




## <a name="changes-to-setup-with-the-1606-baseline-media"></a>1606 기준 미디어의 설치 프로그램 변경 내용
1606 기준 미디어에서는 Configuration Manager 설치 프로그램이 다음과 같이 변경되었습니다.

### <a name="branch-and-edition"></a>분기 및 버전
설치 프로그램을 실행할 때 이제 설치할 Configuration Manager 분기를 선택할 수 있는 라이선스 페이지가 표시됩니다. 현재 분기 또는 LTSB를 사용이 허가된 설치로 선택하거나, 현재 분기의 평가판을 사용이 허가되지 않은 설치로 선택할 수 있습니다.

자세한 내용은 [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md)를 참조하세요.

### <a name="software-assurance-expiration"></a>Software Assurance 만료
설치하는 동안 **Software Assurance 만료 날짜** 값을 입력할 수 있습니다. 이 값은 편리한 미리 알림으로 지정할 수 있는 선택적 값입니다.

> [!NOTE]
> Microsoft는 입력된 만료 날짜의 유효성을 검사하지 않으며 이 날짜를 라이선스 유효성 검사에 사용하지 않습니다.  대신, 만료 날짜 미리 알림으로 사용할 수 있습니다. 이 기능은 Configuration Manager가 온라인에서 제공되는 새 소프트웨어 업데이트를 정기적으로 확인하며 이러한 추가 업데이트를 사용할 수 있으려면 Software Assurance 라이선스 상태가 현재여야 하기 때문에 유용합니다.    

- System Center Configuration Manager 버전 1606 기준선 미디어에서 설치 프로그램을 실행할 때 설치 마법사의 **제품 키** 페이지에서 날짜 값을 지정할 수 있습니다.
- Configuration Manager 콘솔에 있는 **계층 설정 속성** > **라이선스**를 선택하여 이 날짜를 지정할 수도 있습니다.

자세한 내용은 [System Center Configuration Manager의 라이선스 및 분기](learn-more-editions.md)에서 “Software Assurance 계약”을 참조하세요.


### <a name="additional-pre-upgrade-configurations"></a>추가 업그레이드 전 구성
System Center 2012 Configuration Manager를 LTSB로 업그레이드하기 전에 업그레이드 전 검사 목록의 일부로 다음과 같은 추가 단계를 수행해야 합니다.  
LTSB에서 지원되지 않는 사이트 시스템 역할을 제거합니다.
- Asset Intelligence 동기화 지점
- Microsoft Intune 커넥터
- 클라우드 기반 배포 지점

자세한 내용은 [System Center Configuration Manager 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)를 참조하세요.


### <a name="new-scripted-installation-options"></a>스크립팅된 새 설치 옵션
버전 1606 기준선 미디어는 새 최상위 사이트의 스크립팅된 설치를 위해 새 무인 설치 스크립트 파일 키를 지원합니다. 이 키는 새 독립 실행형 기본 사이트를 설치하거나 사이트 확장 시나리오의 일부로 중앙 관리 사이트를 추가하는 경우에 적용됩니다.

무인 설치 스크립트를 사용하여 사용이 허가된 분기를 설치하는 경우 스크립트의 옵션 섹션에 다음과 같은 섹션, 키 이름 및 값을 추가해야 합니다. 현재 분기의 평가판 설치를 스크립팅할 때는 이러한 값을 사용할 필요가 없습니다.  

 **SABranchOptions**
-     **키 이름: SAActive**
  - 값: 0 또는 1  
  - 세부 정보: 값이 0이면 현재 분기의 사용이 허가되지 않은 평가판이 설치되고, 값이 1이면 사용이 허가된 버전이 설치됩니다.   

- **CurrentBranch**
  - 값: 0 또는 1  
  - 세부 정보: 값이 0이면 장기 서비스 분기가 설치되고, 값이 1이면 현재 분기가 설치됩니다.  

예를 들어 사용이 허가된 현재 분기 버전을 설치하려면 다음을 사용합니다.

  **키 이름: SABranchOptions**
   -    **SAActive = 1**
   - **CurrentBranch = 1**


> [!IMPORTANT]  
> **SABranchOptions**는 기준 미디어의 설치 프로그램에서만 작동합니다. 이전에 버전 1606 기준 미디어를 사용하여 설치한 사이트의 CD.Latest 폴더에 있는 설치 프로그램을 실행할 때는 적용되지 않습니다.
>
> **SABranchOptions**는 System Center 2012 Configuration Manager에서의 스크립팅된 업그레이드에 적용되지 않으며 항상 현재 분기가 됩니다.

자세한 내용은 [명령줄을 사용하여 System Center Configuration Manager 사이트 설치](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites)를 참조하세요.


## <a name="install-a-new-site"></a>새 사이트 설치
1606 기준 미디어를 사용하여 두 분기 중 하나의 새 사이트를 설치하는 경우 [System Center Configuration Manager 사이트 설치](/sccm/core/servers/deploy/install/installing-sites) 항목에 문서화된 사이트 계획, 준비 및 설치 절차와 설치 프로그램에 대한 다음 고려 사항을 추가로 사용합니다.

- 설치하는 동안 설치할 Configuration Manager 분기를 선택해야 하며, Software Assurance 계약에 대한 세부 정보를 지정할 수 있습니다.
- 동일한 계층 구조의 모든 사이트가 동일한 분기를 실행해야 합니다. 여러 사이트에 LTSB와 현재 분기가 혼합되어 있는 계층 구조는 사용할 수 없습니다.
-    스크립팅된 새 설치. 자세한 내용은 이 문서의 앞부분에서 "스크립팅된 새 설치 옵션"을 참조하세요.

## <a name="expand-a-stand-alone-primary-site"></a>독립 실행형 기본 사이트 확장
LTSB를 실행하는 독립 실행형 기본 사이트를 확장할 수 있습니다.  이 프로세스는 현재 분기 사이트에 사용되는 프로세스와 같지만 다음 한 가지 사항에 주의해야 합니다.

- 새 중앙 관리 사이트를 설치하는 경우 LTSB 사이트를 설치하는 데 사용한 원래 원본 미디어의 설치 프로그램을 사용해야 합니다. CD.Latest 폴더에서 설치 프로그램 실행은 이 시나리오에서 지원되지 않습니다.

사이트를 확장하는 방법에 대한 자세한 내용은 [설치 마법사를 사용하여 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites)에서 “독립 실행형 기본 사이트 확장”을 참조하세요.

## <a name="upgrade-from-system-center-2012-configuration-manager"></a>System Center 2012 Configuration Manager에서 업그레이드
System Center 2012 Configuration Manager에서 업그레이드하는 경우 [System Center Configuration Manager 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager) 항목에 문서화된 대로 사이트 계획, 준비 및 절차를 사용하되 다음과 같이 변경합니다.

**현재 분기로 업그레이드:**
- 설치하는 동안 현재 분기를 선택해야 하며, Software Assurance 계약에 대한 세부 정보를 지정할 수 있습니다.
-     스크립팅된 새 설치. 자세한 내용은 이 문서의 앞부분에서 "스크립팅된 새 설치 옵션"을 참조하세요.

**LTSB로 업그레이드:**  
- 업그레이드 전 체크리스트에서 수행할 추가 단계
- 설치하는 동안 LTSB를 선택해야 하며, Software Assurance 계약에 대한 세부 정보를 지정할 수 있습니다.
- System Center 2012 Configuration Manager 서비스 팩 2 또는 System Center 2012 R2 Configuration Manager 서비스 팩 1을 실행하는 사이트만 업그레이드할 수 있습니다.

### <a name="in-place-upgrade-paths-for-the-1606-baseline-media"></a>1606 기준 미디어에 대한 전체 업그레이드 경로
1606 기준 미디어를 사용하여 다음 버전을 System Center Configuration Manager의 사용이 허가된 버전으로 업그레이드할 수 있습니다.
- System Center 2012 Configuration Manager 서비스 팩 2
- System Center 2012 R2 Configuration Manager 서비스 팩 1

이 미디어를 사용하여 현재 분기의 사용이 허가되지 않은 평가판을 현재 분기의 정품 버전으로 업그레이드할 수도 있습니다.

이 미디어는 다음 버전의 업그레이드를 지원하지 않습니다.
- System Center 2012 Configuration Manager의 기타 버전
- Configuration Manager 2007 또는 이전 버전
- System Center Configuration Manager의 릴리스 후보 설치

## <a name="about-the-cdlatest-folder-and-the-ltsb"></a>CD.Latest 폴더 및 LTSB 정보
Configuration Manager가 사이트 서버의 CD.Latest 폴더에 만든 미디어를 사용하는 경우 제한 사항은 다음과 같습니다. 이러한 제한 사항은 LTSB를 실행하는 사이트에 적용됩니다.

CD.Latest 폴더에 있는 미디어는 다음 용도로 사용할 수 있습니다.
- 사이트 복구
- 사이트 유지 관리
- 추가 하위 기본 사이트 설치

CD.Latest 폴더의 미디어는 다음 용도로 사용할 수 없습니다.  
- 사이트 확장 시나리오의 일부로 중앙 관리 사이트 설치.

자세한 내용은 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)를 참조하세요.

## <a name="backup-recovery-and-site-maintenance-for-the-ltsb"></a>LTSB에 대한 백업, 복구 및 사이트 유지 관리
LTSB를 실행하는 사이트에서 백업 또는 복구하거나 사이트 유지 관리를 실행하려면 [System Center Configuration Manager 백업 및 복구](/sccm/protect/understand/backup-and-recovery)에 있는 지침과 절차를 사용합니다.  

LTSB 사이트 백업의 CD.Latest 폴더에 있는 Configuration Manager 설치 프로그램을 사용합니다.

