---
title: "컬렉션 관리 | Microsoft 문서"
description: "System Center Configuration Manager에서 일반적인 컬렉션 관리 작업을 수행합니다."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e102fd1a-76df-4d8e-b1b0-10ee18318f67
caps.latest.revision: 8
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: b41b50c75f1b89c8fc712b53988bd8e24813106d
ms.lasthandoff: 12/16/2016


---
# <a name="how-to-manage-collections-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 컬렉션을 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 개요 정보를 참조하여 System Center Configuration Manager에서 컬렉션에 대한 관리 작업을 수행할 수 있습니다.  

> [!NOTE]  
>  Configuration Manager 컬렉션을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)을 참조하세요.  

## <a name="how-to-manage-device-collections"></a>장치 컬렉션을 관리하는 방법  
 **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 선택하고 관리할 컬렉션을 선택한 다음 관리 작업을 선택합니다.  

 다음 표에서는 선택 전에 약간의 정보가 필요할 수 있는 관리 작업에 대한 자세한 정보를 제공합니다.  

|관리 작업|세부 정보|추가 정보|  
|---------------------|-------------|----------------------|  
|**멤버 표시**|**장치** 노드의 임시 노드에 선택한 컬렉션의 멤버인 모든 리소스를 표시합니다.|추가 정보가 없습니다.|  
|**선택한 항목 추가**|다음 작업 중 하나를 수행하기 위해 다음 옵션을 제공합니다.<br /><br /> - <br />                    **선택한 항목을 기존 장치 컬렉션에 추가** - 선택한 컬렉션의 멤버를 추가하려는 컬렉션을 선택할 수 있는 **컬렉션 선택** 대화 상자를 엽니다. 선택한 컬렉션이 **컬렉션 포함** 멤버 관리 규칙을 사용하여 이 컬렉션에 포함됩니다.<br /><br /> - **선택한 항목을 새 장치 컬렉션에 추가** - 새 컬렉션을 만들 수 있는 **장치 컬렉션 만들기 마법사**를 엽니다. 선택한 컬렉션이 **컬렉션 포함** 멤버 관리 규칙을 사용하여 이 컬렉션에 포함됩니다.|[System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)|  
|**클라이언트 설치**|선택한 컬렉션의 모든 컴퓨터에서 Configuration Manager 클라이언트를 설치하기 위해 클라이언트 강제 설치를 사용하는 **클라이언트 설치 마법사**를 엽니다.|[System Center Configuration Manager에 대한 클라이언트 배포 작업](../../../../core/clients/deploy/client-deployment-tasks.md)|  
|**선호도 요청 관리**|보류 중인 요청을 승인하거나 거부하여 선택한 컬렉션의 장치에 대해 사용자 장치 선호도를 설정할 수 있는 **사용자 장치 선호도 요청 관리** 대화 상자를 엽니다.|[System Center Configuration Manager에서 사용자 장치 선호도를 사용하여 사용자와 장치 연결](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**필수 PXE 배포 지우기**|선택한 컬렉션의 모든 멤버에서 필수 PXE 부팅 배포를 지웁니다.|[운영 체제 배포 소개](../../../../osd/understand/introduction-to-operating-system-deployment.md)|  
|**멤버 자격 업데이트**|선택한 컬렉션에 대한 멤버 자격을 평가합니다. 멤버가 많은 컬렉션의 경우 이 업데이트를 완료하려면 다소 시간이 걸릴 수 있습니다. 업데이트가 완료된 후 **새로 고침** 작업을 사용하여 새 컬렉션 멤버로 화면 표시를 업데이트합니다.|추가 정보가 없습니다.|  
|**리소스 추가**|선택한 컬렉션에 추가할 새 리소스를 검색할 수 있는 **컬렉션에 리소스 추가** 대화 상자를 엽니다.<br /><br /> 업데이트가 진행되는 동안 선택한 컬렉션에 대한 아이콘이 모래 시계 기호를 표시합니다.|추가 정보가 없습니다.|  
|**클라이언트 알림**|선택한 장치 컬렉션의 모든 클라이언트에게 컴퓨터 또는 사용자 정책을 다운로드하라고 지시합니다.|추가 정보가 없습니다.|  
|**Endpoint Protection**|선택한 컬렉션의 컴퓨터에 대해 전체 또는 빠른 맬웨어 방지 검색을 수행하거나 최신 맬웨어 방지 정의를 다운로드합니다.|[System Center Configuration Manager의 Endpoint Protection](../../../../protect/deploy-use/endpoint-protection.md)|  
|**내보내기**|다른 Configuration Manager 사이트에서 보관하거나 사용할 수 있는 MOF(Managed Object Format) 파일에 이 컬렉션을 내보낼 수 있는 **컬렉션 내보내기 마법사**를 엽니다.<br /><br /> 컬렉션을 내보낼 때 **포함** 또는 **제외** 규칙을 사용하여 선택한 컬렉션에서 참조한 컬렉션은 내보낼 수 없습니다.|추가 정보가 없습니다.|  
|**복사**|선택한 컬렉션의 복사본을 만듭니다. 새 컬렉션은 선택한 컬렉션을 제한 컬렉션으로 사용합니다.|추가 정보가 없습니다.|  
|**삭제**|선택한 컬렉션을 삭제합니다. 사이트 데이터베이스에서 컬렉션의 모든 리소스를 삭제할 수도 있습니다.<br /><br /> Configuration Manager에 기본 제공된 컬렉션을 삭제할 수 없습니다.|기본 제공 컬렉션 목록을 보려면 [System Center Configuration Manager의 컬렉션 소개](../../../../core/clients/manage/collections/introduction-to-collections.md)를 참조하세요.|  
|**배포 시뮬레이트**|**응용 프로그램 배포 시뮬레이트 마법사** 를 엽니다. 이 마법사를 통해 응용 프로그램을 설치하거나 제거하지 않고도 응용 프로그램 배포 결과를 테스트할 수 있습니다.|[System Center Configuration Manager에서 응용 프로그램 배포를 시뮬레이트하는 방법](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**배포:**|다음 옵션이 표시됩니다.<br /><br /> - <br />                    **응용 프로그램** - 선택한 컬렉션에 대한 응용 프로그램 배포를 선택하고 구성할 수 있는 **소프트웨어 배포 마법사**를 엽니다.<br /><br /> - <br />                    **프로그램** – 선택한 컬렉션에 대한 패키지 및 프로그램 배포를 선택하고 구성할 수 있는 **소프트웨어 배포 마법사** 를 엽니다.<br /><br /> - **구성 기준** - 선택한 컬렉션에 하나 이상의 구성 기준 배포를 구성할 수 있는 **구성 기준 배포** 대화 상자를 엽니다.<br /><br /> - <br />                    **작업 순서** – 선택한 컬렉션에 대한 작업 시퀀스 배포를 선택하고 구성할 수 있는 **소프트웨어 배포 마법사** 를 엽니다.<br /><br /> - <br />                    **소프트웨어 업데이트** - 선택한 컬렉션의 리소스에 대해 소프트웨어 업데이트 배포를 구성할 수 있는 **소프트웨어 업데이트 배포 마법사**를 엽니다.|[System Center Configuration Manager에서 응용 프로그램을 배포하는 방법](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [System Center Configuration Manager의 패키지 및 프로그램](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [System Center Configuration Manager에서 구성 기준을 배포하는 방법](../../../../compliance/deploy-use/deploy-configuration-baselines.md)<br /><br /> [System Center Configuration Manager에서 작업을 자동화하는 작업 순서 관리](../../../../osd/deploy-use/manage-task-sequences-to-automate-tasks.md)<br /><br /> [System Center Configuration Manager에서 소프트웨어 업데이트 관리](/sccm/sum/understand/software-updates-introduction)|  

## <a name="how-to-manage-user-collections"></a>사용자 컬렉션을 관리하는 방법  
 **자산 및 준수** 작업 영역에서 **사용자 컬렉션**을 선택하고 관리할 컬렉션을 선택한 다음 관리 작업을 선택합니다.  

 다음 표에서는 선택 전에 약간의 정보가 필요할 수 있는 관리 작업에 대한 자세한 정보를 제공합니다.  

|관리 작업|세부 정보|추가 정보|  
|---------------------|-------------|----------------------|  
|**멤버 표시**|**사용자** 노드의 임시 노드에 선택한 컬렉션의 멤버인 모든 리소스를 표시합니다.|추가 정보가 없습니다.|  
|**선택한 항목 추가**|이 옵션으로 다음 작업 중 하나를 수행할 수 있습니다.<br /><br /> - <br />                    **선택한 항목을 기존 사용자 컬렉션에 추가** - 선택한 컬렉션의 멤버를 추가하려는 컬렉션을 선택할 수 있는 **컬렉션 선택** 대화 상자를 엽니다. 선택한 컬렉션이 **컬렉션 포함** 멤버 관리 규칙을 사용하여 이 컬렉션에 포함됩니다.<br /><br /> - **선택한 항목을 새 사용자 컬렉션에 추가** - 새 컬렉션을 만들 수 있는 **사용자 컬렉션 만들기 마법사**를 엽니다. 선택한 컬렉션이 **컬렉션 포함** 멤버 관리 규칙을 사용하여 이 컬렉션에 포함됩니다.|[System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)|  
|**선호도 요청 관리**|보류 중인 요청을 승인하거나 거부하여 선택한 컬렉션의 사용자에 대해 사용자 장치 선호도를 설정할 수 있는 **사용자 장치 선호도 요청 관리** 대화 상자를 엽니다.|[System Center Configuration Manager에서 사용자 장치 선호도를 사용하여 사용자와 장치 연결](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)|  
|**멤버 자격 업데이트**|선택한 컬렉션에 대한 멤버 자격을 평가합니다. 멤버가 많은 컬렉션의 경우 이 업데이트를 완료하려면 다소 시간이 걸릴 수 있습니다. 업데이트가 완료된 후 **새로 고침** 작업을 사용하여 새 컬렉션 멤버로 화면 표시를 업데이트합니다.<br /><br /> 업데이트가 진행되는 동안 선택한 컬렉션에 대한 아이콘이 모래 시계 기호를 표시합니다.|추가 정보가 없습니다.|  
|**리소스 추가**|선택한 컬렉션에 추가할 새 리소스를 검색할 수 있는 **컬렉션에 리소스 추가** 대화 상자를 엽니다.|추가 정보가 없습니다.|  
|**내보내기**|다른 Configuration Manager 사이트에서 보관하거나 사용할 수 있는 MOF(Managed Object Format) 파일에 이 컬렉션을 내보낼 수 있는 **컬렉션 내보내기 마법사**를 엽니다.<br /><br /> 컬렉션을 내보낼 때 **포함** 또는 **제외** 규칙을 사용하여 선택한 컬렉션에서 참조한 컬렉션은 내보낼 수 없습니다.|추가 정보가 없습니다.|  
|**복사**|선택한 컬렉션의 복사본을 만듭니다. 새 컬렉션은 선택한 컬렉션을 제한 컬렉션으로 사용합니다.|추가 정보가 없습니다.|  
|**삭제**|선택한 컬렉션을 삭제합니다. 사이트 데이터베이스에서 컬렉션의 모든 리소스를 삭제할 수도 있습니다.<br /><br /> Configuration Manager에 기본 제공된 컬렉션을 삭제할 수 없습니다.|기본 제공 컬렉션 목록을 보려면 [System Center Configuration Manager의 컬렉션 소개](../../../../core/clients/manage/collections/introduction-to-collections.md)를 참조하세요.|  
|**배포 시뮬레이트**|**응용 프로그램 배포 시뮬레이트 마법사** 를 엽니다. 이 마법사를 통해 응용 프로그램을 설치하거나 제거하지 않고도 응용 프로그램 배포 결과를 테스트할 수 있습니다.|[System Center Configuration Manager에서 응용 프로그램 배포를 시뮬레이트하는 방법](../../../../apps/deploy-use/simulate-application-deployments.md)|  
|**배포:**|다음 옵션이 표시됩니다.<br /><br /> - **응용 프로그램** - 선택한 컬렉션에 대한 응용 프로그램 배포를 선택하고 구성할 수 있는 **소프트웨어 배포 마법사**를 엽니다.<br /><br /> - <br />                    **프로그램** – 선택한 컬렉션에 대한 패키지 및 프로그램 배포를 선택하고 구성할 수 있는 **소프트웨어 배포 마법사** 를 엽니다.<br /><br /> - **구성 기준** - 선택한 컬렉션에 하나 이상의 구성 기준 배포를 구성할 수 있는 **구성 기준 배포** 대화 상자를 엽니다.|[System Center Configuration Manager에서 응용 프로그램을 배포하는 방법](../../../../apps/deploy-use/deploy-applications.md)<br /><br /> [System Center Configuration Manager의 패키지 및 프로그램](../../../../apps/deploy-use/packages-and-programs.md)<br /><br /> [System Center Configuration Manager에서 구성 기준을 배포하는 방법](../../../../compliance/deploy-use/deploy-configuration-baselines.md)|  

##  <a name="BKMK_CollProp"></a> 컬렉션 속성  
 컬렉션의 **속성** 대화 상자를 열면 컬렉션에 대한 다음 속성을 보고 구성할 수 있습니다.  

|탭 이름|추가 정보|  
|--------------|----------------------|  
|**일반**|컬렉션 이름 및 제한 컬렉션을 비롯한 선택한 컬렉션에 대한 일반 정보를 보고 구성할 수 있습니다.|  
|**멤버 관리 규칙**|이 컬렉션의 멤버 자격을 정의하는 멤버 관리 규칙을 구성할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../../core/clients/manage/collections/create-collections.md)을 참조하세요.|  
|**전원 관리**|선택한 컬렉션의 컴퓨터에 할당되는 전원 관리 계획을 구성할 수 있습니다. 자세한 내용은 [전원 관리 소개](../../../../core/clients/manage/power/introduction-to-power-management.md)를 참조하세요.|  
|**배포**|선택한 컬렉션의 멤버에게 배포된 모든 소프트웨어를 표시합니다.|  
|**유지 관리 기간**|선택한 컬렉션의 멤버에 적용되는 유지 관리 기간을 보고 구성할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 유지 관리 기간을 사용하는 방법](../../../../core/clients/manage/collections/use-maintenance-windows.md)을 참조하세요.|  
|**컬렉션 변수**|이 컬렉션에 적용하고 작업 순서에서 사용할 수 있는 변수를 구성할 수 있습니다. 자세한 내용은 [작업 순서 기본 제공 변수](../../../../osd/understand/task-sequence-built-in-variables.md)를 참조하세요.|  
|**배포 지점 그룹**|선택한 컬렉션의 멤버에 하나 이상의 배포 지점 그룹을 연결할 수 있습니다. 자세한 내용은 [System Center Configuration Manager용 콘텐츠 및 콘텐츠 인프라 관리](../../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|**보안**|연결된 역할 및 보안 범위에서 선택한 컬렉션에 대한 권한이 있는 관리자를 표시합니다.|  
|**모니터**|클라이언트 상태와 Endpoint Protection에 대해 경고가 생성되는 때를 구성할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 상태를 구성하는 방법](../../../../core/clients/deploy/configure-client-status.md) 및 [System Center Configuration Manager에서 Endpoint Protection을 모니터링하는 방법](../../../../protect/deploy-use/monitor-endpoint-protection.md)을 참조하세요.|  

