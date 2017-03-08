---

title: "소프트웨어 업데이트에 대한 모범 사례 | Microsoft 문서"
description: "System Center Configuration Manager의 소프트웨어 업데이트에 대한 다음 모범 사례를 따르세요."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 6d20389a-9de2-4a64-bced-9fc4fa519174
translationtype: Human Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: ea365491dd334980693375fbb7730653af9cd8e4
ms.lasthandoff: 12/16/2016



---
# <a name="best-practices-for-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager의 소프트웨어 업데이트에 대한 모범 사례

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에는 System Center Configuration Manager의 소프트웨어 업데이트에 대한 모범 사례가 포함되어 있습니다. 초기 설치에 대한 모범 사례와 지속적인 작업에 대한 모범 사례로 정보가 분류되어 있습니다.  

## <a name="installation-best-practices"></a>설치 모범 사례  
 Configuration Manager에서 소프트웨어 업데이트를 설치할 때 따라야 하는 모범 사례는 다음과 같습니다.  

### <a name="use-a-shared-wsus-database-for-software-update-points"></a>소프트웨어 업데이트 지점에 공유 WSUS 데이터베이스 사용  
 기본 사이트에서 둘 이상의 소프트웨어 업데이트 지점을 설치하는 경우 동일한 Active Directory 포리스트에 있는 각 소프트웨어 업데이트 지점에 같은 WSUS 데이터베이스를 사용합니다. 동일한 데이터베이스를 공유하면 클라이언트가 새 소프트웨어 업데이트 지점으로 전환될 때 발생할 수 있는 클라이언트 및 네트워크 성능 영향이 대폭 줄어들 수 있습니다. 클라이언트가 이전 소프트웨어 업데이트 지점과 같은 데이터베이스를 사용하는 새 소프트웨어 업데이트 지점으로 전환하는 경우에도 델타 검사는 이루어지지만 WSUS 서버가 자체 데이터베이스를 갖는 경우보다 검사 규모가 훨씬 작아집니다.  

> [!IMPORTANT]  
>  소프트웨어 업데이트 지점에 공유 WSUS 데이터베이스를 사용하는 경우 로컬 WSUS 콘텐츠 폴더를 공유해야 합니다.  

 소프트웨어 업데이트 지점 전환에 대한 자세한 내용은 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](../../sum/plan-design/plan-for-software-updates.md) 항목에서 [소프트웨어 업데이트 지점 전환](../../sum/plan-design/plan-for-software-updates.md#BKMK_SUPSwitching) 섹션을 참조하세요.  

### <a name="when-configuration-manager-and-wsus-use-the-same-sql-server-configure-one-of-these-to-use-a-named-instance-and-the-other-to-use-the-default-instance-of-sql-server"></a>Configuration Manager와 WSUS가 동일한 SQL Server를 사용하는 경우 하나는 명명된 인스턴스를 사용하고 다른 하나는 SQL Server의 기본 인스턴스를 사용하도록 구성  
 Configuration Manager와 WSUS 데이터베이스가 동일한 SQL Server를 사용하고 동일한 SQL Server 인스턴스를 공유하는 경우 두 응용 프로그램 간의 리소스 사용을 손쉽게 파악할 수 없습니다. Configuration Manager와 WSUS에 서로 다른 SQL Server 인스턴스를 사용하는 경우 각 응용 프로그램에 대해 발생할 수 있는 리소스 사용 문제를 해결하고 진단하기가 더 쉽습니다.  

### <a name="specify-the-store-updates-locally-setting-for-the-wsus-installation"></a>WSUS 설치에 "로컬로 업데이트 저장" 설정 지정  
 WSUS 3.0을 설치하는 경우 **로컬로 업데이트 저장** 설정을 선택합니다. 이 설정을 선택하면 동기화 중에 소프트웨어 업데이트에 대한 사용 조건이 다운로드되어 WSUS 서버용 로컬 하드 드라이브에 저장됩니다. 이 설정을 선택하지 않으면 클라이언트 컴퓨터가 사용 조건이 있는 소프트웨어 업데이트에 대한 소프트웨어 업데이트 호환성을 검사하지 못할 수 있습니다. 소프트웨어 업데이트 지점을 설치하면 기본적으로 WSUS Synchronization Manager에서 이 설정이 사용되는지 60분마다 확인합니다.  

## <a name="operational-best-practices"></a>작업 모범 사례  
 소프트웨어 업데이트를 사용할 때 따라야 하는 모범 사례는 다음과 같습니다.  

### <a name="limit-software-updates-to-1000-in-a-single-software-update-deployment"></a>소프트웨어 배포 시 1000개로 소프트웨어 업데이트 제한  
 각 소프트웨어 업데이트 배포의 소프트웨어 업데이트 수를 1000개로 제한해야 합니다. 자동 배포 규칙을 만드는 경우 소프트웨어 업데이트가 1000개가 넘지 않도록 조건을 지정해야 합니다. 소프트웨어 업데이트를 수동으로 배포할 경우 배포할 업데이트는 1000개 이하로 선택합니다.  

### <a name="create-a-new-software-update-group-each-time-an-automatic-deployment-rule-runs-for-patch-tuesday-and-for-general-deployment"></a>"Patch Tuesday"와 일반 배포를 위한 자동 배포 규칙을 실행할 때마다 새 소프트웨어 업데이트 그룹을 만듭니다.  
 각 소프트웨어 업데이트 배포 시 소프트웨어 업데이트 수가 1000개로 제한되어 있습니다. 자동 배포 규칙을 만드는 경우 기존 업데이트 그룹을 사용할지, 규칙이 실행될 때마다 새 업데이트 그룹을 만들지 지정합니다. 여러 소프트웨어 업데이트가 이루어지는 자동 배포 규칙의 조건을 지정하고 해당 규칙이 되풀이 일정으로 실행되는 경우 규칙이 실행될 때마다 새 소프트웨어 업데이트 그룹을 만들도록 지정합니다. 이렇게 하면 각 배포 시 소프트웨어 업데이트 제한인 1000개가 넘지 않도록 방지됩니다.  

### <a name="use-an-existing-software-update-group-for-automatic-deployment-rules-for-endpoint-protection-definition-updates"></a>Endpoint Protection 정의 업데이트에 대한 자동 배포 규칙에 기존 소프트웨어 업데이트 그룹 사용  
 Endpoint Protection 정의 업데이트를 자주 배포하기 위한 자동 배포 규칙을 사용하는 경우 항상 기존 소프트웨어 업데이트 그룹을 사용합니다. 그러지 않으면 시간이 지남에 따라 수백 개의 소프트웨어 업데이트 그룹이 만들어질 수 있습니다. 일반적으로 정의 업데이트 게시자는 정의 업데이트가 4개의 최신 업데이트로 대체될 때 만료되도록 설정합니다. 따라서 게시자의 경우 자동 배포 규칙을 통해 만들어지는 소프트웨어 업데이트 그룹에 4개 이하의 정의 업데이트(활성 1개와 교체 3개)가 포함됩니다.  

## <a name="see-also"></a>참고 항목  
 [System Center Configuration Manager에서 소프트웨어 업데이트 계획](../../sum/plan-design/plan-for-software-updates.md)

