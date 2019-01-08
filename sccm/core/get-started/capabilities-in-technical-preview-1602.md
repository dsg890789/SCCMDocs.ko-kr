---
title: 기술 미리 보기 1602의 기능
titleSuffix: Configuration Manager
description: System Center Configuration Manager용 Technical Preview 버전 1602에서 사용 가능한 기능에 대해 알아봅니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
author: aczechowski
robots: noindex,nofollow
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 875ee80050b10561471f98ec73625055c5975257
ms.sourcegitcommit: 48098f9fb2f447672bf36d50c9f58a3d26acb9ed
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53416676"
---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>System Center Configuration Manager용 Technical Preview 1602의 기능

*적용 대상: System Center Configuration Manager(Technical Preview)*

이 문서에서는 System Center Configuration Manager용 Technical Preview 버전 1602에서 사용 가능한 기능을 소개합니다. 이 버전을 설치하여 Configuration Manager Technical Preview 사이트를 업데이트하고 새로운 기능을 추가할 수 있습니다. 이 버전의 Technical Preview를 설치하기 전에 소개 항목인 [System Center Configuration Manager용 Technical Preview](../../core/get-started/technical-preview.md)를 검토하여 Technical Preview 사용을 위한 일반 요구 사항 및 제한 사항, 버전 업데이트 방법 및 Technical Preview의 기능에 대해 피드백 제공 방법 등에 익숙해져야 합니다.  

 다음은 이 버전에서 사용할 수 있는 새로운 기능입니다.  

##  <a name="BKMK_MDM"></a> 모바일 디바이스 관리 개선  

### <a name="ios-activation-lock"></a>iOS 활성화 잠금  
 System Center Configuration Manager를 사용하면 iOS 7.1 이상 디바이스용 나의 iPhone 찾기(Find My iPhone) 앱의 기능인 iOS 활성화 잠금을 관리할 수 있습니다. 활성화 잠금은 디바이스에서 나의 iPhone 찾기 앱을 사용할 때 자동으로 사용하도록 설정됩니다. 활성화 잠금이 설정되면 사용자의 Apple ID와 암호를 입력해야 다음 작업을 수행할 수 있습니다.  

- 나의 iPhone 찾기 끄기  

- 디바이스의 콘텐츠 지우기  

- 디바이스 다시 활성화  

  Configuration Manager에서는 iOS 7.1 이상을 실행하는 감독된/감독되지 않은 디바이스의 활성화 잠금 상태를 요청할 수 있습니다. 감독된 디바이스의 경우 Intune은 활성화 잠금 무시 코드를 검색하여 디바이스에 직접 제공할 수 있습니다.  

  자세한 내용은 [Configuration Manager의 활성화 잠금 바이패스를 사용하여 iOS 디바이스 보호](/sccm/mdm/deploy-use/manage-ios-activation-lock)를 참조하세요.  

##  <a name="BKMK_SC1601"></a> 1602 버전에서 소프트웨어 센터의 개선 사항  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>소프트웨어 센터에서 PC 컴퓨터 및 사용자 정책 새로 고침  
 PC가 해당 Configuration Manager 컴퓨터 및 사용자 정책을 새로 고치도록 하는 새 옵션, **동기화 정책**이 **옵션** > **컴퓨터 유지 관리** 페이지에 추가되었습니다.  

##  <a name="BKMK_Win10Servicing"></a> Windows 10 서비스 개선  
 1602 Technical Preview에서는 Windows 10 서비스에 대해 다음과 같은 개선된 기능을 추가했습니다.  

-   서비스 계획에 대한 새 필터 옵션  이제 **언어**, **필수** 및 **제목**에 대해 필터링을 수행할 수 있습니다. 지정된 조건을 충족하는 업그레이드만 연결된 배포에 추가됩니다.  

-   소프트웨어 업데이트 동기화에 대해 **업그레이드** 분류를 선택하면 소프트웨어 업데이트를 성공적으로 동기화하고 Windows 10 서비스를 올바르게 작동하기 위해 WSUS [핫픽스 3095113](https://support.microsoft.com/kb/3095113)이 필요하다는 사실을 알리기 위한 경고 대화 상자가 표시됩니다.  이 대화 상자에서 해당 핫픽스에 대한 기술 자료 문서를 이동할 수 있습니다.  

-   이제 사용 가능한 Windows 10 업그레이드가 Configuration Manager 콘솔의 **Windows 10 서비스** \ **모든 Windows 10 업데이트** 노드에만 표시됩니다. 이러한 업데이트가 **소프트웨어 업데이트** \ **모든 소프트웨어 업데이트** 노드에는 표시되지 않습니다.  

-   Windows 10 업그레이드 패키지를 시작하는 최종 사용자에게는 해당 운영 체제를 업그레이드할 것임을 알려주는 대화 상자가 표시됩니다.  
