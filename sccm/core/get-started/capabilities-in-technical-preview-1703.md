---
title: 기술 미리 보기 1703의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1703에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 2e801f8c-d331-41ee-8f27-908448fc0951
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 26933c878a7a57b40ade404b8ef205c18a01f7f6
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70378004"
---
# <a name="capabilities-in-technical-preview-1703-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1703의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1703에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>디바이스 컬렉션에 대량 구매한 iOS 앱 배포

이제 사용이 허가된 앱을 사용자 및 디바이스에 배포할 수 있습니다. 디바이스 라이선싱을 지원하는 앱 기능에 따라 앱 배포 시 다음과 같이 적절한 라이선스가 청구됩니다.

|||||
|-|-|-|-|
|Configuration Manager 버전|앱이 디바이스 라이선싱을 지원하나요?|배포 컬렉션 유형|청구된 라이선스|
|1702 이전|예|사용자|사용자 라이선스|
|1702 이전|아니요|사용자|사용자 라이선스|
|1702 이전|예|디바이스|사용자 라이선스|
|1702 이전|아니요|디바이스|사용자 라이선스|
|1702 이상|예|사용자|사용자 라이선스|
|1702 이상|아니요|사용자|사용자 라이선스|
|1702 이상|예|디바이스|디바이스 라이선스|
|1702 이상|아니요|디바이스|사용자 라이선스|

대량 구매한 iOS 앱에 대한 자세한 내용은 [대량 구매한 iOS 앱 관리](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)를 참조하세요.

## <a name="direct-links-to-applications-in-software-center"></a>소프트웨어 센터의 애플리케이션에 대한 직접 링크

이제 최종 사용자에게 소프트웨어 센터의 애플리케이션에 대한 직접 링크를 제공할 수 있습니다. 즉, 더 이상 애플리케이션을 설치하기 위해 소프트웨어 센터를 열고 애플리케이션을 검색할 필요가 없습니다. 단, 이러한 직접 링크는 Configuration Manager 애플리케이션에 사용할 수 있으며 패키지 및 프로그램 또는 작업 순서에는 사용할 수 없습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기                 

다음 URL 형식을 사용하여 특정 애플리케이션에 대한 소프트웨어 센터를 엽니다.

**Softwarecenter:SoftwareId=_애플리케이션 식별자_**

### <a name="how-to-get-the-application-identifier-of-an-application"></a>애플리케이션의 애플리케이션 식별자를 가져오는 방법

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리**를 클릭합니다.
2. 소프트웨어 라이브러리 작업 영역에서 **애플리케이션 관리**를 확장한 다음 **애플리케이션**을 클릭합니다.
3. **애플리케이션** 보기에서 열 머리글 중 하나를 마우스 오른쪽 단추로 클릭한 다음 목록에서 **CI 고유 ID**를 선택합니다. 이제 목록에 각 애플리케이션의 고유 ID가 표시됩니다.
4. 링크를 제공하려는 애플리케이션의 **CI 고유 ID**(예: **ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f/2**)를 참조합니다.
5. 그런 다음 애플리케이션 GUID 뒤에 있는 모든 텍스트를 제거합니다(이 경우 **/2**). 그러면 애플리케이션 식별자가 남습니다.
6. 마지막으로 링크 구성을 마치려면 링크 앞에 **Softwarecenter:SoftwareID=** 을 붙입니다. 위의 예제를 사용한 최종 링크는 다음과 같습니다. **Softwarecenter:SoftwareId= ScopeId_1672B0CD-912A-4613-9BAB-D4EF2696D416/Application_970b1fef-1f38-405c-ad37-c753400b895f**.

이 링크를 사용하여 최종 사용자는 지정된 애플리케이션에 대한 소프트웨어 센터를 직접 열 수 있습니다.


## <a name="pfx-certificates-for-configuration-manager-windows-client-computers"></a>Configuration Manager Windows 클라이언트 컴퓨터에 대한 PFX 인증서

이제 Windows 10을 실행하는 Configuration Manager 클라이언트 컴퓨터로 가져온 PFX 인증서 프로필을 배포할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

