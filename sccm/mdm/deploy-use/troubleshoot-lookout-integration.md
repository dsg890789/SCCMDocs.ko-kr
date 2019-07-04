---
title: Lookout 통합 문제 해결
titleSuffix: Configuration Manager
description: 이 항목에서는 Lookout 통합에서 일반적으로 발생하는 문제를 해결하는 방법을 설명합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: e36b98c7-d0f4-4dd6-bac3-6a6c4b4bf841
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 9066983e631e1444cccb7b8c686c5b31e6fcf096
ms.sourcegitcommit: f42b9e802331273291ed498ec88f710110fea85a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67551461"
---
# <a name="troubleshoot-lookout-integration-with-intune"></a>Intune과 Lookout 통합 문제 해결

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="troubleshoot-login-errors"></a>로그인 오류 문제 해결
### <a name="403-errors"></a>403 오류
[Lookout MTP 콘솔](https://aad.lookout.com)에 로그인할 때 403 오류가 표시될 수도 있습니다. **서비스에 액세스할 수 있는 권한이 없습니다**. 이 오류는 지정한 사용자 이름이 Lookout MTP에 액세스하도록 구성된 Azure AD(Azure Active Directory) 그룹의 구성원인 경우에 발생할 수 있습니다.

Lookout MTP는 구성된 Azure AD 그룹의 사용자만 액세스할 수 있도록 구성되어 있습니다. Lookout MTP에 액세스할 수 있도록 구성된 그룹이 확실하지 않은 경우 Lookout 지원 센터로 문의하세요.

다음과 같은 방법으로 Lookout 지원 센터에 문의할 수 있습니다.

* 메일: enterprisesupport@lookout.com
* [MTP 콘솔](http://aad.lookout.com)에 로그인한 다음 **지원** 모듈로 이동합니다.
* [https://enterprise.support.lookout.com/hc/requests](https://enterprise.support.lookout.com/hc/requests )로 이동하여 지원 요청을 합니다.

### <a name="unable-to-sign-in"></a>로그인할 수 없음
Azure AD 전역 관리자가 초기 Lookout 설치에 동의하지 않은 경우 다음 오류가 나타날 수 있습니다.

![로그인 오류를 보여 주는 Lookout 로그인 화면 스크린샷](media/lookout-consent-not-accepted-error.png)

이 문제를 해결하려면 전역 관리자가 https://aad.lookout.com/les?action=consent 에 로그인한 다음, 메시지에 동의하여 설치를 시작해야 합니다. 자세한 정보는 [Lookout MTP를 사용하여 구독 설정](set-up-your-subscription-with-lookout.md) 항목에서 확인할 수 있습니다.

## <a name="troubleshoot-device-status-issues"></a>디바이스 상태 문제 해결

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>디바이스가 Lookout MTP 콘솔의 디바이스 목록에 표시되지 않음

이 오류는 다음 시나리오 중 하나에서 발생할 수 있습니다.
* 이 디바이스를 소유하는 사용자가 **Lookout MTP 콘솔**에 지정된 **등록 그룹**에 없는 경우.  **시스템** 모듈에서 **Intune 커넥터** 탭으로 이동한 다음 **등록 관리** 설정을 확인합니다.  등록에 대해 구성된 Azure AD 그룹이 하나 이상 표시되어야 합니다.  누락된 디바이스를 소유하는 사용자가 지정된 Azure AD 그룹에 속하는지 확인합니다.  새 사용자를 등록 그룹에 추가하면, 구성된 최대 폴링 간격(5분이 기본값임)이 지나야 디바이스가 Lookout MTP 콘솔의 **디바이스** 모듈에서 보입니다.

* 디바이스가 Lookout MTP에서 지원되지 않는 경우.  지원되지 않는 디바이스는 Lookout MTP 콘솔의 커넥터 설정에서 **관리되는 디바이스** 섹션에 나타납니다.

### <a name="device-continues-to-be-reported-as-pending"></a>디바이스가 **보류 중** 상태로 계속 보고됨

디바이스가 **보류 중**으로 나타나는 것은 최종 사용자가 아직 Lookout for work 앱을 열어 **활성화** 단추를 탭하지 않았기 때문입니다. Lookout for Work 앱에서 디바이스를 활성화하는 방법에 대한 자세한 내용은 다음 항목을 참조하세요.

[Android 디바이스에 Lookout for Work를 설치하라는 메시지가 표시됨](https://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>Lookout MTP 콘솔에서 디바이스가 활성 상태로 표시되지만 디바이스 ID가 없습니다.
이 디바이스를 소유하는 사용자가 Lookout MTP 콘솔에 지정된 등록 그룹에 없기 때문입니다.   디바이스를 소유하는 사용자가 등록 그룹에서 제거되었거나 그 사용자가 속한 등록 그룹이 제거되었을 때도 디바이스는 이 상태가 될 수 있습니다.

Lookout MTP 콘솔의 **시스템** 모듈에서 **Intune 커넥터** 탭으로 이동한 다음 **등록** 설정을 검토합니다.  등록에 대해 구성된 Azure AD 그룹이 하나 이상 표시되어야 합니다.  디바이스를 소유하는 사용자가 지정된 Azure AD 그룹에 속하는지 확인합니다.

디바이스가 이 상태에 있다면 Lookout은 위협을 감지하면 계속해서 사용자에게 알려주기는 하지만 Intune에 위협 정보를 전송하지는 않습니다.

### <a name="device-shows-disconnected-state"></a>디바이스가 연결 끊김 상태로 표시됨

연결이 끊겼다는 것은 Lookout MTP가 미리 구성된 시간 간격(기본값은 최소 7일에서 최대 30일) 동안 디바이스에서 아무런 수신을 받지 못했다는 의미입니다. 또한 회사 포털 앱 또는 Lookout for Work 앱이 디바이스에 설치되지 않았거나 제거되었음을 의미합니다. 앱을 다시 설치하면 이 문제가 해결됩니다. 사용자가 Lookout for Work를 열어 앱을 활성화하면 디바이스가 Lookout MTP, Intune과 함께 다시 동기화됩니다.

### <a name="forcing-a-resync-on-the-device"></a>디바이스에서 강제로 다시 동기화
관리자는 Lookout MTP 콘솔의 **디바이스** 모듈에서 디바이스를 선택한 후 삭제하도록 선택할 수 있습니다.   다음번에 디바이스 소유자가 Lookout for Work 앱을 열어 **활성화**를 탭하면 디바이스 상태가 완전히 다시 동기화됩니다.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>디바이스 소유자가 이제 이 디바이스를 사용하지 않음
디바이스를 초기화하고 [이 항목](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe)에 설명된 대로 등록하도록 새 사용자에게 요청해야 합니다.


Lookout MTP 콘솔의 **디바이스** 모듈에서 **삭제**를 선택할 수도 있습니다.

새 사용자가 Lookout MTP 콘솔에 지정된 등록 그룹에 속해 있는 동안에는 Azure AD가 디바이스를 새 사용자에 연결하면 디바이스가 나타납니다.

## <a name="compliance-remediation-workflows"></a>준수 수정 워크플로
[Android 디바이스에 Lookout for Work를 설치하라는 메시지가 표시됨]( https://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Android 디바이스에서 Lookout for Work가 발견한 위협을 해결해야 함](https://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
