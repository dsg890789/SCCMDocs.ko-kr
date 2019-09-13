---
title: 소프트웨어 업데이트에 대한 필수 조건
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 소프트웨어 업데이트에 대한 필수 조건에 대해 알아봅니다.
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 08/22/2019
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: fdf05118-162a-411e-b72e-386b9dc9a5e1
ms.collection: M365-identity-device-management
ms.openlocfilehash: 334854072e5c724f2c76432e7a7372c02cab3d54
ms.sourcegitcommit: 13ac4f5e600dc1edf69e8566e00968f40e1d1761
ms.translationtype: MTE75
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892260"
---
# <a name="prerequisites-for-software-updates-in-system-center-configuration-manager"></a>System Center Configuration Manager의 소프트웨어 업데이트에 대한 필수 조건

*적용 대상: System Center Configuration Manager(현재 분기)*

이 목록에서는 System Center Configuration Manager의 소프트웨어 업데이트에 대한 필수 조건을 나열합니다. 각 필수 구성 요소에 대해 외부 종속성과 내부 종속성이 별도의 표에 표시됩니다.  

## <a name="software-update-dependencies-that-are-external-to-configuration-manager"></a>Configuration Manager 외부인 소프트웨어 업데이트 종속성  
 다음 섹션에는 소프트웨어 업데이트에 대한 외부 종속성이 나열되어 있습니다.  

### <a name="internet-information-services"></a>인터넷 정보 서비스  
 IIS(인터넷 정보 서비스)는 소프트웨어 업데이트 지점, 관리 지점, 배포 지점의 실행을 위해 사이트 시스템 서버에 설치되어야 합니다. 자세한 내용은 [사이트 시스템 역할에 대한 필수 조건](../../core/plan-design/configs/site-and-site-system-prerequisites.md)을 참조하세요.  

### <a name="windows-server-update-services"></a>Windows Server Update Services  
 WSUS(Windows Server Update Services)는 클라이언트에서 소프트웨어 업데이트 동기화 및 소프트웨어 업데이트 적용 가능 여부 검사를 수행하는 데 필요합니다. WSUS 서버는 소프트웨어 업데이트 지점 역할을 만들기 전에 설치해야 합니다. 소프트웨어 업데이트 지점에 대해 다음 버전의 WSUS가 지원됩니다.  

