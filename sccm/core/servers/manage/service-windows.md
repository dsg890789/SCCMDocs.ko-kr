---
title: "서비스 기간 | Microsoft 문서"
description: "서비스 기간을 사용하여 System Center Configuration Manager 사이트에서 업데이트를 설치할 수 있는 시기를 제어할 수 있습니다."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca4886d4-7173-46be-8dcd-1657d5b0deb9
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d06a2a955ff59fa84bb844033fe31874fc735087
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
#  <a name="service-windows-for-site-servers"></a>사이트 서버에 대한 서비스 기간

*적용 대상: System Center Configuration Manager(현재 분기)*

중앙 관리 사이트와 기본 사이트에서 서비스 기간을 구성하여 콘솔 내 업데이트를 설치할 수 있는 시기를 제어할 수 있습니다.  여러 기간을 구성할 수 있으며, 업데이트를 설치할 수 있는 기간은 해당 사이트 서버에 대한 모든 서비스 기간의 조합으로 결정됩니다.

서비스 기간이 구성되지 않은 경우:
- **최상위 계층 사이트**(중앙 관리 사이트 또는 독립 실행형 기본 사이트) - 업데이트 설치를 시작할 시기를 사용자가 선택합니다.
- **자식 기본 사이트** - 중앙 관리 사이트에서 업데이트 설치가 완료된 후 업데이트가 자동으로 설치됩니다.
- **보조 사이트** - 업데이트가 자동으로 시작되지 않습니다. 대신 부모 기본 사이트에서 업데이트 설치를 완료한 후 콘솔 내에서 업데이트 설치를 수동으로 시작해야 합니다.

서비스 기간이 구성된 경우:
- **최상위 계층 사이트** - Configuration Manager 콘솔 내에서 새 업데이트 설치를 시작할 수 없습니다. 서비스 기간이 구성된 경우에도 사이트에서는 업데이트를 자동으로 다운로드하여 언제든 다운로드를 설치할 수 있도록 준비합니다.  
- **자식 기본 사이트** - 중앙 관리 사이트에 설치된 업데이트가 기본 사이트에 다운로드되지만 자동으로 시작되지는 않습니다. 서비스 기간의 사용으로 인해 차단된 기간 동안 업데이트 설치를 수동으로 시작할 수 없습니다. 서비스 기간이 더 이상 업데이트 설치를 차단하지 않을 때 업데이트 설치가 자동으로 시작됩니다.
- **보조 사이트** - 서비스 기간을 지원하지 않으면 업데이트를 자동으로 설치하지 않습니다. 보조 사이트의 기본 부모 사이트에서 업데이트를 설치한 후 콘솔 내에서 보조 사이트의 업데이트를 시작할 수 있습니다.

## <a name="to-configure-a-service-window"></a>서비스 기간을 구성하려면

1.  Configuration Manager 콘솔에서 **관리** > **사이트 구성** > **사이트**를 열고 서비스 기간을 구성할 사이트 서버를 선택합니다.  

2.  이제, 사이트 서버 **속성** 을 편집하고 **서비스 기간** 탭을 선택한 다음 해당 사이트 서버의 서비스 기간을 하나 이상 설정할 수 있습니다.  
