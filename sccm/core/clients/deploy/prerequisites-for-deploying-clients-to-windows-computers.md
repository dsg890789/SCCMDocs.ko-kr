---
title: Windows 클라이언트 배포 필수 조건
titleSuffix: Configuration Manager
description: Windows 컴퓨터에 구성 관리자 클라이언트를 배포하기 위한 필수 조건을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 1a2a9b48-a95b-4643-b00c-b3079584ae2e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2a830b36bec3d112c0b112d2df6887a84c837fa2
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53418257"
---
# <a name="prerequisites-for-deploying-clients-to-windows-computers-in-configuration-manager"></a>Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

사용 환경에 Configuration Manager 클라이언트를 배포할 경우 다음과 같은 외부 종속성과 제품 내 종속성이 있습니다. 또한, 각 클라이언트 배포 방법마다 클라이언트를 성공적으로 설치하기 위해 충족해야 할 자체 종속성이 있습니다.  

Configuration Manager 클라이언트의 최소 하드웨어 및 OS 요구 사항에 대한 자세한 내용은 [지원되는 구성](/sccm/core/plan-design/configs/supported-configurations)을 참조하세요.  

> [!NOTE]  
>  이 문서에 표시된 소프트웨어 버전 번호는 필요한 최소 버전 번호만 나타냅니다.  



##  <a name="BKMK_prereqs_computers"></a> Windows 클라이언트의 필수 구성 요소  

Windows 디바이스에 Configuration Manager 클라이언트를 설치하는 경우 필수 조건을 확인하려면 다음 정보를 참조하세요.  

### <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

|구성 요소|설명|  
|---|---|  
|Windows Installer 버전 3.1.4000.2435|패키지 및 소프트웨어 업데이트용 Windows Installer 업데이트(.msp) 파일을 사용하도록 지원하는 데 필요합니다.|  
|Microsoft BITS(Background Intelligent Transfer Service) 버전 2.5|클라이언트 컴퓨터와 Configuration Manager 사이트 시스템 간에 정체된 데이터 전송을 허용하는 데 필요합니다. BITS는 클라이언트 설치 시 자동으로 다운로드되지 않습니다. BITS가 컴퓨터에 설치되는 경우 일반적으로 다시 시작해야 설치가 완료됩니다.<br /><br /> 대부분의 운영 체제는 BITS를 포함합니다. 그렇지 않은 경우 Configuration Manager 클라이언트를 설치하기 전에 BITS를 설치합니다.|  
|Microsoft 작업 Scheduler|클라이언트 설치를 완료하려면 클라이언트에서 이 서비스를 사용하도록 설정합니다.|  


### <a name="bkmk_ExternalDependencies"></a> 설치 중 자동으로 다운로드되는 Configuration Manager 외부 종속성  

Configuration Manager 클라이언트에는 외부 종속성이 있습니다. 이러한 종속성은 클라이언트 컴퓨터의 OS 버전 및 설치된 소프트웨어에 따라 다릅니다.  

설치를 완료하기 위해 클라이언트에 이러한 종속성이 필요한 경우에는 자동으로 설치됩니다.  

