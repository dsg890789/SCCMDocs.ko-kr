---
title: "PFX 인증서 프로필 만들기 | Microsoft 문서"
description: "System Center Configuration Manager에서 PFX 파일을 사용하여 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: 27435316c6e47531ff989bc8956ca0c874131a0e
ms.contentlocale: ko-kr
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-pfx-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 PFX 인증서 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

인증서 프로필은 사용자가 회사 리소스에 원활하게 액세스할 수 있도록 Active Directory 인증서 서비스 및 네트워크 장치 등록 서비스 역할과 연동하여 관리되는 장치에 인증 인증서를 프로비전합니다. 예를 들어, 인증서 프로필을 만들고 배포하여 사용자가 VPN 및 무선 연결을 시작하는 데 필요한 인증서를 제공할 수 있습니다.

[인증서 프로필](../../protect/deploy-use/introduction-to-certificate-profiles.md)에서는 인증서 프로필을 만들고 구성하는 방법에 대한 일반적인 내용을 소개합니다. 이 항목에서는 PFX 인증서와 관련된 인증서 프로필에 대한 몇 가지 특정 정보를 중점적으로 설명합니다.

-  Configuration Manager에서는 요구 사항, 장치 유형 및 운영 체제에 따라 여러 인증서 저장소에 인증서를 배포할 수 있습니다. 다음 장치는 Intune에 등록된 경우 지원됩니다.

 -   iOS  

- 다른 필수 구성 요소는 [인증서 프로필 필수 구성 요소](../../protect/plan-design/prerequisites-for-certificate-profiles.md)를 참조하세요.

## <a name="pfx-certificate-profiles"></a>PFX 인증서 프로필
System Center Configuration Manager를 통해 개인 정보 교환(.pfx) 파일을 가져온 다음 사용자 장치에 프로비전할 수 있습니다. PFX 파일을 사용하면 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성할 수 있습니다.

> [!TIP]  
>  이 프로세스를 설명하는 단계별 연습은 [PFX 인증서 프로필을 Configuration Manager에서 만들고 배포하는 방법](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx)에서 제공됩니다.  

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>PFX(개인 정보 교환) 인증서 프로필 만들기 및 배포  

### <a name="get-started"></a>시작

1.  System Center Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  

2.  **자산 및 호환성** 작업 영역에서 **호환성 설정**및 **회사 리소스 액세스**를 각각 확장하고 **인증서 프로필**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **인증서 프로필 만들기**를 클릭합니다.

4.  **인증서 프로필 만들기** 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름**: 인증서 프로필의 고유한 이름을 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    -   **설명**: 인증서 프로필에 대한 개략적인 정보를 제공하는 설명과 System Center Configuration Manager 콘솔에서 해당 프로필을 식별하는 데 도움이 되는 기타 관련 정보를 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    -   **만들려는 인증서 프로필의 유형 지정**: PFX 인증서의 경우 다음을 선택합니다.  

        -   **개인 정보 교환 PKCS #12(PFX) 설정 - 가져오기**: PFX 인증서를 가져오려면 이 옵션을 선택합니다.  
       

### <a name="import-a-pfx-certificate"></a>PFX 인증서 가져오기

PFX 인증서를 가져오려면 Configuration Manager SDK가 필요합니다. 사용자를 위해 가져오는 모든 인증서는 사용자가 등록하는 모든 장치에 배포됩니다.

1. **인증서 프로필 만들기** 마법사의 **PFX 인증서** 페이지에서 인증서를 배포할 장치에서 인증서를 저장할 위치를 지정합니다.
    -     **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  
    -   **TPM(신뢰할 수 있는 플랫폼 모듈)에 설치, 그렇지 않으면 실패** 
    -   **비즈니스용 Windows Hello에 설치, 그러지 않으면 실패** 
    -   **소프트웨어 키 저장소 공급자에 설치** 
2. **다음**을 클릭합니다. 
3. 마법사의 **지원되는 플랫폼** 페이지에서 이 인증서를 설치할 장치 플랫폼을 선택하고 **다음**을 클릭합니다.
4. 다운로드 센터([http://go.microsoft.com/fwlink/?LinkId=613525](http://go.microsoft.com/fwlink/?LinkId=613525))에서 제공되는 Windows 8.1용 SDK를 사용하여 PFX 만들기 스크립트를 배포합니다. Configuration Manager 2012 SP2에 추가된 PFX 만들기 스크립트는 SDK에 SMS_ClientPfxCertificate 클래스를 추가합니다. 이 클래스는 다음 메서드를 포함합니다.  

    -   ImportForUser  

    -   DeleteForUser  

     샘플 스크립트:  

```  
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

다음 스크립트 변수는 실제로 사용하는 스크립트에 맞게 수정해야 합니다.  

   -   blob\ = PFX base64로 암호화된 Blob  
   -   $Password = PFX 파일의 암호  
   -   $ProfileName = PFX 프로필의 이름  
   -   ComputerName = 호스트 컴퓨터의 이름   



### <a name="finish-up"></a>끝내기

1.  **다음**을 클릭하고 **요약** 페이지를 검토한 후에 마법사를 닫습니다.  
2.  이제 PFX 파일을 포함하는 인증 프로필을 **인증서 프로필** 작업 영역에서 사용할 수 있습니다. 
3.  프로필을 배포하려면 **자산 및 준수** 작업 영역에서 **준수 설정** > **회사 리소스 액세스** > **인증서 프로필**을 열고, 원하는 인증서를 마우스 오른쪽 단추로 클릭하고, **배포**를 클릭합니다. 



## <a name="see-also"></a>참고 항목
[새 인증서 프로필 만들기](../../protect/deploy-use/create-certificate-profiles.md#create-a-new-certificate-profile)에서는 인증서 프로필 만들기 마법사를 단계별로 안내합니다.

[Wi-Fi, VPN, 메일 및 인증서 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)에서는 인증서 프로필 배포에 대한 정보를 제공합니다.
