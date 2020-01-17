---
title: BitLocker administration and monitoring 웹 사이트
titleSuffix: Configuration Manager
description: Configuration Manager에서 BitLocker administration and monitoring 웹 사이트 (기술 지원팀 포털)를 사용 하는 방법
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 81f03922-90f6-4e8f-be65-da64ccb21cf2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f7285d51353ed273858d2dada110ea6fed08e37f
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75820783"
---
# <a name="bitlocker-administration-and-monitoring-website"></a>BitLocker administration and monitoring 웹 사이트

*적용 대상: Configuration Manager(현재 분기)*

<!--3601034-->

BitLocker administration and monitoring 웹 사이트는 BitLocker 드라이브 암호화에 대 한 관리 인터페이스입니다. 이를 지원 센터 포털이 라고도 합니다. 이 웹 사이트를 사용 하 여 보고서를 검토 하 고, 사용자의 드라이브를 복구 하 고, 장치 Tpm을 관리 합니다.

[![기본 BitLocker administration and monitoring 웹 사이트의 스크린샷](media/bitlocker-helpdesk-website.png)](media/bitlocker-helpdesk-website.png#lightbox)

이 구성 요소를 사용 하려면 먼저 웹 서버에 설치 해야 합니다. 자세한 내용은 [BitLocker 보고서 및 포털 설정](/configmgr/protect/deploy-use/bitlocker/setup-websites)을 참조 하세요.

다음 URL을 통해 administration and monitoring 웹 사이트에 액세스 합니다. `https://webserver.contoso.com/HelpDesk`

> [!NOTE]
> 관리 및 모니터링 웹 사이트에서 **복구 감사 보고서**를 볼 수 있습니다. 다른 BitLocker 관리 보고서를 보고 서비스 지점에 추가 합니다. 자세한 내용은 [BitLocker 보고서 보기](/configmgr/protect/deploy-use/bitlocker/view-reports)를 참조 하세요.

## <a name="groups"></a>Groups

Administration and monitoring 웹 사이트의 특정 영역에 액세스 하려면 사용자 계정이 다음 그룹 중 하나에 있어야 합니다. 원하는 이름을 사용 하 여 Active Directory에서 이러한 그룹을 만듭니다. 이 웹 사이트를 설치 하는 경우 이러한 그룹 이름을 지정 합니다. 자세한 내용은 [BitLocker 보고서 및 포털 설정](/configmgr/protect/deploy-use/bitlocker/setup-websites)을 참조 하세요.

|그룹|설명|
|--- |--- |
|BitLocker 지원 센터 관리자|Administration and Monitoring 웹 사이트의 모든 영역에 액세스할 수 있습니다. 사용자가 드라이브를 복구 하는 데 도움을 주는 경우에는 도메인 및 사용자 이름이 아니라 복구 키만 입력 하면 됩니다. 사용자가이 그룹과 BitLocker 기술 지원팀 사용자 그룹의 구성원 인 경우 관리자 그룹 권한이 사용자 그룹 권한을 재정의 합니다.|
|BitLocker 지원 센터 사용자|Administration and Monitoring 웹 사이트의 **TPM 관리** 및 **드라이브 복구** 영역에 액세스할 수 있습니다. 두 영역 중 하나를 사용 하는 경우 사용자의 도메인 및 계정 이름을 비롯 한 모든 필드를 입력 해야 합니다. 사용자가이 그룹과 BitLocker 기술 지원팀 admins 그룹의 구성원 인 경우 관리자 그룹 권한이 사용자 그룹 권한을 재정의 합니다.|
|BitLocker 보고서 사용자|Administration and Monitoring 웹 사이트의 **보고서** 영역에 액세스할 수 있습니다.|

## <a name="manage-tpm"></a>TPM 관리

사용자가 잘못 된 PIN을 너무 많이 입력 하는 경우 TPM을 잠금 할 수 있습니다. TPM 잠금 전에 사용자가 잘못된 PIN을 입력할 수 있는 횟수는 제조업체에 따라 달라집니다. Administration and monitoring 웹 사이트의 **TPM 관리** 영역에서 중앙 집중식 키 복구 데이터 시스템에 액세스 합니다.

TPM 소유권에 대 한 자세한 내용은 [tpm을 구성 하도록 MBAM 구성 및 저장소 소유자 인증 암호](https://docs.microsoft.com/microsoft-desktop-optimization-pack/mbam-v25/mbam-25-security-considerations#bkmk-tpm)를 참조 하세요.

> [!NOTE]
> Windows 10 버전 1607부터 TPM을 프로 비전 할 때 Windows에서 TPM 소유자 암호를 유지 하지 않습니다.

1. 웹 브라우저에서 administration and monitoring 웹 사이트로 이동 합니다 (예: `https://webserver.contoso.com/HelpDesk`).

1. 왼쪽 창에서 **TPM 관리** 영역을 선택 합니다.

    ![BitLocker administration and monitoring 웹 사이트 TPM 관리 페이지](media/bitlocker-admin-manage-tpm.png)

1. 컴퓨터 및 컴퓨터 이름의 정규화된 도메인 이름을 입력합니다.

1. 필요한 경우 사용자의 도메인 및 사용자 이름을 입력 하 여 TPM 소유자 암호 파일을 검색 합니다.

1. **TPM 소유자 암호 파일을 요청**하는 이유를 위해 다음 옵션 중 하나를 선택 합니다.

    - PIN 잠금 다시 설정
    - TPM 설정
    - TPM 해제
    - TPM 암호 변경
    - TPM 지우기
    - 기타

    양식을 **제출** 하면 웹 사이트는 다음 응답 중 하나를 반환 합니다.

    - 일치 하는 TPM 소유자 암호 파일을 찾을 수 없는 경우 오류 메시지를 반환 합니다.

    - 제출된 컴퓨터의 TPM 소유자 암호 파일

    TPM 소유자 암호 파일을 검색 한 후에는 웹 사이트에서 소유자 암호를 표시 합니다.

1. 파일에 암호를 저장 하려면 **저장**을 선택 합니다.

1. **Tpm 관리** 영역에서 **Tpm 잠금 다시 설정** 옵션을 선택 하 고 tpm 소유자 암호 파일을 제공 합니다.

    TPM 잠금이 다시 설정 됩니다. BitLocker는 장치에 대 한 사용자의 액세스를 복원 합니다.

    > [!IMPORTANT]
    > TPM 해시 값 이나 TPM 소유자 암호 파일을 공유 하지 않습니다.

## <a name="drive-recovery"></a>드라이브 복구

### <a name="bkmk_recovery"></a> 복구 모드에서 드라이브 복구

드라이브는 다음과 같은 시나리오에서 복구 모드로 전환 됩니다.

- 사용자가 PIN 또는 암호를 분실 하거나 잊어버린 경우
- TPM (신뢰할 수 있는 모듈 플랫폼)은 컴퓨터의 BIOS 또는 시작 파일에 대 한 변경 내용을 검색 합니다.

복구 암호를 가져오려면 Administration and Monitoring 웹 사이트의 **드라이브 복구** 영역을 사용합니다.

> [!IMPORTANT]
> 복구 암호는 1회 사용 후 만료됩니다. OS 드라이브 및 고정 데이터 드라이브에서는 단일 사용 규칙이 자동으로 적용 됩니다. 이동식 드라이브는 드라이브를 제거 하 고 다시 삽입할 때 적용 됩니다.

1. 웹 브라우저에서 administration and monitoring 웹 사이트로 이동 합니다 (예: `https://webserver.contoso.com/HelpDesk`).

1. 왼쪽 창에서 **드라이브 복구** 영역을 선택 합니다.

    ![BitLocker administration and monitoring 웹 사이트 드라이버 복구 페이지](media/bitlocker-admin-drive-recovery.png)

1. 필요한 경우 사용자의 도메인 및 사용자 이름을 입력 하 여 복구 정보를 확인 합니다.

1. 가능한 일치 복구 키 목록을 보려면 복구 키 ID의 처음 8 자리를 입력 합니다. 정확한 복구 키를 얻으려면 전체 복구 키 ID를 입력 합니다.

1. **드라이브 잠금 해제의 이유로**다음 옵션 중 하나를 선택 합니다.

    - 운영 체제 부팅 순서 변경됨
    - BIOS 변경됨
    - 운영 체제 파일이 수정 됨
    - 시작 키 손실
    - PIN 손실
    - TPM 다시 설정
    - 암호 손실
    - 스마트 카드 손실
    - 기타

    양식을 **제출** 하면 웹 사이트는 다음 응답 중 하나를 반환 합니다.

    - 일치하는 복구 암호가 여러 개인 경우 가능한 여러 개의 일치를 반환합니다.

    - 제출한 사용자의 복구 암호 및 복구 패키지입니다.

        > [!NOTE]
        > 손상된 드라이브를 복구하는 중인 경우, 복구 패키지 옵션에서 드라이브를 복구하는 데 필요한 중요 정보를 BitLocker에 제공합니다.

    - 일치 하는 복구 암호를 찾을 수 없는 경우 오류 메시지를 반환 합니다.

    복구 암호 및 복구 패키지를 검색 한 후에는 웹 사이트에서 복구 암호를 표시 합니다.

1. 암호를 복사 하려면 **키 복사**를 선택 합니다. 복구 암호를 파일에 저장하려면 **저장**을 선택합니다.

드라이브 잠금을 해제 하려면 복구 암호를 입력 하거나 복구 패키지를 사용 하십시오.

### <a name="bkmk_moved"></a> 이동한 드라이브 복구

드라이브를 새 컴퓨터로 이동 하는 경우 TPM이 다르므로 BitLocker는 이전 PIN을 허용 하지 않습니다. 이동한 드라이브를 복구하려면 복구 키 ID를 가져와 복구 암호를 검색합니다.

Administration and Monitoring 웹 사이트의 **드라이브 복구** 영역을 통해 이동한 드라이브를 복구합니다.

1. 이동 된 드라이브가 있는 컴퓨터에서 WinRE (Windows 복구 환경) 모드로 컴퓨터를 시작 합니다.

1. WinRE에서 BitLocker는 이동 된 OS 드라이브를 고정 데이터 드라이브로 처리 합니다. BitLocker는 드라이브의 복구 암호 ID를 표시 하 고 복구 암호를 묻는 메시지를 표시 합니다.

    > [!NOTE]
    > 경우에 따라 시작 프로세스 중에 옵션을 사용할 수 있는 경우 **PIN을 잊은** 경우를 선택 합니다. 그런 다음 복구 모드를 입력 하 여 복구 키 ID를 표시 합니다.

1. Recovery key ID를 사용 하 여 administration and monitoring 웹 사이트에서 복구 암호를 가져옵니다. 자세한 내용은 [복구 모드에서 드라이브 복구](#bkmk_recovery)를 참조 하세요.

원래 컴퓨터에서 TPM 칩을 사용하도록 이동된 드라이브를 구성한 경우 다음 단계를 완료합니다. 그렇지 않은 경우에는 복구 프로세스가 완료된 것입니다.

1. 드라이브의 잠금을 해제 한 후에는 WinRE 모드로 컴퓨터를 시작 합니다. WinRE에서 명령 프롬프트를 열고 `manage-bde` 명령을 사용 하 여 드라이브 암호를 해독 합니다. 원래 TPM 칩이 없는 경우 **TPM + PIN** 보호기를 제거하는 방법은 이 도구를 사용하는 것뿐입니다. 이 명령에 대한 자세한 내용은 [Manage-bde](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-use-bitlocker-drive-encryption-tools-to-manage-bitlocker#bkmk-managebde)를 참조하세요.

1. 완료 되 면 컴퓨터를 정상적으로 시작 합니다. Configuration Manager는 새 컴퓨터의 TPM plus PIN을 사용 하 여 드라이브를 암호화 하는 BitLocker 정책을 적용 합니다.

### <a name="bkmk_corrupted"></a> 손상된 드라이브 복구

Recovery key ID를 사용 하 여 administration and monitoring 웹 사이트에서 복구 키 패키지를 가져옵니다. 자세한 내용은 [복구 모드에서 드라이브 복구](#bkmk_recovery)를 참조 하세요.

1. 컴퓨터에 **복구 키 패키지** 를 저장 한 다음 손상 된 드라이브가 있는 컴퓨터에 복사 합니다.

1. 관리자 권한으로 명령 프롬프트 창을 열고 다음 명령을 입력합니다.

    `repair-bde <corrupted drive> <fixed drive> -kp <key package> -rp <recovery password>`

    다음 값을 바꿉니다.

    - `<corrupted drive>`: 손상 된 드라이브의 드라이브 문자 (예: `D:`
    - `<fixed drive>`: 손상 된 드라이브 보다 크거나 같은 사용 가능한 하드 디스크 드라이브의 드라이브 문자입니다. BitLocker는 손상 된 드라이브의 데이터를 복구 하 여 지정 된 드라이브로 이동 합니다. 이 드라이브의 모든 데이터를 덮어씁니다.
    - `<key package>`: 복구 키 패키지의 위치
    - `<recovery password>`: 연결 된 복구 암호

    예를 들면 다음과 같습니다.

    `repair-bde C: D: -kp F:\RecoveryKeyPackage -rp 111111-222222-333333-444444-555555-666666-777777-888888`

이 명령에 대한 자세한 내용은 [Repair-bde](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-use-bitlocker-drive-encryption-tools-to-manage-bitlocker#bkmk-repairbde)를 참조하세요.

## <a name="reports"></a>보고서

Administration and monitoring 웹 사이트에는 **복구 감사 보고서**가 포함 되어 있습니다. 다른 보고서는 Configuration Manager 보고 서비스 지점에서 사용할 수 있습니다. 자세한 내용은 [BitLocker 보고서 보기](/configmgr/protect/deploy-use/bitlocker/view-reports)를 참조 하세요.

1. 웹 브라우저에서 administration and monitoring 웹 사이트로 이동 합니다 (예: `https://webserver.contoso.com/HelpDesk`).

1. 왼쪽 창에서 **보고서** 영역을 선택 합니다.

1. 상단 메뉴 모음에서 **복구 감사 보고서**를 선택 합니다.

이 보고서에 대 한 자세한 내용은 [복구 감사 보고서](/configmgr/protect/deploy-use/bitlocker/view-reports#bkmk-audit) 를 참조 하세요.

> [!TIP]
> 보고서 결과를 저장 하려면 **보고서** 메뉴 모음에서 **내보내기** 를 선택 합니다.
