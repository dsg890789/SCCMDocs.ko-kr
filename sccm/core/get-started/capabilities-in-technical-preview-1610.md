---
title: "System Center Configuration Manager용 Technical Preview 1610의 기능 | Microsoft 문서"
description: "System Center Configuration Manager용 Technical Preview 버전 1610에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 10/21/2016
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: 8b31fd3e-875a-4a31-9498-5b050aadce32
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 3bf44f850722afdb8dfe5922c8ceff11c9b56d08
ms.openlocfilehash: 6ffcb33e94f942fc9400457d3f16b65e12332956

---
# <a name="capabilities-in-technical-preview-1610-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1610의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*



이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1610에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다.      이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  
## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>자동 배포 규칙의 콘텐츠 크기에 따라 필터링
이제 자동 배포 규칙에서 소프트웨어 업데이트의 콘텐츠 크기를 기준으로 필터링할 수 있습니다. 예를 들어 **콘텐츠 크기(KB)** 필터를 **< 2048**로 설정하여 2MB보다 작은 크기의 소프트웨어 업데이트만 다운로드할 수 있습니다. 이 필터를 사용하면 큰 소프트웨어 업데이트가 자동으로 다운로드되는 것이 방지되므로 네트워크 대역폭이 제한된 경우 단순화된 Windows 하위 수준 서비스를 보다 잘 지원할 수 있습니다. 자세한 내용은 [Configuration Manager and Simplified Windows Servicing on Down Level Operating Systems](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)(Configuration Manager 및 하위 수준 운영 체제의 단순화된 Windows 서비스)를 참조하세요.

#### <a name="to-configure-the-content-size-field"></a>콘텐츠 크기 필드를 구성하려면
**콘텐츠 크기(KB)** 필드를 구성하려면 ADR을 만들 때 자동 배포 규칙 만들기 마법사의 **소프트웨어 업데이트** 페이지로 이동하거나 기존 ADR의 속성에 있는 **소프트웨어 업데이트** 탭으로 이동합니다.

![콘텐츠 크기 필드](media/contentsizefield.png)

## <a name="improved-functionality-for-required-software-dialogs"></a>필수 소프트웨어 대화 상자에 대한 향상된 기능
사용자가 필수 소프트웨어를 받으면 **다음 시간 후 다시 알림** 설정에서 다음 드롭다운 값 목록을 선택할 수 있습니다.
- 나중에: 클라이언트 에이전트 설정에 구성된 알림 설정에 따라 알림을 예약합니다.
- 고정 시간: 선택한 시간 후에 다시 표시하도록 알림을 예약합니다. 예를 들어 사용자가 30분을 선택하면 알림이 30분 후에 다시 표시됩니다.

![클라이언트 에이전트 설정의 컴퓨터 에이전트 페이지](media/computeragentsettings.png)

최대 다시 알림 시간은 항상 배포 타임라인을 따라 클라이언트 에이전트 설정에 구성된 알림 값을 기반으로 합니다. 예를 들어 컴퓨터 에이전트 페이지의 **배포 최종 기한이 24시간 미만 남은 경우 사용자에게 다음 시간마다 미리 알림(시)** 설정이 10시간으로 구성되고 대화 상자가 실행되기까지 남은 마감일이 24시간보다 큰 경우 사용자에게 일련의 다시 알림 옵션이 표시되지만 10시간 이하여야 합니다. 마감일이 가까워지면 대화 상자에게 몇 가지 옵션이 나타나는데 이 옵션은 배포 타임라인의 각 구성 요소와 관련된 클라이언트 에이전트 설정과 일치합니다.

또한 운영 체제를 배포하는 작업 순서 등 고위험성 배포의 경우 최종 사용자 알림 환경의 침투성이 더 높아졌습니다. 사용자에게 중요 소프트웨어 유지 관리 알림을 표시해야 할 때마다 임시 작업 표시줄 알림 대신 다음과 같은 대화 상자가 사용자 컴퓨터에 표시됩니다.

![필수 소프트웨어 대화 상자](media/requiredsoftwaredialog.png)


