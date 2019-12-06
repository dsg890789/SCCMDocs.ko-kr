---
title: 애플리케이션에 대한 관리 작업
titleSuffix: Configuration Manager
description: System Center Configuration Manager 애플리케이션 및 배포 유형을 관리합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: c4041e21-21ff-4d95-ab05-14007e0047cf
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 39548117fb7e03614af32fa330fb86bf6de4151e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70378060"
---
# <a name="management-tasks-for-system-center-configuration-manager-applications"></a>System Center Configuration Manager 애플리케이션에 대한 관리 작업

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 정보를 사용하여 System Center Configuration Manager 애플리케이션 및 배포 유형을 관리할 수 있습니다.  

애플리케이션 및 배포 유형을 만드는 방법에 대한 도움말은 [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.  

> [!IMPORTANT]  
>  애플리케이션 유형 또는 배포 유형에 따라 일부 관리 옵션을 사용하지 못할 수도 있습니다.  

##  <a name="manage-applications"></a>애플리케이션 관리  
 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리** > **애플리케이션**을 확장하고 관리할 애플리케이션을 선택한 다음 관리 작업을 선택합니다.  

|작업|세부 정보|  
|----------|-------------|  
|**액세스 계정 관리**|**액세스 계정 관리** 대화 상자를 엽니다. 여기서는 선택한 애플리케이션에 연결된 콘텐츠에 대해 허용되는 액세스 수준을 지정할 수 있습니다.|  
|**사전 준비된 콘텐츠 파일 만들기**|**사전 준비된 콘텐츠 파일 만들기 마법사** 를 엽니다. 이 마법사를 통해 원격 배포 지점에 대한 콘텐츠 배포를 손쉽게 관리할 수 있습니다. 원격 배포 지점에 대해 예약 및 제한을 사용하는 것이 효과가 없는 경우 배포 지점에서 콘텐츠를 사전에 준비할 수 있습니다.<br /><br /> [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|**수정 기록**|**애플리케이션 수정 기록** 대화 상자를 엽니다. 여기서 이 애플리케이션에 대한 수정 버전의 속성을 보고, 이전 애플리케이션 수정 버전을 삭제하며, 이 애플리케이션의 이전 버전을 복원할 수 있습니다.<br /><br /> [애플리케이션을 수정하고 교체하는 방법](../../apps/deploy-use/revise-and-supersede-applications.md)을 참조하세요.|  
|**배포 유형 만들기**|**배포 유형 만들기 마법사**를 엽니다. 여기서 선택한 애플리케이션에 새 배포 유형을 추가할 수 있습니다.<br /><br /> [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.|  
|**통계 업데이트**|**모니터링** 작업 영역의 **배포** 노드에 표시되는 이 애플리케이션 배포에 대한 정보를 업데이트합니다.<br /><br /> [System Center Configuration Manager 콘솔에서 애플리케이션 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)을 참조하세요.|  
|**복구**|**사용 중지** 관리 작업을 사용하여 사용이 중지된 애플리케이션을 복구합니다.|  
|**사용 중지**|애플리케이션을 사용 중지하면 더 이상 배포에 사용할 수 없지만 이 애플리케이션과 애플리케이션의 모든 배포가 삭제되지 않습니다. 클라이언트 컴퓨터에 설치된 이 애플리케이션의 기존 복사본은 제거되지 않습니다. 애플리케이션에 대한 모든 수정 사항은 60일 후 Configuration Manager에서 삭제됩니다. 그러나 설치된 애플리케이션 복사본은 제거되지 않습니다.<br /><br /> 애플리케이션을 삭제하려면 먼저 애플리케이션을 사용 중지하고 모든 배포를 삭제하고 이 애플리케이션에 대한 다른 배포의 참조를 제거한 후 애플리케이션의 모든 수정 버전을 삭제해야 합니다.<br /><br /> [애플리케이션 수정 및 대체](../../apps/deploy-use/revise-and-supersede-applications.md)를 참조하세요.|  
|**내보내기**|**애플리케이션 내보내기 마법사**를 엽니다. 여기에서 선택한 애플리케이션을 .zip 파일로 내보낸 후에 다른 사이트에 보관하거나 설치할 수 있습니다. 애플리케이션 콘텐츠를 내보내도록 선택하는 경우 해당 콘텐츠가 포함된 폴더가 만들어집니다.<br /><br /> 또한 애플리케이션 종속성, 교체 관계 및 조건, 애플리케이션 및 해당 종속성 콘텐츠를 내보낼 수 있습니다.<br /><br /> Windows PowerShell cmdlet인 **Export-CMApplication**도 이와 동일한 기능을 수행합니다. 자세한 내용은 Microsoft System Center 2012 Configuration Manager SP1 Cmdlet 참조 문서에서 [Export-CMApplication](https://go.microsoft.com/fwlink/p/?LinkID=258880)을 참조하세요.|  
|**삭제**|현재 선택된 애플리케이션을 삭제합니다.<br /><br /> 종속된 다른 애플리케이션이 있거나, 활성 배포가 있거나, 종속된 작업 순서가 있는 경우 애플리케이션을 삭제할 수 없습니다.|  
|**배포 시뮬레이트**|**애플리케이션 배포 시뮬레이트 마법사** 를 엽니다. 이 마법사를 통해 애플리케이션을 설치하거나 제거하지 않고도 컴퓨터에 대한 애플리케이션 배포 결과를 테스트할 수 있습니다.<br /><br /> [애플리케이션 배포 시뮬레이트](../../apps/deploy-use/simulate-application-deployments.md)를 참조하세요.|  
|**배포**|**소프트웨어 배포 마법사** 를 엽니다. 여기서 선택한 애플리케이션을 계층의 컴퓨터 컬렉션에 배포할 수 있습니다.<br /><br /> [애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.|  
|**콘텐츠 배포**|**콘텐츠 배포 마법사** 를 엽니다. 여기서 선택한 애플리케이션의 콘텐츠를 계층의 배포 지점으로 복사할 수 있습니다.<br /><br /> [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|**관계 보기**|선택한 애플리케이션과 다른 애플리케이션 간의 관계를 보여 주는 그래픽 다이어그램을 표시합니다. 다음 중 하나를 선택합니다.<br><br><ul><li>**종속성** – 선택한 애플리케이션에 종속된 애플리케이션과 선택한 애플리케이션이 종속된 애플리케이션을 표시합니다.</li><li>**대체** – 선택한 애플리케이션으로 인해 대체되는 애플리케이션과 선택한 애플리케이션을 대체하는 애플리케이션을 표시합니다.</li><li>**글로벌 조건** - 이 애플리케이션에서 참조하는 글로벌 조건을 표시합니다.</li></ol><br /> [애플리케이션 수정 및 대체](../../apps/deploy-use/revise-and-supersede-applications.md) 및 [글로벌 조건 만들기](../../apps/deploy-use/create-global-conditions.md)를 참조하세요.|  
|**애플리케이션 복사**|Configuration Manager 애플리케이션을 복사하거나 복제하여 새 애플리케이션을 만듭니다. 이 작업은 항목을 테스트하거나 유사한 애플리케이션을 만들어야 할 때 유용합니다. 사이트에서 이름에 **-copy**가 추가된 새 애플리케이션을 만듭니다. 사이트에서 메타데이터의 대부분을 새 애플리케이션에 복사하지만 배포를 복사하지는 않습니다.|

##  <a name="manage-deployment-types"></a>배포 유형 관리  
 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 확장하고 **애플리케이션**을 선택한 다음 관리할 배포 유형을 가진 애플리케이션을 선택합니다. 세부 정보 창에서 **배포 유형** 탭을 선택하고 관리할 배포 유형을 선택한 다음 관리 작업을 선택합니다.  

|작업|세부 정보|  
|----------|-------------|  
|**우선 순위 높이기**|선택한 배포 유형의 우선 순위를 높입니다. 배포 유형은 순서대로 평가됩니다. 지정된 요구 사항을 충족하는 배포 유형이 있으면 이 배포 유형이 실행되며, 우선 순위 목록에 있는 다른 배포 유형이 평가되지 않습니다.|  
|**우선순위 낮추기**|선택한 배포 유형의 우선 순위를 낮춥니다.|  
|**삭제**|선택한 배포 유형을 삭제합니다.<br><br>다른 애플리케이션의 배포 유형에서 참조되는 배포 유형은 삭제할 수 없습니다.<br>배포 유형을 삭제하려면 다른 배포 유형에 포함된 배포 유형에 대한 모든 종속성을 제거해야 합니다.<br>또한 삭제할 배포 유형을 참조하는 배포 유형이 포함된 모든 애플리케이션의 이전 수정 버전도 제거해야 합니다.|  
|**콘텐츠 업데이트**|선택한 배포 유형의 콘텐츠를 새로 고칩니다.<br /><br /> 가상 애플리케이션이 포함된 배포 유형에 대해 이 마법사를 시작하면 **콘텐츠 업데이트 마법사**가 시작됩니다. 이 마법사를 사용하여 선택한 가상 애플리케이션에 대한 게시 옵션과 요구 사항 규칙을 변경할 수 있습니다. 자세한 내용은 [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.<br /><br /> 배포 유형의 콘텐츠를 새로 고치면 애플리케이션의 새 수정 버전이 만들어집니다. 이로 인해 클라이언트 디바이스가 새 애플리케이션으로 업데이트될 수 있습니다.|  
