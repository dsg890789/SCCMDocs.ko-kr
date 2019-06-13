---
title: 클라이언트 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라이언트를 모니터링하는 방법에 대한 자세한 지침을 가져옵니다.
ms.date: 05/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55fd698ac5213a3b11b207d0625d953f687e319f
ms.sourcegitcommit: 65753c51fbf596f233fc75a5462ea4a44005c70b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/03/2019
ms.locfileid: "66463036"
---
# <a name="how-to-monitor-clients-in-configuration-manager"></a>Configuration Manager에서 클라이언트를 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

구성 관리자 클라이언트를 사이트의 Windows 컴퓨터 및 디바이스에 설치한 후에 Configuration Manager 콘솔에서 해당 상태 및 활동을 모니터링합니다.  


## <a name="bkmk_about"></a> 클라이언트 상태에 대한 정보

Configuration Manager에서는 다음과 같은 정보 유형을 클라이언트 상태로 제공합니다.  

- **클라이언트 온라인 상태**: 사이트는 디바이스가 할당된 관리 지점에 연결된 경우 **온라인** 상태로 간주합니다. 클라이언트가 온라인 상태인지 여부를 나타내기 위해 관리 지점에 ping과 유사한 메시지를 보냅니다. 관리 지점에서 5분 이내에 메시지를 받지 못하면 사이트는 클라이언트를 **오프라인** 상태로 간주합니다.  

- **클라이언트 활동**: 사이트는 클라이언트가 지난 7일 동안 Configuration Manager와 통신한 경우 **활성** 상태로 간주합니다. 사이트는 클라이언트가 지난 7일 동안 다음 작업의 완료를 요청하지 않은 경우 **비활성** 상태로 간주합니다.  

    - 정책 업데이트를 요청함  
    - 하트비트 메시지를 전송함  
    - 하드웨어 인벤토리를 전송함  

