---
title: WSUS의 Endpoint Protection 맬웨어 정의
titleSuffix: Configuration Manager
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: a34d9401-83e4-471d-8e23-b8042fc11c90
author: aczechowski
description: 정의 업데이트를 자동 승인하려면 Windows Server Update Services를 구성하는 방법에 대해 알아봅니다.
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: b1c79a839ad1c83c96d7fe4583b46f6a3edbffba
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32349860"
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-windows-server-update-services-wsus-for-configuration-manager"></a>Configuration Manager의 WSUS(Windows Server Update Services)에서 다운로드하기 위해 Endpoint Protection 맬웨어 정의를 사용하도록 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

 WSUS를 사용하여 맬웨어 방지 정의를 최신 상태로 유지하는 경우 정의 업데이트를 자동 승인하도록 구성할 수 있습니다. Configuration Manager 소프트웨어 업데이트를 사용하여 정의를 최신 상태로 유지하는 것이 좋지만, 사용자가 정의 업데이트를 수동으로 시작할 수 있는 방법으로 WSUS를 구성할 수도 있습니다. WSUS를 정의 업데이트 원본으로 구성하려면 다음 절차를 따르세요.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-configuration-manager-software-updates"></a>Configuration Manager 소프트웨어 업데이트에서 Endpoint Protection 정의 업데이트를 동기화하려면

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.

3.  소프트웨어 업데이트 지점이 있는 사이트를 선택합니다. **설정** 그룹에서 **사이트 구성 요소 구성**을 클릭한 다음 **소프트웨어 업데이트 지점**을 클릭합니다.

4.  **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자의 **분류** 탭에서 **정의 업데이트** 확인란을 선택합니다.

5.  WSUS로 업데이트된 **제품** 을 지정합니다.

    -   Windows 8.1 이전 버전의 경우 **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자의 **제품** 탭에서 **Forefront Endpoint Protection 2010** 확인란을 선택합니다.

    -   Windows 10 이후 버전의 경우 **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자의 **제품** 탭에서 **Windows Defender** 및 **Windows Technical Preview 2** 확인란을 선택합니다.

6.  **확인** 을 클릭하여 **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자를 닫습니다.

 WSUS 서버가 Configuration Manager 환경에 통합되어 있지 않은 경우 다음 절차에 따라 Endpoint Protection 업데이트를 구성합니다.

## <a name="to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus"></a>독립 실행형 WSUS에서 Endpoint Protection 정의 업데이트를 동기화하려면

1.  WSUS 관리 콘솔에서 **컴퓨터**를 확장하고 **옵션**을 클릭한 다음 **제품 및 분류**를 클릭합니다.

2.  WSUS로 업데이트된 **제품** 을 지정합니다.

    -   Windows 8.1 이전 버전의 경우 **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자의 **제품** 탭에서 **Forefront Endpoint Protection 2010** 확인란을 선택합니다.

    -   Windows 10 이후 버전의 경우 **소프트웨어 업데이트 지점 구성 요소 속성** 대화 상자의 **제품** 탭에서 **Windows Defender** 및 **Windows Technical Preview 2** 확인란을 선택합니다.

3.  **제품 및 분류** 대화 상자의 **분류** 탭에서 **정의 업데이트** 및 **업데이트** 확인란을 선택합니다.

## <a name="approving-definition-updates"></a>정의 업데이트 승인
 사용 가능한 업데이트 목록을 요청하는 클라이언트에 Endpoint Protection 정의 업데이트를 제공하기 전에 먼저 승인하고 WSUS 서버로 다운로드해야 합니다. 클라이언트는 WSUS 서버에 연결하여 적용 가능한 업데이트를 확인한 다음 승인된 최신 정의 업데이트를 요청합니다.

### <a name="to-approve-definitions-and-updates-in-wsus"></a>WSUS에서 정의 및 업데이트를 승인하려면

1.  WSUS 관리 콘솔에서 **업데이트**를 클릭한 다음 **모든 업데이트** 또는 승인할 업데이트 분류를 클릭합니다.

2.  업데이트 목록에서 설치를 승인할 업데이트를 마우스 오른쪽 단추로 클릭한 다음 **승인**을 클릭합니다.

3.  **업데이트 승인** 대화 상자에서 업데이트를 승인할 컴퓨터 그룹을 선택하고 **설치 승인**을 클릭합니다.

 수동 승인 외에도 정의 업데이트 및 Endpoint Protection 업데이트에 대한 자동 승인 규칙을 설정할 수도 있습니다. 이렇게 하면 WSUS에서 다운로드한 Endpoint Protection 정의 업데이트를 자동으로 승인하도록 WSUS가 구성됩니다.

### <a name="to-configure-an-automatic-approval-rule"></a>자동 승인 규칙을 구성하려면

1.  WSUS 관리 콘솔에서 **옵션**을 클릭한 다음 **자동 승인**을 클릭합니다.

2.  **업데이트 규칙** 탭에서 **새 규칙**을 클릭합니다.

3.  **규칙 추가** 대화 상자의 **1단계: 속성 선택**에서 **업데이트가 특정 등급에 포함될 때** 확인란을 선택합니다.

4.  **2단계: 속성 편집**에서 **모든 등급**을 클릭합니다.

5.  **정의 업데이트**를 제외한 모든 확인란의 선택을 취소하고 **확인**을 클릭합니다.

6.  **규칙 추가** 대화 상자의 **1단계: 속성 선택**에서 **업데이트가 특정 제품에 포함될 때** 확인란을 선택합니다.

7.  **2단계: 속성 편집**에서 **모든 제품**을 클릭합니다.

8.  **Forefront Endpoint Protection** (Windows 8.1 이전) 또는 **Windows Defender** (Windows 10 이후)를 제외한 모든 확인란의 선택을 취소하고 **확인**을 클릭합니다.

9. **3단계: 이름 지정**에서 규칙의 이름을 입력하고 **확인**을 클릭합니다.

10. **자동 승인** 대화 상자에서 새로 만든 규칙의 확인란을 선택하고 **규칙 실행**을 클릭합니다.

> [!NOTE]
>  WSUS 서버 및 클라이언트 컴퓨터의 성능을 최대화하려면 이전 정의 업데이트를 거부합니다. 이 작업을 수행하기 위해 수정 버전 자동 승인 및 만료된 업데이트 자동 거부를 구성할 수 있습니다. 자세한 내용은 [Microsoft 기술 자료 문서 938947](http://go.microsoft.com/fwlink/p/?LinkId=204078)을 참조하세요.

> [!div class="button"]
[다음 단계 >](endpoint-antimalware-policies.md)

> [!div class="button"]
[뒤로 >](endpoint-configure-alerts.md)
