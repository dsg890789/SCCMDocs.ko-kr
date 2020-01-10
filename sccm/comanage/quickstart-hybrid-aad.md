---
title: 공동 관리를 위해 Azure AD 사용
titleSuffix: Configuration Manager
description: Azure AD를 사용하면 클라우드와 온-프레미스 환경 모두에서 사용자의 생산성과 리소스의 보안을 향상할 수 있음
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2af37410-d04c-4059-801c-9edb8bf72d89
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3241204a386df3e39523b05926e5cae0c7f70d82
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75816992"
---
# <a name="use-azure-ad-for-co-management"></a>공동 관리를 위해 Azure AD 사용

클라우드에서 ID는 새로운 제어 영역입니다. Azure AD(Azure Active Directory)를 사용하면 클라우드 및 온-프레미스 환경 모두에서 사용자, 디바이스 및 애플리케이션을 연결할 수 있습니다. Azure AD에 디바이스를 등록하면 사용자의 생산성과 리소스의 보안을 향상할 수 있습니다. Azure AD에 등록한 디바이스는 공동 관리와 디바이스 기반 조건부 액세스 모두의 기반입니다. 

디바이스 기반 조건부 액세스에 대한 자세한 내용은 [How To: Require managed devices for cloud app access with conditional access](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)(방법: 조건부 액세스를 사용한 클라우드 앱 액세스를 위해 관리형 디바이스 필요)를 참조하세요.

다음 비디오에서는 수석 프로그램 관리자 Sandeep Deo와 제품 마케팅 관리자 Adam Harbour가 공동 관리를 위한 Azure AD에 관해 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Embedding-Co-management-With-Azure-Active-Directory/player]

Azure AD에서는 조직의 요구에 맞게 회사 소유 디바이스에 대한 두 가지 옵션을 제공합니다.  

- **Azure AD 연결 디바이스**: Windows 10 디바이스를 온-프레미스 Active Directory가 아닌 Azure AD에 연결  

    - Windows 10 지원

    - 온-프레미스 환경의 추가 구성 없이 설정  

    - Azure AD에서 몇 가지 설정을 사용하면 사용자가 Windows 설치 환경(OOBE)을 통해 Azure AD에 디바이스를 연결하도록 지원할 수 있음  

    - 자세한 내용은 [방법: Plan your Azure AD join implementation](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)(방법: Azure AD 연결 구현 계획)을 참조하세요.  

- **하이브리드 Azure AD 연결된 디바이스**: 기존 도메인 연결 디바이스를 Azure AD에 연결  

    - Windows 10, Windows 8.1 및 Windows 7 지원

    - AD FS 클레임 또는 Azure AD Connect를 사용하여 설정  

    - Windows 10의 경우 연결이 머신 컨텍스트에서 수행되므로 사용자가 추가 단계를 수행할 필요가 없음  

    - 자세한 내용은 [How to plan your hybrid Azure Active Directory join implementation](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)(하이브리드 Azure Active Directory 연결 구현을 계획하는 방법)을 참조하세요.  

