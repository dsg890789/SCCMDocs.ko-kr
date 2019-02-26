---
title: 공동 관리를 사용 하 여 조건부 액세스
titleSuffix: Configuration Manager
description: Intune에서 규정 준수 규칙에 따라 조직 리소스에 대 한 사용자 액세스 제어
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 4cf640b3-610c-4c3c-b966-c62e9f5654ff
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2d5e5c7d6075697431f8c537366dc16164fedd1f
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755205"
---
# <a name="conditional-access-with-co-management"></a>공동 관리를 사용 하 여 조건부 액세스

조건부 액세스는 신뢰할 수 있는 사용자만 신뢰할 수 있는 앱을 사용 하 여 신뢰할 수 있는 장치에서 조직 리소스에 액세스할 수 있도록 합니다. 이 클라우드에서 처음부터 구축 됩니다. Intune 또는 Configuration Manager 배포 공동 관리를 사용 하 여 확장을 사용 하 여 장치를 관리 하 든 동일 하 게를 작동 합니다.

다음 비디오에서 선임 프로그램 관리자 Joey Glocke 제품 마케팅 관리자 Locky Ainley 설명 하 고 공동 관리를 사용 하 여 조건부 액세스를 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/The-Security-Benefits-of-Conditional-Access/player]

공동 관리를 사용 하 여 Intune 인지 어떻게 신뢰할 수 있는 네트워크의 모든 장치를 평가 합니다. 다음 두 가지 방법으로이 평가 수행합니다.

1. Intune을 사용 하면 있는지 장치 또는 앱을 관리 하 고 안전 하 게 구성 합니다. 이 검사는 조직의 준수 정책을 설정 하는 방법에 따라 달라 집니다. 예를 들어, 모든 장치 암호화가 설정 될 및 탈 옥 되지 해야 합니다.  

    - 이 평가 사전 보안 위반 및 구성 기준  

    - 공동 관리 장치에 대 한 Configuration Manager 또한 구성 기준 평가 수행합니다. 예를 들어, 업데이트 또는 앱 준수가 필요합니다. Intune이이 평가 자체 평가 함께 결합합니다.  

