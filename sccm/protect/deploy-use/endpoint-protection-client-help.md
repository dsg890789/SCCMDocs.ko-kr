---
title: "Endpoint Protection 클라이언트 도움말 | Microsoft 문서"
description: "위협으로부터 컴퓨터를 보다 효과적으로 보호할 수 있는 Endpoint Protection의 기능과 향상된 기능에 대해 알아봅니다."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fdcee455-22e3-451d-bcf3-e7b62792f04a
caps.latest.revision: "6"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: 212c73fcb947c3b56da6055bf47fe078301ad90d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/07/2017
---
# <a name="endpoint-protection-client-help"></a>Endpoint Protection 클라이언트 도움말

*적용 대상: System Center Configuration Manager(현재 분기)*


이 버전의 Windows Defender 또는 Endpoint Protection에는 위협으로부터 컴퓨터를 보호하는 다음과 같은 기능이 포함됩니다.  

-   **Windows 방화벽 통합.** Endpoint Protection 설치 프로그램에서 Windows 방화벽을 설정하거나 해제할 수 있습니다.  
-   **네트워크 검사 시스템:** 이 기능은 네트워크 트래픽 검사를 통해 알려진 네트워크 기반 취약성을 악용하지 못하도록 사전에 차단하여 실시간 보호를 향상시켜 줍니다.  
-   **보호 엔진.** 실시간 보호를 통해 PC에서 설치 또는 실행되지 못하도록 맬웨어를 찾아서 중지합니다. 업데이트된 엔진은 보다 우수한 성능의 향상된 검색 및 치료 기능을 제공합니다.  

Windows Defender는 Windows 10 운영 체제와 함께 제공됩니다.  이전 버전의 Windows에서 관리자는 관리 소프트웨어를 사용하여 Windows Defender 또는 Endpoint Protection을 제공할 수 있습니다.

[Windows Defender 및 Endpoint Protection에 대한 질문과 대답](endpoint-protection-client-faq.md) 목록도 확인할 수 있습니다. 문제를 해결하려면 [Windows Defender 또는 Endpoint Protection 클라이언트 문제 해결](troubleshoot-endpoint-client.md)을 참조하세요. 새로운 기능 목록을 보려면 [Windows Defender 클라이언트의 새로운 기능](https://support.microsoft.com/help/29276/windows-10-whats-new-in-windows-defender)을 참조하세요.

## <a name="windows-firewall-integration"></a>Windows 방화벽 통합  
 Windows 방화벽은 공격자나 악성 소프트웨어가 인터넷 또는 네트워크를 통해 사용자의 컴퓨터에 액세스하지 못하도록 하는 데 유용합니다. 이제 Endpoint Protection을 설치할 때 설치 마법사에서 Windows 방화벽을 설정할지 확인합니다. Windows 방화벽을 의도적으로 해제하고 있던 경우에는 확인란의 선택을 취소하여 Windows 방화벽이 설정되지 않도록 할 수 있습니다. 제어판의 시스템 및 보안 설정을 통해 언제든지 Windows 방화벽 설정을 변경할 수 있습니다.  

## <a name="network-inspection-system"></a>네트워크 검사 시스템  
 노출된 취약성에 대해 소프트웨어 공급업체에서 미처 보안 업데이트를 개발하고 배포하기도 전에 공격자에 의해 실행되는 네트워크 기반 공격이 점점 늘고 있습니다. 취약성 연구 결과에서는 처음 공격이 보고된 후 적절한 보안 업데이트가 개발 및 테스트되어 릴리스되기까지는 한 달 이상이 소요될 수 있음을 보여 주고 있습니다. 이러한 보호 공백으로 인해 많은 컴퓨터가 상당 기간 동안 공격과 악용에 취약한 상태로 있게 될 수 있습니다. 네트워크 검사 시스템에서는 실시간 보호 기능을 사용하여 취약성 노출 후 패치 배포까지 소요되는 기간을 수주에서 수시간으로 대폭 단축함으로써 네트워크 기반 공격에 대한 보호 수준을 강화합니다.  

## <a name="award-winning-protection-engine"></a>뛰어난 보호 엔진  
 Windows Defender 또는 Endpoint Protection에는 정기적으로 업데이트되는 뛰어난 보호 엔진이 포함되어 있습니다. 이 엔진은 Microsoft 맬웨어 보호 센터에 있는 맬웨어 방지 연구팀의 지원을 받아 24시간 내내 최신 맬웨어에 대한 대처 방법을 제공합니다.  

## <a name="windows-defender-settings"></a>Windows Defender 설정
Windows Defender 설정을 통해 악성 소프트웨어로부터 PC를 보호할 수 있는 설정을 적용할 수 있습니다. 관리자가 사용자 대신 일부 Windows Defender 설정을 관리할 수 있습니다. Windows Defender 설정을 사용하여 다른 설정을 관리할 수 있습니다. PC와 데이터를 보호하도록 Windows Defender 설정을 사용하도록 설정하는 것이 좋습니다.

Windows Defender 설정을 보려면 PC에서 `Windows Defender`를 검색합니다. **Windows Defender**를 열고 **설정**을 선택합니다. Windows Defender 설정은 다음을 포함합니다.
- **실시간 보호** - PC에서 설치 또는 실행되지 못하도록 맬웨어를 찾아서 중지합니다.
- **클라우드 기반 보호** - Windows Defender는 잠재적 보안 위협에 대한 정보를 Microsoft에 보냅니다.
- **자동 샘플 제출** - 맬웨어 검색을 개선하기 위해 Windows Defender가 의심스러운 파일의 샘플을 Microsoft에 보내도록 합니다.
- **제외** - Windows Defender 검사에서 특정 파일, 폴더, 파일 확장명 또는 프로세스를 제외할 수 있습니다.
- **향상된 알림** - PC 상태에 대한 정보를 제공하는 알림을 사용합니다. **해제**한 경우에도 중요한 알림을 받게 됩니다.
- **Windows Defender Offline** - Windows Defender Offline을 실행하여 악성 소프트웨어를 찾아서 제거할 수 있습니다. 이 검사를 수행하면 PC가 다시 시작되고 검사에는 15분 정도가 걸립니다.

### <a name="see-also"></a>참고 항목  
 [Endpoint Protection 클라이언트에 대한 질문과 대답](endpoint-protection-client-faq.md)   
 [Windows Defender 또는 Endpoint Protection 클라이언트 문제 해결](troubleshoot-endpoint-client.md)
