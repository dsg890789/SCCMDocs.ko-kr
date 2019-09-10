---
title: Windows에 클라이언트 배포
titleSuffix: Configuration Manager
description: Windows 컴퓨터에 Configuration Manager 클라이언트를 배포하는 방법을 알아봅니다.
ms.date: 09/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 341f0d0b-f907-44cf-9e10-e1b41fc15f82
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 51a8bd605fae4aea1cb290a19a06b811a7c80382
ms.sourcegitcommit: 9648ce8a8b5c82518e7c8b6a7668e0e9b076cae6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/05/2019
ms.locfileid: "70378211"
---
# <a name="how-to-deploy-clients-to-windows-computers-in-configuration-manager"></a>Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Windows 컴퓨터에 Configuration Manager 클라이언트를 배포하는 방법에 대해 자세히 설명합니다. 클라이언트 배포 계획 및 준비에 대한 자세한 내용은 다음 문서를 참조하세요.

- [클라이언트 설치 방법](/sccm/core/clients/deploy/plan/client-installation-methods)  
- [Windows 컴퓨터에 클라이언트를 배포하기 위한 필수 조건](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers)
- [Configuration Manager 클라이언트에 대한 보안 및 개인 정보](/sccm/core/clients/deploy/plan/security-and-privacy-for-clients)  
- [클라이언트 배포에 대한 모범 사례](/sccm/core/clients/deploy/plan/best-practices-for-client-deployment)  


## <a name="BKMK_ClientPush"></a> 클라이언트 강제 설치

클라이언트 강제를 사용하는 세 가지 주요 방법은 다음과 같습니다.  

- 사이트에 대한 클라이언트 강제 설치를 구성하면 사이트에서 검색한 컴퓨터에서 클라이언트 설치가 자동으로 실행됩니다. 이 방법은 해당 경계가 경계 그룹으로 구성된 경우 사이트의 구성된 경계로 범위가 지정됩니다.  

- 컬렉션 내의 특정 컬렉션 또는 리소스에 대해 클라이언트 강제 설치 마법사를 실행하여 클라이언트 강제 설치를 시작합니다.  

- 클라이언트 강제 설치 마법사를 사용하여 결과를 [쿼리](/sccm/core/servers/manage/introduction-to-queries)하는 데 사용할 수 있는 구성 관리자 클라이언트를 설치합니다. 쿼리에서 반환되는 항목 중 하나가 **시스템 리소스** 클래스의 **ResourceID** 특성인 경우에만 설치가 성공합니다.

사이트 서버에서 클라이언트 컴퓨터에 연결하거나 설치 프로세스를 시작할 수 없는 경우 1시간마다 자동으로 설치를 시도합니다. 서버는 최대 7일 동안 계속해서 다시 시도합니다.  

클라이언트 설치 프로세스를 추적하려면 클라이언트를 설치하기 전에 대체 상태 지점을 설치합니다. 대체 상태 지점을 설치하면 클라이언트 강제 설치 방법으로 클라이언트를 설치할 때 이 지점이 자동으로 클라이언트에 할당됩니다. 클라이언트 설치 진행률을 추적하려면 클라이언트 배포 및 할당 보고서를 봅니다.

클라이언트 로그 파일은 더 자세한 문제 해결 정보를 제공합니다. 로그 파일은 대체 상태 지점이 필요하지 않습니다. 예를 들어, 사이트 서버의 CCM.log 파일은 컴퓨터에 연결할 때 발생하는 모든 문제를 기록합니다. 클라이언트의 CCMSetup.log 파일은 설치 프로세스를 기록합니다.  

