---
title: 자습서&#58; 기존 Configuration Manager 클라이언트의 공동 관리 사용
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 Windows 10 디바이스를 이미 관리하는 경우 Microsoft Intune으로 공동 관리를 구성하세요.
ms.date: 06/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: tutorial
ms.assetid: 140c522f-d09a-40b6-a4b0-e0d14742834a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 8b19f54d60ed0594be4a51b5abcef69304a27ece
ms.sourcegitcommit: 0bd336e11c9a7f2de05656496a1bc747c5630452
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834759"
---
# <a name="tutorial-enable-co-management-for-existing-configuration-manager-clients"></a>자습서: 기존 Configuration Manager 클라이언트에 대해 공동 관리 사용
공동 관리를 사용하면 Configuration Manager를 사용하여 조직의 PC를 관리하기 위해 제대로 설정된 프로세스를 유지할 수 있습니다. 이와 동시에 보안 및 최신 프로비저닝을 위해 Intune을 사용하여 클라우드에 투자할 수 있습니다.  

이 자습서에서는 Configuration Manager에 이미 등록된 Windows 10 디바이스의 공동 관리를 설정합니다. 이 자습서는 Configuration Manager를 이미 사용하여 Windows 10 디바이스를 관리한다는 전제에서 시작됩니다.

이 자습서는 다음과 같은 경우에 사용합니다.  

- 하이브리드 Azure AD 구성에서 Azure AD(Azure Active Directory)에 연결할 수 있는 온-프레미스 Active Directory가 있는 경우 

  Azure AD(Active Directory)로 온-프레미스 AD를 조인하는 하이브리드 Azure AD를 배포할 수 없는 경우에는 [최신 인터넷 기반 Windows 10 디바이스에 대해 공동 관리 사용](/sccm/comanage/tutorial-co-manage-new-devices) 포함 자습서를 따르는 것이 좋습니다. 
- 클라우드에 연결할 기존 Configuration Manager 클라이언트가 있는 경우


**이 자습서에서는 다음을 수행합니다.**  
> [!div class="checklist"]  
> * Azure 및 온-프레미스 환경에 대한 필수 조건 검토  
> * 하이브리드 Azure AD 설정  
> * Configuration Manager 클라이언트 에이전트를 구성하여 Azure AD에 등록  
> * 디바이스를 자동으로 등록하도록 Intune 구성  
> * 사용자에게 Intune 라이선스 할당  
> * Configuration Manager에서 공동 관리 사용  


## <a name="prerequisites"></a>필수 구성 요소  

