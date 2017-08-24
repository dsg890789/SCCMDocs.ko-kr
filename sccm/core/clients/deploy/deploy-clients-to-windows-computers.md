---
title: "Windows 클라이언트 배포 | Microsoft 문서"
description: "System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 08/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
caps.latest.revision: "13"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 9ac54136b93ee366c16cafe89036a79e808980dc
ms.sourcegitcommit: 06aef618f72c700f8a716a43fb8eedf97c62a72b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/21/2017
---
# <a name="how-to-deploy-clients-to-windows-computers-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 클라이언트를 설치하기 전에 모든 [필수 구성 요소](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md)가 준비되어 있어야 하고 필요한 모든 구성을 완료해야 합니다.   

##  <a name="BKMK_ClientPush"></a> 클라이언트 푸시를 사용하여 클라이언트를 설치하는 방법  

사이트에 대한 클라이언트 강제 설치를 구성할 수 있으며, 사이트의 구성된 경계가 경계 그룹으로 구성된 경우 해당 경계 내에서 검색된 컴퓨터에서 클라이언트 설치가 자동으로 실행됩니다. 또는 특정 컬렉션 또는 컬렉션 내의 리소스에 대해 클라이언트 강제 설치 마법사를 실행하여 클라이언트 강제 설치를 시작할 수 있습니다.  

클라이언트 강제 설치 마법사를 사용하면 결과를 [쿼리](../../../core/servers/manage/queries-technical-reference.md)하여 Configuration Manager 클라이언트를 설치할 수도 있습니다. 설치가 제대로 되려면 쿼리에서 반환되는 항목 중 하나가 **시스템 리소스** 클래스의 **ResourceID** 특성이어야 합니다.   

사이트 서버에서 클라이언트 컴퓨터에 연결하거나 설치 프로세스를 시작할 수 없는 경우 최대 7일 동안 1시간마다 자동으로 설치 시도를 반복합니다.  

클라이언트 설치 프로세스를 추적하려면 클라이언트를 설치하기 전에 대체 상태 지점 사이트 시스템을 설치합니다. 대체 상태 지점을 설치하면 클라이언트 강제 설치 방법으로 클라이언트를 설치할 때 자동으로 클라이언트에 할당됩니다. 클라이언트 배포 및 할당 보고서를 보고 클라이언트 설치 진행률을 추적합니다. 

클라이언트 로그 파일은 더 자세한 문제 해결 정보를 제공하며, 로그 파일을 보기 위해 대체 상태 지점이 필요하지 않습니다. 예를 들어 사이트 서버의 CM.log 파일은 사이트 서버가 컴퓨터에 연결할 때 발생하는 문제를 기록하고, 클라이언트의 CCMSetup.log 파일은 설치 프로세스를 기록합니다.  

> [!IMPORTANT]  
>  클라이언트 강제 설치에 성공하려면 모든 필수 구성 요소가 준비되어 있어야 합니다. 다음은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md)의 "설치 방법 종속성" 섹션에 나열되어 있습니다.  

### <a name="to-configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>검색된 컴퓨터에 대해 자동으로 클라이언트 강제 설치를 사용하도록 사이트를 구성하려면

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 선택합니다.  

3.  자동 사이트 전체 클라이언트 강제 설치를 구성하려는 사이트를 선택합니다.  

4.  **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정** > **클라이언트 강제 설치**를 선택합니다.  

5.  **클라이언트 강제 설치 속성** 대화 상자의 **일반** 탭에서 **자동 사이트 전체 클라이언트 강제 설치 사용**을 선택합니다. Configuration Manager에서 클라이언트 소프트웨어 강제 설치를 수행해야 할 시스템 유형을 선택합니다.  

6.  도메인 컨트롤러에 클라이언트 소프트웨어를 설치할지 여부를 선택합니다.  

7.  **계정** 탭에서 Configuration Manager가 컴퓨터에 연결하여 클라이언트 소프트웨어를 설치할 때 사용할 계정을 하나 이상 지정합니다. **만들기** 아이콘을 클릭하고 **사용자 이름**과 **암호**(38자 이하)를 입력한 다음 암호를 확인하고 **확인**을 클릭합니다. 클라이언트 강제 설치 계정을 하나 이상 지정해야 합니다. 이 계정에는 클라이언트를 설치할 모든 컴퓨터에 대한 로컬 관리자 권한이 있어야 합니다. 클라이언트 강제 설치 계정을 지정하지 않으면 Configuration Manager에서 사이트 시스템 컴퓨터 계정을 사용하려고 합니다. 이 경우 도메인 간 클라이언트 강제 설치를 할 수 없습니다.  
    > [!NOTE]  
    >  보조 사이트에서 클라이언트 강제 설치 방법을 사용하려면 클라이언트 강제 설치를 시작할 보조 사이트에서 이 계정을 지정해야 합니다.  
    >   
    >  클라이언트 강제 설치 계정에 대한 자세한 내용은 다음 절차인 "클라이언트 강제 설치 마법사를 사용하려면"을 참조하세요.  
8.  **설치 속성** 탭을 완료합니다.

     Configuration Manager용으로 스키마가 확장되고 설치 속성 없이 CCMSetup을 실행하는 클라이언트 설치에서 이 스키마를 읽으면 이 탭에서 지정한 [클라이언트 설치 속성](../../../core/clients/deploy/about-client-installation-properties.md)이 Active Directory Domain Services에 게시됩니다.  

    > [!NOTE]  
    >  보조 사이트에서 클라이언트 강제 설치를 사용하도록 설정한 경우 SMSSITECODE 속성을 해당 부모 기본 사이트의 Configuration Manager 사이트 이름으로 설정해야 합니다. Active Directory 스키마가 Configuration Manager용으로 확장되면 이 속성을 AUTO로 설정하여 자동으로 올바른 사이트 할당을 찾도록 할 수도 있습니다.  

