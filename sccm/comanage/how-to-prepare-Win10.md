---
title: 함께 인터넷 기반 장치 관리
titleSuffix: Configuration Manager
description: 공동 관리를 위해 Windows 10 인터넷 기반 장치를 준비 하는 방법에 알아봅니다.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 01/14/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.collection: M365-identity-device-management
ms.openlocfilehash: fbe26eee8b01c581776b1c134e1fe59cf4293e1a
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56755208"
---
# <a name="how-to-prepare-internet-based-devices-for-co-management"></a>공동 관리에 대 한 인터넷 기반 장치를 준비 하는 방법

이 문서에서는 새로운 인터넷 기반 장치에 대 한 공동 관리에 두 번째 경로에 중점을 둡니다. 이 시나리오는 Azure AD에 가입 및 Intune에 자동으로 등록 하는 새 Windows 10 장치가 있는 경우. 공동 관리 상태에 연결할 Configuration Manager 클라이언트를 설치할 수 있습니다.  



## <a name="windows-autopilot"></a>Windows Autopilot

새 Windows 10 장치에 대 한 상자 환경 (OOBE) 출력을 구성 하려면 Autopilot 서비스를 사용할 수 있습니다. 이 프로세스는 Azure AD에 장치를 가입 및 Intune에서 장치 등록을 포함 합니다.  

자세한 내용은 [Windows Autopilot 개요](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)합니다.    

Azure AD에 가입할 때 자동으로 등록을 Intune에 장치를 구성 하려면 참조 [Microsoft Intune에 등록 된 Windows 장치](https://docs.microsoft.com/intune/windows-enroll)합니다.  


### <a name="gather-information-from-configuration-manager"></a>Configuration Manager에서 정보를 수집 합니다.

버전 1802부터 Configuration Manager를 사용하여 비즈니스 및 교육용 Microsoft Store에서 필요한 디바이스 정보를 수집하고 보고합니다. 이 정보에는 디바이스 일련 번호, Windows 제품 식별자 및 하드웨어 식별자가 포함됩니다. Windows Autopilot을 지원 하도록 Microsoft Store 장치를 등록 하는 것이 됩니다. 

1. Configuration Manager 콘솔에서로 이동 합니다 **모니터링** 작업 영역에서 확장을 **보고** 노드를 확장 **보고서**, 선택한는 **하드웨어- 일반** 노드.  

2. 보고서를 실행할 **Windows Autopilot 장치 정보**, 결과 봅니다.  

3. 보고서 뷰어를 선택 합니다 **내보내기** 아이콘을 선택 합니다 **CSV (쉼표로 구분)** 옵션.  

4. 파일을 저장한 후 비즈니스 및 교육용 Microsoft 스토어에 데이터를 업로드합니다.  

자세한 내용은 [비즈니스 및 교육용 Microsoft Store 장치를 추가](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile)합니다.


### <a name="autopilot-for-existing-devices"></a>기존 장치에 대 한 autopilot
<!--1358333-->

[기존 장치에 대 한 Windows Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430) 사용 가능한 Windows 10, 버전 1809 이상이 됩니다. 이 기능을 사용 하면 이미지로 다시 설치에 대 한 Windows 7 장치를 프로 비전 하 [Windows Autopilot 사용자 기반 모드](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven) 단일, 기본 Configuration Manager 작업 순서를 사용 합니다. 



## <a name="install-the-configuration-manager-client"></a>Configuration Manager 클라이언트를 설치 합니다.

두 번째 경로에서 인터넷 기반 장치의 경우 Intune에서 앱을 만들려고 해야 합니다. Configuration Manager 클라이언트가 이미 없는 Windows 10 장치에이 앱을 배포 합니다. 

### <a name="get-the-command-line-from-configuration-manager"></a>Configuration Manager에서 명령줄을 가져옵니다

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다.  

2. 공동 관리 개체를 선택 하 고 선택한 **속성** 리본 메뉴에 있습니다.  

3. 에 **사용** 탭, 명령줄을 복사 합니다. 다음 프로세스에 대 한 저장 하려면 메모장에 붙여 넣습니다.  

다음 명령줄은 예: `CCMSETUPCMD="CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC"`

<!--1358215--> 버전 1806부터 더 적은 명령줄 속성이 필요합니다.  

- 모든 시나리오에서 다음 명령줄 속성이 필요합니다.  
    - CCMHOSTNAME  
    - SMSSITECODE  

- 다음 속성은 PKI 기반의 클라이언트 인증 인증서 대신 클라이언트 인증용 Azure AD를 사용하는 경우 필요합니다.  
    - AADCLIENTAPPID  
    - AADRESOURCEURI  

- 클라이언트가 인트라넷으로 다시 로밍 하는 경우 다음 속성이 필요 합니다.  
    - SMSMP  

- 고유 PKI SSL 인증서 및 CRL에 사용 하 여 인터넷에 게시 되지, 다음 매개 변수는 필수:  
    - /noCRLCheck  
    
     자세한 내용은 참조 하세요. [Crl에 대 한 계획](/sccm/core/plan-design/security/plan-for-security#-plan-for-the-site-server-signing-certificate-self-signed)  

다음 예제를 포함 하 여 이러한 모든 속성:   
`ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com`

자세한 내용은 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties)을 참조합니다.


### <a name="create-the-app-in-intune"></a>Intune에서 앱 만들기

1. 로 이동 합니다 [Azure portal](https://portal.azure.com), 한 다음 Intune 페이지를 엽니다.  

2. 선택 **클라이언트 앱** > **앱** > **추가**합니다.  

3. **기타**에서 **기간 업무 앱**을 선택합니다.  

4. 업로드 합니다 **ccmsetup.msi** 앱 패키지 파일입니다. 사이트 서버의 다음 폴더는 Configuration Manager에서이 파일을 찾을: `<ConfigMgr installation directory>\bin\i386`합니다.  

5. 앱이 업데이트 되 면 Configuration Manager에서 복사한 명령줄을 사용 하 여 앱 정보를 구성 합니다.  

> [!IMPORTANT]    
> 이 명령줄을 사용자 지정 하는 경우는 1024 자 보다 긴 없는 있는지 확인 해야 합니다. 명령줄 길이 1024 자 보다 긴 경우 클라이언트 설치에 실패 합니다.


