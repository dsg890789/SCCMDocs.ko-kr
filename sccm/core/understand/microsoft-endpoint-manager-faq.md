---
title: Microsoft Endpoint Configuration Manager FAQ
titleSuffix: Configuration Manager
description: Microsoft Endpoint Configuration Manager에 대해 자주 묻는 질문
ms.date: 11/29/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: be276b34-e283-4386-8b45-5629e431c50d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4c9c1014a153048ffd83ae1e0a5385c2cfcdc5fb
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75825798"
---
# <a name="microsoft-endpoint-configuration-manager-faq"></a>Microsoft Endpoint Configuration Manager FAQ

*적용 대상: Configuration Manager(현재 분기, 기술 미리 보기 분기)*

버전 1910부터, Configuration Manager가 Microsoft Endpoint Manager의 일부가 됩니다. 이 문서에서는 자주 묻는 질문에 대한 답변을 제공합니다.

## <a name="summary"></a>요약

먼저 Microsoft 365 부사장 Brad Anderson이 출연하는 2분 분량의 동양상을 시청하세요.

> [!VIDEO https://www.youtube.com/embed/GS7oNPInFuw]

## <a name="faqs"></a>FAQ(질문과 대답)

### <a name="what-is-microsoft-endpoint-manager"></a>Microsoft Endpoint Manager란?

Microsoft Endpoint Manager는 모든 디바이스를 관리하기 위한 통합 솔루션입니다. Microsoft는 간소화된 라이선싱을 통해 Configuration Manager와 Intune을 함께 제공합니다. 원하는 대로 Microsoft 클라우드의 강력한 기능을 활용하면서 기존 Configuration Manager 투자를 계속 활용하세요.

다음 Microsoft 관리 솔루션은 이제 모두 **Microsoft Endpoint Manager** 브랜드의 일부입니다.

- [Configuration Manager](https://docs.microsoft.com/configmgr)
- [Intune](https://docs.microsoft.com/intune)
- [Desktop Analytics](/configmgr/desktop-analytics/overview)
- [Autopilot](https://docs.microsoft.com/intune/enrollment/enrollment-autopilot)
- [Device Management 관리자 콘솔](https://go.microsoft.com/fwlink/?linkid=2109094)의 기타 기능

자세한 내용은 Microsoft 365의 Microsoft 기업 부사장인 Brad Anderson의 다음 게시물을 참조하세요.

- [공지 블로그 게시물](https://aka.ms/cmannounce)
- [비전 용지](https://aka.ms/MEMVisionPaper)

### <a name="what-things-change-in-configuration-manager-with-microsoft-endpoint-manager"></a>Configuration Manager가 Microsoft Endpoint Manager의 일부가 되면서 무엇이 달라졌나요?

버전 1910에서는 이름 변경을 제외하고는 Configuration Manager의 기능이 전과 동일합니다.

가장 눈에 띄는 변화로 시작 메뉴 폴더에서 [Configuration Manager 콘솔](/configmgr/core/servers/manage/admin-console#bkmk_open), [소프트웨어 센터](/configmgr/core/understand/software-center#bkmk_open)와 같은 공통 구성 요소의 이름이 변경된 것을 들 수 있습니다.

### <a name="how-do-we-refer-to-the-product-now"></a>이제 이 제품을 뭐라고 불러야 하나요?

- 모든 구성 요소를 포함하는 전체 솔루션을 가리킬 때: **Microsoft Endpoint Manager**

- 온-프레미스 구성 요소를 가리킬 때:
  - 처음 언급할 때는 전체 브랜드 이름 사용: **Microsoft Endpoint Configuration Manager**
  - 일반적인 용도: **Configuration Manager**
  - 공간이 제한된 용도: **ConfigMgr** - 일반적인 용도 이름이 적합하지 않은 경우에만

### <a name="are-there-any-licensing-changes"></a>라이선스에도 변경되나요?

예. Microsoft Ignite 2019에서 발표된 바와 같이, Configuration Manager를 사용하도록 라이선스가 부여된 경우에는 이제 Intune을 사용하여 Windows PC를 [공동 관리](/configmgr/comanage/overview)할 수 있습니다. 자세한 내용은 [제품 및 라이선스 FAQ](/configmgr/core/understand/product-and-licensing-faq#bkmk_mem)를 참조하세요.

### <a name="why-do-i-still-see-system-center-configuration-manager-some-places"></a>아직까지 “System Center Configuration Manager”라고 표시된 곳도 있는데 그 이유는 무엇인가요?

모든 제품과 서비스, 설명서와 같은 지원 자료에서 명칭을 바꾸는 데는 시간이 좀 걸립니다.

앞으로도 변경되지 않을 기본적인 구성 요소도 있습니다. 사이트 서버의 기본 Windows 서비스는 종전과 같이 **SMS_Executive**입니다. 이 설명서를 지원하는 GitHub 리포지토리는 앞으로도 종전과 같이 **SCCMDocs**입니다.

## <a name="next-steps"></a>다음 단계

[Configuration Manager 증분 버전의 새로운 기능](/configmgr/core/plan-design/changes/whats-new-incremental-versions)을 알아보세요.
