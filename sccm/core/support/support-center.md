---
title: 지원 센터
titleSuffix: Configuration Manager
description: 지원 센터를 사용하여 Configuration Manager 클라이언트 문제를 해결합니다.
ms.date: 05/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c631197d-7daa-4faa-9e22-980cd6d604c2
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9246ea46787b1db466b8aca5d8a602617c80e26a
ms.sourcegitcommit: ab9f2a7fb7ea3a0c65808fce2975ab25a670281f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612518"
---
# <a name="support-center-for-configuration-manager"></a>Configuration Manager에 대한 지원 센터

*적용 대상: System Center Configuration Manager(현재 분기)*

<!--1357489-->
1810 버전부터 클라이언트 문제 해결, 실시간 로그 보기, 나중에 분석하기 위해 구성 관리자 클라이언트 컴퓨터의 상태 캡처 등의 작업에 지원 센터를 사용합니다. 지원 센터는 많은 관리자 문제 해결 도구를 통합하는 단일 도구입니다. 



## <a name="about"></a>정보 

지원 센터는 Configuration Manager 클라이언트 컴퓨터의 문제를 해결할 때 발생하는 어려움을 줄이기 위한 것입니다. 이전에 Configuration Manager 클라이언트 문제를 해결할 때는 문제 해결에 도움이 되는 로그 파일 및 기타 정보를 수동으로 수집해야 했습니다. 이 때문에 중요한 로그 파일을 실수로 빼놓아 관련 작업자들에게 문제를 초래하기 쉬웠습니다.

이제 지원 센터를 사용하여 지원 환경을 간소화할 수 있습니다. 이를 통해 다음을 수행할 수 있습니다.

 - Configuration Manager 클라이언트 로그 파일을 포함하는 문제 해결 번들(.zip 파일)를 만듭니다. 그러면 지원 담당자에게 보낼 수 있는 단일 파일을 갖게 됩니다.  

 - Configuration Manager 클라이언트 로그 파일, 인증서, 레지스트리 설정, 디버그 덤프, 클라이언트 정책을 확인합니다.  

 - 인벤토리(ContentSpy 대체), 정책(PolicySpy 대체) 및 클라이언트 캐시에 대한 실시간 진단  


### <a name="support-center-viewer"></a>지원 센터 뷰어

지원 센터에는 지원 담당자가 지원 센터를 사용하여 만든 파일 번들을 여는 데 사용할 수 있는 지원 센터 뷰어가 포함되어 있습니다. 지원 센터의 데이터 수집기는 로컬 또는 원격 Configuration Manager 클라이언트에서 진단 로그를 수집하여 패키지로 만듭니다. 데이터 수집기 번들을 보려면 뷰어 애플리케이션을 사용합니다.


### <a name="support-center-log-file-viewer"></a>지원 센터 로그 파일 뷰어

지원 센터에는 최신 로그 뷰어가 포함되어 있습니다. 이 도구는 CMTrace를 대신하며, 탭 및 도킹 가능한 창을 지원하는 사용자 지정 가능한 인터페이스를 제공합니다. 빠른 프레젠테이션 계층이 있으며 몇 초 안에 대용량 로그 파일을 로드할 수 있습니다.


### <a name="powershell-cmdlets"></a>PowerShell cmdlet

