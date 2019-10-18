---
title: 데스크톱 분석 데이터 개인 정보
titleSuffix: Configuration Manager
description: 데스크톱 분석이 고객 데이터 개인 정보 보호에 커밋 됨
ms.date: 10/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b5606f15-f589-485c-a599-cdabf1a9e7ac
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ca2b94b19c4e95da103799e7357063e7253eaa72
ms.sourcegitcommit: b64ed4a10a90b93a5bd5454b6efafda90ad45718
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72384921"
---
# <a name="desktop-analytics-data-privacy"></a>데스크톱 분석 데이터 개인 정보

데스크톱 분석은 이러한 개념를 중심으로 고객 데이터 개인 정보 보호에 완전히 커밋됩니다.

- **투명도:** Windows 진단 이벤트를 완전히 문서화 합니다. 회사의 보안 및 규정 준수 팀에서 검토 합니다. Windows 진단 데이터 뷰어를 사용 하 여 지정 된 장치에서 전송 된 진단 데이터를 볼 수 있습니다. 자세한 내용은 [진단 데이터 뷰어 개요](https://docs.microsoft.com/windows/configuration/diagnostic-data-viewer-overview)를 참조 하세요.  

- **제어:** Microsoft와 공유할 진단 데이터의 수준을 제어 합니다. Windows 10, 버전 1709, 향상 된 진단 데이터를 데스크톱 분석에서 요구 하는 최소 수로 제한 하는 새 정책을 추가 합니다.  

- **보안:** Microsoft는 강력한 보안 및 암호화를 통해 데이터를 보호 합니다.  

- **신뢰:** 데스크톱 분석은 Microsoft [개인 정보 취급 방침](https://privacy.microsoft.com/privacystatement) 및 [온라인 서비스 약관](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46)을 지원 합니다.  

자세한 내용은 Windows 서비스를 참조 하세요. [여기서 Microsoft는 GDPR 아래](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance#windows-services-where-microsoft-is-the-processor-under-the-gdpr)에 있는 프로세서입니다.<!-- 5353168 -->

## <a name="diagnostic-data-flow"></a>진단 데이터 흐름

다음 그림은 진단 데이터 서비스, Azure Log Analytics 저장소 및 Log Analytics 작업 영역을 통해 개별 장치에서 진단 데이터를 전달 하는 방법을 보여 줍니다.

![장치에서 진단 데이터의 흐름을 보여 주는 다이어그램](media/da-data-flow.png)

1. Azure Portal에 로그인 하 고 데스크톱 분석에 등록 합니다. Configuration Manager와 연결 하기 위해 Azure AD 앱을 만듭니다. 데스크톱 분석을 설정 하는 경우 선택한 위치에 Azure Log Analytics 작업 영역을 만듭니다.  

2. Configuration Manager 연결 하 고 장치를 등록 합니다.  

    1. Azure AD 앱 세부 정보를 사용 하 여 Configuration Manager에서 데스크톱 분석 클라우드 서비스를 구성 합니다.  

    2. 15 분 이내 Configuration Manager는 데스크톱 분석과 장치 컬렉션 및 배포 계획을 동기화 합니다. 1 시간 마다이 프로세스를 반복 합니다.  

    3. Configuration Manager은 상용 ID, 진단 데이터 수준 및 대상 컬렉션의 장치에 대 한 기타 설정을 설정 합니다. 이 구성은 데스크톱 분석 작업 영역에 표시 되는 장치를 지정 합니다.  

    4. 모든 대상 장치에 호환성 업데이트를 배포 합니다.  

3. 장치는 Windows 용 Microsoft 진단 데이터 관리 서비스로 진단 데이터를 보냅니다. 이 서비스는 미국에서 호스팅됩니다.  

4. Microsoft는 매일 IT 중심 정보에 대 한 스냅숏을 생성 합니다. 이 스냅숏은 Windows의 진단 데이터와 등록 된 장치에 대 한 입력을 결합 합니다. 이 프로세스는 데스크톱 분석 에서만 사용 되는 임시 저장소에서 발생 합니다. 임시 저장소는 미국의 Microsoft 데이터 센터에서 호스팅됩니다. 스냅숏은 상업적 ID로 분리 됩니다.  

5. 그러면 스냅숏이 적절 한 Azure Log Analytics 작업 영역에 복사 됩니다.  

6. 데스크톱 분석은 Azure Log Analytics 저장소에 입력을 저장 합니다. 이러한 구성에는 배포 계획과 업그레이드 및 중요도에 대 한 자산 결정이 포함 됩니다.  

## <a name="other-resources"></a>관련 자료

데스크톱 분석에 대 한 개인 정보 관련 질문과 대답은 [개인 정보 FAQ](/sccm/desktop-analytics/faq#privacy)를 참조 하세요.

관련 된 개인 정보 취급 방침에 대 한 자세한 내용은 다음 문서를 참조 하세요.

- [IT 의사 결정자를 위한 Windows 10 및 GDPR](https://docs.microsoft.com/windows/privacy/gdpr-it-guidance)  

- [조직에서 Windows 진단 데이터 구성](https://docs.microsoft.com/windows/privacy/configure-windows-diagnostic-data-in-your-organization)  

- [Windows 7, Windows 8 및 Windows 8.1 평가자 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-8.1-and-8/appraiser-diagnostic-data-events-and-fields)  

- [Windows 10, 버전 1809 기본 수준 Windows 진단 이벤트 및 필드](https://docs.microsoft.com/windows/privacy/basic-level-windows-diagnostic-events-and-fields-1809)  

- [데스크톱 분석에서 사용 하는 Windows 10, 버전 1709 고급 진단 데이터 이벤트 및 필드](https://docs.microsoft.com/windows/privacy/enhanced-diagnostic-data-windows-analytics-events-and-fields)  

- [진단 데이터 뷰어 개요](https://docs.microsoft.com/windows/privacy/diagnostic-data-viewer-overview)  

- [사용 약관 및 설명서](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=31)  

- [Microsoft Azure 데이터 센터에서 보안 및 개인 정보 보호](https://azure.microsoft.com/global-infrastructure/)  

- [신뢰할 수 있는 클라우드의 신뢰도](https://azure.microsoft.com/overview/trusted-cloud/)  

- [보안 센터](https://www.microsoft.com/trustcenter)  
