---
title: 개인정보처리방침 - 추가 정보
titleSuffix: Configuration Manager
description: Microsoft가 System Center Configuration Manager에서 데이터를 수집하고 사용하는 방법에 대해 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1fcc921f-085f-4b0b-9c53-1e0707211076
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e98afcbc4215d3157a361eb35b9df54223df97e0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="additional-information-about-privacy-for-system-center-configuration-manager"></a>System Center Configuration Manager의 개인 정보 보호에 대한 추가 정보

*적용 대상: System Center Configuration Manager(현재 분기)*


## <a name="updates-and-servicing"></a>업데이트 및 서비스
Configuration Manager 배포를 최신 업데이트 및 기능이 있는 최신 상태로 유지할 수 있도록 System Center Configuration Manager에 새 업데이트 모델이 도입되었습니다. 설치되는 경우, 이 기능은 관리자가 선택하는 사이트 서버에서 서비스 연결 지점이라고 하는 새로운 사이트 시스템 역할을 추가합니다. 수집되는 정보와 해당 정보의 사용 방법에 대한 자세한 내용은 이 문서의 사용 현황 데이터 섹션을 참조하세요.


## <a name="usage-data"></a>사용 현황 데이터
System Center Configuration Manager에서는 진단 및 사용 현황 데이터를 수집하며, 이러한 데이터는 Microsoft에서 향후 버전의 설치 환경, 품질 및 보안을 개선하기 위해 사용됩니다.
진단 및 사용 현황 데이터는 각 System Center Configuration Manager 계층 구조에 대해 사용할 수 있습니다. 각 기본 사이트 및 중앙 관리 사이트에서 매주 실행되는 SQL Server 쿼리로 구성됩니다. 계층에서 중앙 관리 사이트를 사용하면 기본 사이트의 데이터가 해당 사이트에 복제됩니다. 계층의 최상위 사이트에서, 서비스 연결 지점은 업데이트를 확인할 때 이 정보를 제출합니다. 서비스 연결점이 오프라인 모드인 경우 서비스 연결 도구를 사용하여 정보가 전송됩니다.

Configuration Manager는 사이트 SQL Server 데이터베이스에서만 데이터를 수집하고 클라이언트 또는 사이트 서버에서 직접 데이터를 수집하지 않습니다.

관리자는 Configuration Manager 콘솔의 **사용 현황 데이터** 섹션으로 이동하여 수집된 데이터의 수준을 변경할 수 있습니다.

