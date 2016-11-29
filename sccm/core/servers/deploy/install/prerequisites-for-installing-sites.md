---
title: "사이트에 대한 필수 조건 | System Center Configuration Manager"
description: "다양한 유형의 System Center Configuration Manager 사이트를 설치하는 데 필요한 다양한 필수 조건에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: bf3b1e4d87a972f530590bf94e38a5ec66c4fc9a

---
# <a name="prerequisites-for-installing-system-center-configuration-manager-sites"></a>System Center Configuration Manager 사이트 설치에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*


다음 섹션에서는 다양한 유형의 System Center Configuration Manager 사이트를 설치하는 데 필요한 다양한 필수 조건에 대한 세부 정보를 제공합니다.



## <a name="primary-sites-and-the-central-administration-site"></a>기본 사이트 및 중앙 관리 사이트
다음 필수 조건은 계층, 독립 실행형 기본 사이트 또는 자식 기본 사이트의 첫 번째 사이트로 중앙 관리 사이트를 설치하는 데 적용됩니다. 계층 확장 시나리오의 일부로 중앙 관리 사이트를 설치하는 경우 이 항목의 [독립 실행형 기본 사이트 확장](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand
)을 참조하세요.

####  <a name="a-namebkmkprereqpria-prerequisites-to-install-a-primary-site-or-central-administration-site"></a><a name="bkmk_PrereqPri"></a> 기본 사이트 또는 중앙 관리 사이트 설치를 위한 필수 조건  

-   사이트를 설치하는 사용자에게 다음 권한이 있어야 합니다.  

    -   사이트 서버 컴퓨터에 대한**로컬 관리자**  

    -   **사이트 데이터베이스** 를 호스트할 각 컴퓨터 또는 사이트의 **SMS_Provider** 인스턴스에 대한 **로컬 관리자** 권한  

    -   사이트 데이터베이스를 호스트하는 SQL Server 인스턴스에 대한**Sysadmin** 권한  

        > [!IMPORTANT]  
        >  설치가 완료된 후에는 설치 프로그램을 실행한 사용자 계정과 사이트 서버 컴퓨터 계정 모두 SQL Server에 대한 sysadmin 권한을 보유해야 합니다. 이러한 계정에서 sysadmin 권한을 제거할 수 없습니다.  

-   기본 사이트를 설치할 때에는 다음과 같은 추가 권한이 필요합니다.  
    -  첫 관리 지점 및 배포 지점(사이트 서버에 없는 경우)을 설치하려는 추가 컴퓨터의**로컬 관리자** 권한  

-   중앙 관리 사이트 아래에 새 자식 기본 사이트를 설치할 때는 다음 추가 권한이 필요합니다.  

    -   중앙 관리 사이트를 호스트하는 컴퓨터에 대한**로컬 관리자** 권한  

    -   **인프라 관리자** 또는 **전체 관리자**의 보안 역할과 동등한 Configuration Manager 내의 역할 기반 관리 권한  

-   올바른 설치 미디어(소스 파일)를 사용하고 해당 위치에서 설치 프로그램을 실행해야 합니다. 서로 다른 사이트를 설치하는 데 사용할 올바른 소스 파일에 대한 자세한 내용은 [사이트를 설치할 준비](../../../../core/servers/deploy/install/prepare-to-install-sites.md) 항목의 [서로 다른 유형의 사이트 설치 옵션](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options)을 참조하세요.

-   사이트 서버 컴퓨터에는 Microsoft의 업데이트된 설치 파일에 대한 액세스 권한이 있어야 합니다.
    -  설치를 시작하기 전에 [설치 다운로더](../../../../core/servers/deploy/install/setup-downloader.md)를 사용하여 로컬 네트워크에 이러한 파일의 복사본을 다운로드 및 저장할 수 있습니다.
    -  이러한 파일의 로컬 복사본을 사용할 수 없는 경우 설치하는 동안 Microsoft에서 이러한 파일을 다운로드할 수 있도록 사이트 서버에서 인터넷에 액세스해야 합니다.

  - 서비스 연결 지점 사이트 시스템 역할이 설치된 독립 실행형 기본 사이트를 확장하려면 서비스 연결 지점을 제거해야 합니다. 계층 구조에는 이 역할 인스턴스를 계층 구조 최상위 계층 사이트에 하나만 포함할 수 있습니다. 중앙 관리 사이트 설치 중에 역할을 다시 설치할 수 있습니다.
  - 사이트 서버와 사이트 데이터베이스 컴퓨터는 모든 필수 조건 구성을 충족해야 합니다. 설치 프로그램을 시작하기 전에 [필수 조건 검사기를 수동으로 실행](../../../../core/servers/deploy/install/prerequisite-checker.md)하여 문제를 확인하고 해결할 수 있습니다.  


## <a name="a-namebkmkexpanda-expanding-a-stand-alone-primary-site"></a><a name="bkmk_expand"></a> 독립 실행형 기본 사이트 확장
독립 실행형 기본 사이트를 중앙 관리 사이트와 함께 계층 안으로 확장하려면 먼저 다음 필수 구성 요소를 충족해야 합니다.


-   **독립 실행형 기본 사이트의 버전과 일치하는 새 중앙 관리 사이트 설치 미디어(소스 파일)를 설치해야 합니다.**  
     버전과 일치하도록 독립 실행형 기본 사이트의 [CD.Latest 폴더](../../../../core/servers/manage/the-cd.latest-folder.md)에 있는 소스 파일을 사용하여 새 사이트를 설치합니다.

     다른 사이트를 설치하는 데 사용할 올바른 소스 파일에 대한 자세한 내용은 [사이트를 설치할 준비](../../../../core/servers/deploy/install/prepare-to-install-sites.md) 항목의 [서로 다른 유형의 사이트 설치 옵션](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options)을 참조하세요.


