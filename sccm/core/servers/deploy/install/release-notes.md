---
title: "릴리스 정보 - Configuration Manager | Microsoft 문서"
description: "Microsoft 기술 자료 문서에서 다루지 않거나 제품에서 아직 해결되지 않은 긴급한 문제에 대해서는 이 정보를 참조하세요."
ms.custom: na
ms.date: 08/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: "41"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: e54c2cd1c3e83609bff6a8cb64fb3c23b26a4eaa
ms.sourcegitcommit: 974fbc4408028c8be28911e5cd646efcf47c7f15
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/28/2017
---
# <a name="release-notes-for-system-center-configuration-manager"></a>System Center Configuration Manager의 릴리스 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 제품에서 수정되지 않은 긴급한 문제(콘솔 내 업데이트를 통해 사용 가능) 또는 Microsoft 기술 자료 문서에 자세히 설명되지 않은 긴급한 문제로 제품 릴리스 정보가 제한됩니다.  

핵심 시나리오에 영향을 주는 알려진 문제에 대한 내용은 System Center Configuration Manager 설명서 라이브러리의 온라인 제품 설명서에서 제공됩니다.  

> [!TIP]  
>  이 항목에는 System Center Configuration Manager의 현재 분기에 대한 릴리스 정보가 포함되어 있습니다. System Center Configuration Manager의 Technical Preview의 경우 [System Center Configuration Manager용 Technical Preview](../../../../core/get-started/technical-preview.md)를 참조하세요.  

다른 버전에서 도입된 새 기능에 대한 자세한 내용은 다음을 참조하세요.
- [버전 1706의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1706)  
- [버전 1702의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1702)
- [버전 1610의 새로운 기능](/sccm/core/plan-design/changes/whats-new-in-version-1610)
   


## <a name="setup-and-upgrade"></a>설치 및 업그레이드  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>사이트 서버 폴더에서 ConsoleSetup.exe를 사용하여 Configuration Manager 콘솔을 업데이트한 후 최근 언어 팩 변경 내용을 사용할 수 없습니다.
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
*다음은 버전 1610 및 1702에 적용됩니다.*   
사이트 서버 설치 폴더에서 ConsoleSetup.exe를 사용하여 콘솔에 대한 현재 위치 업데이트를 실행한 후 최근에 설치한 언어 팩을 사용할 수 없습니다. 이 문제는 다음과 같은 경우에 발생합니다.
- 사이트에서 버전 1610 또는 1702를 실행합니다.
- 사이트 서버 설치 폴더에서 ConsoleSetup.exe를 사용하여 콘솔을 현재 위치 업데이트합니다.

이 문제가 발생하면 다시 설치된 콘솔이 구성되어 있는 최신 언어 팩 집합을 사용하지 않습니다. 오류가 반환되지 않지만 콘솔에 사용할 수 있는 언어 팩이 변경되지 않습니다.  

**해결 방법:** 현재 콘솔을 제거하고 콘솔을 새 설치로 다시 설치합니다. 사이트 서버 설치 폴더에서 ConsoleSetup.exe를 사용할 수 있습니다. 설치하는 동안 사용할 언어 팩 파일을 선택해야 합니다.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>버전 1702에서는 사이트 할당에 사용할 기본 사이트 경계 그룹이 구성됩니다.
<!--  SMS 486380   Applicability should only be to 1702. -->
*다음은 버전 1702에 적용됩니다.*  
기본 사이트 경계 그룹의 [참조] 탭에서는 **사이트 할당에 대해 이 경계 그룹 사용**에 대한 확인 표시가 있고, 사이트가 **할당된 사이트**로 나열되며, 구성을 편집하거나 제거할 수 없도록 회색으로 표시되어 있습니다.