지원 센터는 [Windows PowerShell cmdlet](https://go.microsoft.com/fwlink/?linkid=397830)도 포함합니다. 이 cmdlet을 사용하여 다른 Configuration Manager 클라이언트에 원격 연결하고, 데이터 수집 옵션을 구성하며, 데이터 수집을 시작합니다.



## <a name="prerequisites"></a>필수 구성 요소

지원 센터를 설치한 서버나 클라이언트 컴퓨터에 다음 구성 요소를 설치합니다.

- Configuration Manager에서 지원하는 OS 버전. 자세한 내용은 [지원되는 클라이언트 OS 버전](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)을 참조하세요. 지원 센터는 모바일 장치를 지원하지 않습니다.  

- 지원 센터와 구성 요소를 실행하는 컴퓨터에 .NET Framework 4.5.2가 필요합니다.  



## <a name="install"></a>설치

`cd.latest\SMSSETUP\Tools\SupportCenter\SupportCenterInstaller.msi` 경로에서 사이트 서버의 지원 센터 설치 관리자를 찾습니다.

설치한 후 **Microsoft System Center** 그룹의 시작 메뉴에서 다음 항목을 찾습니다.  
- 지원 센터(ConfigMgrSupportCenter.exe)  
- 지원 센터 로그 파일 뷰어(CMLogViewer.exe)  
- 지원 센터 뷰어(ConfigMgrSupportCenterViewer.exe)  



## <a name="known-issues"></a>알려진 문제 

#### <a name="you-cant-install-the-latest-version-if-an-older-version-is-already-installed"></a>이전 버전이 이미 설치되어 있으면 최신 버전을 설치할 수 없음
<!--SCCMDocs-pr issue #3090-->
이전 버전의 지원 센터가 설치되어 있으면 버전 1810 설치 관리자에 오류가 발생합니다. 이 문제는 파일이 원래 버전과 최신 버전 간에 버전이 지정되는 방식 때문에 발생합니다. 이 문제를 해결하려면 지원 센터의 이전 버전을 먼저 제거하세요. 그런 다음, Configuration Manager 버전 1810에서 최신 버전을 설치합니다.

#### <a name="remote-connections-must-include-computer-name-or-domain-as-part-of-the-user-name"></a>원격 연결이 사용자 이름의 일부로 컴퓨터 이름 또는 도메인을 포함해야 함
지원 센터에서 원격 클라이언트에 연결할 경우 연결을 수립할 때 사용자 이름에 대해 머신 이름 또는 도메인 이름을 입력해야 합니다. 약식 컴퓨터 이름 또는 도메인 이름(예: `.\administrator`)을 사용할 경우 연결은 성공하지만 지원 센터가 해당 클라이언트에서 데이터를 수집하지는 않습니다. 

이 문제를 방지하려면 다음 사용자 이름 형식을 사용하여 원격 클라이언트에 연결합니다. 
- `ComputerName\UserName`  
- `DomainName\UserName`  

#### <a name="scripted-server-message-block-connections-to-remote-clients-might-require-removal"></a>원격 클라이언트에 대한 스크립팅된 서버 메시지 차단 연결에서 제거가 필요할 수 있음
[New-CMMachineConnection](https://go.microsoft.com/fwlink/p/?linkid=390542) PowerShell cmdlet을 사용하여 원격 클라이언트에 연결할 때 지원 센터는 각 원격 클라이언트에 대한 SMB(서버 메시지 블록)를 만듭니다. 데이터 수집을 완료한 후 해당 연결은 유지됩니다. Windows에 대해 최대 원격 연결 수를 초과하지 않기 위해 `net use` 명령을 사용하여 현재 활성화된 원격 연결 집합을 확인합니다. 그런 다음, `net use <connection_name> /d` 명령을 사용하여 불필요한 연결을 사용하지 않게 설정합니다. 
여기서 `<connection_name>`은 원격 연결의 이름입니다.

#### <a name="application-deployment-evaluation-cycle-request-isnt-sent-correctly-to-remote-machines"></a>애플리케이션 배포 평가 주기 요청이 원격 머신에 올바르게 전송되지 않음
<!--2849356-->
지원 센터에서 **콘텐츠** 탭의 **트리거 호출** 작업에서 **애플리케이션 배포 평가**를 선택하면 배포된 애플리케이션을 평가하는 작업이 시작됩니다. 로컬 클라이언트에 연결된 경우, 머신 및 사용자 애플리케이션 배포를 둘 다 평가합니다. 그러나 원격 클라이언트에 연결된 경우 머신 애플리케이션 배포만 평가합니다.


## <a name="next-steps"></a>다음 단계

[지원 센터 빠른 시작](/sccm/core/support/support-center-quickstart)
