---
title: 리소스 액세스 프로필 배포
titleSuffix: Configuration Manager
description: Configuration Manager에서 Wi-Fi, VPN, 메일 및 인증서 프로필을 배포하는 방법을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 3753608d-b539-44dc-8e3f-b631319e7687
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 75c9dd3dccd9ac65a540eb65f2eb802beda1b6c4
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74660889"
---
# <a name="deploy-resource-access-profiles-in-configuration-manager"></a>Configuration Manager에서 리소스 액세스 프로필 배포

*적용 대상: Configuration Manager (현재 분기)*

다음 리소스 액세스 프로필 중 하나를 만든 후 하나 이상의 컬렉션에 배포 합니다.

- [Wi-Fi](/configmgr/protect/deploy-use/create-wifi-profiles)
- [VPN](/configmgr/protect/deploy-use/create-vpn-profiles)
- [전자 메일](/configmgr/mdm/deploy-use/create-exchange-activesync-profiles)
- [인증서](/configmgr/protect/deploy-use/create-certificate-profiles)

이러한 프로필을 배포할 때 대상 컬렉션을 지정 하 고 클라이언트가 준수를 위해 프로필을 평가 하는 빈도를 지정 합니다.  

## <a name="deploy-a-profile"></a>프로필 배포

1. Configuration Manager 콘솔에서 **자산 및 호환성** 작업 영역으로 이동합니다. **호환성 설정**을 확장 하 고 **회사 리소스 액세스**를 확장 한 다음 적절 한 프로필 노드를 선택 합니다. 예를 들어 **Wi-fi 프로필**입니다.

1. 프로필 목록에서 배포 하려는 프로필을 선택 합니다. 그다음에, 리본의 **홈** 탭에 있는 **배포** 그룹에서 **배포**를 선택합니다.  

1. 프로필 배포 창에서 다음 정보를 지정합니다.  

    - **컬렉션**: 프로필을 배포할 컬렉션을 선택합니다.

    - **경고 생성**: 경고를 구성 하려면이 옵션을 사용 하도록 설정 합니다. 이 사이트는 지정 된 날짜 및 시간을 기준으로 프로필 호환성이 지정 된 비율 보다 작은 경우이 경고를 생성 합니다. 경고를 System Center Operations Manager로 전송할지 여부도 선택할 수 있습니다.

    - **임의 지연(시간)** : SCEP(단순 인증서 등록 프로토콜) 설정이 포함된 인증서 프로필의 경우, NDES(네트워크 디바이스 등록 서비스)의 과도한 처리를 방지하려면 지연 기간을 지정합니다. 기본값은 `64`시간입니다.  

    - **이에 대 한 준수 평가 일정을 지정 하세요. 프로필**: 클라이언트가이 프로필에 대 한 호환성을 평가 하는 빈도를 지정 합니다. **간단한 일정** 을 선택 하거나 **사용자 지정 일정**을 구성 하십시오. 기본적으로 단순 일정은 `12` 시간 마다입니다.

1. **확인** 을 선택 하 여 창을 닫고 배포를 만듭니다.

## <a name="delete-a-deployment"></a>배포 삭제

배포를 삭제 하려면 목록에서 배포를 선택 합니다. 세부 정보 창에서 **배포** 탭으로 전환합니다. 배포를 선택한 다음 리본의 **배포** 탭에서 **삭제**를 선택 합니다.

> [!IMPORTANT]
> VPN 프로필 배포를 제거 하면 Configuration Manager Windows에서 VPN 프로필을 제거 하지 않습니다. 디바이스에서 프로필을 제거하려면 수동으로 제거합니다.

## <a name="next-steps"></a>다음 단계

[Wi-fi, VPN 및 전자 메일 프로필 모니터링](/configmgr/protect/deploy-use/monitor-wifi-email-vpn-profiles)

[인증서 프로필 모니터링](/configmgr/protect/deploy-use/monitor-certificate-profiles)
