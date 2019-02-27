---
title: 보안 구성
titleSuffix: Configuration Manager
description: Configuration Manager에 대한 보안 관련 옵션을 구성합니다.
ms.date: 11/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4d58f8566f80efa2700f5947f4144623b10eb6ad
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56140595"
---
# <a name="configure-security-in-configuration-manager"></a>Configuration Manager에서 보안 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 정보를 사용하면 Configuration Manager에 대한 보안 관련 옵션을 설정할 수 있습니다. 여기에서는 다음 보안 옵션을 설명합니다.
- 클라이언트 PKI 인증서에 대한 [클라이언트 컴퓨터 통신](#BKMK_ConfigureClientPKI)  
- [서명 및 암호화](#BKMK_ConfigureSigningEncryption)  
- [역할 기반 관리](#BKMK_ConfigureRBA)  
- [계정 관리](#BKMK_ManageAccounts)  
- [Azure Active Directory 구성](#bkmk_azuread)  
- [SMS 공급 기업 인증 구성](#bkmk_auth)  



##  <a name="BKMK_ConfigureClientPKI"></a> 클라이언트 PKI 인증서의 설정 구성  

IIS(인터넷 정보 서비스)를 사용하는 사이트 시스템에 대한 클라이언트 연결에 PKI(공개 키 인프라) 인증서를 사용하려는 경우 이러한 인증서에 대한 설정을 구성하려면 다음 절차를 수행하십시오.  

#### <a name="to-configure-client-pki-certificate-settings"></a>클라이언트 PKI 인증서 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 구성할 기본 사이트를 선택합니다.  

2.  리본에서 **속성**을 선택합니다. 그런 다음, **클라이언트 컴퓨터 통신** 탭으로 전환합니다.  

    이 탭은 기본 사이트에서만 사용할 수 있습니다. **클라이언트 컴퓨터 통신** 탭이 보이지 않으면 중앙 관리 사이트나 보조 사이트에 연결되어 있지 않은지 확인하세요.  

3.  IIS를 사용하는 사이트 시스템에 대한 설정을 선택합니다.  

    - **HTTPS 전용**: 사이트에 할당된 클라이언트는 IIS를 사용하는 사이트 시스템에 연결할 때 항상 클라이언트 PKI 인증서를 사용합니다.  

    - **HTTPS 또는 HTTP**: 클라이언트가 PKI 인증서를 사용하지 않아도 됩니다.  

    - **HTTP 사이트 시스템에 Configuration Manager가 생성한 인증서 사용**: 이 설정에 대한 자세한 내용은 [고급 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 참조하세요.  

4.  클라이언트 컴퓨터의 설정을 선택합니다.  

    - **사용 가능한 경우 PKI 클라이언트 인증서(클라이언트 인증 기능) 사용**: **HTTPS 또는 HTTP** 사이트 서버 설정을 선택한 경우 이 옵션을 선택하여 HTTP 연결에 클라이언트 PKI 인증서를 사용합니다. 클라이언트가 사이트 시스템에 대해 자신을 인증할 때 자체 서명된 인증서 대신 이 인증서를 사용합니다. **HTTPS 전용**을 선택한 경우 이 옵션이 자동으로 선택됩니다.  

    클라이언트에서 사용 가능한 유효한 PKI 클라이언트 인증서가 두 개 이상일 경우 **수정**을 선택하여 클라이언트 인증서 선택 방법을 구성합니다.  

    클라이언트 인증서 선택 방법에 대한 자세한 내용은 [PKI 클라이언트 인증서 선택 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForClientCertificateSelection)을 참조하세요.  

    - **클라이언트에서 사이트 시스템에 대한 CRL(인증서 해지 목록) 확인**: 클라이언트에 대해 이 설정을 사용하도록 설정하면 해지된 인증서에 대해 조직의 CRL을 확인합니다.  

    클라이언트의 CRL 확인에 대한 자세한 내용은 [PKI 클라이언트 인증서 해지 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForCRLs)을 참조하세요.  

5.  신뢰할 수 있는 루트 인증 기관의 인증서를 가져오고, 보고, 삭제하려면 **설정**을 선택합니다.  

    자세한 내용은 [PKI 신뢰할 수 있는 루트 인증서 및 인증서 발급자 목록 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForRootCAs)을 참조하세요.  


계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.  



##  <a name="BKMK_ConfigureSigningEncryption"></a> 서명 및 암호화 구성  

사이트 시스템에 대해 사이트의 모든 클라이언트가 지원할 수 있는 가장 안전한 서명 및 암호화 설정을 구성하십시오. 이러한 설정은 클라이언트가 HTTP를 통해 자체 서명된 인증서를 사용하여 사이트 시스템과 통신할 수 있는 경우에 특히 중요합니다.  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>사이트에 대해 서명 및 암호화를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 구성할 기본 사이트를 선택합니다.  

2.  리본에서 **속성**을 선택한 다음, **서명 및 암호화** 탭으로 전환합니다.  

    이 탭은 기본 사이트에서만 사용할 수 있습니다. **서명 및 암호화** 탭이 보이지 않으면 중앙 관리 사이트 또는 보조 사이트에 연결되지 있지 않은지 확인합니다.  

3.  클라이언트가 사이트와 통신할 수 있도록 서명 및 암호화 옵션을 구성합니다.  

    - **서명 필요**: 클라이언트가 데이터를 관리 지점으로 보내기 전에 데이터에 서명합니다.  

    - **SHA-256 필요**: 클라이언트는 데이터에 서명할 때 SHA-256 알고리즘을 사용합니다.  

    > [!WARNING]  
    >  모든 클라이언트가 해시 알고리즘을 지원하는지 먼저 확인하지 않고 **SHA-256을 요청**하지 마세요. 이러한 클라이언트에는 나중에 사이트에 할당될 수 있는 클라이언트가 포함됩니다.  
    >   
    >  이 옵션을 선택했지만 자체 서명 인증서가 있는 클라이언트가 SHA-256을 지원할 수 없으며 Configuration Manager에서 클라이언트를 거부합니다. SMS_MP_CONTROL_MANAGER 구성 요소는 메시지 ID 5443을 로깅합니다.  

    - **암호화 사용**: 클라이언트가 클라이언트 인벤토리 데이터 및 상태 메시지를 관리 지점으로 보내기 전에 암호화합니다. 3DES 알고리즘을 사용합니다.  

계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.  



##  <a name="BKMK_ConfigureRBA"></a> 역할 기반 관리 구성  

역할 기반 관리는 각 관리자의 관리 범위를 정의하기 위해 보안 역할, 보안 범위, 그리고 할당된 컬렉션을 결합합니다. 범위에는 사용자가 콘솔에서 볼 수 있는 개체와 사용 권한이 있는 개체와 관련된 작업이 포함됩니다. 역할 기반 관리 구성은 계층의 각 사이트에 적용됩니다.  

자세한 내용은 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요. 이 문서에서는 다음 작업을 자세히 설명합니다.  

- 사용자 지정 보안 역할 만들기  

- 보안 역할 구성  

- 개체에 대한 보안 범위 구성  

- 보안을 관리할 컬렉션 구성  

- 새 관리자 만들기  

- 관리자의 관리 범위 수정  

> [!IMPORTANT]  
>  관리 범위는 다른 관리자의 역할 기반 관리를 구성할 때 할당할 수 있는 개체와 설정을 정의합니다. 역할 기반 관리 계획에 대한 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.  



##  <a name="BKMK_ManageAccounts"></a> Configuration Manager에서 사용하는 계정 관리  

Configuration Manager에서는 여러 가지 작업과 용도를 위해 Windows 계정을 지원합니다. 여러 가지 작업을 위해 구성된 계정을 보고 Configuration Manager에서 각 계정에 사용하는 암호를 관리하려면 다음 절차를 수행합니다.  

#### <a name="to-manage-accounts-that-configuration-manager-uses"></a>Configuration Manager에서 사용하는 계정을 관리하려면  

1.  Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **보안**을 확장한 다음, **계정** 노드를 선택합니다.  

2.  계정의 암호를 변경하려면 목록에서 계정을 선택합니다. 그런 다음, 리본에서 **속성**을 선택합니다.  

3.  **설정**을 선택하여 **Windows 사용자 계정** 대화 상자를 엽니다. 이 계정에 사용할 Configuration Manager의 새 암호를 지정합니다.  

    > [!NOTE]  
    >  지정한 암호는 Active Directory에서 이 계정의 암호와 일치해야 합니다.  

자세한 내용은 [Configuration Manager에 사용되는 계정](/sccm/core/plan-design/hierarchy/accounts)을 참조하세요.



##  <a name="bkmk_azuread"></a> Azure Active Directory 구성

Azure AD(Azure Active Directory)와 Configuration Manager를 통합하여 환경을 간소화하고 클라우드를 지원합니다. 사이트와 클라이언트가 Azure AD를 사용하여 인증받도록 허용합니다. 자세한 내용은 [Azure 서비스 구성](/sccm/core/servers/deploy/configure/azure-services-wizard)의 **클라우드 관리** 서비스를 참조하세요.



## <a name="bkmk_auth"></a> SMS 공급 기업 인증 구성

1810 버전부터 관리자가 Configuration Manager 사이트에 액세스하는 데 필요한 최소 인증 수준을 지정할 수 있습니다. 이 기능은 관리자에게 필요한 수준으로 Windows에 로그인하도록 요구합니다. 자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#bkmk_auth)을 참조하세요. <!--1357013-->  



## <a name="see-also"></a>참고 항목

- [보안 계획](/sccm/core/plan-design/security/plan-for-security)  

- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  

- [엔드포인트 간의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints)  

- [암호화 컨트롤 기술 참조](/sccm/core/plan-design/security/cryptographic-controls-tehnical-reference)  

- [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)  
