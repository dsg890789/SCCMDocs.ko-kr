---
title: Windows 클라이언트 배포 필수 조건
titleSuffix: Configuration Manager
description: Windows 컴퓨터에 구성 관리자 클라이언트를 배포하기 위한 필수 조건을 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 1a2a9b48-a95b-4643-b00c-b3079584ae2e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bf929e605a7d44ac2f29226177d3ab962eb8fba0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-deploying-clients-to-windows-computers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

사용 환경에 Configuration Manager 클라이언트를 배포할 경우 다음과 같은 외부 종속성과 제품 내 종속성이 있습니다. 또한, 각 클라이언트 배포 방법마다 클라이언트를 성공적으로 설치하기 위해 충족해야 할 자체 종속성이 있습니다.  

  장치가 구성 관리자 클라이언트의 최소 하드웨어 및 OS 요구 사항을 충족하는지 확인하려면 [지원되는 구성](../../../core/plan-design/configs/supported-configurations.md)도 검토해야 합니다.  

 Linux 및 UNIX용 구성 관리자 클라이언트의 필수 조건에 대한 자세한 내용은 [Linux 및 UNIX 컴퓨터에 클라이언트 배포 계획](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md)을 참조하세요.  

> [!NOTE]  
>  이 문서에 표시된 소프트웨어 버전 번호는 필요한 최소 버전 번호만 나타냅니다.  



##  <a name="BKMK_prereqs_computers"></a> 컴퓨터 클라이언트에 대한 필수 조건  
 컴퓨터에 Configuration Manager 클라이언트를 설치할 경우의 필수 조건을 확인하려면 다음 정보를 참조하세요.  

### <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

