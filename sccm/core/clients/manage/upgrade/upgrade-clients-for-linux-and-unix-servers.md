---
title: Linux 및 UNIX 클라이언트 업그레이드
titleSuffix: Configuration Manager
description: Configuration Manager에서 Linux 또는 UNIX 서버의 클라이언트를 업그레이드합니다.
ms.date: 03/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 7d2bb377-1005-4a55-bd1f-b80a6d0b22e1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 987014084626e13b09a3c39fe6eff08ecc8fbe6b
ms.sourcegitcommit: d8d142044586a53709b4478ad945f714737c8d6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58523999"
---
# <a name="how-to-upgrade-clients-for-linux-and-unix-servers-in-configuration-manager"></a>Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 업그레이드하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Important]  
> 버전 1902부터 Configuration Manager는 Linux 또는 UNIX 클라이언트를 지원하지 않습니다. 
> 
> 따라서 Linux 서버를 관리하려면 Microsoft Azure 관리를 고려해야 합니다. Azure 솔루션은 대부분의 경우 Linux용 엔드투엔드 패치 관리를 포함하여 Configuration Manager 기능을 능가하는 광범위한 Linux 지원을 제공합니다.

현재 클라이언트를 먼저 제거하지 않고 컴퓨터의 Linux 및 UNIX용 클라이언트 버전을 최신 클라이언트 버전으로 업그레이드할 수 있습니다. 이렇게 하려면 **-keepdb** 명령줄 속성을 사용하여 컴퓨터에 새 클라이언트 설치 패키지를 설치합니다. Linux 및 UNIX용 클라이언트를 설치하면 기존 클라이언트 데이터를 새 클라이언트 파일로 덮어씁니다. 그러나 **–keepdb** 명령줄 속성을 사용하면 설치 프로세스에서 클라이언트 고유 식별자(GUID), 정보의 로컬 데이터베이스 및 인증서 저장소가 유지되고 새 클라이언트 설치에 사용됩니다.  

 예를 들어 Linux 및 UNIX용 Configuration Manager 클라이언트의 원래 릴리스에 있는 클라이언트를 실행하는 RHEL5 x64 컴퓨터가 있습니다. 이 클라이언트를 누적 업데이트 1의 클라이언트 버전으로 업그레이드하려면 **–keepdb** 명령줄 스위치를 추가해서 수동으로 **install** 스크립트를 실행하여 누적 업데이트 1의 해당 클라이언트 패키지를 설치합니다. 다음 예제 명령줄을 참조하세요.  

`./install -mp <hostname\> -sitecode <code\> -keepdb ccm-Universal-x64.<build\>.tar`  



## <a name="how-to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>소프트웨어 배포를 사용하여 Linux 및 UNIX 서버의 클라이언트를 업그레이드하는 방법  
 소프트웨어 배포를 사용하여 Linux 및 UNIX용 클라이언트를 새 클라이언트 버전으로 업그레이드할 수 있습니다. 그러나 Configuration Manager 클라이언트는 설치 스크립트를 바로 실행하여 새 클라이언트를 설치할 수 없습니다. 새 클라이언트를 설치하려면 현재 클라이언트를 먼저 제거해야 합니다. 이 작업을 수행하면 새 클라이언트의 설치를 시작하기 전에 설치 스크립트를 실행하는 Configuration Manager 클라이언트 프로세스가 종료됩니다. 소프트웨어 배포를 사용하여 새 클라이언트를 설치하려면 이후 시간에 시작되고 운영 체제의 기본 제공 일정 기능에 의해 실행되도록 설치를 예약해야 합니다.  

 소프트웨어 배포를 사용하여 새 클라이언트 설치 패키지의 파일을 먼저 클라이언트 컴퓨터에 복사합니다. 그런 다음, 스크립트를 배포 및 실행하여 클라이언트 설치 프로세스를 예약합니다. 스크립트는 운영 체제의 기본 제공 **at** 명령을 사용하여 시작을 지연합니다. 스크립트를 실행할 때 해당 작업은 컴퓨터의 Configuration Manager 클라이언트가 아니라 클라이언트 운영 체제에 의해 관리됩니다. 이 동작으로 인해 스크립트에서 호출된 명령줄이 먼저 Configuration Manager 클라이언트를 제거한 다음, 새 클라이언트를 설치할 수 있습니다. 이러한 작업은 Linux 또는 UNIX 컴퓨터에서 클라이언트 업그레이드 프로세스를 완료합니다. 업그레이드를 완료한 후 업그레이드된 클라이언트는 계속 Configuration Manager에 의해 관리됩니다.  

 Linux 및 UNIX용 클라이언트를 업그레이드하도록 소프트웨어 배포를 구성하려면 다음 절차를 참조하세요. 다음 단계 및 예제에서는 클라이언트의 초기 릴리스를 실행하는 RHEL5 x64 컴퓨터를 누적 업데이트 1 클라이언트 버전으로 업그레이드합니다.  