자세한 내용을 보려면 다음을 수행하십시오.
- [높은 위험 수준의 배포를 관리하는 설정](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [클라이언트 설정을 구성하는 방법](../clients/deploy/configure-client-settings.md)

## <a name="deny-previously-approved-application-requests"></a>이전에 승인된 응용 프로그램 요청 거부

관리자는 이제 이전에 승인된 응용 프로그램 요청을 거부할 수 있습니다. 요청이 거부된 응용 프로그램을 나중에 설치하려면 요청을 다시 제출해야 합니다. 요청을 거부해도 응용 프로그램이 제거되지는 않으며 해당 응용 프로그램에 대한 해당 사용자의 새 요청을 다시 승인하도록 합니다. 이전에는 승인되지 않은 응용 프로그램 요청에 대해서만 응용 프로그램 요청을 거부할 수 있었습니다.

#### <a name="try-it-out"></a>기능 직접 사용해 보기
승인된 응용 프로그램 요청을 거부하려면:

1.  Configuration Manager 콘솔에서 승인이 필요한 [응용 프로그램을 만들고 배포합니다](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/create-applications).
2.  클라이언트 컴퓨터에서 소프트웨어 센터를 열고 응용 프로그램에 대한 요청을 제출합니다.
3.  Configuration Manager 콘솔에서 응용 프로그램 요청을 승인합니다.
4.  승인된 응용 프로그램 요청 거부: Configuration Manager 콘솔에서 **소프트웨어 라이브러리** > **개요** > **응용 프로그램 관리** > **승인 요청**으로 이동한 다음 거부할 응용 프로그램 요청을 선택합니다.  리본에서 **거부**를 클릭합니다.

## <a name="exclude-clients-from-automatic-upgrade"></a>자동 업그레이드에서 클라이언트 제외
Technical Preview 1610에는 업데이트된 클라이언트 버전을 자동으로 설치하지 않도록 제외할 클라이언트 컬렉션을 지정할 수 있는 설정이 새로 추가되었습니다.  이 설정은 자동 업그레이드 및 소프트웨어 업데이트 기반 업그레이드, 로그온 스크립트 및 그룹 정책 등에 적용됩니다. 클라이언트를 업그레이드할 때 주의가 필요한 컴퓨터 컬렉션에 이 설정을 사용할 수 있습니다. 제외된 컬렉션에 있는 클라이언트는 업데이트된 클라이언트 소프트웨어 설치 요청을 무시합니다.

### <a name="configure-exclusion-from-automatic-upgrade"></a>자동 업그레이드 작업의 제외 구성
자동 업그레이드 제외를 구성하려면:
1.  Configuration Manager 콘솔에서 **관리 > 사이트 구성 > 사이트** 아래의 **계층 설정**을 열고 **클라이언트 업그레이드** 탭을 선택합니다.
2.  **Exclude specified clients from upgrade**(지정된 클라이언트를 업그레이드에서 제외)의 확인란을 선택하고 **Exclusion collection**(제외 컬렉션)에서 제외할 컬렉션을 선택합니다. 제외할 컬렉션은 하나만 선택할 수 있습니다.
3.  **확인**을 클릭하여 구성을 닫고 저장합니다. 그러면 클라이언트가 정책을 업데이트한 후 제외된 컬렉션의 클라이언트가 클라이언트 소프트웨어에 대한 업데이트를 더 이상 자동으로 설치하지 않습니다.

  ![자동 업그레이드 제외에 대한 설정](media/automatic_upgrade_exclusion.png)

> [!NOTE]
> 사용자 인터페이스에는 어떠한 방법으로도 클라이언트가 업그레이드되지 않는다고 명시되어 있지만 두 가지 방법을 통해 이러한 설정을 재정의할 수 있습니다. 클라이언트 강제 설치 및 수동 클라이언트 설치를 사용하여 이 구성을 재정의할 수 있습니다. 자세한 내용은 다음 섹션을 참조하세요.

### <a name="how-to-upgrade-a-client-that-is-in-an-excluded-collection"></a>제외된 컬렉션에 있는 클라이언트를 업그레이드하는 방법
컬렉션이 제외되도록 구성하면 해당 컬렉션의 멤버가 다음 두 가지 방법 중 하나를 사용하여 제외를 재정의해야만 클라이언트 소프트웨어를 업그레이드할 수 있습니다.
 - **클라이언트 강제 설치** – 클라이언트 강제 설치를 사용하여 제외된 컬렉션에 있는 클라이언트를 업그레이드할 수 있습니다. 이 방법은 관리자의 의도인 것으로 간주되고 전체 컬렉션을 제외에서 제거하지 않고 클라이언트를 업그레이드할 수 있습니다.       
 - **수동 클라이언트 설치** – ccmsetup과 명령줄 스위치 ***/ignoreskipupgrade***를 함께 사용하면 제외된 컬렉션에 있는 클라이언트를 수동으로 업그레이드할 수 있습니다.

  제외된 컬렉션의 멤버인 클라이언트를 수동으로 업그레이드할 때 이 스위치를 사용하지 않으면 새 클라이언트 소프트웨어가 설치되지 않습니다. 자세한 내용은 [Configuration Manager 클라이언트를 수동으로 설치하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-configuration-manager-clients-manually)을 참조하세요.

클라이언트 설치 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Windows 컴퓨터에 클라이언트를 배포하는 방법](/sccm/core/clients/deploy/deploy-clients-to-windows-computers)을 참조하세요.

## <a name="windows-defender-configuration-settings"></a>Windows Defender 구성 설정

이제 Configuration Manager 콘솔에서 구성 항목을 사용하여 Intune에 등록된 Windows 10 컴퓨터에 대한 Windows Defender 클라이언트 설정을 구성할 수 있습니다.

