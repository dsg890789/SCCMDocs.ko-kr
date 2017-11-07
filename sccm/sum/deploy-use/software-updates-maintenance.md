---
title: "소프트웨어 업데이트 유지 관리"
titleSuffix: Configuration Manager
description: "Configuration Manager에서 업데이트를 유지 관리하려면 WSUS 정리 태스크를 예약하거나 수동으로 실행할 수 있습니다."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
ms.openlocfilehash: 51e103b09ced9916fc76f9c87654379b538248b4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="software-updates-maintenance"></a>소프트웨어 업데이트 유지 관리

*적용 대상: System Center Configuration Manager(현재 분기)*

Configuration Manager 콘솔에서 WSUS 정리 태스크를 예약 및 실행하거나, 소프트웨어 업데이트 지점 구성 요소 속성에서 WSUS 정리 태스크를 수동으로 실행할 수 있습니다. WSUS 정리 작업 실행을 선택하면 다음 소프트웨어 업데이트 동기화에서 실행됩니다. 만료된 소프트웨어 업데이트는 WSUS 서버에서 거부함 상태로 설정되고, 컴퓨터의 Windows 업데이트 에이전트에서는 이 소프트웨어 업데이트를 더는 검색하지 않습니다. 기본적으로 WSUS 정리 작업은 30일마다 실행됩니다.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>WSUS 정리 작업을 예약하고 실행하려면  

1.  Configuration Manager 콘솔에서 **관리** > **개요** > **사이트 구성** > **사이트**로 이동합니다.  

2.  **설정** 그룹에서 **사이트 구성 요소 구성** 을 클릭하고 **소프트웨어 업데이트 지점** 을 클릭하여 소프트웨어 업데이트 지점 구성 요소 속성을 엽니다.  

3.  **대체 규칙** 탭을 클릭하고, **WSUS 정리 마법사 실행**을 선택하고, **확인**을 클릭합니다.
