---
title: SCAP(Security Content Automation Protocol) 확장 정보
titleSuffix: Configuraton Manager
description: SCAP(Security Content Automation Protocol) 확장에 대해 알아보기
ms.date: 03/27/2018
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: a315489d-5e12-46d6-903e-3a35235b72c5
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: noindex,nofollow
ms.openlocfilehash: 18463e4f87c60135bdc29d0f7ce4cb2f80a0eea7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="about-the-security-content-automation-protocol-scap-extensions"></a>SCAP(Security Content Automation Protocol) 확장 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

> [!Tip]  
> 이 기능은 기술 미리 보기 버전 1803에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 도입되었습니다. SCAP 확장의 이 시험판 버전은 현재 지원되는 모든 버전의 Configuration Manager 현재 분기 및 LTSB 1606에 설치할 수 있습니다. 설치 파일은 1803 미리 보기부터 cd.latest\SMSSETUP\TOOLS\ConfigMgrSCAPExtension\ConfigMgrExtensionsForSCAP.msi에 있습니다. 

Microsoft System Center Configuration Manager용 SCAP 확장을 사용하면 네트워크 환경을 분석하여 SCAP(Security Content Automation Protocol) 준수 여부를 평가할 수 있습니다. SCAP는 미국 NIST(National Institute of Standards and Technology)에서 정의 및 유지 관리합니다.

Microsoft System Center Configuration Manager용 SCAP 확장은 Microsoft System Center Configuration Manager의 준수 설정 기능을 사용하여 환경 내의 컴퓨터를 검색한 다음 USGCB(United States Government Configuration Baseline)의 요구 사항에 따라 준수 수준을 문서화합니다.

Configuration Manager는 이 확장을 통해 SCAP(Security Content Automation Protocol) 데이터 스트림을 사용하고, 시스템에서 준수를 평가하고, SCAP 형식으로 보고서 결과를 생성할 수 있습니다. 조직에서는 기존 Configuration Manager 인프라를 사용하여 관리 대상 컴퓨터가 이 연방 준수 요구 사항을 충족하는지 확인할 수 있으며, NIST(National Institute of Standards and Technology) 및 미국 OMB(Office of Management and Budget)의 필수 USGCB 보고서를 생성할 수 있습니다.

이 가이드에서는 System Center Configuration Manager 인프라에서 SCAP 확장을 설치, 구성 및 실행하는 데 도움이 되는 정보를 제공합니다.



# <a name="what39s-new-in-scap-extensions-prerelease-for-microsoft-system-center-configuration-manager"></a>Microsoft System Center Configuration Manager용 SCAP 확장 시험판의 새로운 기능

이 섹션에서는 최신 버전의 새로운 기능을 알아봅니다.

System Center Configuration Manager용 SCAP 확장 시험판:

- SCAP 콘텐츠를 System Center Configuration Manager 현재 분기에 대한 준수 설정 기준으로 완전히 변환할 수 있는 Configuration Manager 콘솔 확장이 포함되어 있습니다.
- SCAP 버전 1.2를 지원하며 이전 버전인 SCAP 버전 1.1 및 1.0과 호환됩니다.


  - XCCDF(Extensible Configuration Checklist Description Format) 버전 1.2를 지원합니다.
  - OVAL(Open Vulnerability and Assessment Language) 버전을 5.10까지 지원합니다.
  - ARF(Asset Reporting Format) 1.1 보고서 생성을 지원합니다.
  - CPE(Common Platform Enumeration) 2.3을 지원합니다.
  - CVE(Common Vulnerabilities and Exposures)를 지원합니다.
  - CCE(Supports Common Configuration Enumeration) 버전 5를 지원합니다.
  - USGCB Internet Explorer 8, USGCB Windows 7 및 USGCB Windows 7 방화벽을 지원합니다.

- 구성 기준으로 변환하기 위해 SCAP 1.2/1.1/1.0 및 OVAL 콘텐츠를 가져오는 UI 마법사가 포함되어 있습니다.


  - SCAP 원본 데이터 스트림 및 XCCDF 벤치마크와 프로필을 변환용으로 선택할 수 있습니다.

- 구성 평가 결과를 SCAP 형식 XML 보고서로 내보내는 UI 마법사가 포함되어 있습니다.


  - 기준을 생성하는 데 사용된 원본 파일, SCAP 데이터 스트림, XCCDF 벤치마크 및 XCCDF 프로필을 표시합니다.
  - LASR(Cyberscope Lightweight Asset Summary Results) 보고서 생성을 지원합니다.

- 구성 기준 배포를 기반으로 SCAP 보고서 생성을 지원합니다. XCCDF 규칙 준수뿐만 아니라 클라이언트 준수를 시각화하는 새 대시보드가 포함되어 있습니다. 대시보드는 검색 및 필터링이 가능한 보다 자세한 보고서로 드릴스루하는 기능을 지원합니다.
- OVAL 테스트에서 변환된 여러 가지 구성 항목의 성능을 향상시켜 보다 빠른 평가가 가능하게 합니다.

- Windows 10 DISA v1r3 콘텐츠에서 발견된 여러 문제를 해결합니다.

# <a name="scap-extensions-for-microsoft-system-center-configuration-manager-deployment-process"></a>Microsoft System Center Configuration Manager용 SCAP 확장 배포 프로세스

