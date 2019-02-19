---
title: UNIX/Linux 클라이언트 구성 요소 서비스 및 명령
titleSuffix: Configuration Manager
description: System Center Configuration Manager의 Linux 및 UNIX 클라이언트 구성 요소 서비스 및 명령에 대해 알아봅니다.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: e5a8c79f-5791-49c5-8055-086d742e5559
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.collection: M365-identity-device-management
ms.openlocfilehash: 2ecd5b3ad493f4916b475aea69b4db241f7ff74b
ms.sourcegitcommit: 874d78f08714a509f61c52b154387268f5b73242
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56132853"
---
# <a name="linux-and-unix-clients-component-services-and-commands-for-system-center-configuration-manager"></a>System Center Configuration Manager의 Linux 및 UNIX 클라이언트 구성 요소 서비스 및 명령

*적용 대상: System Center Configuration Manager(현재 분기)*


 다음 표에서는 Linux 및 UNIX용 Configuration Manager 클라이언트의 클라이언트 구성 요소 서비스를 식별합니다.  

|파일 이름|추가 정보|  
|---------------|----------------------|  
|ccmexec.bin|이 서비스는 Windows 기반 클라이언트의 ccmexc 서비스와 같습니다. Configuration Manager 사이트 시스템 역할과의 모든 통신을 담당하며, 로컬 컴퓨터에서 하드웨어 인벤토리를 수집하도록 omiserver.bin 서비스와도 통신합니다.<br /><br /> 지원되는 명령줄 인수 목록에 대해 **ccmexec -h**를 실행합니다.|  
|omiserver.bin|이 서비스는 CIM 서버입니다. CIM 서버는 공급자라는 플러그형 소프트웨어 모듈에 대한 프레임워크를 제공합니다. 공급자는 Linux 및 UNIX 컴퓨터 리소스와 상호 작용하고 하드웨어 인벤토리 데이터를 수집합니다. 예는 **프로세스 공급자** 는 Linux에 대 한 컴퓨터는 Linux 운영 체제 프로세스와 연관 된 데이터를 수집 합니다.|  

 를 시작 하려면 사용할 수 있는 다음 테이블 목록 명령을 중지 또는 Linux 또는 UNIX의 각 버전에 클라이언트 서비스 (ccmexec.bin 및 omiserver.bin)를 다시 시작 합니다. ccmexec 서비스를 시작하거나 중지하면 omiserver 서비스도 시작되거나 중지됩니다.  

|운영 체제|명령|  
|----------------------|--------------|  
|유니버설 에이전트<br /><br /> RHEL 4 및 SLES 9|시작: **/etc/init d/ccmexecd start**<br /><br /> 중지: **/etc/init d/ccmexecd stop**<br /><br /> 다시 시작: **/etc/init d/ccmexecd restart**|  
|Solaris 9|시작: **/etc/init d/ccmexecd start**<br /><br /> 중지: **/etc/init d/ccmexecd stop**<br /><br /> 다시 시작: **/etc/init d/ccmexecd restart**|  
|Solaris 10|시작:<br /><br /> **svcadm enable -s svc:/application/management/omiserver**<br /><br /> **svcadm enable -s svc:/application/management/ccmexecd**<br /><br /> 중지:<br /><br /> **svcadm disable -s svc:/application/management/ccmexecd**<br /><br /> **svcadm disable -s svc:/application/management/omiserver**|  
|Solaris 11|시작:<br /><br /> **svcadm enable -s svc:/application/management/omiserver**<br /><br /> **svcadm enable -s svc:/application/management/ccmexecd**<br /><br /> 중지:<br /><br /> **svcadm disable -s svc:/application/management/ccmexecd**<br /><br /> **svcadm disable -s svc:/application/management/omiserver**|  
|AIX|시작:<br /><br /> **startsrc -s omiserver**<br /><br /> **startsrc -s ccmexec**<br /><br /> 중지:<br /><br /> **stopsrc -s ccmexec**<br /><br /> **stopsrc -s omiserver**|  
|HP-UX|시작: **/sbin/init.d/ccmexecd start**<br /><br /> 중지: **/sbin/init.d/ccmexecd stop**<br /><br /> 다시 시작: **/sbin/init.d/ccmexecd restart**|  
