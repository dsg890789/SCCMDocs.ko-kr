---
title: "검색 방법 | Microsoft 문서"
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed931751-18f2-4230-a09e-a0a329fbfa1c
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 223ebc3009b33c43818636a9e19b9b482619550b

---
# <a name="about-discovery-methods-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 검색 방법 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

각 System Center Configuration Manager 검색 방법을 통해 네트워크에서 다양한 장치를 찾거나 Active Directory에서 장치 및 사용자를 찾을 수 있습니다. 검색 방법을 효율적으로 사용하려면 사용 가능한 구성 및 제한 사항을 이해해야 합니다.  

##  <a name="a-namebkmkaboutforesta-active-directory-forest-discovery"></a><a name="bkmk_aboutForest"></a> Active Directory 포리스트 검색  
 **구성 가능 여부:** 예  

 **기본값으로 사용 가능:** 아니요  

 이 방법을 실행하는 데 사용할 수 있는 **계정**은 다음과 같습니다.  

-   **Active Directory 포리스트 검색 계정**(사용자 정의)  

-   사이트 서버의 **컴퓨터 계정**  

다른 Active Directory 검색 방법과 달리, Active Directory 포리스트 검색은 관리할 수 있는 리소스를 검색하지 않습니다. 대신 이 방법은 Active Directory에 구성된 네트워크 위치를 검색하고 이러한 위치를 계층 전체에서 사용할 경계로 전환할 수 있습니다.  

이 방법을 실행하면 로컬 Active Directory 포리스트, 각 트러스트된 포리스트 및 Configuration Manager 콘솔의 **Active Directory 포리스트** 노드에 구성하는 각 추가 포리스트를 검색합니다.  

다음 작업에 Active Directory 포리스트 검색을 사용합니다.  

-   Active Directory 사이트 및 서브넷을 검색한 다음 해당 네트워크 위치에 따라 Configuration Manager 경계를 만듭니다.  

-   Active Directory 사이트에 할당된 슈퍼넷을 식별하고 해당 슈퍼넷을 IP 주소 범위 경계로 변환합니다.  

-   포리스트에 대한 게시를 사용하도록 설정되어 있고 지정된 Active Directory 포리스트 계정에 해당 포리스트에 대한 권한이 있는 경우 포리스트의 Active Directory Domain Services에 게시  

Configuration Manager 콘솔에서 **관리** 작업 영역의 **계층 구성** 아래에 있는 다음 노드에서 Active Directory 포리스트 검색을 관리할 수 있습니다.  

-   **검색 방법**: 여기서 Active Directory 포리스트 검색이 계층의 상위 사이트에서 실행되도록 설정할 수 있습니다. 또한 간단한 일정을 지정하여 검색을 실행하고 검색되는 IP 서브넷과 Active Directory 사이트에서 자동으로 경계를 만들도록 구성할 수 있습니다. Active Directory 포리스트 검색은 자식 기본 사이트 또는 보조 사이트에서 실행할 수 없습니다.  

-   **Active Directory 포리스트**: 여기서 검색할 추가 Active Directory 포리스트를 구성하고 각 포리스트의 Active Directory 포리스트 계정으로 사용할 계정을 지정하고 각 포리스트에 대한 게시를 구성할 수 있습니다. 또한 검색 프로세스를 모니터링하고 IP 서브넷 및 Active Directory 사이트를 Configuration Manager에 경계 및 경계 그룹의 구성원으로 추가할 수 있습니다.  

계층 내 각 사이트에 대한 Active Directory 포리스트에 게시를 구성하려면 Configuration Manager 콘솔을 계층의 최상위 사이트에 연결합니다. Active Directory 사이트 **속성** 대화 상자의 **게시** 탭에는 현재 사이트 및 자식 사이트만 표시됩니다. 포리스트에 게시를 사용하도록 설정되어 있고 Configuration Manager를 위해 포리스트 스키마가 확장된 경우 Active Directory 포리스트에 게시하도록 설정된 각 사이트에 대해 다음 정보가 게시됩니다.  

-    **SMS-Site-&lt;사이트 코드>**

-   **SMS-MP-&lt;사이트 코드>-&lt;사이트 시스템 서버 이름>**  

-   **SMS-SLP-&lt;사이트 코드>-&lt;사이트 시스템 서버 이름>**  

-   **SMS-&lt;사이트 코드>-&lt;Active Directory 사이트 이름 또는 서브넷>**  

> [!NOTE]  
>  보조 사이트에서는 Active Directory에 게시하는 데 항상 보조 사이트 서버 컴퓨터 계정을 사용합니다. 보조 사이트에서 Active Directory에 게시하려면 보조 사이트 서버 컴퓨터 계정에 Active Directory 게시 권한이 있어야 합니다. 보조 사이트에서는 트러스트되지 않은 포리스트에 데이터를 게시할 수 없습니다.  

> [!CAUTION]  
>  Active Directory 포리스트에 사이트를 게시하는 옵션을 선택 취소하면 해당 사이트에 대해 이전에 게시된 모든 정보(사용 가능한 사이트 시스템 역할 포함)는 해당 포리스트의 Active Directory에서 제거됩니다.  

Active Directory 포리스트 검색 작업은 다음 로그에 기록됩니다.  

-   게시와 관련된 예외 작업을 비롯한 모든 작업은 사이트 서버의 **&lt;InstallationPath>\Logs** 폴더에 있는 **ADForestDisc.Log** 파일에 기록됩니다.  

-   Active Directory 포리스트 검색 게시 작업은 사이트 서버에 있는 **&lt;InstallationPath>\Logs** 폴더의 **hman.log** 및 **sitecomp.log**에 기록됩니다.  

