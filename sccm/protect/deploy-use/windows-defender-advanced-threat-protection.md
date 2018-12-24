---
title: Windows Defender Advanced Threat Protection
titleSuffix: Configuration Manager
description: 기업이 고급 공격에 대응하는 데 도움이 되는 새로운 서비스인 Windows Defender Advanced Threat Protection을 관리 및 모니터링하는 방법을 알아봅니다.
ms.date: 03/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: a5fc033e-828e-4e45-9097-bbbd0697ebdf
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 10d746f88d0e7b869e2b73d389944f3b382d687d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32348388"
---
# <a name="windows-defender-advanced-threat-protection"></a>Windows Defender Advanced Threat Protection

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 1606 버전부터(현재 분기) Endpoint Protection은 [Windows Defender ATP(Advanced Threat Protection)](http://aka.ms/technet-wdatp)를 관리하고 모니터링할 수 있습니다. Windows Defender ATP는 엔터프라이즈에서 네트워크에 대한 고급 공격을 검색, 조사 및 대응할 수 있게 해줍니다.  Configuration Manager 또는 Microsoft Intune 정책은 관리되는 Windows 10 버전 1607(빌드 14328) 이상을 등록하고 모니터링하는 데 도움이 됩니다.

Windows Defender ATP는 [Windows Defender 보안 센터](https://securitycenter.windows.com)의 서비스입니다. 클라이언트 온보딩 구성 파일을 추가 및 배포하면 Configuration Manager에서 배포 상태 및 Windows Defender ATP 에이전트 상태를 모니터링할 수 있습니다. Windows Defender ATP는 Configuration Manager 클라이언트를 실행하는 PC에서 지원되거나 Microsoft Intune에서 관리되지만 Intune 하이브리드 MDM 관리 컴퓨터는 지원되지 않습니다.

 **전제 조건**  

-   Windows Defender Advanced Threat Protection 온라인 서비스에 대한 구독  
-   Windows 10 버전 1607 이상을 실행하는 클라이언트 컴퓨터  
-   Configuration Manager 1610 이상 버전의 클라이언트 에이전트를 실행하거나 Microsoft Intune에서 관리하는 클라이언트 컴퓨터

## <a name="how-to-create-an-onboarding-configuration-file"></a>온보딩 구성 파일을 만드는 방법  

 1.  [Windows Defender ATP 온라인 서비스](https://securitycenter.windows.com/)에 로그온합니다.   

 2.  **끝점 관리** 메뉴 항목을 클릭합니다.  

 3.  **System Center Configuration Manager(현재 분기) 버전 1606**을 선택하고 **패키지 다운로드**를 클릭합니다.  

 4.  압축된 보관 파일(.zip)을 다운로드하고 압축을 풉니다.

> [!IMPORTANT]
> Windows Defender ATP 구성 파일에는 보안을 유지해야 하는 중요한 정보가 포함되어 있습니다.

## <a name="onboard-devices-for-windows-defender-atp"></a>Windows Defender ATP 디바이스 온보딩  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **Endpoint Protection** > **Windows Defender ATP 정책**으로 이동하고 **Windows Defender ATP 정책 만들기**를 클릭합니다. Windows Defender ATP 정책 마법사가 열립니다.  

2.  Windows Defender ATP 정책의 **이름** 및 **설명**을 입력하고 **온보딩**을 선택합니다. **다음**을 클릭합니다.  

3.  조직의 Windows Defender ATP 클라우드 서비스 테넌트에서 제공하는 구성 파일을 **찾습니다**. **다음**을 클릭합니다.  

4.  분석을 위해 관리되는 디바이스에서 수집 및 공유되는 파일 샘플을 지정합니다.  

    -   **없음**   

    -   **모든 파일 형식**  

     **다음**을 클릭합니다.  

5.  요약을 검토하고 마법사를 완료합니다.  

6.  이제 **배포**를 클릭하면 관리되는 클라이언트 컴퓨터에 Windows Defender ATP 정책을 배포할 수 있습니다.  

## <a name="monitor-windows-defender-atp"></a>Windows Defender ATP 모니터링  

1.  Configuration Manager 콘솔에서 **모니터링** > **개요** > **보안**으로 이동한 다음 **Windows Defender ATP**를 클릭합니다.  

2.  Windows Defender Advanced Threat Protection 대시보드를 검토합니다.  

    -   **Windows Defender 에이전트 배포 상태** – 활성 Windows Defender ATP 정책이 온보딩된 적합한 관리되는 클라이언트 컴퓨터 수 및 백분율  

    -   **Windows Defender ATP 에이전트 상태** – Windows Defender ATP 에이전트에 대한 상태를 보고하는 컴퓨터 클라이언트의 백분율  

        -   **정상** - 정상적으로 작동  

        -   **비활성** - 기간 동안 서비스로 보내는 데이터가 없음  

        -   **에이전트 상태** - Windows에서 에이전트에 대한 시스템 서비스가 실행되지 않음  

        -   **온보딩되지 않음** - 정책이 적용되었지만 에이전트가 온보딩된 정책을 보고하지 않음  


## <a name="how-to-create-and-deploy-an-offboarding-configuration-file"></a>오프보딩 구성 파일을 만들고 배포하는 방법  

1.  [Windows Defender ATP 온라인 서비스](https://securitycenter.windows.com/)에 로그온합니다.   

2.  **끝점 관리** 메뉴 항목을 클릭합니다.  

3.  **System Center Configuration Manager(현재 분기) 버전 1606**을 선택하고 **끝점 오프보딩**을 클릭합니다.  

4.  압축된 보관 파일(.zip)을 다운로드하고 압축을 풉니다. 오프보딩 파일은 30일 동안 유효합니다.

5.  Configuration Manager 콘솔에서 **자산 및 준수** > **개요** > **Endpoint Protection** > **Windows Defender ATP 정책**으로 이동하고 **Windows Defender ATP 정책 만들기**를 클릭합니다. Windows Defender ATP 정책 마법사가 열립니다.  

6.  Windows Defender ATP 정책의 **이름** 및 **설명**을 입력하고 **오프보딩**을 선택합니다. **다음**을 클릭합니다.  

7.  조직의 Windows Defender ATP 클라우드 서비스 테넌트에서 제공하는 구성 파일을 **찾습니다**. **다음**을 클릭합니다.  

8.  요약을 검토하고 마법사를 완료합니다.  

9.  이제 **배포**를 클릭하면 관리되는 클라이언트 컴퓨터에 Windows Defender ATP 정책을 배포할 수 있습니다.  

> [!IMPORTANT]
> Windows Defender ATP 구성 파일에는 보안을 유지해야 하는 중요한 정보가 포함되어 있습니다.

[Windows Defender Advanced Threat Protection](https://technet.microsoft.com/itpro/windows/keep-secure/windows-defender-advanced-threat-protection)

[Windows Defender Advanced Threat Protection 등록 문제 해결](https://technet.microsoft.com/itpro/windows/keep-secure/troubleshoot-onboarding-windows-defender-advanced-threat-protection)
