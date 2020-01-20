---
title: 서비스 연결 지점
titleSuffix: Configuration Manager
description: 이 Configuration Manager 사이트 시스템 역할에 대해 알아보고 사용 범위를 이해하고 계획합니다.
ms.date: 01/08/2020
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: da9fa173ea298ba7565b709532be180f60baff73
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76033478"
---
# <a name="about-the-service-connection-point-in-configuration-manager"></a>Configuration Manager의 서비스 연결 지점 정보

*적용 대상: Configuration Manager(현재 분기)*

서비스 연결 지점은 계층 구조에 대한 몇 가지 중요한 기능을 제공하는 사이트 시스템 역할입니다. 서비스 연결 지점을 설정하기 전에 추가적인 사용 범위를 이해하고 계획하세요. 사용량 계획은 이 사이트 시스템 역할을 설정 방법에 영향을 줄 수 있습니다.

- Configuration Manager 인프라에 적용되는 업데이트를 다운로드합니다. 업로드하는 사용량 현황 데이터에 따라 인프라에 대한 관련 업데이트만 사용할 수 있습니다.

- Configuration Manager 인프라에서 사용량 데이터를 업로드합니다. 업로드하는 세부 정보의 수준 또는 양을 제어할 수 있습니다. 자세한 내용은 [사용량 현황 데이터 수준 및 설정](/configmgr/core/servers/deploy/install/setup-reference#bkmk_usage)을 참조하세요.

- Azure에서 [클라우드 관리 게이트웨이](/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway) 배포

- [비즈니스 및 교육용 Microsoft Store](/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business)에서 앱 동기화

- [Azure AD(Azure Active Directory)](/configmgr/core/servers/deploy/configure/about-discovery-methods#azureaddisc)에서 사용자 및 그룹 검색

- [Desktop Analytics](/configmgr/desktop-analytics/overview)를 사용하여 Windows 10 업데이트 및 앱 준비에 대한 인사이트 얻기

각 계층 구조에서 이 역할의 단일 인스턴스를 지원합니다. 이 역할은 계층 구조의 최상위 계층 사이트(CAS(중앙 관리 사이트) 또는 독립 실행형 기본 사이트)에만 설치할 수 있습니다. 독립 실행형 기본 사이트를 더 큰 계층 구조로 확장하는 경우 기본 사이트에서 이 역할을 제거한 다음, CAS에 설치합니다.

## <a name="bkmk_modes"></a> 작동 모드

서비스 연결 지점은 다음 두 가지 작동 모드를 지원합니다.

- **온라인**: 서비스 연결 지점은 24시간마다 업데이트를 자동으로 확인합니다. 현재 인프라 및 제품 버전에 사용 가능한 새 업데이트를 자동으로 다운로드하여 Configuration Manager 콘솔에서 사용할 수 있게 합니다.

- **오프라인**: 서비스 연결 지점은 Microsoft 클라우드 서비스에 연결하지 않습니다. 사용 가능한 업데이트를 수동으로 가져오려면 [서비스 연결 도구](/configmgr/core/servers/manage/use-the-service-connection-tool)를 사용합니다.

### <a name="change-mode"></a>모드 변경

서비스 연결 지점을 설치한 후 온라인 또는 오프라인 모드 사이를 변경하는 경우 SMS_Executive 서비스의 **SMS_DMP_DOWNLOADER** 스레드를 다시 시작합니다. 이 스레드를 다시 시작하면 변경 내용이 적용됩니다. 이 스레드를 다시 시작하려면 Configuration Manager Service Manager를 사용하세요.

> [!TIP]
> 또한 대부분의 사이트 구성 요소를 다시 시작하는 Configuration Manager에 대해 SMS_Executive 서비스를 다시 시작할 수도 있습니다. 또는 SMS_Executive 서비스를 중지했다가 다시 시작하는 사이트 백업과 같은 예약된 작업을 기다립니다.

Configuration Manager Service Manager를 사용하여 SMS_DMP_DOWNLOADER 스레드를 다시 시작하려면 다음과 같이 합니다.

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **시스템 상태**를 확장하고 **구성 요소 상태** 노드를 선택합니다. 리본 메뉴에서 **시작**을 선택한 다음, **Configuration Manager Service Manager**를 선택합니다.

1. 서비스 관리자 탐색 창에서 사이트를 확장하고 **구성 요소**를 확장한 다음, 다시 시작할 구성 요소를 선택합니다. **SMS_DMP_DOWNLOADER**.

1. **구성 요소** 메뉴로 이동하고 **쿼리**를 선택합니다.

1. 구성 요소의 현재 상태를 확인합니다. 그런 다음, **구성 요소** 메뉴로 이동하고 **중지**를 선택합니다.  

1. 구성 요소를 다시 **쿼리**하여 중지되었는지 확인합니다. 그런 다음, **시작** 구성 요소 작업을 선택하여 다시 시작합니다.

## <a name="remote-site-system-requirements"></a>원격 사이트 시스템 요구 사항

사이트 서버의 원격 서버인 사이트 시스템 서버에 서비스 연결 지점을 설치하는 경우 다음 요구 사항을 구성합니다.

- 사이트 서버의 컴퓨터 계정은 원격 서비스 연결 지점을 호스트하는 컴퓨터의 로컬 관리자여야 합니다.

- [사이트 시스템 설치 계정](/configmgr/core/plan-design/hierarchy/accounts#site-system-installation-account)을 사용하여 역할을 호스트하는 사이트 시스템 서버를 설치합니다. 사이트 서버의 배포 관리자는 사이트 시스템 설치 계정을 사용하여 서비스 연결 지점에서 업데이트를 전송합니다.

## <a name="bkmk_urls"></a> 인터넷 액세스 요구 사항

조직에서 방화벽 또는 프록시 디바이스를 사용하여 인터넷과의 네트워크 통신을 제한하는 경우 서비스 연결 지점에서 인터넷 엔드포인트에 액세스하도록 허용해야 합니다.

자세한 내용은 [Internet access requirements](/configmgr/core/plan-design/network/internet-endpoints#bkmk_scp)(인터넷 액세스 요구 사항)를 참조하세요.

## <a name="install"></a>설치

**설치 프로그램**을 실행하여 계층의 최상위 사이트를 설치하면 서비스 연결 지점을 설치할 수 있습니다.

설치 프로그램을 실행한 후 또는 역할을 다시 설치하는 경우, **사이트 시스템 역할 추가** 마법사 또는 **사이트 시스템 서버 만들기** 마법사를 사용합니다. (계층 구조의 최상위 계층 사이트에만 서비스 연결 지점을 설치합니다.) 자세한 내용은 [사이트 시스템 역할 설치](/configmgr/core/servers/deploy/configure/install-site-system-roles)를 참조하세요.

## <a name="bkmk_move"></a> 역할 이동

<!-- SCCMDocs#922 -->
서비스 연결 지점을 다른 서버로 이동해야 하는 다음과 같은 몇 가지 시나리오가 있습니다.

- [복구](/configmgr/core/servers/manage/recover-sites)
- [사이트 서버 고가용성](/configmgr/core/servers/deploy/configure/site-server-high-availability)
- [사이트 확장](/configmgr/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_expand)

서비스 연결 지점을 이동한 후 모든 사이트 기능을 확인합니다. 예를 들어 Azure AD(Azure Active Directory) 테넌트에 대한 모든 연결의 비밀 키를 갱신해야 합니다. 자세한 내용은 [비밀 키 갱신](/sccm/core/servers/deploy/configure/azure-services-wizard#bkmk_renew)을 참조하세요.

## <a name="log-files"></a>로그 파일

Microsoft에 대한 업로드 정보를 보려면 서비스 연결 지점을 실행하는 서버에서 **Dmpuploader.log**를 봅니다. 업데이트 다운로드 진행률은 **Dmpdownloader.log**를 봅니다. 서비스 연결 지점과 관련된 전체 로그 목록은 [로그 파일 - 서비스 연결 지점](/configmgr/core/plan-design/hierarchy/log-files#BKMK_WITLog)을 참조하세요.

## <a name="next-steps"></a>다음 단계

다음 순서도를 사용하여 프로세스 흐름과 키 로그 항목을 이해할 수 있습니다. 이 프로세스에는 업데이트 다운로드 및 다른 사이트로 업데이트 복제가 포함됩니다.

- [순서도 – 업데이트 다운로드](/configmgr/core/servers/manage/download-updates-flowchart)

- [순서도 – 업데이트 복제](/configmgr/core/servers/manage/update-replication-flowchart)
