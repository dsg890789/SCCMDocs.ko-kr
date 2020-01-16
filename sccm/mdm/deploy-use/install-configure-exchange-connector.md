---
title: Exchange Connector 설치
titleSuffix: Configuration Manager
description: ActiveSync를 통해 모바일 장치를 관리 하도록 Configuration Manager 용 Exchange connector를 설치 하 고 구성 합니다.
ms.date: 12/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: e179e30a-a1fc-461e-8087-ff3a55803450
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7d064b440922eb6994b2f761833f27a1d9590f34
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76037082"
---
# <a name="install-and-configure-the-exchange-connector"></a>Exchange connector 설치 및 구성

*적용 대상: Configuration Manager (현재 분기)*

이 절차를 사용 하 여 모바일 장치를 관리 하도록 Exchange Server 커넥터를 설치 및 구성할 수 있습니다. Configuration Manager는 Exchange 조직의 커넥터를 하나만 지원합니다.

Configuration Manager 용 Exchange Server 커넥터를 설치 하기 전에 필요한 사용 권한 및 버전이 있는지 확인 합니다. 자세한 내용은 [Exchange를 사용한 장치 관리 및 Configuration Manager](/configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync#prerequisites)을 참조 하세요.

## <a name="exchange-connection-account"></a>Exchange 연결 계정

모바일 디바이스를 관리하도록 Exchange Client Access 서버에 연결할 계정을 결정합니다. 계정은 사이트 서버의 컴퓨터 계정이거나 Windows 사용자 계정일 수 있습니다.

그런 다음 exchange 역할 그룹에서이 계정을 구성 하 여 다음 Exchange Server cmdlet을 실행 합니다.

- **Clear-ActiveSyncDevice**  

- **Get-ActiveSyncDevice**  

- **Get-ActiveSyncDeviceAccessRule**  

- **Get-ActiveSyncDeviceStatistics**  

- **Get-ActiveSyncMailboxPolicy**  

- **Get-ActiveSyncOrganizationSettings**  

- **Get-ExchangeServer**  

- **Get-Mailbox**

- **Get-Recipient**  

- **Set-ADServerSettings**  

- **Set-ActiveSyncDeviceAccessRule**  

- **Set-ActiveSyncMailboxPolicy**  

- **Set-CASMailbox**  

- **New-ActiveSyncDeviceAccessRule**  

- **New-ActiveSyncMailboxPolicy**  

- **Remove-ActiveSyncDevice**  

- **Get-CasMailbox**  

- **Get-User**  

- **Set-ActiveSyncOrganizationSettings**  

이러한 cmdlet이 포함되는 Exchange Server 관리 역할은

- 받는 사람 관리
- 보기 전용 조직 관리
- 서버 관리

자세한 내용은 Exchange Server 2013 설명서의 [관리 역할 그룹 이해](https://docs.microsoft.com/exchange/understanding-management-role-groups-exchange-2013-help) 를 참조 하십시오.

> [!TIP]  
> 필수 cmdlet 없이 Exchange Server 커넥터를 설치 하거나 사용 하려고 하면 사이트 서버 컴퓨터의 디스크 파일 (`Invoking cmdlet <cmdlet> failed`)에 다음과 같은 오류가 표시 됩니다.

## <a name="install-the-connector"></a>커넥터 설치

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동 하 고 **계층 구성**을 확장 한 다음 **Exchange Server 커넥터**를 선택 합니다.

1. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **Exchange Server 추가**를 선택 합니다.

1. Exchange Server 추가 마법사의 **일반** 페이지에서 exchange server 환경 중 하나를 선택 합니다.

    - **온-프레미스 Exchange Server**: 각 Active Directory 사이트에 대해 단일 서버 또는 클라이언트 액세스 서버 배열을 지정 합니다.

        서버 또는 배열이 오프라인인 경우 Configuration Manager에서 사용할 클라이언트 액세스 서버를 검색합니다. 검색하지 못하는 경우 Configuration Manager가 사서함 서버 사용으로 대체되어 클라이언트 액세스 서버에 연결합니다. 연결을 다시 시도 하면 사이트 서버 컴퓨터의 `Failed to open runspace for site <site_name>`에 대 한 로그 파일에 다음과 같은 경고가 기록 됩니다.

    - **호스트 된 Exchange server**: exchange Online 환경의 서버 주소를 지정 합니다.

    그런 다음 기본 사이트를 선택 하 여 Exchange Server 커넥터를 실행 합니다.

1. **계정** 페이지에서 Exchange 서버에 연결할 계정을 지정 합니다. 자세한 내용은 [Exchange 연결 계정](#exchange-connection-account)을 참조 하세요.

1. **검색** 페이지에서 장치를 찾기 위한 동기화 일정 및 규칙을 구성 합니다.

1. **설정** 페이지에서 다음 그룹의 모바일 장치 설정을 구성 합니다.

    - **일반**
    - **암호**
    - **전자 메일 관리**
    - **Security**
    - **애플리케이션**

    자세한 내용은 [Exchange 커넥터 설정](/configmgr/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync#policies)을 참조 하세요.

    Configuration Manager [온-프레미스 MDM](/configmgr/mdm/understand/manage-mobile-devices-with-on-premises-infrastructure)을 사용 하 여 모바일 장치를 등록 하는 경우 **외부 모바일 장치 관리를 허용**하는 옵션을 사용 하도록 설정 합니다. 이 설정을 통해 이러한 모바일 장치는 Configuration Manager 등록 한 후에도 계속 Exchange에서 전자 메일을 받을 수 있습니다.

1. 마법사 완료

## <a name="verify-and-monitor"></a>확인 및 모니터링

상태 메시지 및 로그 파일이 포함 된 Exchange Server 커넥터 설치를 확인 합니다.

- 사이트 구성 요소 관리자 Exchange Server 커넥터를 성공적으로 설치 했는지 확인 합니다. **SMS_EXCHANGE_CONNECTOR** 구성 요소에서 메시지 상태 ID **1015** 을 찾습니다.

    지정 된 클라이언트 액세스 서버가 오프 라인인 경우 설치에 실패할 수 있습니다. Configuration Manager 커넥터를 설치할 수 없는 경우 Configuration Manager는 60 분 마다 설치를 다시 시도 합니다. 설치가 성공 하거나 Exchange Server 커넥터를 제거할 때까지 계속 해 서 다시 시도 합니다.

- 사이트 서버 컴퓨터에서 다음 항목에 대 한 **Sitecomp .log** 를 검토 합니다. `Component SMS_EXCHANGE_CONNECTOR flagged for installation`. 그런 다음 `STATMSG: ID=1015`텍스트를 사용 하 여 성공적인 설치를 로깅합니다.

설치를 완료 한 후 커넥터에서 찾아서 관리 하는 모바일 장치를 모니터링 합니다. 모바일 장치의 컬렉션을 확인 하 고 모바일 장치에 대 한 보고서를 사용 합니다.

> [!NOTE]  
> Configuration Manager는 검색 된 모바일 장치에 대 한 이름을 생성 합니다. *사용자 이름*_*장치 유형*형식을 사용 합니다. 예를 들어 **jdoe_WindowsPhone**합니다. 사용자에게 동일한 디바이스 유형의 모바일 디바이스가 둘 이상 있는 경우 Configuration Manager가 콘솔과 보고서에 이러한 모바일 디바이스를 동일한 이름으로 표시합니다.  

## <a name="see-also"></a>참고 항목

- [구성 클라이언트 및 사이트 시스템에 사용 되는 포트](/configmgr/core/plan-design/hierarchy/ports#BKMK_PortsExchangeConnectorHosted)
- [프록시 서버 지원](/configmgr/core/plan-design/network/proxy-server-support#site-system-roles-that-use-a-proxy)
- [모바일 장치에 대 한 보안 권장 사항](/configmgr/core/clients/deploy/plan/security-and-privacy-for-clients#bkmk_mobile)
- [Exchange Server 커넥터로 관리 되는 모바일 장치에 대 한 개인 정보](/configmgr/core/clients/deploy/plan/security-and-privacy-for-clients#BKMK_Privacy_ExchangeConnector)