|구성 요소|설명|  
|---|---|  
|Windows Update 에이전트 버전 7.0.6000.363|Windows에서 업데이트 검색 및 배포를 지원하는 데 필요합니다.|  
|Microsoft Core XML Services(MSXML) 버전 6.20.5002 이상|Windows에서 XML 문서 처리를 지원하는 데 필요합니다.|  
|Microsoft RDC(원격 차등 압축)|네트워크를 통한 데이터 전송을 최적화하는 데 필요합니다.|  
|Microsoft Visual C++ 2013 재배포 가능 버전 12.0.21005.1|클라이언트 작업을 지원하는 데 필요합니다. 이 업데이트를 클라이언트 컴퓨터에 설치하는 경우 설치를 완료하려면 다시 시작이 필요할 수 있습니다.|  
|Microsoft Visual C++ 2005 재배포 가능 버전 8.0.50727.42|버전 1606 이전에서는 Microsoft SQL Server Compact 작업을 지원하는 데 필요합니다.|  
|Windows 이미징 API 6.0.6001.18000|Configuration Manager에서 Windows 이미지 파일(.wim)을 관리하도록 허용하는 데 필요합니다.|  
|Microsoft Policy Platform 1.2.3514.0|클라이언트에서 호환성 설정을 평가하는 데 필요합니다.|  
|Microsoft Silverlight 5.1.41212.0|애플리케이션 카탈로그 웹 사이트 사용자 환경을 지원하는 데 필요합니다. Configuration Manager 1802부터 클라이언트는 Silverlight를 자동으로 설치하지 않습니다. 애플리케이션 카탈로그의 기본 기능이 이제는 소프트웨어 센터에 포함됩니다. 애플리케이션 카탈로그 웹 사이트에 대한 지원은 1806 버전에서 종료됩니다.<!--1356195-->|  
|Microsoft .NET Framework 버전 4.5.2|클라이언트 작업을 지원하는 데 필요합니다. Microsoft.NET Framework 버전 4.5 이상이 설치되지 않은 경우 클라이언트 컴퓨터에 자동으로 설치됩니다. 자세한 내용은 [Microsoft .NET Framework 버전 4.5.2에 대한 추가 세부 정보](#dotNet)를 참조하세요.|  
|Microsoft SQL Server Compact 4.0 SP1 구성 요소|클라이언트 작업과 관련된 정보를 저장하는 데 필요합니다.|  


####  <a name="dotNet"></a> Microsoft .NET Framework 버전 4.5.2에 대한 추가 세부 정보  

> [!NOTE]  
>  .NET 4.0, 4.5 및 4.5.1은 더 이상 지원되지 않습니다. 자세한 내용은 [Microsoft .NET Framework 지원 기간 정책 FAQ](https://support.microsoft.com/help/17455/lifecycle-faq-net-framework)를 참조하세요.  

Microsoft.NET Framework 버전 4.5.2의 설치를 완료하려면 다시 시작이 필요할 수 있습니다. 시스템 트레이에 **다시 시작 필요** 알림이 표시됩니다. 다음과 같은 일반적인 시나리오에서는 클라이언트 컴퓨터를 다시 시작해야 합니다.  

-   컴퓨터에서 .NET 애플리케이션이나 서비스를 실행 중입니다.  

-   .NET 설치에 필요한 소프트웨어 업데이트가 하나 이상 없습니다.  

-   컴퓨터가 이전의 .NET framework 소프트웨어 업데이트 설치 다시 시작을 보류 중입니다.  


.NET Framework 4.5.2가 설치된 다음, 추가 업데이트가 필요할 수 있습니다. 이러한 추가 업데이트로 인해 컴퓨터 다시 시작이 더 필요할 수 있습니다.  


### <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  

자세한 내용은 [클라이언트에 대한 사이트 시스템 역할 결정](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients)을 참조하세요.  

|구성 요소|설명|  
|---|---|  
|관리 지점|Configuration Manager 클라이언트를 배포하려면 관리 지점이 필요하지 않습니다. 클라이언트에는 사이트와 정보를 전송하기 위한 관리 지점이 필요합니다. 관리 지점이 없으면 클라이언트 컴퓨터를 관리할 수 없습니다.|  
|배포 지점|배포 지점은 선택 사항이지만 클라이언트 배포 및 관리 시 권장되는 사이트 시스템 역할입니다. 모든 배포 지점에서 클라이언트 원본 파일을 호스트합니다. 클라이언트 배포 또는 업데이트 중에 클라이언트는 원본 파일을 다운로드할 가장 가까운 배포 지점을 찾습니다. 사이트에 배포 지점이 없으면 컴퓨터가 자체 관리 지점에서 클라이언트 원본 파일을 다운로드합니다.|  
|대체 상태 지점|대체 상태 지점은 선택 사항이지만 클라이언트 배포 시 권장되는 사이트 시스템 역할입니다. 대체 상태 지점은 클라이언트 배포를 추적하며, Configuration Manager 사이트의 컴퓨터는 관리 지점과 통신할 수 없는 경우에 대체 상태 지점을 통해 상태 메시지를 보낼 수 있습니다.|  
|보고 서비스 지점|보고 서비스 지점은 선택 사항이지만 권장되는 사이트 시스템 역할입니다. 클라이언트 배포 및 관리와 관련된 보고서를 표시합니다. 자세한 내용은 [Configuration Manager의 보고 기능](/sccm/core/servers/manage/reporting)을 참조하세요.|  


### <a name="installation-method-dependencies"></a>설치 방법 종속성  

다음 전제 조건은 다양한 클라이언트 설치 방법에 따라 달라집니다.  

#### <a name="client-push-installation"></a>클라이언트 강제 설치  

   -   사이트는 클라이언트 강제 설치 계정을 사용하여 클라이언트를 설치할 컴퓨터에 연결합니다. 이 계정은 클라이언트 강제 설치 속성의 **계정** 탭에서 지정합니다. 이 계정은 대상 컴퓨터에서 로컬 관리자 그룹의 구성원이어야 합니다.  

         클라이언트 강제 설치 계정을 지정하지 않으면 사이트 서버는 해당 컴퓨터 계정을 사용합니다.  

   -   사이트는 클라이언트를 설치할 컴퓨터를 검색해야 합니다. Configuration Manager 검색 방법이 하나 이상 필요합니다.  

   -   컴퓨터에 ADMIN$ 공유가 있습니다.  

   -   검색된 리소스에 Configuration Manager 클라이언트를 자동으로 푸시하려면 클라이언트 강제 설치 속성에서 **Enable client push installation to assigned resources**(할당된 리소스에 클라이언트 강제 설치 사용) 옵션을 선택합니다.  

   -   클라이언트 컴퓨터가 원본 파일을 다운로드하려면 배포 지점이나 관리 지점과 통신해야 합니다.  

   -   버전 1806부터, Kerberos 상호 인증이 필요한 경우에는 클라이언트가 신뢰할 수 있는 Active Directory 포리스트에 있어야 합니다. Windows의 Kerberos는 상호 인증을 위해 Active Directory를 사용합니다.<!--1358204-->  


클라이언트 강제를 사용하려면 다음 보안 권한이 필요합니다.  

   -   클라이언트 강제 설치 계정을 구성하려면: **사이트** 개체에 대한 **수정** 및 **읽기** 권한이 필요합니다.  

   -   클라이언트 강제 설치를 사용하여 컬렉션, 장치 및 쿼리에 클라이언트 설치: **컬렉션** 개체에 대한 **리소스 수정** 및 **읽기** 권한이 필요합니다.  


**인프라 관리자** 기본 보안 역할에는 클라이언트 강제 설치를 관리하는 데 필요한 권한이 포함됩니다.  


#### <a name="software-update-point-based-installation"></a>소프트웨어 업데이트 지점 기반 설치  

   -   Active Directory 스키마를 확장하지 않았거나 다른 포리스트에서 클라이언트를 설치하는 경우에는 그룹 정책을 사용하여 CCMSetup.exe의 설치 매개 변수를 프로비전합니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Provision)을 참조하세요.  

   -   소프트웨어 업데이트 지점에 Configuration Manager 클라이언트 게시  

   -   원본 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점과 통신해야 합니다.  


Configuration Manager 소프트웨어 업데이트를 관리하는 데 필요한 보안 권한에 대한 내용은 [소프트웨어 업데이트에 대한 필수 조건](/sccm/sum/plan-design/prerequisites-for-software-updates)을 참조하세요.  


#### <a name="group-policy-based-installation"></a>그룹 정책 기반 설치  

   -   Active Directory 스키마를 확장하지 않았거나 다른 포리스트에서 클라이언트를 설치하는 경우에는 그룹 정책을 사용하여 CCMSetup.exe의 설치 매개 변수를 프로비전합니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Provision)을 참조하세요.  

   -   원본 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점과 통신해야 합니다.  


