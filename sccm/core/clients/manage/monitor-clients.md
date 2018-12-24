---
title: '클라이언트 모니터링 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 클라이언트를 모니터링하는 방법에 대한 자세한 지침을 가져옵니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 976aeaacfadfa7d2f189f20ab001486d486b764e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32335884"
---
# <a name="how-to-monitor-clients-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트를 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


 System Center Configuration Manager 클라이언트 응용 프로그램이 사이트의 Windows 컴퓨터 및 디바이스에 설치되면 Configuration Manager 콘솔에서 해당 상태 및 활동을 모니터링할 수 있습니다.  

##  <a name="bkmk_about"></a> 클라이언트 상태에 대한 정보  
 Configuration Manager에서는 다음과 같은 정보 유형을 클라이언트 상태로 제공합니다.  

-   **클라이언트 온라인 상태** - Configuration Manager 버전 1602부터, 이 상태는 컴퓨터가 온라인 상태인지 여부를 나타냅니다. 컴퓨터가 할당된 관리 지점에 연결된 경우 온라인 상태인 것으로 간주합니다.  클라이언트가 온라인 상태인지 여부를 나타내기 위해 관리 지점에 ping과 유사한 메시지를 보냅니다. 관리 지점에서 5분 내에 메시지를 받지 못하면 클라이언트 상태가 오프라인으로 변경된 것입니다.  

-   **클라이언트 활동** - 이 상태는 클라이언트가 지난 7일 동안 Configuration Manager에서 적극적으로 조작되었음을 나타냅니다. 클라이언트에서 정책 업데이트를 요청하지 않거나 하트비트 메시지를 보내지 않거나 7일간 하드웨어 인벤토리를 보내지 않은 경우 클라이언트는 비활성으로 간주됩니다.  

-   **클라이언트 검사** - 이 상태는 Configuration Manager 클라이언트가 컴퓨터에서 실행하는 정기적으로 평가의 성공 여부를 나타냅니다.  평가에서 컴퓨터를 검사하고 검색된 문제를 수정할 수 있습니다. 자세한 내용은 [클라이언트 검사를 통한 검사 및 수정](#BKMK_ClientHealth)을 참조하세요.  

     Windows 7을 실행하는 컴퓨터에서 클라이언트 검사는 예약된 작업으로 실행됩니다. Windows 7 이후의 운영 체제에서는 Windows 유지 관리 기간 중에 클라이언트 검사가 자동으로 실행됩니다.  

     재구성이 업무에 중요한 서버와 같은 특정 컴퓨터에서 실행되지 않도록 구성할 수 있습니다. 또한 평가할 추가 항목이 있는 경우 Configuration Manager 준수 설정을 사용하여 조직 내 컴퓨터의 전체 상태, 활동 및 준수를 모니터링할 수 있는 포괄적인 솔루션을 제공할 수 있습니다. 준수 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 준수 설정 계획 및 구성](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)을 참조하세요.  

##  <a name="bkmk_indStatus"></a> 개별 클라이언트의 상태 모니터링  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **디바이스**를 클릭하거나 **디바이스 컬렉션** 아래에서 컬렉션을 선택합니다.  

     Configuration Manager 버전 1602부터, 각 행의 시작 부분에 있는 아이콘은 디바이스의 온라인 상태를 나타냅니다.  

    |||  
    |-|-|  
    |![클라이언트에 대한 온라인 상태 아이콘](../../../core/clients/manage/media/online-status-icon.png)|디바이스가 온라인입니다.|  
    |![클라이언트에 대한 오프라인 상태 아이콘](../../../core/clients/manage/media/offline-status-icon.png)|디바이스가 오프라인입니다.|  
    |![클라이언트에 대한 알 수 없는 상태 아이콘](../../../core/clients/manage/media/unknown-status-icon.png)|클라이언트 상태를 알 수 없습니다.|  
    |![클라이언트 설치 안 됨](../../../core/clients/manage/media/client-not-installed.png)|클라이언트가 디바이스에 설치되지 않았습니다.|  

