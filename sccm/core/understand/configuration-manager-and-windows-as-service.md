---
title: Configuration Manager 및 Windows as a Service
titleSuffix: Configuration Manager
description: Configuration Manager 현재 분기를 채택하여 Windows as a Service를 지원하는 데 필요한 기본 정보를 얻을 수 있습니다.
ms.date: 06/15/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c8534a1e-57b8-4688-b6e6-299d82cfcec9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e2fb6b022526ce4bae1de21012ac996dbcea35cf
ms.sourcegitcommit: 4b8afbd08ecf8fd54950eeb630caf191d3aa4767
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36260910"
---
# <a name="configuration-manager-and-windows-as-a-service"></a>Configuration Manager 및 Windows as a Service

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 Windows 10의 기능 업데이트를 포괄적으로 제어합니다. Windows as a Service 모델을 완전히 채택하려면 Configuration Manager 현재 분기 모델도 채택해야 합니다. Windows 10을 최신 상태로 유지하려면 최상의 환경을 위해 Configuration Manager를 최신 상태로 유지해야 합니다. 새 버전의 Configuration Manager는 Windows 10의 흥미롭고 새로운 엔터프라이즈 기능을 최대한 활용해야 합니다. 이 문서는 Configuration Manager 현재 분기를 채택하는 데 필요한 주요 문서의 방문 페이지로 사용됩니다. Configuration Manager 현재 분기는 Windows as a Service로 안내합니다.

## <a name="key-articles-about-adopting-configuration-manager-current-branch"></a>Configuration Manager 현재 분기 채택에 관한 주요 문서

| 문서        | 설명          | 
| ------------- |-------------|
|[Configuration Manager 현재 분기의 개요](/sccm/core/plan-design/changes/whats-new-incremental-versions)|Configuration Manager(현재 분기)에 대한 새로운 서비스 모델의 주요 사항을 간략하게 요약합니다.|
|[제품 지원 기간](/sccm/core/servers/manage/current-branch-versions-supported)|새로운 지원 및 서비스 모델에 대해 설명합니다.|
|[제거되는 항목과 사용되지 않는 항목](/sccm//core/plan-design/changes/deprecated/removed-and-deprecated)|Configuration Manager 사용에 영향을 줄 수 있는 향후 변경 사항에 대해 미리 알려드립니다.|
|[Configuration Manager 현재 분기 업데이트](/sccm/core/servers/manage/updates)|Configuration Manager에 기능 업데이트를 적용하는 것을 간편한 콘솔 방식으로 설명합니다.|
|[사용 가능 업데이트 가져오기](/sccm/core/servers/manage/install-in-console-updates#get-available-updates)|새로운 Configuration Manager 기능 업데이트를 가져오는 데 사용할 수 있는 두 가지 모드에 대해 설명합니다.|
|[업데이트 검사 목록](/sccm/core/servers/manage/install-in-console-updates#bkmk_beforeinstall)|해당되는 경우 업데이트 버전별 검사 목록을 제공합니다.| 
|[새로운 Configuration Manager 기능 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates#bkmk_install)|기능 업데이트의 간단한 설치 단계에 설명합니다.|
|[Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)|Windows 10(및 ADK) 버전에 대한 지원 매트릭스를 제공합니다.|
|[Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)|ConfigMgr Technical Preview 프로그램에 대한 정보를 제공합니다.|


## <a name="key-articles-about-adopting-windows-as-a-service"></a>Windows as a service 채택에 관한 주요 문서
| 문서        | 설명          | 
| ------------- |-------------|
|[Windows as a Service 관리](/sccm/osd/deploy-use/manage-windows-as-a-service)|서비스 계획을 사용하여 Windows 10 기능 업데이트를 배포하는 방법을 설명합니다.|
|[작업 순서를 통한 Windows 10 업그레이드](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)|추가 권장 사항으로 Windows 10을 업그레이드하기 위한 작업 순서 만드는 세부 정보입니다.|
|[단계별 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)|단계적 배포는 여러 컬렉션에서 작업 순서가 조정된 순차적 출시를 자동화합니다.|  
|[Windows 10 업데이트 전송 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)|Configuration Manager로 업데이트 콘텐츠를 관리하여 Windows 10으로 최신 상태를 유지합니다.|
|[업그레이드 준비와 통합](/sccm/core/clients/manage/upgrade/upgrade-analytics)|업그레이드 준비는 Windows 10으로 업그레이드하기 위해 사용자 환경에서 디바이스의 준비 상태를 평가하고 분석할 수 있습니다.| 
|[Windows Update for Business 통합(선택 사항)](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10)|Configuration Manager를 사용하여 WUfB(Windows Update for Business) 정책을 정의하고 배포하는 방법을 설명합니다.|
|[Microsoft Intune 및 Windows Update for Business와 공동 관리 사용(선택 사항)](/sccm/core/clients/manage/co-management-overview)|공동 관리의 개요를 제공합니다.| 


## <a name="related-articles"></a>관련 문서

- [ConfigMgr 2012에서 System Center Configuration Manager(현재 분기)로 전체 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
- [ConfigMgr 2007에서 System Center Configuration Manager(현재 분기)로 마이그레이션 계획](/sccm/core/migration/planning-for-migration)