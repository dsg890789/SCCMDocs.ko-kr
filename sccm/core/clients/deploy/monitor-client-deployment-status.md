---
title: 클라이언트 배포 상태 모니터링
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 클라이언트 배포 상태를 모니터링합니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 20a573b3-53cb-4ed5-bae1-7542f533ed20
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55fea1e8453837538c5e7059dc5257037dd3eb38
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56120442"
---
# <a name="how-to-monitor-client-deployment-status-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트 배포 상태를 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

사이트 전체에 클라이언트를 배포하는 작업은 시간이 걸리며 일부 설치는 처음에 성공하지 못합니다. System Center Configuration Manager 콘솔은 실시간으로 클라이언트 배포 상태를 보고하여 컬렉션 내에서 클라이언트 배포를 파악할 수 있는 방법을 제공합니다.  

> [!NOTE]  
>  클라이언트 배포를 모니터링하는 가장 신뢰할 수 있는 최상의 방법은 Configuration Manager 콘솔을 사용하는 것입니다(이 문서에 설명되어 있음). 콘솔에 있는 **모니터링** 작업 영역의 클라이언트 상태 섹션에서 **클라이언트 배포** 상태를 정확하게 그리고 실시간으로 제공합니다. Windows Server 또는 System Center Operations Manager에서 서버 관리자와 같은 다른 도구로 클라이언트 배포를 모니터링할 수 있지만 일반적인 클라이언트 설치 작업에서 경보를 표시할 수 있습니다. 클라이언트 설치 프로그램(CCMSetup.exe)이 다양한 환경에서 실행되는 방식 때문에 이와 같은 다른 도구에서 클라이언트 배포의 상태를 정확하게 반영하지 않는 거짓 경보 및 경고를 생성할 수 있습니다.  

 콘솔의 **모니터링** 작업 영역에서, 지정된 컬렉션 내에서 수행되는 클라이언트 배포에 대해 다음과 같은 상태를 모니터링할 수 있습니다.  

- 규정  

- 진행 중  

- 호환되지 않음  

- 실패  

- 알 수 없음  

  Configuration Manager에서는 프로덕션 클라이언트 또는 사전 프로덕션 클라이언트에 대한 배포를 보고합니다. 또한 Configuration Manager 콘솔에서는 지정된 기간 동안 실패한 클라이언트 배포의 차트를 제공하므로 배포 문제를 해결하기 위해 수행하는 작업이 시간이 지남에 따라 배포 성공을 개선하는지 여부를 알 수 있습니다.  

## <a name="to-monitor-client-deployments"></a>클라이언트 배포를 모니터링하려면  

- Configuration Manager 콘솔에서 **모니터링** > **클라이언트 상태**를 클릭합니다.  

- 모니터링하려는 클라이언트의 버전에 따라 **프로덕션 클라이언트 배포** 또는 **사전 프로덕션 클라이언트 배포**를 클릭합니다.  

- 클라이언트 배포 상태 및 클라이언트 배포 실패에 대한 차트를 검토합니다.  

- 보고서의 범위를 변경하려면 **찾아보기...** 를 클릭하고 다른 컬렉션을 선택합니다.  

  사전 프로덕션 클라이언트 배포에 대한 자세한 내용은 [System Center Configuration Manager의 사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](../../../core/clients/manage/upgrade/test-client-upgrades.md)을 참조하세요.

  > [!NOTE]
  > 사전 프로덕션 컬렉션의 사이트 시스템 역할을 호스팅하는 컴퓨터의 배포 상태는 클라이언트가 배포된 경우에도 **호환되지 않음**으로 보고될 수 있습니다. 클라이언트 수준을 프로덕션에 올리면 배포 상태가 올바르게 나타납니다.   

  배포된 클라이언트 상태를 모니터링하려면 [System Center Configuration Manager에서 클라이언트를 모니터링하는 방법](../../../core/clients/manage/monitor-clients.md)을 참조하세요.  

  Configuration Manager 보고서를 사용하면 사이트 내 클라이언트의 상태에 대해 더 많은 정보를 확인할 수 있습니다. 보고서 실행 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고 기능](../../../core/servers/manage/reporting.md)을 참조하세요.  
