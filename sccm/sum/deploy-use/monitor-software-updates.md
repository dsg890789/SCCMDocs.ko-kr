---
title: 소프트웨어 업데이트 모니터링
titleSuffix: Configuration Manager
description: System Center Configuration Manager 콘솔은 업데이트 및 준수를 모니터링하기 위해 경고 및 상태를 제공합니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 07/30/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9399900849ead41118cb727c3ec36cd8345e393b
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56133108"
---
# <a name="monitor-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 업데이트 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 소프트웨어 업데이트 개체, 프로세스 및 준수 정보를 모니터링할 수 있도록 여러 가지 방법을 제공합니다. 다음 섹션을 사용하여 소프트웨어 업데이트를 모니터링합니다.

## <a name="software-updates-dashboard"></a>소프트웨어 업데이트 대시보드
Configuration Manager 버전 1610부터 소프트웨어 업데이트 대시보드를 사용하여 조직 내 디바이스의 현재 준수 상태를 보고 데이터를 빠르게 분석하여 위험한 디바이스를 확인할 수 있습니다. 대시보드를 보려면 **모니터링** > **개요** > **보안** > **소프트웨어 업데이트 대시보드**로 이동합니다.   

##  <a name="BKMK_SUAlerts"></a> 소프트웨어 업데이트에 대한 경고  
 소프트웨어 업데이트에 대한 경고를 구성하여 소프트웨어 업데이트 배포의 호환성 수준이 구성된 백분율 이하인 경우 관리자에게 알릴 수 있습니다. 소프트웨어 업데이트 배포에 대한 경고는 다음 위치에서 구성할 수 있습니다.  

-   ADR 설정: 자동 배포 규칙 마법사 및 ADR의 속성에서 경고 설정을 구성할 수 있습니다.  

-   배포 설정: 소프트웨어 업데이트 배포 마법사뿐 아니라 배포 속성에서 경고 설정을 구성할 수 있습니다.  

경고 설정을 구성한 후 지정한 조건의 상황이 발생하면 Configuration Manager에서 경고가 생성됩니다. 소프트웨어 업데이트 경고는 다음 위치에서 검토할 수 있습니다.  

1.  **소프트웨어 라이브러리** 작업 영역의 **소프트웨어 업데이트** 노드에서 최신 경고를 검토할 수 있습니다.  

2.  **모니터링** 작업 영역의 **경고** 노드에서 구성된 경고를 관리할 수 있습니다.  

##  <a name="BKMK_SUSyncStatus"></a> 소프트웨어 업데이트 동기화 상태  
 동기화 프로세스를 시작한 후 Configuration Manager 콘솔에서 계층의 모든 소프트웨어 업데이트 지점에 대한 동기화 프로세스를 모니터링할 수 있습니다. 소프트웨어 업데이트 동기화 프로세스를 모니터링하려면 다음 절차를 따르세요.  

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>소프트웨어 업데이트 동기화 프로세스를 모니터링하려면  

- Configuration Manager 콘솔에서 **모니터링** > **개요** > **소프트웨어 업데이트 지점 동기화 상태**로 이동합니다.  

    Configuration Manager 계층 구조의 소프트웨어 업데이트 지점이 결과 창에 표시됩니다. 이 보기에서 모든 소프트웨어 업데이트 지점의 동기화 상태를 모니터링할 수 있습니다. 동기화 프로세스에 대한 자세한 내용은 각 사이트 서버의 <*ConfigMgrInstallationPath*>\Logs에 있는 wsyncmgr.log 파일을 참조하세요.  

##  <a name="BKMK_SUDeployStatus"></a> 소프트웨어 업데이트 배포 상태  
 소프트웨어 업데이트 그룹의 소프트웨어나 개별 소프트웨어 업데이트를 배포한 후 배포 상태를 모니터링할 수 있습니다. 소프트웨어 업데이트 그룹 또는 소프트웨어 업데이트의 배포 상태를 모니터링하려면 다음 절차를 따르세요.  

#### <a name="to-monitor-deployment-status"></a>배포 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포**로 이동합니다.  

2.  배포 상태를 모니터링하려는 소프트웨어 업데이트 그룹이나 소프트웨어 업데이트를 클릭합니다.  

3.  **홈** 탭의 **배포** 그룹에서 **상태 보기**를 클릭합니다.  

##  <a name="BKMK_SUReports"></a> 소프트웨어 업데이트 보고서  
 소프트웨어 업데이트의 상태 메시지에는 소프트웨어 업데이트의 호환성 정보와 소프트웨어 업데이트 배포의 평가 및 적용 상태가 나와 있습니다. 소프트웨어 업데이트 보고서를 실행하여 이러한 상태 메시지를 표시할 수 있습니다. 미리 정의된 소프트웨어 업데이트 보고서는 30개 이상 제공됩니다. 이러한 보고서는 여러 범주로 구성한 후 소프트웨어 업데이트 및 배포에 대한 특정 정보를 보고하는 데 사용될 수 있습니다. 미리 구성된 보고서 이외에도 사용자 기업의 필요에 따라 사용자 지정 소프트웨어 업데이트 보고서를 만들 수도 있습니다. 자세한 내용은 [보고 작업 및 유지 관리](../../core/servers/manage/operations-and-maintenance-for-reporting.md)를 참조하세요.  

