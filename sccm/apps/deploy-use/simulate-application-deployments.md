---
title: 애플리케이션 배포 시뮬레이트
titleSuffix: Configuration Manager
description: 애플리케이션을 설치하지 않고 배포 유형에 대한 검색 방법, 요구 사항 및 종속성을 평가합니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 89283226a067ff3e0bd232c33ab1cfe5d9240fb5
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62198787"
---
# <a name="simulate-application-deployments-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 애플리케이션 배포 시뮬레이트

*적용 대상: System Center Configuration Manager(현재 분기)*

시뮬레이트된 배포를 사용하면 애플리케이션을 설치하거나 제거하지 않고 애플리케이션 배포를 테스트할 수 있습니다. 시뮬레이트된 배포는 배포 유형의 검색 방법, 요구 사항 및 종속성을 평가합니다. 결과는 **모니터링** 작업 영역의 **배포** 노드에 보고됩니다. System Center Configuration Manager(Configuration Manager)에서 애플리케이션 배포를 시뮬레이트하려면 이 항목의 절차를 따르세요.  

> [!NOTE]  
> 시뮬레이트된 배포는 모바일 디바이스 컬렉션에 대해 사용할 수 없습니다.  
>   
> 배포 용도가 **제거** 인 애플리케이션은 동일한 애플리케이션의 시뮬레이트된 배포가 활성화된 경우 배포할 수 없습니다.  

## <a name="configure-a-simulated-application-deployment"></a>시뮬레이트된 애플리케이션 배포 구성

1.  Configuration Manager 콘솔에서 다음 중 하나를 선택합니다.  
    -   사용자 컬렉션  
    -   디바이스 컬렉션  
    -   Configuration Manager 애플리케이션.  

2.  **홈** 탭의 **배포** 그룹에서 **배포 시뮬레이트**를 선택합니다.  

3.  애플리케이션 배포 시뮬레이트 마법사에서 시뮬레이트된 배포에 대한 다음 세부 정보를 설정합니다.  

    -   **애플리케이션**. **찾아보기**를 선택한 다음 시뮬레이트된 배포를 만들려는 애플리케이션을 선택합니다.  

    -   **컬렉션**. **찾아보기**를 선택한 다음 시뮬레이트된 배포에 사용하려는 컬렉션을 선택합니다.  

    -   **작업**. 드롭다운 목록에서, 선택한 애플리케이션의 설치 또는 제거 중 무엇을 시뮬레이트할지 선택합니다.  

    -   **사용자 로그인 여부에 상관없이 자동으로 배포**. 이 옵션을 선택한 경우 클라이언트에서 로그인 여부에 상관없이 시뮬레이트된 배포를 평가합니다.  

4.  **다음**을 클릭하여 **요약** 페이지에서 정보를 검토한 다음 마법사를 완료하여 시뮬레이트된 애플리케이션 배포를 만듭니다.  

5.  시뮬레이트된 애플리케이션은 **모니터링** 작업 영역의 **배포** 노드에 **시뮬레이트** 용도로 나타납니다. 애플리케이션 배포를 모니터링하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 콘솔에서 애플리케이션 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)을 참조하세요.  
