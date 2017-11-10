---
title: "Intune에 등록된 장치의 정책 원격 동기화"
titleSuffix: Configuration Manager
description: "Configuration Manager 콘솔에서 Intune에 등록된 장치의 정책을 동기화하는 방법 알아보기"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
caps.latest.revision: "18"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: a03ba69c679bcfdc54744314c7a4cb3ef8b2a7a0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/12/2017
---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 Intune에 등록된 장치의 정책 원격 동기화

*적용 대상: System Center Configuration Manager(현재 분기)*


Intune에 등록된 장치 자체의 회사 포털 앱에서 동기화를 요청하는 대신 Configuration Manager 콘솔에서 장치에 대한 정책 동기화를 요청할 수 있습니다. 

가상 하드 디스크 파일에 대한 중요 정보를 제공하려면

1.  **자산 및 준수** > **개요** > **장치** 아래에서 장치를 선택합니다.
2.  **원격 장치 작업** 메뉴에서 **동기화 요청 보내기**를 클릭합니다.


5~10분 후에 정책 변경 내용이 장치에 동기화됩니다. 각 장치에 대한 **속성** 대화 상자의 검색 데이터 섹션 및 **원격 동기화 상태**라는 장치 보기의 새 열에서 동기화 요청 상태 정보를 볼 수 있습니다.
