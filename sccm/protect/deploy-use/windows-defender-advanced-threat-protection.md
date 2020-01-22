---
title: Microsoft Defender Advanced Threat Protection
titleSuffix: Configuration Manager
description: 기업이 고급 공격에 대응하는 데 도움이 되는 새로운 서비스인 Microsoft Defender Advanced Threat Protection을 관리 및 모니터링하는 방법을 알아봅니다.
ms.date: 01/07/2020
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 9326be9aed2975d24282bd2ced09cec54efe2732
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76032757"
---
# <a name="microsoft-defender-advanced-threat-protection"></a>Microsoft Defender Advanced Threat Protection

*적용 대상: Configuration Manager(현재 분기)*

Endpoint Protection은 [Microsoft Defender ATP(Advanced Threat Protection)](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)(이전에는 Windows Defender ATP라고 함)를 관리하고 모니터링하는 데 도움이 됩니다. Windows Defender ATP는 엔터프라이즈에서 네트워크에 대한 고급 공격을 검색, 조사 및 대응할 수 있게 해줍니다. Configuration Manager 정책은 Windows 10 클라이언트를 등록하고 모니터링하는 데 도움이 됩니다.

Microsoft Defender ATP는 [Windows Defender Security Center](https://securitycenter.windows.com)의 서비스입니다. 클라이언트 온보딩 구성 파일을 추가 및 배포하면 Configuration Manager에서 배포 상태 및 Microsoft Defender ATP 에이전트 상태를 모니터링할 수 있습니다. Microsoft Defender ATP는 구성 관리자 클라이언트를 실행하는 PC에서 지원되거나 [Microsoft Intune에서 관리됩니다](https://docs.microsoft.com/intune/protect/advanced-threat-protection).

## <a name="prerequisites"></a>전제 조건

- Microsoft Defender Advanced Threat Protection 온라인 서비스에 대한 구독  
- Windows 10 버전 1607 이상을 실행하는 클라이언트 컴퓨터  
- 구성 관리자 클라이언트를 실행하는 클라이언트 컴퓨터용입니다.

## <a name="create-an-onboarding-configuration-file"></a>온보딩 구성 파일 만들기  

1. [Microsoft Defender ATP 온라인 서비스](https://securitycenter.windows.com/)로 이동하여 로그인합니다.

2. **설정**에서 **컴퓨터 관리** 항목을 선택한 다음 **온보딩**을 선택합니다.

3. **Configuration Manager(현재 분기) 버전 1606**을 선택하고 **패키지 다운로드**를 선택합니다.

4. 압축된 보관 파일(.zip)을 다운로드하고 압축을 풉니다.

> [!IMPORTANT]
> Microsoft Defender ATP 구성 파일에는 보안을 유지해야 하는 중요한 정보가 포함되어 있습니다.

## <a name="onboard-devices"></a>디바이스 온보딩

1. Configuration Manager 콘솔에서 **자산 및 준수** > **Endpoint Protection** > **Windows Defender ATP 정책**으로 이동하고 **Windows Defender ATP 정책 만들기**를 선택합니다. Microsoft Defender ATP 정책 마법사가 열립니다.  

2. Windows Defender ATP 정책의 **이름** 및 **설명**을 입력하고 **온보딩**을 선택합니다.

3. 조직의 Microsoft Defender ATP 클라우드 서비스 테넌트에서 제공하는 구성 파일을 **찾습니다**.

4. 분석을 위해 관리되는 디바이스에서 수집 및 공유되는 파일 샘플을 지정합니다.  

   - **없음**

   - **모든 파일 형식**  

5. 요약을 검토하고 마법사를 완료합니다.  

**배포**를 선택하여 Microsoft Defender ATP 정책을 클라이언트에 대상으로 합니다.

## <a name="monitor"></a>모니터

1. Configuration Manager 콘솔에서 **모니터링** > **보안**으로 이동한 다음 **Windows Defender ATP**를 선택합니다.  

2. Microsoft Defender Advanced Threat Protection 대시보드를 검토합니다.  

    - **Windows Defender 에이전트 배포 상태**: 활성 Microsoft Defender ATP 정책이 온보딩된 적합한 관리형 클라이언트 컴퓨터 수 및 백분율  

    - **Windows Defender ATP 에이전트 상태**: Microsoft Defender ATP 에이전트에 대한 상태를 보고하는 컴퓨터 클라이언트의 백분율  

        - **정상** - 정상적으로 작동  

        - **비활성** - 기간 동안 서비스로 보내는 데이터가 없음  

        - **에이전트 상태** - Windows에서 에이전트에 대한 시스템 서비스가 실행되지 않음  

        - **온보딩되지 않음** - 정책이 적용되었지만 에이전트가 온보딩된 정책을 보고하지 않음  

## <a name="create-an-offboarding-configuration-file"></a>오프보딩 구성 파일 만들기  

1. [Microsoft Defender ATP 온라인 서비스](https://securitycenter.windows.com/)에 로그인합니다.

2. **설정**에서 **컴퓨터 관리** 항목을 선택한 다음 **온보딩**을 선택합니다.  

3. **Configuration Manager(현재 분기) 버전 1606**을 선택하고 **엔드포인트 오프보딩**을 선택합니다.  

4. 압축된 보관 파일(.zip)을 다운로드하고 압축을 풉니다. 오프보딩 파일은 30일 동안 유효합니다.

5. Configuration Manager 콘솔에서 **자산 및 준수** > **Endpoint Protection** > **Windows Defender ATP 정책**으로 이동하고 **Windows Defender ATP 정책 만들기**를 선택합니다. Microsoft Defender ATP 정책 마법사가 열립니다.  

6. Microsoft Defender ATP 정책의 **이름** 및 **설명**을 입력하고 **오프보딩**을 선택합니다.

7. 조직의 Microsoft Defender ATP 클라우드 서비스 테넌트에서 제공하는 구성 파일을 **찾습니다**.

8. 요약을 검토하고 마법사를 완료합니다.  

**배포**를 선택하여 Microsoft Defender ATP 정책을 클라이언트에 대상으로 합니다.  

> [!IMPORTANT]
> Microsoft Defender ATP 구성 파일에는 보안을 유지해야 하는 중요한 정보가 포함되어 있습니다.

## <a name="next-steps"></a>다음 단계

- [Microsoft Defender Advanced Threat Protection](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection)

- [Microsoft Defender Advanced Threat Protection 온보딩 문제 해결](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
