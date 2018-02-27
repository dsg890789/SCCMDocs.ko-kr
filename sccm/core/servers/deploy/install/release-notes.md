---
title: "릴리스 정보 "
titleSuffix: Configuration Manager
description: "Microsoft 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해서는 이 정보를 참조하세요."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 53685ef2647cfd87c2fcb603097186360f1c96a5
ms.sourcegitcommit: fbd4a9d2fa8ed4ddd3a0fecc4a2ec4fc0ccc3d0c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/19/2018
---
# <a name="release-notes-for-system-center-configuration-manager"></a>System Center Configuration Manager의 릴리스 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager에서는 제품 릴리스 정보가 긴급한 문제로 제한됩니다. 이러한 문제는 제품에서 아직 해결되지 않았거나 Microsoft 기술 자료 문서에서 자세히 설명되지 않은 문제입니다.  

기능별 문서에는 핵심 시나리오에 영향을 주는 알려진 문제에 대한 정보가 포함됩니다.  

> [!TIP]  
>  이 항목에는 Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. Technical Preview 분기에 대한 자세한 내용은 [System Center Configuration Manager용 Technical Preview](../../../../core/get-started/technical-preview.md)를 참조하세요.  

다른 버전에서 도입된 새 기능에 대한 자세한 내용은 다음 문서를 참조하세요.
- [버전 1710의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1710)
- [버전 1706의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1706)  
- [버전 1702의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1702)



## <a name="setup-and-upgrade"></a>설치 및 업그레이드  


### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>버전 1606을 사용하여 장기 서비스 분기 사이트를 설치하는 경우 현재 분기 사이트가 설치됨
<!-- Consider move to core content  -->
2016년 10월 릴리스의 버전 1606 기준 미디어를 사용하여 LTSB(장기 서비스 분기) 사이트를 설치하는 경우 현재 분기 사이트가 대신 설치됩니다. 이 동작은 사이트 설치를 사용하여 서비스 연결 지점을 설치하는 옵션을 선택하지 않았기 때문에 발생합니다.

 - 서비스 연결 지점이 필요하지 않더라도 LTSB 사이트를 설치하려면 설치 중에 선택해야 합니다.

설치가 완료된 후 서비스 연결 지점을 제거할 수 있습니다. 그러나 원격 분석 데이터를 제출하고 현재 분기 및 LTSB 사이트 둘 다에 대한 보안 업데이트를 가져오려면 오프라인 또는 온라인 모드의 서비스 연결 지점이 있어야 합니다.

