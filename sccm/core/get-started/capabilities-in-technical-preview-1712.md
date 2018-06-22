---
title: Technical Preview 1712 | Microsoft Docs
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1712에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 12/15/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3ce372d6-bd93-4d4d-b612-5303f89c36f0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5ecaa025a9a9f0d85b7a2ef857e70c4d762fd1f5
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32338281"
---
# <a name="capabilities-in-technical-preview-1712-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1712의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1712에서 사용할 수 있는 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 

이 버전의 Technical Preview를 설치하기 전에 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 검토하세요. 해당 문서에서는 Technical Preview를 사용하기 위한 일반 요구 사항 및 제한 사항, 버전 간에 업데이트하는 방법 및 Technical Preview의 기능에 대한 피드백을 제공하는 방법에 대해 설명합니다.     


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
<!--sms489412-->


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

<!--  Section Template
##  FEATURE
<-- TFS ID - need to fix comment md here
### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="do-not-automatically-upgrade-superseded-applications"></a>교체된 응용 프로그램을 자동으로 업그레이드하지 않습니다
<!-- 1351266 -->
[사용자 음성 피드백](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/11532669-fix-supercedence-behavior)에 따라 이 릴리스에서 교체된 버전을 자동으로 업그레이드하지 않도록 응용 프로그램 배포를 구성하는 옵션이 있습니다. 이제 **소프트웨어 배포 마법사**의 **배포 설정** 페이지에서 배포를 만들 때 **사용 가능** 또는 **필수** 설치 목적으로 **이 응용 프로그램의 교체된 버전을 자동으로 업그레이드**하는 옵션을 활성화하거나 비활성화할 수 있습니다.


## <a name="install-multiple-applications-in-software-center"></a>소프트웨어 센터에서 여러 응용 프로그램 설치
<!-- 1357126 -->
이제 최종 사용자 또는 데스크톱 기술자가 장치에 여러 응용 프로그램을 설치해야 하는 경우 소프트웨어 센터는 선택한 여러 응용 프로그램을 설치하도록 지원합니다. 그러면 사용자가 다음 단계를 시작하기 전에 설치가 완료되기를 기다리지 않고 효율적으로 작업할 수 있습니다.

**응용 프로그램** 탭에서 다중 선택 모드를 사용하는 경우 다음 조건은 다중 선택에서 소프트웨어 센터가 사용하도록 설정할 앱을 결정합니다.
 - 앱이 사용자에게 표시됩니다.
 - 앱이 설치되어 있지 않습니다.
 - 관리자의 승인이 필요하지 않거나 이미 부여되었습니다.
 - 앱 상태가 제공됩니다(예: 콘텐츠를 아직 다운로드하지 않음).

### <a name="try-it-out"></a>기능 직접 사용해 보기
**Configuration Manager 콘솔에서:** 사용자 또는 장치에 사용할 수 있는 또는 필수로 설치할 여러 응용 프로그램을 배포합니다(나중에 최종 기한 지정됨). 관리자 승인이 필요하지 않습니다. 자세한 내용은 [응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications)를 참조하세요.

**소프트웨어 센터에서:**
 1. **응용 프로그램** 탭은 기본적으로 열려야 합니다. 
 2. 목록 보기에서 다중 선택 모드를 시작하려면 새 아이콘을 클릭합니다. ![오른쪽 위 모서리에 있는](media/software-center-multi-select-apps.png) 소프트웨어 센터 다중 선택 아이콘
 3. 목록에서 앱의 왼쪽에 있는 확인란을 클릭하여 설치할 두 개 이상의 앱을 선택합니다.
 4. **선택한 설치** 단추를 클릭합니다.

이제 연속적으로 앱이 정상적으로 설치됩니다.


## <a name="client-based-pxe-responder-service"></a>클라이언트 기반 PXE 응답자 서비스
<!-- 1357148 -->
고객에 대한 일반적인 문제는 서버 인프라가 거의 없거나 전혀 없이 원격으로/지점에서 PXE 서비스를 제공해야 한다는 점입니다. 배포 지점 역할은 클라이언트 운영 체제를 지원하지만 Windows 배포 서비스에 대한 종속성으로 인해 PXE를 사용할 수 없습니다.

