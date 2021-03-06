---
title: Desktop Analytics 데이터 프라이버시
titleSuffix: Configuration Manager
description: Desktop Analytics가 고객 데이터 프라이버시에 커밋됨
ms.date: 12/12/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b5606f15-f589-485c-a599-cdabf1a9e7ac
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b3ac5b3b9f91fbbb426a5314f72f3bb6d9b608db
ms.sourcegitcommit: cf978bfea545ed9116dacadfac830cbb08aaa649
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75951657"
---
# <a name="desktop-analytics-data-privacy"></a>Desktop Analytics 데이터 프라이버시

Desktop Analytics는 이러한 개념을 중심으로 고객 데이터 프라이버시에 완전히 커밋됩니다.

- **투명도:** Windows 진단 이벤트를 완전히 문서화합니다. 회사의 보안 및 규정 준수 팀에서 검토합니다. Windows 진단 데이터 뷰어를 사용하여 지정된 디바이스에서 전송된 진단 데이터를 볼 수 있습니다. 자세한 내용은 [진단 데이터 뷰어 개요](https://docs.microsoft.com/windows/configuration/diagnostic-data-viewer-overview)를 참조하세요.  

- **제어:** Microsoft와 공유할 진단 데이터의 수준을 제어합니다. Windows 10, 버전 1709는 향상된 진단 데이터를 Desktop Analytics에서 요구하는 최소로 제한하는 새 정책을 추가합니다.  

- **보안:** Microsoft는 강력한 보안 및 암호화를 통해 데이터를 보호합니다.  

- **신뢰:** Desktop Analytics는 Microsoft [개인정보처리방침](https://privacy.microsoft.com/privacystatement) 및 [온라인 서비스 약관](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)을 지원합니다.  

자세한 내용은 [Microsoft가 GDPR 아래에 있는 프로세서인 Windows 서비스](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance#windows-services-where-microsoft-is-the-processor-under-the-gdpr)를 참조하세요.<!-- 5353168 -->

## <a name="data-flow"></a>데이터 흐름

다음 그림은 진단 데이터 서비스, 임시 스토리지를 통해 개별 디바이스에서 Log Analytics 작업 영역으로 진단 데이터를 전달하는 방법을 보여 줍니다.

![디바이스에서 진단 데이터의 흐름을 보여 주는 다이어그램](media/da-data-flow.png)

1. Azure Portal에 로그인하고, Desktop Analytics에 등록합니다. Configuration Manager와 연결하기 위해 Azure AD 앱을 만듭니다. Desktop Analytics를 설정하는 경우 선택한 위치에 Azure Log Analytics 작업 영역을 만듭니다.  

2. Configuration Manager를 연결하고 디바이스를 등록합니다.  

    1. Azure AD 앱 세부 정보를 사용하여 Configuration Manager에서 Desktop Analytics 클라우드 서비스를 구성합니다.  

    2. 15분 이내에 Configuration Manager가 테넌트 ID를 사용하는 Desktop Analytics와 다음 데이터를 동기화합니다. 1시간마다 이 프로세스를 반복합니다.

      - [배포 계획 만들기](/configmgr/desktop-analytics/create-deployment-plans)에 필요한 디바이스 컬렉션과 관련된 정보입니다. 이 정보에는 컬렉션 ID, 계층 구조 ID, 컬렉션 이름, 디바이스 수가 포함됩니다. 
      - [디바이스 등록](/configmgr/desktop-analytics/enroll-devices)에 필요한 정보입니다. 이 정보에는 컬렉션 ID, SMS 고유 식별자, OS 빌드 버전, 디바이스 이름, 일련 번호가 포함됩니다.
      - [모니터 연결 상태](/configmgr/desktop-analytics/monitor-connection-health) 대시보드의 정보입니다. 이 정보에는 성능 상태별 디바이스 수와 디바이스 속성이 포함됩니다.
      - 배포 계획 관련 정보이며, 여기에는 컬렉션 ID, 배포 ID, 파일럿 또는 프로덕션 배포 유형, 업그레이드 결정별 디바이스 수가 포함됩니다.

    3. Configuration Manager는 상업용 ID, 진단 데이터 수준 및 대상 컬렉션의 디바이스에 대한 기타 설정을 설정합니다. 이 구성은 Desktop Analytics 작업 영역에 표시되는 디바이스를 지정합니다.  

    4. 모든 대상 디바이스에 호환성 업데이트를 배포합니다.  

3. 디바이스는 Windows용 Microsoft 진단 데이터 관리 서비스로 진단 데이터를 보냅니다. 이 서비스는 미국에서 호스트됩니다.  

4. Microsoft는 매일 IT 중심 인사이트의 스냅샷을 생성합니다. 이 스냅샷은 Windows의 진단 데이터와 등록된 디바이스에 대한 입력을 결합합니다. 이 프로세스는 Desktop Analytics에서만 사용되는 임시 스토리지에서 발생합니다. 임시 스토리지는 미국의 Microsoft 데이터 센터에서 호스트됩니다. 모든 데이터는 SSL(HTTPS) 암호화 채널을 통해 전송됩니다. 스냅샷은 상업용 ID로 분리됩니다.  

5. 그러면 스냅샷이 Azure Log Analytics 작업 영역에 복사됩니다. 이 데이터 전송은 HTTPS상에서 Log Analytics의 기능인 웹후크 수집 프로토콜을 통해 수행됩니다. Desktop Analytics에는 Log Analytics 스토리지에 대한 읽기 또는 쓰기 권한이 없습니다. Desktop Analytics에서는 SAS(공유 액세스 서명) URI로 웹후크 API를 호출합니다. 그러면 Log Analytics는 HTTPS를 통해 스토리지 테이블에서 데이터를 가져옵니다.

6. Desktop Analytics는 Log Analytics 스토리지에 입력을 저장합니다. 이러한 구성에는 배포 계획과 업그레이드 및 중요도에 대한 자산 결정이 포함됩니다.  

## <a name="other-resources"></a>관련 자료

Desktop Analytics에 대한 개인 정보 관련 질문과 대답은 [개인 정보 FAQ](/sccm/desktop-analytics/faq#privacy)를 참조하세요.

관련된 개인 정보 측면에 대한 자세한 내용은 다음 문서를 참조하세요.

- [IT 의사 결정자를 위한 Windows 10 및 GDPR](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance)  

- [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)  

- [Windows 7, Windows 8 및 Windows 8.1 평가자 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/appraiser-diagnostic-data-events-and-fields)  

- [Windows 10, 버전 1809 기본 수준 Windows 진단 이벤트 및 필드](https://docs.microsoft.com/windows/privacy/basic-level-windows-diagnostic-events-and-fields-1809)  

- [Desktop Analytics에서 사용하는 Windows 10, 버전 1709 고급 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/windows/privacy/enhanced-diagnostic-data-windows-analytics-events-and-fields)  

- [진단 데이터 뷰어 개요](https://docs.microsoft.com/windows/privacy/diagnostic-data-viewer-overview)  

- [사용 약관 및 설명서](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)  

- [Log Analytics 데이터 보안](https://docs.microsoft.com/azure/azure-monitor/platform/data-security)

- [Microsoft Azure 데이터 센터에서 보안 및 개인 정보 보호](https://azure.microsoft.com/global-infrastructure/)  

- [신뢰할 수 있는 클라우드의 신뢰도](https://azure.microsoft.com/overview/trusted-cloud/)  

- [보안 센터](https://www.microsoft.com/trustcenter)  

- [개인 정보 보호](https://www.privacyshield.gov/)  

Configuration Manager는 Desktop Analytics와는 별도로 Microsoft에 진단 및 사용량 현황 데이터를 전송합니다. 이러한 데이터는 Microsoft에서 향후 Configuration Manager 릴리스 시의 설치 환경, 품질 및 보안을 개선하는 데 사용됩니다. 자세한 내용은 [Configuration Manager의 진단 및 사용량 현황 데이터](/configmgr/core/plan-design/diagnostics/diagnostics-and-usage-data)를 참조하세요.
