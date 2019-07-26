---
title: 권장 하드웨어
titleSuffix: Configuration Manager
description: System Center Configuration Manager 환경을 기본 배포 이상으로 확장하는 데 도움이 되는 하드웨어 권장 사항을 확인합니다.
ms.date: 05/23/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5267f0af-34d3-47a0-9ab8-986c41276e6c
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: cbad2440f9309e712fb00da2739ed5302866ff63
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68339473"
---
# <a name="recommended-hardware-for-system-center-configuration-manager"></a>System Center Configuration Manager에 권장되는 하드웨어

*적용 대상: System Center Configuration Manager(현재 분기)*

사이트, 사이트 시스템 및 클라이언트의 기본 배포 이상을 지원하도록 System Center Configuration Manager 환경을 확장하려는 경우 다음 권장 사항을 지침으로 참고할 수 있습니다. 권장 사항이 가능한 모든 사이트 및 계층 구조 구성을 포괄하는 것은 아닙니다.  

다음 섹션의 정보는 기본 구성으로 사용 가능한 Configuration Manager 기능을 사용하는 클라이언트와 사이트의 처리 부하를 충족할 수 있는 하드웨어를 계획하기 위한 지침으로 사용하세요.  



##  <a name="bkmk_ScaleSieSystems"></a> 사이트 시스템  
이 섹션에서는 최대 개수의 클라이언트를 지원하고 Configuration Manager 기능을 대부분 또는 모두 사용하는 배포를 위해 Configuration Manager 사이트 시스템에 권장되는 하드웨어 구성을 제공합니다. 최대 개수보다 적은 클라이언트를 지원하고 사용 가능한 모든 기능을 사용하지 않는 배포에서 필요한 컴퓨터 리소스는 더 적을 수 있습니다. 일반적으로 전반적인 시스템의 성능을 제한하는 주요 요인은 나열된 순서대로 다음과 같습니다.  

1.  디스크 I/O 성능  

2.  사용 가능한 메모리  

3.  CPU  

성능을 최적화하려면 모든 데이터 드라이브 및 1Gbps 이더넷 네트워크에 대해 RAID 10 구성을 사용합니다.  

###  <a name="bkmk_ScaleSiteServer"></a> 사이트 서버  

|사이트 구성|CPU(코어)|메모리(GB)|SQL Server에 대한 메모리 할당(%)|  
|-------------------------------|---------------|---------------|----------------------------------------|  
|동일한 서버에 데이터베이스 사이트 역할이 있는 독립 실행형 기본 사이트 서버<sup>1</sup>|16|96|80|  
|원격 사이트 데이터베이스가 있는 독립 실행형 기본 사이트 서버|8|16|-|  
|독립 실행형 기본 사이트에 대한 원격 데이터베이스 서버|16|72|90|  
|동일한 서버에 데이터베이스 사이트 역할이 있는 중앙 관리 사이트 서버<sup>1</sup>|20|128|80|  
|원격 사이트 데이터베이스가 있는 중앙 관리 사이트 서버|8|16|-|  
|중앙 관리 사이트에 대한 원격 데이터베이스 서버|16|96|90|  
|동일한 서버에 데이터베이스 사이트 역할이 있는 자식 기본 사이트|16|96|80|  
|원격 사이트 데이터베이스가 포함된 자식 기본 사이트 서버|8|16|-|  
|자식 기본 사이트에 대한 원격 데이터베이스 서버|16|72|90|  
|보조 사이트 서버|8|16|-|  

<sup>1</sup> 사이트 서버와 SQL Server가 동일한 컴퓨터에 설치된 경우 배포에서 사이트와 클라이언트에 대해 최대 [크기 조정 및 규모 숫자 값](/sccm/core/plan-design/configs/size-and-scale-numbers)을 지원합니다. 그러나 이 구성에서는 SQL Server 클러스터 사용과 같은 [System Center Configuration Manager의 고가용성 옵션](/sccm/protect/understand/high-availability-options)이 제한될 수 있습니다. 또한 동일한 컴퓨터에서 실행할 경우 SQL Server와 Configuration Manager 사이트 서버를 둘 다 지원하기 위해 더 높은 I/O 요구 사항이 필요하기 때문에 대규모 배포를 사용하는 경우 원격 SQL Server 컴퓨터가 포함된 구성을 사용하는 것이 좋습니다.  

###  <a name="bkmk_RemoteSiteSystem"></a> 원격 사이트 시스템 서버  
다음 지침은 단일 사이트 시스템 역할을 포함하는 컴퓨터에 적용됩니다. 같은 컴퓨터에 여러 사이트 시스템 역할을 설치할 때는 해당 지침을 조정하세요.  

