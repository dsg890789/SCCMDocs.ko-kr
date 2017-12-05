---
title: "인프라 수정"
titleSuffix: Configuration Manager
description: "배포한 Configuration Manager 인프라에 영향을 주는 작업이나 변경을 수행하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a7975dc8-46ab-4dae-86b6-dc3e3cf3b2f0
caps.latest.revision: "19"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 93456b2708afbdaac0ff3c68dc6c2d9927def7ad
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/04/2017
---
# <a name="modify-your-system-center-configuration-manager-infrastructure"></a>System Center Configuration Manager 인프라 수정

*적용 대상: System Center Configuration Manager(현재 분기)*

하나 이상의 사이트를 설치한 후 배포한 인프라에 영향을 주는 작업을 수행하거나 구성을 수정해야 할 수도 있습니다.  


##  <a name="BKMK_ManageSMSprovider"></a> SMS 공급자 관리  
 SMS 공급자(동적 연결 라이브러리 파일(smsprov.dll))는 하나 이상의 Configuration Manager 콘솔에 대한 관리 연결 지점을 제공합니다. 여러 SMS 공급자를 설치하면 사이트와 계층을 관리하는 연결 지점에 중복성을 구현할 수 있습니다.  

 각 Configuration Manager 사이트에서 설치 프로그램을 다시 실행하여 다음 작업을 수행할 수 있습니다.  

-   SMS 공급자 인스턴스 추가. SMS 공급자의 각 추가 인스턴스는 개별 컴퓨터에 있어야 합니다.  

-   SMS 공급자 인스턴스 제거. 사이트의 마지막 SMS 공급자를 제거하려면 사이트를 제거해야 합니다.  

 설치 프로그램을 실행하는 사이트 서버의 루트 폴더에서 **ConfigMgrSetup.log** 를 확인하여 SMS 공급자의 설치 또는 제거를 모니터링할 수 있습니다.  

 사이트에서 SMS 공급자를 수정하기 전에 [System Center Configuration Manager용 SMS 공급자에 대한 계획](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)의 정보를 숙지해 주세요.  

#### <a name="to-manage-the-sms-provider-configuration-for-a-site"></a>사이트의 SMS 공급자 구성을 관리하려면  

1.  **&lt;Configuration Manager 사이트 설치 폴더\>\BIN\X64\setup.exe**에서 **Configuration Manager 설치 프로그램**을 실행합니다.  

2.  **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 클릭하고 **다음**을 클릭합니다.  

3.  **사이트 유지 관리** 페이지에서 **SMS 공급자 구성 수정**을 선택하고 **다음**을 클릭합니다.  

4.  **SMS 공급자 관리** 페이지에서 다음 옵션 중 하나를 선택하고 다음 옵션 중 하나를 사용하여 마법사를 완료합니다.  

    -   이 사이트에서 SMS 공급자를 더 추가하려면:  

         **새 SMS 공급자 추가**를 선택하고 현재는 SMS 공급자를 호스팅하지 않지만 SMS 공급자를 호스팅할 컴퓨터의 FQDN을 지정한 후에 **다음**을 클릭합니다.  

    -   서버에서 SMS 공급자를 제거하려면:  

         **지정한 SMS 공급자 제거**를 선택하고 SMS 공급자를 제거할 컴퓨터의 이름을 선택한 후 **다음**을 클릭하고 작업을 확인합니다.  

        > [!TIP]  
        >  두 컴퓨터 간에 SMS 공급자를 이동하려면 SMS 공급자를 새 컴퓨터에 설치한 후에 원래 위치에서 SMS 공급자를 제거해야 합니다. 한 번의 프로세스로 두 컴퓨터 간에 SMS 공급자를 이동하는 전용 옵션은 없습니다.  

 설치 마법사가 완료된 후에는 SMS 공급자 구성이 완료됩니다. 사이트 **속성** 대화 상자의 **일반** 탭에서 사이트용 SMS 공급자가 설치된 컴퓨터를 확인할 수 있습니다.  

##  <a name="bkmk_Console"></a> Configuration Manager 콘솔 관리  
 다음은 Configuration Manager 콘솔 관리를 위해 수행할 수 있는 작업입니다.  

