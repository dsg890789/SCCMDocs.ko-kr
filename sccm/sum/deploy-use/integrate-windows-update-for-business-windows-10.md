---
title: Windows 10에서 비즈니스용 Windows 업데이트와 통합
titleSuffix: Configuration Manager
description: 비즈니스용 Windows 업데이트를 사용하면 Windows 업데이트 서비스에 연결된 디바이스에 대해 조직의 Windows 10 기반 디바이스를 최신 상태로 유지할 수 있습니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 183315fe-27bd-456f-b2c5-e8d25e05229b
ms.collection: M365-identity-device-management
ms.openlocfilehash: 456e4537e7c397063c50422e8c408dc5d688af04
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56121576"
---
# <a name="integration-with-windows-update-for-business-in-windows-10"></a>Windows 10에서 비즈니스용 Windows 업데이트와 통합

*적용 대상: System Center Configuration Manager(현재 분기)*

조직의 Windows 10 기반 디바이스를 WU(Windows 업데이트) 서비스에 직접 연결하면 WUfB(비즈니스용 Windows 업데이트)를 통해 최신 보안 방어 및 Windows 기능을 사용하여 이러한 디바이스를 항상 최신 상태로 유지할 수 있습니다. Configuration Manager는 WUfB 및 WSUS를 사용하여 소프트웨어 업데이트를 가져오는 Windows 10 컴퓨터를 구분할 수 있습니다.  

 Configuration Manager 클라이언트가 WUfB 또는 Windows 참가자를 포함하는 WU에서 업데이트를 수신하도록 구성된 경우에는 일부 Configuration Manager 기능을 더 이상 사용할 수 없습니다.  

-   Windows 업데이트 준수 보고:  

    -   Configuration Manager에서 WU에 게시되는 업데이트를 인식할 수 없습니다. WU에서 업데이트를 수신하도록 구성된 Configuration Manager 클라이언트는 해당 업데이트에 대해 Configuration Manager 콘솔에 **알 수 없음**을 표시합니다.  

    -   **알 수 없음** 상태는 WSUS의 검색 상태를 다시 보고하지 않은 클라이언트에만 사용되었므로 전체적인 준수 상태 문제를 해결하기 어렵습니다. 이제 WU에서 업데이트를 수신하는 Configuration Manager 클라이언트도 포함됩니다.  

    -   업데이트 준수 상태를 기반으로 하는 조건부 액세스(회사 리소스 대상)는 WU에서 업데이트를 수신하는 클라이언트에 대해 예상대로 작동하지 않습니다. 해당 클라이언트가 Configuration Manager의 준수를 충족하지 않기 때문입니다.  

    -   정의 업데이트 준수는 전체 업데이트 준수 보고의 일부이며 역시 예상대로 작동하지 않습니다.  또한 정의 업데이트 준수는 조건부 액세스 평가의 일부이기도 합니다.  

-   업데이트 준수 상태를 기반으로 하는 Defender에 대한 전체 Endpoint Protection 보고에서는 검색 데이터가 누락되어 정확한 결과를 반환하지 않습니다.  

-   Configuration Manager는 WUfB에 연결하여 업데이트를 받는 클라이언트에 Office, IE, Visual Studio와 같은 Microsoft 업데이트를 배포할 수 없습니다.  

-   Configuration Manager는 WUfB에 연결하여 업데이트를 받는 클라이언트에 WSUS에 게시되고 Configuration Manager를 통해 관리되는 타사 업데이트를 배포할 수 없습니다.  

-   소프트웨어 업데이트 인프라를 사용하는 Configuration Manager 전체 클라이언트 배포는 WUfB에 연결하여 업데이트를 받는 클라이언트에 대해 작동하지 않습니다.  

## <a name="identify-clients-that-use-wufb-for-windows-10-updates"></a>Windows 10 업데이트를 위해 WUfB를 사용하는 클라이언트 식별  
 다음 프로시저를 사용하여 Windows 10 업데이트 및 업그레이드를 가져오는 데 WUfB를 사용하는 클라이언트를 식별합니다. 그런 다음, 이러한 클라이언트를 업데이트를 가져오는 데 WSUS를 사용하지 않도록 구성한 후, 클라이언트 에이전트 설정을 배포하여 해당 클라이언트에 소프트웨어 업데이트 워크플로를 사용하지 않도록 설정합니다.  

 **전제 조건**  

-   클라이언트에서 Windows 10 Desktop Pro 또는 Windows 10 Enterprise Edition 버전 1511 이상을 실행합니다.  

