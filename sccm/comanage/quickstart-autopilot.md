---
title: 공동 관리를 사용하는 Windows Autopilot
titleSuffix: Configuration Manager
description: Configuration Manager에서 Windows Autopilot과 공동 관리를 함께 사용하여 새 Windows 10 디바이스의 설정을 간소화합니다.
ms.date: 02/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e3e3c97f-5945-49ab-a622-9f6fe6b9737e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 28710b925444d681a161eff184b845a1cdd430b1
ms.sourcegitcommit: 9aebc20b25cdef0af908918ccfd791f3264a5d94
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/27/2019
ms.locfileid: "56838755"
---
# <a name="windows-autopilot-with-co-management"></a>공동 관리를 사용하는 Windows Autopilot

새 Windows 10 디바이스를 받는 건 즐거운 일입니다. 하지만 모든 설정과 앱을 구성하여 생산적으로 일할 준비를 하는 데에는 시간이 걸릴 수 있습니다. 공동 관리에서는 Windows Autopilot을 사용하여 이 디바이스 프로비저닝 문제를 해결합니다.

Autopilot에서는 다음과 같은 상황에 귀하와 귀하의 사용자를 위한 간소화된 환경을 제공합니다.
- 새 Windows 10 디바이스 설정 및 미리 구성  
- 기존 디바이스 재설정, 재생 및 복구  

Autopilot은 디바이스 배포, 관리 및 사용 중지와 관련된 시간, 리소스 및 복잡성을 줄입니다. 동시에 사용자의 환경을 처음 부팅할 때부터 효율적이고 간소하게 만듭니다.

Windows Autopilot에서는 여러 시나리오를 지원하며, 이들 모두 공동 관리를 사용하면 효율이 극대화됩니다.

- 사용자가 새 디바이스를 하이브리드 Azure AD 연결을 사용하여 Active Directory로 또는 Azure AD(Azure Active Directory)로 자체 배포할 수 있습니다.  

- 새 디바이스를 공유 디바이스 및 키오스크용 Azure AD로 자체 배포하도록 설정할 수 있습니다.  

- 기존 디바이스를 위한 Windows Autopilot에서는 Configuration Manager를 사용하여 기존 디바이스를 Windows 7 및 Active Directory에서 Windows 10 및 Azure AD로 마이그레이션합니다.  

다음 비디오에서는 선임 프로그램 관리자 Danny Guillory와 수석 프로그램 관리자 Andrew McMurray가 공동 관리를 사용하는 Windows Autopilot에 관해 논의하고 시연합니다.

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Using-Windows-Autopilot-with-Co-Management/player]



## <a name="benefits"></a>이점

공동 관리와 Autopilot을 함께 사용할 때는 네트워크로 진입하는 새 디바이스를 같은 관리 상태가 되게 합니다. 이 설정에서 디바이스는 Intune에 등록되고 Configuration Manager 클라이언트를 가집니다.  따라서 새 Windows 10 프로비저닝 모델을 사용할 수 있고 사용자 지정 OS 이미지를 만들고, 유지하고, 업데이트할 필요를 없앨 수 있습니다. 

이러한 모든 시나리오에서 자동으로 Intune에서 [공동 관리를 사용하도록 설정](/sccm/comanage/how-to-prepare-win10)할 수 있습니다. 이 자동화는 프로비저닝 프로세스와 지속적인 디바이스 관리에 도움이 됩니다.

Autopilot을 사용하면 이미지와 드라이버에 신경 쓸 필요가 없습니다. 공동 관리를 통해 Intune과 Configuration Manager를 사용한 이 자동화된 프로세스에 따라 디바이스를 프로비저닝하는 데에 집중합니다.


공동 관리와 Autopilot을 함께 사용하여 지금 바로 얻을 수 있는 이점은 다음과 같습니다.

#### <a name="reduce-time-costs-and-complexity"></a>시간, 비용 및 복잡성 줄이기
Windows Autopilot은 디바이스에 사전 설치된 OEM에 최적화된 버전의 Windows 10을 사용합니다. 이 구성에서는 조직이 사용 중인 각 디바이스 모델의 사용자 지정 이미지와 드라이버를 유지 관리할 필요가 없습니다. 디바이스를 이미지로 다시 설치하지 않고 기존 Windows 10 설치를 “비즈니스 지원” 상태로 변환할 수 있습니다. 즉, 설정과 설정을 적용하고, 앱을 설치하고, Windows 10의 버전을 변경합니다. 예를 들어 Windows 10 Pro에서 Windows 10 Enterprise로 업그레이드하여 고급 기능을 지원할 수 있습니다.

