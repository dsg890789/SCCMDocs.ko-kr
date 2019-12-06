---
title: 바이러스 백신 제외 구성
titleSuffix: Configuration Manager
description: 발생할 수 있는 문제를 해결할 때 사용하기 위해 권장되는 바이러스 백신 제외에 대해 알아봅니다.
ms.date: 10/31/2019
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: deb470e3-6f6b-4ccf-b3d8-1598d79d3490
author: mestew
ms.author: mstewart
manager: dougeby
ms.collection: M365-identity-device-management
ROBOTS: NOINDEX
ms.openlocfilehash: a0d844c6ee5b40e987ab25f4183e8365d18edac3
ms.sourcegitcommit: 1bccb61bf3c7c69d51e0e224d0619c8f608e8777
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2019
ms.locfileid: "73145516"
---
# <a name="recommended-antivirus-exclusions-for-configuration-manager"></a>Configuration Manager에 대한 권장 바이러스 백신 제외

*적용 대상: System Center Configuration Manager(현재 분기)*

이 문서에는 관리자가 지원되는 버전의 Configuration Manager 사이트 서버, 사이트 시스템 및 클라이언트를 실행하는 컴퓨터에서 바이러스 백신 소프트웨어이 함께 사용됐을 때 잠재적인 불안정의 원인을 확인하는 데 도움이 되는 권장 사항이 포함되어 있습니다.

> [!IMPORTANT]
>
> - 이러한 절차를 일시적으로 적용하여 시스템을 평가하는 것이 좋습니다. 이 문서에서 설명하는 권장 사항에 따라 시스템 성능이나 안정성이 향상되면 바이러스 백신 소프트웨어 공급 업체에 문의하여 안내를 받거나 업데이트된 버전의 바이러스 백신 소프트웨어를 받으십시오.
> - 이 문서에는 보안 설정을 낮추거나 컴퓨터의 보안 기능을 일시적으로 해제하는 방법을 보여주는 정보가 포함되어 있습니다. 이러한 변경을 수행하여 특정 문제의 특성을 이해할 수 있습니다. 이러한 변경을 수행하기 전에 특정 환경에서 이 해결 방법을 구현하는 것과 관련된 위험을 평가하는 것이 좋습니다.

## <a name="possible-symptoms"></a>가능한 증상 

바이러스 백신 실시간 보호는 Configuration Manager 사이트 서버, 사이트 시스템 및 클라이언트에서 많은 문제를 일으킬 수 있습니다.

다음은 가능한 증상의 일부를 보여주는 목록입니다.

- 원격 사이트 시스템 구성 요소가 설치되지 않습니다. SiteComp.log, Distmgr.log, hman.log 또는 기타 Configuration Manager 로그 파일에 오류 80070005와 같은 오류가 포함될 수 있습니다.
- Client Push를 사용해 Configuration Manager 클라이언트를 설치할 수 없습니다.
- 클라이언트 인벤토리 정보가 부정확하거나 누락되거나 만료되었습니다.
- 백로그는 *Install_Directory*\Program Files\Microsoft Configuration Manager\Inboxes 폴더에서 발생합니다.
- 소프트웨어 센터는 클라이언트 시스템에 배포된 소프트웨어에 의해 배포되거나 시작되지 않습니다. CCMRepair.log 파일에는 다음 예제와 유사한 오류가 포함될 수도 있습니다.

  > 다음 결과와 같이 데이터베이스 확인에 실패했습니다. 0x80004005(DB): C:\Windows\CCM\filename.sdf를 열 수 있습니다. DB 복구를 건너뜁니다.

- 클라이언트에 배포된 소프트웨어를 설치할 수 없습니다.
- 소프트웨어 배포에 대한 준수 데이터가 정확하지 않습니다.

## <a name="exclusions"></a>제외

이러한 문제를 방지하려면 다음과 같은 실시간 보호 제외를 추가하는 것이 좋습니다.

### <a name="default-installation-folders"></a>기본 설치 폴더

|  |  |
| - | - |
|*ConfigMgr 설치 폴더*  |  %ProgramFiles%\Microsoft Configuration Manager  |  
|*MP 설치 폴더*  |%ProgramFiles%\SMS_CCM  |  
|*클라이언트 설치 폴더*  |%Windir%\CCM  |  

