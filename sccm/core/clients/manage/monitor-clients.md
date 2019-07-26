---
title: 클라이언트 모니터링
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라이언트를 모니터링하는 방법에 대한 자세한 지침을 가져옵니다.
ms.date: 07/12/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2c8f57cf-1968-48de-87fb-4897432ed6e0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9b3c3f52f15ba4d61a589833e43144ce5ecb6de0
ms.sourcegitcommit: b62de6c9cb1bc3e4c9ea5ab5ed3355d83e3a59bc
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894203"
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


## <a name="bkmk_health"></a> 클라이언트 상태 대시보드

<!--3599209-->
사용자의 환경을 보호하기 위해 소프트웨어 업데이트 및 기타 앱을 배포하지만 이러한 배포는 정상 클라이언트에만 적용됩니다. 비정상 Configuration Manager 클라이언트는 전반적인 규정 준수에 부정적인 영향을 줍니다. 클라이언트 상태 확인은 분모에 따라 어려울 수 있습니다. 관리 범위에 있어야 하는 총 디바이스는 몇 개인가요? 예를 들어 Active Directory에서 모든 시스템을 검색 하는 경우 이러한 레코드의 일부가 사용 중지된 머신에 해당된다 해도 이 프로세스는 분모를 증가시킵니다.

버전 1902부터 사용자 환경에서 Configuration Manager 클라이언트의 상태에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 클라이언트 상태, 시나리오 상태 및 일반적인 오류를 봅니다. OS 및 클라이언트 버전으로 잠재적인 문제를 확인하려면 몇 가지 특성으로 뷰를 필터링합니다.

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동합니다. **클라이언트 상태**를 확장하고 **클라이언트 상태 대시보드** 노드를 선택합니다.

![클라이언트 상태 대시보드 스크린샷](media/3599209-client-health-dashboard.png)

> [!Tip]  
> ccmeval에 대한 변경 내용이 없습니다.  

클라이언트 상태 대시보드는 기본적으로 온라인 클라이언트와 지난 3일간 활성 상태에 있었던 클라이언트를 표시합니다. 따라서 이 대시보드에 표시되는 숫자가 **클라이언트 상태** 아래의 다른 노드나 클라이언트 상태 범주의 보고서와 같은 여타 클라이언트 상태 이력 소스에 표시되는 숫자와 다를 수 있습니다.

### <a name="filters"></a>필터

대시보드 맨 위의 대시보드에 표시되는 데이터를 조정하기 위한 필터 집합이 있습니다.

- **컬렉션**: 기본적으로 대시보드는 **모든 시스템** 컬렉션에 디바이스를 표시합니다. 목록에서 디바이스 컬렉션을 선택하여 특정 컬렉션에서 디바이스 하위 집합에 대한 보기의 범위를 지정합니다.  

- **온라인/오프라인**: 기본적으로 대시보드는 온라인 클라이언트만 표시합니다. 이 상태는 5분마다 클라이언트의 상태를 업데이트하는 클라이언트 알림 채널에서 제공됩니다. 자세한 내용은 [클라이언트 상태 정보](/sccm/core/clients/manage/monitor-clients#bkmk_about)를 참조하세요.  

- **활성화 \# 일**: 기본적으로 대시보드는 지난 3일 동안 활성화된 클라이언트를 표시합니다.  

- **오류만**: 클라이언트 상태 오류를 보고 하는 디바이스에 대해서만 보기의 범위를 지정합니다.  

    > [!Tip]  
    > 클라이언트 버전 및 OS 버전 타일과 함께 이 필터를 사용합니다. 자세한 내용은 [버전 타일](#version-tiles)을 참조하세요.

### <a name="client-health-percentage"></a>클라이언트 상태 백분율

이 타일은 계층 구조의 전반적인 클라이언트 상태를 표시합니다.

정상 Configuration Manager 클라이언트에는 다음 속성이 있습니다.

- Online  
- 적극적으로 데이터 전송하기  
- 모든 클라이언트 상태 평가 통과 확인  

자세한 내용은 [클라이언트 상태 정보](/sccm/core/clients/manage/monitor-clients#bkmk_about)를 참조하세요.

정상 클라이언트는 사이트와 성공적으로 통신합니다. 클라이언트 설정에서 정의된 일정에 따라 모든 데이터를 보고합니다.

이 차트의 세그먼트를 선택하여 디바이스 목록 보기로 드릴다운합니다.

### <a name="version-tiles"></a>버전 타일

Configuration Manager 클라이언트 버전 및 OS 버전으로 클라이언트 상태를 표시하는 두 개의 타일이 있습니다. 이러한 타일은 **오류만**과 같이 필터를 변경하는 경우 유용합니다. 이러한 타일은 특정 버전에서 문제가 일관되는지 여부를 강조 표시할 수 있습니다. 이 정보를 사용하여 업그레이드 결정을 내릴 수 있습니다.

이러한 차트의 세그먼트를 선택하여 디바이스 목록 보기로 드릴다운합니다.

### <a name="scenario-health"></a>시나리오 상태

이 막대형 차트에는 다음 핵심 시나리오에 대한 전반적인 상태가 표시됩니다.

- 클라이언트 정책
- 하트비트 검색
- 하드웨어 인벤토리
- 소프트웨어 인벤토리
- 상태 메시지

차트에서 특정 시나리오에 대한 초점을 조정하려면 선택기를 사용합니다.

다음 두 개의 막대는 항상 다음과 같이 표시됩니다.

- **결합됨(모두)** : 모든 시나리오의 조합(AND)  
- **결합됨(임의)** : 하나 이상의 시나리오(OR)

> [!Tip]  
> 시나리오 상태는 클라이언트 설정의 구성에서 측정되지 않습니다. 이러한 값은 디바이스당 정책의 결과 세트에 따라 달라질 수 있습니다. 시나리오 상태에 대한 평가 기간을 조정하려면 다음 단계를 사용합니다.
>
> - Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **클라이언트 상태** 노드를 선택합니다.  
> - 리본 메뉴에서 **클라이언트 상태 설정**을 선택합니다.  
>
> 기본적으로 클라이언트가 **7일** 안에 시나리오별 데이터를 보내지 않는 경우 Configuration Manager에서는 해당 시나리오를 비정상으로 간주합니다.

### <a name="top-10-client-health-failures"></a>상위 10개 클라이언트 상태 오류

이 차트에는 사용자 환경에서 가장 일반적인 오류가 나열됩니다. 이러한 오류는 Windows 또는 Configuration Manager에서 제공됩니다.

<!-- The following list includes some of the more common failures overall:

#### Failure 1 title
Failure 1 description

Solution for failure 1 -->


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
