---
title: 문서 사용 방법
titleSuffix: Configuration Manager
description: Configuration Manager 기술 문서 라이브러리를 사용하는 방법에 대한 팁을 알아봅니다.
ms.date: 04/30/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: conceptual
ms.assetid: b3d755bd-0870-4f1f-a56d-bfd3c7b492b9
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 46bff7e26a5df326b686b07c37f1d58352755857
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-use-the-configuration-manager-docs"></a>Configuration Manager 문서를 사용하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에서는 다음 섹션에 Configuration Manager 문서 라이브러리를 사용하기 위한 여러 팁 및 리소스를 제공합니다.  

- [검색 방법](#bkmk_searchtips)  

- [문서 버그, 고급 기능, 질문 및 새로운 아이디어 제출](#bkmk_docfeedback)  

- [변경에 대한 알림 받는 방법](#bkmk_notifications)  

- [문서에 기여하는 방법](#bkmk_contribute)  


제품에 대한 일반적인 도움말은 [도움말 찾기](/sccm/core/understand/find-help)를 참조합니다.


##  <a name="bkmk_searchtips"></a>검색   
 필요한 정보를 찾으려면 다음 검색 팁을 사용하세요.  

-   Configuration Manager에 대한 콘텐츠를 찾기 위해 기본 설정 검색 엔진을 사용할 경우 검색 키워드와 함께 `SCCM`을 포함합니다.  

    - Configuration Manager 현재 분기에 대한 docs.microsoft.com에서 결과를 찾습니다. technet.microsoft.com의 또는 msdn.microsoft.com의 결과는 이전 제품 버전용입니다.  

    - 검색 결과를 현재 콘텐츠 라이브러리에 추가 포커스를 설정하려면 검색 엔진 범위를 지정하는 `site:docs.microsoft.com`을 포함합니다.  

-   사용자 인터페이스 및 온라인 설명서에 있는 용어와 일치하는 검색 용어를 사용합니다. 커뮤니티 콘텐츠에 표시될 수 있는 약어나 비공식 용어를 사용하지 않습니다. 예를 들어 "MP"보다는 "관리 지점"으로, "DT"보다는 "배포 유형"으로, "SUM"보다는 "소프트웨어 업데이트"로 검색하세요.  

-   현재 보고있는 문서 내에서 검색하려면 브라우저의 **찾기** 기능을 사용합니다. 대부분의 현대 웹 브라우저를 사용하여 **Ctrl**+**F** 키를 누른 다음, 검색어를 입력합니다.  

-   docs.microsoft.com의 각 문서에는 콘텐츠 검색을 지원하는 다음 필드가 포함됩니다.  

    - 오른쪽 위 모서리에 있는 **검색** 모든 문서를 검색하려면 이 필드에 용어를 입력합니다. Configuration Manager 라이브러리의 문서에는 "ConfigMgr" 범위가 자동으로 포함됩니다.  

    - 콘텐츠의 왼쪽 테이블 위에 있는 **제목별 필터**입니다. 콘텐츠의 현재 테이블을 검색하려면 이 필드에 용어를 입력합니다. 이 필드는 현재 노드에 대한 문서 제목에 나타나는 용어와 일치합니다. 예를 들어 핵심 인프라 또는 응용 프로그램 관리입니다.  

- 특정 항목을 찾는 데 문제가 있습니까? [파일 피드백!](#bkmk_docfeedback) 이 문제를 신고하는 경우 사용하는 검색 엔진, 시도한 키워드 및 대상 문서를 제공합니다. 이 피드백은 Microsoft가 더 나은 검색을 위해 콘텐츠를 최적화하는 데 도움이 됩니다.  



## <a name="bkmk_docfeedback"></a>피드백

모든 문서의 오른쪽 위에 있는 **피드백** 링크를 클릭하여 맨 아래의 피드백 섹션으로 이동합니다. 이 섹션은 GitHub 문제와 통합됩니다. GitHub 문제와 통합에 대한 자세한 내용은 [문서 플랫폼 블로그 게시물](https://docs.microsoft.com/teamblog/a-new-feedback-system-is-coming-to-docs)을 참조합니다.

Configuration Manager 제품 자체에 대한 피드백을 공유하려면 **제품 피드백 제공**을 클릭합니다. 자세한 내용은 [제품 피드백](/sccm/core/understand/find-help#product-feedback)을 참조하세요. 

[GitHub 계정](https://github.com/join)은 설명서 피드백을 제공하는 데 필수 조건입니다. 로그인하면 MicrosoftDocs에 대한 일회성 인증 방법이 있습니다. **설명서 피드백 제공**을 클릭해서 제목 및 설명을 입력한 다음, **피드백을 제출**합니다. 이 작업은 [SCCMdocs 리포지토리](https://github.com/MicrosoftDocs/SCCMdocs/issues)에서 대상 문서에 대한 새로운 문제를 제기합니다.

또한 이 통합에는 대상 문서에 대한 기존 개방형 또는 폐쇄형 문제가 모두 표시됩니다. 있는 경우 새 문제를 제출하기 전에 검토합니다. 관련 문제를 발견할 경우 얼굴 아이콘을 클릭하여 대응을 추가하거나 확장하여 주석을 추가할 수 있습니다. 

#### <a name="types-of-feedback"></a>피드백 유형
GitHub 문제를 사용하여 다음 유형의 피드백을 제출합니다.
- 문서 버그: 콘텐츠가 만료되고 불명확하고 혼동을 주거나 끊어집니다.
- 문서 향상: 문서를 개선하기 위한 제안입니다.
- 문서 질문: 기존 문서를 찾는 데 도움이 필요합니다.
- 문서 아이디어: 새 문서에 대한 제안입니다. 설명서 피드백을 위해 UserVoice 대신 이 메서드를 사용합니다.
- Kudos: 유용한 정보 문서에 대한 긍정적인 피드백!
- 지역화: 콘텐츠 변환에 대한 피드백입니다.
- SEO(검색 엔진 최적화): 콘텐츠 검색 문제에 대한 피드백입니다. 주석에 검색 엔진, 키워드 및 대상 문서를 포함합니다.

[제품 피드백](/sccm/core/understand/find-help#product-feedback), [제품 질문](https://social.technet.microsoft.com/Forums/en-US/home?category=ConfigMgrCB), 또는 [지원 요청](https://aka.ms/cmcbsupport)과 같은 비문서 관련 항목에 대해 문제가 발생한 경우 이러한 문제는 종결되고 사용자는 적절한 피드백 채널로 리디렉션됩니다.

docs.microsoft.com 플랫폼에 대한 피드백을 공유하려면 [문서 피드백](https://aka.ms/sitefeedback)을 참조합니다. 플랫폼에는 헤더, 목차 및 메뉴 등 래퍼 구성 요소 모두가 포함됩니다. 또한 글꼴, 경고 상자 및 페이지 책갈피 같이 문서를 브라우저에서 렌더링하는 방법입니다.



## <a name="bkmk_notifications"></a> 알림

문서 라이브러리에서 콘텐츠가 변경될 때 알림을 받으려면 다음 단계를 사용합니다.

1. 문서 또는 문서 집합을 찾으려면 [문서 검색](https://docs.microsoft.com/search/index?scope=ConfigMgr)을 사용합니다. 예:
    - ["문제 해결을 위한 로그 파일 - Configuration Manager"](https://docs.microsoft.com/search/index?search=%22Log+files+for+troubleshooting+-+Configuration+Manager%22&scope=ConfigMgr)라는 제목으로 단일 문서를 검색합니다.
    - [SQL](https://docs.microsoft.com/search/index?search=SQL&scope=ConfigMgr)에 관한 모든 문서 검색
2. 오른쪽 위 모서리에서 **RSS** 링크를 클릭합니다. 
3. 검색 결과에 변경이 있는 경우 알림을 받으려면 모든 RSS 응용 프로그램에서 이 피드를 사용합니다.


> [!Tip]  
> GitHub에서 [SCCMdocs 리포지토리](https://github.com/MicrosoftDocs/SCCMdocs)를 **감시**할 수도 있습니다. 이 메서드는 많은 알림을 생성합니다. 또한 Microsoft에서 사용하는 개인 리포지토리의 변경은 포함하지 않습니다.  



## <a name="bkmk_contribute"></a> 기여

docs.microsoft.com의 대부분 콘텐츠와 마찬가지로 Configuration Manager 문서 라이브러리는 GitHub의 오픈 소스입니다. 이 라이브러리는 커뮤니티 기여를 수용하고 권장합니다. 시작 방법에 대한 자세한 내용은 [기여자 가이드](https://docs.microsoft.com/contribute)를 참조합니다. [GitHub 계정](https://github.com/join) 만들기는 유일한 필수 조건입니다.

#### <a name="basic-steps-to-contribute-to-sccmdocs"></a>SCCMdocs에 기여하는 기본 단계
1. 대상 문서에서 **편집**을 클릭합니다. 이 작업은 GitHub에서 원본 파일을 엽니다.
2. 원본 파일을 편집하려면 연필 아이콘을 클릭합니다.
3. Markdown 원본에서 변경합니다. 자세한 내용은 [문서 작성을 위한 Markdown 사용 방법](https://docs.microsoft.com/contribute/how-to-write-use-markdown)을 참조하세요. 
4. 파일 변경 제안 섹션에서 변경한 *내용*을 설명하는 공용 커밋 주석을 입력합니다. 그럼 다음, **파일 변경 제안**을 클릭합니다.
5. 아래로 스크롤하여 변경 내용을 확인합니다. **끌어오기 요청 만들기**를 클릭하여 양식을 엽니다. 이런 변경을 한 *이유*를 설명합니다. 검토할 문서 작성자 및 요청을 태그합니다. **끌어오기 요청 만들기**를 클릭합니다.

### <a name="what-to-contribute"></a>기여한 내용
기여에 관심이 있지만 어디서 시작해야 할지 모르는 경우 다음 제안을 참조합니다.
- 문서의 정확도를 검토합니다. 그런 다음, `mm/dd/yyyy` 형식을 사용하여 **ms.date** 메타데이터를 업데이트합니다. 이 기여는 콘텐츠를 최신 상태로 유지하는 데 도움이 됩니다.
- 설명, 예제 또는 사용자 경험 기반 지침을 추가합니다. 이 기여는 지식을 공유하는 커뮤니티의 능력을 사용합니다.  
- 비영어권 언어로 된 올바른 번역입니다. 이 기여는 지역화된 콘텐츠의 유용성을 향상시킵니다.
- [good-first-issue](https://github.com/MicrosoftDocs/sccmdocs/issues?q=is:open+is:issue+label:good-first-issue) 및 [help-wanted](https://github.com/MicrosoftDocs/sccmdocs/issues?q=is:open+is:issue+label:help-wanted) 같은 커뮤니티 대상 레이블에 대한 문제 목록을 검색합니다. Microsoft 작성자가 커뮤니티 기여를 위해 적합한 후보인 문제에 이러한 레이블을 할당합니다.