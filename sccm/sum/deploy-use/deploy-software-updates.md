---
title: "소프트웨어 업데이트 배포 | Microsoft 문서"
description: "Configuration Manager 콘솔에서 소프트웨어 업데이트를 선택하여 수동으로 배포 프로세스를 시작하거나 자동으로 업데이트를 배포합니다."
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
ms.assetid: 04536d51-3bf7-45e5-b4af-36ceed10583d
translationtype: Human Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 70a0ad1da03a7ca88df206fec683ab1df2b531e1
ms.lasthandoff: 12/16/2016

---

#  <a name="BKMK_SUMDeploy"></a> 소프트웨어 업데이트 배포  

*적용 대상: System Center Configuration Manager(현재 분기)*

소프트웨어 업데이트 배포 단계는 소프트웨어 업데이트를 배포하는 프로세스입니다. 소프트웨어 업데이트를 배포하는 방법에 관계없이 업데이트는 일반적으로 소프트웨어 업데이트 그룹에 추가되고 소프트웨어 업데이트는 배포 지점에 다운로드되며 업데이트 그룹은 클라이언트에 배포됩니다. 배포를 만들 경우, 관련된 소프트웨어 업데이트 정책이 클라이언트 컴퓨터에 전송되고 소프트웨어 업데이트 콘텐츠 파일이 배포 지점에서 클라이언트 컴퓨터의 로컬 캐시에 다운로드된 후 클라이언트에서 소프트웨어 업데이트를 설치할 수 있게 됩니다. 인터넷상의 클라이언트는 Microsoft Update에서 콘텐츠를 다운로드합니다.  

> [!NOTE]  
>  배포 지점을 사용할 수 없는 경우 인트라넷상의 클라이언트가 Microsoft 업데이트에서 소프트웨어 업데이트를 다운로드하도록 구성할 수 있습니다.  

