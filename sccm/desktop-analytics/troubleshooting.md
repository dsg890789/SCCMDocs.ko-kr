---
title: 데스크톱 분석 문제 해결
titleSuffix: Configuration Manager
description: 데스크톱 분석과 관련 된 문제를 해결 하는 데 도움이 되는 기술 세부 정보입니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 63e08f3f-9558-4ed7-9bf3-3a185ddaac5c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f9e13911ef7337ca4f1f9fb2291aa026c90cfee8
ms.sourcegitcommit: 72faa1266b31849ce1a23d661a1620b01e94f517
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68536020"
---
# <a name="troubleshoot-desktop-analytics"></a>데스크톱 분석 문제 해결

이 문서의 세부 정보를 사용 하 여 Configuration Manager와 통합 된 데스크톱 분석과 관련 된 문제를 해결할 수 있습니다.



## <a name="confirm-prerequisites"></a>필수 조건 확인

많은 일반적인 문제는 필수 구성 요소가 누락 되었기 때문에 발생 합니다. 먼저 다음 구성을 확인 합니다.

- [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)  

- [Windows 구성 요소 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)  

- [데이터 공유를 사용 하도록 설정](/sccm/desktop-analytics/enable-data-sharing)하는 방법에 대 한 자세한 내용은 다음 항목을 포함 합니다.  

    - 클라이언트에서 연결 해야 하는 인터넷 끝점  

    - 프록시 서버 인증  

    - 진단 데이터 수준  



## <a name="monitor-connection-health"></a>연결 상태 모니터링

Configuration Manager의 **연결 상태** 대시보드를 사용 하 여 장치 상태별로 범주를 드릴 다운 합니다. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **데스크톱 분석 서비스** 노드를 확장 하 고 **연결 상태** 대시보드를 선택 합니다.  

자세한 내용은 [연결 상태 모니터링](/sccm/desktop-analytics/monitor-connection-health)을 참조 하세요.


## <a name="log-files"></a>로그 파일