이 검색 방법을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)을 참조하세요.  

##  <a name="a-namebkmkaboutgroupa-active-directory-group-discovery"></a><a name="bkmk_aboutGroup"></a> Active Directory 그룹 검색  
**구성 가능 여부:** 예  

**기본값으로 사용 가능:** 아니요  

이 방법을 실행하는 데 사용할 수 있는 **계정**은 다음과 같습니다.  

-   **Active Directory 그룹 검색 계정**(사용자 정의)  

-   사이트 서버의 **컴퓨터 계정**  

> [!TIP]  
>  이 섹션의 정보 외에 [Active Directory 그룹, 시스템 및 사용자 검색의 일반적인 기능](#bkmk_shared)을 참조하세요.  

이 방법을 사용하여 다음 사항을 식별할 AD DS(Active Directory Domain Services)를 검색합니다.  

-   로컬, 글로벌 및 유니버설 보안 그룹  

-   그룹의 멤버 자격  

-   그룹 구성원 컴퓨터와 사용자에 대한 제한된 정보. 이러한 컴퓨터와 사용자가 이전에 다른 검색 방법을 통해 검색되지 않은 경우에도 해당됩니다.  

이 검색 방법은 그룹과 그룹 구성원의 그룹 관계를 파악하는 데 사용됩니다. 기본적으로 보안 그룹만 검색됩니다. 배포 그룹의 멤버 자격도 찾으려면 Active Directory 그룹 검색 속성 대화 상자의 **옵션** 탭에서 **배포 그룹의 멤버 자격 검색** 옵션 확인란을 선택해야 합니다.  

Active Directory 그룹 검색은 Active Directory 시스템 검색 또는 Active Directory 사용자 검색을 사용하여 파악할 수 있는 확장된 Active Directory 특성은 지원하지 않습니다. 이 검색 방법은 컴퓨터와 사용자 리소스를 검색하도록 최적화되어 있지 않으므로 Active Directory 시스템 검색과 Active Directory 사용자 검색을 실행한 후에 이 검색 방법을 실행해야 합니다. 그 이유는 이 방법을 통해 그룹에 대해서는 전체 DDR이 만들어지지만 그룹 구성원인 컴퓨터와 사용자에 대해서는 제한된 DDR만 만들어지기 때문입니다.  

이 방법이 정보를 검색하는 방식을 제어하는 다음과 같은 검색 범위를 구성할 수 있습니다.  

-   **위치**: 하나 이상의 Active Directory 컨테이너를 검색하려면 위치를 사용합니다. 이 범위 옵션은 지정된 Active Directory 컨테이너의 하위 항목 포함 검색을 지원하여 지정한 컨테이너 아래에 있는 각 자식 컨테이너도 검색합니다. 이 프로세스는 자식 컨테이너가 더 이상 검색되지 않을 때까지 계속됩니다.  

-   **그룹**: 하나 이상의 특정 Active Directory 그룹을 검색하려면 그룹을 사용합니다. 기본 도메인 및 포리스트를 사용하도록 **Active Directory 도메인** 을 구성하거나, 개별 도메인 컨트롤러로 검색을 제한할 수 있습니다. 또한 검색할 그룹을 하나 이상 지정할 수 있습니다. 하나 이상의 그룹을 지정하지 않을 경우 지정된 **Active Directory 도메인** 위치에 있는 모든 그룹이 검색됩니다.  

> [!CAUTION]  
>  검색 범위를 구성하는 경우 검색할 그룹만 선택합니다. 그 이유는 Active Directory 그룹 검색이 검색 범위에서 각 그룹의 각 구성원을 검색하기 때문입니다. 대규모 그룹의 검색을 위해서는 대역폭과 Active Directory 리소스를 많이 사용해야 할 수 있습니다.  

> [!NOTE]  
>  확장된 Active Directory 특성을 기반으로 하는 컬렉션을 만들고 컴퓨터와 사용자에 대한 정확한 검색 결과를 보장할 수 있으려면 먼저 검색하려는 항목에 따라 Active Directory 시스템 검색 또는 Active Directory 사용자 검색을 실행합니다.  

Active Directory 그룹 검색 작업은 사이트 서버에 있는 **&lt;InstallationPath\>\LOGS** 폴더의 **adsgdis.log** 파일에 기록됩니다.  

이 검색 방법을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)을 참조하세요.  

##  <a name="a-namebkmkaboutsystema-active-directory-system-discovery"></a><a name="bkmk_aboutSystem"></a> Active Directory 시스템 검색  
**구성 가능 여부:** 예  

**기본값으로 사용 가능:** 아니요  

이 방법을 실행하는 데 사용할 수 있는 **계정**은 다음과 같습니다.  

-   **Active Directory 시스템 검색 계정**(사용자 정의)  

-   사이트 서버의 **컴퓨터 계정**  

