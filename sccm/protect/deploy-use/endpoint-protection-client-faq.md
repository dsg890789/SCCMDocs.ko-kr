---
title: Endpoint Protection 클라이언트에 대한 질문과 대답
titleSuffix: Configuration Manager
description: Windows Defender 및 Endpoint Protection에 대한 질문과 대답을 확인합니다.
ms.date: 12/09/2017
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: e3aaa9d2-a40e-42b1-ad75-5a115351729e
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 642f74319fca149cce15c019a473904641b4ea9e
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "70902939"
---
# <a name="endpoint-protection-client-frequently-asked-questions"></a>Endpoint Protection 클라이언트에 대한 질문과 대답

*적용 대상: System Center Configuration Manager(현재 분기)*


이 FAQ는 해당 IT 관리자가 관리되는 컴퓨터에 Windows Defender 또는 Endpoint Protection을 배포한 컴퓨터 사용자를 위한 것입니다. 여기 내용은 다른 맬웨어 방지 프로그램에 적용되지 않을 수 있습니다. Microsoft System Center Endpoint Protection은 Windows 10에서 Windows Defender를 관리합니다. 또한 Windows 10 이전의 컴퓨터에 Endpoint Protection 클라이언트를 배포하고 관리할 수 있습니다. 이 문서에서 Windows Defender가 설명되고 있지만 해당 정보가 Endpoint Protection에도 적용됩니다.  

