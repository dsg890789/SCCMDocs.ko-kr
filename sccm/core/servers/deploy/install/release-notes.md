---
title: 릴리스 정보
titleSuffix: Configuration Manager
description: Microsoft 지원 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해 알아봅니다.
ms.date: 02/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: bc19092f1272611ea3e05d708bf89bda1a4ba3b9
ms.sourcegitcommit: 0a23cde6112cbb5987f433bffcf6f223b994ba72
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56667463"
---
# <a name="release-notes-for-configuration-manager"></a>Configuration Manager의 릴리스 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서는 제품 릴리스 정보가 긴급한 문제로 제한됩니다. 이러한 문제는 제품에서 아직 해결되지 않았거나 Microsoft 지원 기술 자료 문서에서 자세히 설명되지 않은 문제입니다.  

기능별 문서에는 핵심 시나리오에 영향을 주는 알려진 문제에 대한 정보가 포함됩니다.  

> [!TIP]  
>  이 항목에는 Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. 기술 미리 보기 분기에 대한 자세한 내용은 [기술 미리 보기](/sccm/core/get-started/technical-preview)를 참조하세요.  

다른 버전에서 도입된 새 기능에 대한 자세한 내용은 다음 문서를 참조하세요.
- [버전 1810의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1810)
- [버전 1806의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1806)  
- [버전 1802의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1802)



## <a name="set-up-and-upgrade"></a>설치 및 업그레이드  


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
설치 프로세스의 결과에 영향을 주지 않지만 설치 명령줄에 **JoinCEIP** 매개 변수를 포함합니다.

 > [!Note]  
 > [콘솔 설치 프로그램](/sccm/core/servers/deploy/install/install-consoles)에 대한 EnableSQM 매개 변수가 필요하지 않습니다.


### <a name="cloud-service-manager-component-stopped-on-site-server-in-passive-mode"></a>클라우드 서비스 관리자 구성 요소가 수동 모드의 사이트 서버에서 정지
<!--VSO 2858826, SCCMDocs issue 772-->
*적용 대상: Configuration Manager 버전 1806*

[서비스 연결 지점](/sccm/core/servers/deploy/configure/about-the-service-connection-point)이 [수동 모드의 사이트 서버](/sccm/core/servers/deploy/configure/site-server-high-availability)에 배치되면 [클라우드 관리 게이트웨이](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)의 배포 및 모니터링이 시작되지 않습니다. 클라우드 서비스 관리자 구성 요소(SMS_CLOUD_SERVICES_MANAGER)가 중지 상태에 있습니다.

#### <a name="workaround"></a>해결 방법
서비스 연결점 역할을 다른 서버로 이동합니다.



<!-- ## Backup and recovery  -->


<!--## Client deployment and upgrade-->



## <a name="os-deployment"></a>OS 배포

### <a name="after-passive-site-server-is-promoted-the-default-boot-image-packages-still-have-package-source-on-the-previous-active-server"></a>수동 사이트 서버가 승격된 후에도 기본 부팅 이미지 패키지에는 이전 활성 서버의 패키지 소스가 여전히 있습니다.
<!--3453224, SCCMDocs-pr issue 3097-->
*적용 대상: Configuration Manager 버전 1810*

수동 모드(서버 B)의 사이트 서버가 있는 경우, 사이트 서버를 활성으로 승격할 때 기본 부팅 이미지의 콘텐츠 위치는 이전의 활성 서버(서버 A)를 계속 참조합니다. 서버 A에 하드웨어 오류가 있으면 기본 부팅 이미지를 업데이트하거나 변경할 수 없습니다.

#### <a name="workaround"></a>해결 방법
없음



## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="security-roles-are-missing-for-phased-deployments"></a>단계적 배포에 대한 보안 역할이 누락됨
<!--3479337, SCCMDocs-pr issue 3095-->
*적용 대상: Configuration Manager 버전 1810*

**OS 배포 관리자** 기본 제공 보안 역할에는 [단계적 배포](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)에 대한 권한이 있습니다. 이러한 권한이 없는 역할은 다음과 같습니다.  

- **애플리케이션 관리자**  
- **애플리케이션 배포 관리자**  
- **소프트웨어 업데이트 관리자**  

**앱 작성자** 역할은 단계적 배포에 대한 일부 권한이 있는 것처럼 보일 수 있지만 배포를 만들 수 없습니다. 

이러한 역할이 있는 사용자는 단계적 배포 만들기 마법사를 시작할 수 있으며, 애플리케이션 또는 소프트웨어 업데이트에 대한 단계적 배포를 확인할 수 있습니다. 그러나 마법사를 완료하거나 기존 배포를 변경할 수 없습니다.

#### <a name="workaround"></a>해결 방법
사용자 지정 보안 역할을 만듭니다. 기존 보안 역할을 복사하고, **단계적 배포** 개체 클래스에 다음 권한을 추가합니다.
- 만들기  
- 삭제  
- 수정  
- 읽기  

자세한 내용은 [사용자 지정 보안 역할 만들기](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_CreateSecRole)를 참조하세요.


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



## <a name="mobile-device-management"></a>모바일 디바이스 관리  

### <a name="you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10"></a>Windows Phone 8.1 VPN 프로필을 Windows 10에 더 이상 배포할 수 없습니다.
<!-- 503274  -->
*적용 대상: Configuration Manager 버전 1710*

Windows 10 디바이스에도 적용 가능한 Windows Phone 8.1 워크플로를 사용하여 VPN 프로필을 만들 수 없습니다. 이러한 프로필의 경우 만들기 마법사에 지원되는 플랫폼 페이지가 더 이상 표시되지 않습니다. 백 엔드에서 Windows Phone 8.1이 자동으로 선택됩니다. 지원되는 플랫폼 페이지는 프로필 속성에서 사용할 수 있지만 Windows 10 옵션이 표시되지 않습니다.

#### <a name="workaround"></a>해결 방법
 Windows 10 디바이스의 경우 Windows 10 VPN 프로필 워크플로를 사용합니다. 이 옵션이 환경에 적합하지 않은 경우 지원 서비스에 문의하세요. 지원 서비스를 통해 Windows 10 타기팅을 추가할 수 있습니다.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
