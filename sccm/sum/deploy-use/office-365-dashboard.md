---
title: Office 365 클라이언트 관리 대시보드
titleSuffix: Configuration Manager
description: Office 365 클라이언트 관리 대시보드에서 Office 365 클라이언트 정보 검토
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 11/06/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 69f234a2-b04b-445a-b81f-6b4acfc00eaf
ms.collection: M365-identity-device-management
ms.openlocfilehash: bf13e3389ec610ffacb06f56278113eb84a6089b
ms.sourcegitcommit: edc7a5ad6a2eb72d0448d4689b9534f7e6f4d2b7
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623100"
---
# <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드

Configuration Manager 버전 1802부터 Office 365 클라이언트 관리 대시보드에서 Office 365 클라이언트 정보를 검토할 수 있습니다. 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에 관련 디바이스의 목록이 표시됩니다. <!--1357281 -->

## <a name="prerequisites"></a>필수 구성 요소

### <a name="enable-hardware-inventory"></a>하드웨어 인벤토리를 사용하도록 설정

Office 365 클라이언트 관리 대시보드에 표시되는 데이터는 하드웨어 인벤토리에서 옵니다. 하드웨어 인벤토리를 사용하도록 설정하고 대시보드에서 데이터가 표시되도록 **Office 365 ProPlus 구성** 하드웨어 인벤토리 클래스를 선택합니다.
 
