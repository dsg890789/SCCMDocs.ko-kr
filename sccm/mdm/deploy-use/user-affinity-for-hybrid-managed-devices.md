---
title: 하이브리드 관리 디바이스에 대한 사용자 선호도
titleSuffix: Configuration Manager
description: Configuration Manager에서 관리 디바이스에 대한 사용자 선호도를 구성합니다.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b5d520a7-e9e5-40ee-91f9-f2684214beb6
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: d673a77c8d0e0abb9cf273f0333acbe31aa87ddd
ms.sourcegitcommit: 7f64c5fb3e9fa3dba006af618b1f1ceaf61a99f0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/28/2019
ms.locfileid: "75519687"
---
# <a name="user-affinity-for-hybrid-managed-devices-in-configuration-manager"></a>Configuration Manager의 하이브리드 관리 디바이스에 대한 사용자 선호도

*적용 대상: Configuration Manager (현재 분기)*

회사 소유 디바이스의 프로필을 구성할 때 관리자는 디바이스로 특정 사용자를 식별하는 *사용자 선호도*를 관리 디바이스가 포함할 수 있는지 여부를 지정할 수 있습니다.  

##  <a name="BKMK_iOSCP"></a> 사용자 선호도를 포함하는 관리 디바이스  
 **사용자 선호도**로 구성한 디바이스에서 회사 포털 앱을 설치하고 실행하여 앱을 다운로드하고 디바이스를 관리할 수 있습니다. 디바이스를 받은 사용자는 몇 가지 추가 단계를 완료하여 설정 도우미를 완료하고 회사 포털 앱을 설치해야 합니다.  

#### <a name="how-to-enroll-ios-devices-with-user-affinity"></a>사용자 선호도를 사용하여 iOS 디바이스를 등록하는 방법  

1.  사용자가 새 디바이스를 처음 켜면 설정 도우미를 완료하라는 메시지가 표시됩니다. 등록 프로필에서 설정하는 동안 자격 증명을 묻는 메시지가 표시되도록 지정할 수 있습니다. 사용자는 Intune에서 구독과 연결된 자격 증명(즉, 고유 개인 이름 또는 UPN)을 사용해야 합니다.  

2.  설정하는 동안 Apple ID를 묻는 메시지가 표시될 수도 있습니다. Apple ID를 제공해야 디바이스에서 회사 포털을 설치할 수 있습니다. 사용자는 iOS **설정** 메뉴에서 설정을 완료한 후에 Apple ID를 제공할 수 있습니다.  

3.  설정을 완료 한 후 iOS 디바이스에서 App Store의 회사 포털 앱(예: [회사 포털 앱](https://itunes.apple.com/us/app/id719171358))을 설치해야 합니다.  

4.  이제 디바이스를 설정할 때 사용된 UPN을 사용하여 회사 포털에 로그인할 수 있습니다.  

5.  로그인한 후에는 디바이스를 등록하라는 메시지가 표시됩니다. 첫 번째 단계는 **디바이스를 식별**하는 것입니다. 앱에서 이미 회사에 등록되어 최종 사용자의 Intune 계정에 할당된 iOS 디바이스 목록을 표시합니다. 일치하는 디바이스를 선택합니다.  

     이 디바이스가 아직 회사에 등록되지 않은 경우 "새 디바이스"를 선택하여 표준 등록 흐름에 따라 계속 진행합니다.  

6.  다음 화면에서 새 디바이스의 일련 번호를 확인해야 합니다. "일련 번호 확인" 링크를 탭하여 설정 앱을 시작해서 일련 번호를 확인할 수 있습니다. 그런 다음 회사 포털 앱에 일련 번호의 마지막 4자리를 입력해야 합니다.  

     이 단계에서는 디바이스가 Intune에 등록된 회사 디바이스인지 확인합니다. 디바이스의 일련 번호와 일치하지 않으면 잘못된 디바이스를 선택한 것입니다. 이전 화면으로 돌아가서 다른 디바이스를 선택합니다.  

7.  일련 번호를 확인한 후 회사 포털 앱에서 회사 포털 웹 사이트로 리디렉션하여 등록을 마친 후 앱으로 돌아가라는 메시지를 표시합니다.  

8.  이제 등록이 완료되었습니다. 이제 기능의 전체 집합으로 이 디바이스를 사용할 수 있습니다.  

##  <a name="BKMK_noUA"></a> 사용자 선호도가 없는 관리 디바이스  
 **사용자 선호도 없음**으로 구성된 디바이스에서는 회사 포털을 지원하지 않으므로 앱을 설치하지 않아야 합니다. 회사 포털은 회사 자격 증명을 갖고 있으며 개인 설정된 회사 리소스(예: 메일)에 대한 액세스 권한이 필요한 사용자를 위해 설계되었습니다. **사용자 선호도 없음** 으로 등록된 디바이스의 경우에는 전용 사용자가 로그인할 필요가 없습니다. 키오스크, POS(Point of Sale) 또는 공유 유틸리티 디바이스는 사용자 선호도 없음으로 등록된 디바이스에 대한 일반적인 사용 사례입니다. 사용자 선호도가 필요한 경우 디바이스를 등록하기 전에 디바이스의 등록 프로필에서 **사용자 선호도** 가 선택되어 있어야 합니다. 디바이스에 대한 선호도 상태를 변경하려면 디바이스를 사용 중지한 후 다시 등록해야 합니다.
