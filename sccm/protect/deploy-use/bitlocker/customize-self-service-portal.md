---
title: 셀프 서비스 포털 사용자 지정
titleSuffix: Configuration Manager
description: BitLocker 관리 셀프 서비스 포털에 사용자 지정 조직 관련 정보 추가
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 6bc26e36-9914-4606-ae8d-f7b23218942f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c35641e809092b832a081dbcba6ad7b5006beb70
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74662411"
---
# <a name="customize-the-self-service-portal"></a>셀프 서비스 포털 사용자 지정

*적용 대상: Configuration Manager (현재 분기)*

<!--3601034-->

[BitLocker 셀프 서비스 포털을 설치한](/configmgr/protect/deploy-use/bitlocker/setup-websites)후에는 조직에 맞게 사용자 지정할 수 있습니다. 사용자 지정 알림, 조직 이름 및 기타 조직 관련 정보를 추가 합니다.

## <a name="branding"></a>브랜딩

조직의 이름, 지원 센터 URL 및 알림 텍스트를 사용 하 여 셀프 서비스 포털을 브랜드 합니다.

1. 셀프 서비스 포털을 호스팅하는 웹 서버에서 관리자 권한으로 로그인 합니다.

1. **인터넷 정보 서비스 (IIS) 관리자** 를 시작 합니다 ( **sn.exe**실행).

