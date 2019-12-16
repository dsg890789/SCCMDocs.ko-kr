---
title: Configuration Manager란?
titleSuffix: Configuration Manager
description: Microsoft Endpoint Configuration Manager의 기본 사항을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3343eccf-bf09-41cd-9e68-03e893c7f904
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ee7b026662cb37ba8d0cc80062a24046a5c59342
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74661188"
---
# <a name="what-is-configuration-manager"></a>Configuration Manager란?

*적용 대상: Configuration Manager(현재 분기)*

버전 1910부터, Configuration Manager가 Microsoft Endpoint Manager의 일부가 됩니다.

![Microsoft Endpoint Configuration Manager](media/4960084-endpoint-manager-logo.png)

Microsoft Endpoint Manager는 모든 디바이스를 관리하기 위한 통합 솔루션입니다. Microsoft는 복잡한 마이그레이션 없이 간소화된 라이선싱을 통해 Configuration Manager와 Intune을 함께 제공합니다. 원하는 대로 Microsoft 클라우드의 강력한 기능을 활용하면서 기존 Configuration Manager 투자를 계속 활용하세요.

다음 Microsoft 관리 솔루션은 이제 모두 **Microsoft Endpoint Manager** 브랜드의 일부입니다.

- [Configuration Manager](https://docs.microsoft.com/configmgr)
- [Intune](https://docs.microsoft.com/intune)
- [Desktop Analytics](/configmgr/desktop-analytics/overview)
- [Autopilot](https://docs.microsoft.com/intune/enrollment/enrollment-autopilot)
- [Device Management 관리자 콘솔](https://go.microsoft.com/fwlink/?linkid=2109094)의 기타 기능

자세한 내용은 [Microsoft Endpoint Configuration Manager FAQ](/configmgr/core/understand/microsoft-endpoint-manager-faq)를 참조하세요.

## <a name="introduction"></a>소개

Configuration Manager를 사용하여 다음과 같은 시스템 관리 활동을 수행할 수 있습니다.

- 수동 작업을 줄이고 부가 가치가 높은 프로젝트에 집중하여 IT 생산성과 효율성을 개선합니다.  
- 하드웨어 및 소프트웨어 투자를 극대화합니다.  
- 적절한 시기에 올바른 소프트웨어를 제공하여 사용자 생산성을 증대합니다.  

Configuration Manager에서 다음과 같은 기능을 사용하여 보다 효율적인 IT 서비스를 제공할 수 있습니다.

- 애플리케이션, 소프트웨어 업데이트 및 운영 체제의 안전하고 확장 가능한 배포.
- 관리형 디바이스에 대해 실시간으로 조치 취하기.
- 온-프레미스 및 인터넷 기반 디바이스를 위한 클라우드 기반 분석 및 관리.
- 준수 설정 관리.  
- 서버, 데스크톱, 노트북의 종합적인 관리.

Configuration Manager는 Microsoft 기술 및 솔루션을 확장하고 함께 사용됩니다. 예를 들어 Configuration Manager는 다음 요소와 통합됩니다.  

- Microsoft Intune - 다양한 모바일 디바이스 공동 플랫폼 관리
- Microsoft Azure - 클라우드 서비스를 호스트하여 관리 서비스 확장
- WSUS(Windows Software Update Services) - 소프트웨어 업데이트 관리
- 인증서 서비스
- Exchange Server 및 Exchange Online
- 그룹 정책
- DNS
- Windows ADK(Windows 자동 배포 키트) 및 USMT(사용자 환경 마이그레이션 도구)
- WDS(Windows 배포 서비스)
- 원격 데스크톱 및 원격 지원

Configuration Manager에서는 다음 요소도 사용됩니다.  

- 보안, 서비스 위치, 구성 관련 작업을 수행하고 관리할 사용자 및 디바이스를 검색하는 Active Directory Domain Services 및 Azure Active Directory  
- 분산 변경 관리 데이터베이스로 사용되고 SQL Server Reporting Services(SSRS)와 통합되어 관리 활동을 모니터링하고 추적하는 보고서를 생성하는 Microsoft SQL Server  
- 관리 기능을 확장하고 IIS(인터넷 정보 서비스)의 웹 서비스를 사용하는 사이트 시스템 역할
- 네트워크상에서와 디바이스 간에 콘텐츠를 관리하는 데 도움이 되는 전송 최적화, Windows LEDBAT(낮은 추가 지연 백그라운드 전송), BITS(Background Intelligent Transfer Service), BranchCache 및 기타 피어 캐싱 기술

프로덕션 환경에서 Configuration Manager를 성공적으로 사용하려면 관리 기능을 철저히 계획하고 테스트해야 합니다. Configuration Manager는 조직의 모든 컴퓨터에 영향을 줄 가능성이 있는 강력한 관리 애플리케이션입니다. 신중히 계획하고 비즈니스 요구 사항을 고려하여 Configuration Manager를 배포하고 관리하면 Configuration Manager를 통해 관리 오버헤드와 총 소유 비용을 줄일 수 있습니다.  

## <a name="user-interfaces"></a>사용자 인터페이스

### <a name="BKMK_Console"></a> Configuration Manager 콘솔

Configuration Manager를 설치한 후에는 Configuration Manager 콘솔을 사용하여 사이트 및 클라이언트를 구성하고 관리 작업을 실행하고 모니터링합니다. 이 콘솔은 기본 관리 지점으로, 여러 사이트를 관리할 수 있습니다.  

추가 컴퓨터에 Configuration Manager 콘솔을 설치하고 Configuration Manager 역할 기반 관리를 사용하여 액세스 및 관리자가 콘솔에서 볼 수 있는 내용을 제한할 수 있습니다.  

자세한 내용은 [Configuration Manager 콘솔 사용](/configmgr/core/servers/manage/admin-console)을 참조하세요.

### <a name="BKMK_ApplicationCatalog"></a> 소프트웨어 센터

**소프트웨어 센터**는 Windows 디바이스에 구성 관리자 클라이언트를 설치하면 설치되는 애플리케이션입니다. 사용자는 소프트웨어 센터를 사용하여 관리자가 배포하는 소프트웨어를 요청하고 설치합니다. 사용자가 소프트웨어 센터에서 수행할 수 있는 작업은 다음과 같습니다.  

- 애플리케이션, 소프트웨어 업데이트 및 새 OS 버전 찾아보기 및 설치
- 소프트웨어 요청 기록 보기
- 조직의 정책을 기준으로 디바이스 규정 준수 확인

추가적인 비즈니스 요구 사항을 충족하기 위해 소프트웨어 센터에서 사용자 지정 탭을 표시할 수도 있습니다.

자세한 내용은 [소프트웨어 센터 사용자 가이드](/configmgr/core/understand/software-center)를 참조하세요.

## <a name="next-steps"></a>다음 단계

Configuration Manager를 설치하기 전에 먼저 기본 개념과 용어를 숙지하세요.

- System Center 2012 Configuration Manager에 대해 잘 알고 있다면 [System Center 2012 Configuration Manager에서 변경된 System Center Configuration Manager의 기능](/configmgr/core/plan-design/changes/what-has-changed-from-configuration-manager-2012)을 참조하세요.

- Configuration Manager의 개략적인 기술 개요는 [Configuration Manager의 기본 사항](/configmgr/core/understand/fundamentals)을 참조하세요.

기본 개념을 숙지한 후에는 문서 라이브러리를 참고하여 Configuration Manager를 성공적으로 배포하고 사용하시기 바랍니다. 다음 문서로 시작하세요.

- [Configuration Manager의 기능 및 특성](/configmgr/core/plan-design/changes/features-and-capabilities)  
- [디바이스 관리 솔루션 선택](/configmgr/core/plan-design/choose-a-device-management-solution)  
- [고유한 랩 환경을 구축하여 Configuration Manager 평가](/configmgr/core/get-started/set-up-your-lab)
- [Configuration Manager 사용 도움말 찾기](/configmgr/core/understand/find-help)  
