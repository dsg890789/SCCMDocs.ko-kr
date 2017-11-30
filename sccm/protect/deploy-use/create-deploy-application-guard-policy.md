---
title: "Windows Defender Application Guard 정책 만들기 및 배포"
titleSuffix: Configuration Manager
description: "Windows Defender Application Guard 정책을 만들고 배포합니다."
ms.custom: na
ms.date: 11/21/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 
caps.latest.revision: "5"
author: ErikjeMS
ms.author: erikje
manager: angrobe
ms.openlocfilehash: db2508e5bbd1435fce432b6ef98d7968e68ea5ab
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/21/2017
---
# <a name="create-and-deploy-windows-defender-application-guard-policy----1351960---"></a>Windows Defender Application Guard 정책 만들기 및 배포 <!-- 1351960 -->

Configuration Manager 엔드포인트 보호를 사용하여 [Windows Defender Application Guard](https://docs.microsoft.com/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview) 정책을 만들고 배포할 수 있습니다. 이러한 정책은 운영 체제의 다른 부분에서 액세스할 수 없는 안전하게 격리된 컨테이너에서 신뢰할 수 없는 웹 사이트를 열어 사용자를 보호하는 데 도움이 됩니다.

## <a name="prerequisites"></a>전제 조건

Windows Defender Application Guard 정책을 만들고 배포하려면 Windows 10 Fall Creators Update를 사용해야 합니다. 또한 정책을 배포하는 Windows 10 장치는 네트워크 격리 정책을 사용하여 구성해야 합니다. 자세한 내용은 [Windows Defender Application Guard 개요](https://docs.microsoft.com/en-us/windows/threat-protection/windows-defender-application-guard/wd-app-guard-overview)를 참조하세요. 이 기능은 현재 Windows 10 참가자 빌드에서만 작동합니다. 이 기능을 테스트하려면 클라이언트에서 최신 Windows 10 참가자 빌드를 실행하고 있어야 합니다.


## <a name="create-a-policy-and-to-browse-the-available-settings"></a>정책 만들기 및 사용 가능한 설정 검색

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.
2. **자산 및 준수** 작업 영역에서 **개요** > **Endpoint Protection** > **Windows Defender Application Guard**를 선택합니다.
3. **홈** 탭의 **만들기** 그룹에서  **만들기**를 클릭합니다.
4. [블로그 게시물](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97)을 참조하여 사용 가능한 설정을 찾아보고 구성할 수 있습니다.
5. **네트워크 정의** 페이지에서 회사 ID를 지정하고 회사 네트워크 경계를 정의합니다.

    > [!NOTE]
    > Windows 10 PC는 클라이언트에 하나의 네트워크 격리 목록만 저장합니다. 서로 다른 두 가지 종류의 네트워크 격리 목록을 만들어 다음 클라이언트에 배포할 수 있습니다.
    >
    >  - Windows Information Protection 중 하나
    >  - Windows Defender Application Guard 중 하나
    >
    > 두 정책 모두 배포하는 경우 두 네트워크 격리 목록이 일치해야 합니다. 동일 클라이언트와 일치하지 않는 목록을 배포할 경우 배포가 실패합니다. 자세한 내용은 [Windows Information Protection 설명서](https://docs.microsoft.com/windows/threat-protection/windows-information-protection/create-wip-policy-using-sccm)를 참조하세요.
    > 
    > 

6. 작업이 끝나면 마법사를 완료하고 하나 이상의 Windows 10 장치에 정책을 배포합니다.

## <a name="next-steps"></a>다음 단계
Windows Defender Application Guard에 대한 자세한 내용은 [이 블로그 게시물](https://blogs.windows.com/msedgedev/2016/09/27/application-guard-microsoft-edge/#BmJGKPfSjHHzsMmI.97)을 참조하세요. 또한 Windows Defender Application Guard 독립 실행형 모드에 대한 자세한 내용은 [이 블로그 게시물](https://techcommunity.microsoft.com/t5/Windows-Insider-Program/Windows-Defender-Application-Guard-Standalone-mode/td-p/66903)을 참조하세요.