#### <a name="improve-the-user-experience"></a>사용자 환경 개선
최상의 사용자 환경을 통해 중단을 최소화하고 다시 작업에 집중할 수 있도록 도와줍니다. Windows Autopilot에서는 사용자가 몇 번의 간단한 클릭과 Azure AD 자격 증명을 사용하여 빠르게 설정할 수 있는 간소한 접근 방식을 제공합니다. 광범위한 원격 직원을 보유한 많은 조직의 경우 Windows Autopilot을 사용하여 제조업체에서 직접 새 디바이스를 배송합니다.

#### <a name="use-autopilot-and-configuration-manager-to-migrate-existing-windows-7-devices-to-windows-10"></a>Autopilot 및 Configuration Manager를 사용하여 기존 Windows 7 디바이스를 Windows 10으로 마이그레이션
기존 디바이스를 위한 Windows Autopilot에서는 Configuration Manager 작업 순서에 따라 구성 파일을 만들고 배포합니다. 이 프로세스에서 기존 디바이스를 Windows 7에서 Windows 10으로 간단히 마이그레이션합니다. Configuration Manager에서 서명 Windows 10 이미지를 사용하고 기존 Windows 7 디바이스에 Autopilot 구성과 함께 적용합니다. 사용자는 디바이스를 시작할 때 Autopilot 사용자 구동 등록 프로세스를 사용합니다.

기존 디바이스용 Autopilot의 단계는 다음과 같습니다.

![기존 디바이스용 Windows Autopilot의 프로세스 개요](media/autopilot-for-existing-devices.png)

1. 알려진 폴더를 OneDrive에 리디렉션하도록 그룹 정책 배포
2. Autopilot 구성 파일 생성
3. Windows 10으로 업그레이드하는 작업 순서 배포
4. Windows 10 머신이 처음 부팅할 때 Autopilot 단계 수행

#### <a name="modernizing-device-provisioning-for-all-types-of-workers"></a>모든 작업자 유형을 위한 디바이스 프로비저닝 현대화
Autopilot을 사용하면 이제 자체 배포 모드를 사용하여 무인 디바이스 또는 공유 디바이스에 자동 처리 OS 배포를 제공할 수 있습니다. 이 설정은 다양한 작업자 유형 모두의 요구를 충족합니다. 또한 Windows Autopilot 재설정 기능을 사용하면 새 사용자에서 디바이스를 간단하고 쉽게 다시 프로비저닝할 수 있습니다. 이 프로세스는 계절 근로자나 계약직이 있을 경우 기존에 어려웠던 작업을 간소화합니다. 



## <a name="case-study"></a>사례 연구

독일어 물류 및 철도운송 회사 DB Shenker는 Autopilot을 사용하여 직원 생산성을 향상하고 IT 팀의 일상적인 지원 작업 부담을 덜고 있습니다. Shenker는 기존 이미징에서 벗어나 클라우드를 통한 프로비저닝으로 대체했습니다. 이제는 Azure AD 연결과 Intune을 사용하여 새 디바이스를 신속하게 실행합니다. 

원격 직원이 IT 서비스가 제공되는 위치로 이동하느라 시간을 낭비하지 않게 하고 Shenker는 이제 Windows Autopilot을 사용합니다. 하드웨어를 제조업체에서 직접 작업자의 지역 현장 사무소로 배송합니다. 작업자는 새 디바이스를 인터넷에 연결하고 자신의 Azure AD 자격 증명으로 로그인합니다. 그러면 디바이스는 Schenker IT 부서에서 사용자의 개별 프로필에 할당하는 애플리케이션 및 서비스에 연결됩니다.

자세한 내용은 [Global logistics firm centralizes IT, unites employees with modern digital workplace](https://customers.microsoft.com/story/db-schenker-travel-transportation-windows-10)(글로벌 물류 회사, 최신 디지털 작업 공간을 통해 IT 중앙 집중화 및 직원 통합)를 참조하세요.



## <a name="value-proposition"></a>가치 제안

사용자를 위한 더 나은 사용자 환경을 조성하여 조직의 만족도를 높입니다. Windows Autopilot을 사용하여 비용을 절감합니다. 가치를 증진하고 조직에 영향을 주는 다른 프로젝트에 집중할 시간을 확보합니다.



## <a name="configure"></a>구성

자세한 내용은 다음 아티클을 참조하세요.

[Intune을 사용하여 Windows Autopilot 프로필 만들기](https://docs.microsoft.com/intune/enrollment-autopilot)

[Windows Autopilot for existing devices](/sccm/osd/deploy-use/windows-autopilot-for-existing-devices)(기존 디바이스용 Windows Autopilot) 작업 순서

