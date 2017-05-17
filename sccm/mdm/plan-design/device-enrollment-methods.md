---
title: "하이브리드 MDM에 대한 장치 등록 방법 | Microsoft Docs"
description: "하이브리드 MDM에 대한 장치 등록 방법"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b81d06dc-3844-4117-9937-16732a227994
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: c38b3bae681821a886bfdab66d71cd6067adc425
ms.contentlocale: ko-kr
ms.lasthandoff: 03/06/2017


---
# <a name="overview-of-device-enrollment-methods"></a>장치 등록 방법 개요

*적용 대상: System Center Configuration Manager(현재 분기)*

Intune으로 Configuration Manager를 확장하면 관리자가 회사 소유 장치를 등록 및 관리하거나 사용자에게 개인 장치를 등록할 수 있는 권한을 부여할 수 있습니다. Intune에서 Configuration Manager를 사용하여 회사 소유 장치를 관리할 수도 있습니다.

다음 표에서는 등록 방법 및 지원되는 기능을 보여 줍니다. 해당 기능은 다음과 같습니다.
- **초기화** - 장치를 초기화하고 모든 데이터를 제거합니다. [장치 사용 중지](../deploy-use/wipe-lock-reset-devices.md)
- **선호도** - 장치를 사용자에 연결합니다. MAM(모바일 응용 프로그램 관리) 및 회사 데이터에 대한 조건부 액세스에 필요합니다. [사용자 선호도](../deploy-use/user-affinity-for-hybrid-managed-devices.md)
- **잠금** 사용자가 관리에서 장치를 제거할 수 없도록 차단합니다. iOS 장치에서 잠금을 사용하려면 감독 모드여야 합니다. [원격 잠금](../deploy-use/wipe-lock-reset-devices.md#remote-lock)

**iOS 등록 방법**

| **방법** |    **초기화** |    **선호도**    |    **잠금** | **세부 정보** |
|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 아니요|    예 |    아니요 | [자세히](../deploy-use/enable-platform-enrollment.md)|
|**[DEM](#dem)**|    아니요 |아니요 |아니요    | [자세히](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|
|**[DEP](#dep)**|    예 |    선택 사항 |    선택 사항|[자세히](../deploy-use/ios-device-enrollment-program-for-hybrid.md)|
|**[USB-SA](#usb-sa)**|    예 |    선택 사항 |    아니요| [자세히](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)|

**Windows 및 Android 등록 방법**

| **방법** |    **초기화** |    **선호도**    |    **잠금** | **세부 정보**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[BYOD](#byod)** | 아니요|    예 |    아니요 | [자세히](../deploy-use/enroll-hybrid-windows.md)|
|**[DEM](#dem)**|    아니요 |아니요 |아니요    |[자세히](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|

올바른 방법을 찾는 데 도움이 되는 일련의 질문을 보려면 [장치 등록 방법 선택](/intune/get-started/choose-how-to-enroll-devices1)을 참조하세요.

## <a name="byod"></a>BYOD
"BYOD(Bring Your Own Device)" 사용자는 회사 포털 앱을 설치하고 자신의 장치를 등록합니다. 이렇게 하면 사용자가 회사 네트워크에 연결하고 도메인 또는 Azure Active Directory에 가입할 수 있습니다. 대부분의 플랫폼에 대한 여러 COD 시나리오에서 BYOD 등록 사용은 필수 조건입니다. [하이브리드 MDM 설치](../deploy-use/setup-hybrid-mdm.md)를 참조하세요. ([표로 돌아가기](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>회사 소유 장치
Configuration Manager 콘솔을 사용하여 COD(회사 소유 장치)를 관리할 수 있습니다. iOS 장치는 Apple에서 제공하는 도구를 통해 직접 등록할 수 있습니다. 관리자(admin) 또는 관리자(manager)는 장치 등록 관리자를 사용하여 모든 장치 유형을 등록할 수 있습니다. COD 시나리오를 사용할 수 있도록 IMEI 번호가 있는 장치도 식별하고 회사 소유로 태그를 지정할 수 있습니다.

[회사 소유 장치 등록](../deploy-use/enroll-company-owned-devices.md)

### <a name="dem"></a>DEM
장치 등록 관리자는 여러 회사 소유 장치를 등록 및 관리하는 데 사용되는 특수 사용자 계정입니다. 관리자는 회사 포털을 설치하고 사용자가 없는 많은 장치를 등록할 수 있습니다. [DEM](../deploy-use/enroll-devices-with-device-enrollment-manager.md)에 대해 자세히 알아보세요. ([표로 돌아가기](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Apple DEP(장치 등록 프로그램) 관리를 사용하면 정책을 만들고 DEP로 구입하여 관리하는 iOS 장치에 "무선으로" 배포할 수 있습니다. 장치는 사용자가 처음으로 장치를 켜고 iOS 설정 도우미를 실행할 때 등록됩니다. 이 방법은 **iOS 감독** 모드를 지원하고, 다시 이 모드에서 다음 기능이 사용됩니다.
  -    잠긴 등록
  -    조건부 액세스
  -    탈옥 검색
  -    모바일 응용 프로그램 관리

[DEP](../deploy-use/ios-device-enrollment-program-for-hybrid.md)에 대해 자세히 알아보세요. ([표로 돌아가기](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
USB로 연결된 설정 도우미 등록입니다. 관리자가 정책을 만들어 Apple Configurator로 내보냅니다. USB로 연결된 회사 소유 장치는 정책을 사용하여 준비됩니다. 관리자가 각 장치를 직접 등록해야 합니다. 사용자가 자신의 장치를 받고 설정 도우미를 실행하여 장치를 등록합니다. 이 방법은 **iOS 감독** 모드를 지원하고, 다시 이 모드에서 다음 기능이 사용됩니다.
  -    조건부 액세스
  -    탈옥 검색
  -    모바일 응용 프로그램 관리

자세한 내용은 [Apple Configurator를 사용한 설정 도우미 등록](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)을 참조하세요. ([표로 돌아가기](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-configuration-manager"></a>Exchange ActiveSync 및 Configuration Manager를 사용한 모바일 장치 관리
등록되어 있지 않지만 EAS(Exchange ActiveSync)에 연결하는 모바일 장치는 Intune에서 EAS MDM 정책을 사용하여 관리할 수 있습니다. Intune은 Exchange 커넥터를 사용하여 온-프레미스 및 클라우드에 호스트된 EAS와 통신합니다.

[Exchange ActiveSync와 Intune을 사용한 모바일 장치 관리](../deploy-use/manage-mobile-devices-with-exchange-activesync.md)