특히 다음과 같은 Windows Defender 설정을 구성할 수 있습니다.
- 실시간 모니터링 허용
- 동작 모니터링 허용
- 네트워크 검사 시스템 사용
- 모든 다운로드 검색
- 스크립트 검사 허용
- 파일 및 프로그램 활동 모니터링
  - 모니터링되는 파일
- 해결된 맬웨어 추적 일수
- 클라이언트 UI 액세스 허용
- 시스템 검색 예약
  - 예약일
  - 예약 시간
- 매일 빠른 검색 예약
  - 예약 시간
- 검색하는 동안 CPU 사용(%) 제한 보관 파일 검색
- 전자 메일 메시지 검색
- 이동식 드라이브 검색
- 매핑된 드라이브 검색
- 네트워크 공유에서 열린 파일 검색
- 서명 업데이트 간격
- 클라우드 보호 허용
- 사용자에게 샘플 확인
- 사용자 동의 없이 설치된 응용 프로그램 검색
- 제외된 파일/폴더
- 제외된 파일 확장명
- 제외된 프로세스

> [!NOTE]
> 이러한 설정은 Windows 10 년 11월 업데이트(1511) 이상을 실행하는 클라이언트 컴퓨터에서만 구성할 수 있습니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

1.  Configuration Manager 콘솔에서 **자산 및 호환성** > **개요** > **준수 설정** > **구성 항목**으로 이동한 다음 새 **구성 항목**을 만듭니다.
2.  이름을 입력하고 **Configuration Manager 클라이언트를 사용하지 않고 관리되는 장치에 대한 설정**에서 **Windows 8.1 및 Windows 10**을 선택하고 **다음**을 클릭합니다.
3.  **지원되는 플랫폼** 페이지에서 **모든 Windows 10(64비트)** 및 **모든 Windows 10(32비트)**가 선택되었는지 확인하고 **다음**을 클릭합니다.
4.  **Windows Defender** 설정 그룹을 선택하고 **다음**을 클릭합니다.
5.  이 페이지에서 원하는 설정을 구성하고 **다음**을 클릭합니다.
6.  마법사를 완료합니다.
7.  구성 기준에 이 구성 항목을 추가하고 Windows 10 11월 업데이트(1511) 이상을 실행하는 컴퓨터에 이 기준을 배포합니다.

> [!NOTE]
> 구성 기준을 배포할 때 **비호환 설정 재구성** 확인란을 선택해야 합니다.

## <a name="request-policy-sync-from-administrator-console"></a>관리자 콘솔에서 정책 동기화 요청

이제 장치 자체에서 동기화를 요청할 필요 없이 Configuration Manager 콘솔에서 모바일 장치에 대한 정책 동기화를 요청할 수 있습니다. 동기화 요청 상태 정보는 장치 뷰에서 **원격 동기화 상태**라는 새 열로 제공됩니다. 상태는 각 모바일 장치에 대한 **속성** 대화 상자의 **검색 데이터** 섹션에도 표시됩니다.

### <a name="try-it-out"></a>기능 직접 사용해 보기

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > 장치로 이동합니다.
2.  **원격 장치 작업** 메뉴에서 **동기화 요청 보내기**를 선택합니다.

동기화는 5~10분 정도 걸릴 수 있습니다. 정책의 모든 변경 내용이 장치에 동기화됩니다. **장치** 보기의 **원격 동기화 상태** 열이나 장치의 **속성** 대화 상자에서 동기화 요청 상태를 추적할 수 있습니다.

## <a name="additional-security-role-support"></a>추가 보안 역할 지원

이제는 전체 관리자 권한 외에 다음과 같은 기본 제공 보안 역할도 **회사가 소유한 모든 장치** 노드의 항목(**미리 선언된 장치**, **iOS 등록 프로필**, **Windows 등록 프로필** 포함)에 대한 모든 권한을 소유합니다. •   **자산 관리자** •   **회사 리소스 액세스 관리자**

**읽기 전용 분석가** 역할에는 이러한 Configuration Manager 콘솔 영역에 대한 읽기 전용 권한이 계속 부여됩니다.

## <a name="conditional-access-for-windows-10-vpn-profiles"></a>Windows 10 VPN 프로필에 대한 조건부 액세스

이제 Azure Active Directory에 등록된 Windows 10 장치가 Configuration Manager 콘솔에서 작성된 Windows 10 VPN 프로필을 통해 VPN에 액세스하려면 규정을 준수해야 하도록 지정할 수 있습니다. 이렇게 하려면 Windows 10 VPN 프로필의 VPN 프로필 속성과 VPN 프로필 마법사의 **인증 방법** 페이지에서 새로운 **이 VPN 연결에 조건부 액세스 사용** 확인란을 사용합니다. 프로필에 대한 조건부 액세스를 사용하도록 설정하는 경우 SSO(Single Sign-On) 인증용으로 별도의 인증서를 지정할 수도 있습니다.

## <a name="see-also"></a>참고 항목
[System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)



<!--HONumber=Dec16_HO3-->


