---
title: 계정 사용 중지 하는 방법
titleSuffix: Configuration Manager
description: Azure 계정에서 데스크톱 분석을 제거 하는 방법
ms.date: 06/11/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6e7d2850-b0af-497e-bbc1-bfc2a7420a7a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 499d24e20b8220e685cb7aed9adea3f21caa12ae
ms.sourcegitcommit: e3c1eb0b75d79c05a750d49354c851d15d5e26a3
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/13/2019
ms.locfileid: "67039744"
---
# <a name="how-to-close-your-account"></a>계정 사용 중지 하는 방법

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

사용자 환경에서 데스크톱 Analytics를 설정 하 고 다음 제거 하기로 결정 하는 경우 계정을 닫으려면이 프로세스를 사용 합니다.

## <a name="contact-support"></a>지원에 문의

첫 번째 단계는 Microsoft 지원에 문의 하는 것입니다. 데스크톱 분석 계정 닫기 지원 사례를 엽니다. Microsoft 계정의 닫았는지 확인을 받을 때까지 추가 단계를 진행 하지 마십시오.

## <a name="delete-the-solution"></a>솔루션 삭제

1. 에 로그인 합니다 [Azure portal](https://portal.azure.com) 사용자로는 **회사 관리자** 역할입니다.

1. 검색할 **모든 리소스** 데스크톱 Analytics 작업 영역의 이름입니다. 이 이름은 서비스에 등록할 때 만든 새로운입니다.

1. 삭제할 `Microsoft365Analytics(YourWorkspaceName)` 형식의 **솔루션**합니다.

데스크톱 분석 데이터가 완전히 노후 작업 영역에 대 한 데이터 보존 정책에 기반 합니다. 동일한 작업 영역에서 다른 솔루션을 사용 하 여 계속할 수 있습니다.

> [!Important]  
> Windows Analytics와 같은 다른 솔루션을 사용 하 여 Log Analytics 작업 영역을 사용 중인 경우 작업 영역을 삭제 하지 마십시오.

## <a name="remove-user-and-app-access"></a>사용자 및 앱에 대 한 액세스 제거

1. 에 로그인 합니다 [Azure portal](https://portal.azure.com) 사용자로는 **회사 관리자** 역할입니다. 로 이동 **Azure Active Directory**합니다.

1. **역할과 관리자**를 검색 합니다 **데스크톱 분석 관리자** 역할입니다. 해당 멤버를 제거 합니다.

1. **그룹**를 다음 그룹의 구성원을 제거 합니다.

    - **M365 Analytics 클라이언트 관리자 (Log Analytics 소유자)**
    - **M365 Analytics 클라이언트 관리자 (Log Analytics 참가자)**

1. **엔터프라이즈 응용 프로그램**, 삭제 또는 다음 앱에 대 한 액세스 권한을 취소 합니다.

    - `MaLogAnalyticsReader`

    - ConfigMgr 앱입니다. 이 앱의 이름을 찾으려면 Configuration Manager 콘솔로 이동 합니다. 에 **관리** 작업 영역에서 확장 **Cloud Services**, 선택는 **Azure Services** 노드. 속성을 엽니다는 **데스크톱 분석** 서비스 및 전환 하는 **응용 프로그램** 탭 합니다. 합니다 **웹 앱** Azure 앱이 됩니다.

        > [!Important]  
        > 레코드를 Azure AD에서이 앱을 변경 하기 전에 수는 없습니다 다시 사용할 Configuration Manager에서 다른 서비스를 사용 하 여 있는지 확인 합니다.

## <a name="disconnect-configuration-manager"></a>Configuration Manager를 연결 끊기

1. 사용자로 Configuration Manager 콘솔을 엽니다는 **전체 관리자** 역할입니다.

1. 로 이동 합니다 **관리** 작업 영역에서 확장 **Cloud Services**를 선택한는 **Azure Services** 노드.

1. 데스크톱 분석 서비스를 삭제 합니다.

## <a name="reconfigure-clients"></a>클라이언트 다시 구성

### <a name="unenroll-devices"></a>장치를 등록 취소

등록 된 장치에서 다음 Windows 레지스트리 키에서 CommercialID 값을 제거 합니다.

- `HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DataCollection`
- `HKLM:\SOFTWARE\Policies\Microsoft\Windows\DataCollection`

### <a name="windows-diagnostic-data-configuration"></a>Windows 진단 데이터 구성

진단 데이터를 전송 합니다. 계속 하려면 장치와 사용 하지 않으려는 경우:

- Windows 10: 진단 데이터 수준으로 **보안**
- Windows 7 SP1 또는 8.1: 사용 하지 않도록 설정 된 **상용 데이터 옵트인 키**

다음 방법 중 하나를 사용 하 여 이러한 값을 설정 합니다.

- 그룹 정책을 **컴퓨터 구성** > **관리 템플릿** > **Windows 구성 요소**  >  **데이터 수집 및 미리 보기 빌드**
- 모바일 장치 관리 (MDM)와 같은 [Microsoft Intune](https://docs.microsoft.com/intune/device-restrictions-windows-10#reporting-and-telemetry)

자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)을 참조하세요.

> [!NOTE]  
> 이러한 변경 내용을 적용 하면, 장치 즉시 중지 진단 데이터를 전송 합니다. Microsoft insights 작업 영역에 대 한 처리를 중지 하려면 24 ~ 48 시간 걸릴 수 있습니다. Microsoft는 30 일 이하의 해당 클라우드 서비스에서이 데이터를 삭제합니다.
