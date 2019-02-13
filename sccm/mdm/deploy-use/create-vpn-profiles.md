---
title: VPN 프로필
titleSuffix: Configuration Manager
description: Configuration Manager의 모바일 디바이스 VPN 프로필에 대해 자세히 알아보세요.
ms.date: 06/12/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 45388103-2410-4c7e-b4cf-73a1bda485fc
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7accfe4c329b61c7791bc4b82028d48fdc81931
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56122625"
---
# <a name="vpn-profiles-on-mobile-devices-in-system-center-configuration-manager"></a>System Center Configuration Manager의 모바일 디바이스에 대한 VPN 프로필

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager의 VPN 프로필을 사용하여 조직의 모바일 디바이스 사용자에게 VPN 설정을 배포할 수 있습니다. 이러한 설정을 배포할 때 최종 사용자가 회사 네트워크에 있는 리소스에 연결하는 데 필요한 노력을 최소화할 수 있습니다.  

예를 들어 모든 iOS 디바이스가 기업 네트워크의 파일 공유에 연결하도록 설정할 수 있습니다. 필요한 연결 설정이 포함된 VPN 프로필을 만듭니다. 그런 다음, iOS 디바이스를 소유한 모든 사용자에게 이 프로필을 배포합니다. 이러한 사용자는 사용 가능한 네트워크 목록에서 VPN 연결이 보이며 이 네트워크에 간편하게 연결할 수 있습니다.  

VPN 프로필을 만들 경우 광범위한 보안 설정을 포함할 수 있습니다. 예를 들어 Configuration Manager 인증서 프로필을 사용하여 설정했던 서버 유효성 검사 및 클라이언트 인증용 인증서를 지정할 수 있습니다. 자세한 내용은 [인증서 프로필](../../protect/deploy-use/introduction-to-certificate-profiles.md)을 참조하세요.  



## <a name="vpn-profiles-when-using-configuration-manager-together-with-intune"></a>Configuration Manager 및 Intune을 사용하는 경우의 VPN 프로필

iOS, Android, Windows Phone 및 Windows 8.1 디바이스에 프로필을 배포하려면 디바이스를 Microsoft Intune에 등록해야 합니다. 다른 플랫폼의 디바이스를 Intune에 등록할 수도 있습니다. 등록하는 방법에 대한 자세한 내용은 [Microsoft Intune에서 디바이스 등록](/intune/device-enrollment)을 참조하세요. 

이 표에서는 각 디바이스 플랫폼에 대해 지원되는 연결 형식을 보여 줍니다.  

 |연결 유형|iOS 및 macOS X|Android|Windows 8.1|Windows RT|Windows RT 8.1|Windows Phone 8.1|Windows 10 Desktop 및 Mobile|  
 |---------------|---------------|-------|-----------|----------|--------------|-----------------|-----------------------------|  
 |Cisco AnyConnect|예<sup>1</sup>|예|아니오|아니요|아니요|아니요|아니요|
 |Cisco(IPsec)|iOS에만 해당|아니요|아니요|아니요|아니요|아니요|아니요|  
 |Pulse Secure|예|예|예|아니요|예|예|예|  
 |F5 Edge Client|예|예|예|아니요|예|예|예|  
 |Dell SonicWALL Mobile Connect|예|예|예|아니요|예|예|예|  
 |검사점 모바일 VPN|예|예|예|아니요|예|예|예|  
 |Microsoft SSL(SSTP)|아니요|아니요|예|예|예|아니오|아니요|  
 |Microsoft 자동|아니요|아니요|예|예|예|아니요|예|  
 |IKEv2|예(사용자 지정 정책, iOS 9 이상)|아니요|예|예|예|예|예|  
 |PPTP|예|아니요|예|예|예|아니요|예|  
 |L2TP|예|아니요|예|예|예|아니요|예(OMA-URI)|  

