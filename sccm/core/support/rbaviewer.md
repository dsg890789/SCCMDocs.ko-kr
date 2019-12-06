---
title: 역할 기반 관리 도구
titleSuffix: Configuration Manager
description: 역할 기반 관리 및 감사 도구를 사용하여 Configuration Manager에서 보안 역할 및 범위를 모델링하고 감사합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6372ff17-7f56-4d7b-a21b-87fb8bdd6d3a
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 533d055db3a68360c3c18d0e30e0718bf42c2a7c
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "65500796"
---
# <a name="role-based-administration-and-auditing-tool"></a>역할 기반 관리 및 감사 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

역할 기반 관리 및 감사 도구는 [Configuration Manager 도구](/sccm/core/support/tools)에 속합니다. 다음 작업에 이 도구를 사용합니다.

- 특정 권한을 가진 보안 역할 모델링  

- 다른 사용자의 보안 역할과 보안 범위 감사



## <a name="requirements"></a>요구 사항

- Configuration Manager 콘솔로 동일한 컴퓨터에서 실행  

- **전체 관리자**, **읽기 전용 분석가** 또는 **보안 관리자** 역할이 있음  

- **모든** 보안 범위 및 모든 컬렉션에 사용자 계정 할당  

- (*선택 사항*) 보고서 폴더 보안을 분석하려면 SQL 액세스 권한이 있어야 함  

- (*선택 사항*) 드릴스루 보고서를 분석하려면 보고 지점 역할을 사용하여 사이트 시스템 서버에서 이 도구 실행



## <a name="procedures"></a>절차


### <a name="model-permissions-for-a-new-role"></a>새 역할에 대한 권한 모델링

만들려는 새 역할에 대한 권한을 모델링하려면 다음 절차를 수행합니다. 

1. **RBAViewer.exe**를 실행합니다.  

2. 빈 권한 집합에서 시작하거나 빌드하려는 기본 보안 역할을 선택합니다. 필요한 사용 권한을 선택합니다.  

3. **분석**을 클릭하여 이 사용자 지정 역할이 보게 될 사용자 인터페이스를 확인합니다.  

    > [!Note]  
    > 기존 보안 역할이 요구 사항을 충족하는지 여부를 확인하려면 **유사성** 탭으로 전환합니다.  

4. **내보내기**를 클릭하여 XML 파일로 역할을 저장합니다. 그런 다음, Configuration Manager 콘솔로 이 역할을 가져옵니다. 자세한 내용은 [사용자 지정 보안 역할 만들기](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_CreateSecRole)를 참조하세요.


### <a name="audit-existing-security-scopes"></a>기존 보안 범위 감사

다음 절차를 사용하여 Configuration Manager에서 모든 기존 관리자, 컬렉션 및 보안 범위를 감사합니다.

1. **RBAViewer.exe**를 실행합니다.  

2. 도구 모음에서 **RBA 감사** 단추를 선택합니다.  

    1. 트리 보기에서 컬렉션 제한 관계를 보려면 **컬렉션 요약** 탭으로 전환합니다.  

    2. 보안 역할에 할당된 개체를 보려면 **범위 요약** 탭으로 전환합니다.  


### <a name="audit-a-specific-user"></a>특정 사용자 감사

다음 절차를 사용하여 특정 사용자에 대한 역할 기반 관리 구성을 감사합니다.

1. **RBAViewer.exe**를 실행합니다.  

2. 도구 모음에서 **실행** 단추를 선택합니다.  

3. 해당 계정에 대한 사용 권한을 확인하려면 특정 사용자 이름을 입력합니다.  

4. 이 도구는 사용자가 속한 보안 그룹 또는 사용자에게 할당된 보안 역할을 표시합니다. 또한 이 사용자가 확인할 수 있는 개체 및 콘솔에서 사용할 수 있는 작업도 표시합니다.  



## <a name="see-also"></a>참고 항목

- [역할 기반 관리의 기본 사항](/sccm/core/understand/fundamentals-of-role-based-administration)
- [역할 기반 관리 구성](/sccm/core/servers/deploy/configure/configure-role-based-administration)
