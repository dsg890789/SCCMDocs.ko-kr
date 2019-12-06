---
title: 네트워크 공유에서 정의 다운로드
titleSuffix: Configuration Manager
description: Microsoft에서 최신 정의 업데이트를 수동으로 다운로드한 다음 이러한 정의를 다운로드하도록 클라이언트를 구성하는 방법을 알아봅니다.
ms.date: 11/18/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: ddef4d2a-f481-4020-9ddd-9cca5f9795cb
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: da691b4b9f9fdb34bd0bbba0a9090be9e78aae39
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74161672"
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-a-network-share"></a>네트워크 공유에서 다운로드하기 위해 Endpoint Protection 맬웨어 정의를 사용하도록 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

 Microsoft에서 최신 정의 업데이트를 수동으로 다운로드한 다음 네트워크의 공유 폴더에서 이러한 정의를 다운로드하도록 클라이언트를 구성할 수 있습니다. 이 업데이트 원본을 사용하는 경우 사용자가 정의 업데이트를 시작할 수도 있습니다.

> [!NOTE]
>  정의 업데이트를 다운로드하려면 클라이언트에 공유 폴더에 대한 읽기 권한이 있어야 합니다.

 파일 공유의 저장소에 정의 및 엔진 업데이트를 다운로드하는 방법에 대한 자세한 내용은 [Install the latest Microsoft antimalware and antispyware software](https://www.microsoft.com/wdsi/definitions)(최신 Microsoft 맬웨어 방지 및 스파이웨어 방지 소프트웨어 설치)를 참조하세요.

## <a name="to-configure-definition-downloads-from-a-file-share"></a>파일 공유에서 정의 다운로드를 구성하려면

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.

2.  **자산 및 호환성** 작업 영역에서 **Endpoint Protection**을 확장하고 **맬웨어 방지 정책**을 클릭합니다.

3.  **기본 맬웨어 방지 정책** 의 속성 페이지를 열거나 새 맬웨어 방지 정책을 만듭니다. 맬웨어 방지 정책을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)을 참조하세요.

4.  맬웨어 방지 속성 대화 상자의 **보안 인텔리전스 업데이트** 섹션에서 **원본 설정**을 클릭 합니다.
    - **정의 업데이트** 섹션의 이름이 Configuration Manager 버전 1902부터 **Security Intelligence 업데이트** 로 바뀌었습니다.

5.  **정의 업데이트 원본 구성** 대화 상자에서 **UNC 파일 공유에서 업데이트**를 선택합니다.

6.  **확인** 을 클릭하여 **정의 업데이트 원본 구성** 대화 상자를 닫습니다.

7.  **경로 설정**을 클릭합니다. 그런 다음 **정의 업데이트 UNC 경로 구성** 대화 상자에서 네트워크 공유에 있는 정의 업데이트 파일 위치의 UNC 경로를 하나 이상 추가합니다.

8.  **확인** 을 클릭하여 **정의 업데이트 UNC 경로 구성** 대화 상자를 닫습니다.


> [!div class="button"]
> [다음 단계 >](endpoint-antimalware-policies.md)
> 
> [!div class="button"]
> [뒤로 >](endpoint-configure-alerts.md)
