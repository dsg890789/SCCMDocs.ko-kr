---
title: Windows 10에 대 한 구성 항목 만들기
titleSuffix: Configuration Manager
description: Windows 10 구성 항목을 사용하여 구성 관리자 클라이언트에서 관리되는 Windows 10 컴퓨터에 대한 설정을 관리합니다.
ms.date: 01/06/2020
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 14226fbe-dd07-4432-910b-130790624a4e
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 8050850582ca8e98e153966155b693075bd35949
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75816550"
---
# <a name="create-configuration-items-for-windows-10-devices"></a>Windows 10 장치에 대 한 구성 항목 만들기

System Center Configuration Manager **Windows 10** 구성 항목을 사용하여 구성 관리자 클라이언트에서 관리되는 Windows 10 컴퓨터에 대한 설정을 관리할 수 있습니다.  
  
> [!IMPORTANT]  
>  이 릴리스에서는 **Windows 10** 형식의 구성 항목의 일부로 **암호** 설정을 만든 경우 (Configuration Manager 클라이언트를 사용 하 여 관리 되는 장치의 경우) 다음 문제에 주의 해야 합니다. 이 설정이 아직 존재 하지 않거나 Windows 10 장치에서 구성 되지 않은 경우 호환 되는 것으로 잘못 평가 됩니다.  
>   
>  해결 방법으로, 이러한 디바이스에 대한 설정을 만들 때 구성 항목 만들기 마법사의 설정 페이지에서 **비규격 설정 재구성** 이 선택되어 있는지 확인합니다. 또한 암호 설정을 포함하는 Windows 10 구성 항목이 포함된 구성 기준을 배포할 경우 **지원되는 경우 비규격 규칙 재구성**을 선택합니다. 이렇게 하려면 구성 기준 배포 대화 상자에서이 옵션을 선택 합니다. 이 해결 방법을 사용하면 설정이 모니터링되고 비규격 상태로 확인되는 경우 재구성됩니다. 재구성 후에는 **오류**로 보고할 문제가 발생하지 않는 경우 설정이 **규격**으로 올바르게 보고됩니다.  
  
### <a name="to-create-a-windows-10-configuration-item"></a>Windows 10 구성 항목을 만들려면  
  
1. Configuration Manager 콘솔에서 **자산 및 준수**를 선택합니다.  
  
2. **자산 및 준수** 작업 영역에서 **준수 설정**을 확장하고 **구성 항목**을 선택합니다.  
  
3. **만들기** 그룹의 **홈** 탭에서 **구성 항목 만들기**를 선택합니다.  
  
4. **구성 항목 만들기** 마법사의 **일반** 페이지에서 구성 항목의 이름 및 선택적 설명을 지정합니다.  
  
5. **만들려는 구성 항목의 유형 지정**아래에서 **Windows 10**을 선택합니다.  
  
6. Configuration Manager 콘솔에서 구성 항목을 검색하고 필터링하는 데 도움이 되는 범주를 만들고 할당하려면 **범주**를 선택합니다.  
  
7. 마법사의 **지원되는 플랫폼** 페이지에서 구성 항목을 평가할 특정 Windows 10 플랫폼을 선택합니다.  
  
