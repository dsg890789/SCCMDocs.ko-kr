---
title: 분류 및 제품 구성
titleSuffix: Configuration Manager
description: 다음 단계에 따라 Configuration Manager 콘솔에서 동기화할 소프트웨어 업데이트 분류 및 제품을 구성하세요.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 02/15/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 5ddde4e6-d553-4182-b752-6bc8b4a26745
ms.collection: M365-identity-device-management
ms.openlocfilehash: f1d984598288434aa1e81c6bd2c51a315edfa551
ms.sourcegitcommit: fd16fc2b681608fd6def5bad2cedffbcd1f2423a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56405695"
---
#  <a name="configure-classifications-and-products-to-synchronize"></a>동기화할 분류 및 제품 구성  

*적용 대상: System Center Configuration Manager(현재 분기)*


> [!NOTE]  
>  이 섹션의 절차는 최상위 사이트에서만 수행하세요.  

 소프트웨어 업데이트 메타데이터는 동기화 과정 중에 소프트웨어 업데이트 지점 구성 요소 속성에서 지정한 설정에 따라 Configuration Manager에서 검색됩니다. 소프트웨어 업데이트를 처음 동기화한 후 또는 새 제품 및 분류가 출시된 경우 속성에서 새 항목을 선택해야 합니다. 동기화할 분류 및 제품을 구성하려면 다음 절차를 수행하세요.  

#### <a name="to-configure-classifications-and-products-to-synchronize"></a>동기화할 분류 및 제품을 구성하려면  

1.  **Configuration Manager** 콘솔에서 **관리** > **사이트 구성** > **사이트**로 이동합니다.

2. 중앙 관리 사이트나 독립 실행형 기본 사이트를 선택합니다.  

3.  **홈** 탭의 **설정** 그룹에서 **사이트 구성 요소 구성**과 **소프트웨어 업데이트 지점**을 차례로 클릭합니다.