-   **독립 실행형 기본 사이트는 다른 Configuration Manager 계층의 데이터를 마이그레이션하도록 구성될 수 없습니다.**  

     다른 Configuration Manager 계층에서 독립 실행형 기본 사이트로 진행되는 활성 마이그레이션을 중지하고 마이그레이션에 대한 모든 구성을 제거해야 합니다. 여기에는 완료되지 않은 마이그레이션 작업, 데이터 수집 및 활성 원본 계층의 구성이 포함됩니다.  

     이는 곧 마이그레이션 작업은 계층의 최상위 계층 사이트에서 수행되며 마이그레이션 구성은 독립 실행형 기본 사이트를 확장할 때 중앙 관리 사이트에 전송되지 않기 때문에 필요합니다.  

     독립 실행형 기본 사이트를 확장한 후 기본 사이트에서 마이그레이션을 다시 구성하면 마이그레이션 관련 작업은 중앙 관리 사이트에서 수행될 것입니다. 마이그레이션을 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager로 마이그레이션할 원본 계층 구조 및 원본 사이트 구성](../../../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)을 참조하세요.  

-   **새 중앙 관리 사이트를 호스트할 컴퓨터의 컴퓨터 계정은 독립 실행형 기본 사이트에서 관리자 그룹의 구성원이어야 합니다.**  

     독립 실행형 기본 사이트를 성공적으로 확장하려면 새 중앙 관리 사이트의 컴퓨터 계정은 독립 실행형 기본 사이트 **관리자** 그룹의 구성원이어야 합니다. 이 요구 사항은 사이트 확장 중에만 필요하며 사이트 확장이 완료되면 해당 계정을 기본 사이트의 그룹에서 제거할 수 있습니다.  

-   **독립 실행형 기본 사이트에서 설치 프로그램을 실행하여 새 중앙 관리 사이트를 설치하는 사용자 계정에는 역할 기반 관리 권한을 부여해야 합니다.**  

     사이트 확장 시나리오의 일부로 중앙 관리 사이트를 설치하려면 독립 실행형 기본 사이트에서 설치 프로그램을 실행하여 중앙 관리 사이트를 설치하는 사용자 계정을 역할 기반 관리에서 **전체 관리자** 또는 **인프라 관리자**로 정의해야 합니다.  

-   **사이트를 확장하려면 먼저 독립 실행형 기본 사이트에서 다음 사이트 시스템 역할을 제거해야 합니다.**  

    -   Asset Intelligence 동기화 지점  

    -   Endpoint Protection 지점  

    -   서비스 연결 지점  

     이러한 사이트 시스템 역할은 계층의 최상위 계층 사이트에서만 지원됩니다. 따라서 독립 실행형 기본 사이트를 확장하려면 먼저 이러한 사이트 시스템 역할을 제거해야 합니다. 사이트를 확장한 후 중앙 관리 사이트에 이 사이트 시스템 역할을 다시 설치할 수 있습니다.  

    다른 모든 사이트 시스템 역할은 기본 사이트에 그대로 유지해도 됩니다.  

-   **독립 실행형 기본 사이트와 중앙 관리 사이트를 설치할 컴퓨터 간에 SQL Server Service Broker의 포트를 열어야 합니다.**  

     중앙 관리 사이트와 기본 사이트 간에 데이터를 성공적으로 복제하려면 Configuration Manager에서 두 사이트 간에 SQL Server Service Broker가 사용할 포트를 열어야 합니다. 중앙 관리 사이트를 설치하고 독립 실행형 기본 사이트를 확장하면 필수 구성 요소 검사에서 SQL Server Service Broker용으로 지정한 포트가 기본 사이트에서 열리도록 설정되지 않습니다.  


## <a name="a-namebkmksecondarya-secondary-sites"></a><a name="bkmk_secondary"></a> 보조 사이트
다음은 보조 사이트 설치를 위한 필수 조건입니다.
-   Configuration Manager 콘솔에서 보조 사이트의 설치를 구성하는 관리자에게는 **인프라 관리자** 또는 **전체 관리자**의 보안 역할에 해당하는 역할 기반 관리 권한이 있어야 합니다.  

-   부모 기본 사이트의 컴퓨터 계정은 보조 사이트 서버 컴퓨터의 **로컬 관리자** 여야 합니다.  

-   보조 사이트에서 이전에 설치한 SQL Server 인스턴스를 사용하여 보조 사이트 데이터베이스를 호스팅하는 경우 다음을 충족해야 합니다.  

    -   부모 기본 사이트의 **컴퓨터 계정** 에는 보조 사이트 서버 컴퓨터의 SQL Server 인스턴스에 대한 **sysadmin** 권한이 있어야 합니다.  

    -   보조 사이트 서버 컴퓨터의 **로컬 시스템** 계정에는 보조 사이트 서버 컴퓨터의 SQL Server 인스턴스에 대한 **sysadmin** 권한이 있어야 합니다.  

        > [!IMPORTANT]  
        >  설치가 완료된 후에는 두 계정 모두 SQL Server에 대한 sysadmin 권한을 보유해야 합니다. 이러한 계정에서 sysadmin 권한을 제거할 수 없습니다.  

-   보조 사이트 서버 컴퓨터는 관리 지점 및 배포 지점의 SQL Server 및 기본 사이트 시스템 역할을 포함하는 모든 필수 조건 구성을 충족해야 합니다.  



<!--HONumber=Nov16_HO1-->


