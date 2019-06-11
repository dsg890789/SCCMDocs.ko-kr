---
title: 데이터 공유를 사용하도록 설정
titleSuffix: Configuration Manager
description: 데스크톱 Analytics를 사용 하 여 진단 데이터를 공유 하는 것에 대 한 참조 가이드입니다.
ms.date: 06/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: be680198-4cea-4378-a686-d52f382ba483
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7292fdd3cc370af314cef95a4b782616e315a0cb
ms.sourcegitcommit: 725e1bf7d3250c2b7b7be9da01135517428be7a1
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821985"
---
# <a name="enable-data-sharing-for-desktop-analytics"></a>데이터 분석 데스크톱에 대 한 공유를 사용 하도록 설정

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 Analytics에는 장치를 등록 하려면 Microsoft에 진단 데이터를 전송 해야 합니다. 사용자 환경에서 프록시 서버를 사용 하는 경우 프록시를 구성 하는 데이 정보를 사용 합니다.


## <a name="diagnostic-data-levels"></a>진단 데이터 수준

![데스크톱 분석에 대 한 진단 데이터 수준의 다이어그램](media/diagnostic-data-levels.png)

데스크톱 Analytics를 사용 하 여 Configuration Manager와 통합 하면 있습니다도 관리 하는데 사용할 장치에서 진단 데이터 수준입니다. 최상의 환경을 위해 Configuration Manager를 사용 합니다.