이 가이드에서는 Microsoft System Center Configuration Manager용 SCAP 확장을 사용하여 SCAP 준수 분석/평가/보고를 수행하는 방법을 설명합니다. 다음에는 수행 절차가 간략하게 요약되어 있습니다.

- 확장을 활용할 수 있도록 필수 구성 요소 인프라 준비
- Microsoft System Center Configuration Manager용 SCAP 확장을 설치 및 구성
- [NVD(National Vulnerability Database)](http://nvd.nist.gov)에서 SCAP 데이터 스트림 파일을 다운로드, 설치 및 구성합니다.
- 명령줄 Microsoft.Sces.ScapToDcm.exe 도구를 사용하는 캐비닛(.cab) 파일 **또는** 가져오기 마법사를 사용하여 SCAP 데이터 스트림 파일을 System Center Configuration Manager 준수 설정 기준으로 직접 변환하고 가져옵니다.
- 내보내기 마법사 또는 명령줄 Microsoft.Sces.DcmToScap.exe 도구를 사용하여 준수 결과를 SCAP 형식으로 내보냅니다.

# <a name="terms"></a>용어

**OVAL ID:** OVAL ID의 형식을 따르는 특정 OVAL 정의에 대한 식별자입니다.

**SCAP 결과 데이터 스트림:** 출력(결과) 콘텐츠를 보유하는 SCAP 구성 요소 간의 참조 매핑과 SCAP 구성 요소의 번들입니다.

**SCAP 원본 데이터 스트림:** 입력(원본) 콘텐츠를 보유하는 SCAP 구성 요소 간의 참조 매핑과 SCAP 구성 요소의 번들입니다.

# <a name="prepare-the-prerequisite-infrastructure"></a>필수 인프라 준비

Microsoft System Center Configuration Manager용 SCAP 확장을 활용하려면 다음의 소프트웨어 및 하드웨어 요구 사항이 충족되는지 확인합니다.

## <a name="software-requirements"></a>소프트웨어 요구 사항

Microsoft System Center Configuration Manager용 SCAP 확장을 설치, 구성 및 실행하려면 다음 소프트웨어가 설치된 컴퓨터가 필요합니다

- [지원되는 버전](/sccm/core/servers/manage/current-branch-versions-supported)의 System Center Configuration Manager 현재 분기 콘솔입니다.
- System Center Configuration Manager 콘솔과 호환되는 운영 체제입니다. 호환되는 운영 체제 목록은 [System Center Configuration Manager 콘솔에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-consoles) 아티클을 참조하세요.

SCAP 확장을 실행하는 컴퓨터 외에 다음 항목도 필요합니다.

- System Center Configuration Manager의 현재 분기 인프라 Configuration Manager 배포 요구 사항에 대한 자세한 내용은 [Configuration Manager의 지원되는 구성](/sccm/core/plan-design/configs/supported-configurations) 아티클을 참조하세요.

SCAP 호환성을 평가하려는 컴퓨터에는 다음 소프트웨어 및 구성이 필요합니다.

- Configuration Manager 클라이언트에서 호환 및 설정 관리 구성 요소를 사용하도록 설정해야 합니다.
- Windows PowerShell 2.0 이상을 설치해야 합니다.
- Configuration Manager PowerShell 실행 정책을 **무시**로 설정해야 합니다. 자세한 내용은 [PowerShell 실행 정책](/sccm/core/clients/deploy/about-client-settings#computer-agent) 아티클을 참조하세요.
- 다음 운영 체제 중 하나
  - Windows 7 릴리스 버전 또는 SP1(32비트 또는 64비트)이 필요합니다.
  - Windows 10, 32비트 또는 64비트
  - Windows Server 2012 R2

## <a name="hardware-requirements"></a>하드웨어 요구 사항

최소 시스템 요구 사항은 여기에 나와 있습니다.

[Configuration Manager의 하드웨어 구성 계획](/sccm/core/plan-design/configs/recommended-hardware)



## <a name="accessibility-features"></a>접근성 기능

System Center Configuration Manager용 SCAP 확장에는 Windows의 내게 필요한 옵션 기능과 도구를 활용할 수 있는 Windows 명령줄 도구가 포함되어 있습니다.

- 이 사용자 가이드에서는 Microsoft.Sces.ScapToDcm.exe 및 Microsoft.Sces.DcmToScap.exe의 명령줄 매개 변수에 대해 설명합니다.
- -help 및 -? 를 입력하면 도구 사용법이 화면에 출력되며, 이 화면에서 화면 읽기 프로그램 및 기타 보조 기술이 해당 정보를 사용할 수 있습니다.
- Windows [접근성](http://windows.microsoft.com/windows/help/accessibility)

또한 SCAP 확장은 System Center Configuration Manager의 기능을 사용합니다.  Configuration Manager에는 장애가 있는 사용자가 제품을 더 쉽게 사용할 수 있도록 하는 기능이 포함되어 있습니다.

- [System Center Configuration Manager의 접근성 기능](/sccm/core/understand/accessibility-features)

Microsoft의 접근성 제품 및 서비스에 대한 일반적인 내용은 [Microsoft Accessibility 웹 사이트](http://go.microsoft.com/fwlink/p/?LinkId=9212)를 참조하세요.

## <a name="next-step"></a>다음 단계
> [!div class="nextstepaction"]
> [SCAP 확장 설치 및 구성](/sccm/compliance/plan-design/scap/install-configure-scap)
