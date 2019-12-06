---
title: Windows에서 클라이언트 업그레이드
titleSuffix: Configuration Manager
description: Configuration Manager에서 Windows 컴퓨터의 클라이언트를 업그레이드합니다.
ms.date: 08/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 6143fd47-48ec-4bca-b53b-5b9b9f067bc3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b811d6bb974dce7e71d986f81d3255d61382737
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70889920"
---
# <a name="how-to-upgrade-clients-for-windows-computers-in-configuration-manager"></a>Configuration Manager에서 Windows 컴퓨터의 클라이언트를 업그레이드하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

클라이언트 설치 방법 또는 자동 클라이언트 업그레이드 기능을 사용하여 Windows 컴퓨터에서 Configuration Manager 클라이언트를 업그레이드합니다. 다음과 같은 클라이언트 설치 방법이 Windows 컴퓨터에서 클라이언트 소프트웨어를 업그레이드하는 올바른 방법입니다.  

- 그룹 정책 설치  

- 로그온 스크립트 설치  

- 수동 설치  

- 업그레이드 설치  

자세한 내용은 [Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.

제외 컬렉션을 지정하여 클라이언트를 업그레이드에서 제외합니다. 자세한 내용은 [업그레이드에서 클라이언트를 제외하는 방법](/sccm/core/clients/manage/upgrade/exclude-clients-windows)을 참조하세요. 제외된 클라이언트는 여전히 CCMSETUP을 다운로드하여 실행하지만 업그레이드되지는 않습니다.

> [!TIP]  
> 서버 인프라를 Configuration Manager 이전 버전에서 업그레이드하는 경우 Configuration Manager 클라이언트를 업그레이드하기 전에 서버 업그레이드를 완료하세요. 이 프로세스에는 모든 현재 분기 업데이트 설치가 포함됩니다. 최신 현재 분기 업데이트에는 클라이언트 최신 버전이 포함됩니다. 모든 Configuration Manager 업데이트를 설치한 후 클라이언트를 업그레이드합니다.

> [!NOTE]
> 업그레이드 중에 클라이언트의 사이트를 다시 할당하려는 경우 `SMSSITECODE` client.msi 속성을 사용하여 새 사이트를 지정합니다. `SMSSITECODE`에 `AUTO` 값을 사용하는 경우 `SITEREASSIGN=TRUE`도 지정합니다. 이 속성은 업그레이드 중에 자동 사이트 다시 할당을 허용합니다. 자세한 내용은 [클라이언트 설치 속성 - SMSSITECODE](/sccm/core/clients/deploy/about-client-installation-properties#smssitecode)를 참조하세요.

## <a name="bkmk_autoupdate"></a> 자동 클라이언트 업그레이드 정보

클라이언트를 최신 Configuration Manager 버전으로 자동 업그레이드하도록 사이트를 구성합니다. Configuration Manager는 할당된 클라이언트의 버전이 계층 구조 버전보다 이전 버전임을 식별하면 클라이언트를 자동으로 업그레이드합니다. 이 시나리오에는 클라이언트가 Configuration Manager 사이트에 할당을 시도할 때 해당 클라이언트를 최신 버전으로 업그레이드하는 작업이 포함됩니다.  

다음 시나리오에서는 클라이언트가 자동으로 업그레이드될 수 있습니다.  

- 클라이언트 버전이 계층 구조에서 사용 중인 버전보다 이전 버전입니다.  

- 중앙 관리 사이트(CAS)의 클라이언트에 언어 팩이 설치되어 있고 기존 클라이언트에는 설치되어 있지 않습니다.  

- 계층의 클라이언트 필수 구성 요소가 클라이언트에 설치된 필수 구성 요소와 버전이 다릅니다.  

- 하나 이상의 클라이언트 설치 파일이 다른 버전입니다.  

> [!NOTE]  
> 계층 구조에 있는 Configuration Manager 클라이언트의 다양한 버전을 식별하려면 **사이트 - 클라이언트 정보** 보고서 폴더에서 **클라이언트 버전별 Configuration Manager 클라이언트 수** 보고서를 사용하세요.  

Configuration Manager는 기본적으로 업그레이드 패키지를 만듭니다. Configuration Manager는 계층 구조의 모든 배포 지점에 자동으로 패키지를 보냅니다. CAS에서 클라이언트 패키지를 변경하는 경우 Configuration Manager는 자동으로 패키지를 업데이트하고 재배포합니다. 변경의 예는 클라이언트 언어 패키지를 추가하는 경우입니다. 자동 클라이언트 업그레이드를 사용하도록 설정하면 모든 클라이언트가 새 클라이언트 언어 패키지를 자동으로 설치합니다.

> [!NOTE]  
> Configuration Manager는 Configuration Manager 클라우드 기반 배포 지점에 클라이언트 업그레이드 패키지를 자동으로 보내지 않습니다.  

계층 구조 전체에서 자동 클라이언트 업그레이드를 사용하도록 설정하세요. 이 구성은 힘을 덜 들이고 클라이언트를 최신 상태로 유지합니다.  

Configuration Manager 사이트 시스템을 클라이언트로도 관리하는 경우 자동 업그레이드 프로세스의 일부로 해당 시스템을 포함할지 여부를 결정합니다. 클라이언트 업그레이드에서 모든 서버 또는 특정 컬렉션을 제외할 수 있습니다. 일부 Configuration Manager 사이트 역할은 클라이언트 프레임워크를 공유합니다. 예를 들어 관리 지점과 풀(pull) 배포 지점이 그렇습니다. 이러한 역할은 사이트를 업데이트할 때 업그레이드되므로 이러한 서버의 클라이언트 버전은 동시에 업데이트됩니다.

## <a name="bkmk_configure"></a> 자동 클라이언트 업그레이드 구성

다음 절차를 사용하여 CAS에서 자동 클라이언트 업그레이드를 구성합니다. 이 구성은 계층 구조의 모든 클라이언트에 적용됩니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장한 다음, **사이트** 노드를 선택합니다.  

1. 리본의 **홈** 탭에 있는 **사이트** 그룹에서 **계층 설정**을 선택합니다.  

1. **클라이언트 업그레이드** 탭으로 전환합니다. 프로덕션 클라이언트의 버전과 날짜를 검토합니다. 클라이언트 업그레이드에 사용하려는 버전인지 확인합니다. 예상한 클라이언트 버전이 아니라면 사전 프로덕션 클라이언트를 프로덕션으로 승격해야 할 수도 있습니다. 자세한 내용은 [사전 프로덕션 컬렉션에서 클라이언트 업그레이드를 테스트하는 방법](/sccm/core/clients/manage/upgrade/test-client-upgrades)을 참조하세요.  

1. **프로덕션 클라이언트를 사용하여 계층 구조의 모든 클라이언트 업그레이드**를 선택합니다. **확인**을 선택하여 확인합니다.  

1. 서버에 클라이언트 업그레이드를 적용하지 않으려면 **서버 업그레이드 안 함**을 선택합니다.  

1. 디바이스가 클라이언트를 업그레이드해야 하는 기간(일)을 지정합니다. 디바이스는 정책을 수신한 후 이 기간(일) 안에 임의의 간격으로 클라이언트를 업그레이드합니다. 이 동작은 많은 수의 클라이언트가 동시에 업그레이드되는 것을 방지합니다.

    > [!NOTE]
    > 클라이언트를 업그레이드하려면 컴퓨터가 실행되고 있어야 합니다. 업그레이드를 받도록 예약된 시간에 컴퓨터가 실행되고 있지 않으면 업그레이드가 이루어지지 않습니다. 컴퓨터가 켜지고 정책을 수신하면 허용되는 기간(일) 내의 임의의 시간 동안 업그레이드가 예약됩니다. 업그레이드할 기간(일)이 만료된 후라면 컴퓨터는 컴퓨터가 켜진 후 24시간 내의 임의의 시간으로 업그레이드를 예약합니다.
    >
    > 이 동작 때문에 정기적으로 종료되는 컴퓨터는 임의로 예약된 업그레이드 시간이 정상 근무 시간 내가 아닌 경우 업그레이드하는 데 예상보다 오래 걸릴 수 있습니다.

1. 클라이언트를 업그레이드에서 제외하려면 **지정한 클라이언트를 업그레이드에서 제외**를 선택하고 제외할 컬렉션을 지정합니다. 자세한 내용은 [업그레이드에서 클라이언트 제외](/sccm/core/clients/manage/upgrade/exclude-clients-windows)를 참조하세요.

1. 사이트가 [사전 준비된 콘텐츠](/sccm/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent)에 대해 사용하도록 설정한 배포 지점에 클라이언트 설치 패키지를 복사하도록 하려면 **클라이언트 설치 패키지를 사전 준비된 콘텐츠에 대해 설정된 배포 지점에 자동으로 배포** 옵션을 선택합니다.  

1. **확인**을 클릭하여 설정을 저장하고 계층 구조 속성을 닫습니다.

클라이언트는 다음에 정책을 다운로드할 때 이 설정을 수신합니다.

> [!NOTE]
> 클라이언트 업그레이드는 사용자가 구성한 Configuration Manager 유지 관리 기간을 준수합니다.

## <a name="next-steps"></a>다음 단계

클라이언트를 업그레이드하는 다른 방법에 대해서는 [Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.

자동 업그레이드에서 특정 클라이언트를 제외합니다. 자세한 내용은 [업그레이드에서 클라이언트를 제외하는 방법](/sccm/core/clients/manage/upgrade/exclude-clients-windows)을 참조하세요.
