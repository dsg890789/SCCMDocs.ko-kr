---
title: "Mac 클라이언트 배포 | Microsoft 문서"
description: "System Center Configuration Manager에서 Mac 컴퓨터에 클라이언트를 배포하는 방법을 알아봅니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: aaroncz
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
caps.latest.revision: 12
author: robstackmsft
ms.author: robstack
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1b9e49da1a5bbfca93fe683b82d2c0056a22cc1f
ms.openlocfilehash: 9cab5b91a94e8bf2ad96a8a706f46c58e2a3d712
ms.lasthandoff: 03/21/2017


---
# <a name="how-to-deploy-clients-to-macs"></a>How to deploy clients to Macs

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목에서는 Mac 컴퓨터에 Configuration Manager 클라이언트를 배포 및 유지 관리하는 방법을 설명합니다. 클라이언트를 Mac 컴퓨터에 배포하기 전에 구성해야 하는 내용을 알아보려면 [Mac에 클라이언트 소프트웨어 배포 준비](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients)를 참조하세요.

Mac 컴퓨터용 새 클라이언트를 설치할 때 Configuration Manager 콘솔에서 새 클라이언트 정보를 반영하려면 Configuration Manager 업데이트도 설치해야 할 수 있습니다.

이러한 절차에는 클라이언트 인증서를 설치할 수 있는 두 가지 옵션이 있습니다. [Mac에 클라이언트 소프트웨어 배포 준비](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#certificate-requirements)에서 Mac용 클라이언트 인증서에 대해 자세히 읽어보세요.  

-   [CMEnroll 도구](#install-the-client-and-then-enroll-the-client-certificate-on-the-mac)를 사용하여 Configuration Manager 등록을 사용합니다. 등록 프로세스는 자동 인증서 갱신을 지원하지 않으므로 설치된 인증서가 만료되기 전에 Mac 컴퓨터를 다시 등록해야 합니다.    

-   [Configuration Manager와 별개의 인증서 요청 및 설치 방법을 사용합니다](#use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager).  


## <a name="configure-client-settings-for-enrollment"></a>등록을 위한 클라이언트 설정 구성  
 Mac 컴퓨터에 대해 등록을 구성하려면 [기본 클라이언트 설정](../../../core/clients/deploy/about-client-settings.md)을 사용해야 합니다. 사용자 지정 클라이언트 설정은 사용할 수 없습니다.  

 Mac에서 인증서를 요청하고 설치하려면 Configuration Manager에서 이 작업을 수행해야 합니다.  

### <a name="to-configure-the-default-client-settings-for-configuration-manager-to-enroll-certificates-for-macs"></a>Configuration Manager의 기본 클라이언트 설정에서 Mac용 인증서를 등록하도록 구성하려면  

1.  Configuration Manager 콘솔에서 **관리** >  **클라이언트 설정** > **기본 클라이언트 설정**을 선택합니다.  

4.  **홈** 탭의 **속성** 그룹에서 **속성**을 선택합니다.  

5.  **등록** 섹션을 선택하고 다음 설정을 구성합니다.  

    1.  **사용자가 모바일 장치 및 Mac 컴퓨터를 등록할 수 있도록 허용: 예**  

    2.  **등록 프로필:** **프로필 설정**을 선택합니다.  

6.  **모바일 장치 등록 프로필** 대화 상자에서 **만들기**를 선택합니다.  

7.  **등록 프로필 만들기** 대화 상자에서 이 등록 프로필의 이름을 입력한 다음 **관리 사이트 코드**를 구성합니다. Mac 컴퓨터를 관리할 관리 지점이 포함된 Configuration Manager 기본 사이트를 선택합니다.  

    > [!NOTE]  
    >  이 사이트를 선택할 수 없는 경우 사이트에서 모바일 장치를 지원할 관리 지점을 하나 이상 구성했는지 확인합니다.  

8.  **추가**를 선택합니다.  

9. **모바일 장치에 대한 인증 기관 추가** 대화 상자에서 Mac 컴퓨터에 대한 인증서를 발급할 CA(인증 기관) 서버를 선택합니다.  

10. **등록 프로필 만들기** 대화 상자에서 3단계에서 만든 Mac 컴퓨터 인증서 템플릿을 선택합니다.  

11. **확인**을 클릭하여 **등록 프로필** 대화 상자, **기본 클라이언트 설정** 대화 상자를 차례로 닫습니다.  

    > [!TIP]  
    >  클라이언트 정책 간격을 변경하려면 **클라이언트 정책** 클라이언트 설정 그룹에서 **클라이언트 정책 폴링 간격**을 사용합니다.  

 모든 사용자는 다음에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [Configuration Manager 클라이언트에 대한 정책 검색 시작](../../../core/clients/manage/manage-clients.md#BKMK_PolicyRetrieval)을 참조하세요.  

 등록 클라이언트 설정 외에도 다음 클라이언트 장치 설정을 구성했는지 확인합니다.  

-   **하드웨어 인벤토리**: Mac 및 Windows 클라이언트 컴퓨터에서 하드웨어 인벤토리를 수집하려면 이 설정을 사용하도록 설정하고 구성합니다. 자세한 내용은 [System Center Configuration Manager에서 하드웨어 인벤토리를 확장하는 방법](../../../core/clients/manage/inventory/extend-hardware-inventory.md)을 참조하세요.  

-   **준수 설정**: Mac 및 Windows 클라이언트 컴퓨터에 대한 설정을 평가하고 수정하려면 이 설정을 사용하도록 설정하고 구성합니다. 자세한 내용은 [준수 설정 계획 및 구성](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)을 참조하세요.  

> [!NOTE]  
>  Configuration Manager 클라이언트 설정에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트 설정을 구성하는 방법](../../../core/clients/deploy/configure-client-settings.md)을 참조하세요.  

## <a name="download-the-client-source-files-for-macs"></a>Mac용 클라이언트 원본 파일 다운로드  

1.  Mac OS X 클라이언트 파일 패키지 **ConfigmgrMacClient.msi**를 다운로드하여 Windows를 실행하는 컴퓨터에 저장합니다.  

     이 파일은 Configuration Manager 설치 미디어에서 제공되지 않습니다. [Microsoft 다운로드 센터](http://go.microsoft.com/fwlink/?LinkID=525184)에서 다운로드할 수 있습니다.  

2.  Windows 컴퓨터에서 **ConfigmgrMacClient.msi**를 실행하여 Mac 클라이언트 패키지 Macclient.dmg를 로컬 디스크의 폴더(기본적으로 **C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client\\**)에 추출합니다.  

3.  Macclient.dmg 파일을 Mac 컴퓨터의 폴더에 복사합니다.  

4.  Mac 컴퓨터에서 Macclient.dmg 파일을 실행하여 로컬 디스크의 폴더에 추출합니다.  

5.  이 폴더에서 Ccmsetup and CMClient.pkg 파일이 추출되어 있고 CMDiagnostics, CMUninstall, CMAppUtil, CMEnroll 도구가 포함된 Tools 폴더가 만들어졌는지 확인합니다.

    -  **Ccmsetup**: Mac 컴퓨터에 Configuration Manager 클라이언트를 설치합니다.  

    -   **CMDiagnostics**: Mac 컴퓨터에 설치된 Configuration Manager 클라이언트와 관련된 진단 정보를 수집합니다.  

    -   **CMUninstall**: Mac 컴퓨터에서 클라이언트를 제거합니다.  

    -   **CMAppUtil**: Apple 응용 프로그램 패키지를 Configuration Manager 응용 프로그램으로 배포할 수 있는 형식으로 변환합니다.  

    -   **CMEnroll**: Configuration Manager 클라이언트를 설치할 수 있도록 Mac 컴퓨터에 대한 클라이언트 인증서를 요청하고 설치합니다.   

## <a name="install-the-client-and-then-enroll-the-client-certificate-on-the-mac"></a>Mac에 클라이언트를 설치한 다음 클라이언트 인증서 등록  

[Mac 컴퓨터 등록 마법사](#enroll-the-client-with-the-mac-computer-enrollment-wizard)를 사용하여 개별 클라이언트를 등록할 수 있습니다.

여러 클라이언트를 등록할 수 있도록 자동화하려면 [CMEnroll 도구](#client-and-certificate-automation-with-cmenroll)를 사용합니다.   


###  <a name="enroll-the-client-with-the-mac-computer-enrollment-wizard"></a>Mac 컴퓨터 등록 마법사를 사용하여 클라이언트 등록  

1.  클라이언트 설치를 마치면 컴퓨터 등록 마법사가 열립니다. 마법사가 열리지 않거나 마법사를 실수로 닫은 경우 **Configuration Manager** 기본 설정 페이지에서 **등록**을 클릭하여 마법사를 엽니다.  

2.  마법사의 두 번째 페이지에서 다음을 입력합니다.  

    -   **사용자 이름** - 사용자 이름은 다음 형식이 될 수 있습니다.  

        -   '도메인\이름'. 예를 들면 'contoso\mnorth'와 같습니다.  

        -   'user@domain'. 예: 'mnorth@contoso.com'  

            > [!IMPORTANT]  
            >  메일 주소를 사용하여 **사용자 이름** 필드를 채운 경우 Configuration Manager는 메일 주소의 도메인 이름과 등록 프록시 지점 서버의 기본 이름을 자동으로 사용하여 **서버 이름** 필드를 채웁니다. 이 도메인 이름과 서버 이름이 등록 프록시 지점 서버의 이름과 일치하지 않는 경우 Mac 컴퓨터를 등록할 때 사용할 올바른 이름을 사용자에게 알립니다.  

         사용자 이름과 해당 암호는 Mac 클라이언트 인증서 템플릿에 대한 읽기 및 등록 권한이 부여된 Active Directory 사용자 계정과 일치해야 합니다.  

    -   **암호** – 지정한 사용자 이름에 해당하는 암호를 입력합니다.  

    -   **서버 이름** – 등록 프록시 지점 서버의 이름을 입력합니다.  


### <a name="client-and-certificate-automation-with-cmenroll"></a>CMEnroll을 사용하여 클라이언트 및 인증서 자동화  

CMEnroll 도구를 사용하여 클라이언트 설치를 자동화하고 클라이언트 인증서를 요청 및 등록하려면 다음 절차를 따릅니다. 도구를 실행하려면 Active Directory 사용자 계정이 있어야 합니다.

1.  Mac 컴퓨터에서 Macclient.dmg 파일의 콘텐츠를 추출한 폴더로 이동합니다.  

2.  다음 명령줄을 입력합니다. **sudo ./ccmsetup**  

3.  **설치 완료** 메시지가 나타날 때까지 기다립니다. 설치 관리자에서 지금 다시 시작해야 한다는 메시지가 표시되더라도 다시 시작하지 않고 다음 단계를 계속합니다.  

4.  Mac 컴퓨터의 Tools 폴더에서 다음 명령을 입력합니다. **sudo ./CMEnroll -s &lt;enrollment_proxy_server_name> -ignorecertchainvalidation -u &lt;사용자 이름'>**  

    클라이언트를 설치한 후 Mac 컴퓨터 등록을 안내하는 Mac 컴퓨터 등록 마법사가 열립니다. 이 방법으로 클라이언트를 등록하려면 이 항목에서 [To enroll the client by using the Mac Computer Enrollment Wizard](#BKMK_EnrollR2) 섹션을 참조하세요.  

5. Active Directory 사용자 계정의 암호를 입력합니다.  이 명령을 입력하면 두 가지 암호를 묻는 메시지가 나타납니다. 첫 번째는 명령을 실행하기 위한 슈퍼 사용자 계정의 암호를 묻고, 두 번째는 Active Directory 사용자 계정의 암호를 묻습니다. 메시지가 동일하게 나타날 수 있으므로 올바른 순서로 암호를 지정해야 합니다.  

    사용자 이름은 다음 형식이 될 수 있습니다.  

    -   '도메인\이름'. 예를 들면 'contoso\mnorth'와 같습니다.  

    -   'user@domain'. 예: 'mnorth@contoso.com'  

     사용자 이름과 해당 암호는 Mac 클라이언트 인증서 템플릿에 대한 읽기 및 등록 권한이 부여된 Active Directory 사용자 계정과 일치해야 합니다.  

     예: 등록 프록시 지점 서버 이름이 **server02.contoso.com**이고 사용자 이름이 **contoso\mnorth**인 사용자에게 Mac 클라이언트 인증서 템플릿에 대한 권한이 부여된 경우 다음을 입력합니다. **sudo ./CMEnroll -s server02.contoso.com -ignorecertchainvalidation -u 'contoso\mnorth'**  

    > [!NOTE]  
    >  사용자 이름에 **&lt;>"+=,** 중 하나가 포함된 경우 등록에 실패합니다. 이러한 문자가 포함되지 않은 사용자 이름으로 대역 외 인증서를 가져옵니다.  
    >  
    >  보다 원활한 사용자 경험을 위해 설치 단계와 명령을 스크립팅하여 사용자가 사용자 이름과 암호만 입력하면 되도록 할 수 있습니다.  

5.  **등록 성공** 메시지가 나타날 때까지 기다립니다.  

6.  등록된 인증서를 Configuration Manager로 제한하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    a.  **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**명령을 입력합니다.  

    b.  **키 집합 접근** 대화 상자의 **키 집합** 섹션에서 **시스템**을 선택한 다음 **카테고리** 섹션에서 **키**를 선택합니다.  

    c.  클라이언트 인증서를 보려면 해당 키를 확장합니다. 방금 설치한 인증서를 개인 키로 식별한 경우 키를 두 번 클릭합니다.  

    d.  **Access Control**(액세스 제어) 탭에서 **접근 허용 전 확인**을 선택합니다.  

    e.  **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 선택합니다.  

    f.  **변경사항 저장**을 선택하고 **키 집합 접근** 대화 상자를 닫습니다.  

7.  Mac 컴퓨터를 다시 시작합니다.  

 Mac 컴퓨터에서, **시스템 환경설정** 에서 **Configuration Manager**를 열어 설치가 성공했는지 확인합니다. 또한 **모든 시스템** 컬렉션을 업데이트하고 확인하여 이제 Mac 컴퓨터가 이 컬렉션에 관리되는 클라이언트로 나타나는지 확인합니다.  

> [!TIP]  
>  Mac 클라이언트에 대한 문제를 해결하려는 경우 Mac OS X 클라이언트 패키지에 포함된 CMDiagnostics 프로그램을 사용하여 다음 진단 정보를 수집할 수 있습니다.  
>   
>  -   실행 중인 프로세스 목록  
> -   Mac OS X 운영 체제 버전  
> -   **CCM\*.crash** 및 **System Preference.crash**를 비롯한 Configuration Manager 클라이언트와 관련된 Mac OS X 충돌 보고서  
> -   Configuration Manager 클라이언트 설치를 통해 생성된 BOM(제품 구성 정보) 파일 및 속성 목록(.plist) 파일  
> -   라이브러리/응용 프로그램 지원/Microsoft/CCM/Logs 폴더의 내용  
>   
>  CmDiagnostics를 통해 수집되는 정보는 이름이 cmdiag-*<호스트 이름\>***-***&gt;날짜 및 시간\>*.zip인 압축 파일에 추가되어 컴퓨터 바탕 화면에 저장됩니다.***


##  <a name="use-a-certificate-request-and-installation-method-that-is-independent-from-configuration-manager"></a>Configuration Manager와 별개의 인증서 요청 및 설치 방법 사용  

먼저 [Mac에 클라이언트 소프트웨어 배포 준비](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients)에서 다음과 같은 특정 작업을 수행합니다.

1. [사이트 시스템 서버에 웹 서버 인증서 배포](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-web-server-certificate-to-site-system-servers)

2. [사이트 시스템 서버에 클라이언트 인증 인증서 배포](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#deploy-a-client-authentication-certificate-to-site-system-servers)

3. [관리 지점 및 배포 지점 구성](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#configure-the-management-point-and-distribution-point)

4. [선택 사항: 보고 서비스 지점 설치](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#install-the-reporting-services-point)

그러고 나서 다음 작업을 수행합니다.

5. [Mac용 클라이언트 원본 파일 다운로드](#download-the-client-source-files-for-macs)  
6. 선택한 인증서 배포 방법에 따른 지침을 사용하여 Mac 컴퓨터에서 클라이언트 인증서를 요청하고 설치합니다.  
7.  Microsoft 다운로드 센터에서 다운로드한 macclient.dmg 파일의 콘텐츠를 추출한 폴더를 찾습니다.  

3.  **sudo ./ccmsetup -MP <관리 지점 인터넷 FQDN\> -SubjectName <인증서 주체 값\>** 명령줄을 입력합니다.  인증서 주체 값은 대소문자를 구분하므로 인증서 세부 정보에 나타난 대로 정확히 입력합니다.  

     예: 사이트 시스템 속성의 인터넷 FQDN이 **server03.contoso.com**이고 Mac 클라이언트 인증서가 **mac12.contoso.com**의 FQDN을 인증서 주체의 일반 이름으로 사용하는 경우 다음을 입력합니다. **sudo ./ccmsetup -MP server03.contoso.com -SubjectName mac12.contoso.com**  

4.  **설치 완료** 메시지가 나타날 때까지 기다렸다가 Mac 컴퓨터를 다시 시작합니다.  

5.  이 인증서를 Configuration Manager에서 액세스할 수 있도록 하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    a.  **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**명령을 입력합니다.  

    b.  **키 집합 접근** 대화 상자의 **키 집합** 섹션에서 **시스템**을 선택한 다음 **카테고리** 섹션에서 **키**를 선택합니다.  

    c.  클라이언트 인증서를 보려면 해당 키를 확장합니다. 방금 설치한 인증서를 개인 키로 식별한 경우 키를 두 번 클릭합니다.  

    d.  **Access Control**(액세스 제어) 탭에서 **접근 허용 전 확인**을 선택합니다.  

    e.  **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 선택합니다.  

    f.  **변경사항 저장**을 선택하고 **키 집합 접근** 대화 상자를 닫습니다.  

6.  동일한 주체 값을 포함하는 인증서가 둘 이상 있는 경우 Configuration Manager 클라이언트에 사용하려는 인증서를 식별할 수 있도록 인증서 일련 번호를 지정해야 합니다. 이 작업을 수행하려면 다음 명령을 사용합니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "<일련 번호\>"**.  

     예를 들면 다음과 같습니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

 Mac의 **시스템 환경설정**에서 **Configuration Manager**를 열어 클라이언트가 설치되었는지 확인합니다. 또한 **모든 시스템** 컬렉션을 업데이트하고 표시하여 Mac이 이 컬렉션에 관리되는 클라이언트로 나타나는지 확인합니다.  

## <a name="renewing-the-mac-client-certificate"></a>Mac 클라이언트 인증서 갱신  
 Mac 컴퓨터에서 컴퓨터 인증서를 갱신하기 전에 다음 단계를 따르세요.  

 이 절차는 클라이언트에서 Mac 컴퓨터에 대한 새 인증서 또는 갱신된 인증서를 사용하는 데 필요한 SMSID를 제거합니다.  

> [!IMPORTANT]  
>  SMSID를 제거하고 대체할 경우 Configuration Manager 콘솔에서 클라이언트를 삭제한 후에 인벤토리와 같은 저장된 클라이언트 기록이 삭제됩니다.  

### <a name="to-renew-the-mac-client-certificate"></a>Mac 클라이언트 인증서를 갱신하려면  

1.  컴퓨터 인증서를 갱신해야 하는 Mac 컴퓨터에 대한 장치 컬렉션을 만들고 채웁니다.  

2.  **자산 및 호환성** 작업 영역에서 **구성 항목 만들기 마법사**를 시작합니다.  

3.  마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **유형:Mac OS X**  

4.  마법사의 **지원되는 플랫폼** 페이지에서 모든 Mac OS X 버전이 선택되어 있는지 확인합니다.  

5.  마법사의 **설정** 페이지에서 **새로 만들기** 를 클릭하고 **설정 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **설정 유형:스크립트**  

    -   **데이터 형식:문자열**  

6.  **설정 만들기** 대화 상자의 **검색 스크립트**에 대해 **스크립트 추가** 를 클릭하여 SMSID가 구성된 Mac 컴퓨터를 검색하는 스크립트를 지정합니다.  

7.  **검색 스크립트 편집** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8.  **확인**을 선택하여 **검색 스크립트 편집** 대화 상자를 닫습니다.  

9. **설정 만들기** 대화 상자의 **재구성 스크립트(옵션)**에 대해 **스크립트 추가**를 선택하여 Mac 컴퓨터에서 발견된 SMSID를 제거하는 스크립트를 지정합니다.  

10. **재구성 스크립트 만들기** 대화 상자에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. **확인**을 선택하여 **재구성 스크립트 만들기** 대화 상자를 닫습니다.  

12. 마법사의 **호환성 규칙** 페이지에서 **새로 만들기**를 선택하고 **규칙 만들기** 대화 상자에서 다음 정보를 지정합니다.  

    -   **이름:Mac용 SMSID 제거**  

    -   **선택한 설정:** **찾아보기**를 선택하고 이전에 지정한 검색 스크립트를 선택합니다.  

    -   **다음 값** 필드에 **The domain/default pair of (com.microsoft.ccmclient, SMSID) does not exist**를 입력합니다.  

    -   **이 설정이 규칙과 호환되지 않는 경우 지정한 재구성 스크립트 실행**옵션을 사용하도록 설정합니다.  

13. 구성 항목 만들기 마법사를 완료합니다.  

14. 방금 만든 구성 항목을 포함하는 구성 기준을 만들고 이를 1단계에서 만든 장치 컬렉션에 배포합니다.  

     구성 기준을 만들고 배포하는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 구성 기준을 만드는 방법](../../../compliance/deploy-use/create-configuration-baselines.md)을 참조하세요.  

15. SMSID가 제거된 Mac 컴퓨터에 새 인증서를 설치한 후 다음 명령을 실행하여 새 인증서를 사용하도록 클라이언트를 구성합니다.  

    ```  
    sudo defaults write com.microsoft.ccmclient SubjectName -string <Subject_Name_of_New_Certificate>  
    ```  

16. 동일한 주체 값을 포함하는 인증서가 둘 이상 있는 경우에는 Configuration Manager 클라이언트에 사용하려는 인증서를 식별할 수 있도록 인증서 일련 번호를 지정해야 합니다. 이 작업을 수행하려면 다음 명령을 사용합니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "<일련 번호\>"**.  

     예를 들면 다음과 같습니다. **sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"**  

17. 다시 시작.  


### <a name="see-also"></a>참고 항목

[Mac 클라이언트 유지 관리](/sccm/core/clients/manage/maintain-mac-clients)

