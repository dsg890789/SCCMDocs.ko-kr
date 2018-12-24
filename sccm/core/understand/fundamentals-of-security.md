---
title: 보안 기본 사항
titleSuffix: Configuration Manager
description: Configuration Manager의 보안 계층에 대해 알아봅니다.
ms.date: 10/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1a7d8e6fe1824ab2a7fe3cfb6f89965a4b5800c0
ms.sourcegitcommit: 6e42785c8c26e3c75bf59d3df7802194551f58e1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52456076"
---
# <a name="fundamentals-of-security-for-configuration-manager"></a>Configuration Manager의 보안 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에는 모든 Configuration Manager 환경의 다음 기본 보안 구성 요소가 요약되어 있습니다.
- [보안 계층](#bkmk_layers)
- [역할 기반 관리](#bkmk_rba)
- [클라이언트 엔드포인트 보안](#bkmk_endpoints)
- [Configuration Manager 계정 및 그룹](#bkmk_accounts)
- [개인 정보 보호](#bkmk_privacy)

## <a name="bkmk_layers"></a> 보안 계층

Configuration Manager의 보안은 다음 계층으로 구성됩니다. 
- [Windows OS 및 네트워크 보안](#bkmk_layer-windows)
- [네트워크 인프라: 방화벽, 침입 감지, PKI(공개 키 인프라)](#bkmk_layer-network)
- [Configuration Manager 보안 컨트롤](#bkmk_layer-cm)
- [SMS 공급자](#bkmk_layer-provider)
- [사이트 데이터베이스 사용 권한](#bkmk_layer-db)

#### <a name="bkmk_layer-windows"></a> Windows OS 및 네트워크 보안
첫 번째 계층은 OS 및 네트워크 모두에 대한 Windows 보안 기능을 통해 제공됩니다. 이 계층에는 다음 구성 요소가 포함됩니다.  

-   Configuration Manager 구성 요소 간 파일 전송을 위한 파일 공유  

-   파일과 레지스트리 키를 보호하는 ACL(Access Control 목록)  

-   통신 보호를 지원하는 IPsec(인터넷 프로토콜 보안)  

-   보안 정책을 설정하기 위한 그룹 정책  

-   Configuration Manager 콘솔과 같은 배포 응용 프로그램에 대한 DCOM(Distributed Component Object Model) 권한  

-   보안 주체를 저장할 Active Directory Domain Services  

-   설치 중에 Configuration Manager가 생성하는 일부 그룹을 포함한 Windows 계정 보안  

#### <a name="bkmk_layer-network"></a> 네트워크 인프라

방화벽 및 침입 검색과 같은 추가 보안 구성 요소를 통해 전체 환경을 방어할 수 있습니다. 업계 표준 PKI(공개 키 인프라) 구현으로 발급된 인증서는 인증, 서명 및 암호화를 제공하는 데 유용합니다.  

#### <a name="bkmk_layer-cm"></a> Configuration Manager 보안 컨트롤

Windows 서버 및 네트워크 인프라에서 제공하는 보안 외에도, Configuration Manager는 몇 가지 방법으로 해당 콘솔 및 리소스에 대한 액세스를 제어합니다. 기본적으로 Configuration Manager 콘솔이 설치되는 컴퓨터에 필요한 파일 및 레지스트리 키에 대한 권한은 로컬 관리자만 보유하고 있습니다.  

#### <a name="bkmk_layer-provider"></a> SMS 공급자

그 다음 보안 계층은 WMI(Windows Management Instrumentation), 특히 SMS 공급자를 통한 액세스에 기반합니다. SMS 공급자는 Configuration Manager 정보에 대한 사이트 데이터베이스를 쿼리할 수 있는 액세스 권한을 사용자 부여하는 구성 요소입니다. 기본적으로 공급자에 대한 액세스 권한은 로컬 SMS 관리자 그룹의 구성원으로 제한됩니다. 처음에 이 그룹에는 Configuration Manager를 설치한 사용자만 포함됩니다. CIM(Common Information Model) 리포지토리와 SMS 공급자에 대한 권한을 다른 계정에 부여하려면 다른 계정을 SMS 관리자 그룹에 추가해야 합니다.  

1810 버전부터 관리자가 Configuration Manager 사이트에 액세스하는 데 필요한 최소 인증 수준을 지정할 수 있습니다. 이 기능은 관리자에게 필요한 수준으로 Windows에 로그인하도록 요구합니다. <!--1357013-->  

자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.

#### <a name="bkmk_layer-db"></a> 사이트 데이터베이스 사용 권한

최종 보안 계층은 사이트 데이터베이스의 개체에 대한 권한에 기반합니다. 기본적으로, Configuration Manager를 설치하는 데 사용한 로컬 시스템 계정 및 사용자 계정은 사이트 데이터베이스의 모든 개체를 관리할 수 있습니다. 역할 기반 관리를 사용하여 Configuration Manager 콘솔에서 추가 관리자에게 권한을 부여하고 제한합니다.  



## <a name="bkmk_rba"></a> 역할 기반 관리  

 Configuration Manager는 역할 기반 관리를 사용하여 컬렉션, 배포, 사이트 등의 개체를 보호합니다. 이 관리 모델은 모든 사이트 및 사이트 설정에 대한 계층 전체의 보안 액세스를 중앙 집중식으로 정의하고 관리합니다. 

 관리자가 관리 사용자 및 그룹 사용 권한에 *보안 역할*을 할당합니다. 사용 권한은 여러 Configuration Manager 개체 유형에 연결됩니다(예: 클라이언트 설정 만들기 또는 변경 권한). 

 *보안 범위*에서는 Microsoft Office를 설치하는 응용 프로그램과 같이 관리자가 관리해야 하는 개체의 특정 인스턴스가 그룹화됩니다. 

 보안 역할, 보안 범위 및 컬렉션의 조합에 따라 관리자가 보고 관리할 수 있는 개체가 정의됩니다. Configuration Manager에서 일반적인 관리 작업에 대한 일부 기본 보안 역할을 설치합니다. 특정 비즈니스 요구 사항을 지원하는 고유한 보안 역할을 만듭니다.  

 자세한 내용은 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요.  



## <a name="bkmk_endpoints"></a> 클라이언트 엔드포인트 보안  

 Configuration Manager는 자체 서명, PKI 인증서 또는 Azure AD(Azure Active Directory) 토큰을 사용하여 사이트 시스템 역할에 대한 클라이언트 통신을 보호합니다. 일부 시나리오에서는 PKI 인증서를 사용해야 합니다. 예를 들어 [인터넷 기반 클라이언트 관리](/sccm/core/clients/manage/plan-internet-based-client-management) 및 [모바일 디바이스 클라이언트](/sccm/mdm/plan-design/plan-on-premises-mdm)용 인증서가 있습니다.  

 HTTPS 또는 HTTP 클라이언트 통신을 위해 클라이언트가 연결하는 사이트 시스템 역할을 구성할 수 있습니다. 클라이언트 컴퓨터는 항상 가장 안전한 방법을 사용하여 통신합니다. 클라이언트 컴퓨터는 HTTP 통신을 허용하는 사이트 시스템 역할이 있는 경우에만 덜 안전한 통신 방법으로 보안 수준을 낮춥니다.  

 자세한 내용은 [보안 계획](/sccm/core/plan-design/security/plan-for-security)을 참조하세요.



## <a name="bkmk_accounts"></a> Configuration Manager 계정 및 그룹  

 Configuration Manager는 대부분의 사이트 작업에 대해 로컬 시스템 계정을 사용합니다. 일부 관리 작업을 수행하려면 추가 계정을 만들어 유지 관리해야 합니다. Configuration Manager는 설치 중에 몇 가지 기본 그룹 및 SQL Server 역할을 만듭니다. 이러한 기본 그룹과 SQL Server 역할에 컴퓨터나 사용자 계정을 수동으로 추가해야 할 수 있습니다.  

 자세한 내용은 [Configuration Manager에 사용되는 계정](/sccm/core/plan-design/hierarchy/accounts)을 참조하세요.  



## <a name="bkmk_privacy"></a> 개인 정보 보호  

 Configuration Manager를 구현하기 전에 개인 정보 요구 사항을 고려합니다. 엔터프라이즈 관리 제품은 많은 클라이언트를 효과적으로 관리할 수 있기 때문에 다양한 이점을 제공하지만 이 소프트웨어는 조직의 사용자 개인 정보에 영향을 줄 수 있습니다. Configuration Manager에는 데이터를 수집하고 디바이스를 모니터링하는 많은 도구가 포함되어 있습니다. 일부 도구는 조직의 개인 정보 문제를 유발할 수 있습니다.  

 예를 들어 Configuration Manager 클라이언트를 설치하면 기본적으로 여러 관리 설정이 활성화됩니다. 이 구성을 사용하면 클라이언트 소프트웨어가 Configuration Manager 사이트에 정보를 보냅니다. 사이트는 클라이언트 정보를 사이트 데이터베이스에 저장합니다. 클라이언트 정보는 Microsoft로 직접 전송되지 않습니다. 자세한 내용은 [진단 및 사용 현황 데이터](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조합니다.



## <a name="see-also"></a>참고 항목

- [보안 계획](/sccm/core/plan-design/security/plan-for-security)  

- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  

- [보안 구성](/sccm/core/plan-design/security/configure-security)   

- [엔드포인트 간의 통신](/sccm/core/plan-design/hierarchy/communications-between-endpoints)  

- [암호화 컨트롤 기술 참조](/sccm/core/plan-design/security/cryptographic-controls-tehnical-reference)  
