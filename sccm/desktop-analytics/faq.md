---
title: 데스크톱 분석에 대 한 FAQ
titleSuffix: Configuration Manager
description: 질문과 대답 데스크톱 분석용입니다.
ms.date: 04/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: e0db3311-2303-4013-a906-76b408172d3c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.collection: M365-identity-device-management
ms.openlocfilehash: 4596923f9a6a42ad98dc17257b22925ad0bc5eed
ms.sourcegitcommit: 9af73f5c1b93f6ccaea3e6a096f75a5fecd65c2f
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/26/2019
ms.locfileid: "64562450"
---
# <a name="desktop-analytics-faq"></a>데스크톱 분석 FAQ

> [!Note]  
> 이 정보는 정식으로 발표 되기 전에 대폭 수정 될 수 있는 미리 보기 서비스에 연결 합니다. Microsoft는 여기에 제공된 정보와 관련하여 명시적이거나 묵시적인 어떤 보증도 하지 않습니다.  

## <a name="windows-upgrade"></a>Windows 업그레이드

### <a name="can-i-upgrade-windows-and-change-architecture"></a>Windows 업그레이드 및 아키텍처를 변경할 수 있나요?

데스크톱 분석은 최상의 지원 업그레이드 하도록 설계 되었습니다. 전체 업그레이드는 32 비트에서 64 비트 아키텍처에서의 마이그레이션을 지원 하지 않습니다. 이 시나리오에서는 컴퓨터를 마이그레이션하는 경우 새로 고침 시나리오를 사용 합니다. 데스크톱 분석 정보는이 시나리오에서는 여전히 중요 하지만 업그레이드 관련 지침을 무시할 수 있습니다.

자세한 내용은 [새 버전의 Windows로 기존 컴퓨터 새로 고침](/sccm/osd/deploy-use/refresh-an-existing-computer-with-a-new-version-of-windows)을 참조하세요.

### <a name="can-i-change-from-bios-to-uefi-when-upgrading-windows"></a>변경 BIOS에서 UEFI로 Windows를 업그레이드 하는 경우

예. 자세한 내용은 [전체 업그레이드를 사용 하는 동안 BIOS에서 UEFI로 변환](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)합니다.

### <a name="can-i-use-desktop-analytics-with-windows-10-ltsc"></a>Windows 10 LTSC를 사용 하 여 데스크톱 분석을 사용할 수 있나요?

데스크톱 Analytics를 사용 하 여 장치에서 Windows 10 장기 서비스 채널 LTSC () Windows 10 반기 채널에 업데이트를 도우려면 데스크톱 Analytics Windows 10 LTSC에 대 한 업데이트를 지원 하지 않습니다. 이 채널의 Windows 10 광범위 한 용도로 적합 하지 않습니다 및 데스크톱 Analytics를 사용 하 여 지원 되는 대상 되지 않도록 기능 업데이트를 수신 하지 않습니다. 자세한 내용은 [Windows 서비스에 대 한 개요로](https://docs.microsoft.com/windows/deployment/update/waas-overview#long-term-servicing-channel)합니다.

## <a name="privacy"></a>개인 정보 보호

### <a name="can-desktop-analytics-be-used-without-a-direct-client-connection-to-the-microsoft-data-management-service"></a>Microsoft 데이터 관리 서비스에 직접 클라이언트 연결 없이 데스크톱 Analytics는 사용할 수 있습니까?

아니요, 전체 서비스는 장치 되어이 직접 연결 해야 하는 진단 데이터를 Windows에서 구현 됩니다.

### <a name="can-i-choose-the-data-center-location"></a>데이터 센터 위치를 선택할 수 있나요?

Azure Log analytics: 예, 데스크톱 Analytics를 설정 하 고 Log Analytics 작업 영역을 만들 때.

Microsoft 데이터 관리 서비스 및 분석에 대 한 Azure Storage: 아니요, 이러한 두 서비스는 미국에서 호스트 됩니다.

### <a name="where-is-my-organizations-data-stored"></a>조직의 데이터 저장 위치

Windows 컴퓨터에서 진단 데이터는 암호화, 전송 및 미국에 있는 Microsoft에서 관리 하는 보안 데이터 센터에서 처리 합니다. 데스크톱 Analytics와 관련 된 데이터의 분석 후에 Azure portal에서 데스크톱 분석 솔루션을 통해 제공 됩니다. 데스크톱 분석은 모든 Azure 지역에서 지원 됩니다. 국가별 Azure 지역 선택 것을 막기 위해 진단 데이터에서 전송 및 미국에서 Microsoft의 보안 데이터 센터에서 처리 합니다.
