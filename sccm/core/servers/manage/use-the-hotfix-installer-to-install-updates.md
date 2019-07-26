---
title: 핫픽스 설치 관리자
titleSuffix: Configuration Manager
description: Configuration Manager용 핫픽스 설치 관리자를 통해 업데이트를 설치하는 시기 및 방법을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: f3058277-c597-4dac-86d1-41b6f7e62b36
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7831b8b818f68b3094ed765eb5e69441ce18d0f6
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68337897"
---
# <a name="use-the-hotfix-installer-to-install-updates-for-system-center-configuration-manager"></a>핫픽스 설치 관리자를 사용하여 System Center Configuration Manager의 업데이트 설치

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 일부 업데이트는 Microsoft 클라우드 서비스에서 사용할 수 없으며, 대역 외에서만 가져옵니다. 특정 문제를 해결하는 제한된 릴리스 핫픽스를 예로 들 수 있습니다.   
Microsoft에서 받은 업데이트(핫픽스)를 설치해야 하며 해당 업데이트의 파일 이름이 **.exe** 확장명(**update.exe** 제외)으로 끝나는 경우 해당 핫픽스 다운로드에 포함된 핫픽스 설치 관리자를 사용하여 Configuration Manager 사이트 서버에 직접 업데이트를 설치합니다.  

핫픽스 파일에 **.update.exe** 파일 확장명이 있는 경우 [업데이트 등록 도구를 사용하여 System Center Configuration Manager에 핫픽스 가져오기](../../../core/servers/manage/use-the-update-registration-tool-to-import-hotfixes.md)를 참조하세요.  

> [!NOTE]  
> 이 항목에서는 System Center Configuration Manager를 업데이트하는 핫픽스를 설치하는 방법에 대한 일반적인 지침을 제공합니다. 특정 업데이트에 대한 자세한 내용은 Microsoft 지원에서 해당 KB(기술 자료)를 참조하세요.  

##  <a name="bkmk_Overview"></a> Configuration Manager의 핫픽스 개요  
Configuration Manager의 핫픽스는 SQL Server와 같은 다른 Microsoft 제품과 비슷하고 하나의 개별 수정이나 번들(수정 사항의 롤업)을 포함하며 Microsoft 기술 자료 문서에서 설명되어 있습니다.  

개별 업데이트에는 특정 버전의 Configuration Manager에 대한 단일 집중 업데이트가 포함됩니다.  
업데이트 번들에는 특정 버전의 Configuration Manager에 대한 여러 업데이트가 포함됩니다.  
업데이트가 번들인 경우 해당 번들에서 개별 업데이트를 설치할 수 없습니다.  

배포를 만들어 추가 컴퓨터에 업데이트를 설치하려는 경우 중앙 관리 사이트 서버 또는 기본 사이트 서버에 업데이트 번들을 설치해야 합니다.  

업데이트 번들을 실행하면 다음과 같은 작업이 수행됩니다.  

- 업데이트 번들에서 적용 가능한 각 구성 요소의 업데이트 파일을 추출합니다.  

- 업데이트 및 업데이트 배포 옵션을 구성하는 프로세스를 안내하는 마법사를 시작합니다.  

- 마법사를 완료하면 사이트 서버에 적용되는 번들의 업데이트가 사이트 서버에 설치됩니다.  

마법사는 업데이트를 추가 컴퓨터에 설치하는 데 사용할 수 있는 배포를 만들기도 합니다. 소프트웨어 배포 패키지 또는 Microsoft System Center Updates Publisher 2011 등의 지원되는 배포 방법을 사용하여 추가 컴퓨터에 업데이트를 배포합니다.  

마법사를 실행하면 Updates Publisher 2011에서 사용하기 위한 **.cab** 파일이 사이트 서버에 생성됩니다. 필요한 경우에는 소프트웨어 배포용 패키지도 하나 이상 만들도록 마법사를 구성할 수 있습니다. 이러한 배포를 사용하여 클라이언트 또는 Configuration Manager 콘솔과 같은 구성 요소에 업데이트를 설치할 수 있습니다. 또한 Configuration Manager 클라이언트를 실행하지 않는 컴퓨터에 업데이트를 수동으로 설치할 수 있습니다.  

