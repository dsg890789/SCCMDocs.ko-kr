---
title: "Microsoft Intune에서 Windows 하이브리드 장치 관리 설정"
titleSuffix: Configuration Manager
description: "System Center Configuration Manager 및 Microsoft Intune에서 Windows 장치 관리 설정"
ms.custom: na
ms.date: 03/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: "9"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: dd62748f853915d71fcbad1964f5a67785aaf3f6
ms.sourcegitcommit: 1132886e07d0c0a87dcc7eeef4577dd8d8840023
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/01/2017
---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune에서 Windows 하이브리드 장치 관리 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 IT 관리자가 사용자에게 Configuration Manager 및 Microsoft Intune을 사용하여 Windows PC 및 모바일 장치를 관리할 수 있도록 설정하는 방법을 설명합니다.

## <a name="enable-windows-device-management"></a>Windows 장치 관리 사용
PC 또는 모바일 장치에 대해 Windows 장치 관리를 사용하도록 설정하려면 다음 단계를 따릅니다.

1.  플랫폼에 대한 등록을 설정하려면 먼저 [하이브리드 MDM 설정](setup-hybrid-mdm.md)에서 필수 조건 및 절차를 완료합니다.  
2.  Configuration Manager 콘솔의 **관리** 작업 영역에서 **개요** > **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  
3.  리본 메뉴에서 **플랫폼 구성**을 선택하고 Windows 플랫폼을 선택합니다.
    - Windows PC 및 노트북의 경우 **Windows**를 선택하고 다음 단계를 수행합니다.
      1. **일반** 탭에서 **Windows 등록 사용** 확인란을 클릭합니다.
      2. 인증서를 사용하여 코드 서명하고 회사 포털 앱을 배포하는 경우 **코드 서명 인증서**를 찾습니다. 또한 장치 사용자가 Windows 스토어에서 회사 포털 앱을 설치할 수 있거나, 코드 서명하지 않고 비즈니스용 Windows 스토어에서 앱을 배포할 수 있습니다.
      3. [비즈니스용 Windows Hello 설정](windows-hello-for-business-settings.md)을 구성할 수도 있습니다.
    - Windows 휴대폰 및 태블릿의 경우 **Windows Phone**을 선택하고 다음 단계를 수행합니다.
      1. **일반** 탭에서 **Windows Phone 8.1 및 Windows 10 Mobile** 확인란을 클릭합니다. Windows Phone 8.0은 더 이상 지원되지 않습니다.
      2. 조직에서 회사 앱을 사이드로드해야 하는 경우 필요한 토큰 또는 파일을 업로드할 수 있습니다. 앱 사이드로드에 대한 자세한 내용은 [Windows 앱 만들기](https://docs.microsoft.com/sccm/apps/get-started/creating-windows-applications)를 참조하세요.
        - **응용 프로그램 등록 토큰**
        - **.pfx 파일**
        - **없음** Symantec 인증서를 사용하는 경우 **Show an alert before Symantec certificates expire**(Symantec 인증서가 만료되기 전에 경고 표시)를 지정할 수 있습니다.
4. **확인** 을 클릭하여 대화 상자를 닫습니다.  회사 포털을 사용하여 등록 프로세스를 간소화하려면 장치 등록에 대한 DNS 별칭을 만들어야 합니다. 그런 다음 사용자에게 장치 등록 방법을 알릴 수 있습니다.

## <a name="choose-how-to-enroll-windows-devices"></a>Windows 장치를 등록하는 방법 선택

Intune 라이선스를 사용자에게 할당하면 추가 단계 없이 Windows 장치를 등록할 수 있지만, 사용자를 위해 등록을 더 쉽게 만들 수 있습니다.

다음 두 가지 요소를 통해 Windows 장치 등록을 간소화하는 방법을 결정합니다.
- **Azure Active Directory Premium을 사용하나요?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium)은 Enterprise Mobility + Security 및 기타 라이선싱 계획에 포함되어 있습니다.
- **등록할 Windows 클라이언트 버전은 무엇인가요?** <br>Windows 10 장치는 회사 또는 학교 계정을 추가하여 자동으로 등록할 수 있습니다. 이전 버전은 회사 포털 앱을 사용하여 등록해야 합니다.

