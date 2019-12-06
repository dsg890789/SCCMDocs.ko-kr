---
title: Application Guard 정책 관리
titleSuffix: Configuration Manager
description: Windows Defender Application Guard 정책 만들기 및 배포에 대한 자세한 정보
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 33a6c1d9-4dd8-411c-a748-693a5bd2ea5a
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a9567dc53a204d639b3da5920cf1fc452426a11f
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70892477"
---
# <a name="create-and-deploy-windows-defender-application-guard-policy"></a>Windows Defender Application Guard 정책 만들기 및 배포

*적용 대상: System Center Configuration Manager(현재 분기)*
<!-- 1351960 -->  
Configuration Manager 엔드포인트 보호를 사용하여 [Windows Defender Application Guard (Application Guard)](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) 정책을 만들고 배포할 수 있습니다. 이러한 정책은 운영 체제의 다른 부분에서 액세스할 수 없는 안전하게 격리된 컨테이너에서 신뢰할 수 없는 웹 사이트를 열어 사용자를 보호하는 데 도움이 됩니다.

## <a name="prerequisites"></a>필수 구성 요소

Windows Defender Application Guard 정책을 만들고 배포하려면 Windows 10 Fall Creators Update(1709)를 사용해야 합니다. 정책을 배포하는 Windows 10 디바이스는 네트워크 격리 정책을 사용하여 구성해야 합니다. 자세한 내용은 [Windows Defender Application Guard 개요](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview)를 참조하세요.

## <a name="create-a-policy-and-to-browse-the-available-settings"></a>정책 만들기 및 사용 가능한 설정 검색

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.
2. **자산 및 준수** 작업 영역에서 **개요** > **Endpoint Protection** > **Windows Defender Application Guard**를 선택합니다.
3. **홈** 탭의 **만들기** 그룹에서  **만들기**를 클릭합니다.
4. [문서](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/configure-wd-app-guard)를 참조하여 사용 가능한 설정을 찾아보고 구성할 수 있습니다. Configuration Manager를 사용 하 여 특정 정책 설정을 지정할 수 있습니다.
   - [호스트 상호 작용 설정](#bkmk_HIS)
   - [애플리케이션 동작](#bkmk_ABS)
   - [파일 관리](#bkmk_FM)
5. **네트워크 정의** 페이지에서 회사 ID를 지정하고 회사 네트워크 경계를 정의합니다.

    > [!NOTE]
    > Windows 10 PC는 클라이언트에 하나의 네트워크 격리 목록만 저장합니다. 서로 다른 두 가지 종류의 네트워크 격리 목록을 만들어 다음 클라이언트에 배포할 수 있습니다.
    >
    >  - Windows Information Protection 중 하나
    >  - Windows Defender Application Guard 중 하나
    >
    > 두 정책 모두 배포하는 경우 두 네트워크 격리 목록이 일치해야 합니다. 동일 클라이언트와 일치하지 않는 목록을 배포할 경우 배포가 실패합니다. 자세한 내용은 [Windows Information Protection 설명서](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm)를 참조하세요.

6. 작업이 끝나면 마법사를 완료하고 하나 이상의 Windows 10 1709 디바이스에 정책을 배포합니다.

### <a name="bkmk_HIS"></a> 호스트 상호 작용 설정

호스트 디바이스와 Application Guard 컨테이너 간의 상호 작용을 구성합니다. Configuration Manager 1802 이전 버전에서는 애플리케이션 동작과 호스트 상호 작용이 **설정** 탭에 있었습니다.

- **클립보드** - Configuration Manager 1802 이전 버전에서는 설정에 있었습니다.
  - 허용되는 콘텐츠 형식
    - 텍스트
    - 이미지
- **인쇄:**
  - XPS 인쇄 사용
  - PDF 인쇄 사용
  - 로컬 프린터 인쇄 사용
  - 네트워크 프린터 인쇄 사용
- **그래픽:** (Configuration Manager 1802 버전부터 시작)
  - 가상 그래픽 프로세서 액세스
- **파일:** (Configuration Manager 1802 버전부터 시작)
  - 다운로드한 파일을 호스트에 저장

### <a name="bkmk_ABS"></a> 애플리케이션 동작 설정

Application Guard 세션 내에서 애플리케이션 동작을 구성합니다. Configuration Manager 1802 이전 버전에서는 애플리케이션 동작과 호스트 상호 작용이 **설정** 탭에 있었습니다.

- **콘텐츠:**
  - 엔터프라이즈 사이트에서 타사 플러그인과 같은 비 엔터프라이즈 콘텐츠를 로드할 수 있습니다.
- **기타:**
  - 사용자가 생성한 브라우저 데이터 보존
  - 격리된 Application Guard 세션의 보안 이벤트 감사

### <a name="bkmk_FM"></a> 파일 관리
<!--3555858-->
Configuration Manager 버전 1906부터 사용자가 일반적으로 Application Guard에서 열리는 파일을 신뢰할 수 있도록 하는 정책 설정이 있습니다. 성공적으로 완료되면 파일이 Application Guard 안이 아니라 호스트 디바이스에서 열립니다. Application Guard 정책에 대한 자세한 정보는 [Windows Defender Application Guard 정책 설정 구성](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/configure-wd-app-guard)을 참조하세요.

- **사용자가 Windows Defender Application Guard에서 열리는 파일을 신뢰할 수 있도록 허용** -사용자가 파일을 신뢰할 수 있는 것으로 표시할 수 있습니다. 신뢰할 수 있는 파일은 Application Guard가 아닌 호스트에서 열립니다. Windows 10 버전 1809 이상 클라이언트에 적용 됩니다.
  - **허용 안 함**: 사용자가 파일을 신뢰하는 항목으로 표시할 수 없습니다(기본값).
  - **파일에서 확인: 바이러스 백신:** 바이러스 검사 후 사용자가 파일을 신뢰할 수 있는 것으로 표시할 수 있습니다.
  - **모든 파일:** 사용자가 모든 파일을 신뢰할 수 있는 항목으로 표시할 수 있습니다.

파일 관리를 사용 하도록 설정 하면 클라이언트의 DCMReporting .log에 기록 된 오류가 표시 될 수 있습니다. 아래 오류는 일반적으로 기능에 영향을 주지 않습니다. <!--4619457-->

- 호환 가능한 디바이스 관련:
  - FileTrustCriteria_condition 찾을 수 없음
- 호환되지 않는 디바이스 관련:
  - FileTrustCriteria_condition 찾을 수 없음
  - 맵에서 FileTrustCriteria_condition 찾을 수 없음
  - 다이제스트에서 FileTrustCriteria_condition 찾을 수 없음

Application Guard 설정을 편집 하려면 **자산 및 호환성** 작업 영역에서 **Endpoint Protection** 를 확장 한 다음 **Windows Defender application Guard** 노드를 클릭 합니다. 편집할 정책을 마우스 오른쪽 단추로 클릭한 다음, **속성**을 선택합니다.

## <a name="next-steps"></a>다음 단계

Windows Defender Application Guard에 대한 자세한 내용은 [Windows Defender Application Guard 개요](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/wd-app-guard-overview)를 참조하세요.
[Windows Defender Application Guard FAQ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-application-guard/faq-wd-app-guard).