-   [비즈니스용 Windows 업데이트](https://technet.microsoft.com/library/mt622730\(v=vs.85\).aspx) 가 배포되어 있으며 클라이언트에서 WUfB를 사용하여 Windows 10 업데이트 및 업그레이드를 가져옵니다.  

#### <a name="to-identify-clients-that-use-wufb"></a>WUfB를 사용하는 클라이언트를 식별하려면 다음을 수행합니다.  

1.  이전에 설정된 경우 Windows 업데이트 에이전트를 사용하지 않도록 설정하여 WSUS에 대한 검사가 이루어지지 않도록 합니다. 다음 레지스트리 키는 컴퓨터가 WSUS 또는 Windows 업데이트에 대해 검사하는지를 나타내도록 설정될 수 있습니다.  값이 2이면 WSUS에 대해 검사하지 않는 것입니다.  
    - **HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate\AU\UseWUServer**

2.  Configuration Manager 리소스 탐색기의 **Windows 업데이트** 노드 아래에 새 특성 **UseWUServer**가 있습니다.  

3.  업데이트 및 업그레이드를 위해 WUfB를 통해 연결된 모든 컴퓨터에 대해 **UseWUServer** 특성을 기반으로 컬렉션을 만듭니다.  

4.  클라이언트 에이전트 설정을 만들어 소프트웨어 업데이트 워크플로를 사용하지 않도록 설정합니다. 설정을 WUfB에 직접 연결하는 컴퓨터의 컬렉션에 배포합니다.  

5.  WUfB를 통해 관리되는 컴퓨터는 준수 상태가 **알 수 없음**으로 표시되며 전체 준수 비율의 일부로 계산되지 않습니다.  

## <a name="configure-windows-update-for-business-deferral-policies"></a>비즈니스용 Windows 업데이트 지연 정책 구성
<!-- 1290890 --> Configuration Manager 버전 1706부터 비즈니스용 Windows 업데이트에서 직접 관리되는 Windows 10 장치에 대한 Windows 10 기능 업데이트 또는 품질 업데이트의 지연 정책을 구성할 수 있습니다. **소프트웨어 라이브러리** > **Windows 10 서비스** 아래의 새 **비즈니스용 Windows 업데이트 정책** 노드에서 지연 정책을 관리할 수 있습니다.

>[!NOTE] 
>Configuration Manager 버전 1802부터는 Windows 참가자에 대한 지연 정책을 설정할 수 있습니다. <!--507201-->Windows 참가자 프로그램에 대한 자세한 내용은 [비즈니스용 Windows 참가자 프로그램 시작](https://docs.microsoft.com/windows/deployment/update/waas-windows-insider-for-business)을 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
-   Windows 10 버전 1703 이상
-   비즈니스용 Windows 업데이트에서 관리되는 Windows 10 디바이스는 인터넷에 연결되어 있어야 합니다.

#### <a name="to-create-a-windows-update-for-business-deferral-policy"></a>비즈니스용 Windows 업데이트 지연 정책을 만들려면
1. **소프트웨어 라이브러리** > **Windows 10 서비스** > **비즈니스용 Windows 업데이트 정책**으로 이동합니다.
2. **홈** 탭의 **만들기** 그룹에서 **비즈니스용 Windows 업데이트 정책 만들기**를 선택하여 비즈니스용 Windows 업데이트 정책 만들기 마법사를 엽니다.
3. **일반** 페이지에서 정책의 이름 및 설명을 제공합니다.
4. **지연 정책** 페이지에서 기능 업데이트를 연기할지 또는 일시 중지할지를 구성합니다. 기능 업데이트는 일반적으로 새로운 Windows용 기능입니다. **분기 준비 수준** 설정을 구성한 후에 Microsoft에서 출시한 후에 기능 업데이트 수신을 연기할지 여부 및 연기 기간을 정의할 수 있습니다.
    - **분기 준비 상태 수준**: 디바이스가 Windows 업데이트(현재 분기 또는 비즈니스용 현재 분기)를 받을 분기를 설정합니다.
    - **지연 기간(일)**:  기능 업데이트를 연기할 일 수를 지정합니다. 이러한 기능 업데이트는 출시되고 365일 동안 수신을 연기할 수 있습니다.
    - **기능 업데이트 시작 일시 중지**: 기능 업데이트를 일시 중지한 날로부터 최대 60일 동안 디바이스에서 기능 업데이트를 받지 못하도록 일시 중지할지 여부를 선택합니다. 최대 일수가 경과하고 나면 일시 중지 기능은 자동으로 만료되고 디바이스가 Windows 업데이트에서 적용되는 업데이트를 검색합니다. 이 검색 후에 업데이트를 다시 일시 중지할 수 있습니다. 이 확인란을 선택 취소하여 기능 업데이트 일시 중지를 해제할 수 있습니다.   
5. 품질 업데이트를 연기할지 또는 일시 중지할지를 선택합니다. 품질 업데이트는 일반적으로 기존 Windows 기능에 대한 수정 내용 및 향상된 기능이며, 매월 첫째 화요일에 게시되는 것이 보통입니다. 물론 Microsoft는 언제든지 이러한 업데이트를 출시할 수 있습니다. 출시된 후에 품질 업데이트 수신을 연기할지 여부 및 연기할 기간을 정의할 수 있습니다.
    - **지연 기간(일)**: 품질 업데이트를 연기할 일 수를 지정합니다. 이러한 품질 업데이트는 출시되고 30일 동안 수신을 연기할 수 있습니다.
    - **품질 업데이트 시작 일시 중지**: 기능 업데이트를 일시 중지한 날로부터 최대 35일 동안 디바이스에서 품질 업데이트를 받지 못하도록 일시 중지할지 여부를 선택합니다. 최대 일수가 경과하고 나면 일시 중지 기능은 자동으로 만료되고 디바이스가 Windows 업데이트에서 적용되는 업데이트를 검색합니다. 이 검색 후에 업데이트를 다시 일시 중지할 수 있습니다. 이 확인란을 선택 취소하여 품질 업데이트 일시 중지를 해제할 수 있습니다.
6. **다른 Microsoft 제품에 대한 업데이트 설치**를 선택하여 지연 설정이 Windows 업데이트 뿐만 아니라 Microsoft 업데이트에도 적용될 수 있게 하는 그룹 정책 설정을 사용하도록 설정합니다.
7. Windows 업데이트에서 드라이버를 자동으로 업데이트하려면 **Windows 업데이트에 드라이버 포함**을 선택합니다. 이 설정을 선택 취소하면 드라이버 업데이트가 Windows 업데이트에서 다운로드되지 않습니다.
8. 마법사를 완료하여 새 지연 정책을 만듭니다.

#### <a name="to-deploy-a-windows-update-for-business-deferral-policy"></a>비즈니스용 Windows 업데이트 지연 정책을 배포하려면
1. **소프트웨어 라이브러리** > **Windows 10 서비스** > **비즈니스용 Windows 업데이트 정책**으로 이동합니다.
2. **홈** 탭의 **배포** 그룹에서 **비즈니스용 Windows 업데이트 정책 배포**를 선택합니다.
3. 다음 설정을 구성합니다.
    - **배포할 구성 정책**: 배포하려는 비즈니스용 Windows 업데이트 정책을 선택합니다.
    - **컬렉션**: **찾아보기**를 클릭하여 프로필을 배포하려는 컬렉션을 선택합니다.
    - **지원되는 경우 비규정 준수 규칙 수정**: Configuration Manager에서 등록된 모바일 디바이스의 레지스트리, 스크립트 및 모든 설정, WMI(Windows Management Instrumentation)에 대해 비규정 준수 규칙을 자동으로 수정하도록 선택합니다.
    - **유지 관리 기간을 벗어나도 수정 허용**: 정책을 배포할 컬렉션에 대해 유지 관리 기간이 구성된 경우 유지 관리 기간 외의 기간에 규정 준수 설정이 값을 수정할 수 있도록 하려면 이 옵션을 사용하도록 설정합니다. 유지 관리 기간에 대한 자세한 내용은 [유지 관리 기간을 사용하는 방법](/sccm/core/clients/manage/collections/use-maintenance-windows)을 참조하세요.
    - **경고 생성**: 지정된 날짜 및 시간을 기준으로 구성 기준 규정 준수가 지정된 비율에 못 미치는 경우에 생성되는 경고를 구성합니다. 경고를 System Center Operations Manager로 전송할지 여부도 지정할 수 있습니다.
    - **임의 지연(시)**: 네트워크 디바이스 등록 서비스의 과도한 처리를 방지하기 위해 지연 기간을 지정합니다. 기본값은 64시간입니다.
    - **일정**: 클라이언트 컴퓨터에서 배포된 프로필이 평가되는 규정 준수 평가 일정을 지정합니다. 단순 일정 또는 사용자 지정 일정 중에서 지정할 수 있습니다. 사용자가 로그온해 있을 때 클라이언트 컴퓨터에서 프로필을 평가합니다.
4.  마법사를 완료하여 프로필을 배포합니다.
