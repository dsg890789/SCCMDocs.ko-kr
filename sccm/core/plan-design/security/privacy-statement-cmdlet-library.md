---
title: cmdlet의 개인정보처리방침
titleSuffix: Configuration Manager
description: Microsoft에서 Configuration Manager cmdlet과 관련된 데이터를 수집하고 사용하는 방법을 알아봅니다.
ms.date: 01/3/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bec00fb4-1ac0-4e49-b330-0871b3722459
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: e777c509ae0461120ae195712aaecf7f44813261
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70889228"
---
# <a name="configuration-manager-cmdlet-library-privacy-statement"></a>Configuration Manager cmdlet 라이브러리 개인정보처리방침

*적용 대상: System Center Configuration Manager(현재 분기)*

이 개인 정보 취급 방침에서는 System Center Configuration Manager Cmdlet 라이브러리에 대한 기능을 다룹니다.  

## <a name="usage-data"></a>사용량 현황 데이터  

#### <a name="what-this-feature-does"></a>이 기능의 용도

System Center Configuration Manager cmdlet 라이브러리를 사용하면 Windows PowerShell cmdlet 및 스크립트를 사용하여 Configuration Manager 계층 구조를 관리할 수 있습니다. Cmdlet 라이브러리는 경향과 사용 패턴을 식별하기 위해 라이브러리에 포함된 cmdlet의 사용 방법에 대한 정보를 수집합니다. 또한 cmdlet 라이브러리는 cmdlet을 사용할 때 나타나는 오류의 유형과 개수를 수집합니다.  

#### <a name="information-collected-processed-or-transmitted"></a>정보의 수집, 처리 또는 전송
   
수집되는 사용량 현황 데이터에는 cmdlet의 시작, 중지 및 종료, 사용되지 않는 cmdlet의 실행 및 cmdlet과 관련된 SMS 공급자 작업에 대한 활동 메트릭이 포함됩니다. 이 정보는 개인적으로 식별할 수 없습니다. 수집되는 오류 정보에는 cmdlet에서 반환하는 오류와 예외 오류에 대한 오류 세부 정보가 포함됩니다. 일부 오류 세부 정보 보고서에는 컴퓨터에 연결된 디바이스에 대한 일련 번호와 같은 개별 식별자가 의도하지 않게 포함될 수도 있습니다. Cmdlet 라이브러리는 오류 보고서에 있는 정보를 필터링하고 익명으로 처리하여 개인 식별자를 제거한 후에 Microsoft에 전송합니다.  

#### <a name="use-of-information"></a>정보의 사용
   
이 정보는 Microsoft에서 제공하는 제품과 서비스의 품질, 보안 및 무결성을 향상하기 위해 사용됩니다.  

#### <a name="choicecontrol"></a>선택/제어   

이 사용량 현황 데이터 기능은 기본적으로 사용하도록 설정됩니다. System Center Configuration Manager cmdlet 라이브러리에는 이 기능을 제어하기 위한 두 개의 레지스트리 키가 있습니다.  

 완전히 옵트아웃하려면 이 두 레지스트리 키 값을 설정합니다. 각 ETW(Windows용 이벤트 추적) 공급자에 대한 값입니다.  

- HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Provider:CeipLevel=0(드라이브 공급자에 대한 사용량 현황 데이터 옵트아웃)  

- HKLM\Software\Microsoft\ConfigMgr10\PowerShell\Microsoft.ConfigurationManagement.PowerShell.Cmdlets:CeipLevel=0(cmdlet에 대한 사용량 현황 데이터 옵트아웃)  

  사용량 현황 데이터 설정에 대한 변경 사항은 변경이 수행된 컴퓨터에만 적용됩니다.  


## <a name="next-steps"></a>다음 단계

[System Center Configuration Manager Cmdlet 라이브러리 설명서](https://docs.microsoft.com/powershell/sccm/configurationmanager/).   
