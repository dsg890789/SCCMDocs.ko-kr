---
title: 접근성
titleSuffix: Configuration Manager
description: 모든 사용자가 Configuration Manager에 액세스할 수 있도록 하는 기능에 대해 알아봅니다.
ms.date: 03/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1cb96666-98bf-49a9-85ca-dbb53f0655e9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 5a1bf32c77989c11c55723d5edf271e234ccd4ec
ms.sourcegitcommit: d8d142044586a53709b4478ad945f714737c8d6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58523744"
---
# <a name="accessibility-features-in-configuration-manager"></a>Configuration Manager의 내게 필요한 옵션 기능

*적용 대상: System Center Configuration Manager(현재 분기)*


Configuration Manager에는 모든 사용자가 액세스할 수 있도록 하는 기능이 포함되어 있습니다.

> [!Note]  
> 버전 1902부터 Configuration Manager 콘솔의 내게 필요한 옵션 기능을 개선하려면 콘솔을 실행하는 컴퓨터에서 .NET을 4.7 버전 이상으로 업데이트하세요. <!-- SCCMDocs-pr issue #3228 -->  
> 
> .NET 4.7.1 및 4.7.2에 수행된 내게 필요한 옵션 변경에 대한 자세한 내용은 [.NET Framework에서 내게 필요한 옵션의 새로운 기능](https://docs.microsoft.com/dotnet/framework/whats-new/whats-new-in-accessibility)을 참조하세요.  



## <a name="keyboard-shortcuts"></a>바로 가기 키

### <a name="console-workspaces"></a>콘솔 작업 영역

작업 영역에 액세스하려면 다음 키보드 바로 가기 키를 사용합니다.  

|키보드 바로 가기 키| 작업 영역|
|--------|--------|  
|Ctrl + 1| 자산 및 호환성|
|Ctrl + 2|  소프트웨어 라이브러리|
|Ctrl + 3|  모니터링|
|Ctrl + 4|  관리|


### <a name="other-keyboard-shortcuts"></a>기타 바로 가기 키

|키보드 바로 가기 키|  용도|
|--------|--------|  
|Ctrl+M|주(가운데) 창에 포커스를 설정합니다.|
|Ctrl+T|탐색 창에서 최상위 노드에 포커스를 설정합니다. 포커스가 이미 해당 창에 있는 경우 포커스는 마지막으로 방문한 노드로 설정됩니다.|
|Ctrl+I|리본 메뉴 바로 아래의 이동 경로 탐색 막대로 포커스를 설정합니다.|
|Ctrl+L|사용 가능한 경우 **검색** 필드로 포커스를 설정합니다.|
|Ctrl+D|사용 가능한 경우 세부 정보 창으로 포커스를 설정합니다.|
|Alt     |포커스를 리본 메뉴 안 및 밖으로 변경합니다.|



## <a name="other-accessibility-features"></a>기타 내게 필요한 옵션 기능

- 탐색 창으로 이동하려면 노드 이름의 문자를 입력하세요.

- 주 보기 및 리본 간의 키보드 탐색이 순환됩니다.

- 세부 정보 창의 키보드 탐색이 순환됩니다. 이전 개체 또는 창으로 돌아가려면 Ctrl+D를 누른 다음 Shift+탭을 누릅니다.

- 작업 영역 보기를 새로 고치면 포커스가 작업 영역의 주 창으로 설정됩니다.

- 작업 영역 메뉴에 액세스하려면 키를 선택하여 확장/축소 아이콘으로 이동합니다. 그런 다음 아래쪽 화살표 키를 선택하여 작업 영역 메뉴에 액세스합니다.  

- 작업 영역 메뉴를 탐색하려면 화살표 키를 사용합니다.  

- 작업 영역의 각 영역에 액세스하려면  키와  키를 사용합니다. 리본과 같은 작업 영역의 영역 안에서 이동하려면 화살표 키를 사용합니다.  

- 포커스가 트리 노드에 있을 때 주소 표시줄에 액세스하려면 Shift+Tab 키를 세 번 사용합니다.  

- 마법사 또는 속성 페이지에서 키보드 바로 가기 키를 사용하여 상자 간에 이동할 수 있습니다. 특정 상자를 선택하려면 Alt 키와 밑줄 친 문자(Alt+_)를 누릅니다.     

- 작업 영역의 다른 노드로 이동하려면 노드 이름의 첫 글자를 입력합니다. 키를 누를 때마다 해당 문자로 시작하는 다음 노드로 커서가 이동합니다. 화면 읽기 프로그램을 사용하는 경우 읽기 프로그램이 해당 노드의 이름을 읽어냅니다.



## <a name="see-also"></a>참고 항목

Configuration Manager 사용자 인터페이스 탐색의 기본 사항에 대한 자세한 내용은 다음 문서를 참조하세요.
- [Configuration Manager 콘솔 사용](/sccm/core/servers/manage/admin-console)  
- [소프트웨어 센터 사용자 가이드](/sccm/core/understand/software-center)

> [!NOTE]  
> 이 문서의 정보는 미국에 거주하는 Microsoft 제품 라이선스를 보유한 사용자에게만 적용될 수 있습니다. 미국 이외의 지역에서 이 제품을 구입한 경우 Microsoft 지원 서비스 연락처 정보를 보려면 소프트웨어 패키지와 함께 제공되는 자회사 정보 카드를 확인하거나 [Microsoft 내게 필요한 옵션 웹 사이트](https://go.microsoft.com/fwlink/?LinkId=8431)를 방문하세요. 현지 자회사에 문의하여 이 섹션에 설명된 제품 유형 및 서비스를 해당 지역에서 이용할 수 있는지 알아볼 수 있습니다. 내게 필요한 옵션에 대한 정보는 일본어 및 프랑스어를 비롯한 여러 언어로 제공됩니다.  

