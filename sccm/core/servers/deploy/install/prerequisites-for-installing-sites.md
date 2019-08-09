---
title: 사이트 필수 조건
titleSuffix: Configuration Manager
description: 각 유형의 Configuration Manager 사이트를 설치하기 위한 필수 조건을 알아봅니다.
ms.date: 07/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0db2b5aa34034f85c97da0bbfe2f604ff606e753
ms.sourcegitcommit: ef7800a294e5db5d751921c34f60296c1642fc1f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68712543"
---
# <a name="prerequisites-for-installing-configuration-manager-sites"></a>Configuration Manager 사이트 설치에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

사이트 설치를 시작하기 전에 각 유형의 Configuration Manager 사이트를 설치하기 위한 필수 조건을 알아보는 것이 좋습니다.


## <a name="primary-sites-and-the-central-administration-site"></a>기본 사이트 및 중앙 관리 사이트

다음과 같은 필수 구성 요소는 다음 유형 중 하나를 설치하는 데 적용됩니다.

- 계층의 첫 번째 사이트로서의 중앙 관리 사이트
- 독립 실행형 기본 사이트
- 자식 기본 사이트

계층 구조 확장의 일부로 중앙 관리 사이트를 설치하는 경우 [독립 실행형 기본 사이트 확장](#bkmk_expand)을 참조하세요.

### <a name="bkmk_PrereqPri"></a> 기본 사이트 또는 중앙 관리 사이트 설치를 위한 필수 조건  

- 필수 Windows Server 역할, 기능 및 Windows 구성 요소가 설치되어 있어야 합니다. 자세한 내용은 [사이트 시스템 필수 구성 요소](/sccm/core/plan-design/configs/site-and-site-system-prerequisites#bkmk_2012sspreq)를 참조하세요.  

- 사이트를 설치하는 사용자 계정에는 다음 권한이 있어야 합니다.  

    - 다음 서버의**관리자**:  
        - 사이트 서버  
        - **사이트 데이터베이스**를 호스팅하는 각 서버  
        - 사이트에 대한 **SMS 공급자**의 각 인스턴스  

    - 사이트 데이터베이스를 호스트하는 SQL Server 인스턴스에 대한**Sysadmin** 권한  

        > [!IMPORTANT]  
        > Configuration Manager 설치가 완료되면 사이트 서버 컴퓨터 계정에 SQL Server에 대한 sysadmin 권한이 있어야 합니다. 이 계정에서 SQL sysadmin 권한을 제거하면 안 됩니다.  

- 기본 사이트를 설치하는 경우 다음과 같은 추가 권한이 필요합니다.  

    - 첫 관리 지점 및 배포 지점(사이트 서버에 없는 경우)을 설치하려는 추가 서버에 대한 **관리자** 권한  

- 중앙 관리 사이트 아래에 새 자식 기본 사이트를 설치하는 경우 다음 추가 권한이 필요합니다.  

    - 중앙 관리 사이트를 호스트하는 컴퓨터에 대한 **관리자** 권한  

    - **인프라 관리자** 또는 **전체 관리자**의 보안 역할과 동등한 Configuration Manager 내의 역할 기반 관리 권한  

- 올바른 설치 소스 파일을 사용하고 해당 위치에서 설치 프로그램을 실행해야 합니다. 서로 다른 유형의 사이트를 설치하는 데 사용할 올바른 소스 파일에 대한 자세한 내용은 [서로 다른 유형의 사이트 설치 옵션](/sccm/core/servers/deploy/install/prepare-to-install-sites#bkmk_options)을 참조하세요.  

- 사이트 서버는 다음 방법 중 하나로 Microsoft의 업데이트된 설치 파일에 액세스할 수 있어야 합니다.  

    - 설치를 시작하기 전에 이러한 파일 복사본을 다운로드하여 로컬 네트워크에 저장합니다. 자세한 내용은 [설치 다운로더](/sccm/core/servers/deploy/install/setup-downloader)를 참조하세요.  

    - 이러한 파일의 로컬 복사본을 사용할 수 없는 경우 사이트 서버에서 인터넷에 액세스해야 합니다. 설치 중에 이러한 파일을 Microsoft에서 다운로드합니다.  

- 사이트 서버와 사이트 데이터베이스 서버는 모든 필수 조건 구성을 충족해야 합니다. Configuration Manager 설치 프로그램을 시작하기 전에 [필수 조건 검사기를 수동으로 실행](/sccm/core/servers/deploy/install/prerequisite-checker)하여 문제를 확인하고 해결합니다.  

### <a name="bkmk_expand"></a> 독립 실행형 기본 사이트를 확장하기 위한 필수 구성 요소

독립 실행형 기본 사이트를 중앙 관리 사이트와 함께 계층 안으로 확장하려면 먼저 다음 필수 구성 요소를 충족해야 합니다.

#### <a name="source-file-version-matches-site-version"></a>소스 파일 버전이 사이트 버전과 일치

독립 실행형 기본 사이트의 버전과 일치하는 CD.Latest 폴더에서 미디어를 사용하여 새 중앙 관리 사이트를 설치합니다. 버전과 일치하도록 독립 실행형 기본 사이트의 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)에 있는 원본 파일을 사용합니다.

서로 다른 사이트를 설치하는 데 사용할 올바른 소스 파일에 대한 자세한 내용은 [서로 다른 유형의 사이트 설치 옵션](/sccm/core/servers/deploy/install/prepare-to-install-sites#bkmk_options)을 참조하세요.  

#### <a name="stop-active-migration-from-another-hierarchy"></a>다른 계층에서 활성 마이그레이션 중지

독립 실행형 기본 사이트는 다른 Configuration Manager 계층 구조의 데이터를 마이그레이션하도록 구성할 수 없습니다. 다른 Configuration Manager 계층 구조에서 독립 실행형 기본 사이트로 진행되는 활성 마이그레이션을 중지하고 마이그레이션에 대한 모든 구성을 제거해야 합니다. 구성에는 다음이 포함됩니다.

- 완료되지 않은 마이그레이션 작업  
- 데이터 수집  
- 활성 원본 계층의 구성  

이 구성은 Configuration Manager가 계층의 최상위 사이트에서 데이터를 마이그레이션하기 때문에 필요합니다. 독립 실행형 기본 사이트를 확장할 때 마이그레이션에 대한 구성은 중앙 관리 사이트에 전달되지 않습니다.  

독립 실행형 기본 사이트를 확장한 후 기본 사이트에서 마이그레이션을 다시 구성하면 중앙 관리 사이트에서 마이그레이션 작업을 수행합니다.

마이그레이션을 구성하는 방법에 대한 자세한 내용은 [마이그레이션할 원본 계층 구조 및 원본 사이트 구성](/sccm/core/migration/configuring-source-hierarchies-and-source-sites-for-migration)을 참조하세요.  

#### <a name="computer-account-as-administrator"></a>관리자로서의 컴퓨터 계정

새 중앙 관리 사이트를 호스트할 컴퓨터의 컴퓨터 계정은 독립 실행형 기본 사이트 서버에서 **관리자** 그룹의 구성원이어야 합니다.

독립 실행형 기본 사이트를 성공적으로 확장하려면 새 중앙 관리 사이트의 컴퓨터 계정에 독립 실행형 기본 사이트에 대한 **관리자** 권한이 있어야 합니다. 이 권한은 사이트 확장 중에만 필요합니다. 사이트 확장이 완료되면 기본 사이트의 사용자 그룹에서 계정을 제거할 수 있습니다.  

#### <a name="installation-account-permissions"></a>설치 계정 권한

독립 실행형 기본 사이트에서 Configuration Manager 설치 프로그램을 실행하여 새 중앙 관리 사이트를 설치하는 사용자 계정에는 역할 기반 관리 권한이 있어야 합니다.

사이트 확장의 일부로 중앙 관리 사이트를 설치하려면 독립 실행형 기본 사이트에서 설치 프로그램을 실행하여 중앙 관리 사이트를 설치하는 사용자 계정을 역할 기반 관리에서 **전체 관리자** 또는 **인프라 관리자**로 정의해야 합니다.

필수 권한의 전체 목록을 포함한 자세한 내용은 [사이트 설치 계정](/sccm/core/plan-design/hierarchy/accounts#site-installation-account)을 참조하세요.

#### <a name="top-level-site-roles"></a>최상위 사이트 역할

사이트를 확장하려면 먼저 독립 실행형 기본 사이트에서 다음 사이트 시스템 역할을 제거해야 합니다.

- Asset Intelligence 동기화 지점  
- Endpoint Protection 지점  
- 서비스 연결 지점  

Configuration Manager만 계층의 최상위 사이트에서 이러한 역할을 지원합니다. 독립 실행형 기본 사이트를 확장하려면 먼저 이러한 사이트 시스템 역할을 제거해야 합니다. 사이트를 확장한 후 중앙 관리 사이트에 이 사이트 시스템 역할을 다시 설치할 수 있습니다.  

다른 모든 사이트 시스템 역할은 기본 사이트에 그대로 유지해도 됩니다.  

#### <a name="open-the-sql-server-service-broker-port"></a>SQL Server Service Broker 포트 열기

독립 실행형 기본 사이트와 중앙 관리 사이트를 설치할 서버 간에 SQL SSB(Server Service Broker)의 네트워크 포트를 열어야 합니다.  

중앙 관리 사이트와 기본 사이트 간에 데이터를 성공적으로 복제하려면 Configuration Manager에서 두 사이트 간에 SSB가 사용할 포트가 열려 있어야 합니다. 중앙 관리 사이트를 설치하고 독립 실행형 기본 사이트를 확장하면 필수 조건 검사에서 SSB용으로 지정한 포트가 기본 사이트에서 열리는지 확인하지 않습니다.  

#### <a name="known-issues-with-azure-services"></a>Azure 서비스 관련 알려진 문제

사이트를 확장한 다음 Configuration Manager에서 다음의 Azure 서비스를 다시 구성해야 합니다.

- [Log Analytics](/sccm/core/clients/manage/sync-data-log-analytics)  
- [업그레이드 준비](/sccm/core/clients/manage/upgrade-readiness)  
- [비즈니스용 Microsoft Store](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)  
- [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)

버전 1806 이상에서는 Azure Active Directory 테넌트 비밀 키를 갱신합니다. 자세한 내용은 [비밀 키 갱신](/sccm/core/servers/deploy/configure/azure-services-wizard#bkmk_renew)을 참조하세요.

또는 해당 서비스로의 연결을 제거한 다음 재생성할 수도 있습니다.

1. Configuration Manager 콘솔에서 **Azure 서비스** 노드의 Azure 서비스를 삭제합니다.  

2. Azure Portal에서 Azure Active Directory 테넌트 노드의 서비스와 연결된 테넌트를 삭제합니다. 또한 서비스와 연결된 Azure AD 웹앱도 삭제됩니다.  

3. Configuration Manager와 함께 사용할 Azure 서비스를 다시 구성합니다.  


## <a name="bkmk_secondary"></a> 보조 사이트

다음은 보조 사이트 설치를 위한 필수 조건입니다.  

- 필수 Windows Server 역할, 기능 및 Windows 구성 요소가 설치되어 있어야 합니다. 자세한 내용은 [사이트 시스템 필수 구성 요소](/sccm/core/plan-design/configs/site-and-site-system-prerequisites#bkmk_2012secpreq)를 참조하세요.  

- Configuration Manager 콘솔에서 보조 사이트의 설치를 구성하는 관리자에게는 **인프라 관리자** 또는 **전체 관리자**의 보안 역할에 해당하는 역할 기반 관리 권한이 있어야 합니다.  

- 부모 기본 사이트의 컴퓨터 계정은 보조 사이트 서버의 **관리자**여야 합니다.  

- 보조 사이트에서 이전에 설치한 SQL Server 인스턴스를 사용하여 보조 사이트 데이터베이스를 호스팅하는 경우 다음을 충족해야 합니다.  

    - 부모 기본 사이트의 컴퓨터 계정에는 보조 사이트 서버의 SQL Server 인스턴스에 대한 **sysadmin** 권한이 있어야 합니다.  

    - 보조 사이트 서버 컴퓨터의 **로컬 시스템** 계정에는 보조 사이트 서버의 SQL Server 인스턴스에 대한 **sysadmin** 권한이 있어야 합니다.  

        > [!IMPORTANT]  
        > Configuration Manager 설치가 완료되면 두 계정에 모두 SQL Server에 대한 sysadmin 권한이 있어야 합니다. 이러한 계정에서 sysadmin 권한을 제거하지 마세요.  

- 보조 사이트 서버가 모든 전제 조건 구성을 충족해야 합니다. 이러한 구성에는 SQL Server와 관리 지점과 배포 지점의 기본 사이트 시스템 역할이 포함됩니다.  


## <a name="next-steps"></a>다음 단계

필수 구성 요소를 확인하고 나면 설치 프로그램을 실행할 수 있습니다. 자세한 내용은 [설치 마법사를 사용하여 Configuration Manager 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites)를 참조하세요.
