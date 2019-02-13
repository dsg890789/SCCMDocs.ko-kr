---
title: '모바일 장치 관리 '
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 Exchange Server 커넥터를 사용하여 모바일 디바이스를 관리합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: aba688d9-fd5b-4c42-8cb4-f7e1b161ef50
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a157e8696a9b4b24acb722be037185351f94ccdc
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56127884"
---
# <a name="manage-mobile-devices-with-system-center-configuration-manager-and-exchange"></a>System Center Configuration Manager와 Exchange를 사용하여 모바일 디바이스 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Exchange ActiveSync 프로토콜을 사용하여 Exchange Server(온-프레미스 또는 온라인)에 연결하는 모바일 디바이스를 관리하려고 하며 Configuration Manager를 사용하여 해당 디바이스를 등록할 수 없는 경우 System Center Configuration Manager에서 Exchange Server 커넥터를 사용합니다. Configuration Manager 콘솔에서 여러 Exchange 서버에 대한 설정 제어 및 원격 디바이스 초기화와 같은 Exchange 모바일 디바이스 관리 기능을 구성할 수 있습니다.  

 ![configmgr&#45;with&#45;exchange](../../mdm/deploy-use/media/configmgr-with-exchange.png "configmgr-with-exchange")  

 Exchange Server 커넥터를 사용하여 모바일 디바이스를 관리하는 경우 모바일 디바이스에 Configuration Manager 클라이언트가 설치되지 않습니다. 따라서 일부 관리 기능이 제한됩니다. 예를 들어 소프트웨어를 해당 디바이스에 설치할 수 없거나 구성 항목을 사용하여 해당 디바이스를 구성할 수 없습니다. Configuration Manager와 함께 모바일 디바이스에 사용할 수 있는 다양한 관리 기능에 대한 자세한 내용은 [System Center Configuration Manager용 디바이스 관리 솔루션 선택](../../core/plan-design/choose-a-device-management-solution.md)을 참조하세요.  

> [!IMPORTANT]  
>  Exchange Server 커넥터를 설치하기 전에 사용 중인 Microsoft Exchange 버전이 Configuration Manager에서 지원되는지 확인합니다. 자세한 내용은 [System Center Configuration Manager의 사이트 및 클라이언트에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)에서 "Exchange Server 커넥터"를 참조하세요.  

 Exchange Server 커넥터를 사용하는 경우 모바일 디바이스를 기본 Exchange ActiveSync 사서함 정책으로 관리하는 대신 Configuration Manager에서 구성한 설정으로 관리할 수 있습니다. 다음 그룹 설정에서 사용 하려는 설정을 정의 합니다. **일반**, **암호**, **메일 관리**, **Security**, 및 **응용 프로그램**합니다. 예를 들어 **암호** 그룹 설정에서, 모바일 디바이스에서 암호를 요구할 것인지 여부, 최소 암호 길이, 암호 복잡도, 암호 복구 허용 여부를 구성할 수 있습니다.  

 그룹에 하나 이상의 설정을 구성하면 Configuration Manager가 모바일 디바이스에 대한 그룹의 모든 설정을 관리합니다. 특정 그룹에서 어떤 설정도 구성하지 않으면 Exchange가 모바일 디바이스의 이러한 설정을 계속 관리합니다. Exchange Server에 구성되어 사용자에게 할당된 모든 Exchange ActiveSync 사서함 정책은 여전히 적용됩니다.  

 또한 Exchange 액세스 규칙을 관리하고 모바일 디바이스를 허용 또는 차단하거나 격리하도록 Exchange Server 커넥터를 구성할 수도 있습니다. 관리자는 Configuration Manager 콘솔을 사용하여 모바일 장치를 원격으로 초기화할 수 있으며, 사용자는 애플리케이션 카탈로그를 사용하여 모바일 장치를 원격으로 초기화할 수 있습니다.  

 사용자의 모바일 장치가 Exchange Server 커넥터를 통해 관리되고 Exchange Server가 온-프레미스 버전인 경우 사용자의 모바일 장치가 애플리케이션 카탈로그에 자동으로 표시됩니다. Microsoft Exchange Online에 대해 Exchange Server 커넥터를 구성하는 경우 사용자의 모바일 장치가 애플리케이션 카탈로그에 표시되도록 사용자 장치 선호도를 수동으로 구성해야 합니다. 사용자 디바이스 선호도를 수동으로 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 사용자 디바이스 선호도를 사용하여 사용자와 디바이스 연결](../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)을 참조하세요.  

