---
title: "사이트에 클라이언트 할당 | Microsoft 문서"
description: "System Center Configuration Manager에서 사이트에 클라이언트 할당"
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ba9b623f-6e86-4006-93f2-83d563de0cd0
caps.latest.revision: "10"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: fbac58f3745839d974f9ec865fee313dda211d0a
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-assign-clients-to-a-site-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 클라이언트를 설치한 후 Configuration Manager 기본 사이트에 먼저 가입시켜야 관리할 수 있습니다. 클라이언트가 가입하는 사이트를 *할당된 사이트*라고 합니다. 클라이언트는 중앙 관리 사이트 또는 보조 사이트에 할당할 수 없습니다.  

할당 프로세스는 클라이언트가 성공적으로 설치된 후 실행되며 클라이언트 컴퓨터를 관리할 사이트를 결정합니다. 클라이언트를 사이트에 직접 할당하거나 자동 사이트 할당을 사용하면 됩니다. 자동 사이트 할당을 사용할 경우 클라이언트는 현재 네트워크 위치에 따른 적합한 사이트 또는 계층 구조에 대해 구성된 대체 사이트를 자동으로 검색합니다.

Configuration Manager 등록 중 모바일 장치 클라이언트를 설치할 때 항상 자동으로 장치가 사이트에 할당됩니다. 컴퓨터에 클라이언트를 설치할 때 클라이언트를 사이트에 할당할지 여부를 선택할 수 있습니다. 그러나 설치 후 사이트에 할당되지 않는 클라이언트는 사이트 할당이 완료되기 전에는 관리되지 않습니다.  
 

> [!NOTE]  
>  항상 동일한 버전의 Configuration Manager를 실행하는 사이트에 클라이언트를 할당합니다. 최신 릴리스에서 이전 릴리스의 사이트에 Configuration Manager 클라이언트를 할당하지 마세요.   필요한 경우 클라이언트에 사용 중인 동일한 Configuration Manager 버전으로 기본 사이트를 업데이트합니다.  

클라이언트는 사이트에 할당된 후 해당 사이트에 계속 할당된 상태로 유지되며 자신의 IP 주소를 변경하고 다른 사이트로 로밍하는 경우에도 마찬가지입니다. 관리자만 수동으로 클라이언트를 다른 사이트에 할당하거나 클라이언트 할당을 제거할 수 있습니다.  

> [!WARNING]  
>  클라이언트가 사이트에 할당된 상태로 유지되지 않는 예외는 클라이언트를 쓰기 필터가 설정된 Windows Embedded 장치에 할당하는 경우입니다. 클라이언트를 할당하기 전에 먼저 쓰기 필터를 해제하지 않으면 클라이언트의 사이트 할당 상태는 장치가 다음에 다시 시작할 때 원래 상태로 되돌아갑니다.  
>   
>  예를 들어 클라이언트에 자동 사이트 할당이 구성되어 있는 경우 시작 시 할당이 다시 실행되어 클라이언트는 다른 사이트에 할당될 수 있습니다. 클라이언트에 자동 사이트 할당이 구성되지 않았지만 수동 사이트 할당이 필요한 경우, 시작 후 클라이언트를 수동으로 재할당해야 Configuration Manager를 사용하여 이 클라이언트를 다시 관리할 수 있습니다.  
>   
>  이 작업을 생략하려면 클라이언트를 임베디드 장치에 할당하기 전에 쓰기 필터를 사용하지 않도록 설정한 다음 사이트 할당의 성공을 확인한 후 쓰기 필터를 다시 사용하도록 설정합니다.  

클라이언트 할당에 실패하면 클라이언트 소프트웨어는 설치된 상태로 유지되지만 관리되지 않습니다. 클라이언트는 설치 후 사이트에 할당되지 않았거나 사이트에 할당되었지만 관리 지점과 통신할 수 없는 경우 관리되지 않는 것으로 간주됩니다.  

