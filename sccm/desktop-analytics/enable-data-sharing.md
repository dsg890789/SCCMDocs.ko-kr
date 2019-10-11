---
title: 데이터 공유를 사용하도록 설정
titleSuffix: Configuration Manager
description: 데스크톱 분석과 진단 데이터를 공유 하는 방법에 대 한 참조 가이드입니다.
ms.date: 07/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: be680198-4cea-4378-a686-d52f382ba483
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0128a802916958c69b07dffe86d04f31698fd028
ms.sourcegitcommit: 974b20f5faa0e0bbf9e43391280fdebeb657ac47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72237017"
---
# <a name="enable-data-sharing-for-desktop-analytics"></a>데스크톱 분석에 데이터 공유 사용

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

데스크톱 분석에 장치를 등록 하려면 Microsoft에 진단 데이터를 전송 해야 합니다. 환경에서 프록시 서버를 사용 하는 경우이 정보를 참조 하 여 프록시를 구성 합니다.


## <a name="diagnostic-data-levels"></a>진단 데이터 수준

![데스크톱 분석의 진단 데이터 수준 다이어그램](media/diagnostic-data-levels.png)

데스크톱 분석과 Configuration Manager를 통합 하는 경우이를 사용 하 여 장치에서 진단 데이터 수준을 관리할 수도 있습니다. 최상의 환경을 위해 Configuration Manager를 사용 합니다.

