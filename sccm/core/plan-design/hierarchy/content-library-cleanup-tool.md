---
title: 콘텐츠 라이브러리 정리 도구
titleSuffix: Configuration Manager
description: 콘텐츠 라이브러리 정리 도구를 사용하여 더 이상 Configuration Manager 배포와 연결되어 있지 않은 분리된 콘텐츠를 제거합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7efcd8eab0891cd953fe182cc97602a814df1049
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75800426"
---
# <a name="content-library-cleanup-tool"></a>콘텐츠 라이브러리 정리 도구

*적용 대상: Configuration Manager(현재 분기)*

콘텐츠 라이브러리 정리 명령줄 도구를 사용하여 배포 지점의 패키지 또는 애플리케이션과 더 이상 연결되지 않은 콘텐츠를 제거합니다. 이 유형의 콘텐츠는 *분리된 콘텐츠*라고 합니다. 이 도구는 이전 Configuration Manager 제품용으로 릴리스된 이전 버전의 유사 도구를 대체합니다.  

이 도구는 도구를 실행할 때 지정하는 배포 지점에 있는 콘텐츠에만 영향을 미칩니다. 이 도구로 사이트 서버에 있는 콘텐츠 라이브러리의 콘텐츠를 제거할 수는 없습니다.

사이트 서버의 `CD.Latest\SMSSETUP\TOOLS\ContentLibraryCleanup`에서 **ContentLibraryCleanup.exe**를 찾습니다.



## <a name="requirements"></a>요구 사항  

- 한 번에 하나의 배포 지점에 대해서만 도구를 실행합니다.  

- 정리할 배포 지점을 호스트하는 컴퓨터에서 직접 실행하거나 다른 컴퓨터에서 원격으로 실행합니다.  

- 이 도구를 실행하는 사용자 계정은 Configuration Manager에서 **전체 관리자** 보안 역할과 동일한 권한을 가지고 있어야 합니다.  



## <a name="modes-of-operation"></a>작동 모드

