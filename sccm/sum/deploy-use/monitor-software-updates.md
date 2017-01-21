---

title: "소프트웨어 업데이트 모니터링 | Microsoft 문서"
description: "System Center Configuration Manager 콘솔은 업데이트 및 준수를 모니터링하기 위해 경고 및 상태를 제공합니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
translationtype: Human Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 956ef263a1c178b5ab5926705859f4b2d0ae5bc7

---
# <a name="monitor-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 소프트웨어 업데이트 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 소프트웨어 업데이트 개체, 프로세스 및 준수 정보를 모니터링할 수 있도록 여러 가지 방법을 제공합니다. 다음 섹션을 사용하여 소프트웨어 업데이트를 모니터링합니다.

## <a name="software-updates-dashboard"></a>소프트웨어 업데이트 대시보드
Configuration Manager 버전 1610부터 소프트웨어 업데이트 대시보드를 사용하여 조직 내 장치의 현재 준수 상태를 보고 데이터를 빠르게 분석하여 위험한 장치를 확인할 수 있습니다. 대시보드를 보려면 **모니터링** > **개요** > **보안** > **소프트웨어 업데이트 대시보드**로 이동합니다.   

##  <a name="a-namebkmksualertsa-alerts-for-software-updates"></a><a name="BKMK_SUAlerts"></a> 소프트웨어 업데이트에 대한 경고  
 소프트웨어 업데이트에 대한 경고를 구성하여 소프트웨어 업데이트 배포의 호환성 수준이 구성된 백분율 이하인 경우 관리자에게 알릴 수 있습니다. 소프트웨어 업데이트 배포에 대한 경고는 다음 위치에서 구성할 수 있습니다.  

-   ADR 설정: 자동 배포 규칙 마법사 및 ADR의 속성에서 경고 설정을 구성할 수 있습니다.  

-   배포 설정: 소프트웨어 업데이트 배포 마법사뿐 아니라 배포 속성에서 경고 설정을 구성할 수 있습니다.  

경고 설정을 구성한 후 지정한 조건의 상황이 발생하면 Configuration Manager에서 경고가 생성됩니다. 소프트웨어 업데이트 경고는 다음 위치에서 검토할 수 있습니다.  

1.  **소프트웨어 라이브러리** 작업 영역의 **소프트웨어 업데이트** 노드에서 최신 경고를 검토할 수 있습니다.  

2.  **모니터링** 작업 영역의 **경고** 노드에서 구성된 경고를 관리할 수 있습니다.  

##  <a name="a-namebkmksusyncstatusa-software-updates-synchronization-status"></a><a name="BKMK_SUSyncStatus"></a> 소프트웨어 업데이트 동기화 상태  
 동기화 프로세스를 시작한 후 Configuration Manager 콘솔에서 계층의 모든 소프트웨어 업데이트 지점에 대한 동기화 프로세스를 모니터링할 수 있습니다. 소프트웨어 업데이트 동기화 프로세스를 모니터링하려면 다음 절차를 따르세요.  

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>소프트웨어 업데이트 동기화 프로세스를 모니터링하려면  

- Configuration Manager 콘솔에서 **모니터링** > **개요** > **소프트웨어 업데이트 지점 동기화 상태**로 이동합니다.  

    Configuration Manager 계층 구조의 소프트웨어 업데이트 지점이 결과 창에 표시됩니다. 이 보기에서 모든 소프트웨어 업데이트 지점의 동기화 상태를 모니터링할 수 있습니다. 동기화 프로세스에 대한 자세한 내용은 각 사이트 서버의 <*ConfigMgrInstallationPath*>\Logs에 있는 wsyncmgr.log 파일을 참조하세요.  

##  <a name="a-namebkmksudeploystatusa-software-update-deployment-status"></a><a name="BKMK_SUDeployStatus"></a> 소프트웨어 업데이트 배포 상태  
 소프트웨어 업데이트 그룹의 소프트웨어나 개별 소프트웨어 업데이트를 배포한 후 배포 상태를 모니터링할 수 있습니다. 소프트웨어 업데이트 그룹 또는 소프트웨어 업데이트의 배포 상태를 모니터링하려면 다음 절차를 따르세요.  

#### <a name="to-monitor-deployment-status"></a>배포 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포**로 이동합니다.  

2.  배포 상태를 모니터링하려는 소프트웨어 업데이트 그룹이나 소프트웨어 업데이트를 클릭합니다.  

3.  **홈** 탭의 **배포** 그룹에서 **상태 보기**를 클릭합니다.  