1. **사이트**를 확장 하 고 **기본 웹 사이트**를 확장 한 다음 **SelfService** 노드를 선택 합니다. 세부 정보 창의 **ASP.NET** 그룹에서 **응용 프로그램 설정**을 엽니다.

    [![예제 SelfService IIS 관리자에서 응용 프로그램 설정의 스크린샷](media/bitlocker-self-service-iis-app-settings.png)](media/bitlocker-self-service-iis-app-settings.png#lightbox)

1. 변경 하려는 항목을 선택 하 고 **작업** 창에서 **편집**을 선택 합니다. 사용할 새 이름으로 **값** 을 변경 합니다.

    > [!CAUTION]
    > **이름** 값을 변경 하지 마세요. 예를 들어 `CompanyName`변경 하지 않고 `Contoso IT`를 변경 합니다. **이름** 값을 변경 하면 셀프 서비스 포털의 작동이 중지 됩니다.

변경 내용은 즉시 적용 됩니다.

### <a name="supported-branding-values"></a>지원 되는 브랜딩 값

설정할 수 있는 값에 대해서는 다음 표를 참조 하세요.

|Name|설명|기본&nbsp;값|
|--- |--- |--- |
|CompanyName|셀프 서비스 포털이 모든 페이지 맨 위에 헤더로 표시 하는 조직 이름입니다.|`Contoso IT`|
|DisplayNotice|사용자가 승인 해야 하는 초기 통지를 표시 합니다.|`true`|
|HelpdeskText|오른쪽 창에서 "기타 모든 관련 문제에 대 한"|`Contact Helpdesk or IT Department`|
|HelpdeskUrl|HelpdeskText 문자열에 대 한 링크입니다.|(비어 있음)|
|NoticeTextPath|사용자가 승인 해야 하는 초기 알림의 텍스트입니다. 기본적으로 웹 서버의 전체 파일 경로는 `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\Notice.txt`됩니다. 일반 텍스트 편집기에서 파일을 편집 하 고 저장 합니다. 이 경로 값은 SelfService 응용 프로그램을 기준으로 합니다.|`Notice.txt`|

<!-- Not sure if we support changing these values. At a minimum need a description.
|ClientValidationEnabled||`true`|
|UnobtrusiveJavaScriptEnabled||`true`|
-->

기본 셀프 서비스 포털의 스크린샷은 [BitLocker 셀프 서비스 포털](/configmgr/protect/deploy-use/bitlocker/self-service-portal)을 참조 하세요.

> [!TIP]
> 필요한 경우 이러한 문자열 중 일부를 지역화 하 여 다른 언어로 표시할 수 있습니다. 자세한 내용은 [지역화](#bkmk_localize)를 참조하세요.

## <a name="session-time-out"></a>세션 제한 시간

지정 된 비활성 기간이 지나면 사용자 세션이 만료 되도록 하려면 셀프 서비스 포털에 대 한 세션 시간 제한 설정을 변경할 수 있습니다.

1. 셀프 서비스 포털을 호스팅하는 웹 서버에서 관리자 권한으로 로그인 합니다.

1. **인터넷 정보 서비스 (IIS) 관리자** 를 시작 합니다 ( **sn.exe**실행).

1. **사이트**를 확장 하 고 **기본 웹 사이트**를 확장 한 다음 **SelfService** 노드를 선택 합니다. 세부 정보 창의 **ASP.NET** 그룹에서 **세션 상태**를 엽니다.

1. **쿠키 설정** 그룹에서 **제한 시간 (분)** 값을 변경 합니다. 사용자 세션이 만료 되는 시간 (분)입니다. 기본값은 `5`입니다. 시간 제한이 없도록 이 설정을 사용하지 않으려면 값을 `0`으로 설정합니다.

1. **작업** 창에서 **적용**을 선택 합니다.

## <a name="bkmk_localize"></a>기술 지원팀 텍스트 및 URL 지역화

지역화 된 버전의 셀프 서비스 포털 `HelpdeskText` 문과 `HelpdeskUrl` 링크를 구성할 수 있습니다. 이 문자열은 사용자가 포털을 사용할 때 추가적인 지원을 받는 방법을 사용자에 게 알려줍니다. 지역화 된 텍스트를 구성 하는 경우 포털에는 해당 언어로 된 웹 브라우저의 지역화 된 버전이 표시 됩니다. 지역화 된 버전을 찾지 못하면 `HelpdeskText` 및 `HelpdeskUrl` 설정에 기본값을 표시 합니다.

1. 셀프 서비스 포털을 호스팅하는 웹 서버에서 관리자 권한으로 로그인 합니다.

1. **인터넷 정보 서비스 (IIS) 관리자** 를 시작 합니다 ( **sn.exe**실행).

1. **사이트**를 확장 하 고 **기본 웹 사이트**를 확장 한 다음 **SelfService** 노드를 선택 합니다. 세부 정보 창의 **ASP.NET** 그룹에서 **응용 프로그램 설정**을 엽니다.

1. **작업** 창에서 **추가**를 선택 합니다.

1. **응용 프로그램 설정 추가** 창에서 다음 값을 구성 합니다.

    - **이름**: `HelpdeskText_<language>`를 입력 합니다. 여기서 `<language>`는 텍스트의 언어 코드입니다.

      예를 들어 스페인어 (스페인)에서 지역화 된 `HelpdeskText` 문을 만들려면 이름이 `HelpdeskText_es-es`됩니다.

    - **값**: "다른 모든 관련 문제에 대해" 아래 셀프 서비스 포털의 오른쪽 창에 표시할 지역화 된 문자열입니다.

1. **확인** 을 선택 하 여 새 설정을 저장 합니다.

1. 이 프로세스를 반복 하 여 연결 된 `HelpdeskText_<language>` 설정과 일치 하는 `HelpdeskUrl_<language>`에 대 한 새 응용 프로그램 설정을 추가 합니다.

이 프로세스를 반복 하 여 조직에서 지원 되는 모든 언어에 대 한 설정 쌍을 추가 합니다.

## <a name="localize-the-notice-file"></a>알림 파일 지역화

사용자가 셀프 서비스 포털에서 승인 해야 하는 초기 알림의 지역화 된 버전을 구성할 수 있습니다. 기본적으로 웹 서버의 전체 파일 경로는 `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\Notice.txt`됩니다.

지역화 된 알림 텍스트를 표시 하려면 지역화 된 알림 .txt 파일을 만듭니다. 그런 다음 특정 언어 폴더 아래에 저장 합니다. 예: 스페인어 (스페인)의 경우 `Self Service Website\es-es\Notice.txt`.

셀프 서비스 포털은 다음 규칙에 따라 알림 텍스트를 표시 합니다.

- 기본 알림 파일이 없으면 포털에 기본 파일이 없음을 알리는 메시지가 표시 됩니다.

- 해당 언어 폴더에 지역화 된 알림 파일을 만드는 경우 지역화 된 알림 텍스트를 표시 합니다.

- 웹 서버가 알림 파일의 지역화 된 버전을 찾지 못하면 기본 알림을 표시 합니다.

- 사용자가 브라우저를 지역화 된 알림이 없는 언어로 설정 하면 포털에서 기본 알림이 표시 됩니다.

### <a name="create-a-localized-notice-file"></a>지역화 된 알림 파일 만들기

1. 셀프 서비스 포털을 호스팅하는 웹 서버에서 관리자 권한으로 로그인 합니다.

1. `Self Service Website` 응용 프로그램 경로에서 지원 되는 각 언어에 대 한 `<language>` 폴더를 만듭니다. 예를 들어 스페인어 (스페인)의 `es-es` 합니다. 기본적으로 전체 경로는 `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\es-es`됩니다.

    사용할 수 있는 유효한 언어 코드 목록은 [National Language Support (NLS) API Reference(NLS[국가별 언어 지원] API 참조)](https://docs.microsoft.com/windows/win32/intl/locale-identifiers#predefined-locale-identifiers)를 참조하세요.

    > [!TIP]
    > 언어 폴더의 이름은 언어 중립 이름일 수도 있습니다. 예를 들어 스페인어 (스페인 **)의 경우** **와 스페인어** (아르헨티나)의 경우 es 대신 스페인어 **를 사용할 것** 입니다. 사용자가 브라우저를 **es**로 설정 하 고 해당 언어 폴더가 없으면 웹 서버에서 부모 로캘 폴더를 재귀적으로 확인 합니다 **** . 부모 로캘은 .NET에 정의 되어 있습니다. `Self Service Website\es\Notice.txt` 예를 들면 다음과 같습니다. 이 재귀 대체 (fallback)는 .NET 리소스 로드 규칙을 모방 합니다.

1. 지역화 된 텍스트를 사용 하 여 기본 알림 파일의 복사본을 만듭니다. 언어 코드의 폴더에 저장 합니다. 예를 들어 스페인어 (스페인)의 경우 기본적으로 전체 경로가 `C:\inetpub\Microsoft BitLocker Management Solution\Self Service Website\es-es\Notice.txt`됩니다.

조직에서 지원 되는 모든 언어에 대 한 지역화 된 알림 파일에이 프로세스를 반복 합니다.

## <a name="next-steps"></a>다음 단계

셀프 서비스 포털을 설치 하 고 사용자 지정 했으므로 사용해 보세요! 자세한 내용은 [BitLocker 셀프 서비스 포털](/configmgr/protect/deploy-use/bitlocker/self-service-portal)을 참조 하세요.
