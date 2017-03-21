---
title: "Technical Preview 1702 Configuration Manager의 기능"
description: "System Center Configuration Manager용 Technical Preview 버전 1702에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 02/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aedd608d-6db3-4ea5-851d-70f2dcda6bb5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 3bdbcd1a3c64a1d50f2f6219b2a5e17d60979864
ms.lasthandoff: 03/13/2017

---
# <a name="capabilities-in-technical-preview-1702-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1702의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1702에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

##  <a name="send-feedback-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 피드백 보내기

이 미리 보기에는 Configuration Manager 콘솔에 새 피드백 옵션이 도입되었습니다. 피드백 옵션을 사용하면 Configuration Manager UserVoice 피드백 웹 사이트를 통해 개발 팀에 직접 피드백을 보낼 수 있습니다.  

>**피드백** 옵션은 다음 위치에서 찾을 수 있습니다.
-  리본에서 각 노드의 홈 탭 맨 왼쪽  
   ![리본](./media/feedback-home.png)

-  콘솔에서 아무 개체나 마우스 오른쪽 단추로 클릭할 때   
    ![마우스 오른쪽 단추 클릭 옵션](./media/feedback-option.png)   

**피드백**을 선택하면 브라우저에서 Configuration Manager UserVoice 피드백 웹 사이트(https://configurationmanager.uservoice.com/forums/300492-ideas)가 열립니다.
##  <a name="changes-for-updates-and-servicing"></a>업데이트 및 서비스의 변경 내용
이 미리 보기에서 도입된 내용은 다음과 같습니다.

**보다 간단한 업데이트 선택**  
다음에 인프라에 둘 이상의 업데이트를 사용할 수 있는 경우 최신 업데이트만 다운로드됩니다. 예를 들어 현재 사이트 버전이 사용할 수 있는 가장 최근 버전보다 두 버전 이상 이전인 경우 가장 최근 업데이트 버전만 자동으로 다운로드됩니다.  

가장 최근 버전이 아닌 경우에도 다른 사용 가능한 업데이트를 다운로드하여 설치할 수 있습니다. 그러나 업데이트가 최신 버전으로 바뀌었다는 경고를 받게 됩니다. *다운로드 가능*한 업데이트를 다운로드하려면 콘솔에서 업데이트를 선택하고 **다운로드**를 클릭합니다.

**이전 업데이트 정리 개선**   
사이트 서버의 'EasySetupPayload' 폴더에서 불필요한 다운로드를 삭제하는 자동 정리 기능이 추가되었습니다.  


## <a name="peer-cache-improvements"></a>피어 캐시 개선
이 릴리스부터 피어 캐시 원본 컴퓨터가 다음 조건 중 하나라도 충족할 경우 피어 캐시 원본 컴퓨터는 콘텐츠 요청을 거부합니다.  
 -     배터리 부족 모드에 있는 경우
 -  콘텐츠를 요청 시 CPU 로드가 80%를 초과하는 경우
 -  디스크 I/O에 10을 초과하는 *AvgDiskQueueLength*가 있는 경우
 -  컴퓨터에 대한 연결을 더 이상 사용할 수 없는 경우   

System Center Configuration Manager SDK를 사용하는 경우 피어 원본 기능에 대한 클라이언트 에이전트 구성 클래스(*SMS_WinPEPeerCacheConfig*)를 사용하여 이러한 설정을 구성할 수 있습니다.

컴퓨터가 콘텐츠 요청을 거부하는 경우 요청하는 컴퓨터는 사용 가능한 콘텐츠 원본 위치 풀에서 콘텐츠 폼 대체 원본을 계속 검색합니다.   

## <a name="azurediscovery"></a> Azure Active Directory Domain Services를 사용하여 장치, 사용자 및 그룹 관리

이 기술 미리 보기 버전에서는 Azure AD(Active Directory) Domain Services 관리되는 도메인에 가입된 장치를 관리할 수 있습니다. 또한 다양한 Configuration Manager 검색 방법으로 해당 도메인에서 장치, 사용자 및 그룹을 검색할 수 있습니다.

기술 미리 보기 사이트 인프라, 클라이언트 및 Azure AD Domain Services 도메인은 모두 Azure에서 실행되어야 합니다.


### <a name="set-up-configuration-manager-to-use-azure-ad"></a>Azure AD를 사용하도록 Configuration Manager 설정
Configuration Manager에서 Azure AD를 사용하려면 다음이 필요합니다.
-    Azure 구독
-    Azure AD 및 DS(Domain Services)
-    Azure AD에 가입된 Azure VM에서 실행되는 Configuration Manager 사이트
-    동일한 Azure AD 환경에서 실행되는 Configuration Manager 클라이언트

Azure AD Domain Services를 구성하려면 [Azure AD Domain Services 시작](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started)을 참조하세요.

### <a name="discover-resources"></a>리소스 검색
Azure AD에서 실행되도록 Configuration Manager를 설정하면 다음 Active Directory 검색 방법을 사용하여 Azure AD에서 리소스를 검색할 수 있습니다.  
- Active Directory 시스템 검색
- Active Directory 사용자 검색
- Active Directory 그룹 검색  

사용하는 각 방법에 대해 온-프레미스 Active Directory에 일반적인 컨테이너 대신 Azure AD OU 구조를 검색하도록 LDAP 쿼리를 편집합니다. 이렇게 하려면 Azure 구독에서 Active Directory를 검색하도록 쿼리를 지정해야 합니다.  

다음 예제에서는 Azure AD *contoso.onmicrosoft.com*을 사용합니다.
 - **시스템 복구**   
Azure AD는 **AADDC 컴퓨터** OU 아래에 장치를 저장합니다.  다음을 구성 합니다.  
  -    *LDAP://OU=AADDC Computers,DC=contoso,DC=onmicrosoft,DC=com*  


- **사용자 검색** AAD는 **AADDC 사용자** OU 아래에 사용자를 저장합니다.  다음을 구성 합니다.
  - *LDAP://OU=AADDC Users,DC= contoso,DC=onmicrosoft,DC=com*


- **그룹 검색**  
Azure AD에는 그룹을 저장하는 OU가 없습니다. 대신, 시스템 또는 사용자 쿼리와 동일한 일반적인 구조를 사용하고 검색할 그룹을 포함하는 OU를 가리키도록 LDAP 쿼리를 구성합니다.

Azure AD에 대한 자세한 내용은 다음을 참조하세요.  
 - azure.microsoft.com의 [Azure Active Directory Domain Services](https://azure.microsoft.com/en-us/services/active-directory-ds)
 - docs.microsoft.com의 [Active Directory Domain Services 설명서](https://docs.microsoft.com/azure/active-directory-domain-services)

## <a name="conditional-access-device-compliance-policy-improvements"></a>조건부 액세스 장치 준수 정책 개선

새 장치 준수 정책 규칙을 사용하면 사용자가 비규격 앱 목록에 포함된 앱을 사용하는 경우 조건부 액세스를 지원하는 회사 리소스에 대한 액세스를 차단할 수 있습니다. 비규격 앱 목록은 관리자가 새 준수 규칙 **설치할 수 없는 앱**을 추가할 때 정의할 수 있습니다. 이 규칙을 사용하려면 관리자가 비규격 목록에 앱을 추가할 때 **앱 이름**, **앱 ID** 및 **앱 게시자**(선택 사항)를 입력해야 합니다. 이 설정은 iOS 및 Android 장치에만 적용됩니다.

또한 이렇게 하면 조직에서 보안되지 않은 앱을 통한 데이터 누출을 완화하고 특정 앱을 통한 과도한 데이터 사용을 방지할 수 있습니다.

- 자세한 내용은 [장치 준수 정책의 작동 방식](https://docs.microsoft.com/sccm/protect/deploy-use/device-compliance-policies)을 참조하세요.
- 자세한 내용은 [장치 준수 정책을 만드는 방법](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy)을 참조하세요.

### <a name="try-it-out"></a>기능 직접 사용해 보기

**시나리오:** 회사 데이터를 회사 외부로 전송하여 데이터 누출을 초래할 가능성이 있거나 과도한 데이터 사용을 초래하는 앱을 식별하고, 이러한 앱을 비규격 앱 목록에 추가하는 [조건부 액세스 장치 준수 정책을 만듭니다](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy). 이렇게 하면 사용자가 차단된 앱을 제거할 수 있을 때까지 조건부 액세스를 지원하는 회사 리소스에 대한 액세스가 차단됩니다.

## <a name="antimalware-client-version-alert"></a>맬웨어 방지 클라이언트 버전 경고
이 미리 보기 버전부터 만료된 버전의 맬웨어 방지 클라이언트(예: Windows Defender 또는 Endpoint Protection 클라이언트)를 사용하는 관리되는 클라이언트가 20%(기본값)를 초과할 경우 Configuration Manager Endpoint Protection에서 경고를 제공합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
클라이언트 설정 정책을 사용하는 모든 데스크톱 및 서버 클라이언트에서 Endpoint Protection이 사용되도록 설정되었는지 확인합니다. 이제 **자산 및 호환성** > **개요** > **장치** > **모든 데스크톱 및 클라이언트 역할**로 이동하여 **맬웨어 방지 클라이언트 버전** 및 **Endpoint Protection 배포 상태**를 확인할 수 있습니다. 경고를 확인하려면 **모니터링** 작업 영역에서 **경고**를 봅니다. 만료된 버전의 맬웨어 방지 소프트웨어를 실행하는 관리되는 클라이언트가 20%를 초과할 경우 [맬웨어 방지 클라이언트 버전이 오래되었습니다.] 경고가 표시됩니다. 이 경고는 **모니터링** > **개요** 탭에 표시되지 않습니다. 만료된 맬웨어 방지 클라이언트를 업데이트하려면 맬웨어 방지 클라이언트에 대한 소프트웨어 업데이트를 사용하도록 설정합니다.

경고가 생성되는 백분율을 구성하려면 **모니터링** > **경고** > **모든 경고**를 확장하고 **맬웨어 방지 클라이언트가 오래됨**을 두 번 클릭한 다음 **오래된 버전의 맬웨어 방지 클라이언트로 관리되는 클라이언트의 비율이 다음 이상인 경우 경고 생성** 옵션을 수정합니다.

## <a name="compliance-assessment-for-windows-update-for-business-updates"></a>Windows Update for Business 업데이트에 대한 준수 평가
이제 조건부 액세스 평가의 일부로 Windows Update for Business 평가 결과를 포함하도록 준수 정책 업데이트 규칙을 구성할 수 있습니다.
> [!IMPORTANT]
> Windows Update for Business 업데이트에 대한 준수 평가를 사용하려면 Windows 10 Insider Preview 빌드 15019 이상이 있어야 합니다.

### <a name="allow-windows-update-for-business-to-manage-windows-10-updates"></a>Windows Update for Business에서 Windows 10 업데이트를 관리할 수 있도록 허용
Windows Update for Business 업데이트에 대한 준수 평가 정보를 수집하려면 다음 절차에 따라 Windows Update for Business에서 Windows 10 업데이트를 관리할 수 있도록 명시적으로 허용하는 클라이언트 에이전트 설정을 구성합니다.
1. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정**으로 이동합니다.
2. 클라이언트 설정의 속성에서 **소프트웨어 업데이트**로 이동한 다음 **Windows Update for Business를 통해 Windows 10 업데이트 관리** 설정에 대해 **예**를 선택합니다.

### <a name="create-a-compliance-policy-for-windows-update-for-business-assessment"></a>Windows Update for Business 평가에 대한 준수 정책 만들기
1. Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **준수 정책**으로 이동합니다.
2. **준수 정책 만들기**를 클릭하거나 수정할 기존 준수 정책을 선택합니다.
3. 일반 페이지에서 이름 및 설명을 입력하고 **Configuration Manager 클라이언트를 사용하여 관리되는 장치에 대한 준수 규칙**을 선택한 다음 보고할 비준수 심각도를 설정하고 **다음**을 클릭합니다.
4. 지원되는 플랫폼 페이지에서 **Windows 10**을 선택하고 **다음**을 클릭합니다.
5. 규칙 페이지에서 **새로 만들기...**를 클릭한 다음 **조건**에 대해 **Windows Update for Business 준수 필요**를 선택합니다. **값** 설정이 자동으로 **True**로 설정됩니다.

새 정책이 **자산 및 준수** 작업 영역의 **준수 정책** 노드에 표시됩니다.

### <a name="deploy-a-compliance-policy"></a>준수 정책 배포
1. Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정**으로 이동한 다음 **준수 정책**을 클릭합니다.
2. **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.
3. **규정 준수 정책 배포** 대화 상자에서 **찾아보기** 를 클릭하여 정책을 배포할 사용자 컬렉션을 선택합니다.
   정책 미준수 시 경고를 생성하는 옵션과 이 정책의 준수 여부를 평가할 일정을 구성하는 옵션을 선택할 수도 있습니다.
4. 작업이 끝나면 **확인**을 클릭합니다.

### <a name="monitor-the-compliance-policy"></a>규정 준수 정책 모니터링
준수 정책을 만든 후 Configuration Manager 콘솔에서 준수 결과를 모니터링할 수 있습니다. 자세한 내용은 [준수 정책 모니터링](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)을 참조하세요.


## <a name="improvements-to-software-center-settings-and-notification-messages-for-high-impact-task-sequences"></a>영향력이 큰 작업 순서에 대한 소프트웨어 센터 설정 및 알림 메시지 개선
이 릴리스에는 영향력이 큰 배포 작업 순서에 대한 소프트웨어 센터 설정 및 알림 메시지와 관련해서 다음과 같은 개선 사항이 포함되어 있습니다.

- 이제 작업 순서 속성에서 비운영 체제 작업 순서를 비롯한 모든 작업 순서를 높은 위험 수준 배포로 구성할 수 있습니다. 특정 조건을 충족하는 작업 순서는 자동으로 모두 강력한 작업 순서로 정의됩니다. 자세한 내용은 [위험 수준이 높은 배포 관리](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments)를 참조하세요.
- 작업 순서 속성에서 기본 알림 메시지를 사용하거나 강력한 배포에 대한 고유한 사용자 지정 알림 메시지를 만들 수 있습니다.
- 작업 순서 속성에서 다시 시작을 필수로 설정, 작업 순서의 다운로드 크기 및 예상 실행 시간을 포함하는 소프트웨어 센터 속성을 구성할 수 있습니다.
- 이제 현재 위치 업그레이드에 대한 강력한 배포 기본 메시지에 앱, 데이터 및 설정이 자동으로 마이그레이션된다고 표시됩니다. 이전에는 모든 운영 체제 설치에 대한 기본 메시지에 모든 앱, 데이터 및 설정이 손실된다고 표시되었으며, 이는 현재 위치 업그레이드에 적용되지 않습니다.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>작업 순서를 강력한 작업 순서로 설정
작업 순서를 강력한 작업 순서로 설정하려면 다음 절차를 따르세요.
> [!NOTE]
> 특정 조건을 충족하는 작업 순서는 자동으로 모두 강력한 작업 순서로 정의됩니다. 자세한 내용은 [위험 수준이 높은 배포 관리](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments)를 참조하세요.

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **운영 체제** > **작업 순서**로 이동합니다.
2. 편집할 작업 순서를 선택하고 **속성**을 클릭합니다.
3. **사용자 알림** 탭에서 **강력한 작업 순서임**을 선택합니다.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>위험 수준이 높은 배포에 대한 사용자 지정 알림 만들기
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **운영 체제** > **작업 순서**로 이동합니다.
2. 편집할 작업 순서를 선택하고 **속성**을 클릭합니다.
3. **사용자 알림** 탭에서 **사용자 지정 텍스트 사용**을 선택합니다.
>  [!NOTE]
>  **강력한 작업 순서임**이 선택된 경우에만 사용자 알림 텍스트를 설정할 수 있습니다.

4. 다음 설정을 구성합니다(각 텍스트 상자에 최대 255자까지 입력).

   **사용자 알림 헤드라인 텍스트**: 소프트웨어 센터 사용자 알림에 표시되는 파란색 텍스트를 지정합니다. 예를 들어 기본 사용자 알림에서 이 섹션에는 "이 컴퓨터의 운영 체제를 업그레이드할 것인지 확인하세요."와 같은 내용이 포함됩니다.

   **사용자 알림 메시지 텍스트**: 사용자 지정 알림의 본문을 제공하는 텍스트 상자 세 개가 있습니다.
   - 첫 번째 텍스트 상자: 일반적으로 사용자에 대한 지침이 포함된 텍스트의 본문을 지정합니다. 예를 들어 기본 사용자 알림에서 이 섹션에는 "운영 체제를 업그레이드하는 데 시간이 걸리며 컴퓨터가 여러 번 다시 시작될 수 있습니다."와 같은 내용이 포함됩니다.
   - 두 번째 텍스트 상자: 텍스트의 기본 본문 아래에 표시되는 굵은 텍스트를 지정합니다. 예를 들어 기본 사용자 알림에서 이 섹션에는 "이 현재 위치 업그레이드에서는 새 운영 체제를 설치하고 앱, 데이터 및 설정을 자동으로 마이그레이션합니다."와 같은 내용이 포함됩니다.
   - 세 번째 텍스트 상자: 굵은 텍스트 아래에 표시되는 텍스트의 마지막 줄을 지정합니다. 예를 들어 기본 사용자 알림에서 이 섹션에는 "시작하려면 [설치]를 클릭하고 그렇지 않으면 [취소]를 클릭하세요."와 같은 내용이 포함됩니다.   

   속성에서 다음과 같은 사용자 지정 알림을 구성한다고 가정해 봅니다.

   ![작업 순서에 대한 사용자 지정 알림](.\media\user-notification.png)

   최종 사용자가 소프트웨어 센터에서 설치를 열면 다음과 같은 알림 메시지가 표시됩니다.

   ![작업 순서에 대한 사용자 지정 알림](.\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>소프트웨어 센터 속성 구성
소프트웨어 센터에 표시된 작업 순서에 대한 세부 정보를 구성하려면 다음 절차를 따르세요. 이러한 세부 정보는 정보 제공용입니다.  
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **운영 체제** > **작업 순서**로 이동합니다.
2. 편집할 작업 순서를 선택하고 **속성**을 클릭합니다.
3. **일반** 탭에서 소프트웨어 센터에 대한 다음 설정을 사용할 수 있습니다.
  - **다시 시작 필요**: 설치하는 동안 다시 시작해야 하는지 여부를 사용자에게 알립니다.
  - **다운로드 크기(MB)**: 작업 순서에 대해 소프트웨어 센터에 표시되는 메가바이트 수를 지정합니다.  
  - **예상 실행 시간(분)**: 작업 순서에 대해 소프트웨어 센터에 표시되는 예상 실행 시간(분)을 지정합니다.


## <a name="check-for-running-executable-files-before-installing-an-application"></a>응용 프로그램을 설치하기 전에 실행 중인 실행 파일 확인

이제 [설치 동작] 탭에 있는 배포 유형의 *<deployment type name>* **속성** 대화 상자에서 배포 유형의 설치를 차단하는 실행 파일(실행 중일 경우)을 하나 이상 지정할 수 있습니다. 사용자가 실행 중인 실행 파일을 닫아야(또는 필수 용도의 배포를 위해 자동으로 닫힐 수 있음) 배포 유형을 설치할 수 있습니다.

### <a name="try-it-out"></a>직접 시도해 보세요.

1.    Configuration Manager 배포 유형의 속성에서 **설치 동작** 탭을 선택합니다.
2.    **추가**를 선택하여 확인할 실행 파일 이름을 하나 이상 추가합니다. 사용자가 목록에서 응용 프로그램을 식별하기 쉽도록 표시 이름을 추가할 수도 있습니다.
3.    배포 용도가 필수인 경우 소프트웨어 배포 마법사에서 필요에 따라 **배포 유형 속성 대화 상자의 설치 동작 탭에 지정한 모든 실행 중인 실행 파일 자동으로 닫기**를 선택할 수 있습니다.

응용 프로그램이 **사용 가능**으로 배포된 경우 최종 사용자가 응용 프로그램을 설치하려고 하면 지정된 실행 중인 실행 파일을 닫아야 설치를 계속할 수 있다는 메시지가 표시됩니다.

응용 프로그램이 **필수**로 배포되었으며 **배포 유형 속성 대화 상자의 설치 동작 탭에 지정한 모든 실행 중인 실행 파일 자동으로 닫기** 옵션이 선택된 경우 응용 프로그램 설치 최종 기한에 도달하면 지정된 실행 파일이 자동으로 닫힌다고 알리는 대화 상자가 표시됩니다. **클라이언트 설정** > **컴퓨터 에이전트**에서 이러한 대화 상자를 예약할 수 있습니다. 이러한 메시지를 최종 사용자에게 표시하지 않으려면 배포 속성의 **사용자 환경** 탭에서 **소프트웨어 센터에 모든 알림 숨기기**를 선택합니다.

응용 프로그램이 **필수**로 배포되었으며 **배포 유형 속성 대화 상자의 설치 동작 탭에 지정한 모든 실행 중인 실행 파일 자동으로 닫기** 옵션이 선택되지 않은 경우 지정된 응용 프로그램 중 하나 이상이 실행 중이면 앱 설치에 실패합니다.

## <a name="create-pfx-certificates-with-s-mime-support"></a>S MIME을 지원하는 PFX 인증서 만들기

이제 S/MIME을 지원하는 PFX 인증서 프로필을 만들어 사용자에게 배포할 수 있습니다.  그러면 사용자가 등록한 장치 전체에서 이 인증서를 S/MIME 암호화 및 암호 해독에 사용할 수 있습니다.

또한 이제 여러 인증서 등록 지점 사이트 시스템 역할에 여러 CA(인증 기관)를 지정한 다음 인증서 프로필의 일부로 요청을 처리하는 CA를 할당할 수 있습니다.

iOS 장치의 경우 PFX 인증서 프로필을 메일 프로필에 연결하고 S/MIME 암호화를 사용하도록 설정할 수 있습니다.  이렇게 하면 iOS의 네이티브 메일 클라이언트에서 S/MIME이 사용되고 올바른 S/MIME 암호화 인증서가 연결됩니다.

Configuration Manager의 인증서에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필 소개]( https://docs.microsoft.com/sccm/protect/deploy-use/introduction-to-certificate-profiles)를 참조하세요.


## <a name="new-compliance-settings-for-ios-devices"></a>iOS 장치에 대한 새 준수 설정

iOS 장치에 대한 구성 항목에서 사용할 수 있는 새 설정이 추가되었습니다. 이러한 설정은 이전에 Microsoft Intune의 독립 실행형 구성에 있던 설정이며 이제 Intune과 Configuration Manager를 사용할 때 제공됩니다. 이러한 설정에 대한 도움이 필요하면 [Microsoft Intune의 iOS 정책 설정](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune)을 참조하세요.

- **관리되는 앱에서 데이터를 iCloud와 동기화**
- **다른 디바이스에서 작업을 계속하도록 핸드오프**
- **iCloud 사진 공유**
- **iCloud 사진 라이브러리**
- **새로운 엔터프라이즈 앱 작성자 신뢰**
- **사용자가 iBook 스토어에서 'Erotica'로 플래그가 지정된 콘텐츠를 다운로드하도록 허용**(감독 모드인 경우에만)
- **페어링된 Apple Watch에서 강제로 손목 감지를 사용하도 지정**
- **AirPlay 발신 요청 암호**
- **계정 설정 수정**(감독 모드인 경우에만)
- **앱 셀룰러 데이터 사용량 설정 변경**(감독 모드인 경우에만)
- **모든 콘텐츠 및 설정 지우기**(감독 모드인 경우에만)
- **장치에 대한 제한 구성** (감독된 모드에만 해당)
- **호스트 페어링을 사용하여 iOS 장치에서 페어링할 수 있는 장치 제어**(감독 모드인 경우에만)
- **구성 프로필 및 인증서 설치**(감독 모드인 경우에만)
- **장치 이름 수정**(감독 모드인 경우에만)
- **암호 수정**(감독 모드인 경우에만)
- **Apple Watch 페어링**(감독 모드인 경우에만)
- **알림 설정 수정**(감독 모드인 경우에만)
- **배경 화면 수정**(감독 모드인 경우에만)
- **진단 전송 설정 수정**(감독 모드인 경우에만)
- **Bluetooth 수정**(감독 모드인 경우에만)
- **AirDrop**(감독 모드인 경우에만)
- **Siri를 사용하여 인터넷에서 사용자 생성 콘텐츠 쿼리**(감독 모드인 경우에만)
- **Siri 욕설 필터**(감독 모드인 경우에만)
- **Spotlight 검색에서 인터넷 검색 결과 반환**(감독 모드인 경우에만)
- **단어 정의 조회**(감독 모드인 경우에만)
- **자동 완성 키보드**(감독 모드인 경우에만)
- **자동 수정**(감독 모드인 경우에만)
- **키보드 맞춤법 검사**(감독 모드인 경우에만)
- **바로 가기 키**(감독 모드인 경우에만)
<!--- - **Enterprise app trust settings modification** --->
- **Apple Configurator 및 iTunes를 사용한 앱 설치만**(감독 모드인 경우에만)
- **자동 앱 다운로드**(감독 모드인 경우에만)
- **Find My Friends 앱 설정 변경**(감독 모드인 경우에만)
- **iBooks 스토어 액세스**(감독 모드인 경우에만)
- **메시지 앱**(감독 모드인 경우에만)
- **팟캐스트**(감독 모드인 경우에만)
- **Apple Music**(감독 모드인 경우에만)
- **iTunes Radio**(감독 모드인 경우에만)
- **Apple News**(감독 모드인 경우에만)
- **Game Center**(감독 모드인 경우에만)
- **Airdrop을 관리되지 않는 대상으로 처리**

## <a name="android-for-work-support"></a>Android for Work 지원

Technical Preview 버전 1702부터 Google 계정을 하이브리드 MDM 테넌트에 바인딩할 수 있습니다. 이렇게 하면 다음을 수행할 수 있습니다.

- [지원되는 Android 장치](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012)를 Android for Work로 등록하고 이러한 등록된 장치에 작업 프로필 만들기
- Play for Work 스토어에서 앱을 승인하고, Configuration Manager 콘솔과 동기화한 다음 장치의 작업 프로필에 배포
- 구성 항목을 만들고 배포하여 해당 장치에 대한 작업 프로필 및 암호 설정 구성
- Android 장치에 대해 이미 수행하는 것처럼 Android for Work 장치에 대한 준수 정책 항목과 리소스 액세스 프로필 만들기 및 배포
- Android for Work 장치에서 선택적 초기화 수행

장치를 Android for Work로 등록하면 Intune에서 관리할 수 있는 장치에 작업 프로필이 생성됩니다. 이 작업 프로필은 Android 장치의 개인 프로필과 나란히 존재합니다. 사용자는 작업 프로필 앱과 개인 프로필 앱 간에 쉽게 전환할 수 있습니다. 개인 프로필에서 항목을 관리할 수 없습니다. 개인 앱과 데이터는 관리되지 않는 상태로 유지됩니다. Configuration Manager는 작업 프로필 및 해당 내용에 대한 모든 권한을 가지며 장치에서 제거할 수 있습니다.

Android for Work는 Android와 별도 플랫폼이며, 작업 프로필을 지원하는 Android 장치에 사용할 관리 형식을 결정해야 합니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기
다음 섹션에서는 Android for Work 관리에 대해 설명합니다.

#### <a name="enable-android-for-work-management"></a>Android for Work 관리 사용
1. 이 Intune 테넌트에 대한 모든 Android for Work 관리 작업과 연결할 Android for Work 관리자 계정으로 사용할 Google 계정을 https://accounts.google.com/SignUp에서 만듭니다. 이 Google 계정은 Android 장치를 관리하는 관리자 간에 공유될 수 있습니다. 또한 조직이 Play for Work 콘솔에서 앱을 관리하고 게시하는 데 사용하는 Google 계정입니다. 이 계정을 사용하여 Play for Work 스토어에서 앱을 승인하므로 계정 이름과 암호를 추적합니다.
2. Configuration Manager에서 관리되는 Intune 테넌트에 Google 계정을 바인딩하여 Android 등록을 사용하도록 설정합니다.
  1. **관리** > **개요** > **Cloud Services** > **Microsoft Intune 구독**으로 이동한 다음 Intune 구독을 선택합니다.
  2. 리본에서 **플랫폼 구성** > **Android**를 클릭하고 **Android 등록 사용**이 선택되었는지 확인합니다.
  3. 리본에서 **플랫폼 구성** > **Android for Work**를 클릭합니다.
  4. 대화 상자에서 **Intune 콘솔에서 Android for Work 구성**을 클릭합니다. Intune 콘솔이 웹 브라우저에서 열립니다.
  5. Intune 관리자 자격 증명을 사용하여 Intune 포털에 로그인합니다.
  6. **구성**을 클릭하여 Google Play의 Android for Work 웹 사이트를 엽니다.
  7. Google의 로그인 페이지에서 1단계의 Google 계정 자격 증명을 입력한 다음 회사 정보를 제공합니다.
3. Intune 포털로 돌아오면 Android for Work이 사용되며, Android for Work 장치에 대한 세 가지 등록 옵션이 있습니다.
  - **모든 장치를 Android로 관리** - (사용 안 함) Android for Work를 지원하는 장치를 포함하여 모든 Android 장치가 기존 Android 장치로 등록됩니다.
  - **지원되는 장치를 Android for Work로 관리** - (사용) Android for Work를 지원하는 모든 장치가 Android for Work로 등록됩니다. Android for Work를 지원하지 않는 Android 장치는 기존 Android 장치로 등록됩니다.
  - **이러한 그룹의 사용자에 대해서만 지원되는 장치를 Android for Work로 관리** - (테스트 중) Android for Work 관리의 대상을 제한된 사용자 집합으로 지정할 수 있습니다. Android for Work를 지원하는 장치를 등록하는 선택된 그룹의 구성원만 Android for Work 장치로 등록됩니다. 다른 모든 장치는 Android 장치로 등록됩니다.
  
> [!NOTE]
> 알려진 문제로 인해 **Manage supported devices for users only in these groups as Android for Work**(이 그룹의 사용자만을 위해 지원되는 장치를 Android for Work로 관리) 옵션이 제대로 작동되지 않습니다. 지정된 Azure AD 그룹의 사용자 장치가 Android for Work 대신 Android로 등록됩니다. Android for Work를 테스트하려면 **Manage all supported devices as Android for Work**(지원되는 장치를 모두 Android for Work로 관리)를 사용해야 합니다.


  Android for Work 등록을 사용하도록 설정하려면 아래쪽 두 옵션 중 하나를 선택해야 합니다. **이러한 그룹의 사용자에 대해서만 지원되는 장치를 Android for Work로 관리** 옵션을 사용하려면 Azure Active Directory 보안 그룹을 먼저 설정해야 합니다.

바인딩이 완료되면 계정 이름 및 조직 이름이 Intune 포털에 표시되며, 이제 두 브라우저를 닫아도 됩니다.

#### <a name="approve-and-deploy-android-for-work-apps"></a>Android for Work 앱 승인 및 배포
Play for Work 스토어에서 앱을 승인하고, Configuration Manager 콘솔과 동기화하고, 관리되는 Android for Work 장치에 배포하려면 다음 단계를 따르세요. 사용자의 작업 프로필에 앱을 배포하려면 Play for Work에서 앱을 승인한 다음 Configuration Manager 콘솔과 동기화해야 합니다.

1. 브라우저를 열고 https://play.google.com/work로 이동합니다.
2. Intune 테넌트에 바인딩된 Google 관리자 계정을 사용하여 로그인합니다.
3. 환경에 배포하려는 앱을 찾은 다음 각 앱에 대해 **승인**을 클릭합니다.
4. Configuration Manager 콘솔에서 **관리자** > **개요** > **Cloud Services** > **Android for Work**로 이동한 다음 **동기화**를 클릭합니다.
5. 앱이 동기화될 때까지 최대 10분 정도 기다린 다음 **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **스토어 앱에 대한 라이선스 정보**로 이동합니다.
6. Android for Work에서 동기화된 앱을 클릭한 다음 **응용 프로그램 만들기**를 클릭합니다.
7. 마법사를 완료하고 **닫기**를 클릭합니다.
8. **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **응용 프로그램**으로 이동한 다음 Android for Work 앱을 선택하여 평소대로 배포합니다.

Android for Work 앱을 Configuration Manager와 동기화하려면 Android for Work 웹 사이트에서 앱을 하나 이상 승인해야 합니다.

#### <a name="enroll-an-android-for-work-device"></a>Android for Work 장치 등록
Android for Work 장치를 등록하는 방법은 Android 등록과 비슷합니다. 모바일 장치에서 Android용 회사 포털 앱을 다운로드하여 실행합니다. 등록 프로세스의 일부로 작업 프로필을 만들라는 메시지가 나타납니다.  작업 프로필을 만든 후 관리되는 버전의 회사 포털로 전환해야 합니다. 관리되는 회사 포털은 오른쪽 아래에 작은 주황색 서류 가방이 태그로 지정되어 있습니다.

#### <a name="create-and-deploy-a-configuration-item"></a>구성 항목 만들기 및 배포
Android for Work에는 구성 항목에 대한 다음 두 가지 설정 그룹이 있습니다.
- 암호
- 작업 프로필

Android 6 이상을 실행하는 장치에서는 다음 구성 항목뿐 아니라 작업 프로필 간에 콘텐츠 공유를 구성할 수 있습니다.
- 특정 사용 권한을 요청하는 앱에 대한 동작
- 작업 프로필 내의 응용 프로그램에 대한 알림이 잠금 화면에 표시되는지 여부

이 동작을 시도하려면 표준 워크플로를 통해 구성 항목을 만들고, **일반** 페이지에서 **Android for Work**를 선택하고, 기준에 구성 항목을 추가한 다음 평소대로 배포하여 각 설정 그룹에 대한 설정을 구성합니다. 이러한 설정은 Android for Work로 등록된 장치에만 적용되고 Android로 등록된 장치에는 적용되지 않습니다.

#### <a name="perform-selective-wipe"></a>선택적 초기화 수행
작업 프로필만 관리하기 때문에 Android for Work로 등록된 장치는 선택적 초기화만 가능합니다. 이렇게 하면 개인 프로필이 초기화되지 않도록 보호됩니다. Android for Work 장치에서 선택적 초기화를 수행하면 모든 앱과 데이터를 비롯한 작업 프로필이 제거되고 장치 등록이 취소됩니다.

Android for Work 장치를 선택적으로 초기화하려면 Configuration Manager 콘솔에서 일반적인 [선택적 초기화 프로세스](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)를 사용합니다.

#### <a name="known-issues-for-android-for-work"></a>Android for Work의 알려진 문제
**Android for Work 메일 프로필에 동기화 일정을 구성하면 배포에 실패함** Android for Work 메일 프로필에 대한 ConfigMgr UI의 옵션 중 하나는 "Schedule"(일정)입니다. 다른 플랫폼에서는 관리자가 메일 및 다른 메일 계정 데이터를 배포되는 모바일 장치와 동기화하는 일정을 구성할 수 있습니다. 그러나 Android for Work 메일 프로필에 대해서는 동기화 일정을 구성할 수 없으며, "Not Configured"(구성되지 않음) 외에 다른 옵션을 선택하면 프로필이 장치에 배포되지 않습니다.

