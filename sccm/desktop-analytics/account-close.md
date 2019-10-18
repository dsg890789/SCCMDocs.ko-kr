---
title: 계정을 종료 하는 방법
titleSuffix: Configuration Manager
description: Azure 계정에서 데스크톱 분석을 제거 하는 방법
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
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72386773"
---
# <a name="how-to-close-your-account"></a>계정을 종료 하는 방법

사용자 환경에서 데스크톱 분석을 설정 하 고이를 제거 해야 한다고 결정 한 경우이 프로세스를 사용 하 여 계정을 닫습니다.

## <a name="prerequisites"></a>Prerequisites

**전역 관리자** 만 Azure Portal의 계정을 닫거나 다시 활성화할 수 있습니다.

## <a name="process-to-offboard"></a>오프 보드로 처리

1. **전역 관리자** 역할이 있는 사용자로 Microsoft 365 장치 관리에서 [데스크톱 분석 포털](https://aka.ms/desktopanalytics) 을 엽니다.

1. **전역 설정** 메뉴에서 **연결 된 서비스**를 선택 합니다. 장치 등록 섹션에서 **Offboard**옵션을 선택 합니다.

1. 계속 하기로 결정 한 경우에는 계정이 닫힙니다.

> [!Important]
> 90 일 후에만이 문서의 나머지 부분을 계속 하거나 다시 활성화 하지 않습니다.
>
> 90 일 동안 대기 하지 않고 계정을 완전히 종결 하려면 먼저 계정을 [다시 설정](/sccm/desktop-analytics/account-reset) 합니다.

## <a name="reactivate"></a>받아야

다음 90 일 동안에는 데스크톱 분석 포털에 액세스 하는 조직의 모든 관리자에 게 offboard에 대 한 알림이 표시 됩니다.

전역 관리자는 90 일 이내에 계정을 다시 활성화할 수 있습니다. 조직의 데스크톱 분석을 복원 하려면 **뒤로 이동**옵션을 선택 합니다.

## <a name="delete-the-solution"></a>솔루션 삭제

> [!Warning]
> 90 일 후에만이 문서의 나머지 부분을 계속 하거나 다시 활성화 하지 않습니다. 이러한 다른 구성 요소를 삭제 하 고 연결을 끊으면 다시 활성화를 시도 하지 마세요.

1. **전역 관리자** 역할이 있는 사용자로 [Azure Portal](https://portal.azure.com) 에 로그인 합니다.

1. **모든 리소스** 에서 데스크톱 분석 작업 영역 이름을 검색 합니다. 이 이름은 서비스에 등록할 때 생성 됩니다.

1. **솔루션**형식 `Microsoft365Analytics(YourWorkspaceName)`를 삭제 합니다.

데스크톱 분석 데이터는 작업 영역에 대 한 데이터 보존 정책에 따라 에이징됩니다. 동일한 작업 영역에서 다른 솔루션을 계속 사용할 수 있습니다.

> [!Important]  
> Windows Analytics와 같은 다른 솔루션과 함께 Log Analytics 작업 영역을 사용 하는 경우 작업 영역을 삭제 하지 마세요.

## <a name="remove-user-and-app-access"></a>사용자 및 앱 액세스 제거

1. **전역 관리자** 역할이 있는 사용자로 [Azure Portal](https://portal.azure.com) 에 로그인 합니다. **Azure Active Directory**로 이동 합니다.

1. **역할 및 관리자**에서 **데스크톱 분석 관리자** 역할을 검색 합니다. 해당 멤버를 제거 합니다.

1. **그룹**에서 다음 그룹의 구성원을 제거 합니다.

    - **M365 Analytics 클라이언트 관리자 (Log Analytics 소유자)**
    - **M365 Analytics 클라이언트 관리자 (Log Analytics 기여자)**

1. **엔터프라이즈 응용 프로그램**에서 다음 앱에 대 한 액세스 권한을 삭제 하거나 취소 합니다.

    - `MaLogAnalyticsReader`

    - ConfigMgr 앱입니다. 이 앱의 이름을 찾으려면 Configuration Manager 콘솔로 이동 합니다. **관리** 작업 영역에서 **Cloud Services**를 확장 하 고 **Azure 서비스** 노드를 선택 합니다. **데스크톱 분석** 서비스의 속성을 열고 **응용 프로그램** 탭으로 전환 합니다. **웹 앱** 은이 Azure 앱입니다.

        > [!Important]  
        > Azure AD에서이 앱을 변경 하기 전에 Configuration Manager의 다른 서비스와 다시 사용 하지 않는지 확인 합니다.

## <a name="disconnect-configuration-manager"></a>Configuration Manager 연결 끊기

1. **전체 관리자** 역할이 있는 사용자로 Configuration Manager 콘솔을 엽니다.

1. **관리** 작업 영역으로 이동 하 여 **Cloud Services**를 확장 하 고 **Azure 서비스** 노드를 선택 합니다.

1. 데스크톱 분석 서비스를 삭제 합니다.

### <a name="delete-collections-for-the-pilot-and-production-deployments"></a>파일럿 및 프로덕션 배포에 대 한 컬렉션 삭제

1. Configuration Manager 콘솔의 **자산 및 호환성** 작업 영역에서 **장치 컬렉션** 을 선택 합니다.

1. 더 이상 사용 하지 않는 모든 컬렉션을 삭제 합니다. 기본적으로 컬렉션은 **배포 계획** 폴더 아래에 있습니다.  

## <a name="reconfigure-clients"></a>클라이언트 다시 구성

### <a name="unenroll-devices"></a>등록 취소 장치

등록 된 장치에서 다음 Windows 레지스트리 키의 CommercialID 값을 제거 합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

### <a name="windows-diagnostic-data-configuration"></a>Windows 진단 데이터 구성

장치에서 진단 데이터를 계속 전송 하지 않도록 하려면 다음을 수행 합니다.

- Windows 10: 진단 데이터 수준을 **보안** 으로 설정
- Windows 7 SP1 또는 8.1: **상업용 데이터 옵트인 키** 사용 안 함

다음 방법 중 하나를 사용 하 여 이러한 값을 설정 합니다.

- 그룹 정책, **컴퓨터 구성**  > **관리 템플릿**  > **Windows 구성 요소**  > **데이터 수집 및 Preview 빌드**
- [Microsoft Intune](https://docs.microsoft.com/intune/device-restrictions-windows-10#reporting-and-telemetry) 와 같은 MDM (모바일 장치 관리)

자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)을 참조하세요.

> [!NOTE]  
> 이러한 변경 내용을 적용 하면 장치는 즉시 진단 데이터 전송을 중지 합니다. Microsoft에서 작업 영역에 대 한 정보 처리를 중지 하는 데 24-48 시간이 걸릴 수 있습니다. Microsoft는 30 일 이내에 클라우드 서비스에서이 데이터를 삭제 합니다.
