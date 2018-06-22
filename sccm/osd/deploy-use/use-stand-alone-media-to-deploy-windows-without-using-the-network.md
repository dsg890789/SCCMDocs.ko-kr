---
title: 독립 실행형 미디어를 사용하여 네트워크를 사용하지 않고 Windows 배포
titleSuffix: Configuration Manager
description: Configuration Manager의 독립 실행형 미디어를 사용하여 대역폭이 제한된 운영 체제를 배포하거나 컴퓨터를 새로 고치거나 설치 또는 업그레이드하는 옵션으로 사용할 수 있습니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 58a0d2ae-de76-401f-b854-7a5243949033
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18e50806868955eac807645a5378aea53acdc899
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32348609"
---
# <a name="use-stand-alone-media-to-deploy-windows-without-using-the-network-in-system-center-configuration-manager"></a>독립 실행형 미디어를 사용하여 System Center Configuration Manager에서 네트워크를 사용하지 않고 Windows 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 독립 실행형 미디어에는 컴퓨터에서 운영 체제를 배포하는 데 필요한 모든 항목이 포함되어 있습니다. 여기에는 부팅 이미지 및 운영 체제 이미지와, 응용 프로그램, 드라이버 등을 비롯한 운영 체제를 설치하는 작업 순서가 포함됩니다. 독립 실행형 미디어 배포를 사용하면 다음 상태에서 운영 체제를 배포할 수 있습니다.  

-   운영 체제 이미지 또는 기타 대규모 패키지를 네트워크를 통해 복사하는 것이 불가능한 환경  

-   네트워크 연결이 없거나 대역폭이 낮은 네트워크 연결 환경  

다음과 같은 운영 체제 배포 시나리오에서 독립 실행형 미디어를 사용할 수 있습니다.  

-   [새 버전의 Windows로 기존 컴퓨터 새로 고침](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [새 컴퓨터에 새 버전의 Windows 설치(완전 복구)](install-new-windows-version-new-computer-bare-metal.md)  

-   [최신 버전으로 Windows 업그레이드](upgrade-windows-to-the-latest-version.md)  

 운영 체제 배포 시나리오 중 하나의 단계를 완료하고 다음 섹션을 참조하여 독립 실행형 미디어를 준비하고 만듭니다.  

## <a name="task-sequence-actions-not-supported-when-using-stand-alone-media"></a>독립 실행형 미디어를 사용하는 경우 작업 순서의 작업이 지원 안 됨  
 지원되는 운영 체제 배포 시나리오, 배포할 작업 순서 또는 업그레이드 중 하나의 단계를 완료한 경우 운영 체제가 만들어지고 모든 관련 콘텐츠가 배포 지점에 배포된 것입니다. 독립 실행형 미디어를 사용하면 작업 순서에서 다음 작업 지원되지 않습니다.  

-   작업 순서의 드라이버 자동 적용 단계. 드라이버 카탈로그에서 장치 드라이버 자동 적용은 지원되지 않지만 Windows 설치 프로그램에서 지정된 드라이버 집합을 사용할 수 있도록 드라이버 패키지 적용 단계를 선택할 수 있습니다.  

-   소프트웨어 업데이트 설치  

-   운영 체제 배포 전 소프트웨어 설치  

-   사용자를 대상 컴퓨터와 연결하여 사용자 장치 선호도 지원  

-   동적 패키지는 패키지 설치 작업을 통해 설치됩니다.  

-   동적 응용 프로그램은 응용 프로그램 설치 작업을 통해 설치됩니다.  

> [!NOTE]  
>  운영 체제를 배포하는 작업 순서에 [패키지 설치](../understand/task-sequence-steps.md#BKMK_InstallPackage) 단계가 포함되어 있고 중앙 관리 사이트에서 독립 실행형 미디어를 만들면 오류가 발생할 수 있습니다. 중앙 관리 사이트에는 작업 순서를 실행하는 동안 소프트웨어 배포 에이전트를 사용하도록 설정하는 데 필요한 필수 클라이언트 구성 정책이 없습니다. CreateTsMedia.log 파일에 다음 오류가 나타날 수 있습니다.  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`
>   
>  **패키지 설치** 단계가 포함된 독립 실행형 미디어를 사용할 경우 소프트웨어 배포 에이전트를 사용하도록 설정된 기본 사이트에 독립 실행형 미디어를 만들거나 작업 순서에서 [Windows 및 ConfigMgr 설치](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) 단계와 첫 번째 **패키지 설치** 단계 사이에 [명령줄 실행](../understand/task-sequence-steps.md#BKMK_RunCommandLine) 단계를 추가해야 합니다. **명령줄 실행** 단계에서는 WMIC 명령을 실행하여 첫 번째 패키지 설치 단계가 실행되기 전에 소프트웨어 배포 에이전트를 사용하도록 설정합니다. **명령줄 실행** 작업 순서 단계에서 다음을 사용할 수 있습니다.  
>   
>  **명령줄**: **WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE**  

## <a name="configure-deployment-settings"></a>배포 설정 구성  
 독립 실행형 미디어를 사용하여 운영 체제 배포 프로세스를 시작할 경우 해당 운영 체제를 미디어에서 사용할 수 있도록 배포를 구성해야 합니다. 소프트웨어 배포 마법사의 **배포 설정** 페이지 또는 배포에 대한 속성의 **배포 설정** 탭에서 이를 구성할 수 있습니다.  **다음에 사용 가능하도록 설정** 설정에 대해 다음 중 하나를 구성합니다.  

-   **Configuration Manager 클라이언트, 미디어 및 PXE**  

-   **미디어 및 PXE만**  

-   **미디어 및 PXE만(숨김)**  

## <a name="create-the-stand-alone-media"></a>독립 실행형 미디어 만들기  
 독립 실행형 미디어가 USB 플래시 드라이브인지 아니면 CD/DVD 세트인지를 지정할 수 있습니다. 미디어를 시작하는 컴퓨터는 부팅 가능한 드라이브로 선택하는 옵션을 지원해야 합니다. 자세한 내용은 [독립 실행형 미디어 만들기](create-stand-alone-media.md)를 참조하세요.  

## <a name="install-the-operating-system-from-stand-alone-media"></a>독립 실행형 미디어에서 운영 체제 설치  
 컴퓨터에서 부팅 가능한 드라이브에 독립 실행형 미디어를 삽입한 다음 전원을 켜서 운영 체제를 설치합니다.  
