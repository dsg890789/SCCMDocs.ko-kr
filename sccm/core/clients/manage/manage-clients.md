---
title: "클라이언트 관리 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 클라이언트를 관리하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: 17
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: f777295958e9cbc729e3759d354521c96ae3e8ac
ms.openlocfilehash: 67a814330123a1615a0663872bf4af64e5b81a84


---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트를 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 클라이언트를 설치하여 Configuration Manager 사이트에 성공적으로 할당하면 **장치** 노드의 **자산 및 준수** 작업 영역과 **장치 컬렉션** 노드의 컬렉션 하나 이상에 장치가 표시됩니다. 장치 또는 장치가 포함된 컬렉션을 선택하면 여러 가지 관리 작업을 선택할 수 있습니다. 그러나 다른 방법으로 클라이언트를 관리할 수도 있습니다. 이 경우 Configuration Manager 콘솔을 사용하지 않는 작업이나 콘솔의 다른 작업 영역이 사용될 수 있습니다.  

 이 항목에서는 **자산 및 준수** 작업 영역에서 Configuration Manager 클라이언트를 관리할 수 있는 작업에 대한 대략적인 정보와, Configuration Manager 클라이언트를 관리하는 데 도움이 되는 추가 작업에 대한 상세 정보를 모두 확인할 수 있습니다. 클라이언트를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

> [!NOTE]  
>  Configuration Manager 클라이언트가 설치되었지만 Configuration Manager 콘솔에 표시되지 않습니다. 이 시나리오는 사이트에 클라이언트를 아직 할당하지 않은 경우나 콘솔을 새로 고치거나 컬렉션 멤버 자격을 업데이트해야 하는 경우에 발생할 수 있습니다.  
>   
>  또한, Configuration Manager 클라이언트가 설치되지 않은 경우에도 콘솔에 장치가 표시될 수 있습니다. 이 시나리오는 장치가 검색되지만 Configuration Manager 클라이언트가 설치되거나 할당되지 않은 경우에 발생할 수 있습니다. Exchange Server 커넥터를 사용하여 관리하는 모바일 장치에는 Configuration Manager 클라이언트가 설치되지 않습니다. 또한, Microsoft Intune에서 등록한 장치에도 Configuration Manager 클라이언트가 설치되지 않습니다.  
>   
>  Configuration Manager 콘솔의 **클라이언트** 열을 사용하여 Configuration Manager 콘솔에서 관리할 수 있도록 Configuration Manager 클라이언트 설치 여부를 결정합니다.  

##  <a name="a-namebkmkmanagingclientsdevicesnodea-manage-clients-from-the-devices-node"></a><a name="BKMK_ManagingClients_DevicesNode"></a> 장치 노드에서 클라이언트 관리  
 **자산 및 호환성** 작업 영역의 **장치** 노드에서 하나 이상의 장치를 관리하려면 다음 절차 및 표를 참조하세요.  

> [!IMPORTANT]  
>  장치 유형에 따라 이러한 옵션 중 일부를 사용하지 못할 수도 있습니다.  

#### <a name="to-manage-clients-from-the-devices-node"></a>장치 노드에서 클라이언트를 관리하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **장치**를 클릭합니다.  

