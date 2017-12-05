---
title: "보안 구성"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager에서 보안 관련 옵션 구성"
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 552e7e3d-e584-4a7c-9155-0f796a14b678
caps.latest.revision: "5"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 11793684a276cbefb371f27642146d46b714b0b2
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2017
---
# <a name="configure-security-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 보안 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서의 정보를 사용하면 System Center Configuration Manager에 대한 보안 관련 옵션을 설정할 수 있습니다.  

##  <a name="BKMK_ConfigureClientPKI"></a> 클라이언트 PKI 인증서의 설정 구성  
IIS(인터넷 정보 서비스)를 사용하는 사이트 시스템에 대한 클라이언트 연결에 PKI(공개 키 인프라) 인증서를 사용하려는 경우 이러한 인증서에 대한 설정을 구성하려면 다음 절차를 수행하십시오.  

#### <a name="to-configure-client-pki-certificate-settings"></a>클라이언트 PKI 인증서 설정을 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 선택합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 선택한 다음 구성할 기본 사이트를 선택합니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택한 다음 **클라이언트 컴퓨터 통신** 탭을 선택합니다.  

    이 탭은 기본 사이트에서만 사용할 수 있습니다. **클라이언트 컴퓨터 통신** 탭이 보이지 않으면 중앙 관리 사이트나 보조 사이트에 연결되지 않았는지 확인하십시오.  

4.  사이트에 할당된 클라이언트가 IIS를 사용하는 사이트 시스템에 연결할 때 항상 클라이언트 PKI 인증서를 사용하도록 하려면 **HTTPS만 사용**을 선택합니다. 그렇지 않고 클라이언트가 PKI 인증서를 사용하지 않아도 된다면 **HTTPS 또는 HTTP**를 선택합니다.  

5.  **HTTPS 또는 HTTP**를 선택한 경우 HTTP 연결에 클라이언트 PKI 인증서를 사용하도록 하려면 **사용 가능한 경우 PKI 클라이언트 인증서(클라이언트 인증 기능) 사용**을 선택합니다. 클라이언트가 사이트 시스템에 대해 자신을 인증할 때 자체 서명된 인증서 대신 이 인증서를 사용합니다. **HTTPS만 사용**을 선택하는 경우에는 이 옵션이 자동으로 선택됩니다.  

    클라이언트가 인터넷에 있다고 검색되거나 인터넷 전용 클라이언트 관리용으로 구성되어 있으면 항상 클라이언트 PKI 인증서를 사용합니다.  

6.  **수정**을 선택하여 클라이언트에 유효한 PKI 클라이언트 인증서가 두 개 이상 있는 경우에 대해 선택한 클라이언트 선택 방법을 구성한 다음 **확인**을 선택합니다.  

    클라이언트 인증서 선택 방법에 대한 자세한 내용은 [PKI 클라이언트 인증서 선택 계획](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection)을 참조하세요.  

7.  CRL(인증서 해지 목록)을 확인할 클라이언트의 확인란을 선택하거나 선택 해제합니다.  

    클라이언트의 CRL 확인에 대한 자세한 내용은 [PKI 클라이언트 인증서 해지 계획](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs)을 참조하세요.  

8.  클라이언트에 대해 신뢰할 수 있는 루트 CA(인증 기관) 인증서를 지정해야 하는 경우 **설정**을 선택하고 루트 CA 인증서 파일을 가져온 다음 **확인**을 선택합니다.  

    이 설정에 대한 자세한 내용은 [PKI 신뢰할 수 있는 루트 인증서 및 인증서 발급자 목록 계획](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRootCAs)을 참조하세요.  

9. **확인**을 선택하여 사이트의 속성 대화 상자를 닫습니다.  

계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.  

##  <a name="BKMK_ConfigureSigningEncryption"></a> 서명 및 암호화 구성  
사이트 시스템에 대해 사이트의 모든 클라이언트가 지원할 수 있는 가장 안전한 서명 및 암호화 설정을 구성하십시오. 이러한 설정은 클라이언트가 HTTP를 통해 자체 서명된 인증서를 사용하여 사이트 시스템과 통신할 수 있는 경우에 특히 중요합니다.  

#### <a name="to-configure-signing-and-encryption-for-a-site"></a>사이트에 대해 서명 및 암호화를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 선택합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 선택한 다음 구성할 기본 사이트를 선택합니다.  

