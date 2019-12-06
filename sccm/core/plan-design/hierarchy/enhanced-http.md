---
title: 고급 HTTP
titleSuffix: Configuration Manager
description: 최신 인증을 사용하여 PKI 인증서가 없어도 클라이언트 통신의 보안을 유지할 수 있습니다.
ms.date: 05/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4deac022-e397-4f1f-bc0a-cea6c6c6368d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b5634fb611d305fff196b7d6eb0b4ed97ff13d3e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70110076"
---
# <a name="enhanced-http"></a>고급 HTTP

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1356889,1358460-->

> [!Tip]  
> 이 기능은 버전 1806에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1810 버전부터 이 기능은 더 이상 시험판 기능이 아닙니다.  

Microsoft는 모든 Configuration Manager 통신 경로에 HTTPS 통신을 사용할 것을 권장하지만 일부 고객의 경우 PKI 인증서 관리 부담으로 인해 어려울 수 있습니다.

Configuration Manager 버전 1806에서는 클라이언트가 사이트 시스템과 통신하는 방법이 개선되었습니다. 이러한 개선에는 두 가지 기본 목표가 있습니다.  

- PKI 서버 인증 인증서가 없어도 중요한 클라이언트 통신의 보안을 유지할 수 있습니다.  

- 클라이언트는 네트워크 액세스 계정, 클라이언트 PKI 인증서 및 Windows 인증이 없어도 배포 지점에서 콘텐츠에 안전하게 액세스할 수 있습니다.  

다른 모든 클라이언트 통신은 HTTP를 통해 이루어집니다. 향상된 HTTP는 클라이언트 통신 또는 사이트 시스템을 위해 HTTPS를 사용하도록 설정하는 방식과 다릅니다.<!-- SCCMDocs issue #1212 -->

> [!Note]  
> PKI 인증서는 다음 요구 사항을 가진 고객에게 여전히 유효한 옵션입니다.  
>
> - 모든 클라이언트 통신이 HTTPS를 통해 이루어집니다.  
> - 서명 인프라의 고급 제어  


## <a name="bkmk_scenario"></a> 시나리오

다음은 이러한 개선 사항을 활용하는 시나리오입니다.  

### <a name="bkmk_scenario1"></a> 시나리오 1: 관리 지점의 클라이언트

<!--1356889-->
[Azure Active Directory(Azure AD) 가입 디바이스](/azure/active-directory/devices/concept-azure-ad-join)는 HTTP용으로 구성된 관리 지점과 통신할 수 있습니다. 사이트 서버는 관리 지점에 대한 인증서를 생성하여 보안 채널을 통해 통신할 수 있도록 허용합니다.

> [!Note]  
> 이 동작은 Configuration Manager 현재 분기 버전 1802에서 클라우드 관리 게이트웨이를 통해 통신하는 Azure AD 조인 클라이언트에 대한 HTTPS 지원 관리 지점을 요구하는 것으로 변경됩니다. 자세한 내용은 [HTTPS에 대한 관리 지점 설정](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_mphttps)을 참조하세요.  

### <a name="bkmk_scenario2"></a> 시나리오 2: 배포 지점의 클라이언트

<!--1358228-->
작업 그룹 또는 Azure AD 조인 클라이언트는 HTTP용으로 구성된 배포 지점에서 보안 채널을 통해 콘텐츠를 인증하고 다운로드할 수 있습니다. 이러한 종류의 디바이스는 클라이언트에서 PKI 인증서를 요구하지 않고 HTTPS용으로 구성된 배포 지점에서 콘텐츠를 인증하고 다운로드할 수도 있습니다. 클라이언트 인증 인증서를 작업 그룹 또는 Azure AD 조인 클라이언트에 추가하는 것은 어렵습니다.

