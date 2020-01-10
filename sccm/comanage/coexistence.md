---
title: 타사 MDM 공존성
titleSuffix: Configuration Manager
description: Configuration Manager에서 타사 MDM 서비스를 사용하는 방법에 대해 알아보기
ms.date: 05/21/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: ed4dc65e-e5d5-4f75-88ac-f4849ec8fc10
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c4ecc3f5b456eb8d50675797ba2bfa4c7a6ecf25
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75782033"
---
# <a name="third-party-mdm-coexistence-with-configuration-manager"></a>Configuration Manager와 타사 MDM 공존

Configuration Manager 및 Microsoft Intune을 둘 다 사용해서 Windows 10 디바이스를 동시에 관리할 경우 이 기능을 [공동 관리](/sccm/comanage/overview)라고 합니다. Configuration Manager로 디바이스를 관리하고 타사 MDM 서비스에 등록하는 경우 이 기능을 *공존*이라고 합니다. 두 관리 기관을 제대로 오케스트레이션하지 못한 상태에서 단일 디바이스 관리에 사용하는 일은 어려운 일일 수 있습니다. 공동 관리를 사용하면 Configuration Manager와 Intune이 [워크로드](/sccm/comanage/workloads)의 균형을 유지하여 충돌이 일어나지 않도록 합니다. 이러한 상호 작용은 타사 서비스와 공존하지 않으므로 공존의 관리 기능은 제한됩니다.

Configuration Manager 클라이언트는 Windows 10 버전 1709 이상을 실행하며 Azure Active Directory에 가입된 디바이스에서 타사 MDM 서비스와 공존할 수 있습니다. 이러한 디바이스는 다음 유형 중 하나일 수 있습니다.

- [Azure AD 조인](https://docs.microsoft.com/azure/active-directory/devices/azureadjoin-plan)만 (이 유형은 “클라우드 도메인 연결”이라고도 함)  

- [하이브리드 도메인 가입](https://docs.microsoft.com/azure/active-directory/devices/hybrid-azuread-join-plan): 디바이스가 온-프레미스 Active Directory에 가입되고 Azure Active Directory에 등록됩니다.  

> [!Note]  
> [개인 소유 디바이스](https://docs.microsoft.com/windows/client-management/mdm/mdm-enrollment-of-windows-devices#connecting-personally-owned-devices-bring-your-own-device)는 지원되지 않습니다.  

구성 관리자 클라이언트가 타사 MDM 서비스에서도 디바이스를 관리하고 있음을 감지하면 Configuration Manager의 특정 워크로드를 자동으로 비활성화합니다. 이 동작을 통해 MDM 서비스가 이러한 기능을 인계받을 수 있습니다. 또한 디바이스 및 사용자 환경을 저하시킬 수 있는 클라이언트의 설정 충돌도 방지됩니다. 이 경우 Configuration Manager의 다음 워크로드가 비활성화됩니다.

- VPN, Wi-Fi, 메일 및 인증서 설정에 대한 리소스 액세스 정책
- 레거시 패키지를 포함하는 애플리케이션 관리
- 소프트웨어 업데이트 검색 및 설치
- Windows Defender 맬웨어 방지 보호 기능 세트인 Endpoint Protection
- 조건부 액세스에 대한 규정 준수 정책
- 디바이스 구성
- Office 간편 실행 관리

구성 관리자 클라이언트는 다음 읽기 전용 작업을 계속 진행하여 타사 관리 기관과의 충돌을 방지합니다.

- 하드웨어 및 소프트웨어 인벤토리
- Asset Intelligence
- 소프트웨어 계량
- 전원 관리 보고

Configuration Manager 및 Intune을 사용한 공동 관리의 이점에 대한 자세한 내용은 [공동 관리 혜택](/sccm/comanage/overview#benefits)을 참조하세요.