#### <a name="logon-script-based-installation"></a>로그온 스크립트 기반 설치  

원본 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점과 통신해야 합니다. 다음 명령줄 매개 변수로 CCMSetup.exe를 지정한 경우는 제외됩니다. `ccmsetup /source`  


#### <a name="manual-installation"></a>수동 설치  

원본 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점과 통신해야 합니다. 다음 명령줄 매개 변수로 CCMSetup.exe를 지정한 경우는 제외됩니다. `ccmsetup /source`  


#### <a name="microsoft-intune-mdm-installation"></a>Microsoft Intune MDM 설치

 - Microsoft Intune 구독 및 적절한 라이선스가 필요합니다.  

 - 인터넷 기반이 아니더라도 디바이스에 인터넷 액세스가 필요합니다.  

 - 사용 사례에 따라 다음 기술 중 하나 또는 둘 모두가 필요할 수 있습니다.  

     - Azure Active Directory  

     - 클라우드 관리 게이트웨이  


#### <a name="workgroup-computer-installation"></a>작업 그룹 컴퓨터 설치  

Configuration Manager 사이트 서버 도메인의 리소스에 액세스하려면 사이트에 대한 네트워크 액세스 계정을 구성합니다.  

네트워크 액세스 계정을 구성하는 방법에 대한 자세한 내용은 [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)을 참조하세요.  