자세한 내용은 [System Center Configuration Manager의 진단 및 사용 현황 데이터](https://go.microsoft.com/fwlink/?LinkID=626566)에서 사용 현황 데이터 수준 및 설정에 대한 “자세히” 문서를 참조하세요.


## <a name="customer-experience-improvement-program"></a>사용자 환경 개선 프로그램

> [!Note]  
> Configuration Manager 버전 1802부터 CEIP 기능은 제품에서 제거됩니다.

"CEIP"(사용자 환경 개선 프로그램)는 사용 패턴과 경향을 파악하기 위해 Configuration Manager 콘솔에서 사용자의 하드웨어 구성과 소프트웨어 및 서비스 사용 방식에 대한 기본 정보를 수집하는 기능입니다. 또한 CEIP는 발생한 오류 유형과 개수, 소프트웨어 및 하드웨어 성능, 서비스의 속도를 수집합니다. 그러나 사용자 이름, 주소 또는 기타 연락처 정보는 수집하지 않습니다. 또한 클라이언트 컴퓨터에서는 어떤 CEIP 데이터도 수집하지 않습니다.

수집된 정보는 Microsoft 소프트웨어 및 서비스의 품질, 안정성 및 성능을 개선하는 데 사용됩니다.

CEIP를 통해 수집, 처리 또는 전송되는 정보에 대한 자세한 내용은 [CEIP 개인정보취급방침](https://go.microsoft.com/fwlink/?LinkID=525211)을 참조하세요.

## <a name="operations-management-suite-connector"></a>Operations Management Suite 커넥터
Microsoft Operations Management Suite 커넥터는 System Center Configuration Manager의 컬렉션과 같은 데이터를 Microsoft Operations Management Suite에 동기화합니다. Microsoft Azure 구독 ID와 비밀 키는 관리자가 기능을 구성하는 경우 Configuration Manager 데이터베이스에 저장됩니다. Azure Active Directory 클라이언트 암호 및 Microsoft Operations Management Suite 작업 영역 공유 키는 모두 온-프레미스 System Center Configuration Manager 데이터베이스에 저장됩니다. System Center Configuration Manager와 Microsoft Operations Management Suite 간의 모든 통신은 HTTPS를 사용합니다. 컬렉션에 대한 추가 정보는 임의 원격 분석 데이터 외부에서 Microsoft에 제공되지 않습니다. Microsoft Operations Management Suite가 수집하는 정보에 대한 자세한 내용은 [로그 분석 보안](https://go.microsoft.com/fwlink/?LinkId=823545)을 참조하세요.

## <a name="asset-intelligence"></a>Asset Intelligence
Asset Intelligence를 통해 IT 관리자는 구성 표준에 대한 준수를 정의 및 추적하고, 사전 예방적으로 관리할 수 있습니다. 배포에 대한 계량 및 보고와 실제 및 가상 응용 프로그램 사용을 통해 조직은 소프트웨어 라이선스에 대한 비즈니스 결정을 더욱 원활하게 내릴 수 있고 라이선싱 계약을 준수할 수 있습니다. Configuration Manager 클라이언트의 사용량 데이터를 수집한 후 관리자는 여러 기능을 사용하여 컬렉션, 쿼리, 보고 등의 데이터를 볼 수 있습니다.

동기화할 때마다 확인된 소프트웨어의 카탈로그가 Microsoft에서 다운로드됩니다. IT 관리자가 조직에서 검색된 분류되지 않은 소프트웨어 타이틀에 대한 정보를 Microsoft에 전송하도록 선택할 수 있습니다. 그렇게 하면 소프트웨어 타이틀이 조사되어 카탈로그에 추가됩니다. 이 정보를 업로드하기 전에 대화 상자에서 업로드할 데이터를 표시합니다. 업로드된 데이터는 취소할 수 없습니다. Asset Intelligence는 사용자 또는 컴퓨터에 대한 정보나 라이선스 사용량을 Microsoft에 전송하지 않습니다.

소프트웨어 타이틀이 업로드되면 Microsoft 연구원은 해당 정보를 파악하고 분류한 후 이 기능을 사용하는 다른 모든 고객과 카탈로그의 다른 고객이 사용할 수 있도록 설정합니다. 업로드한 모든 소프트웨어 타이틀이 공개됩니다. 응용 프로그램 및 분류에 대한 정보가 카탈로그의 일부가 되므로, 다른 카탈로그 고객이 다운로드할 수 있습니다. Asset Intelligence 데이터 컬렉션을 구성하고 Microsoft에 정보를 제출할지 여부를 결정하려면 먼저 조직의 개인정보취급방침 요구 사항을 고려하세요.

Asset Intelligence는 기본적으로 System Center Configuration Manager에서 사용되지 않습니다. 분류되지 않은 타이틀 업로드는 자동으로 발생하지 않으며 시스템에서 이 작업을 자동화하도록 설정할 수 없습니다. 각 소프트웨어 타이틀의 업로드는 수동으로 선택하고 승인해야 합니다.

## <a name="endpoint-protection"></a>Endpoint Protection
Microsoft 클라우드 보호 서비스는 이전에는 MAPS(Microsoft 활성 보호 서비스)라고 했습니다.
해당하는 제품은 System Center Endpoint Protection 및 System Center Configuration Manager의 Endpoint Protection 기능(System Center Endpoint Protection 및 Windows 10용 Windows Defender 관리)입니다. Linux용 System Center Endpoint Protection 또는 Mac용 System Center Endpoint Protection에는 이 기능이 구현되지 않습니다.

Microsoft 클라우드 보호 서비스의 맬웨어 방지 커뮤니티는 System Center Endpoint Protection 사용자를 포함하는 자발적인 전 세계 온라인 커뮤니티입니다. Microsoft 클라우드 보호 서비스에 가입하면 System Center Endpoint Protection에서는 자동으로 정보를 Microsoft에 보냅니다. Microsoft에서는 이 정보를 사용하여 잠재적인 위협을 조사할 소프트웨어를 결정하고 System Center Endpoint Protection의 효율성을 개선하도록 지원합니다. 이 커뮤니티는 새로운 악성 소프트웨어 감염의 확산을 막기 위해 지원합니다. Microsoft 클라우드 보호 서비스 보고서에 맬웨어 또는 Endpoint Protection 클라이언트가 제거할 수도 있는 사용자 동의 없이 설치된 소프트웨어가 포함되어 있는 경우 Microsoft 클라우드 보호 서비스에서 최신 서명을 다운로드하여 문제를 해결합니다. 또한 Microsoft 클라우드 보호 서비스는 "긍정 오류", 즉 처음에는 악성 소프트웨어로 식별되었다가 악성이 아닌 것으로 판별된 프로그램을 찾아서 수정할 수 있습니다.

Microsoft 클라우드 보호 서비스 보고서에는 파일 이름, 암호화 해시, 공급업체, 크기 및 날짜 스탬프 등 잠재적인 맬웨어 파일에 대한 정보가 포함되어 있습니다. 또한 Microsoft 클라우드 보호 서비스는 파일의 원본을 가리키는 전체 URL을 수집할 수도 있습니다. 이러한 URL에는 경우에 따라 양식에 입력한 검색 단어 또는 데이터와 같은 개인 정보가 포함될 수 있습니다. 또한 Endpoint Protection에서 사용자 동의 없이 설치된 소프트웨어에 대한 알림을 받았을 때 수행한 작업이 보고서에 포함될 수 있습니다. Microsoft 클라우드 보호 서비스 보고서에 포함된 이 정보를 통해 Microsoft에서 Endpoint Protection이 얼마나 효과적으로 맬웨어 및 사용자 동의 없이 설치된 소프트웨어를 검색하고 제거하는지 측정할 수 있으며 새로운 맬웨어를 식별할 수 있습니다.

기본 또는 고급 멤버 자격이 있는 경우 Microsoft 클라우드 보호 서비스에 가입할 수 있습니다. 일반 멤버 보고서에는 이전에 설명한 정보가 포함됩니다. 고급 멤버 보고서는 보다 종합적이며, Endpoint Protection이 검색한 소프트웨어에 대한 추가적인 세부 정보(예: 해당 소프트웨어 위치, 파일 이름, 소프트웨어 작동 방법, 컴퓨터에 영향을 주는 방법)를 포함할 수 있습니다. Microsoft 연구원들이 이러한 보고서와 함께 Microsoft 클라우드 보호 서비스에 참여하는 다른 Endpoint Protection 사용자의 보고서를 사용하여 새로운 위험을 신속하게 검색합니다. 그런 다음 분석 조건을 충족하는 프로그램에 대한 맬웨어 정의를 만들고 Microsoft 업데이트를 통해 모든 사용자가 업데이트된 정의를 사용할 수 있도록 합니다.

특정 종류의 맬웨어 감염을 쉽게 검색하고 수정하기 위해 제품은 사용자 PC의 보안 상태에 대한 정보를 Microsoft 클라우드 보호 서비스에 보냅니다. 이 정보에는 PC를 시작하는 동안 로드되는 드라이버 및 기타 소프트웨어를 기술하는 PC의 보안 설정 및 로그 파일에 대한 정보가 포함됩니다.
PC를 고유하게 식별하는 번호도 전송됩니다. 또한 Microsoft 클라우드 보호 서비스가 잠재적인 맬웨어 파일에서 연결하는 IP 주소를 수집할 수 있습니다.

Microsoft 클라우드 보호 서비스 보고서는 Microsoft 소프트웨어 및 서비스를 개선하는 데 사용됩니다. 또한 통계, 기타 테스트 또는 분석용으로 사용되거나 정의를 생성하는 데 사용될 수도 있습니다. 업무상 보고서를 사용해야 하는 Microsoft 직원, 수급인, 파트너 및 공급업체만이 이러한 보고서에 액세스할 수 있습니다.

Microsoft 클라우드 보호 서비스는 개인 정보를 의도적으로 수집하지 않습니다. Microsoft 클라우드 보호 서비스에서 개인 정보를 수집하는 경우 Microsoft는 사용자를 식별하거나 사용자에게 연락하는 데 이러한 정보를 사용하지 않습니다.

수집된 데이터에 대한 추가적인 세부 정보는 [System Center Configuration Manager의 Endpoint Protection](https://go.microsoft.com/fwlink/?LinkId=823547)에 있는 제품 문서에서 찾을 수 있습니다.

## <a name="site-hierarchy--geographical-view-with-bing-maps"></a>사이트 계층 - Bing 지도를 사용하는 지리적 보기
사이트 계층 구조 – 지리적 보기를 통해 Microsoft Bing 지도에서 제공하는 지도를 사용하여 Configuration Manager 실제 서버 토폴로지를 볼 수 있도록 합니다. 이 기능을 사용할 수 있도록 사용자 서버에서 Bing 지도 웹 서비스로 사용자가 제공한 위치 정보가 전송됩니다.

Microsoft는 정보를 사용하여 Microsoft Bing 지도와 기타 Microsoft 사이트 및 서비스를 작동하고 개선합니다. 자세한 내용은 [Microsoft 개인정보취급방침](https://go.microsoft.com/fwlink/?LinkId=823548)을 참조하세요.
사이트 계층에 대한 지리적 보기를 사용하지 않도록 선택할 수 있습니다. 계층 구조 다이어그램 보기에서 계층 구조를 볼 수 있으며, 이 보기에서는 Bing 지도 서비스가 사용되지 않습니다.

## <a name="microsoft-intune-subscription"></a>Microsoft Intune 구독
Microsoft Intune의 구독을 구매한 고객은 Configuration Manager를 사용하여 Microsoft Intune을 통해 연결된 모바일 장치를 관리할 수 있습니다. [Microsoft Online Services 개인정보취급방침](https://go.microsoft.com/fwlink/?LinkId=262214)은 Microsoft Intune을 비롯한 Microsoft Online Services에 적용됩니다. 고객이 Microsoft Intune도 구독하고 있는 경우에도 [Microsoft Online Services 개인정보취급방침](https://go.microsoft.com/fwlink/?LinkId=262214)은 이 개인정보취급방침과 함께 확인해야 합니다.

Microsoft Intune과의 모든 통신은 HTTPS를 사용합니다. Microsoft Intune 구독을 구성하고 iOS 지원 구성에 필요한 CSR(인증서 서명 요청)을 다운로드하려면 관리자가 회사 계정 및 암호를 사용하여 Microsoft Intune에 로그인해야 합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. Microsoft Intune과의 모든 다른 통신은 Microsoft Intune에서 자동으로 생성되는 PKI 인증서를 사용하여 인증됩니다.

Microsoft Intune에 연결된 장치를 관리하기 위해 일부 정보는 Microsoft Intune에 전송하고 일부 정보는 Microsoft Intune에서 수신합니다. 이 정보에는 서비스에 할당된 모든 사용자의 UPN(사용자 계정 이름)과 Microsoft Intune을 통해 관리되는 장치에 대한 장치 인벤토리 정보가 포함됩니다. Manage.Microsoft.com 배포 지점에 할당된 콘텐츠의 메타데이터(예: 응용 프로그램 이름, 게시자, 버전 등)가 Microsoft Intune으로 전송됩니다. Manage.Microsoft.com 배포 지점에 할당되는 실제 이진 콘텐츠는 Microsoft Intune에 업로드되기 전에 암호화됩니다.

이 기능은 기본적으로 구성되어 있지 않습니다. 관리자가 Manage.Microsoft.com 배포 지점으로 전송되는 콘텐츠와 서비스에 할당되는 사용자를 제어합니다. 이 기능은 언제든 제거할 수 있습니다.