사이트가 현재 분기 사이트로 설치되었지만 LTSB를 설치하려는 경우 사이트를 제거한 후 다시 설치할 수 있습니다. 또는 [Microsoft 도움말 및 지원](http://go.microsoft.com/fwlink/?LinkId=243064)에 도움을 요청할 수 있습니다.  

설치된 분기를 확인하려면 콘솔의 **관리** > **사이트 구성** > **사이트**에서 **계층 설정**을 엽니다. 사이트를 현재 분기 사이트로 변환하는 옵션은 사이트에서 LTSB를 실행하는 경우에만 사용할 수 있습니다.  

**해결 방법:** 없음   


### <a name="an-update-persists-in-downloading-state-in-the-updates-and-servicing-node-of-the-console"></a>콘솔의 업데이트 및 서비스 노드에서 업데이트가 다운로드 중 상태로 유지됨  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
온라인 서비스 연결 지점을 통해 업데이트를 자동으로 다운로드하는 동안 업데이트가 다운로드 중 상태로 고정될 수 있습니다. 업데이트의 다운로드가 고정되면 걸려 표시된 로그 파일에 다음과 유사한 항목이 표시됩니다.  

DMPdownloader 로그:  
`ERROR: Failed to download redist for 037cd17e-4d7b-40e1-802b-14bb682364c7 with command  /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 /RedistVersion 112015 /NoUI  "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"`  

ConfigMgrSetup.log:  
`Error: failed to verify 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi' authenticode signature.`  
`Error: file signature check failed for 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi`  

**해결 방법**: 사이트 서버에서 다음 레지스트리 키를 다음 값과 일치하도록 수정합니다.  

-   **편집할 키**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software Publishing  

-   **상태 값**: **146944** 10진수 또는 **0x00023e00** 16진수로 설정  

그런 다음, SMS_Executive 서비스를 다시 시작하거나 다음 자동 다운로드 주기까지 최대 24시간 동안 기다립니다.

### <a name="when-using-redistributable-files-from-the-cdlatest-folder-setup-fails-with-a-manifest-verification-error"></a>CD.Latest 폴더의 재배포 가능 파일을 사용하는 경우 매니페스트 확인 오류가 발생하여 설치가 실패합니다.
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

1606 버전용으로 생성된 CD.Latest 폴더에서 설치 프로그램을 실행하고 해당 CD.Latest 폴더에 포함된 재배포 가능 파일을 사용하는 경우 설치가 실패하고 Configuration Manager 설치 프로그램 로그에 다음 오류가 표시됩니다.

  `ERROR: File hash check failed for defaultcategories.dll`  
  `ERROR: Manifest verification failed. Wrong version of manifest?`

**해결 방법:** 다음 옵션 중 하나를 사용합니다.
 - 설치하는 동안 Microsoft에서 최신 재배포 가능 파일을 다운로드하도록 선택합니다. CD.Latest 폴더에 포함된 파일 대신 최신 재배포 가능 파일을 사용합니다.
 - 수동으로 *cd.latest\redist\languagepack\zhh* 폴더를 삭제한 다음 설치 프로그램을 다시 실행합니다.



<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>클라이언트 배포 및 업그레이드  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>오류 코드 0x8007064c를 나타내며 클라이언트 설치가 실패합니다.
<!--- SMS 486973  applies 1606 to 1706. Not yet fixed. -->
*다음 문제는 Configuration Manager의 모든 활성 버전에 적용됩니다.*  

Windows 컴퓨터에 클라이언트를 배포할 때 설치가 실패합니다. ccmsetup.log 파일에 다음 항목이 포함됩니다. 

`File 'C:\WINDOWS\ccmsetup\Silverlight.exe' returned failure exit code 1612. Fail the installation`  
`InstallFromManifest failed 0x8007064c`

**해결 방법** 이 문제는 이전에 설치한 Silverlight 버전이 손상되었기 때문에 발생합니다. 이 문제를 해결하려면 영향을 받는 컴퓨터에서 다음 도구를 실행합니다. [프로그램이 설치 또는 제거되지 않도록 하는 문제 해결](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed).

## <a name="operating-system-deployment"></a>운영 체제 배포  

### <a name="servicing-plans-create-many-duplicate-software-update-groups-and-deployments-by-default"></a>서비스 계획은 기본적으로 중복 소프트웨어 업데이트 그룹 및 배포를 많이 만듭니다.  
기본적으로 서비스 계획 만들기 마법사는 현재 소프트웨어 업데이트를 동기화한 후마다 실행됩니다. 마법사가 실행될 때마다 새 소프트웨어 업데이트 그룹 및 배포가 생성됩니다. 하루에 여러 번 실행되는 소프트웨어 업데이트 동기화 일정을 사용하는 경우 계획 서비스 만들기 마법사에서 매일 소프트웨어 업데이트 그룹 및 배포를 여러 개 만듭니다.  

**해결 방법**: 서비스 계획을 만든 후 서비스 계획에 대한 속성을 열고 **평가 일정** 탭으로 이동한 다음, **일정에 따라 규칙 실행**을 선택하고 **사용자 지정**을 클릭하여 사용자 지정 일정을 만듭니다. 예를 들어 60일마다 실행하는 서비스 계획이 있을 수 있습니다.  



## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>지원되지 않는 언어를 포함하는 경우 구성 파일에서 Office 365 클라이언트 설정을 가져올 수 없음
<!-- 489258  Fixed in 1706  -->
*다음 문제는 1702 및 이전 버전에 적용됩니다.*   

기존 XML 구성 파일에서 Office 365 클라이언트 설정을 가져오는 경우 파일에 Office 365 ProPlus 클라이언트에서 지원되지 않는 언어가 포함될 경우 오류가 발생합니다. 자세한 내용은 [Office 365 클라이언트 관리 대시보드에서 클라이언트에 Office 365 앱 배포](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard)를 참조하세요.

**해결 방법**: XML 구성 파일에는 [Office 365 ProPlus 클라이언트에서 지원하는 언어](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx)만 사용하세요.  



## <a name="mobile-device-management"></a>모바일 장치 관리  

### <a name="beginning-with-version-1710-you-can-no-longer-deploy-windows-phone-81-vpn-profiles-to-windows-10------503274--should-be-fixed-by-1802-if-not-sooner---"></a>버전 1710부터는 Windows Phone 8.1 VPN 프로필을 Windows 10에 더 이상 배포할 수 없습니다. <!-- 503274  Should be fixed by 1802, if not sooner -->
1710에서는 Windows 10 장치에도 적용 가능한 Windows Phone 8.1 워크플로를 사용하여 VPN 프로필을 만들 수 없습니다. 이러한 프로필의 경우 만들기 마법사에 지원되는 플랫폼 페이지가 더 이상 표시되지 않습니다. 백 엔드에서 Windows Phone 8.1이 자동으로 선택됩니다. 지원되는 플랫폼 페이지는 프로필 속성에서 사용할 수 있지만 Windows 10 옵션이 표시되지 않습니다.

**해결 방법**: Windows 10 장치의 경우 Windows 10 VPN 프로필 워크플로를 사용합니다. 이 옵션이 환경에 적합하지 않은 경우 지원 서비스에 문의하세요. 지원 서비스를 통해 Windows 10 타기팅을 추가할 수 있습니다.


### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-of-memory"></a>전체 초기화 시 메모리가 4GB 미만인 Windows 10 장치를 사용할 수 없음
Windows 10 버전 1507을 실행하고 RAM이 4GB 미만인 장치에서 전체 초기화를 수행하면 장치를 사용하지 못하게 될 수 있습니다. 장치 초기화를 시도한 후 장치를 시작할 수 없으며 장치가 응답하지 않습니다.

**해결 방법**: 전체 초기화를 수행하기 전에 Windows 10 장치에서 4GB 이상의 메모리를 사용할 수 있는지 확인합니다. Windows 10 장치의 버전 번호를 보려면 명령 프롬프트에서 'winver'를 입력합니다. 장치가 이미 초기화되어 더 이상 응답하지 않는 경우 부팅 가능 Windows 10 USB 드라이브를 사용하여 장치를 복구합니다.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-to-which-you-deploy-a-terms-and-conditions-policy-the-user-sees-multiple-sets-of-the-same-terms"></a>사용 약관 정책이 배포된 둘 이상의 사용자 컬렉션에 속한 사용자에게 동일한 사용 약관의 여러 집합이 표시됨  
<!-- 454394    -->
사용 약관 집합을 여러 사용자 컬렉션에 배포하는 경우 이러한 컬렉션 중 둘 이상의 멤버인 사용자는 회사 포털에서 동일한 사용 약관의 여러 복사본을 보게 됩니다. 예:
- 이름이 “SampleUser”인 사용자는 두 가지 사용자 컬렉션 “CompanyEmployeesFTE” 및 “CompanyEmployeesNA”의 멤버입니다.
- “CompanyTerms” 사용 약관을 CompanyEmployeesFTE 및 CompanyEmployeesNA 둘 다에 배포합니다.
- SampleUser는 회사 포털의 사용 약관 동의 페이지에서 두 가지 동일한 CompanyTerms 집합을 보게 됩니다. 

사용자는 모든 사용 약관에 동의하거나 모두 거부할 수만 있습니다. 따라서 모호한 동의 상태가 발생할 위험이 없습니다. (모호한 상태는 사용자가 동일한 사용 약관에 동의 및 거부하는 경우입니다.) 사용 약관 동의 보고서에는 사용자별로 각 사용 약관 집합이 단일 행에 표시되므로 보고서에 오류가 나타나지 않습니다. 유일한 영향은 동의 페이지에서 두 개의 사용 약관 집합이 사용자에게 표시된다는 것입니다.  

**해결 방법**: 각 사용자가 사용 약관이 배포된 한 컬렉션에만 포함되어 있는지 확인합니다.  


<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->
<!-- ## Endpoint Protection -->
