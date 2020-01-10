---
title: 인터넷 기반 디바이스 공동 관리
titleSuffix: Configuration Manager
description: 공동 관리를 위해 Windows 10 인터넷 기반 디바이스를 준비하는 방법을 알아봅니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 07/31/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: 956f5386b80246268a79fc85110cc52b8f16a550
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825373"
---
# <a name="how-to-prepare-internet-based-devices-for-co-management"></a>공동 관리를 위해 인터넷 기반 디바이스를 준비하는 방법

이 문서에서는 새 인터넷 기반 디바이스를 위한 공동 관리의 두 번째 경로를 주로 다룹니다. 이 시나리오는 Azure AD에 가입되고 Intune에 자동으로 등록되는 새 Windows 10 디바이스가 있는 경우입니다. Configuration Manager 클라이언트를 설치하여 공동 관리 상태가 됩니다.  

## <a name="windows-autopilot"></a>Windows Autopilot

새 Windows 10 디바이스에서 Autopilot 서비스를 사용하여 OOBE(첫 실행 경험)를 구성할 수 있습니다. 이 프로세스에는 디바이스를 Azure AD에 가입시키고 Intune에 등록하는 과정이 포함됩니다.  

자세한 내용은 [Overview of Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)(Windows Autopilot 개요)을 참조하세요.