> [!TIP]  
>  이 섹션의 정보 외에 [Active Directory 그룹, 시스템 및 사용자 검색의 일반적인 기능](#bkmk_shared)을 참조하세요.  

이 검색 방법을 통해 컬렉션과 쿼리를 만드는 데 사용할 수 있는 컴퓨터 리소스의 지정된 AD DS(Active Directory Domain Services) 위치를 검색할 수 있습니다. 또한 클라이언트 강제 설치를 사용하여 검색된 장치에 Configuration Manager 클라이언트를 설치할 수도 있습니다.  

기본적으로 이 방법은 다음을 포함하여 컴퓨터에 대한 기본 정보를 검색합니다.  

-   컴퓨터 이름  

-   운영 체제 및 버전  

-   Active Directory 컨테이너 이름  

-   IP 주소  

-   Active Directory 사이트  

-   마지막 로그온 타임스탬프  

컴퓨터에 대한 DDR(검색 데이터 레코드)을 성공적으로 만들려면 Active Directory 시스템 검색에서 컴퓨터 계정을 식별한 다음 컴퓨터 이름을 IP 주소로 확인할 수 있어야 합니다.  

Active Directory 시스템 검색에서 반환된 기본 개체 특성의 전체 목록을 보고 **Active Directory 시스템 검색 속성** 대화 상자의 **Active Directory 특성** 탭에서 추가(확장) 특성을 검색할 방법을 구성할 수 있습니다.  

Active Directory 시스템 검색 작업은 사이트 서버에 있는 **&lt;InstallationPath\>\LOGS** 폴더의 **adsysdis.log** 파일에 기록됩니다.  

이 검색 방법을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)을 참조하세요.  

##  <a name="a-namebkmkaboutusera-active-directory-user-discovery"></a><a name="bkmk_aboutUser"></a> Active Directory 사용자 검색  
**구성 가능 여부:** 예  

**기본값으로 사용 가능:** 아니요  

이 방법을 실행하는 데 사용할 수 있는 **계정**은 다음과 같습니다.  

-   **Active Directory 사용자 검색 계정**(사용자 지정)  

-   사이트 서버의 **컴퓨터 계정**  

> [!TIP]  
>  이 섹션의 정보 외에 [Active Directory 그룹, 시스템 및 사용자 검색의 일반적인 기능](#bkmk_shared)을 참조하세요.  

이 검색 방법을 통해 AD DS(Active Directory Domain Services)를 검색하여 사용자 계정 및 관련 특성을 파악할 수 있습니다.  기본적으로 이 방법은 다음을 포함하여 사용자 계정에 대한 기본 정보를 검색합니다.  

-   사용자 이름  

-   고유한 사용자 이름(도메인 이름 포함)  

-   도메인  

-   Active Directory 컨테이너 이름  

Active Directory 사용자 검색에서 반환된 전체 기본 개체 특성 목록을 보고 **Active Directory 사용자 검색 속성** 대화 상자의 **Active Directory 특성** 탭에서 추가(확장) 특성을 검색할 방법을 구성할 수 있습니다.  

Active Directory 사용자 검색 작업은 사이트 서버에 있는 **&lt;InstallationPath\>\LOGS** 폴더의 **adusrdis.log** 파일에 기록됩니다.  

이 검색 방법을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)을 참조하세요.  

##  <a name="a-namebkmkaboutheartbeata-heartbeat-discovery"></a><a name="bkmk_aboutHeartbeat"></a> 하트비트 검색  
**구성 가능 여부:** 예  

**기본값으로 사용 가능:** 예  

이 방법을 실행하는 데 사용할 수 있는 **계정**은 다음과 같습니다.  

-   사이트 서버의 **컴퓨터 계정**  

하트비트 검색은 기타 Configuration Manager 검색 방법과는 다릅니다. 기본적으로 설정되어 있으며 사이트 서버가 아닌 각 컴퓨터 클라이언트에서 실행되어 DDR(검색 데이터 기록)을 만듭니다. 모바일 장치 클라이언트의 경우, 이 DDR은 모바일 장치 클라이언트에서 사용되는 관리 지점에 의해 만들어집니다.  Configuration Manager 클라이언트의 데이터베이스 레코드를 유지하려면 하트비트 검색을 사용하도록 설정해 둡니다.  데이터베이스 레코드 유지 관리 외에 이 방법은 강제로 컴퓨터를 새 리소스 레코드로 검색되도록 하거나 데이터베이스에서 삭제된 컴퓨터의 데이터베이스 레코드를 다시 채울 수 있습니다.  

하트비트 검색은 계층의 모든 클라이언트에 대해 구성된 일정에 따라 실행되거나, 수동으로 호출하는 경우 클라이언트 Configuration Manager 프로그램의 **작업** 탭에서 **검색 데이터 컬렉션 주기**를 실행하는 방식으로 특정 클라이언트에 대해 실행됩니다. 하트비트 검색의 기본 일정은 매 7일로 설정되어 있습니다. 하트비트 검색 간격을 변경할 경우, 사이트 데이터베이스에서 비활성 클라이언트 레코드를 삭제하는 **오래된 검색 데이터 삭제**사이트 유지 관리 작업보다 하트비트 검색이 더 자주 실행되도록 설정해야 합니다. **오래된 검색 데이터 삭제** 작업은 기본 사이트에 대해서만 구성할 수 있습니다.  

하트비트 검색이 실행되면 클라이언트의 현재 정보를 포함하는 DDR이 만들어집니다. 그런 다음 클라이언트는 기본 사이트에서 처리될 수 있도록 이 작은 파일(약 1KB의 크기)을 관리 지점에 복사합니다.  파일에는 다음 정보가 포함됩니다.  

-   네트워크 위치  

-   NetBIOS 이름  

-   클라이언트 에이전트의 버전  

-   작업 상태 세부 정보  

하트비트 검색은 클라이언트 설치 상태에 대한 세부 정보를 제공하는 유일한 검색 방법입니다. **예**와 일치하는 값을 설정하도록 시스템 리소스 클라이언트 특성을 업데이트하여 수행합니다.  

