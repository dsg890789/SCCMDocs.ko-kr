---
title: 배포 모니터링 도구
titleSuffix: Configuration Manager
description: 배포 모니터링 도구를 사용하여 Configuration Manager 클라이언트에서 소프트웨어 배포 문제를 해결합니다.
ms.date: 07/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9edc214f-f405-456d-80df-8adcc2a5428d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 67a052fffcaf6ad105f417649aa9f3826922ce80
ms.sourcegitcommit: 1826664216c61691292ea2a79e836b11e1e8a118
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/31/2018
ms.locfileid: "39385894"
---
# <a name="deployment-monitoring-tool"></a>배포 모니터링 도구

*적용 대상: System Center Configuration Manager(현재 분기)*

배포 모니터링 도구는 [Configuration Manager 도구](/sccm/core/support/tools)에 속합니다. 애플리케이션, 소프트웨어 업데이트 및 Configuration Manager 클라이언트에서 구성 기준 배포의 문제 해결을 지원하기 위해 설계된 그래픽 사용자 인터페이스입니다. 도구는 클라이언트에서 상태를 변경하지 않으므로 읽기 전용입니다. 이를 안전하게 사용하여 일반적인 배포 시나리오를 진단할 수 있습니다.


## <a name="features"></a>기능

- 관리자 권한으로 실행하여 로컬 클라이언트에서 배포 문제를 해결합니다.  

- 원격 클라이언트에서 배포 문제를 해결합니다. 도구를 시작하고 관리자 권한으로 원격 머신에 연결합니다.  

- 도구에서 수집된 모든 데이터를 XML로 내보냅니다. XML 파일을 다른 사용자와 공유하고, 배포 문제 해결에 대해 이야기하기 위해 공용 플랫폼으로 사용합니다.  

- 이전에 내보낸 데이터를 다른 머신으로 가져오고, 이를 사용하여 오프라인 모드에서 도구를 실행합니다.   


## <a name="usage"></a>용도

배포 모니터링 도구는 그래픽 사용자 인터페이스만을 지원합니다. 이 도구를 시작하려면 관리자 권한으로 **DeploymentMonitoringTool.exe**를 실행합니다. 다음 세 가지 보기가 있습니다.  

- **클라이언트 속성**: 장치 및 Configuration Manager 클라이언트에 대한 유용한 특성 목록입니다. 이 보기는 기본값입니다.   

- **배포**: 현재 대상으로 지정된 모든 배포를 봅니다. 결과 창에서 배포를 선택하여 세부 정보 창에서 자세한 정보를 봅니다.  

- **모든 업데이트**: 모든 소프트웨어 업데이트 및 해당 상태를 봅니다.  

모든 보기에서 데이터를 복사하려면 셀을 선택하고, **CTRL** + **C** 키를 누릅니다.


### <a name="actions-menu"></a>작업 메뉴

**작업** 메뉴에서는 다음 작업을 사용할 수 있습니다.  

- **원격 머신에 연결**: 연결할 컴퓨터를 선택합니다. 사용자 이름 및 암호를 지정하지 않는 경우 현재 자격 증명을 사용합니다. **저장**을 클릭하여 원격 컴퓨터에 연결합니다.  

- **데이터 내보내기**: 데이터를 작성할 파일을 선택하고, **저장**을 클릭합니다. 다른 컴퓨터에서 원격 문제 해결을 위해 내보낸 XML 파일을 사용합니다.  

- **데이터 가져오기**: 도구로 가져올 파일을 선택합니다.  

- **로그 보기**: 보기에 따라 연결된 로그 파일을 엽니다.  
    - 클라이언트 속성: `\\<hostname>\c$\Windows\CCM\Logs\PolicyAgent.log`
    - 배포: `\\<hostname>\c$\Windows\CCM\Logs\PolicyAgent.log`
    - 모든 업데이트: `C:\Windows\WindowsUpdate.log`



## <a name="see-also"></a>참고 항목

- [응용 프로그램 배포](/sccm/apps/deploy-use/deploy-applications)
- [소프트웨어 업데이트 배포](/sccm/sum/deploy-use/deploy-software-updates)
- [구성 기준 배포](/sccm/compliance/deploy-use/deploy-configuration-baselines)
