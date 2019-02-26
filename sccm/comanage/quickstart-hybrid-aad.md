---
title: 공동 관리를 위해 Azure AD를 사용 합니다.
titleSuffix: Configuration Manager
description: Azure AD를 사용 하 여 있습니다 활용 향상 된 생산성의 사용자 및 보안에 대 한 리소스에 대 한 클라우드 및 온-프레미스 환경에서
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 2af37410-d04c-4059-801c-9edb8bf72d89
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3b773c0bfe8cd0f8253a67ac96f5a0113b7206c0
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755413"
---
# <a name="use-azure-ad-for-co-management"></a>공동 관리를 위해 Azure AD를 사용 합니다.

클라우드에서 id는 새 제어 평면입니다. Azure Active Directory (Azure AD)를 사용 하면 클라우드 및 온-프레미스 환경에서 사용자, 장치 및 응용 프로그램을 링크할 수 있습니다. Azure AD에 장치를 등록 합니다. 사용자에 대 한 생산성 및 리소스에 대 한 보안을 향상 시킬 수 있습니다. Azure AD에 장치를 포함 하는 것은 공동 관리 및 장치 기반 조건부 액세스에 대 한 기초입니다. 

장치 기반 조건부 액세스에 대 한 자세한 내용은 참조 하세요. [방법: 조건부 액세스를 사용 하 여 클라우드 앱 액세스를 위해 관리 되는 장치 필요](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)

다음 비디오, Sandeep Deo 선임 프로그램 관리자 및 제품 마케팅 관리자 Adam Harbour 설명 및 데모 공동 관리를 위해 Azure AD:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Embedding-Co-management-With-Azure-Active-Directory/player]

Azure AD는 조직의 요구에 맞게 회사 소유 장치에 대 한 두 가지 옵션을 제공 합니다.  

- **Azure AD 가입 장치**: 온-프레미스 Active Directory에 연결할 필요 없이 Windows 10 장치가 Azure AD에 연결  

    - Windows 10 지원

    - 온-프레미스 환경에 추가 구성 없이 설정  

    - 몇 가지 설정에서 Azure AD를 사용 하 여 Windows 설치 환경 (OOBE)을 통해 Azure AD에 장치를 조인할 사용자 수 있습니다.  

    - 자세한 내용은 [방법: Azure AD 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)  

- **하이브리드 Azure AD 가입 장치**: 기존 도메인에 가입 된 장치를 Azure AD에 조인  

    - Windows 10, Windows 8.1 및 Windows 7 지원

    - AD FS 클레임 또는 Azure AD Connect를 사용 하 여 설정 합니다.  

    - Windows 10에 대 한 조인 컨텍스트에서 발생 컴퓨터, 사용자가 추가 단계를 수행 필요가  

    - 자세한 내용은 참조 하세요. [하이브리드 Azure Active Directory 조인 구현을 계획 하는 방법](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)  

