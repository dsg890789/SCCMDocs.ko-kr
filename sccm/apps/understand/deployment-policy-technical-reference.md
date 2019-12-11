---
title: 응용 프로그램 배포 정책 기술 참조
titleSuffix: Configuration Manager
description: 응용 프로그램 배포 정책 문제 해결 Configuration Manager에 대 한 기술 참조입니다.
ms.date: 11/04/2019
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: troubleshooting
ms.assetid: bf24fb83-521f-4a41-ab8e-df70a6c10e78
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: b56a2b5b7ce6e1352bce6323aba0b5f918a2feb0
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74823333"
---
# <a name="application-deployment-policy"></a>애플리케이션 배포 정책

*적용 대상: System Center Configuration Manager(현재 분기)*

## <a name="policy-creation"></a>정책 만들기

응용 프로그램을 배포 하면 컬렉션에 응용 프로그램을 할당 하는 것을 나타내는 [SMS_ApplicationAssignment](/sccm/develop/reference/apps/sms_applicationassignment-server-wmi-class) 클래스 인스턴스가 만들어집니다. 이 활동은 **smsprov.dll**에서 추적할 수 있습니다.

<pre><code class="lang-text">SMS Provider    PutInstanceAsync <b>SMS_ApplicationAssignment</b>~
SMS Provider    Auditing: User CONTOSO\Admin created an instance of class SMS_ApplicationAssignment.~
</code></pre>

Configuration Manager 데이터베이스에서이 정보는 `CI_CIAssignments` 테이블에 저장 됩니다. 여기서 `AssignmentType` 2는 응용 프로그램 배포를 나타냅니다. 할당을 만들면 SMS 데이터베이스 모니터 구성 요소는 테이블의 변경 내용을 검색 한 후 CI 할당 (CIA) 정책을 처리 하도록 개체 복제 관리자에 게 알립니다. 그런 다음 Object Replication Manager 구성 요소는 데이터베이스에 응용 프로그램 할당에 대 한 정책을 만들고, 데이터베이스의 `Policy` 테이블에 저장 되며, 정책 ID는 응용 프로그램의 고유 ID를 기반으로 합니다. 이 활동은 할당 고유 ID를 참조 하 여 **objreplmgr .log** 에서 추적할 수 있습니다 .이 ID는 [시작 하기 전에](/sccm/apps/understand/app-deployment-technical-reference#before-you-begin) 섹션에서 참조 하는 SQL 쿼리에서 가져올 수 있습니다.

<pre><code class="lang-text">***** Processing Application Assignment {<b>3AC57DFE-3F87-4C59-930B-B9F57CB41B91</b>} *****
</code></pre>

응용 프로그램 할당에 대 한 정책은 아래와 비슷한 SQL 쿼리를 사용 하 여 데이터베이스에서 볼 수 있습니다.

```sql
SELECT P.PolicyID, PA.PolicyAssignmentID, PA.PADBID, PA.IsTombstoned, PA.LastUpdateTime FROM Policy P
JOIN PolicyAssignment PA ON P.PolicyID = PA.PolicyID
WHERE P.PolicyID = '{3AC57DFE-3F87-4C59-930B-B9F57CB41B91}' -- Replace Assignment Unique ID
```

## <a name="policy-targeting"></a>정책 대상

정책이 생성 된 후 정책 공급자 구성 요소는 응용 프로그램 배포의 대상으로 지정 된 컬렉션의 리소스에이 정책을 할당 합니다. 정책 대상 지정 정보는 데이터베이스의 `ResPolicyMap` 테이블에 저장 됩니다. 위의 쿼리에서 반환 된 PADBID를 사용 하 여 **policypv .log**에서이 작업을 추적할 수 있습니다. 그러나 여러 정책을 동시에 처리 하는 경우 로그에 기록 된 PADBID는 위의 쿼리에서 반환 된 PADBID 일치 하지 않을 수 있습니다.

<pre><code class="lang-text">~Policy or Policy Target Change Event triggered.
~Completed batch with beginning <b>PADBID = 16778403 ending PADBID = 16778403</b>.
</code></pre>

> [!NOTE]
> `ResPolicyMap` 테이블은 사용자 컬렉션에 **사용할 수** 있도록 배포 된 응용 프로그램에 대 한 대상 정보를 포함 하지 않습니다. 소프트웨어 센터는 관리 지점에서 이러한 응용 프로그램 목록을 쿼리 하 고, 사용자가 소프트웨어 센터에서 응용 프로그램을 요청할 때 이러한 응용 프로그램에 대 한 정책 대상 정보를 동적으로 생성 합니다.

## <a name="next-steps"></a>다음 단계

- [장치 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/device-deployment-technical-reference)
- [사용자 컬렉션에 응용 프로그램 배포](/sccm/apps/understand/user-deployment-technical-reference)