### <a name="to-use-the-client-push-installation-wizard"></a>클라이언트 강제 설치 마법사를 사용하려면

1.  Configuration Manager 콘솔에서 **관리** >  **사이트 구성** > **사이트**를 선택합니다.  

3.  자동 사이트 전체 클라이언트 강제 설치를 구성하려는 사이트를 선택합니다.  

4.  **홈** 탭 > **설정** 그룹에서 **클라이언트 설치 설정** > **클라이언트 강제 설치**를 선택합니다.  

5.  **설치 속성** 탭을 완료합니다.  

     Configuration Manager용으로 스키마가 확장되고 설치 속성 없이 CCMSetup을 실행하는 클라이언트 설치에서 이 스키마를 읽으면 이 탭에서 지정한 [클라이언트 설치 속성](../../../core/clients/deploy/about-client-installation-properties.md)이 Active Directory Domain Services에 게시됩니다.  

6.  Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.  

7.  **자산 및 호환성** 작업 영역에서 하나 이상의 컴퓨터나 컴퓨터 컬렉션을 선택합니다.  

8.  **홈** 탭에서 다음 중 하나를 선택합니다.  

    -   하나 또는 여러 대의 컴퓨터에 클라이언트를 설치하려면 **장치** 그룹에서 **클라이언트 설치**를 선택합니다.  

    -   컴퓨터의 컬렉션에 클라이언트를 설치하려면 **컬렉션** 그룹에서 **클라이언트 설치**를 선택합니다.  

9. **클라이언트 설치 마법사**의 **시작하기 전에** 페이지에서 정보를 검토하고 **다음**을 선택합니다.  

10. **설치 옵션** 페이지를 완료합니다.  

11. 설치 설정을 검토한 후 마법사를 닫습니다.  

> [!NOTE]  
>  클라이언트 강제 설치를 사용할 수 있도록 사이트를 구성하지 않은 경우에도 이 마법사를 사용하여 클라이언트를 설치할 수 있습니다.  

##  <a name="BKMK_ClientSUP"></a> 소프트웨어 업데이트 기반 설치를 사용하여 클라이언트를 설치하는 방법  
 소프트웨어 업데이트 기반 설치는 클라이언트를 소프트웨어 업데이트 지점에 소프트웨어 업데이트로 게시합니다. 처음 설치하거나 업그레이드할 경우 이 방법을 사용합니다.  

 컴퓨터에 클라이언트가 설치된 경우 Configuration Manager에서 소프트웨어 업데이트를 받을 소프트웨어 업데이트 지점 서버 이름과 포트가 포함된 클라이언트 정책을 클라이언트에 제공합니다.   

> [!IMPORTANT]  
>  소프트웨어 업데이트 기반 설치를 사용하려면 클라이언트 설치와 소프트웨어 업데이트에 동일한 WSUS(Windows Server Update Services) 서버를 사용해야 합니다. 이 서버는 기본 사이트의 활성 소프트웨어 업데이트 지점이어야 합니다. 자세한 내용은 [소프트웨어 업데이트 지점 설치](../../../sum/get-started/install-a-software-update-point.md)를 참조하세요.  

컴퓨터에 Configuration Manager 클라이언트가 설치되지 않은 경우 Active Directory Domain Services에서 GPO(그룹 정책 개체)를 구성하고 할당하여 소프트웨어 업데이트 지점 서버 이름을 지정해야 합니다.  

소프트웨어 업데이트 기반 클라이언트 설치에는 명령줄 속성을 추가할 수 없습니다. Configuration Manager용으로 Active Directory 스키마를 확장한 경우 클라이언트 컴퓨터에서 설치할 때 자동으로 Active Directory Domain Services에서 설치 속성을 쿼리합니다.  

