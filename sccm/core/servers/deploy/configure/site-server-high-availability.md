---
title: 사이트 서버 고가용성
titleSuffix: Configuration Manager
description: 수동 모드 사이트 서버를 추가하여 Configuration Manager 사이트 서버에 대해 고가용성을 구성하는 방법입니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6dcef836-c0d1-40af-ad30-cd8d864b09a9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 912bdb93db05091ff756c51ee9f951a17a76ff5d
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385974"
---
# <a name="site-server-high-availability-in-configuration-manager"></a>Configuration Manager의 사이트 서버 고가용성 

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1128774-->

Configuration Manager 버전 1806부터 사이트 서버 역할에 대한 고가용성은 *수동* 모드에서 추가 사이트 서버를 설치하기 위한 Configuration Manager 기반 솔루션입니다. 수동 모드의 사이트 서버는 *활성* 모드의 기존의 사이트 서버 외의 추가 서버입니다. 수동 모드의 사이트 서버는 필요할 때 즉시 사용할 수 있습니다. Configuration Manager 서비스의 [고가용성](/sccm/core/servers/deploy/configure/high-availability-options)을 위해 전체 설계의 일부로 추가 사이트 서버를 포함합니다.  

수동 모드의 사이트 서버:
- 활성 모드의 사이트 서버와 동일한 사이트 데이터베이스를 사용합니다.
- 수동 모드에서는 사이트 데이터베이스에 데이터를 쓰지 않습니다.
- 활성 모드의 사이트 서버와 동일한 콘텐츠 라이브러리를 사용합니다.

수동 모드의 사이트 서버를 활성화하려면 수동으로 *수준을 올립니다*. 이 작업은 활성 모드의 사이트 서버를 수동 모드의 사이트 서버로 전환합니다. 원래 활성 모드인 서버에서 사용할 수 있는 사이트 시스템 역할은 컴퓨터에 액세스할 수 있기만 하면 사용 가능한 상태로 유지됩니다. 사이트 서버 역할만 활성 모드와 수동 모드 간에 전환됩니다.

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.



## <a name="prerequisites"></a>필수 구성 요소