데스크톱 분석의 기본 기능은 **기본** 진단 데이터 수준에서 작동 합니다. **향상 된 (제한 된)** 수준을 사용 하지 않으면 업데이트 된 장치에 대 한 사용량 또는 상태 데이터를 얻지 못합니다. **향상 된 (제한 된)** 진단 데이터 수준을 사용 하도록 설정 하는 것이 좋습니다. 자세한 내용은 windows [10 고급 진단 데이터 이벤트 및 Windows Analytics에서 사용 되는 필드](https://docs.microsoft.com/windows/privacy/enhanced-diagnostic-data-windows-analytics-events-and-fields)를 참조 하세요.

> [!Important]   
> Microsoft는 사용자의 개인 정보에 대 한 제어를 제공 하는 도구와 리소스를 제공 하기 위해 노력 하 고 있습니다. 따라서 Microsoft는 유럽 국가 (EEA 및 스위스)에 있는 장치에서 다음 데이터를 수집 하지 않습니다.
>
> - Windows 8.1 장치의 Windows 진단 데이터
> - Windows 7 용 앱 사용 현황 데이터

자세한 내용은 [데스크톱 분석 개인 정보](/sccm/desktop-analytics/privacy)를 참조 하세요.

다음 문서는 Windows 진단 데이터 수준을 보다 잘 이해 하기 위한 유용한 리소스입니다.

- [IT 의사 결정자를 위한 Windows 10 및 GDPR](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance)  

- [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)  

> [!Note]  
> 향상 된 (제한 된) 수준에서 각 클라이언트는 초기 전체 검색을 수행 하는 경우 약 2mb의 데이터를 Microsoft 클라우드에 보냅니다. 일별 델타는 하루에 250-400 k b 마다 다릅니다.
>
> 매일 델타 검색은 오전 3:00 시 (장치 현지 시간)에 발생 합니다. 일부 이벤트는 하루 내내 처음 사용 가능한 시간에 전송 됩니다. 이러한 시간은 구성할 수 없습니다.
>
> 자세한 내용은 [조직에서 Windows 진단 데이터 구성](https://aka.ms/enterprisetelemetry)을 참조하세요.  



## <a name="endpoints"></a>종점

데이터 공유를 사용 하도록 설정 하려면 다음 끝점을 허용 하도록 프록시 서버를 구성 합니다.

> [!Important]  
> 개인 정보 및 데이터 무결성을 위해 Windows는 진단 데이터 끝점과 통신할 때 Microsoft SSL 인증서를 확인 합니다. SSL 가로채기 및 검사는 불가능 합니다. 데스크톱 분석을 사용 하려면 이러한 끝점을 SSL 검사에서 제외 합니다.<!-- BUG 4647542 -->

| 엔드포인트  | 기능  |
|-----------|-----------|
| `https://aka.ms` | 서비스를 찾는 데 사용 됩니다. |
| `https://v10c.events.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. 2018-09 누적 업데이트 이상을 설치한 Windows 10 버전 1703 이상을 실행 하는 장치에서 사용 됩니다. |
| `https://v10.events.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. 2018-09 누적 업데이트가 설치 _되지 않은_ Windows 10 버전 1803 이상을 실행 하는 장치에서 사용 됩니다. |
| `https://v10.vortex-win.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. Windows 10, 버전 1709 이전 버전을 실행 하는 장치에서 사용 됩니다. |
| `https://vortex-win.data.microsoft.com` | 연결 된 사용자 환경 및 진단 구성 요소 끝점입니다. Windows 7 및 Windows 8.1를 실행 하는 장치에서 사용 |
| `https://settings-win.data.microsoft.com` | 호환성 업데이트를 사용 하 여 데이터를 Microsoft로 보냅니다. |
| `http://adl.windows.com` | 호환성 업데이트가 Microsoft에서 제공 하는 최신 호환성 데이터를 받을 수 있도록 허용 합니다. |
| `https://watson.telemetry.microsoft.com` | WER (Windows 오류 보고). Windows 10 버전 1803 이전 버전에서 배포 상태를 모니터링 하는 데 필요 합니다. |
| `https://umwatsonc.events.data.microsoft.com` | WER (Windows 오류 보고). Windows 10 버전 1809 이상에서 장치 상태 보고서에 필요 합니다. |
| `https://ceuswatcab01.blob.core.windows.net`<br> `https://ceuswatcab02.blob.core.windows.net`<br> `https://eaus2watcab01.blob.core.windows.net`<br> `https://eaus2watcab02.blob.core.windows.net`<br> `https://weus2watcab01.blob.core.windows.net`<br> `https://weus2watcab02.blob.core.windows.net` | WER (Windows 오류 보고). Windows 10 버전 1809 이상에서 배포 상태를 모니터링 하는 데 필요 합니다. |
| `https://kmwatsonc.events.data.microsoft.com` | 온라인 충돌 분석. Windows 10 버전 1809 이상에서 장치 상태 보고서에 필요 합니다. |
| `https://oca.telemetry.microsoft.com`  | 온라인 충돌 분석 (OCA). Windows 10 버전 1803 이전 버전에서 배포 상태를 모니터링 하는 데 필요 합니다. |
| `https://login.live.com` | 데스크톱 분석에 보다 안정적인 장치 id를 제공 하는 데 필요 합니다. <br> <br>최종 사용자 Microsoft 계정 액세스를 사용 하지 않도록 설정 하려면이 끝점을 차단 하는 대신 정책 설정을 사용 합니다. 자세한 내용은 [엔터프라이즈의 Microsoft 계정](https://docs.microsoft.com/windows/security/identity-protection/access-control/microsoft-accounts#block-all-consumer-microsoft-account-user-authentication)을 참조 하세요. |
| `https://graph.windows.net` | 계층을 데스크톱 분석에 연결할 때 CommercialId 같은 설정을 자동으로 검색 하는 데 사용 됩니다 (Configuration Manager 서버 역할에만 해당). |
| `https://*.manage.microsoft.com` | 데스크톱 분석 (Configuration Manager 서버 역할의 경우에만)을 사용 하 여 장치 컬렉션 멤버 자격, 배포 계획 및 장치 준비 상태를 동기화 하는 데 사용 됩니다. |


## <a name="proxy-server-authentication"></a>프록시 서버 인증

인증으로 인해 프록시에서 진단 데이터를 차단 하지 않는지 확인 합니다. 조직에서 아웃 바운드 트래픽에 대해 프록시 서버 인증을 사용 하는 경우 다음 방법 중 하나 이상을 사용 합니다.

- **바이패스** (권장): 프록시 서버에서 진단 데이터 끝점에 대 한 트래픽에 대해 프록시 인증을 요구 하지 않도록 구성 합니다. 이 옵션은 가장 포괄적인 솔루션입니다. 모든 버전의 Windows 10에서 작동 합니다.  

- **사용자 프록시 인증**: 프록시 인증을 위해 로그인 한 사용자의 컨텍스트를 사용 하도록 장치를 구성 합니다. 이 방법을 사용 하려면 장치에서 Windows 10 버전 1703 이상을 실행 해야 합니다. 사용자에 게 진단 데이터 끝점에 연결할 수 있는 프록시 권한이 있는지 확인 합니다. 이 옵션을 사용 하려면 장치에 프록시 권한이 있는 콘솔 사용자가 있어야 하므로 헤드리스 장치에서이 방법을 사용할 수 없습니다.  

- **장치 프록시 인증**:

    - 장치에서 시스템 수준 프록시 서버를 구성 합니다.  
    - 장치 기반 아웃 바운드 프록시 인증을 사용 하도록 장치를 구성 합니다.  
    - 컴퓨터 계정에서 진단 데이터 끝점에 액세스할 수 있도록 프록시 서버를 구성 합니다.  
