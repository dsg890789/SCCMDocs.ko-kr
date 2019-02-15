---
title: Wi-Fi, VPN, 메일 및 인증서 프로필 배포
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 Wi-Fi, VPN, 메일 및 인증서 프로필을 배포하는 방법을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 3753608d-b539-44dc-8e3f-b631319e7687
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.collection: M365-identity-device-management
ms.openlocfilehash: 63b52b42a9957ed8728d0942988067fef2be6271
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56129717"
---
# <a name="deploy-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager의 프로필 배포

*적용 대상: System Center Configuration Manager(현재 분기)*

프로필을 사용하려면 먼저 하나 이상의 컬렉션에 배포해야 합니다.  

 **Wi-Fi 프로필 배포**, **VPN 프로필 배포**, **Exchange ActiveSync 프로필 배포** 또는 **인증서 프로필 배포** 대화 상자를 사용하여 이러한 프로필의 배포를 구성합니다. 구성 과정에서, 프로필을 배포할 컬렉션을 정의하고 준수와 관련하여 프로필을 평가할 빈도를 지정합니다.  

> [!NOTE]
>  동일한 사용자에게 여러 회사 리소스 액세스 프로필을 배포하는 경우 다음 동작이 수행됩니다.  
> 
> - 충돌하는 설정에 선택적 값이 포함된 경우 이 값은 디바이스에 전송되지 않습니다.  
>   -   충돌하는 설정에 필수 값이 포함된 경우 기본값이 디바이스에 전송됩니다. 기본값이 없으면 전체 회사 리소스 액세스 프로필이 실패합니다. 예를 들어 **Exchange ActiveSync 호스트** 또는 **전자 메일 주소** 에 대해 지정된 값이 다른 전자 메일 프로필 두 개를 동일한 사용자에게 배포할 경우 이는 필수 설정이므로 두 전자 메일 프로필이 모두 실패합니다.  
> 
> - 인증서 프로필을 배포하려면 먼저 인프라를 구성하고 인증서 프로필을 만들어야 합니다. 자세한 내용은 다음 항목을 참조하세요.  
> 
>   -   [System Center Configuration Manager에서 인증서 인프라 구성](certificate-infrastructure.md)  
> - [System Center Configuration Manager에서 인증서 프로필을 만드는 방법](create-certificate-profiles.md)    
> 
> [!IMPORTANT]
>  VPN 프로필 배포를 제거할 경우 클라이언트 디바이스에서는 VPN 프로필이 제거되지 않습니다. 디바이스에서 프로필을 제거하려면 수동으로 제거해야 합니다.

## <a name="deploying--profiles"></a>프로필 배포  


1.  System Center Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.  

2.  **자산 및 준수** 작업 영역에서 **준수 설정**을 확장하고 **회사 리소스 액세스**를 확장한 다음 **Wi-Fi 프로필**과 같은 적절한 프로필 유형을 선택합니다.  

3.  프로필 목록에서 배포하려는 프로필을 선택하고 **홈** 탭의 **배포** 그룹에서 **배포**를 클릭합니다.  

4.  프로필 배포 대화 상자에서 다음 정보를 지정합니다.  

    -   **컬렉션** – **찾아보기**를 클릭하여 프로필을 배포할 컬렉션을 선택합니다.  

    -   **경고 생성** - 지정된 날짜 및 시간을 기준으로 프로필 준수가 지정된 비율에 못 미치는 경우에 생성되는 경고를 구성하려면 이 옵션을 사용합니다. 경고를 System Center Operations Manager로 전송할지 여부도 지정할 수 있습니다.  

    -   -   **임의 지연(시간)**: (단순 인증서 등록 프로토콜 설정이 포함된 인증서 프로필에 대한 경우에만) 네트워크 디바이스 등록 서비스의 과도한 처리를 방지하려면 지연 기간을 지정합니다. 기본값은 **64** 시간입니다.  

    -   **이 <type> 프로필에 대한 준수 평가 일정 지정** - 클라이언트 컴퓨터에서 배포된 프로필을 평가할 일정을 지정합니다. 단순 일정 또는 사용자 지정 일정 중에서 지정할 수 있습니다.  

        > [!NOTE]  
        >  사용자가 로그온해 있을 때 클라이언트 컴퓨터에서 프로필을 평가합니다.  

5.  **확인**을 클릭하여 대화 상자를 닫고 배포를 만듭니다.

### <a name="see-also"></a>참고 항목  

[System Center Configuration Manager에서 Wi-Fi, VPN 및 메일 프로필을 모니터링하는 방법](monitor-wifi-email-vpn-profiles.md)

[System Center Configuration Manager에서 인증서 프로필을 모니터링하는 방법](monitor-certificate-profiles.md)
