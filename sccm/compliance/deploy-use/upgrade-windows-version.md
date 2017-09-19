---
title: "Configuration Manager를 사용하여 Windows 장치를 다른 버전으로 업그레이드 | Microsoft Docs"
description: "Configuration Manager를 사용하여 Windows 10 Desktop, Windows 10 Mobile 또는 Windows 10 Holographic을 실행하는 장치를 최신 버전으로 자동으로 업그레이드합니다."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b0c9db74-841e-46eb-8924-957cde968bf7
caps.latest.revision: "8"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 89b0b89ae6acfb6e9d82dfb6d233fe131969924c
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/15/2017
---
# <a name="upgrade-windows-devices-with-the-edition-upgrade-policy-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 버전 업그레이드 정책을 사용하여 Windows 장치 업그레이드

*적용 대상: System Center Configuration Manager(현재 분기)*


System Center Configuration Manager **버전 업그레이드 정책**을 사용하면 다음 Windows 10 버전 중 하나를 실행하는 장치를 다른 버전으로 자동으로 업그레이드할 수 있습니다.

- Windows 10 Desktop
- Windows 10 Mobile
<!-- - Windows 10 Holographic -->

지원되는 업그레이드 경로는 다음과 같습니다.

- Windows 10 Pro에서 Windows 10 Enterprise로 업그레이드
- Windows 10 Home에서 Windows 10 Education으로 업그레이드
- Windows 10 Mobile에서 Windows 10 Mobile Enterprise로 업그레이드
<!-- - From Windows 10 Holographic Pro to Windows 10 Holographic Enterprise -->

장치를 Microsoft Intune에 등록하거나 Configuration Manager 클라이언트 소프트웨어를 실행해야 합니다. 이 정책은 현재 온-프레미스 MDM에서 관리되는 PC와 호환되지 않습니다.

## <a name="before-you-start"></a>시작하기 전에  
 장치를 최신 버전으로 업그레이드하기 전에 다음 중 하나가 있어야 합니다.  

-   데스크톱 운영 체제용 정책에서 대상으로 지정하는 모든 장치에 새 버전의 Windows를 설치하는 데 유효한 제품 키  

-   Windows 10 Mobile<!-- and Windows 10 Holographic-->용 정책에서 대상으로 지정하는 모든 장치에 새 버전의 Windows를 설치하기 위한 라이선스 정보가 포함된 Microsoft 라이선스 파일

- 이 정책 유형을 만들고 배포하려면 Configuration Manager **전체 관리자** 보안 역할이 할당된 상태여야 합니다.

## <a name="configure-the-edition-upgrade-policy"></a>버전 업그레이드 정책 구성  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **Windows 10 버전 업그레이드**를 클릭합니다.  

3.  **홈** 탭의 **만들기** 그룹에서 **버전 업그레이드 정책 만들기**를 클릭합니다.  

4.  **정책 만들기**를 클릭합니다.  

5.  **버전 업그레이드 정책 만들기 마법사** 의 **일반**페이지에서 다음 정보를 지정합니다.  

    -   **이름** - 버전 업그레이드 정책의 이름을 입력합니다.  

    -   **설명** (선택 사항) - 필요에 따라 Intune 콘솔에서 식별하는 데 도움이 되는 정책 설명을 입력합니다.  

    -   **장치를 업그레이드할 SKU** - 드롭다운 목록에서 대상 장치를 업그레이드할 Windows 10 Desktop, <!-- Windows 10 Holographic,--> 또는 Windows 10 Mobile 버전을 선택합니다.  

    -   **라이선스 정보** - 다음 중 하나를 선택합니다.  

        -   **제품 키** - Windows 10 Desktop 운영 체제를 실행하는 대상 장치를 업그레이드하는 데 사용할 유효한 Windows 10 제품 키를 입력합니다.  

            > [!NOTE]  
            >  제품 키가 포함된 정책을 만든 후에는 나중에 제품 키를 편집할 수 없습니다. 보안상 키가 가려지기 때문입니다. 제품 키를 변경하려면 전체 키를 다시 입력해야 합니다.  

        -   **라이선스 파일** - **찾아보기** 를 클릭하여 <!--Windows 10 Holographic and -->Windows 10 Mobile 운영 체제를 실행하는 대상 장치를 업그레이드하는 데 사용할 XML 형식의 유효한 라이선스 파일을 선택합니다.  

6.  마법사를 완료합니다.  

새 정책이 **자산 및 준수** 작업 영역의 **Windows 10 버전 업그레이드** 노드에 표시됩니다.  

## <a name="deploy-the-edition-upgrade-policy"></a>버전 업그레이드 정책 배포  

1.  Configuration Manager 콘솔에서 **자산 및 준수** > **준수 설정** > **Windows 10 버전 업그레이드**를 클릭합니다.  

3.  배포할 Windows 10 버전 업그레이드 정책을 선택한 다음 **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

4.  **Windows 10 버전 업그레이드 배포** 대화 상자에서 정책을 배포할 컬렉션과 정책 평가 일정을 선택한 다음 **확인**을 클릭합니다. Configuration Manager 클라이언트를 사용하여 관리되는 PC의 경우 장치 컬렉션에 정책을 배포해야 합니다. Intune에 등록된 PC의 경우 사용자 또는 장치 컬렉션에 정책을 배포할 수 있습니다. 



## <a name="next-steps"></a>다음 단계

**모니터링** 작업 영역의 **배포** 노드에서 방금 만든 배포를 모니터링하는 경우 다음과 같이 배포가 성공적이지 않음을 나타내는 오류가 표시될 수 있습니다.
- **이 장치에 해당 없음**
- **데이터 형식 변환 실패**

이러한 오류가 배포 실패를 의미하지는 않습니다. 대상 PC에서 업그레이드가 성공적으로 수행되었는지 확인합니다.

정책이 대상 Windows PC에 도달하고 평가되면 2시간 내에 PC가 다시 시작되어 업그레이드를 적용합니다. 정책을 배포할 모든 사용자에게 알리거나 사용자의 근무 시간 외에 정책이 실행되도록 예약해야 합니다.
