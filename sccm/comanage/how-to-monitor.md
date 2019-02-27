---
title: 공동 관리 모니터링
titleSuffix: Configuration Manager
description: 공동 관리 대시보드를 사용하여 공동 관리형 디바이스에 관한 정보를 검토합니다.
ms.date: 01/14/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e83a7b0d-b381-4b4a-8eca-850385abbebb
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 7c731692bc2277cc5ce97e079387b392ca09ff3e
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755397"
---
# <a name="how-to-monitor-co-management-in-configuration-manager"></a>Configuration Manager에서 공동 관리를 모니터링 하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


공동 관리를 사용하도록 설정하면 다음 방법을 사용하여 공동 관리 디바이스를 모니터링합니다.

- [공동 관리 대시보드](#co-management-dashboard)  

- [배포 정책](#deployment-policies)

- [WMI 장치 데이터](#wmi-device-data)



## <a name="co-management-dashboard"></a>공동 관리 대시보드

버전 1802부터는 공동 관리에 대한 정보가 포함된 대시보드를 볼 수 있습니다. 대시보드를 사용하면 사용자 환경에서 공동으로 관리되는 시스템을 검토할 수 있습니다. 그래프는 주의가 필요한 디바이스를 식별하는 데 도움이 될 수 있습니다.<!--1356648-->

Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **공동 관리** 노드를 선택합니다.

1810 버전부터 공동 관리 대시보드가 좀 더 자세한 정보로 개선되었습니다. <!--1358980-->

![공동 관리 대시보드의 스크린 샷](media/co-management-dashboard.png)


### <a name="co-managed-devices"></a>공동 관리형 디바이스

*버전 1802 및 1806에 적용*

환경 전체에서 공동 관리형 디바이스의 백분율을 표시합니다.

![공동 관리 장치 타일](media/co-management-dashboard/Percent-Co-managed-graph.PNG)


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
- 오류: 자동 등록 실패  

그래프 섹션을 마우스로 가리키면 해당 범주에서 디바이스의 백분율이 표시됩니다. 

![공동 관리 상태 (도넛형) 타일](media/co-management-dashboard/Co-management-status-graph.PNG)

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

타일에서 상태를 선택하여 해당 상태의 디바이스 목록으로 드릴스루합니다.  

![공동 관리 등록 상태 타일](media/co-management-dashboard/1358980-enrollment-status.png)


### <a name="workload-transition"></a>워크로드 전환

*모든 버전에 적용*

사용 가능한 워크로드에 대해 Microsoft Intune으로 전환한 디바이스 수를 포함한 가로 막대형 차트를 표시합니다. 

워크 로드 목록을 Configuration Manager 버전에 따라 다릅니다. 자세한 내용은 [Intune으로 전환될 수 있는 워크로드](/sccm/comanage/workloads)를 참조하세요.

차트 섹션을 마우스로 가리키면 워크로드에 대해 전환된 디바이스 수가 표시됩니다. 

![워크 로드 전환 막대 그래프](media/co-management-dashboard/Workload-Transition.PNG)


### <a name="enrollment-errors"></a>등록 오류

*버전 1810 이상에 적용*

이 테이블은 장치에서 등록 오류의 목록입니다. 이러한 오류는 Windows, 핵심 Windows OS 또는 Configuration Manager 클라이언트에서 MDM 구성 요소에서 발생할 수 있습니다. 

수백 개의 오류가 발생할 수 있습니다. 다음 표에서 가장 일반적인 오류를 보여 줍니다.
<!-- SCCMDocs issue 1064, BUG 3158555 -->

| 오류 | Description |
|---------|---------|
| 2147549183 (0x8000FFFF) | MDM 등록을 Azure AD에서 아직 구성 되지 않았습니다 또는 등록 URL이 필요 하지 않습니다.<br><br>[Windows 10 자동 등록 사용](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) |
| 2149056536 (0x80180018)<br>MENROLL_E_USERLICENSE | 사용자의 라이선스는 잘못 된 상태 차단 등록<br><br>[사용자에 게 라이선스 할당](https://docs.microsoft.com/intune/licenses-assign) |
| 2149056555 (0x8018002B)<br>MENROLL_E_MDM_NOT_CONFIGURED | 자동으로 하려고 할 때 Intune로 등록 되지만 Azure AD 구성을 완전히 적용 되지 않습니다. 이 문제는 일시적으로 짧은 시간 후에 다시 시도 장치 여야 합니다. |
| 2149056554 (0x‭8018002A‬)<br>&nbsp; | 사용자가 작업 취소<br><br>MDM 등록에 다단계 인증이 필요 하 고 사용자는 지원 되는 두 번째 요소를 사용 하 여 로그인 하지 않은 경우 Windows 알림 메시지를 등록 하려면 사용자에 게 표시 합니다. 사용자 알림에 응답 하지 않으면이 오류가 발생 합니다. Configuration Manager는 다시 시도 하 고 묻는 메시지를이 문제는 일시적인 것 이어야 합니다. 사용자가 Windows에 로그인 할 때 multi-factor authentication을 사용 해야 합니다. 또한이 동작을 예상 하도록 교육 하 고 메시지가 표시 되 면 작업을 수행 합니다. | 
| 2149056533 (0x80180015)<br>MENROLL_E_NOTSUPPORTED | 일반적으로 지원 되지 않습니다 하는 모바일 장치 관리 | 
| 2149056514 (0x80180002)<br>MENROLL_E_DEVICE_AUTHENTICATION_ERROR | 서버가 사용자를 인증 하지 못했습니다<br><br> 사용자에 대 한 Azure AD 토큰이 없습니다. 사용자가 Azure AD에 인증할 수 있는지 확인 합니다. |
| 2147942450 (0x‭80070032‬)<br>&nbsp; | MDM 자동 등록은 Windows RS3 이상 에서만 지원 됩니다.<br><br>장치에서 충족 하는지 확인 합니다 [최소 요구 사항을](/sccm/comanage/overview#windows-10) 공동 관리에 대 한 합니다. |
| 3400073293 | 알 수 없는 ADAL 사용자 영역 계정 응답<br><br>Azure AD 구성을 확인 하 고 사용자가 성공적으로 인증할 수 있는지 확인 합니다. | 
| 3399548929 | 필요한 사용자 로그인<br><br>이 문제는 일시적인 이어야 합니다. 사용자 신속 하 게 로그 아웃 등록 작업이 발생 하기 전에 발생 합니다. | 
| 3400073236 | ADAL 보안 토큰 요청이 실패 했습니다.<br><br>Azure AD 구성을 확인 하 고 사용자가 성공적으로 인증할 수 있는지 확인 합니다. |
| 2149122477 | 제네릭 HTTP 문제 |
| 3400073247 | ADAL 통합 Windows 인증 페더레이션된 흐름 에서만 지원 됩니다.<br><br>[하이브리드 Azure Active Directory 조인 구현 계획](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan) | 
| 3399942148 | 서버 또는 프록시를 찾을 수 없습니다.<br><br>클라이언트는 클라우드를 사용 하 여 통신할 수 없는 경우이 문제는 일시적인 이어야 합니다. 계속 될 경우 클라이언트에서 Azure로 일관 된 연결이 있는지 확인 합니다. | 
| 2149056532 | 특정 플랫폼 또는 버전 지원 되지 않습니다.<br><br>장치에서 충족 하는지 확인 합니다 [최소 요구 사항을](/sccm/comanage/overview#windows-10) 공동 관리에 대 한 합니다. |
| 2147943568 | 찾을 수 없는 요소<br><br>이 문제는 일시적인 이어야 합니다. 지속 되 면 Microsoft 지원에 문의 합니다. |
| 2192179208 | 이 명령을 처리할 수 있는 메모리 리소스가 부족 합니다.<br><br>이 문제는 일시적인 해야이 자동으로 해결 됩니다 클라이언트에서 재시도할 때. |
| 3399614467 | 이 어설션에 대 한 ADAL 인증 부여 하지 못했습니다.<br><br>Azure AD 구성을 확인 하 고 사용자가 성공적으로 인증할 수 있는지 확인 합니다. |
| 2149056517 | DB 액세스 오류와 같은 관리 서버에서 일반 오류가 발생 했습니다.<br><br>이 문제는 일시적인 이어야 합니다. 지속 되 면 Microsoft 지원에 문의 합니다. |
| 2149134055 | Winhttp 이름이 확인 되지 않음<br><br>클라이언트는 서비스의 이름을 확인할 수 없습니다. DNS 구성을 확인 합니다. | 
| 2149134050 | 인터넷 제한 시간<br><br>클라이언트는 클라우드를 사용 하 여 통신할 수 없는 경우이 문제는 일시적인 이어야 합니다. 계속 될 경우 클라이언트에서 Azure로 일관 된 연결이 있는지 확인 합니다. | 


자세한 내용은 [MDM 등록 오류 값](https://docs.microsoft.com/windows/desktop/mdmreg/mdm-registration-constants)합니다.



## <a name="deployment-policies"></a>배포 정책

두 정책을 **모니터링** 작업 영역의 **배포** 노드에서 만듭니다. 한 정책은 파일럿 그룹용이며 다른 정책은 프로덕션용입니다. 이러한 정책은 Configuration Manager에서 정책을 적용한 디바이스의 수만 보고합니다. 디바이스를 공동 관리할 수 있기 전의 요구 사항인 Intune에 등록된 디바이스의 수는 고려하지 않습니다.  



## <a name="wmi-device-data"></a>WMI 장치 데이터

쿼리는 **SMS_Client_ComanagementState** WMI 클래스입니다. 만들면 사용자 지정 컬렉션 Configuration Manager에서 공동 관리 배포의 상태를 확인 하는 데 도움이 되는 됩니다. 사용자 지정 컬렉션을 만드는 방법에 대 한 자세한 내용은 참조 하세요. [컬렉션을 만드는 방법](/sccm/core/clients/manage/collections/create-collections)합니다. 

다음 필드는 WMI 클래스에 사용할 수 있습니다.  

- **MachineId**: Configuration Manager 클라이언트에 대 한 고유한 장치 ID  

- **MDMEnrolled**: 디바이스가 MDM에 등록되었는지 여부 지정  

- **기관**: 장치를 등록 하는 인증 기관  

- **ComgmtPolicyPresent**: 클라이언트에 Configuration Manager 공동 관리 정책이 있는지 여부를 지정합니다. **MDMEnrolled** 값이 **0**이면 공동 관리 정책이 클라이언트에 있는지 여부에 관계 없이 디바이스를 공동 관리하지 않습니다.  

**MDMEnrolled** 필드 및 **ComgmtPolicyPresent** 필드의 값이 모두 **1**이면 디바이스가 공동 관리됩니다.  
