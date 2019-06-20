---
title: 업데이트 및 서비스
titleSuffix: Configuration Manager
description: 업데이트 및 서비스라는 콘솔 내 서비스 메서드에 대해 알아봅니다. 이 방법을 사용하면 권장 업데이트를 간편하게 찾아서 설치할 수 있습니다.
ms.date: 06/06/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 3a832943-580a-4a40-b454-961d0854ac2b
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bb875529224655fb56aeea5636bf92c7ddaf8b2c
ms.sourcegitcommit: 725e1bf7d3250c2b7b7be9da01135517428be7a1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/10/2019
ms.locfileid: "66822056"
---
# <a name="updates-and-servicing-for-configuration-manager"></a>Configuration Manager에 대한 업데이트 및 서비스

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager는 **업데이트 및 서비스**라는 콘솔 내 서비스 메서드를 사용합니다. 이 콘솔 내 메서드는 Configuration Manager 인프라에 대한 권장 업데이트를 손쉽게 찾아서 설치할 수 있도록 합니다. 콘솔 내 서비스는 핫픽스와 같은 대역 외 업데이트로 보완됩니다. 대역 외 업데이트는 고객 환경 특유의 문제를 해결해야 하는 고객을 위한 것입니다.  

> [!TIP]  
> *업그레이드*, *업데이트* 및 *설치* 용어들은 Configuration Manager의 세 가지 별도 개념을 설명하는 데 사용됩니다. 각 용어가 어떻게 사용되는지에 대한 자세한 내용은 [업그레이드, 업데이트 및 설치 정보](/sccm/core/understand/upgrade-update-install)를 참조하세요.  


##  <a name="bkmk_Baselines"></a> 기준 및 업데이트 버전  

새 계층 구조에 새로운 사이트를 설치할 때 최신 기준 버전을 사용합니다.

- 또한 System Center 2012 Configuration Manager를 업그레이드하려면 기준 버전을 사용합니다.  

- Configuration Manager 현재 분기로 업그레이드한 후 최신 상태를 유지하려면 기준선 버전을 사용하지 마십시오. 대신 [콘솔 내 업데이트](/sccm/core/servers/manage/install-in-console-updates)만 사용하여 최신 버전으로 업데이트합니다.  

- 정기적으로 추가 기준 버전이 릴리스됩니다. 최신 기준 버전을 사용하여 새 계층을 설치하면 최신 버전을 제공하는 추가 인프라 업그레이드에 따라 오래되거나 지원되지 않는 버전의 Configuration Manager를 설치하는 것을 피할 수 있습니다.  

기준 버전을 설치한 후 콘솔 내 업데이트로 Configuration Manager에 대한 추가 버전을 사용할 수 있습니다. 콘솔 내 업데이트는 최신 버전의 Configuration Manager로 인프라를 업데이트합니다.  

- 최상위 사이트의 버전을 업데이트하기 위해 콘솔 내 업데이트를 설치합니다.  

- 중앙 관리 사이트에 설치하는 업데이트는 자동으로 자식 기본 사이트에 설치됩니다. 기본 사이트에서 유지 관리 기간을 사용하여 이 시기를 제어합니다.  

- 보조 사이트를 콘솔 내에서 새로운 업데이트 버전으로 수동으로 업데이트합니다.  

업데이트를 설치하면, 해당 버전에 대한 설치 파일이 사이트 서버의 **CD.Latest** 폴더에 저장됩니다. 이러한 파일에 대한 자세한 내용은 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)를 참조하세요.  

- 사이트 복구 시 CD.Latest 폴더에서 파일을 사용 합니다. 또한 계층 구조가 더 이상 기준 버전을 실행하지 못할 경우 이러한 파일을 사용하여 추가 사이트를 설치합니다.  

- CD.Latest의 설치 파일을 사용하여 새 계층 구조의 첫 번째 사이트를 설치하거나 System Center 2012 Configuration Manager에서 사이트를 업그레이드할 수 없습니다.  

### <a name="version-details"></a>버전 세부 정보

Configuration Manager에 대한 일부 업데이트는 기존 인프라에 대한 콘솔 내 업데이트 버전과 새 기준 버전이 모두 제공됩니다.  

#### <a name="supported-versions"></a>지원되는 버전

Configuration Manager의 다음과 같은 지원되는 버전은 기준, 업데이트 또는 두 가지 버전이 모두 제공됩니다.  

