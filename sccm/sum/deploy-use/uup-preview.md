---
title: UUP 미리 보기
titleSuffix: Configuration Manager
description: UUP 통합 미리 보기 지침
ms.date: 02/19/2019
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 0b0da585-0096-410b-8035-6b7a312f37f5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: ece763244ffbd1ebaabd2c85d92697683eea8732
ms.sourcegitcommit: e7e5ca04601270ea7af90183123d5db1d42784da
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56422190"
---
# <a name="uup-private-preview-instructions"></a>UUP 비공개 미리 보기 지침

> [!Note]  
> 이 정보는 정식으로 출시되기 전에 대폭 수정될 수 있는 미리 보기 기능과 관련이 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

## <a name="benefits"></a>이점

### <a name="feature-updates"></a>기능 업데이트

Windows 10 UUP(통합 업데이트 플랫폼)를 통한 기능 업데이트는 현재 서비스를 제공할 때 고객에게 발생하는 여러 가지 문제를 완화하도록 설계되었습니다. 다음을 포함한 UUP 기능 업데이트를 사용해 보세요.

- 최신 보안 규정 준수 수준으로 바로 업그레이드합니다. 그러면 규정을 준수하기 위해 업그레이드하는 즉시 더 이상 보안 업데이트를 설치할 필요가 없습니다. 매월 최신 누적 보안 업데이트가 포함된 새로운 기능 업데이트가 게시됩니다. 매월 대부분의 기능 업데이트 콘텐츠를 다시 다운로드하거나 배포하지 않고 누적 업데이트와도 공유되는 보안 업데이트 구성 요소만 배포하면 됩니다.

- 모든 FOD(주문형 기능) 및 언어 팩은 업그레이드 프로세스 중에 유지되고 손실되지 않아야 합니다.

- UUP를 통한 기능 업데이트는 기본 설치 파일을 지원하므로 각 클라이언트에서 다운로드해야 하는 콘텐츠의 양을 줄일 수 있습니다.