디바이스를 Azure AD에 가입시킬 때 Intune에 자동으로 등록되도록 구성하려면  [Microsoft Intune에 Windows 디바이스 등록](https://docs.microsoft.com/intune/windows-enroll)을 참조하세요.  

### <a name="gather-information-from-configuration-manager"></a>Configuration Manager에서 정보 수집

버전 1802부터 Configuration Manager를 사용하여 Intune에서 필요한 디바이스 정보를 수집하고 보고합니다. 이 정보에는 디바이스 일련 번호, Windows 제품 식별자 및 하드웨어 식별자가 포함됩니다. 이 정보는 Windows Autopilot을 지원하도록 Intune에 디바이스를 등록하는 데 사용됩니다.

1. Configuration Manager 콘솔에서 **모니터링** 작업 영역으로 이동하고 **보고** 노드, **보고서** 노드를 차례로 확장하고 **하드웨어 - 일반** 노드를 선택합니다.  

2. **Windows Autopilot 디바이스 정보** 보고서를 실행하고 결과를 확인합니다.  

3. 보고서 뷰어에서 **내보내기** 아이콘을 선택하고 **CSV(쉼표로 구분)** 옵션을 선택합니다.  

4. 파일을 저장하고 Intune에 업로드합니다.  

자세한 내용은 [Intune에 디바이스 추가](https://docs.microsoft.com/intune/enrollment-autopilot#add-devices)를 참조하세요.

### <a name="autopilot-for-existing-devices"></a>기존 디바이스를 위한 Autopilot
<!--1358333-->

[기존 디바이스를 위한 Windows Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)은 Windows 10 버전, 1809 이상에서 사용할 수 있습니다. 이 기능을 사용하면 단일, 네이티브 Configuration Manager 작업 순서를 사용하여 [Windows Autopilot user-driven mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)(Windows Autopilot 사용자 기반 모드)용으로 Windows 7 디바이스를 이미지로 다시 설치하고 프로비전할 수 있습니다.

자세한 내용은 [Windows Autopilot for existing devices task sequence](/sccm/osd/deploy-use/windows-autopilot-for-existing-devices)(기존 디바이스를 위한 Windows Autopilot 작업 순서)를 참조하세요.

## <a name="install-the-configuration-manager-client"></a>Configuration Manager 클라이언트 설치

두 번째 경로의 인터넷 기반 디바이스의 경우 Intune에서 앱을 만들어야 합니다. 아직 Configuration Manager 클라이언트가 아닌 Windows 10 디바이스에 이 앱을 배포합니다.

> [!Note]  
> 이 앱을 디바이스에 배포하기 전에 디바이스는 CMG 서버 인증 인증서를 신뢰해야 합니다. 자세한 내용은 [클라이언트에서 신뢰할 수 있는 CMG 루트 인증서](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#bkmk_cmgroot)를 참조하세요. 디바이스가 CMG 서버 인증 인증서를 신뢰하지 않는 경우, 클라이언트이 ccmsetup.log에 WINHTTP_CALLBACK_STATUS_FLAG_INVALID_CA 오류가 표시됩니다.

### <a name="get-the-command-line-from-configuration-manager"></a>Configuration Manager에서 명령줄 가져오기

1. Configuration Manager 콘솔에서 **관리** 작업 영역으로 이동하고, **Cloud Services**를 확장하고, **공동 관리** 노드를 선택합니다.  

2. 공동 관리 개체를 선택한 다음 리본에서 **속성**을 선택합니다.  

3. **사용 여부** 탭에서 명령줄을 복사합니다. 명령줄을 메모장에 붙여넣어 다음 프로세스를 위해 저장합니다.  

다음 명령줄은 예제 명령줄입니다. `CCMSETUPCMD="CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC"`

<!--1358215-->
버전 1806부터 이제 더 적은 명령줄 속성이 필요합니다.  

- 모든 시나리오에서 다음 명령줄 속성이 필요합니다.  
  - CCMHOSTNAME  
  - SMSSITECODE  

- 다음 속성은 PKI 기반의 클라이언트 인증 인증서 대신 클라이언트 인증용 Azure AD를 사용하는 경우 필요합니다.  
  - AADCLIENTAPPID  
  - AADRESOURCEURI  

- 클라이언트가 인트라넷으로 다시 로밍되는 경우 다음 속성이 필요합니다.  
  - SMSMP  

- 고유 PKI SSL 인증서를 사용하고 CRL이 인터넷에 게시되지 않은 경우 다음 매개 변수가 필요합니다.  
  - /noCRLCheck  

     자세한 내용은 [CRL 계획](/sccm/core/plan-design/security/plan-for-security#BKMK_PlanningForCRLs)을 참조하세요.  

버전 1810부터 사이트는 추가 Azure AD 정보를 CMG(클라우드 관리 게이트웨이)에 게시합니다. Azure AD에 가입된 클라이언트는 가입된 동일한 테넌트를 사용하여 ccmsetup 프로세스 중에 CMG에서 이 정보를 가져옵니다. 이 동작은 둘 이상의 Azure AD 테넌트가 있는 환경의 공동 관리에 디바이스를 등록하는 작업을 추가로 간소화합니다. 이제 유일한 두 개의 필수 ccmsetup 속성은 **CCMHOSTNAME** 및 **SMSSiteCode**입니다.<!--3607731-->

> [!Note]
> Intune에서 Configuration Manager 클라이언트를 이미 배포하는 경우 새 명령줄과 새 MSI를 사용하여 Intune 앱을 업데이트합니다. <!-- SCCMDocs-pr issue 3084 -->

다음 예제에서는 이러한 속성 모두를 포함합니다.

`ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com`

자세한 내용은 [클라이언트 설치 속성](/sccm/core/clients/deploy/about-client-installation-properties)을 참조합니다.

### <a name="create-the-app-in-intune"></a>Intune에서 앱 만들기

1. [Azure Portal](https://portal.azure.com)로 이동한 다음 Intune 페이지를 엽니다.  

2. **클라이언트 앱** > **앱** > **추가**를 선택합니다.  

3. **기타**에서 **기간 업무 앱**을 선택합니다.  

4. **ccmsetup.msi** 앱 패키지 파일을 업로드합니다. Configuration Manager 사이트 서버의 `<ConfigMgr installation directory>\bin\i386` 폴더에서 이 파일을 찾습니다.  

    > [!Tip]  
    > 사이트를 업데이트하는 경우 Intune에서 이 앱도 업데이트해야 합니다.  

5. 앱을 업데이트했으면 Configuration Manager에서 복사한 명령줄을 사용하여 앱 정보를 구성합니다.  

> [!IMPORTANT]
> 이 명령줄을 사용자 지정하는 경우는 이 명령줄이 1024자보다 길지 않아야 합니다. 명령줄 길이가 1024자를 넘는 경우 클라이언트 설치에 실패합니다.
