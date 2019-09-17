---
title: Endpoint Protection 클라이언트 설정
titleSuffix: Configuration Manager
description: Endpoint Protection에 대한 사용자 지정 클라이언트 설정을 구성하는 방법을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: fadbdaf8dc836e2f468aa0f8a82408d718606bc1
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892324"
---
# <a name="configure-custom-client-settings-for-endpoint-protection"></a>Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 절차에서는 계층 구조의 디바이스 컬렉션에 배포할 수 있는 Endpoint Protection에 대한 사용자 지정 클라이언트 설정을 구성합니다.

> [!IMPORTANT]  
>  확실히 계층 구조의 모든 컴퓨터에 적용하려면 기본 Endpoint Protection 클라이언트 설정만 구성합니다. 



## <a name="to-enable-endpoint-protection-and-configure-custom-client-settings"></a>Endpoint Protection을 사용하도록 설정하고 사용자 지정 클라이언트 설정을 구성하려면

1. Configuration Manager 콘솔에서 **관리**를 클릭합니다.  

2. **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.  

3. **홈** 탭의 **만들기** 그룹에서 **사용자 지정 클라이언트 디바이스 설정 만들기**를 클릭합니다.  

4. **사용자 지정 클라이언트 디바이스 설정 만들기** 대화 상자에서 설정 그룹의 이름과 설명을 지정하고 **Endpoint Protection**을 선택합니다.  

