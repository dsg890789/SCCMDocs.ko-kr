---
title: "진단 데이터 보기 | System Center Configuration Manager"
description: "진단 및 사용 현황 데이터를 보고 System Center Configuration Manager 계층 구조에 중요한 정보가 포함되어 있지 않은지 확인합니다."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 594eb284-0d93-4c5d-9ae6-f0f71203682a
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
translationtype: Human Translation
ms.sourcegitcommit: 1134bb2f04152288e72d40b1b1083f415cb4e900
ms.openlocfilehash: 5d1382d4912d03fb38bfc2f07edfb361c0ac6139


---
# <a name="how-to-view-diagnostics-and-usage-data-for-system-center-configuration-manager"></a>System Center Configuration Manager의 진단 및 사용 현황 데이터를 보는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager 계층 구조에서 진단 및 사용 현황 데이터를 보면 중요하거나 식별할 수 있는 정보가 포함되지 않았는지 확인할 수 있습니다. 원격 분석 데이터가 요약되어 사이트 데이터베이스의 **TEL_TelemetryResults** 테이블에 저장되며 프로그래밍 방식으로 사용 가능하고 효율적이 되도록 형식이 지정됩니다. 다음 옵션을 사용하여 Microsoft로 전송되는 정확한 데이터를 볼 수 있지만 이러한 옵션은 데이터 분석 등의 다른 목적에 사용하기 위한 것은 아닙니다.  

다음 SQL 명령을 사용하면 이 테이블의 내용을 볼 수 있으며 전송되는 정확한 데이터를 보여 줍니다(이 데이터를 텍스트 파일로 내보낼 수도 있음).  

-   **SELECT \* FROM TEL_TelemetryResults**  

> [!NOTE]  
>  버전 1602를 설치하기 전에 원격 분석 데이터를 저장하는 테이블은 **TelemetryResults**입니다.  

서비스 연결점이 오프라인 모드인 경우 서비스 연결 도구를 사용하여 현재 진단 및 사용 현황 데이터를 쉼표로 구분된 값(CSV) 파일로 내보낼 수 있습니다. **-Export** 매개 변수가 있는 서비스 연결 지점에서 서비스 연결 도구를 실행합니다.  

##  <a name="a-namebkmkhashesa-one-way-hashes"></a><a name="bkmk_hashes"></a> 단방향 해시  
일부 데이터는 임의의 영숫자 문자열로 구성됩니다. Configuration Manager에서는 SHA-256 알고리즘을 사용하는 단방향 해시를 사용하여 잠재적으로 중요한 데이터를 상관관계 및 비교 목적으로 사용할 수 있는 상태로 유지하면서 수집하지 않습니다. 예를 들어 사이트 데이터베이스에서 테이블 이름을 수집하는 대신 각 테이블 이름에 대해 단방향 해시가 캡처됩니다. 이렇게 하면 사용자 또는 타사 제품 추가 기능에서 만든 모든 사용자 지정 테이블 이름이 표시되지 않습니다. 사용자는 제품에서 기본적으로 제공되는 SQL 테이블 이름의 동일한 단방향 해시를 사용하고 비교하여 제품 기본값에 대한 데이터베이스 스키마의 편차를 확인할 수 있습니다. 이 데이터는 SQL 스키마 변경이 필요한 업데이트 개선에 사용됩니다.  

원시 데이터를 볼 때 데이터의 각 행에는 해시된 공통 값이 표시됩니다. 이는 계층 ID입니다. 이 해시된 값은 고객 또는 원본을 식별하지 않고 동일한 계층 구조와 데이터의 상관관계를 지정하는 데 사용됩니다.  

#### <a name="to-see-how-the-one-way-hash-works"></a>단방향 해시가 작동하는 방식을 보려면  

1.  Configuration Manager 데이터베이스에 대해 SQL Management Studio에서 SQL 문 **select [dbo].[fnGetHierarchyID](\)**를 실행하여 계층 구조 ID를 가져옵니다.  

2.  이제, 다음 Windows PowerShell 스크립트를 사용하여 데이터베이스에서 가져온 GUID의 단방향 해시를 수행합니다. 이를 원시 데이터의 계층 ID와 비교하여 이 데이터를 가리는 방법을 알아볼 수 있습니다.  

    ```  
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



<!--HONumber=Nov16_HO1-->


