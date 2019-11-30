---
title: PFX 인증서 프로필 가져오기
titleSuffix: Configuration Manager
description: Configuration Manager에서 PFX 파일을 사용 하 여 암호화 된 데이터 교환을 지 원하는 사용자 관련 인증서를 생성 하는 방법에 대해 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: c6b0867f5f872eacb52d5e0e3faaffdfd7dae761
ms.sourcegitcommit: 2f34d9457d95a9bd25603699fcf0e26cac77ad30
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/29/2019
ms.locfileid: "74659496"
---
# <a name="import-pfx-certificate-profiles"></a>PFX 인증서 프로필 가져오기

*적용 대상: Configuration Manager (현재 분기)*

외부 인증서에서 자격 증명을 가져와서 인증서 프로필을 만드는 방법에 대해 알아봅니다. 이 문서에서는 PFX (개인 정보 교환) 인증서 프로필에 대 한 특정 정보를 강조 표시 합니다. 이러한 프로필을 만들고 구성 하는 방법에 대 한 자세한 내용은 [인증서 프로필](/configmgr/protect/deploy-use/introduction-to-certificate-profiles)을 참조 하세요.

Configuration Manager는 다양 한 장치 및 OS 버전에 대 한 다양 한 종류의 인증서 저장소를 지원 합니다. 예를 들어 Windows 10 및 Windows 10 Mobile입니다. 자세한 내용은 [인증서 프로필 필수 조건](/configmgr/protect/plan-design/prerequisites-for-certificate-profiles)을 참조 하세요.

Configuration Manager를 사용 하 여 인증서 자격 증명을 가져온 다음 장치에 PFX 파일을 프로 비전 합니다. 이러한 파일을 사용 하 여 암호화 된 데이터 교환을 지원 하기 위한 사용자별 인증서를 생성할 수 있습니다.

> [!TIP]  
> 이 프로세스의 단계별 연습에 대해서는 블로그 게시물 [Configuration Manager에서 PFX 인증서 프로필을 만들고 배포 하는 방법](https://blogs.technet.microsoft.com/karanrustagi/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager/)을 참조 하세요.  

## <a name="create-a-profile"></a>프로필 만들기

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **준수 설정**, **회사 리소스 액세스**를 차례로 확장 한 다음 **인증서 프로필**을 선택 합니다.

1. 리본 메뉴의 **홈** 탭에 있는 **만들기** 그룹에서 **인증서 프로필 만들기**를 선택 합니다.

1. **인증서 프로필 만들기 마법사**의 **일반** 페이지에서 다음 정보를 지정 합니다.  

    - **이름**: 인증서 프로필의 고유한 이름을 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    - **설명**: Configuration Manager 콘솔에서 식별 하는 데 도움이 되는 인증서 프로필의 개요를 제공 하는 설명을 제공 합니다. 최대 256자까지 사용할 수 있습니다.  

1. **개인 정보 교환-PKCS #12 (PFX) 설정-가져오기**를 선택 합니다. 이 옵션은 기존 인증서의 정보를 가져와 인증서 프로필을 만듭니다.

    > [!NOTE]
    > **만들기** 옵션은 연결 된 온-프레미스 CA (인증 기관)에서 사용자를 대신 하 여 인증서를 요청 합니다. 그런 다음이 프로세스는 인증서를 PFX 파일로 클라이언트에 안전 하 게 전달 합니다. 자세한 내용은 [인증 기관을 사용 하 여 PFX 인증서 프로필 만들기](/configmgr/mdm/deploy-use/create-pfx-certificate-profiles)를 참조 하세요.

1. **인증서 프로필 만들기 마법사**의 **PFX 인증서** 페이지에서 장치 KSP (키 저장소 공급자)를 지정 합니다.

    - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
    - **신뢰할 수 있는 플랫폼 모듈 (TPM)에 설치, 그렇지 않으면 실패**
    - **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패**
    - **소프트웨어 키 스토리지 공급자에 설치**

1. **지원 되는 플랫폼** 페이지에서 지원 되는 장치 플랫폼을 선택 합니다.

1. 마법사 완료

## <a name="deploy-the-profile"></a>프로필 배포

인증서 프로필을 만들고 프로 비전 한 후에는 **인증서** 프로필 노드에서 사용할 수 있습니다. 배포 하는 방법에 대 한 자세한 내용은 [리소스 액세스 프로필 배포](/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)를 참조 하세요.

## <a name="assign-primary-users"></a>기본 사용자 할당

PFX 인증서를 설치 해야 하는 Windows 10 장치에서 대상 사용자를 기본 사용자로 할당 합니다. 자세한 내용은 [사용자 장치 선호도](/configmgr/apps/deploy-use/link-users-and-devices-with-user-device-affinity)를 참조 하세요.

## <a name="provision-a-create-pfx-script"></a>PFX 만들기 스크립트 프로 비전

PFX 인증서를 가져오려면 다음 Configuration Manager PowerShell cmdlet을 사용 하 여 PFX 만들기 스크립트를 프로 비전 합니다.

- [Get-CMClientCertificatePfx](https://docs.microsoft.com/powershell/module/configurationmanager/get-cmclientcertificatepfx?view=sccm-ps)
- [가져오기-CMClientCertificatePfx](https://docs.microsoft.com/powershell/module/configurationmanager/import-cmclientcertificatepfx?view=sccm-ps)
- [제거-CMClientCertificatePfx](https://docs.microsoft.com/powershell/module/configurationmanager/remove-cmclientcertificatepfx?view=sccm-ps)

### <a name="example-script"></a>예제 스크립트

사용자에 대 한 인증서 프로필에 PFX 파일을 프로 비전 하려면 Configuration Manager 콘솔을 사용 하 여 컴퓨터에서 PowerShell을 엽니다. 사용자 환경의 값으로 변수를 변경 합니다.

``` PowerShell
# The display name of your PFX Import certificate profile
$PfxProfileDisplayName = "ImportPFX"

# The password you used to protect/encrypt the external PFX file that was created/exported from your certificate storage provider
# If you omit this password, PowerShell will securely prompt you for it. You can specify it as a parameter for process automation.
$password = ""

# The username of the user who will receive this PFX certificate on their device
$user = "Melissa"

# The full path to the PFX file you exported from the certificate store
$pfxfile = "c:\p1.pfx"

# If the target user isn't in the same domain as the user running this script, specify a different domain
Import-CMClientCertificatePfx -UserName "$env:USERDOMAIN\$user" -Password (ConvertTo-SecureString -String $password -AsPlainText -Force) -CertificateProfilePfx (Get-CMCertificateProfilePfx -Fast -Name $PfxProfileDisplayName) -Path $pfxfile
```

## <a name="see-also"></a>참고 항목

[새 인증서 프로필 만들기](/configmgr/protect/deploy-use/create-certificate-profiles)

[인증 기관을 사용 하 여 PFX 인증서 프로필 만들기](/configmgr/mdm/deploy-use/create-pfx-certificate-profiles)

[Wi-Fi, VPN, 메일 및 인증서 프로필 배포](/configmgr/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles)
