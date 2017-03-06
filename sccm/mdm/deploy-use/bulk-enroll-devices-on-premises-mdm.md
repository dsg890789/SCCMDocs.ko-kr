---

title: "장치 대량 등록 | Microsoft 문서 | 온-프레미스 MDM"
description: "System Center Configuration Manager에서 온-프레미스 모바일 장치 관리를 사용하여 자동화된 방법으로 장치를 대량 등록합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b36f5e4a-2b57-4d18-83f6-197081ac2a0a
caps.latest.revision: 13
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 0d6479bcc134103e6005159a8ea295a5f359a436
ms.openlocfilehash: ef68a9f998ea6ff9628e01f6ac622711de68375d
ms.lasthandoff: 12/16/2016


---
# <a name="how-to-bulk-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 온-프레미스 모바일 장치 관리를 사용하여 장치를 대량 등록하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager 온-프레미스 모바일 장치 관리에서의 대량 등록은 사용자가 장치를 등록하기 위해 자격 증명을 입력해야 하는 사용자 등록에 비해 더 자동화된 장치 등록 방법입니다.  대량 등록은 등록 패키지를 사용하여 등록 중에 장치를 인증합니다. 패키지(.ppkg 파일)에는 인증서 프로필이 포함되어 있으며, 장치가 등록을 지원하기 위해 인트라넷에 연결할 수 있어야 하는 경우 필요에 따라 Wi-Fi 프로필이 포함되어 있습니다.  

 > [!NOTE]  