2.  온라인 상태에 대한 자세한 내용을 보려면 열 머리글을 마우스 오른쪽 단추로 클릭하고 추가하려는 온라인 상태 필드를 클릭하여 디바이스 보기에 클라이언트 온라인 상태 정보를 추가합니다. 추가할 수 있는 열은 다음과 같습니다.  

    -   **장치 온라인 상태** 는 클라이언트가 현재 온라인 상태인지 또는 오프라인 상태인지를 나타냅니다. 이는 아이콘으로 제공되는 것과 동일한 정보입니다.  

    -   **마지막 온라인 시간** 은 클라이언트 온라인 상태가 오프라인에서 온라인으로 변경되었을 때를 나타냅니다.  

    -   **마지막 오프라인 시간** 은 상태가 오프라인으로 변경되었을 때를 나타냅니다.  

3.  목록 창의 개별 클라이언트를 클릭해서 클라이언트 활동 및 클라이언트 검사에 대한 정보를 비롯하여 자세한 상태를 세부 정보 창에서 봅니다.  

##  <a name="bkmk_allStatus"></a> 모든 클라이언트의 상태 모니터링  

1.  Configuration Manager 콘솔에서 **모니터링** > **클라이언트 상태**를 클릭합니다. 콘솔의 이 페이지에서 전체 사이트에 걸쳐 클라이언트 활동 및 클라이언트 검사에 대한 전체 통계를 검토할 수 있습니다.  또한 여러 컬렉션을 선택하여 정보의 범위를 변경할 수 있습니다.  

2.  보고된 통계에 대한 세부 정보를 드릴다운하려면 보고된 정보(예: **클라이언트 검사를 통과했거나 결과가 없는 활성 클라이언트**)의 이름을 클릭하고 개별 클라이언트에 대한 정보를 검토합니다.  

3.  **클라이언트 활동**을 클릭하여 Configuration Manager 사이트에서 클라이언트 활동을 보여 주는 차트를 표시합니다.  

4.  **클라이언트 검사**를 클릭하여 Configuration Manager 사이트에서 클라이언트 검사의 상태를 표시합니다.  

 클라이언트 검사 결과 또는 클라이언트 활동이 컬렉션 내 지정된 클라이언트 비율(%) 아래로 떨어지거나 지정된 클라이언트 비율(%)에 대해 재구성이 실패할 경우 알림을 보내도록 경고를 구성할 수 있습니다. 클라이언트 상태를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 상태를 구성하는 방법](../../../core/clients/deploy/configure-client-status.md)을 참조하세요.  

##  <a name="BKMK_ClientHealth"></a> 클라이언트 검사를 통한 검사 및 재구성  
 다음 검사 및 재구성은 클라이언트 검사를 통해 수행할 수 있습니다.  