[PFX 인증서 프로필을 만드는 방법](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)의 지침을 사용하여 PFX 프로필을 가져오고 프로필을 배포한 다음 대상 사용자에 대해 인증서가 설치되었는지 확인합니다.



## <a name="configure-azure-services-wizard"></a>Azure 서비스 구성 마법사
Technical Preview 1703에는 **Azure 서비스 구성** 마법사가 도입되었습니다. 이 마법사는 Configuration Manager에서 사용하는 클라우드 서비스를 설정하기 위한 개별 워크플로를 대체하는 공통 구성 환경을 제공합니다. 이 작업은 **Azure 웹앱**을 사용하여 구독 및 구성 세부 정보를 제공함으로써 수행합니다. Azure 웹앱을 사용하지 않을 경우, Azure에서 새 Configuration Manager 구성 요소 또는 서비스를 설정할 때마다 이러한 세부 정보를 입력해야 합니다.

Technical Preview 1703에서는 WSfB(비즈니스용 Windows 스토어)만 이 마법사를 사용하여 구성됩니다.  다른 클라우드 서비스는 별도의 워크플로를 사용하여 구성됩니다.

- 이 Preview 항목의 정보를 사용하여 현재 분기 항목 [System Center Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱 관리](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)의 [비즈니스용 Windows 스토어 동기화 설정](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#bkmk_setup) 섹션에 있는 구성 단계를 바꿉니다.

- 웹앱에 대한 자세한 내용은 [Azure App Service의 인증 및 권한 부여](https://docs.microsoft.com/azure/app-service/app-service-authentication-overview) 및 [Web Apps 개요](https://docs.microsoft.com/azure/app-service-web/app-service-web-overview)를 참조하세요.

### <a name="prerequisites-and-planning"></a>필수 조건 및 계획
Configuration Manager와 비즈니스용 Windows 스토어 간의 연결을 설정하는 경우 스토어에서 동기화된 앱 콘텐츠를 보관할 폴더를 제공해야 합니다. 이 폴더가 안전하고 해당 콘텐츠를 디바이스에 배포할 수 있도록 다음 사용 권한을 지정해야 합니다.
- 서비스 연결 지점 사이트 시스템 역할(계층 구조의 최상위 사이트)를 설치하는 컴퓨터에는 **Computer$** 계정을 사용할 때 지정한 폴더에 대한 읽기 및 쓰기 권한이 있어야 합니다.  

- 앱 작성자에게 지정한 폴더에 대한 읽기 권한이 있어야 합니다.  

- SMS 공급자 인스턴스를 호스트하는 각 컴퓨터의 **Computer$** 계정이 지정한 폴더를 사용할 수 있어야 합니다.

Azure Active Directory에서 Configuration Manager를 웹 애플리케이션 또는 Web API 관리 도구로 등록합니다. 그러면 나중에 필요한 클라이언트 ID가 만들어집니다.

### <a name="use-the-wizard-to-configure-the-wsfb-cloud-service"></a>마법사를 사용하여 WSfB 클라우드 서비스 구성

1. 콘솔에서 **관리** > **개요** > **클라우드 서비스 관리** > **Azure** > **Azure 서비스**로 이동한 다음 **Azure 서비스 구성**을 선택하여 **Azure 서비스 마법사**를 시작합니다.

2. **Azure 서비스** 페이지에서 구성할 서비스를 선택하고 **다음**을 클릭합니다. 이 Preview에서는 WSfB만 구성할 수 있습니다.

3. **일반** 페이지에서 **Azure 서비스 이름**에 이름을 입력하고 원하는 경우 선택적 설명을 입력한 후 **다음**을 클릭합니다.

4. **앱** 페이지에서 Azure 환경을 지정한 다음 **찾아보기**를 클릭하여 서버 앱 창을 엽니다.

5. **서버 앱** 창에서 사용할 서버 앱을 선택한 다음 **확인**을 클릭합니다.
   서버 앱은 테넌트 ID, 클라이언트 ID 및 클라이언트의 비밀 키를 비롯한 Azure 계정에 대한 구성을 포함하는 Azure 웹앱입니다. 사용 가능한 서버 앱이 없는 경우 다음 중 하나를 사용합니다.
   - **만들기**: 새 서버 앱을 만들려면 **만들기**를 클릭합니다. 앱 및 테넌트의 이름을 입력합니다. 그런 다음 Azure에 로그인하면 Configuration Manager가 Azure에서 사용자를 위해 웹앱을 만듭니다(웹앱에 사용할 클라이언트 ID 및 비밀 키 포함). 나중에 Azure Portal에서 이러한 내용을 확인할 수 있습니다.
   - **가져오기**: Azure 구독에 이미 있는 웹앱을 사용하려면 **가져오기**를 클릭합니다. 앱 및 테넌트의 이름을 입력한 다음 테넌트 ID, 클라이언트 ID 및 Configuration Manager에서 사용하도록 할 Azure 웹앱의 비밀 키를 지정합니다. 정보를 **확인**한 후 **확인**을 클릭하여 계속합니다.  </br></br>

6. **정보** 페이지를 검토하고 지시에 따라 추가 단계 및 구성을 완료합니다. 이러한 구성은 Configuration Manager를 통해 서비스를 사용하는 데 필요합니다.
   예를 들어 WSfB를 구성하려면:

   1. Azure에서 Configuration Manager를 웹 애플리케이션 또는 Web API로 등록하고 클라이언트 ID를 기록합니다. 관리 도구(Configuration Manager)에서 사용하도록 할 클라이언트 키도 지정합니다.

   2.    WSfB 콘솔에서 Configuration Manager를 저장소 관리 도구로 구성하고 오프라인 사용이 허가된 앱에 대한 지원을 사용하도록 설정한 다음 하나 이상의 앱을 구매해야 합니다.   </br>

   계속 진행할 준비가 되면 **다음**을 클릭합니다.

7. **앱 구성** 페이지에서 이 서비스에 대한 앱 카탈로그 및 언어 구성을 완료하고 **다음**을 클릭합니다.
8. 마법사가 완료된 후 Configuration Manager 콘솔에는 **비즈니스용 Windows 스토어**를 **클라우드 서비스 유형**으로 구성했음이 표시됩니다.

이제 [현재 분기 콘텐츠](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)의 나머지 부분을 사용하여 WSfB에서 동기화할 앱을 관리하고, 비즈니스용 Windows 스토어 앱을 만들고 배포하고 모니터링할 수 있습니다.

### <a name="modify-a-cloud-service-configuration"></a>클라우드 서비스 구성 수정
클라우드 서비스의 속성을 보고 편집하여 구성을 수정할 수 있습니다.

콘솔에서 **관리** > **개요** > **클라우드 서비스 관리** > **Azure** > **Azure 서비스**로 이동한 다음 **Azure 서비스 구성**을 선택하고 클라우드 서비스를 선택한 다음 **속성**을 선택합니다.

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환
Windows 10 크리에이터 업데이트에서는 UEFI 사용 하드웨어에 맞게 하드 디스크를 다시 분할하는 프로세스를 자동화하는 간단한 변환 도구를 소개하고 Windows 7에서 Windows 10으로의 현재 위치 업그레이드 프로세스에 변환 도구를 통합합니다. 펌웨어를 BIOS에서 UEFI로 변환하는 OEM 도구 및 운영 체제 업그레이드 작업 순서와 이 도구를 결합하면 Windows 10 크리에이터 업데이트로의 현재 위치 업그레이드 중에 BIOS에서 UEFI로 컴퓨터를 변환할 수 있습니다. 자세한 내용은 [BIOS-UEFI 변환을 관리하는 작업 순서 단계](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)를 참조하세요.

## <a name="collapsible-task-sequence-groups"></a>축소 가능한 작업 순서 그룹
이 버전에는 작업 순서 그룹을 확장하고 축소하는 기능이 도입되었습니다. 개별 그룹을 확장 또는 축소하거나, 모든 그룹을 한 번에 확장 또는 축소할 수 있습니다.


## <a name="client-settings-to-configure-windows-analytics-for-upgrade-readiness"></a>업그레이드 준비를 위해 Windows Analytics를 구성하기 위한 클라이언트 설정
이 버전부터 디바이스 클라이언트 설정을 사용하여 Configuration Manager에서 [업그레이드 준비](/sccm/core/clients/manage/upgrade/upgrade-analytics)와 같은 [Windows Analytics](https://www.microsoft.com/WindowsForBusiness/windows-analytics) 솔루션을 사용하는 데 필요한 Windows 원격 분석의 구성을 간소화할 수 있습니다. Configuration Manager는 클라이언트 컴퓨터에서 보고한 Windows 원격 분석 데이터를 기준으로 사용자 환경의 현재 상태에 대한 귀중한 정보를 제공할 수 있는 데이터를 Windows Analytics에서 검색할 수 있습니다. 클라이언트 컴퓨터에서 Windows 원격 분석 서비스에 Windows 원격 분석 데이터를 보고하면 관련 데이터가 조직의 OMS 작업 영역 중 하나에서 호스트되는 Windows Analytics 솔루션으로 전송됩니다. 업그레이드 준비는 관리되는 디바이스의 Windows 업그레이드에 대한 결정 우선 순위를 지정하는 데 도움이 될 수 있는 Windows Analytics 솔루션입니다.

Windows 원격 분석 설정에 대한 자세한 내용은 [조직에서 Windows 원격 분석 구성](https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization)을 참조하세요.

### <a name="prerequisites"></a>필수 구성 요소
- 업그레이드 준비 클라우드 서비스를 사용하도록 사이트를 구성해야 합니다. 자세한 내용은 [업그레이드 준비](/sccm/core/clients/manage/upgrade/upgrade-analytics)를 참조하세요.

### <a name="configure-windows-analytics-client-settings"></a>Windows Analytics 클라이언트 설정 구성
Windows Analytics를 구성하려면 Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동하고 **사용자 지정 디바이스 클라이언트 설정 만들기**를 두 번 클릭한 다음 **Windows Analytics**를 클릭합니다.  

**Windows Analytics** 설정 탭으로 이동한 후 다음을 구성합니다.
- **상업용 ID**  
상업용 ID 키는 관리하는 디바이스의 정보를 조직의 Windows Analytics 데이터를 호스트하는 OMS 작업 영역으로 매핑합니다. 업그레이드 준비에 사용하기 위한 상업용 ID 키를 이미 구성한 경우 해당 ID를 사용합니다. 아직 상업용 ID 키가 없는 경우 [상업용 ID 키 생성]( https://technet.microsoft.com /itpro/windows/deploy/upgrade-readiness-get-started#generate-your-commercial-id-key)을 참조하세요.

- **Windows 10 디바이스에 대한 원격 분석 수준**  설정  
각 Windows 10 원격 분석 수준에서 수집되는 항목에 대한 자세한 내용은 Windows 온라인 설명서의 [조직에서 Windows 원격 분석 구성]( https://technet.microsoft.com/itpro/windows/manage/configure-windows-telemetry-in-your-organization#telemetry-levels)을 참조하세요.

- **Windows 7, 8 및 8.1 디바이스에서 상용 데이터 수집에 옵트인**  선택  
옵트인할 경우 이러한 운영 체제에서 수집되는 데이터에 대한 자세한 내용을 보려면 Microsoft에서 [Windows 7, Windows 8, and Windows 8.1 appraiser telemetry events and fields](https://go.microsoft.com/fwlink/?LinkID=822965)(Windows 7, Windows 8 및 Windows 8.1 appraiser 원격 분석 이벤트 및 필드) pdf 파일을 다운로드하세요.

- **Internet Explorer 데이터 수집 구성** Windows 8.1 또는 이전 버전을 실행하는 디바이스에서 Internet Explorer 데이터 수집을 수행하면 업그레이드 준비 기능을 통해 Windows 10으로의 원활한 업그레이드에 방해가 될 수 있는 웹앱 비호환성 문제를 감지할 수 있습니다. Internet Explorer 데이터 수집은 인터넷 영역별로 사용 가능하게 설정할 수 있습니다. 인터넷 영역에 대한 자세한 내용은 [URL 보안 영역 정보](https://msdn.microsoft.com/library/ms537183(v=vs.85).aspx)를 참조하세요.