> [!NOTE]  
>  하트비트 검색이 사용하지 않도록 설정되더라도 DDR은 활성 모바일 장치 클라이언트에 대해 계속 만들어지고 제출됩니다. 따라서 **오래된 검색 데이터 삭제** 작업은 활성 모바일 장치에 영향을 주지 않습니다. **오래된 검색 데이터 삭제** 작업을 통해 모바일 장치에 대한 데이터베이스 레코드가 삭제되면 동시에 장치 인증서는 해지되고 모바일 장치는 관리 지점에 연결하지 못하도록 차단되기 때문입니다.  

하트비트 검색 작업은 다음 위치에 기록됩니다.  

-   컴퓨터 클라이언트의 경우, 하트비트 검색 작업은 클라이언트의 **InventoryAgent.log** 폴더에 있는 *%Windir%\CCM\Logs*에 기록됩니다.  

-   모바일 장치 클라이언트의 경우, 하트비트 검색 작업은 모바일 장치 클라이언트에서 사용하는 관리 지점의 **DMPRP.log** 폴더에 있는 *%Program Files%\CCM\Logs* 에 기록됩니다.  

이 검색 방법을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)을 참조하세요.  

##  <a name="a-namebkmkaboutnetworka-network-discovery"></a><a name="bkmk_aboutNetwork"></a> 네트워크 검색  
**구성 가능 여부:** 예  

**기본값으로 사용 가능:** 아니요  

이 방법을 실행하는 데 사용할 수 있는 **계정**은 다음과 같습니다.  

-   사이트 서버의 **컴퓨터 계정**  

이 방법을 사용하여 네트워크의 토폴로지를 검색하고 네트워크에서 IP 주소가 있는 장치를 검색합니다. 네트워크 검색은 Microsoft DHCP를 실행하는 서버, 라우터의 ARP(Address Resolution Protocol) 캐시, SNMP 사용 장치 및 Active Directory 도메인 등을 쿼리하여 네트워크에서 IP 사용 리소스를 검색합니다.  

네트워크 검색을 사용하려면 실행할 검색의 **수준**을 지정해야 합니다. 또한 네트워크 검색에서 네트워크 세그먼트 또는 장치를 쿼리할 수 있도록 지원하는 검색 메커니즘을 하나 이상 구성해야 합니다. 네트워크상의 검색 작업을 제어할 수 있는 설정을 구성할 수도 있습니다. 끝으로, 네트워크 검색이 실행되는 일정을 하나 이상 정의합니다.  

이 방법의 경우 네트워크 검색에서 리소스를 성공적으로 검색하려면 리소스의 IP 주소 및 서브넷 마스크를 식별해야 합니다. 다음 방법을 사용하여 개체의 서브넷 마스크를 식별합니다.  

-   **라우터의 ARP 캐시:** 네트워크 검색이 라우터의 ARP 캐시를 쿼리하여 서브넷 정보를 검색합니다. 일반적으로 라우터 ARP 캐시의 데이터는 유지 기간이 짧습니다. 따라서 네트워크 검색이 ARP 캐시를 검색할 때 ARP 캐시에 요청한 개체에 대한 정보가 더 이상 들어 있지 않을 수 있습니다.  

-   **DHCP:** 네트워크 검색이 지정된 각 DHCP 서버를 쿼리하여 DHCP 서버가 임대를 제공한 장치를 검색합니다. 네트워크 검색은 Microsoft DHCP를 실행하는 DHCP 서버만 지원합니다.  

-   **SNMP 장치:** 네트워크 검색이 SNMP 장치를 직접 쿼리할 수 있습니다. 네트워크 검색이 장치를 쿼리하려면 장치에 로컬 SNMP 에이전트가 설치되어 있어야 합니다. 또한 네트워크 검색이 SNMP 에이전트에 사용되는 커뮤니티 이름을 사용하도록 구성해야 합니다.  

검색에서 IP 주소 지정 가능 개체를 식별하고 개체 서브넷 마스크를 확인할 수 있는 경우 해당 개체에 대한 DDR이 만들어집니다. 다양한 유형의 장치가 네트워크에 연결될 수 있으므로 Configuration Manager 클라이언트 소프트웨어를 지원하지 못하는 리소스가 네트워크 검색을 통해 검색될 수도 있습니다. 검색 가능하지만 관리되지 않는 장치의 예로는 프린터와 라우터가 있습니다.  

네트워크 검색에서 생성하는 검색 레코드의 일부로 몇 가지 특성이 반환될 수 있으며 여기에는 다음이 포함됩니다.  

-   NetBIOS 이름  

-   IP 주소  

-   리소스 도메인  

-   시스템 역할  

-   SNMP 커뮤니티 이름  

-   MAC 주소  

네트워크 검색 작업은 검색을 실행하는 사이트 서버에 있는 **&lt;InstallationPath\>\Logs**의 **Netdisc.log**에 기록됩니다.  

 이 검색 방법을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 검색 방법 구성](../../../../core/servers/deploy/configure/configure-discovery-methods.md)을 참조하세요.  

> [!NOTE]  
>  복잡한 네트워크와 낮은 대역폭으로 구성된 연결로 인해 네트워크 검색의 실행 속도가 느려지고 상당한 네트워크 트래픽이 생성될 수도 있습니다. 네트워크 검색은 검색하려는 리소스를 다른 검색 방법으로는 찾을 수 없는 경우에만 실행하는 것이 좋습니다. 예를 들어 작업 그룹 컴퓨터를 검색해야 할 경우 네트워크 검색을 사용하십시오. 작업 그룹 컴퓨터는 다른 검색 방법으로는 검색할 수 없습니다.  

