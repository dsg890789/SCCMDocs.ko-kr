---
title: "System Center Configuration Manager용 Technical Preview 1511의 기능 | Microsoft 문서"
description: "System Center Configuration Manager용 Technical Preview 버전 1511에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 69473706-21b3-498b-a67e-670fdc988f0d
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 3bf44f850722afdb8dfe5922c8ceff11c9b56d08
ms.openlocfilehash: 8ef43a2f10a7ef1cbb101f6737c606c72ccdce4f

---
# <a name="capabilities-in-technical-preview-1511-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1511의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1511에서 사용 가능한 기능을 소개합니다. 이 버전은 새 Technical Preview 사이트를 설치하거나 이전 버전의 Technical Preview에서 업그레이드하는 데 사용할 수 있는 Technical Preview의 기준선 설치입니다.   이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.  

다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.  

##  <a name="a-namebkmkwufba-integration-with-windows-update-for-business-in-windows-10"></a><a name="BKMK_WUfB"></a> Windows 10에서 비즈니스용 Windows 업데이트와 통합  
 Configuration Manager에서는 WUfB(비즈니스용 Windows 업데이트)를 통해 직접 연결된 Windows 10 컴퓨터와 Windows 10 업데이트 및 업그레이드를 다운로드하기 위해 WSUS에 연결된 컴퓨터를 구별할 수 있습니다.  WUfB를 통해 연결된 컴퓨터의 경우 업데이트와 업그레이드는 관리자가 그룹 정책 또는 MDM 정책을 통해 설정하는 빈도로 관리할 수 있으며, 이러한 업데이트/업그레이드를 WUfB에서 직접 설치할 수 있습니다.    
WUfB를 통해 연결된 컴퓨터의 경우 Configuration Manager에서 준수 상태를 보고할 수 없습니다(Windows 업데이트 또는 정의 업데이트 포함). 또한 Configuration Manager에서는 이러한 컴퓨터에 Microsoft 업데이트 또는 타사 업데이트를 배포할 수 없습니다.  

 **이 시나리오에 대한 필수 조건:**  

-   Windows 10 Desktop Pro 또는 Windows 10 Enterprise Edition 버전 1511 이상  

-   [비즈니스용 Windows 업데이트](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx)를 통해 관리할 컴퓨터  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

1.  이전에 설정된 경우 Windows 업데이트 에이전트를 사용하지 않도록 설정하여 WSUS에 대한 검사가 이루어지지 않도록 합니다.   
    컴퓨터가 WSUS에 대해 검사하는지 아니면 Windows 업데이트에 대해 검사하는지 나타내도록 레지스트리 키 **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\useWSUSServer** 를 설정할 수 있습니다.  값이 2이면 WSUS에 대해 검사되지 않는 것입니다.  

2.  Configuration Manager 리소스 탐색기에서 **Windows 업데이트**노드 아래에 새 특성 **UseWUServer** 가 나옵니다.  

3.  업데이트 및 업그레이드를 위해 WUfB를 통해 연결된 모든 컴퓨터에 대해 **UseWUServer** 특성을 기반으로 컬렉션을 만듭니다.  

4.  소프트웨어 업데이트 워크플로를 사용하지 않도록 클라이언트 에이전트 설정을 만들고 이 설정을 WUfB에 직접 연결된 컴퓨터 컬렉션에 배포합니다.  

5.  WUfB를 통해 관리하는 컴퓨터에서 준수 상태가 **알 수 없음** 으로 표시되며, 해당 컴퓨터는 전체 준수 비율의 일부로 계산되지 않습니다.  

##  <a name="a-namebkmkoffice365proplusa-managing-office-365-proplus-client-update-through-system-center-configuration-manager"></a><a name="BKMK_Office365ProPlus"></a> System Center Configuration Manager를 통해 Office 365 ProPlus 클라이언트 업데이트 관리  
 이제 Configuration Manager에서는 Configuration Manager 소프트웨어 업데이트 관리 워크플로를 사용하여 Office 365 데스크톱 클라이언트 업데이트를 관리할 수 있습니다.    
