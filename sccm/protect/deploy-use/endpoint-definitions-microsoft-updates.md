---
title: Microsoft에서 정의 다운로드
titleSuffix: Configuration Manager
description: Configuration Manager의 Microsoft 업데이트에서 Endpoint Protection 맬웨어 정의 다운로드를 사용하도록 설정하는 방법을 알아봅니다.
ms.date: 11/18/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: ab7626ae-d4bf-4ca6-ab25-c61f96800a02
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 1f0d8ac635d514e750584126458bfde6b5fc24ee
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75819916"
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-microsoft-updates"></a>Microsoft 업데이트에서 다운로드하기 위해 Endpoint Protection 맬웨어 정의를 사용하도록 설정

*적용 대상: Configuration Manager(현재 분기)*

Microsoft 업데이트에서 정의 업데이트를 다운로드하도록 선택하면 클라이언트는 맬웨어 방지 정책 대화 상자의 **보안 인텔리전스** 섹션에서 정의된 간격마다 Microsoft 업데이트 사이트를 확인합니다.

 이 방법은 클라이언트에서 Configuration Manager 사이트에 연결할 수 없는 경우 또는 사용자가 정의 업데이트를 시작할 수 있도록 하려는 경우에 유용할 수 있습니다.

> [!IMPORTANT]
> - 이 방법을 사용하여 정의 업데이트를 다운로드하려면 클라이언트가 인터넷을 통해 Microsoft 업데이트에 액세스할 수 있어야 합니다.
> - **정의 업데이트** 섹션의 이름이 Configuration Manager 버전 1902부터 **Security Intelligence 업데이트** 로 바뀌었습니다.

## <a name="using-the-microsoft-malware-protection-center-to-download-definitions"></a>Microsoft 맬웨어 보호 센터를 사용하여 정의 다운로드
 Microsoft 맬웨어 보호 센터에서 정의 업데이트를 다운로드하도록 클라이언트를 구성할 수 있습니다. 이 옵션은 Endpoint Protection 클라이언트가 다른 원본에서 업데이트를 다운로드할 수 없는 경우 정의 업데이트를 다운로드하는 데 사용됩니다. 이 업데이트 방법은 Configuration Manager 인프라에 문제가 있어 업데이트를 제공할 수 없는 경우에 유용할 수 있습니다.

> [!IMPORTANT]
>  이 방법을 사용하여 정의 업데이트를 다운로드하려면 클라이언트가 인터넷을 통해 Microsoft 업데이트에 액세스할 수 있어야 합니다.
> 
> 
> [!div class="button"]
> [다음 단계 >](endpoint-antimalware-policies.md)
> 
> [!div class="button"]
> [뒤로 >](endpoint-configure-alerts.md)
