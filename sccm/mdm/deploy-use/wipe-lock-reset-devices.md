---
title: 온-프레미스 MDM을 사용 하 여 장치 관리
titleSuffix: Configuration Manager
description: Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 전체 초기화, 선택적 초기화, 원격 잠금 또는 암호 재설정으로 장치 데이터를 보호 합니다.
ms.date: 08/14/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: feacf91e43404401bae62c5527798c7a56356661
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76032661"
---
# <a name="manage-devices-and-protect-data-with-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM을 사용 하 여 장치 관리 및 데이터 보호

*적용 대상: Configuration Manager (현재 분기)*

모바일 장치는 중요 한 데이터를 저장 하 고 많은 조직 리소스에 쉽게 액세스할 수 있습니다. 장치 및 데이터를 보호 하려면 다음 장치 관리 작업에 Configuration Manager를 사용 합니다.

- **전체 초기화**: 장치를 출하 시 설정으로 복원 합니다.

- **선택적 초기화**: 조직 데이터만 제거 합니다.

- **암호 재설정**: 사용자가 암호를 잊어버린 경우 암호를 제거 하거나 다시 설정 합니다.

- **원격 잠금**: 손실 될 수 있는 장치를 보호 하는 데 도움이 됩니다.

## <a name="full-wipe"></a>전체 초기화  

분실 한 장치를 보호 해야 하거나 장치의 활성 사용을 중지할 때 전체 초기화를 시작할 수 있습니다. 이 작업을 수행 하면 장치가 공장 기본값으로 복원 됩니다. 모든 조직 및 사용자 데이터와 설정이 제거 됩니다.

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **장치** 노드를 선택 합니다. **장치 컬렉션** 을 선택 하 고 장치가 멤버로 속해 있는 컬렉션을 선택할 수도 있습니다.

1. 초기화 하려는 장치를 선택 합니다.

1. 리본 메뉴의 장치 그룹에서 **원격 장치 작업**을 선택한 후 사용 **중지/초기화**를 선택 합니다.

1. **Configuration Manager에서 사용 중지** 창에서 **모바일 장치를 초기화 하 고 Configuration Manager에서**사용을 중지 하는 옵션을 선택 합니다.

## <a name="selective-wipe"></a>선택적 초기화

장치에서 조직 데이터만 제거 하려면 선택적 초기화를 시작 합니다.

### <a name="behaviors-by-os-version"></a>OS 버전별 동작

다음 표에서는 제거 되는 데이터와 선택적 초기화 후 장치에 남아 있는 데이터에 대 한 영향을 설명 합니다.

#### <a name="windows-10-windows-81-windows-rt-81-and-windows-rt"></a>Windows 10, Windows 8.1, Windows RT 8.1 및 Windows RT

|Content|선택적 초기화 동작|  
|-------|--------|
|Configuration Manager에 의해 설치 된 앱 및 연결 된 데이터|앱을 제거 하 고 모든 테스트용 로드 키를 제거 합니다. Windows 선택적 초기화를 사용 하는 앱에 대 한 암호화 키를 해지 하 고 데이터에 더 이상 액세스할 수 없습니다.|
|VPN 및 Wi-Fi 프로필|프로필을 제거 합니다.|
|인증서|인증서를 제거 하 고 해지 합니다.|
|설정|요구 사항 제거|
|전자 메일 프로필|Windows 전자 메일 및 첨부 파일용 메일 앱을 포함 하는 EFS 사용 메일을 제거 합니다.|

#### <a name="windows-10-mobile-windows-phone-80-and-windows-phone-81"></a>Windows 10 Mobile, Windows Phone 8.0 및 Windows Phone 8.1

|Content|선택적 초기화 동작|  
|-------|--------|
|Configuration Manager에 의해 설치 된 회사 앱 및 관련 데이터|앱을 제거 하 고 조직 앱 데이터를 제거 합니다.|
|VPN 및 Wi-Fi 프로필|Windows 10 Mobile 및 Windows Phone 8.1에 대 한 프로필을 제거 합니다.|
|인증서|Windows Phone 8.1에 대 한 인증서를 제거 합니다.|
|전자 메일 프로필|프로필을 제거 합니다 (Windows Phone 8.0).|

Windows 10 Mobile 및 Windows Phone 8.1 디바이스에서는 다음 설정도 제거됩니다.  

- **모바일 디바이스의 잠금을 해제하는 데 암호 필요**  
- **단순 암호 허용**  
- **최소 암호 길이**  
- **필수 암호 유형**
- **암호 만료(일)**  
- **암호 기록 기억**  
- **디바이스를 초기화하기 전까지 허용되는 로그인 반복 오류 횟수**  
- **암호를 요구하기 전까지 비활성 시간(분)**  
- **필수 암호 유형 - 최소 문자 집합 수**  
- **카메라 허용**
- **모바일 디바이스 암호화 필요**  
- **이동식 스토리지 허용**  
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

### <a name="start-a-selective-wipe"></a>선택적 초기화 시작

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **장치** 노드를 선택 합니다. **장치 컬렉션** 을 선택 하 고 장치가 멤버로 속해 있는 컬렉션을 선택할 수도 있습니다.