Active Directory 스키마를 확장하지 않은 경우 그룹 정책을 사용하여 클라이언트 설치 설정을 사이트의 컴퓨터에 프로비전할 수 있습니다. 이러한 설정은 모든 소프트웨어 업데이트 기반 클라이언트 설치에 자동으로 적용됩니다. 자세한 내용은 [클라이언트 설치 속성(그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치)을 프로비전하는 방법](#BKMK_Provision) 및 [System Center Configuration Manager에서 사이트에 클라이언트를 할당하는 방법](../../../core/clients/deploy/assign-clients-to-a-site.md)을 참조하세요.  

Configuration Manager 클라이언트가 없는 컴퓨터에서 클라이언트 설치 및 소프트웨어 업데이트를 위한 소프트웨어 업데이트 지점을 사용하고 클라이언트 소프트웨어를 소프트웨어 업데이트 지점에 게시하도록 구성하려면 다음 절차를 수행하세요.  

> [!NOTE]  
>  컴퓨터가 이전 소프트웨어 설치를 수행한 후 다시 시작을 보류 중인 상태인 경우 소프트웨어 업데이트 기반 클라이언트 설치 시 컴퓨터가 다시 시작될 수 있습니다.  

### <a name="configure-a-group-policy-object-in-active-directory-domain-services-to-specify-the-software-update-point-for-client-installation-and-software-updates"></a>클라이언트 설치 및 소프트웨어 업데이트를 위한 소프트웨어 업데이트 지점을 지정하도록 Active Directory Domain Services의 그룹 정책 개체를 구성합니다.  

1.  그룹 정책 관리 콘솔을 사용하여 새 그룹 정책 개체나 기존 그룹 정책 개체를 엽니다.  

2.  콘솔에서 **컴퓨터 구성**, **관리 템플릿**, **Windows 구성 요소**를 차례로 확장하고 **Windows Update**를 선택합니다.  

3.  **인트라넷 Microsoft 업데이트 서비스 위치 지정** 설정의 속성을 열고 **사용**을 선택합니다.  

4.  **인트라넷 업데이트 서비스에서 업데이트를 검색하도록 설정** 상자에서 소프트웨어 업데이트 지점 서버의 이름과 포트를 지정합니다.  

    -   FQDN(정규화된 도메인 이름)을 사용하도록 Configuration Manager 사이트 시스템을 구성한 경우 FQDN 형식을 사용합니다.  

    -   FQDN을 사용하도록 Configuration Manager 사이트 시스템을 구성하지 않은 경우 짧은 이름 형식을 사용합니다.  

    > [!NOTE]  
    >  포트 번호를 확인하려면 [System Center Configuration Manager에서 WSUS에 사용되는 포트 설정을 확인하는 방법](../../../sum/plan-design/plan-for-software-updates.md)을 참조하세요.  

     예: **http://server1.contoso.com:8530**  

5.  **인트라넷 통계 서버 설정** 상자에서 인트라넷 통계 서버 이름을 지정합니다. 소프트웨어 업데이트 지점 서버와 동일하지 않아도 되며 동일한 서버인 경우 형식이 일치하지 않아도 됩니다.  

6.  클라이언트를 설치하고 소프트웨어 업데이트를 받을 컴퓨터에 그룹 정책 개체를 할당합니다.  

### <a name="to-publish-the-configuration-manager-client-to-the-software-update-point"></a>소프트웨어 업데이트 지점에 Configuration Manager 클라이언트를 게시하려면  

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 클릭합니다.  

3.  소프트웨어 업데이트 기반 클라이언트 설치를 구성하려는 사이트를 선택합니다.  

4.  **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정**을 선택한 다음 **소프트웨어 업데이트 기반 클라이언트 설치**를 선택합니다.  

5.  **소프트웨어 업데이트 기반 클라이언트 설치 사용**을 선택합니다.  

6.  Configuration Manager 사이트 서버의 클라이언트 소프트웨어가 소프트웨어 업데이트 지점의 버전보다 최신 버전이면 **최신 버전의 클라이언트 패키지 검색** 대화 상자가 열립니다. **예**를 클릭하여 최신 버전을 게시합니다.  

    > [!NOTE]  
    >  이전에 소프트웨어 업데이트 지점에 클라이언트 소프트웨어를 게시하지 않은 경우에는 이 상자가 비어 있습니다.  

새 버전이 있으면 Configuration Manager 클라이언트의 소프트웨어 업데이트가 자동으로 업데이트되지 않습니다. 새 클라이언트 버전이 포함된 사이트를 업그레이드할 경우 이 절차를 반복하고 6단계에서 **예** 를 클릭해야 합니다.  

##  <a name="BKMK_ClientGP"></a> 그룹 정책을 사용하여 클라이언트를 설치하는 방법  
 Active Directory Domain Services의 그룹 정책을 사용하면 엔터프라이즈 환경 내 컴퓨터에 설치할 Configuration Manager 클라이언트를 게시하거나 할당할 수 있습니다. 컴퓨터가 시작되면 클라이언트가 설치됩니다. 그룹 정책을 사용할 경우 제어판의 **프로그램 추가/제거**에 사용자가 설치할 클라이언트가 표시됩니다.  

 그룹 정책 기반 설치에는 Windows Installer 패키지(CCMSetup.msi)를 사용합니다. 이 파일은 Configuration Manager 사이트 서버의 **&lt;ConfigMgr 설치 디렉터리\>\bin\i386** 폴더에 있습니다. 이 파일에 속성을 추가하여 설치 동작을 수정할 수 없습니다.  

> [!IMPORTANT]  
>  클라이언트 설치 파일에 액세스하려면 관리자 권한이 있어야 합니다.  

-   Active Directory 스키마가 Configuration Manager에 대해 확장되고 **사이트 속성** 대화 상자의 **고급** 탭에서 **Active Directory Domain Services에 이 사이트 게시**를 선택한 경우 클라이언트 컴퓨터는 Active Directory Domain Services에서 설치 속성을 자동으로 검색합니다. 게시되는 설치 속성에 대한 자세한 내용은 [System Center Configuration Manager에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md)를 참조하세요.  

-   Active Directory 스키마가 확장되지 않은 경우 이 항목의 [클라이언트 설치 속성을 프로비전하는 방법(그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치)](#BKMK_Provision) 절차에 따라 설치 속성을 컴퓨터 레지스트리에 저장할 수 있습니다. 이 설치 속성은 클라이언트가 설치될 때 사용됩니다.  

Active Directory Domain Services에서 그룹 정책을 사용하여 소프트웨어를 설치하는 방법에 대한 자세한 내용은 해당 Windows Server 설명서를 참조하세요.  

##  <a name="BKMK_Manual"></a> 수동으로 클라이언트를 설치하는 방법  
 CCMSetup.exe 프로그램을 사용하면 기업 내 컴퓨터에 클라이언트 소프트웨어를 수동으로 설치할 수 있습니다. 이 프로그램과 해당 지원 파일은 사이트 서버 및 사이트 내 관리 지점에서 Configuration Manager 설치 폴더의 **Client** 폴더에서 찾을 수 있습니다. 이 폴더는 네트워크에서  

 \\\\*&lt;사이트 서버 이름\>*\SMS_*&lt;사이트 코드\>*\Client\  

 여기서 *&lt;사이트 서버 이름\>*은 관리 지점을 호스트하는 서버 중 하나의 이름이고, *&lt;사이트 코드\>*는 클라이언트가 속하는 기본 사이트의 코드입니다.  클라이언트의 명령줄에서 CCMSetup.exe를 실행하려면 네트워크 드라이브를 이 위치에 매핑하고 명령을 실행해야 합니다.  

> [!IMPORTANT]  
>  클라이언트 설치 파일에 액세스하려면 관리자 권한이 있어야 합니다.  

 CCMSetup.exe는 필요한 모든 필수 구성 요소를 클라이언트 컴퓨터에 복사하고 Windows Installer 패키지(Client.msi)를 호출하여 클라이언트를 설치합니다. Client.msi는 직접 실행할 수 없습니다.  

 CCMSetup.exe 및 Client.msi 모두에 대해 명령줄 속성을 지정하여 클라이언트 설치의 동작을 수정할 수 있습니다. Client.msi 속성을 지정하기 전에 CCMSetup 속성(**/**로 시작하는 속성)을 지정해야 합니다. 예를 들면 다음과 같습니다.  

```  
CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01  
```  
다음 속성을 사용하여 클라이언트를 설치합니다.  

|속성|설명|  
|--------------|-----------------|  
|**/mp:SMSMP01**|이 CCMSetup 속성은 관리 지점 SMSMP01이 필수 클라이언트 설치 파일을 다운로드하도록 지정합니다.|  
|**/logon**|이 CCMSetup 속성은 컴퓨터에서 기존 Configuration Manager 클라이언트가 발견되면 설치를 중지하도록 지정합니다.|  
|**SMSSITECODE=AUTO**|이 Client.msi 속성은 클라이언트가 사용할 Configuration Manager 사이트 코드의 검색을 시도하도록 지정합니다. 예를 들어 클라이언트는 Active Directory Domain Services를 사용하여 검색을 시도할 수 있습니다.|  
|**FSP=SMSFP01**|이 Client.msi 속성은 클라이언트 컴퓨터에서 보낸 상태 메시지를 수신하는 데 대체 상태 지점 SMSFP01을 사용할 것을 지정합니다.|  

 모든 CCMSetup.exe 속성에 대한 자세한 내용은 [System Center Configuration Manager 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

### <a name="examples"></a>예
 이 예제는 인트라넷상의 Active Directory 클라이언트에 대한 것이며 다음 값을 사용하여 사이트의 다양한 측면을 나타냅니다.  

 **MPSERVER** = 관리 지점을 호스트하는 서버   
**FSPSERVER** = 대체 상태 지점을 호스트하는 서버  
**ABC** = 사이트 코드  
**contoso.com** = 도메인 이름  

 모든 사이트 시스템 서버에는 인트라넷 FQDN이 구성되어 있고 사이트는 클라이언트의 Active Directory 포리스트에 게시됩니다.  

 클라이언트 컴퓨터에서 로컬 관리자로 로그온하고 드라이브(z:)를 \\\MPSERVER\SMS_ABC\Client에 매핑하고 명령 프롬프트를 z 드라이브로 전환한 후 다음 명령 중 하나를 실행합니다.  

 **예제 1:**  

```  
CCMSetup.exe  
```  
이 예제에서는 클라이언트를 추가 속성 없이 설치하므로 클라이언트는 Active Directory Domain Services에 게시된 클라이언트 설치 속성을 사용하여 자동으로 구성됩니다. 예를 들어 클라이언트에는 사이트 코드, 관리 지점, 대체 상태 지점, HTTPS만 사용하여 통신해야 하는지 여부 등이 자동으로 구성됩니다. 사이트 코드를 사용하려면 클라이언트의 네트워크 위치는 클라이언트 할당을 위해 구성된 경계 그룹에 포함되어야 합니다. Active Directory 클라이언트에 대해 자동으로 구성 가능한 클라이언트 설치 속성에 대한 자세한 내용은 [System Center Configuration Manager에서 Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md)를 참조하세요.  

 **예제 2:**  

```  
CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com  
```  
이 예제는 Active Directory Domain Services에서 제공할 수 있는 자동 구성을 재정의하며 여기서는 클라이언트의 네트워크 위치가 클라이언트 할당을 위해 구성된 경계 그룹에 포함될 필요가 없습니다. 대신 설치 과정에서 사이트, 인트라넷 관리 지점, 인터넷 기반 관리 지점, 대체 상태 지점 등이 지정됩니다. 대체 상태 지점은 인터넷의 연결을 승인하는 역할을 하고 가장 긴 유효 기간을 갖는 클라이언트 PKI 인증서(사용 가능한 경우)를 사용하도록 지원합니다.  

##  <a name="BKMK_ClientLogonScript"></a> 로그온 스크립트를 사용하여 클라이언트를 설치하는 방법  
 Configuration Manager는 Configuration Manager 클라이언트 소프트웨어를 설치하기 위한 로그온 스크립트를 지원합니다. 로그온 스크립트에서 **CCMSetup.exe** 프로그램 파일을 사용하면 클라이언트 설치를 트리거할 수 있습니다.  

 로그온 스크립트 설치에는 수동 클라이언트 설치와 동일한 방법이 사용됩니다. CCMSsetup.exe에 대해 **/logon** 설치 속성을 지정하면 컴퓨터에 다른 클라이언트 버전이 이미 설치된 경우 클라이언트가 설치되지 않습니다. 따라서 로그온 스크립트가 실행될 때마다 클라이언트가 다시 설치되지는 않습니다.  

 **/Source** 속성을 사용하는 설치 소스를 지정하지 않았고 **/MP** 속성으로 설치 파일을 가져올 관리 지점을 지정하지 않은 경우, CCMSetup.exe를 실행하면 Active Directory Domain Services를 검색하여 관리 지점을 찾을 수 있습니다. 단, 스키마가 Configuration Manager에 대해 확장되고 사이트가 Active Directory Domain Services에 게시된 경우에 한합니다. 또는 클라이언트는 DNS 또는 WINS를 사용하여 관리 지점을 찾을 수 있습니다.  

##  <a name="BKMK_ClientApp"></a> 패키지 및 프로그램을 사용하여 클라이언트를 설치하는 방법  
 Configuration Manager를 사용하면 계층 내 선택한 컴퓨터에 대해 클라이언트 소프트웨어를 업그레이드하는 패키지 및 프로그램을 만들어 배포할 수 있습니다. 패키지 속성이 일반적으로 사용되는 값으로 채워지는 패키지 정의 파일은 Configuration Manager와 함께 제공됩니다. 추가 명령줄 속성을 지정하면 클라이언트 설치의 동작을 사용자 지정할 수 있습니다.  

> [!NOTE]  
>  이 방법으로는 Configuration Manager 2007 클라이언트를 업그레이드할 수 없습니다. 대신, 최신 버전의 클라이언트가 포함된 패키지를 자동으로 만들고 배포하는 자동 클라이언트 업그레이드를 사용해야 합니다. 자세한 내용은 [System Center Configuration Manager에서 클라이언트 업그레이드](../../../core/clients/manage/upgrade/upgrade-clients.md)를 참조하세요.  
>   
>  Configuration Manager 클라이언트의 이전 버전에서 마이그레이션하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 마이그레이션 전략 계획](../../../core/migration/planning-a-client-migration-strategy.md)을 참조하세요.  

 
###<a name="to-create-a-package-and-program-for-the-client-software"></a>클라이언트 소프트웨어용 패키지 및 프로그램을 만들려면  

클라이언트 소프트웨어를 업그레이드하려면 다음 절차를 사용하여 Configuration Manager 클라이언트 컴퓨터에 배포할 수 있는 Configuration Manager 패키지 및 프로그램을 만듭니다.  

1.  Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **응용 프로그램 관리** > **패키지**를 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **정의에서 패키지 만들기**를 선택합니다.  

4.  마법사의 **패키지 정의** 페이지에서 **게시자** 드롭다운 목록에 있는 **Microsoft**를 선택하고 **패키지 정의** 목록에서 **Configuration Manager 클라이언트 업그레이드**를 선택합니다.  

5.  **원본 파일** 페이지에서 **항상 원본 폴더에서 파일 가져오기**를 선택합니다.  

6.  **원본 폴더** 페이지에서 **네트워크 경로(UNC 이름)**를 선택하고 클라이언트 설치 파일이 포함된 컴퓨터 및 폴더의 네트워크 경로를 입력합니다.  

    > [!NOTE]  
    >  Configuration Manager 배포가 실행되는 컴퓨터에는 지정된 네트워크 폴더에 대한 액세스 권한이 있어야 합니다. 그렇지 않으면 설치에 실패합니다.  

    클라이언트 설치 속성을 변경하려면 **Configuration Manager 에이전트 자동 업그레이드 속성** 프로그램 대화 상자의 **일반** 탭에서 CCMSetup.exe 명령줄 매개 변수를 수정하면 됩니다. 기본 설치 속성은 **/noservice SMSSITECODE=AUTO**입니다.  

9. 클라이언트 업그레이드 패키지를 호스트할 모든 배포 지점에 패키지를 배포합니다. 그런 다음, 업그레이드할 클라이언트를 포함하는 컴퓨터 컬렉션에 패키지를 배포할 수 있습니다.  

## <a name="how-to-install-clients-to-intune-mdm-managed-windows-devices"></a>Intune MDM에서 관리되는 Windows 장치에 클라이언트를 설치하는 방법

Microsoft Intune에 등록된 컴퓨터에 클라이언트 설치 파일을 배포할 수 있습니다. 

클라이언트 소프트웨어가 설치된 후 장치를 관리되는 상태로 유지하려면 장치가 회사 네트워크에서 Configuration Manager 사이트 경계 내에 있어야 합니다. 

> [!NOTE]
> 클라이언트 소프트웨어가 설치된 후 Intune에서 장치 등록이 취소됩니다.

### <a name="to-install-clients-with-intune"></a>Intune을 사용하여 클라이언트를 설치하려면

1. Intune에서 Configuration Manager 클라이언트 설치 파일 **ccmsetup.msi**가 포함된 [앱을 만듭니다](/intune/deploy-use/add-apps-for-mobile-devices-in-microsoft-intune).

2. Intune 소프트웨어 게시자에서 다음 명령줄 매개 변수를 사용합니다.

  **CCMSETUPCMD="/MP:&lt;관리 지점의 FQDN> SMSMP=&lt;관리 지점의 FQDN> SMSSITECODE=&lt;사이트 코드> DNSSUFFIX=&lt;관리 지점의 DNS 접미사>"**

3. 등록된 Windows 컴퓨터에 [앱을 배포](/intune/deploy-use/deploy-apps-in-microsoft-intune)합니다.

##  <a name="BKMK_ClientImage"></a> 컴퓨터 이미지를 사용하여 클라이언트를 설치하는 방법  
Configuration Manager 클라이언트 소프트웨어를 다른 컴퓨터를 이미징하는 데 사용할 마스터 이미지 컴퓨터에 사전 설치할 수 있습니다.   

### <a name="to-prepare-the-client-computer-for-imaging"></a>이미징에 대한 클라이언트 컴퓨터를 준비하려면  

1.  마스터 이미지 컴퓨터에 Configuration Manager 클라이언트 소프트웨어를 수동으로 설치합니다. 자세한 내용은 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual)을 참조하세요.  

    > [!IMPORTANT]  
    >  CCMSetup.exe 명령줄 속성에서 클라이언트에 대한 Configuration Manager 사이트 코드를 지정하지 마세요.  

2.  명령 프롬프트에서 **net stop ccmexec** 을 입력하여 **SMS Agent Host** 서비스(Ccmexec.exe)가 마스터 이미지 컴퓨터에서 실행되지 않도록 합니다.
3.  참조 컴퓨터의 **Windows** 폴더에서 **SMSCFG.INI** 파일을 삭제합니다.  
3.  마스터 이미지 컴퓨터에서 로컬 컴퓨터 저장소에 저장되어 있는 인증서를 모두 제거합니다.  예를 들어 PKI(공개 키 인프라) 인증서를 사용하는 경우 컴퓨터를 이미지로 만들기 전에 **컴퓨터** 및 **사용자** 에 대한 **개인** 저장소에서 인증서를 제거해야 합니다.

4.  클라이언트가 마스터 이미지 컴퓨터와 다른 Configuration Manager 계층 구조에 설치될 경우 마스터 이미지 컴퓨터에서 신뢰할 수 있는 루트 키를 제거합니다.  
    > [!NOTE]  
    >  클라이언트가 Active Directory Domain Services를 쿼리하여 관리 지점을 찾을 수 없으면 해당 클라이언트는 신뢰할 수 있는 루트 키를 사용하여 신뢰할 수 있는 관리 지점을 결정합니다. 이미지로 만든 모든 클라이언트가 마스터 컴퓨터와 동일한 계층에 배포될 경우 신뢰할 수 있는 루트 키를 적합한 위치에 두세요. 클라이언트가 다른 계층에 배포될 경우 신뢰할 수 있는 루트 키를 제거한 후 해당 클라이언트는 새 신뢰할 수 있는 루트 키로 사전 프로비전하는 것이 좋습니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK)을 참조하세요. 

5.  이미징 소프트웨어를 사용하여 마스터 컴퓨터의 이미지를 캡처합니다.  

6.  대상 컴퓨터에 이미지를 배포합니다.  

##  <a name="BKMK_ClientWorkgroup"></a> 작업 그룹 컴퓨터에 클라이언트를 설치하는 방법  
 Configuration Manager에서 작업 그룹의 컴퓨터에 대한 클라이언트 설치를 지원합니다. [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual)에 지정된 방법을 사용하여 작업 그룹 컴퓨터에 클라이언트를 설치하세요.  

 필수 조건:  

-   클라이언트는 각 작업 그룹 컴퓨터에 수동으로 설치되어야 합니다. 설치 시, 로그온한 사용자에게 로컬 관리자 권한이 있어야 합니다.  

-   Configuration Manager 사이트 서버 도메인의 리소스에 액세스하려면 해당 사이트에 대한 네트워크 액세스 계정을 구성해야 합니다. 이 계정은 소프트웨어 배포 구성 요소 속성으로 지정합니다. 자세한 내용은 [System Center Configuration Manager의 사이트 구성 요소](../../../core/servers/deploy/configure/site-components.md)를 참조하세요.  

 제한 사항:  

-   작업 그룹 클라이언트는 Active Directory Domain Services에서 관리 지점을 찾을 수 없으며 대신 DNS, WINS 또는 다른 관리 지점을 사용해야 합니다.  

-   클라이언트는 Active Directory Domain Services에서 사이트 정보를 쿼리할 수 없으므로 글로벌 로밍은 지원되지 않습니다.  

-   Active Directory 검색 방법으로 작업 그룹에서 컴퓨터를 검색할 수 없습니다.  

-   작업 그룹 컴퓨터의 사용자에게 소프트웨어를 배포할 수 없습니다.  

-   클라이언트 강제 설치 방법을 사용하여 작업 그룹 컴퓨터에 클라이언트를 설치할 수 없습니다.  

-   작업 그룹 클라이언트는 인증에 Kerberos를 사용할 수 없고 수동 승인이 필요할 수 있습니다.  

-   작업 그룹 클라이언트는 배포 지점으로 구성할 수 없습니다. Configuration Manager에서는 배포 지점 컴퓨터가 도메인의 구성원이어야 합니다.  

### <a name="to-install-the-client-on-workgroup-computers"></a>작업 그룹 컴퓨터에 클라이언트를 설치하려면  

필수 구성 요소를 확인하고 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual) 섹션의 지침을 따르세요.  

   이 예제에서는 인트라넷 클라이언트 관리용 클라이언트를 설치하고 관리 지점을 찾기 위한 사이트 코드 및 DNS 접미사를 지정합니다. `**CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com**`  

     

   이 예제에서 자동 사이트 할당이 성공할 수 있도록 클라이언트는 경계 그룹에 구성된 네트워크 위치에 있어야 합니다. 클라이언트 배포를 추적하고 클라이언트 통신 문제를 확인할 수 있도록 명령에는 FSPSERVER 서버의 대체 상태 지점이 포함됩니다. `**CCMSetup.exe FSP=fspserver.constoso.com**`  

      

