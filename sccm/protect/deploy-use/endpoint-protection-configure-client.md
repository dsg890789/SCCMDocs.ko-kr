---
title: Endpoint Protection 클라이언트 구성
titleSuffix: Configuration Manager
description: 계층 구조의 컴퓨터 컬렉션에 배포할 수 있는 Endpoint Protection용 사용자 지정 클라이언트 설정을 구성하는 방법을 알아봅니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: e63f2394-6eb1-4a33-bec5-8377fc62a34e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 10572c367dcdc70bf9c708d3a6bb514c0afa2b24
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="configure-custom-client-settings-for-endpoint-protection"></a>Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성

*적용 대상: System Center Configuration Manager(현재 분기)*

이 절차에서는 계층 구조의 컴퓨터 컬렉션에 배포할 수 있는 Endpoint Protection에 대한 사용자 지정 클라이언트 설정을 구성합니다.

> [!IMPORTANT]
>  확실히 계층 구조의 모든 컴퓨터에 적용하려면 기본 Endpoint Protection 클라이언트 설정만 구성합니다. 

## <a name="to-enable-endpoint-protection-and-configure-custom-client-settings"></a>Endpoint Protection을 사용하도록 설정하고 사용자 지정 클라이언트 설정을 구성하려면

1.  Configuration Manager 콘솔에서 **관리**를 클릭합니다.

2.  **관리** 작업 영역에서 **클라이언트 설정**을 클릭합니다.

3.  **홈** 탭의 **만들기** 그룹에서 **사용자 지정 클라이언트 장치 설정 만들기**를 클릭합니다.

4.  **사용자 지정 클라이언트 장치 설정 만들기** 대화 상자에서 설정 그룹의 이름과 설명을 지정하고 **Endpoint Protection**을 선택합니다.

5.  필요한 Endpoint Protection 클라이언트 설정을 구성합니다. 구성할 수 있는 전원 관리 클라이언트 설정의 전체 목록은 [System Center Configuration Manager의 클라이언트 설정 정보](../../core/clients/deploy/about-client-settings.md)의 Endpoint Protection 섹션을 참조하세요.

   > [!IMPORTANT]
   >  Endpoint Protection용 클라이언트 설정을 구성하려면 먼저 Endpoint Protection 사이트 시스템 역할을 설치해야 합니다.

6.  **확인** 을 클릭하여 **사용자 지정 클라이언트 장치 설정 만들기** 대화 상자를 닫습니다. 새 클라이언트 설정이 **관리** 작업 영역의 **클라이언트 설정** 노드에 표시됩니다.

7.  사용자 지정 클라이언트 설정을 사용하려면 먼저 컬렉션에 배포해야 합니다. 배포하려는 사용자 지정 클라이언트 설정을 선택하고 **홈** 탭의 **클라이언트 설정** 그룹에서 **배포**를 클릭합니다.

8.  **컬렉션 선택** 대화 상자에서 클라이언트 설정을 배포할 컬렉션을 선택하고 **확인**을 클릭합니다. 새 배포가 세부 정보 창의 **배포** 탭에 표시됩니다.

클라이언트 컴퓨터는 다음에 클라이언트 정책을 다운로드할 때 이 설정으로 구성됩니다. 단일 클라이언트에 대해 정책 검색을 시작하려면 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../core/clients/manage/manage-clients.md)에서 Configuration Manager 클라이언트에 대한 정책 검색 시작 섹션을 참조하세요.

## <a name="how-to-provision-the-endpoint-protection-client-in-a-disk-image-in-configuration-manager"></a>Configuration Manager에서 디스크 이미지의 Endpoint Protection 클라이언트 프로비전 방법
Configuration Manager 운영 체제 배포의 디스크 이미지 원본으로 사용하려는 컴퓨터에 Endpoint Protection 클라이언트를 설치할 수 있습니다. 이 컴퓨터는 일반적으로 참조 컴퓨터라고 합니다. 운영 체제 이미지를 만든 다음 Configuration Manager 운영 체제 배포를 사용하여 Endpoint Protection과 같은 소프트웨어 패키지를 포함할 수 있는 이미지를 클라이언트 컴퓨터에 배포할 수 있습니다.

이 문서의 절차는 참조 컴퓨터에서 Endpoint Protection 클라이언트를 설치하고 구성하는 방법을 설명합니다.

### <a name="prerequisites-for-installing-the-endpoint-protection-client-on-the-reference-computer"></a>참조 컴퓨터에 Endpoint Protection 클라이언트를 설치하는 데 필요한 필수 구성 요소
다음 목록에는 참조 컴퓨터에 Endpoint Protection 클라이언트 소프트웨어를 설치하는 데 필요한 필수 구성 요소가 포함되어 있습니다.

