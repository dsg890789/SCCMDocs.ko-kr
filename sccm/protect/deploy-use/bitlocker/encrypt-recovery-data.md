---
title: 복구 데이터 암호화
titleSuffix: Configuration Manager
description: ''
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 1ee6541a-e243-43ea-be16-d0349f7f0c6e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2d1bf84178c5b130d6fe1aa7d7b7e7cb9fd66878
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75820834"
---
# <a name="encrypt-recovery-data"></a>복구 데이터 암호화

*적용 대상: Configuration Manager(현재 분기)*

<!--3601034-->

BitLocker 관리 정책을 만들 때 Configuration Manager는 HTTPS 사용 관리 지점에 복구 서비스를 배포 합니다. Bitlocker 관리 정책의 **클라이언트 관리** 페이지에서 **bitlocker 관리 서비스를 구성할**때 클라이언트는 키 복구 정보를 사이트 데이터베이스에 백업 합니다. 이 정보에는 BitLocker 복구 키, 복구 패키지 및 TPM 암호 해시가 포함 됩니다.

사용자가 보호 된 장치에서 잠긴 경우이 정보를 사용 하 여 장치에 대 한 액세스를 복구할 수 있습니다. 이 정보의 중요 한 특성에 따라 사이트 데이터베이스에서이 데이터를 암호화 하는 것이 좋습니다.

이 문서에서는 사용자 고유의 인증서를 사용 하 여 SQL Server 셀 수준 암호화를 사용 하는 방법을 설명 합니다.

BitLocker 관리 암호화 인증서를 만들지 않으려면 복구 데이터의 일반 텍스트 저장소를 옵트인 (opt in) 합니다. BitLocker 관리 정책을 만들 때 **복구 정보를 일반 텍스트로 저장 하도록 허용**하는 옵션을 사용 하도록 설정 합니다.

> [!NOTE]
> 또 다른 보안 계층은 전체 사이트 데이터베이스를 암호화 하는 것입니다. 데이터베이스에서 암호화를 사용 하도록 설정 하면 Configuration Manager에 기능 문제가 없습니다.
>
> 특히 대규모 환경에서는 암호화를 주의 깊게 사용해야 합니다. 암호화 하는 테이블 및 SQL 버전에 따라 25% 성능 저하가 발생할 수 있습니다. 암호화 된 데이터를 성공적으로 복구할 수 있도록 백업 및 복구 계획을 업데이트 합니다.

## <a name="certificate-requirements"></a>인증서 요구 사항

사용자 고유의 프로세스를 사용 하 여 다음 요구 사항을 충족 하는 한 BitLocker 관리 암호화 인증서를 만들고 배포할 수 있습니다.

- BitLocker 관리 암호화 인증서의 이름은 `BitLockerManagement_CERT`이어야 합니다.

- 데이터베이스 마스터 키를 사용 하 여이 인증서를 암호화 합니다.

- 다음 SQL 사용자는 인증서에 대 한 **Control** 권한이 필요 합니다.
  - Recoveryand하드
  - RecoveryAndHardwareRead
  - RecoveryAndHardwareWrite

- 계층의 모든 사이트 데이터베이스에 동일한 인증서를 배포 합니다.

- 사용자 환경에서 최신 버전의 SQL Server를 사용 하 여 인증서를 만듭니다. 예를 들면 다음과 같습니다.
  - SQL Server 2016 이상에서 만든 인증서는 SQL Server 2014 이전 버전과 호환 됩니다.
  - SQL Server 2014 이전 버전에서 만든 인증서는 SQL Server 2016 이상과 호환 되지 않습니다.

## <a name="example-scripts"></a>샘플 스크립트

이러한 SQL 스크립트는 Configuration Manager 사이트 데이터베이스에 BitLocker 관리 암호화 인증서를 만들고 배포 하는 예입니다.

### <a name="create-certificate"></a>인증서 만들기

이 샘플 스크립트는 다음 작업을 수행 합니다.

- 인증서를 만듭니다.
- 권한을 설정합니다.
- 데이터베이스 마스터 키를 만듭니다.

프로덕션 환경에서이 스크립트를 사용 하기 전에 다음 값을 변경 합니다.

- 사이트 데이터베이스 이름(`CM_ABC`)
- 마스터 키를 만들기 위한 암호 (`MyMasterKeyPassword`)
- 인증서 만료 날짜(`20391022`)

``` SQL
USE CM_ABC
IF NOT EXISTS (SELECT name FROM sys.symmetric_keys WHERE name = '##MS_DatabaseMasterKey##')
BEGIN
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = MyMasterKeyPassword
END

IF NOT EXISTS (SELECT name from sys.certificates WHERE name = 'BitLockerManagement_CERT')
BEGIN
    CREATE CERTIFICATE BitLockerManagement_CERT AUTHORIZATION RecoveryAndHardwareCore
    WITH SUBJECT = 'BitLocker Management',
    EXPIRY_DATE = '20391022'

    GRANT CONTROL ON CERTIFICATE ::BitLockerManagement_CERT TO RecoveryAndHardwareRead
    GRANT CONTROL ON CERTIFICATE ::BitLockerManagement_CERT TO RecoveryAndHardwareWrite
END
```

