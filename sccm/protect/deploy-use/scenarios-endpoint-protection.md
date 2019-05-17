---
title: 맬웨어로부터 컴퓨터 보호
titleSuffix: Configuration Manager
description: Configuration Manager에서 Endpoint Protection을 구현하여 맬웨어 공격으로부터 컴퓨터를 보호하는 방법을 알아봅니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 539c7a89-3c03-4571-9cb4-02d455064eeb
author: mestew
ms.author: mstewart
manager: doubeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 0b6bbf7acd30ca8a19b898738490d30733e81f2d
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65494327"
---
# <a name="example-scenario-use-endpoint-protection-to-protect-computers-from-malware"></a>예제 시나리오: Endpoint Protection을 사용하여 맬웨어로부터 컴퓨터 보호

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 Configuration Manager에서 Endpoint Protection을 구현하여 조직 내 컴퓨터를 맬웨어 공격으로부터 보호하는 방법을 보여 주는 예제 시나리오를 제공합니다.  



## <a name="scenario-overview"></a>시나리오 개요

John은 Woodgrove 은행의 Configuration Manager 관리자입니다. 현재 이 은행은 맬웨어 공격으로부터 컴퓨터를 보호하기 위해 System Center Endpoint Protection을 사용합니다. 또한 Windows 그룹 정책을 사용하여 회사의 모든 컴퓨터에서 Windows 방화벽을 사용하도록 설정하고 Windows 방화벽이 새 프로그램을 차단할 때 사용자에게 알림이 제공되도록 합니다.  

John은 Woodgrove Bank가 최신 맬웨어 방지 프로그램 기능을 활용하고 Configuration Manager 콘솔에서 맬웨어 방지 솔루션을 중앙에서 관리할 수 있도록 Woodgrove Bank 맬웨어 방지 프로그램을 System Center Endpoint Protection으로 업그레이드할 것을 요청받았습니다. 


## <a name="business-requirements"></a>비즈니스 요구 사항

이 구현을 위해서는 다음과 같은 요구 사항이 필요합니다.  

- Configuration Manager를 사용하여 그룹 정책에 의해 현재 관리되는 Windows 방화벽 설정을 관리합니다.  

- Configuration Manager 소프트웨어 업데이트를 사용하여 컴퓨터에 맬웨어 정의를 다운로드합니다. 가령 컴퓨터가 회사 네트워크에 연결되어 있지 않기 때문에 소프트웨어 업데이트를 사용할 수 없는 경우 Microsoft 업데이트에서 정의 업데이트를 다운로드해야 합니다.  

- 사용자의 컴퓨터는 매일 빠른 맬웨어 검색을 수행해야 합니다. 그러나 서버는 영업일이 아닌 토요일마다 새벽 1시에 전체 검색을 실행해야 합니다.  

- 다음 이벤트 중 하나가 발생할 때마다 메일 경고를 보냅니다.  

  -   컴퓨터에서 맬웨어 검색  

  -   5% 이상이 컴퓨터에서 동일한 맬웨어 위협 검색  

  -   24시간 동안 5번 이상 동일한 맬웨어 위협이 검색됨  

  -   24시간 동안 3가지 이상 다른 유형의 맬웨어가 검색됨  

  John은 다음 단계를 수행하여 Endpoint Protection을 구현합니다.  



##  <a name="steps-to-implement-endpoint-protection"></a>Endpoint Protection을 구현하는 단계  