8. 마법사의 **디바이스 설정** 페이지에서 구성하려는 설정 그룹을 선택합니다. 자세한 내용은이 문서에서 [Windows 10 구성 항목 설정 참조](#BKMK_Ref) 를 참조 하세요. **다음**을 선택합니다.  
  
   > [!TIP]  
   >  원하는 설정이 나열되지 않은 경우 **기본 설정 그룹에 없는 추가 설정 구성 확인란**을 선택합니다.  
  
9. 각 설정 페이지에서 필요한 설정과 디바이스에서 준수되지 않는 경우 수정 여부(지원되는 경우)를 구성합니다.  
  
10. 각 설정 그룹에 대해 구성 항목이 비규격인 것으로 확인되는 경우 보고될 심각성을 구성할 수도 있습니다.  
  
    -   **없음**: 이 호환성 규칙에 실패한 디바이스가 Configuration Manager 보고서에 오류 심각도를 보고하지 않습니다.  
  
    -   **정보**: 이 준수 규칙을 충족하지 않는 디바이스가 Configuration Manager 보고서에 **정보** 오류 심각도를 보고합니다.  
  
    -   **경고**: 이 준수 규칙을 충족하지 않는 디바이스가 Configuration Manager 보고서에 **경고** 오류 심각도를 보고합니다.  
  
    -   **위험**: 이 준수 규칙을 충족하지 않는 디바이스가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다.  
  
    -   **위험(이벤트 포함)** : 이 준수 규칙을 충족하지 않는 디바이스가 Configuration Manager 보고서에 **위험** 오류 심각도를 보고합니다. 또한 이 심각도 수준은 애플리케이션 이벤트 로그에 Windows 이벤트로 기록됩니다.  
  
11. 마법사의 **플랫폼 적용 여부 가능성** 페이지에서 이전에 선택한 지원되는 플랫폼과 호환되지 않는 설정을 검토합니다. 뒤로 돌아가서 이러한 설정을 제거하거나 계속할 수 있습니다.  
  
    > [!TIP]  
    >  지원되지 않는 설정은 준수 여부에 대해 평가되지 않습니다.  
  
12. 마법사를 완료합니다.  
  
    **자산 및 준수** 작업 영역의 **구성 항목** 노드에서 새 구성 항목을 볼 수 있습니다.  
  
## <a name="BKMK_Ref"></a> Windows 10 configuration item settings reference  
  
### <a name="password"></a>암호  
  
|Setting|세부 정보|  
|-------------|-------------|  
|**디바이스에 암호 설정 필요**|지원되는 디바이스에는 암호가 필요합니다.|  
|**최소 암호 길이(문자 수)**|암호의 최소 문자 길이입니다.|  
|**다음 기간 후 암호 만료(일)**|암호를 변경해야 할 때까지의 기간(일)입니다.|  
|**저장한 암호 수**|이전 암호를 다시 사용하지 못하도록 설정합니다.|  
|**다음 로그온 실패 횟수 후 디바이스 초기화**|이 횟수만큼 로그인에 실패하면 디바이스를 초기화합니다.|  
|**다음 유휴 시간 후 디바이스 잠그기**|디바이스가 자동으로 잠기기 전에 몇 분 동안 비활성 상태로 있어야 하는지 지정합니다.|  
|**암호 복잡도**|'1234' 등의 PIN을 지정할 수 있는지 아니면 강력한 암호를 입력해야 하는지를 선택합니다.|
|**암호에 필요한 복합 문자 집합 수**|**강력한** 암호를 선택한 경우 이 설정을 사용하여 필요한 복합 문자 집합 수를 구성합니다. 강력한 암호의 경우 이 설정을 **3** 이상으로 설정해야 하며, 문자와 숫자가 둘 다 필요합니다. **(%$** 등의 특수 문자를 추가로 요구하는 암호를 적용하려면 **4**를 선택합니다.<br>(Windows 10만 해당)  |
  
###  <a name="device"></a>디바이스  
  
|설정 이름|세부 정보|  
|------------------|-------------|  
|**Bluetooth**|디바이스에서 Bluetooth 기능을 사용할 수 있습니다.|  
  
### <a name="cloud"></a>클라우드  
  
|설정 이름|세부 정보|  
|------------------|-------------|  
|**설정 동기화**|디바이스 간에 설정을 동기화할 수 있습니다.|  
|**자격 증명 동기화**|디바이스 간에 자격 증명을 동기화할 수 있습니다.|  
|**유료 네트워크에서 설정 동기화**|인터넷 연결이 유료일 때 설정을 동기화할 수 있습니다.|  
  
### <a name="roaming"></a>로밍  
  
|설정 이름|세부 정보|  
|------------------|-------------|  
|**데이터 로밍**|데이터 액세스 시 네트워크 간 로밍이 가능합니다.|  
  
### <a name="encryption"></a>암호화  
  
|설정 이름|세부 정보|  
|------------------|-------------|  
|**디바이스에 파일 암호화**|디바이스의 파일을 암호화해야 합니다.|  
  
### <a name="system-security"></a>시스템 보안  
  
|설정 이름|세부 정보|  
|------------------|-------------|  
|**사용자 계정 컨트롤**|디바이스에서 Windows 사용자 계정 컨트롤이 작동하는 방법을 구성합니다.<br />예를 들어 사용하지 않도록 설정하거나 알리는 수준을 설정할 수 있습니다.|  
|**네트워크 방화벽**|Windows 방화벽을 사용하거나 사용하지 않도록 설정합니다.|  
|**SmartScreen**|Windows SmartScreen을 사용 하거나 사용 하지 않도록 설정 합니다.|  
|**바이러스 방지**|바이러스 백신 소프트웨어를 설치 및 구성해야 합니다.|  
|**바이러스 방지 서명이 최신임**|디바이스에서 바이러스 백신 소프트웨어에 대한 서명 파일이 최신이어야 합니다.|  
  
### <a name="windows-information-protection"></a>Windows Information Protection

기업에서 직원 소유 디바이스가 증가하면서 메일, 소셜 미디어 및 퍼블릭 클라우드와 같은 앱 및 서비스를 통해 실수로 데이터가 유출될 위험이 높아지고 있습니다. 이러한 기능은 조직의 제어를 벗어납니다. 직원의 경우를 예로 들면 다음과 같습니다.

- 개인 전자 메일 계정에서 최신 엔지니어링 사진을 보냅니다.
- 제품 정보를 복사 하 여 트 윗에 붙여넣습니다.
- 진행 중인 판매 보고서를 해당 공용 클라우드 저장소에 저장 합니다.

WIP(Windows Information Protection, 이전 엔터프라이즈 데이터 보호)는 직원 환경을 방해하지 않으면서 이러한 잠재적인 데이터 유출로부터 보호하는 데 도움이 됩니다. 또한 WIP는 회사 소유 디바이스 및 직원이 회사로 가져오는 개인 디바이스에서 엔터프라이즈 앱 및 데이터가 실수로 데이터를 누출되지 않게 하는 데도 유용합니다. WIP는 사용자 환경 또는 다른 앱을 변경할 필요가 없습니다.

Windows Information Protection 구성 항목 Configuration Manager 다음을 관리 합니다.

- WIP로 보호 되는 앱 목록
- 엔터프라이즈 네트워크 위치
- 보호 수준
- 암호화 설정
  

Configuration Manager를 사용 하 여 WIP를 구성 하는 방법에 대 한 자세한 내용은 다음을 참조 하세요.
- [WIP(Windows Information Protection)를 사용하여 엔터프라이즈 데이터 보호](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/protect-enterprise-data-using-wip)
- [System Center Configuration Manager를 사용하여 WIP(Windows Information Protection) 정책 만들기 및 배포](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/create-wip-policy-using-sccm#related-topics)
- [Windows Information Protection를 사용 하는 동안 발생 하는 제한 사항 (WIP)](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/limitations-with-wip)

## <a name="see-also"></a>참고 항목  
[Configuration Manager 클라이언트로 관리되는 디바이스의 구성 항목](../../compliance/deploy-use/create-configuration-items.md)
