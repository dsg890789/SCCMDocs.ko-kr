---
title: BitLocker 셀프 서비스 포털
titleSuffix: Configuration Manager
description: BitLocker 복구를 위해 Configuration Manager에서 사용자 셀프 서비스 포털을 사용 하는 방법
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 88e0ad46-7f0c-4f5c-9b48-54773c23768d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: cf839c9a4f80638194781a8f1f25432f9dcda0cf
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74662541"
---
# <a name="bitlocker-self-service-portal"></a>BitLocker 셀프 서비스 포털

*적용 대상: Configuration Manager (현재 분기)*

<!--3601034-->

Bitlocker [셀프 서비스 포털을 설치한](/configmgr/protect/deploy-use/bitlocker/setup-websites)후 bitlocker가 사용자의 장치를 잠그면 해당 컴퓨터에 독립적으로 액세스할 수 있습니다. 따라서 셀프 서비스 포털을 사용하는 경우 지원 센터 담당자로부터 지원을 받지 않아도 됩니다.

[기본 BitLocker 셀프 서비스 포털의 ![스크린샷](media/bitlocker-self-service-portal.png)](media/bitlocker-self-service-portal.png#lightbox)

> [!IMPORTANT]
> 셀프 서비스 포털에서 복구 키를 가져오려면 사용자가 최소한 한 번 이상 컴퓨터에 로그인 해야 합니다. 이 로그인은 원격 세션이 아니라 장치에 대해 로컬 이어야 합니다. 그렇지 않으면 키 복구를 위해 기술 지원팀에 문의 해야 합니다. 지원 센터 관리자는 [administration and monitoring 웹 사이트](/configmgr/protect/deploy-use/bitlocker/helpdesk-portal) 를 사용 하 여 복구 키를 요청할 수 있습니다.

BitLocker는 다음과 같은 상황에서 장치를 잠글 수 있습니다.

- 사용자가 BitLocker 암호나 PIN을 잊은 경우

- 장치의 OS 파일, BIOS 또는 신뢰할 수 있는 플랫폼 모듈 (TPM)이 변경 되었습니다.

셀프 서비스 포털에서 BitLocker 복구 키를 요청 하려면 다음을 수행 합니다.

1. BitLocker는 장치를 잠글 때 시작 중에 BitLocker 복구 화면을 표시 합니다. 32 자리의 BitLocker 복구 키 ID를 기록 합니다.

1. 다른 컴퓨터의 웹 브라우저에서 셀프 서비스 포털로 이동 합니다 (예: `https://webserver.contoso.com/SelfService`).

1. 알림을 읽고 동의 합니다.

1. **복구 키 id** 필드에 BitLocker 복구 키 id의 처음 8 자리를 입력 합니다. 여러 키가 일치 하는 경우 32 자리를 모두 입력 합니다.

1. 이 요청에 대 한 **이유에** 다음 옵션 중 하나를 선택 합니다.

    - BIOS/TPM 변경
    - OS 수정 됨
    - PIN/암호 분실

1. **키 가져오기**를 선택 합니다. 셀프 서비스 포털에 48 자리의 **BitLocker 복구 키**가 표시 됩니다.

1. 컴퓨터의 BitLocker 복구 화면에 이 48자리 코드를 입력합니다.

> [!NOTE]
> 비활성 기간 후 BitLocker 셀프 서비스 포털이 시간 초과 될 수 있습니다. 예를 들어 5 분 후에 60 초 카운터가 포함 된 시간 제한 경고가 표시 될 수 있습니다.
>
> ![BitLocker 셀프 서비스 포털 시간 제한 경고](media/bitlocker-self-service-portal-timeout-warning.png)
>
> 카운트다운에 응답 하지 않으면 세션이 만료 됩니다.
>
> ![BitLocker 셀프 서비스 포털 세션 만료 페이지](media/bitlocker-self-service-portal-session-expired.png)