3.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택한 다음 **서명 및 암호화** 탭을 선택합니다.  

    이 탭은 기본 사이트에서만 사용할 수 있습니다. **서명 및 암호화** 탭이 보이지 않으면 중앙 관리 사이트나 보조 사이트에 연결되지 않았는지 확인하십시오.  

4.  원하는 서명 및 암호화 옵션을 구성하고 **확인**을 선택합니다.  

    > [!WARNING]  
    >  **SHA-256 필요**는 선택하기 전에 사이트에 할당되었을 수 있는 모든 클라이언트가 이 해시 알고리즘을 지원할 수 있는지 또는 유효한 PKI 클라이언트 인증 인증서가 있는지를 먼저 확인해야 합니다. SHA-256을 지원하려면 클라이언트에 업데이트나 핫픽스를 설치해야 할 수 있습니다. 예를 들어 Windows Server 2003 SP2를 실행하는 컴퓨터는 [기술 자료 문서 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666)에 언급된 핫픽스를 설치해야 합니다.  
    >   
    >  이 옵션을 선택했지만 클라이언트가 SHA-256을 지원할 수 없고 자체 서명된 인증서를 사용하는 경우 Configuration Manager에서 클라이언트를 거부합니다. 이 시나리오에서 SMS_MP_CONTROL_MANAGER 구성 요소는 메시지 ID 5443을 로깅합니다.  

5.  **확인**을 선택하여 사이트의 **속성** 대화 상자를 닫습니다.  

계층의 모든 기본 사이트에 대해 이 절차를 반복합니다.  

##  <a name="BKMK_ConfigureRBA"></a> 역할 기반 관리 구성  
역할 기반 관리는 각 관리자의 관리 범위를 정의하기 위해 보안 역할, 보안 범위, 그리고 할당된 컬렉션을 결합합니다. 관리 범위에는 관리자가 Configuration Manager 콘솔에서 볼 수 있는 개체 및 해당 개체와 관련이 있고 관리자가 수행할 권한이 있는 작업이 포함됩니다. 역할 기반 관리 구성은 계층의 각 사이트에 적용됩니다.  

다음 링크는 [System Center Configuration Manager용 역할 기반 관리 구성](../../../core/servers/deploy/configure/configure-role-based-administration.md) 문서의 관련 섹션에 연결되어 있습니다.  

-   [사용자 지정 보안 역할 만들기](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)  

-   [보안 역할 구성](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecRole)  

-   [개체에 대한 보안 범위 구성](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigSecScope)  

-   [보안을 관리할 컬렉션 구성](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ConfigColl)  

-   [새 관리자 만들기](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_Create_AdminUser)  

-   [관리자의 관리 범위 수정](../../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_ModAdminUser)  

> [!IMPORTANT]  
>  관리 범위는 다른 관리자의 역할 기반 관리를 구성할 때 할당할 수 있는 개체와 설정을 정의합니다. 역할 기반 관리를 계획하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 역할 기반 관리 기본 사항](../../../core/understand/fundamentals-of-role-based-administration.md)을 참조하세요.  

##  <a name="BKMK_ManageAccounts"></a> Configuration Manager에서 사용되는 계정 관리  
Configuration Manager에서는 여러 가지 작업과 용도를 위해 Windows 계정을 지원합니다.  

여러 가지 작업을 위해 구성된 계정을 보고 Configuration Manager에서 각 계정에 사용하는 암호를 관리하려면 다음 절차를 수행합니다.  

#### <a name="to-manage-accounts-that-are-used-by-configuration-manager"></a>Configuration Manager에서 사용되는 계정을 관리하려면  

1.  Configuration Manager 콘솔에서 **관리**를 선택합니다.  

2.  **관리** 작업 영역에서 **보안**을 확장한 후 **계정**을 선택하여 Configuration Manager용으로 구성된 계정을 봅니다.  

3.  Configuration Manager용으로 구성된 계정의 암호를 변경하려면 계정을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **설정**을 선택하여 **Windows 사용자 계정** 대화 상자를 열고 Configuration Manager에서 계정에 사용할 새 암호를 지정합니다.  

    > [!NOTE]  
    >  지정하는 암호는 Active Directory 사용자 및 컴퓨터의 계정에 지정된 암호와 일치해야 합니다.  

6.  **확인**을 선택하여 절차를 완료합니다.  