##  <a name="using-manual-site-assignment-for-computers"></a>컴퓨터에 대해 수동 사이트 할당 사용  
 다음 두 가지 방법으로 클라이언트 컴퓨터를 사이트에 수동으로 할당할 수 있습니다.  

-   사이트 코드를 지정하는 클라이언트 설치 속성을 사용합니다.  

-   제어판의 **Configuration Manager**에서 사이트 코드를 지정합니다.  

> [!NOTE]  
>  클라이언트 컴퓨터를 존재하지 않는 Configuration Manager 사이트 코드에 수동으로 할당하면 사이트 할당은 실패합니다.   

##  <a name="BKMK_AutomaticAssignment"></a> 컴퓨터에 대해 자동 사이트 할당 사용  
 자동 사이트 할당은 클라이언트 배포 중 실행되거나 제어판의 **Configuration Manager 속성** 의 **고급** 탭에서 **사이트 찾기** 를 클릭하면 실행할 수 있습니다. Configuration Manager 클라이언트는 자체 네트워크 위치를 Configuration Manager 계층 구조에 구성된 경계와 비교합니다. 클라이언트의 네트워크 위치가 사이트 할당에 대해 설정된 경계 그룹에 속하거나 계층이 대체 사이트를 사용하도록 구성된 경우 클라이언트가 해당 사이트에 자동으로 할당되므로 사이트 코드를 지정할 필요가 없습니다.  

 경계를 다음 중 하나 이상의 방법으로 구성할 수 있습니다.  

-   IP 서브넷  

-   Active Directory 사이트  

-   IP v6 접두사  

-   IP 주소 범위  

> [!NOTE]  
>  Configuration Manager 클라이언트에 여러 네트워크 어댑터가 있어서 여러 IP 주소가 있는 경우 클라이언트 사이트 할당의 평가에 사용되는 IP 주소는 임의로 선택됩니다.  

 사이트 할당에 경계 그룹을 구성하는 방법과 자동 사이트 할당에 대체 사이트를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 경계 및 경계 그룹 정의](../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md)를 참조하세요.  

 자동 사이트 할당을 사용하는 Configuration Manager 클라이언트는 Active Directory Domain Service에 게시된 사이트 경계 그룹의 검색을 시도합니다. Active Directory 스키마가 Configuration Manager에 대해 확장되지 않았거나 클라이언트가 작업 그룹 컴퓨터인 이유 등으로 이 작업이 실패하면 클라이언트는 관리 지점에서 경계 그룹 정보를 가져올 수 있습니다.  

 클라이언트 컴퓨터에서 사용할 관리 지점은 클라이언트 컴퓨터 설치 시 지정할 수 있습니다. 또는 클라이언트는 DNS 게시나 WINS 등을 사용하여 관리 지점을 찾을 수도 있습니다.  

 클라이언트가 네트워크 위치를 포함하는 경계 그룹과 연결된 사이트를 찾을 수 없고 계층에 대체 사이트가 없는 경우, 클라이언트는 사이트에 할당될 수 있을 때까지 10분마다 검색을 다시 시도합니다.  

 Configuration Manager 클라이언트 컴퓨터는 다음 중 하나라도 해당되면 사이트에 자동으로 할당될 수 없으며 대신 수동으로 할당되어야 합니다.  

-   현재 사이트에 할당되어 있습니다.  

-   인터넷상에 있거나 인터넷 전용 클라이언트로 구성되었습니다.  

-   네트워크 위치가 Configuration Manager 계층에 구성된 경계 그룹 중 어느 하나에도 속하지 않으며 계층에 대한 대체 사이트도 없습니다.  

