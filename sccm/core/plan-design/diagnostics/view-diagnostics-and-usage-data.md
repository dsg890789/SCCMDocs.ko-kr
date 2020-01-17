---
title: 진단 데이터 보기
titleSuffix: Configuration Manager
description: 진단 및 사용량 현황 데이터를 보고 Configuration Manager 계층 구조에 중요한 정보가 포함되어 있지 않은지 확인합니다.
ms.date: 09/10/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 51cc45b2524895beb1cf3ead5839e4fc3a1b11fb
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75800766"
---
# <a name="how-to-view-diagnostics-and-usage-data-for-configuration-manager"></a>Configuration Manager의 진단 및 사용량 데이터를 보는 방법

*적용 대상: Configuration Manager(현재 분기)*

Configuration Manager 계층 구조에서 진단 및 사용량 데이터를 보면 여기에 중요하거나 식별할 수 있는 정보가 포함되지 않았는지 확인할 수 있습니다. 사이트는 사이트 데이터베이스의 **TEL_TelemetryResults** 테이블에 진단 데이터를 요약하고 저장합니다. 이렇게 하면 프로그래밍 방식으로 사용할 수 있고 효율적인 데이터 형식이 지정됩니다.

이 문서의 정보는 Microsoft로 전송되는 정확한 데이터의 보기를 제공합니다. 이 보기는 데이터 분석 등의 다른 목적에 사용하기 위한 것은 아닙니다.  

## <a name="view-data-in-database"></a>데이터베이스의 데이터 보기

다음 SQL 명령을 사용하면 이 테이블의 내용을 볼 수 있으며 전송되는 정확한 데이터를 보여 줍니다.  

``` SQL
SELECT * FROM TEL_TelemetryResults
```

## <a name="export-the-data"></a>데이터 내보내기

서비스 연결점이 오프라인 모드인 경우 서비스 연결 도구를 사용하여 현재 데이터를 쉼표로 구분된 값(CSV) 파일로 내보냅니다. **-Export** 매개 변수가 있는 서비스 연결 지점에서 서비스 연결 도구를 실행합니다.

자세한 내용은 [서비스 연결 도구 사용](/sccm/core/servers/manage/use-the-service-connection-tool)을 참조하세요.

## <a name="bkmk_hashes"></a> 단방향 해시

일부 데이터는 임의의 영숫자 문자열로 구성됩니다. Configuration Manager는 SHA-256 알고리즘을 사용하여 단방향 해시를 만듭니다. 이 프로세스는 Microsoft에서 잠재적으로 중요한 데이터를 수집하지 않는지 확인합니다. 해시된 데이터는 상관관계 및 비교 목적으로 계속 사용할 수 있습니다.

예를 들어 사이트 데이터베이스에서 테이블 이름을 수집하는 대신 각 테이블 이름에 대해 단방향 해시를 캡처합니다. 이 동작은 사용자 지정 테이블 이름이 표시되지 않는지 확인합니다. 그러면 Microsoft에서는 기본 SQL 테이블 이름의 동일한 단방향 해시 프로세스를 수행합니다. 두 쿼리의 결과를 비교하면 제품 기본값에서 데이터베이스 스키마의 편차가 확인됩니다. 이 정보는 SQL 스키마 변경이 필요한 업데이트 개선에 사용됩니다.  

원시 데이터를 볼 때 데이터의 각 행에는 해시된 공통 값이 표시됩니다. 이 해시는 계층 구조 ID입니다. 고객 또는 원본을 식별하지 않고 동일한 계층 구조와 데이터의 상관관계를 지정하는 데 사용됩니다.

### <a name="how-the-one-way-hash-works"></a>단방향 해시가 작동하는 방식

1. Configuration Manager 데이터베이스에 대해 SQL Management Studio에서 다음 SQL 쿼리를 실행하여 계층 구조 ID를 가져옵니다.

    ``` SQL
    select [dbo].[fnGetHierarchyID]()
    ```

2. 다음 Windows PowerShell 스크립트를 사용하여 계층 구조 ID의 단방향 해시를 수행합니다.  

    ``` PowerShell
    Param( [Parameter(Mandatory=$True)] [string]$value )  
      $guid = [System.Guid]::NewGuid()  
      if( [System.Guid]::TryParse($value,[ref] $guid) -eq $true ) {  
      #many of the values we hash are Guids  
      $bytesToHash = $guid.ToByteArray()  
    } else {  
      #otherwise hash as string (unicode)  
      $ue = New-Object System.Text.UnicodeEncoding  
      $bytesToHash = $ue.GetBytes($value)
    }  
      # Load Hash Provider (https://en.wikipedia.org/wiki/SHA-2)
    $hashAlgorithm = [System.Security.Cryptography.SHA256Cng]::Create()
    # Hash the input
    $hashedBytes = $hashAlgorithm.ComputeHash($bytesToHash)
    # Base64 encode the result for transport
    $result = [Convert]::ToBase64String($hashedBytes)
    return $result
    ```

3. 원시 데이터의 GUID에 스크립트 출력을 비교합니다. 이 프로세스는 데이터를 가리는 방법을 보여 줍니다.
