---
title: 계정을 종료하는 방법
titleSuffix: Configuration Manager
description: Azure 계정에서 Desktop Analytics를 제거하는 방법
ms.date: 10/17/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6e7d2850-b0af-497e-bbc1-bfc2a7420a7a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0a37062bc945a69bfb6679186954146a337f8aed
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "72386773"
---
# <a name="how-to-close-your-account"></a>계정을 종료하는 방법

사용자 환경에서 Desktop Analytics를 설정한 다음, 이를 제거해야 한다고 결정한 경우 이 프로세스를 사용하여 계정을 닫습니다.

## <a name="prerequisites"></a>필수 구성 요소

**전역 관리자**만 Azure Portal에서 계정을 닫거나 다시 활성화할 수 있습니다.

## <a name="process-to-offboard"></a>등록 취소로 처리

1. **전역 관리자** 역할을 가진 사용자로 Microsoft 365 Device Management에서 [Desktop Analytics 포털](https://aka.ms/desktopanalytics)을 엽니다.

1. **글로벌 설정** 메뉴에서 **연결된 서비스**를 선택합니다. 디바이스 등록 섹션에서 **등록 취소** 옵션을 선택합니다.

1. 계속하기로 결정하면 계정이 닫힙니다.

> [!Important]
> 90일 후에 또는 다시 활성화하지 않는 경우 이 문서의 나머지 부분을 계속합니다.
>
> 90일 동안 기다리지 않고 계정을 완전히 닫으려면 먼저 계정을 [다시 설정](/sccm/desktop-analytics/account-reset)합니다.

## <a name="reactivate"></a>다시 활성화

다음 90일 동안에는 Desktop Analytics 포털에 액세스하는 조직의 모든 관리자에게 등록 취소에 대한 알림이 표시됩니다.

전역 관리자는 90일 이내에 계정을 다시 활성화할 수 있습니다. 조직에 대한 Desktop Analytics를 복원하려면 **되돌리기** 옵션을 선택합니다.

## <a name="delete-the-solution"></a>솔루션 삭제

> [!Warning]
> 90일 후에 또는 다시 활성화하지 않는 경우 이 문서의 나머지 부분을 계속합니다. 이러한 다른 구성 요소를 삭제하고 연결을 끊으면 다시 활성화를 시도하지 마세요.

1. [Azure Portal](https://portal.azure.com)에 **전역 관리자** 역할이 있는 사용자로 로그인합니다.

1. **모든 리소스**에서 Desktop Analytics 작업 영역의 이름을 검색합니다. 이 이름은 서비스에 가입할 때 생성됩니다.

1. **솔루션** 형식의 `Microsoft365Analytics(YourWorkspaceName)`를 삭제합니다.

Desktop Analytics 데이터는 작업 영역에 대한 데이터 보존 정책에 따라 에이징됩니다. 동일한 작업 영역에서 다른 솔루션을 계속 사용할 수 있습니다.

> [!Important]  
> Windows Analytics와 같은 다른 솔루션과 함께 Log Analytics 작업 영역을 사용하는 경우 작업 영역을 삭제하지 마세요.

## <a name="remove-user-and-app-access"></a>사용자 및 앱 액세스 제거

1. [Azure Portal](https://portal.azure.com)에 **전역 관리자** 역할이 있는 사용자로 로그인합니다. **Azure Active Directory**로 이동합니다.

1. **역할 및 관리자**에서 **Desktop Analytics 관리자** 역할을 검색합니다. 해당 멤버를 제거합니다.

1. **그룹**에서 다음 그룹의 멤버를 제거합니다.

    - **M365 Analytics 클라이언트 관리자(Log Analytics 소유자)**
    - **M365 Analytics 클라이언트 관리자(Log Analytics 기여자)**

1. **Enterprise 애플리케이션**에서 다음 앱에 대한 액세스 권한을 삭제하거나 취소합니다.

    - `MaLogAnalyticsReader`

    - ConfigMgr 앱 이 앱의 이름을 찾으려면 Configuration Manager 콘솔로 이동합니다. **관리** 작업 영역에서 **Cloud Services**를 펼친 다음, **Azure 서비스** 노드를 선택합니다. **Desktop Analytics** 서비스의 속성을 열고, **애플리케이션** 탭으로 전환합니다. **웹앱**이 Azure 앱입니다.

        > [!Important]  
        > Azure AD에서 이 앱을 변경하기 전에 Configuration Manager의 다른 서비스와 다시 사용하지 않는지 확인합니다.

## <a name="disconnect-configuration-manager"></a>Configuration Manager 연결 끊기

1. **전체 관리자** 역할을 가진 사용자로 Configuration Manager 콘솔을 엽니다.

1. **관리** 작업 영역으로 이동하여 **Cloud Services**를 펼친 다음, **Azure 서비스** 노드를 선택합니다.

1. Desktop Analytics 서비스를 삭제합니다.

### <a name="delete-collections-for-the-pilot-and-production-deployments"></a>파일럿 및 프로덕션 배포에 대한 컬렉션 삭제

1. Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **디바이스 컬렉션**을 선택합니다.

1. 더 이상 사용하지 않는 모든 컬렉션을 삭제합니다. 기본적으로 컬렉션은 **배포 계획** 폴더 아래에 있습니다.  

## <a name="reconfigure-clients"></a>클라이언트 다시 구성

### <a name="unenroll-devices"></a>디바이스 등록 취소

등록된 디바이스에서 다음 Windows 레지스트리 키의 CommercialID 값을 제거합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

### <a name="windows-diagnostic-data-configuration"></a>Windows 진단 데이터 구성

디바이스에서 진단 데이터를 더 이상 전송하지 않도록 하려면 다음을 수행합니다.

- Windows 10: 진단 데이터 수준을 **보안**으로 설정
- Windows 7 SP1 또는 8.1: **상업용 데이터 옵트인 키**를 사용하지 않도록 설정

다음 방법 중 하나를 사용하여 이러한 값을 설정합니다.

- **컴퓨터 구성** > **관리 템플릿** > **Windows 구성 요소** > **데이터 수집 및 미리 보기 빌드**에서 그룹 정책
- [Microsoft Intune](https://docs.microsoft.com/intune/device-restrictions-windows-10#reporting-and-telemetry)과 같은 MDM(모바일 디바이스 관리)

자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)을 참조하세요.

> [!NOTE]  
> 이러한 변경 내용을 적용하면 디바이스는 즉시 진단 데이터 전송을 중지합니다. Microsoft에서 작업 영역에 대한 인사이트 처리를 중지하는 데 24-48시간이 걸릴 수 있습니다. Microsoft는 30일 이내에 해당 클라우드 서비스에서 이 데이터를 삭제합니다.