> [!NOTE]  
>  다른 배포 유형과 달리 소프트웨어 업데이트는 클라이언트의 최대 캐시 크기 설정에 관계없이 클라이언트 캐시에 모두 다운로드됩니다. 클라이언트 캐시 설정에 대한 자세한 내용은 [Configure the Client Cache for Configuration Manager Clients](../../core/clients/manage/manage-clients.md#BKMK_ClientCache)을 참조하세요.  

필수 소프트웨어 업데이트 배포를 구성할 경우 소프트웨어 업데이트는 예약된 최종 기한에 맞춰 자동으로 설치됩니다. 또는 클라이언트 컴퓨터의 사용자는 최종 기한 전에 소프트웨어 업데이트를 설치하도록 예약하거나 설치를 시작할 수 있습니다. 설치 시도 후 클라이언트 컴퓨터는 사이트 서버에 상태 메시지를 보내 소프트웨어 업데이트 설치의 성공 여부를 보고합니다. 소프트웨어 업데이트 배포에 대한 자세한 내용은 [Software update deployment workflows](../understand/software-updates-introduction.md#BKMK_DeploymentWorkflows)를 참조하세요.  

소프트웨어 업데이트 배포에는 두 가지 기본 시나리오, 즉 수동 배포와 자동 배포가 있습니다. 일반적으로 처음에는 클라이언트 컴퓨터에 대한 기준을 만들기 위해 소프트웨어 업데이트를 수동으로 배포하고 그 후에는 자동 배포를 사용하여 클라이언트의 소프트웨어 업데이트를 관리합니다.  

## <a name="BKMK_ManualDeployment"></a> 소프트웨어 업데이트 수동 배포
Configuration Manager 콘솔에서 소프트웨어 업데이트를 선택하고 수동으로 배포 프로세스를 시작할 수 있습니다. 먼저 이 배포 방법을 사용하여 클라이언트 컴퓨터에 필수 소프트웨어 업데이트를 최신 버전으로 유지하는 것이 일반적인 방법입니다. 그 다음에 지속적인 월별 소프트웨어 업데이트 배포를 관리할 자동 배포 규칙을 만듭니다. 또한 수동 배포를 사용하면 대역 외 소프트웨어 업데이트 요구 사항을 배포할 수 있습니다. 다음 목록은 소프트웨어 업데이트의 수동 배포에 대한 일반적인 워크플로입니다.  

1. 특정 요구 사항을 사용하는 소프트웨어 업데이트를 필터링합니다. 예를 들어 51개 이상의 클라이언트 컴퓨터에 필요한 보안 또는 중요 소프트웨어 업데이트를 모두 검색하는 기준을 제시할 수 있습니다.  
2. 소프트웨어 업데이트를 포함하는 소프트웨어 업데이트 그룹을 만듭니다.  
3. 소프트웨어 업데이트 그룹 내 소프트웨어 업데이트에 대한 콘텐츠를 다운로드합니다.  
4. 소프트웨어 업데이트 그룹을 수동으로 배포합니다.

자세한 단계는 [소프트웨어 업데이트 수동 배포](manually-deploy-software-updates.md)를 참조하세요.

## <a name="automatically-deploy-software-updates"></a>소프트웨어 업데이트 자동 배포
자동 소프트웨어 업데이트 배포는 ADR(자동 배포 규칙)를 사용하여 구성합니다. 이는 월별 소프트웨어 업데이트 배포(일반적으로 "화요일 패치"라고 함)의 업데이트 관리 등에 일반적으로 사용되는 방법입니다. 규칙이 실행되면 소프트웨어 업데이트가 소프트웨어 업데이트 그룹에서 제거되고(기존 업데이트 그룹을 사용하는 경우), 지정된 조건을 충족하는 소프트웨어 업데이트(예: 지난 달에 릴리스된 모든 보안 소프트웨어 업데이트)가 소프트웨어 업데이트 그룹에 추가되고, 소프트웨어 업데이트의 콘텐츠 파일이 배포 지점에 다운로드 및 복사되고, 대상 컬렉션의 클라이언트에 소프트웨어 업데이트가 배포됩니다. 다음 목록은 소프트웨어 업데이트를 자동으로 배포하는 일반적인 워크플로입니다.  

1.  배포 설정을 지정하는 ADR을 만듭니다.
2.  소프트웨어 업데이트는 소프트웨어 업데이트 그룹에 추가됩니다.  
3.  소프트웨어 업데이트 그룹은 대상 컬렉션 내의 클라이언트 컴퓨터에 배포(지정된 경우)됩니다.  

현재 환경에서 사용할 배포 전략을 결정해야 합니다. 예를 들어 ADR를 만들고 테스트 클라이언트의 컬렉션을 대상으로 지정할 수 있습니다. 테스트 그룹에 소프트웨어 업데이트가 설치된 것을 확인한 후에는 규칙에 새 배포를 추가하거나 기존 배포의 컬렉션을 대규모 클라이언트 집합이 포함된 대상 컬렉션으로 변경할 수 있습니다. ADR에 의해 만들어진 소프트웨어 업데이트 개체는 대화형으로 작동합니다.  

-   ADR를 사용하여 배포한 소프트웨어 업데이트는 대상 컬렉션에 추가되는 새 클라이언트에 자동으로 배포됩니다.  
-   소프트웨어 업데이트 그룹에 추가되는 새 소프트웨어 업데이트는 대상 컬렉션의 클라이언트에 자동으로 배포됩니다.  
-   언제든지 ADR에 대해 배포를 사용하거나 사용하지 않도록 설정할 수 있습니다.  

ADR을 만든 후에 규칙에 배포를 더 추가할 수 있습니다. 따라서 컬렉션마다 각기 다른 업데이트를 배포해야 하는 복잡한 작업을 관리할 수 있습니다. 각각의 새 배포는 모든 기능 및 배포 모니터링 환경과 사용자가 추가하는 각 새 배포를 포함합니다.  

-   ADR을 처음 실행할 때 작성되는 것과 같은 업데이트 그룹 및 패키지를 사용  
-   다른 컬렉션 지정 가능  
-   다음을 비롯한 고유 배포 속성 지원  
   -   활성화 시간  
   -   최종 기한  
   -   최종 사용자 환경 표시/숨기기  
   -   이 배포에 대한 개별 경고  

자세한 단계는[소프트웨어 업데이트 자동 배포](automatically-deploy-software-updates.md)를 참조하세요.

<!-- ###  <a name="BKMK_ClientCache"></a> Client cache setting  
The Configuration Manager client downloads the content for required software updates to the local client cache soon after it receives the deployment. However, the client waits to download the content until after the **Software available time** setting for the deployment. The client does not download software updates in optional deployments (deployments that do not have a scheduled installation deadline) until the user manually starts the installation. When the configured deadline passes, the software updates client agent performs a scan to verify that the software update is still required, then the software updates client agent checks the local cache on the client computer to verify that the software update source file is still available, and then installs the software update. If the content was deleted from the client cache to make room for another deployment, the client downloads the software updates to the cache. Software updates are always downloaded to the client cache regardless of the configured maximum client cache size. For other deployments, such as applications or packages, the client only downloads content that is within the maximum cache size that you configure for the client. Cached content is not automatically deleted, but it remains in the cache for at least one day after the client used that content.  -->


 <!-- For more information about the deployment process, see [Software update deployment process](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).  -->

