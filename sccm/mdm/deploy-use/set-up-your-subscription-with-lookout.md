---
title: Lookout 구독 설정
titleSuffix: Configuration Manager
description: Lookout 모바일 위협 방어를 구성하는 방법에 대해 알아봅니다.
ms.date: 05/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 56b1ed9f22aeab073bb936ae525c3dec3c422837
ms.sourcegitcommit: 7f64c5fb3e9fa3dba006af618b1f1ceaf61a99f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75519779"
---
# <a name="set-up-your-subscription-for-lookout-mobile-threat-defense"></a>Lookout 모바일 위협 방어에 대한 구독 설정

*적용 대상: Configuration Manager (현재 분기)*

Lookout 모바일 위협 방어 구독을 설정하려면 다음 단계가 필요합니다.

| #        |단계  |
| ------------- |-------------|
| 1 | [Azure AD 정보 수집](#collect-azure-ad-information) |
| 2 | [구독 구성](#configure-your-subscription) |
| 3 | [등록 그룹 구성](#configure-enrollment-groups) |
| 4 | [상태 동기화 구성](#configure-state-sync) |
| 5 | [오류 보고서 이메일 받는 사람 정보 구성](#configure-error-report-email-recipient-information) |
| 6 | [등록 설정 구성](#configure-enrollment-settings) |
| 7 | [메일 알림 구성](#configure-email-notifications) |
| 8 | [위협 분류 구성](#configure-threat-classification) |
| 9 | [등록 감시](#watching-enrollment) |


> [!IMPORTANT]  
> Azure AD 테넌트와 연결되지 않은 기존 Lookout Mobile Endpoint Security 테넌트는 Azure AD 및 Intune과 통합에 사용할 수 없습니다. 새 Lookout Mobile Endpoint Security 테넌트를 만들려면 Lookout 지원 센터로 문의하세요. 새 테넌트를 사용하여 Azure AD 사용자를 등록할 수 있습니다.




## <a name="collect-azure-ad-information"></a>Azure AD 정보 수집
Lookout Mobility Endpoint Security 테넌트가 Azure AD 구독과 연결되어 Lookout을 Intune과 통합합니다. Lookout 모바일 위협 방어 서비스 구독을 사용하도록 설정하려면 Lookout 지원 팀(enterprisesupport@lookout.com)은 다음 정보가 필요합니다.

- **Azure AD 테넌트 ID**
- *전체* Lookout 콘솔 액세스를 위한 **Azure AD 그룹 개체 ID**
- *제한된* Lookout 콘솔 액세스를 위한 **Azure AD 그룹 개체 ID**(선택 사항)

Lookout 지원 팀에게 제공해야 하는 정보를 수집하려면 다음 단계를 사용하세요.

1. [Azure Portal](https://portal.azure.com)에 로그인하고 구독을 선택합니다. 

2. 구독 이름을 선택하면 결과로 표시되는 URL에 구독 ID가 포함됩니다. 구독 ID를 찾는 동안 문제가 발생하는 경우 구독 ID 찾기에 대한 팁을 보려면 [Microsoft 지원 문서](https://support.office.com/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b)를 참조하세요.

3. Azure AD 그룹 ID를 찾습니다.  
     > [!NOTE]   
     > **그룹 개체 ID**는 Azure Portal의 Azure AD 블레이드에서 그룹의 **속성** 페이지에 있습니다.  

   Lookout 콘솔은 다음 두 가지 수준의 액세스를 지원합니다.  

   - **모든 권한:** Azure AD 관리자는 모든 권한이 있는 사용자 그룹을 만들고, 선택적으로 제한된 권한이 있는 사용자 그룹을 만들 수 있습니다. 이러한 그룹의 사용자만 **Lookout 콘솔**에 로그인할 수 있습니다.
   - **제한된 권한:** 이 그룹의 사용자는 Lookout 콘솔의 여러 구성 및 등록 관련 모듈에 대한 액세스 권한이 없으며, Lookout 콘솔의 **보안 정책** 모듈에 대한 읽기 전용 액세스 권한을 갖습니다.  

     > [!TIP]  
     > 사용 권한에 대한 자세한 내용은 [이 Lookout 지원 문서](https://personal.support.lookout.com/hc/articles/114094105653)를 참조하십시오.


4. 이 정보를 수집한 후 Lookout 지원 센터로 문의하세요(메일: enterprisesupport@lookout.com). Lookout 지원 센터는 주 담당자와 협력하여 구독을 등록하고 수집한 정보를 사용하여 Lookout Enterprise 계정을 만듭니다.



## <a name="configure-your-subscription"></a>구독 구성

1. Lookout 지원 팀에서 Lookout 엔터프라이즈 계정을 만든 후 Lookout에서 [로그인 url](https://aad.lookout.com/les?action=consent)이 포함된 이메일이 회사의 주 담당자에게 전송됩니다.

2. Lookout 콘솔에 첫 로그인은 Azure AD 테넌트를 등록하려면 Azure AD 역할이 전역 관리자인 사용자 계정을 사용해야 합니다. 나중에 로그인은 이 수준의 Azure AD 권한을 요구하지 않습니다. 동의 페이지가 표시됩니다. **동의**를 선택하여 등록을 완료합니다. 동의하고 승인하면 Lookout 콘솔로 리디렉션됩니다.

   ![Lookout 콘솔의 첫 번째 로그인 페이지 스크린샷](media/lookout-initial-login.png)

3. [Lookout 콘솔](https://aad.lookout.com)의 **시스템** 모듈에서 **커넥터** 탭을 선택한 다음, **Intune**을 선택합니다.

   ![커넥터 탭이 열려 있고 Intune 옵션이 강조 표시된 Lookout 콘솔 스크린샷](media/lookout-setup-intune-connector.png)

4. **커넥터** > **연결 설정**으로 이동하여 분 단위로 **하트비트 빈도**를 지정합니다.

   ![구성된 하트비트 빈도를 보여 주는 연결 설정 탭 스크린샷](media/lookout-connection-settings.png)



## <a name="configure-enrollment-groups"></a>등록 그룹 구성
1. 모범 사례로 Lookout 통합을 테스트하는 작은 수의 사용자가 포함된 [Azure Portal](https://portal.azure.com)에서 Azure AD 보안 그룹을 만듭니다.

    > [!NOTE]  
    > 식별되고 지원되는 Azure AD 내 등록 그룹 사용자의 모든 Lookout 지원, Intune 등록 디바이스가 Lookout MTD 콘솔에 등록되며 활성화할 수 있습니다.

2. [Lookout 콘솔](https://aad.lookout.com)의 **시스템** 모듈에서 **커넥터** 탭, **등록 관리**를 차례로 선택하여 Lookout에서 해당 디바이스를 등록해야 하는 사용자 집합을 정의합니다. 등록을 위해 Azure AD 보안 그룹 **표시 이름**을 추가합니다.

    ![Intune 커넥터 등록 페이지 스크린샷](media/lookout-enrollment.png)

    >[!IMPORTANT]  
    > **표시 이름**은 Azure Portal에서 보안 그룹의 **속성**에 표시된 것처럼 대/소문자를 구분합니다. 아래 그림에 표시된 것처럼 보안 그룹의 **표시 이름**은 카멜식 대/소문자입니다. 반면 제목은 모두 소문자입니다. Lookout 콘솔에서 보안 그룹에 대한 **표시 이름** 대/소문자를 일치시킵니다.
    >![Azure Portal, Azure Active Directory 서비스, 속성 페이지 스크린샷](media/aad-group-display-name.png)

    >[!NOTE]  
    >새 디바이스를 확인할 시간 증분에 기본값 5분을 사용하는 것이 좋습니다. 현재 제한 사항, **Lookout은 그룹 표시 이름의 유효성을 확인할 수 없습니다:** Azure Portal에서 **표시 이름** 필드는 Azure AD 보안 그룹과 정확히 일치하도록 합니다. **중첩 그룹 만들기는 지원되지 않습니다:** Lookout에 사용된 Azure AD 보안 그룹에는 사용자만 포함돼야 합니다. 다른 그룹을 포함할 수 없습니다.

3.  그룹이 추가된 후 다음번에 사용자가 지원되는 해당 디바이스에서 Lookout for Work 앱을 열면 디바이스가 Lookout에서 활성화됩니다.

4.  결과에 만족하면 추가 사용자 그룹으로 등록을 확장합니다.



## <a name="configure-state-sync"></a>상태 동기화 구성
**상태 동기화** 옵션에서 Intune에 보내야 하는 데이터 형식을 지정합니다. Lookout Intune 통합이 제대로 작동하려면 디바이스 상태와 위협 상태가 둘 다 필요합니다. 이러한 설정은 기본적으로 사용하도록 설정됩니다.



## <a name="configure-error-report-email-recipient-information"></a>오류 보고서 이메일 받는 사람 정보 구성
**오류 관리** 옵션에서 오류 보고서를 받을 메일 주소를 입력합니다.

![Intune 커넥터 오류 관리 페이지 스크린샷](media/lookout-connector-error-notifications.png)



## <a name="configure-enrollment-settings"></a>등록 설정 구성
**커넥터** 페이지의 **시스템** 모듈에서 디바이스 연결이 끊긴 것으로 간주되는 일 수를 지정합니다. 연결이 끊긴 디바이스는 비규격으로 간주되며 SCCM 조건부 액세스 정책에 따라 회사 애플리케이션에 액세스할 수 없습니다. 1일에서 90일 사이의 값을 지정할 수 있습니다.

![Lookout 등록 설정](media/lookout-console-enrollment-settings.png)



## <a name="configure-email-notifications"></a>메일 알림 구성
위협에 대한 메일 경고를 받으려면 알림을 받을 사용자 계정으로 [Lookout 콘솔](https://aad.lookout.com)에 로그인합니다. **시스템** 모듈의 **기본 설정** 탭에서 알림을 받아야 하는 위협 수준을 선택하고 **ON**으로 설정합니다. 변경 내용을 저장합니다.

![사용자 계정이 표시된 기본 설정 페이지 스크린샷](media/lookout-email-notifications.png) 메일 알림을 더 이상 받지 않으려면 알림을 OFF로 설정하고 변경 내용을 저장합니다.



## <a name="configure-threat-classification"></a>위협 분류 구성
Lookout 모바일 위협 방어는 다양한 유형의 모바일 위협을 분류합니다. [Lookout 위협 분류](https://personal.support.lookout.com/hc/articles/114094130693)에는 기본 위험 수준이 연결되어 있습니다. 이러한 설정은 언제든지 회사 요구 사항에 맞게 변경할 수 있습니다.

![위협 및 분류를 보여 주는 정책 페이지 스크린샷](media/lookout-threat-classification.png)

>[!IMPORTANT]  
> 위험 수준은 위협 모바일 방어의 중요한 측면입니다. Intune 통합은 런타임 시 이러한 위험 수준에 따라 디바이스 준수를 계산합니다. Intune 관리자가 디바이스에 최소 수준의 활성 위협(**높음**, **중간** 또는 **낮음**)이 있다면 디바이스가 규정을 준수하지 않는 것으로 식별하도록 정책 규칙을 설정할 수 있습니다. Lookout 모바일 위협 방어의 위협 분류 정책은 직접적으로 Intune에서 디바이스 준수 계산을 실행합니다.



## <a name="watching-enrollment"></a>등록 감시
설치가 완료되면 Lookout 모바일 위협 방어에서 지정한 등록 그룹에 해당하는 디바이스를 Azure AD에 폴링하기 시작합니다. 등록된 디바이스에 대한 정보는 디바이스 모듈에서 찾을 수 있습니다. 디바이스의 초기 상태는 보류 중으로 표시됩니다. 디바이스에서 Lookout for Work 앱을 설치하고 열고 활성화하면 디바이스 상태가 변경됩니다. Lookout for Work 앱을 디바이스에 푸시하는 방법에 대한 자세한 내용은 [Lookout for Work 구성 및 배포](configure-and-deploy-lookout-for-work-apps.md)를 참조하세요.


## <a name="next-steps"></a>다음 단계
[Intune에서 Lookout MTP 연결 사용](enable-lookout-connection-in-intune.md)