-   Endpoint Protection 클라이언트 설치 패키지(**scepinstall.exe**)에 대한 액세스 권한이 있어야 합니다. 이 패키지는 사이트 서버에서 Microsoft System Center Configuration Manager 설치 폴더의 **Client** 폴더에서 찾을 수 있습니다. Windows 10 및 Windows Server 2016에는 Windows Defender가 설치되어 있습니다. 

-   조직에 필요한 구성으로 Endpoint Protection 클라이언트를 배포하려면 맬웨어 방지 정책을 만든 다음 해당 정책을 내보냅니다. 그런 다음 수동으로 Endpoint Protection 클라이언트를 설치할 때 맬웨어 방지 정책을 사용하도록 지정할 수 있습니다. 자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)을 참조하세요.

   > [!NOTE]
   >  **기본 클라이언트 맬웨어 방지 정책**은 내보낼 수 없습니다.

-   최신 정의를 사용하여 Endpoint Protection 클라이언트를 설치하려면 [Microsoft 맬웨어 보호 센터](http://go.microsoft.com/fwlink/?LinkID=200965)에서 최신 정의를 다운로드해야 합니다.

>[!NOTE]
> Configuration Manager 1802부터 Windows 10 장치에 Endpoint Protection 에이전트(SCEPInstall)를 설치할 필요가 없습니다. Windows 10 장치에 이미 설치되어 있는 경우 Configuration Manager는 에이전트를 제거하지 않습니다. 관리자는 1802 클라이언트 버전 이상이 실행 중인 Windows 10 장치에서 Endpoint Protection 에이전트를 제거할 수 있습니다. SCEPInstall.exe는 동일한 컴퓨터의 C:\Windows\ccmsetup 위치에 여전히 있을 수 있지만 새 클라이언트 설치 시 다운로드할 수 없습니다. <!--503654-->
### <a name="how-to-install-the-endpoint-protection-client-software-on-the-reference-computer"></a>참조 컴퓨터에 Endpoint Protection 클라이언트 소프트웨어를 설치하는 방법
명령 프롬프트에서 참조 컴퓨터에 로컬로 Endpoint Protection 클라이언트를 설치할 수 있습니다. 그렇게 하려면 먼저 설치 파일( **scepinstall.exe**)을 구해야 합니다. 미리 구성한 맬웨어 방지 정책이나 이전에 내보낸 맬웨어 방지 정책을 사용하여 클라이언트를 설치할 수도 있습니다.

## <a name="to-install-the-endpoint-protection-client-from-a-command-prompt"></a>명령 프롬프트에서 Endpoint Protection 클라이언트를 설치하려면

1.  System Center Configuration Manager 설치 미디어의 **Client** 폴더에서 Endpoint Protection 클라이언트 소프트웨어를 설치하려는 컴퓨터로 **scepinstall.exe**를 복사합니다.

2.  관리자 권한으로 명령 프롬프트를 열고 **scepinstall.exe**가 있는 폴더로 이동한 후 필요한 추가 명령줄 속성을 추가하여 다음 명령을 실행합니다.

   ```
   scepinstall.exe
   ```

    다음 명령줄 속성 중 하나를 지정할 수 있습니다.

   |속성|설명|
   |--------------|-----------------|
   |/s|자동 설치를 수행하도록 지정합니다.|
   |/q|설치 파일 자동 추출을 수행하도록 지정합니다.|
   |/i|일반 설치를 수행하도록 지정합니다.|
   |/noreplace|설치 중에 타사 맬웨어 방지 소프트웨어를 설치하지 않도록 지정합니다.|
   |/policy|설치 중에 클라이언트를 구성하는 데 사용할 맬웨어 방지 정책을 지정합니다.|
   |/sqmoptin|이 클라이언트 소프트웨어를 Microsoft 사용자 환경 개선 프로그램에 가입하도록 지정합니다.|

3.  클라이언트 설치를 완료하려면 화면의 지시를 따릅니다.

4.  최신 업데이트 정의 패키지를 다운로드한 경우 이 패키지를 클라이언트 컴퓨터로 복사한 다음 정의 패키지를 두 번 클릭하여 설치합니다.

   > [!NOTE]
   >  Endpoint Protection 클라이언트 설치를 완료하면 클라이언트에서 자동으로 정의 업데이트 확인을 수행합니다. 이 업데이트 확인에 성공하면 최신 정의 업데이트 패키지를 수동으로 설치하지 않아도 됩니다.

## <a name="to-install-the-client-software-with-an-antimalware-policy-from-the-command-prompt"></a>명령 프롬프트에서 맬웨어 방지 정책이 있는 클라이언트 소프트웨어를 설치하려면

1.  Endpoint Protection 클라이언트 소프트웨어를 설치할 컴퓨터로 **scepinstall.exe** 및 내보냈거나 미리 구성한 맬웨어 방지 정책을 복사합니다.

2.  관리자 권한으로 명령 프롬프트를 열고 **scepinstall.exe** 와 맬웨어 방지 정책이 있는 폴더로 이동한 후 다음 명령을 실행합니다.

   ```
   scepinstall.exe /policy <full path>\<policy file>
   ```

3.  클라이언트 설치를 완료하려면 화면의 지시를 따릅니다.

4.  최신 정의 패키지를 다운로드한 경우 이 패키지를 클라이언트 컴퓨터로 복사한 다음 정의 패키지를 두 번 클릭하여 설치합니다.

   > [!NOTE]
   >  Endpoint Protection 클라이언트 설치를 완료하면 클라이언트에서 자동으로 정의 업데이트 확인을 수행합니다. 이 업데이트 확인에 성공하면 최신 정의 업데이트 패키지를 수동으로 설치하지 않아도 됩니다.

## <a name="verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Endpoint Protection 클라이언트가 올바르게 설치되었는지 확인
참조 컴퓨터에 Endpoint Protection 클라이언트를 설치한 후 클라이언트가 제대로 작동하는지 확인합니다.

### <a name="to-verify-that-the-endpoint-protection-client-is-installed-correctly"></a>Endpoint Protection 클라이언트가 올바르게 설치되었는지 확인하려면

1.  참조 컴퓨터의 Windows 알림 영역에서 **System Center Endpoint Protection**을 엽니다.

2.  **System Center Endpoint Protection** 대화 상자의 **홈** 탭에서 **실시간 보호**가 **설정**으로 설정되었는지 확인합니다.

3.  **바이러스 및 스파이웨어 정의**에 대해 **최신 상태**가 표시되는지 확인합니다.

4.  참조 컴퓨터가 이미징을 위해 준비되었는지 확인하려면 **검사 옵션**아래에서 **전체**를 선택한 다음 **지금 검사**를 클릭합니다.

### <a name="how-to-prepare-the-endpoint-protection-client-for-imaging"></a>Endpoint Protection 클라이언트에서 이미징을 준비하는 방법
참조 컴퓨터에 Endpoint Protection 클라이언트가 올바르게 설치되었는지 확인한 후 참조 컴퓨터에서 이미징을 준비할 수 있습니다. 다음 단계를 수행하여 이미징에 대한 Endpoint Protection 클라이언트를 준비합니다.


Configuration Manager에서 운영 체제 배포에 대한 자세한 내용은 [System Center Configuration Manager에서 운영 체제 이미지 관리](/sccm/osd/get-started/manage-operating-system-images)를 참조하세요.

### <a name="to-prepare-the-endpoint-protection-client-for-imaging"></a>Endpoint Protection 클라이언트에서 이미징을 준비하려면

1.  참조 컴퓨터에서 관리 권한이 있는 사용자로 로그온합니다.

2.  **PsTools** 를 TechNet의 [Windows SysInternals 사이트](http://go.microsoft.com/fwlink/?LinkId=215263) 에서 다운로드하여 설치합니다.

3.  관리자 권한 명령 프롬프트를 열고 PsTools를 설치한 폴더로 이동한 후 다음 명령을 입력합니다.

   ```
   Psexec.exe -s -i regedit.exe
   ```

   > [!IMPORTANT]
   >  이 방법으로 레지스트리 편집기를 실행하는 동안 경고를 참조하세요. PsExec.exe의 –s 옵션은 LocalSystem 권한으로 레지스트리 편집기를 실행합니다.

4.  레지스트리 편집기에서 다음 각 레지스트리 키로 이동하여 해당 키를 삭제합니다.

   > [!IMPORTANT]
   >  참조 컴퓨터를 이미징하기 전의 마지막 단계로 레지스트리 키를 삭제해야 합니다. 레지스트리 키는 Endpoint Protection 클라이언트가 시작될 때 다시 만들어집니다. 참조 컴퓨터를 다시 시작하는 경우 레지스트리 키를 다시 삭제해야 합니다.

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\InstallTime**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanRun**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastScanType**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastQuickScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft Antimalware\Scan\LastFullScanID**

   -   **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\RemovalTools\MRT\GUID**

앞의 단계를 완료한 후 참조 컴퓨터에서 이미징을 준비할 수 있습니다. Configuration Manager에서 운영 체제 배포에 대한 자세한 내용은 [System Center Configuration Manager에서 운영 체제 이미지 관리](/sccm/osd/get-started/manage-operating-system-images)를 참조하세요.

Endpoint Protection 클라이언트 소프트웨어를 포함하는 이미지가 배포될 때 Endpoint Protection 클라이언트가 컴퓨터가 할당되어 있는 Configuration Manager 사이트에 자동으로 정보를 보고하고 클라이언트 컴퓨터에 적용 가능한 정책이 다운로드되어 적용됩니다.
