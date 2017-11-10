---
title: "응용 프로그램 배포 시뮬레이트"
titleSuffix: Configuration Manager
description: "응용 프로그램을 설치하지 않고 배포 유형에 대한 검색 방법, 요구 사항 및 종속성을 평가합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
caps.latest.revision: "6"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: ecd641a14188e0247d10e0fac613ea760abb00d1
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="simulate-application-deployments-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 응용 프로그램 배포 시뮬레이트

*적용 대상: System Center Configuration Manager(현재 분기)*

시뮬레이트된 배포를 사용하면 응용 프로그램을 설치하거나 제거하지 않고 응용 프로그램 배포를 테스트할 수 있습니다. 시뮬레이트된 배포는 배포 유형의 검색 방법, 요구 사항 및 종속성을 평가합니다. 결과는 **모니터링** 작업 영역의 **배포** 노드에 보고됩니다. System Center Configuration Manager(Configuration Manager)에서 응용 프로그램 배포를 시뮬레이트하려면 이 항목의 절차를 따르세요.  

> [!NOTE]  
> 시뮬레이트된 배포는 모바일 장치 컬렉션에 대해 사용할 수 없습니다.  
>   
> 배포 용도가 **제거** 인 응용 프로그램은 동일한 응용 프로그램의 시뮬레이트된 배포가 활성화된 경우 배포할 수 없습니다.  

## <a name="configure-a-simulated-application-deployment"></a>시뮬레이트된 응용 프로그램 배포 구성

1.  Configuration Manager 콘솔에서 다음 중 하나를 선택합니다.  
    -   사용자 컬렉션  
    -   장치 컬렉션  
    -   Configuration Manager 응용 프로그램.  

2.  **홈** 탭의 **배포** 그룹에서 **배포 시뮬레이트**를 선택합니다.  

3.  응용 프로그램 배포 시뮬레이트 마법사에서 시뮬레이트된 배포에 대한 다음 세부 정보를 설정합니다.  

    -   **응용 프로그램**. **찾아보기**를 선택한 다음 시뮬레이트된 배포를 만들려는 응용 프로그램을 선택합니다.  

    -   **컬렉션**. **찾아보기**를 선택한 다음 시뮬레이트된 배포에 사용하려는 컬렉션을 선택합니다.  

    -   **작업**. 드롭다운 목록에서, 선택한 응용 프로그램의 설치 또는 제거 중 무엇을 시뮬레이트할지 선택합니다.  

    -   **사용자 로그인 여부에 상관없이 자동으로 배포**. 이 옵션을 선택한 경우 클라이언트에서 로그인 여부에 상관없이 시뮬레이트된 배포를 평가합니다.  

4.  **다음**을 클릭하여 **요약** 페이지에서 정보를 검토한 다음 마법사를 완료하여 시뮬레이트된 응용 프로그램 배포를 만듭니다.  

5.  시뮬레이트된 응용 프로그램은 **모니터링** 작업 영역의 **배포** 노드에 **시뮬레이트** 용도로 나타납니다. 응용 프로그램 배포를 모니터링하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 콘솔에서 응용 프로그램 모니터링](../../apps/deploy-use/monitor-applications-from-the-console.md)을 참조하세요.  