5. 필요한 Endpoint Protection 클라이언트 설정을 구성합니다. 구성할 수 있는 Endpoint Protection 클라이언트 설정의 전체 목록은 [클라이언트 설정 정보](/sccm/core/clients/deploy/about-client-settings#endpoint-protection)에서 Endpoint Protection 섹션을 참조하세요.  

   > [!IMPORTANT]  
   >  Endpoint Protection용 클라이언트 설정을 구성하려면 먼저 Endpoint Protection 사이트 시스템 역할을 설치합니다.  

6. **확인** 을 클릭하여 **사용자 지정 클라이언트 디바이스 설정 만들기** 대화 상자를 닫습니다. 새 클라이언트 설정이 **관리** 작업 영역의 **클라이언트 설정** 노드에 표시됩니다.  

7. 다음은, 사용자 지정 클라이언트 설정을 컬렉션에 배포합니다. 배포할 사용자 지정 클라이언트 설정을 선택합니다. **홈** 탭의 **클라이언트 설정** 그룹에서 **배포**를 클릭합니다.  

8. **컬렉션 선택** 대화 상자에서 클라이언트 설정을 배포할 컬렉션을 선택하고 **확인**을 클릭합니다. 새 배포가 세부 정보 창의 **배포** 탭에 표시됩니다.  

클라이언트가 다음번에 클라이언트 정책을 다운로드할 때 이러한 설정으로 구성됩니다. 자세한 내용은 [Configuration Manager 클라이언트에 대한 정책 검색 시작](/sccm/core/clients/manage/manage-clients#BKMK_PolicyRetrieval)을 참조하세요.  



## <a name="how-to-provision-the-endpoint-protection-client-in-a-disk-image"></a>디스크 이미지의 Endpoint Protection 클라이언트를 프로비전하는 방법

Configuration Manager OS 배포의 디스크 이미지 원본으로 사용하려는 컴퓨터에 Endpoint Protection 클라이언트를 설치합니다. 이 컴퓨터는 일반적으로 참조 컴퓨터라고 합니다. OS 이미지를 만든 다음, Configuration Manager OS 배포를 사용하여 이미지를 배포합니다.

> [!Important]  
> Windows 10 및 Windows Server 2016에는 Windows Defender가 기본적으로 설치되어 있습니다. 해당 Windows 버전에서는 이 절차가 필요하지 않습니다.  

다음 절차에 따라 참조 컴퓨터에 Endpoint Protection 클라이언트를 설치하고 구성할 수 있습니다.


### <a name="prerequisites"></a>필수 구성 요소

다음 목록에는 참조 컴퓨터에 Endpoint Protection 클라이언트 소프트웨어를 설치하는 데 필요한 필수 구성 요소가 포함되어 있습니다.

- Endpoint Protection 클라이언트 설치 패키지(**scepinstall.exe**)에 대한 액세스 권한이 있어야 합니다. 사이트 서버에서 Configuration Manager 설치 폴더의 **Client** 폴더에서 이 패키지를 찾습니다.  

- 조직의 필수 구성으로 Endpoint Protection 클라이언트를 배포하려면 맬웨어 방지 정책을 만들어서 내보냅니다. 그런 다음, Endpoint Protection 클라이언트를 수동으로 설치할 때 이 정책을 지정합니다. 자세한 내용은 [맬웨어 방지 정책을 만들어 배포하는 방법](/sccm/protect/deploy-use/endpoint-antimalware-policies)을 참조하세요.  

  > [!NOTE]  
  >  **기본 클라이언트 맬웨어 방지 정책**은 내보낼 수 없습니다.  

- 최신 정의로 Endpoint Protection 클라이언트를 설치하려는 경우에는 [Windows Defender Security Intelligence](https://www.microsoft.com/wdsi)에서 다운로드합니다.  

> [!NOTE]  
> Configuration Manager 1802부터 Windows 10 디바이스에 Endpoint Protection 에이전트(SCEPInstall)를 설치할 필요가 없습니다. Windows 10 디바이스에 이미 설치되어 있는 경우 Configuration Manager가 제거하지 않습니다. 관리자는 1802 클라이언트 버전 이상이 실행 중인 Windows 10 디바이스에서 Endpoint Protection 에이전트를 제거할 수 있습니다. SCEPInstall.exe가 일부 머신의 C:\Windows\ccmsetup에 여전히 있을 수 있지만 새 클라이언트 설치 시 다운로드하지 않아야 합니다. <!--503654-->


### <a name="how-to-install-the-endpoint-protection-client-on-the-reference-computer"></a>참조 컴퓨터에 Endpoint Protection 클라이언트를 설치하는 방법

명령 프롬프트에서 Endpoint Protection 클라이언트를 참조 컴퓨터에 로컬로 설치합니다. 먼저 설치 파일 **scepinstall.exe**을 가져옵니다. 자세한 내용은 [명령 프롬프트에서 Endpoint Protection 클라이언트를 설치](#bkmk_manual-install)를 참조하세요.

필요한 경우 미리 구성된 맬웨어 방지 정책이나 이전에 내 보낸 맬웨어 방지 정책도 포함시킵니다. 



## <a name="bkmk_manual-install"></a> 명령 프롬프트에서 Endpoint Protection 클라이언트를 설치하려면

1. Configuration Manager 설치 폴더의 **Client** 폴더에서 Endpoint Protection 클라이언트 소프트웨어를 설치하려는 컴퓨터로 **scepinstall.exe**를 복사합니다.  

2. 관리자 권한으로 명령 프롬프트를 엽니다. 설치 관리자가 있는 폴더로 디렉터리를 변경합니다. 그런 다음, 필요한 추가 명령줄 속성이 있으면 추가하고 `scepinstall.exe`를 실행합니다.


   |  속성   |                                  설명                                   |
   |-------------|--------------------------------------------------------------------------------|
   |    `/s`     |                           설치 관리자를 자동으로 실행                           |
   |    `/q`     |                        설치 파일을 자동으로 추출                        |
   |    `/i`     |                           설치 관리자를 정상적으로 실행                           |
   |  `/policy`  | 설치 중에 클라이언트를 구성할 맬웨어 방지 정책 파일을 지정 |
   | `/sqmoptin` |     Microsoft CEIP(사용자 환경 개선 프로그램)에 옵트인(opt in)     |


3. 화면의 지시를 따라 클라이언트 설치를 완료합니다.  

4. 최신 업데이트 정의 패키지를 다운로드한 경우 이 패키지를 클라이언트 컴퓨터로 복사한 다음 정의 패키지를 두 번 클릭하여 설치합니다.  

   > [!NOTE]  
   >  Endpoint Protection 클라이언트 설치를 완료하면 클라이언트에서 자동으로 정의 업데이트 확인을 수행합니다. 이 업데이트 확인에 성공하면 최신 정의 업데이트 패키지를 수동으로 설치하지 않아도 됩니다.  

#### <a name="example-install-the-client-with-an-antimalware-policy"></a>예: 맬웨어 방지 정책으로 클라이언트 설치

`scepinstall.exe /policy <full path>\<policy file>`



## <a name="verify-the-endpoint-protection-client-installation"></a>Endpoint Protection 클라이언트 설치 확인

참조 컴퓨터에 Endpoint Protection 클라이언트를 설치한 후 클라이언트가 제대로 작동하는지 확인합니다.

1.  참조 컴퓨터의 Windows 알림 영역에서 **System Center Endpoint Protection**을 엽니다.  

2.  **System Center Endpoint Protection** 대화 상자의 **홈** 탭에서 **실시간 보호**가 **설정**으로 설정되었는지 확인합니다.  

3.  **바이러스 및 스파이웨어 정의**에 대해 **최신 상태**가 표시되는지 확인합니다.  

4.  참조 컴퓨터가 이미징 준비가 되었는지 확인하려면 **검사 옵션**아래에서 **전체**를 선택한 다음, **지금 검사**를 클릭합니다.  



## <a name="prepare-the-endpoint-protection-client-for-imaging"></a>이미징을 위해 Endpoint Protection 클라이언트 준비

다음 단계를 수행하여 이미징을 위해 Endpoint Protection 클라이언트를 준비합니다.

1. 참조 컴퓨터에서 관리자로 로그인합니다.  

2. [Windows SysInternals](https://docs.microsoft.com/sysinternals/downloads/psexec)에서 **PsExec**를 다운로드하여 설치합니다.  

3. 관리자로 명령 프롬프트를 실행하고 PsTools를 설치한 폴더로 디렉터리를 변경한 다음, 다음 명령을 입력합니다.  

   `psexec.exe -s -i regedit.exe`  

   > [!IMPORTANT]  
   >  이 방식으로 레지스트리 편집기를 실행하는 경우에는 주의해야 합니다. PsExec.exe는 LocalSystem 컨텍스트에서 실행됩니다.  

4. 레지스트리 편집기에서 다음 레지스트리 키를 삭제합니다.  

   > [!IMPORTANT]  
   >  참조 컴퓨터를 이미징하기 전의 마지막 단계로 이 레지스트리 키를 삭제합니다. Endpoint Protection 클라이언트가 시작할 때 이 키를 다시 만듭니다. 참조 컴퓨터를 다시 시작하는 경우 레지스트리 키를 다시 삭제합니다.  

   -   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\InstallTime`  

   -   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanRun`  

   -   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanType`  

   -   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastQuickScanID`   

   -   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastFullScanID`  

   -   `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RemovalTools\MRT\GUID`

이제 이미징을 위해 참조 컴퓨터를 준비할 준비가 되었습니다.

Endpoint Protection 클라이언트가 포함된 OS 이미지를 배포하는 경우에는 디바이스의 할당된 Configuration Manager 사이트에 정보가 자동으로 보고됩니다. 클라이언트는 대상으로 하는 모든 맬웨어 방지 정책을 다운로드하여 적용합니다.  



## <a name="see-also"></a>참고 항목

Configuration Manager에서 OS 배포에 대한 자세한 내용은 [OS 이미지 관리](/sccm/osd/get-started/manage-operating-system-images)를 참조하세요.

