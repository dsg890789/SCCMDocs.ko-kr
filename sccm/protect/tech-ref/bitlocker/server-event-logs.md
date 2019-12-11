---
title: 서버 이벤트 로그
titleSuffix: Configuration Manager
description: Windows 이벤트 로그에서 가능한 BitLocker (MBAM) 서버 항목에 대 한 기술 참조
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: c3279b7d-654d-444b-bd17-1262894590c3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 54f6ec4442e729db4dd5c9d4d02f5903babb5f47
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74662501"
---
# <a name="server-event-logs"></a>서버 이벤트 로그

*적용 대상: Configuration Manager (현재 분기)*

<!--3601034-->

Windows 이벤트 뷰어를 사용 하 여 Configuration Manager의 다음 BitLocker 관리 서버 구성 요소에 대 한 이벤트 로그를 볼 수 있습니다.

- 관리 지점의 복구 서비스
- 셀프 서비스 포털
- 웹 사이트 관리 및 모니터링

하나 이상의 이러한 구성 요소를 호스트 하는 서버에서 이벤트 뷰어를 엽니다. 그런 다음 **응용 프로그램 및 서비스 로그**, **Microsoft**, **Windows**로 이동 하 고 **mbam-Web**을 확장 합니다. 기본적으로 [관리](#admin) 및 [운영](#operational) 이벤트 로그가 있습니다.

다음 섹션에는 BitLocker 관리 서버 구성 요소에서 발생할 수 있는 이벤트 Id에 대 한 메시지 및 문제 해결 정보가 포함 되어 있습니다.

## <a name="admin"></a>관리

### <a name="1-webappspnerror"></a>1: WebAppSpnError

응용 프로그램: {SiteName} {VirtualDirectory}에 다음 Spn (서비스 사용자 이름)이 없습니다. {ListOfSpns} 계정에 필요한 Spn을 등록 합니다. {ExecutionAccount}.

Windows 통합 인증을 성공적으로 수행 하려면 필요한 Spn을 준비 해야 합니다. 이 메시지는 응용 프로그램에 필요한 SPN이 올바르게 구성 되지 않았음을 나타냅니다. 이 이벤트에 포함 된 세부 정보는 자세한 정보를 제공 해야 합니다.

<!-- See “Service Principal Name (SPN)” in MBAM 2.5 Server Prerequisites for Stand-alone and Configuration Manager Integration Topologies for more information. -->

### <a name="100-adminservicerecoverydberror"></a>100: AdminServiceRecoveryDbError

가능한 오류 메시지:

- GetMachineUsers: 데이터베이스에서 사용자 정보를 가져오는 동안 오류가 발생 했습니다.
- GetRecoveryKey: 데이터베이스에서 복구 키를 가져오는 동안 오류가 발생 했습니다.
- GetRecoveryKey: 데이터베이스에서 사용자 정보를 가져오는 동안 오류가 발생 했습니다.
- GetRecoveryKeyIds: 데이터베이스에서 복구 키 Id를 가져오는 동안 오류가 발생 했습니다.
- GetTpmHashForUser: 복구 데이터베이스에서 TPM 해시 데이터를 가져오는 동안 오류가 발생 했습니다.
- GetTpmHashForUser: 복구 데이터베이스에서 TPM 해시 데이터를 가져오는 동안 오류가 발생 했습니다.
- Querydriverec과잉 Ydata: 데이터베이스에서 드라이브 복구 데이터를 가져오는 동안 오류가 발생 했습니다.
- QueryRecoveryKeyIdsForUser: 데이터베이스에서 복구 키 Id를 가져오는 동안 오류가 발생 했습니다.
- QueryVolumeUsers: 데이터베이스에서 사용자 정보를 가져오는 동안 오류가 발생 했습니다.

이 메시지는 복구 데이터베이스와 통신 하는 동안 예외가 발생할 때마다 기록 됩니다. 예외에 대 한 구체적인 정보를 얻으려면 추적에 포함 된 정보를 읽습니다.

### <a name="101-adminservicecompliancedberror"></a>101: AdminServiceComplianceDbError

가능한 오류 메시지:

- GetRecoveryKey: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.
- GetRecoveryKeyIds: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.
- GetTpmHashForUser: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.
- QueryRecoveryKeyIdsForUser: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.
- Querydriverec과잉 Ydata: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.

이 메시지는 준수 데이터베이스와 통신 하는 동안 예외가 발생할 때마다 기록 됩니다. 예외에 대 한 구체적인 정보를 얻으려면 추적에 포함 된 정보를 읽습니다.

### <a name="102-agentservicerecoverydberror"></a>102: AgentServiceRecoveryDbError

이 메시지는 서비스가 복구 데이터베이스와 통신 하려고 할 때 발생 하는 예외를 나타냅니다. 예외에 대 한 특정 정보를 얻기 위해 이벤트에 포함 된 메시지를 읽습니다.

MBAM 앱 풀 계정에 복구 데이터베이스에 연결 하는 데 필요한 권한이 있는지 확인 합니다.

### <a name="103-agentserviceerror"></a>103: AgentServiceError

가능한 오류 메시지:

- 클라이언트 컴퓨터 계정 또는 데이터 마이그레이션 사용자 계정을 검색할 수 없습니다.

    `PostKeyRecoveryInfo`, `IsRecoveryKeyResetRequired`, `CommitRecoveryKeyRest`또는 `GetTpmHash` 웹 메서드가 호출 될 때마다 호출자 컨텍스트를 검색 하 여 호출자 자격 증명을 가져옵니다. 호출자 컨텍스트가 null 이거나 비어 있으면 서비스는이 메시지를 기록 합니다.

- 호출자 id에 대 한 계정을 확인 하지 못했습니다.

    이 메시지는 웹 메서드가 호출자를 컴퓨터 계정으로 예상 하 고 있지 않은 경우에 기록 됩니다. 웹 메서드가 호출자를 사용자 계정으로 예상 하 고 사용자 계정이 나 데이터 마이그레이션 그룹 계정의 구성원이 아닌 경우에도 발생할 수 있습니다.

### <a name="104-statusservicecompliancedbconfigerror"></a>104: StatusServiceComplianceDbConfigError

레지스트리의 준수 데이터베이스 연결 문자열이 비어 있습니다.

이 메시지는 준수 db 연결 문자열이 잘못 될 때마다 기록 됩니다. `HKLM\Software\Microsoft\MBAM Server\Web\ComplianceDBConnectionString`레지스트리 키에서 값을 확인 합니다.

### <a name="105-statusservicecompliancedberror"></a>105: StatusServiceComplianceDbError

이 오류는 웹 사이트 또는 웹 서비스에서 준수 데이터베이스에 연결할 수 없음을 나타냅니다. IIS 응용 프로그램 풀 계정이 데이터베이스에 연결할 수 있는지 확인 합니다.

### <a name="106-helpdeskerror"></a>106: HelpdeskError

알려진 오류 및 가능한 원인:

- URL에 대 한 요청에서 내부 오류가 발생 했습니다.

    관리 및 모니터링 웹 사이트 (기술 지원팀)의 응용 프로그램에서 처리 되지 않은 예외가 발생 했습니다. **관리** 이벤트 로그의 로그 항목을 검토 하 여 특정 예외를 확인 합니다.

- 실행 컨텍스트 정보를 가져오는 동안 오류가 발생 했습니다. SPN (서비스 사용자 이름) 등록을 확인할 수 없습니다.

    초기 기술 지원팀 웹 사이트 로드 작업 중에 SPN을 확인 합니다. SPN을 확인 하려면 기술 지원팀 웹 사이트에 해당 하는 계정 정보, IIS Sitename 및 ApplicationVirtualPath이 필요 합니다. 이러한 특성 중 하나 이상이 잘못 되었거나 누락 된 경우이 오류 메시지를 기록 합니다.

- SPN (서비스 사용자 이름) 등록을 확인 하는 동안 오류가 발생 했습니다.

    이 메시지는 SPN을 확인할 때 보안 예외가 throw 됨을 나타냅니다. 이벤트 정보에 포함 된 예외를 참조 하세요.

### <a name="107-selfserviceportalerror"></a>107: SelfServicePortalError

알려진 오류 및 가능한 원인:

- 사용자에 대 한 복구 키를 가져오는 동안 오류가 발생 했습니다.

    복구 키를 검색 하기 위해 요청을 수행할 때 예기치 않은 예외가 throw 되었음을 나타냅니다. 이벤트 세부 정보에서 예외 메시지를 참조 하십시오. 기술 지원팀 앱에서 추적을 사용 하는 경우 자세한 예외 메시지를 얻으려면 추적 데이터를 참조 하세요.

- 실행 컨텍스트 정보를 가져오는 동안 오류가 발생 했습니다. SPN (서비스 사용자 이름) 등록을 확인할 수 없습니다.

    초기 로드 작업을 수행 하는 동안 셀프 서비스 포털은 셀프 서비스 웹 사이트에서 SPN을 확인 하는 계정 정보, IIS Sitename 및 ApplicationVirtualPath를 검색 합니다. 이러한 특성 중 하나 이상이 올바르지 않으면이 오류 메시지가 기록 됩니다.

- SPN (서비스 사용자 이름) 등록을 확인 하는 동안 오류가 발생 했습니다. EventDetails: {ExceptionMessage}

    이 메시지는 SPN을 확인 하는 동안 보안 예외가 throw 되었음을 나타냅니다. 이벤트 정보에 포함 된 예외를 참조 하세요.

### <a name="108-domaincontrollererror"></a>108: DomainControllerError

알려진 오류 및 가능한 원인:

- 도메인 이름 {DomainName}을 (를) 확인 하는 동안 오류가 발생 했습니다. 메모리 할당 오류가 발생 했습니다.

    도메인 이름을 확인 하기 위해 `DsGetDcName` Windows API를 호출 합니다. 이 메시지는이 API가 메모리 할당 오류를 나타내는 `ERROR_NOT_ENOUGH_MEMORY`를 반환할 때 기록 됩니다.

- DsGetDcName 메서드를 호출할 수 없습니다.

    이 메시지는 `DsGetDcName` API를 호스트에서 사용할 수 없음을 나타냅니다.

### <a name="109-webapprecoverydberror"></a>109: WebAppRecoveryDbError

알려진 오류 및 가능한 원인:

- 복구 데이터베이스의 구성을 읽는 동안 오류가 발생 했습니다. 복구 데이터베이스에 대 한 연결 문자열이 구성 되지 않았습니다.

    이 메시지는 `HKLM\Software\Microsoft\MBAM Server\Web\RecoveryDBConnectionString`의 복구 데이터베이스 연결 문자열 정보가 잘못 되었음을 나타냅니다. 지정 된 레지스트리 키 값을 확인 합니다.

다음 메시지가 표시 되는 경우 IIS 서버의 앱 풀 자격 증명이 복구 데이터베이스에 연결할 수 있는지 확인 합니다.

- DoesUserHaveMatchingRecoveryKey: 사용자에 대 한 복구 키 Id를 가져오는 동안 오류가 발생 했습니다.
- Querydriverec과잉 Ydata: 드라이브 복구 데이터를 가져오는 동안 오류가 발생 했습니다.
- QueryRecoveryKeyIdsForUser: 사용자의 복구 키 Id를 가져오는 동안 오류가 발생 했습니다.
- 복구 데이터베이스에서 TPM 암호 해시를 가져오는 동안 오류가 발생 했습니다.

### <a name="110-webappcompliancedberror"></a>110: WebAppComplianceDbError

알려진 오류 및 가능한 원인:

- 준수 데이터베이스의 구성을 읽는 동안 오류가 발생 했습니다. 준수 데이터베이스에 대 한 연결 문자열이 구성 되지 않았습니다.

    이 메시지는 `HKLM\Software\Microsoft\MBAM Server\Web\ComplianceDBConnectionString`의 호환 데이터베이스 연결 문자열 정보가 잘못 되었음을 나타냅니다. 이 레지스트리 키의 값을 확인 하십시오.

다음 메시지가 표시 되는 경우 IIS 서버의 앱 풀 자격 증명이 준수 데이터베이스에 연결할 수 있는지 확인 합니다.

- GetRecoveryKeyForCurrentUser: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.
- QueryRecoveryKeyIdsForUser: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.
- QueryRecoveryKeyIdsForUser: 규정 준수 데이터베이스에 감사 이벤트를 로깅하는 동안 오류가 발생 했습니다.

### <a name="111-webappdberror"></a>111: WebAppDbError

이러한 오류는 다음 두 조건 중 하나를 나타냄

- MBAM websites/webservices가 준수 또는 복구 데이터베이스에 연결 하지 못했습니다.
- MBAM websites/webservices 실행 계정 (앱 풀 계정)이 준수 또는 복구 데이터베이스에 대 한 `GetVersion` 저장 프로시저를 실행 하지 못했습니다.

이벤트에 포함 된 메시지는 예외에 대 한 자세한 정보를 제공 합니다.

앱 풀 계정이 준수 또는 복구 데이터베이스에 연결할 수 있는지 확인 합니다. `GetVersion` 저장 프로시저를 실행할 수 있는 권한이 있는지 확인 하십시오.

### <a name="112-webapperror"></a>112: WebAppError

SPN (서비스 사용자 이름) 등록을 확인 하는 동안 오류가 발생 했습니다.

SPN을 확인 하려면 Active Directory을 쿼리하여 Spn이 매핑된 실행 계정 목록을 검색 합니다. 또한 `ApplicationHost.config`를 쿼리하여 웹 사이트 바인딩을 가져옵니다. 이 오류 메시지는 Active Directory와 통신할 수 없거나 `ApplicationHost.config` 파일을 로드할 수 없음을 나타냅니다.

앱 풀 계정에 Active Directory 또는 `ApplicationHost.config` 파일을 쿼리할 수 있는 권한이 있는지 확인 합니다. 또한 `ApplicationHost.config` 파일에서 사이트 바인딩 항목을 확인 합니다.

## <a name="operational"></a>운영

### <a name="4-performancecountererror"></a>4: PerformanceCounterError

성능 카운터를 검색 하는 동안 오류가 발생 했습니다.

추적 메시지에는 실제 예외 메시지가 포함 되어 있으며, 그 중 일부는 여기에 나열 되어 있습니다.

- ArgumentNullException: 요청 된 성능 카운터의 범주, 카운터 또는 인스턴스가 잘못 된 경우이 예외가 throw 됩니다.
- InvalidOperationException: 범주는 빈 문자열 ("")입니다. counterName은 빈 문자열 ("")입니다.
- 요청 된 읽기/쓰기 권한 설정이이 카운터에 대해 잘못 되었습니다.
- 지정 된 범주가 없습니다 (readOnly가 true 인 경우).
- 지정 된 범주가 .NET Framework 사용자 지정 범주가 아닙니다 (readOnly가 false 인 경우).
- 지정 된 범주가 다중 인스턴스로 표시 되어 있고 인스턴스 이름을 사용 하 여 성능 카운터를 만들어야 합니다.
- instanceName이 127 자 보다 깁니다.
- 범주 및 counterName 다른 언어로 지역화 되었습니다.
- System.componentmodel. System.componentmodel.win32exception: 시스템 API에 액세스 하는 동안 오류가 발생 했습니다.
- System.unauthorizedaccessexception: 관리자 권한 없이 실행 되는 코드에서 성능 카운터를 읽으려고 했습니다.

이벤트의 메시지는 예외에 대 한 자세한 정보를 제공 합니다.

`System.UnauthorizedAccessException`의 경우 응용 프로그램 풀 계정에 성능 카운터 Api에 대 한 액세스 권한이 있는지 확인 합니다.

### <a name="200-helpdeskinformation"></a>200: HelpDeskInformation

관리 웹 사이트 응용 프로그램을 찾아서 지원 되는 버전의 복구/준수 데이터베이스에 연결 했습니다.

기술 지원팀 웹 사이트의 복구 또는 준수 데이터베이스 연결에 성공 했음을 나타냅니다.

### <a name="201-selfserviceportalinformation"></a>201: SelfServicePortalInformation

셀프 서비스 포털 응용 프로그램을 찾아서 지원 되는 버전의 복구/규정 준수 데이터베이스에 연결 했습니다.

셀프 서비스 포털에서 복구 또는 준수 데이터베이스에 성공적으로 연결 되었음을 나타냅니다.

### <a name="202-webappinformation"></a>202: WebAppInformation

응용 프로그램의 Spn이 올바르게 등록 되어 있습니다.

는 기술 지원팀 웹 사이트에 필요한 Spn이 실행 계정에 대해 올바르게 등록 되었음을 나타냅니다.

## <a name="see-also"></a>참고 항목

이러한 로그를 사용 하는 방법에 대 한 자세한 내용은 [BitLocker 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/about-event-logs)를 참조 하세요.

문제 해결에 대 한 자세한 내용은 [BitLocker 문제 해결](/configmgr/protect/tech-ref/bitlocker/troubleshoot)을 참조 하세요.

이러한 웹 사이트를 설치 하는 방법에 대 한 자세한 내용은 [BitLocker 보고서 및 포털 설정](/configmgr/protect/deploy-use/bitlocker/setup-websites)을 참조 하세요.
