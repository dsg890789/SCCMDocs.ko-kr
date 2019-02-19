---
title: '운영 체제 이미지 사용자 지정 '
titleSuffix: Configuration Manager
description: 캡처 및 빌드 작업 순서, 수동 구성 또는 이 둘의 조합을 사용하여 운영 체제 이미지를 사용자 지정할 수 있습니다.
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 95033a9b-ff13-4b70-b1de-bcb25bcb6024
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b18c8e780ac5fa43f3fdf6790c80ed6d38e02e28
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56128741"
---
# <a name="customize-operating-system-images-with-system-center-configuration-manager"></a>System Center Configuration Manager를 사용하여 운영 체제 이미지 사용자 지정

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 운영 체제 이미지는 WIM 파일이며 컴퓨터에 운영 체제를 성공적으로 설치하고 구성하는 데 필요한 참조 파일 및 폴더의 압축된 컬렉션을 나타냅니다. 사용자 지정 운영 체제 이미지는 필요한 모든 운영 체제 파일, 지원 파일, 소프트웨어 업데이트, 도구 및 기타 소프트웨어 앱을 사용하여 구성된 참조 컴퓨터에서 만들어지고 캡처됩니다. 참조 컴퓨터를 수동으로 구성하는 범위는 사용자가 결정합니다. 빌드를 사용하여 참조 컴퓨터의 구성을 완전히 자동화하고 작업 순서를 캡처하거나, 참조 컴퓨터의 특정 부분을 수동으로 구성한 다음 작업 순서를 사용하여 나머지를 자동화하거나, 작업 순서를 사용하지 않고 수동으로 참조 컴퓨터를 구성할 수 있습니다. 다음 섹션은 운영 체제를 사용자 지정하는 데 사용됩니다.

##  <a name="BKMK_PrepareReferenceComputer"></a> 참조 컴퓨터 준비  
 참조 컴퓨터에서 운영 체제 이미지를 캡처하기 전에 고려할 사항이 몇 가지 있습니다.  

###  <a name="BKMK_RefComputerDecide"></a> 자동 구성 또는 수동 구성을 사용할지 결정  
 다음에는 참조 컴퓨터의 자동화된 구성과 수동 구성의 장단점이 나와 있습니다.  

#### <a name="automated-configuration"></a>자동화된 구성  
 **장점**  

- 완전히 자동으로 구성할 수 있으므로 관리자나 사용자가 없어도 됩니다.  

- 작업 순서를 다시 사용하여 다른 참조 컴퓨터의 구성을 높은 신뢰 수준으로 반복할 수 있습니다.  

- 작업 순서를 수정하면 전체 작업 순서를 다시 만들지 않고도 참조 컴퓨터 간에 차이를 둘 수 있습니다.  

  **단점**  

- 작업 순서를 만드는 첫 번째 작업을 만들고 테스트하려면 시간이 오래 걸릴 수 있습니다.  

- 참조 컴퓨터 요구 사항이 크게 변경되면 작업 순서를 다시 만들고 다시 테스트하는 데 시간이 오래 걸릴 수 있습니다.  

#### <a name="manual-configuration"></a>수동 구성  
 **장점**  

- 작업 순서를 만들 필요도 없고 오랫동안 작업 순서를 테스트하고 문제를 해결할 필요도 없습니다.  

- 모든 소프트웨어 패키지(Windows 자체 포함)를 Configuration Manage 패키지에 넣지 않고도 CD에서 바로 설치할 수 있습니다.  

  **단점**  

- 참조 컴퓨터 구성의 정확도는 컴퓨터를 구성하는 관리자나 사용자에 따라 달라집니다.  

- 참조 컴퓨터가 제대로 구성되었는지 계속 확인하고 테스트해야 합니다.  

- 구성 방법을 다시 사용할 수 없습니다.  

- 프로세스 내내 적극적으로 개입할 사람이 필요합니다.  

###  <a name="BKMK_RefComputerConsiderations"></a> 참조 컴퓨터에 대한 고려 사항  
 다음에는 참조 컴퓨터를 구성할 때 고려할 기본 항목이 나와 있습니다.  

-   **배포할 운영 체제**  

     참조 컴퓨터에는 대상 컴퓨터에 배포할 운영 체제가 설치되어 있어야 합니다. 배포할 수 있는 운영 체제에 대한 자세한 내용은 [운영 체제 배포를 위한 인프라 요구 사항](../plan-design/infrastructure-requirements-for-operating-system-deployment.md)을 참조하세요.  

-   **적절한 서비스 팩**  

     참조 컴퓨터에는 대상 컴퓨터에 배포할 운영 체제가 설치되어 있어야 합니다.  

-   **적절한 소프트웨어 업데이트**  

     참조 컴퓨터에서 캡처하는 운영 체제 이미지에 포함할 모든 소프트웨어 애플리케이션을 설치합니다. 캡처한 운영 체제 이미지를 대상 컴퓨터에 배포할 때 소프트웨어 애플리케이션도 설치할 수 있습니다.  

-   **작업 그룹 멤버 자격**  

     참조 컴퓨터는 작업 그룹의 구성원으로 구성해야 합니다.  

