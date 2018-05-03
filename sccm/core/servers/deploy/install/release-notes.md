---
title: 릴리스 정보
titleSuffix: Configuration Manager
description: Microsoft 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해서 알아보세요.
ms.custom: na
ms.date: 04/18/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 41
caps.handback.revision: 0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2eabcba6e56bd2a0a9977ab31610a9d747ab6207
ms.sourcegitcommit: e23350fe65ff99228274e465b24b5e163769f38f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/20/2018
---
# <a name="release-notes-for-system-center-configuration-manager"></a>System Center Configuration Manager의 릴리스 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서는 제품 릴리스 정보가 긴급한 문제로 제한됩니다. 이러한 문제는 제품에서 아직 해결되지 않았거나 Microsoft 기술 자료 문서에서 자세히 설명되지 않은 문제입니다.  

기능별 문서에는 핵심 시나리오에 영향을 주는 알려진 문제에 대한 정보가 포함됩니다.  

> [!TIP]  
>  이 항목에는 Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. Technical Preview 분기에 대한 자세한 내용은 [System Center Configuration Manager용 Technical Preview](../../../../core/get-started/technical-preview.md)를 참조하세요.  

다른 버전에서 도입된 새 기능에 대한 자세한 내용은 다음 문서를 참조하세요.
- [버전 1802의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1802)
- [버전 1710의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1710)
- [버전 1706의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1706)  



## <a name="setup-and-upgrade"></a>설치 및 업그레이드  


### <a name="when-using-redistributable-files-from-the-cdlatest-folder-setup-fails-with-a-manifest-verification-error"></a>CD.Latest 폴더의 재배포 가능 파일을 사용하는 경우 매니페스트 확인 오류가 발생하여 설치가 실패합니다.
<!-- 510080, 490569  -->

1606 버전용으로 생성된 CD.Latest 폴더에서 설치 프로그램을 실행하고 해당 CD.Latest 폴더에 포함된 재배포 가능 파일을 사용하는 경우 설치가 실패하고 Configuration Manager 설치 프로그램 로그에 다음 오류가 표시됩니다.

  `ERROR: File hash check failed for defaultcategories.dll`  
  `ERROR: Manifest verification failed. Wrong version of manifest?`

#### <a name="workaround"></a>해결 방법
다음 옵션 중 하나를 사용합니다.
 - 설치하는 동안 Microsoft에서 최신 재배포 가능 파일을 다운로드하도록 선택합니다. CD.Latest 폴더에 포함된 파일 대신 최신 재배포 가능 파일을 사용합니다.
 - 수동으로 *cd.latest\redist\languagepack\zhh* 폴더를 삭제한 다음 설치 프로그램을 다시 실행합니다.


### <a name="setup-command-line-option-joinceip-must-be-specified"></a>설치 명령줄 옵션 JoinCEIP를 지정해야 함
<!--510806-->
*적용 대상: Configuration Manager 버전 1802*

Configuration Manager 버전 1802부터 CEIP(사용자 환경 개선 프로그램) 기능은 제품에서 제거됩니다. 명령줄 또는 무인 스크립트에서 새 사이트의 [설치를 자동화하는](/sccm/core/servers/deploy/install/command-line-options-for-setup) 경우 설치 프로그램은 필요한 매개 변수가 누락되었다는 오류를 반환합니다. 

#### <a name="workaround"></a>해결 방법
설치 프로세스의 결과에 영향을 주지 않으면서, 설치 명령줄에 **JoinCEIP** 매개 변수를 포함합니다.

 > [!Note]  
 > [콘솔 설치 프로그램](/sccm/core/servers/deploy/install/install-consoles)에 대한 EnableSQM 매개 변수가 필요하지 않습니다.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>클라이언트 배포 및 업그레이드

