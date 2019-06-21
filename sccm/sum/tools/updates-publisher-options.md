---
title: 옵션 구성
titleSuffix: Configuration Manager
description: System Center Updates Publisher 사용 옵션 구성
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 4e620080-5400-45bb-87c2-fbdbc8aeacac
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d576057c1ca7940a8d09bcfa305b80b178a6006
ms.sourcegitcommit: 659976b943226c5124057429ac7444989f98433f
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67159519"
---
# <a name="configure-options-for-updates-publisher"></a>Updates Publisher의 옵션 구성

*적용 대상: System Center Updates Publisher*

Updates Publisher의 작동에 영향을 주는 옵션 및 관련 설정을 검토하고 구성합니다.

Updates Publisher 옵션에 액세스하려면 콘솔의 왼쪽 상단 모서리에 있는 **Updates Publisher** **속성** 탭을 선택한 다음 **옵션**을 선택합니다.

![Options](media/properties1.png)   


옵션은 다음으로 구분됩니다.

-   업데이트 서버
-   ConfigMgr 서버
-   프록시 설정
-   신뢰할 수 있는 게시자
-   고급
-   업데이트
-   로깅

## <a name="update-server"></a>업데이트 서버
WSUS(Windows Server Update Services)와 같은 업데이트 서버에서 작동하도록 Updates Publisher를 구성해야 [업데이트 게시](/sccm/sum/tools/manage-updates-with-updates-publisher#publish-updates-and-bundles-from-the-updates-workspace)가 가능합니다. 이러한 구성에는 서버를 지정하고 콘솔의 원격 서버인 해당 서버에 연결하는 방법을 지정하고 게시하는 디지털 서명 업데이트에 사용할 인증서를 지정하는 작업이 포함됩니다.

- **업데이트 서버를 구성**합니다. 업데이트 서버를 구성할 때 모든 자식 사이트가 게시하는 업데이트에 대한 액세스 권한을 갖도록 Configuration Manager 계층 구조에서 최상위 WSUS 서버(업데이트 서버)를 선택합니다.

  업데이트 서버가 Updates Publisher 서버의 원격 서버이고 SSL로 연결된 경우 서버의 FQDN(정규화된 도메인 이름)을 지정합니다. SSL로 연결할 경우 기본 포트가 8530에서 8531로 변경됩니다. 설정한 포트가 업데이트 서버에서 사용 중인 포트와 일치하는지 확인합니다.

  > [!TIP]  
  > 업데이트 서버를 구성하지 않은 경우 Updates Publisher를 계속 사용하여 소프트웨어 업데이트를 작성할 수 있습니다.

- **서명 인증서를 구성**합니다. 먼저 업데이트 서버를 구성하여 성공적으로 연결해야 서명 인증서를 구성할 수 있습니다.

  Updates Publisher는 서명 인증서를 사용하여 업데이트 서버에 게시된 소프트웨어 업데이트에 서명합니다. Updates Publisher를 실행하는 업데이트 서버 또는 컴퓨터의 인증서 저장소에서 디지털 인증서를 사용할 수 없는 경우 게시가 실패합니다.

  인증서 저장소에 인증서를 추가하는 방법에 대한 자세한 내용은 [Updates Publisher의 인증서 및 보안](/sccm/sum/tools/updates-publisher-security)을 참조하세요.

  업데이트 서버에 대한 디지털 인증서가 자동으로 검색되지 않으면 다음 중 하나를 선택합니다.

  -   **찾아보기**: 찾아보기는 콘솔을 실행하는 서버에 업데이트 서버가 설치된 경우에만 사용할 수 있습니다. 인증서를 선택한 후 **만들기**를 선택하여 해당 인증서를 업데이트 서버의 WSUS 인증서 저장소에 추가해야 합니다. 이러한 방법으로 선택한 인증서의 **.pfx** 파일 암호를 입력해야 합니다.

  -   **만들기:** 이 옵션을 사용하여 새 인증서를 만듭니다. 또한 이 옵션으로 업데이트 서버의 WSUS 인증서 저장소에 인증서를 추가합니다.

  **자체 서명 인증서를 만드는 경우** 다음을 구성합니다.

  -   **프라이빗 키를 내보낼 수 있음** 옵션을 사용하도록 설정합니다.

  -   **키 사용**을 디지털 서명으로 설정합니다.

  -   **최소 키 크기**를 2048비트보다 크거나 같은 값으로 설정합니다.

  **제거** 옵션을 사용하여 WSUS 인증서 저장소에서 인증서를 제거합니다. 이 옵션은 업데이트 서버가 사용하는 Updates Publisher 콘솔의 로컬 서버이거나 **SSL**을 사용하여 원격 업데이트 서버에 연결한 경우에 사용할 수 있습니다.

## <a name="configmgr-server"></a>ConfigMgr 서버
Updates Publisher에서 Configuration Manager를 사용할 경우 이러한 옵션을 사용합니다.

-   **Configuration Manager 서버 지정:** Configuration Manager에 대한 지원을 사용하도록 설정한 후 Configuration Manager 계층 구조에서 최상위 계층 사이트 서버의 위치를 지정합니다. 해당 서버가 Updates Publisher 설치의 원격 서버인 경우 사이트 서버의 FQDN을 지정합니다. **연결 테스트**를 선택하여 사이트 서버에 연결할 수 있는지 확인합니다.

-   **임계값 구성:** 임계값은 자동 게시물 유형으로 업데이트를 게시할 때 사용됩니다. 임계값은 메타데이터만이 아닌, 업데이트에 대한 전체 콘텐츠가 게시되는 시기를 결정하는 데 도움이 됩니다. 게시물 유형에 대한 자세한 내용은 [게시물에 업데이트 할당](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)을 참조하세요.

    다음 임계값 중 하나 또는 둘 다 사용할 수 있습니다.

    -   **요청된 클라이언트 수 임계값:** Updates Publisher에서 해당 업데이트의 전체 콘텐츠 집합을 자동으로 게시하기 전에 업데이트를 요청해야 할 클라이언트 수를 정의합니다. 지정된 수의 클라이언트가 업데이트를 요청할 때까지 업데이트 메타데이터만 게시됩니다.

    -   **패키지 원본 크기 임계값(MB):** 지정한 크기를 초과하는 업데이트가 자동 게시되지 않도록 합니다. 업데이트 크기가 이 값을 초과하는 경우 메타데이터만 게시됩니다. 지정된 크기보다 작은 업데이트의 경우 전체 콘텐츠를 게시할 수 있습니다.

## <a name="proxy-settings"></a>프록시 설정
Updates Publisher는 인터넷에서 소프트웨어 카탈로그를 가져오거나 인터넷에 업데이트를 게시할 때 프록시 설정을 사용합니다.

-   프록시 서버의 FQDN 또는 IP 주소를 지정합니다. IPv4 및 IPv6이 지원됩니다.

-   프록시 서버에서 인터넷 액세스에 대해 사용자를 인증하는 경우 Windows 이름을 지정해야 합니다. UPN(범용 계정 이름)은 지원되지 않습니다.

## <a name="trusted-publishers"></a>신뢰할 수 있는 게시자
업데이트 카탈로그를 가져올 때 해당 인증서 기반의 해당 카탈로그 원본은 신뢰할 수 있는 게시자로 추가됩니다. 마찬가지로 업데이트를 게시할 때 업데이트 인증서 원본은 신뢰할 수 있는 게시자로 추가됩니다.

각 게시자에 대한 인증서 세부 정보를 보고 신뢰할 수 있는 게시자 목록에서 게시자를 제거할 수 있습니다.

신뢰할 수 없는 게시자의 콘텐츠는 클라이언트가 업데이트를 검색할 때 클라이언트 컴퓨터를 잠재적으로 손상시킬 수 있습니다. 신뢰할 수 있는 게시자의 콘텐츠만 수락해야 합니다.

## <a name="advanced"></a>고급
고급 옵션에는 다음이 포함됩니다.

-   **리포지토리 위치:** **scupdb.sdf** 데이터베이스 파일의 위치를 보고 수정합니다. 이 파일은 Updates Publisher의 리포지토리입니다.

-   **타임스탬프:** 사용하도록 설정하면 서명하는 업데이트에 타임스탬프가 추가되어 서명 시기를 식별할 수 있습니다. 인증서가 유효한 동안 서명된 업데이트는 서명 인증서가 만료된 이후에도 사용할 수 있습니다. 기본적으로 소프트웨어 업데이트는 서명 인증서가 만료된 후에는 배포할 수 없습니다.

-   **구독 카탈로그에 대한 업데이트 확인:** Updates Publisher가 시작될 때마다 구독하는 카탈로그에 대한 업데이트를 자동으로 확인할 수 있습니다. 카탈로그 업데이트를 찾으면 세부 정보가 **업데이트 작업 영역**의 **개요** 창에 **최근 경고**로 제공됩니다.

-   **인증서 해지:** 인증서 해지 확인을 사용하도록 설정하려면 이 옵션을 선택합니다.

-   **로컬 원본 게시:** Updates Publisher는 인터넷에서 해당 업데이트를 다운로드하기 전에 게시 중인 업데이트의 로컬 복사본을 사용할 수 있습니다. 위치는 Updates Publisher를 실행하는 컴퓨터에 있는 폴더여야 합니다. 기본적으로 이 위치는 **My Documents\LocalSourcePublishing**입니다. 이전에 하나 이상의 업데이트를 다운로드했거나 배포하려는 업데이트를 수정한 경우 이 옵션을 사용합니다.

-   **Software Updates Cleanup Wizard**(소프트웨어 업데이트 정리 마법사): 업데이트 정리 마법사를 시작합니다. 마법사는 업데이트 서버에 있지만 Updates Publisher 리포지토리에 없는 업데이트를 만료시킵니다. 자세한 내용은 [참조되지 않은 업데이트 만료](#expire-unreferenced-software-updates)를 참조하세요.

## <a name="updates"></a>업데이트
 Updates Publisher가 열릴 때마다 자동으로 새 업데이트를 확인할 수 있습니다. Updates Publisher의 미리 보기 빌드 수신을 선택할 수도 있습니다.

수동으로 업데이트를 확인하려면 Updates Publisher 콘솔에서 ![속성](media/properties2.png)을 클릭하여  
**Updates Publisher 속성**을 연 다음 **업데이트 확인**을 선택합니다.

Updates Publisher가 새 업데이트를 찾은 후 **업데이트 사용 가능** 창이 표시되면 업데이트를 설치하도록 선택할 수 있습니다. 업데이트를 설치하지 않도록 선택하는 경우 다음 콘솔을 열 때 제공됩니다.

## <a name="logging"></a>로깅
Updates Publisher는 **%WINDIR%\Temp\UpdatesPublisher.log**에 Updates Publisher에 대한 기본 정보를 기록합니다.

로그를 보려면 메모장 또는 **CMTrace**를 사용합니다. CMTrace는 Configuration Manager 로그 파일 도구이며 Configuration Manager 원본 미디어의 **\SMSSetup\Tools** 폴더에 있습니다.

로그의 크기 및 해당 수준의 세부 정보를 변경할 수 있습니다.

데이터베이스 로깅을 사용하도록 설정하면 Updates Publisher 데이터베이스에 대해 실행되는 쿼리 정보가 포함됩니다. 데이터베이스 로깅을 사용하면 Updates Publisher 컴퓨터의 성능이 저하될 수 있습니다.

로그 파일을 보려면 콘솔에서 ![속성](media/properties2.png)을 클릭하여 **Updates Publisher 속성**을 연 다음 **로그 파일 보기**를 선택합니다.

## <a name="expire-unreferenced-software-updates"></a>참조되지 않은 소프트웨어 업데이트 만료
**Software Update Cleanup Wizard**(소프트웨어 업데이트 정리 마법사)를 실행하여 업데이트 서버에 있지만 Updates Publisher 리포지토리에는 없는 업데이트를 만료시킵니다. 그러면 Configuration Manager에 통보하여 이후의 모든 배포에서 해당 업데이트를 제거합니다.

업데이트를 만료시키는 작업은 되돌릴 수 없습니다. 선택한 소프트웨어 업데이트가 더 이상 조직에 필요하지 않은 경우에만 이 작업을 수행합니다.

### <a name="to-remove-expired-software-updates"></a>만료된 소프트웨어 업데이트를 제거하려면
1.  Updates Publisher 콘솔에서 ![속성](media/properties2.png)을 클릭하여 **Updates Publisher 속성**을 연 다음 **옵션**을 선택합니다.

2.  **고급**을 선택한 다음 **Software Update Clean Wizard**(소프트웨어 업데이트 정리 마법사)에서 **시작**을 선택합니다.

3.  만료시킬 소프트웨어 업데이트를 선택한 후 **다음**을 선택합니다.

4.  선택 항목을 검토한 후 **다음**을 선택하여 선택 항목을 수락하고 해당 업데이트를 만료시킵니다.

5.  마법사가 완료되면 **닫기**를 선택하여 마법사를 마칩니다.
