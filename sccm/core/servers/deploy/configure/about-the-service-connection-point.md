---
title: 서비스 연결 지점
titleSuffix: Configuration Manager
description: 이 Configuration Manager 사이트 시스템 역할에 대해 알아보고 사용 범위를 이해하고 계획합니다.
ms.date: 06/19/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 68f6c464b31aed1ee3b99eb6be4fb34e8d9a8c02
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75799090"
---
# <a name="about-the-service-connection-point-in-configuration-manager"></a>Configuration Manager의 서비스 연결 지점 정보

*적용 대상: Configuration Manager(현재 분기)*

서비스 연결 지점은 계층 구조에 대한 몇 가지 중요한 기능을 수행하는 사이트 시스템 역할입니다. 서비스 연결 지점을 설정하기 전에 추가적인 사용 범위를 이해하고 계획하세요. 사용량 계획은 이 사이트 시스템 역할을 설정 방법에 영향을 줄 수 있습니다.  

- **Microsoft Intune을 사용하여 모바일 디바이스 관리**: 이 역할은 이전 버전의 Configuration Manager에서 사용했으며 Intune 구독 세부 정보로 구성할 수 있는 Windows Intune 커넥터를 대체합니다. 자세한 내용은 [하이브리드 MDM(모바일 디바이스 관리)](/sccm/mdm/understand/hybrid-mobile-device-management)을 참조하세요.  

- **온-프레미스 MDM을 사용하여 모바일 디바이스 관리**: 이 역할은 관리하는 온-프레미스 디바이스와 인터넷에 연결하지 않는 온-프레미스 디바이스를 지원합니다. 자세한 내용은 [온-프레미스 인프라로 모바일 디바이스 관리](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)를 참조하세요.  

