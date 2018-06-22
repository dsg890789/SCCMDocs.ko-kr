---
title: 보안 기본 사항
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 보안 계층에 대해 알아봅니다.
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 035b7f73-8b78-4ed1-835e-a31f9a5c4a02
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 86191b4ebf1ba03cbc95776186c452f728cc1a2c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32338264"
---
# <a name="fundamentals-of-security-for-system-center-configuration-manager"></a>System Center Configuration Manager의 보안 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 보안은 여러 계층으로 구성됩니다. 첫 번째 계층 구조는 운영 체제 및 네트워크 모두에 대한 Windows 보안 기능을 통해 제공되며 여기에는 다음이 포함됩니다.  

-   Configuration Manager 구성 요소 간 파일 전송을 위한 파일 공유  

-   파일과 레지스트리 키를 보호하도록 돕는 ACL(액세스 제어 목록)  

-   통신을 보호하도록 돕는 IPsec(인터넷 프로토콜 보안)  

-   보안 정책을 설정하기 위한 그룹 정책  

-   Configuration Manager 콘솔과 같은 배포 응용 프로그램에 대한 DCOM(Distributed Component Object Model) 권한  

-   보안 주체를 저장할 Active Directory Domain Services  

-   Configuration Manager 설치 과정에서 만들어진 일부 그룹을 포함하여 Windows 계정 보안  

또한 방화벽, 침입 검색 등의 추가 보안 구성 요소를 통해 전체 환경을 방어할 수 있습니다. 업계 표준 PKI(공개 키 인프라) 구현으로 발급된 인증서는 인증, 서명 및 암호화를 제공하는 데 유용합니다.  

Windows 서버 및 네트워크 인프라에서 제공하는 보안 외에도, Configuration Manager는 몇 가지 방법으로 Configuration Manager 콘솔 및 리소스에 대한 액세스를 제어합니다. 기본적으로, 로컬 관리자만 Configuration Manager 콘솔이 설치된 컴퓨터에서 해당 콘솔을 실행하는 데 필요한 파일 및 레지스트리 키에 대한 권한을 보유하고 있습니다.  

그 다음 보안 계층은 WMI(Windows Management Instrumentation), 특히 SMS 공급자를 통한 액세스에 기반합니다. SMS 공급자는 Configuration Manager 정보에 대한 사이트 데이터베이스를 쿼리할 수 있는 액세스 권한을 사용자 부여하는 구성 요소입니다. 기본적으로 공급자에 대한 액세스 권한은 로컬 SMS 관리자 그룹의 구성원으로 제한됩니다. 처음에 이 그룹에는 Configuration Manager를 설치한 사용자만 포함됩니다. CIM(Common Information Model) 리포지토리와 SMS 공급자에 대한 권한을 다른 계정에 부여하려면 다른 계정을 SMS 관리자 그룹에 추가해야 합니다.  

최종 보안 계층은 사이트 데이터베이스의 개체에 대한 권한에 기반합니다. 기본적으로, Configuration Manager를 설치하는 데 사용한 로컬 시스템 계정 및 사용자 계정은 사이트 데이터베이스의 모든 개체를 관리할 수 있습니다. Configuration Manager 콘솔에서 역할 기반 관리를 사용하여 추가 관리자에게 권한을 부여하거나 제한할 수 있습니다.  



## <a name="role-based-administration"></a>역할 기반 관리  
 Configuration Manager는 역할 기반 관리를 사용하여 컬렉션, 배포, 사이트 등의 개체를 보호합니다. 이 관리 모델은 모든 사이트 및 사이트 설정에 대한 계층 전체의 보안 액세스를 중앙 집중식으로 정의하고 관리합니다. 보안 역할은 관리자 및 그룹 권한에 할당됩니다. 해당 권한은 여러 Configuration Manager 개체 유형에 연결됩니다(예: 클라이언트 설정을 만들거나 변경하는 데 사용되는 권한). 보안 범위에서는 Microsoft Office를 설치하는 응용 프로그램과 같이 관리자가 관리해야 하는 개체의 특정 인스턴스가 그룹화됩니다. 보안 역할, 보안 범위 및 컬렉션의 조합에 따라 관리자가 보고 관리할 수 있는 개체가 정의됩니다. Configuration Manager에서 일반적인 관리 작업에 대한 일부 기본 보안 역할을 설치합니다. 하지만 특정 비즈니스 요구 사항을 지원할 수 있도록 사용자 자신의 보안 역할을 만들 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager용 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.  

## <a name="securing-client-endpoints"></a>클라이언트 끝점 보안  
 사이트 시스템 역할에 대한 클라이언트 통신은 자체 서명된 인증서를 사용하거나 PKI 인증서를 사용하여 보안됩니다. Configuration Manager에서 인터넷에 있고 모바일 장치 클라이언트와 관련된 것으로 검색되는 컴퓨터 클라이언트에는 PKI 인증서를 사용해야 합니다. PKI 인증서에서는 HTTPS를 사용하여 클라이언트 끝점을 보호합니다. 클라이언트에 연결된 사이트 시스템 역할은 HTTPS 또는 HTTP 클라이언트 통신 중 하나에 대해 구성될 수 있습니다. 클라이언트 컴퓨터는 사용할 수 있는 가장 안전한 방법을 사용하여 항상 통신합니다. 또한 HTTP 통신을 허용하는 사이트 시스템 역할인 경우에만 인트라넷에서 덜 안전한 통신 방법인 HTTP를 사용하도록 대체합니다.  

 자세한 내용은 [System Center Configuration Manager에 대한 암호화 제어 기술 참조](../../protect/deploy-use/cryptographic-controls-technical-reference.md)를 참조하세요.  

## <a name="configuration-manager-accounts-and-groups"></a>Configuration Manager 계정 및 그룹  
 Configuration Manager는 대부분의 사이트 작업에 대해 로컬 시스템 계정을 사용합니다. 일부 관리 작업을 수행하려면 추가 계정을 만들어 유지 관리해야 합니다. 설치 과정에서 여러 기본 그룹 및 SQL Server 역할이 만들어집니다. 이러한 기본 그룹과 SQL Server 역할에 컴퓨터나 사용자 계정을 수동으로 추가해야 할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager에 사용된 계정](../../core/plan-design/hierarchy/accounts.md)을 참조하세요.  

## <a name="privacy"></a>개인 정보 보호  
 엔터프라이즈 관리 제품은 많은 클라이언트를 효과적으로 관리할 수 있기 때문에 다양한 이점을 제공하지만 이 소프트웨어가 조직에서 사용자의 개인 정보에 영향을 줄 수 있다는 점도 알아야 합니다. System Center Configuration Manager에는 데이터를 수집하고 장치를 모니터링하는 많은 도구가 포함되어 있습니다. 일부 도구는 개인 정보 문제를 유발할 수 있습니다.  

 예를 들어 Configuration Manager 클라이언트를 설치할 때 여러 관리 설정이 기본적으로 사용하도록 설정됩니다. 결과적으로 클라이언트 소프트웨어가 Configuration Manager 사이트에 정보를 보냅니다. 클라이언트 정보는 Configuration Manager 데이터베이스에 저장되고, Microsoft로는 전송되지 않습니다. System Center Configuration Manager를 구현하기 전에 개인 정보 요구 사항을 고려합니다.  