> [!TIP]  
>  Exchange Server 커넥터를 사용하여 모바일 디바이스를 관리하고 모바일 디바이스가 다른 사용자에게 양도되는 경우 모바일 디바이스의 새 소유자가 양도된 모바일 디바이스에 자신의 Exchange 계정을 구성하기 전에 Configuration Manager 콘솔에서 모바일 디바이스를 삭제합니다.  

## <a name="required-security-permissions"></a>필요한 보안 권한  
 Exchange Server 커넥터를 구성하려면 다음 보안 권한이 있어야 합니다.  

- 추가, 수정 및 Exchange Server 커넥터를 삭제 합니다. **사이트** 개체에 대한 **수정** 권한이 필요합니다.  

- 모바일 장치 설정을 구성 하려면: **ModifyConnectorPolicy** 에 대 한 권한을 합니다 **사이트** 개체입니다.  

  **전체 관리자** 보안 역할에는 Exchange Server 커넥터를 구성하기 위해 필요한 권한이 포함됩니다.  

  모바일 디바이스를 관리하려면 다음 보안 권한이 있어야 합니다.  

- 모바일 장치를 초기화 합니다. **컬렉션** 개체에 대한 **리소스 삭제** 권한이 필요합니다.  

- 초기화 명령 취소: **컬렉션** 개체에 대한 **리소스 수정** 권한이 필요합니다.  

- 허용 하 고 모바일 장치를 차단 합니다. **컬렉션** 개체에 대한 **리소스 수정** 권한이 필요합니다.  

  **운영 관리자** 보안 역할에는 Exchange Server 커넥터를 사용하여 모바일 디바이스를 관리하기 위해 필요한 권한이 포함됩니다.  

  보안 권한을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에 대한 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.  

## <a name="installing-and-configuring-an-exchange-server-connector"></a>Exchange Server 커넥터 설치 및 구성  
 다음 절차에 따라 Exchange Server 커넥터를 설치하고 모바일 디바이스를 관리하도록 구성합니다. Configuration Manager는 Exchange 조직의 커넥터를 하나만 지원합니다. 이러한 단계를 완료한 후에는 모바일 디바이스가 표시된 컬렉션을 확인하고 모바일 디바이스에 대한 보고서를 사용하여 커넥터로 검색 및 관리되는 모바일 디바이스를 모니터링할 수 있습니다.  

> [!NOTE]  
>  Configuration Manager는 *사용자 이름*_*디바이스 유형* 형식을 사용하여 검색되는 모바일 디바이스에 대한 이름을 생성합니다. 사용자에게 동일한 디바이스 유형의 모바일 디바이스가 둘 이상 있는 경우 Configuration Manager가 콘솔과 보고서에 이러한 모바일 디바이스를 동일한 이름으로 표시합니다.  

#### <a name="to-install-and-configure-an-exchange-server-connector"></a>Exchange Server 커넥터를 설치하고 구성하려면  

