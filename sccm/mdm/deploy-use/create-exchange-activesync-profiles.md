---
title: Exchange ActiveSync 메일 프로필 만들기
titleSuffix: Configuration Manager
description: Microsoft Intune에서 작동하는 System Center Configuration Manager의 메일 프로필을 만들고 구성하는 방법을 알아봅니다.
ms.date: 07/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 120442be-179e-450c-a0c4-284046895da3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5ee29053f69eaf624079f42a33efa5cdba9d1de9
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32352603"
---
# <a name="exchange-activesync-email-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 Exchange ActiveSync 메일 프로필

*적용 대상: System Center Configuration Manager(현재 분기)*

Microsoft Intune 및 Exchange ActiveSync를 사용하여 디바이스에 메일 프로필 및 제한 사항을 설정할 수 있습니다. 그러면 최소한의 설정으로 자신의 디바이스에서 회사 메일에 액세스할 수 있습니다.  

 전자 메일 프로필을 사용하여 구성할 수 있는 디바이스 유형은 다음과 같습니다.  

- Windows 10
- Windows Phone 8.1
- iOS 9 이상을 실행하는 iPhone 
- iOS 9 이상을 실행하는 iPad 
- Samsung KNOX Standard 4 이상
- Android for Work

메일 프로필을 디바이스에 배포하려면 디바이스가 Intune에 등록되어 있어야 합니다. 디바이스를 등록하는 방법에 대한 자세한 내용은 [Microsoft Intune을 사용하여 모바일 디바이스 관리](https://technet.microsoft.com/library/dn646962.aspx)를 참조하세요.

> [!NOTE]
> Intune은 Gmail 메일 앱 및 Nine Work 메일 앱 각각에 대해 Android for Work 메일 프로필을 하나씩 제공합니다. 이러한 앱은 Google Play 스토어에서 사용할 수 있으며 Exchange로의 연결을 지원합니다. 메일 연결을 사용하도록 설정하려면 사용자의 디바이스에 이러한 메일 앱 중 하나를 배포한 다음 적절한 프로필을 만들어 배포합니다. Nine Work와 같은 메일 앱은 무료가 아닐 수도 있습니다. 앱의 라이선스 정보를 검토하거나, 질문이 있으면 앱 회사에 문의하세요.

 디바이스에서 메일 계정을 구성하는 것 외에 연락처, 일정 및 작업에 대한 동기화 설정을 구성할 수 있습니다.  

 메일 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 이러한 설정에는 System Center Configuration Manager 인증서 프로필을 사용하여 설정된 서명, 암호화 및 ID의 인증서가 포함되어 있습니다. 인증서 프로필에 대한 자세한 내용은 [System Center Configuration Manager의 인증서 프로필](/sccm/protect/deploy-use/introduction-to-certificate-profiles.md)을 참조하세요.    

## <a name="create-an-exchange-activesync-email-profile"></a>Exchange ActiveSync 메일 프로필 만들기  

프로필을 만들려면 Exchange ActiveSync 메일 프로필 만들기 마법사를 사용합니다. 

1.  Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.  

2.  **자산 및 호환성** 작업 영역에서 **호환성 설정**및 **회사 리소스 액세스**를 각각 확장하고 **메일 프로필**을 선택합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **Exchange ActiveSync 메일 프로필 만들기**를 선택하여 마법사를 시작합니다.

4.  마법사의 **일반** 페이지에서 다음을 구성합니다.

    - **이름**. 메일 프로필에 대한 설명이 포함된 이름을 제공합니다.

    - **설명**. 선택적으로 Configuration Manager 콘솔에서 메일 프로필을 식별하는 데 도움이 되는 메일 프로필에 대한 설명을 제공합니다.

    - **이 메일 프로필은 Android for Work용입니다**. 이 메일 프로필을 Android for Work 디바이스에만 배치하려면 이 옵션을 선택합니다. 이 확인란을 선택하면 **지원되는 플랫폼** 마법사 페이지가 표시되지 않습니다. Android for Work 메일 프로필만 구성됩니다.

4.  마법사의 **Exchange ActiveSync** 페이지에서 다음 정보를 지정합니다.  

    -   **Exchange ActiveSync 호스트**. Exchange ActiveSync 서비스를 호스트하는 회사 Exchange Server의 호스트 이름을 지정합니다.  

    -   **계정 이름**. 디바이스에서 사용자에게 표시될 메일 계정의 표시 이름을 지정합니다.  

    -   **계정 사용자 이름**. 클라이언트 디바이스에서 메일 계정 사용자 이름을 구성하는 방법을 선택합니다. 드롭다운 목록에서 다음 옵션 중 하나를 선택할 수 있습니다.  

        -   **UPN(사용자 계정 이름)**. 전체 사용자 계정 이름을 사용하여 Exchange에 로그인합니다.  

        -   **AccountName**. Active Directory의 전체 사용자 계정 이름을 사용합니다.

        -   **기본 SMTP 주소**. 사용자의 기본 SMTP 주소를 사용하여 Exchange에 로그인합니다.  

    -   **메일 주소** 각 클라이언트 디바이스에서 사용자의 메일 주소가 생성되는 방식을 선택합니다. 드롭다운 목록에서 다음 옵션 중 하나를 선택할 수 있습니다.  

        -   **기본 SMTP 주소**. 사용자의 기본 SMTP 주소를 사용하여 Exchange에 로그인합니다.  

        -   **UPN(사용자 계정 이름)**. 전체 사용자 계정 이름을 메일 주소로 사용합니다.  

    -   **계정 도메인**. 다음 옵션 중 하나를 선택합니다.  

        -   **Active Directory에서 가져오기**  

        -   **사용자 지정**  

         이 필드는 **계정 사용자 이름** 드롭다운 목록에서 **sAMAccountName** 을 선택한 경우에만 적용됩니다.  

    -   **인증 방법**. 다음 인증 방법 중에서 Exchange ActiveSync에 대한 연결을 인증하는 데 사용할 방법 하나를 선택합니다.  

        -   **인증서**. ID 인증서를 사용하여 Exchange ActiveSync 연결을 인증합니다.  

        -   **사용자 이름 및 암호**. Exchange ActiveSync에 연결하려면 디바이스 사용자가 암호를 제공해야 합니다. (사용자 이름은 메일 프로필의 일부로 구성됩니다.)  

    -   **ID 인증서**. **선택**을 선택한 다음 ID에 사용할 인증서를 선택합니다.  

         ID 인증서는 SCEP 인증서여야 합니다. PFX 인증서는 사용할 수 없습니다.  자세한 내용은 [Configuration Manager의 인증서 프로필](/sccm/protect/deploy-use/introduction-to-certificate-profiles)을 참조하세요.  

         이 옵션은 **인증 방법** 에서 **인증서**를 선택한 경우에만 사용할 수 있습니다.  

    -   **S/MIME 사용**. S/MIME 암호화를 사용하여 발신 메일을 전송합니다. 이 옵션은 iOS 디바이스에만 적용됩니다. 다음 옵션 중에서 선택 합니다.

        -   **서명 인증서**.  **선택**을 선택한 다음 암호화에 사용할 인증서 프로필을 선택합니다.  

            프로필은 SCEP 또는 PFX 인증서일 수 있습니다.  그러나 서명 및 암호화를 둘 다 사용하는 경우 서명 및 암호화 *둘 다*에 대해 PFX 인증서 프로필을 선택해야 합니다.

        -   **암호화 인증서**. **선택**을 선택한 다음 암호화에 사용할 인증서를 선택합니다. 암호화 인증서로 사용할 PFX 인증서를 선택해야 합니다.

        -   iOS 디바이스에서 모든 메일 메시지를 암호화하려면 **암호화 필요** 확인란을 선택합니다.    

         여기서 선택하려면 먼저 인증서 프로필을 만들어야 합니다.  자세한 내용은 [Configuration Manager의 인증서 프로필](/sccm/protect/deploy-use/introduction-to-certificate-profiles)을 참조하세요.  

## <a name="configure-synchronization-settings-for-the-exchange-activesync-email-profile"></a>Exchange ActiveSync 메일 프로필에 대한 동기화 설정을 구성합니다.  

Exchange ActiveSync 전자 메일 프로필 만들기 마법사의 **동기화 설정 구성** 페이지에서 다음 정보를 지정합니다.  

-   **일정**. 디바이스가 Exchange 서버의 데이터를 동기화할 일정을 선택합니다. 이 옵션은 Windows Phone 디바이스에만 적용됩니다. 다음 중에서 선택합니다.  

    -   **구성되지 않음**. 동기화 일정이 적용되지 않습니다. 그러면 고유한 동기화 일정을 구성할 수 있습니다.  

    -   **메시지가 도착할 때**. 메일 및 일정 항목과 같은 데이터가 도착 시 자동으로 동기화됩니다.  

    -   **15분**. 메일 및 일정 항목과 같은 데이터가 15분마다 자동으로 동기화됩니다.  

    -   **30분**. 메일 및 일정 항목과 같은 데이터가 30분마다 자동으로 동기화됩니다.  

    -   **60분**. 메일 및 일정 항목과 같은 데이터가 60분마다 자동으로 동기화됩니다.  

    -   **수동**. 디바이스 사용자가 수동으로 동기화를 시작해야 합니다.  

-   **동기화할 메일의 일 수**. 드롭다운 목록에서 동기화할 메일의 일 수를 선택합니다. 다음 값 중 하나를 선택합니다.  

    -   **구성되지 않음**. 설정이 적용되지 않습니다. 이 경우 사용자는 디바이스에 다운로드할 메일 수를 구성할 수 있습니다.  

    -   **무제한**. 사용 가능한 메일을 모두 동기화합니다.  

    -   **1일**  

    -   **3일**  

    -   **1주**  

    -   **2주**  

    -   **1개월**  

-   **메시지를 다른 메일 계정으로 이동하도록 허용**. 이 옵션을 선택하여 사용자가 디바이스에서 구성한 여러 계정 간에 메일 메시지를 이동할 수 있도록 허용합니다. 이 옵션은 iOS 디바이스에만 적용됩니다.  

-   **타사 응용 프로그램에서 메일을 전송할 수 있도록 허용**. 이 옵션을 선택하여 사용자가 기본이 아닌 타사 메일 애플리케이션에서 메일을 보낼 수 있도록 허용합니다. 이 옵션은 iOS 디바이스에만 적용됩니다.  

-   **최근에 사용한 메일 주소를 동기화**. 이 옵션을 선택하여 디바이스에서 최근에 사용된 메일 주소 목록을 동기화합니다. 이 옵션은 iOS 디바이스에만 적용됩니다.  

-   **SSL 사용**. 메일을 보내거나 받고 Exchange 서버와 통신할 때 SSL(Secure Sockets Layer)을 사용하려면 이 옵션을 선택합니다.  

-   **동기화할 콘텐츠 형식**. 디바이스에 동기화할 콘텐츠 형식을 선택합니다. 이 옵션은 Windows Phone 디바이스에만 적용됩니다. 다음 중에서 선택합니다.  

    -   **전자 메일**  

    -   **연락처**  

    -   **일정**  

    -   **태스크**  

## <a name="specify-supported-platforms-for-the-exchange-activesync-email-profile"></a>Exchange ActiveSync 메일 프로필에 대한 지원되는 플랫폼을 지정합니다.  

1.  Exchange ActiveSync 메일 프로필 만들기 마법사의 **지원되는 플랫폼** 페이지에서 메일 프로필을 설치할 운영 체제를 선택합니다. 또는 **모두 선택**을 클릭하여 사용 가능한 모든 운영 체제에 메일 프로필을 설치합니다.  

2.  마법사를 마칩니다.

Exchange ActiveSync 메일 프로필을 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)를 참조하세요.  
