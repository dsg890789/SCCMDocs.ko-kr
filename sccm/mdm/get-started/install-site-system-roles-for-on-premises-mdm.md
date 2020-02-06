---
title: 온-프레미스 MDM에 대 한 역할 설치
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)에 필요한 사이트 시스템 역할을 설치 합니다.
ms.date: 01/09/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3768d5930c2523fbc9a5be3e68788206915ec73e
ms.sourcegitcommit: e7583b5e522d01bc8710ec8e0fe3e5f75a281577
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/05/2020
ms.locfileid: "77035235"
---
# <a name="install-site-system-roles-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 사이트 시스템 역할 설치

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하려면 Configuration Manager 사이트에서 다음 사이트 시스템 역할이 필요 합니다.

- 등록 지점

- 등록 프록시 지점

- 배포 지점

- 장치 관리 지점-모바일 장치에 대해 허용 하는 관리 지점

## <a name="requirements-and-limitations"></a>요구 사항 및 제한 사항

- 온-프레미스 MDM을 사용 하려면 HTTPS 통신에 대 한 사이트 시스템 역할을 사용 하도록 설정 해야 합니다. 자세한 내용은 [온-프레미스 MDM에서 신뢰할 수 있는 통신에 대 한 인증서 설정](/sccm/mdm/get-started/set-up-certificates-on-premises-mdm)을 참조 하세요.

- 현재 Configuration Manager 분기는 장치에서 온-프레미스 MDM에 대 한 배포 지점 및 장치 관리 지점으로의 *인트라넷* 연결만 지원 합니다. 그러나 macOS 컴퓨터도 관리 하는 경우 해당 클라이언트는 동일한 역할에 대 한 *인터넷* 연결이 필요 합니다. 배포 지점 및 장치 관리 지점을 구성할 때 **인트라넷 및 인터넷 연결을 허용**하는 옵션을 사용 합니다.

- 인트라넷 연결에 대해 구성 하는 배포 지점의 경우 사이트 경계를 구성 해야 합니다. Configuration Manager은 온-프레미스 MDM에 대 한 IPv4 범위 경계를 지원 합니다. 자세한 내용은 [사이트 경계 및 경계 그룹 정의](/configmgr/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups)를 참조하세요.

- 장치 관리 지점에서 [데이터베이스 복제본](/configmgr/core/servers/deploy/configure/database-replicas-for-management-points) 을 사용 하는 경우 새로 등록 된 장치는 처음에 연결에 실패 합니다. 이 연결 오류는 데이터베이스 복제본에 성공적인 연결에 필요한 새로 등록 된 장치에 대 한 정보가 없기 때문에 발생 합니다. 복제본은 5 분 마다 동기화 됩니다. 장치는 등록 후 처음 5 분 동안 연결 되지 않고 일반적으로 두 번 연결을 시도 합니다. 그러면 장치가 성공적으로 연결 됩니다.

## <a name="add-roles"></a>역할 추가

Configuration Manager 클라이언트를 사용 하 여 관리 하는 장치가 대부분 있는 사이트에 온-프레미스 MDM을 추가 하는 경우 이러한 역할 중 일부가 사이트에 이미 설치 되어 있을 수 있습니다. 예를 들어 배포 지점은 일반적인 역할 이며, macOS 장치를 관리 하려면 장치 관리 지점이 필요 합니다.

사이트에 역할을 추가 하는 방법에 대 한 자세한 내용은 [사이트 시스템 역할 추가](/configmgr/core/servers/deploy/configure/install-site-system-roles)를 참조 하세요.

## <a name="configure-roles"></a>역할 구성

모바일 장치를 관리 하도록 새 역할이 나 기존 역할을 구성 합니다. 아래 단계에 따라 온-프레미스 MDM에 대 한 배포 지점 및 장치 관리 지점이 제대로 작동 하도록 구성 합니다.

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하여 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할** 노드를 선택합니다.

1. 구성 하려는 배포 지점 또는 장치 관리 지점이 있는 사이트 시스템 서버를 선택 합니다. 목록에서 서버를 선택 하 고 사이트 시스템 역할 세부 정보 창에서 **사이트 시스템** 역할을 선택 합니다. 리본 메뉴의 **사이트 역할** 탭에서 **속성**을 선택 합니다.

    > [!TIP]
    > 규모가 많은 사이트에서는 특정 역할이 있는 서버만 표시 하도록 보기의 범위를 지정할 수 있습니다. **서버 및 사이트 시스템 역할** 노드를 선택 하는 경우 리본의 홈 태그에서 **역할이 있는 서버**를 선택 합니다. 그런 다음 사이트에서 현재 사용할 수 있는 역할 목록에서 원하는 역할을 선택 합니다.

    **사이트 시스템 속성**의 **일반** 탭에서 **이름이** FQDN (정규화 된 도메인 이름) 인지 확인 합니다. 속성을 닫습니다.

1. 콘솔 목록에서 온-프레미스 배포 지점 역할이 있는 서버를 선택 합니다. 사이트 시스템 역할 세부 정보 창에서 **배포 지점** 역할을 선택 합니다. 리본 메뉴의 **사이트 역할** 탭에서 **속성**을 선택 합니다. **배포 지점 속성**의 **통신** 탭에서 다음을 수행 합니다.

    1. **HTTPS**를 선택 하 고 **인트라넷 전용 연결 허용**을 선택 합니다.

        > [!IMPORTANT]
        > Configuration Manager 클라이언트를 사용 하 여 macOS 컴퓨터도 관리 하는 경우 **인트라넷 및 인터넷 연결 허용** 을 대신 사용 합니다.

    1. **모바일 장치가이 배포 지점에 연결할 수 있도록 허용**하는 옵션을 사용 하도록 설정 하 고 속성을 닫습니다.

1. **관리 지점** 사이트 시스템 역할에 대 한 속성을 엽니다.

    1. **일반** 탭에서 **HTTPS**를 선택 하 고 **인트라넷 전용 연결 허용**을 선택 합니다.

        > [!IMPORTANT]
        > Configuration Manager 클라이언트를 사용 하 여 macOS 컴퓨터도 관리 하는 경우 **인트라넷 및 인터넷 연결 허용** 을 대신 사용 합니다.

    1. **모바일 장치 및 Mac 컴퓨터가이 관리 지점을 사용할 수 있도록 허용**하는 옵션을 사용 하도록 설정 하 고 속성을 닫습니다.

        > [!NOTE]
        > 이 옵션을 선택 하면 관리 지점이 *장치* 관리 지점으로 전환 됩니다.  

## <a name="next-step"></a>다음 단계

모바일 장치를 관리 하기 위한 역할을 추가 하 고 구성한 후에는 서버를 신뢰할 수 있는 끝점으로 구성 합니다. 이 트러스트는 역할에서 관리 되는 장치를 통신 하 고 등록할 수 있도록 합니다.

> [!div class="nextstepaction"]
> [신뢰할 수 있는 통신에 대 한 인증서 설정](/configmgr/mdm/get-started/set-up-certificates-on-premises-mdm)
