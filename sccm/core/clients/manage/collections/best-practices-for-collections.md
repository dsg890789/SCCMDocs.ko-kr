---
title: 컬렉션 모범 사례
titleSuffix: Configuration Manager
description: System Center Configuration Manager에서 컬렉션에 대한 모범 사례를 확인합니다.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 7a2abb79-9ae5-4a25-9e18-5dcf528de3bf
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: be96b106424c6340a27b015a06e0c3d06e3257d6
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70890190"
---
# <a name="best-practices-for-collections-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 컬렉션에 대한 모범 사례

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager에서 컬렉션에 대한 다음 모범 사례를 사용합니다.  

## <a name="do-not-use-incremental-updates-for-a-large-number-of-collections"></a>많은 컬렉션에 대해 증분 업데이트를 사용하지 마세요.  
 **이 컬렉션에 대해 증분 업데이트 사용** 옵션을 사용하도록 설정하는 경우 많은 컬렉션에 대해 이 구성을 사용하도록 설정하면 평가가 지연될 수 있습니다. 계층에서 약 200개의 컬렉션이 임계값입니다. 정확한 수는 다음 요인에 따라 달라집니다.  

-   컬렉션의 총 수  

-   계층에서 추가되고 변경되는 새 리소스의 빈도  

-   계층의 클라이언트 수  

-   계층의 컬렉션 멤버 관리 규칙의 복잡성  

## <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>유지 관리 기간을 중요 소프트웨어 업데이트를 충분히 배포할 수 있을 만큼 설정합니다.  
 Configuration Manager가 디바이스에 소프트웨어를 설치할 수 있는 횟수를 제한하도록 디바이스 컬렉션에 대한 유지 관리 기간을 구성할 수 있습니다. 유지 관리 기간을 너무 짧게 구성하면 클라이언트는 중요 소프트웨어 업데이트를 설치하지 못할 수도 있으며, 이 경우 클라이언트는 해당 소프트웨어 업데이트로 방지할 수 있었던 공격에 취약해집니다.  
