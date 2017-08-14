---
title: "비즈니스용 Windows 스토어에서 앱 관리 | Microsoft 문서"
description: "System Center Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱을 관리 및 배포합니다."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8cdb22a6-72d7-41f5-9bed-c098b1bcf675
caps.latest.revision: 11
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: HT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: 369b6a82a20a90ca534f9484c0be71096dd35a30
ms.contentlocale: ko-kr
ms.lasthandoff: 07/29/2017

---

# <a name="manage-apps-from-the-windows-store-for-business-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 비즈니스용 Windows 스토어에서 앱 관리
[비즈니스용 Windows 스토어](https://www.microsoft.com/business-store)에서 조직을 위한 Windows 앱을 찾아서 개별적으로 또는 대량으로 구매할 수 있습니다. 스토어를 Configuration Manager에 연결하면 구매한 앱 목록을 Configuration Manager와 동기화할 수 있습니다. 동기화한 후에는 Configuration Manager 콘솔에서 앱 목록을 보고 다른 앱을 배포하는 것과 마찬가지로 배포할 수 있습니다.


## <a name="online-and-offline-apps"></a>온라인 및 오프라인 앱

비즈니스용 Windows 스토어에서는 다음 두 가지 유형의 앱을 지원합니다.

- **온라인** - 이 라이선스 유형에서는 사용자와 장치가 저장소에 연결하여 앱과 해당 라이선스를 가져와야 합니다. Windows 10 장치는 Azure Active Directory 도메인에 가입된 장치여야 합니다.
- **오프라인** - 저장소에 연결하거나 인터넷에 연결하지 않고도 앱과 라이선스를 캐시하여 온-프레미스 네트워크 내에 직접 배포할 수 있습니다.

비즈니스용 Windows 스토어에 대해 [자세히 알아보세요](https://technet.microsoft.com/itpro/windows/whats-new/windows-store-for-business-overview?f=255&MSPPError=-2147217396).

Configuration Manager에서는 Configuration Manager 클라이언트를 실행하는 Windows 10 장치 및 Microsoft Intune에 등록된 Windows 10 장치(하이브리드 구성이라고 함) 둘 다에서 비즈니스용 Windows 스토어 앱 관리를 지원합니다. Configuration Manager는 온라인 및 오프라인 앱에 대해 다음과 같은 기능을 제공합니다.

> [!IMPORTANT]
> 이 기능을 사용하려면 Windows 10 장치에서 2015년 11월(1511) 릴리스 이상을 실행해야 합니다.


|기능|오프라인 앱|온라인 앱|
|------------|------------|------------|
|Configuration Manager에 앱 데이터 동기화<br>(24시간마다 동기화 발생)|예|예|
|스토어 앱에서 Configuration Manager 응용 프로그램 만들기|예|예|
|스토어에서 무료 앱 지원|예|예|
|스토어에서 유료 앱 지원|아니요|예|
|사용자 또는 장치 컬렉션에 대한 필수 배포 지원|예|예|
|사용자 또는 장치 컬렉션에 대한 사용 가능한 배포 지원|예|예|
|스토어에서 LOB(기간 업무) 앱 지원|예|예|

Configuration Manager 클라이언트를 통해 사용이 허가된 온라인 앱을 Windows 10 PC에 배포하려면 PC에서 Windows 10 크리에이터 업데이트 이상을 실행하고 있어야 합니다.

## <a name="deploying-online-apps-using-the-windows-store-for-business-with-pcs-that-run-the-configuration-manager-client"></a>Configuration Manager 클라이언트를 실행하는 PC에서 비즈니스용 Windows 스토어를 사용하여 온라인 앱 배포
전체 Configuration Manager 클라이언트를 실행하는 PC에 비즈니스용 Windows 스토어 앱을 배포하기 전에 다음을 고려하세요.

- 전체 기능을 사용하려면 PC에서 Windows 10 크리에이터 업데이트 이상을 실행하고 있어야 합니다.
- PC는 Azure Active Directory 작업 영역에 가입되고 비즈니스용 Windows 스토어를 관리 도구로 등록한 동일한 AAD 테넌트에 있어야 합니다.
- PC가 기본 제공 관리자 계정으로 로그인되어 있으면 비즈니스용 Windows 스토어 앱에 액세스할 수 없습니다.
- PC는 비즈니스용 Windows 스토어에 인터넷으로 연결되어 있어야 합니다.

### <a name="notes-for-pcs-running-earlier-versions-of-windows-10"></a>Windows 10의 이전 버전을 실행하는 PC에 대한 노트
크리에이터 업데이트 이전의 Windows 10 버전을 실행하는 PC(Configuration Manager 클라이언트 포함)에는 다음 기능이 적용됩니다.


- 응용 프로그램을 설치하는 사용자에 의해 또는 필요한 배포에 대한 설치 기한이나 설치 후 재평가에 도달한 응용 프로그램에 의해 설치가 적용될 경우:
    - 비즈니스용 Windows 스토어 앱을 시작하여 응용 프로그램이 “적용”됩니다. 
    - 최종 사용자는 실제로 설치되기 전에 스토어에서 설치를 완료해야 합니다.
    - Configuration Manager 콘솔의 응용 프로그램 상태는 실패로 보고되고 “Windows 스토어 앱이 클라이언트 PC에서 열렸으며 사용자가 설치를 완료하기를 기다리고 있습니다.” 오류가 표시됩니다.
- 다음 응용 프로그램 평가 주기에서:
    - 사용자가 스토어에서 응용 프로그램을 설치한 경우 응용 프로그램에서는 상태 **성공**을 보고합니다. 
    - 최종 사용자가 스토어에서 앱을 설치하려고 시도하지 않은 경우:
        - 필수 배포가 스토어를 시작하고 응용 프로그램 설치를 다시 적용하려고 시도합니다.
        - 사용 가능한 배포는 다시 적용되지 않습니다.

#### <a name="further-notes-for-pcs-running-earlier-versions-of-windows-10"></a>Windows 10의 이전 버전을 실행하는 PC에 대한 추가 노트:

- 비즈니스용 Windows 스토어에서 LOB(기간 업무) 앱을 배포할 수 없습니다.
- 스토어에서 유료 앱을 배포할 경우 최종 사용자는 스토어에 로그인하고 직접 앱을 구매해야 합니다.
- Windows 스토어의 소비자 버전에 대한 액세스를 사용하지 않는 그룹 정책을 배포한 경우에는 비즈니스용 Windows 스토어가 사용되더라도 비즈니스용 Windows 스토어를 통한 배포가 작동하지 않습니다.


## <a name="set-up-windows-store-for-business-synchronization"></a>비즈니스용 Windows 스토어 동기화 설정

### <a name="for-configuration-manager-versions-prior-to-1706"></a>Configuration Manager 1706 이전 버전

**Azure Active Directory에서 Configuration Manager를 "웹 응용 프로그램 및/또는 웹 API" 관리 도구로 등록합니다. 이 작업으로 나중에 필요한 클라이언트 ID를 알 수 있습니다.**
1. [https://manage.windowsazure.com](https://manage.windowsazure.com)의 Active Directory 노드에서 Azure Active Directory를 선택한 후 **응용 프로그램** > **추가**를 클릭합니다.
2.  **조직에서 개발 중인 응용 프로그램 추가**를 클릭합니다.
3.  응용 프로그램의 이름을 입력하고, **웹 응용 프로그램** 및/또는 **웹 API**를 선택한 후 **다음** 화살표를 클릭합니다.
4.  **로그온 URL** 및 **앱 ID URI** 모두에 대해 동일한 URL을 입력합니다. URL은 어떤 문자열이든 될 수 있으며, 실제 주소로 확인할 필요는 없습니다. 예를 들어 *https://yourdomain/sccm*을 입력할 수 있습니다.
5.  마법사를 완료합니다.

**Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.**
1.  만든 응용 프로그램을 강조 표시하고 **구성**을 클릭합니다.
2.  **키** 아래의 목록에서 기간을 선택하고 **저장**을 클릭합니다. 이 작업은 새 클라이언트 키를 만듭니다. 비즈니스용 Windows 스토어를 Configuration Manager에 성공적으로 등록할 때까지 이 페이지에서 이동하지 마세요.

**비즈니스용 Windows 스토어에서 Configuration Manager를 저장소 관리 도구로 구성**
1.  [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools)를 열고 메시지가 표시되면 로그인합니다.
2.  필요한 경우 사용 약관에 동의합니다.
3.  **관리 도구**에서 **관리 도구 추가**를 클릭합니다.
4.  **이름별 도구 검색**에서 이전에 AAD에서 만든 응용 프로그램의 이름을 입력한 후 **추가**를 클릭합니다.
5.  가져온 응용 프로그램 옆에 있는 **활성화**를 클릭합니다.
6.  오프라인 사용이 허가된 앱을 구매할 수 있도록 허용하려면 **관리 > 계정 정보** 페이지에서 **오프라인 사용이 허가된 앱 표시**를 선택합니다.

**Configuration Manager에 스토어 계정 추가**

1. 비즈니스용 Windows 스토어에서 하나 이상의 앱을 구매했는지 확인 Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장한 후 **비즈니스용 Windows 스토어**를 클릭합니다.
2.  **홈** 탭의 **비즈니스용 Windows 스토어** 그룹에서 **비즈니스용 Windows 스토어 계정 추가**를 클릭합니다. 
3.  Azure Active Directory의 테넌트 ID, 클라이언트 ID 및 클라이언트 키를 추가한 후 마법사를 완료합니다.
4. 완료한 후에는 Configuration Manager 콘솔의 **비즈니스용 Windows 스토어** 목록에서 구성한 계정이 표시됩니다.

### <a name="for-configuration-manager-version-1706-and-later"></a>Configuration Manager 1706 이상 버전

1. 콘솔에서 **관리** > **개요** > **클라우드 서비스 관리** > **Azure** > **Azure 서비스**로 이동한 다음 **Azure 서비스 구성**을 선택하여 **Azure 서비스 마법사**를 시작합니다.
2. **Azure 서비스** 페이지에서 구성할 서비스를 선택하고 **다음**을 클릭합니다.
3. **일반** 페이지에서 Azure 서비스 이름에 이름을 입력하고 원하는 경우 선택적 설명을 입력한 후 **다음**을 클릭합니다.
4. **앱** 페이지에서 Azure 환경을 지정한 다음 **찾아보기**를 클릭하여 **서버 앱** 창을 엽니다.
5. **서버 앱** 창에서 사용할 서버 앱을 선택한 다음 **확인**을 클릭합니다. 서버 앱은 테넌트 ID, 클라이언트 ID 및 클라이언트의 비밀 키를 비롯한 Azure 계정에 대한 구성을 포함하는 Azure 웹앱입니다. 사용 가능한 서버 앱이 없는 경우 다음 중 하나를 사용합니다.
    - **만들기:** 새 서버 앱을 만들려면 **만들기**를 클릭합니다. 앱 및 테넌트의 이름을 입력합니다. 그런 다음 Azure에 로그인하면 Configuration Manager가 Azure에서 사용자를 위해 웹앱을 만듭니다(웹앱에 사용할 클라이언트 ID 및 비밀 키 포함). 나중에 Azure Portal에서 이러한 내용을 확인할 수 있습니다.
    - **가져오기:** Azure 구독에 이미 있는 웹앱을 사용하려면 **가져오기**를 클릭합니다. 앱 및 테넌트의 이름을 입력한 다음 테넌트 ID, 클라이언트 ID 및 Configuration Manager에서 사용하도록 할 Azure 웹앱의 비밀 키를 지정합니다. 정보를 **확인**한 후 **확인**을 클릭하여 계속합니다. 
6. **정보** 페이지를 검토하고 지시에 따라 추가 단계 및 구성을 완료합니다. 이러한 구성은 Configuration Manager를 통해 서비스를 사용하는 데 필요합니다. 예를 들어 비즈니스용 Windows 스토어를 구성하려면
    - Azure에서 Configuration Manager를 웹 응용 프로그램 또는 Web API로 등록하고 클라이언트 ID를 기록합니다. 관리 도구(Configuration Manager)에서 사용하도록 할 클라이언트 키도 지정합니다.
    - 비즈니스용 Windows 스토어 콘솔에서 Configuration Manager를 저장소 관리 도구로 구성하고 오프라인 사용이 허가된 앱에 대한 지원을 사용하도록 설정한 다음 하나 이상의 앱을 구매해야 합니다. 
7. 계속 진행할 준비가 되면 **다음**을 클릭합니다.
8. **앱 구성** 페이지에서 이 서비스에 대한 앱 카탈로그 및 언어 구성을 완료하고 **다음**을 클릭합니다.
9. 마법사가 완료된 후 Configuration Manager 콘솔에는 **비즈니스용 Windows 스토어**를 **클라우드 서비스 유형**으로 구성했음이 표시됩니다.




## <a name="create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-app"></a>비즈니스용 Windows 스토어 앱에서 Configuration Manager 응용 프로그램을 만들고 배포합니다.
1.  Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.
2.  배포하려는 앱을 선택한 후 **홈** 탭의 **만들기** 그룹에서 **응용 프로그램 만들기**를 클릭합니다.
비즈니스용 Windows 스토어 앱을 포함하여 Configuration Manager 응용 프로그램이 만들어집니다. 그런 다음 이 응용 프로그램을 원하는 Configuration Manager 응용 프로그램으로 배포 및 모니터링할 수 있습니다.

> [!IMPORTANT]
> Intune에 등록된 장치의 경우 원래 장치를 등록한 사용자만 배포된 앱을 사용할 수 있습니다. 다른 사용자는 앱에 액세스할 수 없습니다.

## <a name="next-steps"></a>다음 단계

**소프트웨어 라이브러리** 작업 영역에서 **응용 프로그램 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.

앱 이름, 플랫폼, 소유한 앱의 라이선스 수, 사용할 수 있는 라이선스 수 등을 포함하여 관리하는 각 스토어 앱에 대한 앱 정보를 볼 수 있습니다.

