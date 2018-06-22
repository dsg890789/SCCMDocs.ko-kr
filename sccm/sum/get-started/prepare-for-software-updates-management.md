---
title: 소프트웨어 업데이트 관리 준비
titleSuffix: Configuration Manager
description: 업데이트 관리를 준비하려면 System Center Configuration Manager 콘솔에 준수 평가 데이터가 표시되도록 이 작업을 완료합니다.
author: aczechowski
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 01907900-e28b-4cd7-9479-42906416707b
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: f2608d8cd46572a0fbcbafc6bc8c0f5e013356a2
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32353623"
---
# <a name="prepare-for-software-updates-management"></a>소프트웨어 업데이트 관리 준비

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 콘솔에 소프트웨어 업데이트의 준수 평가 데이터가 표시되기 전에, 그리고 클라이언트 컴퓨터에 소프트웨어 업데이트를 배포하기 전에 먼저 다음 섹션의 단계를 완료해야 합니다.

## <a name="step-1-install-a-software-update-point"></a>1단계: 소프트웨어 업데이트 지점 설치  
소프트웨어 업데이트 준수 평가를 사용하고 클라이언트에 소프트웨어 업데이트를 배포하려면 중앙 관리 사이트, 독립 실행형 기본 사이트 등에 소프트웨어 업데이트 지점이 필요합니다. 보조 사이트에서는 소프트웨어 업데이트 지점이 선택 사항입니다. 자세한 내용은 [소프트웨어 업데이트 지점 설치](install-a-software-update-point.md)를 참조하세요.  

## <a name="step-2-synchronize-software-updates"></a>2단계: 소프트웨어 업데이트 동기화
소프트웨어 업데이트 동기화는 구성한 기준을 충족하는 소프트웨어 업데이트 메타데이터를 검색하는 프로세스입니다. 소프트웨어 업데이트를 동기화하기 전에는 소프트웨어 업데이트가 Configuration Manager 콘솔에 표시되지 않습니다. 자세한 내용은 [소프트웨어 업데이트 동기화](synchronize-software-updates.md)를 참조하세요.   

## <a name="step-3-configure-classifications-and-products-to-synchronize"></a>3단계: 동기화할 분류 및 제품 구성
이 구성은 중앙 관리 사이트나 독립 실행형 기본 사이트에서 수행합니다. 처음 소프트웨어 업데이트를 동기화한 후 Configuration Manager가 업데이트된 분류 및 제품 목록을 검색합니다. 이제 소프트웨어 업데이트 지점 구성 요소 속성의 새 옵션에서 선택할 수 있습니다. 새 분류 및 제품을 구성한 후 2단계를 반복하여 새 조건에 대한 소프트웨어 업데이트 메타데이터를 검색하도록 소프트웨어 업데이트 동기화를 시작합니다. 자세한 내용은 [동기화할 분류 및 제품 구성](configure-classifications-and-products.md)을 참조하세요.

## <a name="step-4-manage-settings-for-software-updates"></a>4단계: 소프트웨어 업데이트 설정 관리
소프트웨어 업데이트를 동기화한 후 소프트웨어 업데이트를 배포하기 전에 Configuration Manager 클라이언트 설정, 그룹 정책 구성 및 소프트웨어 업데이트 설정을 확인합니다. 자세한 내용은 [소프트웨어 업데이트 설정 관리](manage-settings-for-software-updates.md)를 참조하세요.
