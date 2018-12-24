---
title: 인증서 인프라 구성
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 인증서 등록을 구성하는 방법을 알아봅니다.
ms.date: 07/25/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 29ae59b7-2695-4a0f-a9ff-4f29222f28b3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c27f92374470c7d87d49661b20996a3f0c47f8a4
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32351992"
---
# <a name="configure-certificate-infrastructure"></a>인증서 인프라 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 인증서 인프라를 구성하는 방법을 알아봅니다. 시작하기 전에 [System Center Configuration Manager에서 인증서 프로필에 대한 필수 조건](../../protect/plan-design/prerequisites-for-certificate-profiles.md)에 나열된 모든 필수 조건을 확인합니다.  

이러한 단계를 사용하여 SCEP 또는 PFX 인증서의 인프라를 구성합니다.

## <a name="step-1---install-and-configure-the-network-device-enrollment-service-and-dependencies-for-scep-certificates-only"></a>1단계: 네트워크 디바이스 등록 서비스 및 종속성 설치 및 구성(SCEP 인증서에만 해당)

 AD CS(Active Directory 인증서 서비스)용 네트워크 디바이스 등록 서비스 역할 서비스를 설치 및 구성하고, 인증서 템플릿에 대한 보안 권한을 변경하고, PKI(공개 키 인프라) 클라이언트 인증 인증서를 배포하고, IIS(인터넷 정보 서비스) 기본 URL 크기 제한을 늘리도록 레지스트리를 편집해야 합니다. 필요한 경우 발급 CA(인증 기관)에서 사용자 지정 유효 기간을 허용하도록 구성해야 합니다.  

> [!IMPORTANT]  
>  네트워크 디바이스 등록 서비스와 함께 사용할 수 있도록 System Center Configuration Manager를 구성하기 전에 네트워크 디바이스 등록 서비스가 설치 및 구성되어 있는지 확인하세요. 이러한 종속 항목이 제대로 작동하지 않는 경우 System Center Configuration Manager를 사용하여 인증서 등록 문제를 해결하는 데 어려움을 겪을 수 있습니다.  

### <a name="to-install-and-configure-the-network-device-enrollment-service-and-dependencies"></a>네트워크 디바이스 등록 서비스 및 종속 항목을 설치하고 구성하려면  

