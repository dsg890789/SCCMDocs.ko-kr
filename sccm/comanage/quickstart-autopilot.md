---
title: 공동 관리를 사용 하 여 Windows Autopilot
titleSuffix: Configuration Manager
description: 새 Windows 10 장치 등록 집합을 간소화 하기 위해 Configuration Manager에서 공동 관리를 사용 하 여 Windows Autopilot을 사용 합니다.
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
ms.sourcegitcommit: ef2960bd91655c741450774e512dd0a9be610625
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56838755"
---
# <a name="windows-autopilot-with-co-management"></a>공동 관리를 사용 하 여 Windows Autopilot

새 Windows 10 장치를 수신 하는 것은 흥미로운 기능입니다. 그러나 수 있도록 모든 설정 및 앱을 구성 하는 데 시간이 걸릴 수 있습니다. 공동 관리는이 장치를 Windows Autopilot을 사용 하 여 문제를 프로 비전을 해결 합니다.

Autopilot와 같은 상황에서 사용자에 대 한 간소화 된 환경을 제공합니다.
- 설정 하 고 새 Windows 10 장치를 미리 구성  
- 다시 설정 하 고 재활용을 기존 장치를 복구  

Autopilot 시간, 리소스 및 배포, 관리 및 장치 사용 중지와 관련 된 복잡성을 줄입니다. 동시에 사용자를 위한 환경은 간소화 하 고 첫 번째 부팅에서 쉽게 합니다.

Windows Autopilot에 공동 관리를 사용 하 여 최대화 됩니다 모든는 여러 가지 시나리오를 지원 합니다.

- 사용자가 하이브리드 Azure AD 조인 된 Active Directory 또는 Azure Active Directory (Azure AD)에 새 장치는 자신의 배포를 유도할 수 있습니다.  

- 공유 장치 및 키오스크에 대 한 Azure AD로 새 장치 배포를 배포 하는 자체를 설정할 수 있습니다.  

- 기존 장치에 대 한 Windows Autopilot을 사용 하 여 Configuration Manager로 기존 장치를 Windows 7 및 Active Directory에서 Windows 10과 Azure AD를 사용  

다음 비디오를 Danny Guillory 선임 프로그램 관리자 Andrew McMurray의 주요 프로그램 관리자에 설명 하 고 공동 관리를 사용 하 여 Windows Autopilot 데모:

