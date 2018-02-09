---
title: "Configuration Manager as a Service 및 Windows as a Service의 기본 사항"
titleSuffix: Configuration Manager
description: "Configuration Manager as a Service를 채택하여 Windows as a Service를 지원하는 데 필요한 기본 정보를 얻을 수 있습니다."
ms.custom: na
ms.date: 01/04/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c8534a1e-57b8-4688-b6e6-299d82cfcec9
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 40894c4ebb562e5c979f1226349ff91c38516618
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/01/2018
---
# <a name="keep-windows-10-up-to-date-in-the-enterprise-using-configuration-manager"></a>Configuration Manager를 사용하여 기업에서 Windows 10을 최신 상태로 유지

*적용 대상: System Center Configuration Manager(현재 분기), Windows 10(반기 채널)*

System Center Configuration Manager는 Windows 10의 기능 업데이트를 포괄적으로 제어합니다. Windows as a Service 모델을 완전히 채택하려면 Configuration Manager as a Service 모델도 채택해야 합니다. Windows 10을 최신 상태로 유지하려면 최상의 환경을 위해 Configuration Manager를 최신 상태로 유지해야 합니다. 새 버전의 Configuration Manager는 Windows 10의 흥미롭고 새로운 엔터프라이즈 기능을 최대한 활용해야 합니다. 이 콘텐츠는 Configuration Manager as a Service를 채택하는 데 필요한 주요 문서의 방문 페이지로 사용됩니다. Configuration Manager as a Service는 Windows as a Service로 안내합니다.

## <a name="key-topics-about-adopting-configuration-manager-as-a-service"></a>Configuration Manager as a Service 채택에 관한 주요 항목

| 항목        | 설명          | 
| ------------- |-------------|
|[Configuration Manager as a Service 개요](/sccm/core/plan-design/changes/whats-new-incremental-versions)|Configuration Manager(현재 분기)에 대한 새로운 서비스 모델의 주요 사항을 간략하게 요약합니다.|
|[제품 지원 기간](/sccm/core/servers/manage/current-branch-versions-supported)|새로운 지원 및 서비스 모델에 대해 설명합니다.|
|[제거되는 항목과 사용되지 않는 항목](/sccm//core/plan-design/changes/deprecated/removed-and-deprecated)|Configuration Manager 사용에 영향을 줄 수 있는 향후 변경 사항에 대해 미리 알려드립니다.|
|[Configuration Manager as a Service](/sccm/core/servers/manage/updates)|Configuration Manager에 기능 업데이트를 적용하는 것을 간편한 콘솔 방식으로 설명합니다.|
|[사용 가능 업데이트 가져오기](/core/servers/manage/install-in-console-updates#get-available-updates)|새로운 Configuration Manager 기능 업데이트를 가져오는 데 사용할 수 있는 두 가지 모드에 대해 설명합니다.|
|[업데이트 검사 목록](/sccm/core/servers/manage/install-in-console-updates#bkmk_beforeinstall)|해당되는 경우 업데이트 버전별 검사 목록을 제공합니다.| 
|[새로운 Configuration Manager 기능 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates#bkmk_install)|기능 업데이트의 간단한 설치 단계에 설명합니다.|
|[Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)|Windows 10(및 ADK) 버전에 대한 지원 매트릭스를 제공합니다.|
|[Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)|ConfigMgr Technical Preview 프로그램에 대한 정보를 제공합니다.|


## <a name="key-topics-about-adopting-windows-as-a-service"></a>Windows as a Service 채택에 관한 주요 항목
| 항목        | 설명          | 
| ------------- |-------------|
|[Windows as a Service 관리](/sccm/osd/deploy-use/manage-windows-as-a-service)|서비스 계획을 사용하여 Windows 10 기능 업데이트를 배포하는 방법을 설명합니다.|
|[Windows Update for Business 통합(선택 사항)](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10)|Configuration Manager를 사용하여 WUfB(Windows Update for Business) 정책을 정의하고 배포하는 방법을 설명합니다.|
|[Microsoft Intune 및 Windows Update for Business와 공동 관리 사용(선택 사항)](/sccm/core/clients/manage/co-management-overview)|공동 관리의 개요를 제공합니다.| 


## <a name="related-articles"></a>관련 문서

- [ConfigMgr 2012에서 System Center Configuration Manager(현재 분기)로 전체 업그레이드](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
- [ConfigMgr 2007에서 System Center Configuration Manager(현재 분기)로 마이그레이션 계획](/sccm/core/migration/planning-for-migration)