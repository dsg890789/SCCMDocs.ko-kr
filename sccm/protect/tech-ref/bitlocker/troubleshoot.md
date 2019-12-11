---
title: BitLocker 문제 해결
titleSuffix: Configuration Manager
description: Configuration Manager에서 BitLocker 관리 문제를 해결 하는 방법을 알아봅니다.
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 134c5b50-edeb-4d60-aaca-944d26deb9ba
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bd379017be114a9599f9519b3cb56ee0c3f22470
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74662321"
---
# <a name="troubleshoot-bitlocker"></a>BitLocker 문제 해결

*적용 대상: Configuration Manager (현재 분기)*

이 문서의 정보를 참조 하 여 Configuration Manager의 BitLocker 관리 문제를 해결할 수 있습니다.

## <a name="server-error-in-self-service"></a>셀프 서비스에서 서버 오류가 발생 했습니다.

처음으로`https://webserver.contoso.com/SelfService`(셀프 서비스 포털)을 열려고 할 때 다음 오류 메시지가 표시 됩니다.

``` error
Configuration Error - Server Error in '/SelfService' Application

Description: An error occurred during the processing of a configuration file required to service this request. Please review the specific error details below and modify your configuration file appropriately.

Parser Error Message: Could not load file or assembly 'System.Web.Mvc, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35' or one of its dependencies. The system cannot find the file specified.
```

이 문제를 해결 하려면 웹 서버에 **MICROSOFT ASP.NET MVC 4.0** 에 대 한 [필수 구성 요소](/configmgr/protect/plan-design/bitlocker-management#prerequisites) 를 설치 했는지 확인 합니다.

## <a name="see-also"></a>참고 항목

BitLocker 이벤트 로그를 사용 하는 방법에 대 한 자세한 내용은 [bitlocker 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/about-event-logs)를 참조 하십시오.

알려진 오류 및 이벤트 로그 항목의 가능한 원인 목록은 다음 문서를 참조 하세요.

- [클라이언트 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/client-event-logs)
- [서버 이벤트 로그](/configmgr/protect/tech-ref/bitlocker/server-event-logs)

클라이언트가 BitLocker 관리 정책을 준수 하지 않는 것으로 보고 하는 이유를 이해 하려면 비호환 [코드](/configmgr/protect/tech-ref/bitlocker/non-compliance-codes)를 참조 하세요.
