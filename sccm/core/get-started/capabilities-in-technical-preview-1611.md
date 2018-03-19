---
title: "기술 미리 보기 1611의 기능"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager용 Technical Preview 버전 1611에서 사용 가능한 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d2ad00e8-9f10-41b6-816a-d8542c23a22e
caps.latest.revision: 
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: b56aee663319861427048fb722b1cdc0b5cc664d
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1611-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1611의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*



이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1611에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.    

**이 Technical Preview의 알려진 문제:**   
- ***필수 조건 상태***: 버전 1611을 설치하는 경우 필수 조건의 전반적인 상태가 통과(경고 있음)로 표시될 수도 있지만 경고를 발생한 필수 조건은 표시되지 않습니다. 다음 두 가지 필수 조건이 원인일 수 있습니다.
  - SQL 인덱스 생성 메모리 옵션
  - 지원되는 SQL Server 버전 검사  

 경고일 뿐이므로 무시해도 됩니다.

- ***PowerShell***: Configuration Manager 콘솔에서 Windows PowerShell에 연결하는 경우 다음 오류가 발생할 수 있습니다. **Microsoft.ConfigurationManagement.PowerShell.Types.ps1xml이 디지털 서명되어 있지 않습니다**.  

   특정 파일을 버전 1610의 서명된 버전으로 대체하여 이 문제를 해결할 수 있습니다. 버전 1610 설치의 **&lt;설치 디렉터리>\AdminConsole\bin\** 폴더에서 확장명이 **.psd1**, **.ps1xml** 및 **.psm1**인 파일을 모두 복사합니다. Technical Preview 1611 설치의 **&lt;설치 디렉터리>\AdminConsole\bin\** 폴더에 이 파일을 붙여넣어 1611 버전의 파일을 덮어씁니다.


**다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.**  

## <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>사용 가능한 배포 및 작업 순서에 대한 사전 캐시 콘텐츠
이 Technical Preview에서 사용 가능한 배포 및 작업 순서에 대해 사전 캐시 기능을 사용하도록 선택하여 사용자가 콘텐츠를 설치하기 전에 클라이언트에서 관련 콘텐츠만 다운로드하도록 할 수 있습니다.

예를 들어 Windows 10 현재 위치 업그레이드 작업 순서를 배포하고 모든 사용자에게 단일 작업 순서만 사용하려는데 여러 아키텍처 및/또는 언어가 있다고 가정해 보겠습니다. 현재 분기에서 사용 가능한 배포를 만든 후 사용자가 소프트웨어 센터에서 **설치**를 클릭하면 해당 시간에 콘텐츠가 다운로드됩니다. 이 때문에 설치를 시작할 준비가 되기 전에 추가 시간이 필요합니다. 또는 현재 분기에서 사용 가능한 작업 순서 배포를 만드는 경우 작업 순서에서 참조된 모든 콘텐츠가 다운로드됩니다. 여기에는 모든 언어 및 아키텍처에 대한 운영 체제 업그레이드 패키지가 포함됩니다. 각각 크기가 약 3GB인 경우 다운로드 패키지가 매우 클 수 있습니다.

사전 캐시 콘텐츠 기능을 사용하면 클라이언트가 배포를 받는 즉시 해당 콘텐츠만 다운로드할 수 있습니다. 따라서 사용자가 소프트웨어 센터에서 **설치**를 클릭할 때 콘텐츠가 준비되어 있으며, 콘텐츠가 로컬 하드 드라이브에 있으므로 설치가 신속하게 시작됩니다.

### <a name="to-configure-the-pre-cache-feature"></a>사전 캐시 기능을 구성하려면

1. 특정 아키텍처 및 언어에 대한 운영 체제 업그레이드 패키지를 만듭니다. 패키지의 **데이터 원본** 탭에서 아키텍처 및 언어를 지정합니다. 언어에 대해 10진수 변환을 사용합니다(예: 1033은 영어의 10진수이고, 0x0409는 동등한 16진수임). 자세한 내용은 [운영 체제를 업그레이드하는 작업 순서 만들기](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system)를 참조하세요.

    아키텍처 및 언어 값은 다음 단계에서 만들 작업 순서 단계 조건과 일치시켜 운영 체제 업그레이드 패키지를 사전 캐시할지 여부를 확인하는 데 사용됩니다.
2. 다양한 언어 및 아키텍처에 대한 조건부 단계를 사용하여 작업 순서를 만듭니다. 예를 들어 영어 버전의 경우 다음과 같은 단계를 만들 수 있습니다.

    ![사전 캐시 속성](media/precacheproperties2.png)

    ![사전 캐시 옵션](media/precacheoptions2.png)  

3. 작업 순서를 배포합니다. 사전 캐시 기능에 대해 다음을 구성합니다.
    - **일반** 탭에서 **이 작업 순서에 대한 콘텐츠 사전 다운로드**를 선택합니다.
    - **배포 설정** 탭에서 **목적**에 **사용 가능**을 지정하여 작업 순서를 구성합니다. **필수** 배포를 만드는 경우에는 사전 캐시 기능이 작동하지 않습니다.
    - **일정** 탭에서 **이 배포를 사용할 수 있는 시기 예약** 설정에 대해 배포가 사용자에게 제공되기 전에 해당 콘텐츠를 사전 캐시할 충분한 시간을 클라이언트에 제공하는 미래 시간을 선택합니다. 예를 들어 콘텐츠를 사전 캐시하기에 충분한 시간을 허용하기 위해 사용 가능한 시간을 3시간 후로 설정할 수 있습니다.  
    - **배포 지점** 탭에서 **배포 옵션** 설정을 구성합니다. 사용자가 설치를 시작하기 전에 클라이언트에서 콘텐츠가 사전 캐시되지 않은 경우 이러한 설정이 사용됩니다.


### <a name="user-experience"></a>사용자 환경
- 클라이언트가 배포 정책을 받으면 콘텐츠 사전 캐시를 시작합니다. 여기에는 참조된 모든 콘텐츠(다른 패키지 형식) 및 작업 순서에서 설정한 조건에 따라 클라이언트와 일치하는 운영 체제 업그레이드 패키지만 포함됩니다.
- 배포가 사용자에게 제공되면(배포의 **일정** 탭에서 설정) 사용자에게 배포를 알리는 알림이 표시되고 소프트웨어 센터에 배포가 표시됩니다. 사용자가 소프트웨어 센터로 이동한 다음 **설치**를 클릭하여 설치를 시작합니다.
- 콘텐츠가 완전히 사전 캐시되지 않은 경우 배포의 **배포 옵션** 탭에서 지정된 설정을 사용합니다. 클라이언트가 콘텐츠를 사전 캐시하기에 충분한 시간이 있도록 배포를 만든 시간과 배포가 사용자에게 제공되는 시간 사이에 충분한 간격을 두는 것이 좋습니다.


## <a name="see-also"></a>참고 항목
[System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)
