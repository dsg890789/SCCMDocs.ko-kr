---
title: 하이브리드 Azure AD 설정
titleSuffix: Configuration Manager
description: 사용자 환경에는 현재 도메인에 가입 된 Windows 10 장치에, 경우 공동 관리를 활성화 하기 전에 Azure AD 하이브리드 설정
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
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755215"
---
# <a name="set-up-hybrid-azure-ad-for-co-management"></a>공동 관리를 위해 Azure AD 하이브리드 설정

Configuration Manager에서 공동 관리를 활성화 하기 전에 온-프레미스 Active directory에 가입 된 Windows 10 장치에 있는 경우 Azure Active Directory (Azure AD)를 이러한 장치 가입 합니다. 이 프로세스를 하이브리드 Azure AD 조인을 이라고 합니다. 

다음 비디오에서는 수석 프로그램 관리자 Sandeep Deo 및 제품 마케팅 관리자 Adam Harbour 설명 및 Azure AD에서 장치를 구성 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Configuring-Devices-in-Azure-Active-Directory/player]

하이브리드 Azure AD 연결 프로세스가 자동으로 레지스터를 Azure AD와 온-프레미스 도메인에 가입 된 장치입니다. 이 프로세스에 대한 자세한 내용은 다음 문서를 참조하세요.
- [Azure Active Directory의 장치 관리 소개](https://docs.microsoft.com/azure/active-directory/device-management-introduction) 
- [하이브리드 Azure AD 조인에 계획 하는 방법](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)

하이브리드 Azure AD 조인 공동 관리에 대 한 주요 토대 중 하나입니다. 이 프로세스는 예를 들어 일부 고객의 경우에 대 한 어려울 수 있습니다.
- 조직에서 사용 하는 타사 id 솔루션 
- Active Directory 페더레이션 서비스 (ADFS)을 등록을 설정 하는 복잡성

이러한 문제를 해결 하면 몇 가지 지침을 걸릴 수 있습니다. 이 문서에서는 지연이 완화 하도록 도와줍니다.


## <a name="how-to-do-it"></a>작업을 수행 하는 방법

장치를 보호 하려는 id를 만들 때 사용자와 비슷합니다. 장치의 id를 모든 위치에 언제 든 지 보호 하려면 Azure AD에 해당 장치 id를 제공 해야 합니다.

사용 하는 도메인의 유형에 따라 두 가지 기본 작업을 수행 하 합니다. 다음 도메인 유형 중 하나에 대 한 하이브리드 Azure AD 연결을 구성 합니다.  
- [페더레이션된 도메인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-federated-domains)  
- [관리 되는 도메인](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains)  

앞의 두 가지 방법을 최상의 환경을 제공 합니다. 완벽 하 게 수동 프로세스를 비롯 한 자세한 내용은 다음 문서를 참조 하세요.
- [하이브리드 Azure AD 가입 장치를 수동으로 구성](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)  
- [하이브리드 Azure AD 통과 인증 ADFS](https://docs.microsoft.com/windows-server/identity/ad-fs/ad-fs-overview), Azure AD 검색 포함  

문제 해결 지침에 대해서는 [문제 해결 가이드는 Windows 10 하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current)합니다.



## <a name="case-study"></a>사례 연구

많은 유럽 소프트웨어 회사 네트워크에 100,000 개가 넘는 사용자를 사용 하 여 하이브리드 Azure AD join을 사용 하도록 설정 하는 중심 세밀 하 고 단계적 접근 방식이 소요 되었습니다.

계획 단계에서 하이브리드 Azure AD 조인 공동 관리를 지 원하는 핵심 요소 이므로 Configuration Manager 관리자 id 팀을 사용 하 여 작동 합니다. 이 소프트웨어 회사 많은 ADFS 규칙 있어 그 중 일부 복잡 한 되었습니다. 이 문제를 해결 하기 위해 id 팀은 하이브리드 Azure AD 조인 사용 하기 전에 기존 ADFS 규칙을 검토 합니다. IT 팀은 또한 Azure AD Connect 최신 버전으로 업그레이드 하도록 선택 했습니다. Azure AD Connect는 이제 하이브리드 Azure AD join을 사용 하도록 설정 하는 것에 대 한 자동화 된 프로세스 흐름을를 제공 합니다.

성공적인 배포 및 사전 프로덕션 환경에서 테스트 후이 고객에 전체 프로덕션 자산에 대 한 하이브리드 Azure AD 조인을 사용할 수 있습니다. 1 주일 내에서 공동 관리 되는 모든 Windows 10 장치를 해야 했습니다.



## <a name="contact-fasttrack"></a>FastTrack에 문의 하세요

로 이동 하는 프로세스의 시점에서 Azure AD 지원을 설정 해야 합니다 [Microsoft FastTrack](https://Microsoft.com/FastTrack/), 로그인 및 지원을 요청 합니다. 

자세한 내용은 [FastTrack에서 도움말을 얻고](/sccm/comanage/quickstart-fasttrack)합니다. 

