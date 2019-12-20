---
title: BitLocker 관리 플랜
titleSuffix: Configuration Manager
description: Configuration Manager를 사용 하 여 BitLocker 드라이브 암호화 관리 계획
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: a4d8cda2-bc9b-4fb4-aa0d-23c31b4fc60b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 25f8b13cbf0aa6e505c7fe22980e5bce3a39a2e4
ms.sourcegitcommit: 3a0eaf3378632f312b46b2b8a524e286f9c4cd8e
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/19/2019
ms.locfileid: "75198730"
---
# <a name="plan-for-bitlocker-management"></a>BitLocker 관리 플랜

*적용 대상: Configuration Manager (현재 분기)*

<!-- 3601034 -->

1910 버전부터 Configuration Manager를 사용 하 여 온-프레미스 Windows 클라이언트에 대 한 MANAGE-BDE (BitLocker 드라이브 암호화)를 관리 합니다. Microsoft BitLocker Administration and Monitoring (MBAM)의 사용을 대체할 수 있는 전체 BitLocker 수명 주기 관리를 제공 합니다.

> [!Note]  
> Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/configmgr/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  

자세한 내용은 [BitLocker 개요](https://docs.microsoft.com/windows/security/information-protection/bitlocker/bitlocker-overview)를 참조하세요.

> [!TIP]
> Microsoft Endpoint Manager 클라우드 서비스를 사용 하 여 공동 관리 되는 Windows 10 장치에서 암호화를 관리 하려면 [ **Endpoint Protection** 워크 로드](/configmgr/comanage/workloads#endpoint-protection) 를 Intune으로 전환 합니다. Intune 사용에 대 한 자세한 내용은 [Windows 암호화](/intune/protect/endpoint-protection-windows-10#windows-encryption)를 참조 하세요.

## <a name="features"></a>기능

이제 Configuration Manager가 BitLocker 드라이브 암호화를 위한 다음과 같은 관리 기능을 제공합니다.

### <a name="client-deployment"></a>클라이언트 배포

Windows 10, Windows 8.1 또는 Windows 7을 실행 하는 관리 되는 Windows 장치에 BitLocker 클라이언트 배포

### <a name="manage-encryption-policies"></a>암호화 정책 관리

- 예: 드라이브 암호화 및 암호화 수준 선택, 사용자 예외 정책 구성, 고정 데이터 드라이브 암호화 설정

- 장치를 암호화 하는 데 사용 하는 알고리즘과 암호화를 위해 대상으로 하는 디스크를 결정 합니다.

- 장치를 사용 하기 전에 사용자가 새 보안 정책을 준수 하도록 강제 합니다.

- 장치 단위로 조직의 보안 프로필을 사용자 지정 합니다.

- 사용자가 OS 드라이브의 잠금을 해제 하는 경우 OS 드라이브 또는 연결 된 모든 드라이브의 잠금 해제 여부를 지정 합니다.

### <a name="compliance-reports"></a>규정 준수 보고서

기본 제공 보고서:

- 볼륨 또는 장치당 암호화 상태
- 장치의 기본 사용자
- 규정 준수 상태
- 비준수 이유

### <a name="administration-and-monitoring-website"></a>웹 사이트 관리 및 모니터링

키 회전 및 기타 BitLocker 관련 지원을 포함 하 여 키 복구에 도움을 주는 Configuration Manager 콘솔 외부에서 조직의 다른 사용자를 허용 합니다. 예를 들어 지원 센터 관리자는 키 복구를 통해 사용자에 게 도움을 줍니다.

### <a name="user-self-service-portal"></a>사용자 셀프 서비스 포털

사용자가 BitLocker로 암호화 된 장치의 잠금을 해제 하기 위해 단일 사용 키로 도움을 줄 수 있습니다. 이 키를 사용 하면 장치에 대 한 새 키가 생성 됩니다.

## <a name="prerequisites"></a>필수 구성 요소

- 1910 버전에서 BitLocker 관리 정책을 만들려면 Configuration Manager **전체 관리자** 역할이 필요 합니다.

- Configuration Manager에서 BitLocker 복구 서비스를 통합 하려면 HTTPS 지원 관리 지점이 필요 합니다. 관리 지점 속성에서 **클라이언트 연결** 설정은 **HTTPS**여야 합니다.

    > [!NOTE]
    > 버전 1910에서는 향상 된 HTTP를 지원 하지 않습니다.

- BitLocker 관리 보고서를 사용 하려면 보고 서비스 지점 사이트 시스템 역할을 설치 합니다. 자세한 내용은 [보고 구성](/configmgr/core/servers/manage/configuring-reporting)을 참조하세요.

    > [!NOTE]
    > 버전 1910에서 **복구 감사 보고서** 는 administration and monitoring 웹 사이트에서 작동 하려면 기본 사이트의 보고 서비스 지점만 사용 합니다.

- 셀프 서비스 포털 또는 administration and monitoring 웹 사이트를 사용 하려면 IIS를 실행 하는 Windows 서버가 필요 합니다. Configuration Manager 사이트 시스템을 다시 사용 하거나 사이트 데이터베이스 서버에 연결 된 독립 실행형 웹 서버를 사용할 수 있습니다. [사이트 시스템 서버에 대해 지원되는 OS 버전](/configmgr/core/plan-design/configs/supported-operating-systems-for-site-system-servers)을 사용합니다.

    > [!NOTE]
    > 버전 1910에서는 기본 사이트 데이터베이스를 사용 하 여 셀프 서비스 포털과 administration and monitoring 웹 사이트만 설치 합니다. 계층에서 각 기본 사이트에 대해 이러한 웹 사이트를 설치 합니다.

- 셀프 서비스 포털을 호스트 하는 웹 서버에서 [MICROSOFT ASP.NET MVC 4.0](https://docs.microsoft.com/aspnet/mvc/mvc4)을 설치 합니다.

- 포털 설치 관리자 스크립트를 실행하는 사용자 계정에는 사이트 데이터베이스 서버에 대한 SQL **sysadmin** 권한이 필요합니다. 설치 프로세스 중 스크립트는 웹 서버 컴퓨터 계정에 대한 로그인, 사용자 및 SQL 역할 권한을 설정합니다. 셀프 서비스 포털 및 administration and monitoring 웹 사이트의 설정을 완료 한 후에는 sysadmin 역할에서이 사용자 계정을 제거할 수 있습니다.

> [!TIP]
> 기본적으로 **BitLocker 사용** 작업 순서 단계는 드라이브의 *사용 된 공간만* 암호화 합니다. BitLocker 관리에서는 *전체 디스크* 암호화를 사용 합니다. 이 작업 순서 단계를 구성 하 여 **전체 디스크 암호화를 사용**하는 옵션을 사용 하도록 설정 합니다. 자세한 내용은 [작업 순서 단계-BitLocker 사용](/configmgr/osd/understand/task-sequence-steps#BKMK_EnableBitLocker)을 참조 하세요.

## <a name="next-steps"></a>다음 단계

[복구 데이터 암호화](/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data) (처음으로 정책을 배포 하기 전에 선택적 필수 구성 요소)

[BitLocker 관리 클라이언트 배포](/configmgr/protect/deploy-use/bitlocker/deploy-management-agent)