Configuration Manager의 다음 세 그룹을 업데이트할 수 있습니다.  

- 다음을 포함하는 Configuration Manager 서버 역할:  

  - 중앙 관리 사이트  

  - 기본 사이트  

  - 보조 사이트  

  - 원격 SMS 공급자  

- Configuration Manager 콘솔  

- Configuration Manager 클라이언트  

> [!NOTE]  
> **사이트 시스템 역할에 대한 업데이트**(사이트 데이터베이스 및 클라우드 기반 배포 지점에 대한 업데이트 포함)는 사이트 구성 요소 관리자가 사이트 서버 및 서비스용 업데이트의 일부로 설치됩니다.  
>   
> 그러나 업데이트 끌어오기 배포 지점은 사이트 구성 요소 관리자가 아닌 배포 관리자에서 서비스됩니다.  

Configuration Manager의 각 업데이트 번들은 해당 Configuration Manager 구성 요소에 업데이트를 설치하는 데 필요한 파일이 포함된 자동 압축 풀기 .exe 파일(SFX)입니다. 일반적으로 SFX 파일에는 다음 파일이 포함될 수 있습니다.  

|파일|세부 정보|  
|----------|-------------|  
|&lt;제품 버전\>-QFE-KB&lt;기술 자료 문서 ID\>-&lt;플랫폼\>-&lt;언어\>.exe|업데이트 파일입니다. 이 파일의 명령줄은 Updatesetup.exe로 관리됩니다.<br /><br /> 예:<br />CM1511RTM-QFE-KB123456-X64-ENU.exe|  
|Updatesetup.exe|이 .msi wrapper는 업데이트 번들의 설치를 관리합니다.<br /><br /> 업데이트를 설치할 때 Updatesetup.exe가 실행되는 컴퓨터의 표시 언어를 감지합니다. 기본적으로 업데이트의 사용자 인터페이스는 영어로 되어 있습니다. 그러나 표시 언어가 지원되는 경우 사용자 인터페이스에 컴퓨터의 로컬 언어가 표시됩니다.|  
|License_&lt;언어\>.rtf|해당되는 경우 각 업데이트에는 지원되는 언어에 대한 하나 이상의 라이센스 파일이 들어 있습니다.|  
|&lt;제품 및 업데이트 형식>-&lt;제품 버전\>-&lt;기술 자료 문서 ID\>-&lt;플랫폼\>.msp|Configuration Manager 콘솔 또는 클라이언트에 업데이트가 적용될 때 업데이트 번들에는 별도의 Windows 설치 관리자 패치(.msp) 파일이 포함되어 있습니다.<br /><br /> 예:<br /><br /> **Configuration Manager 콘솔 업데이트:** ConfigMgr1511-AdminUI-KB1234567-i386.msp<br /><br /> **클라이언트 업데이트:** ConfigMgr1511-client-KB1234567-i386.msp<br />ConfigMgr1511-client-KB1234567-x64.msp|  

기본적으로 업데이트 번들은 작업을 사이트 서버의 .log 파일에 로깅합니다. 로그 파일은 업데이트 번들과 이름이 같으며 **%SystemRoot%/Temp** 폴더에 기록됩니다.  

업데이트 번들을 실행하면 업데이트 번들과 이름이 같은 파일이 컴퓨터의 임시 폴더에 추출된 다음 Updatesetup.exe가 실행됩니다. Updatesetup.exe는 Configuration Manager &lt;제품 버전\> &lt;KB 번호\>의 소프트웨어 업데이트 마법사를 시작합니다.  

업데이트의 범위에 해당하는 경우 마법사는 사이트 서버의 System Center Configuration Manager 설치 폴더 아래에 일련의 폴더를 만듭니다. 폴더 구조는   
**\\\\&lt;서버 이름\>\SMS_&lt;사이트 코드\>\Hotfix\\&lt;KB 번호\>\\&lt;업데이트 형식\>\\&lt;플랫폼\>** 입니다.  

다음 표에는 폴더 구조의 폴더에 대한 자세한 정보가 나와 있습니다.  

