---
title: 공동 관리 경로
titleSuffix: Configuration Manager
description: 공동 관리를 설정 하는 두 가지 주요 방법에 대 한 필수 구성 요소를 이해 합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 5beb5564-2fdf-4f0a-8801-d0cec8214c43
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 803f05dd14da8d280f08f2bcf3608865f384d273
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755195"
---
# <a name="paths-to-co-management"></a>공동 관리 경로

두 가지 기본 공동 관리를 설정할 수 있습니다. 각 경로 대 한 필수 구성 요소를 이해 하는 것이 반드시 합니다. 각 Azure Active Directory (Azure AD), Configuration Manager, Microsoft Intune 및 Windows 10의 몇 가지 조합이 필요합니다. 

1. [Configuration Manager에서 관리 하는 장치를 Intune에 기존 자동으로 등록](#bkmk_path1)  
2. [최신 프로 비전 사용 하 여 Configuration Manager 클라이언트를 부트스트랩 합니다.](#bkmk_path2)  

![공동 관리 경로 다이어그램](media/co-management-paths.png)



## <a name="bkmk_path1"></a> 경로 1: 기존 클라이언트를 자동으로 등록

이 경로 신속 하 게 Intune에 등록 된 기존 Configuration Manager에서 관리 하는 장치를 가져올 수 있습니다. 공동 관리를 활성화 하기 전에 이러한 장치에서 Configuration Manager의 관리는 다르지 않습니다. 이제 모든 클라우드 기반 이점을 얻을 수 있습니다. 이 경로 사용자에 게 투명 합니다.

설정 해야 다음과 같습니다.
- 하이브리드 Azure AD
    - Active Directory 페더레이션 서비스 (ADFS) 통과 인증 (PTA)를 사용 하 여
    - Azure AD Connect
    - Azure AD Premium 라이선스
    - 구성 하이브리드 Azure AD 조인 (한 가지 옵션을 선택 합니다.):
        - 관리 되는 도메인
        - 페더레이션된 도메인에 대 한
- 클라이언트 에이전트 설정을 하이브리드 Azure AD 조인
- Intune로 장치 자동 등록 구성
- Intune 사용자 라이선스 할당
- Configuration Manager에서 공동 관리를 사용 하도록 설정

이 경로에 대 한 자습서를 참조 하세요. [자습서: 기존 Configuration Manager 클라이언트에 대 한 공동 관리를 사용 하도록 설정](/sccm/comanage/tutorial-co-manage-clients)합니다.



## <a name="bkmk_path2"></a> 경로 2: 최신 프로 비전 부트스트랩

설정 해야 다음과 같습니다.

1. [향상 된 HTTP 설정](/sccm/core/plan-design/hierarchy/enhanced-http)  
2. [Azure에서 클라우드 서비스 만들기](/sccm/core/servers/deploy/configure/azure-services-wizard)  
3. [관리 지점 및 클라우드 관리 게이트웨이 사용 하는 클라이언트 구성](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)  
4. [Intune을 사용 하 여 Configuration Manager 클라이언트를 배포 하려면](/sccm/comanage/how-to-prepare-win10)  

> [!Note]  
> 이 경로 대 한 자습서는 곧 제공 됩니다.

