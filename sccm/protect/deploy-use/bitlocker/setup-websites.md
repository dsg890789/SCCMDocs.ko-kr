---
title: BitLocker 포털 설정
titleSuffix: Configuration Manager
description: 셀프 서비스 포털에 대 한 BitLocker 관리 구성 요소와 administration and monitoring 웹 사이트를 설치 합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 1cd8ac9f-b7ba-4cf4-8cd2-d548b0d6b1df
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e2b0c71dfd93fd264e900b6a42952cf3c80374b1
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74662351"
---
# <a name="set-up-bitlocker-portals"></a>BitLocker 포털 설정

*적용 대상: Configuration Manager (현재 분기)*

<!--3601034-->

Configuration Manager에서 다음 BitLocker 관리 구성 요소를 사용 하려면 먼저 해당 구성 요소를 설치 해야 합니다.

- 사용자 셀프 서비스 포털
- Administration and monitoring 웹 사이트 (기술 지원팀 포털)

IIS를 사용 하 여 기존 사이트 서버에 포털을 설치 하거나 독립 실행형 웹 서버를 사용 하 여 포털을 호스트할 수 있습니다.

> [!NOTE]
> 버전 1910에서는 기본 사이트 데이터베이스를 사용 하 여 셀프 서비스 포털과 administration and monitoring 웹 사이트만 설치 합니다. 계층에서 각 기본 사이트에 대해 이러한 웹 사이트를 설치 합니다.