|폴더 이름|추가 정보|  
|-----------------|----------------------|  
|&lt;서버 이름\>|업데이트 번들을 실행하는 사이트 서버의 이름입니다.|  
|SMS_&lt;사이트 코드\>|Configuration Manager 설치 폴더의 공유 이름입니다.|  
|&lt;KB 번호\>|이 업데이트 번들에 대한 기술 자료 문서의 ID 번호입니다.|  
|&lt;업데이트 형식\>|Configuration Manager의 업데이트 형식입니다. 마법사에서는 업데이트 번들에 포함되는 각 업데이트 유형에 대해 별도의 폴더를 만듭니다. 폴더 이름은 업데이트 형식을 나타냅니다. 이름은 다음과 같습니다.<br /><br /> **서버**: SMS 공급자를 실행하는 사이트 서버, 사이트 데이터베이스 서버 및 컴퓨터에 대한 업데이트가 포함되어 있습니다.<br /><br /> **클라이언트**: Configuration Manager 클라이언트에 대한 업데이트가 포함되어 있습니다.<br /><br /> **AdminConsole**: Configuration Manager 콘솔에 대한 업데이트가 포함되어 있습니다.<br /><br /> 위의 업데이트 형식 외에도 마법사에서는 **SCUP**라는 이름의 폴더를 만듭니다. 이 폴더는 업데이트 형식을 나타내지 않지만, Updates Publisher에 대한 .cab 파일을 포함하고 있습니다.|  
|&lt;플랫폼\>|플랫폼별 폴더입니다. 프로세서 유형에 따른 업데이트 파일이 포함되어 있습니다.  이러한 폴더는 다음과 같습니다.<br /><br />- x64<br /><br /> - I386|  

##  <a name="bkmk_Install"></a> 업데이트를 설치하는 방법  
업데이트를 설치하려면 먼저 사이트 서버에 업데이트 번들을 설치해야 합니다. 업데이트 번들을 설치하면 해당 업데이트에 대한 설치 마법사를 시작합니다. 이 마법사는 다음을 수행합니다.  

- 업데이트 파일을 추출합니다.  

- 배포를 구성하는 데 도움을 줍니다.  

- 로컬 컴퓨터의 서버 구성 요소에 해당 업데이트를 설치합니다.  

사이트 서버에 업데이트 번들을 설치하면 Configuration Manager를 업데이트하는 핫픽스를 설치하는 방법에 대한 일반적인 지침을 제공합니다. 다음 표에서는 다양한 구성 요소에 대한 업데이트 작업을 설명합니다.  

|구성 요소|지침|  
|---------------|------------------|  
|사이트 서버|원격 사이트 서버에 직접 업데이트를 번들을 설치하지 않으려면 원격 사이트 서버에 업데이트를 배포합니다.|  
|사이트 데이터베이스|원격 사이트 서버의 경우, 원격 사이트 서버에 직접 업데이트를 번들을 설치하지 않으려면 사이트 데이터베이스에 대한 업데이트가 포함된 서버 업데이트를 배포합니다.|  
|Configuration Manager 콘솔|Configuration Manager 콘솔의 초기 설치 후에 이 콘솔을 실행하는 각 컴퓨터에서 Configuration Manager 콘솔에 대한 업데이트를 설치할 수 있습니다. 콘솔 초기 설치 시에 업데이트를 적용하도록 Configuration Manager 콘솔 설치 파일을 수정할 수 없습니다.|  
|원격 SMS 공급자|업데이트 번들을 설치한 사이트 서버가 아닌 컴퓨터에서 실행되는 각 SMS 공급자 인스턴스의 업데이트를 설치합니다.|  
|Configuration Manager 클라이언트|Configuration Manager 클라이언트의 초기 설치 후에 이 클라이언트를 실행하는 각 컴퓨터에서 Configuration Manager 클라이언트에 대한 업데이트를 설치할 수 있습니다.|  

> [!NOTE]  
> Configuration Manager 클라이언트를 실행하는 컴퓨터에만 업데이트를 배포할 수 있습니다.  

클라이언트, Configuration Manager 콘솔 또는 SMS 공급자를 다시 설치하는 경우 이러한 구성 요소에 대한 업데이트도 다시 설치해야 합니다.  

Configuration Manager의 각 구성 요소에 대한 업데이트를 설치하려면 다음 섹션의 정보를 사용하세요.  

