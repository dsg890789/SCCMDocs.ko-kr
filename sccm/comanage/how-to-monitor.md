---
title: 공동 관리 모니터링
titleSuffix: Configuration Manager
description: 공동 관리 대시보드를 사용하여 공동 관리형 디바이스에 관한 정보를 검토합니다.
ms.date: 07/26/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e83a7b0d-b381-4b4a-8eca-850385abbebb
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: ef379593a04c1f1e584c3d7066dbf1bece7a08c8
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825339"
---
# <a name="how-to-monitor-co-management-in-configuration-manager"></a>Configuration Manager에서 공동 관리를 모니터링하는 방법

*적용 대상: Configuration Manager(현재 분기)*

공동 관리를 사용하도록 설정하면 다음 방법을 사용하여 공동 관리 디바이스를 모니터링합니다.

- [공동 관리 대시보드](#co-management-dashboard)  

- [배포 정책](#deployment-policies)

- [WMI 디바이스 데이터](#wmi-device-data)

## <a name="co-management-dashboard"></a>공동 관리 대시보드

버전 1802부터는 공동 관리에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 대시보드를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 디바이스를 식별하는 데 도움이 될 수 있습니다.<!--1356648-->

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **공동 관리** 노드를 선택합니다.

1810 버전부터 공동 관리 대시보드가 좀 더 자세한 정보로 개선되었습니다. <!--1358980-->

![공동 관리 대시보드의 스크린샷](media/co-management-dashboard.png)

### <a name="co-managed-devices"></a>공동 관리형 디바이스

*버전 1802 및 1806에 적용*

환경 전체에서 공동 관리형 디바이스의 백분율을 표시합니다.

![공동 관리하는 디바이스 타일](media/co-management-dashboard/Percent-Co-managed-graph.PNG)

### <a name="client-os-distribution"></a>클라이언트 OS 배포

*모든 버전에 적용* 

OS당 클라이언트 디바이스의 수를 버전별로 표시합니다. 다음과 같은 그룹화를 사용합니다.  

- Windows 7 & 8.x
- 1709 이하의 Windows 10  
- Windows 10 1709 이상  

    > [!Tip]  
    > Windows 10, 1709 이상 버전은 공동 관리에 필수 구성 요소입니다.  

그래프 섹션을 마우스로 가리키면 OS 그룹에서 디바이스의 백분율이 표시됩니다.

![클라이언트 OS 배포 타일](media/co-management-dashboard/Co-management-OS-distribution-graph.PNG)

### <a name="co-management-status-donut"></a>공동 관리 상태(도넛형)

*버전 1802 및 1806에 적용*

다음 범주에 디바이스의 성공 또는 실패에 대한 분석 결과를 표시합니다.

- 성공, 하이브리드 Azure AD 조인됨
- 성공, Azure AD 조인됨  
- 실패: 자동 등록 실패  

그래프 섹션을 마우스로 가리키면 해당 범주에서 디바이스의 백분율이 표시됩니다.

![공동 관리 상태(도넛형) 타일](media/co-management-dashboard/Co-management-status-graph.PNG)

해당 범주에 대한 디바이스 목록을 보려면 그래프 섹션을 선택합니다.

![등록 실패 디바이스 목록](media/co-management-dashboard/Enrollment-Failure_Device-List.PNG)

### <a name="co-management-status-funnel"></a>공동 관리 상태(깔대기형)

*버전 1810 이상에 적용*

등록 프로세스의 다음과 같은 상태를 사용하여 디바이스의 수를 표시하는 깔때기형 차트:
  
- 적격 디바이스
- 예약됨  
- 등록이 시작됨  
- 등록됨  

![공동 관리 상태(깔대기형) 타일](media/co-management-dashboard/1358980-status-funnel.png)

### <a name="co-management-enrollment-status"></a>공동 관리 등록 상태

*버전 1810 이상에 적용*

다음 범주에 디바이스 상태의 분석 결과를 표시합니다.

- 성공, 하이브리드 Azure AD 조인됨  
- 성공, Azure AD 조인됨  
- 등록 중, 하이브리드 Azure AD 조인됨  
- 실패, 하이브리드 Azure AD 조인됨  
- 실패, Azure AD 조인됨  
- 사용자 로그인 보류 중  

    > [!Note]  
    > 1906년 버전부터 이 보류 상태의 디바이스 수를 줄이기 위해 새로운 공동 관리 디바이스가 Azure AD ‘device’ 토큰을 기반으로 Microsoft Intune 서비스에 자동으로 등록됩니다.  사용자가 디바이스에 로그인하여 자동 등록을 시작할 때까지 기다릴 필요가 없습니다. 이 동작을 지원하려면 디바이스에서 Windows 10 버전 1803 이상을 실행해야 합니다.
    >
    > 디바이스 토큰이 실패하면 사용자 토큰을 사용하여 이전 동작으로 대체합니다. **ComanagementHandler.log**에서 `Enrolling device with RegisterDeviceWithManagementUsingAADDeviceCredentials` 항목을 살펴보세요.

타일에서 상태를 선택하여 해당 상태의 디바이스 목록으로 드릴스루합니다.  

![공동 관리 등록 상태 타일](media/co-management-dashboard/1358980-enrollment-status.png)


### <a name="workload-transition"></a>워크로드 전환

*모든 버전에 적용*

사용 가능한 워크로드에 대해 Microsoft Intune으로 전환한 디바이스 수를 포함한 가로 막대형 차트를 표시합니다.

워크로드의 목록은 Configuration Manager의 버전에 따라 달라집니다. 자세한 내용은 [Intune으로 전환될 수 있는 워크로드](/sccm/comanage/workloads)를 참조하세요.

차트 섹션을 마우스로 가리키면 워크로드에 대해 전환된 디바이스 수가 표시됩니다. 

![워크로드 전환 막대 그래프](media/co-management-dashboard/Workload-Transition.PNG)


### <a name="enrollment-errors"></a>등록 오류

*버전 1810 이상에 적용*

이 표는 디바이스의 등록 오류 목록입니다. 이러한 오류는 Windows의 MDM 구성 요소, 핵심 Windows OS 또는 Configuration Manager 클라이언트에서 발생할 수 있습니다.

가능한 오류는 수백 개에 이릅니다. 다음 표에서는 가장 일반적인 오류를 보여 줍니다.
<!-- SCCMDocs issue 1064, BUG 3158555 -->

| 오류 | 설명 |
|---------|---------|
| 2147549183(0x8000FFFF) | Azure AD에서 MDM 등록이 아직 구성되지 않았거나 등록 URL이 필요하지 않습니다.<br><br>[Windows 10 자동 등록을 사용하도록 설정](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) |
| 2149056536(0x80180018)<br>MENROLL_E_USERLICENSE | 사용자 라이선스가 잘못된 상태여서 등록 차단<br><br>[사용자에게 라이선스 할당](https://docs.microsoft.com/intune/licenses-assign) |
| 2149056555(0x8018002B)<br>MENROLL_E_MDM_NOT_CONFIGURED | Intune으로 자동으로 등록하려고 하지만 Azure AD 구성이 완전히 적용되지 않습니다. 이 문제는 일시적이며 잠시 후 디바이스에서 다시 시도합니다. |
| 2149056554(0x8018002A)<br>&nbsp; | 사용자가 작업을 취소했습니다.<br><br>MDM 등록에 다단계 인증이 필요한데 사용자가 지원되는 두 번째 단계로 로그인하지 않은 경우 Windows에서 사용자에게 등록하라는 알림을 표시합니다. 사용자가 알림에 응답하지 않으면 이 오류가 발생합니다. 이 문제는 일시적이며 Configuration Manager가 다시 시도하고 사용자에게 메시지를 표시합니다. 사용자는 Windows에 로그인할 때 다단계 인증을 사용해야 합니다. 또한 이 동작이 필요하고 메시지가 표시되면 작업을 수행하도록 사용자를 교육합니다. | 
| 2149056533(0x80180015)<br>MENROLL_E_NOTSUPPORTED | 모바일 디바이스 관리는 일반적으로 지원되지 않음 | 
| 2149056514(0x80180002)<br>MENROLL_E_DEVICE_AUTHENTICATION_ERROR | 서버가 사용자를 인증하지 못했습니다.<br><br> 사용자의 Azure AD 토큰이 없습니다. 사용자가 Azure AD에 인증할 수 있는지 확인합니다. |
| 2147942450(0x80070032)<br>&nbsp; | MDM 자동 등록은 Windows RS3 이상에서만 지원됩니다.<br><br>디바이스가 공동 관리의 [최소 요구 사항](/sccm/comanage/overview#windows-10)을 충족하는지 확인합니다. |
| 3400073293 | ADAL 사용자 영역 계정 응답을 알 수 없음<br><br>Azure AD 구성을 확인하고 사용자가 인증할 수 있는지 확인합니다. | 
| 3399548929 | 사용자 로그인 필요<br><br>일시적인 문제입니다. 등록 작업이 수행되기 전에 사용자가 신속하게 로그아웃하는 경우 발생합니다. | 
| 3400073236 | ADAL 보안 토큰 요청이 실패했습니다.<br><br>Azure AD 구성을 확인하고 사용자가 인증할 수 있는지 확인합니다. |
| 2149122477 | 일반 HTTP 문제 |
| 3400073247 | ADAL 통합 Windows 인증은 페더레이션된 흐름에서만 지원됩니다.<br><br>[Plan your hybrid Azure Active Directory join implementation](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan)(하이브리드 Azure Active Directory 연결 구현 계획) | 
| 3399942148 | 서버 또는 프록시를 찾을 수 없습니다.<br><br>이 문제는 클라이언트가 클라우드와 통신할 수 없는 경우 발생하는 일시적인 문제입니다. 계속될 경우 클라이언트가 Azure에 계속 연결되어 있는지 확인합니다. | 
| 2149056532 | 특정 플랫폼 또는 버전이 지원되지 않습니다.<br><br>디바이스가 공동 관리의 [최소 요구 사항](/sccm/comanage/overview#windows-10)을 충족하는지 확인합니다. |
| 2147943568 | 요소를 찾을 수 없음<br><br>일시적인 문제입니다. 계속되면 Microsoft 지원에 문의하세요. |
| 2192179208 | 메모리 리소스가 부족하여 이 명령을 처리할 수 없습니다.<br><br>이 문제는 일시적이며, 클라이언트에서 다시 시도하면 저절로 해결됩니다. |
| 3399614467 | 이 어설션에 대한 ADAL 권한 부여에 실패함<br><br>Azure AD 구성을 확인하고 사용자가 인증할 수 있는지 확인합니다. |
| 2149056517 | DB 액세스 오류와 같은 관리 서버의 일반 오류<br><br>일시적인 문제입니다. 계속되면 Microsoft 지원에 문의하세요. |
| 2149134055 | Winhttp 이름이 확인 안 됨<br><br>클라이언트가 서비스 이름을 확인할 수 없습니다. DNS 구성을 확인합니다. | 
| 2149134050 | 인터넷 제한 시간<br><br>이 문제는 클라이언트가 클라우드와 통신할 수 없는 경우 발생하는 일시적인 문제입니다. 계속될 경우 클라이언트가 Azure에 계속 연결되어 있는지 확인합니다. |

자세한 내용은 [MDM Registration Error Values](https://docs.microsoft.com/windows/desktop/mdmreg/mdm-registration-constants)(MDM 등록 오류 값)를 참조하세요.

## <a name="deployment-policies"></a>배포 정책

두 정책을 **모니터링** 작업 영역의 **배포** 노드에서 만듭니다. 한 정책은 파일럿 그룹용이며 다른 정책은 프로덕션용입니다. 이러한 정책은 Configuration Manager에서 정책을 적용한 디바이스의 수만 보고합니다. 디바이스를 공동 관리할 수 있기 전의 요구 사항인 Intune에 등록된 디바이스의 수는 고려하지 않습니다.  

프로덕션 정책(CoMgmtSettingsProd)은 **모든 시스템** 컬렉션을 대상으로 합니다. 또한 OS 유형 및 버전을 확인하는 적용 가능성 조건을 포함합니다. 클라이언트가 서버 OS 또는 Windows 10이 아니면 정책이 적용되지 않으며, 아무 작업도 수행되지 않습니다.

## <a name="wmi-device-data"></a>WMI 디바이스 데이터

**SMS_Client_ComanagementState** WMI 클래스를 쿼리합니다. Configuration Manager에서 사용자 지정 컬렉션을 만들어 공동 관리 배포의 상태를 확인할 수 있습니다. 사용자 지정 컬렉션을 만드는 방법에 대한 자세한 내용은 [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)을 참조하세요.

다음 필드는 WMI 클래스에서 사용할 수 있습니다.  

- **MachineId**: Configuration Manager 클라이언트의 고유한 디바이스 ID  

- **MDMEnrolled**: 디바이스가 MDM에 등록되었는지 여부 지정  

- **기관**: 디바이스가 등록된 기관  

- **ComgmtPolicyPresent**: 클라이언트에 Configuration Manager 공동 관리 정책이 있는지 여부를 지정합니다. **MDMEnrolled** 값이 **0**이면 공동 관리 정책이 클라이언트에 있는지 여부에 관계 없이 디바이스를 공동 관리하지 않습니다.  

**MDMEnrolled** 필드 및 **ComgmtPolicyPresent** 필드의 값이 모두 **1**이면 디바이스가 공동 관리됩니다.  