새 클라이언트 설정을 사용하여 Configuration Manager 클라이언트에서 PXE 응답기 서비스를 활성합니다. PXE 사용 부팅 이미지는 PXE 응답자의 클라이언트 캐시에 있어야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
테스트 환경에서 이 클라이언트 PXE 응답자와 충돌할 수 있는 기존 PXE 사용 배포 지점 또는 다른 PXE 서버가 없는지 확인합니다.

Configuration Manager 콘솔에서:
 1. **운영 체제** 아래의 **소프트웨어 라이브러리** 작업 영역에서 **작업 시퀀스**: 사용자 지정 템플릿을 사용하여 작업 순서를 만듭니다.
    1. **추가**를 클릭하고 **일반**을 선택한 다음 **작업 순서 변수 설정** 단계를 선택합니다. **SMSTSPersistContent**를 작업 순서 변수로 입력하고 **TRUE** 값을 입력합니다.
    1. **추가**를 클릭하고 **소프트웨어**를 선택한 다음 **패키지 콘텐츠 다운로드** 단계를 선택합니다. 골드 별표를 클릭하고 PXE 사용 부팅 이미지를 선택합니다. x86 및 x64 부팅 이미지를 포함합니다. **Configuration Manager 클라이언트 캐시**에 배치하도록 단계를 구성합니다.
    1. **추가**를 클릭하고 **일반**을 선택한 다음 **작업 순서 변수 설정** 단계를 선택합니다. **SMSTSPreserveContent**를 작업 순서 변수로 입력하고 **TRUE** 값을 입력합니다.
 2. **클라이언트 설정** 아래의 **관리** 작업 영역에서: 사용자 지정 클라이언트 장치 설정 정책을 만듭니다.
    1. **클라이언트 캐시 설정** 그룹을 선택합니다.
  1. **콘텐츠를 공유하도록 정품 OS에서 Configuration Manager 클라이언트 사용** 설정을 **예**로 설정합니다.
    1. **PXE 응답자 서비스 사용** 설정을 **예**로 설정합니다.
  1. **자체 서명된 인증서 만들기 또는 PKI 클라이언트 인증서 가져오기** 설정에서 **인증서 제공**을 클릭합니다. 테스트 환경에 PKI가 없는 경우 **인증서 가져오기**를 선택하고, 그렇지 않으면 **확인**을 클릭하여 자체 서명된 인증서를 만듭니다. 
    1. 테스트 환경에 필요한 대로 나머지 설정을 구성합니다. (특정 네트워크 또는 보안 요구 사항이 없다면 기본 설정이 작동해야 합니다.)
 3. PXE 응답자인 대상 클라이언트의 컬렉션에 작업 순서 및 사용자 지정 클라이언트 설정을 배포합니다. 적용할 정책 및 실행할 작업 순서를 대기합니다.
 4. 일반적으로 PXE/네트워크 부팅에 대한 동일한 서브넷에서 다른 클라이언트를 시작합니다.

### <a name="known-issues"></a>알려진 문제
 - 부팅 이미지를 추가할 때 작업 순서 편집기가 **패키지 콘텐츠 다운로드** 단계에 대해 빨간색 오류 아이콘을 표시했지만 작업 순서는 성공적으로 저장되었습니다. 또한 편집기에서 이 작업 순서를 다시 열면 참조된 개체를 찾을 수 없다는 별다른 해가 없는 경고가 표시됩니다. <!-- sms427542 -->
 - 패키지 콘텐츠 다운로드 단계의 부팅 이미지는 사용자 지정 작업 순서의 참조 목록에 표시되지 않습니다. 또한 **콘텐츠 배포** 작업을 사용할 수 없습니다. <!-- sms504017 -->