- WSUS 10.0.14393(Windows Server 2016의 역할)
- WSUS 10.0.17763(Windows Server 2019의 역할)(Configuration Manager 1810 이상 필요)
- WSUS 6.2 및 6.3(Windows Server 2012 및 Windows Server 2012 R2의 역할)
  - Windows 10 업그레이드를 배포 하는 경우 WSUS 6.2 및 6.3에 [kb 3095113 및 kb 3159706 (또는 이와 동등한 업데이트)](#BKMK_wsus2012) 가 필요 합니다.

> [!NOTE]
> - 버전 1702부터 Windows Server 2008 R2는 소프트웨어 업데이트 지점 역할을 지원하지 않습니다. 자세한 내용은 [사이트 시스템 서버에 대해 지원되는 운영 체제](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers#bkmk_2008r2sp1)를 참조하세요.
> - 한 사이트에 여러 소프트웨어 업데이트 지점이 있는 경우 모두 동일한 버전의 WSUS를 실행해야 합니다.

### <a name="wsus-administration-console"></a>WSUS 관리 콘솔  
소프트웨어 업데이트 지점이 원격 사이트 시스템 서버에 있고 WSUS가 Configuration Manager 사이트 서버에 아직 설치되지 않은 경우 이 사이트 서버에 WSUS 관리 콘솔이 필요합니다.  

> [!IMPORTANT]  
> - 사이트 서버의 WSUS 버전은 소프트웨어 업데이트 지점에서 실행 중인 WSUS 버전과 같아야 합니다.
> - WSUS 관리 콘솔을 사용하여 WSUS 설정을 구성하지 마세요. Configuration Manager는 소프트웨어 업데이트 지점에서 실행 중인 WSUS의 인스턴스에 연결하고 적합한 설정을 구성합니다.  


### <a name="windows-update-agent"></a>Windows Update 에이전트  
 WSUS 서버에 연결할 수 있도록 클라이언트에 WUA(Windows Update 에이전트) 클라이언트가 필요합니다. WUA는 호환성을 검사해야 하는 소프트웨어 업데이트의 목록을 검색합니다.  

 Configuration Manager를 설치하면 최신 버전의 WUA가 다운로드됩니다. 그런 다음, Configuration Manager 클라이언트가 설치될 때 필요한 경우 WUA가 업그레이드됩니다. 이 설치가 실패하면 다른 방법을 사용하여 WUA를 업그레이드해야 합니다.  

## <a name="software-update-dependencies-that-are-internal-to-configuration-manager"></a>Configuration Manager 내부인 소프트웨어 업데이트 종속성  
 다음 섹션에는 Configuration Manager의 소프트웨어 업데이트에 대한 내부 종속성이 나열되어 있습니다.  

### <a name="management-points"></a>관리 지점  
 관리 지점은 클라이언트 컴퓨터와 Configuration Manager 사이트 간에 정보를 전송합니다. 관리 지점은 소프트웨어 업데이트에 필요합니다.  

### <a name="software-update-points"></a>소프트웨어 업데이트 지점  
 Configuration Manager에서 소프트웨어 업데이트를 배포하려면 WSUS 서버에 소프트웨어 업데이트 지점을 설치해야 합니다. 자세한 내용은 [소프트웨어 업데이트 지점 설치 및 구성](../get-started/install-a-software-update-point.md)을 참조하세요.

### <a name="distribution-points"></a>배포 지점  
 소프트웨어 업데이트에 대한 콘텐츠를 저장하려면 배포 지점이 필요합니다. 배포 지점을 설치하고 콘텐츠를 관리하는 방법에 대한 자세한 내용은 [콘텐츠 및 콘텐츠 인프라 관리](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)를 참조하세요.  

### <a name="client-settings-for-software-updates"></a>소프트웨어 업데이트를 위한 클라이언트 설정  
기본적으로 소프트웨어 업데이트는 클라이언트에 대해 사용하도록 설정됩니다. 클라이언트에서 소프트웨어 업데이트에 대한 호환성을 평가하는 방법과 시점을 제어하고 소프트웨어 업데이트가 설치되는 방식을 제어하는 다른 설정도 있습니다.  

 자세한 내용은 다음 아티클을 참조하세요.  

- [소프트웨어 업데이트를 위한 클라이언트 설정](../get-started/manage-settings-for-software-updates.md#BKMK_ClientSettings)   

- [소프트웨어 업데이트 클라이언트 설정](../../core/clients/deploy/about-client-settings.md#software-updates)  

### <a name="reporting-services-points"></a>보고 서비스 지점  
 보고 서비스 지점 사이트 시스템 역할에서는 소프트웨어 업데이트에 대한 보고서를 표시할 수 있습니다. 이 역할은 선택 사항이지만 사용하는 것이 좋습니다. 보고 서비스 지점을 만드는 방법에 대한 자세한 내용은 [보고 구성](../../core/servers/manage/configuring-reporting.md)을 참조하세요.  

## <a name="BKMK_wsus2012"></a>WSUS 6.2 및 6.3에 필요한 업데이트는 무엇입니까?

WSUS 6.2 및 6.3에서 **업그레이드** 분류를 동기화 하려면 두 가지 업데이트가 필요 합니다. 경우에 따라 KB3095113 및 KB3159706가 설치 되기 전에 동기화 된 경우 업그레이드를 다운로드 하거나 배포 하는 동안 오류가 발생할 수 있습니다. 가능한 문제에 대 한 정보는 다음 섹션에서 설명 합니다.  

- **업그레이드** 분류를 동기화하기 전에 소프트웨어 업데이트 지점 및 사이트 서버에 2015년 10월에 릴리스된 [KB 3095113](https://support.microsoft.com/kb/3095113)을 설치해야 합니다.
  - 이 업데이트는 **업그레이드** 분류를 사용 하도록 설정 합니다.
- Windows 10 버전 1607 이상을 서비스 하려면 [KB 3159706](https://support.microsoft.com/en-us/help/3159706)을 설치 하 고 구성 해야 합니다. KB 3159706은 2016 년 5 월에 출시 되었습니다.
  - 이 업데이트를 통해 WSUS는 Windows 10 버전 1607 이상을 업그레이드 하는 데 사용 되는 파일의 암호를 기본적으로 해독할 수 있습니다.

>[!IMPORTANT]
> KB 3095113 및 KB 3159706 모두 **보안 월별 품질 롤업에** 7 2017 월부터 시작 하 여 제공 됩니다. 즉, 롤업으로 설치 되었을 수 있으므로 KB 3095113 및 KB 3159706이 설치 된 업데이트로 표시 되지 않을 수 있습니다. 그러나 이러한 업데이트 중 하나가 필요한 경우 WSUS의 clientwebservice에서 메모리 사용률을 줄이도록 추가 WSUS 업데이트를 포함 하므로 10 월 2017 일 이후에 릴리스된 **보안 월간 품질 롤업을** 설치 하는 것이 좋습니다.

## <a name="BKMK_RecoverUpgrades"></a>"오류: 인증서 서명이 잘못 되었습니다." 또는 0xc1800118을 사용 하 여 Windows 10 업그레이드를 다운로드 하지 못했습니다.

이 섹션에 설명 된 업데이트 및 문제는 Windows Server 2012 또는 Windows Server 2012 R2 컴퓨터 (WSUS 6.2 및 6.3)에서 실행 되는 WSUS에만 적용 됩니다. 일반적으로 7 월 2017 일 전에 WSUS를 설치 하 고 최근에 **업그레이드** 분류를 사용 하도록 설정한 경우에만이 섹션에 설명 된 문제를 볼 수 있습니다. 그러나 이러한 문제는 다른 상황 에서도 확인할 수 있습니다.

### <a name="historical-information-about-kb-3095113"></a>KB 3095113에 대 한 기록 정보

 [KB 3095113](https://support.microsoft.com/kb/3095113) 은 WSUS에 대 한 Windows 10 업그레이드 지원을 추가 하기 위해 10 월 2015에 [핫픽스로 출시](https://blogs.technet.microsoft.com/wsus/2015/12/03/important-update-for-wsus-4-0-kb-3095113/) 되었습니다. 업데이트를 사용 하면 WSUS에서 Windows 10 용 **업그레이드** 분류의 업데이트를 동기화 하 고 배포할 수 있습니다.

먼저 [KB 3095113](https://support.microsoft.com/kb/3095113)을 설치하지 않고 업그레이드를 동기화하는 경우 WSUS 데이터베이스(SUSDB) 업그레이드가 사용할 수 없는 데이터로 채워집니다. 이러한 데이터는 업그레이드를 제대로 배포하기 위해 지워야 합니다. 이 상태의 Windows 10 업그레이드는 소프트웨어 업데이트 다운로드 마법사를 사용 하 여 다운로드할 수 없습니다.

소프트웨어 업데이트 다운로드 마법사의 완료 페이지에 다음과 유사한 오류가 표시 됩니다.

``` Output
Error: Upgrade to Windows 10 Pro, version 1511, 10586
Failed to download content id {content_id}. Error: Invalid certificate signature
```

또한 다음과 유사한 오류가 PatchDownloader 파일에 기록 됩니다.

``` Log
Download http://wsus.ds.b1.download.windowsupdate.com/d/upgr/2015/12/10586.0.151029-1700.th2_release_...esd...
Authentication of file C:\Users\{username}\AppData\Local\Temp\2\{temporary_filename}.tmp failed, error 0x800b0004
ERROR: DownloadContentFiles() failed with hr=0x80073633
# This log is truncated for readability.
```

지금까지 이러한 오류가 발생 하면 [WSUS에 대 한 해결 단계](https://blogs.technet.microsoft.com/wsus/2016/01/29/how-to-delete-upgrades-in-wsus/)의 수정 된 버전을 수행 하 여 해결할 수 있습니다. 이러한 단계는 KB 3159706 설치 후 필요한 수동 단계를 수행 하지 않는 해결 방법과 유사 하기 때문에 아래 섹션에서 두 단계 집합을 단일 해상도로 결합 했습니다.

- [KB 3095113 또는 KB 3159706을 설치하기 전에 업그레이드 동기화에서 복구하는 방법](#bkmk_fix-upgrades).

### <a name="historical-information-about-kb-3159706"></a>KB 3159706에 대 한 기록 정보

WSUS에서 Windows 10 패키지를 업그레이드 하는 데 사용 되는 esd 파일의 암호를 기본적으로 해독할 수 있도록 KB 3148812는 처음에는 2016에 릴리스 되었습니다. [Kb 3148812에서 일부 고객에 게 문제가 발생](https://blogs.technet.microsoft.com/wsus/2016/05/05/the-long-term-fix-for-kb3148812-issues/) 하 여 [kb 3159706](https://support.microsoft.com/en-us/help/3159706)로 바뀌었습니다. Windows 10 버전 1607 이상 장치를 서비스 하려면 먼저 모든 소프트웨어 업데이트 지점과 사이트 서버에 KB 3159706을 설치 해야 합니다. 그러나 KB를 인식 하지 못하는 경우에는 설치 후 다음 수동 단계를 수행 해야 하는 문제가 발생할 수 있습니다.

1. 관리자 권한 명령 프롬프트에서 `"C:\Program Files\Update Services\Tools\wsusutil.exe" postinstall /servicing`를 시작합니다.
1. 모든 WSUS 서버에서 WSUS 서비스를 다시 시작 합니다.

설치 후 KB 3159706가 수동 단계를 수행 하거나 KB 3159706을 설치 하기 전에 Windows 10 1607 업그레이드에서 동기화 한 경우, WSUS 콘솔에 연결 하 고 업그레이드를 각각 배포 하는 데 문제가 발생 합니다. 클라이언트에서 업그레이드 파일을 다운로드 하면 [ **0Xc1800118** 오류 코드가](https://support.microsoft.com/help/3194588/0xc1800118-error-when-you-push-windows-10-version-1607-by-using-wsus)표시 됩니다.

해결 단계는 KB 3095113 설치 전에 업그레이드를 동기화 하는 것과 유사 하기 때문에 다음 섹션에서 두 단계 집합을 단일 해상도로 결합 했습니다.
 

### <a name="bkmk_fix-upgrades"></a> KB 3095113 또는 KB 3159706을 설치하기 전에 업그레이드 범주 동기화에서 복구하는 방법

아래 단계에 따라 0xc1800118 오류 및 "오류: 잘못 된 인증서 서명"을 모두 해결 합니다.

1. WSUS와 Configuration Manager 모두에서 **업그레이드** 분류를 사용 하지 않도록 설정 합니다. 이러한 지침에 따라로 이동할 때까지 동기화가 수행 되지 않도록 합니다.  
   - 최상위 사이트에서 소프트웨어 업데이트 지점 구성 요소 속성에서 **업그레이드** 분류의 선택을 해제합니다.
     - 자세한 내용은 [분류 및 제품 구성](../get-started/configure-classifications-and-products.md)을 참조하세요.
   - [ **옵션** 페이지](https://docs.microsoft.com/windows-server/administration/windows-server-update-services/manage/setting-up-update-synchronizations)의 **제품 및 분류** 아래 WSUS에서 **업그레이드** 분류를 선택 취소 하거나 관리자 권한으로 실행 되는 PowerShell ISE를 사용 합니다.
      ```PowerShell
      Get-WsusClassification | Where-Object -FilterScript {$_.Classification.Title -Eq “Upgrades”} | Set-WsusClassification -Disable
      ```  
     - 여러 WSUS 서버 간에 WSUS 데이터베이스를 공유 하는 경우 각 데이터베이스에 대해 한 번만 **업그레이드** 를 선택 취소 해야 합니다.  
1. 각 WSUS 서버에서 관리자 권한 명령 프롬프트를 실행 `"C:\Program Files\Update Services\Tools\wsusutil.exe" postinstall /servicing`합니다. 그런 다음 모든 WSUS 서버에서 WSUS 서비스를 다시 시작 합니다.
   -  WSUS는 서비스가 필요한 지 여부를 확인 하기 전에 [단일 사용자 모드로](https://docs.microsoft.com/sql/relational-databases/databases/set-a-database-to-single-user-mode) 데이터베이스를 배치 합니다. 서비스가 실행 되거나 검사 결과에 따라 실행 되지 않습니다. 그런 다음 데이터베이스를 다중 사용자 모드로 다시 전환 합니다. 
   - 여러 WSUS 서버 간에 WSUS 데이터베이스를 공유 하는 경우 각 데이터베이스에 대해이 서비스를 한 번만 수행 하면 됩니다.
1. 관리자 권한으로 실행 되는 PowerShell ISE를 사용 하 여 각 WSUS 데이터베이스에서 모든 Windows 10 업그레이드를 삭제 합니다.
   ```PowerShell
   [reflection.assembly]::LoadWithPartialName("Microsoft.UpdateServices.Administration")
   $wsus = [Microsoft.UpdateServices.Administration.AdminProxy]::GetUpdateServer();
   $wsus.GetUpdates() | Where {$_.UpdateClassificationTitle -eq 'Upgrades' -and $_.Title -match 'Windows 10'} `
   | ForEach-Object {$wsus.DeleteUpdate($_.Id.UpdateId.ToString()); Write-Host $_.Title removed}
   ```
1. 소프트웨어 업데이트 지점이 사용 하는 각 WSUS 데이터베이스의 tbFile 테이블에서 파일을 삭제 합니다. WSUS 데이터베이스의 SQL Server Management Studio에서 다음 명령을 실행 합니다.
   ```SQL
   declare @NotNeededFiles table (FileDigest binary(20) UNIQUE)
   insert into @NotNeededFiles(FileDigest) (select FileDigest from tbFile where FileName like '%.esd%'  except select FileDigest from tbFileForRevision)
   delete from tbFileOnServer where FileDigest in (select FileDigest from @NotNeededFiles)
   delete from tbFile where FileDigest in (select FileDigest from @NotNeededFiles)
   ```
1. Configuration Manager의 최상위 사이트에서 소프트웨어 업데이트 동기화를 시작 하 고 완료 될 때까지 기다립니다. 전체 동기화는 **업그레이드**를 제거할 때 Configuration Manager 분류를 변경 했기 때문에 발생 합니다. (자세한 내용은 [소프트웨어 업데이트 동기화](../get-started/synchronize-software-updates.md)를 참조하세요.
1. 소프트웨어 업데이트 지점 구성 요소 속성에서 **업그레이드** 분류를 선택합니다. 그런 다음 다른 소프트웨어 업데이트 동기화를 시작 하 여 **업그레이드** 를 다시 WSUS로 전환 하 고 Configuration Manager 합니다. Configuration Manager는 WSUS에서 **업그레이드** 분류를 사용 하도록 설정할 필요가 없습니다.
1. 클라이언트에서 업그레이드를 다운로드할 때 **0Xc1800118** 오류 코드를 받은 경우 Windows 업데이트 에이전트에서 사용 하는 데이터 저장소를 삭제 해야 합니다. 장치에서 숨겨진 ~ BT 폴더를 삭제 해야 할 수도 있습니다. 클라이언트는 다음에 검색할 때 델타 대신 WSUS 서버에 대 한 전체 검색을 수행 합니다. 다음 샘플 스크립트와 유사한 PowerShell 스크립트를 사용할 수 있습니다.  
   ```PowerShell
   stop-service wuauserv
   remove-item -path c:\windows\softwaredistribution\datastore -recurse -force
   # If the device has a hidden ~BT folder on the c drive, delete it too by uncommenting the next line.
   # remove-item -path c:\~BT -recurse -force
   start-service wuauserv
   ```

## <a name="next-steps"></a>다음 단계
[소프트웨어 업데이트 관리 준비](../get-started/prepare-for-software-updates-management.md)
