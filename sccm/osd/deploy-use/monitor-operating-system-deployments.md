---
title: "운영 체제 배포 모니터링 | Microsoft 문서"
description: "운영 체제 배포 개체를 모니터링할 수 있도록 돕기 위해 Configuration Manager 콘솔에서는 경고, 보고서 및 다양한 상태 표시기를 제공합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08085d94-295c-432f-b5e3-9736bce0193b
caps.latest.revision: 6
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 154c0a286e6b9ccedc7545eb010967ac00d35407


---
# <a name="monitor-operating-system-deployments-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 운영 체제 배포 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

운영 체제 배포 개체를 모니터링할 수 있도록 돕기 위해 Configuration Manager 콘솔에서는 다양한 방법을 제공합니다.  


##  <a name="a-namebkmkosdalertsa-alerts-for-operating-system-deployments"></a><a name="BKMK_OSDAlerts"></a> 운영 체제 배포에 대한 경고  
 작업 순서 배포 설정의 경고를 구성하여 배포의 준수 수준이 구성된 백분율 이하인 경우 관리자에게 알릴 수 있습니다.  

 경고 설정을 구성한 후 지정한 조건의 상황이 발생하면 Configuration Manager에서 경고가 생성됩니다. 다음 위치에서 작업 순서 배포 경고를 검토할 수 있습니다.  

1.  **소프트웨어 라이브러리** 작업 영역의 **운영 체제** 노드에서 최신 경고를 검토할 수 있습니다.  

2.  **모니터링** 작업 영역의 **경고** 노드에서 구성된 경고를 관리할 수 있습니다.  

##  <a name="a-namebkmktsdeploystatusa-task-sequence-deployment-status"></a><a name="BKMK_TSDeployStatus"></a> 작업 순서 배포 상태  
 작업 순서를 배포한 후 배포 상태를 모니터링할 수 있습니다. 작업 순서에 대한 배포 상태를 모니터링하려면 다음 절차를 따르세요.  

#### <a name="to-monitor-deployment-status"></a>배포 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  모니터링 작업 영역에서 **배포**를 클릭합니다.  

3.  배포 상태를 모니터링하려는 작업 순서를 클릭합니다.  

4.  **홈** 탭의 **배포** 그룹에서 **상태 보기**를 클릭합니다.  

##  <a name="a-namebkmktsreportsa-operating-system-deployment-reports"></a><a name="BKMK_TSReports"></a> 운영 체제 배포 보고서  
 미리 정의된 많은 운영 체제 배포 보고서를 사용할 수 있습니다. 이러한 보고서는 여러 범주로 구성한 후 상태 마이그레이션 및 작업 순서 배포에 대한 특정 정보를 보고하는 데 사용할 수 있습니다. 미리 구성된 보고서 이외에도 사용자 기업의 필요에 따라 사용자 지정 소프트웨어 업데이트 보고서를 만들 수도 있습니다. 자세한 내용은 [보고 작업 및 유지 관리](../../core/servers/manage/operations-and-maintenance-for-reporting.md)를 참조하세요.  

##  <a name="a-namebkmkmonitorcontenta-monitor-content"></a><a name="BKMK_MonitorContent"></a> 콘텐츠 모니터링  
 Configuration Manager 콘솔에서 콘텐츠를 모니터링하여 연결된 배포 지점과 관련된 모든 패키지 유형의 상태를 검토할 수 있습니다. 여기에는 패키지의 콘텐츠에 대한 콘텐츠 유효성 검사 상태, 특정 배포 지점 그룹에 할당된 콘텐츠의 상태, 배포 지점에 할당된 콘텐츠의 상태, 각 배포 지점(콘텐츠 유효성 검사, PXE, 멀티캐스트 등)의 선택적 기능에 대한 상태 등이 포함됩니다.  

###  <a name="a-namebkmkcontentstatusa-content-status-monitoring"></a><a name="BKMK_ContentStatus"></a> 콘텐츠 상태 모니터링  
 **모니터링** 작업 영역의 **콘텐츠 상태** 노드에는 콘텐츠 패키지에 대한 정보가 제공됩니다. 패키지에 대한 일반 정보, 패키지의 배포 상태, 패키지의 세부적인 상태 정보 등을 검토할 수 있습니다. 콘텐츠 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-content-status"></a>콘텐츠 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  모니터링 작업 영역에서 **배포 상태**를 확장한 후 **콘텐츠 상태**를 클릭합니다. 패키지가 표시됩니다.  

3.  자세한 상태 정보를 볼 패키지를 선택합니다.  

4.  **홈** 탭에서 **상태 보기**를 클릭합니다. 패키지에 대한 자세한 상태 정보가 표시됩니다.  

###  <a name="a-namebkmkdpgroupstatusa-distribution-point-group-status"></a><a name="BKMK_DPGroupStatus"></a> 배포 지점 그룹 상태  
 **모니터링** 작업 영역의 **배포 지점 그룹 상태** 노드에는 배포 지점 그룹에 대한 정보가 제공됩니다. 배포 지점 그룹 상태 및 호환성 비율과 같은 배포 지점 그룹에 대한 일반 정보와 더불어, 배포 지점 그룹의 자세한 상태 정보를 검토할 수 있습니다. 배포 지점 그룹 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-distribution-point-group-status"></a>배포 지점 그룹 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  모니터링 작업 영역에서 **배포 상태**를 확장한 후 **배포 지점 그룹 상태**를 클릭합니다. 배포 지점 그룹이 표시됩니다.  

3.  자세한 상태 정보를 볼 배포 지점 그룹을 선택합니다.  

4.  **홈** 탭에서 **상태 보기**를 클릭합니다. 배포 지점 그룹에 대한 자세한 상태 정보가 표시됩니다.  

###  <a name="a-namebkmkdpconfigstatusa-distribution-point-configuration-status"></a><a name="BKMK_DPConfigStatus"></a> 배포 지점 구성 상태  
 **모니터링** 작업 영역의 **배포 지점 구성 상태** 노드에는 배포 지점에 대한 정보가 제공됩니다. PXE, 멀티캐스트, 콘텐츠 유효성 검사 등 배포 지점에 설정된 특성이 무엇인지 검토할 수 있습니다. 또한 배포 지점의 자세한 상태 정보를 볼 수도 있습니다. 배포 지점 구성 상태를 보려면 다음 절차를 수행하세요.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>배포 지점 구성 상태를 모니터링하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  모니터링 작업 영역에서 **배포 상태**를 확장한 후 **배포 지점 구성 상태**를 클릭합니다. 배포 지점이 표시됩니다.  

3.  배포 지점 상태 정보를 볼 배포 지점을 선택합니다.  

4.  결과 창에서 **세부 정보** 탭을 클릭합니다. 배포 지점에 대한 상태 정보가 표시됩니다.  



<!--HONumber=Dec16_HO3-->


