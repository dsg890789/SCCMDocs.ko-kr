---
title: 진단 데이터 수집
titleSuffix: Configuration Manager
description: Configuration Manager에서 자체 진단 및 사용량 현황 데이터를 수집하는 방법을 알아봅니다.
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 63ac768d4c2779be02c8258a964bb4181e246608
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75801514"
---
# <a name="how-diagnostics-and-usage-data-is-collected-by-configuration-manager"></a>Configuration Manager에서 진단 및 사용량 현황 데이터를 수집하는 방법

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager에 대한 진단 및 사용량 현황 데이터를 수집하기 위해 각 기본 사이트에서 매주 SQL Server 쿼리를 실행합니다. 다중 사이트 계층에서 데이터는 중앙 관리 사이트에 복제됩니다.  

계층의 최상위 사이트에서 서비스 연결 지점 사이트 시스템 역할은 업데이트를 확인할 때 이 정보를 제출합니다. 데이터를 전송하는 방법은 서비스 연결 지점 모드에 따라 달라집니다.  

-   **온라인 모드:** 진단 및 사용량 현황 데이터가 서비스 연결 지점에서 클라우드 서비스로 한 주에 한 번 자동으로 전송됩니다.  

-   **오프라인 모드:** 서비스 연결 도구를 사용하여 진단 및 사용량 현황 데이터가 수동으로 전송됩니다. 자세한 내용은 [Configuration Manager의 서비스 연결 도구 사용](../../../core/servers/manage/use-the-service-connection-tool.md)을 참조하세요.  

자세한 내용은 [서비스 연결 지점 정보](../../../core/servers/deploy/configure/about-the-service-connection-point.md)를 참조하세요.  
