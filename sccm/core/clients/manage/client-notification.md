---
title: 클라이언트 알림
titleSuffix: Configuration Manager
description: 중앙 Configuration Manager 콘솔에서 즉각적인 작업을 수행하여 클라이언트를 관리합니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: deb8aac8-2bd9-4980-a25b-5f8d93051226
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e0a7334e2c4c47a7de3854b736faf480a35caaa2
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76033992"
---
# <a name="client-notification-in-configuration-manager"></a>Configuration Manager의 클라이언트 알림

*적용 대상: Configuration Manager(현재 분기)*

원격 클라이언트에 대해 즉각적인 작업을 수행하려면 Configuration Manager 콘솔에서 클라이언트 알림 작업을 보냅니다. 개별 디바이스 또는 디바이스 컬렉션에 대해 이러한 작업을 시작합니다.

## <a name="actions"></a>작업

다음 작업은 홈 탭의 디바이스 또는 컬렉션 그룹의 리본에 있습니다.

### <a name="install-client"></a>클라이언트 설치

**클라이언트 설치 마법사**를 엽니다. 이 마법사는 클라이언트 강제 설치를 사용하여 Configuration Manager 클라이언트를 설치합니다. 자세한 내용은 [클라이언트 강제 설치](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_ClientPush)를 참조하세요.

#### <a name="permissions---install-client"></a>권한 - 클라이언트 설치

이 작업에는 **컬렉션** 개체에 대한 **리소스 수정** 및 **읽기** 권한이 필요합니다.

다음 기본 제공 역할은 기본적으로 이 권한을 가집니다.

- 애플리케이션 관리자  
- 전체 관리자  
- 인프라 관리자  
- 운영 관리자  
- OS 배포 관리자  

클라이언트를 푸시해야 하는 모든 사용자 지정 역할에 이 권한을 추가합니다.

### <a name="run-script"></a>스크립트 실행

컬렉션에 있는 모든 클라이언트에서 PowerShell 스크립트를 실행하는 **스크립트 실행** 마법사를 엽니다. 자세한 내용은 [PowerShell 스크립트 만들기 및 실행](/sccm/apps/deploy-use/create-deploy-scripts)을 참조하세요.

#### <a name="permissions---run-script"></a>권한 - 스크립트 실행

이 작업에는 **컬렉션** 개체에 대한 **스크립트 실행** 권한이 필요합니다.

다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.

- 전체 관리자  
- 인프라 관리자  
- 운영 관리자  

스크립트 실행이 필요한 모든 사용자 지정 역할에 이 권한을 추가합니다.

### <a name="start-cmpivot"></a>CMPivot 시작

대상 디바이스에 대해 실시간 쿼리를 실행하는 **CMPivot**을 시작합니다. 자세한 내용은 [CMPivot](/sccm/core/servers/manage/cmpivot)을 참조하세요.

#### <a name="permissions---start-cmpivot"></a>권한 - CMPivot 시작

이 작업에는 [스크립트 실행](#run-script) 작업과 동일한 권한이 필요합니다.

버전 1906부터 **컬렉션** 개체에서 **CMPivot 실행** 권한을 사용할 수 있습니다.

## <a name="client-notification"></a>클라이언트 알림

이 작업은 홈 탭의 디바이스 또는 컬렉션 그룹에서 리본의 **클라이언트 알림** 메뉴에 있습니다.

버전 1806 이전에서 **클라이언트 알림** 옵션은 디바이스 컬렉션 노드에서 또는 디바이스 컬렉션의 멤버 자격을 볼 때만 사용 가능했습니다. 버전 1810부터는 **클라이언트 알림**을 **디바이스** 노드에서 바로 시작할 수 있습니다. 더는 컬렉션 멤버 자격 보기 내에 있을 필요가 없습니다. <!--SCCMDocs-pr issue 2972-->

#### <a name="permissions---client-notification"></a>권한 - 클라이언트 알림

<!--SCCMDocs-pr issue #2972-->
1810 버전부터 클라이언트 알림 작업에서 컬렉션 개체에 대해 **리소스 알림** 권한이 필요합니다. 이 권한은 **클라이언트 알림** 메뉴의 모든 작업에 적용됩니다.

다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.

- 전체 관리자  
- 운영 관리자  

클라이언트 알림 작업이 필요한 모든 사용자 지정 역할에 이 권한을 추가합니다.

### <a name="download-computer-policy"></a>컴퓨터 정책 다운로드

디바이스 정책을 새로 고칩니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 정책 검색 시작](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.  

### <a name="download-user-policy"></a>사용자 정책 다운로드

사용자 정책을 새로 고칩니다.  

### <a name="collect-discovery-data"></a>검색 데이터 수집

DDR(검색 데이터 레코드)을 전송하도록 클라이언트를 트리거합니다. 자세한 내용은 [하트비트 검색](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutHeartbeat)을 참조하세요.  

### <a name="collect-software-inventory"></a>소프트웨어 인벤토리 수집

소프트웨어 인벤토리 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-software-inventory)를 참조하세요.  

### <a name="collect-hardware-inventory"></a>하드웨어 인벤토리 수집

하드웨어 인벤토리 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [하드웨어 인벤토리 소개](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory)를 참조하세요.  

### <a name="evaluate-application-deployments"></a>애플리케이션 배포 평가

