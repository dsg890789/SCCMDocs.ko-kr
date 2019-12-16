---
title: 클라이언트의 사이트 시스템 역할
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 클라이언트에 대한 사이트 시스템 역할을 결정합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 984e8d92-7327-4b08-9228-0c955e6ac778
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 40328e2156ea238bca29eff4a89c6d32efa2124d
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74658492"
---
# <a name="determine-the-site-system-roles-for-configuration-manager-clients"></a>Configuration Manager 클라이언트를 위한 사이트 시스템 역할 결정

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서는 Configuration Manager 클라이언트를 배포하는 데 필요한 사이트 시스템 역할을 결정하는 데 도움이 됩니다.

이러한 역할을 설치할 계층 구조 내 위치에 대한 자세한 내용은 [사이트 계층 구조 설계](/sccm/core/plan-design/hierarchy/design-a-hierarchy-of-sites)를 참조하세요.  

이러한 역할을 설치하고 구성하는 자세한 방법은 [사이트 시스템 역할 설치](/sccm/core/servers/deploy/configure/install-site-system-roles)를 참조하세요.  

## <a name="management-point"></a>관리 지점

기본적으로 모든 Windows 클라이언트 컴퓨터는 배포 지점을 사용하여 Configuration Manager 클라이언트를 설치합니다. 배포 지점을 사용할 수 없는 경우 관리 지점으로 대체할 수 있습니다. 그러나 사용자는 CCMSetup 명령줄 속성인 `/source:<Path>`를 사용하면 대체 원본의 컴퓨터에 Windows 클라이언트를 설치할 수 있습니다. 예를 들어 인터넷에서 클라이언트를 설치할 경우 이 작업을 수행할 수 있습니다. 또 다른 시나리오는 클라이언트 설치 중에 컴퓨터와 관리 지점 간에 네트워크 패킷을 전송하지 않으려는 경우입니다. 이 시나리오가 가능한 것은 필요한 포트를 방화벽이 차단하거나 연결의 대역폭이 낮기 때문입니다. 그러나 모든 클라이언트는 관리 지점과 통신해야 사이트에 할당될 수 있으며 Configuration Manager를 통해 관리될 수 있습니다.  

