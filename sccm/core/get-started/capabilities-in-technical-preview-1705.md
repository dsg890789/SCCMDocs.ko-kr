---
title: 기술 미리 보기 1705
titleSuffix: Configuration Manager
description: Configuration Manager용 Technical Preview 버전 1705에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 00684289-d21a-45f8-b1e3-c5c787d73096
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: ff14adadca4024cf480bdf2a138c8781697d1469
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75804846"
---
# <a name="capabilities-in-technical-preview-1705-for-configuration-manager"></a>Configuration Manager용 Technical Preview 1705의 기능

*적용 대상: Configuration Manager(기술 미리 보기 분기)*

이 문서에서는 Configuration Manager용 Technical Preview 버전 1705에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대한 피드백 제공 방법 등에 익숙해져야 합니다.    

**이 Technical Preview의 알려진 문제:**
-   **Operations Manager 도구 모음 커넥터가 업그레이드되지 않습니다**. OMS 커넥터가 구성된 Technical Preview의 이전 버전에서 업그레이드하는 경우 해당 커넥터는 업그레이드되지 않으며 콘솔에서 더 이상 사용할 수 없게 됩니다. 업그레이드 후에는 [Azure 서비스 마법사를 사용](capabilities-in-technical-preview-1705.md#use-azure-services-wizard-to-configure-a-connection-to-oms)하고 OMS 작업 영역에 대한 연결을 다시 설정해야 합니다.
-   **Sufrace 드라이버가 동기화되지 않습니다**. Surface 드라이버에 대한 지원이 Technical Preview에 대한 Configuration Manager 콘솔의 **새로운 기능**에 표시되어 있지만 이 기능이 예상대로 작동하지 않습니다.
-   **비즈니스용 Windows 업데이트 지연 정책을 만들 수 없습니다**. 비즈니스용 Windows 업데이트 지연 정책을 구성하는 기능이 Technical Preview에 대한 Configuration Manager 콘솔의 **새로운 기능**에 표시되어 있지만 마법사가 열리지 않고 정책을 구성할 수 없습니다.


<!--  Known Issues Template
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="update-reset-tool"></a>업데이트 다시 설정 도구  
Configuration Manager 업데이트를 다시 설정 도구 **CMUpdateReset.exe**를 사용하여 콘솔 내 업데이트의 다운로드 및 복제 문제를 수정할 수 있습니다. 이 도구는 Technical Preview 버전 1705에 포함되어 있습니다. ***\cd.latest\SMSSETUP\TOOLS*** 폴더에서 Technical Preview를 설치한 후 미리 보기 사이트의 사이트 서버에서 이 도구를 찾을 수 있습니다.

Technical Preview 버전 1606 이상에서 이 도구를 사용할 수 있습니다. 광범위한 Technical Preview 업데이트 시나리오에서 이 도구를 사용할 수 있고 다음 Technical Preview를 사용할 수 있을 때까지 기다리지 않아도 되도록 이전 버전 지원이 제공됩니다.

콘솔 내 업데이트를 아직 설치하지 않았으며 오류 상태에 있는 경우 이 도구를 사용할 수 있습니다. 오류 상태은 업데이트 다운로드가 진행 중이지만 중단되었고, 비슷한 크기의 업데이트 패키지에 대한 이전 소요 시간보다 몇 시간 더 오래 걸리는 상황을 의미할 수 있습니다. 업데이트를 자식 기본 사이트로 복제하지 못한 것일 수도 있습니다.  

이 도구를 실행하면 지정한 업데이트에 대해 실행됩니다. 기본적으로 이 도구는 성공적으로 설치되었거나 다운로드된 업데이트를 삭제하지 않습니다.  

### <a name="prerequisites"></a>전제 조건
이 도구를 실행하는 데 사용하는 계정에는 다음 권한이 필요합니다.
-   중앙 관리 사이트 및 계층 구조에 있는 각 기본 사이트의 사이트 데이터베이스에 대한 **읽기** 및 **쓰기** 권한. 이러한 권한을 설정하려면 사용자 계정을 각 사이트의 Configuration Manager 데이터베이스에 **db_datawriter** 및 **db_datareader** [고정 데이터베이스 역할](/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles)의 구성원으로 추가할 수 있습니다. 이 도구는 보조 사이트와는 상호 작용하지 않습니다.
-   계층 구조의 최상위 사이트에 대한 **로컬 관리자**
-   서비스 연결 지점을 호스트하는 컴퓨터의 **로컬 관리자**

다시 설정하려는 업데이트 패키지의 GUID가 필요합니다. GUID를 가져오려면
-   콘솔에서 **관리** > **업데이트 및 서비스**로 이동한 다음 표시 창에서 열 중 하나(예: **상태**)를 마우스 오른쪽 단추로 클릭하고 **패키지 GUID**를 선택합니다. 이렇게 하면 표시에 해당 열이 추가되고 열은 업데이트 패키지 GUID를 표시합니다.

> [!TIP]  
> GUID를 복사하려면 다시 설정하려는 업데이트 패키지에 대한 행을 선택하고 Ctrl+C를 눌러 해당 행을 복사합니다. 복사한 선택 항목을 텍스트 편집기에 붙여 넣은 다음 도구를 실행할 때 명령줄 매개 변수로 사용할 GUID만 복사할 수 있습니다.

### <a name="run-the-tool"></a>도구 실행    
이 도구는 계층의 최상위 사이트에서 실행해야 합니다.

이 도구를 실행할 경우 명령줄 매개 변수를 사용하여 계층 구조의 최상위 계층 사이트에 있는 SQL Server, 사이트 데이터베이스 이름 및 다시 설정하려는 업데이트 패키지의 GUID를 지정합니다. 그러면 이 도구는 업데이트 상태에 따라 액세스해야 하는 추가 서버를 식별합니다.   

업데이트 패키지가 *다운로드 게시* 상태이면 도구는 패키지를 정리하지 않습니다. 선택적으로 force delete 매개 변수를 사용하여 성공적으로 다운로드한 업데이트를 강제로 제거할 수 있습니다(이 항목 뒷부분에 나오는 명령줄 매개 변수 참조).

도구가 실행된 후에 다음 작업을 수행합니다.
-   패키지가 삭제된 경우 최상위 계층 사이트 SMS_Executive 서비스를 다시 시작하고 업데이트를 확인하여 패키지를 다시 다운로드합니다.
-   패키지가 삭제되지 않은 경우 업데이트가 다시 초기화되고 복제 또는 설치가 다시 시작되므로 수행해야 하는 작업은 없습니다.

**명령줄 매개 변수:**  


|                        매개 변수                         |                                                            설명                                                            |
|----------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| **-S &lt;최상위 계층 사이트에 있는 SQL Server의 FQDN>** | *필수* <br> 계층 구조에서 최상위 계층 사이트에 대한 사이트 데이터베이스를 호스트하는 SQL Server의 FQDN을 지정해야 합니다. |
|                **-D &lt;데이터베이스 이름>**                 |                             *필수* <br> 최상위 계층 사이트 데이터베이스의 이름을 지정해야 합니다.                             |
|                 **-P &lt;패키지 GUID>**                 |                        *필수* <br> 다시 설정하려는 업데이트 패키지에 대한 GUID를 지정해야 합니다.                        |
|           **-I &lt;SQL Server 인스턴스 이름>**           |                   *선택 사항* <br> 사이트 데이터베이스를 호스트하는 SQL Server 인스턴스를 식별하는 데 사용합니다.                   |
|                       **-FDELETE**                       |                      *선택 사항* <br> 성공적으로 다운로드한 업데이트 패키지를 강제로 삭제하는 데 사용합니다.                      |

 **예:**  
 일반적인 시나리오에서는 다운로드 문제가 있는 업데이트를 다시 설정하려고 할 것입니다. SQL Server FQDN은 *server1.fabrikam.com*, 사이트 데이터베이스는 *CM_XYZ*, 패키지 GUID는 *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*입니다.  실행: ***CMUpdateReset.exe -S server1.fabrikam.com -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

 좀 더 극단적인 시나리오에서는 문제가 있는 업데이트 패키지를 강제로 삭제하려고 할 수 있습니다. SQL Server FQDN은 *server1.fabrikam.com*, 사이트 데이터베이스는 *CM_XYZ*, 패키지 GUID는 *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*입니다.  실행: ***CMUpdateReset.exe  -FDELETE -S server1.fabrikam.com -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

### <a name="test-the-tool-with-the-technical-preview"></a>Technical Preview에서 도구 테스트  
Technical Preview 버전 1606 이상에서 이 도구를 사용할 수 있습니다. 많은 수의 Technical Preview 업데이트 시나리오에서 이 도구를 사용할 수 있고 다음 Technical Preview 버전을 사용할 수 있을 때까지 기다리지 않아도 되도록 이전 버전 지원이 제공됩니다.

해당 업데이트 이전에 Technical Preview의 업데이트 패키지에 대해 이 도구를 실행하여 필수 구성 요소 검사를 완료합니다. 완료된 필수 구성 요소 검사 상태는 **관리** > **업데이트 및 서비스**에서 패키지에 대한 다음 상태 중 하나로 식별됩니다.  
-   **필수 구성 요소 검사 통과**
-   **필수 구성 요소 검사 통과(경고 있음)**
-   **필수 구성 요소 검사 실패**


## <a name="high-dpi-console-support"></a>높은 DPI 콘솔 지원

이 릴리스에서는 높은 DPI 디바이스(예: Surface Book)에서 볼 때 Configuration Manager 콘솔이 확장되고 UI의 다른 부분을 표시하는 방식의 문제가 수정되었습니다.


## <a name="peer-cache-improvements"></a>피어 캐시 개선
이 Technical Preview부터 피어 캐시는 [더 이상 네트워크 액세스 계정을 사용하여](/sccm/core/plan-design/hierarchy/client-peer-cache) 피어의 다운로드 요청을 인증하지 않습니다.


## <a name="improvements-for-sql-server-always-on-availability-groups"></a>SQL Server Always On 가용성 그룹에 대한 향상된 기능  
이 릴리스에서는 이제 Configuration Manager에서 SQL Server Always On 가용성 그룹의 비동기 커밋 복제본을 사용할 수 있습니다.  즉, 오프사이트(원격) 백업으로 사용하도록 추가 복제본을 가용성 그룹에 추가한 다음 재해 복구 시나리오에서 사용할 수 있습니다.  

- Configuration Manager에서는 비동기 커밋 복제본을 사용하여 동기 복제본을 복구하도록 지원합니다.  이 작업을 수행하는 방법에 대한 자세한 내용은 백업 및 복구 항목에서 [사이트 데이터베이스 복구 옵션](/sccm/core/servers/manage/recover-sites#site-database-recovery-options)을 참조하세요.

- 이 릴리스에서는 비동기 커밋 복제본을 사이트 데이터베이스로 사용하기 위한 장애 조치를 지원하지 않습니다.
  > [!CAUTION]  
  > Configuration Manager는 비동기 커밋 복제본의 상태가 현재 상태인지 확인하지 않으며 [의도적으로 이러한 복제본은 동기화되지 않을 수 있으므로](https://msdn.microsoft.com/library/ff877884(SQL.120).aspx(d=robot)#Availability%20Modes) 비동기 커밋 복제본을 사이트 데이터베이스로 사용하면 사이트와 데이터의 무결성이 손상될 수 있습니다.  

- 사용 중인 SQL Server 버전에서 지원하는 것과 같은 개수 및 유형의 복제본을 가용성 그룹에서 사용할 수 있습니다.   (이전 지원은 두 개의 동기 커밋 복제본으로 제한되었습니다.)

### <a name="configure-an-asynchronous-commit-replica"></a>비동기 커밋 복제본 구성
비동기 복제본을 [Configuration Manager에서 사용하는 가용성 그룹](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database)에 추가하려는 경우 동기 복제본을 구성하는 데 필요한 구성 스크립트를 실행할 필요가 없습니다. (해당 비동기 복제본을 사이트 데이터베이스로 사용하는 것은 지원되지 않기 때문입니다.) 가용성 그룹에 보조 복제본을 추가하는 방법에 대한 자세한 내용은 [SQL Server 설명서](https://msdn.microsoft.com/library/hh213247(v=sql.120).aspx(d=robot))를 참조하세요.

### <a name="use-the-asynchronous-replica-to-recover-your-site"></a>비동기 복제본을 사용하여 사이트 복구
비동기 복제본을 사용하여 사이트 데이터베이스를 복구하기 전에 활성 기본 사이트를 중지하여 사이트 데이터베이스에 대한 추가 쓰기를 방지해야 합니다. 사이트를 중지한 후에 [수동으로 복구된 데이터베이스](/sccm/core/servers/manage/recover-sites#use-a-site-database-that-has-been-manually-recovered)를 사용하는 대신, 비동기 복제본을 사용할 수 있습니다.

사이트를 중지하려면 [계층 유지 관리 도구](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe)를 사용하여 사이트 서버의 핵심 서비스를 중지할 수 있습니다. 명령줄 사용: **Preinst.exe /stopsite**   

사이트를 중지하는것은 사이트 서버에서 사이트 구성 요소 관리자 서비스(sitecomp)를 중지한 후 SMS_Executive 서비스를 중지하는 것과 같습니다.


## <a name="improved-user-notifications-for-office-365-updates"></a>Office 365 업데이트에 대한 향상된 사용자 알림
클라이언트가 Office 365 업데이트를 설치할 때 Office 간편 실행 사용자 환경을 활용하도록 개선되었습니다. 여기에는 팝업 및 앱 내 알림과 카운트다운 환경이 포함됩니다. 이 릴리스 전에는 Office 365 업데이트가 클라이언트로 전송될 때 열려 있던 Office 애플리케이션이 경고 없이 자동으로 닫혔습니다. 이 업데이트 후에는 Office 애플리케이션이 더 이상 예기치 않게 닫히지 않습니다.

### <a name="prerequisites"></a>전제 조건
이 업데이트는 Office 365 ProPlus 클라이언트에 적용됩니다.

### <a name="known-issues"></a>알려진 문제
클라이언트가 처음으로 Office 365 업데이트 할당을 평가하고 업데이트의 기한이 과거 날짜로 예약되어 있거나, 즉시로 예약되어 있거나, 30분 이내로 에약되어 있는 경우 Office 365 사용자 환경이 일관되지 않을 수 있습니다. 예를 들어 클라이언트에서 업데이트에 대해 30분의 카운트다운 대화 상자가 표시될 수 있지만 실제 적용은 카운트다운이 종료되기 전에 시작될 수 있습니다. 이 동작을 방지하려면 다음을 고려합니다.
- 현재 시간보다 최종 기한이 60분 이전으로 예약된 Office 365 업데이트를 배포합니다.
- 업무 외 시간 동안 유지 관리 기간을 구성하거나 배포에 대해 적용 유예 기간을 구성합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
다음 작업을 완료한 다음 리본 메뉴의 **홈** 탭에서 **사용자 의견**을 전송하여 작동 상황을 알려주세요.
- 기한이 현재 시간보다 적어도 60분 이전으로 설정된 상태로 Office 365 업데이트를 클라이언트에 배포합니다. 클라이언트에서 새 동작을 관찰합니다.


## <a name="configure-and-deploy-windows-defender-application-guard-policies"></a>Windows Defender Application Guard 정책 구성 및 배포

[Windows Defender Application Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97)는 운영 체제의 다른 부분에서 액세스할 수 없는 보안 격리된 컨테이너에서 신뢰할 수 없는 웹 사이트를 열어 사용자를 보호하는 새로운 Windows 기능입니다. 이 Technical Preview에서는 구성하는 Configuration Manager 준수 설정을 사용하여 이 기능을 구성한 다음 컬렉션에 배포하기 위한 지원이 추가되었습니다.
이 기능은 64비트 버전의 Windows 10 크리에이터 업데이트에 대한 미리 보기에 릴리스될 예정입니다(코드명: RS2). 이 기능을 지금 테스트하려면 이 업데이트의 미리 보기 버전을 사용하고 있어야 합니다.


### <a name="before-you-start"></a>시작하기 전에

Windows Defender Application Guard 정책을 만들고 배포하려면 정책을 배포하는 Windows 10 디바이스를 네트워크 격리 정책을 사용하여 구성해야 합니다. 자세한 내용은 뒷부분에서 참조되는 블로그 게시물을 참조하세요.
이 기능은 현재 Windows 10 참가자 빌드에서만 작동합니다. 이 기능을 테스트하려면 클라이언트에서 최신 Windows 10 참가자 빌드를 실행하고 있어야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

Windows Defender Application Guard에 대한 기본 사항을 이해하려면 블로그 게시물 읽어야 합니다.

정책을 만들고 사용 가능한 설정을 검색하려면

1.  Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.
2.  **자산 및 준수** 작업 영역에서 **개요** > **Endpoint Protection** > **Windows Defender Application Guard**를 선택합니다.
3.  **홈** 탭의 **만들기** 그룹에서  **만들기**를 클릭합니다.
4.  블로그 게시물을 참조하여 사용 가능한 설정을 찾아보고 구성한 후 기능을 사용해볼 수 있습니다.
5.  작업이 끝나면 마법사를 완료하고 하나 이상의 Windows 10 디바이스에 정책을 배포합니다.

### <a name="further-reading"></a>추가 참고 자료

Windows Defender Application Guard에 대한 자세한 내용은 [이 블로그 게시물]( https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97)을 참조하세요.
또한 Windows Defender Application Guard 독립 실행형 모드에 대한 자세한 내용은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903)을 참조하세요.




## <a name="new-capabilities-for-azure-ad-and-cloud-management"></a>Azure AD 및 클라우드 관리에 대한 새로운 기능

이 릴리스에서는 다음 시나리오를 지원하기 위해 Azure AD를 사용하도록 클라우드 서비스를 구성할 수 있습니다.

- 인터넷에서 수동으로 Configuration Manager 클라이언트를 설치하고 Configuration Manager 사이트에 할당합니다.
- Intune을 사용하여 인터넷의 디바이스에 Configuration Manager 클라이언트를 배포합니다.

### <a name="advantages"></a>장점

클라우드 서비스 및 Azure AD를 사용하면 클라이언트 인증 인증서를 사용할 필요가 없습니다.

컬렉션 및 기타 Configuration Manager 작업에서 사용하기 위해 사이트로 Azure AD 사용자를 검색할 수 있습니다.

### <a name="before-you-start"></a>시작하기 전에

- Azure AD 테넌트가 있어야 합니다.
- 디바이스는 Windows 10을 실행해야 하고 Azure AD에 가입되어야 합니다.  클라이언트는 Azure AD에 가입될 수 있을 뿐만 아니라 도메인에도 가입될 수 있습니다.
- 관리 지점 사이트 시스템 역할에 대한 [기존 필수 구성 요소](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) 외에, 이 사이트 시스템 역할을 호스트하는 컴퓨터에서 **ASP.NET 4.5**(및 이와 함께 자동으로 선택되는 기타 옵션)가 사용되도록 설정되어 있는지도 확인해야 합니다.
- Microsoft Intune을 사용하여 Configuration Manager 클라이언트를 배포하려면
    - 작동하는 Intune 테넌트가 있어야 합니다(Configuration Manager 및 Intune이 연결될 필요는 없음).
    - Intune에서 Configuration Manager 클라이언트를 포함하는 앱을 만들고 배포해야 합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 Intune MDM에서 관리되는 Windows 디바이스에 클라이언트를 설치하는 방법을 참조하세요.
- Configuration Manager를 클라이언트를 배포하려면
    - 하나 이상의 관리 지점이 HTTPS 모드에 대해 구성되어야 합니다.
    - 클라우드 관리 게이트웨이를 설정해야 합니다.


### <a name="set-up-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이 설정

클라이언트가 인증서를 사용하지 않고 인터넷에서 Configuration Manager 사이트에 액세스할 수 있도록 클라우드 관리 게이트웨이를 설정합니다.

다음 항목에서 이 작업을 수행하는 방법에 대한 도움말을 찾을 수 있습니다.

- [Configuration Manager에서 클라우드 관리 게이트웨이 계획](/sccm/core/clients/manage/plan-cloud-management-gateway)
- [Configuration Manager용 클라우드 관리 게이트웨이 설정](/sccm/core/clients/manage/setup-cloud-management-gateway)
- [Configuration Manager에서 클라우드 관리 게이트웨이 모니터링](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway)

### <a name="set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>Configuration Manager 클라우드 서비스에서 Azure 서비스 앱 설정

이렇게 하면 Configuration Manager 사이트가 Azure AD에 연결되므로 이 섹션의 다른 모든 작업을 위해 반드시 필요합니다. 가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

1. Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장한 후 **Azure 서비스**를 클릭합니다.
2. **홈** 탭의 **Azure 서비스** 그룹에서 **Azure 서비스 구성**을 클릭합니다.
3. Azure 서비스 마법사의 **Azure 서비스** 페이지에서 **클라우드 관리**를 선택하여 클라이언트가 Azure AD를 사용하여 계층에서 인증을 받도록 합니다.
4. 마법사의 **일반** 페이지에서 Azure 서비스에 대한 이름 및 설명을 지정합니다.
5. 마법사의 **앱** 페이지에 있는 목록에서 Azure 환경을 선택하고 **찾아보기**를 클릭하여 Azure 서비스를 구성하는 데 사용할 서버 및 클라이언트 앱을 선택합니다.
   - **서버 앱** 창에서 사용할 서버 앱을 선택한 다음 **확인**을 클릭합니다. 서버 앱은 테넌트 ID, 클라이언트 ID 및 클라이언트의 비밀 키를 비롯한 Azure 계정에 대한 구성을 포함하는 Azure 웹앱입니다. 사용 가능한 서버 앱이 없는 경우 다음 중 하나를 사용합니다.
       - **만들기**: 새 서버 앱을 만들려면 **만들기**를 클릭합니다. 앱 및 테넌트의 이름을 입력합니다. 그런 다음 Azure에 로그인하면 Configuration Manager가 Azure에서 사용자를 위해 웹앱을 만듭니다(웹앱에 사용할 클라이언트 ID 및 비밀 키 포함). 나중에 Azure Portal에서 이러한 내용을 확인할 수 있습니다.
       - **가져오기**: Azure 구독에 이미 있는 웹앱을 사용하려면 **가져오기**를 클릭합니다. 앱 및 테넌트의 이름을 입력한 다음 테넌트 ID, 클라이언트 ID 및 Configuration Manager에서 사용하도록 할 Azure 웹앱의 비밀 키를 지정합니다. 정보를 확인한 후에 **확인**을 클릭하여 계속합니다. 이 옵션은 현재 이 Technical Preview에서 사용할 수 없습니다.
   - 클라이언트 앱에 대해 동일한 프로세스를 반복합니다.

   포털에서 올바른 권한을 설정하려면 애플리케이션 가져오기를 사용할 때 *디렉터리 데이터 읽기* 애플리케이션 권한을 부여해야 합니다. 애플리케이션 만들기를 사용하면 애플리케이션에 대해 사용 권한이 자동으로 만들어지지만 Azure Portal에서 여전히 애플리케이션에 동의해야 합니다.
6. 마법사의 **검색** 페이지에서 필요에 따라 **Azure Active Directory 사용자 검색을 사용하도록 설정**하고 **설정**을 클릭합니다.
   **Azure AD 사용자 검색 설정** 대화 상자에서 검색 일정을 구성합니다. 또한 Azure AD에서 새 계정 또는 변경된 계정만 확인하는 델타 검색을 사용하도록 설정할 수도 있습니다.
7. 마법사를 완료합니다.

이제 Configuration Manager 사이트가 Azure AD에 연결되었습니다.


### <a name="install-the-cm-client-from-the-internet"></a>인터넷에서 CM 클라이언트 설치

시작 하기 전에 클라이언트를 설치하려는 디바이스에 클라이언트 설치 원본 파일이 로컬로 저장되어 있는지 확인합니다.
그런 다음 [Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual)의 지침에 따라 다음 설치 명령줄을 사용합니다(이 예제의 값을 고유한 값으로 대체).

**ccmsetup.exe /NoCrlCheck /Source:C:\CLIENT  CCMHOSTNAME=SCCMPROXYCONTOSO.CLOUDAPP.NET/CCM_Proxy_ServerAuth/72457598037527932 SMSSiteCode=HEC AADTENANTID=780433B5-E05E-4B7D-BFD1-E8013911E543 AADTENANTNAME=contoso  AADCLIENTAPPID=\<GUID> AADRESOURCEURI=<https://contososerver>**

- **/NoCrlCheck**: 관리 지점 또는 클라우드 관리 게이트웨이에서 비공용 서버 인증서를 사용하는 경우 클라이언트는 CRL 위치를 연결하지 못할 수 있습니다.
- **/Source**: 로컬 폴더:   클라이언트 설치 파일의 위치입니다.
- **CCMHOSTNAME**: 인터넷 관리 지점의 이름입니다. 관리되는 클라이언트의 명령 프롬프트에서 **gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate**를 실행하여 이 이름을 찾을 수 있습니다.
- **SMSMP**: 조회 관리 지점의 이름으로, 인트라넷에 있을 수 있습니다.
- **SMSSiteCode**: Configuration Manager 사이트의 사이트 코드입니다.
- **AADTENANTID**, **AADTENANTNAME**: Configuration Manager에 연결된 Azure AD 테넌트의 ID 및 이름입니다. Azure AD에 가입된 디바이스의 명령 프롬프트에서 dsregcmd.exe /status를 실행하여 찾을 수 있습니다.
- **AADCLIENTAPPID**: Azure AD 클라이언트 앱 ID입니다. 이를 찾으려면 [포털을 사용하여 리소스에 액세스할 수 있는 Azure Active Directory 애플리케이션 및 서비스 사용자 만들기](https://docs.microsoft.com/azure/active-directory/develop/howto-create-service-principal-portal#get-values-for-signing-in)를 참조하세요.
- **AADResourceUri**: 등록된 Azure AD 서버 앱의 식별자 URI입니다.

## <a name="use-azure-services-wizard-to-configure-a-connection-to-oms"></a>Azure 서비스 마법사를 사용하여 OMS에 대한 연결 구성
1705 Technical Preview 릴리스부터 **Azure 서비스 마법사**를 사용하여 Configuration Manager에서 OMS(Operations Management Suite) 클라우드 서비스에 대한 연결을 구성합니다. 마법사는 이 연결을 구성하기 위한 이전 워크플로를 대신합니다.

-   이 마법사는 OMS, WSfB(비즈니스용 Windows 스토어), Azure AD(Azure Active Directory)와 같은 Configuration Manager용 클라우드 서비스를 구성하는 데 사용됩니다.  

-   Configuration Manager는 [Log Analytics](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) 또는 [업그레이드 준비](/sccm/core/clients/manage/upgrade/upgrade-analytics)와 같은 기능을 위해 OMS에 연결합니다.

### <a name="prerequisites-for-the-oms-connector"></a>OMS 커넥터에 대한 필수 구성 요소
OMS에 대한 연결을 구성하기 위한 필수 구성 요소는 [혀냊 분기 버전 1702에 대해 문서화](/sccm/core/clients/manage/sync-data-log-analytics)된 내용에서 달라졌습니다. 이 정보는 여기에도 설명되어 있습니다.  

-   OMS에 대한 Configuration Manager 사용 권한 제공

-   OMS 커넥터는 [서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)을 [온라인 모드](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes)에서 호스트하는 컴퓨터에 설치해야 합니다.

-   OMS 커넥터와 함께 서비스 연결 지점에 설치된 OMS에 대해 Microsoft Monitoring Agent를 설치해야 합니다. Agent 및 OMS 커넥터는 동일한 **OMS 작업 영역**을 사용하도록 구성해야 합니다. 에이전트를 설치하려면 OMS 문서에서 [에이전트 다운로드 및 설치](/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent)를 참조하세요.
-   커넥터와 에이전트를 설치한 후 Configuration Manager 데이터를 사용하도록 OMS를 구성해야 합니다. 이렇게 하려면 OMS 포털에서 [Configuration Manager 컬렉션을 가져옵니다](/azure/log-analytics/log-analytics-sccm#import-collections).

### <a name="use-the-azure-services-wizard-to-configure-the-connection-to-oms"></a>Azure 서비스 마법사를 사용하여 OMS에 대한 연결 구성

1.  콘솔에서 **관리** > **개요** > **클라우드 서비스** > **Azure 서비스**로 이동한 후 리본 메뉴의 **홈** 탭에서 **Azure 서비스 구성**을 선택하여 **Azure 서비스 마법사**를 시작합니다.

2.  **Azure 서비스** 페이지에서 Operation Management Suite 클라우드 서비스를 선택합니다. **Azure 서비스 이름**에 이름을 입력하고 원하는 경우 선택적 설명을 입력한 후 **다음**을 클릭합니다.

3.  **앱** 페이지에서 Azure 환경(기술 미리 보기는 퍼블릭 클라우드만 지원함)을 지정합니다. 그런 후 **찾아보기**를 클릭하여 서버 앱 창을 엽니다.

4.  웹앱을 선택합니다.

    -   **가져오기**: Azure 구독에 이미 있는 웹앱을 사용하려면 **가져오기**를 클릭합니다. 앱 및 테넌트의 이름을 입력한 다음 테넌트 ID, 클라이언트 ID 및 Configuration Manager에서 사용하도록 할 Azure 웹앱의 비밀 키를 지정합니다. 정보를 **확인**한 후 **확인**을 클릭하여 계속합니다.   

    > [!NOTE]   
    > 이 미리 보기에서 OMS를 구성하는 경우 OMS는 웹앱에 대해서만 *import* 함수를 지원합니다. 새 웹앱을 만드는 것은 지원되지 않습니다. 마찬가지로 OMS에 대해 기존 앱을 재사용할 수 없습니다.

5.  다른 모든 절차를 성공적으로 완료한 경우 **OMS 연결 구성** 화면의 정보가 이 페이지에 자동으로 나타납니다. 연결 설정에 대한 정보가 **Azure 구독**, **Azure 리소스 그룹** 및 **Operations Management Suite 작업 영역**에 대해 나타납니다.

6.  마법사는 사용자가 입력한 정보를 사용하여 OMS 서비스에 연결합니다. OMS와 동기화하려는 디바이스 컬렉션을 선택하고 **추가**를 클릭합니다.

7.  **요약** 화면에서 연결 설정을 확인하고 **다음**을 선택합니다. **진행률** 화면에 연결 상태가 표시되며 **완료**여야 합니다.

8.  마법사가 완료된 후 Configuration Manager 콘솔에는 **Operation Management Suite**가 **클라우드 서비스 유형**으로 표시됩니다.
