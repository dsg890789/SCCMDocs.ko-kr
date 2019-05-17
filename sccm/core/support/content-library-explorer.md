---
title: 콘텐츠 라이브러리 탐색기
titleSuffix: Configuration Manager
description: 콘텐츠 라이브러리 탐색기를 사용하여 Configuration Manager 배포 지점에서 콘텐츠 라이브러리를 보고 문제를 해결합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 691896d9-ec0f-461f-a3f2-40378ebd3121
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 1fbd046115dcd4d13cec7a2bf880740a9dd616cc
ms.sourcegitcommit: 80cbc122937e1add82310b956f7b24296b9c8081
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65495773"
---
# <a name="content-library-explorer"></a>콘텐츠 라이브러리 탐색기

*적용 대상: System Center Configuration Manager(현재 분기)*

콘텐츠 라이브러리 탐색기는 [Configuration Manager 도구](/sccm/core/support/tools)에 속합니다. 다음과 같은 작업에 도구를 사용합니다.  

- 특정 배포 지점에서 콘텐츠 라이브러리 탐색  

- 콘텐츠 라이브러리를 사용하여 문제 해결  

- 콘텐츠 라이브러리에서 패키지, 콘텐츠, 폴더 및 파일 복사  

- 배포 지점에 패키지 재배포  

- 원격 배포 지점에서 패키지의 유효성 검사  



## <a name="requirements"></a>요구 사항

- 다음에 대한 관리 권한이 있는 계정을 사용하여 도구를 실행합니다.  

    - 대상 배포 지점  

    - 사이트 서버의 WMI 공급자  

    - Configuration Manager 공급자  

- **전체 관리자** 및 **읽기 전용 분석가** 역할만 이 도구의 모든 정보를 볼 충분한 권한을 갖습니다.  

    - **애플리케이션 관리자**와 같은 다른 역할은 부분 정보를 볼 수 있습니다. 자세한 내용은 [비활성화된 패키지](#bkmk_disabled-packages)를 참조하세요.  

    - **읽기 전용 분석가**는 이 도구에서 패키지를 재배포할 수 없습니다.  

- 연결할 수 있으면 모든 컴퓨터에서 도구를 실행합니다.  

    - 대상 배포 지점  

    - 기본 사이트 서버  

    - Configuration Manager 공급자  

- 배포 지점이 사이트 서버와 공동 배치된 경우 여전히 사이트 서버에 대한 관리 액세스 권한이 필요합니다.  



## <a name="usage"></a>용도 

**ContentLibraryExplorer.exe**를 시작할 때 대상 배포 지점의 FQDN(정규화된 도메인 이름)을 입력합니다. 그런 다음, 배포 지점에 연결합니다. 배포 지점이 보조 사이트의 일부인 경우 기본 사이트 서버의 FQDN 및 기본 사이트 코드를 묻는 메시지를 표시합니다.

왼쪽 창에서 이 배포 지점에 배포되는 패키지를 봅니다. 패키지를 확장하고, 해당 폴더 구조를 탐색합니다. 이 구조는 패키지를 만든 폴더 구조와 일치합니다.

폴더를 선택하면 폴더 내의 모든 파일을 오른쪽 창에 표시합니다. 이 뷰에는 다음 정보가 포함되어 있습니다. 
- 파일 이름
- 파일 크기
- 해당 드라이브
- 드라이브에서 동일한 파일을 사용하는 다른 패키지
- 배포 지점에서 파일이 마지막으로 변경된 시간

도구는 또한 Configuration Manager 공급자에 연결합니다. 이 연결은 배포 지점에 배포되는 패키지 및 배포 지점의 콘텐츠 라이브러리에 실제로 있는지 여부를 결정하는 것입니다. 예를 들어 배포를 보류 중인 패키지는 콘텐츠 라이브러리에 아직 존재하지 않습니다. 이러한 패키지는 도구에서 "보류 중"으로 표시되고 이 패키지에 대해 활성화된 작업이 없습니다.


### <a name="bkmk_disabled-packages"></a> 비활성화된 패키지

일부 패키지는 배포 지점에 있지만 Configuration Manager 콘솔에 표시되지 않습니다. 이러한 패키지는 별표(\*)로 표시됩니다. 이러한 패키지에서 작업을 수행할 수 없습니다. 다른 패키지는 별표로 표시될 수도 있으며 비활성화된 작업을 갖습니다. 

비활성화된 패키지에 대한 세 가지 주요 이유가 있습니다.  

- 패키지는 Configuration Manager 클라이언트 업그레이드입니다. 이 패키지는 "ccmsetup.exe"를 포함합니다.  

- 사용자 계정은 역할 기반 관리로 인해 패키지에 액세스할 수 없습니다. 예를 들어 **애플리케이션 작성자** 역할은 콘솔에서 드라이버 패키지를 볼 수 없으므로 배포 지점의 모든 드라이버 패키지는 비활성화로 표시됩니다.  

- 패키지는 배포 지점에서 분리됩니다.  


### <a name="validate-packages"></a>패키지 유효성 검사

도구 모음에서 **패키지** > **유효성 검사**를 사용하여 패키지의 유효성을 검사합니다. 먼저 왼쪽 창에서 패키지 노드를 선택합니다. 콘텐츠 또는 폴더를 선택하지 마십시오. 도구는 이 작업에 대한 배포 지점의 WMI 공급자에 연결합니다. 도구가 시작되면 하나 이상의 콘텐츠가 누락된 패키지가 유효하지 않은 것으로 표시됩니다. 패키지 유효성 검사는 누락된 콘텐츠를 표시합니다. 모든 콘텐츠가 있지만 데이터가 손상된 경우 유효성 검사는 손상을 감지합니다.


### <a name="redistribute-packages"></a>패키지 재배포

도구 모음에서 **패키지** > **재배포**를 사용하여 패키지를 재배포합니다. 먼저 왼쪽 창에서 패키지 노드를 선택합니다. 이 작업에는 패키지를 재배포하는 권한이 필요합니다.


### <a name="other-actions"></a>다른 작업

**편집** > **복사**를 사용하여 콘텐츠 라이브러리에서 패키지, 콘텐츠, 폴더 및 파일을 지정된 폴더에 복사합니다. 콘텐츠 라이브러리 자체를 복사할 수 없습니다. 둘 이상의 파일을 선택하지만 여러 폴더를 선택할 수 없습니다.

**편집** > **패키지 찾기**를 사용하여 패키지를 검색합니다. 이 작업은 패키지 이름 및 패키지 ID에서 쿼리를 검색합니다.



## <a name="limitations"></a>제한 사항

- 도구는 어떤 방식으로든 직접 콘텐츠 라이브러리를 조작할 수 없습니다. 콘텐츠 라이브러리를 변경하면 오작동이 발생할 수 있습니다.  

- 도구는 패키지를 재배포할 수 있지만 대상 배포 지점에만 재배포할 수 있습니다.  

- 사이트 서버와 배포 지점을 공동 배치하는 경우 패키지 데이터의 유효성을 검사할 수 없습니다. 대신 Configuration Manager 콘솔을 사용합니다. 도구는 모든 콘텐츠가 있는지 확인하도록 패키지를 검사하지만 반드시 그대로 유지될 필요는 없습니다.  

- 이 도구를 사용하여 콘텐츠를 삭제할 수 없습니다.



## <a name="see-also"></a>참고 항목

- [콘텐츠 관리의 기본 개념](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management)
- [콘텐츠 라이브러리](/sccm/core/plan-design/hierarchy/the-content-library)