##  <a name="completing-site-assignment-by-checking-site-compatibility"></a>사이트 호환성 검사를 통한 사이트 할당 완료  
 클라이언트가 할당된 사이트를 찾으면 Configuration Manager 사이트에서 관리할 수 있도록 해당 클라이언트의 버전 및 운영 체제가 검사됩니다. 예를 들어 Configuration Manager는 Configuration Manager 2007 클라이언트, System Center 2012 Configuration Manager 클라이언트 또는 Windows 2000을 실행하는 클라이언트를 관리할 수 없습니다.  

 Windows 2000을 실행하는 클라이언트를 Configuration Manager 사이트에 할당하면 사이트 할당에 실패합니다. Configuration Manager 2007 클라이언트 또는 System Center 2012 Configuration Manager 클라이언트를 Configuration Manager(현재 분기) 사이트에 할당하는 경우 사이트 할당 시 자동 클라이언트 업그레이드를 지원합니다. 그러나 이전 세대 클라이언트가 Configuration Manager(현재 분기) 클라이언트로 업그레이드될 때까지 Configuration Manager에서 클라이언트 설정, 응용 프로그램 또는 소프트웨어 업데이트를 사용하여 해당 클라이언트를 관리할 수 없습니다.  

> [!NOTE]  
>  Configuration Manager 2007 또는 System Center 2012 Configuration Manager 클라이언트를 Configuration Manager(현재 분기) 사이트에 사이트 할당하도록 지원하려면 계층 구조에 대한 자동 클라이언트 업그레이드를 구성해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터용 클라이언트를 업그레이드하는 방법](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md)을 참조하세요.  

Configuration Manager는 Configuration Manager(현재 분기) 클라이언트를 지원하는 사이트에 할당했는지도 확인합니다. 다음 시나리오는 이전 버전의 Configuration Manager에서 마이그레이션하는 동안 발생할 수 있습니다.  

-   시나리오: 자동 사이트 할당을 사용했고 경계가 이전 버전의 Configuration Manager에서 정의된 경계와 겹칩니다.  

     이 경우 클라이언트는 자동으로 Configuration Manager(현재 분기) 사이트를 찾으려고 시도합니다.  

     클라이언트에서 먼저 Active Directory Domain Services를 확인하고 게시된 Configuration Manager(현재 분기) 사이트를 찾을 경우 사이트 할당이 성공합니다. Configuration Manager 사이트가 게시되지 않았거나 컴퓨터가 작업 그룹 클라이언트인 이유 등으로 이 작업이 실패하면 클라이언트는 할당된 관리 지점에서 사이트 정보를 확인합니다.  

    > [!NOTE]  
    >  클라이언트 설치 중 Client.msi 속성 **SMSMP=&lt;server_name>**을 사용하여 클라이언트에 관리 지점을 할당할 수 있습니다.  

     두 방법 모두 실패하면 사이트 할당은 실패하고 이 경우 수동으로 클라이언트를 할당해야 합니다.  

-   시나리오: Configuration Manager(현재 분기) 클라이언트를 자동 사이트 할당이 아닌 특정 사이트 코드를 사용하여 할당하고 System Center 2012 R2 Configuration Manager보다 이전 버전의 Configuration Manager에 대해 사이트 코드를 잘못 지정했습니다.  

     이 경우 사이트 할당은 실패하며 클라이언트를 Configuration Manager(현재 분기) 사이트에 수동으로 다시 할당해야 합니다.  

 사이트 호환성 검사에는 다음 조건 중 하나가 필요합니다.  

-   클라이언트가 Active Directory Domain Services에 게시되는 사이트 정보에 액세스할 수 있습니다.  

-   클라이언트에서 사이트 내 관리 지점과 통신할 수 있습니다.  

 사이트 호환성 검사가 성공적으로 완료되지 못할 경우 사이트 할당은 실패하고 클라이언트는 사이트 호환성 검사가 다시 실행되어 성공하기 전까지 관리되지 않습니다.  

 사이트 호환성 검사의 예외는 클라이언트가 인터넷 기반 관리 지점에 대해 구성된 경우입니다. 이 경우 사이트 호환성 검사는 수행되지 않습니다. 클라이언트를 인터넷 기반 사이트 시스템이 포함된 사이트에 할당하고 인터넷 기반 관리 지점을 지정할 경우 클라이언트를 올바른 사이트에 할당하는지 확인하세요. 클라이언트를 Configuration Manager 2007 사이트, System Center 2012 Configuration Manager 사이트 또는 인터넷 기반 사이트 시스템 역할이 없는 Configuration Manager 사이트에 잘못 할당하는 경우 해당 클라이언트는 관리되지 않습니다.  

