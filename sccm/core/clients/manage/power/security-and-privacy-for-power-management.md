---
title: 전원 관리에 대한 보안 및 개인 정보
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 전원 관리에 대한 보안 및 개인 정보를 확인합니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 47ddbf358426b7683dab42b4f7a6a89ad8e631de
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="security-and-privacy-for-power-management-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 전원 관리에 대한 보안 및 개인 정보

*적용 대상: System Center Configuration Manager(현재 분기)*

이 섹션에서는 System Center Configuration Manager에서 전원 관리에 대한 보안과 개인 정보에 대해 설명합니다.  

## <a name="security-best-practices-for-power-management"></a>전원 관리의 보안 모범 사례  
 전원 관리에 대한 보안 관련 모범 사례가 없습니다.  

## <a name="privacy-information-for-power-management"></a>전원 관리를 위한 개인 정보  
 전원 관리 전원 사용을 모니터링 하 고 업무 시간 및 업무 외 시간 동안 컴퓨터에 전원 설정을 적용 하려면 Windows에서 제공 하는 기능을 사용 합니다. Configuration Manager는 전원 사용 정보를 컴퓨터에서 수집하며 여기에는 사용자가 컴퓨터를 사용하는 시간에 대한 데이터가 포함됩니다. Configuration Manager가 각 컴퓨터가 아닌 컬렉션에 대해 전원 사용을 모니터링하지만 컬렉션에는 한 대의 컴퓨터만 들어갈 수 있습니다. 전원 관리는 기본적으로 사용하지 않도록 설정되어 있으며 관리자가 구성해야 합니다.  

 전원 사용 정보는 Configuration Manager 데이터베이스에 저장되며 Microsoft로 전송되지 않습니다. 세부 정보는 31일, 요약 정보는 13개월 동안 데이터베이스에 보존됩니다. 삭제 간격을 구성할 수 없습니다.  

 전원 관리를 구성하기 전에 개인 정보 요구 사항을 확인합니다.  
