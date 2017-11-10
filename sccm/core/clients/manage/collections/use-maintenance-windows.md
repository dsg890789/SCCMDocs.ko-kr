---
title: "유지 관리 기간 사용"
titleSuffix: Configuration Manager
description: "컬렉션 및 유지 관리 기간을 사용하여 System Center Configuration Manager에서 클라이언트를 효과적으로 관리할 수 있습니다."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 960955af87cdae9c43b5b520c348e32e1f48ef32
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 유지 관리 기간을 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

유지 관리 기간을 사용하면 장치 컬렉션에 대해 Configuration Manager 작업을 수행할 수 있는 시간을 정의할 수 있습니다. 유지 관리 기간을 사용하여 생산성에 영향을 미치지 않는 기간 동안 클라이언트 구성 변경이 이루어지도록 할 수 있습니다.  

 다음 작업이 유지 관리 기간을 지원합니다.  

-   소프트웨어 배포  

-   소프트웨어 업데이트 배포  

-   준수 설정 배포 및 평가  

-   운영 체제 배포  

-   작업 순서 배포  

 시작 날짜, 시작/종료 시간 및 되풀이 패턴으로 유지 관리 기간을 구성합니다. 최대 기간은 24시간 미만이어야 합니다. 기본적으로 배포로 인한 컴퓨터 다시 시작은 유지 관리 외 기간에 허용되지 않지만 기본값을 재정의할 수 있습니다. 유지 관리 기간은 배포 프로그램이 실행되는 시간에만 적용되며, 로컬로 다운로드 및 실행하도록 구성된 응용 프로그램은 해당 기간 외에도 콘텐츠를 다운로드할 수 있습니다.  

 클라이언트 컴퓨터가 유지 관리 기간이 있는 장치 컬렉션의 멤버이면 배포 프로그램은 최대 허용 실행 시간이 해당 기간으로 구성된 기간을 초과하지 않는 경우에만 실행됩니다. 프로그램이 실행되지 않으면 경고가 생성되고 예약된 다음번 유지 관리 기간 동안 사용 가능한 시간이 있는 경우 배포가 다시 실행됩니다.  

## <a name="using-multiple-maintenance-windows"></a>여러 유지 관리 기간 사용  
 클라이언트 컴퓨터가 유지 관리 기간이 있는 여러 장치 컬렉션의 멤버인 경우 다음 규칙이 적용됩니다.  

-   유지 관리 기간이 겹치지 않으면 독립된 두 유지 관리 기간으로 취급되며,  

-   유지 관리 기간이 겹치면 두 유지 관리 기간을 포괄하는 시간의 단일 유지 관리 기간으로 취급됩니다. 예를 들어 각각 한 시간인 두 기간이 30분 겹칠 경우 유효한 유지 관리 기간이 90분이 됩니다.  

 사용자가 소프트웨어 센터에서 응용 프로그램 설치를 시작할 경우 유지 관리 기간에 관계없이 응용 프로그램이 즉시 설치됩니다.  

 **필수** 가 목적인 응용 프로그램 배포가 소프트웨어 센터의 사용자가 구성한 업무 외 시간 동안 설치 최종 기한에 도달하는 경우 해당 응용 프로그램이 설치됩니다.  

### <a name="how-to-configure-maintenance-windows"></a>유지 관리 기간을 구성하는 방법  

1.  Configuration Manager 콘솔에서 **자산 및 준수**>  **장치 컬렉션**을 선택합니다.  

3.  **장치 컬렉션** 목록에서 컬렉션을 선택합니다. 유지 관리 기간은 **모든 시스템** 컬렉션에 대해 만들 수 없습니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **&lt;컬렉션 이름\> 속성** 대화 상자의 **유지 관리 기간** 탭에서 **새로 만들기** 아이콘을 선택합니다.  

6.  **&lt;새\> 일정** 대화 상자를 완료합니다.  

7.  **다음에 이 일정 적용** 드롭다운 목록에서 선택합니다.  

8.  **확인**을 선택하고 **&lt;컬렉션 이름\> 속성** 대화 상자를 닫습니다.  
