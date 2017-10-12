---
title: "System Center Configuration Manager를 사용하여 원격 초기화, 잠금 또는 암호 재설정으로 데이터 보호 | Microsoft Docs"
description: "System Center Configuration Manager를 사용하여 전체 초기화, 선택적 초기화, 원격 잠금 또는 암호 다시 설정으로 장치 데이터를 보호합니다."
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: ea92d7b4656a04f312f04c19cac6b17df931c9c5
ms.sourcegitcommit: db079cd7322e7d4926b2df0ccb37e752c570d902
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/28/2017
---
# <a name="protect-data-with-remote-wipe-lock-or-passcode-reset-by-using-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 원격 초기화, 잠금 또는 암호 재설정으로 데이터 보호

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager는 선택적 초기화, 전체 초기화, 원격 잠금 및 암호 재설정 기능을 제공합니다. 모바일 장치에 회사의 중요한 데이터를 저장하고, 많은 회사 리소스에 대한 액세스를 제공할 수 있습니다. 장치를 보호하기 위해 다음 명령을 실행할 수 있습니다.  

- 출하 시 설정으로 장치를 복원하는 전체 초기화  

- 회사 데이터만 제거하는 선택적 초기화  

- 분실한 장치를 보호하는 데 유용한 원격 잠금  

- 장치 암호 재설정.  

## <a name="full-wipe"></a>전체 초기화  
분실한 장치를 보호하거나 장치의 활성 사용을 중지할 경우 장치에 초기화 명령을 실행할 수 있습니다.  

장치에서 출하 시 기본값으로 장치를 복원하는 **전체 초기화** 를 실행합니다. 그러면 모든 회사 및 사용자 데이터와 설정이 제거됩니다. Windows Phone, iOS, Android 및 Windows 10 장치에서 전체 초기화를 수행할 수 있습니다.  

> [!NOTE]
> 버전 1511보다 이전 버전에서 RAM이 4GB 미만인 Windows 10 장치를 초기화하면 장치가 응답하지 않는 상태가 될 수 있습니다. [자세히 알아봅니다](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram).

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 원격 초기화를 시작하려면  

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택하고 **장치**를 선택합니다. **장치 컬렉션** 을 선택하고 컬렉션을 선택할 수도 있습니다.  

2. 사용 중지/초기화하려는 장치를 선택합니다.  

3. **장치 그룹**에서 **원격 장치 작업**을 선택한 다음 **사용 중지/초기화**를 선택합니다.  

## <a name="selective-wipe"></a>선택적 초기화  
장치에서 회사 데이터만 제거하는 **선택적 초기화** 를 실행합니다. 다음 표에서는 플랫폼별로 제거되는 데이터와 선택적 초기화 후 장치에 남아 있는 데이터에 대한 영향을 설명합니다.  

**iOS**  

|장치를 사용 중지할 경우 제거되는 콘텐츠|iOS|  
|--------------------------------------------|---------|  
|Configuration Manager 및 Intune을 사용하여 설치된 회사 앱 및 관련 데이터|앱이 제거됩니다. 회사 앱 데이터가 제거됩니다.|  
|VPN 및 Wi-Fi 프로필|제거됩니다.|  
|인증서|제거되고 해지됩니다.|  
|설정|**음성 로밍 허용**, **데이터 로밍 허용** 및 **로밍하는 동안 자동 동기화 허용**을 제외하고 제거됩니다.|  
|관리 에이전트|관리 프로필이 제거됩니다.|  
|전자 메일 프로필|Intune에 의해 설정된 메일 프로필의 경우 메일 계정 및 메일이 제거됩니다.|  

**Android 및 Android Samsung KNOX Standard**  

|장치를 사용 중지할 경우 제거되는 콘텐츠|Android|Samsung KNOX Standard|  
|--------------------------------------------|-------------|------------------|  
|Configuration Manager 및 Intune을 사용하여 설치된 회사 앱 및 관련 데이터|앱 및 데이터는 계속 설치되어 있습니다.|앱이 제거됩니다.|  
|VPN 및 Wi-Fi 프로필|제거됩니다.|제거됩니다.|  
|인증서|해지됩니다.|해지됩니다.|  
|설정|요구 사항이 제거됩니다.|요구 사항이 제거됩니다.|  
|관리 에이전트|장치 관리자 권한이 해지됩니다.|장치 관리자 권한이 해지됩니다.|  
|전자 메일 프로필|해당 없음.|Intune에 의해 설정된 메일 프로필의 경우 메일 계정 및 메일이 제거됩니다.|  

**Android for Work**

Android for Work 장치에서 선택적 초기화를 수행하면 해당 장치에 있는 회사 프로필의 모든 데이터, 앱 및 설정과 함께 회사 프로필이 제거됩니다. 이 경우 Configuration Manager 및 Intune을 사용한 관리에서 장치 사용이 중지됩니다. Android for Work에서는 전체 초기화가 지원되지 않습니다.

 **Windows 10, Windows 8.1, Windows RT 8.1 및 Windows RT**  

