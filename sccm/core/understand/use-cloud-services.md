---
title: "클라우드 서비스 사용 | System Center Configuration Manager"
description: "System Center Configuration Manager에 대한 클라우드 리소스를 프로비전하여 온-프레미스 인프라를 보완합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 72e01c23ab597ad5a446492c3dc371aa50b9d949
ms.openlocfilehash: 9440123f6f13e19723657e7b4d5627f3a349a3b4


---
# <a name="use-cloud-services-with-system-center-configuration-manager"></a>System Center Configuration Manager에서 클라우드 서비스 사용

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서는 온-프레미스 인프라를 보완하며 다음과 같은 비즈니스 문제를 해결하는 데 도움이 되는 다양한 클라우드 기반 옵션을 지원합니다.  

-   모바일 장치 관리용 Intune을 사용하여 BYOD 관리  

-   클라우드 기반 배포 지점을 사용하여 회사 방화벽 외부의 인트라넷에서 격리된 클라이언트 또는 리소스에 대해 콘텐츠 리소스 제공  

-   실제 하드웨어가 사용할 수 없는 상태이거나 요구 사항을 지원하기 위해 논리적으로 배치된 경우 Microsoft Azure Virtual Machine을 사용하여 인프라 규모 확장  

Configuration Manager를 배포하기 전에 클라우드 리소스를 프로비전해야 하는 것은 아니지만 계층 구조 디자인 계획을 많이 진행하기 전에 이러한 옵션에 대해 이해하면 도움이 될 수 있습니다. 클라우드 리소스를 사용하면 비용과 시간을 절약하는 동시에 온-프레미스 인프라에서는 해결할 수 없는 비즈니스 문제를 해결할 수 있습니다.  

## <a name="cloud-based-resources-you-can-use-with-configuration-manager"></a>Configuration Manager에서 사용할 수 있는 클라우드 기반 리소스  
 각 옵션의 요구 사항은 서로 다르므로 각 옵션을 자세히 조사하여 고유한 필수 구성 요소, 제한 사항 및 사용량 기준 추가 비용 발생 가능성을 파악해야 합니다.  

-   클라우드 기반 배포 지점에 대한 자세한 내용은 [클라우드 기반 배포 지점 설치](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure)를 참조하세요.

-   Microsoft Azure에 대한 자세한 내용은 MSDN 라이브러리에서 [Microsoft Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) 를 참조하세요.  

### <a name="microsoft-azure-virtual-machines-for-cloud-based-infrastructure"></a>Microsoft Azure Virtual Machine(클라우드 기반 인프라의 경우)  
 Configuration Manager에서는 실제 회사 네트워크 내의 온-프레미스에서 실행하는 경우와 마찬가지로 Azure의 가상 컴퓨터에서 실행되는 컴퓨터 사용을 지원합니다. 다음과 같은 시나리오에서 Azure 가상 컴퓨터를 사용할 수 있습니다.  

-   **시나리오 1:** 가상 컴퓨터에서 Configuration Manager를 실행하고 다른 가상 컴퓨터에 설치된 클라이언트를 관리하는 데 사용할 수 있습니다.  

-   **시나리오 2:** 가상 컴퓨터에서 Configuration Manager를 실행하고 Azure에서 실행 중이지 않은 클라이언트를 관리하는 데 사용할 수 있습니다.  

-   **시나리오 3:** 적합한 통신용 네트워크 연결을 사용할 수 있는 경우 실제 회사 네트워크에서는 다른 역할을 실행하면서 가상 컴퓨터에서는 다른 Configuration Manager 사이트 시스템 역할을 실행할 수 있습니다.  

실제 회사 네트워크에서 Configuration Manager를 설치할 때 적용되는 것과 동일한 네트워크, 운영 체제 및 하드웨어 요구 사항이 Microsoft Azure에서 Configuration Manager를 설치할 때도 적용됩니다.  

Azure 가상 컴퓨터를 사용하려면 Azure 구독이 있어야 하며 사용하는 가상 컴퓨터 수, 가상 컴퓨터 구성 및 클라우드 기반 리소스 사용을 기반으로 요금이 부과됩니다.  

또한 Azure 가상 컴퓨터에서 실행되는 Configuration Manager 사이트 및 클라이언트에는 온-프레미스 설치와 같은 라이선스 요구 사항이 적용됩니다.  