#### <a name="to-use-a-software-deployment-to-upgrade-the-client-on-linux-and-unix-servers"></a>소프트웨어 배포를 사용하여 Linux 및 UNIX 서버의 클라이언트를 업그레이드하려면  

1. 업그레이드할 Configuration Manager 클라이언트를 실행하는 컴퓨터에 새 클라이언트 설치 패키지를 복사합니다.  

    예를 들어 누적 업데이트 1에 대한 클라이언트 설치 패키지 및 설치 스크립트를 클라이언트 컴퓨터의 다음 위치에 배치합니다. **/tmp/PATCH**  

2. Configuration Manager 클라이언트의 업그레이드를 관리하는 스크립트를 만듭니다. 그런 다음, 클라이언트 컴퓨터에서 1단계의 클라이언트 설치 파일과 동일한 폴더에 스크립트 복사본을 저장합니다.  

    스크립트에는 특정 이름이 필요하지 않습니다. 클라이언트 컴퓨터의 로컬 폴더에 있는 클라이언트 설치 파일을 사용하고 **–keepdb** 명령줄 속성을 통해 클라이언트 설치 패키지를 설치하는 명령줄이 포함되어야 합니다. **-keepdb** 명령줄 속성을 사용하여 설치하는 새 클라이언트에서 사용할 현재 클라이언트의 고유 식별자를 유지 관리합니다.  

    예를 들어, 다음 줄을 포함하는 **upgrade.sh**라고 명명된 스크립트를 만듭니다.  

   ```  
   #!/bin/sh  
   #  
   /tmp/PATCH/install -sitecode <code> -mp <hostname> -keepdb /tmp/PATCH/ccm-Universal-x64.<build>.tar  

   ```  

    그런 다음, 클라이언트 컴퓨터의 **/tmp/PATCH** 폴더로 복사합니다.

3. 소프트웨어 배포를 사용하여 각 클라이언트가 기본 제공 **at** 명령을 통해 **upgrade.sh** 스크립트를 실행하도록 합니다. 스크립트가 실행되기 전에 약간의 지연이 있습니다.  

    예를 들어 다음 명령줄을 사용하여 스크립트를 실행합니다. **at -f /tmp/upgrade.sh -m now + 5 minutes**  

   클라이언트에서 **upgrade.sh** 실행을 예약한 후 소프트웨어 배포가 완료되었음을 나타내는 상태 메시지를 전송합니다. 그러나 실제 클라이언트 설치는 지연 후 컴퓨터에서 관리됩니다. 클라이언트 업그레이드를 완료한 후 클라이언트 컴퓨터의 **/var/opt/microsoft/scxcm.log** 파일을 검토하여 설치 유효성을 검사합니다. Configuration Manager 콘솔의 **자산 및 준수** 작업 영역의 **디바이스** 노드에서 클라이언트에 대한 세부 정보를 통해 클라이언트가 설치되고 사이트와 통신하고 있는지 확인합니다.  