1.  Windows Server 2012 R2를 실행하는 서버에서 Active Directory 인증서 서비스 서버 역할용 네트워크 디바이스 등록 서비스 역할 서비스를 설치하고 구성합니다. 자세한 내용은 TechNet의 Active Directory 인증서 서비스 라이브러리에서 [Network Device Enrollment Service Guidance(네트워크 디바이스 등록 서비스 지침)](http://go.microsoft.com/fwlink/p/?LinkId=309016) 를 참조하세요.  

2.  다음과 같이 네트워크 디바이스 등록 서비스에 사용되는 인증서 템플릿의 보안 권한을 확인하고 필요한 경우 수정합니다.  

    -   System Center Configuration Manager 콘솔을 실행하는 계정의 경우: **읽기** 권한  

         인증서 프로필 만들기 마법사를 실행할 때 SCEP 설정 프로필을 만드는 데 사용할 인증서 템플릿을 찾아 선택하려면 이 권한이 필요합니다. 인증서 템플릿을 선택하면 마법사의 일부 설정이 자동으로 채워집니다. 따라서 사용자가 구성할 항목이 적어지고 네트워크 디바이스 등록 서비스에 사용되는 인증서 템플릿과 호환되지 않는 설정을 선택할 위험이 줄어듭니다.  

    -   네트워크 디바이스 등록 서비스 응용 프로그램 풀에서 사용하는 SCEP 서비스 계정의 경우: **읽기** 및 **등록** 권한  

         이 요구 사항은 System Center Configuration Manager에 한정되지 않지만 네트워크 디바이스 등록 서비스를 구성하는 과정에 필요합니다. 자세한 내용은 TechNet의 Active Directory 인증서 서비스 라이브러리에서 [Network Device Enrollment Service Guidance(네트워크 디바이스 등록 서비스 지침)](http://go.microsoft.com/fwlink/p/?LinkId=309016) 를 참조하세요.  

    > [!TIP]  
    >  네트워크 디바이스 등록 서비스에서 사용하는 인증서 템플릿을 식별하려면 네트워크 디바이스 등록 서비스를 실행하는 서버에서 HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Cryptography\MSCEP 레지스트리 키를 확인합니다.  

    > [!NOTE]  
    >  이들은 대부분의 환경에 적합한 기본 보안 권한입니다. 그러나 다른 보안 구성을 사용할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 인증서 프로필에 대한 인증서 템플릿 권한 계획](../../protect/plan-design/planning-for-certificate-template-permissions.md)을 참조하세요.  

3.  클라이언트 인증을 지원하는 PKI 인증서를 이 서버에 배포합니다. 컴퓨터에 사용할 수 있는 적합한 인증서가 이미 설치되어 있거나 이 용도로만 인증서를 배포해야 하거나 배포하려고 할 수도 있습니다. 이 인증서의 요구 사항에 대한 자세한 내용은 [System Center Configuration Manager를 위한 PKI 인증서 요구 사항](../../core/plan-design/network/pki-certificate-requirements.md) 항목의 **서버용 PKI 인증서** 섹션에서 네트워크 디바이스 등록 서비스 역할 서비스와 함께 Configuration Manager 정책 모듈을 실행하는 서버 관련 세부 정보를 참조하세요.  

    > [!TIP]  
    >  이 인증서를 배포하는 데 도움이 필요한 경우 [배포 지점용 클라이언트 인증서 배포](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clientdistributionpoint2008_cm2012)에 있는 지침을 참조하세요. 다음 항목 하나를 제외하고 인증서 요구 사항이 동일하기 때문입니다.  
    >   
    >  -   인증서 템플릿 속성의 **요청 처리** 탭에서 **개인 키를 내보낼 수 있음** 확인란을 선택하지 않습니다.  
    >   
    >  System Center Configuration Manager 정책 모듈을 구성할 때 이 인증서를 로컬 컴퓨터 저장소에서 찾아 선택할 수 있으므로 개인 키를 포함하여 내보낼 필요가 없습니다.  

4.  클라이언트 인증 인증서를 연결할 루트 인증서를 찾습니다. 그런 다음 이 루트 CA 인증서를 인증서(.cer) 파일로 내보냅니다. 나중에 인증서 등록 지점의 사이트 시스템 서버를 설치 및 구성할 때 안전하게 액세스할 수 있도록 보안이 유지되는 위치에 이 파일을 저장합니다.  

5.  동일한 서버의 레지스트리 편집기에서 HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\HTTP\Parameters의 다음 레지스트리 키 DWORD 값을 설정하여 IIS 기본 URL 크기 제한을 늘립니다.  

    -   **MaxFieldLength** 키를 **65534**로 설정합니다.  

    -   **MaxRequestBytes** 키를 **16777216**으로 설정합니다.  

     자세한 내용은 Microsoft 기술 자료의 [820129: Windows에 대한 Http.sys 레지스트리 설정](http://go.microsoft.com/fwlink/?LinkId=309013) 문서를 참조하세요.  

6.  동일한 서버의 IIS(인터넷 정보 서비스) 관리자에서 /certsrv/mscep 응용 프로그램의 요청 필터링 설정을 수정한 후 서버를 다시 시작합니다. **요청 필터링 설정 편집** 대화 상자에서 **요청 제한** 설정을 다음과 같이 구성해야 합니다.  

    -   **허용되는 최대 콘텐츠 길이(바이트)**: **30000000**  

    -   **최대 URL 길이(바이트)**: **65534**  

    -   **최대 쿼리 문자열(바이트)**: **65534**  

     이러한 설정에 대한 자세한 내용과 해당 설정을 구성하는 방법에 대한 자세한 내용은 IIS 참조 라이브러리에서 [Requests Limits(요청 제한)](http://go.microsoft.com/fwlink/?LinkId=309014) 항목을 참조하세요.  

7.  사용 중인 인증서 템플릿보다 유효 기간이 짧은 인증서를 요청할 수 있도록 설정하려는 경우 이 구성은 엔터프라이즈 CA에 대해 기본적으로 사용하지 않도록 설정되어 있습니다. 엔터프라이즈 CA에 대해 이 옵션을 사용하도록 설정하려면 Certutil 명령줄 도구에서 다음 명령을 사용하여 인증서 서비스를 중지한 후 다시 시작해야 합니다.  

    1.  **certutil - setreg Policy\EditFlags +EDITF_ATTRIBUTEENDDATE**  

    2.  **net stop certsvc**  

    3.  **net start certsvc**  

     자세한 내용은 TechNet에서 PKI 기술 라이브러리의 [Certificate Services Tools and Settings(인증서 서비스 도구 및 설정)](http://go.microsoft.com/fwlink/p/?LinkId=309015) 를 참조하세요.  

8.  네트워크 디바이스 등록 서비스가 다음 링크를 사용하여 작동 중인지 확인합니다(예: **https://server.contoso.com/certsrv/mscep/mscep.dll**). 기본 제공되는 네트워크 디바이스 등록 서비스 웹 페이지가 나타납니다. 이 웹 페이지에서는 서비스에 대해 설명하고, 네트워크 디바이스가 인증서 요청을 제출하는 URL을 사용한다는 것을 설명합니다.  

 네트워크 디바이스 등록 서비스와 종속 항목을 구성했으므로 이제 인증서 등록 지점을 설치 및 구성할 준비가 되었습니다.


## <a name="step-2---install-and-configure-the-certificate-registration-point"></a>2단계 - 인증서 등록 지점 설치 및 구성

System Center Configuration Manager 계층에 인증서 등록 지점을 하나 이상 설치하고 구성해야 하며, 중앙 관리 사이트 또는 기본 사이트에 이 사이트 시스템 역할을 설치할 수 있습니다.  

> [!IMPORTANT]  
>  인증서 등록 지점을 설치하기 전에 운영 체제 요구 사항 및 인증서 등록 지점의 종속 항목을 다루는 [System Center Configuration Manager에서 지원되는 구성](../../core/plan-design/configs/supported-configurations.md) 항목의 **사이트 시스템 요구 사항** 섹션을 참조하세요.  

##### <a name="to-install-and-configure-the-certificate-registration-point"></a>인증서 등록 지점을 설치하고 구성하려면  

1.  System Center Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2.  **관리** 작업 영역에서 **사이트 구성**을 확장하고 **서버 및 사이트 시스템 역할**을 클릭한 다음 인증서 등록 지점에 사용할 서버를 선택합니다.  

3.  **홈** 탭의 **서버** 그룹에서 **사이트 시스템 역할 추가**를 클릭합니다.  

4.  **일반** 페이지에서 사이트 시스템의 일반 설정을 지정하고 **다음**을 클릭합니다.  

5.  **프록시** 페이지에서 **다음**을 클릭합니다. 인증서 등록 지점은 인터넷 프록시 설정을 사용하지 않습니다.  

6.  **시스템 역할 선택** 페이지의 사용 가능한 역할 목록에서 **인증서 등록 지점** 을 선택하고 **다음**을 클릭합니다. 

7. **인증서 등록 모드** 페이지에서 이 인증서 등록 지점으로 **SCEP 인증서 요청 처리** 또는 **PFX 인증서 요청 처리**를 수행할지 선택합니다. 인증서 등록 지점은 두 종류의 요청을 모두 처리할 수 없지만 두 가지 인증서 유형을 모두 사용할 경우 여러 인증서 등록 지점을 만들 수 있습니다.

   PFX 인증서를 처리하는 경우 Microsoft 또는 Entrust 인증 기관을 선택해야 합니다.

8.  **인증서 등록 지점 설정** 페이지는 인증서 유형에 따라 다릅니다.
    -   **SCEP 인증서 요청 처리**를 선택한 경우 다음을 구성합니다.
        -   인증서 등록 지점에 대한 **웹 사이트 이름**, **HTTPS 포트 번호** 및 **가상 응용 프로그램 이름**. 이러한 필드는 기본값으로 자동으로 입력됩니다. 
        -   **네트워크 장치 등록 서비스 및 루트 CA 인증서의 URL** - **추가**를 클릭하고 **URL 및 루트 CA 인증서 추가** 대화 상자에서 다음을 지정합니다.
            - **네트워크 장치 등록 서비스의 URL**: URL을 https://*<server_FQDN>*/certsrv/mscep/mscep.dll 형식으로 지정합니다. 예를 들어 네트워크 디바이스 등록 서비스를 실행하는 서버의 FQDN이 server1.contoso.com인 경우 **https://server1.contoso.com/certsrv/mscep/mscep.dll**을 입력합니다.
            - **루트 CA 인증서**: **1단계: 네트워크 장치 등록 서비스 및 종속성 설치 및 구성**에서 만들어 저장한 인증서(.cer) 파일을 찾아서 선택합니다. 인증서 등록 지점은 이 루트 CA 인증서를 사용하여 System Center Configuration Manager 정책 모듈에 사용될 클라이언트 인증 인증서의 유효성을 검사할 수 있습니다.  

    - **PFX 인증서 요청 처리**를 선택한 경우 선택한 인증 기관에 대한 연결 정보 및 자격 증명을 구성합니다.

        - Microsoft를 인증 기관으로 사용하려면 **추가**를 클릭하고 **인증 기관 및 계정 추가** 대화 상자에서 다음을 지정합니다.
            - **인증 기관 서버 이름** - 인증 기관 서버의 이름을 입력합니다.
            - **인증 기관 계정** - **설정**을 클릭하여 인증 기관에서 템플릿에 등록할 권한이 있는 계정을 선택하거나 만듭니다.
            - **인증서 등록 지점 연결 계정** - 인증 등록 지점을 Configuration Manager 데이터베이스에 연결하는 계정을 선택하거나 만듭니다. 또는 인증서 등록 지점을 호스트하는 컴퓨터의 로컬 컴퓨터 계정을 사용할 수 있습니다.
            - **Active Directory 인증서 게시 계정** - Active Directory의 사용자 개체에 인증서를 게시하는 데 사용되는 계정을 선택하거나 새로 만듭니다.

            - **네트워크 장치 등록 URL 및 루트 CA 인증서** 대화 상자에서 다음을 지정한 후 **확인**을 클릭합니다.  

        - 인증 기관으로 Entrust를 사용하려면 다음을 지정합니다.

           - **MDM 웹 서비스 URL**
           - URL에 대한 사용자 이름 및 암호 자격 증명

           MDM API를 사용하여 Entrust 웹 서비스 URL을 정의할 경우 다음 샘플과 같이 버전 9 이상의 API를 사용해야 합니다.

           `https://entrust.contoso.com:19443/mdmws/services/AdminServiceV9`

           이전 버전의 API는 Entrust를 지원하지 않습니다.

9. **다음** 을 클릭하여 마법사를 완료합니다.  

10. 설치가 완료될 때까지 몇 분간 기다린 후 다음 방법 중 하나를 사용하여 인증서 등록 지점이 성공적으로 설치되었는지 확인합니다.  

    -   **모니터링** 작업 영역에서 **시스템 상태**를 확장한 후 **구성 요소 상태**를 클릭하고 **SMS_CERTIFICATE_REGISTRATION_POINT** 구성 요소의 상태 메시지를 찾아봅니다.  

    -   사이트 시스템 서버에서 *<Configuration Manager 설치 경로\>* \Logs\crpsetup.log 파일 및 *<Configuration Manager 설치 경로\>* \Logs\crpmsi.log 파일을 사용합니다. 설치가 성공하면 종료 코드 0이 반환됩니다.  

    -   브라우저를 사용하여 https://server1.contoso.com/CMCertificateRegistration과 같은 인증서 등록 지점의 URL에 연결할 수 있는지 확인합니다. HTTP 404 설명과 함께 응용 프로그램 이름에 대한 **서버 오류** 페이지가 나타나야 합니다.  

11. 인증서 등록 지점에서 기본 사이트 서버 컴퓨터의 *<ConfigMgr 설치 경로\>* \inboxes\certmgr.box 폴더에 자동으로 만든 내보낸 루트 CA용 인증서 파일을 찾습니다. 나중에 네트워크 디바이스 등록 서비스를 실행하는 서버에 System Center Configuration Manager 정책 모듈을 설치할 때 안전하게 액세스할 수 있도록 보안이 유지되는 위치에 이 파일을 저장합니다.  

    > [!TIP]  
    >  이 폴더에서 이 인증서를 바로 사용할 수는 없습니다. System Center Configuration Manager에서 파일을 이 위치로 복사할 때까지 어느 정도(예: 30분) 기다려야 할 수 있습니다.  


## <a name="step-3----install-the-system-center-configuration-manager-policy-module-for-scep-certificates-only"></a>3단계 - System Center Configuration Manager 정책 모듈 설치(SCEP 인증서에만 해당)

System Center Configuration Manager 정책 모듈을 **2단계: 인증서 등록 지점 설치 및 구성**에서 지정한 각 서버에서 인증서 등록 지점에 대한 속성인 **네트워크 디바이스 등록 서비스의 URL**로 설치하고 구성해야 합니다.  

##### <a name="to-install-the-policy-module"></a>정책 모듈을 설치하려면  

1.  네트워크 장치 등록 서비스를 실행하는 서버에서 도메인 관리자로 로그온하고 System Center Configuration Manager 설치 미디어의 <ConfigMgrInstallationMedia\>\SMSSETUP\POLICYMODULE\X64 폴더에 있는 다음 파일을 임시 폴더에 복사합니다.  

    -   PolicyModule.msi  

    -   PolicyModuleSetup.exe  

    또한 설치 미디어에 LanguagePack 폴더가 있는 경우 LanguagePack 폴더와 폴더의 내용을 복사합니다.  

2.  임시 폴더에서 PolicyModuleSetup.exe를 실행하여 System Center Configuration Manager 정책 모듈 설치 마법사를 시작합니다.  

3.  마법사의 시작 페이지에서 **다음**을 클릭하고 사용 조건에 동의한 후 **다음**을 클릭합니다.  

4.  **설치 폴더** 페이지에서 정책 모듈의 기본 설치 폴더를 그대로 적용하거나 다른 폴더를 지정한 후 **다음**을 클릭합니다.  

5.  **인증서 등록 지점** 페이지에서 인증서 등록 지점 속성에 지정된 사이트 시스템 서버의 FQDN과 가상 응용 프로그램 이름을 사용하여 인증서 등록 지점의 URL을 지정합니다. 기본 가상 응용 프로그램 이름은 CMCertificateRegistration입니다. 예를 들어 사이트 시스템 서버의 FQDN이 server1.contoso.com이고 기본 가상 응용 프로그램 이름을 사용하는 경우 **https://server1.contoso.com/CMCertificateRegistration**을 지정합니다.  

6.  기본 포트 **443** 을 수락하거나 인증서 등록 지점에 사용되는 다른 포트 번호를 지정하고 **다음**을 클릭합니다.  

7.  **정책 모듈의 클라이언트 인증서**페이지에서 **1단계: 네트워크 장치 등록 서비스 및 종속성 설치 및 구성**에서 배포한 클라이언트 인증 인증서를 찾아서 지정하고 **다음**을 클릭합니다.  

8.  **인증서 등록 지점 인증서** 페이지에서 **찾아보기** 를 클릭하여 **2단계: 인증서 등록 지점 설치 및 구성**을 마무리할 때 찾아서 저장한 루트 CA용 내보낸 인증서 파일을 선택합니다.  

    > [!NOTE]  
    >  이 인증서 파일을 이전에 저장하지 않은 경우 이는 사이트 서버 컴퓨터의 <ConfigMgr 설치 경로\>\inboxes\certmgr.box에 있습니다.  

9. **다음** 을 클릭하여 마법사를 완료합니다.  

 System Center Configuration Manager 정책 모듈을 제거하려는 경우 제어판에서 **프로그램 및 기능**을 사용하세요. 

 
구성 단계를 완료했으므로 인증서 프로필을 만들어 배포하는 방식으로 사용자와 디바이스에 인증서를 배포할 준비가 되었습니다. 인증서 프로필을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 인증서 프로필을 만드는 방법](../../protect/deploy-use/create-certificate-profiles.md)을 참조하세요.  
