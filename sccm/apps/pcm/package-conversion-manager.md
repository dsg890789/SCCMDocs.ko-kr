---
title: Package Conversion Manager
titleSuffix: Configuration Manager
description: Configuration Manager에서 패키지를 응용 프로그램으로 변환하는 Package Conversion Manager에 대해 알아봅니다.
ms.date: 08/24/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: f053fa73-c553-4522-a6b9-f885f23fe57c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 41dd6ad6f8a0292fdb16a0d727665b17e038f87b
ms.sourcegitcommit: 1439817f1309658b31008d7bafaab32fc5ef8789
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52820044"
---
# <a name="package-conversion-manager"></a>Package Conversion Manager

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1357861-->

버전 1806부터 Package Conversion Manager가 Configuration Manager 레거시 패키지를 응용 프로그램으로 변환하는 데 도움을 줍니다. 응용 프로그램에는 종속성, 요구 사항 규칙, 검색 방법 및 사용자 장치 선호도와 같은 추가 혜택이 있습니다.

> [!Tip]  
> 이 기능은 버전 1806에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 소개되었습니다. 버전 1810 버전부터 이 기능은 더 이상 시험판 기능이 아닙니다.  


Configuration Manager 응용 프로그램에는 클라이언트 장치에 배포할 파일 및 프로그램이 포함되어 있습니다. 그러나 레거시 패키지 및 프로그램과 달리 응용 프로그램은 사용자 중심 기능을 추가로 제공합니다. 예를 들어 응용 프로그램에는 소프트웨어 패키지, 가상 응용 프로그램 패키지 또는 모바일 장치용 응용 프로그램 버전 등의 로컬 설치를 위한 배포 유형이 포함될 수 있습니다.

자세한 내용은 다음 아티클을 참조하세요. 
- [응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management)  
- [패키지 및 프로그램](/sccm/apps/deploy-use/packages-and-programs)  

> [!Important]  
> 이전 버전의 Package Conversion Manager를 전에 설치한 경우 먼저 이를 제거한 후 사이트를 업그레이드합니다. 이 통합 버전이 설치를 요구하지는 않지만 기존 버전과 충돌할 수 있습니다.  

이 통합 버전의 Package Conversion Manager는 Configuration Manager 현재 분기 사이트의 패키지에서 작동합니다. 독립 실행형 도구가 아닙니다. 이전 버전의 Configuration Manager에 패키지 및 프로그램이 있는 경우 먼저 패키지를 현재 분기 사이트로 마이그레이션합니다. 자세한 내용은 [계층 구조 간에 데이터 마이그레이션](/sccm/core/migration/migrate-data-between-hierarchies)을 참조하세요.



## <a name="planning"></a>계획

패키지를 응용 프로그램으로 변환하려면 먼저 플랜을 수립합니다. 다음 프로세스는 플랜의 예입니다.