두 옵션 모두 사용자에 대 한 유사한 기능을 제공 합니다. 이 필요에 따라 하나를 선택 하기 위한 유연 합니다. 예를 들어 있습니다 [온-프레미스 리소스에 액세스할](https://docs.microsoft.com/azure/active-directory/devices/azuread-join-sso) Azure AD에 가입 된 컴퓨터에서도 해당 되지 Active Directory에 조인 합니다. 

든 관계 없이 다양 한 환경에서 Azure AD에 장치를 조인할 수 있습니다 하 [인증 방법을](https://docs.microsoft.com/azure/security/azure-ad-choose-authn)합니다. 예를 들어, 페더레이션된 인증 또는 클라우드 인증 합니다. 

온-프레미스 Active Directory에 이미 있는 경우 간단 옵션 중 하나를 설정 합니다. 



## <a name="benefits"></a>이점

Azure AD에 장치를 조인할 조직에 다음과 같은 이점이 있습니다.

#### <a name="single-sign-on-to-cloud-resources"></a>클라우드 리소스에서 single sign-on
Azure AD에 가입 된 장치에서 모든 클라우드 또는 온-프레미스 리소스에 액세스 하는 통합된 된 환경을 가져올 수 있습니다. Azure AD에 가입 된 Windows 컴퓨터에 로그인 한 후 추가 로그인 프롬프트 없이 모든 응용 프로그램에서 single sign-on 얻게 됩니다.  

#### <a name="windows-hello-for-business"></a>비즈니스용 Windows Hello
Windows Hello 비즈니스에 대 한 강력한 암호 없는 인증을 제공 Windows 10 합니다. 장치를 Azure AD에 가입 하면 사용할 수 있습니다 Windows Hello 비즈니스에 대 한 클라우드 및 온-프레미스 리소스에 대 한 기본 사용자에서. Windows Hello 비즈니스에 대 한 제거 복잡 한 암호를 기억 하거나 실수로 노출 하는 문제입니다. 해당 로그인 과정이 단순 하며 안전 합니다. 

자세한 내용은 [비즈니스용 Windows Hello](https://docs.microsoft.com/windows/security/identity-protection/hello-for-business/hello-identity-verification)를 참조하세요.  

#### <a name="device-based-conditional-access"></a>장치 기반 조건부 액세스
조직의 데이터를 더욱 효과적으로 보호할 장치 상태에 따라 조건부 액세스를 사용 하도록 설정 합니다. 장치 기반 조건부 액세스를 관리 되는 장치에 필요합니다. 이 장치는 규격 장치 또는 하이브리드 Azure AD에 가입 된 장치 여야 합니다. Azure AD 가입 장치에 대 한 Intune 장치 규정 준수로 표시 해야 합니다. 하지만 조건부 액세스를 평가 하는 데 하이브리드 Azure AD 가입 장치를 자체 장치 상태를 사용 합니다. 공동 관리는 Intune 통해 Azure 하이브리드에 대 한 준수 평가의 추가적인 이점도 제공 AD에 가입 된 장치입니다. 이 기능을 통해 장치 구성을 그대로 유지 됩니다. 

장치 기반 조건부 액세스에 대 한 자세한 내용은 참조 하세요. [방법: 조건부 액세스를 사용 하 여 클라우드 앱 액세스를 위해 관리 되는 장치가](https://docs.microsoft.com/azure/active-directory/conditional-access/require-managed-devices)합니다.  

#### <a name="automatic-device-licensing"></a>자동 장치 라이선스
Azure AD에 가입 된 모든 Windows 10 장치 라이선스 검사를 통과 합니다. 이러한 검사를 사용 하도록 자동으로 업그레이드 하 고 Pro에서 Enterprise Microsoft 클라우드를 통해 설정 합니다. 사용자에서 관련 구독을 제거 하면 장치에 자동으로 해당 라이선스 다운 그레이드 합니다. 이 기능은 모든 복잡 한 프로세스가 없는 Windows 라이선스 관리에 대 한 컨트롤의 단일 창이 제공 또는 온-프레미스 시스템입니다.

#### <a name="self-service-functionality"></a>셀프 서비스 기능
셀프 서비스 기능이 셀프 서비스 암호 재설정 및 BitLocker 복구 키를 포함합니다. 또한 azure AD 암호를 재설정 하거나 BitLocker 복구 키에 액세스 하는 직접 옵션을 누릴 수 있습니다. 웹 브라우저에서 대신 Windows 잠금 화면에서 직접 암호를 재설정 하려면 Azure AD를 사용할 수 있습니다. 이러한 사용자를 위한 마찰 기능과 조직의 기술 지원팀 비용을 절감 하는 데 도움이 합니다.  

자세한 내용은 참조 하세요. [빠른 시작: 셀프 서비스 암호 재설정](https://docs.microsoft.com/azure/active-directory/authentication/quickstart-sspr)합니다.

#### <a name="enterprise-state-roaming"></a>엔터프라이즈 상태 로밍
Azure AD에 가입 된 모든 장치는 클라우드로 해당 설정을 동기화 수 있습니다. 사용자가 로그인 동기화 생산성 환경에 대 한 모든 설정을 모든 장치입니다.  



## <a name="value-proposition"></a>가치 제안

디지털 전환을 가속화 방법 중 하나를 통해 Azure AD에 장치를 조인 합니다. Microsoft 365에서 제공 하는 더 많은 기능이 있습니다. 더 나은 환경을 해야 하 고 데이터에 대 한 보안을 강화 해야 합니다. 

Azure AD는 예를 들어 몇 가지 옵션을 작업을 쉽게 로드를 제공 합니다.

- 단일 위치에서 조직의 모든 장치 id 관리  

- 셀프 서비스 암호 재설정을 사용 하 여 기술 지원팀 비용을 줄이세요. 그런 다음 언제 든 지 장치에서 Windows 10 잠금 화면에서 암호를 재설정할 수 있습니다 사용자.  



## <a name="configure"></a>구성

온-프레미스 Active Directory 환경에 이미 있는 경우 Azure AD에 도메인 가입 장치를 조인 하려는 구성 하이브리드 Azure AD에 가입 된 장치입니다. 자세한 내용은 [하이브리드 Azure Active Directory 조인 구현을 계획 하는 방법을](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)합니다. 

Configuration Manager에는 클라이언트 설정을 [Azure AD를 사용 하 여 새 Windows 10 도메인에 가입 된 장치를 자동으로 등록](/sccm/core/clients/deploy/about-client-settings#automatically-register-new-windows-10-domain-joined-devices-with-azure-active-directory)합니다. 클라이언트 설정 구성에 대 한 자세한 내용은 참조 하세요. [클라이언트 설정을 구성 하는 방법을](/sccm/core/clients/deploy/configure-client-settings)합니다.

Azure를 구성 하려는 경우 AD 가입 없이 온-프레미스 도메인에 조인 하 여 장치에 대 한 Azure에 대 한 고려 사항을 검토 환경에서 AD 가입 합니다. Azure AD 조인 사용 하기로 되 면 조직의 요구에 따라 배포 하는 많은 옵션이 있습니다. 자세한 내용은 다음 아티클을 참조하세요.
- [방법: Azure AD 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)  
- [프로 비전 옵션 이해](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan#understand-your-provisioning-options)  

