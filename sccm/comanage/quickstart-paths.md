---
title: 공동 관리 경로
titleSuffix: Configuration Manager
description: 공동 관리를 설정하는 두 가지 기본 방법의 필수 조건을 이해합니다.
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
ms.sourcegitcommit: 9aebc20b25cdef0af908918ccfd791f3264a5d94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "56755195"
---
# <a name="paths-to-co-management"></a>공동 관리 경로

공동 관리를 설정하는 두 가지 기본 방법이 있습니다. 각 경로의 필수 조건을 이해하는 것이 중요합니다. 각 경로에는 Azure AD(Azure Active Directory), Configuration Manager, Microsoft Intune 및 Windows 10의 몇 가지 조합이 필요합니다. 

1. [기존 Configuration Manager 관리 디바이스를 Intune에 자동 등록](#bkmk_path1)  
2. [최신 프로비저닝을 사용하여 Configuration Manager 클라이언트 부트스트랩](#bkmk_path2)  

![공동 관리 경로 다이어그램](media/co-management-paths.png)



## <a name="bkmk_path1"></a> 경로 1: 기존 클라이언트 자동 등록

이 경로를 따르면 기존 Configuration Manager 관리 디바이스를 Intune에 빠르게 등록할 수 있습니다. Configuration Manager에서 이러한 디바이스의 관리는 공동 관리를 사용하도록 설정하기 전과 다르지 않습니다. 이제 클라우드 기반 이점을 모두 활용할 수 있습니다. 이 경로는 사용자에게 투명합니다.

설정하려면 다음이 필요합니다.
- 하이브리드 Azure AD
    - PTA(통과 인증)를 사용하는 ADFS(Active Directory Federation Services)
    - Azure AD Connect
    - Azure AD Premium 라이선스
    - 하이브리드 Azure AD 연결 구성(한 가지 옵션 선택):
        - 관리형 도메인용
        - 페더레이션된 도메인용
- 하이브리드 Azure AD 연결을 위한 클라이언트 에이전트 설정
- Intune에 대한 디바이스 자동 등록 구성
- Intune 사용자 라이선스 할당
- Configuration Manager에서 공동 관리 사용

이 경로의 자습서는 [자습서: 기존 Configuration Manager 클라이언트에 대해 공동 관리 사용](/sccm/comanage/tutorial-co-manage-clients)을 참조하세요.



## <a name="bkmk_path2"></a> 경로 2: 최신 프로비저닝을 사용하여 부트스트랩

설정하려면 다음이 필요합니다.

1. [고급 HTTP 설정](/sccm/core/plan-design/hierarchy/enhanced-http)  
2. [Azure에서 클라우드 서비스 만들기](/sccm/core/servers/deploy/configure/azure-services-wizard)  
3. [클라우드 관리 게이트웨이를 사용할 관리 지점 및 클라이언트 구성](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)  
4. [Intune을 사용하여 Configuration Manager 클라이언트 배포](/sccm/comanage/how-to-prepare-win10)  

> [!Note]  
> 이 경로의 자습서는 곧 제공됩니다.

