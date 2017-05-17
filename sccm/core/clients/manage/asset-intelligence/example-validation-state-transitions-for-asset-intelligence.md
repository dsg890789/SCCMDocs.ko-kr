---
title: "Asset Intelligence에 대한 유효성 검사 상태 전환 예제 | Microsoft 문서"
description: "Asset Intelligence System Center Configuration Manager에서 Asset Intelligence에 대한 유효성 검사 상태 전환 예제를 참조하세요."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6230a6e5-a1f6-459b-84f1-07fbde0e70f0
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Human Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: d1e320c6498e034307557e8a182c36cef2de640b
ms.contentlocale: ko-kr
ms.lasthandoff: 12/16/2016


---
# <a name="example-validation-state-transitions-for-asset-intelligence-in-system-center-configuration-manager"></a>Asset Intelligence System Center Configuration Manager에서 Asset Intelligence에 대한 유효성 검사 상태 전환 예제

*적용 대상: System Center Configuration Manager(현재 분기)*

System Center Configuration Manager의 Asset Intelligence 유효성 검사 상태는 고정된 것이 아니며 수행하는 관리 작업에서 변경하면 Asset Intelligence 카탈로그에 저장된 데이터에 영향을 줄 수 있습니다. 이 항목에서는 가능한 유효성 검사 상태 전환에 대한 예제를 제공합니다.

##  <a name="BKMK_UncategorizedIsCategorized"></a> 분류되지 않은 카탈로그 항목이 관리자에 의해 분류되었습니다.  

|**상태 전환**|**상태 전환 설명**|  
|--------------------------|--------------------------------------|  
|**범주화되지 않음**|System Center Online에서 이전에 분류되지 않았거나 관리자가 Asset Intelligence 카탈로그에 입력한 인벤토리에 포함된 소프트웨어 제목입니다.|  
|**분류 되지 않은** 를 **사용자정의**|분류되지 않은 항목이 관리자에 의해 분류되었습니다.|  

##  <a name="BKMK_CategorizedIsReCategorized"></a> 분류된 카탈로그 항목이 관리자에 의해 다시 분류되었습니다.  

|**상태 전환**|**상태 전환 설명**|  
|--------------------------|--------------------------------------|  
|**유효성 검사됨**|카탈로그 항목이 System Center Online 연구원에 의해 정의되어 Asset Intelligence 카탈로그에 있습니다.|  
|**유효성 검사됨** 에서 **사용자 정의됨**|유효성 검사된 카탈로그 항목이 관리자에 의해 다시 분류되었습니다.|  

> [!NOTE]  
>  System Center Online에서 가져온 분류 정보는 데이터베이스에 저장되어 삭제할 수 없으므로 관리자는 나중에 System Center Online 분류로 되돌아갈 수 있습니다.  

##  <a name="BKMK_UserDefinedIsRecategorized"></a> 사용자 정의 카탈로그 항목이 System Center Online에 의해 다시 분류되었습니다.  

|**상태 전환**|**상태 전환 설명**|  
|--------------------------|--------------------------------------|  
|**범주화되지 않음**|인벤토리 소프트웨어 제목이 System Center Online이나 관리자에 의해 이전에 분류되지 않은 Asset Intelligence 카탈로그에 입력되었습니다.|  
|**사용자 정의됨**|분류되지 않은 항목이 관리자에 의해 분류되었습니다.|  
|**사용자 정의됨** 에서 **업데이트 가능**|사용자 정의 카탈로그 항목이 Asset Intelligence 카탈로그에 대한 이후의 수동 대량 업데이트 중에 System Center Online에서 다르게 분류되었습니다.<br /><br /> 관리자는 **충돌하는 소프트웨어 세부 정보 해결** 대화 상자에서 새 분류 정보를 사용할지 이전의 사용자 정의 값을 사용할지 여부를 결정할 수 있습니다.|  
|**업데이트 가능** 에서 **유효성 검사됨**|관리자가 **충돌하는 소프트웨어 세부 정보 해결** 대화 상자에서 이전 카탈로그가 업데이트될 때 System Center Online에서 받은 새 분류 정보를 사용합니다.|  
|or||  
|**업데이트 가능** 에서 **사용자 정의됨**|관리자가 **충돌하는 소프트웨어 세부 정보 해결** 대화 상자에서 이전 사용자 정의 값을 사용합니다.|  