**해결 방법:** 없음 이 설정을 무시할 수 있습니다. 사이트 할당에 그룹이 사용되더라도 기본 사이트 경계 그룹은 사이트 할당에 사용되지 않습니다. 1702에서 이 구성을 적용하면 기본 사이트 경계 그룹이 올바른 사이트와 연결됩니다.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>버전 1606을 사용하여 장기 서비스 분기 사이트를 설치하는 경우 현재 분기 사이트가 설치됨
<!-- Consider move to core content  -->
2016년 10월 릴리스의 버전 1606 기준 미디어를 사용하여 LTSB(장기 서비스 분기) 사이트를 설치하는 경우 현재 분기 사이트가 대신 설치됩니다. 이 문제는 사이트 설치를 사용하여 서비스 연결 지점을 설치하는 옵션을 선택하지 않았기 때문에 발생합니다.

 - 서비스 연결 지점이 필요하지 않더라도 LTSB 사이트를 설치하려면 설치 중에 선택해야 합니다.

설치가 완료된 후 서비스 연결 지점을 제거할 수 있습니다.  그러나 원격 분석 데이터를 제출하고 현재 분기 및 LTSB 사이트 둘 다에 대한 보안 업데이트를 가져오려면 오프라인 또는 온라인 모드의 서비스 연결 지점이 있어야 합니다.