|장치를 사용 중지할 경우 제거되는 콘텐츠|Windows 10, Windows 8.1 및 Windows RT 8.1|  
|---------------------------------|-------------|
|Configuration Manager 및 Intune을 사용하여 설치된 회사 앱 및 관련 데이터|앱이 제거되고 테스트용 로드 키가 제거됩니다. Windows 선택 초기화를 사용하는 앱에서 암호화 키가 해지되고 더 이상 데이터에 액세스할 수 없게 됩니다.|  
|VPN 및 Wi-Fi 프로필|제거됩니다.|  
|인증서|제거되고 해지됩니다.|  
|설정|요구 사항이 제거됩니다.|
|관리 에이전트|해당 없음. 관리 에이전트가 기본 제공됨|  
|전자 메일 프로필|Windows 메일 및 첨부 파일용 메일 앱을 포함하는 EFS 사용 메일을 제거합니다.|  

 **Windows 10 Mobile, Windows Phone 8.0 및 Windows Phone 8.1**

|장치를 사용 중지할 경우 제거되는 콘텐츠|Windows 10 Mobile, Windows Phone 8 및 Windows Phone 8.1|  
|-|-|
|Configuration Manager 및 Intune을 사용하여 설치된 회사 앱 및 관련 데이터|앱이 제거됩니다. 회사 앱 데이터가 제거됩니다.|  
|VPN 및 Wi-Fi 프로필|Windows 10 Mobile 및 Windows Phone 8.1의 경우 제거됩니다.|  
|인증서|Windows Phone 8.1의 경우 제거됩니다.|  
|관리 에이전트|해당 없음. 관리 에이전트가 기본 제공됨|  
|전자 메일 프로필|Windows Phone 8.0을 제외하고 제거됩니다.|  

Windows 10 Mobile 및 Windows Phone 8.1 장치에서는 다음 설정도 제거됩니다.  

- **모바일 장치의 잠금을 해제하는 데 암호 필요**  
- **단순 암호 허용**  
- **최소 암호 길이**  
- **필수 암호 유형**
- **암호 만료(일)**  
- **암호 기록 기억**  
- **장치를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수**  
- **암호를 요구하기 전까지 비활성 시간(분)**  
- **필수 암호 유형 - 최소 문자 집합 수**  
- **카메라 허용**
- **모바일 장치 암호화 필요**  
- **이동식 저장소 허용**  
- **웹 브라우저 허용**  
- **앱 스토어 허용**  
- **화면 캡처 허용**  
- **지리적 위치 허용**  
- **Microsoft 계정 허용**  
- **복사 및 붙여넣기 허용**  
- **Wi-Fi 테더링 허용**  
- **무료 Wi-Fi 핫스팟에 자동 연결 허용**  
- **Wi-Fi 핫스팟 보고 허용**  
- **공장 재설정 허용**
- **Bluetooth 허용**  
- **NFC 허용**
- **Wi-Fi 허용**

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 원격 초기화를 시작하려면  

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택하고 **장치**를 선택합니다. **장치 컬렉션** 을 선택하고 컬렉션을 선택할 수도 있습니다.  

2. 사용 중지/초기화하려는 장치를 선택합니다.  

3. **장치 그룹**에서 **원격 장치 작업**을 선택한 다음 **사용 중지/초기화**를 선택합니다.  

## <a name="wiping-efs-enabled-content"></a>EFS 지원 콘텐츠 초기화  
Windows 8.1 및 Windows RT 8.1에서 파일 시스템 암호화(EFS)-암호화된 콘텐츠의 선택적 초기화를 지원합니다. 다음은 EFS 지원 콘텐츠의 선택 초기화에 적용됩니다.  

