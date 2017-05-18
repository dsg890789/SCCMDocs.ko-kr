---
title: "운영 체제 배포를 위한 인프라 요구 사항 | Microsoft 문서"
description: "운영 체제 배포를 위해 System Center 2012 Configuration Manager를 사용하기 전에 외부 종속성과 제품 종속성을 알고 있어야 합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: 24
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 065b1fcb25d7c7845b6f26e757b36e7fb97ce013
ms.openlocfilehash: ef4536578456c13de5afaa5cd1977d2e6b4b6bd1
ms.contentlocale: ko-kr
ms.lasthandoff: 05/10/2017


---
# <a name="infrastructure-requirements-for-operating-system-deployment-in-system-center-configuration-manager"></a>System Center Configuration Manager의 운영 체제 배포에 대한 인프라 요구 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center 2012 Configuration Manager의 운영 체제 배포에는 외부 종속성과 제품 내 종속성이 있습니다. 다음 섹션을 사용하여 운영 체제 배포를 위한 준비를 수행하세요.  

##  <a name="BKMK_ExternalDependencies"></a> Configuration Manager 외부 종속성  
 다음은 Configuration Manager에서 운영 체제를 배포하는 데 필요한 외부 도구, 설치 키트 및 운영 체제에 대한 정보를 제공합니다.  

### <a name="windows-adk-for-windows-10"></a>Windows 10용 Windows ADK  
 Windows ADK는 Windows 운영 체제의 구성과 배포를 지원하는 도구 및 설명서 세트입니다. Configuration Manager는 Windows ADK를 사용하여 Windows 설치를 자동화하고, Windows 이미지를 캡처하며, 사용자 프로필 및 데이터를 마이그레이션하는 등 여러 작업을 수행합니다.  

 다음 Windows ADK 기능은 계층 내 최상위 사이트의 사이트 서버, 계층 내 각 기본 사이트의 사이트 서버, 그리고 SMS 공급자 사이트 시스템 서버에 설치해야 합니다.  

-   USMT(사용자 상태 마이그레이션 도구) <sup>1</sup>  

-   Windows 배포 도구  

-   Windows PE(Windows 사전 설치 환경)  

 <sup>1</sup> SMS 공급자 사이트 시스템 서버에는 USMT가 필요하지 않습니다.  

> [!NOTE]  
>  Configuration Manager 사이트를 설치하기 전에 중앙 관리 사이트 또는 기본 사이트 서버를 호스트할 각 컴퓨터에 수동으로 Windows ADK를 설치해야 합니다.  

 자세한 내용은 다음을 참조하십시오.  

