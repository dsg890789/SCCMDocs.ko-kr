---
title: "원격 제어 | Microsoft 문서"
description: "System Center Configuration Manager의 원격 제어를 소개합니다."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 29350919-6a25-446b-a0da-05e8914fbb26
caps.latest.revision: "4"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: fe517e110036e09907fb070afe973b246ce4147c
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-remote-control-in-system-center-configuration-manager"></a>System Center Configuration Manager의 원격 제어 소개

*적용 대상: System Center Configuration Manager(현재 분기)*

원격 제어를 사용하여 원격으로 관리하거나 지원을 제공하고 또는 계층 구조에 있는 모든 클라이언트 컴퓨터를 볼 수 있습니다. 원격 제어를 사용하여 클라이언트 프로그램에서 발생하는 하드웨어 및 소프트웨어 구성 문제를 해결할 수 있으며 지원을 제공할 수 있습니다. Configuration Manager는 Configuration Manager 클라이언트에 대해 지원되는 운영 체제를 실행하는 모든 작업 그룹 컴퓨터 및 도메인에 조인된 컴퓨터의 원격 제어를 지원합니다. 자세한 내용은 [System Center Configuration Manager의 클라이언트 및 장치에 대해 지원되는 운영 체제](../../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)를 참조하세요.

또한 Configuration Manager로 클라이언트 설정을 구성하여 Configuration Manager 콘솔에서 Windows 원격 데스크톱 및 원격 지원을 실행할 수 있습니다.  

> [!NOTE]  
>  Configuration Manager 콘솔에서 작업 그룹에 있는 클라이언트 컴퓨터로 원격 지원 세션을 설정할 수 없습니다. 

 **자산 및 준수** > **장치**, 모든 장치 컬렉션, Windows 명령 프롬프트 창 또는 Widnows **시작** 메뉴의 Configuration Manager 콘솔에서 원격 제어 세션을 시작할 수 있습니다.  
