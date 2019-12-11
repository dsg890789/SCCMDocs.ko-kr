---
title: 응용 프로그램 배포 기술 참조 문제 해결
titleSuffix: Configuration Manager
description: Configuration Manager의 응용 프로그램 배포 문제 해결에 대 한 기술 참조입니다.
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: a4eb09c8-e570-4369-9adb-ded9c8ad3400
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: a436c7acd254d9b07289eb0f5ddce6f75d93fa43
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74823443"
---
# <a name="technical-reference-for-application-deployment-in-configuration-manager"></a>Configuration Manager에서 애플리케이션 배포에 대한 기술 참조

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 응용 프로그램 배포의 작동 방식에 대해 알아봅니다.

## <a name="before-you-begin"></a>시작하기 전에

응용 프로그램 배포 문제를 해결 하는 경우 클라이언트 로그를 검토할 때 유용할 수 있는 여러 항목이 있습니다. 이 항목은 다음과 같습니다.

- 응용 프로그램 CI ID
- 응용 프로그램 고유 ID
- 배포 유형 고유 ID
- 응용 프로그램 배포 고유 ID (할당 고유 ID 라고도 함)
- 응용 프로그램 배포 목적
- 콘텐츠 고유 ID
- 컬렉션 ID 및 이름
- 컬렉션 형식

문제 해결을 간소화 하기 위해 Configuration Manager 데이터베이스에 대해 아래와 비슷한 SQL 쿼리를 실행 하 여 위에 나열 된 정보를 얻을 수 있습니다.

```sql
SELECT APP.CI_ID [App CI ID], APP.CI_UniqueID [App Unique ID], APP.DisplayName [App Name],
DT.CI_UniqueID [DT Unique ID], DT.ContentId [DT Content ID],
CIA.Assignment_UniqueID [Assignment ID], CIA.CollectionID, CIA.CollectionName,
CASE CIA.OfferTypeID WHEN 0 THEN 'Required' WHEN 2 THEN 'Available' WHEN 3 THEN 'Simulate' ELSE 'Unknown' END AS [Deployment Purpose],
CASE C.CollectionType WHEN 1 THEN 'User Collection' WHEN 2 THEN 'Device Collection' ELSE 'Unknown' END AS [Collection Type],
DT.Technology, DT.DisplayName [DT Name]
FROM fn_ListApplicationCIs(1033) APP
JOIN fn_ListDeploymentTypeCIs(1033) DT ON DT.AppModelName = APP.ModelName AND DT.IsLatest = 1
LEFT JOIN v_CIAssignmentToCI CIACI ON CIACI.CI_ID = APP.CI_ID
LEFT JOIN v_CIAssignment CIA ON CIACI.AssignmentID = CIA.AssignmentID
LEFT JOIN v_Collection C ON C.CollectionID = CIA.CollectionID
WHERE APP.IsLatest = 1 AND APP.DisplayName = 'Application Name' -- Replace Application Name
```

> [!IMPORTANT]
> 이 쿼리를 실행 하는 경우 응용 프로그램 속성의 소프트웨어 센터 탭에 나열 된 지역화 된 응용 프로그램 이름을 사용 하는 대신 응용 프로그램 속성의 일반 정보 탭에 나열 된 응용 프로그램 이름을 사용 **해야 합니다** .

## <a name="next-steps"></a>다음 단계

- [애플리케이션 배포 정책](/sccm/apps/understand/deployment-policy-technical-reference)
