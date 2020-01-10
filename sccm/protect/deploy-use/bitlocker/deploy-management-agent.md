---
title: BitLocker 관리 배포
titleSuffix: Configuration Manager
description: Configuration Manager 클라이언트 및 복구 서비스를 관리 지점의 BitLocker 관리 에이전트 배포
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 39aa0558-742c-4171-81bc-9b1e6707f4ea
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 398b85c1dd7aa871027fb71196c3c027c9bf4f75
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75820868"
---
# <a name="deploy-bitlocker-management"></a>BitLocker 관리 배포

*적용 대상: Configuration Manager(현재 분기)*

<!--3601034-->

Configuration Manager의 BitLocker 관리에는 다음 구성 요소가 포함 됩니다.

- **BitLocker 관리 에이전트**: [정책을 만들고](#create-a-policy) [컬렉션에 배포](#deploy-a-policy)하는 경우 장치에서이 에이전트를 사용 하도록 설정 Configuration Manager 합니다.

- **복구 서비스**: 클라이언트에서 BitLocker 복구 데이터를 수신 하는 서버 구성 요소입니다. 자세한 내용은 [복구 서비스](#recovery-service)를 참조 하세요.

BitLocker 관리 정책을 만들고 배포 하기 전에 다음을 수행 합니다.

- [필수 구성 요소](/configmgr/protect/plan-design/bitlocker-management#prerequisites) 검토

- 필요한 경우 사이트 데이터베이스에서 [복구 키를 암호화](/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data) 합니다.

## <a name="create-a-policy"></a>정책 만들기

이 정책을 만들고 배포할 때 Configuration Manager 클라이언트는 장치에서 BitLocker 관리 에이전트를 사용 하도록 설정 합니다.

> [!NOTE]
> 1910 버전에서 BitLocker 관리 정책을 만들려면 Configuration Manager **전체 관리자** 역할이 필요 합니다.

1. Configuration Manager 콘솔에서 **자산 및 규정 준수** 작업 영역으로 이동하여 **Endpoint Protection**를 확장하고 **BitLocker 관리** 노드를 선택합니다.

1. 리본에서 **BitLocker 관리 제어 정책 만들기**를 선택 합니다.

1. **일반** 페이지에서 이름 및 설명(선택 사항)을 지정합니다. 이 정책을 통해 클라이언트에서 사용할 구성 요소를 선택합니다.  

    - **클라이언트 관리**: BitLocker 드라이브 암호화 복구 정보의 키 복구 서비스 백업 관리  

    - **운영 체제 드라이브**: OS 드라이브가 암호화 되어 있는지 여부를 관리 합니다.

1. **설치** 페이지에서 BitLocker 드라이브 암호화에 대 한 다음 설정을 구성 합니다.

    > [!NOTE]
    > Configuration Manager BitLocker를 사용 하도록 설정할 때 이러한 설정을 적용 합니다. 드라이브가 이미 암호화 되어 있거나 진행 중인 경우 이러한 정책 설정에 대 한 변경 내용은 장치에서 드라이브 암호화를 변경 하지 않습니다.
    >
    > 이러한 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 BitLocker는 기본 암호화 방법 (AES 128 비트)을 사용 합니다.

    - Windows 8.1 또는 Windows 7 장치의 경우 **드라이브 암호화 및 암호화 강도를 선택**하는 옵션을 사용 하도록 설정 합니다. 암호화 방법 선택:

        - AES 128 비트, 디퓨저 (Windows 7에만 해당)
        - AES 256 비트, 디퓨저 (Windows 7에만 해당)
        - AES 128 비트 (기본값)
        - AES 256 비트

    - Windows 10 장치의 경우 **드라이브 암호화 및 암호 강도 (windows 10)를 선택**하는 옵션을 사용 하도록 설정 합니다. 그런 다음 OS 드라이브, 고정 데이터 드라이브 및 이동식 데이터 드라이브에 대 한 암호화 방법을 개별적으로 선택 합니다.

        - AES-CBC 128비트
        - AES-CBC 256비트
        - XTS-AES 128비트
        - XTS-AES 256비트

    > [!TIP]
    > BitLocker는 128 또는 256 비트의 구성 가능한 키 길이를 사용 하 여 암호화 알고리즘으로 AES (AES(Advanced Encryption Standard))를 사용 합니다. Windows 10 장치에서 AES 암호화는 CBC (암호 블록 체인) 또는 XTS (암호 블록 가로채기)를 지원 합니다.

1. **클라이언트 관리** 페이지에서 다음과 같은 설정을 지정합니다.

    > [!IMPORTANT]
    > HTTPS 지원 관리 지점이 없는 경우이 설정을 구성 하지 마십시오. 자세한 내용은 [복구 서비스](#recovery-service)를 참조 하세요.

    - **BitLocker 관리 서비스 구성**:이 설정을 사용 하도록 설정 하면 Configuration Manager 자동으로 사이트 데이터베이스에 키 복구 정보를 자동으로 백업 합니다. 이 설정을 사용 하지 않도록 설정 하거나 구성 하지 않으면 Configuration Manager 키 복구 정보가 저장 되지 않습니다.

        - **저장할 BitLocker 복구 정보 선택**: 복구 암호 및 키 패키지를 사용 하거나 복구 암호만 사용 하도록 구성 합니다.

        - **복구 정보를 일반 텍스트로 저장 하도록 허용**: BitLocker 관리 암호화 인증서를 사용 하지 않으면 Configuration Manager 키 복구 정보를 일반 텍스트로 저장 합니다. 자세한 내용은 [복구 데이터 암호화](/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data)를 참조 하세요.

        - **클라이언트 검사 상태 빈도 (분)** : 기본적으로 Configuration Manager 클라이언트는 90 분 마다 BitLocker 복구 정보를 업데이트 합니다.

1. **운영 체제 드라이브** 페이지에서 다음 설정을 지정합니다.  

    - **운영 체제 드라이브 암호화 설정**:이 설정을 사용 하도록 설정 하면 사용자가 OS 드라이브를 보호 해야 하며 BitLocker는 드라이브를 암호화 합니다. 비활성화하면 사용자가 드라이브를 보호할 수 없습니다.  

        > [!Note]  
        > 드라이브가 이미 암호화되었는데 이 설정을 사용하지 않도록 설정할 경우 BitLocker가 드라이브의 암호를 해독합니다.  

    - **호환 되는 tpm 없이 Bitlocker 허용 (암호 필요)** : 장치에 [신뢰할 수 있는 플랫폼 모듈 (TPM)](https://docs.microsoft.com/windows/security/information-protection/tpm/trusted-platform-module-top-node)가 없는 경우에도 bitlocker에서 OS 드라이브를 암호화할 수 있습니다. 이 옵션을 허용 하면 Windows에서 사용자에 게 BitLocker 암호를 지정 하 라는 메시지를 표시 합니다.

    - **운영 체제 드라이브에 대 한 보호기 선택**: TPM 및 PIN을 사용 하거나 tpm만 사용 하도록 구성 합니다.

    - **시작에 대 한 최소 pin 길이 구성**: pin을 요구 하는 경우이 값은 사용자가 지정할 수 있는 가장 짧은 길이입니다. 컴퓨터가 부팅될 때 사용자는 이 PIN을 입력하여 드라이브의 잠금을 해제합니다. 기본적으로 최소 PIN 길이는 `4`입니다.

1. 마법사를 완료합니다.

기존 정책의 설정을 변경 하려면 목록에서 선택 하 고 **속성**을 선택 합니다.

둘 이상의 정책을 만들 때 상대적 우선 순위를 구성할 수 있습니다. 클라이언트에 여러 정책을 배포 하는 경우 해당 설정을 결정 하는 데 우선 순위 값이 사용 됩니다.

## <a name="deploy-a-policy"></a>정책 배포

1. **BitLocker 관리** 노드에서 기존 정책을 선택 합니다. 리본에서 **배포**를 선택 합니다.

1. 배포 대상으로 장치 컬렉션을 선택 합니다.

1. 언제 든 지 장치에서 드라이브를 암호화 하거나 암호를 해독할 수 있도록 하려면 **유지 관리 기간을 벗어나도**관리를 허용 하는 옵션을 선택 합니다. 컬렉션에 유지 관리 기간이 있는 경우 여전히이 BitLocker 정책을 정책 미준수 상태 합니다.

1. **단순** 또는 **사용자 지정** 일정을 구성 합니다. 기본적으로 클라이언트는 12 시간 마다이 정책에 대 한 준수를 평가 합니다.

1. **확인** 을 선택 하 여 정책을 배포 합니다.

동일한 정책의 배포를 여러 개 만들 수 있습니다. 각 배포에 대 한 추가 정보를 보려면 **BitLocker 관리** 노드에서 정책을 선택한 다음 세부 정보 창에서 **배포** 탭으로 전환 합니다.

## <a name="monitor"></a>모니터

**BitLocker 관리** 노드의 세부 정보 창에서 정책 배포에 대 한 기본 준수 통계를 확인 합니다.

- 준수 개수
- 오류 수
- 비준수 개수

**배포** 탭으로 전환 하 여 호환성 비율 및 권장 조치를 확인 합니다. 배포를 선택한 다음 리본에서 **상태 보기**를 선택 합니다. 이 작업을 수행 하면 보기가 **모니터링** 작업 영역 **배포** 노드로 전환 됩니다. 다른 구성 정책 배포의 배포와 마찬가지로,이 보기에서 더 자세한 준수 상태를 볼 수 있습니다.

클라이언트가 BitLocker 관리 정책을 준수 하지 않는 것으로 보고 하는 이유를 이해 하려면 비호환 [코드](/configmgr/protect/tech-ref/bitlocker/non-compliance-codes)를 참조 하세요.

문제 해결에 대 한 자세한 내용은 [BitLocker 문제 해결](/configmgr/protect/tech-ref/bitlocker/troubleshoot)을 참조 하세요.

다음 로그를 사용하여 모니터링하고 문제를 해결합니다.

### <a name="client-logs"></a>클라이언트 로그

- MBAM 이벤트 로고: Windows 이벤트 뷰어에서 애플리케이션 및 서비스 > Microsoft > Windows > MBAM으로 이동합니다.  자세한 내용은 [BitLocker 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/about-event-logs) 및 [클라이언트 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/client-event-logs)정보를 참조 하세요.

- 클라이언트 로그 경로의 **BitlockerMangementHandler.log**, 기본적으로 `%WINDIR%\CCM\Logs`

### <a name="management-point-logs-recovery-service"></a>관리 지점 로그 (복구 서비스)

- 복수 서비스 이벤트 로고: Windows 이벤트 뷰어에서 애플리케이션 및 서비스 > Microsoft > Windows > MBAM으로 이동합니다. 자세한 내용은 [BitLocker 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/about-event-logs) 및 [서버 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/server-event-logs)정보를 참조 하세요.

- 복구 서비스 추적 로그: `<Default IIS Web Root>\Microsoft BitLocker Management Solution\Logs\Recovery And Hardware Service\trace*.etl`

## <a name="recovery-service"></a>복구 서비스

BitLocker 복구 서비스는 Configuration Manager 클라이언트에서 BitLocker 복구 데이터를 수신 하는 서버 구성 요소입니다. BitLocker 관리 정책을 만들 때 사이트에서 복구 서비스를 배포 합니다. Configuration Manager는 각 HTTPS 사용 관리 지점에 복구 서비스를 자동으로 설치 합니다.

> [!IMPORTANT]
> 복구 서비스에는 HTTPS 지원 관리 지점이 필요 합니다. HTTP 또는 다른 사이트 시스템에 대해 구성 하는 관리 지점에는 설치할 수 없습니다.

Configuration Manager은 사이트 데이터베이스에 복구 정보를 저장 합니다. BitLocker 관리 암호화 인증서를 사용 하지 않으면 Configuration Manager 키 복구 정보를 일반 텍스트로 저장 합니다. 자세한 내용은 [복구 데이터 암호화](/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data)를 참조 하세요.

## <a name="migration-considerations"></a>마이그레이션 고려 사항

현재 MBAM (Microsoft BitLocker Administration and Monitoring)을 사용 하는 경우 관리를 Configuration Manager로 원활 하 게 마이그레이션할 수 있습니다. Configuration Manager에서 BitLocker 관리 정책을 배포할 때 클라이언트는 복구 키와 패키지를 Configuration Manager 복구 서비스에 자동으로 업로드 합니다.

### <a name="group-policy"></a>그룹 정책

- BitLocker 관리 설정은 MBAM 그룹 정책 설정과 완전히 호환 됩니다. 장치에서 그룹 정책 설정과 Configuration Manager 정책을 모두 수신 하는 경우 일치 하도록 구성 합니다.

- Configuration Manager는 모든 MBAM 그룹 정책 설정을 구현 하지 않습니다. 그룹 정책에서 추가 설정을 구성 하는 경우 Configuration Manager 클라이언트의 BitLocker 관리 에이전트가 이러한 설정을 준수 합니다.

### <a name="tpm-password-hash"></a>TPM 암호 해시

- 이전 MBAM 클라이언트는 Configuration Manager에 TPM 암호 해시를 업로드 하지 않습니다. 클라이언트는 TPM 암호 해시를 한 번만 업로드 합니다.

- 이 정보를 Configuration Manager recovery 서비스로 마이그레이션해야 하는 경우 장치에서 TPM을 지우십시오. 다시 시작 되 면 복구 서비스에 새 TPM 암호 해시를 업로드 합니다.

### <a name="re-encryption"></a>다시 암호화

Configuration Manager는 이미 BitLocker 드라이브 암호화로 보호 된 드라이브를 다시 암호화 하지 않습니다. 드라이브의 현재 보호와 일치 하지 않는 BitLocker 관리 정책을 배포 하는 경우 호환 되지 않는 것으로 보고 됩니다. 드라이브가 여전히 보호 되 고 있습니다.

예를 들어 PIN 보호 없이 드라이브를 암호화 하는 데 MBAM을 사용 했지만 Configuration Manager 정책에는 PIN이 필요 합니다. 드라이브가 암호화 되어 있더라도 드라이브가 정책과 호환 되지 않습니다.

이 문제를 해결 하려면 먼저 장치에서 BitLocker를 사용 하지 않도록 설정 합니다. 그런 다음 새 설정을 사용 하 여 새 정책을 배포 합니다.

## <a name="next-steps"></a>다음 단계

[BitLocker 보고서 및 포털 설정](/configmgr/protect/deploy-use/bitlocker/setup-websites)
