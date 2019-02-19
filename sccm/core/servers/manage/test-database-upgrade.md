---
title: 데이터베이스 업데이트 테스트
titleSuffix: Configuration Manager
description: Configuration Manager에 대한 업데이트를 설치할 때 사이트 데이터베이스의 테스트 업그레이드를 수행합니다.
ms.date: 06/13/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: abb696f3-a816-4f12-a9f1-0503a81e1976
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 6adb326a484976335d114277e095884e107f9906
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56124799"
---
# <a name="test-the-database-upgrade-when-installing-an-update"></a>업데이트를 설치할 때 데이터베이스의 테스트 업그레이드 수행

*적용 대상: System Center Configuration Manager(현재 분기)*

이 항목의 정보는 Configuration Manager의 현재 분기에 대한 콘솔 내 업데이트를 설치하기 전에 데이터베이스의 테스트 업그레이드를 실행하는 데 도움이 될 수 있습니다. 그러나 데이터베이스에 문제가 있는 것으로 의심되거나 Configuration Manager에서 명시적으로 지원하지 않는 사용자 지정으로 수정된 경우가 아니면 더 이상 테스트 업그레이드가 필요하거나 권장되는 단계는 아닙니다.

## <a name="do-i-need-to-run-a-test-upgrade"></a>테스트 업그레이드를 실행해야 할까요?
이 테스트 업그레이드는 System Center Configuration Manager에 도입된 변경 내용 때문에 더 이상 사용되지 않을 수 있습니다. 이러한 변경 내용은 프로세스를 단순화하고 프로덕션 환경을 더 빠르게 최신 버전으로 업데이트할 수 있도록 합니다. 이러한 재디자인은 고객이 각 새 업데이트를 설치할 때 위험을 줄이고 운영 오버헤드를 줄이면서 최신 상태를 유지하도록 도와주기 위해 진행되었습니다.

사이트 복구를 실행할 필요 없이 실패한 업데이트를 자동으로 롤백하는 논리를 비롯하여 업데이트가 설치되는 방식이 변경되었습니다. 이러한 변경 내용은 콘솔을 사용하여 업데이트 설치를 관리하도록 하며 [실패한 업데이트의 설치를 다시 시도](/sccm/core/servers/manage/install-in-console-updates#bkmk_retry)하는 옵션을 포함합니다.

> [!TIP]
> System Center 2012 Configuration Manager와 같은 이전 제품에서 System Center Configuration Manager로 업그레이드할 때 [테스트 데이터베이스는 권장 단계를 유지](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager#a-namebkmktesta-test-the-site-database-upgrade)합니다.

콘솔 내 업데이트를 설치할 때 사이트 데이터베이스의 업그레이드를 테스트하려면 [콘솔 내 업데이트 설치 지침](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)을 보완하는 다음 정보를 참조하세요.

## <a name="prepare-to-run-a-test-database-upgrade"></a>테스트 데이터베이스 업그레이드 실행 준비  
업데이트 1702와 같은 계층 구조에 새 업데이트를 설치하기 전에 사이트 데이터베이스의 업그레이드를 테스트할 수 있습니다.

업그레이드 테스트를 실행하려면 업데이트하려는 Configuration Manager 버전을 실행하는 사이트의 [CD.Latest 폴더](/sccm/core/servers/manage/the-cd.latest-folder)에 있는 소스 파일의 Configuration Manager 설치 프로그램을 사용합니다. 이러한 요구 사항은 1702로의 업데이트에 대한 데이터베이스 업데이트를 테스트함을 의미합니다.
-   해당 CD.Latest 폴더를 가져올 수 있는 버전 1702를 실행하는 하나 이상의 사이트가 있어야 합니다.
-   필요한 버전을 실행하는 사이트가 없으면 랩 환경에서 사이트를 설치한 후 해당 사이트를 새 버전으로 업데이트합니다. 이렇게 하면 올바른 버전의 소스 파일이 있는 CD.Latest 폴더가 만들어집니다.

SQL Server의 별도 인스턴스로 복원한 사이트 데이터베이스의 백업에 대해 업그레이드 테스트가 실행됩니다.  **testdbupgrade** 명령줄 스위치를 사용하여 **CD.Latest** 폴더에서 설치 프로그램 실행함으로써 데이터베이스의 복원된 복사본에 대해 업그레이드 테스트를 수행합니다. 테스트 업그레이드를 완료한 후 업그레이드된 데이터베이스는 삭제됩니다. Configuration Manager 사이트에서 사용할 수 없기 때문입니다.

업데이트 설치가 실패할 경우 사이트를 복구할 필요가 없습니다. 대신 콘솔 내에서 업데이트 설치를 다시 시도할 수 있습니다.

##  <a name="run-the-test-upgrade"></a>테스트 업그레이드 실행    
1. Configuration Manager 설치 프로그램과 업데이트하려는 버전을 실행하는 사이트의 **CD.Latest** 폴더에 있는 소스 파일을 사용합니다.  

2. 테스트 데이터베이스 업그레이드를 실행하는 데 사용할 SQL Server 인스턴스의 위치로 **CD.Latest** 폴더를 복사합니다.

3. 업그레이드를 테스트할 사이트 데이터베이스의 백업을 만듭니다. 다음으로 Configuration Manager 사이트를 호스트하지 않는 SQL Server의 인스턴스로 데이터베이스 복사본을 복원합니다. SQL Server 인스턴스는 사이트 데이터베이스와 동일한 버전의 SQL Server를 사용해야 합니다.  

4. 데이터베이스 복사본을 복원한 후에 업데이트하려는 버전의 소스 파일이 포함된 CD.Latest 폴더에서 **설치 프로그램**을 실행합니다. 설치 프로그램을 실행할 때 **/TESTDBUPGRADE** 명령줄 옵션을 사용합니다. 데이터베이스 사본을 호스트하는 SQL Server 인스턴스가 기본 인스턴스가 아닌 경우 명령줄 인수를 제공하여 사이트 데이터베이스 사본을 호스트하는 인스턴스를 식별합니다.   

   예를 들어 데이터베이스 이름이 *SMS_ABC*인 사이트 데이터베이스가 있다고 가정할 경우 이 사이트 데이터베이스의 사본을 인스턴스 이름이 *DBTest*인 지원되는 SQL Server 인스턴스로 복원합니다. 사이트 데이터베이스의 이 사본을 테스트하려면 다음 명령줄을 사용하십시오. **Setup.exe /TESTDBUPGRADE DBtest\CM_ABC**.  

   원본 미디어의 다음 위치에서 System Center Configuration Manager에 대한 Setup.exe를 찾을 수 있습니다. **SMSSETUP\BIN\X64**.  

5. 업그레이드 테스트를 실행하는 SQL Server 인스턴스에서 시스템 드라이브 루트에 있는 *ConfigMgrSetup.log*를 보고 진행률 및 성공 여부를 모니터링합니다.  

    테스트 업그레이드가 실패하면 사이트 데이터베이스 업그레이드 실패와 관련된 문제를 수정합니다. 그런 다음 사이트 데이터베이스의 새 백업을 만들고 데이터베이스의 새 복사본에 대한 업그레이드를 테스트합니다.  



## <a name="next-steps"></a>다음 단계
테스트 데이터베이스 업데이트가 성공적으로 완료된 후에는 업데이트된 데이터베이스를 삭제합니다. Configuration Manager 사이트에서 사용할 수 없기 때문입니다. 그런 후 활성 사이트로 돌아가 [업데이트 설치를 시작](/sccm/core/servers/manage/install-in-console-updates)할 수 있습니다.