이 동작에는 부팅 미디어, PXE 또는 소프트웨어 센터에서 실행되는 작업 순서가 있는 OS 배포 시나리오가 포함됩니다. 자세한 내용은 [네트워크 액세스 계정](/sccm/core/plan-design/hierarchy/accounts#network-access-account)을 참조하세요.<!--1358278-->

### <a name="bkmk_scenario3"></a> 시나리오 3: Azure AD 디바이스 ID

<!--1358460-->
Azure AD 사용자가 로그인되지 않은 Azure AD 조인 또는 [하이브리드 Azure AD 디바이스](/azure/active-directory/devices/concept-azure-ad-join-hybrid)에서 할당된 사이트와 안전하게 통신할 수 있습니다. 클라우드 기반 디바이스 ID는 이제 디바이스 중심 시나리오에 대한 CMG 및 관리 지점을 인증하기에 충분합니다. (사용자 중심 시나리오에서는 여전히 사용자 토큰이 필요합니다.)  


## <a name="features"></a>기능

다음 Configuration Manager 기능은 향상된 HTTP를 지원하거나 요구합니다.

- [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [네트워크 액세스 계정을 사용하지 않는 OS 배포](/sccm/osd/plan-design/planning-considerations-for-automating-tasks#enhanced-http)
- [최신 인터넷 기반 Windows 10 디바이스에 대한 공동 관리 사용](/sccm/comanage/tutorial-co-manage-new-devices)
- [메일을 통해 앱 승인](/sccm/apps/deploy-use/app-approval#bkmk_email-approve)
- [관리 서비스](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_admin-service)
- [최근에 연결된 콘솔 보기](/sccm/core/servers/manage/admin-console#bkmk_viewconnected)

> [!Note]  
> 소프트웨어 업데이트 지점 및 관련된 시나리오는 항상 클라우드 관리 게이트웨이 뿐만 아니라 클라이언트와의 보안 HTTP 트래픽을 지원했습니다. 여기서는 인증서 또는 토큰 기반 인증과는 다른 관리 지점의 메커니즘을 사용합니다.<!-- SCCMDocs issue #1148 -->


## <a name="prerequisites"></a>필수 구성 요소  

- HTTP 클라이언트 연결용으로 구성된 관리 지점. 사이트 시스템 역할 속성의 **일반** 탭에서 이 옵션을 설정합니다.  

- HTTP 클라이언트 연결용으로 구성된 배포 지점. 사이트 시스템 역할 속성의 **일반** 탭에서 이 옵션을 설정합니다. **클라이언트의 익명 연결 허용** 옵션을 사용하도록 설정하지 마세요.  

- 클라우드 관리를 위해 Azure AD에 사이트 등록.  

    - 사이트에 대한 이 필수 요구 조건을 이미 충족한 경우 Azure AD 애플리케이션을 업데이트해야 합니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 다음, **Azure Active Directory 테넌트**를 선택합니다. Azure AD 테넌트를 선택하고 **애플리케이션** 창에서 웹 애플리케이션을 선택한 다음, 리본에서 **애플리케이션 설정 업데이트**를 선택합니다.  

- *[시나리오 3](#bkmk_scenario3) 전용*: Windows 10 버전 1803 이상에서 실행되고 Azure AD에 가입한 클라이언트 Azure AD 디바이스 인증을 위해 클라이언트에 이 구성이 필요합니다.<!-- SCCMDocs issue 1126 -->


## <a name="configure-the-site"></a>사이트 구성

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 사이트를 선택하고 리본 메뉴에서 **속성**을 선택합니다.  

2. **클라이언트 컴퓨터 통신** 탭으로 전환합니다.

    > [!Note]
    > 버전 1906부터 이 탭을 **통신 보안**이라고 합니다.<!-- SCCMDocs#1645 -->  

    **HTTPS 또는 HTTP**에 대한 옵션을 선택합니다. 일반 탭에서 **HTTP 사이트 시스템에 대해 Configuration Manager 생성 인증서 사용**에 대한 옵션을 선택합니다.

> [!Tip]
> 관리 지점이 사이트에서 새 인증서를 받고 구성하려면 최대 30분까지 기다려야 합니다.

<!--3798957-->
버전 1902부터 중앙 관리 사이트에 대해 고급 HTTP를 사용하도록 설정할 수도 있습니다. 이 동일한 프로세스를 사용하고 중앙 관리 사이트의 속성을 엽니다. 이 작업은 중앙 관리 사이트에서 SMS 공급자 역할에 대한 고급 HTTP만 활성화합니다. 계층 구조의 모든 사이트에 적용되는 글로벌 설정이 아닙니다.

이러한 인증서는 Configuration Manager 콘솔에서 볼 수 있습니다. **관리** 작업 공간으로 이동하여 **보안**을 확장하고 **인증서** 노드를 선택합니다. SMS 발급 루트에서 발급한 사이트 서버 역할 인증서뿐만 아니라 **SMS 발급** 루트 인증서를 찾습니다.

클라이언트가 이 구성을 사용하여 관리 지점 및 배포 지점과 통신하는 방법에 대한 자세한 내용은 [클라이언트에서 사이트 시스템과 서비스로의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints#Planning_Client_to_Site_System)을 참조하세요.


## <a name="see-also"></a>참고 항목

- [보안 계획](/sccm/core/plan-design/security/plan-for-security)  

- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  

- [보안 구성](/sccm/core/plan-design/security/configure-security)  

- [엔드포인트 간의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints)  
