---
title: 자습서&#58; 공동 관리 경로 1
titleSuffix: Configuration Manager
description: 이미 Configuration Manager에서 Windows 10 장치를 관리 하는 경우 Microsoft Intune을 사용 하 여 공동 관리를 구성 합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: tutorial
ms.assetid: 140c522f-d09a-40b6-a4b0-e0d14742834a
author: brenduns
ms.author: brenduns
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1aecb2c33c874717f1da979f1316d1b46b785071
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755265"
---
# <a name="tutorial-enable-co-management-for-existing-configuration-manager-clients"></a>자습서: 기존 Configuration Manager 클라이언트에 대 한 공동 관리를 사용 하도록 설정
공동 관리를 사용 하 여 Configuration Manager를 사용 하 여 조직의 Pc를 관리 하 여 잘 구성 된 프로세스를 유지할 수 있습니다. 동시에, 보안 및 최신 프로 비전에 대 한 Intune 사용 하 여 클라우드에서 투자는 있습니다.  

이 자습서에서는 이미 Configuration Manager에서 등록 된 Windows 10 장치의 공동 관리를 설정 합니다. 이 자습서는 Windows 10 장치를 관리 하려면 Configuration Manager를 이미 사용 하는 내부로 시작 합니다.

이 자습서를 사용 하는 경우:  

- Azure Active Directory (Azure AD)에 연결할 수 있는 온-프레미스 Active Directory를 Azure AD 하이브리드 구성에
- 클라우드 연결 하려는 기존 Configuration Manager 클라이언트가 있습니다


**이 자습서에서는 다음을 수행 해야합니다.**  
> [!div class="checklist"]  
> * Azure와 온-프레미스 환경에 대 한 필수 구성 요소 검토  
> * 하이브리드 Azure AD 설정  
> * Azure AD에 등록 하려면 Configuration Manager 클라이언트 에이전트를 구성 합니다.  
> * 장치를 자동으로 등록 하도록 Intune 구성  
> * 사용자에 게 Intune 라이선스 할당  
> * Configuration Manager에서 공동 관리를 사용 하도록 설정  


## <a name="prerequisites"></a>필수 구성 요소  

