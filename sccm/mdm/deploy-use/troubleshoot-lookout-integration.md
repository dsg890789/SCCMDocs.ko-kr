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
ms.openlocfilehash: ee978543248e70182e12a3d6234cfd12be80dc98
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32348585"
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
* https://enterprise.support.lookout.com/hc/requests로 이동하여 지원 요청을 합니다.

### <a name="unable-to-sign-in"></a>로그인할 수 없음
Azure AD 전역 관리자가 초기 Lookout 설치에 동의하지 않은 경우 다음 오류가 나타날 수 있습니다.

![로그인 오류를 보여 주는 Lookout 로그인 화면 스크린샷](media/lookout-consent-not-accepted-error.png)

이 문제를 해결하려면 전역 관리자가 https://aad.lookout.com/les?action=consent에 로그인한 다음, 메시지에 동의하여 설치를 시작해야 합니다. 자세한 정보는 [Lookout MTP를 사용하여 구독 설정](set-up-your-subscription-with-lookout.md) 항목에서 확인할 수 있습니다.

## <a name="troubleshoot-device-status-issues"></a>장치 상태 문제 해결

### <a name="device-not-showing-up-in-the-lookout-mtp-console-device-list"></a>Lookout MTP 콘솔 장치 목록에 장치가 표시되지 않음

이 오류는 다음 시나리오 중 하나에서 발생할 수 있습니다.
* 이 장치를 소유한 사용자가 **Lookout MTP 콘솔**에 지정된 **등록 그룹**에 없는 경우.  **시스템** 모듈에서 **Intune 커넥터** 탭으로 이동한 다음 **등록 관리** 설정을 확인합니다.  등록에 대해 구성된 Azure AD 그룹이 하나 이상 표시되어야 합니다.  누락된 장치를 소유한 사용자가 지정한 Azure AD 그룹 중 하나의 일부인지 확인합니다.  새 사용자가 등록 그룹에 추가된 후 장치가 Lookout MTP 콘솔의 **장치** 모듈에 표시될 때까지 구성된 폴링 간격(5분이 기본값임)까지 걸릴 수 있습니다.

* 장치가 Lookout MTP에서 지원되지 않는 경우.  지원되지 않는 장치가 Lookout MTP 콘솔에서 커넥터 설정의 **관리되는 장치** 섹션에 표시됩니다.

### <a name="device-continues-to-be-reported-as-pending"></a>장치가 계속 **보류 중**으로 보고됨

**보류 중**으로 표시되는 장치는 최종 사용자가 Lookout for Work 앱을 열고 **활성화** 단추를 탭하지 않았음을 의미합니다. Lookout for Work 앱을 사용한 장치 활성화에 대한 자세한 내용은 다음 항목을 참조하세요.

[Android 장치에 Lookout for Work를 설치하라는 메시지가 표시됨](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

### <a name="in-the-lookout-mtp-console-a-device-is-showing-as-active-but-does-not-have-a-device-id"></a>Lookout MTP 콘솔에서 장치가 활성으로 표시되지만 장치 ID가 없습니다.
이는 이 장치를 소유한 사용자가 Lookout MTP 콘솔에 지정된 등록 그룹에 없음을 의미합니다.   장치를 소유한 사용자가 등록 그룹에서 제거되었거나 사용자가 속한 등록 그룹이 제거된 경우 장치가 이 상태로 전환될 수 있습니다.

Lookout MTP 콘솔의 **시스템** 모듈에서 **Intune 커넥터** 탭으로 이동한 다음 **등록** 설정을 검토합니다.  등록에 대해 구성된 Azure AD 그룹이 하나 이상 표시되어야 합니다.  장치를 소유한 사용자가 지정한 Azure AD 그룹 중 하나의 일부인지 확인합니다.

장치가 이 상태에 있는 동안 Lookout은 검색된 위협을 사용자에게 계속 알리지만 위협 정보를 Intune에 보내지 않습니다.

### <a name="device-shows-disconnected-state"></a>장치가 연결 끊김 상태로 표시됨

연결 끊김은 Lookout MTP가 미리 구성된 시간 간격(기본값은 30일이고 최소값은 7일임) 동안 듣지 못했음을 의미합니다. 즉, 회사 포털 앱 또는 Lookout for Work 앱이 장치에 설치되어 있지 않거나 제거되었습니다. 앱을 다시 설치하면 이 문제가 해결됩니다. 사용자가 Lookout for Work를 열고 앱을 활성화하면 장치가 Lookout MTP 및 Intune과 다시 동기화됩니다.

### <a name="forcing-a-resync-on-the-device"></a>장치에서 강제로 다시 동기화
Lookout MTP 콘솔의 **장치** 모듈에서 관리자는 장치를 선택하고 삭제하도록 선택할 수 있습니다.   다음에 장치 소유자가 Lookout for Work 앱을 열고 **활성화**를 탭하면 장치 상태가 전체 다시 동기화를 수행합니다.

### <a name="the-owner-of-the-device-is-no-longer-using-this-device"></a>장치 소유자가 더 이상 이 장치를 사용하고 있지 않음
장치를 초기화하고 [이 항목](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#full-wipe)에 설명된 대로 등록하도록 새 사용자에게 요청해야 합니다.


Lookout MTP 콘솔의 **장치** 모듈로 이동한 다음 **삭제**를 선택할 수도 있습니다.

새 사용자가 Lookout MTP 콘솔에 지정된 등록 그룹 중 하나에 속하는 한, Azure AD에서 장치를 새 사용자에 연결하면 장치가 표시됩니다.

## <a name="compliance-remediation-workflows"></a>준수 수정 워크플로
[Android 장치에 Lookout for Work를 설치하라는 메시지가 표시됨]( http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

[Lookout for Work가 Android 장치에서 발견한 위협을 해결해야 함](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)
