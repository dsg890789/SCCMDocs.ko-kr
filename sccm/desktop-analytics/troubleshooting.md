---
title: 데스크톱 Analytics 문제 해결
titleSuffix: Configuration Manager
description: 데스크톱 Analytics를 사용 하 여 문제를 해결 하려면 기술 세부 정보입니다.
ms.date: 06/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 63e08f3f-9558-4ed7-9bf3-3a185ddaac5c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 271803e42ba20d8d0340754b3167210414423014
ms.sourcegitcommit: d8cfd0edf2579e2b08a0ca8a0a7b8f53d1e4196f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67463802"
---
# <a name="troubleshoot-desktop-analytics"></a>데스크톱 Analytics 문제 해결

데스크톱 Analytics를 Configuration Manager 통합을 사용 하 여 문제를 해결 하기 위해이 문서에서 세부 정보를 사용 합니다.



## <a name="confirm-prerequisites"></a>필수 구성 요소 확인

많은 일반적인 문제는 누락 된 필수 구성 요소에서 발생 합니다. 먼저 다음과 같은 구성을 확인 합니다.

- [전제 조건](/sccm/desktop-analytics/overview#prerequisites)  

- [Windows 구성 요소 업데이트](/sccm/desktop-analytics/enroll-devices#update-devices)  

- [데이터 공유를 사용 하는 방법](/sccm/desktop-analytics/enable-data-sharing)에 다음 항목을 다룹니다.  

    - 클라이언트를 연결 하려면 인터넷 끝점  

    - 프록시 서버 인증  

    - 진단 데이터 수준  



## <a name="monitor-connection-health"></a>연결 상태 모니터링

사용 된 **연결 상태** 장치 상태별으로 범주로 드릴 다운 하려면 Configuration Manager의 대시보드. Configuration Manager 콘솔에서로 이동 합니다 **소프트웨어 라이브러리** 작업 영역에서 확장을 **데스크톱 분석 서비스** 노드를 선택한는 **연결 상태** 대시보드입니다.  

자세한 내용은 [연결 상태를 모니터링](/sccm/desktop-analytics/monitor-connection-health)합니다.


## <a name="log-files"></a>로그 파일

자세한 내용은 참조 하세요. [데스크톱 분석에 대 한 로그 파일](/sccm/core/plan-design/hierarchy/log-files#desktop-analytics)

### <a name="enable-verbose-logging"></a>자세한 정보 로깅 사용

1. 서비스 연결 지점에서 다음 레지스트리 키로 이동 합니다. `HKLM\Software\Microsoft\SMS\Tracing\SMS_SERVICE_CONNECTOR`  
2. 설정 된 **LoggingLevel** 값 `0`  
3. (선택 사항) 사이트 데이터베이스에서 다음 SQL 명령을 실행 합니다.  

    ```SQL
    DELETE FROM M365AProperties WHERE Name = 'M365ATenantUpdateInfo_LastUpdateTime'
    ```

4. 다시 시작 합니다 **SMS_EXECUTIVE** 사이트 서버의 서비스



## <a name="bkmk_AzureADApps"></a> Azure AD 응용 프로그램

Azure ad에 응용 프로그램을 추가 하는 데스크톱 분석:

- **Configuration Manager 마이크로 서비스**: 데스크톱 Analytics를 사용 하 여 Configuration Manager에 연결 합니다. 이 앱에 대 한 액세스 요구 사항이 없습니다.  

- **MALogAnalyticsReader**: OMS 그룹 및 Log Analytics에서 생성 하는 장치를 검색 합니다. 자세한 내용은 [MALogAnalyticsReader 응용 프로그램 역할](#bkmk_MALogAnalyticsReader)입니다.  

설치를 완료 한 후 이러한 앱을 프로 비전 해야 할 경우으로 이동 합니다 **연결 된 서비스** 창입니다. 선택 **사용자 및 앱에 대 한 액세스 구성**, 및 앱 프로 비전 합니다.  

- **Configuration Manager에 대 한 azure AD 앱**합니다. 프로 비전 또는 설치를 완료 한 후 연결 문제를 해결 하 고, 참조 하는 경우 [Configuration Manager에 대 한 앱 만들기 및 가져오기](#create-and-import-app-for-configuration-manager)합니다. 이 앱에 필요한 **CM 컬렉션 데이터 쓰기** 하 고 **CM 컬렉션 데이터 읽기** 에 **Configuration Manager 서비스** API.  


### <a name="create-and-import-app-for-configuration-manager"></a>만들기 및 Configuration Manager에 대 한 앱 가져오기

완료 한 후 합니다 [초기 온 보 딩](/sccm/desktop-analytics/set-up#initial-onboarding) 데스크톱 Analytics 포털에서 사용 하 여 다음 단계를 수동으로 만들고 Azure 서비스 구성에서이 Azure AD 앱을 만들 수 없는 경우 Configuration Manager에 대 한 앱 가져오기 마법사입니다.

#### <a name="create-app-in-azure-ad"></a>Azure AD에서 앱 만들기

1. 열기를 [Azure portal](http://portal.azure.com) 사용자로 *전역 관리자* 권한으로 이동 **Azure Active Directory**를 선택 하 고 **앱 등록**. 선택한 **새 등록**합니다.  

2. 에 **만들기** 패널에서 다음 설정을 구성 합니다.  

    - **이름**: 예를 들어 앱을 식별 하는 고유 이름: `Desktop-Analytics-Connection`  

    - **지원 되는 계정 유형**: **이 조직 디렉터리에만 (Contoso) 계정**

    - **리디렉션 URI (선택 사항)** : **Web**  

    <!--     - **Sign-on URL**: this value isn't used by Configuration Manager, but required by Azure AD. Enter a unique and valid URL, for example: `https://configmgrapp`   -->
  
    선택 **등록**합니다.  

3. 앱을 선택 합니다 **(클라이언트) 응용 프로그램 ID** 하 고 **디렉터리 (테 넌 트) ID**합니다. 값은 Configuration Manager 연결을 구성 하는 데 사용 되는 Guid입니다.  

4. 에 **관리** 메뉴에서 **인증서 및 비밀**합니다. 선택 **새 클라이언트 암호**합니다. 입력 한 **설명을**, 만료 기간을 지정 하 고 선택한 **추가**합니다. 복사 합니다 **값** Configuration Manager 연결을 구성 하는 데 사용 되는 키입니다.

    > [!Important]  
    > 키 값을 복사만 기회입니다. 이제 복사 안 함, 하는 경우 다른 키를 만들 해야 합니다.  
    >
    > 키 값을 안전한 위치에 저장 합니다.  

5. 에 **관리** 메뉴에서 **API 사용 권한**합니다.  

    1. 에 **API 사용 권한** 패널에서 **권한을 추가**합니다.  

    2. 에 **요청 API 사용 권한** 패널에서 전환할 **내 조직에서 사용 하는 Api**합니다.  

    3. 검색 하 고 선택 합니다 **Configuration Manager 마이크로 서비스** API.  

    4. 선택 된 **응용 프로그램 사용 권한** 그룹입니다. 확장 **CmCollectionData**, 다음 사용 권한을 모두 선택 합니다. **CM 컬렉션 데이터를 쓸** 하 고 **CM 컬렉션 데이터를 읽을**합니다.  

    5. 선택 **권한 추가**합니다.  

6. 에 **API 사용 권한** 패널에서 **관리자 동의 부여 하는 중...** . 선택 **예**합니다.  


#### <a name="import-app-in-configuration-manager"></a>Configuration Manager에서는 가져오기 앱

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. 선택 **Azure 서비스 구성** 리본 메뉴에 있습니다.  

2. 에 **Azure Services** 페이지 Azure 서비스 마법사의 다음 설정을 구성 합니다.  

    - Configuration Manager의 개체 **이름**을 지정합니다.  

    - 서비스를 식별하는 데 도움이 되도록 선택적 **설명**을 지정합니다.  

    - 선택 **데스크톱 분석** 사용 가능한 서비스 목록에서.  
  
   **다음**을 선택합니다.  

3. 에 **앱** 페이지에서 적절 한 선택 **Azure 환경**합니다. 선택한 **가져오기** 웹 앱에 대 한 합니다. 다음 설정을 구성 합니다 **앱 가져오기** 창:  

    - **Azure AD 테 넌 트 이름**: 이 이름은 Configuration Manager에서 지정 됩니다 하는 방법  

    - **Azure AD 테 넌 트 ID**: 합니다 **디렉터리 ID** Azure AD에서 복사한  

    - **클라이언트 ID**: 합니다 **응용 프로그램 ID** Azure AD 앱에서 복사  

    - **비밀 키**: 키 **값** Azure AD 앱에서 복사  

    - **비밀 키 만료**: 동일한 키의 만료 날짜  

    - **앱 ID URI**: 이 설정은 다음 값을 사용 하 여 자동으로 채워야 합니다. `https://cmmicrosvc.manage.microsoft.com/`  
  
   선택 **확인**를 선택한 후 **확인** 앱 가져오기 창을 닫습니다. 선택 **다음** Azure 서비스 마법사의 앱 페이지에 있습니다.  

마법사의 나머지 부분에서 계속 합니다 **진단 데이터** 페이지를 참조 하십시오 [서비스에 연결](/sccm/desktop-analytics/connect-configmgr#bkmk_connect)합니다.

#### <a name="troubleshoot-app-in-configuration-manager"></a>Configuration Manager에서 앱 문제 해결

만들기 또는 가져오기 앱, 첫 번째 검사 문제를 겪고 있는 경우 **smsadminui.log 하세요** 특정 오류에 대 한 합니다. 다음 구성을 확인 합니다.

- 성공적으로 데스크톱 Analytics 서비스에 테 넌 트를 등록 했습니다. 자세한 내용은 [데스크톱 Analytics를 설정 하는 방법을](/sccm/desktop-analytics/set-up)합니다.

- 모든 필요한 끝점에 액세스할 수 있습니다. 자세한 내용은 [끝점](/sccm/desktop-analytics/enable-data-sharing#endpoints)합니다.

- 로그인 한 사용자 권한이 있는지 확인 합니다. 자세한 내용은 [필수 구성 요소](/sccm/desktop-analytics/overview#prerequisites)를 참조하세요.

- 사용자 로그인 할 수 있는지 azure 일반적 있는지 확인 합니다. 이 작업 확인 하는 경우 일반 Azure AD 인증 문제.

- 에 대 한 상태 메시지를 확인 합니다 **SMS_SERVICE_CONNECTOR** 구성 요소에 대 한 합니다 *데스크톱 분석 작업자*.


### <a name="bkmk_MALogAnalyticsReader"></a> MALogAnalyticsReader 응용 프로그램 역할

데스크톱 Analytics를 설정 하는 경우 조직을 대신 하 여 동의 합니다. 이 동의 MALogAnalyticsReader 응용 프로그램 작업 영역에 대 한 Log Analytics Reader 역할을 할당 하는 것입니다. 이 응용 프로그램 역할은 데스크톱 분석 필요 합니다.

설치 하는 동안이 프로세스에 문제가 있으면이 사용 권한을 수동으로 추가 하려면 다음 프로세스를 사용 합니다.

1. 로 이동 합니다 [Azure portal](http://portal.azure.com), 선택한 **모든 리소스**합니다. 형식의 작업 영역 선택 **Log Analytics**합니다.  

2. 작업 영역 메뉴에서 선택 **액세스 제어 (IAM)** 을 선택한 후 **추가**합니다.  

3. 에 **권한 추가** 패널에서 다음 설정을 구성 합니다.  

    - **역할**: **판독기**  

    - **에 대 한 액세스 할당**: **Azure AD 사용자, 그룹 또는 응용 프로그램**  

    - **선택**: **MALogAnalyticsReader**  

4. **저장**을 선택합니다.

알림 역할 할당을 추가 하는 포털 보여 줍니다.


## <a name="data-latency"></a>데이터 대기 시간

<!-- 3846531 -->
데스크톱 Analytics를 처음 설치할 때 Configuration Manager 및 Desktop Analytics 포털에서 보고서 표시 되지 않습니다 전체 데이터 바로. 발생 하는 다음 단계에 대해 2 ~ 3 일 걸릴 수 있습니다.

- 활성 장치 데스크톱 Analytics 서비스에 진단 데이터 보내기
- 서비스 데이터를 처리합니다.
- Configuration Manager 사이트를 사용 하 여 동기화 서비스

Configuration Manager 계층 구조에서 데스크톱 분석을 장치 컬렉션을 동기화 하는 경우 데스크톱 Analytics 포털에서 표시 하는 컬렉션에 대해 최대 10 분까지 걸릴 수 있습니다. 마찬가지로, 데스크톱 Analytics에서 배포 계획을 만들 때 Configuration Manager 계층에 표시 하기 위한 배포 계획을 사용 하 여 연결 된 새 컬렉션에 대 일 분 정도 걸릴 수 있습니다. 주 사이트 컬렉션을 만들고 데스크톱 Analytics를 사용 하 여 중앙 관리 사이트를 동기화 합니다.

데스크톱 Analytics 포털 내는 두 가지 유형의 데이터 **관리자 데이터** 하 고 **진단 데이터**:

- **관리자 데이터** 작업 영역 구성에 변경 내용이 가리킵니다. 예를 들어 변경한 경우 자산의 **업그레이드 결정** 하거나 **중요도** 관리자 데이터를 변경 하는 합니다. 이러한 변경 내용은 경우가 말고 효과 처럼 설치의 해당 자산을 사용 하 여 장치 준비 상태를 변경할 수 있습니다.

- **진단 데이터** 클라이언트 장치에서 Microsoft에 업로드 하는 시스템 메타 데이터를 가리킵니다. 이 데이터 분석 데스크톱을 구동 합니다. 장치 인벤토리 등의 특성을 포함 하 고 보안 및 기능 업데이트 상태입니다.

기본적으로 포털은 자동으로 데스크톱 Analytics에서 모든 데이터에는 매일을 새로 고쳐집니다. 이 새로 고침 구성 (관리자 데이터)의 변경 내용을 진단 데이터에 변경 내용을 포함 합니다. 표시 되는 것 오전 08시 UTC에서 데스크톱 Analytics 포털에서 각 날짜입니다.

관리자 데이터를 변경한 경우에 작업 영역에서 관리자 데이터는 요청 시 새로 고침을 트리거할 수 있습니다. 데스크톱 Analytics 포털에서 모든 페이지에서 데이터 통화 플라이 아웃을 엽니다.

![데스크톱 Analytics 포털에서 데이터 통화 플라이 아웃 탭의 스크린샷](media/data-currency-flyout.png)

선택한 **변경 내용을 적용**:

![데스크톱 Analytics 포털에서 확장 된 데이터가 통화 플라이 아웃의 스크린샷](media/data-currency-flyout-expand.png)

이 프로세스는 일반적으로 15 ~ 60 분 정도 걸립니다. 타이밍 작업 영역의 크기와 프로세스를 필요로 하는 변경 내용의 범위에 따라 달라 집니다. 요청 시 데이터 새로 고침을 요청 하면 하지 발생 하 게 변경 내용을 진단 데이터입니다.  자세한 내용은 참조는 [데스크톱 분석 FAQ](/sccm/desktop-analytics/faq#can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal)합니다.

위에 표시 된 시간 프레임 내에서 업데이트 된 변경 내용에 표시 되지 않으면 다른 24 시간 동안 대기 다음 매일 새로 고침에 대 한 합니다. 긴 지연 표시 되 면 서비스 상태 대시보드를 확인 합니다. 서비스를 정상으로 보고 하는 경우 Microsoft 지원에 문의 합니다.<!-- 3896921 -->