###  <a name="a-namebkmknetdisclevelsa-levels-of-network-discovery"></a><a name="BKMK_NetDiscLevels"></a> 네트워크 검색 수준  
네트워크 검색을 구성할 경우 세 가지 검색 수준 중 하나를 지정해야 합니다.  

|검색 수준|세부 정보|  
|------------------------|-------------|  
|토폴로지|이 수준에서는 라우터와 서브넷을 검색하지만 개체의 서브넷 마스크는 식별하지 않습니다.|  
|토폴로지 및 클라이언트|이 수준에서는 토폴로지 외에 컴퓨터와 같은 잠재적 클라이언트와 프린트 및 라우터와 같은 리소스를 검색합니다. 이 검색 수준에서 개체를 찾을 경우 해당 개체의 서브넷 마스크를 확인하려고 시도합니다.|  
|토폴로지, 클라이언트 및 클라이언트 운영 체제|이 수준에서는 토폴로지 및 잠재적 클라이언트 외에 컴퓨터 운영 체제 이름 및 버전을 검색합니다. 이 수준에서는 Windows 브라우저와 Windows 네트워킹 호출을 사용합니다.|  

 네트워크 검색은 수준이 올라감에 따라 작업 및 네트워크 대역폭 사용량도 증가합니다. 네트워크 검색의 모든 기능을 사용하도록 설정하기 전에 예상되는 네트워크 트래픽을 고려하십시오.  

 예를 들어 네트워크 검색을 처음 사용할 때 토폴로지 수준만으로 시작하여 네트워크 인프라를 확인할 수도 있습니다. 그런 다음 개체 및 해당 장치 운영 체제를 검색하도록 네트워크 검색을 다시 구성하면 됩니다. 또한 네트워크 검색을 특정 네트워크 세그먼트 범위로 제한하는 설정을 구성할 수 있습니다. 이를 통해 원하는 네트워크 위치에서 개체를 검색할 수 있으며 불필요한 네트워크 트래픽을 방지하고 경계측 라우터나 네트워크 외부를 대상으로 한 개체 검색을 차단할 수 있습니다.  

###  <a name="a-namebkmknetdiscoptionsa-network-discovery-options"></a><a name="BKMK_NetDiscOptions"></a> 네트워크 검색 옵션  
네트워크 검색에서 IP 주소 지정 가능 장치를 검색하도록 설정하려면 장치 쿼리 방법을 지정하는 다음 옵션을 하나 이상 구성해야 합니다.  

> [!NOTE]  
>  네트워크 검색은 검색을 실행하는 사이트 서버의 컴퓨터 계정의 컨텍스트에서 실행됩니다. 이 컴퓨터 계정에 트러스트되지 않은 도메인에 대한 권한이 없는 경우 도메인 및 DHCP 서버 구성 모두에서 리소스를 검색하지 못할 수도 있습니다.  

**DHCP:**  

네트워크 검색에서 쿼리할 각 DHCP 서버를 지정합니다. 네트워크 검색은 Microsoft DHCP를 실행하는 DHCP 서버만 지원합니다.  

-   네트워크 검색은 DHCP 서버의 데이터베이스에 대한 원격 프로시저 호출을 사용하여 정보를 검색합니다.  

-   네트워크 검색은 32비트 및 64비트 DHCP 서버 모두에서 각 서버에 등록된 장치 목록을 쿼리할 수 있습니다.  

-   네트워크 검색에서 DHCP 서버를 성공적으로 쿼리하려면 검색을 실행하는 서버의 컴퓨터 계정은 DHCP 서버에서 DHCP 사용자 그룹의 구성원이어야 합니다. 예를 들어 다음 조건 중 하나에 해당하는 경우 이러한 액세스 수준을 볼 수 있습니다.  

    -   지정된 DHCP 서버가 검색을 실행하는 서버의 DHCP 서버입니다.  

    -   검색을 실행하는 컴퓨터와 DHCP 서버가 동일한 도메인 안에 있습니다.  

    -   검색을 실행하는 컴퓨터와 DHCP 서버 간에 양방향 트러스트가 존재합니다.  

    -   사이트 서버가 DHCP 사용자 그룹의 구성원입니다.  

-   네트워크 검색에서 DHCP 서버를 열거할 경우 항상 정적 IP 주소가 검색되는 것은 아닙니다. 네트워크 검색은 DHCP 서버의 IP 주소 제외 범위에 속하는 IP 주소와 수동 할당으로 예약된 IP 주소는 검색하지 않습니다.  

**도메인:**  

네트워크 검색에서 쿼리할 각 도메인을 지정합니다.  

-   검색을 실행하는 사이트 서버의 컴퓨터 계정에는 각 지정된 도메인에서 도메인 컨트롤러를 읽을 수 있는 권한이 있어야 합니다.  

-   로컬 도메인에서 컴퓨터를 검색하려면 네트워크 검색을 실행하는 사이트 서버와 같은 서브넷에 위치한 하나 이상의 컴퓨터에서 컴퓨터 브라우저 서비스를 사용하도록 설정해야 합니다.  

-   네트워크 검색은 네트워크를 찾아볼 때 사이트 서버에서 볼 수 있는 모든 컴퓨터를 검색할 수 있습니다.  

-   네트워크 검색은 IP 주소를 검색한 다음 검색되는 각 장치에 대해 ICMP(Internet Control Message Protocol) 에코 요청을 사용하여 ping을 실행합니다. **ping** 명령을 사용하면 현재 활성 상태인 컴퓨터를 확인할 수 있습니다.  

**SNMP 장치:**  

네트워크 검색에서 쿼리할 각 SNMP 장치를 지정합니다.  

