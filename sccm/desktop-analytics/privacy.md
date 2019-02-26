---
title: 데스크톱의 분석 데이터 개인 정보 보호
titleSuffix: Configuration Manager
description: 데스크톱 Analytics 고객 데이터 개인 정보 보호에 커밋됩니다.
ms.date: 01/25/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b5606f15-f589-485c-a599-cdabf1a9e7ac
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 370bfc26b8a7b6ca0223803a36e765528460d89f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755446"
---
# <a name="desktop-analytics-data-privacy"></a>데스크톱의 분석 데이터 개인 정보 보호

데스크톱 Analytics는 고객 데이터 개인 정보 보호를 위해 최선을 다하고 이러한 개념에 가운데 맞춤 합니다.

- **투명성:** Windows 진단 이벤트를 완벽 하 게 설명 되어 있습니다. 회사의 보안 및 규정 준수 팀과 함께 검토 합니다. Windows 진단 데이터 뷰어를 사용 하면 특정된 장치에서 전송 하는 진단 데이터를 볼 수 있습니다. 자세한 내용은 [진단 데이터 뷰어 개요](https://docs.microsoft.com/windows/configuration/diagnostic-data-viewer-overview)합니다.  

- **컨트롤:** Microsoft와 공유 하는 진단 데이터의 수준을 제어할 수 있습니다. Windows 10 버전 1709 데스크톱 Analytics에서 필요한 최소 수준으로 향상 된 진단 데이터를 제한 하는 새 정책을 추가 합니다.  

- **보안:** Microsoft는 강력한 보안 및 암호화를 사용 하 여 데이터를 보호합니다.  

- **신뢰:** 데스크톱 Analytics는 Microsoft 지원 [개인정보취급방침](https://privacy.microsoft.com/privacystatement) 하 고 [온라인 서비스 약관](http://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)합니다.  



## <a name="diagnostic-data-flow"></a>진단 데이터 흐름

다음 그림에서는 어떻게 진단 데이터를 표시 하 고 Log Analytics 작업 영역에 Azure Log Analytics 저장소에 진단 데이터 서비스를 통해 개별 장치에서 흐름:

![장치에서 진단 데이터의 흐름을 보여 주는 다이어그램](media/da-data-flow-v1.png)

1. Azure 포털 및 데스크톱 Analytics에 등록에 로그인 합니다. Configuration Manager를 연결 하려면 Azure AD 앱 만들기 데스크톱 Analytics를 설정 하는 경우 사용자가 선택한 위치에는 Azure Log Analytics 작업 영역을 만듭니다.  

2. Configuration Manager를 연결 하 고 장치를 등록 합니다.  

    1. 구성한 데스크톱 Analytics 클라우드 서비스를 Configuration Manager에서 Azure AD 앱 세부 정보를 사용 하 여 합니다.  

    2. 15 분 이내 Configuration Manager는 장치 컬렉션 및 배포 계획 데스크톱 Analytics와 동기화 합니다. 매시간이이 프로세스를 반복 합니다.  

    3. Configuration Manager는 대상 컬렉션의 상용 ID, 진단 데이터 수준 및 장치에 대 한 다른 설정을 설정합니다. 이 구성은 데스크톱 분석 작업 영역에 표시할 장치를 지정 합니다.  

    4. 모든 대상 장치에 호환성 업데이트를 배포 합니다. 필요에 따라 앱 상태 분석기 및 Office Readiness Toolkit에 배포할 장치 집합을 표시 합니다. 사용자 지정 기간 업무 응용 프로그램 및 Office 매크로에서 이러한 도구 제공 insights 추가 합니다.  

3. 장치는 Windows 및 Office에 대 한 Microsoft 진단 데이터 관리 서비스에 진단 데이터를 보냅니다. 이 서비스는 미국에서 호스트 됩니다.  

4. 매일 Microsoft IT에 초점을 맞춘 insights의 스냅숏을 생성합니다. 이 스냅숏이 등록된 된 장치에 대 한 입력을 사용 하 여 Windows 및 Office에서 진단 데이터를 결합합니다. 이 프로세스는 데스크톱 분석에만 사용 되는 임시 저장소에 발생 합니다. 일시적인 저장소는 미국에서 Microsoft 데이터 센터에서 호스팅됩니다. 상용 id 스냅숏은 분리 됩니다.  

5. 스냅숏에 적절 한 Azure Log Analytics 작업 영역에 복사 됩니다.  

6. 데스크톱 Analytics는 Azure Log Analytics 저장소에 입력을 저장합니다. 이러한 구성에는 배포 계획과 업그레이드 및 중요도 대 한 자산 결정 포함 됩니다.  


<!-- ![Diagram illustrating flow of diagnostic data from devices](media/wa-data-flow-v1.png)

1. Devices send diagnostic data to the Microsoft Diagnostic Data Management service. This service is hosted in the United States.  

2. Set up and enrollment  

    1. You create an Azure Log Analytics workspace when you set up Desktop Analytics. You choose the location and copy the commercial ID. This ID identifies your workspace.  
    
    2. When you connect Configuration Manager to Desktop Analytics, it sets the commercial ID on the devices in your target collection. This configuration specifies the devices to appear in your workspace.  

3. Each day Microsoft produces a "snapshot" of IT-focused insights for each workspace in the Diagnostic Data Management service.  

4. These snapshots are copied to transient storage, which is only used by Desktop Analytics. The transient storage is hosted in Microsoft data centers in the United States. The snapshots are segregated by commercial ID.  

5. The snapshots are then copied to the appropriate Azure Log Analytics workspace.  

6. Desktop Analytics stores your configurations in Analytics Azure storage. These configurations include deployment plans and asset upgrade decisions.  
-->


## <a name="other-resources"></a>관련 자료

관련된 개인 정보 보호 측면에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [Windows 10 및 IT 의사 결정자를 위한 GDPR](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance)  

- [조직에서 Windows 진단 데이터를 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)  

- [Windows 7, Windows 8 및 Windows 8.1 평가자 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/appraiser-diagnostic-data-events-and-fields)  

- [Windows 10, 버전 1809 기본 수준 Windows 진단 이벤트 및 필드](https://docs.microsoft.com/windows/privacy/basic-level-windows-diagnostic-events-and-fields-1809)  

- [Windows 10 버전 1709 향상 된 진단 데이터 이벤트 및 데스크톱 분석에서 사용 되는 필드](https://docs.microsoft.com/windows/privacy/enhanced-diagnostic-data-windows-analytics-events-and-fields)  

- [진단 데이터 뷰어 개요](https://docs.microsoft.com/windows/privacy/diagnostic-data-viewer-overview)  

- [라이선스 사용 조건 및 설명서](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)  

- [보안 및 Microsoft Azure 데이터 센터에서 개인 정보](https://azure.microsoft.com/global-infrastructure/)  

- [신뢰할 수 있는 클라우드의 신뢰도](https://azure.microsoft.com/overview/trusted-cloud/)  

- [보안 센터](https://www.microsoft.com/trustcenter)  



## <a name="faq"></a>FAQ

### <a name="can-desktop-analytics-be-used-without-a-direct-client-connection-to-the-microsoft-data-management-service"></a>Microsoft 데이터 관리 서비스에 직접 클라이언트 연결 없이 데스크톱 Analytics는 사용할 수 있습니까?
아니요, 전체 서비스는 장치 되어이 직접 연결 해야 하는 진단 데이터를 Windows에서 구현 됩니다.


### <a name="can-i-choose-the-data-center-location"></a>데이터 센터 위치를 선택할 수 있나요?

Azure Log analytics: 예, 데스크톱 Analytics를 설정 하 고 Log Analytics 작업 영역을 만들 때.

Microsoft 데이터 관리 서비스 및 분석에 대 한 Azure Storage: 아니요, 이러한 두 서비스는 미국에서 호스트 됩니다.