애플리케이션 배포 평가 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [배포의 재평가 일정](/sccm/core/clients/deploy/about-client-settings#schedule-re-evaluation-for-deployments)을 참조하세요.  

### <a name="evaluate-software-update-deployments"></a>소프트웨어 업데이트 배포 평가

소프트웨어 업데이트 배포 평가 주기를 실행하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 업데이트 소개](/sccm/sum/understand/software-updates-introduction)를 참조하세요.  

### <a name="switch-to-the-next-software-update-point"></a>다음 소프트웨어 업데이트 지점으로 전환

다음 사용 가능한 소프트웨어 업데이트 지점으로 전환하도록 클라이언트를 트리거합니다. 자세한 내용은 [소프트웨어 업데이트 지점 전환](/sccm/sum/plan-design/plan-for-software-updates#BKMK_SUPSwitching)을 참조하세요.  

### <a name="evaluate-device-health-attestation"></a>디바이스 상태 증명 평가

최신 디바이스 성능 상태를 확인하고 보내도록 Windows 10 클라이언트를 트리거합니다. 자세한 내용은 [상태 증명](/sccm/core/servers/manage/health-attestation)을 참조하세요.  

### <a name="wake-up"></a>절전 모드 해제

버전 1810부터 Wake On LAN 패키지를 보내기 위해 동일한 서브넷에 있는 다른 디바이스를 사용하여 절전 모드를 해제하는 Wake On LAN을 지원하도록 구성된 디바이스를 트리거합니다. 자세한 내용은 [Wake On LAN을 구성하는 방법](/sccm/core/clients/deploy/configure-wake-on-lan)을 참조하세요.

### <a name="restart"></a>다시 시작

선택한 디바이스를 다시 시작하도록 트리거합니다. 자세한 내용은 [클라이언트 다시 시작](/sccm/core/clients/manage/manage-clients#restart-clients)을 참조하세요.

## <a name="client-diagnostics"></a>클라이언트 진단

<!--4433455-->

버전 1910부터, Configuration Manager 콘솔에 **클라이언트 진단**을 위한 새로운 디바이스 작업이 있습니다. 이 릴리스에는 다음 작업이 포함됩니다.

- **자세한 정보 로깅 사용** CCM 구성 요소의 전역 로그 수준을 자세히로 변경하고 디버그 로깅을 사용하도록 설정합니다.
- **자세한 정보 로깅 사용 안 함**: 전역 로그 수준을 기본값으로 변경하고 디버그 로깅을 사용하지 않도록 설정합니다.

> [!IMPORTANT]
> 이러한 작업은 크기 또는 기록이 아니라 로그의 자세한 정도를 변경합니다. 더 자세한 로깅은 더 많은 로그 콘텐츠를 생성할 수 있습니다.

이러한 설정에 대한 자세한 내용은 [로그 파일 정보](/sccm/core/plan-design/hierarchy/about-log-files#bkmk_reg-client)를 참조하세요.

> [!NOTE]
> 관리 지점 역할도 CCM 구성 요소를 사용합니다. 대상 디바이스가 관리 지점이기도 한 경우 이 작업은 해당 역할에도 적용됩니다.

클라이언트의 **diagnostics.log**에서 작업 상태를 추적합니다.

### <a name="prerequisites---client-diagnostics"></a>필수 조건 - 클라이언트 진단

- 대상 클라이언트를 최신 버전으로 업데이트합니다.

- Configuration Manager 관리자는 **리소스 알림** 사용 권한이 있어야 합니다.

  다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.

  - 전체 관리자  
  - 인프라 관리자  

  클라이언트 알림 작업이 필요한 모든 사용자 지정 역할에 이 권한을 추가합니다.

## <a name="endpoint-protection"></a>Endpoint Protection

다음 작업은 **Endpoint Protection** 메뉴에 있습니다. 이 메뉴는 홈 탭의 컬렉션 그룹에 있는 리본에 있습니다. 하나 이상의 디바이스를 선택하면 이러한 작업이 리본의 **선택한 개체** 탭에 표시됩니다.

자세한 내용은 [Configuration Manager의 Endpoint Protection](/sccm/protect/deploy-use/endpoint-protection)을 참조하세요.

### <a name="permissions---endpoint-protection"></a>권한 - Endpoint Protection

이 작업에는 **컬렉션** 개체에 대한 **보안 적용** 권한이 필요합니다.

다음 기본 제공 역할은 기본적으로 이 권한을 갖습니다.

- 전체 관리자  
- Endpoint Protection Manager  
- 운영 관리자  

Endpoint Protection 작업을 트리거해야 하는 모든 사용자 지정 역할에 이 권한을 추가합니다.

### <a name="full-scan"></a>전체 검사

Endpoint Protection 또는 Windows Defender가 *전체* 맬웨어 방지 검사를 실행하도록 트리거합니다.  

### <a name="quick-scan"></a>빠른 검사

*빠른* 맬웨어 방지 검사를 실행하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  

### <a name="download-definition"></a>정의 다운로드

최신 맬웨어 방지 정의를 다운로드하도록 Endpoint Protection 또는 Windows Defender를 트리거합니다.  

## <a name="see-also"></a>참고 항목

- [클라이언트를 관리하는 방법](/sccm/core/clients/manage/manage-clients)
- [컬렉션을 관리하는 방법](/sccm/core/clients/manage/collections/manage-collections)
