---
title: Mac 클라이언트 배포
titleSuffix: Configuration Manager
description: Configuration Manager에서 클라이언트를 Mac 컴퓨터에 배포하는 방법을 알아봅니다.
ms.date: 12/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e46ad501-5d73-44ac-92de-0de14ef72b83
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e686f9cdbece2ceb652ecd2e0f3c6d5eca420caf
ms.sourcegitcommit: f9654cd1a3af6d67de52fedaccceb2e22dafc159
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67677830"
---
# <a name="how-to-deploy-clients-to-macs"></a>Mac에 클라이언트를 배포하는 방

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager 클라이언트를 Mac 컴퓨터에 배포 및 유지 관리하는 방법에 대해 설명합니다. 클라이언트를 Mac 컴퓨터에 배포하기 전에 구성해야 하는 내용을 알아보려면 [Mac에 클라이언트 소프트웨어 배포 준비](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients)를 참조하세요.

Mac 컴퓨터용 새 클라이언트를 설치할 때 Configuration Manager 콘솔에서 새 클라이언트 정보를 반영하려면 Configuration Manager 업데이트도 설치해야 할 수 있습니다.

이러한 절차에는 클라이언트 인증서를 설치할 수 있는 두 가지 옵션이 있습니다. [Mac에 클라이언트 소프트웨어 배포 준비](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients#certificate-requirements)에서 Mac용 클라이언트 인증서에 대해 자세히 읽어보세요.  

- [CMEnroll 도구](#bkmk_enroll)를 사용하여 Configuration Manager 등록을 사용합니다. 등록 프로세스는 자동 인증서 갱신을 지원하지 않습니다. 설치된 인증서가 만료되기 전에 Mac 컴퓨터를 다시 등록합니다.    

- [Configuration Manager와 별개의 인증서 요청 및 설치 방법을 사용합니다](#bkmk_external).  

> [!IMPORTANT]  
> macOS Sierra를 실행하는 디바이스에 클라이언트를 배포하려면 관리 지점 인증서의 **주체 이름**을 올바르게 구성합니다. 예를 들어 관리 지점 서버의 FQDN을 사용합니다.



## <a name="configure-client-settings"></a>클라이언트 설정 구성  

Mac 컴퓨터에 대한 등록을 구성하려면 [기본 클라이언트 설정](/sccm/core/clients/deploy/about-client-settings)을 사용합니다. 사용자 지정 클라이언트 설정은 사용할 수 없습니다. 인증서를 요청하고 설치하려면 Mac용 Configuration Manager 클라이언트에 기본 클라이언트 설정이 필요합니다.  

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동합니다. **클라이언트 설정** 노드를 선택한 다음, **기본 클라이언트 설정**을 선택합니다.  

2. 리본의 **홈** 탭에 있는 **속성** 그룹에서 **속성**을 선택합니다.  

3. **등록** 섹션을 선택하고, 다음 설정을 구성합니다.  

    1. **사용자가 모바일 디바이스 및 Mac 컴퓨터를 등록할 수 있도록 허용**: **예**  

    2. **등록 프로필:** **프로필 설정**을 선택합니다.  

4. **모바일 디바이스 등록 프로필** 대화 상자에서 **만들기**를 선택합니다.  

5. **등록 프로필 만들기** 대화 상자에서 이 등록 프로필에 대한 이름을 입력합니다. 그런 다음, **관리 사이트 코드**를 구성합니다. 이러한 Mac 컴퓨터에 대한 관리 지점이 포함된 Configuration Manager 주 사이트를 선택합니다.  

    > [!NOTE]  
    >  사이트를 선택할 수 없는 경우 사이트에서 모바일 디바이스를 지원할 관리 지점을 하나 이상 구성해야 합니다.  

6. **추가**를 선택합니다.  

7. **모바일 디바이스에 대한 인증 기관 추가** 창에서 Mac 컴퓨터에 인증서를 발급하는 인증 기관 서버를 선택합니다.  

8. **등록 프로필 만들기** 대화 상자에서 이전에 만든 Mac 컴퓨터 인증서 템플릿을 선택합니다.  

9. **확인**을 선택하여 **등록 프로필** 대화 상자를 닫은 다음, **기본 클라이언트 설정** 대화 상자를 닫습니다.  

    > [!TIP]  
    > 클라이언트 정책 간격을 변경하려면 **클라이언트 정책** 클라이언트 설정 그룹에서 **클라이언트 정책 폴링 간격**을 사용합니다.  

다음에 디바이스에서 클라이언트 정책을 다운로드하면 Configuration Manager에서 모든 사용자에 대해 이러한 설정을 적용합니다. 단일 클라이언트에 대한 정책 검색을 시작하려면 [Configuration Manager 클라이언트에 대한 정책 검색 시작](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.  

등록 클라이언트 설정 외에도 다음 클라이언트 디바이스 설정을 구성했는지 확인합니다.  

- **하드웨어 인벤토리**: Mac 및 Windows 클라이언트 컴퓨터에서 하드웨어 인벤토리를 수집하려면 이 기능을 사용하도록 설정하고 구성합니다. 자세한 내용은 [하드웨어 인벤토리를 확장하는 방법](/sccm/core/clients/manage/inventory/extend-hardware-inventory)을 참조하세요.  

- **규정 준수 설정**: Mac 및 Windows 클라이언트 컴퓨터에서 설정을 평가하고 수정하려면 이 기능을 사용하도록 설정하고 구성합니다. 자세한 내용은 [준수 설정 계획 및 구성](/sccm/compliance/plan-design/plan-for-and-configure-compliance-settings)을 참조하세요.  

자세한 내용은 [클라이언트 설정을 구성하는 방법](/sccm/core/clients/deploy/configure-client-settings)을 참조하세요.  



## <a name="bkmk_download"></a> Mac 클라이언트 다운로드  

1. [Microsoft 다운로드 센터](https://www.microsoft.com/download/details.aspx?id=47719)에서 Mac OS X 클라이언트 파일 패키지를 다운로드합니다. **ConfigmgrMacClient.msi**를 Windows를 실행하는 컴퓨터에 저장합니다. 이 파일은 Configuration Manager 설치 미디어에 없습니다.  

2. Windows 컴퓨터에서 설치 관리자를 실행합니다. **Macclient.dmg** Mac 클라이언트 패키지를 로컬 디스크의 폴더에 추출합니다. 기본 경로는 `C:\Program Files (x86)\Microsoft\System Center 2012 Configuration Manager Mac Client`입니다.  

3. **Macclient.dmg** 파일을 Mac 컴퓨터의 폴더에 복사합니다.  

4. Mac 컴퓨터에서 **Macclient.dmg**를 실행하여 로컬 디스크의 폴더에 추출합니다.  

5. 폴더에서 다음 파일이 포함되어 있는지 확인합니다. 

    - **Ccmsetup**: **CMClient.pkg**를 사용하여 Configuration Manager 클라이언트를 Mac 컴퓨터에 설치합니다.  

    - **CMDiagnostics**: Mac 컴퓨터에서 Configuration Manager 클라이언트와 관련된 진단 정보를 수집합니다.  

    - **CMUninstall**: Mac 컴퓨터에서 클라이언트를 제거합니다.  

    - **CMAppUtil**: Apple 애플리케이션 패키지를 Configuration Manager 애플리케이션으로 배포할 수 있는 형식으로 변환합니다.  

    - **CMEnroll**: Configuration Manager 클라이언트를 설치할 수 있도록 Mac 컴퓨터에 대한 클라이언트 인증서를 요청하고 설치합니다.  



## <a name="bkmk_enroll"></a> Mac 클라이언트 등록  

[Mac 컴퓨터 등록 마법사](#enroll-the-client-with-the-mac-computer-enrollment-wizard)를 사용하여 개별 클라이언트를 등록합니다.

많은 클라이언트에 대한 등록을 자동화하려면 [CMEnroll 도구](#client-and-certificate-automation-with-cmenroll)를 사용합니다.   


### <a name="enroll-the-client-with-the-mac-computer-enrollment-wizard"></a>Mac 컴퓨터 등록 마법사를 사용하여 클라이언트 등록  

1. 클라이언트가 설치되면 컴퓨터 등록 마법사가 열립니다. 마법사를 수동으로 시작하려면 **Configuration Manager** 기본 설정 페이지에서 **등록**을 선택합니다.  

2. 마법사의 두 번째 페이지에서 다음 정보를 제공합니다.  

   - **사용자 이름**: 사용자 이름은 다음 형식이 될 수 있습니다.  

     - `domain\name`를 재정의하려면 선택합니다. `contoso\mnorth`  

     - `user@domain`를 재정의하려면 선택합니다. `mnorth@contoso.com`  

         > [!IMPORTANT]  
         >  이메일 주소를 사용하여 **사용자 이름** 필드를 채우면 Configuration Manager에서 **서버 이름** 필드를 자동으로 채웁니다. 등록 프록시 지점 서버의 기본 이름과 이메일 주소의 도메인 이름을 사용합니다. 이러한 이름이 등록 프록시 지점 서버의 이름과 일치하지 않으면 등록 중에 **서버 이름**을 수정합니다.  

       사용자 이름 및 해당 암호는 Mac 클라이언트 인증서 템플릿에 대한 **읽기** 및 **등록** 권한이 있는 Active Directory 사용자 계정과 일치해야 합니다.  

   - **서버 이름**: 등록 프록시 지점 서버의 이름입니다.  


### <a name="client-and-certificate-automation-with-cmenroll"></a>CMEnroll을 사용하여 클라이언트 및 인증서 자동화  

CMEnroll 도구를 사용하여 클라이언트 설치를 자동화하고 클라이언트 인증서를 요청 및 등록하려면 다음 절차를 따릅니다. 도구를 실행하려면 Active Directory 사용자 계정이 있어야 합니다.

1. Mac 컴퓨터에서 **Macclient.dmg** 파일의 콘텐츠를 추출한 폴더로 이동합니다.  

2. 다음 명령을 입력합니다. `sudo ./ccmsetup`  

3. **설치 완료** 메시지가 나타날 때까지 기다립니다. 설치 관리자에서 지금 다시 시작해야 한다는 메시지가 표시되더라도 다시 시작하지 않고 다음 단계를 계속 진행합니다.  

4. Mac 컴퓨터의 **Tools** 폴더에서 `sudo ./CMEnroll -s <enrollment_proxy_server_name> -ignorecertchainvalidation -u '<user_name>'` 명령을 입력합니다.  

    클라이언트를 설치한 후 Mac 컴퓨터 등록을 안내하는 Mac 컴퓨터 등록 마법사가 열립니다. 자세한 내용은 [Mac 컴퓨터 등록 마법사를 사용하여 클라이언트 등록](#bkmk_enroll)을 참조하세요.  

     예제: 등록 프록시 지점 서버의 이름이 **server02.contoso.com**,이고 Mac 클라이언트 인증서 템플릿에 대해 **contoso\mnorth** 권한을 부여하는 경우 `sudo ./CMEnroll -s server02.contoso.com -ignorecertchainvalidation -u 'contoso\mnorth'` 명령을 입력합니다.  

    > [!NOTE]  
    > 사용자 이름에 `<>"+=,` 문자 중 하나가 포함되면 등록이 실패합니다. 이러한 문자가 포함되지 않은 사용자 이름으로 대역 외 인증서를 사용합니다.  
    >  
    > 더 원활한 사용자 환경을 위해 설치 단계를 스크립팅합니다. 그런 다음, 사용자가 자신의 사용자 이름과 암호만 제공해야 합니다.  

5. Active Directory 사용자 계정의 암호를 입력합니다. 이 명령을 입력하면 두 개의 암호를 입력하라는 메시지가 나타납니다. 첫 번째 암호는 명령을 실행할 슈퍼 사용자 계정에 대한 암호입니다. 두 번째는 Active Directory 사용자 계정의 암호를 묻습니다. 메시지가 동일하게 나타날 수 있으므로 올바른 순서로 암호를 지정해야 합니다.  

6. **등록 성공** 메시지가 나타날 때까지 기다립니다.  

7. 등록된 인증서를 Configuration Manager로 제한하려면 Mac 컴퓨터에서 터미널 창을 열고 다음과 같이 변경합니다.  

    1. `sudo /Applications/Utilities/Keychain Access.app/Contents/MacOS/Keychain Access` 명령 입력  

    2. **키 집합 액세스** 창의 **키 집합** 섹션에서 **시스템**을 클릭합니다. 그런 다음, **범주** 섹션에서 **키**를 선택합니다.  

    3. 클라이언트 인증서를 보려면 해당 키를 확장합니다. 설치한 프라이빗 키를 사용하여 인증서를 찾은 다음, 해당 키를 엽니다.  

    4. **Access Control**(액세스 제어) 탭에서 **접근 허용 전 확인**을 선택합니다.  

    5. **/Library/Application Support/Microsoft/CCM**으로 이동하고 **CCMClient**를 선택한 후 **추가**를 선택합니다.  

    6. **변경사항 저장**을 선택하고 **키 집합 접근** 대화 상자를 닫습니다.  

8. Mac 컴퓨터를 다시 시작합니다.  

클라이언트 설치가 성공했는지 확인하려면 Mac 컴퓨터의 **시스템 기본 설정**에서 **Configuration Manager**를 항목을 엽니다. 또한 Configuration Manager 콘솔에서 **모든 시스템** 컬렉션을 업데이트하고 확인합니다. Mac 컴퓨터가 이 컬렉션에서 관리되는 클라이언트로 나타나는지 확인합니다.  

> [!TIP]  
> Mac 클라이언트 문제를 해결하려면 Mac 클라이언트 패키지에 포함된 **CMDiagnostics** 도구를 사용합니다. 이 도구를 사용하여 수집하는 진단 정보는 다음과 같습니다.  
>   
> - 실행 중인 프로세스 목록  
> - Mac OS X 운영 체제 버전  
> - **CCM\*.crash** 및 **System Preference.crash**를 비롯한 Configuration Manager 클라이언트와 관련된 Mac OS X 충돌 보고서  
> - Configuration Manager 클라이언트 설치를 통해 생성된 BOM(제품 구성 정보) 파일 및 속성 목록(.plist) 파일  
> - **/Library/Application Support/Microsoft/CCM/Logs** 폴더의 내용  
>   
> CmDiagnostics를 통해 수집되는 정보는 `cmdiag-<hostname>-<datetime>.zip`이라는 이름의 Zip 파일에 추가되어 컴퓨터 바탕 화면에 저장됩니다.



## <a name="bkmk_external"></a> Configuration Manager 외부의 인증서 관리

Configuration Manager와 별도로 인증서 요청 및 설치 방법을 사용할 수 있습니다. 동일한 일반 프로세스를 사용하지만 여기에 추가되는 단계는 다음과 같습니다. 

- Configuration Manager 클라이언트를 설치할 때 **MP** 및 **SubjectName** 명령줄 옵션을 사용합니다. `sudo ./ccmsetup -MP <management point internet FQDN> -SubjectName <certificate subject name>` 명령을 입력합니다. 인증서 주체 이름은 대/소문자를 구분하므로 인증서 세부 정보에 표시된 대로 정확하게 입력합니다.  

     예제: 관리 지점의 인터넷 FQDN은 **server03.contoso.com**입니다. Mac 클라이언트 인증서에는 인증서 주체의 일반 이름으로 **mac12.contoso.com**의 FQDN이 있습니다. `sudo ./ccmsetup -MP server03.contoso.com -SubjectName mac12.contoso.com` 명령을 사용합니다.  

- 주체 값이 동일한 인증서가 둘 이상 있는 경우 Configuration Manager 클라이언트에 사용할 인증서 일련 번호를 지정합니다. `sudo defaults write com.microsoft.ccmclient SerialNumber -data "<serial number>"` 명령을 사용합니다.  

     `sudo defaults write com.microsoft.ccmclient SerialNumber -data "17D4391A00000003DB"`  



## <a name="renew-the-mac-client-certificate"></a>Mac 클라이언트 인증서 갱신  

이 절차에서는 SMSID를 삭제합니다. Mac용 Configuration Manager 클라이언트에서 새 인증서 또는 갱신된 인증서를 사용하려면 새 ID가 필요합니다.  

> [!IMPORTANT]  
> 클라이언트 SMSID를 바꾼 후에 Configuration Manager 콘솔에서 이전 리소스를 삭제하면 저장된 클라이언트 기록도 모두 삭제됩니다. 예를 들어 해당 클라이언트에 대한 하드웨어 인벤토리 기록이 있습니다.  


1. 컴퓨터 인증서를 갱신해야 하는 Mac 컴퓨터에 대한 디바이스 컬렉션을 만들고 채웁니다.  

2. **자산 및 호환성** 작업 영역에서 **구성 항목 만들기 마법사**를 시작합니다.  

3. 마법사의 **일반** 페이지에서 다음 정보를 지정합니다.  

    - **이름**: **Mac용 SMSID 제거**  

    - **유형**: **Mac OS X**  

4. **지원되는 플랫폼** 페이지에서 모든 Mac OS X 버전을 선택합니다.  

5. **설정** 페이지에서 **새로 만들기**를 선택합니다. **설정 만들기** 창에서 다음 정보를 지정합니다.  

    - **이름**: **Mac용 SMSID 제거**  

    - **설정 유형**: **스크립트**  

    - **데이터 형식**: **문자열**  

6. **설정 만들기** 창에서 **검색 스크립트**에 대해 **스크립트 추가**를 선택합니다. 이 작업은 SMSID로 구성된 Mac 컴퓨터를 검색하는 스크립트를 지정합니다.  

7. **검색 스크립트 편집** 창에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults read com.microsoft.ccmclient SMSID  
    ```  

8. **확인**을 선택하여 **검색 스크립트 편집** 창을 닫습니다.  

9. **설정 만들기** 창에서 **재구성 스크립트(옵션)** 에 대해 **스크립트 추가**를 선택합니다. 이 작업은 Mac 컴퓨터에서 찾은 SMSID를 제거하는 스크립트를 지정합니다.  

10. **재구성 스크립트 만들기** 창에서 다음 셸 스크립트를 입력합니다.  

    ```  
    defaults delete com.microsoft.ccmclient SMSID  
    ```  

11. **확인**을 선택하여 **재구성 스크립트 만들기** 창을 닫습니다.  

12. **규정 준수 규칙** 페이지에서 **새로 만들기**를 선택합니다. 그런 다음, **규칙 만들기** 창에서 다음 정보를 지정합니다.  

    - **이름**: **Mac용 SMSID 제거**  

    - **선택한 설정**: **찾아보기**를 선택한 다음, 이전에 지정한 검색 스크립트를 선택합니다.  

    - **다음 값** 필드에서 **(com.microsoft.ccmclient, SMSID)의 도메인/기본값 쌍이 존재하지 않음**를 입력합니다.  

    - **이 설정이 규칙을 준수하지 않는 경우 지정한 재구성 스크립트를 실행**하는 옵션을 사용하도록 설정합니다.  

13. 마법사를 완료합니다.  

14. 이 구성 항목이 포함된 구성 기준을 만듭니다. 해당 기준을 대상 컬렉션에 배포합니다.  

     자세한 내용은 [구성 기준을 만드는 방법](/sccm/compliance/deploy-use/create-configuration-baselines)을 참조하세요.  

15. SMSID가 제거된 Mac 컴퓨터에 새 인증서를 설치한 후에 다음 명령을 실행하여 클라이언트에서 새 인증서를 사용하도록 구성합니다.  

    ```  
    sudo defaults write com.microsoft.ccmclient SubjectName -string <subject_name_of_new_certificate>  
    ```  



## <a name="see-also"></a>참고 항목

[Mac에 클라이언트 배포 준비](/sccm/core/clients/deploy/prepare-to-deploy-mac-clients)

[Mac 클라이언트 유지 관리](/sccm/core/clients/manage/maintain-mac-clients)
