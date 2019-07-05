---
title: 랩 환경에서 평가
titleSuffix: Configuration Manager
description: 조직에서 사용할 System Center Configuration Manager를 평가하는 랩 환경을 만듭니다.
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 78fdf0a07d1a299f7d10a0325b48f0c1fcfde2e3
ms.sourcegitcommit: 4981a796e7886befb7bdeeb346dba32be82aefd6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67516004"
---
# <a name="evaluate-system-center-configuration-manager-by-building-your-own-lab-environment"></a>고유한 랩 환경을 구축하여 System Center Configuration Manager 평가

*적용 대상: System Center Configuration Manager(현재 분기)*

 조직에서 사용할 System Center Configuration Manager를 평가하는 랩 환경을 만드는 방법에 알아봅니다.  

 System Center Configuration Manager는 사용자, 디바이스 및 소프트웨어를 관리하는 복잡하고 강력한 도구입니다. 개념적 이해를 바탕으로 실무 연습을 진행할 수 있도록 전체 배포 전에 System Center Configuration Manager를 철저히 평가하는 것이 좋습니다.  

 이 가이드는 주로 기업 환경에서 Configuration Manager의 사용을 평가하는 관리자를 위해 작성되었습니다.  

-   PC, 서버 및 모바일 디바이스를 완전하게 관리하기 위한 솔루션을 원하는 관리자  

-   클라우드 기반 디바이스 관리의 유연성과 더불어 온-프레미스 디바이스 관리를 위한 보안이 요구되는 높은 수준의 보안 분야에서 일하는 관리자  

-   온-프레미스 서버 아키텍처의 수직 확장을 관리하려는 관리자  

## <a name="what-this-lab-does"></a>이 랩에서 수행하는 작업  
 이 랩 환경을 만드는 기본 목표는 Configuration Manager 작업을 시작하고 Configuration Manager에 대한 이해를 높이기 위한 일반적인 지식을 제공하는 것입니다. 다음 두 서버를 사용하여 현재 Configuration Manager 버전의 긴급 어셈블리를 단계별로 살펴보겠습니다.  

-   Active Directory, 도메인 컨트롤러 및 DNS 서버를 호스트하는 서버  

-   Configuration Manager 및 관련된 모든 SQL Server 구성 요소를 호스트하는 서버  

클라이언트 컴퓨터는 Hyper-V 내에서 설치됩니다. 랩 자체를 단일 서버의 완전 가상화 시스템으로 실행할 수도 있습니다.  

## <a name="what-this-lab-does-not-do"></a>이 랩에서 수행하지 않는 작업  
 이 랩에서 모든 Configuration Manager 시나리오를 설명하지는 않으며, 활성 환경으로 즉시 마이그레이션할 수 있도록 설계되지도 않았습니다.  

 이 랩을 구축하면 작업할 수 있는 기능 환경이 구현되게 됩니다. 그러나 이 환경은 시스템 성능, 하드 디스크 공간 관리, SQL Server 스토리지 등의 요소에 대해 최적화되지 않습니다.  

##  <a name="BKMK_EvalRec"></a> 랩을 빌드하기 전의 권장 자료  
 [System Center Configuration Manager에 대한 설명서](https://docs.microsoft.com/sccm/)에서 다양한 콘텐츠를 사용할 수 있습니다. 랩 빌드를 시작하기 전에 이 라이브러리에서 다음 항목을 참조하는 것이 좋습니다.  

-   [System Center Configuration Manager 소개](../../core/understand/introduction.md)에서 Configuration Manager 콘솔, 최종 사용자 포털 및 예제 시나리오에 대한 핵심 개념을 알아봅니다.  

-   [System Center Configuration Manager의 기능 및 특성](../../core/plan-design/changes/features-and-capabilities.md)에서 Configuration Manager의 기본 관리 기능에 대해 알아봅니다.  

-   [System Center Configuration Manager의 기본 사항](../../core/understand/fundamentals.md)으로 풍부한 지식을 얻습니다.  

-   [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../core/understand/fundamentals-of-role-based-administration.md)에서 보안 역할의 중요성을 알아봅니다.  

-   콘텐츠 관리에 대한 자세한 내용은 [콘텐츠 관리 관련 개념](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)을 참조하세요.  

-   [클라이언트가 System Center Configuration Manager에 대한 사이트 리소스 및 서비스를 찾는 방법 이해](../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md)를 통해 배포 전체에서 매일 진행하는 작업을 지원하는 방법을 알아봅니다.  
