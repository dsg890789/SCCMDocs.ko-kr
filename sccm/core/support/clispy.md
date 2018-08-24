---
title: 클라이언트 감시
titleSuffix: Configuration Manager
description: 클라이언트 감시를 사용하여 Configuration Manager 클라이언트에서 소프트웨어 배포, 인벤토리 및 소프트웨어 계량 문제를 해결합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 60575413-44fe-43bb-bcfb-39ec5ed5055b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e798c11bbbd6c6d69ea8455ecb7b0252a408659d
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385934"
---
# <a name="client-spy"></a>클라이언트 감시

*적용 대상: System Center Configuration Manager(현재 분기)*

클라이언트 감시는 [Configuration Manager 도구](/sccm/core/support/tools) 중 하나입니다. Configuration Manager 클라이언트에서 소프트웨어 배포, 인벤토리 및 소프트웨어 계량 문제를 해결하기 위한 도구입니다. 

도구에서 검색된 대부분의 정보는 소프트웨어 배포와 관련됩니다.
- 모든 현재 소프트웨어 배포 
- 소프트웨어 배포 기록
- 클라이언트 캐시 구성
- 캐시된 항목
- 보류 중인 필수 배포
- 사용 가능한 배포  

다음과 같은 인벤토리 정보도 표시합니다.
- 최신 인벤토리 주기 날짜
- 마지막 보고서 날짜
- 소프트웨어 인벤토리 주 버전 및 부 버전
- 파일 컬렉션
- 하드웨어 인벤토리
- IDMIF 컬렉션
- DDR(검색 데이터 레코드) 

소프트웨어 계량 규칙도 표시됩니다. 

> [!Note]   
> 성능 향상을 위해 도구는 선택할 때 각 탭에 대한 정보만을 수집합니다. 마찬가지로 **새로 고침**을 클릭하면 현재 표시된 탭에 대한 정보만을 새로 고칩니다.



## <a name="usage"></a>용도


### <a name="tools-menu"></a>도구 메뉴

**도구** 메뉴에서는 다음 작업을 사용할 수 있습니다.  

#### <a name="connect"></a>연결
다른 컴퓨터에서 정보를 검색합니다.  

- 기본적으로 도구는 현재 컴퓨터에서 정보를 표시합니다. 

- 계정에 대한 원격 컴퓨터 이름, 사용자 이름 및 암호를 사용하여 연결합니다. 도구에서는 원격 컴퓨터의 IPC$ 공유에 연결합니다. 도구가 종료하거나 다른 컴퓨터에 연결할 때 연결을 삭제합니다.  

- 정보를 얻으려면 충분한 자격 증명이 있는 계정이 필요합니다.  

- 사용자 이름 및 암호를 지정하지 않으면 클라이언트 감시에서 현재 로그인한 사용자의 보안 컨텍스트를 사용하여 연결을 시도합니다.  

- 원격 컴퓨터에 연결할 때 표시되는 모든 탭은 원격 컴퓨터에서 정보를 표시합니다.