> [!NOTE]  
>  System Center Online에서 가져온 분류 정보는 데이터베이스에 저장되어 삭제할 수 없으므로 관리자는 나중에 System Center Online 분류로 되돌아갈 수 있습니다.  

##  <a name="BKMK_UncategorizedIsSubmitted"></a> 분류되지 않은 카탈로그 항목이 분류를 위해 System Center Online으로 제출되었습니다.  

|**상태 전환**|**상태 전환 설명**|  
|--------------------------|--------------------------------------|  
|**범주화되지 않음**|인벤토리에 포함된 소프트웨어 제목이 System Center Online이나 관리자에 의해 이전에 분류되지 않은 Asset Intelligence 데이터베이스에 입력되었습니다.|  
|**범주화되지 않음** 에서 **보류 중**|분류되지 않은 항목이 분류되기 위해 관리자에 의해 System Center Online으로 제출되었습니다.|  
|**보류 중** 에서 **유효성 검사됨**|항목이 System Center Online에 의해 분류되었습니다. 관리자는 대량 카탈로그 업데이트나 Asset Intelligence 카탈로그 동기화를 사용하여 Asset Intelligence 카탈로그에 해당 항목을 가져옵니다. Asset Intelligence 동기화 지점 사이트 시스템 역할을 사용하면 둘 다 사용할 수 있습니다.|  

##  <a name="BKMK_UserDefinedIsSubmitted"></a> 사용자 정의 카탈로그 항목이 분류를 위해 System Center Online으로 제출되었습니다.  

|**상태 전환**|**상태 전환 설명**|  
|--------------------------|--------------------------------------|  
|**범주화되지 않음**|인벤토리에 포함된 소프트웨어 제목이 System Center Online이나 관리자에 의해 이전에 분류되지 않은 Asset Intelligence 데이터베이스에 입력되었습니다.|  
|**사용자 정의됨**|분류되지 않은 항목을 분류했습니다.|  
|**사용자 정의됨** 에서 **보류 중**|사용자 정의 항목을 분류를 위해 System Center Online에 제출했습니다.|  
|**보류 중** 에서 **업데이트 가능**|사용자 정의된 카탈로그 항목이 후속 카탈로그 동기화 중 System Center Online에서 다르게 분류되었습니다. **충돌 해결** 작업을 사용하여 새 분류 정보를 사용할지 이전 사용자 정의 값을 사용할지 여부를 결정할 수 있습니다. 충돌 해결에 대한 자세한 내용은 [소프트웨어 세부 정보 충돌 해결](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails)을 참조하세요.|  
|**업데이트 가능** 에서 **유효성 검사됨**|**충돌 해결** 작업에서 이전 카탈로그 업데이트 중 System Center Online에서 받은 새 분류 정보를 선택합니다. 충돌 해결에 대한 자세한 내용은 [소프트웨어 세부 정보 충돌 해결](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails)을 참조하세요.|  
|or||  
|**업데이트 가능** 에서 **사용자 정의됨**|**충돌 해결** 작업에서 이전 사용자 정의 값을 사용하도록 선택합니다. 충돌 해결에 대한 자세한 내용은 [소프트웨어 세부 정보 충돌 해결](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ResolveSoftwareDetails)을 참조하세요.|  

> [!NOTE]  
>  System Center Online에서 가져온 분류 정보는 데이터베이스에 저장되어 삭제할 수 없으므로 관리자가 System Center Online 분류로 나중에 되돌아갈 수 있습니다.  

