---
title: 기존 디바이스에 대한 Windows Autopilot
titleSuffix: Configuration Manager
description: Configuration Manager 작업 순서를 사용하여 Windows Autopilot 사용자 기반 모드용으로 Windows 7 디바이스를 이미지로 다시 설치하고 프로비전합니다.
ms.date: 03/05/2019
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 2e96f847-5b5a-4da9-8e8f-6aa488838508
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 31004429493252ddef4b45621695d2fcd275fa36
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75821412"
---
# <a name="windows-autopilot-for-existing-devices"></a>기존 디바이스에 대한 Windows Autopilot
<!--3607717, fka 1358333-->

*적용 대상: Configuration Manager(현재 분기)*

[Windows Autopilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-autopilot)을 통해 조직은 새로운 Windows 10 디바이스를 본래 그대로 최종 사용자에게 제공하며 안전하고 생산성 높은 Windows 10 디바이스를 구성하기 위해 사용자가 수행할 프로비저닝 흐름을 정의할 수 있습니다. 디바이스는 Windows Autopilot 서비스를 통해 등록되므로 필요한 Windows Autopilot 프로필을 할당할 수 있습니다. 이 프로필은 해당 디바이스에 대한 OOBE(첫 실행 경험)를 정의합니다. 

[기존 디바이스에 대한 Windows Autopilot](https://techcommunity.microsoft.com/t5/Windows-IT-Pro-Blog/New-Windows-Autopilot-capabilities-and-expanded-partner-support/ba-p/260430)은 Windows 10 버전 1809 이상에서 사용할 수 있습니다. 이 기능을 사용하면 단일, 네이티브 Configuration Manager 작업 순서를 사용하여 [Windows Autopilot user-driven mode](https://docs.microsoft.com/windows/deployment/windows-autopilot/user-driven)(Windows Autopilot 사용자 기반 모드)용으로 Windows 7 디바이스를 이미지로 다시 설치하고 프로비전할 수 있습니다. 



## <a name="prerequisites"></a>전제 조건

- Windows 10 버전 1809 이상의 설치 미디어를 가져옵니다. 그런 다음, Configuration Manager OS 이미지를 만듭니다. 자세한 내용은 [OS 이미지 관리](/sccm/osd/get-started/manage-operating-system-images)를 참조하세요.

- Microsoft Intune에서 Windows Autopilot 프로필을 만듭니다. 자세한 내용은 [Windows Autopilot을 사용하여 Intune에 Windows 디바이스 등록](https://docs.microsoft.com/intune/enrollment-autopilot)을 참조하세요.

- Windows Autopilot 서비스에 아직 등록되지 않은 디바이스입니다. 디바이스가 이미 등록되어 있으면 할당된 프로필이 우선 적용됩니다. 기존 장치에 대 한 Autopilot 프로필은 온라인 프로필의 시간이 초과 되는 경우에만 적용 됩니다.



## <a name="create-the-configuration-file"></a>구성 파일 만들기

1. 인터넷에 연결된 Windows 디바이스에서 관리 PowerShell 명령 창을 열고 다음 명령을 실행합니다.  

    1. 필요한 모듈을 설치하고 프롬프트를 수락하여 계속합니다.  
        ``` PowerShell  
        Install-Module AzureAD
        Install-Module WindowsAutopilotIntune 
        Import-Module WindowsAutopilotIntune 
        ```

    2. 관리자 자격 증명을 사용하여 Intune에 로그인합니다.  
        ``` PowerShell  
        Connect-AutopilotIntune 
        ```

    3. Intune 테넌트와 연결된 모든 Windows Autopilot 프로필을 검색합니다.  
        ``` PowerShell  
        $AutopilotProfile = Get-AutopilotProfile
        ```

    4. 각 프로필에 대한 구성 파일을 만듭니다. 파일은 프로필의 표시 이름에 따라 이름이 지정되며 현재 사용자의 바탕 화면에 저장됩니다.<!--PowerShell example courtesy of GitHub user treestryder from SCCMDocs issue #1196-->  
        ``` PowerShell  
        $AutopilotProfile | ForEach-Object { $_ | ConvertTo-AutoPilotConfigurationJSON | Set-Content -Encoding Ascii "~\Desktop\$($_.displayName).json" }
        ```  

        > [!Note]  
        > 구성 파일에는 하나의 프로필만 포함될 수 있습니다. 각 프로필은 중괄호(`{}`) 안에 있어야 합니다.  

2. 프로필 중 하나를 **AutopilotConfigurationFile.json**이라는 ANSI 인코딩 파일에 저장합니다. Configuration Manager 패키지 원본으로 적합한 위치에 파일을 저장합니다.  

    > [!Tip]  
    > PowerShell cmdlet **Out-File**을 사용하여 JSON 출력을 파일로 리디렉션하는 경우 기본적으로 유니코드 인코딩을 사용합니다. 이 cmdlet은 긴 줄을 자를 수도 있습니다. **Set-Content** cmdlet을 `-Encoding ASCII` 매개 변수와 함께 사용하여 적절한 텍스트 인코딩을 설정합니다.   
    > 
    > Windows 메모장은 기본적으로 ANSI 인코딩을 사용합니다.  

3. 이 파일을 포함하는 Configuration Manager 패키지를 만듭니다. 프로그램이 필요하지 않습니다. 자세한 내용은 [패키지 만들기](/sccm/apps/deploy-use/packages-and-programs#create-a-package-and-program)를 참조하세요.  

    > [!NOTE]  
    > Windows에서는 이 파일 이름이 **AutopilotConfigurationFile.json**이어야 합니다. 둘 이상의 Autopilot 프로필을 사용하려면 개별 Configuration Manager 패키지를 만듭니다.  



## <a name="create-the-task-sequence"></a>작업 순서 만들기

1. Configuration Manager 콘솔에서 **소프트웨어 라이브러리** 작업 영역으로 이동하고 **운영 체제**를 확장하고 **작업 순서** 노드를 선택합니다. 리본에서 **작업 순서 만들기**를 선택합니다.  

2. **새 작업 순서 만들기** 페이지에서 **기존 디바이스에 대한 Windows Autopilot 배포** 옵션을 선택합니다.  

3. **작업 순서 정보** 페이지에서 이름을 지정하고, 선택적으로 설명을 추가하고, 부팅 이미지를 선택합니다. 지원되는 부팅 이미지 버전에 대한 자세한 내용은 [Windows 10에 대한 지원](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk)을 참조하세요.  

4. **Windows 설치** 페이지에서 Windows 10 **이미지 패키지**를 선택합니다. 그런 다음, 아래 설정을 구성합니다.  

    - **이미지 인덱스**: 조직의 필요에 따라 Enterprise, Education 또는 Professional을 선택합니다.  

    - **운영 체제를 설치하기 전에 대상 컴퓨터 파티션을 만들고 포맷** 옵션을 사용하도록 설정합니다.  

    - **Bitlocker에 사용할 작업 순서 구성**:이 옵션을 사용 하도록 설정 하는 경우 작업 순서에 bitlocker를 사용 하도록 설정 하는 데 필요한 단계가 포함 됩니다.  

    - **제품 키**: Windows 정품 인증을 위한 제품 키를 지정해야 하는 경우 여기에 입력합니다.  

    - 다음 옵션 중 하나를 선택하여 Windows 10에서 로컬 관리자 계정을 구성합니다.  
        - **로컬 관리자 암호를 임의로 생성하고 모든 지원 플랫폼에서 계정 사용 안 함(권장)**
        - **계정을 사용하고 로컬 관리자 암호 지정**

5. **네트워크 구성** 페이지에서 **작업 그룹에 가입** 옵션을 선택합니다. 이 작업 순서에서는 Windows 시스템 준비 도구(Sysprep)를 사용합니다. 디바이스가 도메인에 가입되어 있으면 Sysprep이 실패합니다.  

6. **Configuration Manager 설치** 페이지에서 사용자 환경에 필요한 설치 속성을 추가합니다.  

    > [!Tip]  
    > Sysprep을 실행하기 전 작업 순서가 진행되는 동안 구성 관리자 클라이언트 구성 요소가 필요한 경우에만 작업 순서에서 이 정보가 필요합니다. 소프트웨어 업데이트나 애플리케이션을 설치하는 경우를 예로 들 수 있습니다. 이러한 작업을 수행하지 않는 경우 클라이언트가 필요하지 않습니다. 작업 순서에서 Sysprep을 실행하기 전에 제거됩니다.  

7. **업데이트 포함** 페이지에는 기본적으로 **소프트웨어 업데이트 설치 안 함** 옵션이 선택됩니다.  

    > [!Tip]  
    > 오프라인 이미지 서비스를 사용하여 최신 Windows 10 품질 업데이트를 통해 이미지를 최신 상태로 유지합니다. 자세한 내용은 [OS 이미지에 소프트웨어 업데이트 적용](/sccm/osd/get-started/manage-operating-system-images#BKMK_OSImagesApplyUpdates)을 참조하세요.  

8. **애플리케이션 설치** 페이지에서 작업 순서가 진행되는 동안 설치할 애플리케이션을 선택할 수 있습니다. 그러나 이 시나리오를 사용하여 서명 이미지 접근 방식을 미러링하는 것이 좋습니다. Autopilot을 사용하여 디바이스가 프로비전된 후 Microsoft Intune 또는 Configuration Manager 공동 관리의 모든 애플리케이션 및 구성을 적용합니다. 이 프로세스는 새 디바이스를 받는 사용자와 기존 디바이스에 대한 Windows Autopilot을 사용하는 사용자 간에 일관성 있는 환경을 제공합니다.  

8. **시스템 준비** 페이지에서 Autopilot 구성 파일이 포함된 패키지를 선택합니다. 기본적으로 작업 순서는 Windows Sysprep을 실행한 후 컴퓨터를 다시 시작합니다. **이 작업 순서가 완료된 후 컴퓨터 종료** 옵션을 선택할 수도 있습니다. 이 옵션을 사용하여 디바이스를 준비하고 나서 일관성 있는 Autopilot 환경을 위해 사용자에게 제공할 수 있습니다.  

9. 마법사를 완료합니다.  

작업 순서를 편집하는 것은 기존 OS 이미지를 적용하는 기본 작업 순서와 비슷합니다. 이 작업 순서에는 다음 추가 단계가 포함됩니다.  

- **Windows Autopilot 구성 적용**: 이 단계에서는 지정된 패키지의 Autopilot 구성 파일을 적용합니다. 이 단계는 새로운 형식의 단계가 아니라 파일을 복사하는 **명령줄 실행** 단계입니다.  

- **Windows 캡처 준비**: 이 단계는 Windows Sysprep을 실행하며 **이 작업을 실행한 후 컴퓨터 종료** 설정을 포함하고 있습니다. 자세한 내용은 [Windows 캡처 준비](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareWindowsforCapture)를 참조하세요.  

기존 디바이스에 대한 Windows Autopilot 작업 순서를 진행하면 디바이스가 Azure AD(Azure Active Directory)에 가입됩니다. 

비즈니스용 OneDrive의 [알려진 폴더 이동](https://docs.microsoft.com/onedrive/redirect-known-folders)을 사용하여 Windows 10 업그레이드 전에 사용자 데이터가 백업되도록 해야 합니다.



## <a name="next-steps"></a>다음 단계

공동 관리를 사용하여 Windows 10 디바이스의 관리 기능을 개선하세요. 두 번째 공동 관리 경로는 Windows Autopilot을 통해 최신 프로비저닝을 사용하는 것입니다. 자세한 내용은 다음 아티클을 참조하세요.

- [What is co-management?](/sccm/comanage/overview)(공동 관리란?)
- [Paths to co-management](/sccm/comanage/quickstart-paths)(공동 관리 경로)
- [Windows Autopilot with co-management](/sccm/comanage/quickstart-autopilot)(공동 관리가 포함된 Windows Autopilot)

## <a name="see-also"></a>참고 항목

- [Windows Autopilot을 사용하여 Intune에 Windows 디바이스 등록](https://docs.microsoft.com/intune/enrollment-autopilot)