##  <a name="locating-management-points"></a>관리 지점 찾기  
 클라이언트는 사이트에 성공적으로 할당된 후 해당 사이트에서 관리 지점을 찾습니다.  

 클라이언트 컴퓨터는 사이트에서 연결할 수 있는 관리 지점 목록을 다운로드합니다. 이 작업은 클라이언트가 다시 시작할 때마다, 25시간에 한 번씩 또는 클라이언트에서 네트워크 변경 내용(예: 컴퓨터의 네트워크 연결 끊김 및 다시 연결)을 검색하거나 새 IP 주소를 받을 때 수행됩니다. 목록에는 인트라넷상의 관리 지점 및 관리 지점이 HTTP 또는 HTTPS를 통한 클라이언트 연결을 허용하는지 여부 등이 포함됩니다. 클라이언트 컴퓨터가 인터넷상에 있고 클라이언트에 아직 관리 지점 목록이 없는 경우 이 클라이언트는 지정된 인터넷 기반 관리 지점에 연결하여 관리 지점 목록을 가져옵니다. 클라이언트에 할당된 사이트에 대한 관리 지점의 목록이 있는 경우 클라이언트는 연결할 관리 지점 하나를 선택합니다.  

-   클라이언트가 인트라넷상에 있고 사용할 수 있는 유효한 PKI 인증서를 갖고 있는 경우 이 클라이언트는 HTTP 관리 지점 이전에 HTTPS 관리 지점을 선택합니다. 그런 다음 이 클라이언트는 포리스트 멤버 자격에 기반해 가장 가까운 관리 지점을 찾습니다.  

-   인터넷상에 있는 클라이언트는 인터넷 기반 관리 지점 중 하나를 임의로 선택합니다.  

Configuration Manager에서 등록된 모바일 장치 클라이언트는 할당된 사이트에 있는 하나의 관리 지점에만 연결하며 보조 사이트의 관리 지점에는 연결하지 않습니다. 이러한 클라이언트는 항상 HTTPS를 통해 연결하며 이에 관리 지점은 인터넷을 통한 클라이언트 연결을 허용하도록 구성되어야 합니다. 기본 사이트에 모바일 장치 클라이언트에 대한 관리 지점이 둘 이상 있을 경우 Configuration Manager는 할당 시 이 관리 지점 중 하나를 임의로 선택하고 모바일 장치 클라이언트는 동일한 관리 지점을 계속 사용합니다.  

클라이언트가 사이트 내 관리 지점에서 클라이언트 정책을 다운로드하면 이 클라이언트는 관리되는 클라이언트가 됩니다.  

##  <a name="downloading-site-settings"></a>사이트 설정 다운로드  
 사이트 할당이 성공하고 클라이언트에서 관리 지점을 찾으면 사이트 호환성 검사를 위해 Active Directory 도메인 서비스를 사용하는 클라이언트 컴퓨터는 할당된 사이트에 대한 클라이언트 관련 사이트 설정을 다운로드합니다. 이 설정에는 클라이언트 인증서 선택 기준, CRL(인증서 해지 목록) 사용 여부 및 클라이언트 요청 포트 번호 등이 포함됩니다. 클라이언트는 이 설정을 주기적으로 계속 확인합니다.  

 클라이언트 컴퓨터는 Active Directory Domain Services에서 사이트 설정을 가져올 수 없는 경우 자체 관리 지점에서 사이트 설정을 다운로드합니다. 또한 클라이언트 컴퓨터는 클라이언트 강제를 통해 설치된 경우 사이트 설정을 가져올 수 있습니다. 또는 CCMSetup.exe 및 클라이언트 설치 속성을 사용하면 사이트 설정을 수동으로 지정할 수 있습니다. 클라이언트 설치 속성에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

