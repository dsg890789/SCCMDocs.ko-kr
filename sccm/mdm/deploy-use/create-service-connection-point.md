---
title: 서비스 연결 지점 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager를 사용하여 서비스 연결 지점 만들기
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 617abb22-d22f-41fb-a76b-1c4259e419d2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d0ce47e9ade73d76e99aa5c0d4e5581c713a847a
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62224846"
---
# <a name="create-a-service-connection-point-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune을 사용하여 서비스 연결 지점 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

구독을 만든 후에는 Intue 서비스에 연결하는 데 사용할 수 있는 서비스 연결 지점 사이트 시스템 역할을 설치할 수 있습니다. 이 사이트 시스템 역할은 Intue 서비스에 설정 및 애플리케이션을 푸시합니다.

 서비스 연결 지점은 설정과 소프트웨어 배포 정보를 Configuration Manager에 전송하고 모바일 디바이스에서 상태 및 인벤토리 메시지를 검색합니다. Configuration Manager 서비스는 게이트웨이 역할을 하며 모바일 디바이스와 통신하고 설정을 저장합니다.

> [!NOTE]
>  서비스 연결 지점 사이트 시스템 역할은 중앙 관리 사이트 또는 독립 실행형 기본 사이트에만 설치할 수 있습니다. 서비스 연결 지점에는 인터넷 액세스가 있어야 합니다.


## <a name="configure-the-service-connection-point-role"></a>서비스 연결 지점 역할 구성

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭합니다.

3.  다음 중 해당 단계를 사용하여 새 또는 기존 사이트 시스템 서버에 **서비스 연결 지점** 역할을 추가합니다.

    -   새 사이트 시스템 서버: **홈** 탭의 **만들기** 그룹에서 **사이트 시스템 서버 만들기** 를 클릭하여 사이트 시스템 서버 만들기 마법사를 시작합니다.

    -   기존 사이트 시스템 서버: 서비스 연결 지점 역할을 설치할 서버를 클릭합니다. 그런 다음 **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가** 를 클릭하여 사이트 시스템 역할 추가 마법사를 시작합니다.

4.  **시스템 역할 선택** 페이지에서 **서비스 연결 지점**을 선택하고 **다음**을 클릭합니다.
![서비스 연결 지점 만들기](../media/mdm-service-connection-point.png)

* 마법사 완료

## <a name="how-does-the-service-connection-point-authenticate-with-the-microsoft-intune-service"></a>서비스 연결 지점이 Microsoft Intune 서비스를 인증하는 방법
 서비스 연결 지점은 인터넷을 통해 모바일 디바이스를 관리하는 클라우드 기반 Intune 서비스에 대한 연결을 설정하여 Configuration Manager를 확장합니다. 서비스 연결 지점은 Intune 서비스를 다음과 같이 인증합니다.

1.  Configuration Manager 콘솔에서 Intune 구독을 만들 때 Configuration Manager 관리자가 Azure Active Directory에 연결하여 인증을 받습니다. 그러면 개별 ADFS 서버로 리디렉션되어 사용자 이름과 암호를 입력하라는 메시지가 표시됩니다. 해당 정보를 입력하면 Intune에서 테넌트에 인증서를 발급합니다.

2.  1단계에서 발급된 인증서가 서비스 연결 지점 사이트 역할에 설치되며 Microsoft Intune 서비스와의 이후 모든 통신을 인증하고 권한을 부여하는 데 사용됩니다.

> [!div class="button"]
> [< 이전 단계](terms-and-conditions.md)  [다음 단계 >](enable-platform-enrollment.md)
