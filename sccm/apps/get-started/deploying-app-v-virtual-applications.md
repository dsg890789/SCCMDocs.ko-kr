---
title: "App-V 가상 응용 프로그램 배포 | System Center Configuration Manager"
description: "가상 응용 프로그램을 만들고 배포할 때 고려해야 할 사항을 확인합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddcad9f2-a542-4079-83ca-007d7cb44995
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: d6e787d5968b281afe4e4b475287944563c8a77f


---
# <a name="deploy-app-v-virtual-applications-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 App-V 가상 응용 프로그램 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

응용 프로그램을 만들기 위한 다른 System Center Configuration Manager 요구 사항 및 절차 외에도 가상 응용 프로그램을 만들어 배포할 때는 다음 사항을 고려해야 합니다.  

 Configuration Manager를 사용하여 가상 응용 프로그램을 관리할 때 다음과 같은 이점이 있습니다.  

-   단일 관리 인프라 사용  

-   확장성, 배포 및 콘텐츠 배포 기능(예: 컬렉션 및 사용자 장치 선호도)  

-   Configuration Manager에서 제공하는 고급 응용 프로그램 관리 기능 활용  

-   운영 체제 배포, 소프트웨어 및 하드웨어 인벤토리, 소프트웨어 계량, Asset Intelligence 등 가상 응용 프로그램을 지원하는 Configuration Manager 기능 사용  