## <a name="change-in-the-configuration-manager-client-install"></a>Configuration Manager 클라이언트 설치 변경  
사용자 음성 피드백의 결과로 [Silverlight는 더 이상 클라이언트에 자동으로 설치되지 않습니다.](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/10886427-please-do-not-install-silverlight-by-default-in-v) <!--1356195-->
  

## <a name="change-to-the-surface-device-dashboard"></a>Surface 장치 대시보드 변경
이제 Surface 대시보드는 운영 체제 버전이 아닌 Surface 장치에 대한 펌웨어 버전을 표시합니다. 콘솔에서 **Surface 장치**  > **모니터링**으로 이동합니다. 다음 항목을 볼 수 있습니다.
- Surfaces의 백분율
- Surface 모델의 백분율
- 상위 5개 펌웨어 버전
 <!--1355788-->


## <a name="improvements-to-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드에 대한 향상된 기능 
이제 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에서는 관련 장치의 목록을 표시합니다. 콘솔에서 **소프트웨어 라이브러리** >**개요** >**Office 365 클라이언트 관리**로 이동합니다. 대시보드는 오른쪽에 표시됩니다. 차트에서 조건을 선택하면 장치 목록이 표시됩니다.  
<!--1357281-->


## <a name="improvements-to-the-configuration-manager-console"></a>Configuration Manager 콘솔에 대한 향상된 기능 
사용자 의견 피드백을 반영하여 Configuration Manager 콘솔이 다음과 같이 향상되었습니다.

- [기본 사용자를 표시하는 장치 목록](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8782225-enable-a-column-for-primary-user): 자산 및 호환성, 장치 아래의 장치 목록은 이제 기본적으로 기본 사용자를 표시합니다. 마지막으로 로그온한 사용자는 선택적 열로 추가될 수도 있습니다. <!-- 1357280 -->
- [이름을 바꾼 컬렉션이 기존 컬렉션 멤버 관리 규칙에 표시됨](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/20125567-fix-the-renaming-of-collections): 컬렉션이 다른 컬렉션의 멤버이며 이름이 바뀐 경우 새 이름은 멤버 관리 규칙 하에서 업데이트됩니다.<!--1357282--> 


## <a name="improvements-to-operating-system-deployment"></a>운영 체제 배포 향상
사용자 의견 피드백을 일부 반영하여 운영 체제 배포가 다음과 같이 향상되었습니다.
 - [부팅 이미지의 기본 로그 뷰어](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/19269823-stop-cmtrace-from-asking-us-if-we-want-to-use-it-a): cmtrace.exe를 시작할 때 Windows PE에서 이 프로그램을 로그 파일에 대한 기본 뷰어로 만들지를 선택하는 메시지가 더 이상 표시되지 않습니다. <!-- SMS 500897 -->
 - 패키지 콘텐츠 다운로드 단계: 이제 이 작업 순서 단계에 부팅 이미지를 추가할 수 있습니다.


## <a name="windows-10-feedback-hub-app-integration"></a>Windows 10 피드백 허브 앱 통합

Windows 10에 기본 제공되는 [피드백 허브 앱](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)을 통해 피드백을 활성화할 정도로 피드백을 선호합니다. **새 피드백을 추가**할 때 **엔터프라이즈 관리** 범주를 선택하고 다음과 같은 하위 범주가 중 하나를 선택해야 합니다.
 - Configuration Manager 클라이언트
 - Configuration Manager 콘솔
 - Configuration Manager OS 배포
 - Configuration Manager 서버

[사용자 의견 페이지](http://configurationmanager.uservoice.com/)를 계속 사용하려면 Configuration Manager에서 새로운 기능 아이디어에 투표하세요.


<!-- When we have another H2 in this topic, Add this Next Steps section back in.  -->

## <a name="next-steps"></a>다음 단계
Technical Preview 분기를 설치하거나 업데이트하는 방법에 대한 정보는 [System Center Configuration Manager용 Technical Preview](/sccm/core/get-started/technical-preview)를 참조하세요.    