|클라이언트 검사|재구성 작업|추가 정보|  
|------------------|------------------------|----------------------|  
|클라이언트 검사가 최근에 실행되었는지 확인|클라이언트 검사 실행|지난 3일간 클라이언트 검사가 1회 이상 실행되었는지 검사합니다.|  
|클라이언트 필수 구성 요소가 설치되었는지 확인|클라이언트 필수 구성 요소 설치|클라이언트 필수 구성 요소가 설치되었는지 검사합니다. 필수 구성 요소 검색을 위해 클라이언트 설치 폴더에서 ccmsetup.xml 파일을 읽습니다.|  
|WMI 저장소 무결성 테스트|Configuration Manager 클라이언트 다시 설치|WMI에 Configuration Manager 클라이언트 항목이 있는지 검사합니다.|  
|클라이언트 서비스가 실행 중인지 확인|클라이언트(SMS 에이전트 호스트) 서비스 시작|추가 정보 없음|  
|WMI 이벤트 싱크 테스트|클라이언트 서비스 다시 시작|Configuration Manager 관련 WMI 이벤트 싱크가 손실되었는지 검사합니다.|  
|WMI(Windows Management Instrumentation) 서비스가 있는지 확인|해결 방법 없음|추가 정보 없음|  
|클라이언트가 올바르게 설치되었는지 확인|클라이언트 다시 설치|추가 정보 없음|  
|WMI 리포지토리 읽기 및 쓰기 테스트|WMI 리포지토리 다시 설정 및 Configuration Manager 클라이언트 다시 설치|이 클라이언트 검사의 재구성은 Windows Server 2003, Windows XP(64비트) 이하 버전을 실행하는 컴퓨터에서만 수행됩니다.|  
|맬웨어 방지 서비스 시작 유형이 자동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|맬웨어 방지 서비스가 실행 중인지 확인|맬웨어 방지 서비스 시작|추가 정보 없음|  
|Windows Update 서비스 시작 유형이 자동 또는 수동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|클라이언트 서비스(SMS 에이전트 호스트) 시작 유형이 자동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|WMI 서비스가 실행 중인지 확인|WMI 서비스 시작|추가 정보 없음|  
|Microsoft SQL CE 데이터베이스가 정상 상태인지 확인|Configuration Manager 클라이언트 다시 설치|추가 정보 없음|  
|Microsoft Policy Platform WMI 무결성 테스트|Microsoft Policy Platform 복구|추가 정보 없음|  
|Microsoft Policy Platform 서비스가 존재하는지 확인|Microsoft Policy Platform 복구|추가 정보 없음|  
|Microsoft Policy Platform 서비스 시작 유형이 수동인지 확인|서비스 시작 유형을 '수동'으로 다시 설정|추가 정보 없음|  
|Background Intelligent Transfer Service가 있는지 확인|해결 방법 없음|추가 정보 없음|  
|Background Intelligent Transfer Service 시작 유형이 자동 또는 수동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|네트워크 검사 서비스 시작 유형이 수동인지 확인|서비스 시작 유형을 수동으로 다시 설정(설치된 경우)|추가 정보 없음|  
|WMI 서비스 시작 유형이 자동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|Windows 8 컴퓨터의 Windows Update 서비스 시작 유형이 자동 또는 수동인지 확인|서비스 시작 유형을 '수동'으로 다시 설정|추가 정보 없음|  
|클라이언트(SMS 에이전트 호스트) 서비스가 존재하는지 확인|해결 방법 없음|추가 정보 없음|  
|Configuration Manager 원격 제어 서비스 시작 유형이 자동 또는 수동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|Configuration Manager 원격 제어 서비스가 실행 중인지 확인|원격 제어 서비스를 시작|추가 정보 없음|  
|클라이언트 WMI 공급자가 정상인지 확인|WMI(Windows Management Instrumentation) 서비스를 다시 시작|이 클라이언트 검사의 해결 방법은 Windows Server 2003, Windows XP(64비트) 이하를 실행하는 컴퓨터에서만 수행해야 합니다.|  
|절전 모드 해제 프록시 서비스(ConfigMgr 절전 모드 해제 프록시)가 실행 중인지 확인|ConfigMgr 절전 모드 해제 프록시 서비스를 시작|이 클라이언트 검사는 지원되는 클라이언트 운영 체제에서 **전원 관리**: **절전 모드 해제 프록시 사용** 클라이언트 설정이 **예** 로 설정된 경우에만 수행됩니다.|  
|절전 모드 해제 프록시 서비스(ConfigMgr 절전 모드 해제 프록시) 시작 유형이 자동인지 확인|ConfigMgr 절전 모드 해제 프록시 서비스 시작 유형을 '자동'으로 다시 설정|이 클라이언트 검사는 지원되는 클라이언트 운영 체제에서 **전원 관리**: **절전 모드 해제 프록시 사용** 클라이언트 설정이 **예** 로 설정된 경우에만 수행됩니다.|  

## <a name="client-deployment-log-files"></a>클라이언트 배포 로그 파일
클라이언트 배포 및 관리 작업에 사용되는 로그 파일에 대한 자세한 내용은 [System Center Configuration Manager의 로그 파일](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs)을 참조하세요.
