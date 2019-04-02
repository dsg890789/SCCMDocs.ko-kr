---
title: 공동 관리를 사용하는 조건부 액세스
titleSuffix: Configuration Manager
description: Intune의 준수 규칙에 따라 조직 리소스에 대한 사용자 액세스 제어
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
ms.sourcegitcommit: 9aebc20b25cdef0af908918ccfd791f3264a5d94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "56755205"
---
# <a name="conditional-access-with-co-management"></a>공동 관리를 사용하는 조건부 액세스

조건부 액세스는 신뢰할 수 있는 사용자만 신뢰할 수 있는 디바이스에서 신뢰할 수 있는 앱을 사용하여 조직 리소스에 액세스하도록 합니다. 이 기능은 처음부터 클라우드에서 구축되었습니다. Intune에서 디바이스를 관리하든, 공동 관리를 사용하여 Configuration Manager 배포를 확장하든 이 기능은 똑같이 작동합니다.

다음 비디오에서는 선임 프로그램 관리자 Joey Glocke와 제품 마케팅 관리자 Locky Ainley가 공동 관리를 사용하는 조건부 액세스에 관해 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/The-Security-Benefits-of-Conditional-Access/player]

공동 관리를 사용하는 경우 Intune은 네트워크의 모든 디바이스를 평가하여 얼마나 신뢰할 수 있는지 확인합니다. 이 평가는 다음 두 가지 방법으로 수행합니다.

1. Intune에서는 디바이스 또는 앱이 관리되며 안전하게 구성되어 있는지 확인합니다. 이 확인은 조직의 준수 정책을 어떻게 설정했는지에 따라 달라집니다. 예를 들어 모든 디바이스가 암호화를 사용하도록 설정되어 있고 무단 해제되지 않았는지 확인합니다.  

    - 이 평가는 사전 보안 위반 및 구성을 기반으로 합니다.  

    - 공동 관리하는 디바이스의 경우 Configuration Manager도 구성 기반 평가를 수행합니다. 예를 들어 필수 업데이트 또는 앱을 준수하는지 평가합니다. Intune은 이 평가를 자체 평가와 결합합니다.  