| Version | 가용일 | [지원 종료 날짜](/sccm/core/servers/manage/current-branch-versions-supported) | 기준 | 콘솔 내 업데이트 |  
|-------------|-----------|------------|--------------|------------------------|  
| [1902](/sccm/core/plan-design/changes/whats-new-in-version-1902)<br /><br /> 5.00.8790.1000 | 2019년 3월 27일 | 2020년 9월 27일 | 예<sup>[참고 1](#bkmk_note1)</sup> | 예 |
| [1810](/sccm/core/plan-design/changes/whats-new-in-version-1810)<br /><br /> 5.00.8740.1000 | 2018년 11월 27일 | 2020년 5월 27일 | 아니요 | 예 |
| [1806](/sccm/core/plan-design/changes/whats-new-in-version-1806)<br /><br /> 5.00.8692.1000 | 2018년 7월 31일 | 2020년 1월 31일 | 아니요 | 예 |
| [1802](/sccm/core/plan-design/changes/whats-new-in-version-1802)<br /><br /> 5.00.8634.1000 | 2018년 3월 22일 | 2019년 9월 22일 | 예<sup>[참고 1](#bkmk_note1)</sup> | 예 |
| [1710](/sccm/core/plan-design/changes/whats-new-in-version-1710)<br /><br /> 5.00.8577.1000 | 2017년 11월 20일 | 2019 년 5 월 20 | 아니요 | 예 |

<a name="bkmk_note1"></a>

> [!Note]  
> <sup>**참고 1:**</sup> 기준 미디어는 VLSC([볼륨 라이선스 서비스 센터](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx))에서 다음 릴리스의 일부로 사용할 수 있습니다.
>
> - System Center Config Mgr(현재 분기)
> - System Center 2016 Datacenter
> - System Center 2016 Standard  
>
> 예를 들어 `System Center Config Mgr (current branch)`용 VLSC를 검색합니다. 파일 목록에서 기준 미디어를 찾아 해당 릴리스를 다운로드합니다.  

#### <a name="historical-versions"></a>이전 버전

다음 표에 지원되지 않는 Configuration Manager 현재 분기의 이전 버전이 나열되어 있습니다.

| Version | 가용일 | 지원 종료 날짜 | 기준 | 콘솔 내 업데이트 |  
|-------------|-----------|------------|--------------|------------------------|  
| 1706 <br /><br /> 5.00.8540.1000 | 2017년 7월 31일 | 2018년 7월 31일 | 아니요 | 예 |
| 1702 <br /><br /> 5.00.8498.1000 | 2017년 3월 27일 | 2018년 3월 27일 | 예 | 예 |
| 1610 <br /><br /> 5.00.8458.1000 | 2016년 11월 18일 | 2017년 11월 18일 | 아니요 | 예 |
| 1606 <br /><br /> 5.00.8412.1000 | 2016년 7월 22일 | 2017년 7월 22일 | 아니요 | 예 |
| 1606 및 1606 핫픽스 롤업(KB3186654) <br><br>5.00.8412.1307 | 2016년 10월 12일 | 2017년 10월 12일 | 예 | 아니요 |
| 1602<br /><br /> 5.00.8355.1000 | 2016년 3월 11일 | 2017년 3월 11일 | 아니요 | 예 |
| 1511 <br /><br /> 5.00.8325.1000 | 2015년 12월 8일 | 2016년 12월 8일 | 예 | 아니요 |  

#### <a name="how-to-check-the-version"></a>버전을 확인하는 방법

Configuration Manager 사이트 버전을 확인하려면 콘솔의 왼쪽 위에 있는 **System Center Configuration Manager 정보**로 이동합니다. 이 대화 상자에는 사이트 및 콘솔 버전이 표시됩니다.  

> [!Note]  
> 1802 버전부터는 콘솔 버전이 이제 사이트 버전과 약간 다릅니다. 이제 콘솔의 부 버전이 Configuration Manager 릴리스 버전에 해당합니다. 예를 들어, Configuration Manager 버전 1802에서 초기 사이트 버전은 5.0.8634.1000이고 초기 콘솔 버전은 5.**1802**.1082.1700입니다. 빌드(1082) 및 수정(1700) 번호는 향후 핫픽스에서 1802 릴리스로 변경될 수 있습니다.


## <a name="bkmk_inconsole"></a> 콘솔 내 업데이트 및 서비스  

System Center Configuration Manager 현재 분기의 프로덕션이 준비된 설치를 사용하는 경우 대부분의 업데이트는 **업데이트 및 서비스** 채널을 사용하여 제공됩니다. 이 메서드는 현재 인프라 버전 및 구성에 해당하는 업데이트를 식별하고 다운로드하고 사용할 수 있게 합니다. 또한 Microsoft에서 모든 고객에게 권장하는 업데이트만 포함합니다.

이러한 업데이트에는 다음이 포함됩니다.  

- 1806, 1810 또는 1902 버전과 같은 새 버전.  

- 현재 버전에 대한 새로운 기능을 포함하는 업데이트입니다.

- 사용자의 Configuration Manager 버전에 해당하며 모든 고객이 설치해야 하는 핫픽스입니다.

    > [!Note]  
    > 버전 1902부터 콘솔 내 핫픽스는 대체 관계에 있습니다. 자세한 내용은 [콘솔 내 핫픽스 대체](#bkmk_supersede)를 참조하세요.

콘솔 내 업데이트는 안정성을 향상시키고, 일반적인 문제를 해결합니다. 모든 고객에게 해당하는 서비스 팩, 누적 업데이트, 핫픽스 및 Microsoft Intune용 확장 같은 이전 제품 버전에 대한 업데이트 유형을 대체합니다.

콘솔 내 업데이트는 하나 이상의 다음 시스템에 적용됩니다.  

- 기본 및 중앙 관리 사이트 서버  

- 사이트 시스템 역할 및 사이트 시스템 서버  

- SMS 공급자 인스턴스  

- Configuration Manager 콘솔  

- Configuration Manager 클라이언트  

Configuration Manager는 사용자를 위해 새 업데이트를 검색합니다. Configuration Manager 서비스 연결 지점과 다음 동작을 기록하는 Microsoft 클라우드 서비스와 동기화합니다.  

- 서비스 연결 지점이 온라인 모드이면 사이트는 Microsoft와 매일 동기화합니다. 인프라에 적용되는 새 업데이트를 자동으로 식별합니다. 업데이트 및 재배포 가능 파일을 다운로드하려면 서비스 연결 지점 사이트 시스템 역할을 호스트하는 컴퓨터는 **시스템** 컨텍스트를 사용하여 다음 인터넷 위치(go.microsoft.com 및 download.microsoft.com)에 액세스합니다. 서비스 연결 지점에서 사용하는 추가 위치에 대한 자세한 내용은 [인터넷 액세스 요구 사항](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)을 참조하세요.  

- 서비스 연결 지점이 오프라인 모드인 경우 서비스 연결 도구를 사용하여 Microsoft 클라우드와 수동으로 동기화합니다. 자세한 내용은 [서비스 연결 도구 사용](/sccm/core/servers/manage/use-the-service-connection-tool)을 참조하세요.  

- 콘솔 내 업데이트는 개별적인 업데이트, 서비스 팩, 새 기능을 독립적으로 찾아서 설치할 필요성을 대체합니다.  

- 선택한 콘솔 내 업데이트만 설치합니다. 일부 업데이트를 설치할 때 사용하도록 설정할 개별 기능을 선택할 수 있습니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.  

콘솔 내 업데이트를 설치하는 경우 다음 프로세스가 발생합니다.  

- 필수 구성 요소 확인이 자동으로 실행됩니다. 설치를 시작하기 전에 이런 확인을 수동으로 실행할 수도 있습니다.  

- 사용자 환경에서 최상위 사이트를 설치합니다. 이 사이트는 있는 경우 중앙 관리 사이트입니다. 계층 구조에서 업데이트가 기본 사이트에 자동으로 설치됩니다. [사이트 서버에 대한 서비스 기간](/sccm/core/servers/manage/service-windows)을 사용하여 각각의 기본 사이트 서버가 업데이트하도록 허용할 시기를 제어합니다.  

- 사이트 서버 업데이트 후에는, 영향을 받은 모든 사이트 시스템 역할이 자동으로 업데이트됩니다. 이러한 역할은 SMS 공급자의 인스턴스를 포함합니다. 사이트에 업데이트가 설치된 후 Configuration Manager 콘솔에서 콘솔 사용자에게 콘솔을 업데이트하라는 메시지를 표시합니다.  

- 업데이트에 Configuration Manager 클라이언트가 포함되어 있으면 프로덕션에 앞서 업데이트를 테스트하거나 모든 클라이언트에 업데이트를 즉시 적용할 수 있는 옵션이 제공됩니다.  

- 기본 사이트가 업데이트된 후에 보조 사이트는 자동으로 업데이트되지 않습니다. 대신에, 사용자가 보조 사이트 업데이트를 수동으로 시작해야 합니다.  

> [!NOTE]  
> Configuration Manager 현재 분기, 장기 서비스 분기 및 기술 미리 보기 분기는 다른 릴리스입니다. 한 분기에 적용되는 업데이트를 다른 분기에 대한 콘솔 내 업데이트로 사용할 수 없습니다. 사용 가능한 분기에 대한 자세한 내용은 [사용해야 하는 Configuration Manager 분기](/sccm/core/understand/which-branch-should-i-use)를 참조하세요.

### <a name="bkmk_supersede"></a> 콘솔 내 핫픽스 대체

<!-- 3229613 -->
버전 1902부터 콘솔 내 핫픽스는 대체 관계에 있습니다. Microsoft가 새 Configuration Manager 핫픽스를 게시하면 이 새 핫픽스로 대체되는 핫픽스가 더 이상 콘솔에 표시되지 않습니다. 이 새 동작은 설치할 핫픽스를 좀 더 쉽게 확인할 수 있도록 도와줍니다.

### <a name="supersedence-example"></a>대체 규칙

사용할 수 있는 핫픽스로는 핫픽스-A, 핫픽스-B, 핫픽스-C 세 가지가 있습니다. 핫픽스-A는 핫픽스-B로 대체되고, 핫픽스-B는 핫픽스-C로 대체됩니다.

|핫픽스-A|핫픽스-B|핫픽스-C|콘솔 내 보기|
|--------|--------|--------|---------------|
|설치 안 됨|설치 안 됨|설치 안 됨|세 가지 핫픽스 모두 표시|
|설치됨|설치됨|설치 안 됨|핫픽스-B는 설치된 것으로 표시<br/>핫픽스-C는 설치 준비가 완료된 것으로 표시|
|설치 안 됨|설치 안 됨|설치됨|핫픽스-C는 설치된 것으로 표시|


## <a name="bkmk_outofband"></a> 대역 외 핫픽스  

일부 핫픽스는 특정 문제를 처리할 가능성이 제한된 상태로 릴리스됩니다. 다른 핫픽스는 모든 고객에게 적용할 수 있지만 콘솔 내 메서드를 사용하여 설치할 수 없습니다. 이러한 수정 프로그램은 대역 외로 제공되며 Microsoft 클라우드 서비스에서 찾을 수 없습니다.  

일반적으로 Configuration Manager 배포 문제를 해결하거나 처리하려는 경우 Microsoft 고객 지원 서비스, Microsoft 지원 지술 자료 문서 또는 [Configuration Manager 팀 블로그](https://techcommunity.microsoft.com/t5/Configuration-Manager-Blog/bg-p/ConfigurationManagerBlog)에서 대역 외 핫픽스에 관해 학습할 수 있습니다.

이러한 수정 프로그램은 다음 두 가지 방법 중 한 가지를 사용하여 수동으로 설치합니다.  

#### <a name="update-registration-tool"></a>업데이트 등록 도구

이 도구로 핫픽스를 Configuration Manager 콘솔에 수동으로 가져옵니다. 그런 다음, 자동으로 검색되는 콘솔 내 업데이트를 수행할 때 업데이트를 설치합니다.  

이 메서드는 다음과 같은 파일 이름 구조를 사용하는 핫픽스에 사용됩니다.  
    `<Product>-<product version>-<KB article ID>-ConfigMgr.Update.exe`

자세한 내용은 [업데이트 등록 도구를 사용하여 핫픽스 가져오기](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes)를 참조하세요.  

#### <a name="hotfix-installer"></a>핫픽스 설치 관리자

콘솔 내 메서드를 사용하여 설치할 수 없는 핫픽스를 수동으로 설치하려면 이 도구를 사용합니다.  

이 메서드는 다음과 같은 파일 이름 구조를 사용하는 핫픽스에 사용됩니다.  
    `<Product>-<product version>-<KB article ID>-<platform>-<language>.exe`  

자세한 내용은 [핫픽스 설치 관리자를 사용하여 업데이트 설치](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates)를 참조하세요.  


## <a name="next-steps"></a>다음 단계

다음 문서는 Configuration Manager에 대한 다양한 업데이트 형식을 찾아서 설치하는 방법을 이해하는 데 유용합니다.  

- [콘솔 내 업데이트 설치](/sccm/core/servers/manage/install-in-console-updates)  

- [서비스 연결 도구 사용](/sccm/core/servers/manage/use-the-service-connection-tool)  

- [핫픽스를 가져오려면 업데이트 등록 도구 사용](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes)  

- [업데이트를 설치하려면 핫픽스 설치 관리자 사용](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates)  

기술 미리 보기 분기에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.