Microsoft가 WSUS(Windows Server Updates Services)를 위한 새로운 Office 365 데스크톱 클라이언트 업데이트를 게시하면 카탈로그 동기화의 일부로 Office 365 업데이트가 구성된 경우 Configuration Manager에서 업데이트를 카탈로그에 동기화할 수 있습니다.  Configuration Manager 사이트 서버에서 Office 365 클라이언트 업데이트를 다운로드하고 패키지를 Configuration Manager 배포 지점에 배포합니다.  그러면 Configuration Manager 클라이언트에서 업데이트를 가져올 위치와 업데이트 설치 프로세스를 시작할 시기를 Office 365 데스크톱 클라이언트에 알립니다.  

**이 시나리오에 대한 필수 조건:**  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

1.  Configuration Manager 사이트 서버에 대한 Office 365 업데이트를 동기화하고 이를 Configuration Manager 콘솔에서 볼 수 있습니다.  

2.  Office 365 업데이트를 성공적으로 승인하고 배포할 수 있습니다.  

3.  Office 365 업데이트를 성공적으로 클라이언트에 다운로드할 수 있습니다.  

4.  콘솔 내 모니터링이나 보고서를 사용하여 Office 365 업데이트의 준수를 확인할 수 있습니다.  

 자세한 내용은 [System Center Configuration Manager Technical Preview로 Office 365 클라이언트 업데이트 관리](https://technet.microsoft.com/library/mt628083.aspx)를 참조하세요.  

##  <a name="a-namebkmkalwasyona-support-for-sql-server-alwayson-for-highly-available-databases"></a><a name="BKMK_AlwasyOn"></a> 항상 사용 가능한 데이터베이스에 대한 SQL Server AlwaysOn 지원  
 Configuration Manager에서는 이제 SQL Server AlwaysOn 가용성 그룹을 사용하여 사이트 데이터베이스를 호스트할 수 있습니다.  새 사이트를 설치할 때 설치 프로그램이 SQL Server의 일반 인스턴스가 아닌 가용성 그룹을 사용하도록 지정할 수 있습니다.  

> [!NOTE]  
>  가용성 그룹을 올바르게 구성하고 사용하려면 SQL Server 가용성 그룹 구성 방법을 잘 알고 있어야 하며, SQL Server 문서 라이브러리에서 제공되는 문서와 절차를 참조해야 합니다.  

가용성 그룹을 구성하고 만드는 대략적인 프로세스는 다음과 같습니다.  

1.  SQL Server의 가용성 그룹을 구성합니다.  

2.  새 Configuration Manager 사이트를 설치하고, 설치 중에 그룹 끝점을 지정하여 사이트에서 가용성 그룹을 사용하도록 지정합니다.  

**이 시나리오에 대한 필수 조건:**  

-   Configuration Manager 기술 미리 보기에서 지원하는 SQL Server 버전이 있어야 합니다.  

-   Configuration Manager를 설치하기 전에 SQL Server 가용성 그룹을 만들고 구성해야 합니다.  

-   가용성 그룹에는 주 복제본이 하나 있어야 하며 동기 보조 복제본이 2개까지 포함될 수 있습니다.  

-   가용성 그룹에는 끝점이 하나 이상 있어야 합니다.  

-   가용성 그룹의 각 SQL Server가 액세스할 수 있는 네트워크 위치가 있어야 합니다. 이 위치는 가용성 그룹을 구성할 때 설치 프로그램에서 사용하며, 설치 완료 후에 제거할 수 있습니다.  

**이 릴리스의 알려진 문제:**  

-   사이트 데이터베이스로 이미 사용 중인 가용성 그룹에는 새 복제본 구성원을 추가할 수 없습니다. 대신 새 복제 구성원을 추가한 후 사이트를 다시 설치해야 합니다.  

-   이 시나리오를 수행하려면 관리 지점 서버에 **SQL Server 2012 기능 팩** 의[SQL Server 2012 Native Client](http://www.microsoft.com/download/details.aspx?id=29065)를 설치해야 할 수 있습니다. 이렇게 하면 관리 지점 서버의 **mp_getauth.log** 에 기록되는 SQL 연결 오류를 방지할 수 있습니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

-   SQL AlwaysOn 가용성 그룹에 대해 구성된 데이터베이스 서버를 사용하는 기본 사이트를 설치할 수 있습니다.  

-   기본 사이트가 계속 작동하는 상태를 유지하면서 SQL AlwaysOn 가용성 그룹을 그룹 내의 새 복제본으로 장애 조치(failover)할 수 있습니다.  

### <a name="configuring-sql-server-alwayson-for-configuration-manager"></a>Configuration Manager용으로 SQL Server AlwaysOn 구성  
 다음 절차에 따라 먼저 가용성 그룹을 만들고 구성한 다음 해당 가용성 그룹을 사용하는 새 Configuration Manager 사이트를 설치합니다.  

#### <a name="to-create-a-sql-server-alwayson-availability-group"></a>SQL Server AlwaysOn 가용성 그룹을 만들려면  
[SQL Server 가용성 그룹 만들기](https://technet.microsoft.com/library/ff878265\(v=sql.120\).aspx) 프로세스는 SQL Server 문서 라이브러리에 설명되어 있습니다.  가용성 그룹을 만들 때는 Configuration Manager와 함께 가용성 그룹을 사용하기 위한 다음 요구 사항을 충족하는지 확인합니다.  

-   최대 3개 구성원:  

    -   주 복제본 1개/보조 복제본 최대 2개  

    -   보조 복제본은 동기 복제본이어야 함  

        > [!TIP]  
        >  보조 복제본은 읽기 전용으로 구성하는 것이 좋습니다. 이렇게 하면 사이트 작업을 위해 주 복제본의 성능은 유지하면서 보조 복제본을 보고 등의 기능에 사용할 수 있습니다.  

-   끝점 하나 이상. Configuration Manager 사이트를 설치할 때 이 끝점의 가상 이름을 사용합니다.  

    > [!TIP]  
    >  그룹 하나에 끝점을 여러 개 포함할 수는 있지만 Configuration Manager에서는 끝점을 하나만 사용합니다.  

#### <a name="to-install-a-configuration-manager-site-that-uses-the-availability-group"></a>가용성 그룹을 사용하는 Configuration Manager 사이트를 설치하려면  
SQL Server 가용성 그룹을 사용하는 사이트를 설치하려면 다음을 수행합니다.  

1.  Configuration Manager 설치 프로그램에 표시될 때 다음 항목을 바꿉니다.  

    -   **SQL Server 이름**: 가용성 그룹을 만들 때 구성한 끝점의 가상 이름을 입력합니다. 가상 이름은 **&lt;endpointServer\>.fabrikam.com**과 같은 전체 DNS 이름이어야 합니다.  

    -   **인스턴스**: 이 값은 비워 두어야 합니다. 이 구성에는 인스턴스가 없습니다.  

    -   **데이터베이스**: 가용성 그룹의 주 복제본에 만든 데이터베이스의 이름을 입력합니다.  

2.  다음으로 그룹의 각 SQL Server가 액세스할 수 있는 네트워크 위치를 입력해야 합니다.  

    -   각 SQL Server의 컴퓨터 계정과 서비스 계정에는 이 위치에 대한 모든 권한이 있어야 합니다.  

    -   이 위치는 설치 중에만 사용되며 설치가 완료되고 사이트가 설치된 후에는 공유하지 않거나 삭제할 수 있습니다.  

3.  이 정보를 입력한 후 일반적인 프로세스와 구성을 사용하여 설치를 완료합니다.  

##  <a name="a-namebkmkclusterserverupdatesa-service-a--server-cluster"></a><a name="BKMK_ClusterServerUpdates"></a> 서버 클러스터 서비스  
이제는 클러스터의 서버를 포함하는 컬렉션을 만든 다음 클러스터에 업데이트를 배포할 때 사용할 클러스터 설정을 구성할 수 있습니다. 지정된 시간에 온라인 상태인 서버의 백분율을 제어할 수 있으며 사용자 지정 작업을 실행하도록 배포 전/배포 후 PowerShell 스크립트를 구성할 수도 있습니다.  

**이 릴리스의 알려진 문제:**  

-   보고를 사용하여 클러스터 서버에 대해 소프트웨어 업데이트 배포 상태를 확인할 수 없습니다.  

-   **클러스터 설정** 페이지의 유지 관리 순서 옵션이 사용하지 않도록 설정되며 이 릴리스에서는 제공되지 않습니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

-   서버 클러스터를 나타내는 컬렉션을 만들 수 있습니다. 이 테스트를 위해 이 컬렉션의 컴퓨터 2대를 포함하도록 구성원 자격 수집 규칙을 구성할 수 있습니다.  

-   클러스터 서비스 과정의 모든 지점에서 클러스터 내 서버 중 50%만 오프라인 상태일 수 있도록 지정할 수 있습니다. 배포 전/배포 후 스크립트를 지정하려면 아래 절차의 샘플 스크립트를 사용합니다.  

-   이 컬렉션에 대해 업데이트를 배포할 수 있습니다. C:\temp의 start.txt 및 end.txt 파일을 검토하여 클러스터 내 서버의 배포 시작 시간과 종료 시간을 확인합니다. 자세한 내용은 UpdatesDeployment.log 파일을 검토하세요.  

#### <a name="to-create-a-collection-for-a-server-cluster"></a>서버 클러스터의 컬렉션을 만들려면  

1.  클러스터의 서버를 포함하는 [장치 컬렉션을 만듭니다](https://technet.microsoft.com/library/gg712295.aspx).  

2.  **자산 및 준수** 작업 영역에서 **장치 컬렉션**을 클릭하고 클러스터의 서버를 포함하는 컬렉션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  

3.  **일반** 탭에서 **모든 장치가 동일한 서버 클러스터에 속함**을 선택한 다음 **설정**을 클릭합니다.  

4.  **클러스터 설정** 페이지에서 소프트웨어 업데이트를 설치하는 동시에 오프라인 상태로 만들 수 있는 서버의 백분율을 선택합니다. 하나의 클러스터 서버는 제공하는 백분율에 상관없이 한 번에 오프라인 상태로 만들 수 있습니다. 한 번에 처리하는 서버 수를 선택할 때 Configuration Manager에서 끝수를 잘라 버립니다. 예를 들어 51%를 선택했는데 클러스터에 4개의 서버가 있으면 2개의 서버가 동시에 오프라인 상태가 됩니다.  

5.  배포 전(노드 드레이닝) 또는 배포 후(노드 다시 시작) 스크립트 사용 여부를 지정합니다.  

    > [!TIP]  
    >  다음은 텍스트 파일에 현재 시간을 작성하는 배포 전/배포 후 스크립트를 테스트하는 데 사용할 수 있는 예제입니다.  
    >   
    >  **배포 전**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **배포 후**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-cluster"></a>서버 클러스터에 소프트웨어 업데이트를 배포하려면  

1.  서버 클러스터 컬렉션에 [소프트웨어 업데이트를 배포](https://technet.microsoft.com/library/gg712304.aspx)합니다.  

2.  [소프트웨어 업데이트 배포를 모니터링](https://technet.microsoft.com/library/gg712304.aspx)합니다.  



<!--HONumber=Dec16_HO3-->