1. 초기화 하려는 장치를 선택 합니다.

1. 리본 메뉴의 장치 그룹에서 **원격 장치 작업**을 선택한 후 사용 **중지/초기화**를 선택 합니다.

1. **Configuration Manager에서 사용 중지** 창에서 **회사 콘텐츠 초기화 및 Configuration Manager 모바일 장치 사용 중지**옵션을 선택 합니다.

### <a name="recommendations-for-selective-wipe"></a>선택적 초기화에 대 한 권장 사항

- 전자 메일을 성공적으로 초기화 하려면 전자 메일 프로필을 Windows Phone 8.1 장치로 설정 합니다.

- 앱을 성공적으로 초기화하려면 모바일 디바이스 앱 관리를 통해 앱을 배포해야 합니다.

## <a name="passcode-reset"></a>암호 재설정

사용자가 암호를 잊은 경우이 작업을 사용 하 여 장치에서 새 임시 암호를 강제로 적용 합니다. 암호를 완전히 제거할 수도 있습니다. 다음 표에는 여러 모바일 플랫폼에서 암호 재설정이 작동하는 방법이 정리되어 있습니다.

| OS 버전 | 암호 재설정 |
|------------|----------------|
| Windows 10 | 지원되지 않음 |
| Windows 10 Mobile | 지원 됨, Azure Active Directory 연결 된 장치 제외 |
| Windows Phone 8 및 Windows Phone 8.1 | 지원됨 |
| Windows RT 8.1 | 지원되지 않음 |
| Windows 8.1 | 지원되지 않음 |

> [!Note]
> 최상위 사이트에서 암호 재설정 작업을 시작 합니다. 예를 들어 중앙 관리 사이트를 사용 하는 경우 해당 사이트 에서만 작업을 수행할 수 있습니다. 독립 실행형 기본 사이트를 사용 하는 경우 해당 사이트 에서만 작업을 수행할 수 있습니다.

### <a name="remotely-reset-the-passcode-on-a-mobile-device"></a>모바일 장치에서 암호를 원격으로 다시 설정

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **장치** 노드를 선택 합니다. **장치 컬렉션** 을 선택 하 고 장치가 멤버로 속해 있는 컬렉션을 선택할 수도 있습니다.

1. 암호를 재설정할 디바이스를 하나 이상 선택합니다.

1. 리본 메뉴의 장치 그룹에서 **원격 장치 작업**을 선택한 다음 **암호 재설정**을 선택 합니다.  

### <a name="show-the-state-of-the-passcode-reset"></a>암호 재설정의 상태를 표시 합니다.  

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **장치** 노드를 선택 합니다. **장치 컬렉션** 을 선택 하 고 장치가 멤버로 속해 있는 컬렉션을 선택할 수도 있습니다.

1. 암호 재설정 상태를 표시할 디바이스를 하나 이상 선택합니다.

1. 리본 메뉴의 장치 그룹에서 **원격 장치 작업**을 선택한 다음 **암호 상태 표시**를 선택 합니다.  

## <a name="remote-lock"></a>원격 잠금

사용자가 디바이스를 잃어버린 경우 디바이스를 원격으로 잠글 수 있습니다. 아래 표에는 여러 모바일 플랫폼에서 원격 잠금이 작동하는 방법이 정리되어 있습니다.  

|OS 버전|원격 잠금|
|----------|-----------|
|Windows 10|지원되지 않음|
|Windows Phone 8 및 Windows Phone 8.1|지원됨|
|Windows RT 8.1|장치의 현재 사용자가 장치를 등록 한 사용자 인 경우 지원 됩니다.|
|Windows 8.1|장치의 현재 사용자가 장치를 등록 한 사용자 인 경우 지원 됩니다.|

> [!Note]
> 최상위 사이트에서 원격 잠금 작업을 시작 합니다. 예를 들어 중앙 관리 사이트를 사용 하는 경우 해당 사이트 에서만 작업을 수행할 수 있습니다. 독립 실행형 기본 사이트를 사용 하는 경우 해당 사이트에서 작업을 수행 합니다.

### <a name="remotely-lock-a-mobile-device"></a>모바일 장치 원격 잠금

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **장치** 노드를 선택 합니다. **장치 컬렉션** 을 선택 하 고 장치가 멤버로 속해 있는 컬렉션을 선택할 수도 있습니다.

1. 잠글 디바이스를 하나 이상 선택합니다.

1. 리본 메뉴의 장치 그룹에서 **원격 장치 작업**을 선택한 다음 **원격 잠금**을 선택 합니다. 동작을 확인 합니다.

### <a name="show-the-state-of-the-remote-lock"></a>원격 잠금의 상태를 표시 합니다.

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동 하 고 **장치** 노드를 선택 합니다. **장치 컬렉션** 을 선택 하 고 장치가 멤버로 속해 있는 컬렉션을 선택할 수도 있습니다.

1. 원격 잠금 상태를 표시할 디바이스를 선택합니다.

1. 리본 메뉴의 장치 그룹에서 **원격 장치 작업**을 선택한 다음 **원격 잠금 상태 표시**를 선택 합니다.
