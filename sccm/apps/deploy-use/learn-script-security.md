---
title: PowerShell 스크립트 보안에 대해 자세히 알아보기
titleSuffix: Configuration Manager
description: PowerShell 스크립트 보안에 대해 알아볼 수 있는 리소스입니다.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: a0bd093d-67a5-4f74-bf79-dd604889f5ba
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0c2f2f13d20f1148e85f06ade8c0410c0c48b132
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75815700"
---
# <a name="learn-more-about-powershell-script-security"></a>PowerShell 스크립트 보안에 대해 자세히 알아보기

*적용 대상: Configuration Manager(현재 분기)*

관리자는 환경에서 제안된 PowerShell 및 PowerShell 매개 변수 사용의 유효성을 검사해야 합니다. PowerShell 및 잠재적 위험 표면의 기능에 대한 관리자를 학습할 수 있는 몇 가지 유용한 리소스는 다음과 같습니다. 잠재적 위험 표면을 완화하고 안전한 스크립트를 사용할 수 있도록 합니다.

## <a name="powershell-script-security"></a>PowerShell 스크립트 보안
스크립트 실행에 기본 제공되는 기능은 환경에서 실행되도록 요청된 스크립트를 시각적으로 검토하고 승인하는 것입니다. 관리자는 PowerShell 스크립트가 스크립트 승인 프로세스 중에 악성이거나 시각적 검사에서 감지하기 어려운 경우 난독 처리될 수 있다는 점을 알고 있어야 합니다. 모범 사례로 PowerShell 스크립트를 시각적으로 검토하는 것 외에도 특정 검사 도구를 사용하여 의심스러운 스크립트 문제를 감지할 수 있습니다. 이러한 도구에서는 의심스러운 스크립트에 주의할 수 있도록 PowerShell 작성자의 의도를 확인하지 못할 수도 있습니다. 하지만 도구에서 관리자가 악성 또는 의도적인 스크립트 구문인지를 판단해야 합니다.

## <a name="recommendations"></a>권장 사항
- 아래에 참조한 다양한 링크를 사용하여 PowerShell 보안 모범 사례를 이해합니다.
- **스크립트에 서명**: 스크립트를 보호하는 다른 메서드는 사용하기 위해 가져오기 전에 조사한 다음, 서명하는 것입니다.
- PowerShell 스크립트에서 암호를 저장하지 않고 암호를 처리하는 방법에 대해 자세히 알아봅니다.


## <a name="general-information-about-powershell-security-best-practices"></a>PowerShell 보안 모범 사례에 대한 일반 정보

링크의 이 컬렉션을 선택하여 Configuration Manager 관리자에게 PowerShell 스크립트 보안 모범 사례에 대해 학습하는 시작점을 제공했습니다.  

