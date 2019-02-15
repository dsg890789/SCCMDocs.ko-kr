---
title: Endpoint Protection 구성
titleSuffix: Configuration Manager
description: 클라이언트 컴퓨터에서 맬웨어 방지 정의를 최신 상태로 유지하도록 System Center Configuration Manager에서 Endpoint protection의 방법을 선택하고 구성하는 방법을 알아봅니다.
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 537dd2a7-4e44-4877-b8dd-5e1499407f8d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: f87f6c439a7f42144553406081e0b21bcef84c9b
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56123866"
---
#  <a name="configure-definition-updates-for-endpoint-protection"></a>Endpoint Protection에 대한 정의 업데이트 구성  

*적용 대상: System Center Configuration Manager(현재 분기)*

 System Center Configuration Manager의 Endpoint Protection에서는 사용 가능한 여러 가지 방법 중 하나를 사용하여 계층 구조에 있는 클라이언트 컴퓨터의 맬웨어 방지 정의를 최신 상태로 유지할 수 있습니다. 이 항목의 정보는 이러한 방법을 선택하고 구성하는 데 유용할 수 있습니다.

 맬웨어 방지 정의를 업데이트하려면 다음 방법 중 하나 이상을 사용합니다.

- [Configuration Manager에서 배포되는 업데이트](endpoint-definitions-configmgr.md) - 이 방법은 Configuration Manager 소프트웨어 업데이트를 사용하여 정의 및 엔진 업데이트를 계층 구조의 컴퓨터에 제공합니다.

- [WSUS(Windows Server Update Services)에서 배포되는 업데이트](endpoint-definitions-wsus.md) - 이 방법은 WSUS 인프라를 사용하여 컴퓨터에 정의 및 엔진 업데이트를 제공합니다.

- [Microsoft 업데이트에서 배포되는 업데이트](endpoint-definitions-microsoft-updates.md) - 이 방법을 사용하면 컴퓨터가 정의 및 엔진 업데이트를 다운로드하기 위해 Microsoft 업데이트에 직접 연결합니다. 이 방법은 회사 네트워크에 자주 연결하지 않는 컴퓨터에 유용할 수 있습니다.

- [Microsoft 맬웨어 보호 센터에서 배포되는 업데이트](endpoint-definitions-protection-center.md) - 이 방법은 Microsoft 맬웨어 보호 센터에서 정의 업데이트를 다운로드합니다.

- [UNC 파일 공유의 업데이트](endpoint-definitions-network.md) - 이 방법을 사용하면 최신 정의 및 엔진 업데이트를 네트워크 공유에 저장할 수 있습니다. 그런 후에 클라이언트에서 네트워크에 액세스하여 업데이트를 설치할 수 있습니다.

  여러 정의 업데이트 원본을 구성하고 평가하고 적용하는 순서를 제어할 수 있습니다. 이 작업은 맬웨어 방지 정책을 만들 때 **정의 업데이트 원본 구성** 대화 상자에서 수행합니다.

> [!IMPORTANT]
>  Windows 10 PC의 경우 Windows Defender에 대한 맬웨어 정의를 업데이트하도록 Endpoint Protection을 구성해야 합니다.

## <a name="how-to-configure-definition-update-sources"></a>정의 업데이트 원본을 구성하는 방법
 각 맬웨어 방지 정책에 사용할 정의 업데이트 원본을 구성하려면 다음 절차를 따르세요.

1.  Configuration Manager 콘솔에서 **자산 및 호환성**을 클릭합니다.

2.  **자산 및 호환성** 작업 영역에서 **Endpoint Protection**을 확장하고 **맬웨어 방지 정책**을 클릭합니다.

3.  **기본 맬웨어 방지 정책** 의 속성 페이지를 열거나 새 맬웨어 방지 정책을 만듭니다. 맬웨어 방지 정책을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)을 참조하세요.

4.  맬웨어 방지 속성 대화 상자의 **정의 업데이트** 섹션에서 **원본 설정**을 클릭합니다.

5.  **정의 업데이트 원본 구성** 대화 상자에서 정의 업데이트에 사용할 원본을 선택합니다. **위로** 또는 **아래로** 를 클릭하여 이러한 원본의 사용 순서를 수정할 수 있습니다.

6.  **확인** 을 클릭하여 **정의 업데이트 원본 구성** 대화 상자를 닫습니다.

## <a name="configure-endpoint-protection-definitions"></a>Endpoint Protection 정의 구성

-   [Configuration Manager에서 배포되는 업데이트](endpoint-definitions-configmgr.md) - 이 방법은 Configuration Manager 소프트웨어 업데이트를 사용하여 정의 및 엔진 업데이트를 계층 구조의 컴퓨터에 제공합니다.

-   [WSUS(Windows Server Update Services)에서 배포되는 업데이트](endpoint-definitions-wsus.md) - 이 방법은 WSUS 인프라를 사용하여 컴퓨터에 정의 및 엔진 업데이트를 제공합니다.

-   [Microsoft 업데이트에서 배포되는 업데이트](endpoint-definitions-microsoft-updates.md) - 이 방법을 사용하면 컴퓨터가 정의 및 엔진 업데이트를 다운로드하기 위해 Microsoft 업데이트에 직접 연결합니다. 이 방법은 회사 네트워크에 자주 연결하지 않는 컴퓨터에 유용할 수 있습니다.

-   Microsoft 맬웨어 보호 센터에서 배포되는 업데이트 - 이 방법은 Microsoft 맬웨어 보호 센터에서 정의 업데이트를 다운로드합니다.

-   [UNC 파일 공유의 업데이트](endpoint-definitions-network.md) - 이 방법을 사용하면 최신 정의 및 엔진 업데이트를 네트워크 공유에 저장할 수 있습니다. 그런 후에 클라이언트에서 네트워크에 액세스하여 업데이트를 설치할 수 있습니다.
