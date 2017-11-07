---
title: "상태 증명"
titleSuffix: Configuration Manager
description: "Configuration Manager 콘솔에서 볼 수 있는 장치 상태 증명 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 10/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 91f9de33-b277-4500-acd6-e7d90a2947c9
caps.latest.revision: "17"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 4b9ce2aad95036e12167626897052de23cc937ae
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="health-attestation-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 상태 증명

*적용 대상: System Center Configuration Manager(현재 분기)*

관리자는 Configuration Manager 콘솔에서 [Windows 10 장치 상태 증명](https://technet.microsoft.com/library/mt592023.aspx)의 상태를 볼 수 있습니다.  장치 상태 증명을 사용하여 관리자는 클라이언트 컴퓨터가 다음과 같이 신뢰할 수 있는 BIOS, TPM 및 부팅 소프트웨어 구성을 활성화했는지 확인할 수 있습니다.  

-   맬웨어 방지 조기 실행 - ELAM(맬웨어 방지 조기 실행)은 ELAM이 시작되면서 그리고 타사 드라이버가 초기화되기 전에 컴퓨터를 보호합니다. [ELAM을 켜는 방법](https://gallery.technet.microsoft.com/How-to-turn-on-Early-84552ec5)  
-   BitLocker - Windows BitLocker 드라이브 암호화는 Windows 운영 체제 볼륨에 저장된 모든 데이터를 암호화할 수 있도록 지원하는 소프트웨어입니다.  [BitLocker를 켜는 방법](https://gallery.technet.microsoft.com/How-to-turn-on-BitLocker-34294d3d)  
-   보안 부팅 - 보안 부팅은 PC 제조업체에서 신뢰할 수 있는 소프트웨어만 사용하여 PC가 부팅되는지 확인하기 위해 PC 업계의 멤버가 개발한 보안 표준입니다. [보안 부팅에 대한 자세한 정보](https://technet.microsoft.com/library/hh824987.aspx)  
-   코드 무결성 - 코드 무결성은 메모리에 로드될 때마다 드라이버 또는 시스템 파일의 무결성을 확인하여 운영 체제의 보안을 향상시키는 기능입니다. [코드 무결성에 대해 알아보기](https://technet.microsoft.com/library/dd348642.aspx)  

이 기능은 Configuration Manager에서 관리하는 PC 및 온-프레미스 리소스와 Microsoft Intune로 관리되는 모바일 장치에 사용할 수 있습니다. 관리자는 클라우드를 통해 또는 온-프레미스 인프라를 통해 보고를 수행할지 여부를 지정할 수 있습니다. 온-프레미스 장치 상태 증명 모니터링을 통해 관리자는 인터넷 액세스 없이 클라이언트 PC를 모니터링할 수 있습니다.

## <a name="enable-health-attestation"></a>상태 증명 사용

 **요구 사항:**  

-   [장치 상태 증명이 사용하도록 설정된](https://technet.microsoft.com/windows-server-docs/security/device-health-attestation) Windows 10 버전 1607 또는 Windows Server 2016 버전 1607을 실행하는 클라이언트 장치
-   TPM 1.2 또는 TPM 2 사용 장치
-   클라우드 관리를 사용하는 경우 Configuration Manager 클라이언트 에이전트와 *has.spserv.microsoft.com*(포트 443) 상태 증명 서비스(클라우드 관리) 간 통신 온-프레미스인 경우 클라이언트는 장치 상태 증명 사용 관리 지점과 통신할 수 있어야 합니다.

### <a name="how-to-enable-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Configuration Manager 클라이언트 컴퓨터에서 상태 증명 서비스 통신을 활성화하는 방법

이 절차에 따라 인터넷에 연결된 장치의 장치 상태 증명 모니터링을 사용하도록 설정합니다.

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 선택합니다.  **컴퓨터 에이전트** 설정의 탭을 선택합니다.  
2.  **기본 설정** 대화 상자에서 **컴퓨터 에이전트** 를 선택한 후 **상태 증명 서비스와의 통신 사용**으로 스크롤합니다.  
3.  **상태 증명 서비스와의 통신 사용** 을 **예**로 설정한 후 **확인**을 클릭합니다.  
4. 장치 상태를 보고해야 하는 장치 컬렉션을 대상으로 지정합니다.

### <a name="how-to-enable-on-premises-health-attestation-service-communication-on-configuration-manager-client-computers"></a>Configuration Manager 클라이언트 컴퓨터에서 온-프레미스 상태 증명 서비스 통신을 사용하는 방법
이 절차에 따라 인터넷에 연결되지 않은 온-프레미스 장치의 장치 상태 증명 모니터링을 사용하도록 설정합니다.

Configuration Manager 1702부터 인터넷 액세스 없이 클라이언트 장치를 지원하도록 관리 지점에서 온-프레미스 장치 상태 증명 서비스 URL을 구성할 수 있습니다.

1. Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.
2. 온-프레미스 장치 상태 증명 클라이언트를 지원하는 관리 지점이 있는 기본 또는 보조 사이트를 마우스 오른쪽 단추로 클릭하고 **사이트 구성 요소 구성** > **관리 지점**을 선택합니다. **관리 지점 구성 요소 속성** 페이지가 열립니다.
3. **고급 옵션** 탭에서 **추가**를 선택하고 유효한 온-프레미스 장치 상태 증명 서비스 URL을 지정합니다. 여러 URL을 추가할 수 있습니다. 온-프레미스 URL을 여러 개 지정하면 클라이언트는 전체 집합을 받고 사용할 URL을 임의로 선택합니다.
4.  Configuration Manager 콘솔에서 **관리** > **개요** > **클라이언트 설정**을 선택합니다.  **컴퓨터 에이전트** 설정의 탭을 선택합니다.  
5.  **기본 설정** 대화 상자에서 **컴퓨터 에이전트**를 선택한 후 **온-프레미스 상태 증명 서비스 사용**으로 아래로 스크롤하고 **예**로 설정합니다.
6. 클라이언트 에이전트 설정을 통해 장치 상태를 보고해야 하는 장치 컬렉션을 대상으로 지정하여 장치 상태 증명 보고를 사용하도록 설정합니다.

장치 상태 증명 서비스 URL을 **편집** 또는 **제거**할 수도 있습니다.

> [!NOTE]
> Configuration Manager 1702로 업그레이드하기 전에 장치 상태 증명을 사용한 경우 클라이언트 에이전트 설정에 지정된 온-프레미스 URL은 업그레이드하는 동안 관리 지점 속성에 미리 채워집니다. 온-프레미스 클라이언트는 업그레이드될 때까지 클라이언트 에이전트 설정에 지정된 URL을 계속 사용합니다. 이후 이러한 클라이언트는 관리 지점에 지정된 URL 중 하나로 전환됩니다.

## <a name="monitor-device-health-attestation"></a>장치 상태 증명 모니터링

1.  장치 상태 증명 보기를 보려면 Configuration Manager에서 **모니터링** 작업 영역으로 이동한 후 **보안** 노드를 클릭하고 **상태 증명**을 클릭합니다.  
2.  장치 상태 증명이 표시됩니다.  

Configuration Manager 장치 상태 증명에는 다음이 표시됩니다.  

-   **상태 증명** - 규격, 비규격, 오류 및 알 수 없는 상태의 장치 비율을 표시합니다.  
-   **장치 보고 상태 증명** - 상태 증명 상태를 보고하는 장치의 비율을 표시합니다.  
-   **클라이언트 유형별 비규격 장치** - 비규격인 모바일 장치 및 컴퓨터의 비율을 표시합니다.  
-   **가장 많이 누락되는 상태 증명 설정** - 상태 증명 설정이 누락된 장치의 수를 표시합니다(설정별로 나열됨).

클라이언트 장치 상태 증명 상태를 사용하여 Microsoft Intune과 함께 Configuration Manager에서 관리하는 장치에 대한 준수 정책에서 조건부 액세스에 대한 규칙을 정의할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 장치 규정 준수 정책 관리](/sccm/protect/deploy-use/device-compliance-policies)를 참조하세요.  
