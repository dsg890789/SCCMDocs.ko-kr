---
title: 클라이언트 관리의 기본 사항
titleSuffix: Configuration Manager
description: System Center Configuration Manager 클라이언트를 관리하기 위해 실행하는 작업을 알아봅니다.
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 8d4e5641-354e-4439-8b4f-620a760e233d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 468d21123e6a4166957b7dcc8cda614a78d2366e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "62252649"
---
# <a name="fundamentals-of-client-management-tasks-for-system-center-configuration-manager"></a>System Center Configuration Manager에 대한 클라이언트 관리 작업의 기본 사항

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 클라이언트를 설치한 후 클라이언트를 관리하기 위해 실행하는 여러 작업이 있습니다.  몇몇 작업은 Configuration Manager 콘솔에서 실행됩니다. 다른 작업은 Configuration Manager 클라이언트 애플리케이션에서 실행됩니다. Configuration Manager 클라이언트 애플리케이션은 Configuration Manager 클라이언트 소프트웨어와 함께 설치됩니다.

## <a name="configuration-manager-console-tasks"></a>Configuration Manager 콘솔 작업
 Configuration Manager 콘솔에서 다음과 같은 다양한 클라이언트 관리 작업을 수행할 수 있습니다.  

-   애플리케이션, 소프트웨어 업데이트, 유지 관리 스크립트 및 운영 체제를 배포할 수 있습니다. 특정 날짜와 시간에 설치되도록 구성하거나, 요청된 경우에 사용자가 소프트웨어를 설치할 수 있도록 하거나, 제거할 애플리케이션을 구성합니다.  

-   맬웨어 및 보안 위협으로부터 컴퓨터를 보호하고 문제가 검색된 경우 사용자에게 알릴 수 있습니다.  

-   모니터링할 클라이언트 구성 설정을 정의하고 호환되지 않는 경우 재구성할 수 있습니다.  

-   라이선스 모니터링 및 라이선스 조정을 포함하여 Microsoft에서 하드웨어 및 소프트웨어 인벤토리 정보를 수집할 수 있습니다.  

-   원격 제어를 사용하여 컴퓨터 문제를 해결합니다.  

-   컴퓨터의 전원 소비를 관리 및 모니터링하도록 전원 관리 설정을 구현할 수 있습니다.  

Configuration Manager 콘솔은 거의 실시간으로 이전 작업을 모니터링합니다. 각 작업에 대한 알림과 상태 정보는 Configuration Manager 콘솔에서 확인할 수 있습니다. 데이터와 기록적 추세 정보를 캡처하려면 SQL Server Reporting Services의 통합 보고 기능을 사용합니다. 클라이언트에서 사이트에 대한 세부 정보를 클라이언트 상태로 제출합니다.  클라이언트 상태 정보는 클라이언트 및 클라이언트 활동의 상태에 대한 데이터를 제공하며, 콘솔에서 또는 Configuration Manager에 대한 기본 제공 보고서를 사용하여 볼 수 있습니다. 이 데이터를 통해 응답하지 않는 컴퓨터를 식별하고 경우에 따라 문제가 자동으로 해결됩니다.  

 클라이언트의 관리 작업에 대한 자세한 내용은 [System Center Configuration Manager에서 클라이언트를 관리하는 방법](../../core/clients/manage/manage-clients.md) 및 [System Center Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 관리하는 방법](../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md)을 참조하세요. 보고서 사용 방법에 대한 자세한 내용은   
            [System Center Configuration Manager의 보고 소개](../../core/servers/manage/introduction-to-reporting.md)  

## <a name="configuration-manager-client-application"></a>Configuration Manager 클라이언트 애플리케이션  
 Configuration Manager 클라이언트 소프트웨어를 설치하면 Configuration Manager 클라이언트 애플리케이션도 설치됩니다. 소프트웨어 센터와 달리 Configuration Manager 클라이언트 애플리케이션은 최종 사용자가 아닌 지원 센터를 위해 고안되었습니다. 일부 구성 옵션을 사용하려면 로컬 관리자 권한이 필요하고, 대부분의 옵션을 사용하려면 Configuration Manager 클라이언트 애플리케이션의 작동 원리에 대한 기술적 지식이 필요합니다. 이 애플리케이션을 사용하여 클라이언트에서 다음 작업을 수행할 수 있습니다.  

-   빌드 번호, 할당된 사이트, 통신 중인 관리 지점, 클라이언트가 사용하는 인증서가 PKI(공개 키 인프라) 인증서인지, 아니면 자체 서명된 인증서인지 등 클라이언트에 대한 속성을 볼 수 있습니다.  

-   클라이언트가 처음으로 설치된 이후 클라이언트 정책이 성공적으로 다운로드되었는지 확인합니다. 또한 Configuration Manager 콘솔에 구성된 클라이언트 설정에 따라 예상대로 클라이언트 설정이 사용 또는 사용하지 않도록 설정되었는지 확인합니다.  

-   클라이언트 작업을 시작합니다. 예를 들어 Configuration Manager 콘솔에서 최근 구성이 변경된 경우 클라이언트 정책을 다운로드하고 다음 예약 시간까지 기다리지 않습니다.  

-   클라이언트를 Configuration Manager 사이트에 수동으로 할당하거나 사이트를 찾습니다. 그런 다음 DNS(Domain Name System)로 게시하는 관리 지점에 대해 DNS 접미사를 지정합니다.  

-   파일을 일시적으로 저장하는 클라이언트 캐시를 구성합니다. 이후 소프트웨어 설치에 더 많은 디스크 공간이 필요하면 캐시에서 파일을 삭제합니다.  

-   인터넷 기반 클라이언트 관리에 대한 설정을 구성할 수 있습니다.  

-   클라이언트에 배포된 구성 기준을 보고, 호환성 평가를 시작하며, 호환성 보고서를 볼 수 있습니다.  