### <a name="azure-services-and-environment"></a>Azure 서비스 및 환경
- Azure 구독([평가판](https://azure.microsoft.com/free))
- Azure Active Directory Premium
- Microsoft Intune 구독
  > [!TIP]  
  > EMS(Enterprise Mobility + Security) 구독에는 Azure Active Directory Premium 및 Microsoft Intune이 모두 포함되어 있습니다. EMS 구독([평가판](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-trial))  

사용 중인 환경에 아직 없는 경우 이 자습서에서 표시됩니다.
- *Intune* 및 *Azure Active Directory Premium*에 대한 사용자 라이선스 할당
- 온-프레미스 Active Directory 및 Azure AD(Active Directory) 테넌트 사이에 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-select-installation) 구성


### <a name="on-premises-infrastructure"></a>온-프레미스 인프라
- [지원되는 버전](https://docs.microsoft.com/sccm/core/servers/manage/updates#supported-versions)의 System Center Configuration Manager 현재 분기
- [MDM 기관](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority)은 Intune으로 설정되어야 함  


### <a name="permissions"></a>사용 권한
이 자습서 전체에서 다음 권한을 사용하여 작업을 완료할 수 있습니다.  
- Azure에서 ’전역 관리자’인 계정   
- 온-프레미스 인프라에서 ‘도메인 관리자’인 계정   
- Configuration Manager의 ‘모든’ 범위에 대해 ‘전체 관리자’인 계정     

## <a name="set-up-hybrid-azure-ad"></a>하이브리드 Azure AD 설정
하이브리드 Azure AD를 설정하면 실제로 Azure AD Connect와 ADFS(Active Directory Federated Services)를 사용하여 Azure AD와 온-프레미스 AD의 통합이 설정됩니다. 성공적인 구성을 통해 작업자들은 온-프레미스 AD 자격 증명을 사용하여 외부 시스템에 원활하게 로그인할 수 있습니다.

> [!IMPORTANT]  
> 이 자습서에서는 관리되는 도메인에 대한 하이브리드 Azure AD를 설정하는 핵심 프로세스를 자세히 설명합니다. 프로세스를 잘 숙지하여 이 자습서를 하이브리드 Azure AD를 이해 및 배포하는 가이드로 사용하지 않는 것이 좋습니다.
>
> 하이브리드 Azure AD에 대한 자세한 내용은 Azure Active Directory 문서에서 다음 문서를 참조하세요.
> - [Azure AD 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)
> -  [하이브리드 Azure AD 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)
> -  [디바이스의 하이브리드 Azure AD 조인 컨트롤](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-control)
> -  [페더레이션된 도메인에 대한 하이브리드 Azure AD 조인 구성](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-federated-domains)  


### <a name="set-up-azure-ad-connect"></a>Azure AD Connect 설정  
온-프레미스 AD(Active Directory)의 컴퓨터 계정 및 Azure AD에 있는 디바이스 개체를 동기화 상태로 유지하려면 사용하려면 하이브리드 Azure AD에 Azure AD Connect의 구성이 필요합니다.

버전 1.1.819.0부터 Azure AD Connect는 하이브리드 Azure AD 조인을 구성하는 마법사를 제공합니다. 해당 마법사를 사용하여 구성 프로세스를 간소화할 수 있습니다.  

Azure AD Connect를 구성하려면 Azure AD 테넌트에 대한 전역 관리자 자격 증명이 필요합니다.  

> [!TIP]  
> 다음 절차는 Azure AD Connect의 설정에 대해 신뢰할 만한 것으로 간주해서는 안 되지만 여기에 제공되어 Intune 및 Configuration Manager 간의 공동 관리 구성을 간소화하는 데 도움이 됩니다. Azure AD 설정을 위한 신뢰할 수 있는 콘텐츠 및 관련 절차는 Azure AD 문서에서 [관리되는 도메인에 대한 하이브리드 Azure AD 조인 구성](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains)을 참조하세요.  


#### <a name="configure-a-hybrid-azure-ad-join-using-azure-ad-connect"></a>Azure AD Connect를 사용하여 하이브리드 Azure AD 조인 구성

1. [최신 버전의 Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)(1.1.819.0 이상)를 다운로드하여 설치합니다.  
2. Azure AD Connect를 시작한 다음, **구성**을 선택합니다.
3. **추가 작업** 페이지에서 **디바이스 옵션 구성**을 선택하고 **다음**을 선택합니다.
4. **개요** 페이지에서 **다음**을 선택합니다.
5. **Azure AD에 연결** 페이지에서 Azure AD 테넌트에 대한 전역 관리자의 자격 증명을 입력합니다.
6. **디바이스 옵션** 페이지에서 **하이브리드 Azure AD 조인 구성**을 선택하고 **다음**을 선택합니다.
7. **디바이스 운영 체제** 페이지에서 Active Directory 환경 내에 디바이스가 사용하는 운영 체제를 선택하고 **다음**을 선택합니다.  

   Windows 하위 수준 도메인 조인 디바이스를 지원하는 옵션을 선택할 수 있지만, 디바이스의 공동 관리는 Windows 10에서만 지원된다는 점에 유의하세요.
8. **SCP** 페이지에서 Azure AD Connect가 SCP(서비스 연결 지점)를 구성할 각 온-프레미스 포리스트에 대해 다음 단계를 완료한 후 **다음**을 선택합니다.  
   1. 포리스트를 선택합니다.  
   2. 인증 서비스를 선택합니다.  페더레이션된 도메인이 있는 경우 조직에 Windows 10 클라이언트만 있지 않고 컴퓨터/디바이스 동기화를 구성하지 않았거나 조직에서 [SeamlessSSO](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)를 사용하지 않는다면 AD FS 서버를 선택합니다.  
   3. **추가**를 클릭하여 엔터프라이즈 관리자 자격 증명을 입력합니다.  
9. 관리되는 도메인에 있으면 이 단계를 건너뜁니다.  

   **페더레이션 구성** 페이지에서 AD FS 관리자의 자격 증명을 입력하고 **다음**을 선택합니다.
10. **구성 준비** 페이지에서 **구성**을 선택합니다.
11. **구성 완료** 페이지에서 **종료**를 선택합니다.

도메인 조인된 Windows 디바이스에 대한 하이브리드 Azure AD 조인을 완료하는 데 문제가 발생한 경우 [현재 Windows 디바이스에 대한 하이브리드 Azure AD 조인 문제 해결](https://docs.microsoft.com/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current)을 참조하세요.


## <a name="configure-client-settings-to-direct-clients-register-with-azure-ad"></a>Azure AD를 사용하여 직접 클라이언트를 등록하도록 클라이언트 설정 구성  
클라이언트 설정을 사용하여 Azure AD에 자동으로 등록하도록 Configuration Manager 클라이언트를 구성합니다.  

1. **Configuration Manager 콘솔** > **관리** > **개요** > **클라이언트 설정**을 연 다음, **기본 클라이언트 설정**을 편집합니다.  

2. **Cloud Services**를 선택합니다.  

3. **기본 설정** 페이지에서 **Azure Active Directory에 새 Windows 10 도메인 조인된 디바이스를 자동으로 등록**을 **예**로 설정합니다.  

4. **확인**을 선택하여 이 구성을 저장합니다.  

## <a name="configure-auto-enrollment-of-devices-to-intune"></a>Intune에 대한 디바이스 자동 등록 구성   
이제 Intune으로 디바이스의 자동 등록을 설정하겠습니다. 자동 등록을 사용하면 Configuration Manager로 관리하는 디바이스가 자동으로 Intune에 등록됩니다.

또한 자동 등록이 있으면 사용자가 Windows 10 디바이스를 Intune에 등록할 수도 있습니다. 사용자가 개인 소유 디바이스에 회사 계정을 추가하거나, 회사 소유 디바이스가 Azure Active Directory에 조인되면 디바이스가 등록됩니다.  

1. [Azure Portal](https://portal.azure.com/)에 로그인하고 **Azure Active Directory** > **모바일(MDM 및 MAM)**  > **Microsoft Intune**을 선택합니다.  

2. **MDM 사용자 범위**를 구성합니다. 다음 중 하나를 지정하여 Microsoft Intune에서 관리하는 사용자의 디바이스를 구성하고 URL 값의 기본값을 수락합니다.  

   - **일부** - Windows 10 디바이스를 자동으로 등록할 수 있는 **그룹** 선택  

   - **모두** - 모든 사용자가 Windows 10 디바이스를 자동으로 등록할 수 있으며 **없음**으로 설정하면 MDM(모바일 디바이스 관리) 자동 등록이 사용하지 않도록 설정됨

   > [!IMPORTANT]  
   > **MAM 사용자 범위** 및 MDM 자동 등록(**MDM 사용자 범위**)이 모두 그룹에 대해 사용하도록 설정되어 있으면 MAM만 사용하도록 설정됩니다. 해당 그룹의 사용자가 개인 디바이스를 작업 공간에 연결하는 경우에는 해당 사용자에 대한 MAM(모바일 애플리케이션 관리)만 추가됩니다. 디바이스는 자동으로 MDM 등록되지 않습니다.  

3. 자동 등록의 구성을 완료하려면 **저장**을 선택합니다.  

4. **모바일(MDM 및 MAM)** 로 돌아간 다음, **Microsoft Intune 등록**을 선택합니다.  

5. MDM 사용자 범위의 경우 **모두**, **저장**을 차례로 선택합니다.  


## <a name="assign-intune-licenses-to-users"></a>사용자에게 Intune 라이선스 할당   
흔히 간과되지만 중요한 작업은 공동 관리되는 디바이스를 사용할 각 사용자에게 Intune 라이선스를 할당하는 것입니다.  

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

사용자에게 Intune에 대한 라이선스 할당에 대해 자세히 알아보려면 [라이선스 할당](https://docs.microsoft.com/intune/licenses-assign)을 참조하세요.


## <a name="enable-co-management-in-configuration-manager"></a>Configuration Manager에서 공동 관리 사용
하이브리드 Azure AD를 설정하면 Configuration Manager 클라이언트가 적절히 구성되고 사용자에게 제품 라이선스가 할당되며, Windows 10 디바이스의 공동 관리를 바로 전환 및 사용하도록 설정할 수 있습니다.  

> [!TIP]  
>  다음 절차의 6단계에서는 공동 관리를 위해 ‘파일럿 그룹’으로 컬렉션을 할당합니다.  이 그룹에는 공동 관리 구성을 테스트할 수 있는 소수의 클라이언트가 포함되어 있습니다. 절차를 시작하기 전에 적합한 컬렉션을 만드는 것이 좋습니다. 그러면 기존 절차를 종료하지 않고도 해당 컬렉션을 선택할 수 있습니다.  

1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.

2. [홈] 탭의 [관리] 그룹에서 **공동 관리 구성**을 선택하여 공동 관리 구성 마법사를 엽니다.

3. 구독 페이지에서 **로그인**을 선택하여 Intune 테넌트에 로그인하고 **다음**을 선택합니다.

4. 사용 페이지의 ‘Intune에서 자동 등록’ 드롭다운 목록에서 다음 옵션 중 하나를 선택합니다.   

   - **파일럿**  - ‘(권장)’ 지정하는 컬렉션의 멤버는 자동으로 Intune에 등록되어 공동으로 관리될 수 있습니다.  이 마법사의 ‘스테이징’ 페이지에서 파일럿 컬렉션을 지정합니다.  이 옵션을 사용하면 클라이언트의 하위 집합에서 공동 관리를 테스트할 수 있습니다. 그런 다음, 단계적 접근 방식을 사용하여 공동 관리를 추가 고객에게 출시할 수 있습니다.  

   - **모두** - 모든 클라이언트에 대한 공동 관리가 사용하도록 설정됩니다.  

5. 워크로드 페이지에서 **Configuration Manager**의 워크로드를 다음 중 하나로 전환할 수 있으며 계속할 준비가 되면 **다음**을 선택합니다.  

   - **파일럿 Intune** - 파일럿 그룹의 디바이스에 대해서만 워크로드를 전환합니다. 마법사의 다음 페이지에서는 파일럿 그룹으로 컬렉션을 할당합니다.  

   - **Intune** - 공동 관리되는 모든 Windows 10 디바이스에 대한 관련 워크로드를 전환합니다.  

   공동 관리를 사용하도록 설정할 때 워크로드를 전환할 필요가 없습니다. 공동 관리가 구성되면 나중에 Configuration Manager 콘솔에서 이 구성을 다시 방문할 수 있습니다.  

   워크로드를 전환하기 전에 Intune의 해당 워크로드가 구성되어 배포되었는지 확인하세요. 이 작업을 수행하면 워크로드를 계속 관리할 수 있습니다.  

6. 스테이징 페이지에서 **파일럿 컬렉션**에 대해 사용할 컬렉션을 지정하고 **다음**을 클릭합니다. 지정한 컬렉션은 공동 관리의 단계별 출시의 일부로 사용됩니다. 공동 관리 속성에서 언제든지 파일럿 그룹의 컬렉션을 변경할 수 있습니다.  

7. 마법사를 완료하려면 요약 페이지에서 **다음**을 선택한 다음, **닫기**를 선택합니다.  


## <a name="next-steps"></a>다음 단계
- [공동 관리 대시보드](/sccm/comanage/how-to-monitor)를 사용하여 공동 관리 디바이스 상태 검토
- 공동 관리에서 [즉치 값](quickstarts.md#immediate-value) 받기 시작
- [조건부 액세스](quickstart-conditional-access.md) 및 Intune 준수 규칙을 사용하여 회사 리소스에 대한 사용자 액세스 관리