- **클라이언트 검사**: 구성 관리자 클라이언트가 디바이스에서 실행하는 정기 평가의 상태입니다. 평가에서 디바이스를 검사하고 검색된 문제를 수정할 수 있습니다. 자세한 내용은 [클라이언트 상태 검사](#BKMK_ClientHealth)를 참조하세요.  

     Windows 7을 실행하는 디바이스에서 클라이언트 검사는 예약된 작업으로 실행됩니다. Windows 7 이후의 OS 버전에서는 Windows 유지 관리 기간 중에 클라이언트 검사가 자동으로 실행됩니다.  

     중요 비즈니스용 서버와 같은 특정 디바이스에서 수정 작업을 실행하지 않도록 구성할 수 있습니다. 평가하려는 추가 항목이 있는 경우 Configuration Manager 준수 설정을 사용하여 추가 구성을 모니터링합니다. 준수 설정에 대한 자세한 내용은 [준수 설정 계획 및 구성](/sccm/compliance/plan-design/plan-for-and-configure-compliance-settings)을 참조하세요.  

- **서비스 해제됨**: 사이트는 디바이스에 삭제용 레코드를 표시합니다. 이 동작은 동일한 디바이스에 대한 새 등록을 계층의 동일하거나 다른 기본 사이트에 할당하는 경우 발생할 수 있습니다. 사이트는 다음번에 사이트 유지 관리 작업, **오래된 검색 데이터 삭제**를 실행할 때 이러한 디바이스를 삭제합니다.<!-- SCCMDocs issue #1418 -->  

- **사용되지 않음**: 사이트는 동일한 하드웨어 ID 사용하여 새 디바이스 레코드를 검색했으므로 오래된 레코드를 사용되지 않음으로 표시합니다. 보고서는 동일한 디바이스의 사용되지 않는 레코드를 여러 번 계산하지 않습니다. 사용되지 않는 디바이스를 여전히 정책 대상으로 지정할 수 있습니다. 사이트는 90일 동안 비활성 상태였다가 사용되지 않는 레코드의 하트비트를 받지 못하면 사이트 유지 관리 작업인 **사용되지 않는 클라이언트 검색 데이터 삭제**를 실행할 때 사용되지 않는 디바이스를 제거합니다.


## <a name="bkmk_indStatus"></a> 개별 클라이언트 모니터링

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다. **디바이스** 노드 또는 **디바이스 컬렉션** 아래의 컬렉션을 선택합니다.  

    각 행의 시작 부분에 있는 아이콘은 디바이스의 온라인 상태를 나타냅니다.  

    |||  
    |-|-|  
    |![클라이언트에 대한 온라인 상태 아이콘](../../../core/clients/manage/media/online-status-icon.png)|디바이스가 온라인임|  
    |![클라이언트에 대한 오프라인 상태 아이콘](../../../core/clients/manage/media/offline-status-icon.png)|디바이스가 오프라인임|  
    |![클라이언트에 대한 알 수 없는 상태 아이콘](../../../core/clients/manage/media/unknown-status-icon.png)|온라인 상태를 알 수 없음|  
    |![클라이언트 설치 안 됨](../../../core/clients/manage/media/client-not-installed.png)|클라이언트가 디바이스에 설치되지 않음|  

2. 자세한 온라인 상태를 보려면 디바이스 보기에 클라이언트 온라인 상태 정보를 추가합니다. 열 머리글을 마우스 오른쪽 단추로 클릭하고 추가하려는 온라인 상태 필드를 선택합니다.

    - **디바이스 온라인 상태**: 클라이언트가 현재 온라인 상태인지 또는 오프라인 상태인지를 나타냅니다. 이 상태는아이콘으로 제공되는 것과 동일한 정보입니다.  

    - **마지막 온라인 시간**: 클라이언트 온라인 상태가 오프라인에서 온라인으로 변경되었을 때를 나타냅니다.  

    - **마지막 오프라인 시간**상태가 오프라인으로 변경되었을 때를 나타냅니다.  

3. 목록 창의 개별 클라이언트를 선택하여 세부 정보 창에서 자세한 상태를 확인합니다. 이 정보는 클라이언트 작업 및 클라이언트 검사 상태를 포함합니다.  


## <a name="bkmk_allStatus"></a> 모든 클라이언트의 상태 모니터링

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **클라이언트 상태** 노드를 선택합니다. 전체 사이트에 걸쳐 클라이언트 활동 및 클라이언트 검사에 대한 전체 통계를 검토합니다. 여러 컬렉션을 선택하여 정보의 범위를 변경합니다.  

2. 보고된 통계의 세부 정보로 드릴다운하려면 보고된 정보의 이름을 선택합니다. **클라이언트 검사를 통과했거나 결과가 없는 활성 클라이언트**를 예로 들 수 있습니다. 그런 후 개별 클라이언트에 대한 정보를 검토합니다.  

3. **클라이언트 활동**을 선택하여 Configuration Manager 사이트에서 클라이언트 활동을 보여 주는 차트를 표시합니다.  

4. **클라이언트 검사**를 선택하여 Configuration Manager 사이트에서 클라이언트 검사의 상태를 표시합니다.  

    클라이언트 검사 결과 또는 클라이언트 활동이 지정된 백분율 밑으로 떨어질 때 알리도록 경고를 구성합니다. 또한 사이트는 지정된 백분율의 클라이언트를 대상으로 수정에 실패할 때 경고할 수 있습니다. 자세한 내용은 [클라이언트 상태를 구성하는 방법](/sccm/core/clients/deploy/configure-client-status)을 참조하세요.  


## <a name="BKMK_ClientHealth"></a> 클라이언트 상태 검사

클라이언트 검사는 다음 검사 및 수정 작업을 실행합니다.  

|클라이언트 검사|재구성 작업|추가 정보|  
|------------------|------------------------|----------------------|  
|클라이언트 검사가 최근에 실행되었는지 확인|클라이언트 검사 실행|지난 3일간 클라이언트 검사가 1회 이상 실행되었는지 검사합니다.|  
|클라이언트 필수 구성 요소가 설치되었는지 확인|클라이언트 필수 구성 요소 설치|클라이언트 필수 구성 요소가 설치되었는지 검사합니다. 필수 구성 요소 검색을 위해 클라이언트 설치 폴더에서 ccmsetup.xml 파일을 읽습니다.|  
|WMI 저장소 무결성 테스트|Configuration Manager 클라이언트 다시 설치|WMI에 Configuration Manager 클라이언트 항목이 있는지 검사합니다.|  
|클라이언트 서비스가 실행 중인지 확인|클라이언트(SMS 에이전트 호스트) 서비스 시작|추가 정보 없음|  
|WMI 이벤트 싱크 테스트|클라이언트 서비스 다시 시작|Configuration Manager 관련 WMI 이벤트 싱크가 손실되었는지 검사합니다.|  
|WMI(Windows Management Instrumentation) 서비스가 있는지 확인|해결 방법 없음|추가 정보 없음|  
|클라이언트가 올바르게 설치되었는지 확인|클라이언트 다시 설치|추가 정보 없음|  
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
|Windows 8 디바이스의 Windows 업데이트 서비스 시작 유형이 자동 또는 수동인지 확인|서비스 시작 유형을 '수동'으로 다시 설정|추가 정보 없음|  
|클라이언트(SMS 에이전트 호스트) 서비스가 존재하는지 확인|해결 방법 없음|추가 정보 없음|  
|Configuration Manager 원격 제어 서비스 시작 유형이 자동 또는 수동인지 확인|서비스 시작 유형을 '자동'으로 다시 설정|추가 정보 없음|  
|Configuration Manager 원격 제어 서비스가 실행 중인지 확인|원격 제어 서비스를 시작|추가 정보 없음|  
|절전 모드 해제 프록시 서비스(ConfigMgr 절전 모드 해제 프록시)가 실행 중인지 확인|ConfigMgr 절전 모드 해제 프록시 서비스를 시작|이 클라이언트 검사는 지원되는 클라이언트 운영 체제에서 **전원 관리**: **절전 모드 해제 프록시 사용** 클라이언트 설정이 **예**로 설정된 경우에만 수행됩니다.|  
|절전 모드 해제 프록시 서비스(ConfigMgr 절전 모드 해제 프록시) 시작 유형이 자동인지 확인|ConfigMgr 절전 모드 해제 프록시 서비스 시작 유형을 '자동'으로 다시 설정|이 클라이언트 검사는 지원되는 클라이언트 운영 체제에서 **전원 관리**: **절전 모드 해제 프록시 사용** 클라이언트 설정이 **예**로 설정된 경우에만 수행됩니다.|  


<!-- 
5/31/2019 ACz: need to confirm if these checks are still applicable
|WMI repository read and write test|Reset the WMI repository and reinstall the Configuration Manager client|Remediation of this client check is only performed on devices that run Windows Server 2003, Windows XP (64-bit) or earlier versions.|  
|Verify that the client WMI provider is healthy|Restart the Windows Management Instrumentation service|Remediation of this client check is only performed on devices that run Windows Server 2003, Windows XP (64-bit) or earlier.|  
 -->


## <a name="client-deployment-log-files"></a>클라이언트 배포 로그 파일

클라이언트 배포 및 관리 작업에 사용되는 로그 파일에 대한 내용은 [로그 파일](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs)을 참조하세요.
