---
title: "System Center Configuration Manager 및 Microsoft Intune에서 Windows 하이브리드 장치 관리 설정 | Microsoft 문서"
description: "System Center Configuration Manager 및 Microsoft Intune에서 Windows 장치 관리 설정"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: 9
author: mtillman
ms.author: mtillman
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: a4fc4a16c78b0eaa0dcefdd596b049eacf1d255b
ms.lasthandoff: 03/06/2017


---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>System Center Configuration Manager 및 Microsoft Intune에서 Windows 하이브리드 장치 관리 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

Intune과 Configuration Manager를 사용하여 데스크톱, 노트북 및 Windows를 실행하는 다른 장치를 모바일 장치로 관리할 수 있습니다. Windows PC의 자동 등록을 허용하도록 Azure Active Directory를 설정할 수 있습니다. 또한 회사 포털 앱을 사용하여 등록을 단순화하도록 Configuration Manager를 구성할 수 있습니다.


Windows 등록 옵션은 다음과 같습니다.

- [Azure AD를 사용한 자동 등록](#azure-active-directory-enrollment)
- [Windows PC](#configure-windows-pc-enrollment)
- [Windows 10 Mobile 및 Windows Phone 장치](#enable-windows-phone-devices)

## <a name="azure-active-directory-enrollment"></a>Azure Active Directory 등록

자동 등록을 통해 사용자는 회사 또는 학교 계정을 추가하고 관리에 동의하여 회사 소유 또는 개인 Windows 10 PC 및 Intune의 Windows 10 Mobile 장치를 등록할 수 있습니다. 백그라운드에서 사용자의 장치가 Azure Active Directory를 등록하고 연결합니다. 등록이 되고 나면 Intune으로 장치를 관리할 수 있습니다.

**전제 조건**
- Azure Active Directory Premium 구독([평가판 구독](http://go.microsoft.com/fwlink/?LinkID=816845))
- Microsoft Intune 구독


### <a name="configure-automatic-mdm-enrollment"></a>자동 MDM 등록 구성

1. [Azure 관리 포털](https://manage.windowsazure.com)(https://manage.windowsazure.com)에서 **Active Directory** 노드로 이동하고 디렉터리를 선택합니다.

2. **응용 프로그램** 탭을 클릭하면 응용 프로그램 목록에 **Microsoft Intune**이 표시됩니다.

    ![Microsoft Intune에서 Azure AD 앱](../media/aad-intune-app.png)

3. **Microsoft Intune**에 대한 화살표를 클릭하면 Microsoft Intune을 구성할 수 있는 페이지가 표시됩니다.

4. **구성**을 클릭하여 Microsoft Intune으로 자동 MDM 등록을 구성하기 시작합니다.

5. Intune의 URL을 지정합니다.

  - **MDM 등록 URL** – 기본값을 사용합니다.
  - **MDM 사용 약관 URL** – 기본값을 사용합니다. 이 URL은 장치 등록 시 사용자에 대한 사용 약관을 표시합니다.
  - **MDM 준수 URL** – 기본값을 사용합니다. 장치가 준수하지 않는 것으로 확인되는 경우 **액세스 거부됨** 메시지가 이 URL과 함께 표시됩니다. 이 URL이 가리키는 페이지에서 장치가 정책을 준수하지 않는 이유와 다시 준수할 수 있는 방법을 확인할 수 있습니다.

6.  Microsoft Intune에서 관리해야 하는 사용자의 장치를 지정합니다. 이러한 사용자의 Windows 10 장치는 Microsoft Intune을 사용한 관리에 자동으로 등록됩니다.

  - **모두**
  - **그룹**
  - **없음**

7. **저장**을 선택합니다.

## <a name="configure-windows-pc-enrollment"></a>Windows PC 등록 구성
 Windows 모바일 장치 관리를 사용하려면 운영 체제에 대한 관리를 사용하도록 설정해야 합니다.  사용자의 등록을 단순화하기 위해 DNS CNAME을 추가할 수도 있습니다.

### <a name="create-dns-alias-for-device-enrollment"></a>장치 등록에 대한 DNS 별칭 만들기  
 DNS 별칭(CNAME 레코드 종류)을 사용하면 장치를 등록하는 동안 서버 이름이 자동으로 채워지므로 사용자가 보다 쉽게 장치를 등록할 수 있습니다. DNS 별칭(CNAME 레코드 종류)을 만들려면 회사의 DNS 레코드에서, 회사의 도메인에 있는 URL로 전송된 요청을 Microsoft의 클라우드 서비스 서버로 리디렉션하는 CNAME을 구성해야 합니다.  예를 들어 회사의 도메인이 contoso.com인 경우 DNS에 EnterpriseEnrollment.contoso.com을 EnterpriseEnrollment-s.manage.microsoft.com으로 리디렉션하는 CNAME을 만들어야 합니다.  

 CNAME DNS 항목을 만드는 것은 선택 사항이지만 CNAME 레코드를 사용하면 사용자가 보다 쉽게 등록할 수 있습니다. 등록 CNAME 레코드가 없으면 사용자에게 MDM 서버 이름인 enrollment.manage.microsoft.com을 수동으로 입력하라는 메시지가 표시됩니다.

|유형|호스트 이름|지시 대상|  
|----------|---------------|---------------|  
|CNAME|EnterpriseEnrollment.company_domain.com|EnterpriseEnrollment-s.manage.microsoft.com|  
|CNAME|EnterpriseRegistration.company_domain.com|EnterpriseRegistration.windows.net|  
### <a name="to-enable-enrollment-for-windows-devices"></a>Windows 장치에 대한 등록을 사용하려면 다음을 수행합니다.  

1.  **필수 조건** - 플랫폼에 대한 등록을 설정하려면 먼저 [하이브리드 MDM 설정](setup-hybrid-mdm.md)에서 필수 조건 및 절차를 완료합니다.  

2.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  

    > [!WARNING]  
    >  다른 Configuration Manager 대화 상자가 열려 있으면 모두 닫은 후 이 절차를 계속합니다.  

3.  **홈** 탭에서 **플랫폼 구성**, **Windows**를 차례로 클릭합니다.  

4.  **일반** 탭에서 **Windows 등록 사용**을 선택합니다.  

 설정한 후에는 사용자에게 장치를 등록하는 방법을 알려 주어야 합니다. [장치 등록에 대해 최종 사용자에게 알릴 내용](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)을 참조하세요. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 장치에 적용됩니다.

## <a name="enable-windows-phone-devices"></a>Windows Phone 장치를 사용하도록 설정  
  사용자가 Windows Phone 8.1 이상 장치만 등록하고 Windows Phone 장치에 LOB(기간 업무) 앱을 배포하지 않는 경우에는 Symantec 인증서가 필요하지 않습니다. Windows Phone 등록을 사용하도록 설정하면 사용자에게 Windows Phone 스토어에서 회사 포털 앱을 설치하여 자신의 장치를 등록하도록 지시해야 합니다.  

  관리하려는 Windows Phone 장치에 대해 다음 단계를 완료합니다.  

### <a name="to-enable-enrollment-for-windows-phone-81-and-later-devices"></a>Windows Phone 8.1 이상 장치에 대해 등록을 사용하려면 다음을 수행합니다.  

 1.  **필수 조건** - 플랫폼에 대한 등록을 설정하려면 먼저 [하이브리드 MDM 설정](setup-hybrid-mdm.md)에서 필수 조건 및 절차를 완료합니다.  

 2.  Configuration Manager 콘솔의 **관리 작업** 영역에서 **클라우드 서비스** > **Microsoft Intune 구독**으로 이동합니다.  

     > [!WARNING]  
     >  다른 Configuration Manager 대화 상자가 열려 있으면 모두 닫은 후 이 절차를 계속합니다.  

 3.  **홈** 탭에서 **플랫폼 구성**, **Windows Phone**을 차례로 클릭합니다.  

 4.  **일반** 탭에서  **Windows Phone 8.1 및 Windows 10 Mobile**을 선택합니다. AET.xml 파일 데이터 또는 .pfx 파일을 업로드하여 회사 포털의 배포를 지원하거나 Windows Phone 스토어에서 회사 포털을 다운로드하도록 사용자에게 알립니다.  

      **확인**을 클릭합니다.  

  설정한 후에는 사용자에게 장치를 등록하는 방법을 알려 주어야 합니다. [장치 등록에 대해 최종 사용자에게 알릴 내용](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune)을 참조하세요. 이 정보는 Microsoft Intune 및 Configuration Manager에서 관리되는 모바일 장치에 적용됩니다.  

  > [!div class="button"]
  [< 이전 단계](create-service-connection-point.md)  [다음 단계 >](set-up-additional-management.md)

