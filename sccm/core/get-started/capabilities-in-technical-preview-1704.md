---
title: 기술 미리 보기 1704의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1704에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 04/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e318e705-20f2-417d-8cde-7dfe661b2fa7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: d9a7c8b9aab94e9b56d2d421be94a523116f35c9
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70889676"
---
# <a name="capabilities-in-technical-preview-1704-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1704의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1704에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="configure-android-apps-with-app-configuration-policies"></a>앱 구성 정책을 사용하여 Android 앱 구성
System Center Configuration Manager(Configuration Manager)에서 앱 구성 정책을 사용하여 사용자가 Android for Work 디바이스에서 앱을 실행할 때 필요할 수도 있는 설정을 배포할 수 있습니다. Android 앱 구성 정책은 Android for Work를 실행 중인 디바이스에서만 사용 가능하며 Play for Work 스토어에서 승인한 앱에 적용됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기                 

Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **애플리케이션 관리** > **앱 구성 정책**을 선택하고 **앱 구성 정책 만들기**를 선택합니다. 이제 마법사의 **일반** 페이지에서 **구성 정책 형식을 선택**할 수 있습니다. 앱 구성 정책에서 대상이 지정된 플랫폼을 지정합니다. **Android for Work 앱에 대한 구성 정책**. **이름 및 값 쌍을 지정**하거나 **속성 목록 JSON 파일을 찾을** 수 있습니다. 새 앱 구성 정책이 **소프트웨어 라이브러리** 작업 영역의 **앱 구성 정책** 노드에 표시됩니다. 앱 구성 정책을 Android for Work 앱 배포와 연결하려면 [애플리케이션 배포](/sccm/apps/deploy-use/deploy-applications) 항목의 프로시저를 사용하여 일반적인 방식으로 애플리케이션을 배포합니다.

## <a name="hardware-inventory-collects-secure-boot-information"></a>하드웨어 인벤토리를 통해 보안 부팅 정보 수집
이제 하드웨어 인벤토리는 클라이언트에서 보안 부팅을 사용할 수 있는지에 대한 정보를 수집합니다. 이 정보는 버전 1702에 도입된 **SMS_Firmware** 클래스에 저장되며 하드웨어 인벤토리에서 기본적으로 사용하도록 설정됩니다. 하드웨어 인벤토리에 대한 자세한 내용은 [하드웨어 인벤토리 구성 방법](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.

## <a name="add-child-task-sequences-to-a-task-sequence"></a>작업 순서에 자식 작업 순서 추가
이 버전에서는 다른 작업 순서를 실행하는 새 작업 순서 단계를 추가할 수 있습니다. 이렇게 하면 작업 순서 간에 부모/자식 관계가 생성됩니다. 이러한 관계를 생성하면 다시 사용 가능한 모듈식 작업 순서를 더 만들 수 있습니다.  

작업 순서에 자식 작업 순서를 추가할 때는 다음 사항을 고려하세요.

- 부모 및 자식 작업 순서는 실제로는 클라이언트가 실행하는 단일 정책으로 결합됩니다.
- 다른 작업 순서의 부모인 자식 작업 순서를 추가할 수는 없습니다.
- 전역 환경이 사용됩니다. 예를 들어 변수가 부모 작업 순서에 의해 설정된 후 자식 작업 순서에 의해 변경된 경우, 변수는 계속 변경된 상태로 유지됩니다. 마찬가지로 자식 작업 순서에서 새로 만든 변수는 부모 작업 순서의 나머지 단계에서 사용할 수 있습니다.
- 상태 메시지는 단일 작업 순서 작업에 대해 일반적인 방식을 사용할 때마다 전송됩니다.
- 작업 순서는 smsts.log 파일에 항목을 쓰며 자식 작업 순서가 시작될 때 새 로그 항목이 추가되므로 해당 작업 순서를 쉽게 확인할 수 있습니다.
- Configuration Manager용 Technical Preview 버전 1704에서 자식 작업 순서가 패키지를 참조하고 소프트웨어 센터에서 부모 작업 순서를 실행하면 자식 작업 순서가 실행될 때 클라이언트가 패키지 콘텐츠를 찾지 않습니다. 이 시나리오에서는 부팅 미디어, PXE 등의 미디어에서 작업 순서를 실행해야 합니다.  

    자식 작업 순서가 **명령줄 실행**(패키지 미참조), **형식**, **BitLocker** 등의 단계를 사용하는 경우에는 소프트웨어 센터에서 작업 순서가 정상적으로 실행됩니다.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>작업 순서에 자식 작업 순서를 추가하려면
1. 작업 순서 편집기에서 **추가**를 클릭하고 **일반**을 선택한 다음 **작업 순서 실행**을 클릭합니다.
2. **찾아보기**를 클릭하여 자식 작업 순서를 선택합니다.  

## <a name="reload-boot-images-with-current-windows-pe-version"></a>현재 Windows PE 버전을 사용하여 부팅 이미지 다시 로드
이제는 선택한 부팅 이미지에서 **배포 지점 업데이트**를 실행할 때 부팅 이미지의 Windows ADK 설치 디렉터리에서 최신 Windows PE 버전을 다시 로드하도록 선택할 수 있습니다. 마법사의 **일반** 페이지에서는 사이트 서버에 설치된 Windows ADK 버전, 부팅 이미지에서 Windows PE가 사용된 Windows ADK 버전 및 Configuration Manager 클라이언트 버전에 대한 정보를 제공합니다. 이 정보를 통해 부팅 이미지를 다시 로드할지를 결정할 수 있습니다. 또한 **부팅 이미지** 노드에서 부팅 이미지를 볼 때 새로운 열(**클라이언트 버전**)이 추가되므로 각 부팅 이미지에서 사용하는 Configuration Manager의 버전을 확인할 수 있습니다.

### <a name="to-reload-a-boot-image-with-the-current-windows-pe-version"></a>현재 Windows PE 버전으로 부팅 이미지를 다시 로드하려면

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **운영 체제** > **부팅 이미지**로 이동합니다.
2. 부팅 이미지를 선택하고 **배포 지점 업데이트**를 클릭합니다.
3. 마법사의 **일반** 페이지에서 **설치한 Windows ADK에서 현재 버전의 Windows PE를 사용하여 부팅 이미지 다시 로드**를 선택합니다.

## <a name="improvements-to-operating-system-deployment"></a>운영 체제 배포 향상
사용자 의견 피드백을 반영하여 운영 체제 배포가 다음과 같이 향상되었습니다.

- [운영 체제 이미지용 새 **OS 버전** 열](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17558407-add-a-column-to-the-operating-system-images-node-f): **운영 체제 이미지** 및 **운영 체제 업그레이드 패키지** 노드의 정보를 확인할 때 **OS 버전** 열을 새로 추가하여 이미지용 운영 체제 버전을 표시했습니다. .WIM의 첫 번째 인덱스 버전만 표시됩니다. 이미지의 **세부 정보** 탭으로 이동하면 다른 인덱스의 운영 체제 버전을 검토할 수 있습니다.

- [보다 효율적인 방식으로 Smsts.log에 로깅](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16791919-stop-filling-smsts-log-with-useless): 이 버전부터는 CCM_CIVersionInfo.PolicyID 정보에 대한 항목이 smsts.log 파일에 더 이상 기록되지 않습니다. 이전 버전에서는 해당 정보를 포함하는 항목이 매우 많은 경우가 있어서 로그 파일에서 관련성이 높은 정보를 찾기가 어려웠습니다.