- Intune 계정과 동일한 인터넷 도메인을 사용하는 EFS로 보호되는 앱 및 데이터만 선택적으로 초기화됩니다. 자세한 내용은 [장치 데이터 관리를 위한 Windows 선택적 초기화](http://technet.microsoft.com/library/dn486874.aspx)를 참조하세요.  

- EFS와 연결된 도메인에 대한 변경 사항이 있는 경우 새 도메인을 사용하는 앱 및 데이터를 선택적으로 초기화하기 전에 변경 사항을 적용하는 데 최대 48시간이 걸릴 수 있습니다.  

- Intune에 등록된 각 도메인이 초기화되는 도메인입니다.  

현재 EFS 선택 초기화가 지원되는 데이터 및 앱은 다음과 같습니다.  

- Windows용 메일 앱  

- 작업 폴더

- EFS로 암호화된 파일 및 폴더. 자세한 내용은 [파일 시스템 암호화에 대한 모범 사례](http://support.microsoft.com/kb/223316)항목을 참조하세요.  

### <a name="best-practices-for-selective-wipe"></a>선택 초기화에 대한 모범 사례  

- 메일을 성공적으로 초기화하려면 메일 프로필을 iOS 및 Windows Phone 8.1 장치에 설정해야 합니다.  

- 앱을 성공적으로 초기화하려면 모바일 장치 앱 관리를 통해 앱을 배포해야 합니다.  

- iOS의 경우 사용자가 iCloud를 사용하여 콘텐츠를 복원할 수 없도록 **iCloud에 백업 허용** 설정을 **허용 안함**으로 구성합니다.  

- 계정이 비활성화된 경우에는 1년이 지난 후 Intune에서 계정의 사용이 중지되고 선택 초기화가 수행됩니다.  

##  <a name="passcode-reset"></a>암호 재설정  
사용자가 암호를 잊은 경우 장치에서 암호를 제거하거나 장치에 대한 새로운 임시 암호를 적용하여 사용자를 도울 수 있습니다. 아래 표에는 여러 모바일 플랫폼에서 암호 재설정이 작동하는 방법이 정리되어 있습니다.  

|플랫폼|암호 재설정|  
|--------------|--------------------|  
|iOS|장치에서 암호를 제거하도록 지원됩니다. 새로운 임시 암호를 만들지 않습니다.|
|macOS| 지원 안 됨|
|Android|지원되며 임시 암호가 생성됩니다.|
|Android for Work | 지원 안 됨|
|Windows 10 PC|지원 안 됨|  
|Windows 10 Mobile|Azure AD 결합 장치를 제외하고 지원됩니다.|
|Windows Phone 8.1|지원됨.|  
|Windows RT 8.1 |지원 안 됨|  
|Windows 8.1 PC |지원 안 됨|  

> [!Note]    
> 환경에서 최상위 사이트의 암호 다시 설정 작업을 수행해야 합니다. 예를 들어 중앙 관리 사이트를 사용하는 경우 해당 사이트에서만 작업을 수행할 수 있습니다. 독립 실행형 기본 사이트를 사용하는 경우 해당 사이트에서만 작업을 수행할 수 있습니다.

#### <a name="to-reset-the-passcode-on-a-mobile-device-remotely-in-configuration-manager"></a>Configuration Manager에서 원격으로 모바일 장치의 암호를 재설정하려면  

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택하고 **장치**를 선택합니다. **장치 컬렉션** 을 선택하고 컬렉션을 선택할 수도 있습니다.  

2. 암호를 재설정할 장치를 하나 이상 선택합니다.  

3. **장치 그룹**에서 **원격 장치 작업**을 선택한 다음 **암호 재설정**를 선택합니다.  

#### <a name="to-show-the-state-of-the-passcode-reset"></a>암호 재설정 상태를 표시하려면  

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택하고 **장치**를 선택합니다. **장치 컬렉션** 을 선택하고 컬렉션을 선택할 수도 있습니다.  

2. 암호 재설정 상태를 표시할 장치를 하나 이상 선택합니다.  

3. **장치 그룹**에서 **원격 장치 작업**을 선택한 다음 **암호 상태 표시**를 선택합니다.  

## <a name="remote-lock"></a>원격 잠금  
사용자가 장치를 잃어버린 경우 장치를 원격으로 잠글 수 있습니다. 아래 표에는 여러 모바일 플랫폼에서 원격 잠금이 작동하는 방법이 정리되어 있습니다.  

|플랫폼|원격 잠금|  
|--------------|-----------------|  
|iOS|지원됨.|  
|Android|지원됨.|  
|Windows 10|현재 지원되지 않습니다.|  
|Windows Phone 8 및 Windows Phone 8.1|지원됨.|  
|Windows RT 8.1 |장치의 현재 사용자가 장치를 등록한 사용자인 경우 지원됨|  
|Windows 8.1|장치의 현재 사용자가 장치를 등록한 사용자인 경우 지원됨|  

> [!Note]    
> 환경에서 최상위 사이트의 원격 잠금 작업을 수행해야 합니다. 예를 들어 중앙 관리 사이트를 사용하는 경우 해당 사이트에서만 작업을 수행할 수 있습니다. 독립 실행형 기본 사이트를 사용하는 경우 해당 사이트에서만 작업을 수행할 수 있습니다.

#### <a name="to-lock-a-mobile-device-remotely-through-the-configuration-manager-console"></a>Configuration Manager 콘솔을 통해 원격으로 모바일 장치를 잠그려면  

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택하고 **장치**를 선택합니다. **장치 컬렉션** 을 선택하고 컬렉션을 선택할 수도 있습니다.  

2. 잠글 장치를 하나 이상 선택합니다.  

3. **장치 그룹**에서 **원격 장치 작업**을 선택한 다음 **원격 잠금**을 선택합니다.  

#### <a name="to-show-the-state-of-the-remote-lock"></a>원격 잠금 상태를 표시하려면  

1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택하고 **장치**를 선택합니다. **장치 컬렉션** 을 선택하고 컬렉션을 선택할 수도 있습니다.  

2. 원격 잠금 상태를 표시할 장치를 선택합니다.  

3. **장치 그룹**에서 **원격 장치 작업**을 선택한 다음 **원격 잠금 상태 표시**를 선택합니다.  

### <a name="see-also"></a>참고 항목  
[장치 데이터 관리를 위한 Windows 선택적 초기화](http://technet.microsoft.com/library/dn486874.aspx)   
