---
title: Technical Preview 1801 | Microsoft Docs
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 기술 미리 보기 버전 1801에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/19/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5a352ae0-355f-4fcf-b863-fb0654f51c52
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 995c84e51ec72b385390f76fabfe08d60c2832d7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32335952"
---
# <a name="capabilities-in-technical-preview-1801-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1801의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1801에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 

이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 검토하세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 피드백을 제공하는 방법에 대해 설명합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
**Known Issues in this Technical Preview:**
-->
**이 Technical Preview의 알려진 문제:**
-   **수동 모드의 사이트 서버가 있는 경우 새 미리 보기 버전에 대한 업데이트가 실패합니다**. [수동 모드의 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 경우 이 새 미리 보기 버전으로 업데이트하기 전에 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 업데이트를 완료한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.
<!--sms 489412-->


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Section Template
##  FEATURE
<-- TFS ID - need to fix comment md here
### Procedure 1
### Try it out!  
 Try to complete the tasks. Then send **Feedback** from the **Home** tab of the ribbon letting us know how it worked.
 -  Task 1
 -  Task 2              
-->



## <a name="create-phased-deployments"></a>단계별 배포 만들기
<!-- 1357405 -->
단계별 배포는 여러 배포를 만들지 않고도 자동으로 소프트웨어를 조정하고 순차적으로 출시합니다. 이 Technical Preview 버전에서는 관리 콘솔의 작업 순서에 대해 단계별 배포 마법사를 완료할 수 있습니다. 그러나 배포는 만들어지지 않습니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기  
  작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.
 
**작업 순서에 대한 단계별 배포 만들기** </br>
1. **소프트웨어 라이브러리** 작업 영역에서 **운영 체제**를 확장하고 **작업 순서**를 선택합니다.
2. 기존 작업 순서를 마우스 오른쪽 버튼으로 클릭하고 **단계별 배포 만들기**를 선택합니다. 
3. **일반** 탭에서 단계별 배포에 이름, 설명(선택 사항)을 입력하고 **자동으로 기본 파일럿 및 프로덕션 단계 만들기**를 선택합니다. 
4. **파일럿 컬렉션** 및 **프로덕션 컬렉션** 필드를 채웁니다. **다음**을 선택합니다.
5. **설정** 탭에서 각 일정 설정에 대해 하나의 옵션을 선택하고 완료되면 **다음**을 선택합니다. 
6. **단계**  탭에서 필요하면 단계를 편집하고 **다음**을 클릭합니다.
7. **요약** 탭에서 선택을 확인한 후 **다음**을 클릭하여 진행합니다.

## <a name="co-management-reporting"></a>공동 관리 보고
<!-- 1356648 -->
[공동 관리](/sccm/core/clients/manage/co-management-overview) 기능을 사용하면 사용자 환경의 공동 관리에 대한 정보가 포함된 대시보드를 볼 수 있습니다. Configuration Manager 콘솔에서 **모니터링** 작업 공간으로 이동하고 **업그레이드 준비**를 확장하고 **공동 관리** 대시보드를 선택합니다. 이 대시보드에는 다음과 같은 타일이 있습니다.
- **공동 관리 장치**: 환경 내에서 공동 관리에 사용했던 장치의 비율
- **운영 체제 배포**: 버전별 운영 체제(OS)의 분류. 이 차트에서는 아래와 같은 그룹화를 사용합니다.
   - Windows 7 & 8.x
   - 1709 이하의 Windows 10
   - Windows 10 1709 이상
  > [!NOTE] 
  > Windows 10, 1709 이상의 버전은 공동 관리에 필수 구성 요소입니다.
- **공동 관리 상태**: 다음 범주에서 장치의 성공 또는 실패를 분류합니다.
   - 성공, 하이브리드 Azure AD 조인됨
   - 성공, Azure AD 조인됨
   - 실패: 자동 등록 실패함
- **워크로드 전환**: 사용 가능한 세 가지 작업 부하에 대해 Microsoft Intune으로 전환한 장치 수를 나타내는 가로 막대형 차트 
   - 규정 준수 정책
   - 리소스 액세스
   - Windows Update for Business

### <a name="prerequisites"></a>필수 구성 요소
- Configuration Manager 콘솔을 실행하는 컴퓨터는 Internet Explorer 9 이상이 필요합니다.



## <a name="improvements-to-automatic-deployment-rule-evaluation-schedule"></a>자동 배포 규칙 평가 일정의 향상된 기능
<!-- 1357133 -->
[사용자 음성 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8819518-software-update-patch-tuesday-scheduling)에 따라 ADR(자동 배포 규칙) 평가가 기준일로부터 오프셋되도록 예약할 수 있습니다. 예를 들어, 매월 두 번째 화요일 후 2일째 오프셋은 목요일에 규칙을 평가합니다. 

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다. <br/>

**평가하는 사용자 지정 일정과 기준일로부터 ADR 오프셋 만들기** </br>
1.  **소프트웨어 라이브러리** 작업 영역에서 **소프트웨어 업데이트**를 확장한 다음 **자동 배포 규칙**을 선택합니다.
2. **자동 배포 규칙**을 마우스 오른쪽 단추로 클릭하고 **자동 배포 규칙 생성**을 선택합니다. 
3. 프롬프트에 따라 **일반**, **배포 설정** 및 **소프트웨어 업데이트** 탭을 완료합니다. 
4. **평가 일정** 탭에서 **일정에 따라 규칙 실행** 및 **사용자 정의**을 선택합니다.
5. 사용자 정의 일정의 경우 **월별**을 선택하고 두 번째 화요일처럼 기본 요일을 입력합니다. 
6. **오프셋(일)**, 오프셋에 대한 일 수를 확인한 다음, 완료되면 **확인**을 선택합니다.  
7. **자동 배포 규칙 만들기 마법사**의 나머지 부분을 완료합니다. 



## <a name="reassign-distribution-point"></a>배포 지점 재할당
<!-- 1306937 -->
많은 고객들이 대형 Configuration Manager 인프라를 보유하고 있으며 환경을 단순화하기 위해 기본 또는 보조 사이트를 줄이고 있습니다. 하지만 관리 대상 고객에게 콘텐츠를 제공하기 위해 각 지사에서 배포 지점을 유지해야 합니다. 이러한 배포 지점에는 종종 여러 테라바이트 이상의 콘텐츠가 포함됩니다. 이 컨텐츠는 이러한 원격 서버에 배포하는 데 상당한 시간과 네트워크 대역폭을 소비합니다. 

이 기능을 사용하면 콘텐츠를 재배포하지 않고 다른 기본 사이트에 배포 지점을 재할당할 수 있습니다. 이 작업은 서버의 모든 콘텐츠를 유지하면서 사이트 시스템 할당을 업데이트합니다. 여러 배포 지점을 재할당해야 하는 경우 먼저 단일 배포 지점에서 이 작업을 수행한 다음 한 번에 하나씩 서버를 추가합니다.

> [!IMPORTANT]
> 사이트 시스템 서버는 배포 지점 역할만 호스팅할 수 있습니다. 사이트 시스템 서버가 상태 마이그레이션 지점과 같은 다른 Configuration Manager 서버 역할을 호스팅하는 경우 배포 지점을 재할당할 수 없습니다. 클라우드 배포 지점을 재할당할 수 없습니다. 

이 옵션은 단일 기본 사이트의 Technical Preview 제한 때문에 이 릴리스에서 작동하지 않습니다. 시나리오를 고려한 다음 이 작업의 기능과 관련하여 리본의 **홈** 탭에서 **피드백**을 보냅니다.
1. Configuration Manager 콘솔에서 **관리** 작업 공간으로 이동하여 **배포 지점** 노드를 선택합니다.
2. 대상 배포 지점을 마우스 오른쪽 단추로 클릭하고 **배포 지점 재할당**을 선택합니다. 
  ![배포 지점 재할당](media/1306937-reassign-dp.png)
3. 이 배포 지점을 재할당할 사이트 서버 및 사이트 코드를 선택합니다. 
  ![사이트 서버 선택](media/1306937-select-site.png)



## <a name="improvements-to-hardware-inventory"></a>하드웨어 인벤토리의 향상된 기능
<!-- 1357389 -->
새로 추가된 클래스의 경우 키가 아닌 하드웨어 인벤토리 속성에 대해 255자 이상의 문자열 길이를 지정할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기  
작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.<br/>

1. **관리** 작업 공간에서 **클라이언트 설정**을 클릭하여 편집할 클라이언트 장치 설정을 강조 표시하고 마우스 오른쪽 버튼으로 클릭한 다음 **속성**을 선택합니다. 
2. **하드웨어 인벤토리**, **클래스**, **추가**를 선택합니다.
3. **연결** 단추를 클릭합니다.
4. **컴퓨터 이름**, **WMI 네임스페이스**를 채우고 필요한 경우 **재귀**를 선택합니다. 연결하는 데 필요한 경우 자격 증명을 제공합니다. **연결**을 클릭하여 네임스페이스 클래스를 봅니다.
5. 새 클래스를 선택하고 **편집**을 클릭합니다.
6. 키가 아닌 문자열이며 최소 하나의 속성인 **길이**을 255보다 크게 변경합니다. **확인**을 클릭합니다. 
7. **하드웨어 인벤토리 클래스 추가**에 대해 편집된 속성이 선택되었는지 확인하고 **확인**을 클릭합니다. 
8. 길이가 255자를 초과하는 속성을 포함하는 새로 추가된 클래스로 하드웨어 인벤토리를 수집합니다. 



## <a name="improvements-to-client-settings-for-software-center"></a>소프트웨어 센터에 대한 클라이언트 설정의 향상된 기능
<!-- 1351224 & 1355146 -->
이 Technical Preview 버전에서는 클라이언트 설정의 소프트웨어 센터 사용자 지정이 향상되었습니다. 

1. 소프트웨어 센터에 대한 클라이언트 설정에는 이제 **사용자 정의** 단추가 있습니다.
2. 미리보기가 추가되어 소프트웨어 센터 배너의 모양을 보여줍니다.<!--1351224-->
    - 로고를 선택하지 않으면 미리보기에 회사 이름 텍스트와 색상이 표시됩니다.
    - 로고를 선택하면 미리보기에 로고와 회사 이름 텍스트가 표시됩니다.  
3.  **소프트웨어 센터에서 승인되지 않은 응용 프로그램 숨기기**는 소프트웨어 센터의 새로운 설정입니다. 이 옵션을 사용하면 소프트웨어 센터에서 승인이 필요한 사용자 사용 가능 애플리케이션이 숨겨집니다.<!--1355146-->

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 작업을 완료합니다. 그런 다음 어떻게 작동하는지 알 수 있도록 리본의 **홈** 탭에서 **피드백**을 보냅니다.

1. **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다. 클라이언트 디바이스 설정을 선택하여 편집합니다. 이를 마우스 오른쪽 단추로 클릭한 다음 **속성**, **소프트웨어 센터**를 차례로 선택합니다.
2.  **사용자 지정** 단추를 클릭합니다. 미리 보기를 포함하여 다른 사용자 지정을 설정해봅니다.
3. **소프트웨어 센터에서 승인되지 않은 프로그램 숨기기** 설정을 사용합니다. 소프트웨어 센터의 변경 내용을 확인합니다. 



## <a name="new-settings-for-windows-defender-application-guard"></a>Windows Defender Application Guard의 새로운 설정
<!-- 1356256 -->
Windows 10 버전 1709 이상이 설치된 디바이스에는 [Windows Defender Application Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy)에 대한 두 가지 새로운 호스트 상호 작용 설정이 있습니다. 
1. 호스트의 가상 그래픽 프로세서에 대한 액세스 권한을 웹 사이트에 부여할 수 있습니다. 
2. 컨테이너 내부에 다운로드한 파일을 호스트에 유지할 수 있습니다. </br>



## <a name="improvements-to-run-scripts"></a>스크립트 실행의 향상된 기능
<!-- 1236459 -->
이제 [**스크립트 실행** 기능](/sccm/apps/deploy-use/create-deploy-scripts)을 사용하여 서명된 PowerShell 스크립트를 가져오고 실행할 수 있습니다. 
- 스크립트 무결성을 유지하려면 복사/붙여넣기 대신 서명된 스크립트를 가져와야 합니다. 
- 서명된 스크립트를 가져온 후에는 편집할 수 없습니다.
    
>[!IMPORTANT]
>이 Technical Preview에는 두 가지의 임시 제한이 있습니다.
>- 스크립트는 스크립트 실행 기능에서만 가져올 수 있으며 콘솔에서 직접 편집할 수 없습니다.
>- 비 유니코드 인코딩으로 가져온 스크립트는 콘솔에 잘못 표시될 수 있습니다. 하지만 스크립트는 원래 작성된 대로 실행됩니다.





## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