[PowerShell 보안 모범 사례 소개](https://blogs.msdn.microsoft.com/powershell/2013/12/16/powershell-security-best-practices/ )

[PowerShell 보안 모범 사례 PowerPoint](https://msdnshared.blob.core.windows.net/media/MSDNBlogsFS/prod.evol.blogs.msdn.com/CommunityServer.Blogs.Components.WeblogFiles/00/00/00/63/74/metablogapi/1055.PowerShell-Security-Best-Practices_3CA24C32.pptx)

<iframe src="https://channel9.msdn.com/Events/Blue-Hat-Security-Briefings/BlueHat-Security-Briefings-Fall-2013-Sessions/PowerShell-Best-Practices/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>

[PowerShell 공격에 대한 방어, PowerShell 팀 블로그](https://blogs.msdn.microsoft.com/powershell/2017/10/23/defending-against-powershell-attacks/)

[PowerShell 공격 twitter에 대한 방어, Microsoft PowerShell 및 보안 지원 Lee Holmes](https://twitter.com/Lee_Holmes/status/922462821081694208)

[악성 코드 삽입으로부터 보호](https://blogs.msdn.microsoft.com/powershell/2006/11/22/protecting-against-malicious-code-injection/)

[PowerShell 블루팀, 심층 스크립트 블록 로깅, 보호된 이벤트 로깅, 맬웨어 방지 검사 인터페이스, 보안 코드 생성 API에 대해 설명](https://blogs.msdn.microsoft.com/powershell/2015/06/09/powershell-the-blue-team/)

[Windows 10의 경우 맬웨어 방지 검사 인터페이스에 대한 API가 있습니다.](https://cloudblogs.microsoft.com/microsoftsecure/2015/06/09/windows-10-to-offer-application-developers-new-malware-defenses/?source=mmpc)

## <a name="powershell-parameters-security"></a>PowerShell 매개 변수 보안
매개 변수를 전달하는 것은 스크립트에서 유연성을 갖고 런타임까지 결정을 연기하는 방법입니다. 다른 위험 표면이 시작될 수도 있습니다. 악성 매개 변수 또는 스크립트 삽입을 방지하기 위한 최상의 방법은 다음과 같습니다.

- 미리 정의된 매개 변수만을 사용하도록 허용합니다.
- 허용되는 매개 변수의 유효성을 검사하기 위해 정규식 기능을 사용합니다.
    - 예제: 특정 값 범위만이 허용되는 경우 정규식을 사용하여 범위를 만들 수 있는 해당 문자 또는 값에 대해서만 검사합니다.
    - 매개 변수의 유효성을 검사하면 사용자가 따옴표 등의 이스케이프될 수 있는 특정 문자를 사용하지 않도록 방지할 수 있습니다. 여러 형식의 따옴표가 있을 수 있습니다. 따라서 확인한 문자를 허용하는지 유효성을 검사하는 정규식을 사용하는 편이 허용되지 않는 모든 입력을 정의하는 것보다 쉽습니다.
- PowerShell 갤러리에서 PowerShell 모듈 ["주입 사냥꾼"](https://www.powershellgallery.com/packages/InjectionHunter/1.0.0)을 활용합니다.
    - 거짓 긍정일 수 있습니다. 따라서 항목이 의심스럽다는 플래그가 지정된 경우 실제 문제가 있는지 확인하려면 의도를 찾아봅니다. 
- Microsoft Visual Studio에는 PowerShell 구문을 확인하여 지원할 수 있는 스크립트 분석기가 있습니다.
- 이 비디오 제목: “DEF CON 25 - Lee Holmes - Get $pwnd: 전투가 격화된 Windows Server 공격”에서는 보호할 수 있는 형식의 문제 개요를 제공합니다(특히 섹션 12:20에서 17:50).     <iframe width="560" height="315" src="https://www.youtube.com/embed/ahxMOAAani8" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen></iframe>

## <a name="environment-recommendations"></a>환경 권장 사항
PowerShell 관리자에 대한 일반 권장 사항입니다.
1. Windows 10에 기본 제공된 버전 5 이상인 최신 버전의 PowerShell을 배포합니다. 또는 Windows 7 및 Windows Server 2008 R2에 지원되고 해당 기능을 포함하는 [Windows Management Framework](https://www.microsoft.com/download/details.aspx?id=54616)를 배포할 수 있습니다. 
2. 경우에 따라 보호된 이벤트 로깅을 비롯한 PowerShell 로그를 사용하고 수집합니다. 서명, 사냥 및 인시던트 대응 워크플로에 이러한 로그를 통합합니다.
3. 중요 시스템에 적당한 관리를 구현하여 해당 시스템에 대해 제한되지 않는 관리 액세스를 제거하거나 권한을 축소합니다.
4. PowerShell 언어의 제한된 하위 집합에 승인되지 않은 대화형 사용을 제한하는 동안 사전 승인된 관리 작업이 PowerShell 언어의 전체 기능을 사용하도록 허용하는 Windows Defender Application Control 정책을 배포합니다.
5. Windows 10을 배포하여 바이러스 백신 공급자에게 PowerShell을 비롯한 Windows 스크립팅 호스트에서 처리되는 모든 콘텐츠(런타임 시 생성되거나 난독 처리가 취소된 콘텐츠 포함)에 대한 전체 액세스 권한을 허용합니다.