> [!VIDEO https://channel9.msdn.com/Series/Endpoint-Zone/Using-Windows-Autopilot-with-Co-Management/player]



## <a name="benefits"></a>이점

공동 관리 및 Autopilot 함께 사용할 수 있도록 새 장치에 네트워크로 유입 결국 관리 동일한 상태에서입니다. 이 설치에서 Intune에 등록 된 장치와 Configuration Manager 클라이언트  새 Windows 10 프로 비전 모델을 사용할 수 있습니다 하 고 만들기, 유지 관리 및 사용자 지정 운영 체제 이미지를 업데이트 하지 않아도 도움이 됩니다. 

이러한 모든 시나리오를 수행할 수 있습니다 자동으로 [공동 관리를 사용 하도록 설정](/sccm/comanage/how-to-prepare-win10) Intune에서. 이 자동화는 지속적으로 장치 관리 및 프로 비전 프로세스를 지원합니다.

Autopilot을 사용 하 여 이미지 및 드라이버에 걱정할 필요가 없습니다. Intune 및 Configuration Manager를 사용 하 여 공동 관리를 통해이 자동화 된 프로세스에 의해 장치를 프로 비전에 집중 합니다.


공동 관리 및 Autopilot을 함께 사용 하는 방법을 지금 바로 다음과 같습니다.

#### <a name="reduce-time-costs-and-complexity"></a>시간, 비용 및 복잡성 줄이기
Windows Autopilot 장치에 미리 설치 되어 있는 Windows 10의 OEM에 최적화 된 버전을 사용 합니다. 이 구성은 조직 사용자 지정 이미지 및 드라이버에서 사용 하 여 장치의 모든 모델에 대 한 유지 관리 해야 노력을 저장 합니다. 장치를 이미지로 다시 설치 하는 대신 기존 Windows 10 설치 "비즈니스 준비" 상태로 변환 합니다. 설정 및 정책 적용, 앱을 설치 하 고 Windows 10의 버전을 변경 합니다. 예를 들어로 Windows 10 Pro에서 Windows 10 Enterprise 고급 기능을 지원할 수 있도록 합니다.

#### <a name="improve-the-user-experience"></a>사용자 환경 개선
최상의 사용자 환경을 중단을 최소화 시키고 해당 작업에 초점을 맞추어 돌아갈 하는 데 도움이 됩니다. Windows Autopilot에 사용자가 간단한 몇 번의 클릭 하 고 Azure AD 자격 증명을 사용 하 여 신속 하 게 설정 하는 데는 간단한 방법을 제공 합니다. 원격 직원의 큰 필드를 사용 하 여 많은 조직에 대 한 새 장치 제조업체에서 바로 전달할 Windows Autopilot을 사용 합니다.

#### <a name="use-autopilot-and-configuration-manager-to-migrate-existing-windows-7-devices-to-windows-10"></a>Autopilot 및 Configuration Manager를 사용 하 여 Windows 10으로 기존 Windows 7 장치를 마이그레이션하려면
기존 장치에 대 한 Windows Autopilot을 사용 하 여 구성 파일을 만들고 Configuration Manager 작업 순서를 사용 하 여 배포 합니다. 이 프로세스는 쉽게 Windows 10에 Windows 7에서 기존 장치를 마이그레이션합니다. Configuration Manager에서 서명 Windows 10 이미지를 사용 하 고이 정보를 Autopilot 구성 사용 하 여 기존 Windows 7 장치에 적용 합니다. 사용자 장치가 시작 되 면 Autopilot 사용자 기반 온 보 딩 프로세스를 사용 합니다.

Autopilot 기존 장치에 대 한 단계는 다음과 같습니다.

![기존 장치에 대 한 Windows Autopilot에 대 한 프로세스 개요](media/autopilot-for-existing-devices.png)

1. OneDrive에 알려진된 폴더 리디렉션 그룹 정책 배포
2. Autopilot 구성 파일 생성
3. Windows 10으로 업그레이드 하는 작업 순서 배포
4. Windows 10 컴퓨터를 거칩니다 Autopilot 처음 부팅 시

#### <a name="modernizing-device-provisioning-for-all-types-of-workers"></a>작업자의 모든 형식에 대 한 장치 프로 비전 현대화
Autopilot을 사용 하 여 이제 unmanned 장치 또는 자체 배포 모드를 사용 하 여 공유 장치 핸 즈 프리 OS 배포를 제공할 수 있습니다. 이 설정을 모든 다양 한 유형의 작업자의 요구를 충족 합니다. 또한 Windows Autopilot Reset 함수를 사용 하면 장치의 새 사용자에 게 다시 프로 비전를 간단 하 고 쉽습니다. 이 프로세스는 계절 했거나 근로자 계약 하는 경우는 어려운 작업 이었습니다 일반적으로 무엇을 간소화 합니다. 



## <a name="case-study"></a>사례 연구

독일어 물류 및 철도 운송 회사 DB Shenker Autopilot 직원 생산성 향상 및 무료 해당 IT 팀에서 일상적인 지원 작업을 사용 합니다. Shenker 기존 이미징 떨어져 있으며 클라우드를 통해 프로 비전으로 대체 합니다. 사용 하 여 Azure AD 가입 및 Intune 신속 하 게 새 장치를 실행 합니다. 

IT 서비스를 사용 하 여 위치로 이동 하 여 원격 작업자 폐기물 시간이 아닌 Shenker는 이제 Windows Autopilot을 사용 합니다. 해당 로컬 필드 office 작업자 하드웨어 제조업체에서 직접 전송 합니다. 인터넷에 새 장치를 연결 하는 작업자 및 Azure AD 자격 증명으로 로그인 합니다. 장치에서 그런 다음 응용 프로그램에 연결 하 고 해당 Schenker services IT 부서는 사용자의 개별 프로필에 할당 합니다.

자세한 내용은 참조 하세요. [전역 물류 회사 중앙 IT, 최신 디지털 작업 영역을 사용 하 여 직원을 결합 합니다.](https://customers.microsoft.com/story/db-schenker-travel-transportation-windows-10)합니다.



## <a name="value-proposition"></a>가치 제안

사용자에 게 더 나은 사용자 환경을 만들어 조직에 대 한 만족도 만듭니다. 비용을 절감 하려면 Windows Autopilot을 사용 합니다. 시간 값과 조직에 대 한 영향을 높이기 위한 다른 프로젝트에 집중을 확보 합니다.



## <a name="configure"></a>구성

자세한 내용은 다음 아티클을 참조하세요.

[Intune을 사용 하 여 Windows Autopilot 프로필을 만들려면](https://docs.microsoft.com/intune/enrollment-autopilot)

[기존 장치에 대 한 Windows Autopilot](/sccm/osd/deploy-use/windows-autopilot-for-existing-devices) 작업 순서

