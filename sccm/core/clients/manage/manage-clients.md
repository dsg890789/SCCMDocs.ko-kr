---
title: 클라이언트 관리
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 클라이언트를 관리하는 방법을 알아봅니다.
ms.date: 12/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 623d7b6a048b7728e40adb3655dc1017408fb1d7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32342225"
---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라이언트를 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 클라이언트를 디바이스에 설치하고 사이트에 성공적으로 할당하면 **디바이스** 노드의 **자산 및 호환성** 작업 영역과 **디바이스 컬렉션** 노드의 컬렉션 하나 이상에 디바이스가 표시됩니다. 디바이스 또는 컬렉션을 선택하면 관리 작업을 수행할 수 있습니다. 그러나 다른 방법으로도 클라이언트를 관리할 수 있습니다. 이 경우 콘솔의 다른 작업 영역을 포함하거나 콘솔의 외부에서 작업을 수행할 수도 있습니다.  

> [!NOTE]  
>  Configuration Manager 클라이언트가 설치되어 있어도 사이트에 아직 할당하지 않은 경우 콘솔에 표시되지 않을 수도 있습니다. 클라이언트를 사이트에 할당한 후에 컬렉션 멤버 자격을 업데이트하고 콘솔 보기를 새로 고칩니다.  
>   
>  또한, Configuration Manager 클라이언트가 설치되지 않은 경우에도 콘솔에 디바이스가 표시될 수 있습니다. 디바이스가 검색되지만 클라이언트가 설치되거나 할당되지 않은 경우에 이 동작이 발생합니다. 
>
> Exchange Server 커넥터를 사용하여 관리되는 모바일 디바이스 및 Microsoft Intune에 등록한 디바이스에는 Configuration Manager 클라이언트가 설치되지 않습니다.  
>   
>  Configuration Manager 콘솔의 **클라이언트** 열을 사용하여 콘솔에서 관리할 수 있도록 클라이언트 설치 여부를 결정합니다.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> 장치 노드에서 클라이언트 관리  

디바이스 유형에 따라 이러한 옵션 중 일부를 사용하지 못할 수도 있습니다.  

1.  Configuration Manager 콘솔에서 **자산 및 준수** >  **장치**를 선택합니다.  

