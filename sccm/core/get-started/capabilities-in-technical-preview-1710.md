---
title: 기술 미리 보기 1710 | Microsoft Docs
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1710에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: f4706a58-1f11-4eab-b1eb-3d1a0da02d0f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: e668baafac94dfc7da5008c37556c017c5e01c9d
ms.sourcegitcommit: 3936b869d226cea41fa0090e2cbc92bd530db03a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67286101"
---
# <a name="capabilities-in-technical-preview-1710-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1710의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1710에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**이 Technical Preview의 알려진 문제:**
- **Windows 10 버전 1709(Fall Creators Update라고도 함) 지원**.  이 Windows 릴리스부터 Windows 미디어에는 여러 버전이 포함됩니다. 운영 체제 업그레이드 패키지 또는 운영 체제 이미지를 사용하도록 작업 시퀀스를 구성할 때 [Configuration Manager가 사용할 수 있도록 지원되는 버전](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)을 선택해야 합니다.
- **수동 모드의 사이트 서버가 있는 경우 새 미리 보기 버전에 대한 업데이트가 실패합니다**. [수동 모드의 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 미리 보기 버전을 실행할 경우 미리 보기 사이트를 이러한 새 미리 보기 버전으로 성공적으로 업데이트하려면 먼저 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 업데이트를 완료한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Section Template
##  FEATURE
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-for-deploying-powershell-scripts-from-configuration-manager"></a>Configuration Manager에서 PowerShell 스크립트를 배포하기 위한 향상된 기능
이 릴리스에서는 이제 배포하는 PowerShell 스크립트에서 다음과 같은 향상된 기능을 사용하도록 지원합니다. 
- **보안 범위** -  스크립트에서 보안 범위를 사용하여 스크립트 작성 및 실행을 제어합니다. 이는 사용자 그룹을 나타내는 태그를 할당하여 수행됩니다. 보안 범위 사용에 대한 자세한 내용은 [System Center Configuration Manager에 대한 역할 기반 관리 구성](../../core/servers/deploy/configure/configure-role-based-administration.md)을 참조하세요.
- **실시간 모니터링** - 스크립트 실행을 모니터링하는 경우 스크립트가 실행되는 즉시 실시간으로 수행됩니다.
- **매개 변수 유효성 검사** - 스크립트의 각 매개 변수는 **스크립트 매개 변수 속성** 대화 상자를 통해 해당 매개 변수에 대한 유효성 검사를 추가할 수 있습니다. 유효성 검사를 추가한 후에 유효성 검사를 충족하지 않는 매개 변수 값이 입력되면 오류가 발생합니다.

PowerShell 스크립트 배포는 [Tech Preview 1706](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console) Technical Preview에서 처음 소개되었습니다. [Tech Preview 1707](/sccm/core/get-started/capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager) 및 [Tech Preview 1708](/sccm/core/get-started/capabilities-in-technical-preview-1708#improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)에서 향상된 기능이 추가로 제공되었습니다.


### <a name="try-it-out"></a>기능 직접 사용해 보기

스크립트 실행 기능을 사용해 보려면 [스크립트 만들기 및 실행](../../apps/deploy-use/create-deploy-scripts.md)을 참조하세요.



## <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Windows 10 향상된 원격 분석을 Windows Analytics 디바이스 상태와 관련된 데이터만 전송하도록 제한
<!-- 1356148 -->

이 릴리스에서는 이제 Windows 10 원격 분석 데이터 컬렉션 수준을 **고급(제한적)** 으로 설정할 수 있습니다. 이 설정을 사용하면 Windows 10 버전 1709 이상을 사용하여 **고급** 원격 분석 수준의 모든 데이터를 보고하는 디바이스가 없는 환경에서 디바이스에 대해 조치 가능한 통찰력을 얻을 수 있습니다.

고급(제한적) 원격 분석 수준에는 Windows Analytics와 관련된 **고급** 수준에서 수집된 데이터 하위 집합뿐 아니라 기본 레벨의 메트릭도 포함됩니다. 원격 분석 수준에 대한 자세한 내용은 [원격 분석 수준](/windows/privacy/configure-windows-diagnostic-data-in-your-organization#use-group-policy-to-set-the-diagnostic-data-level)을 참조하세요.

### <a name="try-it-out"></a>기능 직접 사용해 보기
클라이언트에서 Windows 10 원격 분석 컬렉션을 구성하려면 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요. **Cloud Services** 창을 열고 Windows 10 원격 분석을 **고급**으로 설정합니다.


## <a name="software-center-no-longer-distorts-icons-larger-than-250x250"></a>소프트웨어 센터는 더 이상 250x250보다 큰 아이콘을 왜곡하지 않음  
<!-- 1356194 -->

이 릴리스를 사용하면 소프트웨어 센터는 더 이상 250x250보다 큰 아이콘을 왜곡하지 않습니다. 소프트웨어 센터는 그러한 아이콘이 흐리게 표시되도록 만듭니다. 이제 최대 512x512 픽셀 크기로 아이콘을 설정할 수 있으며 아이콘은 왜곡 없이 표시됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
소프트웨어 센터에서 앱의 아이콘을 추가합니다. 기능을 사용해 보려면 [애플리케이션 만들기](/sccm/apps/deploy-use/create-applications)를 참조하세요.


## <a name="check-compliance-from-software-center-for-co-managed-devices"></a>소프트웨어 센터에서 공동 관리 디바이스에 대한 준수 확인
<!-- 1356374 -->
이 릴리스에서는 Intune에서 조건부 액세스를 관리하는 경우 사용자는 이제 소프트웨어 센터를 사용하여 공동 관리하는 Windows 10 디바이스의 준수 상태를 확인할 수 있습니다. 자세한 내용은 [Windows 10 디바이스의 공동 관리](./capabilities-in-technical-preview-1709.md#co-management-for-windows-10-devices)를 참조하세요.


## <a name="support-for-exploit-guard"></a>Exploit Guard 지원
이 릴리스는 Windows Defender Exploit Guard에 대한 지원을 추가합니다. Exploit Guard의 네 가지 구성 요소를 모두 관리하는 정책을 구성 및 배포할 수 있습니다. 이러한 구성 요소는 다음과 같습니다.
-   공격 노출 영역 축소
-   폴더 액세스 제어
-   악용 방지
-   네트워크 보호

Exploit Guard 정책 배포를 위한 준수 데이터는 Configuration Manager 콘솔에서 사용할 수 있습니다.

Exploit Guard 및 구체적인 구성 요소와 규칙에 대한 자세한 내용은 Windows 설명서 라이브러리에 있는 [Windows Defender Exploit Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard)를 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
관리되는 디바이스는 Windows 10 1709 Fall Creators Update 이상을 실행해야 하며 구성된 구성 요소 및 규칙에 따라 다음 요구 사항을 충족해야 합니다.

|Exploit Guard 구성 요소 |추가 필수 구성 요소|
|------------------------|------------------------|
| 공격 노출 영역 축소  | 디바이스에서 [Windows Defender AV 실시간 보호]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) 기능을 사용하도록 설정해야 합니다.  |
| 폴더 액세스 제어  | 디바이스에서 [Windows Defender AV 실시간 보호]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) 기능을 사용하도록 설정해야 합니다.   |
| 악용 방지  | 없음  |
| 네트워크 보호  |  디바이스에서 [Windows Defender AV 실시간 보호]( https://docs.microsoft.com/windows/threat-protection/windows-defender-exploit-guard/controlled-folders-exploit-guard) 기능을 사용하도록 설정해야 합니다.  |

### <a name="create-an-exploit-guard-policy----1355468---"></a>Exploit Guard 정책 만들기  <!--1355468 -->
1. Configuration Manager 콘솔에서 **자산 및 준수** > **엔드포인트 보호**로 이동한 다음 **Windows Defender Exploit Guard**를 클릭합니다.
2. **홈** 탭의 **만들기** 그룹에서 **악용 정책 만들기**를 클릭합니다.
3. **구성 항목 만들기 마법사** 의 **일반**페이지에서 구성 항목에 대한 이름 및 선택적 설명을 지정합니다.
4. 그런 다음 이 정책으로 관리할 Exploit Guard 구성 요소를 선택합니다. 선택한 각 구성 요소에 대해 추가 세부사항을 구성할 수 있습니다.
   - **공격 노출 영역 축소:** 차단 또는 감사하려는 Office 위협, 스크립팅 위협 및 이메일 위협을 구성합니다. 이 규칙에서 특정 파일 또는 폴더를 제외할 수도 있습니다.
   - **폴더 액세스 제어:** 차단 또는 감사를 구성한 다음, 이 정책을 무시할 수 있는 앱을 추가합니다.  기본적으로 보호되지 않는 추가 폴더도 지정할 수 있습니다.
   - **악용 방지:**  시스템 프로세스 및 앱의 악용을 완화하기 위한 설정이 포함된 XML 파일을 지정합니다. Windows 10 디바이스의 Windows Defender Security Center 앱에서 이러한 설정을 내보낼 수 있습니다.
   - **네트워크 보호:** 의심스러운 도메인에 대한 액세스를 차단 또는 감사하기 위한 네트워크 보호를 설정합니다.
5. 마법사를 완료하여 나중에 디바이스에 배포할 수 있는 정책을 만듭니다.

### <a name="deploy-an-exploit-guard-policy"></a>Exploit Guard 정책 배포     
Exploit Guard 정책을 만든 후에는 Exploit Guard 정책 배포 마법사를 사용하여 배포합니다. 이를 위해서는 Configuration Manager 콘솔을 열고 **자산 및 준수** > **엔드포인트 보호**로 이동한 다음 **Exploit Guard 정책 배포**를 클릭합니다.

## <a name="limited-support-for-cng-certificates"></a>CNG 인증서에 대한 제한적 지원
<!-- 1356191 -->
이 릴리스부터 [CNG(Cryptography API: Next Generation)](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx) 인증서 템플릿을 사용할 수 있는 시나리오는 다음과 같습니다.

- 클라이언트 등록 및 HTTPS 관리 지점과의 커뮤니케이션.   
- HTTPS 배포 지점을 사용하여 소프트웨어 배포 및 애플리케이션 배포.   
- 운영 체제 배포.  
- 클라이언트 메시징(최신 업데이트 포함) 및 ISV 프록시.   
- 클라우드 관리 게이트웨이 구성.  

CNG 인증서를 사용하려면 CA(인증 기관)가 대상 컴퓨터에 대한 CNG 인증서 서식 파일을 제공해야 합니다.  서식 파일의 세부 사항은 시나리오에 따라 다릅니다. 그러나 다음 특성이 필요합니다.

- **호환성** 탭

    - **인증 기관**은 Windows Server 2008 이상이어야 합니다. (Windows Server 2012 권장)

    - **인증서 수신자**는 Windows Vista/Server 2008 이상이어야 합니다. (Windows 8/Windows Server 2012 권장)

- **암호화** 탭

    - **공급자 범주**는 **주요 스토리지 공급자**여야 합니다.  (필수)

최상의 결과를 위해 Active Directory 정보에서 제목 이름을 빌드하는 것이 좋습니다.  **주체 이름 형식**에 DNS 이름을 사용하고 DNS 이름을 대체 주체 이름에 포함시킵니다.  그렇지 않으면 디바이스가 인증서 프로필에 등록될 때 이 정보를 제공해야 합니다.


## <a name="improved-descriptions-for-pending-computer-restarts-----1356283---"></a>컴퓨터 다시 시작 보류에 대한 향상된 설명   <!--1356283 -->
[기술 미리 보기 1708](/sccm/core/get-started/capabilities-in-technical-preview-1708#restart-computers-from-the-configuration-manager-console)에서는 Configuration Manager 콘솔에서 다시 시작이 보류되어 있는 디바이스를 식별하는 기능을 추가했습니다.

이 기술 미리 보기부터 콘솔은 재부팅을 요청하는 프로세스 또는 작업에 대한 정보를 제공하는 추가 세부 사항을 표시합니다.

## <a name="device-guard-policy-changes----1355092---"></a>Device Guard 정책 변경 <!-- 1355092 -->
1710 기술 미리 보기 빌드에서는 Device Guard 정책에 있어 다음 세 가지가 변경되었습니다.

### <a name="device-guard-policies-renamed-to-windows-defender-application-control-policies"></a>Device Guard 정책의 이름이 Windows Defender 애플리케이션 제어 정책으로 변경
Device Guard 정책의 이름이 Windows Defender 애플리케이션 제어 정책으로 바뀌었습니다. 예를 들어 **Device Guard 정책 만들기 마법사**의 이름이 이제는 **Windows Defender 애플리케이션 제어 정책 만들기 마법사**입니다.

### <a name="restart-is-not-required-to-apply-policies"></a>정책을 적용하려면 다시 시작해야 합니다.
Windows 버전 1709용 Fall Creators Update로 시작하는 경우에는 Windows Defender 애플리케이션 제어 정책을 적용하기 위해 새 Windows 버전을 사용하는 디바이스를 다시 시작할 필요가 없습니다.

다시 시작은 기본적으로 이루어집니다.

#### <a name="try-it-out"></a>기능 직접 사용해 보기  

다시 시작하기를 끄려면 다음 단계를 수행하세요.

1.  **Windows Defender 애플리케이션 제어 정책 만들기** 마법사를 엽니다.
2.  **일반** 페이지에서 **모든 프로세스에 대해 이 정책을 적용할 수 있도록 디바이스 다시 시작 적용** 확인란을 취소합니다.
3.  **다음**을 계속 클릭하여 마법사를 종료합니다.

이전 버전의 Windows에서는 자동화된 다시 시작이 강제 실행됩니다.

### <a name="automatically-run-software-trusted-by-the-intelligent-security-graph"></a>Intelligent Security Graph에서 신뢰하는 소프트웨어를 자동으로 실행

이제 관리자는 잠긴 디바이스가 Microsoft ISG(Intelligent Security Graph)에서 결정된 대로 좋은 평판을 가진 신뢰할 수 있는 소프트웨어를 실행하도록 허용할 수 있는 옵션을 갖게 됩니다. ISG는 Windows Defender SmartScreen 및 기타 Microsoft 서비스로 구성됩니다.

신뢰할 수 있는 소프트웨어가 되도록 하려면 디바이스가 Windows Defender SmartScreen을 실행해야 합니다.

#### <a name="try-it-out"></a>기능 직접 사용해 보기  

Windows Defender SmartScreen을 실행하는 디바이스에서 신뢰할 수 있는 소프트웨어를 실행하도록 하려면 다음 단계를 수행합니다.

1.  **Windows Defender 애플리케이션 제어 정책 만들기** 마법사를 엽니다.
2.  **포함** 페이지에서 **Intelligent Security Graph에서 신뢰하는 소프트웨어 권한 부여** 확인란을 선택합니다.
3.  **신뢰할 수 있는 파일 또는 폴더** 상자에서 원하는 파일과 폴더를 추가합니다.
4.  **다음**을 계속 클릭하여 마법사를 종료합니다.

## <a name="configure-and-deploy-windows-defender-application-guard-policies----1351960---"></a>Windows Defender Application Guard 정책 구성 및 배포 <!-- 1351960 -->

[Windows Defender Application Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97)는 운영 체제의 다른 부분에서 액세스할 수 없는 보안 격리된 컨테이너에서 신뢰할 수 없는 웹 사이트를 열어 사용자를 보호하는 새로운 Windows 기능입니다. 이 Technical Preview에서는 구성하는 Configuration Manager 준수 설정을 사용하여 이 기능을 구성한 다음 컬렉션에 배포하기 위한 지원이 추가되었습니다. 이 기능은 64비트 버전의 Windows 10 크리에이터 업데이트에 대한 미리 보기에 릴리스될 예정입니다(코드명: RS2). 이 기능을 지금 테스트하려면 이 업데이트의 미리 보기 버전을 사용하고 있어야 합니다.

### <a name="before-you-start"></a>시작하기 전에
Windows Defender Application Guard 정책을 만들고 배포하려면 정책을 배포하는 Windows 10 디바이스를 네트워크 격리 정책을 사용하여 구성해야 합니다. 자세한 내용은 뒤에서 언급하는 블로그 게시물을 참조하세요. 이 기능은 현재 Windows 10 참가자 빌드에서만 작동합니다. 이 기능을 테스트하려면 클라이언트에서 최신 Windows 10 참가자 빌드를 실행하고 있어야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

Windows Defender Application Guard에 대한 기본 사항을 이해하려면 [블로그 게시물](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97)을 읽어야 합니다.

정책을 만들고 사용 가능한 설정을 검색하려면
1. **Configuration Manager** 콘솔에서 **자산 및 준수**를 선택합니다.
2. **자산 및 준수** 작업 영역에서 **개요** > **Endpoint Protection** > **Windows Defender Application Guard**를 선택합니다.
3. **홈** 탭의 **만들기** 그룹에서  **만들기**를 클릭합니다.
4. 블로그 게시물을 참조하여 사용 가능한 설정을 찾아보고 구성한 후 기능을 사용해볼 수 있습니다.
5. 이 릴리스에서는 마법사에 네트워크 정의 페이지가 추가되었습니다. 이 페이지에서 회사 ID를 지정하고 회사 네트워크 경계를 정의합니다.

    > [!NOTE]
    > Windows 10 PC는 클라이언트에 하나의 네트워크 격리 목록만 저장합니다. 이 릴리스에서 두 가지 종류의 네트워크 격리 목록(Windows Information Protection의 목록, Windows Defender 애플리케이션 가드의 목록)을 만들고 클라이언트에 배포할 수 있습니다. 두 정책 모두 배포하는 경우 두 네트워크 격리 목록이 일치해야 합니다. 동일 클라이언트와 일치하지 않는 목록을 배포할 경우 배포가 실패합니다.

    네트워크 정의를 지정하는 자세한 방법은 [Windows Information Protection 설명서](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm)에서 참조하세요.

6. 작업이 끝나면 마법사를 완료하고 하나 이상의 Windows 10 디바이스에 정책을 배포합니다.

### <a name="further-reading"></a>추가 참고 자료

Windows Defender Application Guard에 대한 자세한 내용은 [이 블로그 게시물](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97)을 참조하세요. 또한 Windows Defender Application Guard 독립 실행형 모드에 대한 자세한 내용은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903)을 참조하세요.

## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