#### <a name="software-distribution-based-installation-for-upgrades-only"></a>소프트웨어 배포 기반 설치(업그레이드 전용)  

   -   Active Directory 스키마를 확장하지 않았거나 다른 포리스트에서 클라이언트를 설치하는 경우에는 그룹 정책을 사용하여 CCMSetup.exe의 설치 매개 변수를 프로비전합니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Provision)을 참조하세요.   

   -   원본 파일을 다운로드하려면 클라이언트 컴퓨터가 배포 지점이나 관리 지점과 통신해야 합니다.  


애플리케이션 관리를 사용하여 Configuration Manager 클라이언트를 업그레이드하는 데 필요한 보안 권한은 [애플리케이션 관리에 대한 보안 및 개인 정보](/sccm/apps/plan-design/security-and-privacy-for-application-management)를 참조하세요.  


#### <a name="automatic-client-upgrades"></a>자동 클라이언트 업그레이드  

자동 클라이언트 업그레이드를 구성하려면 **전체 관리자** 보안 역할의 구성원이어야 합니다.  


### <a name="firewall-requirements"></a>방화벽 요구 사항  

Configuration Manager 클라이언트를 설치할 컴퓨터와 사이트 시스템 서버 사이에 방화벽이 있는 경우에는 [클라이언트용 Windows 방화벽 및 포트 설정](/sccm/core/clients/deploy/windows-firewall-and-port-settings-for-clients)을 참조하세요.  



##  <a name="BKMK_prereqs_mobiledevices"></a> 모바일 디바이스 클라이언트에 대한 필수 조건  

모바일 디바이스에 구성 관리자 클라이언트를 설치하고 등록할 때 이 정보를 사용하여 필수 조건을 확인하세요.  

### <a name="dependencies-external-to-configuration-manager"></a>Configuration Manager 외부 종속성  

-   모바일 디바이스에 필요한 인증서를 배포하고 관리하는 데 필요한 인증서 템플릿이 있는 Microsoft Microsoft Enterprise CA(인증 기관).  

     발급 CA는 등록 프로세스 중에 모바일 디바이스 사용자의 인증서 요청을 자동으로 승인해야 합니다.  

     인증서 요구 사항에 대한 자세한 내용은 [인증서 프로필에 대한 보안 및 개인 정보](/sccm/protect/plan-design/security-and-privacy-for-certificate-profiles)를 참조하세요.  

-   모바일 디바이스 디바이스를 등록할 수 있는 사용자가 포함된 보안 그룹.  

     이 보안 그룹은 모바일 디바이스 등록 중에 사용되는 인증서 템플릿을 구성하는 데 사용됩니다.  

-   선택 사항이지만 권장 사항: **ConfigMgrEnroll**이라는 DNS 별칭(CNAME 레코드). 등록 프록시 지점의 서버 이름으로 이 별칭을 입력합니다.  

     이 DNS 별칭은 등록 서비스의 자동 검색을 지원하는 데 필요합니다. 이 DNS 레코드를 구성하지 않으면 사용자가 등록 프로세스 중에 등록 프록시 지점의 이름을 수동으로 지정해야 합니다.  

-   등록 지점 및 등록 프록시 지점 사이트 시스템 역할을 실행할 컴퓨터의 사이트 시스템 역할 종속성.  

     자세한 내용은 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers)를 참조하세요.  


