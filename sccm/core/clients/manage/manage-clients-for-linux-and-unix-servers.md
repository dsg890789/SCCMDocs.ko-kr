---
title: Linux 및 UNIX 클라이언트 관리
titleSuffix: Configuration Manager
description: Configuration Manager에서 Linux 및 UNIX 서버의 클라이언트 관리
ms.date: 03/27/2019
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 948664f2-239d-47a8-92fc-f8efeebd5796
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 716441bd146e9172b3f183c497fcaa4036ad0084
ms.sourcegitcommit: 148745e1c3d9817d8beea20684a54436210959c6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/09/2020
ms.locfileid: "75824166"
---
# <a name="how-to-manage-clients-for-linux-and-unix-servers-in-configuration-manager"></a>Configuration Manager에서 Linux 및 UNIX 서버용 클라이언트를 관리하는 방법

*적용 대상: Configuration Manager(현재 분기)*

> [!Important]  
> 버전 1902부터 Configuration Manager는 Linux 또는 UNIX 클라이언트를 지원하지 않습니다. 
> 
> 따라서 Linux 서버를 관리하려면 Microsoft Azure 관리를 고려해야 합니다. Azure 솔루션은 대부분의 경우 Linux용 엔드투엔드 패치 관리를 포함하여 Configuration Manager 기능을 능가하는 광범위한 Linux 지원을 제공합니다.

Configuration Manager에서 Linux 및 UNIX 서버를 관리하는 경우 서버를 관리할 수 있도록 컬렉션, 유지 관리 기간 및 클라이언트 설정을 구성할 수 있습니다. 또한 Linux 및 UNIX용 Configuration Manager 클라이언트에 사용자 인터페이스가 없어도 클라이언트가 수동으로 클라이언트 정책을 강제로 폴링할 수 있습니다.

##  <a name="BKMK_CollectionsforLnU"></a> Linux 및 UNIX 서버 컬렉션  
 컬렉션을 사용하여 다른 클라이언트 형식을 관리하는 것과 같은 방식으로 Linux 및 UNIX 서버 그룹을 관리합니다. 컬렉션은 직접 멤버 자격 컬렉션 또는 쿼리 기반 컬렉션일 수 있습니다. 쿼리 기반 컬렉션은 클라이언트 운영 체제, 하드웨어 구성 또는 사이트 데이터베이스에 저장된 클라이언트의 다른 세부 정보를 식별합니다. 예를 들어 Linux 및 UNIX 서버를 포함하는 컬렉션을 사용하여 다음 설정을 관리할 수 있습니다.  

- 클라이언트 설정  

- 소프트웨어 배포  

- 유지 관리 기간 적용  

  Linux 또는 UNIX 클라이언트를 해당 운영 체제 또는 배포로 식별하려면 클라이언트에서 [하드웨어 인벤토리](../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md)를 수집해야 합니다.  

  하드웨어 인벤토리에 대한 기본 클라이언트 설정에는 클라이언트 컴퓨터의 운영 체제에 대한 정보가 포함됩니다. **운영 체제** 클래스의 **캡션** 속성을 사용하여 Linux 또는 UNIX 서버의 운영 체제를 식별할 수 있습니다.  

  Configuration Manager 콘솔에 있는 **자산 및 준수** 작업 영역의 **디바이스** 노드에서 Linux 및 UNIX용 Configuration Manager 클라이언트를 실행하는 컴퓨터에 대한 세부 정보를 볼 수 있습니다. Configuration Manager 콘솔의 **자산 및 준수** 작업 영역에 있는 **운영 체제** 열에서 각 컴퓨터 운영 체제의 이름을 볼 수 있습니다.  

  기본적으로 Linux 및 UNIX 서버는 **모든 시스템** 컬렉션의 멤버입니다. Linux 및 UNIX 서버 또는 그 하위 집합만을 포함하는 사용자 지정 컬렉션을 빌드하는 것이 좋습니다. 사용자 지정 컬렉션을 사용하면 소프트웨어 배포 또는 유사 컴퓨터 그룹에 클라이언트 설정 할당과 같은 작업을 관리할 수 있으므로 배포에 성공했는지 정확히 측정할 수 있습니다.   

  Linux 및 UNIX 서버용 사용자 지정 컬렉션을 빌드할 때 운영 체제 특성에 대해 캡션 특성을 포함하는 멤버 관리 규칙 쿼리를 포함시킵니다. 컬렉션 만들기에 대한 자세한 내용은 [컬렉션을 만드는 방법](../../../core/clients/manage/collections/create-collections.md)을 참조하세요.  

