---
title: 데스크톱 분석 FAQ
titleSuffix: Configuration Manager
description: 데스크톱 분석에 대 한 질문과 대답입니다.
ms.date: 09/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e0db3311-2303-4013-a906-76b408172d3c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e47827c6ad2b52ebb2b9dfabcdc4c61320385bf3
ms.sourcegitcommit: cb169396acf0d50fedd9f2ae62f7894615c3cce5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808387"
---
# <a name="desktop-analytics-faq"></a>데스크톱 분석 FAQ

> [!Note]  
> 이 정보는 미리 보기 서비스와 관련이 있으며,이 서비스는 상업적으로 출시 되기 전에 대폭 수정 될 수 있습니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

## <a name="prerequisites"></a>필수 구성 요소

### <a name="can-i-use-desktop-analytics-with-intune-managed-devices"></a>Intune 관리 장치에서 데스크톱 분석을 사용할 수 있나요? 

데스크톱 분석 워크플로에서 이점을 누릴 수 있는 대다수의 고객은 Configuration Manager를 사용 하 여 Windows를 배포할 수 있습니다. Intune 고객은 분석 데이터의 추가 정보를 선호 하며,이를 통해 정보를 공유 하는 방법에 대해 노력 하 고 있습니다.

### <a name="its-been-over-72-hours-and-the-portal-is-still-processing-data-what-next"></a>72 시간을 초과 하 여 포털에서 여전히 데이터를 처리 하 고 있으며, 그 다음에는 어떻게 되나요? 

데스크톱 분석을 처음 설정 하는 경우 Configuration Manager 및 데스크톱 분석 포털의 보고서에 전체 데이터가 즉시 표시 되지 않을 수 있습니다. 서비스가 데이터를 처리 하는 데 2-3 일이 소요 될 수 있습니다. 72 시간을 초과 하는 경우 포털에서 계속 데이터를 처리 하는 경우 다음 단계를 수행 합니다.

