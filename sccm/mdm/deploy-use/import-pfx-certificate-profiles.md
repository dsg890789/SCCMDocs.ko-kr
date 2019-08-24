---
title: 인증서 세부 정보를 가져와 PFX 인증서 프로필 만들기
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 PFX 파일을 사용하여 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성하는 방법을 알아봅니다.
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 18879c37bf51adda20dd1cf7bb7a52960312951d
ms.sourcegitcommit: 79c51028f90b6966d6669588f25e8233cf06eb61
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68338040"
---
# <a name="how-to-create-pfx-certificate-profiles-by-importing-certificate-details"></a>인증서 세부 정보를 가져와 PFX 인증서 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


여기서 외부 인증서의 자격 증명을 가져와 인증서 프로필을 만드는 방법을 알아봅니다.  

[인증서 프로필](../../protect/deploy-use/introduction-to-certificate-profiles.md)에서는 인증서 프로필을 만들고 구성하는 방법에 대한 일반적인 내용을 소개합니다. 이 항목에서는 PFX 인증서와 관련된 인증서 프로필에 대한 몇 가지 특정 정보를 중점적으로 설명합니다.

- Configuration Manager는 다양한 디바이스 및 운영 체제에 적합한 여러 인증서 저장소를 제공합니다.  이러한 개체는 다음과 같습니다.

  - iOS 및 MacOS/OSX
  - Android 및 Android for Work
  - Windows 10(Windows 10 모바일 포함)

자세한 내용은 [인증서 프로필 필수 조건](../../protect/plan-design/prerequisites-for-certificate-profiles.md)을 참조하세요.

## <a name="pfx-certificate-profiles"></a>PFX 인증서 프로필
System Center Configuration Manager를 통해 인증서 자격 증명을 가져온 다음 개인 정보 교환(.pfx) 파일을 사용자 디바이스에 프로비전할 수 있습니다. PFX 파일을 사용하면 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성할 수 있습니다.

> [!TIP]  
> 이 프로세스를 설명하는 단계별 연습은 [PFX 인증서 프로필을 Configuration Manager에서 만들고 배포하는 방법](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx)에서 제공됩니다.  

## <a name="create-import-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>PFX(개인 정보 교환) 인증서 프로필 만들기, 가져오기 및 배포  

### <a name="get-started"></a>시작

1.  System Center Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  
2.  **자산 및 호환성** 작업 영역에서 **호환성 설정**및 **회사 리소스 액세스**를 각각 확장하고 **인증서 프로필**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **인증서 프로필 만들기**를 클릭합니다.

4.  **인증서 프로필 만들기** 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    - **이름**: 인증서 프로필의 고유한 이름을 입력 합니다. 최대 256자까지 사용할 수 있습니다.  

    - **설명**: 인증서 프로필에 대한 개략적인 정보를 제공하는 설명과 System Center Configuration Manager 콘솔에서 해당 프로필을 식별하는 데 도움이 되는 기타 관련 정보를 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    - **만들려는 인증서 프로필 유형 지정**: PFX 인증서의 경우 다음 옵션 중 하나를 선택 합니다.  

      - **개인 정보 교환 PKCS #12(PFX) 설정 – 가져오기**: 기존 인증서에서 프로그래밍 방식으로 정보를 가져와 인증서 프로필을 만듭니다.  

      - **개인 정보 교환-PKCS #12 (PFX) 설정-만들기**: 인증 기관에서 제공 하는 자격 증명을 사용 하 여 PFX 인증서 프로필을 만듭니다.  자세한 내용은 [인증 기관을 사용하여 PFX 인증서 프로필을 만드는 방법](../../mdm/deploy-use/create-pfx-certificate-profiles.md)을 참조하세요.


### <a name="create-a-pfx-certificate-profile-for-the-imported-credentials"></a>가져온 자격 증명에 대한 PFX 인증서 프로필 만들기

PFX 인증서를 가져오려면 Configuration Manager SDK를 사용하여 PFX 만들기 스크립트를 배포합니다. 

가져온 인증서는 등록된 디바이스에 나중에 배포됩니다.

1. **인증서 프로필 만들기 마법사**의 **PFX 인증서** 페이지에서 디바이스 키 스토리지 공급자의 위치를 지정합니다.
    - **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
    - **TPM(신뢰할 수 있는 플랫폼 모듈)에 설치, 그렇지 않으면 실패** 
    - **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패** 
    - **소프트웨어 키 스토리지 공급자에 설치** 
2. **다음**을 클릭합니다. 
3. 마법사의 **지원되는 플랫폼** 페이지에서 지원되는 디바이스 플랫폼을 선택하고 **다음**을 클릭합니다.

### <a name="finish-the-profile"></a>프로필 완료

1.  **다음**을 클릭하고 **요약** 페이지를 검토한 후에 마법사를 닫습니다.  
2.  이제 PFX 파일을 포함하는 인증 프로필을 **인증서 프로필** 작업 영역에서 사용할 수 있습니다. 
3.  프로필을 배포하려면 **자산 및 준수** 작업 영역에서 **준수 설정** > **회사 리소스 액세스** > **인증서 프로필**을 열고, 원하는 인증서를 마우스 오른쪽 단추로 클릭하고, **배포**를 클릭합니다. 

### <a name="deploy-a-create-pfx-script"></a>PFX 만들기 스크립트 배포

[Configuration Manager SDK](http://go.microsoft.com/fwlink/?LinkId=613525)를 사용하여 PFX 만들기 스크립트를 배포합니다. 

Configuration Manager 2012 SP2에 추가된 PFX 만들기 스크립트는 SDK에 SMS_ClientPfxCertificate 클래스를 추가합니다. 이 클래스는 다음 메서드를 포함합니다.  

- `ImportForUser`  

- `DeleteForUser`  

다음 예제에서는 PFX 인증서 프로필에 자격 증명을 가져옵니다.

``` powershell
    $EncryptedPfxBlob = "<blob>"  
    $Password = "abc"  
    $ProfileName = "PFX_Profile_Name"  
    $UserName = "ComputerName\Administrator"  

    #New pfx  
    $WMIConnection = ([WMIClass]"\\nksccm\root\SMS\Site_MDM:SMS_ClientPfxCertificate")  
        $NewEntry = $WMIConnection.psbase.GetMethodParameters("ImportForUser")  
        $NewEntry.EncryptedPfxBlob = $EncryptedPfxBlob  
        $NewEntry.Password = $Password  
        $NewEntry.ProfileName = $ProfileName  
        $NewEntry.UserName = $UserName  
    $Resource = $WMIConnection.psbase.InvokeMethod("ImportForUser",$NewEntry,$null)  
```  

이 예제를 사용하려면 다음 스크립트 변수를 업데이트합니다.  

- **blob**\ - PFX base64로 암호화된 Blob  
- **$Password** - PFX 파일의 암호  
- **$ProfileName** - PFX 프로필의 이름  
- **ComputerName** - 호스트 컴퓨터의 이름   

## <a name="see-also"></a>참고자료
[새 인증서 프로필 만들기](../../protect/deploy-use/create-certificate-profiles.md)에서는 인증서 프로필 만들기 마법사를 단계별로 안내합니다.

[인증서 세부 정보를 가져와 PFX 인증서 프로필을 만드는 방법](../../mdm/deploy-use/create-pfx-certificate-profiles.md)

[Wi-Fi, VPN, 메일 및 인증서 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)에서는 인증서 프로필 배포 방법을 설명합니다.
