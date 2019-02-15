---
title: 인증서 프로필 모니터링
titleSuffix: Configuration Manager
description: System Center Configuration Manager 인증서 프로필의 준수 상태를 모니터링하는 방법을 알아봅니다.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 98feaa06-64b1-4e86-a122-93017c97cd4f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 86485a1a54acb122e1b56118de9e72d840e01809
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56137663"
---
# <a name="how-to-monitor-certificate-profiles-in-system-center-configuration-manager"></a>System Center Configuration Manager에서 인증서 프로필을 모니터링하는 방법

*적용 대상: System Center Configuration Manager(현재 분기)*


##  <a name="view-compliance-results-in-the-configuration-manager-console"></a>Configuration Manager 콘솔에서 준수 결과 보기  

SCEP 인증서 준수 여부를 모니터링하려면 [보고서](#view-compliance-results-by-using-reports)를 사용하세요. 

1. Configuration Manager 콘솔에서 **모니터링**>  **배포**를 선택합니다.  

2. 원하는 인증서 프로필 배포를 선택합니다.  

3. 기본 페이지에서 요약 인증서 준수 정보를 검토합니다. 자세한 내용은 인증서 프로필을 선택한 후 **홈** 탭의 **배포** 그룹에서 **상태 보기**를 선택하여 **배포 상태** 페이지를 엽니다.  

    **배포 상태** 페이지에는 다음 탭이 있습니다.  

   -   **호환성**: 영향받는 자산 수에 따라 인증서 프로필의 호환성을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 인증서 프로필과 호환되는 모든 사용자가 포함됩니다. **자산 정보** 창에도 이 프로필과 호환되는 사용자가 표시됩니다. 목록에서 추가 정보를 확인할 사용자를 두 번 클릭합니다.  

       > [!IMPORTANT]  
       >  인증서 프로필이 클라이언트 디바이스에 적용되지 않는 경우에는 평가되지 않습니다. 그러나 해당 프로필은 호환 상태로 반환됩니다.  

   -   **오류**: 영향받는 자산 수에 따라 선택한 인증서 프로필 배포에 대한 모든 오류 목록을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 이 프로필과 관련하여 오류가 발생한 모든 사용자가 포함됩니다. 사용자를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자가 표시됩니다. 목록에서 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

   -   **비준수**: 영향받는 자산 수에 따라 인증서 프로필 내에 있는 모든 비준수 규칙 목록을 표시합니다. 규칙을 두 번 클릭하여 **자산 및 준수** 작업 영역의 **사용자** 노드 아래에 임시 노드를 만들 수 있습니다. 이 노드에는 이 프로필과 호환되지 않는 모든 사용자가 포함됩니다. 사용자를 선택하면 **자산 정보** 창에 선택한 문제의 영향을 받는 사용자가 표시됩니다. 목록에서 문제에 대한 추가 정보를 표시할 사용자를 두 번 클릭합니다.  

   -   **알 수 없음**: 선택한 인증서 프로필 배포의 호환성과 디바이스의 현재 클라이언트 상태를 보고하지 않은 모든 사용자 목록을 표시합니다.  

4. **배포 상태** 페이지에서 배포된 인증서 프로필의 준수에 대한 자세한 정보를 검토할 수 있습니다. 이 정보를 나중에 빠르게 다시 찾을 수 있도록 임시 노드가 **배포** 노드 아래에 만들어집니다.  

    인증서의 등록 상태가 숫자로 표시됩니다. 다음 표를 사용하면 각 숫자의 의미를 이해할 수 있습니다.  


   | 등록 상태 |                                                                                                                   설명                                                                                                                   |
   |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |    0x00000001     |                                                                                         등록에 성공했으며 인증서가 발급되었습니다.                                                                                          |
   |    0x00000002     |                                                                    요청이 제출되었는데 등록이 보류 중이거나 요청이 대역 외에서 발급되었습니다.                                                                    |
   |    0x00000004     |                                                                                                          등록이 지연되고 있습니다.                                                                                                           |
   |    0x00000010     |                                                                                                               오류가 발생했습니다.                                                                                                                |
   |    0x00000020     |                                                                                                        등록 상태를 알 수 없습니다.                                                                                                        |
   |    0x00000040     | 상태 정보를 건너뛰었습니다. 이러한 현상은 하이퍼링크 "<http://msdn.microsoft.com/windows/ms721572>" \l "_security_certification_authority_gly" 인증 기관이 유효하지 않거나 모니터링용으로 선택되지 않은 경우 발생할 수 있습니다. |
   |    0x00000100     |                                                                                                           등록이 거부되었습니다.                                                                                                           |

##  <a name="view-compliance-results-by-using-reports"></a>보고서를 사용하여 준수 결과 보기

 System Center Configuration Manager의 준수 설정에는 인증서 프로필에 대한 정보를 모니터링하는 데 사용할 수 있는 기본 제공 보고서가 포함됩니다. 이러한 보고서에는 **호환 및 설정 관리**라는 보고서 범주가 있습니다.  

> [!IMPORTANT]  
>  호환성 설정 보고서에서 **디바이스 필터** 및 **사용자 필터** 매개 변수를 사용할 경우 와일드카드(%) 문자를 사용해야 합니다.  

SCEP 인증서 준수 여부를 모니터링하려면 **회사 리소스 액세스** 보고서 노드에 있는 다음과 같은 인증서 보고서를 사용하세요.  

 -   인증서 발급 기록  
 -   만료 날짜에 가까운 인증서와 자산 목록  
 -   인증서 발급 상태별 자산 목록  



 System Center Configuration Manager에서 보고를 구성하는 방법에 대한 자세한 내용은 [System Center Configuration Manager의 보고](../../core/servers/manage/reporting.md)를 참조하세요.  
