---
title: OSD 인프라 요구 사항
titleSuffix: Configuration Manager
description: 외부 및 제품 종속성과 Configuration Manager의 OS 배포에 대한 요구 사항을 알아봅니다.
ms.date: 10/02/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 03ec9c046e1b32f137777f15393b5d26b49e5520
ms.sourcegitcommit: 265d38d55ca0db043e3a7131a56f123e1d98aa5b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48236160"
---
# <a name="infrastructure-requirements-for-os-deployment-in-configuration-manager"></a>Configuration Manager의 OS 배포에 대한 인프라 요구 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 OS 배포에는 외부 종속성뿐만 아니라 제품 내 종속성이 있습니다. 이 아티클을 사용하여 OS 배포를 위한 인프라를 준비할 수 있습니다.  



##  <a name="BKMK_ExternalDependencies"></a> Configuration Manager에 대한 외부 종속성  

이 섹션은 Configuration Manager에서 운영 체제를 배포하는 데 필요한 외부 도구, 설치 키트 및 OS 버전에 대한 정보를 제공합니다.  

### <a name="windows-adk-for-windows-10"></a>Windows 10용 Windows ADK  

Windows ADK(Assessment and Deployment Kit)는 Windows의 구성과 배포를 지원하는 도구 및 설명서 집합입니다. Configuration Manager는 Windows ADK를 사용하여 Windows를 설치하고, 이미지를 캡처하고, 사용자 프로필 및 데이터를 마이그레이션하는 등의 작업을 자동화합니다.  

자세한 내용은 다음 아티클을 참조하세요.  