-   [IT 전문가를 위한 Windows 10용 Windows ADK 시나리오](https://technet.microsoft.com/library/mt280162\(v=vs.85\).aspx)  

-   [Windows 10용 Windows ADK 다운로드](https://msdn.microsoft.com/windows/hardware/dn913721.aspx#adkwin10)  

-   [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)  


### <a name="user-state-migration-tool-usmt"></a>USMT(사용자 상태 마이그레이션 도구)  
 Configuration Manager에서는 USMT 10 원본 파일을 포함하는 USMT 패키지를 사용하여 사용자 상태를 운영 체제 배포의 일부로 캡처하고 복원합니다. 최상위 사이트의 Configuration Manager 설치 프로그램에서 자동으로 USMT 패키지를 만듭니다. USMT 10은 Windows 7, Windows 8, Windows 8.1 및 Windows 10의 사용자 상태를 캡처할 수 있습니다. USMT 10은 Windows 10용 Windows ADK(Windows 평가 및 배포 키트)에 배포됩니다.  

 자세한 내용은 다음을 참조하세요.  

-   [USMT 10에 대한 일반 마이그레이션 시나리오](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)  

-   [사용자 상태 관리](../get-started/manage-user-state.md)  

### <a name="windows-pe"></a>Windows PE  
 Windows PE는 부팅 이미지에서 컴퓨터를 시작하는 데 사용됩니다. Windows PE는 제한된 서비스를 갖는 Windows 운영 체제로서 Windows 운영 체제의 설치 전과 배포 시에 사용됩니다. 다음에는 Configuration Manager 버전, 지원되는 Windows ADK 버전, Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 기반 Windows PE 버전, DISM을 통해 사용자 지정하여 Configuration Manager의 지정된 버전에 추가할 수 있는 부팅 이미지의 기반 Windows PE 버전 등이 나와 있습니다.  

#### <a name="configuration-manager-version-1511"></a>Configuration Manager 버전 1511  
 다음에는 지원되는 Windows ADK 버전, Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 기반 Windows PE 버전, DISM을 통해 사용자 지정하여 Configuration Manager에 이미지를 추가할 수 있는 부팅 이미지의 기반 Windows PE 버전이 나와 있습니다.  

-   **Windows ADK 버전**  

     Windows 10용 Windows ADK  

-   **Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 Windows PE 버전**  

     Windows PE 10  

-   **Configuration Manager 콘솔에서 사용자 지정할 수 없지만 지원되는 부팅 이미지의 Windows PE 버전**  

     Windows PE 3.1<sup>1</sup> 및 Windows PE 5  

     <sup>1</sup> 부팅 이미지가 Windows PE 3.1을 기반으로 하는 경우에만 Configuration Manager에 부팅 이미지를 추가할 수 있습니다. Windows 7 SP1용 Windows AIK 추가 기능을 설치하여 Windows 7 SP1용 Windows AIK 추가 기능(Windows PE 3.1에 기반)이 포함된 Windows 7용 Windows AIK(Windows PE 3에 기반)로 업그레이드하세요. [Microsoft 다운로드 센터](http://www.microsoft.com/download/details.aspx?id=5188)에서 Windows 7 SP1용 Windows AIK 추가 기능을 다운로드할 수 있습니다.  

     예를 들어 Configuration Manager를 설치한 경우 Configuration Manager 콘솔에서 Windows 10용 Windows ADK(Windows PE 10 기반)의 부팅 이미지를 사용자 지정할 수 있습니다. 그러나 Windows PE 5를 기반으로 하는 부팅 이미지가 지원되지만 여러 컴퓨터의 부팅 이미지를 사용자 지정하고 Windows 8용 Windows ADK와 함께 설치된 DISM 버전을 사용해야 합니다. 그런 다음 부팅 이미지를 Configuration Manager 콘솔에 추가할 수 있습니다. 부팅 이미지를 사용자 지정하고(옵션 구성 요소 및 드라이버 추가), 부팅 이미지를 지원하는 명령을 사용하고, 부팅 이미지를 Configuration Manager 콘솔에 추가하고, 배포 지점을 부팅 이미지로 업데이트하는 단계에 대한 자세한 내용은 [부팅 이미지 사용자 지정](../get-started/customize-boot-images.md)을 참조하세요. 부팅 이미지에 대한 자세한 내용은 [부팅 이미지 관리](../get-started/manage-boot-images.md)를 참조하세요.  

### <a name="windows-server-update-services-wsus"></a>WSUS(Windows Server Update Services)  
다음 WSUS 4.0 핫픽스를 설치해야 합니다.
  - [Hotfix 3095113](https://support.microsoft.com/kb/3095113) 이 설치된 WSUS 4.0은 Windows 10을 지원하는 데 필요하며, 소프트웨어 업데이트 인프라를 사용하여 Windows 10 기능 업그레이드를 가져옵니다. WSUS 3.2가 있는 경우 작업 순서를 사용하여 Windows 10을 업그레이드해야 합니다. 자세한 내용은 [Windows as a Service 관리](../deploy-use/manage-windows-as-a-service.md)를 참조하세요.  
  - Windows 10 서비스를 사용하여 컴퓨터를 Windows 10 1주년 업데이트 및 후속 버전으로 업그레이드하려면 [핫픽스 3159706](https://support.microsoft.com/kb/3159706)이 필요합니다. 이 핫픽스를 설치하기 위해 수행해야 하는 수동 단계는 지원 문서에 설명되어 있습니다. 자세한 내용은 [Windows as a Service 관리](../deploy-use/manage-windows-as-a-service.md)를 참조하세요.


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>사이트 시스템 서버의 IIS(인터넷 정보 서비스)  
 IIS는 배포 지점, 상태 마이그레이션 지점 및 관리 지점에 필요합니다. 이 요구 사항에 대한 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](../../core/plan-design/configs/site-and-site-system-prerequisites.md)을 참조하세요.  

### <a name="windows-deployment-services-wds"></a>WDS(Windows 배포 서비스)  
 WDS는 PXE 배포 시, 멀티캐스트를 사용하여 대역폭을 최적화할 때, 그리고 이미지의 오프라인 서비스 시에 필요합니다. 원격 서버에 공급자가 설치되어 있는 경우 사이트 서버와 원격 공급자에 WDS를 설치해야 합니다. 자세한 내용은 이 항목에서 [Windows 배포 서비스](#BKMK_WDS) 섹션을 참조하세요.  

### <a name="dynamic-host-configuration-protocol-dhcp"></a>DHCP(Dynamic Host Configuration Protocol)  
 DHCP는 PXE 배포에 필요합니다. PXE를 사용하여 운영 체제를 배포하려면 활성 호스트를 포함하는 작동 중인 DHCP 서버가 있어야 합니다. PXE 배포에 대한 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md)를 참조하세요.  

### <a name="supported-operating-systems-and-hard-disk-configurations"></a>지원되는 운영 체제 및 하드 디스크 구성  
 운영 체제를 배포할 때 Configuration Manager에서 지원되는 운영 체제 버전 및 하드 디스크 구성에 대한 자세한 내용은 [지원되는 운영 체제](#BKMK_SupportedOS) 및 [지원되는 디스크 구성](#BKMK_SupportedDiskConfig)을 참조하세요.  

### <a name="windows-device-drivers"></a>Windows 장치 드라이버  
 Windows 장치 드라이버는 대상 컴퓨터에 운영 체제를 설치할 경우와 부팅 이미지를 사용하여 Windows PE를 실행할 경우에 사용할 수 있습니다. 장치 드라이버에 대한 자세한 내용은 [드라이버 관리](../get-started/manage-drivers.md)를 참조하세요.  

##  <a name="BKMK_InternalDependencies"></a> Configuration Manager 종속성  
 다음에서는 Configuration Manager 운영 체제 배포 필수 조건에 대한 정보를 제공합니다.  

### <a name="operating-system-image"></a>운영 체제 이미지  
 Configuration Manager의 운영 체제 이미지는 WIM(Windows Imaging) 형식 파일으로 저장되며 컴퓨터에 운영 체제를 성공적으로 설치하고 구성하는 데 필요한 참조 파일 및 폴더의 압축된 컬렉션을 나타냅니다. 자세한 내용은 [운영 체제 이미지 관리](../get-started/manage-operating-system-images.md)를 참조하세요.  

### <a name="driver-catalog"></a>드라이버 카탈로그  
 장치 드라이버를 배포하려면 장치 드라이버를 가져와서 사용하도록 설정한 다음 Configuration Manager 클라이언트가 액세스할 수 있는 배포 지점에서 활성화해야 합니다. 드라이버 카탈로그에 대한 자세한 내용은 [드라이버 관리](../get-started/manage-drivers.md)를 참조하세요.  

### <a name="management-point"></a>관리 지점  
 관리 지점은 클라이언트 컴퓨터와 Configuration Manager 사이트 간에 정보를 전송합니다. 클라이언트에서는 관리 지점을 사용하여 운영 체제 배포를 완료하는 데 필요한 작업 순서를 실행합니다.  

 작업 순서에 대한 자세한 내용은 [작업 자동화에 대한 계획 고려 사항](planning-considerations-for-automating-tasks.md)을 참조하세요.  

### <a name="distribution-point"></a>배포 지점  
 대부분의 배포에서는 운영 체제 배포에 사용되는 데이터(예: 운영 체제 이미지 또는 장치 드라이버 패키지)를 저장하기 위해 배포 지점을 사용합니다. 일반적으로 작업 순서는 배포 지점에서 데이터를 검색하여 운영 체제를 배포합니다.  

 배포 지점을 설치하고 콘텐츠를 관리하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

### <a name="pxe-enabled-distribution-point"></a>PXE 사용 배포 지점  
 PXE에서 시작한 배포를 배포하려면 배포 지점에서 클라이언트의 PXE 요청을 허용하도록 구성해야 합니다. 배포 지점을 구성하는 방법에 대한 자세한 내용은 [배포 지점 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#pxe)을 참조하세요.  

### <a name="multicast-enabled-distribution-point"></a>멀티캐스트 사용 배포 지점  
 멀티캐스트를 사용하여 운영 체제 배포를 최적화하려면 배포 지점에서 멀티캐스트를 지원하도록 구성해야 합니다. 배포 지점을 구성하는 방법에 대한 자세한 내용은 [배포 지점 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast)을 참조하세요.   

### <a name="state-migration-point"></a>상태 마이그레이션 지점  
 사용자 상태 데이터를 동시에 캡처 및 복원하고 배포를 새로 고칠 경우 상태 마이그레이션 지점에서 다른 컴퓨터의 사용자 상태 데이터를 저장하도록 구성해야 합니다.  

 상태 마이그레이션 지점을 구성하는 방법에 대한 자세한 내용은 [상태 마이그레이션 지점](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints)을 참조하세요.  

 사용자 상태를 캡처 및 복원하는 방법에 대한 자세한 내용은 [사용자 상태 관리](../get-started/manage-user-state.md)를 참조하세요.  

### <a name="service-connection-point"></a>서비스 연결 지점  
 WaaS(Windows as a Service)를 사용하여 Windows 10 현재 분기를 배포할 때 서비스 연결 지점이 설치되어 있어야 합니다. 자세한 내용은 [Windows as a Service 관리](../deploy-use/manage-windows-as-a-service.md)를 참조하세요.  

### <a name="reporting-services-point"></a>보고 서비스 지점  
 운영 체제 배포에 Configuration Manager 보고서를 사용하려면 보고 서비스 지점을 설치하고 구성해야 합니다. 자세한 내용은 [보고](../../core/servers/manage/reporting.md)를 참조하세요.  

### <a name="security-permissions-for-operating-system-deployments"></a>운영 체제 배포를 위한 보안 권한  
 **운영 체제 배포 관리자** 보안 역할은 변경이 불가능한 기본 제공 역할입니다. 그러나 이 역할을 복사하여 변경한 다음 이러한 변경 내용을 새 사용자 지정 보안 역할로 저장할 수 있습니다. 다음은 운영 체제 배포에 직접 적용되는 일부 권한입니다.  

-   **부팅 이미지 패키지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

-   **장치 드라이버**: 만들기, 삭제, 수정, 폴더 수정, 보고서 수정, 개체 이동, 읽기, 보고서 실행  

-   **드라이버 패키지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

-   **운영 체제 이미지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

-   **운영 체제 설치 패키지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

-   **작업 순서 패키지**: 만들기, 작업 순서 미디어 만들기, 삭제, 수정, 폴더 수정, 보고서 수정, 개체 이동, 읽기, 보고서 실행, 보안 범위 설정  

 보안 역할에 대한 자세한 내용은 [사용자 지정 보안 역할 만들기](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole)를 참조하세요.  

### <a name="security-scopes-for-operating-system-deployments"></a>운영 체제 배포를 위한 보안 범위  
 관리자에게 운영 체제 배포에서 사용되는 보안 개체(예: 운영 체제 및 부팅 이미지, 드라이버 패키지, 작업 순서 패키지 등)에 대한 액세스 권한을 제공하려면 보안 범위를 사용합니다. 자세한 내용은 [보안 범위](../../core/understand/fundamentals-of-role-based-administration.md#bkmk_PlanScope)를 참조하세요.  

##  <a name="BKMK_WDS"></a> Windows 배포 서비스  
 WDS(Windows 배포 서비스)는 PXE 또는 멀티캐스트를 지원하기 위해 구성한 배포 지점과 동일한 서버에 설치해야 합니다. WDS가 서버 운영 체제에 포함되어 있습니다. PXE 배포를 실행할 때 WDS는 PXE 부팅을 수행하는 서비스입니다. 배포 지점이 설치되고 이 배포 지점이 PXE를 사용하도록 설정되면 Configuration Manager에서는 WDS PXE 부팅 기능을 사용하는 공급자를 WDS에 설치합니다.  

> [!NOTE]  
>  서버를 다시 시작해야 할 경우 WDS 설치는 실패할 수도 있습니다.  

 그 밖에 고려해야 할 다른 WDS 구성은 다음과 같습니다.  

-   서버에 WDS를 설치하려면 관리자가 로컬 관리자 그룹의 구성원이어야 합니다.  

-   WDS 서버는 Active Directory 도메인의 구성원이거나 Active Directory 도메인의 도메인 컨트롤러여야 합니다. 모든 Windows 도메인 및 포리스트 구성은 WDS를 지원합니다.  

-   원격 서버에 공급자가 설치되어 있는 경우 사이트 서버와 원격 공급자에 WDS를 설치해야 합니다.  

###  <a name="BKMK_WDSandDHCP"></a> WDS 및 DHCP가 동일한 서버에 있을 때 고려할 사항  
 배포 지점을 DHCP가 실행되는 서버에서 함께 호스트하려면 다음과 같은 구성상의 문제를 고려하세요.  

-   활성 영역을 포함하는 작동 중인 DHCP 서버가 있어야 합니다. Windows 배포 서비스는 PXE를 사용하며, PXE에는 DHCP 서버가 필요합니다.  

-   DHCP 및 Windows 배포 서비스에서는 모두 포트 번호 67을 사용해야 합니다. Windows 배포 서비스와 DHCP를 함께 호스트하는 경우에는 PXE용으로 구성된 배포 지점 또는 DHCP를 별도의 서버로 이동할 수 있습니다. 또는 다음 절차에 따라 Windows 배포 서비스 서버가 다른 포트에서 수신하도록 구성할 수 있습니다.  

    #### <a name="to-configure-the-windows-deployment-services-server-to-listen-on-a-different-port"></a>Windows 배포 서비스 서버가 다른 포트에서 수신하도록 구성하려면  

    1.  다음 레지스트리 키를 수정합니다.  

         **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE**  

    2.  레지스트리 값을 다음과 같이 설정합니다. **UseDHCPPorts = 0**  

    3.  새 구성을 적용하려면 서버에서 다음 명령을 실행합니다.  

         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  

-   Windows 배포 서비스를 실행하려면 DNS 서버가 필요합니다.  

-   Windows 배포 서비스 서버에서 다음 UDP 포트가 열려 있어야 합니다.  

    -   포트 67(DHCP)  

    -   포트 69(TFTP)  

    -   포트 4011(PXE)  

    > [!NOTE]  
    >  또한 서버에서 DHCP 권한 부여가 필요한 경우 해당 서버에 DHCP 클라이언트 포트 68이 열려 있어야 합니다.  

##  <a name="BKMK_SupportedOS"></a> 지원되는 운영 체제  
 [클라이언트 및 장치에서 지원되는 운영 체제](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)에 지원되는 클라이언트 운영 체제로 나열된 모든 Windows 운영 체제를 운영 체제 배포에 사용할 수 있습니다.  

##  <a name="BKMK_SupportedDiskConfig"></a> 지원되는 디스크 구성  
 Configuration Manager 운영 체제 배포에 지원되는 참조 및 대상 컴퓨터의 하드 디스크 구성 조합은 다음 표와 같습니다.  

|참조 컴퓨터 하드 디스크 구성|대상 컴퓨터 하드 디스크 구성|  
|------------------------------------------------|--------------------------------------------------|  
|기본 디스크|기본 디스크|  
|동적 디스크의 단순 볼륨|동적 디스크의 단순 볼륨|  

 Configuration Manager는 단순 볼륨으로 구성된 컴퓨터에서만 운영 체제 이미지 캡처를 지원합니다. 다음 하드 디스크 구성은 지원하지 않습니다.  

-   스팬 볼륨  

-   스트라이프 볼륨(RAID 0)  

-   미러 볼륨(RAID 1)  

-   패리티 볼륨(RAID 5)  

 다음 표에서는 Configuration Manager 운영 체제 배포에서 지원되지 않는 참조 및 대상 컴퓨터의 추가 하드 디스크 구성을 보여 줍니다.  

|참조 컴퓨터 하드 디스크 구성|대상 컴퓨터 하드 디스크 구성|  
|------------------------------------------------|--------------------------------------------------|  
|기본 디스크|동적 디스크|  

## <a name="next-steps"></a>다음 단계
[운영 체제 배포 준비](../get-started/prepare-for-operating-system-deployment.md)

