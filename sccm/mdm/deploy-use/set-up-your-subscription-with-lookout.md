---
title: "Lookout을 사용하여 구독 설정 | System Center Configuration Manager"
description: "이 항목에서는 Lookout 장치 위협 방지를 구성하는 방법을 자세히 설명합니다."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6087b279-ba05-4824-b5e3-3af14f3d3cfe
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: b777140c753e709f4048a30e63d8ae730d3e8723
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="set-up-your-subscription-for--lookout-device-threat-protection"></a>Lookout 장치 위협 방지에 대해 구독 설정

*적용 대상: System Center Configuration Manager(현재 분기)*

Lookout 장치 위협 방지 서비스에 대해 구독을 준비하려면 Lookout 지원(enterprisesupport@lookout.com)에 Azure AD(Azure Active Directory) 구독에 대한 다음 정보가 필요합니다. Lookout을 Intune과 통합하기 위해 Lookout Mobility Endpoint Security 테넌트는 Azure AD 구독과 연결됩니다. 

* **Azure AD 테넌트 ID**
* **전체** Lookout 콘솔 액세스를 위한 **Azure AD 그룹 개체 ID**
* **제한된** Lookout 콘솔 액세스를 위한 **Azure AD 그룹 개체 ID**(선택 사항)

> [!IMPORTANT]
> Azure AD 테넌트와 연결되지 않은 기존 Lookout Mobile Endpoint Security 테넌트는 Azure AD 및 Intune과 통합에 사용할 수 없습니다. 새 Lookout Mobile Endpoint Security 테넌트를 만들려면 Lookout 지원 센터로 문의하세요. 새 테넌트를 사용하여 Azure AD 사용자를 등록할 수 있습니다.

Lookout 지원 팀에게 제공해야 하는 정보를 수집하려면 다음 섹션을 사용하세요.  

