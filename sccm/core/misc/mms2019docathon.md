---
title: MMS 2019 Docathon
ms.date: 05/06/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.collection: M365-identity-device-management
ms.assetid: 8fe2ecfc-f5c1-4fa6-8703-245339400723
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX
ms.openlocfilehash: 76970a024e54067aaa6a3059bb95a6c134a2e999
ms.sourcegitcommit: 99dfe4fb9e9cfd20c44380ae442b3a5b895a0d9b
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65214699"
---
# <a name="mms-2019-docathon"></a>MMS 2019 Docathon

MMS(Midwest Management Summit) 2019 기간에 System Center Configuration Manager 및 Microsoft Intune을 위한 Microsoft 콘텐츠 팀은 docathon을 진행합니다. 5월 6일 월요일 [Docs.microsoft.com 실습 랩](https://sched.co/N6fd) 세션에 참석하는 동안 Microsoft 작성자의 지원과 함께 기여 활동에 참여하게 됩니다. Docathon은 회의 내내 진행되고 모든 등록된 MMS 2019 참석자가 참여할 수 있습니다.

참여하신 이유는 무엇인가요? Docs.microsoft.com은 GitHub에서 제공하는 Microsoft 제품 설명서를 위한 오픈 소스 플랫폼입니다. Microsoft는 모든 사용자가 문서에 기여할 것을 권장합니다. 기여 활동에 참여하면 귀하는 이 플랫폼을 통해 모든 문서의 기여자 목록에 포함됩니다. 커뮤니티에서 제공할 수 있는 몇 가지 기여 유형은 다음과 같습니다.

- 오타
- 간단한 설명
- 예
- 실제 지침 및 팁
- 콘텐츠 검토, 새로 고침

## <a name="set-up"></a>설정

기여 활동을 위한 준비가 되지 않았다면 사전에 다음 단계를 수행합니다.

### <a name="github-account"></a>GitHub 계정

[GitHub 계정](https://github.com/join) 만들기

- 프로필에서 가입 확인  

- 2단계 인증 사용  

#### <a name="additional-considerations"></a>추가 고려 사항

- 오픈 소스 기여에 대한 회사 정책 확인  

    > [!Note]  
    > 대규모 기여의 경우 Microsoft 오픈 소스 [CLA(Contributor License Agreement)](https://cla.opensource.microsoft.com/)에 동의해야 합니다. 사전에 이 계약을 검토합니다.  

- Docs.microsoft.com에 대한 기여가 MVP 어워드 심사에 고려됨  

- Microsoft 직원의 경우 몇 가지 추가적인 필수 일회성 단계와 약간 다른 기여 프로세스가 있음  

자세한 내용은 docs.microsoft.com 기여자 가이드에서 [GitHub 계정 설정](https://docs.microsoft.com/contribute/get-started-setup-github)을 참조하세요.

## <a name="scope"></a>범위

이 이벤트는 다음 GitHub 리포지토리에만 해당합니다.

- [IntuneDocs](https://github.com/MicrosoftDocs/IntuneDocs)
- [SCCMDocs](https://github.com/MicrosoftDocs/SCCMdocs)
- [sccm-docs-powershell-ref](https://github.com/MicrosoftDocs/sccm-docs-powershell-ref)

다른 docs.microsoft.com 콘텐츠를 자유롭게 변경할 수 있고 변경이 권장되지만, 해당 변경은 이 이벤트에 대한 크레딧에 반영되지 않습니다.

## <a name="learn-the-process"></a>프로세스 알아보기

[이슈 제출 방법](/sccm/core/understand/use-docs#bkmk_docfeedback) 및 [기여 방법](/sccm/core/understand/use-docs#bkmk_contribute)의 정보를 읽어보세요. 대부분의 기본적인 변경은 GitHub 브라우저 환경을 통해 수행할 수 있습니다.  

> [!Note]  
> Git 및 VSCode를 사용한 더 복잡한 워크플로에 관심이 있다면 [콘텐츠 작성 도구 설치](https://docs.microsoft.com/contribute/get-started-setup-tools)를 참조하세요. 또는 Aaron/Erik에게 도움을 요청하세요. 더 복잡한 워크플로를 사용하는 몇 가지 이유는 다음과 같은 작업 때문입니다.
>
> - 새 문서 만들기
> - 이미지 추가
> - 정규식을 포함한 문자열 검색 및 바꾸기
> - 더 복잡한 대규모 변경  

## <a name="determine-your-goals"></a>목표 확인

먼저 이 이벤트의 목표를 생각해 보고 계획합니다. 무엇을 달성하고 싶으세요?

- 범위 내 리포지토리에서 기본 기존 이슈를 살펴봅니다. **good-first-issue** 또는 **help-wanted**와 같은 레이블이 좋은 시작점을 나타낼 수 있습니다. 이 이슈 중 하나를 해결하려면 **#MMS2019Docathon**을 통해 이 문제에 댓글을 달고 @author 태그를 지정하여 해당 문제를 할당받습니다. 다시 말해, [call dib](https://www.merriam-webster.com/words-at-play/word-origin-dibs)(찜)합니다. 원하는 만큼 이 프로세스를 여러 번 반복합니다.  
    예를 들어 SCCMDocs에서 Aaron은 문서 작성자입니다. `@aczechowski I'm claiming this issue for #MMS2019Docathon`

- 문서 관련 이슈를 알고 있지만 아직 제출된 피드백이 없습니다. 즉, 문서 아래쪽의 **피드백** 섹션에 아무것도 없습니다. 새 이슈를 제출한 후 위의 동일한 지침을 사용하여 이슈 소유권을 주장합니다.  

    - 예를 들어, 코드 샘플, 실제 예제 또는 일반적인 팁을 추가합니다.  

    - 미리 Aaron/Erik과 논의한 경우가 아니면 문법 또는 스타일을 변경하지 마세요.  

    - 원하는 문서의 날짜가 2019년 2월 6일 전으로 90일을 초과하는 날짜입니다. 문서를 검토할 수 있고, 이후에 편집 내용이 **ms.date** 메타데이터 속성에 적용됩니다. 해당 기여의 의미는 다음과 같습니다. “이 문서를 검토했고 기술적으로 정확하므로 날짜를 새로 고칩니다.” 이슈를 제출하여 이슈 소유권을 주장합니다.  

    - 먼저 문서 피드백을 확인하여 이미 이슈 소유권을 주장한 다른 사람의 열린 이슈가 없는지 확인합니다. 엄밀히 말하면 이 작업은 필수는 아닙니다. 이렇게 하지 않고 다른 사용자가 먼저 제출하면 Microsoft는 첫 번째 기여만 받아들입니다.  

- 월요일의 1시간 점심 세션은 이 목표에 전념할 수 있는 시간입니다. Aaron 및 Erik이 질문 또는 문제에 관련된 도움을 줄 수 있습니다.

## <a name="contest-summary"></a>콘테스트 요약

콘테스트는 5월 6일부터 9일까지 일주일 내내 진행됩니다. 모든 등록된 MMS 2019 참석자가 참여할 수 있습니다. 2019년 5월 9일 목요일 오후 3시까지 신청서를 제출하세요. 수상자 혜택은 [ConfigMgr 제품 팀 Q&A 세션](https://sched.co/N6ge) 후인 5월 9일 화요일에 제공됩니다. 수상하려면 MMS 2019에 참여해야 하지만 해당 세션에 참석할 필요는 없습니다. 세션에 참석하지 않은 경우 수상하려면 금요일 아침에 Aaron이 떠나기 전에 Aaron에게 문의하세요.

> [!Important]  
> 크레딧을 얻으려면 모든 기여에 **#MMS2019Docathon** 해시태그를 포함해야 합니다.

### <a name="award-categories"></a>어워드 범주

#### <a name="grand-prize"></a>대상

- **가장 영향력 있음**: 다음 기준에 따라 Aaron 및 Erik이 판단합니다. 제출 내용이 수상 자격이 된다고 생각하면 끌어오기 요청에 댓글을 달아 그 이유를 납득시키세요.

    - 커뮤니티 혜택(50%)
    - Microsoft 스타일 준수(25%)
    - 적절한 markdown(25%)  

대상 수상자는 다음 수상자 혜택을 받습니다.

- MMS 운영 위원회에서 제공하는 $1799 상당의 [MMS Jazz Edition](https://mmsmoa.com/registration/mms-jazz-edition.html) 등록 패스.
- Yeti Rambler 로고가 있는 30oz 텀블러
- Popsocket 로고가 있는 자동차 통풍구 거치대

#### <a name="first-place-prizes"></a>1등 상품

다음 어워드는 범위 내 리포지토리에 대한 타당한 기여 수로 계산됩니다. 병합 또는 게시될 필요는 없고 회의 종료까지 끌어오기 요청으로 제출되면 됩니다. Microsoft는 부정 행위로 판단되는 사용자의 자격을 박탈할 권한을 보유합니다. 각 범주의 수상자는 Yeti Rambler 로고가 있는 30oz 텀블러와 Popsocket 로고가 있는 자동차 통풍구 거치대를 받습니다. 범주별 수상자는 한 명입니다.

- **가장 많은 커밋 제출**

- **가장 많은 줄 변경**

- **가장 많은 문서 작업**

> [!Note]  
> 가장 많은 이슈 제출에 대한 수상자 혜택은 제공하지 않습니다. 피드백은 도움이 되지만 이 이벤트에서 중요한 것은 기여하는 것입니다.

## <a name="resources"></a>리소스

- [Microsoft Style](https://aka.ms/MicrosoftStyle)(Microsoft 스타일)

    - [빠른 시작](https://docs.microsoft.com/contribute/style-quick-start)

    - [Top 10 tips for Microsoft style and voice](https://docs.microsoft.com/style-guide/top-10-tips-style-voice)(Microsoft 스타일 및 음성에 대한 상위 10가지 팁)

- [기여자 가이드](https://docs.microsoft.com/contribute)

- [Markdown을 사용하여 Docs를 작성하는 방법](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

## <a name="official-rules"></a>공식 규칙

Microsoft Cloud + AI 개발자 관계 콘텐츠 및 학습 MMS 2019 Docathon 이벤트 콘테스트 공식 규칙

1. 스폰서

    이 공식 규칙(“규칙”)은 Microsoft C+AI 개발자 관계 콘텐츠 MMS 2019 Docathon 이벤트 콘테스트("콘테스트")의 운영에 적용됩니다. Microsoft Corporation은 스폰서("스폰서")입니다.

2. 정의

    이 규칙에서 “Microsoft”, “당사” 및 “우리”는 스폰서를 나타냅니다. "귀하"는 콘테스트 참가자를 나타냅니다. “이벤트”는 미네소타주 미니애폴리스에서 개최되는 MMS 2019 Docathon 이벤트를 나타냅니다. 출품하는 것은 이 규칙이 적용됨에 동의하는 것입니다.

3. 출품 기간

    콘테스트는 2019년 5월 6일부터 5월 9일까지(“출품 기간”) 정규 이벤트 시간 중에 운영됩니다.

4. 자격

    미국 50개 주(콜럼비아 특별구 포함)의 법적 거주자인 18세 이상 등록된 이벤트 참석자에게 개방합니다. Microsoft Corporation 및 자회사의 직원과 임원, 이 프로모션의 진행과 관리에 관련된 사람 및 각각의 가족 구성원(부양 가족, 직계 가족 및 동일 세대에 거주하는 개인)은 자격이 없습니다. 금지된 지역에서는 자격이 없습니다.

    비즈니스/박람회 이벤트의 경우: 직원 자격으로 이벤트에 참석하는 경우 고용주의 상품 정책을 준수할 책임은 귀하에게 있습니다. Microsoft는 이 문제에 관련된 모든 분쟁 또는 행위에 관여하지 않습니다. 교육자를 포함한 정부 직원: Microsoft는 정부 상품 및 윤리 규칙을 준수하므로 정부 및 공공 부문 직원은 이 프로모션에 참여할 자격이 없습니다.

5. 출품 방법

    출품작을 만들려면 다음 GitHub 리포지토리에서 문서의 편집 내용을 제출합니다. IntuneDocs, SCCMDocs, sccm-docs-powershell-ref. 제출 프로세스에 대한 자세한 내용은 [기여하는 방법](https://docs.microsoft.com/sccm/core/understand/use-docs#bkmk_contribute)을 참조하세요.

    출품작을 제출하려면 GitHub에서 끌어오기 요청을 제출합니다.

    제출하는 출품작 수에는 제한이 없습니다. 개인당 범주별로 하나의 수상자 혜택만 제공합니다.

    Microsoft는 초과하거나, 손실되거나, 늦거나, 손상되거나, 불완전한 출품작에 대한 책임을 지지 않습니다. 분쟁이 있는 경우 출품작은 GitHub 계정의 허가된 계정 보유자가 제출한 것으로 간주합니다.

6. 적격 출품작

    적격한 출품작은 다음 콘텐츠/기술 요구 사항을 충족해야 합니다.

    - 출품작은 직접 제작한 내용이어야 하고,
    - 출품작은 다른 콘테스트의 수상자로 선정된 적이 없어야 하고,
    - 출품작을 제출하는 데 필요한 모든 동의 승인 또는 라이선스를 획득한 상태여야 하고,
    - 출품 시 소프트웨어, 사진, 동영상, 음악, 미술품, 에세이 등 사용자가 제작한 출품작을 제출해야 하므로 출품자는 해당 출품작이 직접 제작한 내용이고, 권한 또는 명시적 권리 없이 다른 내용에서 복사되지 않았고, 프라이버시, 지적 재산권 또는 다른 사람이나 단체의 기타 권리를 위반하지 않음을 보증합니다. Microsoft가 귀하에게 이 콘테스트에 출품작을 제출할 목적만으로 사용하도록 제한적 라이선스를 부여하는 Microsoft 상표, 로고 및 디자인을 포함할 수 있습니다.
    - Microsoft의 절대적인 단독 재량에 따라 결정된 대로, 출품작은 모욕적 또는 외설적이거나, 폭력적이거나, 욕설이 포함되거나, 비난이 포함되거나 불법적이거나, 음주, 흡연 또는 특정 정치적 선전을 장려하거나, Microsoft의 선의에 부정적 인상을 줄 수 있는 메시지를 전달하는 모든 콘텐츠를 포함할 수 없습니다.

7. 출품작 사용

    Microsoft는 귀하의 제출작에 대한 소유권을 주장하지 않습니다. 그러나 출품작을 제출하는 것은 이 콘테스트와 관련하여 출품작 및 모든 해당 콘텐츠를 사용, 검토, 평가, 테스트 및 분석하며, 귀하의 추가 허가 없이 Microsoft 제품이나 서비스의 마케팅, 판매 또는 홍보를 포함하되 이에 제한되지 않는 현재 알려지고 향후 비상업적 또는 상업적 목적으로 고안되는 모든 미디어에서 해당 출품작을 사용할 수 있는 변경 불가능하고, 로열티가 없고, 전 세계적인 권리 및 라이선스를 Microsoft에 부여하는 것입니다. 이 공식 규칙에 설명된 내용 이외에는 출품작 사용에 대한 보상이나 크레딧을 받지 못합니다.

    출품하는 것은 Microsoft가 해당 출품작과 유사하거나 동일한 자료를 개발하거나 의뢰했을 수 있음을 인정하고 해당 출품작과 유사함으로 인해 발생하는 모든 권리 주장을 포기하는 것입니다. 또한 출품작에 액세스할 수 있었던 담당자의 작업 할당을 제한하지 않을 것을 이해하고, Microsoft 제품 또는 서비스를 개발하거나 배포할 때 해당 담당자의 자발적인 기억에 따른 정보 사용이 이 계약이나 저작권법 또는 영업 비밀 보호법에 따라 Microsoft의 책임을 형성하지 않음에 동의하는 것입니다.

    출품작은 공용 웹 사이트에 게시될 수 있습니다. Microsoft는 이 웹 사이트 방문자가 해당 출품작을 무단 사용하는 것에 대한 책임을 지지 않습니다. Microsoft는 해당 출품작이 수상 출품작으로 선정된 경우에도 어떤 용도로 사용할 의무는 없습니다.

8. 수상자 선정 및 알림

    자격 확인이 보류 중인 잠재적인 수상자는 Microsoft나 해당 에이전트 또는 적격한 판정단에 의해 다음 판정 기준에 따라 접수된 모든 적격 출품작 중에서 선정됩니다.

    - 대상: 다음 기준에 따라 가장 영향력 있음:
        - 50% - 커뮤니티 혜택
        - 25% - Microsoft 스타일 준수
        - 25% - 적절한 markdown
    - 다음 1등 수상자 혜택은 범위 내 리포지토리에 대한 타당한 기여 수로 계산됩니다. 병합 또는 게시될 필요는 없고 회의 종료까지 끌어오기 요청으로 제출되면 됩니다. Microsoft는 부정 행위로 판단되는 사용자의 자격을 박탈할 권한을 보유합니다.
        - 가장 많은 커밋 제출
        - 가장 많은 줄 변경
        - 가장 많은 문서 작업

    수상자는 2019년 5월 9일 목요일 오후 3시(중부 표준시) 이후 선정됩니다.

    수상자는 이벤트 중에 알림을 받으며 이벤트 종료 전에 수상자 혜택을 청구해야 합니다.

    적격 출품작 중에 동률이 있는 경우 추가 판정을 통해 위에 설명된 판정 기준에 따라 수상자를 선정합니다. 판정단의 결정은 최종적이고 구속력이 있습니다. 출품 요구 사항을 충족하는 충분한 수의 출품작을 접수하지 못하면 Microsoft는 재량에 따라 아래 설명된 콘테스트 수상자 혜택 수보다 적은 수상자를 선정할 수 있습니다.

    수상자는 출품하는 동안 제공한 연락처 정보를 통해 알림을 받으며, 수상자 혜택 청구 및 세금 양식(“양식”)을 작성해야 할 수 있습니다. 선정된 수상자가 연락 되지 않거나, 적격하지 않거나, 수상자 혜택을 청구하지 않거나, 양식을 반환하지 않는 경우에는 선정된 수상자는 수상자 혜택을 받지 못하고 허용된 시간에 대체 수상자가 선정됩니다. 청구되지 않은 수상자 혜택이 제공되고 있지 않을 경우 이후 대체 수상자는 세 명만 선정됩니다.  

9. 수상자 혜택

    다음 수상자 혜택이 제공됩니다.

    - 대상 한(1) 명. 다음 항목으로 구성된 수상자 혜택 패키지:
        - [MMS Jazz Edition](https://mmsmoa.com/registration/mms-jazz-edition.html) 등록 패스(MMS 운영 위원회에서 제공). $1799 ARV(Approximate Retail Value)
        - Yeti Rambler 30oz 텀블러. $35.00 ARV(Approximate Retail Value).
        - Popsocket 자동차 통풍구 거치대. $15.00 ARV(Approximate Retail Value).

        이 패키지의 총 ARV(Approximate Retail Value)는 $1849입니다.

    - 1등 세(3) 명. 다음 항목으로 구성된 수상자 혜택 패키지:
        - Yeti Rambler 30oz 텀블러. $35.00 ARV(Approximate Retail Value).
        - Popsocket 자동차 통풍구 거치대. $15.00 ARV(Approximate Retail Value).

        이 패키지의 총 ARV(Approximate Retail Value)는 $50입니다.

    모든 수상자 혜택의 총 ARV(Approximate Retail Value): $1999

    개인당 하나(1)의 수상자 혜택만 제공합니다. 수상자 혜택은 명시된 개수 이하로 제공됩니다. 수상자 혜택의 대체, 이전 또는 양도는 허용되지 않습니다. 단, 제공되는 수상자 혜택을 사용할 수 없는 경우 Microsoft가 동일하거나 더 큰 가치의 수상자 혜택을 대체할 권리를 보유한다는 것은 예외로 합니다. 수상자 혜택은 상품성, 특정 목적에의 적합성 또는 비침해성에 대한 묵시적 보증을 포함하되 이에 제한되지 않는 어떠한 명시적 또는 묵시적 보증 없이 “있는 그대로” 제공됩니다. 수상자는 수상자 알림에 명시된 기한 내에 수상자 혜택 청구 및/또는 세금 양식(“양식”)을 작성 및 반환해야 할 수 있습니다. 수상자 혜택에 대한 세금(있는 경우)은 수상자의 단독 책임이며, 수상자는 수상자 혜택 수락의 세금과 관련해 독자적인 자문을 구하는 것이 좋습니다. 수상자 혜택을 수락하는 것은 법적으로 금지되는 경우를 제외하고, Microsoft가 비용 지급이나 보상 없이 이 콘테스트에 관련된 해당 출품작, 이름, 이미지 및 출신지를 온라인과 인쇄물 또는 기타 미디어에서 사용할 수 있음에 동의하는 것입니다.

10. 가능성

    수상 가능성은 접수된 적격 출품작의 수 및 품질을 기준으로 합니다.

11. 일반 조건 및 책임 면제

    법률이 허용하는 범위 내에서, 출품하는 것은 이 콘테스트 또는 모든 수상자 혜택과 관련하여 발생하는 모든 책임이나 모든 종류의 손상, 손실 또는 피해로부터 Microsoft 및 해당하는 각 모회사, 파트너, 자회사, 계열사, 직원 및 에이전트를 면제 및 보호함에 동의하는 것입니다.

    모든 현지 법률이 적용됩니다. Microsoft의 결정은 최종적이고 구속력이 있습니다.

    Microsoft는 인간 또는 기계 관련이든 관계없이 이 콘테스트의 무결성에 영향을 주는 부정 행위, 기술 오류, 재해, 전쟁 또는 기타 모든 예상치 못한 이벤트를 포함하여 어떠한 이유로 이 콘테스트를 취소, 변경 또는 일시 중단할 권리를 보유합니다. 콘테스트의 무결성을 복원할 수 없는 경우 Microsoft는 콘테스트를 취소, 변경 또는 일시 중단해야 하는 시점 전에 접수한 모든 적격 출품작 중에서 수상자를 선정할 수 있습니다. 규칙 위반자는 법이 허용하는 최대 한도까지 처벌을 받게 되며 Microsoft 콘테스트 참가가 금지될 수 있습니다.

12. 수상자 목록

    수상자 목록은 2019년 5월 9일부터 30일 이내에 https://aka.ms/mms2019docathon에 게시됩니다.

13. 개인 정보

    Microsoft는 개인 정보를 보호하기 위해 최선을 다하고 있습니다. Microsoft는 이 양식에서 귀하가 제공하는 정보를 사용하여 제품, 업그레이드 및 개선 사항에 대한 중요한 정보를 알리고 기타 Microsoft 제품 및 서비스에 대한 정보를 전송합니다. Microsoft는 요청한 서비스나 트랜잭션을 완료하는 데 필요한 경우를 제외하고 또는 법에서 요구하는 대로 귀하의 허가 없이 귀하가 제공하는 정보를 제3자와 공유하지 않습니다. Microsoft는 사용자의 개인 정보를 보호하기 위해 최선을 다할 것을 약속합니다. 사용자의 개인 정보가 무단으로 액세스, 사용 또는 공개되지 않도록 보호하기 위해 다양한 기술과 절차를 사용하고 있습니다. 개인 정보는 위에 설명된 조건에 해당하는 경우 외에는 귀하의 허가 없이 회사 외부에서 공유되지 않습니다.

    Microsoft가 이 진술을 준수하지 않는다고 판단되는 경우 privrc@microsoft.com에 메일 보내거나 Microsoft Privacy Response Center, Microsoft Corporation, One Microsoft Way, Redmond, WA 98052에 우편물을 보내 Microsoft에 문의하세요.
