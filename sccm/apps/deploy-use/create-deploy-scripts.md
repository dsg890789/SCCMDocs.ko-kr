---
title: "스크립트 만들기 및 실행"
titleSuffix: Configuration Manager
description: "Configuration Manager를 사용하여 클라이언트 장치에서 스크립트를 만들고 실행합니다."
ms.custom: na
ms.date: 09/15/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: "14"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: d1cbb760c6e40c21b97d0227ff93613066189d4b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 PowerShell 스크립트 만들기 및 실행

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서 패키지 및 프로그램을 사용하여 스크립트를 배포하는 것 외에 다음 기능을 사용하여 다음과 같은 작업을 수행할 수 있습니다.

- Configuration Manager에 PowerShell 스크립트 가져오기
- Configuration Manager 콘솔에서 스크립트 편집(서명되지 않은 스크립트만 해당)
- 스크립트를 승인 또는 거부로 표시하여 보안 강화
- Windows 클라이언트 PC 및 온-프레미스 관리 Windows PC 컬렉션에 대해 스크립트를 실행합니다. 스크립트는 배포하지 않아도 됩니다. 클라이언트 장치에서 거의 실시간으로 실행되기 때문입니다.
- Configuration Manager 콘솔에서 스크립트에 의해 반환된 결과를 검토합니다.

>[!TIP]
>이 버전의 Configuration Manager에서 스크립트는 시험판 기능입니다. 스크립트를 사용하도록 설정하려면 [System Center Configuration Manager의 시험판 기능](/sccm/core/servers/manage/pre-release-features)을 참조하세요.

## <a name="prerequisites"></a>전제 조건

PowerShell 스크립트를 실행하려면 클라이언트에서 PowerShell 버전 3.0 이상이 실행되고 있어야 합니다. 그러나 실행하는 스크립트에 이후 버전의 PowerShell 기능이 포함되어 있을 경우 스크립트를 실행하는 클라이언트에서 해당 버전이 실행되고 있어야 합니다.

Configuration Manager 클라이언트는 스크립트를 실행하려면 1706 릴리스 이상의 클라이언트를 실행하고 있어야 합니다.

스크립트를 사용하려면 해당 Configuration Manager 보안 역할의 구성원이어야 합니다.

- 스크립트를 가져오기 작성하려면 - 계정의 **전체 관리자** 보안 역할에 **SMS 스크립트**에 대한 **만들기** 권한이 있어야 합니다.
- 스크립트를 승인하거나 거부하려면 - 계정의 **전체 관리자** 보안 역할에 **SMS 스크립트**에 대한 **승인** 권한이 있어야 합니다.
- 스크립트를 실행하려면 - 계정의 **준수 설정 관리자** 보안 역할에 **컬렉션**에 대한 **스크립트 실행** 권한이 있어야 합니다.

Configuration Manager 보안 역할에 대한 자세한 내용은 [역할 기반 관리 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)을 참조하세요.

기본적으로 사용자는 작성한 스크립트를 승인할 수 없습니다. 스크립트는 강력하고 다양한 기능을 제공하며 여러 장치에 배포할 수 있으므로 스크립트를 작성하는 사용자와 스크립트를 승인하는 사용자 간에 역할을 분리할 수 있습니다. 이러한 역할을 통해 감독 없이 스크립트를 실행할 때도 추가적으로 보안을 강화하는 효과를 얻을 수 있습니다. 쉬운 테스트를 위해 이러한 보조 승인을 해제할 수 있습니다.

## <a name="allow-users-to-approve-their-own-scripts"></a>사용자가 자신의 스크립트를 승인하도록 허용

1. Configuration Manager 콘솔에서 **관리**를 클릭합니다.
2. **관리** 작업 영역에서 **사이트 구성**을 확장하고 **사이트**를 클릭합니다.
3. 사이트 목록에서 사이트를 선택한 후 **홈** 탭의 **사이트** 그룹에서 **계층 설정**을 클릭합니다.
4. **계층 구조 설정 속성** 대화 상자의 **일반** 탭에서 **스크립트 작성자가 스크립트를 승인하도록 허용 안 함** 확인란을 선택 취소합니다.

>[!IMPORTANT]
>모범 사례에서는 스크립트 작성자가 고유한 스크립트를 승인하도록 허용하지 않아야 합니다. 랩 설정에서만 허용해야 합니다. 프로덕션 환경에서 이 설정을 변경하는 잠재적인 영향을 신중하게 고려하세요.