-   [바이러스 백신 및 스파이웨어 방지 소프트웨어가 필요한 이유는 무엇인가요?](#why-do-i-need-antivirus-and-antispyware-software)  
-   [컴퓨터가 악성 소프트웨어에 감염되었는지 어떻게 알 수 있나요?](#how-can-i-tell-if-my-computer-is-infected-with-malicious-software)
-   [Windows Defender의 버전을 어떻게 확인할 수 있나요?](#how-can-i-find-the-version-of-windows-defender)
-   [Windows Defender 또는 Endpoint Protection이 컴퓨터에서 악성 소프트웨어를 발견할 경우 어떻게 해야 하나요?](#what-should-i-do-if-windows-defender-or-endpoint-protection-detects-malicious-software-on-my-computer)  
-   [바이러스란 무엇인가요?](#what-is-a-virus)  
-   [스파이웨어란 무엇인가요?](#what-is-spyware)  
-   [바이러스, 스파이웨어 및 기타 잠재적으로 위험한 소프트웨어 간의 차이는 무엇인가요?](#whats-the-difference-between-viruses-spyware-and-other-potentially-harmful-software)  
-   [바이러스, 스파이웨어 및 기타 사용자 동의 없이 설치된 소프트웨어의 출처는 무엇인가요?](#where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from)  
-   [자기도 모르는 사이에 악성 소프트웨어를 받을 수 있나요?](#can-i-get-malicious-software-without-knowing-it)  
-   [소프트웨어를 설치하기 전에 사용권 계약을 검토하는 것이 중요한 이유는 무엇인가요?](#why-is-it-important-to-review-license-agreements-before-installing-software)  
-   [Endpoint Protection 및 Windows Defender의 차이는 무엇인가요?](#whats-the-difference-between-endpoint-protection-and-windows-defender)  
-   [Windows Defender가 쿠키를 검색하지 않는 이유는 무엇인가요?](#why-doesnt-windows-defender-detect-cookies)  
-   [맬웨어를 방지하려면 어떻게 해야 하나요?](#how-can-i-prevent-malware)  
-   [바이러스 및 스파이웨어 정의란?](#what-are-virus-and-spyware-definitions)  
-   [바이러스 및 스파이웨어 정의를 최신 상태로 유지하려면 어떻게 해야 하나요?](#how-do-i-keep-virus-and-spyware-definitions-up-to-date)  
-   [Windows Defender 또는 Endpoint Protection에 의해 격리된 항목을 제거 또는 복원하려면 어떻게 하나요?](#how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection)  
-   [실시간 보호란?](#what-is-real-time-protection)  
-   [컴퓨터에서 Windows Defender 또는 Endpoint Protection이 실행되고 있는지 확인하려면 어떻게 하나요?](#how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer)
-   [Windows Defender 또는 Endpoint Protection 경고를 설정하는 방법](#how-to-set-up-windows-defender-or-endpoint-protection-alerts)  

##  <a name="why-do-i-need-antivirus-and-antispyware-software"></a>바이러스 백신 및 스파이웨어 방지 소프트웨어가 필요한 이유는 무엇입니까?  

 악성 소프트웨어로부터 보호해 주는 소프트웨어가 컴퓨터에서 실행되고 있는지 확인하는 것은 중요합니다. 바이러스, 스파이웨어 또는 그 밖의 사용자 동의 없이 설치되는 소프트웨어를 비롯한 악성 소프트웨어는 컴퓨터가 인터넷에 연결되어 있으면 언제든지 자동으로 설치를 시도할 수 있습니다. CD, DVD 또는 기타 이동식 미디어를 사용하여 프로그램을 설치할 때도 컴퓨터가 감염될 수 있습니다. 또한 설치할 때만이 아니라 예기치 않은 시간에 실행되도록 프로그래밍된 악성 소프트웨어도 있을 수 있습니다.  

 Windows Defender 또는 Endpoint Protection에서는 컴퓨터가 악성 소프트웨어에 감염되지 않도록 하는 데 유용한 세 가지 방법을 제공합니다.  

-   **실시간 보호 사용** - Windows Defender에서는 실시간 보호를 통해 항상 컴퓨터를 모니터링하고 바이러스, 스파이웨어 또는 그 밖의 사용자 동의 없이 설치되는 소프트웨어를 비롯한 악성 소프트웨어가 컴퓨터에서 자동으로 설치 또는 실행을 시도할 때 사용자에게 경고할 수 있습니다. 그런 다음 Windows Defender에서는 해당 소프트웨어를 일시 중단하고 사용자가 해당 소프트웨어에 대해 권장 조치를 따르거나 다른 조치를 수행할 수 있도록 합니다.

-   **검사 옵션** - Windows Defender를 사용하여 바이러스, 스파이웨어 및 컴퓨터를 위험에 빠트릴 수 있는 기타 악성 소프트웨어와 같은 잠재적인 위협 요소를 검사할 수 있습니다. 정기적 검사를 예약하고 검사 중 검색된 악성 소프트웨어를 제거할 수도 있습니다.  

-   **Microsoft 활성 보호 서비스 커뮤니티** - 온라인 Microsoft 활성 보호 서비스 커뮤니티에서는 아직 위험 여부가 분류되지 않은 소프트웨어에 대한 다른 사용자의 대처 방법을 확인할 수 있습니다. 이 정보를 사용하여 컴퓨터에서 이 소프트웨어를 허용할지 여부를 선택할 수 있습니다. 또한 참여 시 사용자의 선택 사항이 커뮤니티 등급에 추가되어 다른 사용자가 대처 방법을 결정하는 데 활용됩니다.  

##  <a name="how-can-i-tell-if-my-computer-is-infected-with-malicious-software"></a>컴퓨터가 악성 소프트웨어에 감염되었는지를 어떻게 알 수 있나요?  

 다음과 같은 경우 바이러스, 스파이웨어 또는 기타 사용자 동의 없이 설치된 소프트웨어를 비롯한 몇 가지 형태의 악성 소프트웨어가 있는 것일 수 있습니다.  

-   웹 브라우저에 추가하려고 하지 않은 새 도구 모음, 링크 또는 즐겨찾기가 추가되어 있습니다.  

-   홈페이지, 마우스 포인터 또는 검색 프로그램이 예기치 않게 변경됩니다.  

-   검색 엔진 등에 특정 사이트의 주소를 입력하지만 예고 없이 다른 웹 사이트로 이동됩니다.  

-   파일이 컴퓨터에서 자동으로 삭제됩니다.  

-   컴퓨터가 다른 컴퓨터를 공격하는 데 사용됩니다.  

-   인터넷에 연결되어 있지 않은데 팝업 광고가 표시됩니다.  

-   컴퓨터가 갑자기 보통 때보다 더 느리게 실행되기 시작합니다. 모든 컴퓨터 성능 문제가 악성 소프트웨어로 인해 발생하는 것은 아니지만 악성 소프트웨어(특히 스파이웨어)로 인해 눈에 띄는 변화가 발생할 수 있습니다.  

증상이 보이지 않아도 컴퓨터에 악성 소프트웨어가 있을 수 있습니다. 이러한 종류의 소프트웨어는 사용자 모르게 동의 없이 사용자 및 컴퓨터에 대한 정보를 수집할 수 있습니다. 사용자의 개인 정보 및 컴퓨터를 보호하려면 Windows Defender 또는 Endpoint Protection을 실행해야 합니다.  

## <a name="how-can-i-find-the-version-of-windows-defender"></a>Windows Defender의 버전을 어떻게 확인할 수 있나요?
 컴퓨터에서 실행 중인 Windows Defender의 버전을 보려면 Windows Defender를 열고(**시작**을 클릭한 후 **Windows Defender** 검색) **설정**을 클릭한 다음 Windows Defender 설정 아래쪽으로 스크롤하여 **버전 정보**를 확인합니다.

##  <a name="what-should-i-do-if-windows-defender-or-endpoint-protection-detects-malicious-software-on-my-computer"></a>Windows Defender 또는 Endpoint Protection이 컴퓨터에서 악성 소프트웨어를 발견할 경우 어떻게 해야 하나요?  

 Windows Defender에서는 실시간 보호를 사용하여 컴퓨터를 모니터링할 때나 검사를 실행한 후에 컴퓨터에서 악성 소프트웨어나 사용자 동의 없이 설치된 소프트웨어가 검색되면 화면의 오른쪽 아래에 알림 메시지를 표시하여 검색된 항목에 대해 사용자에게 알려 줍니다.  

 알림 메시지에는 **컴퓨터 치료** 단추와 검색된 항목에 대한 추가 정보를 보여 주는 **자세한 정보 표시** 링크가 포함됩니다. **자세한 정보 표시** 링크를 클릭하면 **잠재적인 위협 요소 정보** 창이 열리고 검색된 항목에 대한 추가 정보가 표시됩니다. 이 창에서 항목에 적용할 조치를 선택하거나 **컴퓨터 치료**를 클릭할 수 있습니다. 검색된 항목에 적용할 조치를 결정하는 데 도움이 필요하면 Windows Defender에서 사용자를 돕기 위해 항목에 할당한 경고 수준을 사용합니다. 자세한 내용은 경고 수준 이해를 참조하세요.  

 경고 수준을 통해 바이러스, 스파이웨어 및 기타 사용자 동의 없이 설치된 소프트웨어에 대응하는 방법을 선택할 수 있습니다. Windows Defender에서는 바이러스와 스파이웨어를 모두 제거할 것을 권장하지만 플래그가 지정된 모든 소프트웨어가 악성이거나 사용자 동의 없이 설치되는 소프트웨어인 것은 아닙니다. 다음 정보는 Windows Defender가 컴퓨터에서 사용자 동의 없이 설치된 소프트웨어를 검색할 경우 수행할 작업을 결정하는 데 도움이 됩니다.  

 경고 수준에 따라 다음 조치 중 하나를 선택하여 검색된 항목에 적용할 수 있습니다.  

- **제거** - 이 작업을 수행하면 해당 소프트웨어가 컴퓨터에서 영구적으로 삭제됩니다.  

- **격리** - 이 작업을 수행하면 해당 소프트웨어가 실행되지 않도록 격리됩니다. Windows Defender에서는 소프트웨어를 격리할 때 소프트웨어를 컴퓨터의 다른 위치로 이동한 다음 사용자가 복원하거나 컴퓨터에서 제거하도록 선택할 때까지 이 소프트웨어가 실행되지 않도록 합니다.  

- **허용** -이 작업을 수행하면 소프트웨어가 Windows Defender 허용 목록에 추가되어 컴퓨터에서 실행할 수 있게 됩니다. Windows Defender에서는 해당 소프트웨어가 사용자의 개인 정보나 컴퓨터에 끼칠 수 있는 위험에 대한 경고를 표시하지 않습니다.  

  소프트웨어 등의 항목에 대해 **허용** 을 선택하면 Windows Defender에서는 해당 소프트웨어가 사용자의 개인 정보나 컴퓨터에 끼칠 수 있는 위험에 대한 경고를 표시하지 않습니다. 따라서 소프트웨어와 소프트웨어 공급자를 신뢰하는 경우에만 소프트웨어를 허용 목록에 추가해야 합니다.  

### <a name="how-to-remove-potentially-harmful-software"></a>잠재적으로 위험한 소프트웨어를 제거하는 방법

Windows Defender에서 검색된 사용자 동의 없이 설치되거나 컴퓨터에 손상을 줄 수 있는 모든 항목을 빠르고 쉽게 제거하려면 **컴퓨터 치료** 옵션을 사용합니다.  

1.  잠재적인 위협 요소를 검색한 후에 알림 영역에 표시하는 알림 메시지가 나타나면 **컴퓨터 치료**를 클릭합니다.  

2.  Windows Defender에서는 잠재적인 위협 요소를 제거한 다음 컴퓨터 치료를 마쳤을 때 사용자에게 이를 알려 줍니다.  

3.  검색된 위협 요소에 대한 자세한 내용을 보려면 **기록** 탭을 클릭하고 **검색된 모든 항목**을 선택합니다.  

4.  검색된 항목이 모두 표시되지 않으면 **자세한 정보 보기**를 클릭합니다. 관리자 암호 또는 확인을 요청하는 메시지가 표시되면 암호를 입력하거나 해당 작업을 확인합니다.

> [!NOTE]  
>  컴퓨터 치료 중 Windows Defender에서는 가능한 한 파일 전체가 아닌 파일의 감염된 부분만 제거합니다.  

##  <a name="what-is-a-virus"></a>바이러스란 무엇인가요?  
 컴퓨터 바이러스는 컴퓨터 작업을 방해하거나, 데이터를 기록, 손상 또는 삭제하거나, 인터넷 전체의 다른 컴퓨터를 감염시키도록 의도적으로 만들어진 소프트웨어 프로그램입니다. 바이러스는 속도를 저하시키고 다른 문제가 발생되도록 합니다.  

##  <a name="what-is-spyware"></a>스파이웨어란 무엇인가요?  
 스파이웨어는 사용자의 동의를 구하거나 적절한 알림 또는 제어 권한을 제공하지 않고 컴퓨터에서 자체적으로 설치되거나 실행될 수 있는 소프트웨어입니다. 스파이웨어는 컴퓨터를 감염시킨 후에 증상을 나타내지 않을 수 있지만 많은 악성 또는 사용자 동의 없이 설치된 프로그램은 컴퓨터 실행 방식에 영향을 줄 수 있습니다. 예를 들어 스파이웨어는 사용자의 온라인 동작을 모니터링하거나 사용자에 대한 정보(사용자를 식별할 수 있는 정보 또는 기타 중요한 정보 포함)를 수집하거나, 컴퓨터의 설정을 변경하거나, 컴퓨터 작동을 느리게 만들 수 있습니다.  

##  <a name="whats-the-difference-between-viruses-spyware-and-other-potentially-harmful-software"></a>바이러스, 스파이웨어 및 기타 잠재적으로 위험한 소프트웨어 간의 차이는 무엇인가요?  
 바이러스와 스파이웨어 모두 사용자 모르게 컴퓨터에 설치되며, 침투적이고 파괴적인 잠재성을 가지고 있습니다. 또한 컴퓨터에 대한 정보를 캡처하고 해당 정보를 손상시키거나 삭제할 수 있습니다. 둘 다 컴퓨터의 성능에 부정적인 영향을 미칠 수 있습니다.  

 바이러스와 스파이웨어 간의 주요 차이점은 컴퓨터에서 작동하는 방식입니다. 생물과도 같은 바이러스는 컴퓨터를 감염시키고 복제된 다음 가능한 많은 다른 컴퓨터에 확산되려고 합니다. 그러나 스파이웨어는 스파이와 같습니다. 컴퓨터"로 이동"하고 가능한 한 오래 머물면서 컴퓨터에 대한 귀중한 정보를 외부 소스로 보내려고 합니다.  

##  <a name="where-do-viruses-spyware-and-other-potentially-unwanted-software-come-from"></a>바이러스, 스파이웨어 및 기타 사용자 동의 없이 설치된 소프트웨어의 출처는 무엇인가요?  
 바이러스와 같은 원치 않는 소프트웨어는 웹 사이트 또는 다운로드하거나 CD, DVD, 외부 하드 디스크 또는 디바이스를 사용하여 사용자가 설치하는 프로그램에 의해 설치될 수 있습니다. 스파이웨어는 파일 공유, 화면 보호기 또는 검색 도구 모음 등의 무료 소프트웨어를 통해 가장 일반적으로 설치됩니다.  

##  <a name="can-i-get-malicious-software-without-knowing-it"></a>자기도 모르는 사이에 악성 소프트웨어를 받을 수 있나요?  
 예, 일부 악성 소프트웨어는 웹 페이지의 포함된 스크립트 또는 프로그램을 통해 웹 사이트에서 설치될 수 있습니다. 일부 악성 소프트웨어는 설치를 위해 사용자의 도움을 필요로 합니다. 이 소프트웨어는 사용자가 다운로드된 파일을 동의해야 하는 웹 팝업 또는 무료 소프트웨어를 사용합니다. 그러나 Microsoft Windows®를 최신 상태로 유지하고 보안 설정을 줄이지 않는 경우 감염의 가능성을 최소화할 수 있습니다.  

##  <a name="why-is-it-important-to-review-license-agreements-before-installing-software"></a>소프트웨어를 설치하기 전에 사용권 계약을 검토하는 것이 중요한 이유는 무엇인가요?  
 웹 사이트를 방문할 때는 사이트가 제공하는 어떤 것도 다운로드하도록 자동으로 동의하지 않도록 합니다. 파일 공유 프로그램 또는 화면 보호기와 같은 무료 소프트웨어를 다운로드하는 경우 사용권 계약을 신중하게 읽으세요. 회사의 광고 및 팝업을 동의해야 한다거나 소프트웨어가 소프트웨어 게시자에게 특정 정보를 다시 보낸다고 설명하는 구절이 있는지 찾으세요.  

##  <a name="whats-the-difference-between-endpoint-protection-and-windows-defender"></a>Endpoint Protection 및 Windows Defender의 차이는 무엇인가요?  
 Endpoint Protection은 맬웨어 방지 소프트웨어입니다. 즉, 바이러스, 스파이웨어 및 기타 사용자 동의 없이 설치되는 소프트웨어를 비롯한 광범위한 악성 소프트웨어로부터 컴퓨터를 보호하는 데 도움을 주도록 고안되었습니다. Windows 운영 체제와 함께 자동으로 설치되는 Windows Defender는 스파이웨어를 감지하고 중지하는 소프트웨어입니다.  

##  <a name="why-doesnt-windows-defender-detect-cookies"></a>Windows Defender가 쿠키를 검색하지 않는 이유는 무엇인가요?  
 쿠키는 웹 사이트에서 사용자에 대한 정보와 기본 설정을 저장하기 위해 컴퓨터에 추가하는 작은 텍스트 파일입니다. 웹 사이트는 쿠키를 사용하여 개인화된 환경을 제공하고, 웹 사이트 사용에 대한 정보를 수집합니다. Windows Defender는 쿠키를 사용자의 개인 정보 또는 사용자 컴퓨터 보안에 대한 위협 요인으로 간주하지 않으므로 검색하지 않습니다. 대부분의 인터넷 브라우저 프로그램에서는 쿠키를 차단할 수 있습니다.  

##  <a name="how-can-i-prevent-malware"></a>맬웨어를 방지하려면 어떻게 해야 하나요?  
 오늘날 컴퓨터 사용자가 직면하는 가장 심각한 문제 중 두 가지는 바이러스와 스파이웨어입니다. 두 경우 모두 문제가 될 수 있지만 간단한 계획만으로도 쉽게 방어할 수 있습니다.  

-   컴퓨터의 소프트웨어를 최신 상태로 유지하고 모든 패치를 설치합니다. 운영 체제를 정기적으로 업데이트합니다.  

-   바이러스 백신 및 스파이웨어 방지 소프트웨어인 Windows Defender는 잠재적인 위협에 대해 최신 업데이트를 사용합니다(바이러스 및 스파이웨어 정의를 최신 상태로 유지하려면 어떻게 해야 하나요? 참조). 또한 항상 최신 버전의 Windows Defender를 사용해야 합니다.  

-   신뢰할 수 있는 원본의 업데이트만 다운로드합니다. Windows 운영 체제의 경우 항상 [Microsoft 업데이트](https://go.microsoft.com/fwlink/?LinkID=96304)(https://go.microsoft.com/fwlink/?LinkID=96304) 로 이동하고, 다른 소프트웨어의 경우에는 항상 해당 소프트웨어를 생성한 회사 또는 사람의 합법적인 웹 사이트를 사용하세요.  

-   출처가 불확실한 첨부 파일이 있는 전자 메일을 받는 경우 즉시 삭제해야 합니다. 알 수 없는 원본의 애플리케이션이나 파일을 다운로드하지 말고 다른 사용자와 파일을 주고받는 경우 특히 주의하세요.  

-   방화벽을 설치하고 사용합니다. Windows 방화벽을 사용하는 것이 좋습니다.  

##  <a name="what-are-virus-and-spyware-definitions"></a>바이러스 및 스파이웨어 정의란?  
 Windows Defender 또는 Endpoint Protection을 사용하는 경우 최신 바이러스 및 스파이웨어 정의를 보유해야 합니다. 정의란 잠재적인 소프트웨어 위협에 대한 백과사전과 같은 파일로, 점점 크기가 커질 수 있습니다. Windows Defender 또는 Endpoint Protection에서는 정의를 사용하여 검색된 소프트웨어가 바이러스, 스파이웨어 또는 기타 사용자 동의 없이 설치된 소프트웨어인지 확인한 다음 잠재적인 위험에 대해 경고합니다. 사용자 정의를 최신 상태로 유지하기 위해 Windows Defender 또는 Endpoint Protection은 Microsoft 업데이트와 함께 작동하여 새 정의를 자동으로 설치합니다. 검색하기 전에 업데이트된 정의를 온라인에서 확인하도록 Windows Defender 또는 Endpoint Protection을 설정할 수도 있습니다.  

##  <a name="how-do-i-keep-virus-and-spyware-definitions-up-to-date"></a>바이러스 및 스파이웨어 정의를 최신 상태로 유지하려면 어떻게 해야 하나요?  
 바이러스 및 스파이웨어 정의는 바이러스, 스파이웨어 및 기타 사용자 동의 없이 설치된 소프트웨어를 포함하여 알려진 악성 소프트웨어에 대한 백과 사전처럼 작동하는 파일입니다. 악성 소프트웨어는 지속적으로 발전되고 있으므로 Windows Defender 또는 Endpoint Protection은 최신 정의를 활용하여 컴퓨터에서 설치되거나, 실행되거나, 설정을 변경하려고 하는 소프트웨어가 바이러스, 스파이웨어 또는 기타 사용자 동의 없이 설치된 소프트웨어인지 확인합니다.  

### <a name="to-automatically-check-for-new-definitions-before-scheduled-scans-recommended"></a>예약된 검색 전에 새 정의를 자동으로 확인하려면(권장)  

1.  알림 영역에서 아이콘을 클릭하거나 **시작** 메뉴에서 실행하여 Windows Defender 또는 Endpoint Protection 클라이언트를 엽니다.  

2.  **설정**을 클릭하고 **예약 검사**를 클릭합니다.  

3.  **예약 검사를 실행하기 전에 최신 바이러스 및 스파이웨어 정의 파일 확인** 확인란을 선택한 다음 **변경 내용 저장**을 클릭합니다. 관리자 암호 또는 확인을 요청하는 메시지가 표시되면 암호를 입력하거나 해당 작업을 확인합니다.  

### <a name="to-check-for-new-definitions-manually"></a>새 정의를 수동으로 확인하려면

 Windows Defender 또는 Endpoint Protection은 컴퓨터의 바이러스 및 스파이웨어 정의를 자동으로 업데이트합니다. 정의가 7일 넘게 업데이트되지 않은 경우(예: 1주일 동안 컴퓨터를 켜지 않음) Windows Defender 또는 Endpoint Protection은 정의가 이전 버전임을 알립니다.  

1.  알림 영역에서 아이콘을 클릭하거나 **시작** 메뉴에서 실행하여 Windows Defender 또는 Endpoint Protection 클라이언트를 엽니다.  

2.  새 정의를 수동으로 확인하려면 **업데이트** 탭을 클릭한 다음 **정의 업데이트**를 클릭합니다.  

##  <a name="how-do-i-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Windows Defender 또는 Endpoint Protection에 의해 격리된 항목을 제거 또는 복원하려면 어떻게 하나요?  

 Windows Defender 또는 Endpoint Protection에서는 소프트웨어를 격리할 때 소프트웨어를 컴퓨터의 다른 위치로 이동한 다음 사용자가 복원하거나 컴퓨터에서 제거하도록 선택할 때까지 이 소프트웨어가 실행되지 않도록 합니다.  

 이 절차에 설명된 모든 단계에서 관리자 암호 또는 확인을 요청하는 메시지가 표시되면 암호를 입력하거나 해당 작업을 확인합니다.  

###  <a name="to-remove-or-restore-items-quarantined-by-windows-defender-or-endpoint-protection"></a>Windows Defender 또는 Endpoint Protection에 의해 격리된 항목을 제거 또는 복원하려면


1.  **기록** 탭을 클릭하고 **격리된 항목**을 선택한 후 **격리된 항목** 옵션을 선택합니다.  

2.  **세부 정보 보기** 를 클릭하여 모든 항목을 볼 수 있습니다.  

3.  각 항목을 검토하고 각 항목에 대해 **제거** 또는 **복원**을 클릭합니다. 컴퓨터에서 격리된 모든 항목을 제거하려면 **모두 제거**를 클릭합니다.  

##  <a name="what-is-real-time-protection"></a>실시간 보호란?  

 실시간 보호는 Windows Defender에서 항상 컴퓨터를 모니터링하고 바이러스 및 스파이웨어 같은 잠재적인 위협 요소가 자체적으로 설치되거나 컴퓨터에서 실행되려고 할 때 경고할 수 있습니다. 이 기능은 Windows Defender가 컴퓨터를 보호하는 방식의 중요한 요소이기 때문에 실시간 보호가 항상 켜져 있는지 확인해야 합니다. 실시간 보호가 해제되면 Windows Defender는 알림을 표시하고 컴퓨터의 상태를 **위험**으로 변경합니다.  

 실시간 보호가 위협 또는 잠재적인 위협을 감지할 때마다 Windows Defender는 알림을 표시합니다. 이제 다음 옵션 중에서 선택할 수 있습니다.  

- **컴퓨터 정리** 를 클릭하여 검색된 항목을 제거합니다. Windows Defender는 컴퓨터에서 해당 항목을 자동으로 제거합니다.  

- **세부 정보 표시** 링크를 클릭하여 잠재적인 위협 세부 정보 창을 표시하고 검색된 항목에 적용할 작업을 선택합니다.  

  Windows Defender에서 모니터링하게 하려는 소프트웨어 및 설정을 선택할 수 있지만 실시간 보호를 켜고 모든 실시간 보호 옵션을 사용하도록 설정하는 것이 좋습니다. 다음 표에서는 사용 가능한 옵션에 대해 설명합니다.  

|||  
|-|-|  
|**실시간 보호 옵션**|**용도**|  
|모든 다운로드 검색|이 옵션은 파일 및 ActiveX ® 컨트롤 및 소프트웨어 설치 프로그램과 같이 Windows Internet Explorer 및 Microsoft Outlook® Express를 통해 자동으로 다운로드되는 파일을 비롯하여 다운로드 파일 및 프로그램을 모니터링합니다. 이러한 파일은 브라우저 자체에서 다운로드, 설치 또는 실행될 수 있습니다. 바이러스, 스파이웨어 및 기타 사용자 동의 없이 설치되는 소프트웨어를 비롯한 악성 소프트웨어가 이러한 파일에 포함되어 사용자 모르게 설치될 수 있습니다.<br /><br /> 실시간 보호 옵션을 사용하면 Windows Defender는 항상 컴퓨터를 모니터링하고 다운로드되었을 수 있는 악의적인 파일 또는 프로그램을 확인합니다. 이 모니터링 기능은 사용자가 다운로드하려는 파일 또는 프로그램을 확인하도록 요구하여 Windows Defender로 인해 탐색 또는 전자 메일 환경이 느려지지 않도록 합니다.|  
|컴퓨터에서 파일 및 프로그램 활동 모니터|이 옵션은 파일 및 프로그램이 컴퓨터에서 실행되기 시작하면 모니터링을 수행하고 수행할 작업 및 수행된 작업을 사용자에게 알립니다. 악성 소프트웨어는 사용자가 설치한 프로그램의 취약점을 악용하여 사용자 모르게 악성 또는 동의 없이 설치된 소프트웨어를 실행할 수 있으므로 이러한 알림은 매우 중요합니다. 예를 들어 스파이웨어는 사용자가 자주 사용자는 프로그램을 시작하면 백그라운드에서 자체적으로 실행될 수 있습니다. Windows Defender는 프로그램을 모니터링하고 의심스러운 활동이 감지되면 경고합니다.|  
|동작 모니터링 사용|이 옵션은 기존의 바이러스 백신 검색 방법으로 검색될 수 없는 의심스러운 패턴의 동작 모음을 모니터링합니다.|  
|네트워크 검사 시스템 사용|이 옵션은 알려진 취약점의 "제로 데이" 악용으로부터 컴퓨터를 보호하여, 취약점이 발견되는 시점과 업데이트가 적용되는 시점 사이의 기간을 줄입니다.|  

### <a name="to-turn-off-real-time-protection"></a>실시간 보호를 해제하려면  

1.  **설정**을 클릭하고 **실시간 보호**를 클릭합니다.  

2.  해제하려는 실시간 보호 옵션을 선택 취소하고 **변경 내용 저장**을 클릭합니다. 관리자 암호 또는 확인을 요청하는 메시지가 표시되면 암호를 입력하거나 해당 작업을 확인합니다.  

##  <a name="how-do-i-know-that-windows-defender-or-endpoint-protection-is-running-on-my-computer"></a>컴퓨터에서 Windows Defender 또는 Endpoint Protection이 실행되고 있는지 확인하려면 어떻게 하나요?  

 컴퓨터에 Windows Defender를 설치한 후 기본 창을 닫고 백그라운드에서 자동 모드로 Windows Defender를 실행할 수 있습니다. Windows Defender는 사용자 컴퓨터에서 계속 실행되고 위협 요소를 모니터링하고 이러한 요인으로부터 보호하도록 도와줍니다.  

 물론 알림 영역에 알림 메시지가 표시될 때마다 Windows Defender가 실행 중이라는 것을 알 수 있습니다. 이러한 경고는 Windows Defender에서 검색된 잠재적인 위협 요소를 알려 줍니다.  

 어떤 이유로 실시간 보호를 해제했거나, 일정일 동안 바이러스 및 스파이웨어 정의를 업데이트하지 않았거나, 프로그램에 대한 업그레이드가 제공된 경우에는 다른 경고 알림이 표시될 수도 있습니다. Windows Defender에서는 컴퓨터가 검사 중임을 알 수 있도록 간단한 알림도 표시합니다.  

> [!TIP]
> 
> 알림 영역에 Windows Defender 아이콘이 표시되지 않는 경우 Windows Defender 아이콘을 포함한 숨겨진 아이콘을 표시하려면 알림 영역의 화살표를 클릭하세요.  


 아이콘 색은 다음과 같이 컴퓨터의 현재 상태에 따라 달라집니다.  

-   녹색은 컴퓨터가 "보호됨" 상태임을 나타냅니다.  

-   노란색은 컴퓨터가 "잠재적으로 보호되지 않음" 상태임을 나타냅니다.  

-   빨간색은 컴퓨터가 "위험" 상태임을 나타냅니다.  

##  <a name="how-to-set-up-windows-defender-or-endpoint-protection-alerts"></a>Windows Defender 또는 Endpoint Protection 경고를 설정하는 방법  
 컴퓨터에서 Windows Defender가 실행 중이면 바이러스, 스파이웨어 또는 그 밖의 사용자 동의 없이 설치되는 소프트웨어가 검색될 때 자동으로 경고가 표시됩니다. 아직 분석되지 않은 소프트웨어를 실행할 경우 Windows Defender에서 경고를 표시하도록 설정하고, 컴퓨터의 설정을 변경하려고 하는 소프트웨어가 있을 때 경고를 표시하도록 선택할 수도 있습니다.  

### <a name="to-set-up-alerts"></a>경고를 설정하려면  

1.  **설정**을 클릭하고 **실시간 보호**를 클릭합니다.  

2.  **실시간 보호 설정(권장)** 확인란이 선택되어 있는지 확인합니다.  

3.  실행할 실시간 보호 옵션 옆의 확인란을 선택하고 **변경 내용 저장**을 클릭합니다. 관리자 암호 또는 확인을 요청하는 메시지가 표시되면 암호를 입력하거나 해당 작업을 확인합니다.  

### <a name="see-also"></a>참고 항목  
 [Windows Defender 또는 Endpoint Protection 클라이언트 문제 해결](troubleshoot-endpoint-client.md)   

 [Endpoint Protection 클라이언트 도움말](endpoint-protection-client-help.md)
