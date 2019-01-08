---
title: 무인 복구
titleSuffix: Configuration Manager
description: Configuration Manager에서 스크립트를 사용하여 사이트를 복구합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 828c31d1-3d70-4412-b1a8-c92e7e504d39
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 637727356724085f019ac9ab336bc37e3635ea3a
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53415146"
---
# <a name="unattended-site-recovery-for-configuration-manager"></a>Configuration Manager에 대한 무인 사이트 복구   

*적용 대상: System Center Configuration Manager(현재 분기)*

 Configuration Manager 중앙 관리 사이트 또는 기본 사이트의 [무인 복구](/sccm/protect/understand/recover-sites#site-recovery-procedures)를 수행하려는 경우, 무인 설치 스크립트를 만든 후 **/script** 명령 옵션과 함께 설치 프로그램을 사용하면 됩니다. 이 스크립트는 기본 설정이 없다는 점만 제외하고 설치 마법사에서 요구하는 정보와 동일한 유형의 정보를 제공합니다. 사용 중인 복구 유형에 적용되는 설치 키에 대해 모든 값을 지정해야 합니다.

 /Script 설치 명령줄 옵션을 사용하려면 초기화 파일을 만들어야 합니다. 그리고 /script 옵션 뒤에 이 파일 이름을 지정합니다. 파일 이름은 **.ini** 파일 이름 확장명만 붙이면 자유롭게 지정해도 됩니다. 명령줄에서 설치 초기화 파일을 참조할 때 파일의 전체 경로를 입력해야 합니다. 예를 들어 이름이 *setup.ini*인 설치 초기화 파일이 *C:\setup 폴더*에 저장되어 있는 경우 명령줄은 다음과 같습니다.

 `setup /script c:\setup\setup.ini`

> [!IMPORTANT]  
>  설치 프로그램을 실행하려면 관리자 권한이 있어야 합니다. 무인 스크립트로 설치 프로그램을 실행할 경우 **관리자 권한으로 실행**을 사용하여 명령 프롬프트를 관리자 컨텍스트로 시작하세요.

 스크립트에는 섹션 이름, 키 이름 및 값이 포함됩니다. 필요한 섹션 키 이름은 스크립트를 작성하는 복구 유형에 따라 다릅니다. 섹션 내의 키 순서와 파일 내의 섹션 순서는 중요하지 않습니다. 키는 대/소문자를 구분하지 않습니다. 키에 값을 지정할 때에는 키 이름 뒤에 등호(=)를 추가하고 키 값을 입력해야 합니다.

 다음 섹션에서는 무인 사이트 복구를 위한 스크립트를 만드는 방법에 대해 설명합니다. 이 표에는 사용 가능한 설치 스크립트 키, 해당 값, 필수 여부, 설치 유형, 키에 대한 간략한 설명이 나와 있습니다.

## <a name="recover-a-central-administration-site-unattended"></a>중앙 관리 사이트의 무인 복구
 다음 정보를 참조하여 중앙 관리 사이트를 복구하도록 무인 설치 스크립트 파일을 구성할 수 있습니다.

 **Identification**

-   **키 이름:** 작업

    -   **필수:** 예
    -   **값:** RecoverCCAR
    -   **세부 정보:** 중앙 관리 사이트를 복구합니다.


-   **키 이름:** CDLatest

    -   **필수:** 예 – CD.Latest 폴더의 미디어를 사용할 경우에만.
    -   **값:** 1 1이 아닌 모든 값은 CD.Latest를 사용하지 않는 것으로 간주합니다.
    -   **세부 정보:** 기본 또는 중앙 관리 사이트를 설치하거나 기본 또는 중앙 관리 사이트를 복구할 목적으로 CD.Latest 폴더에 있는 미디어의 설치 프로그램을 실행할 경우 이 키 및 값을 스크립트에 포함해야 합니다. 이 값은 미디어 양식 CD.Latest가 사용되고 있음을 설치 프로그램에 알립니다.

**RecoveryOptions**   
-   **키 이름:** ServerRecoveryOptions   

    -   **필수:** 예
    -   **값:** 1, 2 또는 4  
         1 = 사이트 서버와 SQL Server 복구   
         2 = 사이트 서버만 복구  
         4 = SQL Server만 복구
    -   **세부 정보:** 설치 프로그램이 사이트 서버, SQL Server 또는 둘 다 복구하는지 여부를 지정합니다. ServerRecoveryOptions 설정에 대해 다음 값을 설정하는 경우 연결된 키는 필수입니다.  
        -   **값 = 1** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.

             **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.

        -   **값 = 2** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.

        -   **값 = 4** **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.

-   **키 이름:** DatabaseRecoveryOptions

    -   **필수:** 경우에 따라
    -   **값:**   
         - **10** = 백업에서 사이트 데이터베이스 복구.  
         - **20** = 다른 방법을 사용하여 수동으로 복구된 사이트 데이터베이스 사용.   
         - **40** = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 글로벌 데이터 및 사이트 데이터는 다른 사이트를 복제하여 복구됩니다.  
         - **80** = 데이터베이스 복구 건너뛰기.
    -   **세부 정보:** SQL Server의 사이트 데이터베이스를 복구하는 방법을 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.


-   **키 이름:** ReferenceSite  

    -   **필수:** 경우에 따라
    -   **값:** &lt;ReferenceSiteFQDN\>
    -   **세부 정보:** 참조 기본 사이트를 지정합니다. 데이터베이스 백업이 변경 내용 추적 보존 기간보다 오래 되었거나 백업 없이 사이트를 복구할 경우 중앙 관리 사이트에서는 참조 사이트를 사용하여 글로벌 데이터를 복구합니다.

         참조 사이트를 지정하지 않았는데 백업이 변경 추적 보존 기간보다 오래된 경우 모든 기본 사이트는 중앙 관리 사이트에서 복원된 데이터로 다시 초기화됩니다.

         참조 사이트를 지정하지 않고 백업이 변경 내용 추적 보존 기간 내에 있는 경우, 백업 이후 변경된 내용만 기본 사이트에서 복제됩니다. 서로 다른 기본 사이트 간에 충돌하는 변경 내용이 있으면 중앙 관리 사이트에서는 가장 먼저 수신한 변경 내용을 사용합니다.

         **DatabaseRecoveryOptions** 설정 값이 **40**인 경우 이 키는 필수입니다.

-   **키 이름:** SiteServerBackupLocation

    -   **필수:** 아니요
    -   **값:** &lt;PathToSiteServerBackupSet\>
    -   **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.


-   **키 이름:** BackupLocation

    -   **필수:** 경우에 따라
    -   **값:** &lt;PathToSiteDatabaseBackupSet\>
    -   **세부 정보:** 사이트 데이터베이스 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 키 값을 **1** 또는 **4** 로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하는 경우 **BackupLocation** 키는 필수입니다.


**Options**

- **키 이름:** ProductID
  -   **필수:** 예
  -   **값:**   
       - xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
       - 평가 버전
  -   **세부 정보:** 대시를 포함한 Configuration Manager 설치 제품 키입니다. **Eval** 입력을 통해 Configuration Manager의 평가 버전을 설치할 수 있습니다.  


- **키 이름:** SiteCode

  -   **필수:** 예
  -   **값:** &lt;사이트 코드\>
  -   **세부 정보:** 계층 구조에서 사이트를 고유하게 식별하는 세 자리 영숫자입니다. 실패하기 전에 사이트에서 사용했던 사이트 코드를 지정합니다.


- **키 이름:** SiteName

  -   **필수:** 예
  -   **값:** SiteName
  -   **세부 정보:** 이 사이트에 대한 설명입니다.


- **키 이름:** SMSInstallDir

  - **필수:** 예
  - **값:** &lt;*ConfigMgrInstallationPath*>
  - **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.
    > [!NOTE]   
    >  Configuration Manager 설치에 사용할 원래 경로 또는 새 경로를 지정할 수 있습니다.

- **키 이름:** SDKServer

  -   **필수:** 예
  -   **값:** &lt;*SMS 공급 기업의 FQDN*>
  -   **세부 정보:** SMS 공급 기업을 호스트하는 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정합니다.

       초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.

- **키 이름:** PrerequisiteComp

  -   **필수:** 예
  -   **값:** 0 또는 1  
       0 = 다운로드   
       1 = 이미 다운로드됨
  -   **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 0 값을 사용하는 경우 파일이 다운로드됩니다.  


- **키 이름:** PrerequisitePath

  -   **필수:** 예
  -   **값:** &lt;*PathToSetupPrerequisiteFiles*>
  -   **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.

- **키 이름:** AdminConsole

  -   **필수:** 경우에 따라
  -   **값:** 0 또는 1 0 = 설치 안 함   
       1 = 설치
  -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다. **ServerRecoveryOptions** 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.


- **키 이름:** JoinCEIP   
  > [!Note]  
  > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

  -   **필수:** 예
  -   **값:** 0 또는 1  
       0 = 참여 안 함  
       1 = 참여
  -   **세부 정보:** 사용자 환경 개선 프로그램에 참여할지 여부를 지정합니다.

**SQLConfigOptions**

-   **키 이름:** SQLServerName

    -   **필수:** 예
    -   **값:** *&lt;SQLServerName\>*
    -   **세부 정보:** 사이트 데이터베이스를 호스트하는 SQL Server를 실행하는 서버 이름 또는 클러스터형 인스턴스 이름입니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정합니다.


-   **키 이름:** DatabaseName

    -   **필수:** 예
    -   **값:** *&lt;SiteDatabaseName\>* 또는 *&lt;InstanceName\>*\\*&lt;SiteDatabaseName\>*
    -   **세부 정보:** 중앙 관리 사이트 데이터베이스를 설치하는 데 사용하거나 만들 SQL Server 데이터베이스의 이름입니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정합니다.

        > [!IMPORTANT]  
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.

-   **키 이름:** SQLSSBPort

    -   **필수:** 아니요
    -   **값:** &lt;*SSBPortNumber*>
    -   **세부 정보:** SQL Server에서 사용하는 SQL Server Service Broker(SSB) 포트를 지정합니다. 일반적으로, SSB는 TCP 포트 4022를 사용하도록 구성되지만 다른 포트도 지원됩니다. 실패하기 전에 사용했던 SSB 포트를 지정합니다.

## <a name="recover-a-primary-site-unattended"></a>기본 사이트 무인 복구
 다음 정보를 참조하여 중앙 관리 사이트를 복구하도록 무인 설치 스크립트 파일을 구성할 수 있습니다.

 **Identification**

-   **키 이름:** 작업

    -   **필수:** 예
    -   **값:** RecoverPrimarySite
    -   **세부 정보:** 기본 사이트 복구


-   **키 이름:** CDLatest

    -   **필수:** 예 – CD.Latest 폴더의 미디어를 사용할 경우에만.
    -   **값:** 1 1이 아닌 모든 값은 CD.Latest를 사용하지 않는 것으로 간주합니다.
    -   **세부 정보:** 기본 또는 중앙 관리 사이트를 설치하거나 기본 또는 중앙 관리 사이트를 복구할 목적으로 CD.Latest 폴더에 있는 미디어의 설치 프로그램을 실행할 경우 이 키 및 값을 스크립트에 포함해야 합니다. 이 값은 미디어 양식 CD.Latest가 사용되고 있음을 설치 프로그램에 알립니다.

**RecoveryOptions**

-   **키 이름:** ServerRecoveryOptions

    -   **필수:** 예
    -   **값:** 1, 2 또는 4    
         1 = 사이트 서버와 SQL Server 복구   
         2 = 사이트 서버만 복구  
         4 = SQL Server만 복구
    -   **세부 정보:** 설치 프로그램이 사이트 서버, SQL Server 또는 둘 다 복구하는지 여부를 지정합니다. ServerRecoveryOptions 설정에 대해 다음 값을 설정하는 경우 연결된 키는 필수입니다.

        -   **값 = 1** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.

             **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.

        -   **값 = 2** 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키 값을 지정하는 옵션이 있습니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.

        -   **값 = 4** **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하여 백업에서 사이트 데이터베이스를 복원하는 경우 **BackupLocation** 키는 필수입니다.

-   **키 이름:** DatabaseRecoveryOptions

    -   **필수:** 경우에 따라
    -   **값:**   
         - **10** = 백업에서 사이트 데이터베이스 복구.  
         - **20** = 다른 방법을 사용하여 수동으로 복구된 사이트 데이터베이스 사용.     
         - **40** = 사이트에 새 데이터베이스 만들기. 사이트 데이터베이스 백업을 사용할 수 없는 경우 이 옵션을 사용하세요. 글로벌 데이터 및 사이트 데이터는 다른 사이트를 복제하여 복구됩니다.  
         - **80** = 데이터베이스 복구 건너뛰기.
    -   **세부 정보:** SQL Server의 사이트 데이터베이스를 복구하는 방법을 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **4**인 경우 이 키는 필수입니다.


-   **키 이름:** SiteServerBackupLocation

    -   **필수:** 아니요
    -   **값:** &lt;PathToSiteServerBackupSet\>
    -   **세부 정보:** 사이트 서버 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 설정 값이 **1** 또는 **2**인 경우 이 키는 옵션입니다. 사이트 백업을 사용하여 사이트를 복구할 수 있도록 **SiteServerBackupLocation** 키의 값을 지정합니다. 값을 지정하지 않으면 사이트는 백업 집합으로부터 복원되지 않고 다시 설치됩니다.     


-   **키 이름:** BackupLocation

    -   **필수:** 경우에 따라
    -   **값:** &lt;PathToSiteDatabaseBackupSet\>
    -   **세부 정보:** 사이트 데이터베이스 백업 집합의 경로를 지정합니다. **ServerRecoveryOptions** 키 값을 **1** 또는 **4** 로 구성하고 **DatabaseRecoveryOptions** 키 값을 **10** 으로 구성하는 경우 **BackupLocation** 키는 필수입니다.

**Options**

-   **키 이름:** ProductID

    -   **필수:** 예
    -   **값:**     
         - xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
         - 평가 버전     
    -   **세부 정보:** 대시를 포함한 Configuration Manager 설치 제품 키입니다. **Eval** 입력을 통해 Configuration Manager의 평가 버전을 설치할 수 있습니다.  


-   **키 이름:** SiteCode

    -   **필수:** 예
    -   **값:** &lt;사이트 코드\>
    -   **세부 정보:** 계층 구조에서 사이트를 고유하게 식별하는 세 자리 영숫자입니다. 실패하기 전에 사이트에서 사용했던 사이트 코드를 지정합니다.


-   **키 이름:** SiteName

    -   **필수:** 예
    -   **값:** SiteName
    -   **세부 정보:** 이 사이트에 대한 설명입니다.


-   **키 이름:** SMSInstallDir

    -   **필수:** 예
    -   **값:** &lt;*ConfigMgrInstallationPath*>
    -   **세부 정보:** Configuration Manager 프로그램 파일의 설치 폴더를 지정합니다.

        > [!NOTE]   
        >  Configuration Manager 설치에 사용할 원래 경로 또는 새 경로를 지정할 수 있습니다.

-   **키 이름:** SDKServer

    -   **필수:** 예
    -   **값:** &lt;*SMS 공급 기업의 FQDN*>
    -   **세부 정보:** SMS 공급 기업을 호스트하는 서버의 FQDN을 지정합니다. 장애가 발생하기 전에 SMS 공급자를 호스트하던 서버를 지정합니다.

         초기 설치 후 사이트에 대해 다른 SMS 공급자를 구성할 수 있습니다.

-   **키 이름:** PrerequisiteComp

    -   **필수:** 예
    -   **값:** 0 또는 1    
         0 = 다운로드   
         1 = 이미 다운로드됨   
    -   **세부 정보:** 설치 필수 구성 요소 파일이 이미 다운로드되었는지 여부를 지정합니다. 예를 들어 0 값을 사용하는 경우 파일이 다운로드됩니다.


-   **키 이름:** PrerequisitePath

    -   **필수:** 예
    -   **값:** &lt;*PathToSetupPrerequisiteFiles*>
    -   **세부 정보:** 설치 필수 구성 요소 파일의 경로를 지정합니다. **PrerequisiteComp** 값에 따라 이 경로는 다운로드한 파일을 저장하는 데 사용되거나 이전에 다운로드한 파일을 찾는 데 사용됩니다.


-   **키 이름:** AdminConsole

    -   **필수:** 경우에 따라
    -   **값:** 0 또는 1  
         0 = 설치 안 함   
         1 = 설치  
    -   **세부 정보:** Configuration Manager 콘솔 설치 여부를 지정합니다. **ServerRecoveryOptions** 설정 값이 **4**인 경우를 제외하고 이 키는 필수입니다.

-   **키 이름:** JoinCEIP  
    > [!Note]  
    > Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

    -   **필수:** 예
    -   **값:** 0 또는 1    
         0 = 참여 안 함  
         1 = 참여
    -   **세부 정보:** 사용자 환경 개선 프로그램에 참여할지 여부를 지정합니다.


**SQLConfigOptions**

-   **키 이름:** SQLServerName

    -   **필수:** 예
    -   **값:** *&lt;SQLServerName\>*
    -   **세부 정보:** 사이트 데이터베이스를 호스트하는 SQL Server를 실행하는 서버 이름 또는 클러스터형 인스턴스 이름입니다. 실패하기 전에 사이트 데이터베이스를 호스팅했던 서버를 지정합니다.


-   **키 이름:** DatabaseName

    -   **필수:** 예
    -   **값:** *&lt;SiteDatabaseName\>* 또는 *&lt;InstanceName\>*\\*&lt;SiteDatabaseName\>*
    -   **세부 정보:** 중앙 관리 사이트 데이터베이스를 설치하는 데 사용하거나 만들 SQL Server 데이터베이스의 이름입니다. 실패하기 전에 사용되던 동일한 데이터베이스 이름을 지정합니다.

        > [!IMPORTANT]    
        >  기본 인스턴스를 사용하지 않는 경우 인스턴스 이름과 사이트 데이터베이스 이름을 지정해야 합니다.

-   **키 이름:** SQLSSBPort

    -   **필수:** 아니요
    -   **값:** &lt;*SSBPortNumber*>
    -   **세부 정보:** SQL Server에서 사용하는 SQL Server Service Broker(SSB) 포트를 지정합니다. 일반적으로, SSB는 TCP 포트 4022를 사용하도록 구성되지만 다른 포트도 지원됩니다. 실패하기 전에 사용했던 SSB 포트를 지정합니다.

**Hierarchy ExpansionOption**

-   **키 이름:** CCARSiteServer

    -   **필수:** 경우에 따라
    -   **값:** &lt;*SiteCodeForCentralAdministrationSite*>
    -   **세부 정보:** 기본 사이트가 Configuration Manager 계층 구조에 조인할 때 연결하는 중앙 관리 사이트를 지정합니다. 실패하기 전에 기본 사이트가 중앙 관리 사이트에 연결되었던 경우 이 설정은 필수입니다. 실패하기 전에 중앙 관리 사이트에 사용했던 사이트 코드를 지정합니다.

-   **키 이름:** CASRetryInterval

    -   **필수:** 아니요
    -   **값:** &lt;*간격*>
    -   **세부 정보:** 연결에 실패한 후 중앙 관리 사이트를 연결하려고 다시 시도하는 간격(분)을 지정합니다. 예를 들어 기본 사이트가 중앙 관리 사이트에 연결하지 못하면 WaitForCASTimeout 기간에 도달할 때까지 기본 사이트는 CASRetryInterval 값에 기반하여 중앙 관리 사이트에 대한 연결을 다시 시도합니다.


-   **키 이름:** WaitForCASTimeout

    -   **필수:** 아니요
    -   **값:** &lt;*시간 초과*>
    -   **세부 정보:** 기본 사이트가 중앙 관리 사이트에 연결하는 최대 시간 제한 값(분)을 지정합니다. 예를 들어 기본 사이트가 중앙 관리 사이트에 연결하지 못하면 WaitForCASTimeout 기간에 도달할 때까지 기본 사이트는 CASRetryInterval 값에 기반하여 중앙 관리 사이트에 대한 연결을 다시 시도합니다. 값은 0에서 100까지 지정할 수 있습니다.
