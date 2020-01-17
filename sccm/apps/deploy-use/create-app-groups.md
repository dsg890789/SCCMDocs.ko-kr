---
title: 애플리케이션 그룹 만들기
titleSuffix: Configuration Manager
description: Configuration Manager에서 사용자 또는 디바이스 컬렉션을 단일 배포로 보낼 수 있는 애플리케이션 그룹을 만듭니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: e67c691e-62ef-4f43-9cfb-0e957d1e7a5f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b3538a679886e41d047146b36ef79a48440ee215
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75815989"
---
# <a name="create-application-groups"></a>애플리케이션 그룹 만들기

*적용 대상: Configuration Manager(현재 분기)*

<!--3555907-->

1906 버전부터는 사용자 또는 디바이스 컬렉션을 단일 배포로 보낼 수 있는 애플리케이션 그룹을 만듭니다. 앱 그룹에 대해 지정한 메타데이터는 소프트웨서 센터에 단일 항목으로 표시됩니다. 클라이언트가 특정 순서대로 앱을 설치하도록 그룹에서 순서를 지정할 수 있습니다.

> [!Note]  
> 이 버전의 Configuration Manager에서 앱 그룹은 시험판 기능입니다. 이 기능을 사용하려면 [시험판 기능](/configmgr/core/servers/manage/pre-release-features)을 참조하세요.  

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동합니다. **애플리케이션 관리**를 펼치고 **애플리케이션 그룹** 노드를 선택합니다.  

1. 리본 메뉴의 만들기 그룹에서 **응용 프로그램 그룹 만들기**를 선택 합니다.

1. **일반 정보** 페이지에서 앱 그룹의 정보를 지정합니다.  

1. **소프트웨어 센터** 페이지에서 소프트웨어 센터에 표시되는 정보를 포함합니다.  

1. **애플리케이션 그룹** 페이지에서 **추가**를 선택합니다. 이 그룹에 대해 하나 이상의 앱을 선택합니다. **위로 이동** 및 **아래로 이동** 작업을 사용하여 다시 정렬합니다.  

1. 마법사를 완료합니다.  

애플리케이션에서와 같은 프로세스를 사용하여 앱 그룹을 배포합니다. 자세한 내용은 [애플리케이션 배포](/configmgr/apps/deploy-use/deploy-applications)를 참조하세요. 버전 1910부터 장치 또는 사용자 컬렉션에 앱 그룹을 배포할 수 있습니다.

그룹을 배포한 후:

- 그룹에 새 앱을 추가 하는 경우 배포 지점의 새 앱 콘텐츠를 별도로 배포 해야 합니다.

- 앱 그룹에서 응용 프로그램을 수정 하는 경우 콘텐츠를 다시 배포 합니다.

앱 그룹 배포 문제를 해결 하려면 클라이언트에서 다음 로그 파일을 사용 합니다.

- **AppGroupHandler.log**
- **AppEnforce.log**
- **SettingsAgent.log**

> [!Important]  
> 전체 계층 및 대상 클라이언트를 버전 1906 이상으로 업데이트할 때까지 앱 그룹을 만들거나 배포 하지 마십시오.

### <a name="known-issues"></a>알려진 문제

- 그룹의 앱은 **Windows Installer** 또는 **스크립트** 배포 유형만 포함할 수 있습니다.
  - *버전 1906*: 배포 유형 설치 동작을 **시스템에 대해 설치**로 설정 합니다.
- 다음 배포 옵션은 작동 하지 않을 수 있습니다. 경고, 승인, 단계적 배포, 복구.
- 앱 그룹을 내보내거나 가져올 수 없습니다.
- 다시 시작 해야 하는 앱은 그룹에 포함 하지 마세요. 그렇지 않으면 그룹 배포가 실패할 수 있습니다.
- *버전 1906*: 사용자 컬렉션에 앱 그룹을 배포할 수 없습니다.
- *버전 1906*: 사용자는 소프트웨어 센터에서 앱 그룹을 **제거**할 수 없습니다.