||**Azure AD Premium**|**기타 AD** |
|----------|---------------|---------------|  
|**Windows 10**|[자동 등록](#enable-windows-10-automatic-enrollment) |[사용자 등록](#enable-windows-enrollment-without-azure-ad-premium)|
|**이전 버전의 Windows**|[사용자 등록](#enable-windows-enrollment-without-azure-ad-premium)|[사용자 등록](#enable-windows-enrollment-without-azure-ad-premium)|

## <a name="enable-windows-10-automatic-enrollment"></a>Windows 10 자동 등록 사용

자동 등록을 통해 사용자는 회사 또는 학교 계정을 추가하고 관리에 동의하여 회사 소유 또는 개인 Windows 10 PC 및 Intune의 Windows 10 Mobile 장치를 등록할 수 있습니다. 이러기만 하면 됩니다. 백그라운드에서 사용자의 장치가 Azure Active Directory를 등록하고 연결합니다. 등록이 되고 나면 Intune으로 장치를 관리할 수 있습니다.

**전제 조건**
- Azure Active Directory Premium 구독([평가판 구독](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 구독


### <a name="configure-automatic-mdm-enrollment"></a>자동 MDM 등록 구성

1. [Azure 관리 포털](https://portal.azure.com) (https://manage.windowsazure.com) 에 로그인하여 **Azure Active Directory**를 선택합니다.

  ![Azure 포털의 스크린샷](../media/auto-enroll-azure-main.png)

2. **이동성(MDM 및 MAM)**을 선택합니다.

  ![Azure 포털의 스크린샷](../media/auto-enroll-mdm.png)

3. **Microsoft Intune**을 선택합니다.

  ![Azure 포털의 스크린샷](../media/auto-enroll-intune.png)

4. **MDM 사용자 범위**를 구성합니다. Microsoft Intune에서 관리해야 하는 사용자의 장치를 지정합니다. 이러한 사용자의 Windows 10 장치는 Microsoft Intune을 사용한 관리에 자동으로 등록됩니다.

    - **없음**
    - **일부**
    - **모두**

   ![Azure 포털의 스크린샷](../media/auto-enroll-scope.png)

5. 다음 URL의 기본값을 사용합니다.
    - **MDM 사용 약관 URL**
    - **MDM 검색 URL**
    - **MDM 규정 준수 URL**

6. **저장**을 선택합니다.


기본적으로 서비스에 대해 2단계 인증이 사용되도록 설정되지 않습니다. 그러나 장치를 등록할 때 2단계 인증이 권장됩니다. 이 서비스에 대해 2단계 인증을 요구하기 전에 Azure Active Directory에서 2단계 인증 공급자를 구성하고 다단계 인증에 대한 사용자 계정을 구성해야 합니다. [Azure Multi-Factor Authentication Server 시작](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud)을 참조하세요.

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Azure AD Premium을 사용하지 않고 Windows 등록 사용
사용자가 Azure AD Premium 자동 등록 없이도 장치를 등록하도록 할 수 있습니다. 라이선스를 할당하고 나면 작업 계정을 개인적으로 소유한 장치에 추가하거나 회사에서 소유한 장치를 Azure AD에 결합하여 등록할 수 있습니다. DNS 별칭(CNAME 레코드 유형)을 만들면 사용자가 자신의 장치를 쉽게 등록할 수 있습니다. DNS CNAME 리소스 레코드를 만들면 사용자가 Intune 서버 이름을 입력하지 않고도 Intune에서 연결 및 등록할 수 있습니다.

### <a name="create-cnames-to-simplify-enrollment"></a>CNAME을 만들어 등록을 단순화
회사의 도메인에 대한 CNAME DNS 리소스 레코드를 만듭니다. 예를 들어, 회사의 웹 사이트가 contoso.com인 경우 DNS에 EnterpriseEnrollment.contoso.com을 enterpriseenrollment-s.manage.microsoft.com으로 리디렉션하는 CNAME을 만듭니다.

CNAME DNS 항목을 만드는 것은 선택 사항이지만 CNAME 레코드를 사용하면 사용자가 보다 쉽게 등록할 수 있습니다. 등록 CNAME 레코드가 없으면 사용자에게 MDM 서버 이름인 enrollment.manage.microsoft.com을 수동으로 입력하라는 메시지가 표시됩니다.

|유형|호스트 이름|지시 대상|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com| 1시간|

UPN 접미사가 두 개 이상 있는 경우 각 도메인 이름에 대해 CNAME을 하나 만들고 EnterpriseEnrollment-s.manage.microsoft.com에 각각을 가리켜야 합니다. 예를 들어 Contoso의 사용자가 name@contoso.com을 사용하지만 메일/UPN으로 name@us.contoso.com 및 name@eu.constoso.com도 사용하는 경우 Contoso DNS 관리자는 다음 CNAME을 만들어야 합니다.

|유형|호스트 이름|지시 대상|TTL|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1시간|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1시간|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1시간|

`EnterpriseEnrollment-s.manage.microsoft.com` – 메일의 도메인 이름에서 도메인을 인식하여 Intune 서비스로 리디렉션을 지원합니다.

DNS 레코드 변경 내용이 전파되는 데는 최대 72시간이 걸릴 수 있습니다. DNS 레코드가 전파될 때까지 Intune의 DNS 변경 내용을 확인할 수 없습니다.

## <a name="tell-users-how-to-enroll-devices"></a>사용자에게 장치 등록 방법 알리기  

 설정한 후에는 사용자에게 장치를 등록하는 방법을 알려 주어야 합니다. 지침은 [장치 등록에 대해 사용자에게 알릴 내용](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)을 참조하세요. 사용자를 [Intune에서Windows 장치 등록](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows)으로 바로 이동시킬 수 있습니다. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 장치에 적용됩니다.

> [!div class="button"]
[< 이전 단계](create-service-connection-point.md)  [다음 단계 >](set-up-additional-management.md)