>  현재 분기의 Configuration Manager는 다음 운영 체제를 실행하는 장치에 대한 온-프레미스 모바일 장치 관리에서의 등록을 지원합니다.  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team\(Configuration Manager 버전 1602 이상\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise

다음 작업에서는 온\-프레미스 모바일 장치 관리에 대해 컴퓨터 및 장치를 대량 등록하는 방법을 설명합니다.  

-   [인증서 프로필 만들기](#bkmk_createCert)  

-   [Wi-Fi 프로필 만들기](#CreateWifi)  

-   [등록 프로필 만들기](#bkmk_createEnroll)  

-   [등록 패키지(ppkg) 파일 만들기](#bkmk_createPpkg)  

-   [패키지를 사용하여 장치 대량 등록](#bkmk_getPpkg)  

-   [장치 등록 확인](#bkmk_verifyEnroll)  

##  <a name="a-namebkmkcreatecerta-create-a-certificate-profile"></a><a name="bkmk_createCert"></a> 인증서 프로필 만들기  
 등록 패키지의 주요 구성 요소는 등록하는 장치에 신뢰할 수 있는 루트 인증서를 자동으로 프로비전하는 데 사용되는 인증서 프로필입니다.  이 루트 인증서는 장치와 온\-프레미스 모바일 장치 관리에 필요한 사이트 시스템 역할 간의 신뢰할 수 있는 통신에 필요합니다. 루트 인증서가 없으면 장치는 해당 장치와 등록 지점, 등록 프록시 지점, 배포 지점 및 장치 관리 지점 사이트 시스템 역할을 호스트하는 서버 간의 HTTPS 연결에서 신뢰되지 않습니다.  

 온\-프레미스 모바일 장치 관리에 대한 시스템 준비 과정의 일부로 등록 패키지의 인증서 프로필에서 사용할 수 있는 루트 인증서를 내보냅니다. 신뢰할 수 있는 루트 인증서를 가져오는 방법에 대한 지침은 [웹 서버 인증서와 동일한 루트를 가진 인증서 내보내기](../../mdm/get-started/set-up-certificates-on-premises-mdm.md#bkmk_exportCert)를 참조하세요.  

 내보낸 루트 인증서를 사용하여 인증서 프로필을 만듭니다. 자세한 지침은 [System Center Configuration Manager에서 인증서 프로필을 만드는 방법](../../protect/deploy-use/create-certificate-profiles.md)을 참조하세요.  

##  <a name="a-namecreatewifia-create-a-wi-fi-profile"></a><a name="CreateWifi"></a> Wi-Fi 프로필 만들기  
 대량 등록에 사용 되는 패키지의 다른 구성 요소는 Wi-Fi 프로필입니다. 일부 장치에는 네트워크 설정이 프로비전될 때까지 등록을 지원하는 데 필요한 네트워크 연결이 없을 수 있습니다. 등록 패키지에 Wi-Fi 프로필을 포함하면 장치에 대한 네트워크 연결을 설정할 수 있게 됩니다.  

 Configuration Manager에서 Wi-Fi 프로필을 만들려면 [System Center Configuration Manager에서 Wi-Fi 프로필을 만드는 방법](../../protect/deploy-use/create-wifi-profiles.md)에 대한 지침을 따르세요.  

> [!IMPORTANT]  
>대량 등록을 위해 Wi-Fi 프로필을 만들 때 다음 두 가지 문제를 고려하세요.
>
> - 현재 분기의 Configuration Manager에서는 온\-프레미스 모바일 장치 관리에 대한 다음 Wi-Fi 보안 구성만 지원합니다.  
>   
>   - 보안 유형: **WPA2 엔터프라이즈** 또는 **WPA2 개인**  
>   - 암호화 유형: **AES** 또는 **TKIP**  
>   - EAP 유형: **스마트 카드 또는 기타 인증서** 또는 **PEAP**  
>
>
> - Configuration Manager는 Wi-Fi 프로필에 프록시 서버 정보용 설정이 있지만 장치가 등록되면 프록시를 구성하지 않습니다. 등록된 장치에 프록시 서버를 설정해야 하는 경우 장치가 등록된 후 구성 항목을 사용하여 설정을 배포하거나 대량 등록 패키지와 함께 배포하도록 Windows ICD(이미지 및 구성 디자이너)를 사용하여 두 번째 패키지를 만들 수 있습니다.

##  <a name="a-namebkmkcreateenrolla-create-an-enrollment-profile"></a><a name="bkmk_createEnroll"></a> 등록 프로필 만들기  
 등록 프로필을 사용하면 장치에 신뢰할 수 있는 루트 인증서를 동적으로 프로비전하는 인증서 프로필과 필요한 경우 네트워크 설정을 프로비전하는 Wi-Fi 프로필을 포함하여 장치 등록에 필요한 설정을 지정할 수 있습니다.  

 등록 프로필을 만들기 전에 인증서 프로필 및 Wi-Fi 프로필(필요한 경우)을 만들었는지 확인합니다. 자세한 내용은 [인증서 프로필 만들기](#bkmk_createCert) 및 [Wi-Fi 프로필 만들기](#CreateWifi)항목을 참조하세요.  

#### <a name="to-create-an-enrollment-profile"></a>등록 프로필을 만들려면  

1.  Configuration Manager 콘솔에서 **자산 및 준수** >**개요** >**모든 회사 소유 장치** >**Windows** >**등록 프로필**을 클릭합니다.  

2.  **등록 프로필** 을 마우스 오른쪽 단추로 클릭하고 **프로필 만들기**를 클릭합니다.  

3.  등록 프로필 만들기 마법사에서 프로필의 이름을 입력하고 **관리 기관** 에 대해 **온-프레미스**를 선택한 후 **다음**을 클릭합니다.  

4.  사이트 코드를 선택하고 **다음**을 클릭합니다.  

5.  **인트라넷만**을 선택하고 장치가 등록 프로세스를 시작하는 데 사용하는 등록 프록시 지점을 선택한 후 **다음**을 클릭합니다.  

6.  신뢰할 수 있는 루트 인증서가 포함된 인증서 프로필( [Create a certificate profile](#bkmk_createCert)에서 만든 프로필)을 선택한 후 **다음**을 클릭합니다.  

7.  장치가 인트라넷에 연결하는 데 필요한 네트워크 설정이 포함된 W-Fi 프로필( [Create a Wi-Fi profile](#CreateWifi)에서 만든 프로필)을 선택하고 **다음**을 클릭합니다.  

    > [!NOTE]  
    >  등록 패키지에 대해 Wi-Fi 프로필을 사용하지 않는 경우 이 단계를 건너뜁니다.  

8.  등록 프로필에 대한 설정을 확인하고 **다음**을 클릭합니다. 마법사를 종료하려면 **닫기** 를 클릭합니다.  

##  <a name="a-namebkmkcreateppkga-create-an-enrollment-package-ppkg-file"></a><a name="bkmk_createPpkg"></a> 등록 패키지(ppkg) 파일 만들기  
 등록 패키지는 온\-프레미스 모바일 장치 관리에 대해 장치를 대량 등록하는 데 사용하는 파일입니다.  이 파일은 Configuration Manager를 사용하여 만들어야 합니다. Windows ICD(이미지 및 구성 디자이너)를 사용하여 비슷한 유형의 패키지를 만들 수 있지만, Configuration Manager에서 만드는 패키지만 온\-프레미스 모바일 장치 관리에 대해 장치를 등록하는 데 처음부터 끝까지 사용할 수 있습니다. Windows ICD로 만든 패키지는 등록에 필요한 UPN(사용자 계정 이름)만 제공하며 실제 등록 프로세스는 실행할 수 없습니다.  

 등록 패키지를 만드는 프로세스에는 Windows 10용 Windows ADK(평가 및 배포 도구 키트)가 필요합니다.  Configuration Manager 콘솔을 실행 중인 서버에서 Windows ADK 버전 1511이 설치되어 있는지 확인합니다. 자세한 내용은 [Windows 10용 키트 및 도구 다운로드](https://msdn.microsoft.com/windows/hardware/dn913721.aspx)의 ADK 섹션을 참조하세요.  

> [!TIP]  
>  Configuration Manager 콘솔에서 등록 패키지를 제거하면 장치를 등록하는 데 사용할 수 없습니다. 더 이상 장치 대량 등록에 사용하지 않으려는 패키지를 관리하는 방법으로 패키지 제거를 사용할 수 있습니다.  

#### <a name="to-create-an-enrollment-package-ppkg-file"></a>등록 패키지(ppkg) 파일을 만들려면  

1.  방금 만든 프로필( [등록 프로필 만들기](#bkmk_createEnroll))을 마우스 오른쪽 단추로 클릭하고 **내보내기**를 클릭합니다.  

2.  	**찾아보기**를 클릭하고 .ppkg 파일을 저장할 위치를 찾은 후 패키지 이름을 입력한 다음 **저장**을 클릭합니다.  

3.  패키지를 암호로 보호하려는 경우 **패키지 암호화**옆의 확인란을 클릭하고 **내보내기** 를 클릭한 다음 내보내기가 완료될 때까지 10초 정도 기다립니다.  

    > [!NOTE]  
    >  패키지를 암호화한 경우 Configuration Manager에서 해독된 암호가 있는 메시지를 제공합니다. 장치에 패키지를 프로비전하는 데 필요하기 때문에 암호 정보를 저장해야 합니다.  

4.  **확인**을 클릭합니다.  

##  <a name="a-namebkmkgetppkga-use-the-package-to-bulk-enroll-a-device"></a><a name="bkmk_getPpkg"></a> 패키지를 사용하여 장치 대량 등록  
 OOBE(첫 실행 경험) 프로세스를 통해 장치가 프로비전되기 전이나 후에 패키지를 사용하여 장치를 등록할 수 있습니다.   등록 패키지를 OEM 프로비저닝 패키지의 일부로 포함할 수도 있습니다.  

 대량 등록에 사용하려면 해당 패키지를 장치에 물리적으로 전달해야 합니다. 다음을 비롯한 사용자 요구에 따라 다양한 방법으로 장치에 등록 패키지를 전달할 수 있습니다.  

-   파일 시스템에서 복사  

-   메일에 첨부  

-   NFC(근거리 통신) 연결을 통해 복사  

-   메모리 카드에서 복사  

-   바코드 스캔  

-   테더링된 장치에서 복사  

-   OEM 프로비저닝 패키지에 포함  

#### <a name="to-bulk-enroll-a-device"></a>장치를 대량 등록하려면  

1.  등록할 장치에서 파일 탐색기를 사용하여 등록 패키지를 찾은 후 .ppkg 파일을 두 번 클릭합니다.  

2.  사용자 계정 컨트롤 창에서 **예** 를 클릭합니다.  

3.  패키지가 신뢰할 수 있는 원본인지 묻는 대화 상자에서 **예, 추가**를 클릭합니다.  

     등록 프로세스가 시작되고 약 5분이 걸립니다.  

4.  **설정**을 엽니다.  

5.  마법사를 종료하려면  **계정** > **회사 액세스**에 필요한 사이트 시스템 역할 간의 신뢰할 수 있는 통신에 필요합니다. 계정이 등록되면 **CompanyApps**아래에 계정이 표시됩니다.  

6.  계정을 클릭한 다음 **동기화**를 클릭하여 Configuration Manager를 사용한 관리를 시작합니다.  

##  <a name="a-namebkmkverifyenrolla-verify-enrollment-of-device"></a><a name="bkmk_verifyEnroll"></a> 장치 등록 확인  
 Configuration Manager 콘솔에서 장치가 성공적으로 등록되었는지 확인할 수 있습니다.  

-   Configuration Manager 콘솔을 시작합니다.  

-   마법사를 종료하려면 **자산 및 준수** > **개요** > **장치**에 필요한 사이트 시스템 역할 간의 신뢰할 수 있는 통신에 필요합니다. 등록된 장치가 목록에 표시됩니다.  