App-V를 사용하여 응용 프로그램을 만들고 시퀀스하는 방법에 대한 자세한 내용은 TechNet 라이브러리에서 [Application Virtualization(응용 프로그램 가상화)](https://technet.microsoft.com/library/cc843848.aspx) 를 참조하세요.  

컴퓨터에 가상 응용 프로그램을 배포하려면 Configuration Manager 클라이언트와 App-V 클라이언트를 컴퓨터에 설치해야 합니다. 클라이언트 장치에는 데스크톱 및 휴대용 컴퓨터와 VDI(가상 데스크톱 인프라) 클라이언트가 포함될 수 있습니다. Configuration Manager와 App-V 클라이언트 소프트웨어가 함께 작동하여 가상 응용 프로그램 패키지를 제공하고 찾아서 시작합니다. Configuration Manager 클라이언트는 App-V 클라이언트에 대한 가상 응용 프로그램 패키지 제공을 관리합니다. App-V 클라이언트는 클라이언트에서 가상 응용 프로그램을 실행합니다.  

-   가상 응용 프로그램을 배포하려면 먼저 App-V Application Virtualization Sequencer를 사용하여 가상 응용 프로그램을 만들어야 합니다. Application Virtualization Sequencer는 응용 프로그램에 대한 설치 및 설정 프로세스를 모니터링하고 응용 프로그램 실행을 위해 필요한 정보를 가상 환경에 기록합니다. 또한 Application Virtualization Sequencer를 사용하면 모든 사용자에게 적용되는 파일 및 구성과 사용자가 사용자 지정할 수 있는 구성을 구성할 수 있습니다.  

-   응용 프로그램을 시퀀스할 때 Configuration Manager에서 액세스할 수 있는 위치에 패키지를 저장해야 합니다. 그런 다음 이 가상 응용 프로그램이 포함된 응용 프로그램 배포를 만들 수 있습니다.  

-   Configuration Manager는 App-V 공유 읽기 전용 캐시 기능의 사용을 지원하지 않습니다.  

-   Configuration Manager는 App-V 5의 공유 콘텐츠 저장소 기능을 지원합니다.  

-   가상 응용 프로그램에 대한 배포 유형을 만들 경우 Configuration Manager는 응용 프로그램 매니페스트 파일의 콘텐츠를 사용하여 배포 유형을 만듭니다. 이는 가상 응용 프로그램에 대한 정보를 포함하는 XML 파일입니다. 또한 Configuration Manager는 가상 응용 프로그램에 대해 지원되는 운영 체제의 관련 정보가 포함된 App-V .osd 파일의 콘텐츠를 기반으로 배포 유형에 대한 요구 사항을 만듭니다.  

-   Configuration Manager에서 가상 응용 프로그램을 배포하려면 클라이언트 컴퓨터에 적어도 App-V 4.6 SP1 이상 버전의 클라이언트가 설치되어 있어야 합니다.  

-   또한 가상 응용 프로그램을 배포하려면 먼저 기술 자료 문서 [2645225](https://support.microsoft.com/kb/2645225)에 설명된 핫픽스로 App-V 클라이언트를 업데이트해야 합니다.  
  
-   Microsoft Application Virtualization 5.0의 연결 그룹을 사용하면 배포된 가상 응용 프로그램은 클라이언트 컴퓨터에서 서로 같은 파일 시스템 및 레지스트리를 공유할 수 있습니다. 표준 가상 응용 프로그램과 달리 이러한 응용 프로그램은 서로 간에 데이터를 공유할 수 있습니다. 또한 연결 그룹은 포함하고 있는 응용 프로그램의 사용자 설정을 보존합니다. Configuration Manager의 App-V 가상 환경은 클라이언트 컴퓨터에서 연결 그룹을 구성하는 데 사용됩니다. 가상 환경은 응용 프로그램이 설치되거나 설치된 응용 프로그램을 클라이언트가 다음에 평가할 때 클라이언트 컴퓨터에서 만들어지거나 변경됩니다. 이러한 응용 프로그램의 우선 순위를 지정함으로써 여러 응용 프로그램에서 파일 시스템 또는 레지스트리 값을 변경하려고 시도할 때 우선 순위가 가장 높은 응용 프로그램이 우선권을 얻도록 할 수 있습니다. 자세한 내용은 [App-V 가상 환경 만들기](../../apps/deploy-use/create-app-v-virtual-environments.md)를 참조하세요.  

##  <a name="supported-app-v-versions"></a>지원되는 App-V 버전  
 Configuration Manager는 다음 버전의 App-V를 지원합니다.  

-   **App-V 4.6:** Configuration Manager에서 가상 응용 프로그램을 사용하려면 클라이언트 컴퓨터에 App-V 4.6 SP1, App-V 4.6 SP2 또는 App-V 4.6 SP3 클라이언트가 설치되어 있어야 합니다.  

     또한 기술 자료 문서 [2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322) 에 설명된 핫픽스를 사용하여 App-V 4.6 SP1 클라이언트를 업데이트해야 가상 응용 프로그램을 성공적으로 배포할 수 있습니다.  

-   **App-V 5, App-V 5.0 SP1, App-V 5.0 SP2, App-V 5.0 SP3 및 App-V 5.1:** App-V 5.0 SP2의 경우 [핫픽스 패키지 5](https://support.microsoft.com/en-us/kb/2963211) 를 설치하거나 App-V 5.0 SP3를 사용해야 합니다.  

##  <a name="steps-to-manage-app-v-virtual-applications"></a>App-V 가상 응용 프로그램을 관리하는 단계  
 App-V 가상 응용 프로그램을 관리하려면 다음 단계를 완료하세요.  

-   **시퀀싱** - 시퀀싱은 App-V 시퀀서를 사용하여 응용 프로그램을 가상 응용 프로그램으로 변환하는 프로세스입니다.  

-   **Configuration Manager 응용 프로그램 만들기** – 배포 유형 만들기 마법사를 사용하여 응용 프로그램에 추가할 수 있는 Configuration Manager 배포 유형으로 시퀀스된 응용 프로그램을 가져옵니다. 여러 가상 응용 프로그램이 설정을 공유할 수 있는 가상 환경을 만들 수도 있습니다.  

-   **배포** – 배포는 App-V 응용 프로그램을 Configuration Manager 배포 지점에서 사용할 수 있게 만드는 프로세스입니다.  

-   **배포** – 배포(Deployment)는 응용 프로그램을 클라이언트 컴퓨터에서 사용할 수 있게 만드는 프로세스입니다. 이러한 프로세스를 App-V 전체 인프라의 스트리밍이라고 합니다. Configuration Manager에서는 가상 응용 프로그램 배포를 위한 두 가지 옵션, 즉 **스트리밍**과 **다운로드 및 실행**을 제공합니다.  

##  <a name="configuration-manager-virtual-application-delivery-methods"></a>Configuration Manager의 가상 응용 프로그램 제공 방법  
 Configuration Manager에서는 클라이언트에 가상 응용 프로그램을 제공하는 방법이 두 가지 있습니다. 이 두 방법은 스트리밍 배달과 로컬 배달(다운로드 및 실행)입니다.  

-   **스트리밍 배달**  

     Configuration Manager를 사용하여 App-V 클라이언트를 관리하면 배포 지점에서 HTTP 또는 HTTPS를 통해 가상 응용 프로그램을 스트리밍할 수 있습니다. HTTP 또는 HTTPS를 통한 스트리밍은 기본적으로 사용하도록 설정되어 있으며 배포 지점 속성 대화 상자에서 구성됩니다. 클라이언트 컴퓨터에 가상 응용 프로그램을 배포하고 사용자가 이 가상 응용 프로그램을 실행하는 경우 Configuration Manager 클라이언트는 관리 지점에 연결하여 사용할 배포 지점을 결정합니다. 그런 다음 배포 지점에서 응용 프로그램이 스트리밍됩니다.  

-   **로컬 배달(다운로드 및 실행)**  

     이 배달 방법을 사용하면 Configuration Manager 클라이언트는 먼저 전체 가상 응용 프로그램 패키지를 Configuration Manager 클라이언트 캐시에 다운로드한 다음 App-V 클라이언트가 Configuration Manager 캐시에서 App-V 캐시로 응용 프로그램을 스트리밍하도록 지시합니다. 클라이언트 컴퓨터에 가상 응용 프로그램을 배포하고 해당 콘텐츠가 App-V 캐시에 없는 경우 App-V 클라이언트는 Configuration Manager 클라이언트 캐시에서 App-V 캐시로 응용 프로그램 콘텐츠를 스트리밍한 다음 응용 프로그램을 실행합니다. 응용 프로그램이 성공적으로 실행된 후에는 Configuration Manager 클라이언트가 다음 삭제 주기에 오래된 버전의 패키지를 삭제하거나 Configuration Manager 클라이언트 캐시에 유지하도록 구성할 수 있습니다.  

 사용할 Configuration Manager 가상 응용 프로그램 배달 방법을 결정할 때에는 로컬 배달을 사용하여 App-V 응용 프로그램의 가용성을 보장하는 장점과 스트리밍 배달을 통해 필요한 디스크 공간을 줄이는 장점 간에 서로 비교합니다. 사용자가 어느 위치에서든 항상 응용 프로그램을 사용할 수 있도록 로컬 배달에 필요한 클라이언트 디스크 공간을 늘리는 것이 스트리밍 배달에 유용할 수 있습니다.  

 다음 표에서는 가장 적합한 배달 방법을 선택하는 데 도움이 되는 정보를 제공합니다.  

 **스트리밍 배달**  

|장점|단점|  
|----------------|-------------------|  
|이 방법은 표준 네트워크 프로토콜을 사용하여 배포 지점에서 패키지 콘텐츠를 스트리밍합니다.<br /><br /> 가상 응용 프로그램에 대한 프로그램 바로 가기는 배포 지점에 대한 연결을 호출하여 가상 응용 프로그램 배달이 주문형으로 이루어지도록 합니다.<br /><br /> 이 방법은 배포 지점에 대한 고속 연결을 사용하는 클라이언트에 대해 효과적으로 작동합니다.<br /><br /> 기업 전체에 배포되는 업데이트된 가상 응용 프로그램은 클라이언트에서 현재 버전이 대체됨을 알리는 정책을 받고 이전 버전으로부터의 변경 사항만 다운로드할 때 사용할 수 있습니다.<br /><br /> 액세스 권한은 사용자가 무단 응용 프로그램 또는 패키지에 액세스하지 못하도록 배포 지점에서 정의됩니다.|가상 응용 프로그램은 사용자가 처음으로 응용 프로그램을 실행할 때까지 스트리밍되지 않습니다. 이 시나리오에서는 사용자가 가상 응용 프로그램에 대한 프로그램 바로 가기를 받을 수 있지만, 처음으로 가상 응용 프로그램을 실행하기 전에 네트워크에서 연결이 끊길 수 있습니다. 클라이언트가 오프라인 상태인 동안 가상 응용 프로그램을 실행하려고 하면 응용 프로그램을 스트리밍하기 위한 Configuration Manager 배포 지점을 사용할 수 없기 때문에 오류가 표시되고 사용자가 가상화된 응용 프로그램을 실행할 수 없게 됩니다. 사용자가 네트워크에 다시 연결하여 응용 프로그램을 실행할 때까지 응용 프로그램을 사용할 수 없습니다.<br /><br /> 이를 방지하려면 클라이언트에 가상 응용 프로그램을 배달하는 데 로컬 배달 방법을 사용하거나, 스트리밍 배달에 인터넷 기반 클라이언트 관리를 사용하도록 설정할 수 있습니다.|  

 **로컬 배달**  

|장점|단점|  
|----------------|-------------------|  
|표준 배포 지점 기능은 BITS(Background Intelligent Transfer Service)를 사용하여 패키지를 다운로드하는 데 사용됩니다.<br /><br /> 가상 응용 프로그램 패키지 콘텐츠는 클라이언트에 로컬로 배달됩니다. 따라서 컴퓨터가 네트워크에 연결되어 있지 않을 때에도 사용자가 콘텐츠를 실행할 수 있습니다.<br /><br /> 이 방법은 네트워크 연결이 느리거나 불안정한 경우 및 컴퓨터가 네트워크에 가끔씩만 연결되는 경우에 적합합니다.<br /><br /> Configuration Manager는 RDC(원격 차등 압축)를 사용해서 가상 응용 프로그램 패키지 콘텐츠가 업데이트될 때 변경된 파일 내 바이트만 클라이언트에 전송합니다. Configuration Manager 클라이언트에서는 RDC를 사용하여 현재 버전의 패키지와 클라이언트에 전송된 변경 사항을 기반으로 새 버전의 가상 응용 프로그램 패키지를 만듭니다.<br /><br /> 이 방법을 통해 모바일 사용자와 연결이 끊긴 사용자의 응용 프로그램이 복원될 수 있습니다. 관리자는 설치 작업을 통해 가상 응용 프로그램이 배포된 경우 배달 후에 패키지를 Configuration Manager 캐시에 유지하도록 선택할 수 있습니다. Configuration Manager 클라이언트 캐시의 패키지는 App-V 클라이언트가 캐시로 패키지를 가져오기 위한 안정적인 로컬 스트리밍 원본으로 사용됩니다.|Configuration Manager 캐시에 가상 응용 프로그램을 유지하는 경우 클라이언트에 가상 응용 프로그램 패키지 크기의 최대 두 배에 이르는 디스크 공간이 필요합니다.|  

 또한 가상 응용 프로그램을 컴퓨터에 미리 설치한 다음 해당 컴퓨터의 이미지를 만들어 다른 컴퓨터에 배포할 수도 있습니다. 그러나 다른 사이트에서 가상 응용 프로그램 패키지가 만들어진 경우 응용 프로그램에 업데이트를 다운로드하는 데 이진 델타 복제가 사용되지 않습니다. 이 옵션은 가상 데스크톱 인프라에서 사용자가 로그온한 후 응용 프로그램을 다운로드하는 대신 응용 프로그램을 즉시 사용할 수 있도록 하려는 경우에 유용할 수 있습니다.  

##  <a name="migrating-from-an-app-v-infrastructure-to-a-configuration-manager-and-app-v-infrastructure"></a>App-V 인프라에서 Configuration Manager 및 App-V 인프라로 마이그레이션  
 다음 표에서는 Configuration Manager를 사용하여 기존 App-V 인프라에서 가상 응용 프로그램 관리로의 마이그레이션을 계획하는 데 도움이 되는 정보를 제공합니다.  

|단계|추가 정보|  
|----------|----------------------|  
|현재 가상 응용 프로그램을 검토하여 Configuration Manager 인프라로 마이그레이션할 응용 프로그램을 선택합니다.|추가 정보가 없습니다.|  
|가상 응용 프로그램을 배포할 사용자와 장치를 평가합니다.|가상 응용 프로그램을 배포할 사용자와 장치를 함께 그룹화하는 Configuration Manager 컬렉션을 만듭니다. 자세한 내용은 [컬렉션 소개](/sccm/core/clients/manage/collections/introduction-to-collections)를 참조하세요.|  
|App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 마이그레이션합니다.|자세한 내용은 이 항목의 [App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 마이그레이션](/sccm/apps/get-started/deploying-app-v-virtual-applications#migrate-app-v-5-connection-groups-to-configuration-manager-virtual-environments) 섹션을 참조하세요.|  
|가상 응용 프로그램이 Configuration Manager 인프라에 전체 응용 프로그램으로 존재하는지 확인합니다.|관리를 간소화하기 위해 가상 응용 프로그램을 새 배포 유형으로 기존 전체 응용 프로그램에 추가할 수 있습니다. 배포 유형을 만드는 방법에 대한 자세한 내용은 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.|  
|기존 APP-V 패키지를 대체하는 응용 프로그램을 만듭니다.|Configuration Manager 응용 프로그램을 만드는 방법에 대한 자세한 내용은 [응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management) 및 [응용 프로그램 만들기](../../apps/deploy-use/create-applications.md)를 참조하세요.|  
|가상 응용 프로그램이 처음 배포된 후에 클라이언트에서 Configuration Manager를 통해 가상 응용 프로그램 관리를 시작합니다. 이후에 컴퓨터의 모든 App-V 응용 프로그램은 Configuration Manager로 관리해야 합니다.|추가 정보가 없습니다.|  
|응용 프로그램의 로컬 배달을 사용하도록 콘텐츠를 적절한 배포 지점에 배포합니다.|자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.|  
|Configuration Manager 클라이언트에 응용 프로그램을 배포합니다.<br /><br /> 매니페스트 XML 파일을 만들지 않는 이전 버전의 시퀀서로 App-V 응용 프로그램이 만들어진 경우 최신 버전의 시퀀서로 이 응용 프로그램을 열고 저장하여 매니페스트 XML 파일을 만들 수 있습니다. 이 파일은 Configuration Manager를 사용하여 가상 응용 프로그램을 배포하는 데 필요합니다.<br /><br /> App-V는 SoftGrid 4.1 SP1 또는 4.2 버전의 시퀀서로 만들어진 가상 응용 프로그램 패키지를 지원합니다.<br /><br /> 응용 프로그램이 이전에 로컬로 설치된 경우 이를 제거한 후에 응용 프로그램의 가상 버전을 배포해야 합니다.|자세한 내용은 [응용 프로그램 배포](../../apps/deploy-use/deploy-applications.md)를 참조하세요.|  
|System Center Configuration Manager에서는 더 이상 가상 응용 프로그램이 포함된 패키지와 프로그램을 사용할 수 없습니다. Configuration Manager 2007에서 System Center Configuration Manager로 마이그레이션할 때 Configuration Manager가 이러한 패키지를 응용 프로그램으로 변환합니다.<br /><br /> Configuration Manager 2007 보급 알림은 다음 배포 유형으로 변환됩니다.<br /><br /> - 보급 알림이 없는 App-V 패키지 마이그레이션: 기본 배포 유형 설정을 사용하는 한 가지 배포 유형입니다.<br /><br /> - 보급 알림이 하나 포함된 App-V 패키지 마이그레이션: Configuration Manager 2007 보급 알림과 동일한 설정을 사용하는 <br />                한 가지 배포 유형입니다.<br /><br /> - 보급 알림이 여러 개 포함된 App-V 패키지 마이그레이션: 각각에 대한 배포 유형 <br />                Configuration Manager 2007 보급 알림은 해당 보급 알림에 대한 설정을 사용합니다.|자세한 내용은 [Configuration Manager 개체를 System Center Configuration Manager로 마이그레이션하도록 계획](../../core/migration/planning-for-the-migration-of-objects.md)을 참조하세요.|  

##  <a name="migrate-app-v-5-connection-groups-to-configuration-manager-virtual-environments"></a>App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 마이그레이션  
 Configuration Manager의 App-V 가상 환경에서는 배포된 가상 응용 프로그램이 클라이언트 컴퓨터에 있는 동일한 파일 시스템과 레지스트리를 공유할 수 있습니다. 즉, 일반 가상 응용 프로그램과 달리 이러한 응용 프로그램은 서로 데이터를 공유할 수 있습니다. 응용 프로그램이 설치되거나 클라이언트에서 다음 번에 설치된 응용 프로그램을 평가할 때 클라이언트 컴퓨터에서 가상 환경이 만들어지거나 수정됩니다. 가상 환경은 독립 실행형 App-V 5의 연결 그룹과 유사합니다.  

 연결 그룹을 독립 실행형 App-V 5에서 Configuration Manager 가상 환경으로 마이그레이션하는 경우 클라이언트 컴퓨터에 이미 있는 연결 그룹이 Configuration Manager에서 올바르게 관리되고 이러한 연결 그룹 내 사용자 환경이 유지되는지 확인해야 합니다.  

 성공적으로 App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 변환하려면 다음 절차를 따르세요.  
  
### <a name="convert-app-v-5-connection-groups-to-configuration-manager-virtual-environments"></a>App-V 5 연결 그룹을 Configuration Manager 가상 환경으로 변환  
  
1.  App-V에 있던 모든 응용 프로그램에 대한 Configuration Manager 응용 프로그램을 만듭니다.  

2.  배포 목적이 **필수**인 사용자 또는 장치에 응용 프로그램을 배포합니다. App-V에서 응용 프로그램을 사용하는 사용자와 동일한 사용자에게 배포해야 하며, App-V에 응용 프로그램을 보유한 동일한 컴퓨터에 배포해야 합니다.  

3.  배포가 완료되면 독립 실행형 App-V에 게시된 연결 그룹과 일치하는 가상 환경을 만듭니다. 가상 환경에는 동일한 패키지(구체적으로는 App-V 5 배포 유형)가 같은 순서로 포함되어야 합니다.  

App-V 가상 환경을 만드는 방법에 대한 자세한 내용은 [APP-V 가상 환경을 만드는 방법](../../apps/deploy-use/create-app-v-virtual-environments.md)을 참조하세요.  

또는 Configuration Manager로 응용 프로그램 배포를 시작하기 전에 App-V 클라이언트에서 모든 연결 그룹을 삭제할 수 있습니다. 하지만 사용자가 App-V 연결 그룹에 저장했을 수 있는 설정이 손실됩니다.  

##  <a name="dynamic-suite-composition-in-app-v-46"></a>APP-V 4.6의 Dynamic Suite Composition  
 Dynamic Suite Composition은 다른 가상 응용 프로그램 패키지에 대한 종속성을 보유한 상태로 단일 가상 응용 프로그램 패키지를 정의할 수 있는 기능을 제공합니다. 응용 프로그램이 실행될 때 App-V 클라이언트는 동일한 가상 환경에서 응용 프로그램의 기본 패키지와 종속 패키지를 호스트합니다.  

 Configuration Manager와 함께 이 기능을 사용하려면 두 패키지 모두 App-V 클라이언트에 배포 및 등록되어야 합니다. 종속 패키지 콘텐츠가 클라이언트 컴퓨터에 로컬로 호스트되어 있는지 확인하려면 응용 프로그램 배포를 로컬 배달(다운로드 및 실행)로 구성합니다.  

 App-V Dynamic Suite Composition에 대한 자세한 내용은 관련 App-V 설명서를 참조하세요.  

##  <a name="convert-app-v-46-applications-to-app-v-5-applications"></a>App-V 4.6 응용 프로그램을 App-V 5 응용 프로그램으로 변환  
 App-V 4.6과 App-V 5 간에는 응용 프로그램 패키지 형식이 변경되었습니다. App-V 4.6을 사용하여 시퀀스된 응용 프로그램은 더 이상 지원되지 않습니다. 하지만 App-V 5의 패키지 변환기 도구를 사용하여 응용 프로그램을 변환할 수 있습니다. 자세한 내용은 [APP-V 5 설명서](http://technet.microsoft.com/library/jj713472.aspx)를 참조하세요.  

 App-V 4.6 응용 프로그램을 App-V 5 응용 프로그램으로 변환하려면 다음 단계를 따르세요.  

1.  App-V 4.6 패키지를 App-V 5 형식으로 변환하거나 시퀀싱 작업을 다시 수행합니다.  

2.  App-V 5 클라이언트를 계층에 있는 컴퓨터에 배포합니다.  

3.  App-V 5 응용 프로그램용 배포 유형이 포함된 새 응용 프로그램을 만들고 App-V 4.6 응용 프로그램을 교체하는 교체 규칙을 만듭니다.  

4.  필요한 경우 가상 환경을 만듭니다.  

5.  새 5 APP-V 응용 프로그램을 컴퓨터에 배포합니다.  

##  <a name="user-and-deployment-configuration-files"></a>사용자 및 배포 구성 파일  
 사용자 및 배포 구성 파일에는 응용 프로그램의 동작 방식을 제어하는 설정이 포함되어 있습니다. 이러한 파일을 사용하면 응용 프로그램을 다시 시퀀싱하지 않고 응용 프로그램 설정을 변경할 수 있습니다.  

 일반적인 App-V 5 응용 프로그램에는 다음 파일이 포함되어 있을 수 있습니다.  

-   응용 프로그램 패키지(.appv) 파일  

-   사용자 구성 파일  

-   배포 구성 파일  

 사용자 구성 파일에는 로그온한 사용자에게만 적용되는 설정이 포함됩니다. 예를 들어 구성 파일을 편집하여 사용자에게 배포되는 응용 프로그램의 바로 가기에 대한 정보를 변경할 수 있습니다. 또한 여러 배포 유형을 포함하는 Configuration Manager 응용 프로그램을 만들 수도 있습니다. 각 배포 유형별로 다른 사용자 구성 파일을 포함하고, 요구 사항 규칙을 사용하여 관련 사용자에 대한 응용 프로그램만 설치되도록 할 수 있습니다.  

 배포 구성 파일에는 레지스트리 설정과 같이 컴퓨터에 적용되는 설정이 포함됩니다. 파일에는 모든 사용자에게 적용되는 사용자 설정도 포함됩니다.  

 Configuration Manager로 App-V 5 가상 응용 프로그램을 배포하려는 경우 모든 세 파일이 App-V 5 배포 유형을 만들 때 사용한 폴더와 동일한 폴더에 있어야 합니다. 폴더에 여러 파일이 있는 경우 Configuration Manager는 최신 파일을 사용합니다.  

 자세한 내용은 [APP-V 5 설명서](http://technet.microsoft.com/library/jj713466.aspx)를 참조하세요.  

##  <a name="app-v-local-interaction"></a>App-V 로컬 상호 작용  
 일부 응용 프로그램 배포의 경우 일부 응용 프로그램은 클라이언트 컴퓨터에 로컬로 설치되고 다른 응용 프로그램은 동일한 클라이언트 컴퓨터에 가상 응용 프로그램으로 배포될 수 있습니다. 기본적으로, 로컬로 설치된 응용 프로그램은 가상화된 응용 프로그램과 직접 통신하거나 서로 인식할 수 없습니다. 이러한 현상은 App-V에서 제공되는 응용 프로그램 격리의 정상적인 동작입니다. 로컬 상호 작용은 App-V 클라이언트의 기능으로, 클라이언트 컴퓨터에서 실행되는 로컬에 설치된 응용 프로그램이 가상화된 응용 프로그램을 확인하고 가상화된 응용 프로그램과 통신할 수 있도록 각 응용 프로그램에 대해 이 기능을 사용하도록 설정할 수 있습니다. Configuration Manager 및 App-V는 로컬 상호 작용을 완전히 지원합니다.  

 App-V 로컬 상호 작용 기능에 대한 자세한 내용은 관련 App-V 설명서를 참조하세요.  

##  <a name="app-v-5-shared-content-store"></a>App-V 5 공유 콘텐츠 저장소  
 App-V 5 공유 콘텐츠 저장소 기능은 Configuration Manager에서 지원됩니다. 자세한 내용은 [App-V 5.0 SCS(공유 콘텐츠 저장소) 계획](http://technet.microsoft.com/library/jj713431.aspx)항목을 참조하세요.  

##  <a name="monitor-virtual-applications"></a>가상 응용 프로그램 모니터링  

### <a name="virtual-application-reports"></a>가상 응용 프로그램 보고서  
 다음 보고서를 사용하여 Configuration Manager 환경에서 App-V를 모니터링할 수 있습니다.  

|보고서 이름|설명|  
|-----------------|-----------------|  
|APP-V 가상 환경 결과|선택한 가상 환경의 선택한 컬렉션이 지정한 상태에 있는 경우 해당 정보를 표시합니다(App-V 5에만 해당).|  
|자산에 대한 App-V 가상 환경 결과|선택한 자산의 선택한 가상 환경에 대한 정보 및 선택한 가상 환경의 모든 배포 유형에 대한 정보를 표시합니다(App-V 5에만 해당).|  
|App-V 가상 환경 상태|선택한 컬렉션의 선택한 가상 환경에 대한 호환성 정보를 표시합니다. 이 보고서의 **보존** 열은 이전에 구성된 가상 환경의 자산 중 더 이상 적용할 수 없지만 가상 환경에서 실행하는 응용 프로그램의 사용자 설정을 유지할 목적으로 보존되는 자산을 표시합니다(App-V 5에만 해당).|  
|특정 가상 응용 프로그램을 포함하는 컴퓨터|Application Virtualization Management Sequencer를 사용하여 만든 지정 App-V 바로 가기가 있는 컴퓨터의 요약 정보를 표시합니다(App-V 4.6에만 해당).|  
|특정 가상 응용 프로그램 패키지를 포함하는 컴퓨터|지정한 App-V 응용 프로그램 패키지가 설치된 컴퓨터 목록을 표시합니다(App-V 4.6에만 해당).|  
|모든 가상 응용 프로그램 패키지 인스턴스 수|검색한 모든 App-V 응용 프로그램 패키지 수를 표시합니다(App-V 4.6에만 해당).|  
|모든 가상 응용 프로그램 인스턴스 수|검색한 모든 App-V 응용 프로그램 수를 표시합니다(App-V 4.6에만 해당).|  

## <a name="log-files"></a>로그 파일  
 Configuration Manager는 가상 응용 프로그램 배포에 대한 정보를 로그 파일에 기록합니다. 가상 응용 프로그램 및 Configuration Manager 응용 프로그램 관리에서 사용되는 로그 파일에 대한 자세한 내용은 [System Center Configuration Manager의 로그 파일](../../core/plan-design/hierarchy/log-files.md)을 참조하세요.  

 또한 다음 위치에서 App-V 클라이언트 로그 파일을 찾을 수 있습니다.  

-   Windows Vista, Windows 7 및 Windows 8: **C:\ProgramData\Microsoft\Application Virtualization Client**  



<!--HONumber=Nov16_HO1-->


