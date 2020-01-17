---
title: 기술 미리 보기 1608의 기능
titleSuffix: Configuration Manager
description: Configuration Manager용 Technical Preview 버전 1608에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 63e1df5e-637c-4b07-b7ec-95340f43a805
author: aczechowski
manager: dougeby
ms.author: aaroncz
ROBOTS: NOINDEX
ms.openlocfilehash: 8ea43f36351ac461396b84c248ca8084b3da9774
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75805118"
---
# <a name="capabilities-in-technical-preview-1608-for-configuration-manager"></a>Configuration Manager용 Technical Preview 1608의 기능

*적용 대상: Configuration Manager(기술 미리 보기 분기)*

이 문서에서는 Configuration Manager용 Technical Preview 버전 1608에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대한 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  




##  <a name="improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step"></a>ConfigMgr 클라이언트 캡처 준비 작업 순서 단계의 향상 기능  
이제 ConfigMgr 클라이언트 준비 단계에서 주요 정보만 제거하는 것이 아니라 Configuration Manager 클라이언트를 완전히 제거합니다. 작업 순서에서 운영 체제 캡처 이미지를 배포할 때마다 새 Configuration Manager 클라이언트가 설치됩니다.  


## <a name="improvements-to-software-center"></a>소프트웨어 센터 개선
* 소프트웨어 센터 **애플리케이션**, **업데이트** 및 **운영 체제** 탭에는 이제 최근에 추가된 소프트웨어가 표시됩니다. 탐색 창의 숫자에는 각 탭에 있는 새 소프트웨어 수가 표시됩니다.
* 이제 사용자가 애플리케이션에 대한 승인을 요청하고 소프트웨어 센터의 **애플리케이션 정보** 보기에서 요청 기록을 볼 수 있습니다. **애플리케이션 정보**에서 **요청** 단추를 누르면 더 이상 웹 기반 애플리케이션 카탈로그로 리디렉션되지 않습니다.

## <a name="improvements-to-asset-intelligence"></a>Asset Intelligence 개선
다른 소프트웨어와 부모 및 자식 관계를 설정할 수 있도록 인벤토리 소프트웨어의 속성에 필드를 추가했습니다. 인벤토리 소프트웨어 목록에서 소프트웨어의 부모를 볼 수 있으며 모든 자식 소프트웨어를 숨길 수도 있습니다.

### <a name="configure-a-parent-to-child-relationship"></a>부모 자식 관계 구성
  1. 부모 소프트웨어를 설정하려면 인벤토리 소프트웨어 노드에서 **인벤토리 소프트웨어** 목록의 소프트웨어 항목을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.
  2. 대화 상자가 열리면 처음 선택에서 부모 소프트웨어로 설정할 소프트웨어를 선택합니다.

### <a name="filter-the-software-display"></a>소프트웨어 표시 필터링
부모 자식 관계를 정의한 후에 부모인 소프트웨어만 표시하도록 보기를 필터링하거나 정의된 관계가 없는 소프트웨어만 표시하도록 필터링할 수 있습니다. 이렇게 하면 또 다른 인벤토리 소프트웨어의 자식으로 설정된 모든 소프트웨어가 숨겨집니다. 확인 방법은 다음과 같습니다.
   1. 검색 창에서 **조건 추가**를 선택합니다.
   2. **부모 소프트웨어**를 선택한 다음 조건 값을 **비어 있음**으로 변경한 후 **검색**을 클릭합니다.

이제 부모 소프트웨어 항목 또는 정의된 관계가 없는 소프트웨어만 표시됩니다. 다른 제목의 자식에만 해당하는 소프트웨어는 표시되지 않습니다.

## <a name="remote-control-keyboard-translation"></a>원격 제어 키보드 변환
과거의 Configuration Manager에서는 뷰어의 위치에서 공유자의 위치로 키 위치를 전송했습니다. 이로 인해 뷰어와 공유자 간의 차이가 있는 키보드 구성에 대한 문제가 있었습니다. 예를 들어 영어 키보드를 사용하는 뷰어는 "A"를 입력하지만 공유자의 프랑스어 키보드는 "Q"를 제공합니다. 뷰어의 키보드에서 공유자의 키보드로 문자 자체가 변환되어 뷰어가 입력하려고 했던 문자가 공유자에게 표시될 수 있도록 기본 동작을 변경합니다.

공유자의 키보드 배열에 따라 입력하기를 원하는 경우 뷰어가 이 동작을 해제할 수 있습니다. 동작을 변경하려면 **Configuration Manager 원격 제어**에서 **작업**, **키보드 변환 사용**을 선택하여 키 위치를 전송합니다.

> [!NOTE]
>
> ~!#@$% 등의 특수 키는 올바르게 변환되지 않습니다.
