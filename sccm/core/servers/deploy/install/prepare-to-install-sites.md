---
title: 사이트를 설치할 준비
titleSuffix: Configuration Manager
description: 여러 Configuration Manager 사이트를 설치할 계획인 경우 이 정보를 읽으면 시간을 절약하고 오류를 방지할 수 있습니다.
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9089e1b5-cba4-42bd-a2de-126ef882a3af
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 29e0f58404df2cadf2a1e28939ebcec2647b3e6d
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68339418"
---
# <a name="prepare-to-install-system-center-configuration-manager-sites"></a>System Center Configuration Manager 사이트 설치 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

하나 이상의 System Center Configuration Manager 사이트의 성공적인 배포를 준비하려면 이 문서를 자세히 이해하고 숙지해야 합니다. 이 단계를 통해 여러 사이트를 설치할 때 시간을 절약할 수 있으며 하나 이상의 사이트를 다시 설치해야 할 경우를 발생시키는 실수를 방지할 수 있습니다.

> [!TIP]
> System Center Configuration Manager 사이트 및 계층 인프라를 관리할 때 *업그레이드*, *업데이트* 및 *설치*라는 용어는 세 가지 별도의 개념을 설명하는 데 사용됩니다. 각 용어가 어떻게 사용되는지 알아보려면 [업그레이드, 업데이트 및 설치 정보](/sccm/core/understand/upgrade-update-install)를 참조하세요.

## <a name="bkmk_options"></a> 서로 다른 유형의 사이트 설치 옵션
새 Configuration Manager 사이트를 설치하는 경우 사용할 수 있는 소스 파일의 버전은 계층 구조에 이미 있는 사이트(있는 경우)의 버전에 따라 달라집니다. 사용할 수 있는 설치 방법은 설치하려는 사이트 유형에 따라 달라집니다.  

사이트를 설치하기 전에 먼저 계층 구조를 계획했어야 하고 설치하려는 사이트의 유형을 이해해야 합니다. 자세한 내용은 [사이트 계층 구조 디자인](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)을 참조하세요.


### <a name="first-site"></a>첫 번째 사이트
계층 구조에 설치할 첫 번째 사이트는 독립 실행형 기본 사이트 또는 중앙 관리 사이트입니다.

