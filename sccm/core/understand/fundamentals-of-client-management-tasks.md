---
title: "클라이언트 관리 기본 사항 | System Center Configuration Manager"
description: "System Center Configuration Manager 클라이언트를 관리하기 위해 실행할 수 있는 작업에 대해 알아봅니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: b746c051eee42bcea5c01ced359f568c5aae5fd8


---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 클라이언트 관리 작업의 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 클라이언트를 설치한 후 클라이언트를 관리하기 위해 실행할 수 있는 여러 작업이 있습니다.  일부는 Configuration Manager 콘솔에서 시작하지만 그 외의 작업은 클라이언트에서 Windows 제어판의 Configuration Manager 앱을 통해 시작하거나 볼 수 있습니다.  

## <a name="the-console"></a>콘솔  
 Configuration Manager 콘솔에서 다음을 비롯하여 다양한 클라이언트 관리 작업을 수행할 수 있습니다.  

-   응용 프로그램, 소프트웨어 업데이트, 유지 관리 스크립트 및 운영 체제를 배포할 수 있습니다. 지정한 날짜와 시간에 설치되도록 구성하거나, 요청된 경우에 사용자가 설치할 수 있도록 만들거나, 제거할 응용 프로그램을 구성할 수 있습니다.  

-   맬웨어 및 보안 위협으로부터 컴퓨터를 보호하고 문제가 검색된 경우 사용자에게 알릴 수 있습니다.  

-   클라이언트 구성 설정을 정의하여 클라이언트를 모니터링하고 호환되지 않는 경우 재구성할 수 있습니다.  

-   라이선스 모니터링 및 라이선스 조정을 포함하여 Microsoft에서 하드웨어 및 소프트웨어 인벤토리 정보를 수집할 수 있습니다.  

-   원격 제어를 사용하여 컴퓨터 문제를 해결합니다.  

-   컴퓨터의 전원 소비를 관리 및 모니터링하도록 전원 관리 설정을 구현할 수 있습니다.  

Configuration Manager 콘솔에서 경고 및 상태 정보를 확인하여 작업을 거의 실시간으로 모니터링할 수 있습니다. SQL Reporting Services의 통합 보고 기능을 사용해서는 데이터와 기록적 추세 정보를 캡처할 수 있습니다.  클라이언트에서 사이트에 대한 세부 정보를 클라이언트 상태로 제출합니다.  클라이언트 상태 정보는 클라이언트 및 클라이언트 활동의 상태에 대한 데이터를 제공하며, 콘솔에서 또는 Configuration Manager에 대한 기본 제공 보고서를 사용하여 볼 수 있습니다. 이러한 데이터를 통해 응답하지 않는 컴퓨터를 식별하고 경우에 따라 문제를 자동으로 해결할 수 있습니다.  

 클라이언트의 관리 작업에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../core/clients/manage/manage-clients.md) 및 [System Center Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 관리하는 방법](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md)을 참조하세요. 보고서 사용 방법에 대한 자세한 내용은   
            [System Center Configuration Manager의 보고 소개](../../core/servers/manage/introduction-to-reporting.md)  

## <a name="the-windows-control-panel-app"></a>Windows 제어판 앱  
 Configuration Manager 클라이언트 소프트웨어를 설치하면 제어판에 **Configuration Manager** 클라이언트 응용 프로그램이 설치됩니다. 소프트웨어 센트와 달리 이 응용 프로그램은 최종 사용자가 아닌 지원 센터를 위해 고안되었습니다. 일부 구성 옵션을 사용하려면 로컬 관리자 권한이 필요하고, 대부분의 옵션을 사용하려면 Configuration Manager 작동 원리에 대한 기술적 지식이 필요합니다. 이 응용 프로그램을 사용하여 클라이언트에서 다음 작업을 수행할 수 있습니다.  

-   빌드 번호, 할당된 사이트, 통신 중인 관리 지점, 클라이언트가 사용하는 인증서가 PKI 인증서인지, 아니면 자체 서명된 인증서인지 등 클라이언트에 대한 속성을 볼 수 있습니다.  

-   클라이언트가 처음으로 설치된 이후 클라이언트 정책이 성공적으로 다운로드되었으며, Configuration Manager 콘솔에 구성된 클라이언트 설정에 따라 예상대로 클라이언트 설정이 사용 또는 사용하지 않도록 설정되었는지 확인할 수 있습니다.  

-   Configuration Manager 콘솔에서 구성이 최근에 변경된 경우 다음 예약 시간까지 기다리지 않기 위해 클라이언트 정책을 다운로드하는 등의 클라이언트 작업을 시작할 수 있습니다.  

-   클라이언트를 Configuration Manager 사이트에 수동으로 할당하거나 사이트를 찾을 수 있으며 DNS로 게시하는 관리 지점에 대해 DNS 접미사를 지정할 수 있습니다.  

-   캐시에 일시적으로 파일을 저장하고, 소프트웨어 설치에 더 많은 디스크 공간이 필요하면 파일을 삭제하는 등 클라이언트 캐시를 구성할 수 있습니다.  

-   인터넷 기반 클라이언트 관리에 대한 설정을 구성할 수 있습니다.  

-   클라이언트에 배포된 구성 기준을 보고, 호환성 평가를 시작하며, 호환성 보고서를 볼 수 있습니다.  



<!--HONumber=Nov16_HO1-->


