---
title: 사이트 구성 요소
titleSuffix: Configuration Manager
description: 사이트 시스템 역할 및 사이트 상태 보고의 동작을 수정하기 위해 사이트 구성 요소를 구성하는 방법을 알아봅니다.
ms.date: 10/26/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5fccbbeb-0faa-4943-83c2-e67db62d392d
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 932d0aa50b02f422ca335c60cac0a9db5357e1d0
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75798427"
---
# <a name="site-components-for-configuration-manager"></a>Configuration Manager를 위한 사이트 구성 요소

*적용 대상: Configuration Manager(현재 분기)*

각 Configuration Manager 사이트에서 사이트 시스템 역할의 동작 및 사이트 상태 보고를 수정하도록 사이트 구성 요소를 구성할 수 있습니다. 사이트 구성 요소 구성은 사이트와 해당 사이트의 해당하는 각 사이트 시스템 역할 인스턴스에 적용됩니다.  

Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 사이트를 선택합니다. 리본 메뉴의 **설정** 그룹에서 **사이트 구성 요소 구성**을 선택합니다. 다음 옵션 중 하나를 선택합니다.

- [소프트웨어 배포](#software-distribution)  
- [소프트웨어 업데이트 지점](#software-update-point) 
- [운영 체제 배포](#operating-system-deployment)
- [관리 지점](#management-point)  
- [상태 보고](#status-reporting)  
- [이메일 알림](#email-notification)
- [컬렉션 멤버 자격 평가](#bkmk_colleval)


## <a name="about-site-components"></a>사이트 구성 요소 정보  

 다양한 사이트 구성 요소에 대한 대부분의 옵션은 Configuration Manager 콘솔에 표시되는 상태를 보면 해당 용도를 파악할 수 있습니다. 그러나 다음 세부 정보를 통해 보다 복잡한 몇 가지 구성을 설명하거나 추가 콘텐츠로 이동할 수 있습니다.  

> [!Note]  
> 중앙 관리 사이트, 기본 사이트 또는 보조 사이트 중 무엇을 선택하느냐에 따라 일부 구성 요소에 사용 가능한 옵션이 달라집니다. 일부 구성 요소는 특정 유형의 사이트에 전혀 사용할 수 없습니다.  



### <a name="software-distribution"></a>소프트웨어 배포  

#### <a name="content-distribution-settings"></a>콘텐츠 배포 설정
**일반** 탭에서 사이트 서버가 콘텐츠를 배포 지점으로 전송하는 방법을 수정하는 설정을 지정합니다. 동시 배포 설정에 사용하는 값을 더 크게 지정하면 콘텐츠 배포에서 네트워크 대역폭을 더 많이 사용할 수 있습니다.  

#### <a name="pull-distribution-point"></a>풀(pull) 배포 지점
자세한 내용은 [풀(pull) 배포 지점 사용](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)을 참조하세요.

#### <a name="network-access-account"></a>네트워크 액세스 계정
자세한 내용은 [네트워크 액세스 계정](/sccm/core/plan-design/hierarchy/accounts#network-access-account)을 참조하세요.  


### <a name="software-update-point"></a>소프트웨어 업데이트 지점  

자세한 내용은 [소프트웨어 업데이트 지점 설치](/sccm/sum/get-started/install-a-software-update-point)를 참조하세요.  


### <a name="operating-system-deployment"></a>운영 체제 배포

자세한 내용은 [오프라인 OS 이미지 서비스용 드라이브 지정](/sccm/osd/get-started/manage-operating-system-images#bkmk_servicing-drive)을 참조하세요.


### <a name="management-point"></a>관리 지점  

**일반** 탭에서 해당 관리 지점에 대한 정보를 Active Directory Domain Services에 게시하도록 사이트를 설정합니다.  

Configuration Manager 클라이언트는 관리 지점을 사용하여 서비스를 찾고 경계 그룹 멤버 자격 및 PKI 인증서 선택 옵션과 같은 사이트 정보를 검색할 뿐 아니라 소프트웨어를 다운로드할 배포 지점과 사이트의 기타 관리 지점도 검색합니다. 또한 관리 지점은 클라이언트가 사이트 할당을 완료하고, 클라이언트 정책을 다운로드하고, 클라이언트 정보를 업로드하는 데 도움이 됩니다.  

클라이언트가 관리 지점을 찾는 가장 안전한 방법은 Active Directory Domain Services에 게시하는 것입니다. 이 서비스 위치 방법을 사용하려면 다음 사항을 충족해야 합니다.

- Configuration Manager의 스키마를 확장합니다.
- 사이트 서버가 이 컨테이너에 게시할 수 있는 적절한 보안 권한이 있는 **시스템 관리** 컨테이너가 있습니다.
- Configuration Manager 사이트가 Active Directory Domain Services에 게시하도록 설정되었습니다.
- 클라이언트가 사이트 서버의 포리스트와 동일한 Active Directory에 속해 있습니다.  

인트라넷의 클라이언트가 Active Directory Domain Services를 사용하여 관리 지점을 찾을 수 없는 경우 [DNS 게시](/sccm/core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services#bkmk_dns)를 사용합니다.  

서비스 위치에 대한 일반적인 내용은 [클라이언트가 사이트 리소스 및 서비스를 찾는 방법 이해](/sccm/core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services)를 참조하세요.  


#### <a name="publish-selected-intranet-management-points-in-dns"></a>DNS에 선택한 인트라넷 관리 지점 게시
인트라넷의 클라이언트가 Active Directory Domain Services에서 관리 지점을 찾을 수 없는 경우 이 옵션을 지정합니다. DNS SRV RR(서비스 위치 리소스 레코드)을 사용하여 할당된 사이트에서 관리 지점을 찾을 수 있는 경우 이 옵션을 지정합니다.  

Configuration Manager에서 인트라넷 관리 지점을 DNS에 게시하려면 다음 모든 조건을 충족해야 합니다.  

-   DNS 서버의 BIND 버전은 8.1.2 이상이어야 합니다.  

-   DNS 서버에 자동 업데이트가 설정되어 있고 DNS 서버가 서비스 위치 리소스 레코드를 지원해야 합니다.  

-   Configuration Manager에서 관리 지점에 지정한 FQDN(정규화된 도메인 이름)에 DNS의 호스트 항목(A 또는 AAA 레코드)이 있어야 합니다.  

> [!WARNING]  
>  클라이언트가 DNS에 게시된 관리 지점을 찾으려면 자동 사이트 할당을 사용하는 대신 클라이언트를 특정 사이트에 할당해야 하며, 이러한 클라이언트가 해당 관리 지점의 도메인 접미사가 있는 사이트 코드를 사용하도록 설정합니다. 자세한 내용은 [관리 지점 찾기](/sccm/core/clients/deploy/assign-clients-to-a-site#locating-management-points)를 참조하세요.  

Configuration Manager 클라이언트가 Active Directory Domain Services 또는 DNS를 사용하여 인트라넷에서 관리 지점을 찾을 수 없는 경우 [WINS](/sccm/core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services#bkmk_wins)를 사용합니다. 사이트에 설치된 첫 번째 관리 지점은 인트라넷에서 HTTP 클라이언트 연결을 허용하도록 설정된 경우 WINS에 자동으로 게시됩니다.  


### <a name="status-reporting"></a>상태 보고  

이러한 설정은 사이트와 클라이언트의 상태 보고서에 포함되는 세부 정보 수준을 직접 설정합니다.  


### <a name="email-notification"></a>메일 알림  

Configuration Manager에서 경고를 위한 메일 알림을 보내도록 설정하려면 계정 및 메일 서버 세부 정보를 지정합니다.  

자세한 내용은 [경고 및 상태 시스템 사용](/sccm/core/servers/manage/use-alerts-and-the-status-system)을 참조하세요.


### <a name="bkmk_colleval"></a> 컬렉션 멤버 자격 평가  

이 구성 요소를 사용하여 컬렉션 멤버 자격의 증가분을 평가할 빈도를 설정합니다. 증가분 평가는 컬렉션 멤버 자격에서 변경되거나 새로운 리소스만 업데이트합니다.  

자세한 내용은 [컬렉션에 대한 모범 사례](/sccm/core/clients/manage/collections/best-practices-for-collections)를 참조하세요.



##  <a name="BKMK_ServiceMgr"></a> Configuration Manager Service Manager를 사용하여 사이트 구성 요소 관리  

Configuration Manager Service Manager를 사용하여 Configuration Manager 서비스를 제어하고 Configuration Manager 서비스 또는 작업 스레드의 상태를 확인할 수 있습니다. 이러한 서비스 및 스레드를 통칭하여 Configuration Manager 구성 요소라고 합니다. Configuration Manager 구성 요소에 대한 다음 설명을 이해합니다.  

-   구성 요소는 모든 사이트 시스템에서 실행될 수 있습니다.  

-   구성 요소는 Windows에서 서비스를 관리하는 것과 동일한 방식으로 관리되므로 Configuration Manager 구성 요소를 시작, 중지, 일시 중지, 재시작 또는 쿼리할 수 있습니다.  

수행할 작업이 있을 때 Configuration Manager 서비스가 실행됩니다. 이 작업은 일반적으로 구성 파일이 구성 요소의 수신함에 기록될 때 수행됩니다. 


### <a name="use-the-configuration-manager-service-manager"></a>Configuration Manager Service Manager 사용  

1.  Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고, **시스템 상태**를 확장하고, **구성 요소 상태** 노드를 선택합니다.  

2.  리본 메뉴의 **구성 요소** 그룹에서 **시작**을 선택한 다음, **Configuration Manager Service Manager**를 선택합니다.  

3.  Configuration Manager Service Manager가 열리면 관리할 사이트에 연결합니다.  

     관리하려는 사이트가 표시되지 않으면 **사이트** 메뉴로 이동하여 **연결**을 선택합니다. 그런 다음, 올바른 사이트의 사이트 서버 이름을 입력합니다.  

4.  사이트를 확장하고 관리할 구성 요소의 위치에 따라 **구성 요소** 또는 **서버**로 이동합니다.  

5.  오른쪽 창에서 구성 요소를 하나 이상 선택합니다. 그런 다음, **구성 요소** 메뉴에서 **쿼리**를 선택하여 선택 항목의 상태를 업데이트합니다.  

6.  구성 요소의 상태가 업데이트되면 **구성 요소** 메뉴에서 4개의 동작 기반 옵션 중 하나를 사용하여 구성 요소 작업을 수정합니다. 작업을 요청한 후에는 구성 요소의 새 상태가 표시되도록 구성 요소를 쿼리해야 합니다.  

7.  구성 요소 작업 상태의 수정을 마치면 Configuration Manager Service Manager를 닫습니다.  