3.  장치를 하나 이상 선택한 다음 클라이언트 관리 작업 중 하나를 리본에서 선택하거나 장치를 마우스 오른쪽 단추로 클릭하여 선택합니다.  

    -   **사용자 장치 선호도 정보 관리**  

         사용자와 장치 간의 연결을 구성할 수 있습니다. 그러면 사용자에게 소프트웨어를 효율적으로 배포할 수 있습니다.  

         [System Center Configuration Manager에서 사용자 장치 선호도를 사용하여 사용자와 장치 연결](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)을 참조하세요.  

    -   **새 컬렉션 또는 기존 컬렉션에 장치 추가**  

         직접 규칙을 사용하여 선택한 장치를 컬렉션에 빠르게 추가하려면 다음과 같은 컬렉션 관련 작업을 수행하세요.  

         [System Center Configuration Manager의 컬렉션 작업 및 유지 관리](../../../core/clients/manage/collections/operations-and-maintenance-for-collections.md)  

    -   **클라이언트 강제 설치 마법사를 사용하여 클라이언트 설치 및 다시 설치**  

         클라이언트 강제 설치 마법사는 Windows를 실행하는 컴퓨터에서 사이트 구성 옵션과, 클라이언트 강제 설치를 위해 지정한 다른 client.msi 속성을 사용하여 Configuration Manager 클라이언트를 복구하거나 다시 구성할 수 있도록 이 클라이언트를 설치하거나 다시 설치하는 효율적인 방법을 제공합니다.  

        > [!TIP]  
        >  Configuration Manager 클라이언트를 설치(및 다시 설치)하는 다른 여러 가지 방법이 있습니다. 클라이언트 강제 설치 마법사는 콘솔에서 실행할 수 있기 때문에 편리한 클라이언트 설치 방법을 제공하지만 이 클라이언트 설치 방법은 여러 가지 종속성이 있어 모든 환경에 적합하지는 않습니다. 클라이언트 강제 설치를 사용하여 클라이언트를 설치하지 못하는 경우에 사용할 수 있는 다른 여러 가지 클라이언트 설치 방법이 있습니다. 종속성에 대한 자세한 내용은 [Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md)을 참조하세요. 다른 클라이언트 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 방법](../../../core/clients/deploy/plan/client-installation-methods.md)을 참조하세요.  

         [클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush)을 참조하세요.  

    -   **사이트 재할당**  

         관리되는 모바일 장치를 포함한 클라이언트를 계층의 다른 기본 사이트에 재할당합니다. 클라이언트는 개별적으로 재할당할 수도 있고 여러 개를 선택하여 새 사이트에 대량으로 재할당할 수도 있습니다.  

    -   **원격으로 클라이언트 관리**  

         리소스 탐색기를 실행하면 Windows 클라이언트에서 하드웨어 및 소프트웨어 인벤토리 정보를 확인하고 원격 제어, 원격 지원 또는 원격 데스크톱을 사용하여 원격으로 관리할 수 있습니다.  

         [System Center Configuration Manager에서 하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) 및 [System Center Configuration Manager에서 소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md)을 참조하세요.  

         [System Center Configuration Manager를 사용하여 Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md)을 참조하세요.  

    -   **클라이언트 승인**  

         클라이언트가 HTTP와 자체 서명된 인증서를 사용하여 사이트 시스템과 통신하는 경우 이러한 클라이언트를 승인해야 신뢰할 수 있는 컴퓨터로 식별됩니다. 기본적으로 사이트 구성은 동일한 Active Directory 포리스트 및 신뢰할 수 있는 포리스트의 클라이언트를 자동으로 승인하므로 각 클라이언트를 수동으로 승인할 필요는 없습니다. 그러나 신뢰하는 작업 그룹 컴퓨터 및 신뢰하지만 승인하지 않은 다른 컴퓨터는 수동으로 승인해야 합니다.  

        > [!WARNING]  
        >  승인되지 않은 클라이언트에 대해서도 일부 관리 기능이 작동할 수 있지만 이는 Configuration Manager에서 지원되지 않는 시나리오입니다.  

         항상 HTTP가 아니라 HTTPS를 사용하여 사이트 시스템과 통신하는 클라이언트나 HTTP를 사용하여 사이트 시스템과 통신할 때 PKI 인증서를 사용하는 클라이언트는 승인할 필요가 없습니다. 이러한 클라이언트는 PKI 인증서를 사용하여 Configuration Manager와의 신뢰 관계를 설정합니다.  

    -   **클라이언트 차단 또는 차단 해제**  

         더 이상 신뢰하지 않는 클라이언트를 차단하여 클라이언트 정책을 받지 않도록 하고 Configuration Manager 사이트 시스템이 해당 클라이언트와 통신하지 않도록 합니다.  

        > [!WARNING]  
        >  클라이언트를 차단하면 클라이언트에서 Configuration Manager 사이트 시스템으로 보내는 통신만 차단되고 다른 장치로 보내는 통신은 차단되지 않습니다. 또한, 클라이언트가 HTTPS 대신 HTTP를 사용하여 사이트 시스템과 통신할 경우 몇 가지 보안 관련 제한 사항이 있습니다.  

         나중에 마음이 바뀌면 차단된 클라이언트를 차단 해제할 수 있습니다. 그러나 AMT용으로 프로비전된 Intel AMT 기반 컴퓨터가 차단된 경우에 이 컴퓨터를 차단 해제하면 추가 단계를 수행해야 해당 컴퓨터를 다시 대역 외로 관리할 수 있습니다.  

         [System Center Configuration Manager에서 클라이언트를 차단할지 여부 결정](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md)을 참조하세요.  

    -   **필수 PXE 배포 지우기**  

         선택한 컴퓨터에 대해 필수 PXE 배포를 다시 배포하려면 이 옵션을 사용합니다.  

         [System Center Configuration Manager에서 PXE를 사용하여 네트워크를 통해 Windows 배포](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

    -   **클라이언트 속성 관리**  

         클라이언트를 대상으로 하는 검색 데이터 및 배포를 볼 수 있습니다. 작업 순서에서 장치에 운영 체제를 배포하는 데 사용하는 변수를 구성할 수도 있습니다.  

    -   **클라이언트 삭제**  

        > [!WARNING]  
        >  Configuration Manager 클라이언트를 제거하거나 컬렉션에서 제거하려면 클라이언트를 삭제하지 마세요.  

         **삭제** 작업은 Configuration Manager 데이터베이스에서 클라이언트 레코드를 수동으로 삭제하며, 일반적으로 문제 해결 시나리오가 아니라면 이 작업을 사용하지 않아야 합니다. 클라이언트 레코드를 삭제했으나 Configuration Manager 클라이언트가 아직 설치되어 있고 Configuration Manager와 통신하는 경우 클라이언트 기록 및 이전 연결은 모두 없어지지만 하트비트 검색에서 클라이언트 레코드를 다시 만들게 되고 Configuration Manager 콘솔에 다시 표시됩니다.  

        > [!NOTE]  
        >  Configuration Manager에서 등록한 모바일 장치 클라이언트를 삭제하면 이 작업으로 인해 모바일 장치에 발급된 PKI 인증서도 해지되므로 IIS에서 CRL을 확인하지 않아도 이 인증서는 관리 지점에서 거부됩니다. 모바일 장치 기존 클라이언트를 삭제해도 이러한 클라이언트의 인증서는 해지되지 않습니다.  

         클라이언트를 제거하려면 [Configuration Manager 클라이언트 제거](#BKMK_UninstalClient)섹션을 참조하세요.  

         새 기본 사이트에 클라이언트를 할당하려면 [System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법](../../../core/clients/deploy/assign-clients-to-a-site.md)을 참조하세요.  

         컬렉션에서 클라이언트를 제거하려면 컬렉션 속성을 다시 구성하세요. [System Center Configuration Manager에서 컬렉션을 관리하는 방법](../../../core/clients/manage/collections/manage-collections.md)을 참조하세요.  

    -   **모바일 장치 초기화**  

         초기화 명령을 지원하는 모바일 장치를 초기화할 수 있습니다.  

         이 작업은 개인 설정 및 개인 데이터를 포함하여 모바일 장치의 모든 데이터를 영구적으로 제거합니다. 일반적으로 이 작업은 모바일 장치를 공장 기본값으로 다시 설정합니다. 모바일 장치를 더 이상 신뢰하지 않는 경우(예: 잃어버렸거나 도난당한 경우) 모바일 장치를 초기화합니다.  

        > [!TIP]  
        >  모바일 장치에서 원격 초기화 명령을 처리하는 방법에 대한 자세한 내용은 제조업체의 설명서를 확인하세요.  

         초기화 요청을 보내면 대개의 경우 모바일 장치에서 초기화 명령을 받을 때까지 지연이 있습니다.  

        -   Configuration Manager 또는 Microsoft Intune에서 모바일 장치를 등록한 경우 클라이언트에서 다음에 클라이언트 정책을 다운로드할 때 초기화 명령을 받습니다.  

        -   Exchange Server 커넥터로 모바일 장치를 관리하는 경우 다음에 Exchange와 동기화할 때 모바일 장치에서 초기화 명령을 받습니다.  

         **초기화 상태** 열을 사용하면 모바일 장치에서 초기화 명령을 받는 시간을 모니터링할 수 있습니다. 모바일 장치에서 Configuration Manager로 초기화 승인을 보낼 때까지는 초기화 명령을 취소할 수 있습니다.  

    -   **모바일 장치 사용 중지**  

         **사용 중지** 옵션은 Intune 또는 온\-프레미스 모바일 장치 관리에서 등록한 모바일 장치에서만 지원됩니다.  

         자세한 내용은 [System Center Configuration Manager를 사용하여 원격 초기화, 원격 잠금 또는 암호 재설정으로 데이터 보호 지원](../../../mdm/deploy-use/wipe-lock-reset-devices.md)을 참조하세요.  

    -   **장치의 소유권 변경**  

         장치가 도메인에 가입되어 있지 않으며 Configuration Manager 클라이언트가 설치되어 있지 않으면 장치 소유권을 **회사** 또는 **개인**으로 변경할 수 있습니다.  

         응용 프로그램 요구 사항에서 이 값을 사용하여 배포를 제어할 수 있고 이 구성을 사용하여 사용자 장치에서 수집되는 인벤토리 수도 제어할 수 있습니다.  

        장치 목록에서 소유권 값을 보려면 열 머리글을 마우스 오른쪽 단추로 클릭하고 **장치 소유자**를 선택하여 보기에는 열을 추가해야 할 수 있습니다.

         자세한 내용은 [System Center Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 장치 관리)](../../../mdm/plan-design/hybrid-mobile-device-management.md)을 참조하세요.  

##  <a name="a-namebkmkmanagingclientsdevicecollectionsnodea-manage-clients-from-the-device-collections-node"></a><a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> 장치 컬렉션 노드에서 클라이언트 관리  
 **자산 및 호환성** 작업 영역의 **장치 컬렉션** 노드에서 컬렉션의 장치를 관리하려면 다음 절차 및 표를 참조하세요.  

 **장치** 노드에서 장치를 하나 또는 여러 개 선택할 경우에 수행할 수 있는 클라이언트 관리 작업은 대부분 컬렉션 수준에서도 수행할 수 있습니다. 이 경우 컬렉션의 모든 사용 가능 장치에 관리 작업을 자동으로 적용할 수 있는 이점이 있습니다. 이 방법은 동시에 여러 클라이언트를 관리하는 데 편리한 방법일 수 있지만 사이트 서버에서 네트워크 패킷이 많이 생성되고 CPU 사용량이 늘어납니다.  

 컬렉션 수준에서만 수행할 수 있는 클라이언트 관리 작업도 몇 가지 있습니다. 이러한 작업은 다음 표에 나와 있습니다.  

 컬렉션 수준 클라이언트 관리 작업을 수행하기 전에 컬렉션에 있는 장치 수, 대역폭이 낮은 네트워크 연결로 연결되었는지 여부 및 모든 장치에 대해 작업을 완료하는 데 걸리는 시간을 고려하세요. 클라이언트 관리 작업을 수행할 때 콘솔에서 작업을 중지할 수 없습니다.  

#### <a name="to-manage-clients-from-the-device-collections-node"></a>장치 컬렉션 노드에서 클라이언트를 관리하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 클릭합니다.  

3.  컬렉션을 선택한 다음 클라이언트 관리 작업 중 하나를 리본에서 선택하거나 컬렉션을 마우스 오른쪽 단추로 클릭하여 선택합니다.  

    -   **컴퓨터에서 맬웨어를 검사하고 맬웨어 방지 정의 파일을 다운로드합니다.**  

         [System Center Configuration Manager의 Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md)을 참조하세요.  

    -   **소프트웨어, 구성 기준 및 작업 순서를 배포합니다.**  

         소프트웨어 및 구성 기준을 배포하는 방법에 대한 자세한 내용은 다음을 참조하세요.  

        -   [System Center Configuration Manager에서 소프트웨어 업데이트 배포](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [System Center Configuration Manager에서 준수 설정 계획 및 구성](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **전원 관리 설정을 구성합니다.**  

         [System Center Configuration Manager에서 전원 계획을 만들고 적용하는 방법](../../../core/clients/manage/power/create-and-apply-power-plans.md)을 참조하세요. 전원 계획은 Windows를 실행하는 컴퓨터에서만 사용할 수 있습니다.  

    -   **정책을 최대한 빨리 다운로드하도록 컴퓨터에 알립니다.**  

         구성된 클라이언트 정책 폴링 간격이 아니더라도 최대한 빨리 정책을 다운로드하도록, 선택한 Windows 클라이언트에 알리려면 클라이언트 알림을 사용합니다.  

         클라이언트 알림 작업은 **모니터링** 작업 영역의 **클라이언트 작업** 노드에 표시됩니다.  

##  <a name="a-namebkmkclientcachea-configure-the-client-cache-for-configuration-manager-clients"></a><a name="BKMK_ClientCache"></a> Configuration Manager 클라이언트에 대한 클라이언트 캐시 구성  
 Windows Configuration Manager 클라이언트에서 응용 프로그램 및 프로그램을 설치할 때 임시 파일을 저장하는 데 사용할 위치 및 디스크 공간을 구성할 수 있습니다. 소프트웨어 업데이트도 클라이언트 캐시를 사용하지만 소프트웨어 업데이트는 구성된 캐시 크기의 제한을 받지 않으며 항상 캐시로 다운로드하려고 시도합니다. Configuration Manager 클라이언트를 수동으로 설치할 때나 클라이언트 강제 설치를 사용할 때 또는 클라이언트를 설치한 후에 클라이언트 캐시 설정을 구성할 수 있습니다.

Configuration Manager 버전 1606부터 Configuration Manager 콘솔에서 클라이언트 설정을 사용하여 캐시 폴더 크기를 지정할 수 있습니다.   

 Configuration Manager 클라이언트 캐시의 기본 위치는 %*windir*%\ccmcache이고 기본 디스크 공간은 5120MB입니다.  

> [!IMPORTANT]  
>  클라이언트 캐시에 사용되는 폴더는 암호화하지 마세요. Configuration Manager는 암호화된 폴더로 콘텐츠를 다운로드할 수 없습니다.  

### <a name="about-client-cache"></a>클라이언트 캐시 정보  

Configuration Manager 클라이언트는 배포를 받자마자 필수 소프트웨어의 콘텐츠를 다운로드하지만 예약된 배포 시간까지 실행하지 않고 기다립니다. 예약된 시간에 Configuration Manager 클라이언트가 캐시에서 콘텐츠를 사용할 수 있는지 여부를 확인합니다. 콘텐츠가 캐시에 있고 올바른 버전이면 클라이언트는 항상 캐시된 콘텐츠를 사용합니다. 그러나 필수 버전의 콘텐츠가 변경되었거나 다른 패키지에 필요한 공간을 만들기 위해 콘텐츠가 삭제된 경우에는 해당 콘텐츠가 다시 캐시로 다운로드됩니다.  

클라이언트가 캐시 크기보다 큰 응용 프로그램이나 프로그램의 콘텐츠를 다운로드하려고 하면 캐시 크기가 부족하여 배포가 실패하며 Configuration Manager에서 상태 메시지 ID 10050을 생성합니다. 나중에 캐시 크기를 늘리면 필수 프로그램과 필수 응용 프로그램에 대해 서로 다른 다운로드 다시 시도 동작이 수행됩니다.  

-   필수 프로그램의 경우: 클라이언트에서 자동으로 콘텐츠를 다시 다운로드하려고 시도하지 않습니다. 클라이언트에 패키지와 프로그램을 다시 배포해야 합니다.  
-   필수 응용 프로그램의 경우: 응용 프로그램 배포는 상태 기반이므로 클라이언트에서 다음에 클라이언트 정책을 다운로드할 때 자동으로 콘텐츠를 다시 다운로드하려고 시도합니다.  

클라이언트에서 캐시 크기보다 작은 패키지를 다운로드하려고 시도하지만 현재 캐시가 꽉 차 있는 경우에는 캐시 공간을 사용할 수 있게 되거나, 다운로드 제한 시간이 초과되거나, 캐시 공간 실패에 대한 다시 시도 제한에 도달할 때까지 모든 필수 배포가 계속 다시 시도됩니다. 나중에 캐시 크기가 늘어나면 Configuration Manager 클라이언트가 다음 다시 시도 간격 때 패키지를 다시 다운로드하려고 시도합니다. 클라이언트는 4시간 간격으로 18회까지 콘텐츠를 다운로드하려고 시도합니다.  

캐시된 콘텐츠는 자동으로 삭제되지 않지만 클라이언트에서 해당 콘텐츠를 사용한 후 최소 하루 동안 캐시에 남아 있습니다. 클라이언트 캐시에 콘텐츠를 유지하는 옵션으로 패키지 속성을 구성하면 클라이언트가 캐시에서 패키지 콘텐츠를 자동으로 삭제하지 않습니다. 최근 24시간 이내에 다운로드된 패키지가 클라이언트 캐시 공간을 사용하고 있는데 클라이언트가 새 패키지를 다운로드해야 하는 경우 클라이언트 캐시 크기를 늘리거나, 유지된 캐시 콘텐츠를 삭제하는 삭제 옵션을 선택할 수 있습니다.  

 수동으로 클라이언트를 설치하는 동안이나 클라이언트를 설치한 후에 클라이언트 캐시를 구성하려면 다음 절차를 수행하세요.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>수동 클라이언트 설치를 사용하여 클라이언트를 설치할 때 클라이언트 캐시를 구성하려면  

설치 원본 위치에서 CCMSetup.exe 명령을 실행하고 다음 필수 속성을 공백으로 구분하여 지정합니다.  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > 버전 1606의 경우 SMSCACHESIZE 대신 Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](../../../core/clients/deploy/about-client-settings.md#Client-Cache-Settings)을 참조하세요.

CCMSetup.exe에서 이러한 명령줄 속성을 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>클라이언트 강제 설치를 사용하여 클라이언트를 설치할 때 클라이언트 캐시를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.  

3.  **사이트** 목록에서 자동 사이트 전체 클라이언트 강제 설치를 구성하려는 사이트를 선택합니다.  

4.  **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정**을 클릭한 다음 **설치 속성**탭을 선택합니다.  

5.  **설치 속성** 탭에서 다음 필수 속성을 지정하고 공백을 사용하여 구분합니다.  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > 버전 1606의 경우 SMSCACHESIZE 대신 Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](../../../core/clients/deploy/about-client-settings.md#Client-Cache-Settings)을 참조하세요.

       CCMSetup.exe에서 이러한 명령줄 속성을 사용하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

6.  **확인** 을 클릭하여 지정한 속성을 저장합니다.  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>클라이언트 컴퓨터에 클라이언트 캐시 폴더를 구성하려면  

1.  클라이언트 컴퓨터의 제어판에서 **Configuration Manager** 로 이동한 다음 속성을 두 번 클릭하여 엽니다.  

2.  **캐시** 탭을 클릭합니다.  

3.  클라이언트 캐시로 예약할 디스크 공간을 지정합니다.  

4.  클라이언트 캐시 폴더의 위치를 변경하려면 **위치 변경**을 클릭한 다음 새 위치를 지정합니다. 기본 위치는 *%windir%*\ccmcache입니다.  

5.  클라이언트 캐시 폴더에 현재 저장된 파일을 삭제하려면 **파일 삭제**를 클릭합니다.  

6.  **확인** 을 클릭하여 **Configuration Manager 속성**을 닫습니다.  

### <a name="to-configure-client-cache-size-in-client-settings"></a>클라이언트 설정에서 클라이언트 캐시 크기를 구성하려면

버전 1606부터 클라이언트를 다시 설치하지 않고 클라이언트 캐시 폴더의 크기를 조정할 수 있습니다. 이를 위해 클라이언트 설정을 사용하여 Configuration Manager 콘솔에서 클라이언트 캐시 크기를 구성합니다.  

1. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동합니다.

2. **기본 클라이언트 설정**을 두 번 클릭합니다.
  또한 캐시 크기를 선택적으로 적용하여 사용자 지정 클라이언트 설정을 만들 수도 있습니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.

 3. **클라이언트 캐시 설정** 을 클릭하고 **클라이언트 캐시 크기 구성** 에 대해 **예**를 선택합니다.

 4. **MB** 또는 **디스크 설정 백분율**중 하나를 사용하여 최대 캐시 크기를 조정합니다. 캐시는 어떤 크기로든 작게 조정됩니다.

 5. **확인**을 클릭합니다.

    Configuration Manager 클라이언트에서는 그 다음 클라이언트 정책을 다운로드할 때 이러한 설정으로 캐시 크기를 구성할 수 있습니다.

##  <a name="a-namebkmkuninstalclienta-uninstall-the-configuration-manager-client"></a><a name="BKMK_UninstalClient"></a> Configuration Manager 클라이언트 제거  
 **/Uninstall** 속성을 통해 **CCMSetup.exe**를 사용하여 Windows Configuration Manager 클라이언트 소프트웨어를 제거할 수 있습니다. 명령 프롬프트에서 개별 컴퓨터에 대해 CCMSetup.exe를 실행하거나 컴퓨터의 컬렉션에 대해 클라이언트를 제거하는 패키지 및 프로그램을 배포합니다.  

> [!WARNING]  
>  모바일 장치에서는 Configuration Manager 클라이언트를 제거할 수 없습니다. 모바일 장치에서 Configuration Manager 클라이언트를 제거해야 하는 경우 장치를 초기화해야 합니다. 그러면 모바일 장치에서 모든 데이터가 삭제됩니다.  

 컴퓨터에서 Configuration Manager 클라이언트를 제거하려면 다음 절차를 따르세요.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>명령 프롬프트에서 Configuration Manager 클라이언트를 제거하려면  

1.  Windows 명령 프롬프트를 열고 폴더를 CCMSetup.exe가 있는 위치로 변경합니다.  

2.   **Ccmsetup.exe /uninstall**을 입력하고 **Enter**키를 누릅니다  

> [!NOTE]  
>  제거 프로세스는 자동으로 진행되며 화면에 결과가 표시되지 않습니다. 클라이언트가 제대로 제거되었는지 확인하려면 클라이언트 컴퓨터의 **%windir%\ ccmsetup** 폴더에서 *CCMSetup.log* 라는 로그 파일을 검토합니다.  

##  <a name="a-namebkmkconflictingrecordsa-manage-conflicting-records-for-configuration-manager-clients"></a><a name="BKMK_ConflictingRecords"></a> Configuration Manager 클라이언트에 대한 충돌 레코드 관리  
 Configuration Manager에서는 하드웨어 ID를 사용하여 중복되었을 수 있는 클라이언트를 식별하고 충돌 레코드에 대해 경고합니다. 예를 들어 컴퓨터를 다시 설치하면 하드웨어 ID는 동일하지만 Configuration Manager에서 사용하는 GUID는 변경될 수 있습니다.  

 Configuration Manager에서 신뢰할 수 있는 원본의 컴퓨터 계정이나 PKI 인증서의 Windows 인증을 사용하여 충돌을 해결할 수 있는 경우에는 충돌이 자동으로 해결됩니다. 그러나 Configuration Manager에서 충돌을 해결할 수 없는 경우 중복된 하드웨어 ID(기본 설정)를 검색할 때 자동으로 레코드를 병합하는 계층 구조 설정을 사용할 수도 있고, 어떠한 경우에 새 클라이언트 레코드를 병합하거나 차단하거나 만들지를 결정할 수도 있습니다. 중복된 레코드를 수동으로 관리하려는 경우 Configuration Manager 콘솔을 사용하여 충돌 레코드를 수동으로 해결해야 합니다.  

#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>충돌 레코드 관리를 위한 계층 설정을 변경하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.  

3.  **사이트** 그룹에서 **계층 설정**을 클릭한 다음 **클라이언트 승인 및 충돌 레코드** 탭을 클릭합니다.  

4.  **충돌 레코드를 자동으로 해결** 을 클릭하여 충돌 레코드를 자동으로 병합하거나 **충돌 레코드를 수동으로 해결**을 클릭한 다음 **확인**을 클릭합니다.  

    > [!NOTE]  
    >  Configuration Manager에서 컴퓨터 계정이나 PKI 인증서를 사용하여 충돌을 해결할 수 있는 경우에는 이 설정이 무시되고 충돌이 자동으로 해결됩니다.  

#### <a name="to-manually-resolve-conflicting-records"></a>충돌 레코드를 수동으로 해결하려면  

1.  Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.  

2.  **모니터링** 작업 영역에서 **시스템 상태**를 확장한 후 **충돌하는 레코드**를 클릭합니다.  

3.  결과 창에서 충돌 레코드를 하나 이상 선택한 다음 **충돌하는 레코드**를 클릭합니다.  

4.  **충돌하는 레코드** 대화 상자에서 다음 중 하나를 선택한 다음 **확인**을 클릭합니다.  

    -   **병합** 을 클릭하여 새로 검색된 레코드와 기존 클라이언트 레코드를 결합하여 통합된 하나의 레코드를 만듭니다.  

    -   **새로 만들기** 를 클릭하여 충돌 클라이언트 레코드에 대해 새 레코드를 만듭니다.  

    -   **차단** 을 클릭하여 충돌 클라이언트 레코드에 대해 새 레코드를 만들되, 차단됨으로 표시합니다.  

##  <a name="a-namebkmkpolicyretrievala-initiate-policy-retrieval-for-a-configuration-manager-client"></a><a name="BKMK_PolicyRetrieval"></a> Configuration Manager 클라이언트에 대한 정책 검색 시작  
 Windows Configuration Manager 클라이언트는 클라이언트 설정으로 구성한 일정에 따라 클라이언트 정책을 다운로드합니다. 그러나 클라이언트에서 애드혹 정책 검색을 시작하려는 경우(예: 문제 해결 시나리오나 테스트하는 경우)가 있을 수 있습니다.  

 예약된 폴링 간격이 아닐 때 Configuration Manager 클라이언트에서 **작업** 탭을 사용하거나 컴퓨터에서 스크립트를 실행하여 클라이언트에서 애드혹 정책 검색을 시작하려면 다음 절차를 수행하세요. 이러한 절차를 수행할 수 있는 로컬 관리 권한으로 클라이언트 컴퓨터에 로그온해야 합니다.  

> [!NOTE]  
>  클라이언트 알림을 사용하면 예약된 클라이언트 정책 폴링 간격이 아닐 때 클라이언트 정책 검색을 시작할 수 있습니다.  
>   
>  Linux 및 UNIX를 실행하는 클라이언트를 관리할 수 있습니다. Linux 및 UNIX를 실행하는 클라이언트의 정책 검색에 대한 자세한 내용은 [Linux 및 UNIX 서버에 대한 컴퓨터 정책](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU)을 참조하세요.  

#### <a name="to-initiate-client-policy-retrieval-by-using-client-notification"></a>클라이언트 알림을 사용하여 클라이언트 정책 검색을 시작하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.  

2.  **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 클릭합니다.  

3.  정책을 다운로드할 컴퓨터가 포함된 장치 컬렉션을 선택한 다음 **홈** 탭의 **컬렉션** 그룹에서 **클라이언트 알림** 을 클릭하고 **컴퓨터 정책 다운로드**를 클릭합니다.  

    > [!NOTE]  
    >  클라이언트 알림을 사용하여 **장치** 노드의 임시 컬렉션 노드에 표시되는 하나 이상의 선택한 장치에 대한 정책 검색을 시작할 수도 있습니다.  

#### <a name="to-manually-initiate-client-policy-retrieval-by-using-the-actions-tab-on-the-configuration-manager-client"></a>Configuration Manager 클라이언트의 작업 탭을 사용하여 수동으로 클라이언트 정책 검색을 시작하려면  

1.  컴퓨터의 제어판에서 **Configuration Manager** 를 선택합니다.  

2.  **작업** 탭을 클릭합니다.  

3.  **컴퓨터 정책 검색 및 평가 주기**를 클릭하여 컴퓨터 정책을 시작한 다음 **지금 실행**을 클릭합니다.  

4.  **확인** 을 클릭하여 프롬프트를 확인합니다.  

5.  필요한 다른 작업(예: 사용자 클라이언트 설정의 **사용자 정책 검색 및 평가 주기**에 대해서도 3단계와 4단계를 반복합니다.  

6.  **확인** 을 클릭하여 **Configuration Manager 속성**을 닫습니다.  

#### <a name="to-manually-initiate-client-policy-retrieval-by-using-a-script"></a>스크립트를 사용하여 수동으로 클라이언트 정책 검색을 시작하려면  

1.  메모장과 같은 텍스트 편집기를 엽니다.  

2.  다음 내용을 복사하여 파일에 삽입합니다.  

    ```  
    on error resume next  

    dim oCPAppletMgr 'Control Applet manager object.  
    dim oClientAction 'Individual client action.  
    dim oClientActions 'A collection of client actions.  

    'Get the Control Panel manager object.  
    set  oCPAppletMgr=CreateObject("CPApplet.CPAppletMgr")  
    if err.number <> 0 then  
        Wscript.echo "Couldn't create control panel application manager"  
        WScript.Quit  
    end if  

    'Get a collection of actions.  
    set oClientActions=oCPAppletMgr.GetClientActions  
    if err.number<>0 then  
        wscript.echo "Couldn't get the client actions"  
        set oCPAppletMgr=nothing  
        WScript.Quit  
    end if  

    'Display each client action name and perform it.  
    For Each oClientAction In oClientActions  

        if oClientAction.Name = "Request & Evaluate Machine Policy" then  
            wscript.echo "Performing action " + oClientAction.Name   
            oClientAction.PerformAction  
        end if  
    next  

    set oClientActions=nothing  
    set oCPAppletMgr=nothing  
    ```  

3.  .vbs 확장명으로 파일을 저장합니다.  

4.  클라이언트 컴퓨터에서 다음 방법 중 하나를 사용하여 파일을 실행합니다.  

    -   Windows 탐색기를 사용하여 파일로 이동한 다음 스크립트 파일을 두 번 클릭합니다.  

    -   명령 프롬프트를 열고 **cscript &lt;경로\파일 이름.vbs>**를 입력합니다.  

5.  **Windows 스크립트 호스트** 대화 상자에서 **확인** 을 클릭합니다.  



<!--HONumber=Nov16_HO1-->


