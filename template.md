---
title: "문서 제목 | Microsoft Docs"
description: 
keywords: 
author: GITHUB USERNAME
manager: ALIAS
ms.date: 10/06/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: GET ONE FROM guidgenerator.com
ms.openlocfilehash: a218011ded1ff3acc1dbd24471119b701f2cce23
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="metadata-and-markdown-template"></a>메타데이터 및 Markdown 템플릿

이 docs.ms 템플릿은 Markdown 구문의 예제뿐만 아니라 메타데이터를 설정하는 지침을 포함합니다. 각 EM 파일럿 리포지토리의 루트 디렉터리(예: ~/Azure-RMSDocs-pr /template.md)에서 사용할 수 있고 Markdown 파일로 읽어야 하지만 Markdown 예제를 렌더링하는 방법은 [게시된 버전](https://stage.docs.microsoft.com/en-us/rights-management/template)을 참조할 수 있습니다.

Markdown 파일을 만들 때 새 파일에 템플릿을 복사하고, 아래에 지정된 대로 메타데이터를 입력하고, 위의 H1 제목을 문서의 제목으로 설정하고, 내용을 삭제합니다.


## <a name="metadata"></a>Metadata

전체 메타데이터 블록은 위와 같이 필수 필드 및 선택적 필드로 분할됩니다. 자세한 내용은 [OPS 메타데이터 참조 문서](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data)를 참조하세요. 몇 가지 주요 참고 사항:

- 콜론(:)과 메타데이터 요소 값 사이에 공백이 **있어야** 합니다.
- 선택적 메타데이터 요소에 값이 없는 경우 #로 해당 요소를 주석 처리합니다(비워 두거나 "na"를 사용하지 않음). 주석 처리된 요소에 값을 추가하는 경우 #를 제거해야 합니다.
- 값(예: 제목)에 콜론이 있으면 메타데이터 파서가 중단됩니다. 그 자리에 &#58;이라는 HTML 인코딩을 사용합니다(예: "제목: Azure Rights Management&#58;기본 사항 | Azure RMS").
- **제목**: 이 제목은 검색 엔진 결과에 표시됩니다. 제목은 파이프(|) 뒤에 서비스의 이름으로 끝나야 합니다(예: 위 참조). 제목은 H1 제목의 제목과 일치하지 않아도 됩니다(또한 일치하지 않아야 함). 대략 65자여야 합니다(| 서비스 이름 포함)
- **작성자**, **관리자**, **검토자**: 작성자 필드는 별칭이 아니라 작성자의 **Github 사용자 이름**를 포함해야 합니다.  반면에 "관리자" 및 "검토자" 필드는 별칭을 포함해야 합니다. ms.reviewer는 문서 또는 서비스와 관련된 PM의 이름을 지정합니다.
- **ms.assetid**: CAPS에서 문서의 GUID입니다. 새 Markdown 파일을 만들 때 [https://www.guidgenerator.com](https://www.guidgenerator.com)에서 GUID를 가져옵니다.
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: [여기](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default)에서 이러한 요소에 가능한 값을 찾을 수 있습니다.

## <a name="basic-markdown-and-gfm"></a>기본 Markdown 및 GFM

모든 기본 사항 및 Github 지원 Markdown이 지원됩니다. 이러한 항목에 대한 자세한 내용은 다음을 참조하세요.

- [기준 Markdown 구문](https://daringfireball.net/projects/markdown/syntax)
- [GFM(Github 지원 Markdown) 설명서](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>제목

첫 번째 및 두 번째 수준 제목의 예제는 위와 같습니다.

항목에는 페이지 제목으로 표시되는 하나의 첫 번째 수준 제목만 **있어야** 합니다.  

두 번째 수준 제목은 페이지 제목 아래에서 "이 문서에서" 섹션에 표시되는 페이지 TOC를 생성합니다.

### <a name="third-level-heading"></a>세 번째 수준 제목
#### <a name="fourth-level-heading"></a>네 번째 수준 제목
##### <a name="fifth-level-heading"></a>다섯 번째 수준 제목
###### <a name="sixth-level-heading"></a>여섯 번째 수준 제목

## <a name="text-styling"></a>텍스트 스타일

*기울임꼴*

**굵게**

~~취소선~~



## <a name="links"></a>링크

동일한 리포지토리에 있는 Markdown 파일에 연결하려면 [상대 링크](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2)를 사용합니다.

- 예제: [Azure Rights Management란?](./understand-explore/what-is-azure-rights-management.md)

동일한 Markdown 파일에 있는 헤더를 연결하려면 게시된 문서의 소스를 보고, 헤드의 ID(예: `id="blockquote"`)를 찾고, # + id를 사용하여 연결합니다(예: `#blockquote`).

- 예: [Blockquotes](#blockquote)

동일한 리포지토리에 있는 Markdown 파일의 헤더에 연결하려면 상대 연결 + 해시태그 연결을 사용합니다.

- 예: [등록 프로세스의 기술 개요](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

외부 파일에 연결하려면 전체 URL을 링크로 사용합니다.

- 예: [Github](http://www.github.com)

Markdown 파일에 URL이 표시되는 경우 클릭 가능한 링크로 변환됩니다.

- 예: http://www.github.com

## <a name="lists"></a>목록

### <a name="ordered-lists"></a>정렬된 목록

1. This
1. Is
1. An
1. Ordered
1. 목록  


#### <a name="ordered-list-with-an-embedded-list"></a>포함된 목록으로 정렬된 목록

1. Here
1. comes
1. an
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. 목록


### <a name="unordered-lists"></a>정렬되지 않은 목록

- This
- is
- a
- bulleted
- 목록


##### <a name="unordered-list-with-an-embedded-lists"></a>포함된 목록으로 정렬되지 않은 목록

- This
- bulleted
- 목록
    - Mrs. Peacock
    - Mr. Green
- 포함  
- other
    1. Colonel Mustard
    1. Mrs. White
- lists


## <a name="horizontal-rule"></a>단락 구분선

---

## <a name="tables"></a>Tables

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| col 1 is default | left-aligned     |    $1 |


## <a name="code"></a>코드

### <a name="codeblock"></a>Codeblock

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>인라인 코드

`in-line code`의 예제입니다.

## <a name="blockquotes"></a>Blockquotes

> 가뭄이 천만 년 동안 지속되고 공룡의 지배는 오래 전에 끝났습니다. 예전에 아프리카라고 알려졌던 대륙의 에콰도르에서 생존을 위한 전쟁은 잔인함이 극에 달하고 승자가 누구인지 아직 알 수 없었습니다. 이 척박하고 메마른 땅에서는 오직 작고 빠른 사나운 동물만이 번창하고 살아남을 수 있었습니다.

## <a name="images"></a>이미지

### <a name="static-image"></a>고정 이미지

![대체 텍스트임](./media/AzRMS_elements.png)

### <a name="linked-image"></a>연결된 이미지

[![연결된 이미지에 대한 대체 텍스트](./media/AzRMS_elements.png)](https://azure.microsoft.com)

### <a name="animated-gif"></a>애니메이션된 gif

![애니메이션된 gif](./media/hololens.gif)

## <a name="alerts"></a>경고

### <a name="note"></a>참고

> [!NOTE]
> 이것은 참고입니다.

### <a name="warning"></a>경고

> [!WARNING]
> 이것은 경고입니다.

### <a name="tip"></a>팁

> [!TIP]
> 이것은 팁입니다.

### <a name="important"></a>중요

> [!IMPORTANT]
> 이것은 중요합니다.

## <a name="videos"></a>비디오

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>Youtube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms 확장

### <a name="button"></a>단추

> [!div class="button"]
[단추 링크](/rights-management)

### <a name="selector"></a>선택기

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [bar](/rights-management/scratch.md)

### <a name="step-by-step"></a>단계별

>[!div class="step-by-step"]
[이전](https://www.example.com)
[다음](https://www.example.com)