-   네트워크 검색은 쿼리에 응답하는 모든 SNMP 장치에서 ipNetToMediaTable 값을 검색합니다. 이 값에서는 클라이언트 컴퓨터 또는 기타 리소스(예: 프린터, 라우터, 기타 IP 주소 지정 가능 장치)에 해당하는 IP 주소의 배열을 반환합니다.  

-   장치를 쿼리하려면 해당 장치의 IP 주소 또는 NetBIOS 이름을 지정해야 합니다.  

-   네트워크 검색에서 장치의 커뮤니티 이름을 사용하도록 구성해야 하며, 그렇지 않으면 장치는 SNMP 기반 쿼리를 거부합니다.  

###  <a name="a-namebkmklimitnetdisca-limiting-network-discovery"></a><a name="BKMK_LimitNetDisc"></a> 네트워크 검색 제한  
네트워크 검색에서 네트워크 경계측에 있는 SNMP 장치를 쿼리할 경우 서브넷 관련 정보 및 현재 네트워크 외부에 있는 SNMP 장치에 관한 정보를 확인할 수 있습니다. 다음 정보를 사용하여 검색에서 통신할 수 있는 SNMP 장치를 구성하고 쿼리할 네트워크 세그먼트를 지정하면 네트워크 검색을 제한할 수 있습니다.  

**서브넷:**  

네트워크 검색이 SNMP 및 DHCP 옵션을 사용할 때 쿼리하는 서브넷을 구성합니다. 사용하도록 설정된 서브넷만 이러한 두 옵션을 통해 검색됩니다.  

예를 들어 DHCP 요청은 전체 네트워크 위치에서 장치를 반환할 수 있습니다. 특정 서브넷의 장치만 검색하려는 경우 **네트워크 검색 속성** 대화 상자의 **서브넷** 탭에서 해당 서브넷을 지정하고 사용하도록 설정합니다. 서브넷을 지정하고 사용하도록 설정하면 이후의 DHCP 및 SNMP 검색 작업이 이러한 서브넷으로 제한됩니다.  

> [!NOTE]  
>  서브넷 구성은 도메인 검색 옵션을 통해 검색되는 개체를 제한하지 않습니다.  

**SNMP 커뮤니티 이름:**  

네트워크 검색이 SNMP 장치를 성공적으로 쿼리할 수 있도록 하려면 해당 장치의 커뮤니티 이름을 사용하여 네트워크 검색을 구성합니다. 네트워크 검색이 SNMP 장치의 커뮤니티 이름을 사용하여 구성되지 않은 경우 장치가 쿼리를 거부합니다.  

**최대 홉 수:**  

최대 라우터 홉 수를 구성하면 네트워크 검색이 SNMP를 사용하여 쿼리할 수 있는 네트워크 세그먼트와 라우터 수가 제한됩니다.  

-   구성하는 홉 수에 따라 네트워크 검색이 쿼리할 수 있는 추가 장치와 네트워크 세그먼트 수가 제한됩니다.  

 예를 들어 **0** 개의 라우터 홉을 지정하고 토폴로지만 검색하면 원본 서버가 있는 서브넷이 검색되고 해당 서브넷에 있는 라우터가 포함됩니다.  

다음 다이어그램에서는 0개의 라우터 홉을 지정하고 서버 1에서 토폴로지만 포함한 네트워크 검색을 실행할 때 서브넷 D와 라우터 1이 검색되는 것을 보여 줍니다.  

 ![0개의 라우터 점프가 있는 검색 이미지](media/Disc-0.gif)  

 다음 다이어그램에서는 0개의 라우터 홉을 지정하고 서버 1에서 토폴로지와 클라이언트를 포함한 네트워크 검색을 실행할 때 서브넷 D와 라우터 1 및 서브넷 D에 있을 수 있는 모든 클라이언트가 검색되는 것을 보여 줍니다.  

 ![1개의 라우터 점프가 있는 검색 이미지](media/Disc-1.gif)  

 다음 네트워크를 살펴보면 라우터 홉이 추가됨에 따라 검색되는 네트워크 리소스 양이 어떻게 늘어나는지 잘 알 수 있습니다.  

 ![2개의 라우터 점프가 있는 검색 이미지](media/Disc-2.gif)  

 1개의 라우터 홉을 지정하고 서버 1에서 토폴로지만 포함한 네트워크 검색을 실행하면 다음이 검색됩니다.  

-   라우터 1 및 서브넷 10.1.10.0(0개의 홉 지정 시 검색됨)  

-   서브넷 10.1.20.0 및 10.1.30.0, 서브넷 A 및 라우터 2(첫 번째 홉에서 검색됨)  

> [!WARNING]  
>  라우터 홉 수가 하나씩 늘어날 때마다 검색될 수 있는 리소스 수가 상당히 증가하며 네트워크 검색이 사용하는 네트워크 대역폭이 크게 증가할 수 있습니다.  

##  <a name="a-namebkmkaboutservera-server-discovery"></a><a name="bkmk_aboutServer"></a> 서버 검색  
**구성 가능 여부:** 아니요  

사용자 구성 가능 검색 방법 이외에도 Configuration Manager에서는 **서버 검색**(SMS_WINNT_SERVER_DISCOVERY_AGENT)이라는 프로세스를 사용합니다. 이 검색 방법은 관리 지점으로 구성된 컴퓨터를 비롯한 사이트 시스템인 컴퓨터에 대한 리소스 레코드를 만듭니다.  

##  <a name="a-namebkmkshareda-common-features-of-active-directory-group-system-and-user-discovery"></a><a name="bkmk_shared"></a> Active Directory 그룹, 시스템 및 사용자 검색의 일반적인 기능  
이 섹션에서는 다음 검색 방법의 일반적인 기능에 대한 정보를 제공합니다.  