-   **Sysprep**  

     Sysprep(시스템 준비) 도구는 다른 배포 도구와 함께 Windows 운영 체제를 새 하드웨어에 설치하는 데 사용할 수 있는 기술입니다. Sysprep은 컴퓨터를 다시 시작할 때 새 컴퓨터 SID(보안 식별자)를 만들도록 컴퓨터를 구성하여 컴퓨터에서 디스크 이미징 또는 고객에게 제공할 항목을 준비합니다. 그 밖에도 Sysprep은 대상 컴퓨터로 복사하면 안 되는 사용자 및 컴퓨터 관련 설정과 데이터를 정리합니다.  

     다음 명령을 실행하면 참조 컴퓨터에서 수동으로 Sysprep을 실행할 수 있습니다.  

     `Sysprep /quiet /generalize /reboot`  

     /generalize 옵션은 Windows 설치에서 시스템 관련 데이터를 제거하도록 Sysprep에 지시합니다. 시스템 관련 정보에는 이벤트 로그, 고유 SID(보안 ID) 및 기타 고유 정보가 포함됩니다. 고유한 시스템 정보를 제거한 후 컴퓨터를 다시 시작합니다.  

     [Windows 캡처 준비](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) 작업 순서 단계나 미디어 캡처를 사용하여 Sysprep을 자동화할 수 있습니다.  

    > [!IMPORTANT]  
    >  [Windows 캡처 준비](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture) 작업 순서 단계는 Sysprep 실행 전에 참조 컴퓨터에서 로컬 관리자 암호를 빈 값으로 다시 설정하려고 시도합니다. **암호는 복잡성을 만족해야 함** 이라는 로컬 보안 정책을 사용하는 경우 이 작업 순서 단계에서 관리자 암호를 다시 설정하지 못합니다. 이 시나리오에서는 작업 순서를 실행하기 전에 이 정책을 사용하지 않도록 설정합니다.  

     Sysprep에 대한 자세한 내용은 [Sysprep(시스템 준비) 기술 참조](http://go.microsoft.com/fwlink/?LinkId=280286)를 참조하세요.  

-   **설치 시나리오의 문제를 줄이는 데 필요한 적절한 도구 및 스크립트**  

     설치 시나리오의 문제를 줄이는 데 필요한 적절한 도구 및 스크립트  

-   **배경 무늬, 브랜딩 및 기본 사용자 프로필과 같은 적절한 바탕 화면 사용자 지정**  

     참조 컴퓨터에서 운영 체제 이미지를 캡처할 때 포함할 바탕 화면 사용자 지정 속성으로 참조 컴퓨터를 구성할 수 있습니다. 바탕 화면 속성에는 배경 무늬, 조직 브랜딩 및 표준 기본 사용자 프로필이 있습니다.  

##  <a name="BKMK_ManuallyBuildReference"></a> 수동으로 참조 컴퓨터 만들기  
 수동으로 참조 컴퓨터를 만들려면 다음 절차를 따르세요.  

> [!NOTE]  
>  수동으로 참조 컴퓨터를 만드는 경우 미디어 캡처를 사용하여 운영 체제 이미지를 캡처할 수 있습니다. 자세한 내용은 [미디어 캡처 만들기](../deploy-use/create-capture-media.md)를 참조하세요.  

#### <a name="to-manually-build-the-reference-computer"></a>수동으로 참조 컴퓨터를 만들려면  

1. 참조 컴퓨터로 사용할 컴퓨터를 확인합니다.  

2. 적절한 운영 체제 및 배포할 운영 체제 이미지를 만드는 데 필요한 기타 모든 소프트웨어로 참조 컴퓨터를 구성합니다.  

   > [!WARNING]  
   >  최소한 적절한 운영 체제와 서비스 팩, 지원 드라이버 및 필수 소프트웨어 업데이트를 설치합니다.  

3. 참조 컴퓨터를 작업 그룹의 구성원으로 구성합니다.  

4. 참조 컴퓨터에서 로컬 관리자 암호를 다시 설정하여 암호 값을 없앱니다.  

5. 다음 명령을 사용하여 Sysprep을 실행합니다.  **sysprep /quiet /generalize /reboot** /generalize 옵션은 Windows 설치에서 시스템 관련 데이터를 제거하도록 Sysprep에 지시합니다. 시스템 관련 정보에는 이벤트 로그, 고유 SID(보안 ID) 및 기타 고유 정보가 포함됩니다. 고유한 시스템 정보를 제거한 후 컴퓨터를 다시 시작합니다.  

   참조 컴퓨터가 준비되면 참조 컴퓨터에서 운영 체제 이미지를 캡처하는 작업 순서를 사용합니다.  자세한 내용은 [기존 참조 컴퓨터에서 운영 체제 이미지 캡처](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_CaptureExistingRefComputer)를 참조하세요.  

##  <a name="BKMK_UseTSToBuildReference"></a> 작업 순서를 사용하여 참조 컴퓨터 만들기  
 운영 체제, 드라이버, 애플리케이션 등에 배포하는 작업 순서를 사용하여 참조 컴퓨터를 만드는 프로세스를 자동화할 수 있습니다.  참조 컴퓨터를 빌드하고 참조 컴퓨터에서 운영 체제 이미지를 캡처하려면 다음 단계를 따르세요.  

-   참조 컴퓨터에서 운영 체제 이미지를 빌드하고 캡처하는 작업 순서를 배포합니다.  자세한 단계는 [작업 순서를 사용하여 참조 컴퓨터 만들기 및 캡처](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md#BKMK_BuildCaptureTS)를 참조하세요.  