시작 하기 전에 이러한 구성 요소에 대 한 [필수](/configmgr/protect/plan-design/bitlocker-management#prerequisites) 구성 요소를 확인 합니다.

## <a name="script-usage"></a>스크립트 사용량

이 프로세스는 PowerShell 스크립트, MBAMWebSiteInstaller.ps1을 사용하여 웹 서버에 이 구성 요소를 설치합니다. 다음 매개 변수를 허용합니다.

- `-SqlServerName <ServerName>` (필수): 기본 사이트 데이터베이스 서버의 정규화 된 도메인 이름입니다.

- `-SqlInstanceName <InstanceName>`: 기본 사이트 데이터베이스의 SQL Server 인스턴스 이름입니다. SQL에서 기본 인스턴스를 사용하는 경우 이 매개 변수는 선택 사항입니다.

- `-SqlDatabaseName <DatabaseName>` (필수): 기본 사이트 데이터베이스의 이름입니다 (예: `CM_ABC`.

- `-ReportWebServiceUrl <ReportWebServiceUrl>`: 기본 사이트의 보고 서비스 지점의 웹 서비스 URL입니다. **Reporting Services 구성 관리자**의 **웹 서비스 URL** 값입니다.

    > [!NOTE]
    > 이 매개 변수는 administration and monitoring 웹 사이트에서 연결 된 **복구 감사 보고서** 를 설치 하는 것입니다. 기본적으로 Configuration Manager에는 다른 BitLocker 관리 보고서가 포함 됩니다.

- `-HelpdeskUsersGroupName <DomainUserGroup>`: 예: `contoso\BitLocker help desk users`. 구성원이 Administration and Monitoring 웹 사이트의 **TPM 관리** 및 **드라이브 복구** 영역에 액세스할 수 있는 도메인 사용자 그룹입니다. 이러한 옵션을 사용하는 경우, 이 역할은 사용자의 도메인 및 계정 이름을 비롯한 모든 필드를 입력해야 합니다.

- `-HelpdeskAdminsGroupName <DomainUserGroup>`: 예: `contoso\BitLocker help desk admins`. 구성원이 관리 및 모니터링 웹 사이트의 모든 복구 영역에 액세스할 수 있는 도메인 사용자 그룹입니다. 사용자가 드라이브를 복구할 수 있도록 지원하는 경우 이 역할은 복구 키만 입력하면 됩니다.

- `-MbamReportUsersGroupName <DomainUserGroup>`: 예: `contoso\BitLocker report users`. 구성원이 관리 및 모니터링 웹 사이트의 **보고서** 영역에 읽기 전용으로 액세스할 수 있는 도메인 사용자 그룹입니다.

- `-SiteInstall Both`: 설치할 구성 요소를 지정합니다. 유효한 선택 사항은 다음과 같습니다.
  - `Both`: 두 구성 요소 모두 설치
  - `HelpDesk`: administration and monitoring 웹 사이트만 설치
  - `SSP`: 셀프 서비스 포털만 설치

- `IISWebSite`: 스크립트가 MBAM 웹 애플리케이션을 설치하는 웹 사이트입니다. 기본적으로 IIS 기본 웹 사이트를 사용합니다.

- `InstallDirectory`: 스크립트에서 웹 애플리케이션 파일을 설치하는 경로입니다. 기본적으로 이 경로는 `C:\inetpub`입니다.

## <a name="run-the-script"></a>스크립트 실행

대상 웹 서버에서 다음 작업을 수행 합니다.

> [!NOTE]
> 사이트 디자인에 따라 스크립트를 여러 번 실행 해야 할 수도 있습니다. 예를 들어 관리 지점에서 스크립트를 실행 하 여 administration and monitoring 웹 사이트를 설치 합니다. 그런 다음 독립 실행형 웹 서버에서 다시 실행 하 여 셀프 서비스 포털을 설치 합니다.

1. 사이트 서버의 Configuration Manager 설치 폴더에 있는 `SMSSETUP\BIN\X64`에서 다음 파일을 대상 서버의 로컬 폴더로 복사 합니다.

    - `MBAMWebSite.cab`
    - `MBAMWebSiteInstaller.ps1`

1. 관리자 권한으로 PowerShell을 실행한 후, 다음 명령줄과 비슷한 스크립트를 실행합니다.

    ``` PowerShell
    .\MBAMWebSiteInstaller.ps1 -SqlServerName <ServerName> -SqlInstanceName <InstanceName> -SqlDatabaseName <DatabaseName> -ReportWebServiceUrl <ReportWebServiceUrl> -HelpdeskUsersGroupName <DomainUserGroup> -HelpdeskAdminsGroupName <DomainUserGroup> -MbamReportUsersGroupName <DomainUserGroup> -SiteInstall Both
    ```

    예를 들어

    ``` PowerShell
    .\MBAMWebSiteInstaller.ps1 -SqlServerName sql.contoso.com -SqlInstanceName instance1 -SqlDatabaseName CM_ABC -ReportWebServiceUrl https://rsp.contoso.com/ReportServer -HelpdeskUsersGroupName "contoso\BitLocker help desk users" -HelpdeskAdminsGroupName "contoso\BitLocker help desk admins" -MbamReportUsersGroupName "contoso\BitLocker report users" -SiteInstall Both
    ```

설치 후에 다음 URL을 통해 포털에 액세스합니다.

- 셀프 서비스 포털: `https://webserver.contoso.com/SelfService`
- Administration and monitoring 웹 사이트: `https://webserver.contoso.com/HelpDesk`

> [!NOTE]
> Microsoft에서 HTTPS를 사용하는 것을 권장하며 이는 필수 사항은 아닙니다. 자세한 내용은 [IIS에서 SSL을 설정하는 방법](https://docs.microsoft.com/iis/manage/configuring-security/how-to-set-up-ssl-on-iis)을 참조하세요.

## <a name="verify"></a>확인

다음 로그를 사용하여 모니터링하고 문제를 해결합니다.

- **Microsoft windows-MBAM-Web**아래에 있는 Windows 이벤트 로그입니다. 자세한 내용은 [BitLocker 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/about-event-logs) 및 [서버 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/server-event-logs)정보를 참조 하세요.

- 각 구성 요소에 대 한 추적 로그의 기본 위치는 다음과 같습니다.

  - 셀프 서비스 포털: `C:\inetpub\Microsoft BitLocker Management Solution\Logs\Self Service Website`

  - Administration and monitoring 웹 사이트: `C:\inetpub\Microsoft BitLocker Management Solution\Logs\Help Desk Website`

문제 해결에 대 한 자세한 내용은 [BitLocker 문제 해결](/configmgr/protect/tech-ref/bitlocker/troubleshoot)을 참조 하세요.

## <a name="next-steps"></a>다음 단계

[셀프 서비스 포털 사용자 지정](/configmgr/protect/deploy-use/bitlocker/customize-self-service-portal)

설치한 구성 요소를 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [BitLocker administration and monitoring 웹 사이트](/configmgr/protect/deploy-use/bitlocker/helpdesk-portal)
- [BitLocker 셀프 서비스 포털](/configmgr/protect/deploy-use/bitlocker/self-service-portal)
