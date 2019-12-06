---
title: Desktop Analytics에 대한 FAQ
titleSuffix: Configuration Manager
description: Desktop Analytics에 대한 질문과 대답입니다.
ms.date: 11/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e0db3311-2303-4013-a906-76b408172d3c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ce8f76438e38cb9266750da573103296f92a668e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73704937"
---
# <a name="desktop-analytics-faq"></a>Desktop Analytics FAQ

## <a name="prerequisites"></a>필수 구성 요소

### <a name="bkmk_intune"></a> Intune 관리 디바이스에서 Desktop Analytics를 사용할 수 있나요? 

Desktop Analytics 워크플로의 이점을 누릴 수 있는 대다수의 고객은 Configuration Manager를 사용하여 Windows를 배포할 수 있습니다. Intune 고객은 분석 데이터의 추가 인사이트를 선호하며, 그러한 고객들과 인사이트를 공유하는 방법에 대해 연구하고 있습니다.

### <a name="its-been-over-72-hours-and-the-portal-is-still-processing-data-what-next"></a>72시간이 지나 포털에서 여전히 데이터를 처리하고 있는데, 그 다음에는 어떻게 되나요? 

Desktop Analytics를 처음 설정하는 경우 Configuration Manager 및 Desktop Analytics 포털의 보고서에 전체 데이터가 즉시 표시되지 않을 수 있습니다. 서비스가 데이터를 처리하는 데 2-3일이 소요될 수 있습니다. 72시간이 지나 포털에서 여전히 데이터를 처리하고 있는 경우 다음과 같은 단계를 따릅니다.

