---
title: "콘텐츠 라이브러리 정리 도구"
titleSuffix: Configuration Manager
description: "콘텐츠 라이브러리 정리 도구를 사용하여 더 이상 System Center Configuration Manager 배포와 연관이 없는 분리된 콘텐츠를 제거합니다."
ms.custom: na
ms.date: 4/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 226cbbb2-9afa-4e2e-a472-be989c0f0e11
caps.latest.revision: "4"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 334b79e675ea7804128b0feb9678de4ad06dbc93
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/04/2018
---
# <a name="the-content-library-cleanup-tool-for-system-center-configuration-manager"></a>System Center Configuration Manager용 콘텐츠 라이브러리 정리 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

 버전 1702부터 명령줄 도구(**ContentLibraryCleanup.exe**)를 사용하여 배포 지점의 패키지 또는 응용 프로그램과 더 이상 연결되지 않은 콘텐츠(분리된 콘텐츠)를 제거할 수 있습니다. 이 도구를 콘텐츠 라이브러리 정리 도구라고 하며 이 도구는 이전 Configuration Manager 제품용으로 릴리스된 이전 버전의 유사 도구를 대체합니다.  

이 도구는 도구를 실행할 때 지정하는 배포 지점에 있는 콘텐츠에만 영향을 미칩니다. 이 도구로 사이트 서버에 있는 콘텐츠 라이브러리의 콘텐츠를 제거할 수는 없습니다.

중앙 관리 사이트 또는 기본 사이트의 사이트 서버에 있는 *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* 폴더에서 **ContentLibraryCleanup.exe**를 찾을 수 있습니다.

## <a name="requirements"></a>요구 사항  
 한 번에 하나의 배포 지점에 대해서만 도구를 실행할 수 있습니다.  
 - 이 도구는 정리할 배포 지점을 호스트하는 컴퓨터에서 직접 실행하거나 다른 서버에서 원격으로 실행할 수 있습니다.
 - 도구를 실행하는 사용자 계정에 Configuration Manager 계층 구조의 전체 관리자와 동일한 직접 역할 기반 관리 권한이 있어야 합니다. 계정에 전체 관리자 권한이 있는 Windows 보안 그룹의 구성원으로 이러한 권한이 부여된 경우에는 도구가 작동하지 않습니다.

## <a name="modes-of-operation"></a>작동 모드
도구는 다음 두 가지 모드에서 실행할 수 있습니다. *삭제 모드*에서 도구를 실행하기 전에 결과를 검토할 수 있도록 *What-If* 모드에서 도구를 실행하는 것이 좋습니다.
  1.    **What-If 모드**:   
      **/delete** 스위치를 지정하지 않으면 도구는 What-If 모드에서 실행되고 배포 지점에서 삭제될 콘텐츠를 식별합니다.
   - 이 모드에서 실행되는 도구는 데이터를 삭제하지 않습니다.
   - 삭제될 콘텐츠에 대한 정보는 도구 로그 파일에 기록되고 각각의 삭제 가능성을 확인하는 메시지는 표시되지 않습니다.  
      </br>   

  2. **삭제 모드**:   
    **/delete** 스위치와 함께 도구를 실행하면 도구가 삭제 모드에서 실행됩니다.

     - 이 모드에서 실행될 경우 지정된 배포 지점에 있는 분리된 콘텐츠가 배포 지점의 콘텐츠 라이브러리에서 삭제될 수 있습니다.
     -  각 파일을 삭제하기 전에 파일이 삭제되어야 하는지 확인해야 합니다.  **Y**(예) 또는 **N**(아니요)을 선택하거나, 추가 메시지를 건너뛰고 분리된 콘텐츠를 모두 삭제하려면 **모두 예**를 선택할 수 있습니다.  
     </br>

도구가 어느 모드에서 실행되든 도구가 실행되는 모드를 포함하는 이름, 배포 지점 이름 및 작업 날짜/시간이 포함된 로그가 자동으로 생성됩니다. 도구가 완료되면 로그 파일이 자동으로 열립니다.

기본적으로 로그 파일은 도구가 실행되는 컴퓨터에 있는, 도구를 실행하는 사용자 계정의 임시 폴더에 기록됩니다. **/log** 스위치를 사용하여 네트워크 공유를 비롯한 다른 위치로 로그 파일을 리디렉션할 수 있습니다.