도구는 다음 두 가지 모드에서 실행합니다. [What-if](#what-if-mode) 및 [삭제](#delete-mode).

> [!Tip]  
> *what-if*로 시작합니다. 결과에 만족할 경우 *delete* 모드에서 결과를 실행합니다.  


### <a name="what-if-mode"></a>What-If 모드   

`/delete` 매개 변수를 지정하지 않으면 도구는 what-if 모드로 실행합니다. 이 모드는 배포 지점에서 삭제될 콘텐츠를 식별합니다.

- 이 모드에서 실행되는 도구는 데이터를 삭제하지 않습니다.  

- 도구는 삭제할 콘텐츠에 대한 정보를 로그 파일에 기록합니다. 각 잠재적 삭제를 확인하는 메시지가 사용자에게 표시되지 않습니다.  


### <a name="delete-mode"></a>삭제 모드   

`/delete` 매개 변수로 도구를 실행하면 도구가 삭제 모드에서 실행됩니다.

- 이 모드에서 실행될 경우 지정된 배포 지점에 있는 분리된 콘텐츠가 배포 지점의 콘텐츠 라이브러리에서 삭제될 수 있습니다.  

- 각 파일을 삭제하기 전에 도구는 삭제 여부를 확인합니다. **Y**(예) 또는 **N**(아니요)을 선택하거나, 추가 메시지를 건너뛰고 분리된 콘텐츠를 모두 삭제하려면 **모두 예**를 선택합니다.  


### <a name="log-file"></a>로그 파일

두 모드 중 하나로 도구가 실행되면 로그가 자동으로 생성됩니다. 다음 정보를 사용하여 로그 파일의 이름을 지정합니다. 
- 도구 실행 모드  
- 배포 지점 이름  
- 작업 날짜 및 시간  

도구가 완료되면 로그 파일이 Windows에서 자동으로 열립니다. 

기본적으로 도구는 해당 도구를 실행하는 사용자 계정의 임시 폴더에 로그 파일을 기록합니다. 이 위치는 도구를 실행하는 컴퓨터에 있으며 항상 도구의 대상은 아닙니다. `/log` 매개 변수를 사용하여 네트워크 공유를 비롯한 다른 위치로 로그 파일을 리디렉션합니다.



## <a name="run-the-tool"></a>도구 실행

도구를 실행하려면: 

1. 관리자 권한으로 명령 프롬프트를 엽니다. 디렉터리를 **ContentLibraryCleanup.exe**가 포함된 폴더로 변경합니다.  

2. 필수 [명령줄 매개 변수](#bkmk_params)와 사용할 선택적 매개 변수를 포함하는 명령줄을 입력합니다.



## <a name="bkmk_params"></a> 명령줄 매개 변수  

이러한 명령줄 매개 변수를 어떤 순서로든 사용할 수 있습니다.   

### <a name="required-parameters"></a>필수 매개 변수

|매개 변수|세부 정보|
|---------|-------|
| `/dp <distribution point FQDN>`  | 정리하려는 배포 지점의 FQDN(정규화된 도메인 이름)을 지정합니다. |
| `/ps <primary site FQDN>` | 보조 사이트의 배포 지점에서 콘텐츠를 정리하는 경우에만 *필수*입니다. 이 도구는 부모 기본 사이트에 연결하여 SMS 공급자에 대한 쿼리를 실행합니다. 이러한 쿼리를 통해 도구는 배포 지점에 있어야 할 콘텐츠를 결정합니다. 그런 다음, 제거할 분리된 콘텐츠를 식별할 수 있습니다. 보조 사이트에서 바로 필요한 세부 정보를 이용할 수 없기 때문에 부모 기본 사이트에 대한 이러한 연결은 보조 사이트에서 배포 지점에 대해 이루어져야 합니다.|
| `/sc <primary site code>`  | 보조 사이트의 배포 지점에서 콘텐츠를 정리하는 경우에만 *필수*입니다. 부모 기본 사이트의 사이트 코드를 지정합니다. |

#### <a name="example-scan-and-log-what-content-it-would-delete-what-if"></a>예제: 검사 및 삭제할 콘텐츠 로깅(what-if)
`ContentLibraryCleanup.exe /dp server1.contoso.com`

#### <a name="example-scan-and-log-content-for-a-dp-at-a-secondary-site"></a>예제: 보조 사이트에서 검사 및 DP 콘텐츠 로깅
`ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com /sc ABC` 


### <a name="optional-parameters"></a>선택적 매개 변수

|매개 변수|세부 정보|
|---------|-------|
|`/delete`| 배포 지점에서 콘텐츠를 삭제할 준비가 되면 이 매개 변수를 사용합니다. 콘텐츠를 삭제하기 전에 확인 메시지를 표시합니다. </br></br> 이 매개 변수를 사용하지 않는 경우 도구는 삭제할 콘텐츠에 대한 결과를 기록합니다. 이 매개 변수 없이는 배포 지점에서 어떠한 콘텐츠도 실제로 삭제하지 않습니다. |
| `/q` | 이 매개 변수는 모든 확인 메시지를 표시하지 않는 자동 모드로 도구를 실행합니다. 이 확인 메시지는 콘텐츠 삭제 시간을 포함하며 로그 파일을 자동으로 열지도 않습니다. |
| `/ps <primary site FQDN>` | 기본 사이트의 배포 지점에서 콘텐츠를 정리하는 경우에만 선택 사항입니다. 배포 지점이 속하는 기본 사이트의 FQDN을 지정합니다. |
| `/sc <primary site code>` | 기본 사이트의 배포 지점에서 콘텐츠를 정리하는 경우에만 선택 사항입니다. 배포 지점이 속하는 기본 사이트의 사이트 코드를 지정합니다. |
| `/log <log file directory>` | 도구가 로그 파일을 기록하는 위치를 지정합니다. 이 위치는 로컬 드라이브 또는 네트워크 공유일 수 있습니다.</br></br> 이 매개 변수를 사용하지 않는 경우 도구는 도구가 실행되는 컴퓨터의 사용자 임시 디렉터리에 로그 파일을 저장합니다.|

#### <a name="example-delete-content"></a>예제: 콘텐츠 삭제 
`ContentLibraryCleanup.exe /dp server1.contoso.com /delete`

#### <a name="example-delete-content-without-prompts"></a>예제: 확인 메시지 없이 콘텐츠 삭제
`ContentLibraryCleanup.exe /q /dp server1.contoso.com /delete` 

#### <a name="example-log-to-local-drive"></a>예제: 로컬 드라이브에 로깅
`ContentLibraryCleanup.exe /dp server1.contoso.com /log C:\Users\Administrator\Desktop` 

#### <a name="example-log-to-network-share"></a>예제: 네트워크 공유에 로깅
`ContentLibraryCleanup.exe /dp server1.contoso.com /log \\server\share`


### <a name="known-issue"></a>알려진 문제

패키지 또는 배포가 실패했거나 진행 중인 경우 도구는 다음 오류를 반환합니다. `System.InvalidOperationException: This content library cannot be cleaned up right now because package <packageID> is not fully installed.`

이 문제에 대한 해결 방법은 없습니다. 콘텐츠가 진행 중이거나 배포에 실패한 경우 도구는 분리된 파일을 안정적으로 식별할 수 없습니다. 도구는 이 문제를 해결할 때까지 콘텐츠를 정리할 수 없습니다.
