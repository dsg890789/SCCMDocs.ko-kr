---
title: 사이트 오류 영향
titleSuffix: Configuration Manager
description: Configuration Manager 사이트에서 다양한 오류의 영향을 이해합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6f0e08f8-f2e1-4823-90f6-7b1f4341eb46
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: eebd1aaf72cbd7932a919c0a8ffdef6d6af8389f
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62217468"
---
# <a name="site-failure-impacts-in-configuration-manager"></a>Configuration Manager에서 사이트 오류 영향

*적용 대상: System Center Configuration Manager(현재 분기)*

사이트 서버 및 다른 사이트 시스템은 실패할 수 있으며 정기적으로 제공하는 서비스의 손실이 발생할 수 있습니다. 동일한 컴퓨터에서 여러 사이트 시스템을 설치하고, 해당 컴퓨터가 실패하는 경우 해당 사이트 시스템에서 정기적으로 제공하는 모든 서비스는 더 이상 사용할 수 없습니다.

프로세스 계획의 일부는 조직에 제공하는 서비스에 미치는 영향에 대한 이해를 포함해야 합니다. 사이트의 각 사이트 시스템은 다양한 기능을 제공하므로 사이트에서 오류의 영향은 실패한 사이트 시스템의 역할에 따라 다릅니다. 

[고가용성 옵션](/sccm/core/servers/deploy/configure/high-availability-options)을 사용하여 모든 단일 시스템의 오류를 완화할 수 있습니다. 또한 [백업 및 복구](/sccm/core/servers/manage/backup-and-recovery) 전략을 계획하고 연습하여 서비스를 사용할 수 없는 시간을 줄입니다.

다음 섹션에서는 지정된 사이트 시스템이 작동되지 않을 때 미치는 영향을 설명합니다.


### <a name="site-server"></a>사이트 서버

- 사이트 관리가 불가능합니다. 콘솔을 사이트에 연결할 수 없습니다.  

- 관리 지점은 클라이언트 정보를 수집하고 사이트 서버가 다시 온라인 상태가 될 때까지 캐시합니다.  

- 사용자는 기존 배포를 실행할 수 있으며, 클라이언트는 배포 지점에서 콘텐츠를 다운로드할 수 있습니다.  


### <a name="site-database"></a>사이트 데이터베이스

- 사이트 관리가 불가능합니다.  

- Configuration Manager 클라이언트에 새 정책이 있는 정책 할당이 이미 있고, 관리 지점에서 정책 본문을 캐시한 경우 클라이언트는 정책 본문을 요청하고 정책 본문 응답을 수신할 수 있습니다. 그러나 사이트는 모든 새 정책 할당 요청을 제공할 수 없습니다.  

- 클라이언트가 정책을 이미 받고, 연결된 원본 파일이 클라이언트에서 로컬로 이미 캐시된 경우에만 배포를 실행할 수 있습니다.  


### <a name="management-point"></a>관리 지점

- 새 배포를 만들 수 있지만 클라이언트는 관리 지점이 온라인 상태가 될 때까지 수신하지 않습니다.  

- 클라이언트는 여전히 인벤토리, 소프트웨어 계량 및 상태 정보를 수집합니다. 관리 지점을 사용할 수 있을 때까지 이 데이터를 로컬로 저장합니다.  

- 클라이언트가 정책을 이미 받고, 연결된 원본 파일이 클라이언트에서 로컬로 이미 캐시된 경우에만 배포를 실행할 수 있습니다.  


### <a name="distribution-point"></a>배포 지점

- Configuration Manager 클라이언트는 연결된 원본 파일이 로컬로 이미 다운로드되었거나 피어 원본에서 사용할 수 있는 경우에만 배포를 실행할 수 있습니다.