## <a name="run-the-tool"></a>도구 실행
도구를 실행하려면:
1. 관리 명령 프롬프트를 **ContentLibraryCleanup.exe**가 포함된 폴더로 엽니다.  
2. 필수 명령줄 스위치와 사용할 선택적 스위치를 포함하는 명령줄을 입력합니다.

**알려진 문제** 도구가 실행되면 패키지 또는 배포가 실패했거나 진행 중인 경우 다음과 같은 오류가 반환될 수 있습니다.
-  *System.InvalidOperationException: <packageID> 패키지가 완전히 설치되지 않으므로 이 콘텐츠 라이브러리가 바로 정리될 수 없습니다.*

**해결 방법:** 없음 콘텐츠가 진행 중이거나 배포에 실패한 경우 도구는 분리된 파일을 안정적으로 식별할 수 없습니다. 따라서 해당 문제가 해결될 때까지 도구를 통해 콘텐츠를 정리할 수 없습니다.

### <a name="command-line-switches"></a>명령줄 스위치  
다음 명령줄 스위치를 순서에 관계없이 사용할 수 있습니다.   

|스위치|세부 정보|
|---------|-------|
|**/delete**  |**선택 사항** </br> 배포 지점에서 콘텐츠를 삭제하려는 경우 이 스위치를 사용합니다. 콘텐츠를 삭제하기 전에 확인 메시지가 표시됩니다. </br></br> 이 스위치를 사용하지 않으면 도구는 삭제되는 콘텐츠에 대한 결과를 기록하지만 배포 지점에서 콘텐츠를 삭제하지는 않습니다. </br></br> 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /delete*** |
| **/q**       |**선택 사항** </br> 이 스위치는 모든 메시지(예: 콘텐츠 삭제 프롬프트)를 표시하지 않는 자동 모드로 도구를 실행하고 자동으로 로그 파일을 열지 않습니다. </br></br> 예: ***ContentLibraryCleanup.exe /q /dp server1.contoso.com*** |
| **/dp &lt;배포 지점 FQDN>**  | **필수** </br> 정리하려는 배포 지점의 FQDN(정규화된 도메인 이름)을 지정합니다. </br></br> 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com***|
| **/ps &lt;기본 사이트 FQDN>**       | 기본 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **선택 사항**입니다.</br>보조 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **필수**입니다. </br></br>이 도구는 부모 기본 사이트에 연결하여 SMS_Provider에 대 한 쿼리를 실행합니다. 이러한 쿼리를 통해 도구에서는 배포 지점에 있어야 할 콘텐츠를 확인하여 분리되어 있고 제거할 수 있는 콘텐츠를 식별할 수 있습니다. 보조 사이트에서 바로 필요한 세부 정보를 이용할 수 없기 때문에 부모 기본 사이트에 대한 이러한 연결은 보조 사이트에서 배포 지점에 대해 이루어져야 합니다.</br></br> 배포 지점이 속하는 기본 사이트 또는 배포 지점이 보조 사이트에 있는 경우 부모 기본 사이트의 FQDN을 지정합니다. </br></br> 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;기본 사이트 코드>**  | 기본 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **선택 사항**입니다.</br>보조 사이트의 배포 지점에서 콘텐츠를 정리하는 경우 **필수**입니다. </br></br> 배포 지점이 속하는 기본 사이트 또는 배포 지점이 보조 사이트에 있는 경우 부모 기본 사이트의 사이트 코드를 지정합니다.</br></br> 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/log <log file directory>**       |**선택 사항** </br> 도구가 로그 파일을 기록하는 위치를 지정합니다. 로컬 드라이브 또는 네트워크 공유일 수 있습니다.</br></br> 이 스위치를 사용하지 않으면 로그 파일은 도구가 실행되는 컴퓨터에 있는 사용자의 임시 폴더에 저장됩니다.</br></br> 로컬 드라이브의 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /log C:\Users\Administrator\Desktop*** </br></br>네트워크 공유의 예: ***ContentLibraryCleanup.exe /dp server1.contoso.com /log \\&lt;공유>\&lt;폴더>***|
