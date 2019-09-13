---
title: 비운영 체제 배포에 대한 작업 순서 만들기
titleSuffix: Configuration Manager
description: 소프트웨어 배포 또는 작업 자동화와 같이 OS 배포용이 아닌 작업 순서 만들기
ms.date: 05/03/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d3cd923348b3ac6dfd6b2da652efc0a56ad9b787
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70888462"
---
# <a name="create-a-task-sequence-for-non-os-deployments"></a>비운영 체제 배포에 대한 작업 순서 만들기

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 작업 순서는 사용자 환경 내에서 다양한 작업을 자동화하는 데 사용됩니다. 이러한 작업은 주로 운영 체제 배포를 위해 설계되고 테스트됩니다. Configuration Manager에는 다음과 같은 시나리오에 사용하는 기본 기술에 해당하는 여러 다른 기능이 있습니다.

- [애플리케이션 설치](/sccm/apps/understand/introduction-to-application-management)
- [소프트웨어 업데이트 설치](/sccm/sum/understand/software-updates-introduction)
- [구성 설정](/sccm/compliance/understand/ensure-device-compliance)

또한 [Orchestrator](https://docs.microsoft.com/system-center/orchestrator/) , [Service Management Automation](https://docs.microsoft.com/system-center/sma/) 등 기타 Microsoft System Center 자동화 기술도 고려해야 합니다.  

작업 순서의 장점은 유연성과 사용 방법에 있습니다. 작업 순서를 통해 클라이언트 설정을 구성하고, 소프트웨어를 배포하고, 드라이버를 업데이트하고, 사용자 환경을 편집하고, OS 배포와는 관련 없는 기타 작업을 수행할 수 있습니다. 개수와 상관없이 작업을 추가하는 사용자 지정 작업 순서를 만들 수 있습니다. Configuration Manager에서 비 OS 배포에 대한 사용자 지정 작업 순서 사용이 지원됩니다. 그러나 작업 순서로 인해 원치 않거나 일관성이 없는 결과가 발생하는 경우 작업을 간소화하는 방법을 살펴보세요.

- 보다 더 간단한 단계 사용
- 작업을 여러 작업 순서 간에 분산
- 작업 순서를 만들고 테스트하는 단계별 방법을 수행

비 OS 배포 사용자 지정 작업 순서에 사용할 수 있는 단계는 다음과 같습니다.  

- [준비 확인](/sccm/osd/understand/task-sequence-steps#BKMK_CheckReadiness)  

- [네트워크 폴더에 연결](/sccm/osd/understand/task-sequence-steps#BKMK_ConnectToNetworkFolder)  

- [패키지 콘텐츠 다운로드](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent)  

- [애플리케이션 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallApplication)  

- [패키지 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallPackage)  

- [소프트웨어 업데이트 설치](/sccm/osd/understand/task-sequence-steps#BKMK_InstallSoftwareUpdates)  

- [컴퓨터 다시 시작](/sccm/osd/understand/task-sequence-steps#BKMK_RestartComputer)  

- [명령줄 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine)  

- [PowerShell 스크립트 실행](/sccm/osd/understand/task-sequence-steps#BKMK_RunPowerShellScript)  

- [작업 순서 실행](/sccm/osd/understand/task-sequence-steps#child-task-sequence)  

- [동적 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetDynamicVariables)  

- [작업 순서 변수 설정](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable)  