2. Intune은 디바이스에서 활성 보안 인시던트를 검색합니다. [Windows Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-atp/get-started) 및 기타 [모바일 위협 방어 공급자](https://www.lookout.com/about/partners/microsoft)의 지능형 보안을 사용합니다. 이러한 파트너는 디바이스에서 지속적인 동작 분석을 실행합니다. 이 분석에서는 활성 인시던트를 검색한 다음 이 정보를 실시간 준수 평가를 위해 Intune에 전달합니다.  

    - 이 평가는 사전 보안 위반 및 인시던트 기반입니다.  

Microsoft 부사장인 Brad Anderson이 2018 Ignite 키노트 중 라이브 데모를 통해 조건부 액세스에 관해 자세히 설명합니다. 

> [!VIDEO https://www.youtube.com/embed/7tDbUhVCX_I?start=1071]

또한 조건부 액세스를 통해 한곳에서 네트워크로 연결된 모든 디바이스의 상태를 확인할 수 있습니다. 클라우드 규모를 활용할 수 있어서 Configuration Manager 프로덕션 인스턴스를 테스트하는 데 특히 유용합니다.


## <a name="benefits"></a>이점

모든 IT 팀은 네트워크 보안 문제에 시달리고 있습니다. 모든 디바이스의 네트워크 액세스를 허용하기 전에 보안 및 비즈니스 요구 사항에 맞는지 확인하는 일은 필수입니다. 조건부 액세스를 사용하면 다음 요소를 확인할 수 있습니다. 
- 모든 디바이스가 암호화되어 있는지 여부  
- 맬웨어가 설치되어 있는지 여부  
- 설정이 업데이트되어 있는지 여부  
- 무단 해제 또는 루팅되었는지 여부  

조건부 액세스는 어디서든 모든 디바이스에서 조직 데이터에 대한 세부 제어와 작업자 생산성을 극대화하는 사용자 환경을 결합니다.

다음 비디오에서는 [ATP(고급 위협 보호)](https://www.microsoft.com/windowsforbusiness/windows-atp)를 자주 발생하는 일반적인 시나리오와 통합하는 방법을 보여 줍니다.

> [!VIDEO https://www.youtube.com/embed/A7IrxAH87wc?start=178]

공동 관리를 사용하면 Intune에서 Configuration Manager의 기능을 통합하여 필수 업데이트 또는 앱의 보안 표준 준수를 평가할 수 있습니다. 이 동작은 계속 Configuration Manager를 사용하여 복잡한 앱 및 패치 관리하려고 하는 IT 조직에 중요합니다.

조건부 액세스는 [제로 트러스트 네트워크](https://cloudblogs.microsoft.com/microsoftsecure/2018/06/14/building-zero-trust-networks-with-microsoft-365/) 아키텍처를 개발할 때도 중요한 부분입니다. 조건부 액세스를 사용하는 규격 디바이스 액세스 제어는 제로 트러스트 네트워크의 기본 계층입니다. 이 기능은 미래에 조직을 보호하는 방법의 중요한 부분입니다.

자세한 내용은 [Enhancing conditional access with machine-risk data from Windows Defender Advanced Threat Protection](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Enhancing-conditional-access-with-machine-risk-data-from-Windows/ba-p/250559)(Windows Defender Advanced Threat Protection에서 머신 위험 데이터를 사용하여 조건부 액세스 개선)의 블로그 게시물을 참조하세요.



## <a name="case-studies"></a>사례 연구

IT 컨설팅 업체인 Wipro는 조건부 액세스를 사용하여 91,000여 직원이 사용하는 디바이스를 보호하고 관리합니다. 최근 사례 연구에서 Wipro의 IT 담당 부사장은 다음과 같이 설명했습니다.

> *조건부 액세스를 달성한 것은 Wipro에게 큰 성과입니다. 이제 모든 직원이 온디맨드를 정보에 모바일 액세스할 수 있습니다.*
> *보안 상태와 직원 생산성이 향상되었습니다. 이제 91,000여 직원이 어디서나 원하는 디바이스에서 100개 이상의 앱에 안전하게 액세스할 수 있습니다.*

<!-- waiting for the case study to be public
For more information, see [Wipro drives mobile productivity with Microsoft cloud security tools to improve customer engagements](https://customers.microsoft.com/story/446f72f9-2f50-4697-b688-6d279786e010)
-->

다른 예는 다음과 같습니다. 

- Nestle는 150,000명이 넘은 직원을 대상으로 앱 기반 조건부 액세스를 사용합니다.  

- 자동화 소프트웨어 회사 Cadence는 이제 “관리형 디바이스만 Teams 및 회사 인트라넷과 같은 Office 365 앱에 액세스할 수 있습니다." 또한 직원이 “Workday 및 Salesforce 같은 다른 클라우드 기반 앱에도 더 안전하게 액세스”할 수 있습니다. Cadence의 Intune 사용 경험에 대한 자세한 내용은 [Cadence increases the pace of business with mobile collaboration tools in Microsoft 365](https://customers.microsoft.com/story/cadence-partner-professional-services-microsoft-365)(Cadence, Microsoft 365의 모바일 공동 작업 도구로 비즈니스 속도 향상)를 참조하세요.

Intune은 Cisco ISE, Aruba Clear Pass, Citrix NetScaler 등과 같은 파트너와도 완전하게 통합됩니다. 이러한 파트너를 사용하면 이러한 다른 플랫폼 전반에서 Intune 등록 및 디바이스 준수 상태에 따라 액세스 제어를 유지할 수 있습니다.

자세한 내용은 다음 비디오를 참조하세요.
- [Brad Anderson demos conditional access in detail](https://youtu.be/8321obNofgM?t=547)(Brad Anderson의 조건부 액세스 자세한 시연)  
- [Additional detail from Endpoint Zone 1805](https://youtu.be/f-ILlEuBFZg?t=196)(엔드포인트 영역 1805의 추가 정보)  


## <a name="value-proposition"></a>가치 제안

조건부 액세스와 ATP 통합을 사용하면 모든 IT 조직의 기반 구성 요소를 보강하여 클라우드 액세스를 보호할 수 있습니다.

모든 데이터 위반의 63% 이상에서 공격자는 취약한 기본 또는 도난당한 사용자 자격 증명을 통해 조직 네트워크에 액세스합니다. 조건부 액세스는 사용자 ID 보안에 중점을 두므로 자격 증명 절도를 제한합니다. 조건부 액세스는 권한이 있든 없는 사용자 ID를 관리하고 보호합니다. 디바이스와 디바이스에 보관된 데이터를 보호하는 가장 효과적인 방법입니다.

조건부 액세스는 EMS(Enterprise Mobility + Security)의 핵심 구성 요소이므로 온-프레미스 설정이나 아키텍처가 필요하지 않습니다. Intune 및 Azure AD(Azure Active Directory)를 사용하면 클라우드에서 조건부 액세스를 신속하게 구성할 수 있습니다. 현재 Configuration Manager를 사용하는 경우 공동 관리를 사용하여 환경을 클라우드로 쉽게 확장하고 바로 사용할 수 있습니다.

ATP 통합에 대한 자세한 내용은 [Windows Defender ATP device risk score exposes new cyberattack, drives Conditional access to protect networks](https://cloudblogs.microsoft.com/microsoftsecure/2018/11/28/windows-defender-atp-device-risk-score-exposes-new-cyberattack-drives-conditional-access-to-protect-networks/)(Windows Defender ATP 디바이스 위험 점수를 통해 새 사이버 공격을 탐지하고 조건부 액세스를 적용하여 네트워크 보호) 블로그 게시물을 참조하세요. 이 블로그에서는 고급 해커 그룹이 기존에 보지 못한 도구를 사용한 방법을 자세히 설명합니다. Microsoft 클라우드에서는 대상 사용자가 조건부 액세스하므로 이 그룹을 감지하고 중지시켰습니다. 침입으로 디바이스의 위험 기반 조건부 액세스 정책이 활성화되었습니다. 공격자가 이미 네트워크에 진입했지만, 악용된 머신에서 Azure AD로 관리되는 조직 서비스 및 데이터에 액세스하는 권한이 자동으로 제한되었습니다.



## <a name="configure"></a>구성

조건부 액세스는 [공동 관리를 사용하도록 설정](/sccm/comanage/how-to-enable)하면 쉽게 사용할 수 있습니다. 이에 따라 **준수 정책** 워크로드를 Intune 워크로드로 이동해야 합니다. 자세한 내용은 [Configuration Manager 워크로드를 Intune으로 전환하는 방법](/sccm/comanage/how-to-switch-workloads)을 참조하세요. 

조건부 액세스를 사용하는 방법에 대한 자세한 내용은 다음 문서를 참조하세요. 

- [Azure AD의 조건부 액세스](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal)  

- [Intune 디바이스 준수 정책](https://docs.microsoft.com/intune/device-compliance)  

- [Intune을 사용하는 앱 기반 조건부 액세스](https://docs.microsoft.com/intune/app-based-conditional-access-intune)  

> [!Note]  
> 하이브리드 Azure AD 연결 디바이스에서는 조건부 액세스 기능을 즉시 사용할 수 있습니다. 이러한 기능에는 다단계 인증 및 하이브리드 Azure AD 연결 액세스 제어가 포함됩니다. 이 동작은 Azure AD 속성을 기반으로 하기 때문입니다. Intune 및 Configuration Manager에서 구성 기반 평가를 활용하려면 공동 관리를 사용하도록 설정합니다. 이 구성을 사용하면 Intune에서 곧바로 규격 디바이스에 대한 액세스를 제어할 수 있습니다. 또한 Intune의 준수 정책 평가 기능도 이용할 수 있습니다.  

