---
title: 콘텐츠 라이브러리 전송 도구
titleSuffix: Configuration Manager
description: 콘텐츠 라이브러리 전송 도구를 사용하여 Configuration Manager 배포 지점에서 하나의 디스크 드라이브에서 다른 디스크 드라이브로 콘텐츠를 전송합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7d07bd0a-7012-47f7-8bc5-509a402915b7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6f7375a62349aba30ee239aa34fa594650f5a844
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56121984"
---
# <a name="content-library-transfer-tool"></a>콘텐츠 라이브러리 전송 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

콘텐츠 라이브러리 전송 도구는 [Configuration Manager 도구](/sccm/core/support/tools)에 속합니다. 이 도구는 한 디스크 드라이브에서 다른 디스크 드라이브로 콘텐츠를 전송합니다. 이 도구는 배포 지점 사이트 시스템에서 실행되도록 설계되었습니다. 또한 사이트 또는 원격 사이트 시스템과 함께 배치된 배포 지점을 지원합니다.  

이 도구는 콘텐츠 라이브러리를 호스팅하는 디스크 드라이브가 꽉 찬 경우 시나리오에 유용합니다. 먼저 콘텐츠 라이브러리를 호스트할 충분한 공간이 있는 다른 하드 디스크를 추가하거나 식별합니다. 그런 다음, **ContentLibraryTransfer.exe**를 사용하여 기존의 꽉 찬 하드 디스크에서 새로운 빈 드라이브로 콘텐츠를 전송합니다.
 
콘텐츠가 전송이 완료되면 새 위치에서 클라이언트 컴퓨터에 액세스할 수 있습니다.



## <a name="usage"></a>용도 

배포 지점에 대한 관리 권한이 있는 사용자로 **ContentLibraryTransfer.exe**를 실행합니다. 

#### <a name="syntax"></a>구문 
`ContentLibraryTransfer.exe –SourceDrive <drive letter of source drive> –TargetDrive <drive letter of destination drive>`

#### <a name="example"></a>예
`ContentLibraryTransfer –SourceDrive E –TargetDrive G`



## <a name="limitations"></a>제한 사항

- 배포 지점에서 로컬로 도구를 실행합니다. 그러나 원격 컴퓨터에서는 실행할 수 없습니다.  

- 클라이언트가 배포 지점에 적극 액세스할 수 없는 경우에만 도구를 사용합니다. 클라이언트가 콘텐츠에 액세스하는 동안 도구를 실행하는 경우 대상 드라이브의 콘텐츠 라이브러리에는 불완전한 데이터가 있을 수 있습니다. 데이터 전송은 사용할 수 없는 콘텐츠 라이브러리로 연결이 완전히 실패할 수 있습니다.  

- 도구를 실행할 경우 배포 지점에 콘텐츠를 배포하지 마세요. 배포 지점에 콘텐츠를 작성하는 동안 도구를 실행하는 경우 대상 드라이브의 콘텐츠 라이브러리에는 불완전한 데이터가 있을 수 있습니다. 데이터 전송은 사용할 수 없는 콘텐츠 라이브러리로 연결이 완전히 실패할 수 있습니다.



## <a name="see-also"></a>참고 항목

- [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)
- [콘텐츠 라이브러리](/sccm/core/plan-design/hierarchy/the-content-library)
