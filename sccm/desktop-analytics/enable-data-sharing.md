---
title: 데이터 공유를 사용하도록 설정
titleSuffix: Configuration Manager
description: Desktop Analytics와 진단 데이터를 공유하는 방법에 대한 참조 가이드입니다.
ms.date: 10/28/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: be680198-4cea-4378-a686-d52f382ba483
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f8b21f1fcc702190322c97ed36333bd612ae3984
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74734616"
---
# <a name="enable-data-sharing-for-desktop-analytics"></a>Desktop Analytics에 데이터 공유 사용

Desktop Analytics에 디바이스를 등록하려면 Microsoft에 진단 데이터를 전송해야 합니다. 환경에서 프록시 서버를 사용하는 경우 이 정보를 사용하여 프록시를 구성합니다.


## <a name="diagnostic-data-levels"></a>진단 데이터 수준

![Desktop Analytics의 진단 데이터 수준 다이어그램](media/diagnostic-data-levels.png)

Desktop Analytics와 Configuration Manager를 통합하는 경우 이를 사용하여 디바이스에서 진단 데이터 수준을 관리할 수도 있습니다. 최상의 환경을 위해 Configuration Manager를 사용합니다.

> [!Important]  
> 대부분의 경우 Configuration Manager만 사용하여 이러한 설정을 구성합니다. 도메인 그룹 정책 개체에도 이러한 설정을 적용하지 마십시오. 자세한 내용은 [충돌 해결](/configmgr/desktop-analytics/enroll-devices#conflict-resolution)을 참조하세요.

Desktop Analytics의 기본 기능은 **기본** [진단 데이터 수준](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization#diagnostic-data-levels)에서 작동합니다. Configuration Manager에서 **강화(제한됨)** 수준을 구성하지 않으면 Desktop Analytics의 다음 기능이 제공되지 않습니다.

- 앱 사용량
- [추가 앱 인사이트](https://docs.microsoft.com/sccm/desktop-analytics/compat-assessment#additional-insights)
- 배포 상태 데이터
- 상태 모니터링 데이터

Microsoft는 Desktop Analytics로 **강화(제한됨)** 진단 데이터 수준을 사용하도록 설정하여 얻을 수 있는 이점을 최대화하는 것을 권장합니다. 

> [!Tip]
> Configuration Manager에서 **강화(제한됨)** 설정은 Windows 10, 버전 1709 이상을 실행하는 디바이스에서 **Windows Analytics 정책에 필요한 최소 수준으로 고급 진단 데이터 제한**과 동일한 설정입니다. 
>
> Windows 10, 버전 1703 및 이전 버전, Windows 8.1 또는 Windows 7을 실행하는 디바이스에는 이 정책 설정이 없습니다. Configuration Manager에서 **강화(제한됨)** 설정을 구성할 때 이러한 디바이스는 **기본** 수준으로 대체됩니다.
>
> Windows 10, 버전 1709를 실행하는 디바이스에는 이 정책 설정이 있습니다. 그러나 Configuration Manager에서 **강화(제한됨)** 설정을 구성할 때 이러한 디바이스도 **기본** 수준으로 대체됩니다.

**강화(제한됨)** 가 포함된 Microsoft와 공유되는 진단 데이터에 대한 자세한 내용은 [Windows 10 고급 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/windows/privacy/enhanced-diagnostic-data-windows-analytics-events-and-fields)를 참조하세요.

> [!Important]   
> Microsoft는 사용자의 개인 정보에 대한 제어를 제공하는 도구와 리소스를 제공하기 위해 노력하고 있습니다. 따라서 Desktop Analytics에서 Windows 8.1 디바이스를 지원하는 동안 Microsoft는 유럽 국가(EEA 및 스위스)에 있는 Windows 8.1 디바이스의 Windows 진단 데이터를 수집하지 않습니다.

자세한 내용은 [Desktop Analytics 개인 정보](/sccm/desktop-analytics/privacy)를 참조하세요.

다음 문서는 Windows 진단 데이터 수준을 보다 잘 이해하기 위한 유용한 리소스입니다.

- [IT 의사 결정자를 위한 Windows 10 및 GDPR](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance)  

- [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)  

> [!Note]  
> 고급 진단 데이터를 제한하도록 구성된 클라이언트는 초기 전체 검색에서 약 2MB의 데이터를 Microsoft 클라우드에 보냅니다. 일별 델타는 하루에 250-400KB로 다양합니다.
>
> 일별 델타 검색은 오전 3시(디바이스 현지 시간)에 발생합니다. 일부 이벤트는 하루 내내 처음 사용 가능한 시간에 전송됩니다. 이러한 시간은 구성할 수 없습니다.
>
> 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://aka.ms/enterprisetelemetry)을 참조하세요.  



## <a name="endpoints"></a>엔드포인트

데이터 공유를 사용하도록 설정하려면 다음 엔드포인트를 허용하도록 프록시 서버를 구성합니다.

> [!Important]  
> 개인 정보 및 데이터 무결성을 위해 Windows는 진단 데이터 엔드포인트와 통신할 때 Microsoft SSL 인증서(인증서 고정)를 확인합니다. SSL 가로채기 및 검사는 불가능합니다. Desktop Analytics를 사용하려면 이러한 엔드포인트를 SSL 검사에서 제외합니다.<!-- BUG 4647542 -->

| 엔드포인트  | 기능  |
|-----------|-----------|
| `https://aka.ms` | 서비스를 찾는 데 사용됨 |
| `https://v10c.events.data.microsoft.com` | 연결된 사용자 환경 및 진단 구성 요소 엔드포인트입니다. 2018-09 누적 업데이트 이상이 설치된 Windows 10, 버전 1809 이상 또는 버전 1803을 실행하는 디바이스에서 사용됩니다. |
| `https://v10.events.data.microsoft.com` | 연결된 사용자 환경 및 진단 구성 요소 엔드포인트입니다. 2018-09 누적 업데이트를 설치하지 _않은_ Windows 10, 버전 1803을 실행하는 디바이스에서 사용됩니다. |
| `https://v10.vortex-win.data.microsoft.com` | 연결된 사용자 환경 및 진단 구성 요소 엔드포인트입니다. Windows 10, 버전 1709 이전을 실행하는 디바이스에서 사용됩니다. |
| `https://vortex-win.data.microsoft.com` | 연결된 사용자 환경 및 진단 구성 요소 엔드포인트입니다. Windows 7 및 Windows 8.1을 실행하는 디바이스에서 사용됨 |
| `https://settings-win.data.microsoft.com` | 호환성 업데이트를 사용하여 데이터를 Microsoft로 보냅니다. |
| `http://adl.windows.com` | Microsoft에서 제공하는 최신 호환성 데이터를 받을 수 있도록 호환성 업데이트를 허용합니다. |
| `https://watson.telemetry.microsoft.com` | [WER(Windows 오류 보고)](https://docs.microsoft.com/windows/win32/wer/windows-error-reporting) Windows 10, 버전 1803 이전에서 배포 상태를 모니터링하는 데 필요합니다. |
| `https://umwatsonc.events.data.microsoft.com` | [WER(Windows 오류 보고)](https://docs.microsoft.com/windows/win32/wer/windows-error-reporting) Windows 10, 버전 1809 이상에서 디바이스 상태 보고서에 필요합니다. |
| `https://ceuswatcab01.blob.core.windows.net`<br> `https://ceuswatcab02.blob.core.windows.net`<br> `https://eaus2watcab01.blob.core.windows.net`<br> `https://eaus2watcab02.blob.core.windows.net`<br> `https://weus2watcab01.blob.core.windows.net`<br> `https://weus2watcab02.blob.core.windows.net` | [WER(Windows 오류 보고)](https://docs.microsoft.com/windows/win32/wer/windows-error-reporting) Windows 10, 버전 1809 이상에서 배포 상태를 모니터링하는 데 필요합니다. |
| `https://kmwatsonc.events.data.microsoft.com` | [OCA(온라인 충돌 분석)](https://docs.microsoft.com/windows/win32/dxtecharts/crash-dump-analysis) Windows 10, 버전 1809 이상에서 디바이스 상태 보고서에 필요합니다. |
| `https://oca.telemetry.microsoft.com`  | [OCA(온라인 충돌 분석)](https://docs.microsoft.com/windows/win32/dxtecharts/crash-dump-analysis) Windows 10, 버전 1803 이전에서 배포 상태를 모니터링하는 데 필요합니다. |
| `https://login.live.com` | Desktop Analytics에 보다 안정적인 디바이스 ID를 제공하는 데 필요합니다. <br> <br>최종 사용자 Microsoft 계정 액세스를 사용하지 않도록 설정하려면 이 엔드포인트를 차단하는 대신 정책 설정을 사용합니다. 자세한 내용은 [Enterprise의 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)을 참조하세요. |
| `https://graph.windows.net` | Configuration Manager 서버 역할의 Desktop Analytics에 계층을 연결할 때 CommercialId와 같은 설정을 자동으로 검색하는 데 사용됩니다. 자세한 내용은 [사이트 시스템 서버에 대한 프록시 구성](/sccm/core/plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server)을 참조하세요. |
| `https://*.manage.microsoft.com` | Desktop Analytics(Configuration Manager 서버 역할에서만)와 함께 디바이스 컬렉션 멤버 자격, 배포 계획 및 디바이스 준비 상태를 동기화하는 데 사용됩니다. 자세한 내용은 [사이트 시스템 서버에 대한 프록시 구성](/sccm/core/plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server)을 참조하세요. |


## <a name="proxy-server-authentication"></a>프록시 서버 인증

인증으로 인해 프록시에서 진단 데이터를 차단하지 않는지 확인합니다. 조직에서 아웃바운드 트래픽에 대해 프록시 서버 인증을 사용하는 경우 다음 방법 중 하나 이상을 사용합니다.

### <a name="bypass-recommended"></a>바이패스(권장)

프록시 서버에서 진단 데이터 엔드포인트에 대한 트래픽에 대해 프록시 인증을 요구하지 않도록 구성합니다. 이 옵션은 가장 포괄적인 솔루션입니다. 모든 버전의 Windows 10에서 작동합니다.  

### <a name="user-proxy-authentication"></a>사용자 프록시 인증

프록시 인증을 위해 로그인한 사용자의 컨텍스트를 사용하도록 디바이스를 구성합니다. 이 메서드에는 다음과 같은 구성이 필요합니다.

- 디바이스에는 Windows 7, Windows 8.1 또는 Windows 10, 버전 1703 이상에 대한 현재 품질 업데이트가 있습니다.
- Windows 설정의 네트워크 & 인터넷 그룹의 **프록시 설정**에서 사용자 수준 프록시(WinINET 프록시)를 구성합니다. 레거시 인터넷 옵션 제어판을 사용할 수도 있습니다. 
- 사용자에게 진단 데이터 엔드포인트에 연결할 수 있는 프록시 권한이 있는지 확인합니다. 이 옵션을 사용하려면 디바이스에 프록시 권한이 있는 콘솔 사용자가 있어야 하므로 헤드리스 디바이스에서 이 방법을 사용할 수 없습니다.

> [!IMPORTANT]
> 사용자 프록시 인증 방법은 Microsoft Defender Advanced Threat Protection 사용과 호환되지 않습니다. 이 동작은 이 인증이 `0`으로 설정된 **DisableEnterpriseAuthProxy** 레지스트리 키를 사용하는 반면 Microsoft Defender ATP에서는 `1`로 설정하도록 요구하기 때문입니다. 자세한 내용은 [머신 프록시 및 인터넷 연결 설정 구성](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/configure-proxy-internet-windows-defender-advanced-threat-protection)을 참조하세요.

### <a name="device-proxy-authentication"></a>디바이스 프록시 인증

이 방법은 다음과 같은 구성이 필요하기 때문에 가장 복잡합니다.

- 디바이스가 로컬 시스템 컨텍스트에서 WinHTTP를 통해 프록시 서버에 연결할 수 있는지 확인합니다. 이 동작을 구성하려면 다음 옵션 중 하나를 사용합니다.
  - 명령줄 'netsh winhttp set proxy'
  - WPAD(웹 프록시 자동 검색) 프로토콜
  - 투명 프록시
  - 라우팅된 연결 또는 NAT(Network Address Translation) 사용

- Active Directory의 컴퓨터 계정에서 진단 데이터 엔드포인트에 액세스할 수 있도록 프록시 서버를 구성합니다. 이 구성에서는 Windows 통합 인증을 지원하기 위해 프록시 서버가 필요합니다.  