- 활성 장치가 올바르게 구성 되었는지 확인 하려면 [연결 상태 대시보드](/sccm/desktop-analytics/monitor-connection-health)를 사용 합니다. 이 대시보드는 실시간으로 업데이트 되지 않습니다.
- 장치에서 진단 데이터를 데스크톱 분석 서비스로 전송 하는지 확인 합니다. 자세한 내용은 [데이터 공유 사용](/sccm/desktop-analytics/enable-data-sharing)을 참조 하세요.
- Azure AD에서 [AZURE ad 응용 프로그램](/sccm/desktop-analytics/troubleshooting#bkmk_AzureADApps) 을 프로 비전 합니다.
- 지난 7 일간 조직에 연결 된 장치를 확인 합니다. [데스크톱 분석 포털](https://aka.ms/desktopanalytics)에서 **연결 된 서비스** 창으로 이동 합니다. **장치 등록**을 선택 하 고 **최근 데이터 보기**

장치가 제대로 구성 되어 있고 작업 영역에 아직 데이터가 표시 되지 않는 경우 [Microsoft 지원에 문의 하세요](https://support.microsoft.com/hub/4343728/support-for-business).

## <a name="windows-upgrade"></a>Windows 업그레이드

### <a name="can-i-upgrade-windows-and-change-architecture"></a>Windows를 업그레이드 하 고 아키텍처를 변경할 수 있나요?

데스크톱 분석은 전체 업그레이드를 가장 잘 지원 하도록 설계 되었습니다. 현재 위치의 업그레이드는 32 비트에서 64 비트 아키텍처로의 마이그레이션을 지원 하지 않습니다. 이 시나리오에서 컴퓨터를 마이그레이션해야 하는 경우 새로 고침 시나리오를 사용 합니다. 데스크톱 분석 정보는이 시나리오에서 여전히 중요 하지만 업그레이드 관련 지침은 무시할 수 있습니다.

자세한 내용은 [새 버전의 Windows로 기존 컴퓨터 새로 고침](/sccm/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)을 참조하세요.

### <a name="can-i-change-from-bios-to-uefi-when-upgrading-windows"></a>Windows를 업그레이드할 때 BIOS에서 UEFI로 변경할 수 있나요?

예. 자세한 내용은 [전체 업그레이드 중에 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)을 참조 하세요.

### <a name="can-i-use-desktop-analytics-with-windows-10-ltsc"></a>Windows 10 LTSC에서 데스크톱 분석을 사용할 수 있나요?

데스크톱 분석을 사용 하 여 Windows 10 LTSC (장기 서비스 채널)에서 Windows 10 반기 채널로 장치를 업데이트 하는 데 도움을 제공할 수 있지만, 데스크톱 분석에서는 Windows 10 LTSC 업데이트를 지원 하지 않습니다. 이 Windows 10 채널은 광범위 하 게 사용 하기 위한 것이 아니며 기능 업데이트를 수신 하지 않으므로 데스크톱 분석에서 지원 되는 대상이 아닙니다. 자세한 내용은 [Windows as a service 개요](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)를 참조 하세요.

### <a name="can-i-reduce-the-amount-of-time-it-takes-for-data-to-refresh-in-my-desktop-analytics-portal"></a>내 데스크톱 분석 포털에서 데이터를 새로 고치는 데 걸리는 시간을 줄일 수 있나요?

데스크톱 분석 포털에는 다음과 같은 두 가지 유형의 데이터가 있습니다. 관리자 데이터 및 진단 데이터입니다. 요청 시 관리자 데이터를 새로 고치려면 데이터 통화 플라이 아웃을 열고 **변경 내용 적용**을 선택 합니다. 이 작업을 수행 하면 작업 영역에서 보류 중인 관리자 변경 내용에 대 한 일회성 새로 고침이 즉시 트리거됩니다. 변경 내용은 전파 되며 일반적으로 15-60 분 이내에 사용할 수 있습니다. 타이밍은 작업 영역의 크기 및 보류 중인 변경 내용의 범위에 따라 달라 집니다. 24 시간 내에 최대 6 회까지 요청 시 데이터 새로 고침을 요청할 수 있습니다.

요청 시 데이터 새로 고침을 요청 하지 않더라도 매일 한 번 자동으로 모든 데이터가 업데이트 됩니다. 진단 데이터의 요청 시 새로 고침을 트리거할 수 있는 방법은 없습니다. 데스크톱 분석의 다양 한 데이터 형식에 대 한 자세한 내용은 [데이터 대기 시간](/sccm/desktop-analytics/troubleshooting#data-latency)을 참조 하세요.

## <a name="privacy"></a>개인 정보 취급 방침

### <a name="can-desktop-analytics-be-used-without-a-direct-client-connection-to-the-microsoft-data-management-service"></a>Microsoft 데이터 관리 서비스에 대 한 직접 클라이언트 연결 없이 데스크톱 분석을 사용할 수 있나요?

아니요, 전체 서비스는 Windows 진단 데이터를 기반으로 하며,이로 인해 장치에 직접 연결 해야 합니다.

### <a name="can-i-choose-the-data-center-location"></a>데이터 센터 위치를 선택할 수 있나요?

Azure Log Analytics: 예, 데스크톱 분석을 설정 하 고 Log Analytics 작업 영역을 만들 때

Microsoft 데이터 관리 서비스 및 분석 Azure Storage: 아니요. 이러한 두 서비스는 미국에서 호스팅됩니다.

### <a name="where-is-my-organizations-data-stored"></a>내 조직의 데이터는 어디에 저장 되나요?

컴퓨터의 Windows 진단 데이터는 미국에 있는 Microsoft에서 관리 하는 보안 데이터 센터에서 암호화, 전송 및 처리 됩니다. 그런 다음 데스크톱 분석 관련 데이터에 대 한 분석은 Azure Portal의 데스크톱 분석 솔루션을 통해 제공 됩니다. 데스크톱 분석은 모든 Azure 지역에서 지원 됩니다. 국제 Azure 지역을 선택 하면 Microsoft의 보안 데이터 센터에서 진단 데이터를 전송 및 처리 하는 것을 막을 수 없습니다.

## <a name="existing-windows-analytics-customers"></a>기존 Windows 분석 고객

### <a name="can-i-migrate-inputs-from-windows-analytics"></a>Windows Analytics에서 입력을 마이그레이션할 수 있나요?

예, [초기 온 보 딩](/sccm/desktop-analytics/set-up#initial-onboarding)중에 기존 Windows Analytics 작업 영역을 데스크톱 분석 작업 영역으로 설정 합니다. 새 작업 영역을 만들거나 Windows Analytics 작업 영역이 아닌 작업 영역을 선택 하는 경우 데스크톱 분석에서 입력을 마이그레이션하지 않습니다.

#### <a name="migration-scope"></a>마이그레이션 범위

| 입력 유형 | 마이그레이션할 예정 인가요? |
|------------|---------------|
| 중요도 | 예 |
| 앱 소유자 | 예 |
| 업그레이드 결정 | 아니요 |
| 테스트 계획 | 아니요 |
| 테스트 결과 | 아니요 |

#### <a name="importance-mapping"></a>중요도 매핑

| Windows Analytics | Desktop Analytics |
|-------------------| ------------------|
| 낮은 설치 수 | (해당 사항 없음) <br> 참고: 데스크톱 분석은 자신의 추론을 실행 하 여 설치 수를 낮게 결정 합니다. |
| 검토 되지 않음 | 검토 되지 않음 |
| 검토 진행 중 | 검토 되지 않음 |
| 중요 업무용 | 심각 |
| 업무상 중요 | 심각 |
| 중요 | 중요 |
| 최상의 노력 | 중요 |
| 무시 | 중요 하지 않음 |

### <a name="can-i-migrate-from-multiple-windows-analytics-workspaces"></a>여러 Windows Analytics 작업 영역에서 마이그레이션할 수 있나요?

아니요, 입력을 마이그레이션할 Windows Analytics 작업 영역을 하나만 선택할 수 있습니다. 여러 Windows Analytics 작업 영역을 소유 하는 경우 조직에 가장 적합 한 작업 영역을 선택 합니다.

### <a name="ive-chosen-to-migrate-where-can-i-find-the-inputs-on-desktop-analytics"></a>마이그레이션을 선택 했습니다. 데스크톱 분석에서 입력을 찾을 수 있나요?

장치가 등록 되 면 데스크톱 분석 포털에서 마이그레이션된 입력을 보려면 **관리 > 자산 > 앱**으로 이동 합니다.

### <a name="when-can-i-see-my-migrated-inputs"></a>마이그레이션된 입력을 언제 볼 수 있나요?

마이그레이션 프로세스가 트랜잭션입니다. 모든 입력이 손상 없이 마이그레이션 되었거나 마이그레이션되지 않은 입력이 모두 표시 됩니다. 24 시간 동안 마이그레이션된 입력이 표시 되지 않으면 Microsoft 지원에 문의 하세요. 마이그레이션된 입력이 표시 되 면 앱 태깅을 시작 합니다. 일부 앱에 이미 태그가 지정 된 경우, 데스크톱 분석은 Windows Analytics의 입력과 충돌 하는 경우 이러한 입력을 유지 합니다.

### <a name="im-not-ready-yet-can-i-migrate-after-the-initial-onboarding"></a>아직 준비 되지 않았습니다. 초기 온 보 딩 후에 마이그레이션할 수 있나요?

아니요, 지금은 [초기](/sccm/desktop-analytics/set-up#initial-onboarding)등록 중에 마이그레이션을 결정 해야 합니다.

### <a name="can-i-use-update-compliance-together-with-desktop-analytics"></a>데스크톱 분석과 함께 업데이트 준수를 사용할 수 있나요?

예. 현재 Azure Portal에서 [업데이트 준수](https://docs.microsoft.com/windows/deployment/update/update-compliance-get-started) 를 사용 하는 경우 2020 년 1 월 이후에도 계속 해 서이 작업을 수행할 수 있습니다.

자세한 내용은 블로그 게시물을 참조 하세요. [사용자 입력 데이터 마이그레이션 "Windows Analytics: "데스크톱 분석](https://techcommunity.microsoft.com/t5/Desktop-Analytics-Blog/Migrate-user-input-data-from-Windows-Analytics-Upgrade-Readiness/ba-p/841744)으로 업그레이드 준비 합니다.

## <a name="other"></a>기타

### <a name="can-i-use-desktop-analytics-for-my-office-365-proplus-upgrades"></a>Office 365 ProPlus 업그레이드에 데스크톱 분석을 사용할 수 있나요?

아니요, 데스크톱 분석은 Windows에 집중 됩니다. Microsoft는 여러 고객과의 긴밀 한 공동 작업에서 데스크톱 분석을 개발 했습니다. 미리 보기 프로그램을 통해 고객 의견은 데스크톱 분석이 Windows 배포를 안전 하 게 관리 하는 기능을 개선 하는 방법에 대 한 것 이었습니다. 또한 [office 365 ProPlus 준비](/sccm/sum/deploy-use/office-365-dashboard#bkmk_o365_readiness) 를 Configuration Manager 및 Intune의 office 관리 도구와 더욱 긴밀 하 게 통합 하고자 했습니다. Microsoft는 데스크톱 분석의 Windows 시나리오에 중점을 두는 동시에 이러한 영역에 대 한 투자를 계속 합니다.

### <a name="how-can-i-provide-feedback-about-desktop-analytics"></a>데스크톱 분석에 대 한 피드백을 제공 하려면 어떻게 해야 하나요?

데스크톱 분석에 대 한 피드백을 공유 하려면 포털 위쪽에서 **웃는 얼굴 보내기** 아이콘을 선택 합니다. Microsoft에서 피드백을 더 잘 이해할 수 있도록 제출 된 스크린샷을 포함 합니다. 제품 제안 사항을 제출 하 고 [UserVoice](https://configurationmanager.uservoice.com/forums/300492-ideas?category_id=366805)에서 기타 아이디어를 제출할 수도 있습니다.

> [!Note]
> 웃는 얼굴 또는 UserVoice 보내기를 통해 개인 정보를 공유 하지 마세요. 이러한 개인 정보에는 테 넌 트 Id 또는 상업적 Id가 포함 됩니다. Microsoft는 웃는 얼굴 또는 UserVoice 채널 보내기를 통해 지원을 제공 하지 않습니다. 데스크톱 분석 작업 영역에 대 한 도움말을 보려면 탐색 메뉴에서 **도움말 및 지원** 링크를 선택 하 여 지원 티켓을 엽니다.