자세한 내용은 [데스크톱 분석을 위한 로그 파일](/sccm/core/plan-design/hierarchy/log-files#desktop-analytics) 을 참조 하세요.

Configuration Manager 버전 1906부터 데스크톱 분석 문제를 해결 하려면 Configuration Manager 설치 디렉터리의 **DesktopAnalyticsLogsCollector** 도구를 사용 합니다. 몇 가지 기본적인 문제 해결 단계를 실행 하 고 관련 로그를 단일 작업 디렉터리로 수집 합니다. 자세한 내용은 [로그 수집기](/sccm/desktop-analytics/log-collector)를 참조 하세요.

### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용

1. 서비스 연결 지점에서 다음 레지스트리 키로 이동 합니다.`HKLM\Software\Microsoft\SMS\Tracing\SMS_SERVICE_CONNECTOR`  
2. **Logginglevel.information** 값을로 설정 합니다.`0`  


## <a name="bkmk_AzureADApps"></a>Azure AD 응용 프로그램

데스크톱 분석은 Azure AD에 다음 응용 프로그램을 추가 합니다.

- **Configuration Manager 마이크로 서비스**: 데스크톱 분석과 Configuration Manager 연결 합니다. 이 앱에는 액세스 요구 사항이 없습니다.  

- **MALogAnalyticsReader**: Log Analytics에서 만든 OMS 그룹 및 장치를 검색 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](#bkmk_MALogAnalyticsReader)을 참조 하세요.  

설치를 완료 한 후 이러한 앱을 프로 비전 해야 하는 경우 **연결 된 서비스** 창으로 이동 합니다. **사용자 및 앱 액세스 구성**을 선택 하 고 앱을 프로 비전 합니다.  

- **Configuration Manager에 대 한 AZURE AD 앱**입니다. 설치를 완료 한 후 연결 문제를 프로 비전 하거나 문제를 해결 해야 하는 경우 [Configuration Manager에 대 한 앱 만들기 및 가져오기](#create-and-import-app-for-configuration-manager)를 참조 하세요. 이 앱에는 **Configuration Manager Service** API에 대 한 **쓰기 cm 컬렉션 데이터** 및 **읽기 cm 컬렉션 데이터가** 필요 합니다.  


### <a name="create-and-import-app-for-configuration-manager"></a>Configuration Manager에 대 한 앱 만들기 및 가져오기

Azure 서비스 구성 마법사에서 Configuration Manager 용 Azure AD 앱을 만들 수 없거나 기존 앱을 다시 사용 하려는 경우 수동으로 만들고 가져와야 합니다. 데스크톱 분석 포털에서 [초기 온 보 딩](/sccm/desktop-analytics/set-up#initial-onboarding) 을 완료 한 후 다음 단계를 사용 합니다.

#### <a name="create-app-in-azure-ad"></a>Azure AD에서 앱 만들기

1. *전역 관리자* 권한이 있는 사용자로 [Azure Portal](http://portal.azure.com) 를 열고 **Azure Active Directory**으로 이동한 다음 **앱 등록**를 선택 합니다. 그런 다음 **새 등록**을 선택 합니다.  

2. **만들기** 패널에서 다음 설정을 구성 합니다.  

    - **이름**: 앱을 식별 하는 고유한 이름입니다. 예를 들면 다음과 같습니다.`Desktop-Analytics-Connection`  

    - **지원 되는 계정 유형**: **이 조직 디렉터리에만 있는 계정 (Contoso)**

    - **URI 리디렉션 (선택 사항)** : **웹**  

    <!--     - **Sign-on URL**: this value isn't used by Configuration Manager, but required by Azure AD. Enter a unique and valid URL, for example: `https://configmgrapp`   -->
  
    **등록**을 선택 합니다.  

3. 앱을 선택 하 고 **응용 프로그램 (클라이언트) id** 및 **디렉터리 (테 넌 트) id**를 적어둡니다. 값은 Configuration Manager 연결을 구성 하는 데 사용 되는 Guid입니다.  

4. **관리** 메뉴에서 **인증서 & 암호**를 선택 합니다. **새 클라이언트 암호**를 선택 합니다. **설명을**입력 하 고 만료 기간을 지정한 다음 **추가**를 선택 합니다. Configuration Manager 연결을 구성 하는 데 사용 되는 키의 **값** 을 복사 합니다.

    > [!Important]  
    > 이는 키 값을 복사 하는 유일한 기회입니다. 지금 복사 하지 않는 경우 다른 키를 만들어야 합니다.  
    >
    > 키 값을 안전한 위치에 저장 합니다.  

5. **관리** 메뉴에서 **API 권한**을 선택 합니다.  

    1. **API 권한** 패널에서 **사용 권한 추가**를 선택 합니다.  

    2. **Api 권한 요청** 패널에서 **내 조직에서 사용**하는 api로 전환 합니다.  

    3. **Configuration Manager 마이크로 서비스** API를 검색 하 고 선택 합니다.  

    4. **응용 프로그램 사용 권한** 그룹을 선택 합니다. **Cmcollectiondata**를 확장 하 고 다음 두 사용 권한을 모두 선택 합니다. **Cm 컬렉션 데이터** 를 쓰고 **cm 컬렉션 데이터를 읽습니다**.  

    5. **권한 추가**를 선택 합니다.  

6. **API 권한** 패널에서 **관리자 동의 부여**...를 선택 합니다. **예**를 선택 합니다.  


#### <a name="import-app-in-configuration-manager"></a>Configuration Manager에서 앱 가져오기

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 리본에서 **Azure 서비스 구성** 을 선택 합니다.  

2. Azure 서비스 마법사의 **Azure 서비스** 페이지에서 다음 설정을 구성 합니다.  

    - Configuration Manager의 개체 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    - 사용 가능한 서비스 목록에서 **데스크톱 분석** 을 선택 합니다.  
  
   **다음**을 선택합니다.  

3. **앱** 페이지에서 적절 한 **Azure 환경을**선택 합니다. 그런 다음 웹 앱에 대해 **가져오기** 를 선택 합니다. **앱 가져오기** 창에서 다음 설정을 구성 합니다.  

    - **AZURE AD 테 넌 트 이름**: 이 이름은 Configuration Manager 이름이 지정 되는 방식입니다.  

    - **AZURE AD 테 넌 트 ID**: Azure AD에서 복사한 **디렉터리 ID**  

    - **클라이언트 ID**: Azure AD 앱에서 복사한 **응용 프로그램 ID**  

    - **비밀 키**: Azure AD 앱에서 복사한 키 **값**  

    - **비밀 키 만료**: 키의 동일한 만료 날짜  

    - **앱 ID URI**: 이 설정은 다음 값으로 자동으로 채워집니다.`https://cmmicrosvc.manage.microsoft.com/`  
  
   **확인**을 선택 하 고 **확인** 을 선택 하 여 앱 가져오기 창을 닫습니다. Azure 서비스 마법사의 앱 페이지에서 **다음** 을 선택 합니다.  

**진단 데이터** 페이지에서 마법사의 나머지 부분을 계속 하려면 [서비스에 연결](/sccm/desktop-analytics/connect-configmgr#bkmk_connect)을 참조 하세요.

#### <a name="troubleshoot-app-in-configuration-manager"></a>Configuration Manager에서 앱 문제 해결

앱을 만들거나 가져오는 데 문제가 있는 경우 먼저 특정 오류에 대 한 **Smsadminui.log** 를 확인 합니다. 그런 후에 다음 구성을 확인 합니다.

- 데스크톱 분석 서비스에 테 넌 트를 등록 했습니다. 자세한 내용은 [데스크톱 분석을 설정 하는 방법](/sccm/desktop-analytics/set-up)을 참조 하세요.

- 모든 필수 끝점에 액세스할 수 있습니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)을 참조 하세요.

- 로그인 한 사용자에 게 올바른 사용 권한이 있는지 확인 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.

- 사용자가 일반적으로 Azure에 로그인 할 수 있는지 확인 합니다. 이 작업은 일반적인 Azure AD 인증 문제가 있는지 여부를 확인 합니다.

- *데스크톱 분석 작업자*와 관련 된 **SMS_SERVICE_CONNECTOR** 구성 요소에 대 한 상태 메시지를 확인 합니다.


### <a name="bkmk_MALogAnalyticsReader"></a>MALogAnalyticsReader 응용 프로그램 역할

데스크톱 분석을 설정 하는 경우 조직을 대신 하 여 동의 하 게 됩니다. 이러한 동의는 MALogAnalyticsReader 응용 프로그램에 작업 영역에 대 한 Log Analytics 판독기 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석에 필요 합니다.

설치 하는 동안이 프로세스에 문제가 있는 경우 다음 프로세스를 사용 하 여이 권한을 수동으로 추가 합니다.

1. [Azure Portal](http://portal.azure.com)로 이동 하 여 **모든 리소스**를 선택 합니다. **Log Analytics**유형의 작업 영역을 선택 합니다.  

2. 작업 영역 메뉴에서 **액세스 제어 (IAM)** 를 선택한 다음 **추가**를 선택 합니다.  

3. **권한 추가** 패널에서 다음 설정을 구성 합니다.  

    - **역할**: **익숙해야**  

    - **액세스 권한을 할당 합니다**. **Azure AD 사용자, 그룹 또는 응용 프로그램**  

    - **선택**: **MALogAnalyticsReader**  

4.           **저장**을 선택합니다.

포털에는 역할 할당을 추가 하는 알림이 표시 됩니다.


## <a name="data-latency"></a>데이터 대기 시간

<!-- 3846531 -->
데스크톱 분석을 처음 설정 하는 경우 Configuration Manager 및 데스크톱 분석 포털의 보고서에 전체 데이터가 즉시 표시 되지 않을 수 있습니다. 다음 단계를 수행 하는 데 2-3 일이 소요 될 수 있습니다.

- 활성 장치에서 데스크톱 분석 서비스로 진단 데이터 보내기
- 서비스는 데이터를 처리 합니다.
- 서비스는 Configuration Manager 사이트와 동기화 됩니다.

Configuration Manager 계층에서 데스크톱 분석으로 장치 컬렉션을 동기화 하는 경우 해당 컬렉션이 데스크톱 분석 포털에 표시 되는 데 최대 10 분 정도 걸릴 수 있습니다. 마찬가지로, 데스크톱 분석에서 배포 계획을 만들 때 배포 계획과 연결 된 새 컬렉션이 Configuration Manager 계층 구조에 표시 되는 데 최대 10 분이 걸릴 수 있습니다. 기본 사이트에서 컬렉션을 만들고 중앙 관리 사이트가 데스크톱 분석과 동기화 합니다.

데스크톱 분석 포털에는 두 가지 유형의 데이터가 있습니다. **관리자 데이터** 및 **진단 데이터**:

- **관리자 데이터** 는 작업 영역 구성에서 변경한 내용을 나타냅니다. 예를 들어 자산의 **업그레이드 결정** 또는 **중요도** 를 변경 하는 경우 관리자 데이터를 변경 하 게 됩니다. 이러한 변경 내용은 설치 된 자산의 장치 준비 상태를 변경할 수 있기 때문에 종종 그래야만 효과가 있습니다.

- **진단 데이터** 는 클라이언트 장치에서 Microsoft로 업로드 되는 시스템 메타 데이터를 나타냅니다. 이 데이터는 데스크톱 분석을 향상 시킵니다. 장치 인벤토리, 보안 및 기능 업데이트 상태와 같은 특성을 포함 합니다.

기본적으로 데스크톱 분석 포털의 모든 데이터는 매일 자동으로 새로 고쳐집니다. 이 새로 고침에는 진단 데이터의 변경 내용과 구성 (관리자 데이터)에 대 한 변경 내용이 포함 됩니다. 매일 오전 08:00 시에 데스크톱 분석 포털에 표시 되어야 합니다.

관리자 데이터를 변경할 때 작업 영역에서 관리자 데이터의 요청 시 새로 고침을 트리거할 수 있습니다. 데스크톱 분석 포털의 모든 페이지에서 데이터 통화 플라이 아웃을 엽니다.

![데스크톱 분석 포털의 데이터 통화 플라이 아웃 탭 스크린샷](media/data-currency-flyout.png)

그런 다음 **변경 내용 적용**을 선택 합니다.

![데스크톱 분석 포털에서 확장 된 데이터 통화 플라이 아웃의 스크린샷](media/data-currency-flyout-expand.png)

이 프로세스는 일반적으로 15-60 분이 소요 됩니다. 타이밍은 작업 영역의 크기와 프로세스를 필요로 하는 변경 내용의 범위에 따라 달라 집니다. 요청 시 데이터 새로 고침을 요청 하면 진단 데이터를 변경 하지 않습니다.  자세한 내용은 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)를 참조 하세요.

위에 표시 된 시간 프레임 내에 업데이트 된 변경 내용이 표시 되지 않으면 다음 일간 새로 고침을 위해 24 시간 동안 기다립니다. 더 긴 지연이 표시 되는 경우 서비스 상태 대시보드를 확인 합니다. 서비스가 정상으로 보고 되는 경우 Microsoft 지원에 문의 하세요.<!-- 3896921 -->