### <a name="back-up-certificate"></a>인증서 백업

이 샘플 스크립트는 인증서를 백업 합니다. 인증서를 파일에 저장 하는 경우 계층의 다른 사이트 데이터베이스로 [복원할](#restore-certificate) 수 있습니다.

프로덕션 환경에서이 스크립트를 사용 하기 전에 다음 값을 변경 합니다.

- 사이트 데이터베이스 이름(`CM_ABC`)
- 파일 경로 및 이름(`C:\BitLockerManagement_CERT_KEY`)
- 키 암호 내보내기 (`MyExportKeyPassword`)

``` SQL
USE CM_ABC
BACKUP CERTIFICATE BitLockerManagement_CERT TO FILE = 'C:\BitLockerManagement_CERT'
    WITH PRIVATE KEY ( FILE = 'C:\BitLockerManagement_CERT_KEY',
        ENCRYPTION BY PASSWORD = MyExportKeyPassword)
END
```

> [!IMPORTANT]
> 내보낸 인증서 파일 및 관련 암호를 안전한 위치에 저장 합니다.

### <a name="restore-certificate"></a>인증서 복원

이 샘플 스크립트는 파일에서 인증서를 복원 합니다. 이 프로세스를 사용 하 여 다른 사이트 데이터베이스에서 만든 인증서를 배포할 수 있습니다.

프로덕션 환경에서이 스크립트를 사용 하기 전에 다음 값을 변경 합니다.

- 사이트 데이터베이스 이름(`CM_ABC`)
- 마스터 키 암호(`MyMasterKeyPassword`)
- 파일 경로 및 이름(`C:\BitLockerManagement_CERT_KEY`)
- 키 암호 내보내기 (`MyExportKeyPassword`)

``` SQL
USE CM_ABC
IF NOT EXISTS (SELECT name FROM sys.symmetric_keys WHERE name = '##MS_DatabaseMasterKey##')
BEGIN
    CREATE MASTER KEY ENCRYPTION BY PASSWORD = MyMasterKeyPassword
END

IF NOT EXISTS (SELECT name from sys.certificates WHERE name = 'BitLockerManagement_CERT')
BEGIN

CREATE CERTIFICATE BitLockerManagement_CERT AUTHORIZATION RecoveryAndHardwareCore
FROM FILE  = 'C:\BitLockerManagement_CERT'
    WITH PRIVATE KEY ( FILE = 'C:\BitLockerManagement_CERT_KEY',
        DECRYPTION BY PASSWORD = MyExportKeyPassword)

GRANT CONTROL ON CERTIFICATE ::BitLockerManagement_CERT TO RecoveryAndHardwareRead
GRANT CONTROL ON CERTIFICATE ::BitLockerManagement_CERT TO RecoveryAndHardwareWrite
END
```

### <a name="verify-certificate"></a>인증서 확인

이 SQL 스크립트를 사용 하 여 SQL에서 필요한 사용 권한으로 인증서를 만들었는지 확인 합니다.

``` SQL
USE CM_ABC
declare @count int
select @count = count(distinct u.name) from sys.database_principals u
join sys.database_permissions p on p.grantee_principal_id = u.principal_id or p.grantor_principal_id = u.principal_id
join sys.certificates c on c.certificate_id = p.major_id
where u.name in('RecoveryAndHardwareCore', 'RecoveryAndHardwareRead', 'RecoveryAndHardwareWrite') and
c.name = 'BitLockerManagement_CERT' and p.permission_name like 'CONTROL'
if(@count >= 3) select 1
else select 0
```

인증서가 유효한 경우 스크립트는 `1`값을 반환 합니다.

## <a name="see-also"></a>참고 항목

이러한 SQL 명령에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [SQL Server 및 데이터베이스 암호화 키](https://docs.microsoft.com/sql/relational-databases/security/encryption/sql-server-and-database-encryption-keys-database-engine)
- [인증서 만들기](https://docs.microsoft.com/sql/t-sql/statements/create-certificate-transact-sql)
- [인증서 백업](https://docs.microsoft.com/sql/t-sql/statements/backup-certificate-transact-sql)
- [마스터 키 만들기](https://docs.microsoft.com/sql/t-sql/statements/create-master-key-transact-sql)
- [마스터 키 백업](https://docs.microsoft.com/sql/t-sql/statements/backup-master-key-transact-sql)
- [인증서 권한 부여](https://docs.microsoft.com/sql/t-sql/statements/grant-certificate-permissions-transact-sql)