|사이트 시스템 역할|CPU(코어)|메모리(GB)|디스크 공간(GB)|  
|----------------------|---------------|---------------|--------------------|  
|관리 지점|4|8|50|  
|배포 지점|2|8|운영 체제의 요구 사항을 충족하고 배포되는 콘텐츠를 저장할 수 있는 크기|  
|사이트 시스템 컴퓨터에서 웹 서비스와 웹 사이트를 사용하는 애플리케이션 카탈로그|4|16|50|  
|소프트웨어 업데이트 지점<sup>1</sup>|8|16|운영 체제의 요구 사항을 충족하고 배포되는 업데이트를 저장할 수 있는 크기|  
|기타 모든 사이트 시스템 역할|4|8|50|  

<sup>1</sup> 소프트웨어 업데이트 지점을 호스트하는 컴퓨터에서 IIS 애플리케이션 풀에 대해 다음 구성을 사용해야 합니다.  

- **WsusPool 큐 길이**를 **2000**으로 늘립니다.  

- **WsusPool 프라이빗 메모리 제한**을 4배로 늘리거나 **0**(무제한)으로 설정합니다.  

###  <a name="bkmk_DiskSpace"></a> 사이트 시스템용 디스크 공간  
디스크 할당 및 구성은 Configuration Manager 성능에 영향을 줍니다. 각 Configuration Manager 환경이 서로 다르므로 구현하는 값은 다음 지침과 달라질 수 있습니다.  

최적의 성능을 위해서는 각 개체를 별도의 전용 RAID 볼륨에 배치해야 합니다. 모든 데이터 볼륨(Configuration Manager 및 해당 데이터베이스 파일)에 대해 RAID 10을 사용할 때 최적의 성능을 낼 수 있습니다.  

|데이터 사용량|최소 디스크 공간|25,000개의 클라이언트|50,000개의 클라이언트|100,000개의 클라이언트|150,000개의 클라이언트|700,000개의 클라이언트(중앙 관리 사이트)|  
|----------------|------------------------|--------------------|--------------------|---------------------|---------------------|-----------------------------------------------------|  
|운영 체제|운영 체제에 대한 지침을 참조하세요.|운영 체제에 대한 지침을 참조하세요.|운영 체제에 대한 지침을 참조하세요.|운영 체제에 대한 지침을 참조하세요.|운영 체제에 대한 지침을 참조하세요.|운영 체제에 대한 지침을 참조하세요.|  
|Configuration Manager 애플리케이션 및 로그 파일|25GB|50GB|100GB|200GB|300GB|200GB|  
|사이트 데이터베이스 .mdf 파일|25,000개의 클라이언트당 75GB|75GB|150GB|300GB|500GB|2TB|  
|사이트 데이터베이스 .ldf 파일|25,000개의 클라이언트당 25GB|25GB|50GB|100GB|150GB|100GB|  
|임시 데이터베이스 파일(.mdf 및.ldf)|필요에 따라|필요에 따라|필요에 따라|필요에 따라|필요에 따라|필요에 따라|  
|콘텐츠(배포 지점 공유)|필요한 경우<sup>1</sup>|필요한 경우<sup>1</sup>|필요한 경우<sup>1</sup>|필요한 경우<sup>1</sup>|필요한 경우<sup>1</sup>|필요한 경우<sup>1</sup>|  

<sup>1</sup> 디스크 공간 지침에는 사이트 서버나 배포 지점의 콘텐츠 라이브러리에 있는 콘텐츠에 필요한 공간이 포함되지 않습니다. 콘텐츠 라이브러리 계획에 대한 자세한 내용은 [콘텐츠 라이브러리](../../../core/plan-design/hierarchy/the-content-library.md)를 참조하세요.  

디스크 공간 요구 사항을 계획할 때는 위의 지침 이외에도 다음과 같은 지침을 고려해야 합니다.  

- 클라이언트당 약 5MB의 공간이 필요합니다.  

- 기본 사이트를 위한 임시 데이터베이스 크기를 계획하는 경우 데이터베이스를 합한 크기를 사이트 데이터베이스 .mdf 파일의 25%~30% 크기로 계획합니다. 실제 크기는 훨씬 작거나 클 수 있으며 사이트 서버의 성능과 장/단기 수신 데이터 양에 따라 달라집니다.  

  > [!NOTE]  
  >  사이트의 클라이언트 수가 50,000개 이상이면 4개 이상의 임시 데이터베이스 .mdf 파일을 사용하도록 계획합니다.  

- 중앙 관리 사이트의 임시 데이터베이스 크기는 일반적으로 기본 사이트의 경우보다 훨씬 작습니다.  

- 보조 사이트 데이터베이스에는 다음 크기 제한이 있습니다.  

  - SQL Server 2012 Express: 10GB  

  - SQL Server 2014 Express: 10GB  

##  <a name="bkmk_ScaleClient"></a> 클라이언트  
이 섹션에서는 Configuration Manager 클라이언트 소프트웨어를 사용하여 관리하는 컴퓨터에 대해 권장되는 하드웨어 구성을 제공합니다.  