- **Configuration Manager 인프라에서 사용량 현황 데이터 업로드**: 업로드하는 세부 정보의 수준 또는 양을 제어할 수 있습니다. 업로드된 데이터로 다음 작업을 수행할 수 있습니다.  

    - 사전에 문제 식별 및 해결  

    - 제품 및 서비스 개선  

    - 사용하는 버전의 Configuration Manager에 적용되는 Configuration Manager 업데이트 식별  

    역할이 설치된 후 각 수준에서 수집하는 데이터 및 수집 수준을 변경하는 방법에 대한 자세한 내용은 [진단 및 사용량 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조하세요. 그런 다음, 사용되는 Configuration Manager 버전의 링크를 따릅니다.  

    자세한 내용은 [사용량 현황 데이터 수준 및 설정](/sccm/core/servers/deploy/install/setup-reference#bkmk_usage)을 참조하세요.  

- **Configuration Manager 인프라에 적용되는 업데이트 다운로드**: 업로드하는 사용량 현황 데이터에 따라 인프라에 대한 관련 업데이트만 사용할 수 있습니다.  

- **각 계층 구조에서 이 역할의 단일 인스턴스 지원**:  

    - 사이트 시스템 역할은 계층 구조의 최상위 계층 사이트(중앙 관리 사이트 또는 독립 실행형 기본 사이트)에만 설치할 수 있습니다.  

    - 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음 중앙 관리 사이트에서 설치해야 합니다.  


##  <a name="bkmk_modes"></a> 작동 모드  
서비스 연결 지점은 다음 두 가지 작동 모드를 지원합니다.  

- **온라인 모드**에서 서비스 연결 지점은 24시간마다 업데이트를 자동으로 확인합니다. 현재 인프라 및 제품 버전에 사용 가능한 새 업데이트를 자동으로 다운로드하여 Configuration Manager 콘솔에서 사용할 수 있게 합니다.  

- **오프라인 모드**에서 서비스 연결 지점은 Microsoft 클라우드 서비스에 연결하지 않습니다. 사용 가능한 업데이트를 수동으로 가져오려면 [서비스 연결 도구](/sccm/core/servers/manage/use-the-service-connection-tool)를 사용합니다.  

서비스 연결 지점을 설치한 후 온라인 또는 오프라인 모드 사이를 변경할 때 변경 내용을 적용하려면 먼저 Configuration Manager SMS_Executive 서비스의 SMS_DMP_DOWNLOADER 스레드를 다시 시작해야 합니다. Configuration Manager Service Manager를 사용하여 SMS_Execctuive 서비스의 SMS_DMP_DOWNLOADER 스레드만 다시 시작할 수 있습니다. 또한 대부분의 사이트 구성 요소를 다시 시작하는 Configuration Manager에 대해 SMS_Executive 서비스를 다시 시작할 수도 있습니다. 또는 SMS_Executive 서비스를 중지했다가 다시 시작하는 사이트 백업과 같은 예약된 작업을 기다릴 수 있습니다.  

Configuration Manager 서비스 관리자를 사용하려면 콘솔에서 **모니터링** > **시스템 상태** > **구성 요소 상태**로 이동하고, **시작**을 선택한 후 **Configuration Manager Service Manager**를 선택합니다. Service manager에서 다음을 수행합니다.  

- 탐색 창에서 사이트를 확장하고 **구성 요소**를 확장한 다음 다시 시작할 구성 요소를 선택합니다.  

- 세부 정보 창에서 구성 요소를 마우스 오른쪽 단추로 클릭한 다음 **쿼리**를 선택합니다.  

- 구성 요소의 상태를 확인한 후 구성 요소를 마우스 오른쪽 단추로 다시 클릭하고 **중지**를 선택합니다.  

- 구성 요소를 다시 **쿼리**하여 중지되었는지 확인합니다. 구성 요소를 한번 더 오른쪽 단추로 클릭한 다음, **시작**을 선택합니다.  

> [!IMPORTANT]  
> 서비스 연결 지점에 Microsoft Intune 구독을 추가하는 프로세스를 통해 사이트 시스템 역할이 자동으로 온라인 상태로 설정됩니다. Intune 구독을 사용하여 설정된 경우 서비스 연결 지점에서 오프라인 모드를 지원하지 않습니다.  

**사이트 서버에서 원격 컴퓨터에 역할을 설치하는 경우:**  

- 사이트 서버의 컴퓨터 계정은 원격 서비스 연결을 호스팅하는 컴퓨터의 로컬 관리자여야 합니다.

- 사이트 시스템 설치 계정을 사용하여 역할을 호스팅하는 사이트 시스템 서버를 설정해야 합니다.  

- 사이트 서버의 배포 관리자는 사이트 시스템 설치 계정을 사용하여 서비스 연결 지점에서 업데이트를 전송합니다.


## <a name="bkmk_urls"></a> 인터넷 액세스 요구 사항  

조직에서 방화벽 또는 프록시 디바이스를 사용하여 인터넷과의 네트워크 통신을 제한하는 경우 서비스 연결 지점에서 인터넷 엔드포인트에 액세스하도록 허용해야 합니다.

자세한 내용은 [Internet access requirements](/sccm/core/plan-design/network/internet-endpoints#bkmk_scp)(인터넷 액세스 요구 사항)를 참조하세요.


## <a name="install-the-service-connection-point"></a>서비스 연결점 설치
**설치 프로그램**을 실행하여 계층의 최상위 사이트를 설치할 때는 서비스 연결점을 설치할 수 있습니다.

설치 프로그램을 실행한 후나 사이트 시스템 역할을 다시 설치하는 경우에는 **사이트 시스템 역할 추가** 마법사 또는 **사이트 시스템 서버 만들기** 마법사를 사용하여 계층의 최상위 사이트(중앙 관리 사이트 또는 독립 실행형 기본 사이트)에 있는 서버에 사이트 시스템을 설치합니다. 이 두 마법사는 모두 콘솔 **홈** 탭의 **관리** > **사이트 구성** > **서버 및 사이트 시스템 역할**에 있습니다.



## <a name="log-files-used-by-the-service-connection-point"></a>서비스 연결 지점에서 사용되는 로그 파일
Microsoft에 대한 업로드 정보를 보려면 서비스 연결 지점을 실행하는 컴퓨터에서 **Dmpuploader.log**를 봅니다.  업데이트 다운로드 진행 상황을 포함하여 다운로드를 확인하려면 **Dmpdownloader.log**를 봅니다. 서비스 연결 지점에 관련된 전체 로그 목록을 보려면 Configuration Manager 로그 파일 문서의 [서비스 연결 지점](/sccm/core/plan-design/hierarchy/log-files#BKMK_WITLog)을 참조하세요.

다음 순서도를 통해 업데이트 다운로드 및 다른 사이트에 대한 업데이트 복제에 관련된 프로세스 흐름 및 주요 로그 항목을 이해할 수도 있습니다.
- [순서도 – 업데이트 다운로드](/sccm/core/servers/manage/download-updates-flowchart)
- [순서도 – 업데이트 복제](/sccm/core/servers/manage/update-replication-flowchart)