-   Active Directory 그룹 검색  

-   Active Directory 시스템 검색  

-   Active Directory 사용자 검색  

> [!NOTE]  
>  이 섹션의 정보는 Active Directory 포리스트 검색에 적용되지 않습니다.  

이러한 세 가지 검색 방법은 구성과 작업이 유사하며 Active Directory Domain Services에 저장된 리소스의 컴퓨터, 사용자 및 그룹 멤버 자격 정보를 검색할 수 있습니다. 검색 프로세스는 검색 에이전트로 관리되며, 검색 에이전트는 검색을 실행하도록 구성된 각 사이트의 사이트 서버에서 실행됩니다. 이러한 로컬 포리스트 또는 원격 포리스트의 위치 인스턴스로 하나 이상의 Active Directory 위치를 검색하도록 각 검색 방법을 구성할 수 있습니다.  

검색을 통해 리소스에 대한 트러스트되지 않은 포리스트가 검색될 경우, 검색 에이전트가 성공적으로 실행되려면 다음을 확인할 수 있어야 합니다.  

-   Active Directory 시스템 검색을 통해 컴퓨터 리소스를 검색하려면 검색 에이전트가 리소스의 FQDN을 확인할 수 있어야 합니다. FQDN을 확인할 수 없는 경우 검색 에이전트는 NetBIOS 이름으로 리소스를 확인합니다.  

-   Active Directory 사용자 검색 또는 Active Directory 그룹 검색을 통해 사용자 또는 그룹 리소스를 검색하려면 검색 에이전트가 Active Directory 위치를 위해 지정한 도메인 컨트롤러 이름의 FQDN을 확인할 수 있어야 합니다.  

지정한 각 위치에 대해 위치 Active Directory 자식 컨테이너의 회귀적 검색을 사용하도록 설정하는 것 같은 개별 검색 옵션을 구성할 수 있습니다. 또한 해당 위치를 검색할 때 사용할 고유한 계정을 구성할 수 있어야 합니다. 이렇게 하면 단일 계정이 모든 위치에 대한 권한을 갖도록 구성할 필요 없이 한 사이트에서 여러 포리스트에 걸친 여러 Active Directory 위치를 검색하도록 검색 방법을 유연하게 구성할 수 있습니다.  

이러한 세 검색 방법이 각각 특정 사이트에서 실행되는 경우 해당 사이트의 Configuration Manager 사이트 서버는 지정된 Active Directory 포리스트에서 가장 가까운 도메인 컨트롤러에 연결하여 Active Directory 리소스를 찾습니다. 도메인과 포리스트는 지원되는 모든 Active Directory 모드에 있을 수 있으며, 각 위치 인스턴스에 할당하는 계정은 지정된 Active Directory 위치에 대한 **읽기** 권한을 가져야 합니다. 검색은 지정된 위치에서 개체를 찾은 다음 이러한 개체에 대한 정보를 수집합니다. 리소스에 대한 충분한 정보가 파악되면 DDR(검색 데이터 기록)이 만들어집니다. 필요한 정보는 사용되는 검색 방법에 따라 달라집니다.  

서로 다른 Configuration Manager 사이트에서 동일한 검색 방법을 실행하여 로컬 Active Directory 서버 쿼리를 활용하도록 구성하는 경우 각 사이트에 고유한 검색 옵션 집합을 구성할 수 있습니다. 계층의 각 사이트에서 검색 데이터가 공유되므로 각 리소스를 한 번에 효율적으로 검색하려면 이러한 구성 간에 겹치지 않도록 해야 합니다. 소규모 환경의 경우 관리 부담과 여러 검색 작업으로 동일한 리소스를 재검색할 가능성을 줄이도록 계층의 한 사이트에서만 각 검색 방법을 실행하는 것이 좋을 수 있습니다. 검색을 실행하는 사이트 수를 최소화하면 검색에 사용되는 전체 네트워크 대역폭을 줄이는 동시에 사이트 서버에서 만들어지고 처리해야 하는 전체 DDR 수를 줄일 수 있습니다.  

대다수의 검색 방법 구성은 별도의 설명이 필요 없이 쉽게 이해할 수 있습니다. 다음 섹션에서는 구성 전에 추가 정보가 필요할 수 있는 검색 옵션에 대한 자세한 정보를 제공합니다.  

다음 옵션은 여러 Active Directory 검색 방법과 함께 사용할 수 있습니다.  