클라이언트 명령줄 속성에 대한 자세한 내용은 [클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

계층에서 둘 이상의 관리 지점을 설치할 경우 클라이언트는 포리스트 멤버 자격 및 네트워크 위치에 따라 관리 지점 하나에 자동으로 연결합니다. 하나의 보조 사이트에 둘 이상의 관리 지점을 설치할 수 없습니다.  

Configuration Manager에 등록하는 Mac 컴퓨터 클라이언트 및 모바일 디바이스 클라이언트에는 항상 클라이언트 설치를 위한 관리 지점이 필요합니다. 이 관리 지점은 기본 사이트에 위치하고 모바일 디바이스를 지원하도록 구성되어야 하며, 인터넷으로부터의 클라이언트 연결을 수락해야 합니다. 이러한 클라이언트는 보조 사이트에 있는 관리 지점을 사용하거나 다른 기본 사이트에 있는 관리 지점에 연결할 수 없습니다.  

## <a name="distribution-point"></a>배포 지점

Windows 컴퓨터에서 Configuration Manager 클라이언트를 설치할 때는 배포 지점이 필요하지 않습니다. 기본적으로 Configuration Manager는 배포 지점을 사용하여 Windows 컴퓨터에 클라이언트 원본 파일을 설치합니다. Configuration Manager는 관리 지점에서 이 파일을 다운로드하는 것으로 대체할 수 있습니다. 배포 지점은 Configuration Manager에서 등록하는 모바일 디바이스 클라이언트를 설치하는 데는 사용되지 않지만 모바일 디바이스 레거시 클라이언트를 설치할 경우에는 사용됩니다. Configuration Manager 클라이언트를 OS 배포의 일부로 설치하는 경우 OS 이미지는 배포 지점에서 저장되고 검색됩니다.

대부분의 Configuration Manager 클라이언트를 설치하는 데는 배포 지점이 필요하지 않을 수도 있지만 클라이언트에 애플리케이션 및 소프트웨어 업데이트와 같은 소프트웨어를 설치하려면 배포 지점이 필요합니다.  

## <a name="fallback-status-point"></a>대체 상태 지점

대체 상태 지점을 사용하여 Windows 컴퓨터에 대한 클라이언트 배포를 모니터링할 수 있습니다. 또한 관리 지점과 통신할 수 없기 때문에 관리되지 않는 Windows 컴퓨터 클라이언트도 식별할 수 있습니다.

다음 클라이언트 유형은 대체 상태 지점을 사용하지 않습니다.

- Mac 컴퓨터
- Configuration Manager에서 등록된 모바일 디바이스
- Exchange Server 커넥터를 사용하여 관리되는 모바일 디바이스

대체 상태 지점은 클라이언트 활동 및 클라이언트 상태를 모니터링하는 데는 필요하지 않습니다.  

대체 상태 지점은 항상 HTTP를 통해 클라이언트와 통신하는데, HTTP는 인증되지 않은 연결을 사용하며 데이터를 일반 텍스트로 전송합니다. 이 동작 때문에 대체 상태 지점은 각종 공격에 취약하며 특히 인터넷 기반 클라이언트 관리 방식과 함께 사용될 경우에 더욱 취약해집니다. 공격에 대한 취약성을 줄이려면 항상 대체 상태 지점을 실행하는 전용 서버를 지정하세요. 프로덕션 환경의 동일한 서버에 다른 사이트 시스템 역할을 설치하지 마세요.  

다음 조건에 모두 해당하는 경우 대체 상태 지점을 설치합니다.  

- 해당 클라이언트 컴퓨터가 관리 지점과 통신할 수 없더라도 Windows 컴퓨터의 클라이언트 통신 오류를 사이트에 전송하려 합니다.  

- 대체 상태 지점에서 전송되는 데이터를 표시하는 Configuration Manager 클라이언트 배포 보고서를 사용하려고 합니다.  

- 이 사이트 시스템 역할을 위한 전용 서버가 있고 해당 서버를 공격으로부터 보호할 추가적인 보안 수단이 있습니다.  

- 대체 상태 지점의 사용으로 인한 이점이 인증되지 않은 연결이나 HTTP 트래픽을 통한 일반 텍스트 전송과 관련된 보안 위협을 보충하고도 남습니다.  

인증되지 않은 연결 및 일반 텍스트 전송을 사용하여 웹 사이트를 실행하는 데 따른 보안 위험이 클라이언트 통신 문제를 식별할 수 있다는 이점보다 크다면 대체 상태 지점을 설치하지 마세요.  

## <a name="reporting-services-point"></a>보고 서비스 지점

Configuration Manager는 Configuration Manager 콘솔에서 클라이언트 설치, 할당 및 관리를 모니터링할 수 있는 많은 보고서를 제공합니다. 일부 클라이언트 배포 보고서는 클라이언트가 대체 상태 지점에 할당되어 있어야 사용할 수 있습니다.  

이 보고서는 클라이언트를 배포하는 데 필요하지 않습니다. Configuration Manager 콘솔에서 일부 배포 정보를 확인하거나 클라이언트 로그 파일을 사용하여 자세한 정보를 확인할 수 있습니다. 하지만 클라이언트 보고서는 클라이언트 배포를 모니터링하고 문제를 해결하는 데 유용한 정보를 제공합니다.  

## <a name="enrollment-point-and-enrollment-proxy-point"></a>등록 지점 및 등록 프록시 지점

Configuration Manager를 사용하려면 모바일 디바이스를 등록하고 Mac 컴퓨터용 인증서를 등록할 등록 지점 및 등록 프록시 지점이 필요합니다. 다음 상황에서는 이러한 사이트 시스템 역할이 필요하지 않습니다.

- Exchange Server 커넥터를 사용하여 모바일 디바이스를 관리하려는 경우
- 모바일 디바이스 레거시 클라이언트(예: Windows CE용)를 설치하는 경우
- Configuration Manager와 별개로 Mac 컴퓨터에서 클라이언트 인증서를 요청하고 설치하는 경우

## <a name="application-catalog"></a>애플리케이션 카탈로그

> [!Important]  
> 애플리케이션 카탈로그의 Silverlight 사용자 환경은 현재 분기 버전 1806부터 지원되지 않습니다. 버전 1906부터 업데이트된 클라이언트는 사용자가 이용할 수 있는 애플리케이션 배포에 관리 지점을 자동으로 사용하게 됩니다. 새 애플리케이션 카탈로그 역할도 설치할 수 없습니다. 버전 1910에서 애플리케이션 카탈로그 역할에 대한 지원이 종료됩니다.  
>
> 자세한 내용은 다음 아티클을 참조하세요.
>
> - [소프트웨어 센터 구성](/sccm/apps/plan-design/plan-for-software-center#bkmk_userex)
> - [제거되는 기능과 사용되지 않는 기능](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures)  

## <a name="cloud-management-gateway-connector-point"></a>클라우드 관리 게이트웨이 커넥터 지점

[인터넷에서 클라이언트를 관리](/sccm/core/clients/manage/manage-clients-internet)하도록 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/setup-cloud-management-gateway)를 설정하는 경우에는 클라우드 관리 게이트웨이 커넥터 지점이 필요합니다.