### <a name="configuration-manager-dependencies"></a>Configuration Manager 종속성  

자세한 내용은 [클라이언트에 대한 사이트 시스템 역할 결정](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients)을 참조하세요.  

- HTTPS 클라이언트 연결용으로 구성되고 모바일 디바이스에 사용하도록 설정된 관리 지점  

   모바일 디바이스에 Configuration Manager 클라이언트를 설치하려면 항상 관리 지점이 필요합니다. 관리 지점은 HTTPS용으로 구성하고 모바일 디바이스에 사용하도록 설정해야 할 뿐 아니라 인터넷 FQDN으로 구성하고 인터넷의 클라이언트 연결을 허용해야 합니다.  

- 등록 지점 및 등록 프록시 지점  

   등록 프록시 지점은 모바일 디바이스로부터의 등록 요청을 관리하고, 등록 지점은 등록 프로세스를 완료합니다. 등록 지점은 사이트 서버와 동일한 Active Directory 포리스트에 있어야 하지만 등록 프록시 지점은 다른 포리스트에 있을 수 있습니다.  

- 모바일 디바이스 등록을 위한 클라이언트 설정  

   클라이언트 설정을 구성하여 사용자가 모바일 디바이스를 등록하고 하나 이상의 등록 프로필을 구성할 수 있도록 허용해야 합니다.  

- 보고 서비스 지점  

   보고 서비스 지점은 선택적이지만, 모바일 디바이스 등록 및 클라이언트 관리와 관련된 보고서를 표시할 수 있는 사이트 시스템 역할에는 권장됩니다.  

   자세한 내용은 [Configuration Manager의 보고 기능](/sccm/core/servers/manage/reporting)을 참조하세요.  

- 모바일 디바이스의 등록을 구성하려면 다음 보안 권한을 보유하고 있어야 합니다.  

  - 등록 사이트 시스템 역할을 추가, 수정 및 삭제하려면: **사이트** 개체에 대한 **수정** 권한이 필요합니다.  

  - 등록에 대한 클라이언트 설정을 구성하려면: 기본 클라이언트 설정에는 **사이트** 개체에 대한 **수정** 권한이 필요하고, 사용자 지정 클라이언트 설정에는 **클라이언트 에이전트** 권한이 필요합니다.  

    **전체 관리자** 기본 보안 역할에는 등록 사이트 시스템 역할을 구성하는 데 필요한 권한이 포함됩니다.  

    등록된 모바일 디바이스를 관리하려면 다음 보안 권한을 보유하고 있어야 합니다.  

  - 모바일 장치를 초기화하거나 사용을 중지하려면 **컬렉션** 개체에 대한 **리소스 삭제** 권한이 필요합니다.  

  - 초기화 또는 사용 중지 명령을 취소하려면 **컬렉션** 개체에 대한 **리소스 삭제** 권한이 필요합니다.  

  - 모바일 장치를 허용 및 차단하려면: **컬렉션** 개체에 대한 **리소스 수정** 권한이 필요합니다.  

  - 모바일 장치를 원격으로 잠그거나 모바일 장치의 암호를 다시 설정하려면 **컬렉션** 개체에 대한 **리소스 수정** 권한이 필요합니다.  

    **운영 관리자** 기본 보안 역할에는 모바일 디바이스를 관리하는 데 필요한 권한이 포함됩니다.  

    보안 권한을 구성하는 방법에 대한 자세한 내용은 [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration) 및 [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)을 참조하세요.  


### <a name="firewall-requirements"></a>방화벽 요구 사항  

라우터, 방화벽과 같은 중간 네트워크 디바이스 및 적용되는 경우 Windows 방화벽은 모바일 디바이스 등록과 연결된 트래픽을 허용해야 합니다.  

-   모바일 장치 및 등록 프록시 지점 사이의 HTTPS(기본적으로 TCP 443)  

-   등록 프록시 지점 및 등록 지점 사이의 HTTPS(기본적으로 TCP 443)  


프록시 웹 서버를 사용하는 경우에는 SSL 터널링에 대해 구성되어야 합니다. 모바일 디바이스에서는 SSL 브리징이 지원되지 않습니다.  
