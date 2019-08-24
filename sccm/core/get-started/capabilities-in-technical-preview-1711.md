---
title: Technical Preview 1711 | Microsoft Docs
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1711에서 사용 가능한 기능을 알아봅니다.
ms.date: 11/17/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2e68dc12-6776-437a-9138-45cd7d4bf9cf
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: c4194472965ea498626921a1277047783251649e
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68340065"
---
# <a name="capabilities-in-technical-preview-1711-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1711의 기능

*적용 대상: System Center Configuration Manager(기술 미리 보기)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1711에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**이 Technical Preview의 알려진 문제:**
- **Windows 10 버전 1709(Fall Creators Update라고도 함) 지원**.  이 Windows 릴리스부터 Windows 미디어에는 여러 버전이 포함됩니다. 운영 체제 업그레이드 패키지 또는 운영 체제 이미지를 사용하도록 작업 시퀀스를 구성할 때 [Configuration Manager가 사용할 수 있도록 지원되는 버전](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client)을 선택해야 합니다.
- **수동 모드의 사이트 서버가 있는 경우 새 미리 보기 버전에 대한 업데이트가 실패합니다**. [수동 모드의 기본 사이트 서버](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability)가 있는 미리 보기 버전을 실행할 경우 미리 보기 사이트를 이러한 새 미리 보기 버전으로 성공적으로 업데이트하려면 먼저 수동 모드 사이트 서버를 제거해야 합니다. 사이트에서 업데이트를 완료한 후에 수동 모드 사이트 서버를 다시 설치할 수 있습니다.

  수동 모드 사이트 서버를 제거하려면
  1. 콘솔에서 **관리** > **개요** > **사이트 구성** > **서버 및 사이트 시스템 역할**로 이동한 다음 수동 모드 사이트 서버를 선택합니다.
  2. **사이트 시스템 역할** 창에서 **사이트 서버** 역할을 마우스 오른쪽 단추로 클릭한 후 **역할 제거**를 선택합니다.
  3. 수동 모드 사이트 서버를 마우스 오른쪽 단추로 클릭하고 **삭제**를 선택합니다.
  4. 사이트 서버를 제거한 후에 활성 기본 사이트 서버에서 **CONFIGURATION_MANAGER_UPDATE** 서비스를 다시 시작합니다.

**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Section Template
##  FEATURE
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-to-run-task-sequence"></a>작업 순서 실행 개선
<!-- 1261338 -->

이 기술 미리 보기는 작업 순서 실행 단계를 향상시킵니다. 향상된 기능은 다음과 같습니다.

- 소프트웨어 센터, PXE 및 미디어에서 모든 운영 체제 배포 시나리오를 지원합니다.
- 개체 삭제 중 복사, 가져오기, 내보내기 및 경고와 같은 콘솔 작업이 향상되었습니다.
- **사전 준비된 콘텐츠 파일 만들기** 마법사를 지원합니다.
- 배포 확인과 통합됩니다.
- 작업 순서 실행 단계는 이제 단일 부모-자식 관계뿐만 아니라 여러 수준의 작업 순서에서도 사용할 수 있습니다. 여러 수준 관계는 복잡성이 증가되므로 신중하게 사용합니다. 이러한 관계는 여전히 순환 참조를 확인합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기  

다음 작업을 완료한 다음 리본 메뉴의 **홈** 탭에서 **사용자 의견**을 전송하여 작동 상황을 알려주세요.

1. 작업 순서 편집기에서 **추가**를 클릭하고 **일반**을 선택한 다음 **작업 순서 실행**을 클릭합니다.
2. **찾아보기**를 클릭하여 자식 작업 순서를 선택합니다.

## <a name="allow-user-interaction-when-installing-an-application----1356976---"></a>애플리케이션 설치 시 사용자 상호 작용 허용 <!-- 1356976 -->

이 미리 보기를 사용하면 최종 사용자가 작업 순서를 실행하는 동안 애플리케이션 설치와 상호 작용할 수 있습니다. 예를 들어 최종 사용자에게 다양한 옵션을 요구하는 설치 프로세스를 실행합니다. 일부 애플리케이션 설치 관리자에서는 사용자 프롬프트를 닫을 수 없거나 설치 프로세스에 사용자에게만 알려진 특정 구성 값이 필요할 수 있습니다. 이 기능을 사용하면 이러한 설치 시나리오를 처리할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

다음 작업을 완료한 다음, 리본의 **홈** 탭에서 **사용자 의견**을 보내어 작동된 방식을 알려주세요.

1.  애플리케이션을 만들거나 편집합니다. 자세한 내용은 [System Center Configuration Manager에서 애플리케이션을 만들기](/sccm/apps/deploy-use/create-applications)를 참조하세요.

    a. **Windows Installer(\*msi 파일) 속성**에서 **사용자 환경** 탭을 선택합니다.

    b. **설치 동작**에 대해 **시스템용 설치**를 선택합니다.

    c. **로그온 요구 사항**에 대해 **사용자의 로그온 여부에 상관없이**를 선택합니다.

    d. **설치 프로그램 표시 여부**에 대해 **보통**을 선택합니다. 세 가지 옵션, 즉 **최소화**, **보통** 또는 **최대화** 중에서 선택할 수 있습니다.

    e. **사용자가 프로그램 설치를 사용하도록 허용** 상자를 선택합니다.

2.  **애플리케이션 설치** 단계를 사용하여 애플리케이션을 설치하는 작업 순서를 만들거나 편집합니다. 자세한 내용은 [System Center Configuration Manager의 작업 순서 단계](/sccm/osd/understand/task-sequence-steps)에서 [애플리케이션 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallApplication)를 참조하세요.

    a. Windows 및 Configuration Manager 설치 단계 후 이미징 작업 순서

    b. 사후 처리 그룹의 전체 업그레이드 작업 순서

3.  클라이언트에 작업 순서를 배포합니다.
4.  소프트웨어 센터에서 작업 순서를 설치합니다.

작업 순서를 진행하는 동안 애플리케이션 설치 인터페이스가 대상 최종 사용자 디바이스에 표시됩니다. 최종 사용자가 애플리케이션 설치 워크플로를 완료할 때까지 작업 순서 진행률이 일시 중지됩니다.

### <a name="install-using-the-wizard"></a>마법사를 사용하여 설치

앱을 배포할 때 마법사를 사용하여 다음 기능을 사용할 수도 있습니다.

1. 애플리케이션을 만들거나 편집합니다.
2. 애플리케이션을 클라이언트에 배포합니다.
3. 소프트웨어 센터에서 애플리케이션을 설치합니다. 애플리케이션 설치 인터페이스가 표시됩니다. 최종 사용자가 애플리케이션 설치 마법사에 따라 애플리케이션을 성공적으로 설치합니다.




<!-- When we have another H2 in this topic, Add this Next Steps section back in.  -->

## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