4.  **분류** 탭에서 소프트웨어 업데이트를 동기화할 소프트웨어 업데이트 분류를 지정합니다.  

    > [!NOTE]  
    >  모든 소프트웨어 업데이트는 다양한 유형의 업데이트를 정리하는 데 도움이 되는 업데이트 분류와 함께 정의됩니다. 동기화 프로세스 중에는 지정한 분류에 대한 소프트웨어 업데이트 메타데이터가 동기화됩니다. Configuration Manager에서는 다음 업데이트 분류와 소프트웨어 업데이트를 동기화하는 기능을 제공합니다.  
    >   
    > - **중요 업데이트**: 보안과 관련 없는 중요한 버그를 다루는, 특정 문제에 대해 광범위하게 릴리스되는 수정 사항을 지정합니다.  
    > - **정의 업데이트**: 제품 정의 데이터베이스에 대한 추가를 포함하여 광범위하게 릴리스되는 잦은 소프트웨어 업데이트를 지정합니다.  
    > - **기능 팩**: 처음에는 제품 릴리스와 별도로 배포되었다가 보통은 차후의 정품 릴리스에 포함되는 새 제품 기능을 지정합니다.  
    > - **보안 업데이트**: 제품에 특정한 보안 관련 취약성에 대해 대폭 릴리스된 수정 사항을 지정합니다.  
    > - **서비스 팩**: 제품에 적용되는 모든 핫픽스, 보안 업데이트, 중요 업데이트 및 업데이트의 테스트된 누적 집합을 지정합니다. 서비스 팩에는 제품 릴리스 후 내부적으로 발견된 문제의 추가적인 수정 사항도 포함될 수 있습니다.  
    > - **도구**: 하나 이상의 작업을 완료하는 데 도움이 되는 유틸리티 또는 기능을 지정합니다.  
    > - **업데이트 롤업**: 손쉬운 배포를 위해 하나의 패키지로 묶인 핫픽스, 보안 업데이트, 중요 업데이트 및 업데이트의 테스트된 누적 집합입니다. 업데이트 롤업은 일반적으로 보안 또는 제품 구성 요소 등과 같은 특정 영역을 다룹니다.  
    > - **업데이트**: 특정 문제에 대해 광범위하게 릴리스되는 수정 사항을 지정합니다. 업데이트는 중요하지 않으면서 보안과는 무관한 버그를 해결합니다.  
    > - **업그레이드**: Windows 10 기능 및 작동에 대한 업그레이드를 지정합니다. **업그레이드** 분류를 가져오려면 소프트웨어 업데이트 지점 및 사이트에서 [핫픽스 3095113](https://support.microsoft.com/kb/3095113)이 있는 최소 WSUS 4.0을 실행해야 합니다.    
    >       

    > [!NOTE]    
    > Configuration Manager 버전 1706부터 **Microsoft Surface 드라이버 및 펌웨어 업데이트 포함** 확인란을 선택하여 Microsoft Surface 드라이버를 동기화할 수 있습니다.<!--1098490--> Surface 드라이버를 성공적으로 동기화하려면 모든 소프트웨어 업데이트 지점에서 Windows Server 2016을 실행해야 합니다. Surface 드라이버를 사용하도록 설정한 후 Windows Server 2012를 실행하는 컴퓨터에서 소프트웨어 업데이트 지점을 사용하도록 설정하면 드라이버 업데이트에 대한 검색 결과가 정확하지 않습니다. 이에 따라 Configuration Manager 콘솔 및 Configuration Manager 보고서에서 잘못된 준수 데이터가 표시됩니다.  
    >  
    > 이 기능은 버전 1706에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1710 버전부터 이 기능은 더 이상 시험판 기능이 아닙니다.  
    >  
    > Configuration Manager는 기본적으로 이 선택적 기능을 활성화하지 않습니다. 이 기능은 사용하기 전에 활성화해야 합니다. 자세한 내용은 [업데이트에서 선택적 기능 사용](/sccm/core/servers/manage/install-in-console-updates#bkmk_options)을 참조하세요.<!--505213-->  

5.  **제품** 탭에서 소프트웨어 업데이트를 동기화할 제품을 지정한 다음 **닫기**를 클릭합니다.  

    > [!NOTE]  
    >  각 소프트웨어 업데이트의 메타데이터는 업데이트를 적용할 수 있는 제품을 정의합니다. 제품은 Windows Server 2012와 같은 특정 버전의 운영 체제 또는 애플리케이션입니다. 제품군은 개별 제품이 파생되는 기본 운영 체제 또는 애플리케이션입니다. 제품군의 예로는 Windows를 들 수 있으며, Windows Server 2012는 Windows에 속합니다. 하나의 제품군 안에 다른 제품군 또는 개별 제품을 지정할 수 있습니다. 선택한 제품이 많을수록 소프트웨어 업데이트를 동기화하는 시간이 더 오래 걸립니다.  
    >   
    >  소프트웨어 업데이트를 여러 제품에 적용할 수 있고 하나 이상의 제품이 동기화되도록 선택하면 일부 제품을 선택하지 않아도 모든 제품이 Configuration Manager 콘솔에 표시됩니다. 예를 들어 Windows Server 2012 운영 체제만 선택했지만 소프트웨어 업데이트가 Windows 8 및 Windows Server 2012에 적용되는 경우 두 제품이 모두 Configuration Manager 콘솔에 표시됩니다.  

    > [!IMPORTANT]  
    >  Configuration Manager에는 소프트웨어 업데이트 지점을 처음 설치할 때 선택할 수 있는 제품 및 제품군의 목록이 저장됩니다. Configuration Manager를 릴리스한 후에 릴리스된 제품 및 제품군은 선택 가능한 제품 및 제품군 목록을 업데이트하는 소프트웨어 업데이트 동기화를 완료할 때까지 선택하지 못할 수 있습니다.  

## <a name="next-steps"></a>다음 단계
소프트웨어 업데이트 동기화를 시작하여 새 기준을 기반으로 소프트웨어 업데이트를 검색합니다. 자세한 내용은 [소프트웨어 업데이트 동기화](synchronize-software-updates.md)를 참조하세요.
