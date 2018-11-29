---
title: 고급 HTTP
titleSuffix: Configuration Manager
description: 최신 인증을 사용하여 PKI 인증서가 없어도 클라이언트 통신의 보안을 유지할 수 있습니다.
ms.date: 10/29/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4deac022-e397-4f1f-bc0a-cea6c6c6368d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3a49fd8e171b053a5cc89d316fce3651e2a2f567
ms.sourcegitcommit: 8791bb9be477fe6a029e8a7a76e2ca310acd92e0
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50411568"
---
# <a name="enhanced-http"></a>고급 HTTP

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1356889,1358460-->

> [!Note]  
> 이 버전의 Configuration Manager에서 고급 HTTP는 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.  

Microsoft는 모든 Configuration Manager 통신 경로에 HTTPS 통신을 사용할 것을 권장하지만 일부 고객의 경우 PKI 인증서 관리 부담으로 인해 어려울 수 있습니다. Azure AD(Azure Active Directory) 통합이 도입되면서 인증서 요구 사항의 일부는 줄었지만 전체가 없어지지는 않았습니다. 

Configuration Manager 버전 1806에서는 클라이언트가 사이트 시스템과 통신하는 방법이 개선되었습니다. 이러한 개선에는 두 가지 기본 목표가 있습니다.  

- PKI 서버 인증 인증서가 없어도 중요한 클라이언트 통신의 보안을 유지할 수 있습니다.  

- 클라이언트는 네트워크 액세스 계정, 클라이언트 PKI 인증서 및 Windows 인증이 없어도 배포 지점에서 콘텐츠에 안전하게 액세스할 수 있습니다.  

> [!Note]  
> PKI 인증서는 다음 요구 사항을 가진 고객에게 여전히 유효한 옵션입니다.   
> - 모든 클라이언트 통신이 HTTPS를 통해 이루어집니다.  
> - 서명 인프라의 고급 제어  


## <a name="bkmk_scenario"></a> 시나리오

다음은 이러한 개선 사항을 활용하는 시나리오입니다.  


### <a name="bkmk_scenario1"></a> 시나리오 1: 관리 지점의 클라이언트
<!--1356889-->

[Azure AD 조인 장치](https://docs.microsoft.com/azure/active-directory/device-management-introduction#azure-ad-joined-devices)는 HTTP용으로 구성된 관리 지점과 통신할 수 있습니다. 사이트 서버는 관리 지점에 대한 인증서를 생성하여 보안 채널을 통해 통신할 수 있도록 허용합니다.   

> [!Note]  
> 이 동작은 Configuration Manager 현재 분기 버전 1802에서 클라우드 관리 게이트웨이를 통해 통신하는 Azure AD 조인 클라이언트에 대한 HTTPS 지원 관리 지점을 요구하는 것으로 변경됩니다. 자세한 내용은 [HTTPS에 대한 관리 지점 설정](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_mphttps)을 참조하세요.  


### <a name="bkmk_scenario2"></a> 시나리오 2: 배포 지점의 클라이언트
<!--1358228-->

작업 그룹 또는 Azure AD 조인 클라이언트는 HTTP용으로 구성된 배포 지점에서 보안 채널을 통해 콘텐츠를 인증하고 다운로드할 수 있습니다. 이러한 종류의 장치는 클라이언트에서 PKI 인증서를 요구하지 않고 HTTPS용으로 구성된 배포 지점에서 콘텐츠를 인증하고 다운로드할 수도 있습니다. 클라이언트 인증 인증서를 작업 그룹 또는 Azure AD 조인 클라이언트에 추가하는 것은 어렵습니다.

이 동작에는 부팅 미디어, PXE 또는 소프트웨어 센터에서 실행되는 작업 순서가 있는 OS 배포 시나리오가 포함됩니다. 자세한 내용은 [네트워크 액세스 계정](/sccm/core/plan-design/hierarchy/accounts#network-access-account)을 참조하세요.<!--1358278-->


### <a name="bkmk_scenario3"></a> 시나리오 3: Azure AD 장치 ID 
<!--1358460-->

Azure AD 사용자가 로그인되지 않은 Azure AD 조인 또는 [하이브리드 Azure AD 장치](https://docs.microsoft.com/azure/active-directory/device-management-introduction#hybrid-azure-ad-joined-devices)에서 할당된 사이트와 안전하게 통신할 수 있습니다. 클라우드 기반 장치 ID는 이제 장치 중심 시나리오에 대한 CMG 및 관리 지점을 인증하기에 충분합니다. (사용자 중심 시나리오에서는 여전히 사용자 토큰이 필요합니다.)  


## <a name="prerequisites"></a>필수 구성 요소  

- HTTP 클라이언트 연결용으로 구성된 관리 지점. 사이트 시스템 역할 속성의 **일반** 탭에서 이 옵션을 설정합니다.  

- HTTP 클라이언트 연결용으로 구성된 배포 지점. 사이트 시스템 역할 속성의 **일반** 탭에서 이 옵션을 설정합니다. **클라이언트의 익명 연결 허용** 옵션을 사용하도록 설정하지 마세요.  

- 클라우드 관리를 위해 Azure AD에 사이트 등록.  

    - 사이트에 대한 이 필수 요구 조건을 이미 충족한 경우 Azure AD 응용 프로그램을 업데이트해야 합니다. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장한 다음, **Azure Active Directory 테넌트**를 선택합니다. Azure AD 테넌트를 선택하고 **응용 프로그램** 창에서 웹 응용 프로그램을 선택한 다음, 리본에서 **응용 프로그램 설정 업데이트**를 선택합니다.  

- *[시나리오 3](#bkmk_scenario3)에만 해당*: Windows 10 버전 1803을 실행하고 Azure AD에 조인된 클라이언트. 



## <a name="configure-the-site"></a>사이트 구성

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 사이트를 선택하고 리본 메뉴에서 **속성**을 선택합니다.  

2. **클라이언트 컴퓨터 통신** 탭으로 전환합니다. **HTTPS 또는 HTTP**에 대한 옵션을 선택한 다음, **HTTP 사이트 시스템에 대해 Configuration Manager 생성 인증서 사용** 옵션을 사용하도록 설정합니다.  

> [!Tip]
> 관리 지점이 사이트에서 새 인증서를 받고 구성하려면 최대 30분까지 기다려야 합니다.

이러한 인증서는 Configuration Manager 콘솔에서 볼 수 있습니다. **관리** 작업 공간으로 이동하여 **보안**을 확장하고 **인증서** 노드를 선택합니다. SMS 발급 루트에서 발급한 사이트 서버 역할 인증서뿐만 아니라 **SMS 발급** 루트 인증서를 찾습니다.

클라이언트가 이 구성을 사용하여 관리 지점 및 배포 지점과 통신하는 방법에 대한 자세한 내용은 [클라이언트에서 사이트 시스템과 서비스로의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints#Planning_Client_to_Site_System)을 참조하세요.



## <a name="see-also"></a>참고 항목
- [보안 계획](/sccm/core/plan-design/security/plan-for-security)  

- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  

- [보안 구성](/sccm/core/plan-design/security/configure-security)  

- [엔드포인트 간의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints)  
