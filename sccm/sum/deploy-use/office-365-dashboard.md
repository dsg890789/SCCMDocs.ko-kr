---
title: Office 365 클라이언트 관리 대시보드
titleSuffix: Configuration Manager
description: Office 365 클라이언트 관리 대시보드에서 Office 365 클라이언트 정보 검토
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 04/10/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 69f234a2-b04b-445a-b81f-6b4acfc00eaf
ms.collection: M365-identity-device-management
ms.openlocfilehash: aff55aee5b2eaa584a6161452b4a232fab07412a
ms.sourcegitcommit: 6f4c2987debfba5d02ee67f6b461c1a988a3e201
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59802175"
---
# <a name="office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드

Configuration Manager 버전 1802부터 Office 365 클라이언트 관리 대시보드에서 Office 365 클라이언트 정보를 검토할 수 있습니다. 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에 관련 디바이스의 목록이 표시됩니다. <!--1357281 -->

## <a name="prerequisites"></a>필수 구성 요소

Office 365 클라이언트 관리 대시보드에 표시되는 데이터는 하드웨어 인벤토리에서 옵니다. 하드웨어 인벤토리를 사용하도록 설정하고 대시보드에서 데이터가 표시되도록 **Office 365 ProPlus 구성** 하드웨어 인벤토리 클래스를 선택합니다.
 
1. 하드웨어 인벤토리를 사용하도록 아직 설정하지 않은 경우 설정합니다. 자세한 내용은 [하드웨어 인벤토리 구성](/sccm/core/clients/manage/inventory/configure-hardware-inventory)을 참조하세요.
2. Configuration Manager 콘솔에서 **관리** > **클라이언트 설정** > **기본 클라이언트 설정**으로 이동합니다.  
3. **홈** 탭의 **속성** 그룹에서 **속성**을 클릭합니다.  
4. 에 **기본 클라이언트 설정** 대화 상자를 클릭 하 여 **하드웨어 인벤토리**.  
5. 에 **디바이스 설정을** 목록에서 클릭 **클래스 설정**.  
6. **하드웨어 인벤토리 클래스** 대화 상자에서 **Office 365 ProPlus 구성**을 선택합니다.  
7. 클릭 하 여 **확인** 변경 내용을 저장 하 고 닫습니다는 **하드웨어 인벤토리 클래스** 대화 상자. 

하드웨어 인벤토리가 보고되면 Office 365 클라이언트 관리 대시보드에서 데이터를 표시하기 시작합니다.

## <a name="viewing-the-office-365-client-management-dashboard"></a>Office 365 클라이언트 관리 대시보드 보기

Configuration Manager 콘솔에서 Office 365 클라이언트 관리 대시보드를 보려면 **소프트웨어 라이브러리** > **개요** > **Office 365 클라이언트 관리**로 이동합니다. 대시보드 맨 위에 있는 **컬렉션** 드롭다운 설정을 사용하여 특정 컬렉션 멤버별로 대시보드 데이터를 필터링합니다. Configuration Manager 버전 1802부터 그래프 섹션을 선택하면 Office 365 클라이언트 관리 대시보드에서는 관련 디바이스의 목록을 표시합니다.

Office 365 클라이언트 관리 대시보드는 다음 정보에 대한 차트를 제공합니다.

- Office 365 클라이언트 수
- Office 365 클라이언트 버전
- Office 365 클라이언트 언어
- Office 365 클라이언트 채널에 대한 자세한 내용은 [Office 365 ProPlus의 업데이트 채널 개요](/DeployOffice/overview-of-update-channels-for-office-365-proplus)를 참조하세요.


## <a name="bkmk_o365_readiness"></a> Office 365 ProPlus 준비를 위한 통합
<!--3735402-->
Configuration Manager 버전 1902부터는 대시보드를 사용하여 Office 365 ProPlus로 업그레이드할 준비가 된 디바이스를 식별할 수 있습니다. Office 분석과의 통합을 통해 Office 추가 기능 및 사용자 환경에서 사용되는 매크로의 잠재적인 호환성 문제에 대한 인사이트를 제공합니다. 그런 다음, Configuration Manager를 사용하여 준비된 디바이스에 Office를 배포합니다.

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

보다 자세한 평가가 필요한 경우 **Office Readiness Toolkit**을 배포합니다. 이 도구는 매크로 파일 내의 코드를 분석합니다. 잠재적인 호환성 문제가 있는지 여부를 확인합니다. 예를 들어 파일은 최신 버전의 Office에서 변경된 함수를 사용합니다. Office Readiness Toolkit을 실행한 후 Configuration Manager는 해당 결과를 사용할 수 있습니다. 이 추가 데이터는 디바이스 준비 계산을 향상시킵니다. 자세한 내용은 [Readiness Toolkit을 사용하여 Office 365 ProPlus 애플리케이션 호환성 평가](http://aka.ms/readinesstoolkit)를 참조하세요.

## <a name="next-steps"></a>다음 단계

[Configuration Manager를 사용하여 Office 365 ProPlus 관리](/sccm/sum/deploy-use/manage-office-365-proplus-updates)