-   **Configuration Manager 콘솔에 표시되는 언어 수정** - 설치된 언어를 수정하려면 이 항목에서 [Configuration Manager 콘솔 언어 관리](#BKMK_ManageConsoleLanguages)를 참조하세요.  

-   **추가 콘솔 설치** - 추가 콘솔을 설치하려면 [System Center Configuration Manager 콘솔 설치](/sccm/core/servers/deploy/install/install-consoles)를 참조하세요.  

-   **DCOM 구성** - 사이트 서버의 원격 콘솔에서 연결할 수 있도록 하는 DCOM 권한을 구성하려면 이 항목에서 [원격 Configuration Manager 콘솔에 대한 DCOM 권한 구성](#BKMK_ConfigDCOMforRemoteConsole)을 참조하세요.  

-   **권한을 수정하여 관리자가 콘솔에서 볼 수 있는 사항 제한** - 관리 권한을 수정하여 사용자가 콘솔에서 보고 수행할 수 있는 사항을 제한하려면 [관리자의 관리 범위 수정](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_ModAdminUser)을 참조하세요.     

###  <a name="BKMK_ManageConsoleLanguages"></a> Configuration Manager 콘솔 언어 관리  
 사이트 서버 설치 중 Configuration Manager 콘솔 설치 파일 및 사이트에 대해 지원되는 언어 팩은 사이트 서버의 **&lt;Configuration Manager 설치 경로\>\Tools\ConsoleSetup** 하위 폴더에 복사됩니다.  

-   사이트 서버의 이 폴더에서 Configuration Manager 콘솔 설치를 시작하면 Configuration Manager 콘솔 및 지원되는 언어 팩 파일이 컴퓨터에 복사됩니다.  

-   이 언어 팩을 컴퓨터의 현재 언어 설정에 대해 사용할 수 있는 경우 Configuration Manager 콘솔은 해당 언어로 열립니다.  

-   관련 언어 팩을 Configuration Manager 콘솔에 대해 사용할 수 없는 경우 콘솔은 영어로 열립니다.  

예를 들어 영어, 독일어 및 프랑스어를 지원하는 사이트 서버에서 Configuration Manager 콘솔을 설치하는 시나리오를 가정해봅니다. 언어 설정이 프랑스어로 구성된 컴퓨터에서 Configuration Manager 콘솔을 열면 이 콘솔은 프랑스어로 열립니다. 언어 설정이 일본어로 구성된 컴퓨터에서 Configuration Manager 콘솔을 열면, 일본 언어 팩을 사용할 수 없으므로 이 콘솔은 영어로 열립니다.  

 Configuration Manager 콘솔이 열릴 때마다 컴퓨터에 구성된 언어 설정이 파악되고, 관련 언어 팩이 Configuration Manager 콘솔에 대해 사용 가능한지 여부가 확인된 다음 적절한 언어 팩을 사용하여 콘솔이 열립니다. Configuration Manager 콘솔을 컴퓨터에 구성된 언어 설정에 관계없이 영어로 열려고 할 경우 컴퓨터의 언어 팩 파일을 수동으로 제거하거나 파일 이름을 바꾸어야 합니다.  

 Configuration Manager 콘솔을 컴퓨터에 구성된 로캘 설정에 관계없이 영어로 시작하려면 다음 절차를 따르세요.  

##### <a name="to-install-an-english-only-version-of-the-configuration-manager-console-on-computers"></a>컴퓨터에 Configuration Manager 콘솔의 영어 단독 버전을 설치하려면  

1.  Windows 탐색기에서 **&lt;Configuration Manager 설치 경로\>\Tools\ConsoleSetup\LanguagePack**을 찾습니다.  

2.  **.msp** 및 **.mst** 파일의 이름을 바꿉니다. 예를 들어 **&lt;파일 이름\>.MSP**를 **&lt;파일 이름\>.MSP.disabled**로 변경합니다.  

3.  컴퓨터에 Configuration Manager 콘솔을 설치합니다.  

    > [!IMPORTANT]  
    >  사이트 서버에 대해 새 서버 언어가 구성되면 .msp 및 .mst 파일은 **LanguagePack** 폴더에 다시 복사되며, 사용자는 이 절차를 반복해 새 Configuration Manager 콘솔을 영어로만 설치해야 합니다.  

##### <a name="to-temporarily-disable-a-console-language-on-an-existing-configuration-manager-console-installation"></a>기존 Configuration Manager 콘솔 설치에서 일시적으로 콘솔 언어를 사용하지 않도록 설정하려면  

1.  Configuration Manager 콘솔을 실행하는 컴퓨터에서 Configuration Manager 콘솔을 닫습니다.  

2.  Configuration Manager 콘솔 컴퓨터의 Windows 탐색기에서 &lt;*Configuration Manager 설치 경로*>\Bin\을 찾습니다.  

3.  컴퓨터에 구성된 언어에 대한 해당 언어 폴더의 이름을 바꿉니다. 예를 들어 컴퓨터에 대한 언어 설정이 독일어로 설정된 경우 **de** 폴더의 이름을 **de.disabled**로 바꾸면 됩니다.  

4.  Configuration Manager 콘솔을 컴퓨터에 구성된 언어로 열려면 폴더의 이름을 원래 이름으로 바꾸세요. 예를 들어 **de.disabled** 폴더 이름을 **de**로 바꿉니다.  

##  <a name="BKMK_ConfigDCOMforRemoteConsole"></a> 원격 Configuration Manager 콘솔에 대한 DCOM 권한 구성  
 Configuration Manager 콘솔을 실행하는 사용자 계정에는 SMS 공급자를 사용하여 사이트 데이터베이스에 액세스하기 위한 권한이 필요합니다. 그러나 원격 Configuration Manager 콘솔을 사용하는 관리자에게는 다음에 대한 **원격 활성화** DCOM 권한이 필요합니다.  

-   사이트 서버 컴퓨터  

-   SMS 공급자 인스턴스를 호스트하는 각 컴퓨터  

 **SMS Admins** 라는 보안 그룹은 컴퓨터에서 SMS 공급자에 대한 액세스를 허용하며, 필요한 DCOM 권한을 부여하는 데에도 사용할 수 있습니다. 이 그룹은 SMS 공급자가 구성원 서버에서 실행될 때 컴퓨터에 대해 로컬이며, SMS 공급자가 도메인 컨트롤러에서 실행될 때 도메인 로컬 그룹입니다.  

> [!IMPORTANT]  
>  Configuration Manager 콘솔은 WMI(Windows Management Instrumentation)를 사용하여 SMS 공급자에 연결하며, WMI는 내부적으로 DCOM을 사용합니다. 따라서 Configuration Manager 콘솔이 SMS 공급자 컴퓨터 이외의 컴퓨터에서 실행되는 경우 Configuration Manager에 SMS 공급자 컴퓨터에서 DCOM 서버를 활성화하기 위한 권한이 필요합니다. 기본적으로 원격 활성화는 기본 제공 관리자 그룹의 구성원에게만 허용됩니다. SMS 관리자 그룹이 원격 활성화 권한을 갖도록 허용할 경우 이 그룹의 구성원이 SMS 공급자 컴퓨터에 대한 DCOM 공격을 시도할 수 있습니다. 또한 이 구성은 컴퓨터가 공격을 받을 수 있는 취약점을 늘립니다. 이러한 공격 위협을 완화하려면 SMS 관리자 그룹의 구성원을 주의 깊게 모니터링해야 합니다.  

 SMS 공급자가 설치되는 각 중앙 관리 사이트, 기본 사이트 서버 및 각 컴퓨터에서 관리자에 대한 원격 Configuration Manager 콘솔 액세스를 허용하려면 다음 절차를 따르세요.  

#### <a name="to-configure-dcom-permissions-for-remote-configuration-manager-console-connections"></a>원격 Configuration Manager 콘솔 연결에 대한 DCOM 권한을 구성하려면  

1.  **Dcomcnfg.exe** 를 실행하여 **구성 요소 서비스**를 엽니다.  

2.  **구성 요소 서비스**에서 **콘솔 루트** >  **구성 요소 서비스** > **컴퓨터**를 클릭한 다음 **내 컴퓨터**를 클릭합니다. **작업** 메뉴에서 **속성**을 클릭합니다.  

3.  **내 컴퓨터 속성** 대화 상자에서 **COM 보안** 탭의 **시작 및 활성화 권한** 섹션에 있는 **제한 편집**을 클릭합니다.  

4.  **시작 및 활성화 권한** 대화 상자에서 **추가**를 클릭합니다.  

5.  **사용자, 컴퓨터, 서비스 계정 또는 그룹 선택** 대화 상자에서 **선택할 개체 이름을 입력하세요(예제)** 상자에 **SMS Admins**를 입력하고 **확인**을 클릭합니다.  

    > [!NOTE]  
    >  SMS Admins 그룹을 찾기 위해 **찾을 위치를 선택하십시오.** 에 대한 설정을 변경해야 할 수 있습니다. 이 그룹은 SMS 공급자가 구성원 서버에서 실행될 때 컴퓨터에 대해 로컬이며, SMS 공급자가 도메인 컨트롤러에서 실행될 때 도메인 로컬 그룹입니다.  

6.  **SMS Admins의 권한** 섹션에서, 원격 활성화를 허용하도록 **원격 활성화** 확인란을 선택합니다.  

7.  **확인** 을 클릭하고 한 번 더 **확인** 을 클릭한 후 **컴퓨터 관리**를 닫습니다. 이제 컴퓨터가 SMS Admins 그룹의 구성원에게 원격 Configuration Manager 콘솔 액세스를 허용하도록 구성됩니다.  

 원격 Configuration Manager 콘솔을 지원할 수 있는 각 SMS 공급자 컴퓨터에 대해 이 절차를 반복합니다.  

##  <a name="bkmk_dbconfig"></a> 사이트 데이터베이스 구성 수정  
 사이트를 설치한 후 중앙 관리 사이트 서버 또는 기본 사이트 서버에서 설치 프로그램을 실행하여 사이트 데이터베이스 및 사이트 데이터베이스 서버의 구성을 수정할 수 있습니다. 사이트 데이터베이스는 동일한 컴퓨터의 SQL Server 새 인스턴스 또는 지원되는 SQL Server 버전을 실행하는 다른 컴퓨터로 이동할 수 있습니다. 이러한 변경 내용 및 관련 변경 내용이 보조 사이트의 데이터베이스 구성에 대해서는 지원되지 않습니다.  

 지원 제한 사항에 대한 자세한 내용은 [구성 관리자 환경의 수동 데이터베이스 변경에 대한 지원 정책](https://support.microsoft.com/kb/3106512)을 참조하세요.  

> [!NOTE]  
>  사이트에 대한 데이터베이스 구성을 수정할 때 Configuration Manager에서는 사이트 서버와 데이터베이스와 통신하는 원격 사이트 시스템 서버의 Configuration Manager 서비스를 다시 시작하거나 다시 설치합니다.  

**데이터베이스 구성을 수정하려면**사이트 서버에서 설치 프로그램을 실행하고 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**옵션을 선택해야 합니다. 그런 다음 **SQL Server 구성 수정(_M)** 옵션을 선택합니다. 다음 사이트 데이터베이스 구성을 변경할 수 있습니다.  

-   데이터베이스를 호스트하는 Windows 기반 서버  

-   SQL Server 데이터베이스를 호스트하는 서버에서 사용 중인 SQL Server의 인스턴스  

-   데이터베이스 이름.  

-   Configuration Manager에서 사용 중인 SQL Server 포트  

-   Configuration Manager에서 사용 중인 SQL Server Service Broker 포트  

**사이트 데이터베이스를 이동하려면 다음을 구성해야 합니다.**  

-   **액세스 구성** : 사이트 데이터베이스를 새 컴퓨터로 이동할 경우 사이트 서버의 컴퓨터 계정을 SQL Server를 실행하는 컴퓨터의 **로컬 관리자** 그룹에 추가합니다. 사이트 데이터베이스에 대해 SQL Server 클러스터를 사용할 경우 같은 컴퓨터 계정을 각 Windows Server 클러스터 노드 컴퓨터의 **로컬 관리자** 그룹에 추가해야 합니다.  

-   **CLR(공용 언어 런타임) 통합 사용:**  데이터베이스를 SQL Server의 새 인스턴스 또는 새 SQL Server 컴퓨터로 이동할 경우 CLR(공용 언어 런타임) 통합을 사용하도록 설정해야 합니다. CLR을 사용하도록 설정하려면 **SQL Server Management Studio**를 사용하여 사이트 데이터베이스를 호스트하는 SQL Server 인스턴스에 연결하고 **sp_configure 'clr enabled',1; reconfigure** 저장 프로시저를 쿼리로 실행합니다.  
-  **새 SQL Server가 백업 위치에 액세스할 수 있는지 확인:** UNC를 사용하여 사이트 데이터베이스 백업을 저장하는 경우 SQL Server AlwaysOn 가용성 그룹을 SQL Server 클러스터로 이동을 포함하여 데이터베이스를 새 서버로 이동한 후 새 SQL Server의 컴퓨터 계정에 UNC 위치에 대한 **쓰기** 권한이 있는지 확인합니다.  


> [!IMPORTANT]  
>  관리 지점에 대해 하나 이상의 데이터베이스 복제본이 있는 데이터베이스를 이동하려면 먼저 데이터베이스 복제본을 제거해야 합니다. 데이터베이스 이동을 완료한 후 데이터베이스 복제본을 다시 구성할 수 있습니다. 자세한 내용은 [System Center Configuration Manager의 관리 지점용 데이터베이스 복제본](../../../core/servers/deploy/configure/database-replicas-for-management-points.md)을 참조하세요.  

##  <a name="bkmk_SPN"></a> 사이트 데이터베이스 서버에 대한 SPN 관리  
사이트 데이터베이스에 대한 SQL 서비스를 실행하는 계정을 선택할 수 있습니다.  

-   컴퓨터 시스템 계정으로 서비스를 실행하는 경우 SPN이 자동으로 등록됩니다.  

-   도메인 로컬 사용자 계정으로 서비스를 실행하는 경우 SPN을 수동으로 등록하여 SQL 클라이언트 및 다른 사이트 시스템이 Kerberos 인증을 수행할 수 있도록 해야 합니다. Kerberos 인증을 사용하지 않으면 데이터베이스와 통신할 수 없습니다.  

SQL Server 설명서는 [수동으로 SPN을 등록](https://technet.microsoft.com/library/ms191153\(v=sql.120\).aspx)하는 데 도움이 되며, SPN 및 Kerberos 연결에 대한 추가 배경 정보를 제공합니다.  

> [!IMPORTANT]  
>  -   클러스터된 SQL Server에 대한 SPN을 만들 때 SQL Server 클러스터의 가상 이름을 SQL Server 컴퓨터 이름으로 지정해야 합니다.  
> -   SQL Server 명명된 인스턴스에 대한 SPN을 등록하는 명령은 포트 번호가 명명된 인스턴스에서 사용되는 포트와 일치해야 한다는 점만 제외하고 기본 인스턴스에 대한 SPN을 등록할 때 사용하는 명령과 동일합니다.  

**Setspn** 도구를 사용하면 사이트 데이터베이스 서버의 SQL Server 서비스 계정에 대한 SPN을 등록할 수 있습니다. Setspn 도구는 SQL Server의 도메인에 상주하는 컴퓨터에서 도메인 관리자 자격 증명을 사용하여 실행해야 합니다.  

 다음 절차는 Windows Server 2008 R2에서 Setspn 도구를 사용하여 SQL Server 서비스 계정에 대한 SPN을 관리하는 방법을 보여 주는 예제입니다. Setspn에 대한 특정 지침은 [Setspn Overview(Setspn 개요)](http://go.microsoft.com/fwlink/p/?LinkId=226343)또는 이에 해당하는 운영 체제별 설명서를 참조하십시오.  

> [!NOTE]  
>  다음 절차는 Setspn 명령줄 도구를 참조합니다. Setspn 명령줄 도구는 제품 CD 또는 [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/p/?LinkId=100114)에서 Windows Server 2003 지원 도구를 설치할 때 포함됩니다. 제품 CD에서 Windows 지원 도구를 설치하는 방법에 대한 자세한 내용은 [Windows 지원 도구 설치](http://go.microsoft.com/fwlink/p/?LinkId=62270)를 참조하십시오.  

#### <a name="to-manually-create-a-domain-user-service-principal-name-spn-for-the-sql-server-service-account"></a>수동으로 SQL Server 서비스 계정에 대한 도메인 사용자 SPN을 만들려면  

1.  **시작** 메뉴에서 **실행**을 클릭한 다음 [실행] 대화 상자에 **cmd** 를 입력합니다.  

2.  명령줄에서 Windows Server 지원 도구 설치 디렉터리로 이동합니다. 기본적으로 이러한 도구는 **C:\Program Files\Support Tools** 디렉터리에 있습니다.  

3.  SPN을 만드는 데 올바른 명령을 입력합니다. SPN을 만들 때 SQL Server를 실행하는 컴퓨터의 NetBIOS 이름 또는 FQDN(정규화된 도메인 이름)을 사용할 수 있습니다. 그러나 NetBIOS 이름 및 FQDN 모두에 대한 SPN을 만들어야 합니다.  

    > [!IMPORTANT]  
    >  클러스터된 SQL Server에 대한 SPN을 만들 때 SQL Server 클러스터의 가상 이름을 SQL Server 컴퓨터 이름으로 지정해야 합니다.  

    -   SQL Server 컴퓨터의 NetBIOS 이름에 대해 SPN을 만들려면 **setspn -A MSSQLSvc/&lt;SQL Server 컴퓨터 이름\>:1433 &lt;도메인\계정>** 명령을 입력합니다.  

    -   SQL Server 컴퓨터의 FQDN에 대해 SPN을 만들려면 **setspn -A MSSQLSvc/&lt;SQL Server FQDN\>:1433 &lt;도메인\계정>** 명령을 입력합니다.  

    > [!NOTE]  
    >  SQL Server 명명된 인스턴스에 대한 SPN을 등록하는 명령은 포트 번호가 명명된 인스턴스에서 사용되는 포트와 일치해야 한다는 점만 제외하고 기본 인스턴스에 대한 SPN을 등록할 때 사용하는 명령과 동일합니다.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-by-using-the-setspn-command"></a>Setspn 명령을 사용하여 도메인 사용자 SPN이 올바르게 등록되었는지 확인하려면  

1.  **시작** 메뉴에서 **실행**을 클릭한 다음 **실행** 대화 상자에 **cmd** 를 입력합니다.  

2.  명령 프롬프트에서 **setspn -L &lt;domain\SQL Service 계정>** 명령을 입력합니다.  

3.  등록된 **ServicePrincipalName** 을 검토하여 SQL Server에 대해 유효한 SPN이 만들어졌는지 확인합니다.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-when-using-the-adsiedit-mmc-console"></a>ADSIEdit MMC 콘솔을 사용하여 도메인 사용자 SPN이 올바르게 등록되었는지 확인하려면  

1.  **시작** 메뉴에서 **실행**을 클릭한 다음 **adsiedit.msc** 를 입력하여 ADSIEdit MMC 콘솔을 시작합니다.  

2.  필요한 경우 사이트 서버의 도메인에 연결합니다.  

3.  콘솔 창에서 사이트 서버의 도메인, **DC=&lt;서버 고유 이름\>**, **CN=Users**를 차례로 확장하고 **CN=&lt;서비스 계정 사용자\>**를 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  

4.  **CN=&lt;서비스 계정 사용자\> 속성** 대화 상자에서 **servicePrincipalName** 값을 검토하여 유효한 SPN이 작성되어 올바른 SQL Server 컴퓨터에 연결되었는지 확인합니다.  

#### <a name="to-change-the-sql-server-service-account-from-local-system-to-a-domain-user-account"></a>로컬 시스템의 SQL Server 서비스 계정을 도메인 사용자 계정으로 변경하려면  

1.  SQL Server 서비스 계정으로 사용할 도메인 또는 로컬 시스템 사용자 계정을 만들거나 선택합니다.  

2.  **SQL Server 구성 관리자**를 엽니다.  

3.  **SQL Server 서비스**를 클릭한 다음 **SQL Server&lt;인스턴스 이름\>**을 두 번 클릭합니다.  

4.  **로그온** 탭에서 **계정 지정**을 선택한 다음 1단계에서 만든 도메인 사용자 계정에 대한 사용자 이름 및 암호를 입력하거나, **찾아보기** 를 클릭하여 Active Directory Domain Services에서 사용자 계정을 찾은 후 **적용**을 클릭합니다.  

5.  **계정 변경 확인** 대화 상자에서 **예** 를 클릭하여 서비스 계정 변경을 확인하고 SQL Server 서비스를 다시 시작합니다.  

6.  서비스 계정이 성공적으로 변경되면 **확인** 을 클릭합니다.  

##  <a name="bkmk_reset"></a> 사이트 다시 설정 실행  
 중앙 관리 사이트 또는 기본 사이트에서 사이트 다시 설정을 실행할 경우 사이트에서 다음 작업이 수행됩니다.  

-   기본 Configuration Manager 파일 및 레지스트리 권한을 다시 적용합니다.  

-   사이트에 모든 사이트 구성 요소 및 모든 사이트 시스템 역할을 다시 설치합니다.  

보조 사이트는 사이트 다시 설정을 지원하지 않습니다.  

필요한 경우 사이트 다시 설정을 수동으로 실행할 수 있지만, 사이트 구성을 수정한 후 자동으로 실행할 수도 있습니다.  

예를 들어 Configuration Manager 구성 요소에서 사용하는 계정이 변경된 경우 수동으로 사이트를 다시 설정하여 사이트 구성 요소에서 새 계정 정보를 사용하도록 업데이트하는 것이 좋습니다. 그러나 사이트에서 클라이언트 또는 서버 언어를 수정할 경우 사이트가 이러한 변경 내용을 사용하려면 다시 설정해야 하므로 Configuration Manager에서 사이트 다시 설정을 자동으로 실행합니다.  

> [!NOTE]  
>  사이트 다시 설정을 실행해도 비 Configuration Manager 개체에 대한 액세스 권한은 다시 설정되지 않습니다.  

사이트를 다시 설정을 실행하면 다음 작업이 수행됩니다.  

1.  설치 프로그램에서 **SMS_EXECUTIVE** 서비스의 스레드 구성 요소와 **SMS_SITE_COMPONENT_MANAGER** 서비스를 중지한 후 다시 시작합니다.  

2.  설치 프로그램에서 로컬 컴퓨터 및 원격 사이트 시스템 컴퓨터에서 사이트 시스템 공유 폴더 및 **SMS Executive** 구성 요소를 제거한 후 다시 만듭니다.  

3.  설치 프로그램에서 **SMS_SITE_COMPONENT_MANAGER** 서비스를 다시 시작하며, 이 서비스가 **SMS_EXECUTIVE** 및 **SMS_SQL_MONITOR** 서비스를 설치합니다.  

또한 사이트 다시 설정을 통해 다음 개체가 복원됩니다.  

-   **SMS** 또는 **NAL** 레지스트리 키 및 이러한 키 아래의 모든 기본 하위 키  

-   Configuration Manager 파일 디렉터리 트리 및 해당 파일 디렉터리 파일의 기타 기본값 파일이나 하위 디렉터리입니다.  

**사이트 다시 설정을 실행하기 위한 필수 조건**  

사이트 재설정을 수행하는 데 사용하는 계정은 다음 사용 권한을 보유해야 합니다.  

-   사이트 재설정을 수행하는 데 사용하는 계정은 다음 사용 권한을 보유해야 합니다.  

    -   **중앙 관리 사이트**: 이 사이트에서 사이트 재설정을 실행하는 데 사용하는 계정은 중앙 관리 사이트 서버의 로컬 관리자여야 하며 **전체 관리자** 역할 기반 관리 보안 역할과 동일한 권한을 보유해야 합니다.  

    -   **기본 사이트**: 이 사이트에서 사이트 재설정을 실행하는 데 사용하는 계정은 기본 사이트 서버의 로컬 관리자여야 하며 **전체 관리자** 역할 기반 관리 보안 역할과 동일한 권한을 보유해야 합니다. 기본 사이트가 중앙 관리 사이트의 계층 내에 있으면 또한 이 계정은 중앙 관리 사이트 서버의 로컬 관리자여야 합니다.  

**사이트 다시 설정에 대한 제한 사항**
  - 버전 1602부터, 계층 구조가 [사전 프로덕션 컬렉션에서 클라이언트 업그레이드 테스트](/sccm/core/clients/manage/upgrade/test-client-upgrades)를 지원하도록 구성되어 있으면 사이트 다시 설정을 사용하여 사이트에 설치된 서버 또는 클라이언트 언어 팩을 변경할 수 없습니다.

#### <a name="to-perform-a-site-reset"></a>사이트 재설정을 수행하려면  

1.  **&lt;Configuration Manager 사이트 설치 폴더\>\BIN\X64\setup.exe**에서 **Configuration Manager 설치 프로그램**을 실행합니다.  

    > [!TIP]  
    >  사이트 서버 컴퓨터의 **시작** 메뉴 또는 Configuration Manager 원본 미디어에서 Configuration Manager 설치 프로그램을 시작하여 사이트 다시 설정을 실행할 수도 있습니다.  

2.  **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.  

3.  **사이트 유지 관리** 페이지에서 **구성 변경 없이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.  

4.  사이트 재설정을 시작하려면 **예** 를 클릭합니다.  

사이트 재설정을 마치면 **닫기** 를 클릭하여 이 절차를 완료합니다.  

##  <a name="bkmk_sitelang"></a> 사이트에서 언어 팩 관리  
사이트를 설치한 후 사용 중인 서버와 클라이언트 언어 팩을 변경할 수 있습니다.  

**서버 언어 팩:**  

-   **적용 대상:**  

     Configuration Manager 콘솔 설치  

     적용 가능한 사이트 시스템 역할의 새 설치  

-   **세부 정보:**  

     사이트에서 서버 언어 팩을 업데이트한 후 Configuration Manager 콘솔에 언어 팩 지원을 추가할 수 있습니다.  

     Configuration Manager 콘솔에 서버 언어 팩에 대한 지원을 추가하려면 사용할 언어 팩이 포함된 사이트 서버의 **ConsoleSetup** 폴더에서 Configuration Manager 콘솔을 설치해야 합니다. Configuration Manager 콘솔이 이미 설치된 경우 이를 먼저 제거해야 새로 설치할 때 지원되는 언어 팩의 최신 목록이 식별됩니다.  

**클라이언트 언어 팩:**  

-   **적용 대상:**  

     클라이언트 언어 팩을 변경하면 클라이언트 설치 소스 파일이 업데이트되므로 새 클라이언트 설치 및 업그레이드 시 업데이트된 클라이언트 언어 목록에 대한 지원이 추가됩니다.  

-   **세부 정보:**  

     사이트에서 클라이언트 언어 팩을 업데이트한 후 클라이언트 언어 팩을 포함하는 원본 파일을 사용하여 언어 팩을 사용하는 각 클라이언트를 설치해야 합니다.  

Configuration Manager에서 지원하는 클라이언트 및 서버 언어에 대한 자세한 내용은 [System Center Configuration Manager의 언어 팩](../../../core/servers/deploy/install/language-packs.md)을 참조하세요.  

#### <a name="to-modify-the-language-packs-that-are-supported-at-a-site"></a>사이트에서 지원되는 언어 팩을 수정하려면  

1.  사이트 서버의 **&lt;Configuration Manager 사이트 설치 폴더\>\BIN\X64\setup.exe**에서 Configuration Manager 설치 프로그램을 실행합니다.  

2.  **시작** 페이지에서 **사이트 유지 관리 수행 또는 이 사이트 다시 설정**을 선택하고 **다음**을 클릭합니다.  

3.  **사이트 유지 관리** 페이지에서 **언어 구성 수정**을 선택하고 **다음**을 클릭합니다.  

4.  **필수 다운로드** 페이지에서 **필수 파일 다운로드** 를 선택하여 언어 팩의 업데이트를 가져오거나, **이전에 다운로드한 파일 사용** 을 선택하여 사이트에 추가하려는 언어 팩이 포함된 이전에 다운로드한 파일을 사용합니다. **다음** 을 클릭하여 파일의 유효성을 검사하고 계속합니다.  

5.  **서버 언어 선택** 페이지에서 이 사이트가 지원하는 서버 언어의 확인란을 선택하고 **다음**을 클릭합니다.  

6.  **클라이언트 언어 선택** 페이지에서 이 사이트가 지원하는 클라이언트 언어의 확인란을 선택하고 **다음**을 클릭합니다.  

7.  **다음**을 클릭하여 사이트에서 언어 지원을 수정합니다.  

    > [!NOTE]  
    >  Configuration Manager는 사이트 다시 설정을 시작하여 사이트에서 모든 사이트 시스템 역할을 다시 설치합니다.  

8.  **닫기** 를 클릭하여 이 절차를 완료합니다.  

##  <a name="BKMK_ModDBAlert"></a> 데이터베이스 서버 경고 임계값 수정  
 기본적으로 Configuration Manager는 사이트 데이터베이스 서버에서 사용 가능한 디스크 공간이 부족해지면 경고를 생성합니다. 기본값은 사용 가능한 디스크 공간이 10GB 이하일 때 경고를 생성하고 5GB 이하일 때는 중요한 경고를 생성하도록 설정되어 있습니다. 이 값을 수정하거나 각 사이트에 대해 경고를 사용하지 않도록 설정할 수 있습니다.  

 이 설정을 변경하려면  

1.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.  

2.  구성할 사이트를 선택하고 해당 사이트의 **속성**을 엽니다.  

3.  사이트의 **속성** 대화 상자에서 **경고** 탭을 선택한 다음 설정을 편집합니다.  

4.  **확인** 을 클릭하여 사이트 속성 대화 상자를 닫습니다.  
