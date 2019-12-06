---
title: 기술 미리 보기 1707
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1707에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 08/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: cb405ba0-8792-4ab7-988b-2f835f3a9550
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7dbd7696821b9c333b556f67e42cdccd086dc2bf
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62228865"
---
# <a name="capabilities-in-technical-preview-1707-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1707의 기능

*적용 대상: System Center Configuration Manager(기술 미리 보기)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1707에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->

**이 Technical Preview의 알려진 문제:**
- **수동 모드인 사이트 서버를 보유한 경우 미리 보기 버전 1707에 대한 업데이트에 실패합니다**. 미리 보기 버전 1706을 실행하고 [수동 모드인 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 경우 미리 보기 사이트를 1707 버전으로 성공적으로 업데이트하기 전에 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 1707 버전을 실행한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.



**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365"></a>Windows 10 및 Office 365에 대한 고속 설치 파일을 위한 클라이언트 피어 캐시 지원
<!-- 1352486 -->
이 릴리스부터 피어 캐시가 Windows 10 콘텐츠 고속 설치 파일과 Office 365 업데이트 파일 배포를 지원합니다. 추가 구성이 필요 없습니다.

## <a name="surface-device-dashboard"></a>Surface 디바이스 대시보드
<!--1355788-->
Surface 디바이스 대시보드는 사용자 환경에 있는 Surface 디바이스에 대한 정보를 제공합니다. 콘솔에서 **Surface 디바이스**  > **모니터링**으로 이동합니다. 다음을 볼 수 있습니다.
- Surfaces의 백분율
- Surface 모델의 백분율
- 상위 5개 운영 체제 버전

전체 디바이스 목록을 보려면 **Surface 모델** 차트의 섹션을 클릭합니다.  

## <a name="configure-and-deploy-windows-defender-application-guard-policies"></a>Windows Defender Application Guard 정책 구성 및 배포
<!-- 1351960 -->

[Windows Defender Application Guard](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#XLxEbcpkuKcFebrw.97)는 운영 체제의 다른 부분에서 액세스할 수 없는 보안 격리된 컨테이너에서 신뢰할 수 없는 웹 사이트를 열어 사용자를 보호하는 새로운 Windows 기능입니다. 이 Technical Preview에서는 구성하는 Configuration Manager 준수 설정을 사용하여 이 기능을 구성한 다음 컬렉션에 배포하기 위한 지원이 추가되었습니다. 이 기능은 64비트 버전의 Windows 10 Fall Creator Update(코드명: RS3)에 대한 미리 보기에 릴리스될 예정입니다. 이 기능을 지금 테스트하려면 이 업데이트의 미리 보기 버전을 사용하고 있어야 합니다.

### <a name="before-you-start"></a>시작하기 전에

Windows Defender Application Guard 정책을 만들고 배포하려면 정책을 배포하는 Windows 10 디바이스를 네트워크 격리 정책을 사용하여 구성해야 합니다. 자세한 내용은 [이 블로그 게시물](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97)을 참조하세요. 이 기능은 현재 Windows 10 참가자 빌드에서만 작동합니다. 이 기능을 테스트하려면 클라이언트에서 최신 Windows 10 참가자 빌드를 실행하고 있어야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

#### <a name="to-create-a-policy-and-to-browse-the-available-settings"></a>정책을 만들고 사용 가능한 설정을 검색하려면

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.
2. **자산 및 준수** 작업 영역에서 **개요** > **Endpoint Protection** > **Windows Defender Application Guard**를 선택합니다.
3. **홈** 탭의 **만들기** 그룹에서  **만들기**를 클릭합니다.
4. 블로그 게시물을 참조하여 사용 가능한 설정을 찾아보고 구성한 후 기능을 사용해볼 수 있습니다.
5. 이 릴리스에서는 마법사에 **네트워크 정의** 페이지가 추가되었습니다. 이 페이지에서 회사 ID를 지정하고 회사 네트워크 경계를 정의합니다.<br>Windows 10 PC는 클라이언트에 하나의 네트워크 격리 목록만 저장합니다. 이 릴리스에서 두 가지 종류의 네트워크 격리 목록(Windows Information Protection의 목록, Windows Defender 애플리케이션 가드의 목록)을 만들고 클라이언트에 배포할 수 있습니다. 두 정책 모두 배포하는 경우 두 네트워크 격리 목록이 일치해야 합니다. 동일 클라이언트와 일치하지 않는 목록을 배포할 경우 배포가 실패합니다.
네트워크 정의를 지정하는 자세한 방법은 [Windows Information Protection 설명서](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm)에서 참조하세요.
6. 작업이 끝나면 마법사를 완료하고 하나 이상의 Windows 10 디바이스에 정책을 배포합니다.

### <a name="further-reading"></a>추가 참고 자료
Windows Defender Application Guard에 대한 자세한 내용은 [이 블로그 게시물](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97)을 참조하세요. 또한 Windows Defender Application Guard 독립 실행형 모드에 대한 자세한 내용은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903)을 참조하세요.

## <a name="add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager"></a>Configuration Manager에서 PowerShell 스크립트를 배포할 때 매개 변수 추가

<!-- 1236459 --->

지난 기술 미리 보기에서 [Configuration Manager 콘솔에서 PowerShell 스크립트를 작성하고 실행](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console)할 수 있는 새로운 기능을 도입했습니다.
이 기술 미리 보기에서는 이 기능을 확장했습니다. 이제 Configuration Manager가 PowerShell 스크립트를 읽고 스크립트 만들기 마법사에서 매개 변수를 표시합니다. 마법사에서 매개 변수에 대해 스크립트 실행 시 사용할 값을 입력할 수 있습니다. 또는 매개 변수를 비워 둘 수 있습니다. 비워 둘 경우 스크립트를 실행할 때 매개 변수 값을 입력해야 합니다.
이 기술 미리 보기에서 스크립트가 필요로 하는 모든 매개 변수를 제공해야 합니다. 이후 버전에서 선택적 스크립트 매개 변수를 제공할 계획입니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

1. 지침에 따라 [Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행](/sccm/core/get-started/capabilities-in-technical-preview-1706#create-and-run-powershell-scripts-from-the-configuration-manager-console)을 수행하세요.
2. **스크립트 만들기 마법사**의 새 **스크립트 매개 변수** 페이지에서 **편집**을 클릭합니다.
3. 선택한 매개 변수에 대한 값을 입력하고 **확인**을 클릭합니다.
4. 마법사를 완료합니다.

스크립트 실행 시 구성된 매개 변수 값이 사용됩니다.