##  <a name="downloading-client-settings"></a>클라이언트 설정 다운로드  
 모든 클라이언트는 기본 클라이언트 설정 정책 및 해당되는 사용자 지정 클라이언트 설정 정책을 다운로드합니다. 소프트웨어 센터는 Windows 컴퓨터와 관련해 이러한 클라이언트 구성 정책에 의존하며 이 구성 정보를 다운로드해야 올바르게 실행될 수 있다고 사용자에게 알립니다. 클라이언트 설정을 처음 다운로드하면 구성된 클라이언트 설정에 따라 어느 정도 시간이 걸릴 수 있으며 일부 클라이언트 관리 작업은 이 프로세스가 완료되어야 실행할 수 있습니다.  

##  <a name="verifying-site-assignment"></a>사이트 할당 확인  
 다음 방법을 사용하여 사이트 할당에 성공했는지 확인할 수 있습니다.  

-   Windows 컴퓨터의 클라이언트인 경우 제어판에서 Configuration Manager를 사용하여 **사이트** 탭에 사이트 코드가 올바로 표시되는지 확인합니다.  

-   클라이언트 컴퓨터의 **자산 및 호환성** 작업 영역 > **장치** 노드에서 컴퓨터가 **클라이언트** 열에 대해 **예**를 표시하고 **사이트 코드** 열에 올바른 기본 사이트 코드를 표시하는지 확인합니다.  

-   모바일 장치 클라이언트 컴퓨터의 **자산 및 호환성** 작업 영역에서 **모든 모바일 장치** 컬렉션을 사용하여 모바일 장치가 **클라이언트** 열에 대해 **예** 를 표시하고 **사이트 코드** 열에 올바른 기본 사이트 코드를 표시하는지 확인합니다.  

-   클라이언트 할당 및 모바일 장치 등록과 관련된 보고서를 사용합니다.  

-   클라이언트 컴퓨터의 경우 클라이언트에서 LocationServices.log 파일을 사용합니다.  

##  <a name="roaming-to-other-sites"></a>다른 사이트로 로밍  
 인트라넷의 클라이언트 컴퓨터가 기본 사이트에 할당되어 있지만 다른 사이트에 대해 구성된 경계 그룹에 속하도록 네트워크 위치를 변경하면 해당 다른 사이트로 로밍됩니다. 해당 다른 사이트가 할당된 사이트의 보조 사이트인 경우 클라이언트는 보조 사이트의 관리 지점을 사용하여 클라이언트 정책을 다운로드하고 클라이언트 데이터를 업로드할 수 있습니다. 그러면 이러한 데이터 전송으로 인해 네트워크가 느려지는 문제가 발생하지 않습니다. 하지만 이러한 클라이언트가 다른 기본 사이트의 경계로 로밍되거나 할당된 사이트의 자식 사이트가 아닌 보조 사이트의 경계로 로밍되면 이러한 클라이언트는 항상 할당된 사이트의 관리 지점을 사용하여 클라이언트 정책을 다운로드하고 데이터를 사이트로 업로드합니다.  

 다른 사이트(모든 기본 사이트 및 모든 보조 사이트)로 로밍하는 이러한 클라이언트 컴퓨터는 콘텐츠 위치 요청에 대해 다른 사이트의 관리 지점을 항상 사용할 수 있습니다. 현재 사이트의 관리 지점은 클라이언트가 요청한 콘텐츠를 포함하는 배포 지점 목록을 클라이언트에 제공합니다.  

 인터넷 전용 클라이언트 관리에 대해 구성된 클라이언트 컴퓨터의 경우 및 Configuration Manager를 통해 등록된 모바일 장치와 Mac 컴퓨터의 경우 이러한 컴퓨터는 할당된 사이트의 관리 지점과만 통신합니다. 이러한 클라이언트는 보조 사이트의 관리 지점 또는 다른 기본 사이트의 관리 지점과 통신하지 않습니다.  