## <a name="import-and-edit-a-script"></a>스크립트 가져오기 및 편집

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. **소프트웨어 라이브러리** 작업 영역에서 **스크립트**를 클릭합니다.
3. **홈** 탭의 **만들기** 그룹에서 **스크립트 만들기**를 클릭합니다.
4. **스크립트 만들기** 마법사의 **스크립트** 페이지에서 다음 설정을 구성합니다.
    - **스크립트 이름** - 스크립트의 이름을 입력합니다. 여러 스크립트를 같은 이름으로 만들 수 있지만 중복된 이름을 사용하면 Configuration Manager 콘솔에서 필요한 스크립트를 찾는 것이 더 어려워집니다.
    - **스크립트 언어** - 현재 PowerShell 스크립트만 지원됩니다.
    - **가져오기** - 콘솔로 PowerShell 스크립트를 가져옵니다. 스크립트는 **스크립트** 필드에 표시됩니다.
    - **지우기** - 스크립트 필드에서 현재 스크립트를 제거합니다.
    - **스크립트** - 현재 가져온 스크립트를 표시합니다. 필요에 따라 이 필드에서 스크립트를 편집할 수 있습니다.
5. 마법사를 완료합니다. 새 스크립트가 **승인 대기 중** 상태로 **스크립트** 목록에 표시됩니다. 클라이언트 장치에서 이 스크립트를 실행하려면 먼저 승인해야 합니다.

### <a name="script-examples"></a>스크립트 예제

다음은 이 기능을 사용할 수 있는 스크립트를 보여 주는 몇 가지 예제입니다.

#### <a name="create-a-folder"></a>폴더 만들기

*New-Item "c:\scripts" -type folder name*


#### <a name="create-a-file"></a>파일 만들기

*New-Item c:\scripts\new_file.txt -type file name*


## <a name="approve-or-deny-a-script"></a>스크립트 승인 또는 거부

스크립트를 실행하려면 먼저 승인을 받아야 합니다. 스크립트를 승인하려면

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. **소프트웨어 라이브러리** 작업 영역에서 **스크립트**를 클릭합니다.
3. **스크립트** 목록에서 승인 또는 거부하려는 스크립트를 선택한 후 **홈** 탭의 **스크립트** 그룹에서 **승인/거부**를 클릭합니다.
4. **스크립트 승인 또는 거부** 대화 상자에서 스크립트를 **승인** 또는 **거부**한 다음, 필요에 따라 이와 같은 결정에 대한 설명을 입력합니다. 스크립트를 거부하는 경우 클라이언트 장치에서 실행할 수 없습니다.
5. 마법사를 완료합니다. **스크립트** 목록에서 **승인 상태** 열이 수행한 작업에 따라 변경됩니다.

## <a name="run-a-script"></a>스크립트 실행
스크립트가 승인되면 선택한 컬렉션에 대해 실행할 수 있습니다.

1. Configuration Manager 콘솔에서 **자산 및 준수**을 클릭합니다.
2. 자산 및 호환성 작업 영역에서 **장치 컬렉션**을 클릭합니다.
3. **장치 컬렉션** 목록에서 스크립트를 실행하려는 장치 컬렉션을 클릭합니다.
4. **홈** 탭의 **모든 시스템** 그룹에서 **스크립트 실행**을 클릭합니다.
5. **스크립트 실행** 마법사의 **스크립트** 페이지에서 목록에 있는 스크립트를 선택합니다. 승인된 스크립트만 표시됩니다.
6. **다음**을 클릭하여 마법사를 완료합니다.

>[!IMPORTANT]
>스크립트에 1시간의 실행 기간이 지정됩니다. 이 기간 안에 실행되지 않으면(예: PC가 꺼진 경우) 다시 실행해야 합니다.

>[!IMPORTANT]
>스크립트는 대상으로 지정된 클라이언트에서 시스템 또는 컴퓨터 계정으로 실행됩니다. 이 계정은 매우 제한된 네트워크 액세스 권한을 갖습니다. 이를 염두하여 원격 시스템에 대한 액세스 및 스크립트에 의한 위치를 프로비전해야 합니다.

## <a name="next-steps"></a>다음 단계

클라이언트 장치에 대해 스크립트를 실행한 후 다음 절차를 사용하여 작업의 성공 여부를 모니터링합니다.

1. Configuration Manager 콘솔에서 **모니터링**을 클릭합니다.
2. **모니터링** 작업 영역에서 **스크립트 상태**를 클릭합니다.
3. **스크립트 상태** 목록에서 클라이언트 장치에서 실행한 각 스크립트에 대한 결과를 확인합니다. 스크립트 종료 코드 **0**은 일반적으로 스크립트가 성공적으로 실행되었음을 나타냅니다.
