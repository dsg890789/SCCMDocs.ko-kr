---
title: 소프트웨어 업데이트에 대한 모범 사례
titleSuffix: Configuration Manager
description: Configuration Manager의 소프트웨어 업데이트에 대한 모범 사례를 사용합니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 07/30/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 6d20389a-9de2-4a64-bced-9fc4fa519174
ms.collection: M365-identity-device-management
ms.openlocfilehash: eb5471c5a993a1a2f683807a12dfc01ea00bf275
ms.sourcegitcommit: 6f4c2987debfba5d02ee67f6b461c1a988a3e201
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59802125"
---
# <a name="best-practices-for-software-updates-in-configuration-manager"></a>Configuration Manager의 소프트웨어 업데이트에 대한 모범 사례

*적용 대상: System Center Configuration Manager(현재 분기)*

이 아티클에는 Configuration Manager의 소프트웨어 업데이트에 대한 모범 사례가 포함되어 있습니다. 초기 설치와 지속적인 작업에 대한 모범 사례로 정보가 분류되어 있습니다.  



## <a name="bkmk_install"></a> 설치 모범 사례  

Configuration Manager에서 소프트웨어 업데이트를 설치할 때 따라야 하는 모범 사례는 다음과 같습니다.  


### <a name="bkmk_shared-susdb"></a> 소프트웨어 업데이트 지점에 공유 WSUS 데이터베이스 사용  

기본 사이트에서 둘 이상의 소프트웨어 업데이트 지점을 설치하는 경우 동일한 Active Directory 포리스트에 있는 각 소프트웨어 업데이트 지점에 같은 WSUS 데이터베이스를 사용합니다. 같은 데이터베이스를 공유하면 클라이언트가 새 소프트웨어 업데이트 지점으로 전환할 때 발생할 수 있는 클라이언트 및 네트워크 성능 영향이 완전히 없어지지는 않더라도 상당히 줄어듭니다. 클라이언트가 이전 소프트웨어 업데이트 지점과 같은 데이터베이스를 사용하는 새 소프트웨어 업데이트 지점으로 전환하는 경우에도 델타 검사는 이루어지지만 WSUS 서버가 자체 데이터베이스를 갖는 경우보다 검사 규모가 훨씬 작아집니다. 소프트웨어 업데이트 지점 전환에 대한 자세한 내용은 [소프트웨어 업데이트 지점 전환](/sccm/sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching)을 참조하세요.  

> [!IMPORTANT]  
>  소프트웨어 업데이트 지점에 공유 WSUS 데이터베이스를 사용하는 경우에는 로컬 WSUS 콘텐츠 폴더도 공유합니다.  

WSUS 데이터베이스 공유에 대한 자세한 내용은 다음 블로그 게시물을 참조하세요.  

- [Configuration Manager 소프트웨어 업데이트 지점에 대 한 공유 SUSDB를 구현하는 방법](https://techcommunity.microsoft.com/t5/Configuration-Manager-Archive/How-to-implement-a-shared-SUSDB-for-Configuration-Manager/ba-p/274103)  

- [System Center Configuration Manager를 사용하는 경우 콘텐츠 데이터베이스를 공유하는 여러 WSUS 인스턴스에 대한 고려 사항](https://blogs.technet.microsoft.com/wsus/2014/03/22/considerations-for-multiple-wsus-instances-sharing-a-content-database-when-using-system-center-configuration-manager-but-without-network-load-balancing-nlb/)  


### <a name="bkmk_sql-instance"></a> Configuration Manager와 WSUS가 동일한 SQL Server를 사용하는 경우 하나는 명명된 인스턴스를 사용하고 다른 하나는 SQL Server의 기본 인스턴스를 사용하도록 구성  

Configuration Manager와 WSUS 데이터베이스가 동일한 SQL Server 인스턴스를 공유하는 경우 두 애플리케이션 간의 리소스 사용을 손쉽게 파악할 수 없습니다. Configuration Manager와 WSUS에 서로 다른 SQL Server 인스턴스를 사용합니다. 이 구성으로, 각 애플리케이션에 대해 발생할 수 있는 리소스 사용 문제를 해결하고 진단하기가 더 쉽습니다.  


### <a name="bkmk_store-local"></a> "로컬로 업데이트 저장" 설정 지정  

WSUS를 설치할 때는 **업데이트를 로컬에 저장** 설정을 선택합니다. 이 설정으로 WSUS는 소프트웨어 업데이트와 연결된 사용 조건을 다운로드합니다. 동기화 프로세스 중 조건을 다운로드하고 WSUS 서버용 로컬 하드 드라이브에 저장합니다. 이 설정을 선택하지 않을 경우 클라이언트 컴퓨터가 사용 조건이 있는 소프트웨어 업데이트에 대한 규정 준수 검사에 실패할 수 있습니다. 소프트웨어 업데이트 지점의 **WSUS Synchronization Manager** 구성 요소는 이 설정이 사용되는지 60분마다(기본값) 확인합니다.  



## <a name="bkmk_operation"></a> 작업 모범 사례  

소프트웨어 업데이트를 사용할 때 따라야 하는 모범 사례는 다음과 같습니다.  


### <a name="bkmk_object-limit"></a> 소프트웨어 배포 시 1000개로 소프트웨어 업데이트 제한  

각 소프트웨어 업데이트 배포의 소프트웨어 업데이트 수를 1000개로 제한합니다. 자동 배포 규칙을 만드는 경우 소프트웨어 업데이트가 1000개를 넘지 않도록 조건을 지정해야 합니다. 소프트웨어 업데이트를 수동으로 배포할 경우 1000개 이하의 업데이트를 선택합니다.  


### <a name="bkmk_new-group"></a> "Patch Tuesday"와 일반 배포를 위한 ADR을 실행할 때마다 새 소프트웨어 업데이트 그룹 만들기  

단일 배포에 1000개의 소프트웨어 업데이트로 제한합니다. 자동 배포 규칙(ADR)을 만드는 경우 기존 업데이트 그룹을 사용할지, 규칙이 실행될 때마다 새 업데이트 그룹을 만들지 지정합니다. 여러 소프트웨어 업데이트가 이루어지는 ADR의 조건을 지정하고 해당 규칙이 되풀이 일정으로 실행되는 경우 규칙이 실행될 때마다 새 소프트웨어 업데이트 그룹을 만듭니다. 이 동작으로 각 배포 시 소프트웨어 업데이트 제한인 1000개를 넘지 않습니다.  


### <a name="bkmk_same-group"></a> Endpoint Protection 정의 업데이트에 대한 ADR에 기존 소프트웨어 업데이트 그룹 사용  

Endpoint Protection 정의 업데이트를 자주 배포하기 위한 ADR을 사용하는 경우 항상 기존 소프트웨어 업데이트 그룹을 사용합니다. 그러지 않으면 ADR은 시간이 지남에 따라 수백 개의 소프트웨어 업데이트 그룹을 만듭니다. 정의 업데이트 게시자는 일반적으로 정의 업데이트가 4개의 최신 업데이트로 대체될 때 만료되도록 설정합니다. 따라서 게시자의 경우 ADR을 통해 만들어지는 소프트웨어 업데이트 그룹에 4개 이하의 정의 업데이트(활성 1개와 교체 3개)가 포함됩니다.  



## <a name="see-also"></a>참고 항목  
 [소프트웨어 업데이트 계획](/sccm/sum/plan-design/plan-for-software-updates)
