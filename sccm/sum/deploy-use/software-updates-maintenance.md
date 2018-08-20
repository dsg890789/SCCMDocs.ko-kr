---
title: 소프트웨어 업데이트 유지 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 업데이트를 유지 관리하려면 WSUS 정리 태스크를 예약하거나 수동으로 실행할 수 있습니다.
author: aczechowski
ms.date: 07/30/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 3a44643870234a08169db1d55cc834e4ca5fcbb5
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385493"
---
# <a name="software-updates-maintenance"></a>소프트웨어 업데이트 유지 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 콘솔의 소프트웨어 업데이트 지점 구성 요소 속성에서 WSUS 정리 작업을 예약하고 실행할 수 있습니다. WSUS 정리 작업을 처음으로 실행하도록 선택하면 다음 소프트웨어 업데이트 동기화 후에 실행됩니다.  

## <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>WSUS 정리 작업을 예약하고 실행하려면 
다음 단계를 실행하여 WSUS 정리 작업을 예약합니다.   

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다. 
2. Configuration Manager 계층 구조의 최상위 사이트를 선택합니다. 

3.  **설정** 그룹에서 **사이트 구성 요소 구성** 을 클릭하고 **소프트웨어 업데이트 지점** 을 클릭하여 소프트웨어 업데이트 지점 구성 요소 속성을 엽니다.  

4. **대체 동작**을 검토합니다. 필요한 경우 동작을 수정합니다. 
![대체 동작 스크린샷](media/sccm-supersedence-behavior.PNG)

5.  **대체 규칙** 탭을 클릭하고, **WSUS 정리 마법사 실행**을 선택합니다. 1806 버전에서는 옵션의 이름이 **Run WSUS cleanup after synchronization**(동기화 후 WSUS 정리 실행)으로 바뀝니다. 
 
6. **확인**을 클릭합니다(1806 버전을 실행하는 경우 **닫기** 클릭).

## <a name="wsus-cleanup-behavior-in-version-1802-and-earlier"></a>1802 및 이전 버전의 WSUS 정리 동작
Configuration Manager 1806 버전 이전의 WSUS 정리 옵션에서 실행하는 항목은 다음과 같습니다. 
- 최상위 사이트의 WSUS 서버에만 있는 WSUS 정리 마법사의 **만료된 업데이트** 옵션. 
![WSUS 만료된 업데이트 정리 스크린샷](media/wsus-cleanup-expired.PNG)

-  Configuration Manager 데이터베이스의 소프트웨어 업데이트 구성 항목 정리는 7일마다 발생하고 콘솔에서 불필요한 업데이트를 제거합니다. 
   - 이 정리는 현재 배포된 Configuration Manager 콘솔에서 만료된 업데이트를 제거하지 않습니다. 

최상위 WSUS 데이터베이스와 환경의 다른 모든 WSUS 데이터베이스에는 추가 유지 관리가 여전히 필요합니다. 자세한 내용과 지침은 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://blogs.technet.microsoft.com/configurationmgr/2016/01/26/the-complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maintenance/) 블로그 게시물을 참조하세요. 


## <a name="wsus-cleanup-behavior-starting-in-version-1806"></a>1806 버전부터 시작하는 WSUS 정리 동작
1806 버전부터 WSUS 정리 옵션은 동기화를 완료할 때마다 발생하고 다음 정리 항목을 수행합니다. <!--1357898 -->
- CAS 및 기본 사이트의 WSUS 서버에 대한 **만료된 업데이트** 옵션
    - 보조 사이트의 WSUS 서버는 만료된 업데이트에 대해 WSUS 정리를 실행하지 않습니다. 
- Configuration Manager는 데이터베이스에서 대체된 업데이트 목록을 작성합니다. 목록은 소프트웨어 업데이트 지점 구성 요소 속성의 대체 동작을 기반으로 합니다. 
    - 대체 동작 조건이 충족되는 업데이트 구성 항목은 Configuration Manager 콘솔에서 만료됩니다.
    - WSUS에서 CAS 및 기본 사이트에 대한 업데이트는 거부되지만, 보조 사이트에 대한 업데이트는 거부되지 않습니다.
- Configuration Manager 데이터베이스의 소프트웨어 업데이트 구성 항목 정리는 7일마다 발생하고 콘솔에서 불필요한 업데이트를 제거합니다. 
    - 이 정리는 현재 배포된 Configuration Manager 콘솔에서 만료된 업데이트를 제거하지 않습니다. 

> [!NOTE]
> "Months to wait before a superseded update is expired"(대체된 업데이트가 만료되기 전에 대기할 월 수)는 대체하는 업데이트를 만든 날짜를 기반으로 합니다. 예를 들어 이 설정으로 2개월을 사용하면 대체된 업데이트가 WSUS에서 거부되고, 대체하는 업데이트가 2개월이면 Configuration Manager에서 만료됩니다. 

모든 WSUS 유지 관리는 보조 사이트 WSUS 데이터베이스에서 수동으로 실행해야 합니다. CAS 및 기본 사이트에서 실행되지 않는 **WSUS 서버 정리 마법사** 옵션은 다음과 같습니다.

- 사용되지 않는 업데이트 및 업데이트 수정 버전
- 서버에 연결되지 않은 컴퓨터
- 불필요한 업데이트 파일

 자세한 내용과 지침은 [Microsoft WSUS 및 Configuration Manager SUP 유지 관리에 대한 전체 가이드](https://blogs.technet.microsoft.com/configurationmgr/2016/01/26/the-complete-guide-to-microsoft-wsus-and-configuration-manager-sup-maintenance/) 블로그 게시물을 참조하세요. 

## <a name="updates-cleanup-log-entries"></a>정리 로그 항목 업데이트
 
이 정리를 확인하기 위해 wsyncmgr.log에서 검토할 수 있는 항목은 다음과 같습니다. 
  - `Cleanup processed <number> total updates and declined <number>`: 이 로그 항목이 표시되면 WSUS에서 대체된 업데이트가 거부됩니다.
  - `Calling WSUS Cleanup.`: 이 항목이 표시되면 WSUS 정리가 시작됩니다.
  - `Successfully completed WSUS Cleanup.`: 이 항목이 표시되면 만료된 업데이트에 대한 WSUS 정리가 완료됩니다.
  - `Deleting old expired updates...`: 이 항목이 표시되면 Configuration Manager 만료된 업데이트 구성 항목 정리가 시작됩니다.
  - `Deleted <number> expired updates total`: 이 항목이 표시되면 Configuration Manager 만료된 업데이트 구성 항목 정리가 완료됩니다.