### <a name="recommended-software-updates-reports"></a>권장되는 소프트웨어 업데이트 보고서
다음은 잠재적인 문제를 파악하는 데 유용한 몇 가지 보고서입니다. 

#### <a name="compliance-9---overall-health-and-compliance-starting-in-version-1806"></a>준수 9 - 전체 상태 및 준수(버전 1806부터 적용)
보고서에는 다음과 같은 부분이 포함됩니다.

- **정상 클라이언트 수 및 총 클라이언트 수**: 이 막대형 차트는 지정된 컬렉션의 총 클라이언트 수에 대해 지정된 기간에 사이트와 통신한 “정상” 상태의 클라이언트를 비교합니다.
- **규정 준수 개요**: 이 원형 차트는 지정된 컬렉션의 활성 클라이언트에 있는 특정 소프트웨어 업데이트 그룹의 전체 규정 준수 상태를 보여 줍니다.
- **상위 5개의 문서 ID별 비준수**: 이 막대형 차트는 지정된 컬렉션의 활성 클라이언트에서 비준수 상태인 지정된 그룹의 소프트웨어 업데이트 상위 5개를 표시합니다.
- 보고서의 맨 아래에는 추가 정보가 포함된 표가 있으며 지정된 그룹의 소프트웨어 업데이트를 나열합니다.

#### <a name="management-2---updates-required-but-not-deployed"></a>관리 2 - 필요하지만 배포되지 않은 업데이트

이 보고서는 클라이언트에 필요한 것으로 감지되었지만 특정 컬렉션에 배포되지 않은 특정 업데이트 분류에 공급 업체별 소프트웨어 업데이트를 표시합니다. 

#### <a name="troubleshooting-2---deployment-errors"></a>문제 해결 2 - 배포 오류

이 보고서는 사이트에서 발생한 배포 오류 및 각 오류가 발생한 컴퓨터 수를 반환합니다. 


##  <a name="BKMK_MonitorContent"></a> 콘텐츠 모니터링  
 Configuration Manager 콘솔에서 콘텐츠를 모니터링하여 연결된 배포 지점과 관련된 모든 패키지 유형의 상태를 검토할 수 있습니다. 여기에는 패키지의 콘텐츠에 대한 콘텐츠 유효성 검사 상태, 특정 배포 지점 그룹에 할당된 콘텐츠의 상태, 배포 지점에 할당된 콘텐츠의 상태, 각 배포 지점(콘텐츠 유효성 검사, PXE, 멀티캐스트 등)의 선택적 기능에 대한 상태 등이 포함됩니다.  

###  <a name="BKMK_ContentStatus"></a> 콘텐츠 상태 모니터링  
 **모니터링** 작업 영역의 **콘텐츠 상태** 노드에는 콘텐츠 패키지에 대한 정보가 제공됩니다. 패키지에 대한 일반 정보, 패키지의 배포 상태, 패키지의 세부적인 상태 정보 등을 검토할 수 있습니다. 콘텐츠 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-content-status"></a>콘텐츠 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포 상태** > **콘텐츠 상태**로 이동합니다. 패키지가 표시됩니다.  

2.  자세한 상태 정보를 볼 패키지를 선택합니다.  

3.  **홈** 탭에서 **상태 보기**를 클릭합니다. 패키지에 대한 자세한 상태 정보가 표시됩니다.  

###  <a name="BKMK_DPGroupStatus"></a> 배포 지점 그룹 상태  
 **모니터링** 작업 영역의 **배포 지점 그룹 상태** 노드에는 배포 지점 그룹에 대한 정보가 제공됩니다. 배포 지점 그룹 상태 및 호환성 비율과 같은 배포 지점 그룹에 대한 일반 정보와 더불어, 배포 지점 그룹의 자세한 상태 정보를 검토할 수 있습니다. 배포 지점 그룹 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-distribution-point-group-status"></a>배포 지점 그룹 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포 상태** > **배포 지점 그룹 상태**로 이동합니다. 배포 지점 그룹이 표시됩니다.  

2.  자세한 상태 정보를 볼 배포 지점 그룹을 선택합니다.  

3.  **홈** 탭에서 **상태 보기**를 클릭합니다. 배포 지점 그룹에 대한 자세한 상태 정보가 표시됩니다.  

###  <a name="BKMK_DPConfigStatus"></a> 배포 지점 구성 상태  
 **모니터링** 작업 영역의 **배포 지점 구성 상태** 노드에는 배포 지점에 대한 정보가 제공됩니다. PXE, 멀티캐스트, 콘텐츠 유효성 검사 등 배포 지점에 설정된 특성이 무엇인지 검토할 수 있습니다. 또한 배포 지점의 자세한 상태 정보를 볼 수도 있습니다. 배포 지점 구성 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>배포 지점 구성 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포 상태** > **배포 지점 구성 상태**로 이동합니다. 배포 지점이 표시됩니다.  

2.  배포 지점 상태 정보를 볼 배포 지점을 선택합니다.  

3.  결과 창에서 **세부 정보** 탭을 클릭합니다. 배포 지점에 대한 상태 정보가 표시됩니다.  
