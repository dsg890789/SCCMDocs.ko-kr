---
title: "Technical Preview 1607 Configuration Manager의 기능"
description: "System Center Configuration Manager용 Technical Preview 버전 1607에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bb69547-3370-4860-96b0-7fb600c56482
caps.latest.revision: "11"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 4717e0f8eef01501fb5b5790e855c476c1ca4590
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1607-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1607의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1607에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="dmp_edition"></a>Windows 10 버전 업그레이드 정책의 향상 기능

이번 릴리스에서 이 정책이 다음과 같이 향상되었습니다.

* 이제 Microsoft Intune에 등록된 Windows 10 PC 외에도 Configuration Manager를 실행하는 Windows 10 PC에서 버전 업그레이드 정책을 사용할 수 있습니다.
* Windows 10 Professional에서 마법사에 있는 하드웨어와 호환되는 아무 플랫폼으로나 업그레이드할 수 있습니다.

[Windows 10 버전 업그레이드 정책에 대한 자세한 내용 읽기](/sccm/compliance/deploy-use/upgrade-windows-version)

### <a name="try-it-out"></a>기능 직접 사용해 보기

1. [기존 버전 업그레이드 정책 항목](/sccm/compliance/deploy-use/upgrade-windows-version)의 정보를 사용하여 버전 업그레이드 정책을 만듭니다.
2. Configuration Manager 클라이언트를 실행하는 Windows 10 PC에 이 정책을 배포합니다.
정책이 대상 Windows PC에 도달하면 2시간 내에 PC가 다시 시작되어 업그레이드를 적용합니다. 현재 이러한 다시 시작을 무시할 수 없습니다. 정책을 배포할 모든 사용자에게 알리거나 사용자의 근무 시간 외에 정책이 실행되도록 예약해야 합니다.

### <a name="known-issue-with-this-release"></a>이 릴리스의 알려진 문제
Configuration Manager 클라이언트 설정에서 **버전 업그레이드**에 대한 설정을 볼 수 있습니다. 이 릴리스에서는 이러한 설정이 작동하지 않습니다. 위에 나와 있는 지침을 사용하여 Windows 10을 최신 버전으로 업그레이드합니다.

## <a name="customizable-branding-for-software-center-dialogs"></a>소프트웨어 센터 대화 상자에 대한 사용자 지정 가능한 브랜딩

소프트웨어 센터에 대한 사용자 지정 브랜딩은 Configuration Manager 버전 1602에서 도입되었습니다. Technical Preview 버전 1607에서는 해당 브랜딩이 이제 모든 관련 대화 상자 및 작업 표시줄 알림으로 확장되어 소프트웨어 센터 사용자에게 보다 일관된 환경을 제공합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

소프트웨어 센터에 대한 사용자 지정 브랜딩은 다음 규칙에 따라 적용됩니다.

1. 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되지 않은 경우 소프트웨어 센터에서 **컴퓨터 에이전트** 클라이언트 설정 **소프트웨어 센터에 표시되는 조직 이름**에 지정된 조직 이름을 표시합니다. 자세한 내용은 [클라이언트 설정을 구성하는 방법](../../core/clients/deploy/configure-client-settings.md)을 참조하세요.

2. 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할이 설치되어 있는 경우 소프트웨어 센터에서 응용 프로그램 카탈로그 웹 사이트 지점 사이트 서버 역할 속성에 지정된 조직 이름 및 색을 표시합니다. 자세한 내용은 [응용 프로그램 카탈로그 웹 사이트 지점에 대한 옵션 구성](../../core/servers/deploy/configure/configuration-options-for-site-system-roles.md#BKMK_ApplicationCatalog_Website)을 참조하세요.

3. Microsoft Intune 구독을 구성하고 Configuration Manager 환경에 연결한 경우 소프트웨어 센터에서 Intune 구독 속성에 지정된 조직 이름, 색 및 회사 로고를 표시합니다. 자세한 내용은 [Microsoft Intune 구독 구성](/mdm/deploy-use/configure-intune-subscription)을 참조하세요.

## <a name="use-the-same-network-adapter-for-multiple-pxe-initiated-deployments"></a>여러 PXE 시작 배포에 같은 네트워크 어댑터 사용
Technical Preview 버전 1607에서는 이미지 다중 장치(예: 여러 장치에서 사용하는 USB 이더넷 어댑터)에 이더넷 어댑터를 사용하면 이더넷 어댑터에 대한 하드웨어 식별자를 입력할 수 있는 새 설정을 사용할 수 있습니다. Configuration Manager는 PXE 설치 수행 시 목록의 하드웨어 식별자와 클라이언트 등록을 위한 하드웨어 식별자를 무시합니다.

이 문제에 대한 자세한 내용은 [Configuration Manager OSD 지원 팀 블로그](https://blogs.technet.microsoft.com/system_center_configuration_manager_operating_system_deployment_support_blog/2015/08/27/reusing-the-same-nic-for-multiple-pxe-initiated-deployments-in-system-center-configuration-manger-osd/)를 참조하세요.  

### <a name="enable-the-feature-to-manage-duplicate-hardware-identifiers"></a>중복 하드웨어 식별자 관리 기능 사용  
1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **업데이트 및 서비스** > **기능**으로 이동합니다.
2. 디스플레이 창에서 **중복 하드웨어 식별자 관리**를 선택합니다.
3. **홈** 탭의 **기능** 그룹에서 **켜기**를 클릭합니다.

### <a name="add-hardware-identifiers-for-configuration-manager-to-ignore"></a>무시할 Configuration Manager에 대한 하드웨어 식별자 추가  
1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.
2. **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 클릭합니다.
3. **클라이언트 승인 및 충돌 레코드** 탭으로 이동합니다.
4. **중복 하드웨어 식별자** 섹션에서 **추가**를 클릭하여 새 하드웨어 식별자를 추가합니다.