## <a name="get-your-azure-ad-information"></a>Azure AD 정보 가져오기
### <a name="azure-ad-tenant-id"></a>Azure AD 테넌트 ID
[Azure AD 관리 포털](https://manage.windowsazure.com)에 로그인하고 구독을 선택합니다. 

![테넌트 이름을 표시하는 Azure AD 페이지의 스크린샷](media/aad_tenant_name.png) 구독 이름을 선택하면 결과 URL에 구독 ID가 포함됩니다.  구독 ID를 찾는 동안 문제가 발생하는 경우 구독 ID 찾기에 대한 팁을 보려면 [Microsoft 지원 문서](https://support.office.com/en-us/article/Find-your-Office-365-tenant-ID-6891b561-a52d-4ade-9f39-b492285e2c9b?ui=en-US&rs=en-US&ad=US)를 참조하세요.   
### <a name="azure-ad-group-id"></a>Azure AD 그룹 ID
Lookout 콘솔은 다음 두 가지 수준의 액세스를 지원합니다.  
* **모든 권한:** Azure AD 관리자는 모든 권한이 있는 사용자 그룹을 만들고, 선택적으로 제한된 권한이 있는 사용자 그룹을 만들 수 있습니다.  이러한 그룹의 사용자만 **Lookout 콘솔**에 로그인할 수 있습니다.
* **제한된 권한:** 이 그룹의 사용자는 Lookout 콘솔의 여러 구성 및 등록 관련 모듈에 대한 액세스 권한이 없으며, Lookout 콘솔의 **보안 정책** 모듈에 대한 읽기 전용 액세스 권한을 갖습니다.  

사용 권한에 대한 자세한 내용은 Lookout 웹 사이트에서 [이 문서](https://personal.support.lookout.com/hc/en-us/articles/114094105653)를 참조하세요.

**그룹 개체 ID**는 **Azure AD 관리 콘솔**의 그룹 **속성** 페이지에 있습니다.

![GroupID 필드가 강조 표시된 속성 페이지 스크린샷](media/aad_group_object_id.png)

이 정보를 수집한 후 Lookout 지원 센터로 문의하세요(메일: enterprisesupport@lookout.com).

Lookout 지원 센터는 주 담당자와 협력하여 구독을 등록하고 수집한 정보를 사용하여 Lookout Enterprise 계정을 만듭니다.


## <a name="configure-your-subscription-with-lookout-device-threat-protection"></a>Lookout 장치 위협 방지를 사용하여 구독 구성
### <a name="step-1-set-up-your-device-threat-protection"></a>1단계: 장치 위협 방지 설정
Lookout 지원 센터는 Lookout Enterprise 계정을 만든 후 Lookout 콘솔에 로그인할 수 있습니다.   Lookout에서 로그인 링크(url: https://aad.lookout.com/les?action=consent)가 포함된 메일이 회사 주 담당자에게 전송됩니다.

Lookout에서 Azure AD 테넌트를 등록하려면 이 정보가 필요하므로 Lookout 콘솔에 처음 로그인할 때 Azure AD 역할이 전역 관리자인 사용자 계정을 사용해야 합니다.   후속 로그인 시에는 사용자에게 이러한 수준의 Azure AD 권한이 필요하지 않습니다.  첫 번째 로그인 시 승인 페이지가 표시됩니다. **동의**를 선택하여 등록을 완료합니다.

![Lookout 콘솔의 첫 번째 로그인 페이지 스크린샷](media/lookout-initial-login.png)

동의하고 승인하면 Lookout 콘솔로 리디렉션됩니다. 초기 등록 후 후속 로그인은 URL: https://aad.lookout.com을 사용하여 수행할 수 있습니다.

로그인 문제가 발생하는 경우 [문제 해결 문서]()를 참조하세요.

다음 단계에서는 [Lookout 콘솔](https://aad.lookout.com) 내에서 설정된 Lookout을 완료하기 위해 수행해야 하는 작업을 간략하게 설명합니다.

### <a name="step-2-configure-the-intune-connector"></a>2단계: Intune 커넥터 구성

1.  Lookout 콘솔의 **시스템** 모듈에서 **커넥터** 탭을 선택한 다음 **Intune**을 선택합니다.

  ![커넥터 탭이 열려 있고 Intune 옵션이 강조 표시된 Lookout 콘솔 스크린샷](media/lookout-setup-intune-connector.png)

2.  연결 설정 옵션에서 하트비트 빈도(분)를 구성합니다.  이제 Intune 커넥터가 준비되었습니다.  

  ![구성된 하트비트 빈도를 보여 주는 연결 설정 탭 스크린샷](media/lookout-connection-settings.png)

### <a name="step-3-configure-enrollment-groups"></a>3단계: 등록 그룹 구성
**등록 관리** 옵션에서 Lookout을 사용하여 장치를 등록해야 하는 사용자 집합을 정의합니다. 작은 사용자 그룹으로 테스트를 시작해서 통합 작동 방식을 익히는 것이 좋습니다.  테스트 결과에 만족하면 등록을 추가 사용자 그룹으로 확장할 수 있습니다.

그룹 등록을 시작하려면 먼저 Lookout 장치 위협 방지에 등록하는 첫 번째 사용자 집합이 될 Azure AD 보안 그룹을 정의합니다. Azure AD에서 그룹을 만든 후 Lookout 콘솔의 **등록 관리** 옵션으로 이동한 다음 등록할 Azure AD 보안 그룹의 **표시 이름**을 추가합니다.

사용자가 등록 그룹에 포함되면 Azure AD에서 식별되고 지원되는 모든 장치가 등록되고 Lookout 장치 위협 방지에서 활성화할 수 있습니다.  지원되는 장치에서 Lookout for Work 앱을 처음 열면 Lookout에서 장치가 활성화됩니다.

![Intune 커넥터 등록 페이지 스크린샷](media/lookout-enrollment.png)

새 장치를 확인할 시간 증분에 기본값(5분)을 사용하는 것이 좋습니다.

>[!IMPORTANT]
> 표시 이름은 대/소문자를 구분합니다.  Azure Portal에서 보안 그룹의 **속성** 페이지에 표시된 **표시 이름**을 사용합니다. 아래 그림에서 보안 그룹의 **속성** 페이지, 표시 이름은 카멜 대/소문자입니다.  그러나 제목은 모두 소문자로 표시되며, Lookout 콘솔에 입력하는 데 사용하면 안 됩니다.
>![Azure Portal, Azure Active Directory 서비스, 속성 페이지 스크린샷](media/aad-group-display-name.png)

현재 릴리스에는 다음과 같은 제한이 있습니다.  
* 그룹 표시 이름에 대한 유효성 검사는 없습니다.  Azure AD 보안 그룹에 대해 Azure Portal에 표시되는 **표시 이름** 필드의 값을 사용해야 합니다.
* 그룹 내에 그룹을 만드는 기능은 현재 지원되지 않습니다.  지정한 Azure AD 보안 그룹에는 사용자만 포함할 수 있고 중첩된 그룹은 포함할 수 없습니다.


### <a name="step-4-configure-state-sync"></a>4단계: 상태 동기화 구성
**상태 동기화** 옵션에서 Intune에 보내야 하는 데이터 형식을 지정합니다.  현재 Lookout Intune 통합이 제대로 작동하려면 장치 상태와 위협 상태를 둘 다 사용하도록 설정해야 합니다.  기본적으로 사용됩니다.
### <a name="step-5-configure-error-report-email-recipient-information"></a>5단계: 오류 보고서 메일 받는 사람 정보 구성
**오류 관리** 옵션에서 오류 보고서를 받을 메일 주소를 입력합니다.

![Intune 커넥터 오류 관리 페이지 스크린샷](media/lookout-connector-error-notifications.png)

### <a name="step-6-configure-enrollment-settings"></a>6단계. 등록 설정 구성
**시스템** 모듈의 **커넥터** 페이지에서 장치가 연결 끊김으로 간주되기 전의 일수를 지정합니다.  연결이 끊긴 장치는 비규격으로 간주되며 SCCM 조건부 액세스 정책에 따라 회사 응용 프로그램에 액세스할 수 없습니다. 1일에서 90일 사이의 값을 지정할 수 있습니다.

![](media/lookout-console-enrollment-settings.png)

### <a name="step-7-configure-email-notifications"></a>7단계: 메일 알림 구성
위협에 대한 메일 경고를 받으려면 알림을 받을 사용자 계정으로 [Lookout 콘솔](https://aad.lookout.com)에 로그인합니다. **시스템** 모듈의 **기본 설정** 탭에서 원하는 알림을 선택하고 **ON**으로 설정합니다. 변경 내용을 저장합니다.

![사용자 계정이 표시된 기본 설정 페이지 스크린샷](media/lookout-email-notifications.png) 메일 알림을 더 이상 받지 않으려면 알림을 **OFF**로 설정하고 변경 내용을 저장합니다.
### <a name="step-8-configure-threat-classification"></a>8단계: 위협 분류 구성
Lookout 장치 위협 방지는 다양한 유형의 모바일 위협을 분류합니다. [Lookout 위협 분류](http://personal.support.lookout.com/hc/en-us/articles/114094130693)에는 기본 위험 수준이 연결되어 있습니다. 이러한 수준은 언제든지 회사 요구 사항에 맞게 변경할 수 있습니다.

![위협 및 분류를 보여 주는 정책 페이지 스크린샷](media/lookout-threat-classification.png)

>[!IMPORTANT]
> 여기서 지정한 위험 수준은 Intune 통합에서 런타임 시 위험 수준에 따라 장치 준수를 계산하기 때문에 장치 위협 방지의 중요한 측면입니다. 즉, Intune 관리자는 최소 수준이 높음, 중간 또는 낮음인 활성 위협이 장치에 있는 경우 장치를 비규격으로 식별하는 규칙을 정책에 설정합니다. Lookout 장치 위협 방지의 위협 분류 정책은 직접적으로 Intune에서 장치 준수 계산을 실행합니다.

## <a name="watching-enrollment"></a>등록 감시
설치가 완료되면 Lookout 장치 위협 방지에서 지정한 등록 그룹에 해당하는 장치를 Azure AD에 폴링하기 시작합니다.  장치 모듈에서 등록된 장치에 대한 정보를 찾을 수 있습니다.  장치의 초기 상태는 보류 중으로 표시됩니다.  장치에서 Lookout for Work 앱을 설치하고 열고 활성화하면 장치 상태가 변경됩니다.  Lookout for Work 앱을 장치에 푸시하는 방법에 대한 자세한 내용은 [Lookout for Work 구성 및 배포](configure-and-deploy-lookout-for-work-apps.md) 항목을 참조하세요.
## <a name="next-steps"></a>다음 단계
[Intune에서 Lookout MTP 연결 사용](enable-lookout-connection-in-intune.md)