UUP에 대한 자세한 내용은 Windows 블로그 게시물 [UUP(통합 업데이트 플랫폼) 업데이트](https://blogs.windows.com/windowsexperience/2017/03/02/an-update-on-our-unified-update-platform-uup/)를 참조하세요.


### <a name="cumulative-updates"></a>누적 업데이트

- UUP를 통한 누적 업데이트를 사용하면 FOD 및 언어 팩의 콘텐츠를 오프라인으로 배포할 수 있으므로 인터넷으로 이동하거나 관리자가 지루하게 작업을 준비할 필요 없이 최종 사용자가 필요할 때 이를 얻을 수 있습니다.

- UUP를 통한 누적 업데이트에는 월간 누적 보안 업데이트와 함께 서비스 스택 업데이트가 포함됩니다. UUP를 통한 누적 업데이트를 통해 이러한 두 업데이트의 오케스트레이션 문제를 해결할 수 있습니다. 관계를 관리하고 오케스트레이션할 필요 없이, UUP를 통한 누적 업데이트에서 서비스 스택 업데이트가 누적 업데이트 설치를 위해 준비가 되어 있는지 확인합니다.



## <a name="set-up-instructions"></a>설치 지침

### <a name="1-send-your-wsus-id-to-your-uup-preview-contact-at-microsoft"></a>1. Microsoft의 UUP 미리 보기 담당자에게 WSUS ID 보내기

UUP 비공개 미리 보기에 참여하려면 WSUS ID를 Microsoft와 공유하여 해당 환경을 미리 보기의 허용 목록에 추가해야 합니다. 이 ID가 없으면 미리 보기가 공개될 때까지 UUP 업데이트를 볼 수 없습니다.

WSUS ID를 검색하려면 다음을 수행합니다.

```PowerShell
$server = Get-WsusServer
$config = $server.GetConfiguration()
$config.ServerId

# also check MUUrl
$config.MUUrl
```

**MUUrl** 속성은 `https://sws.update.microsoft.com`이어야 합니다. 변경하려면 다음 지원 문서에서 해결 방법을 참조하세요. [SoapException으로 인해 WSUS 동기화 실패](https://support.microsoft.com/help/4482416/wsus-synchronization-fails-with-soapexception)


### <a name="2-update-configmgr"></a>2. ConfigMgr 업데이트

Configuration Manager 사이트에 다음 변경을 수행하여 이 UUP 미리 보기를 지원합니다.


#### <a name="diagnostics-and-usage-data-level"></a>진단 및 사용량 데이터 수준
이 미리 보기 기간 동안 Configuration Manager 진단 및 데이터 사용량 수준을 증가하는 것이 좋습니다. **전체** 수준을 통해 Microsoft에서는 이 새로운 기능으로 문제를 효과적으로 분석하고 해결합니다. 자세한 내용은 [버전 1810의 진단 사용량 데이터 수집 수준](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1810)을 참조하세요.


#### <a name="update-rollup-for-configmgr-1810-4486457"></a>ConfigMgr 1810(4486457)에 대한 업데이트 롤업

1. 버전 1810에 대한 업데이트 롤업을 사용하여 사이트를 업데이트합니다. 자세한 내용은 [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)를 참조하세요.  

2. 클라이언트 업데이트  

    - 이 프로세스를 간소화하려면 자동 클라이언트 업그레이드를 사용하는 것이 좋습니다. 자세한 내용은 [클라이언트 업그레이드](/sccm/core/clients/manage/upgrade/upgrade-clients#automatic-client-upgrade)를 참조하세요.  

    - UUP 업데이트를 대상으로 하는 모든 클라이언트는 **약 6GB의 사용되지 않은 콘텐츠를 클라이언트에 불필요하게 다운로드하지 않도록** 업그레이드해야 합니다.

이 업데이트에 대한 자세한 내용은 [System Center Configuration Manager 현재 분기 버전 1810에 대한 업데이트 롤업](https://support.microsoft.com/help/4486457)을 참조하세요.


<!-- 
#### 1812 Technical Preview
The 1812 Technical Preview is equivalent in supported UUP scenarios to the ConfigMgr 1810 UUP Hotfix (KB4482615).

The only note is that client upgrade of 1812 Technical Preview is broken from 1810.1 TP or 1811 TP. To work around this issue, you'll need to uninstall 1810.1 TP and 1811 TP clients, then install the 1812 TP client cleanly. All clients you target UUP updates to must be on 1812 Technical Preview (or later) to prevent **unnecessarily downloading around 6 GB** of unused content to the client.
 -->


### <a name="3-update-windows-clients-to-supported-versions"></a>3. Windows 클라이언트를 지원되는 버전으로 업데이트

#### <a name="for-express-installation-file-sync"></a>기본 설치 파일 동기화인 경우
기본 콘텐츠의 경우 지원되는 Windows 버전은 다음과 같습니다.

- **Windows 10 버전 1809**(1월 22일 릴리스된 비보안 누적 업데이트 [KB4476976](https://support.microsoft.com/help/4476976/windows-10-update-kb4476976) 이상). 이 업데이트는 카탈로그에서만 제공되며 WSUS와 직접 동기화되지 않습니다. 업데이트를 배포하기 위해 환경으로 가져오려면 [Microsoft 업데이트 카탈로그에서 업데이트 가져오기](/sccm/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)를 참조하세요.

- **Windows 10 버전 1803**([KB4284835](https://support.microsoft.com/help/4284835)(2017년 6월 누적 보안 업데이트)) 이상  

- **Windows 10 버전 1709**([KB4338825](https://support.microsoft.com/help/4338825)(2017년 7월 누적 보안 업데이트)) 이상  


#### <a name="for-non-express-installation-file-sync"></a>기본 이외의 설치 파일 동기화인 경우
기본 이외의 콘텐츠의 경우 추가 패치를 적용해야 합니다. 이 업데이트는 약 6GB의 사용되지 않은 콘텐츠를 불필요하게 클라이언트로 다운로드하지 않도록 방지하는 데 중요합니다. 지원되는 Windows 버전에는 다음 빌드가 포함됩니다.

- **Windows 10 버전 1809**(1월 22일 릴리스된 비보안 누적 업데이트 [KB4476976](https://support.microsoft.com/help/4476976/windows-10-update-kb4476976) 이상). 이 업데이트는 카탈로그에서만 제공되며 WSUS와 직접 동기화되지 않습니다. 업데이트를 배포하기 위해 환경으로 가져오려면 [Microsoft 업데이트 카탈로그에서 업데이트 가져오기](/sccm/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)를 참조하세요.


- **Windows 10 버전 1803** 및 **Windows 10 버전 1709** 클라이언트에는 기본 누적 업데이트 수준과 비누적 업데이트가 있어야 합니다.
    - 누적 업데이트
        - 1803: [KB4284835](https://support.microsoft.com/help/4284835)(2017년 6월 누적 보안 업데이트) - 2019년 1월 누적 보안 업데이트 포함
        - 1709: [KB4338825](https://support.microsoft.com/help/4338825)(2017년 7월 누적 보안 업데이트) - 2019년 1월 누적 보안 업데이트 포함
    - 비누적 업데이트 이 업데이트는 카탈로그에서만 제공되며 WSUS와 직접 동기화되지 않습니다. 업데이트를 배포하기 위해 환경으로 가져오려면 [Microsoft 업데이트 카탈로그에서 업데이트 가져오기](/sccm/sum/get-started/synchronize-software-updates#import-updates-from-the-microsoft-update-catalog)를 참조하세요.
        - 1803: [KB4483541](https://support.microsoft.com/help/4483541)
        - 1709: [KB4483530](https://support.microsoft.com/help/4483530)


### <a name="4-enable-express-installation-on-clients-in-client-settings"></a>4. 클라이언트 설정에서 클라이언트에 기본 설치를 사용하도록 설정

기본 설치를 사용하도록 설정하는 클라이언트 설정은 기본 콘텐츠의 동기화 여부와 상관없이 UUP 업데이트에 대해 설정해야 합니다. 이 설정을 사용하면 ConfigMgr에서 UUP 업데이트와 관련된 모든 콘텐츠를 다운로드하지 않고 WUA(Windows 업데이트 에이전트)를 통해 클라이언트에 다운로드하는 데 필요한 콘텐츠를 결정할 수 있습니다. 선택적 FOD 및 언어 팩 콘텐츠가 있으므로 이 설정은 기본 이외의 시나리오에도 필요합니다. 이로 인해 업데이트와 관련된 모든 클라이언트에서 필요하지 않은 의미 없는 양의 추가 데이터가 발생합니다.

이 설정을 사용하도록 설정하면 서버 콘텐츠 다운로드에는 영향을 주지 않고 클라이언트 다운로드 동작에만 영향을 줍니다. 이 설정을 아직 사용하도록 설정하지 않은 경우 이렇게 설정하기 전에 위에서 설명한 ConfigMgr 및 Windows 클라이언트 버전이 있어야 합니다. 이러한 버전은 WSUS에서 업데이트 승인과 직접 관련된 일부 호환성 문제를 해결하고, 기본 콘텐츠가 동기화되지 않는 경우에도 ConfigMgr에서 UUP 업데이트를 위해 이 채널을 사용할 수 있도록 하기 때문입니다.

클라이언트에 기본 설치를 사용하도록 설정하려면 다음을 수행합니다.

1. Configuration Manager 콘솔에서 **관리** \ **클라이언트 설정**으로 차례로 이동합니다.  

2. 사용하려는 [클라이언트 설정]의 [속성]을 열거나 필요에 따라 배포할 새 속성을 적절히 만듭니다.  

3. **소프트웨어 업데이트** 그룹 아래에서 **클라이언트에서 기본 설치 파일 설치 사용**을 **예**로 설정합니다.

![소프트웨어 업데이트 그룹에서 강조 표시된 클라이언트 설정](../media/uup-preview-client-settings.png)


### <a name="5-make-sure-your-adrs-are-set-as-desired"></a>5. ADR이 원하는 대로 설정되었는지 확인 

UUP 업데이트 동기화를 사용하도록 설정하기 전에 ADR(자동 배포 규칙) 및 사용하고 있는 다른 업데이트 인프라를 고려합니다. 이러한 업데이트가 기존 ADR 및 설치 계획의 일부로 자동으로 배포되지 않도록 하려면 ADR을 업데이트하여 해당 업데이트를 정리해야 합니다. [동기화된 UUP 업데이트를 찾는 방법](#how-to-find-synced-uup-updates)을 참조하세요. 기존 설치 계획은 기본적으로 UUP가 아닌 업데이트 인프라만 배포하지만 이 동작을 변경하도록 업데이트할 수 있습니다.

또한 이러한 업데이트가 동기화를 통해 규정 준수 보고서 또는 다른 인프라에 영향을 주고 원하는 대로 미리 수정할 수 있는지도 고려합니다. 예를 들어 모든 제품에서 규정 준수를 측정하면 UUP 및 UUP 이외의 Windows 10 누적 업데이트가 모두 준수 또는 비준수로 표시되어 번호가 왜곡됩니다.



## <a name="enable-uup-and-start-testing"></a>UUP 사용 및 테스트 시작

### <a name="select-products-and-classifications-to-sync"></a>동기화할 제품 및 분류 선택

UUP 업데이트를 동기화하고 사용해 볼 준비가 되면 WSUS에서 파일럿을 볼 수 있도록 설정했다는 알림을 Microsoft로부터 받습니다. 그러면 새 제품을 사용하도록 설정합니다.

1. [소프트웨어 업데이트 동기화](/sccm/sum/get-started/synchronize-software-updates)를 통한 새 제품 채우기  

2. Configuration Manager 콘솔에서 **관리** \ **사이트 구성** \ **사이트**로 차례로 이동합니다.  

3. CAS(중앙 관리 사이트) 또는 독립 실행형 기본 사이트 중 하나인 최상위 사이트 선택  

4. **사이트 구성 요소 구성** \ **소프트웨어 업데이트 지점**을 차례로 엽니다.  

5. WSUS 서버가 미리 보기에 추가되면 **제품** 탭에 두 개의 새 제품이 표시됩니다. 이러한 제품에는 미리 보기 UUP 콘텐츠가 포함되어 있습니다.  

    - **Windows 10 UUP 미리 보기**  
    - **Windows Server UUP 미리 보기**  

6. **분류** 탭에서 다음을 선택합니다.  

    - **보안 업데이트**: UUP 누적 업데이트를 보려면  
    - **업그레이드**: UUP 기능 업데이트를 보려면  

7. 소프트웨어 업데이트를 동기화하여 새 UUP 업데이트를 확인합니다.


### <a name="how-to-find-synced-uup-updates"></a>동기화된 UUP 업데이트를 찾는 방법

UUP 업데이트가 환경에 동기화되면 해당 UUP 업데이트를 찾아서 테스트할 수 있습니다. Configuration Manager 콘솔 내에서 미리 보기 업데이트를 쉽게 찾을 수 있는 두 가지 방법이 있습니다.

- 이러한 미리 보기 업데이트는 별도의 제품에 있으므로 언제든지 해당 제품을 사용하여 이러한 업데이트를 필터링하거나 찾을 수 있습니다. UUP 또는 UUP 이외의 기능 업데이트를 배포할지 여부를 선택할 수 있도록 제품 필터가 설치 계획에 추가되었습니다.  

- ADR의 필터뿐만 아니라 소프트웨어 라이브러리의 **모든 소프트웨어 업데이트** 및 **모든 Windows 10 업데이트** 노드에도 새로운 선택적인 **태그** 열이 있습니다. 이 필드는 UUP 업데이트인 경우 **UUP**로 설정되고, UUP 이외의 업데이트인 경우 비어 있습니다.  


### <a name="updates-available-during-preview"></a>미리 보기 동안 사용 가능한 업데이트

- Windows 10 1809 누적 업데이트
    - 2월 보안 업데이트(2월 12일)  

- Windows 10 1803 누적 업데이트
    - 12월 보안 업데이트(12월 11일)
    - 1월 보안 업데이트(1월 8일)
    - 1월 비보안 업데이트(1월 15일)
    - 2월 보안 업데이트(2월 12일)  

- Windows 10 1709 누적 업데이트
    - 12월 보안 업데이트(12월 11일)
    - 1월 보안 업데이트(1월 8일)
    - 1월 비보안 업데이트(1월 15일)
    - 2월 보안 업데이트(2월 12일)  

- Windows 10 1809 기능 업데이트(1709 또는 1803)
    - 12월 보안 업데이트 규정 준수(12월 11일)
    - 1월 보안 업데이트 규정 준수(1월 8일)
    - 2월 보안 업데이트 규정 준수(2월 12일)  

- Windows 10 1803 기능 업데이트(1709 또는 1803)   
    - 12월 보안 업데이트 규정 준수(12월 11일)
    - 1월 보안 업데이트 규정 준수(1월 8일)
    - 2월 보안 업데이트 규정 준수(2월 12일)  

UUP가 아직 미리 보기(비공개 또는 공개)로 있는 한 필요한 경우 3월 및 향후 보안 업데이트가 이러한 모든 영역에 계속 게시될 예정입니다. 미리 보기기 완성되면 프로덕션 환경에서 Windows 10 버전 1809 누적 업데이트 및 Windows 10 버전 1803 기능 업데이트만 지원됩니다.


### <a name="scenarios-to-try"></a>시도 중인 시나리오

#### <a name="feature-updates"></a>기능 업데이트
- 선택한 보안 규정 준수 수준으로 바로 업그레이드합니다.  

- 업그레이드 전에 설치된 FOD 및 언어 팩으로 업그레이드하더라도 업그레이드에서 이러한 구성 요소를 유지합니다.  

- 필요에 따라 기능 업데이트에 대한 기본 설치 파일 동기화를 사용하도록 설정하여 각 클라이언트에서 다운로드해야 하는 콘텐츠의 양을 줄입니다.  

    > [!Note]  
    > 이 클라이언트 혜택으로 인해 누적 업데이트에 대한 기본 설치 파일의 경우와 같이 더 큰 서버 다운로드 및 배포에 대한 비용이 발생합니다.  

#### <a name="cumulative-updates"></a>누적 업데이트
미리 보기 동안 여러 연속 업데이트에 UUP 유형 업데이트를 사용하여 클라이언트를 준수 상태로 계속 유지함으로써 진행 중인 기대 수준을 느껴보세요.

#### <a name="content"></a>Content
이전에 UUP 이외의 업데이트에서 확인한 것과 비교해 볼 때 각 주요 버전(1809, 1803, 1709), 아키텍처 및 언어 조합에 대한 첫 번째 업데이트는 파일 수와 디스크 공간 모두에서 큰 것으로 나타납니다. 이 추가 콘텐츠는 주로 누적 업데이트에 대한 모든 FOD 및 언어 팩에 사용됩니다. 기능 업데이트의 경우, 특히 기본 설치를 사용하도록 설정된 경우 첫 번째 업데이트에는 대규모의 추가 콘텐츠가 있습니다. 

그러나 모든 FOD 및 언어 팩 콘텐츠는 다시 다운로드되거나 재배포되지 않고 업데이트 전반에 지능적으로 공유되므로 후속 업데이트(누적 업데이트와 높은 규정 준수 수준의 월별 기능 업데이트 모두 해당)를 통해 다운로드하고 배포해야 하는 새 콘텐츠의 양이 훨씬 적습니다. 1709 및 1803의 미리 보기 동안 이 월별 다운로드는 UUP 이외의 시나리오에서 볼 수 있는 누적 업데이트의 크기와 거의 같습니다. 그러나 1809에서는 누적 업데이트의 증분 다운로드가 매월 훨씬 더 적으므로 스토리가 훨씬 향상됩니다. 

비기본 설치에 대해 12개월 동안 다운로드하고 배포한 전체 콘텐츠 크기를 살펴볼 때 UUP가 없는 1803은 UUP가 있는 1809와 거의 같아야 하며, 이 티핑 포인트 이후에는 릴리스의 전체 수명 동안 UUP가 있는 1809에서 다운로드되고 배포되는 전체 콘텐츠 크기가 더 작습니다. 기본 설치의 경우 티핑 포인트는 1809에서와 같이 더 빠르고 기본 설치가 기능 업데이트(누적 업데이트 아님)에만 적용되므로 기본 설치의 대규모 서버 콘텐츠에 대한 비용은 월별 기준이 아니라 릴리스당 한 번만 발생합니다.

#### <a name="supported-content-channels"></a>지원되는 콘텐츠 채널
미리 보기에서는 실제 엔터프라이즈 환경에서 사용할 기능을 테스트합니다. UUP는 다음을 포함한 모든 콘텐츠 채널을 지원합니다.
- Windows 배달 최적화
- Configuration Manager 피어 캐시
- Windows BranchCache
- Microsoft 업데이트에서 직접 다운로드하려면 서버로 다운로드하지 않고 배포합니다(배포 패키지 없음). 사용하고 있는 경우 전송 최적화를 함께 사용하는 것이 좋습니다.
- 타사 대체 콘텐츠 공급자

자세한 내용은 [Windows 10 업데이트 배달 최적화](/sccm/sum/deploy-use/optimize-windows-10-update-delivery)를 참조하세요.


## <a name="known-issues"></a>알려진 문제

### <a name="additional-resources-are-required-on-wsus"></a>WSUS에는 추가 리소스가 필요합니다.
UUP 업데이트를 동기화할 때, 특히 처음인 경우 WSUS 서버에 추가 리소스가 필요합니다. 이 동작으로 인해 상위 WSUS 서버와의 업데이트 동기화 또는 하위 수준 서버에 대한 계층 동기화가 차단되는 경우가 있습니다.

이 문제는 WSUS에서 동기화 실패로 매니페스트됩니다. Configuration Manager는 또한 동기화 실패로 표시합니다.

#### <a name="workaround"></a>해결 방법
최상위 WSUS 서버 또는 계층의 부모 WSUS 서버에서 다음과 같이 변경합니다.
1. ServerSyncWebService 시간 제한 증가 

    1. `C:\Program Files\Update Services\WebServices\serversyncwebservice\web.config`의 백업 복사본을 다른 이름으로 만들기  

    2. 메모장에서 `C:\Program Files\Update Services\WebServices\serversyncwebservice\web.config` 열기  

    3. 예를 들어 **executionTimeout** 특성을 추가하여 **httpRunTime**을 수정합니다.  

        `<httpRuntime maxRequestLength="4096" executionTimeout="3600" />`  

    4. web.config를 다른 위치에 저장합니다. 구성 파일은 일반적으로 파일의 소유권을 획득하지 않고 편집할 수 없기 때문에 이 단계가 필요합니다.  

    5. 그런 다음, 수정된 web.config를 `C:\Program Files\Update Services\WebServices\serversyncwebservice` 디렉터리로 복사하여 이전 버전을 대체합니다.  

    6. 관리자 권한 명령 프롬프트에서 IIS(`IISReset`)를 다시 시작합니다.  

        > [!Note]  
        > 이 작업은 IIS 서버를 일시적으로 중지합니다.

2. WSUS 서버용 앱 풀 메모리를 늘립니다.  

    1. IIS Manager> 애플리케이션 풀 > WsusPool 선택으로 이동하여 오른쪽 창의 **고급 설정**을 선택합니다.  

    2. **전용 메모리** 및 **가상 메모리** 제한 모두를 `0`로 설정합니다.

