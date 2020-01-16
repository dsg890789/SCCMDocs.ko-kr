---
title: 온-프레미스 MDM에 대한 디바이스 등록
titleSuffix: Configuration Manager
description: Configuration Manager에서 온-프레미스 MDM (모바일 장치 관리)에 대 한 장치를 등록 하는 방법에 대해 알아봅니다.
ms.date: 01/13/2020
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 647cb65a078c5bd8a7b3b90667ecbfe3f69a33db
ms.sourcegitcommit: 4ca147f2bb3de35bd5089743c832e00bc3babd19
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/15/2020
ms.locfileid: "76032998"
---
# <a name="enroll-devices-for-on-premises-mdm-in-configuration-manager"></a>Configuration Manager에서 온-프레미스 MDM에 대 한 장치 등록

*적용 대상: Configuration Manager (현재 분기)*

Configuration Manager 온-프레미스 MDM (모바일 장치 관리)을 사용 하 여 장치를 관리 하려면 먼저 등록 해야 합니다. 그런 다음 Configuration Manager 관리 작업을 위해 장치와 통신할 수 있습니다. Configuration Manager는 장치를 등록 하는 두 가지 방법을 제공 합니다.

- **사용자 등록**: 사용자가 자신의 장치에서 등록 프로세스를 시작 합니다. 사용자 등록이 성공 하려면 장치에 신뢰할 수 있는 루트 인증서를 설치 하 고 클라이언트 설정에서 등록을 위해 사용자를 프로 비전 합니다. 장치를 등록 하려면 사용자가 자격 증명을 입력 하기만 하면 됩니다.

    자세한 내용은 [사용자가 장치를 등록 하는 방법](/configmgr/mdm/deploy-use/user-enroll-devices-on-premises-mdm)을 참조 하세요.

- **대량 등록**: 장치의 사용자가 등록을 시작 하지 않습니다. Configuration Manager에서 대량 등록 패키지를 만듭니다. 장치에서 열 때 패키지는 장치를 등록 하는 데 필요한 정보를 제공 합니다.

    자세한 내용은 [장치를 대량 등록 하는 방법](/configmgr/mdm/deploy-use/bulk-enroll-devices-on-premises-mdm)을 참조 하세요.

온-프레미스 MDM에서 장치 등록에 대해 Configuration Manager 지 원하는 OS 버전에 대 한 자세한 내용은 [지원 되는 구성](/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices#bkmk_OnpremOS)을 참조 하세요.
