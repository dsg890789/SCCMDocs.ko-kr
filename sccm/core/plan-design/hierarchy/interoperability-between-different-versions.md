---
title: 버전 간 상호 운용성
titleSuffix: Configuration Manager
description: 동일한 네트워크에 있는 여러 Configuration Manager 계층 구조 간의 충돌을 방지하는 방법을 알아봅니다.
ms.date: 05/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9b0a7859-747f-4495-a2f4-13fd5991f897
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e9aa62d03224afe86f688d70f8b17b58bf68edff
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75800120"
---
# <a name="interoperability-between-different-versions-of-configuration-manager"></a>다른 버전의 Configuration Manager 간의 상호 운용성

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager의 여러 독립적인 계층 구조를 동일한 네트워크에 설치하고 운영할 수 있습니다. 그러나 마이그레이션 프로세스 이외에는 Configuration Manager의 각 계층 구조가 상호 운용되지 않으므로 각 계층 구조 간에 충돌을 방지하도록 구성해야 합니다. 또한 관리하는 리소스가 올바른 계층 구조의 사이트 시스템과 상호 작용하도록 특정 구성을 만들 수 있습니다.  

## <a name="BKMK_SupConfigInterop"></a> 현재 분기와 이전 버전 간의 상호 운용성  

다른 버전의 사이트가 동일한 Configuration Manager 계층 구조에 공존할 수 없습니다. 유일하게 다음 업그레이드 시나리오 프로세스가 진행되는 동안에는 이러한 사이트가 공존할 수 있습니다.

- System Center 2012 Configuration Manager에서 Configuration Manager 현재 분기로
- 콘솔 내 업데이트를 사용하여 특정 Configuration Manager 현재 분기 버전에서 최신 버전으로

기존 System Center 2012 Configuration Manager 사이트 또는 계층 구조와 Configuration Manager 현재 분기 사이트 및 계층 구조를 병렬로 배포할 수 있습니다. 각 버전의 클라이언트가 다른 버전의 사이트에 연결하지 않도록 계획합니다.