- 수동 모드의 사이트 서버는 Azure에서 온-프레미스 또는 클라우드 기반일 수 있습니다.  
    > [!Note]  
    > 수동 모드의 클라우드 기반 사이트 서버는 Azure IaaS(Infrastructure as a service)를 사용합니다. 자세한 내용은 다음 아티클을 참조하세요.  
    > - [Azure 가상 머신 (클라우드 기반 인프라의 경우)](/sccm/core/understand/use-cloud-services#azure-virtual-machines-for-cloud-based-infrastructure)
    > - [Azure의 Configuration Manager FAQ](/sccm/core/understand/configuration-manager-on-azure)  

- 두 사이트 서버는 모두 동일한 Active Directory 도메인에 조인되어야 합니다.  

- 사이트는 독립 실행형 기본 사이트입니다. 

- 두 사이트 서버는 각 사이트 서버에서 원격인 동일한 사이트 데이터베이스를 사용해야 합니다.  

     - 두 사이트 서버는 사이트 데이터베이스를 호스팅하는 SQL Server의 인스턴스에 대한 **sysadmin** 권한이 필요합니다.

     - 사이트 데이터베이스를 호스트하는 SQL Server는 기본 인스턴스, 명명된 인스턴스, [SQL Server 클러스터](/sccm/core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database) 또는 [SQL Server Always On 가용성 그룹](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).을 사용할 수 있습니다.  

     - 수동 모드의 사이트 서버는 활성 모드의 사이트 서버와 동일한 사이트 데이터베이스를 사용하도록 구성됩니다. 수동 모드의 사이트 서버는 데이터베이스에서 읽기만 수행합니다. 활성 모드로 수준을 올려야 데이터베이스에 씁니다.  

- 사이트 콘텐츠 라이브러리는 원격 네트워크 공유에 있어야 합니다. 두 사이트 서버는 공유와 해당 내용에 대한 모든 권한이 필요합니다. 자세한 내용은 [콘텐츠 라이브러리관리](/sccm/core/plan-design/hierarchy/the-content-library#manage-content-library)를 참조하세요.<!--1357525-->  

    - 사이트 서버는 배포 지점 역할을 가질 수 없습니다. 배포 지점도 콘텐츠 라이브러리를 사용하며 이 역할은 원격 콘텐츠 라이브러리를 지원하지 않습니다. 콘텐츠 라이브러리를 이동한 후 사이트 서버에 배포 지점 역할을 추가할 수 없습니다.  

- 수동 모드의 사이트 서버:  

     - [기본 사이트를 설치하기 위한 필수 구성 요소](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#primary-sites-and-the-central-administration-site)를 충족해야 합니다.  

     - 활성 모드의 사이트 서버에서 로컬 관리자 그룹에 해당 컴퓨터 계정이 있어야 합니다. <!--516036-->

     - 활성 모드의 사이트 서버의 버전과 일치하는 원본 파일을 사용하여 설치됩니다.  

     - 수동 모드 역할에 사이트 서버를 설치하기 전에는 어떤 사이트의 사이트 시스템 역할도 가질 수 없습니다.  

- 두 사이트 서버는 [해당 항목을 모두 Configuration Manager에서 지원한다면](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers) 서로 다른 OS와 서비스 팩 버전을 실행할 수 있습니다.  



## <a name="limitations"></a>제한 사항
- 수동 모드의 단일 사이트 서버는 각 기본 사이트에서 지원됩니다.  

- 수동 모드의 사이트 서버는 계층 구조에서 지원되지 않습니다. 계층 구조에는 중앙 관리 사이트와 자식 기본 사이트가 포함됩니다. 수동 모드의 사이트 서버는 독립 실행형 기본 사이트에서만 만듭니다.<!--1358224-->

- 수동 모드의 사이트 서버는 독립 실행형 보조 사이트에서 지원되지 않습니다.<!--SCCMDocs issue 680-->  

- 수동 모드에서 활성 모드로의 사이트 서버 수준 올리기는 수동입니다. 자동 장애 조치(failover)는 없습니다.  

- 수동 모드에서 사이트 서버를 추가하기 전에는 새 서버에 사이트 시스템 역할을 추가할 수 없습니다.  

    > [!Note]  
    > 수동 모드에 사이트 서버를 추가한 후 필요에 따라 다른 역할을 추가할 수 있습니다. SMS 공급자 또는 기본 사이트의 관리 지점을 예로 들 수 있습니다.  

- 데이터베이스를 사용하는 보고 지점 같은 역할의 경우 데이터베이스를 두 사이트 서버에서 원격인 서버에 호스트합니다.  

- SMS 공급자는 수동 모드로 사이트 서버에 설치되지 않습니다. 수동 모드의 사이트 서버를 수동으로 활성 모드로 수준을 올리려면 사이트에 대한 공급자에 연결합니다. 다른 서버에 공급자의 추가 인스턴스를 하나 이상 설치합니다. 자세한 내용은 [SMS 공급자 계획](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider)을 참조하세요.  

- Configuration Manager 콘솔은 수동 모드에서 자동으로 사이트를 설치하지 않습니다.  



## <a name="add-a-site-server-in-passive-mode"></a>수동 모드로 사이트 서버 추가

일반적인 역할 추가 프로세스는 [사이트 시스템 역할 설치](/sccm/core/servers/deploy/configure/install-site-system-roles)를 참조하세요.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택한 다음, 리본에서 **사이트 시스템 서버 만들기**를 클릭합니다.   

2. 사이트 시스템 서버 만들기 마법사의 **일반** 페이지에서 수동 모드의 사이트 서버를 호스트할 서버를 지정합니다. 지정한 서버는 수동 모드에서 사이트 서버를 설치하기 전에는 사이트 시스템 역할을 호스트할 수 없습니다.  

3. **시스템 역할 선택** 페이지에서 **수동 모드의 사이트 서버**만 선택합니다.  

    > [!Note]  
    > 마법사가 이 페이지에서 다음 초기 필수 구성 요소 검사를 수행합니다.  
    > - 선택한 서버가 보조 사이트 서버가 아님
    > - 선택한 서버가 아직 수동 모드의 사이트 서버가 아님
    > - 사이트 콘텐츠 라이브러리가 원격 위치에 있음  
    >  
    > 이러한 초기 필수 구성 요소 검사가 실패하면 마법사의 이 페이지를 진행할 수 없습니다.  

4. **수동 모드의 사이트 서버** 페이지에서 마법사를 완료하려면 설치 프로그램을 실행하고 지정된 서버에서 사이트 서버 역할을 설치하는 데 사용되는 다음 정보를 제공해야 합니다.

     - 다음 옵션 중 하나를 선택합니다.  

         - **활성 모드의 사이트 서버에서 네트워크를 통해 설치 원본 파일 복사**: 이 옵션은 압축된 패키지를 만들어 새 사이트 서버에 보냅니다.  

         - **수동 모드의 사이트 서버에서 다음 위치에 원본 파일 사용**: 이미 복사한 원본 파일의 로컬 경로를 예로 들 수 있습니다. 이 콘텐츠가 활성 모드의 사이트 서버와 같은 버전인지 확인합니다.  

         - (*권장*) **다음 네트워크 위치의 원본 파일 사용**: 활성 모드의 사이트 서버에서 **CD.Latest** 폴더의 콘텐츠 경로를 직접 지정합니다. 예를 들어 `\\Server\SMS_ABC\CD.Latest`입니다. 여기서 "*Server*"는 활성 모드의 사이트 서버 이름, "*ABC*"는 사이트 이름입니다.  

     - 새 사이트 서버에서 Configuration Manager 설치의 로컬 경로를 지정합니다.  예를 들면 다음과 같습니다. `C:\Program Files\Configuration Manager`  

5. 마법사를 완료합니다. 그러면 Configuration Manager는 수동 모드에서 사이트 서버를 지정된 서버에 설치합니다.

설치 상태에 대한 자세한 내용은 콘솔에서 **모니터링** 작업 영역으로 이동하고 **사이트 서버 상태** 노드를 선택합니다. 수동 모드의 사이트 서버 상태는 **설치 중**으로 표시됩니다. 자세한 내용은 서버를 선택하고 **상태 표시**를 클릭합니다. 이 작업은 사이트 서버 설치 창을 엽니다. 프로세스가 완료되면 상태가 두 서버 모두 **확인**으로 표시됩니다.   

설정 프로세스에 대한 자세한 내용은 [순서도 - 수동 모드의 사이트 서버 설정](/sccm/core/servers/deploy/configure/passive-site-server-flowchart)을 참조하세요.

수동 모드의 사이트 서버를 추가한 다음에는 콘솔에서 **사이트** 노드의 **노드** 탭에 두 서버가 표시됩니다. 

모든 Configuration Manager 사이트 구성 요소는 수동 모드의 사이트 서버에서 대기 상태입니다. Windows 서비스는 계속 실행됩니다.



## <a name="site-server-promotion"></a>사이트 서버 수준 올리기  

백업 및 복구와 마찬가지로 사이트 서버 변경을 위한 프로세스를 계획하여 연습합니다. 프로모션 계획에서는 다음을 고려합니다.  

- 두 사이트 서버가 모두 온라인일 때 계획된 수준 올리기를 연습합니다. 활성 모드의 사이트 서버를 강제로 분리하거나 종료하여 계획되지 않은 장애 조치(failover)도 연습합니다.  

- 장애 조치(failover) 중의 운영 프로세스와, 다른 Configuration Manager 관리자에게 알릴 사항을 결정합니다.  

- 계획된 수준 올리기를 수행하기 전에:  

    - 사이트 및 사이트 구성 요소의 전체 상태를 확인합니다. 환경에 대해 모든 항목이 정상 상태인지 확인합니다.  

    - 사이트 간에 적극적으로 복제하는 모든 패키지의 콘텐츠 상태를 확인합니다.  

    - 새 콘텐츠 배포 작업은 시작하지 않습니다. 

        > [!Note]  
        > 장애 조치(failover) 도중에 사이트 간 파일 복제가 진행 중인 경우 새 사이트 서버가 복제된 파일을 받지 못할 수 있습니다. 이 경우 새 사이트 서버가 활성 상태가 된 후 소프트웨어 콘텐츠를 다시 배포합니다.<!--515436-->  


### <a name="process-to-promote-the-site-server-in-passive-mode-to-active-mode"></a>수동 모드에서 활성 모드로의 사이트 서버 수준 올리기 프로세스

이 섹션에서는 수동 모드에서 활성 모드로 사이트 서버를 변경하는 방법을 설명합니다. 사이트에 액세스하여 이러한 변경을 수행하려면 SMS 공급자의 인스턴스에 액세스할 수 있어야 합니다. 자세한 내용은 [다중 SMS 공급자](/sccm/core/plan-design/hierarchy/plan-for-the-sms-provider#BKMK_MultiSMSProv)를 참조하세요.  

> [!Important]  
> 기본적으로 원본 사이트 서버에는 SMS 공급자 역할이 있습니다. 이 서버가 오프라인 상태라면 공급자를 사용할 수 없으므로 사이트에 연결할 수 없습니다. 수동 모드의 사이트 서버를 추가할 때는 SMS 공급자가 자동으로 추가되지 않습니다. 고가용성 서비스를 위해 하나 이상의 추가 SMS 공급자 역할을 사이트에 추가합니다.  

> [!Tip]  
> Configuration Manager 콘솔은 사이트 서버의 WMI에서 사용할 수 있는 SMS 공급자 목록을 요청합니다. 사이트에 여러 SMS 공급자를 설치할 때는 설치된 SMS 공급자를 사용하도록 사이트가 각각의 새 연결 요청을 무작위로 할당합니다. 특정 연결 세션과 함께 사용할 SMS 공급자 위치는 지정할 수 없습니다. 현재 사이트 서버가 오프라인이라 콘솔이 사이트에 연결할 수 없는 경우 사이트 연결 창에서 다른 사이트 서버를 지정합니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 사이트를 선택한 다음, **노드** 탭으로 전환합니다. 수동 모드의 사이트 서버를 선택한 다음, 리본 메뉴에서 **활성으로 수준 올리기**를 클릭합니다. **예**를 클릭하여 계속합니다.   
  
2. 콘솔 노드를 새로 고칩니다. 수준을 올리려는 서버의 **상태** 열에서 **노드** 탭이 **수준 올리기**로 표시됩니다.  

3. 수준 올리기가 완료되면 활성 모드의 새 사이트 서버 모두와 수동 모드의 새 사이트 서버에 대해 **상태** 열이 **확인**으로 표시됩니다. 이제 사이트의 **서버 이름** 열이 활성 모드의 새 사이트 서버 이름을 표시합니다.

상세 상태를 보려면 **모니터링** 작업 영역으로 이동하고 **사이트 서버 상태** 노드를 선택합니다. **모드** 열에는 *활성* 또는 *수동* 서버가 식별됩니다. 수동 모드에서 활성 모드로 수준을 올리려는 경우 활성으로 수준을 올리려는 사이트 서버를 선택한 다음, 리본에서 **상태 표시**를 선택합니다. 이렇게 하면 프로세스에 대한 추가 세부 정보를 표시하는 사이트 서버 수준 올리기 상태 창이 열립니다.

활성 모드의 사이트 서버가 수동 모드로 전환될 경우 사이트 시스템 역할만 수동으로 지정됩니다. 해당 컴퓨터에 설치된 다른 모든 사이트 시스템은 활성 상태를 유지하며 클라이언트에서 액세스할 수 있습니다.

*계획된* 수준 올리기 프로세스에 대한 자세한 내용은 [순서도 - 사이트 서버 수준 올리기(계획)](/sccm/core/servers/deploy/configure/promote-site-server-flowchart)를 참조하세요.


### <a name="unplanned-failover"></a>계획되지 않은 장애 조치(Failover)

활성 모드의 현재 사이트 서버가 오프라인인 경우 수준 올리기를 위한 사이트 서버가 30분 동안 활성 모드의 현재 사이트 서버에 연결을 시도합니다. 오프라인 서버가 이 시간 안에 돌아오면 성공적으로 알림을 받고 변경이 정상적으로 진행됩니다. 그렇지 않으면 수준 올리기를 위한 사이트 서버가 사이트 구성을 활성으로 업데이트합니다. 오프라인 서버가 이 시간 이후에 돌아오면 먼저 사이트 데이터베이스에서 현재 상태를 확인합니다. 그런 다음, 스스로 수동 모드의 사이트 서버로 수준을 내립니다.

이 30분 대기 중에는 사이트에 활성 모드인 사이트 서버가 없습니다. 클라이언트는 관리 지점, 소프트웨어 업데이트 지점, 배포 지점 등과 같은 클라이언트 측 역할과 계속 통신할 수 있습니다. 사용자는 이미 배포된 소프트웨어를 계속 설치할 수 있습니다. 이 기간 동안에는 사이트 관리가 불가능합니다. 자세한 내용은 [사이트 오류 영향](/sccm/core/servers/manage/site-failure-impacts)을 참조하세요.  

오프라인 서버가 손상되어 복구될 수 없는 경우 이 사이트 서버를 콘솔에서 삭제합니다. 그런 다음, 수동 모드의 새 사이트 서버를 만들어 고가용성 서비스를 복원합니다. 

*계획되지 않은* 수준 올리기 프로세스에 대한 자세한 내용은 [순서도 - 사이트 서버 수준 올리기(계획되지 않음)](/sccm/core/servers/deploy/configure/promote-site-server-unplanned-flowchart)를 참조하세요.


### <a name="additional-tasks-after-site-server-promotion"></a>사이트 서버 수준 올리기 후 추가 작업  

사이트 서버 전환 후에는 [사이트복구](/sccm/core/servers/manage/recover-sites#post-recovery-tasks)에서 필요한 대부분의 다른 작업은 수행할 필요가 없습니다. 예를 들어 암호를 다시 설정하거나 Microsoft Intune 구독을 다시 연결하지 않아도 됩니다.

환경에서 요구하는 경우 다음 단계가 필요할 수 있습니다.  

- 배포 지점에 대한 PKI 인증서를 가져온 경우 해당 서버에 대해 인증서를 다시 가져옵니다. 자세한 내용은 [배포 지점에 대한 인증서 다시 생성](/sccm/core/servers/manage/recover-sites#regenerate-the-certificates-for-distribution-points)을 참조하세요.  

- Confguration Manager를 Microsoft Store for Business에 통합한 경우 연결을 다시 구성합니다. 자세한 내용은 [Microsoft Store for Business에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)를 참조하세요.  



## <a name="daily-monitoring"></a>일별 모니터링

수동 모드의 사이트 서버가 있으면 매일 모니터링합니다. 상태가 항상 양호하며 사용이 가능한지 확인합니다. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **사이트 서버 상태** 노드를 선택합니다. 사이트 서버와 현재 상태를 모두 봅니다. 또한 **관리** 작업 영역에서 상태를 확인합니다. **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다. 사이트를 선택한 다음, **노드** 탭으로 전환합니다. 