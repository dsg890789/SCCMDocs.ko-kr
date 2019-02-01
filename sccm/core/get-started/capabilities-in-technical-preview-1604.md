---
title: 기술 미리 보기 1604의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1604에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 684a5559-9e6e-469b-86ae-e768e9f0c9ac
author: aczechowski
ROBOTS: NOINDEX
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 9aecb8f744185116b85232bd9b2893cdf20a3b6d
ms.sourcegitcommit: ef3fdf21180e43afd7af6c8264524711435e426e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54897545"
---
# <a name="capabilities-in-technical-preview-1604-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1604의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1604에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.  

 다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.  

##  <a name="BKMK_WindowsVPP"></a> 비즈니스용 Windows 스토어에서 대량 구매 앱 관리  
 [비즈니스용 Windows 스토어](https://www.microsoft.com/en-us/business-store)에서 조직을 위한 앱을 찾아서 개별적으로 또는 대량으로 구매할 수 있습니다. 예를 들어 스토어를 Configuration Manager에 연결하여 Configuration Manager 콘솔에서 대량 구매 앱을 관리할 수 있습니다.  

-   구매한 앱 목록을 Configuration Manager와 동기화할 수 있습니다.  

-   동기화되는 앱은 Configuration Manager 콘솔에 표시되며 다른 앱과 유사하게 해당 앱을 배포할 수 있습니다.  

-   사용 가능한 라이선스 수와 Configuration Manager 콘솔에 사용되는 라이선스 수를 추적할 수 있습니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  

##### <a name="scenario-1-set-up-windows-store-for-business-synchronization"></a>시나리오 1: 비즈니스용 Windows 스토어 동기화 설정  

1.  Azure Active Directory에서 Configuration Manager를 "웹 애플리케이션 및/또는 웹 API" 관리 도구로 등록합니다. 이렇게 하면 나중에 필요한 클라이언트 ID가 제공됩니다.  

    1.  [https://manage.windowsazure.com](https://manage.windowsazure.com)의 **Active Directory** 노드에서 Azure Active Directory를 선택한 다음, **응용 프로그램** > **추가**를 클릭합니다.  

    2.  **조직에서 개발 중인 애플리케이션 추가**를 클릭합니다.  

    3.  애플리케이션의 이름을 입력하고, **웹 애플리케이션** 및/또는 **웹 API**를 선택한 후 다음 화살표를 클릭합니다.  

    4.  **로그온 URL** 및 **앱 ID URI** 모두에 대해 동일한 URL을 입력합니다.  URL은 어떤 문자열이든 될 수 있으며, 실제 주소로 확인할 필요는 없습니다. 예를 들어 **https://&lt;yourdomain\>/sccm**을 입력할 수 있습니다.  

    5.  마법사를 완료합니다.  

2.  Azure Active Directory에서 등록된 관리 도구에 대한 클라이언트 키를 만듭니다.  

    1.  방금 만든 애플리케이션을 강조 표시하고 **구성**을 클릭합니다.  

    2.  **키** 아래의 목록에서 기간을 선택하고 **저장**을 클릭합니다.  그러면 새 클라이언트 키가 생성됩니다.  비즈니스용 Windows 스토어를 Configuration Manager에 성공적으로 등록할 때까지 이 페이지에서 이동하지 마세요.  

3.  비즈니스용 Windows 스토어에서 Configuration Manager를 저장소 관리 도구로 구성합니다.  

    1.  [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/en-us/managementtools)를 열고 메시지가 표시되면 로그인합니다.  

    2.  필요한 경우 사용 약관에 동의합니다.  

    3.  **관리 도구**에서 **관리 도구 추가**를 클릭합니다.  

    4.  **이름별 도구 검색**에서 이전에 AAD에서 만든 애플리케이션의 이름을 입력한 후 **추가**를 클릭합니다.  

    5.  방금 가져온 애플리케이션 옆에 있는 **활성화**를 클릭합니다.  

    6.  **오프라인 라이선스 앱 표시** 마법사에서, 오프라인 라이선스 애플리케이션을 구매할 수 있도록 허용하려면 **예**를 클릭합니다.  

4.  비즈니스용 Windows 스토어에서 앱을 하나 이상 구매합니다.  

5.  Configuration Manager 콘솔의 **관리** 작업 영역에서 **Cloud Services**를 확장한 후 **비즈니스용 Windows 스토어**를 클릭합니다.  

6.  **홈** 탭의 **만들기** 그룹에서 **비즈니스용 Windows 스토어 계정 추가**를 클릭합니다.  

7.  Azure Active Directory의 테넌트 ID, 클라이언트 ID 및 클라이언트 키를 추가한 후 마법사를 완료합니다.  

8.  완료한 후에는 Configuration Manager 콘솔의 **비즈니스용 Windows 스토어 계정** 목록에서 구성한 계정이 표시됩니다.  

##### <a name="scenario-2-create-and-deploy-a-configuration-manager-application-from-a-windows-store-for-business-offline-licensed-app"></a>시나리오 2: 비즈니스용 Windows 스토어 사용이 허가된 오프라인 앱에서 Configuration Manager 애플리케이션의 생성 및 배포  

1.  Configuration Manager 콘솔의 **소프트웨어 라이브러리** 작업 영역에서 **애플리케이션 관리**를 확장한 다음 **스토어 앱에 대한 라이선스 정보**를 클릭합니다.  

2.  **구매한 비즈니스용 Windows 스토어 앱** 목록에서 스토어에서 동기화된 앱 목록을 볼 수 있습니다. 배포하려는 앱을 선택한 후 **홈** 탭의 **만들기** 그룹에서 **애플리케이션 만들기**를 클릭합니다.  

3.  비즈니스용 Windows 스토어 앱을 포함하여 Configuration Manager 애플리케이션이 만들어집니다. 그런 다음 이 애플리케이션을 원하는 Configuration Manager 애플리케이션으로 배포 및 모니터링할 수 있습니다.  

##  <a name="BKMK_PFW"></a> Microsoft Passport for Work 관리의 개선 사항  
 이제 Configuration Manager 클라이언트에서 관리되는 도메인에 가입된 Windows 10 디바이스에 Passport for Work 정책을 배포할 수 있습니다.  

##  <a name="bkmk_switchsup"></a> 클라이언트에서 새 소프트웨어 업데이트 지점으로 전환하는 옵션  
 1604 Technical Preview에서, 활성 소프트웨어 업데이트 지점에 문제가 있는 경우 Configuration Manager 클라이언트가 새로운 소프트웨어 업데이트 지점으로 전환하는 옵션을 사용할 수 있습니다. 이 옵션의 경우 기본 사이트에서 여러 소프트웨어 업데이트 지점을 사용할 수 있어야 합니다. 디바이스 컬렉션에서 이 옵션을 사용하도록 설정합니다. 옵션을 사용하면 클라이언트가 활성 소프트웨어 업데이트 지점에 연결하지 못할 경우 컬렉션의 클라이언트에서 다음 검색에서 다른 소프트웨어 업데이트 지점을 찾습니다. 새 소프트웨어 업데이트 지점으로 전환하면 WSUS 구성 설정(업데이트 분류, 제품 등)에 따라 추가 네트워크 트래픽이 발생합니다. 따라서 필요한 경우에만 이 옵션을 사용해야 합니다.  

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>소프트웨어 업데이트 지점을 전환하는 옵션을 활성화하려면  

1.  Configuration Manager 콘솔에서 **자산 및 호환성 &gt; 개요 &gt; 디바이스 컬렉션**으로 이동합니다.  

2.  **홈** 탭의 **컬렉션** 그룹에서, **클라이언트 알림**을 클릭하고 **다음 소프트웨어 업데이트 지점으로 전환**을 클릭합니다.  

> [!NOTE]  
>  이 옵션은 여러 소프트웨어 업데이트 지점이 있는 사이트에만 사용할 수 있습니다.  

##  <a name="bkmk_peercache"></a> 클라이언트 캐시 설정 및 클라이언트 피어 캐시를 관리하는 클라이언트 설정  
 Technical Preview 버전 1604에서는 클라이언트의 캐시 사용에 영향을 주는 두 개의 새로운 디바이스 클라이언트 설정을 제공합니다. 둘 다 개별적으로 사용할 수 있지만 클라이언트 설정에 대한 동일한 속성 시트에 구성되며, 함께 사용하면 원격 위치에서 클라이언트에 콘텐츠 배포를 관리할 수 있습니다.  

-   첫 번째는 클라이언트가 로컬 캐시의 콘텐츠를 다른 클라이언트와 직접 공유하도록 기본 제공된 Configuration Manager 솔루션인 **피어 캐시 클라이언트**입니다. 콘텐츠를 공유하는 피어 캐시 클라이언트의 경우 해당 클라이언트가 동일한 경계 그룹의 구성원이어야 합니다. 피어 캐시가 BranchCache와 같은 다른 솔루션의 사용을 대체하지는 않지만 나란히 작동하면 배포 지점과 같은 기존 콘텐츠 배포 솔루션을 확장할 수 있는 더 많은 옵션을 제공할 수 있습니다.  

     컬렉션에 대한 피어 캐시를 사용하는 클라이언트 설정을 배포한 후 해당 컬렉션의 멤버가 해당 경계 그룹에서 다른 클라이언트의 피어 콘텐츠 원본 역할을 할 수 있습니다.  피어 콘텐츠 원본으로 작동하는 클라이언트는 해당 관리 지점에 캐시되어 있고 사용할 수 있는 콘텐츠의 목록을 제출합니다. 그런 다음 해당 경계 그룹의 다음 클라이언트가 해당 콘텐츠를 요청하는 경우 피어 캐시 원본이 빠르도록 구성된 모든 배포 지점과 함께 잠재적 콘텐츠 원본으로 제공됩니다. 클라이언트는 결합된 콘텐츠 원본 풀에서 임의의 콘텐츠 원본을 선택합니다. 빠른 배포 지점 또는 피어 캐시 원본이 경계 그룹에 없는 경우 클라이언트는 느리도록 구성된 배포 지점에서만 콘텐츠를 검색합니다.  

-   두 번째 새로운 설정을 사용하면 클라이언트에 있는 **캐시의 크기를 관리**할 수 있습니다. 캐시는 메가바이트 단위로 그리고 드라이브 공간의 백분율로 최대 크기를 갖도록 설정할 수 있습니다.  클라이언트는 먼저 도달하는 설정을 적용합니다.  

클라이언트 피어 캐시 사용을 이해하기 위해 **클라이언트 데이터 원본** 대시보드를 볼 수 있습니다. 콘솔에서 **모니터링 > 클라이언트 상태 > 클라이언트 데이터 원본**으로 이동합니다. 여기서 대시보드에 적용하는 기간을 선택할 수 있습니다. 그런 다음 디스플레이에서, 정보를 보려는 경계 그룹 또는 패키지를 선택할 수 있습니다. 정보를 볼 때 서로 다른 콘텐츠 또는 정책 원본에 대한 자세한 내용을 보려면 화면 위로 마우스를 가져가면 됩니다.  

 새 보고서 **클라이언트 데이터 원본 - 요약**을 사용하면 각 경계 그룹에 대한 클라이언트 데이터 원본의 요약을 볼 수 있습니다.   
**피어 캐시를 사용하기 위한 요구 사항:**  

-   각 클라이언트의 캐시 폴더에 대해 **모든 권한**을 가진 **네트워크 액세스 계정**으로 사이트를 구성해야 합니다. 기본적으로 캐시 폴더는 **%windir%\ccmcache**입니다.  

-   클라이언트가 같은 경계 그룹의 멤버인 경우에만 피어 캐시를 사용하여 콘텐츠를 전송할 수 있습니다.  

#### <a name="to-configure-client-peer-cache-client-settings"></a>클라이언트 피어 캐시 클라이언트 설정을 구성하려면  

1.  두 설정 모두 동일한 클라이언트 설정 페이지에서 구성합니다. Configuration Manager 콘솔에서 **관리 &gt; 클라이언트 설정**으로 이동한 다음 사용할 디바이스 클라이언트 설정 개체를 엽니다. 기본 클라이언트 설정 개체를 수정할 수도 있습니다.  

2.  사용 가능한 설정 목록에서 **클라이언트 캐시 설정**을 선택합니다.  

3.  캐시의 크기를 관리하려면 **클라이언트 캐시 크기 구성**을 **예**로 설정합니다. 그러면 최대 캐시 크기를 메가바이트 단위 및 클라이언트 드라이브 공간의 백분율로 구성할 수 있습니다.  

4.  클라이언트가 클라이언트 피어 캐시에 참여할 수 있도록 하려면 **콘텐츠를 공유하도록 정품 OS에서 Configuration Manager 클라이언트 사용**을 **예**로 설정합니다. 그러면 HTTP 또는 HTTPS인지를 비롯하여 클라이언트에서 사용하는 포트를 구성할 수 있습니다.  

### <a name="try-it-out"></a>기능 직접 사용해 보기  
 다음 작업을 완료한 후에 이 항목 위쪽의 사용자 의견 정보를 사용하여 기능 작동 상태에 대한 정보를 보내 주세요.  

1.  클라이언트 설정을 수정하여 클라이언트 캐시의 새로운 크기를 지정한 다음 클라이언트에서 이 설정을 확인합니다.  

2.  클라이언트 설정을 사용하여 여러 클라이언트를 피어 캐시를 사용하도록 구성  

3.  피어 캐시를 사용하여 다른 클라이언트에서 콘텐츠를 얻을 수 있도록 일부 또는 대부분의 클라이언트에 콘텐츠를 배포합니다.  새로운 대시보드를 보는 데 사용되는 콘텐츠 원본을 확인할 수 있습니다.  

    > [!NOTE]  
    >  기술 미리 보기 및 단일 배포 지점으로 이 작업을 완료하려면 모든 클라이언트의 네트워크 위치에 대해 배포 지점을 느린 속도로 구성합니다. 이제 단일 클라이언트에 콘텐츠를 배포합니다.  해당 클라이언트가 콘텐츠를 가져온 후 클라이언트 위치가 느린 것으로 간주되는 배포 지점을 사용하려면 먼저 콘텐츠 원본으로 사용할 로컬 피어를 찾아야 하는 추가 클라이언트에 콘텐츠를 배포할 수 있습니다.  

##  <a name="bkmk_passport"></a> KSP로서 Passport for Work에 대한 지원  
 System Center Configuration Manager에서는 Active Directory 또는 Azure Active Directory 계정을 사용하여 암호, 스마트 카드 또는 가상 스마트 카드를 대신하는 대체 로그인 방법인 Microsoft Passport for Work와 통합할 수 있습니다.  
Passport를 사용하면 암호 대신 사용자 제스처를 사용하여 로그인할 수 있습니다. 사용자 제스처는 단순 PIN, 생체 인식 인증(예: Windows Hello) 또는 외부 디바이스(예: 지문 판독기)일 수 있습니다.  

-   Configuration Manager에서 사용자가 로그인하는 데 사용할 수 있는 제스처와 사용할 수 없는 제스처를 제어하고 PIN 복잡성 요구 사항을 구성할 수 있습니다.  

-   Passport for Work KSP(키 스토리지 공급자)에 인증 인증서를 저장할 수 있습니다.  

사용자가 Passport PIN을 만들 때 Windows에서 Configuration Manager가 수신 대기하는 알림을 보냅니다.  이를 통해 Configuration Manager에서 Passport PIN을 만든 사용자를 신속하게 파악할 수 있습니다. 그런 다음 Passport가 인증서 프로필에서 키 스토리지 공급자로 사용되는 경우 Configuration Manager에서 새로운 인증서를 발행할 수 있습니다.  

##  <a name="bkmk_onpremdha"></a> 온-프레미스 디바이스 상태 증명  
 이제 온-프레미스 인프라를 사용하여 통신하도록 Windows 10 디바이스에 대한 상태 증명을 구성할 수 있습니다.  관리자는 보고를 클라우드를 통해 또는 온-프레미스 리소스를 통해 수행할지 여부를 지정할 수 있습니다.  상태 증명 보고를 위해 **온-프레미스**를 선택한 경우 서비스에 대해 URI를 지정할 수 있습니다. 이를 통해 인터넷에 액세스할 수 없는 클라이언트 PC에서 상태 증명을 사용하여 디바이스를 활성화하고 관리할 수 있습니다.  

#### <a name="enable-health-attestation-for-on-premises-devices"></a>온-프레미스 디바이스에 상태 증명 사용  

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**으로 이동한 후 **온-프레미스 정상 증명 서비스 사용** 을 **예**로 설정합니다.  

2.  **온-프레미스 상태 증명 서비스 URL**을 지정하고 **확인**을 클릭합니다.  

사용해 보려면 클라이언트 에이전트 설정을 사용하여 온-프레미스 상태 증명 서비스를 구성합니다.  

##  <a name="BKMK_Smart"></a> Android 디바이스에 대한 SmartLock 설정  
 새 설정인 **스마트 잠금 및 기타 신뢰 에이전트 허용**이 **Android 및 삼성 KNOX** 구성 항목에 추가되었습니다. 이를 통해 호환되는 Android 디바이스에서 SmartLock 기능을 제어할 수 있습니다. 신뢰 에이전트라고도 하는 이 전화 기능을 통해 디바이스가 특정 Bluetooth 디바이스에 연결된 경우 또는 NFC 태그에 가까이 있는 경우와 같이 신뢰할 수 있는 위치에 있는 경우 디바이스 잠금 화면 암호를 사용하지 않도록 설정하거나 무시할 수 있습니다. 이 설정을 사용하면 최종 사용자가 SmartLock을 구성하지 않도록 방지할 수 있습니다.  