##  <a name="BKMK_MaintenanceWindowsforLnU"></a> Linux 및 UNIX 서버에 대 한 유지 관리 기간  
 Linux 및 UNIX 서버용 Configuration Manager 클라이언트는 [유지 관리 기간](../../../core/clients/manage/collections/use-maintenance-windows.md) 사용을 지원합니다. 이 지원은 Windows 기반 클라이언트 지원에서 변경되지 않았습니다.  

##  <a name="BKMK_ClientSettingsforLnU"></a> Linux 및 UNIX 서버에 대 한 클라이언트 설정  
 다른 클라이언트에 대한 설정을 구성하는 것과 동일한 방식으로 Linux 및 UNIX 서버에 적용하는 [클라이언트 설정을 구성](../../../core/clients/deploy/configure-client-settings.md)할 수 있습니다.  

 기본적으로 **기본 클라이언트 에이전트 설정** 은 Linux 및 UNIX 서버에 적용됩니다. 사용자 지정 클라이언트 설정을 만들고 특정 클라이언트의 컬렉션에 배포할 수도 있습니다.  

 Linux 및 UNIX 클라이언트에만 적용하는 추가 클라이언트 설정은 없습니다. 그러나 Linux 및 UNIX 클라이언트에 적용하지 않는 기본 클라이언트 설정은 있습니다. Linux 및 UNIX용 클라이언트는 지원되는 기능에 대한 설정만 적용합니다.  

 예를 들어 원격 제어 설정을 사용하도록 설정하고 구성하는 사용자 지정 클라이언트 디바이스 설정은 Linux 및 UNIX 서버에서 무시됩니다. Linux 및 UNIX용 클라이언트는 원격 제어를 지원하지 않기 때문입니다.  

##  <a name="BKMK_PolicyforLnU"></a> Linux 및 UNIX 서버에 대 한 컴퓨터 정책  
 Linux 및 UNIX 서버용 클라이언트는 주기적으로 컴퓨터 정책에 대해 해당 사이트를 폴링하여 요청된 구성에 대해 알아보고 배포를 확인합니다.  

 또한 컴퓨터 정책에 대해 Linux 또는 UNIX 서버의 클라이언트를 즉시 폴링하도록 강제할 수 있습니다. 이렇게 하려면 서버에서 **루트** 자격 증명을 사용하여 **/opt/microsoft/configmgr/bin/ccmexec -rs policy** 명령을 실행합니다.  

 컴퓨터 정책 폴링에 대한 세부 정보는 공유 클라이언트 로그 파일인 **scxcm.log**에 입력됩니다.  

> [!NOTE]  
>  Linux 및 UNIX용 Configuration Manager 클라이언트는 사용자 정책을 요청하거나 처리하지 않습니다.  

##  <a name="BKMK_ManageLinuxCerts"></a> Linux 및 UNIX 용 클라이언트에서 인증서를 관리 하는 방법  
 Linux 및 UNIX용 클라이언트를 설치한 후 **certutil** 도구를 사용하여 새 PKI 인증서로 클라이언트를 업데이트하고 새 CRL(인증서 해지 목록)을 가져옵니다. Linux 및 UNIX용 클라이언트를 설치할 때 이 도구는 `/opt/microsoft/configmgr/bin/certutil`에 배치됩니다. 

 인증서를 관리하려면 각 클라이언트에서 다음 옵션 중 하나를 사용하여 certutil을 실행합니다.  

|옵션|추가 정보|  
|------------|----------------------|  
|`importPFX`|클라이언트에서 현재 사용 중인 인증서를 대체할 인증서를 지정하려면 이 옵션을 사용합니다.<br /><br /> `-importPFX`를 사용하는 경우 `-password` 명령줄 매개 변수도 사용하여 PKCS#12 파일과 관련된 암호를 입력해야 합니다.<br /><br /> `-rootcerts`를 사용하여 추가 루트 인증서 요구 사항을 지정합니다.<br /><br /> 예: `certutil -importPFX <path to the PKCS#12 certificate> -password <certificate password> [-rootcerts <comma-separated list of certificates>]`|  
|`importsitecert`|관리 서버의 사이트 서버 서명 인증서를 업데이트하려면 이 옵션을 사용합니다.<br /><br /> 예: `certutil -importsitecert <path to the DER certificate>`|  
|`importcrl`|클라이언트에서 하나 이상의 CRL 파일 경로로 CRL을 업데이트하려면 이 옵션을 사용합니다.<br /><br /> 예: `certutil -importcrl <comma separated CRL file paths>`|  