2. Intune 장치에서 활성 보안 인시던트를 검색합니다. 지능형 보안을 사용 하 여 [Windows Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/get-started) 및 기타 [모바일 위협 방어 공급자](https://www.lookout.com/about/partners/microsoft)합니다. 이러한 파트너는 장치에서 지속적으로 동작 분석을 실행합니다. 이 분석 활성 인시던트가 검색 하 고 그런 다음 실시간 규정 준수 평가 위해 Intune에이 정보를 전달 합니다.  

    - 이 평가판은 후 보안 위반 및 인시던트 기반  

Microsoft 회사 부사장 인 Brad Anderson 중 2018 Ignite 키 노트 라이브 데모를 사용 하 여 깊이에서 조건부 액세스를 설명합니다. 

> [!VIDEO https://www.youtube.com/embed/7tDbUhVCX_I?start=1071]

또한 조건부 액세스는 네트워크에 연결 된 모든 장치의 상태를 볼 수 있는 중앙된 위치를 제공 합니다. 특히 테스트 Configuration Manager 프로덕션 인스턴스에 대 한 유용한는 클라우드 규모의 이점을 얻게 됩니다.


## <a name="benefits"></a>이점

모든 IT 팀은 네트워크 보안을 사용 하 여 obsessed 됩니다. 네트워크에 액세스 하기 전에 모든 장치 보안 및 비즈니스 요구 사항을 충족 하는지 확인 하는 것이 반드시 합니다. 조건부 액세스를 사용 하 여 다음 요소를 확인할 수 있습니다. 
- 모든 장치에서 암호화 된 경우  
- 맬웨어 설치 된 경우  
- 해당 설정을 업데이트 하는 경우  
- 무단 해제 또는 루 팅 된 경우  

조건부 액세스 어디서 든 모든 장치에서 작업자의 생산성을 최대화 하는 사용자 환경을 세부적으로 제어할 조직 데이터를 결합 합니다.

비디오에서는 다음 방법을 [스레드 보호 고급](https://www.microsoft.com/windowsforbusiness/windows-atp) (ATP)은 정기적으로 발생 하는 일반적인 시나리오를 통합 합니다.

> [!VIDEO https://www.youtube.com/embed/A7IrxAH87wc?start=178]

공동 관리를 사용 하 여 Intune 필수 업데이트 또는 앱의 보안 표준 준수를 평가 하는 것에 대 한 Configuration Manager의 책임을 통합할 수 있습니다. 이 동작은 복잡 한 앱 및 패치 관리에 대 한 Configuration Manager를 사용 하 여 계속 하려는 모든 IT 조직에 중요 합니다.

조건부 액세스 개발의 중요 한 부분 이기도 하 [0 신뢰 네트워크](https://cloudblogs.microsoft.com/microsoftsecure/2018/06/14/building-zero-trust-networks-with-microsoft-365/) 아키텍처입니다. 조건부 액세스 준수 장치 액세스 제어 0 신뢰 네트워크의 기본 계층이 포함 됩니다. 이 기능은 많은 부분이 나중에 조직의 보호 하는 방법을 설명 합니다.

자세한 내용은 블로그 게시물에서 참조 하세요 [Windows Defender Advanced Threat Protection에서 컴퓨터 위험 데이터를 사용 하 여 조건부 액세스를 향상](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Enhancing-conditional-access-with-machine-risk-data-from-Windows/ba-p/250559)합니다.



## <a name="case-studies"></a>사례 연구

IT 컨설팅 업체인 Wipro 조건부 액세스를 사용 하 여 보호 하 고 모든 91,000 직원이 사용 하는 장치를 관리 합니다. 최근 사례 연구의 부사장에 명시 된 Wipro에서 IT:

> *조건부 액세스를 달성 Wipro에 큰 장점입니다. 이제 모든 직원 모바일 액세스 요청에 대 한 정보를 경우 * 
>  *보안 상태 및 직원 생산성을 향상 했습니다. 100 개 이상의 보안 수준이 높은 액세스 로부터 91,000 직원 혜택 이제 어디서 든 모든 장치에서 앱.*

<!-- waiting for the case study to be public
For more information, see [Wipro drives mobile productivity with Microsoft cloud security tools to improve customer engagements](https://customers.microsoft.com/story/446f72f9-2f50-4697-b688-6d279786e010)
-->

다른 예입니다. 

- Nestle 150,000 개 직원에 대 한 앱 기반 조건부 액세스를 사용 하는  

- 자동화 소프트웨어 회사 케이 던스, 이제 수행할 수 있는지 "관리 되는 장치만 회사의 인트라넷 팀 등 Office 365 앱에 대 한 액세스." 제공할 수도 있습니다 인력의 "Workday 및 Salesforce와 같은 다른 클라우드 기반 앱으로 안전 하 게 액세스 합니다." Intune 사용 하 여 흐름의 환경에 대 한 자세한 내용은 참조 하세요. [주기로 Microsoft 365의 모바일 공동 작업 도구를 사용 하 여 비즈니스의 속도 증가](https://customers.microsoft.com/story/cadence-partner-professional-services-microsoft-365)합니다.

Intune은 Cisco ISE, Aruba Clear Pass, Citrix NetScaler 등 파트너와 완전 하 게 통합 됩니다. 이러한 파트너를 사용 하 여 이러한 다른 플랫폼에서 Intune 등록 및 장치 준수 상태에 따라 액세스 제어를 유지할 수 있습니다.

자세한 내용은 다음 비디오를 참조 하세요.
- [Brad Anderson 데모 세부 정보에서 조건부 액세스를 보여 줍니다.](https://youtu.be/8321obNofgM?t=547)  
- [끝점 영역 1805에서 추가 세부 정보](https://youtu.be/f-ILlEuBFZg?t=196)  


## <a name="value-proposition"></a>가치 제안

조건부 액세스와 ATP 통합을 사용 하면 모든 IT 조직의 기본 구성 요소를 기능 보강 하 고: 클라우드 액세스를 보호 합니다.

63% 이상 모든 데이터 침해, 공격자는 약하거나 기본, 도난 당한 사용자 자격 증명을 통해 조직의 네트워크 액세스할을 수 있습니다. 조건부 액세스는 사용자 id를 보안에 중점을 두고, 때문에 자격 증명 도난 완화를 제한 합니다. 조건부 액세스를 관리 및 권한 또는 권한 없는 사용자 id를 보호 합니다. 장치 및 데이터를 보호할 수 없는 더 나은 방법이 있습니다.

조건부 액세스는 Enterprise Mobility + Security (EMS)의 핵심 구성 요소, 이므로 온-프레미스 설치 나 설정이 필요한 아키텍처입니다. Intune 및 Azure Active Directory (Azure AD)를 사용 하 여 클라우드에서 조건부 액세스를 신속 하 게 구성할 수 있습니다. Configuration Manager에서 현재 사용 중인 경우 쉽게 환경의 공동 관리를 사용 하 여 클라우드로 확장를 지금 바로 사용을 시작 합니다.

ATP 통합에 대 한 자세한 내용은이 블로그 게시물을 참조 하세요 [Windows Defender ATP 장치 위험 점수 새 cyberattack 노출, 네트워크 보호에 대 한 조건부 액세스를 드라이브](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/28/windows-defender-atp-device-risk-score-exposes-new-cyberattack-drives-conditional-access-to-protect-networks/)합니다. 방법 표시 도구는 이전에 사용 되는 고급 해커가 그룹을 자세히 설명 합니다. Microsoft cloud 감지 하 고 대상된 사용자는 조건부 액세스를 갖고 있기 때문에 중지 합니다. 침입 장치 위험 기반 조건부 액세스 정책을 활성화 합니다. 공격자가 이미 설정 된 한 발판을 마련 네트워크에 있지만 악용된 컴퓨터 자동으로 제한 되었습니다 액세스 로부터 조직 서비스를 Azure AD에서 관리 하는 데이터입니다.



## <a name="configure"></a>구성

조건부 액세스는 쉽게 사용할 수 있습니다 [공동 관리를 사용 하도록 설정](/sccm/comanage/how-to-enable)합니다. 이동 해야 하는 **준수 정책을** Intune 워크 로드. 자세한 내용은 [Configuration Manager 워크로드를 Intune으로 전환하는 방법](/sccm/comanage/how-to-switch-workloads)을 참조하세요. 

조건부 액세스를 사용 하는 방법에 대 한 자세한 내용은 다음 문서를 참조 하세요. 

- [Azure AD의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)  

- [Intune 장치 준수 정책](https://docs.microsoft.com/intune/device-compliance)  

- [Intune 사용한 앱 기반 조건부 액세스](https://docs.microsoft.com/intune/app-based-conditional-access-intune)  

> [!Note]  
> 조건부 액세스 기능 가능해 즉시 하이브리드 Azure AD에 가입 된 장치입니다. 이러한 기능에는 multi-factor authentication 및 하이브리드 Azure AD 조인 액세스 제어 포함 됩니다. 이 동작은 Azure AD 속성을 토대로 하는 것입니다. Intune 및 Configuration Manager에서 구성 기준 평가 활용 하려면 공동 관리를 사용 하도록 설정 합니다. 규격 장치에 대해 Intune에서 곧바로 액세스 제어를 제공 하는 구성 합니다. 또한, Intune의 준수 정책 평가 기능을 제공합니다.  