**설치 미디어**: 중앙 관리 사이트 또는 독립 실행형 기본 사이트를 새 계층 구조의 첫 번째 사이트로 설치하려면 Configuration Manager의 [기준 버전을 사용](../../../../core/servers/manage/updates.md#bkmk_Baselines)해야 합니다. 임의 사이트의 [CD.Latest 폴더](../../../../core/servers/manage/the-cd.latest-folder.md)에서 업데이트된 소스 파일을 사용하여 새 계층 구조의 첫 번째 사이트를 설치하지 마세요.

**설치 방법**: [Configuration Manager 설치 마법사](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md)를 사용하여 두 유형의 사이트를 설치하거나 [스크립팅된 명령줄 설치](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md)와 함께 사용하도록 스크립트를 구성할 수 있습니다.


### <a name="additional-sites"></a>추가 사이트
첫 사이트를 설치한 후 언제든지 사이트를 더 추가할 수 있습니다. 다음 옵션을 사용하여 사이트를 [지원되는 제한](../../../../core/plan-design/configs/size-and-scale-numbers.md)까지 추가할 수 있습니다.

|현재 소유한 사이트|설치할 수 있는 추가 사이트 유형|
|---|---|
|중앙 관리 사이트|자식 기본 사이트|
|자식 기본 사이트|보조 사이트|
|독립 실행형 기본 사이트|보조 사이트(기본 사이트를 확장할 수 있으며, 독립 실행형 기본 사이트가 자식 기본 사이트로 변환됨)|

**설치 미디어**: 중앙 관리 사이트를 설치하여 독립 실행형 기본 사이트를 확장하거나 기존 계층 구조에 새 자식 기본 사이트를 설치하는 경우 기존 사이트 또는 사이트의 버전과 일치하는 설치 미디어(원본 파일 포함)를 사용해야 합니다.

> [!IMPORTANT]
> 이전에 설치된 사이트 버전이 변경된 콘솔 내 업데이트를 설치한 경우 원본 설치 미디어를 사용하지 마세요. 대신, 해당 시나리오에서는 업데이트된 사이트의 [CD.Latest 폴더](../../../../core/servers/manage/the-cd.latest-folder.md)에 있는 소스 파일을 사용합니다. Configuration Manager에서는 새 사이트가 연결될 기존 사이트의 버전과 일치하는 소스 파일을 사용해야 합니다.

Configuration Manager 콘솔에서 보조 사이트를 설치해야 합니다. 이러한 방식으로 보조 사이트는 항상 부모 기본 사이트의 소스 파일을 사용하여 설치됩니다.

**설치 방법**: 추가 사이트를 설치하는 방법은 설치하려는 사이트의 유형에 따라 다릅니다.
- **중앙 관리 사이트 추가**:  Configuration Manager 설치 마법사 또는 스크립팅된 명령줄을 사용하여 새 중앙 관리 사이트를 기존 독립 실행형 기본 사이트에 부모 사이트로 설치할 수 있습니다. 자세한 내용은 [독립 실행형 기본 사이트 확장](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand)을 참조하세요.
- **자식 기본 사이트 추가**:  Configuration Manager 설치 마법사 또는 명령줄 설치를 사용하여 중앙 관리 사이트 아래 자식 기본 사이트를 추가합니다.
- **보조 사이트 추가**:  Configuration Manager 콘솔을 사용하여 보조 사이트를 기본 사이트의 자식 사이트로 설치합니다. 보조 사이트를 추가하는 다른 방법은 지원되지 않습니다.

## <a name="bkmk_tasks"></a> 설치를 시작하기 전에 완료해야 하는 일반적인 작업
- **배포에 사용할 계층 구조 토폴로지 이해**    
자세한 내용은 [System Center Configuration Manager에 대한 사이트 계층 구조 디자인](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)을 참조하세요.  

- **Configuration Manager에 사용할 수 있도록 필수 조건과 지원되는 구성을 충족하는 개별 서버 준비 및 구성**         
자세한 내용은 [사이트 및 사이트 시스템 필수 조건](../../../../core/plan-design/configs/site-and-site-system-prerequisites.md)을 참조하세요.  

- **사이트 데이터베이스를 호스트하는 SQL Server 설치 및 구성**     
자세한 내용은 [System Center Configuration Manager에 대한 SQL Server 버전 지원](../../../../core/plan-design/configs/support-for-sql-server-versions.md)을 참조하세요.  

- **Configuration Manager를 지원하도록 네트워크 환경 준비**      
자세한 내용은 [Configuration Manager를 준비하기 위한 방화벽, 포트 및 도메인 구성](../../../../core/plan-design/network/configure-firewalls-ports-domains.md)을 참조하세요.  

- **PKI(공개 키 인프라)를 사용하려는 경우 인프라 및 인증서 준비**      
자세한 내용은 [Configuration Manager를 위한 PKI 인증서 요구 사항](../../../../core/plan-design/network/pki-certificate-requirements.md)을 참조하세요.

- **사이트 서버 또는 사이트 시스템 서버로 사용할 컴퓨터에 최신 보안 업데이트 설치 및 필요한 경우 다시 시작**

## <a name="bkmk_sitecodes"></a> 사이트 이름 및 사이트 코드 정보
사이트 코드 및 사이트 이름은 Configuration Manager 계층 구조의 사이트를 식별하고 관리하는 데 사용됩니다. Configuration Manager 콘솔에서 사이트 코드 및 사이트 이름은 &lt;*사이트 코드*\> - &lt;*사이트 이름*\> 형식으로 표시됩니다. 계층에 사용하는 사이트 코드는 모두 서로 고유해야 합니다. Active Directory 스키마가 Configuration Manager에 대해 확장된 경우 사이트에서 데이터를 게시하면 Active Directory 포리스트 내에 사용되는 사이트 코드는 다른 Configuration Manager 계층 구조에 사용되거나 이전 Configuration Manager 설치에 사용되었던 경우라도 반드시 고유해야 합니다. 따라서 계층을 배포하기 전에 사이트 코드 및 사이트 이름을 신중하게 계획해야 합니다.

### <a name="specify-a-site-code-and-site-name"></a>사이트 코드 및 사이트 이름 지정
Configuration Manager 설치 프로그램을 실행하는 경우 중앙 관리 사이트와 각 기본 사이트 및 보조 사이트 설치에 대한 사이트 코드 및 사이트 이름을 지정하라는 메시지가 나타납니다. 사이트 코드는 계층 구조의 각 사이트를 고유하게 식별해야 합니다. 사이트 코드는 폴더 이름에 사용되므로 사이트 코드에 다음 이름(Configuration Manager 및 Windows에 예약된 이름 포함)을 사용하지 마세요.
- AUX
- CON
- NUL
- PRN
- SMS

> [!NOTE]
> Configuration Manager 설치 프로그램은 사이트 코드를 이미 사용 중인지 여부를 확인하지 않습니다.

Configuration Manager 설치 프로그램을 실행하는 동안 사이트의 사이트 코드를 입력하려면 3자리 영숫자를 입력해야 합니다. *A*~*Z* 문자와 *0*~*9* 숫자만 임의로 조합해서 사이트 코드에 사용할 수 있습니다. 연속된 문자나 숫자는 사이트 간 통신에 아무런 영향을 미치지 않습니다. 예를 들어 기본 사이트 이름을 *ABC*로 지정하고 보조 사이트 이름을 *DEF*로 지정할 필요가 없습니다.

사이트 이름은 사이트의 이름 식별자입니다. 문자 *A*~*Z*, *a*~*z*, *0*~*9* 및 하이픈( *-* )만 사이트 이름에 사용할 수 있습니다.

> [!IMPORTANT]
> 사이트를 설치한 후에는 사이트 코드 또는 사이트 이름을 변경할 수 없습니다.

### <a name="reuse-a-site-code"></a>사이트 코드 다시 사용
사이트 코드는 원본 사이트 및 사이트 코드가 제거되었더라도 중앙 관리 사이트 또는 기본 사이트에 대해 Configuration Manager 계층 구조에서 한 번만 사용할 수 있습니다. 사이트 코드를 다시 사용하는 경우 계층 구조에서 개체 ID가 충돌할 위험이 있습니다. 보조 사이트 및 사이트 코드가 Configuration Manager 계층 구조 또는 Active Directory 포리스트에서 더 이상 사용되지 않는 경우 해당 사이트 코드를 보조 사이트에 다시 사용할 수 있습니다.

## <a name="limits-and-restrictions-for-installed-sites"></a>설치되는 사이트에 대한 제한 사항
사이트를 설치하기 전에 사이트 및 계층 구조에 적용되는 다음 제한 사항을 이해하는 것이 중요합니다.
- 설치 프로그램을 실행한 후 사이트를 제거하고 새 값을 사용하여 다시 설치하지 않으면 다음 사이트 속성을 변경할 수 없습니다.  
  - 프로그램 파일 설치 디렉터리  
  - 사이트 코드  
  - 사이트 설명  
- 계층 구조에 중앙 관리 사이트가 포함된 경우:  
  - Configuration Manager에서는 독립 실행형 기본 사이트를 만들거나 다른 계층 구조에 연결하기 위해 계층 구조에서 자식 기본 사이트를 이동할 수 없습니다. 대신, 자식 기본 사이트를 제거한 다음 새 독립 실행형 기본 사이트로 다시 설치하거나 다른 계층 구조의 중앙 관리 사이트의 자식 사이트로 다시 설치할 수 있습니다.  


## <a name="bkmk_optionalsteps"></a> 설치 프로그램을 실행하기 전의 선택적 단계
**수동으로 [설치 다운로더](../../../../core/servers/deploy/install/setup-downloader.md) 실행**

Configuration Manager의 업데이트된 설치 파일을 다운로드하려면 설치 다운로더를 실행합니다. 설치 프로그램을 실행할 컴퓨터가 인터넷에 연결되어 있지 않거나 여러 사이트 서버를 설치하려는 경우에는 설치 다운로더를 사용하여 설치 프로그램에 대한 필수 업데이트를 다운로드하는 것이 좋습니다. 추가 정보는 다음과 같습니다.
- 기본적으로 설치 프로그램은 인터넷에 연결하여 업데이트된 설치 파일을 다운로드합니다.
- 기본적으로 파일은 Redist 폴더에 저장됩니다.
- 설치 프로그램이 이전에 이러한 파일의 복사본을 저장한 네트워크의 위치를 사용하도록 지정할 수 있습니다.

**수동으로 [필수 조건 검사기](../../../../core/servers/deploy/install/prerequisite-checker.md) 실행**

설치 프로그램을 실행하여 사이트를 설치하기 전과 서버에 사이트 시스템 역할을 설치하기 전에 문제를 식별하고 해결하려면 필수 조건 검사기를 실행할 수 있습니다. 필수 조건 검사기는 컴퓨터가 사이트 또는 사이트 시스템 역할을 호스트하기 위한 요구 사항을 충족하는지 확인합니다. 추가 정보는 다음과 같습니다.
- 기본적으로 설치 프로그램은 필수 조건 검사기를 실행합니다.
- 오류가 발생하면 문제를 해결할 때까지 설치 프로그램이 중지됩니다.

**선택적 포트 식별**

사이트 시스템 및 클라이언트에서 사용할 선택적 포트를 식별할 수 있습니다. 추가 정보는 다음과 같습니다.
- 기본적으로 사이트 시스템 및 클라이언트는 미리 정의된 포트를 사용하여 통신합니다.
- 설치하는 동안 대체 포트를 구성할 수 있습니다.

자세한 내용은 [System Center Configuration Manager에서 사용되는 포트](../../../../core/plan-design/hierarchy/ports.md)를 참조하세요.