예를 들어 둘 이상의 Configuration Manager 계층 구조에 동일한 네트워크 위치를 포함하는 [겹치는 경계](/sccm/core/servers/deploy/configure/boundary-groups#overlapping-boundaries)가 있는 경우 자동 사이트 할당을 사용하지 않고 각 새 클라이언트를 특정 사이트에 할당합니다. 자세한 내용은 [사이트에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/assign-clients-to-a-site)을 참조하세요.  

또한 System Center 2012 Configuration Manager의 클라이언트를 Configuration Manager 현재 분기의 사이트 시스템 역할을 호스트하는 컴퓨터에 설치할 수 없습니다. 그뿐 아니라 System Center 2012 Configuration Manager의 사이트 시스템 역할을 호스트하는 컴퓨터에 Configuration Manager 현재 분기 클라이언트를 설치할 수 없습니다.  

다음 클라이언트와 연결은 지원되지 않습니다.  

- System Center 2012 Configuration Manager 또는 이전 버전의 컴퓨터 클라이언트  

- System Center 2012 Configuration Manager 또는 이전 버전의 디바이스 관리 클라이언트  

- Windows CE Platform Builder 디바이스 관리 클라이언트(모든 버전)  

- System Center Mobile Device Manager VPN 연결  

### <a name="BKMK_SupConfigSiteAssignment"></a> 클라이언트 사이트 할당 고려 사항  

Configuration Manager 클라이언트는 단일 기본 사이트에만 할당될 수 있습니다. 다음 조건을 모두 만족하는 경우 클라이언트의 실제 사이트 할당을 예측할 수 없습니다.

- 자동 사이트 할당을 사용하여 클라이언트 설치 동안 사이트에 클라이언트를 할당하는 경우
- 둘 이상의 경계 그룹이 동일한 경계를 포함하는 경우
- 경계 그룹에 다른 사이트가 할당된 경우

여러 Configuration Manager 사이트 및 계층 구조에서 경계가 겹치는 경우 클라이언트가 필요한 사이트에 할당되지 않거나 어떤 사이트에도 할당되지 않을 수 있습니다.  

Configuration Manager 현재 분기 클라이언트는 사이트 할당을 완료하기 전에 사이트의 버전을 확인합니다. 사이트 경계가 겹치는 경우 이전 버전이 있는 사이트에 클라이언트를 할당할 수 없습니다. 그러나 이전 System Center 2012 Configuration Manager 클라이언트가 나중 버전의 Configuration Manager 현재 분기 사이트에 잘못 할당될 수도 있습니다.  

두 계층 구조에서 경계가 겹치는 경우 클라이언트가 의도치 않게 잘못된 사이트에 할당되지 않도록 하려면 클라이언트를 특정 사이트에 할당하도록 클라이언트 설치 매개 변수를 구성합니다.  

## <a name="bkmk_mixed"></a> 혼합 버전 계층 구조의 Configuration Manager 제한 사항  

Configuration Manager 현재 분기 계층 구조를 업그레이드하는 경우 사이트마다 버전이 다른 시기가 있습니다. 예를 들어, 먼저 중앙 관리 사이트를 업그레이드합니다. 사이트 유지 관리 기간 때문에 이후 시간 및 날짜가 될 때까지 기본 사이트를 업그레이드하지 않게 됩니다.  

단일 계층 구조에 있는 여러 사이트가 서로 다른 버전을 실행하는 경우 일부 기능을 사용할 수 없습니다. 이 동작은 Configuration Manager 콘솔에서 Configuration Manager 개체를 관리하는 방법 및 클라이언트에서 사용할 수 있는 기능에 영향을 줄 수 있습니다. 일반적으로 최신 버전의 Configuration Manager는 더 낮은 서비스 팩 버전을 실행하는 사이트 또는 클라이언트에서 액세스할 수 없습니다.  

### <a name="network-access-account"></a>네트워크 액세스 계정

중앙 관리 사이트를 Configuration Manager 현재 분기로 업그레이드합니다. 이 업데이트된 사이트에 연결된 Configuration Manager 콘솔에서 네트워크 액세스 계정 정보를 확인합니다. System Center 2012 Configuration Manager를 여전히 실행하는 사이트의 경우에는 계정 세부 정보가 표시되지 않습니다.

기본 사이트를 중앙 관리 사이트와 동일한 버전으로 업그레이드하면 계정 정보가 콘솔에 표시됩니다.

Configuration Manager 버전 간에 업데이트할 경우 동일한 동작이 적용됩니다.

### <a name="boot-images-for-os-deployment"></a>OS 배포용 부팅 이미지

#### <a name="when-upgrading-from-system-center-2012-configuration-manager-to-configuration-manager-current-branch"></a>System Center 2012 Configuration Manager에서 Configuration Manager 현재 분기로 업그레이드하는 경우

계층 구조의 최상위 사이트를 Configuration Manager 현재 분기로 업그레이드하는 경우 Windows ADK(Windows Assessment and Deployment Kit) 버전 10을 사용하도록 기본 부팅 이미지가 자동으로 업데이트됩니다. 이러한 부팅 이미지는 Configuration Manager 현재 분기 사이트에 있는 클라이언트에 배포하는 경우에만 사용합니다. 자세한 내용은 [OS 배포 상호 운용성 플랜](/sccm/osd/plan-design/planning-for-operating-system-deployment-interoperability)을 참조하세요.

#### <a name="when-upgrading-between-configuration-manager-current-branch-versions"></a>Configuration Manager 현재 분기 버전 간에 업그레이드하는 경우

새 버전의 Configuration Manager가 사용 중인 Windows ADK 버전을 업데이트하지 않는 한, 부팅 이미지에는 영향을 주지 않습니다.

### <a name="new-task-sequence-steps"></a>새 작업 순서 단계

특정 버전의 Configuration Manager에 도입되고 이전 버전에서 사용할 수 없는 단계를 포함하는 작업 순서를 만드는 경우 다음과 같은 문제가 발생할 수 있습니다.

- 이전 버전의 Configuration Manager를 실행하는 사이트에서 작업 순서를 편집하려고 하면 오류가 발생합니다.

- 이전 버전의 구성 관리자 클라이언트를 실행하는 컴퓨터에서 작업 순서가 실행되지 않습니다.

### <a name="client-to-down-level-management-point-communications"></a>클라이언트에서 하위 버전 관리 지점으로의 통신

클라이언트보다 낮은 버전을 실행하는 사이트의 관리 지점과 통신하는 Configuration Manager 클라이언트는 하위 버전의 Configuration Manager가 지원하는 기능만 사용할 수 있습니다. 예를 들어 최근에 업그레이드된 Configuration Manager 현재 분기 사이트의 콘텐츠를 아직 해당 버전으로 업그레이드되지 않은 관리 지점과 통신하는 클라이언트에 배포하는 경우 해당 클라이언트에서 최신 버전의 새로운 기능을 사용할 수 없습니다.

### <a name="package-and-task-sequence-deployments-to-legacy-clients"></a>레거시 클라이언트에 패키지 및 작업 순서 배포

<!-- SCCMDocs-pr issue #3493 -->

버전 1902부터는 패키지 또는 작업 순서를 클라이언트 5.7730 이하에 배포할 수 없습니다. 이 제한을 해결하려면 클라이언트를 최신 버전으로 업그레이드합니다.


## <a name="BKMK_ConsoleInterop"></a> Configuration Manager 콘솔에 대한 상호 운용성  

이 섹션에는 여러 버전의 Configuration Manager가 설치된 환경에서의 Configuration Manager 콘솔 사용에 대한 정보가 포함되어 있습니다.  

### <a name="an-environment-with-both-system-center-2012-configuration-manager-and-configuration-manager-current-branch"></a>System Center 2012 Configuration Manager 및 Configuration Manager 현재 분기가 둘 다 포함된 환경

Configuration Manager 사이트를 관리하려면 콘솔 및 콘솔이 연결하는 사이트에서 동일한 버전의 Configuration Manager를 실행해야 합니다. 예를 들어 System Center 2012 Configuration Manager 콘솔을 사용하여 Configuration Manager 현재 분기 사이트를 관리할 수 없으며, 그 반대의 경우도 마찬가지입니다.

System Center 2012 Configuration Manager 콘솔과 Configuration Manager 현재 분기 콘솔을 동일한 컴퓨터에 설치할 수 없습니다.

### <a name="an-environment-with-multiple-versions-of-configuration-manager"></a>여러 버전의 Configuration Manager가 설치된 환경

Configuration Manager 현재 분기는 한 컴퓨터에서 하나를 초과하는 Configuration Manager 콘솔의 설치를 지원하지 않습니다. 각기 다른 버전의 Configuration Manager와 관련된 여러 콘솔을 사용하려면 각 콘솔을 별도의 컴퓨터에 설치해야 합니다.

한 계층 구조의 사이트를 새 버전으로 업데이트하는 동안 최신 버전을 실행하는 사이트에 콘솔을 연결하고 해당 계층 구조의 다른 사이트에 대한 정보를 볼 수 있습니다. 그러나이 구성은 권장되지 않습니다. 콘솔 버전과 Configuration Manager 사이트 버전 간의 차이가 데이터 문제로 나타날 수 있습니다. 최신 제품 버전에서 사용할 수 있는 몇 가지 기능을 콘솔에서 사용할 수 없습니다.

사이트 버전이 일치하지 않는 버전으로 콘솔을 사용하는 경우 사이트 관리가 지원되지 않습니다. 이렇게 하면 데이터의 손실이 발생할 수 있으며 사이트를 위험하게 할 수 있습니다. 예를 들어 1606 버전을 실행하는 사이트를 관리하는 데 1610 버전의 콘솔 사용이 지원되지 않습니다.