###  <a name="bkmk_servers"></a> 서버 업데이트  
서버에 대한 업데이트에는 **SMS 공급자**인스턴스를 실행하는 **site database**, **사이트 데이터베이스**및 컴퓨터에 대한 업데이트가 포함될 수 있습니다.  

####  <a name="bkmk_site"></a> 사이트 업데이트  
Configuration Manager 사이트를 업데이트하기 위해 사이트 서버에 직접 업데이트 번들을 설치하거나 한 사이트에 업데이트 번들을 설치한 후 다른 사이트 서버에 업데이트를 배포할 수 있습니다.  

사이트 서버에 업데이트를 설치하면 업데이트 설치 프로세스가 사이트 시스템 역할 업데이트를 비롯하여 업데이트 적용에 필요한 추가 작업을 관리합니다. 사이트 데이터베이스는 이에 대한 예외입니다. 다음 섹션에는 사이트 데이터베이스를 업데이트하는 방법에 대한 정보가 포함되어 있습니다.  

####  <a name="bkmk_database"></a> 사이트 데이터베이스 업데이트  
설치 프로세스에서 사이트 데이터베이스를 업데이트하기 위해 사이트 데이터베이스에 대해 **update.sql** 이라는 파일을 실행합니다. 업데이트 프로세스에서 자동으로 사이트 데이터베이스를 업데이트하도록 구성하거나 나중에 수동으로 사이트 데이터베이스를 업데이트할 수 있습니다.  

**사이트 데이터베이스 자동 업데이트**  

사이트 서버에 업데이트 번들을 설치하는 경우 서버 업데이트가 설치될 때 사이트 데이터베이스가 자동으로 업데이트되도록 선택할 수 있습니다. 이 결정은 업데이트 번들을 직접 설치하고, 원격 사이트 서버에 업데이트를 설치하도록 만들어진 배포를 적용하지 않는 사이트 서버에만 해당됩니다.  

> [!NOTE]  
> 사이트 데이터베이스를 자동으로 업데이트하도록 선택할 경우 데이터베이스의 위치(사이트 서버 또는 원격 컴퓨터)에 관계없이 데이터베이스가 업데이트됩니다.  

> [!IMPORTANT]  
> 사이트 데이터베이스를 업데이트하기 전에 사이트 데이터베이스의 백업을 만드십시오. 사이트 데이터베이스에 대한 업데이트는 제거할 수 없습니다. Configuration Manager에 대한 백업을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager 백업 및 복구](../../../protect/understand/backup-and-recovery.md)를 참조하세요.  

**사이트 데이터베이스 수동 업데이트**  

사이트 서버에 업데이트 번들을 설치할 때 사이트 데이터베이스를 자동으로 업데이트하지 않도록 선택할 경우 업데이트 번들이 실행되는 사이트 서버에서 서버 업데이트로 인해 데이터베이스가 수정되지 않습니다. 그러나 소프트웨어 배포를 위해 생성되었거나 설치하는 패키지를 사용하는 배포는 항상 사이트 데이터베이스를 업데이트합니다.  

> [!WARNING]  
> 사이트 서버와 사이트 데이터베이스 모두에 대한 업데이트가 포함된 경우 사이트 서버와 사이트 데이터베이스 모두에 대한 업데이트가 완료될 때까지 업데이트가 기능하지 않습니다. 업데이트가 사이트 데이터베이스에 적용될 때까지 사이트는 지원되지 않는 상태에 있게 됩니다.  

**사이트 데이터베이스를 수동으로 업데이트하려면**  

1.  사이트 서버에서 SMS_SITE_COMPONENT_MANAGER 서비스를 중지한 다음 SMS_EXECUTIVE 서비스를 중지합니다.  

2.  Configuration Manager 콘솔을 닫습니다.  

3.  해당 사이트의 데이터베이스에 대해 업데이트 스크립트 **update.sql** 을 실행합니다. 스크립트를 실행하여 SQL Server 데이터베이스를 업데이트하는 방법에 대한 자세한 내용은 사이트 데이터베이스 서버에 사용하는 SQL Server 버전의 설명서를 참조하세요.  

4.  이전 단계에서 중지했던 서비스를 다시 시작합니다.  

