---
title: 분류 및 제품 구성
titleSuffix: Configuration Manager
description: 다음 단계에 따라 Configuration Manager 콘솔에서 동기화할 소프트웨어 업데이트 분류 및 제품을 구성하세요.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.openlocfilehash: 8d8373a060e3ee798c43b5b5defc8e4de2262f41
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75827318"
---
# <a name="configure-classifications-and-products-to-synchronize"></a>동기화할 분류 및 제품 구성  

*적용 대상: Configuration Manager(현재 분기)*

소프트웨어 업데이트 메타데이터는 동기화 과정 중에 소프트웨어 업데이트 지점 구성 요소 속성에서 지정한 설정에 따라 Configuration Manager에서 검색됩니다. 소프트웨어 업데이트를 처음 동기화한 후 또는 새 제품 및 분류가 출시된 경우 속성에서 새 항목을 선택해야 합니다. 동기화할 분류 및 제품을 구성하려면 다음 절차를 수행하세요.  

> [!NOTE]  
> 이 섹션의 절차는 최상위 사이트에서만 수행하세요.  

## <a name="to-configure-classifications-and-products-to-synchronize"></a>동기화할 분류 및 제품을 구성하려면  

1. **Configuration Manager** 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동합니다.

2. 중앙 관리 사이트나 독립 실행형 기본 사이트를 선택합니다.  

3. **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성**과 **소프트웨어 업데이트 지점**을 차례로 클릭합니다.