### <a name="azure-ad-enabled-clients-cant-communicate-with-management-point"></a>Azure AD 사용 클라이언트가 관리 지점과 통신할 수 없습니다.
<!--501089-->
*적용 대상: Configuration Manager 버전 1706*
<!--also fixed in 1710 HFRU-->
[인증을 위해 Azure AD를 사용하여 Configuration Manager Windows 10 클라이언트를 설치 및 할당](/sccm/core/clients/deploy/deploy-clients-cmg-azure)하는 시나리오에서 HTTPS 사용 관리 지점이 대체 데이터베이스 자격 증명을 사용하는 경우 클라이언트 통신에 실패합니다. 

#### <a name="workaround"></a>해결 방법
이 문제를 완화하려면 다음 작업 중 하나를 수행합니다.
- 최신 버전으로 사이트를 업데이트하고 최신 핫픽스를 적용합니다.
- 관리 지점에서 사용하는 자격 증명을 변경합니다.


<!-- ## Operating system deployment  -->



## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="servicing-plans-create-many-duplicate-software-update-groups-and-deployments-by-default"></a>서비스 계획은 기본적으로 중복 소프트웨어 업데이트 그룹 및 배포를 많이 만듭니다.  
<!-- 474326 -->
기본적으로 서비스 계획 만들기 마법사는 현재 소프트웨어 업데이트를 동기화한 후마다 실행됩니다. 마법사가 실행될 때마다 새 소프트웨어 업데이트 그룹 및 배포가 생성됩니다. 하루에 여러 번 실행되는 소프트웨어 업데이트 동기화 일정을 사용하는 경우 계획 서비스 만들기 마법사에서 매일 소프트웨어 업데이트 그룹 및 배포를 여러 개 만듭니다.  

#### <a name="workaround"></a>해결 방법
 서비스 계획을 만든 후 서비스 계획에 대한 속성을 열고, **평가 일정** 탭으로 이동하고, **일정에 따라 규칙 실행**을 선택하고, **사용자 지정**을 클릭하여 사용자 지정 일정을 만듭니다. 예를 들어 60일마다 실행하는 서비스 계획이 있을 수 있습니다.  


### <a name="changing-office-365-client-setting-doesnt-apply"></a>Office 365 클라이언트 설정 변경이 적용되지 않습니다. 
<!--511551-->
*적용 대상: Configuration Manager 버전 1802*  

**Office 365 클라이언트 에이전트 관리 사용**이 `Yes`로 구성된 [클라이언트 설정](/sccm/core/clients/deploy/about-client-settings#enable-management-of-the-office-365-client-agent)을 배포합니다. 그런 다음, 설정을 `No` 또는 `Not Configured`로 변경합니다. 대상 클라이언트에서 정책을 업데이트하면 Office 365 업데이트가 Configuration Manager에서 계속 관리됩니다. 

#### <a name="workaround"></a>해결 방법
다음 레지스트리 값을 `0`으로 변경하고 **Microsoft Office 간편 실행 서비스**(ClickToRunSvc)를 다시 시작합니다.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\office\16.0\Common\officeupdate]
"OfficeMgmtCOM"=dword:00000000
```



## <a name="mobile-device-management"></a>모바일 장치 관리  

### <a name="you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10"></a>Windows Phone 8.1 VPN 프로필을 Windows 10에 더 이상 배포할 수 없습니다.
<!-- 503274  -->
*적용 대상: Configuration Manager 버전 1710*

Windows 10 장치에도 적용 가능한 Windows Phone 8.1 워크플로를 사용하여 VPN 프로필을 만들 수 없습니다. 이러한 프로필의 경우 만들기 마법사에 지원되는 플랫폼 페이지가 더 이상 표시되지 않습니다. 백 엔드에서 Windows Phone 8.1이 자동으로 선택됩니다. 지원되는 플랫폼 페이지는 프로필 속성에서 사용할 수 있지만 Windows 10 옵션이 표시되지 않습니다.

#### <a name="workaround"></a>해결 방법
 Windows 10 장치의 경우 Windows 10 VPN 프로필 워크플로를 사용합니다. 이 옵션이 환경에 적합하지 않은 경우 지원 서비스에 문의하세요. 지원 서비스를 통해 Windows 10 타기팅을 추가할 수 있습니다.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