- [IT 전문가를 위한 Windows 10용 Windows ADK 시나리오](https://docs.microsoft.com/windows/deployment/windows-adk-scenarios-for-it-pros)  

- [Windows 10용 Windows ADK 다운로드](https://docs.microsoft.com/windows-hardware/get-started/adk-install)  

- [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10)  


#### <a name="site-systems"></a>사이트 시스템
Windows ADK는 다음 사이트 시스템 서버에 대한 전제 조건입니다.

- 계층에 있는 최상위 사이트의 사이트 서버  

- 계층에 있는 각 기본 사이트의 사이트 서버  

- SMS 공급자의 모든 인스턴스  


> [!NOTE]  
> Configuration Manager 사이트를 설치하기 전에 각 사이트 서버에 수동으로 Windows ADK를 설치합니다.  

#### <a name="windows-adk-features"></a>Windows ADK 기능
Windows ADK의 다음 기능을 설치합니다.  

-   USMT(사용자 상태 마이그레이션 도구)  

    > [!Note]  
    > SMS 공급자에는 USMT가 필요하지 않습니다.

-   Windows 배포 도구  

-   Windows PE(Windows 사전 설치 환경)  

    > [!Important]  
    > Windows 10 버전 1809부터 Windows PE는 별도의 설치 프로그램입니다. 그러나 기능 차이는 없습니다.<!--SCCMDocs-pr issue 2908-->  

여러 버전의 Configuration Manager에서 사용할 수 있는 Windows 10 ADK 버전 목록은 [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)을 참조하세요.


### <a name="user-state-migration-tool-usmt"></a>USMT(사용자 상태 마이그레이션 도구)  

Configuration Manager에서는 USMT 10 원본 파일을 포함하는 USMT 패키지를 사용하여 사용자 상태를 OS 배포의 일부로 캡처하고 복원합니다. 최상위 사이트의 Configuration Manager 설치 프로그램에서 자동으로 USMT 패키지를 만듭니다. USMT 10은 Windows 7, Windows 8, Windows 8.1 및 Windows 10의 사용자 상태를 캡처합니다.  

자세한 내용은 다음 아티클을 참조하세요.  

- [USMT 10에 대한 일반 마이그레이션 시나리오](https://docs.microsoft.com/windows/deployment/usmt/usmt-common-migration-scenarios)  

- [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)  


### <a name="windows-pe"></a>Windows PE  

Windows PE는 부팅 이미지에서 컴퓨터를 시작하는 데 사용됩니다. Windows PE는 제한된 서비스를 갖는 Windows 버전으로서 Windows의 설치 전과 배포 시에 사용됩니다. 다음 목록에는 지원되는 버전의 Configuration Manager용 Windows ADK, 현재 분기가 포함됩니다.  

#### <a name="windows-adk-version"></a>Windows ADK 버전  
Windows 10용 Windows ADK 자세한 내용은 [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)을 참조하세요.

#### <a name="windows-pe-versions-for-boot-images-customizable-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 사용자 지정 가능한 부팅 이미지의 Windows PE 버전  
Windows PE 10  

#### <a name="supported-windows-pe-versions-for-boot-images-not-customizable-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 사용자 지정할 수 없지만 지원되는 부팅 이미지의 Windows PE 버전  
Windows PE 3.1<sup>1</sup> 및 Windows PE 5  

<sup>1</sup> 부팅 이미지가 Windows PE 3.1을 기반으로 하는 경우에만 Configuration Manager에 부팅 이미지를 추가할 수 있습니다. Windows 7 SP1용 Windows AIK 추가 기능을 설치하여 Windows 7 SP1용 Windows AIK 추가 기능(Windows PE 3.1에 기반)이 포함된 Windows 7용 Windows AIK(Windows PE 3에 기반)로 업그레이드하세요. [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=5188)에서 Windows 7 SP1용 Windows AIK 추가 기능을 다운로드합니다.  

예를 들어 Configuration Manager를 설치한 경우 Configuration Manager 콘솔에서 Windows 10용 Windows ADK(Windows PE 10 기반)의 부팅 이미지를 사용자 지정할 수 있습니다. 그러나 Windows PE 5를 기반으로 하는 부팅 이미지가 지원되지만 여러 컴퓨터의 부팅 이미지를 사용자 지정하고 Windows 8용 Windows ADK와 함께 설치된 DISM 버전을 사용해야 합니다. 그런 다음, 부팅 이미지를 Configuration Manager 콘솔에 추가합니다. 부팅 이미지를 사용자 지정하고(옵션 구성 요소 및 드라이버 추가), 부팅 이미지를 지원하는 명령을 사용하고, 부팅 이미지를 Configuration Manager 콘솔에 추가하고, 배포 지점을 부팅 이미지로 업데이트하는 단계에 대한 자세한 내용은 [부팅 이미지 사용자 지정](/sccm/osd/get-started/customize-boot-images)을 참조하세요. 부팅 이미지에 대한 자세한 내용은 [부팅 이미지 관리](/sccm/osd/get-started/manage-boot-images)를 참조하세요.  


### <a name="windows-server-update-services-wsus"></a>WSUS(Windows Server Update Services)  

WSUS는 소프트웨어 업데이트 지점에 필요합니다. 이 기능은 OS를 배포하는 동안 소프트웨어 업데이트를 설치하는 데 필요합니다. 자세한 내용은 [소프트웨어 업데이트 지점 설치 및 구성](/sccm/sum/get-started/install-a-software-update-point)을 참조하세요.


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>사이트 시스템 서버의 IIS(인터넷 정보 서비스)  

IIS는 배포 지점, 상태 마이그레이션 지점 및 관리 지점에 필요합니다. 자세한 내용은 [사이트 및 사이트 시스템 필수 조건](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)을 참조하세요.  


### <a name="windows-deployment-services-wds"></a>WDS(Windows 배포 서비스)  

1802 및 이전 버전에서는 PXE 배포에 WDS가 필요합니다. 1806 버전부터 WDS 없이 배포 지점에서 PXE를 사용할 수 있습니다. 자세한 내용은 이 아티클에서 [Windows 배포 서비스](#BKMK_WDS) 섹션을 참조하세요. 


### <a name="dynamic-host-configuration-protocol-dhcp"></a>DHCP(Dynamic Host Configuration Protocol)  

DHCP는 PXE 배포에 필요합니다. PXE를 사용하여 운영 체제를 배포하려면 활성 호스트를 포함하는 작동 중인 DHCP 서버가 있어야 합니다. PXE 배포에 대한 자세한 내용은 [PXE를 사용하여 네트워크를 통해 Windows 배포](/sccm/osd/deploy-use/use-pxe-to-deploy-windows-over-the-network)를 참조하세요.  


### <a name="supported-operating-systems-and-hard-disk-configurations"></a>지원되는 운영 체제 및 하드 디스크 구성  

운영 체제를 배포할 때 Configuration Manager에서 지원되는 OS 버전 및 하드 디스크 구성에 대한 자세한 내용은 [지원되는 운영 체제](#BKMK_SupportedOS) 및 [지원되는 디스크 구성](#BKMK_SupportedDiskConfig)을 참조하세요.  


### <a name="windows-device-drivers"></a>Windows 디바이스 드라이버  

대상 컴퓨터에 OS를 설치할 때 Windows 디바이스 드라이버를 사용할 수 있습니다. 부팅 이미지에서 Windows PE를 실행할 때도 사용됩니다. 자세한 내용은 [드라이버 관리](/sccm/osd/get-started/manage-drivers)를 참조하세요.  



##  <a name="BKMK_InternalDependencies"></a> Configuration Manager 종속성  

이 섹션에서는 Configuration Manager OS 배포 필수 구성 요소에 대한 정보를 제공합니다.  


### <a name="os-image"></a>OS 이미지  

Configuration Manager의 OS 이미지는 WIM(Windows Imaging) 파일 형식으로 저장됩니다. 참조 파일 및 폴더의 압축된 컬렉션을 나타냅니다. 컴퓨터에 OS를 성공적으로 설치하고 구성하기 위해 이러한 이미지가 필요합니다. 자세한 내용은 [OS 이미지 관리](/sccm/osd/get-started/manage-operating-system-images)를 참조하세요.  


### <a name="driver-catalog"></a>드라이버 카탈로그  

디바이스 드라이버를 배포하려면 디바이스 드라이버를 가져와서 사용하도록 설정한 다음, Configuration Manager 클라이언트가 액세스할 수 있는 배포 지점에서 활성화합니다. 드라이버 카탈로그에 대한 자세한 내용은 [드라이버 관리](/sccm/osd/get-started/manage-drivers)를 참조하세요.  


### <a name="management-point"></a>관리 지점  

관리 지점은 클라이언트와 Configuration Manager 사이트 간에 정보를 전송합니다. 클라이언트는 관리 지점을 사용하여 OS 배포를 완료하는 작업 시퀀스를 실행합니다. 작업 순서에 대한 자세한 내용은 [작업 자동화에 대한 계획 고려 사항](/sccm/osd/plan-design/planning-considerations-for-automating-tasks)을 참조하세요.  


### <a name="distribution-point"></a>배포 지점  

대부분의 배포에서는 OS를 배포하는 데 사용되는 데이터(예: 이미지 또는 드라이버 패키지)를 저장하기 위해 배포 지점을 사용합니다. 일반적으로 작업 순서는 배포 지점에서 데이터를 검색하여 OS를 배포합니다. 배포 지점을 설치하고 콘텐츠를 관리하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](/sccm/core/servers/deploy/configure/manage-content-and-content-infrastructure)를 참조하세요.  


### <a name="pxe-enabled-distribution-point"></a>PXE 사용 배포 지점  

PXE에서 시작한 배포를 배포하려면 배포 지점에서 클라이언트의 PXE 요청을 허용하도록 구성합니다. 자세한 내용은 [배포 지점 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)을 참조하세요.


### <a name="multicast-enabled-distribution-point"></a>멀티캐스트 사용 배포 지점  

멀티캐스트를 사용하여 OS 배포를 최적화하려면 배포 지점에서 멀티캐스트를 지원하도록 구성합니다. 자세한 내용은 [배포 지점 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-multicast)을 참조하세요.   


### <a name="state-migration-point"></a>상태 마이그레이션 지점  

사용자 상태 데이터를 동시에 캡처 및 복원하고 배포를 새로 고칠 경우 상태 마이그레이션 지점에서 다른 컴퓨터의 사용자 상태 데이터를 저장하도록 구성합니다.  

상태 마이그레이션 지점을 구성하는 방법에 대한 자세한 내용은 [상태 마이그레이션 지점](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments#BKMK_StateMigrationPoints)을 참조하세요.  

사용자 상태를 캡처 및 복원하는 방법에 대한 자세한 내용은 [사용자 상태 관리](/sccm/osd/get-started/manage-user-state)를 참조하세요.  


### <a name="reporting-services-point"></a>보고 서비스 지점  

OS 배포에 Configuration Manager 보고서를 사용하려면 보고 지점을 설치하고 구성합니다. 자세한 내용은 [보고](/sccm/core/servers/manage/reporting)를 참조하세요.  


### <a name="security-permissions-for-os-deployments"></a>OS 배포를 위한 보안 권한  

**운영 체제 배포 관리자** 보안 역할은 변경이 불가능한 기본 제공 역할입니다. 그러나 이 역할을 복사하여 변경한 다음 이러한 변경 내용을 새 사용자 지정 보안 역할로 저장할 수 있습니다. OS 배포에 직접 적용되는 일부 권한은 다음과 같습니다.  

- **부팅 이미지 패키지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

- **장치 드라이버**: 만들기, 삭제, 수정, 폴더 수정, 보고서 수정, 개체 이동, 읽기, 보고서 실행  

- **드라이버 패키지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

- **운영 체제 이미지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

- **운영 체제 업그레이드 패키지**: 만들기, 삭제, 수정, 폴더 수정, 개체 이동, 읽기, 보안 범위 설정  

- **작업 순서 패키지**: 만들기, 작업 순서 미디어 만들기, 삭제, 수정, 폴더 수정, 보고서 수정, 개체 이동, 읽기, 보고서 실행, 보안 범위 설정  

자세한 내용은 [사용자 지정 보안 역할 만들기](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_CreateSecRole)를 참조하세요.  


### <a name="security-scopes-for-os-deployments"></a>OS 배포의 보안 범위  

관리 사용자에게 OS 배포에서 사용되는 보안 개체(예: OS 및 부팅 이미지, 드라이버 패키지, 작업 순서 패키지 등)에 대한 액세스 권한을 제공하려면 보안 범위를 사용합니다. 자세한 내용은 [보안 범위](/sccm/core/understand/fundamentals-of-role-based-administration#bkmk_PlanScope)를 참조하세요.  



##  <a name="BKMK_WDS"></a> Windows 배포 서비스  

1802 이전 버전에서 WDS(Windows 배포 서비스)는 PXE 또는 멀티캐스트를 지원하기 위해 구성한 배포 지점과 동일한 서버에 설치해야 합니다. WDS는 서버 OS에 포함되어 있습니다. PXE 배포를 실행할 때 WDS는 PXE 부팅을 수행하는 서비스입니다. 배포 지점이 설치되고 이 배포 지점이 PXE를 사용하도록 설정되면 Configuration Manager에서는 WDS PXE 부팅 기능을 사용하는 공급자를 WDS에 설치합니다.  

1806 버전부터 WDS 없이 배포 지점에서 PXE를 사용할 수 있습니다. 자세한 내용은 [배포 지점 설치 및 구성](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe)에서 **Windows 배포 서비스 없이 PXE 응답기 사용** 옵션을 참조하세요.


> [!NOTE]  
>  서버를 다시 시작해야 할 경우 WDS 설치는 실패할 수도 있습니다. 


### <a name="wds-requirements"></a>WDS 요구 사항  

-   서버에 WDS를 설치하려면 관리자가 로컬 관리자 그룹의 멤버여야 합니다.  

-   WDS 서버는 Active Directory 도메인의 구성원이거나 Active Directory 도메인의 도메인 컨트롤러여야 합니다. 모든 Windows 도메인 및 포리스트 구성은 WDS를 지원합니다.  

-   원격 서버에 공급자가 설치되어 있는 경우 사이트 서버와 원격 공급자에 WDS를 설치합니다.  


###  <a name="BKMK_WDSandDHCP"></a> WDS 및 DHCP가 동일한 서버에 있을 때 고려할 사항  

배포 지점을 DHCP가 실행되는 서버에서 함께 호스트하려면 다음과 같은 구성상의 문제를 고려하세요.  

-   활성 영역을 포함하는 작동 중인 DHCP 서버가 있어야 합니다. WDS는 DHCP 서버가 필요한 PXE를 사용합니다.  

-   WDS를 실행하려면 DNS 서버가 필요합니다.  

-   WDS 서버에서 다음 UDP 포트가 열려 있어야 합니다.  

    -   포트 67(DHCP)  

    -   포트 69(TFTP)  

    -   포트 4011(PXE)  

    > [!NOTE]  
    >  서버에서 DHCP 권한 부여가 필요한 경우 해당 서버에 DHCP 클라이언트 포트 68이 열려 있어야 합니다.  

-   DHCP 및 WDS에는 모두 포트 번호 67이 필요합니다. WDS와 DHCP를 함께 호스트하는 경우 PXE용으로 구성된 배포 지점 또는 DHCP를 별도의 서버로 이동할 수 있습니다. 또는 다음 프로시저에 따라 WDS 서버가 다른 포트에서 수신하도록 구성할 수 있습니다.  

#### <a name="to-configure-the-wds-server-to-listen-on-a-different-port"></a>WDS 서버가 다른 포트에서 수신하도록 구성하려면  

1.  다음 레지스트리 키를 수정합니다.  

     `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE`  

2.  레지스트리 값 **UseDHCPPorts**를 **0**으로 설정합니다.  

3.  새 구성을 적용하려면 서버에서 다음 명령을 실행합니다.  

     `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  



##  <a name="BKMK_SupportedOS"></a> 지원되는 운영 체제  

[클라이언트 및 장치에서 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)에 지원되는 클라이언트로 나열된 모든 Windows 운영 체제는 OS 배포에 사용할 수 있습니다.  



##  <a name="BKMK_SupportedDiskConfig"></a> 지원되는 디스크 구성  

Configuration Manager OS 배포에 지원되는 참조 및 대상 컴퓨터의 하드 디스크 구성 조합은 다음 표와 같습니다.  

|참조 컴퓨터 하드 디스크 구성|대상 컴퓨터 하드 디스크 구성|  
|------------------------------------------------|--------------------------------------------------|  
|기본 디스크|기본 디스크|  
|동적 디스크의 단순 볼륨|동적 디스크의 단순 볼륨|  

Configuration Manager는 단순 볼륨으로 구성된 컴퓨터에서만 OS 이미지를 캡처하도록 지원합니다. 다음과 같은 하드 디스크 구성은 지원하지 않습니다.  

-   스팬 볼륨  

-   스트라이프 볼륨(RAID 0)  

-   미러 볼륨(RAID 1)  

-   패리티 볼륨(RAID 5)  

다음 표에서는 Configuration Manager OS 배포에서 지원되지 않는 참조 및 대상 컴퓨터의 추가 하드 디스크 구성을 보여줍니다.  

|참조 컴퓨터 하드 디스크 구성|대상 컴퓨터 하드 디스크 구성|  
|------------------------------------------------|--------------------------------------------------|  
|기본 디스크|동적 디스크|  



## <a name="next-steps"></a>다음 단계

- [OS 배포를 위한 사이트 시스템 역할 준비](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments)
- [OS 배포를 위한 준비](/sccm/osd/get-started/prepare-for-operating-system-deployment)
