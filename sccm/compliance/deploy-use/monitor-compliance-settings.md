---
title: 준수 설정 모니터링
titleSuffix: Configuration Manager
description: 이 항목의 절차 중 하나 이상을 사용하여 구성 기준의 준수 상태를 표시할 수 있습니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 92c1ccca-a748-44cd-a52e-e41d34bf981d
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 9920bd48ad7b953469261602c21a6664580143a2
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32335782"
---
# <a name="monitor-compliance-settings-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 준수 설정 모니터링

*적용 대상: System Center Configuration Manager(현재 분기)*

계층 구조의 장치에 System Center Configuration Manager 구성 기준을 배포한 후 이 항목의 절차 중 하나 이상을 사용하여 구성 기준의 준수 상태를 표시할 수 있습니다.

> [!NOTE]  
>  준수 설정 보고서의 유효성 검사 조건 필드(클라이언트 쪽 보고서의 **제약 조건**에 해당)는 기본 SML(Service Modeling Language)을 표시합니다. 이로 인해 Configuration Manager 콘솔의 구성 항목을 작성한 관리자가 SML에 대한 지식이 없을 경우 유효성 검사 조건을 이해하기 어려울 수 있습니다. 이 경우 Configuration Manager 콘솔의 **모니터링** 작업 영역에서 구성 항목 및 해당 유효성 검사 기준의 속성을 볼 수 있습니다.  

##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 준수 결과 보기  
 Configuration Manager 콘솔에서 배포된 구성 기준 준수에 대한 자세한 내용을 보려면 다음 절차를 따르세요.  

### <a name="view-compliance-results-in-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 준수 결과 보기  

1.  Configuration Manager 콘솔에서 **모니터링** > **배포**를 클릭합니다.  

3.  **배포** 목록에서 준수 정보를 검토할 구성 기준 배포를 선택합니다.  

4.  기본 페이지에서 구성 기준 배포 준수에 대한 요약 정보를 검토할 수 있습니다. 자세한 내용을 보려면 구성 기준 배포를 선택한 후 **홈** 탭의 **배포** 그룹에서 **상태 보기** 를 클릭하여 **배포 상태** 페이지를 엽니다.  

     **배포 상태** 페이지에는 다음 탭이 있습니다.  

    -   **규격**: 영향받는 자산 수에 따라 구성 기준 준수를 표시합니다. 규칙을 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 또는 **장치** 노드 아래에 임시 노드를 만들 수 있습니다. 그러면 이 규칙을 준수하는 모든 사용자 또는 장치가 해당 노드에 포함됩니다. **자산 정보** 창에 구성 기준을 준수하는 사용자 또는 장치가 표시됩니다. 목록에서 추가 정보를 표시할 사용자 또는 장치를 두 번 클릭합니다.  

        > [!IMPORTANT]  
        >  클라이언트 장치에서 적용할 수 없거나 검색되지 않는 경우 구성 항목 규칙이 평가되지 않지만 해당 규칙이 준수 상태로 반환됩니다.  

    -   **오류**: 영향받는 자산 수에 따라 선택한 구성 기준 배포에 대한 모든 오류 목록을 표시합니다. 규칙을 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 또는 **장치** 노드 아래에 임시 노드를 만들 수 있습니다. 그러면 이 규칙에 대해 오류를 생성한 모든 사용자 또는 장치가 해당 노드에 포함됩니다. 사용자 또는 장치를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자 또는 장치가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자 또는 장치를 두 번 클릭합니다.  

    -   **비규격**: 영향받는 자산 수에 따라 구성 기준 내에 있는 모든 비규격 규칙의 목록을 표시합니다. 규칙을 클릭하여 **자산 및 호환성** 작업 영역의 **사용자** 또는 **장치** 노드 아래에 임시 노드를 만들 수 있습니다. 그러면 이 규칙을 준수하지 않는 모든 사용자 또는 장치가 해당 노드에 포함됩니다. 사용자 또는 장치를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자 또는 장치가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자 또는 장치를 두 번 클릭합니다.  

    -   **알 수 없음**: 선택한 구성 기준 배포에 대해 준수 여부를 보고하지 않은 모든 사용자 및 장치의 목록과 장치의 현재 클라이언트 상태를 표시합니다.  

