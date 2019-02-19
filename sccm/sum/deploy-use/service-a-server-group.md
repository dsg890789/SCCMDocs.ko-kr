---
title: 서버 그룹 제공
titleSuffix: Configuration Manager
description: System Center Configuration Manager 콘솔은 업데이트 및 준수를 모니터링하기 위해 경고 및 상태를 제공합니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 12/07/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 304a83ea-0f72-437d-9688-2e6e0c7526dd
ms.collection: M365-identity-device-management
ms.openlocfilehash: aac5c9d6c683447fe7dda50e6dcfd52b7024656d
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56131645"
---
# <a name="service-a-server-group"></a>서버 그룹 제공

*적용 대상: System Center Configuration Manager(현재 분기)*

>[!IMPORTANT]
>시험판 기능은 프로덕션 환경에서의 초기 테스트를 위해 현재 분기에 포함된 기능입니다. 이러한 기능은 완전하게 지원되지만 아직 개발 중인 상태이므로 시험판 범주에서 벗어날 때까지는 변경될 수 있습니다. 이 기능을 사용하려면 사용자가 설정해야 합니다. 자세한 내용은 [업데이트에서 시험판 기능 사용](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease)을 참조하세요.

System Center Configuration Manager 버전 1606부터, 컬렉션에 대한 서버 그룹 설정을 구성하여 소프트웨어 업데이트를 설치할 컬렉션의 컴퓨터 수, 백분율 또는 순서를 정의할 수 있습니다. 사용자 지정 작업을 실행하도록 배포 전/배포 후 PowerShell 스크립트를 구성할 수도 있습니다.

서버 그룹 설정이 구성되어 있는 컬렉션에 소프트웨어 업데이트를 배포하는 경우 Configuration Manager는 지정된 시간에 소프트웨어 업데이트를 설치할 수 있는 컬렉션의 컴퓨터 수를 확인하고 동일한 개수의 배포 잠금을 제공합니다. 배포 잠금을 얻은 컴퓨터만 소프트웨어 업데이트 설치를 시작합니다. 배포 잠금을 사용할 수 있는 경우 컴퓨터가 배포 잠금을 얻고 소프트웨어 업데이트를 설치한 다음 소프트웨어 업데이트 설치가 성공적으로 완료되면 배포 잠금을 제거합니다. 그러면 배포 잠금을 다른 컴퓨터에 사용할 수 있습니다. 컴퓨터에서 배포 잠금을 제거할 수 없는 경우 컬렉션에 대한 모든 서버 그룹 배포 잠금을 수동으로 제거할 수 있습니다.

>[!IMPORTANT]
>컬렉션에 있는 모든 컴퓨터를 동일한 사이트에 할당해야 합니다.

#### <a name="to-create-a-collection-for-a-server-group"></a>서버 그룹의 컬렉션을 만들려면  
서버 그룹 설정은 디바이스 컬렉션의 속성에서 구성됩니다. 서버 그룹을 제공하려면 컬렉션의 모든 구성원을 동일한 사이트에 할당해야 합니다. 컬렉션을 만들고 서버 그룹 설정을 구성하려면 다음 단계를 따르세요.
1.  서버 그룹의 컴퓨터를 포함하는 [디바이스 컬렉션을 만듭니다](../../core/clients/manage/collections/create-collections.md).  

2.  **자산 및 준수** 작업 영역에서 **디바이스 컬렉션**을 클릭하고 서버 그룹에서 컴퓨터를 포함하는 컬렉션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  

3.  **일반** 탭에서 **모든 디바이스가 동일한 서버 그룹에 속함**을 선택한 다음 **설정**을 클릭합니다.  

4.  **서버 그룹 설정** 페이지에서 다음 설정 중 하나를 지정합니다.  

    -   **일정 비율의 머신이 동시에 업데이트되도록 허용**: 특정 비율의 클라이언트만 한 번에 업데이트되도록 지정합니다. 예를 들어 컬렉션에 10개의 클라이언트가 있고 클라이언트의 30%를 동시에 업데이트하도록 컬렉션을 구성하는 경우에는 지정된 시간에 3개의 클라이언트만 소프트웨어 업데이트를 설치합니다.  

    -   **여러 머신이 동시에 업데이트되도록 허용**: 특정 수의 클라이언트만 한 번에 업데이트되도록 지정합니다.  

    -   **유지 관리 순서 지정**: 컬렉션의 클라이언트가 구성한 순서대로 한 번에 하나씩 업데이트되도록 지정합니다. 클라이언트는 목록에서 앞의 클라이언트가 해당 소프트웨어 업데이트 설치를 완료하고 난 다음에야 소프트웨어 업데이트를 설치합니다.  

5.  배포 전(노드 드레이닝) 또는 배포 후(노드 다시 시작) 스크립트 사용 여부를 지정합니다.  

    > [!WARNING]
    > 사용자 지정 스크립트는 Microsoft에서 서명하지 않은 스크립트입니다. 이러한 스크립트의 무결성을 유지하는 것은 사용자의 책임입니다.

    > [!TIP]  
    > 다음은 텍스트 파일에 현재 시간을 작성하는 배포 전/배포 후 스크립트를 테스트하는 데 사용할 수 있는 예제입니다.  
    >   
    >  **배포 전**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\Windows\Temp\start.txt`  
    >   
    >  **배포 후**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\Windows\Temp\end.txt`  

## <a name="deploy-software-updates-to-the-server-group-and-monitor-status"></a>서버 그룹에 소프트웨어 업데이트 배포 및 상태 모니터링  
일반적인 배포 프로세스를 사용하여 서버 그룹 컬렉션에 소프트웨어 업데이트를 배포합니다. 소프트웨어 업데이트를 배포한 후 Configuration Manager 콘솔에서 소프트웨어 업데이트 배포를 모니터링할 수 있습니다.
1.  서버 그룹 컬렉션에 [소프트웨어 업데이트를 배포](manually-deploy-software-updates.md)합니다.   

2.  [소프트웨어 업데이트 배포를 모니터링](monitor-software-updates.md)합니다. 클라이언트가 소프트웨어 업데이트 설치 차례를 기다리고 있을 때 소프트웨어 업데이트 배포에 대한 표준 모니터링 보기 외에도 **잠금 대기 중** 상태가 표시됩니다. 자세한 내용은 UpdatesDeployment.log 파일을 검토하세요.


## <a name="clear-the-deployment-locks-for-computers-in-a-server-group"></a>서버 그룹의 컴퓨터에 대한 배포 잠금 제거  
컴퓨터에서 배포 잠금을 제거하지 못한 경우 컬렉션에 대한 모든 서버 그룹 배포 잠금을 수동으로 제거할 수 있습니다. 컬렉션의 컴퓨터를 업데이트하는 동안 배포가 중단되었으며 준수하지 않는 컴퓨터가 있는 경우에만 잠금을 제거합니다.  
1.  **자산 및 준수** 작업 영역에서 **디바이스 컬렉션**을 클릭하고 배포 잠금을 제거할 컬렉션을 클릭합니다.  

2.  **홈** 탭의 **배포** 그룹에서 **서버 그룹 배포 잠금 제거**를 클릭합니다. 클라이언트가 소프트웨어 업데이트를 설치하지 못한 경우와 다른 클라이언트가 해당 소프트웨어 업데이트를 설치하지 못하도록 하는 경우 배포 잠금을 수동으로 제거할 수 있습니다.  