|||  
|-|-|  
|Windows Installer 버전 3.1.4000.2435|패키지 및 소프트웨어 업데이트용 Windows Installer 업데이트(.msp) 파일을 사용하도록 지원하는 데 필요합니다.|  
|[KB2552033](https://go.microsoft.com/fwlink/p/?LinkId=240048)|클라이언트 강제 설치를 사용하는 경우 Windows Server 2008 R2를 실행하는 사이트 서버에 이 핫픽스를 설치합니다.|  
|Microsoft BITS(Background Intelligent Transfer Service) 버전 2.5|클라이언트 컴퓨터와 Configuration Manager 사이트 시스템 간에 정체된 데이터 전송을 허용하는 데 필요합니다. BITS는 클라이언트 설치 시 자동으로 다운로드되지 않습니다. 컴퓨터에 BITS를 설치하는 경우 일반적으로 설치를 완료하려면 다시 시작해야 합니다.<br /><br /> 대부분의 운영 체제에는 BITS가 포함되어 있지만 그렇지 않은 경우(예: Windows Server 2003 R2 SP2) Configuration Manager 클라이언트를 설치하기 전에 BITS부터 설치해야 합니다.|  
|Microsoft 작업 Scheduler|클라이언트 설치를 완료하려면 클라이언트에서 이 서비스를 사용하도록 설정합니다.|  

### <a name="bkmk_ExternalDependencies"></a> 설치 중 자동으로 다운로드되는 Configuration Manager 외부 종속성  
 Configuration Manager 클라이언트에는 몇 가지 잠재적인 외부 종속성이 있습니다. 이러한 종속성은 클라이언트 컴퓨터의 운영 체제 및 설치된 소프트웨어에 따라 다릅니다.  

 클라이언트의 설치를 완료하는 데 이러한 종속성이 필요한 경우 클라이언트 소프트웨어와 함께 자동으로 설치됩니다.  

|||  
|-|-|  
|Windows Update 에이전트 버전 7.0.6000.363|Windows에서 업데이트 검색 및 배포를 지원하는 데 필요합니다.|  
|Microsoft Core XML Services(MSXML) 버전 6.20.5002 이상|Windows에서 XML 문서 처리를 지원하는 데 필요합니다.|  
|Microsoft RDC(원격 차등 압축)|네트워크를 통한 데이터 전송을 최적화하는 데 필요합니다.|  
|Microsoft Visual C++ 2013 재배포 가능 버전 12.0.21005.1|클라이언트 작업을 지원하는 데 필요합니다. 이 업데이트를 클라이언트 컴퓨터에 설치한 경우 설치를 완료하려면 컴퓨터를 다시 시작해야 할 수 있습니다.|  
|Microsoft Visual C++ 2005 재배포 가능 버전 8.0.50727.42|버전 1606 이전에서는 Microsoft SQL Server Compact 작업을 지원하는 데 필요합니다.|  
|Windows 이미징 API 6.0.6001.18000|Configuration Manager에서 Windows 이미지 파일(.wim)을 관리하도록 허용하는 데 필요합니다.|  
|Microsoft Policy Platform 1.2.3514.0|클라이언트에서 호환성 설정을 평가하는 데 필요합니다.|  
|Microsoft Silverlight 5.1.41212.0|응용 프로그램 카탈로그 웹 사이트 사용자 환경을 지원하는 데 필요합니다. Configuration Manager 1802부터는 Silverlight가 더 이상 자동으로 설치되지 않습니다. 응용 프로그램 카탈로그의 기본 기능이 이제는 소프트웨어 센터에 포함됩니다. 2018년 6월 1일 이후 출시된 첫 번째 업데이트에서 응용 프로그램 카탈로그 웹 사이트에 대한 지원이 종료됩니다.<!--1356195-->|  
|Microsoft .NET Framework 버전 4.5.2|클라이언트 작업을 지원하는 데 필요합니다. Microsoft.NET Framework 버전 4.5 이상을 설치하지 않은 경우 자동으로 클라이언트 컴퓨터에 설치됩니다. 자세한 내용은 [Microsoft .NET Framework 버전 4.5.2에 대한 추가 세부 정보](#dotNet)를 참조하세요.|  
|Microsoft SQL Server Compact 3.5 SP2 구성 요소|클라이언트 작업과 관련된 정보를 저장하는 데 필요합니다.|  
|Microsoft Windows Imaging 구성 요소|64비트 컴퓨터용 Windows Server 2003 또는 Windows XP SP2의 Microsoft .NET Framework 4.0에 필요합니다.|
|Microsoft Intune PC 소프트웨어 클라이언트|Intune PC 소프트웨어 클라이언트 및 Configuration Manager 클라이언트를 같은 PC에서 실행할 수 없습니다. Configuration Manager 클라이언트를 설치하기 전에 Intune 클라이언트가 제거되었는지 확인하세요.|

####  <a name="dotNet"></a> Microsoft .NET Framework 버전 4.5.2에 대한 추가 세부 정보  

> [!NOTE]  
>  2016년 1월 12일에 .NET 4.0, 4.5 및 4.5.1에 대한 지원이 만료되었습니다. 자세한 내용은 [Microsoft .NET Framework 지원 기간 정책 FAQ](https://support.microsoft.com/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)를 참조하세요.  

 Microsoft.NET Framework 버전 4.5.2의 설치를 완료하려면 다시 시작해야 할 수 있습니다. 시스템 트레이에 **다시 시작 필요** 알림이 표시됩니다. 클라이언트 컴퓨터를 다시 시작해야 하는 일반적인 시나리오:  

-   컴퓨터에서 .NET 응용 프로그램이나 서비스를 실행 중입니다.  

-   .NET 설치에 필요한 소프트웨어 업데이트가 하나 이상 없습니다.  

-   컴퓨터가 이전의 .NET framework 소프트웨어 업데이트 설치 다시 시작을 보류 중입니다.  

 .NET Framework 4.5.2를 설치한 후 추가 업데이트를 설치할 수 있습니다. 해당 업데이트 설치로 인해 컴퓨터를 다시 시작해야 할 수도 있습니다.  

### <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  
 자세한 내용은 [클라이언트에 대한 사이트 시스템 역할 결정](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md)을 참조하세요.  

|||  
|-|-|  
|관리 지점|Configuration Manager 클라이언트를 배포하는 데 관리 지점이 필요하지는 않지만 클라이언트 컴퓨터와 Configuration Manager 서버 간에 정보를 전송하려면 관리 지점이 있어야 합니다. 관리 지점이 없으면 클라이언트 컴퓨터를 관리할 수 없습니다.|  
|배포 지점|배포 지점은 선택 사항이지만 클라이언트 배포 시 권장되는 사이트 시스템 역할입니다. 모든 배포 지점은 클라이언트 원본 파일을 호스팅하기 때문에 클라이언트 배포 중에 컴퓨터가 클라이언트 원본 파일을 다운로드할 가장 가까운 배포 지점을 찾을 수 있습니다. 사이트에 배포 지점이 없으면 컴퓨터가 자신의 관리 지점에서 클라이언트 원본 파일을 다운로드합니다.|  
|대체 상태 지점|대체 상태 지점은 선택 사항이지만 클라이언트 배포 시 권장되는 사이트 시스템 역할입니다. 대체 상태 지점은 클라이언트 배포를 추적하며, Configuration Manager 사이트의 컴퓨터는 관리 지점과 통신할 수 없는 경우에 대체 상태 지점을 통해 상태 메시지를 보낼 수 있습니다.|  
|보고 서비스 지점|보고 서비스 지점은 선택 사항이지만 클라이언트 배포 및 관리와 관련된 보고서를 표시할 수 있으며 권장되는 사이트 시스템 역할입니다. 자세한 내용은 [System Center Configuration Manager의 보고](../../../core/servers/manage/reporting.md)를 참조하세요.|  

### <a name="installation-method-dependencies"></a>설치 방법 종속성  
 다음 전제 조건은 다양한 클라이언트 설치 방법에 따라 달라집니다.  

#### <a name="client-push-installation"></a>클라이언트 강제 설치  

   -   클라이언트 강제 설치 계정은 클라이언트를 설치할 컴퓨터에 연결하는 데 사용되며 **클라이언트 강제 설치 속성** 대화 상자의 **계정** 탭에서 지원됩니다. 이 계정은 대상 컴퓨터에서 로컬 관리자 그룹의 구성원이어야 합니다.  

         클라이언트 강제 설치 계정을 지정하지 않으면 사이트 서버 컴퓨터 계정이 사용됩니다.  

   -   클라이언트를 설치할 컴퓨터가 한 가지 이상의 Configuration Manager 검색 방법으로 검색되어야 합니다.  

   -   컴퓨터에 ADMIN$ 공유가 있습니다.  

   -   Configuration Manager 클라이언트를 검색된 리소스에 자동으로 강제 설치하려면 **클라이언트 강제 설치 속성** 대화 상자에서 **할당된 리소스에 클라이언트 강제 설치 사용**을 선택해야 합니다.  

   -   지원 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점에 연결할 수 있어야 합니다.  


클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치하려면 다음 보안 권한이 있어야 합니다.  

   -   클라이언트 강제 설치 계정 구성: **사이트** 개체에 대한 **수정** 및 읽기 권한.  

   -   클라이언트 강제를 사용하여 클라이언트를 컬렉션, 장치 및 쿼리에 설치: 컬렉션 개체에 대한 **리소스 수정** 및 **읽기** 권한.  


**인프라 관리자** 보안 역할에는 클라이언트 강제 설치를 관리하는 데 필요한 권한이 포함되어 있습니다.  


#### <a name="software-update-point-based-installation"></a>소프트웨어 업데이트 지점 기반 설치  

   -   Active Directory 스키마가 확장되지 않았거나 다른 포리스트에서 클라이언트를 설치하는 경우 그룹 정책을 사용하여 컴퓨터의 레지스트리에서 CCMSetup.exe의 설치 속성을 프로비전해야 합니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법(그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision)을 참조하세요.  

   -   소프트웨어 업데이트 지점에 Configuration Manager 클라이언트를 게시해야 합니다.  

   -   지원 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점에 연결할 수 있어야 합니다.  


Configuration Manager 소프트웨어 업데이트를 관리하는 데 필요한 보안 권한에 대한 내용은 [소프트웨어 업데이트에 대한 필수 조건](../../../sum/plan-design/prerequisites-for-software-updates.md)을 참조하세요.  


#### <a name="group-policy-based-installation"></a>그룹 정책 기반 설치  

   -   Active Directory 스키마가 확장되지 않았거나 다른 포리스트에서 클라이언트를 설치하는 경우 그룹 정책을 사용하여 컴퓨터의 레지스트리에서 CCMSetup.exe의 설치 속성을 프로비전해야 합니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법(그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision)을 참조하세요.  

   -   지원 파일을 다운로드하려면 클라이언트 컴퓨터가 관리 지점에 연결할 수 있어야 합니다.  


#### <a name="logon-script-based-installation"></a>로그온 스크립트 기반 설치  

지원 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점에 연결할 수 있어야 합니다. 아니면 명령줄 속성 **ccmsetup /source**를 사용하여 CCMSetup.exe를 지정해야 합니다.  


#### <a name="manual-installation"></a>수동 설치  

지원 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점에 연결할 수 있어야 합니다. 아니면 명령줄 속성 **ccmsetup /source**를 사용하여 CCMSetup.exe를 지정해야 합니다.  


#### <a name="microsoft-intune-mdm-installation"></a>Microsoft Intune MDM 설치

 - Microsoft Intune 구독 및 적절한 라이선스가 필요합니다.  

 - 인터넷 기반이 아니더라도 장치가 인터넷에 액세스할 수 있어야 합니다.  

 - 사용 사례에 따라 다음 기술 중 하나 또는 둘 모두 필요할 수 있습니다.  

     - Azure Active Directory  

     - 클라우드 관리 게이트웨이  


#### <a name="workgroup-computer-installation"></a>작업 그룹 컴퓨터 설치  

Configuration Manager 사이트 서버 도메인의 리소스에 액세스하려면 해당 사이트에 대한 네트워크 액세스 계정을 구성해야 합니다.  

네트워크 액세스 계정을 구성하는 방법에 대한 자세한 내용은 [콘텐츠 관리의 기본 개념](../../plan-design/hierarchy/fundamental-concepts-for-content-management.md)을 참조하세요.  


#### <a name="software-distribution-based-installation-for-upgrades-only"></a>소프트웨어 배포 기반 설치(업그레이드 전용)  

   -   Active Directory 스키마가 확장되지 않았거나 다른 포리스트에서 클라이언트를 설치하는 경우 그룹 정책을 사용하여 컴퓨터의 레지스트리에서 CCMSetup.exe의 설치 속성을 프로비전해야 합니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법(그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치)](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_Provision)을 참조하세요.  

   -   지원 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점에 연결할 수 있어야 합니다.  


응용 프로그램 관리를 사용하여 Configuration Manager 클라이언트를 업그레이드하는 데 필요한 보안 권한은 [응용 프로그램 관리에 대한 보안 및 개인 정보](../../../apps/plan-design/security-and-privacy-for-application-management.md)를 참조하세요.  


#### <a name="automatic-client-upgrades"></a>자동 클라이언트 업그레이드  

자동 클라이언트 업그레이드를 구성하려면 **전체 관리자** 보안 역할의 구성원이어야 합니다.  


### <a name="firewall-requirements"></a>방화벽 요구 사항  

구성 관리자 클라이언트를 설치할 컴퓨터와 사이트 시스템 서버 사이에 방화벽이 있는 경우 [클라이언트용 Windows 방화벽 및 포트 설정](../../../core/clients/deploy/windows-firewall-and-port-settings-for-clients.md)을 참조하세요.  



##  <a name="BKMK_prereqs_mobiledevices"></a> 모바일 장치 클라이언트에 대한 필수 조건  

모바일 장치에 구성 관리자 클라이언트를 설치하고 등록할 때 이 정보를 사용하여 필수 조건을 확인하세요.  

### <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

-   모바일 장치에 필요한 인증서를 배포하고 관리하는 데 필요한 인증서 템플릿이 있는 Microsoft Microsoft Enterprise CA(인증 기관).  

     발급 CA는 등록 프로세스 중에 모바일 장치 사용자의 인증서 요청을 자동으로 승인해야 합니다.  

     인증서 요구 사항에 대한 자세한 내용은 [인증서 프로필에 대한 보안 및 개인 정보](../../../protect/plan-design/security-and-privacy-for-certificate-profiles.md)를 참조하세요.  

-   모바일 장치 장치를 등록할 수 있는 사용자가 포함된 보안 그룹.  

     이 보안 그룹은 모바일 장치 등록 중에 사용되는 인증서 템플릿을 구성하는 데 사용됩니다.  

-   선택 사항이지만 권장 사항: **ConfigMgrEnroll**이라는 DNS 별칭(CNAME 레코드). 등록 프록시 지점의 서버 이름으로 이 별칭을 입력합니다.  

     이 DNS 별칭은 등록 서비스의 자동 검색을 지원하는 데 필요합니다. 이 DNS 레코드를 구성하지 않으면 사용자가 등록 프로세스 중에 등록 프록시 지점의 이름을 수동으로 지정해야 합니다.  

-   등록 지점 및 등록 프록시 지점 사이트 시스템 역할을 실행할 컴퓨터의 사이트 시스템 역할 종속성.  

     [사이트 시스템 서버에 대해 지원되는 운영 체제](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)를 참조하세요.  

### <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  
 자세한 내용은 [클라이언트에 대한 사이트 시스템 역할 결정](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md)을 참조하세요.  

-   HTTPS 클라이언트 연결용으로 구성되고 모바일 장치에 사용하도록 설정된 관리 지점  

     모바일 장치에 Configuration Manager 클라이언트를 설치하려면 항상 관리 지점이 필요합니다. 관리 지점은 HTTPS용으로 구성하고 모바일 장치에 사용하도록 설정해야 할 뿐 아니라 인터넷 FQDN으로 구성하고 인터넷의 클라이언트 연결을 허용해야 합니다.  

-   등록 지점 및 등록 프록시 지점  

     등록 프록시 지점은 모바일 장치로부터의 등록 요청을 관리하고, 등록 지점은 등록 프로세스를 완료합니다. 등록 지점은 사이트 서버와 동일한 Active Directory 포리스트에 있어야 하지만 등록 프록시 지점은 다른 포리스트에 있을 수 있습니다.  

-   모바일 장치 등록을 위한 클라이언트 설정  

     클라이언트 설정을 구성하여 사용자가 모바일 장치를 등록하고 하나 이상의 등록 프로필을 구성할 수 있도록 허용해야 합니다.  

-   보고 서비스 지점  

     보고 서비스 지점은 선택적이지만, 모바일 장치 등록 및 클라이언트 관리와 관련된 보고서를 표시할 수 있는 사이트 시스템 역할에는 권장됩니다.  

     자세한 내용은 [System Center Configuration Manager의 보고](../../../core/servers/manage/reporting.md)를 참조하세요.  

-   모바일 장치의 등록을 구성하려면 다음 보안 권한을 보유하고 있어야 합니다.  

    -   등록 사이트 시스템 역할 추가, 수정 및 삭제: **사이트** 개체에 대한 **수정** 권한.  

    -   등록에 대해 클라이언트 설정 구성: 기본 클라이언트 설정에는 **사이트** 개체에 대한 **수정** 권한이 필요하고, 사용자 지정 클라이언트 설정에는 **클라이언트 에이전트**  권한이 필요합니다.  

     **전체 관리자** 보안 역할에는 등록 사이트 시스템 역할을 구성하는 데 필요한 권한이 포함됩니다.  

     등록된 모바일 장치를 관리하려면 다음 보안 권한을 보유하고 있어야 합니다.  

    -   모바일 장치 초기화 또는 사용 중지: **컬렉션** 개체에 대한 **리소스 삭제** .  

    -   초기화 또는 사용 중지 명령 취소: **컬렉션** 개체에 대한 **리소스 삭제** .  

    -   모바일 장치 허용 및 차단: **컬렉션** 개체에 대한 **리소스 수정** .  

    -   모바일 장치를 원격으로 잠그거나 모바일 장치의 암호 다시 설정: **컬렉션** 개체에 대한 리소스 **수정** .  

     **운영 관리자** 보안 역할에는 모바일 장치를 관리하는 데 필요한 권한이 포함되어 있습니다.  

     보안 권한을 구성하는 방법에 대한 자세한 내용은 [역할 기반 관리의 기본 사항](../../../core/understand/fundamentals-of-role-based-administration.md) 및 [역할 기반 관리 구성](../../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.  

### <a name="firewall-requirements"></a>방화벽 요구 사항  
라우터, 방화벽과 같은 중간 네트워크 장치 및 적용되는 경우 Windows 방화벽은 모바일 장치 등록과 연결된 트래픽을 허용해야 합니다.  

-   모바일 장치 및 등록 프록시 지점 간: HTTPS(기본적으로 TCP 443)  

-   등록 프록시 지점 및 등록 지점 간: HTTPS(기본적으로 TCP 443)  


프록시 웹 서버를 사용하는 경우 SSL 터널링에 대해 프록시 웹 서버를 구성해야 하며 SSL 브리징은 모바일 장치에 대해 지원되지 않습니다.  