데스크톱 분석의 기본 기능에서 작동 합니다 **기본** 진단 데이터 수준입니다. 사용 하지 않고 업데이트 된 장치에 대 한 사용량 또는 상태 데이터를 가져오는지 않습니다 합니다 **고급 (제한적)** 수준입니다. 사용할 수 있도록 하는 것이 좋습니다 합니다 **고급 (제한적)** 진단 데이터 수준입니다. 자세한 내용은 [Windows 10 향상 된 진단 데이터 이벤트 및 Windows Analytics에 의해 사용 되는 필드](https://docs.microsoft.com/windows/privacy/enhanced-diagnostic-data-windows-analytics-events-and-fields)).

자세한 내용은 [데스크톱 분석 개인 정보 보호](/sccm/desktop-analytics/privacy)합니다.

다음 문서는 또한 유용한 리소스를 더 나은 Windows 진단 데이터 수준 이해:

- [Windows 10 및 IT 의사 결정자를 위한 GDPR](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance)  

- [조직에서 Windows 진단 데이터를 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)  

> [!Note]  
> 고급 (제한적) 수준에서 각 클라이언트는 초기 전체 검색을 수행 하는 경우 보낼 데이터의 약 2MB Microsoft 클라우드입니다. 일일 델타 하루 250-400 KB 다릅니다.
>
> 매일 델타 검색 (장치 현지 시간) 오전 3 시에 발생합니다. 일부 이벤트는 하루 종일 첫 번째 사용 가능한 시간에 전송 됩니다. 이러한 시간은 구성할 수 없습니다.
>
> 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://aka.ms/enterprisetelemetry)을 참조하세요.  



## <a name="endpoints"></a>끝점

데이터 공유를 사용 하려면 다음 끝점을 허용 하도록 프록시 서버를 구성 합니다.

> [!Important]  
> 개인 정보 보호 및 데이터 무결성에 대 한 Windows 진단 데이터 끝점과 통신할 때 Microsoft SSL 인증서를 확인 합니다. SSL 인터 셉 션 및 검사에 사용할 수 없습니다. 데스크톱 Analytics를 사용 하려면 SSL 검사에서 이러한 끝점을 제외 합니다.<!-- BUG 4647542 -->

| 엔드포인트  | 기능  |
|-----------|-----------|
| `https://v10c.events.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. Windows 10을 실행 하는 장치, 버전 1703 이상, 2018-09 누적를 사용 하 여 업데이트 또는 사용 이상이 설치 되어 있습니다. |
| `https://v10.events.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. Windows 10, 버전 1803에서 이상을 실행 하는 장치에서 사용 하는 _없이_ 2018-09 누적 업데이트가 설치 되어 있습니다. |
| `https://v10.vortex-win.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. Windows 10 버전 1709 또는 이전 버전을 실행 하는 장치에서 사용 합니다. |
| `https://vortex-win.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. Windows 7 및 Windows 8.1 실행 하는 장치에서 사용 하는 |
| `https://settings-win.data.microsoft.com` | 호환성 업데이트를 Microsoft로 데이터를 보낼 수 있습니다. |
| `http://adl.windows.com` | Microsoft에서 최신 호환성 데이터를 받도록 호환성 업데이트를 허용 합니다. |
| `https://watson.telemetry.microsoft.com` | Windows 오류 보고 (WER)입니다. Windows 10, 버전 1803에서 배포 상태를 모니터링 해야 합니다. |
| `https://umwatsonc.events.data.microsoft.com` | Windows 오류 보고 (WER)입니다. Windows 10 1809 이상 버전에서에서 장치 상태 보고서에 필요합니다. |
| `https://ceuswatcab01.blob.core.windows.net`<br> `https://ceuswatcab02.blob.core.windows.net`<br> `https://eaus2watcab01.blob.core.windows.net`<br> `https://eaus2watcab02.blob.core.windows.net`<br> `https://weus2watcab01.blob.core.windows.net`<br> `https://weus2watcab02.blob.core.windows.net` | Windows 오류 보고 (WER)입니다. Windows 10 1809 이상 버전에서에서 배포 상태를 모니터링 해야 합니다. |
| `https://kmwatsonc.events.data.microsoft.com` | 온라인 크래시 분석 합니다. Windows 10 1809 이상 버전에서에서 장치 상태 보고서에 필요합니다. |
| `https://oca.telemetry.microsoft.com`  | 온라인 Analysis (OCA)입니다. Windows 10, 버전 1803에서 배포 상태를 모니터링 해야 합니다. |
| `https://login.live.com` | 데스크톱 분석에 대 한 더 신뢰할 수 있는 장치 id를 제공 해야 합니다. <br> <br>최종 사용자가 Microsoft 계정 액세스를 비활성화 하려면이 끝점을 차단 하는 대신 정책 설정을 사용 합니다. 자세한 내용은 [기업에서 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)합니다. |
| `https://nexusrules.officeapps.live.com` | 향후 기능에 대 한 <!-- Used to request dynamic diagnostic data events from Office clients. This data is useful for drill-down and diagnostics purposes in the Desktop Analytics portal --> |
| `https://nexus.officeapps.live.com` | 향후 기능에 대 한 <!-- Used by Office clients to send diagnostic data events from Office 14, Office 15, and versions of Office 16 earlier than 16.0.8702. It's used to collect usage and reliability signals events for Desktop Analytics. --> |
| `https://office.pipe.aria.microsoft.com` | 향후 기능에 대 한 <!-- Used by Office clients to send diagnostic data events from universal/modern Office apps, and Win32 Office 16 versions later than 16.0.8702. It's used to collect usage and reliability signals events for Desktop Analytics. --> |
| `https://graph.windows.net` | Configuration Manager 서버 역할에만 해당) (에 계층 데스크톱 Analytics에 연결 하는 경우 commercialid 입니다와 같은 설정이 자동으로 검색 하는 데 사용 합니다. |
| `https://fef.msua06.manage.microsoft.com` | 동기화 장치 컬렉션 멤버 자격, 배포 계획 (Configuration Manager 서버 역할에만 해당)에 데스크톱 Analytics를 사용 하 여 장치 준비 상태를 사용 합니다. |


## <a name="proxy-server-authentication"></a>프록시 서버 인증

프록시 인증으로 인해 진단 데이터를 차단 하지 않는지 확인 합니다. 조직에서 아웃 바운드 트래픽에 대 한 프록시 서버 인증을 사용 하는 경우 다음 방법 중 하나 이상을 사용 합니다.

- **바이패스** (권장): 진단 데이터 끝점에 대 한 트래픽의 프록시 인증을 요구 하지 않도록 프록시 서버를 구성 합니다. 이 옵션은 가장 포괄적인 솔루션입니다. 모든 버전의 Windows 10에서 작동합니다.  

- **사용자 프록시 인증**: 프록시 인증에 대 한 로그인 한 사용자의 컨텍스트를 사용 하는 장치를 구성 합니다. 이 메서드는 장치를 Windows 10 버전 1703 이상이 실행 해야 합니다. 사용자가 있는 진단 데이터 끝점에 연결할 프록시 권한이 있는지 확인 합니다. 이 옵션 있어야 장치 프록시 권한으로 콘솔 사용자 헤드리스 장치를 사용 하 여이 메서드를 사용할 수 없습니다.  

- **장치 프록시 인증**:

    - 장치에서 시스템 수준의 프록시 서버를 구성 합니다.  
    - 아웃 바운드 프록시 장치 기반 인증을 사용 하려면 이러한 장치를 구성 합니다.  
    - 진단 데이터 끝점에 액세스 하는 컴퓨터 계정을 허용 하도록 프록시 서버를 구성 합니다.  
