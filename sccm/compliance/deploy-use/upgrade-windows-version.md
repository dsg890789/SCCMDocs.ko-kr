---
title: Windows 디바이스를 다른 버전으로 업그레이드
titleSuffix: Configuration Manager
description: Configuration Manager를 사용하여 Windows 10 Desktop 또는 Windows 10 Mobile을 실행하는 디바이스를 다른 버전으로 자동 업그레이드합니다.
ms.date: 06/07/2019
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 87105e2f9fa090c171b35ed4cb8a6523c624eca4
ms.sourcegitcommit: 0bd336e11c9a7f2de05656496a1bc747c5630452
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834842"
---
# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 버전 업그레이드 정책을 사용하여 Windows 디바이스 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*


**버전 업그레이드 정책**을 사용하면 다음 Windows 10 버전 중 하나를 실행하는 디바이스를 다른 버전으로 자동 업그레이드할 수 있습니다.

- Windows 10 Desktop
- Windows 10 Mobile

지원되는 업그레이드 경로는 다음과 같습니다.

- Windows 10 Pro에서 Windows 10 Enterprise로 업그레이드
- Windows 10 Home에서 Windows 10 Education으로 업그레이드
- Windows 10 Mobile에서 Windows 10 Mobile Enterprise로 업그레이드

디바이스를 Microsoft Intune에 등록하거나 Configuration Manager 클라이언트 소프트웨어를 실행해야 합니다. 이 정책은 현재 온-프레미스 MDM에서 관리되는 PC와 호환되지 않습니다.

## <a name="before-you-start"></a>시작하기 전에  
 디바이스를 최신 버전으로 업그레이드하기 전에 다음과 같은 필수 구성 요소를 검토합니다.  

-   Windows 10의 데스크톱 버전의 경우: 정책으로 대상을 지정하는 모든 디바이스에서 새 버전의 Windows에 유효한 제품 키 이 제품 키는 MAK(복수 정품 인증 키) 또는 GVLK(일반 볼륨 라이선스 키)일 수 있습니다. GVLK는 또한 KMS(키 관리 서비스) 클라이언트 설정 키라고도 합니다. 자세한 내용은 [볼륨 활성화 계획](https://docs.microsoft.com/windows/deployment/volume-activation/plan-for-volume-activation-client)을 참조하세요. KMS 클라이언트 설정 키의 목록은 Windows Server 정품 인증 가이드의 [부록 A](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys)를 참조하세요. <!--496871-->  

-   Windows 10 Mobile의 경우: VLSC(Microsoft 볼륨 라이선스 서비스 센터)의 XML 라이선스 파일 이 파일에는 정책으로 대상을 지정하는 모든 디바이스에서 새 버전의 Windows에 대한 라이선스 정보가 있습니다.

- 이 정책 유형을 관리하려면 Configuration Manager **전체 관리자** 보안 역할이 있어야 합니다.

## <a name="configure-the-edition-upgrade-policy"></a>버전 업그레이드 정책 구성  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **Windows 10 버전 업그레이드**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **버전 업그레이드 정책 만들기**를 클릭합니다.  

4.  **정책 만들기**를 클릭합니다.  

5.  **버전 업그레이드 정책 만들기 마법사** 의 **일반**페이지에서 다음 정보를 지정합니다.  

    -   **이름** - 버전 업그레이드 정책의 이름을 입력합니다.  

    -   **설명** (선택 사항) - 필요에 따라 Intune 콘솔에서 식별하는 데 도움이 되는 정책 설명을 입력합니다.  

    -   **디바이스를 업그레이드할 SKU** - 드롭다운 목록에서 Windows 10 Desktop 또는 Windows 10 Mobile의 대상 버전을 선택합니다.  

    -   **라이선스 정보** - 다음 중 하나를 선택합니다.  

        -   **제품 키** - 대상 Windows 10 Desktop 버전에 대한 유효한 제품 키를 입력합니다.  

            > [!NOTE]  
            >  제품 키가 포함된 정책을 만든 후에는 나중에 제품 키를 편집할 수 없습니다. Configuration Manager는 보안 상의 이유로 키를 가립니다. 제품 키를 변경하려면 전체 키를 다시 입력해야 합니다.  

        -   **라이선스 파일** - **찾아보기**를 클릭하여 XML 형식의 유효한 라이선스 파일을 선택합니다. Configuration Manager는 이 라이선스 파일을 사용하여 Windows 10 Mobile 디바이스를 업그레이드합니다.  

6.  마법사를 완료합니다.  


## <a name="deploy-the-edition-upgrade-policy"></a>버전 업그레이드 정책 배포  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **Windows 10 버전 업그레이드**를 클릭합니다.  

3.  배포할 Windows 10 버전 업그레이드 정책을 선택한 다음 **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

4.  **Windows 10 버전 업그레이드 배포** 대화 상자에서 정책을 배포하려는 컬렉션을 선택합니다. 클라이언트가 정책을 평가하는 일정을 선택하고 **확인**을 클릭합니다. Configuration Manager 클라이언트를 사용하여 관리되는 PC의 경우 디바이스 컬렉션에 정책을 배포해야 합니다. Intune에 등록된 PC의 경우 사용자 또는 디바이스 컬렉션에 정책을 배포할 수 있습니다. 



## <a name="next-steps"></a>다음 단계

**모니터링** 작업 영역의 **배포** 노드에서 이 배포를 모니터합니다. 다음 예와 같이 실패한 배포가 실패했음을 나타내는 오류가 표시되는 경우
- **이 디바이스에 해당 없음**
- **데이터 형식 변환 실패**

이러한 오류가 배포 실패를 의미하지는 않습니다. 대상 PC에서 업그레이드가 성공적으로 실행되었는지 확인합니다.

클라이언트가 대상 정책을 평가하면 2시간 이내에 업그레이드를 적용합니다. [특정 업그레이드 경로에서 시스템을 다시 시작해야 할 경우](https://docs.microsoft.com/windows/deployment/upgrade/windows-10-edition-upgrades) 해당 시점에서 다시 시작됩니다. 정책을 배포할 모든 사용자에게 알리거나 사용자의 근무 시간 외에 정책이 실행되도록 예약해야 합니다.

클라이언트의 **DcmWmiProvider.log**에 다음 오류가 나타나면 정품 인증 시나리오에 적절한 키를 사용하고 있는지 확인합니다. 자세한 내용은 [시작하기 전에](#before-you-start) 섹션을 참조하세요. 정품 인증에 키 관리 서비스를 사용하는 경우 [KMS 클라이언트 설치 키](https://docs.microsoft.com/windows-server/get-started/kmsclientkeys)를 사용해야 합니다.  <!-- 496871 -->   

`Failed to execute CheckApplicabilityMethod with error = 0x80041001 OsEditionUpgradeProvider`