#### <a name="software-distribution"></a>소프트웨어 배포
[소프트웨어 배포](#software-distribution) 탭을 표시하고 다른 탭을 숨깁니다. 기본적으로 클라이언트 감시는 소프트웨어 배포 탭을 표시합니다.

#### <a name="inventory"></a>인벤토리
인벤토리 탭을 표시하고 다른 탭을 숨깁니다.

#### <a name="software-metering"></a>소프트웨어 계량
소프트웨어 계량 탭을 표시하고 다른 탭을 숨깁니다.

#### <a name="save-current-tab-to-file"></a>파일에 현재 탭 저장
현재 표시된 탭의 정보를 지정하는 텍스트 파일에 저장합니다. 

#### <a name="save-all-tabs-to-file"></a>파일에 모든 탭 저장
모든 탭의 정보를 지정하는 텍스트 파일에 저장합니다. 계정에서 확인할 수 있는 정보만을 저장합니다.



## <a name="software-distribution-tab"></a>소프트웨어 배포 탭

다음 네 개의 탭에서 설정을 구성합니다.
- [소프트웨어 배포 실행 요청](#bkmk_exec-requests)
- [소프트웨어 배포 기록](#bkmk_history)
- [소프트웨어 배포 캐시 정보](#bkmk_cache-info)
- [소프트웨어 배포 보류 중인 실행](#bkmk_pending-exec)


### <a name="bkmk_exec-requests"></a> 소프트웨어 배포 실행 요청

이 탭은 장치 및 사용자 대상 배포를 비롯한 모든 기존 배포를 표시합니다.

소프트웨어 배포 실행 요청 탭의 각 트리 항목은 다음 네 가지 특성을 포함합니다.
- 보급 알림 ID 사용 가능한 배포인 경우에 이 값은 비어 있을 수 있습니다. 
- 패키지 ID 
- 프로그램 이름 
- 사용자 대상 사용자 SID 또는 요청을 시작한 사용자의 SID일 수 있습니다. 둘 모두 시스템 요청인 경우 표시된 사용자는 시스템입니다. 

각 실행 요청의 경우 하위 트리 구조에 다음 정보도 표시합니다.
- 프로그램 이름 
- 패키지 ID 
- 패키지 이름 
- 요청 생성 시간 
- 시스템 상태 
- 상태가 실행 중인 경우 실행 중 상태 
- 실행 컨텍스트(사용자 또는 관리자) 
- 기록 상태(성공, 실패 또는 NotRun) 
- LastRunTime(프로그램이 전에 실행되지 않은 경우 Never) 
- 상태가 WaitingRetry인 경우 RetryCount 
- ContentAccess(상태가 WaitingRetry인 경우 다시 시도 횟수) 
- 상태가 WaitingRetry인 경우 FailureCode 
- 상태가 WaitingRetry인 경우 FailureReason 

요청에 콘텐츠가 필요한 경우 상태는 WaitingContent입니다. 소프트웨어 배포 캐시 정보 탭은 이 다운로드 요청에 대한 세부 정보를 표시합니다.

실행 요청이 다운로드 요청인 경우 다운로드된 바이트 수도 표시합니다.

> [!Note]   
> 실행 요청의 다양한 상태에 대해 서로 다른 아이콘을 사용합니다.


### <a name="bkmk_history"></a> 소프트웨어 배포 기록

이 탭은 이전의 모든 실행 프로그램에 대한 정보를 포함합니다. 이 정보는 레지스트리에 저장됩니다.

이 트리의 주 분기는 시스템을 비롯한 다른 사용자 기록입니다. 각 사용자에 대해 실행된 프로그램의 패키지 목록을 포함하는 하위 트리를 표시합니다. 

각 패키지 하위 트리에 대한 패키지 ID 및 패키지 이름은 실행한 프로그램 목록을 표시합니다. 각각에 대한 다음 특성을 표시합니다. 
- 프로그램 이름
- 실행 상태
- 마지막 실행 시간
- 오류 코드
- 실패 이유  

프로그램이 성공적으로 실행된 경우 오류 코드 및 실패 이유는 비어 있습니다.


### <a name="bkmk_cache-info"></a> 소프트웨어 배포 캐시 정보

#### <a name="cache-config"></a>캐시 구성
Configuration Manager 클라이언트 캐시에 대한 정보를 포함합니다. 이 정보는 캐시 위치, 캐시 크기 및 현재 사용 중인지 여부를 포함합니다. 

#### <a name="cached-items"></a>캐시된 항목
현재 캐시에 있는 모든 항목의 하위 트리를 포함합니다. 각 트리 항목은 각 항목에 대한 다음 정보를 포함합니다. 
- 캐시에서 항목의 위치(폴더)
- 현재 상태
- 패키지 ID
- 패키지 이름
- 패키지 버전
- 패키지 크기
- 현재 참조 수
- UTC(마지막으로 참조한 시간)  

#### <a name="downloading-items"></a>항목 다운로드 중
클라이언트에서 현재 다운로드 중인 항목입니다. 각각은 캐시된 항목에 의해 표시된 동일한 정보 및 다운로드한 킬로바이트의 수를 보여줍니다. 


### <a name="bkmk_pending-exec"></a> 소프트웨어 배포 보류 중인 실행

이 탭은 과거 및 미래에 필요한 배포 및 사용 가능한 배포 목록을 자세히 설명하는 정보를 포함합니다.

각 트리 분기는 시스템을 비롯한 사용 가능한 배포가 있는 각 사용자 계정에 대한 것입니다.

각 사용자의 경우 하위 트리는 다음 세 가지 항목을 포함합니다.  

#### <a name="mandatory-advertisements-with-future-executions"></a>향후 실행이 있는 필수 보급 알림
실행될 것으로 남아 있는 프로그램이 여전히 있는 필수 보급 알림입니다. 이는 되풀이, 일회성 또는 다중 일정 보급 알림일 수 있습니다. 각각은 보급 알림 ID, 다음 실행 시간 및 보급 알림에서 실행하는 일정을 표시합니다. 

#### <a name="optional-advertisements"></a>선택 사항 보급 알림
게시되는 모든 보급 알림의 목록을 표시합니다. 또한 각각에 대한 보급 알림 ID, 프로그램 이름 및 패키지 이름과 같은 세부 정보를 표시합니다. 

#### <a name="past-mandatory-advertisements-with-no-future-scheduled-executions"></a>향후 예약된 실행이 없는 지난 필수 보급 알림
실행되도록 예약된 향후 프로그램이 없는 클라이언트에 있는 보급 알림 목록입니다. 보급 알림 ID, 패키지 이름 및 프로그램 이름이 표시됩니다. 선택 사항인 모든 보급 알림에 대한 하위 트리 항목이 표시됩니다.

> [!Note]  
> 패키지 이름 정보는 표시되는 컴퓨터에서 연결된 정책을 보급한 패키지에 대해서만 제공됩니다. 연결된 사용 가능한 정책이 더 이상 없는 패키지는 "패키지 이름을 더 이상 사용할 수 없음" 메시지를 표시합니다.  



## <a name="inventory-tab"></a>인벤토리 탭

인벤토리 정보를 포함하는 하나의 탭만 있습니다. 주 트리는 다음 5개의 항목을 포함합니다.  

- **소프트웨어 인벤토리**: 마지막 주기가 시작된 날짜, 마지막 보고서의 날짜 및 마지막 보고서의 부 버전과 주 버전을 포함합니다.  

- **파일 컬렉션**: 마지막 주기가 시작된 날짜, 마지막 보고서의 날짜 및 마지막 보고서의 부 버전과 주 버전을 포함합니다.  

- **하드웨어 인벤토리**: 마지막 주기가 시작된 날짜, 마지막 보고서의 날짜 및 마지막 보고서의 부 버전과 주 버전을 포함합니다.  

- **IDMIF 컬렉션**: 마지막 주기가 시작된 날짜, 마지막 보고서의 날짜 및 마지막 보고서의 부 버전과 주 버전을 포함합니다.  

- **DDR**: 마지막 주기가 시작된 날짜, 마지막 보고서의 날짜 및 마지막 보고서의 부 버전과 주 버전을 포함합니다. DDR 정보도 또한 하위 트리에 표시됩니다.



## <a name="software-metering-tab"></a>소프트웨어 계량 탭

이 탭은 하위 트리로 정보를 표시하고, 모든 소프트웨어 계량 규칙을 포함합니다. 파일 이름 및 규칙 ID로 식별하는 노드로 각 규칙을 표시합니다. 트리에서 각 노드를 확장하고, 다음 정보를 봅니다.
- 탐색기 파일 이름 
- 원본 파일 이름
- 규칙 ID
- 파일 버전
- 언어