### <a name="azure-services-and-environment"></a>Azure 서비스 및 환경
- Azure 구독 ([무료 평가판](https://azure.microsoft.com/free))
- Azure Active Directory Premium
- Microsoft Intune 구독
  > [!TIP]  
  > Enterprise Mobility + Security (EMS) 구독에는 Azure Active Directory Premium 및 Microsoft Intune을 모두 포함 됩니다. EMS 구독 ([무료 평가판](https://www.microsoft.com/cloud-platform/enterprise-mobility-security-trial)).  

사용자 환경에서 아직 없는 경우이 자습서에서 표시 됩니다.
- 사용자 라이선스를 할당 *Intune* 한 *Azure Active Directory Premium*
- 구성할 [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-select-installation) 테 넌 트 온-프레미스 Active Directory와 Azure Active Directory (AD) 간의


### <a name="on-premises-infrastructure"></a>온-프레미스 인프라
- A [지원 되는 버전](https://docs.microsoft.com/sccm/core/servers/manage/updates#supported-versions) System Center Configuration Manager 현재 분기의
- 합니다 [MDM 기관을](https://docs.microsoft.com/sccm/mdm/deploy-use/change-mdm-authority) Intune로 설정 되어야 합니다  


### <a name="permissions"></a>사용 권한
이 자습서 전체에서 작업을 완료 하려면 다음 사용 권한을 사용 합니다.  
- 인 계정으로는 *전역 관리자* Azure에서  
- 인 계정으로는 *도메인 관리자* 온-프레미스 인프라에서  
- 인 계정으로는 *전체 관리자* 에 대 한 *모든* 범위 in Configuration Manager   

## <a name="set-up-hybrid-azure-ad"></a>하이브리드 Azure AD 설정
하이브리드 Azure AD 설정 하는 경우 실제로 설정 하는 통합 온-프레미스 AD와 Azure AD Connect 및 페더레이션 서비스 ADFS (Active Directory)를 사용 하 여 Azure AD입니다. 구성을 성공적으로 사용 하 여 작업 자가 원활 하 게 로그인 할 수 온-프레미스를 사용 하 여 외부 시스템 AD 자격 증명입니다.

> [!IMPORTANT]  
> 이 자습서에는 하이브리드 관리 되는 도메인에 대 한 Azure AD 설정 하는 핵심 프로세스 자세히 설명 합니다. 프로세스에 숙지 하는 것이 좋습니다를 이해 하 고 Azure AD 하이브리드 배포를 가이드로이 자습서에 의존 하지 않고 있습니다.
>
> 하이브리드 Azure AD에 대 한 자세한 내용은 Azure Active Directory 설명서에서 다음 문서를 사용 하 여 시작 합니다.
> - [Azure AD 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)
> -  [하이브리드 Azure AD 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)
> -  [하이브리드 Azure AD 조인 장치를 제어 합니다.](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-control)
> -  [페더레이션된 도메인에 대 한 하이브리드 Azure AD 조인 구성](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-federated-domains)  


### <a name="set-up-azure-ad-connect"></a>Azure AD Connect 설정  
하이브리드 Azure AD에 동기화를 유지할 컴퓨터 계정 온-프레미스 Active Directory (AD) 및 장치 개체를 Azure AD에서 Azure AD Connect 구성을 해야 합니다.

Azure AD Connect는 1.1.819.0 버전부터, 하이브리드 Azure AD 조인을 구성 하는 마법사를 사용 하 여를 제공 합니다. 마법사의 사용 하 여 구성 프로세스를 간소화합니다.  

Azure AD Connect를 구성 하려면 Azure AD 테 넌 트에 대 한 전역 관리자의 자격 증명이 필요 합니다.  

> [!TIP]  
> 다음 절차의 Azure AD Connect 설정에 대 한 신뢰할 수 있는 것으로 간주 해야 하지만 제공 하는 데 Intune과 Configuration Manager 간의 공동 관리의 구성을 간소화 합니다. 이 신뢰할 수 있는 콘텐츠에 대 한 Azure AD의 설정에 대 한 관련된 절차를 살펴보고 [관리 되는 도메인에 대 한 하이브리드 Azure AD 조인 구성](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-managed-domains) 에서 Azure AD 설명서.  


#### <a name="configure-a-hybrid-azure-ad-join-using-azure-ad-connect"></a>Azure AD Connect를 사용 하 여 하이브리드 Azure AD 조인 구성

1. 가져오기 및 설치 합니다 [최신 버전의 Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) (1.1.819.0 이상).  
2. Azure AD Connect를 시작 하 고 선택한 **구성**합니다.
3. 에 **추가 작업** 페이지에서 **장치 옵션 구성**를 선택한 후 **다음**합니다.
4. 에 **개요** 페이지에서 **다음**합니다.
5. 에 **Azure AD에 연결** 페이지에서 Azure AD 테 넌 트에 대 한 전역 관리자 자격 증명을 입력 합니다.
6. 에 **장치 옵션** 페이지에서 **구성 하이브리드 Azure AD 조인**를 선택한 후 **다음**합니다.
7. 에 **SCP** 페이지에 대 한 각 온-프레미스 포리스트에 서비스 연결 지점 (SCP)를 구성, 다음 단계를 수행 하 고 선택한 Azure AD Connect를 원하는 **다음**:  
   1. 포리스트를 선택 합니다.  
   2. 인증 서비스를 선택 합니다.  페더레이션된 도메인에 있는 경우 조직에 독점적으로 Windows 10 클라이언트 및 컴퓨터/장치 동기화를 구성한 경우 또는 조직에서 사용 하지 않는 한 AD FS 서버를 선택 [SeamlessSSO](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)합니다.  
   3. 클릭 **추가** 엔터프라이즈 관리자 자격 증명을 입력 합니다.  
8. 에 **장치 운영 체제** 페이지, Active Directory 환경의 장치에서 사용 되는 운영 체제를 선택 하 고, 선택한 **다음**합니다.  

   Windows 하위 수준 도메인에 가입 된 장치를 지원 하지만 유지 하는 옵션을 선택할 수 있습니다 유의 공동 관리를 사용 하는 장치 에서만 Windows 10에 대 한 지원 됩니다.

9. 관리 되는 도메인에 있는 경우이 단계를 건너뜁니다.  

   에 **페더레이션 구성** 페이지에서 AD FS 관리자에 게 자격 증명을 입력 하 고 선택한 **다음**합니다.
10. 에 **구성할 준비가** 페이지에서 **구성**합니다.
11. 에 **구성을 완료할** 페이지에서 **종료**합니다.

문제가 있는 경우 하이브리드 Azure AD를 완료 된 도메인에 대 한 조인 가입 Windows 장치를 참조 하십시오 [Windows 현재 장치에 대 한 문제 해결 하이브리드 Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/troubleshoot-hybrid-join-windows-current)합니다.


## <a name="configure-client-settings-to-direct-clients-register-with-azure-ad"></a>Azure AD를 사용 하 여 클라이언트 등록을 직접 하도록 클라이언트 설정 구성  
클라이언트 설정을 사용 하 여 Azure AD에 자동으로 등록 하도록 Configuration Manager 클라이언트를 구성 합니다.  

1. 엽니다는 **Configuration Manager 콘솔** > **관리** > **개요** > **클라이언트 설정** 를 선택한 다음 편집 합니다 **기본 클라이언트 설정**합니다.  

2. 선택 **Cloud Services**합니다.  

3. 에 **기본 설정** 페이지에서 설정 **자동으로 Azure Active Directory를 사용 하 여 새 Windows 10 도메인 가입 장치를 등록할** = **예**합니다.  

4. **확인**을 선택하여 이 구성을 저장합니다.  

## <a name="configure-auto-enrollment-of-devices-to-intune"></a>Intune로 장치 자동 등록 구성   
다음으로, Intune로 장치 자동 등록 설정 됩니다. 자동 등록을 사용 하 여 Configuration Manager를 자동으로 관리 하는 장치는 Intune에 등록 합니다.

자동 등록에는 또한 Intune에 Windows 10 장치를 등록할 수가 있습니다. 장치는 사용자가 회사 계정을 개인적으로 소유한 장치를 추가 하는 경우 또는 회사 소유의 장치를 Azure Active Directory에 가입할 때 등록 됩니다.  

1. 에 로그인 합니다 [Azure portal](https://portal.azure.com/) 선택한 **Azure Active Directory** > **이동성 (MDM 및 MAM)** > **Microsoft Intune** .  

2. 구성할 **MDM 사용자 범위**합니다. Microsoft Intune에서 관리 되는 사용자의 장치를 구성 하려면 다음 중 하나를 지정 하 고 URL 값에 대 한 기본값을 사용 합니다.  

   - **일부** -선택 된 **그룹** Windows 10 장치를 자동으로 등록할 수 있는  

   - **모든** -모든 사용자로 설정 된 경우 Windows 10 장치를 자동으로 등록할 수 있습니다 **None**, 자동 모바일 장치 관리 (MDM) 등록을 사용할 수 없습니다.

   > [!IMPORTANT]  
   > 둘 다 **MAM 사용자 범위** 및 자동 MDM 등록 (**MDM 사용자 범위**) 사용 하도록 설정 된 그룹에 대해 MAM만 사용 하도록 설정 합니다. 해당 그룹의 사용자만 응용 프로그램 관리 (MAM (모바일) 추가 되었습니다 경우 해당 공간을 개인 장치입니다. 자동으로 장치는 MDM 등록 되지 않습니다.  

3. 선택 **저장할** 자동 등록 구성을 완료 하려면.  

4. 돌아갑니다 **이동성 (MDM 및 MAM)** 선택한 후 **Microsoft Intune 등록**합니다.  

5. MDM 사용자 범위에 대 한 선택 **모든**를 차례로 **저장**합니다.  


## <a name="assign-intune-licenses-to-users"></a>사용자에 게 Intune 라이선스 할당   
일반적으로 간과 되는 중요 한 작업을 공동 관리 장치를 사용 하 여 각 사용자에 게 Intune 라이선스를 할당 하는 경우  

사용자 그룹에 라이선스를 할당 하려면 Azure Active Directory를 사용 합니다.  

1. 에 로그인 합니다 [Azure portal](https://portal.azure.com/) 관리자 계정으로 합니다. 라이선스를 관리 하려면 계정은 전역 관리자 역할 또는 사용자 계정 관리자 여야 합니다.  

2. 선택 **모든 서비스** 의 왼쪽된 탐색창에서 선택한 후 **Azure Active Directory**합니다.  

3. 에 **Azure Active Directory** 창 **라이선스** 참조 하 고 테 넌 트의 모든 라이선스 대상 제품을 관리할 수 있는 창을 엽니다.  

4. 아래 **All products**Intune 라이선스를 포함 하 여 제품 옵션을 선택 하 고 선택한 **할당** 창의 맨 위에 있는 합니다.  

   예를 들어, 선택할 수 있습니다 **Enterprise Mobility + Security E5** Intune 가져와야 하는 방법을 하는 경우.  

5. 에 **라이선스 할당** 창 클릭 **사용자 및 그룹** 열려는 합니다 **사용자 및 그룹** 창입니다. 그룹 및 개별 사용자 라이선스를 할당 하려는 사용자를 선택 합니다.  클릭 **선택** 해당 선택 영역을 확인 하 고 창 맨 아래에 있습니다.  

6. 에 **라이선스 할당** 창 클릭 **할당 옵션** 이전에 선택한 제품에 포함 하는 모든 서비스 계획을 표시 하려면. Intune과 같은 단일 제품을 선택한 경우 해당 제품에만 표시 됩니다.  
   - 설정할 **Microsoft Intune** 하 **에서**합니다.  
   - 각 사용자에 대 한 라이선스 할당 **Azure Active Directory Premium**합니다.  

   해당 라이선스를 할당 하면 선택할 **확인**합니다.  

7. 할당을 완료 하는 **라이선스 할당** 창 클릭 **할당** 창의 맨 아래에 있습니다.

8. 상태 및 프로세스의 결과 보여 주는 오른쪽 위 구석에 알림이 표시 됩니다. (예를 들어, 기존 라이선스 그룹에)으로 인해 그룹에 대 한 할당을 완료할 수 없습니다, 경우에 실패의 세부 정보를 보려면 알림을 클릭 합니다.

사용자에 게 intune 라이선스를 할당 하는 방법에 대 한 자세한 내용은 참조 하세요. [라이선스를 할당](https://docs.microsoft.com/intune/licenses-assign)합니다.


## <a name="enable-co-management-in-configuration-manager"></a>Configuration Manager에서 공동 관리를 사용 하도록 설정
하이브리드 Azure AD 설정, Configuration Manager 클라이언트 구성 및 사용자에 게 할당 된 제품 라이선스를 사용 하 여 준비가 스위치를 대칭 이동 하 고 Windows 10 장치의 공동 관리를 사용 하도록 설정 합니다.  

> [!TIP]  
>  다음 절차의 6 단계에서 컬렉션으로 할당 하 게 됩니다는 *파일럿 그룹* 공동 관리에 대 한 합니다. 공동 관리 구성을 테스트 하기 위해 클라이언트의 작은 수를 포함 하는 그룹입니다. 절차를 시작 하기 전에 적합 한 컬렉션을 만들어야 하는 것이 좋습니다. 그런 다음 작업을 수행 하는 절차를 종료 하지 않고 해당 컬렉션을 선택할 수 있습니다.  

1. Configuration Manager 콘솔에서 **관리** > **개요** > **클라우드 서비스** > **공동 관리**로 이동합니다.

2. 관리 그룹의 홈 탭에서 선택 **공동 관리 구성** 공동 관리 구성 마법사를 엽니다.

3. 구독 페이지에서 선택 **로그인** Intune 테 넌 트에 로그인 하 고 선택한 **다음**합니다.

4. 사용 페이지의에서 *Intune에서 자동 등록* 드롭다운 목록에서 다음 옵션 중 하나를 선택 합니다.  

   - **파일럿**  - *(권장)* 지정한 컬렉션의 멤버는 자동으로 Intune에 등록 및 공동으로 관리 될 수 있습니다. 파일럿 컬렉션을 지정 합니다 *스테이징* 이 마법사의 페이지입니다. 이 옵션을 사용 하면 클라이언트의 하위 집합에서 공동 관리를 테스트할 수 있습니다. 다음 단계별된 접근 방식을 사용 하 여 추가 클라이언트에 공동 관리를 롤아웃할 수 있습니다.  

   - **모든** -모든 클라이언트에 대 한 공동 관리를 사용 합니다.  

5. 페이지의 워크 로드에서 워크 로드를 전환할 수 있습니다 **Configuration Manager** , 다음 중 하나를 선택한 후 계속 준비가 되 면 **다음**합니다.  

   - **Intune 파일럿** -파일럿 그룹의 장치에 대해서만 워크 로드를 전환 합니다. 마법사의 다음 페이지에서 파일럿 그룹으로 컬렉션을 할당할 수 있습니다.  

   - **Intune** -공동 관리 하는 모든 Windows 10 장치에 대 한 연결된 워크 로드를 전환 합니다.  

   공동 관리를 사용 하도록 설정 하면 시간에는 모든 워크 로드를 전환할 필요가 없습니다. 공동 관리를 구성한 후 나중에이 구성 된 Configuration Manager 콘솔에서이 다시 방문할 수 있습니다.  

   워크 로드를 전환 하기 전에 Intune에서 해당 작업을 구성 하 고 배포에 있는지 확인 합니다. 관리 되는 유지 하므로 워크 로드를 수행 합니다.  

6. 준비 페이지에 사용할 컬렉션을 지정 합니다 **파일럿 컬렉션**를 클릭 하 고 **다음**합니다. 지정한 컬렉션은 공동 관리의 단계별된 롤아웃 중 일부로 사용 됩니다. 공동 관리 속성에서 언제든지 파일럿 그룹의 컬렉션을 변경할 수 있습니다.  

7. 요약 페이지에서 선택 **다음**를 차례로 **닫기** 마법사를 완료 합니다.  


## <a name="next-steps"></a>다음 단계
- 공동 관리 하는 장치의 상태를 검토 하 여 [공동 관리 대시보드](/sccm/comanage/how-to-monitor)
- 시작 [즉 치 값](quickstarts.md#immediate-value) 공동 관리
- 사용 하 여 [조건부 액세스](quickstart-conditional-access.md) 및 회사 리소스에 대 한 사용자 액세스를 관리 하려면 Intune 규정 준수 규칙