3.  디바이스를 하나 이상 선택한 다음 이러한 클라이언트 관리 작업 중 하나를 리본에서 선택하거나 디바이스를 마우스 오른쪽 단추로 클릭하여 선택합니다.  

    -   **사용자 장치 선호도 정보 관리**  

         사용자에게 소프트웨어를 효율적으로 배포할 수 있도록 사용자와 디바이스 간의 연결을 구성합니다.  

         [System Center Configuration Manager에서 사용자 장치 선호도를 사용하여 사용자와 장치 연결](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)을 참조하세요.  

    -   **새 컬렉션 또는 기존 컬렉션에 장치 추가**  

         직접 규칙을 사용하여 컬렉션에 디바이스를 추가합니다.  

    -   **클라이언트 강제 설치 마법사를 사용하여 클라이언트 설치 및 다시 설치**  

         Configuration Manager 클라이언트를 설치 및 다시 설치하여 복구하거나 다시 구성합니다. 이 옵션에는 클라이언트 강제 설치에 대해 설정한 사이트 구성 설정 및 client.msi 속성이 포함됩니다.  

        > [!TIP]  
        >  Configuration Manager 클라이언트를 설치(및 다시 설치)하는 다른 여러 가지 방법이 있습니다. 클라이언트 강제 설치 마법사는 콘솔에서 실행할 수 있기 때문에 편리한 클라이언트 설치 방법을 제공하지만 이 방법은 여러 가지 종속성이 있어 일부 환경에서는 적합하지 않습니다. 종속성에 대한 자세한 내용은 [Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md)을 참조하세요. 다른 클라이언트 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 방법](../../../core/clients/deploy/plan/client-installation-methods.md)을 참조하세요.  

         [클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하는 방법](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush)을 참조하세요.  

    -   **사이트 재할당**  

         관리되는 모바일 디바이스를 포함한 클라이언트를 계층의 다른 기본 사이트에 재할당합니다. 클라이언트는 개별적으로 재할당할 수도 있고 여러 개를 선택하여 새 사이트에 대량으로 재할당할 수도 있습니다.  

    -   **원격으로 클라이언트 관리**  

         리소스 탐색기를 실행하여 Windows 클라이언트에서 하드웨어 및 소프트웨어 인벤토리 정보를 확인합니다. 원격 제어, 원격 지원 또는 원격 데스크톱을 사용하여 디바이스를 원격으로 관리합니다.  

         [하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) 및 [소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md)을 참조하세요.  

         [Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md)을 참조하세요.  

    -   **클라이언트 승인**  

         클라이언트가 HTTP와 자체 서명된 인증서를 사용하여 사이트 시스템과 통신하는 경우 이러한 클라이언트를 승인해야 신뢰할 수 있는 컴퓨터로 식별됩니다. 기본적으로 사이트 구성은 동일한 Active Directory 포리스트 및 신뢰할 수 있는 포리스트의 클라이언트를 자동으로 승인하므로 각 클라이언트를 수동으로 승인할 필요는 없습니다. 그러나 신뢰하는 작업 그룹 컴퓨터 및 승인되지 않은 신뢰하는 다른 컴퓨터를 수동으로 승인해야 합니다.  

        > [!WARNING]  
        >  승인되지 않은 클라이언트에 대해서도 일부 관리 기능이 작동할 수 있지만 이는 Configuration Manager에서 지원되지 않는 시나리오입니다.  

         항상 HTTPS를 사용하여 사이트 시스템과 통신하는 클라이언트나 HTTP를 사용하여 사이트 시스템과 통신할 때 PKI 인증서를 사용하는 클라이언트는 승인할 필요가 없습니다. 이러한 클라이언트는 PKI 인증서를 사용하여 신뢰 관계를 설정합니다.  

    -   **클라이언트 차단 또는 차단 해제**  

         더 이상 신뢰할 수 없는 클라이언트를 차단합니다. 차단하면 클라이언트가 정책을 수신하지 못하도록 방지하고 사이트 시스템이 클라이언트와 통신하지 않도록 방지합니다.  

        > [!WARNING]  
        >  클라이언트를 차단하면 클라이언트에서 Configuration Manager 사이트 시스템으로 보내는 통신만 차단되고 다른 디바이스로 보내는 통신은 차단되지 않습니다. 또한, 클라이언트가 HTTPS 대신 HTTP를 사용하여 사이트 시스템과 통신할 경우 몇 가지 보안 관련 제한 사항이 있습니다.  

         차단된 클라이언트를 차단 해제할 수도 있습니다. 

         [System Center Configuration Manager에서 클라이언트를 차단할지 여부 결정](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md)을 참조하세요.  

    -   **필수 PXE 배포 지우기**  

         컴퓨터에 대해 필수 PXE 배포를 다시 배포합니다.  

         [System Center Configuration Manager에서 PXE를 사용하여 네트워크를 통해 Windows 배포](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

    -   **클라이언트 속성 관리**  

         클라이언트를 대상으로 하는 검색 데이터 및 배포를 볼 수 있습니다. 작업 순서에서 디바이스에 운영 체제를 배포하는 데 사용하는 변수를 구성할 수도 있습니다.  

    -   **클라이언트 삭제**  

        > [!WARNING]  
        >  Configuration Manager 클라이언트를 제거하거나 컬렉션에서 제거하려면 클라이언트를 삭제하지 마세요.  

         **삭제** 작업은 Configuration Manager 데이터베이스에서 클라이언트 레코드를 수동으로 삭제하며, 일반적으로 문제 해결 시나리오 외에는 이 작업을 사용하지 않아야 합니다. 클라이언트 레코드를 삭제하지만 클라이언트가 여전히 설치되어 사이트와의 통신하는 경우 하트비트 검색은 클라이언트 레코드를 다시 만듭니다. 클라이언트 기록 및 이전 연결이 모두 손실되지만 클라이언트 레코드는 Configuration Manager 콘솔에 다시 나타납니다.  

        > [!NOTE]  
        >  Configuration Manager에서 등록한 모바일 디바이스 클라이언트를 삭제하면 이 작업으로 인해 모바일 디바이스에 발급된 PKI 인증서도 해지되므로 IIS에서 CRL을 확인하지 않아도 이 인증서는 관리 지점에서 거부됩니다. 모바일 디바이스 기존 클라이언트를 삭제해도 이러한 클라이언트의 인증서는 해지되지 않습니다.  

         클라이언트를 제거하려면 [Configuration Manager 클라이언트 제거](#BKMK_UninstalClient)섹션을 참조하세요.  

         새 기본 사이트에 클라이언트를 할당하려면 [System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법](../../../core/clients/deploy/assign-clients-to-a-site.md)을 참조하세요.  

         컬렉션에서 클라이언트를 제거하려면 컬렉션 속성을 다시 구성하세요. [System Center Configuration Manager에서 컬렉션을 관리하는 방법](../../../core/clients/manage/collections/manage-collections.md)을 참조하세요.  

    -   **모바일 장치 초기화**  

         초기화 명령을 지원하는 모바일 디바이스를 초기화할 수 있습니다.  

         이 작업은 개인 설정 및 개인 데이터를 포함하여 모바일 디바이스의 모든 데이터를 영구적으로 제거합니다. 일반적으로 이 작업은 모바일 디바이스를 공장 기본값으로 다시 설정합니다. 모바일 디바이스를 더 이상 신뢰하지 않는 경우 모바일 디바이스를 초기화합니다. 예를 들어 디바이스를 잃어버렸거나 도난당한 경우입니다.  

        > [!TIP]  
        >  모바일 디바이스에서 원격 초기화 명령을 처리하는 방법에 대한 자세한 내용은 제조업체의 설명서를 확인하세요.  

         대개의 경우 모바일 디바이스에서 초기화 명령을 받을 때까지 지연이 있습니다.  

        -   Configuration Manager 또는 Microsoft Intune에서 모바일 디바이스를 등록한 경우 클라이언트에서 클라이언트 정책을 다운로드할 때 명령을 받습니다.  

        -   Exchange Server 커넥터로 모바일 디바이스를 관리하는 경우 Exchange와 동기화할 때 명령을 받습니다.  

         **Wipe Status**(초기화 상태) 열을 사용하면 장치에서 초기화 명령을 받는 시간을 모니터링할 수 있습니다. 디바이스에서 Configuration Manager로 초기화 승인을 보낼 때까지는 초기화 명령을 취소할 수 있습니다.  

    -   **모바일 장치 사용 중지**  

         **사용 중지** 옵션은 Microsoft Intune 또는 온\-프레미스 모바일 장치 관리에서 등록한 모바일 장치에서만 지원됩니다.  

         자세한 내용은 [System Center Configuration Manager를 사용하여 원격 초기화, 원격 잠금 또는 암호 재설정으로 데이터 보호 지원](../../../mdm/deploy-use/wipe-lock-reset-devices.md)을 참조하세요.  

    -   **장치의 소유권 변경**  

         디바이스가 도메인에 가입되어 있지 않으며 Configuration Manager 클라이언트가 설치되어 있지 않으면 소유권을 **회사** 또는 **개인**으로 변경하는 이 옵션을 사용합니다.  

         응용 프로그램 요구 사항에서 이 값을 사용하여 배포를 제어하고 사용자 디바이스에서 수집되는 인벤토리 수를 제어할 수 있습니다.  

        열 머리글을 마우스 오른쪽 단추로 클릭하고 선택하여 보려는 **Device Owner**(디바이스 소유자) 열을 추가해야 할 수 있습니다.

         자세한 내용은 [System Center Configuration Manager 및 Microsoft Intune에서 하이브리드 MDM(모바일 디바이스 관리)](../../../mdm/understand/hybrid-mobile-device-management.md)을 참조하세요.  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> 장치 컬렉션 노드에서 클라이언트 관리  
  **장치** 노드에서 장치에 사용할 수 있는 많은 작업은 컬렉션에서도 사용할 수 있습니다. 콘솔은 컬렉션에 있는 적격한 모든 디바이스에 자동으로 적용됩니다. 전체 컬렉션에서 이 작업은 추가 네트워크 패킷을 생성하고 사이트 서버에서 CPU 사용량을 증가시킵니다.  

  컬렉션 수준 작업을 수행하기 전에 다음 사항을 고려하세요. 시작하면 콘솔에서 작업을 중지할 수 없습니다. 
 - 컬렉션에 있는 디바이스는 몇 개인가요?
 - 디바이스가 낮은 대역폭 네트워크 연결로 연결되나요?
 - 모든 디바이스에서 이 작업을 완료하는 데 시간이 얼마나 걸리나요?

#### <a name="to-manage-clients-from-the-device-collections-node"></a>디바이스 컬렉션 노드에서 클라이언트를 관리하려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **장치 컬렉션**을 선택합니다.  

3.  컬렉션을 선택한 다음 클라이언트 관리 작업 중 하나를 리본에서 선택하거나 컬렉션을 마우스 오른쪽 단추로 클릭하여 선택합니다. 이러한 클라이언트 관리 작업은 컬렉션 수준에서*만* 수행될 수 있습니다.  

    -   **컴퓨터에서 맬웨어를 검사하고 맬웨어 방지 정의 파일을 다운로드합니다.**  

         [System Center Configuration Manager의 Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md)을 참조하세요.  

    -   **소프트웨어, 구성 기준 및 작업 순서를 배포합니다.**  

         다음을 참조하세요.  

        -   [System Center Configuration Manager에서 소프트웨어 업데이트 배포](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [System Center Configuration Manager에서 준수 설정 계획 및 구성](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **전원 관리 설정을 구성합니다.**  

         [System Center Configuration Manager에서 전원 계획을 만들고 적용하는 방법](../../../core/clients/manage/power/create-and-apply-power-plans.md)을 참조하세요. 전원 계획은 Windows를 실행하는 컴퓨터에서만 사용할 수 있습니다.  

    -   **정책을 최대한 빨리 다운로드하도록 컴퓨터에 알립니다.**  

         클라이언트 정책 폴링 간격이 아니더라도 선택한 Windows 클라이언트에 최대한 빨리 컴퓨터 정책을 다운로드하라고 알리려면 클라이언트 알림을 사용합니다.  

         클라이언트 알림 작업은 **모니터링** 작업 영역의 **클라이언트 작업** 노드에 표시됩니다.  


## <a name="restart-clients"></a>클라이언트 다시 시작
1710 버전부터 Configuration Manager 콘솔을 사용하여 다시 시작해야 하는 클라이언트를 식별할 수 있습니다. 그런 다음 클라이언트 알림 작업을 사용하여 다시 시작합니다.

> [!Tip]
> 이 기능이 작동하려면 1710 버전으로 클라이언트를 업그레이드해야 합니다. 관리 부담을 최소화하여 클라이언트를 최신 상태로 유지하도록 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [자동 클라이언트 업그레이드 사용](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#use-automatic-client-upgrade)을 참조하세요.

다시 시작을 보류한 디바이스를 식별하려면 Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동하고 **디바이스** 노드를 선택합니다. 세부 정보 창의 **다시 시작 보류 중**이라는 새 열에서 각 디바이스에 대한 상태를 확인할 수 있습니다. 각 디바이스에는 다음 값 중 하나 이상이 있습니다. 
 - **아니요**: 다시 시작을 보류하지 않고 있습니다.
 - **Configuration Manager**: 클라이언트 다시 부팅 코디네이터 구성 요소(RebootCoordinator.log)에서 이 값을 가져옵니다.
 - **파일 이름 바꾸기**: Windows에서 보류 중인 파일 이름 바꾸기 작업을 보고하는 이 값을 가져옵니다(HKLM\SYSTEM\CurrentControlSet\Control\Session Manager, PendingFileRenameOperations).
 - **Windows Update**: 보류 중인 다시 시작에 하나 이상의 업데이트가 필요함을 보고하는 Windows Update 에이전트에서 이 값을 가져옵니다(HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\RebootRequired).
 - **기능 추가 또는 제거**: Windows 기능 추가 또는 제거에 다시 시작이 필요함을 보고하는 Windows 구성 요소 기반 서비스에서 이 값을 가져옵니다(HKLM\Software\Microsoft\Windows\CurrentVersion\Component Based Servicing\Reboot Pending).

**장치를 다시 시작하라는 클라이언트 알림을 만들려면**
1.  콘솔의 **디바이스 컬렉션** 노드의 컬렉션 내에서 다시 시작하려는 디바이스를 찾습니다.
2.  해당 디바이스를 마우스 오른쪽 단추로 클릭하고, **클라이언트 알림**을 선택한 다음, **다시 시작**을 선택합니다. 다시 시작에 대한 정보 창이 열립니다. **확인**을 클릭하여 다시 시작 요청을 확인합니다.

클라이언트에서 알림을 받으면 **소프트웨어 센터** 알림 창이 열려 사용자에게 다시 시작을 알려줍니다. 기본적으로 90분 후에 다시 시작됩니다. [클라이언트 설정](/sccm/core/clients/deploy/configure-client-settings)을 구성하여 다시 시작 시간을 수정할 수 있습니다. 다시 시작 동작에 대한 설정은 기본 설정의 [컴퓨터 다시 시작](/sccm/core/clients/deploy/about-client-settings#computer-restart) 탭에 있습니다.


##  <a name="BKMK_ClientCache"></a> Configuration Manager 클라이언트에 대한 클라이언트 캐시 구성  
클라이언트에서 애플리케이션 및 프로그램을 설치할 때 클라이언트 캐시에는 임시 파일이 저장됩니다. 소프트웨어 업데이트도 클라이언트 캐시를 사용하지만 크기 설정에 관계 없이 항상 캐시에 다운로드하려고 시도합니다. 클라이언트를 수동으로 설치하거나, 클라이언트 강제 설치를 사용할 때 또는 클라이언트를 설치한 후에 크기 및 위치와 같은 캐시 설정을 구성합니다.

Configuration Manager 버전 1606부터 Configuration Manager 콘솔에서 클라이언트 설정을 사용하여 캐시 폴더 크기를 지정할 수 있습니다.   

 Configuration Manager 클라이언트 캐시의 기본 위치는 %*windir*%\ccmcache이고 기본 디스크 공간은 5120MB입니다.  

> [!IMPORTANT]  
>  클라이언트 캐시에 사용되는 폴더는 암호화하지 마세요. Configuration Manager는 암호화된 폴더로 콘텐츠를 다운로드할 수 없습니다.  

### <a name="about-client-cache"></a>클라이언트 캐시 정보  

Configuration Manager 클라이언트는 배포를 받자마자 필수 소프트웨어의 콘텐츠를 다운로드하지만 예약된 배포 시간까지 실행하지 않고 기다립니다. 예약된 시간에 Configuration Manager 클라이언트가 캐시에서 콘텐츠를 사용할 수 있는지 여부를 확인합니다. 콘텐츠가 캐시에 있고 올바른 버전이면 클라이언트는 캐시된 콘텐츠를 사용합니다. 필수 버전의 콘텐츠가 변경되었거나 다른 패키지에 필요한 공간을 만들기 위해 클라이언트가 콘텐츠를 삭제한 경우 클라이언트는 해당 콘텐츠를 다시 캐시에 다운로드합니다.  

클라이언트가 캐시 크기보다 큰 애플리케이션이나 프로그램의 콘텐츠를 다운로드하려고 하면 캐시 크기가 부족하여 배포에 실패하게 됩니다. 클라이언트는 부족한 캐시 크기에 대해 상태 메시지 10050을 생성합니다. 나중에 캐시 크기가 늘어날 경우 결과는 다음과 같습니다.  

-   필수 프로그램의 경우: 클라이언트에서 자동으로 콘텐츠를 다시 다운로드하려고 시도하지 않습니다. 클라이언트에 패키지와 프로그램을 다시 배포합니다.  
-   필수 애플리케이션의 경우: 클라이언트에서 클라이언트 정책을 다운로드할 때 자동으로 콘텐츠를 다시 다운로드하려고 시도합니다.  

클라이언트에서 캐시 크기보다 작은 패키지를 다운로드하려고 시도하지만 캐시가 가득 찬 경우 캐시 공간을 사용할 수 있게 되거나, 다운로드 제한 시간이 초과되거나, 다시 시도 수가 제한에 도달할 때까지 모든 필수 배포가 계속 다시 시도됩니다. 나중에 캐시 크기가 늘어나면 Configuration Manager 클라이언트가 다음 다시 시도 간격 때 패키지를 다시 다운로드하려고 시도합니다. 클라이언트는 4시간 간격으로 18회까지 콘텐츠를 다운로드하려고 시도합니다.  

캐시된 콘텐츠는 자동으로 삭제되지 않지만 클라이언트에서 해당 콘텐츠를 사용한 후 최소 하루 동안 캐시에 남아 있습니다. 클라이언트 캐시에 콘텐츠를 유지하는 옵션으로 패키지 속성을 구성하면 클라이언트가 캐시에서 패키지 콘텐츠를 자동으로 삭제하지 않습니다. 최근 24시간 이내에 다운로드된 패키지가 클라이언트 캐시 공간을 사용하고 있는데 클라이언트가 새 패키지를 다운로드해야 하는 경우 캐시 크기를 늘리거나 유지된 캐시 콘텐츠를 삭제하는 삭제 옵션을 선택할 수 있습니다.  

 수동으로 클라이언트를 설치하는 동안이나 클라이언트를 설치한 후에 클라이언트 캐시를 구성하려면 다음 절차를 수행하세요.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>수동 클라이언트 설치를 사용하여 클라이언트를 설치할 때 클라이언트 캐시를 구성하려면  

설치 원본 위치에서 CCMSetup.exe 명령을 실행하고 다음 필수 속성을 공백으로 구분하여 지정합니다.  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > 버전 1606의 경우 SMSCACHESIZE 대신 Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](../../../core/clients/deploy/about-client-settings.md#client-cache-settings)을 참조하세요.

CCMSetup.exe에 이러한 명령줄 속성을 사용하는 방법에 대한 자세한 내용은 [클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>클라이언트 강제 설치를 사용하여 클라이언트를 설치할 때 클라이언트 캐시를 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 선택합니다.  

3.  적절한 사이트를 선택하고 **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정** > **설치 속성 탭**을 선택합니다.  

5.  공백으로 구분된, 다음 속성을 지정합니다.  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > 버전 1606의 경우 SMSCACHESIZE 대신 Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](../../../core/clients/deploy/about-client-settings.md#client-cache-settings)을 참조하세요.

       CCMSetup.exe에 이러한 명령줄 속성을 사용하는 방법에 대한 자세한 내용은 [클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>클라이언트 컴퓨터에 클라이언트 캐시 폴더를 구성하려면  

1.  클라이언트 컴퓨터의 제어판에서 **Configuration Manager**로 이동한 다음 속성을 두 번 클릭하여 엽니다.  

2.  **캐시** 탭에서 공간 및 위치 속성을 설정합니다. 기본 위치는 *%windir%* \ccmcache입니다.  

3.  캐시 폴더의 파일을 삭제하려면 **파일 삭제**를 선택합니다.  

### <a name="to-configure-client-cache-size-in-client-settings"></a>클라이언트 설정에서 클라이언트 캐시 크기를 구성하려면

클라이언트 설정을 사용하는 Configuration Manager 콘솔에서 캐시 크기를 구성하여 클라이언트를 다시 설치하지 않고 클라이언트 캐시의 크기를 조정합니다.  

1. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동합니다.

2. **기본 클라이언트 설정**을 두 번 클릭합니다.
  또한 캐시 크기를 선택적으로 적용하여 사용자 지정 클라이언트 설정을 만들 수도 있습니다. 기본 및 사용자 지정 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.

 3. **클라이언트 캐시 설정**을 선택하고 **클라이언트 캐시 크기 구성**에 대해 **예**를 선택한 다음 **MB** 또는 **percentage of disk settings**(디스크의 백분율 설정)를 사용합니다. 캐시는 어떤 크기로든 작게 조정됩니다.

     Configuration Manager 클라이언트에서는 그 다음 클라이언트 정책을 다운로드할 때 이러한 설정으로 캐시 크기를 구성할 수 있습니다.



##  <a name="BKMK_UninstalClient"></a> Configuration Manager 클라이언트 제거  
 **/Uninstall** 속성을 통해 **CCMSetup.exe**를 사용하여 Windows Configuration Manager 클라이언트 소프트웨어를 제거할 수 있습니다. 명령 프롬프트에서 개별 컴퓨터에 대해 CCMSetup.exe를 실행하거나 컴퓨터의 컬렉션에 대해 클라이언트를 제거하는 패키지 및 프로그램을 배포합니다.  

> [!WARNING]  
>  모바일 디바이스에서는 Configuration Manager 클라이언트를 제거할 수 없습니다. 모바일 디바이스에서 Configuration Manager 클라이언트를 제거해야 하는 경우 디바이스를 초기화해야 합니다. 그러면 모바일 디바이스에서 모든 데이터가 삭제됩니다.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>명령 프롬프트에서 Configuration Manager 클라이언트를 제거하려면  

1.  Windows 명령 프롬프트를 열고 폴더를 CCMSetup.exe가 있는 위치로 변경합니다.  

2.   **Ccmsetup.exe /uninstall**을 입력하고 **Enter**키를 누릅니다  

> [!NOTE]  
>  제거 프로세스는 화면에 결과가 표시되지 않습니다. 클라이언트가 제대로 제거되었는지 확인하려면 클라이언트 컴퓨터의 **%windir%\ ccmsetup** 폴더에서 *CCMSetup.log*라는 로그 파일을 검토합니다.  

##  <a name="BKMK_ConflictingRecords"></a> Configuration Manager 클라이언트에 대한 충돌 레코드 관리  
 Configuration Manager에서는 하드웨어 식별자를 사용하여 중복되었을 수 있는 클라이언트를 식별하고 충돌 레코드에 대해 경고합니다. 예를 들어 컴퓨터를 다시 설치하면 하드웨어 식별자는 동일하지만 Configuration Manager에서 사용하는 GUID는 변경될 수 있습니다.  

 Configuration Manager에서는 신뢰할 수 있는 원본의 컴퓨터 계정이나 PKI 인증서의 Windows 인증을 사용하여 충돌을 자동으로 해결합니다. 그러나 Configuration Manager에서 중복 하드웨어 식별자의 충돌을 해결할 수 없는 경우 계층 설정이 레코드를 자동으로 병합할지 여부를 결정하거나 사용자에게 동작을 결정하도록 허용합니다. 중복된 레코드를 수동으로 관리하려는 경우 Configuration Manager 콘솔에서 충돌 레코드를 수동으로 해결해야 합니다.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>충돌 레코드 관리를 위한 계층 설정을 변경하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트** > **계층 설정**을 선택합니다.
2.  **클라이언트 승인 및 충돌 레코드** 탭에서 **Automatically resolve conflicting records**(충돌 레코드를 자동으로 해결) 또는 **Manually resolve conflicting records**(충돌 레코드를 수동으로 해결)를 선택합니다.  

#### <a name="to-manually-resolve-conflicting-records"></a>충돌 레코드를 수동으로 해결하려면  

1.  Configuration Manager 콘솔에서 선택 **모니터링** > **시스템 상태** > **충돌 레코드**를 선택합니다.  

3.  충돌 레코드를 하나 이상 선택한 다음 **충돌 레코드**를 선택합니다.  

4.  다음 옵션 중 하나를 선택합니다.  

    -   **병합**을 클릭하여 새로 검색된 레코드와 기존 클라이언트 레코드를 결합합니다.  

    -   **새로 만들기** 를 클릭하여 충돌 클라이언트 레코드에 대해 새 레코드를 만듭니다.  

    -   **차단** 을 클릭하여 충돌 클라이언트 레코드에 대해 새 레코드를 만들되, 차단됨으로 표시합니다.  

## <a name="manage-duplicate-hardware-identifiers"></a>중복된 하드웨어 식별자 관리
PXE 부팅 및 클라이언트 등록을 위해 Configuration Manager에서 무시하는 하드웨어 식별자 목록을 제공하면 두 가지 일반적인 문제를 해결할 수 있습니다.

1. Surface Pro 3과 같은 다양한 새 디바이스에는 온보드 이더넷 포트가 포함되어 있지 않습니다. 기술자는 USB-이더넷 어댑터를 사용하여 일반적으로 운영 체제 배포를 위해 유선 연결을 설정합니다. 그러나 비용 및 일반적인 유용성 때문에 이러한 어댑터는 자주 공유됩니다. 이 어댑터의 MAC 주소는 디바이스를 식별하는 데 사용되기 때문에 각 배포 간에 추가 관리자 작업 없이 어댑터를 다시 사용하면 문제가 발생합니다. 이 시나리오에서 어댑터를 다시 사용하려면 해당 MAC 주소를 제외합니다.
2. SMBIOS 특성이 고유해야 하는 반면 일부 특수 하드웨어 디바이스에는 중복 식별자가 있습니다. 이 중복 식별자를 제외하고 각 디바이스에서 고유한 MAC 주소를 사용합니다.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>무시할 Configuration Manager에 대한 하드웨어 식별자를 추가하려면  
1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.
2. **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 선택합니다.
3. **클라이언트 승인 및 충돌 레코드** 탭에서 **Duplicate hardware identifiers**(중복 하드웨어 식별자) 섹션의 **추가**를 선택하여 새 하드웨어 식별자를 추가합니다.

##  <a name="BKMK_PolicyRetrieval"></a> Configuration Manager 클라이언트에 대한 정책 검색 시작  
 Windows Configuration Manager 클라이언트는 클라이언트 설정으로 구성한 일정에 따라 클라이언트 정책을 다운로드합니다. 그러나 클라이언트에서 주문형 정책 검색을 시작하려는 경우(예: 문제 해결 또는 테스트)가 있을 수 있습니다.  

다음을 사용하여 정책 검색을 시작할 수 있습니다.


- [클라이언트 알림](#initiate-client-policy-retrieval-using-client-notification)
- [클라이언트의 **작업** 탭](#manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client)
- [스크립트](#manually-initiate-client-policy-retrieval-by-script)

> [!NOTE]  
>   
>  Linux 및 UNIX를 실행하는 클라이언트의 정책 검색에 대한 자세한 내용은 [Linux 및 UNIX 서버에 대한 컴퓨터 정책](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU)을 참조하세요.  

#### <a name="initiate-client-policy-retrieval-using-client-notification"></a>클라이언트 알림을 사용하여 클라이언트 정책 검색 시작  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **장치 컬렉션**을 선택합니다.  

3.  정책을 다운로드할 컴퓨터가 포함된 디바이스 컬렉션을 선택합니다. **홈** 탭의 **컬렉션** 그룹에서 **클라이언트 알림** > **컴퓨터 정책 다운로드**를 선택합니다.  

    > [!NOTE]  
    >  클라이언트 알림을 사용하여 **디바이스** 노드의 임시 컬렉션 노드에 표시되는 하나 이상의 선택한 디바이스에 대한 정책 검색을 시작할 수도 있습니다.  

#### <a name="manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client"></a>Configuration Manager 클라이언트의 [작업] 탭을 사용하여 수동으로 클라이언트 정책 검색 시작  

1.  컴퓨터의 제어판에서 **Configuration Manager** 를 선택합니다.  

2.  **작업** 탭에서 **컴퓨터 정책 검색 및 평가 주기**를 클릭하여 컴퓨터 정책을 시작한 다음 **지금 실행**을 클릭합니다.  

4.  **확인**을 선택하여 프롬프트를 확인합니다.  

5.  필요한 다른 작업(예: 사용자 클라이언트 설정의 **사용자 정책 검색 및 평가 주기**에 대해서도 3단계와 4단계를 반복합니다.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>스크립트를 사용하여 수동으로 클라이언트 정책 검색 시작  

1.  메모장과 같은 텍스트 편집기를 엽니다.  

2.  다음 샘플 Visual Basic Scripting Edition 코드를 복사하고 파일에 삽입합니다.  

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

    -   명령 프롬프트를 열고 **cscript &lt;경로\파일 이름.vbs>** 를 입력합니다.  

5.  **Windows 스크립트 호스트** 대화 상자에서 **확인**을 선택합니다.  
