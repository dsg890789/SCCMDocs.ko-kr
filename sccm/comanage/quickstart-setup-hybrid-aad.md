---
title: 하이브리드 Azure AD 설정
titleSuffix: Configuration Manager
description: 환경에 현재 도메인에 가입된 Windows 10 디바이스가 있으면 공동 관리를 사용하도록 설정하기 전에 하이브리드 Azure AD를 설정합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 27dd26d1-e99c-4431-b2f8-60406394b6db
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec02f740485d3f8b466cde0a644aaaa8885b91f2
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62204476"
---
# <a name="set-up-hybrid-azure-ad-for-co-management"></a>공동 관리를 위해 하이브리드 Azure AD 설정

온-프레미스 Active Directory에 가입된 Windows 10 디바이스가 있는 경우에는 Configuration Manager에서 공동 관리를 사용하도록 설정하기 전에 먼저 이러한 디바이스를 Azure AD(Azure Active Directory)에연결합니다. 이 프로세스를 하이브리드 Azure AD 연결이라고 합니다. 

다음 비디오에서는 수석 프로그램 관리자 Sandeep Deo와 제품 마케팅 관리자 Adam Harbour가 Azure AD에서 디바이스 구성을 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Configuring-Devices-in-Azure-Active-Directory/player]

하이브리드 Azure AD 연결 프로세스에서는 온-프레미스 도메인 가입 디바이스를 Azure AD에 자동으로 등록합니다. 이 프로세스에 대한 자세한 내용은 다음 문서를 참조하세요.
- [Azure Active Directory의 디바이스 관리 소개](https://docs.microsoft.com/azure/active-directory/device-management-introduction) 
- [하이브리드 Azure AD 연결 계획 방법](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)

하이브리드 Azure AD 연결은 공동 관리의 주요 토대 중 하나입니다. 다음을 비롯한 일부 고객은 이 프로세스를 실행하기 어려울 수 있습니다.
- 고객 조직에서 타사 ID 솔루션을 사용하는 경우 
- ADFS(Active Directory Federation Services) 설정이 복잡한 경우

이러한 문제를 해결하려면 몇 가지 지침이 필요할 수 있습니다. 이 문서에서는 지연을 줄이도록 도와줍니다.


## <a name="how-to-do-it"></a>방법

보호할 ID를 만들 때 사용자에게 디바이스는 비슷합니다. 언제 어디서나 디바이스 ID를 보호하려면 해당 디바이스의 ID를 Azure AD로 가져와야 합니다.

사용 중인 도메인 유형에 따라 두 가지 기본 방법으로 가져올 수 있습니다. 다음 도메인 유형 중 하나에서 하이브리드 Azure AD 연결을 구성합니다.  
- [페더레이션된 도메인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-federated-domains)  
- [관리형 도메인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains)  

앞의 두 가지 방법이 최상의 환경을 제공합니다. 완전 수동 프로세스를 비롯한 자세한 내용은 다음 문서를 참조하세요.
- [Manually configure hybrid Azure AD joined devices](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)(하이브리드 Azure AD 연결 디바이스 수동 구성)  
- Azure AD 검색을 포함하는 [ADFS pass-through authentication for hybrid Azure AD](https://docs.microsoft.com/windows-server/identity/ad-fs/ad-fs-overview)(하이브리드 Azure AD에 대한 ADFS 통과 인증)  

문제 해결 지침은 [Windows 10 hybrid Azure AD join troubleshooting guide](https://docs.microsoft.com/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current)(Windows 10 하이브리드 Azure AD 연결 문제 해결 가이드)를 참조하세요.



## <a name="case-study"></a>사례 연구

네트워크의 사용자가 100,000명이 넘는 유럽의 한 대형 소프트웨어 회사가 세밀하고 단계적인 접근 방식에 따라 하이브리드 Azure AD 연결을 사용하도록 설정했습니다.

계획 단계에서는 하이브리드 Azure AD 연결이 공동 관리를 지원하는 핵심 요소이므로 Configuration Manager 관리자는 Identity 팀과 협력했습니다. 이 소프트웨어 회사에는 ADFS 규칙이 많았고 이 규칙 중 일부는 복잡했습니다. 이 문제를 해결하기 위해 Identity 팀은 하이브리드 Azure AD 연결을 사용하도록 설정하기 전에 기존 ADFS 규칙을 검토했습니다. 또한 IT 팀은 Azure AD Connect를 최신 버전으로 업그레이드하기로 했습니다. Azure AD Connect는 이제 하이브리드 Azure AD 연결을 사용하도록 설정하기 위한 자동화된 프로세스 흐름을 제공합니다.

사전 프로덕션 환경에서 성공적으로 배포 및 테스트한 후 이 고객은 전제 프로덕션 자산에서 하이브리드 Azure AD 연결을 사용하도록 설정했습니다. 1주일 이내에 이 고객은 모든 Windows 10 디바이스를 공동 관리했습니다.



## <a name="contact-fasttrack"></a>FastTrack에 문의

진행 도중 언제든 Azure AD 설정 관련 지원이 필요하면 [Microsoft FastTrack](https://Microsoft.com/FastTrack/)으로 이동하여 로그인하고 지원을 요청하세요. 

자세한 내용은 [Get help from FastTrack](/sccm/comanage/quickstart-fasttrack)(FastTrack에서 도움받기)을 참조하세요. 

