---
title: "클라이언트에 대한 사이트 시스템 역할 | Microsoft 문서"
description: "System Center Configuration Manager에서 클라이언트에 대한 사이트 시스템 역할을 결정합니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
caps.latest.revision: "9"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 65c165ababafab3dd0d9ce8f1ce775be0d72a573
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="determine-the-site-system-roles-for-system-center-configuration-manager-clients"></a>System Center Configuration Manager 클라이언트에 대한 사이트 시스템 역할 결정

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 Configuration Manager 클라이언트를 배포해야 하는 사이트 시스템 역할을 확인할 수 있습니다.  

 계층 구조에서 필수 사이트 시스템 역할을 설치할 위치에 대한 자세한 내용은 [System Center Configuration Manager에 대한 사이트 계층 구조 디자인](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)을 참조하세요.  

 필요한 사이트 시스템 역할을 설치 및 구성하는 방법에 대한 자세한 내용은 [사이트 시스템 역할 설치](../../../../core/servers/deploy/configure/install-site-system-roles.md)를 참조하세요.  

##  <a name="determine-if-you-need-a-management-point"></a>관리 지점이 필요한지 확인  
 기본적으로 모든 Windows 클라이언트 컴퓨터에서는 배포 지점을 사용하여 Configuration Manager 클라이언트를 설치하며 배포 지점을 사용할 수 없을 경우에는 관리 지점으로 대체할 수 있습니다. 그러나 사용자는 CCMSetup 명령줄 속성인 **/source:<경로\>**를 사용하면 대체 원본에서 Windows 클라이언트를 컴퓨터에 설치할 수 있습니다. 예를 들어 인터넷에서 클라이언트를 설치할 경우 이러한 작업을 수행할 수 있습니다. 다른 예로는, 필요한 포트가 방화벽에서 차단되거나 낮은 대역폭 연결을 사용하는 이유 등으로 클라이언트 설치 중 컴퓨터와 관리 지점 간에 네트워크 패킷을 전송하지 않으려는 경우를 들 수 있습니다. 그러나 모든 클라이언트는 관리 지점과 통신해야 사이트에 할당될 수 있으며 Configuration Manager를 통해 관리될 수 있습니다.  

 CCMSetup 명령줄 속성 **/source:<경로\>**에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

 계층에서 둘 이상의 관리 지점을 설치할 경우 클라이언트는 포리스트 멤버 자격 및 네트워크 위치에 따라 관리 지점 하나에 자동으로 연결합니다. 하나의 보조 사이트에 둘 이상의 관리 지점을 설치할 수 없습니다.  

 Configuration Manager에 등록하는 Mac 컴퓨터 클라이언트 및 모바일 장치 클라이언트에는 항상 클라이언트 설치를 위한 관리 지점이 필요합니다. 이 관리 지점은 기본 사이트에 위치하고 모바일 장치를 지원하도록 구성되어야 하며, 인터넷으로부터의 클라이언트 연결을 수락해야 합니다. 이러한 클라이언트는 보조 사이트에 있는 관리 지점을 사용하거나 다른 기본 사이트에 있는 관리 지점에 연결할 수 없습니다.  

##  <a name="determine-if-you-need-a-fallback-status-point"></a>대체 상태 지점이 필요한지 확인  
 대체 상태 지점을 사용하여 Windows 컴퓨터에 대한 클라이언트 배포를 모니터링할 수 있습니다. 또한 관리 지점과 통신할 수 없어 관리되지 않는 Windows 컴퓨터 클라이언트도 식별할 수 있습니다. Configuration Manager에 의해 등록되는 Mac 컴퓨터 및 모바일 장치와 Exchange Server 커넥터를 사용하여 관리되는 모바일 장치는 대체 상태 지점을 이용하지 않습니다.  

 대체 상태 지점은 클라이언트 활동 및 클라이언트 상태를 모니터링하는 데 필요하지 않습니다.  

 대체 상태 지점은 항상 HTTP를 통해 클라이언트와 통신하는데, HTTP는 인증되지 않은 연결을 사용하며 데이터를 일반 텍스트로 전송합니다. 따라서, 대체 상태 지점은 각종 공격에 취약하며 특히 인터넷 기반 클라이언트 관리 방식과 함께 사용될 경우에 더욱 취약해집니다. 공격 노출 영역을 줄이려면 대체 상태 지점 실행을 위해 항상 전용 서버를 배치하고 프로덕션 환경에서 해당 서버에 다른 사이트 시스템 역할을 설치하지 않아야 합니다.  

 다음 조건에 모두 해당하는 경우 대체 상태 지점을 설치합니다.  

-   해당 클라이언트 컴퓨터가 관리 지점과 통신할 수 없더라도 Windows 컴퓨터의 클라이언트 통신 오류를 사이트에 전송하려 합니다.  

-   대체 상태 지점에서 전송되는 데이터를 표시하는 Configuration Manager 클라이언트 배포 보고서를 사용하려고 합니다.  

