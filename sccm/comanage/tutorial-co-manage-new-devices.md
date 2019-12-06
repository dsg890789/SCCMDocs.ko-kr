---
title: 자습서&#58; 인터넷 디바이스의 공동 관리 사용
titleSuffix: Configuration Manager
description: Configuration Manager 및 Microsoft Intune을 사용하여 새로운 인터넷 기반 Windows 10 디바이스의 공동 관리를 구성하는 방법에 대해 알아봅니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 07/26/2019
ms.topic: tutorial
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 7fb02a5c-e286-46b1-a972-6335c858429a
ms.openlocfilehash: 3ecf5f7a0f88275c146adf6c040d98af6c41dc31
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "71712439"
---
# <a name="tutorial-enable-co-management-for-new-internet-based-devices"></a>자습서: 최신 인터넷 기반 디바이스의 공동 관리 사용

공동 관리를 사용하면 Configuration Manager를 사용하여 조직의 PC를 관리하기 위해 제대로 설정된 프로세스를 유지할 수 있습니다. 이와 동시에 보안 및 최신 프로비저닝을 위해 Intune을 사용하여 클라우드에 투자할 수 있습니다.

이 자습서에서는 Azure AD(Active Directory)와 온-프레미스 AD를 모두 사용하지만 [하이브리드 AD](/azure/active-directory/devices/concept-azure-ad-join-hybrid)가 없는 환경에서 Windows 10 디바이스의 공동 관리를 설정합니다. Configuration Manager 환경에는 동일한 단일 서버인 사이트 서버에 모든 사이트 시스템 역할이 있는 단일 기본 사이트가 포함되어 있습니다. 이 자습서는 Windows 10 디바이스가 이미 Intune에 등록되어 있다는 전제에서 시작됩니다. 

Azure AD(Active Directory)로 온-프레미스 AD를 조인하는 하이브리드 Azure AD를 배포할 수 없는 경우에는[구성 관리자 클라이언트에 대한 공동 관리 사용](/sccm/comanage/tutorial-co-manage-clients) 포함 자습서를 따르는 것이 좋습니다.

이 자습서는 다음과 같은 경우에 사용합니다.
  
- 공동 관리로 가져올 Windows 10 디바이스가 있는 경우 이러한 디바이스는 Windows Autopilot을 통해 프로비전되었거나 하드웨어 OEM에서 직접 가져왔을 수 있습니다.
- 구성 관리자 클라이언트를 추가할 Intune으로 현재 관리하고 있는 Windows 10 디바이스가 인터넷상에 있는 경우

**이 자습서에서는 다음을 수행합니다.**  
> [!div class="checklist"]  
> * Azure 및 온-프레미스 환경에 대한 필수 조건 검토
> * CMG(클라우드 관리 게이트웨이)에 대한 공용 SSL 인증서 요청
> * Configuration Manager에서 Azure 서비스 사용
> * 클라우드 관리 게이트웨이 배포 및 관리  
> * CMG를 사용할 클라이언트 및 관리 지점 구성
> * Configuration Manager에서 공동 관리 사용
> * 구성 관리자 클라이언트를 설치할 Intune 구성
> * 클라우드 서비스에 대한 라이선스 할당

## <a name="prerequisites"></a>필수 구성 요소  

### <a name="azure-services-and-environment"></a>Azure 서비스 및 환경