두 옵션 모두 사용자에게 비슷한 기능을 제공합니다. 필요에 따라 하나를 유연하게 선택할 수 있습니다. 예를 들어 Azure AD 연결 머신에서 [온-프레미스 리소스에 액세스](https://docs.microsoft.com/azure/active-directory/devices/azuread-join-sso)할 수 있습니다. 이 리소스가 Active Directory에 연결되어 있는지는 상관이 없습니다. 

다양한 환경에서 디바이스를 Azure AD에 연결할 수 있습니다. [인증 방법](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)이 페더레이션 인증이든 클라우드 인증이든 관계가 없습니다. 

온-프레미스 Active Directory가 이미 있는 경우 어떤 옵션이든 간단히 설정할 수 있습니다. 



## <a name="benefits"></a>이점

Azure AD에 디바이스를 연결하면 조직에 다음과 같은 이점이 제공됩니다.

#### <a name="single-sign-on-to-cloud-resources"></a>클라우드 리소스에 Single Sign-On
Azure AD에 연결된 디바이스에서는 모든 클라우드 또는 온-프레미스 리소스에 액세스하는 통합 환경을 이용할 수 있습니다. Azure AD에 연결된 Windows 머신에 로그인하면 추가 로그인 프롬프트 없이 모든 애플리케이션에 Single Sign-On할 수 있습니다.  

#### <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello
비즈니스용 Windows Hello는 Windows 10에 강력한 암호 없는 인증을 제공합니다. 디바이스를 Azure AD에 연결하면 사용자 기반 전반에서 클라우드 및 온-프레미스 리소스 모두에 비즈니스용 Windows Hello를 사용하도록 설정할 수 있습니다. 비즈니스용 Windows Hello는 복잡한 암호를 기억하거나 암호를 실수로 노출하는 문제를 없앱니다. 따라서 로그인 프로세스가 간단하고 안전해집니다. 

자세한 내용은 [비즈니스용 Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)를 참조하세요.  

#### <a name="device-based-conditional-access"></a>디바이스 기반 조건부 액세스
디바이스 상태를 기반으로 하는 조건부 액세스를 사용하도록 설정하여 조직 데이터를 더 효과적으로 보호합니다. 디바이스 기반 조건부 액세스에는 관리형 디바이스가 필요합니다. 이 디바이스는 규격 디바이스이거나 하이브리드 Azure AD 연결 디바이스여야 합니다. Azure AD 연결 디바이스의 경우 Intune에서 디바이스를 규격으로 표시해야 합니다. 하지만 하이브리드 Azure AD 연결 디바이스의 경우 디바이스 상태 자체로 조건부 액세스를 평가합니다. 공동 관리에서는 Intune을 통해 하이브리드 Azure AD 연결 디바이스의 규정 준수 상태를 추가로 평가할 수 있습니다. 이 기능은 디바이스 구성이 그대로 유지되도록 합니다. 

디바이스 기반 조건부 액세스에 대한 자세한 내용은 [How To: Require managed devices for cloud app access with conditional access](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)(방법: 조건부 액세스를 사용한 클라우드 앱 액세스를 위해 관리형 디바이스 필요)를 참조하세요.  

#### <a name="automatic-device-licensing"></a>자동 디바이스 라이선스
Azure AD에 연결된 모든 Windows 10 디바이스에서는 라이선스 확인을 수행합니다. 이러한 확인에서는 디바이스를 Microsoft 클라우드를 통해 Pro에서 Enterprise로 자동으로 업그레이드할 수 있습니다. 사용자의 관련 구독을 제거하면 디바이스가 자동으로 라이선스를 다운그레이드합니다. 이 기능은 복잡한 프로세스나 온-프레미스 시스템 없이 Windows 라이선스를 관리하기 위한 단일 창 제어를 제공합니다.

#### <a name="self-service-functionality"></a>셀프 서비스 기능
셀프 서비스 기능에는 셀프 서비스 암호 재설정과 BitLocker 복구 키가 포함됩니다. 또한 Azure AD에서는 암호를 재설정하거나 BitLocker 복구 키에 액세스하는 직접 옵션도 제공합니다. Azure AD를 사용하면 웹 브라우저에서가 아니라 Windows 잠금 화면에서 직접 암호를 재설정할 수 있습니다. 이러한 기능을 통해 사용자의 마찰을 줄이고 조직의 기술 지원팀 비용을 절감할 수 있습니다.  

자세한 내용은 [빠른 시작: 셀프 서비스 암호 재설정](https://docs.microsoft.com/azure/active-directory/authentication/quickstart-sspr)을 참조하세요.

#### <a name="enterprise-state-roaming"></a>Enterprise State Roaming
Azure AD에 연결된 모든 디바이스는 설정을 클라우드와 동기화할 수 있습니다. 사용자가 로그인하는 모든 디바이스의 설정이 모두 동기화되므로 더 생산성 높은 환경이 제공됩니다.  



## <a name="value-proposition"></a>가치 제안

어느 방법을 통해서든 디바이스를 Azure AD에 연결하면 디지털 변환이 빨라집니다. Microsoft 365에서 제공하는 더 많은 기능을 지원합니다. 더 나은 환경을 제공하고 데이터의 보안을 강화합니다. 

Azure AD는 작업 로드를 줄이는 다음과 같은 여러 옵션을 제공합니다.

- 단일 위치에서 조직의 모든 디바이스 ID 관리  

- 셀프 서비스 암호 재설정을 사용하도록 설정하여 지원팀 비용 절감. 그러면 사용자가 언제든 디바이스의 Windows 10 잠금 화면에서 암호를 재설정할 수 있습니다.  



## <a name="configure"></a>구성

온-프레미스 Active Directory 환경이 이미 있고 도메인 연결 디바이스를 Azure AD에 연결하려는 경우 하이브리드 Azure AD 연결 디바이스를 구성합니다. 자세한 내용은 [How to plan your hybrid Azure Active Directory join implementation](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)(하이브리드 Azure Active Directory 연결 구현을 계획하는 방법)을 참조하세요. 

Configuration Manager에는 [Azure AD에 새 Windows 10 도메인 연결 디바이스를 자동으로 등록](/sccm/core/clients/deploy/about-client-settings#automatically-register-new-windows-10-domain-joined-devices-with-azure-active-directory)하는 클라이언트 설정이 있습니다. 클라이언트 설정을 구성하는 방법에 대한 자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.

디바이스를 온-프레미스 도메인에는 연결하지 않고 디바이스의 Azure AD 연결을 구성하려면 자신의 환경에서 Azure AD 연결을 위한 고려 사항을 검토합니다. Azure AD 연결을 진행하기로 했으면 조직의 요구에 맞게 배포하는 여러 옵션이 있습니다. 자세한 내용은 다음 아티클을 참조하세요.
- [방법: Plan your Azure AD join implementation](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)(방법: Azure AD 연결 구현 계획)을 참조하세요.  
- [Understand your provisioning options](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#understand-your-provisioning-options)(프로비저닝 옵션 이해)  