### <a name="microsoft-azure-services-for-cloud-based-distribution-points"></a>Microsoft Azure 서비스(클라우드 기반 배포 지점의 경우)  
 Azure 서비스를 사용하여 Configuration Manager 배포 지점(클라우드 기반 배포 지점)을 호스트할 수 있습니다.  Azure 가상 컴퓨터에 배포된 배포 지점 및 온-프레미스 배포 지점과 함께 [System Center Configuration Manager의 클라우드 기반 배포 지점](../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)을 사용할 수 있습니다.  

 이러한 방식은 사이트 시스템 역할을 배포하는 Azure 가상 컴퓨터를 사용하는 방식과는 다릅니다. 클라우드 기반 배포 지점:  

-   가상 컴퓨터가 아닌 Microsoft Azure에서 서비스로 실행됩니다.  

-   클라이언트의 콘텐츠 요청 증가를 충족하기 위해 자동으로 확장됩니다.  

-   인터넷과 인트라넷에서 클라이언트를 지원합니다.  

Azure를 사용하여 배포 지점을 호스트하려면 Azure 구독이 있어야 하며 서비스로 보내고 받는 데이터 크기를 기준으로 요금이 부과됩니다.  

### <a name="microsoft-intune-for-mobile-device-management"></a>Microsoft Intune(모바일 장치 관리의 경우)  
 Microsoft Intune 구독을 Configuration Manager와 통합하여 Intune 서비스로 장치를 관리하도록 설정할 수 있습니다. 이 통합의 특징은 다음과 같습니다.  

-   하이브리드 구성이라고 하며 다양한 장치를 지원하도록 Configuration Manager 또는 사용자 관점에 따라 Intune을 확장합니다.  

-   Microsoft Intune 커넥터 사이트 시스템 역할이 필요합니다.  

-   Intune을 사용하여 관리하려는 장치용으로 충분한 라이선스가 있는 별도의 Intune 구독이 필요합니다.  

Intune에서는 Microsoft Azure를 사용하지만 Azure를 독립적으로 구성할 필요는 없으며 Intune 구독 비용 이외의 추가 비용도 들지 않습니다.  

### <a name="additional-configuration-manager-capabilities"></a>추가 Configuration Manager 기능  
 일부 Configuration Manager 기능은 다음과 같은 클라우드 기반 서비스에 연결할 수 있습니다.  

-   WSUS(Windows Server Update Services)  

-   Configuration Manager용 업데이트를 다운로드할 Configuration Manager 서비스 클라우드  

이러한 추가 기능은 Azure 구독이 없어도 사용할 수 있으며 클라우드에서 특정 연결, 인증서 또는 서비스를 구성할 필요도 없습니다. Configuration Manager에서 이러한 기능을 자동으로 관리하기 때문입니다.  해당하는 사이트 시스템 및 장치가 인터넷 기반 URL에 액세스할 수 있는지만 확인하면 됩니다.  

##  <a name="a-namebkmkcloudseca-security-for-cloud-based-services"></a><a name="BKMK_CloudSec"></a> 클라우드 기반 서비스의 보안  
 Configuration Manager에서는 인증서를 사용하여 Microsoft Azure의 콘텐츠를 프로비전 및 액세스하고 사용자가 사용하는 서비스를 관리합니다. Configuration Manager는 Azure에 저장되는 데이터를 암호화하지만 Azure에서 제공하는 것 이상의 추가 보안 또는 데이터 컨트롤을 제공하지는 않습니다.  

 자세한 내용은 다양한 클라우드 기반 리소스 시나리오의 세부 정보를 참조하세요. Microsoft Azure 보안과 관련된 다음 항목을 확인할 수도 있습니다.  

-   [Microsoft Azure: Microsoft Azure의 보안 계정 관리 이해](http://go.microsoft.com/fwlink/p/?LinkId=262968)  

-   [Microsoft Azure Security Overview](http://go.microsoft.com/fwlink/p/?LinkId=262970)(Microsoft Azure 보안 개요)  

-   [Get Past the Security Crossroads in Your Cloud Migration](http://go.microsoft.com/fwlink/p/?LinkId=262971)(클라우드 마이그레이션의 보안 기로 통과)  

-   [Data Security in Azure Part 1 of 2](http://go.microsoft.com/fwlink/p/?LinkId=262974)(Azure 데이터 보안 1/2부)  



<!--HONumber=Nov16_HO1-->


