---
title: "PFX 인증서 프로필 만들기 | System Center Configuration Manager"
description: "System Center Configuration Manager에서 PFX 파일을 사용하여 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성하는 방법을 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0185ab18-663d-468a-ba54-4f3f232fd4d2
caps.latest.revision: 5
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 4a4025325e635061cb99caed9cdb07390e90ea90


---
# <a name="how-to-create-pfx-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 PFX 인증서 프로필을 만드는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager에서는 사용자 장치에 개인 정보 교환(.pfx) 파일을 프로비전할 수 있습니다. PFX 파일을 사용하면 암호화된 데이터 교환을 지원하기 위한 사용자별 인증서를 생성할 수 있습니다. PFX 인증서는 Configuration Manager 내에서 만들 수도 있고 가져올 수도 있습니다. System Center Configuration Manager를 사용하면 가져오거나 새로 만든 PFX 인증서를 iOS, Android 및 Windows 10 장치로 배포할 수 있습니다. 그런 후에 사용자 기반 PKI 통신을 지원하기 위해 이러한 파일을 여러 장치로 배포할 수 있습니다.  

> [!TIP]  
>  이 프로세스를 설명하는 단계별 연습은 [PFX 인증서 프로필을 Configuration Manager에서 만들고 배포하는 방법](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx)에서 제공됩니다.  

## <a name="create-and-deploy-personal-information-exchange-pfx-certificate-profiles"></a>PFX(개인 정보 교환) 인증서 프로필 만들기 및 배포  

#### <a name="how-to-create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>PFX(개인 정보 교환) 인증서 프로필을 만들고 배포하는 방법  

1.  System Center Configuration Manager 콘솔에서 **자산 및 준수**를 클릭합니다.  

2.  **자산 및 호환성** 작업 영역에서 **호환성 설정**및 **회사 리소스 액세스**를 각각 확장하고 **인증서 프로필**을 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **인증서 프로필 만들기**를 클릭합니다. **인증서 프로필 만들기** 마법사가 열립니다.  

4.  **인증서 프로필 만들기** 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름**: 인증서 프로필의 고유한 이름을 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    -   **설명**: 인증서 프로필에 대한 개략적인 정보를 제공하는 설명과 System Center Configuration Manager 콘솔에서 해당 프로필을 식별하는 데 도움이 되는 기타 관련 정보를 입력합니다. 최대 256자까지 사용할 수 있습니다.  

    -   **만들려는 인증서 프로필의 유형을 지정합니다.**: 다음 인증서 프로필 유형 중 하나를 선택합니다.  

        -   **신뢰할 수 있는 CA 인증서**: 사용자 또는 장치가 다른 장치를 인증해야 할 때 신뢰할 수 있는 루트 CA(인증 기관) 또는 중간 CA 인증서를 배포하여 인증서 신뢰 체인을 형성하려는 경우 이 인증서 프로필 유형을 선택합니다. 예를 들어 장치가 RADIUS(Remote Authentication Dial-In User Service) 서버 또는 VPN(가상 사설망) 서버일 수 있습니다. 또한 SCEP 인증서 프로필을 만들려면 먼저 신뢰할 수 있는 CA 인증서 프로필을 구성해야 합니다. 이러한 경우 신뢰할 수 있는 CA 인증서는 사용자 또는 장치에 인증서를 발급하는 CA(인증 기관)의 신뢰할 수 있는 루트 인증서여야 합니다.  

        -   **SCEP(단순 인증서 등록 프로토콜) 설정**: 단순 인증서 등록 프로토콜 및 네트워크 장치 등록 서비스 역할 서비스를 사용하여 장치 또는 사용자의 인증서를 요청하려면 이 인증서 프로필 유형을 선택합니다.  

        -   **개인 정보 교환 PKCS #12(PFX) 설정 가져오기**: PFX 인증서를 가져오려면 이 옵션을 선택합니다.  

5.  대상 장치에서 PFX 인증서를 저장할 위치를 **인증서 프로필 만들기** 마법사의 **인증서 속성** 창에서 지정합니다.  

    -   **있는 경우 TPM(신뢰할 수 있는 플랫폼 모듈)에 설치**  

    -   **TPM(신뢰할 수 있는 플랫폼 모듈)에 설치, 그렇지 않으면 실패**  

    -   **소프트웨어 키 저장소 공급자에 설치**  

     **다음**을 클릭합니다.  

6.  **인증서 프로필 만들기** 마법사의 **지원되는 플랫폼** 창에서 가져온 PFX 파일을 받을 수 있는 운영 체제나 플랫폼을 지정합니다.  

    -   **Windows 10**  

    -   **iPhone**  

    -   **iPad**  

    -   **Android**  

7.  **다음**을 클릭하고 **요약** 페이지를 검토한 후에 마법사를 닫습니다.  

8.  이제 PFX 파일을 포함하는 인증 프로필을 **인증서 프로필** 작업 영역에서 사용할 수 있습니다.  **자산 및 호환성** 작업 영역에서 **호환성 설정** > **회사 리소스 액세스** > **인증서 프로필** 로 이동한 다음 마우스 오른쪽 단추를 클릭하여 새 인증서를 사용자 컬렉션에 배포합니다.  

9. 다운로드 센터([http://go.microsoft.com/fwlink/?LinkId=613525](http://go.microsoft.com/fwlink/?LinkId=613525))에서 제공되는 Windows 8.1용 SDK를 사용하여 PFX 만들기 스크립트를 배포합니다. Configuration Manager 2012 SP2에 추가된 PFX 만들기 스크립트는 SDK에 SMS_ClientPfxCertificate 클래스를 추가합니다. 이 클래스는 다음 메서드를 포함합니다.  

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

    -   <blob\>> = PFX base64로 암호화된 Blob  

    -   $Password = PFX 파일의 암호  

    -   $ProfileName = PFX 프로필의 이름  

    -   ComputerName = 호스트 컴퓨터의 이름  



<!--HONumber=Nov16_HO1-->


