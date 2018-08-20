---
title: 콘텐츠 소유권 도구
titleSuffix: Configuration Manager
description: 콘텐츠 소유권 도구를 사용하여 Configuration Manager에서 분리된 패키지의 소유권을 변경합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 753d2681-ea72-4f47-94d1-ac10188d9d5b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 962b19f1849628776eb1b9059089f7ce8e6df3ee
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385984"
---
# <a name="content-ownership-tool"></a>콘텐츠 소유권 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

콘텐츠 소유권 도구는 [Configuration Manager 도구](/sccm/core/support/tools)에 속합니다. Configuration Manager에서 분리된 패키지의 소유권을 변경합니다. 분리된 패키지에는 소유하는 사이트 서버가 없습니다. 이 사이트 서버가 계속 소유하는 상태에서 사이트 서버를 제거하면 패키지가 분리될 수 있습니다.

Configuration Manager 계층 구조의 모든 사이트 서버에 대해 콘텐츠 소유권 도구를 실행합니다. 패키지 권한이 충분한 관리자 사용자로 로그인합니다.  

> [!Tip]  
> `CD.Latest\SMSSETUP\TOOLS\ContentLibraryCleanup`에서 **ContentLibraryCleanup.exe**를 사용하여 배포 지점에서 분리된 콘텐츠를 *제거*합니다. 자세한 내용은 [콘텐츠 라이브러리 정리 도구](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool)를 참조하세요.  



## <a name="features"></a>기능

- 모든 분리된 패키지 표시  

- 분리되지 않은 패키지도 모두 표시  

- 사이트 연결 상태 보기  

- 이름, 사이트 코드 또는 패키지 형식으로 패키지 필터링  

- 표시 열 기준 정렬  

- 단일 작업에서 하나 이상의 패키지 할당 변경  

- 소유권 이전 작업 진행률 보기  



## <a name="usage"></a>용도

**ContentOwnershipTool.exe**를 실행하여 도구를 시작합니다. 도구 실행에는 컴퓨터에 대한 로컬 관리자 권한이 필요하지 않습니다.

명령줄 매개 변수는 없습니다.

> [!Important]   
> 이 도구는 분리된 패키지의 소유권을 변경합니다. 패키지 자체는 저장된 배포 지점에서 이동하지 않습니다. 이 소유권 변경은 배포 지점의 패키지 업데이트를 초래하지 않습니다. 또한 클라이언트의 패키지 배포 정책 재평가가 실행되지도 않습니다. 소유권 변경 후에는 새 사이트 서버가 원본 파일에 액세스할 수 있는지 확인합니다. 각 패키지의 원본 파일에 대해 최소한 **읽기** 권한이 있어야 합니다. 



## <a name="see-also"></a>참고 항목

- [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)
- [콘텐츠 라이브러리](/sccm/core/plan-design/hierarchy/the-content-library)
