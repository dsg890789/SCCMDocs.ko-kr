---
title: "기능 및 특성 | Microsoft 문서"
description: "System Center Configuration Manager의 기본 관리 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5d388399-07ca-431c-a9b2-56c69771aa87
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 6ed317d45d90758832d4157985dd95d5e253c6fc
ms.openlocfilehash: 851029368d97312ef2766505f933eac72d6950e5


---
# <a name="features-and-capabilities-of-system-center-configuration-manager"></a>System Center Configuration Manager의 기능 및 특성

*적용 대상: System Center Configuration Manager(현재 분기)*

다음은 System Center Configuration Manager의 기본 관리 기능입니다. 각 기능에는 고유한 필수 구성 요소가 있고 사용하려는 기능에 따라 Configuration Manager 계층 구조의 디자인과 구현이 달라질 수 있습니다. 예를 들어 계층의 장치에 소프트웨어를 배포하려는 경우 배포 지점 사이트 시스템 역할을 설치해야 합니다.  

 사용자 환경에서 이러한 관리 기능을 지원할 수 있도록 Configuration Manager를 계획하고 설치하는 방법에 대한 자세한 내용은 [System Center Configuration Manager 사용 준비](../../../core/plan-design/get-ready.md)를 참조하세요.  

 **응용 프로그램 관리**  

 응용 프로그램을 만들고, 관리하고, 배포하고, 모니터링할 수 있는 도구 및 리소스 집합을 관리하는 다양한 장치 범위에 제공합니다. 또한 Configuration Manager에서는 사용자의 앱에서 앱의 회사 데이터를 보호하는 데 도움이 되는 도구를 제공합니다. [응용 프로그램 관리 소개](/sccm/apps/understand/introduction-to-application-management)를 참조하세요.

 **회사 리소스 액세스**  

 조직의 사용자가 원격 위치에서 데이터와 응용 프로그램에 액세스할 수 있는 도구 및 리소스 집합을 제공합니다. 이러한 도구에는 Wi-Fi 프로필, VPN 프로필, 인증서 프로필과, Exchange 및 SharePoint Online에 대한 조건부 액세스가 포함됩니다. [System Center Configuration Manager를 사용한 데이터 및 사이트 인프라 보호](../../../protect/understand/protect-data-and-site-infrastructure.md) 및 [System Center Configuration Manager에서 서비스에 대한 액세스 관리](../../../protect/deploy-use/manage-access-to-services.md)를 참조하세요.  

 **준수 설정**  

 기업에서 클라이언트 장치의 구성 호환성을 평가하고, 추적하고, 재구성할 수 있는 도구 및 리소스 집합을 제공합니다.  또한 준수 설정을 사용하여 관리하는 장치에서 다양한 기능 및 보안 설정을 구성할 수 있습니다. [System Center Configuration Manager를 사용하여 장치 준수 확인](../../../compliance/understand/ensure-device-compliance.md)을 참조하세요.  

 **Endpoint Protection**  

 기업의 컴퓨터에 보안, 맬웨어 방지, Windows 방화벽 관리 기능을 제공합니다. [System Center Configuration Manager의 Endpoint Protection](../../../protect/deploy-use/endpoint-protection.md)을 참조하세요.  

 **인벤토리**  

 자산을 식별하고 모니터링할 수 있는 도구 집합을 제공합니다.  

-   **하드웨어 인벤토리**: 엔터프라이즈 내 장치의 하드웨어에 대한 자세한 정보를 수집합니다. [System Center Configuration Manager의 하드웨어 인벤토리 소개](../../../core/clients/manage/inventory/introduction-to-hardware-inventory.md)를 참조하세요.  

-   **소프트웨어 인벤토리**: 조직 내 클라이언트 컴퓨터에 저장된 파일에 대한 정보를 수집하고 보고합니다. [System Center Configuration Manager의 소프트웨어 인벤토리 소개](../../../core/clients/manage/inventory/introduction-to-software-inventory.md)를 참조하세요.  

-   **Asset Intelligence**: 인벤토리 데이터를 수집하고 기업의 소프트웨어 라이선스 사용 현황을 모니터링하는 도구를 제공합니다. [System Center Configuration Manager의 Asset Intelligence 소개](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md)를 참조하세요.  