### <a name="folder-exclusions-for-site-servers"></a>사이트 서버에 대한 폴더 제외

- *ConfigMgr 설치 폴더*\Inboxes
- *ConfigMgr 설치 폴더*\logs
- *ConfigMgr 설치 폴더*\EasySetupPayload

### <a name="folder-exclusions-for-site-systems"></a>사이트 시스템에 대한 폴더 제외

- 관리 지점
  - *MP 설치 폴더*\ServiceData
  - 다음 중 하나:
    - *ConfigMgr 설치 폴더*\MP\OUTBOXES
    - *설치 드라이브*\SMS\MP\OUTBOXES
- 배포 지점
  - *클라이언트 설치 폴더*\ServiceData
  - *ContentLib_Drive*\SMS_DP$
  - *ContentLib_Drive*\SMSPKG*Drive_Letter*$
  - *ContentLib_Drive*\SMSPKG
  - *ContentLib_Drive*\SMSPKGSIG
  - *ContentLib_Drive*\SMSSIG$
- 사이트 데이터베이스 서버
  - [SQL Server를 실행하는 컴퓨터에서 실행되는 바이러스 백신 소프트웨어를 선택하는 방법](https://support.microsoft.com/en-us/help/309422)

### <a name="folder-exclusions-for-clients"></a>클라이언트에 대한 폴더 제외

- *클라이언트 설치 폴더*\\\*.sdf
- *클라이언트 설치 폴더*\ServiceData
- C:\Windows\CCMCache
- C:\Windows\CCMSetup
- *클라이언트 설치 폴더*\Logs

### <a name="file-exclusions-for-mps"></a>MP의 파일 제외

- 다음의 POL00000.pol
  - *MP 설치 폴더*\PolReqStaging

### <a name="process-exclusions"></a>프로세스 제외

프로세스 제외는 적극적인 바이러스 백신 프로그램이 System Center Configuration Manager 프로그램 파일(.exe 파일)을 높은 위험 수준 프로세스로 간주하는 경우에만 필요합니다.

- *ConfigMgr 설치 폴더*\bin\64\Smsexec.exe
- 다음 프로세스 중 하나:
  - *클라이언트 설치 폴더*\Ccmexec.exe
  - *MP 설치 폴더*\Ccmexec.exe
- *클라이언트 설치 폴더*\CmRcService.exe (클라이언트 쪽)
- *ConfigMgr 설치 폴더*\bin\64\Sitecomp.exe
- *ConfigMgr 설치 폴더*\bin\64\Smswriter.exe
- *ConfigMgr 설치 폴더*\bin\64\Smssqlbkup.exe 또는 SMS_*SQLFQDN*\bin\x64\Smssqlbkup.exe
- *ConfigMgr 설치 폴더*\bin\64\Cmupdate.exe
- *클라이언트 설치 폴더*\Ccmrepair.exe (클라이언트 쪽)
- %*windir*%\CCMSetup\Ccmsetup.exe (클라이언트 쪽)

## <a name="next-steps"></a>다음 단계

바이러스 백신 제외에 대한 자세한 내용은 다음 문서를 참조하세요.

[Configuration Manager 현재 분기 바이러스 백신 제외 - System Center 프리미어 현장 엔지니어 블로그](https://blogs.technet.microsoft.com/systemcenterpfe/2017/05/24/configuration-manager-current-branch-antivirus-update/)

[업데이트된 System Center 2012 Configuration Manager 바이러스 백신 제외 및 OSD 및 부팅 이미지에 대한 자세한 정보](https://blogs.technet.microsoft.com/systemcenterpfe/2013/01/11/updated-system-center-2012-configuration-manager-antivirus-exclusions-with-more-details-on-osd-and-boot-images-etc/)

[SQL Server를 실행하는 컴퓨터에서 실행되는 바이러스 백신 소프트웨어를 선택하는 방법](https://support.microsoft.com/en-us/help/309422/how-to-choose-antivirus-software-to-run-on-computers-that-are-running-sql-server)

[현재 지원되는 Windows 버전을 실행하는 엔터프라이즈 컴퓨터에 대한 바이러스 검사 권장 사항](https://support.microsoft.com/en-us/help/822158/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows)