사이트가 현재 분기 사이트로 설치되었지만 LTSB를 설치하려는 경우 사이트를 제거한 후 다시 설치할 수 있습니다. 또는 [Microsoft 도움말 및 지원](http://go.microsoft.com/fwlink/?LinkId=243064)에 도움을 요청할 수 있습니다.  

설치된 분기를 확인하려면 콘솔의 **관리** > **사이트 구성** > **사이트**에서 **계층 설정**을 엽니다. 사이트를 현재 분기 사이트로 변환하는 옵션은 사이트에서 LTSB를 실행하는 경우에만 사용할 수 있습니다.  

**해결 방법:**  없습니다.   


### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Configuration Manager 콘솔의 업데이트 및 서비스 노드에서 업데이트가 다운로드 중 상태로 고정됩니다.  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
온라인 서비스 연결 지점을 통해 업데이트를 자동으로 다운로드하는 동안 업데이트가 다운로드 중 상태로 고정될 수 있습니다. 업데이트의 다운로드가 고정되면 걸려 표시된 로그 파일에 다음과 유사한 항목이 표시됩니다.  

DMPdownloader 로그:  

-   ERROR: Failed to download redist for 037cd17e-4d7b-40e1-802b-14bb682364c7 with command  /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 /RedistVersion 112015 /NoUI  "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Error: failed to verify 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi' authenticode signature.  

-   Error: file signature check failed for 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi  

**해결 방법**: 사이트 서버에서 다음 레지스트리 키를 다음과 일치하도록 수정한 후 SMS_Executive 서비스를 다시 시작하거나 다음 자동 다운로드 주기를 위해 최대 24시간 동안 대기합니다.  

-   **편집할 키**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software Publishing  

-   **상태 값**: **146944** 10진수 또는 **0x00023e00** 16진수로 설정  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>CD.Latest 폴더에서 재배포 파일을 사용하는 경우 매니페스트 확인 오류와 함께 설치가 실패합니다.
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

1606 버전에 대해 만든 CD.Latest 폴더에서 설치 프로그램을 실행하고 그 CD.Latest 폴더에 포함된 재배포 파일을 사용하는 경우 Configuration Manager 설치 로그에서 다음 오류와 함께 설치가 실패합니다.

  - 오류: defaultcategories.dll에 대해 파일 해시를 확인하지 못했습니다.
  - 오류: 매니페스트를 확인하지 못했습니다. 잘못된 매니페스트 버전인가요?

**해결 방법:** 다음 방법 중 하나를 사용합니다.
 - 설치 시 CD.Latest 폴더에 포함된 재배포 파일을 사용하는 대신 Microsoft에서 최신 재배포 파일을 다운로드하도록 선택합니다.
 - 수동으로 *cd.latest\redist\languagepack\zhh* 폴더를 삭제한 다음 설치 프로그램을 다시 실행합니다.


### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>SQL Server가 원격이거나 공유 메모리가 사용되지 않는 경우 서비스 연결 도구에서 예외가 발생합니다.
<!-- 479223   Fixed in 1702 and later   -->
*다음은 1610 및 이전 버전에 적용됩니다.*  
다음 중 하나에 해당하는 경우 서비스 연결 도구에서 예외를 생성합니다.  
 -  사이트 데이터베이스가 서비스 연결 지점을 호스트하고 비표준 포트(1433 이외의 포트)를 사용하는 컴퓨터에서 원격인 경우
 -  사이트 데이터베이스가 서비스 연결 지점과 동일한 서버에 있지만 SQL 프로토콜 **공유 메모리**가 사용되지 않는 경우

예외는 다음과 유사합니다.
 - *처리되지 않은 예외: System.Data.SqlClient.SqlException: SQL Server에 대한 연결을 설정하는 동안 네트워크 관련 또는 인스턴스 관련 오류가 발생했습니다. 서버를 찾을 수 없거나 액세스할 수 없습니다. 인스턴스 이름이 올바르고 SQL Server가 원격 연결을 허용하도록 구성되었는지 확인합니다. (공급자: 명명된 파이프 공급자, 오류: 40 - SQL Server에 대한 연결을 열 수 없음) -* 

**해결 방법**: 도구를 사용하는 동안 SQL Server 포트에 대한 정보를 포함하도록 서비스 연결 지점을 호스트하는 서버의 레지스트리를 수정해야 합니다.

   1.   도구를 사용하기 전에 다음 레지스트리 키를 편집하고 사용 중인 포트 번호를 SQL Server의 이름에 추가합니다.
    - 키: HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - 값: &lt;SQL Server 이름>
    - 추가: **,&lt;포트>**

    예를 들어 *testserver.test.net*이라는 서버에 *15001* 포트를 추가하려는 경우 결과로 생성되는 키는 ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.net,15001***입니다.

   2.   레지스트리에 포트를 추가하면 도구기 정상적으로 작동합니다.  

   3.   도구 사용이 완료되면 **-connect** 및 **-import** 단계 둘 다에서 레지스트리 키를 원래 값으로 다시 변경합니다.  


<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>클라이언트 배포 및 업그레이드  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>오류 코드 0x8007064c를 나타내며 클라이언트 설치가 실패합니다.
<!--- SMS 486973  applies 1606 to 1706. Not yet fixed. -->
*다음은 Configuration Manager의 모든 활성 버전에 적용됩니다.*   
Windows 컴퓨터에 클라이언트를 배포할 때 모든 활성 버전에서 설치가 실패합니다. ccmsetup.log 파일에는 "파일 'C:\WINDOWS\ccmsetup\Silverlight.exe'가 실패 종료 코드 1612를 반환했습니다. 설치가 실패합니다.”와 “InstallFromManifest가 0x8007064c를 나타내며 실패했습니다.” 항목이 포함됩니다.

**해결 방법** 이 문제는 이전에 설치된 Silverlight 버전이 손상되었기 때문에 발생합니다. 이 문제를 해결하려면 영향을 받는 컴퓨터에서 다음 도구를 실행할 수 있습니다. [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed)

## <a name="operating-system-deployment"></a>운영 체제 배포  

### <a name="if-the-boot-image-contains-drivers-the-image-fails-to-reload-the-current-windows-pe-version-from-the-windows-assessment-and-deployment-kit-adk"></a>부팅 이미지가 드라이버를 포함하는 경우 이미지는 ADK(Windows Assessment and Deployment Kit)에서 현재 Windows PE 버전을 다시 로드하는 데 실패합니다.
<!-- 495087 -->
ADK(Windows Assessment and Deployment Kit)의 설치 디렉터리에서 최신 버전의 Windows PE를 사용하여 부팅 이미지가 저장된 배포 지점을 업데이트하기 위해 배포 지점 업데이트 마법사를 사용할 수 있습니다. 업데이트하려면 배포 지점 업데이트 마법사를 열고 **Windows ADK의 현재 PE 버전에서 이 부팅 이미지 다시 로드**를 선택합니다.

그러나 부팅 이미지에 드라이버가 있으면 업데이트에 실패합니다. 대신, 마법사는 ADK에서 이미지를 다시 로드하고, 사용자가 해제할 수 있는 예외 대화 상자를 표시한 후에 성공 화면을 보여줍니다. 그러나 최신 Configuration Manager 클라이언트 구성 요소가 부팅 이미지에 추가되지 않습니다. 부팅 이미지는 배포 지점에서 업데이트되지 않습니다.

**해결 방법**: 배포 지점 업데이트 마법사를 두 번 실행합니다.

1. **Windows ADK의 현재 Windows PE 버전에서 이 부팅 이미지 다시 로드**를 선택하여 마법사를 실행합니다. 최신 버전의 Windows PE를 설치할 수 있습니다.
2. **Windows ADK의 현재 Windows PE 버전에서 이 부팅 이미지 다시 로드**를 선택하지 않고 마법사를 다시 실행합니다. 그러면 최신 클라이언트 이진 파일을 가져오고 배포 지점에서 붐 이미지를 업데이트합니다.

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>서비스 계획에서 기본적으로 중복 소프트웨어 업데이트 그룹을 많이 만들고 배포합니다.  
기본적으로 서비스 계획 만들기 마법사는 현재 소프트웨어 업데이트를 동기화한 후마다 실행됩니다. 마법사가 실행될 때마다 새 소프트웨어 업데이트 그룹 및 배포가 생성됩니다. 예를 들어 하루에 여러 번 실행되는 소프트웨어 업데이트 동기화 일정을 사용하는 경우 계획 서비스 만들기 마법사에서 매일 거의 동일한 소프트웨어 업데이트 그룹 및 배포를 여러 개 만듭니다.  

**해결 방법**:    
서비스 계획을 만든 후 서비스 계획에 대한 속성을 열고, **평가 일정** 탭으로 이동하고, **일정에 따라 규칙 실행**을 선택하고, **사용자 지정**을 클릭하여 사용자 지정 일정을 만듭니다. 예를 들어 60일마다 실행하는 서비스 계획이 있을 수 있습니다.  


### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>높은 위험 수준 배포 대화 상자가 사용자에게 표시될 경우 마감일이 더 가까운 후속 높은 위험 수준 대화 상자가 표시되지 않음
<!-- Fixed in 1702 and later -->
*다음은 1610 및 이전 버전에 적용됩니다.*   
높은 위험 수준 작업 배포를 만들고 사용자에게 배포한 후 높은 위험 수준 대화 상자가 사용자에게 표시됩니다. 사용자가 대화 상자를 닫지 않고 첫 번째보다 마감일이 더 가까운 또 다른 높은 위험 수준 배포를 만들고 배포하면 사용자는 원래 대화 상자를 닫을 때까지 업데이트된 대화 상자를 받을 수 없습니다. 배포는 구성된 마감일에 계속 실행됩니다.

**해결 방법**:  
사용자가 첫 번째 높은 위험 수준 배포 대화 상자를 닫아야 다음 높은 위험 수준 배포 대화 상자를 볼 수 있습니다.



## <a name="software-updates"></a>소프트웨어 업데이트

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>지원되지 않는 언어를 포함하는 경우 구성 파일에서 Office 365 클라이언트 설정을 가져올 수 없음
<!-- 489258  Fixed in 1706  -->
*다음은 1702 및 이전 버전에 적용됩니다.*   
기존 XML 구성 파일에서 Office 365 클라이언트 설정을 가져오는 경우 파일에 Office 365 ProPlus 클라이언트에서 지원되지 않는 언어가 포함될 경우 오류가 발생합니다. 자세한 내용은 [Office 365 클라이언트 관리 대시보드에서 클라이언트에 Office 365 앱 배포](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard)를 참조하세요.

**해결 방법**:    
XML 구성 파일에는 [Office 365 ProPlus 클라이언트에서 지원하는 언어](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx)만 사용하세요.  



## <a name="mobile-device-management"></a>모바일 장치 관리  

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>전체 초기화를 진행하면 RAM이 4GB 미만인 Windows 10 장치를 사용하지 못하게 됩니다.
RAM이 4GB 미만인 Windows 10 RTM 장치(버전 1511보다 이전 버전)에 전체 초기화를 진행하면 장치가 사용할 수 없는 상태가 됩니다. 장치 초기화를 시도하면 장치는 시작 불능 상태가 되어 응답이 불가능합니다.

**해결 방법**: Windows 10 RTM PC에 전체 초기화를 진행하기 전에 장치의 가용 RAM이 4GB 이상인지 확인하세요. Windows 10 장치의 버전 번호를 보려면 명령 프롬프트에서 'winver'를 입력합니다. 장치가 이미 초기화되어 이제 응답하지 않는 경우 부팅 가능 Windows 10 USB 드라이브를 사용하여 장치에 대한 액세스를 시작하여 복구합니다.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>계약조건 정책이 배포된 둘 이상의 사용자 컬렉션에 속한 사용자에게 동일한 사용 약관의 여러 집합이 표시됩니다.  
<!-- 454394    -->
관리자가 여러 사용자 컬렉션에 사용 약관 집합을 배포하며 사용자가 이러한 컬렉션 중 둘 이상의 멤버인 경우 회사 포털을 열 때 해당 사용자에게 동일한 사용 약관의 여러 복사본이 표시됩니다.  예를 들어 "SampleUser"라는 사용자가 "CompanyEmployeesFTE"와 "CompanyEmployeesNA"라는 두 개의 서로 다른 사용자 컬렉션의 멤버이고, "CompanyTerms"라는 계약조건이 CompanyEmployeesFTE와 CompanyEmployeesNA 모두에 배포된 경우 사용 약관 동의 페이지에서 CompanyTerms의 동일한 집합 두 개가 SampleUser에게 표시됩니다. 사용자는 모든 사용 약관을 수락하거나 거절할 수만 있으므로 사용자가 사용 약관을 수락도 하고 거절도 하게 되는 모호한 동의 상태가 될 위험은 없습니다. 사용 약관 동의 보고서에는 사용자의 각 약관이 단일 행에 표시되므로 보고서에 오류가 나타나지 않습니다. 유일한 영향은 동의 페이지에서 두 개의 사용 약관 집합이 사용자에게 표시된다는 것입니다.  

**해결 방법**: 각 사용자가 사용 약관이 배포된 한 컬렉션에만 포함되어 있는지 확인합니다.  


### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>인증서 인증을 사용하는 Android for Work 메일 프로필은 장치에 적용되지 않습니다.
<!--  487657      -->
Android for Work 메일 프로필을 만들 때 두 가지 인증 옵션을 사용할 수 있습니다. 하나는 사용자 이름과 암호이고 다른 하나는 인증서입니다. 현재 인증서 옵션은 작동하지 않습니다. 인증 방법이 **인증서**로 설정된 프로필이 작성되면 프로필이 장치에 적용되지 않고 수동으로 메일 계정 세부 정보를 입력하라는 메시지가 표시됩니다.

**해결 방법**: 없음 관리자는 **사용자 이름 및 암호** 옵션을 사용하거나 이 문제가 해결될 때까지 기다려야 합니다.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->


## <a name="endpoint-protection"></a>Endpoint Protection

### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Windows Server 2016 Core에서 맬웨어 방지 정책 적용 실패
<!--  Product Studio bug 485370 added 04 19 2017   Fixed in 1702 -->
*다음은 1610 및 이전 버전에 적용됩니다.*  
Windows Server 2016 Core에서 맬웨어 방지 정책을 적용하는 데 실패합니다.  오류 코드는 0x80070002입니다.  ConfigSecurityPolicy.exe에 대한 종속성이 누락되어 있습니다.

**해결 방법:** 이 문제는 2017년 5월 9일에 발표된 [기술 자료 문서 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472)를 통해 해결됩니다.


### <a name="windows-defender-advanced-threat-protection-policies-fail-on-older-client-agents"></a>Windows Defender Advanced Threat Protection 정책이 이전 클라이언트 에이전트에서 실패함
<!-- Product Studio bug 462286 added  05 25 2017 and valid until July 2017 GA release      Fixed in 1610 -->
Configuration Manager 버전 1610 이상의 사이트 서버에서 만든 Windows Defender Advanced Threat Protection 정책이 Configuration Manager 버전 1606 및 이전 버전의 클라이언트에 적용되지 않습니다.  클라이언트는 온보딩되지 않고 정책 평가 시 오류가 보고됩니다. Windows Defender Advanced Threat Protection 구성의 **배포 상태**에 **오류**가 표시됩니다.

**해결 방법**: Configuration Manager 클라이언트를 버전 1610 이상으로 업그레이드합니다.
