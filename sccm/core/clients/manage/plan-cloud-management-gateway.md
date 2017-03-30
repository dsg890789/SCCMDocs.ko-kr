---
title: "클라우드 관리 게이트웨이 계획 | Microsoft 문서"
description: 
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: arob98
ms.author: angrobe
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: c61769cc97c320452c9ee27a924cb01480e6f33d
ms.lasthandoff: 03/27/2017

---

# <a name="plan-for-cloud-management-gateway-in-configuration-manager"></a>Configuration Manager에서 클라우드 관리 게이트웨이 계획

*적용 대상: System Center Configuration Manager(현재 분기)*

버전 1610부터 클라우드 관리 게이트웨이는 인터넷에서 Configuration Manager 클라이언트를 관리할 수 있는 간단한 방법을 제공합니다. 클라우드 관리 게이트웨이 서비스의 경우 Microsoft Azure에 배포되고 Azure 구독이 필요합니다. 이 서비스는 클라우드 관리 게이트웨이 연결점이라는 새 역할을 사용하여 온-프레미스 Configuration Manager 인프라에 연결합니다. 배포되고 구성된 클라이언트는 내부 개인 네트워크 또는 인터넷에 연결되었는지 여부에 관계없이 온-프레미스 Configuration Manager 사이트 시스템 역할에 액세스할 수 있습니다.

Configuration Manager 콘솔을 사용하여 Azure에 서비스를 배포하고 클라우드 관리 게이트웨이 연결점 역할을 추가하고 클라우드 관리 게이트웨이 트래픽을 허용하도록 사이트 시스템 역할을 구성합니다. 클라우드 관리 게이트웨이는 현재 관리 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.

컴퓨터를 인증하고 서비스의 다른 계층 간 통신을 암호화하려면 클라이언트 인증서 및 SSL(Secure Socket Layer) 인증서가 필요합니다. 클라이언트 컴퓨터는 일반적으로 그룹 정책 적용을 통해 클라이언트 인증서를 받습니다. 역할을 호스트하는 사이트 시스템 서버와 클라이언트 간의 트래픽을 암호화하려면 CA에서 사용자 지정 SSL 인증서를 만들어야 합니다. Configuration Manager에서 클라우드 관리 게이트웨이 서비스를 배포할 수 있도록 Azure에 관리 인증서도 설정해야 합니다.

## <a name="requirements-for-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 요구 사항

-   클라이언트 컴퓨터 및 클라우드 관리 게이트웨이 연결점을 실행하는 사이트 시스템 서버

-   클라이언트 컴퓨터에서 통신 암호화 및 클라우드 관리 게이트웨이 서비스의 ID 인증에 사용되는 내부 CA의 사용자 지정 SSL 인증서

-   클라우드 서비스에 대한 Azure 구독

-   Azure에서 Configuration Manager 인증에 사용되는 Azure 관리 인증서

## <a name="specifications-for-cloud-management-gateway"></a>클라우드 관리 게이트웨이에 대한 사양

- 클라우드 관리 게이트웨이의 각 인스턴스는 클라이언트 4,000개를 지원합니다.
- 가용성을 향상하려면 클라우드 관리 게이트웨이의 인스턴스를 두 개 이상 만드는 것이 좋습니다.
- 클라우드 관리 게이트웨이는 관리 지점 및 소프트웨어 업데이트 지점 역할만 지원합니다.
-   Configuration Manager의 다음 기능은 현재 클라우드 관리 게이트웨이에 대해 지원되지 않습니다.

    -   클라이언트 배포
    -   자동 사이트 할당
    -   사용자 정책
    -   응용 프로그램 카탈로그(소프트웨어 승인 요청 포함)
    -   전체 OSD(운영 체제 배포)
    -   Configuration Manager 콘솔
    -   원격 도구
    -   보고 웹 사이트
    -   Wake on LAN
    -   Mac, Linux 및 UNIX 클라이언트
    -   Azure Resource Manager
    -   피어 캐시
    -   온-프레미스 모바일 장치 관리

## <a name="cost-of-cloud-management-gateway"></a>클라우드 관리 게이트웨이 비용

>[!IMPORTANT]
>아래에 제공된 비용 정보는 평가 목적으로만 사용됩니다. 사용자 환경에 클라우드 관리 게이트웨이 사용의 전체 비용에 영향을 주는 다른 변수가 있을 수 있습니다.

클라우드 관리 게이트웨이는 Azure 구독 계정에 요금이 부과되는 다음 Microsoft Azure 기능을 사용합니다.

-   가상 컴퓨터

    -   클라우드 관리 게이트웨이에는 현재 Standard\_A2 가상 컴퓨터가 필요합니다. 서비스를 만들 때 서비스를 지원할 VM 수를 선택할 수 있습니다.

    -   예측 목적으로만, 단일 Azure Standard\_A2 가상 컴퓨터에서 약 2,000대의 동시 인터넷 기반 클라이언트를 지원할 수 있다고 추정합니다.

    -   잠재적인 비용을 확인하려면 [Azure 가격 계산기](https://azure.microsoft.com/en-us/pricing/calculator/)를 참조하세요.

      >[!NOTE]
      >가상 컴퓨터 비용은 지역에 따라 다릅니다.

-   아웃바운드 데이터 전송

    -   서비스에서 전송되는 데이터 흐름에 대해 비용이 청구됩니다. 잠재적인 비용을 확인하려면 [Azure 대역폭 가격 정보](https://azure.microsoft.com/en-us/pricing/details/bandwidth/)를 참조하세요.

    -   예측 목적으로만, 매시간 정책 새로 고침을 수행하는 인터넷 기반 클라이언트의 경우 월별 클라이언트당 약 100MB를 추정합니다.

    >[!NOTE]
    > 클라우드 관리 게이트웨이를 통해 지원되는 다른 작업(예: 소프트웨어 업데이트 또는 응용 프로그램 배포)을 수행하면 Azure에서 아웃바운드 데이터 전송량이 증가합니다.

-   콘텐츠 저장소

    -   클라우드 관리 게이트웨이를 사용하여 관리되는 인터넷 기반 클라이언트는 비용 없이 Windows 업데이트에서 소프트웨어 업데이트 콘텐츠를 가져옵니다.

    -   기타 필요한 콘텐츠(예: 응용 프로그램)는 클라우드 기반 배포 지점에 배포해야 합니다. 현재 클라우드 관리 게이트웨이는 클라우드 배포 지점만 클라이언트에 콘텐츠를 보낼 수 있도록 지원합니다.

    - 자세한 내용은 [클라우드 기반 배포](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) 사용에 대한 비용 계획을 참조하세요.

## <a name="next-steps"></a>다음 단계

[클라우드 관리 게이트웨이 설정](setup-cloud-management-gateway.md)