-   [델타 검색](#bkmk_delta)  

-   [도메인 로그온으로 오래된 컴퓨터 레코드 필터링](#bkmk_stalelogon)  

-   [컴퓨터 암호로 오래된 레코드 필터링](#bkmk_stalepassword)  

-   [사용자 지정된 Active Directory 특성 검색](#bkmk_customAD)  

###  <a name="a-namebkmkdeltaa-delta-discovery"></a><a name="bkmk_delta"></a> 델타 검색  
다음에 대해 사용할 수 있습니다.  

-   Active Directory 그룹 검색  

-   Active Directory 시스템 검색  

-   Active Directory 사용자 검색  

델타 검색은 독립적인 검색 방법이 아니라 해당하는 검색 방법에 대해 사용할 수 있는 옵션입니다. 델타 검색은 해당하는 검색 방법의 마지막 전체 검색 주기 이후에 수행된 변경 내용에 대한 특정 Active Directory 특성을 검색합니다.  이 검색은 전체 검색 주기보다 더 적은 리소스를 사용하고 특성 변경 내용은 Configuration Manager 데이터베이스에 제출되어 리소스 검색 레코드가 업데이트됩니다.  

기본적으로 델타 검색은 5분 주기로 실행됩니다. 이는 전체 검색 주기의 일반적인 일정보다 훨씬 자주 발생합니다.  이러한 빈번한 주기는 델타 검색이 전체 검색 주기보다 더 적은 사이트 서버와 네트워크 리소스를 사용하기 때문에 가능합니다. 델타 검색을 사용할 경우 해당 검색 방법에 대해 전체 검색 주기의 빈도를 줄일 수 있습니다.  

다음은 델타 검색에서 가장 일반적으로 검색되는 변경 내용입니다.  

-   Active Directory에 추가된 새 컴퓨터 또는 사용자  

-   기본 컴퓨터 및 사용자 정보 변경 내용  

-   그룹에 추가된 새 컴퓨터 또는 사용자  

-   그룹에서 제거된 컴퓨터 또는 사용자  

-   시스템 그룹 개체의 변경 내용  

델타 검색을 통해 새 리소스 및 그룹 멤버 자격 변경 내용을 검색할 수 있지만 리소스가 Active Directory에서 삭제된 시기는 검색하지 못합니다. 델타 검색이 만드는 DDR은 전체 검색 주기를 통해 만들어지는 DDR과 비슷하게 처리됩니다.  

델타 검색은 각 검색 방법에 대한 속성의 **폴링 일정** 탭에서 구성합니다.  

###  <a name="a-namebkmkstalelogona-filter-stale-computer-records-by-domain-logon"></a><a name="bkmk_stalelogon"></a> 도메인 로그온으로 오래된 컴퓨터 레코드 필터링  
다음에 대해 사용할 수 있습니다.  

-   Active Directory 그룹 검색  

-   Active Directory 시스템 검색  

컴퓨터의 최신 도메인 로그온을 기반으로 오래된 컴퓨터 레코드가 있는 컴퓨터를 제외하도록 검색을 구성할 수 있습니다. 이 옵션을 사용하는 경우 Active Directory 시스템 검색이 식별되는 각 컴퓨터를 평가합니다. Active Directory 그룹 검색은 검색되는 그룹의 구성원인 각 컴퓨터를 평가합니다.  

이 옵션을 사용하려면  

-   컴퓨터는 Active Directory Domain Services에서 **lastLogonTimeStamp** 특성을 업데이트하도록 구성되어야 합니다.  

-   Active Directory 도메인 기능 수준이 Windows Server 2003 이상으로 설정되어야 합니다.  

이 설정에 사용하려는 마지막 로그온 후 시간을 구성할 때 도메인 컨트롤러 간의 복제 간격을 고려해야 합니다.  

필터링은 **Active Directory 시스템 검색 속성** 및 **Active Directory 그룹 검색 속성** 대화 상자 모두의 **옵션** 탭에서 **지정한 기간 동안 도메인에 로그온한 컴퓨터만 검색**옵션을 선택하여 구성합니다.  

> [!WARNING]  
>  이 필터 및 **컴퓨터 암호로 오래된 레코드 필터**를 구성하는 경우 각 필터의 조건을 충족하는 컴퓨터는 검색에서 제외됩니다.  

###  <a name="a-namebkmkstalepassworda-filter-stale-records-by-computer-password"></a><a name="bkmk_stalepassword"></a> 컴퓨터 암호로 오래된 레코드 필터링  
다음에 대해 사용할 수 있습니다.  

-   Active Directory 그룹 검색  

-   Active Directory 시스템 검색  

컴퓨터의 최신 컴퓨터 계정 암호 업데이트를 기반으로 오래된 컴퓨터 레코드가 있는 컴퓨터를 제외하도록 검색을 구성할 수 있습니다. 이 옵션을 사용하는 경우 Active Directory 시스템 검색이 식별되는 각 컴퓨터를 평가합니다. Active Directory 그룹 검색은 검색되는 그룹의 구성원인 각 컴퓨터를 평가합니다.  

이 옵션을 사용하려면  

-   컴퓨터는 Active Directory Domain Service의 **pwdLastSet** 특성을 업데이트하도록 구성되어야 합니다.  

이 옵션을 구성하는 경우 도메인 컨트롤러 간의 복제 간격 이외에 이 특성에 대한 업데이트 간격을 고려합니다.  

필터링은 **Active Directory 시스템 검색 속성** 및 **Active Directory 그룹 검색 속성** 대화 상자의 **옵션** 탭에서 **지정한 기간 동안 컴퓨터 계정 암호를 업데이트한 컴퓨터만 검색**옵션을 선택하여 구성합니다.  

> [!WARNING]  
>  이 필터 및 **도메인 로그온으로 오래된 레코드 필터**를 구성할 때 각 필터의 조건을 충족하는 컴퓨터는 검색에서 제외됩니다.  

###  <a name="a-namebkmkcustomada-search-customized-active-directory-attributes"></a><a name="bkmk_customAD"></a> 사용자 지정된 Active Directory 특성 검색  
 다음에 대해 사용할 수 있습니다.  

-   Active Directory 시스템 검색  

-   Active Directory 사용자 검색  

각 검색 방법은 검색할 수 있는 고유한 Active Directory 특성 목록을 지원합니다.  

사용자 지정 특성 목록은 **Active Directory 시스템 검색 속성** 및 **Active Directory 사용자 검색 속성** 대화 상자의 **Active Directory 특성** 탭에서 보고 구성할 수 있습니다.  



<!--HONumber=Dec16_HO3-->


