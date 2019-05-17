---
title: 업데이트 다시 설정 도구
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 콘솔 내 업데이트를 위해 업데이트 다시 설정 도구를 사용합니다.
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 25fa89d6-7e47-45a6-8f4e-70b77560fba6
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: ec78a903bd3fa897a240ea04ca7f14349f9a0acd
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65500966"
---
# <a name="update-reset-tool"></a>업데이트 다시 설정 도구

*적용 대상: System Center Configuration Manager(현재 분기)*  


버전 1706부터 Configuration Manager 기본 사이트 및 중앙 관리 사이트에는 Configuration Manager 업데이트 다시 설정 도구 **CMUpdateReset.exe**가 포함되어 있습니다. 콘솔 내 업데이트를 다운로드 또는 복제하는 데 문제가 있는 경우 이 도구를 사용하여 문제를 해결합니다. 이 도구는 사이트 서버의 ***\cd.latest\SMSSETUP\TOOLS*** 폴더에 있습니다.

계속 지원되는 현재 분기의 모든 버전에 이 도구를 사용할 수 있습니다.

[콘솔 내 업데이트](/sccm/core/servers/manage/install-in-console-updates)를 아직 설치하지 않았으며 오류 상태에 있는 경우 이 도구를 사용합니다. 실패한 상태는 업데이트 다운로드가 진행 중이지만 중단되었거나 시간에 지나치게 오래 걸리고 있음을 의미합니다. 비슷한 크기의 업데이트 패키지에 대해 예상되는 기존 시간보다 몇 시간 더 걸리는 경우를 오래 걸리는 것으로 간주합니다. 업데이트를 자식 기본 사이트로 복제하지 못한 것일 수도 있습니다.  

이 도구를 실행하면 지정한 업데이트에 대해 실행됩니다. 기본적으로 이 도구는 성공적으로 설치되었거나 다운로드된 업데이트를 삭제하지 않습니다.  

### <a name="prerequisites"></a>필수 구성 요소
이 도구를 실행하는 데 사용하는 계정에는 다음 권한이 필요합니다.
-   중앙 관리 사이트 및 계층 구조에 있는 각 기본 사이트의 사이트 데이터베이스에 대한 **읽기** 및 **쓰기** 권한 이러한 권한을 설정하려면 사용자 계정을 각 사이트의 Configuration Manager 데이터베이스에 **db_datawriter** 및 **db_datareader** [고정 데이터베이스 역할](/sql/relational-databases/security/authentication-access/database-level-roles#fixed-database-roles)의 구성원으로 추가할 수 있습니다. 이 도구는 보조 사이트와는 상호 작용하지 않습니다.
-   계층 구조의 최상위 사이트에 대한 **로컬 관리자**
-   서비스 연결 지점을 호스트하는 컴퓨터의 **로컬 관리자**

다시 설정하려는 업데이트 패키지의 GUID가 필요합니다. GUID를 가져오려면
  1.   콘솔에서 **관리** > **업데이트 및 서비스**로 이동합니다.
  2.   콘솔에서 열 하나의 머리글(예: **상태**)을 마우스 오른쪽 단추로 클릭하고 **패키지 GUID**를 선택하여 해당 열을 표시에 추가합니다.
  3.   이제 열에 업데이트 패키지 GUID가 표시됩니다.

> [!TIP]  
> GUID를 복사하려면 다시 설정하려는 업데이트 패키지에 대한 행을 선택하고 Ctrl+C를 눌러 해당 행을 복사합니다. 복사한 선택 항목을 텍스트 편집기에 붙여 넣은 다음 도구를 실행할 때 명령줄 매개 변수로 사용할 GUID만 복사할 수 있습니다.

### <a name="run-the-tool"></a>도구 실행    
이 도구는 계층의 최상위 사이트에서 실행해야 합니다.

이 도구를 실행하는 경우 명령줄 매개 변수를 사용하여 다음을 지정합니다.
  -   계층 구조의 최상위 계층 사이트에 있는 SQL Server
  -   최상위 계층 사이트에 있는 사이트 데이터베이스 이름
  -   다시 설정하려는 업데이트 패키지의 GUID

이 도구는 업데이트 상태에 따라 액세스해야 하는 추가 서버를 식별합니다.   

업데이트 패키지가 *다운로드 게시* 상태이면 도구는 패키지를 정리하지 않습니다. 선택적으로 force delete 매개 변수를 사용하여 성공적으로 다운로드한 업데이트를 강제로 제거할 수 있습니다(이 항목 뒷부분에 나오는 명령줄 매개 변수 참조).

도구가 실행된 후에 다음 작업을 수행합니다.
-   패키지가 삭제된 경우 최상위 계층 사이트에서 SMS_Executive 서비스를 다시 시작합니다. 그런 후 패키지를 다시 다운로드할 수 있도록 업데이트를 확인합니다.
-   패키지가 삭제되지 않은 경우 어떤 작업도 필요하지 않습니다. 업데이트를 다시 초기화한 다음 복제 또는 설치를 다시 시작합니다.

**명령줄 매개 변수:**  


|                        매개 변수                         |                                                       설명                                                        |
|----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|
| **-S &lt;최상위 계층 사이트에 있는 SQL Server의 FQDN>** | *필수* <br> 계층 구조에서 최상위 계층 사이트에 대한 사이트 데이터베이스를 호스트하는 SQL Server의 FQDN을 지정합니다. |
|                **-D &lt;데이터베이스 이름>**                 |                          *필수* <br> 최상위 계층 사이트에 있는 데이터베이스의 이름을 지정합니다.                          |
|                 **-P &lt;패키지 GUID>**                 |                        *필수* <br> 다시 설정하려는 업데이트 패키지에 대한 GUID를 지정합니다.                        |
|           **-I &lt;SQL Server 인스턴스 이름>**           |                    *선택 사항* <br> 사이트 데이터베이스를 호스트하는 SQL Server 인스턴스를 식별합니다.                     |
|                       **-FDELETE**                       |                       *선택 사항* <br> 성공적으로 다운로드한 업데이트 패키지를 강제로 삭제합니다.                        |

 **예:**  
 일반적인 시나리오에서는 다운로드 문제가 있는 업데이트를 다시 설정하려고 할 것입니다. SQL Server FQDN은 *server1.fabrikam.com*, 사이트 데이터베이스는 *CM_XYZ*, 패키지 GUID는 *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*입니다.  실행: ***CMUpdateReset.exe -S server1.fabrikam.com -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***

 좀 더 극단적인 시나리오에서는 문제가 있는 업데이트 패키지를 강제로 삭제하려고 할 수 있습니다. SQL Server FQDN은 *server1.fabrikam.com*, 사이트 데이터베이스는 *CM_XYZ*, 패키지 GUID는 *61F16B3C-F1F6-4F9F-8647-2A524B0C802C*입니다.  실행: ***CMUpdateReset.exe  -FDELETE -S server1.fabrikam.com -D CM_XYZ -P 61F16B3C-F1F6-4F9F-8647-2A524B0C802C***