4. **분류** 탭에서 소프트웨어 업데이트를 동기화할 소프트웨어 업데이트 분류를 지정합니다.  

    모든 소프트웨어 업데이트는 다양한 유형의 업데이트를 정리하는 데 도움이 되는 업데이트 분류와 함께 정의됩니다. 동기화 프로세스 중에는 지정한 분류에 대한 소프트웨어 업데이트 메타데이터가 동기화됩니다. Configuration Manager에서는 다음 업데이트 분류와 소프트웨어 업데이트를 동기화하는 기능을 제공합니다.  

     - **중요 업데이트**: 보안과 관련 없는 중요한 버그를 다루는, 특정 문제에 대해 광범위하게 릴리스되는 수정 사항을 지정합니다.  
     - **정의 업데이트**: 제품 정의 데이터베이스에 대한 추가를 포함하여 광범위하게 릴리스되는 잦은 소프트웨어 업데이트를 지정합니다.  
     - **기능 팩**: 처음에는 제품 릴리스와 별도로 배포되었다가 보통은 차후의 정품 릴리스에 포함되는 새 제품 기능을 지정합니다.  
     - **보안 업데이트**: 제품에 특정한 보안 관련 취약성에 대해 대폭 릴리스된 수정 사항을 지정합니다.  
     - **서비스 팩**: 제품에 적용되는 모든 핫픽스, 보안 업데이트, 중요 업데이트 및 업데이트의 테스트된 누적 집합을 지정합니다. 서비스 팩에는 제품 릴리스 후 내부적으로 발견된 문제의 추가적인 수정 사항도 포함될 수 있습니다.  
     - **도구**: 하나 이상의 작업을 완료하는 데 도움이 되는 유틸리티 또는 기능을 지정합니다.  
     - **업데이트 롤업**: 손쉬운 배포를 위해 하나의 패키지로 묶인 핫픽스, 보안 업데이트, 중요 업데이트 및 업데이트의 테스트된 누적 집합입니다. 업데이트 롤업은 일반적으로 보안 또는 제품 구성 요소 등과 같은 특정 영역을 다룹니다.  
     - **업데이트**: 특정 문제에 대해 광범위하게 릴리스되는 수정 사항을 지정합니다. 업데이트는 중요하지 않으면서 보안과는 무관한 버그를 해결합니다.  
     - **업그레이드**: Windows 10 기능 및 작동에 대한 업그레이드를 지정합니다. **업그레이드** 분류를 가져오려면 소프트웨어 업데이트 지점 및 사이트에서 [핫픽스 3095113](https://support.microsoft.com/kb/3095113)이 있는 최소 WSUS 6.2를 실행해야 합니다. 이 업데이트 및 **업그레이드**를 위한 기타 업데이트를 설치 하는 방법에 대 한 자세한 내용은 [소프트웨어 업데이트에 대 한 필수 조건](/sccm/sum/plan-design/prerequisites-for-software-updates#BKMK_wsus2012)을 참조 하세요.

    > [!NOTE]
    > Microsoft surface **드라이버 및 펌웨어 업데이트 포함** 확인란을 선택 하 여 microsoft surface 드라이버를 동기화 할 수 있습니다.<!--1098490--> 자세한 내용은 [Microsoft Surface 드라이버 및 펌웨어 업데이트 포함](#bkmk_Surface) 섹션을 참조 하세요.

5. **제품** 탭에서 소프트웨어 업데이트를 동기화할 제품을 지정한 다음 **닫기**를 클릭합니다.  

    - Configuration Manager에는 소프트웨어 업데이트 지점을 처음 설치할 때 선택할 수 있는 제품 및 제품군의 목록이 저장됩니다. Configuration Manager를 릴리스한 후에 릴리스된 제품 및 제품군은 선택 가능한 제품 및 제품군 목록을 업데이트하는 소프트웨어 업데이트 동기화를 완료할 때까지 선택하지 못할 수 있습니다.  

    - 각 소프트웨어 업데이트의 메타데이터는 업데이트를 적용할 수 있는 제품을 정의합니다. 제품은 Windows Server 2012와 같은 특정 버전의 운영 체제 또는 애플리케이션입니다. 제품군은 개별 제품이 파생되는 기본 운영 체제 또는 애플리케이션입니다. 제품군의 예로는 Windows를 들 수 있으며, Windows Server 2012는 Windows에 속합니다. 하나의 제품군 안에 다른 제품군 또는 개별 제품을 지정할 수 있습니다. 선택한 제품이 많을수록 소프트웨어 업데이트를 동기화하는 시간이 더 오래 걸립니다.  

    - 소프트웨어 업데이트를 여러 제품에 적용할 수 있고, 하나 이상의 제품이 동기화되도록 선택되었을 때 일부 제품을 선택하지 않아도 모든 제품이 Configuration Manager 콘솔에 표시됩니다. 예를 들어 Windows Server 2012 운영 체제만 선택했지만 소프트웨어 업데이트가 Windows 8 및 Windows Server 2012에 적용되는 경우 두 제품이 모두 Configuration Manager 콘솔에 표시됩니다.  

    > [!NOTE]  
    > **Windows 10 버전 1903 이상**이 이전 버전처럼 **Windows 10** 제품의 일부가 아닌 제품 자체로 Microsoft 업데이트에 추가되었습니다. 이번 변화로 인해 클라이언트가 이러한 업데이트를 확인할 수 있도록 여러 수동 단계를 수행해야 했습니다. Configuration Manager 버전 1906에서 새 제품을 위해 수행 해야 하는 수동 단계의 수를 줄이는 데 도움을 주었습니다. <!--4682946-->
    >
    > Configuration Manager 버전 1906으로 업데이트할 때 **Windows 10** 제품을 동기화하도록 선택한 경우 다음 작업이 자동으로 수행됩니다.
    > - **Windows 10 버전 1903 이상** 제품이 동기화에 추가됩니다.
    > - **Windows 10** 제품을 포함하고 있는 [자동 배포 규칙](/sccm/sum/deploy-use/automatically-deploy-software-updates#bkmk_adr-process)은 **Windows 10 버전 1903 이상**을 포함하도록 업데이트됩니다.
    > - [서비스 플랜](/sccm/osd/deploy-use/manage-windows-as-a-service#servicing-plan-workflow)은 **Windows 10 버전 1903 이상** 제품을 포함하도록 업데이트됩니다.

## <a name="bkmk_Surface"></a>Microsoft Surface 드라이버 및 펌웨어 업데이트 포함

Microsoft surface **드라이버 및 펌웨어 업데이트 포함** 확인란을 선택 하 여 microsoft surface 드라이버를 동기화 할 수 있습니다.<!--1098490--> Surface 드라이버를 성공적으로 동기화 하려면 모든 소프트웨어 업데이트 지점이 누적 업데이트 [KB4025339](https://support.microsoft.com/help/4025339) 이상 설치 된 Windows Server 2016를 실행 해야 합니다. Surface 드라이버를 사용하도록 설정한 후 Windows Server 2012를 실행하는 컴퓨터에서 소프트웨어 업데이트 지점을 사용하도록 설정하면 드라이버 업데이트에 대한 검색 결과가 정확하지 않습니다. 이에 따라 Configuration Manager 콘솔 및 Configuration Manager 보고서에서 잘못된 준수 데이터가 표시됩니다.  

- 이 기능은 버전 1706에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1710 버전부터 이 기능은 더 이상 시험판 기능이 아닙니다.  
- Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  
- ARM 장치용 드라이버는 동기화를 지원 하지 않습니다.

## <a name="configuring-products-for-versions-of-windows-10"></a>Windows 10 버전에 대 한 제품 구성

### <a name="windows-10-version-1909"></a>Windows 10, 버전 1909

Windows 10, 버전 1909은 Windows 10 버전 1903과 공통 핵심 운영 체제를 공유 합니다. 이러한 두 버전은 모두 동일한 누적 업데이트를 사용 하 여 처리 됩니다. Windows 10, 버전 1909에 대 한 자세한 내용은 [windows 10, 버전 1909 배달 옵션](https://aka.ms/1909mechanics) 블로그 게시물을 참조 하세요.

Windows 10 버전 1909 및 Windows 10 버전 1903 클라이언트 모두 Configuration Manager의 업데이트를 설치 하려면 다음을 수행 합니다.

- 1909 및 1903 버전의 Windows 10에 대 한 업데이트를 승인 합니다.
  - 업데이트에는 각 OS 버전에 대 한 제목 및 적용 가능성 규칙이 다릅니다.
  - 버전 당 각 업데이트 및 OS 아키텍처를 승인 하면 관리자에 대 한 일반 승인 프로세스가 유지 됩니다.
- 누적 업데이트 설치 파일은 Windows 10의 1909 및 1903 버전 모두에 대해 동일 합니다.
  - Configuration Manager 업데이트 원본 파일만 다운로드 됩니다.

#### <a name="feature-updates-for-windows-10-version-1909"></a>Windows 10 버전 1909에 대 한 기능 업데이트

Windows 10 버전 1909에 대 한 기능 업데이트를 승인 하는 경우 다음과 같은 몇 가지 옵션이 표시 됩니다.

- Windows 10, 버전 1903 클라이언트에는 2019 년 11 월 12 일 출시 된 사용할 수 있는 [패키지가](https://support.microsoft.com/en-us/help/4517245/feature-update-via-windows-10-version-1909-enablement-package)제공 됩니다.
  - 이 패키지는 Windows 10 버전 1909 기능을 활성화 하 고 장치를 다시 시작 하는 작고 빠른 설치 파일입니다.
  - 활성화 패키지에 대 한 필수 구성 요소는 다음과 같습니다.
    - 2019 년 10 월 8 일에 릴리스된 [KB4517389](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4517389)의 최소 누적 업데이트입니다.
    - 2019 년 9 월 24 일 출시 된 [KB4520390](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4520390)의 최소 서비스 스택 업데이트입니다.
  - 다른 기능 업데이트와 마찬가지로이 업데이트는 `https:\\catalog.update.microsoft.com`에서 가져올 수 없습니다.
  - **Windows 10, 버전 1903 이상** 제품 및 동기화를 위해 선택한 **업그레이드** 분류가 있는 경우 업데이트가 WSUS와 자동으로 동기화 됩니다.
  - Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동 하 여 **windows 10 서비스**를 확장 하 고 **모든 windows 10 업데이트** 노드를 선택 합니다. "사용" 또는 "4517245" 용어를 검색 합니다.

    > [!TIP]
    > 이러한 기능은 기능 업데이트 이므로 **모든 소프트웨어 업데이트** 노드에는 없습니다.

- Windows 10, 버전 1809 및 이전 버전의 클라이언트는 단일 직접 기능 업데이트를 사용 하 여 업그레이드 됩니다.
  - 이는 Windows 10에 대해 수행한 기능 업데이트에 대 한 다른 모든 이전 설치와 동일 합니다.

> [!NOTE]
> 사용 패키지와 Windows 10 용 기존 기능 업데이트 (버전 1909)는 설치에 사용 된 경로에 관계 없이 보고에 "설치 됨"으로 표시 됩니다.

### <a name="windows-10-version-1903-and-later"></a>Windows 10 버전 1903 이상​

**Windows 10 버전 1903 이상**이 이전 버전처럼 **Windows 10** 제품의 일부가 아닌 제품 자체로 Microsoft 업데이트에 추가되었습니다. 이번 변화로 인해 클라이언트가 이러한 업데이트를 확인할 수 있도록 여러 수동 단계를 수행해야 했습니다. Configuration Manager 버전 1906에서 새 제품을 위해 수행 해야 하는 수동 단계의 수를 줄이는 데 도움을 주었습니다. <!--4682946-->

#### <a name="windows-10-version-1903-and-later-with-configuration-manager-version-1906"></a>Windows 10 버전 1903 이상 Configuration Manager 버전 1906
Configuration Manager 버전 1906으로 업데이트할 때 **Windows 10** 제품을 동기화하도록 선택한 경우 다음 작업이 자동으로 수행됩니다.
- **Windows 10 버전 1903 이상** 제품이 동기화에 추가됩니다.
- **Windows 10** 제품을 포함하고 있는 [자동 배포 규칙](/sccm/sum/deploy-use/automatically-deploy-software-updates#bkmk_adr-process)은 **Windows 10 버전 1903 이상**을 포함하도록 업데이트됩니다.
- [서비스 플랜](/sccm/osd/deploy-use/manage-windows-as-a-service#servicing-plan-workflow)은 **Windows 10 버전 1903 이상** 제품을 포함하도록 업데이트됩니다.

#### <a name="windows-10-version-1903-and-later-with-configuration-manager-version-1902"></a>Windows 10 버전 1903 이상 Configuration Manager 버전 1902
Windows 10, 버전 1903 클라이언트에서 Configuration Manager 1902를 사용 하는 경우 다음을 수행 해야 합니다.
- 동기화를 위해 **Windows 10 버전 1903 이상** 제품을 선택합니다.
- Windows 10 버전 1903 클라이언트에 대 한 [자동 배포 규칙](/sccm/sum/deploy-use/automatically-deploy-software-updates#bkmk_adr-process) 을 업데이트 합니다.
- Windows 10 버전 1903 클라이언트에 대 한 [설치 계획](/sccm/osd/deploy-use/manage-windows-as-a-service#servicing-plan-workflow) 을 업데이트 합니다.

## <a name="bkmk_WIfB"></a> Windows 참가자 프로그램
<!--3556023-->
2019년 9월부터 Configuration Manager를 사용하여 Windows Insider Preview 빌드를 실행하는 디바이스를 서비스하고 업데이트할 수 있습니다. 이러한 변화를 통해, 일반적인 프로세스를 변경하거나 비즈니스용 Windows 업데이트를 사용 하도록 설정하지 않고도 이러한 디바이스를 관리할 수 있음을 알 수 있습니다. Windows Insider Preview 빌드의 기능 업데이트 및 누적 업데이트는 다른 Windows 10 업데이트 또는 업그레이드와 마찬가지로 Configuration Manager에 다운로드할 수 있습니다. 자세한 내용은 [WSUS에 시험판 Windows 10 기능 업데이트 게시](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/Publishing-pre-release-Windows-10-feature-updates-to-WSUS/ba-p/845054) 블로그 게시물을 참조 하세요.

Configuration Manager의 Windows 참가자 지원에 대 한 자세한 내용은 [windows 10 지원](/sccm/core/plan-design/configs/support-for-windows-10#bkmk_WIfB-support)을 참조 하세요.

### <a name="prerequisites"></a>전제 조건

- [소프트웨어 업데이트 관리](/sccm/sum/plan-design/plan-for-software-updates)를 위해 구성 된 Configuration Manager 버전 1906 이상
- [Windows Insider preview 빌드](https://docs.microsoft.com/windows-insider/at-work-pro/wip-4-biz-get-started)를 실행 하는 windows 10 장치입니다.
- Windows 참가자 장치를 포함 하는 컬렉션입니다.

### <a name="enable-windows-insider-upgrades-and-updates"></a>Windows 참가자 업그레이드 및 업데이트 사용

Windows 참가자 업그레이드 및 업데이트에 대해 제품 및 분류를 사용 하도록 설정 해야 합니다. Windows 참가자에 대 한 기능 업데이트, 누적 업데이트 및 기타 업데이트는 **Windows 참가자 시험판** 제품 범주에 있습니다.

1. **Configuration Manager** 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동합니다.
2. 중앙 관리 사이트나 독립 실행형 기본 사이트를 선택합니다.  
3. **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성**과 **소프트웨어 업데이트 지점**을 차례로 클릭합니다.
4. **제품** 탭에서 동기화를 위해 다음 제품을 선택 했는지 확인 합니다.
    - Windows 참가자 시험판
    - Windows 10 버전 1903 이상​
5. **분류** 탭에서 동기화를 위해 다음 분류가 선택 되어 있는지 확인 합니다.
    - 업그레이드
    - 보안 업데이트
    - 업데이트 (옵션)
6. **확인**을 클릭하여 **소프트웨어 업데이트 지점 구성 요소 속성**을 닫습니다.

### <a name="upgrading-windows-insider-devices"></a>Windows 참가자 장치 업그레이드

Windows 참가자에 대 한 업그레이드가 동기화 되 면 **소프트웨어 라이브러리** > **windows 10 서비스** > **모든 windows 10 업데이트**에서 볼 수 있습니다.

![Windows 10 서비스에 대 한 windows 참가자 기능 업데이트](media/3556023-windows-insiders-pre-release-feature-update.png)

다른 업그레이드와 마찬가지로 Windows 참가자 용 기능 업데이트를 대상 컬렉션에 배포 합니다. 그러나 이러한 기능 업데이트를 배포 하는 경우 다음 항목을 염두에 두어야 합니다.

- 이러한 업그레이드는 아키텍처, 버전 및 언어가 일치 하는 모든 Windows 10 클라이언트 1903 이전 버전에 적용할 수 있습니다.
- 사용 조건이 있으므로 배포에서 설치를 위해 약관에 동의 해야 합니다.
- [클라이언트 설정에서 스레드 우선 순위](/sccm/core/clients/deploy/about-client-settings#bkmk_thread-priority)를 사용 하는 것이 좋습니다.
- 동적 업데이트는 최신 누적 업데이트를 포함 하 여 Microsoft 업데이트에서 직접 중요 업데이트를 자동으로 설치 합니다. 이 동작은 Windows 10 버전 1903에 대 한 기능 업데이트에서 시작 되었습니다. 
  - 클라이언트 설정 또는 [setupconfig 파일](https://docs.microsoft.com/windows-hardware/manufacture/desktop/windows-setup-command-line-options)을 사용 하 여 [동적 업데이트를 명시적으로 사용 하지 않도록 설정할](/sccm/core/clients/deploy/about-client-settings#bkmk_du) 수 있습니다. 
  - 자세한 내용은 [Windows 10 동적 업데이트](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/The-benefits-of-Windows-10-Dynamic-Update/ba-p/467847) 블로그 게시물을 참조 하세요.

업그레이드를 배포 하는 방법에 대 한 자세한 내용은 [Windows as a Service 관리](/sccm/osd/deploy-use/manage-windows-as-a-service)를 참조 하세요.


### <a name="keeping-insider-devices-up-to-date"></a>Insider 장치를 최신 상태로 유지

Windows 참가자에 대 한 누적 업데이트는 WSUS 및 Configuration Manager 확장에 사용할 수 있습니다. 이러한 누적 업데이트는 Windows 10 버전 1903 누적 업데이트와 유사한 빈도로 릴리스됩니다. Windows 참가자 누적 업데이트는 **Windows 참가자 시험판** 제품 범주에 있으며 **보안 업데이트** 또는 **업데이트로**분류 됩니다. [자동 배포 규칙](/sccm/sum/deploy-use/automatically-deploy-software-updates) 또는 [단계적 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/sccm/sum/toc.json&bc=/sccm/sum/breadcrumb/toc.json)를 사용 하는 등의 일반 소프트웨어 업데이트 프로세스를 사용 하 여 Windows 참가자에 대 한 누적 업데이트를 배포할 수 있습니다.

## <a name="bkmk_ESU"></a> 확장 보안 업데이트 및 Configuration Manager

[확장 보안 업데이트(ESU)](https://support.microsoft.com/help/4497181/lifecycle-faq-extended-security-updates) 프로그램은 지원 종료 이후 특정 레거시 Microsoft 제품을 실행해야 하는 고객이 최후의 수단으로 쓸 수 있는 옵션입니다. 여기에는 제품의 확장 지원 종료 날짜 이후 최대 3년간 ([Microsoft 보안 대응 센터(MSRC)](https://www.microsoft.com/msrc)에서 정의한) 긴급 및/또는 중요 보안 업데이트가 포함되어 있습니다.

즉, 지원 주기가 끝난 제품은 Configuration Manager에서 사용할 수 없습니다. 여기에는 ESU 프로그램에서 설명하는 모든 제품이 포함됩니다. ESU 프로그램에서 릴리스된 보안 업데이트는 WSUS(Windows Server Update Services)에 게시됩니다. 이러한 업데이트는 Configuration Manager 콘솔에 표시됩니다. ESU 프로그램에서 설명하는 제품은 더 이상 Configuration Manager에서 사용할 수 없지만 프로그램에서 릴리스된 Windows 보안 업데이트를 배포하고 설치하는 데는 [Configuration Manager 현재 분기의 최신 릴리스 버전](/sccm/core/servers/manage/updates#version-details)을 사용할 수 있습니다. 최신 릴리스 버전은 OSD(운영 체제 배포)를 통해 지원되는 OS를 배포할 때도 사용할 수 있습니다.

Windows 소프트웨어 업데이트 관리와 관련되지 않은 클라이언트 관리 기능 또는 OSD는 ESU 프로그램에서 다루는 운영 체제에서 더 이상 테스트되지 않으며 계속 작동한다는 보장이 없습니다. 클라이언트 관리 지원을 받으려면 가능한 한 빨리 최신 버전의 운영 체제로 업그레이드하거나 마이그레이션하는 것이 좋습니다.


## <a name="next-steps"></a>다음 단계

소프트웨어 업데이트 동기화를 시작하여 새 기준을 기반으로 소프트웨어 업데이트를 검색합니다. 자세한 내용은 [소프트웨어 업데이트 동기화](synchronize-software-updates.md)를 참조하세요.