- [자세한 패키지 변환 플랜 정의](#bkmk_define)  

- [변환용 패키지 선택 및 준비](#bkmk_prepare)  

- [테스트 패키지 선택](#bkmk_test)  

- [패키지 분석, 조사 및 변환](#bkmk_analyze)  

- [응용 프로그램 테스트 및 배포](#bkmk_deploy)  


### <a name="bkmk_define"></a> 자세한 패키지 변환 플랜 정의

이 섹션에서는 다음 두 개의 샘플 패키지 변환 플랜에 대해 설명합니다.  

- [리소스가 많은 테스트 환경](#bkmk_define-high): 테스트 환경이 프로덕션 환경과 완전히 동일하게 리소스, 권한 및 아키텍처를 갖추고 있습니다.  

- [리소스가 제한된 테스트 환경](#bkmk_define-limited): 테스트 환경이 프로덕션 환경과 동일하지 않습니다.  

사용자 환경에 고유한 다른 문제에 맞게 필요한 대로 이러한 플랜을 조정하세요.

#### <a name="bkmk_define-high"></a> 리소스가 많은 테스트 환경용 샘플 플랜

테스트 환경이 프로덕션 환경과 유사한 리소스, 권한 및 아키텍처를 갖추고 있습니다. 테스트 환경을 사용하여 모든 패키지를 효율적으로 분석하고 변환한 후 모든 Configuration Manager 응용 프로그램을 테스트합니다. 해당 작업을 완료한 후 프로덕션 환경으로 전송하세요. 

패키지 변환 플랜의 단계는 다음과 같습니다.  

1.  변환하려는 패키지를 선택합니다.  

2.  변환할 패키지를 테스트 환경으로 마이그레이션합니다.  

3.  변환용으로 패키지를 준비합니다.  

4.  테스트 패키지를 선택합니다.  

5.  테스트 패키지를 분석, 조사 및 변환합니다.  

6.  변환된 응용 프로그램을 테스트합니다.  

7.  테스트용이 아닌 나머지 패키지를 분석 및 변환합니다.  

8.  테스트 환경에서 응용 프로그램을 내보냅니다. 해당 응용 프로그램을 프로덕션 환경으로 가져옵니다.  

#### <a name="bkmk_define-limited"></a> 리소스가 제한되는 테스트 환경용 샘플 플랜

테스트 환경이 프로덕션 환경과 유사한 리소스, 권한 및 아키텍처를 갖추고 있지 않습니다. 일부 패키지는 분석, 테스트 및 변환할 수 없습니다. 이 시나리오에서는 테스트 패키지만 분석, 조사, 변환 및 테스트합니다. 그런 다음, 나머지 패키지를 프로덕션 환경으로 마이그레이션하여 분석 및 변환합니다. 

패키지 변환 플랜의 단계는 다음과 같습니다.

1.  변환하려는 패키지를 선택합니다.  

2.  테스트 패키지를 선택합니다.  

3.  테스트 패키지를 테스트 환경으로 마이그레이션합니다.  

4.  변환용으로 테스트 패키지를 준비합니다.  

5.  테스트 패키지를 분석, 조사 및 변환합니다.  

6.  변환된 응용 프로그램을 테스트합니다.  

7.  테스트 환경에서 테스트 응용 프로그램을 내보냅니다. 그런 다음, 해당 응용 프로그램을 프로덕션 환경으로 가져옵니다.  

8.  나머지 패키지를 프로덕션 환경으로 마이그레이션하고 변환용으로 준비합니다.  

9.  프로덕션 환경에서 나머지 패키지를 분석, 조사 및 변환합니다.  

10. 나머지 응용 프로그램을 프로덕션 환경으로 릴리스합니다.  


### <a name="bkmk_prepare"></a> 변환용 패키지 선택 및 준비

#### <a name="bkmk_prepare-select"></a> 변환하려는 패키지 선택

모든 패키지가 응용 프로그램으로 변환하기에 적합한 것은 아닙니다. 패키지 변환을 시작하기 전에 변환하지 않을 패키지를 파악합니다. 

응용 프로그램으로 변환하기에 가장 적합한 패키지 유형은 다음과 같이 사용자용 소프트웨어가 포함된 패키지입니다.  

 - Windows Installer 파일(.msi 및 .msu)  

 - Microsoft Application Virtualization(App-V) 프로그램  

 - Windows 실행 파일(.exe)  

응용 프로그램으로 변환하지 않고 패키지로 유지하는 것이 가장 좋은 패키지 유형은 다음과 같습니다.

 - 스크립트 또는 백업 유틸리티와 같은 시스템 유지 관리 도구  

 - 지원되지 않는 소프트웨어 패키지

> [!Tip]  
> 응용 프로그램으로 변환하기에 적합하지 않은 패키지를 파악한 후 Configuration Manager 콘솔의 별도 폴더로 이동합니다. Configuration Manager 콘솔에 패키지 폴더를 만들려면 다음을 수행합니다.  
> - **패키지** 노드를 마우스 오른쪽 단추로 클릭합니다.  
> - **폴더**를 선택한 후 **폴더 만들기**를 선택합니다.  
> - 폴더 이름(예: `Not Converted`)을 입력합니다.  
> - **확인**을 클릭합니다.  

#### <a name="prepare-the-packages-for-conversion"></a>변환용으로 패키지 준비

변환하려는 각 패키지가 다음 조건을 준수하는지 확인합니다.  

 - 원본 파일 위치는 전체 UNC 경로(예: `\\Server\Share\File`)입니다.  

 - Windows Installer 파일은 고유한 제품 코드를 하나만 사용합니다.  


### <a name="bkmk_test"></a> 테스트 패키지 선택

가능하면 테스트 패키지 그룹에 다음 기준을 충족하는 패키지가 포함되어야 합니다.  

 - 준비 상태가 **자동**인 테스트 패키지 하나 이상  

 - 준비 상태가 **수동**인 테스트 패키지 하나 이상  

다음과 같이 테스트 패키지가 코어 패키지여야 가장 바람직합니다.  

 - 사용자가 잘 알고 있는 패키지  

 - 조직에 가장 중요한 패키지  

 - 가장 쉽게 테스트할 수 있는 패키지  

테스트하기 적합한 패키지를 파악합니다. 그런 다음, Configuration Manager 콘솔의 별도 폴더로 이동합니다.


### <a name="bkmk_analyze"></a> 패키지 분석, 조사 및 변환

#### <a name="analyze-packages"></a>패키지 분석

개별 패키지 또는 작은 그룹을 분석하려면 Configuration Manager 콘솔에 통합된 Package Conversion Manager를 사용합니다. 자세한 내용은 [패키지를 분석하고 변환하는 방법](/sccm/apps/pcm/how-to-analyze-and-convert)을 참조하세요.  

> [!NOTE]  
> **모니터링** 작업 영역의 **패키지 변환 상태** 노드를 참조하세요. 분석 및 변환 프로세스에 대한 요약 정보가 표시되어 있습니다.  

#### <a name="investigate-analysis-results"></a>분석 결과 조사

테스트 패키지를 분석한 후에는 준비 상태가 **수동** 또는 **오류**인 패키지를 조사하여 패키지가 이러한 상태로 설정된 이유를 확인합니다. 준비 상태가 **수동** 또는 **오류** 인 경우의 몇 가지 일반적인 원인은 다음과 같습니다.

 - 응용 프로그램 배포 유형에서 검색 방법을 만드는 데 필요한 정보가 패키지에 포함되어 있지 않습니다.  

 - 컬렉션을 글로벌 조건 및 요구 사항으로 변환하는 데 필요한 정보가 패키지에 포함되어 있지 않습니다.  

 - 패키지에 프로그램이 두 개 이상 포함되어 있습니다.  

 - 패키지가 응용 프로그램으로 변환하지 않은 다른 패키지에 종속됩니다.  

자세한 내용은 다음 리소스를 참조하세요.  

- [Package Conversion Manager 오류 메시지에 대한 기술 참조](/sccm/apps/pcm/error-messages)의 오류 메시지 및 수정 사항 검토  

- 로그 파일 **PCMTrace.log** 검토  

- [Package Conversion Manager 문제 해결](/sccm/apps/pcm/troubleshoot-pcm)  

#### <a name="convert-the-packages"></a>패키지 변환

패키지를 변환하는 방법에 대한 자세한 내용은 [패키지를 분석하고 변환하는 방법](/sccm/apps/pcm/how-to-analyze-and-convert)을 참조하세요.

> [!NOTE]  
> **모니터링** 작업 영역의 **패키지 변환 상태** 노드를 참조하세요. 분석 및 변환 프로세스에 대한 요약 정보가 표시되어 있습니다.  


### <a name="bkmk_deploy"></a> 응용 프로그램 테스트 및 배포

자세한 패키지 변환 계획에 따라 테스트 환경이나 프로덕션 환경에서 응용 프로그램을 테스트합니다.



## <a name="recommendations"></a>권장 사항

- **모니터링** 작업 영역의 **패키지 변환 상태** 노드를 사용하세요. 분석 및 변환 프로세스에 대한 요약 정보가 표시되어 있습니다.  

- 래퍼라고도 하는 패키지의 프로그램을 조사합니다. Package Conversion Manager 플러그 인을 사용하여 해당 기능을 동일한 Configuration Manager 기능으로 변환하세요.  

- 변환된 각 응용 프로그램을 프로덕션 환경에 배포하기 전에 철저하게 테스트해야 합니다.  



## <a name="next-steps"></a>다음 단계

[패키지를 분석하고 변환하는 방법](/sccm/apps/pcm/how-to-analyze-and-convert)