|프로세스|참조|  
|-------------|---------------|  
|John은 Configuration Manager에서 Endpoint Protection의 기본 개념에 대해 사용 가능한 정보를 검토합니다.|Endpoint Protection에 대한 개요 정보는 [System Center Configuration Manager의 Endpoint Protection](endpoint-protection.md)을 참조하세요.|  
|John은 Endpoint Protection을 사용하는 데 필요한 필수 조건을 검토하고 구현합니다.|Endpoint Protection에 필요한 필수 조건에 대한 자세한 내용은 [Endpoint Protection 계획](../plan-design/planning-for-endpoint-protection.md)을 참조하세요.|  
|John은 Woodgrove Bank 계층 구조 맨 위에 있는 단일 사이트 시스템 서버에만 Endpoint Protection 사이트 시스템 역할을 설치합니다.|Endpoint Protection 사이트 시스템 역할을 설치하는 방법에 대한 자세한 내용은 [Endpoint Protection 구성](configure-endpoint-protection.md)의 "필수 조건"을 참조하세요.|  
|John은 SMTP 서버를 사용하여 메일 경고를 보내도록 Configuration Manager를 구성합니다.<br /><br /> **참고:** Endpoint Protection 경고가 생성될 때 메일 알림을 받으려는 경우에만 SMTP 서버를 구성해야 합니다.|자세한 내용은 [Endpoint Protection에서 경고 구성](endpoint-configure-alerts.md)을 참조하세요.|  
|John은 Endpoint Protection 클라이언트를 설치할 모든 컴퓨터 및 서버를 포함하는 디바이스 컬렉션을 만듭니다. 이 컬렉션의 이름을 **Endpoint Protection로 보호되는 모든 컴퓨터**로 지정합니다.<br /><br /> **팁:** 사용자 컬렉션에 대해서는 경고를 구성할 수 없습니다.|컬렉션을 만드는 방법에 대한 자세한 내용은 [System Center Configuration Manager에서 컬렉션을 만드는 방법](../../core/clients/manage/collections/create-collections.md)을 참조하세요.|  
|그는 컬렉션에 대 한 다음 경고를 구성합니다. <br /><br />1) **맬웨어가 검색됨**: John은 경고 심각도 **위험**을 구성합니다. <br /><br />2) **동일한 유형의 맬웨어가 여러 컴퓨터에서 검색됨**: John은 경고 심각도 **위험**을 구성하고 5%가 넘는 컴퓨터에서 맬웨어가 검색될 때 경고가 생성되도록 지정합니다. <br /><br />3) **동일한 유형의 맬웨어가 컴퓨터에서 지정된 간격 내에 반복적으로 검색됨**: John은 경고 심각도 **위험**을 구성하고 맬웨어가 24시간 동안에서 5번 넘게 검색될 때 경고가 생성되도록 지정합니다. <br /><br />4) **여러 유형의 맬웨어가 동일한 컴퓨터에서 지정된 간격 내에 검색됨**: John은 경고 심각도 **위험**을 구성하고 24시간 내에 3가지 이상의 맬웨어 유형이 생성될 경우 경고가 생성되도록 지정합니다.<br /><br /> **경고 심각도** 값은 Configuration Manager 콘솔에 표시되는 경고 수준 및 메일 메시지에 수신되는 경고를 나타냅니다.<br /><br /> 또한 Configuration Manager 콘솔에서 경고를 모니터링할 수 있도록 **이 컬렉션을 Endpoint Protection 대시보드에서 보기** 옵션을 추가적으로 선택했습니다.|[System Center Configuration Manager에서 Endpoint Protection 구성](endpoint-configure-alerts.md)의 "Endpoint Protection에 대한 경고 구성"을 참조하세요.|  
|John은 자동 배포 규칙을 사용하여 하루에 3번 정의 업데이트를 다운로드 및 배포하도록 Configuration Manager 소프트웨어 업데이트를 구성합니다.|자세한 내용은 [Configuration Manager 소프트웨어 업데이트를 사용하여 정의 업데이트 제공](endpoint-definitions-configmgr.md)의 "Configuration Manager 소프트웨어 업데이트를 사용하여 정의 업데이트 제공" 섹션을 참조하세요.|  
|이한일은 Microsoft의 권장 보안 설정이 포함되어 있는 기본 맬웨어 방지 정책의 설정을 검사합니다. 컴퓨터에서 매일 빠른 검색이 수행되도록 하기 위해 다음 설정을 변경합니다.<br /><br /> 1) **클라이언트 컴퓨터에서 매일 빠른 검색 실행**: **예**<br /><br /> 2) **일별 빠른 검사 예약 시간**: **오전 9:00**.<br /><br /> 이한일은 정의 업데이트 원본으로 **Microsoft Update에서 배포된 업데이트** 가 기본적으로 선택되어 있는지 확인합니다. 이 경우 컴퓨터가 Configuration Manager 소프트웨어 업데이트를 수신할 수 없을 때 비즈니스 요구에 따라 Microsoft 업데이트에서 정의를 다운로드해야 합니다.|[System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)|  
|이한일은 극동 무역 서버만 포함된 **극동 무역 서버**라는 컬렉션을 만듭니다.|[System Center Configuration Manager에서 컬렉션을 만드는 방법](../../core/clients/manage/collections/create-collections.md)을 참조하세요.|  
|이한일은 **극동 무역 서버 정책**이라는 사용자 지정 맬웨어 방지 정책을 만듭니다. **예약된 검사** 에 대한 설정만 추가하고 다음과 같이 변경합니다.<br /><br /> **검사 유형**:  **전체**<br /><br /> **검사일**:  **토요일**<br /><br /> **검사 시간**: **오전 1시**<br /><br /> **Run a daily quick scan on client computers(클라이언트 컴퓨터에서 매일 빠른 검색 실행)**:  **아니요**|[System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md)|  
|이한일은 배포는 **극동 무역 서버 정책** 사용자 지정 맬웨어 방지 정책을 **극동 무역 서버** 컬렉션에 배포합니다.|[Endpoint Protection에 대한 맬웨어 방지 정책을 만들어 배포하는 방법](endpoint-antimalware-policies.md) 문서의 “클라이언트 컴퓨터에 맬웨어 방지 정책을 배포하려면”을 참조하세요.|  
|John은 Endpoint Protection에 대한 새로운 사용자 지정 클라이언트 디바이스 설정 집합을 만들고 이름을 **Woodgrove Bank Endpoint Protection 설정**으로 지정합니다.<br /><br /> **참고:** 계층 구조 내의 모든 클라이언트에서 Endpoint Protection을 설치하고 사용하도록 설정하지는 않으려면 기본 클라이언트 설정에서 **클라이언트 컴퓨터에서 Endpoint Protection 관리** 및 **클라이언트 컴퓨터에서 Endpoint Protection 클라이언트 설치** 옵션이 둘 다 **아니요**로 구성되어야 합니다.|자세한 내용은 [Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성](endpoint-protection-configure-client.md)을 참조하세요.|  
|Jone은 Endpoint Protection에 대한 다음 설정을 구성합니다.<br /><br /> **클라이언트 컴퓨터에서 Endpoint Protection 관리**을 구현합니다.  **예**<br /><br /> 이 설정 및 값은 설치된 기존 Endpoint Protection 클라이언트가 Configuration Manager에 의해 관리되도록 합니다.<br /><br /> **클라이언트 컴퓨터에 Endpoint Protection 클라이언트 설치**:  **예**</br></br>**참고** Configuration Manager 1802부터 Windows 10 디바이스에 Endpoint Protection 에이전트를 설치할 필요가 없습니다. Windows 10 디바이스에 이미 설치되어 있는 경우 Configuration Manager는 에이전트를 제거하지 않습니다. 관리자는 1802 클라이언트 버전 이상이 실행 중인 Windows 10 디바이스에서 Endpoint Protection 에이전트를 제거할 수 있습니다.|자세한 내용은 [Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성](endpoint-protection-configure-client.md)을 참조하세요.|  
|John은 **Woodgrove Bank Endpoint Protection 설정** 클라이언트 설정을 **Endpoint Protection 컬렉션에 의해 보호된 모든 컴퓨터** 컬렉션에 배포합니다.|[Configuration Manager에서 Endpoint Protection 구성](endpoint-antimalware-policies.md)의 "Endpoint Protection에 대한 사용자 지정 클라이언트 설정 구성"을 참조하세요.|  
|이한일은 Windows 방화벽 정책 만들기 마법사를 통해 도메인 프로필에 대한 다음 설정을 구성하여 정책을 만듭니다.<br /><br /> 1) **Windows 방화벽 설정**: **예**<br /><br /> 2)<br />                    **Windows 방화벽이 새 프로그램을 차단할 때 사용자에게 알림**: **예**|[System Center Configuration Manager에서 Endpoint Protection에 대한 Windows 방화벽 정책을 만들어 배포하는 방법](../../protect/deploy-use/create-windows-firewall-policies.md)을 참조하세요.|  
|John은 이전에 만든 **Endpoint Protection에 의해 보호된 모든 컴퓨터** 컬렉션에 새 방화벽 정책을 배포합니다.|자세한 내용은 [System Center Configuration Manager에서 Endpoint Protection에 대한 Windows 방화벽 정책을 만들어 배포하는 방법](create-windows-firewall-policies.md)의 "Windows 방화벽 정책을 배포하려면"을 참조하세요.|  
|John은 Endpoint Protection에 대해 사용 가능한 관리 작업을 사용하여 맬웨어 방지 및 Windows 방화벽 정책을 관리하고, 필요한 경우 주문형 컴퓨터 검사를 수행하고, 강제로 컴퓨터에서 최신 정의를 다운로드하도록 하고, 맬웨어가 검색되었을 때 수행할 추가 작업을 지정합니다.|[System Center Configuration Manager에서 Endpoint Protection에 대한 맬웨어 방지 정책 및 방화벽 설정을 관리하는 방법](endpoint-antimalware-firewall.md)을 참조하세요.|  
|Jone은 다음 방법을 사용하여 Endpoint Protection의 상태와 Endpoint Protection에 의해 수행된 작업을 모니터링합니다.<br /><br /> 1) **모니터링** 작업 영역의 **보안** 아래에서 **Endpoint Protection 상태** 노드 사용<br /><br /> 2) **자산 및 준수** 작업 영역에서 **Endpoint Protection** 노드 사용<br /><br /> 3) 기본 제공 Configuration Manager 보고서 사용|[System Center Configuration Manager에서 Endpoint Protection을 모니터링하는 방법](monitor-endpoint-protection.md)을 참조하세요.|  

 John은 관리자에게 Endpoint Protection의 성공적인 구현을 보고하고 Woodgrove Bank의 컴퓨터가 지정된 비즈니스 요구에 따라 맬웨어 방지 소프트웨어를 통해 보호됨을 확인합니다.