##  <a name="BKMK_ClientInternet"></a> 인터넷 기반 클라이언트 관리용으로 클라이언트를 설치하는 방법  
 Configuration Manager 사이트가 인트라넷 및 인터넷 간에 이동하는 클라이언트에 대해 인터넷 기반 클라이언트 관리를 지원하는 경우 클라이언트를 인트라넷에 설치할 때 사용할 수 있는 두 가지 옵션이 있습니다.  

-   수동 설치 또는 클라이언트 강제 설치와 같은 방식으로 클라이언트를 설치할 때 CCMHOSTNAME=*&lt;인터넷 기반 관리 지점의 인터넷 FQDN\>* Client.msi 속성을 포함할 수 있습니다. 또한 이 방법을 사용하면 클라이언트를 사이트에 직접 할당해야 하며 자동 사이트 할당은 사용할 수 없습니다. 이 항목의 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual) 섹션에서는 이러한 구성 방법의 예를 제공 합니다.  

-   클라이언트를 인트라넷 클라이언트 관리용으로 설치한 다음 제어판의 Configuration Manager 클라이언트 속성을 사용하거나 스크립트를 사용하여 클라이언트에 인터넷 기반 클라이언트 관리 지점을 할당할 수 있습니다. 이 방법을 사용하면 자동 클라이언트 할당을 사용할 수 있습니다. 자세한 내용은 이 항목에서 [클라이언트 설치 후 클라이언트를 인터넷 기반 클라이언트 관리용으로 구성하는 방법](#BKMK_ConfigureIBCM_MP) 섹션을 참조하세요.  

 인터넷에 있는 특정 클라이언트가 인터넷 전용 클라이언트이므로 또는 인트라넷으로 다시 배치되기 전에 설치되어야 하므로 해당 클라이언트를 설치해야 할 경우 다음 지원되는 방법 중 하나를 선택합니다.  

-   가상 사설망(VPN)을 사용하여 이 클라이언트가 인트라넷에 일시적으로 연결할 수 있는 메커니즘을 제공한 다음 적절한 클라이언트 설치 방법으로 클라이언트를 설치합니다.  

-   Configuration Manager와는 독립적인 설치 방법(예: 지침에 따라 설치할 수 있도록 사용자에게 보낼 수 있는 이동식 미디어에 클라이언트 설치 원본 파일을 패키지화)을 사용합니다. 클라이언트 설치 원본 파일은 Configuration Manager 사이트 서버 및 관리 지점의 *&lt;InstallationPath\>*\Client 폴더에 있습니다. 클라이언트 폴더를 통해 수동으로 복사하고 이 폴더에서 CCMSetup.exe 및 해당되는 모든 CCMSetup 명령줄 속성을 사용하여 클라이언트를 설치하기 위한 스크립트를 미디어에 포함합니다.  

> [!NOTE]  
>  Configuration Manager는 클라이언트를 인터넷 기반 관리 지점 또는 인터넷 기반 소프트웨어 업데이트 지점에서 직접 설치하는 작업을 지원하지 않습니다.  

 인터넷을 통해 관리되는 클라이언트는 인터넷 기반 사이트 시스템과 통신해야 하므로 이러한 클라이언트를 설치하려면 클라이언트에 PKI 인증서도 설치되어 있어야 합니다. 이러한 인증서는 Configuration Manager와 독립적으로 설치해야 합니다. 인증서 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.  

### <a name="to-install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>CCMSetup 명령줄 속성을 지정하여 인터넷에 클라이언트를 설치하려면  

1.  [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual) 섹션의 지침을 따르고 항상 다음을 포함해야 합니다.  

    -   CCMSetup 명령줄 속성 **/source:***&lt;복사된 Client 폴더의 로컬 경로\>*  

    -   CCMSetup 명령줄 속성 **/UsePKICert**  

    -   Client.msi 속성 **CCMHOSTNAME=***&lt;인터넷 기반 관리 지점의 FQDN\>*  

    -   Client.msi 속성 **SMSSIGNCERT=***&lt;내보낸 사이트 서버 서명 인증서의 로컬 경로\>*  

    -   Client.msi 속성 **SMSSITECODE=***&lt;인터넷 기반 관리 지점의 사이트 코드\>*  

    > [!NOTE]  
    >  사이트에 두 개 이상의 인터넷 기반 관리 지점이 있는 경우 CCMHOSTNAME 속성에는 어떤 인터넷 기반 관리 지점을 지정해도 상관없습니다. Configuration Manager 클라이언트에서 지정된 인터넷 기반 관리 지점에 연결하면 관리 지점은 해당 클라이언트에 사이트에서 사용할 수 있는 인터넷 기반 관리 지점의 목록을 보내며, 그 후 클라이언트는 목록에서 원하는 항목을 임의로 선택하면 됩니다.  

2.  클라이언트가 CRL(인증서 해지 목록)을 확인하지 않도록 하려면 CCMSetup 명령줄 속성 **/NoCRLCheck**을 지정합니다.  

3.  인터넷 기반 대체 상태 지점을 사용하는 경우 Client.msi 속성 **FSP=***&lt;인터넷 기반 대체 상태 지점의 인터넷 FQDN\>*을 지정합니다.  

4.  클라이언트를 인터넷 전용 클라이언트 관리용으로 설치하는 경우 Client.msi 속성 **CCMALWAYSINF=1**을 지정합니다.  

5.  추가 CCMSetup 명령줄 속성을 지정해야 하는지 여부를 확인합니다. 예를 들어 클라이언트에 두 개 이상의 유효한 PKI 인증서가 있는 경우 인증서 선택 기준을 지정해야 할 수도 있습니다. 사용 가능한 속성 목록은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

   예: `**CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1**`  

   이 예제에서는 클라이언트 PKI 인증서를 사용하는 설정과 함께 D 드라이브의 폴더에서 클라이언트 원본 파일을 설치하고, 인터넷 전용 클라이언트 관리에 대해 가장 긴 유효 기간을 갖는 인증서를 선택하고, 이름이 SERVER1인 인터넷 기반 관리 지점과 contoso.com 도메인의 인터넷 기반 대체 상태 지점을 사용하도록 클라이언트를 할당한 다음 이 클라이언트를 ABC 사이트에 할당합니다.  

###  <a name="BKMK_ConfigureIBCM_MP"></a>클라이언트 설치 후 클라이언트를 인터넷 기반 클라이언트 관리용으로 구성하려면  
 클라이언트가 설치된 후 인터넷 기반 관리 지점을 할당하려면 다음 절차 중 하나를 사용합니다. 첫 번째 절차는 수동 구성이 필요하고 몇몇 클라이언트에 적절합니다. 두 번째 절차는 많은 클라이언트를 구성하는 데 적절합니다.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-assigning-the-internet-based-management-point-in-configuration-manager-properties"></a>Configuration Manager 속성에서 인터넷 기반 관리 지점을 할당하여 클라이언트 설치 후 클라이언트를 인터넷 기반 클라이언트 관리에 대해 구성하려면  

1.  클라이언트 컴퓨터의 제어판에서 **Configuration Manager** 로 이동한 다음 두 번 클릭하여 속성을 엽니다.  

2.  **인터넷** 탭에서 인터넷 FQDN 텍스트 상자에 인터넷 기반 관리 지점의 FQDN을 입력합니다.  

    > [!NOTE]  
    >  **인터넷** 탭은 클라이언트에 클라이언트 PKI 인증서가 있는 경우에만 사용할 수 있습니다.  

3.  클라이언트가 프록시 서버를 사용하여 인터넷에 액세스할 경우 프록시 서버 설정을 입력합니다.  

#### <a name="to-configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>스크립트를 사용하여 클라이언트 설치 후 클라이언트를 인터넷 기반 클라이언트 관리용으로 구성하려면  

1.  메모장과 같은 텍스트 편집기를 엽니다.  

2.  다음 내용을 복사하여 파일에 삽입합니다. *mp.contoso.com* 을 인터넷 기반 관리 지점의 인터넷 FQDN으로 바꿉니다.  

    ```  
    on error resume next  

    ' Create variables.  
    Dim newInternetBasedManagementPointFQDN  
    Dim client  

    newInternetBasedManagementPointFQDN = "mp.contoso.com"  

    ' Create the client COM object.  
    Set client = CreateObject ("Microsoft.SMS.Client")  

    ' Set the Internet-Based Management Point FQDN by calling the SetCurrentManagementPoint method.  
    client.SetInternetManagementPointFQDN newInternetBasedManagementPointFQDN  

    ' Clear variables.  
    Set client = Nothing  
    Set internetBasedManagementPointFQDN = Nothing  

    ```  

    > [!NOTE]  
    >  특정 인터넷 기반 관리 지점을 삭제하여 클라이언트가 인터넷 기반 관리 지점을 사용하도록 구성하지 않으려면 따옴표 안의 값을 제거하여 이 행이 **newInternetBasedManagementPointFQDN = ""**가 되도록 합니다.  

4.  .vbs 확장명으로 파일을 저장합니다.  

5.  다음 방법 중 하나를 사용하여 cscript로 클라이언트 컴퓨터에서 스크립트를 실행합니다.  

    -   패키지 및 프로그램을 사용하여 파일을 기존 Configuration Manager 클라이언트에 배포합니다.  

    -   Windows 탐색기에서 스크립트 파일을 두 번 클릭하여 이 파일을 기존 Configuration Manager 클라이언트에서 로컬로 실행합니다.  

 변경 내용을 적용하려면 클라이언트를 다시 시작해야 할 수 있습니다.  

##  <a name="BKMK_Provision"></a> 클라이언트 설치 속성을 프로비전하는 방법(그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치)  
 Windows 그룹 정책을 사용하면 Configuration Manager 클라이언트 설치 속성으로 컴퓨터를 프로비전할 수 있습니다. 이 속성은 컴퓨터의 레지스트리에 저장되고 클라이언트 소프트웨어가 설치될 때 읽혀집니다. 이 절차는 보통 필요하지 않지만, 다음과 같은 일부 클라이언트 설치 시나리오에는 필요할 수 있습니다.  

-   그룹 정책 설정 또는 소프트웨어 업데이트 기반 클라이언트 설치 방법을 사용하고 Active Directory 스키마를 Configuration Manager에 대해 확장하지 않았습니다.  

-   특정 컴퓨터에서 클라이언트 설치 속성을 재정의하려고 합니다.  

> [!NOTE]  
>  CCMSetup.exe 명령줄에 설치 속성이 제공될 경우 컴퓨터에 프로비전된 설치 속성은 사용되지 않습니다.  

 Configuration Manager 설치 미디어에 ConfigMgrInstallation.adm이라는 그룹 정책 관리 템플릿이 제공됩니다. 이 그룹 정책 관리 템플릿은 설치 속성을 사용하여 클라이언트 컴퓨터를 프로비전할 때 사용할 수 있습니다.   

### <a name="to-configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>그룹 정책 개체를 사용하여 클라이언트 설치 속성을 구성 및 할당하려면  

1.  Windows 그룹 정책 개체 편집기와 같은 편집기를 사용하여 관리 템플릿인 ConfigMgrInstallation.adm을 새롭거나 기존에 있는 그룹 정책 개체로 가져옵니다. 파일은 Configuration Manager 설치 미디어의 **TOOLS\ConfigMgrADMTemplates** 폴더에서 찾을 수 있습니다.  

2.  가져온 **클라이언트 배포 설정 구성**설정의 속성을 엽니다.  

3.  **사용**을 선택합니다.  

4.  **CCMSetup** 상자에서 필요한 CCMSetup 명령줄 속성을 입력합니다. 모든 CCMSetup 명령줄 속성 및 사용 예가 포함된 목록은 [System Center Configuration Manager의 클라이언트 설치 속성 정보](../../../core/clients/deploy/about-client-installation-properties.md)를 참조하세요.  

5.  Configuration Manager 클라이언트 설치 속성으로 프로비전하려는 컴퓨터에 그룹 정책 개체를 할당합니다.  

Windows 그룹 정책에 대한 자세한 내용은 Windows Server 설명서를 참조하세요.  

## <a name="next-steps"></a>다음 단계
Configuration Manager 클라이언트를 설치할 수 있는 자세한 내용은 [System Center Configuration Manager의 클라이언트 설치 방법](../../../core/clients/deploy/plan/client-installation-methods.md)을 참조하세요.