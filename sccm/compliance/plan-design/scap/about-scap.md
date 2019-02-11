---
title: SCAP 확장
titleSuffix: Configuration Manager
description: Configuration Manager용 SCAP(Security Content Automation Protocol) 확장에 대해 알아봅니다.
ms.date: 01/30/2019
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: a315489d-5e12-46d6-903e-3a35235b72c5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e42027663f06bff715cb7e9087ececbc421cc495
ms.sourcegitcommit: 013ca76d5a3c07306de7b5bfd985b0289d1be599
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55482455"
---
# <a name="about-the-security-content-automation-protocol-scap-extensions"></a>SCAP(Security Content Automation Protocol) 확장 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager용 SCAP 확장을 사용하면 네트워크 환경을 분석하여 SCAP(Security Content Automation Protocol) 준수 여부를 평가할 수 있습니다. SCAP는 NIST(National Institute of Standards and Technology)에서 정의 및 유지 관리합니다. 자세한 내용은 [SCAP 프로젝트 개요](https://csrc.nist.gov/projects/security-content-automation-protocol)를 참조하세요.

> [!Note]  
> 이 버전의 도구는 버전 1806에서만 사용할 수 있는 시험판 기능입니다. 이 버전은 NIST에서 인증되지 않았습니다. <!--SCCMDocs-pr issue 3323-->
> 
> 인증된 도구가 필요하거나 다른 버전의 Configuration Manager 현재 분기를 사용하는 경우, 다음 버전의 SCAP 확장을 사용하세요.
> - [System Center Configuration Manager의 SCAP 확장 다운로드](https://www.microsoft.com/download/details.aspx?id=48741)
> - [SCAP 확장 버전 3.0 설명서](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/mt228311\(v%3dtechnet.10\))

Configuration Manager용 SCAP 확장은 준수 설정 기능을 사용하여 사용자 환경의 컴퓨터를 먼저 검사합니다. 그런 다음, USGCB(United States Government Configuration Baseline)를 사용하여 준수 수준을 문서화합니다.

Configuration Manager는 이 확장을 통해 SCAP 데이터 스트림을 사용하고, 시스템에서 준수를 평가하고, SCAP 형식으로 보고서 결과를 생성할 수 있습니다. 조직은 기존 Configuration Manager 인프라를 사용하여 관리하는 컴퓨터가 이 연방 준수 요구 사항을 충족하도록 할 수 있습니다. 또한 Configuration Manager를 사용하여 NIST와 미국 OMB(Office of Management and Budget)에 필요한 USGCB 보고서를 생성할 수 있습니다.

이 문서에서는 Configuration Manager 인프라에서 SCAP 확장을 설치, 구성 및 실행하는 데 도움이 되는 정보를 제공합니다.



## <a name="whats-new"></a>새로운 기능

이 버전의 Configuration Manager용 SCEP 확장은 다음 기능을 포함하고 지원합니다.  

- SCAP 콘텐츠를 준수 설정 기준으로 변환하도록 지원하는 Configuration Manager 콘솔 확장.  

- 다음 구성 요소를 포함하는 SCAP 버전 1.2:  

  - XCCDF(Extensible Configuration Checklist Description Format) 버전 1.2
  - OVAL(Open Vulnerability and Assessment Language) 버전 5.10까지
  - ARF(Asset Reporting Format) 1.1 보고서 생성
  - CPE(Common Platform Enumeration) 2.3
  - CVE(Common Vulnerabilities and Exposures)
  - CCE(Common Configuration Enumeration) 버전 5
  - USGCB Internet Explorer 8, USGCB Windows 7 및 USGCB Windows 7 방화벽  

- SCAP 버전 1.1 및 1.0 이전 버전과 호환  

- SCAP 1.2/1.1/1.0 및 OVAL 콘텐츠를 가져와서 구성 기준으로 변환하는 콘솔 마법사  

  - SCAP 원본 데이터 스트림 및 XCCDF 벤치마크와 프로필을 변환용으로 선택할 수 있습니다.

- 구성 평가 결과를 SCAP 형식 XML 보고서로 내보내는 콘솔 마법사  

  - 기준을 생성하는 데 사용된 원본 파일, SCAP 데이터 스트림, XCCDF 벤치마크 및 XCCDF 프로필을 표시합니다.
  - Cyberscope LASR(Lightweight Asset Summary Results) 보고서를 생성합니다.  

- 구성 기준 배포를 기반으로 SCAP 보고서를 생성합니다. 아 구성요소에는 XCCDF 규칙 준수뿐만 아니라 클라이언트 준수를 시각화하는 새 대시보드가 포함되어 있습니다. 대시보드는 검색 및 필터링이 가능한 보다 자세한 보고서로 드릴스루하는 기능을 지원합니다.  

- OVAL 테스트에서 변환된 몇 가지 유형의 구성 항목 성능이 향상되어 보다 빠른 평가가 가능합니다.  

- Windows 10 DISA v1r3 콘텐츠에서 발견된 여러 문제를 해결합니다.  



## <a name="terms"></a>용어

- **OVAL ID**: OVAL ID의 형식을 따르는 특정 OVAL 정의에 대한 식별자입니다.  

- **SCAP 결과 데이터 스트림**: 출력(결과) 콘텐츠를 보유하는 SCAP 구성 요소 간의 참조 매핑과 SCAP 구성 요소의 번들입니다.  

- **SCAP 원본 데이터 스트림**: 입력(원본) 콘텐츠를 보유하는 SCAP 구성 요소 간의 참조 매핑과 SCAP 구성 요소의 번들입니다.



## <a name="deployment-process"></a>배포 프로세스

다음은 전반적인 배포 프로세스에 대한 요약입니다.  

- 확장을 사용하기 위한 [인프라 준비](#bkmk_prepare)  

- Configuration Manager용 [SCAP 확장 설치 및 구성](/sccm/compliance/plan-design/scap/install-configure-scap#bkmk_install)  

- NIST에서 [SCAP 데이터 스트림 파일 다운로드 및 설치](/sccm/compliance/plan-design/scap/install-configure-scap#bkmk_scap-data-stream-files)  

- SCAP 데이터 스크림 파일을 Configuration Manager 준수 설정 기준으로 변환하고 가져오기 다음 두 가지 방법 중 하나를 사용합니다.   

    - Configuration Manager 콘솔에서 내보내기 마법사를 사용하는 [수동 프로세스](/sccm/compliance/plan-design/scap/install-configure-scap#bkmk_convert-and-import)  

    - Microsoft.Sces.ScapToDcm.exe 명령줄 도구를 사용하는 [자동화된 프로세스](/sccm/compliance/plan-design/scap/install-configure-scap#bkmk_auto-convert-and-import)  

- 컬렉션에 구성 기준 [배포](/sccm/compliance/plan-design/scap/deploy-monitor-export#bkmk_deploy)  

- 규정 준수 데이터 [모니터링](/sccm/compliance/plan-design/scap/deploy-monitor-export#bkmk_monitor)  

- 다음 두 가지 방법 중 하나를 사용하여 준수 결과를 SCAP 형식으로 내보냅니다.  

    - 콘솔에서 내보내기 마법사를 사용하는 [수동 프로세스](/sccm/compliance/plan-design/scap/deploy-monitor-export#bkmk_export)  

    - Microsoft.Sces.DcmToScap.exe 명령줄 도구를 사용하는 [자동화된 프로세스](/sccm/compliance/plan-design/scap/deploy-monitor-export#bkmk_auto-export)  



## <a name="bkmk_prepare"></a> 인프라 준비

### <a name="software-requirements"></a>소프트웨어 요구 사항

Configuration Manager용 SCAP 확장을 설치, 구성 및 실행하려면 다음 소프트웨어가 설치된 컴퓨터가 필요합니다

- Configuration Manager 현재 분기 콘솔의 [지원되는 버전](/sccm/core/servers/manage/current-branch-versions-supported)  

- Configuration Manager 콘솔과 호환되는 OS 버전 자세한 내용은 [Configuration Manager 콘솔에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-consoles)를 참조하세요.  

SCAP 확장을 실행하는 컴퓨터 외에 다음 항목도 필요합니다.

- Configuration Manager의 현재 분기 인프라 Configuration Manager 배포 요구 사항에 대한 자세한 내용은 [Configuration Manager의 지원되는 구성](/sccm/core/plan-design/configs/supported-configurations) 아티클을 참조하세요.  

SCAP 호환성을 평가하려는 컴퓨터에는 다음 소프트웨어 및 구성이 필요합니다.

- Configuration Manager 클라이언트  

- Windows PowerShell 2.0 이상을 설치해야 합니다.  

- Configuration Manager PowerShell 실행 정책을 **무시**로 설정해야 합니다. 자세한 내용은 [PowerShell 실행 정책](/sccm/core/clients/deploy/about-client-settings#computer-agent) 아티클을 참조하세요.  

- 다음 운영 체제 중 하나가 필요합니다.  
  - Windows 7 SP1, 32비트 또는 64비트
  - Windows 10, 32비트 또는 64비트
  - Windows Server 2012 R2

### <a name="hardware-requirements"></a>하드웨어 요구 사항

Configuration Manager의 최소 시스템 요구 사항에 대한 자세한 내용은 [Configuration Manager의 하드웨어 구성 계획](/sccm/core/plan-design/configs/recommended-hardware)을 참조하세요.



## <a name="accessibility-features"></a>내게 필요한 옵션 기능

Configuration Manager용 SCAP 확장에는 Windows 명령줄 도구가 포함됩니다. 이러한 도구는 Windows의 내게 필요한 옵션 기능과 도구를 활용할 수 있습니다.

- 명령줄 매개 변수는 Microsoft.Sces.ScapToDcm.exe 및 Microsoft.Sces.DcmToScap.exe에 대해 문서화되어 있습니다. 자세한 내용은 [Microsoft.Sces.ScapToDcm.exe. 명령줄 매개 변수](/sccm/compliance/plan-design/scap/install-configure-scap#microsoftscesscaptodcmexe-command-line-parameters) 및 [Microsoft.Sces.DcmToScap.exe 명령줄 매개 변수](/sccm/compliance/plan-design/scap/import-scap-compliance-settings#microsoftscesdcmtoscapexe-command-line-parameters)를 참조하세요.  

- 각 도구의 명령줄 매개 변수 `-help` 및 `-?`는 사용법을 화면에 인쇄합니다. 이러한 사용 정보는 화면 판독기 및 기타 보조 기술에 사용할 수 있습니다.  

- 자세한 내용은 [Windows 내게 필요한 옵션](http://windows.microsoft.com/windows/help/accessibility)을 참조하세요.

SCAP 확장은 Configuration Manager의 내게 필요한 옵션 기능도 사용합니다. 자세한 내용은 [Configuration Manager의 내게 필요한 옵션 기능](/sccm/core/understand/accessibility-features)을 참조하세요.

Microsoft의 내게 필요한 옵션 제품 및 서비스에 대한 일반적인 내용은 [Microsoft 내게 필요한 옵션 웹 사이트](http://go.microsoft.com/fwlink/p/?LinkId=9212)를 참조하세요.



## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [SCAP 확장 설치 및 구성](/sccm/compliance/plan-design/scap/install-configure-scap)
