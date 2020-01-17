---
title: Endpoint Protection 지점 사이트 시스템 역할 만들기
titleSuffix: Configuration Manager
description: Configuration Manager 클라이언트 컴퓨터에서 보안 및 맬웨어를 관리하도록 Endpoint Protection을 구성하는 방법을 알아봅니다.
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 0a9dc0fe-a942-40a2-bab1-7eeee4d95380
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 5a8714f5bacf97e440bae07834ee6df5430a3d37
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75819644"
---
# <a name="create-an-endpoint-protection-point-site-system-role"></a>Endpoint Protection 지점 사이트 시스템 역할 만들기

*적용 대상: Configuration Manager(현재 분기)*

Endpoint Protection을 사용하려면 먼저 Endpoint Protection 지점 사이트 시스템 역할을 설치해야 합니다. 하나의 사이트 시스템 서버에만 설치해야 하며, 중앙 관리 사이트 또는 독립 실행형 기본 사이트의 계층 구조 맨 위에 설치해야 합니다.

Endpoint Protection용 새 사이트 시스템 서버를 설치할지 아니면 기존 사이트 시스템 서버를 사용할지에 따라 다음 절차 중 하나를 사용합니다.
- [새 사이트 시스템 서버에 설치](#new-site-system-server)
- [기존 사이트 시스템 서버에 설치](#existing-site-system-server)

> [!IMPORTANT]
>  Endpoint Protection 지점을 설치할 때 Endpoint Protection 클라이언트는 Endpoint Protection 지점을 호스트하는 서버에 설치됩니다. 서버에 설치되어 있는 기존 맬웨어 방지 솔루션과 함께 사용할 수 있도록 이 클라이언트에서 서비스 및 검사가 비활성화됩니다. 나중에 이 서버를 Endpoint Protection으로 관리하도록 설정하고 타사 맬웨어 방지 솔루션을 제거하는 옵션을 선택할 경우 타사 제품은 제거되지 않습니다. 이 제품은 수동으로 제거해야 합니다.

## <a name="new-site-system-server"></a>새 사이트 시스템 서버

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.

3.  **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기**를 클릭합니다.

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다.

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **Endpoint Protection 지점** 을 선택하고 **다음**을 클릭합니다.

6.  **Endpoint Protection** 페이지에서 **Endpoint Protection 사용 조건에 동의함** 확인란을 선택하고 **다음**을 클릭합니다.

    > [!IMPORTANT]
    >  사용 조건에 동의하지 않으면 Configuration Manager에서 Endpoint Protection을 사용할 수 없습니다.

7.  **클라우드 보호 서비스** 페이지에서 새 정의 개발을 돕기 위해 Microsoft로 전송하려는 정보 수준을 선택하고 **다음**을 클릭합니다.

    > [!NOTE]
    >  이 옵션은 기본적으로 사용되는 클라우드 보호 서비스(이전에는 Microsoft 활성 보호 서비스 또는 MAPS라고 함) 설정을 구성합니다. 그런 후에 만든 각 맬웨어 방지 정책에 대한 사용자 지정 설정을 구성할 수 있습니다. Microsoft에서 맬웨어 방지 정의를 최신 상태로 유지하는 데 도움이 되는 맬웨어 샘플을 Microsoft에 제공하여 컴퓨터를 보다 안전하게 유지하려면 클라우드 보호 서비스에 가입하세요. 또한 클라우드 보호 서비스에 가입하면 Endpoint Protection 클라이언트가 동적 서명 서비스를 사용하여 Windows 업데이트에 게시되기 전에 새 정의를 다운로드할 수 있습니다. 자세한 내용은 [Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)을 참조하세요.

8.  마법사를 완료합니다.


## <a name="existing-site-system-server"></a>기존 사이트 시스템 서버

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭한 다음 Endpoint Protection에 사용할 서버를 선택합니다.

3.  **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가**를 클릭합니다.

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다.

5.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **Endpoint Protection 지점** 을 선택하고 **다음**을 클릭합니다.

6.  **Endpoint Protection** 페이지에서 **Endpoint Protection 사용 조건에 동의함** 확인란을 선택하고 **다음**을 클릭합니다.

    > [!IMPORTANT]
    >  사용 조건에 동의하지 않으면 Configuration Manager에서 Endpoint Protection을 사용할 수 없습니다.

7.  **클라우드 보호 서비스** 페이지에서 새 정의 개발을 돕기 위해 Microsoft로 전송하려는 정보 수준을 선택하고 **다음**을 클릭합니다.

    > [!NOTE]
    >  이 옵션은 기본적으로 사용되는 클라우드 보호 서비스 설정(이전에는 MAPS라고 함)을 구성합니다. 구성한 각 맬웨어 방지 정책에 대한 사용자 지정 설정을 구성할 수 있습니다. 자세한 내용은 [Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)을 참조하세요.

8.  마법사를 완료합니다.