1.  모바일 디바이스를 관리하도록 Exchange Client Access 서버에 연결할 계정을 결정합니다. 계정은 사이트 서버의 컴퓨터 계정이거나 Windows 사용자 계정일 수 있습니다. 그러고 나서 다음 Exchange Server cmdlet을 실행하도록 이 계정을 구성합니다.  

    -   **Clear-ActiveSyncDevice**  

    -   **Get-ActiveSyncDevice**  

    -   **Get-ActiveSyncDeviceAccessRule**  

    -   **Get-ActiveSyncDeviceStatistics**  

    -   **Get-ActiveSyncMailboxPolicy**  

    -   **Get-ActiveSyncOrganizationSettings**  

    -   **Get-ExchangeServer**  
    
    -   **Get-Mailbox**
    
    -   **Get-Recipient**  

    -   **Set-ADServerSettings**  

    -   **Set-ActiveSyncDeviceAccessRule**  

    -   **Set-ActiveSyncMailboxPolicy**  

    -   **Set-CASMailbox**  

    -   **New-ActiveSyncDeviceAccessRule**  

    -   **New-ActiveSyncMailboxPolicy**  

    -   **Remove-ActiveSyncDevice**  
    
    -   **Get-CasMailbox**  
    
    -   **Get-User**  
    
    -   **Set-ActiveSyncOrganizationSettings**  

    > [!NOTE]  
    >  이러한 cmdlet를 포함 하는 다음 Exchange Server 관리 역할: 받는 사람 관리, 보기 전용 조직 관리 및 서버 관리 합니다. Microsoft Exchange Server2010의 관리 역할 그룹에 대한 자세한 내용은 [관리 역할 그룹 이해](http://go.microsoft.com/fwlink/p/?LinkId=212914)를 참조하십시오.  

    > [!TIP]  
    >  필수 cmdlet 없이 Exchange Server 커넥터를 설치하거나 사용하려고 하면 사이트 서버 컴퓨터의 EasDisc.log 로그 파일에 `Invoking cmdlet <cmdlet> failed` 메시지와 함께 로깅된 오류가 표시됩니다.  

2.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

3.  **관리** 작업 영역에서 **계층 구성**을 확장하고 **Exchange Server 커넥터**를 클릭합니다.  

4.  **홈** 탭의 **만들기** 그룹에서 **Exchange Server 추가**를 클릭합니다.  

5.  Exchange Server 추가 마법사를 완료합니다.  

    -   Exchange Server의 온-프레미스 인스턴스를 사용하고 클라이언트 액세스 서버를 지정하는 경우 각 Active Directory 사이트에 대해 단일 서버 또는 클라이언트 액세스 서버 배열을 지정할 수 있습니다. 서버 또는 배열이 오프라인인 경우 Configuration Manager에서 사용할 클라이언트 액세스 서버를 검색합니다. 검색하지 못하는 경우 Configuration Manager가 사서함 서버 사용으로 대체되어 클라이언트 액세스 서버에 연결합니다. 다시 시도하면 사이트 서버 컴퓨터의 EasDisc.log 파일에 경고로 로깅됩니다. 예를 들어 `Failed to open runspace for site <site_name>`을 검색합니다.  

    -   Exchange Server 커넥터 계정에 1단계에서 구성한 계정을 지정합니다.  

    -   또한 Configuration Manager를 사용하여 모바일 디바이스를 등록하는 경우 해당 모바일 디바이스가 Configuration Manager에서 등록된 후에도 Exchange의 메일을 계속 받도록 **외부 모바일 디바이스 관리** 옵션을 사용하도록 설정합니다.  

    -   마법사의 **계정** 페이지에서 Configuration Manager 조건부 액세스에 의해 차단되는 클라이언트로 메일 알림을 보내는 데 사용되는 계정을 구성할 수 있습니다. 이 경우 Exchange 서버에 유효한 사서함이 있는 계정을 지정해야 합니다.  

         자세한 내용은 [System Center Configuration Manager에서 서비스에 대한 액세스 관리](../../protect/deploy-use/manage-access-to-services.md)를 참조하세요.  

6.  상태 메시지를 사용하고 로그 파일을 검토하여 Exchange Server 커넥터가 설치되었는지 확인할 수 있습니다.  

    -   사이트 구성 요소 관리자에서 Exchange Server 커넥터를 설치했는지 확인하려면 **SMS_EXCHANGE_CONNECTOR** 구성 요소의 상태 ID **1015** 를 찾아보십시오. Configuration Manager에서 커넥터를 설치할 수 없는 경우, 예를 들어 지정한 클라이언트 액세스 서버 컴퓨터가 오프라인 상태라서 설치할 수 없는 경우 Configuration Manager에서 설치에 성공하거나 사용자가 Exchange Server 커넥터를 제거할 때까지 60분마다 다시 설치하려고 시도합니다.  

    -   사이트 서버 컴퓨터에서 SiteComp.log 파일을 검색한 후 이 로그 파일에서 `Component SMS_EXCHANGE_CONNECTOR flagged for installation`을 검색합니다. 설치가 완료되면 `STATMSG: ID=1015`텍스트가 기록됩니다.  
