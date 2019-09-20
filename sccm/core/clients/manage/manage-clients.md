---
title: 클라이언트 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라이언트를 관리하는 방법을 알아봅니다.
ms.date: 09/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e49d91f3d01d598cb60d99debb52557432bcb2cc
ms.sourcegitcommit: 4316bff400ffbde8404f8a2092ec17e3601b8d29
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70738188"
---
# <a name="how-to-manage-clients-in-configuration-manager"></a>Configuration Manager에서 클라이언트를 관리하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 클라이언트를 디바이스에 설치하고 사이트에 성공적으로 할당하면 **디바이스** 노드의 **자산 및 호환성** 작업 영역과 **디바이스 컬렉션** 노드의 컬렉션 하나 이상에 디바이스가 표시됩니다. 디바이스 또는 컬렉션을 선택한 후 관리 작업을 실행합니다. 그러나 다른 방법으로도 클라이언트를 관리할 수 있습니다. 이 경우 콘솔의 다른 작업 영역을 포함하거나 콘솔의 외부에서 작업을 수행할 수도 있습니다.  

> [!NOTE]  
> 구성 관리자 클라이언트를 설치하지만, 아직 사이트에 할당되지 않은 경우 콘솔에 표시되지 않을 수도 있습니다. 클라이언트를 사이트에 할당한 후에 컬렉션 멤버 자격을 업데이트한 다음, 콘솔 보기를 새로 고칩니다.  
>
> 구성 관리자 클라이언트가 설치되지 않은 경우에도 콘솔에 디바이스가 표시될 수 있습니다. 사이트에서 디바이스를 검색하지만, 클라이언트가 설치 및 할당되지 않은 경우에 이 동작이 발생합니다.
>
> [Exchange Server 커넥터](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync) 또는 [온-프레미스 MDM](/sccm/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)을 사용하여 관리되는 모바일 디바이스는 구성 관리자 클라이언트를 설치하지 않습니다.  
>
> 콘솔에서 디바이스를 관리하려면 **디바이스** 노드의 **클라이언트** 열을 사용하여 클라이언트가 설치되어 있는지 확인합니다.  

## <a name="BKMK_ManagingClients_DevicesNode"></a> **디바이스** 노드에서 클라이언트 관리  

디바이스 유형에 따라 이러한 옵션 중 일부를 사용하지 못할 수도 있습니다.  

1. Configuration Manager 콘솔에서 **자산 및 규정 준수** 작업 영역으로 이동하고 **디바이스** 노드를 선택합니다.  

2. 디바이스를 하나 이상 선택한 후 이 클라이언트 관리 작업 중 하나를 리본에서 선택합니다. 디바이스를 마우스 오른쪽 단추로 클릭할 수도 있습니다.  

### <a name="import-user-device-affinity"></a>사용자 디바이스 선호도 가져오기

사용자에게 소프트웨어를 효율적으로 배포할 수 있도록 사용자와 디바이스 간의 연결을 구성합니다.  

자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.

### <a name="import-computer-information"></a>컴퓨터 정보 가져오기

**컴퓨터 정보 가져오기 마법사**를 시작하여 새 컴퓨터 정보를 Configuration Manager 데이터베이스로 가져옵니다. 파일을 사용하여 여러 컴퓨터를 가져오거나, 단일 컴퓨터의 정보를 지정할 수 있습니다.

### <a name="add-selected-items"></a>선택한 항목 추가

다음 옵션이 제공됩니다.

- **선택한 항목을 기존 디바이스 컬렉션에 추가**: **컬렉션 선택** 대화 상자를 엽니다. 이 디바이스를 추가하려는 컬렉션을 선택합니다. 디바이스는 **직접** 멤버 자격 규칙을 사용하여 이 컬렉션에 포함됩니다.  

- **선택한 항목을 새 디바이스 컬렉션에 추가**: 새 컬렉션을 만들 수 있는 **디바이스 컬렉션 만들기 마법사**를 엽니다. 선택한 컬렉션은 **직접** 멤버 자격 규칙을 사용하여 이 컬렉션에 포함됩니다.  

자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.

### <a name="install-client"></a>클라이언트 설치

**클라이언트 설치 마법사**를 엽니다. 이 마법사는 클라이언트 강제 설치를 사용하여 선택한 디바이스에서 구성 관리자 클라이언트를 설치하거나 다시 설치합니다.