> [!IMPORTANT]  
> 클라이언트 푸시는 모든 필수 조건이 충족하는 경우에만 성공합니다. 자세한 내용은 [설치 방법 종속성](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#installation-method-dependencies)을 참조하세요.

### <a name="configure-the-site-to-automatically-use-client-push-for-discovered-computers"></a>검색된 컴퓨터에 대해 자동으로 클라이언트 푸시를 사용하도록 사이트 구성

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 자동 사이트 전체 클라이언트 강제 설치를 구성하려는 사이트를 선택합니다.  

3. 리본 메뉴에 있는 **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정**, **클라이언트 강제 설치**를 차례로 선택합니다.  

4. [클라이언트 강제 설치 속성] 창의 **일반** 탭에서 **자동 사이트 전체 클라이언트 강제 설치 사용**을 선택합니다.

5. 1806 버전부터 사이트를 업데이트하면 클라이언트 강제에 대한 Kerberos 확인을 사용하도록 설정합니다. **NTLM에 대한 연결 대체 허용** 옵션은 기본적으로 사용하도록 설정되며 이전 동작과 일치합니다. 사이트에서 Kerberos를 사용하여 클라이언트를 인증할 수 없으면 NTLM을 사용하여 연결을 다시 시도합니다. 향상된 보안을 위해 권장되는 구성은 NTLM 대체 없이 Kerberos가 필요한 이 설정을 사용하지 않도록 설정하는 것입니다.<!--1358204-->  

    > [!NOTE]  
    > 클라이언트 강제를 사용하여 구성 관리자 클라이언트를 설치하는 경우 사이트 서버에서 클라이언트에 대한 원격 연결을 만듭니다. 1806 버전부터 사이트에서 연결을 설정하기 전에 NTLM에 대한 대체를 허용하지 않으므로 Kerberos 상호 인증이 필요할 수 있습니다. 이 개선 사항은 서버와 클라이언트 간의 통신을 보안하는 데 도움이 됩니다.  
    >
    > 보안 정책에 따라 사용자 환경에서 이미 이전 NTLM 인증에 비해 Kerberos를 선호하거나 요구할 수 있습니다. 이러한 인증 프로토콜의 보안 고려 사항에 대한 자세한 내용은 [NTLM을 제한하는 Windows 보안 정책 설정](https://docs.microsoft.com/windows/security/threat-protection/security-policy-settings/network-security-restrict-ntlm-outgoing-ntlm-traffic-to-remote-servers#security-considerations)을 참조하세요.  
    >
    > 이 기능을 사용하려면 클라이언트가 신뢰할 수 있는 Active Directory 포리스트에 있어야 합니다. Windows의 Kerberos는 상호 인증을 위해 Active Directory를 사용합니다.  

6. Configuration Manager에서 클라이언트 소프트웨어 강제 설치를 수행해야 할 시스템 유형을 선택합니다. 도메인 컨트롤러에 클라이언트 소프트웨어를 설치할지 여부를 선택합니다.  

7. **계정** 탭에서 대상 컴퓨터에 연결할 때 사용할 Configuration Manager에 대한 계정을 하나 이상 지정합니다. **만들기** 아이콘을 선택하고 **사용자 이름**과 **암호**(38자 이하)를 입력한 다음, 암호를 확인하고 **확인**을 선택합니다. 하나 이상의 클라이언트 푸시 설치 계정을 지정합니다. 이 계정에는 클라이언트를 설치할 대상 컴퓨터에 대한 로컬 관리자 권한이 있어야 합니다. 클라이언트 강제 설치 계정을 지정하지 않으면 Configuration Manager에서 사이트 시스템 컴퓨터 계정을 사용하려고 시도합니다. 사이트 시스템 컴퓨터 계정을 사용하는 경우 도메인 간 클라이언트 푸시가 실패합니다.  

    > [!NOTE]  
    > 보조 사이트에서 클라이언트 푸시를 사용하려면 클라이언트 푸시를 시작하는 보조 사이트에서 계정을 지정합니다.  
    >
    > 클라이언트 푸시 설치 계정에 대한 자세한 내용은 다음 절차인 [클라이언트 푸시 설치 마법사 사용](#use-the-client-push-installation-wizard)을 참조하세요.  

8. **설치 속성** 탭에서 필요한 설치 속성을 지정합니다.

    Configuration Manager에 대한 Active Directory 스키마를 확장한 경우 사이트에서 지정된 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties)을 Active Directory Domain Services에 게시합니다. CCMSetup이 설치 속성 없이 실행될 때 Active Directory에서 이러한 속성을 읽습니다.  

    > [!NOTE]  
    > 보조 사이트에서 클라이언트 강제 설치를 사용하도록 설정하면 **SMSSITECODE** 속성이 해당 부모 기본 사이트의 Configuration Manager 사이트 코드로 설정됩니다. Configuration Manager에 대한 Active Directory 스키마를 확장한 경우 올바른 사이트 할당을 자동으로 찾게 하려면 이 속성을 **AUTO**로 설정합니다.

### <a name="use-the-client-push-installation-wizard"></a>클라이언트 푸시 설치 마법사 사용

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 자동 사이트 전체 클라이언트 강제 설치를 구성하려는 사이트를 선택합니다.  

3. 리본 메뉴에 있는 **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정**, **클라이언트 강제 설치**를 차례로 선택합니다.  

4. **설치 속성** 탭에서 필요한 설치 속성을 지정합니다.  

    Configuration Manager에 대한 Active Directory 스키마를 확장한 경우 사이트에서 지정된 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties)을 Active Directory Domain Services에 게시합니다. CCMSetup이 설치 속성 없이 실행될 때 Active Directory에서 이러한 속성을 읽습니다.

5. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다.  

6. **디바이스** 노드에서 하나 이상의 컴퓨터를 선택합니다. 또는 **디바이스 컬렉션** 노드에서 컴퓨터 컬렉션을 선택합니다.  

7. 리본 메뉴의 **홈** 탭에서 다음 옵션 중 하나를 선택합니다.  

    - 클라이언트를 하나 이상의 디바이스에 강제 설치하려면 **디바이스** 그룹에서 **클라이언트 설치**를 선택합니다.  

    - 클라이언트를 디바이스 컬렉션에 강제 설치하려면 **컬렉션** 그룹에서 **클라이언트 설치**를 선택합니다.  

8. 구성 관리자 클라이언트 설치 마법사의 **시작하기 전에** 페이지에서 정보를 검토한 다음, **다음**을 선택합니다.  

9. **설치 옵션** 페이지에서 적절한 옵션을 선택합니다.  

10. 설치 설정을 검토한 다음, 마법사를 완료합니다.  

> [!NOTE]  
> 사이트가 클라이언트 강제에 대해 구성되지 않은 경우에도 이 마법사를 사용하여 클라이언트를 설치합니다.  

## <a name="BKMK_ClientSUP"></a> 소프트웨어 업데이트 기반 설치  

소프트웨어 업데이트 기반 설치는 클라이언트를 소프트웨어 업데이트 지점에 소프트웨어 업데이트로 게시합니다. 처음 설치하거나 업그레이드할 경우 이 방법을 사용합니다.  

컴퓨터에 구성 관리자 클라이언트가 설치된 경우 사이트에서 클라이언트 정책이 수신됩니다. 이 정책은 소프트웨어 업데이트를 받는 소프트웨어 업데이트 지점 서버 이름 및 포트를 포함합니다.

> [!IMPORTANT]  
> 소프트웨어 업데이트 기반 설치의 경우 클라이언트 설치 및 소프트웨어 업데이트에 동일한 WSUS(Windows Server Update Services) 서버를 사용합니다. 이 서버는 기본 사이트의 활성 소프트웨어 업데이트 지점이어야 합니다. 자세한 내용은 [소프트웨어 업데이트 지점 설치](/sccm/sum/get-started/install-a-software-update-point)를 참조하세요.

컴퓨터에 구성 관리자 클라이언트가 설치되어 있지 않으면 그룹 정책 개체를 구성하고 할당합니다. 이 그룹 정책에는 소프트웨어 업데이트 지점의 서버 이름이 지정됩니다.  

소프트웨어 업데이트 기반 클라이언트 설치에는 명령줄 속성을 추가할 수 없습니다. Configuration Manager에 대한 Active Directory 스키마를 확장한 경우 클라이언트 설치는 Active Directory Domain Services에서 설치 속성을 자동으로 쿼리합니다.  

Active Directory 스키마를 확장하지 않은 경우 그룹 정책을 사용하여 클라이언트 설치 설정을 프로비저닝합니다. 이러한 설정은 모든 소프트웨어 업데이트 기반 클라이언트 설치에 자동으로 적용됩니다. 자세한 내용은 [클라이언트 설치 속성을 프로비전하는 방법](#BKMK_Provision) 섹션 및 [사이트에 클라이언트를 할당하는 방법](/sccm/core/clients/deploy/assign-clients-to-a-site) 문서를 참조하세요.  

다음 절차를 사용하여 Configuration Manager 클라이언트가 없는 컴퓨터에서 소프트웨어 업데이트 지점을 사용하도록 구성합니다. 클라이언트 소프트웨어를 소프트웨어 업데이트 지점에 게시하는 절차도 있습니다.  

> [!TIP]  
> 컴퓨터가 이전 소프트웨어 설치를 수행한 후 보류 중인 다시 시작 상태인 경우 소프트웨어 업데이트 기반 클라이언트 설치로 인해 컴퓨터가 다시 시작될 수 있습니다.  

### <a name="configure-a-group-policy-object-to-specify-the-software-update-point"></a>소프트웨어 업데이트 지점을 지정하도록 그룹 정책 개체 구성  

1. **그룹 정책 관리 콘솔**을 사용하여 새 또는 기존 그룹 정책 개체를 엽니다.  

2. **컴퓨터 구성**, **관리 템플릿**, **Windows 구성 요소**를 차례로 확장한 다음, **Windows 업데이트**를 선택합니다.  

3. **인트라넷 Microsoft 업데이트 서비스 위치 지정** 설정의 속성을 열고 **사용**을 선택합니다.  

4. **업데이트를 검색하도록 인트라넷 업데이트 서비스 설정**: 소프트웨어 업데이트 지점 서버의 이름 및 포트를 지정합니다.  

    - Configuration Manager 사이트 시스템에서 FQDN(정규화된 도메인 이름)을 사용하도록 구성한 경우 해당 형식을 사용합니다.  

    - Configuration Manager 사이트 시스템에서 FQDN을 사용하도록 구성하지 않은 경우 짧은 이름 형식을 사용합니다.

    > [!TIP]  
    > 포트 번호를 확인하려면 [WSUS에 사용되는 포트 설정을 확인하는 방법](/sccm/sum/plan-design/plan-for-software-updates)을 참조하세요.

    FQDN 형식 예제: `http://server1.contoso.com:8530`  

5. **인트라넷 통계 서버 설정**: 이 설정은 일반적으로 동일한 서버 이름으로 구성됩니다.

6. 클라이언트를 설치하고 소프트웨어 업데이트를 받을 컴퓨터에 그룹 정책 개체를 할당합니다.  

### <a name="publish-the-configuration-manager-client-to-the-software-update-point"></a>소프트웨어 업데이트 지점에 Configuration Manager 클라이언트 게시  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **사이트** 노드를 선택합니다.  

2. 소프트웨어 업데이트 기반 클라이언트 설치를 구성하려는 사이트를 선택합니다.  

3. 리본 메뉴에 있는 **홈** 탭의 **설정** 그룹에서 **클라이언트 설치 설정**을 한 다음, **소프트웨어 업데이트 기반 클라이언트 설치**를 차례로 선택합니다.  

4. **소프트웨어 업데이트 기반 클라이언트 설치 사용**을 선택합니다.  

5. 사이트의 클라이언트 버전이 소프트웨어 업데이트 지점의 버전보다 최신 버전이면 **최신 버전의 클라이언트 패키지 검색** 대화 상자가 열립니다. **예**를 클릭하여 최신 버전을 게시합니다.  

    > [!NOTE]  
    > 아직 소프트웨어 업데이트 지점에 클라이언트 소프트웨어를 게시하지 않은 경우 이 대화 상자는 비어 있습니다.

새 버전이 있으면 Configuration Manager 클라이언트의 소프트웨어 업데이트가 자동으로 업데이트되지 않습니다. 사이트가 업데이트되면 이 절차를 반복하여 클라이언트를 업데이트합니다.  

## <a name="BKMK_ClientGP"></a> 그룹 정책 설치

Active Directory Domain Services에서 그룹 정책을 사용하여 구성 관리자 클라이언트를 게시하거나 할당합니다. 컴퓨터가 시작되면 클라이언트가 설치됩니다. 그룹 정책을 사용하면 클라이언트가 제어판의 **프로그램 추가/제거**에 나타납니다. 사용자는 해당 위치에서 설치할 수 있습니다.  

그룹 정책 기반 설치에는 CCMSetup.msi Windows Installer 패키지를 사용합니다. 이 파일은 사이트 서버의 `<ConfigMgr installation directory>\bin\i386` 폴더에 있습니다. 이 파일에 속성을 추가하여 설치 동작을 변경할 수 없습니다.  

> [!IMPORTANT]  
> 클라이언트 설치 파일에 액세스하려면 관리자 권한이 있어야 합니다.  

- Configuration Manager에 대한 Active Directory 스키마를 확장하고 **사이트 속성** 대화 상자의 **고급** 탭에서 **Active Directory Domain Services에 이 사이트 게시**를 선택한 경우, 클라이언트 컴퓨터는 Active Directory Domain Services에서 설치 속성을 자동으로 검색합니다. 자세한 내용은 [Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services)를 참조하세요.  

- Active Directory 스키마를 확장하지 않은 경우 [클라이언트 설치 속성을 프로비저닝하는 방법](#BKMK_Provision) 섹션에서 컴퓨터의 Windows 레지스트리에 설치 속성을 저장하는 방법에 대한 내용을 참조하세요. 클라이언트는 설치 시 이러한 설치 속성을 사용합니다.  

자세한 내용은 [그룹 정책을 사용하여 소프트웨어를 원격으로 설치하는 방법](https://support.microsoft.com/help/816102/how-to-use-group-policy-to-remotely-install-software-in-windows-server)을 참조하세요.  

## <a name="BKMK_Manual"></a> 수동 설치

CCMSetup.exe를 사용하여 클라이언트 소프트웨어를 컴퓨터에 수동으로 설치합니다. 이 프로그램과 해당 지원 파일은 사이트 서버에 있는 Configuration Manager 설치 폴더의 Client 폴더에서 찾을 수 있습니다. 사이트는 다음과 같이 이 폴더를 네트워크에 공유합니다.  

`\\<site server name>\SMS_<site code>\Client\`  

`<site server name>`은 기본 사이트 서버 이름입니다. `<site code>`는 클라이언트가 할당되는 기본 사이트 코드입니다. 클라이언트의 명령줄에서 CCMSetup.exe를 실행하려면 이 네트워크 위치에 연결한 다음, 명령을 실행합니다.  

> [!IMPORTANT]  
> 클라이언트 설치 파일에 액세스하려면 관리자 권한이 있어야 합니다.  

CCMSetup.exe는 필요한 모든 필수 구성 요소를 클라이언트 컴퓨터에 복사하고 Windows Installer 패키지(Client.msi)를 호출하여 클라이언트를 설치합니다. Client.msi는 직접 실행할 수 없습니다.  

클라이언트 설치의 동작을 수정하려면 CCMSetup.exe와 Client.msi에 대한 명령줄 옵션을 모두 지정합니다. Client.msi 속성을 지정하기 전에 `/`로 시작하는 CCMSetup 매개 변수를 지정해야 합니다. 예:  

`CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=AUTO FSP=SMSFP01`

이 예제에서 클라이언트는 다음 옵션을 사용하여 설치합니다.  

|옵션|설명|  
|--------------|-----------------|  
|`/mp:SMSMP01`|이 CCMSetup 매개 변수는 필수 클라이언트 설치 파일을 다운로드할 SMSMP01 관리 지점을 지정합니다.|  
|`/logon`|이 CCMSetup 매개 변수는 컴퓨터에 기존 Configuration Manager 클라이언트가 있는 경우 설치를 중지하도록 지정합니다.|  
|`SMSSITECODE=AUTO`|예를 들어 이 Client.msi 속성은 Active Directory Domain Services를 사용하여 클라이언트가 사용할 Configuration Manager 사이트 코드의 검색을 시도하도록 지정합니다.|  
|`FSP=SMSFP01`|이 Client.msi 속성은 클라이언트 컴퓨터에서 보낸 상태 메시지를 수신하는 데 대체 상태 지점 SMSFP01을 사용할 것을 지정합니다.|  

자세한 내용은 [클라이언트 설치 매개 변수 및 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

> [!TIP]  
> Azure Active Directory (Azure AD) ID를 사용하는 최신 Windows 10 디바이스에 구성 관리자 클라이언트를 설치하는 절차는 [인증을 위해 Azure AD를 사용하여 Configuration Manager Windows 10 클라이언트 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)을 참조하세요. 해당 절차는 인트라넷 또는 인터넷에서 클라이언트를 위한 것입니다.  

### <a name="manual-installation-examples"></a>수동 설치 예제

다음 예제는 인트라넷에서 Active Directory 조인 클라이언트에 대한 예제입니다. 사용하는 값은 다음과 같습니다.  

- **MPSERVER**: 관리 지점을 호스팅하는 서버
- **FSPSERVER**: 대체 상태 지점을 호스팅하는 서버  
- **ABC**: 사이트 코드  
- **contoso.com**: 도메인 이름  

모든 사이트 시스템 서버를 인트라넷 FQDN으로 구성하고 사이트 정보를 Active Directory에 게시했다고 가정합니다.  

클라이언트 컴퓨터에서 다음 단계를 시작합니다.  

1. 로컬 관리자 권한으로 로그인합니다.  
2. Z 드라이브를 `\\MPSERVER\SMS_ABC\Client`에 매핑합니다.  
3. 명령 프롬프트를 Z 드라이브로 전환합니다.  

그런 다음, 다음 명령 중 하나를 실행합니다.  

#### <a name="manual-example-1"></a>수동 예제 1  

`CCMSetup.exe`  

이 명령은 추가 매개 변수 또는 속성 없이 클라이언트를 설치합니다. 클라이언트는 다음 설정을 포함하여 Active Directory Domain Services에 게시된 클라이언트 설치 속성을 사용하여 자동으로 구성됩니다.  

- 사이트 코드: 이 설정에는 클라이언트의 네트워크 위치가 클라이언트 할당을 위해 구성된 경계 그룹에 포함되어야 합니다.  
- 관리 지점
- 대체 상태 지점
- HTTPS만 사용하여 통신합니다.  

자세한 내용은 [Active Directory Domain Services에 게시된 클라이언트 설치 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services)를 참조하세요.  

#### <a name="manual-example-2"></a>수동 예제 2  

`CCMSetup.exe /MP:mpserver.contoso.com /UsePKICert SMSSITECODE=ABC CCMHOSTNAME=server05.contoso.com CCMFIRSTCERT=1 FSP=server06.constoso.com`
  
이 명령은 Active Directory Domain Services에서 제공하는 자동 구성을 재정의합니다. 클라이언트의 네트워크 위치를 클라이언트 할당을 위해 구성된 경계 그룹에 포함할 필요가 없습니다. 대신 설치는 다음 설정을 지정합니다.

- 사이트 코드
- 인트라넷 관리 지점
- 인터넷 기반 관리 지점
- 인터넷에서 연결을 수락하는 대체 상태 지점
- 사용 가능한 경우 가장 긴 유효 기간을 포함하는 클라이언트 PKI(공개 키 인프라) 인증서를 사용합니다.

## <a name="BKMK_ClientLogonScript"></a> 로그온 스크립트 설치

Configuration Manager는 구성 관리자 클라이언트 소프트웨어를 설치하기 위한 로그온 스크립트를 사용하도록 지원합니다. 로그온 스크립트에서 CCMSetup.exe 프로그램 파일을 사용하여 클라이언트 설치를 트리거합니다.  

로그온 스크립트 설치에는 수동 클라이언트 설치와 동일한 방법이 사용됩니다. CCMSsetup.exe에 대한 `/logon` 설치 매개 변수를 지정합니다. 모든 버전의 클라이언트가 이미 컴퓨터에 있는 경우 이 매개 변수는 클라이언트를 설치하지 못하도록 합니다. 이 동작을 수행하면 로그온 스크립트가 실행될 때마다 클라이언트가 다시 설치되지 않습니다.  

`/Source` 매개 변수를 사용하여 설치 원본을 지정하지 않고 설치를 가져올 관리 지점을 `/MP` 매개 변수로 지정하지 않으면 CCMSetup.exe에서 Active Directory Domain Services를 검색하여 관리 지점을 찾습니다. Configuration Manager에 대한 스키마를 확장하고 사이트를 Active Directory Domain Services에 게시한 경우에만 이 동작이 발생합니다. 또는 클라이언트는 DNS 또는 WINS를 사용하여 관리 지점을 찾을 수 있습니다.  

## <a name="BKMK_ClientApp"></a> 패키지 및 프로그램 설치

Configuration Manager를 사용하여 선택한 디바이스에 대한 클라이언트 소프트웨어를 업그레이드하는 패키지 및 프로그램을 만들고 배포합니다. Configuration Manager는 패키지 속성을 일반적으로 사용되는 값으로 채우는 패키지 정의 파일을 제공합니다. 추가 명령줄 매개 변수와 속성을 지정하여 클라이언트 설치의 동작을 사용자 지정합니다.  

> [!NOTE]  
> 이 방법으로는 Configuration Manager 2007 클라이언트를 업그레이드할 수 없습니다. 대신, 최신 버전의 클라이언트가 포함된 패키지를 자동으로 만들고 배포하는 자동 클라이언트 업그레이드를 사용해야 합니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients)를 참조하세요.  
>
> Configuration Manager 클라이언트의 이전 버전에서 마이그레이션하는 방법에 대한 자세한 내용은 [클라이언트 마이그레이션 전략 계획](/sccm/core/migration/planning-a-client-migration-strategy)을 참조하세요.  

### <a name="create-a-package-and-program-for-the-client-software"></a>클라이언트 소프트웨어용 패키지 및 프로그램 만들기  

클라이언트 소프트웨어를 업그레이드하려면 다음 절차를 사용하여 Configuration Manager 클라이언트 컴퓨터에 배포할 수 있는 Configuration Manager 패키지 및 프로그램을 만듭니다.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고, **애플리케이션 관리**를 펼치고, **패키지**를 선택합니다.  

2. 리본 메뉴에 있는 **홈** 탭의 **만들기** 그룹에서 **정의에서 패키지 만들기**를 선택합니다.  

3. 마법사의 **패키지 정의** 페이지에서 **게시자** 목록에 있는 **Microsoft**를 선택하고 **패키지 정의** 목록에서  **업그레이드**를 선택합니다.  

4. **원본 파일** 페이지에서 **항상 원본 폴더에서 파일 가져오기**를 선택합니다.  

5. **원본 폴더** 페이지에서 **네트워크 경로(UNC 이름)** 를 선택합니다. 그런 다음, 클라이언트 설치 파일이 있는 서버와 공유에 대한 네트워크 경로를 입력합니다.  

    > [!NOTE]  
    > Configuration Manager 배포가 실행되는 컴퓨터에는 지정된 네트워크 폴더에 대한 액세스 권한이 있어야 합니다. 그렇지 않으면 클라이언트 설치가 실패합니다.  

    클라이언트 설치 속성을 변경하려면 **Configuration Manager 에이전트 자동 업그레이드 속성** 프로그램 대화 상자의 **일반** 탭에서 CCMSetup.exe 명령줄을 수정합니다. 기본 설치 속성은 `/noservice SMSSITECODE=AUTO`입니다.  

6. 클라이언트 업그레이드 패키지를 호스트할 모든 배포 지점에 패키지를 배포합니다. 그런 다음, 업그레이드하려는 클라이언트가 포함된 디바이스 컬렉션에 패키지를 배포합니다.  

## <a name="bkmk_mdm"></a> Intune MDM 관리 Windows 디바이스

Microsoft Intune에 등록된 디바이스에 Configuration Manager 클라이언트를 배포합니다.

이 절차는 인트라넷에 연결되어 있는 기존 클라이언트를 위한 것입니다. 기존 클라이언트 인증 방법을 사용합니다. 클라이언트가 설치된 후에 디바이스가 관리되는 상태로 유지되도록 하려면 해당 디바이스가 인트라넷 및 Configuration Manager 사이트 경계 내에 있어야 합니다.  

Azure AD ID를 사용하는 최신 Windows 10 디바이스에 구성 관리자 클라이언트를 설치하는 절차는 [인증을 위해 Azure AD를 사용하여 Configuration Manager Windows 10 클라이언트 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)을 참조하세요.

Configuration Manager 클라이언트를 설치한 후에는 디바이스가 Intune에서 등록 취소되지 않습니다. 구성 관리자 클라이언트와 MDM 등록을 동시에 사용할 수 있습니다. 자세한 내용은 [공동 관리 개요](/sccm/comanage/overview)를 참조하세요.  

> [!Note]
> 다른 클라이언트 설치 방법을 사용하여 Intune 관리 디바이스에 Configuration Manager 클라이언트를 설치할 수 있습니다. 예를 들어 Intune 관리 디바이스가 인트라넷에 있고 Active Directory 도메인에 조인되어 있는 경우 그룹 정책을 사용하여 구성 관리자 클라이언트를 설치할 수 있습니다.<!-- SCCMDocs#757 -->

### <a name="install-the-configuration-manager-client-by-using-intune"></a>Intune을 사용하여 Configuration Manager 클라이언트 설치

1. Intune에서 **CCMSetup.msi** 구성 관리자 클라이언트 설치 파일이 포함된 [Windows LOB(기간 업무) 앱을 추가](https://docs.microsoft.com/intune/lob-apps-windows)합니다. 이 파일은 사이트 서버의 Configuration Manager 설치 디렉터리 `\bin\i386` 폴더에서 찾을 수 있습니다.  

2. Intune 소프트웨어 게시자에서 명령줄 매개 변수를 입력합니다. 예를 들어 인트라넷의 기존 클라이언트로 다음 명령을 사용합니다.  

    `CCMSETUPCMD="/MP:<FQDN of management point> SMSMP=<FQDN of management point> SMSSITECODE=<your site code> DNSSUFFIX=<DNS suffix of management point>"`  

    > [!NOTE]  
    > Azure AD 인증을 사용하는 최신 Windows 10 클라이언트를 사용하는 명령 예제를 보려면 [공동 관리를 위해 인터넷 기반 디바이스를 준비하는 방법](/sccm/comanage/how-to-prepare-win10#install-the-configuration-manager-client)을 참조하세요.  

3. 등록된 Windows 컴퓨터의 그룹에 [앱을 할당](https://docs.microsoft.com/intune/deploy-use/deploy-apps-in-microsoft-intune)합니다.  

## <a name="BKMK_ClientImage"></a> OS 이미지 설치

OS 이미지를 만드는 데 사용하는 참조 컴퓨터에 Configuration Manager 클라이언트를 사전 설치합니다.

> [!IMPORTANT]  
> Configuration Manager 작업 순서를 사용하여 OS 이미지를 배포하는 경우 [ConfigMgr 클라이언트 준비](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) 단계는 구성 관리자 클라이언트를 완전히 제거합니다.  

### <a name="prepare-the-client-computer-for-imaging"></a>이미징에 대한 클라이언트 컴퓨터 준비  

1. 참조 컴퓨터에 Configuration Manager 클라이언트 소프트웨어를 수동으로 설치합니다. 자세한 내용은 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual)을 참조하세요.  

    > [!IMPORTANT]  
    > CCMSetup.exe 명령줄 속성에서 클라이언트에 대한 Configuration Manager 사이트 코드를 지정하지 마세요.  

2. 명령 프롬프트에서 `net stop ccmexec`를 입력하여 참조 컴퓨터에서 SMS 에이전트 호스트 서비스(CcmExec.exe)를 중지합니다.  

3. 참조 컴퓨터의 Windows 폴더에서 SMSCFG.INI 파일을 삭제합니다.  

4. 참조 컴퓨터에서 로컬 컴퓨터 저장소에 저장되어 있는 인증서를 모두 제거합니다. 예를 들어 PKI 인증서를 사용하는 경우 컴퓨터 이미지를 만들기 전에 **개인** 저장소에서 **컴퓨터** 및 **사용자**에 대한 인증서를 제거합니다.  

5. 클라이언트가 참조 컴퓨터의 계층 구조와 다른 Configuration Manager 계층 구조에 설치되는 경우 참조 컴퓨터에서 신뢰할 수 있는 루트 키를 제거합니다.  

    > [!NOTE]  
    > 클라이언트에서 Active Directory Domain Services를 쿼리하여 관리 지점을 찾을 수 없으면, 신뢰할 수 있는 루트 키를 사용하여 신뢰할 수 있는 관리 지점을 결정합니다. 이미지로 만든 모든 클라이언트를 마스터 컴퓨터와 동일한 계층 구조에 배포하는 경우 신뢰할 수 있는 루트 키는 그대로 둡니다.
    >
    > 클라이언트를 다른 계층 구조에 배포하는 경우 신뢰할 수 있는 루트 키를 제거합니다. 새 신뢰할 수 있는 루트 키로 이러한 클라이언트도 프로비전합니다. 자세한 내용은 [신뢰할 수 있는 루트 키 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForRTK)을 참조하세요.  

6. 이미징 소프트웨어를 사용하여 참조 컴퓨터의 이미지를 캡처합니다.  

7. 대상 컴퓨터에 이미지를 배포합니다.  

## <a name="BKMK_ClientWorkgroup"></a> 작업 그룹 컴퓨터

Configuration Manager에서 작업 그룹의 컴퓨터에 대한 클라이언트 설치를 지원합니다. [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual)에 지정된 방법을 사용하여 작업 그룹 컴퓨터에 클라이언트를 설치합니다.  

### <a name="prerequisites"></a>필수 구성 요소  

- 각 작업 그룹 컴퓨터에 클라이언트를 수동으로 설치합니다. 설치 시 대화형 사용자에게는 로컬 관리자 권한이 있어야 합니다.  

- Configuration Manager 사이트 서버 도메인의 리소스에 액세스하려면 사이트에 대한 네트워크 액세스 계정을 구성합니다. 이 계정은 소프트웨어 배포 사이트 구성 요소에서 지정합니다. 자세한 내용은 [사이트 구성 요소](/sccm/core/servers/deploy/configure/site-components)를 참조하세요.  

### <a name="limitations"></a>제한 사항  

- 작업 그룹 클라이언트는 Active Directory Domain Services에서 관리 지점을 찾을 수 없습니다. 대신 DNS, WINS 또는 다른 관리 지점을 사용합니다.  

- 글로벌 로밍은 지원되지 않습니다. 작업 그룹 클라이언트는 Active Directory Domain Services에서 사이트 정보를 쿼리할 수 없습니다.  

- Active Directory 검색 방법으로는 작업 그룹의 컴퓨터를 검색할 수 없습니다.  

- 작업 그룹 컴퓨터의 사용자에게는 소프트웨어를 배포할 수 없습니다.  

- 클라이언트 강제 설치 방법을 사용하여 작업 그룹 컴퓨터에 클라이언트를 설치할 수 없습니다.  

- 작업 그룹 클라이언트는 인증에 Kerberos를 사용할 수 없으며, 수동 승인이 필요할 수 있습니다.  

- 작업 그룹 클라이언트는 배포 지점으로 구성할 수 없습니다. Configuration Manager에서는 배포 지점 컴퓨터가 도메인의 구성원이어야 합니다.  

### <a name="install-the-client-on-workgroup-computers"></a>작업 그룹 컴퓨터에 클라이언트 설치  

필수 구성 요소를 확인한 다음, [구성 관리자 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual) 섹션의 지침을 따릅니다.  

#### <a name="workgroup-example-1"></a>작업 그룹 예제 1

이 예제에서 수행하는 작업은 다음과 같습니다.

- 인트라넷 클라이언트 관리용 클라이언트를 설치합니다.
- 사이트 코드를 지정합니다.
- 관리 지점을 찾을 DNS 접미사를 지정합니다.  

`CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=constoso.com`  

#### <a name="workgroup-example-2"></a>작업 그룹 예제 2

이 예제에서 클라이언트는 경계 그룹에 구성된 네트워크 위치에 있어야 합니다. 이 요구 사항이 충족되지 않으면 자동 사이트 할당이 수행되지 않습니다. 명령은 서버 FSPSERVER의 대체 상태 지점을 포함합니다. 이 속성은 클라이언트 배포를 추적하고 모든 클라이언트 통신 문제를 식별하는 데 도움을 줍니다.

`CCMSetup.exe FSP=fspserver.constoso.com`  

## <a name="BKMK_ClientInternet"></a> 인터넷 기반 클라이언트 관리  

> [!NOTE]  
> 이 섹션은 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/plan-cloud-management-gateway)를 사용하는 클라이언트에 적용되지 않습니다. 클라우드 관리 게이트웨이를 사용하여 인터넷 기반 클라이언트를 설치하려면 [인증을 위해 Azure AD를 사용하여 Configuration Manager Windows 10 클라이언트 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)을 참조하세요.  

Configuration Manager 사이트가 인트라넷 및 인터넷 간에 이동하는 클라이언트에 대해 [인터넷 기반 클라이언트 관리](/sccm/core/clients/manage/plan-internet-based-client-management)를 지원하는 경우 클라이언트를 인트라넷에 설치할 때 사용할 수 있는 두 가지 옵션이 있습니다.  

- 수동 설치 또는 클라이언트 강제 설치와 같은 방식으로 클라이언트를 설치할 때 다음 예제와 같이 Client.msi 속성 `CCMHOSTNAME=<internet FQDN of the internet-based management point>`를 포함합니다. 이 방법을 사용하는 경우 클라이언트를 사이트에 직접 할당합니다. 자동 사이트 할당은 사용할 수 없습니다. 이 구성 방법에 대한 예제를 제공하는 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual) 섹션을 참조하세요.  

- 인트라넷 클라이언트 관리용 클라이언트를 설치한 다음, 인터넷 기반 클라이언트 관리 지점을 이 클라이언트에 할당합니다. 제어판의 **Configuration Manager** 페이지에서 클라이언트 속성을 사용하거나 스크립트를 사용하여 관리 지점을 변경합니다. 이 방법을 사용하면 자동 클라이언트 할당을 사용할 수 있습니다. 자세한 내용은 [클라이언트 설치 후 인터넷 기반 클라이언트 관리용 클라이언트를 구성하는 방법](#BKMK_ConfigureIBCM_MP) 섹션을 참조하세요.  

인터넷에 있는 클라이언트를 설치하려면 지원되는 다음 방법 중 하나를 선택합니다.  

- 이러한 클라이언트를 VPN으로 인트라넷에 일시적으로 연결하기 위한 메커니즘을 제공합니다. 그런 다음, 적절한 클라이언트 설치 방법을 사용하여 클라이언트를 설치합니다.  

- Configuration Manager와 별개의 설치 방법을 사용합니다. 예를 들어, 클라이언트 설치 원본 파일을 이동식 미디어에 패키지하고 해당 미디어를 사용자에게 보냅니다. 클라이언트 설치 원본 파일은 Configuration Manager 사이트 서버의 `<installation path>\Client` 폴더에 있습니다. 미디어에서, 클라이언트 폴더를 통해 수동으로 복사하는 스크립트를 포함합니다. 이 폴더에서 CCMSetup.exe와 모든 적절한 CCMSetup 명령줄 속성을 사용하여 클라이언트를 설치합니다.  

> [!NOTE]  
> Configuration Manager는 클라이언트를 인터넷 기반 관리 지점 또는 인터넷 기반 소프트웨어 업데이트 지점에서 직접 설치하는 작업을 지원하지 않습니다.

인터넷을 통해 관리되는 클라이언트는 인터넷 기반 사이트 시스템과 통신해야 합니다. 클라이언트를 설치하기 전에 이러한 클라이언트에 PKI(공개 키 인프라) 인증서가 있는지 확인합니다. 이러한 인증서를 Configuration Manager와 독립적으로 설치합니다. 자세한 내용은 [PKI 인증서 요구 사항](/sccm/core/plan-design/network/pki-certificate-requirements)을 참조하세요.  

### <a name="install-clients-on-the-internet-by-specifying-ccmsetup-command-line-properties"></a>CCMSetup 명령줄 속성을 지정하여 인터넷에 클라이언트 설치  

1. [Configuration Manager 클라이언트를 수동으로 설치하는 방법](#BKMK_Manual) 섹션의 지침을 따릅니다. 항상 포함되는 옵션은 다음과 같습니다.  

    - CCMSetup 명령줄 매개 변수: `/source:<local path of the copied Client folder>`  

    - CCMSetup 명령줄 매개 변수: `/UsePKICert`  

    - Client.msi 속성: `CCMHOSTNAME=<FQDN of internet-based management point>`  

    - Client.msi 속성: `SMSSIGNCERT=<local path of exported site server signing certificate>`  

    - Client.msi 속성: `SMSSITECODE=<site code of internet-based management point>`  

    > [!NOTE]  
    > 사이트에 두 개 이상의 인터넷 기반 관리 지점이 있는 경우 `CCMHOSTNAME` 속성에는 어떤 항목을 지정해도 상관없습니다. Configuration Manager 클라이언트가 지정된 인터넷 기반 관리 지점에 연결되면 사이트에서 사용할 수 있는 인터넷 기반 관리 지점의 목록을 이 클라이언트에 보냅니다. 클라이언트는 목록에서 원하는 항목을 선택합니다.

2. 클라이언트에서 CRL(인증서 해지 목록)을 확인하지 않도록 하려면 `/NoCRLCheck` CCMSetup 명령줄 매개 변수를 지정합니다.  

3. 인터넷 기반 대체 상태 지점을 사용하는 경우 `FSP=<internet FQDN of the internet-based fallback status point>` Client.msi 속성을 지정합니다.  

4. 인터넷 전용 클라이언트 관리용 클라이언트를 설치하는 경우 `CCMALWAYSINF=1` Client.msi 속성을 지정합니다.  

5. 추가 CCMSetup 명령줄 매개 변수를 지정해야 하는지 결정합니다. 예를 들어 클라이언트에 둘 이상의 유효한 PKI 인증서가 있는 경우 인증서 선택 조건을 지정해야 할 수도 있습니다. 사용 가능한 속성 목록은 [클라이언트 설치 매개 변수 및 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

#### <a name="internet-based-example"></a>인터넷 기반 예제

`CCMSetup.exe /source: D:\Clients /UsePKICert CCMHOSTNAME=server1.contoso.com SMSSIGNCERT=siteserver.cer SMSSITECODE=ABC FSP=server2.contoso.com CCMALWAYSINF=1 CCMFIRSTCERT=1`

이 예제에서는 다음 동작으로 클라이언트를 설치합니다.

- 드라이브 D의 폴더에서 원본 파일을 사용합니다.
- 클라이언트 PKI 인증서를 사용합니다.
- 유효 기간이 가장 긴 인증서를 선택합니다.
- 인터넷 전용 클라이언트 관리
- SERVER1이라는 인터넷 기반 관리 지점을 사용하도록 클라이언트를 할당합니다.
- contoso.com 도메인에 인터넷 기반 대체 상태 지점을 할당합니다.
- ABC 사이트에 클라이언트를 할당합니다.  

### <a name="BKMK_ConfigureIBCM_MP"></a>클라이언트 설치 후 인터넷 기반 클라이언트 관리용 클라이언트를 구성하려면  

클라이언트가 설치된 후 인터넷 기반 관리 지점을 할당하려면 다음 절차 중 하나를 사용합니다. 첫 번째 절차는 수동 구성이 필요하고 몇몇 클라이언트에 적절합니다. 두 번째 절차는 많은 클라이언트를 구성하는 데 적절합니다.  

#### <a name="configure-clients-for-internet-based-client-management-after-client-installation-from-the-configuration-manager-control-panel"></a>Configuration Manager 제어판에서 클라이언트를 설치한 후 인터넷 기반 클라이언트 관리용 클라이언트 구성  

1. 클라이언트에서 **Configuration Manager** 제어판을 엽니다.  

2. **인터넷** 탭에서 인터넷 기반 관리 지점의 FQDN(정규화된 도메인 이름)을 **인터넷 FQDN**으로 입력합니다.  

    > [!NOTE]  
    > **인터넷** 탭은 클라이언트에 클라이언트 PKI 인증서가 있는 경우에만 사용할 수 있습니다.  

3. 클라이언트가 프록시 서버를 사용하여 인터넷에 액세스하는 경우 프록시 서버 설정을 입력합니다.  

#### <a name="configure-clients-for-internet-based-client-management-after-client-installation-by-using-a-script"></a>스크립트를 사용하여 클라이언트 설치 후 클라이언트를 인터넷 기반 클라이언트 관리용으로 구성  

##### <a name="powershell"></a>PowerShell

1. PowerShell ISE 또는 Visual Studio Code와 같은 PowerShell 인라인 편집기를 엽니다. 메모장과 같은 텍스트 편집기를 사용할 수도 있습니다.

2. 다음 코드 줄을 복사하여 편집기에 삽입합니다. `'mp.contoso.com'`을 인터넷 기반 관리 지점의 인터넷 FQDN으로 바꿉니다.

    ``` PowerShell
    $newInternetBasedManagementPointFQDN = 'mp.contoso.com'
    $client = New-Object -ComObject Microsoft.SMS.Client
    $client.SetInternetManagementPointFQDN($newInternetBasedManagementPointFQDN)
    Restart-Service CcmExec
    $client.GetInternetManagementPointFQDN()
    ```

    > [!NOTE]  
    > 마지막 줄은 새 인터넷 관리 지점 값을 확인하는 데만 필요합니다.
    >
    > 지정된 인터넷 기반 관리 지점을 삭제하려면 따옴표 안에 있는 서버 FQDN 값을 제거합니다. 그러면 이 줄이 `$newInternetBasedManagementPointFQDN = ''`과 같이 됩니다.

3. .ps1 확장명으로 파일을 저장합니다.  

4. 클라이언트 컴퓨터에서 관리자 권한으로 스크립트를 실행합니다. 다음 방법 중 하나를 사용합니다.  

    - 패키지 및 프로그램을 사용하여 파일을 기존 Configuration Manager 클라이언트에 배포합니다.  

    - 파일 탐색기에서 스크립트 파일을 두 번 클릭하여 이 파일을 기존 구성 관리자 클라이언트에서 로컬로 실행합니다.  

변경 내용을 적용하려면 클라이언트를 다시 시작해야 할 수 있습니다.  

## <a name="BKMK_Provision"></a> 클라이언트 설치 속성 프로비전

그룹 정책 및 소프트웨어 업데이트 기반 클라이언트 설치에 대한 클라이언트 설치 속성을 프로비저닝합니다. Windows 그룹 정책을 사용하여 구성 관리자 클라이언트 설치 속성이 있는 컴퓨터를 프로비저닝합니다. 이러한 속성은 컴퓨터의 레지스트리에 저장됩니다. 클라이언트에서 설치할 때 이러한 속성을 읽습니다. 이 절차는 보통 필요하지 않지만, 다음과 같은 일부 클라이언트 설치 시나리오에는 필요할 수 있습니다.  

- 그룹 정책 설정 또는 소프트웨어 업데이트 기반 클라이언트 설치 방법을 사용하고 있습니다. Configuration Manager용으로 Active Directory 스키마를 확장하지 않았습니다.  

- 특정 컴퓨터에서 클라이언트 설치 속성을 재정의하려고 합니다.  

> [!NOTE]  
> CCMSetup.exe 명령줄에 설치 속성이 제공될 경우 컴퓨터에 프로비전된 설치 속성은 사용되지 않습니다.

Configuration Manager 설치 미디어에 `ConfigMgrInstallation.adm`이라는 그룹 정책 관리 템플릿이 제공됩니다. 이 템플릿을 사용하여 설치 속성을 클라이언트 컴퓨터에 프로비전합니다.

> [!TIP]
> 기본적으로 `ConfigMgrInstallation.adm`에서는 255자를 초과하는 문자열을 지원하지 않습니다. 이 구성은 다중 매개 변수 또는 CCMCERTISSUERS처럼 긴 값의 매개 변수를 추가하는 데 영향을 줄 수 있습니다.<!-- SCCMDocs#1648 -->
>
> 이 문제를 해결하려면 다음을 수행합니다.
>
> 1. 메모장에서 `ConfigMgrInstallation.adm`을 엽니다.
> 2. `VALUENAME SetupParameters` 속성에서 `MAXLEN` 값을 더 큰 정수로 변경합니다. 예: `MAXLEN 511`

### <a name="configure-and-assign-client-installation-properties-by-using-a-group-policy-object"></a>그룹 정책 개체를 사용하여 클라이언트 설치 속성 구성 및 할당  

1. Windows 그룹 정책 개체 편집기와 같은 편집기를 사용하여 ConfigMgrInstallation.adm 관리 템플릿을 새 또는 기존 그룹 정책 개체(GPO)로 가져옵니다. 이 파일은 Configuration Manager 설치 미디어의 `TOOLS\ConfigMgrADMTemplates` 폴더에서 찾을 수 있습니다.  

2. 가져온 **클라이언트 배포 설정 구성**설정의 속성을 엽니다.  

3. **사용**을 선택합니다.  

4. **CCMSetup** 상자에서 필요한 CCMSetup 명령줄 속성을 입력합니다. 모든 CCMSetup 명령줄 속성 및 사용 예제에 대한 목록은 [클라이언트 설치 매개 변수 및 속성 정보](/sccm/core/clients/deploy/about-client-installation-properties)를 참조하세요.  

5. Configuration Manager 클라이언트 설치 속성으로 프로비전하려는 컴퓨터에 GPO를 할당합니다.  