-   이 사이트 시스템 역할을 위한 전용 서버가 있고 해당 서버를 공격으로부터 보호할 추가적인 보안 수단이 있습니다.  

-   대체 상태 지점의 사용으로 인한 이점이 인증되지 않은 연결이나 HTTP 트래픽을 통한 일반 텍스트 전송과 관련된 보안 위협을 보충하고도 남습니다.  

 인증되지 않은 연결 및 일반 텍스트 전송 기능을 사용하여 웹 사이트를 실행하는 데 따른 보안 위협이 클라이언트 통신 문제를 확인할 수 있는 데 따른 이점보다 더 크다면 대체 상태 지점을 설치하지 마세요.  

##  <a name="determine-whether-you-need-a-reporting-services-point"></a>보고 서비스 지점이 필요한지 확인  
 Configuration Manager는 Configuration Manager 콘솔에서 클라이언트 설치, 할당 및 관리를 모니터링할 수 있는 많은 보고서를 제공합니다. 일부 클라이언트 배포 보고서는 클라이언트가 대체 상태 지점에 할당되어 있어야 사용할 수 있습니다.  

 보고서가 없어도 클라이언트를 배포할 수는 있으며, Configuration Manager 콘솔에서 일부 배포 정보를 확인하거나 클라이언트 로그 파일을 통해 세부 정보를 확인할 수는 있습니다. 하지만 클라이언트 보고서에서는 클라이언트 배포를 모니터링하고 문제를 해결하는 데 유용한 정보를 제공합니다.  

##  <a name="determine-if-you-need-an-enrollment-point-and-an-enrollment-proxy-point"></a>등록 지점 및 등록 프록시 지점이 필요한지 확인  
 Configuration Manager를 사용하려면 모바일 장치를 등록하고 Mac 컴퓨터용 인증서를 등록할 등록 지점 및 등록 프록시 지점이 필요합니다. Exchange Server 커넥터를 사용하여 모바일 장치를 관리하거나, 모바일 장치 레거시 클라이언트(예: Windows CE용 클라이언트)를 설치하거나, Configuration Manager와는 별도로 Mac 컴퓨터에서 클라이언트 인증서를 요청 및 설치할 경우에는 이러한 사이트 시스템 역할이 필요하지 않습니다.  

##  <a name="determine-if-you-need-a-distribution-point"></a>배포 지점이 필요한지 확인  
 Windows 컴퓨터에서 Configuration Manager 클라이언트를 설치할 때는 배포 지점이 필요하지 않습니다. 그러나 기본적으로 Configuration Manager에서는 배포 지점을 사용하여 Windows 컴퓨터에 클라이언트 원본 파일을 설치하지만 관리 지점에서 이 파일을 다운로드하는 대체 방식을 사용할 수도 있습니다. 배포 지점은 Configuration Manager에서 등록하는 모바일 장치 클라이언트를 설치하는 데는 사용되지 않지만 모바일 장치 레거시 클라이언트를 설치할 경우에는 사용됩니다. Configuration Manager 클라이언트를 운영 체제 배포의 일부로 설치하는 경우 운영 체제 이미지는 배포 지점에서 저장되고 검색됩니다.  

 대부분의 Configuration Manager 클라이언트를 설치하는 데는 배포 지점이 필요하지 않을 수도 있지만 클라이언트에 응용 프로그램 및 소프트웨어 업데이트와 같은 소프트웨어를 설치하려면 배포 지점이 필요합니다.  

##  <a name="determine-if-you-need-an-application-catalog-website-point-and-an-application-catalog-web-services-point"></a>응용 프로그램 카탈로그 웹 사이트 지점 및 응용 프로그램 카탈로그 웹 서비스 지점이 필요한지 확인  
 클라이언트를 배포할 때 응용 프로그램 카탈로그 웹 사이트 지점 및 응용 프로그램 카탈로그 웹 서비스 지점은 필요하지 않습니다. 그러나 클라이언트 배포 프로세스의 일부로 두 지점을 설치하려는 경우도 있으므로 이러한 사용자는 Windows 컴퓨터에 Configuration Manager 클라이언트가 설치되는 즉시 다음 작업을 수행하면 됩니다.  

-   모바일 장치를 초기화합니다.  

-   응용 프로그램 카탈로그에서 응용 프로그램을 검색해 설치합니다.  

-   배포 목적이 **사용 가능**인 사용자 및 장치에 응용 프로그램을 배포합니다.  

##  <a name="determine-whether-you-require-a-cloud-management-gateway-connector-point"></a>클라우드 관리 게이트웨이 연결점이 필요한지 확인 

[인터넷에서 클라이언트를 관리](/sccm/core/clients/manage/manage-clients-internet)하도록 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/setup-cloud-management-gateway)를 설정하는 경우에는 클라우드 관리 게이트웨이 연결점이 필요합니다.


 