- Azure 구독([평가판](https://azure.microsoft.com/free))
- Azure Active Directory Premium
- Microsoft Intune 구독
  > [!TIP]  
  > EMS(Enterprise Mobility 및 Security) 구독에는 Azure Active Directory Premium 및 Microsoft Intune이 모두 포함되어 있습니다. EMS 구독([평가판](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-trial))  

- 사용자는 *Intune* 및 *Azure Active Directory Premium*에 대한 [라이선스를 받아야](tutorial-co-manage-clients.md#assign-intune-licenses-to-users) 함
- [디바이스를 자동으로 등록](tutorial-co-manage-clients.md#configure-auto-enrollment-of-devices-to-intune)하도록 Intune이 구성됨  

### <a name="on-premises-infrastructure"></a>온-프레미스 인프라

- System Center Configuration Manager 현재 분기, 버전 1810 이상
  
  버전 1810은 [향상된 HTTP](/sccm/core/plan-design/hierarchy/enhanced-http)를 도입하였으며 더욱 복잡한 PKI 요구 사항을 피하기 위해 이 자습서에서 사용됩니다. 향상된 HTTP를 사용하면 클라이언트를 관리하는 데 사용하는 기본 사이트가 HTTP 사이트 시스템에 대해 Configuration Manager가 생성한 인증서를 사용하도록 구성되어야 합니다.  

  또한 버전 1810에는 구성 관리자 클라이언트의 인터넷 기반 설치를 위해 더욱 간단한 명령줄이 도입되었습니다.

- [MDM 기관](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority)은 Intune으로 설정되어야 함  

### <a name="external-certificates"></a>외부 인증서

- CMG 서버 인증 인증서입니다. 이 인증서는 공용 및 전역으로 신뢰할 수 있는 인증서 공급자의 SSL 인증서입니다. 예를 들어 DigiCert, VeriSign 또는 Thawte가 있지만, 이에 국한되지는 않습니다. 이 인증서를 프라이빗 키를 사용하여 .PFX 파일로 내보냅니다.  

- 이 자습서의 뒷부분에서 이 인증서 요청을 구성하는 방법에 대한 지침을 제공합니다.

### <a name="permissions"></a>사용 권한

이 자습서 전체에서 다음 권한을 사용하여 작업을 완료할 수 있습니다.

- Azure에서 ’전역 관리자’인 계정 
- 온-프레미스 인프라에서 ‘도메인 관리자’인 계정   
- Configuration Manager의 ‘모든’ 범위에 대해 ‘전체 관리자’인 계정  

## <a name="request-a-public-certificate-for-the-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 공용 인증서 요청

디바이스가 인터넷에 연결되어 있으면 공동 관리 작업에 CMG(Configuration Manager 클라우드 관리 게이트웨이)가 필요합니다. CMG를 사용하면 인터넷 기반 Windows 10 디바이스가 온-프레미스 Configuration Manager 배포와 통신할 수 있습니다. 디바이스와 Configuration Manager 환경 간에 신뢰를 설정하려면 CMG에 SSL 인증서가 필요합니다.

이 자습서에서는 전역으로 신뢰할 수 있는 인증서 공급자로부터 권한을 받는  **CMG 서버 인증 인증서**라는 공용 인증서를 사용합니다. 온-프레미스 Microsoft 인증 기관으로부터 권한을 받는 인증서를 사용하여 공동 관리를 구성할 수도 있지만 자체 서명된 인증서 사용에 대한 내용은 이 자습서에서 다루지 않습니다.

**CMG 서버 인증 인증서**는 구성 관리자 클라이언트와 CMG 사이의 통신 트래픽을 암호화하는 데 사용됩니다. 인증서는 클라이언트에 대한 서버의 ID를 확인하기 위해 신뢰할 수 있는 루트를 추적합니다. 공용 인증서에는 Windows 클라이언트가 이미 신뢰하는 신뢰할 수 있는 루트가 포함되어 있습니다.

이 인증서에 대한 정보: 

- Azure에서 CMG 서비스의 고유한 이름을 식별한 다음, 인증서 요청에 해당 이름을 지정합니다.  
- 특정 서버에서 인증서 요청을 생성한 후 요청을 공용 인증서 공급자에게 제출하여 필요한 SSL 인증서를 가져옵니다.  
- 공급자로부터 받은 인증서를 요청을 생성한 시스템으로 가져옵니다. CMG를 나중에 Azure에 배포할 때 동일한 컴퓨터를 사용하여 인증서를 내보낼 수 있습니다.  
- CMG가 설치되면 인증서에 지정한 이름을 사용하여 Azure에 CMG 서비스를 만듭니다.  

### <a name="identify-a-unique-name-for-your-cloud-management-gateway-in-azure"></a>Azure에서 클라우드 관리 게이트웨이의 고유한 이름 식별

CMG 서버 인증 인증서를 요청하는 경우 Azure에서 ‘클라우드 서비스(클래식)’를 식별할 고유한 이름을 지정해야 합니다.  기본적으로 Azure 퍼블릭 클라우드는 *cloudapp.net*을 사용하며 CMG는 cloudapp.net 도메인 내에서 *\<YourUniqueDnsName&gt;.cloudapp.net*으로 호스트됩니다.  

> [!TIP]  
> 이 자습서에서 **CMG 서버 인증 인증서**는 *contoso.com*으로 끝나는 FQDN을 사용합니다.  CMG를 만든 후에는 조직의 공용 DNS에 CNAME(정식 이름 레코드)을 구성합니다. 이 레코드는 공용 인증서에서 사용하는 이름으로 매핑하는 CMG에 대한 별칭을 만듭니다.  

공용 인증서를 요청하기 전에 사용하려는 이름이 Azure에서 사용 가능한지 확인하세요. Azure에서는 서비스를 직접 만들지 않습니다. 대신에, 요청하는 공용 인증서에 지정된 이름은 CMG를 설치할 때 Configuration Manager가 클라우드 서비스를 만드는 데 사용됩니다.  

1. [Microsoft Azure Portal](https://portal.azure.com/)에 로그인합니다.  

2. **리소스 만들기**를 선택하고, **컴퓨팅** 범주를 선택한 다음, **클라우드 서비스**를 선택합니다. 클라우드 서비스(클래식) 페이지가 열립니다.

3. **DNS 이름**의 경우 사용할 클라우드 서비스의 접두사 이름을 지정합니다. 이 접두사는 CMG 서버 인증 인증서에 대한 게시 인증서를 요청하는 경우 나중에 사용하는 항목과 같아야 합니다. *MyCSG.cloudapp.net*의 네임스페이스를 만드는 *MyCSG*를 사용합니다. 인터페이스에는 이름을 사용할 수 있는지, 아니면 다른 서비스에서 이미 사용 중인지 여부가 확인됩니다.  
 사용하려는 이름이 사용 가능한지 확인하면 CSR(인증서 서명 요청)을 제출할 준비가 된 것입니다.

### <a name="request-the-certificate"></a>인증서 요청

다음 정보를 사용하여 CMG에 대한 인증서 서명 요청을 공용 인증서 공급자에게 제출합니다. 환경에 맞게 다음과 같은 값을 변경합니다.  

- 클라우드 관리 게이트웨이의 서비스 이름을 확인하려면 *MyCMG*
- 회사 이름으로 *Contoso*
- 공용 도메인으로 *Contoso.com*

기본 사이트 서버를 사용하여 CSR(인증서 서명 요청)을 생성하는 것이 좋습니다. 인증서를 가져올 때 CSR을 생성한 동일한 서버에 인증서를 등록해야 합니다. 그러지 않으면 필수 항목인 인증서 프라이빗 키를 내보낼 수 없습니다.  

CSR을 생성할 때 버전 2 키 공급자 유형을 요청합니다. 버전 2 인증서만 지원됩니다.  

> [!TIP]  
> CMG를 배포할 때 동시에 CDP(클라우드 배포 지점)도 설치합니다. 기본적으로 **CMG가 클라우드 배포 지점으로 기능하고 Azure 스토리지에서 콘텐츠를 제공하도록 허용** 옵션이 선택되어 있습니다. 서버의 CDP를 CMG와 함께 배치하면 CDP를 지원할 별도의 인증서 및 구성이 필요하지 않습니다. CDP에는 공동 관리를 사용할 필요가 없지만 대부분의 환경에서 유용합니다.  
>
> 공동 관리를 위해 추가 클라우드 배포 지점을 사용할 경우 각 추가 서버에 대해 별도의 인증서를 요청해야 합니다. CDP에 대한 공용 인증서를 요청하려면 클라우드 관리 게이트웨이 CSR과 동일한 세부 정보를 사용합니다. 일반 이름을 각 CDP에 대해 고유하게 변경하기만 하면 됩니다.  

#### <a name="details-for-the-cloud-management-gateway-csr"></a>클라우드 관리 게이트웨이 CSR에 대한 세부 정보

- **일반 이름**: ClousServiceNameCMG.YourCompanyPubilcDomainName.com  
예제: MyCSG.contoso.com  
- **주체 대체 이름**: CN(일반 이름)과 동일  
- **조직**:  조직의 이름  
- **부서**: 조직별  
- **구/군/시**: 조직별  
- **상태**: 조직별  
- **국가**: 조직별  
- **키 크기: 2048**  
- **공급자: Microsoft RSA SChannel 암호화 공급자**  

### <a name="import-the-certificate"></a>인증서 가져오기

공용 인증서를 받으면 CSR을 만든 컴퓨터의 로컬 인증서 저장소로 가져옵니다. 그런 다음, Azure에서 CMG용으로 사용할 수 있도록 인증서를 .PFX 파일로 내보냅니다.  

공용 인증서 공급자는 일반적으로 인증서 가져오기에 대한 지침을 제공합니다. 인증서를 가져오기 프로세스는 다음 지침과 유사해야 합니다.  

1. 인증서를 가져올 컴퓨터에서 인증서 파일(.pfx)을 찾습니다.  

2. 파일을 마우스 오른쪽 단추로 클릭한 후 **PFX 설치**를 선택합니다.  

3. 인증서 가져오기 마법사가 시작되면 **다음**을 선택합니다.  

4. **가져올 파일** 페이지에서 **다음**을 선택합니다.

5. **암호** 페이지의 [암호] 상자에 프라이빗 키 암호를 입력하고 **다음**을 선택합니다.  
  
   키를 내보낼 수 있도록 설정하는 옵션을 선택합니다.

6. **인증서 저장소 페이지**에서 **인증서 유형을 기반으로 인증서 저장소를 자동으로 선택**을 선택한 후 **다음**을 선택합니다.  

7. **완료**를 선택합니다.

### <a name="export-the-certificate"></a>인증서 내보내기

서버에서 ‘CMG 서버 인증 인증서’를 내보냅니다.  인증서를 다시 내보내면 Azure의 클라우드 관리 게이트웨이에서 사용할 수 있습니다.  

1. 공용 SSL 인증서를 가져온 서버에서 **certlm.msc**를 실행하여 인증서 관리자 콘솔을 엽니다.  

2. 인증서 관리자 콘솔에서 **개인 > 인증서**를 선택합니다. 그런 다음, 이전 절차에서 등록한 ‘CMG 서버 인증 인증서’를 마우스 오른쪽 단추로 클릭한 후 **모든 작업 > 내보내기**를 선택합니다.   

3. 인증서 내보내기 마법사에서 **다음**, **예, 프라이빗 키를 내보냅니다.** 를 선택한 후 **다음**을 선택합니다.  

4. 파일 내보내기 형식 페이지에서 **개인 정보 교환 - PKCS #12(.PFX)** , **다음**을 차례를 선택하고 암호를 입력합니다. 파일 이름의 경우 **C:\ConfigMgrCloudMGServer**와 같이 이름을 지정합니다. Azure에서 CMG를 만들 때 이 파일을 참조할 것입니다.  

5. **다음**을 선택하고, 다음 설정을 먼저 확인한 후에 **완료**를 선택하여 내보내기를 완료합니다.  

   - 키 내보내기 = 예  
   - 인증 경로에 모든 인증서 포함 = 예  
   - 파일 형식 = .pfx(개인 정보 교환)  

6. 내보내기를 완료한 후 .pfx 파일을 찾아서 인터넷 기반 클라이언트를 관리할 Configuration Manager 기본 사이트 서버의 **C:\Certs**에 복사본을 저장합니다. Certs 폴더는 서버 간에 인증서를 이동하는 동안 사용할 임시 폴더입니다. Azure에 클라우드 관리 게이트웨이를 배포할 때 기본 사이트 서버에서 인증서 파일에 액세스합니다.  

기본 사이트 서버에 인증서를 복사하면 멤버 서버의 개인 인증서 저장소에서 인증서를 삭제할 수 있습니다.

## <a name="enable-azure-cloud-services-in-configuration-manager"></a>Configuration Manager에서 Azure 클라우드 서비스 사용

Configuration Manager 콘솔 내에서 Azure 서비스를 구성하려면 Azure 서비스 구성 마법사를 사용하고 Azure AD (Azure Active Directory) 앱을 두 개 만듭니다.  

- **서버 앱** – Azure AD의 ‘웹앱’   
- **클라이언트 앱** – Azure AD의 ‘네이티브 클라이언트’ 앱   

기본 사이트 서버에서 다음 절차를 실행합니다.  

1. 기본 사이트 서버에서 Configuration Manager 콘솔을 열고 **관리 > Cloud Services > Azure 서비스**로 이동하여 **Azure 서비스 구성**을 선택합니다.  

   Azure 서비스 구성 페이지에서 구성 중인 클라우드 관리 서비스의 식별 이름을 지정합니다. 예: ‘내 클라우드 관리 서비스’ 

   그런 다음, **클라우드 관리**를 선택한 후 **다음**을 선택합니다.  

   > [!TIP]  
   > 마법사에서 수행하는 구성에 대한 자세한 내용은 [Azure 서비스 마법사 시작](https://docs.microsoft.com/sccm/core/servers/deploy/configure/Azure-services-wizard#start-the-azure-services-wizard)을 참조하세요.

2. **앱 속성** 페이지에서 **웹앱**의 경우 **찾아보기**를 선택하여 **서버 앱** 대화 상자를 연 다음, **만들기**를 선택합니다. 다음 필드를 구성합니다.

   - **애플리케이션 이름**: *Cloud Management 웹앱*과 같이 앱의 식별 이름을 지정합니다.  

   - **홈페이지 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

   - **앱 ID URI**: 이 값은 Azure AD 테넌트에서 고유해야 합니다. Configuration Manager 클라이언트가 서비스 액세스를 요청할 때 사용하는 액세스 토큰입니다. 이 값은 기본적으로 `https://ConfigMgrService`입니다.  

   다음으로 **로그인**을 선택하고 Azure 전역 관리자 계정을 지정합니다. 이러한 자격 증명은 Configuration Manager에 저장되지 않습니다. 이 가상 사용자는 Configuration Manager에서 권한이 필요 없으며, Azure 서비스 마법사를 실행하는 계정과 동일한 계정이 아니어도 상관없습니다.

   로그인하면 결과가 표시됩니다. **확인**을 선택하면 서버 만들기 애플리케이션 대화 상자가 닫히고 앱 속성 페이지로 돌아갑니다.

3. **앱**의 경우에는 **찾아보기**를 선택하여 **클라이언트 앱** 대화 상자를 엽니다.

4. **만들기**를 선택하여 **클라이언트 애플리케이션 만들기** 대화 상자를 열고 다음 필드를 구성합니다.  

   - **애플리케이션 이름**: ‘Cloud Management 네이티브 클라이언트 앱’과 같이 앱의 식별 이름을 지정합니다. 

   - **회신 URL**: 이 값은 Configuration Manager에서 사용되지는 않지만, Azure AD에 필요합니다. 이 값은 기본적으로 `https://ConfigMgrClient`입니다.
   다음으로 **로그인**을 선택하고 Azure 전역 관리자 계정을 지정합니다. 웹앱과 같은 이러한 자격 증명은 저장되지 않으며 Configuration Manager에서 권한이 필요하지 않습니다.

   로그인하면 결과가 표시됩니다. **확인**을 선택하면 클라이언트 만들기 애플리케이션 대화 상자가 닫히고 앱 속성 페이지로 돌아갑니다. 그런 다음, 계속하려면 **다음**을 선택합니다.

5. **검색 구성 설정** 페이지에서 **Azure Active Directory 사용자 검색 사용** 확인란을 선택하고, **다음**을 선택한 후 사용 중인 환경에 대한 검색 대화 상자 구성을 완료합니다.  

6. 요약, 진행 및 완료 페이지를 계속 진행한 다음, 마법사를 닫습니다.  

   이제 Azure AD 사용자 검색을 위한 Azure 서비스를 Configuration Manager에서 사용할 수 있습니다.  지금은 콘솔을 열린 상태로 둡니다.  

7. 브라우저를 열고 [Azure Portal](https://portal.azure.com/)에 로그인합니다.  

8. **모든 서비스 > Azure Active Directory > 앱 등록**을 선택한 후 다음을 수행합니다.

   1. 만든 웹앱을 선택합니다.

   2. **설정 > 필요한 권한**으로 이동하여 **권한 부여**, **예**를 차례로 선택합니다.  

   3. 만든 네이티브 클라이언트 앱을 선택합니다.

   4. **설정 > 필요한 권한**으로 이동하여 **권한 부여**, **예**를 차례로 선택합니다.  

9. Configuration Manager 콘솔에서 **관리 > 개요 > Cloud Services > Azure 서비스**로 이동하여 Azure 서비스를 선택합니다. 그런 다음, **Azure Active Directory 사용자 검색**을 마우스 오른쪽 단추로 클릭하고 **지금 전체 검색 실행**을 선택합니다. **예**를 선택하여 작업을 확인합니다.  

10. 기본 사이트 서버에서 Configuration Manager **SMS_AZUREAD_DISCOVERY_AGENT.log**를 열고 다음 항목을 찾아 검색이 수행되는지 확인합니다.  ‘Azure Active Directory 사용자에 대한 UDX가 게시되었음’   

    기본적으로 로그 파일은 *%Program_Files%\Microsoft Configuration Manager\Logs*에 있습니다.  

## <a name="create-the-cloud-services-in-azure"></a>Azure에서 클라우드 서비스 만들기

**자습서의 이 섹션에서는 다음을 수행합니다.**

- CMG 클라우드 서비스 만들기  
- 두 서비스에 대한 DNS CNAME 레코드 만들기  

### <a name="create-the-cmg"></a>CMG 만들기

이 절차에 따라 Azure에 서비스로 클라우드 관리 게이트웨이를 설치할 수 있습니다. 계층 구조의 최상위 계층 사이트에서 CMG를 설치합니다. 이 자습서에서는 인증서를 등록하고 내보낸 기본 사이트를 계속 사용합니다.

1. 기본 사이트 서버에서 Configuration Manager 콘솔을 연 다음, **관리 > 개요 > Cloud Services > 클라우드 관리 게이트웨이**로 이동하고, **클라우드 관리 게이트웨이 만들기**를 선택합니다.  

2. **일반** 페이지에서 다음을 수행합니다.  

   1. **Azure 환경**에 대한 클라우드 환경을 선택합니다. 이 자습서에서는 **AzurePublicCloud**를 사용합니다.  

   2. **Azure Resource Manager 배포**를 선택합니다.  
  
   3. Azure 구독에 **로그인**합니다. Configuration Manager는 Configuration Manager에 대한 Azure 클라우드 서비스를 사용할 때 구성한 정보에 따라 추가 정보를 채웁니다.  

   계속하려면 **다음**을 선택합니다.  

3. **설정** 페이지에서 **ConfigMgrCloudMGServer.pfx** 파일을 찾아 선택합니다. 이 파일은 CMG 서버 인증 인증서를 가져온 후 내보낸 파일입니다. 암호를 지정하면 .pfx 인증서 파일의 세부 정보를 기반으로 **서비스 이름** 및 **배포 이름**이 자동으로 채워집니다.

4. **지역**을 설정합니다.

5. **리소스 그룹**의 경우 기존 리소스 그룹을 사용하거나 **CofigMgrCloudServices**와 같이 공백을 사용하지 않는 식별 이름으로 그룹을 만듭니다. 그룹을 만들도록 선택한 경우 그룹이 Azure의 리소스 그룹으로 추가됩니다.  

6. 대규모로 구성할 준비가 되지 않은 경우에는 **VM 인스턴스** 수에 1을 사용합니다. VM 인스턴스 수를 사용하면 CMG(단일 클라우드 관리 게이트웨이) 클라우드 서비스를 확장하여 더 많은 클라이언트 연결을 지원할 수 있습니다. 나중에 Configuration Manager 콘솔을 사용하여 사용 중인 VM 인스턴스 수를 반환 및 편집할 수 있습니다.  

7. **클라이언트 인증서 해지 확인** 에 대한 확인란을 사용하도록 설정합니다.

8. CMG를 사용하여 클라우드 배포 지점을 배포하려면 **CMG가 클라우드 배포 지점으로 작동하고 Azure 스토리지의 콘텐츠를 제공하도록 허용** 확인란을 사용하도록 설정합니다.

9. 계속하려면 **다음**을 선택합니다.

10. **경고** 페이지에서 값을 검토하고 **다음**을 선택합니다.

11. **요약** 페이지를 검토하고 **다음**을 클릭하여 클라우드 관리 게이트웨이 Cloud Service를 만듭니다. **닫기**를 선택하여 마법사를 완료합니다.  

12. 이제 Configuration Manager 콘솔의 클라우드 관리 게이트웨이 노드에서 새 서비스를 볼 수 있습니다.  

### <a name="create-dns-cname-records"></a>DNS CNAME 레코드 만들기

CMG에 대한 DNS 항목을 만들 때 회사 네트워크 내부 및 외부 모든 곳에서 Windows 10 디바이스를 사용하도록 설정하면 이름 확인을 사용하여 Azure에서 CMG 클라우드 서비스를 찾을 수 있습니다.

CNAME 레코드 예제는 다음과 같은 세부 정보를 사용합니다.  

- 회사 이름은 ***Contoso.com***의 공용 DNS 네임스페이스를 사용하는 **Contoso**입니다.  

- CMG 서비스 이름은 **MyCMG**로, Azure에서 ***MyCMG.CloudApp.Net***이 됩니다.  

CNAME 레코드 예제: *MyCMG.contoso.com => My.cloudapp.net*

## <a name="configure-the-management-point-and-clients-to-use-the-cmg"></a>CMG를 사용할 클라이언트 및 관리 지점 구성

온-프레미스 관리 지점 및 클라이언트가 클라우드 관리 게이트웨이를 사용하도록 설정하는 구성 설정입니다.

클라이언트 통신을 위해 향상된 HTTP를 사용하기 때문에 HTTPS 관리 지점을 사용할 필요가 없습니다.  

### <a name="create-the-cmg-connection-point"></a>CMG 연결 지점 만들기

향상된 HTTP를 지원하도록 사이트를 구성합니다.  

1. Configuration Manager 콘솔에서 **관리 > 개요 > 사이트 구성 > 사이트**로 이동하여 기본 사이트의 속성을 엽니다.  

2. **클라이언트 컴퓨터 통신** 탭에서 **HTTP 사이트 시스템에 Configuration Manager 생성 인증서 사용**에 대한 ‘HTTPS 또는 HTTP’ 옵션을 선택한 다음, **확인**을 선택하여 구성을 저장합니다. 

    > [!Note]
    > 버전 1906부터 이 탭을 **통신 보안**이라고 합니다.<!-- SCCMDocs#1645 -->  

3. 이제 **관리 > 개요 > 사이트 구성 > 서버 및 사이트 시스템 역할**로 이동하여 클라우드 관리 게이트웨이 연결 지점을 설치할 관리 지점이 있는 서버를 선택합니다.  

4. **사이트 시스템 역할 추가**, **다음**> **다음**을 차례로 선택합니다.  

5. **클라우드 관리 게이트웨이 연결 지점**을 선택한 후 **다음**을 선택하여 계속합니다.  

6. **클라우드 관리 게이트웨이 연결 지점** 페이지에서 기본 선택 항목을 검토하고 올바른 CMG가 선택되었는지 확인합니다=. 여러 클라우드 관리 게이트웨이가 있는 경우 드롭다운 목록을 사용하여 다른 CMG를 지정할 수 있습니다. 또한 설치 후에 사용 중인 CMG를 변경할 수도 있습니다. 계속하려면 **다음**을 선택합니다.

7. 설치를 시작한 다음, 완료 페이지에서 결과를 보려면 **다음**을 선택합니다.  연결 지점의 설치를 완료하려면 **닫기**를 선택합니다.

8. 이제 **관리 > 개요 > 사이트 구성 > 서버 및 사이트 시스템 역할**로 이동하여 연결 지점을 설치한 관리 지점의 **속성** 을 엽니다. **일반** 탭에서 **Configuration Manager 클라우드 관리 게이트웨이 트래픽 허용** 확인란을 선택한 다음, **확인**을 선택하여 구성을 저장합니다.
   > [!TIP]  
   > 공동 관리를 사용할 필요는 없지만 모든 소프트웨어 업데이트 지점에 대해 이와 동일한 편집을 수행하는 것이 좋습니다.

### <a name="configure-client-settings-to-direct-clients-to-use-the-cmg"></a>클라이언트가 직접 CMG를 사용하도록 클라이언트 설정 구성

클라이언트 설정을 사용하여 구성 관리자 클라이언트가 CMG와 통신하도록 구성합니다.  

1. **Configuration Manager 콘솔 > 관리 > 개요 > 클라이언트 설정**을 연 다음, **기본 클라이언트 설정**을 편집합니다.  

2. **Cloud Services**를 선택합니다.

3. **기본 설정** 페이지에서 다음 설정을 **예**로 설정합니다.  

   - **Azure Active Directory에 새 Windows 10 도메인에 연결된 디바이스를 자동으로 등록**  

   - **클라이언트가 클라우드 관리 게이트웨이를 사용하도록 설정**

   - **클라우드 배포 지점에 대한 액세스 허용**

4. **클라이언트 정책** 페이지에서 **인터넷 클라이언트의 사용자 정책 요청 사용**을  = **예**로 설정합니다.

5. **확인**을 선택하여 이 구성을 저장합니다.

## <a name="enable-co-management-in-configuration-manager"></a>Configuration Manager에서 공동 관리 사용

Azure 구성, 사이트 시스템 역할 및 클라이언트 설정을 적절히 사용하면 공동 관리가 가능하도록 Configuration Manager를 구성할 수 있습니다. 그러나 이 자습서를 완료하기 전에 공동 관리를 사용하도록 설정한 후에도 Intune에서 몇 가지 구성을 설정해야 합니다. 이러한 작업 중 하나는 구성 관리자 클라이언트를 배포하도록 Intune을 구성하는 것입니다. 공동 관리 구성 마법사 내에 사용 가능한 클라이언트 배포용 명령줄을 저장하면 이 작업을 더욱 쉽게 수행할 수 있습니다. 이것이 바로 Intune에 대한 구성을 완료하기 전에 공동 관리가 가능한 이유입니다.

> [!TIP]
> - 공동 관리를 사용하는 경우에는 컬렉션을 *파일럿 그룹*으로서 할당하게 됩니다. 이 그룹에는 공동 관리 구성을 테스트할 수 있는 소수의 클라이언트가 포함되어 있습니다. 절차를 시작하기 전에 적합한 컬렉션을 만드는 것이 좋습니다. 그러면 기존 절차를 종료하지 않고도 해당 컬렉션을 선택할 수 있습니다.
> - Configuration Manager 버전 1906부터는 각 워크로드에 대해 서로 다른 *파일럿 그룹*을 할당할 수 있으므로 여러 컬렉션이 필요할 수 있습니다.

### <a name="enable-co-management-starting-in-version-1906"></a>버전 1906부터 시작되는 공동 관리 사용

Configuration Manager 버전 1906부터 시작되는 공동 관리를 사용하려면 아래의 지침을 따릅니다.

[!INCLUDE [Enable Co-management in version 1906 and later](includes/enable-co-management-1906-and-higher.md)]

### <a name="enable-co-management-in-version-1902-and-earlier"></a>버전 1902 이하의 공동 관리 사용

Configuration Manager 버전 1902 이하의 공동 관리를 사용하려면 아래의 지침을 따릅니다.

[!INCLUDE [Enable Co-management in version 1902 and earlier](includes/enable-co-management-1902-and-earlier.md)]

## <a name="use-intune-to-deploy-the-configuration-manager-client"></a>Intune을 사용하여 구성 관리자 클라이언트 배포

현재 Intune으로만 관리되는 Windows 10 디바이스에서 Intune을 사용하여 구성 관리자 클라이언트를 설치할 수 있습니다.  

그러면 이전에 관리되지 않은 Windows 10 디바이스가 Intune에 등록되는 경우 구성 관리자 클라이언트가 자동으로 설치됩니다.

### <a name="create-an-intune-app-to-install-the-configuration-manager-client"></a>구성 관리자 클라이언트를 설치할 Intune 앱 만들기

1. 기본 사이트 서버에서 [Azure Portal](https://portal.azure.com/)에 로그인하고 **Intune > 클라이언트 앱 > 앱 > 추가**로 이동합니다.

2. **앱 유형**의 경우 다음을 수행합니다. **LOB(기간 업무) 앱**을 선택합니다.

3. **앱 패키지 파일**을 선택하고 Configuration Manager 파일 **ccmsetup.msi**의 위치를 찾은 다음, **열기 > 확인**을 선택합니다.
경로 예: *C:\Program Files\Microsoft Configuration Manager\bin\i386\ccmsetup.msi*

4. **앱 정보**를 선택한 후 다음 세부 정보를 지정합니다.
   - **설명**: Configuration Manager 클라이언트  

   - **게시자**: Microsoft  

   - **명령줄 인수**:   *\< **CCMSETUPCMD** 명령줄을 지정합니다. 공동 관리 구성 마법사의* ‘사용’ *페이지에서 저장한 명령줄을 사용할 수 있습니다. 이 명령줄에는 클라우드 서비스의 이름과 디바이스가 구성 관리자 클라이언트 소프트웨어를 설치할 수 있도록 하는 추가 값이 포함되어 있습니다.\>*  

     명령줄 구조는 CCMSETUPCMD 및 SMSSiteCode 매개 변수만 사용하는 이 예제와 유사해야 합니다.  

     ``` Command
     CCMSETUPCMD="CCMHOSTNAME=<ServiceName.CLOUDAPP.NET/CCM_Proxy_MutualAuth/<GUID>" SMSSiteCode="<YourSiteCode>"  
     ```

     > [!TIP]  
     > 사용 가능한 명령줄이 없는 경우 Configuration Manager 콘솔에서 *CoMgmtSettingsProd*의 속성을 보고 명령줄의 복사본을 가져올 수 있습니다.

5. **확인 > 추가**를 선택합니다.  앱이 생성되어 Intune 콘솔에서 사용할 수 있게 됩니다. 앱을 사용할 수 있게 되면 다음 섹션을 사용하여 Windows 10 디바이스에 Intune을 할당하도록 구성할 수 있습니다.

### <a name="assign-the-intune-app-to-install-the-configuration-manager-client"></a>구성 관리자 클라이언트를 설치할 Intune 앱 할당

다음 절차에서는 이전 절차에서 만든 구성 관리자 클라이언트를 설치하기 위해 앱을 배포합니다.

1. [Azure Portal](https://portal.azure.com/)에 로그인합니다.  **모든 서비스 > Intune > 클라이언트 앱 > 앱**을 선택한 다음, 구성 관리자 클라이언트를 배포하기 위해 만든 **ConfigMgr 클라이언트 설정 부트스트랩** 앱을 선택합니다.  

2. **할당 > 그룹 추가**를 선택합니다.  **할당 유형**을 **필수**로 설정한 다음, **포함된 그룹** 및 **제외된 그룹**을 사용하여 공동 관리에 포함할 사용자 및 디바이스가 있는 Azure AD(Active Directory) 그룹을 설정합니다.  

3. **확인**을 선택하여 구성을 **저장**합니다.
이제 할당된 사용자 및 디바이스에 앱이 필요합니다. 앱이 구성 관리자 클라이언트를 디바이스에 설치하면 공동 관리로 관리됩니다.

## <a name="assign-intune-licenses-to-users"></a>사용자에게 Intune 라이선스 할당

흔히 간과되지만 중요한 작업은 공동 관리되는 디바이스를 사용하는 각 사용자에게 Intune 라이선스를 할당하는 것입니다.  

사용자 그룹에 라이선스를 할당하려면 Azure Active Directory를 사용합니다.  

1. [Azure Portal](https://portal.azure.com/)에 관리자 계정으로 로그인합니다. 라이선스를 관리하려면 해당 계정이 전역 관리자 역할 또는 사용자 계정 관리자여야 합니다.  

2. 왼쪽 탐색 창에서 **모든 서비스**를 선택한 다음, **Azure Active Directory**를 선택합니다.  

3. **Azure Active Directory** 창에서 **라이선스**를 선택하여 창을 엽니다. 여기에서 테넌트의 모든 라이선스 대상 제품을 보고 관리할 수 있습니다.  

4. **모든 제품** 아래에서 Intune 라이선스가 포함된 제품 옵션을 선택한 다음, 창의 맨 위에서 **할당**을 선택합니다.  

   예를 들어 Intune을 얻는 방법인 경우 **Enterprise Mobility + Security E5**를 선택할 수 있습니다.  

5. **라이선스 할당** 페이지에서 **사용자 및 그룹**을 클릭하여 **사용자 및 그룹** 창을 엽니다. 그룹 및 라이선스를 할당할 개별 사용자를 선택합니다.  그런 다음, 창 아래에서 **선택**을 클릭하여 선택 항목을 확인합니다.  

6. 이전에 선택한 제품에 포함된 모든 서비스 플랜을 표시하려면 **라이선스 할당** 창에서 **할당 옵션**을 클릭합니다. Intune과 같은 단일 제품을 선택한 경우에는 해당 제품만 표시됩니다.  
   - **Microsoft Intune**을 **켜짐**으로 설정합니다.  
   - 각 사용자에게 **Azure Active Directory Premium**에 대한 라이선스를 할당합니다.  

   해당 라이선스가 할당되면 **확인**을 선택합니다.  

7. 할당을 완료하려면 **라이선스 할당** 창에서 창 아래에 있는 **할당**을 클릭합니다.  

8. 오른쪽 상단에 알림이 표시되어 프로세스의 상태 및 결과를 보여줍니다. 그룹에 대한 할당을 완료할 수 없는 경우(예: 그룹에 대한 기존 라이선스 때문에 할당할 수 없음) 알림을 클릭하여 오류에 대한 세부 정보를 확인하세요. 

## <a name="summary"></a>요약

라이선스가 할당되었는지 확인하기 위한 최종 작업을 포함하여 이 자습서의 구성 단계를 완료하면 디바이스가 성공적으로 공동 관리될 수 있습니다.

## <a name="next-steps"></a>다음 단계

- [공동 관리 대시보드](https://docs.microsoft.com/sccm/core/clients/manage/co-management-dashboard)를 사용하여 공동 관리 디바이스 상태 검토
- [Windows Autopilot](/sccm/comanage/quickstart-autopilot)을 사용하여 새 디바이스 프로비전
- [조건부 액세스](https://docs.microsoft.com/sccm/comanage/quickstart-conditional-access) 및 Intune 규정 준수를 사용하여 회사 리소스에 대한 사용자 액세스 관리