<sup>1</sup> 1802 버전부터 Cisco AnyConnect 연결 형식 사용이 달라집니다.<!--1357393-->  
   - 다음 버전에서는 VPN 프로필에 **Cisco Legacy AnyConnect** 옵션을 사용하세요.
       - Cisco AnyConnect 버전 4.0.5 이하가 설치된 iOS
       - 아무 버전의 Cisco AnyConnect가 설치된 macOS
   - 다음 버전에서는 VPN 프로필에 **Cisco AnyConnect** 옵션을 사용하세요.
       - Cisco AnyConnect 버전 4.0.7 이상이 설치된 iOS

     > [!Tip]  
     > iOS용 Cisco AnyConnect 4.0.07x 이상은 버전 1802에서 [시험판 기능](/sccm/core/servers/manage/pre-release-features)으로 처음 도입되었습니다. [업데이트 4163547](https://support.microsoft.com/help/4163547)에서 버전 1802부터 이 기능은 더 이상 시험판 기능이 아닙니다.  
  
  
> [!Note]  
> 하이브리드 MDM의 VPN 프로필에서는 iOS용 F5 Access 버전 3.0 이상이 지원되지 않습니다. 이 제품을 F5 Access 2018이라고도 합니다. 이 VPN 클라이언트에 대해 VPN 프로필을 만들어야 하는 경우 Intune 독립 실행형을 사용합니다. 버전 12를 비롯한 이후 버전의 iOS에서는 F5 Access 버전 2.1 이전 버전을 지원하지 않습니다. 자세한 내용은 [Microsoft Intune support team blog](https://aka.ms/iOS12_and_VPN)(Microsoft Intune 지원 팀 블로그)를 참조하세요.


## <a name="windows-10-vpn-features-available-when-using-configuration-manager-with-intune"></a>Intune에서 Configuration Manager를 사용할 때 사용할 수 있는 Windows 10 VPN 기능  

다음 옵션은 Windows 10의 모든 연결 형식에 사용할 수 있습니다.

- **회사 Wi-fi 네트워크에 연결 시 VPN 건너뛰기**: 장치가 회사 Wi-fi 네트워크에 연결 된 경우 VPN 연결이 사용 되지 않습니다. 디바이스가 회사 네트워크에 연결되어 있는지 확인하는 데 사용되는 신뢰할 수 있는 네트워크 이름을 입력합니다.  

- **네트워크 트래픽 규칙**: 프로토콜, 로컬 포트, 원격 포트 및 주소 범위만 VPN 연결에 대해 사용 하도록 설정 합니다.  

     > [!Note]  
     > 네트워크 트래픽 규칙을 만들지 않으면 모든 프로토콜, 포트 및 주소 범위를 사용할 수 있습니다. 규칙을 만들고 나면 해당 규칙이나 추가 규칙에서 지정하는 프로토콜, 포트 및 주소 범위만 VPN 연결에 사용됩니다.  
  
- **경로**: VPN 연결을 사용 하는 경로입니다. 경로가 60개를 초과하면 정책이 실패할 수 있습니다.  

- **DNS 서버**: VPN 연결이 설정된 후 해당 연결에서 사용되는 DNS 서버입니다.  

- **자동으로 VPN에 연결 하는 앱**: 앱을 추가할 수도 있고 자동으로 VPN 연결을 사용 하는 앱의 목록을 가져올 수 있습니다. 앱 형식에 따라 앱 식별자가 결정됩니다. 데스크톱 앱의 경우 앱의 파일 경로를 제공합니다. 유니버설 앱의 경우 PFN(패키지 패밀리 이름)을 제공합니다. 앱의 PFN을 찾는 방법은 [Find a package family name for per-app VPN](../../protect/deploy-use/find-a-pfn-for-per-app-vpn.md)(앱별 VPN에 대한 패키지 패밀리 이름 찾기)을 참조하세요.  

     > [!IMPORTANT]  
     > 앱별 VPN 구성에 사용하기 위해 컴파일하는 모든 관련 앱 목록을 보호해야 합니다. 권한이 없는 사용자가 목록을 변경하고 해당 목록을 앱별 VPN 앱 목록으로 가져오는 경우 액세스 권한이 부여되면 안 되는 앱에 VPN 액세스 권한을 잠재적으로 부여하게 됩니다. 앱 목록을 보호할 수 있는 한 가지 방법은 ACL(액세스 제어 목록)을 사용하는 것입니다.  



## <a name="create-vpn-profiles"></a>VPN 프로필 만들기


1. Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에서 **준수 설정**, **회사 리소스 액세스**를 차례로 확장하고 **VPN 프로필**을 선택합니다. 

2. 리본 메뉴에서 **VPN 프로필 만들기**를 클릭합니다.  

3. **일반** 페이지에서 **이름**을 지정한 다음, **VPN 프로필 유형**을 선택합니다.   
     > [!NOTE]  
     > Windows 10 VPN 기능을 사용하는 VPN 프로필의 이름은 유니코드일 수 없고 특수 문자를 포함할 수 없습니다.


4. **지원되는 플랫폼** 페이지를 사용할 수 있는 경우 이전에 지정한 VPN 프로필 유형의 OS 버전을 선택합니다. 사용 가능한 모든 OS 버전에 VPN 프로필을 설치하려면 **모두 선택**을 선택합니다.  

5. **연결** 페이지에서 VPN 연결을 구성합니다. 이러한 옵션에 대한 자세한 내용은 [VPN 프로필 만들기](/sccm/protect/deploy-use/create-vpn-profiles#create-a-vpn-profile)에서 연결 페이지의 단계를 참조하세요.  

6. **인증 방법** 페이지에서 다음 설정을 지정합니다.  

   - **인증 방법**: VPN 연결에 사용 된 인증 방법을 선택 합니다. 사용 가능한 방법은 이 표에 표시된 연결 형식에 따라 달라집니다.  

     |인증 방법|지원되는&nbsp;연결&nbsp;형식|  
     |---------------------------|--------------------------------|  
     |**인증서**<br /><br /> **참고:**<ul><li>클라이언트 인증서가 네트워크 정책 서버와 같은 RADIUS 서버를 인증하는 경우 인증서의 주체 대체 이름을 사용자 계정 이름으로 설정합니다.</li><li>Android 배포의 경우 EKU 식별자 및 인증서 발급자 지문 해시 값을 선택합니다. 이렇게 하지 않으면 사용자가 적절한 인증서를 수동으로 선택해야 합니다.</li></ul>  |<ul><li>Cisco AnyConnect</li><li>Cisco Legacy AnyConnect</li><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> 검사점 모바일 VPN</li></ul>|  
     |**사용자 이름 및 암호**|<ul><li>Pulse Secure</li><li>F5 Edge Client</li><li>Dell SonicWALL Mobile Connect</li><li> 검사점 모바일 VPN</li></ul>|  
     |**Microsoft EAP-TTLS**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>PPTP</li><li>IKEv2</li><li>L2TP</li></ul>|  
     |**Microsoft 보호된 EAP(PEAP)**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
     |**Microsoft 보안 암호(EAP-MSCHAP v2)**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
     |**스마트 카드 또는 기타 인증서**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
     |**MSCHAP v2**|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>IKEv2</li><li>PPTP</li><li>L2TP</li></ul>|  
     |**RSA SecurID** (iOS에만 해당)|<ul><li>Microsoft SSL(SSTP)</li><li>Microsoft 자동</li><li>PPTP</li><li>L2TP</li></ul>|  
     |**컴퓨터 인증서 사용**|<ul><li>IKEv2</li></ul>|  

      선택한 옵션에 따라 다음과 같은 추가 정보를 지정하라는 메시지가 표시될 수 있습니다.  

     - **로그온 할 때마다 사용자 자격 증명 기억**: 사용자 연결할 때마다 입력 하지 않아도 되도록 사용자 자격 증명 기억 되지 않습니다.  

     - **클라이언트 인증을 위해 클라이언트 인증서 선택**: 이전에 만든 클라이언트 [SCEP 인증서](create-pfx-certificate-profiles.md) VPN 연결을 인증 하는 데 사용 되는 합니다.   

       > [!NOTE]  
       >  iOS 디바이스의 경우 선택하는 SCEP 프로필이 VPN 프로필에 포함됩니다. 다른 플랫폼의 경우 인증서가 없거나 호환되지 않으면 VPN 프로필이 설치되지 않도록 적용 가능성 규칙이 추가됩니다.  
       >   
       >  지정하는 SCEP 인증서가 호환되지 않거나 배포되지 않은 경우 VPN 프로필이 디바이스에 설치되지 않습니다.
       >  
       >  iOS를 실행하는 디바이스는 연결 형식이 PPTP인 경우 인증 방법으로 RSA SecurID 및 MSCHAP v2만 지원합니다. 오류 보고를 방지하려면 iOS를 실행하는 디바이스에 별도의 PPTP VPN 프로필을 배포하세요.   

     - **조건부 액세스**  
         - 연결 전에 VPN에 연결하는 디바이스의 조건부 액세스 준수를 테스트하려면 **이 VPN 연결에 조건부 액세스 사용**을 선택합니다. 자세한 내용은 [디바이스 규정 준수 정책](/sccm/protect/deploy-use/device-compliance-policies)를 참조하세요.  

         - 디바이스 준수에 대해 VPN 인증 인증서 이외의 인증서를 선택하려면 **대체 인증서로 SSO(Single Sign-On) 사용**을 선택합니다. 이 옵션을 선택하는 경우 VPN 클라이언트가 찾아야 하는 올바른 인증서의 **EKU**(쉼표로 구분된 목록) 및 **발급자 해시**를 제공합니다.  

       - **Windows Information Protection** - 엔터프라이즈에서 관리되는 회사 ID를 제공합니다. 일반적으로 조직의 기본 도메인(예: *contoso.com*)입니다. "|" 문자로 구분하여 조직에서 소유하는 여러 도메인을 지정할 수 있습니다. 예를 들어 *contoso.com|newcontoso.com*입니다. 자세한 내용은 [Intune을 사용하여 Windows Information Protection 앱 보호 정책 만들기 및 배포](/intune/windows-information-protection-policy-create)를 참조하세요.   

       ![VPN 프로필 만들기 마법사, 인증 방법 페이지](media/vpn-conditional-access.png)

       Windows 클라이언트 버전에서 지원하는 경우 인증 방법을 **구성**하는 옵션을 사용할 수 있습니다. 이 옵션은 인증 방법을 구성하는 Windows 속성 대화 상자를 엽니다. **구성**이 사용하지 않도록 설정되어 있으면 다른 수단을 통해 인증 방법 속성을 구성합니다.  

7. VPN 연결에 프록시 서버가 사용되는 경우 **VPN 프로필 만들기 마법사**의 **프록시 설정**페이지에서 **이 VPN 프로필에 대한 프록시 설정 구성** 확인란을 선택합니다. 그런 다음 프록시 서버 정보를 제공합니다. 자세한 내용은 Windows Server 설명서를 참조하세요.  

   > [!NOTE]  
   >  Windows 8.1 컴퓨터에서 VPN 프로필은 해당 컴퓨터를 사용하여 VPN에 연결할 때까지 프록시 정보를 표시하지 않습니다.  


8. 필요한 경우 DNS 설정을 추가로 구성합니다.  

9. 마법사를 마칩니다. 새로운 VPN 프로필이 **자산 및 호환성** 작업 영역의 **VPN 프로필** 노드에 새 VPN 프로필이 표시됩니다.  



## <a name="next-steps"></a>다음 단계  
VPN 프로필 배포 방법에 대한 자세한 내용은 [Wi-Fi, VPN, 이메일 및 인증서 프로필 배포](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md)를 참조하세요.

 다음 항목에서는 VPN 프로필을 계획, 설정, 운영 및 유지 관리하는 방법을 설명합니다.  

-   [VPN 프로필에 대한 필수 구성 요소](../../protect/plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [VPN 프로필에 대한 보안 및 개인 정보](../../protect/plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
