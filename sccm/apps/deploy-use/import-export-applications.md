---
title: 애플리케이션 가져오기 및 내보내기
titleSuffix: Configuration Manager
description: 별도의 계층 간에 공유하기 위해 Configuration Manager에서 애플리케이션을 가져오고 내보내는 방법에 대해 알아봅니다.
ms.date: 05/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: dba00e54-9d5b-4f6b-916d-ead48c66e288
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 02bb394de4f3bb947bdc2669a830167089c42311
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "66411012"
---
# <a name="import-and-export-applications"></a>애플리케이션 가져오기 및 내보내기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager를 사용하여 두 계층 간에 애플리케이션을 가져오고 내보냅니다. 예를 들어 애플리케이션을 테스트 환경에서 프로덕션 환경으로 복사합니다.

## <a name="export"></a>내보내기

1. Configuration Manager 콘솔에서 **애플리케이션** 노드를 선택합니다. 리본의 Create 그룹에서 **애플리케이션 내보내기**를 선택합니다.
1. **일반** 화면에서 내보낼 새 ZIP 파일의 경로를 입력합니다. 선택적으로 *종속성, 교체 관계, 조건 및 가상 환경*과 *선택한 애플리케이션 및 종속성에 대한 콘텐츠*를 내보낼지 여부를 지정합니다.  원하는 경우 관리자 설명을 입력하고 **다음**을 선택합니다.
1. 애플리케이션 및 모든 종속성이 **관련 개체** 페이지에 나열되어 있는지 확인하고 **다음**을 선택합니다.
1. 요약 페이지에서 **다음**을 선택합니다.
1. 프로세스가 완료되면 ZIP 파일이 생성되고 마법사를 닫을 수 있습니다.

> [!IMPORTANT]
> 이 애플리케이션을 다른 환경에 복사하려면 ZIP 파일과 함께 제공되는 폴더를 가져옵니다. ZIP 파일은 만든 폴더와 동일한 디렉터리에 있어야 합니다.

## <a name="import"></a>가져오기

> [!NOTE]
> UNC 경로에서만 애플리케이션을 가져올 수 있으며 로컬 디스크에서 직접 가져올 수 없습니다.

1. Configuration Manager 콘솔에서 **애플리케이션** 노드를 선택합니다. 리본의 Create 그룹에서 **애플리케이션 가져오기**를 선택합니다.
1. 가져올 ZIP 파일을 선택하고 **다음**을 선택합니다.
1. 파일 콘텐츠 창에는 애플리케이션을 가져올 때 발생하는 일을 보여줍니다. **다음**을 선택합니다.
1. 요약 화면을 검토하고 **다음**을 선택합니다.
1. 마법사를 닫습니다. 이제 애플리케이션을 사이트에서 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목
 
PowerShell을 사용하여 애플리케이션 가져오기 및 내보내기를 자동화합니다.

* [Import-CMApplication](https://docs.microsoft.com/powershell/module/configurationmanager/import-cmapplication)
* [Export-CMApplication](https://docs.microsoft.com/powershell/module/configurationmanager/export-cmapplication)