> [!TIP]  
> 구성 관리자 클라이언트를 설치하는 다른 여러 가지 방법이 있습니다. 클라이언트 강제 설치 마법사는 콘솔에서 편리한 클라이언트 설치 방법을 제공하지만, 이 방법은 여러 가지 종속성이 있어 일부 환경에서는 적합하지 않습니다. 종속성에 관한 자세한 내용은 [Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#client-push-installation)을 참조하세요. 다른 클라이언트 설치 방법에 관한 자세한 내용은 [클라이언트 설치 방법](/sccm/core/clients/deploy/plan/client-installation-methods)을 참조하세요.

자세한 내용은 [클라이언트 강제 설치를 사용하여 구성 관리자 클라이언트를 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)을 참조하세요.

### <a name="run-script"></a>스크립트 실행

**스크립트 실행** 마법사를 열고 선택한 디바이스에서 PowerShell 스크립트를 실행합니다.

자세한 내용은 [PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

### <a name="install-application"></a>애플리케이션 설치

실시간으로 디바이스에 애플리케이션을 설치합니다. 이 기능을 사용하면 애플리케이션마다 별도의 컬렉션이 필요하지 않습니다.

자세한 내용은 [디바이스용 애플리케이션 설치](/sccm/apps/deploy-use/install-app-for-device)를 참조하세요.

### <a name="reassign-site"></a>사이트 재할당

관리되는 모바일 디바이스를 포함한 클라이언트를 계층의 다른 기본 사이트에 재할당합니다. 클라이언트를 개별적으로 다시 할당하거나 두 개 이상을 선택하여 대량으로 다시 할당할 수 있습니다.  

### <a name="client-settings---resultant-client-settings"></a>클라이언트 설정 - 결과 클라이언트 설정

같은 디바이스에 여러 클라이언트 설정을 배포한 경우 설정의 우선 순위 및 조합이 복잡합니다. 이 디바이스에 배포된 클라이언트 설정의 결과 세트를 보려면 이 옵션을 사용합니다.

자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.

### <a name="start"></a>시작

- **리소스 탐색기**를 실행하여 Windows 클라이언트에서 하드웨어 및 소프트웨어 인벤토리 정보를 확인합니다. 자세한 내용은 다음 아티클을 참조하세요.

  - [하드웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory)

  - [소프트웨어 인벤토리를 보기 위해 리소스 탐색기를 사용하는 방법](/sccm/core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory)

- **원격 제어**, **원격 지원** 또는 **원격 데스크톱 클라이언트**를 사용하여 디바이스를 원격으로 관리합니다. 자세한 내용은 [Windows 클라이언트 컴퓨터를 원격으로 관리하는 방법](/sccm/core/clients/manage/remote-control/remotely-administer-a-windows-client-computer)을 참조하세요.

### <a name="approve"></a>승인

클라이언트가 HTTP와 자체 서명된 인증서를 사용하여 사이트 시스템과 통신하는 경우 이러한 클라이언트를 승인해야 신뢰할 수 있는 컴퓨터로 식별됩니다. 기본적으로 사이트 구성은 동일한 Active Directory 포리스트 및 신뢰할 수 있는 포리스트의 클라이언트를 자동으로 승인합니다. 이 기본 동작은 각 클라이언트를 수동으로 승인할 필요가 없음을 의미합니다. 신뢰하는 작업 그룹 컴퓨터 및 승인되지 않은 신뢰하는 다른 컴퓨터를 수동으로 승인합니다.

> [!IMPORTANT]  
> 승인되지 않은 클라이언트에 대해서도 일부 관리 기능이 작동할 수 있지만 이는 Configuration Manager에서 지원되지 않는 시나리오입니다.  

항상 HTTPS를 사용하여 사이트 시스템과 통신하는 클라이언트나 HTTP를 사용하여 사이트 시스템과 통신할 때 PKI 인증서를 사용하는 클라이언트는 승인할 필요가 없습니다. 이러한 클라이언트는 PKI 인증서를 사용하여 신뢰 관계를 설정합니다.

### <a name="block-or-unblock"></a>차단 또는 차단 해제

더 이상 신뢰할 수 없는 클라이언트를 차단합니다. 차단하면 클라이언트가 정책을 수신하지 못하도록 방지하고 사이트 시스템이 클라이언트와 통신하지 않도록 방지합니다.  

> [!IMPORTANT]  
> 클라이언트를 차단하면 클라이언트에서 Configuration Manager 사이트 시스템으로 보내는 통신만 차단됩니다. 다른 디바이스로 보내는 통신은 차단되지 않습니다. 클라이언트가 HTTPS 대신 HTTP를 사용하여 사이트 시스템과 통신할 경우 몇 가지 보안 관련 제한 사항이 있습니다.  

차단된 클라이언트를 차단 해제할 수도 있습니다.

자세한 내용은 [클라이언트 차단 여부 결정](/sccm/core/clients/deploy/plan/determine-whether-to-block-clients)을 참조하세요.

<!-- Change Category is a hybrid action -->

### <a name="clear-required-pxe-deployments"></a>필수 PXE 배포 지우기

Configuration Manager 컬렉션 또는 컴퓨터에 할당된 마지막 PXE 배포의 상태를 지우면 필수 PXE 배포를 재배포할 수 있습니다. 이 작업은 해당 배포의 상태를 다시 설정하고 가장 최근의 필수 배포를 다시 설치합니다.

자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.

### <a name="client-notification"></a>클라이언트 알림

자세한 내용은 [클라이언트 알림](/sccm/core/clients/manage/client-notification#client-notification)을 참조하세요.

### <a name="endpoint-protection"></a>Endpoint Protection

자세한 내용은 [클라이언트 알림](/sccm/core/clients/manage/client-notification#endpoint-protection)을 참조하세요.

### <a name="edit-primary-users"></a>기본 사용자 편집

최근 90일 동안 이 디바이스의 사용자를 보거나 이 디바이스의 기본 사용자를 지정합니다.

자세한 내용은 [사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](/sccm/apps/deploy-use/link-users-and-devices-with-user-device-affinity)을 참조하세요.

### <a name="wipe-a-mobile-device"></a>모바일 디바이스 초기화

초기화 명령을 지원하는 모바일 디바이스를 초기화할 수 있습니다. 이 작업은 개인 설정 및 개인 데이터를 포함하여 모바일 디바이스의 모든 데이터를 영구적으로 제거합니다. 일반적으로 이 작업은 모바일 디바이스를 공장 기본값으로 다시 설정합니다. 더 이상 신뢰하지 않는 경우 모바일 디바이스를 초기화합니다. 예를 들어 디바이스를 잃어버렸거나 도난당한 경우입니다.  

> [!TIP]  
> 모바일 디바이스에서 원격 초기화 명령을 처리하는 방법에 대한 자세한 내용은 제조업체의 설명서를 확인하세요.  

대개의 경우 모바일 디바이스에서 초기화 명령을 받을 때까지 지연이 있습니다.  

- Configuration Manager에서 모바일 디바이스를 등록한 경우 클라이언트에서 클라이언트 정책을 다운로드할 때 명령을 받습니다.

- Exchange Server 커넥터로 모바일 디바이스를 관리하는 경우 Exchange와 동기화할 때 명령을 받습니다.  

디바이스에서 초기화 명령을 받는 시간을 모니터링하려면 **초기화 상태** 열을 사용합니다. 디바이스에서 Configuration Manager로 초기화 승인을 보낼 때까지는 초기화 명령을 취소할 수 있습니다.  

### <a name="retire-a-mobile-device"></a>모바일 디바이스 사용 중지

**사용 중지** 옵션은 온-프레미스 MDM에서 등록한 모바일 디바이스에서만 지원됩니다.  

자세한 내용은 [원격 초기화, 원격 잠금 또는 암호 재설정으로 데이터 보호 지원](/sccm/mdm/deploy-use/wipe-lock-reset-devices)을 참조하세요.

### <a name="change-ownership"></a>소유권 변경

디바이스가 도메인에 가입되어 있지 않으며 구성 관리자 클라이언트가 설치되어 있지 않은 경우 소유권을 **회사** 또는 **개인**으로 변경하려면 이 옵션을 사용합니다.  

애플리케이션 요구 사항에서 이 값을 사용하여 배포를 제어하고 사용자 디바이스에서 수집되는 인벤토리 수를 제어할 수 있습니다.  

열 머리글을 마우스 오른쪽 단추로 클릭하고 선택하여 보려는 **Device Owner**(디바이스 소유자) 열을 추가해야 할 수 있습니다.

자세한 내용은 [Hybrid MDM with Configuration Manager and Microsoft Intune](/sccm/mdm/understand/hybrid-mobile-device-management)(Configuration Manager 및 Microsoft Intune에서 하이브리드 MDM)을 참조하세요.

### <a name="delete"></a>삭제

> [!WARNING]  
> 구성 관리자 클라이언트를 제거하거나 컬렉션에서 제거하려면 클라이언트를 삭제하지 마세요.  

**삭제** 작업은 Configuration Manager 데이터베이스에서 클라이언트 레코드를 수동으로 제거합니다. 이 작업은 문제를 해결하는 데만 사용합니다. 개체를 삭제하지만, 클라이언트가 여전히 설치되어 사이트와의 통신하는 경우 하트비트 검색은 클라이언트 레코드를 다시 만듭니다. 클라이언트 기록 및 이전 연결이 모두 손실되지만 이 클라이언트 레코드가 Configuration Manager 콘솔에 다시 나타납니다.  
> [!NOTE]  
> Configuration Manager에서 등록한 모바일 디바이스 클라이언트를 삭제하면 이 작업은 발급된 PKI 인증서도 해지합니다. IIS에서 CRL(인증서 해지 목록)을 확인하지 않아도 이 인증서는 관리 지점에서 거부됩니다.
>
> 모바일 디바이스 기존 클라이언트를 삭제해도 이러한 클라이언트의 인증서는 해지되지 않습니다.

클라이언트를 제거하려면 [구성 관리자 클라이언트 제거](#BKMK_UninstalClient)를 참조하세요.  

새 기본 사이트에 클라이언트를 할당하려면 [사이트에 클라이언트를 할당하는 방법](/sccm/core/clients/deploy/assign-clients-to-a-site)을 참조하세요.

컬렉션에서 클라이언트를 제거하려면 컬렉션 속성을 다시 구성하세요. 자세한 내용은 [컬렉션을 관리하는 방법](/sccm/core/clients/manage/collections/manage-collections)을 참조하세요.

### <a name="refresh"></a>새로 고침

데이터베이스의 최신 데이터로 콘솔 보기를 새로 고칩니다. 예를 들어 검색에서 디바이스가 목록에 나타나지만 설치된 것으로 표시되지 않는 경우입니다. 클라이언트를 설치하고 사이트에 할당되었는지 확인한 후 **새로 고침**을 선택합니다.

### <a name="properties"></a>속성

클라이언트를 대상으로 하는 검색 데이터 및 배포를 볼 수 있습니다.

작업 순서에서 디바이스에 OS를 배포하는 데 사용하는 변수를 구성할 수도 있습니다. 자세한 내용은 [컴퓨터 및 컬렉션에 관한 순서 변수 만들기](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_CreateTSVariables)를 참조하세요.


## <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> **디바이스 컬렉션** 노드에서 클라이언트 관리

**디바이스** 노드에서 디바이스에 사용할 수 있는 많은 작업은 컬렉션에서도 사용할 수 있습니다. 콘솔은 컬렉션에 있는 적격한 모든 디바이스에 자동으로 적용됩니다. 전체 컬렉션에서 이 작업은 추가 네트워크 패킷을 생성하고 사이트 서버에서 CPU 사용량을 증가시킵니다.  

컬렉션 수준 작업을 실행하기 전에 다음 질문을 고려하세요. 시작하면 콘솔에서 작업을 중지할 수 없습니다.

- 컬렉션에 있는 디바이스는 몇 개인가요?
- 디바이스가 낮은 대역폭 네트워크 연결로 연결되나요?
- 모든 디바이스에서 이 작업을 완료하는 데 시간이 얼마나 걸리나요?

자세한 내용은 [컬렉션을 관리하는 방법](/sccm/core/clients/manage/collections/manage-collections)을 참조하세요.


## <a name="restart-clients"></a>클라이언트 다시 시작

Configuration Manager 콘솔을 사용하여 다시 시작이 필요한 클라이언트를 식별합니다. 그런 다음 클라이언트 알림 작업을 사용하여 다시 시작합니다.

> [!Tip]
> 힘을 덜 들이고 클라이언트를 최신 상태로 유지하려면 자동 클라이언트 업그레이드를 사용 설정하세요. 자세한 내용은 [자동 클라이언트 업그레이드 정보](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#bkmk_autoupdate)를 참조하세요.

다시 시작을 보류한 디바이스를 식별하려면 Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동하고 **디바이스** 노드를 선택합니다. 세부 정보 창의 **다시 시작 보류 중**이라는 새 열에서 각 디바이스에 대한 상태를 확인할 수 있습니다. 각 디바이스에는 다음 값 중 하나 이상이 있습니다.

- **아니요**: 다시 시작을 보류하지 않고 있습니다.
- **Configuration Manager**: 클라이언트 다시 부팅 코디네이터 구성 요소(RebootCoordinator.log)에서 이 값을 가져옵니다.
- **파일 이름 바꾸기**: Windows에서 보류 중인 파일 이름 바꾸기 작업을 보고하는 이 값을 가져옵니다(HKLM\SYSTEM\CurrentControlSet\Control\Session Manager, PendingFileRenameOperations).
- **Windows Update**: 보류 중인 다시 시작에 하나 이상의 업데이트가 필요함을 보고하는 Windows Update 에이전트에서 이 값을 가져옵니다(HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\RebootRequired).
- **기능 추가 또는 제거**: Windows 기능 추가 또는 제거에 다시 시작이 필요함을 보고하는 Windows 구성 요소 기반 서비스에서 이 값을 가져옵니다(HKLM\Software\Microsoft\Windows\CurrentVersion\Component Based Servicing\Reboot Pending).

### <a name="create-the-client-notification-to-restart-a-device"></a>디바이스를 다시 시작하라는 클라이언트 알림 만들기

1. 콘솔의 **디바이스 컬렉션** 노드의 컬렉션 내에서 다시 시작하려는 디바이스를 선택합니다.
2. 리본에서 **클라이언트 알림**을 선택한 후 **다시 시작**을 선택합니다. 다시 시작에 대한 정보 창이 열립니다. **확인**을 선택하여 다시 시작 요청을 확인합니다.

클라이언트에서 알림을 받으면 **소프트웨어 센터** 알림 창이 열려 사용자에게 다시 시작을 알려줍니다. 기본적으로 90분 후에 다시 시작됩니다. [클라이언트 설정](/sccm/core/clients/deploy/configure-client-settings)을 구성하여 다시 시작 시간을 수정할 수 있습니다. 다시 시작 동작에 대한 설정은 기본 설정의 [컴퓨터 다시 시작](/sccm/core/clients/deploy/about-client-settings#computer-restart) 탭에 있습니다.


## <a name="BKMK_ClientCache"></a> 클라이언트 캐시 구성

클라이언트에서 애플리케이션 및 프로그램을 설치할 때 클라이언트 캐시에는 임시 파일이 저장됩니다. 소프트웨어 업데이트도 클라이언트 캐시를 사용하지만 크기 설정에 관계 없이 항상 캐시에 다운로드하려고 시도합니다. 클라이언트를 수동으로 설치하거나, 클라이언트 강제 설치를 사용할 때 또는 클라이언트를 설치한 후에 크기 및 위치와 같은 캐시 설정을 구성합니다.

Configuration Manager 콘솔에서 클라이언트 설정을 사용하여 캐시 폴더 크기를 지정할 수 있습니다. 자세한 내용은 [클라이언트 캐시 설정](/sccm/core/clients/deploy/about-client-settings#client-cache-settings)을 참조하세요.

구성 관리자 클라이언트 캐시의 기본 위치는 `%windir%\ccmcache`이고 기본 디스크 공간은 5120MB입니다.  

> [!IMPORTANT]  
> 클라이언트 캐시에 사용되는 폴더는 암호화하지 마세요. Configuration Manager는 암호화된 폴더로 콘텐츠를 다운로드할 수 없습니다.  

### <a name="about-the-client-cache"></a>클라이언트 캐시 정보  

Configuration Manager 클라이언트는 배포를 받자마자 필수 소프트웨어의 콘텐츠를 다운로드하지만 예약된 배포 시간까지 실행하지 않고 기다립니다. 예약된 시간에 Configuration Manager 클라이언트가 캐시에서 콘텐츠를 사용할 수 있는지 여부를 확인합니다. 콘텐츠가 캐시에 있고 올바른 버전이면 클라이언트는 캐시된 콘텐츠를 사용합니다. 필수 버전의 콘텐츠가 변경되었거나 다른 패키지에 필요한 공간을 만들기 위해 클라이언트가 콘텐츠를 삭제한 경우 클라이언트는 해당 콘텐츠를 다시 캐시에 다운로드합니다.  

클라이언트가 캐시 크기보다 큰 애플리케이션이나 프로그램의 콘텐츠를 다운로드하려고 하면 캐시 크기가 부족하여 배포에 실패하게 됩니다. 클라이언트는 부족한 캐시 크기에 대해 상태 메시지 10050을 생성합니다. 나중에 캐시 크기가 늘어날 경우 결과는 다음과 같습니다.  

- 필수 프로그램의 경우: 클라이언트에서 자동으로 콘텐츠를 다시 다운로드하려고 시도하지 않습니다. 클라이언트에 패키지와 프로그램을 다시 배포합니다.  
- 필수 애플리케이션의 경우: 클라이언트에서 클라이언트 정책을 다운로드할 때 자동으로 콘텐츠를 다시 다운로드하려고 시도합니다.  

클라이언트에서 캐시 크기보다 작은 패키지를 다운로드하려고 시도하지만, 캐시가 가득 찬 경우 다음 시기까지 모든 ‘필수’ 배포가 계속 다시 시도됩니다. 

- 캐시 공간을 사용할 수 있을 때까지
- 다운로드 제한 시간이 초과될 때까지
- 다시 시도 수가 제한에 도달할 때까지

나중에 캐시 크기를 늘리면 클라이언트가 다음 다시 시도 간격 때 패키지를 다시 다운로드하려고 시도합니다. 클라이언트는 4시간 간격으로 18회까지 콘텐츠를 다운로드하려고 시도합니다.  

캐시된 콘텐츠는 자동으로 삭제되지 않습니다. 클라이언트에서 해당 콘텐츠를 사용한 후 최소 하루 동안 캐시에 남아 있습니다. 클라이언트 캐시에 콘텐츠를 유지하는 옵션으로 패키지 속성을 구성하면 클라이언트가 해당 콘텐츠를 자동으로 삭제하지 않습니다. 최근 24시간 이내에 다운로드된 패키지가 클라이언트 캐시 공간을 사용하고 있는데 클라이언트가 새 패키지를 다운로드해야 하는 경우 캐시 크기를 늘리거나 유지된 캐시 콘텐츠를 삭제하는 삭제 옵션을 선택합니다.  

수동으로 클라이언트를 설치하는 동안이나 클라이언트를 설치한 후에 클라이언트 캐시를 구성하려면 다음 절차를 수행하세요.  

### <a name="configure-the-cache-during-manual-client-installation"></a>수동으로 클라이언트를 설치하는 동안 캐시 구성  

설치 원본 위치에서 CCMSetup.exe 명령을 실행하고 다음 필수 속성을 공백으로 구분하여 지정합니다.  

- DISABLECACHEOPT  

  - SMSCACHEDIR  

  - SMSCACHEFLAGS  

  - SMSCACHESIZE  

    > [!NOTE]
    > SMSCACHESIZE 대신 Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](/sccm/core/clients/deploy/about-client-settings#client-cache-settings)을 참조하세요.

CCMSetup.exe에 이러한 명령줄 속성을 사용하는 방법에 대한 자세한 내용은 [클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.

### <a name="configure-the-cache-during-client-push-installation"></a>클라이언트를 강제 설치하는 동안 캐시 구성  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 해당하는 사이트를 선택합니다. 리본의 **홈** 탭에 있는 **설정** 그룹에서 **클라이언트 설치 설정**, **클라이언트 강제 설치**를 차례로 선택합니다. **설치 속성** 탭으로 전환합니다.  

3. 공백으로 구분된, 다음 속성을 지정합니다.  

   - DISABLECACHEOPT  

   - SMSCACHEDIR  

   - SMSCACHEFLAGS  

   - SMSCACHESIZE  

     > [!NOTE]
     > SMSCACHESIZE 대신 Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](/sccm/core/clients/deploy/about-client-settings#client-cache-settings)을 참조하세요.

     CCMSetup.exe에 이러한 명령줄 속성을 사용하는 방법에 대한 자세한 내용은 [클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

### <a name="configure-the-cache-on-the-client-computer"></a>클라이언트 컴퓨터에서 캐시 구성  

1. 클라이언트 컴퓨터에서 **Configuration Manager** 제어판을 엽니다.  

2. **캐시** 탭으로 전환합니다. 공간 및 위치 속성을 설정합니다. 기본 위치는 `%windir%\ccmcache`입니다.  

3. 캐시 폴더의 파일을 삭제하려면 **파일 삭제**를 선택합니다.  

### <a name="configure-client-cache-size-in-client-settings"></a>클라이언트 설정에서 클라이언트 캐시 크기 구성

클라이언트를 다시 설치하지 않고 클라이언트 캐시의 크기를 조정합니다. Configuration Manager 콘솔의 **클라이언트 설정**에서 사용할 수 있는 캐시 크기 설정을 사용합니다. 자세한 내용은 [클라이언트 캐시 설정](/sccm/core/clients/deploy/about-client-settings#client-cache-settings)을 참조하세요.


## <a name="BKMK_UninstalClient"></a> 클라이언트 제거

**/Uninstall** 속성을 통해 **CCMSetup.exe**를 사용하여 구성 관리자 클라이언트 소프트웨어를 제거할 수 있습니다. 명령 프롬프트에서 개별 컴퓨터에 대해 CCMSetup.exe를 실행하거나 컴퓨터의 컬렉션에 대해 클라이언트를 제거하는 패키지를 배포합니다.  

> [!NOTE]  
> 모바일 디바이스에서는 구성 관리자 클라이언트를 제거할 수 없습니다. 모바일 디바이스에서 Configuration Manager 클라이언트를 제거해야 하는 경우 디바이스를 초기화해야 합니다. 그러면 모바일 디바이스에서 모든 데이터가 삭제됩니다.  

1. 관리자 권한으로 Windows 명령 프롬프트를 엽니다. 폴더를 CCMSetup.exe가 있는 위치(예: `cd %windir%\ccmsetup`)로 변경합니다.

2. 다음 명령을 실행합니다. `CCMSetup.exe /uninstall`

> [!TIP]  
> 제거 프로세스는 화면에 결과가 표시되지 않습니다. 클라이언트가 제거되었는지 확인하려면 다음 로그 파일을 참조하세요. `%windir%\ccmsetup\logs\CCMSetup.log`  
>
> 다른 작업을 위해 제거 프로세스가 완료되도록 기다려야 할 경우 PowerShell에서 `Wait-Process CCMSetup`을 실행합니다. 이 명령은 CCMSetup 프로세스가 완료될 때까지 스크립트를 일시 중지할 수 있습니다.


## <a name="BKMK_ConflictingRecords"></a> 충돌 레코드 관리

Configuration Manager에서는 하드웨어 식별자를 사용하여 중복되었을 수 있는 클라이언트를 식별하고 충돌 레코드에 대해 경고합니다. 예를 들어 컴퓨터를 다시 설치하면 하드웨어 식별자는 동일하지만 Configuration Manager에서 사용하는 GUID는 변경될 수 있습니다.  

Configuration Manager에서는 신뢰할 수 있는 원본의 컴퓨터 계정이나 PKI 인증서의 Windows 인증을 사용하여 충돌을 자동으로 해결합니다. Configuration Manager에서 중복 하드웨어 식별자의 충돌을 해결할 수 없는 경우 계층 설정에 따라 동작이 결정됩니다.

### <a name="change-the-hierarchy-setting-for-managing-conflicting-records"></a>충돌 레코드 관리를 위한 계층 설정 변경  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.

1. 리본에서 **계층 구조 설정**을 선택합니다.

1. **클라이언트 승인 및 충돌 레코드** 탭으로 전환하고 다음 옵션 중 하나를 선택합니다.

    - **충돌 레코드를 자동으로 해결**
    - **충돌 레코드를 수동으로 해결**

### <a name="manually-resolve-conflicting-records"></a>충돌 레코드를 수동으로 해결  

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고, **시스템 상태**를 확장하고, **충돌 레코드** 노드를 선택합니다.  

1. 충돌 레코드를 하나 이상 선택한 다음 **충돌 레코드**를 선택합니다.  

1. 다음 옵션 중 하나를 선택합니다.  

    - **병합**: 새로 검색된 레코드와 기존 클라이언트 레코드를 결합합니다.  

    - **새로 만들기**: 충돌 클라이언트 레코드에 대해 새 레코드를 만듭니다.  

    - **차단**: 충돌 클라이언트 레코드에 대해 새 레코드를 만들되, 차단됨으로 표시합니다.  


## <a name="manage-duplicate-hardware-identifiers"></a>중복된 하드웨어 식별자 관리

Configuration Manager에서 PXE 부팅 및 클라이언트 등록을 위해 무시하는 하드웨어 식별자 목록을 제공할 수 있습니다. 이 목록은 다음과 같은 두 가지 일반적인 문제를 해결하는 데 도움이 됩니다.

1. 다양한 새 디바이스에는 온보딩 이더넷 포트가 포함되어 있지 않습니다. 기술자는 USB-이더넷 어댑터를 사용하여 일반적으로 OS 배포를 위해 유선 연결을 설정합니다. 비용 및 일반적인 유용성 때문에 이러한 어댑터는 자주 공유됩니다. 사이트는 이 어댑터의 MAC 주소를 사용하여 디바이스를 식별합니다. 따라서 각 배포 간에 추가 관리자 작업 없이 어댑터를 다시 사용하면 문제가 발생합니다. 이 시나리오에서 어댑터를 다시 사용하려면 해당 MAC 주소를 제외합니다.

2. SMBIOS 특성이 고유해야 하는 반면 일부 특수 하드웨어 디바이스에는 중복 식별자가 있습니다. 이 중복 식별자를 제외하고 각 디바이스에서 고유한 MAC 주소를 사용합니다.

다음 프로세스를 사용하여 무시할 Configuration Manager에 관한 하드웨어 식별자를 추가합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.

2. 리본의 **홈** 탭에 있는 **사이트** 그룹에서 **계층 설정**을 선택합니다.

3. **클라이언트 승인 및 충돌 레코드** 탭으로 전환합니다. 새 하드웨어 식별자를 추가하려면 **중복 하드웨어 식별자** 섹션에서 **추가**를 선택합니다.


## <a name="BKMK_PolicyRetrieval"></a> 정책 검색 시작

구성 관리자 클라이언트는 클라이언트 설정으로 구성하는 일정에 따라 클라이언트 정책을 다운로드합니다. 클라이언트에서 요청 시 정책 검색을 시작할 수도 있습니다. 예를 들어 문제를 해결하거나 테스트하는 경우입니다.  

- [클라이언트 알림](#bkmk_policy-notify)
- [클라이언트 제어판](#bkmk_policy-manual)
- [지원 센터](#bkmk_policy-support)
- [스크립트](#bkmk_policy-script)

### <a name="bkmk_policy-notify"></a> 클라이언트 알림을 사용하여 클라이언트 정책 검색 시작  

1. Configuration Manager 콘솔에서 **자산 및 규정 준수** 작업 영역으로 이동하고 **디바이스**를 선택합니다.  

1. 정책을 다운로드하려는 디바이스를 선택합니다. 리본의 **홈** 탭에 있는 **디바이스** 그룹에서 **클라이언트 알림**, **컴퓨터 정책 다운로드**를 차례로 선택합니다.  

    > [!NOTE]  
    > 클라이언트 알림을 사용하여 컬렉션의 모든 디바이스에 대해 정책 검색을 시작할 수도 있습니다.  

### <a name="bkmk_policy-manual"></a> 구성 관리자 클라이언트 제어판에서 클라이언트 정책 검색 시작

1. 컴퓨터에서 **Configuration Manager** 제어판을 엽니다.  

2. **작업** 탭으로 전환합니다. **머신 정책 검색 및 평가 주기**를 선택하여 컴퓨터 정책을 시작한 후 **지금 실행**을 선택합니다.  

3. **확인**을 선택하여 프롬프트를 확인합니다.  

4. 다른 작업에 대해 이전 단계를 반복합니다. 예를 들어 사용자 클라이언트 설정에 대해 **사용자 정책 검색 및 평가 주기**를 반복합니다.  

### <a name="bkmk_policy-support"></a> 지원 센터를 사용하여 클라이언트 정책 검색 시작

지원 센터를 사용하여 클라이언트 정책을 요청하고 확인합니다. 자세한 내용은 [지원 센터 참조](/sccm/core/support/support-center-ui-reference#bkmk_support-policy)를 참조하세요.

### <a name="bkmk_policy-script"></a> 스크립트를 사용하여 클라이언트 정책 검색 시작  

1. 메모장 또는 Windows PowerShell ISE와 같은 스크립트 편집기를 엽니다.  

2. 다음 샘플 PowerShell 코드를 복사하고 다음 파일에<!-- SCCMDocs#1591 --> 삽입합니다.  

    ```PowerShell
    $trigger = "{00000000-0000-0000-0000-000000000021}"
    Invoke-WmiMethod -Namespace root\ccm -Class sms_client -Name TriggerSchedule $trigger
    ```  

    > [!TIP]
    > 일정 ID에 관한 자세한 내용은 [메시지 ID](/sccm/core/support/send-schedule-tool#bkmk_sendschedule-guids)를 참조하세요.

3. .ps1 확장명으로 파일을 저장합니다.  

4. 클라이언트에서 스크립트를 실행합니다.