5.  업데이트 번들이 설치될 때 **update.sql** 이 사이트 서버의 다음 위치에 추출됩니다.  **\\\\&lt;Server Name\>\SMS_&lt;Site Code\>\Hotfix\\&lt;KB Number\>\update.sql**  

####  <a name="bkmk_provider"></a> SMS 공급자가 실행되는 컴퓨터 업데이트  
SMS 공급자의 업데이트가 포함된 업데이트 번들을 설치한 후에는SMS 공급자가 실행되는 각 컴퓨터에 업데이트를 배포해야 합니다. 이에 대한 유일한 예외는 업데이트 번들을 설치하는 사이트 서버에 이전에 설치된 SMS 공급자 인스턴스입니다. 사이트 서버에 있는 SMS 공급자의 로컬 인스턴스는 업데이트 번들을 설치할 때 업데이트됩니다.  

컴퓨터에서 SMS 공급자를 제거한 후에 다시 설치할 경우 해당 컴퓨터에서 SMS 공급자의 업데이트를 다시 설치해야 합니다.  

###  <a name="BKMK_clients"></a> 클라이언트 업데이트  
Configuration Manager 클라이언트에 대한 업데이트가 포함된 업데이트를 설치할 때 업데이트 설치를 사용하여 클라이언트를 자동으로 업그레이드하거나 나중에 클라이언트를 수동으로 업그레이드하는 옵션이 제공됩니다. 자동 클라이언트 업그레이드에 대한 자세한 내용은 [How to upgrade clients for Windows computers](https://technet.microsoft.com/library/mt627885.aspx)를 업데이트하는 핫픽스를 설치하는 방법에 대한 일반적인 지침을 제공합니다.  

Updates Publisher 또는 소프트웨어 배포 패키지를 사용하여 업데이트를 배포하거나 각 클라이언트에 수동으로 업데이트를 설치하도록 선택할 수 있습니다. 배포를 사용하여 업데이트를 설치하는 방법에 대한 자세한 내용은 이 항목의 [Configuration Manager에 대한 업데이트 배포](#BKMK_Deploy) 섹션을 참조하세요.  

> [!IMPORTANT]  
> 클라이언트에 대한 업데이트를 설치하는 경우 업데이트 번들에 서버에 대한 업데이트가 포함되어 있으면 클라이언트가 할당된 기본 사이트에서 서버 업데이트도 설치해야 합니다.  

클라이언트 업데이트를 수동으로 설치하려면 각 Configuration Manager 클라이언트에서 **Msiexec.exe**를 실행하고 플랫폼별 클라이언트 업데이트인 .msp 파일을 참조해야 합니다.  

예를 들어 클라이언트 업데이트에 다음 명령줄을 사용할 수 있습니다. 이 명령줄은 클라이언트 컴퓨터에서 MSIEXEC를 실행하고 업데이트 번들이 사이트 서버에 추출한 .msp 파일을 참조합니다. **msiexec.exe /p \\\\&lt;서버 이름\>\SMS_&lt;사이트 코드\>\Hotfix\\&lt;KB 번호\>\Client\\&lt;플랫폼\>\\&lt;msp\> /L\*v &lt;로그 파일\>REINSTALLMODE=mous REINSTALL=ALL**  

###  <a name="BKMK_console"></a> Configuration Manager 콘솔 업데이트  
Configuration Manager 콘솔을 업데이트하려면 콘솔 설치가 완료된 후에 콘솔이 실행되는 컴퓨터에서 업데이트를 설치해야 합니다.  

> [!IMPORTANT]  
> Configuration Manager 콘솔에 대한 업데이트를 설치하는 경우 업데이트 번들에 서버에 대한 업데이트가 포함되어 있으면 Configuration Manager 콘솔과 같은 구성 요소에 업데이트를 설치할 수 있습니다.  

업데이트하는 컴퓨터에서 Configuration Manager 클라이언트를 실행하는 경우:  

- 배포를 사용하여 업데이트를 설치할 수 있습니다. 배포를 사용하여 업데이트를 설치하는 방법에 대한 자세한 내용은 이 항목의 [Configuration Manager에 대한 업데이트 배포](#BKMK_Deploy) 섹션을 참조하세요.  

- 클라이언트 컴퓨터에 직접 로그온한 경우 설치를 대화형으로 실행할 수 있습니다.  

- 각 컴퓨터에서 수동으로 업데이트를 설치할 수 있습니다. Configuration Manager 콘솔 업데이트를 수동으로 설치하기 위해 Configuration Manager 콘솔이 실행되는 각 컴퓨터에서 Msiexec.exe를 실행하고 Configuration Manager 콘솔 업데이트 .msp 파일을 참조할 수 있습니다.  

예를 들어 Configuration Manager 콘솔을 업데이트하기 위해 다음 명령줄을 사용할 수 있습니다. 이 명령줄은 컴퓨터에서 MSIEXEC를 실행하고 업데이트 번들이 사이트 서버에 추출한 .msp 파일을 참조합니다. **msiexec.exe /p \\\\&lt;서버 이름\>\SMS_&lt;사이트 코드\>\Hotfix\\&lt;KB 번호\>\AdminConsole\\&lt;플랫폼\>\\&lt;msp\> /L\*v &lt;로그 파일\>REINSTALLMODE=mous REINSTALL=ALL**  

##  <a name="BKMK_Deploy"></a> Configuration Manager에 대한 업데이트 배포  
사이트 서버에 업데이트 번들을 설치한 후에는 다음 세 가지 방법 중 하나를 사용하여 추가 컴퓨터에 업데이트를 배포할 수 있습니다.  

###  <a name="BKMK_DeploySCUP"></a> Updates Publisher 2011을 사용하여 업데이트 설치  
사이트 서버에 업데이트 번들을 설치하면 설치 마법사에서 Updates Publisher용 카탈로그 파일을 생성하며, 이를 사용하여 해당 컴퓨터에 업데이트를 배포할 수 있습니다. 마법사는 사용자가 **패키지와 프로그램을 사용하여 이 업데이트 배포**를 업데이트하는 핫픽스를 설치하는 방법에 대한 일반적인 지침을 제공합니다.  

Updates Publisher의 카탈로그는 **SCUPCatalog.cab**로 이름이 지정되며 업데이트 번들이 실행되는 컴퓨터의 다음 위치에 있습니다. **\\\\&lt;ServerName\>\SMS_&lt;SiteCode\>\Hotfix\\&lt;KB Number\>\SCUP\SCUPCatalog.cab**  

> [!IMPORTANT]  
> SCUPCatalog.cab 파일은 업데이트 번들이 설치되는 사이트 서버에 해당하는 경로를 사용하여 만들어지므로 다른 사이트 서버에서는 사용할 수 없습니다.  

마법사가 완료되면 카탈로그를 Updates Publisher로 가져온 후 Configuration Manager 소프트웨어 업데이트를 사용하여 업데이트를 배포할 수 있습니다. Updates Publisher에 대한 자세한 내용은 System Center 2012의 TechNet 라이브러리에서 [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkID=83449)을 참조하세요.  

SCUPCatalog.cab 파일을 Updates Publisher로 가져와서 업데이트를 게시하려면 다음 절차를 따르세요.  

##### <a name="to-import-the-updates-to-updates-publisher-2011"></a>Updates Publisher 2011로 업데이트를 가져오려면  

1.  Updates Publisher 콘솔을 시작하고 **가져오기**를 클릭합니다.  

2.  소프트웨어 업데이트 카탈로그 가져오기 마법사의 **가져오기 형식** 페이지에서 **가져올 카탈로그의 경로 지정**을 선택하고 SCUPCatalog.cab 파일을 지정합니다.  

3.  **다음**을 클릭한 후에 다시 **다음** 을 클릭합니다.  

4.  **보안 경고 - 카탈로그 유효성 검사** 대화 상자에서 **적용**을 클릭합니다. 완료되면 마법사를 닫습니다.  

5.  Updates Publisher 콘솔에서 배포할 업데이트를 선택한 다음 **게시**를 클릭합니다.  

6.  소프트웨어 업데이트 게시 마법사의 **게시 옵션** 페이지에서 **전체 콘텐츠**를 선택하고 **다음**을 클릭합니다.  

7.  마법사를 완료하여 업데이트를 게시합니다.  

###  <a name="BKMK_DeploySWDist"></a> 소프트웨어 배포를 사용하여 업데이트 설치  
기본 사이트 또는 중앙 관리 사이트의 사이트 서버에 업데이트 번들을 설치할 때 설치 소프트웨어 배포에 대한 업데이트 패키지를 만들도록 마법사를 구성할 수 있습니다. 그런 다음 각 패키지를 업데이트할 컴퓨터 컬렉션에 배포할 수 있습니다.  

소프트웨어 배포 패키지를 만들려면 마법사의 **소프트웨어 업데이트 배포 구성** 페이지에서 업데이트할 각 업데이트 패키지 유형의 확인란을 선택합니다. 사용 가능한 유형으로는 서버, Configuration Manager 콘솔, 클라이언트 등이 있습니다. 선택한 각 업데이트 유형에 대해 별도의 패키지가 만들어집니다.  

> [!NOTE]  
> 서버용 패키지에는 다음 구성 요소에 대한 업데이트가 포함되어 있습니다.  
>   
> - 사이트 서버  
> - 사이트 데이터베이스  
> - 사이트 데이터베이스  

다음으로, 마법사의 **소프트웨어 업데이트 배포 방법 구성** 페이지에서 **소프트웨어 배포를 사용합니다**옵션을 선택합니다. 이 옵션을 선택하면 마법사가 소프트웨어 배포 패키지를 만듭니다.  

마법사가 완료된 후에는 Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에 있는 **패키지** 노드에서 만들어진 패키지를 확인할 수 있습니다. 그런 다음 표준 프로세스를 사용하여 소프트웨어 패키지를 Configuration Manager 클라이언트에 배포할 수 있습니다. 패키지는 클라이언트에서 실행될 때 클라이언트 컴퓨터에서 해당 Configuration Manager 구성 요소에 업데이트를 설치합니다.  

Configuration Manager 클라이언트에 패키지를 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 패키지 및 프로그램](../../../apps/deploy-use/packages-and-programs.md)을 참조하세요.  

###  <a name="BKMK_DeployCollections"></a> Configuration Manager에 업데이트를 배포하기 위한 컬렉션 만들기  
특정 업데이트를 해당 클라이언트에 배포할 수 있습니다. 다음 표에는 Configuration Manager의 여러 구성 요소를 위한 디바이스 컬렉션을 만드는 방법이 나와 있습니다.  

|Configuration Manager의 구성 요소|지침|  
|----------------------------------------|------------------|  
|중앙 관리 사이트 서버|직접 멤버 자격 쿼리를 만들고 중앙 관리 사이트 서버 컴퓨터를 추가합니다.|  
|모든 기본 사이트 서버|직접 멤버 자격 쿼리를 만들고 각 기본 사이트 서버 컴퓨터를 추가합니다.|  
|모든 보조 사이트 서버|직접 멤버 자격 쿼리를 만들고 각 보조 사이트 서버 컴퓨터를 추가합니다.|  
|모든 x86 클라이언트|다음 쿼리 조건을 사용하여 컬렉션을 만듭니다.<br /><br /> **Select \* from SMS_R_System inner join SMS_G_System_SYSTEM on SMS_G_System_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_SYSTEM.SystemType = "X86-based PC"**|  
|모든 x64 클라이언트|다음 쿼리 조건을 사용하여 컬렉션을 만듭니다.<br /><br /> **Select \* from SMS_R_System inner join SMS_G_System_SYSTEM on SMS_G_System_SYSTEM.ResourceID = SMS_R_System.ResourceId where SMS_G_System_SYSTEM.SystemType = "X64-based PC"**|  
|Configuration Manager 콘솔을 실행하는 모든 컴퓨터|직접 멤버 자격 쿼리를 만들고 각 컴퓨터를 추가합니다.|  
|SMS 공급자 인스턴스를 실행하는 원격 컴퓨터|직접 멤버 자격 쿼리를 만들고 각 컴퓨터를 추가합니다.|  

> [!NOTE]  
> 사이트 데이터베이스를 업데이트하려면 해당 사이트의 사이트 서버에 업데이트를 배포합니다.  

컬렉션을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../../core/clients/manage/collections/create-collections.md)을 참조하세요.  
