---
titleSuffix: Configuration Manager
description: Configuration Manager 콘솔에서 지원되는 관리 정보 기능에 대해 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a79f83be-884c-48e6-94d6-ed0a68c22e2f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 9ded020bd654672bb6133c9aad15478c22498ab7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="management-insights-in-system-center-configuration-manager"></a>System Center Configuration Manager의 관리 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 관리 정보는 환경의 현재 상태에 대한 정보를 제공합니다. 이 정보는 사이트 데이터베이스의 데이터 분석을 기반으로 합니다. 이 정보를 통해 환경을 더 잘 이해하고 해당 정보에 기반한 조치를 취할 수 있습니다. 이 기능은 Configuration Manager 버전 1802에서 릴리스되었습니다. <!--1353967-->

## <a name="review-management-insights-in-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 관리 정보 검토 
규칙을 보려면 **site-read** 권한이 필요합니다.

1. Configuration Manager 콘솔을 엽니다. 
2. **관리** 노드로 이동하고 **관리 정보**를 클릭합니다.
3. **모든 정보**를 선택합니다.
4. 검토하려는 **관리 정보 그룹 이름**을 두 번 클릭합니다. 또는 강조 표시하고 리본 메뉴에서 **정보 표시**를 클릭합니다. 
5. 규칙을 실행하는 데 필요한 필수 구성 요소와 함께 검토용으로 4개의 탭이 지원됩니다. 
    - **모든 규칙**: 선택한 관리 정보 그룹에 대한 규칙의 전체 목록을 제공합니다.
    - **완료**: 아무 조치도 필요하지 않은 규칙을 나열합니다. 
    - **진행 중**: 모두는 아니지만 일부 필수 구성 요소가 완료되는 규칙을 보여줍니다.
    - **필요한 작업**: 작업을 수행해야 하는 규칙이 나열됩니다. **자세한 세부 내용**을 마우스 오른쪽 단추로 클릭하고 선택하여 작업이 필요한 특정 항목을 검색합니다. 
    - **필수 구성 요소**: 규칙을 실행하기 전에 항목을 완료해야 하는 경우 필수 항목이 여기에 나열됩니다.   
    
    **클라우드 서비스 그룹에 대한 모든 규칙 및 필수 구성 요소** ![관리 정보 - 클라우드 서비스 그룹에 대한 모든 규칙 및 필수 구성 요소](./media/Management-insights-all-cloud-rules.png)

## <a name="management-insights-reevaluation-and-logging"></a>관리 정보 재평가 및 로깅
관리 정보 규칙은 주별 일정에 따라 해당 적용 가능성을 재평가합니다. 규칙을 마우스 오른쪽 단추로 클릭하고 **재평가**를 선택하여 요구된 규칙을 재평가할 수 있습니다.

**관리 정보 규칙에 대한 로그 파일**: SMS_DataEngine.log
## <a name="management-insights-groups-and-rules"></a>관리 정보 그룹 및 규칙
규칙은 다른 관리 정보 그룹으로 구성됩니다. 그룹 및 규칙이 추가되면 다음 목록에 추가됩니다.

**응용 프로그램**: 응용 프로그램 관리에 대한 정보입니다.

- **배포가 없는 응용 프로그램** - 사용자 환경에서 활성 배포가 없는 응용 프로그램을 나열합니다. 이 규칙을 통해 사용되지 않는 응용 프로그램을 찾고 삭제하여 콘솔에 표시된 응용 프로그램 목록을 간소화할 수 있습니다. 

**클라우드 서비스**: 많은 클라우드 서비스와 통합하여 장치의 최신 관리를 사용하도록 설정합니다. 
 - **공동 관리 준비 상태 평가** - 공동 관리를 사용하는 데 필요한 단계를 이해할 수 있습니다. 이 규칙에는 필수 구성 요소가 있습니다. 
 - **장치를 하이브리드 Azure Active Directory 가입하도록 설정** - Azure AD 가입 장치를 통해 장치가 조직의 보안 및 준수 표준을 충족하는 경우 사용자가 해당 도메인 자격 증명을 사용하여 로그인할 수 있습니다. 
 - **ID 및 액세스 인프라 현대화** - 통합된 다단계 인증을 사용하는 Azure AD 클라우드 서비스는 온-프레미스와 클라우드에서 중요한 데이터 및 응용 프로그램을 보호합니다. 
 - **Windows 10 버전 1709 이상으로 클라이언트 업그레이드** - Windows 10 버전 1709 이상은 사용자의 컴퓨팅 환경을 향상시키고 현대화합니다. 


**컬렉션**: 컬렉션을 정리하고 다시 구성하여 관리를 간소화하는 데 도움이 되는 정보입니다.
   - **빈 컬렉션** - 사용자 환경에서 멤버가 없는 컬렉션을 나열합니다. 

**간소화된 관리**: 환경의 일상적인 관리를 단순화하는 데 도움이 되는 정보입니다. 
   - **오래된 클라이언트 버전** - 2년이 초과된 버전이 있는 모든 클라이언트를 나열합니다. 

**소프트웨어 센터**: 소프트웨어 센터를 관리하기 위한 정보입니다. 
   - **사용자를 응용 프로그램 카탈로그 대신 소프트웨어 센터로 이동** - 사용자가 지난 14일 동안 응용 프로그램 카탈로그의 응용 프로그램을 설치했거나 요청했는지를 확인합니다. 응용 프로그램 카탈로그의 기본 기능이 이제는 소프트웨어 센터에 포함됩니다. 2018년 6월 1일 이후 출시된 첫 번째 업데이트에서 응용 프로그램 카탈로그 웹 사이트에 대한 지원이 종료됩니다.
   - **새 버전의 소프트웨어 센터 사용** - 이전 버전의 소프트웨어 센터는 더 이상 지원되지 않습니다. 클라이언트 설정인 **컴퓨터 에이전트** >**새 소프트웨어 센터 사용**을 활성화하여 새로운 소프트웨어 센터를 사용하도록 클라이언트를 설정합니다.

**Windows 10**: Windows 10 서비스를 배포하고 제공하는 데 관련된 정보입니다. Windows 10 관리 정보 그룹은 Windows 7, Windows 8 또는 Windows 8.1을 실행하는 클라이언트의 절반을 초과하는 경우 지원됩니다.
   - **Windows 원격 분석 및 상업용 ID 키 구성** - 업그레이드 준비에서 데이터를 사용하려면 장치는 상업용 ID 키로 구성되고 원격 분석을 사용하도록 설정해야 합니다. Windows 10 장치는 강화된(제한된) 원격 분석 수준 이상으로 설정되어야 합니다.
   - **업그레이드 준비에 Configuration Manager 연결** - Windows 7 지원이 중지되기 전에 업그레이드 준비를 활용하여 Windows 10 배포를 신속하게 처리합니다. **Windows 원격 분석 및 상용 ID 키 구성**은 필수 구성 요소입니다.

     **Windows 10 관리 정보 규칙**
    ![관리 정보 - Windows 10에 대한 규칙](./media/Windows-10-insights-group.png)
    