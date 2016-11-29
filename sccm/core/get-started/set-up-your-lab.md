---
title: "System Center Configuration Manager 랩 설정"
description: "시뮬레이트된 실제 작업을 사용하여 Configuration Manager를 평가하기 위한 랩을 설정합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b1970688-0cd2-404f-a17f-9e2aa4a78758
caps.latest.revision: 11
caps.handback.revision: 0
author: brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: ea084f30a1a6ec731e97cec46448d0ffbfca42e0


---
# <a name="set-up-your-system-center-configuration-manager-lab"></a>System Center Configuration Manager 랩 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 지침을 따라 시뮬레이트된 실제 작업을 사용하여 Configuration Manager 평가를 위해 랩을 설정할 수 있습니다.  

##  <a name="a-namebkmklabcorea-core-components"></a><a name="BKMK_LabCore"></a> 핵심 구성 요소  
 System Center Configuration Manager에 대해 환경을 설정하려면 일부 핵심 구성 요소가 Configuration Manager 설치를 지원해야 합니다.  

-   **랩 환경에서는 Windows Server 2012 R2를 사용**하며, 여기에 System Center Configuration Manager를 설치합니다.  

     Windows Server 2012 R2 평가판은 [TechNet 평가 센터](https://www.microsoft.com/evalcenter/evaluate-windows-server-2012)에서 다운로드할 수 있습니다.  

     이러한 실습 과정에서 참조된 일부 다운로드에 더 쉽게 액세스하려면 Internet Explorer 보안 강화 구성을 수정하거나 사용하지 않는 것이 좋습니다. 자세한 내용은 [Internet Explorer: 보안 강화 구성](https://technet.microsoft.com/en-us/library/dd883248\(v=ws.10\).aspx)을 참조하세요.  

-   **랩 환경에서는 SQL Server 2012 SP2**를 사이트 데이터베이스로 사용합니다.  

     SQL Server 2012 평가판은 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=29066)에서 다운로드할 수 있습니다.  

     SQL Server에는 System Center Configuration Manager에서 사용하기 위해 충족해야 하는 [지원되는 버전의 SQL Server](../../core/plan-design/configs/support-for-sql-server-versions.md#bkmk_SQLVersions)가 있습니다.  

    -   Configuration Manager에서 사이트 데이터베이스를 호스트하려면 64비트 버전의 SQL Server가 필요합니다.  

    -   **SQL_Latin1_General_CP1_CI_AS**가 **SQL Collation** 클래스로 필요합니다.  

    -   [SQL 인증 대신](https://technet.microsoft.com/en-us/library/ms144284.aspx) **Windows 인증**이 필요합니다.  

    -   전용 **SQL Server 인스턴스**가 필요합니다.  

    -   SQL Server에 대한 **시스템 주소 지정 가능 메모리**를 제한하지 마세요.  

    -   **도메인 로컬 사용자** 계정을 사용하여 실행되도록 **SQL Server 서비스 계정**을 구성합니다.  

    -   **SQL Server Reporting Services**를 설치해야 합니다.  

    -   **사이트 간 통신**은 기본 포트 TCP 4022에서 SQL Server Service Broker를 사용합니다.  

    -   SQL Server 데이터베이스 엔진 및 선택한 Configuration Manager 사이트 시스템 역할 간의 **사이트 간 통신**은 기본 포트 TCP 1433을 사용합니다.  

-   **도메인 컨트롤러는 Windows Server 2008 R2**(Active Directory Domain Services가 설치되어 있음)를 사용합니다. 또한 도메인 컨트롤러는 정규화된 도메인 이름에 사용할 DHCP 및 DNS 서버에 대한 호스트 역할을 합니다.  

     자세한 내용은 이 [Active Directory Domain Services 개요](https://technet.microsoft.com/en-us/library/hh831484)를 참조하세요.  

-   **Hyper-V는 몇몇 가상 컴퓨터와 함께 사용**되어 이 연습에서 수행하는 관리 단계가 예상대로 작동하는지 확인합니다. Windows 7 이상이 설치된 최소 3대의 가상 컴퓨터를 사용하는 것이 좋습니다.  

     자세한 내용은 이 [Hyper-V 개요](https://technet.microsoft.com/en-us/library/hh831531.aspx)를 참조하세요.  

-   이러한 모든 구성 요소에는 **관리자 권한**이 필요합니다.  

    -   Configuration Manager는 Windows Server 환경 내에서 로컬 권한을 가진 관리자가 필요함  

    -   Active Directory는 스키마를 수정할 수 있는 권한이 있는 관리자가 필요함  

    -   가상 컴퓨터는 컴퓨터 자체에 대한 로컬 권한이 필요함  

이 랩에는 필요하지 않지만 System Center Configuration Manager 구현 요구 사항에 대한 추가 정보를 위해 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md)을 검토할 수 있습니다. 여기서 참조할 수 없는 소프트웨어 버전은 설명서를 참조하세요.  

이러한 구성 요소를 모두 설치한 후에는 Configuration Manager에 대한 Windows 환경을 구성하기 위해 다음과 같은 추가 단계를 수행해야 합니다.  

###  <a name="a-namebkmklabadprepa-prepare-active-directory-content-for-the-lab"></a><a name="BKMK_LabADPrep"></a> 랩에 대한 Active Directory 콘텐츠 준비  
 이 랩에 대해 보안 그룹을 만든 다음 도메인 사용자를 추가합니다.  

-   보안 그룹: **Evaluation**  

    -   그룹 범위: **Universal**  

    -   그룹 유형: **Security**  

-   도메인 사용자: **ConfigUser**  

     정상적인 상황에서는 환경 내의 모든 사용자에게 공용 액세스 권한을 부여하지 않습니다. 온라인에서 랩을 가져오는 것을 간소화하기 위해 이 사용자에게 그렇게 하고 있는 것입니다.  

다음 단계는 Configuration Manager 클라이언트가 사이트 리소스를 찾기 위해 Active Directory Domain Services를 쿼리하도록 하는 데 필요하며 다음 절차에 나열됩니다.  

###  <a name="a-namebkmkcreatesysmgmtlaba-create-the-system-management-container"></a><a name="BKMK_CreateSysMgmtLab"></a> 시스템 관리 컨테이너 만들기  
 Configuration Manager에서는 스키마를 확장할 때 Active Directory Domain Services에서 필요한 시스템 관리 컨테이너가 자동으로 만들어지지 않습니다. 따라서 랩을 위해 이를 만듭니다. 이 단계를 수행하려면 [ADSI 편집 설치](https://technet.microsoft.com/en-us/library/cc773354\(WS.10\).aspx#BKMK_InstallingADSIEdit)가 필요합니다.  

 Active Directory Domain Services의 **시스템** 컨테이너에 대해 **모든 자식 개체 만들기** 권한이 있는 계정으로 로그온해야 합니다.  

##### <a name="to-create-the-system-management-container"></a>시스템 관리 컨테이너를 만들려면  

1.  **ADSI 편집**을 실행하고 사이트 서버가 있는 도메인에 연결합니다.  

2.  **도메인&lt;컴퓨터의 정규화된 도메인 이름\>**, **<고유 이름\>**을 차례로 확장한 다음 **CN=System**을 마우스 오른쪽 단추로 클릭하고 **새로 만들기**, **개체**를 차례로 클릭합니다.  

3.  **개체 만들기** 대화 상자에서 **컨테이너**를 선택한 후 **다음**을 클릭합니다.  

4.  **값** 상자에 **System Management**을 입력하고 **다음**을 클릭합니다.  

5.  **마침** 을 클릭하여 절차를 완료합니다.  

###  <a name="a-namebkmksetsecpermlaba-set-security-permissions-for-the-system-management-container"></a><a name="BKMK_SetSecPermLab"></a> 시스템 관리 컨테이너에 대한 보안 권한 설정  
 사이트 정보를 컨테이너에 게시하는 데 필요한 권한을 사이트 서버의 컴퓨터 계정에 부여합니다. 이 작업에 대해서도 ADSI 편집을 사용합니다.  

> [!IMPORTANT]  
>  다음 절차를 시작하기 전에 사이트 서버의 도메인에 연결되어 있는지 확인합니다.  

##### <a name="to-set-security-permissions-for-the-system-management-container"></a>시스템 관리 컨테이너에 대한 보안 권한을 설정하려면  

1.  콘솔 창에서 **사이트 서버의 도메인**, **DC=&lt;서버 고유 이름\>**, **CN=System**을 차례로 확장합니다. **CN=System Management**를 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.  

2.  **CN=System Management Properties** 대화 상자에서 **보안** 탭을 클릭한 다음 **추가** 를 클릭하여 사이트 서버 컴퓨터 계정을 추가합니다. 계정에 **모든 권한** 을 부여합니다.  

3.  **고급**을 클릭하고 사이트 서버의 컴퓨터 계정을 선택한 다음 **편집**을 클릭합니다.  

4.  **적용 대상** 목록에서 **이 개체 및 모든 하위 개체**를 선택합니다.  

5.  **확인** 을 클릭하여 **ADSI Edit** 콘솔을 닫고 절차를 완료합니다.  

     이 절차에 대한 자세한 내용은 [System Center Configuration Manager에 대한 Active Directory 스키마 확장](../../core/plan-design/network/extend-the-active-directory-schema.md)을 참조하세요.  

###  <a name="a-namebkmkextadschlaba-extend-the-active-directory-schema-using-extadschexe"></a><a name="BKMK_ExtADSchLab"></a> extadsch.exe를 사용하여 Active Directory 스키마 확장  
 이 랩에 대해 Active Directory 스키마를 확장하면 최소한의 관리 오버헤드로 모든 Configuration Manager 기능을 사용할 수 있습니다. Active Directory 스키마 확장은 포리스트당 한 번만 수행하는 포리스트 전체 구성입니다. 스키마를 영구적으로 확장하면 기본 Active Directory 구성에서 클래스 및 특성의 집합이 수정됩니다. 이 작업은 되돌릴 수 없습니다. 스키마를 확장하면 Configuration Manager가 랩 환경에서 가장 효과적으로 기능을 수행할 수 있게 하는 구성 요소에 액세스할 수 있습니다.  

> [!IMPORTANT]  
>  **스키마 관리** 보안 그룹의 멤버인 계정으로 스키마 마스터 도메인 컨트롤러에 로그온했는지 확인합니다. 대체 자격 증명을 사용하려는 시도는 실패합니다.  

##### <a name="to-extend-the-active-directory-schema-using-extadschexe"></a>extadsch.exe를 사용하여 Active Directory 스키마를 확장하려면  

1.  스키마 마스터 도메인 컨트롤러의 시스템 상태에 대한 백업을 만듭니다. 백업 마스터 도메인 컨트롤러에 대한 자세한 내용은 [Windows Server 백업](https://technet.microsoft.com/en-us/library/cc770757.aspx)을 검토하세요.  

2.  설치 미디어에서 **\SMSSETUP\BIN\X64** 으로 이동합니다.  

3.  **extadsch.exe**를 실행합니다.  

4.  시스템 드라이브의 루트 폴더에 있는 **extadsch.log** 를 검토하여 스키마가 제대로 확장되었는지 확인합니다.  

     이 절차에 대한 자세한 내용은 [System Center Configuration Manager에 대한 Active Directory 스키마 확장](../../core/plan-design/network/extend-the-active-directory-schema.md)을 참조하세요.  

###  <a name="a-namebkmkothertaskslaba-other-required-tasks"></a><a name="BKMK_OtherTasksLab"></a> 기타 필수 작업  
 또한 설치하기 전에 다음 작업도 완료해야 합니다.  

 **모든 다운로드를 저장할 폴더 만들기**  

 이 연습에서 설치 미디어의 구성 요소에 필요한 여러 다운로드가 있습니다. 모든 설치 절차를 시작하기 전에 이러한 파일의 이동을 요구하고 나서 랩의 서비스를 해제하려고 하는 위치를 결정합니다. 이러한 다운로드를 저장하기 위해 별도의 하위 폴더가 있는 단일 폴더를 사용하는 것이 좋습니다.  

 **.NET을 설치하고 Windows Communication Foundation을 활성화합니다.**  

 두 .NET Framework를 설치해야 합니다. 먼저 .NET 3.5.1을 설치한 다음 .NET 4.5.2 이상을 설치합니다. WCF(Windows Communication Foundation)도 활성화해야 합니다. WCF는 분산 컴퓨팅, 광범위한 상호 운용성 및 서비스 방향에 대한 직접 지원에 관리 가능한 접근을 제공하도록 설계되었으며 서비스 지향 프로그래밍 모델을 통해 연결된 응용 프로그램의 배포를 간소화합니다. WCF에 대한 자세한 내용은 [Windows Communication Foundation 정의](https://technet.microsoft.com/en-us/subscriptions/ms731082\(v=vs.90\).aspx) 를 검토하세요.  

##### <a name="to-install-net-and-activate-windows-communication-foundation"></a>.NET을 설치하고 Windows Communication Foundation을 활성화하려면  

1.  **Server Manager**를 연 다음 **관리**로 이동합니다.  **역할 및 기능 추가** 를 클릭하여 **역할 및 기능 추가 Wizard.**를 엽니다.  

2.  **시작하기 전에** 패널에서 제공된 정보를 검토하고 **다음**을 클릭합니다.  

3.  **역할 기반 또는 기능 기반 설치**를 선택하고 **다음**을 클릭합니다.  

4.  **서버 풀**에서 서버를 선택하고 **다음**을 클릭합니다.  

5.  **서버 역할** 패널을 검토하고 **다음**을 클릭합니다.  

6.  다음 **기능** 을 목록에서 선택하여 추가합니다.  

    -   **.NET Framework 3.5 기능**  

        -   **.NET Framework 3.5(.NET 2.0 및 3.0 포함)**  

    -   **.NET Framework 4.5 기능**  

        -   **.NET Framework 4.5**  

        -   **ASP.NET 4.5**  

        -   **WCF 서비스**  

            -   **HTTP 활성화**  

            -   **TCP 포트 공유**  

7.  **웹 서버 역할(IIS)** 및 **역할 서비스** 화면을 검토하고 **다음**을 클릭합니다.  

8.  **확인** 화면을 검토하고 **다음**을 클릭합니다.  

9. **설치** 를 클릭하고 **서버 관리자** 의 **알림**창에서 설치가 제대로 완료되었는지 확인합니다.  

10. .NET의 기본 설치가 완료된 후 [Microsoft 다운로드 센터](https://www.microsoft.com/en-us/download/details.aspx?id=42643) 로 이동하여 .NET Framework 4.5.2에 대한 웹 설치 관리자를 가져옵니다. **다운로드** 단추를 클릭한 다음 설치 관리자를 **실행** 합니다. 선택한 언어로 필요한 구성 요소를 자동으로 검색하고 설치합니다.  

자세한 내용은 이 .NET Framework가 필요한 이유에 대한 다음 문서를 검토하세요.  

-   [.NET Framework 버전 및 종속성](https://technet.microsoft.com/en-us/library/bb822049.aspx)  

-   [.NET Framework 4 RTM 응용 프로그램 호환성 연습](https://technet.microsoft.com/en-us/library/dd889541.aspx)  

-   [방법: ASP.NET 웹 응용 프로그램을 ASP.NET 4로 업그레이드](https://technet.microsoft.com/en-us/library/dd483478\(VS.100\).aspx)  

-   [Microsoft .NET Framework 지원 기간 정책 FAQ](https://support.microsoft.com/en-us/gp/framework_faq?WT.mc_id=azurebg_email_Trans_943_NET452_Update)  

-   [CLR 자세히 보기 - In-Process Side-by-Side](https://msdn.microsoft.com/en-us/magazine/ee819091.aspx)  

**BITS, IIS 및 RDC 사용**  

[BITS(Background Intelligent Transfer Service)](https://technet.microsoft.com/en-us/library/dn282296.aspx) 는 클라이언트와 서버 간에 파일을 비동기적으로 전송하는 데 필요한 응용 프로그램에 사용됩니다. BITS는 전경과 배경에서 전송의 흐름을 측정하여 다른 네트워크 응용 프로그램의 응답을 유지합니다. 또한 전송 세션이 중단되는 경우 파일 전송이 자동으로 다시 시작됩니다.  

이 사이트 서버가 관리 지점으로도 사용되므로 이 랩에 대한 BITS를 설치합니다.  

IIS(인터넷 정보 서비스)는 웹에서 서비스를 호스트하는 데 사용할 수 있는 유연하고 확장성 있는 웹 서버입니다. 이는 많은 사이트 시스템 역할을 위해 Configuration Manager에서 사용됩니다. IIS에 대한 자세한 내용은 [System Center Configuration Manager의 사이트 시스템 서버용 웹 사이트](../../core/plan-design/network/websites-for-site-system-servers.md)를 참조하세요.  

[RDC(원격 차등 압축)](https://technet.microsoft.com/en-us/library/cc754372.aspx) 은 응용 프로그램이 파일 집합에 변경 사항이 생겼는지 확인하는 데 사용할 수 있는 API 집합입니다. RDC를 통해 응용 프로그램이 파일의 변경된 부분만 복제하므로 네트워크 트래픽을 최소로 유지할 수 있습니다.  

##### <a name="to-enable-bits-iis-and-rdc-site-server-roles"></a>BITS, IIS 및 RDC 사이트 서버 역할을 사용하도록 설정하려면  

1.  사이트 서버에서 **Server Manager**를 엽니다. **관리**로 이동합니다. **역할 및 기능 추가** 를 클릭하여 **역할 및 기능 추가 마법사**를 엽니다.  

2.  **시작하기 전에** 패널에서 제공된 정보를 검토하고 **다음**을 클릭합니다.  

3.  **역할 기반 또는 기능 기반 설치**를 선택하고 **다음**을 클릭합니다.  

4.  **서버 풀**에서 서버를 선택하고 **다음**을 클릭합니다.  

5.  목록에서 다음 **서버 역할** 을 선택하여 추가합니다.  

    -   **웹 서버(IIS)**  

        -   **일반 HTTP 기능**  

            -   **기본 문서**  

            -   **디렉터리 검색**  

            -   **HTTP 오류**  

            -   **정적 콘텐츠**  

            -   **HTTP 리디렉션**  

        -   **상태 및 진단**  

            -   **HTTP 로깅**  

            -   **로깅 도구**  

            -   **요청 모니터**  

            -   **추적**  

    -   **성능**  

        -   **정적 콘텐츠 압축**  

        -   **동적 콘텐츠 압축**  

    -   **Security**  

        -   **요청 필터링**  

        -   **기본 인증**  

        -   **클라이언트 인증서 매핑 인증**  

        -   **IP 및 도메인 제한**  

        -   **URL 권한 부여**  

        -   **Windows 권한 부여**  

    -   **응용 프로그램 개발**  

        -   **.NET 확장성 3.5**  

        -   **.NET 확장성 4.5**  

        -   **ASP**  

        -   **ASP.NET 3.5**  

        -   **ASP.NET 4.5**  

        -   **ISAPI 확장**  

        -   **ISAPI 필터**  

        -   **SSI(SSI(Server Side Includes))**  

    -   **FTP 서버**  

        -   **FTP 서비스**  

    -   **관리 도구**  

        -   **IIS 관리 콘솔**  

        -   **IIS 6 관리 호환성**  

            -   **IIS 6 메타데이터 호환성**  

            -   **IIS 6 관리 콘솔**  

            -   **IIS 6 스크립팅 도구**  

            -   **IIS 6 WMI 호환성**  

        -   **IIS 6 관리 스크립트 및 도구**  

        -   **Management Service**  

6.  다음 **기능** 을 목록에서 선택하여 추가합니다.  

    -   -   **BITS(Background Intelligent Transfer Service)**  

            -   **IIS 서버 확장**  

        -   **원격 서버 관리 도구**  

            -   **기능 관리 도구**  

                -   **BITS 서버 확장 도구**  

7.  **설치** 를 클릭하고 **서버 관리자** 의 **알림**창에서 설치가 제대로 완료되었는지 확인합니다.  

기본적으로 IIS는 HTTP 또는 HTTPS 통신을 통한 여러 파일 확장명 및 위치 액세스를 차단합니다. 이러한 파일을 클라이언트 시스템에 배포하려면 배포 지점에서 IIS에 대한 요청 필터링을 구성해야 합니다. 자세한 내용은 [배포 지점에 대한 IIS 요청 필터링](../../core/plan-design/network/prepare-windows-servers.md#BKMK_IISFiltering)을 참조하세요.  

##### <a name="to-configure-iis-filtering-on-distribution-points"></a>배포 지점에서 IIS 필터링을 구성하려면  

1.  **IIS Manager** 를 열고 사이드바에서 서버 이름을 선택합니다. 그러면 **홈** 화면으로 이동됩니다.  

2.  **기능 보기** 가 **홈** 화면의 맨 아래에서 선택되었는지 확인합니다. **IIS** 로 이동하고 **요청 필터링**을 엽니다.  

3.   **작업** 창에서 **파일 이름 확장명 허용...**을 클릭합니다.  

4.  대화 상자에 **.msi** 을 입력하고 **확인**을 클릭합니다.  

###  <a name="a-namebkmkinstallcmlaba-installing-configuration-manager"></a><a name="BKMK_InstallCMLab"></a> Configuration Manager 설치  
클라이언트를 직접 관리하기 위해 [기본 사이트를 사용할 시기 결정](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md#BKMK_ChoosePriimary)을 만듭니다. 그러면 랩 환경에서 잠재적인 장치의 [사이트 시스템 배율](/sccm/core/plan-design/configs/size-and-scale-numbers)에 대한 관리를 지원할 수 있습니다.  
또한 이 과정에서 계속 평가 장치를 관리하는 데 사용할 Configuration Manager 콘솔도 설치합니다.  

설치를 시작하기 전에 Windows Server 2012를 사용하는 서버에서 [필수 조건 검사기](/sccm/core/servers/deploy/install/prerequisite-checker)를 시작하여 모든 설정이 올바르게 사용되었는지 확인합니다.  

##### <a name="to-download-and-install-configuration-manager"></a>구성 관리자를 다운로드하고 설치하려면  

1.  [System Center 평가](https://www.microsoft.com/evalcenter/evaluate-system-center-2012-configuration-manager-and-endpoint-protection) 페이지로 이동하여 System Center Configuration Manager의 최신 평가판을 다운로드합니다.  

2.  미리 정의된 위치에 다운로드 미디어의 압축을 풉니다.  

3.  [System Center Configuration Manager 설치 마법사를 사용하여 사이트 설치](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites)에 나열된 설치 절차를 따릅니다. 해당 절차 내에서 다음을 입력합니다.  

    |사이트 설치 절차 단계|선택 항목|  
    |-----------------------------------------|---------------|  
    |4단계: **제품 키** 페이지|**평가**를 선택합니다.|  
    |7단계:  **필수 조건 다운로드**|**필수 파일 다운로드** 를 선택하고 미리 정의된 위치를 지정합니다.|  
    |10단계: **사이트 및 설치 설정**|-   **사이트 코드:LAB**<br />-   **사이트 이름:Evaluation**<br />-   **설치 폴더:** 미리 정의된 위치를 지정합니다.|  
    |11단계: **기본 사이트 설치**|**기본 사이트를 독립 사이트로 설치**를 선택하고 **다음**을 클릭합니다.|  
    |12단계: **데이터베이스 설치**|-   **SQL Server 이름(FQDN):** 여기에 FQDN을 입력합니다.<br />-   **인스턴스 이름:** 이전에 설치한 SQL의 기본 인스턴스를 사용하므로 이 이름을 비워둡니다.<br />-   **Service Broker 포트:** 기본 포트인 4022로 그대로 둡니다.|  
    |13단계: **데이터베이스 설치**|이 설정은 기본값으로 그대로 둡니다.|  
    |14단계: **SMS 공급자**|이 설정은 기본값으로 그대로 둡니다.|  
    |15단계: **클라이언트 통신 설정**|**모든 사이트 시스템 역할이 클라이언트로부터의 HTTPS 통신만 수락** 이 선택되지 않은 상태인지 확인합니다.|  
    |16단계: **사이트 시스템 역할**|FQDN을 입력하고 **모든 사이트 시스템 역할이 클라이언트로부터의 HTTPS 통신만 수락** 이 여전히 선택 취소된 상태인지 확인합니다.|  

###  <a name="a-namebkmkenablepublaba-enable-publishing-for-the-configuration-manager-site"></a><a name="BKMK_EnablePubLab"></a> Configuration Manager 사이트에 대해 게시 사용  
각 Configuration Manager 사이트에서는 자체 사이트 관련 정보를 Active Directory 스키마의 해당 도메인 파티션 내 System Management 컨테이너에 게시합니다. 이 트래픽을 처리하려면 Active Directory와 Configuration Manager 간의 통신에 대한 양방향 채널이 열려 있어야 합니다. 또한 Active Directory 및 네트워크 인프라의 특정 구성 요소를 확인하려면 포리스트 검색도 사용하도록 설정합니다.  

##### <a name="to-configure-active-directory-forests-for-publishing"></a>게시를 위한 Active Directory 포리스트를 구성하려면:  

1.  Configuration Manager 콘솔의 왼쪽 아래에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **계층 구성**을 확장하고 **검색 방법**을 클릭합니다.  

3.  **Active Directory 포리스트 검색** 을 선택하고 **속성**을 클릭합니다.  

4.  **속성** 대화 상자에서 **Active Directory 포리스트 검색 사용**을 선택합니다. 이 옵션이 활성화되면 **Active Directory 사이트 경계가 검색되면 자동으로 만들기**를 선택합니다.  **가능한 한 빨리 전체 검색을 실행하시겠습니까?** **예**를 클릭합니다.  

5.  화면 맨 위의 **검색 방법** 그룹에서 **지금 포리스트 검색 실행**을 클릭한 다음 사이드바에서 **Active Directory 포리스트** 로 이동합니다. Active Directory 포리스트가 검색된 포리스트 목록에 표시되어야 합니다.  

6.  화면 맨 위의 **일반** 탭으로 이동합니다.  

7.  **관리** 작업 영역에서 **계층 구성**을 확장하고 **Active Directory 포리스트**를 클릭합니다.  

##### <a name="to-enable-a-configuration-manager-site-to-publish-site-information-to-your-active-directory-forest"></a>Configuration Manager 사이트에서 사이트 정보를 Active Directory 포리스트에 게시할 수 있도록 하려면  

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  아직 검색되지 않은 새 포리스트를 구성합니다.  

3.  **관리** 작업 영역에서 **Active Directory 포리스트**를 클릭합니다.  

4.  사이트 속성의 **게시** 탭에서 연결된 포리스트를 선택한 다음 **확인** 을 클릭하여 구성을 저장합니다.



<!--HONumber=Nov16_HO1-->


