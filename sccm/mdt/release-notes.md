---
title: MDT 릴리스 정보
description: 지원되는 플랫폼, 필수 구성 요소 및 Microsoft Deployment Toolkit의 제한 사항을 이해합니다.
ms.date: 06/04/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 6e32ce6d-585d-4801-a345-ff0f6f2d90ad
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7cb287a17322af8069708268a18d638bd04dddcf
ms.sourcegitcommit: 10b3a571e2a822bbd7b58a25840ee1e6f703a7a2
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814283"
---
# <a name="microsoft-deployment-toolkit-release-notes"></a>Microsoft Deployment Toolkit 릴리스 정보  

이 문서에서는 최신 릴리스의 MDT(Microsoft Deployment Toolkit)에 대해 자세히 설명합니다. 이러한 세부 정보는 지원되는 플랫폼, 필수 구성 요소 및 모든 제한 사항을 포함합니다. MDT 버전 개념, 특징 및 기능에 익숙하다고 가정합니다.



## <a name="latest-release"></a>최신 릴리스

**MDT 빌드 8450**은 [Microsoft 다운로드 센터](https://aka.ms/mdtdownload)에서 사용할 수 있는 최신 버전입니다. 

이 업데이트는 Windows 10 버전 1709용 Windows ADK(평가 및 배포 키트)에 대한 지원을 시작합니다. 

***업데이트***: 2018년 5월 기준으로 이 빌드는 Windows 10 버전 1803도 지원합니다.

자세한 내용은 [지원되는 플랫폼](#supported-platforms) 섹션을 참조하십시오.


### <a name="significant-changes"></a>중요한 변경
이 빌드의 MDT에서 주요 변경 사항에 대한 요약입니다.

#### <a name="supported-configuration-updates"></a>지원되는 구성 업데이트
- Windows 10 버전 1709용 Windows ADK
- Windows 10 버전 1709
- Configuration Manager 버전 1710

#### <a name="quality-updates"></a>품질 업데이트
다음은 이 릴리스의 버그 수정 제목입니다.
- Win10 사이드로드된 앱 종속성 및 라이선스 설치 안 됨
- CaptureOnly 작업 시퀀스는 이미지 캡처를 허용하지 않음
- MDT 작업 순서를 시작할 때 수신된 오류: 잘못된 DeploymentType 값 ""이 지정됐습니다. 배포가 진행되지 않음
- ZTIMoveStateStore는 이동하지 못하게 하는 잘못된 위치에서 상태 저장 폴더를 찾음
- xml에는 원하지 않는 동작을 일으키는 단순 오타가 포함됨
- 설치 역할 및 기능은 Windows Server 2016 IIS 관리 콘솔 기능에 대해 작동하지 않음
- 업그레이드 작업 순서에서 OS 이미지 찾아보기는 폴더를 사용하는 경우 작동하지 않음
- MDT 도구는 TPM을 기능 제한 상태로 부적절하게 프로비전합니다. 자세한 내용은 [KB 4018657](https://support.microsoft.com/help/4018657/tpm-is-in-reduced-functionality-mode-after-successful-deployment-of-wi)을 참조하세요.
- ZTIGather 섀시 유형 검색 논리로 업데이트
- OS 단계 업그레이드는 SetupComplete.cmd를 남겨 두어 이후 배포를 중단시킴
- 일부 하드웨어의 Windows 10 ADK 1607 이상 UEFI 부팅 문제
- 업데이트된 Configuration Manager 작업 시퀀스 바이너리 포함



## <a name="supported-platforms"></a>지원되는 플랫폼

MDT 릴리스는 더 이상 연도나 업데이트 버전으로 태그가 지정되지 않습니다. 이제 **Microsoft Deployment Toolkit**만으로 현재 분기의 Windows 10 및 Configuration Manager에 더 잘 맞추어 조정하고 브랜딩 및 릴리스 프로세스를 단순화합니다. 빌드 번호는 각 릴리스를 구분하는데 사용됩니다. 예를 들어 다운로드할 수 있는 최신 빌드는 8450입니다.

릴리스 일정이 미리 결정된 Configuration Manager와 달리 MDT는 새 버전의 Windows 10, Windows ADK 또는 Configuration Manager 현재 분기를 지원하려면 필요에 따라 릴리스합니다. 이러한 구성 요소와 관련해 알려진 모든 문제는 필요에 따라 이 문서에 문서화됩니다.

다음 OS 버전은 MDT 배포에 대해 지원됩니다.
- Windows 10 버전 1803
- Windows 10 버전 1709
- Windows 10의 기타 [지원되는 버전](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet)
- Windows 8.1
- Windows 7
- Windows Server 2016
- Windows Server 2012 R2
- Windows Server 2012
- Windows Server 2008 R2



## <a name="prerequisites"></a>필수 구성 요소

MDT는 Windows에 포함된 다음 구성 요소를 필요로 합니다.
- Microsoft .NET Framework 4.0
- Windows PowerShell 버전 3.0

[Windows 10용 Windows ADK](https://docs.microsoft.com/windows-hardware/get-started/adk-install) 최신 버전을 사용합니다. 

> [!Note]  
> 배포하는 Windows 버전과 일치하는 Windows ADK를 사용하는 것이 좋습니다. 예를 들어 Windows 10 버전 1703을 배포할 때는 Windows 10용 Windows ADK 버전 1703을 사용합니다. Windows ADK 구성 요소 지원 가능성에 대한 자세한 내용은 [DISM 지원 플랫폼](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) 및 [USMT 요구 사항](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1)을 참조하세요.

ZTI 및 UDI 시나리오에 대해 MDT와 Configuration Manager를 통합할 때 최신 버전의 Configuration Manager 현재 분기를 사용합니다.



## <a name="upgrading-mdt"></a>MDT 업그레이드

MDT 설치 프로세스에서는 동일한 컴퓨터에 설치된 MDT의 기존 모든 인스턴스를 제거합니다. 기존 배포 공유, 배포 지점 및 데이터베이스는 이 프로세스 동안 유지됩니다. 설치가 완료되면 업그레이드해야 합니다.

현재 릴리스의 MDT는 다음 버전의 MDT부터 업그레이드를 지원합니다.
- MDT 빌드 8443

> [!Tip]  
> 업그레이드를 시도하기 전에 기존 MDT 인프라의 백업을 만듭니다.

### <a name="lti"></a>LTI
MDT를 설치한 후 배포 Workbench의 배포 공유 노드에서 **배포 공유 마법사 열기**를 실행하여 기존 배포 공유를 업그레이드합니다. 기존 배포 공유 디렉터리에 경로를 지정한 다음, **업그레이드** 확인란을 선택합니다. 또한 이 프로세스는 기존 네트워크 배포 공유 및 미디어 배포 공유를 업그레이드하므로 해당 공유에 액세스할 수 있어야 합니다. 사용 중인 파일은 업그레이드 문제를 일으킬 수 있기 때문에 배포를 수행하는 동안은 이 업그레이드를 수행하지 마십시오.

### <a name="zti"></a>ZTI
Configuration Manager에 있는 기존 MDT 작업 순서는 MDT의 설치 과정 동안 수정되지 않습니다. 아무 문제 없이 작업을 계속해야 합니다. 이러한 작업 순서를 업그레이드하기 위해 아무런 메커니즘도 제공되지 않습니다. 새로운 MDT 기능 중 하나를 사용하려는 경우 Configuration Manager에서 새 MDT 통합 작업 순서를 만듭니다.

업그레이드 프로세스가 완료된 경우:  

- 업그레이드 후 **ConfigMgr 통합 마법사 구성**을 실행합니다. 새 구성 요소를 등록하고 업데이트된 ZTI 작업 순서 템플릿을 설치합니다.  

- 만든 새 ZTI 작업 순서에 대한 새 **MDT(Microsoft Deployment Toolkit) 파일** 패키지를 만듭니다. 업그레이드 전에 만든 모든 ZTI 작업 순서에 대한 기존 MDT(Microsoft Deployment Toolkit) 파일 패키지를 사용할 수 있지만 새 ZTI 작업 순서에 대한 새 MDT 파일 패키지를 만들어야 합니다.



<!--
## Known issues
-->



## <a name="frequently-asked-questions"></a>질문과 대답

#### <a name="whats-the-mdt-support-life-cycle"></a>MDT 지원 수명 주기란?  
자세한 내용은 [Microsoft Deployment Toolkit 지원 수명 주기](https://support.microsoft.com/help/2872000/microsoft-deployment-toolkit-support-life-cycle)를 참조합니다.

#### <a name="is-this-release-only-supported-with-windows-10-windows-adk-or-configuration-manager-version-x"></a>이 릴리스는 Windows 10, Windows ADK 또는 Configuration Manager 버전 *X*에서만 지원됩니까?
기본적으로 위에 나열된 구성으로 이 빌드의 MDT를 테스트했습니다. 알려진 명시적 문제가 없으면 위의 구성 외의 모든 것이 여전히 작동할 확률이 높습니다. 명시적으로 다른 조합을 테스트하지 않았기 때문에 마일리지가 달라질 수 있습니다.

#### <a name="how-do-i-get-help-with-mdt"></a>MDT에서 어떻게 도움을 받습니까?
다음 방법 중 하나를 사용하여 MDT에서 도움을 받습니다(지정된 우선 순위 대로).

1. [MDT 포럼](https://social.technet.microsoft.com/Forums/en/home?forum=mdt)에 게시합니다. 커뮤니티의 MVP 및 다른 것이 게시물을 감시하고 응답합니다. 아마도 도움을 얻을 수 있는 가장 효율적인 방법입니다.
2. Microsoft 지원에 문의하십시오. 지원 사례를 시작하고 일부 전문가의 도움을 받으세요.
3. 지속적으로 문제를 재현하고 제품 버그라고 생각하는 경우 Windows 10 [피드백 허브](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)에 이를 제출합니다. 제품 팀은 보고된 모든 것을 조사합니다. 피드백을 제출하는 경우 **엔터프라이즈 관리** 범주 및 **OS 배포** 하위 범주를 사용합니다. 이 분류는 피드백을 분류해 MDT 팀에 라우팅하는 데 도움이 됩니다.
     - 피드백 허브는 제품에 대한 제안(디자인 변경 요청 또는 DCR)을 제출하는 데 사용될 수 있습니다.
     - 이전에 연결을 통해 피드백을 제출한 경우 피드백 허브에서 다시 제출할 필요가 없습니다.