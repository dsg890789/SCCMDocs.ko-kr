---
title: 비운영 체제 배포에 대한 작업 순서 만들기
titleSuffix: Configuration Manager
description: 소프트웨어 배포, 드라이버 업데이트, 사용자 상태 편집 등 운영 체제 배포와 관련이 없는 작업 순서를 만듭니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 42c56b048afe768cd04cd5c91d659535ad5ffc9e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-task-sequence-for-non-operating-system-deployments-with-system-center-configuration-manager"></a>System Center Configuration Manager와 비운영 체제 배포에 대한 작업 순서 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 작업 순서는 사용자 환경 내에서 다양한 작업을 자동화하는 데 사용됩니다. 이러한 작업은 주로 운영 체제 배포를 위해 설계되고 테스트됩니다.  Configuration Manager에는 [응용 프로그램 설치](../../apps/understand/introduction-to-application-management.md), [소프트웨어 업데이트 설치](../../sum/understand/software-updates-introduction.md), [구성 설정](../../compliance/understand/ensure-device-compliance.md), 사용자 지정 자동화 등 시나리오에 사용하는 기본 기술인 기타 많은 기능이 있습니다. 또한 [Orchestrator](https://technet.microsoft.com/library/hh237242.aspx) , [서비스 관리 자동화](https://technet.microsoft.com/library/dn469260.aspx) 등 고려해야 하는 기타 Microsoft System Center 자동화 기술도 있습니다.  

작업 순서의 장점은 유연성에 있으며, 이러한 작업 순서를 사용하여 운영 체제 배포와 독립적으로 클라이언트 설정 구성, 소프트웨어 배포, 드라이버 업데이트, 사용자 환경 편집 및 기타 작업을 수행할 수 있습니다. 개수와 상관없이 작업을 추가하는 사용자 지정 작업 순서를 만들 수 있습니다. Configuration Manager에서 비운영 체제 배포에 대한 사용자 지정 작업 순서 사용이 지원됩니다. 그러나 작업 순서로 인해 원치 않거나 일관성이 없는 결과가 발생하는 경우 작업을 간소화하는 방법을 살펴보세요. 여러 작업 순서로 작업을 나누어 더 간단한 단계를 사용하거나 작업 순서를 만들고 테스트하는 단계별 방법을 사용하면 됩니다.

 비운영 체제 배포 사용자 지정 작업 순서에 사용할 수 있는 단계는 다음과 같습니다.  

-   [준비 확인](../understand/task-sequence-steps.md#BKMK_CheckReadiness)  

-   [네트워크 폴더에 연결](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder)  

-   [패키지 콘텐츠 다운로드](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent)  

-   [응용 프로그램 설치](../understand/task-sequence-steps.md#BKMK_InstallApplication)  

-   [패키지 설치](../understand/task-sequence-steps.md#BKMK_InstallPackage)  

-   [소프트웨어 업데이트 설치](../understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates)  

-   [컴퓨터 다시 시작](../understand/task-sequence-steps.md#BKMK_RestartComputer)   

-   [명령줄 실행](../understand/task-sequence-steps.md#BKMK_RunCommandLine)  

-   [PowerShell 스크립트 실행](../understand/task-sequence-steps.md#BKMK_RunPowerShellScript)  

-   [동적 변수 설정](../understand/task-sequence-steps.md#BKMK_SetDynamicVariables)  

-   [작업 순서 변수 설정](../understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable)  

## <a name="next-steps"></a>다음 단계 
[작업 순서 배포](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS)