1. 하드웨어 인벤토리를 사용하도록 아직 설정하지 않은 경우 설정합니다. 자세한 내용은 [하드웨어 인벤토리 구성](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.
2. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**으로 이동합니다.  
3. **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  
4. 에 **기본 클라이언트 설정** 대화 상자를 클릭 하 여 **하드웨어 인벤토리**.  
5. 에 **디바이스 설정을** 목록에서 클릭 **클래스 설정**.  
6. **하드웨어 인벤토리 클래스** 대화 상자에서 **Office 365 ProPlus 구성**을 선택합니다.  
7. 클릭 하 여 **확인** 변경 내용을 저장 하 고 닫습니다는 **하드웨어 인벤토리 클래스** 대화 상자.

하드웨어 인벤토리가 보고되면 Office 365 클라이언트 관리 대시보드에서 데이터를 표시하기 시작합니다.

### <a name="internet-connectivity-for-clients"></a>클라이언트에 대 한 인터넷 연결

*(필수 구성 요소로 버전 1906에 도입 됨)*

버전 1906부터 office가 설치 된 장치는 [office 365 ProPlus 업그레이드 준비 대시보드의](#bkmk_readiness-dash)추가 기능 정보를 채우기 위해 인터넷 연결이 필요 합니다. 장치는 [Office Content Delivery Network](https://docs.microsoft.com/office365/enterprise/content-delivery-networks#the-office-365-cdn)에서 추가 기능 준비 파일을 다운로드 합니다. 이 파일에는 Microsoft에 알려진 추가 기능의 전체 목록과 Office 365 ProPlus의 예상 성능에 대 한 세부 정보가 포함 되어 있습니다. 각 장치는 파일의 정보를 사용 하 여 추가 기능 호환성을 확인 합니다. 장치에서 파일을 다운로드할 수 없는 경우 추가 기능 준비 상태 ( **요구 검토**)가 포함 됩니다.

## <a name="viewing-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드 보기

Configuration Manager 콘솔에서 Office 365 클라이언트 관리 대시보드를 보려면 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다. 대시보드 맨 위에 있는 **컬렉션** 드롭다운 설정을 사용하여 특정 컬렉션 멤버별로 대시보드 데이터를 필터링합니다. Configuration Manager 버전 1802부터 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에서는 관련 디바이스의 목록을 표시합니다.

Office 365 클라이언트 관리 대시보드는 다음 정보에 대한 차트를 제공합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널에 대한 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.


## <a name="bkmk_o365_readiness"></a> Office 365 ProPlus 준비를 위한 통합
<!--3735402-->
Configuration Manager 버전 1902부터는 대시보드를 사용하여 Office 365 ProPlus로 업그레이드할 준비가 된 디바이스를 식별할 수 있습니다. 통합을 통해 Office 추가 기능 및 사용자 환경에 매크로의 잠재적인 호환성 문제에 대한 인사이트를 제공합니다. 그런 다음, Configuration Manager를 사용하여 준비된 디바이스에 Office를 배포합니다.

Office 365 클라이언트 관리 대시보드에는 새 타일인 **Office 365 ProPlus 업그레이드 준비**가 포함됩니다. 이 타일은 다음 상태의 디바이스 막대형 차트입니다.
- 평가되지 않음
- 업그레이드 준비
- 검토 필요

디바이스 목록에 드릴스루할 상태를 선택합니다. 이 준비 보고서는 디바이스에 대한 자세한 정보를 표시합니다. 여기에는 Office 추가 기능 및 매크로의 호환성 상태에 대한 열이 포함되어 있습니다.

### <a name="prerequisites-for-office-365-proplus-readiness-integration"></a>Office 365 ProPlus 준비 상태 통합을 위한 필수 구성 요소

- 클라이언트 설정에서 하드웨어 인벤토리를 사용하도록 설정합니다. 자세한 내용은 [전제 조건](#prerequisites)을 참조하세요.  

- 이 디바이스는 Office CDN(콘텐츠 전송 네트워크)에 연결하여 추가 기능 준비 파일을 다운로드해야 합니다. 자세한 내용은 [콘텐츠 전송 네트워크](https://docs.microsoft.com/office365/enterprise/content-delivery-networks)를 참조하세요. 디바이스가 이 파일을 다운로드할 수 없는 경우 추가 기능 상태는 *검토 필요* 상태입니다.  

    > [!Note]  
    > 이 기능에 대한 데이터는 Microsoft로 전송되지 않습니다.  

### <a name="bkmk_ort"></a> 자세한 매크로 준비

기본적으로 검색 에이전트는 각 디바이스에서 MRU(가장 최근에 사용됨) 파일 목록을 확인합니다. 매크로를 지원하는 이 목록에 있는 파일을 계산합니다. 이러한 파일에는 다음과 같은 형식이 포함됩니다.
- Excel 매크로 사용 통합 문서(.xlsm) 또는 Word 매크로 사용 문서(.docm)와 같은 매크로 사용 Office 파일 형식  
- 매크로 콘텐츠가 있는지 여부를 나타내지 않는 이전 Office 형식입니다. 예: Excel 97-2003 통합 문서(.xls).

매크로 호환성에 대 한 자세한 정보가 필요한 경우 **Office 용 준비 도구 키트** 를 배포 하 여 매크로 파일 내에서 코드를 분석 합니다. 잠재적인 호환성 문제가 있는지 여부를 확인합니다. 예를 들어 파일은 최신 버전의 Office에서 변경된 함수를 사용합니다. Office용 Readiness Toolkit을 실행한 후 Configuration Manager는 해당 결과를 사용할 수 있습니다. 이 추가 데이터는 디바이스 준비 계산을 향상시킵니다. 자세한 내용은 [Office용 Readiness Toolkit을 사용하여 Office 365 ProPlus 애플리케이션 호환성 평가](https://aka.ms/readinesstoolkit)를 참조하세요.

## <a name="bkmk_readiness-dash"></a> Office 365 ProPlus 업그레이드 준비 대시보드

*(버전 1906에서 도입됨)*

<!--4021125-->
1906 버전부터는 Office 365 ProPlus로 업그레이드할 준비가 완료된 디바이스를 편리하게 확인할 수 있도록 하기 위해 준비 대시보드가 제공됩니다. 여기에는 Configuration Manager 현재 분기 버전 1902에 릴리스된 **Office 365 ProPlus 업그레이드 준비** 타일이 포함되어 있습니다. 이 대시보드의 다음 새 타일에서 Office 추가 기능 및 매크로 준비 상태를 평가할 수 있습니다.

- 배포
- 디바이스 준비 상태
- 추가 기능 준비 상태
- 추가 기능 지원 설명
- 버전별 상위 추가 기능
- 매크로가 있는 디바이스 수
- 매크로 준비 상태
- 매크로 권고 사항

### <a name="using-the-office-365-proplus-upgrade-readiness-dashboard"></a>Office 365 ProPlus 업그레이드 준비 대시보드 사용

[필수 구성 요소가](#prerequisites)있는지 확인 한 후 대시보드를 사용 하려면 다음 지침을 따르십시오.
 
1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **Office 365 클라이언트 관리**를 확장합니다.
1. **Office 365 ProPlus 업그레이드 준비** 노드를 선택 합니다.
1. **컬렉션** 및 **대상 Office 아키텍처** 를 변경 하 여 대시보드에서 릴레이 된 정보를 변경 합니다.

![Office 365 ProPlus 업그레이드 준비 대시보드](./media/4021125-office-365-upgrade-readiness-dashboard.png)

![Office 365 ProPlus 업그레이드 준비 대시보드](./media/4021125-office-365-to-add-ins.png)

![Office 365 ProPlus 업그레이드 준비 대시보드](./media/4021125-office-365-macro-advisories.png)

### <a name="device-readiness-information"></a>장치 준비 정보

각 장치에서 추가 기능과 매크로 인벤토리가 평가 되 면 해당 장치는 정보에 따라 그룹화 됩니다. **업그레이드 준비** 됨으로 표시 되는 상태의 장치에는 호환성 문제가 발생 하지 않을 수 있습니다.

그래프에서 **업그레이드 준비** 됨 범주를 선택 하면 제한 컬렉션의 장치에 대 한 자세한 정보가 표시 됩니다. 장치 목록을 검토 하 고, 비즈니스 요구 사항에 따라 선택 하 고, 선택 항목에서 새 장치 컬렉션을 만들 수 있습니다. 새 컬렉션을 사용 하 여 Configuration Manager으로 Office 365 ProPlus를 배포 합니다.

호환성 문제에 대 한 위험에 노출 될 수 있는 장치는 **요구 사항 검토**로 표시 됩니다. 이러한 장치를 Office 365 ProPlus로 업그레이드 하기 전에 조치를 취해야 할 수 있습니다. 예를 들어 중요 한 추가 기능을 최신 버전으로 업데이트할 수 있습니다.

### <a name="add-in-information"></a>추가 기능 정보

 각 장치에는 설치 된 모든 추가 기능에 대 한 인벤토리가 수집 됩니다. 그러면 인벤토리가 Office 365 ProPlus의 추가 기능 성능에 대해 Microsoft가 본 정보와 비교 됩니다. 업그레이드 후 문제를 일으킬 가능성이 있는 추가 기능이 발견 되 면 추가 기능을 사용 하는 모든 장치에는 검토용 플래그가 지정 됩니다.

### <a name="macro-information"></a>매크로 정보

Configuration Manager는 각 장치에서 가장 최근에 사용 된 파일을 찾습니다. 다음 유형을 포함 하 여이 목록에서 매크로를 지 원하는 파일 수를 계산 합니다.

- 매크로 사용 Office 파일 형식입니다.
- 매크로 콘텐츠가 있는지 여부를 나타내지 않는 이전 Office 형식

매크로 호환성에 대 한 자세한 정보가 필요한 경우 **Office 용 준비 도구 키트** 를 배포 하 여 매크로 파일 내에서 코드를 분석 합니다. **가장 최근에 사용 된 Office 문서 및이 컴퓨터에서 설치 된 추가 기능**에 대 한 옵션을 선택 하면 Configuration Manager의 하드웨어 인벤토리 에이전트에서 결과를 선택할 수 있습니다. 추가 데이터는 장치 준비 계산을 향상 시킬 수 있습니다. 자세한 내용은 [Office용 Readiness Toolkit을 사용하여 Office 365 ProPlus 애플리케이션 호환성 평가](https://aka.ms/readinesstoolkit)를 참조하세요.


## <a name="next-steps"></a>다음 단계

[Configuration Manager를 사용하여 Office 365 ProPlus 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates)
