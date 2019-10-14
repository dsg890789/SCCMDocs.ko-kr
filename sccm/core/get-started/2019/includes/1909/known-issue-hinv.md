---
author: aczechowski
ms.author: aaroncz
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: include
ms.date: 10/04/2019
ms.collection: M365-identity-device-management
ms.openlocfilehash: d7d24b4032f893cfbbb347a1d0a37090f308c365
ms.sourcegitcommit: b631fcb2669ac2a5801e70620b0c3e81431bea8f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/05/2019
ms.locfileid: "71975529"
---
### <a name="ki_hinv"></a> 하드웨어 인벤토리 보고서

<!--5468413-->
하드웨어 인벤토리를 사용하는 보고서를 실행하려고 하면 오류가 반환됩니다. 예를 들어 BitLocker 보고서는 다음 메시지와 비슷한 오류를 반환합니다.

```
Microsoft.Reporting.WinForms.ReportServerException
An error has occurred during report processing. (rsProcessingAborted)
```

**dataldr.log** 파일에 다음과 같은 오류가 표시될 수도 있습니다.

`[42S22][207][Microsoft][SQL Server Native Client 11.0][SQL Server]Invalid column name 'FileTimeStamp00'. : pOFFICE_ADDIN_DATA`

하드웨어 인벤토리를 사용하는 콘솔 대시보드도 영향을 받을 수 있습니다.

이 문제는 특정 하드웨어 인벤토리 테이블에 대한 데이터베이스 스키마 변경 때문에 발생합니다.

#### <a name="workaround"></a>해결 방법

해결 방법은 기존 특성을 데이터베이스에서 삭제하는 것입니다. 그런 다음 dataloader 사이트 구성 요소는 새 특성을 만들 수 있습니다. 사이트 데이터베이스 서버에서 다음 SQL 스크립트를 실행하여 테이블 스키마를 수정합니다.

``` SQL
IF NOT EXISTS (SELECT * FROM SYS.columns WHERE name = 'FileTimestamp00' AND object_id = OBJECT_ID('OFFICE_ADDIN_DATA'))
BEGIN
       DELETE am
       FROM AttributeMap am
       INNER JOIN GroupMap gm ON am.GroupKey=gm.GroupKey
       WHERE gm.GroupClass='MICROSOFT|OFFICE_ADDIN|1.0'
       AND am.AttributeName='FileTimeStamp'

       PRINT 'Fix OFFICE_ADDIN_DATA schema'
END
```
