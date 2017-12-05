---
title: "업그레이드, 업데이트 및 설치 정보"
titleSuffix: Configuration Manager
description: "Configuration Manager 인프라를 관리할 때 설치, 업데이트 및 업그레이드라는 용어 간의 차이점을 알아봅니다."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17fab17f-304d-4f6a-87c7-30ab4f5521ed
caps.latest.revision: "0"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 048678f63cb09f4cd06c2537c5741ba307e6497c
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2017
---
# <a name="about-upgrade-update-and-install-for-site-and-hierarchy-infrastructure"></a>사이트 및 계층 인프라에 대한 업그레이드, 업데이트 및 설치 정보

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager 사이트 및 계층 인프라를 관리할 때 *업그레이드*, *업데이트* 및 *설치*라는 용어는 세 가지 별도의 개념을 설명하는 데 사용됩니다.

## <a name="upgrade"></a>Upgrade
*업그레이드* 또는 *전체 업그레이드*는 Configuration Manager 2012 사이트 또는 계층을 System Center Configuration Manager를 실행하는 사이트 또는 계층으로 변환하는 데 사용됩니다.
System Center 2012 Configuration Manager를 System Center Configuration Manager로 업그레이드한 경우 사이트 및 사이트 서버를 호스트하는 데 계속해서 동일한 서버가 사용되며 Configuration Manager에 대한 기존 데이터 및 구성이 그대로 유지됩니다.  이는 새 하드웨어에 설치된 새 System Center Configuration Manager 사이트를 사용하면서 관리되는 장치에 대한 구성 및 데이터를 유지하는 방법인 [마이그레이션](/sccm/core/migration/migrate-data-between-hierarchies)과 다릅니다.

자세한 내용은 [System Center Configuration Manager로 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)를 참조하세요.



## <a name="update"></a>업데이트
*업데이트*는 System Center Configuration Manager에 대한 콘솔 내 업데이트 설치 및 Configuration Manager 콘솔 내에서 배달할 수 없는 업데이트인 대역 외 업데이트에 사용됩니다. 콘솔 내 업데이트는 상위 버전을 실행할 수 있도록 현재 분기 사이트(또는 기술 미리 보기 사이트)의 버전을 수정할 수 있습니다. 예를 들어 사이트에서 버전 1606을 실행하는 경우 버전 1610에 대한 업데이트를 설치할 수 있습니다. 또한 사이트 버전을 수정하지 않고 업데이트에서 알려진 문제에 대한 수정 프로그램을 설치할 수 있습니다.      

일반적으로 업데이트는 기존 배포에 보안 수정 프로그램, 품질 개선 및 새로운 기능을 추가합니다. 기술 미리 보기 분기를 사용하는 경우 업데이트를 통해 기술 미리 보기의 최신 버전을 설치할 수 있습니다.
-   콘솔 내 업데이트를 설치할 시기는 계층의 최상위 계층 사이트부터 선택합니다.
- 콘솔 내에서 사용할 수 있는 모든 업데이트를 설치할 수 있습니다. 예를 들어 사이트에서 버전 1602를 실행하고 1606과 1610이 둘 다 제공된 경우 버전 1610을 설치하는 것이 좋습니다. 각 버전에는 이전에 릴리스된 버전에서 처음으로 제공된 기능이 포함되어 있기 때문입니다.
- 최상위 계층 사이트에서 새 업데이트 설치가 완료되면 자식 기본 사이트에서 업데이트 프로세스가 자동으로 시작됩니다. 그러나 [서비스 기간](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkservicewindowa-service-windows-for-site-servers)을 설정하여 업데이트 시기를 제어할 수 있습니다.
- 보조 사이트에는 업데이트가 자동으로 설치되지 않습니다. 대신 Configuration Manager 콘솔 내에서 수동으로 업데이트를 시작해야 합니다.

자세한 내용은 [System Center Configuration Manager용 업데이트](/sccm/core/servers/manage/updates) 및 [System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.



## <a name="install"></a>설치
*설치*는 새 Configuration Manager 계층을 처음부터 만들거나 기존 계층에 추가 사이트를 추가할 때 사용됩니다.  

새 기본 사이트 또는 중앙 관리 사이트를 설치하는 경우 사용되는 setup.exe 및 관련 소스 파일의 위치는 설치 시나리오에 따라 다릅니다.

자세한 내용은 [사이트 설치 준비](/sccm/core/servers/deploy/install/prepare-to-install-sites)를 참조하세요.