- 활성 디바이스가 올바르게 구성되었는지 확인하려면 [연결 상태 대시보드](/sccm/desktop-analytics/monitor-connection-health)를 사용합니다. 이 대시보드는 실시간으로 업데이트되지 않습니다.
- 디바이스에서 진단 데이터를 Desktop Analytics 서비스로 전송하는지 확인합니다. 자세한 내용은 [데이터 공유를 사용하도록 설정](/sccm/desktop-analytics/enable-data-sharing)을 참조하세요.
- Azure AD에서 [Azure AD 애플리케이션](/sccm/desktop-analytics/troubleshooting#bkmk_AzureADApps)을 프로비저닝합니다.
- 지난 7일간 조직에 연결된 디바이스를 확인합니다. [Desktop Analytics 포털](https://aka.ms/desktopanalytics)에서 **연결된 서비스** 창으로 이동합니다. **디바이스 등록**, **최근 데이터 보기**를 차례로 선택합니다.

디바이스가 올바르게 구성되어 있지만 작업 영역에 데이터가 표시되지 않는 경우 [Microsoft 지원에 문의](https://support.microsoft.com/hub/4343728/support-for-business)하세요.

## <a name="connect-configuration-manager"></a>Configuration Manager 연결

### <a name="can-i-change-the-target-or-additional-collections"></a>대상 또는 추가 컬렉션을 변경할 수 있나요?

예, 다음 절차를 사용하세요.

- Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **Azure 서비스** 노드를 선택합니다. Desktop Analytics 서비스와 연결된 항목의 속성을 엽니다.

- **Desktop Analtyics 연결** 탭에서 **대상 컬렉션**을 변경하거나 추가 컬렉션을 관리합니다.

> [!IMPORTANT]  
> Configuration Manager는 설정 정책을 사용하여 대상 컬렉션에서 디바이스를 구성합니다. 이 정책에는 디바이스가 Microsoft로 데이터를 보낼 수 있도록 하는 진단 데이터 설정이 포함되어 있습니다. 대상 컬렉션을 변경해도 대상 컬렉션에 더 이상 없는 디바이스에 대한 설정 정책은 실행 취소되지 않습니다. 디바이스에서 진단 데이터를 더 이상 전송하지 않도록 하려면 [디바이스를 다시 구성](/sccm/desktop-analytics/account-close#reconfigure-clients)합니다.

## <a name="windows-upgrade"></a>Windows 업그레이드

### <a name="can-i-upgrade-windows-and-change-architecture"></a>Windows를 업그레이드하고 아키텍처를 변경할 수 있나요?

Desktop Analytics는 현재 위치 업그레이드를 가장 잘 지원하도록 설계되었습니다. 현재 위치 업그레이드는 32비트에서 64비트 아키텍처로의 마이그레이션을 지원하지 않습니다. 이 시나리오에서 컴퓨터를 마이그레이션해야 하는 경우 새로 고침 시나리오를 사용합니다. Desktop Analytics 인사이트는 이 시나리오에서 여전히 중요하지만 업그레이드 관련 지침을 무시할 수 있습니다.

자세한 내용은 [새 버전의 Windows로 기존 컴퓨터 새로 고침](/sccm/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)을 참조하세요.

### <a name="can-i-change-from-bios-to-uefi-when-upgrading-windows"></a>Windows를 업그레이드할 때 BIOS에서 UEFI로 변경할 수 있나요?

예. 자세한 내용은 [현재 위치 업그레이드 중에 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)을 참조하세요.

### <a name="can-i-use-desktop-analytics-with-windows-10-ltsc"></a>Windows 10 LTSC에서 Desktop Analytics를 사용할 수 있나요?

Desktop Analytics를 사용하여 Windows 10 LTSC(장기 서비스 채널)에서 Windows 10 반기 채널로 디바이스를 업데이트하는 데 도움을 제공할 수 있지만, Desktop Analytics에서는 Windows 10 LTSC로의 업데이트를 지원하지 않습니다. 이 Windows 10 채널은 광범위하게 사용하기 위한 것이 아니며 기능 업데이트를 수신하지 않으므로 Desktop Analytics에서 지원되는 대상이 아닙니다. 자세한 내용은 [Windows as a Service 개요](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)를 참조하세요.

### <a name="can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal"></a>내 Desktop Analytics 포털에서 데이터를 새로 고치는 데 걸리는 시간을 줄일 수 있나요?

Desktop Analytics 포털에는 관리자 데이터 및 진단 데이터라는 두 가지 유형의 데이터가 있습니다. 요청 시 관리자 데이터를 새로 고치기 위해서는 데이터 통화 플라이아웃을 열고 **변경 내용 적용**을 선택합니다. 이 작업을 수행하면 작업 영역에서 보류 중인 관리자 변경 내용에 대한 일회성 새로 고침이 즉시 트리거됩니다. 변경 내용이 전파되며 일반적으로 15-60분 이내에 사용할 수 있습니다. 타이밍은 작업 영역의 크기 및 보류 중인 변경 내용의 범위에 따라 달라집니다. 24시간 내에 최대 6회까지 요청 시 데이터 새로 고침을 요청할 수 있습니다.

요청 시 데이터 새로 고침을 요청하지 않더라도 모든 데이터는 매일 한 번 자동으로 업데이트됩니다. 진단 데이터의 요청 시 새로 고침을 트리거할 수 있는 방법은 없습니다. Desktop Analytics의 다양한 데이터 형식에 대한 자세한 내용은 [데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조하세요.

## <a name="privacy"></a>개인 정보 보호

### <a name="can-desktop-analytics-be-used-without-a-direct-client-connection-to-the-microsoft-data-management-service"></a>Microsoft Data Management Service에 대한 직접 클라이언트 연결 없이 Desktop Analytics를 사용할 수 있나요?

아니요, 전체 서비스는 Windows 진단 데이터를 기반으로 하므로 디바이스에 직접 연결해야 합니다.

### <a name="can-i-choose-the-data-center-location"></a>데이터 센터 위치를 선택할 수 있나요?

Azure Log Analytics의 경우: 예, Desktop Analytics를 설정하고 Log Analytics 작업 영역을 만들 때 가능합니다.

Microsoft Data Management Service 및 Analytics Azure Storage의 경우: 아니요, 이러한 두 서비스는 미국에서 호스팅됩니다.

### <a name="where-is-my-organizations-data-stored"></a>내 조직의 데이터는 어디에 저장되나요?

컴퓨터의 Windows 진단 데이터는 미국에 있는 Microsoft에서 관리하는 보안 데이터 센터에서 암호화되어, 전송되고 처리됩니다. Microsoft는 Azure Portal의 Desktop Analytics 솔루션을 통해 Desktop Analytics 관련 데이터의 분석을 제공합니다. Desktop Analytics는 [Log Analytics를 사용할 수 있는](https://azure.microsoft.com/global-infrastructure/services/?products=monitor&regions=all) 대부분의 지역에서 지원됩니다. 국제 Azure 지역을 선택하는 경우에도 진단 데이터는 미국에 있는 Microsoft의 보안 데이터 센터로 전송되어 처리됩니다.

## <a name="existing-windows-analytics-customers"></a>기존 Windows Analytics 고객

### <a name="can-i-migrate-inputs-from-windows-analytics"></a>Windows Analytics에서 입력을 마이그레이션할 수 있나요?

예, [초기 온보딩](/sccm/desktop-analytics/set-up#initial-onboarding) 동안 기존 Windows Analytics 작업 영역을 Desktop Analytics 작업 영역으로 설정하는 경우에 가능합니다. 새 작업 영역을 만들거나 Windows Analytics 작업 영역이 아닌 작업 영역을 선택하는 경우 Desktop Analytics에서 입력을 마이그레이션하지 않습니다.

#### <a name="migration-scope"></a>마이그레이션 범위

| 입력 유형 | 마이그레이션할 예정인가요? |
|------------|---------------|
| 중요도 | 예 |
| 앱 소유자 | 예 |
| 업그레이드 결정 | 아니요 |
| 테스트 계획 | 아니요 |
| 테스트 결과 | 아니요 |

#### <a name="importance-mapping"></a>중요도 매핑

| Windows Analytics | Desktop Analytics |
|-------------------| ------------------|
| 낮은 설치 수 | (해당 없음) <br> 참고: Desktop Analytics는 자신의 추론을 실행하여 설치 수를 낮게 결정합니다. |
| 검토되지 않음 | 검토되지 않음 |
| 검토 진행 중 | 검토되지 않음 |
| 미션 크리티컬 | 중요 |
| 비즈니스 크리티컬 | 중요 |
| 중요 | 중요 |
| 최상의 노력 | 중요 |
| 무시 | 중요하지 않음 |

### <a name="can-i-migrate-from-multiple-windows-analytics-workspaces"></a>여러 Windows Analytics 작업 영역에서 마이그레이션할 수 있나요?

아니요, 입력을 마이그레이션할 Windows Analytics 작업 영역은 하나만 선택할 수 있습니다. 여러 Windows Analytics 작업 영역을 소유한 경우 조직에 가장 적합한 작업 영역을 선택합니다.

### <a name="ive-chosen-to-migrate-where-can-i-find-the-inputs-on-desktop-analytics"></a>마이그레이션을 선택했습니다. Desktop Analytics에서 입력을 찾을 수 있나요?

디바이스를 등록하고 난 후 Desktop Analytics 포털에서 마이그레이션된 입력을 보려면 **관리 > 자산 > 앱**으로 이동합니다.

### <a name="when-can-i-see-my-migrated-inputs"></a>마이그레이션된 입력은 언제 볼 수 있나요?

마이그레이션 프로세스는 트랜잭션입니다. 손상 없이 마이그레이션된 모든 입력이 표시되거나, 마이그레이션된 입력이 전혀 표시되지 않을 수 있습니다. 24시간 동안 마이그레이션된 입력이 표시되지 않으면 Microsoft 지원에 문의하세요. 마이그레이션된 입력이 표시되면 앱 태그 지정을 시작합니다. 일부 앱에 이미 태그를 지정한 경우, Desktop Analytics는 Windows Analytics의 입력과 충돌하는 경우 이러한 입력을 유지합니다.

### <a name="how-long-do-i-have-to-migrate-my-data"></a>데이터를 마이그레이션해야 하는 기간은?

Windows Analytics 업그레이드 준비 솔루션은 [2020년 1월 31일에 사용 중지됩니다](https://aka.ms/waretirement). 사용이 중지된 후 Log Analytics 작업 영역 보존 정책에 따라 시간이 지남에 따라 데이터가 사라집니다. 데이터를 보관해야 하는 고객은 미리 마이그레이션하거나 내보내야 합니다.

### <a name="can-i-migrate-after-the-initial-onboarding"></a>초기 온보딩 후에 마이그레이션할 수 있나요?

예.<!-- 5202803 --> [초기 온보딩](/sccm/desktop-analytics/set-up#initial-onboarding) 동안 기존 Windows Analytics 작업 영역을 Desktop Analytics 작업 영역으로 설정하는 한, 기존 Windows Analytics 고객은 초기 온보딩 후에 데이터를 마이그레이션할 수 있습니다. Desktop Analytics 포털에서 **연결된 서비스**로 이동하여 Windows Analytics에서 데이터를 마이그레이션하는 옵션을 선택합니다.

### <a name="can-i-use-update-compliance-together-with-desktop-analytics"></a>Desktop Analytics와 함께 업데이트 준수를 사용할 수 있나요?

예. 현재 Azure Portal에서 [업데이트 준수](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started)를 사용하는 경우 2020년 1월 이후에도 계속해서 이 작업을 수행할 수 있습니다.

자세한 내용은 [KB 4521815: 2020년 1월 31일 Windows Analytics 사용 중지](https://support.microsoft.com/help/4521815/windows-analytics-retirement)를 참조하세요.

### <a name="are-there-any-windows-analytics-features-that-arent-available-in-desktop-analytics"></a>Desktop Analytics에서 사용할 수 없는 Windows Analytics 기능이 있나요?

<!-- 3616924 -->
예, 다음은 Desktop Analytics에서 아직 사용할 수 없거나 사용 중지될 예정인 Windows Analytics 기능입니다.

#### <a name="general"></a>일반

- Configuration Manager가 필요하지 않은 시나리오에 대한 지원. 예를 들어 [Intune 지원](#bkmk_intune)이 있습니다.
- 모든 유효한 Windows 라이선스 및 E3, E5의 라이선스 전제 조건
- Azure AD 테넌트당 여러 작업 영역에 대한 지원
- 사용자 지정 쿼리를 실행하고 원시 솔루션 데이터를 내보낼 수 있는 기능
- 사용자 지정 보고서에 대한 데이터 모델 설명서

#### <a name="upgrade-readiness"></a>업그레이드 준비

- Internet Explorer 사이트 검색 데이터
- Office 추가 기능 인사이트(현재 [Configuration Manager에서 사용할 수 있음](#bkmk_office))
- 피드백 허브 인사이트

#### <a name="update-compliance"></a>업데이트 준수

- 비즈니스용 Windows 업데이트에 대한 지원
- 배달 최적화 인사이트
- Windows 10 LTSC(장기 서비스 채널)에 대한 지원
- Windows 참가자 보고서
- Windows Defender 상태

> [!Note]
> Desktop Analytics에서 사용할 수 없는 기능을 비롯한 기존의 모든 업데이트 준수 기능은 Azure Portal의 [업데이트 준수](/windows/deployment/update/update-compliance-get-started) 솔루션에서 계속 사용할 수 있습니다.

#### <a name="device-health"></a>디바이스 상태

- 드라이버 상태
- 앱 상태(배포 계획 외)
- 자주 크래시되는 디바이스 또는 드라이버에 의해 발생한 크래시
- Windows 로그인 상태
- Windows Information Protection
- Windows Server에 대한 지원

## <a name="other"></a>기타

### <a name="bkmk_office"></a> Office 365 ProPlus 업그레이드에 Desktop Analytics를 사용할 수 있나요?

아니요, Desktop Analytics는 Windows에 중점을 둡니다. Microsoft는 여러 고객과의 긴밀한 협업을 바탕으로 Desktop Analytics를 개발했습니다. 고객 의견은 Desktop Analytics가 Windows 배포를 안전하게 관리하는 기능을 향상시키기 위함입니다. 또한 고객은 Configuration Manager 및 Intune의 Office 관리 도구와 더욱 긴밀하게 통합된 [Office 365 ProPlus 준비](/sccm/sum/deploy-use/office-365-dashboard#bkmk_o365_readiness)를 원합니다. Microsoft는 Desktop Analytics의 Windows 시나리오에 중점을 두는 동시에 이러한 영역에 대한 투자를 계속하고 있습니다.

### <a name="how-can-i-provide-feedback-about-desktop-analytics"></a>Desktop Analytics에 대한 피드백은 어떻게 제공할 수 있나요?

Desktop Analytics에 대한 피드백을 공유하려면 포털 맨 위에 있는 **웃는 얼굴 보내기** 아이콘을 선택합니다. Microsoft가 피드백을 더 잘 이해할 수 있도록 제출 시 스크린샷을 함께 보내주세요. [UserVoice](https://configurationmanager.uservoice.com/forums/300492-ideas?category_id=366805)에서 제품 제안 사항을 제출하고 기타 아이디어에 투표할 수도 있습니다.

> [!Note]
> 웃는 얼굴 보내기 또는 UserVoice를 통해 개인 정보를 공유하지 마세요. 이러한 개인 정보에는 테넌트 ID 또는 상업적 ID가 포함됩니다. Microsoft는 웃는 얼굴 보내기 또는 UserVoice 채널을 통해 지원을 제공하지 않습니다. Desktop Analytics 작업 영역에 대한 도움말을 보려면 탐색 메뉴에서 **도움말 및 지원** 링크를 선택하여 지원 티켓을 엽니다.