##  <a name="a-namebkmksureportsa-software-updates-reports"></a><a name="BKMK_SUReports"></a> 소프트웨어 업데이트 보고서  
 소프트웨어 업데이트의 상태 메시지에는 소프트웨어 업데이트의 호환성 정보와 소프트웨어 업데이트 배포의 평가 및 적용 상태가 나와 있습니다. 소프트웨어 업데이트 보고서를 실행하여 이러한 상태 메시지를 표시할 수 있습니다. 미리 정의된 소프트웨어 업데이트 보고서는 30개 이상 제공됩니다. 이러한 보고서는 여러 범주로 구성한 후 소프트웨어 업데이트 및 배포에 대한 특정 정보를 보고하는 데 사용될 수 있습니다. 미리 구성된 보고서 이외에도 사용자 기업의 필요에 따라 사용자 지정 소프트웨어 업데이트 보고서를 만들 수도 있습니다. 자세한 내용은 [보고 작업 및 유지 관리](../../core/servers/manage/operations-and-maintenance-for-reporting.md)를 참조하세요.  

##  <a name="a-namebkmkmonitorcontenta-monitor-content"></a><a name="BKMK_MonitorContent"></a> 콘텐츠 모니터링  
 Configuration Manager 콘솔에서 콘텐츠를 모니터링하여 연결된 배포 지점과 관련된 모든 패키지 유형의 상태를 검토할 수 있습니다. 여기에는 패키지의 콘텐츠에 대한 콘텐츠 유효성 검사 상태, 특정 배포 지점 그룹에 할당된 콘텐츠의 상태, 배포 지점에 할당된 콘텐츠의 상태, 각 배포 지점(콘텐츠 유효성 검사, PXE, 멀티캐스트 등)의 선택적 기능에 대한 상태 등이 포함됩니다.  

###  <a name="a-namebkmkcontentstatusa-content-status-monitoring"></a><a name="BKMK_ContentStatus"></a> 콘텐츠 상태 모니터링  
 **모니터링** 작업 영역의 **콘텐츠 상태** 노드에는 콘텐츠 패키지에 대한 정보가 제공됩니다. 패키지에 대한 일반 정보, 패키지의 배포 상태, 패키지의 세부적인 상태 정보 등을 검토할 수 있습니다. 콘텐츠 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-content-status"></a>콘텐츠 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포 상태** > **콘텐츠 상태**로 이동합니다. 패키지가 표시됩니다.  

2.  자세한 상태 정보를 볼 패키지를 선택합니다.  

3.  **홈** 탭에서 **상태 보기**를 클릭합니다. 패키지에 대한 자세한 상태 정보가 표시됩니다.  

###  <a name="a-namebkmkdpgroupstatusa-distribution-point-group-status"></a><a name="BKMK_DPGroupStatus"></a> 배포 지점 그룹 상태  
 **모니터링** 작업 영역의 **배포 지점 그룹 상태** 노드에는 배포 지점 그룹에 대한 정보가 제공됩니다. 배포 지점 그룹 상태 및 호환성 비율과 같은 배포 지점 그룹에 대한 일반 정보와 더불어, 배포 지점 그룹의 자세한 상태 정보를 검토할 수 있습니다. 배포 지점 그룹 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-distribution-point-group-status"></a>배포 지점 그룹 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포 상태** > **배포 지점 그룹 상태**로 이동합니다. 배포 지점 그룹이 표시됩니다.  

2.  자세한 상태 정보를 볼 배포 지점 그룹을 선택합니다.  

3.  **홈** 탭에서 **상태 보기**를 클릭합니다. 배포 지점 그룹에 대한 자세한 상태 정보가 표시됩니다.  

###  <a name="a-namebkmkdpconfigstatusa-distribution-point-configuration-status"></a><a name="BKMK_DPConfigStatus"></a> 배포 지점 구성 상태  
 **모니터링** 작업 영역의 **배포 지점 구성 상태** 노드에는 배포 지점에 대한 정보가 제공됩니다. PXE, 멀티캐스트, 콘텐츠 유효성 검사 등 배포 지점에 설정된 특성이 무엇인지 검토할 수 있습니다. 또한 배포 지점의 자세한 상태 정보를 볼 수도 있습니다. 배포 지점 구성 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>배포 지점 구성 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **배포 상태** > **배포 지점 구성 상태**로 이동합니다. 배포 지점이 표시됩니다.  

2.  배포 지점 상태 정보를 볼 배포 지점을 선택합니다.  

3.  결과 창에서 **세부 정보** 탭을 클릭합니다. 배포 지점에 대한 상태 정보가 표시됩니다.  



<!--HONumber=Dec16_HO3-->


