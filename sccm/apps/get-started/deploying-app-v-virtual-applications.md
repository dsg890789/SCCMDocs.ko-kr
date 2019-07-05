---
title: App-V 가상 애플리케이션 배포
titleSuffix: Configuration Manager
description: 가상 애플리케이션을 만들고 배포할 때 고려해야 할 사항을 확인합니다.
ms.date: 03/12/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: ddcad9f2-a542-4079-83ca-007d7cb44995
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4598b89429ec3a9bd3bed31f57a6b681f88063cf
ms.sourcegitcommit: 4981a796e7886befb7bdeeb346dba32be82aefd6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67515815"
---
# <a name="deploy-app-v-virtual-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 App-V 가상 애플리케이션 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 사용하여 가상 애플리케이션을 관리할 때 다음과 같은 이점이 있습니다.  

-   단일 관리 인프라  

-   확장성, 배포 및 콘텐츠 배포 기능(예: 컬렉션 및 사용자 디바이스 선호도)  

-   고급 애플리케이션 관리 기능  

-   가상 애플리케이션 지원을 위한 운영 체제 배포, 소프트웨어 alc 하드웨어 인벤토리, 소프트웨어 계량 및 Asset Intelligence  

Microsoft App-V(Application Virtualization)를 사용하여 애플리케이션을 만들고 시퀀스하는 방법에 대한 자세한 내용은 TechNet 라이브러리에서 [애플리케이션 가상화](https://technet.microsoft.com/library/cc843848.aspx)를 참조하세요.  

가상 애플리케이션을 만들어 배포할 때는 애플리케이션을 만들기 위한 다른 System Center Configuration Manager 요구 사항 및 절차 외에 다음 사항을 고려해야 합니다.

-   컴퓨터에 가상 애플리케이션을 배포하려면 Configuration Manager 클라이언트와 App-V 클라이언트를 컴퓨터에 설치해야 합니다. 클라이언트 디바이스에는 데스크톱 및 휴대용 컴퓨터와 VDI(가상 데스크톱 인프라) 클라이언트가 포함될 수 있습니다. Configuration Manager와 App-V 클라이언트 소프트웨어가 함께 작동하여 가상 애플리케이션 패키지를 제공하고 찾아서 시작합니다. Configuration Manager 클라이언트는 App-V 클라이언트에 대한 가상 애플리케이션 패키지 제공을 관리합니다. App-V 클라이언트는 클라이언트에서 가상 애플리케이션을 실행합니다.  

-   가상 애플리케이션을 배포하려면 먼저 App-V Application Virtualization Sequencer를 사용하여 가상 애플리케이션을 만들어야 합니다. Application Virtualization Sequencer는 애플리케이션에 대한 설치 및 설정 프로세스를 모니터링하고 애플리케이션 실행을 위해 필요한 정보를 가상 환경에 기록합니다. 또한 Application Virtualization Sequencer를 사용하면 모든 사용자에게 적용되는 파일 및 구성과 사용자가 사용자 지정할 수 있는 구성을 설정할 수 있습니다.  

-   애플리케이션을 시퀀스할 때 Configuration Manager에서 액세스할 수 있는 위치에 패키지를 저장해야 합니다. 그런 다음 이 가상 애플리케이션이 포함된 애플리케이션 배포를 만들 수 있습니다.  

-   Configuration Manager는 App-V 4.6의 공유 읽기 전용 캐시 기능 사용을 지원하지 않습니다.  

-   Configuration Manager는 App-V 5의 공유 콘텐츠 저장소 기능을 지원합니다.  

-   가상 애플리케이션에 대한 배포 유형을 만들 경우 Configuration Manager는 애플리케이션 매니페스트 파일의 콘텐츠를 사용하여 배포 유형을 만듭니다. 매니페스트 파일은 가상 애플리케이션에 대한 정보를 포함하는 XML 파일입니다. 또한 Configuration Manager는 가상 애플리케이션에 대해 지원되는 운영 체제의 관련 정보가 포함된 App-V .osd 파일의 콘텐츠를 기반으로 배포 유형에 대한 요구 사항을 만듭니다.  

-   Configuration Manager에서 가상 애플리케이션을 배포하려면 클라이언트 컴퓨터에 적어도 App-V 4.6 SP1 이상 버전의 클라이언트가 설치되어 있어야 합니다.  

-   가상 애플리케이션을 배포하려면 먼저 기술 자료 문서 [2645225](https://support.microsoft.com/kb/2645225)에 설명된 핫픽스로 App-V 클라이언트를 업데이트해야 합니다.  

-   App-V 5.0의 연결 그룹을 사용하는 경우 배포된 가상 애플리케이션이 클라이언트 컴퓨터에서 같은 파일 시스템 및 레지스트리를 공유할 수 있습니다. 표준 가상 애플리케이션과 달리 이러한 애플리케이션은 서로 간에 데이터를 공유할 수 있습니다. 또한 연결 그룹은 포함하고 있는 애플리케이션의 사용자 설정을 보존합니다. Configuration Manager의 App-V 가상 환경은 클라이언트 컴퓨터에서 연결 그룹을 설정하는 데 사용됩니다. 가상 환경은 애플리케이션이 설치되거나 설치된 애플리케이션을 클라이언트가 다음에 평가할 때 클라이언트 컴퓨터에서 만들어지거나 변경됩니다. 이러한 애플리케이션의 우선 순위를 지정함으로써 여러 애플리케이션에서 파일 시스템 또는 레지스트리 값을 변경하려고 시도할 때 우선 순위가 가장 높은 애플리케이션이 우선권을 얻도록 할 수 있습니다. 자세한 내용은 [App-V 가상 환경 만들기](../../apps/deploy-use/create-app-v-virtual-environments.md)를 참조하세요.  

##  <a name="supported-app-v-versions"></a>지원되는 App-V 버전  
 Configuration Manager는 다음 버전의 App-V를 지원합니다.  

-   **App-V 4.6**: Configuration Manager에서 가상 애플리케이션을 사용하려면 클라이언트 컴퓨터에 App-V 4.6 SP1, App-V 4.6 SP2 또는 App-V 4.6 SP3 클라이언트가 설치되어 있어야 합니다.  

     또한 기술 자료 문서 [2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322)에 설명된 핫픽스를 사용하여 App-V 4.6 SP1 클라이언트를 업데이트해야 가상 애플리케이션을 배포할 수 있습니다.  

-   **App-V 5, App-V 5.0 SP1, App-V 5.0 SP2, App-V 5.0 SP3 및 App-V 5.1**: App-V 5.0 SP2의 경우 [핫픽스 패키지 5](https://support.microsoft.com/en-us/kb/2963211)를 설치하거나 App-V 5.0 SP3을 사용해야 합니다.  
-   **App-V 5.2**: 이는 Windows 10 Education(1607 이상), Windows 10 Enterprise(1607 이상), Windows Server 2016에 기본 제공됩니다.

Windows 10의 App-V에 대한 자세한 내용은 다음 항목을 참조하세요.

- [App-V의 새로운 기능](https://technet.microsoft.com/itpro/windows/manage/appv-about-appv)
- [Windows 10용 App-V 시작](https://technet.microsoft.com/itpro/windows/manage/appv-getting-started)
- [기존 설치에서 Windows 10용 App-V로 업그레이드](https://technet.microsoft.com/itpro/windows/manage/appv-upgrading-to-app-v-for-windows-10-from-an-existing-installation)

##  <a name="steps-to-manage-app-v-virtual-applications"></a>App-V 가상 애플리케이션을 관리하는 단계  
 App-V 가상 애플리케이션을 관리하려면 다음 단계를 수행합니다.  

1.   **시퀀싱**: 시퀀싱은 App-V Sequencer를 사용하여 애플리케이션을 가상 애플리케이션으로 변환하는 프로세스입니다.

2.   **만들기**: 배포 유형 만들기 마법사를 사용하여 시퀀싱된 애플리케이션을 Configuration Manager 배포 유형으로 가져온 다음 애플리케이션에 추가할 수 있습니다. 여러 가상 애플리케이션이 설정을 공유할 수 있는 가상 환경을 만들 수도 있습니다.

3.   **배포**: 배포는 App-V 애플리케이션을 Configuration Manager 배포 지점에서 사용할 수 있게 만드는 프로세스입니다.

4.   **배포**: 배포(Deployment)는 애플리케이션을 클라이언트 컴퓨터에서 사용할 수 있게 만드는 프로세스입니다. App-V 전체 인프라에서는 이 프로세스를 게시 및 스트리밍이라고 합니다.  

##  <a name="configuration-manager-virtual-application-delivery-methods"></a>Configuration Manager의 가상 애플리케이션 제공 방법  
Configuration Manager에서는 스트리밍 배달과 로컬 배달(다운로드 및 실행)의 두 가지 방법으로 클라이언트에 가상 애플리케이션을 제공할 수 있습니다.

사용할 배달 방법을 결정할 때는 로컬 배달을 사용하여 App-V 애플리케이션의 가용성을 보장하는 장점과 스트리밍 배달을 통해 필요한 디스크 공간을 줄이는 장점을 비교합니다. 사용자가 어느 위치에서든 항상 애플리케이션을 사용할 수 있도록 로컬 배달에 필요한 클라이언트 디스크 공간을 늘리는 것이 스트리밍 배달에 유용할 수 있습니다.  

###  <a name="streaming-delivery"></a>스트리밍 배달
Configuration Manager를 사용하여 App-V 클라이언트를 관리하면 배포 지점에서 HTTP 또는 HTTPS를 통해 가상 애플리케이션을 스트리밍할 수 있습니다. HTTP 또는 HTTPS를 통한 스트리밍은 기본적으로 사용하도록 설정되어 있으며 배포 지점 속성 대화 상자에서 설정됩니다. 클라이언트 컴퓨터에 가상 애플리케이션을 배포하고 사용자가 이 가상 애플리케이션을 실행하는 경우 Configuration Manager 클라이언트는 관리 지점에 연결하여 사용할 배포 지점을 결정합니다. 그런 다음 배포 지점에서 애플리케이션이 스트리밍됩니다.  

다음 표에서는 스트리밍 배달이 가장 적합한 배달 방법인지를 결정하는 데 도움이 되는 정보를 제공합니다.

|장점|단점|  
|----------------|-------------------|  
|이 방법은 표준 네트워크 프로토콜을 사용하여 배포 지점에서 패키지 콘텐츠를 스트리밍합니다.<br /><br /> 가상 애플리케이션에 대한 프로그램 바로 가기는 배포 지점에 대한 연결을 호출하여 가상 애플리케이션 배달이 주문형으로 이루어지도록 합니다.<br /><br /> 이 방법은 배포 지점에 대한 고속 연결을 사용하는 클라이언트에 대해 효과적으로 작동합니다.<br /><br /> 기업 전체에 배포되는 업데이트된 가상 애플리케이션은 클라이언트에서 현재 버전이 대체됨을 알리는 정책을 받고 이전 버전으로부터의 변경 사항만 다운로드할 때 사용할 수 있습니다.<br /><br /> 액세스 권한은 사용자가 무단 애플리케이션 또는 패키지에 액세스하지 못하도록 배포 지점에서 정의됩니다.|가상 애플리케이션은 사용자가 처음으로 애플리케이션을 실행할 때까지 스트리밍되지 않습니다. 이 시나리오에서는 사용자가 가상 애플리케이션에 대한 프로그램 바로 가기를 받을 수 있지만, 처음으로 가상 애플리케이션을 실행하기 전에 네트워크에서 연결이 끊길 수 있습니다. 클라이언트가 오프라인 상태인 동안 가상 애플리케이션을 실행하려고 하면 애플리케이션을 스트리밍하기 위한 Configuration Manager 배포 지점을 사용할 수 없기 때문에 오류가 표시되고 사용자가 가상화된 애플리케이션을 실행할 수 없게 됩니다. 사용자가 네트워크에 다시 연결하여 애플리케이션을 실행할 때까지 애플리케이션을 사용할 수 없습니다.<br /><br /> 이를 방지하려면 클라이언트에 가상 애플리케이션을 배달하는 데 로컬 배달 방법을 사용하거나, 스트리밍 배달에 인터넷 기반 클라이언트 관리를 사용하도록 설정할 수 있습니다.|  

###  <a name="local-delivery-download-and-execute"></a>로컬 배달(다운로드 및 실행)  
Configuration Manager를 사용할 때는 다운로드하고 실행하는 것이 가장 일방적인 방법입니다. Configuration Manager를 사용하여 다른 애플리케이션 형식이 배달되는 방법을 밀접하게 모방하기 때문입니다. 로컬 배달 방법을 사용하는 경우 Configuration Manager 클라이언트는 먼저 전체 가상 애플리케이션 패키지를 Configuration Manager 클라이언트 캐시에 다운로드합니다. 그런 다음 Configuration Manager는 App-V 클라이언트에게 Configuration Manager 캐시의 애플리케이션을 App-V 캐시로 스트리밍하도록 지시합니다. 클라이언트 컴퓨터에 가상 애플리케이션을 배포하고 해당 콘텐츠가 App-V 캐시에 없는 경우 App-V 클라이언트는 Configuration Manager 클라이언트 캐시에서 App-V 캐시로 애플리케이션 콘텐츠를 스트리밍한 다음 애플리케이션을 실행합니다. 애플리케이션이 정상 실행되고 나면 Configuration Manager 클라이언트가 오래된 버전의 패키지를 삭제하거나 다음 삭제 주기에 Configuration Manager 클라이언트 캐시에 유지하도록 설정할 수 있습니다. 로컬에 콘텐츠를 유지할 때는 BranchCache 및 PeerCache와 같은 패키지 콘텐츠 배달 최적화 방법을 활용할 수 있습니다.

다음 표에서는 로컬 배달이 가장 적합한 배달 방법인지를 결정하는 데 도움이 되는 정보를 제공합니다.   

|장점|단점|  
|----------------|-------------------|  
|표준 배포 지점 기능은 BITS(Background Intelligent Transfer Service)를 사용하여 패키지를 다운로드하는 데 사용됩니다.<br /><br /> 가상 애플리케이션 패키지 콘텐츠가 클라이언트에 로컬로 배달됩니다. 즉, 사용자는 컴퓨터가 네트워크에 연결되어 있지 않아도 콘텐츠를 실행할 수 있습니다.<br /><br /> 이 방법은 네트워크 연결이 느리거나 불안정한 경우 및 컴퓨터가 네트워크에 가끔씩만 연결되는 경우에 적합합니다.<br /><br /> Configuration Manager는 RDC(원격 차등 압축)를 사용해서 가상 애플리케이션 패키지 콘텐츠가 업데이트될 때 변경된 파일 내 바이트만 클라이언트에 전송합니다. Configuration Manager 클라이언트에서는 RDC를 사용하여 현재 버전의 패키지와 클라이언트에 전송된 변경 사항을 기반으로 새 버전의 가상 애플리케이션 패키지를 만듭니다.<br /><br /> 이 방법을 통해 모바일 사용자와 연결이 끊긴 사용자의 애플리케이션이 복원될 수 있습니다. 관리자는 설치 작업을 통해 가상 애플리케이션이 배포된 경우 배달 후에 패키지를 Configuration Manager 캐시에 유지하도록 선택할 수 있습니다. Configuration Manager 클라이언트 캐시의 패키지는 App-V 클라이언트가 캐시로 패키지를 가져오기 위한 안정적인 로컬 스트리밍 원본으로 사용됩니다.|Configuration Manager 캐시에 가상 애플리케이션을 유지하는 경우 클라이언트에 가상 애플리케이션 패키지 크기의 최대 두 배에 해당하는 디스크 공간이 필요합니다.|  

###  <a name="deployment-from-an-image"></a>이미지에서 배포

또한 가상 애플리케이션을 컴퓨터에 미리 설치한 다음 해당 컴퓨터의 이미지를 만들어 다른 컴퓨터에 배포할 수도 있습니다. 그러나 다른 사이트에서 가상 애플리케이션 패키지가 만들어진 경우 애플리케이션에 업데이트를 다운로드하는 데 이진 델타 복제가 사용되지 않습니다. 이 옵션은 가상 데스크톱 인프라에서 사용자가 로그온한 후 애플리케이션을 다운로드하는 대신 애플리케이션을 즉시 사용할 수 있도록 하려는 경우에 유용할 수 있습니다.    

##  <a name="migrating-from-an-app-v-infrastructure-to-a-configuration-manager-and-app-v-infrastructure"></a>App-V 인프라에서 Configuration Manager 및 App-V 인프라로 마이그레이션  
다음 표에서는 Configuration Manager를 사용하여 기존 App-V 인프라에서 가상 애플리케이션 관리로의 마이그레이션을 계획하는 데 도움이 되는 정보를 제공합니다.  

|단계|추가 정보|  
|----------|----------------------|  
|현재 가상 애플리케이션을 검토하여 Configuration Manager 인프라로 마이그레이션할 애플리케이션을 선택합니다.|추가 정보가 없습니다.|  
|가상 응용 프로그램을 배포할 사용자와 디바이스를 평가합니다.|가상 응용 프로그램을 배포할 사용자와 디바이스를 함께 그룹화하는 Configuration Manager 컬렉션을 만듭니다. [컬렉션 소개](/sccm/core/clients/manage/collections/introduction-to-collections)를 참조하세요.|  
|App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 마이그레이션합니다.|이 항목의 [App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 마이그레이션](/sccm/apps/get-started/deploying-app-v-virtual-applications#migrating-app-v-5-connection-groups-to-configuration-manager-virtual-environments) 섹션을 참조하세요.|  
|가상 애플리케이션이 Configuration Manager 인프라에 전체 애플리케이션으로 존재하는지 확인합니다.|관리를 간소화하기 위해 가상 애플리케이션을 새 배포 유형으로 기존 전체 애플리케이션에 추가할 수 있습니다. [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.|  
|기존 APP-V 패키지를 대체하는 애플리케이션을 만듭니다.|[애플리케이션 관리 소개](/sccm/apps/understand/introduction-to-application-management) 및 [애플리케이션 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.|  
|가상 애플리케이션이 처음 배포된 후에 클라이언트에서 Configuration Manager를 통해 가상 애플리케이션 관리를 시작합니다. 그리고 나면 Configuration Manager가 컴퓨터의 모든 App-V 애플리케이션을 관리해야 합니다.|추가 정보가 없습니다.|  
|애플리케이션의 로컬 배달을 사용하도록 콘텐츠를 적절한 배포 지점에 배포합니다.|[콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|Configuration Manager 클라이언트에 애플리케이션을 배포합니다.<br /><br /> 매니페스트 XML 파일을 만들지 않는 이전 버전의 시퀀서로 App-V 애플리케이션이 만들어진 경우 최신 버전의 시퀀서로 이 애플리케이션을 열고 저장하여 매니페스트 XML 파일을 만들 수 있습니다. 이 파일은 Configuration Manager를 사용하여 가상 애플리케이션을 배포하는 데 필요합니다.<br /><br /> App-V는 SoftGrid 4.1 SP1 또는 4.2 버전의 시퀀서로 만들어진 가상 애플리케이션 패키지를 지원합니다.<br /><br /> 애플리케이션이 이전에 로컬로 설치된 경우 이를 제거한 후에 애플리케이션의 가상 버전을 배포해야 합니다.|[애플리케이션 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.|  
|System Center Configuration Manager에서는 더 이상 가상 애플리케이션이 포함된 패키지와 프로그램을 사용할 수 없습니다. Configuration Manager 2007에서 System Center Configuration Manager로 마이그레이션할 때 Configuration Manager가 이러한 패키지를 애플리케이션으로 변환합니다.<br /><br /> Configuration Manager 2007 보급 알림은 다음 배포 유형으로 변환됩니다.<br /><br /> - 보급 알림이 없는 App-V 패키지 마이그레이션: 기본 배포 유형 설정을 사용하는 한 가지 배포 유형입니다.<br /><br /> - 보급 알림이 하나 포함된 App-V 패키지 마이그레이션: Configuration Manager 2007 보급 알림과 동일한 설정을 사용하는 <br />                한 가지 배포 유형입니다.<br /><br /> - 보급 알림이 여러 개 포함된 App-V 패키지 마이그레이션: 각각에 대한 배포 유형 <br />                Configuration Manager 2007 보급 알림은 해당 보급 알림에 대한 설정을 사용합니다.|[Configuration Manager 개체를 System Center Configuration Manager로 마이그레이션하도록 계획](../../core/migration/planning-for-the-migration-of-objects.md)을 참조하세요.|  

##  <a name="migrating-app-v-5-connection-groups-to-configuration-manager-virtual-environments"></a>App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 마이그레이션  
Configuration Manager의 App-V 가상 환경에서는 배포된 가상 애플리케이션이 클라이언트 컴퓨터에 있는 동일한 파일 시스템과 레지스트리를 공유할 수 있습니다. 즉, 일반 가상 애플리케이션과 달리 이러한 애플리케이션은 서로 데이터를 공유할 수 있습니다. 가상 환경은 애플리케이션이 설치되거나 설치된 애플리케이션을 클라이언트가 다음에 평가할 때 클라이언트 컴퓨터에서 만들어지거나 변경됩니다. 가상 환경은 독립 실행형 App-V 5의 연결 그룹과 유사합니다.  

연결 그룹을 독립 실행형 App-V 5에서 Configuration Manager 가상 환경으로 마이그레이션하는 경우 클라이언트 컴퓨터에 이미 있는 연결 그룹을 Configuration Manager에서 올바르게 관리하며 이러한 연결 그룹 내 사용자 환경이 유지되는지 확인해야 합니다.  

App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 변환하려면  

1.  App-V에 있던 모든 애플리케이션에 대한 Configuration Manager 애플리케이션을 만듭니다.  

2.  배포 목적이 **필수**인 사용자 또는 디바이스에 응용 프로그램을 배포합니다. 사용자에게 배포할 애플리케이션은 App-V에서 애플리케이션을 사용했던 사용자에게 배포해야 합니다. 컴퓨터에 배포할 애플리케이션은 App-V에서 해당 애플리케이션이 포함되어 있었던 컴퓨터에 배포해야 합니다.  

3.  배포가 완료되면 독립 실행형 App-V에 게시된 연결 그룹과 일치하는 가상 환경을 만듭니다. 가상 환경에는 동일한 패키지(구체적으로는 App-V 5 배포 유형)가 같은 순서로 포함되어야 합니다.  

App-V 가상 환경을 만드는 방법에 대한 자세한 내용은 [APP-V 가상 환경을 만드는 방법](../../apps/deploy-use/create-app-v-virtual-environments.md)을 참조하세요.  

또는 Configuration Manager로 애플리케이션 배포를 시작하기 전에 App-V 클라이언트에서 모든 연결 그룹을 삭제할 수 있습니다. 하지만 사용자가 App-V 연결 그룹에 저장했을 수 있는 설정이 손실됩니다.  

##  <a name="dynamic-suite-composition-in-app-v-46"></a>APP-V 4.6의 Dynamic Suite Composition  
Dynamic Suite Composition은 다른 가상 애플리케이션 패키지에 대한 종속성이 있는 단일 가상 애플리케이션 패키지를 정의할 수 있는 기능입니다. 애플리케이션이 실행될 때 App-V 클라이언트는 동일한 가상 환경에서 애플리케이션의 기본 패키지와 종속 패키지를 호스트합니다.  

Configuration Manager와 함께 이 기능을 사용하려면 두 패키지 모두 App-V 클라이언트에 배포 및 등록되어야 합니다. 종속 패키지 콘텐츠가 클라이언트 컴퓨터에서 로컬로 호스트되는지 확인하려면 애플리케이션 배포를 로컬 배달(다운로드 및 실행)로 설정합니다.  

App-V Dynamic Suite Composition에 대한 자세한 내용은 관련 App-V 설명서를 참조하세요.  

##  <a name="converting-app-v-46-applications-to-app-v-5-applications"></a>App-V 4.6 애플리케이션을 App-V 5 애플리케이션으로 변환  
App-V 4.6과 App-V 5 간에는 애플리케이션 패키지 형식이 변경되었습니다. App-V 4.6을 사용하여 시퀀스된 애플리케이션은 더 이상 지원되지 않습니다. 하지만 App-V 5의 패키지 변환기 도구를 사용하여 애플리케이션을 변환할 수 있습니다. 자세한 내용은 [APP-V 5 설명서](https://technet.microsoft.com/library/jj713472.aspx)를 참조하세요.  

App-V 4.6 애플리케이션을 App-V 5 애플리케이션으로 변환하려면 다음 단계를 따르세요.  

1.  App-V 4.6 패키지를 App-V 5 형식으로 변환하거나 시퀀싱 작업을 다시 수행합니다.  

2.  App-V 5 클라이언트를 계층에 있는 컴퓨터에 배포합니다.  

3.  App-V 5 애플리케이션용 배포 유형이 포함된 새 애플리케이션을 만들고 App-V 4.6 애플리케이션을 교체하는 교체 규칙을 만듭니다.  

4.  필요한 경우 가상 환경을 만듭니다.  

5.  새 5 APP-V 애플리케이션을 컴퓨터에 배포합니다.  

##  <a name="user-and-deployment-configuration-files"></a>사용자 및 배포 구성 파일  
사용자 및 배포 구성 파일에는 애플리케이션의 동작 방식을 제어하는 설정이 포함되어 있습니다. 이러한 파일을 사용하면 애플리케이션을 다시 시퀀싱하지 않고 애플리케이션 설정을 변경할 수 있습니다.  

일반적인 App-V 5 애플리케이션에는 다음 파일이 포함되어 있을 수 있습니다.  

-   애플리케이션 패키지(.appv) 파일  

-   사용자 구성 파일  

-   배포 구성 파일  

사용자 구성 파일에는 로그온한 사용자에게만 적용되는 설정이 포함됩니다. 예를 들어 구성 파일을 편집하여 사용자에게 배포되는 애플리케이션의 바로 가기에 대한 정보를 변경할 수 있습니다. 또한 배포 유형이 여러 개인 Configuration Manager 애플리케이션을 만들 수도 있습니다. 각 배포 유형은 다른 사용자 구성 파일을 포함할 수 있으며 요구 사항 규칙을 사용하여 관련 사용자에 대한 응용 프로그램을 설치할 수 있습니다.  

배포 구성 파일에는 레지스트리 설정과 같이 컴퓨터에 적용되는 설정이 포함됩니다. 또한 모든 사용자에게 적용되는 사용자 설정도 포함될 수 있습니다.  

Configuration Manager로 App-V 5 가상 애플리케이션을 배포하려는 경우 모든 세 파일이 App-V 5 배포 유형을 만들 때 사용한 폴더와 동일한 폴더에 있어야 합니다. 폴더에 여러 파일이 있는 경우 Configuration Manager는 최신 파일을 사용합니다.  

자세한 내용은 [APP-V 5 설명서](https://technet.microsoft.com/library/jj713466.aspx)를 참조하세요.  

##  <a name="app-v-local-interaction"></a>App-V 로컬 상호 작용  
일부 애플리케이션 배포의 경우 클라이언트 컴퓨터에 로컬로 설치되는 애플리케이션도 있고, 동일한 클라이언트 컴퓨터에 가상 애플리케이션으로 배포되는 애플리케이션도 있습니다. 기본적으로, 로컬로 설치된 애플리케이션은 가상화된 애플리케이션과 직접 통신하거나 서로 인식할 수 없습니다. 이러한 현상은 App-V에서 제공되는 애플리케이션 격리의 정상적인 동작입니다. 로컬 상호 작용은 App-V 클라이언트의 기능으로, 클라이언트 컴퓨터에서 실행되는 로컬에 설치된 애플리케이션이 가상화된 애플리케이션을 확인하고 가상화된 애플리케이션과 통신할 수 있도록 각 애플리케이션에 대해 이 기능을 사용하도록 설정할 수 있습니다. Configuration Manager 및 App-V는 로컬 상호 작용을 완전히 지원합니다.  

App-V 로컬 상호 작용 기능에 대한 자세한 내용은 관련 App-V 설명서를 참조하세요.  

##  <a name="app-v-5-shared-content-store"></a>App-V 5 공유 콘텐츠 저장소  
Configuration Manager는 App-V 5 공유 콘텐츠 저장소 기능을 지원합니다. 자세한 내용은 [App-V 5.0 SCS(공유 콘텐츠 저장소) 계획](https://technet.microsoft.com/library/jj713431.aspx)항목을 참조하세요.  

##  <a name="monitoring-virtual-applications"></a>가상 애플리케이션 모니터링  

### <a name="virtual-application-reports"></a>가상 애플리케이션 보고서  
다음 보고서를 사용하여 Configuration Manager 환경에서 App-V를 모니터링할 수 있습니다.  

|보고서 이름|설명|  
|-----------------|-----------------|  
|APP-V 가상 환경 결과|선택한 가상 환경에서 지정된 상태로 설정되어 있는 선택된 가상 환경 관련 정보를 표시합니다(App-V 5에만 해당).|  
|자산에 대한 App-V 가상 환경 결과|지정된 자산용으로 선택한 가상 환경 관련 정보와, 선택한 가상 환경의 배포 유형을 표시합니다(App-V 5에만 해당).|  
|App-V 가상 환경 상태|선택한 컬렉션용으로 선택된 가상 환경의 호환성 정보를 표시합니다. 이 보고서의 **보존** 열에는 이전에 설정된 가상 환경의 자산 중 더 이상 적용할 수 없지만 가상 환경에서 실행하는 애플리케이션의 사용자 설정을 유지할 목적으로 보존되는 자산이 표시됩니다(App-V 5에만 해당).|  
|특정 가상 애플리케이션을 포함하는 컴퓨터|Application Virtualization Management Sequencer에서 작성한 지정된 App-V 바로 가기가 있는 컴퓨터의 요약 정보를 표시합니다(App-V 4.6에만 해당).|  
|특정 가상 애플리케이션 패키지를 포함하는 컴퓨터|지정한 App-V 애플리케이션 패키지가 설치된 컴퓨터 목록을 표시합니다(App-V 4.6에만 해당).|  
|모든 가상 애플리케이션 패키지 인스턴스 수|검색된 모든 App-V 애플리케이션 패키지 수를 표시합니다(App-V 4.6에만 해당).|  
|모든 가상 애플리케이션 인스턴스 수|검색된 모든 App-V 애플리케이션 수를 표시합니다(App-V 4.6에만 해당).|  

### <a name="log-files"></a>로그 파일  
Configuration Manager는 가상 애플리케이션 배포에 대한 정보를 로그 파일에 기록합니다. 가상 애플리케이션 및 Configuration Manager 애플리케이션 관리에서 사용하는 로그 파일에 대한 자세한 내용은 [System Center Configuration Manager의 로그 파일](../../core/plan-design/hierarchy/log-files.md)을 참조하세요.  

Windows Vista, Windows 7 및 Windows 8의 경우 App-V 클라이언트의 로그는 C:\ProgramData\Microsoft\Application Virtualization Client에 있습니다.  
