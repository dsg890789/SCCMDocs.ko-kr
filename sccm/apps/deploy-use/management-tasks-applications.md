---
title: 응용 프로그램에 대한 관리 작업
titleSuffix: Configuration Manager
description: System Center Configuration Manager 응용 프로그램 및 배포 유형을 관리합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: c4041e21-21ff-4d95-ab05-14007e0047cf
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 4cc6c423880850b40d67d35e990982583c39e54e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32334143"
---
# <a name="management-tasks-for-system-center-configuration-manager-applications"></a>System Center Configuration Manager 응용 프로그램에 대한 관리 작업

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 정보를 사용하여 System Center Configuration Manager 응용 프로그램 및 배포 유형을 관리할 수 있습니다.  

응용 프로그램 및 배포 유형을 만드는 방법에 대한 도움말은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.  

> [!IMPORTANT]  
>  응용 프로그램 유형 또는 배포 유형에 따라 일부 관리 옵션을 사용하지 못할 수도 있습니다.  

##  <a name="manage-applications"></a>응용 프로그램 관리  
 **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리** > **응용 프로그램**을 확장하고 관리할 응용 프로그램을 선택한 다음 관리 작업을 선택합니다.  

|작업|세부 정보|  
|----------|-------------|  
|**액세스 계정 관리**|**액세스 계정 관리** 대화 상자를 엽니다. 여기서는 선택한 응용 프로그램에 연결된 콘텐츠에 대해 허용되는 액세스 수준을 지정할 수 있습니다.|  
|**사전 준비된 콘텐츠 파일 만들기**|**사전 준비된 콘텐츠 파일 만들기 마법사** 를 엽니다. 이 마법사를 통해 원격 배포 지점에 대한 콘텐츠 배포를 손쉽게 관리할 수 있습니다. 원격 배포 지점에 대해 예약 및 제한을 사용하는 것이 효과가 없는 경우 배포 지점에서 콘텐츠를 사전에 준비할 수 있습니다.<br /><br /> [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|**수정 기록**|**응용 프로그램 수정 기록** 대화 상자를 엽니다. 여기서 이 응용 프로그램에 대한 수정 버전의 속성을 보고, 이전 응용 프로그램 수정 버전을 삭제하며, 이 응용 프로그램의 이전 버전을 복원할 수 있습니다.<br /><br /> [응용 프로그램을 수정하고 교체하는 방법](../../apps/deploy-use/revise-and-supersede-applications.md)을 참조하세요.|  
|**배포 유형 만들기**|**배포 유형 만들기 마법사**를 엽니다. 여기서 선택한 응용 프로그램에 새 배포 유형을 추가할 수 있습니다.<br /><br /> [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.|  
|**통계 업데이트**|**모니터링** 작업 영역의 **배포** 노드에 표시되는 이 응용 프로그램 배포에 대한 정보를 업데이트합니다.<br /><br /> [System Center Configuration Manager 콘솔에서 응용 프로그램 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)을 참조하세요.|  
|**복구**|**사용 중지** 관리 작업을 사용하여 사용이 중지된 응용 프로그램을 복구합니다.|  
|**사용 중지**|응용 프로그램을 사용 중지하면 더 이상 배포에 사용할 수 없지만 이 응용 프로그램과 응용 프로그램의 모든 배포가 삭제되지 않습니다. 클라이언트 컴퓨터에 설치된 이 응용 프로그램의 기존 복사본은 제거되지 않습니다. 응용 프로그램에 대한 모든 수정 사항은 60일 후 Configuration Manager에서 삭제됩니다. 그러나 설치된 응용 프로그램 복사본은 제거되지 않습니다.<br /><br /> 응용 프로그램을 삭제하려면 먼저 응용 프로그램을 사용 중지하고 모든 배포를 삭제하고 이 응용 프로그램에 대한 다른 배포의 참조를 제거한 후 응용 프로그램의 모든 수정 버전을 삭제해야 합니다.<br /><br /> [응용 프로그램 수정 및 대체](../../apps/deploy-use/revise-and-supersede-applications.md)를 참조하세요.|  
|**내보내기**|**응용 프로그램 내보내기 마법사**를 엽니다. 여기에서 선택한 응용 프로그램을 .zip 파일로 내보낸 후에 다른 사이트에 보관하거나 설치할 수 있습니다. 응용 프로그램 콘텐츠를 내보내도록 선택하는 경우 해당 콘텐츠가 포함된 폴더가 만들어집니다.<br /><br /> 또한 응용 프로그램 종속성, 교체 관계 및 조건, 응용 프로그램 및 해당 종속성 콘텐츠를 내보낼 수 있습니다.<br /><br /> Windows PowerShell cmdlet인 **Export-CMApplication**도 이와 동일한 기능을 수행합니다. 자세한 내용은 Microsoft System Center 2012 Configuration Manager SP1 Cmdlet 참조 문서에서 [Export-CMApplication](http://go.microsoft.com/fwlink/p/?LinkID=258880)을 참조하세요.|  
|**삭제**|현재 선택된 응용 프로그램을 삭제합니다.<br /><br /> 종속된 다른 응용 프로그램이 있거나, 활성 배포가 있거나, 종속된 작업 순서가 있는 경우 응용 프로그램을 삭제할 수 없습니다.|  
|**배포 시뮬레이트**|**응용 프로그램 배포 시뮬레이트 마법사** 를 엽니다. 이 마법사를 통해 응용 프로그램을 설치하거나 제거하지 않고도 컴퓨터에 대한 응용 프로그램 배포 결과를 테스트할 수 있습니다.<br /><br /> [응용 프로그램 배포 시뮬레이트](../../apps/deploy-use/simulate-application-deployments.md)를 참조하세요.|  
|**배포**|**소프트웨어 배포 마법사** 를 엽니다. 여기서 선택한 응용 프로그램을 계층의 컴퓨터 컬렉션에 배포할 수 있습니다.<br /><br /> [응용 프로그램 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.|  
|**콘텐츠 배포**|**콘텐츠 배포 마법사** 를 엽니다. 여기서 선택한 응용 프로그램의 콘텐츠를 계층의 배포 지점으로 복사할 수 있습니다.<br /><br /> [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|**관계 보기**|선택한 응용 프로그램과 다른 응용 프로그램 간의 관계를 보여 주는 그래픽 다이어그램을 표시합니다. 다음 중 하나를 선택합니다.<br><br><ul><li>**종속성** – 선택한 응용 프로그램에 종속된 응용 프로그램과 선택한 응용 프로그램이 종속된 응용 프로그램을 표시합니다.</li><li>**대체** – 선택한 응용 프로그램으로 인해 대체되는 응용 프로그램과 선택한 응용 프로그램을 대체하는 응용 프로그램을 표시합니다.</li><li>**글로벌 조건** - 이 응용 프로그램에서 참조하는 글로벌 조건을 표시합니다.</li></ol><br /> [응용 프로그램 수정 및 대체](../../apps/deploy-use/revise-and-supersede-applications.md) 및 [글로벌 조건 만들기](../../apps/deploy-use/create-global-conditions.md)를 참조하세요.|  

##  <a name="manage-deployment-types"></a>배포 유형 관리  
 **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리**를 확장하고 **응용 프로그램**을 선택한 다음 관리할 배포 유형을 가진 응용 프로그램을 선택합니다. 세부 정보 창에서 **배포 유형** 탭을 선택하고 관리할 배포 유형을 선택한 다음 관리 작업을 선택합니다.  

|작업|세부 정보|  
|----------|-------------|  
|**우선 순위 높이기**|선택한 배포 유형의 우선 순위를 높입니다. 배포 유형은 순서대로 평가됩니다. 지정된 요구 사항을 충족하는 배포 유형이 있으면 이 배포 유형이 실행되며, 우선 순위 목록에 있는 다른 배포 유형이 평가되지 않습니다.|  
|**우선순위 낮추기**|선택한 배포 유형의 우선 순위를 낮춥니다.|  
|**삭제**|선택한 배포 유형을 삭제합니다.<br><br>다른 응용 프로그램의 배포 유형에서 참조되는 배포 유형은 삭제할 수 없습니다.<br>배포 유형을 삭제하려면 다른 배포 유형에 포함된 배포 유형에 대한 모든 종속성을 제거해야 합니다.<br>또한 삭제할 배포 유형을 참조하는 배포 유형이 포함된 모든 응용 프로그램의 이전 수정 버전도 제거해야 합니다.|  
|**콘텐츠 업데이트**|선택한 배포 유형의 콘텐츠를 새로 고칩니다.<br /><br /> 가상 응용 프로그램이 포함된 배포 유형에 대해 이 마법사를 시작하면 **콘텐츠 업데이트 마법사**가 시작됩니다. 이 마법사를 사용하여 선택한 가상 응용 프로그램에 대한 게시 옵션과 요구 사항 규칙을 변경할 수 있습니다. 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.<br /><br /> 배포 유형의 콘텐츠를 새로 고치면 응용 프로그램의 새 수정 버전이 만들어집니다. 이로 인해 클라이언트 디바이스가 새 응용 프로그램으로 업데이트될 수 있습니다.|  