**Microsoft Intune에서 모바일 장치 관리**  

 인터넷에서 Microsoft Intune 서비스를 사용하여 Configuration Manager를 통해 iOS, Android(Samsung KNOX Standard 포함), Windows Phone 및 Windows 장치를 관리할 수 있습니다.

 Intune 서비스를 사용하더라도 Configuration Manager 콘솔을 통해 사용 가능한 서비스 연결 지점 사이트 시스템 역할을 사용하여 관리 작업이 완료됩니다. [System Center Configuration Manager 및 Microsoft Intune을 지원하는 하이브리드 MDM(모바일 장치 관리)](../../../mdm/understand/hybrid-mobile-device-management.md)을 참조하세요.  

 **온-프레미스 모바일 장치 관리**  

 장치 플랫폼에 기본 제공되는 온-프레미스 Configuration Manager 인프라 및 관리 기능을 사용하여(별도로 설치된 Configuration Manager 클라이언트를 사용하지 않고) PC 및 모바일 장치를 등록하고 관리합니다. 현재 Windows 10 Enterprise 및 Windows 10 Mobile 장치 관리를 지원합니다.  [System Center Configuration Manager의 온-프레미스 인프라로 모바일 장치 관리](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md)를 참조하세요.  

 **운영 체제 배포**  

 운영 체제 이미지를 만드는 도구를 제공합니다. 그러면 PXE 부팅 또는 부팅 가능한 미디어(예: CD 세트, DVD 또는 USB 플래시 드라이브)를 사용하여 Configuration Manager에서 관리하는 컴퓨터 및 관리되지 않는 컴퓨터에 이러한 이미지를 배포할 수 있습니다. [System Center Configuration Manager의 운영 체제 배포 소개](../../../osd/understand/introduction-to-operating-system-deployment.md)를 참조하세요.  

 **전원 관리**  

 기업에서 클라이언트 컴퓨터의 전력 소비를 관리하고 모니터링하는 데 사용할 수 있는 도구 및 리소스 집합을 제공합니다. [System Center Configuration Manager 전원 관리 소개](../../../core/clients/manage/power/introduction-to-power-management.md)를 참조하세요.  

 **쿼리**  

 계층의 리소스에 대한 정보 및 인벤토리 데이터와 상태 메시지에 대한 정보를 검색하는 도구를 제공합니다. 그러면 이 정보를 사용하여 소프트웨어 배포 및 구성 설정에 대한 장치 또는 사용자 컬렉션을 보고하거나 정의할 수 있습니다. [System Center Configuration Manager의 쿼리 소개](../../../core/servers/manage/introduction-to-queries.md)를 참조하세요.  

 **원격 연결 프로필**  

 조직에서 원격 연결 설정을 만들어 장치에 배포하고 모니터링할 수 있는 도구 및 리소스 집합을 제공합니다. 이러한 설정을 배포하면 최종 사용자가 회사 네트워크에서 자신의 컴퓨터에 연결하는 데 필요한 노력이 최소화됩니다. [System Center Configuration Manager에서 원격 연결 프로필 사용](/sccm/compliance/deploy-use/create-remote-connection-profiles)을 참조하세요.  

 **사용자 데이터 및 프로필 구성 항목**  

 Configuration Manager의 사용자 데이터 및 프로필 구성 항목에는 Windows 8 이상을 실행하는 컴퓨터에서 계층 구조 내 사용자에 대해 폴더 리디렉션, 오프라인 파일 및 로밍 프로필을 관리할 수 있는 설정이 포함됩니다. [System Center Configuration Manager에서 사용자 데이터 및 프로필 구성 항목 작업](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)을 참조하세요.  

 **원격 제어**  

 Configuration Manager 콘솔에서 클라이언트 컴퓨터를 원격으로 관리하는 도구를 제공합니다. [System Center Configuration Manager의 원격 제어 소개](../../../core/clients/manage/remote-control/introduction-to-remote-control.md)를 참조하세요.  

 **보고**  

 Configuration Manager 콘솔에서 SQL Server Reporting Services의 고급 보고 기능을 사용할 수 있는 도구 및 리소스 집합을 제공합니다. [System Center Configuration Manager의 보고 소개](../../../core/servers/manage/introduction-to-reporting.md)를 참조하세요.  

 **소프트웨어 계량**  

 Configuration Manager 클라이언트에서 소프트웨어 사용량 데이터를 모니터링하고 수집하는 도구를 제공합니다. [System Center Configuration Manager의 소프트웨어 계량을 사용하여 앱 사용 모니터링](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md)을 참조하세요.  

 **소프트웨어 업데이트**  

 기업에서 소프트웨어 업데이트를 관리하고, 배포하고, 모니터링할 수 있는 도구 및 리소스 집합을 제공합니다. [System Center Configuration Manager의 소프트웨어 업데이트 소개](/sccm/sum/understand/software-updates-introduction)를 참조하세요.  



<!--HONumber=Dec16_HO3-->