### <a name="client-for-windows-computers"></a>Windows 컴퓨터용 클라이언트  
아래에는 포함된 운영 체제를 비롯해 Configuration Manager를 사용하여 관리하는 Windows 기반 컴퓨터의 최소 요구 사항이 나와 있습니다.  

- **프로세서 및 메모리:** 컴퓨터 운영 체제의 프로세서 및 RAM 요구 사항을 참조하세요.  

- **디스크 공간:** 500MB의 사용 가능한 디스크 공간(Configuration Manager 클라이언트 캐시의 경우 5GB 권장) 사용자 지정된 설정을 사용하여 Configuration Manager 클라이언트를 설치하는 경우에는 필요한 디스크 공간이 더 적어집니다.  

  - 클라이언트에 불필요한 파일을 설치하지 않으려면 CCMSetup 명령줄 속성 /skipprereq를 사용합니다. 예를 들어 클라이언트가 응용 프로그램 카탈로그를 사용하지 않는 경우에는 `CCMSetup.exe /skipprereq:silverlight.exe`를 실행합니다. Configuration Manager 1802부터 Silverlight는 더 이상 자동으로 설치되지 않습니다.  

  - 기본값인 5120MB보다 작은 캐시 파일을 설정하려면 Client.msi 속성 SMSCACHESIZE를 사용합니다. 최소 크기는 1MB입니다. 예를 들어 `CCMSetup.exe SMSCachesize=2`를 사용하는 경우 크기가 2MB인 캐시가 만들어집니다.  

  이러한 클라이언트 설치 설정에 대한 자세한 내용은 [클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

  > [!TIP]  
  >  일반적으로 표준 Windows 컴퓨터에 비해 디스크 크기가 작은 Windows Embedded 디바이스에서는 최소 디스크 공간을 사용하여 클라이언트를 설치하면 유용합니다.  



 Configuration Manager의 선택적 기능에 대한 최소 추가 하드웨어 요구 사항은 다음과 같습니다.  

- **운영 체제 배포:** 384MB의 RAM  

- **소프트웨어 센터:** 500MHz 프로세서  

- **원격 제어:** : Pentium 4 하이퍼 스레드 3GHz(단일 코어) 또는 동급 CPU. 환경을 최적화하려면 1GB RAM 이상이 필요합니다.  

### <a name="client-for-linux-and-unix"></a>Linux 및 UNIX용 클라이언트  
아래에는 Configuration Manager를 사용하여 관리하는 Linux 및 UNIX 서버의 최소 요구 사항이 나와 있습니다.  

|요구 사항|세부 정보|  
|-----------------|-------------|  
|프로세서 및 메모리|컴퓨터 운영 체제의 프로세서 및 RAM 요구 사항을 참조하십시오.|  
|디스크 공간|500MB의 사용 가능한 디스크 공간(Configuration Manager 클라이언트 캐시의 경우 5GB 권장)|  
|네트워크 연결|관리를 수행하려면 Configuration Manager 클라이언트 컴퓨터가 네트워크를 통해 Configuration Manager 사이트 시스템에 연결할 수 있어야 합니다.|  

##  <a name="bkmk_ScaleConsole"></a> Configuration Manager 콘솔  
다음 표의 요구 사항은 Configuration Manager 콘솔을 실행하는 각 컴퓨터에 적용됩니다.  

**최소 하드웨어 구성:**  

- Intel i3 또는 동급 CPU  

- 2GB RAM  

- 2GB의 디스크 공간  

|DPI 설정|최소 해상도|  
|-----------------|------------------------|  
|96/100%|1024 x 768|  
|120/125%|1280 x 960|  
|144/150%|1600 x 1200|  
|196/200%|2500 x 1600|  

**PowerShell 지원:**  

Configuration Manager 콘솔을 실행하는 컴퓨터에 PowerShell 지원을 설치하면 해당 컴퓨터에서 PowerShell cmdlet을 실행하여 Configuration Manager를 관리할 수 있습니다.

- PowerShell 3.0 이상이 지원됩니다.

PowerShell 외에 WMF(Windows Management Framework) 버전 3.0 이상이 지원됩니다.   


##  <a name="bkmk_ScaleLab"></a> 랩 배포  
Configuration Manager 랩 및 테스트 배포의 경우 다음 최소 하드웨어 권장 사항을 따르세요. 이러한 권장 사항은 모든 사이트 유형, 최대 100개의 클라이언트에 적용됩니다.  

|역할|CPU(코어)|메모리(GB)|디스크 공간(GB)|  
|----------|---------------|-------------------|-----------------------|  
|사이트 및 데이터베이스 서버|2 - 4|8 - 12|100|  
|사이트 시스템 서버|1 - 4|2 - 4|50|  
|클라이언트|1 - 2|1 - 3|30|  