5.  **배포 상태** 페이지에서 배포된 구성 기준 준수에 대한 자세한 정보를 검토할 수 있습니다. 이 정보를 나중에 빠르게 다시 찾을 수 있도록 임시 노드가 **배포** 노드 아래에 만들어집니다.  

##  <a name="view-compliance-results-by-using-reports"></a>보고서를 사용하여 준수 결과 보기  
 Configuration Manager의 준수 설정에는 구성 항목, 구성 기준 및 배포에 대한 정보를 모니터링할 수 있는 다양한 기본 제공 보고서가 포함됩니다. 이러한 보고서에는 **호환 및 설정 관리**라는 보고서 범주가 있습니다.  

> [!IMPORTANT]  
>  준수 설정 보고서에서**%** 장치 필터 **및 사용자 필터 매개 변수를 사용할 때 와일드카드(** ) 문자를 사용해야 합니다.  

 Configuration Manager에서 보고를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../core/servers/manage/reporting.md)를 참조하세요.  

##  <a name="view-compliance-results-on-a-configuration-manager-windows-client-computer"></a>Configuration Manager Windows 클라이언트 컴퓨터에서 준수 결과 보기

> [!NOTE]  
>  도메인 게스트 계정으로 로그온하는 경우 Configuration Manager Windows 클라이언트에서 정보를 볼 수 없습니다.    

1.  클라이언트 컴퓨터의 제어판에서 **Configuration Manager** 로 이동한 다음 두 번 클릭하여 속성을 엽니다.  

2.  **구성** 탭을 클릭하여 배포된 구성 기준 목록을 봅니다.  

3.  각 구성 기준에 대한 **준수 상태** 보기:  

    > [!IMPORTANT]  
    >  평가 결과가 클라이언트에서 15분 동안 캐시됩니다. 15분이 지나기 전에 재평가를 시작하면 새 평가가 아닌 이 캐시에서 준수 결과가 반환됩니다. 따라서 클라이언트에서 수행한 변경이 준수 평가 결과에 영향을 줄 수 있으려면 15분이 지난 다음 재평가를 시작해야 합니다.  

    -   **규격**: 클라이언트 컴퓨터가 평가된 구성 기준을 준수합니다.  

    -   **비규격**: 클라이언트 컴퓨터가 평가된 구성 기준을 준수하지 않습니다.  

    -   **알 수 없음**: 클라이언트 컴퓨터가 구성 기준을 아직 평가하지 않았습니다. 준수 평가 일정 외의 평가를 시작하려면 평가할 구성 기준을 선택한 다음 **평가**를 클릭합니다.  

        > [!NOTE]  
        >  클라이언트 컴퓨터에 대한 로컬 관리자 자격 증명이 있는 경우 평가된 각 구성 기준의 세부 정보를 보고 비규격 상태를 보고하는 구성 항목을 확인할 수 있습니다. 이를 위해 구성 기준을 선택한 다음 **보고서 보기**를 클릭합니다.  

4.  **확인**을 클릭합니다.  

##  <a name="create-collections-based-on-configuration-baseline-compliance"></a>구성 기준 준수를 기반으로 하는 컬렉션 만들기  
 지정된 준수를 사용하는 장치를 기반으로 Configuration Manager 컬렉션을 만들려면 다음 절차를 따르세요. 다음 준수 상태를 기반으로 컬렉션을 만들 수 있습니다.  

-   **규격**  

-   **오류**  

-   **Non-compliant**  

-   **알 수 없음**  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **구성 기준**을 클릭합니다.  

3.  **구성 기준** 목록에서 컬렉션을 만들 구성 기준을 선택합니다.  

4.  **배포 그룹** 의 **배포**탭에서 **새 컬렉션 만들기** 를 클릭한 다음 드롭다운 목록에서 컬렉션을 만들려고 하는 준수 수준을 선택합니다.  

5.  사용자 또는 장치에 배포된 구성 항목인지 여부에 따라 **사용자 컬렉션 만들기 마법사** 또는 **장치 컬렉션 만들기 마법사** 가 열립니다. 마법사가 컬렉션을 만들기 위해 자동으로 올바른 값을 채우지만 이러한 값은 편집할 수 있습니다.  

6.  마법사를 완료한 후 컬렉션이 **자산 및 준수** 작업 영역의 **사용자 컬렉션** 또는 **장치 컬렉션** 노드에 표시됩니다.  
